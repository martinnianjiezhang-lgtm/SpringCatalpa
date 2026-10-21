---
title: "R15_fti-workshop-short-reach-optical-interconnects"
tags:
  - OCP2026
  - 讲稿笔记
---

# R15 笔记：fti-workshop-short-reach-optical-interconnects / fts-ai-hpc / fts-data-center-sustainability

### P335 Architecting-Near-Packaged-Optics-for-AI-Datacenters-Key-Technology-Choices-and-Trade-offs
- 讲者/机构：Armaghan Eshaghi，Director, Optical Platform Solutions，Nokia | 类型：技术分享
- 方向归属（主/次）：Up（CPO/NPO/XPO）/ Out（可插拔光模块/LPO/LRO）
- 核心主张：
  1. NPO 与 CPO 同属一个能耗等级，但光引擎在 ASIC 封装之外、可替换，是近期可服务的路线 [p2][p8]。
  2. 调制器与激光器选择相互耦合：InP 天然配单片激光器，TFLN 和 SiPh 需要集成/封装内/外置光源；没有一种调制器在所有维度上胜出 [p4][p8]。
  3. 引擎移出主机热区后，片上激光器重新可行；外置激光（ELSFP）作为最热、最密场景的备选。最终胜出者取决于能否量产封装、冷却与制造 [p8]。
- 关键数据：
  - 链路功耗分级：Re-timed pluggable（1 SerDes+1 DSP）~15 pJ/bit；LRO（1 SerDes+½ DSP）~10 pJ/bit；LPO/NPO/CPO（1 SerDes）~6 pJ/bit；die-to-die 集成光学（0 SerDes）<4 pJ/bit，"距量产还有数年" [p2]（自报）
  - 激光到调制器损耗：单片 InP 0.25 dB；PIC 上集成 0.5–1 dB；封装内微光学耦合 1.5 dB；ELSFP 到调制器 2 dB（最高损耗与激光功率）[p5]（自报）
  - ELSFP 一个光源共享 4–16 lanes，需要 PM 光纤 [p5]（自报）
  - 客户要求到本十年末 InP 产能约 10×；Nokia 有 3 座 InP 厂：Sunnyvale 3 英寸（第一座）、San Jose 6 英寸（新）、Arizona 6 英寸（新）[p7]（自报）
  - 调制器定性比较：TFLN 带宽最高、损耗最低但长度最长；SiPh MZM 近无热敏但 RC 受限、损耗较高；SiPh MRM 驱动电压最低但需主动调谐；InP 可能需要 TEC [p4]（自报）
- 提到的公司/客户/产品/标准：Nokia（DC switch with NPO engines）、CPX Type 1/2 MSA、ELSFP、LGA/弹性体连接器
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（四档链路功耗 15/10/6/<4 pJ/bit 与服务模型对比）；p5（四种激光放置方式的损耗/热/服务对比表）

### P336 Beyond-Copper-Optical-Opportunities-for-AI-Scale-up-Fabrics
- 讲者/机构：Jian Chen，Network Architect，Dell Technologies | 类型：技术分享
- 方向归属（主/次）：Up（铜缆/CPO/NPO/XPO）/ Out（可插拔）
- 核心主张：
  1. "铜墙"是系统级约束：更大的 scale-up 域需要跨机柜、低功耗互连 [p3]。
  2. 过渡将是混合式：铜在可达范围内继续用，距离/密度/功耗不利时用光；全部换成传统可插拔光模块会带来不可接受的功耗、成本与可靠性代价 [p4]。
  3. CPO 有功耗和密度优势，但带来封装、可服务性、"爆炸半径"和厂商锁定问题；XPO 和 Open CPX 等"光学解耦"方案需要开放生态 [p6][p9]。
- 关键数据：
  - 200 Gb/s/lane 下无源铜通常仅几米；400 Gb/s/lane 及以上预计 <1 m [p3]（自报）
  - XPO 模块 64×200G lanes（12.8T）对比 OSFP 8×200G（1.6T）；带宽 8×、前面板密度 4× [p7]（引用 Arista）
  - XPO 支持液冷，同时支持 LPO 和高功耗相干 DWDM 光模块 [p7]（引用 Arista）
- 提到的公司/客户/产品/标准：Dell（XPO MSA 和 Open CPX MSA 成员；OCP Open Silicon Photonics for AI Systems 创始成员）、Arista、XPO MSA、Open CPX MSA（Type 1/Type 2）、ELSFP；术语 FRO/LRO/RTLR/LPO/NPC/NPO/NPX/CPC/CPO/CPX
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（XPO 12.8T 与 OSFP 1.6T 模块对比）

