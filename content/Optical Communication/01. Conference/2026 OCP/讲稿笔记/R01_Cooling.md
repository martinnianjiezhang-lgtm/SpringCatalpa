---
title: "R01_Cooling"
tags:
  - OCP2026
  - 讲稿笔记
---

# R01 笔记：Cooling：Cold Plate / Rack & Power / Security

> 说明：本批 11 份全部为冷却、电力/机架、安全类讲稿，与 AI 网络/互连直接相关的只有 P005（448G 可插拔 I/O 模块液冷）、P034（Slingshot/OCP NIC 液冷）和 P024（OCP-NIC 400G/800G）的部分内容。其余按 NOTE_SPEC 规则 4 写精简版。

### P002 Chemical-Free Water Chemistry Management for Reliable Operation of Copper Cold Plates
- 讲者/机构：两场 lightning talk 合集 [p1]。(1) Fei Dai — Guangzhou Goaland Energy Conservation Tech. Co., Ltd.（talk 9040）；(2) Stirling Boston（Watts | EasyWater）、Kelley Mullick（Avayla Consulting Group）（talk 9255）| 类型：技术分享（厂商方案）
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：
  - 闭式回路的共同失效根源是溶解氧引起的腐蚀，腐蚀产物造成结垢并成为下游磨蚀颗粒 [p16]；只靠化学钝化不能去除氧，也滤不掉威胁冷板微通道的亚微米颗粒 [p18]。
  - 用连续旁流处理（物理/电子调理 + <1 µm 过滤）取代周期性加药，去除"氧 + 颗粒"这个驱动因素 [p19]；用 DO、腐蚀挂片、细菌、颗粒四点协议监测水质 [p20]。
- 关键数据：
  - Goaland 测试回路 63 天：DO 从第 1 天约 3.45 ppm 降至约第 7 天起 ~0.1 ppm 并保持 [p8，看图，实验]；电导率 ~0.2–0.29 µS/cm [p6，看图，实验]；pH 稳定在 ~7.0 [p7，看图，实验]。
  - 铜挂片 1500 h：腐蚀速率 0.37 / 0.53 µm/y（重量变化 1.6 / 2.3 mg）[p9，看图，实验]。
  - Goaland 给出的控制参数：pH 6.8–8.5，电导率 ≤2.00 µS/cm，DO ≤0.20 ppm，腐蚀速率 ≤1.00 µm/y [p10，看图，自报]。
  - 未处理闭式回路典型 DO 3–7 ppm [p17，自报]；未处理回路细菌 10⁴–10⁵ CFU/mL，阈值 10³ CFU/mL [p18，自报]。
  - EasyWater 现场：多站点 DO 3–7 ppm → 0–1 ppm（2–3 周）；长期监测回路 5–6 ppm → <1 ppm 维持 8 个月；挂片损失 0.0692 mils/yr [p21，现网，样本为学校/楼宇供暖回路而非数据中心]。
  - 0.024 in. 结垢使可比换热管效率损失 ≈14% [p22，引用，来源未注明]。
- 提到的公司/客户/产品/标准：Goaland、Watts / EasyWater、Avayla；ASHRAE TC9.9；TCS/CDU [p20, p22]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（DO 随时间下降到 0.1 ppm 的曲线）；p21（现场 DO 前后对比表）

### P003 Cold plate subproject update
- 讲者/机构：Berhanu Wondimu（Intel）、Emily Clark（Dell Technologies），OCP Cold Plate 子项目联合负责人 [p1]；另含 Anthony Constantine（Micron）[p11]、Keegan Yaroch（Dow Chemical）[p19]、Dr. Florian Rüping（Castrol）[p28]、Tim Marquis（Parker Hannifin）[p37]、Elizabeth Langer（CPC）[p47] 的 lightning talks | 类型：标准进展
- 方向归属（主/次）：主 [底座-冷却]；次 [存储]（DLC E1.S）
- 核心主张：
  - Cold Plate 子项目已发布一批规范（UQD V2.0.0、PG25/水基/两相介电冷却液基础规范、PBMC、Rope Leak Sensor 等）[p6]，下一步重点是互操作、测试方法、TIM 表征、遥测与热回收 [p9]。
  - SSD 功耗上升，需要把冷板集成进 E1.S 的参考设计（CoolIT/Micron/Stäubli 发起）[p14, p16]。
  - QD 互操作"必要但实践中难"；UQDv2.0 首次试点跨厂商互操作测试，并正在起草 "Fundamentals of Verification, Reliability, and Interoperability of QDs" [p49, p50, p57，看图]。
