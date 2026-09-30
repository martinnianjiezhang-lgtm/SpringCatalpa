---
title: "B66 · DAY4 · We2-I-实时信号处理与实现"
tags:
  - ECOC2026
  - DAY4
---

# B66 笔记：ECOC 2026 We2-I 实时信号处理与实现 场

说明：`0923-We2-I-00-全场连拍.pdf` 为整场连拍（84页），含6位讲者；其余5个单讲PDF（NTT/PCRL/光通信技术与网络实验室/北邮/华为加拿大）是同一批幻灯的分讲版本，大量页为连拍页的重复。页码 pN 均指该PDF内的页码（连拍页码在连拍节内）。数值以图片核对为准。

### 0923-We2-I-00-全场连拍.pdf（第1–11页，第1讲）
- 讲者/机构：Tao Zeng（报告人，zengtao@cict.com）等（Yimei Pan、Chen Wang、Te Ke、Botao Yang、Ziye Zhong、Ziqing Liu、Ming Luo、Ming Li、Xi Xiao、Hanbing Li）/ 光通信技术和网络全国重点实验室（CICT，武汉）与烽火通信 | 题目：Real-Time 100G Burst-Mode Coherent Receiver with Convergence-Free DSP（p1 看图核实）| 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（相干PON）；次 1 oDSP
- 核心主张：
  1. 上行突发难点在每个ONU突发都有独立CFO、随机SOP和异步时钟，迭代式DSP的反馈延迟会吃掉短突发前导；目标是"消除突发起始处的迭代收敛"[p3][p4]。
  2. 分级DSP：快变损伤（时钟、偏振）用前馈处理，慢变损伤（ISI）用每ONU存储的信道状态初始化，实现确定性突发获取[p5]。
  3. 在Xilinx UltraScale+ FPGA上实时验证，并在投稿后把传输距离从15 km扩展到40 km[p9][p10]。
- 关键数据：
  - 前馈定时恢复：功率平方估计直接得采样相位并跟踪时钟漂移，无反馈环；7抽头FIR均衡器从存储的每ONU信道状态起步；用训练头直接估计Jones矩阵做偏振解复用，无迭代MIMO[p5]。
  - 发端：80 GSa/s AWG产生25 GBaud DP-QPSK突发，400符号（16 ns）训练头 + 8800符号/突发，数字模拟±100 ppm时钟偏差[p6]。
  - 收端：集成相干接收机 + 4×40 GSa/s ADC，Xilinx UltraScale+ FPGA，40→50 GSa/s并行重采样，128→160路并行（图上读数）[p6]。
  - FPGA资源：LUT 1.03M（59.4%），寄存器 1.66M（47.9%），DSP 6368（51.8%）；DSP靠乘法器打包降低，插值/重采样用LUT乘法器[p6]。
  - 双ONU仿真用约790 m延迟臂交织；BER在2^16个包上测（约0.056 s/次），监测15分钟[p6]。
  - 灵敏度：单ONU在FEC阈值2×10^-2处 -30 dBm（无EDFA）；OLT侧EDFA后 -36 dBm，系统功率预算>30 dB；双ONU直通支路与单ONU一致，延迟支路仅约1.8 dB代价（延迟路径插损）[p7]。
  - 鲁棒性：-29 dBm下系数冻结与连续自适应的BER在900 s内几乎不可区分；±100 ppm时钟偏差下BER与同步情形相比变化可忽略[p8]。
  - 传输距离：投稿时15 km SSMF（7抽头时域均衡）；现场更新为40 km SSMF，时域DSP架构不变，为2.7倍[p9]。
  - 结论页称FPGA资源利用约50–60%[p10]。
- 提到的公司/客户/产品/标准：烽火通信（Fiberhome）；Xilinx UltraScale+；PON标准（称功率预算符合PON标准）。
- 与业界对比或记录声明（SOTA/首次/record）：未声明record；40 km为相对投稿版15 km的自比较[p9]。
- 推荐配图页：p7（BER vs 接收功率曲线，-30/-36 dBm与>30 dB预算）；p5（分级前馈DSP框图）；p6（实验装置与FPGA资源表）。

