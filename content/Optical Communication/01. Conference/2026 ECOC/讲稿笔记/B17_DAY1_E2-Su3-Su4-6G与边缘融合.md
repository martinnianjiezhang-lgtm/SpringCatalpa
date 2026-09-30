---
title: "B17 · DAY1 · E2-Su3-Su4-6G与边缘融合"
tags:
  - ECOC2026
  - DAY1
---

# B17 笔记：Su3/Su4-H「Confluence at the edge：面向 6G 及以后的网络」（2026-09-20 下午，10 篇）

说明：数字来自看图核对；仅凭 OCR、未开图的数字标"OCR"。

### 0920-pm-Su3-H-01-主席-6G融合场景导论.pdf
- 讲者/机构：Session 主席（Chalmers University of Technology 标识；具体讲者未在页面上看到）| 题目：无独立英文原题；首页标题 "6G unifies communication, compute and sensing" | 类型：Workshop
- 方向归属（主/次）：主 5 固定与无线接入 / 次 2 Scale-across（边缘算力与光/无线协同）
- 核心主张：
  1. 6G 统一通信、计算、感知；AI-native 网络，"Network for AI & AI for Network" 作为单一端到端 fabric。[p1]
  2. 边缘成为"connected intelligence 的脊髓"：从宽带接入走向 AI 骨干，流量从南北向转东西向，mmWave/THz + 光纤 + FSO 多技术并用。[p2]
  3. 从 convergence 走向 confluence：异构信号端到端保持原生形态（如模拟 RoF 做 CoMP、分布式 MIMO、波束成形，无中间转换），并延伸到跨 device/edge/metro/cloud 的 AI 与算力联合布放。[p3]
- 关键数据：无定量数据。议程列出本场 10 讲（Nokia、Bristol、TCD 两讲、Adtran、ETH、Cambridge、Marvell、NTT 及 Panel）。[p4]
- 提到的公司/客户/产品/标准：ECO-eNET（项目标识），OSaaS，Sensing + DWDM，Analog + digital。[p3]
- 与业界对比或记录声明：无。
- 推荐配图页：p3（confluence 概念图：异构信号原生形态贯通）；p4（本场议程）

### 0920-pm-Su3-H-02-Nokia-时延约束业务.pdf
- 讲者/机构：Nokia Bell Labs（议程列为 Sandip Das，Nokia）| 题目：Access Networks for AI: Enabled by Converged Connectivity, Deterministic Delivery, and Physical Awareness（据议程页 p4 of 01；首页 OCR 不可读）| 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入（PON/FTTR/Optical LAN/光纤传感）/ 次 6 光纤传感 DAS
- 核心主张：
  1. 接入网面向 AI 时代的三项能力：Connect（PON、Optical LAN、Wi-Fi、移动传输融合）、Guarantee（有界时延/低抖动/高可靠）、Observe（光纤感知与可观测性）。[p13]
  2. 通过对 PON 上行调度做确定性设计，使 TSN 流与尽力而为流共存于同一 PON。[p8]
  3. 承载数据的光纤同时可作传感器（DAS/BSS），网络成为传感器。[p11]
- 关键数据：
  - Optical LAN 对比传统 LAN：布线减少 70%，寿命 50+ 年，节能 40%，TCO 节省 50%（Nokia 自述收益）；传统 LAN 能耗 180 kWh/user/year，设备/线缆每 5–10 年更新。[p5]
  - PON 上行调度：125 μs 帧；两个 TSN 应用（App-1、App-2）经调度冲突消解后，抖动分别标注 <1 μs 和 <10 μs（原图抖动标注在右下小图，字迹较小，读数按图面）。[p8]
  - 工业 AI over PON 例子：虚拟 PLC 与分布式 I/O 之间经 PROFINET/TSN 通过 PON 传输；页面给出上/下行时延直方图，坐标数值看不清（下行分布集中在约 21–22 的量级，单位看不清）。[p9]
  - DAS 商用 PON 现场试验：可探测触发振动并沿光纤定位；三类事件：drop 1 上落物、drop 1 上弯折、机柜晃动。[p11]
  - 数字孪生/可观测性页（导入 birth certificates、as-built 文件、实时资产清册、拓扑视图）无数值。[p12，OCR]
