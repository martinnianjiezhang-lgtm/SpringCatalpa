---
title: "OCP 2026 AI Infra 四尺度技术洞察（Scale-across/out/up/in + 底座）"
tags:
  - OCP2026
  - 专题洞察
---

> 生成日期 2026-10-21。完整方向底稿（含需求表、技术路线表、数据表、厂商态势、分歧、时间线、配图清单、与 ECOC 对照、索引对照表）见 `_insight_index/synthesis/`；逐篇笔记见 `_insight_index/notes/`，总目录 `_insight_index/doc_index.csv`。

## 第一部分　管理摘要

本报告的材料来自 OCP Global Summit 2026 本地目录：33 个 track 共 501 份 PDF、8,149 页，加上 Scale Across 专场的 6 场视频转写。
- 6 份 PDF 是 0 字节空文件，官方源同样为空；1 份重复。实际写成 494 篇讲稿笔记和 6 篇转写笔记。
- 文字层读不到的 776 页，逐页渲染成图片后看图转写。

所有数字都带出处：讲稿写作〔PDF id 页码〕，转写稿写作〔T0x 时间戳〕。id 和机构的对照见 `doc_index.csv`。口径分为自报、仿真、实验、现网、预测、引用、看图七类。

和 ECOC 2026 相比，OCP 的材料偏用户侧和系统侧。Meta、OpenAI、Microsoft、Oracle、Google、Alibaba 拿出了大量现网数据；ECOC 偏器件和物理层。两边放在一起看，能把"器件能做到什么"和"用户实际怎么用"对上。

### 一、十条跨方向判断

**1. 四个尺度的分界已基本对齐，分界线来自物理约束和功率预算，不是厂商偏好。**
- Scale-across：Meta 现网分三档，<3 km 用 FR，<10 km 用 LR，10 km 以上用 800ZR+ 加 DWDM〔P147 p25〕〔P247 p12〕。约 120–150 km 再按是否需要 ILA 分成 near 和 far〔P138 p7〕〔P247 p13〕。
- Scale-up：IEEE 的 DAC 目标从 100G 的 2 m 缩到 200G 的 1 m〔P308 p3〕。背板、CPC、retimer 能把铜撑到约 3 m，3 m 以外必须用光〔P346 p11〕。
- Scale-in：D2D 走宽而慢的并行接口。GLink-LL 为 0.05–0.10 pJ/bit、1–3 ns，UCIe-A 为 0.75 pJ/bit、10 ns 再加重传（自报）〔P075 p4〕。

含义：每一档要单独定义介质、FEC 和封装，不能用同一套方案降额覆盖。

**2. 电力是 scale-across 的直接原因，也是整个底座的第一约束。**
- Meta Prometheus 规模 1 GW，跨传统楼宇、户外帐篷和相邻托管设施运行（现网）〔P424 p4〕〔T01 05:06〕。
- Microsoft 的对比是：传统单个 DC 50–300 MW，下一代训练集群 1–5 GW 以上，新站点并网要 3–7 年〔P147 p40〕。
- Ciena 说，所有 near 客户都在评估转向 far，主要原因是电力〔T02 16:09〕。
- 机柜功率按 NVIDIA 的代际走：145 kW（54 VDC）→ 330 kW → 570 kW → 约 1 MW（800 VDC 原生）。800 VDC 设备的就绪时间是 2026 Q3 到 2028 Q1（自报，看图）〔P167 p3, p17〕。

**3. 网络在两个尺度上同时变扁：scale-out 用 radix 换层数，scale-up 用多柜换域规模。**
- Scale-out：102.4T 芯片拆成 200G 端口后 radix 为 512，两层 Clos 最多 131,072 个端口〔P140 p5〕。
  - Microsoft 把 GB200 集群拆成 4 个 200G 独立平面，跑 50K 和 75K GPU 的作业（现网）〔P418 p10〕。
  - NVIDIA 称两层多平面可到 512K GPU（自报，看图）〔P367 p14〕。
- Scale-up：域规模从单柜 64–144 走向多柜 1K–2K（预测）〔P366 p9〕。
  - 但"公布域"和"单跳域"差距很大：NVL576 是 576 对 72，Maia 200 是 6,144 对 48（引用，看图）〔P128 p6〕。
  - 推动力是 MoE 路由专家数增长，从 128 到 896，预测 2028 年后达到 2k–5k（引用）〔P128 p3〕。

**4. 传输智能下沉到 NIC，以太网在 scale-out、scale-up、scale-across 三个尺度上同时成为底座，SRv6 成了跨层的路径控制手段。**
- Scale-out：MRC、UET、MetaRoCE、Falcon 四套多路径 RDMA 并存〔P122 p10〕〔P296 p4〕〔P130 p9〕。
  - OpenAI 的现网实录：75K GPU 作业中一台 T1 静默黑洞，约 25% 的 QP 受影响、约 58 万个包被丢，MRC 约 1 分钟内绕开故障路径〔P133 p12, p13〕〔P422 p13〕。
- Scale-up：ESUN 和 SUE-T 已量产〔P366 p10, p11〕。AMD Helios 在 TH6 上跑 UALoE（UALink over Ethernet），每 GPU 72 条 212G 链路〔P126 p2, p3〕。
- Scale-across：Meta RBB 用 SRv6 TE，因为 6 类 QoS 用 MPLS TC 的 3 bit 编不下〔P425 p7〕；Alibaba 做 per-job TE〔P429 p12〕。
- 下一道门槛是跨厂商互通：Microsoft 指出 MRC 规格有空白，正在筹备 plugfest〔P418 p12–p16〕。

**5. 长 RTT 是 scale-across 包层的核心难题，在缓冲深浅上出现了现网和仿真的正面分歧。**
- 深缓冲一方是 Broadcom/Arista 的仿真：缓冲至少 1.5×BDP，FCT 才接近理想。100T 交换机在 10、30、100 km 下分别需要约 1.9、5.6、18.8 GB〔P416 p9, p10〕〔P147 p49, p51〕。
- 浅缓冲一方是 Meta RBB 的现网：浅缓冲加 ECN，跑到 650 km 跨度〔P425 p5, p6〕。但 Meta 的 BAG 又选了 J3 级深缓冲〔P424 p9〕。
- 两种做法对应不同流量：RBB 是混合流量、端到端控速，BAG 是无损 RoCEv2。
- 拥塞反馈要压到一个 RTT 以内：BTS 从交换机直接回送发送端，看图约 10 µs，对比端到端约 1,000 µs〔P146 p6〕。目前没有现网数据。

**6. 可靠性取代 pJ/bit，成为光互连选型的门槛；口径也从"器件 FIT"换成了"中断率"。**
- Meta LPO（现网，4k 模块）：中断次数比 retimed 少 2.0×，最近 60 天少 8.4×。讲者明确说收益来自少一类故障，不是模块本身更可靠〔P411 p8〕。
- Meta 51.2T 交换机 CPO（实验）：年链路中断率 0.2%，可插拔是 1.22%；MTBI 4.5M 对 0.72M。但 CPO 的 pre-FEC BER 反而更差〔P437 p5, p6〕。
- 面向 scale-up 光的目标：每链路端 ≤2 FIT，每 1M 器件小时 0 次 flap，而可插拔目前是 50–100 FIT〔P346 p5〕。Marvell 估算，约 300 万 GPU 的集群约每 48 秒一次 flap〔P345 p11〕。
- 现网故障的主因是污染：Oracle 90% 的 L1 链路故障、97% 的光模块更换与污染有关〔P438 p11〕。

**7. 光模块形态按时间分层：现在是 LPO 和可插拔，1.6T 一代转向 LRO 和 XPO，2027 年前后 NPO，2028 年起 XPU 侧 CPO。交换机 CPO 先于 scale-up 光化。**
- LPO 有两家现网数据。Oracle 800G：p99 pre-FEC BER 5.2e-10，FRO 为 2.9e-8〔P438 p6〕。
- 到 1.6T，Oracle 认为 LRO 是当前最佳：26 dB 通道、16 W〔P438 p9〕。XPO 单模块 12.8T（224G）或 25.6T（448G）〔P238 p4〕。
- 分层时间（预测）：SROI 给出现在 LPO、1–2 年 NPO、2–3 年以上 CPO〔P346 p6〕；Micas 给出 Open CPX 2027 年原型、2028 年早期部署〔P264 p9, p10〕。
- OCI-MSA 于 2026 年 3 月成立，Broadcom 称集成 OCI 为 7 pJ/bit、500 m，与 DAC 的 7 pJ/bit、2 m 同功耗（自报）〔P433 p13〕〔P445 p11〕。

**8. 光纤数量和机柜物理条件成为新的硬约束：布线、重量和液冷接口开始反过来决定网络形态。**
- 每个 GPU 机柜的后端光纤数（预测）：Hopper 约 576 芯 → GB200 2,308 → Rubin 4,616 → Feynman 18,464〔P316 p3〕。
- Meta GTSW 机柜内有 8,192 根光纤，需要在集成商处预布线〔P407 p12〕。
- 铜 scale-up 机柜约有 5,000 根无源铜缆，整柜重量今天约 4,000 lb，设计目标 8,000 lb〔P253 p15〕。Open DC 规范中，ML 机架加 sidecar 重 15,000 lb〔P180 p5〕。
- 网络机架也转为液冷整柜交付：102.4T 以上、ASIC >1 kW、单柜 2,000 根以上光纤〔P124 p3, p4〕。

