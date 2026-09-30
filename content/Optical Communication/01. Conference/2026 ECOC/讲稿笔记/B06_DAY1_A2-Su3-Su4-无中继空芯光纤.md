---
title: "B06 · DAY1 · A2-Su3-Su4-无中继空芯光纤"
tags:
  - ECOC2026
  - DAY1
---

### 0920-pm-Su4-B-01-Southampton-空芯熔接与监测.pdf
- 讲者/机构：Radan Slavik / Univ. of Southampton, Optoelectronics Research Centre | 题目：Hollow-Core Links: Splicing techniques（Workshop Su4 "Could 100s-km long unrepeatered HCF links reshape economics & design of terrestrial and submarine optical networks?"） | 类型：Workshop
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI；次 2 Scale-across（空芯光纤链路的连接/熔接技术，无单独匹配类，取最近）
- 核心主张：
  1. HCF 损耗持续下降（如 0.032 dB/km），HCF-SMF 与 HCF-HCF 的连接损耗不能主导链路总损耗；关键指标为耦合损耗、模式纯度、寄生背反射 [p2-p3]。
  2. 模场适配（GRIN 1/4 节距等）是低损耗、高模式纯度耦合的基础，本讲多数结果基于 GRIN 模场适配器 [p4]。
  3. HCF-HCF 自动熔接已接近现场可部署（<0.05 dB、约百秒量级）[p10]。
- 关键数据：
  - 低损 HCF 的 MFD 15–25 um，对比 SMF 约 10 um [p4]
  - NANF，纤芯 32.8 um：LP01 最小耦合损耗 0.074 dB（图中标注，MFD 约 24 um 处）；LP11 耦合 <-35 dB；讲者文字"最小耦合约 0.1 dB，取决于几何与抗谐振窗口" [p5]
  - 玻璃-空气界面菲涅尔背反射 -15 dB / 0.15 dB 损耗 [p3]；斜角切割方案菲涅尔损耗 3.5% [p6，OCR]
  - 低温熔接+AR 镀膜：插损 0.2 dB，背反射 -29 dB；电弧偏离 AR 镀膜熔接：0.3 dB，-30 dB；胶接+AR 镀膜：0.08 dB，-40 dB [p7]
  - HCF-HCF 熔接损耗随两纤旋转错位角变化：0° 0.012 dB，12° 0.092，24° 0.099，36° 0.163，48° 0.118，60° 0.086，72° 0.059 dB（图值，Zhou et al. SPIE 2025，使用近标准切割机与熔接机）[p9]
  - 自动熔接对比：OFC2024 Kremp ≤120 s，中位 0.13 dB，成功率 100%；CLEO2026 Liu <20 s 对准，旋转精度 0.1°；OFC2026 Feng 97 s 全流程，≤0.05 dB，30/30 次 [p10]
  - 陆地：每 4 km 一个熔点，HCF 段损耗 0.12 dB（按 0.03 dB/km）；海缆：50 km 预制段，总损耗 1.5 dB [p10]
- 提到的公司/客户/产品/标准：Univ. Southampton；引用 Kremp、Liu、Feng、Zhong、Zuba、Nagase（OECC 2021）等；专利 WO 2021/127032A1 [p8]
- 与业界对比或记录声明（SOTA/首次/record）：无自称首创；汇总他人自动熔接成果（0.13 dB/120 s → ≤0.05 dB/97 s）[p10]
- 推荐配图页：p10（自动熔接文献对比表 + 陆/海缆熔接损耗预算）；p7（三种 AR 镀膜连接方案的插损/背反射）

### 0920-pm-Su4-B-02-NokiaBellLabs-空芯链路性能极限.pdf
- 讲者/机构：Haik Mardoyan / Nokia Bell Labs（合作：YOFC 等） | 题目：Performance limits of HCF links（ECOC26 Workshop） | 类型：Workshop
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI；次 2 Scale-across/ZR
- 核心主张：
  1. HCF 超低损耗、超宽带、超低非线性等特性，使 DCI/城域/长途出现新架构：更少甚至无中继、双向超宽带 [p10, p14(OCR)]。
  2. 不同场景对 HCF 设计优先级不同（"一套环结构无法通吃"）：Intra-DC 重带宽与弯曲损耗；DCI/城域重快速部署与弯曲损耗；长途重低 IMI 与低损耗 [p24]。
  3. 通过一系列实验（S+C+L 宽带、ZR 双向、混合跨段、266 km 超长跨段）展示 HCF 链路极限（结论页未单独见，据各实验页归纳）。
