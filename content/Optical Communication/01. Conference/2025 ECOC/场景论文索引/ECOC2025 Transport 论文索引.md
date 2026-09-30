---
title: "ECOC2025 Transport 论文索引"
tags:
  - ECOC2025
  - 论文索引
---

ECOC 2025 中归入 **Transport**（相干、海缆、长途、多波段、SDM、空芯光纤、光网络智能化）的论文 **173** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）和场景。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2025 ECOC/index|2025年 ECOC 论文专题洞察]]

> [!summary] 关键结论
> 容量纪录集中爆发：G.654 光纤 430.2 Tb/s（PDP）〔Th.03.02.3〕、现网随机耦合 4 芯 927.7 Tb/s〔M.03.05.2〕、568.8 Tb/s × 5166 km〔M.03.05.1〕、S+C+L 2000 km 105.6 Tb/s〔Tu.03.05.2〕、单波 2.52 Tb/s〔Th.03.02.1〕、400 GBd 全相干 QAM〔Th.03.01.5〕；空芯光纤 0.052 dB/km（PDP）〔Th.03.01.1〕、1 Tb/s/λ × 10714 km〔W.03.05.5〕；网络侧 LPM 40 m 分辨率〔Th.03.03.2〕、LLM Agent 现网自治〔M.03.01.3〕、Meta 骨干 1600ZR+ 点对点化〔Th.02.06.4〕。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#HCF\|HCF]] | 15 | 空芯光纤：制备、损耗、熔接、传输与部署 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#AI光网络\|AI光网络]] | 30 | 数字孪生、LLM/智能体、ML、纵向功率监测与故障诊断 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光系统建模\|光系统建模]] | 8 | GN/EGN、非线性与 SRS 模型、QoT 建模 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#高波特率器件\|高波特率器件]] | 11 | 高波特率调制器/探测器/驱动/光 DAC |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光放与多波段\|光放与多波段]] | 25 | EDFA/BDFA/拉曼/参量放大、S/U/E/O 多波段 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#SDM光纤\|SDM光纤]] | 26 | 多芯/少模/OAM 光纤与 SDM 传输 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#相干DSP与编码\|相干DSP与编码]] | 26 | 相干 DSP、MIMO、概率整形、FEC、相噪/定时 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光网络架构与控制\|光网络架构与控制]] | 27 | ROADM/OXC、规划、SDN 控制、可插拔组网 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光纤与测试\|光纤与测试]] | 5 | 光纤本体、连接、测量表征 |

**二级专题 × 场景**

| 二级专题 | DCI | 城域 | 长途 | 海缆 | 通用 |
|---|---|---|---|---|---|
| HCF | – | – | 3 | 1 | 11 |
| AI光网络 | – | 2 | – | 1 | 27 |
| 光系统建模 | – | – | 1 | – | 7 |
| 高波特率器件 | – | 1 | 1 | – | 9 |
| 光放与多波段 | – | 1 | 5 | 2 | 17 |
| SDM光纤 | – | – | 2 | 2 | 22 |
| 相干DSP与编码 | – | 1 | 3 | 1 | 21 |
| 光网络架构与控制 | 1 | 4 | 1 | – | 21 |
| 光纤与测试 | – | – | – | 1 | 4 |

## HCF

15 篇 · 空芯光纤：制备、损耗、熔接、传输与部署

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th.03.01.1 | PDP | 器件 | 通用 | 40 km, 0.052 dB/km and 83 km, 0.076 dB/km in Interstitial-Tube-assisted Hollow-Core Fibre | 间隙管辅助DNANF空芯光纤：40 km损耗0.052 dB/km（纪录最低），单次拉制83 km(0.076 dB/km) |
| Th.03.01.2 | PDP | 器件 | 通用 | First Triple Nested Antiresonant Nodeless Hollow Core Fiber (TNANF) Achieving 0.25 dB/km Loss with Small 145/250 µm Glass/Coating Diameters | 首个三重嵌套反谐振空芯光纤(TNANF)，145/250 µm标准尺寸，损耗0.25 dB/km，弯曲损耗创纪录 |
| Th.03.02.2 | PDP | 光系统 | 长途 | Real-Time, Fully-Loaded C-band, Low-Latency, Long-Haul Transmission over Hollow-Core Fiber | 空芯光纤实时满载C波段长距传输（~120 km跨段）：25.6 Tb/s@1439 km，>6000 km仍10.3 Tb/s，最远11154 km |
| Tu.04.01.1 | 特邀 | 光系统 | 通用 | Field-deployed anti-resonant hollow-core fibre cable | 特邀：低损反谐振空芯光纤(AR-HCF)的先进制备、成缆与现场部署总结 |
| Tu.04.01.2 | 口头 | 器件 | 通用 | Support Tube Hollow-Core Fiber with 0.05 dB/km Attenuation | 支撑管空芯光纤(ST-HCF)：9.1 km损耗0.05±0.01 dB/km，733 km批量平均0.147 dB/km |
| Tu.04.01.3 | 口头 | 器件 | 通用 | Anti-Reflection Coated SSMF to Hollow-Core Fiber Splicing with Low-Loss and Low Back-Reflection | 距AR镀膜1 mm处熔接的SSMF-空芯光纤连接，损耗<0.3 dB、背反射<−33 dB且镀膜不退化 |
| W.02.01.03 | 海报 | 器件 | 通用 | Nitrogen dioxide contamination in as-drawn hollow-core fibre | 刚拉制空芯光纤中的二氧化氮污染：UV/可见波段吸收，浓度达0.1 µmol/cm³ |
| W.02.01.08 | 海报 | 器件 | 通用 | CO₂ Elimination in Hollow-Core Fibre via Post-Processing | 空芯光纤后处理消除CO₂吸收并建立内部正压，保障C+L公里级传输 |
| W.02.01.61 | 海报 | 算法 | 通用 | Hollow-Core Fiber Transmission: Impact of CO2 Absorption and its Mitigation by Waveform Design | NANF空芯光纤CO₂吸收凹陷对140 GBd传输的影响，熵加载OFDM较单载波Q提升0.4 dB |
| W.02.01.83 | 海报 | 光系统 | 海缆 | The Case for a DNANF 1Pb/s Trans-Atlantic Submarine Cable | 论证DNANF空芯光纤1 Pb/s跨大西洋海缆：双向传输+跨段理论可达200 km |
| W.02.01.106 | 海报 | 网络 | 长途 | Optimal Placement of Hollow-Core Fiber Spans to Realize Cost-Effective and High-Capacity Optical Transport Networks | 网状网中选择性升级为空芯光纤跨段的最优放置方法，以最少HCF提升容量/距离 |
| W.03.05.1 | 口头 | 光系统 | 通用 | Ultra-wideband S+C+L Transmission of 137.6 Tb/s over 40.4 km of Support Tube Hollow Core Fiber using Bismuth Doped Fiber Amplifiers and Constellation Shaping | 40.4 km支撑管空芯光纤S+C+L传输(BDFA+EDFA)，PCS-QAM，AIR>137.6 Tb/s |
| W.03.05.2 | 口头 | 器件 | 通用 | Characteristics and Impacts of CO2 Absorption Effects in Hollow Core Fiber (HCF) Transmission Systems | 空芯光纤基线损耗与CO₂吸收线特性及温度依赖，100 km传输中L波段三家转发器均受明显损伤 |
| W.03.05.4 | 口头 | 光系统 | 通用 | 6 × 2.3 Tb/s Net Rate Transmission over 20.2 km of Ultra-low loss Hollow Core Fiber Using DP-16QAM Signalling and High Power Doped Fiber Amplifier | 20.2 km超低损(0.096 dB/km)空芯光纤6×2.3 Tb/s双载波DP-16QAM，高功率放大器入纤34 dBm |
| W.03.05.5 | 口头 | 光系统 | 长途 | 1-Tb/s/λ Transmission over Record 10714-km AR-HCF | 首次单通道1.001 Tb/s DP-36QAM-PCS在DNANF-5空芯光纤循环传输10714 km（纪录） |