**9. Scale-in 的重心从"封装里塞多少算力"移到"内存放在哪、怎么连"；KV cache 把 HBM 同时推到容量、成本和热三个瓶颈上。**
- HBM 约占 XPU 成本的 50% 以上〔P070 p3〕，占 2.5D 封装热阻的 57%（引用 ECTC 2026）〔P070 p7〕。
- 收益主要来自容量：同容量下 CXL 池和 CPU DRAM 的曲线几乎重合（实验）〔P059 p6–p8〕。
- 近存计算在检索类任务上有 64× QPS 的实验收益〔P060 p27〕，但瓶颈在软件接口〔P330 p4〕。
- 现网数据只有 Meta 一家：CXL 扩展使缓存类吞吐 +25%，舰队规模 −15%〔P058 p15〕。

**10. OCP 标准工作的重心，从"写规范"转向"证明能互通"。**
- 网络：OCS YANG R1.0 已发布，计划在 OFC 2027 做 8 家厂商互通演示〔P421 p12, p13〕；MRC 筹备 plugfest〔P418 p16〕；SAI 范围扩到 OTN〔P412 p10〕。
- Chiplet：OCE 自述 2027 年目标是证明互操作〔P079 p8〕。
- 液冷：UQD V2.0 首次做跨厂商测试〔P003 p50〕。
- 电力：800 VDC 板载电源工作组目标 2H 2027 发布〔P190 p12〕。

### 二、技术成熟度（按证据类型）

| 技术 | 所处阶段 | 最强证据 | 索引 |
|---|---|---|---|
| 800ZR+ 路由器直插 + DWDM | 现网规模部署 | Meta 全网 400ZR+→800ZR+ 升级完成 | 〔T06 13:06〕〔P247 p13〕 |
| 多 rail 线路系统 | 接近 GA | Ciena/Cisco 自报 −75% 功耗 | 〔P138 p10〕〔P247 p23〕 |
| 全谱转发器 FST | 概念/早期 | Alibaba 25.6T/纤，Ciena 51.2T 概念 | 〔P429 p13〕〔P138 p12〕 |
| SRv6 TE 跨区域 | 现网 | Meta RBB，5 个月从设计到首站 | 〔P425 p10〕 |
| 深缓冲 scale-across 交换 | 现网 + 仿真论证 | Meta BAG J3；Broadcom 1.5×BDP | 〔P424 p9〕〔P416 p10〕 |
| 亚 RTT 拥塞信号（BTS） | 规范/仿真 | 无现网数据 | 〔P146 p6〕 |
| 多平面两层 Clos | 现网 | Microsoft 75K GPU 作业 | 〔P418 p10〕 |
| MRC 多路径 RDMA | 现网 | OpenAI 75K GPU 故障实录 | 〔P133 p12〕 |
| LPO（100G/lane、800G） | 现网 | Meta 4k 模块、Oracle 约 35 万链路 | 〔P411 p8〕〔P438 p6〕 |
| 1.6T LRO | 多厂商互通演示 | Oracle 3 nm DSP 互通 | 〔P438 p9〕 |
| XPO | MSA 1.0 / 实测 | Microsoft/Arista 平台实测 | 〔P446 p18〕 |
| 交换机 CPO | 大样本实验 | Meta 38,400 端口、175M 器件小时 | 〔P437 p3, p6〕 |
| ESUN / SUE-T 以太网 scale-up | 量产 | Broadcom：5+ hyperscaler 生产 | 〔P366 p10〕 |
| UALink | 规范 + UALoE 落地 | AMD Helios | 〔P126 p2〕 |
| Scale-up NPO / XPU-CPO | 原型/规划 | Open CPX 2027 原型 | 〔P264 p9〕 |
| 宽而慢光 I/O（µLED/µVCSEL） | POC/早期出货 | Avicena 1 Tbps eKit | 〔P339 p12〕 |
| CXL 内存池 | 现网（Meta） | 吞吐 +25%、舰队规模 −15% | 〔P058 p15〕 |
| 近存计算 PNM | 实验 | 64× QPS | 〔P060 p27〕 |
| 800 VDC | 设备排期 | NVIDIA 2026Q3–2028Q1 | 〔P167 p17〕 |
| 单相冷板 | 主流（约 80%） | 已越过经济边界 | 〔P218 p16, p24〕 |

### 三、对三类企业的含义

- **系统和设备商（交换、路由、传输）**
  - Scale-across 交换机要能按距离分配 headroom，或者支持亚 RTT 反馈。深缓冲产品的市场边界取决于流量是无损 RoCE，还是靠 ECN 端到端控速〔P424 p10〕〔P425 p5〕。
  - 线路系统的竞争点从单波性能转到三件事：每机架 rail 数、放大站数量、按整条线路开通的运维自动化〔P138 p10〕〔T01 17:28〕。
  - 网络机架要按液冷整柜设计和交付〔P124 p3〕。
- **光模块和光器件商**
  - 800ZR+ 已是现网量产品；1600ZR 的准入条件是能和 400/800ZR 代际互通〔P147 p29〕。
  - 光保护能让端口需求减半，这是需求侧的一个减项〔T06 14:26〕。
  - 短距一侧要同时准备 1.6T LRO 和 XPO。可靠性的证据要用中断率和 MTBI 表达，不能只给 FIT 或 pre-FEC BER〔P411 p7〕〔P437 p5〕。
  - 抗污染连接器和工厂预端接是确定的增量〔P438 p11〕〔P343 p13〕。
- **芯片商（交换芯片、NIC、DSP、XPU）**
  - NIC 要支持多路径、SRv6 和长 RTT 下的大 cwnd：MetaRoCE 在 1.5 ms RTT 下 cwnd 为 3,500–7,000〔P296 p9〕。
  - 交换芯片侧有两条路：外挂 HBM 做缓冲，或者支持 BTS 这类信号〔P416 p3〕〔P146 p7〕。
  - XPU 侧要在 shoreline 上同时容纳 HBM、D2D 和光 I/O〔P455 p2〕，并为 scale-up 光化预留 OCI/NPO 接口〔P445 p11〕。

### 四、与 ECOC 2026 的总体对照

- **一致**：以下几点两会结论相同。
  - Scale-across 按光纤对部署，多 rail 和 FST 是方向；Ciena 的"22 个放大站对 1 个"在两会都出现〔P138 p10〕。
  - 2 km 以上 IM/DD 受色散限制，由 Coherent-Lite 补位。
  - 1.6T 一代 LRO 是低功耗首选。
  - 交换机 CPO 先行，scale-up 光化在 2027/28 年。
  - 连接器污染是现网故障主因。
- **OCP 新增**：协议层和传输层（MRC/UET/ESUN/SRv6/BTS）、长 RTT 缓冲、超大规模用户的现网故障实录、中断率口径、内存层级（CXL/HBM/PNM）、电力和机柜物理约束。这些在 ECOC 的判断中基本缺席。
- **矛盾或口径不一致**：
  - pre-FEC BER 能否作为可靠性指标：ECOC 用它支撑 LPO 更稳定；OCP 上 Meta 用 CPO 数据说明它单独不可靠〔P437 p5〕。
  - 空芯光纤：ECOC 有 Azure 的 427.97 km 实验；OCP 上超大规模用户的 scale-across 方案全部基于标准单模光纤和 C+L。
  - 铜的距离口径：200G 下 1 m 到 2.5 m 不等，差异在是否计入有源件。
  - 区域 Ring 架构的讲者归属：ECOC 速记记在 OVHcloud 名下，OCP 上同样的表述出自 Meta〔P247 p11〕，需要回查 ECOC 原始速记。
  - 同一组数据被两会复用，不能当作两份独立证据：Oracle 的 LPO 数据（156,591 / 202,042 条链路）、Lumentum 的 VCSEL HTOL 数据。

### 五、材料缺口

- 6 份 PDF 只有标题，没有正文〔notes/X00〕。其中《Wavelength-Granular OCS with Solid-State OPA》与网络相关，FTS 最佳 AI/HPC 论文也是 OCS 题目〔P352 p3〕，这块内容缺失。
- 看图有页数上限：P245 只看了 16 页中的 9 页，P347 有 2 页没看。
- 视频转写是自动字幕，数字与 PDF 冲突时一律以 PDF 为准，并标"转写存疑"。
- OCP 本届没有空芯光纤讲稿；多芯光纤只有 Sumitomo 和 TeraHop 两个来源。


## 第二部分　五个方向的结论与核心判断

### 方向1：Scale-across（跨楼/园区/区域 AI 集群互连：DCI、800ZR/1600ZR、多rail/全谱线路系统、SRv6/路由、深缓冲与长RTT拥塞控制、空芯/多芯光纤、光保护）