### P337 Dense-reliable-and-energy-efficient-interconnects-for-AI
- 讲者/机构：Jeff Hutchins，CTO Office, Dir of Optical Technologies（Ranovus，由 P345 p18 同一讲者署名推断；本 PDF 首页未写公司名）| 类型：技术分享
- 方向归属（主/次）：Up（CPO/NPO、机柜级互连）/ 运维/可靠性
- 核心主张：
  1. scale-up 主导机柜互连功耗，最低功耗方案将用 CPO 或其他低功耗选项 [p3]。
  2. scale-up 要尽量减少突发误码，避免 link flap 带来的尾延迟；关键不在"大管子"，而在达到目标 radix [p5][p6]。
  3. 外置 WDM 激光：mux 与分光放进 PIC，ELS 与 OE 按 1:1 部署以减小爆炸半径；行业成熟前 Tx/Rx 规格要兼容多种技术 [p9]。
- 关键数据：
  - 假想 72 GPU 光互连 pod（100GBd PAM4）链路功耗档：CPO 4 pJ/b、LTLR 6 pJ/b、RTLR 10 pJ/b、RTRR 15 pJ/b；pod 功率纵轴 0–120 kW [p3]（仿真/假设模型；各柱具体 kW 文字层未给出）
  - scale-out 带宽约为 scale-up 的 ~1/10，链路更少 [p3]（自报）
  - OCI-MSA：BiDi 4×50G/λ，2.5 dB，O 波段 Δf=400 GHz（2026）[p7][p8]（自报）
  - 200G/光纤实现选项：PSM 1×200G/λ（光纤数 2×）；COI-BiDi1 1×200G/λ Δλ=20nm（仅 CPO，推测性）；OCI G1 BiDi4 4×50G/λ（仅 CPO 或需 gearbox，受 shoreline 密度/能效限制）[p8]（自报）
  - 链路层演进：PCIe-like（2024）→ Ethernet-lite（2025/6：UALink、UEC、SUE-T、ESUN）；连接器：MPO/VSFF → EBO（2026）[p7]（自报）
- 提到的公司/客户/产品/标准：XPO-MSA、OIF High-Density 12.8T NPO 项目、OCI-MSA、UALink、UEC、SUE-T、ESUN、CBFC、ELS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（72 GPU pod 在 CPO/LTLR/RTLR/RTRR 四档下的功耗柱图）；p8（200G/光纤的多种实现对比）

### P338 High-Density-Optical-I-O-Using-Micro-VCSEL-Arrays-and-Multicore-Fiber
- 讲者/机构：Weipeng Zhang, Wenxuan Zhang, Manchen Hu，LightXcelerate Inc. | 类型：厂商技术分享
- 方向归属（主/次）：In（光 I/O）/ Up（CPO）、Across（多芯光纤）
- 核心主张：
  1. 背面出光 µVCSEL 阵列 + 多芯光纤（MCF）是"宽而原生"的 CPO 方案，用直接调制省去外置激光器和调制器 [p1][p4]。
  2. 用 OSAT 现成工艺（Cu pillar 倒装、underfill、TSV、被动光纤对准）实现量产 [p8]。
- 关键数据：
  - LightX-1 引擎：57 Tx + 57 Rx lanes；引擎占地 1.5 × 0.6 mm；当前 32 Gb/s/lane，路线图 64G，再到 100/200 Gb/s；3.2 Tb/s/引擎；50 m 传输；全链路 <1.5 pJ/bit；µVCSEL 比常规 VCSEL 小约 25× [p6]（自报）
  - 19 芯 MCF 替代 19 根光纤，1:1 图形匹配耦合 [p7]（自报）
  - DC 特性：阈值 ≈1.1 mA；6 mA 输出 ≈3.5 mW；斜率效率 ≈0.7 W/A [p9]（实验）
  - 高速：7 mA 下 S21 带宽 ~20 GHz；25 Gb/s NRZ（6 mA, 0.7 Vpp）眼图 mask margin 23.1%、ER 2.39 dB；32 Gb/s（7 mA）mask margin 5.5%、ER 1.88 dB [p10]（实验；看图确认）
  - 可靠性试验条件：HTOL 125 °C/9 mA；HTOL 85 °C/10 mA；OA 3 µm, 6 mA, Tj 165 °C（结果曲线在图中，文字层无数值）[p11]（实验）
  - 2025 年末以来光学领域战略投资 >\$15B：NVIDIA 光学生态 \$6B；Marvell 收购 Celestial AI \$3.25B（2026 年 2 月完成）；Meta–Corning 光纤供应协议最高 \$6B（2026 年 3 月宣布，商业供货，非股权）；Lumentum \$2B、Coherent \$2B、Marvell \$2B [p3]（引用公开公告）
- 提到的公司/客户/产品/标准：LightXcelerate LightX-1、NVIDIA GB200 NVL72、Marvell/Celestial AI、Meta、Corning、Lumentum、Coherent
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（LightX-1 引擎指标汇总）；p10（S21 与 25/32G 眼图，看图）

