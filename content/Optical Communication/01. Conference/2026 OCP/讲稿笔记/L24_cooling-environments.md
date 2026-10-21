---
title: "L24_cooling-environments"
tags:
  - OCP2026
  - 讲稿笔记
---

# L24 笔记：ai-open-dc-power-distribution / cooling-environments / cooling-immersion / executive-sessions / expo-hall-sessions（低相关精简版）

### P205 Solid-State-Circuit-Breaker-SSCB-and-DC-Fault-Manager
- 讲者/机构：Ke Sun（Vertiv，p9 邮箱域名）| 类型：技术分享
- 方向归属：主 [底座-电力]
- 核心主张：① 800 VDC 保护是系统功能而非器件功能（p1）；AC 靠等电流过零、上游故意延时、电弧耗能，800 VDC 三点都不成立，需"强制过零、µs 级检测、钳位吸能"（p2-3）。② 选择性从时间曲线转移到通信链路：SSCB 本地跳闸，DC Fault Manager 负责区域判定、闭锁上游、重新上电（p7）。
- 关键数据：
  - AC 现状：ACB 短延时 300–400 ms，PDU MCCB 约 100 ms，机架分支瞬时 1–2 周波；ITIC 允许 IT 负载穿越 20 ms 中断 [p2，引用 ITIC]
  - Diablo 400 v0.7.0 §8.1.3 目前规定 ±400 V 输出用熔断器和继电器 [p3]；SSCB 清除时间"数十 µs"，熔断器/机械 DC 断路器为 ms 级 [p4，自报]
  - DC ITIC：800 V ±5% 正常；900 V 稳态上限；1100 V 钳位平台 20–300 µs；允许 0 V 持续 20 ms；2 kV 浪涌 IEC 61000-4-5 [p5]
  - 示例母线：4000 A / 800 V，4 个 1000 A SSCB 分接箱 [p6]；母排回路电感约 0.1–0.2 µH/m，电缆数倍 [p6]；故障约 1 kA/µs [p7]
  - 时序：检测+跳闸 0.7–3 µs，通知对端 <5 µs，隔离定位 ms，重新上电秒级；"打断约 40 µs" [p8，自报]
  - 提议接口预算：跳闸事件上报 <10 µs，闭锁/许可 <5 µs；作者注明预算是提议、非实测 [p8]
- 提到的公司/客户/产品/标准：OCP Diablo 400 v0.7.0、OCP DC PD、UL 489I、IEC 61000-4-5、ITIC/CBEMA、IEEE 9/14/39 节点测试系统
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（SSCB 与 DC Fault Manager 分工及三类故障位置）；p8（跳闸与重新上电时序、接口表）

### P206 Using-the-Full-Low-Voltage-Direct-Current-Range-up-to-1500V-for-Data-Centers
- 讲者/机构：Laurens Mackay，CEO & Founder, DC Opportunities | 类型：技术分享
- 方向归属：主 [底座-电力]
- 核心主张：① LVDC 范围到 1500V（国际标准电压 350/700/1400V，对应数据中心语境 400/800/1500V）可用于不同功率等级，高功率用高电压 [p2]。② 800V 设备应能在 750V 以下工作、并满足 IT 接地或单极 TN-S 的爬电/间隙要求，从而兼容 700/1400V TN-S 系统 [p12]。
- 关键数据：
  - 1400V 单极相对 400/800V 双极：有源导线材料相对值 1–1.5 对 2–3；同等平衡功率下线损相对 0.5、电流相对 0.5 [p5，白皮书对比表]
  - 半导体断路器综合品质因数（越低越好）：表中值 1–3 不等，1400V 单极 TN-S 为 1/IT 为 2 [p5；多列对应关系不易确认，存疑]
  - 脉冲耐受电压 OVC II：350V 系统 2.5 kV，700V 系统 4 kV，1400V 系统 6 kV [p6]；对地间隙 OVC II 1.5/3/5.5 mm [p6]
  - 机架内电压比示例：700V 档标称 700V 范围 620–840V，800V 档范围 640–840V（标称 800V，下限 80%）[p9，看文字层数字，对应关系存疑]
  - 脉冲耐受电压 DC 值提议取 AC rms 的 1.5 倍（IEC 60364-4-44 修订中）[p14]
- 提到的公司/客户/产品/标准：OCP DC PD 白皮书 V1.1.0、Mt. Diablo 0.7.0（2026年3月）、NVIDIA 架构白皮书（2025）、IEC 60664-1、IEC 62477、NEC 240.15(A)
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（电压/极性/接地组合对材料、线损、半导体断路器的影响表）

### P207 What-the-Automotive-Industry-Can-Teach-Us-About-800-VDC-Data-Centers
- 讲者/机构：Adam Morton，CTO Data Centers，Flex | 类型：技术分享
- 方向归属：主 [底座-电力]
- 核心主张：① 800 VDC 在汽车业已有经验，可迁移到数据中心：电池安全/BMS、联锁回路、绝缘监测 [p2, p4-6]。② 标准机构应把数据中心要求对齐其他行业已有要求 [p7]。
- 关键数据：
  - 800 VDC 在全球市场占比：汽车 22 年爬坡、CAGR 25%+；数据中心 3 年爬坡、CAGR 90%+ [p2，来源 S&P Mobility 2026-05、JLL 2026-01、Flex 分析；预测]
  - EV 短路故障须在 <10 µs 进入安全状态 [p6，自报]
  - EV 须保证故障率 <100 FIT（"10^9 operating hours"）[p6]
  - IMD 持续测量 800V 母线对底盘电阻，比 GFCI/RCD 更不易误跳 [p6]
- 提到的公司/客户/产品/标准：Flex、UL Solutions（联合白皮书）、S&P Mobility、JLL、OCP Power Distribution 子项目
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（汽车与数据中心 800 VDC 采用曲线）

### P208 01_Building a Scalable Waste Heat Ecosystem Datacenter Waste Heat, Offtak
- 讲者/机构：Maria Viitaniemi, Bharath Ramakrishnan，Systems Technology Team, CO+I CTO, Microsoft | 类型：技术分享
- 方向归属：主 [底座-冷却]（废热回收）；次 [推理/算力/经济性]
- 核心主张：① 废热回收正成为许可要求，且不应局限于区域供暖（p3-4）。② 用"先过关口（技术/运营/市场/法规，通过/不通过），再按经济/碳/水/社会加权评分"的流程评估废热去向；市场撮合需要统一语言、标准合同和共享数据（p6-8, p15）。
- 关键数据：
  - 德国对 >200 kW 数据中心的 Energy Reuse Factor 目标：2026 年 10%，2028 年 20% [p3，引用法规]
  - Virginia HB2578 在 2025 年未通过，未生效 [p3]
  - 每 1 MW·年：约 650 户供暖、8.76 GWh 输出；产水 6,000–13,500 m³；捕碳 2,000–5,000 t CO₂；约 2 公顷温室；处理水 255,000–365,000 m³ [p5，自报，各列对应路径见图，存疑]
  - 评分示例（权重各 0.25）：地点 1 的食品饮料总分 43.8 对产水 72.5；地点 2 反之 [p12，示例性]
  - 德国某场景：可能释放数百 MW、每年数千 GWh 热、约 50,000 户 [p16，"Subject to assumptions"]
- 提到的公司/客户/产品/标准：OCP Waste Heat Reuse 101、OCP Waste Heat Reuse 子组、NZIH
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（Inputs-Gate-Score-Decide 流程）；p5（非区域供暖的废热去向及每 MW 产出）

### P209 02_Cooling Distribution Unit Sub-Project Overview and Updates
- 讲者/机构：Pardeep Shahi（Dell）、Hussam Kabbani（Google）| 类型：标准进展
- 方向归属：主 [底座-冷却]
- 核心主张：CDU 工作组把液冷变成可部署基础设施：统一需求、接口/术语/测试方法、控制与冷却液质量指导（p2）。
- 关键数据：已发布：Coolant Distribution Units: Specifications and Qualifications、Project Deschutes（Google）、Project Brazos（Google）；2026 进行中：详细 CDU 白皮书（部件、控制、电气、冲洗）；后续：CDU 冲洗与调试指南、泵驱两相冷板 CDU [p3]；贡献时间 2026 年 11 月 [p5]
- 提到的公司/客户/产品/标准：Dell、Google、Deschutes、Brazos
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（CDU 工作组进度）

