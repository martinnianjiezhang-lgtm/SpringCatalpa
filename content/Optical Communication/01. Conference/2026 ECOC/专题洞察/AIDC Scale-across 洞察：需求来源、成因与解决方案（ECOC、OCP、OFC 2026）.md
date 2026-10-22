---
title: "AIDC Scale-across 洞察：需求来源、成因与解决方案（ECOC、OCP、OFC 2026）"
tags:
  - ScaleAcross
  - DCI
  - AIDC
  - ECOC2026
  - OCP2026
  - OFC2026
  - 专题洞察
date: 2026-10-22
---

> [!info] 资料与口径
> - **ECOC 2026**：Scale-across 方向综合底稿与现场讲稿，包括 Ciena、Google、Microsoft Azure、Cignal AI、Marvell、Nokia、Acacia、华为、中兴、中国电信、KDDI、领纤、Corning 等。
> - **OCP 2026**：Scale Across 专场 24 份讲稿 + 6 场视频转写，包括 Meta、Microsoft、Google、Alibaba、Oracle、OpenAI、Ciena、Cisco、Broadcom、Arista、NTT 等。
> - **OFC 2026**：相关论文 53 篇，重点是中兴/长飞 600 km 跨 AIDC 训练、KDDI OCS 网关、空芯光纤（HCF）系列、Coherent-Lite 器件。
> - 标“自报”的是厂商宣称；标“仿真”“预测”的不是现网数据。

**Scale-across 指什么**：把分布在多栋楼、多个园区乃至多个城市的数据中心，连成一个逻辑上的 AI 训练或推理集群。它介于 scale-out（单楼后端网络，<2 km）和传统 DCI/骨干之间，距离从几百米跨到上千公里。

## 结论先行

1. **根本原因是电力，不是网络偏好。** 单个数据中心只能拿到 50–300 MW，下一代训练集群要 1–5 GW 以上，新站点并网要 3–7 年（Microsoft）。Microsoft 的结论是，算力只能分散到多个站点，多站点训练“不是可选项”。
2. **需求量级是“光纤对”，不是“波长”。** 一对训练园区之间的容量，相当于 2020 年前后整个前端区域的约 14 倍（Ciena）。DC 间同步流量已比用户流量大一个数量级（Meta）。Cignal 预测，scale-across 占云可插拔带宽的比例将从 2025 年的 5% 升到 2030 年的 72%。
3. **距离分层已收敛。** <3 km 用灰光 FR，<10 km 用 LR，>10 km 用相干 DWDM；120–150 km 以内不用中继，再往外加中继（ILA）到 500–1,000 km。2–10 km 是 O 波段 Coherent-Lite 和 IM/DD 的争夺区。
4. **解决方案是“六层叠加”。** 光模块（800ZR+ → 1600ZR、Coherent-Lite）、线路系统（多 rail、全谱转发器 FST、光保护）、光纤（C+L/S+C+L、多芯、空芯）、光交换（OCS 网关）、网络协议（深/浅缓冲、亚 RTT 拥塞控制、SRv6）、训练框架（TP/EP 留在 DC 内，PP/DP 跨 DC）。没有单一技术能解决。
5. **价值从模块转向线路系统。** Cignal 预测，2030 年 scale-across 支出 87 亿美元，线路系统占 55%（2025 年为 32%）。Google 称光模块功耗十年降了约 90%，但线路系统功耗不变，已占约一半。

---

## 一、需求来源：谁在要、要多少

### 1.1 四类需求方

| 需求方 | 需求内容 | 代表数据 |
|---|---|---|
| **超大规模训练** | 单个模型的训练集群超出单楼、单园区 | Meta Prometheus 1 GW，跨传统楼宇、户外帐篷和相邻托管设施（现网）；Meta 集群从 24K（单楼）→ 129K（多楼，2024）→ 多区域（2025+）；Google 宣布 Vera Rubin 集群跨多站点扩到 96 万 GPU（GTC Berlin） |
| **区域资源池化** | 存储与算力分区部署，“副本变算力” | Meta RBB 把 1/5/10 ms RTT 内的区域编成 Ring，Ring 内容量是 Ring 间的 10 倍；首个试点区域释放数 MW 电力（自报） |
| **云边界外扩** | 超大云租用 NeoCloud 的 GPU，数据和服务留在云内 | Microsoft Tier0-Edge：256K 个 VXLAN 隧道、MACsec 长距 400/800GbE（自报） |
| **分布式推理** | KV cache、PD 分离、边缘推理跨站点 | 70B 模型 4K 上下文、40 ms 首 token 时延，跨站传 10.74 GB KV 需 2.1 Tb/s，是训练假设的 429 倍（建模）；NTT IOWN APN 做跨站 PD 分离 |