## AI光网络

30 篇 · 数字孪生、LLM/智能体、ML、纵向功率监测与故障诊断

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M.03.01.2 | 口头 | 网络 | 通用 | LLM Assistant for TAPI Context and Client Code Translation | 基于LLM的TAPI上下文与客户端代码翻译中介，解决解耦光网络中编排器与OLS控制器间的TAPI解释不一致 |
| M.03.01.3 | 口头 | 网络 | 通用 | Field Trial of LLM-based Autonomous Network Management with AI-Agent in Real-time 400G/800G Elastic Optical Network | LLM+AI Agent自治网络管理在5节点400G/800G实时弹性光网络中的现场试验，OSNR裕量估计误差<0.5 dB |
| Th.01.05.2 | 口头 | 算法 | 通用 | Combining Machine Learning and the GN Model for Fast NLI Prediction in Dispersion-Managed Links | 机器学习+GN模型的空间解耦模型，实时准确预测色散管理链路的非线性干扰 |
| Th.02.01.1 | 口头 | 网络 | 通用 | LP-VAE: Real-Time and Parameters’ Uncertainty-tolerant Launch-Power Optimization for UWB ISRS-Impaired Optical Links | LP-VAE：概率ML实时发射功率优化，适用ISRS受损超宽带链路，对参数不确定鲁棒 |
| Th.02.01.2 | 口头 | 算法 | 通用 | Generalizability of ML-Based Classification of State of Polarization Signatures Across Different Bands and Links | 基于SOP特征的ML事件分类跨波段/跨链路泛化性评估：系统内准确率98.6%，跨系统泛化有限 |
| Th.03.03.2 | PDP | 算法 | 城域 | Tens-of-Metre Resolution Longitudinal Power Monitoring over 302-km Fibre Link | 302 km链路纵向功率监测(LPM)实现40 m空间分辨率（纪录），可定位局内跳线损耗 |
| Tu.02.12.2 | Demo | 网络 | 通用 | LLM-Powered Desktop AI-Assistant for Network Operations Employing Multi-Agent System with Vision-Language Integration | LLM多智能体+视觉语言模型的桌面AI助手，自动操作网络可视化与管理软件 |
| Tu.02.12.5 | Demo | 网络 | 通用 | Novel Telemetry Data Collection and Closed-Loop Operations for End-to-End Optical Access and Transport Networks with Guaranteed-Quality Connectivity Service Assurance | 端到端光接入与传送网的标准模型遥测与闭环控制，按实时QoS升级保障服务 |
| Tu.04.06.3 | 口头 | 网络 | 通用 | Expertise-Guided LLM Agent Realizing Autonomous Optical Power Optimization in Field-deployed Networks | 融合专家知识的LLM Agent实现现网光功率自治优化，平均约4次调整达最优QoT |
| Tu.04.06.5 | 特邀 | 算法 | 通用 | Digital Twins Beyond C-band Using GNPy | GNPy多波段数字孪生：Kerr非线性与SRS求解器在C+L传输中得到仿真与实验验证 |
| W.01.06.2 | 口头 | 网络 | 通用 | Extreme PPE Capability and Its Application for End-to-End Performance Diagnosis of Millisecond-Level Transients | 功率分布估计(PPE)极限能力：200 kHz监测速率、0.1 dB精度，捕获加/掉波毫秒级瞬态 |
| W.01.06.3 | 口头 | 算法 | 通用 | Impact of Carrier Phase Recovery on Longitudinal Power Monitoring | 载波相位恢复窗口过小对纵向功率监测(LPM)造成系统/统计误差，合适窗口可在300 kHz线宽下稳定 |
| W.01.06.4 | 口头 | 算法 | 通用 | Robust Fibre Longitudinal Power Monitoring with Few Measurements using Two-stage Sparse Regularization | 两阶段稀疏正则化的光纤纵向功率监测，无需链路先验，少量测量即可检出0.72 dB异常损耗 |
| W.01.06.5 | 口头 | 算法 | 通用 | In-band Power Ripple Detection using Longitudinal Power Monitoring | 基于纵向功率估计的带内功率纹波检测（子带功率估计/参考扫描），识别放大器或滤波器异常 |
| W.02.01.100 | 海报 | 算法 | 通用 | Digital Twin for Estimating QoT Statistics in Presence of PDL and Transceiver Imperfections | 物理数字孪生预测含PDL与收发机缺陷光路的QoT统计分布，最差SNR预测精度提升0.73 dB |
| W.02.01.101 | 海报 | 网络 | 通用 | Experimental Demonstration of Improved Deconvoluted Correlation Based Longitudinal Power Monitoring | 改进去卷积相关纵向功率监测（交叉偏振调制），数据需求减少1.5–2倍 |
| W.02.01.105 | 海报 | 算法 | 通用 | A Simple Fiber Anomaly Detection Approach via Band Power in S+C+L-Band Optical Transmission Systems | 仅用各波段放大器入口PD功率实现S+C+L系统光纤异常定位与衰减估计 |
| W.02.01.107 | 海报 | 网络 | 通用 | On-Chip Physical Layer Optical Module Identification Using a Photonic Fingerprint Device | 逆向设计光子指纹器件+CNN实现片上光模块物理层身份识别，准确率98.75% |
| W.02.01.108 | 海报 | 算法 | 通用 | Localization and estimation of multiple PDL anomalies by monitoring a single SNR distribution at the receiver side | 仅监测接收端SNR分布即可定位和量化多个异常PDL（实验不确定度0.2 dB） |
| W.02.01.169 | 海报 | 网络 | 海缆 | Field Demonstration of Digital Twin–enabled Launch Power Profile Optimization in a Submarine SDM Optical Network | 数字孪生驱动现网海底SDM网络发射功率自治优化，约25 s收敛、MAE 0.49 dB |
| W.02.01.170 | 海报 | 网络 | 通用 | OptiMA: Collaborative Multi-Agent Framework for Modelling and Controlling Raman Amplifier in Intelligent Optical Networks | OptiMA：拉曼放大器建模与控制的LLM多智能体协作框架，任务完成率100%，收敛加速约50% |
| W.02.01.171 | 海报 | 网络 | 通用 | Online-Trained Adaptive OSNR Equalization in C+L-Band Optical Networks | 在线训练神经网络实现116通道C+L网络自适应OSNR均衡，14次迭代RMSE<0.4 dB |
| W.02.01.172 | 海报 | 网络 | 通用 | AI-Driven Hitless Network-Level Energy Optimization with Reliability-Aware Bandwidth Reservation Algorithm and Field Trial | 可靠性感知小波-LSTM带宽预留实现无损网络级节能，现网试验节能12.3%且零丢包 |
| W.02.01.173 | 海报 | 网络 | 通用 | Multi-Agent LLM-powered AI for Autonomous Optical Power Commissioning of OMS Links | LLM多智能体+网络数字孪生自主完成WDM OMS链路功率开通调测（功率/OSNR均衡） |
| W.02.01.174 | 海报 | 网络 | 通用 | Experimental Demonstration of Proactive Inline-EDFAs’ Gain Degradation Detection and Localization in Optical Networks | 基于相干接收机数据的ML框架前瞻性检测与定位在线EDFA增益劣化，定位准确率>90% |
| W.02.01.176 | 海报 | 网络 | 通用 | Beyond Performance: Explaining Non-Intuitive Deep Reinforcement Learning Actions in Elastic Optical Networks | 解释弹性光网络RMSA深度强化学习代理的非直观动作（改进SVERL可解释框架） |
| W.02.01.180 | 海报 | 算法 | 通用 | Experimental Analysis of Adaptive ML Classifiers for Dynamic Detection of Emerging Physical-Layer Attacks | 三种ML分类器检测光网络物理层攻击的实验评估，未见攻击平衡准确率达0.936 |
| W.03.06.2 | 口头 | 算法 | 城域 | Spectrally-Sliced Longitudinal Power Profile Estimation | 分谱片纵向功率分布估计(PPE)：提升精度、降复杂度并获得频率分辨功率演化，900 km检测通道内倾斜 |
| W.03.06.3 | 口头 | 网络 | 通用 | Pilot-tone Enabled QoT Awareness and Anomaly Localization in Dynamic Optical Transport Networks | 分布式导频音监测主动校准QoT估计，实现动态光传送网性能劣化感知与异常定位 |
| W.04.01.3 | 口头 | 算法 | 通用 | Leveraging Shared Data and Models for ML-Based QoT Estimation: Toward Standardized and Generalizable Models | 首个用四家机构合成与实测(含现网)数据训练ML QoT估计器的研究，探索统一可泛化模型 |