**一句话结论：** OCP 2026 上的 scale-across 已经是现网工程而非概念：Meta 的 1 GW Prometheus 跨楼、帐篷和托管站点运行，800ZR+ 全网升级完成，区域骨干 RBB 从立项到首站 5 个月；驱动力是电力分布，不是网络偏好。光层的部署单元从"一个波长"变成"一对光纤"，相干可插拔 + 光保护 + 多 rail 线路系统是当前主力，全谱转发器（FST）是下一步；包层的分歧集中在长 RTT 下要不要深缓冲（Broadcom/Arista 仿真要 ≥1.5×BDP，Meta RBB 现网用浅缓冲 + ECN 跑到 650 km），以及如何把拥塞反馈缩到一个 RTT 以内；SRv6 正在成为 DC、DCI、WAN 统一的路径控制手段。

**判断1：scale-across 的动因是电力，距离分层在各家之间已基本收敛为"<3 km 灰光 / <10 km LR / >10 km 相干 DWDM"，再往外以是否需要 ILA（约 120–150 km）划分 near/far；远端目标被推向 500–1,000 km。**
- 电力约束有现网与规划两侧的数字。Microsoft：传统单 DC 50–300 MW，下一代训练集群 1 到 5+ GW，新站点并网周期 3–7 年，结论是多站点训练"不是可选项"（自报）〔P147 p40〕〔T06 19:18〕。Ciena：选址顺序已变成电力第一，园区宣称的功率是终态额定值而非第一天可用（客户反馈）〔T02 01:52〕。Meta：Prometheus 1 GW，含传统楼宇、户外帐篷与相邻托管设施（现网）〔P424 p4〕〔T01 05:06〕。
- 距离分层：Meta 两场口径一致，楼 1–4 <3 km 用 FR，楼 5–6 <10 km 用 LR，10 km+ 用 800ZR+ + DWDM（现网）〔P147 p25〕〔P247 p12〕〔T06 12:05〕；Meta BAG 平台混插 FR4 ≤3 km、LR4 ≤10 km、ZR+ ≤1,000 km〔P424 p10〕。Ciena 以 150 km 为界：<150 km 为 near（扩展园区、无 ILA、点对点满配 C+L），>150 km 为 far（需 ILA）〔P138 p7〕〔T02 05:52〕；Cisco/Meta 图写 ILA-free 120–150 km、带 ILA 500 km+〔P247 p13〕。
- 机制：同步训练里一对园区之间的容量是 2020 年前后整个前端区域的约 14 倍（看图）〔P138 p6〕〔T02 05:20〕；Meta 称 DC 间同步流量已比用户流量大约一个数量级（自报）〔T06 10:58〕。在这个流量规模下，灰光每纤只有 Tb/s 级，必须挖沟布大量光纤，10 km 以外改用每纤数十 Tb/s 的相干 DWDM 更划算〔P138 p5〕。
- 方向：Ciena 称所有 near 客户都在评估或转向 far，主因是电力；客户训练距离将从今天约 100 余 km 走向 500、800 km，最终约 1,000 km，指同步预训练（客户反馈/预测；"115 or 20 km"转写存疑）〔T02 16:09〕〔T02 22:25〕。Meta 已在 800G-ZR+ 上跑到 650 km 跨度〔P425 p5〕。

**判断2：光层部署单元从波长变成光纤对。当前主力是"路由器内 800G 相干可插拔 + 光保护 + C+L 满配"，多 rail 线路系统已接近 GA，FST 仍在概念/早期阶段；收益数字全部是厂商自报。**
- 可插拔相干已在现网大规模使用：Meta 刚完成全网 400ZR+ → 800ZR+ 升级，逐站点进行，代际互通是唯一可行前提（现网）〔T06 13:06〕；Meta 要求 400ZR⇄800ZR⇄1600ZR 代际互通、开放线路系统、C+L 满填、DC 与骨干共用光模块〔P147 p29–p33〕。两端各"10,000s of 800G ZR"（自报）〔P247 p13〕。Cisco 引 ACG Research：ZR+ 直插路由器相对转发器方案能耗 -90%、空间 >-65%、CAPEX -66%（引用）〔P247 p22〕。
- 光保护是节省端口的主要手段：Meta 称光链路保护多数情况下可让终端 IP 端口和转发器数量减半（自报）〔T06 14:26〕〔T01 09:30〕；Meta BAG 容量规则写明"无光保护时 BAG-to-BAG 容量 = (B + buffer) × 2"〔P424 p12〕，两者口径吻合。Ciena 给出三种实现：N+1 光保护 + 路由器内 ZR+（光层先于包层倒换），以及 active-active 由包层倒换、用外置转发器（插件够不到的距离或路由器改用 CPO 时）〔T02 06:54〕。
- 多 rail 线路系统：20 Pb/s 用例按传统线路系统需 22 个放大小屋，Hyper-Rail 只需 1 个，128 rails/机架 vs 4 rails/机架，密度 32 倍（自报，看图）〔P138 p10〕〔T02 11:59〕；Cisco Open Transport 3000 相对 NCS1010 功耗 -75%、空间 -80%，每 4×C+L 轨 350 W，每机柜 12 kW 内 128 条 C+L 轨（自报）〔P247 p23〕。转写里 Cisco 说 NCS1010 做 C+L 时 7 条线路占满一架〔T01 16:26〕。运维单位从"开一个波长"变成"开一整条线路"〔T01 17:28〕。
- FST：Ciena 51.2T C&L 概念为 4 个 8 通道服务模块、每模块 8×1.6T modem、客户侧 6.4T CPO/NPO（概念）〔P138 p12〕〔P447 p13〕；Alibaba 为 C 波段 4.8 THz、8 个固定波长 DFB/模块（ELSFP）、20 dBm 通道功率、每纤 25.6 Tb/s（自报）〔P429 p13〕〔T04 37:06〕。FST 可靠性尚无定案，Ciena 给的选项是拆成 4 个现场可换模块或模块内 N:1 保护〔T02 21:27〕。

**判断3：长 RTT 下的缓冲策略出现明确分歧，且分歧在 Meta 内部也存在：Broadcom/Arista 用仿真主张 ≥1.5×BDP 的分层深缓冲；Meta RBB 用浅缓冲 + 自研 GLIDE 在 650 km 跨度现网运行；Meta BAG 则选 J3 级深缓冲。差别来自流量类型与无损机制不同。**
- 深缓冲论证（仿真）：Broadcom 算例 800GE 在途数据 5 km/5 MB、100 km/100 MB、1,000 km/1 GB〔P147 p46〕〔T06 24:42〕；缓冲 ≥1.5×BDP 时 FCT 开销约 3–8%、重传约 0%；降到 0.1×BDP 时 500/150/50 MB 流 FCT 开销 20.6%/24.9%/31.5%，重传 23.4%/31.2%/55.1%（仿真，看图）〔P416 p9〕〔P147 p49〕；100T 交换机按 1.5×BDP 需 10 km ~1.9 GB、30 km ~5.6 GB、100 km ~18.8 GB〔P416 p10〕〔P147 p51〕。Arista 称现网分层为楼内浅缓冲、楼间 <10 km 浅缓冲轻过订、区域间 10 km+ HBM 深缓冲（自报）〔P416 p4〕。
- 浅缓冲现网（Meta RBB）：Ring 带宽约为 EBB 的 10 倍，只有 DC 级密度设备能满足每瓦要求，"浅缓冲是继承的，不是选择的"；GLIDE 在 5 ms 单向时延下达到 70% 链路利用率目标，常态只占约 7% 缓冲，4.5:1 incast 才填满 32–53 MB（实测，看图）〔P425 p5〕〔P425 p6〕。Meta 的时间线也显示了这个转向：2025.12 Rings 按深缓冲设计，2026.02 改为浅缓冲 + FBOSS，2026.07 首个 RBB 站点〔P425 p10〕。
- 深缓冲现网（Meta BAG）：BAG 承载跨站点 RoCEv2 后端流量，选"深缓冲、信用转发 ASIC（J3 Class）"以获得更大 headroom 支撑长距无损，并用 FADT 多 profile 按距离分配 headroom〔P424 p9〕〔P424 p10〕。
- 机制：RBB 承载存储读、AI 与非 AI 混合流量，靠 ECN 让发送端退避，缓冲只吸收突发；BAG 承载训练 AllReduce 的无损 RoCEv2，headroom 要覆盖一个 RTT 的在途数据，所以随距离线性涨。Broadcom 的仿真条件是 2:1 过订、包喷洒 + NSCC/RCCC〔P416 p8〕，与 RBB 的流量模型不同。两组结论目前不能直接互相否定。