### 0923-We2-I-光通信技术与网络实验室-实时信号处理.pdf（第1–3、7–10页为非重复页）
- 讲者/机构：Tao Zeng / 光通信技术与网络全国重点实验室，CICT武汉；烽火通信 | 题目：同上（100G coherent PON 无收敛DSP）| 类型：学术论文
- 方向归属（主/次）：主 5；次 1
- 核心主张：与连拍第1讲相同（分讲版本）。
- 关键数据：内容与上一节一致，本版在p3多一页议程（背景与挑战、无收敛DSP、实验结果、结论及投稿后进展）；其余p4–6、p11为连拍页重复。[p3]
- 提到的公司/客户/产品/标准：同上。
- 与业界对比或记录声明：同上。
- 推荐配图页：见连拍第1讲（本PDF p7–p9 对应灵敏度、鲁棒性、光纤传输页）。

### 0923-We2-I-00-全场连拍.pdf（第12–24页，第2讲）
- 讲者/机构：Zulin Liu、Yan Li、Yaning Sun、Pengpeng Wei、Shuai Wei、Xiaoting Sun、Jian Wu / 北京邮电大学信息光子学与光通信全国重点实验室 | 题目：Low-Complexity FPGA Implementation of Rate-Adaptive Hierarchical Distribution Matcher | 类型：学术论文（场内编号We2-I2）
- 方向归属（主/次）：主 1 oDSP/高波特率器件（概率整形+速率自适应）；次 5 固定与无线接入（PON/FSO灵活速率场景）
- 核心主张：
  1. 数据中心动态流量、PON、时变FSO信道需要实时、细粒度、不中断的速率自适应整形，并要求低复杂度可与FEC/DSP联合集成[p13]。
  2. 提出flex-LUT分层分布匹配器（HiDM）：离线组合搜索最优序列分配 + 共享映射LUT加速率相关索引LUT的双LUT结构 + 流水线对齐控制[p16]。
  3. 单片FPGA上实现无中断、细粒度速率切换，净速率96–179.2 Gb/s，资源占用低，为更强FEC和光DSP集成留余量[p23]。
- 关键数据：
  - 整形容量：相对均匀16QAM，在2.80 bit/symbol处增益约0.49 dB，在3.76 bit/symbol处约0.25 dB；细粒度整形的峰值速率损失 0.181 bit/symbol（发生在3.0873 bit/symbol）[p18]。
  - 速率切换实验（XCVU13P FPGA 端到端）：12–16 ms 内随速率台阶上升，pre-FEC BER 约 1e-2 → 2e-2，post-FEC BER 约 4e-5 → 5e-4，post-DM BER 约 1.3e-4 → 2e-3，未见切换引起的突发错误尖峰（看图核实）[p19]。
  - 误差传播：post-DM BER相对整形前放大最高12.20倍（R_DM=0.1016），最低3.83倍（R_DM=0.8828），整形越强错误传播越大但仍保持HiDM有限突发误码特性[p20]。
  - 信道仿真：FPGA内10 bit AWGN仿真器；逐级下扫，取在重复10 s窗口内持续零误码的第一个速率；净速率96 Gb/s至179.2 Gb/s，随SNR 11–18 dB上升（图上读数）[p21]。
  - 硬件：Xilinx Virtex UltraScale+ XCVU13P；HiDM级350 MHz运行、44.8 Gbaud符号率；总占用CLB LUT 89687（5.19%）、FF 51846（1.50%）、BRAM 59（2.19%）、DSP 512（4.17%，主要为AWGN），总功耗7.048 W（AWGN占3.879 W）；Flex-LUT HiDM本身8482 LUT、0.083 W，Flex-LUT inv-HiDM 22398 LUT、0.649 W[p22]。
- 提到的公司/客户/产品/标准：Xilinx Virtex UltraScale+ XCVU13P；RS码；参考文献含OFC 2024 W4C1、OFC 2025 Tu2F（同组前作）。
- 与业界对比或记录声明（SOTA/首次/record）：p14 对比 ESS、CCDM、MTO、HiDM、PCDM、BWDM 等整形方案在容量增益/速率自适应/低复杂度部署三方面的权衡，本工作基于 Flex-LUT HiDM（Z. Liu 等 OFC 2025 Tu2F），定位为不中断速率自适应 + 低复杂度实现（看图核实）[p14]。
- 推荐配图页：p18（整形容量与速率损失曲线）；p22（FPGA布局图与资源表）；p21（SNR-净速率阶梯曲线）。