- 关键数据：
  - 损耗演进图：DNANF 0.11 dB/km @1550 nm（OFC24，Microsoft/Southampton）；Linfiber IT-4T-DNANF-B 0.052 dB/km @1550 nm（ECOC25）；YOFC GTA-ST-HCF 0.032 dB/km（45.26 km）@1550 nm [p8]
  - HCF 收益汇总：0.052 dB/km（自家实验室实测）；>50 THz 带宽 @ <0.2 dB/km；非线性比 SSMF/PSCF 低 x1000；色散低且平坦 x5 低；背向散射低 x10000；时延低约 30% [p10]
  - 时延容忍包络内覆盖面积 2.25x（HCF 相对 SMF），基础设施距离增加 50%（巴黎数据中心示意）[p11]
  - S+C+L 传输 137.6 Tb/s，带宽 14.6 THz，ST-HCF 20.2 km（链路长度 40.4 km），256 GSa/s、113 GHz 示波器接收，S 段用 BDFA，"频带间无 SRS 串扰"（ECOC 2025 W.03.05.1）[p13]
  - OFC2026 M1B：2x30.4 Tb/s 双向、60.85 km HCF DCI，使用 800G ZR OSFP，Nokia 7250 IXR-6e；800G-ZR 双向 Q 因子约 7.5–8.3 dB（图读数，191–196 THz）[p15]
  - 混合跨段环路：60.85 km ST-HCF + 101 km SSMF（拉曼泵浦）= 222 km 跨段，跨段损耗 39 dB，HCF 前置高功率 DFA 34 dBm；30 dBm 入纤 @192.396 THz；DP-16QAM/DP-64QAM 传输至约 1300+ km 时 AIR 约 700–900 Gbit/s 量级（曲线读数，精确值看不清）[p18-p19]
  - PDP OFC26：稀疏中继 21.7 Tb/s 净速率跨洋传输，266 km 超长跨段（266.38 km GTA-ST-HCF）；21.7 Tbps 传 6660 km、25 个中继，C 波段 [p20-p22]
  - 跨洋 C 波段对比图：容量 x 距离约 100–150 Pbps.km（本工作，跨段约 266 km）；对比之前 HCF C 波段（Hong, ECOC 2025）约 60 Pbps.km（跨段约 130 km）；SMF C+L 约 500 Pbps.km（跨段约 50 km）[p22，图读数]
  - We3-H2（ECOC 2026）：266 km 无中继（单个 booster）实时双向 2x43.2 Tb/s，GTA-ST HCF，Nokia/YOFC [p23，题目页]
- 提到的公司/客户/产品/标准：YOFC（GTA-ST-HCF、ST-HCF）、Linfiber（4T-DNANF、IT-4T-DNANF-B）、Microsoft（Hybrid ARW DNANF、DNANF）、Lyntia/OFS/Digital Realty（马德里 HCF 部署新闻）[p12]、Accotink、Silentsys、Nokia 7250 IXR-6e、800G ZR OSFP
- 与业界对比或记录声明（SOTA/首次/record）：标题称"recent record-breaking loss"，0.032 dB/km 为 YOFC 最新（图中五角星）[p8]；21.7 Tb/s/266 km 跨段跨洋为 PDP 论文 [p20]
- 推荐配图页：p8（HCF 损耗演进与三种纤芯结构）；p22（跨洋 C 波段对比 SMF/HCF）；p19（混合 HCF/SSMF 长跨段环路与结果）

