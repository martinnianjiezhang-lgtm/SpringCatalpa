---
title: "OFC2026 Scale Out 论文索引"
tags:
  - OFC2026
  - 论文索引
---

OFC 2026 中归入 **Scale Out**（224G/448G IM-DD、光源、调制器、探测器、OCS）的论文 **157** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）和代际。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2026 OFC/index|2026年 OFC 论文专题洞察]]

> [!summary] 关键结论
> 400G/lane 进入多平台 PDP 竞速：硅 MZM〔Th4A.4〕、BTO 1.6T DR4〔Th4B.3〕、膜 EA-DFB 448G〔Th4A.1〕、TFLT 768 Gb/s〔Th4A.2〕、TFLN TOSA 420G〔W4J.4〕、差分 EML〔Tu3J.6〕并存，尚无胜者；1.6T 2×FR4 单片硅光满足 802.3dj〔Th4A.7〕。OCS 走向可用：4096×4096 单层 819.2 Tb/s〔M3F.3〕，训练重构快 37.5%〔M3F.5〕，推理需 <700 ns〔W2A.28〕；百万级光模块现网故障数据出现〔Th3B.2〕。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#调制器\|调制器]] | 50 | Si MZM/MRM、TFLN/TFLT、BTO、EML/EAM、等离子体等 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#光DSP\|光DSP]] | 22 | IM-DD 均衡、MLSE/FEC、时钟恢复、光域处理 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#电SerDes及连接器\|电SerDes及连接器]] | 5 | SerDes、DAC/ADC、驱动/TIA、LPO/LRO、电通道 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#OCS\|OCS]] | 15 | 光电路交换、WSS/AWGR 交换、AI 集群光交换网络 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#光源\|光源]] | 15 | 激光器、光梳、外置光源 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#探测器与接收\|探测器与接收]] | 12 | Ge/InP 光电探测器、APD、接收机 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#集成平台与无源器件\|集成平台与无源器件]] | 33 | 硅光/SiN/异质集成平台、耦合器、滤波器、复用器 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#链路与系统\|链路与系统]] | 5 | 短距链路与系统级实验 |

**二级专题 × 代际**

| 二级专题 | 224G | 448G | — |
|---|---|---|---|
| 调制器 | 16 | 22 | 12 |
| 光DSP | 4 | 3 | 15 |
| 电SerDes及连接器 | 2 | 1 | 2 |
| OCS | – | 1 | 14 |
| 光源 | 4 | 1 | 10 |
| 探测器与接收 | 3 | 3 | 6 |
| 集成平台与无源器件 | 2 | – | 31 |
| 链路与系统 | – | 1 | 4 |

## 调制器