### 0923-We2-I-北邮-实时信号处理.pdf（第1–11页）
- 讲者/机构：Zulin Liu 等 / 北京邮电大学 | 题目：Low-Complexity FPGA Implementation of Rate-Adaptive Hierarchical Distribution Matcher | 类型：学术论文
- 方向归属（主/次）：主 1；次 5
- 核心主张与数据：与连拍第2讲相同（分讲版本，p1–11对应连拍p12–23，仅p12为重复页），要点见上节。
- 提到的公司/客户/产品/标准：同上。
- 与业界对比或记录声明：同上。
- 推荐配图页：见上节（对应本PDF p7 整形容量、p10 SNR-速率阶梯、p11 资源表）。

### 0923-We2-I-00-全场连拍.pdf（第25–40页，第3讲：大阪大学）
- 讲者/机构：Syoma Miura、Yohei Koganei、Koji Igarashi / 大阪大学、1FINITY | 题目：Parallel DSP Architecture with Pilot Aggregation for Real-Time MIMO Equalization Enabling Fast Polarization Tracking
- 该讲归属『0923-We2-I-大阪大学-实时信号处理.pdf』，由另一批处理，此处不展开。

### 0923-We2-I-00-全场连拍.pdf（第41–50页，第4讲）
- 讲者/机构：Xuefeng Tang、Shengming Ma、Zhikui Yong、Wenyi Hu、Ge Gao、Zhiyu Xiao、Shuangyuan Wu、Minggang Si、Zhuhong Zhang / 华为（加拿大渥太华 + 深圳，标HUAWEI，芯片标HiSilicon）| 题目：AI-core Enabled Real-time 2.0-Tbit/s Coherent Transceiver Operating at 234 Gbaud | 类型：学术论文
- 方向归属（主/次）：主 1 相干/oDSP/高波特率器件；次 2 ZR/ZR+（提及1.6T ZR+兼容、ZR/LR系统）
- 核心主张：
  1. 首个2.0 Tb/s实时相干收发机，工作在234 Gbaud的记录波特率，支持最高2.0 Tb/s灵活速率[p43][p44][p50]。
  2. 自研CMOS ASIC中的高级DSP（FDE、TxNLC、FDC、RxNLC、PCS、双子载波）缓解硬件损伤，使234 Gbaud 64QAM成为可能[p45][p50]。
  3. 集成AI计算核（贝叶斯优化、CNN/MLP）优化性能；60 km SSMF上实时无误码传输2.0 Tb/s[p46][p50]。
- 关键数据：
  - Tx与Rx电带宽均超过120 GHz（10 dB损耗处），可支持240 Gbaud运行；图为4通道Tx/Rx幅频响应[p44]。
  - DSP架构：Tx侧 DAC、TxNLC、IFFT、FDE、Mux、FFT、PCS、FEC/交织；Rx侧 ADC、RxNLC、重定时、FDC、解复用、2×2 MIMO、CDC、CR、解交织/FEC；双带数字子载波方案，谱图为194.0–194.2 THz范围内两个子载波，兼容1.6T ZR+标准，并缓解ADDA时钟抖动与EEPN[p45]。
  - AI核通过控制总线和数据RAM与ASIC相连，支持贝叶斯优化、CNN、MLP，并做在线光性能监测（PMD、PDL、BER、SNR）[p46]。
  - 贝叶斯评分 S = α×BER_avg + (1-α)×BER_max，BER_avg在数百毫秒采样，BER_max取纳秒级滑窗内多次测量最大值[p47]。
  - 贝叶斯多维联合优化（ADC/DAC失配、带宽peaking/CTLE、DSP设置、驱动增益、接收光功率、TIA增益）约100次迭代收敛，BER由2.5×10^-2降至1.7×10^-2，约0.7 dB Q因子改善；顺序优化只得到次优点[p48]。
  - 60 km SSMF：pre-FEC BER约0.029（图读数，稳定），post-FEC无误码，连续监测10小时（图横轴约600 min），Q因子余量>0.6 dB；4个子载波（X/Y各2）星座为64QAM类图样[p49]。
  - 发展趋势图：相干收发机速率随年份（2006–2026），本工作星标位于实时曲线上最新点，略高于2025的1.6T实时点[p43]。
