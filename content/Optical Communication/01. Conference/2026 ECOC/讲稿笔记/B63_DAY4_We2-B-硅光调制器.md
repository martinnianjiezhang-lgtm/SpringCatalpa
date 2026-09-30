---
title: "B63 · DAY4 · We2-B-硅光调制器"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We2-B1-Lumentum-800G与1.6T硅光发射机量产.pdf
- 讲者/机构：讲者姓名未见（题目页看不清），Lumentum | 题目：800G and 1.6T Silicon Photonics Transmitters in Volume Production（题目页OCR乱码，英文原题据文件名与内容推断，非逐字）| 类型：邀请报告（Workshop/专题场 We2-B，产业侧）
- 方向归属（主/次）：主 3（Scale-out 224G/光源/调制器）；次 4（CPO/NPO/XPO 下一代）
- 核心主张：
  1. AI 使数据中心网络以约每3.4个月翻倍的速度增长，要求算力与光模块同步；模块量产爬坡时间缩短，性能与质量要求上升。
  2. 采用 InP 激光器的硅光（SiPho）1.6T 模块可满足需求：集成器件可高产量重复制造，并复用电子封装。
  3. 下一代 XPO/NPO/CPO 需要更高集成度与信号完整性；能耗目标为传统方案的 <50%；需提升可靠性（MTBF）以保证网络可用度。
- 关键数据：
  - LLM 算力需求每3.4个月翻倍；LLM 能力密度每3.5个月翻倍；GPU 算力每6个月翻倍（引自 OpenAI/Nature MI/NVIDIA 图）[p3][p4]
  - 面向 GPU 集群 scale-out 的可插拔光模块速率约每4.5年翻倍；达到1000万只/年所需年数：10G 15年、100G 10年、400G 8年、800G 5年、1.6T 4年（LightCounting, OFC 2026）[p6]
  - 可插拔模块功耗构成：DSP 49%、光学+电子 27%、激光器 12%、电源开销 12%；DSP 内部：SerDes（host侧）40%、ADC/DAC（line侧）36%、DSP 核 24% [p8]
  - 800G-1.6T DR8 硅光发射机 PIC：马赫-曾德尔调制器（边缘耦合器+3dB分束+加热器+RF相移器）；EO S21 图显示 100G/lane 与 200G/lane 两条响应，x轴至67 GHz，具体-3 dB带宽看不清；倒装焊装配，眼图标注 112 GBd [p11]
  - 光纤到硅光耦合损耗：SSC->带双透镜激光器 <0.8 dB；Gen1 SSC->光纤阵列单元 <1.8 dB；Gen2 SSC->光纤阵列单元 <0.9 dB（1260–1360 nm，单位 dB/facet）[p12]
  - 片上监测PD读数随 InP 激光功率（0–约220 mW）线性，讲者称高输入光功率下线性，对减少激光器数量重要 [p12]
  - 1.6T DR8 八通道 BER 曲线：接收光功率约 -6 至 +2 dBm，BER 底约 1e-12 量级，讲者称200G PAM4下"close to error free (1e-12)" [p13]
  - 2xDR4 晶圆投片量爬坡 2024–2025（归一化，纵轴到1.0）；典型1.6T DR8 晶圆级测试损耗变化 <0.5 dB（色标 ±0.25） [p14]
  - 晶圆级测试：垂直耦合器只能测单偏振单通带，难测相干或CWDM PIC；新方法用硅光切割沟槽+标准FAU做边缘耦合晶圆测试，FWHM >6 um；可在O波段双偏振下扣除边缘耦合器损耗测 MZM 插损与消光比，重复性高（MZM IL 箱线图约 2.2–2.9 dB，中位约 2.4 dB；ER 约 22–26.5 dB，中位约 24.8 dB） [p15][p16][p17]
  - 能效路线：LPO、XPO、NPO 目标 <10 pJ/bit，交换机 radix 在200G/lane下由512增至1024；CPO 目标 <5 pJ/bit，采用慢而宽（50G/lane）方式，潜在 radix 4096；图中收发器功耗曲线由2016年约38降至2025年约17 pJ/bit [p19]
