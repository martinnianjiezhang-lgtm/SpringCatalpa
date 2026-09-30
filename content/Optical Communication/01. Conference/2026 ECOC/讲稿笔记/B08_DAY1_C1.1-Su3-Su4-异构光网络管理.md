---
title: "B08 · DAY1 · C1.1-Su3-Su4-异构光网络管理"
tags:
  - ECOC2026
  - DAY1
---

说明：本批实际为 ECOC 2026 Sunday 20 Sep 下午 Workshop「How Will We Manage the Heterogeneous Optical Communication Networks of the Future?」（TU/e 主持），四种介质（HCF/SDM/FSO/SMF）技术方各12分钟讲稿，并非严格的AI运维内容；主席开场页仅为议程，不单列。工业方观点讲者（Relativity、Ciena、Tarra、KPN）的讲稿不在本批。页码为PDF内页码（每张照片常含两张投影片）。

### 0920-pm-Su3-D-02-Southampton-空芯光纤技术方.pdf（第1–6页）
- 讲者/机构：Greg Jasion / University of Southampton (Optoelectronics Research Centre, Hollow Core Fibre Group) | 题目：Hollow Core Fibre: Technology perspective（Workshop 题：How Will We Manage the Heterogeneous Optical Communication Networks of the Future?） | 类型：Workshop
- 方向归属（主/次）：主 1（长途/高波特率器件相关的新型光纤）；次 2（DCI/跨楼园区低时延）
- 核心主张：
  1. HCF 在空气中导光，具备低损耗、宽带宽、低色散、低时延、极低非线性、低背向散射六大优势。
  2. HCF 损耗已降至约 SMF 的 25%，多项集成挑战（性能兼容、成缆、熔接、CO2）已基本解决。
  3. 最大剩余挑战为批量生产；发挥 HCF 全部潜力需要突破石英/SMF 生态的传统边界。
- 关键数据：
  - 近期 HCF 损耗记录：0.091 dB/km @1550 nm，纤芯约29.5 µm（M. Petrovich, Nature Photonics 2025）；0.052 dB/km @1550 nm，纤芯约33.6–38 µm（Shoufei Gao, ECOC PDP 2025）；0.04 dB/km @1550 nm，纤芯约28 µm（P. Li, OFC 2026 M2J.1）[p3]
  - 三个团队报告的 HCF 损耗已低于任何实心光纤 [p3]
  - 带宽：66 THz（HCF）vs 25 THz（SMF），称“250% bandwidth increase” [p4]
  - 色散 1–5 ps/nm/km，覆盖整个低损窗口，可减少DSP、利用直接检测 [p4]
  - 时延约 1.5 µs/km 优势（Δt ≈ 1.5 µs/km，相对实芯光纤更快，利于分布式 AI 训练、扩大 DC 选址地理范围）（看图核实）[p4–5]
  - 非线性低约 10^3 倍（气体或真空芯）；背向散射降低约 10^3，可双向传输、电缆纤芯数减半；带宽 66 THz vs SMF 25 THz（+250%），色散 1–5 ps/nm·km（看图核实）[p5]
  - 挑战页：熔接损耗低至 0.05 dB（L. Feng, OFC 2026）；125 µm OD HCF 损耗 0.5 dB/km；250 µm 涂覆 HCF 损耗 0.25 dB/km；Linfibre 报告近 100 km/次拉丝；YOFC 报告 10,000 km 光纤数据；Microsoft 计划 15,000 km 线缆部署；实心光纤可达 >10,000 km/次拉丝 [p6]
  - 单跨 100 km HCF 双向传输、1 Tb/s/λ 实时信号（引用 L. Feng, OFC 2025）[p5]
- 提到的公司/客户/产品/标准：Linfibre、YOFC、Microsoft（Azure 网络已有 HCF 部署）、Relativity Networks（同场产业观点方）
- 与业界对比或记录声明（SOTA/首次/record）：损耗记录 0.04 dB/km（OFC 2026，他人工作）；HCF 损耗低于实心光纤 [p3]
- 推荐配图页：p3（HCF 与实心光纤历年损耗曲线 + 三个损耗记录的截面图）；p6（六项集成挑战勾选表 + Summary）

### 0920-pm-Su3-D-03-TUe-空分复用技术方.pdf（第1–5页）
- 讲者/机构：Chigo Okonkwo / Eindhoven University of Technology（High-Capacity Optical Transmission Laboratory；页面还有 NICT、Macquarie、Sumitomo Electric、Stuttgart 标识） | 题目：SDM 技术视角（幻灯无独立英文题，随 Workshop 题：Heterogeneous optical networks） | 类型：Workshop
- 方向归属（主/次）：主 1（长途/海缆）；次 4/3（多芯高密度，未讨论）
- 核心主张：
  1. 以 125 µm 标准包层为约束：与现有光缆基础设施兼容，19芯随机耦合光纤已在125 µm内实现。
  2. 利用耦合芯光纤冲激响应亚线性增长，限制均衡器记忆与DSP复杂度。
  3. 需开发多模/多芯放大器，替代实验室里的并行单模放大。
