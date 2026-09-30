---
title: "B73 · DAY4 · We5-I VESEL"
tags:
  - ECOC2026
  - DAY4
---

## B73 笔记（We5-I VCSEL 专场，2026-09-23，Malaga）

说明：页码 pN 为 PDF 页码（比幻灯片右下角编号大 1，Coherent/Lumentum/东工大/博升/Tampere 均如此）。数值来自图片核对；未看图的页仅用 OCR，已注明。

### We5-I Coherent.pdf（第1–12页）
- 讲者/机构：M. Ganzhorn（划线讲者）等 / Coherent | 题目：2.3 Tbit/s Backside-Emitting 1060 nm VCSEL Array on Silicon Interposer for CPO Applications（Paper ID #504） | 类型：学术论文（邀请专场 We5-I）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 3 Scale-out 224G/448G/光源
- 核心主张：
  1. 铜互连终将被光取代；一旦如此，可以"慢而宽"（空间/WDM复用降低单lane速率），追求效率、可靠性、冗余、密度，VCSEL 在各码率下效率高、成熟度高、耦合简单 [p4]
  2. 1060 nm 背发射（BSE）VCSEL + GaAs 衬底背面透镜 + 倒装到硅中介层，是通向高密度 CPO 光源的路径 [p5, p6, p12]
  3. 六边形 BSE μVCSEL 阵列，单发射器带宽可达 100 Gbit/s，等效带宽密度最高 9 Tbit/s/mm² [p12]
- 关键数据：
  - 1060 nm 单器件 L-I-V：输出功率约 4 mW 量级、电流至约 20 mA，波长约 1060 nm 单峰（结论页小图，读数粗略）[p12]
  - 硅中介层上 16 通道（2×8）阵列：32 Gbit/s，I=6 mA，Vpp=0.4 V，无DSP，各通道 SNR 约 5.5–7.4；128 Gbit/s，I=12 mA，Rx/Tx 各7 tap，各通道 TDECQ 约 1.95–3.64 dB（个别 14 mA）[p9]
  - 阵列节距 160 μm 对应 >3.2 Tbit/s/mm²；阵列 Max P 约 5.65–5.95 mW，Ith 约 0.66–0.80 mA（色标读数）[p9]
  - 单器件：32 Gbit/s @25°C SNR 7.37（I=6 mA，Vpp=400 mV）；@125°C SNR 6.33，ER 3.6（无DSP）；64 Gbit/s SNR 3.38（I=12 mA，Vpp=1 V，无DSP）；106.25 Gbit/s TDECQ 1.12 dB（I=10 mA）；128 Gbit/s TDECQ 2.04 dB（Rx7 tap/Tx7 tap）[p8]
  - S21 随电流（6–14 mA）与温度（65–125°C，@8 mA）曲线测到40 GHz；积分 RIN 随电流/温度曲线，25°C约-154 dB/Hz、125°C约-146 dB/Hz（曲线读数粗略）[p8]
  - 37 发射器六边形阵列，节距 70 μm（含背面透镜）；106 Gbit/s TDECQ 2.52 dB（I=12 mA，7 tap Rx&Tx）；32 Gbit/s SNR 6.68，ER 3.9 dB，margin 5.6%（I=6 mA，无DSP）[p10, p12]
  - 前面板引用 Julie Eng OFC 2026：聚合带宽在 <2 km / <40 m 的对比（数值看不清）[p3, 仅OCR]
- 提到的公司/客户/产品/标准：Coherent（自家）；引用 Julie Eng（OFC 2026）；现场 booth 有 full link 演示（BSE VCSEL–MFC–BSI PD）[p11]
- 与业界对比或记录声明（SOTA/首次/record）：未使用"record/首次"措辞；给出 9 Tbit/s/mm² 等效带宽密度为展望值 [p12]
- 推荐配图页：p9（16通道阵列逐通道 32G/128G 眼图+中介层照片，最能体现阵列一致性）；p8（S21/RIN/温度与眼图汇总）