50 篇 · Si MZM/MRM、TFLN/TFLT、BTO、EML/EAM、等离子体等

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M2A.1 | 海报 | 器件 | 224G | A 256 Gb/s Silicon Euler Microring Modulator with 3 THz FSR and >67 GHz Bandwidth | O波段硅欧拉微环调制器，FSR 3 THz、带宽>67 GHz，电感峰化，256 Gb/s PAM4 |
| M2A.2 | 海报 | 器件 | 448G | Ultra-High Bandwidth Silicon Microring Modulator with T-Coil Inductive Peaking for >400 Gbps Transmission | T-Coil电感峰化硅微环调制器，1-dB电光带宽>110 GHz，1 Vpp驱动416 Gb/s PAM4 |
| M2A.3 | 海报 | 器件 | 224G | An O-band Silicon Micro Ring Modulator for 200G/ Applications with 1.6THz FSR | 面向200G/λ的O波段硅微环调制器，FSR 1.6 THz，2/3 Vpp下带宽55/70 GHz |
| M2A.5 | 海报 | 器件 | 224G | Low-Voltage, Complex-DSP-Free 200G PAM4 / 140G OOK Operation of Si Photonic Crystal Slow-Light Modulator with Built-in EO Equalizer | 内置电光均衡的硅光子晶体慢光MZM带宽80 GHz，免DSP 112G OOK/180G PAM4，轻DSP达200G |
| M2A.6 | 海报 | 芯片 | 448G | A Compact Mach-Zehnder Modulator in 300 mm Silicon Photonic Platform towards 400Gbps/lane Transmission | 300 mm硅光平台500 µm紧凑MZM，1310 nm带宽中值94.7 GHz，面向400G/lane |
| M2A.7 | 海报 | 器件 | 448G | Si Microring Resonator Modulators at >200Gb/s | 特邀：>200 Gb/s全硅微环调制器发展回顾、折中与挑战 |
| M2B.2 | 高分 | 芯片 | 224G | A 280 Gbps Optical Transceiver with Monolithically Integrated 110 GHz Silicon Microring Modulators and 110 GHz Germanium Photodetectors | 300 mm硅光平台单片集成110 GHz硅微环调制器与110 GHz Ge PD，280 Gb/s光链路 |
| M2B.3 | 口头 | 芯片 | 448G | A 336Gb/s/lane 2.47pJ/b Integrated Transmitter with Silicon Photonic TW-MZM and BW-Boost High-Linearity Driver | 硅光TW-MZM+SiGe BiCMOS带宽增强高线性驱动混合集成发射机，336 Gb/s/lane PAM-8，2.47 pJ/b |
| M2B.4 | 口头 | 器件 | 448G | Ferroelectric Nematic Glass-Based Silicon Photonics Modulator for Net 400 Gbps IM/DD Transmission | 铁电向列相玻璃-硅混合调制器，净400 Gb/s IM/DD（纪录），200 GBd PAM6/168 GBd PAM8 |
| M2B.5 | 高分 | 器件 | 448G | O-Band Silicon-Plasmonic Resonant Ring Modulator Demonstrating Net-Rates of 400 Gbps | 首个O波段硅-等离子体谐振环调制器，片上损耗2.2 dB，PAM8净400 Gb/s，温度稳定性更好 |
| M2B.6 | 特邀 | 光系统 | 448G | Scaling IM/DD Interconnects to 400 Gb/s per Lane: Component and System-Level Tradeoffs | 特邀：IM/DD扩展到400 Gb/s/lane的器件与系统权衡（调制器/PD/放大器/光纤/格式） |
| M3D.4 | 特邀 | 器件 | 224G | Functional Metasurface Devices for High-Speed Communication and Computing | 特邀：嵌入有机电光材料的Si/InP/等离子体超表面实现>Gb/s调制，超表面+InGaAs薄膜PD面法向接收240 Gb/s 64QAM |
| M4B.4 | 口头 | 芯片 | 224G | A 224-Gb/s Si-Photonic WDM Transmitter with Code-Based Calibration for Simultaneous OMA Locking and RLM Optimization | 四级联微环+共集成驱动的224 Gb/s硅光WDM发射机，片上编码校准同时锁定OMA与优化RLM |
| M4D.4 | 口头 | 芯片 | 224G | Truly-Differential Drive of TFLN TWE-MZM by Linear SiGe Driver in a Codesigned Hybrid Integrated Assembly | SiGe线性驱动与TFLN行波MZM协同设计真差分驱动，VπL=1.1 V·cm，140 GBd PAM-8、1.4 pJ/bit |
| Th1C.4 | 口头 | 芯片 | 224G | 1.6 Tb/s Monolithic InP Transmitter PIC with DFB, MZM, and SOA Arrays | 8通道单片InP PIC集成DFB/≤1.5 V MZM/SOA阵列（1.6 Tb/s），单通道212 Gb/s直接线性驱动，出纤+5 dBm |
| Th1H.2 | 口头 | 器件 | 224G | Silicon-Organic Hybrid (SOH) Racetrack Modulators for 200 Gbit/s PAM4 Signaling with Ultra-low Drive Voltages | 首个硅-有机混合(SOH)跑道型调制器，220 mVpp超低驱动实现200 Gb/s PAM4（纪录低电压） |
| Th1H.3 | 口头 | 芯片 | — | DC-to-GHz Modulators in Ferroelectric Nematic Liquid Crystal-on-Si Platforms | 代工兼容铁电向列液晶-硅平台微型调制器(DC–GHz)，双机制相移免热光加热与电极化 |
| Th1H.4 | 口头 | 器件 | — | High Efficiency and High Speed Electro-Optical Modulator Based on Hybrid Calcium Titanate and Lithium Niobate | 钛酸钙+薄膜铌酸锂混合电光调制器，带宽>110 GHz、插损0.86 dB |
| Th2A.11 | 海报 | 器件 | 224G | A 280 Gbps PAM6 Silicon Photonic Tabbed-Electrode Mach-Zehnder Modulator with Co-Optimized Modulation Efficiency and Electro-Optic Bandwidth | 凸片电极硅MZM协同优化效率与带宽(1-dB带宽66 GHz)，280 Gb/s PAM6 |
| Th2A.12 | 海报 | 器件 | — | 67 GHz graphene electro-absorption modulators on silicon with 80 Gb/s C-band and 40 Gb/s O-band NRZ data rates | 硅上石墨烯电吸收调制器带宽67 GHz，C波段80 Gb/s、O波段40 Gb/s NRZ |
| Th3J.2 | 口头 | 芯片 | — | A Linear MRM-based Coherent Optical Link Architecture with Integrated Closed-loop Carrier Phase Recovery | GF 45 nm硅光中MRM发射机+连续模拟免DSP载波相位恢复的线性相干光链路，面向AI基础设施 |
| Th4A.1 | PDP | 芯片 | 448G | 4-ch × 400-Gbps PAM4 O-band Membrane InGaAlAs EA-DFB Laser Array on a Si Photonics Platform | Si上异质集成4通道O波段薄膜InGaAlAs EA-DFB阵列，0.5 V摆幅每通道400/448 Gb/s PAM4，岸线密度3.2 Tb/s/mm |
| Th4A.2 | PDP | 器件 | — | C-band 110-GHz-Bandwidth Thin-Film Lithium Tantalate Modulator Enabling 768 (536) Gbit/s Line (Net) Data Rates | C波段薄膜钽酸锂(TFLT) MZM，Vπ 1.35 V、带宽>110 GHz，线/净速率768/536 Gb/s（TFLT纪录） |
| Th4A.4 | PDP | 器件 | 448G | 400G/lane PAM4 Modulation Using Silicon Mach-Zehnder Modulators | 硅MZM+商用SiGe驱动实现400G/lane PAM4，证明硅MZM可扩展到400G |
| Th4A.5 | PDP | 芯片 | 224G | Fully Integrated 1064 nm Transmitters with Widely Tunable GaAs Lasers and > 100-GHz Thin-Film LiNbO3 Modulators | 首个全集成1064 nm GaAs-on-TFLN发射机（宽调谐GaAs激光器+>100 GHz TFLN调制器），100G NRZ/160G PAM4 |
| Th4B.3 | PDP | 芯片 | 448G | Barium Titanate Enabling Net 1.6T (4x448 Gbps PAM4) On a Silicon Photonics Platform | 商用硅光平台单片集成薄膜钛酸钡O波段DR4芯片，3 nm SerDes实现净1.6T(4×448G PAM4) |
| Tu2J.3 | 口头 | 器件 | — | Inverse-Designed Etch-Stable Ring Modulators | 逆向设计抗刻蚀深度偏差的环形调制器，晶圆级测得敏感度降低2.5倍 |
| Tu3J.1 | 特邀 | 器件 | — | High-Speed EMLs for AI/ML Applications | 特邀：面向AI/ML的高速EML——窄高台面波导+倒装焊，子组件3-dB带宽110 GHz |
| Tu3J.2 | 口头 | 器件 | 448G | Low Loss Electro-absorption Modulator with Extrapolated Bandwidth of 180 GHz Enabled by Ultra-thin Ge Process | 超薄Ge工艺电吸收调制器，插损1.5 dB、外推带宽180 GHz，120G NRZ/300G PAM-4 |
| Tu3J.3 | 口头 | 芯片 | 448G | High-Bandwidth-Density Uncooled EML Array for up to 770 Gb/s/mm and 11 km Fiber Reach | 集成RF走线、缩小通道间距的紧凑非制冷EML阵列，带宽密度770 Gb/s/mm，11 km |
| Tu3J.4 | 口头 | 器件 | 224G | Differential Drive EML with Tandem Modulator Structure for 200G/Lane and Beyond Applications | 串联调制器结构差分驱动EML，带宽80 GHz，113 GBd PAM4 TDECQ 1.28 dB，面向200G/lane+ |
| Tu3J.5 | 高分 | 器件 | 448G | 360 Gbps PAM4 Differentially Driven EML with 100 GHz 3dB Bandwidth Dual Series-Connected EAMs for Next-Generation 3.2 Tbps Data Center Transceivers | 双串联EAM差分驱动EML，3-dB带宽>100 GHz，360 Gb/s(180 GBd PAM4)，面向3.2T |
| Tu3J.6 | 口头 | 器件 | 448G | 400G per lane Differential Drive Electroabsorption Modulated Lasers (EML) with 99GHz 6-dB EO BW for next generation 3.2T IM-DD Applications | O波段差分驱动EML，6-dB带宽99 GHz(55°C)，320G PAM-4/413G PAM-6睁眼，面向400G/lane 3.2T |
| Tu3J.7 | 口头 | 器件 | 224G | 4 x 226 Gbps PAM4 Transmission Over 2-km SSMF with Differential Drive EA-DFB Lasers Under 1.5-Vppd Low Swing Voltage | 4波长差分驱动EA-DFB，1.5 Vppd低摆幅4×226 Gb/s PAM4传2 km，TDECQ<2.4 dB |
| W1A.1 | 特邀 | 芯片 | 448G | Integrated Electro-Optic Frequency-Domain Equalizer for Ultra-Broadband Optical Modulator | 特邀：集成电光频域均衡器的薄膜铌酸锂调制器，突破效率-带宽折中，带宽>100 GHz、支持>200 GBd |
| W1A.2 | 口头 | 芯片 | 224G | A 60 GHz EO Bandwidth Mach-Zehnder Modulator for 200G/λ O-band Datacom in 300-mm Monolithic CMOS Silicon Photonics Foundry | 300 mm CMOS硅光代工推挽MZM，EO带宽60 GHz，200G PAM-4 TDECQ 2.9 dB，面向200G/λ O波段 |
| W1A.3 | 口头 | 芯片 | — | Thin-Film Lithium Niobate Modulators with 110 GHz Bandwidth and 1.9 V·cm Efficiency on 200-mm Silicon Substrate | 200 mm硅衬底后道CMOS代工TFLN调制器，带宽110 GHz、效率1.9 V·cm、O波段损耗<0.5 dB/cm |
| W1A.4 | 口头 | 器件 | — | Sub-V-driven 110-GHz O-band Electro-optic Modulator on Thin-film Litihum Tantalate | 局部去除硅衬底的薄膜钽酸锂O波段MZM，Vπ 1 V(10 Hz–10 kHz)，带宽>110 GHz |
| W1A.5 | 口头 | 器件 | 448G | Lithium-Tantalate-on-Fused Silica Mach-Zehnder Modulators | 4英寸晶圆级熔石英上钽酸锂MZM，带宽67 GHz，PAM8净437 Gb/s |
| W1A.6 | 口头 | 芯片 | — | High-Efficiency Ring-Assisted Mach-Zehnder Modulator on a Lithium Tantalate-on-Silicon Nitride Platform | SiN/钽酸锂异质集成环辅助MZM，效率1.36 V·cm、插损1.75 dB、带宽>50 GHz |
| W1A.7 | 口头 | 芯片 | 224G | A 1.6 Tbit/s WDM Integrated Photonic IMDD Transmitter on Thin-Film Lithium Tantalate | 单片薄膜钽酸锂平台全集成WDM IM-DD发射机，PAM-4/PAM-8总净速率1.6 Tb/s |
| W1D.2 | 口头 | 芯片 | — | Modulation Crosstalk Cancellation for Ultra-Dense WDM Silicon Photonic MRM Transmitters | 定制CMOS IC电域复制并减去干扰数据，消除超密WDM级联硅微环调制器串扰，4×25G PAM-4@340 pm间隔 |
| W2A.5 | 海报 | 器件 | — | Ultracompact High-Speed Surface-Reflective Modulator with Organic Electro-Optic Thin Film | 有机电光薄膜超紧凑偏振无关面反射调制器（30 µm FP腔），0.30 nm/V、带宽40 GHz |
| W2A.12 | 海报 | 芯片 | 224G | A 4 Tbps 16-Channel DWDM Transmitter Using Extended-Depletion Silicon Photonic Microdisk Modulator Array | 扩展耗尽硅光微盘调制器阵列(带宽65 GHz)，16×256 Gb/s PAM4 DWDM发射机，单纤4 Tb/s |
| W2A.14 | 海报 | 器件 | 448G | High-Bandwidth Serpentine Segmented Silicon Photonic Mach-Zehnder Modulator for 192 Gbaud Transmission | 蛇形分段硅MZM，0 V偏置1-dB带宽>67 GHz、效率1.14 V·cm，支持192 GBd |
| W2A.42 | 海报 | 算法 | 448G | 300-Gb/s/λ PAM4 IM/DD Link Enabled by GeSi Electro-absorption Modulator and BU-GRU Equalization | >67 GHz GeSi电吸收调制器+BU-GRU均衡，300 Gb/s/λ净速率PAM4(100 m) |
| W3E.4 | 口头 | 芯片 | 448G | A 6.4 Tbps Optical Transmitter with Low-loss and High-Uniformity Inverse-Designed Multiplexer on a 300-mm CMOS Platform | 300 mm CMOS平台400G微环调制器+逆向设计多维复用器的6.4 Tb/s发射机，损耗<1.5 dB、均匀性σ<0.15 dB |
| W3E.5 | 口头 | 器件 | 448G | Toward 400 G/Lane Silicon Differential-Drive Mach-Zehnder Modulator with > 80 GHz Bandwidth for Optical Interconnects | 差分驱动硅MZM 3-dB带宽81.8 GHz，100 GBd PAM-8，迈向400G/lane |
| W3E.6 | 口头 | 器件 | 448G | 180 GBaud PAM4 Driver-Modulator Engine for IM/DD Transmissions in the O-Band | 76 GHz InP MZM与224 GBd级线性差分EML驱动共封装引擎，O波段180 GBd PAM4背靠背 |
| W4J.4 | 口头 | 器件 | 448G | A 420 Gb/s/lane O-Band PAM-4 TOSA Based on Thin-Film Lithium Niobate for IM-DD Applications | TFLN O波段TOSA，调制器与驱动协同设计，210 GBd/420 Gb/s PAM-4睁眼 |

