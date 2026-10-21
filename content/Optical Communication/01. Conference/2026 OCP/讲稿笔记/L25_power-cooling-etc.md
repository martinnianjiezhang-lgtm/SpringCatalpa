---
title: "L25_power-cooling-etc"
tags:
  - OCP2026
  - 讲稿笔记
---

# L25 笔记：expo-hall-sessions / fts-keynotes-awards / fts-quantum-data-center-design / keynotes / manageability-workshop / market-impact-adoption / networking / server（低相关批次，精简版）

### P300 Burning Cash- The Hidden Cost of Ignoring Thermal in Your AI Strategy presented by Frore
- 讲者/机构：Dr. Seshu Madhavapeddy，CEO & Founder，Frore Systems [p1] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-冷却]；次 [推理/算力/经济性]
- 核心主张：① AI Factory 唯一指标是 Tokens/Watt，世界受电力约束 [p3]；② 热栈（GPU→TIM→Coldplate→Coolant→Free Cooling→Chiller）是剩余的效率杠杆，优化后 Tokens/Watt 可提升 40% 以上 [p6,p14]
- 关键数据：
  - Tokens/Watt 随 GPU 平均结温 TjA 下降：约65℃以内≈100%，约87℃≈80%，95℃≈66% [p4，看图，读图估计]
  - 各环节增益（自报）：GPU 去盖（un-lidded）+20% [p8]；液态金属 TIM +10% [p9]；进水温度每低1℃ +1%（前提：降温不额外耗电）[p10]；流量翻倍 +10% [p11]；Frore coldplate +35% [p12]
  - LiquidJet 冷板：GPU 低 16–22℃，Tokens/Watt +30–35% [p13，自报]
  - 组合对比 [p14，自报]：LiquidJet+液态金属TIM+去盖封装 → 比基线低33℃、+43%；LiquidJet+PTM7950 TIM+带盖封装 → 低18℃、+35%（基线：skived coldplate+PTM7950+带盖）
- 提到的公司/客户/产品/标准：Frore Systems、AirJet、LiquidJet、PTM7950
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（Tokens/Watt vs 结温曲线）、p14（热栈累计增益对比）

### P303 Direct-Medium-Voltage-to-800VDC-Conversion-for-AI-Data-Centers-presented-by-Luxshare-Tech
- 讲者/机构：Jingkui Shi，CEO，Luxshare-Tech & Zinsight Joint Venture [p1] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：① AI 机架逼近 1 MW，低压交流配电电流大、占地大；变压器交期成为排期瓶颈 [p2,p3]；② 用 SST 把中压直接转 800 VDC，取代多级转换 [p4]
- 关键数据：
  - 美国数据中心年新增容量 6.4 GW(2024)→36.3 GW(2027F)，5.7×（引 Goldman Sachs）[p3]；美国变压器交期 128 周（引 Industrialsage 报告）[p3]
  - 35 kV/10 MW：传统架构系统效率 93.3%、占地 188 m²、交期 24–30 个月；Nova Link SST 98.7%、9.6 m²、交期 4 个月 [p4，自报]
  - 35 kV/420 kW 液冷功率单元：峰值效率 99.0%，420 kW/216 L=1.94 kW/L，2.3 kV SiC MOSFET [p8，自报]
  - Nova Link 35 kV/10 MW：98.7%，1.04 MW/m²，800/1500 VDC 输出，符合 OCP SST Spec V0.3 [p9]；13.8 kV/3 MW 风冷：98.8%，1.11 MW/m² [p10]
  - 下一代目标：99% 效率、1.5 MW/m² [p11]
- 提到的公司/客户/产品/标准：Nova Link、ZPAK SiC 模块、NVIDIA 800 VDC、OCP SST Spec V0.3
- 首次/记录/SOTA 声明：无（p11 与公开 benchmark 对比，注明数据来自公开报告）
- 推荐配图页：p4（传统多级 vs SST 单级架构对比及指标）、p11（SST 效率-功率密度基准图）

### P304 Driving Efficiency Through Innovation Across the Operating Range and Power Chain, Aligning Power
- 讲者/机构：Philip Zuk，SVP & GM AIDC BU，OmniOn Power [p1] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：① AI 负载电流快速摆动，没有稳定50%负载点，应以全工作范围的时间加权效率而非单点峰值为目标 [p4,p8]；② 48V 架构需逐级优化，SiC 与 GaN 两条路径性能相近 [p6,p12]
- 关键数据：
  - 80 PLUS Titanium 230V：96%@50% 负载，94%@20%，91%@100% [p4]
  - SiC vs GaN @277Vac：10%负载 95.54% vs 95.85%；50% 97.65% vs 97.60%；100% 96.38% vs 96.23%，差距≤0.3 点；测试条件不同（GaN 为第三方12kW参考设计，不含风扇），厂商自注"非同口径对比" [p6]
  - LLM 负载下 GPU 利用率约15–45%摆动；54V→12V DC/DC 30–100%负载保持>98% [p8，自报/引NVIDIA trace]
  - 效率波动：OmniOn 0.23 点 vs 竞品 0.61 点（50–108A）[p9，自报，图为看图]；示意场景 5年NPV \$1.8M（1000机架、132kW/机架、PUE 1.3、\$0.05/kWh、8%）[p9，场景假设]
  - Osprey 50V→12V：1.3–3.5 kW；50%/100%负载效率 98.5%/97.9%；峰值 4.0kW@3ms；QODN217A0B 2.6kW [p10,p11]；3.5kW 型号开发中 [p11]
- 提到的公司/客户/产品/标准：OmniOn Power、Osprey、80 PLUS Titanium/Ruby、NVIDIA LLM 负载 trace、Kinpo/Compal 工厂
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（SiC vs GaN 效率曲线）、p9（效率平坦度对比）

### P306 Engineering-the-Transition-to-800-VDC-presented-by-MEGMEET
- 讲者/机构：MEGMEET（讲者姓名未见）[p1] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：① 800 VDC 有三种部署选项：A 机架级（Power Rack）、B 集群级（Power Center）、C 下一代（室外 SST 容器）[p5,p8,p9]；② 提供空冷/液冷两种 800VDC 电源架 [p7]
- 关键数据：
  - 公司：营收 \$1.3B，10K+员工，研发占比34% [p2，自报]
  - 现有AC方案：GB200/GB300 33kW 电源架，Vera Rubin 110kW 电源架，5.5kW M-CRPS [p4]
  - 800VDC 方案：110kW 风冷6RU AC-800VDC 电源架；90kW 风冷1RU 800VDC-50VDC 电源架；100kW 液冷5RU、95kW 液冷1RU 版本 [p7]
  - 6个整流槽、每个15kW子模块；峰值效率最高98% [p7]
- 提到的公司/客户/产品/标准：GB200/GB300、Vera Rubin、80 PLUS Ruby、UQD08、IEC 62368
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（MEGMEET 数据中心电力总架构）

