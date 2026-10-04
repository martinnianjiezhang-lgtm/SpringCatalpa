---
title: "NVIDIA × iPronics：硅光 OCS 用在 scale-up 还是 scale-out，推理还是训练"
tags:
  - OCS
  - 专题洞察
  - ECOC2026
date: 2026-10-01
---

版本 v1 · 2026-10-02

材料：ECOC 2026 现场讲稿，包括 iPronics 三场、NVIDIA、Salience Labs、Oriole、KDDI、Columbia、Cignal AI；公司公告与媒体报道。页码标注沿用〔讲稿简写 pN〕。

---

## 〇、先纠正一个事实：是参投，不是收购

- **交易性质：** 2026 年 9 月 2 日，iPronics 完成 1.25 亿美元 B 轮（约 1.076 亿欧元）。领投方是 Maverick Silicon 和 Light Street Capital，NVIDIA 是参投方。其他投资方有 Triatomic、Bosch Ventures、Catalight、欧洲创新委员会基金、Amadeus Capital、Criteria 等。iPronics 累计融资 1.77 亿美元。
- **没有披露的部分：** 公告没有提到 NVIDIA 的供货协议、参考架构纳入或采购承诺。
- **对比 NVIDIA 同年的其他光学布局：**
  - 2026 年 3 月向 Coherent、Lumentum、Marvell 各投 20 亿美元，并附多年采购承诺；
  - 以约 200 亿美元拿下 Groq 的技术与团队，推出 Groq 3 LPX。

  相比之下，iPronics 这一笔是期权型布局：花小钱锁定一条技术路线，不是收购整合。
- **iPronics 自身进展：**
  - 2026 年 3 月宣布在 Fabrinet 建专线（封装、组装、测试、认证），并拿到 10 家超大规模和 AI 集群 OEM 客户的首批订单；
  - 开设 Santa Clara 办公室；
  - 董事会新增前 Rambus CEO Geoffrey Tate 等人。

---

## 一、直接回答

**1. 应用层次：主攻 scale-up，scale-out 是次要市场。**

iPronics 宣传覆盖 scale-up、scale-out、scale-across 三层，但它的产品参数和 scale-up 最匹配：

- 单芯片 32 端口，下一代 64、72、144 端口；
- 亚毫秒重构；
- 每端口约 100 美元；
- 1U 可放 3–4 台。

Cignal AI 给出的 scale-up 所需端口数（radix）只有 64×64 或 72×72，并把硅光 OCS 评为 scale-up 的"Ideal"选项〔0921-MF-am-T02-1020-CignalAI p5, p12〕。iPronics 首页对第一场报告的定位就是"光交换用于 scale-up 扩展"〔0921-Mo3-A1-iPronics p1〕。

NVIDIA 自己在 ECOC 讲 OCS 的三个用途：灵活拓扑、"把故障变成重路由"、"解决 scale-up 前沿，把机架之外的铜换成光"〔0920-am-Su2-I-01-NVIDIA p10, p20〕。Next Platform 的分析也认为 NVIDIA 会把 OCS 放在 scale-up 内存语义网络的 spine 层，用 torus 或 dragonfly 拓扑替代全连接 fat-tree，而不是放进 scale-out 网络。

scale-out 的大端口 spine（300×300 到 512×512）是 MEMS 和液晶 OCS 的地盘，Google、Lumentum R300、Coherent DLX 已经在做。硅光的端口数短期内够不上。

**2. 推理还是训练：短期以推理为先，训练侧主要用于故障切换和阶段级重构。**

推理先落地，原因有四：

- **拓扑是静态的。** 推理框架在部署时就知道所有路由：MoE 的专家并行分组、LPU 的流水线切分、PD 分离的实例配比。OCS 按部署配置一次，长期不动，正好匹配亚毫秒重构能力〔0922-PF-1155-SalienceLabs p16〕。
- **通信在关键路径上。** 高交互 decode 是小 batch，计算和通信几乎不重叠，少一级电交换就直接省时延。单级电分组交换事务约 1,000 ns，两级约 1,600 ns，带宽本身只占约 25 ns〔0922-PF-1155-SalienceLabs p5, p6〕。
- **最直接的候选是 NVIDIA 自己的 Groq 3 LPX。**
  - 每机架 256 颗 LPU；
  - 芯片间 RealScale C2C 由编译器静态调度，没有硬件仲裁和自适应路由，包里也不带源/目的地址；
  - 每颗 LPU 有 96 条 112 Gb/s 链路，机架内 scale-up 带宽 640 TB/s。

  这类"确定性、点到点、静态"的连接，扩到机架之外时天然适合电路交换。The Register 的报道也指出，iPronics 特别适合流水线并行的 LPU 部署。