### P212 05_Heat Reuse Sub-Project Overview and Updates + Economics Tool Contribut
- 讲者/机构：Bharath Ramakrishnan（Microsoft）、Jaime Comella（DayOne）为子项目负责人；分段讲者 Gabriel Lazar（Submer）、Steven Schon（Quantacool）、David Gardiner、Petter Terenius（Uppsala Univ）、Gemma Reeves（Alfa Laval）、Mats Carselid（Danfoss）、Jack Kolar（Dataquarium）| 类型：标准进展
- 方向归属：主 [底座-冷却]（热回收）
- 核心主张：① 参考设计聚焦 24/7 型热利用（海水淡化/MEE、DAC）以解决传统热回收受限于季节性需求的问题（p5, p7）。② 现实项目的经验：运营方主导、进水温度高（45 °C）、水回路几乎是必须、热泵未经此类应用与可用性验证（p14-15）。
- 关键数据：
  - MEE 淡化：约 33 m³/天/级/MW 热；每级目标 5 °C ΔT；级数 N=(T_TCS_cool − T_water_feed)/5 [p11，自报]
  - 热泵+反渗透预热方案的能量回收效率 <4%（RO 功率下降/回收废热）[p9]
  - 提议指标 NWUE=(W_consumed − W_generated)/E_IT [p11]
  - 现场案例（5 MW 大学 HPC、市政供热、欧洲大型托管商）：45 °C 进水可免冷机、减轻热泵负担；一个项目耗时 5 年、基本无经济激励 [p14]
  - 就绪度评估清单中的设计参考值：热回收机房 ≥56 m²/MW（≤1 MW 余热）或 ≥37 m²/MW（≥1 MW）；预留热泵空间 ≥10 m²/MW；储罐 ≥80 m³/MWh [p22]
  - 政策：Virginia 通过首个数据中心热回收立法，能源部报告 9 月 1 日到期；EU 拟将数据中心热回收纳入 2026 年 €10 亿 Clean Industrial Heat Auction（须用热泵）[p18]
  - 欧洲热回收匹配平台 hrp.eudca.org 处于 beta [p23]；热回收模块基础规范目标 2027 年 OCP 提交 [p30]
- 提到的公司/客户/产品/标准：Microsoft、DayOne、Submer、Quantacool、Alfa Laval、Danfoss、Dataquarium、EUDCA、EuroHeat & Power、NZIH；Economics 工具在 GitHub OCP-CE-HR-Economics-Tool（处于初期）[p35]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（热回收指导路径全景）；p8（MEE 多效蒸发与余热回路示意）

### P213 06_Waste Heat Recovery Pathways for AI Data Centers Emerging Opportunitie
- 讲者/机构：Yingbo Zhang，Research Scientist, UC Santa Barbara | 类型：技术分享
- 方向归属：主 [底座-冷却]（废热回收路径）；次 [推理/算力/经济性]
- 核心主张：① 液冷出口 50–60 ℃ 的废热可直接用于供暖、吸附制冷等；ORC 发电、DAC、取水则需热泵升温，其中 ORC 经热泵升温净功率为负（p3, p15）。② 供暖受季节错配限制，DAC 与大气取水可全年用热，具体效果因站点而异（p23）。
- 关键数据：
  - 机架功率密度 2021 年 7 kW → 2026 年 130 kW，19 倍 [p3]
  - 每回收 1 MJ 废热的减排（以对应基线计）：建筑供暖 8.5–129.8 g CO₂e [p9]；温室供暖 8.5–185.0 g [p10]；制冷 1.8–14.9 g [p13]；发电 1.1–8.7 g [p16]；DAC 116.0–226.5 g [p18]；取水 13.7–83.8 g [p21]（均为作者核算/文献参数）
  - 热泵+吸收式 vs 传统冷机（500 kW 冷量）：电输入 178.6 kW 对 100 kW，净 COP 2.8 对 5.0（假设热泵 COP 4.0、吸收式 COP 0.7、冷机 COP 5.0）[p12]
  - 吸附式冷机实验 COP 约 0.45–0.5，可由低至 50 ℃ 热驱动；吸收式需 >80 ℃ [p11, p13]
  - ORC：500 kW 废热经热泵（COP 4.0）+ORC（效率 15%）净功率 −66.7 kW [p15]；直接用 50–60 ℃ 废热的 ORC 电效率 3.7–4.7% [p16]
  - 30 MW 数据中心年估算：制冷减排 1,362–11,277 t [p13]；发电 8.4 GWh、约 780 户 [p16]；DAC 减排 87,796–171,440 t [p18]；取水可满足约 800–1,000 户年用水 [p22]
  - 取水能耗：电加热 1.7 kWh/L → 热泵+废热估计 0.57 kWh/L（假设热泵 COP 3）[p21，估算]
- 提到的公司/客户/产品/标准：Equinix（法国屋顶农场）、QScale（加拿大番茄）、Terra Ventures（加州）、InvenSor LTC 90 e plus [p10, p13]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（热泵+吸收式 vs 冷机对比表）；p18（DAC 减排量）

### P214 07_What Shapes CDU Performance A Comparative Study of Design Choices for
- 讲者/机构：Jake How（Gamma Technologies）、Tommaso Ferrarese、Holly Hilten（Alfa Laval），与 Stulz 合作 | 类型：技术分享
- 方向归属：主 [底座-冷却]
- 核心主张：① 2.3 MW CDU 的换热器选型不同，会改变一次侧流量、泵、管径、CAPEX 与年耗电，应作为系统在全年维度评价（p13）。② 规格应写出非设计点（环境温度扫描、结垢、其他流体、部分负载）并公布工作点，不只写 MW（p14）。
- 关键数据：
  - 校准基准 Deschutes 5：2.0–2.3 MW，ATD 3 K，TCS/FWS 流量各 500 GPM，3 个钎焊两程并联换热器 [p5]
  - ANSI/ASHRAE 127-2020 Addendum b 于 2026-02-27 批准，首次为液-液 CDU 定义测试方法；FWS 供水 26 °C，TCS 30/39.6 °C，部分负载 75/50/25% [p6]
  - 十个满足同一 2.3 MW 的选型：回水温度 34–39 °C，一次侧流量 660–940 GPM；资本成本相差约 3 倍，年能耗相差约 17% [p13，仿真]
  - 相对年能耗变化（3K 趋近 / 结垢 0.9e-4 m²K/W / PG35）：Deschutes 基线 −1.7%/+3.0%/+2.6%；钎焊 2HX 1 程 4K：−0.5%/+7.0%/不可行（供不出目标温度）；垫片式 1HX 1K：−2.1%/+0.4%/+0.4% [p11，仿真]
  - 年气温分箱采用 Dallas, TX，共 8760 h [p10]
- 提到的公司/客户/产品/标准：Gamma Technologies、Alfa Laval、Stulz、Deschutes、ASHRAE 127
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（三点结论）；p8、p9（见 cloud_text 转写）

### P215 Air-vs.-Liquid-Where-Does-Air-Cooling-Still-Win-for-General-Compute
- 讲者/机构：Jayesh Shah（Microsoft）、Stewart Nguyen（Lenovo）| 类型：技术分享
- 方向归属：主 [底座-冷却]；次 [底座-机架/机械]
- 核心主张：通用计算上，加宽风冷机箱/机架（900 mm）是阻力最小的路径；只有实测热裕量、热流密度或场地约束超出风冷包络时才选液冷（p8-9）。
- 关键数据：
  - 高端服务器 CPU TDP 已超过 650 W，趋向 1000 W+；每路内存通道 DDR4 8 → DDR5 16 → DDR6 约 32 [p3，引用公开厂商资料/行业估计]
  - 900 mm 宽较 600 mm 气流面积增加约 50%，同流量下风速降约三分之一；每 kW 散热风扇功率降约 20–30% [p5，自报，机架测试待定]
  - 全液冷（无风扇）基础设施成本比混合液冷高 50% [p4，自报]
  - 32 通道 2S 板需约 300 mm 额外宽度，I/O 或磁盘可多 >50% [p7，估计]
  - 材料明示是早期数据，非贡献/规范/新工作组 [p10]
- 提到的公司/客户/产品/标准：Microsoft、Lenovo、DDR6、OCP Rack & Power、Cooling Environments 例会
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（四种路径对比矩阵）；p5（宽机箱风扇功率曲线）

（P214 补充：看图 p8 十个选型的一次侧回水温度约 35.4–39.4 °C，流量约 660–940 GPM；p9 低于约 21 °C 各选型总功率约 175 kW 且重合，回水更热者压缩机启动更晚，均为仿真，详见 cloud_text/L24.md）

