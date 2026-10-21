---
title: "OCP 方向5 基础设施底座 综合洞察"
tags:
  - OCP2026
  - 综合洞察
---

# 方向5：AI 基础设施底座（电力 800VDC/SST/BBU/储能/电网交互与功率平滑；冷却 冷板单相/两相、浸没、CDU/sidecar、水质与可靠性；机架与机械 ORv3/ORW/Mt Diablo、GW 级园区建设、交付周期）

索引说明：〔Pxxx pN〕为 OCP 2026 讲稿 PDF id 与页码；〔T06 mm:ss〕为 Scale-across 面板视频转写。素材主体为 by_direction/底座.md（主归属 157 节、次归属 49 节），第 8 节另引 by_direction/Across.md、Up.md 中与底座约束相关的条目。口径标注：自报、仿真、实验、现网、预测、引用（注明来源）、看图、存疑。厂商自报数字与实验/现网数字不混表；混表时逐项标注。机构与题目简写见文末索引对照表。

## 0. 一句话结论 + 5 条核心判断

**一句话结论：** OCP 2026 的底座议题已从"机柜能不能供上电、散掉热"转到"园区能不能按电网规则接入、按工厂节奏交付"。电力侧的共识路线是 800 VDC + 集中式 SST + 分层储能，NVIDIA 给出的设备就绪时间为 2026 Q3（机架级）到 2028 Q1（数据大厅级）；冷却侧单相冷板是当前主力，但 2.3 kW 级加速器已落入其经济边界之后的"回避区"；机架承重（4,700 kg 到 15,000 lb）和每柜数千到上万根光纤成为新的物理约束。决定节奏的是并网规则、流体与 DC 保护标准、设备交期，而不是单个器件的效率。

**判断1：机柜功率从 145 kW 走向 570 kW–1 MW，800 VDC 已进入设备排期；争论点是部署形态（sidecar / Power Center / SST Power Block），而不是要不要转。**
- NVIDIA 机柜代际：Gen1 GB200/GB300 54 VDC 145 kW → Gen2 Vera Rubin NVL72 330 kW → Gen3 570 kW（800 VDC 进 PSU、100% 液冷）→ Gen4 800 VDC 原生约 1 MW；设备就绪 A Power Rack Q3 2026、B Power Center Q2 2027、C Power Block Q1 2028（自报，看图）〔P167 p3, p17〕〔P252 p4, p23〕。
- 机制一（空间）：机架功率 ≥100 kW 时机架内转换与备份占 35%+ 空间，AC:DC 转换占 10–15%，N+N 翻倍，机架内 BBU 再占 10–15%；超过 600 kW 机架内 AC/DC 不可行（Google/NVIDIA 自报）〔P201 p4〕。Rittal/Bosch 称 480 VAC 约在 300 kW 到极限〔P031 p2〕。
- 机制二（电流）：48 V 母线在 1 MW 机柜下电流 18,519 A、母线铜损 >50 kW（xFusion 自报计算）〔P271 p12〕；同功率下 800 V 电流约 1/16、损耗约 1/256（理论推导）〔P375 p4〕。
- 板级配套跟进：Google/Meta/Microsoft 2026 Q4 启动 ±400V/800V 板载电源模块工作组，规格 Vin ±400V/800V ±10%、全砖 12 kW、效率峰值 >98.5%，目标 2H 2027 发布〔P190 p3, p10, p12〕。

**判断2：电网交互从运营方的内部问题变成并网准入条件；功率平滑需要从芯片到园区的分层储能，"负载模型"成为交付物。**
- 事件驱动：2024-07 北弗吉尼亚约 1,500 MW 电压敏感负载意外脱网〔P198 p2〕；NVIDIA/Danovo/Equinix 列出 2024–2026 多次数据中心自发减载，含 2026-07-22 Dominion 约 3,800 MW，FERC 2026-07-16 要求 NERC 于 2026-12-31 前提交计算负载可靠性标准（引用公开信息）〔P197 p3, p6〕。
- 规则已成文：MISO 10 MW/5 s 滑窗、30 MW/min；ERCOT 10 MW/5 s；SOCO 5–55 Hz 单频 2.5 MW（Microsoft 汇总）〔P028 p6〕；OCP VRT & PFAPR v1.0 计划 2026-10 发布，Power Ramp & Fluctuations v1.0 计划 2027-Q1〔P198 p9〕。
- 机制：同步 GPU 负载使设施功率毫秒级波动 30–60%，振荡能量集中在 0.2–3 Hz（Echion 引述）〔P182 p3〕；ML 负载约每年 100 万次循环，LFP 3k–10k 次循环不适用，需 BBU/CBU 双功能 + 机架级 EDLC（Google 自报）〔P178 p9, p10〕。
- 已有实测：Vera-Rubin NVL72 机架内 400 J/GPU 储能 + IPS，LLM 训练峰值功率降 13% / 51%（两组结果，实测，看图）〔P389 p3–p5〕；Skeleton 实测 sidecar 内 0.1 Hz 衰减 −72 dB、1 Hz −60 dB（实验，看图）〔P196 p7〕。

**判断3：单相冷板 2026 年已覆盖约 80% 顶级加速器 TDP，但 2.3 kW 级器件已越过其经济边界；两相、微流控、浸没各自推进，没有单一替代者。**
- 采用曲线：顶级加速器 TDP 中以冷板出货的比例约 24 个月内从 <10% 升到 >90%，看图 2026 约 78–80%、2028 约 97%（引用 Thermal Boundaries 白皮书，看图）〔P218 p16〕〔P210 p13〕。
- 边界：单相冷板（每 reticle 级器件）效率边界约 1.2 kW、经济边界约 2.1 kW、物理边界约 4.0 kW；两相冷板效率约 1.8 kW、经济约 3.4 kW；2026 领先加速器约 2.3 kW，落在单相回避区（看图估读，引用白皮书）〔P218 p24〕；按 2020 年以来趋势约 2029 年碰到 4 kW 墙〔P218 p15〕。
- 机制：Meta 拆解结到冷却液热阻，基线冷板 45% / TIM 20% / 硅 35%，冷板只占一半不到（看图）〔P010 p27〕；Wiwynn 指出单相转两相涉及工质、流动不稳定、流动架构、回路四方面，R1233zd(E) 在 2 kW 下结温均值约 93℃ vs PG25 约 78.5℃（实验，看图）〔P012 p2, p9〕，说明两相不是即插即用。
- 浸没处于"经济拉动、渐进不均"阶段：IT OEM 尚未规模出货浸没原生产品〔P233 p6–p8〕；Denvr 浸没 H200 在 neocloud 生产运行，NVLink 带宽与 DLC 差 −0.15%（实验）〔P228 p7, p17〕。

**判断4：液冷的主要风险已从"散不散得掉"转到流体化学、接口互操作与调试运维；OCP 在 2026 年密集发布流体与接口规范，但关键测试方法仍缺。**
- 现网水质问题：PG 25–27.2% 下 TVC 仍有 500–160,000 CFU/mL（现网，看图），PG≥25% 只是抑菌指引不是杀菌保证〔P006 p4, p5–p7〕；Ecolab 给出 PG 运行范围 24–29% v/v、azole >400 ppm〔P324 p8〕。
- 材料与流速：PG25 在 6.2 m/s 运行 93 天铜管无整体冲蚀，但弯头缓蚀膜约 8 nm vs 直管约 35 nm（实验 XPS）〔P008 p15〕；软管 pEPDM 析出物 352–6,379 ppm，配方差异大（实验，Phase 1）〔P249 p9〕；混用 PG25 缺少模拟工况方法，Phase 1 结果 2026-10 下旬才发布〔P217 p3, p8〕。
- 接口：UQD V2.0 首次试点跨厂商互操作测试，非标准插头倒角插拔力尖峰可达约 100 lbf（实验，看图）〔P003 p50, p52〕。
- 调试与运营成本：传统 TCS 管路 6 道冲洗、每道 5–7 天，预调试可从 7 周压到 1 周；每周延迟损失 \$300–400M（假设 100 MW/600 机架，看图，自报）〔P181 p3, p6〕；Meta 生产中 50+ 种液冷配置组合，湿度误报改用去抖与跨传感器过滤后事件约降 100 倍（看图，自报）〔P220 p8, p24〕。

**判断5：GW 级园区的交付瓶颈在电力接入与长交期设备；机架承重、标准化建筑模块和工厂集成成为提速手段，OCP 把范围从机柜扩到"电网到芯片"。**
- 交期：美国变压器交期 128 周（引用）〔P303 p3〕；发电机约 30→100 周、冷机约 20→75 周（2019→2025，McKinsey 引用/访谈）；美国能量接入最长 4–5 年，仅 65% 已宣布容量会投产（预测）〔P396 p4, p6〕；2026 设备交期全球平均 33 周、美国 42 周（引用）〔P387 p2〕。
- 机制：CMU 仿真把"芯片时间价值"计入后，建设 2 年的光储微电网 LCOE（计机会成本）\$0.642–0.690/kWh，低于 4 年接入的电网 \$1.01 和天然气 \$1.13（仿真，New Mexico 30 MW）〔P184 p13〕，部署速度比电价更重要。
- 机架与建筑：ORW 宽 1200 mm、最大载荷 4,700 kg，v1.0.0 已发布，2026-11 量产〔P030 p6, p11〕；Open DC v0.7 给出 2028+ 峰值 IT 密度 335 kW/ft（液冷）、ML 机架+sidecar 15,000 lb、集群基线 12 MW / 优选 24 MW〔P180 p3–p5〕。
- 工厂化：Crusoe 以工厂集成单元为故障域并逐单元通电〔P390 p4, p11〕；Aivres 欧洲 20 MW、约 100 柜项目 60 天交付（现网，自报）〔P291 p24〕；Foxconn 称 VR 相比 GB 自动化覆盖率 94% vs 56%、测试 FPY 80% vs 39%（自报）〔P261 p4〕。

