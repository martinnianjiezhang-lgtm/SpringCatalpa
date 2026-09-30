---
title: "B19 · DAY1 · PV-R-Su3-Su4-窄快还是宽慢"
tags:
  - ECOC2026
  - DAY1
---

## 说明
本批为 ECOC 2026 Workshop（9月20日下午，Su3/Su4，"Can fast narrow channels keep rising without limit or will slow and wide become the winner?"）的9场讲稿。组织者：Eric Bernier (Huawei)、Peter Winzer (Ciena)、Tony Chan Carusone (Qualcomm)、Marianna Pantouvaki (Microsoft)（LightCounting p1）。每人8分钟讲 + 4分钟问答（p3）。Lumentum（Su4-I-03）为主分析师已做篇目，已跳过。页码 pN 均为该PDF的页码。

### 0920-pm-Su3-I-02-LightCounting-AI光模块市场数据.pdf
- 讲者/机构：Roy Rubenstein, Consultant, LightCounting | 题目：Hedging bets while conceding to width（副标题：Can fast and narrow channels keep rising without limit or will slow and wide become the winner?） | 类型：Workshop（市场分析/开场综述）
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS；次 4 Scale-up/in CPO/NPO/XPO
- 核心主张：
  1. 快窄（F&N）会继续（可插拔、相干、调制器发展）；光越靠近芯片越倾向宽慢（W&S），主要在 scale-up 和 GPU-memory，但“变宽”问题遍及所有域 [p13]
  2. 行业无法现在给出答案，正在通过 MSA 囤积可互操作的选项（“stockpiling interoperable options”） [p8, p13]
  3. 一旦跨过“巨大鸿沟”（从可插拔世界到芯片-光紧耦合的计算世界），F&N 与 S&W 将被抽象掉，生态将大不相同 [p14]
- 关键数据：
  - ECOC 2006 Finisar：1G 到 10G、单通道、风冷；ECOC 2026 XPO：1.6T 到 12.8T、64×200G 通道、液冷 [p6]
  - IMDD 路线图：可用 1.6T OSFP（8×200G 或 4×400G）；开发中 3.2T（16×200G / 8×400G）；将来 12.8T（64×200G、32×400G、16×800G、8×1.6T 等组合） [p7]
  - 相干路线图：1.6T pre-OIF，200 GBd，2波长/4波长，已可用；1600 CL/ZR/ZR+，240–270 GBd（2027/28）开发中；2.4T，280 GBd（2028）开发中；3.2T，400 GBd（2029?）；3.2T ZR，450–500 GBd（early 2030s） [p7]
  - 2026年共6个MSA：XPO（64×200G电接口，12.8T可插拔）、CPX（铜或光输出，近封装且可维护）、400G Optics MSA（400G光通道，500 m，快窄）、OCI（慢宽，如200G→4×50G，WDM+BiDi，与CPO/NPO相关）、SDM4 MCF（空分复用）、Expanded Beam Optics（光纤连接自动化/可制造性） [p9, p12]
  - AI算力需求增长速度（月）远快于电/光速率翻倍（年） [p8]
- 提到的公司/客户/产品/标准：Finisar、XPO、CPX、OCI、SDM4 MCF、Expanded Beam Optics MSA；xAI Colossus 2（p4 看图核实：>500K GPU、>500 MW、约 2026；此前 Colossus 100k H100 → 150k H100+50k H200+30k GB200 @250 MW）；OIF（相干 pre-OIF）
- 与业界对比或记录声明（SOTA/首次/record）：无 SOTA 声明；观点性结论“The architecture is a bet, widening is not” [p12]
- 推荐配图页：p7（IMDD 与相干的速率/通道数路线图）；p12（六大MSA在平台/架构/制造三层的分层对冲图）