## 光系统建模

8 篇 · GN/EGN、非线性与 SRS 模型、QoT 建模

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Tu.01.05.1 | 特邀 | 算法 | 长途 | Closed-Form EGN Models and Launch Power Optimization in Multi-band Systems | 闭式EGN模型用于多波段(CLS/CLSE) 1000 km链路发射功率与拉曼泵浦联合优化 |
| Tu.01.05.2 | 口头 | 器件 | 通用 | Nonlinear Interference Investigation in Coupled-Core Multi-Core Fibers with Stimulated Raman Scattering and Mode Dispersion | 耦合芯多芯光纤中SRS与空间模色散对非线性干扰的影响：SRS倾斜与SMD降NLI基本独立 |
| Tu.01.05.3 | 口头 | 算法 | 通用 | A Temporal Gaussian Noise Model for Equalization-enhanced Phase Noise | 均衡增强相噪(EEPN)的时变高斯噪声模型，准确预测高波特率系统的突发性失真 |
| Tu.01.05.4 | 口头 | 算法 | 通用 | Experimental Validation of Closed-form EGN Model at Zero-dispersion Wavelength for O-band Coherent Transmission | O波段零色散波长处相干WDM传输实验验证闭式EGN模型，FWM与XPM为主要非线性来源 |
| Tu.01.05.5 | 口头 | 算法 | 通用 | Fast and stable method for computation of power profiles in transmission systems with high-power backward Raman pumping | 高功率后向拉曼泵浦超宽带系统功率分布的快速稳定无参数计算方法，适用E+S+C+L预加重优化 |
| W.02.01.75 | 海报 | 算法 | 通用 | A General Nonlinear Model for Arbitrary Modulation Formats in the Presence of Inter-Channel Simulated Raman Scattering | 四维非线性模型扩展纳入信道间SRS，准确预测4D调制与概率整形星座 |
| W.02.01.96 | 海报 | 网络 | 通用 | QoT Impairments Induced by Statistical Filtering Variations with a Realistic Equalizer | 含真实分数间隔均衡器的ASE受限链路中滤波统计波动带来的QoT代价蒙特卡洛分析 |
| W.02.01.102 | 海报 | 算法 | 通用 | Availability Estimation of External IP-Optical Network Connections Using Bayesian Modeling | 贝叶斯模型+“超链接”估计多域IP-光网络外部连接可用性 |

## 高波特率器件

11 篇 · 高波特率调制器/探测器/驱动/光 DAC

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M.02.03.2 | 口头 | 芯片 | 通用 | Hybrid Integrated Wavelength Tunable Laser Based on Sampled Multimode Waveguide Gratings | 基于游标采样多模波导光栅的混合集成可调谐外腔激光器，调谐范围>58 nm，SMSR 45 dB，输出12 mW |
| Th.02.02.2 | 口头 | 芯片 | 通用 | High-Performance Heterogeneously Integrated Coherent Optical Sub-Assembly Enabling 130 Gbaud DP-QPSK Transmission | TFLN相干驱动调制器与硅光ICR共封装的异质集成相干光组件，带宽>75 GHz，131 GBd DP-QPSK |
| Th.03.01.5 | PDP | 光系统 | 通用 | 400 GBd 32QAM Transmission Using RF-Synchronized Dark-Soliton Microcombs for Optical Arbitrary Waveform Generation (OAWG) | RF同步暗孤子微梳实现>400 GHz光任意波形生成，400 GBd 16/32QAM（全相干QAM最高符号率） |
| Th.03.02.1 | PDP | 光系统 | 长途 | Net bitrate of 2.52-Tb/s/λ 120-km Single-channel Transmission and >2-Tb/s/λ 1040-km WDM Transmission using InP-DHBTbased all-electronically multiplexed 248-GBd transmitter | 自研InP-DHBT电域带宽复用248 GBd发射机，单波净2.52 Tb/s@120 km，首次>2 Tb/s/λ全C波段>1000 km WDM |
| Tu.04.03.4 | 口头 | 芯片 | 通用 | High Output Power, 128 GBaud Monolithic InP Integrated Transmitter Fabricated in an Open Access Foundry | 开放代工厂制造的单片InP发射机（快速可调窄线宽激光器+MZM+SOA），128 GBd，出纤功率3 dBm |
| W.02.01.15 | 海报 | 芯片 | 通用 | Monolithic Multi-Wavelength Mode-Locked DFB Laser Based on Waveguide Bragg Grating Microcavities | 波导布拉格光栅微腔单片多波长锁模DFB激光器，57.4 GHz间隔3/4波长 |
| W.02.01.17 | 海报 | 器件 | 城域 | Miniature Self-injection-locked Laser with 5.7-mHz Lorentzian Linewidth | 锥形光纤耦合高Q晶体微腔的微型自注入锁定激光器，洛伦兹线宽5.7 mHz |
| W.02.01.18 | 海报 | 器件 | 通用 | High-Power, Narrow-Linewidth Multi-Channel Interference Widely Tunable Lasers Based on Butt-Joint Regrowth | 对接再生长多通道干涉(MCI)可调激光器，>120 mW、线宽<90 kHz、调谐>52 nm |
| W.02.01.46 | 海报 | 芯片 | 通用 | Demonstration of a 1-Tb/s Coherent Receiver Using Silicon Photonic Wavelength Demultiplexed 90° Optical Hybrid | 硅光90°混频器级联MZI格型滤波器的8λ×200 GHz DWDM相干接收机，检测1 Tb/s（25 GBd 32QAM） |
| W.02.01.73 | 海报 | 器件 | 通用 | First Net 800 Gbps/λ 120 Gbaud DP-16 QAM C-Band Coherent | 首次C波段120 GBd DP-16QAM净800 Gb/s相干传输，封装钛酸钡(BTO) DP-IQM集成驱动；非线性DSP达933 Gb/s |
| W.03.02.2 | 口头 | 芯片 | 通用 | Scalable Multi-band Narrow Linewidth Operation by a Single-chip Tunable Laser with InP/Si Heterogeneous Integration | 芯片-晶圆键合InP/Si异质集成双增益单芯片可调激光器，首次覆盖C+L(104.4 nm)，线宽<50 kHz |

