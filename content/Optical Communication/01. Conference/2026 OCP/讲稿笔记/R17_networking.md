---
title: "R17_networking"
tags:
  - OCP2026
  - 讲稿笔记
---

# R17 笔记：networking / market-impact-adoption / keynotes / manageability-workshop

### P370 09_Scaling AI Infrastructure Responsibly Through Open Standards
- 讲者/机构：Pradeep Vincent，Oracle Cloud Infrastructure (OCI) [p1] | 类型：主题演讲
- 方向归属（主/次）：主 [运维/可靠性/遥测]（Optics Reliability）；次 [Out 后端网络]（可插拔光模块/LPO/CPO 链路可靠性、DPU）、[安全]（Tessera IHSM）、[底座-冷却]、[底座-电力]
- 核心主张：
  - 开放生态可以加快 AI 数据中心建设；OCI 在 OCP 中从参与者转为发起多个新工作组、提交规范 [p1, p7]。
  - 在 OCI 的规模下，光链路瞬态故障会扩散成 fabric 重收敛、RDMA 超时和业务中断，链路可靠性已是 fabric 级要求；需要厂商中立的遥测、链路行为、诊断与缓解标准，在 LPO 和 CPO 出现时给芯片、光模块、系统和运营方共同基础 [p20–p22]。
  - 发布三项新工作：Tessera 集成 HSM（IHSM）规范、Optics Reliability（Enhanced Telemetry Optics 软件规范 v1.0）、DPU Abstraction Layer [p9, p16, p19, p24]。
- 关键数据：
  - OCI 区域 220+（含已上线与规划），截至 2026-07-06 [p3]（自报）
  - 时间线：2021 参与 DC-SCM v2；2023 开始采用 OCP ORv3；2025 多个吉瓦级 AI 数据中心站点、ORv3 OCI C3 机柜；2026 成为 OCP Advisory Board 成员 [p7]（自报）
  - Enhanced Telemetry Optics Product Software Specification v1.0 已提交 OCP [p19]（自报）
  - 光模块灰尘会导致链路故障，"Millions of Links"，修复链路故障耗时 [p20]（自报，无具体数值）
  - 新提出数据中心效率指标：Geographic PUE（gPUE）、Compute Density、Infrastructure Utilization Efficiency（IUE）白皮书 [p12]（自报）
  - OCI 与美国能源部及国家实验室合作 Grid-to-DC 规范（Energy and Grid Solutions 子组）[p26]（自报）
- 提到的公司/客户/产品/标准：OCI、Microsoft（Tessera 合作方）[p18]、Caliptra 类 ASIC 路径 [p17]、DC-SCM v2、ORv3、OPF（Open Platform Firmware）、LPO、CPO、DPU Abstraction Layer、US DOE；同届 Oracle 讲题含 "Zero-Touch OCS Fabrics for AI Scale-Out Infrastructure at Hyperscale" [p28]
- 首次/记录/SOTA 声明：宣布 Tessera IHSM 新工作流启动、DPU Abstraction Layer 首次发布（"ANNOUNCING"）[p16, p24]
- 推荐配图页：p22（链路可靠性是 fabric 级要求的论述页）；p14（看图：液冷全系统管路示意）

### P373 12_Scalable and Open AI Solutions From Cloud to Sovereign to Edge
- 讲者/机构：Trish Damkroger，HPE [p1] | 类型：主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [Out 后端网络]（UEC、SONiC）、[Up 机柜/超节点]（ESUN）、[底座-冷却]
- 核心主张：
  - AI 需要全栈异构开放技术，HPE 在 compute/systems/networking 各层与 OCP 协作 [p3, p6]。
  - 以 Ethernet 覆盖 scale-up、scale-out、scale-across，支持 SONiC 和 Junos 两种 NOS 选择 [p8]。
- 关键数据：
  - HPE 液冷专利 300+；建造了全球前 10 超算中的 6 台；Top 25 最节能超算中 13 台 [p4]（自报）
  - HPE Slingshot 网络转向基于 UEC；业界首款 DLC（直接液冷）ORv3 QFX 1.6T 交换机 [p9]（自报）
  - OCP NIC 3.0 液冷，HPE 为规范主要贡献者 [p9]（自报）
  - Mission/Vision 系统（与 Los Alamos、NVIDIA）采用 NVIDIA Vera CPU + Rubin GPU；Discovery/Lux 系统（AMD，Oak Ridge）[p10, p11]（引用：AMD、NVIDIA 高管引语）
