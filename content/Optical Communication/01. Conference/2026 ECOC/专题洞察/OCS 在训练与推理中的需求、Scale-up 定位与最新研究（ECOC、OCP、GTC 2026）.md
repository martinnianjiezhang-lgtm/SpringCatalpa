---
title: "OCS 在训练与推理中的需求、Scale-up 定位与最新研究（ECOC、OCP、GTC 2026）"
tags:
  - OCS
  - ScaleUp
  - 推理
  - ECOC2026
  - OCP2026
  - GTC2026
  - 专题洞察
date: 2026-10-22
---

> [!info] 资料与口径
> - **ECOC 2026**：现场讲稿笔记中提到 OCS 的有 26 批，重点讲者包括 iPronics、KDDI、Salience Labs、Oriole、Columbia、NVIDIA（Bakopoulos）、华为、美团、中国电信、Cignal AI、OneTouch、清华、PsiQuantum。
> - **OCP 2026**：OCS 相关报告 12 份，包括 Google、Oracle/Lumentum、iPronics/KDDI/NTT、Lumotive 快速 OCS 白皮书、P111 精确时间电路交换实验、Marvell/Microsoft 可靠性面板。
> - **OFC 2026 / ECOC 2025 论文**：OCS 相关 18 篇，包括 NVIDIA M3F.6、Ayar Labs/伯克利 W2A.28（推理阈值）、剑桥 M3F.5、中国科大 M4F.2、日本 M4F.4、上海交大 W2A.31、阿里 W2A.41 等。
> - **GTC**：GTC Berlin（10 月 21 日主题演讲）只依据 NVIDIA 官方博客和新闻转写，我没有看到完整讲稿；NVL576/NVL1152 的规划取自 GTC 2026 春季（3 月）的公开报道。
> - 文中“自报”表示厂商宣称、没有第三方数据；“读图”表示从照片曲线估读。

## 结论先行

1. **训练和推理对 OCS 的要求，差别不在带宽，在“流量能不能提前知道”。** 训练的流量是周期性的、可预测的，迭代之间有 100–400 ms 的零流量窗口，毫秒级的 MEMS OCS 已经够用。推理分两种：prefill 平稳；decode 和 MoE 的 all-to-all 时延敏感、目的地不可预测。所以推理里的 OCS 只能当“按部署配置的拓扑”，不能当“按包切换的交换机”。
2. **OCS 进 scale-up 的原因有四个。** 带宽集中在 scale-up 层；scale-up 的流量结构在一个作业内基本固定；铜缆距离到头后需要光把域扩到跨机柜；电交换机每多一跳就多几百 ns 时延和几百瓦功耗。OCS 能用无源、不做光电转换的直连，换掉一层电交换。
3. **OCS 能用于推理，而且已经在现网。** Google TPU 8i 推理 pod 用 OCS 把 36 个组连成 1,024 芯片、最多 7 跳的 Boardfly 拓扑。华为说 OCS + 电交换的稀疏超节点让推理性能提升 10%。美团实测 KV cache 经 OCS 跨 100 km，TTFT 只增加 7%。这些都是“静态或慢重构”的用法。
4. **在集合通信内部动态切换，门槛是亚微秒，外加收发器快速重锁定。** Ayar Labs/伯克利算出，推理中 OCS 要追平电交换，重构时间要小于 400–700 ns；否则只能靠高扇出、高基数来弥补。Oriole 指出，即使开关只要 10 ns，配标准收发器时吞吐仍不到 1%。
5. **NVIDIA 的口径是“铜和光都要”，还没有公开 OCS 进 NVLink 的产品。** GTC Berlin 讲的是 Spectrum-X CPO 已全面量产，以及 Vera Rubin NVL72。NVL576（2027 下半年）的跨机柜 scale-up 走 CPO，组成两层全互联。NVIDIA 研究团队在 OFC 和 ECOC 上把 scale-up 列为“最难但收益最大”的 OCS 插入点。Cignal AI 判断 NVL576 会集成 OCS，但 NVIDIA 没有确认。

