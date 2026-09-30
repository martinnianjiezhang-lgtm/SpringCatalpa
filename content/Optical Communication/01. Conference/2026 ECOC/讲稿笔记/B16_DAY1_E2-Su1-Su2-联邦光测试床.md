---
title: "B16 · DAY1 · E2-Su1-Su2-联邦光测试床"
tags:
  - ECOC2026
  - DAY1
---

### 0920-am-Su1-H-01-Telefonica-开放数据基础设施.pdf
- 讲者/机构：讲者姓名幻灯片未显示；Telefónica（ETSI TC DATA 相关） | 题目：未见完整英文原题（p1 为 "The Motivation" 页，看图核实；主题 Open/Distributed Data Infrastructure；ETSI TC DATA 活动） | 类型：Workshop（Su1-H 联邦光测试床/数据空间）
- 方向归属（主/次）：主 1（AI光网络/数据基础设施）；次 6 不适用
- 核心主张：
  - 数据应像分布式计算一样，摆脱集中化与单一访问模式，需要“分布式、开放、可信”的数据方案 [p1]
  - 数据基础设施含三个独立维度：连接（data in transit）、存储（data at rest）、计算（data in process），面向 agent 应用自主用数，遵循 FAIR 原则 [p2]
  - 手段：语义互操作（知识图谱、本体、n对1映射，lifting/lowering）与治理/溯源/证据（集中式数据目录、Policy as Code、动态授权、workload identity 用 OAuth token 关联到可追责的人、公证服务 notary） [p6][p8]
- 关键数据：无定量结果（概念性/标准活动介绍）。ETSI TC DATA 状态图为 2025 年 9 月（页面标注 Status: September 2025）[p4]
- 提到的公司/客户/产品/标准：ETSI TC DATA、ISG CIM（NGSI-LD）、ISG PDL、ISG CDM、TC Smart M2M（SAREF）、STF 704/685/697/693/702/727、EU Data Act、EU AI Act、YANG、FAIR 原则 [p3][p4]
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p4（ETSI TC DATA 与各 ISG/STF 关系全景图，含 Data governance、Traceability of AI、YANG 等工作项）

### 0920-am-Su1-H-02-德国电信-待定议题.pdf
- 讲者/机构：讲者姓名未见；页脚为 Telecom Infra Project（TIP）Data & AI Foundations 项目组（文件名标德国电信） | 题目：Data and AI Foundations —— The role of open industrial forums（页眉所示） | 类型：Workshop
- 方向归属（主/次）：主 1（AI光网络/运维）
- 核心主张：
  - 用例是否适合协作，应在“洞察的差异化价值”之外，以“数据可共享性”为第三轴判断；流量矩阵、客户行为、成本模型等“永不共享”，参考拓扑、实验室测量、合成数据可“直接公开” [p1]
  - 单个运营商的数据在事件数量与工况组合上都不足以学出故障前兆；协作的理由是数据需求而非隐私，可通过联邦学习“移动模型而非数据”实现，原始遥测不出运营商边界，传输的只是模型权重 [p3][p4]
  - 中立论坛的作用：统一“什么算故障（如 flap）”的定义、统一数据模型与标签体系、参考实现，并导向 OpenConfig、IETF CCAMP、ONF TAPI、TM Forum 与运营商 RFP [p6]
- 关键数据：无定量结果。案例：IP 层链路 flap 持续数周，光层检查均“正常”（功率正常、无告警、跨段损耗在规格内），工单被以“no fault found”关闭后两周重开；前兆通常已在遥测中（pre-FEC BER、Q、OSNR、Rx 功率、SOP 旋转速率、激光器偏置与 TEC 电流、模块温度、FEC 块计数）[p5]
- 提到的公司/客户/产品/标准：TIP Data & AI Foundations 项目组（co-lead：Telus、Telefónica、AT&T；三条工作流：数据、模型、用例）；OpenConfig、IETF CCAMP、ONF TAPI、TM Forum、3GPP、IETF；光传输 AI 用例分类引用 JOCN 2025 等 [p2][p7]
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p5（IP层症状与光层根因对照的 flapping 链路案例）；p2（光传输 AI/自治用例分类总表）

### 0920-am-Su1-H-04-NEC-数据空间支撑数字孪生.pdf
- 讲者/机构：讲者姓名幻灯片未显示；NEC Corporation（p1 看图核实，浏览器标签为 "03_Flavio.pdf"） | 题目：Data Space / Digital Twin（IOWN，页面主题；完整英文原题未显示） | 类型：Workshop
- 方向归属（主/次）：主 1（AI光网络/数字孪生）
- 核心主张：
  - 数据空间提供可信、受治理的数据共享，数字孪生把数据转化为预测、仿真和决策，形成持续价值闭环 [p10]
  - IOWN 将数字孪生使能、分布式数据基础设施、安全与光网络（Open APN）结合，支撑从 descriptive 到 prescriptive 的网络孪生（ETSI CIM 定义 Descriptive / Predictive / Prospective / Prescriptive / Diagnosis 五类孪生）[p3][p4][p10]
  - 下一步：两个 Network Digital Twin 用例走向参考实现模型；多利益相关方场景在讨论中 [p10]