### 0920-pm-Su3-I-03-Arista-交换机侧的选择.pdf
- 讲者/机构：Sunil Priyadarshi, Senior Director, AI & Cloud Network Architect / Arista | 题目：Fast-and-Narrow and Slow-and-Wide: The Optimum Depends on System Constraints | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS；次 4 Scale-up/in CPO/NPO/XPO
- 核心主张：
  1. 最优架构取决于整个系统：ASIC接口、电距离、封装、功耗与系统需求 [p9]
  2. 400G/lane 时电通道成为约束，扩展的重点从“均衡长通道”转向“缩短电路径”，即 XPO/NPO [p3]
  3. 原生OCI功耗/时延收益最大，带 reverse gearbox 的OCI兼容性更好但削弱节能，快窄PAM4 I/O数最少 [p8, p9]
- 关键数据：
  - 交换机带宽演进：51.2T=512 lanes@100G；102.4T=512 lanes@200G；204.8T=1,024 lanes@200G；409.6T=1,024 lanes@400G [p2]
  - 448 Gb/s 电接口：PAM4 224 GBd 需 ~112 GHz；PAM6 ~173 GBd 需 ~90 GHz；PAM8 ~149 GBd 需 ~75 GHz [p3]
  - 插入损耗对频率曲线（示意，讲者注明实际取决于实现）：超低损耗PCB ~2.1 dB/in @112 GHz；Twin-ax ~0.3–0.5 dB/in @112 GHz [p3]
  - 400G电通道用PAM6/PAM8、光通道保持PAM4时需 DSP/transcoder/gearbox 做格式转换，增加复杂度、功耗和时延 [p4]
  - OCI（NRZ光I/O）优点：强原始BER裕量、低时延、极低功耗潜力；reverse gearbox 使系统功耗可能逼近线性光学实现 [p5, p6]
  - TSMC-COUPE 引用数据（H. Hsia et al., 2021 IEEE ECTC）：与 uBump 方案相比，同速率下功耗低 40%，同功耗下速率提升 170% [p7]
  - 对比表：Native OCI 光链路裕量强、电距离很短、DSP最少、节能最大、通道/封装I/O最高；Gearbox OCI 需PAM4 DSP+reverse gearbox、节能被削弱；快窄PAM4 通道/封装I/O最低、高速率下裕量更苛刻 [p8]
- 提到的公司/客户/产品/标准：Arista、OCI MSA、XPO、NPO、TSMC-COUPE、LPO
- 与业界对比或记录声明（SOTA/首次/record）：无自身record声明；COUPE数据为引用自2021 ECTC [p7]
- 推荐配图页：p3（448G电接口调制格式与带宽表 + 插损曲线）；p8（Native OCI / Gearbox OCI / 快窄PAM4 三方系统权衡表）

### 0920-pm-Su3-I-04-Qualcomm-芯片侧的选择.pdf
- 讲者/机构：Letizia Giuliano, VP Product Management / Qualcomm（Dragonfly） | 题目：Beyond the SerDes: From Fast & Narrow to Reliable Connectivity at Scale | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS
- 核心主张：
  1. 差异点在SerDes：PAM4 DSP放在光引擎之外，还是NRZ集成在光引擎上 [p2]
  2. 随着单通道速率上升，互连选择被“迫”改变：Nyquist频率上升、通道与封装损耗增长、可插拔与NPO会到极限、DSP功耗增速超过收益 [p3]
  3. 铜有~5 m的功耗与距离墙；P-CPO 处于光学前沿的最低功耗与较低时延位置 [p4]