### P312 Fungible Power Architectures for the 800V DC Transition presented by Edged Infrastructure
- 讲者/机构：Wes Short（Sr Director, Infrastructure Projects）、James Feasey（Sr Director, AI Infrastructure），Edged Infrastructure [p1] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：① 设施级原生800VDC忽略仍用AC的机械/网络/存储负载，且首例规模化风险高 [p3]；② 主张"可互换（fungible）"基础设施、晚绑定架构，如多端口SST，类比向液冷的过渡 [p4]
- 关键数据：
  - 一个5MW单元（4个一组）：传统SST方案需为机械负载另设 500kVA 变压器+UPS（第二条供电链）；用 GridBlock 功率路由器接入800V DC母线后取消第二条链，~500kW GridBlock [p5,p6，自报]
  - 母线 800V/1500V；TurboCell 2.5 MW 母线 [p5，p7看图]
- 提到的公司/客户/产品/标准：GridBlock、GridTran(SST)、ThermalWorks、TurboCell(燃气轮机)、ISOVA(储能)
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（传统 SST vs GridBlock 单母线对比）

### P314 Liquid-Cooling-Designed-for-Maximum-Uptime-and-Reliability-presented-by-Nidec
- 讲者/机构：Nidec（首页写 OCP Global Summit 2026，Oct 15；p2 列 Senior Vice President Yuji Tanaka）| 类型：厂商展区
- 方向归属（主/次）：主 [底座-冷却]；次 [底座-电力]
- 核心主张：① CDU 从 In-Rack 到 In-Row 全系列覆盖，面向可靠性与可维护性 [p10-13]；② CDU 规划兼容 415VAC 与 800VDC [p14]
- 关键数据：
  - CDU 全球累计出货 >13,000 台 [p7，自报]
  - In-Rack CDU Gen 3.0：最大 300 kW，4U 19"，泵冗余可热插拔，支持 Redfish [p11]
  - In-Row：NIR2.5 2.0MW，NIR3.0 3.2MW，NIR3.0 S/D 6.4MW，NCCDU S/D 15MW [p12]
  - NIR3.0：3,200kW 下 approach temperature 3℃；THDi≤5% [p13]
  - 快接头（UQD/MQD）：Class-100 洁净室，100% 流体/气体泄漏测试 [p17]
  - p4 看图：BESS 10 MWh–2+ GWh；CDU 容量 3.2 MW [看图]
- 提到的公司/客户/产品/标准：Nidec、Takisawa、OCP UQD、MQD、Redfish、NVIDIA 800VDC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（热负荷-冷却产品谱系）、p4（Nidec 数据中心全景产品图）

### P315 Liquid-cooling Approaches for E1.S SSDs presented by KIOXIA
- 讲者/机构：Paul Wu，Product Manager, Data Center Division，KIOXIA America [p1] | 类型：厂商展区
- 方向归属（主/次）：主 [存储]；次 [底座-冷却]
- 核心主张：① 风冷 E1.S 在高功率下热节流，冷板 DLC 可维持稳定性能并提高功率上限 [p3,p4]；② NX1 按 SNIA SFF-TA-1006 Rev 2.0 设计，同一款SSD支持风冷与液冷系统 [p6]
- 关键数据：
  - 典型 E1.S 功率上限：风冷 ~20W，液冷 ~30W [p3，自报]
  - NX1：BiCS FLASH gen8 TLC，PCIe 5.0 x4，NVMe 2.0e，OCP Datacenter NVMe SSD Spec 2.6，最大 15.36TB，1 DWPD；仅 9.5mm 版本支持冷板 DLC [p5]
  - 正在开发 E3.S 直接液冷方案，对应 NVIDIA CMX 上下文内存存储平台 [p7]
- 提到的公司/客户/产品/标准：KIOXIA NX1、Cooler Master 冷板、SNIA SFF-TA-1006 Rev 2.0、NVIDIA CMX
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（风冷/液冷功率上限柱图）

### P320 Powering Progress- Murata's Role in Advancing OCP Innovation presented by Murata
- 讲者/机构：Kevin Gero（Sr Applications Marketing Mgr）、Miguel Millan Montanes（Applications Engineer），Murata [p1] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-电力]；次 [In 封装内]
- 核心主张：① 覆盖 AC 到 xPU：48/400/800V 配电、中间转换、GPU 轨 >1000A [p2]；② 芯片级趋势推动近负载稳压（VPD/iVR）与嵌入式无源器件 [p12]
- 关键数据：
  - ORV3 电源架 21.6kW（6×3.6kW）；ORV3 HPR 33kW（6×5.5kW，每个67mm宽）[p6,p7]
  - 路线图：OCP SPEC 12kW 50Vout PSU/72kW 机架电源架，110kW 19" 架在路线图 [p8]
  - 浸没式：54kW ORV3 Immersion Shelf、82.5kW HPR Immersion Shelf [p9]
  - 54V/5.5kW PSU 标"IQ4 26" [p8，看不清含义]
- 提到的公司/客户/产品/标准：Murata、ORV3、ORV3 HPR、MGX 机架、iPaS、Si-Cap
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（Murata 先进封装/chiplet 无源与热方案示意，看图）

### P322 Scaling-the-Future-of-Open-Infrastructure-with-Advanced-Cooling-presented-by-MiTAC
- 讲者/机构：Raymond Huang（GM, MiTAC Computing Technology USA）、Sachin Dhingra（Sr. Director, Enterprise AI Solutions, AMD）[p1]；Oct.14, 2026 | 类型：厂商展区
- 方向归属（主/次）：主 [底座-冷却]；次 [底座-机架/机械]、[推理/算力/经济性]
- 核心主张：① 开放架构提供扩展灵活性，但算力密度提高带来"热"约束 [p13]；② 开放基础设施包括冷板、冷却液、冷却架构（单相/两相/金刚石）的多源可选 [p14]
- 关键数据：
  - AMD 平台梯度：Instinct MI355X x8 为 AIR/LC 30–60kW 机架功率；AMD Helios 72×MI455X，液冷 100kW+，31TB 内存 [p9]
  - MI350P：风冷 450–600W TBP，最大 260B 参数(FP4)，相对 RTX Pro 6000 tokens/s/\$ 最高 4.2x [p12，自报]
  - 压降降低 44%，优化 CDU 功耗 [p16，自报]
  - Castrol PG25：45℃ 供液、3.5–5.5 LPM，各配比 ΔT 曲线基本重合，约 8.5→5.5–6℃ [p17，看图]
  - Akash 金刚石冷却（G8825Z5 8-GPU 服务器）：GPU 温度最多降 10℃；约75°F环境 FLOPs/Watt 最多 +22%；约120°F环境 token 吞吐最多 +15% [p18，看图，自报]
  - ZutaCore 两相：>4,000W 单芯片热余量、>250 W/cm²、年化 pPUE 1.03、较单相冷却能耗 -74% [p19，看图，自报]
- 提到的公司/客户/产品/标准：AMD Instinct MI355X/MI350P/Helios、EPYC 9005、Cooler Master、JWS、Castrol、PFX、CoolIT、Nidec、ZutaCore、Akash Systems、DDN Infinia
- 首次/记录/SOTA 声明："World's First Diamond Cooling"（Akash，p18，厂商自称）
- 推荐配图页：p14（冷板/冷却液/架构多源选择）、p19（两相 DLC 实测指标）

