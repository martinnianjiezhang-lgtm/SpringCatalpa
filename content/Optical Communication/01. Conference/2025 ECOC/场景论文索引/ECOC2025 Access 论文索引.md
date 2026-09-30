---
title: "ECOC2025 Access 论文索引"
tags:
  - ECOC2025
  - 论文索引
---

ECOC 2025 中归入 **Access**（PON、FTTR、前传/RoF、THz/6G、FSO/卫星/光无线）的论文 **132** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2025 ECOC/index|2025年 ECOC 论文专题洞察]]

> [!summary] 关键结论
> VHSP 两条路线并进：IM-DD 超速率 100G〔W.01.07.1〕、120 GBd 对称〔W.01.07.5〕、200G-PON 与三代 PON 共存〔W.02.01.110〕，相干 PON 三速率/240G/单激光器双向〔M.03.07.2–4〕；固移融合相干接入 109 km 现网（PDP）〔Th.03.03.4〕；相干 FSO 4.6 km 500G 可用率实测〔Th.02.07.1〕、中红外 FSO（PDP）〔Th.03.03.5〕；300 GHz THz 7 b/s/Hz〔W.02.01.153〕。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| 固定接入 · [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#50G PON\|50G PON]] | 9 | GPON/XGS-PON/50G-PON 及现网优化 |
| 固定接入 · [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#Beyond 50G PON\|Beyond 50G PON]] | 24 | 100G/200G VHSP、IM-DD 超速率、相干 PON、TFDM |
| 固定接入 · [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#AI-FAN\|AI-FAN]] | 6 | FTTR/家庭网络、PON 智能化、虚拟化与 ODN 运维 |
| 移动接入 · [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#RoF\|RoF]] | 39 | 前传/RoF、毫米波、THz/6G、微波光子 |
| 移动接入 · [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#FSO\|FSO]] | 54 | 自由空间/卫星/可见光/光无线 |

## 固定接入

### 50G PON

9 篇 · GPON/XGS-PON/50G-PON 及现网优化

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Tu.01.07.1 | 教程 | 光系统 | Optical access networks – An operator view from Past to Future System-technologies and Applications | 特邀：运营商视角GPON/10G-PON/50G-PON演进、标准与未来趋势 |
| Tu.02.12.7 | Demo | 光系统 | First Demonstration of IEEE-802.1CB based deterministic networking over PON for reliability in Industrial TSN networks | 首次在商用TDM-PON上运行IEEE 802.1CB确定性网络(FRER)提升工业TSN可靠性 |
| W.01.02.2 | 口头 | 器件 | Optimization of an EML-SOA Structure for the Next-Generation PON 50G-PON | 1342 nm EML-SOA集成结构优化用于50G-PON，满足Class C+/D，ER 8–10 dB、输出10–15 dBm |
| W.02.01.111 | 海报 | 器件 | A Co-Designed DC-Coupled 30-Gbps Burst-Mode Receiver and CDR with 3.2-ns Locking Time for Fast Optical Switching | 协同设计的DC耦合30 Gb/s突发接收机+CDR，锁定时间3.2 ns，面向快速光交换 |
| W.02.01.115 | 海报 | 网络 | Smartphone Camera Detection of ONU Identification Carried by Modulated 650 nm LED Integrated with ONU Optics | ONU光组件内集成650 nm故障定位LED传输ONU序列号，手机摄像头读取（6 km，18 b/s） |
| W.02.01.123 | 海报 | 网络 | Optimization of Upstream XGS-PON Throughput by Adjusting Burst Preamble Length and Enabling Forward Error Correction | 按光预算与光纤长度优化XGS-PON上行突发前导长度与FEC开关，吞吐提升24% |
| W.02.01.126 | 海报 | 网络 | On-site Fiber Identification for PON Systems by using Reflection Power Measurement of Optical Signal and Test Light | 反射功率测量+光纤弯曲+FBG连接器实现PON现场光纤识别（检测未上电ONU） |
| W.03.07.3 | 口头 | 算法 | Digital vs Analog Equalization in FEC supported 50G-PON | 50G-PON中数字均衡+软输入FEC vs 模拟均衡+硬输入FEC：模拟方案仅0.4 dB代价 |
| W.03.07.5 | 口头 | 算法 | Evaluation of 50G-PON FEC Tolerance to Receiver Impairments | 50G-PON下行LDPC(17280,14592) FEC对抖动与判决门限分辨率等接收损伤的容忍度评估 |

### Beyond 50G PON

24 篇 · 100G/200G VHSP、IM-DD 超速率、相干 PON、TFDM

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M.02.07.1 | 口头 | 算法 | Multi-user Chromatic Dispersion DSP-based Precompensation and DD Receiver for Very High Speed PON | 100G-PON PAM-4 多用户色散预补偿+直检，ONU距离0–20 km任意，ODN损耗31+ dB |
| M.02.07.2 | 口头 | 光系统 | Dual wavelength 200 Gbit/s NRZ-OOK Transmission Over 20 km with >30 dB Power Budget Enabled by Quantum-Dot SOAs | O波段双波长200 Gb/s NRZ-OOK，量子点SOA作功放/前放，20 km功率预算30.1 dB |
| M.03.07.1 | 特邀 | 算法 | Cost-effective and Flexible Coherent Optics for Next-Generation Optical Access Networks | 特邀：面向200G/400G的低成本灵活相干PON(CPON)进展与挑战 |
| M.03.07.2 | 口头 | 算法 | 240 Gbit/s Bidirectional Coherent PON Using Uncalibrated ONU Lasers and Blind Coarse Alignment | 240 Gb/s双向相干PON，盲波长粗对准技术使ONU可用未校准激光器 |
| M.03.07.3 | 口头 | 光系统 | Demonstration of Low-Complexity Triple-Rate Coherent PON Achieving up to 200 Gbit/s Symmetric Data Rates | 低复杂度三速率(100/150/200G)相干PON，DP-QPSK子集调制，连续与突发模式链路预算35–38.6 dB |
| M.03.07.4 | 口头 | 器件 | Single-Laser BiDi Coherent PON with Optical Injection Locking: Enabling 100G/200G Access Without High-Cost Lasers in ONU | 基于光注入锁定的单激光器双向相干PON，ONU免ECL，50 km实现100G/200G |
| M.03.07.5 | 口头 | 算法 | Experimental Demonstrations of Polarisation-Based Sensing in Alamouti-Coded Simplified Coherent PONs | Alamouti编码简化相干PON中利用均衡器抽头跟踪偏振态实现振动传感，100 Gb/s/λ、预算>35 dB |
| Th.03.03.4 | PDP | 光系统 | Field Trial of Converged Fixed–Mobile Coherent Optical Access Networks Enabled by Amplitude–Phase Layered Modulation | 幅相分层调制的固移融合相干接入现场试验：109 km运营商光纤上128 Gb/s数字相干+64QAM模拟波形 |
| Tu.01.07.2 | 口头 | 算法 | Demonstration of C-band, 50-Gbit/s×4λ Single-Sideband-NRZ-Signal Transmission through 40-km SMF using 25G-class APD and Simple Feed-Forward Equalizer for Direct-Detection based 50G-TWDM-PON | 全球首个C波段50 Gb/s×4λ SSB-NRZ 40 km传输(25G级APD+仅FFE)，面向直检50G-TWDM-PON |
| Tu.04.07.4 | 口头 | 算法 | Adaptive Digital Compensation of Cascaded SOA Nonlinearities in Metro-Access Networks without Prior Parameter Knowledge | 无需先验参数的级联SOA非线性自适应数字补偿，20 GBd PAM-4灵敏度提升3 dB |
| W.01.04.3 | 口头 | 算法 | Experimental Demonstration of Rate-Adaptation via Hybrid Polar-BCH Product Code for Flexible PON | 首次在相干PON(16QAM)中实验演示灵活速率Polar-BCH乘积码，48 km较BCH-BCH增益1.75 dB |
| W.01.07.1 | 口头 | 光系统 | Super-Rated IM/DD PON Downstream Demonstration at 100G Net Rate using Line Rates up to 124 Gb/s | 超速率(super-rated) IM/DD PON下行：线速率109–124 Gb/s实现100G净速率，损耗预算>30 dB |
| W.01.07.2 | 口头 | 光系统 | 100-120G IM-DD PONs with 32 dB power budget and TDEC with DFE based reference receiver to ensure interoperability | 100–120G IM-DD PON功率预算≥32 dB，首次提出并验证基于DFE参考接收机的TDEC保证互通 |
| W.01.07.3 | 口头 | 光系统 | Experimental Quantification of Stimulated Raman Scattering Penalties Induced by VHSP in PON Coexistence Scenario | 超高速PON(VHSP)与多代PON共存时的受激拉曼代价：XGS-PON上行最多耗尽1.1 dB，约1%链路受影响 |
| W.01.07.4 | 口头 | 芯片 | Integrated 200G Pre-amplified SC-PON Receiver | 首个C波段预放自相干PON，ONU采用III-V/SiP混合集成接收机，20 km下行100–200 Gb/s |
| W.01.07.5 | 口头 | 光系统 | Downstream and Upstream Symmetric 120 GBd NRZ IM/DD Very High Speed PON Using BiDi Amplifier | OLT单个双向掺铋光纤放大器兼作功放与前放，120 GBd NRZ对称上下行VHSP，预算>35 dB |
| W.02.01.51 | 海报 | 芯片 | Fabrication-Tolerant Integrated Polarization-Independent Receiver for Coherent PONs based on LO SOP Tuning | 调节本振偏振态补偿集成PBS工艺缺陷，实现相干PON偏振无关集成接收机 |
| W.02.01.110 | 海报 | 光系统 | 200G-PON based on 4x50Gbit/s NRZ LWDM Signals Coexisting with 50G-PON, XGS-PON and G-PON | 4×50 Gb/s NRZ LWDM实现200G-PON，20 km预算>33 dB，与50G-PON/XGS-PON/G-PON共存 |
| W.02.01.113 | 海报 | 算法 | Nonlinear Signal Recovery Using Pruned Support Vector Machine for 150 - 210 Gb/s Bandwidth-Limited Flexible PON | 剪枝SVM非线性恢复用于带宽受限灵活PON，150 Gb/s PAM-8预算30.5 dB（纪录），210 Gb/s@40 km |
| W.02.01.120 | 海报 | 光系统 | 19-dB DC Leakage Tolerance Improvement for 200G Coherent TDM-PON in Burst-Mode Upstream with Spectral Peak Removal | 频谱峰值去除算法提升200G相干TDM-PON突发上行DC泄漏容限11.3–19.3 dB |
| W.02.01.127 | 海报 | 光系统 | Efficient Dynamic Range Optimization for Coherent PONs via Burst-Mode Digital Signal Processing with Adaptive Power Rebalancing, and Guard Band Management | 100G/200G相干PON突发接收在ONU功率差异下的动态范围优化（突发DSP+功率再平衡+保护带） |
| W.03.07.1 | 口头 | 光系统 | CD Pre-Compensated Tx with ODB Modulation and Direct-Detection Rx for VHSP Downstream | ODB调制+固定抽头色散预补偿+直检，VHSP下行与全部ITU-T PON共存，达N1预算级 |
| W.03.07.2 | 口头 | 光系统 | Optical Frequency Excursion in the Context of VHSP-IMDD | VHSP上行突发模式下多种光源的波长漂移达150–200 GHz，SOA整形突发包络可抑制漂移 |
| W.03.07.4 | 口头 | 光系统 | Coherent Point-to-Point Overlays over PON Using Off-the-Shelf Single-Laser Single-Carrier Pluggable Transceivers | 首次用现成单激光器单载波相干可插拔在PON ODN上叠加双向相干点对点：400G@29 dB、200G/100G@>35 dB |

### AI-FAN

6 篇 · FTTR/家庭网络、PON 智能化、虚拟化与 ODN 运维

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Th.01.05.3 | 口头 | 网络 | Assessment of Energy-Saving Modes Based on Real User Traffic in Passive Optical Networks | 基于真实流量评估PON标准节能模式：Watchful Sleep低负载省电76%，Doze重载省57% |
| Th.01.07.4 | 口头 | 网络 | Experimental Demonstration of Demand-Driven PON Configuration for Fixed-Mobile Convergence | SDN化PON动态T-CONT配置实现固移融合，移动流量亚毫秒时延，低谷期节省带宽80% |
| Tu.01.07.3 | 口头 | 芯片 | Fiber In-Premises Solution With Low-Cost Mono-Optics Transceivers | 低成本单光学(mono-optics)收发机用于楼内光纤的概念研究与初步测量 |
| W.02.01.122 | 海报 | 网络 | Autonomous Transmitter-optical-power Levelling of ONUs for Energy-efficient PON Systems | ONU发射光功率自主均衡算法，降低ONU功耗并缓解OLT接收功率不平衡 |
| W.04.01.2 | 口头 | 网络 | PON Physical Twin: Enabling Third-party Research on FTTH Optimization with Open Datasets | PON物理孪生：商用设备+SDN的可编程PON测试床，开放数据集支持FTTH优化研究 |
| W.04.01.4 | 口头 | 网络 | Softwarization of 320 10G-EPON OLTs Serving 40,960 ONUs with Total 2.78-Tb/s Throughput for Fully Virtualized Central Offices | 超算上软件化320个10G-EPON OLT服务40960个ONU，总吞吐2.78 Tb/s，全虚拟化局端 |

## 移动接入

### RoF

39 篇 · 前传/RoF、毫米波、THz/6G、微波光子

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M.02.01.2 | 口头 | 光系统 | True Time Delay Two-Dimensional Beamforming Enabled by Heterogeneous Multicore Fiber | 基于色散工程7芯异质多芯光纤+FBG阵列的二维真时延光子波束成形，实现水平连续扫描与7个俯仰角 |
| M.02.02.5 | 特邀 | 芯片 | Silicon Nitride Photonics and Plasmonic Microwave Photonic Circuits | 特邀：氮化硅微波光子电路平台，以及等离子体调制器集成迈向THz应用 |
| M.02.08.1 | 口头 | 芯片 | Integrated Multi-beam Beamformer Enabled by Optical Delay Line-based Butler Matrix | 基于8×8光延迟线Butler矩阵与2×8光开关的集成多波束微波光子波束成形器 |
| M.02.08.2 | 口头 | 光系统 | Photonics-Enabled Simultaneous Demultiplexing and Down-Conversion of 220 Gb/s Aggregate 300 GHz Terahertz Signals | 首次光子学实现300 GHz THz信号的解复用与下变频（TFLN调制器+双音光源），线速率>220 Gb/s |
| M.02.08.3 | 口头 | 光系统 | Real-time super-resolution THz imaging based on compressed sensing | 基于压缩感知的实时超分辨THz光子成像，8192像素/秒，分辨率15.5 µm(λ/64.5) |
| M.02.08.4 | 口头 | 器件 | Sub-THz Wireless Transmission with Photonic-assisted Two-dimensional Beamformer Using Optical Butler Matrix Circuits | 两个光学Butler矩阵构成光辅助二维波束成形器，sub-THz 4×2相控阵平均吞吐74.6 Gb/s |
| M.02.08.5 | 口头 | 算法 | High-Quality 98.5-GHz Carrier Generation with Silicon Photonics mm-Wave Band Synthesizer embedding a Multi-Resonant Optical Filter | 硅光多谐振DFB滤波器构成毫米波合成器，对19.7 GHz本振五倍频得98.5 GHz载波，相噪−125 dBc/Hz@1 MHz |
| Th.01.07.2 | 口头 | 光系统 | Nanosecond Electro-optic Switching with Time Synchronisation for Fronthaul TSN Applications | 带时间同步的纳秒电光交换系统用于前传TSN，开关开启延迟33 ns，支持5G/6G动态流量 |
| Th.01.07.3 | 口头 | 光系统 | C-band 2dir.×40λ×224 Gb/s Co-wavelength Bidirectional IM-DD Fronthaul over 10 km Low-latency Hollow-core Fiber | 10 km反谐振空芯光纤上C波段2方向×40λ×224 Gb/s同波长双向IM-DD前传，净16.7 Tb/s（纪录） |
| Tu.02.12.1 | Demo | 光系统 | First Demonstration of Optical Auto-Negotiation for Fronthaul | 首次演示前传光接口光自协商(OAN)的两种实现，改造现有硬件 |
| Tu.03.01.3 | 特邀 | 网络 | Evolution of Optical Networking in support of 6G | 特邀：支持6G的可扩展X-haul光网络架构——可编程光子子系统+编排平台实现端到端切片 |
| Tu.03.08.1 | 口头 | 芯片 | Distributed Coherent Radar System fully Implemented as Heterogeneous SOI-InP Photonic Integrated Circuits | 首个全异质SOI-InP PIC实现的分布式相干雷达系统，X波段测距测速，集中式处理 |
| W.01.09.1 | 口头 | 算法 | Compact and High-Linearity Analog Optical Transmitter for Radio Over Fiber Based on Embedded Predistortion Circuits | 内嵌预失真电路的紧凑高线性RoF模拟光发射机，SFDR提升>17 dB(DC–18 GHz) |
| W.01.09.2 | 口头 | 器件 | Multi-Octave Modified Uni-Travelling Carrier Photodiode Packaging Exploiting a 100 - 500 GHz Waveguide Transition | 100–500 GHz器件-波导过渡的MUTC-PD封装，100/500 GHz输出−1/−20 dBm，面向6G THz |
| W.01.09.3 | 口头 | 器件 | Wireless Millimeter-Wave Electro-Optic Modulators on Thin-Film Lithium Niobate | 薄膜铌酸锂无线毫米波电光调制器(80–380 GHz)，大孔径天线直接从自由空间耦合 |
| W.02.01.25 | 海报 | 芯片 | An on-chip dual-tone source for photonic-based terahertz transmitters | TFLN片上双音光源，生成>100 GHz可调THz载波，线宽亚kHz |
| W.02.01.35 | 海报 | 芯片 | Hybrid Photonic Integrated Circuit for Tunable, Narrow-Linewidth mmWave to sub-THz Signal Generation | 混合PIC利用片上光梳与注入锁定产生30–105 GHz Hz级线宽可调毫米波/亚THz信号 |
| W.02.01.52 | 海报 | 芯片 | Broadband Microwave Photonic Processor Based on Mach– Zehnder Interferometer Weight-Bank for Radio-Frequency Blind Interference Cancellation | MZI权重库宽带微波光子处理器实现RF盲干扰抵消，>20 GHz、6 GBd 16QAM |
| W.02.01.53 | 海报 | 芯片 | Silicon Photonic Integrated Millimeter-Wave Transceiver in Support of All-Optical Frequency Up-/Down-Conversion | 硅光集成毫米波收发模块(RF带宽>30 GHz)，支持全光上/下变频，28 GHz无线11.5 Gb/s |
| W.02.01.70 | 海报 | 算法 | D-band Ultra-Long-Distance Wireless Transmission with Partial Over-the-Sea Link Using QuadConvNet Equalizer | 光子辅助D波段128 GHz 30.2 km（含海面路径）无线传输9 GBd QPSK，二次卷积网络均衡 |
| W.02.01.91 | 海报 | 光系统 | Single-Fiber Single-Wavelength Bidirectional Digital Subcarrier Point-to-Multipoint Coherent Systems for Beyond 5G Transport | 单纤单波长双向DSCM点到多点相干系统用于B5G移动传送，功率优化抑制反射串扰 |
| W.02.01.114 | 海报 | 光系统 | Field Trial of 3×1 Distributed Fiber Wireless mmWave Xhaul with Coordinated Multi-Point Scheduling and Real-Time MEC | 首个3×1分布式光纤-无线毫米波X-haul户外现场试验，协作多点+实时MEC，2 Gb/s、0.195 ms |
| W.02.01.119 | 海报 | 芯片 | Low Power Consumption and Low Latency SFP112-LPO Transceiver with Real-time 20 km Transmission for Next-generation Fronthaul Networks | EML+TEC的SFP112-LPO收发机实时20 km前传，−40~85°C，较DSP模块功耗降67%、时延降91.8% |
| W.02.01.121 | 海报 | 光系统 | Cell-free Massive MIMO Fronthaul with Point-to-Multipoint Data Transmission and Photonics-assisted Radio Carrier Distribution | 无蜂窝大规模MIMO前传：200 Gb/s/λ类PON点到多点+PIC光子辅助射频载波分发，EVM改善25% |
| W.02.01.131 | 海报 | 光系统 | Synchronous Clock and RF Carrier Transmission for Radio Access Network Fronthaul | 时钟相位缓存+光频梳传输在RAN前传中同时实现时钟同步与超低噪RF载波，抖动<100 fs |
| W.02.01.133 | 海报 | 算法 | Demonstration of 30.4-km 20-Gbps Terahertz Wireless Transmission Utilizing CR-MRC Algorithm for OFDM Signals | CR-MRC信道估计的OFDM THz无线30.4 km 20 Gb/s，容量距离积608 Gb/s·km（纪录） |
| W.02.01.135 | 海报 | 器件 | 300-GHz Photonic Wireless Link with 5.3 mW Output Power Using Waveguide-Combined UTC-PD/SiC Photomixers | 两个SiC基InGaAs UTC-PD光混频器波导合路，300 GHz输出5.3 mW（纪录） |
| W.02.01.136 | 海报 | 芯片 | Real-time Integrated 1.37 Centimetres Range Resolution and 15.5 Gbps Communication in Long-rang Bidirectional Photonicassisted Terahertz Band System | 首个实时双向光子辅助THz通感一体系统，>200 m距离分辨率1.37 cm+通信15.5 Gb/s |
| W.02.01.140 | 海报 | 算法 | Blind Massive MIMO Signal Transmission by High Efficiency Compression IF over Fibre Using Cost-Effective EML-CAN | 正交OFDM导频的PAST-IFoF压缩中频光纤传输，盲环境下传8×256 OFDM-64QAM大规模MIMO信号(EML-CAN) |
| W.02.01.144 | 海报 | 算法 | Logarithm-based Nonlinear Quantized Digital-Analog Radioover-Fiber Enables 20dB SNR Gain in Analog Mobile Fronthaul | 对数非线性量化数字-模拟RoF，较常规DA-RoF再增10 dB SNR，1024QAM-OFDM EVM 1.2% |
| W.02.01.147 | 海报 | 光系统 | Demonstration of Millimetre-Wave Antenna Distribution over IFoF System with TDD Timing-Aligned Remote Beam Control | IFoF毫米波天线分布系统，同时传射频与控制信号，实现TDD定时对齐的远程波束控制(38.5 GHz 5G) |
| W.02.01.149 | 海报 | 光系统 | Backscattering of Crosstalk for Monitoring Power over Fiber Co-transmission with 5G NR Analog Radio Over Fiber and NRZ Signals over Multicore Fiber | 7芯MCF上光供能(PoF)与5G NR ARoF、NRZ多波段共传，利用串扰后向散射监测功率，689 mW、39.5 Gb/s |
| W.02.01.153 | 海报 | 光系统 | Demonstration of a 270 Gb/s 300 GHz Entropy-Loaded IM/DD 2 × 2 MIMO THz Wireless Transmission System | 300 GHz光子辅助IM/DD 2×2 MIMO THz无线，熵加载，271.8 Gb/s，频谱效率7 b/s/Hz（纪录） |
| W.02.01.154 | 海报 | 光系统 | High-Laser Linewidth-Tolerance Photonics-aided 300 GHz Terahertz Wireless Transmission System | RF导频辅助的高线宽容忍光子THz(300 GHz)无线传输，30 GBd PS-64QAM 174 Gb/s |
| W.02.01.155 | 海报 | 芯片 | Integrated Ultra-Broadband Microwave Photonic Multi-Beamformer for Fast and Multi-band Beam Steering | 单片集成可调光延迟线+WDM的超宽带(3–43.5 GHz)微波光子多波束成形器，切换6 ns、4波束±30° |
| W.03.01.3 | 口头 | 网络 | Optical Transport Networks Enabling Security Features in 6G Systems | 光传送网支撑6G安全：基于虚拟机热迁移的移动目标防御(MTD)自动化框架 |
| W.03.03.5 | 口头 | 芯片 | Widely Tunable Silicon Photonics Optoelectronic Oscillator | 内嵌近无FSR高Q谐振器的硅光光电振荡器，3.5–37 GHz可调（纪录），相噪~−110 dBc/Hz@1 MHz |
| W.04.02.1 | 口头 | 芯片 | Integrated Multi-Band Photonic Filter Based on MRR–SSG for Tunable Frequency Hopping | SaDE-SQP优化的级联微环-超结构光栅多通道光子滤波器，支持>300 GHz跳频，面向THz安全通信 |
| W.04.05.1 | 口头 | 算法 | 0.25 ps RMS Time-frequency Synchronized WDM Fronthaul with 16.9 Tb/s Rate and 1-sample-per-symbol Coherent Detection | 电光梳双向反馈架构实现0.25 ps RMS时频同步WDM前传，16.9 Tb/s CPRI等效速率+1 sps自零差coherent-lite |

### FSO

54 篇 · 自由空间/卫星/可见光/光无线

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M.03.09.1 | 口头 | 芯片 | High-Speed Coherent Receiver Array on Silicon Photonics for Turbulence-Resilient Communication Links | CMOS兼容硅光4×4相干接收机阵列对畸变波前空间采样，最大比合并补偿湍流，效率接近理论极限 |
| M.03.09.2 | 口头 | 光系统 | Adaptive Bidirectional Free-Space-Optical Link Resilient to Atmospheric Turbulence | 可编程光处理器+信道标记的自适应双向FSO链路，室内模拟数百米湍流链路传输25 Gb/s OOK |
| M.03.09.4 | 口头 | 光系统 | Turbulence-resilient OAM-PolSK with 21.92 dB Sensitivity Gain in FSOC Direct Detection System | OAM-偏振键控(OAM-PolSK) FSO直检系统，较PAM6灵敏度提升21.92 dB，速率103.4 Gb/s |
| Th.01.01.1 | 特邀 | 器件 | High Power Fiber Amplifiers for Free-Space Communications | 特邀：面向卫星FSO地面站的高功率光纤放大器，100 W超大模场掺铒光纤放大器 |
| Th.02.07.1 | 口头 | 光系统 | Experimental Investigation of Availability in a 4.6 km Terrestrial Urban Coherent Free-Space Optical Communications Link | 4.6 km城市相干FSO链路6天可用性测量：500 Gb/s传输下可用率92%（排除慢衰落99%） |
| Th.02.07.2 | 口头 | 器件 | Demonstration of Photodetector-Array-Based Reconfigurable Mode-Division-Multiplexing Coherent Receiver for Spatial Modes Varying Two Indices | 光电探测器阵列型可重构MDM相干接收机(MIMO DSP)，无光解复用器实现6空间模60 Gb/s FSO并抑制湍流 |
| Th.02.07.3 | 口头 | 光系统 | Secure FSO Transmission System Based on Y-00 Protocol Using Optical Decryption Incorporated into Coherent Receiver | FSO中PSK Y-00密码系统：相干接收机本振相位调制实现光学解密，Q代价小、抗截获 |
| Th.02.07.4 | 特邀 | 光系统 | Coherent Modulation for Free-Space Optical Communications: Impact of Turbulence and Link Optimization | 特邀：大气湍流对相干FSO的影响（仿真+实验）及湍流缓解技术 |
| Th.03.03.5 | PDP | 光系统 | Demonstration of a Mid-IR FSO Link Achieving Complex Data Modulation and a Tuneable Wavelength Covering ~4-5 µm Based on a 1.55-µm-Pumped OPO | 1.55 µm泵浦OPO的中红外(4–5 µm可调)FSO链路，支持OOK/QPSK/16QAM，单通道4 Gb/s、多子载波20 Gb/s |
| Tu.01.04.2 | 口头 | 算法 | Filter Generator-Based Adaptive Volterra Equalizer with Ultra-Low Training Overhead Field-Deployed in 4.3-km FSO Link | 预训练导频引导滤波器生成器实现自适应Volterra均衡，4.3 km 100 Gb/s FSO现场较LMS增益2.4 dB，训练开销1/320 |
| Tu.01.09.1 | 口头 | 网络 | Demonstrating of Network Functionalities for Indoor Optical Wireless Attocell Networks: Handover and Multiplexing | 室内光无线atto-cell网络：网络协同波束控制实现无缝切换与无干扰空间复用 |
| Tu.01.09.2 | 口头 | 器件 | Focal Plane Array using VCSELs for Beam Steering in High-Speed Indoor Optical Wireless Communication | 2×2 VCSEL焦平面阵列波束控制的多用户室内光无线链路，每路10 Gb/s OOK无误码 |
| Tu.01.09.3 | 口头 | 器件 | 11.5 Gbit/s Transmission Using a 660 mW LiFi Transmitter | 9个VCSEL阵列(660 mW)+自适应OFDM的LiFi，净速率11.5 Gb/s |
| Tu.01.09.4 | 口头 | 器件 | Optical Wireless Access with Phased- / Focal-Plane Array Beamformers and Multi-Core Coupled APD Diversity Receiver | 用户与热点双端波束成形+多芯耦合APD分集接收，55.2 dB光无线预算下1 Gb/s，无光放大 |
| Tu.01.09.5 | 口头 | 器件 | 10Gbps Visible Light Optical Interconnection Based on Single-pixel Si-substrate GaN DBR-LED with 3D PN-junction | 硅衬底GaN DBR-LED（3D PN结），首个单像素LED实现10 Gb/s可见光互连 |
| Tu.01.09.6 | 口头 | 算法 | Interference-Resilient Optical Wireless Positioning via Machine Learning-Enhanced Subset Filtering | 机器学习增强子集滤波的抗干扰光无线定位系统 |
| Tu.03.03.2 | 口头 | 芯片 | Low-Noise, Frequency-Agile Photonic Integrated Blue Laser for LiDAR and Underwater Communication | 氮化硅自注入锁定+AlN压电调谐的集成蓝光激光器，低噪声、频率捷变，用于LiDAR/水下通信 |
| Tu.03.03.3 | 特邀 | 器件 | Photonic-Crystal Surface-Emitting Lasers for High-Power Free-Space Optical Communications | 特邀：光子晶体面发射激光器(PCSEL)用于高功率高速FSO/星间通信 |
| Tu.03.08.2 | 口头 | 光系统 | A Long-Range LiDAR System Resilient to Sunlight Interference Using Low-Noise InGaAs-APD | AlGaAsSb倍增层低噪InGaAs-APD用于1550 nm LiDAR，探测距离200 m，日光干扰SNR劣化减少7 dB |
| Tu.03.08.3 | 口头 | 芯片 | Silicon Photonic FMCW LiDAR with Integrated High-Speed Line-Scan Illumination and 2D Coherent Receivers | 单片集成线扫光学相控阵+焦平面相干接收阵列的硅光FMCW LiDAR，10 fps（理论62 fps） |
| Tu.03.08.4 | 特邀 | 芯片 | Integrated silicon photonic phased arrays for joint optical wireless communications and LiDAR sensing applications | 512单元免校准低损OPA实现5 Gb/s光无线通信与FMCW LiDAR联合系统(1.5 m) |
| Tu.03.09.1 | 口头 | 网络 | Field Trial of a Record-High Data Rate SDN-Controlled FiWi FSO/mmWave X-haul with Zero-Touch Handover for 6G | SDN编排的FSO/毫米波光纤-无线X-haul现场试验，100 Gb/s实时、24小时全天候零接触切换（混合链路速率纪录） |
| Tu.03.09.2 | 口头 | 光系统 | Demonstration of 2×4 MIMO Hybrid RF-FSO Transmission System Based on Photonics-Aided and Shared Transmitter | 光子辅助共享发射机的2×4 MIMO混合RF-FSO系统，46 Gb/s |
| Tu.03.09.4 | 特邀 | 光系统 | An Adaptive and Reconfigurable Hybrid Free-Space Optical and Millimeter-Wave Wireless Communication System | 特邀：自适应可重构FSO/毫米波混合无线系统原理、架构与现场测试 |
| W.01.02.5 | 口头 | 器件 | Directly Modulated 1.55-μm-Wavelength Photonic-Crystal Surface-Emitting Lasers for Free-Space Optical Communications | 首个直调1.55 µm高功率窄发散角PCSEL，无透镜FSO，3 GBd、链路预算>43 dB |
| W.01.08.1 | 口头 | 光系统 | Experimental Demonstration of Mid-Infrared Free-Space Optical Communication through Turbulence with Mode-Division Multi-plexing of Two 1-Gbit/s OOK Channels | ~3.4 µm中红外两路模分复用FSO过湍流(2 Gb/s)，串扰较1.55 µm低2 dB |
| W.01.08.2 | 口头 | 光系统 | Hybrid Optical / RF Feeder for 6G Radio Access with Shared FSO / FR3 Aperture and ΣΔ-Modulation Switching | 6G无线接入的光/RF混合馈线：共享FSO/FR3孔径与ΣΔ调制切换，19 dB前传预算 |
| W.01.08.3 | 口头 | 器件 | 14 Gb/s MWIR FSO Transmission using Directly Modulated QCL and an Uncooled UTC-PD at Room-Temperature | 首个4.65 µm中波红外FSO系统级演示：直调QCL+室温非制冷UTC-PD，31 m光程14 Gb/s |
| W.02.01.40 | 海报 | 芯片 | Reconfigurable Silicon Photonic Integrated Circuit-based Mode Repeater for Multi-Dimensional Free-Space Optical Communications | 可重构硅光PIC模式中继器，对自由空间光束做模式解复用/复用，支持多波长与双向 |
| W.02.01.129 | 海报 | 网络 | Real-Time Optical Wireless Architecture for Scalable Open RAN in 5G and Beyond Networks | 实时全栈5G RAN，用光无线(OWC)链路作前传与回传，面向可扩展Open RAN |
| W.02.01.139 | 海报 | 芯片 | Heterogeneous Integrated III-V-on-SOI Transmitter for 6G FiWi mmWave/FSO Integrated Sensing and Communication | III-V-on-SOI激光器+EAM异质集成发射机用于6G光纤-无线/FSO通感一体：16QAM 24 Gb/s+384 m雷达分辨0.03 m |
| W.02.01.156 | 海报 | 光系统 | Outage Capacity of Mode-Division-Multiplexed Free-Space Optical Communications under Atmospheric Turbulence | GPU加速蒙特卡洛仿真模分复用FSO湍流信道，揭示中断容量极限 |
| W.02.01.157 | 海报 | 器件 | Hybrid FSO/mmWave Industry 5.0 System Enabled by Ultra-Fast Tunable PZT-based External Cavity Laser | 亚微秒可调PZT外腔激光器支撑的FSO/毫米波混合工业5.0系统(5 km光纤+5 m无线) |
| W.02.01.158 | 海报 | 光系统 | WDM Operation of High-Flux Phosphor-Converted White LEDs for Joint Illumination and Visible-Light Communication | 高光通量荧光白光LED的WDM工作，照明+可见光通信，100 Mb/s代价1.5 dB、双驱动200 Mb/s PAM4 |
| W.02.01.159 | 海报 | 器件 | Programmable Lens Systems with Liquid Crystals Elastomers for High Capacity and Wide Steering Angle Wireless Optical Link | 光敏液晶弹性体可编程透镜实现宽角度光无线发射，15°偏转下10 Gb/s OOK无误码 |
| W.02.01.160 | 海报 | 算法 | B‑Spline-based Hammerstein Nonlinear Equalizer for High-Sensitive VLC Systems using SiPM | 基于B样条Hammerstein非线性均衡的SiPM高灵敏VLC，优于DP-VNLE等，速率与距离超APD方案 |
| W.02.01.161 | 海报 | 器件 | Improved Sensitivity in SiPM-based VLC by Laser Linearization | 首次将激光器线性化用于405 nm激光-SiPM VLC，5 Gb/s OOK，灵敏度提升6.4 dB |
| W.02.01.162 | 海报 | 算法 | Channel Reciprocity-Driven Adaptive Optical Power Transmission for Turbulence Mitigation | 基于信道互易性的EDFA自适应功率分配抑制湍流，上行10G/下行400G可靠性提升90% |
| W.02.01.163 | 海报 | 光系统 | Self-aligned 10-Gb/s All-optical Infrared Wireless Using Crystalbased Multiplexed Holographic Beamsteering | 光折变晶体复用全息波束控制实现自对准10 Gb/s红外光无线（光纤-无线-光纤） |
| W.02.01.164 | 海报 | 光系统 | Long-Range, High-Capacity FSOC System for Rural Wireless X-Haul Using COTS Transceivers | 美国爱荷华州乡村10.15 km公开FSO测试床，商用10G SFP+多通道，研究闪烁与掉线 |
| W.02.01.165 | 海报 | 光系统 | Impact of Elevation Angle on 100Gbps Optical Coherent Uplink Transmission in Low Earth Orbit Satellite Communication | 地面-LEO卫星100 Gb/s相干上行：不同轨道高度与仰角下性能，验证COTS收发机可行 |
| W.02.01.166 | 海报 | 器件 | Experimental demonstration of 75 Gbps OAM multiplexing system using 1310 nm VCSEL transmitter | 1310 nm VCSEL+螺旋相位板的OAM复用光无线链路，1 m总速率75 Gb/s |
| W.02.01.167 | 海报 | 光系统 | Experimental Demonstration of Event-based Optical Camera Communication in Long-Range Outdoor Environment | 事件相机光学摄像头通信的鲁棒解调，首次室外200 m@60 kb/s、400 m@30 kb/s BER<10⁻³ |
| W.02.01.168 | 海报 | 算法 | Experimental Demonstration of Deep Joint Source-Channel Coding for Robust Image Transmission over Underwater VLC | 深度联合信源信道编码(DeepJSCC)用于水下VLC图像传输，BER>10⁻³时PSNR仍>22 dB |
| W.03.03.3 | 特邀 | 芯片 | Photonic Integrated Processors for Free-Space Optical Communications and Sensing | 特邀：光子集成处理器实现FSO可重构收发——波前扰动实时感知补偿与SDM正交模自动优化 |
| W.03.08.2 | 口头 | 器件 | Ultra-Low Crosstalk FSO Circulator for Full C-band WDM Bidirectional Satellite Communication | 超低串扰(<−90 dB) FSO环行器，实现1 Tb/s C波段WDM双向卫星FSO通信 |
| W.03.08.3 | 口头 | 器件 | Coherent Free-space Optical Communication at the C-band using InP-based Photonic-crystal Surface-emitting Laser | 首次用InP基PCSEL实现C波段相干FSO通信，1 Gb/s、链路预算>67 dB，免光纤放大器 |
| W.04.05.3 | 口头 | 光系统 | Field Demonstration of Full-Photonic Assisted Ultra-Reliable Hybrid FSO/MMW Transmission over 4.3 km based on Single Optical Coherent Receiver | 全光子辅助+单相干接收机的FSO/毫米波混合传输，4.3 km城市链路最高200 Gb/s超高可靠 |
| W.04.05.5 | 特邀 | 光系统 | Photonics for Communications Satellites: a Perspective from Thales Alenia Space | 特邀：Thales Alenia Space视角下通信卫星光子载荷、卫星FSO与量子光通信的进展与展望 |
| W.04.08.1 | 口头 | 光系统 | Attenuation-Resilient 1-Gbit/s OOK Underwater Free-Space Optical Communications Using a Longitudinally Structured Multi-𝑘𝑧 Bessel Beam | 纵向结构多kz贝塞尔光束实现抗衰减1 Gb/s OOK水下FSO，较高斯光束功率提升9 dB |
| W.04.08.2 | 口头 | 光系统 | Spectrum-Woven Flat-Narrow Twin Beams with Time-Domain Adaptation for Underwater Optical Wireless Communication | 频谱编织平顶窄双光束WDM-时域自适应水下光无线，最高2.5 Gb/s |
| W.04.08.3 | 特邀 | 光系统 | Ultra-High Capacity Optical Wireless Communication Enabled by Steered Infrared Beams | 特邀：基于红外光束偏转的室内超高容量光无线通信综述 |
| W.04.08.4 | 口头 | 光系统 | Optical Wireless Transmission of 8 Gbps Using Array of Large Grating Couplers on Silicon Photonics for Light Collection | SOI上四个大面积80°开角光栅耦合器“风车”阵列收光，360°视场，人眼安全功率下8 Gb/s OOK无误码 |
| W.04.08.5 | 口头 | 器件 | Short Range Optical Wireless Communication at 67.8 Gbit/s using a Multiaperture VCSEL | 多孔径VCSEL点对点光无线(固定无线接入)，5 m距离FEC后67.8 Gb/s |