- 关键数据：
  - 19芯随机耦合多芯光纤（RC-MCF）：1.02 Pb/s，1,808.1 km；568.8 Tb/s，5,166 km；包层125 µm [p2]
  - C+L 波段传输系统，环路：86.1 km 19芯 RC-MCF，1530–1610 nm，C波段1548.5 nm 与 L波段1592.1 nm 分别测冲激响应；环路内各复本间隔150 ns；冲激响应时长随距离亚线性增长，5000 km 附近约数 ns（图c纵轴约0–4 ns，读数粗略）[p3]
  - 容量-距离图给出等值线 2.93 Eb/s·km 等，19芯 RC-MCF 两点位于最高等值线附近 [p2]
  - 最大芯数与包层直径关系：包层约80–160 µm，柱状图芯数由约3增至约37（设计相关，非普适上限）；幻灯注明来自Sumitomo Electric供图 [p3]
  - 放大器：45模MMF / 10模、6模FMF 放大器；包层泵浦多芯少模EDFA（Nature Photonics 2016，Chen et al.）[p4]
  - 现场部署议题：L'Aquila 现场，安装与熔接、监测与故障定位、与现有网络互操作 [p5]
- 提到的公司/客户/产品/标准：Sumitomo Electric、NICT、Macquarie University、Nokia Bell Labs（历史）、NTT、L'Aquila 现场网络
- 与业界对比或记录声明（SOTA/首次/record）：数据来源为 B. Kalla et al., SUM Topicals 2026 邀请报告；1.02 Pb/s 为 19芯 RC-MCF 于 125 µm 包层的展示，未直接标“record”字样 [p2–3]
- 推荐配图页：p2（容量–距离散点图与 19芯 RC-MCF 两点）；p3（125 µm 包层芯数柱图 + 19芯环路系统、吞吐随波长、冲激响应随距离）

### 0920-pm-Su3-D-04-Aircision-自由空间光技术方.pdf（第1–7页）
- 讲者/机构：Nourdin Kaai（COO，p1 标题页看图核实，照片分辨率有限）/ Aircision | 题目：FSO: Where the fibre ends | 类型：Workshop（产业发布性质）
- 方向归属（主/次）：主 5（FSO）；次 6（QKD/时间同步）
- 核心主张：
  1. 光纤无法到达之处 FSO 不是竞争者而是答案（结论页“Where fibre cannot go, FSO is not a competitor. It is the answer”）。
  2. 雾/湍流/可用度可通过网络层解决、光相控阵控制与 ITU-T G.641；混合 FSO+无线（无线速率约低100x）作故障切换。
  3. FSO 可延展至 QKD 与 White Rabbit 精确授时。
- 关键数据：
  - 方案：两端光学头（OH），SMF耦合，双向1–5 km，配BBU与网管；卖点：高带宽（4/5/6G）、快速部署（<6小时）、安全（不可探测）、长距（5 km 跨段）[p3]
  - 演示史：2.5 km @10 Gbps（NATO, Hague, 2021）；1 km @10 Gbps（军事基地，2021年12月）；6.1 km @10 Gbps 全双工（布拉格，2022–2023）；1.8 km @4 Tbps（Aveiro，2023）；4.8 km @10 Gbps（Eindhoven，2024）；4.6 km @7.7 Tbps（Eindhoven，2025年4月，标注World Record）[p3]
  - 幻灯标题写"pushing throughput to 5.7 Tbps—a World Record"，而下方卡片为"World Record (4.6 km @ 7.7 Tbps), April 2025, Eindhoven"；看图核实两处数字确实不一致，以卡片 7.7 Tbps 为具体实验值 [p3]
  - Field Photon Loop：TU/e Flux 楼 FSO 链路4.6 km，测风速、雨、温度、闪烁指数 [p4, p7]
  - ITU-T G.641（11/2025）：面向移动回传的短距 FSO 接口；可用度以年度中断概率定义（连续10个SES开始不可用）[p5–6]
  - 混合FSO+无线：无线速率约低100倍但保持链路；在衰落前依据统计切换 [p6]
  - QKD：与QDNL量子测试床同址（四节点，High Tech Campus 至 TU/e），同路径暗光纤已运行QKD；授时：White Rabbit 现为 IEEE 1588-2019 高精度配置，亚纳秒精度、皮秒级精细度 [p7]
