---
title: "ECOC2025 Scale Out 论文索引"
tags:
  - ECOC2025
  - 论文索引
---

ECOC 2025 中归入 **Scale Out**（224G/448G IM-DD、光源、调制器、探测器、OCS）的论文 **101** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）和代际。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2025 ECOC/index|2025年 ECOC 论文专题洞察]]

> [!summary] 关键结论
> 单波 IM-DD 极限被推到净 651 Gb/s〔Tu.03.06.1〕与 320 GBd 净 512 Gb/s〔M.02.07.4〕；400G/lane 雏形出现在 GeSi EAM 224 GBd（PDP）〔Th.03.01.4〕、TFLN 448G 无放大〔Tu.03.07.2〕、等离子体 MZM 净 400G〔W.04.07.5〕、182 GBd PAM6 20 km〔W.04.07.4〕；器件侧零偏 95 GHz 微环〔M.02.02.1〕、205 GHz PD〔Tu.01.02.1〕；AWGR 纳秒光交换加速分布式训练〔Tu.03.07.5〕。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#调制器\|调制器]] | 22 | Si MZM/MRM、TFLN/TFLT、BTO、EML/EAM、等离子体等 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#光DSP\|光DSP]] | 16 | IM-DD 均衡、MLSE/FEC、时钟恢复、光域处理 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#电SerDes及连接器\|电SerDes及连接器]] | 2 | SerDes、DAC/ADC、驱动/TIA、LPO/LRO、电通道 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#OCS\|OCS]] | 5 | 光电路交换、WSS/AWGR 交换、AI 集群光交换网络 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#光源\|光源]] | 22 | 激光器、光梳、外置光源 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#探测器与接收\|探测器与接收]] | 14 | Ge/InP 光电探测器、APD、接收机 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#集成平台与无源器件\|集成平台与无源器件]] | 18 | 硅光/SiN/异质集成平台、耦合器、滤波器、复用器 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#链路与系统\|链路与系统]] | 2 | 短距链路与系统级实验 |

**二级专题 × 代际**

| 二级专题 | 224G | 448G | — |
|---|---|---|---|
| 调制器 | 3 | 10 | 9 |
| 光DSP | 2 | 3 | 11 |
| 电SerDes及连接器 | – | 1 | 1 |
| OCS | – | – | 5 |
| 光源 | 6 | 3 | 13 |
| 探测器与接收 | 4 | 4 | 6 |
| 集成平台与无源器件 | – | 1 | 17 |
| 链路与系统 | – | 1 | 1 |

## 调制器