- 提到的公司/客户/产品/标准：HPE ProLiant DL525/DL585a/XD2300 Gen13、DL340 Gen12、XD245 Gen13、HPE Cray Supercomputing GX5000、PTX/MX 路由器、QFX 交换机、UEC、ESUN、SONiC、Junos、MHS（模块化硬件系统）、AMD、NVIDIA、DOE、Genesis Mission
- 首次/记录/SOTA 声明：业界首款 DLC ORv3 QFX 1.6T 交换机 [p9]；"First national AI system for Genesis Mission with open Ethernet" [p4]（均为自报）
- 推荐配图页：p8（HPE 开放网络：scale-up/out/across + UEC/ESUN/SONiC 一页总览）

### P380 PLDM-Modeling-for-Common-Crash-Dump-Bulk-Telemetry-and-Watchdog-Timer-Access
- 讲者/机构：Łukasz Łanecki、Pat Schoeller，Intel（DMTF）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  - 在现有 PMCI 规范（DSP0240 PLDM Base、DSP0242 PLDM File Transfer、DSP0248 PLDM Monitor and Control）上统一 Bulk Telemetry、Crash Dump、Timer/Watchdog 三类操作的发现、控制和传输，不新造传输协议；内容格式仍由厂商定义 [p3]。
  - BMC 不处理遥测/崩溃数据，只透传到 Redfish，由 OpenTelemetry 等外部工具分析 [p6, p9, p13]。
- 关键数据：
  - Bulk Telemetry 四种数据行为：telemetry file、snapshot、streaming（PLDM File Transfer SerialTxFIFO）、telemetry events [p5]（自报）
  - 示例链路：PLDM Types 0、2、7 → BMC → Redfish → Prometheus/Graphite(Carbon)/Grafana 插件 [p6]（自报）
  - Watchdog 实体 Entity ID = 38 或 82；state sensor/effecter Set ID = 244；counter 与 timeout 数值对象 base unit = 21 [p12]（看图）
  - Redfish 对齐：Bulk Telemetry ↔ TelemetryService/TelemetryData；Crash Log ↔ LogService；Watchdog ↔ HostWatchdogTimer [p13]
- 提到的公司/客户/产品/标准：DMTF PMCI、PLDM DSP0240/0242/0248、Redfish、OpenTelemetry、Prometheus、Graphite、Grafana
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（BMC 透传 bulk telemetry 到 Redfish/Prometheus 的数据流图）

### P381 Redfish Aliasing Support and Redfish Streaming Telemetry Enhancements
- 讲者/机构：Jeff Autor (Vertiv)、Hari Ramachandran (Microsoft)、Bill Scherer (HPE)，DMTF Redfish Forum [p1] | 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  - 各厂商成员 Id 命名不同，超媒体发现成为"fleet tax"；Redfish 引入用户定义的资源别名（~alias）直接寻址，省去发现步骤 [p3–p5]。
  - 新成立 Telemetry Task Force，用标准化 ServiceAlias 构造互通的遥测名称和标签，并提出更省载荷的 TelemetryBundle（TLV 时间序列）输出 [p6–p13]。
- 关键数据：
  - Resource Aliases 进入 Redfish Specification v1.25.0 与 schema 2026.2 [p4]（自报）
  - 从提出到批准在一个发布周期内完成（每年 3–4 次发布）[p3]（自报）
  - Telemetry Task Force 于 2026 年 4 月成立 [p6]（自报）
  - 示例：无别名需 3 次 GET 才能拿到处理器健康状态，有别名 1 次 GET（/redfish/v1/Systems/~system1/Processors/~cpu1）[p5]（自报）
  - ServiceAlias 序号以 1 起始，Processor 与 Drive 例外用 0 起始 [p8]
- 提到的公司/客户/产品/标准：DMTF Redfish、OCP、Vertiv、Microsoft、HPE；Sensor/ProcessorMetrics/MemoryMetrics schema；CDU、RackPDU 等设施对象
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（有无别名的 API 往返对比代码）

### P388 04_From Silicon to Services
- 讲者/机构：Dylan Patel，SemiAnalysis [p1] | 类型：主题演讲（Market Impact & Adoption）
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [Out 后端网络]（未直接展开）
- 核心主张：
  - InferenceX 是开放、可复现的推理基准（公开 GitHub Actions 运行），覆盖 NVIDIA、AMD、Google TPU 等加速器，以 TCO 和 tok/s/MW 比较 [p6]。
  - Agentic 编程负载已成主力；AgentX 用真实 Claude Code 会话回放测试，结果高度依赖模型、引擎和延迟目标 [p8–p10]。
  - Rubin 在高交互度区间的每 MW token 吞吐领先 GB300 较多 [p12]。
