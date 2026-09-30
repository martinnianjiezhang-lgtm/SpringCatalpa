---
title: "B83 · DAY5 · Th2-E-接收机与光电探测器"
tags:
  - ECOC2026
  - DAY5
---

### 0924-Th2-E1-NVIDIA-低PDL二维光栅耦合器实现4波64Gbps偏振分集硅光DWDM接收机.pdf
- 讲者/机构：Nandish Mehta, Trey H. Greer, Meer Sakib, C. Thomas Gray（NVIDIA，Santa Clara / Durham）| 题目：A 4-λ × 64 Gb/s Polarization-Diverse Silicon Photonic DWDM Receiver Using Low-PDL 2D Grating Couplers | 类型：学术论文
- 方向归属（主/次）：主 [3 Scale-out：电芯片/光源/调制器（微环DWDM光I/O接收端）]；次 [4 Scale-up/in CPO]
- 核心主张：
  1. 偏振分集接收机（2D光栅耦合器 + 环回微环组 + 双输入光电探测器dHSPD）可在普通SMF上工作，无需保偏光纤(PMF)或主动偏振跟踪 [p13]
  2. 偏振分集要有效，2D光栅耦合器的PDL必须足够低（α=β 才能避免光电流随输入偏振角θ波动）；低PDL光I/O是硅光DWDM偏振分集RX的必要条件 [p4, p5, p13]
- 关键数据：
  - 4 个DWDM通道，400 GHz间隔，每通道 64 Gb/s（4×64 Gb/s）[p10, p13]
  - 单个独立环回测试点：IL 约 2 dB（1300 nm附近峰值），PDL < ±0.1 dB，工作范围约 1300–1310 nm [p8]
  - 300 mm 晶圆级：252 个环回测试点，1300–1310 nm 范围 PDL 在 ±0.2 dB 以内 [p8, p13]
  - 耦合角优化：θp=θoptimal 时光电流稳定在约 0.42 mA；θp=θoptimal−3° 时随SOP变化光电流在约 0.32–0.45 mA 间大幅波动 [p9]
  - 参考TX（λ1）：SNR = 10.5 dB，ER = 12.7 dB；RX输出（λ4，固定SOP）：SNR = 8.1 dB [p10]
  - SOP以约 2000 rad/s 扰动：SNR 由 8.1 dB 降至 7.6 dB；固定/扰动SOP下均测到 BER < 10^-12，无主动偏振跟踪（浴盆曲线约 ±0.2–0.3 UI 采样窗口，读图估计）[p12]
  - RX版图 820 × 193 μm²；微环半径 5 μm，400 GHz间隔，集成金属加热器；2D GC 为曲线聚焦光栅；环回监测结构 127 μm [p6]
  - 平台：65 nm SOI硅光PIC，与先进CMOS（如7 nm FinFET）EIC 通过 Cu–Cu 混合键合(SoIC)做3D堆叠，硅微透镜(μLens)实现表面耦合，KGD+FAU [p7]
- 提到的公司/客户/产品/标准：NVIDIA（MSD、ATG团队致谢）；Mekis JSTQE 2011、Nojic OFC 2020、Xu OFC 2024、Mehta OFC 2026、Chen ECTC 2025（引用）；MRM/MRR、DWDM激光源（4λ、400 GHz 间隔经 PMF 送 TX；p2 纵轴仅标 dBm per λ (P0)，无具体数值）；平台为 7nm FinFET EIC + 65nm SOI PIC 的 SoIC Cu-Cu 混合键合 3D 堆叠 [p2, p7，看图核实]
- 与业界对比或记录声明（SOTA/首次/record）：未声明record；主张为在普通SMF上无PMF/无主动偏振控制的 4λ×64 Gb/s 偏振分集DWDM RX [p2, p13]
- 推荐配图页：p8（单点与300 mm晶圆级PDL/IL实测）；p12（SOP扰动下眼图与BER浴盆曲线）；p4（偏振分集RX工作原理与光电流–偏振角曲线）

