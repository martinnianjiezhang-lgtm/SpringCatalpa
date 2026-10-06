---
title: "ECOC2026 厂商索引 · AIDC客户"
tags:
  - ECOC2026
  - 厂商
---

> [!info] 本页由 export_entities.py 自动生成，重跑会覆盖；想写自己的内容请另建笔记。

ECOC 2026 中出现的AIDC客户共 **12** 家。“主讲”= 该公司自己上台或署名的报告；“提及”= 别人的报告里提到它。

| 厂商 | 主讲 | 提及 | 主讲报告的场景分布 |
|---|---|---|---|
| [[ECOC2026 厂商索引 · AIDC客户#Microsoft · Azure\|Microsoft · Azure]] | 14 | 21 | Scale Across 2、Scale Out 1、Scale Up 3、Transport 7、新应用 1 |
| [[ECOC2026 厂商索引 · AIDC客户#Oracle OCI\|Oracle OCI]] | 10 | 1 | Scale Across 1、Scale Out 4、Scale Up 5 |
| [[ECOC2026 厂商索引 · AIDC客户#Meta\|Meta]] | 4 | 18 | Scale Up 1、Transport 3 |
| [[ECOC2026 厂商索引 · AIDC客户#Google\|Google]] | 2 | 19 | Scale Across 1、Scale Out 1 |
| [[ECOC2026 厂商索引 · AIDC客户#OpenAI\|OpenAI]] | 4 | 8 | Scale Up 4 |
| [[ECOC2026 厂商索引 · AIDC客户#阿里云\|阿里云]] | 1 | 2 | Scale Out 1 |
| [[ECOC2026 厂商索引 · AIDC客户#Amazon · AWS\|Amazon · AWS]] | 0 | 4 |  |
| [[ECOC2026 厂商索引 · AIDC客户#OVHcloud\|OVHcloud]] | 1 | 0 | Scale Across 1 |
| [[ECOC2026 厂商索引 · AIDC客户#美团\|美团]] | 1 | 0 | Scale Up 1 |
| [[ECOC2026 厂商索引 · AIDC客户#xAI\|xAI]] | 0 | 2 |  |
| [[ECOC2026 厂商索引 · AIDC客户#腾讯\|腾讯]] | 0 | 2 |  |
| [[ECOC2026 厂商索引 · AIDC客户#Starcloud\|Starcloud]] 🌱 | 0 | 1 |  |

🌱 = 初创企业，另见 [[ECOC2026 厂商索引 · 初创企业]]

## Microsoft · Azure

我的笔记：[[00. Microsoft(Azure)]]

- **立场/路线**（厂商地图，涉及方向 1,2,3,4,6）：HCF最积极推动者；scale-up主张宽而慢microLED；OCI Wave1/2
- **关键数字**：400G ZR 3跨427.97 km；microLED目标<1 pJ/bit，自评风险很高；12,000 km+ HCF计划
- **立场/路线**（厂商地图，涉及方向 1,2）：零色散电信级损耗HCF；400G ZR最长HCF传输
- **关键数字**：0.2 dB/km；64×400G，427.97 km
- **立场/路线**（厂商地图，涉及方向 1）：长距双向O+C，190 µm缩径HCF
- **关键数字**：2024 km，GMI 51.9+53.9 Tb/s

**主讲报告（14）**

- [[B06_DAY1_A2-Su3-Su4-无中继空芯光纤#0920-pm-Su4-B-05-MicrosoftAzure-长无中继系统要求.pdf|0920-pm-Su4-B-05-MicrosoftAzure-长无中继系统要求]] · Scale Across · System Requirements for Long Unrepeatered HCF Links
- [[B26_DAY2_Mo3-B-空芯光纤制造与部署#0921-Mo3-B3-待核-空芯光纤制造与部署.pdf|0921-Mo3-B3-待核-空芯光纤制造与部署]] · Transport · 题目页未拍到（p1 起为 "Why Transient Pressure Is Important?"，看图核实，7 管 AR-HCF 几何），内容为空芯光纤拉丝中瞬态压力扰动的热-粘性模型（transient thermo-viscous draw model）
- [[B30_DAY2_Mo4-I-AI互连之争-第二场#0921-Mo4-待定-MicrosoftAzure-AI纵向扩展与通用算力的光互连用例.pdf（第1–10页）|0921-Mo4-待定-MicrosoftAzure-AI纵向扩展与通用算力的光互连用例（第1–10页）]] · Scale Up · 未见原题（p1 为倒拍的 "Key messages" 页，看图核实：近期聚焦 AI scale-up 与通用算力内存解耦；OCI 规范提供多代通用 PHY；Wave 1 引入 OCI 光学用于 scale-up，Wave 2 更紧集成并扩展到内存解耦，VCSEL 成为选项）
- [[B32_DAY2_Mo5-B-空芯光纤设计#0921-Mo5-B1-待核-空芯光纤设计.pdf|0921-Mo5-B1-待核-空芯光纤设计]] · Transport · Hollow Core Fibres: from scientific curiosity to multi-problem solution
- [[B43_DAY3_Tu1-B-空芯光纤在光网络中的应用#0922-Tu1-B3-南安普顿大学-空芯光纤带来的光网络新机会.pdf|0922-Tu1-B3-南安普顿大学-空芯光纤带来的光网络新机会]] · Scale Out · New Opportunities in Optical Networks Enabled by Hollow-Core Fibres（Tu1-B3）
- [[B46_DAY3_Tu1-E-光开关与解复用器#0922-Tu1-E3-Microsoft-宽而慢架构加microLED打破AI网络与内存墙.pdf|0922-Tu1-E3-Microsoft-宽而慢架构加microLED打破AI网络与内存墙]] · Scale Up · Wide-and-slow architecture with microLED to break AI network and memory walls（据文件名与内容概括，原题页未拍到；p1 看图核实为 "The talk in one slide"：互连是扩展瓶颈，光学可根本改变 AI 系统构建，需超越功耗、全栈协同优化、打破采用僵局）
- [[B51_DAY3_Tu3-H-长距空芯光纤系统#0922-Tu3-H1-MicrosoftAzureFiber-空芯光纤传输系统从城域到长距.pdf|0922-Tu3-H1-MicrosoftAzureFiber-空芯光纤传输系统从城域到长距]] · Transport · Hollow-Core Fibre Transmission Systems: From Metro to Long-Haul Applications
- [[B51_DAY3_Tu3-H-长距空芯光纤系统#0922-Tu3-H4-MicrosoftAzureFiber-全C波段400GZR经三跨段427.97km空芯光纤传输.pdf|0922-Tu3-H4-MicrosoftAzureFiber-全C波段400GZR经三跨段427.97km空芯光纤传输]] · Scale Across · Demonstration of Full C-band 400G ZR Transmission over 3-Span 427.97-km Hollow-Core Fibre [p1]
- [[B57_DAY4_We-F-标准化专场#0923-We-F-00-标准化专场II连拍.pdf（第11–19页）|0923-We-F-00-标准化专场II连拍（第11–19页）]] · Scale Up · Optical Scale-Up AI Systems: progress in Standards
- [[B70_DAY4_We3-I-空芯光纤表征与标准化#0923-We3-I-00-全场连拍-空芯表征与部署.pdf（第1–43页）|0923-We3-I-00-全场连拍-空芯表征与部署（第1–43页）]] · Transport · Ultra-high resolution and long-range OFDRs for characterizing and monitoring Hollow-core DNANFs
- [[B70_DAY4_We3-I-空芯光纤表征与标准化#0923-We3-I-00-全场连拍-空芯表征与部署.pdf（第44–67页）|0923-We3-I-00-全场连拍-空芯表征与部署（第44–67页）]] · 新应用 · Distributed Measurement of Magnitude and Orientation of the Local Birefringence Vector in a 5-Tube NANF
- [[B74_DAY5_PDP-A-后期论文A1厅#0924-PDP-A-1-Microsoft与南安普顿大学-C波段电信级损耗零色散空芯光纤首次验证.pdf|0924-PDP-A-1-Microsoft与南安普顿大学-C波段电信级损耗零色散空芯光纤首次验证]] · Transport · First Demonstration of a Zero-Dispersion Hollow-Core Fibre with Telecoms-Grade Loss (0.2 dB/km), in the C-Band
- [[B74_DAY5_PDP-A-后期论文A1厅#0924-PDP-A-2-MicrosoftAzureFiber-TFLN调制器与增益平坦YDFA及低损空芯光纤的1um相干传输系统.pdf|0924-PDP-A-2-MicrosoftAzureFiber-TFLN调制器与增益平坦YDFA及低损空芯光纤的1um相干传输系统]] · Transport · A Coherent 1µm Transmission System using TFLN Modulator, Gain-Flattened YDFAs and Low-Loss Hollow-Core Fibre
- [[B74_DAY5_PDP-A-后期论文A1厅#0924-PDP-A-4-Microsoft与Lightera与UCL-缩小外径宽带空芯光纤的双波段双向长距传输-另一版.pdf|0924-PDP-A-4-Microsoft与Lightera与UCL-缩小外径宽带空芯光纤的双波段双向长距传输-另一版]] · Transport · Dual-Band, Bi-Directional Long-Haul Transmission in Reduced Outer Diameter Wideband HCF

> [!quote]- 被提及的报告（21）
> - [[B01_DAY1_A1-Su1-Su2-AI数据中心光源#0920-am-Su1-A-05-Columbia-片上光源与系统.pdf|0920-am-Su1-A-05-Columbia-片上光源与系统]] · Scale Up
> - [[B02_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第2–13页）|0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描（第2–13页）]] · Scale Up
> - [[B03_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3-A-01-LightCounting-AI连接硬件市场.pdf|0920-pm-Su3-A-01-LightCounting-AI连接硬件市场]] · Scale Up
> - [[B04_DAY1_A2-Su1-Su2-光通信功耗墙#0920-am-Su1-B-04-Broadcom-AI集群高速IO.pdf|0920-am-Su1-B-04-Broadcom-AI集群高速IO]] · Scale Up
> - [[B05_DAY1_A2-Su3-Su4-无中继空芯光纤#0920-pm-Su3-B-01-长飞YOFC-长跨空芯光纤设计.pdf（第1–6页，Workshop 开场/组织者页）|0920-pm-Su3-B-01-长飞YOFC-长跨空芯光纤设计（第1–6页，Workshop 开场／组织者页）]] · Transport
> - [[B05_DAY1_A2-Su3-Su4-无中继空芯光纤#0920-pm-Su3-B-01-长飞YOFC-长跨空芯光纤设计.pdf（第19–37页；同讲另见 B-02 文件）|0920-pm-Su3-B-01-长飞YOFC-长跨空芯光纤设计（第19–37页；同讲另见 B-02 文件）]] · Transport
> - [[B05_DAY1_A2-Su3-Su4-无中继空芯光纤#0920-pm-Su3-B-05-Lightera-铋掺放大器高功率.pdf（第1–11页）|0920-pm-Su3-B-05-Lightera-铋掺放大器高功率（第1–11页）]] · Transport
> - [[B06_DAY1_A2-Su3-Su4-无中继空芯光纤#0920-pm-Su4-B-02-NokiaBellLabs-空芯链路性能极限.pdf|0920-pm-Su4-B-02-NokiaBellLabs-空芯链路性能极限]] · Transport
> - [[B08_DAY1_C1.1-Su3-Su4-异构光网络管理#0920-pm-Su3-D-02-Southampton-空芯光纤技术方.pdf（第1–6页）|0920-pm-Su3-D-02-Southampton-空芯光纤技术方（第1–6页）]] · Transport
> - [[B14_DAY1_E1-Su1-Su2-集成光子产品化#0920-am-Su1-C-02-imec-IClink-欧洲芯片设计平台与MPW.pdf|0920-am-Su1-C-02-imec-IClink-欧洲芯片设计平台与MPW]] · Scale Out
> - [[B15_DAY1_E1-Su3-Su4-AI与端到端光网络#0920-pm-Su4-C-03-华为-算网一体设计.pdf|0920-pm-Su4-C-03-华为-算网一体设计]] · Scale Across
> - [[B20_DAY1_PV-R-Su3-Su4-窄快还是宽慢#0920-pm-Su4-I-07-Credo-电互连路线.pdf|0920-pm-Su4-I-07-Credo-电互连路线]] · Scale Up
> - [[B22_DAY2_MF-0921-下午-模块与子系统#0921-MF-pm-1500-HeraeusCovantics-面向AI数据中心的下一代光纤.pdf|0921-MF-pm-1500-HeraeusCovantics-面向AI数据中心的下一代光纤]] · Scale Up
> - [[B26_DAY2_Mo3-B-空芯光纤制造与部署#0921-Mo3-B1-领纤Linfiber-打破损耗壁垒-空芯光纤从物理极限到量产.pdf|0921-Mo3-B1-领纤Linfiber-打破损耗壁垒-空芯光纤从物理极限到量产]] · Transport
> - [[B26_DAY2_Mo3-B-空芯光纤制造与部署#0921-Mo3-B2-待核-空芯光纤制造与部署.pdf|0921-Mo3-B2-待核-空芯光纤制造与部署]] · Transport
> - [[B35_DAY2__合集待拆#0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf（第2–14页，Mo3-A2）|0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A（第2–14页，Mo3-A2）]] · Scale Across
> - [[B40_DAY3_MF-0922-上午-器件与IC与PIC与光纤#0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲.pdf|0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲]] · Scale Up
> - [[B41_DAY3_MF-0922-下午-新兴技术#0922-MF-pm-1400-Broadcom-共封装光学之后再谈OCI.pdf|0922-MF-pm-1400-Broadcom-共封装光学之后再谈OCI]] · Scale Up
> - [[B70_DAY4_We3-I-空芯光纤表征与标准化#0923-We3-I-00-全场连拍-空芯表征与部署.pdf（第68–90页）|0923-We3-I-00-全场连拍-空芯表征与部署（第68–90页）]] · Transport
> - [[B71_DAY4_We5-B-光发射机与VCSEL#0923-We5-B-中兴-光发射机与收发.pdf（第1–15页；p8 为与 NVIDIA 讲稿重复页）|0923-We5-B-中兴-光发射机与收发（第1–15页；p8 为与 NVIDIA 讲稿重复页）]] · Scale Across
> - [[B74_DAY5_PDP-A-后期论文A1厅#0924-PDP-A-3-NokiaBellLabs与ASN与长飞-532公里空芯光纤全C波段无中继传输带ROPA达30.66Tbps.pdf|0924-PDP-A-3-NokiaBellLabs与ASN与长飞-532公里空芯光纤全C波段无中继传输带ROPA达30.66Tbps]] · Transport


## Oracle OCI

- **立场/路线**（厂商地图，涉及方向 2,3,4）：TCO判据；1.6T选LRO；建议现在试用CPO/NPO；EBO MSA主席方
- **关键数字**：800G LPO约35万链路；集群2020→2026增8倍至131,072 GPU；区域DWDM约60 km跨段

**主讲报告（10）**

- [[B02_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第24–38页）|0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描（第24–38页）]] · Scale Out · Photonic interconnects for modern AI superclusters（ECOC 2026 Workshop Su3-A）
- [[B03_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3-A-03-Oracle-AI超集群光互连.pdf|0920-pm-Su3-A-03-Oracle-AI超集群光互连]] · Scale Out · Photonic interconnects for modern AI superclusters
- [[B22_DAY2_MF-0921-下午-模块与子系统#0921-MF-pm-1320-Oracle-GW级AI部署的经验.pdf|0921-MF-pm-1320-Oracle-GW级AI部署的经验]] · Scale Out · Lessons learned from GW-scale AI deployments
- [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第1–7页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第1–7页）]] · Scale Across · （无题目页）首页标题 "Coherent technology foundation of scale across"（看图核实：IMDD 距离受限推动 ZR-/CL，ZR 为锚定 DCI 应用，ZR+/ZR++ 延伸更长距）
- [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第8–13页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第8–13页）]] · Scale Out · What's next in datacenter optics?（p8 议程页标题）
- [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第14–32页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第14–32页）]] · Scale Up · The Topic is Density, not Port Size（p14 首页）；主体为 XPO 模块介绍
- [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第33–40页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第33–40页）]] · Scale Up · Reality checking 1.6T+ AI interconnect solutions
- [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第41–45页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第41–45页）]] · Scale Up · Optics for NVIDIA Spectrum-X Multiplane Network Architecture
- [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第46–54页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第46–54页）]] · Scale Up · （标题页未拍到；p46 看图核实为 "Electrical to Photonic Transition Continues"）内容涵盖 Optical connectivity expanding / Integrated optics requires a variety of technologies / Driving the future of pluggable transceivers
- [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第55–63页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第55–63页）]] · Scale Up · Open CPX 相关（Open CPX supporting broad NPO and CPO use cases / Diablo-1 6.4T Open CPX engine），标题栏被裁切

> [!quote]- 被提及的报告（1）
> - [[B40_DAY3_MF-0922-上午-器件与IC与PIC与光纤#0922-MF-am-1220-EBOMSA-EBOMSA可靠且可互通的光互连.pdf|0922-MF-am-1220-EBOMSA-EBOMSA可靠且可互通的光互连]] · Scale Up


## Meta

- **立场/路线**（厂商地图，涉及方向 1,4）：骨干去转发器；海缆2 Pbps@TA现有供电下不可能；SerDes主导功耗
- **关键数字**：骨干降功耗约80%；Petal（预计2029，法美约7,000 km，>1 Pbps）首条大规模部署MCF的海缆；OCI约5×/端口
- **立场/路线**（厂商地图，涉及方向 1）：实时海缆跨太平洋800G
- **关键数字**：18 Tb/s，16,608 km

**主讲报告（4）**

- [[B04_DAY1_A2-Su1-Su2-光通信功耗墙#0920-am-Su1-B-01-Meta-AI数据中心功耗.pdf|0920-am-Su1-B-01-Meta-AI数据中心功耗]] · Scale Up · Standard Optic's Perspective on Power Savings（首页标题；无独立总题页）
- [[B21_DAY2_MF-0921-上午-模块与子系统#0921-MF-am-T08-1220-Meta-骨干光纤基础设施扩展.pdf|0921-MF-am-T08-1220-Meta-骨干光纤基础设施扩展]] · Transport · Scaling the Backbone Fabric — Physical infrastructure for the AI era（页内 "The network must lead"）
- [[B28_DAY2_Mo3-G-海底与无中继系统#0921-Mo3-G1-Meta-超petabit海缆的技术与挑战.pdf|0921-Mo3-G1-Meta-超petabit海缆的技术与挑战]] · Transport · Technologies and Challenges for beyond Petabit Submarine Cable
- [[B28_DAY2_Mo3-G-海底与无中继系统#0921-Mo3-待定-Ciena-无中继海缆系统.pdf|0921-Mo3-待定-Ciena-无中继海缆系统]] · Transport · Algorithmically-Optimized Real-Time 18 Tb/s Throughput over a 16,608 km Trans-Pacific Subsea Link

> [!quote]- 被提及的报告（18）
> - [[B01_DAY1_A1-Su1-Su2-AI数据中心光源#0920-am-Su1-A-05-Columbia-片上光源与系统.pdf|0920-am-Su1-A-05-Columbia-片上光源与系统]] · Scale Up
> - [[B02_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第24–38页）|0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描（第24–38页）]] · Scale Out
> - [[B02_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第99–107页）|0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描（第99–107页）]] · Scale Across
> - [[B03_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3-A-03-Oracle-AI超集群光互连.pdf|0920-pm-Su3-A-03-Oracle-AI超集群光互连]] · Scale Out
> - [[B03_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su4-A-03-Acacia-PAM4-DSP竞争.pdf|0920-pm-Su4-A-03-Acacia-PAM4-DSP竞争]] · Scale Across
> - [[B04_DAY1_A2-Su1-Su2-光通信功耗墙#0920-am-Su1-B-04-Broadcom-AI集群高速IO.pdf|0920-am-Su1-B-04-Broadcom-AI集群高速IO]] · Scale Up
> - [[B14_DAY1_E1-Su1-Su2-集成光子产品化#0920-am-Su1-C-02-imec-IClink-欧洲芯片设计平台与MPW.pdf|0920-am-Su1-C-02-imec-IClink-欧洲芯片设计平台与MPW]] · Scale Out
> - [[B14_DAY1_E1-Su1-Su2-集成光子产品化#0920-am-Su1-C-03-STMicro-硅光平台.pdf|0920-am-Su1-C-03-STMicro-硅光平台]] · Scale Out
> - [[B18_DAY1_PV-R-Su1-Su2-绿色AI数据中心与接入#0920-am-Su1-I-05-DTU-ICT可持续性评估.pdf|0920-am-Su1-I-05-DTU-ICT可持续性评估]] · Transport
> - [[B20_DAY1_PV-R-Su3-Su4-窄快还是宽慢#0920-pm-Su4-I-07-Credo-电互连路线.pdf|0920-pm-Su4-I-07-Credo-电互连路线]] · Scale Up
> - [[B21_DAY2_MF-0921-上午-模块与子系统#0921-MF-am-T01-1000-Acacia-跨域与横向扩展网络策略.pdf|0921-MF-am-T01-1000-Acacia-跨域与横向扩展网络策略]] · Scale Across
> - [[B22_DAY2_MF-0921-下午-模块与子系统#0921-MF-pm-1320-Oracle-GW级AI部署的经验.pdf|0921-MF-pm-1320-Oracle-GW级AI部署的经验]] · Scale Out
> - [[B22_DAY2_MF-0921-下午-模块与子系统#0921-MF-pm-1500-HeraeusCovantics-面向AI数据中心的下一代光纤.pdf|0921-MF-pm-1500-HeraeusCovantics-面向AI数据中心的下一代光纤]] · Scale Up
> - [[B23_DAY2_Mo12-A-开幕与大会报告#0921-Mo12-00-全场-开幕与大会报告全场连拍.pdf（第1–36页，Ciena大会报告）|0921-Mo12-00-全场-开幕与大会报告全场连拍（第1–36页，Ciena大会报告）]] · Scale Up
> - [[B24_DAY2_Mo12-A-开幕与大会报告#0921-Mo12-A3-Ciena-AI集群通信.pdf（共33页，单讲）|0921-Mo12-A3-Ciena-AI集群通信（共33页，单讲）]] · Scale Up
> - [[B41_DAY3_MF-0922-下午-新兴技术#0922-MF-pm-1400-Broadcom-共封装光学之后再谈OCI.pdf|0922-MF-pm-1400-Broadcom-共封装光学之后再谈OCI]] · Scale Up
> - [[B53_DAY4_MF-0923-市场聚焦#0923-MF-00-上午连拍.pdf（第39–53页）|0923-MF-00-上午连拍（第39–53页）]] · Scale Up
> - [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第33–40页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第33–40页）]] · Scale Up


## Google

- **立场/路线**（厂商地图，涉及方向 2,3）：功耗为终极约束；HyperRail多rail；OCS主要用户
- **关键数字**：1.6T ZR++ <45 W为风冷天花板；200G FR4失效以LD为主43.4%（他人引用）

**主讲报告（2）**

- [[B04_DAY1_A2-Su1-Su2-光通信功耗墙#0920-am-Su2-B-01-Google-ScaleAcross功耗.pdf|0920-am-Su2-B-01-Google-ScaleAcross功耗]] · Scale Across · Power Efficient Scale Across – Scaling for the AI Era
- [[B48_DAY3_Tu1-G-短距互连#0922-Tu1-G3-SantAnna-双偏振短距系统群速度色散参数的正则微扰.pdf|0922-Tu1-G3-SantAnna-双偏振短距系统群速度色散参数的正则微扰]] · Scale Out · Regular Perturbation on the Group-Velocity Dispersion Parameter for Dual-Polarization Short-Reach Systems（Tu1-G3）

> [!quote]- 被提及的报告（19）
> - [[B07_DAY1_C1.1-Su1-Su2-楼内光网络#0920-am-Su1-D-05-Nokia-面向IoT与AI的楼内网.pdf|0920-am-Su1-D-05-Nokia-面向IoT与AI的楼内网]] · Access
> - [[B09_DAY1_C2.1-Su1-Su2-星地链路大气湍流#0920-am-Su1-F-03-北邮-星地激光链路湍流影响.pdf|0920-am-Su1-F-03-北邮-星地激光链路湍流影响]] · Scale Across
> - [[B14_DAY1_E1-Su1-Su2-集成光子产品化#0920-am-Su1-C-02-imec-IClink-欧洲芯片设计平台与MPW.pdf|0920-am-Su1-C-02-imec-IClink-欧洲芯片设计平台与MPW]] · Scale Out
> - [[B19_DAY1_PV-R-Su3-Su4-窄快还是宽慢#0920-pm-Su3-I-07-Marvell-DSP与波特率路线.pdf|0920-pm-Su3-I-07-Marvell-DSP与波特率路线]] · Scale Out
> - [[B20_DAY1_PV-R-Su3-Su4-窄快还是宽慢#0920-pm-Su4-I-07-Credo-电互连路线.pdf|0920-pm-Su4-I-07-Credo-电互连路线]] · Scale Up
> - [[B21_DAY2_MF-0921-上午-模块与子系统#0921-MF-am-T02-1020-CignalAI-光电路交换的新应用.pdf|0921-MF-am-T02-1020-CignalAI-光电路交换的新应用]] · Scale Up
> - [[B22_DAY2_MF-0921-下午-模块与子系统#0921-MF-pm-1500-HeraeusCovantics-面向AI数据中心的下一代光纤.pdf|0921-MF-pm-1500-HeraeusCovantics-面向AI数据中心的下一代光纤]] · Scale Up
> - [[B23_DAY2_Mo12-A-开幕与大会报告#0921-Mo12-00-全场-开幕与大会报告全场连拍.pdf（第1–36页，Ciena大会报告）|0921-Mo12-00-全场-开幕与大会报告全场连拍（第1–36页，Ciena大会报告）]] · Scale Up
> - [[B23_DAY2_Mo12-A-开幕与大会报告#0921-Mo12-00-全场-开幕与大会报告全场连拍.pdf（第108–153页，PsiQuantum大会报告）|0921-Mo12-00-全场-开幕与大会报告全场连拍（第108–153页，PsiQuantum大会报告）]] · 新应用
> - [[B24_DAY2_Mo12-A-开幕与大会报告#0921-Mo12-A3-Ciena-AI集群通信.pdf（共33页，单讲）|0921-Mo12-A3-Ciena-AI集群通信（共33页，单讲）]] · Scale Up
> - [[B24_DAY2_Mo12-A-开幕与大会报告#0921-Mo12-A6-PsiQuantum-光子量子计算.pdf（共34页，单讲）|0921-Mo12-A6-PsiQuantum-光子量子计算（共34页，单讲）]] · 新应用
> - [[B40_DAY3_MF-0922-上午-器件与IC与PIC与光纤#0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲.pdf|0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲]] · Scale Up
> - [[B45_DAY3_Tu1-D-光放大#0922-Tu1-D4-NTT-增益平坦滤波器弃光的能量收集.pdf|0922-Tu1-D4-NTT-增益平坦滤波器弃光的能量收集]] · Transport
> - [[B46_DAY3_Tu1-E-光开关与解复用器#0922-Tu1-E4-OneTouch-薄膜钽酸锂8x8光电路交换.pdf|0922-Tu1-E4-OneTouch-薄膜钽酸锂8x8光电路交换]] · Scale Out
> - [[B55_DAY4_MF-0923-市场聚焦#0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf（第8–13页）|0923-MF-00-Marvell与Ciena与Arista与Oracle连拍（第8–13页）]] · Scale Out
> - [[B71_DAY4_We5-B-光发射机与VCSEL#0923-We5-B-中兴-光发射机与收发.pdf（第1–15页；p8 为与 NVIDIA 讲稿重复页）|0923-We5-B-中兴-光发射机与收发（第1–15页；p8 为与 NVIDIA 讲稿重复页）]] · Scale Across
> - [[B77_DAY5_Th1-F-可编程光子学专场上半场#0924-推定F3-哥伦比亚大学-面向AI集群的可编程光子学.pdf|0924-推定F3-哥伦比亚大学-面向AI集群的可编程光子学]] · Scale Up
> - [[B78_DAY5_Th1-G-光网络中的AI训练#0924-Th1-G3-北邮-A2A协议增强的多智能体协同实现自治光网络服务开通.pdf|0924-Th1-G3-北邮-A2A协议增强的多智能体协同实现自治光网络服务开通]] · Transport
> - [[B81_DAY5_Th2-B-偏振态传感与应用#0924-Th2-C1-北邮与中科院-模式分集接收与自适应光学增强的星地自由空间光链路.pdf（第1–19页）|0924-Th2-C1-北邮与中科院-模式分集接收与自适应光学增强的星地自由空间光链路（第1–19页）]] · Access


## OpenAI

我的笔记：[[01. OpenAI Jalapeño 芯片规格与 Scale-up 组网]]

- **立场/路线**（厂商地图，涉及方向 3,4）：以请求延迟与每请求能耗比较互连；铜今天够用，慢宽需可靠性证明
- **关键数字**：自研Jalapeño 128/2048颗两级Clos（TH6），同吞吐延迟约低1.8倍（对GB300，自报）

**主讲报告（4）**

- [[B02_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第14–23页）|0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描（第14–23页）]] · Scale Up · AI Scale-Up Networks: Requirements for Reliable, High-Bandwidth-Density Interconnects（p14 标题页，看图核实）
- [[B03_DAY1_A1-Su3-Su4-下一代可插拔架构#0920-pm-Su3-A-02-OpenAI-ScaleUp互连需求.pdf|0920-pm-Su3-A-02-OpenAI-ScaleUp互连需求]] · Scale Up · AI Scale-Up Networks: Requirements for Reliable, High-Bandwidth-Density Interconnects
- [[B04_DAY1_A2-Su1-Su2-光通信功耗墙#0920-am-Su1-B-02-OpenAI-ScaleUp还能用铜吗.pdf|0920-am-Su1-B-02-OpenAI-ScaleUp还能用铜吗]] · Scale Up · AI scale-up – Does copper still do the job?
- [[B19_DAY1_PV-R-Su3-Su4-窄快还是宽慢#0920-pm-Su4-I-02-OpenAI-ScaleUp需求.pdf|0920-pm-Su4-I-02-OpenAI-ScaleUp需求]] · Scale Up · Fast/Narrow or Slow/Wide? Choosing for Bandwidth Density and Reliability

> [!quote]- 被提及的报告（8）
> - [[B01_DAY1_A1-Su1-Su2-AI数据中心光源#0920-am-Su1-A-05-Columbia-片上光源与系统.pdf|0920-am-Su1-A-05-Columbia-片上光源与系统]] · Scale Up
> - [[B04_DAY1_A2-Su1-Su2-光通信功耗墙#0920-am-Su1-B-04-Broadcom-AI集群高速IO.pdf|0920-am-Su1-B-04-Broadcom-AI集群高速IO]] · Scale Up
> - [[B15_DAY1_E1-Su3-Su4-AI与端到端光网络#0920-pm-Su4-C-03-华为-算网一体设计.pdf|0920-pm-Su4-C-03-华为-算网一体设计]] · Scale Across
> - [[B20_DAY1_PV-R-Su3-Su4-窄快还是宽慢#0920-pm-Su4-I-07-Credo-电互连路线.pdf|0920-pm-Su4-I-07-Credo-电互连路线]] · Scale Up
> - [[B41_DAY3_MF-0922-下午-新兴技术#0922-MF-pm-1400-Broadcom-共封装光学之后再谈OCI.pdf|0922-MF-pm-1400-Broadcom-共封装光学之后再谈OCI]] · Scale Up
> - [[B53_DAY4_MF-0923-市场聚焦#0923-MF-Credo-市场聚焦.pdf|0923-MF-Credo-市场聚焦]] · Scale Out
> - [[B63_DAY4_We2-B-硅光调制器#0923-We2-B1-Lumentum-800G与1.6T硅光发射机量产.pdf|0923-We2-B1-Lumentum-800G与1.6T硅光发射机量产]] · Scale Out
> - [[B71_DAY4_We5-B-光发射机与VCSEL#0923-We5-B-中兴-光发射机与收发.pdf（第1–15页；p8 为与 NVIDIA 讲稿重复页）|0923-We5-B-中兴-光发射机与收发（第1–15页；p8 为与 NVIDIA 讲稿重复页）]] · Scale Across


## 阿里云

- **立场/路线**（厂商地图，涉及方向 3,4）：scale-out用FRO，scale-up LPO→NPO→CPO；纯LPO对LPO部署
- **关键数字**：13,234只LPO现网数据；NPO 32/36 lane来自Huawei/Alibaba/Tencent

**主讲报告（1）**

- [[B35_DAY2__合集待拆#0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf（第36–47页，Mo3-A5）|0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A（第36–47页，Mo3-A5）]] · Scale Out · Large-Scale Deployment of LPO in AI Clusters

> [!quote]- 被提及的报告（2）
> - [[B21_DAY2_MF-0921-上午-模块与子系统#0921-MF-am-T04-1100-华为-NPO与CPO的近期部署平衡.pdf|0921-MF-am-T04-1100-华为-NPO与CPO的近期部署平衡]] · Scale Up
> - [[B40_DAY3_MF-0922-上午-器件与IC与PIC与光纤#0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲.pdf|0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲]] · Scale Up


## Amazon · AWS

> [!quote]- 被提及的报告（4）
> - [[B09_DAY1_C2.1-Su1-Su2-星地链路大气湍流#0920-am-Su1-F-03-北邮-星地激光链路湍流影响.pdf|0920-am-Su1-F-03-北邮-星地激光链路湍流影响]] · Scale Across
> - [[B14_DAY1_E1-Su1-Su2-集成光子产品化#0920-am-Su1-C-03-STMicro-硅光平台.pdf|0920-am-Su1-C-03-STMicro-硅光平台]] · Scale Out
> - [[B20_DAY1_PV-R-Su3-Su4-窄快还是宽慢#0920-pm-Su4-I-07-Credo-电互连路线.pdf|0920-pm-Su4-I-07-Credo-电互连路线]] · Scale Up
> - [[B40_DAY3_MF-0922-上午-器件与IC与PIC与光纤#0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲.pdf|0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲]] · Scale Up


## OVHcloud

- **立场/路线**（厂商地图，涉及方向 1,2）：区域Fabric环；<10 km直连，>10 km用800G ZR+；光保护2027考虑
- **关键数字**：一组区域共享一套服务栈

**主讲报告（1）**

- [[B14_DAY1_E1-Su1-Su2-集成光子产品化#0920-am-Su1-C-00-全场-上半场速记.pdf（第10–17页，OVHcloud）|0920-am-Su1-C-00-全场-上半场速记（第10–17页，OVHcloud）]] · Scale Across · AI Driven Traffic Evolution in the Optical Backbone: OVHcloud's Fibre Constrained Architecture（副题：An OVHcloud traffic vision PoP-DC and DC-DC in the AI era）


## 美团

- **立场/路线**（厂商地图，涉及方向 3,4）：NPO为长期路径，224G为务实窗口
- **关键数字**：无量化

**主讲报告（1）**

- [[B54_DAY4_MF-0923-市场聚焦#0923-MF-美团-市场聚焦.pdf|0923-MF-美团-市场聚焦]] · Scale Up · Rethinking Optical Interconnect for the AI Agent Era


## xAI

> [!quote]- 被提及的报告（2）
> - [[B14_DAY1_E1-Su1-Su2-集成光子产品化#0920-am-Su1-C-03-STMicro-硅光平台.pdf|0920-am-Su1-C-03-STMicro-硅光平台]] · Scale Out
> - [[B19_DAY1_PV-R-Su3-Su4-窄快还是宽慢#0920-pm-Su3-I-02-LightCounting-AI光模块市场数据.pdf|0920-pm-Su3-I-02-LightCounting-AI光模块市场数据]] · Scale Out


## 腾讯

> [!quote]- 被提及的报告（2）
> - [[B04_DAY1_A2-Su1-Su2-光通信功耗墙#0920-am-Su1-B-04-Broadcom-AI集群高速IO.pdf|0920-am-Su1-B-04-Broadcom-AI集群高速IO]] · Scale Up
> - [[B21_DAY2_MF-0921-上午-模块与子系统#0921-MF-am-T04-1100-华为-NPO与CPO的近期部署平衡.pdf|0921-MF-am-T04-1100-华为-NPO与CPO的近期部署平衡]] · Scale Up


## Starcloud

> [!quote]- 被提及的报告（1）
> - [[B09_DAY1_C2.1-Su1-Su2-星地链路大气湍流#0920-am-Su1-F-03-北邮-星地激光链路湍流影响.pdf|0920-am-Su1-F-03-北邮-星地激光链路湍流影响]] · Scale Across

