---
title: "B26 · DAY2 · Mo3-B-空芯光纤制造与部署"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo3-B1-领纤Linfiber-打破损耗壁垒-空芯光纤从物理极限到量产.pdf
- 讲者/机构：Yingying Wang，领纤 Linfiber Tech（Linfiber Tech. Co., Ltd.）/ 暨南大学（Jinan University），广州 | 题目：Breaking the Barrier: Hollow-Core Fibers from Physical Limits to Mass Production | 类型：邀请报告（面向熟悉SMF而不熟悉HCF听众的教程式报告）
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件]（空芯光纤传输介质，覆盖DCI/长途/海缆）；次 [2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区]（DCI）与 [3 Scale-out]（DCN，1310 nm HCF）
- 核心主张：
  1. HCF 已在损耗、色散、传播速度、损伤阈值、非线性等光学指标上全面超过 SMF（"Fiber 2.0 时代"），但产能、成本、熔接与部署等工程指标仍远落后，"竞争仍将继续"。[p13]
  2. 单一几何结构同时控制多种相互竞争的机制，存在权衡：表面散射(SSL)与微弯(μBL)、损耗与纤芯直径、高阶模抑制与弯曲鲁棒性（d/D≈0.67–0.68 利于单模，d/D<0.6 利于抗弯）；不同应用（DCN/DCI/长途）需要不同的HCF变体。[p50–p58]
  3. 放大量产的关键难点是拉丝过程中不可逆的"中途管间接触（mid-draw contact）"；间隙管（IT-DNANF）扩大工艺窗口，但未从根本上解决该问题，产业化路径靠多塔并行而非化学沉积设备。[p64–p69]