### P339 LED-Interconnects-Addressing-the-Future-of-Scale-In-and-Scale-Up-Connectivity
- 讲者/机构：Nigel Alvares，VP of Product and Marketing，Avicena | 类型：厂商技术分享
- 方向归属（主/次）：Up（机柜级互连）/ In（光 I/O、HBM）
- 核心主张：
  1. "能用铜就用铜，必须用光才用光"；现有光学方案在可靠性、功耗、延迟、耐温、成本上达不到 scale-up/scale-in 要求 [p3][p5]。
  2. µLED 支持端到端"宽而慢"架构，可替代 SerDes，消除 shoreline I/O 限制，同一架构同时服务 scale-up（替代 ≤10 m 铜缆）与 scale-in [p7][p9]。
- 关键数据：
  - 现有光学方案：>10 pJ/bit（含 >5 pJ/bit 主机 SerDes）；成本 >>>\$0.10/Gbps [p5]（自报）
  - µLED 目标：shoreline >10 Tbps/mm，面积 >10 Tbps/mm²；<1 pJ/bit（无阈值电流）；耐温 >200 °C；<\$0.10/Gbps；NRZ 原生，无 SerDes/DSP [p8]（自报/目标）
  - 每 lane 1–8 Gbps 的宽而慢 µLED 光学 [p7]（自报）
  - scale-up 距离：推理 ≤10 m，训练 ≤50 m [p2]（自报）
  - LightBundle 1Tbps ASIC：集成 300+ 驱动器和 TIA；约 1 mm² µLED 阵列支持 >1 Tbps；1Tbps eKit 为 335 个 µLED 通道 × 3 Gbps [p12]（自报）
  - 路线图：1Tbps eKit 已出货；1.6T–6.4T scale-up 光引擎即将推出；未来为专用 NPO/CPO 引擎 [p13]（自报）
- 提到的公司/客户/产品/标准：Avicena LightBundle、多芯光纤、HBM base die
- 首次/记录/SOTA 声明："Shipping world's 1st µLED interconnects: 1Tbps ASIC-powered" [p12]
- 推荐配图页：p8（µLED 对照七项需求的指标）；p12（LightBundle 1Tbps ASIC 与 eKit）

### P340 Laser-Sources-to-Simplify-Slow-and-Wide-Optical-Interconnects
- 讲者/机构：Alan Liu，CEO，Quintessent | 类型：厂商技术分享
- 方向归属（主/次）：Up（CPO/NPO 外置光源）/ In（光 I/O）
- 核心主张：
  1. O 波段 GaAs 量子点键合到硅光平台，绕开 InP、电子束光刻、二次外延、隔离器等供应链瓶颈 [p5][p14]。
  2. 同一平台可做单波长 QD DFB 和多波长梳状激光器，服务 OCI-MSA DWDM 光源与 ELSFP [p7][p14]。
- 关键数据：
  - 6 英寸 GaAs 衬底上已生长 750+ 片晶圆；3 个外延批次共约 3000 个激光器（946/1019/988），未优化 WPE 集中在 25–30% [p3]（实验，EVT 阶段）
  - FP 量子点激光器 80 °C、125 mA（约对应 30 mW 输出）加速老化已超过 22,000 h 仍稳定；另启动 >150 器件的可靠性测试 [p4]（实验，初步）
  - 单腔单偏置 8λ 梳：芯片 3 × 0.25 mm，2.0 dB 平坦度，偏置 50 mA [p8]；20–110 °C 梳谱保持均匀 [p9]（实验，看图）
  - 梳状激光器峰值 WPE >20%，硅波导内总输出 >80 mW [p10]（实验）
  - 8λ 梳 + SOA：200 mW 总功率，>25 mW/λ，2 dB 均匀度 [p11]（实验）
  - 8×200 GHz DFB+SOA 阵列：>55 dB SMSR，硅波导内单侧功率最高 85 mW [p12]（实验）
  - QD DFB 在 -15 dB 光反馈下 RIN 仍约 -150 dBc/Hz，可能无需隔离器 [p13]（实验）
  - 下一步：OCI-MSA 光源 4λ × 400 GHz/组、一组一个梳；ELSFP 形态 [p14]（计划）
- 提到的公司/客户/产品/标准：Quintessent、OCI-MSA、ELSFP、CPO ELS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（20–110 °C 梳谱均匀，看图）；p11（200 mW 8λ comb+SOA）

### P341 Open-CPX-Optical-Engine-With-Integrated-Laser
- 讲者/机构：Rang-Chen (Ryan) Yu，VP Marketing，TeraHop | 类型：厂商技术分享/标准进展
- 方向归属（主/次）：Up（CPO/NPO/XPO）/ Out（可插拔光模块）
- 核心主张：
  1. 带集成激光的 NPO（ILS）优于 CPO+ELSFP：省掉额外耦合、PM 光纤与盲插连接器的损耗和失效点 [p11]。
  2. 硅光 PIC 与 CW 激光已有足够现网可靠性数据支撑集成激光 [p13][p14]。
  3. "宽而慢"光学需要反向 gearbox SerDes，抵消了光学部分的功耗优势 [p15]。