## 光放与多波段

25 篇 · EDFA/BDFA/拉曼/参量放大、S/U/E/O 多波段

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th.01.01.2 | 口头 | 器件 | 通用 | Performance of PM Holmium Doped Fiber Amplifiers with Hybrid Pumping at 1150nm and 1860nm | 2050 nm保偏掺钬光纤放大器，1150 nm带外同向+1860 nm带内反向混合泵浦，NF 3 dB、多瓦输出 |
| Th.01.01.3 | 口头 | 器件 | 通用 | Distributed Parametric Amplifier in Standard Single-Mode Fibre with Gain up to 44 dB and bandwidth up to 30 nm in O-band | 25 km标准单模光纤中O波段分布式参量放大，30 nm范围增益>20 dB、峰值44 dB，50G PAM4验证 |
| Th.01.01.4 | 特邀 | 器件 | 海缆 | Amplifier Technologies for Unrepeatered Systems | 特邀：无中继系统中的拉曼放大技术原理、限制因素及宽带化/新光纤趋势 |
| Th.01.02.1 | 口头 | 器件 | 通用 | High-gain Suspended Silicon Nitride Waveguide Amplifiers Enabled by Double-sided Er3+:Al2O3 Coating | 双面ALD Er:Al2O3包覆的悬空氮化硅掺铒波导放大器，净增益22.29 dB、片上输出12.51 dBm |
| Th.01.02.3 | 特邀 | 器件 | 通用 | Er Doped Photonic Integrated Circuits: From On-Chip Amplifiers, Tunable Low-Noise Lasers to Mode-Locked fs Sources | 特邀：掺铒光子集成电路——片上放大器、可调低噪激光器到飞秒锁模光源(离子注入Er:SiN) |
| Th.01.03.4 | 口头 | 器件 | 通用 | Design and Integration of a Two-Port C+L High Performance Amplifier in a Module | C+L扩展波段双端口SOA模块设计与封装，增益>15 dB、NF<7 dB、WDM输出18.6 dBm |
| Th.02.06.3 | 口头 | 光系统 | 长途 | On the Feasibility of SCL-Band Transmission over G.654.E-Compliant Long-Haul Fibre Links | 首次在G.654.E光纤上实现SCL波段长距传输，1552 km达100.8 Tb/s(GMI)，集中放大媲美G.652.D+分布拉曼 |
| Tu.01.01.1 | 口头 | 器件 | 通用 | Simplified Hybrid Core and Cladding Pumping Technique for Power-efficient Multi-core Fibre Amplifier | 单泵浦简化纤芯+包层混合泵浦的三包层4芯EDFA，C波段功率转换效率17.6%、每芯400 mW |
| Tu.01.01.2 | 口头 | 器件 | 通用 | High Power E-band Bismuth-Doped Fiber Amplifier | 双级高功率E波段掺铋光纤放大器，输出872 mW、小信号增益47.6 dB、NF 4.8–7 dB |
| Tu.01.01.3 | 口头 | 器件 | 通用 | FIFO-less Bidirectional Core-Pumped 4-core MC-EDFA Featuring with Multicore Isolator / Pump Combiner Hybrids | 无扇入扇出的双向纤芯泵浦4芯MC-EDFA，集成多芯隔离器/泵浦合束器，串扰−58.5 dB |
| Tu.01.01.4 | 口头 | 器件 | 通用 | EDFA-BDFA Cascaded S-band Amplification from 1452nm to 1526nm with Flat-Gain and Low Noise Figure by Placing 980nm Pumped EDFA First with Very High Population Inversion | EDFA先行(980 nm高反转)+BDFA级联S波段放大，1452–1526 nm平坦增益>25 dB，NF低至3.6 dB |
| Tu.01.01.5 | 特邀 | 器件 | 通用 | Designing Energy-Efficient Cladding-Pumped Multi-Core Erbium-Doped Fiber Amplifiers | 包层泵浦多芯EDFA的功率转换效率分析，利用多模泵浦二极管高电光效率可超越纤芯泵浦 |
| Tu.03.05.1 | 口头 | 光系统 | 海缆 | Real Time C-band Unrepeatered Transmission of 36.4 Tb/s in PCS-64QAM and 32 Tb/s in PCS-16QAM over 368 km and 407 km Respectively | 实时C波段无中继纪录：368.7 km传36.4 Tb/s(PCS-64QAM，52×700G)，407.9 km传32 Tb/s(80×400G) |
| Tu.03.05.2 | 口头 | 光系统 | 长途 | Long-Haul 2000-km Single-Mode Fibre Transmission with Net Bitrate of 105.6 Tb/s in S+C+L Band Using Low-Noise Forward-Pumped Distributed Raman Amplification | 低噪声前向泵浦分布拉曼(偏振交织窄纵模泵浦)+后向拉曼，S+C+L 2000 km净105.6 Tb/s |
| Tu.03.05.4 | 口头 | 光系统 | 长途 | 2000 km Coherent U-band Transmission using Recirculating loop with Distributed Raman Amplification | 分布拉曼放大实现创纪录2000 km U波段相干传输(23 GBd DP-QPSK，NZDSF循环环路) |
| Tu.04.05.2 | 口头 | 光系统 | 通用 | Experimental Evaluation of Throughput Gains from Distributed Raman Amplification in Ultra-Wideband ESCL Transmission | 分布式拉曼放大在超宽带ESCL传输中的吞吐增益量化：50/100/150 km分别提升1.5%/5.3%/40% |
| Tu.04.05.3 | 口头 | 算法 | 城域 | Transfer-Learning-Driven Neural Network Equalization for Ultra-High-Capacity 254.7-Tb/s over 200-km SSMF | 迁移学习神经网络均衡，S+C+L 19.8 THz DWDM在200 km SSMF上254.7 Tb/s(GMI)，SE 12.86 b/s/Hz |
| W.02.01.05 | 海报 | 器件 | 通用 | Factor of Two Improvement of Extended L-Band EDFA by Reflecting Out-of-Band ASE | 反射带外ASE使扩展L波段EDFA增益提升3.28 dB（效率提升一倍） |
| W.02.01.06 | 海报 | 器件 | 通用 | Fiber Optical Parametric Amplifier Tuneable across 590nm Range with Continuous Wave Output Power up to 4W | 光纤参量放大器在1303–1892 nm(590 nm)可调，CW输出最高4 W |
| W.02.01.07 | 海报 | 光系统 | 长途 | Digital Dispersion Pre-Compensation in Single Span Transmission Links Using Phase Sensitively Pre-Amplified Receivers | 相敏预放接收机配合数字色散预补偿，80 km 20 Gb/s BPSK NF 1.7 dB，优于EDFA 2.3 dB |
| W.02.01.10 | 海报 | 器件 | 通用 | 157-nm High-gain, Low-noise S-, C-, and Extend L-band Amplifier Using Cascaded Discrete Raman and Bismuth-doped Fiber Amplification | 掺铋光纤+光子晶体光纤级联离散拉曼放大，S/C/扩展L 157 nm带宽，净增益22.7 dB |
| W.02.01.13 | 海报 | 器件 | 通用 | S-Band Variable-Confinement Semiconductor Optical Amplifiers for High-Capacity Multi-Band WDM Systems | 纵向渐变可变限制因子S波段SOA，增益~27 dB、饱和输出18 dBm、NF<6 dB |
| W.02.01.74 | 海报 | 器件 | 通用 | Investigation of Nonlinear Impairments and their Compensation in Integrated SOA within High Bandwidth Coherent Driver Modulator | 高带宽相干驱动调制器(HB-CDM)内集成SOA的非线性损伤：高波特率/非高斯分布损伤更小，后补偿可消除>60% |
| W.02.01.104 | 海报 | 光系统 | 长途 | Comparison of Different Backward Raman Amplification Schemes for C+L Long-Haul Transmission Systems | C+L长途系统不同后向拉曼放大方案在性能、成本、功耗、放大器数量上的比较 |
| W.03.05.6 | 口头 | 光系统 | 通用 | Measurement and Analysis of the Power Consumption of Hybrid-Amplified SCL-band Links | 混合放大SCL波段链路功耗实测：多跨混合拉曼较集中放大每比特能耗最多降26% |

