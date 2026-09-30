---
title: "OFC2026 Scale Up 论文索引"
tags:
  - OFC2026
  - 论文索引
---

OFC 2026 中归入 **Scale Up**（CPO/NPO、光 I/O、Chiplet、外置光源）的论文 **35** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）和形态。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2026 OFC/index|2026年 OFC 论文专题洞察]]

> [!summary] 关键结论
> CPO 关注点从器件转到“系统可靠性 + 外置光源”：8 通道 >+25 dBm ELS〔W1B.3〕、500 mW PCSEL〔W4E.2〕、3D 堆叠 EIC/PIC 光 I/O 1.33 Tb/s/mm²〔M4B.2〕、玻璃基板与 AWGR 光学中介层〔Th3C.2、Th3C.1〕、TFLN 晶圆级 CPO 引擎〔Th4A.6〕；光域 AllReduce〔M4F.3、Th3H.3〕与 THz 介质波导互连〔Th1A.1〕是新候选。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#光源\|光源]] | 8 | 激光器、光梳、外置光源 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#Narrow&Fast\|Narrow&Fast]] | 3 | 窄而快：少通道高速率（微环/DWDM/200G+ 调制） |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#Slow&Wide\|Slow&Wide]] | 7 | 宽而慢：多通道低速率（VCSEL/microLED/多芯并行） |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#SerDes及连接器\|SerDes及连接器]] | 6 | 电 SerDes、驱动/TIA、光纤阵列/耦合/连接器、基板 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#异质集成\|异质集成]] | 2 | 3D 堆叠、键合、微转印、光学中介层、Chiplet |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#架构与系统\|架构与系统]] | 9 | Scale-up 网络架构、光交换、可靠性与运维 |

**二级专题 × 形态**

| 二级专题 | CPO/NPO/XPO | OCS | oWSE/oPSE |
|---|---|---|---|
| 光源 | 6 | – | 2 |
| Narrow&Fast | 2 | – | 1 |
| Slow&Wide | 6 | – | 1 |
| SerDes及连接器 | 4 | 1 | 1 |
| 异质集成 | 1 | – | 1 |
| 架构与系统 | 5 | 4 | – |

## 光源

8 篇 · 激光器、光梳、外置光源

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M4D.5 | 口头 | 器件 | oWSE/oPSE | 82-mm-long Optical Link using Micro-transfer-printed Directly Modulated Membrane Laser and Photodetector on SiN Waveguide: Toward Wafer-scale Optical Interconnects | 微转印III-V直调薄膜激光器与PD于82 mm SiN波导，48 Gb/s NRZ、0.24 pJ/bit，迈向晶圆级光互连 |
| M4F.5 | 口头 | 网络 | CPO/NPO/XPO | Single Microcomb Source for Ultra-Scalable Datacenters for Dense Deep Neural Network Workloads | 单个微梳按负载分配梳线的AI光数据中心网络架构，可支持120 Pb/s与百万级GPU |
| Th2A.13 | 海报 | 器件 | CPO/NPO/XPO | High-Efficiency Silicon Nitride Microcombs for Co-Packaged Optics | 面向CPO的高效氮化硅耗散Kerr孤子微梳，转换效率69%（纪录），24通道>0 dBm |
| Th3C.1 | 口头 | 芯片 | oWSE/oPSE | Chiplet-to-Chiplet All-to-All Interconnecting Photonic Interposer Using AWGRs with 3D Ultrafast-Laser-Inscription | 3D超快激光刻写AWGR光子中介层实现Chiplet间全互连，硅光Chiplet低损耦合 |
| Th3C.5 | 口头 | 芯片 | CPO/NPO/XPO | Ultra-Low Loss Compact SiP Polarization Compensator for CPO with an ELS | 超低损紧凑SiP O波段偏振补偿器，补偿1 km外置光源(ELS)任意偏振，IL 1.9 dB，用于CPO |
| W1B.3 | 口头 | 芯片 | CPO/NPO/XPO | >+25-dBm  8-Channel SOA-Integrated DFB-LD-based TOSA for CPO External Laser Sources | 面向CPO外置光源的8通道SOA集成DFB TOSA，每通道出纤>+25 dBm |
| W3E.1 | 特邀 | 器件 | CPO/NPO/XPO | Ultra-High Optical Output Power External Laser Sources for Co-Packaged Optics | 面向CPO的超高输出功率外置光源：高功率SOA集成DFB的8通道TOSA及双TOSA 16通道ELSFP模块 |
| W4E.2 | 高分 | 芯片 | CPO/NPO/XPO | 500 mW O-Band Photonic-Crystal Surface-Emitting Lasers and Scalable 2D Arrays for Multi-Channel CPO Applications | O波段PCSEL输出>500 mW、墙插效率20%、线宽82 kHz，2×2四通道阵列，面向多通道CPO |