- 提到的公司/客户/产品/标准：Balluff（合作，Celtic-Next 旗舰项目 SUSTAINET）；PROFINET、TSN、TDM-PON、25G-PON（引用 ECOC 2025 Straub DAS 论文）；关联论文 Sandip Das et al., "A Deterministic Bandwidth-Mapper Scheme in Upstream TDM-PON for Time-Sensitive Industrial AI Applications"，ECOC2026 Tu1-F2。[p8, p9, p11]
- 与业界对比或记录声明：无 SOTA 声明。
- 推荐配图页：p5（Optical LAN vs 传统 LAN 及 70/40/50% 收益）；p8（PON 确定性调度示意）；p11（PON 上 DAS 场景）

### 0920-pm-Su3-H-03-Bristol-英国6G计划复盘.pdf
- 讲者/机构：Dimitra Simeonidou / University of Bristol（Smart Internet Lab、JOINER 平台主任）| 题目：UK R&D Ecosystem on Future Networks Technologies and Systems: Including 6G, 6G+（议程页题为 Confluence drivers and the UK 6G program）| 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入（6G/融合研究生态）/ 次 2 Scale-across（NTN、跨域实验平台）
- 核心主张：
  1. 英国 Future Connectivity Hubs（£250m）由 TITAN、CHEDDAR、HASC、JOINER 四个 Hub 加 Federated Telecoms Hubs（FTH，负责 IP、标准化、商业化）构成。[p2]
  2. JOINER 是国家级实验平台，为 6G+ 技术提供真实规模、异构性的验证环境。[p2, p7–p12]
  3. JOINER Space Lab 定位为英国首个未来空间网络开放研究实验室。[p12]
- 关键数据：
  - 两年资助成果：1500+ 论文，20+ 专利/许可/披露，12+ 衍生公司，35 所英国高校参与，£30M 撬动资金，约 178 名研究与支持人员，30% 时间用于技能培训；涉及 3GPP、ETSI、IEEE 标准及与 OFCOM 的频谱监管工作。[p4]
  - JOINER 2024 年 2 月获资助，2025 年 4 月起运行（OCR）。[p7]
  - JOINER 网络：14 个站点之间 10–40 Gbps 二层传输（JISC 与 Heanet 覆盖爱尔兰），并利用现有 NDFF 光层连接 Bristol、Cambridge、Southampton、UCL；含 GEO/LEO 卫星链路（OCR）。[p9]
  - Nomadic Terminal：VW Multivan 插电混动，含 Starlink LEO、Ruckus WiFi7、Benetel RAN650 O-RU、BubbleRAN CU/DU/RIC、Attocore/OpenSGS 5G Core；最多 5 小时离网运行，最高 5 kW 负载（OCR）。[p11]
  - JOINER Space Lab：初期 3 颗白盒 LEO 卫星，射频+光载荷，支持含抗量子在内的新波形；至少 3 个地面段（另有 ESA Harwell 5G/6G AI hub）；至少 10 个战略用例。[p12]
- 提到的公司/客户/产品/标准：TITAN（Harald Haas）、CHEDDAR（Julie McCann）、HASC（Dominic O'Brien）、JOINER；UKRI/EPSRC；ESA Harwell；Starlink；mATRIC（多接入 RIC）。[p2, p10–p12]
- 与业界对比或记录声明：无 SOTA 声明；为项目成果汇报。
- 推荐配图页：p4（两年成果汇总）；p12（JOINER Space Lab）