- 关键数据：
  - SSD 功耗（Micron 引用图）：PCIe 4.0→6.0 约 15→35 W 线性增长，PCIe 7.0 约 50 W（每 NAND 封装约 3.5 W，E1.S），PCIe 8.0 更高 [p14，看图，预测]。
  - PBMC：容许 5 mm 径向偏移、5 mm 与 2.5° 组合偏差、6.5 mm 配合距离 [p39]；36 lpm 时 ΔP <4.0 psi，最大工作压力 75 PSIG [p40，自报]；Rev 1.1 把测试 2.6.1A 扭矩从 6 N 提到 20 N [p44]。
  - UQD08 流体损失：n=60，各 plug/socket 组合均值约 0–0.026 mL/cycle，USL 0.07 [p51，看图，实验]。
  - UQD08 连接力：n=200，实测 0 psi 约 13–25 lbf、100 psi 约 46–58 lbf，规范线 30→71 lbf；非标准插头倒角插拔力尖峰可达 ~100 lbf [p52，看图，实验]。
  - 湿材料示例判据（PP-R/PP-RCT/PP-H，ASTM D543，60/80 °C，1008 h）：重量、尺寸变化 <5%，拉伸强度、断裂伸长率变化 <10% [p31]。
  - 水基冷却液指南预计 2026 年 11 月发布，取代 2022 版 [p23]。
- 提到的公司/客户/产品/标准：Intel、Dell、Micron、CoolIT、Stäubli、Dow、ChemTreat、Castrol、PFX Group、Arteco、NVIDIA、Vantage Data Center、Ecolab、ZutaCore、Saint-Gobain、Parker、CPC、AMD（UQD V2.0.0 贡献者）、CEJN、Danfoss、Travis 等 [p21–p25, p48, p50]；UQD V2.0.0、BMQC (2023)、PBMC (2026)、MQD (WIP 2026)、MiniQD (WIP 2027) [p56，看图]；ASTM D543；ORB 接口
- 首次/记录/SOTA 声明：UQDv2.0 "pilots interoperability testing"（首次试点跨厂商互操作测试）[p50，看图]
- 推荐配图页：p56（OCP QD 规范族与时间线）；p52（UQD08 连接力 vs 管路压力实测）