### 1.2 需求量级

| 维度 | 数字 | 来源 |
|---|---|---|
| 单站电力 | 传统 50–300 MW；下一代 1–5 GW+；并网 3–7 年 | Microsoft（OCP） |
| 已宣布容量 | 约 190 GW 超大规模容量 | Nokia（ECOC） |
| 园区结构 | 每个 AI 园区 4–12 栋楼，园区间隔 2–40 km | Nokia（ECOC） |
| 园区间容量 | 约为 2020 年前端区域的 14 倍；过订比 >8:1 | Ciena（OCP，看图） |
| 楼间带宽 | 数十到数百 Pb/s，约 2×(6,250–62,500) 个 1.6T 模块，平均光纤距离 <2 km | Google（OCP，研究设计） |
| 系统规模 | 每站数百对光纤 × 64×800G = 20 Pb/s；传统 DCI 约 200 Tb/s → scale-across >10 Pb/s | Ciena、华为 |
| 带宽估算 | 数据并行（DP）跨站：GPT-4 级 1.8T 模型在通信可与计算重叠时需 >3.1 Tb/s，不重叠时 62–309 Tb/s；10T 模型最高 1.7 Pb/s | 中兴（仿真） |
| 端口量 | Meta 10 km 以上两端各“数万个 800G ZR”；800ZRx 全球已出货 >10 万端口（2Q26），某超大规模预测 2027 年 >35 万 | Meta、Cignal |
| 光纤总量 | Meta DC 内 >1,000 万根光纤，DC 间 >400 万根 | 引用 Meta（OCP） |
| 市场 | 相干模块 2026 年近 70 亿美元、2030 年近 100 亿；1600ZRx 2030 年 29 亿美元，成为最大单一类别 | Cignal |

---

## 二、成因：为什么必须 scale-across

| 原因 | 机制 | 证据 |
|---|---|---|
| **1. 电力** | 单站拿不到 GW 级电力，并网周期 3–7 年，远慢于算力需求（约 5 个月翻倍） | Microsoft；Ciena 称客户选址“电力第一”，园区宣称的功率是终态额定值、不是第一天可用 |
| **2. 建设速度** | 等不及新建 GW 园区，只能把现有楼宇、帐篷、托管站点和租用的 NeoCloud 拼起来 | Meta Prometheus 用帐篷；Meta RBB 从立项到首站 5 个月 |
| **3. 楼宇面积与散热** | 单楼的面积与功率预算限制了 scale-out 规模，Google Virgo 后端限于单楼 | Google（OCP） |
| **4. 模型规模** | 单个副本已超出单楼；Cisco 称“当前模型已到单数据中心可训练的极限” | Cisco（引自 OFC 执行论坛） |
| **5. 可用性与弹性** | 多站点提供故障域隔离和资源调度弹性；但光纤可用率只有约 97.7%，单次故障就会暂停训练 | Microsoft |
| **6. 推理分布化** | 推理靠近用户与数据，KV cache 和 PD 分离带来新的跨站流量 | NTT、Microsoft |

**距离的物理上限**：光纤时延约 5 µs/km，与带宽无关。网卡升到 400G–1.6T 后，串行化时延变小，光纤时延成为数据并行能否与计算重叠的主导因素（Corning 仿真）：
- 10 km 以内重叠效率接近 1。
- H100 从约 10–30 km 开始下降，A100 从约 100 km 开始下降。
- 1,000 km 时，175B 模型、8,192 卡 H100 的训练时间约为基线的 26 倍；换成空芯光纤可降到约 17 倍。

所以 scale-across 的距离越远，越要靠并行切分和协议层优化，而不只是加带宽。

---

## 三、距离分层：各家口径已收敛

| 距离 | 光层方案 | 网络特征 | 代表口径 |
|---|---|---|---|
| **<3 km**（楼间、同园区） | 灰光 IM/DD（FR/DR），可加 OCS | 浅缓冲，可轻过订 | Meta 楼 1–4；Google 园区 <2 km |
| **3–10 km**（扩展园区） | LR；400G/lane 超过 2 km 后转 O 波段 Coherent-Lite | 浅缓冲 | Meta 楼 5–6；Marvell 2–10 km 用 CL |
| **10–150 km**（near，不用中继） | C 波段 800ZR/ZR+ + DWDM，C+L 满配点对点 | 深缓冲或浅缓冲 + ECN | Ciena <150 km 为 near；Cisco/Meta 120–150 km 不用中继 |
| **150–1,000 km**（far，加中继 ILA） | ZR+ / 高性能转发器 + 线路系统 | RTT 1–10 ms，长 RTT 拥塞控制 | Meta RBB 跑到 650 km；Ciena 称客户训练距离从约 100 km 走向 500–1,000 km |