### 0924-Th2-E2-东南大学与紫金山实验室-电极神经逆设计实现220GHz带宽UTC光电二极管.pdf
- 讲者/机构：Jianwei Chen（报告人）, Min Zhu, Xingyu Chen, Jiao Zhang, Yuancheng Cai, Mingzheng Lei, Bingchang Hua, Junjie Ding, Yunwu Wang, Long Zhang, Xiaohu You（东南大学 / 紫金山实验室）| 题目：Neural Inverse Design of Electrodes Enables Uni-Traveling-Carrier Photodiodes with 220 GHz Bandwidth and 2.7 dBm Output Power at 170 GHz（p1 看图核实）| 类型：学术论文
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件（高速光电探测器）]；次 [5 固定与无线接入 RoF/太赫兹光生（THz光子学）]
- 核心主张：
  1. 用多任务并行神经网络(MTNN)对共面波导/感性电极做逆向设计，可把UTC-PD带宽从约 135 GHz 的设计目标提升，仿真 227 GHz、实测 220 GHz [p12, p16]
  2. 光子学方式产生THz可绕过电子器件带宽瓶颈，UTC-PD是核心器件；改进的外延（MNBUTC-PD能带）提升饱和光电流 [p6, p8]
  3. 后续方向：器件封装（含CPO平台、同轴/波导封装）与THz收发芯片、系统验证 [p17]
- 关键数据：
  - MTNN vs 全连接网络(FCNN)：MSE 约 0.0016 vs 0.041（训练样本约 13 万），精度提升 25.6×，R² = 0.998 [p10]
  - 3 μm 台面 UTC-PD：3 dB带宽 220 GHz，响应度 0.15 A/W，饱和功率 −1 dBm @200 GHz，饱和光电流 14 mA，暗电流 1.4 nA @−2 V；曲线上另见 2.4 dBm @110 GHz（读图）[p16]
  - 6 μm 台面 D 波段(110–170 GHz) UTC-PD：3 dB带宽 150 GHz（无电感电极仿真为 97 GHz，采用 100 GHz 电感峰电极后提升到 150 GHz），响应度 0.23 A/W，饱和功率 6.3 dBm @110 GHz（2.7 dBm @170 GHz），饱和光电流 >25 mA，暗电流 2.2 nA @−2 V [p15]
  - CPW逆设计案例（MTNN 逆设计电极间距/电感长度/位置/金属厚度）：S21 误差 0.16 dB，电感误差 0.06 nH（与目标吻合）[p11，看图核实]
  - 测试系统：VNA 覆盖 DC–110 GHz；光外差法 110–170 GHz、170–260 GHz [p14]
- 提到的公司/客户/产品/标准：ITU-R M.2160（IMT-2030）、WRC-19（275–450 GHz）、美国DARPA THOR、Horizon Europe、中国国家重点研发计划（太赫兹相关）、NTT（2006 THz通信演示）；Ge/Si、硅-石墨烯、InP/InGaAs 光电二极管对比 [p5–p7]
- 与业界对比或记录声明（SOTA/首次/record）：p15 有雷达图对比 Ref.[5]–[9]（带宽/光电流/RF功率），未见明确 record 字样 [p15]
- 推荐配图页：p16（220 GHz频响、THz输出功率、S22与暗电流）；p12（逆设计流程与带宽由135→227 GHz）；p10（MTNN架构与精度对比）

### 0924-Th2-E3-imec-数据中心光互连用高可靠免CMPGe-on-Si波导光电二极管.pdf
- 讲者/机构：Solomon Musibau, Conor Coughlan, Natarajan Rajasekaran, Hakim Kobbi, Artemisia Tsiara, Sadhishkumar Balakrishnan, Leili Shiramin, Philippe Absil（imec，比利时Leuven）| 题目：Highly Reliable CMP-Free Ge-on-Si Waveguide Photodiodes for Data Center Optical Interconnects | 类型：学术论文
- 方向归属（主/次）：主 [3 Scale-out 224G/448G：光电探测器/电芯片器件]；次 [4 Scale-up/in CPO]
- 核心主张：
  1. 免CMP的Ge-on-Si横向p-i-n光电二极管在保持高速的同时，Ge/SiO2界面缺陷少、电荷俘获弱，长期稳定 [p17]
  2. 晶圆级加速老化与500 h HTOL均未观测到暗电流退化；CPO等高热密度场景需要此类可靠性 [p14, p15, p17]