22 篇 · Si MZM/MRM、TFLN/TFLT、BTO、EML/EAM、等离子体等

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M.02.02.1 | 口头 | 芯片 | — | Driver-free and Bias-free 112 Gb/s NRZ O-band Silicon Microring modulator with 95 GHz bandwidth | 零偏压、无驱动的O波段硅微环调制器，带宽创纪录达95 GHz，0.9 Vpp实现112 Gb/s NRZ |
| M.02.02.2 | 口头 | 器件 | — | A 50 Gb/s NRZ O-band Silicon Disk Modulator with 6.4 THz FSR | 半径2.1 µm的硅微盘调制器，FSR达6.47 THz，集成加热器，1.6 Vpp驱动下50 Gb/s NRZ |
| M.02.02.3 | 口头 | 器件 | — | Suspended Membrane TWE-TFLN Mach-Zehnder Modulator on Silicon Substrate | 悬空薄膜上的行波TFLN马赫-曾德调制器（硅衬底），3-dB带宽>110 GHz、Vπ=3.3 V |
| M.02.02.4 | 口头 | 器件 | 448G | High-speed Direct-Detection Advanced Modulation Format Transmission Using a Silicon Microring Modulator with >90 GHz Bandwidth | >90 GHz带宽硅微环调制器实现300 Gb/s DMT、280 Gb/s PAM4与330 Gb/s PAM8直检传输 |
| M.02.07.4 | 口头 | 光系统 | 448G | Net 512 Gbps 320 Gbaud PAM4 Faster-Than-Nyquist Transmission With a 3 nm SerDes and TFLN Modulators | 3 nm SerDes单DAC+TFLN调制器实现320 GBd PAM4超奈奎斯特传输，净速率512/606 Gb/s（纪录） |
| M.03.02.1 | 特邀 | 器件 | — | Thin-Film Lithium-Niobate Photonic Devices with Gratings | 特邀：薄膜铌酸锂光栅器件（多模波导光栅、FP腔调制器、AWG）用于CWDM/DWDM与波长选择调制 |
| M.03.02.2 | 口头 | 器件 | 448G | 420 Gb/s Plasmonic Optical DAC for Coherent and IM/DD | 等离子体光学DAC实现420 Gb/s，用于相干与IM/DD，在光域完成功率高效的幅度复用 |
| M.03.02.3 | 口头 | 芯片 | — | Efficient InGaAsP MOSCAP Microring Optical Modulator on III-V Membrane Platform | III-V薄膜平台上的InGaAsP MOSCAP微环调制器，调制效率0.89 V·cm，32 Gb/s清晰眼图 |
| Th.01.02.4 | 口头 | 芯片 | 448G | Multi-functional Heterogeneously Integrated TFLN on Silicon Photonics Platform Enabling 540 Gbps/lane IMDD Transmission with 0.9 Vpp Driving Voltage | TFLN异质集成于SiN-SOI平台，调制带宽>110 GHz、耦合损耗0.6 dB，首次0.9 Vpp实现540 Gb/s/lane IMDD |
| Th.01.03.1 | 口头 | 芯片 | — | Graphene-based Athermal Optical Transmitter | 氮化硅PIC上集成石墨烯电吸收调制器的无热光发射机，20–60°C支持100 Gb/s |
| Th.01.03.2 | 口头 | 器件 | — | Low Chirp and trimmable Push-pull Thin-Film Lead Zirconate Titanate Ring modulator | 薄膜PZT推挽微环调制器，调制效率46 pm/V，低啁啾100 Gb/s，可易失/非易失修调谐振、零静态功耗 |
| Th.03.01.4 | PDP | 器件 | 448G | 110 GHz GeSi Electroabsorption Modulator on a 300mm SiPh Platform Enabling High-Density 400G/lane IM/DD Links | 300 mm硅光平台GeSi电吸收调制器带宽>110 GHz，200–224 GBd PAM-4，面向400G/lane Scale-up |
| Tu.01.03.4 | 口头 | 芯片 | 448G | 320 Gb/s Unamplified Transmission using 100 GHz Ge PD and TFLN MZM on a Foundry-Compatible SiPh Platform Co-Packaged with Traveling-Wave Drivers and TIAs | 硅光平台上转印TFLN MZM+100 GHz Ge PD与行波驱动/TIA共封装，O波段160 GBd PAM-4无放大2 km 320 Gb/s |
| Tu.03.02.2 | 口头 | 器件 | — | High-Speed Free-Space Electro-Optic Modulator using Double-Layered Dimerized Nanometallic Grating | 双层二聚化纳米金属光栅自由空间有机电光调制器(首次)，100×100 µm²器件带宽4 GHz |
| Tu.03.06.6 | 口头 | 算法 | 448G | 400 Gbps Net Bitrate Optical-Amplification-Free TFLN-based PAM4 Link Enabled by BU-LSTM Equalization | TFLN MZM+BU-LSTM均衡实现O波段无光放大400 Gb/s净速率PAM4链路(500 m) |
| Tu.03.07.2 | 口头 | 光系统 | 448G | 448 Gbps optical-amplification-free PAM6/8 transmission using TFLN transmitter and SNR enhancement approach | 超宽带巴伦聚合4路AWG提升SNR，TFLN发射机0.6 Vpp实现448 Gb/s无光放大PAM6/8 O波段传输 |
| Tu.04.03.2 | 口头 | 芯片 | 224G | 8-Channel Monolithic InP Transmitter PIC Integrating DFB and MZM Arrays, Capable of Operating 106 GBd PAM4 at 85 °C | 单片集成DFB+MZM阵列的8通道InP发射PIC(8×200G)，85°C下106 GBd PAM4，TDECQ 1.27 dB |
| W.01.02.3 | 口头 | 器件 | 224G | 110 GHz Bandwidth Flip-Chip Bonded EML for High-Speed IM-DD Applications | AlN子载体倒装焊EML，3-dB带宽110 GHz，113 GBd PAM4 TDECQ 1.9 dB |
| W.02.01.22 | 海报 | 器件 | — | Ultra-high Linearity Silicon Dual-microring Modulator with High Extinction Ratio and High Bandwidth Based on DC Kerr Effect | 基于DC Kerr效应的硅双微环调制器，带宽58 GHz、SFDR 107 dB·Hz^2/3 |
| W.02.01.39 | 海报 | 芯片 | 448G | An AI-accelerated Silicon Slow-light Modulator Chip for 400 Gbps PAM-4 with a Total Data Capacity of 3.2 Tbps | AI加速设计的硅慢光调制器芯片，标准硅光平台首次单波400 Gb/s PAM-4，总容量3.2 Tb/s、密度1.6 Tb/s/mm² |
| W.02.01.50 | 海报 | 芯片 | 224G | First Demonstration of MRM on Low-loss SiN-SOI Platform for High-density and Low-power Optical Interconnection | 首个低损SiN-SOI平台上的微环调制器发射机，224 Gb/s，面向高密度低功耗互连 |
| W.04.07.5 | 口头 | 器件 | 448G | O-Band Plasmonic MZM enabling Single Carrier net 400 Gbit/s IM/DD over 1 km Fiber | O波段等离子体MZM实现160 GBd PAM-8单载波净>400 Gb/s IM/DD(1 km)，最高256 GBd |