### 0920-pm-Su4-B-03-中国移动-空芯现网部署.pdf
- 讲者/机构：中国移动（China Mobile）（讲者姓名未见） | 题目：Antiresonant Hollow-core Fibers in Deployed Optical Networks: Long-term Stability, Standardization, Operation and …（副标题后半部分看不清，可能含 Interoperability），2026-09-20 | 类型：Workshop
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI；次 2 Scale-across（含 Scale-up/out 场景划分）
- 核心主张：
  1. HCF 现在即可部署：中国现网已运行，两年记录显示无退化 [p11]。
  2. 难题已从光纤转移到现场：如何熔接、如何隔绝气体、如何监测看不进去的链路 [p11]。
  3. 互操作性"现在决定、以后付账"，需考虑标准化特性参数还是结构 [p11]。
- 关键数据：
  - 应用场景划分：机架内 10s m（Scale up）、DC 内 ≤2 km（Scale out）、接入 2–20 km、DC 间/城域 20–120 km（Scale across）、长途 ~500 km、超长途 ~1000 km、海缆至 10000 km；长度占比：接入等 ~70%，长途 ~20%，海缆 ~10%（幻灯表）[p2]
  - 密封方案：CO2 吸收线 1602.876 nm（0.02 nm 分辨率）；缆前附加损耗 0.04 dB/km，部署后附加损耗 0.078 dB/km [p6]
  - 单端吹扫（single-end purge，30.0 km）可完全消除气体吸收；双端充气（17.6 km）；吸收线峰值附加损耗图中标 0.27 与 0.10 dB/km；吹扫耗时长 [p6]
  - 无锡链路 TDNANF-4，18.4 km，2024/10/18–2026/05/26 监测两年，未充气/吹扫，衰减与熔点损耗稳定；熔点损耗变化 -0.19 至 +0.18 dB（图值），部分熔点两年后损耗下降，推测为盘绕应力释放 [p7]
  - 互操作性：4 元与 5 元结构混接耦合损耗最低仍 >0.09 dB，远高于 G.652.D/G.654.E 的约 0.03 dB；同结构不同参数，管径/芯径偏差约 ±7% 可接受 [p8]
  - 标准：CCSA 已批 2 项技术报告，3 项在研；ITU-T SG15 于 2025.10 相关活动、2026.7 启动 GSTR.hcf；IEEE 802.3 NEA "Fiber for AI" 认为 HCF 用于 448G/lane 以太网成为趋势 [p10]
  - 首次商用部署：浙江金华 2024.11；深圳证券交易所场景（OCR，页面 p3 未看图，仅供参考）[p3，OCR]
  - 观众提问：HCF 未来市场规模（5 百万/1 百万/20 万/5 万 fiber·km）及可行价格（USD/fiber·km）[p12-p13]
- 提到的公司/客户/产品/标准：中国移动；CCSA；ITU-T SG15 GSTR.hcf；IEEE 802.3 NEA；G.652.D、G.654.E、G.657；OTDR；NANF-5、TDNANF-4、ST-HCF（广东商用）[p6]；Ciena（OCR，看不清上下文）[p7]
- 与业界对比或记录声明（SOTA/首次/record）：两年现网稳定性记录；"第一个商用部署"（浙江金华，2024.11）[p3，OCR]
- 推荐配图页：p2（HCF 全场景应用矩阵）；p7（无锡两年监测）；p10（标准化进程）

### 0920-pm-Su4-B-04-ASN-长途传输机会.pdf
- 讲者/机构：Alexis Carbo Meseguer / Alcatel Submarine Networks (ASN) | 题目：Challenges and opportunities of HCF in submarine networks（题目大意，第 1 页 OCR 残缺；原标题末尾看不清） | 类型：Workshop
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI（海缆）；次 无
- 核心主张：
  1. HCF 的物理优势（低衰减、低色散、低非线性、低时延、双向、超宽带）明确，关键问题是能否在 SDM 海缆规则下充分利用 [p2, p15]。
  2. 当前 HCF 设计因外径大，每缆光纤对数受限，暂无明确容量优势；需在光纤设计与 SDM 潜力间折中，减小外径或拓宽带宽是关键 [p10]。
  3. 衰减对系统容量的作用有限（仅带来小幅容量增益），但可显著减少中继数；超低衰减可使跨大西洋只需少量中继 [p11-p12]。