- **推理 scale-up 域小，端口数对得上。** 64–256 卡的推理域和 OCS 芯片的 32–144 端口在同一量级。

训练侧的用途主要有三种：

- **GPU 故障切换：** 把链路切到备用 GPU 或机架，iPronics 官网把它列为独立用例；NVIDIA 说的"把故障变成重路由"也是这个意思。
- **作业或训练阶段之间的拓扑重构：** 剑桥的训练阶段感知 OCS 让通信快 37.5%〔OFC26 M3F.5〕；Columbia 称注入带宽超过 1600 GBps 时，一次性重构就够用〔0924-推定F3-哥伦比亚大学 p14〕。
- **在计算阶段的零流量窗口内切换：** KDDI 实测 GPU 计算阶段有 100–400 ms 零流量窗口，周期性切换稳定，随机切换会中断训练〔0921-Mo3-A3-KDDIResearch p13〕。

训练中真正最重的 TP/EP all-to-all 仍要靠全连接的 NVLink 分组交换。NVIDIA 自己的路线是 NVLink 交换机 + CPO（Rubin Ultra NVL576 两层全连接、Feynman NVL1152），OCS 替代不了这一层。

**3. 判断：**

- **2026–2027：** 推理集群试点（LPU 和推理型 ASIC 机架之间的扩展、静态 MoE 推理 pod）加上训练集群的故障切换。
- **2027–2028：** 随 72/144 端口芯片和 scale-up 光化（NPO/CPO）进入机架间 scale-up spine。

---

## 二、iPronics 技术剖析

### 2.1 芯片代际

| 代际 | 端口 | 集成开关单元 | 芯片面积 | 特点 | 时间 |
|---|---|---|---|---|---|
| 初代 | 32×32 | 约 2,000 | 20×23 mm² | — | 已有 |
| v2 | 32×32 | 约 4,000 | — | 偏振透明 | 已投产（ONE-32） |
| 下一代 | 64×64 | 约 6,000 | 20×23 mm² | 偏振透明 | — |
| 再下一代 | >100（媒体称 72、144） | 约 10,000 | 25×25 mm² | — | 2027 年，设计中 |

来源：〔0921-Mo3-A1-iPronics p10〕。媒体口径为"正在推出 72 端口和 144 端口芯片"，单个 1U 最多 720 对端口。

### 2.2 ONE-32 关键指标

- **交换结构：** 严格无阻塞 32 端口、偏振透明、超过 4,000 个开关单元、兼容 WDM、片上遥测〔0924-推定F4-iPronics p18〕。
- **损耗与增益：** 各通道约 10 dB 损耗，用片上 SOA 阵列补偿，增益 8–12 dB，即"增益受控 OCS"〔0921-Mo3-A1-iPronics p9〕〔0920-am-Su2-I-03-iPronics p11〕。
- **基础器件：** O 波段标准硅光工艺。3 dB 分路器插损 0.060–0.104 dB，交叉 0.014–0.016 dB，称比代工厂标准器件库好 10 倍〔0920-am-Su2-I-03-iPronics p7, p8〕。
- **链路实测：** 与 Lumentum 1.6T 2×DR4（200G/lane）带 retimer 的硅光收发器联测，OCS 增益设 10 dB，前后网络损耗模拟 0–3 dB 和 0–10 dB。pre-FEC BER 相对 1e-12 基线只劣化约 1 个数量级，自称"业界首次"〔0921-Mo3-A1-iPronics p14〕〔0924-推定F4-iPronics p21〕。
- **功耗：** 系统 30 W，加每个激活通道 0.78 W。作为对比，64×1600G 电交换机约 3500 W；iPronics 目标低于 100 W，2027 年低于 150 W〔0920-am-Su2-I-03-iPronics p13〕。
- **成本与体积：** 链路成本降低 2 倍；比现有 3D 光学 OCS 紧凑 20 倍；成本效益高 3–5 倍〔0924-推定F4-iPronics p4〕〔0921-Mo3-A1-iPronics p15〕。
- **重构速度：** 资料写法不统一，有"亚毫秒""µs 级""切换 300 ps"三种。300 ps 指单个开关单元，系统级以亚毫秒为准〔0920-am-Su2-I-03-iPronics p11, p14, p16〕。
- **软件：** gNMI/YANG 和 Python API。NCCL 集合通信库、编排器、SDN 控制器的支持仍在开发〔0920-am-Su2-I-03-iPronics p3〕。