## 光DSP

22 篇 · IM-DD 均衡、MLSE/FEC、时钟恢复、光域处理

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M3B.1 | 特邀 | 算法 | 448G | Modulation Formats and Advanced DSP for Next-Generation Data Center Intraconnects | 特邀：下一代数据中心400 Gb/s/lane IM/DD的调制格式与先进DSP可行性分析 |
| M3B.2 | 口头 | 算法 | — | Optics-Inspired Kolmogorov–Arnold Fully-Convolutional Equalizer for High-Speed VCSEL-MMF Optical Interconnects | 光学启发的Kolmogorov-Arnold全卷积均衡器(OIKA-FCN)，用于高速VCSEL-MMF互连 |
| M3B.3 | 口头 | 算法 | 224G | Low-Complexity Circle-Solving and Shift-Augmented Equalizer for 200-Gb/s Skew-Enabled VSB Direct-Detection | 圆求解SSBI提取+移位增强FFE，200 Gb/s偏斜VSB直检80 km，BER降35%或乘法降33% |
| M3B.5 | 口头 | 算法 | — | Mitigation of FWM in High-Speed IM/DD Systems Using DD-LMS Equalizer Aided by Orthogonal Bias Terms | 正交偏置项辅助DD-LMS均衡抑制高速IM/DD中的FWM，112 Gb/s/lane PAM4 WDM灵敏度提升2 dB |
| M3B.6 | 口头 | 光系统 | 448G | 200-Gbaud Single-Wavelength Direct-Detection Transmission over 75 km C-band SSMF Using a PIC-based Recurrent Spectrum Slicer | 硅光循环光谱切片器消除色散功率衰落，C波段200 GBd OOK 75 km、160 GBd PAM-4 50 km直检 |
| M3K.4 | 口头 | 算法 | 448G | Neural-Network-Based Nonlinear Digital Pre-Distortion for Electronically-Multiplexed DACs | 神经网络非线性数字预失真用于电复用DAC，RF SNR提升>1.4 dB，单波IM-DD净速率达600 Gb/s |
| M3K.5 | 口头 | 算法 | — | Neural Network Optimized Spike Encoding for Power-efficient and High-speed Spiking Neural Network Equalization in IM/DD Systems | 神经网络脉冲编码器+SNN均衡器用于IM/DD，较线性均衡增益1.7 dB，低脉冲率适合神经形态硬件 |
| M3K.6 | 口头 | 算法 | — | Circular Reservoir-Computing–Assisted Hybrid Equalizer for Joint Linear/Nonlinear Compensation in 106-Gb/s PAM4 IM/DD Optical Links | 循环储备池计算辅助混合均衡器，106 Gb/s PAM4，98%稀疏度，优于线性与Volterra均衡 |
| Th1B.5 | 口头 | 算法 | 224G | Lite-Equalizer-Aided Baud-Rate Clock and Data Recovery in 256-Gb/s PAM-4 Transmission Systems | Mueller-Müller CDR中单抽头噪声消除器白化噪声，256 Gb/s PAM-4抖动改善8.3 dB、TED增益提升3倍 |
| Th2A.42 | 海报 | 算法 | — | Joint Notch Coding and Nonlinear Equalization for Optical Multipath Interference Suppression in IM-DD Systems | 发端陷波编码+接收PNLF均衡联合抑制IM-DD多径干扰，SIR容限提升3.25/5.23 dB |
| Th2A.45 | 海报 | 算法 | — | Sparse–Quantized Retraining Framework for Complexity-Efficient Volterra Equalizers with Performance Recovery in IM/DD Optical Data-Center Links | 稀疏-量化重训练框架使106 Gb/s PAM4 Volterra均衡器复杂度降>90%且BER接近全精度 |
| Th2A.47 | 海报 | 算法 | — | Non-integer Oversampled and Low-complexity Real-time Timing Recovery for Short-reach Coherent Receivers | 面向FPGA实时的非整数过采样低复杂度定时恢复，用于短距相干接收 |
| W1D.5 | 口头 | 算法 | — | Chirp-Parameter-Independent Zero-Dispersion Wavelength Estimation Method for Penalty-free and Equalizer-free 60-km Transmission of over 100 Gbps IM-DD Signals | 与啁啾参数无关的零色散波长估计方法，实现100G PAM4 60 km无代价免均衡IM-DD传输 |
| W1D.6 | 高分 | 算法 | — | Quaternion Retrieval for Full-field System Identification of Optic Fiber Systems via Direct Detection | 导频辅助四元数恢复，直检实现全场光系统辨识（63.25 GBd双偏振16QAM） |
| W1E.1 | 特邀 | 算法 | — | AI in performance optimization of short reach optical interconnects | 特邀：AI用于短距光互连性能优化，物理辅助AI设计双极PAM直检接收DSP |
| W2A.40 | 海报 | 算法 | — | Density-Aware Clustering-Based Non-Uniform Quantization for Efficient Equalization in a 135-Gb/s IM/DD System using commercial DML | 密度感知聚类非均匀量化用于商用DML IM/DD的Volterra均衡，135 Gb/s PAM-8仅6 bit精度 |
| W2A.45 | 海报 | 算法 | 224G | High-Speed Turbo Equalization for 224 Gb/s PAM4 IM/DD Systems with Standardized FEC | BCJR+标准(128,120)扩展汉明码的Turbo均衡，224 Gb/s PAM4在KP4前FEC门限增益1.35 dB |
| W3B.2 | 口头 | 算法 | — | THP-Based Faster-Than-Nyquist Coherent System with All-Digital Baud-rate Timing Recovery | THP辅助超奈奎斯特短距相干系统，单符号率DSP+全数字波特率定时恢复 |
| W3B.7 | 口头 | 算法 | — | Low-Complexity 2-Order IIR Notch Filter with Adaptive Frequency Tracking for Inter-Channel FWM Mitigation in IMDD-WDM Transmission with 1.6-dB Sensitivity Gain | 自适应频率跟踪二阶IIR陷波器消除IMDD-WDM信道间FWM，112 Gb/s PAM-4灵敏度提升1.6 dB |
| W3F.2 | 口头 | 光系统 | 224G | Wavelength-domain Pairwise Transmission (WD-PT) for CD-tolerant WDM Multilane IM-DD Systems | 成对传输推广到波长域(WD-PT)，C波段WDM多通道IM-DD 110G@80 km、200G@30 km |
| W3J.2 | 口头 | 算法 | — | Advanced Noise Whitening Filter Based on Equalizer Autocorrelation for 122-Gbps PAM-4 IM/DD Transmission with Severe Bandwidth Limitation | 基于均衡器自相关的噪声白化滤波器(EA-NWF)，122 Gb/s PAM-4复杂度降99.2%、灵敏度提升2.8 dB |
| W4J.1 | 口头 | 算法 | — | Improved Multi-Path Interference Detection with Calibrated Variance Difference | 基于调制电平校准方差差的改进多径干扰(MPI)检测，降低噪声与消光比影响 |

