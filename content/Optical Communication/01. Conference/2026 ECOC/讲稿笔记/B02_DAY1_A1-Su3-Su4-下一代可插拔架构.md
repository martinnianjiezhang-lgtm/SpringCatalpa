---
title: "B02 · DAY1 · A1-Su3-Su4-下一代可插拔架构"
tags:
  - ECOC2026
  - DAY1
---

# B02 笔记：Su3+Su4-A "Meeting Diverse AI Connectivity Needs: Architectural Choices for Next-Generation Pluggable Transceivers"（ECOC 2026 周日 Workshop，A1 下午全场连拍）

说明：本批仅 1 个 PDF（147 页，其中 p124、p135 为重复页），内含 10 位讲者的连拍。下列各节的“pN”均指该 PDF 的页码（非幻灯片自带页码）。组织者（p1）：Andrea Carnio（Nokia）、Adonis Bogris（西阿提卡大学）、Mads Lønstrup Nielsen（NVIDIA）。p69 为 Session 2 “Signal Processing Solutions for AI Connectivity” 引言页，主要问题：更多 DSP、更少 DSP，还是电/光之间更聪明的划分。本批 10 讲均不在“已跳过”名单中（p24–38 的 Oracle 讲为 Su3 下午 Workshop 讲稿，与已跳过的 0920-am-Su1-A-02-Oracle 是不同 PDF/不同场次，故照常处理）。

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第2–13页）
- 讲者/机构：Daryl Inniss（Principal Analyst）/ LightCounting | 题目：未见完整英文原题；p3 议程标题为 “Navigating growth and uncertainty” | 类型：市场分析
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO]；次 [3 Scale-out 光源/调制器]
- 核心主张：
  1. 2026 年是硅光之年，硅光收发器首次超过整体市场 50%，增长预期延续。
  2. 光学正从“通信”（可插拔）走向“计算”（可插拔 + CPO/NPO），光引擎（OE）进入半导体体系，长期看连接市场向半导体生态演化。
  3. Capex 存在牛鞭效应，需谨慎；给出“Scale-up 光互连强劲增长 / CPO 起飞”的情景。
- 关键数据：
  - 收发器销售额按技术堆叠（硅光/InP/GaAs/TFLN、LiNbO3 体材等）2022–2031，标注“2026 硅光首次超过 50%”，Y轴数值看不清 [p4]
  - 四类 AI 网络段：Scale-in（毫米级，“宽而慢”，未来或为光）；Scale-up（约 1 m，“contested”，铜+光，可插拔/CPx）；Scale-out（数十至数百米，“快而窄”，SiPh 448G/lane，可插拔+部分 CPO）；Scale-across（500 m 至数公里，SiPh 集成、全频谱相干收发器，可插拔回归嵌入式）[p6]
  - 光互连目标（引自 Microsoft Paolo Costa, HotOptics 2026）：<10 ns 延迟、<1 pJ/bit、>10 Tbps/mm、<<10 FIT、10 m 覆盖 [p10]
  - p5 晶圆厂/市值表（TSMC、Samsung、Intel、GF、ST、Tower 等）OCR 数字混乱，看不清（未开图）
  - p8/p9 云厂商 Capex 与 Ethernet 收发器销售增速相关性图，数值看不清（未开图）
  - p12：CPO 时代对准/测试责任从模块厂移至 OSAT 先进封装线，测试从模块级变为晶圆级；“Modules don't go away”
- 提到的公司/客户/产品/标准：TSMC、Samsung、Intel、GlobalFoundries、ST、Tower；Microsoft（Paolo Costa）；Latitude Design Systems（Terence Chen）；MSA：OCI、CPx、XPO、400G、EBO、SDM4（p7）；LightCounting 另一讲 “Hedging Bets while conceding to width”（Roy Rubenstein）
- 与业界对比或记录声明（SOTA/首次/record）：硅光收发器份额首次 >50% [p4]
- 推荐配图页：p4（硅光/InP/GaAs/TFLN 收发器销售堆叠柱图与 >50% 标注）；p6（四类 AI 网络段对比表）；p10（“打破封装墙”与光互连目标）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第14–23页）
- 讲者/机构：Binbin Guan / OpenAI | 题目：AI [Cluster] Networks: Requirements for Reliable, High-Bandwidth-Density …（p14 标题 OCR 残缺，完整英文原题看不清）| 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO]；次 [3 Scale-out]
- 核心主张（p23 Takeaways）：
  1. 工作负载决定网络需求：通信模式决定带宽、延迟、覆盖与密度。
  2. 恢复能力是交付性能的一部分：评估故障频率、受影响容量、恢复服务时间。
  3. 以系统结果比较互连：评估请求延迟与每请求能耗。