## 1. 需求与架构

### 1.1 需求数字

| 类别 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| 机柜功率代际 | 145 kW（GB200/GB300，54 VDC）→ 330 kW（VR NVL72）→ 570 kW → 约 1,000 kW（800 VDC 原生） | 自报，看图 | 〔P167 p3〕〔P196 p3〕〔P269 p2〕 |
| 机柜功率（他方口径） | GB300 142 kW、VR NVL72 230 kW、Helios(MI455X) 246 kW（互联网检索，近似） | 引用 | 〔P181 p11〕 |
| 机柜功率（Supermicro） | GB300 NVL72 约 136 kW；VR NVL72 约 230 kW；VR NVL4 约 362 kW | 自报 | 〔P265 p16〕 |
| 机柜功率趋势 | 2021 约 100 kW、2024 约 1 MW、2027 起 1.5 MW+（TE）；2020 约 10 kW → 2026 约 150 kW → 2030 约 1,000 kW（Phoenix Contact） | 自报/看图估读 | 〔P025 p3〕〔P280 p29〕 |
| 峰值/平均机柜密度 | 全球平均 2025 约 20 kW → 2030 约 47 kW；峰值 2024 约 320 kW → 2030 约 1,180 kW → 2035 约 3,550 kW | 预测，看图估读（Promersion） | 〔P218 p8, p13〕 |
| 芯片 TDP | 2025 1,000 W、2026 1,400 W、2027 2,300 W、2028–2030 3,100 W（标注来源 NVIDIA DSX） | 看图 | 〔P245 p3〕 |
| 芯片 TDP（他方） | Rubin 2,300 W（2026E）；TH7 204.8T 3.5–4 kW | 自报/预测 | 〔P302 p6〕 |
| 封装热流 | 局部热点 2025 约 3.3 W/mm²，2027 前约 7.5 W/mm² | 预测，看图 | 〔P001 p2〕 |
| 单处理器功率 | 约 200 W → 约 2,000 W（20 年） | 自报 | 〔P022 p2〕 |
| 全球容量需求 | 171 GW（2025）→ 298 GW（2030），基准情景 | 预测（McKinsey，图中对应关系存疑） | 〔P396 p2〕 |
| 全球容量需求（另一口径） | 77 GW（2025）→ 227 GW（2030），15 个来源区间 152–321 GW | 引用多来源 | 〔P397 p4〕 |
| 美国用电 | 176 TWh（2023，4.4%）→ 325–580 TWh（2028，6.7–12%） | 引用 LBNL | 〔P260 p6〕〔P182 p3〕 |
| CSP 新增 AI 算力 | 前 5 大 CSP：2023 3 GW、2024 7、2025 8、2026E 18、2027E 26 GW | 自报（Foxconn） | 〔P261 p2〕 |
| 园区规模 | Meta Prometheus 1+ GW，未来几年 5 GW（Hyperion）；Microsoft Maia 300 多 GW 部署自 2027 | 自报 | 〔P364 p20〕〔P369 p9〕 |
| 电网事件 | 大负载跳闸 1.5 GW（2024）、1.8 GW（2025）、3 GW（2026） | 引用 | 〔P176 p2〕 |
| 并网排队 | ERCOT 仅大负载并网申请 400+ GW | 引用 | 〔P197 p9〕 |
| 可削减负载容量 | 年削减 0.5%（177 h）可接入 98 GW；0.25%（85 h）76 GW | 引用 Duke 2025 | 〔P171 p3〕 |
| 机柜重量 | 单宽机柜 2022 约 800 kg → 2024 >1,300 kg → 2028 >4,000 kg | 预测（Wiwynn） | 〔P222 p3〕 |
| 网络机架光纤 | Legacy 100–200 根 → AI 时代 2,000+ 根；光纤管理区 2,000–4,000 根 | 自报（Arista/Jabil） | 〔P124 p3–p5〕 |
| 冷却占比 | 美国数据中心用电：IT 59%、冷却 30%、变压/UPS 9%（LBNL 2025） | 引用 | 〔P083 p4〕 |

### 1.2 功率分层与架构选择：各家口径对照

| 机构 | 分层（功率 → 供电/冷却形态） | 索引 |
|---|---|---|
| NVIDIA | A Power Rack（机架级，660 kW sidecar，415–480 VAC 入、8×125 A DC 出）/ B Power Center（集群级）/ C Power Block（数据大厅级，SST 5 MVA，6+1 冗余，新建） | 〔P167 p4, p6, p12〕 |
| Delta（含 NVIDIA 讲者） | 50 VDC 适用 <250 kW；>250 kW 用 ±400 VDC/800 VDC | 〔P252 p6〕 |
| Rittal | <30 kW 风冷；140 kW 为 48 VDC 机架内转换实际上限；500+ kW 800 VDC sidecar；约 1 MW 下一代 | 〔P239 p4〕 |
| LITEON | 50–500 kW/机架用电源架；500–2,500 kW/计算单元用 HVDC 电源机架；>2,500 kW 用 SST | 〔P295 p2〕 |
| Rittal/Bosch（引 NVIDIA） | 2026/27 660–800 kW sidecar；约 2028 1.5–2 MW Power Center；约 2029 4–5 MW；2030+ 中压直接转换 | 〔P031 p2〕 |
| Google/NVIDIA | 2026 单列验证；2027–2028 数据中心级验证；2029+ GW 级 LVDC 原生规模部署 | 〔P201 p11〕 |
| SwRI | 风冷至约 60 kW/机架；冷板/后门约 50–100 kW；浸没 >200 kW（对应关系存疑） | 〔P234 p3〕 |
| nVent | 风冷房间约 10–15 kW/机架，热通道封闭 20–40 kW；新 AI 机架 >250 kW | 〔P272 p2〕 |
| MEGMEET/NVIDIA | 风冷上限 33–50 kW/机柜 | 〔P269 p4〕 |
| AICC（hyperscale adjacent） | 8×GPU scale-up 8–15 kW；1×GPU 0.8–3 kW；邻近场景机柜最高 120 kW（多数 <50 kW） | 〔P159 p6〕〔P160 p11〕 |
| 企业调查 | 86% 机架在 5–30 kW；64% 仍仅风冷（来源未见） | 〔P391 p3〕 |

注：SwRI 一行为看图对应，原笔记已标存疑。各家分界数字不一致（48 VDC 上限 140 kW vs 250 kW），差异来自是否计入液冷母排与电源架液冷，材料未给统一条件。

### 1.3 架构演进要点

1. **供电链缩级**：常规路径 7 级对 800 VDC 路径 4 级（NVIDIA，看图）〔P167 p13〕；AC 现状托盘前 3 级转换〔P200 p12〕；Google 估计原生 LVDC 占地致密化 20–30%、减少 9,000 安装工时、芯片到电网效率 >1%（内部估计）〔P260 p18〕。
2. **转换移出机柜**：Rack & Power 路径 2025 LVDC sidecar → 2027 Mt. Diablo/AC busway → 2028+ 设施级 LVDC 与端排 SST〔P032 p3〕；电源架 ORv3 18 kW → HPRv1 33 kW → HPRv2 72 kW → HPRv4 100/160 kW〔P032 p4〕。
3. **储能下沉并分层**：机柜级电容（ms）、LVDC 动力链功率电池（分钟级，UPS/FRT/平滑）、园区级长时储能〔P173 p11〕；Google 按时间尺度列出硅设计→分层软件→工作负载弹性→CBU/超级电容（µs–ms）→设施 BESS〔P260 p9〕；SST + ESS 把机架内数百个电池合并为行级备份〔P199 p4〕。
4. **冷却分段**：acquisition（IT 侧，2–3 年周期）/ transport（manifold/QD/CDU，"seam"）/ rejection（设施侧，几十年周期），两种时钟在接口处相遇〔P218 p17–p20〕。
5. **设施高温化**：S45 供液 45℃ 扩大自然冷却窗口，250 MW 仿真中 Design 2 相对 S30 额外算力 Chicago 23.9 MW、Phoenix 5.5 MW〔P177 p13〕；多家冷板宣称支持 45℃ 入口〔P251 p6〕〔P034 p4（40℃ 设施水）〕。
6. **建筑标准化**：Open DC 1.0 定义 7 个标准空间、12–24 MW 模块〔P260 p22〕；NVIDIA 16 MW 部署单元，800 VDC 母排架空分配到 4 个 4 MW 单元〔P367 p8〕。

## 2. 技术路线对比

### 2.1 电力：配电与转换

