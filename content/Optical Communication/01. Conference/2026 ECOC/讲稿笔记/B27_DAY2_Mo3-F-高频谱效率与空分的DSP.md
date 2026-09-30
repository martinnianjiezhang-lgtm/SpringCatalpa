---
title: "B27 · DAY2 · Mo3-F-高频谱效率与空分的DSP"
tags:
  - ECOC2026
  - DAY2
---

# B27 讲稿笔记（ECOC 2026，Mo3-F 高频谱效率与空分的DSP）

### 0921-Mo3-F1-华为-带双二进制预编码的Turbo均衡.pdf
- 讲者/机构：Tianyuan Kong 等（Huawei Technologies Duesseldorf 慕尼黑研究中心 / Kiel Univ.） | 题目：Turbo Equalization with Duobinary Precoding for High-Speed Bandwidth-limited IM/DD Transmission Systems | 类型：学术论文
- 方向归属（主/次）：主 3 Scale-out（224G IM/DD PAM4 电芯片/DSP）；次 1 oDSP
- 核心主张：
  1. 发端双二进制（DB）预编码有意引入受控ISI，收端Turbo均衡（MAP检测器与FEC译码器迭代交换软信息）可利用该结构化ISI。
  2. 在带宽受限IM/DD PAM4且内码为弱软判决码时，TE+DB预编码增益显著。
  3. 仿真与实验均表明TE+DB预编码可消除非预编码系统的误码平层。
- 关键数据：
  - 仿真：PAM4，ISI系数 α=0.8，弱Hamming码，TE增益最高1.7 dB（对KP4 pre-FEC门限，迭代1到10次）；DB预编码消除error floor并使所需SNR再降0.2 dB [p6]
  - 仿真AIR：目标码率0.9375，DB预编码在 α≥0.7 时优于无预编码；α=0.8时图中SNR范围12.5–16 dB [p7]
  - 实验：224 Gbps 带宽受限IM/DD PAM4（112 GBd），DAC 112 GS/s（BW 45 GHz）、EA（BW 70 GHz）、EML 1310 nm（BW 50 GHz，Pout=3 dBm）、500 m SSMF、PDFA后7 dBm、PD BW 70 GHz、DSO 256 GS/s [p8]
  - 实验结果：α=0.6，TE增益1.5 dB（Hamming码，有无预编码均如此），DB预编码消除error floor；ROP轴范围约-9.5至-8 dBm [p9]
- 提到的公司/客户/产品/标准：KP4 FEC（pre-FEC门限）、Hamming码、BCJR/MAP、400G/800G/1.6T DCI [p3]
- 与业界对比或记录声明（SOTA/首次/record）：未声称record；与传统FFE、MAP/MLSE均衡对比，称传统均衡在严重ISI下失效 [p3]
- 推荐配图页：p6（有/无DB预编码的BER vs SNR，含1.7 dB增益与error floor圈注）；p9（实验BER vs ROP对比）

### 0921-Mo3-F3-FraunhoferHHI-随机耦合多芯纤的无数据辅助SDM-MIMO均衡.pdf
- 讲者/机构：Pamir Oezsuna, Aymeric Arnould, Ronald Freund, Georg Rademacher（Fraunhofer HHI / Univ. Stuttgart / TU Berlin） | 题目：Non-Data-Aided SDM MIMO Equalization for Randomly-Coupled Multi-Core Fibers with a Tap-Correlation Avoidance CMA | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途（SDM、oDSP）；次 无
- 核心主张：
  1. 提出TCA-CMA：在CMA代价函数上加抽头相关惩罚项（Jtca-cma = Jcma + α·Jtca），避免多路输出收敛到同一信号的奇异解，实现无奇异、降复杂度的耦合SDM MIMO均衡。
  2. 仿真验证多种芯数与传输距离下均可无奇异收敛。
  3. 后续需做详细参数研究、实验验证和实时实现（仅仿真）。