## 光DSP

16 篇 · IM-DD 均衡、MLSE/FEC、时钟恢复、光域处理

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M.02.07.3 | 特邀 | 算法 | — | Trends in Digital Signal Processing for IM-DD and Coherent Short-Reach and Optical Access Solutions | 特邀：面向IM-DD与相干短距/接入的DSP发展趋势综述 |
| M.03.03.4 | 口头 | 算法 | — | Integrated recurrent optical spectral slicer for equalization of 100-km C-band IM/DD transmission | 硅光循环光谱切片器做光域预处理，32 GBd PAM-4 C波段IM/DD传输100 km低于FEC门限 |
| Tu.01.04.5 | 口头 | 算法 | — | Recurrent Optical Spectrum Slicers as multi-λ processors for WDM optical equalization of IM/DD channels | 可编程光子学循环光谱切片器作多波长光处理器，75 km C波段同时均衡3路64 Gb/s PAM-4 |
| Tu.03.06.3 | 口头 | 算法 | — | Chromatic Dispersion-Tolerant Digital Clock Recovery for Intensity Modulation and Direct Detection Systems | IM/DD系统抗色散盲数字时钟恢复算法，34 GBd PAM4验证，适用NRZ/RRC/FTN |
| Tu.03.06.5 | 口头 | 芯片 | — | Real-time Demonstration of FPGA-based Advanced Equalizer with ZF-NL-RSSE for Data Center Interconnects | FPGA实时并行ZF-NL-RSSE均衡器，80 Gb/s PAM4，较VDFE/NL-MLSE更优且复杂度降85% |
| W.01.04.4 | 口头 | 算法 | 224G | Turbo Equalization for High-Speed PAM4 Bandwidth-limited IM/DD Transmission System | BCJR检测+2D-SPC译码的Turbo均衡，用于112 GBd PAM4带宽受限IM/DD，优于标准扩展汉明码 |
| W.02.01.55 | 海报 | 算法 | 448G | Simple-Soft-Output MLSE Based on Bayesian Updating and Performance of Turbo Product Codes in High-Baudrate PAM4 Optical Transmission | 基于贝叶斯更新的简化软输出MLSE（含回溯可靠度），200 GBd PAM4下配合SD-FEC/TPC |
| W.02.01.56 | 海报 | 算法 | — | A New 5-bit/2D-symbol Modulation Format for Relative Intensity Noise-dominated IM-DD Systems | 面向RIN主导IM-DD系统的新型5 bit/2D符号调制格式(基于PAM-6)，SNR提升0.94 dB |
| W.02.01.60 | 海报 | 算法 | — | Encoding Optimization for Low-Complexity Spiking Neural Network Equalizers in IM/DD Systems | 强化学习优化SNN神经编码参数，降低IM/DD均衡器计算量与网络规模 |
| W.02.01.67 | 海报 | 算法 | — | Multi-layer Semantic-aware Loading for Short-reach Goal-oriented Optical Communication Systems | 多层语义感知加载用于短距目标导向光通信，硅微环40 Gb/s 20 km图像/文本重建保真度提升43%/32% |
| W.02.01.94 | 海报 | 算法 | — | Joint Localization and Monitoring of Multipath Interference in DMT Systems Using LFM Pilot | LFM导频联合实现DMT系统多径干扰(MPI)定位(3.5 m精度)、监测与帧同步 |
| W.02.01.118 | 海报 | 光系统 | — | DMT vs PAM: an Experimental Comparison over VCSEL-MMF Links for Intra-Datacenter Connections | VCSEL-MMF链路>100 Gb/s下DMT与PAM4实验对比，DMT更适应频率选择信道 |
| W.02.01.128 | 海报 | 算法 | 448G | Traceback-Assisted Simplified Soft-Output MLSE for 320 Gb/s PAM4 Transmissions | 回溯辅助简化软输出MLSE，320 Gb/s PAM4复杂度降61.5%，NGMI差仅0.03 |
| W.04.06.1 | 教程 | 器件 | — | Ultra-Broadband Photonic-Electronic Signal Processing Using Optical Frequency Combs | 教程：基于光频梳的超宽带光电信号处理——光任意波形生成/测量(OAWG/OAWM)与光电DAC/ADC |
| W.04.07.3 | 口头 | 算法 | 224G | Adaptive Removal of Multipath Interference in Short Reach 112 GBd PAM-4 IM/DD Systems | 跨激光相干区间研究多径干扰对224 Gb/s PAM-4的代价，自适应去除强度波动使MPI容限提升8 dB |
| W.04.07.4 | 口头 | 算法 | 448G | Net 400-Gb/s/lane O-band IM-DD Transmission Using 182-GBd PAM-6 with KP4+SFEC over 20-km SSMF | O波段182 GBd PAM-6+KP4/SFEC级联，20 km实现净400 Gb/s/lane，非线性MLSE，FEC时延低于SD-FEC |