| 路线 | 代表方案/厂商 | 关键指标（带条件） | 成熟度 | 索引 |
|---|---|---|---|---|
| 800 VDC sidecar / Power Rack | NVIDIA Option A；Delta 660 kW 行间电源柜；Rittal/Bosch PMoC | Delta 效率最高 98%、集成 480 kW BBU；PMoC 单 PSU >200 kW，800 kW 仅需 4 个 vs PCB 方案 40 个 | 设备 Q3 2026 就绪（自报） | 〔P167 p17〕〔P252 p12〕〔P031 p3〕 |
| 1.1 MW HVDC 电源机架 | LITEON | 6×220 kW 电源架，峰值 >98%、满载 >97%；样机 2026-11，量产目标 2027 Q2 | 样机阶段 | 〔P295 p3, p4〕 |
| 液冷 800 VDC 电源柜 | MEGMEET/NVIDIA | 800 kW 标准，8×100 kW 架，BBU ≥90 s@40℃；液冷后可取消冷热通道，设施 CAPEX 最多约降 10% | 自报 | 〔P269 p7, p10〕 |
| SST（MV→800 VDC） | OCP SST Spec Rev 0.3（Google/NVIDIA）；Luxshare Nova Link；Delta | 规范：±0.5%/±1%/±3% 电压容差，效率 ≥98%，SKU A 13.8 kV/5 MW；Luxshare 35 kV/10 MW 98.7%、9.6 m²、交期 4 个月 vs 传统 93.3%、188 m²、24–30 个月（自报）；Delta 98.5%（看图） | 规范草案；Power Block Q1 2028 | 〔P199 p7, p8〕〔P303 p4, p9〕〔P297 p4〕 |
| 多端口/可互换架构 | Edged GridBlock | 5 MW 单元取消为机械负载另设的 500 kVA 变压器+UPS 第二条链（自报） | 方案阶段 | 〔P312 p5〕 |
| DC/DC 电源架 800→50/54 V | Delta 90/108 kW 峰值 98.5%；LITEON 120 kW 1OU 峰值 >98.5%；Google/NVIDIA 密度 55→95 kW/RU | 自报 | 量产准备 | 〔P252 p15〕〔P295 p8〕〔P201 p7〕 |
| 板载 800→50 V 砖 | LITEON-EPIC 全砖 10 kW、1,522 W/in³、峰值 98.7%；Advanced Energy >98% | 自报 | 2027 年 12 kW | 〔P276 p4〕〔P023 p10〕 |
| 800 V→0.8 V 架构 | TI 五种架构，20 kW 下端到端 64–74%，VPD 优于 LPD | 自报，看图 | 对比研究 | 〔P022 p6〕 |
| 垂直供电 VPD | AMD 二级电流密度 MI300X 0.88 → MI455X 最高 2 A/mm²，目标 3 A/mm² | 自报 | 呼吁标准化 footprint | 〔P466 p3, p5〕 |
| 超导 HTS 配电 | VEIR | ≤800 Vdc 每根 10/20/30 MW；5,000 A 馈线 HTS 12.3 kg/m vs 铜母线 156 kg/m（自报）；系统可用性 5 个 9 需可并行维护液氮系统（模型） | 白皮书工作流 | 〔P183 p3, p4〕〔P202 p11〕 |
| 现场发电 | SOFC（Oracle Project Jupiter 2.45 GW 计划；AEP 1 GW offtake）；Delta 微电网 | SOFC 效率 53–65%（LHV），功率密度 25–100 MW/acre（引用/自报） | 早期，OCP Energy 拟立倡议 | 〔P187 p4, p10, p11〕〔P297 p5〕 |

### 2.2 电力：保护与接地

| 路线 | 代表方案 | 关键指标 | 状态 | 索引 |
|---|---|---|---|---|
| 2-wire（800 V P-N） vs 3-wire（±400 V） | Siemens 对比 | 2-wire 复杂度低、功率密度高但故障能量高；3-wire 需平衡部件；保险丝方案需 300 mF，SSCB 方案仅 10 mF（仿真） | 两者并存（Mt Diablo/Diablo 400 为 ±400 V） | 〔P189 p4, p9〕 |
| 分断器件 | Schneider；Microsoft/NVIDIA | 保险丝 0.5–5 ms、EMCB 1–20 ms、混合 0.2–1 ms、SSCB <10 µs；800 V 以上分支保护存在标准缺口，开关柜与 busway 目前限 1,000 Vdc | 标准缺口 | 〔P191 p11, p17〕〔P195 p8〕 |
| SSCB + DC Fault Manager | Vertiv | 检测+跳闸 0.7–3 µs，通知对端 <5 µs；选择性从时间曲线转到通信链路；接口预算为提议非实测 | 提案 | 〔P205 p7, p8〕 |
| 检测 | IMD（源/主母线）+ RCM（分支/机架） | 高阻抗故障与串联电弧可能低于保护阈值 | 系统设计建议 | 〔P195 p4, p10〕 |
| 电弧闪光 | Schneider 39 次实测；Google 仿真 | 54% 测试 <0.1 cal/cm²，5% >4 cal/cm²（实验）；带二极管时 SSCB 0.128 cal/cm²，无二极管 MCCB >1.2 cal/cm²（仿真）；现有 IEEE 1584/NFPA 70E 不覆盖变换器供电 DC 系统 | 方法缺口 | 〔P193 p12〕〔P203 p8〕 |
| 标准映射 | UL Solutions | 800 VDC 母线槽 UL 857↔IEC 61439-6；SST UL 2877 OOI↔IEC 62477-2；DC AFCI/GFCI、液冷电缆等尚无标准 | 映射完成，部分空白 | 〔P192 p6〕 |

### 2.3 储能与功率平滑

| 路线 | 代表方案 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| GPU/机架闭环平滑 | NVIDIA IPS（Vera-Rubin） | 400 J/GPU；峰值降 13%/51%（实测，看图）；PSU 最大 AC 爬升率 400 W/s 示例配置 | 产品功能 | 〔P389 p3–p7〕 |
| 动态功率分配 | NVIDIA DSX MaxLPS | 540 kW 预算下静态分配搁浅 210 kW，MaxLPS 多放 1 柜；Nscale 同预算多部署 37% GPU（自报） | 现网案例（自报） | 〔P257 p5〕〔P367 p13〕 |
| EDLC/CBU | LITEON 108 kW CBU 架（5 s）；Skeleton CBU800 80 kW 连续/120 kW 峰值 | 自报 | 样机 2026-08，量产 2027 Q2（LITEON） | 〔P295 p5〕〔P196 p9〕 |
| 高功率 BBU 电芯 | Panasonic NCA/LFP 复合 | 300 W×90 s 需 7.5 Wh，LFP 不足；复合电芯热板测试不起火（实验，看图） | 路线图 | 〔P026 p6, p7〕 |
| 对称高倍率 UPS 电池 | Echion XNO / Proper Voltage VaultX | >30C/30C、50,000 循环（实验室电芯）；10 年对比 ORv3 BBU \$317/MWh、LFP UPS \$25、XNO \$10（仅电芯，未折现） | 原型在建 | 〔P182 p8, p10, p13〕 |
| UPS + BESS | Schneider Galaxy；EPC Power | 0.15–0.5 pu 全电池供电 <300 ms 恢复；UPS 电池扩容 0.1–0.15 \$/W vs 新增 BESS 0.3–0.6 \$/W（自报估算）；ESS 需亚周波级 grid-forming 控制 | 产品/提案 | 〔P173 p14, p15〕〔P176 p5, p6〕 |
| 电源固件 + 电网侧设备 | Google | 电源固件更新（利用电容）、MV-UPS、SVC/E-STATCOM；建议设生效日期与既有设施豁免 | 规范在制定 | 〔P198 p7, p8〕 |
| 需求响应 | Google；EPRI | Google 在多家美国公用事业合同中整合 1 GW 需求响应；EPRI 灵活性分类 Class A–E | 现网（自报）/V1.0 | 〔P260 p12〕〔P392 p5〕 |

### 2.4 冷却

| 路线 | 代表方案/厂商 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| 宽机箱风冷（通用计算） | Microsoft/Lenovo 900 mm | 气流面积约 +50%，每 kW 风扇功率降约 20–30%；全液冷基础设施成本比混合液冷高 50%（早期数据） | 早期 | 〔P215 p4, p5, p10〕 |
| 单相冷板（主流） | CoolIT、Corintis、Frore、Auras、Axiom 等 | CoolIT 15 kW TDP 冷板验证（1.2 LPM/kW，45℃ 设施水）；Corintis H200 结-入口温升 −23%（实验）；Microsoft unitary cell 结温最多降 10℃（实验） | 量产，逼近经济边界 | 〔P310 p14〕〔P010 p11, p16〕 |
| 两相冷板 | ZutaCore、Wiwynn、Wistron 负压水沸腾、SemiValley/CreAlien 水两相 | ZutaCore >4,000 W 单芯片、年化 pPUE 1.03（自报，看图）；Wistron 低流量下两相热阻低 15%，≥3–4 LPM 趋同（实验）；SemiValley 325 W/cm²@0.14 L/min（实验/自报） | 生态在对齐，Meta 牵头标准化面板 | 〔P322 p19〕〔P001 p6〕〔P351 p12〕〔P011 p4〕 |
| 单相浸没 | Denvr、Intel/ExxonMobil、GRC 等 | Denvr 1 MW 占地 600 vs 6,400 sq ft，PUE <1.04（自报）；Intel IRDT 24 台 63,548 h，MTBF（80% LCL）39,471 h（实验） | 小规模生产 | 〔P228 p4〕〔P235 p16〕 |
| 两相浸没 | Samsung/Chemours/LiquidStack | SSD >15,000 h、0% 失效（进行中）；主要风险为助焊剂残留致枝晶 | 长期测试 | 〔P231 p3, p8〕 |
| CDU 机架内 / 行间 | Nidec In-Rack 300 kW、In-Row 至 15 MW；Supermicro 机架内 250 kW、行间 1.8/2.5/5 MW；Delta 800 VDC 行间 2.5 MW | 自报 | 量产 | 〔P314 p11, p12〕〔P265 p17〕〔P252 p26〕 |
| CDU 选型 | Gamma/Alfa Laval/Stulz 仿真 | 同 2.3 MW 十种选型资本成本差约 3 倍、年能耗差约 17%；ASHRAE 127-2020 Addendum b 首次定义液-液 CDU 测试方法 | 仿真/新标准 | 〔P214 p6, p13〕 |
| RDHx / AALC sidecar | nVent（Helios 双 RDHX）；AMD/Meta Mega sidecar；Google Brazos | Helios 约 11%（约 27.5 kW）热排入空气；单相 sidecar 需 10+ 机架宽度才做到 1 MW；Brazos 闭环 60 kW 可用于风冷旧机房 | 产品/规范 Rev 1.0 2026 Q4 | 〔P272 p2, p6〕〔P211 p8, p11〕〔P395 p12〕 |
| 光模块/NIC 液冷 | TE 模块内冷板；Luxshare OSFP 2×8 液冷笼；FIT XPO；OCP NIC 200 W | TE：>35 W 模块从未风冷出货；模块内液冷 120–500 W，500 W@0.7 lpm 实测约 75℃；Luxshare 16×32 W 实测最高 55.2–62.6℃ | 产品化初期 | 〔P005 p3, p4, p13〕〔P256 p10〕〔P238 p11〕〔P453 p8〕 |
| 排热侧 | NVIDIA 三设计对比；Daikin 区域对比 | Design 2（WCC+干冷器+CRAH）15 年 TCO 最低，PUE 约 1.09–1.11（仿真）；PJM East、ERCOT 模型偏向干冷（仿真） | 设计选择 | 〔P177 p16, p19〕〔P083 p10〕 |