### 0920-pm-Su3-H-04-Trinity-致密化与韧性.pdf
- 讲者/机构：Dan Kilper / Trinity College Dublin（CONNECT，ECO-eNET 项目，6G SNS 资助）| 题目：Addressing Densification and Resilience Through Confluence（据议程页；首页 OCR 乱码）| 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入（无线-光融合网络）/ 次 2 Scale-across（边缘云与集中化）
- 核心主张：
  1. 小基站致密化配合边缘数据中心集中处理基带，可降低能耗；但集中化带来对故障敏感、跳数增加的代价。[p4, p5, p7]
  2. 在城域网中引入无线（FSO/THz，Tb/s 级）网状链路，可以缩短跳数并提高对节点故障的韧性，只需少量 mesh 连接即可获得大部分收益。[p8, p14, p15]
  3. 目前仍处于早期，收益与挑战尚待理解；保护策略尚未考虑。[p14, p15]
- 关键数据：
  - 边缘云时延 <1 ms，核心云 >20 ms（OCR 与图示一致）。[p4]
  - O-RAN 功耗模型（Tariq, Raj, Kilper, ICC 2025）：基带处理集中在数据中心时每用户总功率最低；O-RU 数量 0–100 内，每用户处理功率随 RU 增多下降（图 a），传输功率基本不随 O-RU 数变化（图 b）。[p5]
  - 仿真参数：11 个核心节点，每条分配链路 4 个分配节点，每分配节点 2 个基站；核心节点间距 20–30 km，分配节点间距 4–6 km，基站到分配节点 0.2–1 km；有线链路 1.6 Tbps，无线链路 1 Tbps，无线渗透率 α=0.5（α = N_wireless / N_wired）；partial mesh 比例：Access-Access 0.4，Access-Distribution 0.2，Access-Core 0.2，Access-DC 0.2。[p11]
  - 最短路径跳数（α=0.5）：纯有线约 5 跳；纯无线：Access-Access 约 3.3，Access-Dist 约 3，Access-Core 约 2，Access-DC 约 1；Hybrid：约 3.1 / 3.1 / 2.7 / 2.3；Partial Mesh：纯无线约 2.5，Hybrid 约 2.8（柱状图读数，近似）。[p12]
  - 核心节点故障影响的接入节点比例（α=0.5）：纯有线约 22%，纯无线约 4–5%，Hybrid 约 9%（Access-DC 场景 Hybrid 约 2%）；分配节点故障：纯有线约 1.6%，纯无线约 0.3–0.5%，Hybrid 约 0.7–1.1%（读数近似）。[p13]
  - 随 α 从 0.1 到 1：核心节点故障下，纯有线恒约 22%；纯无线由约 1% 升至约 6%；Hybrid 由约 10% 降至约 7%。小结中 Hybrid 跳数约 2.5–3。[p14]
  - 参考论文：A. Gupta et al., "Radio-Optical Confluence in Intelligent Edge Networks," OFC 2026。[p14]
- 提到的公司/客户/产品/标准：O-RAN；引用 Cisco AI 基础设施白皮书、LightCounting、Zayo 长途/城域光纤建设、CONNECT 2025（p6，OCR，页面为引用资料拼贴）。
- 与业界对比或记录声明：无 SOTA 声明。
- 推荐配图页：p11（分层 mesh 拓扑与仿真参数表）；p14（无线渗透率对核心节点故障影响曲线 + 结论）

### 0920-pm-Su3-H-05-Adtran-智能体AI做容量驱动.pdf
- 讲者/机构：Achim Autenrieth / Adtran | 题目：Agentic AI as a capacity driver（据议程页与 p6 标题）| 类型：产业发布/市场分析
- 方向归属（主/次）：主 1 相干/长途/DCI/AI 光网络 / 次 5 固定与无线接入
- 核心主张：
  1. AI 是新的带宽增长驱动（互联网流量增长放缓），AI 驱动新一轮光网络建设周期，光互联需求达 Pb/s 量级。[p3, p4]
  2. Agentic AI：一个意图拆成多个相互依赖的步骤，实时放置于边缘或云；流量变为跨管理域东西向；尾时延优先于平均吞吐，新 KPI 为端到端完成时间与总能耗，"时延与确定性成为容量需求"。[p6]
  3. 对 confluent 6G：网络规划需纳入 AI 负载分布、时延与能耗；边缘在算力与传输之间做仲裁，每个放置决策是无线、接入、光与能量的联合决策。[p7]