- 关键数据：
  - AI scale-up 带宽约为 scale-out 的 10×：例 NV VR scale-up 72×200G=14.4 Tbps，ConnectX-9 SuperNIC 1.6 Tbps [p3]（引用 NVIDIA）
  - Open CPX MSA：OFC 2026 宣布，50+ 成员，Release 1.0 于 2026-09-16/17 发布（两页日期不一致）；预计 2027 年内生产部署 [p4][p5]（自报）
  - 12.8T XPO MSA 于 OFC 2026 宣布，预计 2027 年内生产部署；25.6T XPO+ 早期开发；1.6T OSFP 全面量产；IMDD 3.2T 约 2027–2028 [p4]（自报）
  - Open CPX 路线图：Rev 1.0（2026/9）32/36×200G，Type 1&2，ILM&ELM；Rev 1.1（2027/3）铜介质、Type 3；Rev 2.0（2027/6）64/72×200G；Rev 3.0（2027 末/2028 初）N×400G [p16]（看图）
  - Diablo-1 6.4T NPO：32 通道 BER 曲线，ER=3 dB，TECQ=2.1 dB，ASIC 到 NPO 插损约 12 dB [p9]（实验，初步；看图）
  - 1 km 光纤传输 4 通道 BER：1.86E-9、6.19E-10、1.25E-9、3.45E-9（每通道约 6.8–6.9E12 bit）[p10]（实验，看图）
  - Diablo-1 功耗约 5.5 pJ/b（含内置激光）[p11]（自报）；柱图估读：CPO+ELS ~6.6、Diablo-1 NPO+ILS ~5.75、LPO ~6.4、50G NRZ ELS DWDM+RGB ~9.2、50G NRZ ILS PSM+RGB ~7.4、uVCSEL+RGB ~5.75、uLED+RGB ~5.95 pJ/b，反向 gearbox 约占 ~3.9 pJ/b [p15]（看图估读）
  - ELSFP 方案：额外耦合与连接器损失 >3 dB → 需要 >2× CW 激光功率（200–300 mW+），CW LD 功耗约增加 4× [p11]（自报）
  - TeraHop 已出货硅光收发器 PIC 累计 >100B device-hours，FIT <0.01；CW LD Vendor E FIT <0.01、Vendor A FIT <0.03 [p13][p14]（现网，自报）；6.4T NPO-ILS 估算 FIT 约 1.2（看图估读）[p14]
- 提到的公司/客户/产品/标准：TeraHop Diablo-1、Arista（100T 交换机设计概念）、NVIDIA NVL72/NVL576/ConnectX-9、Intel 集成激光 PIC、Open CPX MSA、XPO MSA、OCI MSA、OSFP、"Coherent Lite" 1.6T-CL/3.2T-CL
- 首次/记录/SOTA 声明："Industry 1st 100T Switch with Open CPX Optics"（Arista 设计概念，配 TeraHop 6.4T Diablo-1）[p12]
- 推荐配图页：p15（7 种光学方案 pJ/b 分项堆叠图，看图）；p16（Open CPX MSA 路线图，看图）；p14（FIT 对累计器件小时图）

### P342 Optical-Scale-Up-AI-architecture-with-Co-Packaged-Optics-with-Open-Rack-Scale-Infrastructure
- 讲者/机构：Kinny Chen（Sr. Manager of Pioneering Center, Wiwynn）、Vishal Chandrasekar（Director of Product Management, Ayar Labs）| 类型：技术分享
- 方向归属（主/次）：Up（CPO、机柜级互连、UCIe）/ 底座-机架/机械、底座-冷却
- 核心主张：
  1. 更大模型需要更大 scale-up 域；从 1024-ASIC pod 目标自上而下设计到机柜、托盘、光纤和多芯片封装 [p2]。
  2. 设计难点：两个热域（ASIC/OE 与 ELSFP）、前面板 ELSFP 需可热插拔、光纤作为结构件、电源树分散、跨供应商测试边界 [p3]。
- 关键数据：
  - 1024-ASIC scale-up pod 相比最小评估配置系统性能约 10× [p2]（预测/仿真）
  - 单级拓扑 ASIC–Switch–ASIC；每个交换机机柜 32×1OU scale-up 交换托盘 + shuffle box；每个计算机柜 32×1OU 计算托盘；每个 ASIC 连接每个交换机 [p4][p5]（设计）
  - L10 托盘：805 mm × 537 mm × 46.5 mm；2× CPO ASIC 板、16× ELSFP、12V→3.3V PDB、OCP 3.0 NIC [p6]（设计）
  - 封装：8 个片上光引擎、8 个 HBM 堆栈，每加速器 200+ Tbps scale-up 带宽、数百条 scale-up 链路；微环架构，OCI-MSA 光 PHY；UCIe-A 转 UCIe-S [p7]（设计）
  - 热仿真（冲击式冷板，4.5 LPM，Ta 25 °C）：SoC Tj-max 112 °C（规格 125）；HBM4 75.4 °C（95）；IO 59.9 °C（125）；OE 69.8 °C（100）；ASIC 冷板压降 11.2 kPa，OE 冷板压降 18.8 kPa [p8]（仿真）
  - 电源：48 V/±400 V/800 V 后部输入，前部 3.3 V [p3]（设计）