- 关键数据：
  - 衡量指标：请求延迟（TTLT，time to last token）与每请求能耗（energy/token，tokens/joule，亦为 tokens/s/kW）；主张在同等用户体验下比较效率 [p16 OCR]
  - 推理三阶段（编码上下文/草稿模型/解码等）瓶颈不同，MoE 通信突发（bursty）[p17 OCR，未开图]
  - Jalapeño（OpenAI 自研芯片，Hot Chips 2026）：本地域 128 颗 Jalapeño 配 Broadcom TH6；全局域 2048 颗 Jalapeño，TH6 rail 0–7；“Half flattened” 两级 Clos；张量并行更高带宽、专家并行较低带宽、二者低延迟 [p19]
  - 需求-指标映射：请求延迟→Tb/s/mm、μs；能耗→pJ/bit；连续性→FIT、MTTR/小时 [p21]
  - Scale-up 互连四选项（铜/可插拔/NPO/CPO）的优缺点定性表，无数值 [p22]
- 提到的公司/客户/产品/标准：OpenAI Jalapeño；Broadcom TH6（Tomahawk 6）；OIF（2023, 2026）；Hot Chips 2026
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p22（铜/可插拔/NPO/CPO 强弱与约束对比表）；p19（Jalapeño 两级 Clos scale-up 拓扑）；p21（工作负载到网络指标映射）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第24–38页）
- 讲者/机构：Mark Filer（OCI Architect）/ Oracle | 题目：Photonic interconnects for modern AI superclusters（ECOC 2026 Workshop Su3-A）| 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [4 Scale-up/in CPO/NPO/XPO]、[2 Scale-across/ZR]
- 核心主张：
  1. 网络要为 TCO 求解：可靠性/可用性、能效、Capex（网络相对计算的花费逐年上升，“不可持续”）[p30]。
  2. 800G LPO 在大规模部署中表现不逊于 FRO；1.6T 上 LPO 难满足 SI 与互操作，LRO 是当前最佳低功耗方案 [p32, p33]。
  3. 224G/lane 已适合试用 NPO/CPO，“现在应开始试用 CPO”，可能替代部分可插拔；>224G CPO/NPO 或是唯一出路 [p37]。
- 关键数据：
  - OCI AI 集群规模 2020→2026：16,384 GPU（1x）→32,768（2x）→65,536（4x）→131,072（8x）[p27]
  - NIC 速率 2017 至 2026：25G 至 1600G，“256x 网络集群性能提升” [p28]
  - 800G LPO，约 35 万条链路：LPO-LPO n=156,591，FRO-FRO n=202,042；中位 pre-FEC BER 1.1E-11 vs 1.4E-11；p99 BER 5E-10 vs 3E-8；至少 1 次 down transition 的链路占比 LPO 3.244% vs FRO 5.681%（幻灯片图中数字如此；文字称 FRO 闪断次数为 LRO 的 1.75 倍，原文 FRO/LRO 混用）；提示：短/中/高损耗端口需优化调参，LPO 互操作数据有限 [p32]
  - 1.6T LRO：26 dB 通道，16 W（10 pJ/bit）；支持 DR4+（4 dB）及上层 FR4；多厂商 3 nm DSP 互操作已演示；2 nm 后功耗有望进一步降低 [p33]
  - 1.6T pre-FEC BER（FRO vs LRO，3 厂商）：Vendor1 6.28E-13 vs 4.73E-12；Vendor2 9.40E-13 vs 2.48E-12；Vendor3 9.56E-13 vs 9.56E-13；3 厂商均值 8.41E-13 vs 2.72E-12；FEC bin P50 均为 1，P95 LRO 2 / FRO 1 [p33]
  - CPO 观点（引 Meta, OCP 2025）：CPO 去除人工插拔（误操作为主要故障模式），但系统 FIT 预期高于同等可插拔；功耗最多省 50%（相对全重定时可插拔、200G/lane 代）；理论成本节省 30%；当前 CPO 方案专有、供应链受限、配置不灵活 [p34，OCR 未开图]
  - NPO 优势：多供应商生态、RMA 更容易、后绑定光 PMD（DR/FR 混用或 flyover 线缆）；提及 OpenCPX MSA 公告 [p35 OCR]
  - DCI：OCI 区域 DWDM 互连约 60 km 跨段，400ZR→800ZR→1600ZR；参与 1600ZR/1600ZR+/CMIS；已启动 1.6T 相干可插拔 MACsec 支持项目 [p36 OCR]