### 2.5 机架与机械

| 路线 | 代表 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| ORv3 HPR | Meta/Rittal | 宽 600 mm、高 2,286 mm、最大载荷 1,400 kg | 量产 | 〔P030 p6〕 |
| ORW（双宽） | Meta/Rittal | 宽 1,200 mm、高 2,386 mm、载荷 4,700 kg（上年 3,500 kg），液冷母线 >700 kW；4,700 kg 下振动/跌落/17° 倾斜全通过（实验） | v1.0.0 2026-04-28 发布，2026-11 量产 | 〔P030 p3, p6, p9, p11〕 |
| IT 机柜 800 VDC 母线 | TE | 兼容 ORv3 35 mm 宽，500 kW/625 A 到 1 MW/1,250 A；625 A 实测最大温升约 27℃ | 未作为 OCP 贡献授权 | 〔P025 p2, p6, p10〕 |
| MGX 1.2 | NVIDIA | 钢结构 +100 lb；锁扣杆 6,000 lb 插拔力；液冷母排 5,000 A；托盘无线缆、无风扇、无软管 | 贡献 OCP | 〔P367 p6, p7〕 |
| GX5000 | HPE | 单柜 400 kVA+，50 V 8,000 A DLC 母排，重 4,535 kg，900×1,200 mm | 产品 | 〔P034 p4, p5〕 |
| Open DC | Google/Meta/NVIDIA/AMD | 最大机架 8,000 lb（28"W×48"D），ML 机架+sidecar 15,000 lb；热通道 54"、冷通道 82"、层高 ≥18 ft；2" 管 365 kW、4" 管 1,459 kW（1 lpm/kW，ΔT 15℃） | v0.7 征求意见 | 〔P180 p5–p7〕 |
| 减重 | Wiwynn PPS+GF | 冷板减重 66%、内部 manifold 减重 52%（自报）；冷板/manifold/管路占液冷部件重量 70%+ | 验证中 | 〔P222 p4, p9〕 |
| 模块化 TCS | Victaulic 等 | ≤230 kW 机架 2"/DN50 drop；>150,000 接头、15 年无泄漏，MTBF >9×10⁹ h（下置信界） | 工作流 | 〔P181 p14, p18〕 |

## 3. 关键数据表

### 3.1 转换效率与功率密度（全部为厂商自报，除注明外）

| 环节 | 数值 | 索引 |
|---|---|---|
| 到机架能效 | 今天约 92%（UPS 方案）→ 3.5 MW 整流器约 97% → 带储能 grid-forming SST 约 98%+（Axiom，"illustrative"） | 〔P262 p5–p6〕 |
| 48 V → 800 V 系统 | 转换级 4→3，系统效率 88%→90%，线损 5–8%→<1%（xFusion） | 〔P271 p11〕 |
| SST | Luxshare 35 kV/10 MW 98.7%、1.04 MW/m²；13.8 kV/3 MW 风冷 98.8%；下一代目标 99%、1.5 MW/m² | 〔P303 p9–p11〕 |
| 50 V→12 V | LITEON-EPIC 1,500 W、7,762 W/in³、峰值 97.9%；OmniOn 50%/100% 负载 98.5%/97.9% | 〔P276 p7〕〔P304 p10〕 |
| 50→0.8 V 单级 VRM | 240 A 单模块，峰值 91.4%、满载 87% | 〔P276 p9〕 |
| PSU 液冷理由 | 1 MW 下 97% PSU 损耗 30 kW；液冷 PSU 55 kW/1U | 〔P252 p16〕 |
| 全工作范围效率 | LLM 负载下 GPU 利用率约 15–45% 摆动，主张时间加权效率；SiC vs GaN 差距 ≤0.3 点（非同口径） | 〔P304 p6, p8〕 |

### 3.2 电网并网要求

| 电网/文件 | 要求 | 口径 | 索引 |
|---|---|---|---|
| MISO / ERCOT / SOCO / AESO | 10 MW/5 s 滑窗与 30 MW/min；10 MW/5 s；0.1–5 Hz 单频 10 MW、5–55 Hz 2.5 MW；初期 0.16 MW | 自报汇总 | 〔P028 p6〕 |
| 多电网对照 | 分钟级 ramp 10–30 MW/min；亚分钟 10–25 MW 在 4–6 s；PF 多为 ±0.95；PFAPR 多为 90% 1 s | 引用 Danovo/Quanta，看图 | 〔P176 p4〕 |
| PFAPR | FinGrid 1 s 内 90%；ERCOT 2 s 内 90%；Energinet 5 s 内 80%、30 s 内 90% | 引用 | 〔P198 p5〕〔P260 p8〕 |
| 拟定 VRT | 0.80≤V<0.90 穿越 2 s；0.50–0.80 穿越 0.5 s；V<0.35 0.15 s；恢复后 2 s 内回到 90% | OCP 草案 | 〔P198 p6〕 |
| 频率影响 | 280 MW 机房无缓冲时 44 s 循环使频率摆动 −60 到 +65 mHz，超 ERCOT 死区 ±17 mHz | 仿真（Echion） | 〔P182 p9〕 |
| NERC 注册 | CLO 标准提案：总接入负荷 ≥50 MW、≥100 kV | 引用 | 〔P392 p7〕 |
| 模型交付 | 平均化 EMT 模型 10 s 仿真约 16 s，开关模型约 28 分钟 | 引用 ERCOT/TAMU | 〔P197 p11〕 |

### 3.3 冷却热边界与热数据

| 项目 | 数值 | 口径 | 索引 |
|---|---|---|---|
| 风冷 | 约 600 W 器件处风扇功耗占比约 15%（效率 knee），约 1,000 W 达机箱气流极限、占比约 33% | 看图估读（白皮书） | 〔P218 p23〕 |
| 单相/两相冷板边界 | 见判断3 | 看图估读 | 〔P218 p24〕 |
| 芯片功率路线 | 风冷上限约 500 W、单相上限约 2 kW；2035 每 GPU 模块约 15.4 kW | 看图（行业预测） | 〔P351 p11〕 |
| 结温与产出 | Tokens/Watt：TjA 约 65℃ 内约 100%，约 87℃ 约 80%，95℃ 约 66% | 看图（Frore 自报） | 〔P300 p4〕 |
| 液冷 vs 风冷 | 8×H100 吞吐 +17%、功耗 −16% | 引用 NVIDIA 白皮书 | 〔P397 p9〕 |
| DLC vs 风冷服务器 | 32℃ 下 DLC 省 9.0–11.5% 服务器功率；风扇占风冷 co-lo 服务器功率 10.2%；PUE 风冷 1.28 vs DLC 1.37（风扇计入 IT 所致） | 实验/计算，看图 | 〔P084 p8, p9〕 |
| 冷却转算力 | 500 MW 示意：冷却 175→75 MW，IT 325→425 MW，PUE 1.54→1.18 | 示意模型 | 〔P397 p14〕 |
| PUE 与 IT 容量 | 每降 0.1 PUE 约多 8% IT 容量；100 MW 下 PUE 1.3→1.2 多 6 MW | 示意，自报 | 〔P239 p3–p4〕 |
| HBM 热 | HBM 堆栈占 2.5D 封装热阻 57%；HBM5 >2.0 W/mm² | 引用 ECTC 2026 | 〔P070 p6, p7〕 |
| 光模块 TDP | 224G 8-lane 27 W；448G 8-lane 70 W、64-lane 500 W（预测）；1RU 32 端口面板 1.9 kW/RU（预测） | 自报/预测 | 〔P005 p4〕 |

### 3.4 流体、可靠性与运维

| 项目 | 数值 | 口径 | 索引 |
|---|---|---|---|
| PG25 vs 水基 | 50℃ 导热 0.49 vs 0.63 W/m·K；粘度 1.3 vs 0.5 mPa·s；水基微生物理想 <1,000 CFU/mL | 自报 | 〔P324 p7, p9〕 |
| 溶解氧 | 未处理闭式回路 DO 3–7 ppm；旁流处理后约 0.1 ppm，铜挂片 0.37–0.53 µm/y（63 天/1,500 h） | 实验/自报 | 〔P002 p8, p9, p17〕 |
| 流体监测 | 单传感器能检出 upset，pH 对污染物裕度 0.0；实时监测指南 Q4 2026 | 实验，看图 | 〔P007 p11, p18〕 |
| 流速限值 | CDA 冷水 <2.4 m/s、热水 <1.5 m/s；Gates 称软管在其他行业 >9 m/s；Open DC 用 ASHRAE 3 m/s | 引用/自报 | 〔P008 p3〕〔P221 p2〕〔P180 p7〕 |
| 运输存储 | 降至冰点水膨胀约 9%、PG25 2–5%；量产机柜建议 Wet 或 Dry | 自报 | 〔P004 p10, p17〕 |
| 调试 | Level 5b 用真实算力负载验证瞬态与 PID，含 24–72 h burn-in；液冷负载箱需 ISO 4406 | 面板共识 | 〔P174 p3, p9, p10〕 |
| 浸没 MTBF | 相对风冷模型下限 3.4–5×；3,000+ 浸没服务器 30 个月队列最高 12×（引用 OCP EMEA 2025） | 引用 | 〔P233 p13〕 |
| 浸没液老化 | 在役 E-1（约 6 个月）表面电阻比温度老化样品低 85.1%；多数流体 TAN 高于 OCP 0.02 mg KOH/g 但未见问题 | 实验 | 〔P229 p15, p17〕 |
| 浸没 SI | Rev 3 要求 20–60 GHz 介电测试，覆盖 PCIe Gen5/6 到 224G PAM4；ITE 下一步聚焦 >32 GHz | 规范 | 〔P226 p14〕〔P227 p8〕 |

