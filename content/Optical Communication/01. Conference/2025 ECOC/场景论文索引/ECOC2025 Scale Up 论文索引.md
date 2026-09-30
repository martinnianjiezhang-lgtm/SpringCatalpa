---
title: "ECOC2025 Scale Up 论文索引"
tags:
  - ECOC2025
  - 论文索引
---

ECOC 2025 中归入 **Scale Up**（CPO/NPO、光 I/O、Chiplet、外置光源）的论文 **17** 篇，按二级专题分组；每篇标注技术层（网络/光系统/算法/器件/芯片）和形态。类型：PDP=Postdeadline，高分=Top-Scored。
返回：[[Optical Communication/01. Conference/2025 ECOC/index|2025年 ECOC 论文专题洞察]]

> [!summary] 关键结论
> CPO 进入可靠性统计阶段：51.2T CPO 交换机超百万 400G 端口·小时数据〔Tu.01.03.3〕；1060 nm VCSEL + 多芯光纤 CPO 做到 3.95 pJ/bit〔Tu.01.03.1〕与 2.88 Tb/s〔Tu.01.03.2〕；光 Chiplet 0.75 pJ/bit〔W.01.03.2〕；CMOS 光学中介层 1.6T 发射 PIC〔Th.02.02.3〕；非制冷 400 mW QD-DFB 作 CPO 外置光源〔W.03.02.1〕。

| 二级专题 | 论文数 | 范围 |
|---|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#光源\|光源]] | 4 | 激光器、光梳、外置光源 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#Narrow&Fast\|Narrow&Fast]] | 1 | 窄而快：少通道高速率（微环/DWDM/200G+ 调制） |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#Slow&Wide\|Slow&Wide]] | 5 | 宽而慢：多通道低速率（VCSEL/microLED/多芯并行） |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#SerDes及连接器\|SerDes及连接器]] | 3 | 电 SerDes、驱动/TIA、光纤阵列/耦合/连接器、基板 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#异质集成\|异质集成]] | 2 | 3D 堆叠、键合、微转印、光学中介层、Chiplet |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#架构与系统\|架构与系统]] | 2 | Scale-up 网络架构、光交换、可靠性与运维 |

**二级专题 × 形态**

| 二级专题 | CPO/NPO/XPO | OCS | oWSE/oPSE |
|---|---|---|---|
| 光源 | 4 | – | – |
| Narrow&Fast | 1 | – | – |
| Slow&Wide | 5 | – | – |
| SerDes及连接器 | 3 | – | – |
| 异质集成 | – | – | 2 |
| 架构与系统 | 1 | 1 | – |

## 光源

4 篇 · 激光器、光梳、外置光源

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| W.02.01.26 | 海报 | 器件 | CPO/NPO/XPO | High power wideband quantum dot comb laser with 200GHz mode spacing for short reach optical I/O applications | O波段InAs量子点梳状激光器，200 GHz间隔9波长、每通道8–10 dBm，面向光IO |
| W.02.01.27 | 海报 | 芯片 | CPO/NPO/XPO | 16-wavelength Comb Source Based on Integrated Multi-Wavlength DFB Lasers for Optical I/O Technology | 4个多波长DFB组成16波长(100 GHz间隔)光梳源，面向光IO |
| W.02.01.29 | 海报 | 芯片 | CPO/NPO/XPO | High-power REC-DFB Laser Array Integrated with Phase Compensators for Optical I/O Technology | 集成相位补偿器的高功率REC-DFB激光器阵列，>100 mW、SMSR>50 dB，面向光IO |
| W.03.02.1 | 口头 | 器件 | CPO/NPO/XPO | Efficient Uncooled High-Power 1.31 µm DFB Laser diode for Co-Packaged Optics | O波段InAs/GaAs量子点DFB+集成SOA，25–85°C输出>400 mW、效率>20%，适用CPO非制冷外置光源 |

## Narrow&Fast

1 篇 · 窄而快：少通道高速率（微环/DWDM/200G+ 调制）

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| W.04.07.1 | 特邀 | 芯片 | CPO/NPO/XPO | The Path of Dual-Polarization IM-DD High-Speed Transceivers for Intra-DC and Optical Access Applications | 特邀：双偏振IM-DD缓解光出口密度瓶颈（CPO+光中介层解决电出口密度），425 Gb/s DP-PAM4+集成无尽偏振跟踪 |

## Slow&Wide

