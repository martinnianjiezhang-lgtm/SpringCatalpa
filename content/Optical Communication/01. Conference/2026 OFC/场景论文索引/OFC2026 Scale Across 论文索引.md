---
title: "OFC2026 Scale Across 论文索引"
tags:
  - OFC2026
  - 论文索引
---

OFC 2026 中归入 **Scale Across**（跨楼/园区/区域 DC 互连、跨 DC 训练）的论文 **15** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2026 OFC/index|2026年 OFC 论文专题洞察]]

> [!summary] 关键结论
> 跨 DC 训练从经济性论证走向现网：1024 GPU 跨 600 km 多 AIDC 训练 LLaMA2-70B，DP/PP 效率损失 <5%/<1%〔W4H.5〕；DCI 单波进入 1.2T（S+C+L 134 Tb/s，全部通道 1.276 Tb/s〔W3J.1〕）；coherent-lite 靠光梳共享载波/时钟做波特率采样〔Th4C.8〕，BTO DP-IQM 单波净 1 Tb/s（ZR 80 km）〔Th3J.4〕。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#产业需求\|产业需求]] | 6 | AI 训练跨 DC 需求、架构、经济性、保护与运维 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#FST与Multi-Rail\|FST与Multi-Rail]] | 2 | 全谱转发器、多 rail 线路系统、光纤对为单位的扩容 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#ZR、ZR+、CL\|ZR/ZR+/CL]] | 1 | 400ZR/800ZR/1600ZR(+)、相干可插拔、Coherent-Lite、IPoDWDM |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#低功耗DSP\|低功耗DSP]] | 1 | 低复杂度/波特率采样 DSP、FPGA 实时实现、时钟共享 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#高波特率器件\|高波特率器件]] | 3 | 高波特率调制器/探测器/驱动/光 DAC |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#光源\|光源]] | 1 | 激光器、光梳、外置光源 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#新型光纤介质\|新型光纤介质]] | 1 | 空芯/多芯/少模光纤用于 DC 互连 |

## 产业需求

6 篇 · AI 训练跨 DC 需求、架构、经济性、保护与运维

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M4A.2 | 口头 | 网络 | Agnostic QoT Probing via Receiver-Side ASE Loading in a Production Metro for Transparent Datacenter Exchange | 生产城域网中接收端ASE加载实现与设备无关的QoT探测（估计GSNR），服务数据中心交换 |
| Th3B.3 | 口头 | 网络 | Robust Brownfield Topology Design for Data Centre Interconnection | 面向流量分布变化的鲁棒存量数据中心互连拓扑设计，吞吐提升最多57% |
| Tu2C.6 | 口头 | 网络 | Demonstration of a Collision Control Mechanism for Inter-AIDC Traffic in a Spine-Leaf Multi-Granularity All-Optical Switching Network | spine-leaf多粒度全光交换网络中面向AIDC间时敏流量的冲突控制机制，FPGA测试床验证 |
| W2A.34 | 海报 | 网络 | Enabling Deterministic Inter-Data Center Communication Through a Multi-Layer SDN Architecture | 多层SDN架构SCX（FlexE时分复用+SRv6控制）实现确定性数据中心间通信 |
| W4H.3 | 口头 | 网络 | Clusterand Reach-scalable Optical Switching for Scale-across AI System | 基于OCS、兼具距离与集群可扩展性的Scale-across AI架构，集群间延伸30 km不影响作业完成时间 |
| W4H.5 | 高分 | 网络 | Field Trials of 600-km Large Language Model Distributed Training Across Long-Haul Multi-AIDCs | 600 km长途多AIDC分布式训练现场试验：1024 GPU训练LLaMA2-70B，16λ×800G OTN，DP/PP效率损失<5%/<1% |

## FST与Multi-Rail

2 篇 · 全谱转发器、多 rail 线路系统、光纤对为单位的扩容

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| W3J.1 | 口头 | 光系统 | Real-Time S+C+L-Band 134-Tb/s DCI Bidi Transmission with All Channels at 1.2-Tb/s Enabled by SiPh Transceiver | 硅光收发机实时S+C+L 134 Tb/s DCI双向传输，全部通道1.276 Tb/s，75 km G.654.E |
| W3J.5 | 特邀 | 器件 | Wideband SOA for WDM Systems and Datacenter Interconnects | 特邀：面向WDM与DCI的宽带SOA——非线性损伤表征与发端缓解扩展功率预算 |

## ZR、ZR+、CL

1 篇 · 400ZR/800ZR/1600ZR(+)、相干可插拔、Coherent-Lite、IPoDWDM

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| W4H.1 | 特邀 | 网络 | IPoDWDM Performance and Control Plane Validation in Multi-Vendor Environments | 多厂商IPoDWDM独立实验室验证：400G ZR+/100G ZR-DCO六跨ROADM性能与SDN控制面，CMIS 5.x成熟 |

## 低功耗DSP

1 篇 · 低复杂度/波特率采样 DSP、FPGA 实时实现、时钟共享

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M3B.7 | 口头 | 算法 | On the transceiver nonlinear compensation enhancing power budget in amplifierless DCN coherent systems | 收发端非线性联合补偿提升20 km无放大DCN 150 GBd CS-256QAM 1.6T相干系统功率预算6 dB |

## 高波特率器件

3 篇 · 高波特率调制器/探测器/驱动/光 DAC

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Th3J.4 | 口头 | 器件 | Barium Titanate DP-IQM Enabling Net 1 Tbps/λ ZR and Coherent-Lite Data Center Networks | 钛酸钡(BTO) DP-IQM实现净1 Tb/s/λ：ZR 80 km与coherent-lite 2 km（纪录） |
| Th4B.2 | PDP | 芯片 | Driver-less 448 Gbps PAM4 and 1.2 Tbps 16-QAM IMDD/Coherent-lite transmission using TFLN optical DACs | CMOS逻辑门直驱TFLN光DAC，免驱动实现448 Gb/s PAM4@2 km与1.2 Tb/s 16QAM@10 km（纪录） |
| W3F.4 | 特邀 | 芯片 | High Speed and Low Power Consumption Optical DAC Transmitter Using Fully Integrated CMOS and Silicon Segmented Modulator | 特邀：全集成CMOS+硅分段调制器光DAC发射机，用于coherent-lite与IM-DD的高速低功耗方案 |

## 光源

1 篇 · 激光器、光梳、外置光源

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Th4C.8 | PDP | 光系统 | Carrier/clock-shared comb-based superchannel with <1-ps timing error enabling baud-rate sampling coherent reception for scale-across AIDCs | 电光梳载波/时钟共享的18λ×384 Gb/s超信道，采样抖动<0.9 ps，波特率采样coherent-lite，面向跨区AIDC分布训练 |

## 新型光纤介质

1 篇 · 空芯/多芯/少模光纤用于 DC 互连

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Tu3D.7 | 口头 | 光系统 | BiDi-EDF Enabled Co-Frequency Co-time Full-duplex Transmission over Single-span 150-km ST-HCF for ZR+ Applications | 支撑管空芯光纤+双向EDF放大器，150 km单跨同频同时全双工ZR+传输，双向增益18 dB |