**判断4：反应式拥塞信号的下限是一个 RTT，而 scale-across 中许多同步流短于一个 RTT；业界在三处同时补：交换机直接回送发送端（BTS）、长距传输参数放大（MetaRoCE）、物理层"可证无损"与光层劣化预警。它们都还没有公开的现网量化结果。**
- 问题定义：Broadcom 的参考网络是两个低 RTT 域（本地/远端 DC）夹一个高 RTT DCI 域，现有 CC 按单一 base RTT 设计〔P146 p3〕〔T05 03:48〕；PFC、ECN、CSIG、trimming 都是前向信号，要接收端反射，最快一个 RTT，而同步训练中许多流比一个 RTT 还短〔T05 07:40〕。ECN 仅 1 bit，UEC 新发布的 CSIG 约 10 bit（口述，未核对 PDF）〔T05 06:44〕。
- BTS：由拥塞点/DCI 入口交换机直接向发送端回送带元数据的截断包，看图约 10 µs vs 端到端约 1,000 µs〔P146 p6〕；设计约束为不改传输头和转发头、交换机无状态、控制流量 ≤约 1%〔P146 p7〕〔T05 12:50〕。仿真"显著改善 CC 收敛"但无数值（引用）〔T05 15:38〕；UEC 已有 BTS 工作组，OCP SAI 有配套 PR #2349〔P146〕〔T05 16:04〕。讲者自列多跳通知、重复通知、限速归属、多 RTT 域 CC 适配四个未解问题〔T05 14:00〕。
- 传输层：MetaRoCE 把 scale-across 当作同一传输的长 RTT 场景，示例 RTT 1.5 ms，Max Cwnd 3,500–7,000，Max Path 约 30–50（scale-out 为 RTT 5–15 µs、Cwnd ~75）（自报）〔P296 p9〕；只依赖商用交换机的 ECN + ECMP，不需 trimming/INT〔P296 p4〕。Google 把"long-haul RDMA 后端"和"CSIG 扩展到亚 RTT CC"列为 Virgo 下一步〔P130 p10〕。
- 物理层与光层：Ciena 指出现有相干 FEC 为容忍丢包的业务设计，呼吁 OCP 标准化"可证无损"物理层，示例目标 post-FEC BER 1e-24（提议）〔P138 p15〕〔T02 17:18〕。Alibaba LD/RD：光模块检测 pre-FEC BER 超过门限后向远端注入 RD，同时通知本地交换机把该路径移出 ECMP 组，称可零丢包切换（自报，无测试数据）〔P429 p13〕〔T04 37:42〕。Microsoft 列出 OSP 光纤市场可用性约 97.7%、link flap 与突发误码，"单次故障即暂停训练"〔P147 p42〕。

**判断5：SRv6 正在成为 scale-out、DCI、区域骨干共用的路径控制机制，配套是 SONiC/FBOSS + SAI 开放栈向 DCI 和光传输层延伸。采用理由各不相同，不是单一技术优势驱动。**
- Meta RBB：已大规模运行 MPLS SR TE 仍改用 SRv6，理由是 Olympic QoS 需要 6 类严格优先级，MPLS TC 3 bit 只能编 4 类，IPv6 TC 8 bit 能编全部 6 类〔P425 p7〕；RBB 64 个并行平面，每平面一个控制器，每 30 秒用 5 个调用编程全部交换机（自报）〔P425 p4〕〔P425 p9〕；首批站点基于 SAI + Cisco Silicon One，设计到量产 5 个月，之后 3 个月完成长途与 TE/SDN 控制器量产（现网）〔P425 p10〕〔P244 p16〕。
- Alibaba：DCI 拓扑更不对称、容量更稀缺、时延更敏感，TE 是必需（Cisco 观点）〔P429 p2〕〔T04 23:06〕；scale-across 专用 eCore 用 64×800G 盒子、起步即 800G，现场测试发现长途 100G 链路易哈希碰撞〔P429 p11〕〔T04 33:29〕〔T04 34:42〕；per-job TE 用 RoCE BTH 头 4 个保留位打标，边缘 eSR 导入对应 SRv6 策略（自报，注 P200/Q4D 支持）〔P429 p12〕〔T04 35:19〕。
- OpenAI：后端 scale-out 用 SRv6 源路由 + MRC，GPU 到 GPU 4 跳装进单个 IPv6 DA 的 6 个 uSID；生产中一台 T1 静默黑洞，75K GPU 作业约 25% QP 受影响、约 580K 包被丢，MRC 剔除路径后恢复（现网）〔P422 p13〕〔T04 10:33〕〔T04 13:05〕。OpenAI 同时说明 MRC 也支持基于熵的 ECMP，SRv6 只是可选方式之一〔T04 17:29〕。
- 光传输层开放化：Alibaba 推 SONiC for OTN，SAI OTN Phase 1（OA/VOA）已合并，Phase 2 做完整开放线路系统（OCM、OTDR、WSS、APS、OSC），Phase 3 计划做 Transponder（自报）〔P412 p10〕；SAI 范围已扩到 Packet ASIC、DASH、OCS、OTN〔P412 p9〕。

完整底稿：`_insight_index/synthesis/方向1_ScaleAcross_综合底稿.md`

### 方向2：Scale-out（AI 后端网络：UEC/MRC/RoCE、拥塞控制与负载均衡、多平面拓扑、102.4T 交换芯片与系统、NIC、可插拔光模块 LPO/LRO/FRO、OCS、SONiC/遥测与链路可靠性）

**一句话结论：** OCP 2026 的 scale-out 讨论，重心从"链路更快"移到"拓扑更平、传输进 NIC"。102.4T 交换芯片靠 200G 端口拆分把 radix 换成规模，两层多平面 Clos 已能覆盖 10^5 GPU 量级；MRC、MetaRoCE、UET、Falcon 这四套多路径 RDMA 把负载均衡、乱序和故障绕行交给 NIC，并已有 75K GPU 现网故障实录。光侧，LPO 拿到了 Meta 与 Oracle 的现网可靠性数据，1.6T 代则分流到 LRO 和 XPO。OCS 还处在接口与运维标准化阶段。链路可靠性的瓶颈已从器件转到运维与可观测性。

**判断1：102.4T 的收益主要以 radix 兑现，"降端口速率 + 多平面 + 两层 Clos"成为多家共同的默认拓扑，三层网络开始被视为可以省掉的一层。**
- 机制：两层 1:1 Clos 最多 k²/2 个客户端口，规模随 radix 平方增长。102.4T 器件在 800G 时 radix 128，最多 8,192 客户端；拆到 200G 时 radix 512，最多 131,072〔P140 p5〕。Broadcom 给出同一组数字：TH6 两层 800G 为 8K 端点，400G 为 32K，200G 为 128K；4 平面（每 XPU 4×200G）可到 128K XPU〔P134 p10, p13〕。
- 超大规模用户各自落地：Google Virgo 两层、独立多平面，平面数 N 约等于每加速器的 SerDes 级"skinny link"数，单平面故障剩 (N-1)/N 带宽〔P130 p7〕；Meta 下一代 Flattened Planar Fabric 去 ToR、两层、负载均衡放 NIC〔P244 p9〕；Microsoft GB200 集群把 ConnectX-8 的 800G 拆成 4×200G 独立平面，两层 T0/T1，跑 50K 与 75K GPU 作业（现网）〔P418 p10〕；Microsoft Fairwater 多平面设计最多 524,288 GPU（引用）〔P422 p9〕。
- 厂商口径更激进：NVIDIA 称 Spectrum-X Photonics 多平面两层扁平网络可到 512K GPU、交换机少 40%（看图，自报）〔P367 p14〕。
- 代价落在布线：AMD/Arista 8 平面方案需要在 GPU 与 T1 之间加 8×8 shuffler〔P140 p14, p15〕；每 GPU 机柜后端光纤数 Hopper 约 576 芯、GB200 约 2,308 芯、Rubin 约 4,616 芯（自报/预测）〔P316 p3〕；Meta GTSW 机柜内光纤 8,192 根，需在集成商处预布线〔P407 p12〕。

**判断2：负载均衡、拥塞控制和丢包恢复正从交换机移到 NIC。四套多路径 RDMA 并存，核心技术趋同，分歧集中在 API、拥塞信号和是否依赖交换机新功能；跨厂商互通是下一道门槛。**
- 技术共性：UET 与 MRC 都用包喷洒、乱序交付、流量引导，丢包检测都用 SACK/NACK/超时/trimming〔P132 p3〕；MRC 只做发送端拥塞控制，UET 同时有发送端 NSCC 与接收端 credit RCCC，并带 LLR、CBFC、CSIG〔P122 p10, p13, p15〕。MetaRoCE 只依赖商用交换机的 ECN + ECMP，明确不需要 trimming、自适应路由或 INT，采用"排序完成而非排序投递"〔P296 p4, p5〕。Google Falcon 已在 NVIDIA ConnectX/BlueField 上与 Google NIC 线格式互通〔P130 p9〕。
- 现网证据：OpenAI 75K GPU 训练作业中一台 T1 交换机停止转发，约 25% QP 受影响、约 580K 包被丢；吞吐从约 12.2–12.5 Pb/s 跌到约 10.5 Pb/s，约 1 分钟内恢复，交换机重启上线期间无明显下降（现网，看图）〔P133 p12, p13〕〔P422 p13〕。转写补充：检测与恢复约一个 RTT 量级，告警晚于恢复〔T04 13:05–14:18〕。Microsoft 生产集群 T0–T1 链路抖动每时段多为 2–8 次、峰值约 13 次，MRC 透明重路由（现网，看图）〔P418 p10〕。
- 机制：RC 的问题是一个 QP 只哈希到一条 ECMP 路径、单丢包触发 go-back-N、恢复依赖路由收敛；MRC 用 SRv6 源路由或熵值（EV）把故障变成"选路事件"〔P133 p6, p7〕。每 QP 跟踪 128 条路径，ECN 标记的路径在当前排列中跳过，约每 RTT 对一个坏 EV 发探测〔P141 p7, p9〕。
- 互通缺口：Microsoft 指出早期部署只用单一 NIC 厂商，现有 MRC 规格在保留位、可靠性算法、RTT 测量上有空白，提出线格式/算法/行为三级互通并筹备 plugfest〔P418 p12–p16〕。MetaRoCE 用两个不共享代码的软件实现互相对打作为"最终裁判"〔P419 p5, p6〕。