- 关键数据：
  - 仿真条件：32 GBd DP-16QAM，多段模型（每km一段），每组50次实现，39抽头均衡器（585 ps，2 sps）[p13]
  - 奇异规避统计（50次中收敛成功次数）：100 km与225 km下3/4/7芯、σ=3/4/5 ps/√km 全部50/50；400 km时7芯在σ=4约33次、σ=5约7次（读图估计）；900 km时7芯在σ=3约19次，σ=4、5基本为0，3芯和4芯仍为50/50 [p13]
  - 群时延扩展近似 ±2σ√S（S为段数）[p11]
  - 4芯MCF，100 km，SMD=5 ps/√km：TCA-CMA(39抽头)预收敛后切换到101抽头MMA；不同信道SNR下均衡后SNR：信道SNR=10 dB时3C约9.4 dB、4C约9.2 dB、7C约8.7 dB；15 dB时约14.5/14.4/14.0 dB；20 dB时约19.1/19.1/18.8 dB；25 dB时约23.2/23.1/23.0 dB（读图估计）[p17]
- 提到的公司/客户/产品/标准：无（引用Ho & Kahn多段模型、Puttnam、Luis OFC2025 Pbit/s级SDM传输）[p2, p10]
- 与业界对比或记录声明（SOTA/首次/record）：无record声明；对比常规CMA(α=0)存在奇异（同一输出复制）[p8–p9]
- 推荐配图页：p13（不同距离/芯数/σ下TCA-CMA无奇异成功率柱图）；p17（4芯100 km星座与SNR箱线图）

### 0921-Mo3-F4-NTT-超宽带耦合芯传输中链路SMD与MDL的直接估计.pdf
- 讲者/机构：Akira Kawai, Kohki Shibahara 等（NTT Network Innovation Labs / Access Network Service Systems Labs） | 题目：Simple Direct Estimation of Link SMD and MDL for MIMO-DSP Design in Ultra-Wideband Coupled-Core Fiber Transmission | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途（SDM耦合芯光纤）；次 无
- 核心主张：
  1. 提出无需MIMO的简单方法，用同一套光路（机械扰偏器+光束遮挡器+波长扫描激光器+单芯注入）同时估计链路SMD与MDL。
  2. 在实验室与现场4芯/12芯CCF上得到超宽带（1490–1640 nm，150 nm，S到U波段）测量，与MIMO-DSP估计比对。
  3. 该方法可隔离光纤本身MDL，为MIMO-DSP设计提供实用链路表征。
- 关键数据：
  - 测试对象：约50 km级4芯（53 km lab）和12芯（51 km lab）卷装CCF，以及现场68 km 12芯CCF链路（4.86 km×14段）；1490–1640 nm；扫描速度20 nm/s [p11]
  - SMD：CSMD=1.645（90%能量宽度）；SMD估计bin 3 nm，每bin约600k采样点；现场12芯CCF与MIMO-DSP（C+L波段传输）平均差11 ps；68 km现场12CCF的SMD约120 ps（1490 nm）升至约165 ps（1640 nm）（读图）；51 km lab 12CCF约250 ps降至约220 ps（读图）[p12, p15]
  - MDL仿真器验证：两种MDL仿真（FIFO通道相关损耗；L波段WSS对一路加0.5/1 dB波长选择性损耗），实测与参考值误差<0.1 dB；bin 0.15 nm，每bin 4000采样点 [p13]
  - 光纤MDL：MIMO-DSP估计比本方法高约1 dB（含Tx/Rx子系统、WDM滤波等）；现场68 km 12CCF平均MDL 0.31 dB；1550 nm下MDL随距离累积（约0.15 dB至0.31 dB，0到约60 km，读图），推测由连接器与熔接引入 [p14]
- 提到的公司/客户/产品/标准：NICT ModeReach项目（JPJO12368C01001）；现场CCF链路（引用Mori、Imada等）[p15]
- 与业界对比或记录声明（SOTA/首次/record）：称此前无方法可用同一光路对SMD与MDL做简单、可扩展、超宽带测量；同页提到Shibahara ECOC2026 We5-H1现场Pbit/s传输 [p2, p5]
- 推荐配图页：p14（光纤MDL vs 波长与距离，CCF与CCF+TRx对比）；p12（150 nm SMD测量与MIMO对比）

