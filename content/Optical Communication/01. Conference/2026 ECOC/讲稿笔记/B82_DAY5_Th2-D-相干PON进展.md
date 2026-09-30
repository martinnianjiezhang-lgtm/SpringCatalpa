---
title: "B82 · DAY5 · Th2-D-相干PON进展"
tags:
  - ECOC2026
  - DAY5
---

### 0924-Th2-D1-NokiaBellLabs-单载波超速率混合相干上行突发模式PON实现960至120Gbps.pdf
- 讲者/机构：Kovendhan Vijayan / Nokia Bell Labs | 题目：960/480/240/120 Gbit/s Single-Carrier Super-Rated Hybrid Coherent Upstream Burst-Mode PON | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（相干PON上行突发）；次 1 相干/高波特率器件
- 核心主张：
  1. OLT 侧用一台通用的全相干接收机（现成 120 GBd 级，无纳秒级 TIA 增益控制）即可同时接收简化相干与全相干 ONU 上行；120–480 Gbit/s 异构 ONU 可共存于同一 PON，覆盖家宽到 AI 传输 [p17]
  2. 每个 ONU 的发射端加一个 SOA，同时承担三个角色：功率增强（Booster，达成光功率预算）、高消光比门控（抑制 when-not-enabled 发射）、功率预均衡（Power leveler，使接收端不需快速 TIA）[p8, p17]
  3. 首次报告 480 Gbit/s 上行突发模式下 >40 dB 光功率预算；首次报告 960 Gbit/s 上行 PON 且预算 >26 dB [p17]
- 关键数据：
  - ONU 分四类：Type I 单偏振 MZM（120G BPSK/240G ASK4）；Type II 双偏振 MZM（240G BPSK/480G ASK4）；Type III 单偏振 IQM（240G QAM4/480G QAM16）；Type IV 双偏振 IQM（480G QAM4/960G QAM16）[p7, p8]
  - 实验速率/格式/类型：120G SP-BPSK（I）、240G SP-QAM4（III）、480G DP-QAM4（IV）、480G SP-QAM16（III）、960G DP-QAM16（IV）[p9]
  - 发射：InP 130 GBd 相干驱动调制器（CDM，共封装差分线性驱动），120 GBd、0.05 滚降 RRC，DAC 128 GSa/s（带宽 >50 GHz）；信号/LO 均为 μITLA 1550.1 nm，线宽 <100 kHz，输出功率 13 dBm / 15.5 dBm；SOA 噪声系数 7.8 dB；20 km SSMF；接收 130 GBd OIF Class 80 μICR，ADC 256 GSa/s，模拟带宽约 63 GHz [p9]
  - 120G SP-BPSK：OPB 44.5 dB @ BER 2×10^-2，20 km；SOA 电流 75–425 mA 扫描；未观察到 SOA 非线性代价，光纤传输代价可忽略；偏振为手动对准 [p12]
  - 480G DP-QAM4：OPB 41.1 dB @ BER 2×10^-2；480G SP-QAM16：OPB 28 dB @ BER 2×10^-2 [p14]
  - 960G DP-QAM16：OPB 26.4 dB @ BER 2×10^-2；QAM16 比 QAM4 更易受 SOA 非线性影响（星座图在 425 mA 下畸变）[p15]
  - SOA 电流调节可使不同 ONU 之间的预均衡覆盖 ≈20 dB 接收动态范围；SOA 作门控时 ONU 发射谱 >60 dB 信号抑制（SOA ON 无数据 vs SOA OFF 噪声底）[p16]
  - 120–480 Gbit/s 在最大 SOA 驱动下 OPB 均 >40 dB（图中 960G 曲线约 26 dB 量级）[p16]
- 提到的公司/客户/产品/标准：ITU-T G.Suppl.88（VHSP：IM/DD 2×100G、混合、相干三条路线）；G.9804.3（同 Huawei 讲稿）；100ZR 相干可插拔（成本相对 50G ONU 高）；文献对比含 OFC/ECOC 2024–2025 多篇（Vijayan、Borkowski、Rosato、Kovacs、Hossain Adib 等）；PON 类别 class N1 / C+ / D 标于对比图 [p3, p4, p17]
- 与业界对比或记录声明（SOTA/首次/record）：首次 480G 上行突发 >40 dB OPB；首次 960G 上行 PON >26 dB OPB；对比图为"每波长容量 vs OPB"，本工作两点（DP-16QAM 约 960G/26.4 dB；DP-QAM4 约 480G/41 dB）位于图的左上与右侧 [p17]
- 推荐配图页：p8（异构 ONU 四类 + SOA 三重角色 + 单一相干 OLT 架构图）；p16（OPB vs SOA 电流与 >60 dB 门控抑制谱）；p17（结论与容量-OPB 对比图）