- 关键数据：
  - 四条扩展路径：可插拔+CPO（提高模块速率）、NPO（光引擎移到板边，200G→400G/lane，更难的EIC/PIC与DSP指标）、L-CPO 铜共封装、P-CPO 光I/O（更低速率、更多光通道） [p3]
  - L-CPO：224G下封装损耗约占40 dB链路预算的30–50%，448G下可能变得“effectively prohibitive”；合作方 Samtec（Si-Fly HD，从224G起，面向448G）、Open CPX MSA [p5]
  - P-CPO with Lightmatter Passage：OFC 2026 demo（Passage EVK100）：1.6 Tbps/fiber，200 m SM fiber，106G PAM4 × 16λ DWDM，200 GHz间隔；Qualcomm 112G PAM4 光SerDes chiplet集成 [p6]
  - P-CPO 光 D2D / Extended UCIe：与Lumentum（VCSEL+PD CPO光引擎，10 Tbps，~1 T/mm）、Corning合作；Qualcomm D2D UCIe光直驱PHY 32G，1.8 T/mm；路径为 3D CPO 下 >4 T/mm、<2.5 pJ/bit；D2D需求超过80 Tbps总带宽；ECOC 2026现场demo [p7]
  - 图4（示意值，讲者注明）：Passive DAC/ACC/AEC在~5 m内；LPO约300 m、约13 pJ/bit量级；Retimed pluggable约500 m、约20 pJ/bit量级（图上读数，粗略） [p4]
- 提到的公司/客户/产品/标准：Qualcomm Dragonfly、Samtec Si-Fly HD、Lightmatter Passage EVK100/Guide 1、Lumentum、Corning、OCI MSA、Open CPX MSA、XPO MSA、OIF、IEEE 400G/lane标准启动、OCP参考架构（p8）
- 与业界对比或记录声明（SOTA/首次/record）：OFC 2026 demo 1.6 Tbps/fiber [p6]；ECOC 2026 live demo 光D2D [p7]；未使用“record”字样
- 推荐配图页：p4（铜墙与光学前沿的功耗-距离图，含 LPO/L-CPO/P-CPO 定位）；p7（Lumentum VCSEL + Corning + Qualcomm UCIe光D2D 实物demo）

### 0920-pm-Su3-I-05-Ciena-系统侧的选择.pdf
- 讲者/机构：Bilal Riaz（Sr. Director, Product Line Management）/ Ciena | 题目：Beyond Channel Speed: Rethinking Interconnect Scaling（p1 看图核实） | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区
- 核心主张（原文结论页 p10）：
  1. 慢宽听起来更安全，但宽度带来封装面积、连接器和复杂度，难以回退；动量仍在通道速率，推到448G及以上，快窄仍是规模化最短路径 [p10]
  2. 铜已无余量：200G下无源铜约1.5 m，距离成为光学问题；功耗设上限 [p10]
  3. 时机决定：CPO 在scale-out约2026、scale-up 2027/28，机架从72 XPU到576+ XPU [p10]
- 关键数据：
  - 三个域：Scale Up（机架内，数米）、Scale Out（数据中心）、Scale Across（跨区域，长距）；行业方案多样 [p2, p3]
  - XPU海岸线瓶颈下各方案功耗：Fully Retimed(DSP) 30 W（18.5 pJ/bit）；Half Retimed(LRO) 20 W（12.5 pJ/bit）；Linear(LPO) 10 W（6.5 pJ/bit）；NPO 8 W（5 pJ/bit）；CPO 5 W（3 pJ/bit）；448 Gbps下PCB到前面板连接“breaks down” [p5]
  - 机内互连选项覆盖：铜 DAC 1.5 m / ACC 3.5 m / AEC 5.5 m（现可用）；Micro-LED ~10 m（进行中）；MMF/VCSEL 最长50 m、最高100G（现可用）；Open CPX CPO/NPO 500 m+（sampling）；OCI CPO/NPO 最长500 m（Phase1: SerDes ASIC+reverse gearbox 进行中；Phase2: 带UCIe/OCI的ASIC 更晚；Phase3: 光中介层“strategic end-game”）；SMF/DR/FR 最长2 km及以上（现可用） [p7]
  - 互连演进：当前 ASIC到前面板 retimed光学，100T ASIC额外约1 kW用于retimed光学；Emerging 单厂商CPO（在生产，供应链“some risk”）；Optimized 2027 ramp，Open CPX MSA，6.4T模块标准化，多厂商供应 [p9]
  - 关键问题页：OCI若胜出，VCSEL与uLED能否建立生态或规模竞争（“Slow forces a single-technology bet”） [p4]