## 电SerDes及连接器

5 篇 · SerDes、DAC/ADC、驱动/TIA、LPO/LRO、电通道

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th2A.44 | 海报 | 算法 | 224G | Reinforcement-Learning-Based Electro-Optical Parameter Optimization for 200G Linear Pluggable Optics in Data Center Interconnects | 强化学习自主优化200G LPO电光参数，灵敏度提升3.5 dB，16–22 dB插损下保持>200 Gb/s |
| W2A.43 | 海报 | 光系统 | — | Linear Pluggable Optics Module Adaptation for a 102.4 Tbps Switch with Insertion Loss Exceeding 39 dB | 102.4T交换机LPO模块适配仿真模型与实验，插损>39 dB下BER 1E-9~1E-13 |
| W2A.44 | 海报 | 芯片 | — | A 0.6 pJ/bit Analog Equalizer ASIC for Nonlinearity Compensation in IM/DD Links | 0.6 pJ/bit模拟神经网络均衡ASIC（直接判决）补偿DML高电流非线性，免光放大延长距离 |
| W4J.2 | 口头 | 芯片 | 224G | Adaptive Periodically Time–Variant Background Calibration for Joint Time– and Frequency–Interleaved 160 GSa/s Analog to Digital Converter | 联合时间/频率交织160 GSa/s ADC的周期时变后台校准，100 GBd PAM4 SNR提升2.4 dB |
| W4J.3 | 高分 | 芯片 | 448G | Up to 200 GBd PAM Signal Reception with 33 GHz ADCs Using 256 GSa/s Analog Demultiplexer (ADeMUX) Chip | 256 GSa/s SiGe 1:4模拟解复用(ADeMUX)芯片使33 GHz ADC接收200 GBd PAM-4/176 GBd PAM-8，净464.1 Gb/s（纪录） |

