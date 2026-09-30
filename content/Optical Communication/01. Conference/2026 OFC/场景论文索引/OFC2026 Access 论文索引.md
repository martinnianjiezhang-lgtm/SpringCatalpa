---
title: "OFC2026 Access 论文索引"
tags:
  - OFC2026
  - 论文索引
---

OFC 2026 中归入 **Access**（PON、FTTR、前传/RoF、THz/6G、FSO/卫星/光无线）的论文 **147** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2026 OFC/index|2026年 OFC 论文专题洞察]]

> [!summary] 关键结论
> 相干 PON 独立成场：首个双向 200G TFDM 相干 PON 现场试验〔Th4C.4〕、非制冷 DFB 突发上行 37 dB〔Th4C.3〕、统一 OLT 兼容相干与 IM-DD ONU〔W1I.4〕；THz 单链路 600 Gb/s〔M4H.6〕、312 GHz 3 km 现场〔M4H.7〕；卫星光网络路由/切换成独立 Session（Tu3F），飞机–GEO 激光链路首批结果〔Th4B.1〕；光无线 516 Tb/s〔M3H.3〕。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| 固定接入 · [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#50G PON\|50G PON]] | 3 | GPON/XGS-PON/50G-PON 及现网优化 |
| 固定接入 · [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#Beyond 50G PON\|Beyond 50G PON]] | 21 | 100G/200G VHSP、IM-DD 超速率、相干 PON、TFDM |
| 固定接入 · [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#AI-FAN\|AI-FAN]] | 17 | FTTR/家庭网络、PON 智能化、虚拟化与 ODN 运维 |
| 移动接入 · [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#RoF\|RoF]] | 55 | 前传/RoF、毫米波、THz/6G、微波光子 |
| 移动接入 · [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#FSO\|FSO]] | 51 | 自由空间/卫星/可见光/光无线 |

## 固定接入

### 50G PON

3 篇 · GPON/XGS-PON/50G-PON 及现网优化

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Th1K.5 | 口头 | 算法 | Diagonal Turbo Product Coding for Combating PON Upstream Burst Errors | 对角Turbo乘积码对抗PON上行突发误码，较常规TPC额外增益0.95 dB |
| Th1K.6 | 口头 | 算法 | PON Bitrate Optimization Adapting Flexible Header and FEC According to Field Data | 基于6.8万个ONU现网数据估计调节报头与FEC参数可使XGS-PON上行吞吐提升达70% |
| W1I.3 | 特邀 | 网络 | Optical Access Networks Roadmap | 特邀（Denis Khotimsky, Verizon/FSAN荣誉主席）：光接入网路线图——回顾2007/2016 FSAN规划与实际进展及展望 |

### Beyond 50G PON

21 篇 · 100G/200G VHSP、IM-DD 超速率、相干 PON、TFDM

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Th1K.2 | 口头 | 算法 | Cost-Effective 228-Gb/s Extended-Reach SC-PON using a Dithered Uncooled DFB Laser and Hybrid Integrated Stokes Receiver | 抖动非制冷TO-Can DFB+混合集成Stokes接收机的低成本228 Gb/s扩展距离自相干PON，40.72 km、预算31.2 dB |
| Th1K.3 | 口头 | 光系统 | Simplified Bidirectional PON over 22km AR-HCF with 200-Gb/s/ૃ Downstream and 50-Gb/s/ૃ Upstream | 22 km反谐振空芯光纤上简化双向PON，下行相干200 Gb/s/λ、上行IM 50 Gb/s/λ共享单激光器，预算>40 dB |
| Th2A.37 | 海报 | 算法 | Enhancing coherent PON power budget through SOA boosting and DSP compensation | SOA功放+DSP补偿非线性，200 Gb/s相干PON功率预算提升13.5 dB |
| Th3E.1 | 特邀 | 光系统 | Analysis and Demonstration of Future Coherent Metro-PON Converged Networks | 在承载现网流量的既有基础设施上实验表征相干城域-PON融合网络 |
| Th4C.3 | PDP | 光系统 | Uncooled TO-Can DFB Laser Enabling Extended Reach and Record Power Budget for Burst-Mode Upstream in 200-Gb/s VHSP SC-PON | 每ONU非制冷TO-Can DFB+SOA的突发模式自相干PON，上行228 Gb/s 40.72 km，功率预算37 dB（纪录） |
| Th4C.4 | PDP | 光系统 | World’s First Field-Trial Demonstration of Bidirectional 200G TFDM Coherent PON Enabled by Real-Time FPGA-Based Reception | 全球首个双向200G TFDM相干PON现场试验，FPGA实时双子载波接收，下/上行灵敏度−34/−31 dBm |
| Tu2E.4 | 特邀 | 芯片 | Photonic Integrated Wavelength Distribution Node for Optical Metro-Access Networks | 光子集成波长交换节点向接入节点动态分发800G WDM通道，支撑多Tb/s城域-接入网 |
| Tu2E.6 | 口头 | 网络 | Bandwidth Allocation Optimization for Single-Subcarrier Reception in TFDM Simplified CPON | TFDM简化相干PON单子载波接收约束下的带宽分配优化模型与算法，100G下行 |
| W1I.1 | 口头 | 网络 | Best Migration Strategies Comparison towards 100G Coherent PON | 面向100G PON的迁移策略比较：610 km²、7.35万ONU场景中100G相干PON远端OLT最具成本效益 |
| W1I.2 | 口头 | 算法 | New Chromatic Dispersion Digital Pre-Compensation Method using FIR Coefficients Optimized from Upstream Burst-Mode signals in IMDD/Coherent Hybrid PON | 利用上行突发信号优化FIR系数的色散数字预补偿新方法，IMDD/相干混合PON 80 km 50 Gb/s，预算>33 dB |
| W1I.4 | 口头 | 算法 | Toward Very High-Speed PON: C-band Unified OLT Supporting Coherent and IM/DD ONU Interoperability via DSP Mode Compatibility and Zero-Flip Encoding | C波段统一OLT通过DSP模式切换+零翻转编码同时支持相干与IM/DD ONU，50 km 100/200/400 Gb/s |
| W1I.5 | 口头 | 光系统 | Demonstration of Dual-polarization Intensity Modulation and Coherent-detection Based Hybrid 200G PON Burst Reception with Fastconverging Digital Signal Processing | 双偏振强度调制+相干检测混合200G PON突发接收，51.6 ns前导与快速收敛DSP，22 km预算29.5 dB |
| W2A.36 | 海报 | 算法 | 400G 4ૃ WDM-PON over C-band 20km~50km SSMF Enabled by Optically Filtered Comb Sideband Modulation and Linear Equalizer with 44dB Power Budget | 光滤波梳边带调制+线性均衡的400G 4λ WDM-PON，C波段20–50 km，功率预算44 dB |
| W2A.39 | 海报 | 算法 | IQ Skew Estimation and Calibration with Time-Interleaved Preamble for 256-Gb/s Coherent TFDM PON Downstream | 时间交织前导估计256 Gb/s相干TFDM-PON下行IQ偏斜，误差±0.6 ps内 |
| W4F.1 | 口头 | 器件 | Experimental Demonstration of a Large Dynamic Range Burst-Mode Receiver for 200G Upstream Coherent PON Based on Static Gain TIA | 商用ICR固定增益TIA实现200G上行相干PON大动态范围(20 dB)突发接收，DP-QPSK 40 km |
| W4F.2 | 口头 | 算法 | Spectrum-Notch-Coded Modulation Enabled Pilot-Tone-Aided Carrier Recovery for Single Carrier 200G Coherent PON | 首次提出频谱陷波编码调制，单载波200G相干PON带内导频辅助载波恢复，复杂度低于DSCM |
| W4F.3 | 特邀 | 光系统 | Technologies for Very High Speed PON | 特邀：超高速PON(>50 Gb/s/λ)技术与架构综述，聚焦低成本与多代共存 |
| W4F.4 | 高分 | 光系统 | Advanced Digital FOE Methods for Ultra-Wide Carrier Frequency Offset Handling in Coherent TDM PON | 两种数字频偏估计方法补偿±20 GHz频偏，相干TDM PON 50 km超速率100G/200G |
| W4F.5 | 高分 | 算法 | DC Leakage-Induced ONU Interference and Mitigation in 200G Burst-Mode Coherent PON | 200G突发相干PON中未发送ONU的DC泄漏干扰：OLT低复杂度数字高通优于自适应均衡 |
| W4F.6 | 口头 | 光系统 | 240-Gbps Simplified Super-Rate Coherent TFDM-PON in Upstream with Dual-LO Adaptive Power Control in both Time and Frequency Domain | 双本振时/频域自适应功率控制的240 Gb/s简化超速率相干TFDM-PON上行，突发动态范围>25 dB |
| W4F.7 | 口头 | 算法 | DSP Simplification for Coherent TDM and TFDM PON via CFO Reuse and Warm-Start Phase Recovery | 频偏复用+热启动相位恢复简化相干TDM/TFDM PON DSP，50 km DP-16QAM代价<1 dB |

### AI-FAN

17 篇 · FTTR/家庭网络、PON 智能化、虚拟化与 ODN 运维

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M2F.1 | 口头 | 网络 | Advancing Explainability through a SHAP-Guided Adaptive Windowing Framework | 首个SHAP引导自适应窗口LSTM框架，满足50G-PON上人机交互(H2M)时延，推理时间降46.8% |
| M2F.3 | 口头 | 网络 | TinyML-Empowered Human-to-Machine Applications over Future Access Networks | 在光接入网集成TinyML支撑H2M应用，能耗降低约97%、往返时延降约190 µs |
| M2F.4 | 教程 | 光系统 | From Copper to Fiber-to-the-Room: The Evolution of In-Home Networks for the Era of Immersive Applications | 教程（Elaine Wong）：从铜缆到光纤到房间(FTTR)——面向沉浸式应用的家庭网络演进、标准与ION-2030 |
| M3Z.7 | Demo | 网络 | Demonstration of Remote Robotic Control by Industrial Protocol Softwarization over 117 km All Photonics Network | 工业协议软件化，经117 km全光网(APN)远程控制异构机械臂 |
| M3Z.8 | Demo | 网络 | Distributed Intelligence Framework with Privacy-Preserving Features for FTTR Network Monitoring and Automation | FTTR网络隐私保护分布式智能框架，本地遥测+自主重配 |
| M3Z.9 | Demo | 网络 | Live Demonstration of Optical Connection Switching by APN-Transceiver and No Wavelength Dependance APN-Splitter for Distributed Access Network | 首个PON远程控制APN收发机+波长无关APN分光器的光连接切换现场演示 |
| M3Z.13 | Demo | 网络 | Autonomous Intent-driven Optimization of PONs: A Vendor-agnostic DRL Demonstration | 厂商无关DDQN深度强化学习自主配置PON T-CONT，固移融合上行时延优化 |
| Th1K.1 | 口头 | 光系统 | Real-Time, 1-m Resolution Measurement of the Optical Distribution Network of a 21-km, 1:32 PON with a Coherent Optical Frequency Domain Reflectometer | 相干OFDR实时测量21 km 1:32 PON ODN，1 m分辨率、60 ms采集，识别全部分支末端 |
| Th1K.4 | 特邀 | 网络 | Virtualisation in Optical Access Networks: Challenges and PHY Softwarization | 特邀：光接入网虚拟化——控制功能与PHY软件化的挑战与进展 |
| Th2A.36 | 海报 | 网络 | AI-Driven Multi-User ODN Monitoring by Upstream Polarization-Sensing in IM/DD Passive Optical Networks | IM/DD PON上行偏振传感+AI实现多用户ODN监测，分类/定位准确率达99.98% |
| Th2A.38 | 海报 | 网络 | Telemetry Database for Heterogeneous Optical Access Networks Enabling Monitoring and Sensing Data Fusion | 异构接入网遥测数据库：GPON/XGS-PON/25GS-PON/100ZR共存ODN的监测传感数据融合与树发现 |
| Th2A.40 | 海报 | 网络 | AI Learns G-PON: Toward Adaptive T-CONT Configuration for Fixed-mobile Convergence | 商用G-PON作AI自优化底座，深度强化学习调整T-CONT优化固移融合时延 |
| Th3E.3 | 口头 | 网络 | Dynamic Control of Multi-Technology Optical Access Networks with PON and Coherent P2MP | 可编程矩阵+SDN编排集成PON与相干P2MP的多技术接入汇聚架构 |
| Th3E.4 | 口头 | 网络 | End-to-End Orchestration across MCF Infrastructure: Field Trial of Spatial PON and Metro Convergence with O-RAN for AR/VR Services with Edge Offload | 首个MCF基础设施上空间PON与5G O-RAN能效感知融合现场试验（AR/VR边缘卸载），节能8% |
| Tu2E.1 | 口头 | 网络 | Optical Switching in PON: Improved energy-efficiency and cost-effective protection | PON中引入光交换，使OLT功耗随流量伸缩并实现低成本保护，倒换时间可达Type-B水平 |
| Tu2E.3 | 口头 | 网络 | Generative Forecasting of Aggregated FTTR Traffic for Resource Allocation Enabling Immersive XR Collaborations | Transformer生成式预测FTTR聚合多模态流量，前瞻分配FTTH资源保障XR体验，长时预测准确度提升70% |
| Tu2E.5 | 口头 | 网络 | Traffic Measurements and Models Based on Real User Data from Different German Operators | 基于德国3129条接入连接真实流量的紧凑傅里叶模型，用于PON节能与容量规划 |

## 移动接入

### RoF

55 篇 · 前传/RoF、毫米波、THz/6G、微波光子

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M2F.2 | 特邀 | 算法 | AI-Orchestrated Access Transport Networks for 6G | 特邀：AI编排的6G接入-传送(Xhaul)网络，面向差异化连接与AI训练流量的端到端服务 |
| M2I.1 | 特邀 | 光系统 | Next-Generation Optical Fronthaul for High Speed Wireless Links | 特邀：5G/B5G大容量RoF光前传综述——MIMO、光子波束成形、光毫米波生成与MCF传输 |
| M2I.2 | 口头 | 光系统 | Non-Orthogonal Analog RoF Fronthaul Using Chirp Diversity and Dispersion-Induced Power Fading without Successive Interference Cancellation | 利用啁啾分集与色散功率衰落的非正交多址模拟RoF前传，免SIC，64QAM多用户共传 |
| M2I.3 | 口头 | 芯片 | A High-Power 4-channel Analog Optical Transceiver Supporting Minimalist Base Station with Photodiode-Drive Antenna in Mobile Fronthaul | 支持PD直驱天线的高功率4通道模拟光收发机，实时400 MHz 5G-NR-256QAM，EVM<2.5% |
| M2I.4 | 特邀 | 光系统 | Analog Radio-over-Fiber for 6G | 特邀：面向6G的模拟RoF：线性度/ACLR/EVM需求、动态范围限制与KAN数字预失真 |
| M2I.5 | 口头 | 算法 | Experimental Demonstration of Lightweight Linear Filter-Based Nonlinear Precompensation in Analog Radio-over-Fiber Transmission | 轻量线性滤波器型非线性预补偿用于高频段模拟RoF |
| M2I.6 | 口头 | 算法 | Improved Performance of Seamlessly Converged Fiber-mmWave Transmission Systems by Iterative SSBI Mitigation-Enabled Global Linearization | 迭代SSBI消除的全局线性化用于光纤-毫米波融合系统，25 km 3.556 Gb/s，DSP复杂度较KK降>51.4% |
| M3M.3 | 口头 | 算法 | An Open-Source mmWave Analog Radio-over-Fiber Dataset Enabling Machine Learning Applications | 首个开源毫米波模拟RoF数据集(28–30 GHz，0–10 km SMF)，含QAM波形与ML均衡基线 |
| M4H.1 | 高分 | 光系统 | Demonstration of 104-GBaud/λ Digital Subcarrier Multiplexing 317-GHz THz Signal Wireless Delivery Based on Photonics-aided Technologies | 光子辅助317 GHz THz-over-fiber 104 GBd/λ DSCM，25 km+1 m无线，净374.4 Gb/s/λ/偏振（纪录） |
| M4H.2 | 口头 | 光系统 | Ultralow-Nonlinearity THz Signal Transmission over PBG HCF for Low-Latency, High-Power Fiber–Wireless Links | 光子带隙空芯光纤超低非线性传THz数据与稳定本振，3.9 km入纤29 dBm，300 GHz 100 Gb/s |
| M4H.3 | 口头 | 器件 | DBPSK Communication in THz-band Using Waveguidetype Mach-Zehnder Interferometer-based Receiver | 3D打印金属化空心波导非对称MZI在THz域直接解调20 Gb/s DBPSK(300 GHz) |
| M4H.4 | 口头 | 光系统 | Toward Practical Photonic THz Links: Field Demonstration of Beam Alignment for Real-Time Wireless Fronthaul at 300 GHz | 300 GHz光子THz实时无线前传现场波束对准演示，200 m传25GbE eCPRI |
| M4H.5 | 口头 | 光系统 | Real-time Simplified Coherent Photon-assisted 322GHz Terahertz Signals Transmission over 30-m wireless Using Parallel Kramers-Kronig Receiver and FPGA Operation | 首次FPGA实时简化相干322 GHz THz传输：并行KK接收，27 Gb/s 16QAM DMT，30 m无线 |
| M4H.6 | 口头 | 芯片 | 600-Gbps THz Wireless Communication Enabled by Low-Noise Integrated Kerr Optical Frequency Combs | 低噪集成Kerr光频梳作THz源，首次300 GHz频段4 m无线600 Gb/s |
| M4H.7 | 高分 | 光系统 | Field Trials of Photonics 312 GHz Terahertz-wave Signals Transmission over 3 km Wireless Distance | 光子312 GHz THz信号3 km无线现场传输（>300 GHz最远纪录） |
| M4H.8 | 口头 | 算法 | Polarization Effects and Crosstalk Mitigation in a 240 Gbps Dual-Polarization SISO Optical–THz Integrated System | 正交模转换器双偏振SISO光-THz系统320 GHz 240 Gb/s，相关规避MIMO Volterra抑制偏振串扰 |
| Th1H.1 | 口头 | 芯片 | Low Threshold and RIN in 100-kHz-class Linewidth Monolithic Dual-Mode DFB Laser with 300-GHz Frequency Spacing for sub-THz Transmission | 改变切割角实现300 GHz间隔单片双模DFB激光器，阈值12 mA、RIN −155 dB/Hz，用于亚THz |
| Th2A.21 | 海报 | 光系统 | Evaluation of an Erbium Doped Waveguide Amplifier RF performance in Microwave Photonics Applications | Si3N4平台掺铒波导放大器在集成微波光子系统中的RF性能评估，无诱发非线性 |
| Th2A.58 | 海报 | 光系统 | A Novel High-Speed Photonic Instantaneous Frequency Measurement using Frequency Shifting Recirculating Loops | 移频循环环路光子瞬时频率测量，单激光器数十微秒内识别RF频率 |
| Th2A.60 | 海报 | 芯片 | Indoor Trial of a Distributed Coherent 2x2 MIMO Radar on Three Photonic Chips | 首个三颗硅-InP混合PIC光连接的分布式相干2×2 MIMO雷达室内试验，分辨率优于30 cm |
| Th2A.61 | 海报 | 光系统 | A Novel Photonic Radar Jamming Technique Based on Gate-controlled Dual Modulation | 门控双调制光子雷达干扰技术，生成非对称假目标（5个，最大偏移225 m） |
| Th2A.62 | 海报 | 光系统 | Tunable Microwave Photonic Radar Jamming System Based on Optical Frequency Comb | 基于光频梳的可调微波光子雷达干扰系统，定制梳线幅度生成多样假目标簇 |
| Th2A.63 | 海报 | 光系统 | Demonstration of frequency-tunable photonic-aided D-band km-level communications with high reliability | 频率可调光子辅助D波段公里级高可靠通信，20 Gb/s |
| Th2A.64 | 海报 | 芯片 | High Power Narrow Linewidth Monolithic DW-DFB Laser for Tunable Terahertz Generationn | 高功率窄线宽单片双波长DFB激光器，0.113–0.488 THz可调，输出170 mW |
| Th2A.67 | 海报 | 光系统 | Real-Time Photonic Down-Conversion for Fiber Fading-Free Dual-Sideband Conjugated-RoF Transmission | PD光混频+ADC谐波采样的实时光子下变频，实现无光纤衰落双边带共轭RoF，25 km |
| Th2A.68 | 海报 | 光系统 | Optical Comb-based Next-Generation FTTx Architecture for seamless Residential and 5G-NR Service Provision | 基于光梳的下一代FTTx架构，同时提供家庭宽带与5G-NR（滤波/交换/波束成形PIC） |
| Th2A.72 | 海报 | 光系统 | Impact of Antenna Misalignment on a 30-km D-Band Photonics-Assisted Wireless Link | 30 km D波段光子辅助无线10 Gb/s，天线失准容限0.65°，给出远距THz对准指南 |
| Th3A.6 | 口头 | 芯片 | Ultra-Fast and Multi-point Microwave Photonics Frequency Hopping with Integrated Decoy Tones for Secure Millimeter-Wave Communication | 含诱饵音的超快多点微波光子跳频(70 GHz带宽、5 ns跳周期)，保障毫米波安全通信 |
| Th3A.7 | 口头 | 光系统 | Square-Root-Processed and Optical Carrier-Suppressed DSB Modulation for Simple Analog Radio-over-Fiber Transmission Systems | 平方根预处理+载波抑制DSB调制，简化模拟RoF传输系统 |
| Th3D.3 | 口头 | 光系统 | Wideband, Low-Loss, Multi-Wavelength-channel, Continuously Tunable Optical True Time Delay Processor | MEMS倾斜镜自由空间光谱处理器：32个波长通道独立连续可调真时延(>1 ns)，带宽>40 GHz、损耗6 dB |
| Th3D.4 | 口头 | 光系统 | 2.4 Tbit/s Random Bit Generation with Programmable Massively Parallel Chaos Source | 可编程大规模并行混沌源(40通道×~34 GHz)，随机比特生成2.4 Tb/s |
| Th3D.5 | 口头 | 光系统 | Wide-Bandwidth and High-Precision Silicon Microwave Frequency Measurement System | WDM+可编程测频的硅基信道化瞬时频率测量，1–40 GHz误差24.02 MHz |
| Th3D.6 | 特邀 | 芯片 | Integrated microwave photonics inside radar systems: potential and current issues | 特邀：雷达系统内集成微波光子学的潜力与当前问题（降低SWaP） |
| Th3E.2 | 口头 | 光系统 | Demonstration of High Accuracy Timing Transport over Optical WDM Network alongside 200G Wavelength Traffic | WDM网络中与200G波长共传的高精度时间传送，四级边界时钟链精度±15 ns |
| Th3E.5 | 口头 | 算法 | Decoupling Equalization from Network Complexity: An Interpretable Kolmogorov-Arnold Network-Based Equalizer for Real-time Low-Latency 6G Links | 可解释KAN均衡器用于THz-over-fiber，6个前向计算单元增益1.2 dB，FPGA查表实现超低时延 |
| Tu2E.2 | 特邀 | 网络 | Radio-Optical Confluence in Intelligent Edge Networks | 特邀：智能边缘网络中无线与光从融合走向“汇流”(confluence)的新架构 |
| Tu2H.2 | 高分 | 芯片 | K/Ka-Band mmWave Radio-over-Fiber Transceiver with co-designed SiGe EIC and SiPh PIC for Intra-Satellite Links | SiGe RFIC与硅光PIC协同设计的全硅K/Ka波段(18–36 GHz)毫米波RoF收发机，用于卫星内链路 |
| Tu2H.3 | 高分 | 芯片 | Packaged InP PIC for Photonic RF Receive Front-End of High-Capacity Telecom Satellites | 封装InP PIC光子射频接收前端用于Ka与Q/V波段高容量通信卫星，噪声系数降达14 dB |
| Tu2H.4 | 口头 | 器件 | A Single High-Power SiC-Based UTC-PD Enabling a 40-Gbit/s Two-Channel FDM-THz Link | 单个高功率SiC基UTC-PD实现两通道频分THz(257/277 GHz) 40 Gb/s链路，16.3 m |
| Tu2H.7 | 口头 | 芯片 | J-Band Waveguide-Coupled UTC-PD Module Enabling 200 Gbit/s Photonic Terahertz Communications | J波段波导耦合UTC-PD模块兼顾高响应度与高功率，286 GHz 10 m偏振复用QPSK 200 Gb/s |
| Tu3B.2 | 口头 | 光系统 | Dual optical frequency comb downconversion of D-band mm-wave signals | 双光频梳将任意窄带D波段(110–170 GHz)信号下变频到基带，免滤波与频率调谐 |
| Tu3B.3 | 口头 | 芯片 | On-Chip Active Mode-Locked Optoelectronic Oscillator for Fully Tunable Microwave Pulses Generation | 片上主动锁模光电振荡器，调控自由载流子实现中心频率与占空比全可调微波脉冲 |
| Tu3H.4 | 口头 | 器件 | 300-GHz Independent Multi-Beam Steering from a Single Antenna Using Fiber Chromatic Dispersion and Photomixer Array | 利用光纤色散+UTC-PD阵列，单天线阵列实现300 GHz独立双波束扫描，4K视频传输 |
| Tu3H.5 | 口头 | 器件 | Continuously Tunable, Low Phase Noise Photonic Frequency Synthesizer over 3–170 GHz for High Performance mm-wave Communications | 锁相低线宽激光+分频辅助的3–170 GHz连续可调光子频率合成器，170 GHz抖动12 fs，D波段QPSK/16QAM |
| Tu3K.3 | 口头 | 算法 | Hybrid Quantum Neural Network for Symbol Recovery in Photonic-assisted Terahertz Communication System | 混合量子神经网络用于光子辅助THz通信符号恢复，200 m无线实时11.48 Gb/s |
| W1G.2 | 口头 | 算法 | Interference Suppression with Software Programmable Microwave Photonic Filter in RF Communications | 软件可编程集成微波光子滤波器抑制强RF干扰，2 Gb/s QPSK EVM改善>40% |
| W1H.7 | 口头 | 网络 | User-Mobility-Aware Optimization of Fiber Placement in Hybrid Fiber–IAB Networks | 元启发式优化光纤-IAB混合网络中光纤布放，考虑用户移动性，面向6G回传 |
| W2A.1 | 海报 | 器件 | Broadband MUTC-PD Based Photonic THz Transmitter for Multiband Wireless Communications | 超快MUTC-PD+端射天线紧凑THz发射机，覆盖75–170 GHz，156 Gb/s无误码 |
| W2A.37 | 海报 | 算法 | Ultra-stable Radio Access Network Synchronization by Cesium-Locked Comb Delivery and Clock Phase Caching | 铯钟锁定光梳分发+时钟相位缓存实现RAN超稳同步：3.5天相对同步6.5 ps RMS、RF载波抖动<60 fs |
| W2A.38 | 海报 | 网络 | Novel Optical Connection Switching by APN Transceiver and Passive APN Splitter for 6G Mobile Fronthaul | 可调APN收发机+无源APN分光器实现6G移动前传光连接动态切换 |
| W2A.69 | 海报 | 芯片 | Enhanced Self-Heating 8-Wavelength Monolithic DFB Laser Array for Broadly Tunable CW Terahertz Generation | 增强自热8波长单片DFB阵列，0.69–6.09 THz宽带连续可调CW THz产生 |
| W4C.1 | 口头 | 光系统 | Photonics-assisted THz ISAC System Based on A Time-Frequency Efficient SF-LFM-OFDM Waveform | SF-LFM嵌入Z-OFDM的时频高效通感波形，光子辅助THz系统同时87.7 Gb/s与7 mm距离分辨 |
| W4C.3 | 特邀 | 芯片 | Large-Scale True-Time Delay Beamforming for Integrated Sensing and Communications | 无物理延迟线的准真时延大规模波束成形，1×16天线阵实现厘米级雷达成像与Gb/s通信 |
| W4C.4 | 口头 | 芯片 | 310Gbps Integrated Sensing and Communication Dual-Polarization IM/DD Photonic THz System | 300 GHz双偏振IM/DD光子THz通感一体，310.4 Gb/s、频谱效率8.18 b/s/Hz，免训练测距精度2.7 cm |
| W4C.5 | 口头 | 光系统 | Experimental Demonstration of a Photonics-Assisted mmWave ISAC System Using ODDM Waveform | ODDM波形光子辅助毫米波通感一体系统，23 Gb/s、传感分辨3 cm |

### FSO

51 篇 · 自由空间/卫星/可见光/光无线

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M1H.1 | 口头 | 光系统 | Over-3-Tb/s/λ Free-Space MIMO Transmission Under Diffraction with Geometric Mode-Division Multiplexing | 几何模分复用(GMDM)克服衍射限制，多孔径单模发射，140 GBd三模单波长FSO净3.6 Tb/s |
| M1H.2 | 高分 | 光系统 | Coherent Free-Space Optical Communications with Concurrent Turbulence Characterization in a Terrestrial Urban Link | 4.6 km城市FSO链路19天湍流测量与相干通信联合实验，给出湍流对光纤耦合相干系统影响的实证 |
| M1H.3 | 口头 | 光系统 | Field Demonstration of an SDN-enabled 0.48 Tb/s Hybrid Coherent/IM-DD 0.75 km FSO/Fiber System | SDN控制的混合相干/IM-DD 0.75 km FSO/光纤现场系统，实时重配格式/波特率/波长/路径，0.48 Tb/s、亚毫秒切换 |
| M1H.5 | 口头 | 芯片 | Silicon Vector Optical Phased Array with Polarization Multiplexing and Wavelength Selectivity for 100 Gbps Free Space Coherent Optical Communication | 偏振复用、波长选择的硅矢量光学相控阵，实现100 Gb/s星间相干FSO与相干合束 |
| M3D.1 | 口头 | 芯片 | Circular-Grating Optical Phased Array for On-Chip Tunable OAM Beam Generation | 圆形光栅光学相控阵片上可调OAM光束发生器，1500–1630 nm稳定多阶OAM |
| M3D.2 | 口头 | 芯片 | Multi-aperture coherent beam analyzer implemented by an integrated mesh of Mach–Zehnder interferometers | 集成MZI网格作多孔径相干光束分析仪：波前测绘、空间相干估计与相位漂移补偿，用于通感一体 |
| M3D.3 | 特邀 | 芯片 | Integrated Optical Phase Arrays for Terrestrial Free-Space Optical Communication | 特邀：地面FSO的挑战与集成光学相控阵(OPA)缓解方案，片上OPA封装成功能模块 |
| M3D.5 | 口头 | 芯片 | Flat-Top Beam Shaping in the Far-Field Using On-Chip Fourier-Transform Optical Phased Arrays | 无源片上傅里叶变换OPA芯片，远场生成方形平顶光束，免外部透镜 |
| M3H.1 | 口头 | 光系统 | Experimental Demonstration of Kilometer-Scale Low-Complexity Multi-Gigabit VLC | 450 nm激光(0.1 W)实现1.2 km、6 Gb/s可见光通信，最长的多Gb/s IM/DD VLC |
| M3H.2 | 口头 | 器件 | Demonstrating 80 Gb/s Optical Wireless Communication Using A Multi-Aperture VCSEL and A Multi-Mode Fiber-Coupled Receiver for Next-Generation LiFi Connectivity | 940 nm单模多孔径VCSEL+多模光纤耦合接收，<5 mW光功率实现>80 Gb/s光无线(LiFi) |
| M3H.3 | 高分 | 光系统 | 516Tb/s MIMO-Free Mode/Wavelength Division Multiplexing Optical Wireless Communication System | S+C+L 319波长×免MIMO 3模复用的光无线系统(1.8 m)，容量516 Tb/s（纪录） |
| M3H.4 | 口头 | 光系统 | Experimental demonstration of fractional vortex communications with free-space propagation | 首次实验演示分数涡旋光自由空间传播复用/解复用，k空间模式解调保持正交性 |
| M4A.7 | 口头 | 算法 | Digital Twin-based Quality-of-transmission Estimation for Inter-satellite All-optical Networks | 基于光探测的数字孪生QoT估计用于星间全光网络，测试床模拟Starlink轨道动态 |
| Th1E.1 | 口头 | 光系统 | Full-Duplex mmWave/FSO Transmission over Shared Aperture with Optical Focal Plane Array Feed | 多芯光纤馈电焦平面阵列共享孔径的全双工毫米波/FSO传输，10 Gb/s FSO+26.5/33.7 GHz OFDM |
| Th1E.2 | 口头 | 光系统 | Experimental monitoring and data-driven modelling of outdoor FSO links | 800 m户外FSO链路60天、1 ms分辨率闪烁与偏振连续测量及数据驱动建模 |
| Th1E.3 | 口头 | 光系统 | On Irradiance Distributions for Weakly Turbulent FSO Links: Log-Normal vs. Gamma-Gamma | 实验表明弱湍流FSO辐照度分布用Gamma-Gamma模型比对数正态更准确 |
| Th1E.4 | 口头 | 光系统 | Bidirectional 3-km FSO Transmission Using Multi-Aperture Space Diversity and Digital Subcarrier Combining | 数字子载波合并实现单孔径与多孔径终端间双向3 km FSO空间分集，24小时评估 |
| Th1E.5 | 口头 | 光系统 | Experimental Demonstration of Probabilistically Shaped QAM Signals in a Mid-Infrared FSO Link Under Fog Conditions | 雾天4.5 µm中红外FSO链路中PS-16QAM 2 Gb/s（整形增益~0.4 dB）与PS-64QAM 3 Gb/s |
| Th1E.6 | 口头 | 光系统 | Time-Interleaved Joint Spread-Spectrum Enabled Ultra-Long-Range Ultraviolet Communication | 时间交织联合扩频的紫外LED准视距通信，2100 m/109 kb/s（纪录），昼夜免对准 |
| Th1E.7 | 口头 | 器件 | High-speed, High-sensitivity Mobile FSO Link based on Avalanche Photodetector Array | 高速高灵敏APD阵列空间分集接收的移动FSO系统，视场26.7°，灵敏度−3 dBm |
| Th1G.5 | 口头 | 器件 | Ethernet-over-OWC Using VCSELs: Transparent Gigabit Links with Low Latency and Robust Alignment Tolerance | VCSEL-PIN与商用器件实现1 m双向1 Gb/s以太网光无线，无放大透明、时延<25 ns、厘米级对准容差 |
| Th2A.24 | 海报 | 网络 | Multipath Protection between Ground Stations Based on Virtual Concatenation in Optical Satellite Networks | 光卫星网络地面站间基于虚级联的多路径保护，阻塞率降14.9% |
| Th2A.28 | 海报 | 算法 | Turbulence-resilient all-optical classifier by integrating diffractive deep neural networks with MPLC at the communication wavelength | 衍射深度神经网络+MPLC的抗湍流全光分类器（通信波长MNIST） |
| Th2A.66 | 海报 | 光系统 | Demonstration of a 300-GHz 272-Gbps Hybrid THz/FSO Transmission System Based on 2×4 MIMO-PDM and a Shared Transmitter | 首个300 GHz THz/FSO混合系统，共享发射机+2×4 MIMO-PDM，15 m总速率272 Gb/s |
| Th2A.69 | 海报 | 光系统 | Free-Space Same-Wavelength Transmission of Optical Frequency and Communication Signals | 自由空间同波长共传光频信号与通信信号，100 Gb/s DP-QPSK，频率不稳定度1.47×10⁻¹⁷@1 s |
| Th2A.70 | 海报 | 网络 | Cloud-Aware Reinforcement Learning-Based HAPS Trajectory Optimization in Hybrid FSO/RF Systems Using Rateless Coding | 云感知深度强化学习优化高空平台(HAPS)轨迹，无速率编码实现FSO/RF软切换 |
| Th2A.71 | 海报 | 光系统 | Flat-Top Beam Transmission Mitigating Scintillation and BER Fluctuations in Underwater Optical Links under Longitudinally Uniform Turbulence | 水下纵向均匀湍流中平顶光束较高斯光束抑制闪烁与BER波动、延长距离 |
| Th3E.6 | 特邀 | 网络 | Interoperability in optical space networks | 特邀：光空间网络互操作性——HydRON技术演示与ESTOL多厂商终端互通规范 |
| Th4B.1 | PDP | 光系统 | Aircraft to Geostationary Satellite Optical Links - First Results from the UltraAir Flight Test Campaign | UltraAir飞行试验：喷气式飞机与地球同步卫星间激光链路捕获跟踪与相干通信首批结果 |
| Tu2H.5 | 口头 | 器件 | Imaging APD Receiver for Multi-Gbit/s Optical Wireless Communication with Angular Diversity | 9个VCSEL阵列+12×12成像APD阵列，像素选择实现角度分集光无线，20 cm净4.395 Gb/s（首次） |
| Tu2H.6 | 口头 | 器件 | Semi-Transparent CdTe Solar Panels for Optical Wireless Communications | 首次演示半透明CdTe太阳能板(20%/50%透明度)作光无线接收机，对角度/横向失准鲁棒 |
| Tu3F.1 | 口头 | 网络 | Pre-Load-Balancing Against SGL Attenuation in Optical Satellite Networks | 光卫星网络中针对星地链路衰减的预负载均衡算法，业务中断降53.4%、时延抖动降39.81% |
| Tu3F.2 | 口头 | 网络 | Leveraging Network Diversity for Capacity Maximization in European Optical GEO Feeder Systems under Realistic Optical Turbulence | 基于欧洲25个站点一年湍流数据，利用网络分集+自适应光学优化GEO馈电光网络容量 |
| Tu3F.3 | 口头 | 网络 | Mobile Orbital Domain-based Hierarchical Routing in Satellite Networks | 卫星网络基于移动轨道域的分层路由，提升路由可扩展性与效率 |
| Tu3F.4 | 口头 | 网络 | Orbit-aware Routing Framework for Inter-Satellite All-Optical Networks | 星间全光网络轨道感知路由（优先同轨链路、选地面可见时间最长卫星），Starlink星座仿真 |
| Tu3F.5 | 口头 | 网络 | Proactive Handover for Latency-sensitive Applications in Optical Satellite Networks | 光卫星网络时延敏感业务主动切换策略，传播时延降39.06% |
| Tu3F.6 | 口头 | 网络 | Forecasting-Based Path Precomputation to Reduce APT Delays in Optical Satellite Networks | 预测请求的路径预计算缓解光卫星网络ATP(捕获跟踪瞄准)时延，最多降33.16% |
| Tu3F.7 | 特邀 | 网络 | Non-Terrestrial Networks: Time-Variant Impairments and Recovery Strategies Upon Outages | 非地面网络(NTN)中光纤设备对FSO时变损伤的表征与中断恢复策略 |
| Tu3H.1 | 口头 | 光系统 | Design of FSOC Terminal with Simplified Optical Axis Self-Calibration | 利用环境光的FSO终端光轴自校准，粗偏差由11.70降到1.05 mrad，2 km跨湖验证 |
| Tu3H.2 | 口头 | 器件 | 120° wide-FoV, 40-Gbps high-date-rate, short-range laser communication using avalanche PD array and spatial diversity signal processing | APD阵列+空间分集DSP的宽视场(120°)短距激光通信，最高40 Gb/s |
| Tu3H.6 | 口头 | 芯片 | Enhanced Field-of-View Using Integrated Waveguide-Confined Receiving Antenna for Indoor Optical Wireless Communication Systems | 集成波导限制接收天线扩大室内光无线视场，窄波束下12°内>28 Gb/s，超窄波束支持>70 Gb/s |
| W2A.29 | 海报 | 芯片 | On-Chip Reconfigurable Wavefront Shaper for Precise Spatial and Polarization Control | 可重构硅光处理器处理无序散斑输入，自配置精确操控输出波前空间与偏振分布 |
| W2A.61 | 海报 | 芯片 | Monolithic Integration of Metasurface with Photonic-Crystal Surface-Emitting Laser (PCSEL) for Beam Manipulation in Free Space Optical Communication | 单片集成超表面的PCSEL生成特定角度左/右旋圆偏振，每偏振通道FSO 1.88 Gb/s |
| W2A.62 | 海报 | 算法 | Digital Estimation of Doppler Shift with Gardner Timing Error Detector for Coherent Optical Satellite Communications | 利用多普勒频移与Gardner定时误差检测相关性的频偏估计，用于相干卫星光通信，估计范围更宽 |
| W2A.63 | 海报 | 算法 | Nonlinearity Mitigation for Coherent Ground-to-Satellite Optical Links | 卫星高功率光放大器非线性DSP缓解，地-星相干链路可接受损耗增加6 dB |
| W2A.64 | 海报 | 光系统 | Optical Wireless Communication Using an Arbitrarily Shaped “Bottle” Beam Array | 复振幅调制任意形状“瓶”光束阵列绕开遮挡，三波长两组播540 Gb/s 16QAM光无线 |
| W2A.65 | 海报 | 光系统 | Hybrid FSO/RF Communication System Enabled by PDOA-Based Coarse Pointing and MCF-Assisted Fine Alignment | PDOA粗指向+MCF辅助精对准的FSO/RF混合系统，户外自动对准稳定高速通信 |
| W2A.66 | 海报 | 算法 | Sensor-Free Wavefront Compensation for Free-Space Optical Communication | 发射端无传感器反馈波前补偿湍流，FSO传输效率提升>12倍 |
| W2A.67 | 海报 | 光系统 | EKF-Based Polarization Demultiplexing for Multi-Path Free Space Coherent Optical Communication | 多路径EKF偏振解复用用于多路径自由空间相干通信，免每路偏振控制器 |
| W2A.68 | 海报 | 器件 | Impact of Space Radiation-Induced Optical Transients in Ring Modulators on IM/DD Links for Satellite Applications | 空间辐射致微环调制器光瞬态对卫星IM/DD链路的影响评估 |
| W2A.70 | 海报 | 光系统 | Experimental Demonstration of Power-efficient ACO-OTFS in an Actively Phase-Controlled 2D Beam Steering OPA-based Cooperative FSO Communication System | 主动相控2D波束偏转OPA中继的协作FSO系统，节能ACO-OTFS较ACO-OFDM增益~4 dB |