### 0924-Th2-D2-华为-LDPC前向纠错的256Gbps相干PON突发模式接收实验.pdf
- 讲者/机构：华为（Huawei，讲者姓名与完整题目页未拍到） | 题目：（无标题页；依文件名与内容）Soft-LDPC FEC 下 256 Gbps 相干 PON 突发模式接收实验——post-FEC BER 估计方法与动态范围 | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（相干PON）；次 1 oDSP
- 核心主张：
  1. 提出两种从离线 DSP 数据估计 post-FEC BER 的方法（码字预FEC错误数直方图；码字平均信息密度直方图），二者互相一致且与直接测量的 post-FEC BER 吻合 [p15]
  2. Soft-LDPC 使 post-FEC 无错动态范围达 24 dB，满足 ITU-T 标准要求（20 dB）；配静态增益 TIA 的相干接收机借助削波（clipping）区间与 DP-QPSK 即可满足 200G PON 动态范围 [p13, p15]
  3. 高、低接收功率区的净编码增益损失（NCGR）相近（1.7 dB、1.8 dB），削波非线性对 Soft-LDPC 影响小；可不使用功率均衡硬件，降低下一代相干 PON 的硬件与系统复杂度 [p14, p15]
- 关键数据：
  - 标准要求：ITU-T G.9804.3 要求上行动态范围 20 dB [p3]
  - 256 Gbps DP-QPSK，SD-LDPC (17280, 14592)；pre-FEC BER 阈值 2.45×10^-2；pre-FEC 动态范围 DR = 29 dB（图中另标 DRI = 28 dB）；PON 中 post-FEC BER <10^-12 视为无错；突发长度约 10^5 比特；每个 ROP 点约 1000 个突发；直接测量 post-FEC BER 仅统计有效至约 10^-6 [p4]
  - 图中无错区间：ROP 约 -32 至 -3 dBm 附近有 "zero post-FEC errors" 标注（从曲线读出，非文字给出）[p4]
  - post-FEC 估计结果：24 dB 动态范围（ROP 轴约 -30 至 -6 dBm，BER 降至 10^-12）[p13]
  - 方法 I：每码字 n=17280 比特；方法 II：信息密度 i(x,y)=1−log2(1+e^(−x·LLR(y)))，outage 判据 平均信息密度 < 有效码率 R_eff（图上标 0.883）则码字失败；实验信道非 AWGN，Gumbel 分布拟合较好 [p5, p7–p10 OCR，p8 OCR 数值 R_eff=0.883，图未复核]
  - NCGR：灵敏度端 1.7 dB、过载端 1.8 dB（相对 AWGN 信道曲线，pre-FEC 阈值 2.45×10^-2）[p14]
- 提到的公司/客户/产品/标准：ITU-T G.9804.3；引用 Koma（JLT 2022，Rx SOA 功率均衡）、Vijayan（OFC 2025 M2I.2，Tx SOA 预均衡）、Sarkis（OFC 2026 W4F.1，标准商用 ICR、静态增益 TIA、无功率均衡，29 dB 动态范围）[p3]
- 与业界对比或记录声明（SOTA/首次/record）：未声明"首次/record"；主张相对 Rx-SOA / Tx-SOA / 突发 TIA 三种方案（"增加硬件和系统复杂度"）的简化替代 [p3]
- 推荐配图页：p3（突发模式动态范围问题与三种方案 vs 静态增益 ICR 的 29 dB 动态范围曲线）；p13（post-FEC BER 估计与测量对照，24 dB 动态范围）；p14（NCGR 与 SNR 曲线）

### 0924-Th2-D3-复旦大学-100G实时上行突发模式相干PON的低复杂度FPGA信道估计与均衡.pdf
- 讲者/机构：Renle Zheng, An Yan, Penghao Luo, Shuhong He, Xuyu Deng, Junhao Zhao, Yongzhu Hu, Nan Chi, Junwen Zhang / 复旦大学 | 题目：Low-Complexity FPGA Implementation of Channel Estimation and Equalization for 100G Real-Time Upstream Burst-Mode Detection in Coherent PON | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（相干PON）；次 1 oDSP
- 核心主张：
  1. 提出降并行度的单抽头 SOP（偏振态）辅助 MMSE 信道估计与均衡，在 FPGA 上实时实现 100G 突发模式相干 PON [p8, p17]
  2. 43 并行相对 128 并行仅 0.6 dB 灵敏度劣化和 1 dB 动态范围代价，资源大幅下降 [p14, p17]
  3. 硬件高效的突发模式相干 DSP 使实用化实时相干 PON 成为可能 [p17]