### P352 FTS-Awards-Ceremony
- 讲者/机构：未见（FTS 颁奖页）| 类型：标准进展/奖项
- 方向归属（主/次）：主 [量子/其他]；次 [Out] [底座-冷却] [底座-电力]
- 核心主张：列出 FTS 三个获奖论文，无论述
- 关键数据：
  - Best AI/HPC Track Paper：“Wavelength-Granular OCS with Solid-State OPA: Energy-per-Bit for AI Fabrics”，Shenzhen Litratech / Pixora LLC，Zhongxiang Zhang、Shan Che [p3]
  - Best Sustainability Track Paper：直接废热回收（膜辅助散热器），University of Florida / Univ. of Maryland，Saeed Moghaddam、Roshith Mittakolu [p5]
  - Best Overall Paper：“Copper Sintering BGA Interconnect for Mitigating Electromigration in High-Current AI Power Delivery”，University of Cambridge，Chengjie Du、Xufu Ren、Prof. Teng Long [p7]
- 提到的公司/客户/产品/标准：无
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（OCS 获奖论文页，可引用论文题名）

### P353 FTS-Chair-Keynote
- 讲者/机构：Dr Jon Summers，FTS Chair；Research Institutes of Sweden 数据中心科学负责人 [p2] | 类型：主题演讲
- 方向归属（主/次）：主 [量子/其他]；次 [底座-冷却]
- 核心主张：① 计算面临五堵墙：scaling、memory、power、sustainability、cost（引 imec 路线图）[p8]；② 瓶颈已从算法下移到电网互连容量，"计算的未来是能源、基础设施与可持续问题" [p9,p16]
- 关键数据：
  - FTS 日程：08:00 起，量子专场 12:30–17:00 [p3]
  - 论证"AI 尚未解决 Navier-Stokes 千禧年问题"（引用的是对宣称的反驳：简化方程、Lean 形式化改变命题等）[p13]
  - 引 McKinsey 2025：能耗/冷却/基础设施需求上升（无具体数字）[p14]
- 提到的公司/客户/产品/标准：imec、McKinsey、AlphaFold
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（六层系统瓶颈图）

### P355 01_Scaling Photonic Quantum Computers
- 讲者/机构：Jonah Force Hill，Director of Business Development & Government Relations，Xanadu [p1] | 类型：技术分享
- 方向归属（主/次）：主 [量子/其他]
- 核心主张：① 光量子计算无需为计算制冷、可用硅工艺制造、与电信兼容 [p4]；② 实用规模容错量子计算机是"联网光子模块组成的数据中心"，需数千机架、控制服务器、FPGA、探测器 [p13,p14]
- 关键数据：
  - Aurora：35 块集成光子芯片、3 种衬底、12 物理量子比特、>860 亿模式；首次光子实时纠错解码；损耗降低 30X、硬件开销降低 100X [p6，自报]
  - 路线图（目标）：2026–2031 损耗指标 24.1→10.2→7.2→1.8→1.0→1.0；逻辑量子比特到 200/500/1000+；Quantum Data Center 运行目标 2029–2030 [p15，目标，列表含义对应年份需看图确认，存疑]
  - 12 量子比特模型发表于 Nature 2025；GKP 量子比特演示 Nature 2025 [p5]
- 提到的公司/客户/产品/标准：Xanadu、Aurora、GKP
- 首次/记录/SOTA 声明："World's first full implementation of all subsystems needed for universal quantum computation"、"First modular, scalable, and networked quantum computer"（自称，p6）
- 推荐配图页：p15（硬件路线图）

### P357 Neutral-atoms-for-computing-and-sensing
- 讲者/机构：Paul Lipman，CRO，Infleqtion [p1] | 类型：技术分享
- 方向归属（主/次）：主 [量子/其他]
- 核心主张：① 中性原子：天然相同的量子比特、无需低温、低功耗 [p5]；② 路线：2026 约30 逻辑比特 → 2028 100 → 2030 1,000 [p10，目标，"illustrative"]
- 关键数据：
  - 30 个纠缠逻辑比特 / 80 物理比特，[[8,3,3]] 码 [p6，自报]
  - AI 辅助发现新 CCZ 逻辑门：物理 2Q 门 8→4 [p7]
  - FY26 营收指引约 \$45M；美国商务部 \$100M 投资 [p3,p11]
- 提到的公司/客户/产品/标准：Infleqtion、Sqale、Shunkai QPU、ARPA-E QC3、Genesis Mission
- 首次/记录/SOTA 声明："First and Only 100 qubit machine"（自称，p11）
- 推荐配图页：p10（MegaQuop 路线）

### P364 03_Concrete to Code Engineering AI Infrastructure at Gigawatt Scale
- 讲者/机构：Santosh Janardhan，Head of Global Infrastructure，Meta [p1] | 类型：主题演讲
- 方向归属（主/次）：主 [Across 跨楼/园区/区域]；次 [Out]、[运维/可靠性/遥测]、[底座-机架/机械]
- 核心主张：围绕四个"假设"反驳：① 集群不必在同一屋顶下——跨区域、5km/10km/100km 扩展；② 数据中心不止混凝土与钢（帐篷式快速建设）；③ 建成后不会自动工作（GB200 中断率需持续压降）；④ 软件不是容易的部分 [p2,p10,p13,p17]
- 关键数据：
  - Prometheus 多区域 AI 训练集群；每个 Region 图示 4 个 20k GPU 块（合计是否 80k 存疑），Region 经 BAG（Backend Aggregation）连接，距离 5km/10km [p3,p6,p7]；示意扩展到 100km [p5，看图，示意]
  - MetaRoCE：把网络当作多路径，按路径信号，只重传丢失部分，绕开拥塞 [p8]
  - GB200 中断率：GPU-1 由约 230 降至约 4–5 次/8K GPU/天，趋势 -5.5%/周；GPU-2 趋势 -5.9%/周；目标 2.0 /8K GPUs/day [p15，看图，实测+趋势外推]
  - 1 GW+ 集群、未来几年 5 GW：Prometheus、Hyperion（Titan AI 训练集群）[p20]
- 提到的公司/客户/产品/标准：Meta Prometheus/Hyperion、MetaRoCE、NVIDIA GB200
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（5/10/100km 多层扩展示意）、p15（GB200 中断率趋势）、p11（帐篷式数据中心航拍）