### 3.5 交付周期与成本

| 项目 | 数值 | 口径 | 索引 |
|---|---|---|---|
| 延误 | 2025 年 57% 项目施工延误 ≥3 个月 | 引用 | 〔P387 p2〕 |
| 被阻项目 | 2026 Q1 美国数据中心项目被阻/延迟 \$130B；14+ 州有暂停令 | 引用 Data Center Watch | 〔P172 p2〕 |
| 标准化收益 | OCP 标准化可缩短交期 3–6 个月，定制延长 6–12 个月 | 预测（McKinsey） | 〔P396 p8〕 |
| 每月等待损失 | 100 MW 站点每月等待供电/冷却损失 72 GWh | 示意 | 〔P239 p3〕 |
| 建设周期 | Denvr 模块化 6 个月；Aivres 20 MW 60 天；Supermicro 机架内 CDU 施工"数天" vs 行间 1–2 个月 | 自报 | 〔P386 p3〕〔P291 p22, p24〕 |
| BOM 碎片化 | 服务器与机架配置数 2016 年 25 → 2026 年 400；67% BOM 收到时带错误（引用） | 看图/引用 | 〔P402 p16, p22〕 |
| 部署速度 | Axiom 称部署速度最高快 50% | 看图，自报 | 〔P262 p11〕 |

## 4. 厂商与客户态势

### 4.1 超大规模用户与平台方

- **Google**：主推原生 LVDC（集中式 SST + BESS），估计占地致密化 20–30%〔P260 p18〕；牵头 SST Spec Rev 0.3〔P199 p7〕、VRT/PFAPR 规范〔P198 p9〕、板载电源工作组〔P190 p3〕；Deschutes 1.0（第五代开放 CDU）、Brazos sidecar、Open DC 1.0〔P260 p22〕；硬件储能侧主张 BBU/CBU 双功能 + EDLC，贡献预计 2–3 个季度〔P178 p10, p11〕；已整合 1 GW 需求响应〔P260 p12〕。
- **Meta**：牵头 ORW（4,700 kg）〔P030 p6〕和两相冷板标准化面板〔P011〕；PG25 混用研究、流速侵蚀研究〔P217〕〔P008〕；运营侧 50+ 液冷配置、呼吁最低遥测契约〔P220 p8, p27〕；Prometheus 1+ GW 跨楼宇、帐篷与托管设施〔P364 p2〕；IcePack 为其首个液冷网络机柜〔P244 p8〕；BOM 交换标准〔P402 p38〕。
- **Microsoft**：电网功率振荡限值与机架内电容滤波〔P028 p11, p14〕；聚合/级联电源架故障域〔P033 p5〕；废热回收（德国 ERF 2026 年 10%、2028 年 20%）〔P208 p3〕〔P085〕；通用计算宽机箱风冷〔P215〕；Mt Diablo 与 Mt Atlas〔P369 p14–p27〕；Maia 300 多 GW 自 2027〔P369 p9〕。
- **NVIDIA**：800 VDC 代际与 A/B/C 选项及时间线〔P167〕〔P252〕；系统性能要求（EDPP 180% 400 µs、150% 50 ms；26 µF/kW 输入电容；固态接地限 busway 约 26 m）〔P194 p4, p7, p10, p16〕；IPS、MaxLPS、DSX Flex〔P389〕〔P257〕〔P171〕；MGX 1.2〔P367 p6〕；排热 S45 仿真〔P177〕。
- **AMD**：Helios 约 246–250 kW，需双 RDHX〔P272 p2〕；VPD 电流密度路线〔P466〕；OAC 加速卡〔P391〕〔P465〕；Open DC 成员〔P180〕。
- **Oracle**：水效与区域决策〔P094〕；Project Jupiter 2.45 GW SOFC 计划（引用）〔P187 p4〕；Optics Reliability 与 gPUE/IUE 指标〔P370 p12, p19〕。
- **AWS、阿里**：本方向材料中无专门讲稿；AWS 仅出现在 TCS 工作流参与名单〔P181〕，阿里仅出现在网络平台层规范〔P413〕。

### 4.2 供应商站位

| 类别 | 厂商 | 站位 | 索引 |
|---|---|---|---|
| 800 VDC 电源 | Delta、LITEON、MEGMEET、Advanced Energy、OmniOn、Murata、Vertiv | 均按 NVIDIA A/B/C 选项出产品；LITEON/MEGMEET 给量产节点 2027 Q2–Q3 | 〔P252〕〔P295〕〔P306〕〔P023〕〔P304〕〔P320〕〔P299〕 |
| SST | Luxshare、Delta、MEGMEET、Edged | Luxshare 主打交期 4 个月；Edged 主打多端口晚绑定 | 〔P303〕〔P297〕〔P312〕 |
| 配电与保护 | Schneider、Eaton、Siemens、ABB、Vertiv、Phoenix Contact | 强调系统级协调与安全；Phoenix 引工业 700 V DC 工厂经验 | 〔P191〕〔P246〕〔P189〕〔P036〕〔P205〕〔P280〕 |
| 连接器/母线 | TE、BizLink、Rittal | 800 V 母线接口、硅胶线缆、RiLineX | 〔P025〕〔P263〕〔P239〕 |
| 储能 | Panasonic、Skeleton、Echion、ZincFive、EPC Power | 竞争点在循环寿命与功率密度 | 〔P026〕〔P196〕〔P182〕〔P188〕〔P176〕 |
| CDU/冷却 | Nidec（>13,000 台出货自报）、Vertiv、Envicool、Supermicro、Aivres | 行间 CDU 走向 2–15 MW | 〔P314 p7〕〔P245〕〔P265〕〔P291〕 |
| 冷板 | CoolIT、Corintis、Frore、Auras、HFH、ZutaCore | 单相延伸（CoolIT 15 kW）与两相/微通道并存 | 〔P310〕〔P010〕〔P300〕〔P251〕〔P302〕〔P322〕 |
| 流体/化学 | Ecolab、Castrol、Dow、ChemTreat、ExxonMobil、Shell、Evonik 等 | 推动流体分类与测试方法 | 〔P324〕〔P008〕〔P400〕〔P226〕〔P232〕 |
| ODM/集成 | Wiwynn、Foxconn、Jabil、Supermicro、HPE、Crusoe | 工厂集成、自动化、整柜交付 | 〔P222〕〔P261〕〔P124〕〔P265〕〔P034〕〔P390〕 |

### 4.3 OCP 标准与工作组进展

| 领域 | 文档/工作组 | 状态 | 索引 |
|---|---|---|---|
| LVDC 配电 | Power Distribution 子项目白皮书（250 页，v1.1 2026-09）；系统/组件规范 v0.5，2027 v1.0 | 进行中 | 〔P036 p6, p22〕〔P200〕 |
| SST | SST Specification Rev 0.3 | 征求意见 | 〔P199 p7〕 |
| 电网接口 | Hyperscaler-电网扰动性能接口规范 V1.0.0；Energy 子项目 Q2 启动 | 已贡献 | 〔P368 p9〕 |
| 板载电源 | ±400V/800V 板载模块工作组 | 2026 Q4 启动，2H 2027 发布 | 〔P190 p12〕 |
| 储能安全 | Requirements for ESS Used in Data Centers Rev 1.0 | 已发布 | 〔P186 p7〕 |
| 机架 | ORW v1.0.0；Open DC v0.7；MGX 1.2 | 已发布/评审 | 〔P030〕〔P180〕〔P367〕 |
| 冷板流体 | PG25 Base Spec 2026-08；水基冷却液基础规范 2026-08；水基指南 2026-11 | 已发布/待发 | 〔P400 p4〕〔P003 p23〕 |
| QD | UQD V2.0.0、PBMC（2026）、MQD（WIP 2026）、MiniQD（WIP 2027） | 部分发布 | 〔P003 p56〕 |
| CDU | Deschutes、Brazos 已发布；CDU 白皮书 2026-11 | 进行中 | 〔P209 p3, p5〕 |
| Door HX | Rev 1.0 目标 2026 Q4 | 进行中 | 〔P211 p11〕 |
| 浸没 | Immersion Requirements Rev 3 更新中；材料兼容数据库 570 条观测 | 进行中 | 〔P226 p13〕〔P236 p6〕 |
| 交叉 | ASHRAE–OCP MoU，TC9.9 联络人；ASTM D27.04 启动 2 项标准 | 已签/启动 | 〔P210 p39, p49〕 |

## 5. 分歧与未决问题