- 提到的公司/客户/产品/标准：Ciena、Open CPX MSA、OCI MSA、UCIe、ZR/ZR+、Coherent-Lite、hyper-rail/multi-rail、OCS
- 与业界对比或记录声明（SOTA/首次/record）：无；“448G demos through OFC 2025”为讲者结论页文字（p10 看图核实；同页：200G 无源铜缆约 1.5 m、全重定时可插拔约 30 W/18.5 pJ/bit、CPO scale-out 约 2026、scale-up 2027/28，机架 72 → 576+ XPU） [p10]
- 推荐配图页：p5（DSP/LRO/LPO/NPO/CPO 功耗梯度示意，含pJ/bit）；p9（互连三代演进与供应链红绿灯评估）

### 0920-pm-Su3-I-07-Marvell-DSP与波特率路线.pdf
- 讲者/机构：Lenin Patra（Senior Vice President – Data Center Architecture）/ Marvell | 题目：The Optical I/O Continuum: Architecting Connectivity from Scale-In to Scale-Across（p1 看图核实） | 类型：Workshop（邀请报告/产业）
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS；次 2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区
- 核心主张（结论页 p14）：
  1. AI每年驱动光学更新换代
  2. 所有网络层都需要光I/O
  3. PAM与Coherent-Lite DSP将在scale-out与scale-up共存；新兴光学（uEmitter、flat optics）使scale-in与scale-up成为可能
- 关键数据：
  - 各域链路需求：1–3 m 时延+密度；1–100 m 时延+功耗+密度；100 m–2 km 功耗+radix；2–10+ km 覆盖+功耗；80–1000+ km 容量+覆盖；架构依次为片上光/光chiplet、NPO|XPO、DSP-based PAM4或Coherent-lite、ZR/ZR+相干 [p2]
  - Scale-in 未来一代：SiPho I/O chiplet（激光器）、uVCSEL I/O chiplet 与 uLED I/O chiplet（micro-emitter）、Copper I/O chiplet（电子）；当前为 Passive over Substrate/CoWoS [p4]
  - Scale-up 拓扑：Switch，72 XPU/机架 铜；2D/3D Torus，64 XPU/机架 铜；OCS in PoD，9K XPU/super POD 光（引用 Google 数据中心：144 racks，13,824 optical fibers，48 OCS） [p6]
  - Scale-out：可插拔FRO用于<30 m多机架到<2 km，DCI 2–2,000 km+ [p9]；2027 交换机1.6T FRO|TRO，NIC 800G→1.6T [p10]
  - 3.2T scale-out：C2M 400G；448G下FRO电PAM6|PAM4、光PAM4；TRO 电PAM4、光PAM4；Coherent-Lite DSP 电PAM6|PAM4、光Coh-Lite（光调制QAM16） [p11]
  - Scale-across：DCI连接前端网络约1k–2k端口，400G；Scale-across扩展后端网络约10k–20k端口，800G/1.6T，“10x DCI bandwidth” [p12]
  - 1.6T ZR/ZR+ scale-across 模块：Marvell称“Industry 1st 1.6T ZR DSP Constellation – in the ECOC show-floor”；光学为 Marvell TFLN-based Optics [p13]
- 提到的公司/客户/产品/标准：Marvell、ESUN/UAL（演进中）与 NVLink/Ethernet（成熟）（p5 看图核实）、OCI MSA、XPO、NPO/CPC/CPX/CPO、Photonic Fabric、OCP MGX/ORV3、Google（OCS拓扑来源）、TSMC CoWoS
- 与业界对比或记录声明（SOTA/首次/record）：“Industry 1st 1.6T ZR DSP”（ECOC展厅星座图展示）[p13]
- 推荐配图页：p12（DCI vs scale-across 端口与带宽对比）；p11（3.2T PAM与Coherent-lite在448G的电/光调制格式对照）