---

## 一、训练和推理的流量模型，决定了 OCS 的核心需求

### 1.1 流量画像对比

| 维度 | 训练 | 推理：prefill | 推理：decode / MoE |
|---|---|---|---|
| 主要并行方式 | TP、PP、DP、EP、FSDP | TP，长上下文时加 CP | TP、EP；P/D 分离或 AF 分离（attention 与 FFN 分开部署） |
| 流量特征 | 按迭代周期出现，阶段固定（TP 最频繁，DP 数据量最大）；超过 75% 的训练字节是 TP，且不出 NVLink 域；99% 以上的 GPU 对之间没有流量（P111 引用 Meta、Rail-only） | 计算受限，通信平滑（OpenAI） | 小消息、低 batch、计算与通信难重叠，通信暴露在关键路径上；MoE token 路由的目的地不可预测（Salience、OpenAI、Google） |
| 可预测性 | 高。作业内的拓扑可以提前算好；但 64K GPU 规模下，逐轮的到达时间预测误差约 434 ms（P111） | 高 | 拓扑层面可预测，因为推理框架掌握全部路由分配信息；包层面不可预测 |
| 时间尺度 | 作业：小时到天；迭代：秒级；迭代内零流量窗口 100–400 ms（KDDI） | 请求级：毫秒到秒 | 每 token 一次，TPOT 目标 50 → 20 → 5 ms（华为） |
| 主要 KPI | 作业完成时间（JCT）、MFU、goodput（Google 目标 >97%） | TTFT | TPOT、尾时延、每 token 成本（$/token）、每瓦请求数 |

### 1.2 两类场景对 OCS 的核心需求

| 需求 | 训练 | 推理 | 依据 |
|---|---|---|---|
| **重构速度** | 按作业或切片重构：毫秒级就够。按阶段重构：要小于约 0.1 ms 才有收益。 | 按部署配置：分钟到小时级就够。集合通信内切换：要 <400–700 ns。 | Columbia ACTINA：4096 张 H100 训练 GPT-3，重构时延 <10⁻⁴ s 时比一次性配置最多快 2.3 倍，≥10⁻³ s 时收益消失。伯克利 W2A.28：100 ns、1 µs、10 µs、100 µs 重构，分别是电交换耗时的 0.90、1.15、3.67、28.85 倍（8 GPU AllReduce）。 |
| **重构时机** | 要对齐计算阶段的零流量窗口；在流量峰值时切换会中断作业。 | 绑定模型部署和服务等级（SLO）；华为的 AF 算力池按小时或天调整。 | KDDI p13；Salience p16；华为 p4 |
| **基数与扇出** | 每台 OCS 300 端口级（Google）；跨 pod 的少量直连 | 要求高扇出：伯克利算出扇出 k = N−1 时，即使 100 µs 重构，也比电交换快 2.83 倍（AllReduce）/ 5.24 倍（AlltoAll） | W2A.28；Cignal（scale-up 需要 64/72 端口级） |
| **时延** | 次要，JCT 对几十 ns 不敏感 | 关键：单级电交换 1,000 ns、两级 1,600 ns，其中带宽项只占 25 ns | KDDI：经 OCS 后增加数十 ns；Salience p5–p6 |
| **可靠性与故障恢复** | 核心价值：131K GPU 集群的平均故障间隔（MTBF）只有 15 分钟；OCS 能把 1:1 保护变成 1:N 备件池，自动绕开故障 | 同样重要：GPU 不像交换机那样能消化链路闪断（flap） | iPronics/KDDI/NTT P421；Microsoft P345；Google 8t |
| **与光模块的配合** | LPO 经 OCS 后 pre-FEC BER 没有量级变化；链路建立 4–9 ms | 动态切换必须配“快速重锁定”的收发器 | KDDI p7、p10；Oriole p9 |
| **插损预算** | 3D MEMS 插损中位 1.2–1.4 dB，落在 FR 4 dB 预算内 | 同左；scale-up 用 DR4 时只剩约 3 dB 余量 | Oracle/Lumentum P430；NVIDIA Bakopoulos p18 |