**判断3：LPO 在 100G/lane（Meta）与 800G 模块（Oracle）上有了现网可靠性数据，收益来自"少一类故障"而非模块更可靠；到 1.6T，各家倾向 LRO，LPO 只在电通道余量被验证的地方扩大。**
- Meta：同链路模式、4k 模块、4 个月生产，linear 比 retimed 中断少 2.0×、影响业务的故障少 2.6×，最近 60 天中断少 8.4×（现网，看图）；实验室 0 次模块归因故障/2.96M link-hours，固定风扇下每模块功耗 −46%、温度低 17.5 °C〔P411 p5, p8, p9〕。讲者明确：模块级两者相当，收益是架构性的〔P411 p8〕。
- Oracle：800G T0–T1 链路 24 小时最大 pre-FEC BER，LPO 156,591 条中位 1.137e-11、p99 5.165e-10，FRO 202,042 条中位 1.432e-11、p99 2.888e-8；一个月内至少一次 down transition 的比例 3.244% 对 5.681%；64×800G 交换机半 LPO 比全 FRO 中位功耗低 258 W，其中 66 W 来自风扇（现网）〔P438 p6, p7, p8〕。
- 1.6T 分歧：Oracle 认为 LPO 难以同时满足 SI 与互通，LRO（26 dB 通道、16 W、约 10 pJ/bit，已演示多厂商 3 nm DSP 互通）是当前最佳低功耗方案〔P438 p9〕；Microsoft/Arista 在 XPO 平台上实测 FRO 余量最大、LRO 对光衰减更敏感、LPO 受 Tx 限制，15 dB 损耗下 LPO-LPO 3 dB 光衰时 BER 约 2e-7（实验，看图）〔P446 p18〕；Micas 预测 LPO 2027 年仅在 SI 余量验证处扩大〔P264 p9–p10〕。
- 功耗阶梯各家口径接近：Nokia 给 retimed 可插拔约 15、LRO 约 10、LPO/NPO/CPO 约 6 pJ/bit（自报）〔P335 p2〕；OCP SROI 工作流给 LPO 5–6、RTLR 8–10 pJ/b〔P346 p6〕。LRO 处在"省一半 DSP"的位置，这是它在 1.6T 被多家接受的原因。
- 代价：Oracle 的 OCI 运维团队发现 LPO 链路并不更不稳定，但故障归因变难，"可靠性提升、可解释性倒退"〔P443 p6〕。

**判断4：OCS 在 scale-out 里的实际位置仍是"慢变化的物理层交叉连接"，OCP 的工作集中在接口、运维流程和一致性测试，而非开关速度。**
- 标准化：Google 主导的 OCS Interface Spec v0.8 已提交 OCS 工作组，基于 OpenConfig YANG + gNMI，新增 cold-boot-recovery {MAINTAIN, REMAKE, REMOVE} 等对象〔P427 p10, p14〕；OCP-OCS YANG Model R1.0 已发布，iPronics/KDDI/NTT 计划在 OFC2027 用 8 家厂商 OCS 演示备件池故障恢复（自报，计划）〔P421 p12, p13〕；OCS 白皮书 2026 年 4 月发布，快速切换白皮书待发〔P136 p10〕。
- 光学可行性：Oracle/Lumentum 1,000 台近期产品 1310 nm 插损中位约 1.2–1.4 dB、98 分位约 1.6–1.85 dB，对照 IEEE FR/FR4/FR8 的 4 dB 预算（看图）〔P430 p12〕。
- 用途边界：Google 把 OCS 放在多楼园区 spine 替代电交换，配 1.6T Coherent-Lite（设计概念，非承诺）〔P147 p5–p11〕〔T06 01:06–08:02〕；iPronics/KDDI/NTT 的用例是 1:N 全局备件池和按 All-Reduce/All-to-All 重构光连接〔P421 p8, p9〕。主流 3D MEMS 是毫秒级重配置，只适合慢变负载〔P136 p5〕。
- 时间触发的研究结论：按轮次切换的电路交换，PTP 精度已比预测误差低 5–6 个数量级，难点是把 PHC 时间基暴露给集合通信库；64K GPU 预测误差 434 ms，而 3D-MEMS dark time 20 ms（实验+引用）〔P111 p9〕。

**判断5：链路可靠性的主要矛盾已从"器件 FIT"转到"中断率 + 污染 + 可观测性"，OCP 正在把遥测与诊断做成跨 LPO/CPO/retimed 的统一契约。**
- 量级：Meta 两个平台的作业中断中，scale-out 网络（交换机、NIC、光模块）占 23.6% / 11.7%，scale-up fabric 占 24.2% / 9.2%（现网）〔P125 p8〕；引用 arxiv 2410.21680，131,072 GPU 集群 MTBF 约 15 分钟〔P421 p3, p16〕。
- 指标转向：Meta 主张 AI 训练应看"中断率"而非"故障率"〔P411 p7〕；Meta CPO 评估以单个不可纠正码字定义中断，CPO 平均 pre-FEC BER 约 9e-8、FRO 约 1e-9，但 CPO 年链路中断率 0.2%–0.47% 低于 FRO 1.22%，并指出 pre-FEC BER 单独作健康指标不可靠（实验）〔P437 p5, p6〕。
- 规模放大效应：Marvell 估算约 3M GPU、>10M 光链路的集群约每 48 秒一次 flap（估算）〔P345 p11〕；OCP SROI 工作流把目标定为每链路端 ≤2 FIT、每 1M 器件小时 0 次 flap，对比可插拔 50–100 FIT（需求/目标，面向 scale-up）〔P346 p5〕。Microsoft 主张把同一端口的 lanes 分到不同 flap 故障域，4×200G 模式下单 lane flap 只降级而不终止作业（分析）〔P345 p30–p32〕。
- 主因是污染：Oracle 90% 的 L1 链路故障与污染有关，97% 的光模块更换源于污染（现网），扩束连接器插拔力约降 20 倍〔P438 p11, p12〕。Corning 透镜 MMC 50 次插拔不清洁，最大 ΔIL 0.26 dB 对物理接触 1.42 dB，16 端口部署 8 min 43 s 对 1 h 19 min（实验）〔P343 p11, p13〕。
- 标准动作：OCI 提交 Enhanced Telemetry Optics 软件规范 v1.0〔P370 p19〕；Credo 基于 CMIS CDB 一条命令返回身份、健康分、遥测、告警，48 个收发器试验中健康分随 0/5/10 dB 衰减为 80/60/40（实验）〔P408 p9, p15〕；Oracle 把 DSP 消失后需保留的职能归纳为 Detect、Localize、Remember、Reach、Remediate〔P443 p9〕。

完整底稿：`_insight_index/synthesis/方向2_ScaleOut_综合底稿.md`

### 方向3：Scale-up（机柜/超节点互连：UALink、ESUN、SUE-T、NVLink 对标、域规模、铜背板/AEC/ACC/flyover、CPO/NPO/XPO/OCI、Open CPX、scale-up 光化时间点）

**一句话结论：** OCP 2026 上 scale-up 的协议层基本收敛到"以太网 PHY + 精简头 + LLR/CBFC"（ESUN/SUE-T/UALoE，UALink 也复用 802.3dj PHY），已进入量产；物理层是"柜内铜、跨柜光"的混合期，200G/lane 下铜靠背板、flyover、ACC/AEC、CPC 撑到约 1–4 m，单柜 72–144 XPU 之外的多柜域（512–2K）要靠光；scale-up 光化的专用 PHY 是 OCI-MSA（慢而宽 NRZ、WDM、BiDi），近期形态以 NPO/XPO 为主、XPU 侧 CPO 在 2027–2028 之后；决定落地节奏的不是 pJ/bit，而是可靠性、flap 爆炸半径和可服务性。