- 提到的公司/客户/产品/标准：Oracle OCI；Meta（引用）；OpenCPX MSA；400ZR/800ZR/1600ZR/1600ZR+、CMIS、MACsec；LPO/LRO/FRO；DR4+、FR4；3 nm/2 nm DSP
- 与业界对比或记录声明（SOTA/首次/record）：“OCI 已在 AI 基础设施中广泛部署 800G LPO”；LPO 链路 BER 尾部优于 FRO [p32]
- 推荐配图页：p32（LPO vs FRO 的 pre-FEC BER 分布与闪断对比，约 35 万链路）；p33（1.6T LRO vs FRO 分厂商 BER 柱图）；p37（可插拔/224G NPO-CPO/>224G 的三阶段结论）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第40–52页）
- 讲者/机构：Pantelis Aivaliotis（Director of Photonic Integration）/ Oriole Networks | 题目：A Pure Photonic Network for the AI Era | 类型：产业发布
- 方向归属（主/次）：主 [3 Scale-out …OCS]；次 [4 Scale-up/in]
- 核心主张：
  1. 计算比网络带宽在过去十年快约 100 倍，网络是计算的一部分（p41：Compute has grown 100x faster than network bandwidth over the last decade）。
  2. 方案 PRISM：无电交换的“无分层全连接网络”，核心为无源波长路由（光进光出），任意 xPU 一跳直达。
  3. 需同时具备超快交换与超快收发器重锁定，否则吞吐损失严重。
- 关键数据：
  - 交换时间与收发器重锁定对吞吐的影响：PRISM SiP 超快交换+超快重锁定 >90% 吞吐；自由空间交换（数十 ms）、SiP 热光交换（约 100 μs）、SiP 极快交换（<10 μs）、SiP 电光超快交换（<10 ns）配标准收发器，均 <1% 吞吐 [p47]
  - 三项对比（Oriole vs EPS）：推理延迟有界/可预测 vs EPS 可变（横轴 0.5 至 10s–100s μs，单位符号看不清）；训练算力利用 Active 99%（Oriole）vs 40%（EPS，Idle 60%）；能耗：EPS 中 Compute 80% + Network 20%，Oriole 中 Compute 48% + Network 5%，标注 2x 下降 [p48]
  - 应用层宣称：tokens/sec 与 tokens/sec/user 提升 4x、tokens/watt 提升 5x、ML 训练时间/能耗 10x 更优；all-to-all 完成时间快 2–3x；调度比 SoTA 快 1,000,000x；1 跳可扩展至 >1M 节点；尾延迟低 10–100x [p46 OCR]
  - 推理前沿图：总吞吐（百万 tok/s）对交互性（tok/s/user），Cerebras cs3 + Oriole PRISM 曲线位于 cs3 EPS、NVIDIA groq-lpu EPS、NVIDIA rubin EPS、AMD mi450 EPS 之外侧，例如约 8000 tok/s/user 处仍有非零吞吐，其他方案约 3500 tok/s/user 内归零（读图估计，曲线读数不精确）[p49]
  - 公司：80+ 员工；办公室 Palo Alto、Bangalore、Paignton & London [p51]
- 提到的公司/客户/产品/标准：Oriole XCCL 软件插件、Photonic NIC、XTR Transceiver、Passive Photonic Core；对比 Cerebras cs3、NVIDIA groq-lpu、NVIDIA rubin、AMD mi450；人才来源含 Huawei、Intel、Ericsson、Lumentum、Qualcomm、Semtech、arm 等
- 与业界对比或记录声明（SOTA/首次/record）：以上均为公司自述性能宣称，无第三方验证；“a 1000th of the latency” [p48]
- 推荐配图页：p47（交换时间+重锁定对吞吐的条形对比）；p48（延迟/利用率/能耗三联对比）；p49（吞吐-交互性帕累托前沿对比）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第53–67页）
- 讲者/机构：Daniel Kuchta / NVIDIA | 题目：The Path for Co-Packaged Optics in the AI Ecosystem | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO]；次 [3 Scale-out 224G/448G/光源/调制器]
- 核心主张：
  1. CPO（微环调制器、3D 堆叠硅光引擎、高功率高效率激光器、可拆卸光纤连接器）已在 Spectrum-X / Quantum-X 上量产。
  2. AI 工厂中光网络功耗占计算资源约 10%，CPO 可省大量收发器功耗，“可将这部分功率用于更多 GPU”。
  3. 下一代行业标准是 400 Gb/s（200 GBaud PAM4）；此后靠偏振/光双向、多波长（CWDM/LWDM）、DWDM、coherent lite 扩展。