- 提到的公司/客户/产品/标准：Aircision、TU/e、TNO、European Defence Agency、VUB、Portuguese Institute of Telecommunications、NATO、ITU-T G.641、IEEE 1588-2019 (White Rabbit)、QDNL
- 与业界对比或记录声明（SOTA/首次/record）：4.6 km @7.7 Tbps World Record（2025年4月）[p3]（另见上述5.7 Tbps不一致）
- 推荐配图页：p3（系统结构图 + 六次演示里程碑，含World Record）；p4（Field Photon Loop 试验链路与FSO痛点：雾、湍流）

### 0920-pm-Su3-D-05-Nokia-单模光纤技术方.pdf（第1–7页）
- 讲者/机构：Oleg Sinkin / Nokia | 题目：No one cancelled SSMF yet（p1 标题页看图核实；p1 上半为承接 Aircision 的结论页） | 类型：Workshop
- 方向归属（主/次）：主 1（长途/DCI/海缆）；次 2（DCI）
- 核心主张：
  1. SSMF 一直获胜，当前无替代技术有足够价值主张取代；除非物理上无法扩展、替代价值过于明显、或小众应用愿付溢价。
  2. AI 是光技术主要驱动，但 DCI/长途仍可继续增加 SSMF；MCF 可能因密度与运维价值较早出现在数据中心内、海缆。
  3. 需要 MCF 原生生态（光纤、连接器、熔接机、收发器、放大器）才能与 SSMF 体验等同。
- 关键数据：
  - 2016 与 2026 同一光纤争论对比（OFC 2016 Workshop“Do We Need Anything Other Than the C-Band?”）[p2]
  - SSMF 挑战：容量处于“实际极限”，转发器SE接近实际Shannon极限；线缆最高13,812根光纤；160 µm 缩径光纤；HCF 唯一价值为低时延，实际容量收益有限 [p3]
  - AI 驱动：Telegeography 2024 国际云 inter-AZ 流量 up to 6.4 Pb/s（读数不确定）；单个多区域 AI 集群每区域对需 Pb/s 量级、up to 48 Pb/s [p4]
  - 数据中心内：XPO 每 RU 16个，204 Tb/s；2,048 根光纤 = 128×16f 线缆 = 每RU 5 cm 束；约30 RU 对应30束；CPO 逃逸带宽 Pb/s 更严峻；180–200 µm 光纤、13,812-f 线缆指示压力点 [p5]
  - DCI/长途：已部署128+光纤对线缆，可继续增加光纤；DCI 大多用 DWDM over SSMF [p6]
  - 海缆：已装多条24光纤对线缆；200 µm 光纤密度1.5x；C+L 使光纤容量约提升 2x，相当于 5–6 年（需求每3年翻倍）；供电是单芯与多芯的共同约束；2-core C-band 在设计、部署与功耗上可能优于 C+L；HCF：50 ms vs 35 ms 低时延应用（除交易外有何受益？）[p6]
- 提到的公司/客户/产品/标准：Nokia、Telegeography、XPO、CPO、hyperscalers、Coherent-lite；OFC 2016 Workshop 旧讲者（DiGiovanni、Essiambre、Payne、Stuch 等）
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p6（DCI/长途/海缆下 SSMF vs MCF/HCF 应用空间对比）；p5（数据中心内密度压力：XPO 204 Tb/s/RU、2048 光纤）

## 本批小结
- 四位讲者形成对比：HCF（Southampton）与 SDM（TU/e）各自宣称技术成熟度提升，而 Nokia 从运营商视角认为 SSMF 仍“always won”，替代方案只在有约束的场景采纳（来自 D-02、D-03、D-05）。
- HCF 损耗记录 0.04 dB/km @1550 nm（OFC 2026）已低于实心光纤最好水平；挑战由性能转向量产（Linfibre 约100 km/次拉丝 vs 实心光纤 >10,000 km/次），Microsoft 计划15,000 km 部署（D-02）。
- 125 µm 标准包层成为 SDM 的共识约束：19芯随机耦合光纤 5,166 km 传输 568.8 Tb/s，冲激响应亚线性增长利于降低DSP；仍需多芯放大器等 MCF 原生生态（D-03、D-05）。
- AI 是共同的需求叙事：低时延/分布式AI训练（HCF）、数据中心机架光纤密度（XPO 204 Tb/s/RU，2048 光纤）、多区域 AI 集群 Pb/s 级互联（D-02、D-05）。
- FSO 定位为光纤延伸而非替代：4.6 km @7.7 Tbps 记录、G.641 标准化、FSO+无线混合冗余、扩展到QKD与White Rabbit授时；结论页提出的开放问题是“故障切换路径是否会拖垮网络”（D-04）。
- 本批并无网络智能化/AI运维内容，主题是异构介质的“管理”前提；管理话题仅以监测、故障定位、互操作等提问形式出现（D-03 p5、Workshop questions）。