**判断1：scale-up 域正从单柜 64–144 XPU 走向多柜 512–2K（远期 5K），但"公布域"和"单跳域"差距很大，单跳域的规模由交换芯片 radix 决定。**
- Broadcom：今天 64–144 XPU/单柜，明天 1K–2K XPU/多柜（自报/预测）〔P366 p9〕；Meta 机架演进 ORv3 HPR ≤72 → ORW（2026-Q3）≤144 → ≥256 加速器（自报）〔P437 p2〕；Microsoft/Meta 给出 scale-up GPU 数 8→72→576→1K、每 GPU 450→1200→1800 GBps〔P417 p4〕。
- Delos/Eridu 的对比表（引用 Hot Chips/GTC 2026 等，看图）：NVL72/Helios 公布域 72/单跳 72；NVL576（2027）576/72；NVL1152（2028）1,152/144；OpenAI Jalapeño 2,048/128；Microsoft Maia 200 6,144/48〔P128 p6〕。机制：大域多为两级或多级，跨机柜性能更低，需要拓扑感知放置；仿真中 petabit 交换机比 230T 交换机 GPU 利用率 88% vs 64%（仿真，引用 Turbalance）〔P128 p16〕。
- 推动力来自 MoE：路由专家数 Llama 4 128 → DeepSeek-V3 256 → Kimi K2 384 → Kimi K3 896，2028–29 预测 2k–5k（引用/预测）〔P128 p3〕；MoE 动态多播组超出传统交换机组数，集合通信退化为单播〔P117 p13〕。

**判断2：协议层向以太网收敛，ESUN/SUE-T 已从规范进入量产，UALink 在规范与管理层推进，但其 200G 版本复用以太网 PHY，AMD Helios 实际跑 UALoE（UALink over Ethernet）在 TH6 上。**
- Broadcom 自报：ESUN 175+ 成员、ESUN 机柜已量产；5+ hyperscaler 在生产中运行以太网 scale-up，10+ 伙伴在做机柜，多款 XPU 以太网 scale-up 机柜未来 6 个月量产；SUE v1.0 2026-02 发布，SUE-T 目标 2H2026〔P366 p10, p11〕。
- 现网实例：Meta Tahan（TH5 51.2T，单跳，<1 µs/跳，每加速器每方向 6.4 Tbps）部署于 MTIA300，下一代 TH6 支持 72 加速器、每方向 9.6 Tbps〔P151 p10, p11, p14〕；HPE/AMD Helios 72 GPU、12 台 TH6、每 GPU 72 条 UALoE@212G、1.8 TB/s/dir〔P126 p2, p3〕。
- 机制：ESUN 用约 4–12 B 头替代 IPv4/UDP（省 24–44 B），256B 载荷线效率 82.58%→87.07%（1.0）→89.98%（1.1 UFH_16）（看图）〔P417 p7, p11〕；LLR/CBFC 取代 PFC 实现无损、浅缓冲〔P417 p9〕〔P157 p4〕；UALink 200G 复用 IEEE 802.3dj PHY、线缆与 retimer，Consortium 只定义 DL/TL/协议层〔P428 p3〕。

**判断3：铜在柜内仍是主力且还有一代余量，但 200G/lane 下 DAC 只剩约 1 m，延伸手段（背板、flyover/CPC、ACC、AEC）各有功耗与时延代价；400G/lane 铜能否覆盖整柜取决于"从封装直接出线"。**
- 距离：IEEE DAC 目标 50G 3 m → 100G 2 m → 200G 1 m（引用 802.3cd/ck/dj）〔P308 p3〕；SROI 表：无源背板 1–1.5 m、NPC 飞线 1.4 m、CPC >1.5 m、redriver ~2 m、retimer 2.5–3 m（每级 ~50 ns），>3 m 必须用光，400G CPC-CPC ~1 m（引用 802.3dj/OIF）〔P346 p11〕。
- Broadcom 当前铜背板：72 XPU、1.04 Pbps 整柜、14.4 Tbps/XPU、26 AWG twinax 1024 根/OU、~2 m、SerDes 7 pJ/bit、整柜 ~250 kW；下一代设想 576×400G PAM6、2.08 Pbps、同样 2 m 铜（预测）〔P366 p16〕。Amphenol 估算：封装到封装 0.8 m twinax 全柜走线用 22 dB，40 dB 预算余 18 dB；经主机 PCB 出线只余 5.8 dB（估算）〔P250 p12〕。
- 延伸件分工：Ciena 1.6T ACC 3.5 m、1.5 pJ/bit/端、零附加时延 vs AEC 4.5 m、10 pJ/bit、~2×35 ns〔P308 p6〕；Meta 800G AEC 现网"数百万"互连，<12 W/端，1.0–3.2 m〔P179 p5, p6〕；Broadcom/Molex 1.6T AGERA3 AEC 6m+ 量产（自报）〔P237 p14〕。

**判断4：scale-up 光化有了专用 PHY（OCI-MSA）与开放光引擎插座（Open CPX），时间点分三层：可插拔/LPO（现在）→ NPO/XPO（2027 前后）→ XPU 侧 CPO（2027–2028 起，规模化更晚）；【SO-CPO】先于【SU-光】。**
- OCI-MSA 2026-03 成立（Meta、Microsoft、OpenAI、AMD、Broadcom、NVIDIA），GEN1 为 4λ×50G NRZ、DWDM on CWDM 栅格、BiDi，GEN2 400G 规范 2027，800G >2030（原文带问号）〔P445 p11, p12〕〔P253 p12–p13〕〔P442 p10, p12〕；Broadcom 称 Integrated OCI 7 pJ/bit/500 m，与 DAC 7 pJ/bit/2 m 同功耗，前面板 DR LRO 23 pJ/bit（自报）〔P433 p13〕。
- 分层时间：SROI 主席给出现在 LPO/RTLR、1–2 年 NPO（CPX MSA）、2–3 年以上 CPO（CPX/OCI BiDi）〔P346 p6〕；Micas：Open CPX 2027 原型、2028 早期部署，CPO 交换机 2027–2029 先增长，XPU-CPO 更晚（预测）〔P264 p9–p10〕；NVIDIA 展示 Vera Rubin Ultra NVL576 用 NVLink 7 CPO 交换托盘（看图）〔P367 p18〕，P128 引用其时间为 2027〔P128 p6〕。
- 形态分工：Astera：近期多柜 scale-up 适合 NPO，CPO 面向下一代高 radix 平台；混合 pod（柜内铜背板+柜间 NPO）对应 72–576 加速器，全光 pod 对应 >576〔P439 p11, p14〕；LightCounting（经 GO 引用，看图估读）2031 年 CPO 约 71M 端口中 scale-up 约 46M，NPO 约 89M 中 scale-up 约 37M〔P321 p5〕。

**判断5：可靠性和可服务性取代能效成为选型门槛。【SO-CPO】已有大样本现网/实验数据证明优于可插拔，但【SU-光】的门槛是"达到无源铜可靠性"，flap 爆炸半径与激光器位置是未决焦点。**
- 【SO-CPO】Meta 51.2T CPO 交换机：年链路中断率/MTBI FRO 1.22%/0.72M，CPO Phase 2 0.2%/4.5M（38,400 端口、175M 器件小时），故障 83–85% 来自 ELS 模块（激光驱动 SMT 元件，已修复）（实验）〔P437 p3, p4, p6〕。CPO 的 pre-FEC BER 更差（~9e-8 vs ~1e-9）但故障率更低〔P437 p5〕。
- 【SU-光】门槛：SROI 要求 ≤2 FIT/链路端、每 1M 器件小时 0 次 flap（可插拔 50–100 FIT）〔P346 p5〕；Marvell 估算 3M GPU、>10M 光链路时约每 48 秒一次 flap〔P345 p11〕；Microsoft：单外置激光源驱动单光引擎为 100% blast radius，CWDM 4 波长 25%〔P442 p7〕；GPU 不能像交换机那样处理 flap，1×800 模式单 lane flap 即 job abort〔P345 p30〕。
- 铜也不是零故障：Meta 铜 scale-up 每柜数千连接，99.9% 良率也有约 10 条坏链路；边缘链路仍活跃时 AllReduce 带宽降至约 55%，放弃 plane 后约 86%（看图）〔P152 p2, p7〕；Meta scale-up fabric 占 Platform-A 训练中断 24.2%（现网）〔P125 p8〕。

完整底稿：`_insight_index/synthesis/方向3_ScaleUp_综合底稿.md`

### 方向4：Scale-in——封装内与内存层级（Open Chiplet Economy、UCIe/BoW/GLink 等 D2D、2.5D/3D 封装与热、封装内光 I/O、HBM、CXL 内存池化/KV cache 卸载/PNM、SCM）

**一句话结论：** OCP 2026 的 scale-in 讨论，重心从"封装里能塞多少算力"移到"内存放在哪里、怎么连"。KV cache 让 HBM 同时卡在容量、成本和热上，于是出现三条并行出路：向上把 warm KV 放到 CXL/PCIe/UALink 挂接的机柜级内存池，向内做定制 HBM base die、混合键合 DRAM-on-Compute 和低功耗私有 D2D，向外用面阵或宽慢光 I/O 绕开 shoreline。OCE 标准工作也随之从 PHY 转到系统层（固件、安全、互操作验证）。目前多数收益数字是厂商自报或实验，现网数据只有 Meta 一家。