- 提到的公司/客户/产品/标准：华为、HiSilicon自研DSP ASIC；1.6T ZR+；ZR/LR。
- 与业界对比或记录声明（SOTA/首次/record）："First 2.0 Tbit/s real-time coherent transceiver""record baud rate of 234 Gbaud"[p43][p44]。
- 推荐配图页：p49（60 km 10小时BER与星座）；p48（贝叶斯优化BER收敛曲线）；p43（收发机速率演进图，星标本工作）；p45（DSP框图与双子载波谱）。

### 0923-We2-I-华为加拿大-实时信号处理.pdf（第1–10页）
- 讲者/机构：Xuefeng Tang 等 / 华为 | 题目：AI-core Enabled Real-time 2.0-Tbit/s Coherent Transceiver Operating at 234 Gbaud | 类型：学术论文
- 方向归属（主/次）：主 1；次 2
- 核心主张与数据：与连拍第4讲相同（分讲版本，p3、p7、p10为连拍页重复；本版p4=收发机与带宽，p5=DSP，p6=AI核，p8=贝叶斯优化，p9=60 km传输），要点见上节。
- 提到的公司/客户/产品/标准：同上。
- 与业界对比或记录声明：同上（首个2.0 Tb/s实时、234 Gbaud）。
- 推荐配图页：本PDF p9（60 km BER/星座）、p8（贝叶斯优化曲线）。

### 0923-We2-I-00-全场连拍.pdf（第51–73页，第5讲）
- 讲者/机构：Hiroshi Yamazaki、Josuke Ozaki、Yoshihiro Ogiso、Masanori Nakamura、Kohki Shibahara、Takayuki Kobayashi、Toshikazu Hashimoto、Yutaka Miyamoto / NTT, Inc. | 题目：Completely Optical-Filterless Comb-Based Transmitter with a Relaxed Clock Rate for Multi-Tbps Single-Carrier Transmission | 类型：学术论文（场内编号We2-I5/258）
- 方向归属（主/次）：主 1 高波特率器件/相干；次 3 调制器（InP双IQM）
- 核心主张：
  1. 基于光梳的带宽扩展发射机是多Tbps/波长相干的候选，主要挑战是高时钟率和/或对波长敏感的光梳解复用滤波器[p73]。
  2. 基于B/2间隔频谱切片的"频谱编织"（digital spectral weaver, DSW）同时解决两个问题：无需光滤波器，且DSP时钟减半（本研究 f_clock=B/2，MIMO由8×4增至16×8）[p61–p68][p73]。
  3. 以40 GHz时钟、无光滤波器实现2.9 Tbps/波长传输[p73]。
- 关键数据：
  - 目标信号：320 GBaud PCS-64QAM；AWG 240 GSa/s（带宽80 GHz）；DSW为16×8固定MIMO；发射用InP n-p-i-n延迟双IQ调制器模块（CDM-D2IQM，延迟τ=12.5 ps即1/τ=80 GHz）；光梳由PM在193.40 THz ECL上以40 GHz驱动产生（20 GHz经×2倍频）；后接65.7 ns PDME（偏振复用模拟）[p69][p71]。
  - 谱图：D2IQM在梳输入下输出宽度约±160 GHz以上的拼接谱，CW输入下约80 GHz带宽；梳线间隔40 GHz[p71]。
  - 接收：LO频率切换相干接收，两个ECL（193.48 THz与193.32 THz）经门控，20 kHz切换，256 GSa/s、110 GHz带宽DSO，离线DSP，SSMF 80 km，重复25 μs；320 GHz带宽经切换合成[p70]。
  - 结果：背靠背最佳净比特率 2.94 Tbps（熵11 bit/4D-symbol处，AIR约3.08 Tbps）；80 km SSMF后净比特率 2.90 Tbps（同熵点，AIR约3.04 Tbps）；熵10–12 bit/4D-symb范围扫描，熵12时净速率降至约2.72（B2B）/2.67（80 km）Tbps（图读数）[p72]。