## OCS

15 篇 · 光电路交换、WSS/AWGR 交换、AI 集群光交换网络

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M2D.1 | 口头 | 器件 | — | Waveguide Superlattices with Artificial Gauge Field for High-performance Thermo-Optic Switching | 人工规范场波导超晶格1×8热光开关，损耗1.96 dB、串扰<−20 dB、2.52 mW/π |
| M2D.2 | 口头 | 芯片 | — | Curved Tunable Directional Couplers Empower Ultralow-Crosstalk, Low-Loss Optical Switch Fabrics | 弯曲可调定向耦合器校正MZI功率不平衡，4×4开关矩阵串扰<−50 dB、片上损耗<1.5 dB |
| M2E.5 | 口头 | 芯片 | — | A 4×40 GBaud Femtojoule Kerr All-Optical Switch based on Silicon-Organic Hybrid Nanocavities | 硅-有机混合纳米腔Kerr全光开关，4×40 GBd，每通道开关能量低至52 fJ/bit |
| M3F.2 | 口头 | 器件 | 448G | Experimental Demonstration of O-Band 4×4x8 Wavelength Selective Switch at 100Gbps/ for Data Center Networks | 400 GHz 8通道平顶AWG+SOA阵列的模块化偏振无关O波段4×4×8 WSS，100G PAM4代价0.8 dB |
| M3F.3 | 口头 | 网络 | — | A 4,096×4,096 Strictly Non-Blocking Optical Circuit Switch Delivering 819.2 Tb/s via Space-and-Wavelength Routing | 星形耦合器空间+波长路由的4096×4096严格无阻塞OCS，单层交换819.2 Tb/s |
| M3F.4 | 高分 | 网络 | — | Reconfiguration-Aware Direct-Connect AI Cluster using Spatial-and-Wavelength-Selective Switching | 空间-波长选择开关与Linux网络栈集成的重构感知直连AI集群，6.4 TB传输+4个ResNet-18多租户训练 |
| M3F.5 | 口头 | 网络 | — | Training-Phase-Aware Optical Circuit Switching Reconfiguration for Large Language Model | 感知LLM训练阶段的OCS重构，按阶段切换最优拓扑，通信较静态光网络快37.5% |
| M4F.1 | 高分 | 网络 | — | 1024x1024 All-to-All Interconnect Thin-CLOS-LION system using 64 lambda routing on athermal 64x64 ULCF AWGRs | 无热64×64均匀损耗循环频率AWGR+64波长路由的1024×1024全互连Thin-CLOS-LION系统，损耗7.5 dB |
| M4F.2 | 口头 | 网络 | — | Accelerating LLM Training in Optical AI Clusters with Asynchronously-Invoked Hitless In-Job Partial TPE | LLM训练中在作业内异步无损部分重构OCS，拓扑跟随时变流量矩阵，加速GPT-2训练 |
| M4F.4 | 口头 | 网络 | — | High-speed optical alternate switching between the networks for expert/tensor and data parallelism | 利用AI并行确定性交替通信模式，在专家/张量并行与数据并行网络间高速光切换，开销<2 µs |
| Th2A.30 | 海报 | 芯片 | — | Novel Photonic Integrated Beam Steering Switch for Optical Wireless Data Center Networks | SiN集成光束偏转开关用于光无线数据中心网络，偏转42°、40 Gb/s代价<0.5 dB |
| Th2A.35 | 海报 | 网络 | — | HOCSS: A Hardware-accelerated Optical Circuit Switch Scheduler for low-latency Optimal Ports Matching | HOCSS硬件加速OCS调度器，最优端口匹配时延<1 µs，较CPU快68.8倍 |
| W2A.28 | 海报 | 网络 | — | Performance Thresholds for Optical Circuit Switching in LLM Inference | LLM推理中OCS网络性能门限：无高扇出时需<700 ns重构才能胜过电交换 |
| W2A.31 | 海报 | 网络 | — | OCS-based Double Resource Pooling for Flexible Intra-and Inter-rail Connectivity in AIDC Networks | ocs-DRP：基于OCS双资源池的扁平AIDC网络，灵活rail内/间连接，较rail优化胖树功耗降40% |
| W4H.4 | 口头 | 网络 | — | Auto-allocating OCS Based on Real Time Flow-granularity Controller for LM Training | 实时流粒度控制器自动分配OCS的光电混合网络，AllReduce时间降50.3%、功耗降32.14% |

## 光源