- 关键数据：
  - Omdia 数据（2024 版）：光网络交付 petabit 从 2020 年约 130 Pb 增至 2029 年约 1850 Pb；2026 年约 780 Pb，2029 年组成以 800G 线路和 1.2T/1.6T 线路为主（柱状图读数，近似）。[p4]
  - 边缘到云 AI 流量到 2035 年增长 7–8 倍；AI 光互联 2025–2030 年 39% CAGR（页面标注，来源未在页上看清）。[p5]
  - 层级映射：Inter-rack scale-out：800G+ coherent ZR+；Cloud interconnect scale-across：800G DCI IP OLS；训练流量为数据中心间每次运行 PB 级，推理为持续、时延敏感。[p5]
  - 服务商机会：Private connect、MOFN（Managed Optical Fiber Networks）、Spectrum-as-a-service/波长服务。[p3，OCR]
- 提到的公司/客户/产品/标准：Omdia、TeleGeography；OIF Interop Demo（Booth #2126）；本届关联论文 Mo3-I、Tu2-Ex2、Tu2-Ex3（MCP-enabled agentic AI for autonomous IPoDWDM lifecycle automation）、We2-C4；CELTIC-NEXT SUSTAINET-Advance（德国 BMFTR 资助）。[p7, p8]
- 与业界对比或记录声明：无 SOTA 声明。
- 推荐配图页：p4（Omdia 2020–2029 光网络 Pb 量柱状图）；p6（Agentic AI 工作负载与网络后果）

### 0920-pm-Su4-H-01-ETH-等离子体太赫兹通信.pdf
- 讲者/机构：Jasmin Smajic / ETH Zürich, Institute of Electromagnetic Fields（与 Polariton 相关，p10 出现 Polariton 标识）| 题目：Plasmonic devices approaching 1 THz（据议程页）| 类型：邀请报告
- 方向归属（主/次）：主 3 Scale-out 调制器/高波特率器件 / 次 5 固定与无线接入（RoF、sub-THz）
- 核心主张：
  1. 等离子体调制器与探测器是目前已演示最快的器件（slide 原话 "Fastest demonstrated components so far"）。[p10]
  2. 光-THz 一体的 RF 无源系统（等离子体片上天线）可做 sub-THz-to-optical 接收。[p2, p11]
  3. 已在苏黎世做 5.5 km 户外 sub-THz 实验（2026 年 7/8 月）。[p12–p13]
- 关键数据：
  - 等离子体技术特点（OCR，未开图核对）：调制器+天线占位 <1–3 mm²（OCR 不清），VπL=200 V·μm，损耗 0.5 dB/μm，场增强 >40,000，带宽 1 THz 及以上。[p2]
  - 频响：Hoessbacher 2017 >170 GHz、100 GBd NRZ；Burla 2019 500 GHz MZM；Salamin 2019 探测器 2.4 THz。[p6]
  - Horst et al., Optica 12, 325–328 (2025)：超宽带 MHz–THz 等离子体 EO 调制器，扫描 10 MHz–1.140 THz，3 dB 带宽在 1 THz 附近（图中 3 dB 线在约 1000 GHz 上下）；页 10 写 bandwidth 980 GHz。[p7, p10]
  - 调制器功耗（Heni et al., Nat. Commun. 2019）：有源长度 20 μm，400 Gbit/s，"most compact 400G modulator"；100 GBd QPSK 200 Gbit/s BER 1.4e-3，能耗 0.61 fJ/bit；50 GBd 16QAM 200 Gbit/s BER 2.0e-2，0.30 fJ/bit；50 GBd QPSK 100 Gbit/s BER 2.0e-4，0.36 fJ/bit；25 GBd QPSK 50 Gbit/s BER 2.0e-3，0.07 fJ/bit。[p9]
  - 等离子体探测器（Koepfli et al., Science 380, 2023）：石墨烯超材料，带宽 >500 GHz，数据率 132 Gbit/s，响应度 1.5 mA/W @ 1550 nm，尺寸 10 μm x 10 μm，CMOS 兼容。[p10；p11 标 >500 GHz]
  - RF 无源等离子体天线链路：32 GBd QAM4，64 Gbit/s，BER 1.44e-2，GMI 1.888，AIR 60.41 Gbit/s；40 GBd QAM4，80 Gbit/s，BER 2.15e-2，GMI 1.834，AIR 73.36 Gbit/s。[p12]
  - 苏黎世实验（2026 年 7/8 月）：5.5 km，高差 312 m，主要穿越城区，跨 3 条水道，数据率 138.6 Gbit/s。[p13]