## Narrow&Fast

3 篇 · 窄而快：少通道高速率（微环/DWDM/200G+ 调制）

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th1C.3 | 口头 | 光系统 | CPO/NPO/XPO | 400G/lane for Linear-drive Optics Applications | 高带宽效率TFLN MZM+实用均衡实现400G/lane，增强CTLE下可用于NPO/CPO线性驱动光学 |
| Th2A.14 | 海报 | 器件 | CPO/NPO/XPO | Record-High 90-GHz Silicon Microring Modulator with Compact RLC Modeling and 224-Gb/s PAM4 Operation toward Co-Packaged Optics Integrations | 电感与波长调谐硅微环调制器，EO带宽90 GHz（纪录），224 Gb/s PAM4，面向CPO |
| Th4A.6 | PDP | 芯片 | oWSE/oPSE | TFLN-based Wafer-Level Co-Packaged Optics Engine for Ultrahigh-Bandwidth Electro-Optical Modulation | TFLN电光调制器与驱动EIC晶圆级异质集成的CPO引擎，带宽>100 GHz，飞秒级时频比对 |

## Slow&Wide

7 篇 · 宽而慢：多通道低速率（VCSEL/microLED/多芯并行）

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M2A.4 | 海报 | 芯片 | CPO/NPO/XPO | A 16×128 Gbps DWDM Wavelength-Locked Silicon Photonic Microring Transmitter Enabled by a Quantum-Dot Comb Laser | 量子点锁模光梳(100 GHz)驱动的16×128 Gb/s波长锁定硅微环DWDM发射机，单纤2 Tb/s |
| M4B.2 | 高分 | 芯片 | oWSE/oPSE | A 256 Gb/s DWDM Optical I/O in a 3D-stacked EIC/PIC Silicon Photonics Platform | 3D堆叠7 nm EIC/65 nm PIC硅光平台的(8+1)×32 Gb/s DWDM光IO（含转发时钟），1.33 Tb/s/mm² |
| M4B.3 | 口头 | 芯片 | CPO/NPO/XPO | 16-Wavelength 800-Gbps Bidirectional Link over Single-Mode Fiber Using Microring Transceivers | 首个单纤16波长双向800 Gb/s微环收发链路（XSR SerDes），对偏振与温度鲁棒 |
| Th1G.3 | 口头 | 器件 | CPO/NPO/XPO | Low-power and Short-distance Wireless Optical Interconnection System Based on 1.6 GHz Bandwidth Red Micro-LED | 金刚石衬底1.6 GHz带宽红光Micro-LED短距无线光互连，1.5 Gb/s，功耗0.22 pJ/bit |
| Th1G.4 | 口头 | 器件 | CPO/NPO/XPO | Multicore Fiber Coupled Backside-Emitting VCSEL/PD Arrays for High-Bandwidth Optical Interconnects in Data Center | 19芯MCF耦合背发射VCSEL/背照PD阵列倒装驱动-TIA EIC的共封装光Chiplet，面向多芯片GPU光互连 |
| W1B.4 | 口头 | 芯片 | CPO/NPO/XPO | A 53-Gbaud NRZ/PAM4 × 8-Channel 1060-nm Single-Mode VCSEL-Based Ultra-Compact and High-Energy-Efficient CPO Transceiver for Full-Reach Datacenter Links | 53 GBd×8通道1060 nm单模VCSEL超紧凑CPO收发机(1.22 cm²、4.5 pJ/bit)，2 km SMF并行链路 |
| W1B.5 | 高分 | 芯片 | CPO/NPO/XPO | 106-Gbps 940-nm Flip-Chip Back-Emitting VCSEL with Metalens for NPO/CPO Applications | 集成超透镜的940 nm倒装背发射VCSEL，超大耦合容差、结温更低，100°C下106 Gb/s PAM4 |

## SerDes及连接器