## SDM光纤

26 篇 · 多芯/少模/OAM 光纤与 SDM 传输

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M.02.01.3 | 口头 | 器件 | 通用 | Differential Group Delay Measurement in Spun Birefringent Uncoupled Multicore Fibers | 测量旋制(spun)双折射非耦合多芯光纤的局部双折射与DGD，证明合理设计的旋制可有效降低多芯光纤DGD |
| M.02.01.4 | 口头 | 器件 | 通用 | 0.3-dB-Loss SCF-to-MCF Power Splitter Based on a Biconical Splice Taper | 基于双锥熔接拉锥的单芯-多芯光纤功率分束器，损耗仅0.3 dB，并用宏弯后处理均衡各芯输出 |
| M.02.01.5 | 口头 | 器件 | 通用 | Fibre Fuse Propagation Characteristics and Threshold Power of Randomly Coupled Multi-core Fibre | 随机耦合多芯光纤中模式耦合引起的纵向功率起伏导致独特的光纤熔丝传播特性，给出熔丝阈值测量条件 |
| M.02.05.1 | 特邀 | 光系统 | 通用 | SDM Transmission Technologies Enabling Over-10-Tb/s SDM-MIMO Signals | 特邀：多Tb/s/λ级空间MIMO超信道SDM传输技术综述；现网12耦合芯光纤实现净455 Tb/s（现网最高） |
| M.02.05.2 | 口头 | 光系统 | 通用 | Joint Few-Mode O-band and Single-Mode C-Band Transmission Over a High Cut-Off Wavelength G.654 Compatible Fiber | 在G.654兼容高截止波长光纤中，O波段3模MIMO传输与C波段单模传输联合扩容 |
| M.02.05.3 | 口头 | 光系统 | 通用 | Inter-Core Crosstalk Estimation in Uniand Bi-Directional Multiband WDM Transmissions | 考虑受激拉曼散射与瑞利背向散射的耦合功率方程，估计多波段单/双向传输中多芯光纤芯间串扰 |
| M.03.05.1 | 口头 | 光系统 | 长途 | 568.8 Tb/s C+L-Band Transmission Over 5,166 km in a Standard-Cladding Diameter 19-Core Randomly-Coupled Multicore Fiber | 标准包层19芯随机耦合多芯光纤C+L波段环路传输5166 km，总吞吐568.8 Tb/s，容量距离积2.93 Eb/s·km（纪录） |
| M.03.05.2 | 口头 | 光系统 | 通用 | 19.2 THz S+C+L Transmission in a Field Deployed, Randomly-Coupled, Multicore Fiber | 现网随机耦合4芯光纤上S+C+L 19.2 THz带宽传输，吞吐927.7 Tb/s（现网纪录），首次在该类光纤中实现拉曼放大 |
| M.03.05.4 | 口头 | 光系统 | 通用 | Real-Time SDM-MIMO Transmission with 12-Coupled SDM Channels over Field-Installed Fibre Cable | 现网12耦合芯光缆FPGA实时SDM-MIMO传输68 km，降复杂度频域24×1 MIMO均衡 |
| M.03.05.5 | 口头 | 光系统 | 海缆 | Influence of Inter-core Crosstalk in High-capacity 205 to 359 km Unrepeatered Transmission over 2-Core MCF | 2芯MCF无中继205–359 km高容量传输，研究单/双向配置中芯间串扰损伤 |
| M.03.06.5 | 口头 | 器件 | 海缆 | Impact of Optical Loopback on Backward Crosstalk and Fault Localisation in Multi-Core Fiber Submarine Systems | 多芯海缆系统中光环回对后向串扰与故障定位的影响，证明无环回也可定位故障 |
| Th.02.04.1 | 口头 | 光系统 | 通用 | Real-time GPU-based 48-km 10-mode Transmission | 实时GPU处理的48 km渐变多模光纤10模传输，20个外差接收机+3 FPGA+GPU服务器 |
| Th.02.04.4 | 口头 | 算法 | 通用 | Partitioned MIMO Equalization with Mode-Group Specific Interface Resolution for SDM Transmission over 58.9 km 15-mode Fiber | 15模光纤58.9 km传输的五分区MIMO均衡，按模组耦合调整接口量化精度，接口吞吐降低49% |
| Th.03.02.3 | PDP | 光系统 | 通用 | 430 Tb/s GMI Data Rate Over a Standard G.654 Fiber Using Few-Mode O-Band and Single-Mode ESCL-Band Transmission | G.654光纤中O波段3模+E/S/C/L单模联合传输，30.1 THz带宽，430.2 Tb/s(GMI)纪录 |
| Th.03.02.4 | PDP | 光系统 | 通用 | Transmission over Randomly-Coupled Multi-Core Fiber Enabled by All-Optical MIMO Demultiplexing | 首次用硅光芯片全光MIMO解复用实现随机耦合4芯光纤传输(10 GBd PDM-QPSK，5 km) |
| W.01.01.2 | 口头 | 器件 | 通用 | Experimental Characterization of Mode-Dependent Stimulated Raman Scattering in a 15-Mode Fiber | 15模渐变光纤中模组分辨的受激拉曼散射测量，模组间SRS增益差达1.7 dB（波长相关MDL） |
| W.01.01.3 | 口头 | 器件 | 通用 | Investigation of Nonlinear Coupling and Parametric Interactions in Coupled Multi-Core Fibers | 耦合多芯光纤中线性/非线性耦合与参量相互作用，非线性响应对纵向变化耦合系数敏感 |
| W.01.09.4 | 口头 | 器件 | 通用 | Closed-Form Expressions for Nonlinearity Coefficients in Few-Mode Multicore Fibers | 弱/强混合随机耦合少模多芯光纤非线性系数的解析闭式表达，≥6空间模误差0.4% |
| W.02.01.01 | 海报 | 器件 | 通用 | Experimental Characterization of Stimulated Raman Scattering in Field-Deployed Coupled-Core Multi-Core Fibers | 首次实验表征现网耦合芯多芯光纤中的受激拉曼散射，增益系数与SMF相当 |
| W.02.01.04 | 海报 | 器件 | 通用 | Bending-Induced Birefringence in Uncoupled-Core Multi-Core Fibers | 非耦合多芯光纤弯曲致双折射：与曲率平方相关且依赖纤芯相对弯曲方向 |
| W.02.01.09 | 海报 | 器件 | 通用 | Random and External Twisting Effect on Power Coupling in Bent Coupled Multi-Core Fibres | 随机与外部扭转对弯曲耦合多芯光纤功率耦合的影响，为成缆设计提供参考 |
| W.02.01.54 | 海报 | 算法 | 长途 | Unreplicated Successive Interference Cancellation for MDL Effect Mitigation and Fast Convergence Enabling Long-haul Few-mode Transmission | 非复制连续干扰消除+RLS缓解MDL并快速收敛，MDM系统Q²提升1.4 dB |
| W.02.01.57 | 海报 | 算法 | 通用 | MIMO for Joint Compensation of Mode Coupling, Frequency Offset and Carrier Phase Noise for Optical Carrier-Asynchronous SDM System via Frequency-Domain Pilot Tones | 频域导频辅助MIMO联合补偿模式耦合、频偏与相噪，解决载波异步SDM系统MIMO失效 |
| W.02.01.78 | 海报 | 算法 | 通用 | Evaluation Method of Adaptive SDM-MIMO Equaliser based on the Quantitative Coupled Channel Dynamics | SDM光纤拉伸器定量全扰动耦合信道，评估自适应SDM-MIMO均衡器跟踪性能 |
| W.02.01.81 | 海报 | 光系统 | 通用 | 2 Tb/s/λ 3-mode Transmission over 54-km Few-Mode Fiber | 仅用盲均衡在54 km少模光纤实现3模2 Tb/s/λ传输（DSCM限制MIMO长度） |
| W.02.01.87 | 海报 | 光系统 | 通用 | Partial-MIMO Application for Mode Groups Transmission over 15-Mode and 6-Mode Multi-Mode Fibers | 15模/6模多模光纤中模组传输的部分MIMO解复用，以吞吐换取免全MIMO |