口径差异：Meta 按光模块能力和 RTT 划分，Ciena 按是否需要中继，Google 按园区直径，Broadcom 按拓扑域。Ciena 提议把 scale-across 的定义捐给 OCP 标准化，目前还没有统一定义。

---

## 四、解决方案：六层叠加

### 4.1 光模块层：相干下沉，按距离选引擎

| 方案 | 进展 | 关键数据 |
|---|---|---|
| **800ZR/ZR+ 可插拔** | 现网主力 | Meta 全网 400ZR+ → 800ZR+ 升级完成；Acacia 自报累计 >75,000 个；ZR+ 直插路由器相比转发器方案能耗 -90%、CAPEX -66%（引用 ACG） |
| **1600ZR/ZR+** | 样品与初期部署（2026），放量在 2027 | 1600ZR 约 236 GBd，1600ZR+ 252 GBd 约 1,000 km；OSFP 功耗 34–42 W（2027 预测）；要求与 400/800ZR 代际互通（Meta） |
| **Coherent-Lite（O 波段）** | OIF 立项，演示阶段 | 频谱效率是 IM/DD 的 4 倍，2 nm 低功耗 DSP，低时延 FEC（BCH 类 49–55 ns，不用 OFEC）；OFC：McGill BTO 调制器 2 km 净 1 Tb/s/λ，Ciena TFLN 光 DAC 10 km 1.2 Tb/s 免驱动 |
| **形态** | 风冷逼近天花板，向液冷分流 | Google：1.6T ZR++ 风冷上限约 45 W；12.8T 液冷 XPO：ZR 300 W/24 pJ/bit，CL 250 W/20 pJ/bit（自报） |

### 4.2 线路系统层：从“开一个波长”到“开一整条光纤”

| 方案 | 收益（多为自报） |
|---|---|
| **光保护 + 可插拔** | Meta：多数情况下终端 IP 端口和转发器减半；光层先于包层倒换 |
| **多 rail 线路系统** | Ciena Hyper-Rail：20 Pb/s 用例从 22 个放大小屋降到 1 个，每机架 4 → 128 条 rail；Cisco Open Transport 3000：功耗 -75%、空间 -80%；Google：每站一个 ILA 机房，功耗约 -80% |
| **全谱转发器 FST** | Ciena：16 对光纤时被管设备 192 → 32，功耗约 -50%；华为：C96 25.6T/纤，C+L 51.2T/纤；Alibaba：C 波段 25.6 Tb/s/纤 |
| **高性能转发器** | Ciena WL6：城域 76.8 Tb/s，比 64×800G 可插拔高 50%；场景切分是“频谱效率优先选转发器，功耗与空间优先选可插拔” |
| **OTN** | 中兴/长飞：16λ×800G OTN 支撑 600 km 跨 AIDC 训练（OFC W4H.5） |

**新约束**：Ciena 估计 ILA 站点功率从 30–50 kW 升到 400 kW，站点供电最高 4 MW；线路部件交期 12–18 个月，受 InP 晶圆产能限制。

### 4.3 光纤层：三条扩容路径并行

| 路径 | 进展 |
|---|---|
| **单波提速** | 1.6T/λ，缓解光纤数量危机（Nokia） |
| **频谱扩展** | C+L 满配是现网标准；中兴 19.1 THz S+C+L 单纤节省光纤 74.8%；中国移动/中兴/长飞实时 134 Tb/s、75 km、全 1.2T 通道（OFC W3J.1） |
| **空间复用** | 多芯光纤：Sumitomo 4 芯，SDM4 MCF MSA 1.0（2026-09）；KDDI 12 芯可让 25 个集群全互联 |
| **空芯光纤 HCF** | 进展：<br>- Azure：64×400G ZR 跨三跨 427.97 km（记录）。<br>- 领纤：0.052 dB/km。<br>- 长飞：10.9 km 上 550 Tb/s（单芯记录）。<br>- 华中科大/长飞：150 km 单跨全双工 ZR+。<br>- 中国电信：熔接 0.05 dB、97 s。<br>- Alibaba：CO2 吸收的一次性现场标定。<br><br>约束：价格 >$3,000–5,000/km（SMF $20–40/km）；累计产量约 83 km；OTDR 和熔接生态未成熟。 |