### P365 04_The Agentic Decade Starts with Open Infrastructure
- 讲者/机构：Mohamed Awad，EVP & GM, Cloud AI BU，Arm [p1] | 类型：主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [底座-机架/机械]
- 核心主张：① Agentic AI 成为核心基础设施负载，AI 数据中心需要三类 CPU：AI head node、Cloud native、Agentic virtual users [p16,p21]；② 加速器不应等待 CPU [p8]
- 关键数据：
  - 2030 全球 AI 数据中心及基础设施支出 \$7 万亿，数据中心容量需求 220 GW（引 McKinsey 2026）；OCP 成员到 2026 年底 700，比 2025 增长约 40% [p2]
  - OpenRouter 2026 年 8 月：agent tokens 7.3 万亿 vs 人类 1.4 万亿（引用，p16）
  - CPU 市场预测：2026 \$52B→2030 \$300B（引 Citi Research、Mercury Research，图中 \$52B/\$100B/\$138B/\$202B/\$300B）[p21]
  - 传统云：应用计算 ~75–80%，基础设施服务 ~20–25% [p11]
- 提到的公司/客户/产品/标准：Arm AGI CPU、SBSA/SBBR/SBMR、ACS、ADAC、RAS API、FCSA、ORv3/ORW 机架；Axion、Graviton、Cobalt、Vera 等 [p9,p15,p23]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p21（三类 CPU 任务与 CPU 市场预测）

### P369 08_Intelligent Infrastructure for the Intelligence Era
- 讲者/机构：Reynold D'Sa（首页写作者姓名，机构依内容为 Microsoft：p30 "Microsoft at OCP Global Summit 2026"）[p1,p30] | 类型：主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [Out]、[底座-电力]、[底座-冷却]、[安全]、[Up]
- 核心主张：① "Frontier Firm" = Human capital + Token capital，需要前沿基础设施，Networking delivers the intelligence [p3-5,p13]；② 开放推进网络（MRC 多路径）、光学（FTVO scale-up 规范）、DC 电力（Mt. Diablo）、冷却（Mt. Atlas）、安全与可持续 [p14-p27]
- 关键数据：
  - Maia 300：推理性能最高达上一代 7×；部署时 token/MW 比其余机队高 40%；多 GW 部署自 2027 年开始 [p9，自报/预测]
  - MRC：Multi-Planar Fabric，256 T1 × 8 planes（512 ports），512 T0 × 8 planes（256 up/256 down），每组 256 GPUs；packet spraying，绕过故障 [p14，看图；来源 openai.com MRC 页]
  - 安全芯片 / DPU 页出现 "Up to 70%、50%、33%、4x、3x、23%" 等数字，对应关系文字层无法确认 [p10-12，看不清]
  - 冷却：液冷（GPU 机架+CDU）与风冷并存，出现 "~2x" Zonal Cooling，口径不明 [p19，看不清]
- 提到的公司/客户/产品/标准：Maia 200/300、Cobalt 200、Azure Boost DPU、Integrated HSM、MRC（Microsoft/AMD/Broadcom/Intel/NVIDIA/OpenAI）、FTVO、Mt. Diablo、Mt. Atlas、LEED
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（MRC 多平面 + 包喷洒拓扑）

### P371 10_Women in OCP (WOCP) – Community First, AI Forward
- 讲者/机构：Sung A. Kim、Allison Boen、Anu Ramamurthy [p1] | 类型：主题演讲（社区）
- 方向归属（主/次）：主 [量子/其他]（社区/组织）
- 核心主张：WOCP 社区在 2 年内会员增至 350+ [p2]；提名表彰在冷却/浸没/PCR/PG25 等工作流的女性贡献者 [p4]
- 关键数据：WOCP 会员 350+（两年增长）[p2，自报]；p4 提到 OCP Cooling Environment/Cold plate/PG25 fluid 工作流
- 提到的公司/客户/产品/标准：PG25、Immersion Reliability workstream、Sustainability PCR
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P372 11_Secure Control and Management Plane (SCMP) From AI Racks to Autonomous Infrastructure
- 讲者/机构：Ford Tamer、Sanjoy Maity（首页；机构依内容为 Lattice + AMI）[p1,p7] | 类型：主题演讲
- 方向归属（主/次）：主 [安全]；次 [运维/可靠性/遥测]
- 核心主张：① 在 OCP 既有基础（OpenBMC、Caliptra/OpenPRoT、Redfish、MCTP/PLDM/SPDM、DC-SCM、OpenRMC）上连接成 Secure Control and Management Plane [p6]；② 新 OCP workstream 计划 Q4'26 启动，流程 Discover/Verify/Coordinate/Recover/Validate/Secure [p8]
- 关键数据：
  - 引用：数据中心 AI Capex \$1.2T(2027)（Morgan Stanley, Sep 2026）；\$10T(2030)（SemiAnalysis）；\$400B Q2'26 实际营收；半导体行业 \$50T 预测（Jensen Huang, GTC Mar 2026）——p2 数字与来源对应关系文字层不清，存疑 [p2]
  - 已发布 4 个 AMI+Lattice 方案：Security Retrofit、Plug-and-Play、Rack Boot、Power+Cooling [p11]
- 提到的公司/客户/产品/标准：Lattice、AMI、OpenPRoT、OCP S.A.F.E.、DC-MHS、OpenRMC、ORV3、OCPDiag、Caliptra
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（SCMP 参与方与新 workstream）

### P374 13_Put Every Prompt in Its Place
- 讲者/机构：Nic Dubé，Intel（Intel Keynote at 2026 OCP Global Summit）[p1] | 类型：主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [In]（p20 InP on 300mm 硅/集成激光）
- 核心主张：① 工作负载走向分布式推理与"合适规模的智能"，请求按负载路由到合适算力 [p4,p5]；② 推理编排：Xeon 做分类与路由，Intel GPU D-series 做 prefill，SambaNova RDU 做 decode [p18]
- 关键数据：
  - 合适规模路由：推理成本约降 60%，单次查询能耗降 >80%，性能下降 <1% [p5，自报]
  - Xeon 6+：最多 256 P-cores；Diamond Rapids 最多 288 E-cores（页面标注顺序存疑）[p15]
  - 开放权重 vs 闭源权重：31% / 78%（图含义不明）[p6，看不清]
  - 每企业 agent 数一年三倍；每月 agent 请求半年翻倍（图有 3x、2x、6.6B、3.4B、5.2 等数字，口径不清）[p13]
  - p20：Integrated Lasers、InP on 300mm Silicon，仅关键词，无数据 [p20]
- 提到的公司/客户/产品/标准：Intel GPU D-series、Xeon 6+、Diamond Rapids、SambaNova RDU、Open Accelerator Card (OAC)、ORv3；生态 logo 墙（p11，看图）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p18（prefill/decode/编排分工）、p5（成本与能耗降幅）

### P375 14_Shifting to DC Power Distribution in Data Centers A Collaborative Journey
- 讲者/机构：Paolo Catapane、Peter de Bock [p1]（机构未见；OCP Power Distribution sub-project 相关）| 类型：主题演讲
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：① 低压交流在电流、铜、热、空间上受限，需向 800V DC 转移 [p3,p4]；② 通过 OCP Power Distribution sub-project 标准化互操作（接地、连接器、控制、电压带、代际兼容）与 DC 保护安全 [p7-9]
- 关键数据：
  - 同功率下 800V 电流 16× 更小，损耗 256× 更小 [p4，理论推导，讲者引用]
  - 机架密度演进数字 120/140/240/600（单位未见）[p3，看不清]
  - 子项目：社区 800+，活跃贡献者 100，白皮书 250 页，10 个月/2 篇白皮书发布节奏 [p7，自报]
  - 架构：电网 34.5kVac → SST（MVAC→800Vdc）→ 主配电 800Vdc / ±400Vdc → 机架 [p5]
  - 保护标准：IEC 60947-10、UL 489I [p9]