- 提到的公司/客户/产品/标准：Polariton；引用 Bitter et al. OFC 2024（160 Gbps 直接 subTHz-to-optical 转换 1400 m）。[p11–p12]
- 与业界对比或记录声明：调制器/探测器被称为"fastest demonstrated components so far"；400G 调制器"most compact"。[p9, p10]
- 推荐配图页：p8（10 MHz–1.14 THz 频响）；p10（探测器+调制器带宽并列）；p13（5.5 km 实验）

### 0920-pm-Su4-H-02-Cambridge-无线光与射频融合.pdf
- 讲者/机构：Iman Tavakkolnia / University of Cambridge（TITAN Hub；LiFi R&D Centre；Satellite Applications Catapult）| 题目：Confluence at the Edge: Optical Wireless | 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入（FSO/OWC/融合）/ 次 2 Scale-across
- 核心主张：
  1. FSO 已可提供类光纤容量（多 Tb/s 地面链路、>100 Gb/s 卫星下行）；下一挑战是网络集成而非原始吞吐：透明传输、通用接口、多厂商标准。[p14]
  2. 大气仍是系统设计的一部分：衰减、湍流、光束漂移、指向影响可用性，需要 PAT、自适应光学、自适应和/或分集。[p14]
  3. Confluence 改变可靠性问题：FSO 不必取代光纤或射频，可作为联合编排的光纤-无线-光网络中的动态开通高容量路径。[p14, p11]
- 关键数据：
  - FSO 演示对比表：van Vliet et al. OFC 2025，Eindhoven 屋顶 4.6 km，5.7 Tb/s，相干、WDM、DP-IQ 4/8/16-QAM、22 通道；Bai et al. Optics Express 2025，跨青海湖 104.8 km，112 Gb/s 单波长；NICT 2025，东京城区 7.4 km，2 Tb/s（5x400 Gb/s WDM）；Kyriazi et al. OFC 2026，现场 FSO/光纤，0.75 km，480 Gb/s，相干+IM/DD 混合；Li et al. Commun. Eng. 2025，室外 1 km，100 Gb/s QPSK 相干。[p4]
  - 5G RAN 透明集成：CPRI 线路速率 Rate-2 到 Rate-4（1.2288–3.0720 Gbps）被框出；功耗：短距 OWC（1–10 m）约 3 W 量级，长距 OWC（50–500 m）<20 W，微波回传约 54 W（柱状图读数）。[p8]
  - 混合 THz(300 GHz)/FSO(1550 nm) 2025 年 11 月一个月天气实测：THz 单独容量约 60–105 Gbps；FSO 大部分时间高，但在天气事件下跌至约 15 Gbps；并行混合约 150–230 Gbps；切换混合约 95–128 Gbps。图注 "submitted to IEEE PTL"（读数近似）。[p13]
  - Ethernet-over-OWC 原型：双向 1 Gb/s，VCSEL 直调，1 m 光学无线信道，PIN 探测，无 DSP/均衡。[p9，OCR]
  - 剑桥 450 nm VLC 1.2 km 链路（电气工程系至大学图书馆）。[p5，OCR]
- 提到的公司/客户/产品/标准：Taara、Starlink、pureLiFi；IEEE 802.11bb（LiFi）、802.15.13、802.15.7；NICT；ECO-eNET 十项技术 A–J 的 confluent mesh 图；HAP 中心的飞行自组网。[p2, p3]
- 与业界对比或记录声明：无自身 SOTA；引用他人 5.7 Tb/s（4.6 km）、112 Gb/s（104.8 km）等纪录。[p4]
- 推荐配图页：p4（FSO 演示对比表）；p13（THz/FSO 混合一个月容量曲线）