## 相干DSP与编码

26 篇 · 相干 DSP、MIMO、概率整形、FEC、相噪/定时

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M.03.05.3 | 口头 | 芯片 | 海缆 | Semi-Real-Time 24×24 MIMO Processing on FPGA | FPGA半实时24×24 MIMO处理，12耦合芯光纤跨洋级8240 km传输，实时监测MDL与信道变化 |
| Th.01.04.1 | 口头 | 算法 | 通用 | Novel Phase-Noise-Tolerant Variational-Autoencoder-Based Equalization Suitable for Space-Division-Multiplexed Transmission | 抗相噪变分自编码器(VAE)均衡，用于150 km随机耦合多芯光纤SDM传输 |
| Th.01.04.2 | 口头 | 算法 | 长途 | Experimental Validation of Machine Learning-Aided Nonlinearity-Tailored Carrier Phase Estimation for Subcarrier Multiplexing Systems | 机器学习辅助的非线性定制载波相位估计用于子载波复用系统，3000 km较联合CPE提升0.2 dB |
| Th.01.08.2 | 特邀 | 算法 | 通用 | Impact of Equalizer-Enhanced Phase Noise for Coherent Pluggables | 特邀：均衡增强相噪(EEPN)对相干可插拔模块的影响，1/f噪声致定时漂移及缓解技术 |
| Th.01.08.3 | 口头 | 算法 | 通用 | Digital Subcarrier-Based Synthesis for On-Site Transceiver Calibration with Separate Tx/Rx Frequency Responses | 数字子载波合成实现现场收发机校准，分离Tx/Rx频响；128 GBd PM-64QAM 120 km验证 |
| Th.01.08.4 | 口头 | 算法 | 通用 | Low-complexity Clock Recovery Scheme for Ultra-high-speed Digital Subcarrier Multiplexing Systems | 超高速数字子载波复用(DSCM)的低复杂度时钟恢复，90 GBd实验中ROSNR增益0.4 dB |
| Th.02.04.2 | 口头 | 算法 | 通用 | Vertically Coded Probabilistic Shaping Enabling MDL-tolerant Over-14.5-Tb/s/λ Spatial MIMO Transmission | 垂直编码概率整形提升空间MIMO对MDL的容忍度，140 GBd PS-64QAM在12耦合芯光纤净14.8/16.3 Tb/s/λ |
| Th.02.04.5 | 口头 | 算法 | 通用 | Rate-Adaptive Partial MIMO Equalization for Mode-Group Selective Transmission over Few Mode Fibers | 速率自适应部分MIMO均衡用于少模光纤模组选择传输，实现速率与复杂度细粒度折中 |
| Th.02.06.2 | 口头 | 算法 | 长途 | SPC-Coded PS-QAM with Iterative Decoding for Long-Haul Transmission in a 3.68-THz WDM System | SPC编码PS-256QAM+迭代译码，3.68 THz WDM系统在2232/1860 km实现频谱效率7.31/7.5 b/s/Hz |
| Th.02.08.3 | 口头 | 算法 | 通用 | Block-Wise MLSE Utilizing Periodic Pilot Symbols for Parallel Implementation on Digital Coherent Receiver | 基于块首导频的并行分块MLSE，16QAM实验Q因子提升1.6 dB且与导频间隔无关 |
| Th.02.08.4 | 口头 | 算法 | 通用 | Characterization of MIMO Matrices in a Comb-Based Colorless Coherent WDM Transmitter | 光梳无色相干WDM发射机中MIMO矩阵特性研究：兼容自由运行光梳，可“波束成形”分配波长 |
| Tu.01.04.3 | 口头 | 算法 | 通用 | A Novel Decision-Aided Detection Algorithm for Performance Enhancement in Bandwidth-Limited FTN-DMB Systems | 带宽受限超奈奎斯特数字多带(FTN-DMB)系统的判决辅助检测算法，50 GBd下较Nyquist-DMB增益2 dB |
| Tu.01.04.4 | 口头 | 算法 | 通用 | Nonlinear Mitigation for Coherent Optical DAC Transmitter | 相干光DAC发射机非线性行为模型与比特段映射缓解，考虑交互效应Q提升>1 dB |
| Tu.03.05.3 | 口头 | 算法 | 通用 | Single-Channel DBP Assisted by Decision-Feedback Digital Forward Propagation to Mitigate Waveform Distortion by XPM | 单通道DBP+判决反馈数字前向传播估计XPM相移，缓解WDM信号波形失真 |
| W.01.04.1 | 口头 | 算法 | 通用 | LDPC coding for bursty optical channels | 针对突发残余相噪信道的LDPC译码：Viterbi信道状态估计+突发感知LLR |
| W.01.04.2 | 口头 | 算法 | 通用 | Lowering Error Floors for Hard Decision Decoding of OFEC Code | 新型停滞图样消除算法，将OFEC硬判决译码误码平台降低一个数量级 |
| W.02.01.58 | 海报 | 算法 | 城域 | Neural Probabilistic Shaping: Joint Distribution Learning for Optical Fiber Communications | 神经概率整形：自回归端到端学习联合符号分布，205 km单跨64QAM较最优边缘分布增益0.3 bit/2D |
| W.02.01.62 | 海报 | 算法 | 通用 | Mitigating Equalization-Enhanced Phase Noise Using Adaptive Time Interpolator | 自适应延迟时间插值器缓解均衡增强相噪(EEPN)，SNR代价改善0.3 dB |
| W.02.01.63 | 海报 | 算法 | 通用 | Joint Subcarrier Equalization-Enhanced Phase Noise Mitigation | 利用数字子载波间定时信息联合缓解EEPN，作为一/二级定时恢复 |
| W.02.01.65 | 海报 | 算法 | 长途 | Neural Demodulation-Aided Optimization of Discrete Eigenvalue Assignment Enabling Error-Free 4000-km Transmission | 神经解调辅助的离散本征值分配优化(非线性傅里叶)，实现4000 km无误码传输 |
| W.02.01.66 | 海报 | 算法 | 通用 | Hybrid Soft/Hard-Decision Iterative Decoding of Concatenated RS-BCH Codes | RS外码(硬判)+BCH内码(软判)级联码的混合迭代译码，增加一次硬判迭代提升0.1–0.4 dB |
| W.02.01.71 | 海报 | 算法 | 通用 | Cost Effective and Robust Transmitter IQ skew Compensation Scheme for High Speed Coherent Digital Subcarrier Multiplexing System | DSCM系统低复杂度发射端IQ偏斜补偿，复杂度较4×4 RV-MIMO降50% |
| W.02.01.72 | 海报 | 算法 | 通用 | Asymmetrical Filtering Impairments Mitigation for Digital-Subcarrier-Multiplexing Transmissions Enabled by Multiplicationfree K-State Reserved Complex MLSE | 免乘法K状态保留复数MLSE缓解DSCM级联14个WSS的非对称滤波损伤，ROSNR改善1.63 dB |
| W.02.01.76 | 海报 | 算法 | 通用 | Single-Step Digital Backpropagation for O-band Coherent Transmission Systems | O波段近零色散区单步数字反向传播，2跨151 km 50 GBd PDM-256QAM SNR增益1.6 dB |
| W.02.01.92 | 海报 | 算法 | 通用 | Optimal Symbol Rate for Discrete Nonlinear Frequency Division Multiplexing Transmissions | 离散非线性频分复用(NFDM)最优符号率解析分析：最优值偏低，评估高级均衡增益 |
| W.02.01.93 | 海报 | 算法 | 通用 | A Neural Network Equalizer for SOA Nonlinearities in Coherent Systems | 双向LSTM均衡相干系统SOA非线性，16QAM较线性均衡Q提升4 dB |

