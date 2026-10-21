---
title: "R08_cooling-environments"
tags:
  - OCP2026
  - 讲稿笔记
---

# R08 笔记：cooling-environments

> 说明：本批 4 份均属 Cooling Environments track，与 AI 网络/互连相关度低，按 NOTE_SPEC 规则 4 写精简-中等版本；数据较多的 P211 写得稍完整。

### P210 03_Cooling Environments Kick-off and Lightning Talks
- 讲者/机构：Steve Mills（Meta，Technical Lead）开场；Project Co-Leads Sean Sivapalan（Nvidia）、John Fernandes（Meta）；闪电演讲：Donghun Kim（LBNL）& Cosimo Pecchioli（Singleton Group）；Kelley Mullick（Avayla）& Maryam Mohagheghi（HF Sinclair）；Matt Koukl（Affiliated Engineers，OCP 驻 ASHRAE TC9.9 联络人）；Mick Jones（Vertiv）；Dr Andy E Young（Asperitas）& Eduard Roytman（Microsoft）；Qusai Soud & Mark Steinke（Nvidia）[p1, p30, p37, p47, p53, p62, p70] | 类型：标准进展（项目总览 + 多个闪电演讲）
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]（Redfish 液冷管理 schema、TCS 侵蚀测试）
- 核心主张：
  1. 冷板是被"强制、突然"采用的：当风冷无法承载最热器件时出现拐点，越过"经济点"后继续沿用旧方法属于"回避区"；标准应在倒逼来临前就绪（"Preparation debt"）[p13 看图, p42, p45]。
  2. 业界缺少商用规模测试床、统一测试协议和可共享的第三方数据，DC Cool + OCP 测试工作流要建测试床网络与统一协议 [p31, p32, p34]。
  3. TCS 回路缺乏基于证据的冷却液流速上限；过高流速加速侵蚀和颗粒生成，过低则增加泵功或限制散热，Nvidia 提出实验框架 [p71, p74]。
- 关键数据：
  - 顶级加速器 TDP 采用冷板的比例：约 2024 年底出现拐点（风冷无法承载最热器件），约 2026 年达约 80%，2028 年接近 97%（看图，读图近似值，口径未注明来源）[p13]
  - 冷却技术路线六段：Air → 1-Phase Cold Plate（"the hotspot, now"）→ 2-Phase Cold Plate → Immersion → 2-phase immersion（"waits on fluids"）→ Microfluidics（封装内）（看图）[p14]
  - DC Cool 合作测试床：NERSC/LBNL、B50B-1275/LBNL（Berkeley）、SNL（Albuquerque）、NLR ESIF（Golden）、TACC（Austin），另有一个公私合营 R&D 测试床为概念阶段（自报）[p34]
  - ASTM D27.04：2026 年 6 月 3–4 日达拉斯会议后启动 2 项标准——单相流体最低要求（Griffin Burk, Ergon）和兼容性标准（Lance Lewand, Doble）（自报）[p39, p40]
  - Redfish 液冷管理（HMLC）积压 10+ 个 mockup 与互操作 profile 待做，提出用 AI 辅助 schema/mockup/profile 验证（自报）[p55, p56]
  - OCP TCO 工具 v1.31 发布：纯 Excel、无宏，新增自上而下输入、CDU 可放在 cluster 级、开销与损耗拆分（自报）[p67, p64]
  - NDT 可检测最小缺陷：Borescope 100–200 µm；UT ≥0.5 mm；PAUT ≥0.2–0.5 mm；激光轮廓/结构光 ≥10–50 µm；破坏性：光学显微 ~1–2 µm，SEM <0.1 µm（自报/汇总）[p75]
  - 悬浮颗粒侵蚀性：金属氧化物（Mohs 3.5–9.0，4,000–6,000 kg/m³）与金属屑（Mohs 2.75–6.5，2,700–8,900 kg/m³）为"Highest"；矿物垢 Moderate；聚合物碎屑 Low；生物质 Negligible（引用 ASHRAE TC9.9, 2019）[p78]
  - 流速/侵蚀实验台：闭环、PG25、多个高风险元件同时测试、Coriolis 流量计、Y 型过滤器，测前测后 CT 和显微检查（实验设计，无结果）[p77]
- 提到的公司/客户/产品/标准：Meta、Nvidia、Intel、Dell、Rittal、Eaton、Promersion、Vertiv、Asperitas、Microsoft、Oracle、Avayla、HF Sinclair、LBNL、SNL、TACC、NLR；ASHRAE TC9.9、ASTM D27/D27.04、IEC TC 108、DMTF Redfish、EE HPC WG；白皮书 "Thermal Boundaries in AI Infrastructure"（Promersion/Oracle/Avayla/Meta，CC BY-SA 4.0）、"Certified AI Datacenters"；Plate Heat Exchanger Base Specification [p8]；ORV3
- 首次/记录/SOTA 声明：白皮书 "Thermal Boundaries in AI Infrastructure" 已发布（NEW）[p39]；ASHRAE–OCP 签署 MoU 并设立 TC9.9 联络人角色 [p49]
- 推荐配图页：p13/p14（冷板采用 S 曲线 + 冷却成本"回避区"示意 + 六段冷却技术路线）；p78（颗粒类型与侵蚀等级表）