### 0921-Mo3-F5-NokiaBellLabs-高频谱效率格式的进展-调制与编码.pdf（第1–22页，重复页p3、p7、p10、p17、p21已跳过）
- 讲者/机构：Hussam G. Batshon, Gregory Raybon, Di Che, Xi Chen（Nokia Bell Labs） | 题目：Advances in High-Spectral-Efficiency Formats: Modulation and Coding | 类型：邀请报告
- 方向归属（主/次）：主 1 相干/海缆/长途/oDSP（概率整形与编码调制）；次 无
- 核心主张：
  1. 高频谱效率的进展来自调制与编码的接口；PAS进入产品是因为复用二进制FEC与现有DSP，而非星座阶数本身。
  2. 整形之后仍存在比特度量译码（BMD）惩罚，且随SE增大而增大、基本与符号率无关。
  3. 在PAS符号位上加短SPC（3,4）码并配SPC感知的迭代MAP解映射器，可回收最多0.9 dB，DM、映射器、LDPC均不变；下一个问题是解映射器成本（本工作未量化）。
- 关键数据：
  - 历史：4096-QAM跨509 km、16384-QAM跨25 km（Chen 2019）；2048-QAM几何整形跨100 km（Wakayama 2021）；符号率从100 GBd（Schuh 2017）到440 GBd单载波（Che 2026）[p2]
  - 可回收BMD损耗（PS-256QAM，匹配净SE、调制阶数、FEC）：7 b/s/Hz 0.4 dB，7.5 为0.6 dB，8 为0.7 dB，8.5 为0.85 dB，9 为0.9 dB；7到9 b/s/Hz增加一倍以上 [p6]
  - 系统模型：PS-256QAM，LDPC 20%开销，净SE 7–10 b/s/Hz，实验符号率116 GBd，SPC(3,4)，基线40次LDPC迭代 vs SPC方案4外×10内迭代 [p13]
  - 仿真（OFC 2025 Tu2F.4已发表）：所需SNR降低在各SE点均为正，最大0.9 dB @9 b/s/Hz；约1 dB对应0.5 b/s/Hz，故约等于0.45 b/s/Hz的SE [p15]
  - 阈值：约每0.5 b/s/Hz上移1 dB（文字）；实测阈值与仿真吻合在0.10–0.15 dB内（噪声加载测量，非长途链路），SE 4/8/9/10 b/s/Hz四点，第2次外迭代获得大部分增益，第4次收敛 [p14, p16]
  - 实验验证：3.68 THz C波段，31信道，118.75 GHz间隔，116 GBd PS-256QAM，30个ECL，环路6×62 km（372 km/环），总发射功率19 dBm，接收256 GSa/s实时示波器113 GHz带宽；结论页：7.5 b/s/Hz下1860 km、总速率超过26 Tb/s [p18, p22]
- 提到的公司/客户/产品/标准：Nokia Bell Labs；EX3000光纤（图中标注）；LDPC、DM（Maxwell-Boltzmann）、PAS（Boecherer 2015）[p2, p18]
- 与业界对比或记录声明（SOTA/首次/record）：综述历史记录（440 GBd单载波，Che 2026）；本工作称较常规PAS最多回收0.9 dB，无其他record声明 [p2, p22]
- 推荐配图页：p15（所需SNR vs SE，PS与SPC-PS及ΔSNR）；p6（BMD可回收损耗随SE柱图）；p18（3.68 THz环路实验装置）

