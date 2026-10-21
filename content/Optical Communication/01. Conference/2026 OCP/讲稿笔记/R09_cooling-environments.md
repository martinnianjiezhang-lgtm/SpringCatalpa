---
title: "R09_cooling-environments"
tags:
  - OCP2026
  - 讲稿笔记
---

# R09 笔记：cooling-environments

> 文件说明：P218 共 262 页，但实际是 3 段讲稿/会场幻灯的合集。经文字层逐页比对，p41–p261 是 p28–p40 这 13 页的原样重复（重复 17 次，属导出冗余），p262 只有 "Open Discussion"。有效内容为 p1–p40 + p262，下面按讲稿分为三节。
> 本批相关度：属 [底座-冷却]，与 AI 网络/互连无直接关系；按低相关讲稿处理，但市场预测与热边界数据较完整，所以保留较多数据。

### P218 Liquid-Cooling-Market-Update-Industry-Dynamics-Adoption-Signals-and-the-Road-to-Scale

#### 第 1 节：Liquid Cooling Market Update（p1–p21）
- 讲者/机构：Rolf Brink，CEO，Promersion [p1] | 类型：技术分享（市场分析）
- 方向归属（主/次）：主 [底座-冷却]；次 [推理/算力/经济性]、[底座-电力]
- 核心主张：
  1. 液冷的切换是被芯片功耗"逼"出来的，不是比较后选的。讲者称之为 "least-disruption law"：生态会先用尽所有保留现有架构的办法，然后才接受改变架构的方案 [p16]。
  2. "平均机柜已不存在"：机柜密度两极分化，到 2030 年后机柜、电力、冷却密度会迫使数据中心和 IT 基础设施全面重构，混合的、按应用优化的冷却会成为常态 [p9][p13]。
  3. 冷却分为三段：acquisition（器件取热，IT 侧，2–3 年周期）、transport（manifold/QD/CDU/环路，即"seam"）、rejection（冷机/干冷器/冷却塔/热回收，设施侧，几十年周期）。这三段对应两个行业、两种时钟，"seam" 上的价值在于接口，而不在于谁拥有它 [p17–p20]。
- 关键数据：
  - 全球 DC 市场 2025–2035 CAGR 15.7%；增速 2025 年 29.0% 见顶，2026 年 26.0%，2030 年 15.0%，2035 年 8.9% [p3]（预测，Promersion）
  - DC 市场规模约从 2025 年的 \$470B 增至 2035 年的 \$2,000B [p3]（看图，估读）；图上标注 "On Track since mid-2025 (no updates)"，即 2025 年中以后没有修订预测 [p3]（看图）
  - 增长阶段驱动因素：多 GW 级超大规模 AI 园区（50–200 kW/rack）、NVIDIA GB200/NVL72 放量、2023/24 年预分配的电网容量进入实体建设 [p4]；随后进入"liquid cooling mass inflection" [p5]、"fleet refresh"、电力约束放缓扩张 [p6]（预测）
  - 全球平均机柜密度：2025 年约 20 kW，预测 2030 年约 47 kW、2035 年约 98 kW [p8]（看图，估读）
  - 峰值机柜密度：2024 年约 320 kW，2030 年约 1,180 kW，2035 年约 3,550 kW；高密度机柜 2035 年约 2,030 kW [p13]（看图，估读，预测）
  - 预计会过渡到 800VDC 供电架构；单相浸没预计"从小众走向必需" [p12]（预测）
  - 液冷市场：cold plate 2024 年增速 484%，2025 年 137%，2026 年 62%，2035 年 13%；immersion 2028 年增速 250%，2029 年 125% [p14]（预测，增速取自文字层）
  - 液冷市场规模：cold plate 约从 2025 年的 \$7B 增至 2035 年的 \$57B，immersion 约从 2026 年的 \$1B 增至 2035 年的 \$55B [p14]（看图，估读）
  - 2026 年路线图上领先加速器的封装功耗约 2.3 kW；单相冷板在 reticle 级 die 上的物理墙约 4 kW；2020 年以来的趋势约在 2029 年碰到这堵墙 [p15]（引用 Thermal Boundaries 白皮书 chart set，基于厂商 TDP 披露）
  - 顶级加速器 TDP 中以冷板出货的比例约在 24 个月内从 <10% 升到 >90% [p16]；看图估读：2024 年约 8%，2024 年末出现拐点，2026 年约 78%，2028 年约 97% [p16]（引用白皮书，看图）
- 提到的公司/客户/产品/标准：Promersion、NVIDIA GB200/NVL72 [p4]、OCP Immersion Project、Thermal Boundaries in AI Infrastructure 白皮书（Promersion、Oracle、Avayla、Meta，CC BY-SA 4.0）[p16]、800VDC [p12]、ASHRAE [p19]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（cold plate 与 immersion 在 2022–2035 年的市场规模及增速柱线图）；p13（2024–2035 年机柜密度离散度，峰值到 3.5 MW 级）；p16（冷板占比 S 曲线）