- 关键数据：
  - Spectrum-X Ethernet Photonics：相对可插拔 4x 更少激光器、5x 更低功耗、10x 更高 MTBI；CPO 芯片采用微环调制器；3D 堆叠硅光引擎，TSMC COUPE 工艺 [p59]
  - 传统云数据中心 100K 服务器对应收发器功耗 2.3 MW；AI 工厂 100K 服务器对应 40 MW；CPO 约 4 pJ/b，节省约 72% 收发器功耗 [p60]
  - 微环调制器发射机：212.5 Gbps 眼图；16 通道以 212 Gbps 在 OFC 2026 展会连续运行 3 天，总 BER < 1E-14 [p64]
  - CPO 未来扩展：400 Gb/s（200 GBaud PAM4）为下一行业标准；偏振与光双向再 2x；CWDM/LWDM 2x400G、4x400G；DWDM；需平衡每纤带宽、radix 与总吞吐 [p66]
  - 未来 AI 工厂：网络占总功耗 6–8%，CPO 将降 5x；网络中断可累计每天 \$3M 收入损失，CPO 将“近乎消除” [p67]
  - 套接 vs 焊接 CPO 的优缺点定性讨论；焊接利于信号完整性与最低成本，提及 IBM Power775（约 2010）为首个商用使用 CPO 的系统（OCR，未开图）[p65]
  - NVLink 第六代 scale-up、Spectrum-X 102.4T 交换系统与 1.6T SuperNIC（OCR）[p57–58]
- 提到的公司/客户/产品/标准：NVIDIA Spectrum-X、Quantum-X InfiniBand Photonics、NVLink（第6代）、NVL72、Vera、BlueField-4、SuperNIC；TSMC COUPE；IBM Power775；OFC 2026
- 与业界对比或记录声明（SOTA/首次/record）：“IBM Power775 是首个商用 CPO 系统”（讲者引用）[p65]；16 通道 212G 连续 3 天 BER<1E-14 [p64]
- 推荐配图页：p60（传统 DC vs AI 工厂收发器功耗与 CPO 节省 72%）；p59（Spectrum-X 光子学 4x/5x/10x）；p64（微环调制器 212.5G 眼图与 3 天验证）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第71–86页）
- 讲者/机构：Marvell（Senior Vice President, Data Center Architecture，姓名看不清）| 题目：Meeting Diverse AI Connectivity Needs: Architectural Choices for Next-Generation Pluggable Transceivers | 类型：产业发布（Workshop 邀请报告）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区]、[4 Scale-up/in]
- 核心主张：
  1. 200G/L 到 400G/L 改变可插拔设计点：在约 212.5+ GBd 时电/光边界必须联合设计，“更快的可插拔不只是更快的 DSP，而是新的链路划分”。
  2. 铜与光并存是 AI 架构所需；可插拔 DSP 仍是 scale-out 的主力，NPO 可降低故障爆炸半径、现场可更换。
  3. 可插拔演进为“连接引擎”；AI 连接将汇聚为按延迟、功耗、覆盖、密度、互操作优化的可插拔架构组合；TRO | NPO → PAM4 DSP → Coherent-Lite → 全相干是一个连续谱。
- 关键数据：
  - 分层：DCI | Scale Across（>10 km）C-band 相干 1.6T ZR/ZR+；Scale Across 2 km–10 km+ O-band Coherent-Lite 1.6T | 3.2T；Scale out 100 m–2 km 200G/L→400G/L PAM4；Scale up 10 m–100 m 200G/lane→400G/L PAM4，AOC/光收发器；Scale In 1–10 m 慢而宽光学（μEmitter、μLED、μVCSEL）[p74]
  - 传统划分 C2M/LR 电通道（32 dB | 40 dB）→ 400G/L 下 CPC 通道需被良好管理；第一阶因素：主机电通道长度、封装/PCB 损耗与反射、ADC/DSP 均衡深度、FEC 延迟与增益、模块功耗与热裕度 [p78]
  - 三种架构：Scale-up 铜 PAM6 CPC/线缆背板；Scale-out CPC→FRO/TRO 光，PAM4，35 dB；NPO/CPO，PAM4，20 dB，scale-up/out [p80]
  - 3.2T PAM 与 Coherent-lite：400G C2M 通道；448G 表：PAM DSP FRO 为 PAM6 或 PAM4 C2M + PAM4 光；TRO 为 PAM4 C2M + PAM4 光；Coherent-Lite DSP 为 PAM6 或 PAM4 C2M + Coh-Lite 光；光调制格式 PAM4 | QAM16 [p81]
  - 模块复杂度/主机 SerDes 要求/功耗对比：NPO（1点/4点/1灯）、TRO（2/2/2）、全重定时 FRO（3/1/3）、Coherent-Lite（4/1/4）（点数为幻灯片定性符号，非数值）[p85]
  - 场景：AI 基础设施从单服务器到多数据中心；Campus/跨楼区域最高 1,000 km+，数据中心内最高 500 m+，<100 m 机架内 [p72–73 OCR]