- 关键数据：
  - SMF vs HCF 对比表：传输损耗 SMF 0.142 dB/km@1550 nm vs HCF <0.05 dB/km；色散 SMF 数十 ps/nm/km vs HCF 几 ps/nm/km；传播速度 c/1.45 vs ~c；损伤阈值 SMF kW–MW（峰值）vs HCF ~GW（峰值）；非线性 SMF 1~10 W⁻¹km⁻¹ vs HCF <0.01 W⁻¹km⁻¹；产能 SMF 每预制棒数千 km vs HCF 每预制棒数十 km；价格 SMF \$20–40/km vs HCF >\$3000–5000/km。[p13]
  - 损耗演进（HCF，图右侧时间线）：1000 dB/km（2002）→40 dB/km（2011）→7.7 dB/km（2017）→2 dB/km（2018）→0.22 dB/km（2021）→0.1 dB/km（2024）→图上写"0.52 dB/km, 2025 (ECOC 2025)"（与图中标注的 0.052 dB/km 不一致，疑为笔误，原样记录）。[p59]
  - DNANF：~0.1 dB/km@1550 nm；OTDR 15 km 光纤 1550 nm 约 0.095 dB/km，1310 nm 约 0.123 dB/km。[p11]
  - IT-DNANF：40 km 长度 0.052 dB/km；OTDR 拟合 0.048 dB/km 和 0.046 dB/km。[p12]
  - 图中"10 dB/km → 0.052 dB/km（2014–2026）"，结构为 Multi-Layer Nodeless；图中标注 Microsoft Azure 与 Southampton 的样品截面（2018、2024、2025）。[p10–p12]
  - Trade-off 例1：ECOC 2025 PDP Th03.01.1（S. Gao）：纤芯直径 33.6 μm，玻璃/涂层直径 230/380 μm，损耗 0.052 dB/km，对弯曲敏感；例2：ECOC 2025 PDP Th03.01.2（G. Mahadiraji）：纤芯直径 14.8 μm，145/250 μm，0.25 dB/km，弯曲不敏感。[p41]
  - 单模 vs 抗弯：基模损耗 0.13 dB/km，高阶模损耗 6.5 dB/m（50,000×），弯曲敏感（Optica 12, 56–61, 2025）；对比抗弯设计：基模 0.28 dB/km，高阶模 12 dB/km（42×），抗弯性能好（Jasion, OFC 2020 PDP Th4B.4）。[p53]
  - 应用需求矩阵：≤10 m 机架内（Scale-up）、10 m–2 km 数据中心内（Scale-out）以 O 带为主；2–20 km（Access/PON/xHauls/DCI）、20–200 km（DCI Scale-across/城域）以 C 带；500–1000 km 长途/骨干、>1000 km 海缆以 C+L 带。长途/海缆的核心指标为低损耗、宽带、低IMI；DCN 核心指标为低宏弯、低机械敏感度、小直径/高密度。[p55]
  - DCN 方案（Bending-Enhanced 1310 HCF）：涂覆直径 250 μm；光纤衰减 <0.5 dB/km@1310 nm；SMF-HCF-SMF 跳线 IL <0.6 dB、RL <-50 dB；宏弯符合 G.657.A2；IMI -55 dB/km；弯曲半径 7.5/10/15 mm 下弯曲损耗图给出与 G.657.A2 对比（具体数值看不清）。图中称"关键挑战在生态：连接器/兼容性"。[p56]
  - DCI 方案：衰减@1550 nm 最小 0.068 / 典型 0.1 dB/km；IMI 系数 -55 dB/km；弯曲损耗 R=3 cm、100圈 <0.1 dB；色散@1550 nm <5 ps/nm/km；PMD@1550 nm <0.2 ps/√km。[p57]
  - 长途潜在方案（大芯 HCF）：衰减@1550 nm 最小 0.038 / 典型 0.07 dB/km；IMI 系数 <-60 dB/km；带宽 C+L；弯曲损耗 R=5 cm、100圈 <0.1 dB；PMD <0.2 ps/√km；讲者标注"更大纤芯增大微弯损耗，实际部署更具挑战"（引 Shoufei Gao et al, ECOC 2025 Th03.01.1）。[p58]
  - 产量对比（图）：SCF 历史累计约 10000 km 量级，HCF 产量到 2025 年前后约 83 km；纵轴为对数，图注"45 years"指 HCF 损耗降到 SCF 已达水平所需时间对比；拉丝塔外径示意 230 mm / 30 mm。[p60]
  - 间隙敏感度仿真：4DNANF 允许的管间距上限 6.3 μm→ IT-4DNANF 9.6 μm（约 1.52× 允许间隙），阈值取限制损耗 0.01 dB/km；间隙过大时限制损耗升至 10 dB/km。[p65]
  - 预制棒放大：DNANF 1.00× 预制棒→最终间隙 6.0 μm（小间隙）；IT-DNANF 1.16× → 9.3 μm（低损耗极限）；1.30× → 13.2 μm（间隙过大）。[p68]
  - 产能预测：SMF 每拉丝线 3000 km/天、约 1M km/年，全球需求 850M 纤-km/年（CRU 对 2027 年预测），需 >1000 条拉丝线，瓶颈在化学沉积（OVD/VAD/PCVD）设备；HCF 每拉丝线 100 km/天、30,000 km/年，若占 SMF 市场 1% 即 8.5M 纤-km/年，需 283 座拉丝塔。[p69]
  - 物理/理论要点（OCR 层面，未逐项核对图）：HCF 中 MFD≈0.7D（SMF 的 MFD/芯径>1，如 SMF-28@1550 nm 10.4/8.2=1.27）；SSL 与芯径的关系约为 D⁻³（写作 λ 依赖弱、芯径依赖强，OCR 指数看不清），SMF 瑞利散射 α_R≈0.11(1.55/λ)⁴ dB/km；C+L 波段 HCF 色散约 2 和 5 ps/km·nm（1阶/2阶带）而 SMF 17 ps/km·nm；SMF 弯曲损耗随波长增大，HCF 相反，且存在临界弯曲半径 R_crit。[p26,p32,p36,p45–p48]