**判断1：KV cache 把内存层级的扩展单位从"每 GPU 的 HBM"推到"机柜级共享池"；CXL 池化的实测收益主要来自容量，同容量下与 CPU DRAM 持平。**
- 容量压力（自报）：64 并发 × 32K 上下文时 KV 占 HBM 57%，Qwen3-235B 的 KV 约 384 GB，超过 235 GB 权重〔P057 p2〕；128K 上下文下 2 个用户即填满 80 GB HBM〔P275 p7〕；Nallasway 示意单服务实例内存 2020 年 0.4 TB → 2026 年 agentic 5 TB，其中 KV 约 3 TB（看图，数量级）〔P450 p2〕。
- 收益机制是"避免重算"而非"更快的介质"：Astera 同容量（每实例 128 GB）下 fabric 内存与 CPU DRAM 曲线几乎重合，fabric 侧容量为 2–3 倍时才出现"x2/x3 better"（实验，看图）〔P059 p6, p7, p8〕；Samsung 在 KV 超出 RDIMM 容量后，RDIMM 方案吞吐降到约 17%，CXL 池保持约 95%（5.6×，实验）〔P060 p8〕；Micron 模型显示 KV 层容量 400→600 GB 时 TTFT 从约 13 s 跳到约 1.5 s，过阈值后容量作用很小（实验，看图）〔P062 p12〕。
- 现网证据只有 Meta：CXL 扩展使缓存类吞吐 +25%、开发机每服务器 VM +33%、舰队规模 −15%、ML 参数服务器数 −25%（现网，自报）〔P058 p15〕。
- 架构上各家都把池子放在 HBM 之下、SSD 之上：SK hynix MARS 柜内 CXL、柜间 RDMA〔P268 p7〕〔P326 p4〕；Marvell 定义 G1.5/G2.5 两个"数十 TB @ 数百 ns"层〔P063 p6〕；Samsung 把推理中心 2030 描述为光子 fabric 连接的分解式内存 pod（目标，非实测）〔P354 p3, p4〕。

**判断2：池化解决了容量，没有解决互连带宽与能耗；近存计算（PNM）在检索、KV 选择等搬移密集任务上给出 10×–60× 级实验收益，但瓶颈在软件接口，不在芯片。**
- 带宽缺口（自报，Samsung 内部分析）：CXL 控制器后 DDR5 带宽 268.8 GB/s，而 PCIe Gen6 x8 只有 64 GB/s；控制器到主机的数据传输占能耗 67.2%〔P060 p22〕。
- 实验收益：10 个 PNM 设备做 512M 向量 IVF-Flat 检索，QPS 14.81 vs 主机 0.23（64×），能效 65×〔P060 p27〕；100K 上下文混合注意力 batch=5 时 17.7 vs 5.28 tok/s（3.35×）〔P060 p29〕；SK hynix 池侧 KV 选择平均缩减约 ×30，TTFT 比 LMCache 快 1.67×〔P326 p10, p12〕；Marvell 计算向量检索数据搬移降 60×（计算）〔P328 p9〕。
- 软件是短板：DCC 工作流开场即称"差距在软件而非芯片"〔P330 p4, p5〕；面板主张"先基准、后接口"，否则统一中间件会变成"杂物抽屉"〔P327 p12〕；Samsung 试过 oneAPI、OpenXLA PJRT、PyTorch 三条路径后自研 SPEL，Qwen3-0.6B 跑通但只给出调用次数与时间（实验，看图）〔P334 p2, p14〕。

**判断3：HBM 同时是 XPU 的面积、成本和热瓶颈；业界在"改造 HBM"（定制 base die、低功耗 D2D、混合键合）与"绕开 HBM"（DRAM-on-Compute、LPDDR 串行挂接、3D DRAM、HBF）两条线上并行投入。**
- 瓶颈量级（引用/自报）：HBM 约占 die 面积 30%、XPU 成本 >50%，按当前内存价格内存 BOM 在许多 GPGPU/ASIC 中 >60–80%〔P070 p3〕；HBM 堆栈贡献 2.5D 封装热阻 57%，ASIC 本体 13%（引用 ECTC 2026）〔P070 p7〕；HBM5 >28 Gbps 时热流 >2.0 W/mm²，高于 JEDEC 约 1.7 W/mm² 参考〔P070 p6〕。
- 改造路线：Marvell 定制 base die 回收最多 25% die 面积（自报）〔P070 p4〕；SBD D2D 64 Gbps/wire、常规负载功耗降 75%（自报）〔P070 p10〕；GUC 给出 HBM5 相对 HBM4E PHY 面积效率 0.3 → 0.75–1.0 TB/mm²，2029 年量产（自报/引用 SK hynix）〔P075 p7〕。
- 绕开路线：GUC DRAM-on-Compute（4 层整 reticle）32 TB/s、30 ns、0.5 pJ/bit，对比 6×HBM4E 24 TB/s、200 ns、2.5 pJ/bit，但最高温 125 vs 95°C（自报）〔P075 p8〕；Nallasway 用 50 个 LPDDR5X 串行模块挂在 reticle die 四周，3.2 TB/7.5 TB/s，对比 Jalapeño+6 HBM4 的 216 GB/15.4 TB/s（目标值）〔P450 p8〕；d-Matrix 6 nm、无 HBM 无 CoWoS，Raptor 用 3D DRAM（自报）〔P286 p24〕〔P317 p19〕；SK hynix HBF 容量为 HBM 14×、带宽 0.5×（自报，看图）〔P268 p15〕。

**判断4：D2D 互连按场景分层，UCIe 是互操作底线而非性能上限；OCE 标准的重心已从 PHY 转到固件、安全和"可验证的互操作"。**
- 性能侧走私有：GUC 称多数场景无需标准合规，GLink-LL 0.05–0.10 pJ/bit、1–3 ns，对比 UCIe-A 0.75 pJ/bit、10 ns+retry（自报）〔P075 p4〕；Marvell 称 UCIe 并非为下一代 HBM 带宽密度设计，HBM5 需约 6.4 Tbps/mm〔P070 p11, p14〕；LBNL 指出 UCIe/BoW 的 bump pitch >40 µm 带来串行化功耗与延迟，而 Intel 25 µm、TSMC 10 µm 已在推进〔P066 p20, p28〕。
- 成本侧与出封装：BoW.Flexi 1.0 最少 6 pin、0–4 Gb/s/pin、无链路训练，面向 MCU/模拟 chiplet〔P069 p3, p4〕；Credo 112G VSR 约 10 in、<1 pJ/bit、1.8 Tb/s/mm，填补 D2D（<25 mm）与长距（>1 m）之间的区间（自报）〔P067 p3〕。
- 系统层：FCSA 1.0.0 于 2026 年 2 月发布、1.1.0 本周批准，新增安全章节〔P079 p4〕〔P076 p4, p15〕；OCE 自述"无组织拥有完整开放系统结果"，2027 年目标从定义标准转为证明互操作〔P079 p2, p8〕；GSOC/AMD 认为 BoW 与 UCIe 只解决物理和协议层，还需 SCMI 固件 API 与 MCTP 传输对齐〔P078 p3, p5〕。

**判断5：封装内光 I/O 的出发点是 shoreline 几何约束；宽慢（VCSEL/µLED）与微环 CPO 两条路线的数字多为自报或目标，选哪种 D2D 接口取决于光引擎是否终结 FEC。**
- 几何约束（引用白皮书）：224G、reticle 级封装铜逃逸 26 Tb/s/dir，CPO 93.6，面阵光 I/O 1,191（46×）；半周边加 16 个 HBM 堆栈后 XPU 侧只剩 33 Tb/s/dir〔P455 p2〕；Baya 指出 die 边缘被 SerDes、UCIe、HBM PHY 争抢〔P064 p37〕。
- 宽慢路线（自报/目标）：Lumentum 1060 nm VCSEL HTOL 5000 h（115°C、Tj 181°C），1.6T 在 FIT<1（含 sparing）下需 30–54 路，带宽密度今日约 1 Tb/s/mm、路线约 4〔P444 p2, p3, p5〕；LightX-1 µVCSEL 57+57 lanes、3.2 Tb/s/引擎、<1.5 pJ/bit〔P338 p6〕；Avicena µLED 目标 >10 Tbps/mm、<1 pJ/bit，已出货 1 Tbps eKit（335 路 × 3 Gbps）〔P339 p8, p12〕。
- 微环/CPO 路线（设计/仿真）：Ayar Labs+Wiwynn 封装 8 个光引擎 + 8 个 HBM，每加速器 200+ Tbps，热仿真 SoC Tj 112°C、HBM4 75.4°C、OE 69.8°C〔P342 p7, p8〕。
- 接口选择：Eliyan 认为 UCIe 适合 EIC 终结 FEC/retimer 或单光纤场景，BoW 更适合高 radix、多光纤直驱 EIC，因其可非对称、可变 lane 数、可分别时钟 PPM；OCP-OCE 正在组建光互连工作组〔P071 p8, p13, p17, p18〕。

完整底稿：`_insight_index/synthesis/方向4_ScaleIn_综合底稿.md`

### 方向5：AI 基础设施底座（电力 800VDC/SST/BBU/储能/电网交互与功率平滑；冷却 冷板单相/两相、浸没、CDU/sidecar、水质与可靠性；机架与机械 ORv3/ORW/Mt Diablo、GW 级园区建设、交付周期）