## 电SerDes及连接器

2 篇 · SerDes、DAC/ADC、驱动/TIA、LPO/LRO、电通道

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Tu.03.06.1 | 口头 | 光系统 | 448G | 651-Gb/s Net Bitrate IMDD Transmission Using Electrical Bandwidth Multiplexing and Demultiplexing Techniques Based on Ultra-broadband InP-DHBT Mixers | InP-DHBT 150 GHz混频器电域带宽复用/解复用，248 GBd PS-PAM12，单波净651 Gb/s@11 km（纪录） |
| Tu.03.06.2 | 口头 | 算法 | — | Viterbi-Free Digital Resolution Enhancer for Data Centres IM/DD Interconnection with Low-Resolution DAC | 低分辨率DAC的免Viterbi数字分辨率增强器，复杂度降低93.83%，代价<0.2 dB |

## OCS

5 篇 · 光电路交换、WSS/AWGR 交换、AI 集群光交换网络

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Tu.03.07.4 | 口头 | 网络 | — | Wavefront-Shaping Enabled Scalable Optical Circuit Switch | 基于波前整形/分布式光调制的可扩展OCS，CMOS兼容、低电压、无阻塞，面向AI训练 |
| Tu.03.07.5 | 口头 | 网络 | — | Demonstration of Nanoseconds Reconfigurable All-optical Switching Network for Distributed Deep Learning | AWGR+REC-DFB激光器阵列的纳秒全光交换网络加速分布式深度学习，带宽利用率为MEMS方案的1.5–21.5倍 |
| W.02.01.116 | 海报 | 网络 | — | Two-dimensional photonic-switched high-speed interconnects for AI-driven data centre networks | 硅4×4×8λ空间-波长选择光开关实现二维光交换互连，支持InfiniBand 100 Gb/s，面向AI数据中心 |
| W.02.01.117 | 海报 | 算法 | — | Transmitter-Aware Fast FFE Coefficients Distribution for PAM4 Links in Sub-Microsecond Optical Switching Networks | OCS数据中心网络中发射机感知快速FFE系数分发，50 GBd PAM4收敛<4.5 ns，省电46% |
| W.03.03.2 | 口头 | 器件 | — | Four-state Optical Switches Fabricated by Patterned Integrations of Magneto-optical Materials | 图形化集成Ce:YIG/YIG磁光材料的四态非互易光开关（前/后向独立可控） |

## 光源