### 0921-Mo3-待定-AstonUniversity-用KAN网络做低复杂度数字预失真.pdf
- 讲者/机构：Bilal Khalid, Fabio Cavaliere, Luca Giorgi, Pedro Freire, Sergei K. Turitsyn, Jaroslaw E. Prilepsky（Aston University；Ericsson，EU MSCA NESTOR） | 题目：DPD-KAN: Kolmogorov-Arnold Networks for Low-Complexity Digital Predistortion in 5G Analog Radio-over-Fiber Systems | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（A-RoF/RoF）；次 1 oDSP（神经网络DPD）
- 核心主张：
  1. 用KAN（边上可学习激活函数）做A-RoF的DPD，可在低复杂度下线性化链路。
  2. 与MLP和Volterra类广义记忆多项式（GMP）比较，低复杂度预算下KAN更优。
  3. 高复杂度预算下KAN与MLP性能相近。
- 关键数据：
  - 链路：5G NR Test Model 3.1，100 MHz，64QAM；AWG、驱动放大器、VCSEL/DML、1 km SSMF、PD、实时示波器；MOPA称超过97%的前传RoF链路小于1 km，应用场景为大型室内 [p6]
  - 结构：双路残差学习（线性路径为恒等跳连），B样条基函数（2阶和3阶）[p7]
  - EVM vs RF输入功率：无DPD在约5 dBm输入时约7.5%；KAN[BOP≈10^5]在5 dBm约2.3%；GMP[BOP≈10^5]约4.1%；MLP[BOP≈10^4]约3.9%；KAN[BOP≈10^4]约2.9%（读图）[p9]
  - 结论页：BOP≈10^4时EVM较MLP低约24%、较GMP低约30%；达到平均EVM<2%所需BOP较MLP少约52%（高驱动区2–5 dBm平均）[p11]
  - EVM≤2%平均BOP：KAN约1.32×10^4，MLP约2.75×10^4（OCR值，与52%基本吻合，未图片核对） [p10]
- 提到的公司/客户/产品/标准：Ericsson、MOPA（Mobile Optical Pluggables Alliance）、5G NR TM3.1、GMP [p6]
- 与业界对比或记录声明（SOTA/首次/record）：无record声明；对比MLP与GMP [p11]
- 推荐配图页：p9（EVM vs 输入功率与PSD对比，含KAN/MLP/GMP不同BOP）

### 0921-Mo3-待定-NokiaBellLabs-实时GPU十模传输的降复杂度部分MIMO均衡.pdf
- 讲者/机构：Ruby S. B. Ospina, David Winter, Roland Ryf 等（Nokia Bell Labs；KIT；Prysmian） | 题目：Reduced-Complexity Partial MIMO Equalization for Real-Time GPU-based 10-Mode Transmission over 26 km GI-FMF（Mo3-F2） | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途（SDM、oDSP）；次 无
- 核心主张：
  1. 高模式数SDM的MIMO均衡即使短距、低时延扩展也很复杂；部分自适应均衡（按模式组MG选用）可降复杂度。
  2. 以往部分MIMO均衡仅用示波器离线数据（数微秒），无法反映信道动态；本工作在26 km渐变折射率少模光纤（GI-FMF）上做实时GPU处理，跨120秒（受风扇、机架振动、人员走动扰动）评估。
  3. （本讲无结论页，以上据摘要与结果页）
- 关键数据：
  - 实验平台：4块Xilinx RFSoC FPGA板（Tx 2块、Rx 2块）；Rx DSP服务器为2颗AMD EPYC 7313 16核处理器加4块NVIDIA A100 80 GB GPU；实时、分块、数据辅助LMS复数部分MIMO均衡，10个T/2间隔抽头，带集成相位恢复（32符号一块）[p14]
  - 0.002 ms数据迹：全20×20 MIMO（双偏振10模）恢复MG1约18 dB，MG4约17 dB（读图）；使用的MG数从1增至4时，活动FIR滤波器数：MG4从约65增至160，MG1从约5增至40（读图）；全MIMO下各MG滤波器数40/80/120/160 [p16]
  - 120秒实时迹：恢复MG1时，使用MG1–4全部的SNR约17.9 dB，MG1–3约15.3 dB，MG1–2约12.8 dB，仅MG1约8.2 dB（相差9.7 dB）；恢复MG4时，全部约16.8 dB，MG2–4约14.8 dB，MG3–4约11.1 dB，仅MG4约5.6 dB（相差11.2 dB）；SNR在120 s内稳定（部分标注读图较模糊，数值取近似） [p20]