### 0920-pm-Su3-I-08-AppliedMaterials-工艺与封装视角.pdf
- 讲者/机构：Chris Cole / Applied Materials（声明观点为个人观点） | 题目：Fast Narrow for Real Products & Slow Wide for AI Investment Bubble Fantasies | 类型：Workshop（邀请报告，立场鲜明）
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS；次 4 Scale-up/in CPO/NPO/XPO/WSE/OCS
- 核心主张（结论页 p12）：
  1. 快窄是400G光学的唯一现实选项，很可能也是800G（首先2×400G）
  2. 慢宽是未来技术，“great for attracting AI funding”
  3. 今天设计的慢宽到未来到来时将过时
- 关键数据：
  - 电信（长途/城域/园区）与数据中心交换机到交换机（FR4/FR8/LR4/LR8等，CWDM/DWDM/BiDi出货已达数百万、20年）被视为与本次辩论无关，将保持快宽；Coherent-lite出现 [p2]
  - 交换机到XPU（scale-up）：100G serial 大量出货；200G serial 爬坡到高量，设计与标准已完成，提出的慢宽方案（如4×50G）“too late for market window”；400G serial 设计与标准化中（技术上很有挑战） [p3]
  - 100T交换机：Broadcom Tomahawk 6 102.4T，8×12.8T chiplet，每个64×200G SerDes；NVIDIA Spectrum-X 100T [p4]
  - 封装形态：FPO/NPO/CPO/CIO；NPO预期成为高量光学形态；CPO将保持“高性能、封闭生态、低量”产品，注：被某业界高管重命名为“CPO(CP-zero)”以反映近似市场量 [p5, p8, p9]
  - 200T ASIC：I/O为400G PAM4 SerDes；CIO(CPO-AP)基本问题：商业可行封装还需多年；NVIDIA 200T ASIC 图示CPO（约100 mm）与NPO（interposer，约35 mm）对比 [p10]
  - 200T交换机光学可行性表：快窄400G serial：Full retimed 在FPO/NPO/CPO/CIO均Yes；Half(RTLR) FPO Maybe，NPO/CPO Yes，CIO n/a；None(Linear) FPO No，NPO Maybe，CPO Yes；慢宽4×100G或更慢：Full retimed 在FPO/NPO/CPO需要reverse gearbox，CIO Yes；Half和Linear 全为No [p11]
  - 慢宽需要全retimed reverse gearbox，相对RTLR与Linear 400G serial成本/功耗/尺寸/时延更高；“saving grace”：功耗与全retimed 400G相近 [p12]
- 提到的公司/客户/产品/标准：Broadcom Tomahawk 6 / Davisson CPO、NVIDIA Spectrum-X、Ciena Open CPX 模块（p8示例）、OFDM（作为慢宽失败先例）、FR4/FR8/LR4/LR8
- 与业界对比或记录声明（SOTA/首次/record）：无；强立场判断，非实验数据
- 推荐配图页：p11（200T交换机光学方案可行性矩阵，快窄vs慢宽×重定时程度）；p10（NVIDIA 200T ASIC CPO与NPO尺寸对比）

### 0920-pm-Su4-I-02-OpenAI-ScaleUp需求.pdf
- 讲者/机构：Binbin Guan / OpenAI | 题目：Fast/Narrow or Slow/Wide? Choosing for Bandwidth Density and Reliability | 类型：Workshop（邀请报告，AI用户侧）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS
- 核心主张（Takeaways p14）：
  1. 没有单一互连方案适合所有场景；应基于限制性物理边界处的带宽密度与故障后果来选择
  2. OCI 的DWDM方式是提高每纤容量的有前景途径，但需要进一步的故障与恢复分析来评估系统可靠性