### P220 Managing-Liquid-Cooling-At-Scale-Tooling-Telemetry-and-Reliability-for-High-Density-AI-Racks
- 讲者/机构：Zach Miller（Hardware Systems Engineer, Meta）、Kalpak Dhake（Thermal Engineer, Meta）| 类型：技术分享
- 方向归属：主 [运维/可靠性/遥测]；次 [底座-冷却]
- 核心主张：① 故障点随车队规模增长而修复能力不增长，需要自动化监测（看图 p3-4）。② 每种液冷单元通过不同寄存器映射暴露同样的物理量，运营方须按厂商与代际重复实现检测/诊断/修复；呼吁最低遥测契约（相同信号、相同寻址、各厂商一致）和机器可读诊断规范（p27）。
- 关键数据：
  - 硬件代数 × ODM 厂商 × 控制器版本 × 固件版本，生产中 50+ 种不同配置 [p8，自报]
  - 机架功率 2015 年 12 kW/rack 时风冷足够（看图 p2，后续帧未见）
  - 监测分三层：机架管理控制器 Redfish/I2C/PMBus/Modbus（带外）、主机 agent 与采集守护进程（带内）、车队管理平台 [p10]
  - 湿度误报案例：多机架因绳式传感器冷凝报漏液并断电，改用去抖+跨传感器过滤后事件约减少 100 倍 [看图 p24，自报]
- 提到的公司/客户/产品/标准：Meta、Redfish（DMTF）、AALC、CDU (FLC)、OCP Cooling Environments
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（带外/带内监测范式）；p24（湿度误报案例）

### P221 Maximizing-Cooling-Performance-in-Data-Centers-by-Optimizing-Fluid-Velocity-Limits
- 讲者/机构：Matthew Schantz、William Grant，Gates Corporation | 类型：厂商展区/技术分享
- 方向归属：主 [底座-冷却]
- 核心主张：现行 1–2 m/s（3–6 ft/s）流速上限来自住宅/设施管道经验而非液冷实测；橡胶软管在其他流体动力行业可超过 9 m/s（30 ft/s）；目标是"最优流速"而非最高（p2, p4, p8）。
- 关键数据：
  - 现行限制约 3–6 ft/s（1–2 m/s）；其他行业软管流速部分 >30 ft/s（9 m/s）[p2，自报]
  - 热增益曲线：9 m/s 下 6 in 管约 1770 W，3/16 in 约 50 W [看图 p5，估读]
  - 测试台含老化条件、流体理化分析（pH、FTIR、黏度、缓蚀剂浓度）；文字层未给出实测结果数值 [p6-7]
- 提到的公司/客户/产品/标准：Gates Corporation（Hall 3 Booth D32）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（流速—热增益曲线）

### P223 A-Practical-Infrastructure-Solution-for-Component-and-Device-Level-SSD-Qualification-in-Single-Phase-Immersion-Cooling
- 讲者/机构：Jason Brand、Justin Boldrini，Thermal Validation Engineer, Solidigm | 类型：技术分享
- 方向归属：主 [底座-冷却]（浸没）；次 [存储]
- 核心主张：SSD 热化学老化评估需要专用 SSD-only 浸没平台，而不是大型部署槽：部署环境追求性能与散热效率，老化测试需要受控 BOM、高温和小流体体积（p5-6）。
- 关键数据：
  - 老化阶段流体温度 >60 °C，通电空闲；读出阶段 30–40 °C 做功能/性能测试 [p3]
  - 平台需求：最高约 80 °C 运行；12×4 SSD 阵列 [p6-7]；六项需求均标 "Achieved" [p11，自报]
  - 流程：浸没前 BOM/FMEA/基线 → 老化+周期读出+流体监测 → 浸没后性能/热验证/流体分析 → 拆解截面检查 PCB/走线/过孔 [p2]
- 提到的公司/客户/产品/标准：Solidigm、OCP Thermochemical Reliability Workstream
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（SSD 浸没平台的介电回路与冷水回路架构）

### P224 Advancing-Immersion-Cooling-Safety-From-Fluid-Qualification-to-System-Compliance
- 讲者/机构：Mark Olson、Lizzy Fernando，UL Solutions | 类型：标准进展
- 方向归属：主 [底座-冷却]（浸没安全标准）
- 核心主张：IEC 62368-1 只管电气安全，对长期材料兼容性指导有限（仅 60 天系统级兼容测试）；UL 2417 为浸没液提供可重复的认证基线，后续出兼容性 OOI（p4, p6）。
- 关键数据：
  - IEC 62368-1 第 4 版 2023-05-26 发布；浸没液称 "Insulating Liquids" [p4]
  - UL 2417 于 2025-01-14 发布；必做测试：自燃温度 ASTM E659 ≥300 °C；闪点 ASTM D93 A ≥135 °C；击穿电压 ASTM D1816 ≥6 kV/mm [p6-7]
  - 即将发布 UL 2417B（水/水-乙二醇 D2C 冷却液，注重性能不含兼容性）[p9]；本年发布 UL 4303（D2C 软管与管件，含 working/proof/burst 压力、UL 94 阻燃等）[p10]
  - OCP Industry Liaison 例会每月第 3 个周四 [p11]
- 提到的公司/客户/产品/标准：UL Solutions、IEC 62368-1、UL 2417/2417B/4303、UL Product iQ、ASTM 系列
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（UL 2417 必做测试与阈值表）；p5（从流体认证到系统合规的路径）

### P225 Before-the-Fluid-How-Pre-Immersion-Cleaning-Chemistry-Shapes-Long-Term-Electronic-Reliability
- 讲者/机构：Chelsea Jewell，Application Lab Manager, KYZEN | 类型：技术分享
- 方向归属：主 [底座-冷却]（浸没可靠性）
- 核心主张：浸没前清洗是独立的工艺要求：化学品匹配与漂洗完整性须规定并验证；化学品不匹配、漂洗不良、浸没后 IPA 返工并不比不清洗更好；介电液缺少离子测试方法（p11-12）。
- 关键数据（实验，SAC305/ROL0 免清洗助焊剂，5 种预处理条件，168 h 暴露，EID 电阻监测）：
  - 电阻达到 1×10¹⁰ Ω 所需小时（卡1 新液/卡2 已加热旧液）：A As Built 30.5/21.8；B Robustly Cleaned 7.3/3.7；C Chemistry Mismatched 32.6/14.5；D Poorly Rinsed 16.9/31.0；E IPA Rework 47.4/23.8 [p7-8]
  - 只有彻底清洗的板在两张卡上都快速稳定 [p11]
  - 局部 C3 提取离子色谱：A 与 E 检出硫酸根/琥珀酸/己二酸，总量 2.22 与 2.70 µg/in²；B/C/D 未检出 [p9]
  - GCMS 在 168 h 所有条件与洁净对照一致；LCMS 仅在 19.1 min 有一个所有暴露组共有的小峰 [p10]
- 提到的公司/客户/产品/标准：KYZEN、Micron Technology（有机化学实验室，2026 年 9 月）、OCP CE Immersion Fluids & Cleaning Guidelines
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（各条件达到 1e10 Ω 的小时数）；p6（168 h 电阻曲线）

### P226 Community-Update-Immersion-Fluids-Workstreams-Update
- 讲者/机构：Fluids Technical Committee：Kris Fletcher（Analog Devices）、Vanja Boyd（ExxonMobil）、JanElsa Carty（Shell）、Peter Cooper（Promersion）、Spencer Kerns（Chevron Phillips Chemical）、Alex McManis（ENEOS）、Roma Suris（独立）| 类型：标准进展
- 方向归属：主 [底座-冷却]（浸没液）
- 核心主张：流体委员会下设清洗指南、氧化方法、生命周期管理、流体规范四个工作组；Immersion Requirements 将更新到 Rev 3，之后才开始 Base Specification for Immersion Fluids（p2, p13）。
- 关键数据：
  - Rev 3 要点：新增 4.1 节定义四类流体（烃类、酯类、氟化物、混合物）；氟化物细分 PFC/PFPE/FK/HFE/HFO；介电测试至少 4 个数据点、室温 ≤25 °C；需在 20–60 GHz 做一次测试，推荐 20/40/60 GHz 覆盖 PCIe Gen5/6 到 224G PAM4（VNA+谐振腔或同轴探头）[p14]
  - 单相上限温度 70 °C，两相为沸点 −10 °C [p14，图中标注]
  - 目前 OCP Marketplace 按 Requirements v2.1 接收流体 [p15]
  - 生命周期白皮书 "Single- and Two-Phase Immersion Fluid: End-of-Life Options (v1.0)" 已完成待社区评审；下一步做流体循环与 LCA [p11]
  - 氧化方法白皮书处于编辑阶段，目标 Q4/Q1 '27 征求社区意见；TAN 与介电损耗因数 DDF 可能与流体/硬件寿命相关，征集老化流体 TAN/DDF 数据 [p8-9]
  - 清洗溶剂：酒精类吸水/导电/易燃，去离子水不推荐（无介电性、留腐蚀性残留）[p5]
- 提到的公司/客户/产品/标准：OCP Marketplace、Requirements Rev 2.1（2023）/Rev 3（2026 修订）、PCIe Gen5/6、224G PAM4
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（Rev 3 三项要点）；p11（流体价值保全层级）