- 提到的公司/客户/产品/标准：OCP Power Distribution、IEC 60947-10、UL 489I
- 首次/记录/SOTA 声明：白皮书 #1 为 OCP 点击最多贡献（自称，p10）
- 推荐配图页：p5（SST+800Vdc 配电架构）

### P376 15_Intelligence Infrastructure Scaling AI for the Frontier Era
- 讲者/机构：Partha Ranganathan，Google [p1]（机构依 p13 Google×OCP、p10 等内容）| 类型：主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [底座-电力]、[底座-冷却]、[Up]、[运维/可靠性/遥测]
- 核心主张：① 系统效率每代 10x–100x，需跨 Models→Energy 全栈协同 [p7,p6]；② 下一个拐点是"智能基础设施"：用 AI 改造硬件、软件、数据中心设计与运维（四个 vignette）[p15-19]
- 关键数据：
  - Google 栈要素：HBM 288GB 共封装、垂直供电、Deschutes CDU 液冷、ICI 多 TB/s 环面互连、Palomar MEMS OCS、100kW+ 3D pods、1P/3P GW 园区 [p6]
  - OCP 贡献数 117+（Google，图）[p13，看图]
  - Mantis：每次代码变更合并前扫描，精度 92%，扫描秒级（自报，p17）
  - OCP 项目：Diablo 400V 解耦电力（Google/Meta/Microsoft）、Falcon Networking（Google/NVIDIA）、Deschutes CDU、SST MV→800VDC、LVDC 配电（39 贡献者）、Open Data Center for AI 白皮书 [p10,p12]
- 提到的公司/客户/产品/标准：TPU、Axion、HBM、Deschutes、Palomar OCS、ICI、Falcon、AlphaEvolve、Mantis
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（全栈创新清单）、p12（OCP 贡献项目清单）

### P377 05_Redfish Native Fleet-Scale GPU Observability Assistant for AI Cluster
- 讲者/机构：Cyril Jose，AMD（DMTF Manageability Workshop）[p1] | 类型：标准进展/技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：① AI 规模下的效率靠数字孪生（基础设施孪生 + AI 集群感知孪生），共享一套 vendor-neutral Redfish 数据面 [p4,p5]；② 缺口在租户角色授权、分层证据采集、厂商无关指标命名，均为提案/WIP [p12,p13]
- 关键数据：
  - 带内导出占用主机 CPU 与 GPU 管理带宽，优先带外采集 [p12]
  - 现有 rail 遥测采样多为约 1–10 Hz，只够慢漂移，不够 sub-cycle 瞬态 [p8，讲者观察]
  - 参考实现 GYANAM（AMD，MIT 协议，开源）[p7]；Redfish 2025.2 引入 TelemetryData；PLDM DSP2091/2092/2093 在制 [p13]
  - 引 SemiAnalysis ClusterMAX 2.0（140+ 租户访谈，2025-11）[p3]
- 提到的公司/客户/产品/标准：Redfish、DSP0270、PLDM DSP2091–2093、OCP DCF r1.0、GYANAM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（两个孪生 + 共享数据面架构）

### P378 Crypto for SPDM- From Legacy to Quantum-Resistance and More
- 讲者/机构：Wilson Young（Solidigm）、Xiaoyu Ruan（Intel），DMTF SPDM WG [p1] | 类型：标准进展
- 方向归属（主/次）：主 [安全]
- 核心主张：SPDM 1.5 引入混合（传统+PQC）算法，设计最小化、可由 1.4 固件升级获得 [p7]
- 关键数据：
  - SPDM 版本时间：1.0 2019-12；1.1 2020-7；1.2 2021-12；1.3 2023-6；1.4 2025-5；1.5 计划 Q1/2027 [p4]
  - 1.4 起加入 ML-KEM-512/768/1024、ML-DSA-44/65/87、SLH-DSA；1.5 加混合：MLDSA87-ECDSA-P384 等、MLKEM1024-ECDH-P384/X448/ECDH-P521 [p4]
  - 混合密钥交换：两份共享秘密串接后输入 SPDM key schedule [p10]
- 提到的公司/客户/产品/标准：SPDM、NIST、IETF、ANSSI、BSI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（SPDM 1.0→1.5 算法演进表）

### P379 OCP RAS API PLDM Modeling
- 讲者/机构：Justin King（AMD）、Samer El-Haj-Mahmoud（Arm）、Janusz Jurski（Intel）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：为 OCP RAS API（v0.95rc1 WIP）定义 PLDM 映射（DSP2094 非规范白皮书），用 PLDM type 2 与 type 7 建模队列 [p3,p5]
- 关键数据：
  - 每个接口 1 个 action 队列、1 个 event 队列、最多 4 个错误队列（按严重度）[p4]
  - 命令：Get_CPER、Clear_CPER（可选）、Put_CPAD、Get_EP_config、Write_EP_config [p19]
  - 队列溢出时传感器转为 stressed（Set ID 9）[p11]
- 提到的公司/客户/产品/标准：OCP RAS API、CPER/CPAD、PLDM DSP0242/DSP0251/DSP0248、Redfish
- 首次/记录/SOTA 声明：无
- 推荐配图页：p15（PDR 结构图，看图）

### P382 Remote Attestation of Devices with Redfish and SPDM
- 讲者/机构：Jeff Hilland（Intel）、Mike Raineri（Dell Technologies）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [安全]
- 核心主张：用 Redfish ComponentIntegrity 资源与 SPDMGetSignedMeasurements 动作，让远端验证者以 nonce 取得设备签名的测量值，不依赖 BMC/BIOS 的信任 [p3,p5,p8]
- 关键数据：无定量数据；示例签名算法 RSAPSS_3072 / ECDSA P384，哈希 SHA-256/384 [p8,p11]；Tacklebox 脚本 rf_component_integrity.py 可跑端到端 [p9]
- 提到的公司/客户/产品/标准：Redfish ComponentIntegrity v1.5.0、SPDM 1.3/1.4、DMTF Redfish-Tacklebox
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（SPDMGetSignedMeasurements 交互流程）

### P383 SPDM Update- Hybrid, Authorization Policy and Standard Signatures (FRU)
- 讲者/机构：Jeff Hilland（HPE，DMTF President）、Brett Henning（Broadcom）、Bill Scherer（HPE）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [安全]
- 核心主张：SPDM 1.5：混合算法组合固定且最少、新增 GET_ATTESTATION 自包含签名、DMTF 授权策略 DSP0294、FRU 标准签名 [p5-p10]
- 关键数据：混合签名 4 组（MLDSA87 配 ECDSA-P384/Ed448/RSA3072-PSS/RSA4096-PSS）；密钥交换 3 组（MLKEM1024 配 ECDH-P384/X448/ECDH-P521）[p6]；DSP0289 发布 2025-12，DSP0294 发布 2026-08 [p8]
- 提到的公司/客户/产品/标准：SPDM、DSP0289、DSP0294、FRU
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（混合算法组合）

