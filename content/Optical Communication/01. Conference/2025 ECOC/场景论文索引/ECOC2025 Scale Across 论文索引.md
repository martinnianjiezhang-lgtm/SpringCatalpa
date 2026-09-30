---
title: "ECOC2025 Scale Across 论文索引"
tags:
  - ECOC2025
  - 论文索引
---

ECOC 2025 中归入 **Scale Across**（跨楼/园区/区域 DC 互连、跨 DC 训练）的论文 **22** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2025 ECOC/index|2025年 ECOC 论文专题洞察]]

> [!summary] 关键结论
> AI 训练开始定义 DCI：分布式训练时间/成本/能耗框架显示城域分布训练只慢 7%、长途慢 37%〔Tu.04.06.2〕；<50 ms 光层保护保障多 DC LLM 训练无损〔Tu.01.06.4〕；空芯光纤首次用于 AI DC 的 8λ×225 GBd 双向 IM-DD（7.6 Tb/s，PDP）〔Th.03.03.3〕；coherent-lite 7 芯 80 km 净 31.7 Tb/s〔M.02.05.4〕；L4 自治光网络服务分布式训练〔W.02.01.177〕。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#产业需求\|产业需求]] | 9 | AI 训练跨 DC 需求、架构、经济性、保护与运维 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#FST与Multi-Rail\|FST与Multi-Rail]] | 0 | 全谱转发器、多 rail 线路系统、光纤对为单位的扩容 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#ZR、ZR+、CL\|ZR/ZR+/CL]] | 3 | 400ZR/800ZR/1600ZR(+)、相干可插拔、Coherent-Lite、IPoDWDM |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#低功耗DSP\|低功耗DSP]] | 1 | 低复杂度/波特率采样 DSP、FPGA 实时实现、时钟共享 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#高波特率器件\|高波特率器件]] | 0 | 高波特率调制器/探测器/驱动/光 DAC |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#光源\|光源]] | 1 | 激光器、光梳、外置光源 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#新型光纤介质\|新型光纤介质]] | 8 | 空芯/多芯/少模光纤用于 DC 互连 |

## 产业需求

9 篇 · AI 训练跨 DC 需求、架构、经济性、保护与运维

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Th.01.05.1 | 教程 | 网络 | Leveraging Digital Twins for All-Photonics Networks-as-a-Service: Enabling Innovation and Efficiency (Tutorial) | 教程：利用数字孪生实现面向分布式AI数据中心的全光网络即服务(APN-aaS)，含远端转发器控制与纵向监测 |
| Tu.01.06.4 | 口头 | 网络 | Field Trial of Telecom-Grade Sub-50ms Protection in Wavelength Switched Optical Networks for Lossless Large Language Model Multi-datacenter Distributed Training | 波长交换光网络<50 ms电信级保护现场试验，保障多数据中心LLM分布式训练无损 |
| Tu.03.01.1 | 特邀 | 网络 | One-hop all-optical DC-oriented networks for 2030 | 特邀：面向2030的“一跳全光”数据中心导向网络架构、关键技术与标准化 |
| Tu.04.06.2 | 口头 | 网络 | Training Time, Economics, and Energy for Distributed AI Training in the GenAI Era | GenAI时代分布式AI训练时间/成本/能耗评估框架：城域分布训练仅慢7%，长途慢37%，Bifrost协议再减26% |
| W.02.01.95 | 海报 | 算法 | Impact of SOA Nonlinear Impairments on Data Center Interconnect Link Performance and Optimization | 闭式GN模型分析C+L DCI系统中SOA非线性对最优入纤功率的影响 |
| W.02.01.97 | 海报 | 网络 | Traffic-Interleaved Connectivity Provisioning for Cross-datacenter LLM Training over Optical Transport Networks | 基于AI流量模式的流量交织连接开通，跨数据中心LLM训练OTN带宽节省40% |
| W.02.01.177 | 海报 | 网络 | First Field-Trial Demonstration of L4 Autonomous Optical Network for Distributed AI Training Communication: An LLM-Powered Multi-AI-Agent Solution | 首个面向分布式AI训练的L4自治光网络现场试验：LLM多智能体跨域跨层，任务完成率~98% |
| W.02.01.178 | 海报 | 网络 | GASTPipe: Resource-efficient Hybrid Parallelism Scheme for Distributed AI Training over Cross-DC Optical Networks | GASTPipe：跨DC光网络分布式AI训练的混合并行方案，频隙与时间开销分别降55.87%/80.35% |
| W.02.01.179 | 海报 | 网络 | Straggler-Aware Resource Allocation in Semi-Decentralized Federated Learning for Large-Scale Models over OTNs | OTN上大模型半去中心化联邦学习的掉队者感知资源分配，接近MILP且运行时间降99.78% |

## FST与Multi-Rail

0 篇 · 全谱转发器、多 rail 线路系统、光纤对为单位的扩容

（本次会议无）

## ZR、ZR+、CL