- 提到的公司/客户/产品/标准：LightCounting、OpenAI、NVIDIA、Arista（引用）、XPOMSA、Samtec CPX/CPC（引用 OCP 2025）、MPI（晶圆测试）；DR8、DR4、LPO、XPO、NPO、CPO、InP 激光器、SiPho
- 与业界对比或记录声明（SOTA/首次/record）：未见 record/首次声明；为产业量产进展汇报 [p14]
- 推荐配图页：p19（收发器功耗与交换容量演进+传统/NPO·CPO/LPO 封装对比）；p6（速率与放量年数）；p13（1.6T DR8 八通道BER与眼图）

### 0923-We2-B2-80-硅微环调制器5.2THz FSR与69GHz带宽.pdf
- 讲者/机构：Yeyu Tong 等（Kaihang Lu, Yuxiang Yin, Wu Zhou, Hao Chen, Baohua Wen, Chi-Hang Chan），香港科技大学（广州）HKUST(GZ) | 题目：69 GHz EO Bandwidth for 3.2-Tbps DWDM Integrated Photonic Transmitters | 类型：学术论文（We2-B，编号80）
- 方向归属（主/次）：主 3（调制器/Scale-out）；次 4（CPO/多波长光引擎）
- 核心主张：
  1. 提出耳语回廊模式（WGM）增强的硅微环调制器：小半径下低弯曲辐射损耗、低寄生RC，同时获得大FSR与高带宽。
  2. O波段 Si MRM 半径 2.5 um，FSR 5.2 THz（30.0 nm），EO带宽 ≥69 GHz，FSR×EO带宽积 358 THz×GHz。
  3. 为 16×224 Gbps DWDM 硅微环光引擎提供新思路。
- 关键数据：
  - 半径 2.5 um；Q=2057；FSR 30.0 nm（5.2 THz，约1296–1326 nm）；加热器效率 0.4 nm/mW（70 GHz/mW）；调制效率 25 pm/V（4.4 GHz/V） [p11]
  - EO带宽 ≥69 GHz @ -3 V 偏压，失谐 0.2 nm；等效电路：Cp 9.9 fF，Rsi 620 ohm，Cox 81 fF，Rj 546 ohm，Cj 2.7 fF [p12]
  - 16 通道 DWDM，每通道 224 Gbit/s PAM-4（SD-FEC 门限，2e-2 量级）；设备限制（128 GSa/s AWG）；9-tap FFE + 9-tap DFE；通道 1296.1 nm 至 1323.1 nm，间隔 >1.8 nm（300 GHz）；单个MRM 依次测试 [p13]
  - 对比表（O波段Si MRM）：imec ECOC 2025 圆盘 R=2.1 um，FSR 6.47 THz，BW 31.6 GHz，积 204；Intel OFC 2022 环 4 um，2.9 THz，54 GHz，157；FDU OFC 2025 5 um，2.3 THz，51 GHz，117；AMD OFC 2024 3.8 um，3.2 THz，41 GHz，131；SJTU OFC 2026 Euler 3.6 um，3 THz，67 GHz，201；GF OFC 2026 7.5 um，1.6 THz，67 GHz，107；CAS OFC 2026 [25] 6 um，2 THz，45 GHz，90；CAS OFC 2026 [26] 圆盘 4.1 um，3.5 THz，65 GHz，228；本工作 2.5 um，Q 2057，5.2 THz，69 GHz，358 [p14]
- 提到的公司/客户/产品/标准：对比对象 imec、Intel、FDU、AMD、SJTU、GF（GlobalFoundries）、CAS；SD-FEC
- 与业界对比或记录声明（SOTA/首次/record）：表中 FSR-BW 积 358 THz·GHz 为所列工作最高（次高为 CAS 228），未用"record"字样 [p14][p15]
- 推荐配图页：p14（O波段Si MRM 对比表及 FSR-BW 散点图）；p13（16通道光谱与眼图、DSP 流程）