- 关键数据：无定量结果。DSDT 功能架构含四组功能：数据处理、分析、操作（仿真/可视化）、安全；文档标注 Functional Architecture Release 2, August 2026 [p5][p6]
- 提到的公司/客户/产品/标准：IOWN Global Forum、Open APN（APN-Interchange/Gateway/Transceiver/FlexBridge）、OpenROADM MSA（数据模型对接）、ETSI ISG CIM（NGSI-LD）、IOWN Data Hub；NDT 用例：Green Twin、光网络基础设施管理（多层故障检测与恢复选路、QoT 估计与资源优化）、Time Variable Routing 预测、安全流量分析、Gen-AI 自治运维 [p3][p7]
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p9（光网络基础设施管理的 NDT 用例流程：服务请求—路径设计—监控—告警/排障—服务结束，标出 NDT 支撑环节）

### 0920-am-Su2-H-02-Trinity-测试床遥测与数字孪生.pdf
- 讲者/机构：Agastya Raj / Trinity College Dublin（IRIS 网络 AI 与传感组，Open Ireland 测试床） | 题目：Lessons from Large-Scale Optical Network Experimentation（ECOC 2026 workshop on federated optical testbeds，2026-09-20） | 类型：Workshop
- 方向归属（主/次）：主 1（AI光网络/测试床）
- 核心主张：
  - 跨测试床共享数据与模型时，需随数据附带通道加载、tap 损耗、器件类型及限制，随模型附带训练所用器件类型/工作范围与用于适配的测量；流程为“按原样测试—本地适配—对比”[p6]
  - 用少量本地测量即可把共享 EDFA 模型适配到新器件 [p3][p5]
  - 控制与遥测应统一为一层，脚本和 agent 共用同一接口（Splice），agent 增加检索、工具层与写前策略门，即可无人值守长时间实验 [p7][p8][p9]
- 关键数据：
  - COSMOS：2 个测试床共 26 个放大器，每个增益设置一次满载测量；预测误差评估覆盖 11 个 booster、11 个 pre-amp、4 个 ILA [p3]
  - NICT 共享 3 个放大器、200 km 光纤、4 天测量；Open Ireland 通道加载 15/18/21 dB，NICT 为 26 dB（工作点不同）[p4]
  - NICT EDFA 1 增益形状误差：Open Ireland 模型未适配 0.36 dB；假设平坦谱 0.19 dB；测量噪声 0.03 dB；10 次本地测量适配后 0.046 dB，同类型 NICT 模型 0.037 dB；20 次测量两者均达测量噪声；少于 5 次时仅用本地数据优于迁移模型；测量顺序为先满载再对半再三分之一 [p5]
  - Splice：发现 14,428 条路径（Lumentum、Adtran、Juniper 设备），其中 12,359 条可读；11 个固定工具，对各厂商同一接口 [p8]
  - 13 天无人值守噪声系数采集，2026 年 4 月 12 日起，每 3 分钟一次测量；agent 发现某厂商收发器改频后不生效，需 off-on 循环，当次即修复；大故障经 Discord/Slack 告警通知人 [p9]
- 提到的公司/客户/产品/标准：Lumentum ROADM、Adtran TeraFlex 收发器、Juniper in-line amplifier（p8 看图核实：Splice 在三家设备上发现 14,428 条 YANG 路径、12,359 条可读，Agent 用 11 个固定工具）、Cisco；NICT、Fraunhofer HHI；Optical Testbed Data Space、COSMOS、DTU 公开数据集、YANG、gNMI；Splice 开源（github.com/Open-Ireland-Testbed/splice）；H. Akbari et al., ECOC 2026 demo [p2][p8][p10]
- 与业界对比或记录声明（SOTA/首次/record）：无明确 record 声明；称“我们与 HHI 分别用了 NICT 数据、跑了 TCD 放大器模型”[p2]
- 推荐配图页：p5（增益形状误差 vs 本地测量次数曲线，含 0.36/0.19/0.03 dB 基线）；p9（agent 无人值守 13 天实验闭环）

### 0920-am-Su2-H-03-FraunhoferHHI-电信数据空间.pdf
- 讲者/机构：Angela Mitrovska / Fraunhofer HHI（邮箱见 p5） | 题目：From Data Sharing to Federated Operations: The Expanding Role of Telco Data Spaces（p1 看图核实） | 类型：Workshop
- 方向归属（主/次）：主 1（AI光网络/数据空间）
- 核心主张：
  - 迈向自动化阶梯需跨组织闭环（Awareness→Analysis→Decision→Execution），受厂商专有 IP、运营商保密及监管限制，跨方共享受信任缺失阻碍 [p2][p3][p4]
  - 以数据空间原则做治理：数据主权+策略引擎（谁、何时何地、如何、为何用途），分别治理数据（OTDS）、设备（所有权感知 YANG/ODRL 策略）、计算（多域 QoT 安全多方计算）[p5][p6][p7][p8]
  - 现场演示：IPoWDM 相干可插拔控制架构对比，及 OTDS 跨 HHI/Open Ireland(TCD)/NICT+Cisco 共享数据与数字孪生模型 [p9]