### We5-I Lumentum.pdf（第1–18页）
- 讲者/机构：讲者姓名幻灯片中未见 / Lumentum | 题目：1060nm VCSEL Arrays for Scale-Up | 类型：邀请报告（产业发布/路线）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 3 Scale-out 224G/448G/光源
- 核心主张：
  1. 金属互连在带宽×距离上触顶，VCSEL/光纤/PD 阵列可以以低 pJ/bit 覆盖更长距离，是 scale-up 光互连的有吸引力方案 [p4, p18]
  2. 首个实现预计使用 NRZ（宽并行不需要很高单lane带宽）；相对 InP/TFLN/SiPh 在密度、外置激光/驱动功耗、可靠性(<1 FIT 借助冗余备份)上占优 [p5, p10]
  3. 依托 6 英寸 GaAs 与 3D 传感(3DS) VCSEL 供应链，无需 burn-in 即可达 <50 ppm/发射器寿命失效率目标；数月内将给出倒装阵列更高速度/高温/可靠性数据 [p16, p17, p18]
- 关键数据：
  - 第一代 VCSEL/PD 阵列示例：64 Gb/s NRZ × 256 通道（8 Tb/s），2.0 mm shoreline，2.5 pJ/bit；图中 FoM（带宽密度×能效）VCSEL/PD 阵列对光收发器约 2000x、对当前先进光约 20x（引自 G. Keeler, DARPA MTO ERI Summit 2019 的坐标图）[p4]
  - 器件：倒装背发射，Cu pillar+焊料，光经 GaAs 衬底（150 μm n型）+集成透镜出射，倒装使热阻降低约 40%；示例 80 发射器六边形阵列匹配定制光纤束 [p6, p7, p8（OCR）]
  - S21（8 mA，OA≈5 μm）：25°C 总带宽 33.8 GHz，光带宽 36.2 GHz，RIN -151 dB/Hz；85°C 总带宽 25.3 GHz，光带宽 28.6 GHz，RIN -147 dB/Hz [p9]
  - NRZ：50 Gb/s NRZ，1 m OM5 ER 4.2 dB/eye margin 18.8%；50 m/100 m/150 m 1060nm 光纤 ER 分别 4.0/3.8/3.6 dB，margin 18.6/19.6/12.7%；32 Gb/s NRZ，105°C，50 m OM5，硅子基板，ER 4.0 dB，margin 12.10% [p10]
  - 低偏置：标准 1060nm VCSEL 低偏置电流 2.5–4.0 mA、25/85°C、1 m/30 m OM2，32 Gb/s 与 25 Gb/s 眼图表（具体数值看不清）[p11, 仅OCR]
  - 链路演示：OFC 26 演示为底发射 1060nm VCSEL 阵列+驱动，32 Gb/s，fan-out 封装+光纤连接器，设计可支持 1.5 Tb/s/mm shoreline 密度；ECOC 26 演示为直驱 chiplet 集成，Lumentum VCSEL+PD，与 Corning 及 Qualcomm Dragonfly 合作 [p12]
  - 磨损可靠性：1060nm ~5 μm 孔径，8 mA，115°C 烘箱→Tj 181°C，86 个单元，5000 小时无失效、漂移极小（scale-up 机架最高工作 Tj~130°C）；对比 850nm 22 个单元在类似加速应力下 >600 h 出现功率/Ith 变化、>1600 h 灾难性失效（幻灯片注：该晶圆在 8 mA 85°C 下满足 100G 20 年要求）[p13]
  - 早期失效（顶发射 1060nm 阵列）：72K 发射器（900 器件、5 片晶圆），9.0 mA/e CW 80°C 应力，T=0 h 1 个失效（14 DPPM，装配损伤），24 h 与 96 h 累计 2 个失效（28 DPPM，其中 1 个为 epi 缺陷）[p14]
  - 早期失效（底发射 1060nm 阵列）：8.6K 发射器（1 片晶圆，108 器件，8640 发射器），8.0 mA/e CW 80°C；T=0/8/24 h 1 个失效（116 DPPM），T=100 h 2 个（231 DPPM），均为装配损伤；倒装工艺仍在开发，年底前有更多晶圆数据；目标 <50 dppm（含早期、随机、磨损、环境与机械全部失效模式）[p15]
  - 制造：6 英寸 GaAs（规避 InP 供应问题），外延基于 940nm 3DS 调整到 1060nm；晶圆测试复用 3DS 方法，晶圆探针抽样测 S21 与 RIN；综合外延/探针/目检判定，无需 burn-in [p16, p17]