## 光网络架构与控制

27 篇 · ROADM/OXC、规划、SDN 控制、可插拔组网

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M.03.01.1 | 教程 | 网络 | 通用 | Transport API and its Role in the era of Coherent Pluggable Optics (Tutorial) | 教程：Transport API (TAPI 2.4–2.6) 作为光网络北向接口的演进及对相干可插拔模块的控制(TIP/MANTRA) |
| M.03.06.1 | 口头 | 网络 | 通用 | Implementation and Demonstration of Contention-Less 19-Core Fiber-Based Spatial Cross-Connect Using Packaged Core Selective Switches and Core-Port Selectors | 基于封装芯选择开关与芯-端口选择器的无争用19芯光纤空间交叉连接实现与演示 |
| M.03.06.2 | 口头 | 网络 | 城域 | Fast Optical Switch Enabled Filterless SDM Networks with Adaptive Topology | 纳秒光开关+ILP拓扑优化的无ROADM滤波器less SDM城域网，自适应动态流量 |
| M.03.06.3 | 特邀 | 网络 | 通用 | Evolution Towards High-Dimensional Reconfigurable Optical Add-Drop Multiplexer/Optical Cross-Connect (ROADM/OXC) | 特邀：高维ROADM/OXC演进——空间超信道、稀疏/按需扩展/Clos交换结构 |
| M.03.06.4 | 口头 | 网络 | 通用 | How "pay as you grow" OXC stacking affects the performance of wavelength-routing SDM/WDM transparent networks | 多光纤束WDM透明网络中“按需扩展”OXC堆叠方式对性能的影响 |
| Th.02.01.3 | 特邀 | 网络 | 通用 | Best Planning Practices for Ultra-High-Capacity Networks based on Multi-Band over Space Division Multiplexing | 4芯MCF上C/C+L/C+S/C+L+S多波段叠加SDM网络规划最佳实践：C+L频谱效率最优，C+L+S容量最大 |
| Th.02.06.4 | 特邀 | 网络 | 长途 | IP over DWDM at Scale: Pluggable Transformation at Meta | Meta骨干网IPoDWDM规模化：400ZR+/800ZR+/1600ZR+可插拔+简化线路系统的点对点架构 |
| Tu.01.06.1 | 特邀 | 网络 | 通用 | Towards Truly Scalable Sustainable Flexible Optical Networks | 特邀：基于数字子载波复用的相干点到多点(P2MP)收发机四年研究综述，构建可持续灵活光网络 |
| Tu.01.06.3 | 口头 | 网络 | DCI | A Hybrid FXC-WXC Network Architecture with Low-Cost Pluggable Transceivers for Metro-Scale Optical Networks | 城域网光纤交叉(FXC)+波长交叉(WXC)混合架构配合ZR+可插拔，总成本降低30% |
| Tu.02.12.4 | Demo | 网络 | 通用 | Management of Point-to-Multipoint Coherent Pluggable Transceivers to Provision IP Virtual Network Slice over DWDM Networks using ETSI TeraFlowSDN Multi-layer SDN Controller | ETSI TeraFlowSDN多层控制器管理DSCM点到多点相干可插拔，按需开通IP虚拟切片 |
| Tu.02.12.6 | Demo | 网络 | 通用 | Enabling 3GPP-Driven Services Over Optical Transport Network | 在光传送切片上部署3GPP网络切片，提供光谱即服务(OSaaS) |
| Tu.03.01.2 | 口头 | 网络 | 城域 | Re-grouping Flexibility for Fault Recovery and Traffic Adaptation in Digital Subcarrier Multiplexing Point-to-multipoint Metro-access Integration Network | DSCM点到多点城域-接入一体化网络的重分组灵活性：无损故障恢复与昼夜流量自适应 |
| Tu.04.06.1 | 口头 | 网络 | 通用 | Layered Multiband Network Architecture with Spatially Parallel Bypass for Selective and Cost-Efficient SDM Deployment | 分层多波段光网络：在旁路层选择性引入SDM空间并行旁路，纤芯需求最多降67% |
| Tu.04.06.4 | 口头 | 网络 | 通用 | Adjustable Robust Optimization Technique for P2MP Filterless Optical Networks under Parameter Uncertainty | 可调鲁棒优化(ARO)用于参数不确定下的P2MP滤波器less光网络，减少放大器 |
| Tu.04.07.3 | 口头 | 网络 | 城域 | Extended Photonic Gateway Architecture for Port-Agnostic Accomodation of Dual-Fiber and Single-Fiber User Terminals in Metro/Access Converged All-Photonics Network | 城域/接入融合全光网络扩展光子网关架构，端口无关容纳双纤与单纤双向用户终端 |
| W.02.01.84 | 海报 | 网络 | 通用 | Observing the Worstand Best-Case Line-System Transmission Conditions in a C-Band Variable Spectral Load Scenario | C波段可变频谱负载下OMS最好/最差传输条件实验与简单频谱分配规则 |
| W.02.01.86 | 海报 | 器件 | 通用 | Novel Polarization-dependence-free Optical Injection-locking Circuit using λ/4 Phase-shift-free HR DFB LD at 1.5 µm | 无λ/4相移高反DFB激光器的偏振无关注入锁定电路，随机偏振下240 Gb/s 64QAM |
| W.02.01.98 | 海报 | 网络 | 通用 | Dynamic Risk-Aware Reconfiguration in Coherent P2MP Extended Access Networks Under Time-Varying Demands | 相干P2MP扩展接入网在时变需求下的风险感知光树动态重构 |
| W.02.01.99 | 海报 | 网络 | 通用 | Cross-Band vs Mono-Band Regeneration in C+L Optical Networks: Benefits and Trade-Off Analysis | C+L光网络跨波段vs单波段3R再生：跨波段可增加20%业务量 |
| W.02.01.103 | 海报 | 网络 | 通用 | Large-Scale Optical Networks Fast Routing: A Modified Contraction Hierarchy Approach for Path Recovery | 改进收缩层次(MCH)算法实现大规模光网络单链路故障快速路径恢复，快于Dijkstra |
| W.02.01.109 | 海报 | 网络 | 通用 | A Cost-Effective Multi-band OXC Architecture with Inter-band Wavelength Conversion on a Subset Ports | 仅部分端口带跨波段波长转换的多波段OXC架构，低阻塞同时降节点成本 |
| W.02.01.125 | 海报 | 网络 | 城域 | Performance Assessment of 800G/λ Filterless Optical Metro-Access Network with SOA-based OADM nodes | 800G/λ无滤波城域-接入网级联SOA型OADM节点，6节点80 km无误码，每节点OSNR代价0.7 dB |
| W.02.01.175 | 海报 | 网络 | 通用 | Dynamic Multipoint-to-Multipoint Optical Networking with SDN-Controlled Flexible Digital Subcarrier Multiplexing | SDN控制灵活DSCM实现多点到多点光组网，专用YANG模型+NETCONF验证 |
| W.03.01.4 | 口头 | 网络 | 通用 | Resilience-Aware Dynamic Routing and Resource Assignment in WDM over SDM and WDM over WBDM Optical Networks | 面向链路组故障的弹性感知动态路由与资源分配，比较WDM-over-SDM与WDM-over-WBDM |
| W.03.06.1 | 口头 | 网络 | 通用 | Optical Network Tomography over Live Production Network in Multi-Domain Environment | 首次在多域现网上做光网络层析：仅用商用800G转发器可视化多路由端到端光功率，定位瓶颈 |
| W.04.01.1 | 口头 | 网络 | 通用 | Demonstration of Multi-Provider Network and Cloud Service Provisioning with Blockchain Smart Contracts | 区块链智能合约实现多运营商IP-光网络与云服务的动态开通演示 |
| W.04.01.5 | 特邀 | 网络 | 通用 | Vendor Neutrality Drivers and Hindrances - Optical Spectrum as a Service in Disaggregated and Open Networks | 特邀：解耦开放网络中光谱即服务(OSaaS)的厂商中立驱动与障碍，遥测即服务(TaaS) |