#### 第 2 节：Thermal Boundaries in AI Infrastructure（白皮书讲解，p22–p26）
- 讲者/机构：Rolf Brink（Promersion）、Mohan J. Kumar（Oracle OCI 架构师）、Steve Mills（Meta，AI 硬件与数据中心设计技术负责人）、Kelley Mullick（Avayla CEO）[p22] | 类型：标准进展（OCP 白皮书发布，OSAI Strategic Initiative / Cooling Environments，2026 年 8 月）[p26]
- 方向归属（主/次）：主 [底座-冷却]；次 [推理/算力/经济性]
- 核心主张：
  1. 任何冷却方式都受三条边界约束：效率边界（冷却开销开始吞噬产出）、经济边界（avoidance zone 从这里开始）、物理边界（该方式已无法工作）。经济边界和物理边界之间的 "avoidance zone" 解释了技术切换为何总是滞后 [p26]
  2. 单相冷板已进入它的 avoidance zone：技术上仍可行，但不再划算，拖得越久代价越大 [p24]
  3. 没有单一技术胜出，行业需要一套可互操作的多技术工具箱，按热负荷、场地和时机来匹配 [p26]；冷板负责少数极端热点，单相浸没负责大量分布式负载，两者各自覆盖对方够不到的边界 [p25]
- 关键数据：
  - 风冷：器件功耗 100 W 时风扇功耗占比约 5%；约 600 W 处到达效率边界 "knee"，风扇占比约 15%，此后变为超线性；约 1000 W 达到机箱气流物理极限，此时风扇占比约 33%，而线性外推只有约 15% [p23]（看图，估读）
  - 单相冷板（按每个 reticle 级器件功耗）：效率边界约 1.2 kW，经济边界约 2.1 kW，物理边界约 4.0 kW；两相冷板：效率边界约 1.8 kW，经济边界约 3.4 kW，物理边界超出 6 kW 坐标范围 [p24]（看图，估读，引用白皮书）
  - 2026 年领先加速器约 2.3 kW，已落在单相冷板的 avoidance zone 内 [p24]（Promersion 标注）
  - 当前芯片路线图下，单相冷板每个 reticle 的物理边界预计约为 4,000 W [p26]（预测）
  - 单相浸没流体的热容约为水的一半 [p25]（看图）
- 提到的公司/客户/产品/标准：Promersion、Oracle OCI、Meta、Avayla、OCP OSAI Strategic Initiative
- 首次/记录/SOTA 声明：无（白皮书于 2026 年 8 月发布 [p26]）
- 推荐配图页：p24（单相/两相冷板三条边界与 2.3 kW 加速器标线）；p23（风扇功耗占比随器件功耗的超线性曲线）

#### 第 3 节：Liquid Cooling Bazaar（社区问答环节，p27–p40，p262；p41–p261 为重复页）
- 讲者/机构：Steve Mills（Meta）、Rolf Brink（Promersion），以及 OCP Cooling Environments 全体志愿者负责人 [p27] | 类型：面板（开放问答）
- 方向归属（主/次）：主 [底座-冷却]
- 核心主张：
  1. 本环节是开放问答，由各项目和工作流负责人回答各自领域的问题；答不出的问题被视为下一轮工作的缺口 [p39]
  2. 本节主要内容是 OCP Cooling Environments 的组织架构和项目清单 [p28–p38]
- 关键数据（组织信息，无技术数字）：
  - Cooling Environments 负责人 John Fernandes（Meta），联合负责人 Sean Sivapalan（NVIDIA），Steering Committee 为 Steve Mills（Meta）[p28]
  - Immersion Project 负责人 Rolf Brink（Promersion），联合负责人 Jessica Gullbrand（Eaton），下设 Fluids、ITE、Reliability、Solutions 四个委员会 [p29]；工作流包括流体清洗/生命周期/氧化方法/规范、ITE 信号完整性（TE Connectivity、Intel）、材料与元件兼容性、FMEA、Power Distribution、TCO（Asperitas、Microsoft）等 [p31]
  - Cold Plate Project（Dell、Intel），工作流包括 UQD/UQDB Specification Rev. 2.0（CPC、NVIDIA）、Fluid Velocity（Meta、Microsoft）、BMQC/PBMC（Meta）[p37]
  - CDU Project（前身为 ACF），由 Vertiv、Google、AEI、NVIDIA 共同负责 [p38]；Door Heat Exchanger Project（JMGE、Rittal），含 Door HX Interfaces for ORV3 和 AALC sidecar（AMD）[p35]；Heat Reuse Project（AQ Compute、Microsoft，NREL 参与）[p36]
- 提到的公司/客户/产品/标准：Meta、NVIDIA、Eaton、Intel、Dell、Microsoft、Google、Vertiv、Rittal、AMD、Submer、Shell、ExxonMobil、Chevron Phillips Chemical、TE Connectivity、Alfa Laval、NREL、OVHCloud、Asperitas、ZutaCore 等；规范：UQD/UQDB Rev. 2.0、ORV3
- 首次/记录/SOTA 声明：无
- 推荐配图页：p31（Immersion 工作流与牵头单位总表）