### 2.3 为什么 iPronics 主张"扁平 OCS scale-up"

iPronics 比较了三种 scale-up 拓扑，功耗从高到低依次是：

1. 机架内电交换 + CPO，机架间 OCS；
2. 扁平电交换；
3. 扁平 OCS。

逻辑是每少一次光电转换就省一次 SerDes 和交换芯片的功耗〔0920-am-Su2-I-03-iPronics p2, p3〕。这和 Meta、Credo 的判断一致：链路功耗主要由 SerDes 决定。

---

## 三、和 NVIDIA 架构的对接点

### 3.1 NVIDIA scale-up 的演进路线（公开口径）

| 代际 | scale-up 域 | 互连形态 |
|---|---|---|
| Blackwell / Vera Rubin | NVL72 | 机架内铜背板，NVLink 6 每 GPU 3.6 TB/s |
| Rubin Ultra（Kyber 机架） | NVL144 / NVL576 | NVL576 用 CPO NVLink 交换机连 8 个机架，组成两层全连接 |
| Feynman（2028） | 最高 NVL1152 | NVLink 8 CPO 交换机，原生光 NVLink |
| Groq 3 LPX（2026-08 量产） | 每机架 256 LPU | RealScale C2C，编译器静态调度、点到点 |

NVIDIA 在 ECOC 讲的 scale-up 约束〔0920-am-Su2-I-01-NVIDIA p8〕：

- GPU 带宽每两年翻倍（2.4→3.6→7.2 Tb/s）；
- GPU 域每两年 2–4 倍（8→32→72→数百）；
- 机架功率 25 kW→150 kW→1 MW；
- GPU 到第一级交换机的距离从 0.5 m 到最长 30 m，"铜到了极限"。

### 3.2 OCS 可能嵌入的四个位置

| 位置 | 需求 | 与 iPronics 的匹配度 | 竞争方案 |
|---|---|---|---|
| A. 推理机架间扩展（LPX、推理型 ASIC pod） | 点到点、静态、低时延，64–256 端口 | 高：端口数、静态拓扑、免一级电交换都对得上 | NVLink 交换机 |
| B. scale-up spine（多机架 NVLink 域的 torus/dragonfly） | 机架间 64–144 radix，确定性时延 | 中高：取决于 72/144 端口芯片和 NPO/CPO 进入 scale-up | CPO NVLink 交换机（NVIDIA 自有路线） |
| C. 故障切换和备用机架 | 低频切换、可编程、遥测 | 高："把故障变成重路由"是 NVIDIA 明确说的用途 | 人工跳线、冗余交换 |
| D. scale-out spine（Spectrum-X） | 256–512 radix、大爆炸半径 | 低：端口数不够 | MEMS（Lumentum R300 300×300）、液晶（Coherent DLX 64–512） |

### 3.3 NVIDIA 列出的四道门槛和 iPronics 的回应

| NVIDIA 门槛〔0920-am-Su2-I-01-NVIDIA p18〕 | iPronics 的回应 | 还没解决的部分 |
|---|---|---|
| 插损：路径至少 4 个 bulkhead 连接器，DR4 余量只有 3 dB、FR4 4 dB | 片上 SOA 增益 8–12 dB 补偿约 10 dB 交换损耗，1.6T BER 只劣化 1 个数量级 | SOA 噪声和非线性在多跳、WDM 多波长下的累积；高温下的增益稳定性 |
| 成本：每 1RU 超过 256 个双工端口 | 每端口约 100 美元；1U 放 3–4 台，媒体称每 RU 最多 720 对端口 | 72/144 端口芯片尚未量产（2027） |
| 可靠性：故障半径、FIT，不能吃掉 FEC 余量 | 固态、无运动部件；片上监测 PD 和遥测 | 缺现场 FIT 数据；SOA 和热光单元的长期老化 |
| 端口密度：每机架需要上千个 OCS 端口 | 多芯片堆叠到每 RU 数百端口 | 光纤管理和连接器良率（EBO MSA 算过 1088 根光纤时首过良率只有 23%） |