- 关键数据：
  - InferenceX：13 个加速器 SKU、约 19 个 AgentX 模型、10+ 推理栈、1,806 GitHub stars（2026-10-06）[p6]（自报）
  - ClusterMAX 3.0（2026-09）：跟踪 323 家、评审 77 家、19 个 Medallion [p3]（自报）
  - Codex 占 OpenAI 企业输出 token 64%（2026-06 快照，28 日平均），2025-10 Codex GA 时约 3%，2026-02 约 12% [p8]（引用 OpenAI 数据；中间值为看图）
  - AgentX v1.0：393 个匿名 Claude Code 会话，选自 8,300 个会话语料（3.4M 请求、\$3M+ 花费）；输入 token p50/p90/p99 = 88K/272K/675K；44% 会话使用 subagent；最大上下文 1M [p9]（自报）
  - DeepSeek V4 Pro（2026-08）：SGLang 上 Qwen3.5 在 90 tok/s/user 时 NVIDIA 对 AMD 20x+；GLM 5.3 在 150 tok/s/user 时 NVIDIA 成本效率最高 5x；vLLM CPU KV offload 输出吞吐 +81.7% [p10]（自报基准）
  - TCO \$/chip-hr（SemiAnalysis 2026-07 定价调查）：H100 1.17、H200 1.22、B200 1.73、B300 2.26、GB200 1.86、GB300 2.31、MI300X 0.95、MI325X 1.1、MI355X 1.5、TPUv7 1.03（Google 内部 TCO）[p10, p13]（看图）
  - AMD MI355X FP8 + TileRT 解码：GLM5.2/5.3 744B 峰值 P90 交互度约 470 tok/s/user；B300 \$2.26 / GB300 \$2.31 / MI355X \$1.50 每芯片小时 [p11]（自报；讲者注明峰值速度不代表成本效率优势）
  - Vera Rubin NVL72 vs 最佳 GB300 引擎，每 all-in utility MW 的 token 吞吐：75 tok/s/user 64.00 vs 44.14 M tok/s/MW（1.45x）；100 时 59.38 vs 28.47（2.09x）；125 时 4.29x；150 时 36.98 vs 5.14（7.19x）；200 时 2.72x；all-in 每芯片功率 VR200 3.3kW、GB300 2.12kW、MI355X 2.09kW；Rubin 为预发布软件 [p12]（看图；预览）
  - TPUv7 Ironwood（Qwen3.5 397B FP8 8K/1K，100 tok/s/user，外部 TCO）：\$0.181/M token，B200 \$0.222，B300 \$0.276 [p14]（自报，preview）
  - 低 E2E 延迟时 B200/GB200 领先 TPUv7，高延迟时 TPUv7 领先 [p13]（看图）
- 提到的公司/客户/产品/标准：NVIDIA GB300/GB200 NVL72、B200/B300、Vera Rubin NVL72、AMD MI300X/MI325X/MI355X/MI455X UALoE72、Google TPUv7/TPUv8i、SambaNova SN50、Amazon Trainium3、Dynamo、TRTLLM、SGLang、vLLM、TileRT、DeepSeek V4 Pro、Qwen3.5、GLM 5.x、OpenAI Codex、Claude Code、Bloomberg SAH100SC 指数
- 首次/记录/SOTA 声明：无正式首次声明；InferenceX "One open benchmark, every accelerator" [p6]
- 推荐配图页：p12（看图：Rubin vs GB300 每 MW token 吞吐表）；p8（看图：Codex 占比曲线）

### P395 Designing-Rack-Scale-AI-The-OCP-Advances-its-Vision-of-a-Single-Chip-to-Grid-AI-Production-System
- 讲者/机构：Chris Drake，IDC（另列 Leon Kao、Kuba Stolarski、Dr. William Lee）[p1, p17] | 类型：主题演讲（市场研究）
- 方向归属（主/次）：主 [推理/算力/经济性]（市场）；次 [Up 机柜/超节点]（ESUN、CPO）、[Out 后端网络]、[底座-电力]、[底座-冷却]
- 核心主张：
  - OCP 认可的基础设施支出由 GPU 服务器驱动快速增长；OCP 关注点上移到从芯片到电网的"chip to grid"整体系统 [p2, p15]。
  - 今后重点从开放积木转向集成参考架构、单系统验证与多供应商互通演示 [p15]。
  - Ethernet 正成为覆盖多种网络尺度的 AI 主要 fabric [p9]。