**要点**：训练要的是 OCS 的“可重构性 + 低功耗 + 自动绕障”。推理要的是 OCS 的“少跳数 + 低时延 + 高基数直连”。推理并不需要 OCS 跟着每个请求切换。

---

## 二、为什么 OCS 用在 Scale-up

### 2.1 五个驱动力

1. **带宽集中在 scale-up。**
   - NVIDIA OFC 论文 M3F.6 写明，系统带宽主要集中在 scale-up 层，这里引入 OCS 最难，但收益最大。
   - NewPhotonics 称，scale-up 的每 GPU 带宽是 scale-out 的 9 倍。
   - Columbia 给的数字：NVLink 6 每 GPU 3.6 TB/s，scale-out 网卡每 GPU 1.6 Tb/s。
2. **流量在一个作业或部署内是确定的，适合电路交换。**
   - 训练的 TP/EP 拓扑在作业内基本不变。
   - Salience 认为 scale-up 是“负载静态”网络：推理框架掌握全部路由分配信息，可以按模型部署配置 OCS。
3. **铜缆距离到头，域要扩到跨机柜。**
   - NVL576 有 8 个机柜，宽近 5 m，200G 速率下铜缆连不了。
   - Google V7 pod：144 个机柜 × 96 个 ICI 光口 = 13,824 根光纤，接 48 台 OCS，组成 9K 级超节点（Marvell 引用）。
   - iPronics 和 Cignal 的定位都是“用 OCS 把计算域扩到跨机柜”。
4. **省一层电交换，就省下时延、功耗和光模块。**
   - Salience：单级电交换 1,000 ns，两级 1,600 ns。
   - KDDI：32 端口电交换机满载约 1,000 W，OCS 只要 30–100 W，还能省掉 50% 的收发器。
   - iPronics：64×1.6T 电交换机约 3,500 W，自家 OCS <100 W（自报）。
   - Google 引用 Jupiter 数据：成本 -30%、功耗 -40%。
   - Oriole：32K GPU 集群的网络功耗 -81%（自报）。
5. **速率无关、跨代复用，并且能自动绕障。**
   - OCS 不看协议、不看速率，400G、800G、1.6T 都能透传（中国电信）。
   - TPU 8t 用 OCS 在无人干预下绕开故障，目标 goodput >97%。

### 2.2 Scale-up 用 OCS 的四道门槛（NVIDIA Bakopoulos，ECOC 2026 p18）

| 门槛 | 现状 | 进展 |
|---|---|---|
| 插损 | 路径上至少有 4 个光纤连接器；DR4 只剩 3 dB 余量，FR4 剩 4 dB | iPronics 用片上 SOA 给 10 dB 增益补损耗；PsiQuantum 的 8×8 原型插损约 1.0 dB |
| 成本与密度 | 目标每 1U 超过 256 个双工端口，一个机柜需要上千个 OCS 端口 | 3D MEMS 每 1U 只有 32–40 端口；iPronics 约 $100/端口，芯片从 32 口到 64 口，计划 2027 年做到 100 口以上 |
| 可靠性 | 故障影响面大，必须达到无源铜缆的可靠性；不能吃掉 BER/FEC 余量 | Microsoft 建议把同一端口的 lane 分到不同故障域；OCP 在做 OCS 一致性测试 |
| 光模块形态 | Salience 认为“全 OCS 的 scale-up 需要 NPO/CPO” | NVIDIA 把“OCS 兼容性”列为 scale-up CPO 选型维度之一（Mo4-I p8） |