### P211 04_Door Heat Exchanger Sub-Project Updates and Lightning Talks
- 讲者/机构：Jabari George（LGTS，Door HX 子项目负责人）；Mohamad Hnayno（OVHCloud）& Dominik Sporna（Valeo）；Rajesh Kasukurthy（AMD）& Adrian Zebrowski（Meta）；Ashok Yadav（Vertiv）& Joe Thomas（Stulz）[p1, p15, p24, p31] | 类型：标准进展 + 技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [底座-机架/机械]（ORV3 门式换热器机械/承重规范）
- 核心主张：
  1. 用 Mega AALC sidecar（直液冷 + 风冷混合）让 AI 硬件进入既有风冷数据中心；sidecar 相比 RDHx 功耗更低、容量更高，差距随机架密度/流量增大而扩大 [p7, p24]。
  2. 铝钎焊换热器可替代铜管换热器：容量相当或更高、更轻、水侧压降更低，但需腐蚀验证 [p9, p17]。
  3. OCP Door HX 规范建立统一的机械、承重、热性能报告口径，使不同厂商可比 [p32, p33]。
- 关键数据：
  - 机架功率预计 2030 年前超过 1 MW；液冷采用率趋向 98%（自报/预测，未注明来源）[p8]
  - Mega sidecar：单相冷却液需 10+ 个机架宽度才能做到 1 MW；两相可显著缩小宽度（自报）[p8]；设计目标 1 MW 机架功率，AI 芯片机架 TDP ~500 kW，构建单元为 OCP 双宽机架形态换热器 DWHX [p25]
  - 单个 DWHX 仿真：Flat 176 kW / 风阻 420 Pa / 液阻 250 kPa；Slant 177 kW / 390 Pa / 260 kPa；V 形 179 kW / 150 Pa / 300 kPa；条件：进风 30°C、出风 40°C，液体进 50°C、回服务器 40°C，风量 18,000 CFM，液流 1.5 LPM/kW；铜管和铝管冷量相近（仿真）[p26]
  - 铜管 HX vs 铝钎焊 HX（OVHCloud 机架）：冷量 5,360 W vs 5,650 W（+5.4%）；水侧压降 0.36 vs 0.12 bar（−67%）；空重 16.8 vs 8.0 kg（−52%）（实验/自报）[p9]
  - 48U 散热器（ISO 条件）：铜 23.1 kW vs 铝（Valeo）32 kW（+38.5%）；干重 35→24 kg（−31%）；湿重 43→36 kg（−16%）；功率密度 0.54→0.89 kW/kg（+65%）；风侧压降 62→72 Pa（+16%）；冷却液侧压降 26→21 kPa（−17%）（实验）[p17]
  - 10 kW 机架 PPUE：铜 HEX 1.044 vs 铝 HEX 1.032；每机架冷却功耗 444 W→327 W，约降 25%（主要来自机架内 CDU×2 功耗 240→120 W）（实验/自报）[p20]
  - OVH 腐蚀台架水质 Day 1 → Day 120：pH 8.56→7.7；电导率 1122→1700 µS/cm；Al <0.1→0.16 mg/l；COD 3.7→2200 mg/l；Mn 62→508 mg/l（实验；Cu 一项单位 mg/l 与 µg/l 混用，存疑）[p19]
  - OVH 系统测试：3200 W 加热元件 5 min 开/5 min 关、50°C 循环，1/3/6 个月挂片，自 2026 年 2 月运行 [p10]；全部 5 项测试 2027 Q2 完成 [p21]
  - Door HX 规范：被动门最大深度 305 mm、主动门 370 mm；关门间通道最小 915 mm（36 in）；推荐门重 ≤100 kg，加支撑可到 150 kg，极高密度门最高 200 kg 需评估；统一额定工况为 17°C 冷却液入口、45°C IT 排风；服务器进风 18–27°C（ASHRAE TC9.9）；被动门风侧压降 <15 Pa，主动门风扇功耗 <额定冷量 2%；支持 AC 与 48 VDC 供电 [p33]
  - Door HX 规范路线：2026 年 1 月启动，Rev 0.5 社区评审完成，Rev 1.0 正式发布目标 2026 Q4 [p11]