- 提到的公司/客户/产品/标准：Xilinx RFSoC、AMD EPYC 7313、NVIDIA A100；引用Winter, Ryf 等ECOC 2025“Real-time GPU-based 48-km 10-mode transmission” [p14]
- 与业界对比或记录声明（SOTA/首次/record）：称此前部分MIMO工作仅为离线数据；本工作为实时GPU 10模26 km部分均衡，未使用“首次”一词 [p11–p13]
- 推荐配图页：p16（活动FIR滤波器数与SNR随所用模式组数）；p20（120秒SNR稳定性，MG1与MG4）

### 0921-Mo3-待定-UBC与NokiaBellLabs-序列化神经概率幅度整形.pdf
- 讲者/机构：Mohammad Taha Askari, Lutz Lampe (UBC), Amirhossein Ghazisaeidi (Nokia Bell Labs) | 题目：Sequential Neural Probabilistic Amplitude Shaping: Learning the Channel's Language | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途（概率整形、oDSP）；次 无
- 核心主张：
  1. 提出Seq-NPAS：逐符号自回归、固定长度的联合分布学习，条件于已生成序列，以适应光纤非线性。
  2. 速率损失必须显式优化，而非事后测量。
  3. 性能优于序列选择，且复杂度更低。
- 关键数据：
  - 原理：PAS线性信道最多1.53 dB整形增益；序列选择（rejection sampling）无最优性保证、复杂度高、有块间效应与旁信息速率损失；NPS用Gumbel-softmax、失配高斯解映射器、BCE损失训练 [p2–p7]
  - 速率损失vs块长（n为比特数，L为符号数）：n=16bit/L≈5.2符号时，NPAS约1.25、NPAS++与Seq-NPAS++约0.55–0.6 bit/QAM符号；n=2048bit/L≈570符号时NPAS约0.89，NPAS++约0.02–0.03、Seq-NPAS++约0.05–0.06 bit/QAM符号（读图，含插图）[p10]
  - 仿真条件：64QAM双偏振，50 GBd，5个WDM信道55 GHz间隔，RRC滚降0.1，单跨205 km，光纤损耗0.2 dB/km，色散17 ps/nm/km，γ=1.30 /W/km，EDFA NF 5 dB [p11]
  - 数值结果：AIR峰值在约7 dBm/信道/偏振；Seq-NPAS++峰值约4.47，较ESS+序列选择（约4.43）高约0.05 bit/QAM符号，较均匀分布（约4.27）高约0.2 bit/QAM符号（图中标注0.05与0.2）；ESS约4.42 [p12]
- 提到的公司/客户/产品/标准：ESS（枚举球面整形）、Boecherer PAS、Civelli序列选择（OFC 2023）、Askari NPS（ECOC 2025）[p2–p3, p6]
- 与业界对比或记录声明（SOTA/首次/record）：相对ESS+序列选择提升约0.05 bit/QAM符号，相对均匀提升约0.2 bit/QAM符号（仿真）[p12]
- 推荐配图页：p12（AIR vs 发射功率，ESS/序列选择/NPAS++/Seq-NPAS++）；p10（速率损失vs块长）

### 0921-Mo3-待定-UCL-相干数据中心链路的快速收敛超网络DSP.pdf
- 讲者/机构：Samuel Lennard, Fabio A. Barbosa, Filipe M. Ferreira（UCL Optical Networks Group） | 题目：A Realistic Implementation of Fast Convergence Hypernetwork-based DSP for Coherent Data Centre Links（页脚标注 Mo5-F2） | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI/oDSP；次 2 Scale-across（ZR类相干数据中心链路）
- 核心主张：
  1. DSP重捕获延迟是新型相干传输方式（灵活组网）的重要设计考量；传统LMS/RLS迭代收敛慢，前馈方法复杂。
  2. 用超网络（hypernetwork）由任务上下文直接生成自适应滤波器权重，实现廉价、确定性的前馈滤波器获取，无需迭代、无需CD补偿、无需预自适应载波频偏补偿，也无需信道先验信息。
  3. 仍有进一步降复杂度空间。