**判断**：OCS 进 scale-up，不是去替换机柜内的 NVLink 交换，而是在“机柜之间 / 超节点之间”那一层替换电交换或做直连。Google TPU（8t 的 3D torus、8i 的 Boardfly）是现成样板；GPU 阵营要等 CPO/NPO 成熟以及高基数硅光 OCS，大约在 2027–2028 年。

---

## 三、OCS 能用在推理吗？能，分三种用法

| 用法 | 重构频率 | 成熟度 | 代表案例 |
|---|---|---|---|
| **A. 静态/慢重构的拓扑层** | 按部署或切片，分钟到天 | **已在现网** | **Google TPU 8i Boardfly**：4 芯片一个托盘，8 个托盘铜缆全互联成一组，36 组通过 OCS 互联，共 1,024 芯片；最多 7 跳（3D torus 是 16 跳），all-to-all 时延最多改善 50%，面向 MoE 与推理模型。**华为**：OCS + 电交换的稀疏超节点，动态时延 500 ns 以上，网络时延 -30%、推理性能 +10%，超节点扩展到 16K；AF 分离推理的算力池按小时或天调整，OCS 动态调带宽。 |
| **B. 资源池化与跨域弹性** | 按资源调度，秒到小时 | 已有实测 | **美团**：DeepSeek-R1 671B 的 KV cache 以 8:1 收敛比经 OCS + OTN 跨 100 km，TTFT 为基线的 107.21%，TPOT 约 101%。**阿里** W2A.41：PCIe 5.0 over LPO + OCS，组成可组合的 CPU-GPU 资源池，100 m 无误码。**Columbia SiPAM**：按负载重新分配 I/O，训练与推理迭代时间最多快约 3.5 倍（仿真）。 |
| **C. 集合通信内的动态切换** | 每轮通信，ns 到 µs | 研究阶段 | **伯克利/Ayar** W2A.28：重构时间盈亏点在 400–700 ns。**日本** M4F.4：硅光开关在 EP/TP 网络和 DP 网络间交替切换，光路建立后开销 <2 µs。**Oriole** PRISM：ns 级开关 + 超快重锁定，宣称 tokens/s 提升 4 倍（自报）。**OneTouch** TFLT 8×8 <4 ns；**清华** 波长切换 80 ns。 |

**推理用 OCS 的风险**：
- decode 时延敏感，任何“暗时间”都会直接拉高 TPOT 的尾部。
- 标准收发器重锁定需要毫秒级，抵消了快速开关的优势。
- RoCE/NCCL 对链路闪断敏感，OCS 切换需要和通信库协同（P421 列为空白）。
- 美团数据显示，EP 流量经 OCS 收敛后，最坏情况变慢 21%。所以 EP 的 all-to-all 不宜放在收敛的 OCS 路径上。

**判断**：在推理里，OCS 的正确定位是“拓扑配置器”，不是“包交换替代品”。近期价值在 A、B 两类：降跳数、扩超节点、P/D 与 AF 分离后按负载重配带宽。C 类要等 ns 级开关、快速锁定光模块、通信库调度三者都到位，最早在 2028 年以后。

---

## 四、业界最新研究与产业进展

### 4.1 按重构时间划分的技术图谱

| 技术 | 重构时间 | 典型规模 | 适配场景 | 代表 |
|---|---|---|---|---|
| 3D MEMS（自由空间） | 毫秒级（暗时间约 20 ms） | 300×300 级 | 训练 scale-out、切片、绕障 | Google Palomar/Apollo、Lumentum、Coherent、Triple-Stone 320×320 |
| 机械手/压电/液晶 | 秒到毫秒 | 大 | 配线、园区、DCI | Telescent、Huber+Suhner（POLATIS） |
| 超表面自由空间 | 约 50 µs | — | 快速 scale-out | Lumotive |
| 硅光 MEMS / 热光 | 1–100 µs，系统可做到亚毫秒 | 32 → 64 → 100 口以上 | scale-up 扩展、备件池 | iPronics ONE-32/64、浙大 240×240、PsiQuantum 4×64 |
| 电光（TFLN/TFLT、SOA、AWGR） | ns 级 | 8×8 级 | 推理集合通信内切换 | OneTouch（<4 ns）、清华（80 ns）、Oriole（<10 ns，自报） |
| 空分 + 波分 | — | 4,096×4,096，819.2 Tb/s | 超大基数单层 | 日本 OFC M3F.3 |