- 提到的公司/客户/产品/标准：Corning、Qualcomm Dragonfly（ECOC 26 演示合作）；DARPA MTO ERI Summit 2019（引用图）；OM2/OM5 光纤；对比 InP、TFLN、SiPh [p4, p5, p12]
- 与业界对比或记录声明（SOTA/首次/record）：无"record"；指标对比为 850nm 磨损寿命明显更差、1060nm 5000 h 无失效 [p13]
- 推荐配图页：p13（1060 vs 850 nm 磨损对比曲线）；p15（底发射阵列早期失效表+<50 dppm 目标）

### We5-I 东工大.pdf（第1–17页）
- 讲者/机构：Hameeda R. Ibrahim, Ahmed Hassan, Xiaodong Gu, Fumio Koyama / Institute of Science Tokyo（原东京工业大学），NICT，Al-Azhar 大学，Ambition Photonics | 题目：62-GHz Bandwidth 1060-nm Metal-Aperture VCSELs Enabling 256-Gbps PAM4 and Modal-Dispersion-Free SMF/MMF Links（We5-I.2，讲稿页写为 We5-12） | 类型：学术论文
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器/电芯片；次 4 Scale-up/in CPO/NPO
- 核心主张：
  1. 耦合腔（氧化孔径主腔+金属孔径二次腔）1060 nm VCSEL 在 6 mA 下 -3 dBo 光带宽 >62 GHz，可作为 AI 数据中心 scale-up 与 scale-out 的候选 [p10, p17]
  2. 同一 1060 nm 平台可同时用于 SMF 1 km 与 MMF 500 m 链路（200 Gb/s PAM4）[p6, p13, p15]
  3. VCSEL 芯片直流功耗 <50 fJ/bit（200 Gbps）；下一步：400G/lane、带宽 >70 GHz、并行 8/16/32 通道、>500 m、CMOS EIC <1 pJ/bit [p12, p16]
- 关键数据：
  - 动机：GPU/CPU 峰值算力 20 年 60000x（3.0x/2年），DRAM 带宽 100x（1.6x/2年），互连带宽 30x（1.4x/2年）（引 Gholami, IEEE Micro 2024）；全球数据中心用电 2025 年约 485 TWh，2030 年约 950 TWh（IEA）[p4]
  - 1060 nm 优势：光纤损耗 <1 dB/km（较850nm更长链路）；小氧化孔径下可靠性更好（引 Photonics West 2026）；底发射可倒装用于 NPO/CPO（引 ECOC 2024/2025）[p5]
  - NPO/CPO 光引擎 100 Gbps/lane 能耗：VCSEL 0.90 pJ/bit（Mondal, IEEE ISSCC 2026）；SiPh-MRM 3.0–4.5 pJ/bit（de Valicourt, Opt. Express 2025）；SiPh-MZM 6.25 pJ/bit（Li, OFC 2022）[p7]
  - 器件：In0.4Ga0.6As/GaAsP 10 QW，氧化孔径 4.2 μm，上镜 98%；-3 dBo 带宽 62 GHz（6 mA），-3 dBe 带宽 >52 GHz；另一器件孔径 4 μm，Ib=6.2 mA，chirp 参数 1.5；经 SMF(G652) 500 m/1 km 有效带宽增大，2 km 曲线亦给出 [p9（OCR）, p10]
  - 测量：Keysight M8199B AWG（256 GSa/s，80 GHz）+66 GHz 放大器+Bias Tee（6.5 mA）+65 GHz RF 探针；接收为 Keysight N1092A-60A DCA（>60 GHz）；均衡：200G 用 TX 5-tap/RX 5-tap，256G 用 TX 12-tap/RX 22-tap（幻灯片上下颠倒）[p11]
  - BTB 眼图：孔径 4 μm、Ib=6.4 mA：150 Gbps NRZ ER 1.8 dB；256 Gbps PAM4 TDECQ 4.97 dB，ER 2.2 dB；孔径 <3.5 μm、Ib=3.5 mA：150 Gbps NRZ ER 1.8 dB；200 Gbps PAM4 TDECQ 4.3 dB，ER 2.4 dB；"最高速率 256 Gbps"；200 Gbps 下芯片直流功耗 <50 fJ/bit [p12]
  - 1 km SMF(G652)：100 Gbps ER=2 dB（另一 NRZ 眼图速率标注被标题遮挡，看不清）；200 Gbps PAM4 TDECQ 5.9 dB（Ib=4.1 mA）与 3.4 dB（Ib=6.4 mA）；讲者称"比传统 850 nm MMF 链路长 10 倍以上" [p13]
  - 500 m OM4 MMF：用约 1 m SMF 模式滤波器（MFD 约 8 μm）做限模注入抑制模式色散；3 dB 横向对准容差 ±4 μm；100 Gbps NRZ ER 2.2 dB；200 Gbps PAM4 外 ER 2.3 dB，TDECQ 5.9 dB（孔径 4.0 μm，Ib=6.2 mA）；无滤波器的 500 m MMF 响应明显塌陷 [p14（OCR）, p15]
  - 路线图：单通道 25–400 Gbps，总容量 100GbE→12.8TbE；目标 400G/lane、带宽 >70 GHz、8/16/32 通道、>500 m、EIC <1 pJ/bit [p16]