### P005 Cooling the 448G Frontier- Thermal Architecture for 500 W-Class HSIO Using Direct-to-Chip
- 讲者/机构：Divya Bandaru、Sridhar Mukthineni、Arjun P、Remesh Kuzhikkali，TE Connectivity [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [Out 后端网络：可插拔光模块] / [Up 机柜/超节点：CPO/NPO/XPO]
- 核心主张：
  - 224G 以上、1.6T 以上的可插拔模块已到风冷物理极限；>35 W 的模块从未以风冷出货 [p4]。
  - 把冷却液引入模块内部（direct-to-chip，in-module 集成冷板 + 盲插 QD）比笼外冷板少两层热阻，可在 500 W 下留有余量，并满足 100 次插拔 [p5, p6]。
  - 生态不成熟、QD 互操作与泄漏风险、mini QD 压降高是 DTC 方案的主要短板 [p6]。
- 关键数据：
  - 每 lane 功耗 56G→448G 增长 5 倍（1.5→7.5 W）；DSP 热流密度 100+ W/cm² [p4，自报]。
  - 模块 TDP：56G 8-lane 12 W、112G 8-lane 16 W、224G 8-lane 27 W；448G 8-lane 70 W、16-lane 120 W、64-lane 500 W（448G 为预测）[p4]。
  - 同 1RU 32 端口面板功耗：56G 0.4 kW → 224G 0.9 kW → 1.9 kW/RU [p4，预测]。
  - 冷却方式上限：风冷骑式散热器 ~25–35 W；笼外冷板 + 干 TIM 热桥 ~35–50 W；模块内液冷 ~120–500 W [p3]。XPO 64-lane（224G）为模块内液冷 [p3]。
  - 仿真条件：TIM 0.05 °C/W，PG25，入口 45 °C，1.5 lpm/kW [p8]。64-lane 500 W @0.7 lpm 最高芯片温度 74.9 °C（目标 <95 °C）[p9，仿真]；全部场景 <85 °C [p10，仿真]。
  - 压降：x32/x64 冷板 <2 psi @0.7–0.9 lpm；x8/x16 <9 psi @0.1–0.2 lpm；mini QD 额外 6–10 psi [p11，仿真]。
  - 台架实测 vs 仿真：500 W @0.7 lpm 约 75 °C vs 74.9 °C；250 W @0.7 lpm 约 63 °C vs 60.5 °C；压降 0.8–1.24 psi，与仿真偏差约 0.02 psi 以内 [p13，看图，实验]。
- 提到的公司/客户/产品/标准：TE Connectivity；QSFP56/QSFP112、QSFP-DD/OSFP 400G/800G、OSFP-RHS 1.6T、XPO 64-lane [p3]；OCP Cold Plate workstream [p14]
- 首次/记录/SOTA 声明：无（"no module above 35 W has ever shipped on air" 属行业判断）[p4]
- 推荐配图页：p3（I/O 模块 TDP 随 SerDes 速率演进及各冷却方式上限）；p13（500 W/250 W 实测 vs 仿真）

### P008 Fluid Velocity and Erosion Updates
- 讲者/机构：Sung A Kim（Castrol）、Pradip Sairam Pichumani（Meta）[p2]；第二场 Greg Spangler（SABIC Specialty Resins）[p18] | 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：
  - PG25 在 6.2 m/s 流速下运行 93 天，铜管没有整体金属冲蚀；但弯头处缓蚀膜被剪切减薄，硫化物优先在此形成，弯头的保护余量更小 [p15]。
  - 建议监测唑类缓蚀剂余量、做 BART SRB（MIC）检测，并采用无铅钎焊 [p15]。
  - SABIC 提出按 ASTM D543 做加速筛选，评估热塑性材料在 PG25 中的环境应力开裂 [p22]。
- 关键数据：
  - CDA 铜管流速限值参考：冷水 <2.4 m/s；热水 <60 °C 时 <1.5 m/s；>60 °C 时 0.6–0.9 m/s [p3，引用 CDA A4015-26/24]。
  - 试验：Castrol PG25，6.2 m/s，1" ID 铜管（C12200，H58，未钝化），2,232 h（93 天），Tulsa 大学 [p4，实验]。
  - 管壁厚度在超声设备变异范围内保持不变；流体中铜 <1 ppm（第 0–93 天）[p5, p6，实验]。
  - 唑类/有机膜：弯头 ~8 nm，直管 ~35 nm（薄 4.4 倍）[p15，实验 XPS]；直管 N 1s 8.66 at%，为弯头的 2.5 倍 [p14]；检测到 Pb 0.10 at%（可能来自焊料溶解）[p12]。
  - SABIC 首轮材料筛选预计 1Q2027 完成 [p24，预测]。
- 提到的公司/客户/产品/标准：Castrol ON Direct Liquid Cooling PG25、Meta、University of Tulsa、SABIC；ASTM D6130、ASTM D543；OCP 水基冷却液指南 [p24]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p15（结论页：弯头与直管缓蚀膜厚度对比及建议）

### P010 Pushing the Single-Phase Cold Plate Limit
- 讲者/机构：主持 Joel Chakkalakal（Shield by Guardian）；嘉宾 Remco van Erp（Corintis）、Yin Hang（Meta）、Oscar Farias Moguel（Microsoft）、Weihua Tang（Google Cloud）[p1] | 类型：面板
- 方向归属（主/次）：主 [底座-冷却]；次 [In 封装内：HBM]（芯片-冷板协同设计）
- 核心主张：
  - Microsoft：传统单块鳍片导致流体温升和压降大，"unitary cell" 方法利用入口区高换热、按热点分配流量，可把热点压到目标以下 [p9, p10, p12]。
  - Corintis/Google：芯片发热不均匀，冷板要与芯片协同设计（微流控核心、分流微通道、按热图定制鳍）[p14, p21]。
  - Meta：冷板不是唯一瓶颈，TIM 和硅本身占结到冷却液热阻的一半以上 [p27，看图]。
- 关键数据：
  - 鳍片入口约 1 mm 区域 Nu 高 150 倍 ≈ HTC 高 6 倍 [p10，自报]。
  - Microsoft unitary cell 原型实测结温最多降低 10 °C [p11，实验]。
  - Corintis 微流控冷板在 NVIDIA H200 @1 LPM：GPU 结-入口温升 42.0→32.4 °C（−23%），HBM 29.5→23.9 °C（−19%），对比 skived 冷板，同冷却液、同台架 [p16，实验]；宣称温度降低 10–20% [p15，自报]。
  - Corintis：冷板仿真可耗时 12+ 小时 [p17]；增材制造通道/鳍宽 <100 µm，产能百万件/年 [p18，自报]；硅热测试载具 2 kW、240 通道电源、2×2 mm 像素 [p19]。
  - Meta 热阻构成（结→冷却液）：基线 冷板 45%/TIM 20%/硅 35%；翘曲增大 41%/27%/32%；功率密度增大 38%/17%/45% [p27，看图]。
- 提到的公司/客户/产品/标准：Microsoft SPARC、Corintis（Glacierware、Core Foundry、Therminator）、Google Ironwood（引用 Hot Chips 2025）[p21]、NVIDIA H200、Meta；ECXML 封装模型 [p17]；OCP Cold Plate Performance workstream
- 首次/记录/SOTA 声明：无
- 推荐配图页：p16（H200 上微流控 vs skived 冷板对比）；p27（结→冷却液热阻构成）

### P024 Applying OCP ORv3 and ORW Design Principles to Rack-Scale Arm AI Infrastructure with Supermicro
- 讲者/机构：Daniel Chen（Supermicro）、Marc Meunier（Arm）[p1] | 类型：技术分享（厂商方案）
- 方向归属（主/次）：主 [底座-机架/机械]；次 [底座-电力]、[推理/算力/经济性]
- 核心主张：
  - 按负载定义机柜：agentic AI 中 CPU 负责编排、加速器生成 token，agent 发出的请求量是人类的 15 倍以上 [p2, p3]。
  - ORv3 与 ORW 采用同样的设计原则，ORW 提供更大的规模空间；电力、冷却、机械、管理接口的标准化可减少集成摩擦 [p9, p11, p12]。
- 关键数据：
  - ORv3 液冷 21" 44OU：16 个 2OU4N 节点，128 颗 AGI CPU，最多 22,848 核，~82.5 kW/机柜，3×72 kW 电源架（2+1），6 条 415V/60A 电源线，柜内 CDU [p7, p9，自报]（同页机柜图另标 "64 node, 128 CPUs, 84KW"，口径存疑）。
  - ORW 液冷 42" 机柜：148 节点（1OU4N），296 颗 AGI CPU，最多 40,256 核，~185 kW/机柜，6×72 kW 电源架（4+2），12 条 415V/60A，列间 CDU [p8, p9，自报]（文字写 44OU，机柜图标 48-OU，存疑）。
  - 计算节点：双路，2×400G/800G OCP-NIC，1×DC-SCM（OpenBMC），2×E1.S/M.2，2×PCIe Gen 6，24 DIMM [p5, p7]。
- 提到的公司/客户/产品/标准：Supermicro ARS-122GT-HEOW-LCC、ARS-222GT-HEO-LCC [p6]；Arm Neoverse、Arm AGI CPU（AR3DPT-64C/128C/136C）；SBSA、SBMR、ADAC、FCSA；Meta Yosemite V5 [p5]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（ORv3 与 ORW 参数对比表）

### P026 High-Power-Density BBU and CBU Design for Evolving AI Data Center Power Architectures
- 讲者/机构：Takuya Tsutsumi（Panasonic Energy）、Hank Tsuda（Panasonic Energy Sales Company of America）[p1] | 类型：技术分享（厂商路线图）
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  - 机柜功率走向 1–2 MW 后，BBU/CBU 承担备电、削峰、负载平滑等多种角色，难点在于同时实现高功率密度和安全 [p4]。
  - LFP 难以支撑 300 W/电芯级需求；Panasonic 推 NCA/LFP 复合正极电芯（>250 W），兼顾功率与热稳定性 [p6, p9]。
- 关键数据：
  - Panasonic 已出货 6 亿颗以上锂电池用于关键基础设施，声称零事故 [p3，自报]。
  - 电芯需求：当前 120 W-90 s（HPR v2 12 kW）→ 200 W-90 s（明年起）→ 300 W-90 s（未来）[p6]。200 W×90 s 需 5.0 Wh：LFP future 6.3 Wh（+21%），NCA/NCM 9.8 Wh（+49%）；300 W×90 s 需 7.5 Wh：LFP 不足，NCA/NCM 8.25 Wh（+9%）[p6，看图，仿真/估算]。
  - 针刺测试：NCA 型电芯温度指数峰值 ~100，NCA+LFP 复合型 ~62；热板测试 NCA 起火、复合型不起火 [p7，看图，实验]。
  - 路线：柜内 72 kW/架 → 118 kW（90 s）；侧柜 900 kW → 1.5 MW / 2.0 MW（DC 输入，90 s）；10 ft 集装箱 BBU（8 个电源柜）4.5 MW/300 s 备电、3.4 MW 负载平滑 [p10，预测]。
  - 集装箱配置：8×BBU 柜 / 5 BBU+3 CBU / 8×CBU 柜，对应 300 s 备电 4.5 MW（共享 SOC）或 8 MW / 4.6 MW / 300 kW，负载平滑 3.4 / 4.2 / 10 MW，输出 1,000–1,500 Vdc [p11，预测，初步估算]。
- 提到的公司/客户/产品/标准：Panasonic；NVIDIA Blackwell/Rubin/Rubin Ultra/Feynman 时间线 [p12]；ORv3、HPR、UL9540A、NFPA；OCP Energy、Power Delivery、DC-MHS [p13]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（LFP vs NCA/NCM 在 200 W/300 W×90 s 下的余量表）

### P034 Scaling OCP for Supercomputing- The Cray GX Infrastructure
- 讲者/机构：Jason Zeiler、Javier Izquierdo、Brian Purcell，HPE [p1] | 类型：技术分享（厂商方案）
- 方向归属（主/次）：主 [底座-机架/机械]；次 [底座-电力]、[底座-冷却]、[Out 后端网络：NIC]
- 核心主张：
  - HPC 与 AI 基础设施融合，GX5000 在 OCP 标准基础上做高密度、近 100% 液冷的机柜 [p3, p4]。
  - 通过适配套件让 OCP/MGX 现成部件（交换机、计算刀片、电源）进入 GX5000；呼吁 OCP 制定液冷 QD 尺寸/流量、液冷电源架、液冷 OCP NIC 的标准 [p9, p10]。
- 关键数据：
  - 单柜 400 kVA+，近 100% DLC，支持 40 °C 设施水，最多 144 节点 / 73,728 核，可扩展到数百柜 [p4，自报]。
  - 机柜：50V（8000A）DLC 母排，44 OU，重 4,535 kg，占地 900×1200 mm [p5]。
  - 电源架：无风扇液冷，1 OU 最高 66 kW（2×33 kW 整流器），>30% 负载时效率 97%+，内置储能应对 GPU 瞬态；计算/交换机每 OU 最高 25 kW；未来超过 400 kW 并支持 800VDC [p6，自报]。
  - 冷却：CGD12 QD 每 OU 支持 20 kW+（1.5 lpm/kW）[p7]。
  - GX250 刀片：4×2P AMD Venice（500/600 W，每 CPU ≤256 核），每刀片 4 或 8 个 Slingshot-400/800 端点；每 Scalable Unit 最多 512 / 1024 处理器 [p8]。
- 提到的公司/客户/产品/标准：HPE Cray SC GX5000、EX4000、HPE Slingshot（"connectionless" RDMA，通往 UET）[p9]；NVIDIA Quantum-X800 InfiniBand；OCP NIC 3.0（TDSFF 双宽 v1.5，HPE 主要贡献）[p7]；MGX、ORv3；800VDC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（GX5000 关键指标一页）

### P038 Advancing Data Center Trust- Open Standards for Attestation, Device Identity, and Post-Quantum
- 讲者/机构：Jeff Andersen（Google）、Shiva Dasari（HPE）[p1] | 类型：标准进展（TCG）
- 方向归属（主/次）：主 [安全]
- 核心主张：
  - 用 TCG 开放标准建立从制造到运行的可验证信任链：DICE 做部件级信任根与身份，TPM-over-SPDM 保护 TPM 通道（应对主动 interposer），PQC-ready TPM [p8, p12, p15]。
- 关键数据：
  - TCG 成立于 2003 年，已发布 90 多份规范与指南 [p2, p7]。
  - Promoters 15 家：AMD、Arm、Cisco、Dell、Google、HP Inc、HPE、Huawei、IBM、Infineon、Intel、Lenovo、Microsoft、NVIDIA、Toyota [p3，看图]。
  - PQC TPM 依赖：TPM Library Spec 1.85（已发布）、PC Client PTP 1.07（已发布）、EK Cred Profile V2.7（已发布），PC Client 认证计划进行中 [p14，看图；p15]。
- 提到的公司/客户/产品/标准：TCG、DICE、DPE、TPM、SPDM、"TPM Communication over SPDM Secure Session" 规范 [p12]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（TPM-over-SPDM 分层架构图）

### P039 An Introduction to Attesting Hitlessly Updatable Systems
- 讲者/机构：Matt King（NVIDIA）[p1] | 类型：技术分享（概念）
- 方向归属（主/次）：主 [安全]；次 [运维/可靠性/遥测]
- 核心主张：
  - 支持热更新（hitless update）的系统，在证明之后状态仍可能改变，仅靠重新生成证据无法弥补这个缺口 [p10, p11]。
  - 证据需增加更新历史（history）和一个直到复位前不可变的更新策略（update policy，如防回滚、二次授权公钥），由依赖方评估并拒绝不可接受的策略 [p12, p14, p16]。
- 关键数据：无数值数据（概念性讲稿）；引用 RATS 架构 RFC 9334 [p4]。
- 提到的公司/客户/产品/标准：NVIDIA；IETF RATS（RFC 9334）、TCG、DMTF、OCP [p17]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p15（静态与可更新部件所需证据对比）

### P041 BMC-Mediated Platform Composite Attestation via Redfish
- 讲者/机构：Xiling Sun、Roksana Golizadeh Mojarad，Microsoft [p1] | 类型：技术分享 / 标准提案
- 方向归属（主/次）：主 [安全]
- 核心主张：
  - 当前平台证明是分散的：验证者要对 N 个设备分别发起 Redfish 往返，证据之间没有平台级绑定，BMC 自身结果也不与它转发的设备证据绑定 [p2]。
  - 由 BMC RoT 作为 Lead Attester 生成并签名 Composite EAT，一次 Redfish 请求返回一个平台级签名产物，用 Platform CoRIM 校验组成的完整性和防替换 [p3, p4, p10]。
- 关键数据：
  - 流程：POST CompositeEATBundle(nonce) → 202 → 收集设备证据 → 签名 Composite EAT → GET 返回 CBOR tag-602 Detached EAT Bundle，共 11 步 [p6, p7]。
  - 摘要算法 SHA-384（-43）[p6]。
  - 已有参考实现：Azure GitHub Composite EAT SDK；Aspeed/Nuvoton OpenBMC SDK 早期采用 [p12，自报]。
- 提到的公司/客户/产品/标准：Microsoft Azure、Aspeed、Nuvoton、OpenBMC（bmcweb、spdmd、MCTP）；DMTF Redfish、SPDM、IETF RATS（RFC 9334、RFC 9711）、EAT、CoRIM/CoMID、Project Veraison [p11]
- 首次/记录/SOTA 声明：无（提出将 Platform Composite EAT Profile 提交到 OCP 和 IETF RATS，API 提交 DMTF Redfish）[p12]
- 推荐配图页：p4（平台组合证明架构图）