- 关键数据：
  - AI adoption：ChatGPT周活 700M（15 Sep 2025）、>900M（27 Feb 2026）、>1B（31 Aug 2026）；Codex周活 1.6M（27 Feb 2026）、3M（8 Apr 2026）、>5M（9 Jul 2026）；基准：GPT-5.6 Sol vs GPT-6 Astra，AutomationBench 18.1%→41.4%，Terminal-Bench 4.0 coding 37.3%→57.9%，Terminal-Bench Science 0.1 22.4%→64.6%（“not an equal-cost comparison”，OpenAI 3 Sep 2026） [p3]
  - 一个请求跨三个硬件区间：Prefill（算力高、显存带宽低、通信平滑）、Draft model（小模型、超低batch、通信受时延限制）、Spec-verify/Decode（Attention+HBM带宽，MoE通信突发）；关键指标为“requests/second/watt at required SLA latency” [p4]
  - Jalapeño芯片架构：64个 core slice 各配一个 HBM slice，集合网络（高带宽低时延）+通用NoC（较低带宽、更灵活）+ scale-up Ethernet bridge [p5]
  - Jalapeño scale-up系统：本地域128个 Jalapeño 由 Broadcom TH6 连接；全局域2048个 Jalapeño、TH6 rail 0–7；“half flattened”两级Clos；张量并行带宽更高、专家并行带宽较低、两者均低时延 [p6]
  - 带宽密度四个物理边界：封装边缘 bandwidth/mm、光引擎占地 bandwidth/mm²、连接器 frontage bandwidth/mm、每根光纤 bandwidth/fiber [p7]
  - 选择顺序：先铜（看链路预算）→ 铜不满足时用快窄可插拔光模块 → 短距GPU链路可用带冗余路径的慢宽，但需可靠性证明 [p8]
  - 可靠性：FIT上界公式 FIT_upper,CL = χ²_{CL,2(r+1)} / (2D) × 10^9；1 FIT = 10^9器件小时1次失效；硬件与软件故障都造成有用工作损失，与恢复时间相关 [p9–p10]
  - 快窄/慢宽/快宽对比表（此处“<50Gb/s 为慢”）：DWDM可在三种设计点提升每纤带宽；慢宽/快宽“冗余路径降低等效失效率，服务性有限”；快窄“有可插拔选项，现场数据可得”；慢宽与快宽需要现场验证 [p11–p12]
  - OCI 实例：每方向4×53.125 GBaud NRZ 波长，A/B波段分离，一根双向光纤，外置激光器；规格为每方向212.5 Gb/s raw，标称200G接口；待测量项为全链路时延、可靠性、功耗与生命周期成本 [p13]
- 提到的公司/客户/产品/标准：OpenAI、Jalapeño（OpenAI 自研加速器，标注 Hot Chips 2026）、Broadcom Tomahawk 6 (TH6)、OCI MSA、NIST（置信区间/寿命阶段模型）
- 与业界对比或记录声明（SOTA/首次/record）：无光学record；Jalapeño 为 Hot Chips 2026 披露内容 [p5, p6]
- 推荐配图页：p6（Jalapeño 128/2048 两级Clos scale-up拓扑与机架照）；p13（OCI 4λ×2方向单纤双向DWDM结构图）；p11/p12（快窄/慢宽/快宽对比表）

### 0920-pm-Su4-I-04-Coherent-器件路线.pdf
- 讲者/机构：Chris Kocot / Coherent | 题目：（p1 看图核实为 "Compute scaling is increasingly interconnect-constrained" 页，非题目页：算力需求每年 4.5x vs 芯片能效每两年 2x，引 Bain & Company 2025；未见明确英文题，内容围绕VCSEL阵列与DWDM的能耗/带宽比较） | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS
- 核心主张（Summary p8）：
  1. AI scale-up 受互连限制；铜到基本极限，光必须并行扩展
  2. 共封装光学在光引擎边界可支持低于1 pJ/bit的链路；宽慢阵列在光纤数量足够时可与DWDM互补
  3. 超过200G/lane，VCSEL缩放需要新器件与集成方法；比较架构必须先统一链路预算与核算边界