## 光纤与测试

5 篇 · 光纤本体、连接、测量表征

| 编号 | 类型 | 技术层 | 场景 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th.01.04.3 | 特邀 | 算法 | 通用 | Advancing Intelligent Fiber Optic Link Monitoring: Innovations, Challenges, and Future Directions | 特邀：智能光纤链路数字化监测方案综述、挑战与未来方向 |
| Tu.04.01.4 | 口头 | 器件 | 通用 | Polarization-multiplexed Optoacoustic Information Storage in Chiral Photonic Crystal Fiber | 手性光子晶体光纤中偏振复用光声信息存储（两路正交圆偏振） |
| Tu.04.02.4 | 口头 | 器件 | 通用 | Silicon Nitride TE-pass Polarizer for E+S+C+L Bands | 布儒斯特角SiN亚波长光栅TE通偏振器，E+S+C+L全波段消光比>18 dB |
| W.01.01.1 | 教程 | 器件 | 通用 | Coupling in Optical Fibers: A Review | 特邀：光纤中模式耦合的耦合模理论基本原理及主要应用综述 |
| W.02.01.77 | 海报 | 光系统 | 海缆 | Low-Crosstalk Dual-Core Fibre for Co-and Counter-Propagating Trans-Oceanic Transmission | 低串扰低损双芯光纤用于跨洋传输，80 km跨段传输12800 km，同向/反向性能一致 |