5 篇 · 宽而慢：多通道低速率（VCSEL/microLED/多芯并行）

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Tu.01.03.1 | 口头 | 芯片 | CPO/NPO/XPO | An Ultra-Compact 50-Gbaud × 16-Channel CPO Transceiver employing a 1060-nm Single-Mode VCSEL array and Multicore Fibres | 1060 nm单模VCSEL阵列+多芯光纤的超紧凑50 GBd×16通道CPO收发机，106.25G PAM4能耗3.95 pJ/bit（纪录） |
| Tu.01.03.2 | 口头 | 芯片 | CPO/NPO/XPO | 2.88 Terabit-per-Second 16-Channel VCSEL Array for Co-packaged Optics with Multi-core Fiber | 1060 nm 16通道VCSEL阵列直接耦合单模MCF，每通道180 Gb/s PAM-4，总2.88 Tb/s@500 m，面向CPO |
| W.01.03.2 | 口头 | 芯片 | CPO/NPO/XPO | Optical Chiplet with 0.75-pJ/bit Transmitter Using Membrane III-V Electro-absorption Modulators on Si and Differential CMOS Driver | Si上薄膜III-V电吸收调制器+嵌入式差分CMOS驱动的光Chiplet，64 Gb/s PAM4能耗0.75 pJ/bit |
| W.02.01.16 | 海报 | 芯片 | CPO/NPO/XPO | A Programmable and Reconfigurable On-Chip Photonic Filter for Next-Generation Multi-Channel DWDM | 热光啁啾四相移采样布拉格光栅可编程多通道滤波器，50–250 GHz可调，面向DWDM/光IO |
| W.02.01.23 | 海报 | 芯片 | CPO/NPO/XPO | Energy-Efficient DWDM Transmitter for Silicon Optical I/O Enabled by FP-Cavity Modulators | 大FSR硅FP腔调制器单波128 Gb/s PAM4，4通道200 GHz间隔512 Gb/s DWDM光IO发射机 |

## SerDes及连接器

3 篇 · 电 SerDes、驱动/TIA、光纤阵列/耦合/连接器、基板

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th.02.02.4 | 口头 | 芯片 | CPO/NPO/XPO | Photonic Integrated Circuit CPO Module with Polymer Waveguides for Optical PCIe Transmission | 聚合物波导PIC的CPO模块，EIC有机基板标准工艺组装，32 Gb/s/lane满足PCIe5.0/CXL2.0 |
| W.01.03.1 | 口头 | 芯片 | CPO/NPO/XPO | An All-Silicon 4x56 Gbit/s NRZ, 1pJ/bit Optical Receiver with Ge-on-Si PDs and 28nm CMOS TIA Array | 全硅4×56 Gb/s NRZ光接收机(Ge PD阵列+28 nm CMOS TIA)，1 pJ/bit，面向一跳光交换光IO |
| W.02.01.36 | 海报 | 芯片 | CPO/NPO/XPO | Compact Detachable Optical Connector with Low Loss and High Stability for Co-Packaged Optics | 面向CPO的12通道紧凑可插拔光连接器，插损<0.4 dB、回损>38 dB，50次插拔免清洁波动0.03 dB |

## 异质集成

2 篇 · 3D 堆叠、键合、微转印、光学中介层、Chiplet

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Th.02.02.3 | 口头 | 芯片 | oWSE/oPSE | Hybrid Integrated 1.6T 2xFR4 Transmitter PIC using a CMOS based Optical InterposerTM | 基于CMOS光学中介层的混合集成1.6T 2×FR4发射PIC，EML+驱动无源组装，号称最小1.6T发射光引擎 |
| W.02.01.38 | 海报 | 芯片 | oWSE/oPSE | 3D Silicon Nitride Waveguide Interposers for High-density Scale-up Chiplet Interconnects | 3D多层氮化硅波导中介层，面向高密度Scale-up Chiplet光互连 |

## 架构与系统

2 篇 · Scale-up 网络架构、光交换、可靠性与运维

| 编号 | 类型 | 技术层 | 形态 | 题目 | 中文要点 |
|---|---|---|---|---|---|
| Tu.01.03.3 | 口头 | 网络 | CPO/NPO/XPO | Co-packaged Optics Technology Evaluation for Hyperscale Data Center Fabric Switches | 51.2T CPO交换机大规模评估：超百万400G端口·小时高温应力运行的功耗、光性能与可靠性统计 |
| Tu.03.07.3 | 口头 | 网络 | OCS | Photonic Switching for Dynamic Bandwidth Sharing in Optically Networked Heterogeneous Computing Systems | 面向异构计算的动态光交换(~250 ns开关+光接口CXL+控制器)，芯片间Tbps级带宽共享 |