### 0923-We2-B3-1289-硅有机混合调制器超110GHz.pdf
- 讲者/机构：Conglin Sun 等（含 Christian Haffner, Joris Van Campenhout, Peter Ossieur 等），imec（与 KU Leuven、Politecnico di Torino、Ghent Univ.） | 题目：Beyond 110 GHz Silicon Organic Hybrid (SOH) Modulators | 类型：学术论文（We2-B，编号1289）
- 方向归属（主/次）：主 3（调制器/224G-448G）；次 1（高波特率器件）
- 核心主张：
  1. 垂直（vertical）SOH 调制器，TM 模限制于狭缝，VπL 约为水平 SOH 的一半（页面标"2x improved VπL"，由p4得），并在 50 um 器件上实现超 110 GHz 带宽。
  2. 短器件（<200 um）不再受与50 ohm射频源阻抗失配限制，RF 损耗与速度失配可忽略。
  3. O波段交联材料+几何优化有望 VπL <100 V·um，插入损耗可优化至 <1 dB。
- 关键数据：
  - 背景对比：等离子体（POH）VπL ~80 V·um，f3dB ~1000 GHz，损耗高 0.5 dB/um；水平 SOH VπL ~320 V·um，f3dB ~80 GHz，损耗 0.004 dB/um [p2]
  - 垂直 SOH：VπL <150 V·um，r_eff ≈ 300 pm/V；实测 Vπ ≈ 2.9 V；50 um 器件（1520–1560 nm 传输谱） [p5]
  - 带宽：S21 测至 110 GHz，仍在 -3 dB 线之上；提取 R 约 45 ohm、C 约 11 fF，集总元件 3 dB 带宽约 150 GHz（50 um 器件） [p7]
  - 数据实验：C波段 TLS，256 GSa/s AWG，1 Vpp 驱动，100 GHz PD，示波器；100–200 GBd PAM4，BER 在 180 GBd 约 3e-3（低于 7% HD-FEC 线附近），200 GBd 约 3e-2 但低于 20% SD-FEC；展示 100 GBd 与 180 GBd 眼图；光损耗 0.075 dB/um，主要来自掺杂多晶硅 [p8]
  - 结论页展示 360 Gbps 数据率眼图（对应 180 GBd PAM4）[p10]
  - 优化：器件长度 10–200 um 扫描，传播损耗 <0.005 dB/um（p9 标注，具体条件看不清） [p9]
- 提到的公司/客户/产品/标准：NLM Photonics（极化方法讨论）、UGent IDLab（数据实验）；资助：ERC QAMP、HORIZON-JU-Chips STARLight、Branco Weiss Fellowship；20% SD-FEC、7% HD-FEC
- 与业界对比或记录声明（SOTA/首次/record）：雷达图对比 plasmonic/h-SOH/v-SOH 的 VπL-损耗-带宽折中；未见明确 record 用语 [p10]
- 推荐配图页：p10（结论页：VπL/损耗/带宽三角雷达对比，50 um 器件至110 GHz S21 及 360 Gbps 眼图）；p8（BER 对符号率与眼图）

### 0923-We2-B4-163-激光修整微环调制器超100GBaud.pdf
- 讲者/机构：Erwan Weckenmann 等（含 Wei Shi, Louis-Rafaël Robichaud），Université Laval COPL、Femtum、INRS-EMT（加拿大魁北克） | 题目：Post-Fabrication Laser-Trimmed Microring Modulator Operating Beyond 100 Gbaud | 类型：学术论文（We2-B4，编号163）
- 方向归属（主/次）：主 3（调制器）；次 4（CPO/DWDM 微环光引擎）
- 核心主张：
  1. 制后飞秒（超短脉冲）激光修整可永久调谐微环谐振波长，此前仅在无源器件上演示。
  2. 修整后调制效率、EO带宽和传输性能均无退化，适合在 DWDM 栅格上免加热器工作。
  3. 制后激光修整是微环调制器谐振对准的可行且可扩展方法。