### 4.4 光交换层：OCS 进入跨楼与跨集群

- **KDDI OCS 网关**：用 SDM + WDM + OCS，在多个集群间构成逻辑全连接，同时减少布缆。集群间延伸 20–40 km 时，作业完成时间几乎不变；RDMA 时延只按光纤传播增加（ECOC Tu1-G1、OFC W4H.3）。
- **Google**：研究用 OCS 替代园区 spine，楼间配 1.6T Coherent-Lite、被动复用（研究设计，非承诺）。
- **中国电信**：OCS 替代 super-spine，故障率降 17% 以上，网络功耗约降 20%（自报）。
- **Nokia**：纯光纤交换配 800ZR+，可以用更紧的信道间隔（OFC W3A.3）。
- **Oracle/Lumentum**：1,000 台 OCS 插损中位 1.2–1.4 dB，落在 ZR/ZR+ 11 dB 以上的预算内。

### 4.5 网络与协议层：长 RTT 是最大难点

| 问题 | 方案 | 状态 |
|---|---|---|
| **长距下的缓冲** | 深缓冲派：Broadcom/Arista 仿真要求 ≥1.5×BDP（带宽×往返时延），100T 交换机 10 km 需约 1.9 GB、100 km 需约 18.8 GB；Meta BAG 用 J3 深缓冲承载跨站无损 RoCE。浅缓冲派：Meta RBB 用浅缓冲 + ECN + 自研 GLIDE，在 650 km 跨度现网运行，常态只用约 7% 缓冲 | 两派并存，差别来自流量类型 |
| **拥塞反馈太慢** | 反应式信号最快一个 RTT，而很多同步流比一个 RTT 还短。Broadcom BTS 由拥塞点直接回送发送端，约 10 µs，对比端到端约 1,000 µs；UEC 已有工作组 | 规范编写中 |
| **传输层** | MetaRoCE 把 scale-across 当作长 RTT 场景（RTT 1.5 ms、拥塞窗口 3,500–7,000）；OpenAI/Microsoft 的 MRC 多路径；华为 OTN-Proxy 做 RDMA 代理，称吞吐与距离（0–500 km）基本无关 | MRC 现网；其余自报 |
| **路径控制** | SRv6 成为 DC、DCI、骨干共用机制：Meta RBB（64 个并行平面）、Alibaba eCore（按作业做流量工程）、OpenAI 后端 | 现网 |
| **物理层无损** | Ciena 提议标准化“可证无损”物理层，post-FEC BER 1e-24；Alibaba 光模块检测 BER 超门限后把路径移出 ECMP 组（自报） | 提议 |
| **开放管理** | Alibaba SONiC for OTN；SAI 扩到 OTN、OCS；OIF CMIS；Meta 要求开放线路系统与代际互通 | 进行中 |

### 4.6 训练框架与调度层：把对时延敏感的流量留在 DC 内

**切分原则**：TP/EP 流量大、对时延极敏感，留在单个 DC 的 scale-up 和 scale-out 内；PP 和 DP 的流量对时延不那么敏感，可以跨 DC，并与计算重叠。Meta 把模型副本放在一个 L2 fabric 内，跨副本的 DP AllReduce 走 BAG，并按这个反推 BAG 容量。

**实测（规模仍小）**：

| 来源 | 距离与规模 | 结果 |
|---|---|---|
| 中兴/长飞（OFC W4H.5） | 600 km，1,024 GPU，LLaMA2-70B，16λ×800G OTN | DP 效率下降 <5%，PP 下降 <1% |
| 中国电信（ECOC） | 3 个跨城 DC，1,024 GPU | 训练效率 >97% |
| 美团（ECOC） | 100 km，OCS + OTN，8:1 收敛 | PP 流量 100.01%，DP 106.78%，EP 最坏 121.22% |
| KDDI（ECOC/OFC） | 20–40 km，4 个集群 | 作业完成时间几乎不变 |
| NTT（OCP） | 40 km | 训练时间 +1.9%；100 km 内 <10% |
| 华为（ECOC） | 实网，首末层本地、中间层云端 | 部分场景算力损失 <5% |

**缺口**：目前公开实测都在 1,024 GPU、600 km 以内。十万卡级、上千公里的效率数据，只有 Corning 的仿真。

---

## 五、主要玩家路线