### P227 Community-Update-Immersion-IT-Equipment-ITE-Workstreams-Update
- 讲者/机构：Austin Hipes（UNICOM Engineering），Immersion-ITE Technical Committee Chair | 类型：标准进展
- 方向归属：主 [底座-冷却]（浸没 IT 设备）；次 [底座-机架/机械]
- 核心主张：ITE Design Guidelines 自 2020 年 12 月后未更新，现作 2.0x 大修（第 1-4 节收尾评审，第 5 节编写中）；新项目做浸没线缆与部件验证（p3-5）。
- 关键数据：
  - 高 TDP（>500 W）硅片的热优化；首个定向流散热器参考设计已发布（Targeted Flow Efficiency Heat Sink v1.0）[p6]
  - 热性能测试规范（流体、散热器、TIM 的参考测试平台）已开始撰写 [p7]
  - 信号完整性：DDR/PCIe/以太网/光的裕量测试总体良好但部分场景裕量缩小，DDR5 串扰可降低；下一步聚焦 >32 GHz（例如 224G PAM4 @ 56 GHz）[p8]
  - 新增空气与浸没环境下系统 EMI 对比数据 [p9]
- 提到的公司/客户/产品/标准：UNICOM Engineering、ASMC、Lubrizol、Wieland、Intel、TE
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（三个工作组概览）

### P230 Immersion-Solutions-Integrating-Cooling-Power-Hardware-and-Economics
- 讲者/机构：OCP Immersion Solutions 工作组：Amy Short（Denvr Dataworks，主席）、Andy Young（Asperitas）、Kevin Gero（Murata）、Oriol Chavanel（Hypertec）、Mick Jones（Vertiv）、Nick Beardsley（GRC）、Edi Roytman（Marvell）、Khaled Morsy（BVPI）、Peter Cooper（Promersion）| 类型：标准进展
- 方向归属：主 [底座-冷却]；次 [底座-电力]
- 核心主张：五个工作组（TCO、硬件管理、电力分配、FMEA、浸没要求）共同服务浸没规模部署（p2）。
- 关键数据：
  - TCO 工具 v1.31，含击穿托管费率与开销/损耗可视化，下一步加入 DC 电力架构 [p3]
  - 硬件管理：Liquid Cooling Baseline Profile 已建立；CDU mockup 与 Interop Profile 完成；agentic AI helper 概念验证完成 [p4]
  - 电力分配：新发布 ORv3 浸没系统 Base Spec（电源架、PSU、母排、连接器、槽体接口）；待问：服务器继续 50V 还是 DC 800V 输入；电容架在 150 kW 以下是否必要 [p5, p10]
  - FMEA：聚焦点火风险，计划发布白皮书 [p6]
  - Requirements v2.1 演进中，当前焦点为设备与设施安全措施 [p7]
- 提到的公司/客户/产品/标准：ORv3、Infineon（800V，p10 称"seems doing it"）、OCP Marketplace
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（五个工作组关系）

### P231 Material-Compatibility-and-Long-Term-Hardware-Integrity-of-Enterprise-SSDs-in-Two-Phase-Immersion-Cooling
- 讲者/机构：Youngnam Kim，Samsung Electronics（伙伴：Chemours Opteon 2P50、Liquid Stack 槽体、PKI 运维）| 类型：技术分享
- 方向归属：主 [底座-冷却]（两相浸没）；次 [存储]
- 核心主张：两相浸没大幅降低热机械应力，剩余风险是清洁度，进槽前以 PCBA 清洗控制；建议把 OCP 材料测试指南扩展到产品级并加入 PCBA 清洗规范（p10）。
- 关键数据：
  - 环境：Samsung Gen4/Gen5 企业级 SSD，Liquid Stack 48U 两相槽，Opteon 2P50，>15,000 小时（进行中），JESD219 负载下 0% 失效 [p3，自报，现网/长期实验]
  - 材料相容性判据：质量变化 <2%；Samsung 规范为 Soxhlet 72 h + 80 ℃ 浸泡 336 h；OCP 指南为 Soxhlet 48 h [p5]
  - 结果：电容、标签、EMC、PCB、TIM（Soxhlet，49 ℃，72 h）均 <2% 通过 [p6]；80 ℃ 浸泡 2 周与 4 周，电容/标签/EMC/底填/PCB/锡膏/TIM/产品均 <2% 通过 [p7]
  - 污染失效机理：助焊剂残留与离子迁入冷却液，在沸腾位点沉积于高功率封装，枝晶桥接 BGA 焊球短路烧毁 [p8]；清洗流程为水洗→DI 漂洗→受控干燥，按 IPC-TM-650 验证 [p8]
- 提到的公司/客户/产品/标准：Samsung、Chemours Opteon 2P50、Liquid Stack、PKI、JESD219、IPC-TM-650
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（空气 vs 两相浸没 SSD 温度曲线）；p8（污染致枝晶短路机理）

### P232 Moving-Beyond-Interchangeability-Characterizing-Esters-among-Coolants-for-Immersion
- 讲者/机构：Stefan Maier（Evonik）、Beau Van Vaerenbergh（Oleon）、Valentina Serra-Holm（Perstorp）| 类型：技术分享
- 方向归属：主 [底座-冷却]（浸没液）
- 核心主张：浸没冷却液并非可互换，应以化学类别为标准化基础；酯类可与 Group IV 烃类散热性能相当且闪点高，应建立针对"工程酯"的标准化框架并借鉴变压器行业 40 年经验（p2, p12-13）。
- 关键数据：
  - 对比：Group IV 烃类 闪点 155 °C、40 °C 运动黏度 5.2 cSt、FOM1 62；Ester A 160 °C、4.5 cSt、FOM1 65 [p4，实验]
  - FOM1 与温度在 4–30 cSt 黏度范围内相关性良好（主动循环台：35 L，最大 4 L/min）[p5]
  - 酯在 GHz 相对介电常数接近烃类 [p6]；击穿电压与相对饱和度相关，而非绝对含水量 [p7]
  - Ester B 在最恶劣湿度下 6 天，含水稳定于约 0.11–0.12 wt%，酸值不变 [p8，实验]
  - 材料相容性按 OCP 指南（80 °C，336 h）：Ester C 与 PVC、粘合剂 A1 兼容性优于 Group IV（柱状图 |ΔV|%，无具体数值读出）[p9]
- 提到的公司/客户/产品/标准：Evonik、Oleon、Perstorp、ASTM D93、OCP Material Compatibility guidelines
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（已证明项与待处理项总表）

### P233 OCP-Immersion-Project-Scaling-Open-Collaboration-for-Immersion-Cooling-Adoption
- 讲者/机构：Rolf Brink（Promersion，共同主席）、Jessica Gullbrand（Eaton，共同主席）、Allison Boen（Alcatex）、Rachel Bielstein（Baltimore Aircoil）、Gemma Reeves（Alfa Laval）| 类型：标准进展/社区进展
- 方向归属：主 [底座-冷却]（浸没生态）；次 [推理/算力/经济性]
- 核心主张：① 浸没是 OCP 最大项目社区但 IT OEM 尚未规模出货浸没原生产品，原因是"生态系统在耗尽保持现有架构的选项后才接受改变架构"：冷板是被物理墙推动，浸没是被经济拉动，渐进且不均匀（p6-8）。② 回避成本累积在可靠性、重量、机箱空间、可维护性与下一种方法的成熟度五个账户（p11-12）。
- 关键数据：
  - 全球 DC 市场（Promersion）：CAGR 2025-2035 15.7%，增速 2025 29.0% 降至 2035 8.9% [看图 p3，预测]
  - 液冷市场：冷板 2035 约 \$57B，浸没约 \$55B；浸没 2028 年增速 250% [看图 p4，Promersion 预测，估读]
  - 顶级加速器 TDP 中冷板占比从 <10% 到 >90% 约 24 个月 [看图 p7]
  - 白皮书 Thermal Boundaries in AI Infrastructure（Rolf Brink、Mohan J. Kumar、Steve Mills、Kelley Mullick）[p5-6]
  - 相对 MTBF 对比空气：模型下限 3.4–5x；3,000+ 浸没服务器 30 个月的队列观察最高 12x（OCP EMEA 2025）；Natick 氮气环境失效为陆上的 1/8 [p13，引用]
  - 管路可靠性模型：全冷板托盘 1.45x（设计点）→ 0.96x（全管路）→ 0.72x（按现场耦合率）[p12，模型]；机架功率 250 kW → 600 kW（发货 → 已宣布）[p15]；200 MW AI 案例浸没年总成本最低 [p15，自报]
  - 路线图：2025–2027 标准化与互操作，2027–2028 产业化，2029–2030 规模部署 [p16]
  - 社区：1,342 名活跃成员，同比 +23.9%；15 个并行工作组、4 个技术委员会 [p17, p32]；2026 年新贡献：服务器部件浸没材料兼容性测试、Thermal Boundaries（已发布）；浸没液安全处理指南、高速互连 SI、开源材料兼容性数据库（审批中）[p25]