1. **设施级原生 800 VDC 是否一步到位。** Google/NVIDIA 主张集中式 SST + 原生 LVDC，2029+ GW 级部署〔P201 p11〕〔P260 p15–p18〕。Edged 认为设施级原生 800 VDC 忽略仍用 AC 的机械/网络/存储负载，首例规模化风险高，主张可互换的晚绑定架构〔P312 p3, p4〕；Vertiv 主张固定接口按未来负载设计、可变接口留作替换，过渡期双额定或混合母线槽〔P299 p5, p7〕。未决原因：SST 规范仍为 Rev 0.3，Power Block 设备 2028 Q1 才就绪〔P199〕〔P167 p17〕。
2. **2-wire 800 V 还是 ±400 V，接地方式怎么选。** Mt Diablo/Diablo 400 为 ±400 V〔P205 p3〕，SST 规范为 800 Vdc 单极〔P199 p7〕；Siemens 对比两者各有代价〔P189 p4〕；Eaton 称三种接地没有通用最优〔P246 p16〕；NVIDIA 指出固态接地会把 busway 长度限制在约 26 m〔P194 p16〕；DC Opportunities 建议设备兼容 700/1400 V TN-S〔P206 p12〕。未决原因：分支保护在 800 V 以上有标准缺口〔P191 p17〕，DC 电弧分析方法不覆盖变换器源〔P193 p4〕。
3. **功率平滑放在软件、GPU、机架还是设施。** Google 认为软件平滑有性能代价，硬件本地储能无性能损失〔P178 p5〕；NVIDIA 同时推 GPU 爬升控制 + 机架储能（IPS）和站级 EMS + BESS〔P389〕〔P197 p13〕；Schneider 认为 UPS 电池扩容（0.1–0.15 \$/W）比新增 BESS（0.3–0.6 \$/W）便宜〔P173 p15〕；Echion 认为 UPS 应按对称功率与循环寿命定容〔P182 p4〕。储能化学（LFP、NCA/LFP 复合、XNO、EDLC）各家数据口径不同，Echion 的 10 年成本只计电芯、未折现〔P182 p10〕。
4. **单相冷板还能走多远。** Promersion/白皮书称单相已进入回避区〔P218 p24〕；CoolIT 称单相 DLC 是未来平台，并展示 15 kW 冷板验证〔P310 p14, p26〕；Wiwynn 实验显示两相工质在同冷板下结温未必更低〔P012 p9〕；Meta 指出 TIM 和硅占热阻一半以上，冷板改进空间有限〔P010 p27〕。分歧部分来自"冷板"口径：CoolIT 的 15 kW 针对整封装，白皮书按每 reticle 级器件计。
5. **水基还是 PG25，蒸发还是干冷。** Ecolab 认为水基导热更好但需更强生物控制〔P324 p7, p10〕；OCP 同时发布两类基础规范〔P400 p4〕。排热侧 Daikin 仿真显示 PJM East、ERCOT 偏向干冷〔P083 p10〕，NVIDIA S45 方案零水耗〔P177 p2〕；Oracle/Vertiv 主张按区域水压力选型〔P094 p7〕。用水口径也不统一：现场 vs 电源侧用水合计 750–1,240 gal/MWh（蒸发）〔P170 p4〕，上游供应链占 77%〔P082 p3〕。
6. **浸没的可靠性证据强度。** Promersion 引用最高 12× MTBF 的队列观察〔P233 p13〕；Intel IRDT 给出 24 台服务器 MTBF（80% LCL）39,471 h、1 年服务器存活率 80%〔P235 p16〕，两者统计口径不同，无法直接比。Intel 呼吁统一浸没可靠性统计方法〔P235 p18〕。
7. **需求总量。** McKinsey 2025 年 171 GW〔P396 p2〕、JCI 汇总 77 GW〔P397 p4〕、Epoch AI 2025Q4 AI 数据中心约 31 GW〔P240 p4〕，口径分别为 IT 算力需求、数据中心容量、AI 专用容量，不应并列比较。

## 6. 判断与时间线

### 6.1 未来 12–36 个月里程碑

| 时间 | 事件 | 依据 |
|---|---|---|
| 2026-10 | OCP VRT & PFAPR v1.0 发布；PG25 混用 Phase 1 结果 | 〔P198 p9〕〔P217 p8〕 |
| 2026 Q3 | NVIDIA 800 VDC Option A Power Rack 设备就绪 | 〔P167 p17〕 |
| 2026-11 | ORW 量产开始；LITEON 220 kW 电源架样机测试；CDU 详细白皮书；水基冷却液指南 | 〔P030 p11〕〔P295 p4〕〔P209 p5〕〔P003 p23〕 |
| 2026 Q4 | 板载电源工作组启动；Door HX Rev 1.0；Clean Backup v1.0；实时流体监测指南 | 〔P190 p3〕〔P211 p11〕〔P096 p13〕〔P007 p18〕 |
| 2026-12-31 | NERC 提交计算负载可靠性标准（FERC 要求） | 〔P197 p6〕 |
| 2027 Q1 | Power Ramp & Fluctuations v1.0；Schneider 模块化 AC PDU 原型反馈 | 〔P198 p9〕〔P035 p19〕 |
| 2027 Q2 | NVIDIA Option B Power Center 就绪；LITEON 220 kW 架、CBU 架量产 | 〔P167 p17〕〔P295 p4, p5〕 |
| 2027 | LVDC 规范 v1.0 与 UL/IEC/IEEE 标准化；Microsoft Maia 300 多 GW 部署起步 | 〔P036 p22〕〔P369 p9〕 |
| 2H 2027 | ±400V/800V 板载电源模块规格发布 | 〔P190 p12〕 |
| 2027–2028 | LVDC 数据中心级验证；浸没进入产业化阶段 | 〔P201 p11〕〔P233 p16〕 |
| 2028 Q1 | NVIDIA Option C SST Power Block 就绪 | 〔P167 p17〕〔P252 p23〕 |
| 2028+ | Open DC 2028+ 基线（335 kW/ft 液冷）；单宽机柜 >4,000 kg（预测） | 〔P180 p3〕〔P222 p3〕 |
| 约 2029 | 单相冷板按趋势触及约 4 kW/reticle 物理墙；GW 级 LVDC 原生规模部署 | 〔P218 p15〕〔P201 p11〕 |

### 6.2 对各类厂商的含义

- **设备商（电源/配电/冷却）**：2027 年是 800 VDC 机架级与集群级产品量产窗口，竞争点从峰值效率转向全工作范围效率、与储能/保护的系统协同和通过并网仿真的能力〔P304 p4〕〔P197 p9〕。CDU 与 QD 的竞争点转向互操作测试与清洁度证据链〔P003 p50〕〔P283 p11〕。
- **光模块商**：模块功耗越过 35 W 后必须进入液冷体系（笼外冷板 35–50 W，模块内液冷 120–500 W）〔P005 p3〕；网络机架液冷化和 2,000–8,000 根光纤/柜的预布线，使工厂级光纤清洁与管理成为交付条件〔P124 p4〕〔P407 p12〕〔P266 p5〕。浸没环境下光模块兼容性已列入部件兼容白皮书〔P236 p9〕。
- **芯片商**：2 kW 级封装下 TIM 与硅自身热阻成为主要部分〔P010 p27〕，VPD 电流密度要到 3 A/mm²〔P466 p5〕；GPU 功率爬升/下降特性已写入机架与电网接口要求（EDPP、20 W/s 示例配置）〔P194 p4〕〔P389 p7〕，芯片侧功率管理功能成为并网合规的一部分。

## 7. 推荐配图清单

| 索引 | 图中内容 |
|---|---|
| 〔P167 p3〕 | NVIDIA 机柜功率代际 Gen1–Gen4 与 800 VDC 必要性 |
| 〔P167 p17〕 | 800 VDC A/B/C 选项设备就绪时间线 |
| 〔P201 p11〕 | LVDC 从研发到 GW 级部署的四阶段 |
| 〔P031 p4〕 | 800 kW 风冷 vs 液冷所需风量/液量 |
| 〔P028 p6〕 | 各电网负载变化限值表 |
| 〔P197 p3〕 | 2024–2026 数据中心自发减载事件清单 |
| 〔P389 p5〕 | Vera-Rubin 机架 IPS ON/OFF 功率曲线 |
| 〔P182 p9〕 | 280 MW 机房有/无缓冲的功率与频率对比 |
| 〔P199 p7〕 | SST 规格对齐表 |
| 〔P191 p11〕 | 四类 DC 保护器件分断时间对比 |
| 〔P218 p24〕 | 单相/两相冷板三条边界与 2.3 kW 加速器标线 |
| 〔P218 p16〕 | 冷板占顶级加速器 TDP 比例 S 曲线 |
| 〔P010 p27〕 | 结到冷却液热阻构成（冷板/TIM/硅） |
| 〔P006 p4〕 | PG 浓度与微生物计数散点 |
| 〔P003 p56〕 | OCP QD 规范族与时间线 |
| 〔P181 p3〕 | 预调试 7 周→1 周与延迟成本 |
| 〔P005 p3〕 | I/O 模块 TDP 随 SerDes 演进及各冷却方式上限 |
| 〔P030 p6〕 | ORW 与 ORv3 HPR 规格对比 |
| 〔P180 p4〕 | Open DC 2027/2028+ 密度与集群基线 |
| 〔P124 p3〕 | 旧/新网络交换机与机架（光纤数、液冷）对比 |
| 〔P222 p3〕 | 机柜重量增长曲线 |
| 〔P303 p4〕 | 传统多级 vs SST 单级：效率、占地、交期 |
| 〔P184 p13〕 | 四种供电架构 LCOE（含芯片机会成本） |

## 8. 底座对 Scale-across / out / up / in 的约束

本方向在 ECOC 无对应底稿，本节改为底座条件如何决定网络与互连选型。标"推断"处为本稿据材料作出的连接，材料本身未直接表述。

### 8.1 Scale-across：园区电力上限决定"跨"的起点