### P384 Using SPDM for PLDM Firmware Updates- Authorization Policy and Measurement Manifest Capabilities
- 讲者/机构：Brett Henning（Broadcom）、Patrick Caporale（Lenovo）、Scott Phuong（Microsoft）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [安全]
- 核心主张：① PLDM FW Update 1.3 支持随固件包下发参考测量清单（reference manifest），由数据中心管理系统经可信通道交给验证者 [p7,p8]；② DSP0294 授权策略可给不同用户分配密钥/证书管理、固件更新、复位等权限 [p13]
- 关键数据：无定量；CoRIM 为一种参考清单格式 [p6]
- 提到的公司/客户/产品/标准：PLDM FW Update 1.3、SPDM、CoRIM、DSP0289/0294/267/274
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（PLDM Measurement Manifest 流程）

### P385 01_A unified power management solution for AI data centers and legacy dat
- 讲者/机构：Shuming Zhu，Solution Architect，Lattice/AMI [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [运维/可靠性/遥测]
- 核心主张：① 电力管理需从传统数据中心扩展到 AI 数据中心的 9 个维度（容量规划、实时遥测、封顶、紧急降功率、碳追踪、实时 PUE、事件、通信协议、上电顺序）[p5]；② 企业用户需要社区（电力管理委员会）转译超大规模经验 [p17]
- 关键数据：
  - 功率封顶：引文称对 A100 TDP 封顶至 50% 用于 MILC 作业，性能损失 <15%（引 Acun 等）[p9，引用]；CPU 密集负载封顶可降功耗 15% 且影响可忽略（Intel 测试配置）[p9]
  - 真实事故时间线：12 月 18 日冷机故障，服务器可承受 CRAC 停止 20 分钟，厂商到场需 4 小时，次日 00:30 全部恢复 [p11，案例]
  - 电源架协议：Redfish 27.3% / SNMP 72.7%（11 个电源架品牌）；PDU：SNMP+Redfish 21.7% / SNMP 78.3%（23 个 PDU 品牌）[p15，市场品牌统计]
  - 上电顺序：UPS/电容 → 配电 → 冷却 → 网络 → 存储 → 计算（分组）[p16]
- 提到的公司/客户/产品/标准：OCP ORV3/HPR、OpenRMC、OAM_eFuse、CBU、Redfish、SNMP、PMBus
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（电力管理 9 维度）

### P386 02_From Infrastructure to Impact Implementing Sovereign AI at Denvr Dataw
- 讲者/机构：Amy Short, PhD，Executive Officer – Advanced Data Center Technologies，Denvr Dataworks [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]（浸没）；次 [推理/算力/经济性]（主权 AI）
- 核心主张：① 主权需要全栈本地所有与运营，而非仅数据驻留 [p9]；② 零水浸没式模块化数据中心：同为 1 MW，占地约小 90%，PUE <1.04 [p10,p11]
- 关键数据：
  - 6 个月建设周期，26,000+ GPU 已部署 [p3，自报]
  - 1 MW：风冷托管 6400 sq ft vs Denvr 模块化 600 sq ft [p10，自报]
  - 年化 PUE：全球平均 1.58；容量加权 1.47；"高效"数据中心 1.20；Denvr <1.04；每台服务器省约 800 W [p11，自报，引全球均值]
  - 单个生产浸没槽放 14 台 3OU H200 SXM 服务器；128–512 GPU 服务器 MDC 验证 [p13]
  - H200 集群调试：峰值系统温度仅升 6℃，稳定在约 45℃（槽内 43–47℃），机架进/出口 ΔT 约 10℃ [p15，实测]
- 提到的公司/客户/产品/标准：Denvr Dataworks、Dell H200/B300 SXM ORv2.2/ORv3、OCP Cooling Environments、City of Calgary、NESI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（PUE 对比）

### P387 03_From Projects to Platforms Reducing Risk in AI Infrastructure Through
- 讲者/机构：Troy Goldschmidt, PE，VP of Critical Environments, Data Centers，Kele Incorporated [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-机架/机械]；次 [推理/算力/经济性]、[运维/可靠性/遥测]
- 核心主张：① 项目制无法承接 3x 需求曲线，应转为"平台"：标准化接口、控制逻辑、数据约定，白空间（机架密度、液冷、CDU）保持灵活 [p2,p5,p7]；② 在工厂集成并验证，减少现场发现 [p9]
- 关键数据：
  - 全球数据中心容量需求 82 GW(2025)→219 GW(2030)（引 McKinsey/JLL）[p2，引用]；2025 年 57% 项目施工延误 ≥3 个月；2026 设备交期全球平均 33 周，美国 42 周，比 2019 高 83% [p2，引用]
  - 代表性园区：9 栋楼、90 个独立变量/16 类 [p4，情景]
  - MBOM 情景：140+ 仪表件号→22；9 个提交包→1；60+ 备件 SKU→12 [p10，情景/示例]
- 提到的公司/客户/产品/标准：Kele、McKinsey、JLL、OCP telemetry workstream
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（标准化 vs 灵活清单）、p10（MBOM 标准化对比）

### P389 05_Intelligent Power Smoothing at the Vera-Rubin Rack
- 讲者/机构：Gabriele Gorla、Rouslan Dimitrov，NVIDIA [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [Up 机柜/超节点]
- 核心主张：① 让机架成为"理想电网负载"：受控爬升/下降、平稳稳态，降低峰值以在同等供电下产出更多 token [p2]；② 机架内储能与 GPU 闭环协同 [p3]
- 关键数据：
  - 机架内储能 400 J/GPU [p3，自报]
  - LLM 训练、Vera-Rubin NVL72 机架：峰值功率降低 13%（结果 #1，AC whip 约 40k VA 平直，OFF 时周期下探至约 14–15k VA）；51%（结果 #2，OFF 时尖峰最高约 60k VA）[p4,p5，实测，看图]
  - 默认示例配置：PSU 最大 AC 爬升率 400 W/s，GPU 爬升/下降 20 W/s，空闲滞后 10 s [p7]
  - 硬件要求：NVIDIA AVL 电源架 110 kW AC/DC；800V Power Rack + 90 kW DC/DC [p6]
- 提到的公司/客户/产品/标准：NVIDIA Vera-Rubin NVL72、Intelligent Power Smoothing(IPS)、nvonline ID 1153760
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（IPS ON/OFF 功率曲线对比）

### P390 06_Modular by Design Building AI Clusters from Factory-Built Units
- 讲者/机构：Bill Stube（R&D）、Alex Akesson（Product），Crusoe [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-机架/机械]
- 核心主张：① 建设是项目、计算是产品——把数据中心做成工厂集成、可验证、可复制的单元 [p4]；② 提议 OCP Modular DC 子项目制定开放规范：物理单元及其接口 [p13]
- 关键数据：
  - 单元包含：低压供电、冷却（风冷/DLC）、GPU+网络+辅助机架、结构化布线与配线架、BMS/消防/IT/OT；支持 NVIDIA 与 AMD GPU [p6]
  - 单元即故障域；后端 fabric 跨单元统一，预端接主干 [p8,p9，看图]
  - 逻辑分区实现多租户无需重新布线 [p10，看图]
  - 先建主干供电，按单元逐步通电，建设期即有收入（示意 50%/100% GPU 单元）[p11]
  - 无定量性能数据
- 提到的公司/客户/产品/标准：Crusoe、Crusoe Industries、OCP Modular DC sub-project
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（单元到集群的参考架构）

### P391 07_Open Adapter Card – AI From Small Pod to Enterprise Scale
- 讲者/机构：Kevin Mundt（AMD Fellow）、Alex Sanville（Dell DMTS）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [底座-机架/机械]；次 [Up]
- 核心主张：CEM 与 OAM 在热/机械/电气上已到上限，机架级之间缺少小 pod（8–16 GPU）形态，OAC 规范提供标准化卡（风冷/DLC）[p2,p5]
- 关键数据：
  - 企业调查口径：86% 机架在 5–30 kW；77% 无提高机架密度计划；64% 仍仅风冷 [p3，引用，来源未见]
  - OAC DLC 模块占板面积为 PCIe CEM 的 2.2x [p5，自报]
  - 规范 v0.9 已公开，5 家共同作者（AMD、Qualcomm、Dell、Intel、NVIDIA）[p6,p7]
- 提到的公司/客户/产品/标准：OAC、PCIe CEM、OAM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（机架功率-时间缺口示意）

### P392 08_Standardizing AI Data Centers to Unlock Faster Access to Power
- 讲者/机构：Anuja Ratnayake，Emerging Technologies Executive，EPRI；2026-10-13 [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：① 电网容量稀缺，需用统一"灵活性分类"（Class A–E）让数据中心可响应电网而不牺牲可靠性 [p5]；② NERC 拟对 ≥50 MW、≥100 kV 接入的计算负荷注册 CLO/CLOP 角色 [p7]
- 关键数据：
  - Speed to Power 图出现 "2 yr / 7 yr"（口径未在文字层说明，推测为并网时间对比）[p3，存疑]
  - 灵活性分类 V1.0：Class A–E，涉及通知窗口、激活期（≤5 小时至 ≤96 小时）、年利用率（≤1%/≤10%）[p5]
  - NERC CLO 标准提案：总接入负荷 ≥50 MW，≥100 kV [p7]
- 提到的公司/客户/产品/标准：EPRI、NERC、OCP data-center facility energy 工作组
- 首次/记录/SOTA 声明："World's largest cross-sector collaborative on flexibility"（自称，p5）
- 推荐配图页：p5（Common Flexibility Classification）

### P393 09_Welcome & Overview Adoption, Ecosystem Growth, and the Path to Partici
- 讲者/机构：Ewa McCurdy，Solution Provider Program Manager，OCP Foundation [p1] | 类型：主题演讲（轨道介绍）
- 方向归属（主/次）：主 [量子/其他]（OCP 采用/生态）
- 核心主张：OCP 项目→贡献→产品→OCP Accepted→Marketplace 的路径；OCP Inspired 已退役，仅保留 OCP Accepted [p3,p6]
- 关键数据：Marketplace 各指标同比 +30% 以上：183 个 Solution Provider（+32%）、683 个上架（+39%）、213 个 AI 相关（+46%）、33 个 Experience Centers（+43%）、26 个 OCP Ready 数据中心（+30%）、月均 36K 访问（+38%）[p5，自报]
- 提到的公司/客户/产品/标准：OCP Accepted、OCP S.A.F.E.、OCP Ready、OCP Experience Centers；议程列出 SemiAnalysis、IDC、McKinsey、Johnson Controls、Meta BOM 等场次 [p2]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（Marketplace 指标）

### P394 Designing-AI-Infrastructure-for-the-Inference-Era
- 讲者/机构：面板：Woo Jin Ho（Bloomberg）、Ty Schmidtt（Dell）、Mohan Kumar（Oracle OCI）、Curtis Aubrey（Vantage Data Centers）[p1] | 类型：面板
- 方向归属（主/次）：主 [推理/算力/经济性]
- 核心主张：仅标题页，无内容
- 关键数据：无
- 提到的公司/客户/产品/标准：Bloomberg、Dell、Oracle OCI、Vantage
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P396 From Compute Demand to Capacity Delivered Unlocking the Data Center Value Chain for the AI Build-Out
- 讲者/机构：Maria Goodpaster、Elia Berteletti、Denise Lee，McKinsey & Company（Partner）[p1] | 类型：技术分享/市场分析
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [底座-电力]
- 核心主张：① 电力是数据中心增长的最大障碍；② 定制规格放大所有瓶颈，OCP 标准化可缩短交期 [p4,p8]
- 关键数据（均为 McKinsey 模型/估计）：
  - 全球数据中心 IT 算力需求：2025 年 171 GW → 2030 年 298 GW → 2035 年约 336 GW（基准情景；各情景 2.8x/3.7x/5.2x，图中另含 219、254、472 等数字，对应关系不确定）[p2，预测，存疑]
  - 2025–2030 累计投资约 \$7.3T（约占全球 GDP 每年 1%）；其中 Designers & manufacturers 约 \$4.4T、Energizers 约 \$1.3T、Builders 约 \$1.0T、Software 约 \$0.6T；服务器（含 GPU/CPU）约 \$3.5T [p3，预测]
  - 美国需求 2030 年约 100 GW，仅 65% 的已宣布容量会投产；能量接入最长 4–5 年；65% 的玩家部署现场发电 [p4，调研/预测]
  - 美国供需缺口 2030 年约 15 GW：需求年增 27% vs 供给 24%；2028 年需求/供给比 113% [p5，预测]
  - 关键设备交期（周）：发电机约 30→约 100，冷机约 20→约 75（2019→2025，其余设备数字对应不确定）[p6，引用/专家访谈]
  - OCP 标准化潜在缩短交期 3–6 个月，定制部署延长 6–12 个月 [p8，预测]
- 提到的公司/客户/产品/标准：McKinsey、OCP Power Distribution、Cooling Environments、Rack and Power、Open Cluster Designs for AI、Open Data Centers for AI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（需求情景）、p5（美国供需缺口）

### P398 OCP-in-Action-How-RackRenew-s-Hardware-Enables-Brigade-s-Open-Self-Service-Platform
- 讲者/机构：Matty Bakkeren，Global Partnerships & Alliance Manager，RackRenew [p1] | 类型：厂商展区/案例
- 方向归属（主/次）：主 [底座-机架/机械]；次 [安全]
- 核心主张：Brigade 的开放自助云平台运行在 RackRenew 的 OCP Accepted 再制造硬件上，目标是避免锁定、保证主权与合规、降低成本与嵌入碳 [p3]
- 关键数据：无定量数据 [p3]
- 提到的公司/客户/产品/标准：RackRenew、Brigade、OCP Accepted、NIS、ISO、CNCF landscape
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P400 PG25-at-Scale-What-We-ve-Learned-and-Where-We-re-Going
- 讲者/机构：面板：Paul Artman（AMD）、Chris Campbell（Vertiv）、Jacob Paugh（ChemTreat）、Cam Turner（Microsoft）、Keegan Yaroch（Dow）[p1] | 类型：面板
- 方向归属（主/次）：主 [底座-冷却]
- 核心主张：OCP 发布 PG25 基础规范与使用指南，推动冷板冷却液标准化 [p4]
- 关键数据：PG25 Base Specification 2026-08 发布；PG25 使用指南 2026-09 更新；水基冷板冷却液基础规范 2026-08 发布；Cold Plate Cooling Fluids workstream 每月第二个周一开会 [p4]
- 提到的公司/客户/产品/标准：PG25（Propylene Glycol 25%）、ASHRAE TC 9.9、OCP Cold Plate Coolants workstream
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P402 The-Missing-Layer-Why-Compute-Hardware-Needs-a-BOM-Interchange-Standard
- 讲者/机构：Jacob Wright, MBA，Meta Infrastructure Supply Chain PLM [p1] | 类型：标准进展
- 方向归属（主/次）：主 [底座-机架/机械]；次 [推理/算力/经济性]
- 核心主张：计算硬件缺少 BOM 交换这一层，命名/结构/属性不统一，需 OCP BOM Interchange 标准（延伸而非发明）[p8,p25,p27]
- 关键数据：
  - 67% 的 BOM 收到时带错误（引 Supplyframe NPI Sourcing Study 2022，251 家公司）[p16，引用]
  - 2026 年约 \$7000 亿交易所依据文件未经机器验证 [p20，自报]
  - 行业服务器与机架配置数：2016 年 25 → 2021 年 80 → 2026 年 400；年新增配置速率约 11/年 → 约 64/年（约 6x）[p22，看图，作者分析，OCP/ODM 部分为估计]
  - 时间线：Q4 2026 章程与联席主席；Q1–2 2027 草案分类与 schema；Q3 2027 试点；Q4 2027 发布 v1.0；已承诺：Meta、Quanta、Ingrasys(Foxconn) [p38]
  - 政策背景：CISA HBOM Framework（2023-09）、EU Cyber Resilience Act、EU Digital Product Passport [p23，看图]
- 提到的公司/客户/产品/标准：Meta、Quanta、Ingrasys、Supplyframe、CISA HBOM、EU CRA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p22（配置数量爆炸柱图）

### P403 Upgrading-OCP-S.A.F.E.-and-S.O.L.I.D.-for-the-AI-age
- 讲者/机构：B Keen、Zahra Lak（Microsoft）、Jeff Andersen（Google）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [安全]
- 核心主张：① S.A.F.E.（Security Appraisal Framework and Enablement）输出可复用报告而非通过/不通过；S.O.L.I.D. 为具体要求库，自 2026-10 强制 [p4,p5]；② AI 辅助审查：AI 能发现大量严重问题，但仍需人工，不允许自评 [p7,p9]
- 关键数据：按新要求审查自 2027-01-01 起强制 [p8]；目前需用前沿云模型，开放权重模型是否允许在调研 [p7]；无性能数据
- 提到的公司/客户/产品/标准：OCP S.A.F.E.、S.O.L.I.D.、SRP（Security Review Provider）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（一次审查多客户复用）

### P410 07_Open, AI-Ready FBOSS From Platform Bring-up to Solution Qualification
- 讲者/机构：Benoit Sigoure（Nexthop AI）、Srikrishna Gopu（Meta）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络]（交换机软件/SONiC 同类）；次 [运维/可靠性/遥测]
- 核心主张：① FBOSS 配置驱动：每个子系统一个 JSON 描述，不需为每块板写服务代码；全部可在开源中构建与认证 [p3,p4]；② AI 辅助新平台 bring-up，每次迭代约 5 分钟 [p7]
- 关键数据：
  - 8×800G 流量哈希测试：Wedge800 向对端推 8×800G，1000 条路由 [p7]
  - 结果：25.6T Wedge 800：235 测试通过、50 失败、200 待接入；102T（TH6-P）：50 通过、400 待接入；TaaC 发现了 FBOSS 服务与产品固件缺陷 [p8，自报]
  - 开源 Apache 2.0，可配任意流量发生器 [p6]
- 提到的公司/客户/产品/标准：FBOSS、Wedge800、TH6-P（Broadcom Tomahawk 6 的页内简称，页内未展开）、SAI/SDK、SFF-8024、BGP、OpenR、Nexthop AI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（Wedge800 与 102T 结果表）

### P449 01_Addressing Discovery and Topology Challenges in M-PESTI Systems
- 讲者/机构：Dr. Tamer Gudu、Aleksandar Jovanovic，AMD [p1] | 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [In]（CXL/内存池化相关 CMS 轨道）
- 核心主张：M-PESTI 发起端用 TDM 共享单个 UART/控制 IP，64 个发起端同时通信且 FPGA 面积接近单发起端 [p5]；提出 MUX 后目标发现流程 [p8]
- 关键数据：
  - 标准建议的轮询方式发现时间：N=64、PAYLOAD_SIZE=2048 时 44us×2048×64 ≈ 5.77 s；活动相 N_VW_BYTE=16 时约 45 ms [p4，推算]
  - 系统时钟 Fsys = 250K × 发起端数 × 采样率：64 个发起端，采样率 4→64 MHz，8→128 MHz [p5]
  - AMD 改进建议预计 2027 年初提交 [p9]
- 提到的公司/客户/产品/标准：M-PESTI、DC-MHS、UART、FPGA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（发现时间与活动相时间估算）

### P451 03_MHS Datacenter-Secure Control Module (DC-SCM) 3.0 Specification Update
- 讲者/机构：Tim Lambert（Dell Technologies Fellow）、Javier Lasa（Intel）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：DC-SCM 2.2 不再增强；3.0 在 ~17 家公司参与下制定，形态与引脚与 2.2 不前后兼容，含误插防护 [p2]
- 关键数据：
  - 时间线：EOY 2026 约 0.5 包；OCP GS 2027 目标 1.0；首批产品最早 CY 2028 [p2]
  - 接口变化（暂定）：PCIe x1,x1,x4→x1（Section 0）；I3C 6x→0；I2C 18x→0；USB 4x 2.0 + 1x 3.0 → 4x 2.0；增加 BMC_RECOVERY [p6]
  - LTPI：1.0 保持；2.0 增加链路层与随机访问（不向后兼容）；或弃用 [p5]
  - 评估 M.2 变体用于 mini-SCI；评估 DLC 指导 [p7]
- 提到的公司/客户/产品/标准：DC-SCM、DC-SCI、DC-MHS、OBMF、LTPI、SGPIO、SFF-TA-1002
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（接口变化表）