- 提到的公司/客户/产品/标准：Wiwynn、Ayar Labs、ELSFP、MPO/MMC/EBO、DC-SCM、OCP 3.0 NIC、UCIe-A/UCIe-S、OCI-MSA、HBM4
- 首次/记录/SOTA 声明：无（展位 #C74 有实机 CPO 托盘 [p10]）
- 推荐配图页：p8（封装热仿真与 Tj 表）；p6（L10 托盘布局）

### P343 Predictable-Performance-Link-Stability-and-density-Advancing-field-ready-lens-connectivity-for-next-generation-ai-networks
- 讲者/机构：Rebecca Lovely（Solutions Innovation Engineer, Lensed Connectivity），合作者 Michael Ransford、Josh Wilken，Corning | 类型：厂商技术分享
- 方向归属（主/次）：Up（机柜级互连、光连接器）/ 运维/可靠性
- 核心主张：
  1. scale-up 光化使每机柜光纤数快速增长，传统连接器在空间和安装人工上都会成为瓶颈 [p6]–[p10]。
  2. 扩束透镜连接器（MMC with Prizm TMT）抗灰尘、插拔稳定、不需清洁，部署速度明显更快 [p11]–[p14]。
- 关键数据：
  - 每计算机柜 scale-up+out 光纤：Vera Rubin NVL72（2026）~1k；Rubin Ultra NVL576（2027）~10k；Feynman NVL1152（2028）~30k；Feynman Next（2029+）~45k [p6]（预测）
  - 对应安装时间：9 h / 95 h / 280 h / 420 h（16 芯跳线，拆包布线 3 min，每端插接 3 min 含检查清洁）[p9]（预测/模型）
  - 16 端口部署计时：MMC with Prizm 8 min 43 s（9.3 h/机柜）对比物理接触 MMC 1 h 19 min 23 s（84.7 h/机柜），快 89% [p11]（实验）
  - 5 对连接器、50 次插拔不清洁：物理接触最大 ΔIL 1.42 dB，透镜 0.26 dB（低 81%）；灰尘覆盖芯区 15%（透镜）对 100%（物理接触）[p13][p17]（实验）
  - 箱线图：透镜 ΔIL 中位约 0.11 dB，物理接触中位约 0.25 dB [p12]（看图估读）
  - GR-1435 4.4.4 凝露测试（65 °C、95% RH）最大 ΔIL 0.29 dB @1310 nm（规格 <0.3 dB）[p14]（实验）
  - 1RU 内光纤数：16 芯 MMC 4,224 芯，32 芯 MMC 8,448 芯；前面板密度 3–6×，插拔力为物理接触的 30%，清洁耗材减少 94% [p15]（自报）
  - 90 天从实验到量产部署；2 天把物理接触 MMC 产线转成透镜产线；连接器插损目标 0.5 dB [p16]（自报）
- 提到的公司/客户/产品/标准：Corning MMC with Prizm TMT、EXFO FTBx-88480、Hisense 800G 2DR4、NVIDIA Vera Rubin/Rubin Ultra/Feynman、MGX 机柜、GR-1435、VSFF
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（每机柜光纤数与安装工时随代际增长）；p13（50 次插拔灰尘下 ΔIL 对比）

### P344 Rack-Ready-High-Power-ELSFPs-A-Co-Development-to-Support-CPO-Deployment-in-AI-Scale-Up-and-Scale-Out-Datacenters
- 讲者/机构：Nandita Aggarwal（Sr. Manager, Laser Engineering, Ayar Labs）、Willie Chen（Technical Supervisor, Wiwynn）| 类型：技术分享
- 方向归属（主/次）：Up（CPO 外置光源）/ 底座-冷却
- 核心主张：
  1. Wiwynn 定义冷却边界条件，Ayar Labs 据此设计 ELSFP，联合 CFD 使模块表面温度均匀，降低 TEC 功耗、延长寿命 [p2][p3]。
  2. 前插 ELSFP 可服务，冷板 + 弹性 TIM 设计支持反复插拔 [p6][p9]。
- 关键数据：
  - ELSFP：8 × 23 dBm 通道/模块，内置主动 TEC，多供应商激光芯片 [p2]（自报）
  - 测试 100+ 模块（50 °C 激光芯片温度、-20 dB 回反、全部激光开启、45 °C 进水）：平均输出 23.4 dBm（σ 0.32 dB）；SMSR 均值 53 dB（σ 1.5，全部 >47 dB，规格 >40）；线宽均值 0.16 MHz（σ 0.04，全部 <0.37 MHz，规格 <1 MHz）；RIN 均值 -158 dB/Hz（σ 0.8，全部 <-154，规格 <-150）；单通道 RIN 至 26.5 GHz 低于 -150 dB/Hz [p4][p5]（实验）
  - 表面温度不均匀度降低 >3× [p3]（仿真/实验）
  - 冷板：1OU 内冷却 20 个背靠背 ELSFP；均匀鳍距时板面温差 2.9 °C，改用局部鳍距后 0.8 °C [p6][p7]（实验）
  - 弹性 TIM（石墨 + 铍铜弹簧片）经数百次插拔无磨损 [p6]（实验）
  - 20 个 ELSFP 激光芯片温度 50 ±1 °C（冷却液 45 °C、1.3 LPM）[p8]（实验）