- 提到的公司/客户/产品/标准：Marvell；OSFP、CPC、CPO/NPO、FRO/TRO/LPO、Coherent-Lite、ZR/ZR+；PAM4/PAM6
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p74（AI 网络各层与对应光收发器路线）；p78（200G/L→400G/L 链路划分变化与第一阶因素）；p85（NPO/TRO/FRO/Coherent-Lite 复杂度-功耗对比）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第87–97页）
- 讲者/机构：Kim Roberts（VP, WaveLogic Science）/ Ciena | 题目：Coherent Technology for Data-center Applications | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区]；次 [4 Scale-up/in CPO/NPO/XPO]、[1 相干/…oDSP]
- 核心主张：
  1. 相干（Coherent-Lite）在短距离也具经济性：低热（精心的 DSP 与模拟设计，2 nm CMOS）、低成本（DFB、光子集成）、高密度、高产量、零错误（<1E-24）[p94]。
  2. 零丢包重传：可取消大容量 ARQ 存储和“延迟三倍”，改善 AI 训练 [p93]。
  3. 液冷 400ZR OSFP 与 12.8T Coherent-Lite XPO 展示（p89–92, p95）。
- 关键数据：
  - 零重传：每 3.2 Tb/s、20 km 需要 1.3 Gb 的 ARQ 存储；10T 参数数据集在 BER=1E-12 下丢 160 个包；采用 Compressed FEC 时 BER < 1E-24 [p93]
  - 2 x 1.6T Coherent-Lite OSFP 展示，BER < 1E-24 [p94]
  - 12.8T Coherent-Lite XPO：3.2T Coherent-Lite ASIC、双 1.6T ICR、双 1.6T MZM/驱动、双 DFB O-band 激光器；功耗 <240 W（液冷 XPO 可承受 400 W）；BER < 1E-24 [p95]
  - 冷却演进：自然对流、强制风冷、液冷；液冷 400ZR OSFP 运行流量照片（无数值）[p89–92]
- 提到的公司/客户/产品/标准：Ciena WaveLogic；400ZR OSFP；XPO；Coherent-Lite OSFP；Compressed FEC；DFB；MZM
- 与业界对比或记录声明（SOTA/首次/record）：无明确声明；“Zero Errors”类主张为讲者自述 [p94, p95]
- 推荐配图页：p95（12.8T Coherent-Lite XPO 结构与功耗）；p93（零重传论证及数值）；p94（2 x 1.6T Coherent-Lite OSFP 与低热/低成本论点）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第99–107页）
- 讲者/机构：Tom Williams / Acacia（Cisco 旗下）| 题目：CPO, LPO, T/LRO, XPO, EIEIO…. A vendor perspective on architectural evolution | 类型：产业发布（Workshop 邀请报告）
- 方向归属（主/次）：主 [2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区]；次 [4 Scale-up/in CPO/NPO/XPO]、[3 Scale-out]
- 核心主张：
  1. 成功指标是 GPU 利用率最大化；性能可转化为利润与更稳健链路，质量关注度显著上升。
  2. 相干光正在向更短距离推进：IMDD 的 CD 容限随波特率平方下降，200G/lane 的 IMDD 极限约 10 km，400G/lane 时超过 2 km 需相干；1600G/lane 相干可支撑 >2 km 校园 DCI。
  3. 未来数据中心光学需要多次技术转变，所有新技术须证明规模、性能与质量。
- 关键数据：
  - Scale Across 驱动相干需求：Meta 网络流量图（User、DC-DC 同步、DC-DC 千兆瓦级集群；2017 至 2026 预测）；Cignal AI 曲线称 800ZR+ 是历史上增长最快的相干技术；Acacia 已发货 >75,000 个 800ZR+ 模块 [p101]
  - IEEE 802.3：800GBASE-ER1 与 800GBASE-ER1-20 支持 20 km 与 40 km；相干由 0.5 km–1000 km 各场景向短距移动，过渡区在校园/Edge 附近 [p103]
  - 架构分类：FRO、LPO、NPO、XPO、CPO、OCI（光计算互连：Gen1 200G/方向，Gen2 400G/方向 BiDi），引 A. Ghiasi, IEEE 802.3 400GPL Study Group, Sept 2026 [p104]
  - 时间线：0–2 年 200G/lane、多数 OSFP、硅光、CPO 试点；2–5 年 400G/lane、NPO/CPO 与可插拔、scale-up 用光、Coherent-lite 校园；5–10 年 800G/lane、多数 NPO/CPO、先进材料、数据中心内相干 [p107]
  - 未来 Scale-across 架构：更高波特率使每光带波长数减少；C+L 广泛使用，更多光带被考虑；多轨放大、全频带转发器、媒体转换器；多芯与空芯光纤；将与可插拔并存 [p102 OCR]
  - 液冷：XPO 是首个针对液冷优化的外形尺寸定义 [p106 OCR]