- 提到的公司/客户/产品/标准：Ambition Photonics（合作者单位）；Keysight M8199B/N1092A；G652 SMF、OM4；NICT 资助；引用 Mondal（ISSCC 2026）、IEA、Gholami [p1, p4, p7, p11]
- 与业界对比或记录声明（SOTA/首次/record）：256 Gbps 为"获得的最高速率"，未明说 record；1 km SMF 较 850 nm MMF 链路"长 10 倍以上"[p12, p13]
- 推荐配图页：p10（62 GHz S21 曲线与 SMF 后响应）；p12（256G/200G PAM4 眼图与 <50 fJ/bit）；p7（三种 CPO 引擎能耗对比条形图）

### We5-I 博升.pdf（第1–20页）
- 讲者/机构：Huawen Hu, Yipeng Ji, Binbin Zhao, Sui Zhang, Shasha Li, Jianqiang Chen, Zhenglai Zhang, Jiaxing Wang, ChihChiang Shen, Connie J. Chang-Hasnain / Berxel（博升光电） | 题目：1060 nm Back-Emitting VCSEL Modulated at 106 Gbps PAM4 Transmission over 100 m OM3 MMF for NPO Applications | 类型：学术论文
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 3 Scale-out 224G/448G/光源
- 核心主张：
  1. AI 工厂新需求（带宽密度、功耗、成本、可靠性）：scale-out 用 NPO、scale-up 用 CPO，VCSEL 阵列是"快且宽"的选择 [p4, p8]
  2. 背发射 VCSEL 集成 HCG 超透镜，光纤耦合容差极大，简化封装对准 [p10, p12, p19]
  3. 940 nm 与 1060 nm 背发射阵列均可用于 SDM/WDM/BiDi；1060 nm >44 GHz、RIN <-150 dB/Hz，212 Gbps PAM4 可传 30 m OM2 / 50 m OM5 [p19]
- 关键数据：
  - VCSEL NPO/CPO 优势表：能量约 1 pJ/bit（备注：VCSEL 本身仅 50–100 fJ/bit）；带宽密度数十 Tbps/mm；单 VCSEL <0.03 FIT（Berxel 累计交付 250 亿器件小时无失效）；阵列 <0.1 FIT（备份可大幅降低 FIT）；光纤 OM2–OM5、SMF；距离 50–100 m（SMF 可达 2000 m）[p9]
  - 顶发射 vs 背发射：光束发散 vs 准直；高速可寻址 ~10 vs 100–1000；大阵列节距 >150 μm vs 30–50 μm；背发射热路径短，结温低 40°C [p10]
  - 940 nm 背发射倒装+16 个集成 HCG 超透镜 [p11, 仅OCR]；耦合：3 dB 径向容差 ±22 μm、纵向容差 400 μm（as-cleaved MMF）；+18 μm 偏移处 TDECQ 3.3 dB，+250 μm 处 TDECQ 4.1 dB [p12]
  - 高温倒装 VCSEL：25 Gbps NRZ，5 mA，140°C，经 30 m OM2 与 100 m OM3 MMF 无误码，OMA 低于 IEEE 802.3bm 阈值；106 Gbps PAM4，110°C，30 m OM2 与 50 m OM4 MMF 眼图张开（图示 100°C/110°C）[p13]
  - 1.6 Tbps 共封装 TX：16 通道，每通道 106 Gbps PAM4 眼图均张开 [p14]
  - 1060 nm 背发射：20log S21 3 dB 带宽 >44 GHz（7.0 mA；受仪器与多模 PD 限制）；RIN 平均：3 mA -142.4、5 mA -147.3、7 mA -149.6、9 mA -150.3 dB/Hz [p15]
  - 212 Gbps PAM4：偏置 8.5 mA，ER 1.48 dB；30 m OM2 TDECQ 3.22 dB，50 m OM5 TDECQ 4.47 dB [p16]
  - 超低偏置 50G NRZ @4 mA：ER 2.5 dB；BTB TDEC 2.33 dB，30 m OM2 2.80 dB，100 m OM5+ 2.68 dB，用于 slow-and-wide [p17]
  - 可靠性：140°C、9 mA 强应力下无失效；折合 8 mA 70°C >7M 等效小时；1060 nm VCSEL 为顶发射结构器件；加速因子 Ea=1.3 eV，n=3；Wafer 1/2 功率与电压曲线在 ±20%/±10% 红线内（约 6000 k 小时等效）[p18]
  - 带宽密度路径图：SiPh/EML 8 通道 212–424 Gbps/lane；VCSEL 8 通道 212 Gbps/lane；micro-LED 304 通道 3.3 Gbps/ch（"slow and wide"）（图内数字有 OCR 残缺，读数粗略）[p5–p8]