- 关键数据：
  - OCP 认可基础设施支出：2025 年 \$154B → 2030 年 \$892B，CAGR 42%；2020 \$17B、2026 \$325B [p2]（预测，IDC）
  - 其中服务器：2024 \$61B、2025 \$131B、2026 \$292B、2027 \$516B、2028 \$627B、2029 \$734B、2030 \$814B [p2]（看图，预测）
  - 90% 的 OCP 设计服务器部署于核心数据中心环境 [p3]（IDC）
  - OCP 社区年度贡献数从 2 增至最高 114（年份对应关系文字层不清，存疑）[p3]
  - 非 x86 服务器营收 2025 年较 2024 年翻倍以上；2026 年 \$311B → 2030 年 \$763B [p6]（预测，IDC）
  - 企业电力顾虑：能源成本上涨 38.1%、外部供电容量 29.1%、电能质量 24.4%、冷却耗电 24.3%、电网输电容量不足 19.9% [p11]（IDC 调查 2026）
  - 液冷：31% 已在用，33% 计划 12 个月内实施，22% 在测试；未来 12 个月 35% 计划增加 10–20%、12% 增加 >20% [p13]（IDC 调查）
  - ESUN 发布基础规范（2026-04 Barcelona）；Open Silicon Photonics for AI Systems 工作流目标是标准化 CPO 以替代铜互连（2026-08 Taipei）；Meta Minipack3N 为 51Tbps 交换平台，DSF/NSF 架构 [p9]（引用）
  - Google、Microsoft、NVIDIA 在 800V 数据中心配电上对齐；面向 1 MW 机柜的低压配电框架 [p10]（引用）
  - Google Brazos 冷却 sidecar：闭环 60 kW 机柜液冷，可用于风冷旧机房 [p12]（引用）
- 提到的公司/客户/产品/标准：OCP Open Rack Wide、Open Data Center for AI、Meta Clemente（1RU，2×GB300）、ESUN、Open Silicon Photonics for AI Systems、Meta DSF/NSF、Minipack3N、SAI、FBOSS、LVDC WG、Mt Diablo（Diablo 400）、CDU Project、Google Deschutes、Castrol ON、Quantum Integration Initiative、S.A.F.E.
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（看图：OCP 基础设施支出 2020–2030 堆叠柱）；p9（网络里程碑：ESUN、硅光 CPO、DSF）