- 提到的公司/客户/产品/标准：NTT；参考文献含K. Shi OFC 2017 M2D.3（LO频率切换接收）、arXiv:2604.01623 (2026)（同组）。
- 与业界对比或记录声明（SOTA/首次/record）：p60对比"需光滤波器的频谱拼接"、"前作频谱编织"与"本研究（无滤波器+降时钟）"；未在页上看到"record"字样[p60]。
- 推荐配图页：p72（B2B与80 km的AIR/NBR曲线，2.94/2.90 Tbps）；p71（三条谱：梳输出、CW与D2IQM输出）；p69（发射端装置与D2IQM芯片）。

### 0923-We2-I-NTT-实时信号处理.pdf（第2–5、8–20页为非重复页）
- 讲者/机构：Hiroshi Yamazaki 等 / NTT | 题目：Completely Optical-Filterless Comb-Based Transmitter with a Relaxed Clock Rate for Multi-Tbps Single-Carrier Transmission | 类型：学术论文
- 方向归属（主/次）：主 1；次 3
- 核心主张与数据：与连拍第5讲相同（分讲版本，扫描件带CamScanner水印；本版p17=发射端，p18=接收端，p19=谱图，p20=传输结果，p1、p21等为重复页），要点见上节。
- 提到的公司/客户/产品/标准：同上。
- 与业界对比或记录声明：同上。
- 推荐配图页：本PDF p20（传输结果）、p19（谱图）。

### 0923-We2-I-00-全场连拍.pdf（第74–84页，第6讲）
- 讲者/机构：George Brestas、Christoph Füllner、Robert Borkowski、Maria Spyropoulou、Dimitris Apostolopoulos、Giannis Kanakis（报告人，下划线）、Hercules Avramopoulos / Nokia Bell Labs 与 PCRL（p74 标题页看图核实；Argotech 字样出现在芯片板上）| 题目：First-Ever Burst-Capable Adaptive Optical Signal Processor for Next-Generation PON Upstream Links | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（PON上行）；次 3 光源/调制器/电芯片（InP光子集成）
- 核心主张：
  1. 首个可突发的自适应光信号处理器（AOP）：单片InP PIC，纳秒级逐突发重构，比热调光均衡器快多个数量级[p84]。
  2. 单个光学级同时完成均衡与噪声抑制：CD严重时填补谱凹陷，CD不主导时转向宽带抑制，不增加数字复杂度[p84]。
  3. 接收机SOA的噪声代价被AOP大部分恢复，且AOP单独优于数字FFE；面向100 Gb/s及以上PON上行的紧凑接收机[p82][p84]。
- 关键数据：
  - 器件：4抽头光FIR滤波器，P_out(t)=Σ_{i=1..4} ±g_i P_in(t−iτ)，抽头延迟τ=10 ps，抽头控制为SOA增益 + 相移器，InP两步SI-BH工艺[p79]。
  - 实验：AWG产生50 Gbaud（50 Gb/s）突发，240 ns突发/560 ns保护间隔，MZM偏置在正交点与零点间切换以获得高消光比；波长1340 nm；2 km与25 km光纤路径去相关交织，得到两种色散（19与81 ps/nm）的突发；5 km馈线光纤，VOA，SOA + AOP + APD+TIA接收；AOP系数由贝叶斯优化离线得到并存入LUT，由快速电流开关ns级切换[p80]。
  - 时域：AOP电流在突发边界切换，BER随突发迅速收敛，重构只占突发一小部分（图中周期约400 ns）[p81]。
  - 灵敏度（BER阈值约2×10^-2附近读图）：Burst 2（81 ps/nm）比Burst 1（19 ps/nm）差约3 dB（有无数字FFE均如此）；AOP将差距缩小到约1.5 dB；同为带booster SOA时，AOP单独优于数字FFE（FFE在探测后无法恢复SOA噪声代价）；图例含No eq、FFE13、AOP、AOP+FFE5[p82]。
  - 传递函数：Burst 2（25 km）AOP将30 GHz之前的谱凹陷大部分恢复；Burst 1（2 km）AOP整体低于未校正信道（宽带抑制）[p83]。
  - 功耗：约300 mW偏置功率（约6 pJ/bit @50 Gb/s），可与接收前端共集成，避免薄膜光滤波器[p84]。
  - 背景：PON功率预算29–35 dB，IM/DD NRZ-OOK低成本但带宽受限，主张ONU发射端保持简单、均衡集中在OLT[p76]。