- 提到的公司/客户/产品/标准：Berxel；IEEE 802.3bm；OM2/OM3/OM4/OM5；对比 EML、SiPh、micro-LED [p9, p13]
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；强调"250 亿器件小时无失效"与 <0.03 FIT [p9]
- 推荐配图页：p12（背发射+超透镜耦合容差曲线，±22 μm/400 μm）；p14（1.6 Tbps 16 通道 106G PAM4 眼图墙+样机照）；p13（140°C/110°C 高温结果）

### We5-I 坦佩雷ORC 低温VCSEL.pdf（第1–19页）
- 讲者/机构：Behzad Namvar；Patrik Rajala, Teemu Hakkarainen, Mircea Guina, Jukka Viheriälä / Optoelectronics Research Center (ORC), Tampere University, Finland（PREIN） | 题目：Low-Threshold Single-Frequency Intra-Cavity VCSELs for Scalable Cryogenic Computing | 类型：学术论文
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS（量子计算低温互连）；次 3 Scale-out 224G/448G/光源
- 核心主张：
  1. 数千量子比特的扩展瓶颈是金属同轴线（被动导热、空间拥挤、热负载 vs 制冷功率），光纤链路可降低导热并借 WDM 在单光纤承载数十–数百路控制/读出 [p4, p5]
  2. 低温 VCSEL（4 K 直驱，阈值 <150 μA，能耗至 fJ/bit）是有希望的候选 [p5, p18]
  3. 设计上须处理腔模与增益峰的温度失配（室温失谐设计），双腔内接触（double intra-cavity contact）VCSEL 减小自由载流子吸收与电阻热 [p8, p10, p18]
- 关键数据：
  - 架构：室温（RT）主机/多波长发射源与接收 → MUX/DEMUX → 4 K：Cryo-PD 阵列、Cryo-VCSEL 阵列、Cryo-CMOS 驱动与串并转换 → mK：SFQ 逻辑与脉冲发生器、QPU；光纤降低导热"数量级"（幻灯片标 2.3 dB/km 衰减）[p5]
  - 背景结果：<2 μm 氧化孔径 1/2-λ 腔低温 VCSEL 在 4 K 高速，引 Z. Liu 等，APL 128, 193302 (2026)：136 Gbps 下 28 fJ/bit；80 K 质子注入高效 VCSEL（Bo Lu, PTL 1995）[p7]
  - 温度特性：F-P 谐振红移速率从 200 K 约 -0.08 nm/K 降至 10 K 约 0.007 nm/K；增益峰红移速率从 200 K 约 -0.26 nm/K 降至 10 K 约 -0.05 nm/K [p10（OCR）]
  - 初始设计：厚腔在阻带内可支持多个谐振，170 K 附近增益峰与谐振对齐；极低温下 EL 蓝侧出现肩峰（顶DBR 830 nm）[p11, p12（OCR）]
  - 设计变体：870 nm @4 K（Al0.9Ga As 接触、DBR）与 910 nm @4 K（GaAs 接触、GaAs/Al0.5GaAs），注："GaAs absorbs 850 nm wavelength at 4K"；CW @8 K，I=2 mA 时 SMSR 约 45 dB（870 nm）与 40.4 dB（910 nm）（OCR，读数待核）[p14]
  - 器件性能：3 μm 孔径 Ith=120 μA，输出至约 2.5 mW（5 K，电流约 8 mA）；4.5 μm 孔径 Ith=150 μA，输出功率轴单位标为 μW（似为标注错误，输出图上量级约 5，看不清）；斜率效率最高 0.6 W/A [p15]
  - 3 μm 孔径：6 K 与 295 K 电压-电流及微分电阻曲线（6 K 下 2 mA 处电压约 4.7 V，295 K 约 3.6 V）；RIN（dBc/Hz）在 I=1/3/6 mA，0–15 GHz 范围，约 -110 至 -160 [p16]
  - 未完成：速度测量、传输测量、噪声测量、降低寄生、进一步降低阈值 [p18]