---

## 四、训练和推理的适配对比

| 维度 | 推理（decode、MoE、LPU 流水线） | 训练（TP/EP/DP/PP） |
|---|---|---|
| 流量模式 | 按部署静态：EP 分组、流水线切分、PD 配比固定 | 随迭代变化：每层 all-to-all（EP）、AllReduce（TP/DP） |
| 所需重构频率 | 小时、天或部署级 | 若在集合通信内切换，需 <700 ns 或高扇出〔OFC26 W2A.28〕；阶段级为 100–400 ms 窗口 |
| 时延敏感度 | 极高：通信在关键路径，少一级电交换省约 600 ns | TP/EP 高；DP/PP 可重叠 |
| 端口规模 | 64–256（单推理域） | 数千到数十万（scale-out） |
| OCS 价值 | 省交换机和收发器、降时延，转化为 \$/token | 故障切换、拓扑适配、降网络功耗 |
| 主要竞争者 | NVLink 交换机（全连接，但多一跳） | NVLink + CPO（scale-up）、Spectrum-X（scale-out） |
| 适配结论 | 首选场景 | 辅助场景（故障切换、阶段级重构） |

Salience Labs 的仿真数据也支持这个排序：

- 512 XPU 的 all-reduce，OCS 完成时间比电交换快 58%–61%；
- all-to-all 在全部消息尺寸上 OCS 都更低（小消息约 1.5 µs 对约 2.5 µs）。

但 Salience 同时承认，"全 OCS 架构需要 NPO/CPO"，带光链路的 scale-up 交换机要到 2027 年〔0922-PF-1155-SalienceLabs p7, p10, p13〕。

---

## 五、OCS 技术路线对比

| 路线 | 代表 | 端口 | 重构时间 | 适用 |
|---|---|---|---|---|
| MEMS 自由空间 | Google（自研）、Lumentum R300 | 256–320 | 约数十 ms | scale-out spine、TPU pod 重构；Google 报告功耗 -40%、成本 -30%、吞吐 +30% |
| 液晶 | Coherent DLX | 64–512 | ms 级 | scale-out，部分 scale-up |
| 硅光热光 + SOA | iPronics ONE | 32→64→72/144 | 亚毫秒 | scale-up 扩展、推理 pod、故障切换 |
| 薄膜钽酸锂电光 | OneTouch（8×8 样机） | 8 | <4 ns | 远期包级交换；插损 8.6 dB 偏高 |
| 无源波长路由 + 快速重锁定收发器 | Oriole PRISM | 系统级 | ns 级（瓶颈在收发器重锁定） | 全光无分层网络（自报，32k GPU 网络功耗 -81%） |

Oriole 指出一个关键约束：OCS 系统的有效吞吐取决于"交换时间 + 收发器重锁定时间"。用标准收发器时，就算交换只要 ns 级，吞吐也低于 1%〔0920-pm-Su3-A-04-Oriole p9〕。这也说明亚毫秒级的 iPronics 只适合低频重构，也就是推理部署、故障切换、训练阶段切换，不适合包级或集合通信内的切换。

---

## 六、风险与观察点