### 4.2 主要玩家

| 玩家 | 最新进展 | 场景 |
|---|---|---|
| **Google** | TPU 8t：3D torus + OCS 切片与绕障；8i：Boardfly，36 组经 OCS 互联；OCP 上提交 OCS 接口规范 v0.8（YANG/gNMI）；研究用 OCS 替代园区 spine，配 1.6T Coherent-Lite | 训练 + 推理 scale-up，园区 |
| **NVIDIA** | 研究侧：OFC M3F.6 列出四个 OCS 插入点（scale-up、scale-out、DPU、scale-across）；ECOC 提出 OCS 四道门槛。产品侧：只公开了 CPO（Spectrum-X 已量产，NVL576 跨机柜 CPO） | 尚在评估 |
| **华为** | OCS + 电交换稀疏超节点，扩展到 16K，推理 +10%；AF 分离按负载调带宽 | 推理 scale-up |
| **美团** | OCS + OTN 跨可用区 100 km，实测训练与推理 | 跨域 |
| **中国电信** | OCS 替代 super-spine：网络功耗 -20%、故障率 -17% 以上；在城域汇聚节点部署 OCS | scale-out、城域 |
| **KDDI / NTT / iPronics** | LPO + OCS 稳定预训练 72 小时；OCP-OCS YANG R1.0；OFC 2027 计划做 8 家厂商互通演示 | 训练、备件池 |
| **Oracle / Lumentum** | 1,000 台 OCS 插损数据；零接触生命周期运维 | scale-out |
| **Salience Labs** | 把 OCS 用于推理 scale-up；512 XPU 仿真，all-reduce 和 all-to-all 都比电交换快 | 推理 scale-up |
| **学术界** | Columbia（SiPAM、ACTINA 2.3 倍）、剑桥（按阶段重构，通信快 37.5%）、中国科大（作业内部分重构）、北邮（逐流调度，All-Reduce -50.3%）、上海交大（双资源池，功耗 -40%）、中科院（硬件调度器 <1 µs） | 训练为主，推理开始出现 |

### 4.3 标准与市场

- **OCP OCS 子项目**：2026 年 4 月发布 OCS 白皮书，快速切换白皮书待发；YANG R1.0 已发布；Google 的接口规范 v0.8 已提交；SONiC 成立 OCS 工作组；Oracle 呼吁制定强制的生命周期 profile 和一致性测试。
- **市场（Cignal AI）**：2026 年超过 20 亿美元，2030 年超过 80 亿美元。目前收入几乎都来自 Google 的 TPU scale-out；增量来自 GPU scale-up，预计到 2030 年会追上并反超 scale-out。ECOC 市场聚焦讲读图：2030 年 OCS 端口约 4,600 万个，其中 GPU scale-up 约 2,600 万。
- **OCS 拉动单纤光模块**：DR/FR 光学取代多纤方案，让 OCS 用量增加 8 倍，并推动多波长方案（Cignal 及 ECOC 市场聚焦讲）。

---

## 五、GTC 2026 的信号

- **GTC Berlin（10 月 21 日）**：
  - Spectrum-X CPO 交换机已全面量产（512 端口 × 200G，台积电 COUPE）。
  - Vera Rubin NVL72 把 72 颗 GPU 连成一个整体。
  - DSX Pod 用 7 个液冷机柜和 17 km Spectrum-X 线缆。
  - 推理侧发布 Nemotron 3.5 等模型。
  - **没有发布 OCS 相关产品**。