- 提到的公司/客户/产品/标准：Acacia；Meta；Cignal AI；LightCounting（Capex 图）；IEEE 802.3 ER1/ER1-20、400GPL Study Group；800ZR+；XPO
- 与业界对比或记录声明（SOTA/首次/record）：“Acacia 是领先供应商，>75,000 个 800ZR+ 模块已发货”；“800ZR+ 是历史上增长最快的相干技术”（引 Cignal AI）[p101]
- 推荐配图页：p103（IMDD 到相干随速率-距离的过渡区图与 CD 论点）；p107（0–2/2–5/5–10 年数据中心光学路线）；p104（FRO 至 OCI 架构谱）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第108–127页）
- 讲者/机构：Bilal Syed, Han Sun / Nokia | 题目：Evolution of Coherent DSP to Meet the Evolving Needs of the AI Supercycle | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件]；次 [2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区]
- 核心主张：
  1. 相干 DSP 已是 AI 工厂部件，并正进入园区；800ZR+ 是 scale-across 的 SKU，Coherent-lite 是 >2 km 园区的切分。
  2. 选择 DSP 由覆盖距离、功耗、延迟与冷却决定，“不是峰值波特率”；应做“套件”而非一颗最快的英雄芯片。
  3. 1.6T 单相干通道是可复用构件；同族包含 1600ZR、ZR+、CL。
- 关键数据：
  - 每 AI 园区 4–12 栋楼；1.6T 下园区间隙 2–40 km；光纤时延 5 μs/km；百万级 XPU 集群；约 190 GW 超大规模容量已宣布 [p111]
  - 市场信号（非 Nokia 预测）：2026 年预计 >200k 800ZR 级单元；800G ZR 级 2025–2029 CAGR 145%；到 2030 年 800G+1600G 占相干收入 60%；IP over DWDM 约 20 亿美元增至 2029 年约 50 亿美元 [p113]
  - DSP 代际：400ZR/ZR+ 400 Gb/s ~60 GBd DP-16QAM CFEC 7 nm 量产；800ZR/ZR+ 800 Gb/s 118–135 GBd DP-16QAM+PCS OFEC 3 nm 大规模爬坡；1600ZR 1.6 Tb/s ~236 GBd DP-16QAM 单载波 OFEC 3/2 nm，IA ~Q2 2026；1600ZR+ 1.6 Tb/s 252 GBd（2 x ~126）PCS-16QAM 2 FDM OFEC 3/2 nm，IA ~Q3 2026；1600CL 1.6 Tb/s ~226–~247 GBd（待定）低复杂度 BCH 类 FEC，延迟 50–75 ns，园区 2–40 km [p120]
  - 园区 FEC 表：800G 10 km BCH(126,110) 247.3 GBd，延迟 49–55 ns，RSNR 13.7 dB，模块功耗 +1.5–3%；Compressed FEC 239.1 GBd，70 ns，13.8 dB，0%（基准）；Braided code 226.7 GBd，70–72 ns，14.3 dB，+1.5–3%；“不要在 10 km AI 链路上用 OFEC” [p121]
  - 按覆盖选引擎：IM-DD PAM4 数米至约 2 km；CL 2 km/OCS：2 km，4–8 dB，O-band；CL 10 km：约 6.3 dB，BCH 类 FEC 约 50 ns；CL 园区 WDM：20 km，12–14 dB，8 通道 O-band；ZR/ZR+ 80–1000+ km；嵌入式面向核心/海缆 [p123]
  - 三约束：ZR 级路由器笼内 28–40 W；园区 FEC 50–75 ns；2 km 处 OCS 损耗约 8 dB；风冷与液冷在 1.6T 并存；scale-across 光纤为毫秒级，FEC 纳秒无所谓 [p126]
  - 1600ZR 约 236 GBd 单光载波、约 300 GHz 频隙、80–120 km DCI；1600ZR+ 252 GBd 共 2 x ~126 GBd，到约 1000 km；复用 800G 模拟 [p122 OCR]
  - ZR-plus：约 80–120 km 放大；DP-16QAM 单载波；800G 可达 1700+ km 级 [p115 OCR]