| 玩家 | 路线 |
|---|---|
| **Meta** | 现网最领先：Prometheus 1 GW 多站；800ZR+ 全网；BAG（深缓冲、跨站后端）+ RBB（浅缓冲、SRv6、650 km）；光保护；要求开放线路系统和代际互通 |
| **Google** | 多 rail 线路系统（每站单 ILA 机房）；研究 OCS 园区 spine + 1.6T Coherent-Lite；主张可插拔“二值化” |
| **Microsoft** | 电力论证；空芯光纤先行（Azure 427.97 km 记录）；NeoCloud 扩展；光模块 SKU 收敛（“Less is more”） |
| **Alibaba** | 按业务分设专用 eCore（SRv6 + Silicon One + SONiC）；FST 25.6T；SONiC for OTN；HCF 现场标定 |
| **Oracle** | 区域 DWDM 约 60 km 跨段，400ZR → 1600ZR；1.6T 相干 MACsec；OCS 零接触运维 |
| **NVIDIA** | Spectrum-XGS 以太网连接分布式 DC（OFC M3F.6 引用） |
| **Ciena** | FST + Hyper-Rail + WL6；2×1.6T CL OSFP 与 12.8T CL XPO；推动 scale-across 定义与无损物理层标准 |
| **Cisco** | 1600G ZR+；Open Transport 3000 多 rail；P200 深缓冲路由器 |
| **华为** | 四件套：FST、OCS、HCF、OTN-Proxy；“算网一体” |
| **中兴 / 长飞** | 600 km 跨 AIDC 训练现场试验；S+C+L 宽带；HCF 系列记录 |
| **中国电信** | 跨城 3 DC 训练 >97%；OCS 替代 super-spine；WSON 50 ms 保护 |
| **Broadcom / Arista** | 深缓冲（Jericho + HBM）；BTS 亚 RTT 反馈 |
| **DSP 厂商**（Acacia、Marvell、Nokia） | 800ZR+ 份额 Acacia 领先；1.6T（2 nm）、MACsec、园区低时延 FEC 是新一轮竞争点 |

---

## 六、判断与建议

| 方向 | 判断 | 建议 |
|---|---|---|
| 800ZR+ → 1600ZR/ZR+ 可插拔 | 2026–27 年 800ZR+ 仍是主力，1600ZR 放量取决于 2027 年的功耗（<45 W）与 $/G（<$5/G） | **重点关注** |
| 多 rail 线路系统 / FST / 光保护 | 价值重心，线路系统支出占比 32% → 55%；泵浦与放大器产能是 2027 年前的瓶颈 | **重点关注** |
| O 波段 Coherent-Lite（2–20 km） | 园区是最大增量区间；与 IM/DD 光域均衡的竞争在 400G/lane 定胜负 | **投资研究** |
| 长 RTT 网络与协议（深缓冲芯片、BTS、多路径 RDMA、SRv6） | 决定跨站训练效率上限，芯片与软件机会大于光 | **投资研究** |
| 跨 DC 训练框架与实测 | 1,024 GPU / 600 km 已验证；十万卡级、千公里级是 2027 年前的判断点 | **重点关注** |
| 空芯光纤 HCF | 时延价值明确，但价格和产量差 2 个数量级，12–24 个月内选择性部署 | 跟踪 |
| OCS 网关、多芯光纤 | 减少布缆和交换层级，园区和跨集群的选配项 | 跟踪 |

**要盯的指标**：
- 1.6T ZR/ZR+ 实测功耗与 $/G。
- FST 与多 rail 的现网站点数。
- 跨 DC 训练在 >1,024 GPU、>600 km 的效率。
- Coherent-Lite 1600CL 的波特率与 FEC 定案。
- HCF 单价与年产量。
- UEC BTS 与 OCP scale-across 定义的标准进度。

## 来源

- ECOC 2026：Scale-across 综合底稿（方向 2），讲稿包括 Cignal AI、Ciena、Google、Microsoft Azure、Marvell、Nokia、Acacia、华为、中兴、中国电信、KDDI、领纤、Corning 等。
- OCP 2026：P138（Ciena）、P146/P416（Broadcom/Arista）、P147（五方面板）、P158/P159（NTT）、P247/P424/P425（Meta、Cisco）、P270、P296（MetaRoCE）、P412/P429（Alibaba）、P423（Microsoft）、P430（Oracle/Lumentum），以及 T01–T06 视频转写。
- OFC 2026：W4H.5、W4H.3、W3J.1、Th3J.4、Th4B.2、Th1J.6、Th1J.4、Tu3D.7、M1J.4、Tu3E.3、W3A.3、Th3B.3、M3F.6。
- GTC Berlin 2026：[NVIDIA 官方博客](https://blogs.nvidia.com/gtc-berlin-2026-news/)（Google Vera Rubin 多站点扩展）。