- 关键数据：
  - 传统算法对残余CD很敏感：LMS尤其差，RLS与LS较稳健但硬件难实现（精度限制）（CD范围0–1200 ps/nm，50 km SSMF标注）[p6]
  - 实验：单跨SSMF，C波段填满发射端，接收端噪声加载，16QAM DP，110 GHz带宽（图中标注），RLS与全数据辅助载波频偏补偿基于64符号导频序列 [p11, p12]
  - 波长泛化：扫C波段1540–1565 nm，6 km与25 km下，HN DSP的SNR约20–22 dB，与传统数据辅助DSP接近（有个别点略低） [p13]
  - 复杂度：超网络4M实数乘法，经剪枝与聚类降至300k（与RLS相当）；进一步剪枝与结构简化（不在本文范围）可到25k（与LMS相当但收敛时间固定）；FPGA实现收敛75 ns [p15]
  - 发射功率泛化：线性区内与传统性能匹配（图轴约-10到20 dBm）[p14]
- 提到的公司/客户/产品/标准：UKRI、TRANSNET（EP/R035342/1）、Beyond Exabit Optical Communications项目 [p1]
- 与业界对比或记录声明（SOTA/首次/record）：无record声明；与LMS/RLS/传统数据辅助DSP对比 [p13, p15]
- 推荐配图页：p15（超网络复杂度路线与FPGA 75 ns收敛）；p13（波长泛化SNR对比）

## 本批小结
1. AI/神经网络成为DSP新主线，但都强调“低复杂度”：Aston的KAN DPD（达EVM<2%所需BOP较MLP少约52%）、UCL的超网络DSP（4M降到300k实数乘法，FPGA 75 ns收敛）、UBC/Nokia的Seq-NPAS（复杂度低于序列选择）——来自Aston、UCL、UBC三篇。
2. 编码与调制的联合设计是提升单波长频谱效率的现实路径：Nokia F5用符号位SPC+迭代解映射回收最多0.9 dB（约0.45 b/s/Hz），Huawei用DB预编码+Turbo均衡消除IM/DD PAM4误码平层（增益1.5–1.7 dB）；两者共同点是复用现有FEC/DSP架构、只在“调制-编码接口”做改动——来自Nokia F5、Huawei F1，UBC PAS论文亦属同一思路。
3. SDM/MIMO的重点转向降低均衡复杂度与真实链路表征：HHI的TCA-CMA解决盲均衡奇异，Nokia GPU实时部分MIMO（10模，26 km，120 s）用较少模式组换低复杂度但SNR下降显著（如MG1从17.9降至8.2 dB仅用自身），NTT给出现场68 km 12芯CCF的SMD（约120–165 ps）与平均MDL 0.31 dB——来自HHI、Nokia GPU、NTT。
4. 现场与实时验证在增加，但仍多为单点：NTT测现场12芯CCF，Nokia GPU用4块A100实时处理；HHI仍仅为仿真，7芯在400/900 km下奇异规避成功率下降——来自HHI、NTT、Nokia GPU。
5. 数据中心/短距场景下DSP向“带宽受限+弱FEC”倾斜：Huawei在224G IM/DD（112 GBd PAM4，EML BW 50 GHz）上以弱Hamming内码配Turbo均衡，UCL瞄准相干数据中心链路的快速重捕获——来自Huawei、UCL。
6. 注意：UCL讲稿页脚为Mo5-F2，Nokia GPU页脚为Mo3-F2，与目录“Mo3-待定”不一致，归档场次需以官方日程核对。