- 关键数据：
  - 1310 nm，−2 V：响应度 0.89 ± 0.02 A/W（48器件，Popt=−8 dBm）[p11]
  - −2 V：3 dB带宽 65.3 ± 1.5 GHz（9器件，Popt=−11 dBm，由S参数提取；−3 V 约 70 GHz，读图）[p11]
  - 25 °C，90 器件，−2 V：暗电流 3.34 ± 0.55 nA；室温暗电流 < 10 nA [p12, p17]
  - 暗电流：−2 V 下 3.34 ± 0.55 nA（25 °C、90 器件，晶圆均匀性好）；热激活泄漏主导，25–175 °C 行为一致；激活能约 0.33–0.47 eV，输运机制为扩散+SRH，无 TAT [p12, p13，看图核实]
  - 晶圆级加速老化（150 °C，−4 V 应力约 2.8 h）：暗电流无退化，应力超过工作电压 −2 V 的两倍仍无退化；测试条件含 150 °C/−3,−4,−5 V 与 175 °C/−3,−4 V [p14]
  - HTOL 500 h：125 °C/−3 V、150 °C/−3 V、175 °C/−2 V、175 °C/−3 V，每条件 5–6 器件；失效判据为 85 °C、−2 V 下暗电流增大 10×，500 h后无显著退化 [p15]
  - 退化机制：应力下热辅助电荷俘获于预存缺陷（引 Musibau IRPS 2024），应力后静电势改变+SRH 产生增强，去应力后电荷脱陷+复合即恢复；免 CMP 工艺使预存 Ge/SiO2 缺陷少→退化弱且可恢复 [p16，看图核实]
- 提到的公司/客户/产品/标准：imec 200-mm 硅光平台（iSiPP200/iSiPP300）；引用 Lischke Nature Photonics 2021（Ge PD 记录带宽 265 GHz）、Coughlan OFC 2026、Shahin OFC/ECOC 2026、Musibau IRPS 2024 [p6, p10, p18]
- 与业界对比或记录声明（SOTA/首次/record）：p6 引述Ge PD"state-of-the-art record BW 265 GHz"（Lischke 2021）作背景，非本工作；本工作主张为免CMP+可靠性 [p6]
- 推荐配图页：p15（HTOL 500 h暗电流演化与85 °C I-V盒图）；p11（响应度与带宽晶圆级统计）；p17（总结）

### 0924-Th2-E4-米兰理工-自适应MZI光子网格实现片上实时偏振解复用.pdf
- 讲者/机构：S.M. SeyedinNavadeh 等（Politecnico di Milano，含 Samuele De Gaetano, Michele Crico, Andrea Melloni, Francesco Zanetto, Francesco Morichetti；页脚仅标 SeyedinNavadeh）| 题目：On-Chip Real-Time Polarization Demultiplexing using an Adaptive MZI Photonic Mesh | 类型：学术论文
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件（片上偏振解复用/SDM）]；次 [4 Scale-up/in（电光单片集成 EPIC）]
- 核心主张：
  1. 8-mode MZI网格实验实现偏振与相位不敏感的相干合束器，并兼作偏振解扰器 [p15]
  2. 在标准硅光平台上单片集成数字MUX（PD读出）与DEMUX+驱动（热光移相器TOPS），显著减少电学端口数，利于扩展 [p10, p15]
  3. 同一EPIC增加对角线数即可用于光纤/自由空间SDM；下一步在同平台集成TIA等更多电子元件 [p15]