- 提到的公司/客户/产品/标准：Ayar Labs、Wiwynn（L11 机柜、L10 托盘）、ELSFP
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（100+ ELSFP 的功率/SMSR/线宽/RIN 分布）；p7（均匀鳍与局部鳍的热分布对比）

### P345 Scale-up-optical-reliability-and-GPU-system-resiliency-to-optical-link-flaps
- 讲者/机构：面板，主持 Edi Roytman（Marvell，ex Microsoft）；分讲：Lenin Patra（SVP Data Center Architecture, Marvell）[p2]；Jeff Hutchins（Director, CTO office, Ranovus）[p18]；Eduard (Edi) Roytman & Dr. Greg Link（Microsoft）[p26] | 类型：面板
- 方向归属（主/次）：运维/可靠性/遥测 / Up（CPO/NPO、机柜级互连）
- 核心主张：
  1. scale-up 光 I/O 必须达到今天无源铜的可靠性；flap 在大规模集群中会成为全网事件，多层链路弹性是必需（Marvell）[p7][p11][p15]。
  2. 低延迟 scale-up 用较弱 FEC，需要更低随机 BER；突发误码是导致重传和 flap 的关键，应标准化遥测与测试方法（Ranovus）[p22]–[p24]。
  3. GPU/XPU 不像交换机那样能处理 flap；需要把同一端口的 lanes 分到不同 flap 故障域，并采取主动、在线、事后三类措施（Microsoft）[p27][p32][p35]。
- 关键数据：
  - scale-up 光学目标：距离 >20 m；每 SoC >50 Tbps/方向；延迟 <20 ns；ASIC 带宽密度 >4 Tbps/mm²；能效 <4 pJ/b；pre-FEC BER <1e-9；FEC 延迟 <75 ns；flap <1% 链路（WIP）[p7]（引用行业规格）
  - "2025 模型"：~3M GPU、>10M 光链路，约每 48 秒一次 flap [p11]（Marvell 估算）
  - V7 pod：144 机柜 × 96 ICI 光口 = 13,824 根光纤 → 48 台 OCS（288 有效端口），比例 1.5:1；9K XPU 一个 super pod [p8]（引用）
  - RELIANT 恢复时间分层：物理层实时；链路重试近即时；链路级 <1 ms；应用级 ~500 ms；fleet 级 >1 s [p14]（自报）
  - Ethernet FEC RS(544,514) 可纠正最多 15 个出错码字；在 3.2e-5 重传率上限示例下，可容许随机 BER 约 1e-3；考虑突发后约 3e-5；更低延迟 FEC 需要约 1e-8 [p20]–[p22]（仿真/近似分析；p20 看图）
  - Meta 报告 CPO 交换机 >1e6 个 400G-port-device-hours 无不可纠正码字 [p20]（引用 ECOC25 Tu.01.03.3）
  - Flap-FIT 表：10,000 Flap FIT 时 1024 GPU pod MTBF 0.76 h，50% 概率首次 flap 时间约 0.5 h；10 Flap FIT 时 1024 GPU MTBF 762.94 h [p28]（示意计算，"非现网数据"）
  - 1 条 lane flap：1×800 模式 → job abort；4×200 模式 → 降级为 3×200 或 2×200；若 4 条 lane 分属不同故障域，单 lane flap 概率为 P 时 4 条同时 flap 概率约 P⁴ [p30]–[p32]（分析）
  - 流程分层：Detect（~ms，链路级）→ Contain（~ms 到 s，fabric 级）→ Heal/Reroute（~s，workload 级）[p13]（看图）
- 提到的公司/客户/产品/标准：Marvell RELIANT telemetry、Ranovus、Microsoft、Meta、OCI-MSA、CBFC、MRC、ECMP、TCP、XPO、OSFP、OCS、OCP Networking Optical Reliability workstream、OCP SROI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p28（Flap-FIT × pod 规模的 MTBF 表）；p7（scale-up 光对铜的指标对照）；p14（RELIANT 分层恢复时间）

### P346 Short-Reach-Optical-Interface-for-Scale-up
- 讲者/机构：Ron Swartzentruber（AMD）、Bobby Lu（Lightelligence），OCP SROI Workstream Chairs | 类型：标准进展
- 方向归属（主/次）：Up（机柜级互连、CPO/NPO、UALink/ESUN）/ Out（OCS、LPO）
- 核心主张：
  1. SROI（1–30 m）是独立的光学距离区间，优化目标是封装边界 lane 密度、pJ/b、每 lane 成本和可靠性，而不是衰减、色散、OSNR 和 DSP [p3]。
  2. 分层部署：现在用可插拔 LPO/RTLR，1–2 年过渡到 NPO（CPX MSA），2–3 年以上走向 CPO（CPX MSA / OCI MSA BiDi）[p6]。
  3. OCP 应尽早统一需求，避免碎片化，与 IEEE/OIF/JEDEC、UALink/ESUN/CXL 对齐 [p8]。