- 提到的公司/客户/产品/标准：Promersion、Eaton、Alfa Laval、Natick、Intel、ExxonMobil、Micron、BAC、Samsung、Solidigm、Denvr、Unicom 等议程演讲者 [p2]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（冷板占比拐点曲线）；p13（浸没可靠性对比 headline）

### P234 OCP-SwRI-Collaboration-Data-Center-Immersion-Fluids-Consortium
- 讲者/机构：Peter Morgan，Sr. Program Manager, Southwest Research Institute (SwRI) | 类型：厂商/机构展示
- 方向归属：主 [底座-冷却]（浸没液）
- 核心主张：行业缺乏信号完整性、材料兼容性、安全、老化、传热的标准化浸没鉴定方法，SwRI 提议成立 Data Center Immersion Fluids (DCIF) 联盟作为与 OCP 对齐的独立测试机构（p4-5, p8）。
- 关键数据：
  - 制冷占数据中心耗电 35–50%；耗电预计到 2028 年增长 12%（引用 IEA 2025）[p2]
  - 冷却演进：风冷至约 60 kW/机架、冷板/后门约 50–100 kW、浸没 >200 kW [p3，自报，对应关系以图为准存疑]
  - 联盟：4 年，起步需 \$1.0 M/年；会费 油品/添加剂公司 \$100,000/年、大型 IT 公司 \$75,000、部件公司 \$50,000、测试公司 \$250,000；声称 ROI 约 10x（油/添加剂）、13x（大型 IT）、20x（部件）[p13，自报]
  - SwRI 自筹研究已投入 \$1.5 M；信号完整性项目评估冷却液介电性质至接近 40 GHz [p11, p13]
  - 30% 经费专用于 OCP 社区议题；OCP 无投票权、发布须经 IP 条款批准 [p12]
- 提到的公司/客户/产品/标准：SwRI、OCP、ASTM、ISO、UL、ASHRAE、IEA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（SwRI 作为中立召集人的结构）

### P239 03_A system approach to AI infrastructure presented by Rittal
- 讲者/机构：Andy Gill，CSO, HPC Systems（Rittal）| 类型：厂商/主题演讲
- 方向归属：主 [底座-机架/机械]；次 [底座-电力]、[底座-冷却]
- 核心主张：① AI 工厂只有一个产出——token，约束已从硅转到基础设施，用首 token 时间、每瓦 token、全生命周期 token 衡量（p2）。② 标准化底座（ORv3/ORW）、模块化其余部分：IT、电源（800V DC sidecar、RiLineX 母排、BBU）、冷却（机架内/行内 CDU、RDHx）各自独立扩展（p5）。
- 关键数据：
  - 机架功率阶梯：<30 kW 传统风冷；140 kW 为 48 VDC 机架内转换的实际上限；500+ kW 为 800 VDC sidecar；约 1 MW 下一代 [p4，自报]
  - 100 MW 站点示意：每月等待供电/冷却损失 72 GWh；PUE 从 1.3 降到 1.2 可在同一 100 MW 并网下多 +6 MW IT；每降 0.1 PUE 约多 8% IT 容量 [p3-4，示意性，自报]
  - 2030 年基于 OCP 的机架市场份额预计 70% [p6，引用 Omdia 2025]
  - sidecar 额定最高 2 MW；RiLineX：直流额定 1500 V、交流 1000 V，65 kA 短路耐受，IP 2XB 可升 IP 4X，IEC 61439 与 UL 508A 认证 [p8-9，自报]
  - 冷却：机架内 CDU 250 kW（4K ATD）、行内 CDU 1.25 MW，成组 1.5 MW 至 13.5 MW @ N+1，后门 80 kW [p11-12，自报；与具体产品对应关系存疑]
- 提到的公司/客户/产品/标准：Rittal、Open Rack V3、Deschutes、Diablo 400、DCF LVDC 白皮书、Omdia
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（三种供电架构演进：机架内转换→sidecar→800 VDC 建筑级转换）

### P241 05_Advancing Open AI Infrastructure Management through Community and Ecos
- 讲者/机构：Hancock Chang（Director）、James Shie（Manager），Solution Enabling Division, MiTAC Computing | 类型：厂商展示
- 方向归属：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：开源固件（OpenBMC/OPF）对比专有固件在透明度、生命周期、互操作、成本、合规和锁定上更有优势；Intel 与 AMD 平台固件栈互不统一，需要 OCP openSFI/UPCI 规范走向统一（看图 p3、p6）。
- 关键数据：文字层几乎为空，以下均为看图：MiTAC 产品清单——Intel BHS：R25206G、R25136G（已上游 Coreboot）；AMD EPYC 9004/9005/9006 SP5：B8261、S8050、B8056、Capri2/Capri3、G4826Z5，SP7：M2810Z6 [看图 p6]；G4826Z5 搭载 Mi355、B8056 为带 RMC 功能的 OpenBMC 管理节点 [p8 文字]；基础设施管理平面覆盖 System/Rack/POD 的七类功能 [看图 p2]
- 提到的公司/客户/产品/标准：MiTAC、AMD MI355、EPYC、Intel BHS、OpenBMC、Coreboot、AGESA/openSIL、OCP openSFI/UPCI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（Intel/AMD 开放平台固件栈）

### P245 09_Beyond Megawatts- Engineering Liquid Cooling for AI at Scale presented
- 讲者/机构：Ning Liu，Product Manager，Envicool（英维克）| 类型：厂商展示
- 方向归属：主 [底座-冷却]
- 核心主张：随芯片热流密度上升，冷却从单相冷板演进到微通道、射流冲击、两相冷板，基础设施（泵、CDU、设施冷却）必须同步；集成商角色从选型转为系统验证；长期可靠性取决于制造一致性与生命周期控制（看图 p4, p6, p8）。
- 关键数据（全为看图，文字层为空）：
  - 芯片 TDP：2022 400 W、2024 700 W、2025 1,000 W、2026 1,400 W、2027 2,300 W、2028-2030 3,100 W；机架功率：50/120/140/220/300 kW 与 1,000+ kW（来源标注 NVIDIA "DSX AI Factory Platform"）[看图 p3]
  - CDU 散热能力 300 → 1500 → 2500 kW；水力能力 30/60/90 psi 对应 1.0/1.5/2.0 LPM/kW [看图 p5，自报]
  - Envicool：2005 年成立，9000+ 员工，30% 研发 [看图 p2]
- 提到的公司/客户/产品/标准：Envicool Coolinside™、NVIDIA DSX
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（TDP 与机架功率趋势）；p5（CDU 容量与水力阶梯）

### P251 15_Cooling the AI Revolution Scaling Performance Through Advanced Liquid
- 讲者/机构：Auras Liquid Cooling Solutions（讲者姓名未见）| 类型：厂商展示
- 方向归属：主 [底座-冷却]
- 核心主张：智能 CDU 主动调节温度与流量、以预测性流量降低 LLM 负载下降频风险，节省的冷却功耗回流给 GPU 以提高 tokens per watt（p2-3）。
- 关键数据：冷板支持 45 ℃ 入口温水冷却，称适宜气候下可无冷机运行；铜皮削翅片+金刚石-铜基底（p6，自报）；CDU 功能：免工具模块化、热插拔、干断快接、N+1 泵冗余（p4）；无具体性能数字
- 提到的公司/客户/产品/标准：Auras、W45 Warm Water DLC、BMS/DCIM 遥测集成
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（微通道冷板与 45 ℃ 进水）

### P258 22_Forging an Open Control Plane for the AI Era presented by Lattice
- 讲者/机构：Kelly Bryant（VP Firmware and Solutions Strategy）、Mamta Gupta（VP Compute & Communications Segments），Lattice Semiconductor | 类型：厂商/主题演讲
- 方向归属：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：AI 机架级管理从"管服务器"变成"控系统"，需要开放控制平面把管理与编排、平台固件、信任与安全、开放接口连接起来；要求安全（OS 之下的信任、持续证明）、弹性（不下线更新与恢复）、高效（电/热/健康遥测作为控制回路）（p3, p5-6）。
- 关键数据：定性为主；引用的规模背景：100,000+ 加速器作为单一训练集群，1 MW/机架 [p2，自报，口径未注明]
- 提到的公司/客户/产品/标准：Lattice Semiconductor、BMC、硬件信任根
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（开放控制平面四层）

### P259 23_From Blueprint to Revenue Engineering and Executing AI Cloud Gigafacto
- 讲者/机构：面板：Chris Marriott（NVIDIA）、John Donovan（Lenovo）、Denis Skrinnikoff（IREN，CTO）、Wil Wellington（Lenovo，主持/Global Director AI Data Center Services）| 类型：面板（Executive）
- 方向归属：主 [推理/算力/经济性]
- 核心主张：Lenovo AI Cloud Gigafactory with NVIDIA 以"一个生命周期、一个责任方"缩短从 AI 需求到首 token 的时间：Concept、Build、Deploy、Support & Optimize（p3）。
- 关键数据：幻灯无技术数字。
- 提到的公司/客户/产品/标准：Lenovo、NVIDIA、IREN；Lenovo Booth D35
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（四阶段生命周期）