### 0920-pm-Su4-H-03-Trinity-智能体驱动的跨域自治.pdf
- 讲者/机构：Merim Dzaferagić / Trinity College Dublin（IRIS：Network AI and Sensing group）| 题目：From AI Agents to Network Actions: Enabling Cross-Domain Autonomous Control | 类型：学术论文/邀请报告
- 方向归属（主/次）：主 1 AI光网络（含 AI 控制面/数字孪生）/ 次 5 固定与无线接入
- 核心主张：
  1. Agency 是系统属性而非模型属性：去掉控制环，代理即消失（即使模型很强）。[p2]
  2. AI-Native Network Controller（AI-NNC）：LLM 代理经 MCP Server 与 FastAPI，配合命令校验器（"Safety Shield"）、模型管理、数字孪生与高效数据存储，控制光/RAN/核心网节点。[p3–p6]
  3. 光网络控制实测：越靠近意图层成功率越高，接近设备层直接操控时成功率显著下降。[p8]
- 关键数据：
  - 六个光网络控制场景及成功目标：Equalize（ROADM booster 输出功率在端口均值 0.5 dB 内）、Flatten（全部 booster 输出 0.5 dB 平坦）、Hitless Add（新信道 BER ≤ 3.8x10^-3，受保护信道裕量损失 ≤ 0.5 dB）、Provision（BER ≤ 3.8x10^-3）、Recover（EDFA 欠增益故障后满足 BER 与裕量阈值）、Reroute（经不相交路径，终端 BER ≤ 3.8x10^-3）。[p7]
  - 成功率（每个接口-场景 10 次运行），列顺序 Equalize/Flatten/Hitless/Provision/Recover/Reroute：Intent 10/10 全部；Network 10、9、1、9、9、5（/10）；Device+ 7、0、6、10、1、0；Device 4、0、6、9、3、0。[p8]
- 提到的公司/客户/产品/标准：MCP（Model Context Protocol）、FastAPI、Redis、ZMQ；ROADM、EDFA。研究组方向还含量子网络、光纤传感、AR 智能控制、接入虚拟化。[p3, p9]
- 与业界对比或记录声明：无 SOTA 声明。
- 推荐配图页：p8（四种接口 x 六场景成功率热图）；p5（AI-NNC 架构）

### 0920-pm-Su4-H-04-Marvell-城域收发机.pdf
- 讲者/机构：Annina Moser / Marvell（议程页姓名为 OCR 转写）| 题目：High-speed transceivers: from AI datacenters to the 6G network | 类型：产业发布
- 方向归属（主/次）：主 4 Scale-up/in CPO（硅光/等离子体调制器、Photonic Fabric）/ 次 5 固定与无线接入（6G xhaul）
- 核心主张：
  1. AI 基础设施连接覆盖从公里到毫米的四个层级。[p3]
  2. 铜缆到光的过渡随带宽提升而向更近距离推进；scale-up 采用 Photonic Fabric + Si-Ge EAM。[p5, p8–p9]
  3. 等离子体调制器可比 SiPh 相位调制器小约 500 倍，且无需行波电极与 50 Ω 端接。[p14, p16]
  4. 同一光子平台 + 器件 + 封装 + 固件的组合覆盖 AI 数据中心与 6G xhaul，附加需求为确定性时延、抖动预算、无线同步、户外加固。[p18]