6 篇 · 电 SerDes、驱动/TIA、光纤阵列/耦合/连接器、基板

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th1D.3 | 口头 | 芯片 | CPO/NPO/XPO | Glass Waveguides with 0.01 dB/cm Bend Loss for High-Speed, High-Density Optical Fan-Out for Co-Packaged Optics | 离子交换玻璃波导弯曲损耗0.01 dB/cm，用于CPO光纤-芯片节距转换扇出，耦合损耗<0.3 dB，400G PAM4 |
| Th2A.2 | 海报 | 器件 | CPO/NPO/XPO | Over-8000-GHz/mW-FoM Transimpedance Amplifier for Processor Interconnection | 嵌入有机基板的处理器互连TIA，优值9400 GHz·Ω/mW，为以往两倍以上 |
| Th2A.8 | 海报 | 芯片 | CPO/NPO/XPO | Meta-lens for co-package optics and fiber array unit coupling | 超透镜辅助CPO：多通道可拆卸光纤阵列-硅光芯片耦合，1 dB对准容差±18 µm |
| Th3C.2 | 口头 | 芯片 | oWSE/oPSE | Integrated Glass Waveguide Substrate with Surface Coupled Photonic Chips for Massive Scaling of CPO | 嵌入波导与电互连的玻璃基板+表面耦合光子芯片实现CPO大规模扩展，光纤-芯片损耗2 dB |
| Th3C.3 | 口头 | 芯片 | CPO/NPO/XPO | Vertical Optical Coupling Tapers for Co-Packaged Optics with Multimode Fiber and High-Speed Photodetectors | 多模光纤阵列到小孔径(10 µm)高速PD的垂直耦合锥，效率>95%、对准容差>±25 µm |
| W2A.41 | 海报 | 网络 | OCS | PCIe-over-Optics with OSFP DR8 LPO and an Optical Circuit Switching Fabric for Composable CPU-GPU Resource Pooling | 标准OSFP DR8 LPO承载PCIe5.0 x16（100 m无误码）+OCS交换，实现可组合CPU-GPU资源池 |

## 异质集成

2 篇 · 3D 堆叠、键合、微转印、光学中介层、Chiplet

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M4D.1 | 特邀 | 器件 | CPO/NPO/XPO | Membrane III-V Photonic Devices for Chip-to-Chip Interconnections | 特邀：硅上薄膜III-V光子器件（低电容调制器与激光器）用于高密度芯片间互连 |
| Th3C.4 | 特邀 | 网络 | oWSE/oPSE | High Performing Photonics Systems – CPO, Towards Photonics Chiplets | 特邀：CPO、中介层与光子Chiplet的封装驱动光子系统架构，迈向204.8T级平台 |

## 架构与系统

9 篇 · Scale-up 网络架构、光交换、可靠性与运维

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| M1G.6 | 特邀 | 芯片 | CPO/NPO/XPO | Photonics for AI, AI for Photonics: A Bidirectional Path to Scalable and Fabrication-Robust Design | 特邀：光子赋能AI与AI赋能光子——光互连、模分复用与AI辅助修正工艺偏差的紧凑高能效光子电路 |
| M3F.6 | 特邀 | 网络 | OCS | Optical Switching for AI Factories | 特邀：面向AI工厂的光交换——GPU集群带宽、能效与网络架构 |
| M3Z.14 | Demo | 网络 | OCS | Distributed Evaluation for Optical-Electronic Hybrid Networking in Large-Scale AI Data Center | 树莓派集群模拟万卡GPU光电混合组网的分布式轻量评估平台(SimAI+GPT-22B) |
| M3Z.15 | Demo | 网络 | CPO/NPO/XPO | AI Agent-Driven Network-Aware Decentralized Compute Resource Brokering | AI Agent驱动的网络感知去中心化算力经纪：IP+光编排结合GPU共享 |
| M4B.6 | 特邀 | 网络 | CPO/NPO/XPO | Technology for AI Interconnect Scale-Up Solutions | 特邀：AI Scale-up互连技术——基于CPO可靠性测试评估链路性能与可靠性对集群的影响 |
| M4F.3 | 口头 | 网络 | OCS | All-Optical Analog AllReduce and Digital Switching using a Silicon Hybrid Computing-Switching Optical Processor | 4×4硅光开关动态配置实现全光模拟AllReduce与数字交换的计算-交换一体光处理器 |
| Th1A.1 | 特邀 | 网络 | CPO/NPO/XPO | THz Interconnects for Scale Up Networks | 特邀：面向Scale-up网络的THz互连——THz ASIC+低损介质波导承载224/448 Gb/s PAM4与UCIe |
| Th3H.3 | 高分 | 芯片 | OCS | In-Network Analog ALLREDUCE for ML with Programmable Integrated Photonics | 可编程集成光子网格实现网络内模拟ALLREDUCE（计算与路由同时进行），ML训练通信快2倍 |
| W1D.7 | 特邀 | 网络 | CPO/NPO/XPO | Co-Design of Electronic and Photonic Systems for Future LPO, NPO, and CPO | 特邀：面向LPO/NPO/CPO的电子与光子系统协同设计/封装的收益与挑战 |