- 关键数据：
  - 200 Gb/s/lane 无源铜上限约 1–1.5 m；多机柜 pod 跨度 30 m；下一代 pod 500–1000+ 加速器；未来每机柜数万条光 lane；加速器换代周期 12–18 个月 [p2]（自报）
  - 铜距离表：无源背板 ~1–1.5 m；NPC 飞线 1.4 m；CPC 1.5 m 以上；re-driver ~2.0 m；re-timer ~2.5–3.0 m（每级 ~50 ns）；>3 m 必须用光；400G PAM4 CPC-CPC ~1 m [p11]（引用 IEEE 802.3dj、OIF 研究）
  - SROI 需求：每链路端 ≤5 pJ/b（仅光学）、≤10 pJ/b（SerDes+光学），10 pJ/b 为铜转光的分界点，当前 CPO 4–5 pJ/b；成本目标对标 AEC \$/Gbit/m，无源铜约 \$0.05/Gbit，差距约 10×；可靠性 ≤2 FIT/链路端、每 1M 器件小时 0 次 flap，可插拔 50–100 FIT；延迟目标为光路无 retimer（每 retimer ~50 ns，1 m 光纤 ~5 ns）[p5]（需求/目标）
  - 方案指标：LPO 5–6 pJ/b、RTLR 8–10 pJ/b，1.6T→3.2T+；NPO ~5 pJ/b，6.4T→12.8T；CPO 4–5 pJ/b（PAM4）/ 3 pJ/b（DWDM），FIT 比可插拔好 5× [p6]（自报）
  - scale-up 与 scale-out：<30 m 对 <2 km；RTT <1 µs 对 <10 µs；每 XPU ~1,000 GB/s 对 ~400 Gb/s；规模 256 到 1,000+ XPU 对最多 10,000 节点 [p4][p12]（自报）
  - 封装节距与电接口损耗：FPO >22 dB/200G；NPO-PCB 16–22 dB/200G（flex/cable 13–18）；NPO-HDI 13–18 dB/200G；CPO C4 ~110 µm，CPO-AP µbump ~30–50 µm [p7]（看图）
  - 400G/lane：光学倾向 PAM4，铜倾向 PAM6；SiPh 等离子色散带宽不足以支持 400G PAM4，需与 InP 或 LiNbO₃ 混合集成 [p14]（自报）
- 提到的公司/客户/产品/标准：AMD、Lightelligence、UALink、ESUN、NVLink、PCIe Gen7、CXL、NVMe、InfiniBand、Ultra Ethernet、CPX MSA、OCI-MSA（2026 年 3 月）、IEEE 802.3dj、OIF、JEDEC、Telcordia/AEC、OCS（MEMS/LCoS/压电/机械臂）、SROI 白皮书与 Appendix A
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（SROI 四项系统需求）；p6（可插拔/NPO/CPO 三层部署对比）；p7（光连接术语表，看图）

### P347 AI-HPC-Lightning-Talks
- 讲者/机构：合集，5 个闪电演讲：Gerald Bode & Florian Engel（Nlevel）[p2]；Injae Kang & Jaehoon Shim（首尔大学）[p9]；M A Awal & Jason Barmann（EPC Power）[p18]；Zhenshuai Rong & Yingchao Chi（剑桥大学）[p26]；Marco Pritoni（LBNL）、Nauman Rafique、Leonardo Bachega（Visum AI）[p38] | 类型：技术分享（闪电演讲合集）
- 方向归属（主/次）：底座-电力 / 存储、运维/可靠性
- 核心主张：
  1. Nlevel：集中式 AC-UPS-DC 链路无法扩展，提出 Real-Time Energy Routing（按可寻址能量包路由、无中心、电压无关），倡议建立 OCP 能量路由工作组 [p4]–[p7]。
  2. 剑桥：去掉 6/12 V 中间母线，用单级垂直 48V-to-core VRM 简化供电路径、提升端到端效率 [p27]–[p30]（看图）。
  3. LBNL/Visum：用语义图（扩展 Brick schema）把操作规程与设备关联，使规程可机器校验 [p41]。