- 关键数据：
  - 距离层级：Scale-across 分布式 DC 最多 1,000 km+；Scale-out 数据中心最多 500 m+；Scale-up 机架 2.5–7 m；Scale-in 封装 <10 mm。[p3]
  - 铜缆可达距离随速率：100G 5 m；200G（"TODAY"）2.5 m；400G 1.25 m；800G 0.6 m；1.6T 0.3 m。[p5]
  - Si-Ge EAM（Franz-Keldysh 效应）：80 °C 温度范围内可靠工作；1 dB 光带宽 >30 nm；温度系数 <0.8 nm/°C；4–8 个 WDM 波长；Photonic Fabric Link 含外置激光源 ELS、FAU、4/5 nm EIC。[p8]
  - 网络分工：Teralynx 以太网用于 scale-out；Photonic Fabric（PFLink、PF Memory Appliance）用于 scale-up，内存寻址。[p9]
  - 等离子体调制器：SiPh 相位调制器典型长度 5 mm，等离子体 10 μm（500 倍缩小）；标准 SiPh EO 响应约 60 GHz（示意图，页面未给出等离子体带宽数值）；MIM 槽波导尺寸约 100 nm，填充有机电光（OEO）材料；已集成在 imec 200 mm SiPh 平台上，金及等离子体材料后处理待转移到代工厂。[p13, p14, p16；p12 OCR]
  - 光子平台图谱（OCR）：MZM/TFLN、SiPho（高速长距）；MRM（超低功耗高密度）；EAM；pLED、μVCSEL（短距高密度）；等离子体（超快超紧凑）。[p7]
- 提到的公司/客户/产品/标准：Marvell Photonic Fabric、PFLink、Teralynx；imec；展台 Stand 2002；后续报告：Claudia Hoessbacher（Mon 21 Sep Symposium "Winning Interconnects for AI"、Tue 22 Sep EPIF Polariton 主题）、Russ Esmacher（Tue 22 Sep Market Focus "Scale across architecture"）。[p19]
- 与业界对比或记录声明：无正式 SOTA 声明；"500x smaller" 为相对 SiPh 调制器的对比。[p14]
- 推荐配图页：p3（四级 scale 距离）；p5（铜缆距离-速率）；p8（Si-Ge EAM 与 Photonic Fabric Link 结构）；p14（等离子体 500x 缩小）

### 0920-pm-Su4-H-05-NTT-IOWN频谱与数字孪生.pdf
- 讲者/机构：Toru Mano / NTT | 题目：IOWN perspective on optical spectrum and network digital twins | 类型：邀请报告
- 方向归属（主/次）：主 1 相干/长途/DCI/AI光网络 / 次 2 Scale-across
- 核心主张：
  1. 分布式 AI 系统需要更多数据中心间连接；许多光网络仍有大量闲置频谱，光频谱即服务（OSaaS）可把它变现。[p2, p11]
  2. 多域/多运营商环境中的主要挑战是物理层不确定性：对方域内的光纤损耗、放大器 NF/增益、ROADM 滤波设置、信道装载均未知。[p6]
  3. 光网络数字孪生（ONDT）结合网络测量与物理模型，估计未知物理状态，用于设计、分析与控制。[p7, p11]
- 关键数据：
  - 频谱占用统计图（引用 JOCN 文章）：占用率 <20%、20–40%、40–60%、60–80%、>80% 的网络数量分别约为 8、8、9、6、2（横轴 0–10 的柱状图读数，近似）。[p2]
  - 引用 CignalAI（NANOG93）：可插拔相干模块 400G/800G/1.6T 预测，标注"AI effect: almost 2x growth in one year"。[p2]
  - OFC 2026 演示：多厂商 ROADM 连接多个光域，同时承载相干和 IMDD 信号，验证跨域基本光互联；只聚焦 U-plane（受控制器能力限制）；与 OpenLab/OpenROADM 协作；参与厂商在图中包括 Nokia、Ciena、NEC、Infinera 等（图面标识）。[p5]
  - 关键技术：GN 模型（GNPy）线路 QoT 模型 + 收发器模型；端点测量与控制：Digital Longitudinal Monitoring（DLM，由接收信号得到光纤功率分布/参数）与 OLS calibration（由接收谱得到 EDFA 增益与 NF 曲线）。[p8]
  - 现场试验：多厂商线路系统约 300 km；Galway 至 Dublin，长途暗光纤 280 km（段长 45/70/70/65/20 km，经 Cappagh、Ories、Moyfin、Citywest 四个 ILA 站点），城域 50 km 光纤盘；光纤与放大器设置事先未知。[p9]
  - 结果：QoT 预测误差约 1 dB，整个过程约 6 小时；流程为 Observe（DLM → 光纤参数）→ Estimate & optimize（OLS 校准 → 放大器设置）→ Provision（GSNR → 模式选择 → TRx 配置）；图 b 各节点 GSNR 约 18.3–21.5 dB 范围（193–195 THz 附近，读数近似）；图 c 优化前后功率分布，优化后光纤末段功率整体抬升，约 300+ km 范围。[p10]