- 关键数据：
  - 芯片：AMF多项目晶圆(MPW)，220 nm厚Si波导，芯片长 6.3 mm；8模MZI网格4条对角线，MZI×22，4路边耦合输入（2偏振），4路光栅耦合输出；PD×22，TOPS×44 [p10]
  - 端口数：34 pad（11 MUX + 10 DEMUX + 5 驱动 + 8 GND/阴极）vs 74（44 TOPS + 22 PD + 8），减少 54% [p10]
  - 单片晶体管（AMF标准工艺，无工艺改动）：VT 1.8 V，μC'ox(W/L) 4 μA/V²，VA 35 V，亚阈值摆幅 250 mV/dec，CG 2.8 fF；SOI BOX 3 μm [p5]
  - 相干合束实验：λ=1550 nm，25 Gb/s NRZ-OOK，4根偏振被扰动的光纤输入，EDFA+BPF+高速PD+示波器；网格锁定后 QF = 6.88（仅相位变化）、6.75（相位+偏振变化）；网格固定时眼图闭合 [p12]
  - 配置时间约 25 ms；锁定后最后一级MZI输出功率增大并趋稳（Pol0–Pol10共11种偏振态测试）[p13]
  - 偏振解扰：用两条对角线，X/Y各 25 Gb/s NRZ-OOK；解复用后消光比 >18 dB；单偏振 QF = 5.2（OUT1）/4.6（OUT2），X+Y锁定后 QF = 4.3 / 4.3，固定时眼图闭合 [p14]
  - 控制方式：外部时分复用控制，基于dithering（抖动）技术；FPGA+ADC读取PD，DAC经片上DEMUX驱动TOPS [p6, p9]
- 提到的公司/客户/产品/标准：Advanced Micro Foundry (AMF)；Polifab、PIX Europe、Chips JU（页脚标识）；引用 Zanetto TED 2023、De Gaetano Sci Rep 2026、Seyedin Navadeh Nat. Photon 2024、Grillanda ECOC 2025 PDP [p4, p5, p9]
- 与业界对比或记录声明（SOTA/首次/record）：无 SOTA/record 声明；p5 强调在标准硅光平台（AMF）"零工艺改动"单片集成晶体管（V_T 1.8 V、亚阈值摆幅 250 mV/dec、C_G 2.8 fF，引 Zanetto TED 2023）[p5，看图核实]
- 推荐配图页：p12（相干合束实验框图、14个加热器电压与眼图QF）；p10（实际芯片与端口数-54%）；p14（偏振解扰框图、消光比>18 dB与眼图）

## 本批小结
1. 偏振管理趋向"免主动跟踪/片上自适应"：NVIDIA(E1) 用低PDL 2D光栅耦合器+环回结构，在约 2000 rad/s SOP扰动下 64 Gb/s 通道 BER<10^-12 且无需PMF；米兰理工(E4) 则用MZI网格+片上电子做自适应偏振解复用（配置约 25 ms，消光比>18 dB）。两篇（E1、E4）分别代表"被动分集"与"主动自适应"两条路线。
2. 高速光电探测器的两极：东南大学/紫金山(E2) 的UTC-PD（InP系）在 3 μm 台面实测 3 dB带宽 220 GHz 面向THz光生；imec(E3) 的Ge-on-Si PD为 65.3 GHz、0.89 A/W（1310 nm），走的是可制造性与可靠性（CMP-free）路线，服务数据中心/CPO（E2、E3）。
3. 可靠性成为CPO时代PD的指标：E3 明确以CPO高热密度、器件间热串扰为动机，给出 125–175 °C、−2 至 −3 V、500 h HTOL 无显著暗电流退化（10× 判据）；E2 也把 CPO 平台列入封装进展（E2、E3）。
4. AI/神经网络进入器件设计流程：E2 的MTNN逆设计使电极设计误差(MSE)相对全连接网络降低约 25.6×，把带宽设计目标由 135 GHz 推到 220–227 GHz，体现"AI辅助电磁/光电协同设计"（E2）。
5. 电光单片集成的两种尺度：E1 采用 65 nm SOI PIC + 7 nm FinFET EIC 的 3D 堆叠(Cu–Cu混合键合)，E4 则在无工艺改动的AMF标准硅光平台上直接做MOS电子做控制，端口减少 54%（E1、E4）。
6. O波段DWDM（1300–1310 nm，400 GHz间隔，微环）与 1550 nm SDM/偏振控制并存，说明偏振与相位不敏感接收在短距DWDM和相干/SDM场景都是共性需求（E1、E4）。