1. **SOA 增益方案的可靠性。** 增益补偿是硅光 OCS 能进 DR4 链路预算的前提，但 SOA 的 ASE 噪声、偏振相关增益、温漂和老化会直接影响 FEC 余量和 FIT。目前只有实验室 BER 数据，没有现场数据。
2. **端口数时间线。** 72/144 端口芯片要到 2027 年。在那之前，32/64 端口只够小规模推理 pod 和故障切换。
3. **软件栈。** NCCL、编排器、SDN 控制器支持仍在开发。推理框架（如 Dynamo）能否在部署时直接下发 OCS 配置，是推理场景落地的关键。
4. **NVIDIA 自有路线的挤压。** NVLink CPO 交换机（NVL576/NVL1152）覆盖了训练 scale-up 的全连接需求。OCS 在训练侧可能只停留在故障切换这个辅助角色。
5. **竞争路线。** Lumentum 和 Coherent 有 NVIDIA 各 20 亿美元投资和采购承诺。如果它们的 MEMS 或液晶 OCS 做出低端口数、低成本版本，会直接挤压 iPronics 在 scale-up 的位置。
6. **生态标准。** CW-WDM MSA、OCI MSA 的波长数和栅格还没定，OCS 要对 WDM 透明〔0921-Mo3-A1-iPronics p15〕。

---

## 七、对光通信产业的含义

- **OCS 的主战场从 scale-out 向 scale-up 延伸。** Cignal AI 估计 2026 年 OCS 市场超过 20 亿美元，2030 年超过 80 亿美元，scale-up（GPU）是下一个杀手级应用，并且和 CPO 绑定〔0921-MF-am-T02-1020-CignalAI p16〕。
- **硅光 OCS 拉动 O 波段 SOA 和高功率 CW 光源。** 增益受控 OCS 需要 O 波段 SOA 阵列。如果推理 pod 大量采用，SOA 会成为继外置光源之后又一个 InP 器件增量。
- **收发器形态。** OCS 链路要求收发器对额外损耗和重连更宽容。LPO 经过 OCS 后 pre-FEC BER 没有数量级变化，链路建立约 5.2 ms，比带 DSP 的约 6.2 ms 更快〔0921-Mo3-A3-KDDIResearch p7, p10〕。推理集群里 LPO/NPO 加 OCS 的组合值得跟踪。
- **对 NVIDIA 生态的判断。** NVIDIA 用参投保留硅光 OCS 这个选项，同时把主路线押在 CPO NVLink 交换机上。iPronics 能否进入 NVIDIA 参考架构，关键看 2027 年 72/144 端口芯片，以及它在 LPX 类推理机架间扩展上的实测。

---

## 来源

**本地（ECOC 2026）：**
- 0920-am-Su2-I-03-iPronics（DAY1/PV-R-Su1-Su2）
- 0921-Mo3-A1-iPronics（DAY2/Mo3-A）
- 0924-推定F4-iPronics（DAY5/Th1-F）
- 0920-am-Su2-I-01-NVIDIA
- 0922-PF-1155-SalienceLabs
- 0920-pm-Su3-A-04-Oriole
- 0921-Mo3-A3-KDDIResearch
- 0924-推定F3-哥伦比亚大学
- 0921-MF-am-T02-1020-CignalAI
- 论文：OFC 2026 M3F.5、W2A.28

**网络：**
- The Register，Nvidia joins investment into iPronics：https://www.theregister.com/networks/2026/09/02/nvidia-joins-investment-into-ipronics-to-build-out-optical-circuit-switching-ocs-tech/5293764
- Converge Digest，iPronics Raises \$125M：https://convergedigest.com/ipronics-raises-125m-silicon-photonics-ocs-ai-data-centers/
- iPronics 官网：https://ipronics.com/
- EU-Startups 融资报道：https://www.eu-startups.com/2026/09/spains-ipronics-raises-e107-6-million-with-nvidia-backing-to-scale-optical-networking-for-ai-data-centres/
- Next Platform，Nvidia Sees The Light On Silicon Photonics And Maybe Optical Switching：https://www.nextplatform.com/connect/2026/03/02/nvidia-sees-the-light-on-silicon-photonics-and-maybe-optical-switching/4093099
- NVIDIA Groq 3 LPX：https://www.nvidia.com/en-us/data-center/lpx/ ；https://www.storagereview.com/news/nvidia-groq-3-lpx-enters-full-production-3400-tokens-per-second-at-100k-context-256-lp30s-per-rack
- NVIDIA 路线图（NVL576/NVL1152、scale-up CPO）：https://www.hpcwire.com/2026/03/17/huang-shares-nvidia-roadmap-showing-more-chips-nvl1152-scale-up-cpo/
- NVIDIA–Groq 交易：https://www.cnbc.com/2026/08/24/nvidia-says-groq-racks-will-be-online-this-year-after-20-billion-deal.html