15 篇 · 激光器、光梳、外置光源

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th1A.2 | 口头 | 器件 | 224G | 200G/lane 50-m Multimode VCSEL Link by Low-Material-Dispersion Graded-Index Plastic Optical Fiber | 低材料色散渐变折射率塑料光纤，多模VCSEL 212.5 Gb/s/lane PAM4传50 m |
| Th1A.3 | 口头 | 器件 | 224G | 180 Gb/s PAM-4 Optical Link by Cryogenic VCSEL | 3 K低温VCSEL（带宽>50 GHz@2 mA）实现180 Gb/s PAM-4链路（纪录），目标<50 fJ/bit |
| Th1F.2 | 口头 | 器件 | — | Digital Fiber Interferometry for Measuring Low-Frequency Phase Noise of Single-Frequency Laser Sources | 基于光纤MZI的数字干涉法测量超低噪单频激光0.1 Hz–5 MHz低频相位噪声 |
| Th1F.5 | 口头 | 器件 | — | High-Power Kerr Comb Source for Data Communications | 高功率Kerr光梳源，300/200/100 GHz间隔可配置，多通道32 Gb/s直接调制睁眼，面向WDM光互连 |
| Th1F.6 | 高分 | 芯片 | — | A photonic integrated mode-locked laser based on dispersion-managed mode-locking architecture | 首个自启动光子集成飞秒锁模激光器（色散管理锁模架构），1.2 GHz重频、阈值超低 |
| Th2A.10 | 海报 | 芯片 | — | DFB Laser Stabilization Against On-Chip Parasitic Reflections Using Controlled Feedback from a Silicon Ring Resonator | 硅环相控滤波反馈稳定混合集成DFB，免隔离器，容忍−5 dB片上寄生反射 |
| Th2A.46 | 海报 | 光系统 | 448G | Net 5.8 Tbps IM/DD Transmission over 2 km using 25 Simultaneous 100 GHz Comb Channels and a Single SOA | 首个单SOA+100 GHz量子点梳状激光器25通道O波段IM/DD 2 km，净5.76 Tb/s(PAM-8) |
| Th4A.3 | PDP | 器件 | 224G | High Temperature >35GHz Bandwidth Oxide-Confined VCSELs for 200G-PAM4 Links | 25–80°C带宽>35 GHz的氧化限制VCSEL，200G PAM4，寿命>10年 |
| Tu3C.2 | 高分 | 器件 | — | Ring resonator-based dynamic controller for precise wavelength separation of a DWDM laser source | 基于环形谐振器的控制器连续控制DFB阵列波长间隔，环境变化下保持201±4 GHz |
| W2A.10 | 海报 | 芯片 | — | Reliability and Output Power Improvement of GaAs Nano-Ridge Lasers Integrated on 300 mm Silicon | 300 mm硅上GaAs纳米脊激光器可靠性与功率提升（接触鳍+InGaP钝化），单端>10 mW |
| W2A.15 | 海报 | 芯片 | — | Greater Than 100mW Coupled Power From O-Band Quantum Dot Laser to Silicon Nitride Waveguides Through Micro-Transfer Print Integration | 微转印刻蚀端面O波段量子点FP激光器与低损SiN波导集成，双端耦合>100 mW、每端~4 dB |
| W3E.2 | 口头 | 芯片 | — | DFB laser array based on two-dimensional sampling structure and tilted Bragg grating | 二维采样结构+倾斜布拉格光栅DFB激光器阵列，300 GHz高均匀波长间隔 |
| W4E.3 | 口头 | 器件 | 224G | 200-Gb/s 1060-nm Single-Mode Coupled-Cavity VCSEL Enabling Modal-dispersion Free >50-GHz Bandwidth over 500-m Multimode Fiber | 1060 nm单模耦合腔VCSEL+SMF跳线中心注入，500 m OM4无模色散200 Gb/s，速率×距离100 Gb/s·km（纪录） |
| W4E.4 | 口头 | 器件 | — | High-Performance, Cost-Effective SWIR VCSELs: A New Source for Optical Interconnects | 可量产InP基短波红外VCSEL(3λ腔)，峰值PCE近30%、带宽9 GHz，面向O/C波段光互连 |
| W4E.5 | 口头 | 器件 | — | O-band Membrane Surface-Emitting Laser on a Si Substrate Demonstrating 100-Gbps PAM-4 Operation | Si衬底上O波段薄膜面发射激光器（二阶表面光栅DR激光器），100 Gb/s PAM-4 2 km |

## 探测器与接收

12 篇 · Ge/InP 光电探测器、APD、接收机

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th2A.15 | 海报 | 器件 | 448G | SiGe Photodetector Using a Tapered Ge Design for 400 Gbps Optical Links | CMOS兼容锥形Ge硅锗光电探测器，响应度0.87 A/W，支持400 Gb/s PAM-8 |
| Th3A.5 | 高分 | 芯片 | — | A Monolithic CMOS 28Gb/s PAM-4 Optical Receiver Front-End with Lateral-Enhanced P-Well/N-Well APD for VCSEL-Based Links | 28 nm CMOS单片28 Gb/s PAM-4光接收前端，横向增强PW/NW APD，0.66 pJ/bit，面向VCSEL链路 |
| Th3F.1 | 口头 | 器件 | — | Germanium Photodetectors with >100 GHz Bandwidth and >1.1 A/W Responsivity on 200-mm Silicon Photonics Platform | 200 mm硅光平台Ge凹槽生长+横向PIN，Ge PD带宽>100 GHz、响应度>1.1 A/W、暗电流<25 nA |
| Th3F.2 | 口头 | 器件 | 448G | 360 Gbps Ge-on-Si Avalanche Photodiodes Operating in the Oand C-Band | Ge-on-Si APD（O/C波段带宽70/100 GHz），180 GBd PAM4达360 Gb/s |
| Th3F.3 | 口头 | 器件 | — | A Ge/Si photodiode exceeding 110 GHz with 0.9 A/W, low capacitance and operating at -0.5 V for O and C-band applications | 深嵌入高掺Si的Ge/Si光电二极管，带宽>110 GHz、0.9 A/W、电容≤6 fF、−0.5 V工作 |
| Th3F.4 | 口头 | 器件 | — | 92 GHz Bandwidth and High Power Ge PD with distributed absorption regions and interdigitated electrode | 分布式吸收区+叉指电极紧凑Ge PD，带宽92 GHz(8 mA时69 GHz)、1 A/W@40 mW |
| Th3F.5 | 口头 | 芯片 | 224G | Uniformly Absorbed Waveguide-integrated Germanium Photodetector for High-power and High-speed Receiver | 均匀吸收横向波导耦合Ge-Si PD，4 mA下带宽67 GHz，112G NRZ/224G PAM4 |
| Th3F.6 | 口头 | 芯片 | — | Low-voltage microring-assisted Ge avalanche photodiodes with 56 Gbaud on a 300-mm wafer | 300 mm平台微环辅助Ge APD，−1 V响应度0.82 A/W、增益7.5，56 GBd |
| Th3F.7 | 口头 | 器件 | 224G | 260 Gbit/s PAM-4 Waveguide-Integrated Graphene Photodetector with >110 GHz Bandwidth based on Hybrid Plasmonic Slot Structure | 混合等离子体狭缝波导集成石墨烯光电探测器，带宽>110 GHz，260 Gb/s PAM-4 |
| Tu3C.1 | 高分 | 芯片 | — | Crosstalk-Resilient Wavelength Locking for Si Micro-Ring-Resonator-Based Ultra-Dense WDM Receivers | 抗串扰硅微环超密WDM接收机波长锁定（定制电路抑制相邻环串扰），4λ×28 Gb/s、250 pm间隔 |
| W3E.7 | 高分 | 器件 | 448G | Highly Reliable 210-GHz Vertical-illumination Photodiode with Interference-based Enhanced Absorption in O-band | 倒置p-down结构干涉增强吸收垂直入射InGaAs/InP PD，O波段210 GHz、0.55 A/W，>180 GBd，可靠性高 |
| W3F.5 | 口头 | 算法 | 224G | Adaptive Resonant Wavelength Tracking for High-Q Second-Order MRR in Carrier-Extracted Self-Coherent Detection Systems | 二阶高Q硅微环自适应谐振波长跟踪（全C波段、2 ms收敛、57 mW），载波提取自相干224 Gb/s 50 km |