- 提到的公司/客户/产品/标准：Nokia；OIF ZR、OpenZR+；400ZR/800ZR/1600ZR/1600ZR+/1600CL；CMIS；OFEC、CFEC、BCH、braided code；引用 Zhu et al. ECOC 2025、Pincemin & Renais OFC 2024、Sosio et al. ISSCC 2026、Berikaa et al. JLT 2024 等
- 与业界对比或记录声明（SOTA/首次/record）：无（均为路线图/市场信号）
- 推荐配图页：p120（400ZR 至 1600CL 的 DSP 代际总表）；p121（园区 FEC 三选项延迟/RSNR/功耗）；p123（按覆盖选择引擎的总表）

### 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描.pdf（第129–147页）
- 讲者/机构：Yuki Yoshida, Paikun Zhu, Ken-ichi Kitayama, Bahram Jalali, Satoshi Shinada / NICT（日本）、Hamamatsu Photonics 中央研究所、UCLA | 题目：Can Photonic Signal Processing Simplify DSP?: Breaking the Fiber Dispersion Barrier in IM/DD | 类型：邀请报告（Workshop，Session 2 Signal Processing）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [1 相干/…oDSP]、[2 Scale-across/…CL/跨楼园区]
- 核心主张（p147 Key Takeaways）：
  1. 对 >1.6T（200 Gbaud/lane）IM/DD，仅数 ps/nm 的 CD 就至关重要；CD 补偿上 IM/DD DSP 与相干 DSP 相比“根本不具竞争力”。
  2. 若 IM/DD 无信道零点（null）突破，Coherent-lite 将主导 2 km 以上。
  3. 应严肃研究 IM/DD 的光域均衡；最小光学（1 抽头延迟线、成对/成组使用通道）可打破色散壁垒。
- 关键数据：
  - 拓扑图（400 Gb/s/lane 时代）：3.2T IMDD PAM4/PAM6，400G/Lane（200 GBd），O-band（新光纤？）；1.6T IMDD PAM4 200G/lane（100 GBd）802.3dj；Coherent Lite 16QAM ~260 GBd O/C-band；Digital Coherent 16QAM ~130–260 GBd C-band（OIF 1.6T ZR）；覆盖 DR <500 m、FR <2 km、LR <10 km、ER <40 km、ZR <120 km、ZR+ >120 km；园区/短距 DCI 约 20 km [p130]
  - O-band 色散：基于 ITU-T G.652.D，零色散波长均值 1312 nm（标准差 2 nm），斜率均值 0.086 ps/(nm²·km)（标准差 0.0015），段长 2.5 km；1331 nm 处 2/5/10/20 km 总色散分布（20 km 约 30–35 ps/nm 量级，读图估计）；色散代价 = D x L x BW²，例：16 ps/nm x (50 GHz)² = 2 ps/nm x (200 GHz)² [p131]
  - 224 Gbaud 可用带宽（准则：EQ 抽头 <20 且 SNR 代价 <4 dB，最坏色散、理论最佳 EQ）：2 km 后 IM/DD FFE 仅约 45%，IM/DD FFE+1 抽头 DFE 约 70% [p134]
  - 可用 O-band 频谱：2 km 后 <45%，20 km 后 <5%；Broadcom J. Johnson（ITU-T/IEEE, Jul. 2026）报告更严重结果，2 km 处 <10%；相干 FFE 在 20 km 仍约 75 nm 量级（读图）[p141]
  - 1 抽头光延迟线去信道零点：等效信道响应 G′(L,f) 公式；先前工作（P. Zhu et al., OFC’24）：C 波段 100 Gbaud 超 80/100 km 的“创纪录低 DSP 复杂度”，约 100 km@224 Gbaud，甚至在 O-band 边缘；全 C 波段 WDM，20 km，192.8–193.4 THz，BER 在 11% HD-FEC 与 KP4+Hamming 附近（P. Zhu et al., JOCN 2024）；BiDi 1 抽头 ODL（本届 ECOC，We3-E2，P. Zhu et al.）[p144]
  - 成对传输（空时编码跨多通道，例如 OOK→PAM4）：可完全消除功率衰落且与距离无关；适用条件：衰落缓解增益 >> MUX 与 O-E 编码的 SNR 代价；光纤束 BER 曲线（OFC 2025，0–40 km，pairwise 在 40 km 达约 HD-FEC 极限，优于常规 OOK/PAM4）；MCF 上距离-每通道净比特率图（ECOC 2025，标注 3 与 6 Tb/s·km 曲线，最长约 85 km，读图估计）；WDM 上（OFC 2026）[p146]