- 关键数据：
  - 装置：25.06752 GBaud DP-QPSK，100 Gbps；4 通道 ADC 28.20096 GSa/s、8 bit；FPGA Xilinx XCVU13P；DSP 时钟 261.12 MHz；DSP 并行度 128（基准）；传输 20 km；波长 1552.5 nm；ONU 端 SOA [p13]
  - 帧结构：TS-A（768）、TS-B（1536）、导频符号、载荷；用于帧检测、采样相位偏移估计、频偏估计、帧同步、信道估计 [p10，数字来自 OCR，未复核]
  - MMSE 系数估计并行度 128 → 64/43/32/16，再插值平滑至 128 并行系数用于实时均衡 [p11]
  - 并行度 128/64/43/32/16 对应动态范围 22/21/21/18/17 dB（BER 门限 2E-2）；43 并行较 128 并行灵敏度劣化 0.6 dB，动态范围 22→21 dB [p14]
  - FPGA 资源（43 并行 vs 128 并行）：LUT −49.60%、FF −58.44%、DSP −35.83%、BRAM −64.91% [p15]
  - 功率预算：采用 43 并行，SOA 功率 10 dBm 时最大功率预算 45.7 dB；灵敏度约 -35.7 dBm（10 dBm SOA）至 -37.0 dBm（0–4 dBm SOA）（从曲线读出）[p16]
- 提到的公司/客户/产品/标准：Xilinx XCVU13P；前序工作：OFC 2026 PDP 200G TFDM-CPON 现场试验（复旦校园）、ECOC 2025 / OFC 2025 / OFC 2024 的 Nokia、Adtran、CableLabs、McGill 等相干 PON 工作（仅列文献）[p5, p7]
- 与业界对比或记录声明（SOTA/首次/record）：标题主张"45.7-dB power budget"的 100G 实时突发相干 PON [p8, p16]；无明确"first"字样
- 推荐配图页：p13（实验装置与 Tx/Rx DSP 流程及 FPGA 板）；p14（并行度 vs 灵敏度/动态范围）；p15（FPGA 资源对比柱状图）

### 0924-Th2-D4-上海交大与中国电信-相干TDM-PON首次现场试验速率达300Gbps.pdf
- 讲者/机构：Yixiao Zhu（上海交通大学）, Luyao Huang, Yimin Hu, Ziheng Zhang, Chaofeng Ge, Dezhi Zhang, Ming Jiang（中国电信研究院）, Weisheng Hu / 上海交大 + 中国电信研究院 | 题目：First Field Trial of Coherent TDM-PON Up to 300 Gb/s | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（相干PON现场试验）；次 1 相干
- 核心主张：
  1. 首次在部署的城域光纤（57 km 往返，约 34 dB 损耗）上做相干 TDM-PON 现场试验，速率 120–300 Gb/s 灵活可调 [p20]
  2. 功率预算：200 Gb/s 可达 42 dB，300 Gb/s 为 39 dB；低阶调制格式噪声容限更好、预算更高，带宽允许时提高波特率有益 [p16, p17, p20]
  3. 前导长度可优化到 30 ns，DSP 快速收敛且稳定；验证下一代更高速率、更长距离相干 PON 的可行性 [p20]