## 集成平台与无源器件

33 篇 · 硅光/SiN/异质集成平台、耦合器、滤波器、复用器

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M4B.5 | 口头 | 芯片 | — | Highly-Integrated 16-channel Silicon-Photonics Optical Engine Enabling PAM6 Transmission with BER < 1E-9 | 高集成16通道硅光光引擎53 GBd PAM6，总速率>2 Tb/s，首次原始BER<1E-9 |
| Th1D.1 | 口头 | 芯片 | — | Photonics Heterogeneous Integration (PHI) of Thin-Film Lithium Niobate and Hydrogen-Free Silicon Nitride on a 200-mm Silicon Photonics Platform | 200 mm晶圆级异质集成平台(PHI)：TFLN调制器+无氢氮化硅（芯片-晶圆键合），调制效率2.9 V·cm |
| Th1D.2 | 口头 | 芯片 | — | Dense Interconnect Routing of Visible Deuterated Silicon Nitride (SiNx:D – SiOy:D) Photonic Integrated Circuits | 低温(≤300°C)低损氘化SiNx–SiOy平台，450 nm可见光下弯曲半径<5 µm密集布线 |
| Th1D.6 | 口头 | 器件 | — | Bridging ultrahigh-Q integrated microresonators with optical fiber manufacturing | 火焰水解沉积在硅片上制备Ge:SiO2集成谐振腔，紫外到近红外Q>1亿，1064 nm达5.66亿 |
| Th1F.1 | 口头 | 器件 | — | Deep-Ultraviolet to Mid-infrared Supercontinuum Generation in chirped Poled Lithium Tantalate Waveguides | 啁啾极化钽酸锂波导产生深紫外到中红外(<270 nm至>2400 nm)超连续谱 |
| Th2A.1 | 海报 | 芯片 | — | Hybrid Integration of O-band InP SOA array and PLC using PLC/SiN Spot-Size Converter | PLC/SiN模斑转换器与O波段InP U形SOA阵列混合集成，每端面~1.5 dB |
| Th2A.4 | 海报 | 器件 | — | Broadband Dual-Mode Splitter Based on a Slotted-MMI Coupler Using Subwavelength-Grating Structures | 亚波长光栅开槽MMI宽带双模分束器，1500–1640 nm低损 |
| Th2A.5 | 海报 | 芯片 | — | DFM-Aware Characterization of Curvilinear Photonic Layouts: From Physical Geometry to Process Sign-off | 从GDSII/OASIS重建中心线与曲率的曲线光子版图DFM表征框架 |
| Th2A.6 | 海报 | 器件 | — | Energy-Efficient Non-volatile Si Optical Phase Shifter using Charge-Trap Flash MOS Stack with Graphene Electrode | 石墨烯透明电极+电荷俘获闪存MOS叠层的非易失硅光相移器 |
| Th2A.7 | 海报 | 芯片 | — | Leveraging a Nonvolatile MEMS Switch for Sub-Lithography Silicon Photonics | 非易失MEMS开关后处理将代工230 nm间隙缩至50 nm，实现亚光刻硅光 |
| Th2A.9 | 海报 | 芯片 | — | Demonstration of A Low-Loss Ultra-Compact Silicon-Based Arrayed Waveguide Grating with 1.6 nm Channel Spacing | 超紧凑16通道重叠硅基AWG，1.6 nm间隔、插损<1 dB，540×590 µm² |
| Th3H.5 | 口头 | 芯片 | — | Energy Optimization in Programmable Integrated Photonic Unitary Circuits based on Euler Rotations | 欧拉旋转+最短路径选择优化可编程光子酉电路能耗，每单元节能达1.64 mW |
| Th4A.7 | PDP | 芯片 | 224G | 1.6T (8200Gb/s) 2FR4 Silicon Photonic IMDD Transceiver with Monolithically Integrated Ultra-Low Crosstalk and Wideband Multiplexer | 单片集成布拉格光栅复用器的1.6T(8×200G) 2×FR4硅光收发机，面积缩15倍、串扰低10 dB，3 nm DSP OSFP满足802.3dj |
| Tu2D.1 | 口头 | 芯片 | — | Advancing Silicon Photonics with Photonic-Native Compact Modeling and Hardware Correlation | 特邀：硅光“光子原生”紧凑模型（真双向、多模/多通道仿真）与硬件相关性，面向AI/HPC收发机 |
| Tu2D.2 | 特邀 | 芯片 | — | 3D Hybrid Bonded EIC-PIC Integration and Packaging Technologies | 特邀：3D混合键合EIC-PIC集成与封装技术——全球首个3D混合键合EPIC及协同设计策略 |
| Tu2D.3 | 口头 | 芯片 | — | Samsung Foundry 300-mm Silicon Photonics Platform for HPC/AI Applications | 特邀：三星代工300 mm硅光平台（面向HPC/AI）器件性能与PDK |
| Tu2D.4 | 高分 | 芯片 | 224G | An Innovative 300mm Back Side Integrated Silicon Photonics Platform for 200Gbits/s/lane Applications | 特邀：兼容端面耦合的300 mm背面集成硅光平台PIC100G，面向200G/lane产品 |
| Tu2D.5 | 特邀 | 芯片 | — | Fully Automated Wafer-Level Grating and Edge Coupling Measurement System for Silicon Photonics Integrated Circuits | 全自动晶圆级光栅/端面耦合测量系统，光栅扫描GRR 8.9%、端面耦合重复性±0.03–0.06 dB |
| Tu2J.2 | 高分 | 器件 | — | Adjoint-optimized Dual-Layer Grating Couplers for Low-Loss, High-Bandwidth Optical Interconnects | 伴随法逆向设计的硅/氮化硅双层光栅耦合器，低插损、宽带（单偏振与偏振分离型） |
| Tu2J.5 | 口头 | 器件 | — | Inverse-Designed Edge Couplers for Multimode Silicon Nitride Photonics | 逆向设计氮化硅五模/十模端面耦合器，耦合椭圆芯光纤效率达−2.4 dB，覆盖C+L |
| Tu3C.4 | 口头 | 芯片 | — | Silicon Ring-Based WDM Filter with a Low Tuning Power of 3.80 mW/π per Channel | 硅环8通道WDM滤波器，调谐功耗3.80 mW/π每通道（纪录低），尺寸10×160 µm² |
| Tu3C.5 | 口头 | 器件 | — | Piezoelectrically tunable athermal Mach-Zehnder interferometer based on a tantalum pentoxide platform | 五氧化二钽平台压电可调无热非对称MZI，温漂1.98 pm/K、调谐−36.9 pm/V |
| W2A.3 | 海报 | 芯片 | — | A universal loss characterization method for integrated photonic circuits | 集成光路通用损耗表征方法，无损识别包括光纤-芯片耦合在内各元件损耗/增益 |
| W2A.4 | 海报 | 芯片 | — | Wafer-Scale, Ultra-Low-Loss and Polarization-Insensitive Si3N4 Photonic Integrated Circuits | 晶圆级偏振不敏感超低损Si3N4 PIC平台，单模损耗<15 dB/m、PMD<3.04 ps/m |
| W2A.7 | 海报 | 器件 | — | Quasi-wavelength-agnostic photonic coupler using 3Dnanoprinting | 3D纳米打印椭圆反射耦合器，1 dB带宽覆盖800 nm，准波长无关超宽带耦合 |
| W2A.8 | 海报 | 芯片 | — | Silicon Optical 90° Hybrid Utilizing Widened Waveguides for Mitigating Phase Errors | 1200 nm宽波导伪单模硅光90°混频器，1515–1555 nm相位误差<5°、损耗0.5 dB |
| W2A.9 | 海报 | 器件 | — | Silicon Photonic S-Bent Directional Coupler with Low Wavelength-Dependent Coupling Variation | 硅光S弯定向耦合器，80 nm范围耦合比变化仅0.065，最小特征200 nm |
| W2A.13 | 海报 | 芯片 | — | 12-inch Wafer-level Total Ionizing Dose Effect Analysis of Silicon Photonics Active Devices | 首个12英寸晶圆级硅光高速有源器件总电离剂量(TID)效应分析 |
| W4B.1 | 口头 | 器件 | — | Low Loss Optical Coupling to Photonic Integrated Circuits via Adaptive-Facet-Attached Microlenses | 可回流焊端面贴附微透镜(FaML)光纤-芯片耦合插损<1 dB，可自适应校正达30 µm放置偏差 |
| W4B.2 | 口头 | 器件 | — | All-dielectric integrated microlens coupler for scalable and efficient photonic I/Os | 晶圆级SiON全介质集成微透镜耦合器，宽带偏振不敏感，损耗1.0 dB |
| W4B.4 | 口头 | 器件 | — | Efficient and Polarization-Independent Coupling of Silicon Photonic Chips with 7-Core Multicore Fibers | 硅光芯片与7芯光纤高效偏振分集耦合，损耗2.4 dB、3-dB带宽55 nm、PDL<0.7 dB |
| W4B.5 | 口头 | 器件 | — | Efficient Spatial and Polarization Mode Multiplexer for Few-Mode Fibers Using Silicon-Based Grating Couplers | 硅基光栅耦合器少模光纤空间+偏振模复用器，选择激发8个正交光束通道 |
| W4B.6 | 口头 | 器件 | — | Broadband Dual-Mode Grating Coupler for Efficient Fiber to Chip Interface in Mode Division Multiplexing Systems | 闪耀亚波长光栅双模光栅耦合器，TE0/TE1插损3.03/3.75 dB、1 dB带宽>50 nm |