22 篇 · 激光器、光梳、外置光源

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th.01.02.2 | 口头 | 芯片 | 224G | Heterogeneously Integrated III-V/Si DFB Laser Arrays for Dense Wavelength Division Multiplexing | O波段III-V/Si异质集成DFB激光器阵列（100/200 GHz间隔），50°C下每端>20 mW |
| Th.01.03.3 | 口头 | 芯片 | — | A photonic integrated Erbium DBR laser via scalable manufacturing | 晶圆级制造的氮化硅上掺铒DBR激光器，光纤耦合输出2.05 mW、线宽130 Hz |
| Tu.04.07.1 | 口头 | 光系统 | 224G | 8×225 Gbit/s PAM-8 Transmission Employing DFB Laser Array Source and Quantum-Dot SOA-PIN for Intra DCIs | 200 GHz间隔DFB阵列+量子点SOA-PIN接收，8×225 Gb/s PAM-8数据中心内1 km传输 |
| W.01.02.1 | 口头 | 器件 | 224G | High-speed 200 Gbps 1060 nm Single-Mode Coupled-Cavity VCSEL Enabling 30 m OM4 Multimode Fiber Links | 1060 nm单模金属孔径耦合腔VCSEL直调200 Gb/s PAM4，功耗90 fJ/bit，OM4多模光纤30 m |
| W.01.02.4 | 口头 | 器件 | 448G | 500-Meter Multimode Fiber Transmission with 106Gb/s 850nm Single-Mode VCSELs | 4×106 Gb/s 850 nm单模VCSEL的400G QSFP112模块在OM4上无误码传输500 m，为400GBASE-SR4的5倍 |
| W.01.03.3 | 口头 | 芯片 | 224G | 60 Gbaud NRZ Transmission with 0.94 pJ/b Direct-Drive Optical Transmitter Using SM 1060 nm VCSEL Over 5 km SMF | 单模1060 nm VCSEL直驱60 GBd NRZ 5 km SMF，发射机0.94 pJ/b，FEC后速率距离积纪录283.5 Gb/s·km |
| W.02.01.12 | 海报 | 器件 | — | Monolithically Integrated O-band Quantum Dot DFB Laser with a SOA Section | 单片集成SOA段的O波段GaAs量子点DFB激光器，输出>430 mW，25–105°C工作 |
| W.02.01.20 | 海报 | 器件 | — | A Ultra-Stable Broadband Novel Comb Laser with Tunable Free Spectral Range and Spectra | 量子行走光梳激光器，14 nm带宽、墙插效率6%、RF线宽1 Hz，64 GBd QPSK验证 |
| W.02.01.21 | 海报 | 器件 | — | Semiconductor Laser with Mode-Locking and Single-Longitudinal Bifunctional Operation | 1550 nm AlGaInAs激光器兼具17.7 GHz锁模脉冲与单纵模CW双功能 |
| W.02.01.24 | 海报 | 器件 | — | High-Speed Back Emitting VCSEL with HCG Meta Lens | 集成高对比光栅超透镜的940 nm背发射VCSEL，发散角<6°，25 Gb/s OM4 100 m |
| W.02.01.37 | 海报 | 芯片 | — | Thermally Accessible Low-Repetition-Rate Single Soliton Combs in Mode-Coupling-Engineered Microresonators | 模式耦合工程氮化硅跑道微腔，可热调谐访问30 GHz单孤子微梳 |
| W.02.01.41 | 海报 | 芯片 | — | Monolithic Ring Laser for Optical Frequency Comb Generation | 紧凑InP环形激光器腔内相位调制生成19.12 GHz光频梳，127条梳线、2.33 THz |
| W.02.01.45 | 海报 | 器件 | — | Breaking the Bandwidth-Efficiency Trade-off of Soliton Micro-combs via Strong Mode Coupling | 耦合模泵浦突破孤子微梳带宽-效率折中，倍频程单孤子梳泵浦转换效率近50% |
| W.02.01.48 | 海报 | 器件 | — | O-Band Self-Injection Locked Soliton Comb | DFB自注入锁定氮化硅微环的O波段孤子光梳，带宽234 nm(40.6 THz)，可控完美孤子晶体 |
| W.02.01.89 | 海报 | 光系统 | 448G | Polarization Agnostic Frequency-Comb WDM Transmission Enabling Net 800 Gbps OOK and 1.6 Tbps PAM4 | 偏振无关光梳WDM：11波长SiP发射机，净825 Gb/s(OOK)/1.69 Tb/s(PAM4) |
| W.02.01.112 | 海报 | 器件 | 224G | 200Gbps PAM4 Transmission over 150-m OM5 Fiber Using A Multimode 940-nm VCSEL | 首次用多模940 nm VCSEL在150 m OM5光纤上实现200 Gb/s PAM4 |
| W.02.01.130 | 海报 | 器件 | 224G | 850 nm VCSELs Exceeding 40 GHz Bandwidth Enable 200 Gbps Transmission over 100 m Multimode Fiber Link | 带宽>40 GHz的850 nm VCSEL集成收发机，100 m多模光纤200 Gb/s PAM4/240 Gb/s PAM8 |
| W.02.01.132 | 海报 | 器件 | 448G | 112.5 Gbps PAM4 and 150 Gbps PAM8 Signals for 3.2 Tbps DCI Utilising Off-the-Shelf High Power Fabry-Pérot Laser | 现成高功率FP激光器实现112.5G PAM4/150G PAM8（1/5 km），0.2125 pJ/bit，支撑3.2T DC链路 |
| W.03.02.3 | 口头 | 芯片 | — | Ultrafast Tunable Photonic Integrated Pockels Extended-DBR Laser | InP增益芯片+晶圆级LNOI电光扩展布拉格反射器的超快可调Pockels激光器，10 GHz调谐、>10 mW、kHz线宽 |
| W.03.02.4 | 口头 | 芯片 | — | Micro-transfer Printed Widely Tunable Membrane Laser on a SiN Platform | 微转印InP薄膜SOA于SiN平台的O波段宽调谐窄线宽激光器，调谐34 nm、洛伦兹线宽3.4 kHz |
| W.03.02.5 | 口头 | 器件 | — | Single Soliton Comb Generation in SiC Microresonators via Thermal Compensation using Obliquely Polarized Pumping | 斜偏振泵浦热补偿，在108 GHz FSR碳化硅微腔中稳定产生宽带单孤子微梳 |
| W.03.02.6 | 口头 | 器件 | — | Broadband Microcomb Sources for Ultra-Dense Optical Data Transmission | 考虑损耗-色散关系的工艺感知设计，30 GHz孤子梳可用梳线>300条，支撑超密集光收发 |