- 关键数据：
  - NVMeNext（GPU 发起 I/O 的 SSD 仿真器）：SSD 配置 16 NAND 通道、32 planes/通道、15 µs 读延迟；吞吐表中最高约 32.9（单位文字层未标，推测为 MIOPS 级，存疑）；warp 级合并后 MOLIERE BFS 69.0→17.8 s、CC 118.1→45.5 s；Orkut BFS 2.08→0.69 s、CC 2.48→1.27 s [p15]（实验）
  - EPC Power：5 MW 积木单元，数百个组合成多 GW；以太网 PHY 测量，补偿延迟 <2 ms；实验室验证 0→95% 负载阶跃 [p20][p21][p24]（实验/自报）
  - 剑桥：全球数据中心用电 485→950 TWh/年（2025→2030，引用 IEA）；端到端效率提高约 2 个百分点 ≈ 节电 19 TWh/年，≈\$1.9B/年（\$0.10/kWh，示意）[p27]（看图）
  - 剑桥：23 kW（WSE-3 尺度）下 6 V 母线 ≈3.8 kA，0.1 mΩ 电阻导通损耗 ≈1.47 kW；6 V 对 48 V 电流 8×、I²R 损耗 64× [p28]（看图，计算）
  - 剑桥原型：54 V→0.8 V / 240 A；电流密度 ≈1.5 A/mm²；功率密度 2966 W/in³；峰值效率 90.6%；尺寸 17 × 10.4 × 6 mm [p30][p35]（实验，看图）
  - LBNL：ASHRAE TC 9.9 报告 CDU 泵故障到处理器降频仅 23 秒；一次冷却维护的程序错误导致 11 小时停机 [p39]（引用 ASHRAE 2024、Uptime Institute 2026）；在 OCP Deschutes CDU 规范全量抽取上 0 个 SHACL 违规 [p42]（实验）
- 提到的公司/客户/产品/标准：Nlevel RER、NVMeVirt/NVMeNext、NVIDIA Storage-Next、Intel DSA、EPC Power Agile Grid-Forming BESS、ERCOT NOGRR282、Cerebras WSE-3（作功率尺度示例）、IVR、TLVR、Brick schema v1.4.4、ASHRAE 223、NVIDIA AIF USD、OCP Deschutes CDU
- 首次/记录/SOTA 声明：无
- 推荐配图页：p35（54V-to-core VRM 原型与效率曲线，看图）；p28（低压母线损耗计算，看图）

### P348 Copper-Sintering-BGA-Interconnect-for-Mitigating-Electromigration-in-High-Current-AI-Power-Delivery（精简）
- 讲者/机构：Chengjie Du、Xufu Ren，剑桥大学工程系 | 类型：技术分享
- 方向归属（主/次）：底座-电力 / In（封装互连）
- 核心主张：
  1. 高电流 AI 供电中焊料 BGA 存在电迁移失效风险，电流密度预计将超过 2 A/mm² [p2]。
  2. 纳米铜烧结 BGA 互连可显著提升电迁移可靠性 [p5]。
- 关键数据：
  - 50 A/mm² 下 SAC305 在约 300 h 开路失效，烧结 Cu BGA 稳定导通超过 900 h [p5]（实验）
  - 看图：5 个 SAC305 样品约在 260–330 h 间全部开路；5 个烧结 Cu 样品电压约 0.21–0.23 V 平稳到 900 h [p5]（看图）
  - SAC305 在 300 h 时阳极界面原子聚集明显；烧结 Cu 在 900 h 时成分变化可忽略 [p8]（实验）
- 推荐配图页：p5（SAC305 与烧结 Cu 电迁移电压-时间曲线）

### P350 Investigation-of-Diamond-Based-Materials-for-Direct-Liquid-Cooling-of-Next-Generation-AI-Chips（精简）
- 讲者/机构：Nick Liu（Thermal Engineer）、Jake Hsieh（Assistant Technical Manager），Wiwynn | 类型：技术分享
- 方向归属（主/次）：底座-冷却
- 核心主张：
  1. 先进封装可能使芯片热流密度超过 500 W/cm²；冷板和 TIM 占总热阻 65–85%，是主要降热阻环节 [p2]。
  2. 单晶金刚石微通道直接键合到硅上可大幅降低热阻；仿真与实测的差距来自键合界面热阻 [p9]。
- 关键数据：
  - 热流密度：2022 年 100 W/cm²，2026 年 200 W/cm²，2030 年超过 500 W/cm²；热阻构成：冷板 40–45%，TIM 25–40%，芯片 15–25% [p2]（自报/预测）
  - 热导率：单晶金刚石 >2,000、金刚石铜 600–900、金刚石 SiC 500–800、铜 ~400 W/m·K；CTE 分别为 ~1.0 / 6–9 / 2.0–4.5 / ~17 ppm/K（硅 ~2.6）[p3]（引用材料数据）
  - 微通道：鳍宽/间距 0.1 mm，鳍高 1 mm，底厚 0.5 mm，面积 32.2 × 25.7 mm²；Ti/Ni/Au 金属化 + 铟焊料回流键合 [p5]（实验）
  - 360 W/cm²（3,000 W）下：基线铜冷板 + PCM TIM Tj 106.2 °C、Rth 0.0254 °C/W；金刚石微通道 Tj 77.1 °C、Rth 0.0157 °C/W，降低 38.2%（仿真为 59.5%）；条件 PG25、进水 30 °C、2 LPM/kW [p9]（实验）
- 推荐配图页：p9（三种热流密度下基线与金刚石方案的 Tj/Rth 对比表）