### P397 More-Tokens-Same-Megawatts-How-Agentic-AI-Rewrites-AI-Factory-Economics
- 讲者/机构：Imran Latif、Mohamed Eissa，Johnson Controls International [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [推理/算力/经济性]、[运维/可靠性/遥测]
- 核心主张：
  - 电网功率上限固定，但 IT 与冷却之间的比例可调；把冷却省下的 MW 转给计算，同样电费下产出更多 token [p12, p14]。
  - 用 LLM agent 闭环控制冷水机组设定点与 CDU 泵速，以 tokens/joule 作为奖励，在仿真中所有 agent 都提升了效率，但动作和 agent 增多后多数会过热；只看效率指标会放过不安全的控制器 [p18, p29]。
- 关键数据：
  - 全球数据中心容量 2025 年 77 GW → 2030 年 227 GW（3.0×，+150 GW，24% CAGR）；15 个来源预测区间 152–321 GW；每年新增 24→34 GW [p4]（看图，引用多来源预测）
  - 推理占 AI 算力比例 2023 年约 1/3 → 2026 年约 2/3；推理占模型生命周期算力成本 80–90% [p5]（引用 Deloitte、Gartner）
  - GB300 NVL72：单机柜最高 1,440 PFLOPS FP4 稀疏、120–140 kW/柜、\$3–4M/柜、37 TB 内存（20 TB HBM3e + 17 TB LPDDR5X）；对比 IBM Blue Gene/Q 4 柜 840 TFLOPS FP64、320 kW [p6]；算力密度约 17,000×、能效约 4,200×（精度不同，非同口径）[p7]（自报计算）
  - 芯片 TDP：H100 700W（2023）、B200 1000W（2025）、B300 1400W（2026）、Rubin 2300W（2027）；风冷上限约 1000 W/芯片 [p9]（看图）
  - 液冷对比风冷（8×H100）：吞吐 +17%、功耗 −16%、训练时间 −1.4% [p9]（引用 NVIDIA 白皮书 2025-10）
  - 500 MW 示意模型：IT 325→425 MW（+31%），冷却 175→75 MW（−57%），PUE 1.54→1.18，token/天 363T→476T（+31%），电费不变 [p14]（示意模型）
  - 仿真：3,360 颗 B200（420 节点×8），2 MW IT 负载；B200 32×32 RC 热网格，按真实 8×B200 遥测校准；冷水机组模型为 JCI York YVAM [p16]（仿真）
  - 每 600 s 决策一次，CHWS 范围 15–30°C，每回合 10 次决策；本地 agent 计算功耗约 10 W / 67.5 W [p17, p19]（仿真）
  - 场景 1（仅设定点，单 agent）：8/8 安全；reward +6.9%~+10.7%，partial PUE −6.4%~−9.7%（基线 7.33 tokens/J、pPUE 1.292）[p21, p29]（仿真）
  - qwen3:8b 实时运行：reward +10.7%、pPUE −9.7%、冷水机功率 −44.1%（约 570→320 kW，看图）、CHWS 升至约 30°C [p22]（仿真 + 看图）
  - 场景 2（设定点+泵速，单 agent）：5/8 安全，最佳 +11.5%、pPUE −10.3%（qwen2.5:3b）[p24, p25]（仿真）
  - 场景 3（双 agent 分控）：2/8 安全；过热的 6 个仍降低 pPUE 6–7% [p27, p29]（仿真）
- 提到的公司/客户/产品/标准：JCI、NVIDIA B200/GB300 NVL72、IBM Blue Gene/Q、JCI York YVAM、Ollama、llama3.1、qwen3、qwen2.5、phi3.5、gemma2、GPT-5.4-Mini、Claude-Haiku-4-5；OCP Data Center Facility、Thermal、Hardware Management 工作组
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（500 MW 前后对比：PUE 1.54→1.18、token +31%）；p29（三场景安全/效率汇总）

### P399 Overcoming OCP Adoption Barriers in European Data Centers（精简）
- 讲者/机构：Christoph Streit（ScaleUp Technologies CEO）、Jeroen Burks（ScaleUp / ThermoIT，OCP EMEA co-lead）[p1] | 类型：技术分享（市场采用）
- 方向归属（主/次）：主 [底座-机架/机械]（OCP 采用）；次 [底座-电力]
- 核心主张：
  - OCP 在欧洲的优势：电费高时直流配电和更高进风温度更划算，开放 BMC/固件可审计、生命周期由客户决定 [p6]。
  - 障碍在于认知（被视为超大规模专属）、19 英寸存量与托管合同、缺少本地集成商与 4 小时级支持、ODM 最小起订量和公共采购规则 [p8–p13]。
- 关键数据：
  - 直流配电 6 个 PSU 对比 60 个 [p6]（自报）
  - ScaleUp：首批 OCP 机柜约 4 年前 POC；柏林体验中心 2023、纽伦堡 2025（含 Liquid Lab）；OCP Marketplace 3 项服务、14 个产品的 Solution Provider [p4, p5]（自报）
  - 首批客户：电网运营商、大学、电商（均在德国）[p4]
- 提到的公司/客户/产品/标准：ScaleUp Technologies、ThermoIT、OCP Marketplace、OpenBMC、OpenStack
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（OCP 销售漏斗各阶段难度）

### P401 Recent-Open-Networking-Deployment-Feedback-and-Trends
- 讲者/机构：Sujay Gupta，Edgecore Networks [p1] | 类型：技术分享（部署反馈）
- 方向归属（主/次）：主 [Out 后端网络]（RoCE、SONiC、交换芯片）；次 [运维/可靠性/遥测]
- 核心主张：
  - AMD GPU 云的 RoCEv2 后端网络中，PFC/ECN 配合 DLB 能满足无损、低时延、高吞吐要求 [p3]。
  - 多厂商组合下的链路稳定性和 NIC/交换机 QoS 不一致（DSCP、MTU、PFC 优先级）是主要问题；作业完成时间变长时常规计数器看不出问题，需要查看 ECN/PFC 计数器并在交付前做 xCCL 集合通信基线 [p4]。
  - 社区版 SONiC 在 EVPN/VXLAN 特性组合与园区 AAA 方面不足，生产部署宜用经过验证的商业支持版 SONiC；社区应发布"Implementation Reports" [p6, p9, p10]。
- 关键数据：
  - AI 后端：2 层 rail-optimized Clos，Edgecore AIS800-64O（800G，51.2 Tbps，Broadcom Tomahawk 5）作 spine 与 rail leaf；AMD MI300X→MI355，每 GPU 一块 Pensando NIC [p3]（现网）
  - EVPN/VXLAN：100G 服务器链路，AS9736-64D 作 BGP RR（AS 65000），AS7726-32X 作 leaf/VTEP [p5]（现网）
  - 社区 SONiC 缺少的组合：DHCP Relay over VXLAN、MC-LAG over VXLAN、跨 VXLAN fabric 的 QoS [p6]（现网反馈）
  - EVPN 多归属 ESI all-active 下，MAC 老化/重学习/VM 迁移时对等体间同步不一致导致断连 [p7]（现网反馈）
- 提到的公司/客户/产品/标准：Edgecore AIS800-64O、AS9736-64D、AS7726-32X、AS7326-56X、AS7816-48X/64X、AS4625-54P；Broadcom Tomahawk 5；AMD Instinct MI300X/MI355、Pensando；SONiC；RoCEv2、PFC、ECN、DLB；Cisco ISE
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（RoCEv2 rail-optimized 拓扑 + 部署教训）

### P404 01_Bridging the Gap Accelerating Open-Source Agility on Cisco Silicon One
- 讲者/机构：Wei-Jen Huang、Masiuddin Mohammed，Cisco [p1] | 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络]（交换芯片、SONiC/FBOSS）；次 [Across 跨楼/园区/区域]（P200 scale-across）
- 核心主张：
  - 以通用 BSP、SAI 和可复用验证流程，加快 SONiC、FBOSS 等开源 NOS 在 Silicon One 上的落地 [p2]。
  - 三阶段验证（组件级、单机认证、解决方案级），BSP/数据面/SAI 层测试可高度复用，控制面中度复用，管理面需 NOS 专用测试 [p10–p12]。