## 探测器与接收

14 篇 · Ge/InP 光电探测器、APD、接收机

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th.01.03.5 | 口头 | 芯片 | — | A Si Photonic WDM Receiver with Micro-Ring Resonator Crosstalk Cancellation | 带片上模拟串扰消除的硅光微环WDM接收机，4λ×25 Gb/s，通道间隔仅250 pm |
| Tu.01.02.1 | 口头 | 芯片 | 224G | Broadband 205-GHz Vertical-Illumination Photodiode Enabled by Interference-based Absorption and Field Engineering | 干涉增强吸收+场工程的垂直入射InGaAs/InP光电二极管，带宽205 GHz、响应度0.51 A/W |
| Tu.01.02.2 | 口头 | 器件 | — | 70 GHz, 2 A/W, Waveguide-Coupled Germanium-in-Silicon Avalanche Photodiode | 波导耦合Ge-in-Si雪崩光电二极管，O波段2 A/W时带宽70 GHz，暗电流亚µA |
| Tu.01.02.3 | 口头 | 器件 | — | 150-GHz Bandwidth, -30 dB CMRR Balanced Photodetector for High-Baud Rate PSK Signal Detection | UTC结构150 GHz平衡光电探测器，CMRR<−30 dB，面向高波特率PSK检测 |
| Tu.01.02.4 | 口头 | 器件 | — | Monolithically integrated 100 GHz Ge photodetectors with high responsivity of 0.96 A/W across C+L band | 应力工程单片集成Ge光电探测器，C+L全覆盖，100 GHz带宽、0.96 A/W、暗电流17 nA |
| Tu.03.02.3 | 口头 | 芯片 | 448G | Integrated Eight-Channel WDM Receiver utilizing Plasmonic Graphene Photodetectors enabling Line Rates >800 Gbit/s | 等离子体石墨烯光电探测器与硅光AWG共集成的8通道WDM接收机，总线速率816 Gb/s |
| Tu.03.06.4 | 口头 | 光系统 | 448G | Single Photodiode Detection of 661-Gb/s Signal via Optical Band Multiplexing for High-Speed Optical Interconnects | 光频带复用突破DAC带宽限制，单PD检测661.5 Gb/s线速率(净527.5 Gb/s)@250 m |
| Tu.04.03.1 | 口头 | 芯片 | — | DWDM Link with Fully Integrated Silicon Photonic Transmitter and Passive Polarization Diversity Receiver | 全集成硅光DWDM发射机+无源偏振分集接收机，4λ×32 Gb/s，偏振扰动下稳定 |
| W.02.01.11 | 海报 | 芯片 | 224G | Silicon Photonic CROW Filter for Integrated Carrier-extracted Self-coherent Receiver with Signal Guard Band Optimization | 硅光CROW窄带滤波器(4.62 GHz)用于片上载波提取自相干接收，50 km 180 Gb/s |
| W.02.01.80 | 海报 | 光系统 | 224G | 255-Gb/s C-Band IM-DD over 75 km SSMF Based on Flexible Dispersion-Diverse Receiver with Low Dispersion Path | 含低色散直检支路的灵活色散分集接收机，C波段75 km SSMF实现255 Gb/s IM-DD |
| W.02.01.124 | 海报 | 光系统 | 448G | 400 Gbps/λ Transmission Based on Linear Hybrid Receiver for Intra-Datacenter-Interconnects | 线性混合接收机（直检+相干结合），电带宽减半，单波400 Gb/s C波段500 m |
| W.04.02.4 | 口头 | 芯片 | 224G | InP-Based Polarization Independent LAN WDM Photodetector PIC | InP基偏振无关LAN-WDM AWG解复用+光电探测器PIC，串扰<−30 dB，PD带宽62 GHz（100 GBd PAM4） |
| W.04.02.5 | 口头 | 器件 | — | Comparative Bandwidth Response of GaInAs and GaInAsSb Uni-Traveling Carrier Photodiodes (UTC-PDs) | 首次并列比较GaInAs与GaInAsSb单行载流子光电二极管(UTC-PD)带宽响应 |
| W.04.07.2 | 口头 | 芯片 | 448G | Silicon Photonic Integrated Carrier-Extracted Self-Coherent Detection Receiver based on a second-order CROW filter for Short-Reach Interconnects | 首个基于二阶CROW滤波器的硅光集成载波提取自相干接收机，50 km 62 GBd PCS-64QAM 303.8 Gb/s |