- 提到的公司/客户/产品/标准：IQM 量子路线图（引 meetiqm.com）；Arm/imec 77 K cryo-CMOS 文献；Cryo-CMOS、SFQ [p4, p6]
- 与业界对比或记录声明（SOTA/首次/record）：无自己的 record；引用他人 136 Gbps/28 fJ/bit 结果作对比；本工作尚无速度/传输数据 [p7, p18]
- 推荐配图页：p5（RT–4 K–mK 光互连架构图）；p15（3 μm/4.5 μm 孔径低温 L-I 与斜率效率）

## 本批小结
1. 1060 nm VCSEL 阵列成为 scale-up/NPO/CPO 光源的主线：Coherent、Lumentum、博升、东工大四篇均围绕 1060 nm 背发射（BSE）阵列，共同论点是：GaAs 衬底对 1060 nm 透明，可背发射+衬底透镜+倒装，热阻下降（Lumentum 约 40%，博升称结温低约 40°C）。
2. 速率仍集中在 32–106/128 Gbit/s/发射器，NRZ 与 PAM4 并存：Lumentum 预期首个实现用 NRZ（50G NRZ 50–150 m），Coherent 32/64/106/128G（16 通道阵列，含 125°C 下 32G），博升 106G×16=1.6 Tbps 共封装 TX 与单管 212G PAM4（30 m OM2/50 m OM5）；东工大耦合腔器件把单管推到 256G PAM4（BTB）并配 62 GHz 带宽，但需要 12/22 tap 均衡（Coherent、Lumentum、博升、东工大）。
3. 高温与可靠性成为竞争焦点：Lumentum 5000 h 无失效（Tj 181°C，86 单元）并对比 850 nm >1600 h 灾难失效，底发射阵列 8.6K 发射器 231 DPPM 仍在开发（目标 <50 dppm）；博升 <0.03 FIT、>7M 等效小时；博升 140°C 25G NRZ、Coherent 125°C 32G、Lumentum 105°C 32G（Lumentum、博升、Coherent）。
4. 能效与密度对比论述：东工大给出 VCSEL 0.90 pJ/bit 对 SiPh-MRM 3.0–4.5、MZM 6.25 pJ/bit；博升称 VCSEL 本体 50–100 fJ/bit，东工大芯片 <50 fJ/bit；Lumentum 首代 2.5 pJ/bit、设计 1.5 Tb/s/mm；Coherent 论述 9 Tbit/s/mm²（展望）。注意各家口径（芯片/含驱动/含RX）不同，不能直接横比（东工大、博升、Lumentum、Coherent）。
5. 生态落地信号：Lumentum 的 ECOC 26 直驱 chiplet 演示与 Corning、Qualcomm Dragonfly 合作；博升给出 1.6 Tbps 16 通道共封装 TX 样机；Coherent 现场有 full link 演示。光纤侧提出 1060 nm 优化光纤（Lumentum 150 m 50G NRZ）与 SMF 模式滤波限模注入（东工大 500 m OM4）两条路线。
6. VCSEL 也向低温量子互连延伸：Tampere 4 K 单模 VCSEL（Ith 120/150 μA，斜率效率最高 0.6 W/A），但尚无速度/传输数据；引用的 136 Gbps/28 fJ/bit（Liu, APL 2026）是他人结果（Tampere）。