- 提到的公司/客户/产品/标准：AMD、Meta、Stulz、Vertiv、Valeo、OVHCloud、Chatsworth、LGTS、TESS Energy、AVTRON、Kuhltherm、Asperitas；ORV3、Open Rack Wide (ORW)、EIA310、VDI 2035、ASHRAE TC9.9、Redfish；白皮书 "AALC Sidecar Solution for Enabling High Power Density Hardware"
- 首次/记录/SOTA 声明：无（Valeo 称铝散热器全球年产约 3000 万件 [p16]，为产能自报）
- 推荐配图页：p17（铜/铝 48U 散热器对比表）；p26（Mega sidecar DWHX 三种 HX 形状仿真）；p33（Door HX 规范要点表）

### P216 Fluid-Flush-Fill-Cart-for-Pre-Deployment-Conditioning-of-Liquid-Cooled-IT-Systems
- 讲者/机构：Himanshu Modi（NVIDIA）、Kevin Joseph（Meta）[p1] | 类型：标准进展（Base Specification 提案）
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：
  1. 液冷机架上线前流体状态不受控（残液、颗粒、溶解气体、截留空气；PG25 浓度因供应商/站点而异；仅靠目视验收；无审计记录）会拉长单机架调试并造成返工 [p2]。
  2. 只标准化接口和运行包络，不标准化推车设计；泵拓扑、控制、封装留给供应商 [p3]。
- 关键数据：
  - 范围：移动式单人操作推车，用于 CDU 到机架的 TCS 回路（PG25），供回 dry-break 接口、调压氮气入口；不含设施水、两相/介电流体、固定 CDU [p3]
  - 清洁液与回收液分路：泵 N+1 + VFD，粗滤 + 推荐精滤，过滤器压差监测 [p4, p7]
  - 六种模式：Flush、One-way fill、Closed-loop condition、Drain、Sample、N₂ Purge/Dry [p5, p6]
  - 互锁：泄漏、过压、O₂、缺相故障；关键报警不可屏蔽 [p9]
  - 材料与清洁度：钝化 304L/316L、PTFE/PEEK 类材料，过氧化物硫化 EPDM 或 FKM 密封；清洁度 ISO 4406 18/16/13 [p9]
- 提到的公司/客户/产品/标准：NVIDIA、Meta；PG25、ISO 4406；OCP Cooling Environments
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（推车流体回路图：清洁/回收分路）

### P217 Know-Before-You-Flow-PG25-Mixing-Thresholds-for-DLC
- 讲者/机构：Jake Davis（Meta）、Sung A Kim（Castrol）[p1, p19] | 类型：标准进展（ASHRAE-OCP 联合研究更新）
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：
  1. 不同供应商的 PG25 在部署和维护中会被有意或无意混用，目前没有标准化的模拟工况方法来评估混合冷却液的不良影响 [p3]。
  2. 行业需要两个尚不存在的标准：TCS 版的模拟工况方法（类比 ASTM D2570），以及面向层流冷板、可取样的传热腐蚀方法（"D4778 for cold plates"）[p17, p18]。
- 关键数据：
  - 测试矩阵：4 种流体 A–D，两两 50:50 混合（含正反顺序）加各自未混合对照；指标为化学兼容、腐蚀风险、材料（EPDM）兼容；混合样品由第三方制备 [p4]
  - Phase 1 实验室筛选（ASTM D8040 金属腐蚀：C11000 铜、SS304、SS316、黄铜；ASTM D471 过氧化物硫化 EPDM），流体厂商牵头，目标 2026 年 10 月；结果"2026 年 10 月下旬发布"，本稿无数据（看图）[p5, p7, p8]
  - Phase 2 模拟工况：液体回路 + 热测试载具（TTV）+ 金属挂片架，超大规模用户牵头，2026 年 11–12 月开始，持续 6 个月 [p5, p10]
  - 方法要点：启动阶段不加额外缓蚀剂；先设平衡期再冲洗并换新液（应对缓蚀剂初始吸附造成的"early dip"）；用储液罐而非膨胀罐，N₂ 覆盖防氧化；ASTM D2688 失重挂片（C26000 黄铜 ~30% Zn、304 SS、C11000 铜）；以无缓蚀剂 25% PG 作为对照 [p11, p12, p14, p15, p16]
  - 现有标准局限：ASTM D2688 为等温环境；ASTM D4778 为湍流加热管，不能代表冷板层流；冷板腐蚀评估目前只能靠破坏性拆解 [p17]
- 提到的公司/客户/产品/标准：Meta、Castrol、ASHRAE；ASTM D8040、D471、D1287、D1121、D5827、D1881、D6130、D2570、D2688、D4778；新 OCP "Coolant Technologies Testing Workstream" [p10]
- 首次/记录/SOTA 声明：无（Phase 1 结果未在本稿给出）
- 推荐配图页：p4（50:50 混合测试矩阵与三阶段测试顺序）；p7（实验室筛选分析方法表）