- 关键数据：
  - 链路：上海现场光纤，Site A/B（Park B23/B12）—Site C（南浦东路 1835 号）往返光纤长度 57 km（ODN 57 = 28.5×2 km），OTDR 总损耗约 34 dB（含光纤、连接器、熔接点损耗，主要来自熔接）[p8, p10]
  - 发射：ECL 1550 nm、线宽 100 kHz；IQ 调制器 40 GHz 带宽；AWG Keysight M8195A 64 GSa/s，3 dB 模拟带宽 25 GHz；PDM 仿真；EDFA 发射功率 10 dBm；接收 RTO 100 GSa/s；信号 50/60 GBd PS-16-QAM（p9 文字；实验亦含 30 GBd）[p9, p10]
  - 30 GBd、15% SD-FEC 门限（10 dBm 发射）：240 Gb/s DP 16-QAM 灵敏度 -28 dBm、预算 38 dB；180 Gb/s PS-16-QAM -33 dBm、预算 43 dB；120 Gb/s QPSK -35 dBm、预算 45 dB [p15]
  - 50 GBd、57 km：200 Gb/s QPSK（熵 2 bit/符号）-32 dBm、预算 42 dB；240 Gb/s PS-16-QAM（熵 2.4）-31 dBm、预算 41 dB；300 Gb/s（页面标注"16-QAM，熵 3 bit/符号"，图例同页写 PS-16-QAM，两处表述不一致，原样记录）-29 dBm、预算 39 dB [p16]
  - 速率 vs 光路损耗：30 GBd 曲线 240G（至约 38 dB）、180G（39–43 dB）、120G（44–45 dB）；50 GBd 曲线 300G（至 39 dB）、240G（40–41 dB）、200G（42 dB）[p17]
  - 帧时长：30 GBd 为 1.5 μs，50 GBd 为 0.9 μs；FOE 3000 符号足以可靠识别导频音；LPF 带宽最优 30 MHz；600 符号实现初始收敛、1500 符号使 BER 低于 15% SD-FEC 阈值；FFE 抽头 <20 不足、>80 引入噪声累积，取最优 41 抽头 [p12–p14；p14 的 15% SD-FEC 门限 OCR 记为 2×10^-2，图未逐点核对]
  - 稳定性：240 Gb/s（30 GBd DP 16-QAM）和 300 Gb/s（50 GBd DP PS-16-QAM）在 57 km 上 20 分钟 BER 远低于 15% SD-FEC 门限（约 1×10^-3 与约 5×10^-3 量级，读图）[p18]
  - 对比表（现场试验相干 PON）：[1] 30 km / 200.5 Gb/s / 33 dB / 实时（复旦 OFC 2026 PDP Th4C.4）；[2] 19 km / 200 Gb/s / 30.1 dB / 离线（Kovacs，PTL 2025）；[3] 40 km / 10 Gb/s / 29 dB / 实时（Luo，JOCN 2019）；本工作 57 km / 300 Gb/s / 39 dB / 离线 [p19]
- 提到的公司/客户/产品/标准：中国电信研究院光纤光缆制造技术全国重点实验室；Keysight M8195A；ITU-T G.9804 系列/G.989 等标准演进图（引用 J. S. Wey 教程）；前序现场试验引用 [p2, p5, p6, p19]
- 与业界对比或记录声明（SOTA/首次/record）：标题与结论页称"首次"相干 TDM-PON 现场试验，57 km、最高 300 Gb/s；对比表中在距离与速率上高于前作，但 DSP 为离线（前作 [1] 为实时）[p19, p20]
- 推荐配图页：p8（现场部署光纤地图与 OTDR 曲线，约 34 dB）；p17（数据速率 vs 光路损耗）；p19（现场试验对比表）

### 0924-Th2-D5-FraunhoferHHI-瑞利背向散射对下一代双向200GbpsFDMA相干PON的影响.pdf
- 讲者/机构：Juan L. Moreno Morrone, Laurenz Ebner, Abdelrahmane Moawad, Johannes K. Fischer, Ronald Freund / Fraunhofer HHI 与 TU Berlin（PONGO 项目，德国联邦研究、技术与航天部资助） | 题目：Impact of Rayleigh backscattering on next-generation bidirectional 200 Gb/s FDMA coherent PON（标题页左侧被裁切，据可见部分还原） | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（相干PON）；次 1 相干
- 核心主张：
  1. 实验表征了下行信号的瑞利背向散射对两 ONU 上行传输的影响；仿真评估了上下行共用同一频带的双向 FDMA PON 中瑞利背向散射的影响 [p17]
  2. 合理选择 OLT 与 ONU 的发射功率，可在 23 dB 分光损耗（Nu=128）、最大光路损耗 35 dB 的 ODN 上实现单频带双向传输，图中可划出"可运行区域" [p16, p17]
  3. 后续工作：扩展至考虑突发接收的 TFDMA [p17]