### P260 24_From Chip to Grid Scaling Holistic AI Data Center Co-Design Through Op
- 讲者/机构：Tom Garvens（VP Data Center Technology & Systems，内容显示为 Google）、Amber Huffman（Principal Engineer，OCP Board of Directors）| 类型：主题演讲
- 方向归属：主 [底座-电力]；次 [底座-冷却]、[推理/算力/经济性]
- 核心主张：① AI 负载（训练功率摆动、斜坡率、振荡）已成为电网问题，需要从硅到设施按时间尺度分层缓解（p7, p9）。② 从 LVDC sidecar 过渡到原生 LVDC（集中式 SST+BESS），并用 OCP 在"数月而非数年"内对齐规范（p15-18, p20）。
- 关键数据：
  - 美国数据中心用电占比 2023 年 4.4%（176 TWh），2028 情景 6.7–12%（325–580 TWh）[p6，引用 LBNL 2024/EIA]
  - 新增电网要求：FinGrid 90% 在 1 s 内；ERCOT 90% 在 2 s 内；AESO 100% 在 1.0–10.0 s（可配置）；Energinet 80% 5 s、90% 20 s、95% 30 s [p8，引用]
  - 2024 年约 1,500 MW 负荷一次性掉线；Feb 2026 首稿、Jun 2026 关键项对齐、Sep 2026 v1.0 生效；穿越电压骤降 90% 负载 2 s 内恢复 [p20]
  - 原生 LVDC 收益：占地致密化 20–30%，减少 9,000 安装工时，芯片到电网效率 >1%（三级转换变一级）；均为内部估计，对比现有 AC 基线 [p18]
  - 缓解层次：硅设计特性、分层软件控制、工作负载/弹性、CBU/近机架超级电容（µs–ms）、设施级 BESS（长时）[p9]
  - 需求响应：Google 已在多家美国公用事业合同中整合 1 GW 需求响应容量；2026-03-19 公布 [p12]
  - Mt Diablo ±400 VDC 电源机架；SST MV AC→800 VDC v0.3；板上电源新工作组 2026 Q4 [看图 p21]
  - Gemini：>22B tokens/min（Feb 10B → Apr 16B → Jul 22B，API 直接使用）[p3，自报]；TPU：Ironwood（2025）9k+ 芯片 [p5]
  - Project Deschutes 1.0（第五代开放 CDU 规范）、Project Brazos、Open Data Center 1.0（7 个标准空间，12–24 MW 模块）[p22]
  - 清洁备用电源要求：<10% 柴油 CO₂、<10 s 满功率 [p24]
- 提到的公司/客户/产品/标准：Google、TPU（v1–Ironwood、TPU 8t/8i）、Gemini、Mt Diablo、Deschutes、Brazos、FinGrid、ERCOT、AESO、Energinet
- 首次/记录/SOTA 声明：无（自称里程碑：2026-03-19 公布需求响应 1 GW）
- 推荐配图页：p9（按时间尺度的缓解分层）；p17（LVDC 三阶段演进）

### P262 26_From Dirt to Tokens Building AI Infrastructure as an Integrated System
- 讲者/机构：Chris Butler（Expected CTO and Strategy Officer）、Rob Campbell（Expected Chief Commercial Officer），Axiom（Flex 拟分拆的 Cloud and Power Infrastructure 业务；含 EPC Power 技术，p16）| 类型：厂商/主题演讲
- 方向归属：主 [底座-电力]；次 [底座-冷却]
- 核心主张：把电力—计算—冷却作为集成系统设计：集中式 800V（BESS、MW 级数字整流器、34.5 kV–800 V SST 路线、MV UPS）+ 模块化预制，把数据中心当作产品交付（p3, p12, p14）。
- 关键数据（均为 Axiom 自分析，多处标注"illustrative only"）：
  - 能效到机架：今天约 92%（UPS 方案，至 1.6 MW 电源机架）→ 3.5 MW 整流器约 97% → 未来带储能的 grid-forming SST 约 98%+ [p5-6]
  - 单系统最高扩展到 6 MW，面向 >75 MW 数据中心的电网规范 [p7]
  - 芯片级冷却：单相直达芯片冷板支持 3 kW+ TDP；最高 47% 冷却节省；40 MW 北弗吉尼亚案例每年节省 \$2.5M 冷却成本、4 亿升水 [p8-10]
  - 部署速度最高快 50% [看图 p11]
- 提到的公司/客户/产品/标准：Axiom、Flex、EPC Power、Axiom 微对流/微通道/混合冷板
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（800VDC 架构从 UPS 到整流器到 SST，效率 92%→97%→98%+）

### P266 30_From Switches to Systems presented by Jabil
- 讲者/机构：Abhinav Sharma（Arista）、Matt McGuff（Jabil）| 类型：厂商/主题演讲
- 方向归属：主 [Out 后端网络]（交换机整机与工厂集成）；次 [底座-机架/机械]
- 核心主张：网络机架已成为基础设施：从 TOR 集成、风冷、100 根光纤、51.2T，走向独立网络机架、液冷、1000 根光纤、102.4T 及以上；Arista+Jabil 的差异化是完整性与共同责任，而非多级交接（p2, p7）。
- 关键数据：
  - 今天 → 未来：51.2T → 102.4T 及以上；数百根光纤 → 数千根光纤；风冷 → 液冷；TOR 集成 → 专用网络机架 [p2，自报]
  - 工厂：10 项机架集成优先事项分四主题（物理系统、测试与维修、智能工厂与数据、规模与人员），含 L11、FAT、CDU/QD/泄漏检测、ORv3 48V；规模目标"每周数百个机架" [p4]
  - 挑战：交换机冷板充氮存放的氮气衰减率不一；未定义带冷却液和氮气存放的行为；光纤灰尘导致插入损耗，清洁协议和 100% 清洁是否必要尚未定义；标准 BICSI 培训对工厂规模过深过贵 [p5]
  - 能力栈含 Arista EOS/SONiC 选项、Mikros 热系统 [p7]
- 提到的公司/客户/产品/标准：Arista、Jabil、EOS、SONiC、Mikros、ORv3、BICSI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（今天与未来网络机架对比）；p4（十项工厂优先事项）

### P272 39_nVent RDHX cooling for AMD Helios™ presented by nVent
- 讲者/机构：Sam Dore，Product Manager – Liquid Cooling，nVent Data Center Solutions | 类型：厂商展示
- 方向归属：主 [底座-冷却]；次 [底座-机架/机械]
- 核心主张：冷板方案只带走约 60–90% 热量，剩余热进入空气，机架尾部热交换器（RDHX）在源头捕获以实现"房间中性"；Helios 机架需要双 RDHX（p2, p6-7）。
- 关键数据：
  - 风冷房间极限约 10–15 kW/机架，使用热通道封闭 20–40 kW；新 AI 机架 >250 kW [p2，自报]
  - AMD Helios 机架功率约 246–250 kW，89%/11% 液/气分配，约 27.5 kW 排向空气 [p2, p6]
  - nVent 标准 RDHX：厚度仅 252 mm，最高 5,885 CFM（10,000 m³/h），14 °C 水最大 68 kW；Helios 双 RDHX 可排热 25–45 kW，48 VDC，2:1 软管仅需一个设施歧管连接，2" Danfoss FD83 [p4, p6-8，自报]
  - 接口：Modbus RTU/TCP、Redfish、SNMP、BACnet [p8]
  - 呼吁：DC 供电 RDHx 的母排连接、软管套件标准化、OCP 机架上 RDHx 的扩展框架 [p9]
- 提到的公司/客户/产品/标准：nVent、AMD Helios、Danfoss、OCP Rack
- 首次/记录/SOTA 声明：自称"市场上最薄的 RDHX（252 mm）"[p4]
- 推荐配图页：p3（RDHX 数据中心拓扑）

### P274 41_Open Rack, Liquid Cooling, Now What Operationalizing the Next Gen Data
- 讲者/机构：Joseph "JBK" Knight，Chief Technologist – Service Providers，HPE | 类型：主题演讲
- 方向归属：主 [运维/可靠性/遥测]
- 核心主张：OCP 解决了基础设施（机架电源、液冷、DC-MHS）但运维缺口仍在：基础设施与服务器如何通信、发现、电源时序、遥测合成；行业应从服务器中心转向机架中心运维，机架成为运维单元、基础设施自描述（p4-5）。
- 关键数据：无数字。HPE 以 iLO 为基础，APM 与 PCIM 把管理扩展到机架电源/热/液冷；目标是在 ProLiant 与 HPC/AI、Open Rack 与 EIA 19"、DC-MHS 与 MGX 之间提供一致运维体验 [p6]
- 提到的公司/客户/产品/标准：HPE、iLO、APM、PCIM、DC-MHS、MGX、Open Rack（Booth D34）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（机架级运维所需能力）