- 提到的公司/客户/产品/标准：IOWN Global Forum、Open APN、Open All-Photonic Network Functional Architecture、多域 IOWN 网络功能架构；GNPy；OpenROADM；NICT 资助（adoption 50201）、Research Ireland（CONNECT、Open Ireland、Twilights 项目）；NVIDIA 博客 "scale-across networking"（引用）。[p2–p5, p9]
- 与业界对比或记录声明：无 SOTA 声明；结果为端点测量下 QoT 预测误差约 1 dB / 6 小时。
- 推荐配图页：p10（300 km 现场试验结果：GSNR 与功率优化前后）；p9（Galway–Dublin 现场拓扑）；p5（OFC 2026 多厂商跨域演示）

## 本批小结
1. 本场"Confluence"主线：光纤、射频、FSO/THz 不再作为独立网络，而是联合编排的异构路径，以韧性和确定性换取单点容量。证据：主席导论（p3）、TCD Kilper 的混合 mesh 仿真（无线渗透 α=0.5，核心节点故障下纯有线约 22% 接入节点受影响对 Hybrid 约 9%）、Cambridge 的 THz/FSO 一个月混合实测（并行约 150–230 Gbps，单一 FSO 天气下跌至约 15 Gbps）。
2. 无线光/太赫兹的"英雄演示"已经足够快，瓶颈转到集成与标准：Cambridge 汇总 5.7 Tb/s（4.6 km）、112 Gb/s（104.8 km），ETH 苏黎世 5.5 km sub-THz 138.6 Gbit/s；两讲均强调标准、指向/大气与可用性，而非速率。（来自 Cambridge、ETH）
3. 等离子体器件是跨场（接入 6G 与 AI 互联）的共同话题：ETH 演示调制器带宽约 1 THz、20 μm 有源长度 400G，探测器 >500 GHz；Marvell 则以"比 SiPh 相位调制器小 500 倍、无行波电极/50 Ω 端接、已在 imec 200 mm 平台集成"定位 scale-up/scale-in 应用，Polariton 在 ETH 页出现。（来自 ETH、Marvell）
4. AI 让"时延与确定性"进入容量指标：Adtran 提出新 KPI 为端到端完成时间与总能耗，Nokia 用 PON 上行调度把 TSN 抖动压到 <1 μs 与 <10 μs 量级，TCD 的 Kilper 强调集中化的跳数与故障代价；接入侧与光传输侧共享同一逻辑。（来自 Adtran、Nokia、TCD Kilper）
5. 光层自治与数字孪生走向多域实践：NTT 在 Galway–Dublin 约 300 km 多厂商线路上以端点测量在约 6 小时内把 QoT 预测误差压到约 1 dB；TCD Dzaferagić 的 LLM 代理在光网络控制上，意图层接口 10/10，设备层接口在 Flatten/Reroute 场景为 0/10，说明代理直接操作底层设备尚不可靠，需要命令校验与孪生。（来自 NTT、TCD Dzaferagić、Adtran）
6. 光互联层级：Marvell 以 scale-across（≤1,000 km+）/scale-out（≤500 m+）/scale-up（2.5–7 m）/scale-in（<10 mm）划分，Adtran 对应 800G+ coherent ZR+（机架间）与 800G DCI IP OLS（跨 DC），NTT 把闲置频谱通过 OSaaS 用于 scale-across；三者对同一分层给出各自产品/服务映射。（来自 Marvell、Adtran、NTT）