- 关键数据：
  - 背景：计算需求增长每年4.5x，单芯片效率增长每两年2x（摩尔定律），缺口扩大（来源 Bain & Company 2025） [p1]
  - 低电流VCSEL阵列：实测器件 ~15 GHz @ 0.5 mA 驱动；投影系统 ~0.75 pJ/b 总链路（32 Gb/s NRZ阵列，UCIe/clock-forwarding假设）；~3.2 Tb/s 每VCSEL阵列（背面发射2D阵列，标为“coherent context”） [p3]
  - DWDM/梳状光源：0.8 Tb/s 单纤（80通道MCM+梳状光源）；MCM密度 5.3 Tb/s/mm²（25 µm pitch电光集成）；369 fJ/b（建模，TSMC光栅损耗含，clocking排除） [p4]
  - 能耗核算对照表 [p5, p6]：PAM4 108G VCSEL阵列 0.90 pJ/b（光引擎，实测，总tile估计~2 pJ/b）；NRZ慢宽VCSEL阵列 0.75 pJ/b（完整系统，投影，32 Gb/s NRZ）；梳状SiPh 0.369 pJ/b（梳+TX+RX+热，建模/校准，clocking排除，另需+0.3–0.6 pJ/b）；Broadcom 100G VCSEL 1 pJ/b（驱动+VCSEL+TIA+PD，实测，100 Gb/s CMOS无DSP）；2.5D WDM interposer 3.5 pJ/b（建模，~1.5 pJ/b模块+~2.0 pJ/b远端激光）；Coherent 106G VCSEL 1.2 pJ/b、128G VCSEL 1 pJ/b（驱动+VCSEL+TIA+PD，实测，16CH，2.047T，已演示）
  - VCSEL缩放挑战：200G/lane时器件优化逼近物理极限；需要铜级稳定性；计算托盘快速温变要求保持带宽、光功率、模式和波长稳定 [p7]
- 提到的公司/客户/产品/标准：Coherent、Broadcom VCSEL、TSMC（光栅、ECTC 2025引用）、UCIe、Bain & Company
- 与业界对比或记录声明（SOTA/首次/record）：p5 表中“最低引用值 0.369 pJ/bit”来自建模而非实测，讲者特别强调不同核算边界不可直接比较；Coherent 自身 106G/128G VCSEL 2.047T 为“measured/demonstrated” [p5, p6]
- 推荐配图页：p5（能耗核算边界对照表：实测/投影/建模）；p3（VCSEL阵列三项关键指标卡）

### 0920-pm-Su4-I-05-HyperLight-薄膜铌酸锂路线.pdf
- 讲者/机构：Christian Reimer / HyperLight | 题目：（首页无清晰文字；内容为 TFLN 在快窄/慢宽/快宽中的定位） | 类型：Workshop（邀请报告/产业）
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS；次 1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件
- 核心主张：
  1. 快窄与慢宽都是通向“快宽”的路径（p3 标题）
  2. 阻力最小的路径：TFLN 调制器可支持 224、260、360、448 GBd 等；Ge与III-V探测器支持100+ GHz；同时可向更宽发展（CDWDM→DWDM，O/C/L波段，扩到~1 µm） [p9]
  3. 采用将遵循最小阻力路径（time to market、成本、可靠性、功耗），“TFLN is ready and ramping” [p9]