- 提到的公司/客户/产品/标准：Nokia Bell Labs；PCRL；Argotech（板卡）；GPON共存、VHSP（Very High Speed PON）；对比参考Staffoli CLEO 2025、Wang arXiv 2025、Sackesyn Opt. Express 2021（光域均衡方案）[p78]。
- 与业界对比或记录声明（SOTA/首次/record）："First-ever burst-capable adaptive optical signal processor"（题目）；对比热调光均衡器"快多个数量级"[p84]。
- 推荐配图页：p82（Burst1/2灵敏度曲线，3 dB到1.5 dB）；p79（AOP芯片与4抽头原理）；p81（突发边界处电流切换与BER）；p80（实验装置）。

### 0923-We2-I-PCRL-实时信号处理.pdf（第5、6、8页为非重复页）
- 讲者/机构：George Brestas 等 / Nokia Bell Labs、PCRL | 题目：First-Ever Burst-Capable Adaptive Optical Signal Processor for Next-Generation PON Upstream Links | 类型：学术论文
- 方向归属（主/次）：主 5；次 3
- 核心主张与数据：与连拍第6讲相同（分讲版本，带CamScanner水印；p1–4、7、9–11为连拍页重复；本版p5=光域均衡文献对比，p6=AOP芯片，p8=BER时域演化），要点见上节。
- 提到的公司/客户/产品/标准：同上。
- 与业界对比或记录声明：同上。
- 推荐配图页：本PDF p6（芯片与工作原理）。

## 本批小结

1. 实时/可实现性成为本场主线：华为2.0 Tb/s 234 Gbaud ASIC、烽火/CICT的100G相干PON FPGA、北邮HiDM FPGA、Nokia/PCRL突发AOP都以真实硬件平台（ASIC/FPGA/InP PIC）而非离线DSP作为卖点（来自：华为、CICT、北邮、Nokia/PCRL）。
2. 相干技术向接入侧下沉，核心难点是突发模式：CICT用前馈定时+LUT初始化均衡+训练头Jones估计，在-30 dBm（无EDFA）/-36 dBm（EDFA）灵敏度下实现100G突发相干，40 km为投稿后更新；Nokia/PCRL则走IM/DD + 光域均衡路线，在ns级切换实现逐突发自适应。两条路线都围绕"让每个上行突发免去迭代收敛"（来自：CICT、Nokia/PCRL）。
3. 单载波速率天花板继续上移，路径不同：华为靠ASIC + 双子载波、Tx/Rx电带宽>120 GHz，实现234 Gbaud/2.0 Tb/s实时并在60 km无误码；NTT用光梳 + 频谱编织，以40 GHz时钟实现320 GBaud PCS-64QAM，净速率2.94 Tbps（B2B）/2.90 Tbps（80 km），但为离线DSP（来自：华为、NTT）。
4. AI/优化算法进入器件与DSP调参环节：华为以贝叶斯优化联合优化ADDA、DSP和硬件参数，BER 2.5×10^-2降至1.7×10^-2（约0.7 dB Q）；Nokia/PCRL同样以贝叶斯优化离线得到每突发AOP系数并存LUT（来自：华为、Nokia/PCRL）。
5. 概率整形成为可硬件化的模块：北邮的flex-LUT HiDM在XCVU13P上仅占LUT约5.19%，支持44.8 Gbaud@350 MHz，实现96–179.2 Gb/s无中断速率自适应；华为DSP链路中亦含PCS，NTT用PCS-64QAM并扫描熵取最优净速率（来自：北邮、华为、NTT）。
6. 本场另有大阪大学一讲（导频聚合并行MIMO均衡）由另一批处理，未纳入本批分析。