- 提到的公司/客户/产品/标准：Linfiber 领纤、暨南大学；Microsoft Azure（样品截面标注）、University of Southampton、Sumitomo Electric（0.138 dB/km, 2025 OFC）、Corning、Heraeus（石英材料引用）、NTT News Release（引用）；ITU-T SG15 Q5 WD5-25（HCF 变体针对不同应用的文稿）；G.657.A2；OFC 2026 Tu3E.6（Dawei Ge et al）；ECOC 2025 PDP Th03.01.1/Th03.01.2；CRU 市场预测；Petrovich et al., Nature Photonics 19(11) 2025。
- 与业界对比或记录声明（SOTA/首次/record）：HCF 0.052 dB/km（40 km）低于 SMF 理论/实测极限（SMF 约 0.14 dB/km，Sumitomo 0.138 dB/km 为SMF记录）——讲者表述"HCF 重走 SCF 发展路径并最终超越其理论损耗极限"，HCF 用约 20 年走完 SCF 需 45 年的损耗下降历程（图中 "45 years" 箭头）。[p4,p12,p59]
- 推荐配图页：p13（SMF vs HCF 全指标对比表）；p59/p60（HCF 损耗与产量历史曲线）；p55（不同距离/应用对HCF的要求矩阵）；p69（产能预测：283座塔 vs >1000条线）。

### 0921-Mo3-B2-待核-空芯光纤制造与部署.pdf
- 讲者/机构：Samuel Agah（合作者 Chiang Ping Saw, Peter Horak, Natalie Wheeler），Optoelectronics Research Centre, University of Southampton, UK | 题目：Rate of Water Ingress into Hollow-Core Fibre by Capillary Action | 类型：学术论文
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件]（HCF 部署可靠性，含海缆场景图）；次 无
- 核心主张：
  1. 部署的 HCF 一旦断裂会进水，比常规光纤危害更大（管内压力不平衡对机械结构不利），需要理解进水动力学以评估损伤范围与限制手段。[p3,p17]
  2. 将 HCF 建模为圆柱毛细管（Washburn 方程）并引入拟合因子 κ 得到缩放的"有效半径"；κ 约为 0.5 或 0.8。[p17]
  3. 尚不清楚 κ 差异的原因；未曾接触过水的光纤 κ≈0.5，接触过水（湿段已切除）或长时间暴露于大气的光纤 κ≈0.8。[p15]
- 关键数据：
  - 显微镜实验：DNANF 纤芯直径 2r=28.6 μm，30.8 cm 长样品（p7 标注），实测纤芯进水长度在约 78 min 时约 0.7 m，明显慢于圆柱毛细管模型（同一时间模型约 1.45 m）。进水顺序：外层毛细管之间的缝隙（crevices）最先充水，然后纤芯，最后包层毛细管。[p7,p8]
  - OTDR 实验（圆柱模型直径 26.6 μm，进水端浸入水中，OTDR 观测前进水面的反射）：实验1 κ=0.54，约 17 h 进水长度约 3.8 m；实验2 κ=0.83，约 20 h 约 5.1 m；实验3 κ=0.82，约 19.5 h 约 5 m；实验4 κ=0.47，约 21 h 约 3.9 m。[p13,p14]
  - 图示模型（p5）：外压 20–100 bar 下、25 μm 直径毛细管 1 天内的海水进水长度曲线（纵轴数值看不清）。[p5]
  - 反射峰随时间减弱，原因是缝隙中的水先于纤芯中的水，光在被反射前已被散射。[p12]
  - 方法比较：显微镜法可分辨各部分不同速率但端面流动与实际不同；OTDR 法分辨率好、自动化，但无法确定水在各结构中的确切位置。[p16]
- 提到的公司/客户/产品/标准：Microsoft Azure Blog（引用 HCF 加速AI，2024年6月）、TeleGeography Submarine Cable Map（引用）、EPSRC。
- 与业界对比或记录声明（SOTA/首次/record）：无 SOTA 声明；讲者表述为对进水速率的初步定量模型。
- 推荐配图页：p8（显微镜实验实测点 vs 圆柱毛细管模型）；p13/p14（4次 OTDR 实验与 κ 拟合）。