## 集成平台与无源器件

18 篇 · 硅光/SiN/异质集成平台、耦合器、滤波器、复用器

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M.02.03.1 | 教程 | 芯片 | — | Heterogeneous integration for silicon photonics based on micro-transfer printing | 教程：微转印(micro-transfer printing)实现硅光异质集成——GaAs/InP器件、LiNbO3调制器与电芯片集成 |
| Th.02.04.3 | 口头 | 芯片 | 448G | Enabling 448-Gbps-per-Wavelength Fiber Communications with Integrated Silicon Photonic Transceiver and Processor | 硅光收发机+可重构光子处理器复用4个偏振/模式通道，实现448 Gb/s/λ多维光纤通信 |
| Th.03.01.3 | PDP | 芯片 | — | Scalable On-Chip Post-Fabrication Trimming of Silicon Photonic Passive Devices | 通用无损非易失的硅光片上后制程修调方法，用于MZI开关与微环谐振 |
| Tu.03.03.1 | 口头 | 芯片 | — | InP Temperature Sensor with Si-CMOS Interface for Photonic Integrated Circuits | InP PIC二极管与Si-CMOS接口的数字输出温度传感器，分辨率22 mK |
| Tu.04.02.1 | 特邀 | 芯片 | — | Photonic Integrated Circuits using Perovskites | 特邀：钙钛矿材料光子集成电路——单片集成激光器/LED/探测器 |
| Tu.04.02.2 | 口头 | 器件 | — | An Ultracompact Low-loss Multilevel Nonvolatile Phase Shifter with Rhomboidal Segments of Embedded Sb2Se3 | 嵌入菱形分段Sb2Se3的超紧凑低损多级非易失相移器，0.37π/µm，15个相位级 |
| Tu.04.02.3 | 口头 | 芯片 | — | Fabrication-tolerant Silicon Four-mode (De)Multiplexer With Mode-evolution-based Devices at 2.1 µm Wavelength | 基于模式演化器件的工艺容差硅四模(解)复用器(2.1 µm波段)，宽度偏差±20 nm容忍 |
| Tu.04.02.5 | 口头 | 器件 | — | Phase-Error-Correctable 4×4 Programmable Photonic Integrated Circuit Enabled by Dual-Functional Si PIN Waveguides as Phase Shifter and Transparent Power Monitor | Si PIN波导兼作相移器与透明在线功率监测器，实现可纠错4×4可编程PIC |
| W.02.01.19 | 海报 | 器件 | — | Broadband Athermal Silicon Nitride Microring Resonators with Improved Stability | Si3N4-TiO2混合无热微环，1510–1590 nm温漂<0.6 pm/K，Q 5.6×10⁵ |
| W.02.01.28 | 海报 | 芯片 | — | Ultrasmall Mode Exchangers based on Mosaic Structure Designed by Gradient Direct Binary Search Method | 梯度直接二分搜索设计的马赛克结构超小三模交换器，尺寸仅3×4 µm² |
| W.02.01.30 | 海报 | 芯片 | — | Broadband and High Efficiency Difference Frequency Generation in a Nanophotonic Lithium Niobate Waveguide | 自适应极化纳米铌酸锂波导宽带高效差频产生，转换效率31.73% |
| W.02.01.31 | 海报 | 芯片 | — | Enhancing Non-Volatile and Reversible Phase Shift in Si-Rich SiN Waveguide | 富硅SiN波导经UV照射+加热实现0.534π非易失可逆相移 |
| W.02.01.33 | 海报 | 芯片 | — | Highly Efficient All-Optical Control of Optomechanical Photonic Crystal Nanobeam Cavities via the Mechanical Kerr Effect | 机械Kerr效应全光调控光力光子晶体纳米梁腔，1.85 mW移动6.84 nm，调谐效率483 GHz/mW（纪录） |
| W.02.01.34 | 海报 | 芯片 | — | A Fully Reconfigurable Integrated CWDM (de)multiplexer with a 250nm Operational Bandwidth | 全可重构级联MZI型CWDM解复用器，首次覆盖1400–1650 nm(250 nm)工作带宽 |
| W.02.01.43 | 海报 | 芯片 | — | Ultra-high-capacity (288 channel, 30 Tbit/s) diverse space-division multiplexing (MCF, FMF, OAM, SMF) fiber-chip-fiber optical data transmission and signal processing system using 2D/3D heterogeneous integrated photonics chips | 2D/3D异质集成光子芯片实现MCF/FMF/OAM/SMF多样SDM光纤-芯片-光纤传输，288通道30 Tb/s（纪录） |
| W.03.03.1 | 口头 | 芯片 | — | A New Topology for Programmable Photonics with Large FSR Based on Low-Power Silicon Photonic MEMS | 基于低功耗硅光MEMS的大FSR可编程光子新拓扑，FSR较六边形热光方案提升30倍 |
| W.03.03.4 | 口头 | 芯片 | — | Ultralow-Loss Silicon Optical Tunable Delay Lines Using Ridge Waveguides | 脊形波导螺旋的超低损6-bit硅可调光延迟线，630 ps延迟、波导损耗0.13 dB/cm |
| W.04.02.3 | 口头 | 器件 | — | Inverse design of silicon nitride waveguide bend | 参数化逆向设计氮化硅波导弯曲，较部分欧拉弯半径更小损耗更低，代工厂验证 |

## 链路与系统

2 篇 · 短距链路与系统级实验

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Tu.03.07.1 | 特邀 | 光系统 | 448G | The Role of Statistical Fiber Dispersion in Future Intra-Data-Center and Optical Access Networks | 特邀：统计色散模型（已标准化）放宽800G-LR4/1.6T-LR8指标，并研究1.6T-LR4(400G/lane)与200G-PON |
| W.02.01.90 | 海报 | 光系统 | — | Impact of Non-Uniform Fibre’s Zero-Dispersion Wavelength on Four-Wave Mixing in 10-km IMDD LWDM Systems | 光纤零色散波长沿线非均匀(0.04–0.12 nm/km)使800G-LR4中FWM临界范围扩大3.8倍 |