### P276 44_Powering the AI Revolution Navigating the 800V-to-Chip Frontier presen
- 讲者/机构：Teng Long，Professor，LITEON-EPIC，University of Cambridge | 类型：技术分享
- 方向归属：主 [底座-电力]
- 核心主张：800V DC 机架到芯片需要多级高效变换，趋势是由两托盘三级向单托盘两级或在芯片端用 IVR 的单级演进；金刚石基板加微通道改善封装散热（p10, p12）。
- 关键数据：
  - 800–50V DC-DC 全砖：10 kW，功率密度 1522 W/in³，峰值效率 98.7%（90 A），满载 98.1%；2027 年 12 kW [p4，自报]
  - 800–50V 半砖：6 kW，1746 W/in³，峰值 98.2%（55 A），满载 97.8% [p5，自报]
  - 50V→12V 首级 LLC：1500 W，7762 W/in³，54V 输入峰值 97.9%（500 W），满载 96.9% [p7]；→6V：1000 W，4587 W/in³，峰值 97.9%（300 W），满载 96.6% [p8]
  - 50–0.8V 单级 VRM：240 A 单模块，4 并联 800 A，电流密度 1.28 A/mm²，峰值 91.4%，满载 87% [p9]
  - 金刚石基板：热阻 0.16 °C/W（单面）、0.1 °C/W（双面），隔离 >3 kV（仪器上限）、漏电 7.5 µA [p12]
- 提到的公司/客户/产品/标准：LITEON、Cambridge、OCP 合规与资格认证（p7）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（800V 到芯片的三种架构趋势）

### P277 45_Rethinking CPU Performance for the Agentic AI Era presented by Arm
- 讲者/机构：Ravi Malhotra，Arm | 类型：厂商/主题演讲
- 方向归属：主 [推理/算力/经济性]
- 核心主张：Agentic AI 带来五类 CPU 负载特征，应把现有 agent 基准冻结轨迹并回放为可复现的 CPU 工作负载，从每核性能与每机架吞吐两个维度评估（p2, p7-8）。
- 关键数据：
  - Arm AGI CPU 对 AMD EPYC Turin 的 Performance/Rack：MySQL 1.43x、NGINX 1.95x、Terminal-Bench 1.93x、SWE-bench 2.00x、Milvus 1.54x、vLLM 1.88x、fastText 3.19x [p11，引用 Signal65 第三方测试，自报厂商口径]
  - AGI CPU：第 3 代 Neoverse 核、每核内存带宽 2x、200–400 W，可做 1U 2N 风冷或 1U 8N 液冷，机架密度最高 2x [p10，自报]
  - 负载表为综合估计，非 CPU 基准实测 [p4]
- 提到的公司/客户/产品/标准：Arm AGI CPU、AMD EPYC Turin、Signal65、Terminal-Bench、SWE-bench、tau-bench 等；产品如 Claude Code、Codex、GitHub Copilot 作为应用示例 [p6]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（Performance/Rack 对比柱状图）

### P280 49_Scaling Direct Current in Data Centers From Proven Industrial Concepts
- 讲者/机构：Dr. Martin Wetter，Executive Vice President Power Reliability，Phoenix Contact（德国）| 类型：主题演讲
- 方向归属：主 [底座-电力]
- 核心主张：工业直流电网已有十余年国家资助研究和自建工厂实践，其经验可用于数据中心；规格种类繁多（±350/700 V 工业 vs ±400/800 V 数据中心）拖慢采用，OCP 是定义用例与完整生态的合适社区（p4, p31-32）。
- 关键数据：
  - 机架功率：约 2020 年 10 kW → 2026 年约 150 kW，预测 2030 年约 1,000 kW；"进一步提升只能靠 HVDC" [看图 p29，估读]
  - 自建 Blomberg 工厂：700 V DC 母线，700 kW 双向 AC/DC，1,500 kWp 光伏+110 kWp DC/DC 光伏，300 kWh 电池，EV 充电 2×150 kW+8×60 kW 双向；18,500 m²、>400 工位、>35 m€ 投资 [p6-15]
  - 挑战与对策：短路耐受性（全面短路安全测试）、连接器拉弧（ArcZero 800V/20A 无弧 DC 连接器）、缺乏标准（VDE SPEC 90037）与 DC 就绪产品 [p18-25]
  - 使用时间线（估计）：工业 研究→试点→应用；数据中心更快进入应用 [看图 p30]
- 提到的公司/客户/产品/标准：Phoenix Contact（Expo Hall 1 Booth A13）、PLCnext、ArcZero、VDE SPEC 90037、ODCA（zvei）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p29（机架功率增长与 HVDC 门槛）

### P282 51_Spearheading a New Security Standard for Data Centers presented by Mar
- 讲者/机构：Cary Ussery（SVP/GM Multi-Market Business Group, Marvell）、Bryan Kelly（Hardware Security Architect, Microsoft Azure）、Mohan J. Kumar（Architect, Oracle Cloud）| 类型：标准进展（新工作组宣布）
- 方向归属：主 [安全]
- 核心主张：集中式 HSM 无法满足 AI 与机密计算规模的加密性能（每次加密都需网络往返），提议在每个计算节点集成 NIST FIPS 140-3 Level 3 的集成 HSM（Tessera），把 L3 边界延伸到计算托盘（p4-5, p7）。
- 关键数据：
  - 2026-10 发布 v0.5 草案，之后 v1.0；Marvell、Microsoft、Oracle 为创始成员，在 OCP Security 项目下 [p6, p9]
  - Tessera 对齐：Caliptra、OCP LOCK、DC-SCM、SPDM/TDISP、FIPS 140-3 L3；后量子就绪：ML-KEM/ECDHE、ML-DSA/ECDSA 混合 [p8]
  - 演示：Microsoft 展位 #C73、Marvell 展位 #B31 [p9]
- 提到的公司/客户/产品/标准：Marvell、Microsoft、Oracle、Tessera、Caliptra、OCP LOCK、DC-SCM、SPDM、TDISP
- 首次/记录/SOTA 声明：自称"今天宣布"的新 OCP 工作组与开放集成 HSM 标准 Tessera [p6-7]
- 推荐配图页：p8（Tessera 对齐的开放标准）

### P283 52_Standardization that Enables Innovation Building Deployment Confidence
- 讲者/机构：Sebastien Lafond，Senior Engineering Director, Data Centers, Danfoss Power Solutions | 类型：技术分享
- 方向归属：主 [底座-冷却]
- 核心主张：液冷技术已被证明，挑战在于生态系统能否重复交付同一结果；应"标准化期望的结果，而不是设计"，互换性只是起点（p2-3, p4, p8）。
- 关键数据：无数字。UQD（Universal Quick Disconnects）作为 OCP 项目案例：插头/插座尺寸、对接与面板间距离、压降/流体损失/循环、混合供应商验证；经验：应考虑标准化集成的浮动功能 [p5-6]；最佳实践五条：公布完整工况、标准化完整接口、每个交接点可测量清洁度、保留端到端证据链、"带来问题而非方案" [p11]
- 提到的公司/客户/产品/标准：Danfoss、OCP UQD 项目
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（四层标准化影响：Fit&Form/Function/Interaction/Lifecycle）

### P284 53_The AMI Vision for Open Building an Open Control Plane for the AI Data
- 讲者/机构：Munir Ahmad（Chief Compute Architect）、B Parthiban（CVP Boot FW）；页脚标 Lattice Semiconductor（标题含 AMI，二者关系材料未说明）| 类型：厂商/主题演讲
- 方向归属：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：AI 数据中心缺少"系统级控制层"：管理接口不等于有效控制，需要连接权限、拓扑、策略、状态、命令与证据的通用契约（p3, p5）。
- 关键数据：无数字。四个缺口：设备信任止于组件边界；平台差异随 ODM 与代际倍增；拓扑不可独立证明；启动与恢复专有、机架级 bring-up 权限未规定 [p3, p5]；四项架构能力：安全固件分发、可验证系统启动、证明条件控制、所有权/撤销/恢复 [p8]
- 提到的公司/客户/产品/标准：Redfish、DC-SCM、PLDM、SNMP、gRPC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（四个缺口）