- 关键数据：无定量结果。多域 GSNR 端到端估计用加密份额的安全多方计算，各域不泄露自身 GSNR（引自 OFC 2026）[p8]；演示时间 2026-09-22 11:00–12:30，Pavilion 1 Area 1065 [p9]
- 提到的公司/客户/产品/标准：NICT、TCD/Open Ireland、Cisco、Adtran Networks SE、Telia Company AB、Infosim、TU Berlin（p9 demo 作者机构看图核实）；Edgecore SONiC、400G ZR+ 相干可插拔；YANG + ODRL 策略扩展、NETCONF、IPoWDM、NDGC（Network Data Governance Connector）、安全多方计算 GSNR 估计、TM Forum 自治等级、Optical Testbed Data Space；引用 OFC 2023、JOCN 2025、OFC 2026 两篇 [p5][p6][p7][p8][p9]
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p6（OTDS 数据交换与 DT 模型交换双流程图）；p8（多域 QoT 的安全多方计算架构）

### 0920-am-Su2-H-04-NICT-测试床支撑AI数据管线.pdf
- 讲者/机构：Yuki Yoshida 等（Hirota, Suzuki, Xu, Furukawa, Shinada, Awaji）/ NICT | 题目：Powering AI via Testbeds: Establishing Sustainable and Sovereign Data Pipelines（Su2-H：Can Global and Federated Optical Testbeds Power AI-Native Networks and Telecom Data Spaces?） | 类型：Workshop
- 方向归属（主/次）：主 1（AI光网络/数据）
- 核心主张：
  - 网络 AI 属“物理 AI”，数据成本比 LLM/生成式 AI 高 100~1000 倍；测试床数据开放且易于打标签，可成为数据飞轮的起点 [p4][p5]
  - 测试床数据孤岛源于所有权、出口管制、厂商 IP 保护、数据完整性与可持续性，需数据主权框架（数据空间、Connector）[p6][p7]
  - 测试床数据价值不只在体量，而在捕捉并暴露关键罕见边缘案例 [p11]
- 关键数据：无定量结果。厂商策略演示：HHI 测试床使用 Adtran 设备，NICT 提供数据时须匿名化厂商细节；Adtran 需要数据集训练网络性能监控 AI；流程含协商、授权（Vendor Z 认证服务器）、原始数据与匿名数据两路 [p10]；OTDS 演示涉及 3 个以上机构、各自策略控制 [p9]
- 提到的公司/客户/产品/标准：Adtran、Cisco、Fraunhofer HHI、TCD；IDSA 参考架构、Gaia-X、Data-EX/CADDE、EDCC（Eclipse Dataspace 风格 Connector）、Data Free Flow with Trust（DFFT）[p7][p10]
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p10（HHI–NICT–Adtran 三方厂商策略数据共享演示架构图）

## 本批小结
- 联邦光测试床的核心矛盾不是技术算法，而是数据主权与信任：运营商/厂商遥测因保密、监管、IP 不可外流，故“移动模型不移动数据”（联邦学习）与“数据空间+策略”成为共识路径（来自 TIP/德电、HHI、NICT、Trinity）。
- Optical Testbed Data Space（OTDS）已进入实操：HHI、TCD(Open Ireland)、NICT 加 Cisco/Adtran 在 ECOC 2026 Demo Zone 演示跨方共享数据与数字孪生模型，含厂商匿名化策略（HHI、NICT、Trinity）。
- 迁移与适配是关键实证点：Trinity 显示未适配的迁移 EDFA 模型误差 0.36 dB，仅 10 次本地测量即降到 0.046 dB，接近同类型模型 0.037 dB，少于 5 次时本地模型反而更好（Trinity）。
- Agent 化运维在测试床已落地：统一 YANG/gNMI 接口（Splice）加策略门，agent 无人值守 13 天采集，并自行发现修复收发器改频需 off-on 的问题（Trinity；NICT 称 L4+ 自治与 agentic NW AI）。
- 数字孪生与标准化并行推进：IOWN NDT 用例（QoT、故障恢复、Green Twin）、ETSI CIM/NGSI-LD、OpenROADM、TM Forum 自治等级、Policy as Code 均被引为落地路径（NEC、Telefónica、德电/TIP、HHI）。
- 故障前兆的共享标准化尚缺：需先统一“什么算 flap/故障”和标签体系，光层前兆量（pre-FEC BER、SOP 速率、TEC 电流等）单运营商样本不足（德电/TIP 案例）。