### 0921-Mo3-B3-待核-空芯光纤制造与部署.pdf
- 讲者/机构：Ali Shakiba 等，University of Southampton（Hollow Core Fibre Group / FastNET，EPSRC 资助），含 Microsoft 标识 | 题目：题目页未见（第1页起为 "Why Transient Pressure Is Important?"），内容为空芯光纤拉丝中瞬态压力扰动的热-粘性模型（transient thermo-viscous draw model）；英文原题看不清 | 类型：学术论文（ECOC 2026, 9月21日, Málaga）
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件]（HCF 制造工艺）；次 无
- 核心主张：
  1. 瞬态热-粘性拉丝模型已获实验验证。[p13]
  2. 引入"特征响应时间"，将压力主导的形变与瞬态响应联系起来。[p13]
  3. 拉丝过程表现为低通几何系统：慢扰动引起最大偏差，高频扰动被强烈衰减。[p13]
- 关键数据：
  - 实验验证：套管 20/5 mm（外径/内径）拉至 211 μm 光纤外径；纤芯压力经过阶跃、斜坡、高频振荡输入（压力约 0–14 kPa），模型使用相同实验压力曲线作为输入，复现了实验测得的光纤内径 ID（约 20–90 μm 范围）。[p2]
  - 特征响应时间：压力主导段占颈缩停留时间的比例，纤芯约 1.75 min（约占演化时间的 30%），毛细管约 1.16 min（20%），演化时间约 5.8 min；图上标注 τ_c,Pcore=0.289、τ_c,Pcap=0.192。[p4]
  - 几何敏感度（f=0.002 Hz，慢）：Pcore 20% 与 Pcap 4% 扰动下，间隙（Gap）相对响应最大（约 20–23%），Gap/rcore 约 14–17%，光纤外径 OD 基本不变；小的毛细管位移可引起大的间隙变化。[p7]
  - 幅度/频率扫描：低频（f=0.002）下 Pcore 幅度约 35% 时管间接触指标 χ_MDC 达到 1（接触），幅度 130% 时 rcore 变化约 63%；固定幅度 10% 的 Pcap 扰动下特征频率 f_c,cap≈0.0143 Hz，高于该频率响应和 MDC 风险都下降。[p12]
- 提到的公司/客户/产品/标准：Microsoft、University of Southampton Hollow Core Fibre Group、FastNET、UKRI/EPSRC。
- 与业界对比或记录声明（SOTA/首次/record）：无明确 SOTA 声明。
- 推荐配图页：p4（特征响应时间与颈缩区压力/粘性/表面张力分区）；p12（幅度/频率扫描与接触判据 χ_MDC）；p2（拉丝模型对阶跃/斜坡/振荡压力的实验验证）。

## 本批小结
- 空芯光纤（HCF）的损耗已进入 0.05 dB/km 量级：领纤报告中 IT-DNANF 40 km 0.052 dB/km，DNANF 约 0.1 dB/km，DCI 型号典型 0.1 dB/km（最小 0.068）、长途大芯型号典型 0.07 dB/km（最小 0.038）（来自 B1）。
- HCF 的下一道门槛已从损耗转向工程化与量产：单预制棒仅数十 km、价格 >\$3000–5000/km、熔接/连接器生态未成熟；B1 给出以 283 座拉丝塔并行替代 >1000 条 SMF 拉丝线的规模化路径，并指出拉丝中途管间接触是不可逆失效（B1、B3）。
- 拉丝稳定性是量产的具体瓶颈：Southampton 的模型表明拉丝是低通几何系统，慢的压力漂移（如 f≈0.002 Hz）比快扰动更易使管间间隙变化并引起接触，高于约 0.0143 Hz（毛细管压力，10% 幅度）后风险下降；这与 B1 中"IT-DNANF 将允许间隙从 6.3 μm 放宽到 9.6 μm"的工艺窗口思路互补（B1、B3）。
- 不同应用需要不同的 HCF 变体：DCN/机架内以 O 带、抗弯、小直径为核心，DCI 兼顾 C 带与低损耗，长途/海缆追求 C+L、低损耗、低 IMI 的大芯设计，需与微弯敏感性权衡（B1）。
- 部署可靠性开始被量化研究：光纤断裂后的进水速率可用 Washburn 毛细模型加拟合因子 κ（约 0.5–0.8）描述，实验中 17–21 h 内水前进约 3.8–5.1 m，缝隙先于纤芯进水（B2）。