**一句话结论：** OCP 2026 的底座议题已从"机柜能不能供上电、散掉热"转到"园区能不能按电网规则接入、按工厂节奏交付"。电力侧的共识路线是 800 VDC + 集中式 SST + 分层储能，NVIDIA 给出的设备就绪时间为 2026 Q3（机架级）到 2028 Q1（数据大厅级）；冷却侧单相冷板是当前主力，但 2.3 kW 级加速器已落入其经济边界之后的"回避区"；机架承重（4,700 kg 到 15,000 lb）和每柜数千到上万根光纤成为新的物理约束。决定节奏的是并网规则、流体与 DC 保护标准、设备交期，而不是单个器件的效率。

**判断1：机柜功率从 145 kW 走向 570 kW–1 MW，800 VDC 已进入设备排期；争论点是部署形态（sidecar / Power Center / SST Power Block），而不是要不要转。**
- NVIDIA 机柜代际：Gen1 GB200/GB300 54 VDC 145 kW → Gen2 Vera Rubin NVL72 330 kW → Gen3 570 kW（800 VDC 进 PSU、100% 液冷）→ Gen4 800 VDC 原生约 1 MW；设备就绪 A Power Rack Q3 2026、B Power Center Q2 2027、C Power Block Q1 2028（自报，看图）〔P167 p3, p17〕〔P252 p4, p23〕。
- 机制一（空间）：机架功率 ≥100 kW 时机架内转换与备份占 35%+ 空间，AC:DC 转换占 10–15%，N+N 翻倍，机架内 BBU 再占 10–15%；超过 600 kW 机架内 AC/DC 不可行（Google/NVIDIA 自报）〔P201 p4〕。Rittal/Bosch 称 480 VAC 约在 300 kW 到极限〔P031 p2〕。
- 机制二（电流）：48 V 母线在 1 MW 机柜下电流 18,519 A、母线铜损 >50 kW（xFusion 自报计算）〔P271 p12〕；同功率下 800 V 电流约 1/16、损耗约 1/256（理论推导）〔P375 p4〕。
- 板级配套跟进：Google/Meta/Microsoft 2026 Q4 启动 ±400V/800V 板载电源模块工作组，规格 Vin ±400V/800V ±10%、全砖 12 kW、效率峰值 >98.5%，目标 2H 2027 发布〔P190 p3, p10, p12〕。

**判断2：电网交互从运营方的内部问题变成并网准入条件；功率平滑需要从芯片到园区的分层储能，"负载模型"成为交付物。**
- 事件驱动：2024-07 北弗吉尼亚约 1,500 MW 电压敏感负载意外脱网〔P198 p2〕；NVIDIA/Danovo/Equinix 列出 2024–2026 多次数据中心自发减载，含 2026-07-22 Dominion 约 3,800 MW，FERC 2026-07-16 要求 NERC 于 2026-12-31 前提交计算负载可靠性标准（引用公开信息）〔P197 p3, p6〕。
- 规则已成文：MISO 10 MW/5 s 滑窗、30 MW/min；ERCOT 10 MW/5 s；SOCO 5–55 Hz 单频 2.5 MW（Microsoft 汇总）〔P028 p6〕；OCP VRT & PFAPR v1.0 计划 2026-10 发布，Power Ramp & Fluctuations v1.0 计划 2027-Q1〔P198 p9〕。
- 机制：同步 GPU 负载使设施功率毫秒级波动 30–60%，振荡能量集中在 0.2–3 Hz（Echion 引述）〔P182 p3〕；ML 负载约每年 100 万次循环，LFP 3k–10k 次循环不适用，需 BBU/CBU 双功能 + 机架级 EDLC（Google 自报）〔P178 p9, p10〕。
- 已有实测：Vera-Rubin NVL72 机架内 400 J/GPU 储能 + IPS，LLM 训练峰值功率降 13% / 51%（两组结果，实测，看图）〔P389 p3–p5〕；Skeleton 实测 sidecar 内 0.1 Hz 衰减 −72 dB、1 Hz −60 dB（实验，看图）〔P196 p7〕。

**判断3：单相冷板 2026 年已覆盖约 80% 顶级加速器 TDP，但 2.3 kW 级器件已越过其经济边界；两相、微流控、浸没各自推进，没有单一替代者。**
- 采用曲线：顶级加速器 TDP 中以冷板出货的比例约 24 个月内从 <10% 升到 >90%，看图 2026 约 78–80%、2028 约 97%（引用 Thermal Boundaries 白皮书，看图）〔P218 p16〕〔P210 p13〕。
- 边界：单相冷板（每 reticle 级器件）效率边界约 1.2 kW、经济边界约 2.1 kW、物理边界约 4.0 kW；两相冷板效率约 1.8 kW、经济约 3.4 kW；2026 领先加速器约 2.3 kW，落在单相回避区（看图估读，引用白皮书）〔P218 p24〕；按 2020 年以来趋势约 2029 年碰到 4 kW 墙〔P218 p15〕。
- 机制：Meta 拆解结到冷却液热阻，基线冷板 45% / TIM 20% / 硅 35%，冷板只占一半不到（看图）〔P010 p27〕；Wiwynn 指出单相转两相涉及工质、流动不稳定、流动架构、回路四方面，R1233zd(E) 在 2 kW 下结温均值约 93℃ vs PG25 约 78.5℃（实验，看图）〔P012 p2, p9〕，说明两相不是即插即用。
- 浸没处于"经济拉动、渐进不均"阶段：IT OEM 尚未规模出货浸没原生产品〔P233 p6–p8〕；Denvr 浸没 H200 在 neocloud 生产运行，NVLink 带宽与 DLC 差 −0.15%（实验）〔P228 p7, p17〕。

**判断4：液冷的主要风险已从"散不散得掉"转到流体化学、接口互操作与调试运维；OCP 在 2026 年密集发布流体与接口规范，但关键测试方法仍缺。**
- 现网水质问题：PG 25–27.2% 下 TVC 仍有 500–160,000 CFU/mL（现网，看图），PG≥25% 只是抑菌指引不是杀菌保证〔P006 p4, p5–p7〕；Ecolab 给出 PG 运行范围 24–29% v/v、azole >400 ppm〔P324 p8〕。
- 材料与流速：PG25 在 6.2 m/s 运行 93 天铜管无整体冲蚀，但弯头缓蚀膜约 8 nm vs 直管约 35 nm（实验 XPS）〔P008 p15〕；软管 pEPDM 析出物 352–6,379 ppm，配方差异大（实验，Phase 1）〔P249 p9〕；混用 PG25 缺少模拟工况方法，Phase 1 结果 2026-10 下旬才发布〔P217 p3, p8〕。
- 接口：UQD V2.0 首次试点跨厂商互操作测试，非标准插头倒角插拔力尖峰可达约 100 lbf（实验，看图）〔P003 p50, p52〕。
- 调试与运营成本：传统 TCS 管路 6 道冲洗、每道 5–7 天，预调试可从 7 周压到 1 周；每周延迟损失 \$300–400M（假设 100 MW/600 机架，看图，自报）〔P181 p3, p6〕；Meta 生产中 50+ 种液冷配置组合，湿度误报改用去抖与跨传感器过滤后事件约降 100 倍（看图，自报）〔P220 p8, p24〕。

**判断5：GW 级园区的交付瓶颈在电力接入与长交期设备；机架承重、标准化建筑模块和工厂集成成为提速手段，OCP 把范围从机柜扩到"电网到芯片"。**
- 交期：美国变压器交期 128 周（引用）〔P303 p3〕；发电机约 30→100 周、冷机约 20→75 周（2019→2025，McKinsey 引用/访谈）；美国能量接入最长 4–5 年，仅 65% 已宣布容量会投产（预测）〔P396 p4, p6〕；2026 设备交期全球平均 33 周、美国 42 周（引用）〔P387 p2〕。
- 机制：CMU 仿真把"芯片时间价值"计入后，建设 2 年的光储微电网 LCOE（计机会成本）\$0.642–0.690/kWh，低于 4 年接入的电网 \$1.01 和天然气 \$1.13（仿真，New Mexico 30 MW）〔P184 p13〕，部署速度比电价更重要。
- 机架与建筑：ORW 宽 1200 mm、最大载荷 4,700 kg，v1.0.0 已发布，2026-11 量产〔P030 p6, p11〕；Open DC v0.7 给出 2028+ 峰值 IT 密度 335 kW/ft（液冷）、ML 机架+sidecar 15,000 lb、集群基线 12 MW / 优选 24 MW〔P180 p3–p5〕。
- 工厂化：Crusoe 以工厂集成单元为故障域并逐单元通电〔P390 p4, p11〕；Aivres 欧洲 20 MW、约 100 柜项目 60 天交付（现网，自报）〔P291 p24〕；Foxconn 称 VR 相比 GB 自动化覆盖率 94% vs 56%、测试 FPY 80% vs 39%（自报）〔P261 p4〕。

完整底稿：`_insight_index/synthesis/方向5_基础设施底座_综合底稿.md`