## 链路与系统

5 篇 · 短距链路与系统级实验

| 编号 | 类型 | 技术层 | 代际 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th1C.2 | 口头 | 芯片 | 448G | Dispersion Managed Transceiver Extending CWDM IMDD to 100G/lane 20km, 200G/lane 10km, and 400G/lane 3km | 接收端加入自锁定色散管理器件的标准FR模块，CWDM IMDD延伸至100G@20 km、200G@10 km、400G@3 km |
| Th2A.39 | 海报 | 光系统 | — | 100 Gbit/s Bidirectional Transmission in a Single Fiber with Twin bidi Transceivers | 两个100G PAM4单波收发机以分路器(而非双工器)配对单纤双向，评估隔离与OBI限制 |
| Th3B.1 | 口头 | 网络 | — | Field Operation Data Analysis of Optical Interconnects in AI Computing Networks | 特邀：AI计算网络光互连现网运行数据分析——故障影响、类型分布与根因 |
| Th3B.2 | 口头 | 网络 | — | Systematic Fault Management of Million-Scale Field-Deployed Optical Transceivers in AI Data Centers | 百度生产数据验证的AI数据中心百万级光模块系统化故障管理（预测+根因定位），F1 0.894 |
| W4H.2 | 口头 | 网络 | — | Analysis and Future-Guided Prediction for Optical Transceiver Failures in AI Data Center Networks | AI数据中心在役光模块时序数据故障预测框架，F1达0.964、召回率100% |