3 篇 · 400ZR/800ZR/1600ZR(+)、相干可插拔、Coherent-Lite、IPoDWDM

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| M.02.05.4 | 口头 | 光系统 | Coherent-Lite with Low-Complexity Baud-Rate-Sampling Receiver Enabled by Clock and Wavelength Locking Over 80 km 7-Core Fiber | 80 km数据中心间互连的Coherent-Lite：时钟与波长锁定的波特率采样接收机，7芯光纤48通道净31.7 Tb/s |
| Th.02.08.1 | 特邀 | 算法 | Algorithm and Architecture for Short-Reach Coherent-Lite Optics | 特邀：短距Coherent-Lite算法与架构——相噪跟踪、远端本振偏振衰落消除与接收维度扩展 |
| Tu.01.06.2 | 口头 | 网络 | Capacity Scaling Limits of DCI Networks: A Comparative Study of ZR, ZR+, and High-Performance Transponders | 短距DCI网络中ZR/ZR+与高性能转发器容量扩展极限比较：跨段损耗≤31 dB时高性能转发器多50%容量 |

## 低功耗DSP

1 篇 · 低复杂度/波特率采样 DSP、FPGA 实时实现、时钟共享

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Th.02.08.2 | 口头 | 芯片 | FPGA-Based Hardware Realization of PTBC DSP for 100 Gbps 16-QAM Transmission in Coherent-Lite Optical Network | FPGA实时PTBC DSP硬件实现，100 Gb/s 16QAM 20 km，功率预算34.6 dB，面向coherent-lite |

## 高波特率器件

0 篇 · 高波特率调制器/探测器/驱动/光 DAC

（本次会议无）

## 光源

1 篇 · 激光器、光梳、外置光源

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| W.02.01.49 | 海报 | 芯片 | Demonstration of ±0.5 GHz Lasing Frequency Stability of DFB-CAN with One-Chip Wavelength Monitor and Evaluation of 16QAM 40-km Fiber Transmission | 单芯片波长监测器反馈控制DFB-CAN频率稳定度±0.5 GHz，16QAM 40 km满足DCI |

## 新型光纤介质

8 篇 · 空芯/多芯/少模光纤用于 DC 互连

| 编号 | 类型 | 技术层 | 题目 | 中文要点 |
|---|---|---|---|---|
| Th.03.03.3 | PDP | 光系统 | Fiber for AI Data Center based on 8λ-225 GBaud PAM4/6 | 首个空芯光纤双向8λ×225 GBd IM-DD WDM传输，10 km净6.4/7.6 Tb/s（PAM4/6），面向AI数据中心 |
| Tu.04.07.2 | 口头 | 光系统 | Net 282 Gb/s IM/DD Transmission in C-band over 3.1 km long NANF using Silicon Photonics TW-MZM | 硅光行波MZM在3.1 km NANF空芯光纤C波段IM/DD：256 GBd OOK/145 GBd PAM4/120 GBd PAM6，净282 Gb/s |
| Tu.04.07.5 | 口头 | 光系统 | Pairwise SDM transmission resolving fiber dispersion in up-to-200Gbps/lane multicore fiber IM-DD systems for edge and inter-datacenter networks | “成对SDM传输”解决色散：MCF C波段IM-DD 200 Gb/s/lane@35.5 km、128 Gb/s/lane@85.4 km（速率距离积纪录） |
| W.02.01.02 | 海报 | 器件 | Pushing the Limits of Core Density in Multi-core Fibres for Data Centre Applications | 面向数据中心O波段IM-DD的超高密度8芯/12芯MCF，芯密度创纪录 |
| W.02.01.82 | 海报 | 光系统 | Single-Mode Transmission over Ultra-low-loss 0.1400 dB/km Few-mode Fibre for Data Centre Interconnects | 超低损(0.1400 dB/km)少模光纤单模传输24 km，42 GBd DP-256QAM，保留SDM升级能力 |
| W.02.01.85 | 海报 | 光系统 | C-band 350Gb/s 8.52-km Optical Interconnect enabled by Anti-Resonant Hollow-Core Fiber and PS-PAM16 | 8.52 km反谐振空芯光纤C波段92 GBd PS-PAM16，仅FFE，净294 Gb/s |
| W.02.01.88 | 海报 | 光系统 | Co-Transmission of OSCL-Band 4λ 240 Gb/s/λ PAM8 Signals over 6.2 km Anti-Resonate Hollow-Core-Fiber with Linear FFE | 6.2 km反谐振空芯光纤O/S/C/L四波段4λ×240 Gb/s PAM8共传（960 Gb/s），仅线性FFE |
| W.03.05.3 | 口头 | 光系统 | 211.7-Gbit/s High-Order PAM Transmission over 11.1 km of Hollow-Core NANF in C-band | 封装调制器在11.1 km NANF空芯光纤C波段传90 GBd PAM6/75 GBd PAM8，211.7 Gb/s |