- 关键数据：
  - 动机：晶圆内制造波动；DWDM 栅格对准；免除加热偏置（消耗数十 mW） [p3]
  - 设计：全通过耦合（强过耦合）微环，腔内载流子耗尽相位调制器；修整后变为欠耦合，增加往返损耗 0.4 dB 时谐振深度相近（约 15–16 dB） [p6]
  - 静态：按约 1 nm 步进修整，总谐振偏移 3.1 nm（376 GHz），Δneff ≈ 7.7×10^-3，Δφ ≈ 0.6π；谐振深度 参考 15.4 dB / 修整后 16.2 dB；Q 参考 ~2800 / 修整后 ~2000；调制效率均 22 pm/V [p7]
  - EO 响应：最优 IL 工作点 3 dB 带宽约 52 GHz（参考 IL=4 dB，修整 IL=3 dB），无带宽退化 [p8]
  - 传输：PRBS-25、实时采集、离线 19-tap FFE，AWG 传输，110 GHz 示波器；BER 低于 20% SD-FEC：参考 MRM 至 100 Gbaud，修整后 MRM 至 110 Gbaud（图示；调制格式页面未明确，p9 提及 NRZ）；改进耦合 IL 后 PAM4 100 Gbaud，净 166.6 Gbps [p9][p10]
- 提到的公司/客户/产品/标准：Femtum、EXFO、CMC Microsystems（流片）、NSERC；NVIDIA Spectrum-X/Quantum-X、ISSCC 2026（背景引用）；20% SD-FEC、7% HD-FEC
- 与业界对比或记录声明（SOTA/首次/record）：讲者称此前激光修整仅在无源器件上演示（隐含首次用于有源调制器，原话未写"first"）[p3]
- 推荐配图页：p10（不同IL工作点BER对比与眼图，含110 Gbaud及净166.6 Gbps）；p7（静态谐振偏移3.1 nm 各步曲线）

## 本批小结
- 硅光调制器带宽已跨过100 GHz门槛，但路线分化：微环（HKUST(GZ) 69 GHz/FSR 5.2 THz、Laval 制后修整 52 GHz/110 Gbaud）、有机混合 SOH（imec 50 um 器件平坦至110 GHz，180 GBd PAM4 达 360 Gbps）、行波MZM（Lumentum 200G/lane 量产）。（B2、B3、B4、B1）
- 微环调制器的工程焦点从"带宽"转向"波长对准与可制造性"：HKUST 以 FSR-BW 积（358 THz·GHz）衡量并展示16×224G DWDM；Laval/Femtum 用激光修整移动谐振 376 GHz 以免除数十 mW 加热器。（B2、B4）
- SOH 用极短器件（<200 um）规避阻抗失配和速度失配，代价是光损耗较高（0.075 dB/um，主要来自掺杂多晶硅），插损需优化至 <1 dB 才具实用性；VπL 约 150 V·um，目标 <100 V·um。（B3）
- Lumentum 指出量产硅光的关键在可预测的界面与晶圆级测试：耦合损耗 Gen2 <0.9 dB，晶圆内损耗变化 <0.5 dB，边缘耦合晶圆测试可用于O波段双偏振。（B1）
- 能效路径：可插拔中 DSP 占功耗 49%（其中 SerDes 40%），因此 LPO/XPO/NPO 目标 <10 pJ/bit，CPO <5 pJ/bit，与微环 DWDM 引擎（B2/B4）的"慢而宽"取向一致。（B1、B2、B4）
- 注：本批 B5（IMEC 200GBaud PAM4 硅光MZM）按指示跳过。