- 提到的公司/客户/产品/标准：NICT、Hamamatsu、UCLA；Broadcom（J. Johnson）；IEEE 802.3df/dj、OIF 400ZR/800ZR/1.6T ZR；ITU-T G.652.D；O-band、MZM（单驱动）、MRM 负啁啾（p143 OCR）
- 与业界对比或记录声明（SOTA/首次/record）：“Record low-DSP complexity for C-band 100 Gbaud over 80/100 km”（作者自己 OFC’24 工作）[p144]
- 推荐配图页：p141（相干 vs IM/DD 可用带宽随距离曲线）；p130（400G/lane 时代 Coherent-lite 与 IM/DD 拓扑图）；p146（成对传输原理与光纤束/MCF/WDM 结果）

## 本批小结
1. **400G/lane 使模块从“器件”变成“系统架构的一部分”**：Marvell 认为约 212.5+ GBd 时电/光边界必须联合设计，主机电通道、封装损耗、ADC/DSP 均衡深度、FEC 延迟与模块热裕度成为第一阶变量（Marvell p78、p79、p80）；NVIDIA 同样把 400 Gb/s（200 GBaud PAM4）称为下一行业标准，之后靠偏振/BiDi、CWDM/LWDM、coherent lite 扩展（NVIDIA p66）。
2. **Coherent-lite 在 >2 km 园区/跨楼段几乎成为共识，但 FEC/功耗需要单独定义**：Ciena（2x1.6T OSFP、12.8T XPO，BER<1E-24，p94–95）、Nokia（1600CL，50–75 ns BCH 类 FEC，“不要在 10 km AI 链路用 OFEC”，p120–123）、Acacia（400G/lane 超 2 km 需相干，p103）、Marvell（O-band Coherent-Lite 1.6T/3.2T 用于 2–10 km+，p74）四家口径高度一致。NICT 从物理层给出理由：CD 引起信道零点使 IM/DD 在 2 km 后仅约 45%（O-band 可用带宽）、20 km 后 <5%（NICT p134、p141），但同时提出光延迟线/成对传输作为让 IM/DD 延后被取代的“最小光学”路径（NICT p144–147）。
3. **LPO/LRO 的实测证据来自运营商侧**：Oracle 用约 35 万条 800G 链路称 LPO 中位/尾部 BER 不劣于 FRO，闪断比例更低（p32），并称 1.6T 上 LPO 难以满足 SI 与互操作，LRO 为 10 pJ/bit、26 dB 通道方案（p33）；OpenAI 则在 scale-up 表中把 LPO/LRO 主机负担与故障隔离列为可插拔的约束（OpenAI p22）。两者立场并不完全一致，可作为后续讨论点。
4. **CPO/NPO 的时点判断分化**：NVIDIA 已量产 Spectrum-X/Quantum-X CPO 并宣称 4x 更少激光器、5x 更低功耗、10x MTBI，约 4 pJ/b，节省约 72% 收发器功耗（NVIDIA p59、p60）；Oracle 说 224G“已适合试用 CPO/NPO”，但也强调 CPO 系统 FIT、专有性、供应链是问题，NPO 更利于多供应商与 RMA（Oracle p34、p35、p37）；Marvell 强调 NPO 的可现场更换与更小故障爆炸半径（Marvell p83）；Acacia 时间线为 2–5 年 NPO/CPO 与可插拔并存、5–10 年多数 NPO/CPO（Acacia p107）；LightCounting 认为 CPO 会使光装配/测试责任转移到 OSAT，“模块不会消失”（LightCounting p12）。
5. **评价口径从“成本/比特”转向系统结果**：OpenAI 主张以请求延迟与每请求能耗、恢复时间来比较互连（OpenAI p16、p23）；Oracle 以 TCO 三要素（可靠性、能效、Capex）表述（Oracle p30）；Acacia 称“优化 GPU 利用率是关键指标”（Acacia p100）；NVIDIA 用“网络中断每天可累计 \$3M 收入损失”（NVIDIA p67）；Oriole 以吞吐-交互性前沿与训练利用率为卖点（Oriole p48、p49，均为自述）。
6. **Scale-across 需求的量化信号**：Nokia 引用 2026 年 >200k 800ZR 级单元、2025–2029 800G ZR 级 CAGR 145%（Nokia p113）；Acacia 称已发货 >75,000 个 800ZR+（Acacia p101）；Oracle 已在约 60 km DWDM 跨段用 DCI 优化相干可插拔并参与 1600ZR/ZR+（Oracle p36）；Nokia 1600ZR/1600ZR+ 均以 3/2 nm 与 IA ~Q2/Q3 2026 为节点（Nokia p120）。
7. **提示**：Oriole 的 >90% 吞吐、4x tokens/sec 等均为公司自述；Nokia、LightCounting 的市场数字被讲者标明为“公开市场信号/非本公司预测”，引用时应注明。LightCounting p5、p8、p9 及 OpenAI p15、p17、p18 未开图，图表数值看不清，未记录。