- 关键数据：
  - 图3：横轴每通道数据率（12.5–3200 Gb/s），纵轴通道数（1–256），等带宽斜线（6.4T至204.8T等）；NRZ在低速多通道区，XPO在约200G×64，OSFP约200G×4–8，CohLite在约800–1600G×1–2；“Fast-and-Wide”目标区在102.4T/204.8T附近 [p3]
  - 生态：Bulk LiNbO₃ 与 LNOI 晶圆、FEOL/BEOL、模块与系统；多晶圆厂（6英寸与8英寸）、数百万芯片产能、ISO认证、Telcordia GR468 认证 [p6]
  - 应用市场：数据中心（AI集群、DCI、机内网络）、电信（长途、城域、无线接入）、工业与国防、量子计算 [p7]
  - TFLN已部署：Chiplet平台6/8英寸量产；面向电信：130 GBd DPIQ 已部署并爬坡，260 GBd DPIQ 开发中；面向数通：200G/lane PIC 可用，约 21 W 1.6T FRO、约 12 W 1.6T TRO、约 80 W 12.8T XPO，KGD 与 OSFP 模块可用；400G/lane PIC 可用，无外置驱动器直驱 DSP [p8]
- 提到的公司/客户/产品/标准：HyperLight TFLN Chiplet 平台、OSFP、XPO、NPO/CPO（2.5D/3D集成）、Telcordia GR468、DPIQ（双偏振IQ）
- 与业界对比或记录声明（SOTA/首次/record）：未使用“首次/record”措辞；400G/lane 直驱与 130 GBd DPIQ 部署为其产业成熟度声明（未见对比条件）
- 推荐配图页：p3（每通道速率 vs 通道数的“快窄/慢宽→快宽”地图）；p8（“HyperLight TFLN is deployed” 页，含眼图与功耗数字）；p9（最小阻力路径箭头图）

## 本批小结
1. 无一方声称“慢宽全胜”：LightCounting、Arista、OpenAI 主张“取决于系统约束/多选项对冲”；Ciena、Applied Materials 明确押快窄（Cole 称慢宽是“未来技术”，Ciena 称动量仍在通道速率）；HyperLight 提出两者都是通向“快宽”的路径（LightCounting p13、Arista p9、OpenAI p14、Ciena p10、Applied Materials p12、HyperLight p3）。
2. 448G/400G lane 的电通道被普遍认为是拐点：Arista 给出448G下PAM4/6/8所需带宽（~112/90/75 GHz）与插损；Qualcomm 称224G下封装损耗占40 dB预算的30–50%；Ciena 称448G下PCB到前面板“breaks down”；结论都指向缩短电路径（XPO/NPO/CPO）（Arista p3、Qualcomm p5、Ciena p5）。
3. 慢宽（OCI）的实际落地路径是“reverse gearbox → 原生UCIe/OCI → 光中介层”三阶段，且各家都指出reverse gearbox会吃掉功耗优势（Ciena p7、Arista p6、Applied Materials p11–12）；OpenAI 则从可靠性/FIT与服务性角度要求现场验证（OpenAI p8–p12）。
4. 能耗数字不可直接比较：Coherent 明确指出实测、投影、建模的核算边界不同（0.369 pJ/b 建模 vs 0.75 pJ/b 投影 vs 0.90–1.2 pJ/b 实测）；Ciena 的DSP到CPO梯度（18.5→3 pJ/bit）也为示意性系统级数据（Coherent p5–p6、Ciena p5、Qualcomm p7）。
5. 产业标准与生态碎片化：LightCounting 统计2026年6个MSA（XPO、CPX、400G Optics、OCI、SDM4 MCF、Expanded Beam）；Qualcomm 与 Ciena 均推 Open CPX/OCI，Marvell 押 PAM 与 Coherent-Lite DSP 共存并列出 uVCSEL/uLED chiplet 作为scale-in新选项（LightCounting p9/p12、Qualcomm p8、Ciena p9、Marvell p4/p14）。
6. Scale-across 被单独强调：Marvell 称其扩展后端网络约10k–20k端口，为DCI带宽的10倍，并展示业界首个1.6T ZR DSP 与TFLN光学；HyperLight 显示130 GBd DPIQ已部署；LightCounting 相干路线图1600ZR/ZR+ 240–270 GBd（2027/28）（Marvell p12–p13、HyperLight p8、LightCounting p7）。