- 关键数据：
  - 量产统计：11,265 km ST-DNANF，平均损耗 0.118 dB/km @1550 nm，0.126 dB/km @1625 nm；PDP 记录点约 0.05 dB/km 位于分布最低端（引自 Y. Ding, JLT 2026, "Support Tube DNANF Achieving 0.051 dB/km and Scaled to >10,000 km of Production"）[p3]
  - SDM 规则：Anjana 20 Tbps x 24 FP = 480 Tbps；Amitié 23 Tbps x 16 FP = 370 Tbps；Marea 25 Tbps x 8 FP = 200 Tbps [p4]
  - 外径限制：减径 SCF 约 48 FP（外径约 200 um）对比 HCF 约 16 FP（外径 350 um）[p8]
  - 6000 km 预测容量（供电 18/24/36 kW，默认 48 FP）：今天 0.10 dB/km 的 HCF 设计约 1.1 Pbps，与 SCF 约 1.25 Pbps 相当；HCF C+L 2x32FP 约 3.3–4 Pbps（柱状图读数，SDM x3/x4 情景）[p10]
  - 21 kW @6000 km、2x16FP、C 波段：0.05 dB/km 最优跨段约 170 km/35 中继/24 dBm，容量仅比 0.08 dB/km（约 105 km）多约 6%（若忽略 IMI 再多约 6%）；0.10 dB/km 最优约 85 km/70 中继/21 dBm，比之低约 9% [p11]
  - 0.03 dB/km 时最优跨段可达约 550–750 km量级（曲线读数）[p12]
  - 无中继：HCF 总输出 35 dBm，C 波段，外径 350 um 对比 SCF/MCF 200 um（面积约 x3）；0.08 dB/km 在 440–600 km 仍有约 130–200 Tb/s（读数）；收发器限制约 240 Tb/s [p14]
- 提到的公司/客户/产品/标准：ASN；Petrovich et al., Nat. Photon. 2025（宽带 <0.1 dB/km）[p5]；Undersea Fiber Communication Systems 3rd Ed.
- 与业界对比或记录声明（SOTA/首次/record）：无自称首创；HCF 被 SCF/MCF 对比；引用 PDP 0.051 dB/km 记录 [p3]
- 推荐配图页：p10（SDM 长期容量情景与结论）；p8（外径决定光纤对数）；p11（衰减与最优跨段/容量）

### 0920-pm-Su4-B-05-MicrosoftAzure-长无中继系统要求.pdf
- 讲者/机构：Yang Hong / Microsoft Azure（讲者名据 p1 OCR） | 题目：Requirements for long unrepeatered HCF systems（题目大意，p1 未看图） | 类型：Workshop
- 方向归属（主/次）：主 2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区；次 1 相干/长途
- 核心主张：
  1. 长无中继 HCF 链路的关键系统单元：收发（长途转发器 vs ZR 可插拔）、放大器（常规 vs 高功率 booster）、HCF 熔接与连接器、HCF OTDR、气体吸收线（GLA）[p2]。
  2. 目标是长无中继链路，需要更高 booster 发射功率（NF 良好）与更低链路损耗（含熔点损耗，熔点越少越好）[p8]。
  3. 用 ZR 方案跨长距离 HCF 可降低 CapEx/OpEx、节省机架空间、简化云原生光层架构（配 Tu3-H4 论文）[p7]。