- 关键数据：
  - Silicon One 家族：G200 51.2T、P200 51.2T（scale across）、Q200 12.8T、G300 102.4T、A100（OOB 管理/接入）[p3]（自报）
  - Wedge400C：Q200，12.8T，ODM，2021 年起生产部署；Wedge800C：G202，25.6T，32×800G OSFP（10G–800G）；Cisco 8501：G200，51.2T，与 Meta 合作的 OCP Inspired 系统；Cisco 8223：P200，51.2T，Cisco 自研 [p14]（自报）
  - 复用度：SAI/SDK 验证、性能与时延、光模块、制造测试为 FULL；QoS/PFC/RDMA 为 HIGH（PFCWD 需 FBOSS 专项验证）[p12]（自报）
- 提到的公司/客户/产品/标准：Cisco Silicon One、Meta、FBOSS、SONiC、sonic-mgmt、PTF、SAI Challenger、IXIA、OCP SAI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（Open-NOS 合作模式与平台/带宽/芯片对照表）

### P405 02_Closing the Observability Loop in SAI From Performance Telemetry to Pl
- 讲者/机构：Jai Kumar（Broadcom）、Ravindranath Kanakarajan（Marvell）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [Out 后端网络]（SAI/SONiC、交换芯片）；次 [运维/可靠性/遥测]
- 核心主张：
  - 不同厂商、不同芯片 profile 的硬件限制各异，现有 SAI 用零散的只读 *_RANGE 属性表达，存在膨胀、缺口和不一致；提出统一 API 在编程前查询约束 [p2, p5, p6]。
  - 新增 PerfMon 对象，在 SDK 边界测量每对象 SAI API 时延，用于路由收敛、快速启动和遥测配置的节奏控制 [p10, p11]。
  - 同样的问题也会出现在 UALink 等多厂商对象化接口，应尽早采用 [p13]。
- 关键数据：
  - Constraints API：SAI #2294（评审中）；PerfMon：SAI #2287（已合入 master，基于 2023 年 OCP 提案）[p3, p11]（自报）
  - sai_query_attribute_value_constraints() 返回 MIN/MAX/STEP/DEFAULT/ALLOWED_VALUES，上下文包括 object_type、object_key、attr_list、stage（INGRESS/EGRESS/BOTH）[p6]
  - 示例：PORT_ATTR_SPEED 光口 {100G, 200G, 400G}，铜口 {10G, 100G} [p7]
  - HFT（高频遥测）可达微秒粒度；最小上报间隔同时取决于 stat-id 与 report 对象属性 [p9]（自报）
- 提到的公司/客户/产品/标准：Broadcom、Marvell、OCP SAI、SONiC（STATE_DB、orchagent、syncd、gNMI）、TAM、UALink
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（发现限制—调参—测成本的控制器工作流）

### P406 03_DPU Sled Design Standard in a Modular SmartSwitch by Cisco and AMD
- 讲者/机构：Pirooz Tooyserkani、Murali Venkat，Cisco [p1]（与 AMD 合作）| 类型：标准进展
- 方向归属（主/次）：主 [Out 后端网络]（NIC/DPU、交换平台）；次 [底座-机架/机械]
- 核心主张：
  - Cisco 将开源模块化 SmartSwitch 的 DPU sled 设计（机械、PCB、供电、管理信号、平台软件 API），交换机可吸收 DPU，实现 in-network / bump-in-wire 部署 [p2, p3]。
  - 每个 DPU sled 作为机箱模块管理；下一代 sled 需支持 100G/lane 及更高功率与散热 [p12, p16]。