### P285 54_The New Tokenomics How Data Infrastructure Increasingly Sets AI ROI pr
- 讲者/机构：Ace Stryker（Solidigm）、Steen Graham（Metrum AI）| 类型：厂商/技术分享
- 方向归属：主 [存储]；次 [推理/算力/经济性]
- 核心主张：每个 token 的经济性越来越由 GPU 之下的内存与存储决定；用 SSD 在检索、复用、搬运、共享、压缩五个环节降低 DRAM/GPU 重算开销（p4-5）。
- 关键数据（均为 Solidigm/Metrum AI 自报，其中 p9-p13 标 PRELIMINARY TESTING；p7 声明为独立结果，非叠加加速）：
  - DiskANN vs HNSW（1 亿向量 LAION 100M，Solidigm D7-PS1010）：内存 331 → 116 GB（-65%），QPS 131 → 165（+26%），Recall@10 99.2% 对 98.4% [p6]
  - 视频检索 QPS 2,071 → 2,371（+14%，1,024 查询线程）；赛季上下文重访首 token 时间 31 s → 2.8 s [p7]
  - KV cache + GPUDirect Storage：100K token 重复请求，中位端到端延迟 4.95 → 1.73 s，主机内存流量 9.41 → 1.85 GB/s [p9，两路径块大小不同]
  - 共享池 KV：4 副本轮询，99K token 提示，首 token 18.38 s/413 W → 2.20 s/119 W [p10]
  - 编码 agent（60 任务，并发 4）：D7-PS1010 首 token 2.05 s 对 GPU 内存 13.76 s（6.7x）；D5-P5336 3.10 s（4.4x）；内部基准未发表 [p11]
  - TurboQuant：4-bit 对 BF16 KV 压缩 3.8x，单个 122.88 TB D5-P5336 约 41K → 157K 个 30K token 会话；4-bit 响应等价 0.90 对照 0.90，3-bit 预设 0.62；解码代价 9%（存储边界）对 29%（GPU 内存）；恢复延迟 +9.6%、主机 CPU 2.5x [p13]
- 提到的公司/客户/产品/标准：Solidigm D7-PS1010、D5-P5336、Metrum AI、NVIDIA GPUDirect Storage、DiskANN、HNSW、TurboQuant
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（共享池 KV 首 token 对比）；p6（DiskANN vs HNSW）

### P288 57_Validation Challenges for Next-Generation AI Power Racks From 100kW to
- 讲者/机构：Chroma ATE（讲者姓名未见）| 类型：厂商展示
- 方向归属：主 [底座-电力]
- 核心主张：测试 900 kW–MW 级 HVDC 电源机架需要把冷却、现场供电不足、MW 设备控制与连接作为一个平台规划；用 Server Load Emulator（SLE）在计算托盘到位前复现真实服务器的功率行为并扩展到整机架（p5, p20-23）。
- 关键数据（自报）：
  - MW 实验室风量：电子负载 >13 台×4,000 CFM=52,000 CFM；AC 源 >12 台×2,080 CFM=24,960 CFM [p8]
  - 回馈式负载效率 >90%；混合式回馈负载稳态效率 >80%，峰值 ≥160% 负载，EDPP 10 kHz [p11-12]；回馈负载缺点：压摆率慢、纹波 150 mV；线性负载无能量回收 [p13]
  - 多负载同步：动态同步误差建议 <2 µs，支持 60+ 台、总吸收功率 ≥1.44 MW [p15-17]
  - SLE：1U，15 kW 水冷，80V/300A；负载变化 <20 µs；峰值 24 kW（160%）持续 200 ms；>30 台同步，>300 kW/机架 [p20-22]
- 提到的公司/客户/产品/标准：Chroma（63200A、62000D、63700H）、OCP 机架
- 首次/记录/SOTA 声明：无
- 推荐配图页：p22（SLE 从服务器到机架到集群的验证方法）

### P292 04_From Fleet to Firmware Bringing AI-Native Security to Open Hardware wi
- 讲者/机构：Andrés Lagar-Cavilla，Distinguished Engineer（内容为 Google：Mantis、Kythe、TPU，p6, p10-12）| 类型：展区分享
- 方向归属：主 [安全]
- 核心主张：对抗者已可全自动进攻，需要把防御 SDLC 自动化：对每个代码变更用与编码 agent 分离的安全 agent 做常开扫描，并在提交前 <5 分钟完成分诊与修复补丁（p2, p5, p12）。
- 关键数据（自报，Google 内部）：
  - Project Equilibrium：平均每月约 196 个高危缺陷被预防，约 1,250 个 bug 被修复（部分接入）[p7]
  - Mantis presubmit：25K 次扫描，100+ 威胁模型 [p8]
  - 分诊 agent：精度 91.1%，召回 77.2%，F1 83.6%（355-CL 基准）；5.8 s/bug，约 100 s/CL，10.3 bug/min [p10]
  - Bug Fix Agent 本地 CLI 成功率 78.4%，目标 90%+ [p11]
- 提到的公司/客户/产品/标准：Google、Mantis（开源 github.com/google/mantis）、CodeMender、Kythe、Black Hat USA 2026
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（分诊精度与速度）

### P294 07_Hyperscale Storage Solutions for NeoClouds presented by Everpure
- 讲者/机构：Prathamesh Nalawade，Principal Product Manager，Everpure（2026-10-13）| 类型：厂商展示
- 方向归属：主 [存储]
- 核心主张：NeoCloud 规模下每个百分点都关系到成本；用统一的构件和主机侧 DirectFlash 全局闪存管理（聚合 NAND、降低过度预留和写放大）替代逐盘闪存管理（p2, p6-7）。
- 关键数据（自报）：开发周期缩短 3–6 个月；多源 NAND 达 EB 级供应韧性；存储效率提升 +10–20% [p8]
- 提到的公司/客户/产品/标准：Everpure、DirectFlash、FlashArray/FlashBlade、Ceph
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（DirectFlash 全局闪存管理）

### P295 08_LITEON 1MW Power Rack Solution for AI Data Center presented by LITEON
- 讲者/机构：Terry Zhang，Technical Director / CIPS，LITEON（2026-10-13）| 类型：厂商展示
- 方向归属：主 [底座-电力]
- 核心主张：提出 OCP 21" 1.1 MW HVDC 电源机架架构：6×220 kW 电源架（AC→HVDC）、600 kW DC PDU、CBU/BBU 与 800V→50V DC/DC 架；市场时间线 50VDC 到 800VDC，2028–2029 SST（p2-3）。
- 关键数据（自报，样机/量产时间为计划）：
  - 220 kW 电源架：峰值效率 >98%、满载 >97%，保持时间 >20 ms；样机 2026-11 测试，量产目标 2027 Q2 [p4]
  - 108 kW CBU 架（EDLC，18 kW/模块，5 s 后备）样机 2026-08，量产 2027 Q2 [p5]
  - 180 kW HVDC BBU 架（6×30 kW，60 s@180 kW，LFP，±400 Vdc，10 年设计寿命）样机 2026-11，量产 2027 Q3 [p6]
  - 600 kW/2OU DC PDU，4 条 200 A 800V 软线，每条 150 kW [p7]
  - 120 kW 1OU 800V→50V DC/DC 架：峰值 >98.5%，满载 98% [p8]
  - 规模范围 1.2 MW–7 MW；架构三类：50–500 kW/IT 机架（电源架）、500–2,500 kW/计算单元（电源机架 HVDC）、>2,500 kW（SST）[p2]
- 提到的公司/客户/产品/标准：LITEON、Mt. Diablo、Murata US21700 LFP 电芯、UL1973、UN38.3、UL9540A
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（1.1 MW HVDC 电源机架架构提案）

### P297 10_Microgrids at Scale Resilient Power Infrastructure for AI Data Centers
- 讲者/机构：Nick Baileys，Energy Infrastructure Solutions Director，Delta | 类型：厂商展示（文字层为空，全部看图）
- 方向归属：主 [底座-电力]
- 核心主张：AI 数据中心微电网需要为 AI 负载平滑设计的集成系统（发电、grid-forming BESS、并网接口、多层控制），支持 800VDC 或 480VAC（看图 p2-4）。
- 关键数据（看图，自报）：
  - Delta SST：MW 到 LV 转换效率 98.5%，直接 800VDC [看图 p4]
  - Detroit 测试场：Microgrid 1 交流耦合 5 MW/10 MWh（300 kW 燃气轮机、1332 Vdc、2 个 5 MWh BESS）；Microgrid 2 直流耦合 2.5 MW/5 MWh（SST、800 Vdc 母线、2 个 2 MWh BESS+1 MWh 超级电容）；400 kW 光伏；110 kV 并网 [看图 p5]
  - 微电网并网母线 12.47–34.5 kV AC；通过 SST 向计算侧 800 VDC 供电 [看图 p3]
  - Delta 2025 全球营收 \$17.9B [看图 p6，公司自述]
- 提到的公司/客户/产品/标准：Delta、AESC、PCS3440、SOFC、VPP
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（微电网架构图）；p5（Detroit 微电网示范场）