- 关键数据：
  - >100 km 直线 HCF 传输汇总（C 波段速率 vs 距离）：离线最高约 140 Tb/s（<100 km，双向）；实时 MSFT 点：约 50 Tb/s @~100 km 双向、约 25 Tb/s @~200 km、约 10 Tb/s @~250 km、约 25 Tb/s @~440 km；迄今所有 >200 km 直线 HCF 传输均依赖离线处理或实时长途转发器 [p3]
  - ZR vs 长途转发器：400G/λ vs 800G/λ；25.6T 需 64 vs 32 波；DP-16QAM vs PCS-QAM；约 60 GBaud vs 最高 140+ GBaud；cFEC 限 1.25e-2 vs SD-FEC 2.4e-2；放大最大距离约 120 km vs 1000+ km；TX 功率约 -10 dBm vs >0 dBm [p6]
  - 链路预算：OSNR_req = 25 dB/0.1 nm，NF = 5 dB，总发射功率 25 dBm 时，OSNR 达到 25 dB 对应链路损耗约 35 dB（图读数）；32 ch @138 GBd 与 64 ch @60 GBd 对比 [p8]
  - 需求：熔接损耗 <0.1 dB、速度 <97 s；连接器反射 <-60 dB；OTDR 动态范围约 50 dB、空间分辨率约 1 m [p9]
  - 200.5 km 无中继 32x800G 无损传输（Ali, OFC 2025 Th4A.3）；3 跨 442.66 km 32x800G，通过发射机功率优化应对 GLA（Hong, OFC 2026 Th1J.5）；Tu3-H4：全 C 波段 400G ZR，3 跨 427.97 km HCF [p10, p7]
  - 未来无中继可达距离示意（Copilot 生成的"illustrative"曲线）：可用跨段损耗 60/75/90 dB，衰减 0.05 dB/km 时约 1000–1500–1800 km，0.03 dB/km 时约 2000/2500/3000 km（读数，示意性质）[p13]
- 提到的公司/客户/产品/标准：Microsoft（MSFT）、Coherent（p7 图示，具体产品看不清）、ZR/400ZR、SD-FEC/cFEC；引用 Nokia/YOFC 等多篇 OFC 论文
- 与业界对比或记录声明（SOTA/首次/record）：p3 汇总图显示 Microsoft 多点为"实时"结果；未见自称 record
- 推荐配图页：p3（>100 km HCF 直线传输汇总）；p6（ZR vs 长途转发器对照表）；p8（链路损耗-发射功率-OSNR 预算）

## 本批小结
- HCF 已从"损耗竞赛"进入"系统与现场工程"阶段：损耗记录 0.032 dB/km（YOFC，45.26 km）与量产平均约 0.118 dB/km（11,265 km ST-DNANF）之间仍有约 3–4 倍差距（Nokia p8、ASN p3）。
- 连接与部署是当前瓶颈：Southampton 展示 HCF-HCF 自动熔接已到 ≤0.05 dB、97 s；中国移动指出难题在熔接、气体隔绝、不可见链路的监测，并给出无锡链路两年稳定记录（Southampton p10、CMCC p7/p11、Microsoft p9）。
- 气体吸收线（GLA）是长距离的关键损伤：中国移动用密封（预缆 0.04 dB/km 附加损耗）与单端吹扫处理；Microsoft 以发射功率优化、灵活栅格、信号处理应对（CMCC p6/p9、Microsoft p10）。
- 系统层面出现分歧：Nokia/Microsoft 强调超长跨段（266 km 跨段 21.7 Tb/s 跨洋、266 km 无中继 2x43.2 Tb/s、ZR 跨 3 跨 427.97 km），ASN 则认为受外径限制（约 16 FP vs 48 FP）今天的 HCF 在海缆 SDM 下尚无明确容量优势，衰减降低只带来约 6–9% 容量增益但大幅减少中继（Nokia p19/p22/p23、Microsoft p7、ASN p8/p10/p11）。
- ZR 可插拔进入 HCF 长距离场景：Nokia 用 800G ZR OSFP 做 60.85 km 双向 DCI，Microsoft 论述 ZR 简化架构但受 CD/OSNR 限制（约 120 km 放大距离），HCF 低色散、低非线性有望扩展其覆盖（Nokia p15、Microsoft p6/p7）。
- 标准化与互操作性已启动：CCSA 2 项报告、ITU-T SG15 GSTR.hcf（2026.7）、IEEE 802.3 "Fiber for AI" 讨论 HCF 用于 448G/lane；不同结构混接耦合损耗 >0.09 dB（CMCC p8/p10）。