- 关键数据：
  - SmartSwitch TAM：2026–2030 CAGR 约 167%，2030 年 >\$7B [p3]（预测，未注来源）
  - 一代平台 Cisco 8102-28FH-DPU-O：Silicon One Q200L + AMD Elba DPU，2RU，总 12.8 Tbps（交换 11.2 Tbps + DPU 1.6 Tbps），28×400GbE QSFP-DD，x86 D2779 16C/128GB，DPU 32GB DDR4 + 64GB eMMC，2×2.3 kW PSU [p4]（自报）
  - Sled：每 sled 最多 2 颗 DPU；每 DPU 槽 400G（8×50G）；PCIe 4.0 x2（16 GT/s）每 DPU；最大 180 W/sled（12V）；最大气流 30 CFM；工作温度 0–40°C [p6, p8, p9]（自报）
  - PCB 7.670"×6.978"×0.093"；连接器为 Molex SpeedEdge 金手指 [p6, p10]
  - 框图：SW ASIC 到每 sled 2×200GE（8@50G），每 DPU 200G [p5, p7]（看图）
- 提到的公司/客户/产品/标准：Cisco Silicon One Q200L、AMD Elba（Pensando）DPU、Molex SpeedEdge、gNMI/gRPC、OCP Networking
- 首次/记录/SOTA 声明：无（宣布将开源 DPU sled 设计 [p2]）
- 推荐配图页：p5（看图：SmartSwitch 中 SW ASIC 与 DPU sled 的连接框图）

### P407 04_Meta 102.4T Ethernet Switch
- 讲者/机构：Rongchun Zhou、Reza Niazmand，Meta [p1] | 类型：技术分享（硬件贡献）
- 方向归属（主/次）：主 [Out 后端网络]（交换芯片、可插拔光模块）；次 [Up 机柜/超节点]（铜缆/背板、机柜级互连）、[底座-冷却]
- 核心主张：
  - Meta 第一代 102.4T 交换机 IceCube（Icepack 家族）采用无 PHY 设计和 flyover 铜缆，混合液冷/风冷 [p2]。
  - 当前 100T 平台上机柜级互连已到极限，下一代需要在铜缆技术、L11 光纤管理、电缆背板、光背板上创新 [p13]。
- 关键数据：
  - IceCube：2OU，Broadcom Tomahawk6C，64×OSFP，128×800GE 或 512×200GE 非阻塞；Meta 2×800G-DR4/-FR4 OSFP；与 Celestica 合作；部署于 ORv3-HPRv1 机柜 [p2]（自报）
  - 212G PAM4 flyover 铜缆（UPXR-OSFP），总 DP 长度 340 m（对比足球场周长 346 m）[p4, p5]（看图）
  - 散热：ASIC 与 OSFP 液冷约 85%，micro server、电源级、BMC 风冷约 15%；OCP BMQC 冷却液接口；多个漏液检测区 [p4]（自报）
  - 主板 370×265 mm，厚 5.62 mm ±7%，26+18=44 层 N+M，ENEPIG [p7]（自报）
  - 冷却液入口 30°C/40°C（AALC 或 FLC），约 6 LPM/blade；blade 最大典型功率 3,820 W（全部为 retimed 5nm DSP DR4 模块）；声压 63.3 dBA（30°C/6000ft）[p9]（自报）
  - IceCube-N 预览：NVIDIA Spectrum6 102T，212G PAM4 信号 100% PCB 走线，2×8 叠层 OSFP 笼 belly-to-belly，与 Accton 合作 [p11]（自报）
  - GTSW 机柜内光纤 8,192 根，在集成商处预布线；GTSW/STSW/ETSW 三种机柜同一高度、不同光模块/光纤配置 [p12]（自报）
  - 前面板 8 组 1×8 OSFP-RHS belly-to-belly，后部 48V bus bar 与 BMQC 进出水口 [p8]（看图）
  - 规范与设计包 2026 年 9 月提交 [p13]
- 提到的公司/客户/产品/标准：Meta IceCube/IcePack/IceTea/Anacapa/Santa Barbara、Broadcom Tomahawk6C、NVIDIA Spectrum6、Celestica、Accton、ORv3-HPRv1、OCP BMQC、Intel Icelake-D、NetLake、RunBMC AST2620
- 首次/记录/SOTA 声明：Meta 首代 Icepack 102.4T 交换机家族 [p2]
- 推荐配图页：p5（看图：212G PAM4 flyover 铜缆，总长 340 m）；p3（看图：IceCube 系统架构）