- **GTC 2026 春季（3 月）的规划**：
  - Rubin Ultra NVL576（2027 下半年）：机柜内铜，机柜间 CPO，组成两层全互联。
  - Feynman NVL1152（2028）：NVLink 8 CPO 交换机。
  - 黄仁勋的原话是 scale-up “铜和光都要”。
  - 推理走 AF 分离（attention 放 GPU、FFN 放 Groq LPU），KV cache 和激活要跨设备搬运。
- **解读**：
  - NVIDIA 先用 CPO 解决“扩域”，OCS 是下一步的“可重构层”。
  - AF/PD 分离让推理流量更结构化：哪些 attention 节点对接哪些 FFN 节点，按部署确定。这正好对应上文 A 类的静态 OCS 用法。
  - Cignal 判断 NVL576 会集成 OCS，目前只是分析师观点，需要跟踪 NVIDIA 的正式披露。

---

## 六、判断与建议

| 方向 | 判断 | 建议 |
|---|---|---|
| 训练 scale-out / 切片 / 备件池 OCS（MEMS） | 已规模商用，接下来比的是运维标准化和多厂商互通 | 跟踪 |
| scale-up 跨机柜 OCS（硅光、高基数、带增益） | 2027–2028 年随 CPO/NPO 进入 GPU 阵营；Google 8i 已证明推理也能用 | **重点关注** |
| 推理静态 OCS（Boardfly 类低直径拓扑、PD/AF 资源池） | 能降跳数、降时延，提升 $/token，落地门槛低 | **投资研究** |
| ns 级 OCS + 快速锁定光模块 + 通信库调度 | 推理集合通信内切换的唯一路径，三者缺一不可 | 投资研究（预研） |
| OCS 跨域 / 城域（OCS + OTN、OCS 网关） | 美团、中国电信、KDDI 已验证；随分布式训练和推理增长 | 跟踪 |

**要盯的指标**：
- 硅光 OCS 的基数（≥64/72）、插损（含连接器 ≤3 dB）、每 1U 端口数（≥256）。
- 光模块重锁定时间：从 ms 降到 µs。
- NCCL 等通信库是否原生支持 OCS 调度。
- NVIDIA 是否在 NVL576 或 NVL1152 中正式采用 OCS。
- Google 8i 的 OCS 端口规模。

## 来源

- 本地资料：ECOC 2026 讲稿笔记（B03、B15、B18、B21、B25、B42、B46、B48、B54、B55、B57、B77）；OCP 2026 笔记（P111、P136、P147、P345、P376、P421、P427、P430）；OFC 2026 论文全文（W2A.28、M3F.5、M3F.6、M4F.2、M4F.4、M3F.3、W2A.31、W2A.41、W4H.4、Th2A.35）。
- 网页：
  - [NVIDIA GTC Berlin 实时博客](https://blogs.nvidia.com/gtc-berlin-2026-news/)
  - [GTC Berlin 主题演讲转写（Investing.com）](https://www.investing.com/news/transcripts/nvidia-at-gtc-berlin-2026-keynote-europes-ai-buildout-93CH-4962500)
  - [The Register：NVIDIA 光 scale-up](https://www.theregister.com/2026/04/05/nvidia_optical_scale_up/)
  - [SemiAnalysis：Nvidia GTC 2026](https://newsletter.semianalysis.com/p/nvidia-the-inference-kingdom-expands)
  - [Cignal AI：OCS 市场 2Q26](https://cignal.ai/2026/07/optical-circuit-switching-market-2q26/)
  - [Google Cloud：TPU 8t/8i 技术解读](https://cloud.google.com/blog/products/compute/tpu-8t-and-tpu-8i-technical-deep-dive)
  - [Google：第八代 TPU](https://blog.google/innovation-and-ai/infrastructure-and-cloud/google-cloud/eighth-generation-tpu-agentic-era/)
  - [ServeTheHome：TPUv8 @ Hot Chips 2026](https://www.servethehome.com/googles-tpuv8s-for-training-and-inference-at-hot-chips-2026/)