1. **单楼/单园区电力不够，是跨楼跨区域的直接原因。** Google 称 Virgo scale-out fabric 限定在单楼内，跨楼需求来自楼宇面积或功率预算〔T06 01:52〕；Microsoft 称电力分布不均，算力只能跟着电走，必须跨园区、跨区域〔T06 18:27–23:58〕。Meta Prometheus 1 GW 跨传统楼宇、户外帐篷和相邻托管设施，经 BAG 互连〔P424 p4〕〔P364 p2, p11〕。
2. **并网时长把分散站点变成常态。** 美国能量接入最长 4–5 年，65% 的玩家部署现场发电〔P396 p4〕；CMU 仿真中电网接入 4 年、光储微电网 2 年〔P184 p13〕；NVIDIA 称约束已从发电转为并网排队〔P171 p2〕。推断：电力可得性而非距离成本决定站点位置，scale-across 链路长度由电力选址倒推，ZR/ZR+ 与深缓冲交换的需求随之上升（Meta BAG 用 FR4 ≤3 km、LR4 ≤10 km、ZR+ ≤1,000 km 混用〔P424 p10〕）。
3. **建筑标准化单元决定跨楼汇聚的粒度。** Open DC 集群基线 12 MW、优选 24 MW〔P180 p4〕；NVIDIA 16 MW 部署单元、4×4 MW 可扩展单元〔P367 p8〕。推断：BAG/汇聚层的端口规划会对齐这些电力块，跨单元带宽按模型副本放置计算（Meta：副本放 L2 内，跨副本 DP 走 BAG）〔P424 p12〕。
4. **相干可插拔进入液冷体系。** Ciena：1600 ZR/ZR+ OSFP（2027）约 33–42 W（看图）〔P447 p8〕，而风冷模块 >35 W 从未出货〔P005 p4〕；XPO 液冷 12.8T 承载 Linear/Coherent-Lite/ZR 三类〔P447 p11〕。DCI 路由器端口密度因此受液冷可用性约束。
5. **hyperscale adjacent 站点功率很低。** AICC 场景 8×GPU scale-up 仅 8–15 kW，scale-across 互连 100GbE+ 级〔P159 p6, p7〕，这类站点受功率和风冷限制，互连选型偏向现有以太网与 APN，而不是高功耗相干端口（推断）。

### 8.2 Scale-out：液冷与光纤数量重塑网络机架

1. **网络机架变成液冷整柜交付。** Arista/Jabil：102.4T 及以上、ASIC >1,000 W、液冷、机架 2,000+ 根光纤，网络机架 50 kW+/机架〔P124 p3, p4〕；Meta IcePack 为首个液冷网络机柜〔P244 p8〕；IceCube 刀片 ASIC 与 OSFP 约 85% 液冷、最大典型功率 3,820 W〔P407 p4, p9〕。网络设备选型必须匹配机房的液冷 manifold 与 QD 接口，而 manifold 目前只针对 2U 交换机〔P124 p8〕。
2. **每柜光纤数逼近布线空间上限。** Sumitomo：每 GPU 机柜后端光纤 Hopper 约 576 → GB200 2,308 → Rubin 4,616 → Feynman 18,464 芯（预测），6,912 芯单芯光缆 OD 约 37 mm vs 4 芯 MCF 约 13 mm〔P316 p3, p8〕；Meta GTSW 机柜内 8,192 根光纤需在集成商处预布线〔P407 p12〕。这直接推动 MCF、MMC 等高密连接和工厂预端接。
3. **从风冷 400G 到液冷 800G/1.6T 需要重做集群网络。** Open Cluster Designs 称这是"非常大的转变"，风冷 OPG-128 已发布，液冷 OPG-576 在开发〔P119 p6–p7〕。CLARA 平面图代价函数同时含网络长度与 CDU 管长〔P118 p11〕，说明机柜排布同时受冷却管路和光缆长度约束。
4. **光模块液冷是可插拔继续存在的条件。** 224G 以上、1.6T 以上可插拔已到风冷极限〔P005 p4〕；Luxshare 液冷 OSFP 2×8 笼 16 个模块压降 ≤35 kPa〔P256 p6〕；OCP NIC 需 200 W 连接器与液冷参考设计〔P453 p8〕。
5. **网络在功率预算中占比小，但受电网与冷却挤压。** Epoch AI 估算 GB200 NVL72 数据中心峰值电力中网络与其他 IT 约 8%〔P240 p11〕；MaxLPS 等动态分配把搁浅功率转给 GPU〔P257 p5〕。推断：网络功耗的约束更多体现在液冷接口和机柜位，而非总电力。
6. **工厂集成的物理细节成为交付风险。** 交换机冷板充氮存放的衰减率不一、光纤灰尘清洁协议未定义〔P266 p5〕；OCI 称光链路瞬态故障会扩散为 fabric 级中断，灰尘是原因之一〔P370 p20–p22〕。

### 8.3 Scale-up：机柜功率、重量与布线决定域的边界

1. **铜 scale-up 域受机柜重量与线缆数量限制。** Celestica 材料：单个 scale-up 机柜约 5,000 根无源铜缆，约 1 MW 液冷机柜，重量今天约 4,000 lb、设计目标 8,000 lb〔P253 p15〕；MGX 1.2 需 6,000 lb 插拔力锁扣杆和加强钢结构〔P367 p6〕；ORW 载荷 4,700 kg〔P030 p6〕；Open DC ML 机架+sidecar 15,000 lb〔P180 p5〕。楼板承重与机架结构因此成为铜背板继续扩域的硬约束（Wiwynn 称 AI 机柜重量逼近楼板承重极限〔P222 p3〕）。
2. **功率等级与 scale-up 规模对应。** Lightmatter/Dell：ORv3 MHS Class-H 600 kW+ 对应 72–144 XPU，Class-V 1 MW+ 对应 1,024–1,152+ XPU〔P455 p11〕；NVL72 铜约 1 m 单柜 vs CPO 1,152 GPU/16 柜/约 1 km（引用 SemiAnalysis，看图）〔P455 p10〕。超出单柜功率与重量后，scale-up 必须走光并跨柜。
3. **跨柜光 scale-up 的光纤数量。** Broadcom：1,024 XPU scale-up 示例每 GPU 128 根光纤、每交换机 1,024 根，每机架 8,192 / 32,768 根〔P433 p14〕；每芯片封装 >1k 根光纤且需可拆卸以便回流焊〔P253 p10〕。这与 8.2 的布线空间约束叠加。
4. **sidecar 与电源柜占用机柜位。** NVIDIA 计算:电源柜 4:1〔P269 p4〕；Rittal sidecar 额定最高 2 MW〔P239 p8〕；单相 AALC sidecar 需 10+ 机架宽度才做到 1 MW〔P211 p8〕。推断：电源与冷却 sidecar 插在计算柜之间，会拉长柜间距离，影响铜缆可达范围和跨柜 scale-up 的线缆长度预算。
5. **热通道/冷通道与运输通道尺寸约束整排布局。** Open DC 热通道 54"、冷通道 82"、运输通道 12'〔P180 p6〕；NVIDIA NVL576 CPO 以 8 柜一排呈现〔P367 p18〕。排级尺寸决定 scale-up 光缆长度与托盘维护方式（推断）。

### 8.4 Scale-in：封装热流与供电争夺芯片边缘与面积

1. **封装功率逼近冷板极限。** 2026 领先加速器约 2.3 kW，单相冷板物理边界约 4 kW/reticle〔P218 p24〕；GUC System on Wafer TDP 20 kW、峰值 30 kW〔P075 p13〕；CoolIT 引用 2030 TDP 散点最高约 14,000 W〔P310 p3〕。封装规模与 chiplet 数量的上限受冷却能力约束。
2. **HBM 是热瓶颈。** HBM 堆栈占 2.5D 封装热阻 57%，8→16-high HBM 到 2028 越过热预算（引用 ECTC 2026）〔P070 p7〕；DRAM-on-Compute 最高温 125℃ vs HBM4E 95℃（自报）〔P075 p8〕。内存堆叠高度与带宽路线需要与冷却方案协同。
3. **供电电流密度上升，推动 VPD。** AMD 二级电流密度到 2 A/mm²、目标 3 A/mm²，<50 µΩ PDN 支撑 >2 kA〔P466 p3, p4〕；4,000 A 时 200 µΩ 损耗约 3,200 W（看图）〔P466 p4〕；GUC 称数 kW ASIC 必须垂直供电〔P075 p14〕。
4. **封装边缘被 HBM PHY 占用，光 I/O 需改走面阵。** 224G、reticle 级封装铜逃逸 26 Tb/s/dir，CPO 93.6，面阵 APO 1,191（引用白皮书）；HBM PHY 先占边缘〔P455 p2〕。推断：VPD 从封装下方供电、面阵光 I/O 也需要占用封装面积或背面，两者在封装平面上的分配尚无材料给出方案，属未决问题。
5. **光引擎与 DSP 热流需要专门冷却。** DSP 热流密度 100+ W/cm²〔P005 p4〕；HFH 光模块 TIM 在 30 W 下 ΔT 3–6℃，插拔寿命 200–500 次（看图）〔P302 p16〕。CPO 把光引擎放进封装后，其热预算并入芯片冷板（推断，依据 P455 托盘契约含热维度〔P455 p6〕）。

## 索引对照表