- 关键数据：
  - 背景：ITU-T SG15 Q2 正在讨论 200 Gb/s VHSP（G.sup88 已发布）；双向 PON 中上行接收受 OLT 下行反射的瑞利背向散射干扰；现有解法（上下行频谱分离需双倍带宽；不同波长需重新设计收发器）均增加复杂度 [p2–p4]
  - 实验：ONU1 30 GBd DP-QPSK 35 GHz，ONU2 30 GBd DP-QPSK 25 GHz，EDFA 后各 4.5 dBm；支路 11.4 km / 8.4 km SSMF，2:2 耦合后 20 dB 衰减（Nu=128 模拟），25 km SSMF；下行以带 60 GHz 增益轮廓的 ASE（WSS 整形）模拟；OLT Rx 带宽 73 GHz [p9, p10]
  - [A] 无下行功率时 SD-FEC（2e-2）满足所需 ROP：ONU1 > -33.25 dBm，ONU2 > -34.65 dBm；[B] 下行发射功率最大容限：ONU1 -4.9 dBm，ONU2 -2.65 dBm [p9, p10]
  - 仿真：VPIphotonics Design Suite 11.6 + Toolkit DSP Library 5.5；OLT 发射 2×30 GBd DSCM、guard 2 GHz，DAC 120 GSa/s 8 bit；OLT 接收 CoRx+TIA，ADC 240 GSa/s 8 bit；激光器 OLT 16 dBm / ONU 14.5 dBm，线宽 100 kHz、频偏 1 GHz；SSMF 0.195 dB/km，D=16.73 ps/(nm·km)；瑞利背向散射系数 -80 dB（1 ns 脉宽）；分光损耗 23 dB（128 用户）；馈线光纤 25 km；ONU 子带 193.084 / 193.116 THz [p12–p14 OCR，数值未逐项图上复核]
  - 仿真与实验在仅上行（无下行）时 BER vs ROP 吻合，SD-FEC 2e-2 [p15]
  - Q² 因子随上行/下行子带发射功率扫描（-3 至 12 dBm）：OLT Rx（US）与 ONU Rx（DS）各有等值线，交叠得到"operational region"（US 发射功率约 ≥2–3 dBm 且相对 DS 功率满足一定比例的区域，从图读出）[p16]
- 提到的公司/客户/产品/标准：ITU-T SG15 Q2、G.sup88（VHSP）；VPIphotonics；可复用的可插拔形态 QSFP28、QSFP-DD、CFP2（相干 PON 潜在复用）；35 dB 最大 OPL 引用 [1]（具体标准未看清）[p2, p17]
- 与业界对比或记录声明（SOTA/首次/record）：无 SOTA/record 声明
- 推荐配图页：p10（实验装置、频谱与 BER 曲线 [A][B]）；p16（Q² 因子随上下行发射功率的三联图与可运行区域）

## 本批小结
- 五讲同属 Th2-D 相干 PON 场次，核心矛盾一致：上行突发模式下如何在不使用昂贵突发 TIA 的前提下覆盖 ≥20 dB 动态范围。三条路线并存：ONU 端 Tx-SOA 预均衡+门控（Nokia D1）、OLT 端静态增益 TIA 加削波区与 Soft-LDPC（Huawei D2，24 dB post-FEC 动态范围）、以及低复杂度实时 DSP（Fudan D3，动态范围 21–22 dB）。
- 速率-预算折中已被量化：Nokia 上行 480G 达 >40 dB（DP-QAM4，41.1 dB）而 960G DP-QAM16 仅 26.4 dB；SJTU/中国电信 300G 为 39 dB、200G 为 42 dB、120G 为 45 dB（30 GBd QPSK）。均显示高阶调制在 SOA 非线性和灵敏度上的代价。来自 D1、D4。
- 相干 PON 正从实验室走向现场：SJTU/中国电信 57 km、约 34 dB 损耗的城域现场试验（300G，离线 DSP）；复旦 D3 引用 OFC 2026 PDP 的 200G 实时 FPGA 现场试验（30 km、200.5G、33 dB）。实时 vs 离线 DSP 是对比表中的关键区分（D3、D4）。
- 复杂度与成本被反复强调为落地关键：Nokia 指出 100ZR 级相干可插拔仍相对 50G ONU 有成本溢价，ONU 成本占主导；Fudan 用 43 并行使 LUT/FF/DSP/BRAM 降 35.83%–64.91%；Huawei 主张去掉功率均衡硬件（D1、D2、D3）。
- 双向传输的物理限制也被单独研究：Fraunhofer HHI 显示上下行共带 FDMA 时瑞利背向散射可通过选择 OLT/ONU 发射功率界定可运行区域（23 dB 分光、35 dB OPL 下可行），下一步扩展到含突发的 TFDMA（D5，与 D3/D4 的 TFDM 现场试验方向呼应）。
- 标准背景：多讲引用 ITU-T G.Suppl.88 / G.sup88（VHSP，200G 讨论中）与 G.9804.3 的 20 dB 上行动态范围要求，作为设计目标（D1、D2、D5）。