### P408 05_More Signal, Less Noise Improving AI Cluster Returns Through Standardi
- 讲者/机构：Chris Collins，Credo（VP of Product, DSP and Optical）[p1] | 类型：技术分享 / 标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [Out 后端网络]（可插拔光模块）
- 核心主张：
  - AI fabric 光模块数量巨大，罕见故障也有实际影响；裸金属服务器使运营方无法访问服务器端模块；链路抖动等间歇故障难复现 [p2]。
  - 增强遥测光模块把链路分成交换机电侧、光路、主机电侧三段监测，并从交换机远程读取对端遥测和非易失事件日志，Link Health Score 取最差类别分而非平均 [p3, p4, p6, p7]。
  - OCP Enhanced Telemetry Optics 软件规范基于 CMIS CDB，一条命令返回身份、健康分、遥测、告警 [p9]。
- 关键数据：
  - 试验：16 个交换机端口 400G DR4，16 台服务器 2×200G DR2，共 48 个收发器符合 OCP Enhanced Telemetry Optics Spec；Arista 交换机，远端 NVIDIA CX7 NIC [p10]（实验；设备型号为看图）
  - 衰减分组：0 dB（端口 9/17/18/19/20）、5 dB（1/3/5/6/10/11/12）、10 dB（25–28）[p10, p14]（看图）
  - Link Health Score：0 dB 为 80，5 dB 为 60，10 dB 为 40 [p15]（实验）
  - 故障案例：一个端口高 BER，远端主机侧健康分 40、电眼高度 [26, 29, 31]（正常约 77–104），定位为服务器模块电侧问题，清洁重插后恢复；该链路 pre-FEC BER 1.50E-06 [p11]（实验）
  - 启动检查：端口 18 media 健康分 60（MPI），清洁光纤即可修复，传统光模块安装时通常检测不到 [p13]（实验）
  - 自动化流程可在几分钟内处理整个 fabric [p12]（自报）
  - 示例：五个类别 94/92/91/89/93，平均 92，上报健康分取最小值 89 [p6]（看图，示例数字）
- 提到的公司/客户/产品/标准：Credo ZeroFlap Optics、OCP Networking Optics Reliability Subgroup、CMIS CDB、Arista、NVIDIA CX7
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（看图：链路三段监测示意）；p15（衰减与健康分对应）

### P409 06_NVIDIA SDK + FBOSS Building Production-Ready AI Network Fabrics
- 讲者/机构：Harish Krishnamoorthy、Alan Elder、Tom Zhu（NVIDIA）；Parvez Shaikh（Meta）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络]（交换芯片、SAI/NOS、CPO）；次 [运维/可靠性/遥测]
- 核心主张：
  - 以 OCP SAI 作为契约边界，再加上 Spectrum SimX 功能仿真器，SDK、NOS、测试和部署可在芯片到货前并行推进；硬件到货变成认证节点，而不是起点 [p8, p14]。
  - NVIDIA 与 Meta 在设计、测试、部署各阶段测试驱动协作，避免"dead-on-arrival" [p11]。
- 关键数据：
  - 典型 AI 集群单 zone：288 super spine（8×36）、192 spine（8×24）、144 ToR（6×24）、48 机柜、3,456 GPU；每柜 72 GPU（GB300），3 个 SU/柜，24 GPU/SU；8 个 plane；上层最多 3:1 收敛，其余 1:1；链路 400G [p4]（自报拓扑）
  - Spectrum-6：102.4 Tb/s，512×200G 或 128×800G，支持可插拔与 CPO，Adaptive Routing、拥塞控制，WJH、带内遥测 [p6]（自报）
  - SimX：VM 内通过 PCI 模拟 ASIC，支持转发表、L2/L3/ACL，不模拟 QoS、L1 协议 [p8]（自报）
  - 在 SimX 上约 6 周完成功能开发与测试；Meta 硬件首次到货约 1 周内测试通过率 90%；约 2 个季度达到全部通过并可进入集群认证 [p13]（自报）
  - 联合增强：SDK-ISSU 无损升级、Mirror on Drop（利用 TAC）、硬件丢包原因计数、基于 PTP 的电缆长度估计 [p12]（自报）
- 提到的公司/客户/产品/标准：NVIDIA Spectrum-X / Spectrum-6、NVIDIA SDK、OCP SAI、SimX、Meta FBOSS、GB300
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（单 zone 3,456 GPU 三层拓扑及规模）；p14（SAI + SimX 并行开发时间线）