| 索引 | 机构 | 题目简写 |
|---|---|---|
| P001 | Wistron | 负压两相水沸腾冷板 |
| P002 | Goaland / Watts EasyWater | 铜冷板无化学水质管理 |
| P003 | Intel、Dell 等 | Cold Plate 子项目更新 |
| P004 | Meta、NVIDIA | 单相冷板液冷机柜运输存储 |
| P005 | TE Connectivity | 448G 500 W 级 HSIO 直液冷 |
| P006 | Ecolab、NVIDIA | 液冷生物管理 |
| P007 | Nordran、Dynalene、Ecolab、Switch | 流体监测 |
| P008 | Castrol、Meta、SABIC | 流速与冲蚀 |
| P010 | Corintis、Meta、Microsoft、Google | 单相冷板极限面板 |
| P011 | Meta 等 | 两相冷板标准化面板 |
| P012 | Wiwynn | 单相到两相系统挑战 |
| P022 | TI | 800 V DC-DC 拓扑对比 |
| P023 | Advanced Energy | 800 V 直连服务器与电源架 |
| P025 | TE Connectivity | 1 MW+ 机柜母线接口 |
| P026 | Panasonic | 高功率 BBU/CBU |
| P027 | NVIDIA | MGX Power Rack 参考设计 |
| P028 | Microsoft | AI 训练功率振荡与机架滤波 |
| P030 | Meta、Rittal | ORW 进展 |
| P031 | Rittal、Bosch | 800 V DC sidecar |
| P032 | Advanced Energy、Rittal | Rack & Power 开场 |
| P033 | Microsoft | 聚合/级联电源架 |
| P034 | HPE | Cray GX 基础设施 |
| P035 | Schneider | 减少 AC whip |
| P036 | ABB 等 | Power Distribution 子项目 |
| P070 | Marvell | 定制 HBM 系统协同 |
| P075 | GUC | 算力/内存/连接扩展 |
| P082 | Kaya AI、Ecolab | 供应链水足迹 |
| P083 | Daikin | 美国区域冷却权衡 |
| P084 | SDEA、SLAC、Oracle | DCEM 指标测量 |
| P085 | Microsoft | 废热回收 |
| P094 | Oracle、Vertiv | 水效最佳实践 |
| P096 | Schneider、Microsoft、Google、Castrol | Sustainability 项目更新 |
| P118 | Lenovo | CLARA 集群设计工具 |
| P119 | Celestica、Broadcom | Open Cluster Designs for AI |
| P124 | Arista、Jabil | 高功率液冷网络机架集成 |
| P159 | NTT、HPE、Intel | AI Computing Continuum |
| P160 | HPE、Intel | AI-Native Edge MHS 1.0 |
| P167 | NVIDIA | 800 VDC AI 工厂 |
| P170 | DLB 等 | 水-能耗面板 |
| P171 | NVIDIA | 可削减负载并网 |
| P172 | Phaidra | 开放系统与 IT/OT |
| P173 | Schneider | 800 V 平滑、FRT 与备电 |
| P174 | NVIDIA、Vertiv、Google 等 | 液冷数据中心调试 |
| P176 | EPC Power | 储能与电网合规 |
| P177 | NVIDIA | 排热系统多指标分析 |
| P178 | Google | AI 负载功率波动硬件缓解 |
| P180 | Google、Meta、NVIDIA、AMD | Open DC 架构 |
| P181 | Victaulic、Vertiv、AMD 等 | 模块化 TCS 工作流 |
| P182 | Echion、Proper Voltage | 兆瓦机柜对称 UPS |
| P183 | PMG、Vertiv、VEIR | 250 MW 参考架构（HTS） |
| P184 | Carnegie Mellon | DC/AC 光储微电网技术经济 |
| P186 | 面板（Digital Realty 等） | ESS 合规缺口 |
| P187 | Microsoft、Google | 高温燃料电池 |
| P188 | ZincFive 等 | ESS 安全 |
| P189 | Siemens | 800 VDC 2 线/3 线接地 |
| P190 | Google、Microsoft、Meta | 400V/800V 板载电源要求 |
| P191 | Schneider | 800 VDC 保护协调 |
| P192 | UL Solutions | LVDC 标准缺口 |
| P193 | Schneider | DC 电弧闪光测试 |
| P194 | NVIDIA | 800 VDC 端到端性能要求 |
| P195 | Microsoft、NVIDIA | 800 VDC 安全设计 |
| P196 | Siemens、Skeleton | 600 kW 800 VDC sidecar |
| P197 | NVIDIA、Danovo、Equinix | 大负载并网要求 |
| P198 | Google | AI/ML 负载电网要求与缓解 |
| P199 | Google、NVIDIA | SST 接入 LVDC |
| P200 | Siemens、Direct Energy Partners | LVDC 架构基础 |
| P201 | Google、NVIDIA | LVDC 开放生态 |
| P202 | VEIR、RED | HTS 配电 RAM |
| P203 | Google | 800 V LVDC 安全 |
| P205 | Vertiv | SSCB 与 DC Fault Manager |
| P206 | DC Opportunities | LVDC 至 1500 V |
| P208 | Microsoft | 废热生态 |
| P209 | Dell、Google | CDU 子项目 |
| P210 | Meta、NVIDIA 等 | Cooling Environments 开场与闪电演讲 |
| P211 | LGTS、OVHCloud、AMD、Meta 等 | Door HX 子项目 |
| P214 | Gamma、Alfa Laval | CDU 设计选择对比 |
| P215 | Microsoft、Lenovo | 风冷 vs 液冷（通用计算） |
| P217 | Meta、Castrol | PG25 混用阈值 |
| P218 | Promersion、Oracle、Meta、Avayla | 液冷市场与 Thermal Boundaries |
| P220 | Meta | 规模化液冷运维 |
| P221 | Gates | 流速限值 |
| P222 | Wiwynn | 机柜减重 |
| P226 | Fluids TC | 浸没流体工作流 |
| P227 | UNICOM | 浸没 ITE 工作流 |
| P228 | Denvr、UNICOM | 浸没原生 ITE |
| P229 | Magnalytix、ExxonMobil | 流体氧化与电气可靠性 |
| P231 | Samsung | 两相浸没 SSD |
| P233 | Promersion、Eaton 等 | OCP 浸没项目 |
| P234 | SwRI | 浸没流体联盟 |
| P235 | Intel、ExxonMobil | 浸没机柜级可靠性演示 |
| P236 | Intel 等 | 热化学可靠性工作流 |
| P238 | Foxconn Interconnect | 高密液冷 XPO |
| P239 | Rittal | AI 基础设施系统方法 |
| P240 | QCT | 系统到 AI 工厂 |
| P244 | Meta | 全栈开放 AI 网络 |
| P245 | Envicool | 规模化液冷 |
| P246 | Eaton | 800 V DC 安全生态 |
| P249 | Gates | 软管材料与冷却液化学 |
| P251 | Auras | 先进液冷 |
| P252 | Delta、NVIDIA | 800 VDC 电源与冷却 |
| P253 | Celestica | 计算与光学融合的 AI fabric |
| P256 | Luxshare-Tech | 1600G 光模块液冷 |
| P257 | NVIDIA | DSX MaxLPS |
| P260 | Google、OCP | 芯片到电网协同 |
| P261 | Foxconn Industrial Internet | GW 速度交付 |
| P262 | Axiom（Flex） | 从土地到 token |
| P263 | BizLink | 从电网到比特 |
| P265 | Supermicro | DCBBS 模块化 |
| P266 | Arista、Jabil | 交换机到系统 |
| P269 | NVIDIA、MEGMEET | 液冷电源架与 800 VDC |
| P271 | xFusion | 下一代电源与冷却 |
| P272 | nVent | Helios RDHX |
| P276 | LITEON-EPIC、Cambridge | 800 V 到芯片 |
| P280 | Phoenix Contact | 工业直流经验 |
| P283 | Danfoss | 标准化与部署信心 |
| P291 | Aivres | 液冷 AIDC 方案 |
| P295 | LITEON | 1 MW 电源机架 |
| P297 | Delta | 规模化微电网 |
| P299 | Vertiv | 800 VDC 过渡 |
| P300 | Frore | 热的隐性成本 |
| P302 | HFH Thermal | 冷却系统创新 |
| P303 | Luxshare-Tech | 中压直转 800 VDC |
| P304 | OmniOn | 全工作范围效率 |
| P306 | MEGMEET | 800 VDC 过渡工程 |
| P310 | CoolIT | 无风扇服务器外围冷板 |
| P312 | Edged | 可互换电力架构 |
| P314 | Nidec | 高可靠液冷 |
| P316 | Sumitomo Electric | 多芯光纤 |
| P320 | Murata | OCP 电源 |
| P322 | MiTAC、AMD | 先进冷却 |
| P324 | Ecolab | 水 vs 乙二醇 |
| P351 | 多家 | Sustainability 闪电演讲 |
| P364 | Meta | GW 级 AI 基础设施 |
| P367 | NVIDIA | AI 工厂规模化 |
| P368 | OCP Foundation | 第二天开场 |
| P369 | Microsoft | 智能时代基础设施 |
| P370 | Oracle OCI | 开放标准与光可靠性 |
| P375 | Power Distribution 子项目 | 转向 DC 配电 |
| P386 | Denvr | 主权 AI 实施 |
| P387 | Kele | 项目到平台 |
| P389 | NVIDIA | Vera-Rubin 智能功率平滑 |
| P390 | Crusoe | 工厂单元构建集群 |
| P391 | AMD、Dell | OAC 小 pod 到企业 |
| P392 | EPRI | 标准化以加快获电 |
| P396 | McKinsey | 需求到交付价值链 |
| P397 | Johnson Controls | 同兆瓦更多 token |
| P400 | AMD、Vertiv、Microsoft 等 | PG25 规模化 |
| P402 | Meta | BOM 交换标准 |
| P407 | Meta | 102.4T 以太网交换机 |
| P413 | Meta、Microsoft、Alibaba | 交换机平台架构 OSPA |
| P424 | Meta | BAG 跨 DC 扩展 |
| P433 | Broadcom | CPO、OCI |
| P447 | Ciena | AI 时代相干光 |
| P453 | Intel、Dell | OCP NIC Gen 7 与液冷 |
| P455 | Lightmatter、Dell | 开放硅光与 MHS 契约 |
| P465 | AMD、Intel | OAC 子机柜加速 |
| P466 | AMD | 高密度供电架构 |
| T06 | Google、Microsoft、Meta、Broadcom、Arista | Scale-across 面板视频转写（对应 P147） |
