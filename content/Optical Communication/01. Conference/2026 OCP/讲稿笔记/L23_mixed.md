---
title: "L23_mixed"
tags:
  - OCP2026
  - 讲稿笔记
---

# L23 笔记：Test & Validation, Time Appliances, ai-clusters, ai-computing-continuum, ai-open-data-center, ai-open-dc-power-distribution（低相关精简版）

### P097 AI-Native Hardware Validation- Building a Local-Context Agentic Test and Debug Platform
- 讲者/机构：Wenxi Yan、Cheng Ying Chen（Microsoft，Principal Systems Engineer）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]（硬件验证）；次 [推理/算力/经济性]
- 核心主张：
  1. "context + tools + guardrails"把通用 LLM 变成硬件验证 agent；价值在自建的 MCP/skills（KB、McConsole 执行层、Log_Analyzer、日志归档），基础模型和 agent harness 直接采用外部最优 [p2][p4]。
  2. 三年演进：2024 AI 写脚本/调试 → 2025 AI 按预定义错误签名分类日志 → 2026 AI 驱动完整循环（连节点、跑测试、日志指纹、查 bug 史并复现、写回 bug/状态） [p3]。
- 关键数据：（无量化结果）提出 OCP T&V JSONL 作为步骤/诊断分析接口（提议） [p6][p7]；开源仓库 microsoft/log_analyzer、microsoft/mcconsole、ocp-diag-core [p10]。
- 提到的公司/客户/产品/标准：Microsoft、McConsole、Log_Analyzer、MCP、OCP T&V JSONL、ocp-diag-core
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（AI-native 验证栈分层）；p6（intent→adapter→SUT→日志归档的执行契约）

### P098 CTAM- Three Years of Bridging Hyperscalers and Suppliers Through GPU Accelerator Compliance
- 讲者/机构：Basha Khader（AMD）、Aditya Mishra（Nvidia）| 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]（GPU FW 合规测试）；次 [底座-机架/机械] 无
- 核心主张：
  1. 供应商"自测通过"与超大规模"实验室失败"之间缺乏共同测试与可信数字，CTAM 作为共同验收标准 [p3]。
  2. 2026 年起 CTAM 结果将被超大规模要求作为固件验收条件（讲者表述） [p4]。
- 关键数据：
  - 版本：v0.1 2024-02（12 项 health check）；v1.0 2025-03 正式；v1.1 2025-06 OPP 评分模型；v1.2 2026-08，41+ 测试、4 个 domain，PLDM v1.3 [p4]（自报）
  - 路线：EOY 2026 PLDM v1.3 + PLDM bundling；2027-06 mockup/Redfish 仿真、AI skills、OCP spec 1.9/2.0、recovery image；愿景含 GPU RAS API [p6]
- 提到的公司/客户/产品/标准：NVIDIA、AMD、Microsoft、PLDM、Redfish、OCP GPU FW Update / Manageability Interfaces / RAS 规范、ocp-diag-ctam
- 首次/记录/SOTA 声明：自称"de-facto yardstick"/"gold standard" [p4]（自报）
- 推荐配图页：p4（CTAM 版本时间线）

### P100 From Spec to Sign-off - How Microsoft is transforming the platform validation workflow leveraging AI
- 讲者/机构：Rahul Shah（Microsoft Partner/Director SW Eng）、Vikram Vemulapalli（Microsoft VP Hardware Test, Validation & Quality）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [推理/算力/经济性]
- 核心主张：
  1. NPI 平台验证从 spec 审阅到 sign-off 全流程用专用 agent 改造（SpecInsight.ai、SchematicInsight.ai、TestPlan.ai、TestCase.ai、TestContent.ai、Debug Agent、BugEfficacy.ai 等） [p8][p11]。
  2. 经验：领域数据标准化先行，guardrails 随 agent 同发，sign-off 保留人工 [p13]。
- 关键数据（自报）：端到端周转时间降低 60%；sustaining qualification 周转降低 75%；测试代码开发 100% 自动化 [p13]。演示中 Deep Lens 标出 1 个 WHEA 错误和 7 个热/功耗事件 [p12]。
- 提到的公司/客户/产品/标准：Microsoft、Validation IQ、ADO、M365 Copilot、Teams、Virtual Client、OCP T&V schema
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（8 步 spec-to-sign-off 流程）

### P103 Product Intercept learnings and Compliance measurement for Diagnostics Standardization
- 讲者/机构：Jennifer Lee（Intel）、Rajat Madhusudan（Microsoft）| 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  1. CPACT 检查 CPU 供应商是否符合 Hyperscale CPU Impactless FW Update 与 RAS/Debug/Diagnostic 规范，覆盖 x86 与非 x86 [p2]。
  2. 标准化诊断产物（Diag Recipe、DRC-DRD map、扩展 OCPTV diag log），分层诊断模型有望缩短 MTTR（讲者表述，无数字） [p4][p9]。
- 关键数据：规范/工具诊断部分版本由 0.7 升到 0.9 [p2]；DRD 字段含 message/component/severity/category/action/urgency/confidence，示例 confidence=99 [p5 看图]
- 提到的公司/客户/产品/标准：Intel、Microsoft、CPACT、OCPTV、DRC/DRD
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（诊断流程总览）；p5（DRC-DRD map JSON 示例）

### P104 T&V Update- Wind Tunnels & Bonsai servers
- 讲者/机构：Arun Darlie Koshy、Jean-Marie Verdun（HPE）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：
  1. Wind Tunnels：私有 AI/ML 集群，输出 OCPTV 结构化结果（vLLM on HPE 设备） [p3][p4]。
  2. 固件流式启动：用 Ethernet+中央仓库在每次 boot 拉取已验证固件，不需要 BMC；Bonsai 为无 OS 的微型节点，程序存储在复位时清空并重新流式加载 [p6][p13]。
- 关键数据：PoC 固件镜像 344 kB；4 MB 约 3.14 s ≈ 1.27 MB/s（峰值约 1.6 MB/s）；TFTP 块 1400 B（实验）[p10]；SPI-NOR 为 Winbond 32 MB，RP2350+W5500 [p9]；Bonsai 节点 2–8 核、4 GB/core、1/2.5/10 Gbps [p13]；目标 sub-\$5，PoC 硬件预算约 \$2000 [p15]；"500M+ websites" [p14]（引用，无出处）
- 提到的公司/客户/产品/标准：HPE、RP2350、W5500、TinyGo、AWS Firecracker、ocp-diag-windtunnel、ocp-fwupdater-PoC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（固件流式 PoC 架构）

### P105 A timecard as a resilient A-PNT custom solution
- 讲者/机构：Yair Neugeboren、Anil Reddy（Oscilloquartz）| 类型：厂商技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]（时间同步）；次 [安全]
- 核心主张：
  1. 以 PCIe/M.2/USB 形态的 Timecard 放入通用服务器，取代独立 1U/2U 授时设备，靠近计算 [p2]。
  2. GNSS 被干扰/欺骗会使一个参考变成全数据中心故障域；提出 GNSS-assured OCP TimeCard 的 TAP 贡献（多源校验、告警与源隔离、确定性切换、开放遥测）（提议，里程碑待 TAP 对齐） [p16 看图][p18]。
- 关键数据：PTM 对比（OCP TAP Webinar 2023）：无 PTM 空闲 P-P 37 ns/均值 504 ns；无 PTM 加载 2148 ns/1297 ns；有 PTM 空闲与加载均 15 ns/2 ns [p6]；演示系统 OSA5400 + Intel I226 + Z890，ptp4l G.8275.1 [p7]；P1952 R-PNT 五级 resilience（Detect/Recover/Resist/Withstand/Verify） [p13]
- 提到的公司/客户/产品/标准：Oscilloquartz、OSA5400、OCP-TAP、IEEE P3335、IEEE P1952、PTM、White Rabbit
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（Timecard 架构图）；p16（GNSS 共享风险）

### P106 Bounding Time Uncertainty in Distributed Systems
- 讲者/机构：Kishan Shenoi、Gary Giust（SiTime）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]（时间同步）
- 核心主张：
  1. PTP 做同步，数据中心必须给出端到端时间不确定度边界，否则有静默数据错误；界太松浪费等待，太紧导致错序 [p2][p4]。
  2. 提议用 Total Time Uncertainty (TTU) 作为振荡器的单一规格：TTU = TUPeak + Q×TURMS，Q 由 PE=N×erfc(Q/√2) 迭代求解（N 为部署振荡器数） [p5]。
- 关键数据（示例振荡器数据表，自报）：伺服带宽 0.1/0.01/0.001 Hz 下 TURMS 为 0.13/2.6/82 ns，TUPeak 为 17/181/1856 ns（条件：TURMS 为环境温度 ±1°C，TUPeak 为 −40~105°C 间最高 6°C/min） [p7]。透明时钟（交换机）的振荡器 TTU 线性叠加；普通时钟（NIC）被伺服高通滤波 [p6]
- 提到的公司/客户/产品/标准：SiTime、IEEE 1588、EPPS、XO/TCXO/OCXO
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（TTU 数据表）

### P107 Clock-Aligned Telemetry for AI Clusters- From BMC to GPU to Fleet
- 讲者/机构：Lukas Landgraf、Ahmad Byagowi（turbalance）| 类型：技术分享（含标准提案）
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  1. 有用算力要在六条证据通道（GPU/Host/BMC/Placement/Fabric/Time）上定位，样本须带时钟映射与 WOU（时间不确定窗口），"不支持/不可达"必须显式表示，不得补零 [p3][p4][p6]。
  2. 四道门判断信号是否可操作：Supported、Fresh、Time-valid、Traceable [p13]；跨层对比阶梯分六级（单指标→主机→机架→集群→Fleet→全局基线） [p11]。
- 关键数据：live path 目标 1 秒采样 [p7]；示例（说明性）PTP 锁定 WOU ±12 µs vs NTP slewing 偏移 +143 ms、WOU ±160 ms [p5]；"未宣称实测结果"，验证基于 DGX/GB10 级异构实验室节点 [p9][p12]；提议 30 天定字段字典、90 天出示例 bundle 与一致性样例 [p15]
- 提到的公司/客户/产品/标准：DCGM/NVML、Redfish、Kubernetes、OpenTelemetry、Tangle、Apache Iceberg、PTP/NTP/chrony、Prometheus/Grafana
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（Tangle 时钟映射与 WOU）；p13（四道门）

### P112 Raspberry Pi Compute Module based Open Time Server Cluster (OTS-C) for Resilient Timing at the Edge
- 讲者/机构：Wil Myrick（ENSCO，Chief Technologist）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]（时间同步）
- 核心主张：OTS-C 在 Open Time Server 参考架构上扩展为集群配置以提高边缘授时韧性 [p3][p4]；开发系统用 chrony 探索时钟合并算法 [p5]。
- 关键数据：6 个 CM4 各接 GNSS 接收机组成集群；合并前单路 offset 多在约 ±600 ns、偶发尖峰到约 ±1 µs（个别约 1.8 µs），合并后集中在约 ±250 ns（实验，看图，约值） [p6][p7]
- 提到的公司/客户/产品/标准：ENSCO、Raspberry Pi CM4、chrony、OCP-TAP、OTS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（OTS-C 框图）；p7（合并跟踪对比）

### P116 03_Beyond Physical Digital Twins Why Logical Digital Twins Are Essential
- 讲者/机构：Avi Alkobi（NVIDIA，Sr Director）、Abhijit Lahiri（Keysight，Sr Director）| 类型：技术分享
- 方向归属（主/次）：主 [推理/算力/经济性]（AI 工厂仿真）；次 [运维/可靠性/遥测]、[Out 后端网络]
- 核心主张：
  1. AI Factory 需要 Logical Digital Twin 覆盖 Plan/Deploy/Operate（Day 0/1/2），每次基础设施变更先在孪生中验证 [p3][p5]。
  2. 多种仿真（节点/集群/性能/AI agent 作仿真器）需并存，各有保真度与规模取舍 [p17]。
- 关键数据（自报）：无仿真：建实验室 3 个月 + 软件 bring-up 2 个月 + 多租户 1 个月 = 6 个月；有 DSX Air 仿真：建实验室 3 天、bring-up 0 天、多租户 1 周，合计 1.5 周（由文字层顺序推断，存疑）；称 24x 更快验证 [p8]；传统实验室 vs 孪生：128 GPU vs 1K+ GPU，80K vs 100K+ tokens/s，30 天 vs 30 分钟设置，验证快 60–70%，go-live 提前 3–6 个月 [p9]；支持千台交换机规模测试 [p8]
- 提到的公司/客户/产品/标准：NVIDIA DSX Air、Spectrum-6、Keysight KAI Inference/Data Center Builder、OCP Digital Twin Initiative
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（有/无仿真时间对比）；p9（传统实验室 vs 孪生）

### P118 05_CLARA Automated AI cluster architecture design tool
- 讲者/机构：Rainy Yan、Reece Neff、Hengze Ye、Jerry Cheng（Lenovo ISG）| 类型：技术分享（开源工具）
- 方向归属（主/次）：主 [底座-机架/机械]（集群设计/平面布局）；次 [Out 后端网络]（拓扑生成）
- 核心主张：
  1. CLARA 是 NetBox（开源 DCIM）插件，把 AI 集群设计（硬件选型→拓扑生成→机架立面→平面图→BOM）做成统一开源流程，带自动约束检查 [p4][p5 看图]。
  2. 现有拓扑工具只覆盖"工厂式"简单结构，满足不了多 rail、多 plane；平面图受房间几何、CDU 管路、供电覆盖影响 [p8][p10]。
- 关键数据：幻灯片称 GPU 与电力成本只占 TCO 的 50%，交换机与线缆正成为主要成本项（引用 Solnushkin 2014 博士论文）[p3]；平面图用模拟退火，代价函数 α·网络长度 + β·CDU 管长，优化时间 <10 分钟（自报）[p11]；示例拓扑 XOC-1k with OPG-256（rail 优化、多 plane）[p9]；预计开源时间 2027 年 2 月 [p13]
- 提到的公司/客户/产品/标准：Lenovo、NetBox、XOC-N system architecture（OCP 2026-01）、OPG-256
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（CLARA 流程）；p9（多 plane 拓扑）

### P123 AI-Computing-Continuum-Building-Open-Infrastructure-Standards-for-the-Next-Wave-of-AI
- 讲者/机构：面板：Andi Huels（BluskyAI Data Centers）、Kevin Cochrane（VULTR）、Jacob Yundt（CoreWeave）、Sanee Iqbal（Ex TogetherAI）、Nilesh Shah（主持）| 类型：面板（仅 1 页标题页）
- 方向归属（主/次）：主 [推理/算力/经济性]
- 核心主张：无正文内容可读（仅嘉宾页）。
- 关键数据：无
- 提到的公司/客户/产品/标准：BluskyAI、VULTR、CoreWeave、TogetherAI
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P124 AI‑Ready Network Infrastructure- Practical Realities of High‑Power, Liquid‑Cooled Rack Integration
- 讲者/机构：Arihant Jain（Arista）、Rob Nance（Jabil）| 类型：技术分享
- 方向归属（主/次）：主 [底座-机架/机械]；次 [底座-冷却]、[Up 机柜/超节点]
- 核心主张：
  1. 网络从单台风冷交换机变为液冷、整机架交付的网络机架，集成风险从局部变系统性 [p3][p4]。
  2. 各客户 ORv3 网络机架设计差异大，专有件增多、成本上升；呼吁统一线缆管理与冷却 manifold/QD 接口，并协调 Cooling Environments、Rack & Power、Networking 工作 [p7][p9]。
- 关键数据（自报，厂商对比）：Legacy 交换机 ≤51.2T、ASIC <500W、风冷、机架 100–200 根光纤；AI 时代 102.4T 及以上、ASIC >1000W、液冷、机架 2000+ 根光纤 [p3]；网络机架 48V ORv3 busbar、50 kW+/机架，光纤管理区 2000–4000 根 [p4][p5]；旧模型每台交换机 1–2 kW [p4]；manifold 当前针对 2U 交换机，其他高度需重新设计 [p8]；Jabil 与 Arista 有客户每年需数千机架、每周数百 [p9]
- 提到的公司/客户/产品/标准：Arista、Jabil、ORv3、UQD、UQDB、BMQC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（旧/新交换机与机架对比）；p5（网络机架立面要素）

### P127 Beyond GPUs- Building the Open Operations Layer for AI Factories and Token Economies
- 讲者/机构：面板：Naren Shankar（hosted.ai）、Preeti Vasaikar（Percepteye）、JM Hands（FarmGPU）、Abilash Menon、Peter Sheh（Crusoe）等 | 类型：面板（仅 1 页标题页）
- 方向归属（主/次）：主 [推理/算力/经济性]
- 核心主张：无正文内容可读。
- 关键数据：无
- 提到的公司/客户/产品/标准：hosted.ai、Percepteye、FarmGPU、Crusoe
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P131 Customer-Contextual Fault Management for Bare Metal GPU Infrastructure
- 讲者/机构：Aimer Bhat、Jim Britton（Oracle，OCI）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：
  1. 裸金属 GPU 下，云厂商因安全策略无法装 in-band agent，故障特征客户可见而云侧不可见；客户提交 in-band 证据与 OCI 带外遥测结合，改善诊断与可用性 [p3][p7]。
  2. CREW 流程：Report → Sanitize（隔离沙箱）→ Triage → Repair & Track → Learn & Automate，目标逐步用平台自动信号取代客户提供的诊断；邀请共同撰写 OCP 白皮书 [p6][p7]。
- 关键数据：GB200 平台某一 AD 部署的月度 incoming terminations（Apr 25–May 26）：Jun 25、Sep 25 两个高峰，Jan 26 引入 CREW 后总量与 Customer Return 逐月下降，May 26 最低；图上无绝对数值（现网，看图）[p5]
- 提到的公司/客户/产品/标准：Oracle OCI、GB200、ComputeReportedFaults API、OCP RAS API、OCP GPU Management
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（CREW 引入前后 terminations 趋势）；p4（裸金属节点各网络与 in-band 错误来源）

### P139 MX v1.1- Advancing Open Standards for Low-Precision AI with MicroXcaling formats
- 讲者/机构：Partha Maji（Microsoft，Partner Director）；合作方 AMD、Arm、Google、Intel、Meta、Microsoft、NVIDIA、Qualcomm | 类型：标准进展
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [In 封装内]（数值格式）
- 核心主张：
  1. OCP MX 是开放的低精度格式族（共享 scale X、私有元素 Pi、块大小 k），1.1 版是澄清与实现指导，保持互操作 [p3][p4]。
  2. 厂商私有格式导致碎片化；标准需早定，因软件前置期长 [p9]。
- 关键数据：MX 1.1 更新：新增 expAdj(V) 缩放项；E8M0 更名 UE8M0（bias 127，范围 −127~127，无 Inf/Zero，单一 NaN 编码）；FP8 转换须支持 SAT/NONSAT 模式 [p5–p8]；称计算成本随精度二次方、内存带宽与容量随位宽线性变化（讲者表述）[p11]；硬件支持列表：Microsoft Maia、AMD MI300、x86 ACE v1、Intel Gaudi 2/3、NVIDIA Blackwell、Qualcomm Cloud AI 100、AWS Trainium3、d-Matrix Corsair [p10]
- 提到的公司/客户/产品/标准：见上；PyTorch、cuDNN、CUTLASS、OpenVINO、Triton、ONNX；OFP8
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（MX 软硬件支持清单）

### P154 USB to Rule Them All- One Manageability Interface for AI Platforms
- 讲者/机构：面板：Mariusz Oriol、Kasper Wszolek（NVIDIA）、Bharat Pillilli（Microsoft）、Mohan J. Kumar（Oracle OCI）、Samer El-Haj-Mahmoud（Arm）、Supreeth Venkatesh（AMD）| 类型：面板
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：传统边带接口（I2C/SMBus、I3C、VDM、RBT、SPI、GPIO、LTPI 等）带宽低、引脚多、SI 难，各厂商重复解决发现/升级/恢复/调试；提议在 OCP 内收敛到 USB（MCTP over USB、PLDM/SPDM、OCP Recovery over USB、Caliptra USB、OBMF-ICP v1.0 over USB）[p3]。
- 关键数据：无量化数据
- 提到的公司/客户/产品/标准：MCTP、PLDM、SPDM、NC-SI、Redfish、Caliptra、OCP OBMF-ICP v1.0
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（问题与 USB 收敛方案）

### P162 05_Bridging the AI Continuum Trust, Orchestration, and Open Standards
- 讲者/机构：面板：Çağatay Yılmaz（RISE，主持）、Dirk Blevins（Intel DCG）、Raúl Álvarez（OCP）、Steven Yates（Federant）、Vincent Nguyen（HPE Fellow）| 类型：面板（含工作流提案）
- 方向归属（主/次）：主 [安全]；次 [推理/算力/经济性]
- 核心主张：
  1. AI 工作负载正扩散到超大规模之外的整个算力连续体，带来运维与安全问题；提议成立 AICC Deployment Software Workstream，制定可信 AI 部署的开放规范与参考实现 [p6]。
  2. 可信执行流程：数据所有者发布作业与规则→执行方按统一硬件描述拉取→芯片度量并签名证据→独立验证方通过后释放密钥→enclave 内运行并产生签名 receipt→断链自主运行、恢复后重新验证并同步 [p4][p5]。
- 关键数据：无量化数据
- 提到的公司/客户/产品/标准：RISE、Intel、Federant、HPE、OCP AICC、McKinsey Data Center Demand Model（引用图）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4、p5（8 步可信作业流程，带贸易类比）

### P166 09_Two Years of x86 Ecosystem Collaboration Open Infrastructure, AI Readi
- 讲者/机构：Robert Hormuth（AMD）、Jeff McVeigh（Intel）；面板含 Red Hat、HPE、Google、Microsoft | 类型：标准进展/面板
- 方向归属（主/次）：主 [推理/算力/经济性]
- 核心主张：过去 x86 厂商各自推特性造成分叉，生态做额外验证或取最小公分母；新做法：共同讨论工作负载需求、联合制定特性规范、在实现上竞争 [p2][p3][p5]。
- 关键数据：两年成果列表：FRED（中断模型）、AVX10（可移植向量）、ACE（AI 矩阵乘加速）、APX（更多寄存器/ISA 特性）、MTT（统一内存标记）[p6]；无性能数字
- 提到的公司/客户/产品/标准：AMD、Intel、FRED、AVX10、ACE、APX、MTT
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（五项联合成果）

### P167 01_800 VDC AI Factories From Architecture Alignment to Industry Deploymen
- 讲者/机构：Mike Tu（NVIDIA Principal Electrical Engineer）、Jared Huntington（NVIDIA Power Architect）| 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. 机柜功率从 Gen1 145 kW（54 VDC）→Gen2 330 kW→Gen3 570 kW（800 VDC 进 PSU、100% 液冷）→Gen4 800 VDC 原生，故需要 800 VDC [p3 看图]。
  2. 三种部署：A Power Rack（机架级）、B Power Center（集群级）、C Power Block（数据大厅级，SST，7 个 DC power block，6+1 冗余，可兼作 DC UPS，面向新建）[p4 看图][p6–p11]。
- 关键数据：Option A power rack 660 kW，415–480 VAC 输入 12–100A whip，800 VDC 输出 8×125A DC 缆，机架内 1RU DC/DC power shelf 90 kW/台 [p6]；Option C SST 室外级、5 MVA 输入 [p12]；常规路径 7 级对 800 VDC 路径 4 级 [p13 看图]；设备就绪：A Q3 2026、B Q2 2027、C Q1 2028 [p17 看图]；DSX 现状 VR NVL72 需 8×100A whip（AC）[p5]；800 VDC 连接器 125A/157A [p9][p10]
- 提到的公司/客户/产品/标准：NVIDIA、GB200/GB300、Vera Rubin NVL72、DSX、SST、ESS、UL、MCCB/SSCB
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（机柜功率代际与 800VDC 必要性）；p4（A/B/C 部署选项）；p17（设备就绪时间线）

### P169 03_Beyond the Build Autonomous Robotics and the Future of Data Center Ope
- 讲者/机构：面板：Joel Chakkalakal（PHS West，主持）、Shashank Gupta（Fleet Data Centers）、Evan Johnston（Microsoft）、Maureen Tate（NVIDIA）、Rob Lawson-Shanks（Molg）| 类型：面板
- 方向归属（主/次）：主 [底座-机架/机械]
- 核心主张：数据中心运维需要全自动化（物料搬运、监控、操作与维修）；加入 OCP DCF DC Automation 子项目，近期出自动化机架/服务器搬运参考设计及园区内微型自动维修工厂 [p8]。
- 关键数据：预计 2030 年技术员缺口约 500K；机架重 7,500+ lb（自报）[p8]；Molg 提到全球电子废弃物每年超过 6000 万吨 [p7]
- 提到的公司/客户/产品/标准：OCP DCF DC Automation、OCP ORW
- 首次/记录/SOTA 声明：无
- 推荐配图页：无（以嘉宾简介为主）

### P170 04_Can the Industry Sustain AI The Water-Energy Nexus Debate
- 讲者/机构：Brian Jabeck（DLB，主持）、David Quirk（DLB）、Rob Coyle（OCP）、Michael Obradovitch（Nalco Water/Ecolab）、Megan Schneider（Accenture）| 类型：面板
- 方向归属（主/次）：主 [底座-冷却]（水-能耗）；次 [底座-电力]
- 核心主张：
  1. 数据中心用两次水：现场（utility meter）与电源侧（发电），"不用水"只是水上移；需用 WUE→WUEsource→WUI→WUC 指标栈 [p4][p5]。
  2. 呼吁可行的框架与 WUC（Water Usage Credits，参照 REC 的信用/补偿）[p6][p9]。
- 关键数据（引用 ASHRAE Journal 系列，Quirk et al., 2026）：现场+电源水（gal/MWh）：风冷 0 + 300–500；绝热 0–105 + 300–500；蒸发 450–740 + 300–500，合计 750–1,240 [p4]；不同冷却设计现场用水范围 100×；PJM 容量价格两年约 10× [p3]；San Diego \$9.36/CCF vs Milwaukee \$1.69 [p7]
- 提到的公司/客户/产品/标准：ASHRAE、WRI Aqueduct、iMasons Climate Accord、WUE/WUI/WUC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（冷却方式的站内/电源侧用水表）

### P171 05_Flexibility the Grid Can Count On Turning Curtailable Load Into Interc
- 讲者/机构：Sean James（NVIDIA Distinguished Engineer）| 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. AI 的约束已从发电转为并网排队；电网有闲置余量，若新负载在稀缺时段让路即可接入 [p2][p3]。
  2. 钝性削减（0.5% = 177 小时硬停机）违反可用性条款，应做"有界、可验证"的弹性：调 GPU 功率上限与冷却、用储能/自备电、迁移非紧急作业 [p6]。
- 关键数据（引用 Duke Nicholas Institute，2025-02，22 个 balancing authority）：年削减 1.0%（366 h）→126 GW；0.5%（177 h）→98 GW；0.25%（85 h）→76 GW≈美国峰值负荷约 10% [p3]
- 提到的公司/客户/产品/标准：NVIDIA DSX、AI Factory Flex、BESS、POI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（三档削减率对应可接入 GW）

### P172 07_Open Systems for AI Why Open Communities Are Essential for the Next Er
- 讲者/机构：Michael Sweeney（Phaidra，AI Factory Architect）| 类型：主题演讲
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：行业若不自我规范会被监管（以 2003 大停电、1975 Asilomar 类比）；用开放数据交换连接 IT/OT，统一 tag 命名；GPU 已是基础设施控制信号 [p3–p12][p13]。
- 关键数据：2026 Q1 美国数据中心项目被阻/延迟 \$130B，相当于 2025 全年；14+ 州有活跃暂停令；40%+ 有争议项目提及用水（引用 Data Center Watch）[p2]
- 提到的公司/客户/产品/标准：Phaidra、OCP DC Facility - Data Center Telemetry、Open223、NVIDIA DSX Exchange
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（IT/OT 数据交换四层架构）

### P174 COMMISSIONING LIQUID COOLED DATA CENTERS WITH COMPUTING EQUIPMENT FOR OPERATIONAL READINESS
- 讲者/机构：主持 Pardeep Shahi（NVIDIA）；面板 Vahideh Radmard（NVIDIA）、Sara Hitt（Vertiv）、John Herboth（Glumac）、Eric Kumar（Google）| 类型：面板
- 方向归属（主/次）：主 [底座-冷却]
- 核心主张：
  1. 传统 IST 用静态电阻负载，只回答"能否支撑设计负载"；需增加 Level 5b 用真实算力负载验证瞬态响应、PID 整定与运行边界 [p3][p5][p9]。
  2. 5b/5c 边界测试须可重复、可观测、可逆，并有预设中止条件；含 24–72 h burn-in [p10]。
- 关键数据：调试等级 5a IST→5b 性能验证→5c 模拟故障→6 移交培训→7 持续调试(MBCx) [p3]；液冷负载箱需合规 ISO 4406 颗粒清洁度 [p8]；5b 五步：负载前准备、AI workload 功率验证（从 idle 到 POR 到最低功率上限）、风/液流 PID 整定、动态管理与验收、数字孪生校准 [p9]
- 提到的公司/客户/产品/标准：NVIDIA、Vertiv、Glumac、Google、LCLB、TTV、CDU、ISO 4406
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（IST 与真实负载验证缺口）

### P175 Challenges for High Density Workloads in Modular Data Center
- 讲者/机构：Karl Robe、Daniel Robbins（OCP Modular Data Center subgroup 联席主席）| 类型：标准进展
- 方向归属（主/次）：主 [底座-机架/机械]；次 [底座-冷却]、[底座-电力]
- 核心主张：高密度使模块化数据中心设计基础改变；液冷与风冷收敛速度快于机架、围护、冷却、控制与生命安全的接口；呼吁定义开放 HAC 边界与 vendor-neutral 的 MDC-AI HAC 参考规范，含 FAT/SAT 最小证据 [p2][p18][p19]。
- 关键数据：无量化数据（七项挑战：机架密度不均、机架配电与故障协调、液冷与残余风冷与瞬态热、空间/重量/运输/维护、控制/故障响应/生命安全、供应商接口、可重复验收测试）[p3]
- 提到的公司/客户/产品/标准：OCP MDC 子组、HAC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（七项挑战）

### P176 Enabling Grid-Compliant Data Center Growth Through Advanced Energy Storage
- 讲者/机构：Jason Barmann（EPC Power，Director Data Center Products）| 类型：厂商技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [存储]（储能）
- 核心主张：
  1. AI 负载是电网风险：多 MW 秒级阶跃、次同步振荡；ramp rate、ride-through、振荡阻尼已是并网标准要求而非特例 [p2][p3][p10]。
  2. ESS 作为灵活缓冲，在 POI 呈现稳定合规接口；需要亚周波级的高级控制（Agile Grid Forming），常规 ESS 控制为亚秒级 [p5][p6]。
- 关键数据：大负载跳闸事件 1.5 GW（2024）、1.8 GW（2025）、3 GW（2026）[p2]；各电网要求表（ERCOT/SPP/MISO/ATC/Southern/LIPA/AESO/PG&E）：分钟级 ramp 限值 10–30 MW/min，亚分钟 10–25 MW 在 4–6 s 或 5 s，功率因数多为 ±0.95，PFAPR 多为 90% 1 s（来源 Danovo/Quanta，引用；看图）[p4]；演示：故障期间数据中心在 UPS 供电，电压恢复同时负载恢复 [p7 看图]
- 提到的公司/客户/产品/标准：EPC Power、NERC、ERCOT、PJM、MISO、SPP、CAISO、IEEE 2800、IEEE 519、NVIDIA DSX
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（各电网并网要求对照表）；p7（ride-through 波形）

### P177 Evaluating Heat Rejection System Configurations for AI Data Centers- A Multi-Metric Analysis
- 讲者/机构：Bahareh Eslami、Doug Asay、Raha Kalantarpour（NVIDIA）| 类型：技术分享（仿真/TCO 分析）
- 方向归属（主/次）：主 [底座-冷却]；次 [推理/算力/经济性]
- 核心主张：
  1. 高温冷却（S45，TCS 供液 45°C）扩大自然冷却窗口，机械制冷只做峰值补充，可把电力从冷却转给算力，且零水耗 [p2][p5][p13]。
  2. 三种设计中 Design 2（WCC + 干冷器 + CRAH，专用环路）能效最高、15 年 TCO 最低 [p19]。
- 关键数据（250 MW AI Factory 仿真，5 城市，电价 \$0.12/kWh，3% 通胀，仅含能源费用）[p7][p16]：Design 2 相对 S30→S45 额外算力 Seattle 20.5 MW、Chicago 23.9、Albuquerque 22.6、Dallas 16、Phoenix 5.5（看图）[p13]；Chicago/Phoenix 设施功耗最多降 46%/10% [p13]；Design 2、3 比 Design 1 多 16 MW（37%）、14 MW（33%）算力 [p15]；S45 TCO（每 MW，15 年）：Seattle D1 \$23.6M / D2 \$22.3M / D3 \$22.8M；Phoenix D1 \$24.6M / D2 \$23.0M / D3 \$23.3M；年均 PUE D2 约 1.09–1.11 [p16]；干冷器占地约为风冷冷机的三分之二；Design 1 排热厂区 230K–265K SF vs Design 2/3 100K–115K SF [p16][p19]
- 提到的公司/客户/产品/标准：NVIDIA、S45/S20 供液等级、ACC/WCC/CRAH/CRAC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（Design 2 各城市模式、自然冷却小时、额外算力）；p16（TCO 表）

### P178 Hardware Mitigations for AI-ML Workloads Power Fluctuation
- 讲者/机构：Vijay Boovaragavan（Google，Energy Storage Technical Lead）、Xiong Li（Google，Rack Power Technical Lead）| 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [存储]（储能）
- 核心主张：
  1. 同步的 AI 负载造成 MW 级波动，影响电网（ramp 限值如 20 MW/min）、发电机、母线/变压器与芯片寿命；软件平滑有性能代价，硬件本地储能缓冲无性能损失 [p4][p5]。
  2. 传统电池不适合约每年 100 万次的 ML 循环；需 BBU/CBU 双功能储能模块 + 机架级 EDLC，通过 DC 母线信号去中心化控制 [p9][p10]。
- 关键数据（自报）：传统 IT 机架 10–20 kW，ML 机架达 1 MW 以上 [p2]；LFP 电池 ~3k–10k 循环；电解电容 >5M 循环但只能短时；锂离子超级电容能量密度比 EDLC 高 4–5x [p9]；目标 10 年 100M+ 循环 [p10]；贡献可用时间：未来 2–3 个季度 [p11]
- 提到的公司/客户/产品/标准：Google、BBU/CBU/EDLC/BESS、IEEE 519/1453、OCP Energy 工作组
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（储能技术对比）

### P180 Next-Generation ML Infrastructure- The Open DC Architecture
- 讲者/机构：面板：Ayan Majumdar、Moe Ghamary（Google）、Mike Sabotta/Maureen Tate（NVIDIA）、Paul Artman（AMD）、Mike Edie（Meta）| 类型：面板/标准进展
- 方向归属（主/次）：主 [底座-机架/机械]；次 [底座-电力]、[底座-冷却]
- 核心主张：Google、Meta、NVIDIA、AMD 成立 Open DC 工作组，为 2028 年及以后的 AI 工厂定最小标准集（v0.7，提供反馈，月度会议自 11 月起）[p3][p12]。
- 关键数据：峰值 IT 密度 125 kW/ft → 350 kW/ft（2027 基线 115 kW/ft 液冷；2028+ 335 kW/ft 液冷）；混合 DC 密度 12 → 25 kW/ft；集群基线 12 MW，优选 24 MW [p3][p4]；最大机架重量 8,000 lb（28"W×48"D），ML 机架+sidecar 15,000 lb（56"W×48"D）[p5]；热通道 54"、冷通道 82"、机架高 100"、深 71"、运输通道 12'、层高 ≥18 ft（2 busway）[p6]；最大流速 3 m/s（ASHRAE）；2" 管 365 kW（1 lpm/kW，ΔT 15°C）、4" 管 1459 kW [p7]；NVIDIA 示例 4 行 12.5 MW 块，每行最多 4 MW 冷却，4×5000A busway（800VDC 过渡）[p9]
- 提到的公司/客户/产品/标准：Google、Meta、NVIDIA、AMD、Open DC v0.7、LVDC 工作组
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（2027/2028+ 密度与集群基线）

### P181 OCP Modular Technology Cooling Workstream - 2026 Update
- 讲者/机构：面板：Dariusz Raczkowski（Catalyst Commissioning）、Sara Hitt（Vertiv）、Jerrod Buterbaugh（AMD）、Rajat Bhagat（Arcadis）、Don Mitchell（Victaulic）| 类型：标准进展/面板
- 方向归属（主/次）：主 [底座-冷却]；次 [推理/算力/经济性]
- 核心主张：
  1. 预调试把 7 周压到 1 周（传统 TCS 管路需 6 道冲洗，每道 5–7 天），因为每周延迟成本巨大 [p3][p6 看图]。
  2. 模块化 TCS "Lego"：标准 2"/DN50 drop 与机架连接，管径选型工具，FMEA 与 MTBF/MTBR 可靠性方法 [p12–p18]。
- 关键数据（看图，自报）：每周延迟 \$300–400M 损失（假设 100 MW/600 机架，每机架收入 \$75M）；3 周延迟 \$900M，每日烧 \$42.9M [p3][p4]；机架 ≤230 kW 用 2"/DN50（24" 间距）[p14]；6"/DN150 集管 2.5 MW、8"/DN200 集管 4.3 MW @10 fps；2" 机架连接 172 kW@6 fps、230 kW@8 fps [p15]；>150,000 接头、18 个项目、15 年无泄漏，MTBF >9×10^9 小时（下置信界）[p18]；机架密度路线图：GB300 142 kW、Vera Rubin NVL72 230 kW、Helios(MI455X) 246 kW（数据来自互联网检索，近似）[p11]
- 提到的公司/客户/产品/标准：Victaulic、Vertiv、AMD、NVIDIA、Google、Microsoft、AWS、TCS pipe sizing tool
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（2025–2029 机架功率路线图）；p18（MTBF/MTBR）

### P182 Path to the Megawatt Rack- A Grid-Aware, Symmetric High-Power UPS for AI Data Centers
- 讲者/机构：Tyler Andrews（Echion Technologies，VP Business Dev）、Drew Schaller（Proper Voltage，Technical Solutions Mngr）| 类型：厂商技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [存储]（电池/储能）
- 核心主张：
  1. UPS 电池新增"第二个任务"：对 AI 负载双向缓冲（每分钟多次充放电、多年），按对称功率与循环寿命而非能量定容 [p4]。
  2. 铌酸盐阳极电芯（XNO）可对称 >30C/30C、50,000 循环（5C/5C，10–90% SoC，25°C，Echion 实验室 5.5 Ah 电芯）；800 VDC 母线（±0.5% 静态）需 DC-DC 调节级，电池不能直接挂母线 [p8][p17]。
- 关键数据（自报/仿真，厂商来源）：美国数据中心用电 176 TWh（2023）→325–580 TWh（2028），74–132 GW（LBNL，引用）；同步 GPU 集群使设施功率在毫秒内波动 30–60%，振荡能量主要在 0.2–3 Hz [p3]；280 MW AI 机房示例：计算相 280 MW，通信相 160 MW，电网取电持平 270 MW，缓冲计算相放电 10 MW 40 s，通信相充电 110 MW 4 s，充放电时间比 10:1；无缓冲时 44 s 循环使频率摆动 −60 到 +65 mHz，超出 ERCOT 死区 ±17 mHz [p9]；10 年对比（1,964 次缓冲/天，867 GWh）：ORv3 级 BBU 0.6C 183 MWh/803 柜/4 年更换/\$317 每 MWh；LFP UPS 1C 110 MWh/860 柜/6 年/\$25；VaultX（XNO）6.1C 18 MWh/225 柜/10 年/\$10（仅电芯，未折现）[p10][p16]；柜体 1.6 MW 峰值/1 MW 持续，80 kWh，480 与 800 VDC，UL 9540/9540A/1973、UN 38.3，原型在建 [p13]；ERCOT 约 2,600 MW 瞬时失负荷可使频率升至约 60.4 Hz [p19]
- 提到的公司/客户/产品/标准：Echion XNO、Proper Voltage、VaultX、OCP LVDC white paper v1.0、Mt. Diablo/Diablo 400 spec、ORv3 BBU、ERCOT、RTE、Energinet、EirGrid、NERC
- 首次/记录/SOTA 声明：自称 XNO 对称功率 >30C/30C、50,000 循环（厂商自报）[p8]
- 推荐配图页：p9（280 MW 机房有/无缓冲对比）；p10（三种方案 10 年成本）；p18（四种配电架构演进）

### P184 Technoeconomic comparison of DC-and AC-coupled solar microgrids, natural gas, and grid
- 讲者/机构：Alex C. Newkirk（Carnegie Mellon University；合著含 Gerber、Fuchs、Samaras 等）| 类型：学术技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [推理/算力/经济性]
- 核心主张：
  1. 并网排队与燃机/变压器供应瓶颈下，考虑"带芯片时间价值"后，部署速度比直接电价更重要；全 DC（±400V OCP）光储微电网比 AC 等价系统总成本低 18%（平均）[p11][p13]。
  2. 纯成本口径：DC 数据大厅本身约占一半节省；与电网供电的 AC 等价比较，全 DC 总能源成本低 7.9% [p10][p15]。
- 关键数据（仿真，New Mexico 站点，30 MW IT，99.0% uptime，气价 \$4.58/MMBtu）：AC 光储（254 MW PV/193 MW B）建设 2 年，LCOE \$0.259/kWh，计芯片机会成本 \$0.690；DC 光储（241 MW PV/168 MW B）2 年，\$0.212→\$0.642；天然气 70 MW 4 年，\$0.181→\$1.13；电网 4 年，\$0.054→\$1.01 [p13]；电池 13 年更换时平均保留 89% 容量，约 9% 衰减 [p9][p13]；Colorado 气价 \$7.7/MMBtu 时，燃机 LCOE 在 <约 20–30 MW 超过 DC 光储（\$0.204）[p7 看图]
- 提到的公司/客户/产品/标准：OCP ±400V DC、LBNL、NREL ATB 2024、GPU spot 租赁指数
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（四种架构 LCOE 对比）；p11（美国地图最低成本技术）

### P187 The Future of Fuel Cells in Datacenters - High Temperature Fuel Cells
- 讲者/机构：Afshin Majd（Microsoft）、Priya Chhiba（Google）、Alberto Ravagni（Net Zero Innovation Hub）| 类型：面板/倡议提案（Sustainability）
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. 高温燃料电池（SOFC 为主）已有 GW 级装机，对数据中心仍是新技术；无燃烧、DC 原生，与 800V 架构集成方便，阳极排气 CO2 浓度高便于碳捕集 [p4][p8][p13]。
  2. 提议在 OCP Energy 子项目下启动 HT-FC 倡议：制定集成规范与接口，通过 Net Zero Innovation Hub 做试点验证 [p14][p16]。
- 关键数据：全球 SOFC 已部署 1.5–2 GW，MCFC 0.35–0.50 GW；Oracle Project Jupiter（New Mexico）计划 2.45 GW SOFC 微电网，NOx 较原燃机设计降 92%；AEP 20 年 offtake 1 GW、\$2.65B（2026-01）；Equinix 100+ MW、19+ 数据中心 [p4]（均为引用/公开消息）；SOFC 约占全球固定式燃料电池装机 60–66% [p5]；效率：小型航改燃机 35–42%，大型联合循环最高 64%，SOFC 53–65%（LHV，净交流，生命周期平均约 54%）、热电联供 >90% [p10]；噪声 65 dB @10 ft [p8]；功率密度 SOFC 25–100 MW/acre，燃机/往复机约 50 MW/acre [p11]；效率衰减 0.2–2.0%/1000 h，5–10 年需翻新电堆 [p9]；电堆热插拔间隔 45,000 h（厂商自报）[p22]；SOFC 成本自 2010 年降 50–65% [p12]；阳极排气 CO2 30–80%，燃气发电 4–14%，DAC 约 420 ppm [p13]
- 提到的公司/客户/产品/标准：Microsoft、Google、Oracle、AEP、Equinix、Bloom Energy、NVIDIA 800VDC、OCP LVDC white paper v1.0
- 首次/记录/SOTA 声明：称 AEP 协议为"首个大规模受监管公用事业对燃料电池的押注"（讲者表述）[p4]
- 推荐配图页：p4（三个 SOFC 落地案例）；p10（效率对比表）

### P189 2-Wire-vs.-3-Wire-at-800VDC-Grounding-Fault-Behavior-and-Protection-for-AI-Data-Centers
- 讲者/机构：Guang Yang、Lizhi Wang（Siemens）| 类型：技术分享（仿真研究）
- 方向归属（主/次）：主 [底座-电力]；次 [安全]
- 核心主张：
  1. 2-wire（800V P-N）系统复杂度低、功率密度高，但故障能量高、负载灵活性低；3-wire（±400V）反之，需平衡部件 [p4]。
  2. DC 下"半隔离不是隔离"：只断一极会使电压重分布或机架仍带电；DC 里栓锁短路不是最坏故障，需考虑电容放电与真实故障；SSCB 比保险丝/MCCB 能大幅减少本地储能需求并不受电缆长度影响 [p7][p9][p11]。
- 关键数据（仿真/实验，自报）：4.6 MW SST 源接 1 MW 800 VDC 机架，35 kV AC [p3]；寄生电容人体放电暴露：0.01 µF 时 0.3 ms，5 µF 时 151 ms；<0.5 µF 符合 UL 1400-1，≥1 µF 超阈值 [p6]；保险丝方案需 300 mF（373V），SSCB 方案仅 10 mF（~400V）[p9]；65 kA 下断路器把电流限制到 4.8 kA；1.1 kA 时峰值约 1.5 kA（依赖过零）[p11]
- 提到的公司/客户/产品/标准：Siemens、OCP Diablo 400（±400VDC）、OCP SST specs（800VDC）、IEC 60479-2、UL 1400-1、NEC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（2-wire 与 3-wire 权衡对照）；p9（保险丝与 SSCB 对比）

### P190 400V-800V-On-Board-Power-Delivery-Requirements
- 讲者/机构：Lu Jian、Sachin Madhusoodhanan、Michelle Badal（Google）、James Sun（Microsoft）、Shengwen Xu（Meta）| 类型：标准进展
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：Google、Meta、Microsoft 在 2026 Q4 启动 OCP 工作组，制定 ±400V/800V 板载电源模块规格与资质标准，目标 2H 2027 发布；沿用 2024 的 48V 设计与资质检查清单经验 [p3][p12]。
- 关键数据：DC-DC 模块：Vout 50V（固定比）或 12V（固定比/稳压）；TDP 12 kW（全砖）/6 kW（半砖）/3 kW（四分之一砖）；Vin ±400V/800V ±10%；高度 14 mm；效率目标 >98.5% 峰值，25–100% 负载 >98%（50V），12V 为 >96.5% 峰值；瞬态 >150% TDP 持续 50 ms；800V 加强绝缘 [p10]；模块化比分立功率密度最高可达 2x [p8]
- 提到的公司/客户/产品/标准：Google、Microsoft、Meta、IEC/EN/UL 62368-1、DOSA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（模块关键规格表）；p5（板载电源生态时间线）

### P191 800VDC-Power-Systems-Redefining-Protection-Coordination-System-Safety
- 讲者/机构：Manav Patel、Tony Landry（Schneider Electric）| 类型：厂商技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [安全]
- 核心主张：
  1. 800 VDC 保护的问题从"哪个器件最快"变为"整个系统响应是否可预测"，需 co-design 与系统级验证 [p5][p6]。
  2. 故障电流波形取决于源（非限流源呈电感型指数上升，限流源呈电容放电+馈入两段），但保险丝与 EMCB 目前仅按非限流型认证 [p10]；接地方案先于保护选型决定首次故障行为 [p14]。
- 关键数据（自报）：分支保护器分断时间：保险丝 0.5–5 ms、EMCB 1–20 ms、混合 HCB 0.2–1 ms、SSCB <10 µs；800 V 以上分支保护存在标准缺口；开关柜与 busway 目前限 1000 Vdc [p11][p17]；SSCB 可用性取决于接地：固态接地单极 2 线可用（保护 1 极），其他需保护两极 [p15]
- 提到的公司/客户/产品/标准：Schneider Electric、EMCB/ETU/HCB/SSCB、DC UPS、SST、UL
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（四类保护器件对比）

### P193 DC-Arc-Flash-Learnings-from-Practical-Study-and-Test-Results
- 讲者/机构：Tony Landry、Stuart Sheehan（Schneider Electric）| 类型：技术分享（仿真+实验）
- 方向归属（主/次）：主 [安全]；次 [底座-电力]
- 核心主张：现有 DC 电弧闪光方法（NFPA 70E 表、IEEE 1584、UL RP 2986）建立在 AC 或 PV/电池源假设上，不覆盖有源变换器塑形的 800 Vdc 故障电流；需发布变换器等效输出阻抗与异常行为、测试保护、推进 DC 分析标准（IEEE P3002.12、P3002.14）[p4][p5][p16][p17]。
- 关键数据（实验，Schneider 实验室 2026-09）：39 次电弧测试：<0.1 cal/cm² 21 次（54%）、<0.2 7 次（18%）、<1.2 6 次（15%）、<4 3 次（8%）、>4 2 次（5%），80% 测试电弧未持续；11 次相似配置对比：7 次 <0.1、2 次约 2 cal/cm²（电弧在母排间持续）、2 次 >4（母排与外壳间"两个电弧"）；测试无过流保护，持续时间约 130 ms；250 A MCCB 清除时间 0.6 ms，IE=0.03 cal/cm² [p12][p13][p14]
- 提到的公司/客户/产品/标准：Schneider Electric、Etap、Fire Protection Research Foundation、IEEE IAS ESW
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（39 次测试入射能量分布）

### P194 Defining-End-to-End-800VDC-System-Performance-Requirements
- 讲者/机构：Jared Huntington、Mike Tu（NVIDIA）| 类型：技术分享/标准提案
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：为实现互操作需锁定储能位置、机架输入电气接口、可支持的分配阻抗、启动协商、接地与保护；用小信号/大信号建模保证稳定性，模型应与规格一起开放 [p3][p12][p17]。
- 关键数据（看图，NVIDIA 自报）：GPU 动态负载 EDPP 180% 持续 400 µs，150% 持续 50 ms [p4]；DC/DC power shelf（4M3）峰值/稳态/空闲 92.6/71.3/20.0 kW，非冗余 123.5/95.0/26.6 kW，转换器额定 95 kW，每 whip 输入 slew 0.6 A/µs，输入电容 26 µF/kW [p7]；分配要求：等效输入电容 26 µF/kW，最小 12 µF/kW（@62.4 µH），最大分配电感 250 µH/whip、5 µH/1 MW block，AC busway 拐点频率 500 Hz [p10 看图]；EDPP 储能项使 busway 与断路器电流需求增加 11% [p5 看图]；机架启动：800 VDC ±5%，液体入口 <45°C、出口 <85°C，walk-in 10 s、至少 1024 步 [p13 看图]；固态接地限制 busway 约 26 m（机架到源 7 mΩ）[p16 看图]
- 提到的公司/客户/产品/标准：NVIDIA、SST、DC/DC power shelf、IEC 61000-4-5、SSCB、IMD、RCM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（储能位置与各需求的能量/功率表）；p10（分配电容与长度关系）；p13（启动序列）

### P195 Designing-Safe-800-VDC-Systems-Protection-Fault-Management-and-Operations
- 讲者/机构：Xianyong Feng（Microsoft）、Mike Tu、Sai Somayajula（NVIDIA）| 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [安全]
- 核心主张：800 VDC 是变换器主导、低阻抗系统，保护需"检测→定位→隔离→稳定"，用 IMD（源/主母线）+ RCM（分支/机架）两区检测，并把 SSCB（µs）与保险丝/MCCB（ms）作为一个系统整体协调，避免快速上游器件先跳导致健康负载掉电 [p3][p4][p6][p9]。
- 关键数据（自报）：分断时间：MCCB 数十 ms；SSCB ≈10 µs；混合 CB ~ms；保险丝 100s µs–ms；E-fuse <2–10 µs；Pyro-fuse <2 ms [p8]；三种机架供电配置功率区：数十 kW / 数百 kW / 数 MW [p10]；高阻抗故障与串联电弧可能低于保护阈值，需叠加温度等传感 [p10][p11]
- 提到的公司/客户/产品/标准：Microsoft、NVIDIA、Diablo400、SSCB、IMD、RCM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（六类 DC 分断器件对比表）；p9（两个协调失配案例）

### P197 Grid-Interconnection-Requirements-for-Large-Loads-and-Path-to-Next-Generation-Data-Center-Power-Architectures
- 讲者/机构：Sai Somayajula、Mike Tu（NVIDIA）、Joshua Piruzza（Danovo Energy Solutions）、Eric Mannarino（Equinix）| 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [运维/可靠性/遥测]
- 核心主张：
  1. 并网性能要求必须在通电前用仿真证明，"负载模型就是交付物"；需要经测试验证（而非数据手册推断）的 PSS®E + EMT 模型 [p9][p12]。
  2. NVIDIA 视角：用机架级平滑（IPS/MaxLPS）、站级 EMS + BESS 与 POI 遥测，让 AI 工厂在 POI 呈现有界、可建模、可验证的行为 [p13][p16][p17]。
- 关键数据：数据中心客户自发减载事件：2024-07 1,500 MW；2025-02 1,800 MW 与 428 MW；2025-03 227 MW；2025-05 540 MW；2025-06 1,300 MW；2026-07-22 Dominion 约 3,800 MW（输电故障后）；Texas 2023–2025 共 27 次失负荷 100–450 MW [p3]；FERC 2026-07-16 要求 NERC 于 2026-12-31 前提交计算负载可靠性标准 [p6]；ERCOT 仅大负载并网申请 400+ GW [p9]；ERCOT/TAMU 参考案例：10 s 仿真，平均化 EMT 模型（50 µs 步长）约 16 s，对比开关模型（1 µs）约 28 分钟 [p11]（均为引用/公开信息）
- 提到的公司/客户/产品/标准：NERC LLWG、FERC、ERCOT、PSS®E、PSCAD、DSX（OS、MaxLPS、Flex、Exchange）、OCP "Interface Specification Between Hyperscalers and Utility Grid for Disturbance Performance"
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（历次数据中心自发减载事件清单）；p14（Pre-GB200 到 Vera Rubin 的快速动态控制演进）

### P198 Grid-Requirements-and-Mitigation-options-for-Large-Scale-AI-ML-Loads
- 讲者/机构：Ashish Upreti、Mike Della Penna（Google）| 类型：标准进展
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. 2024-07 北弗吉尼亚事件（雷击与保护动作引发 6 次电压跌落、约 1,500 MW 电压敏感负载意外丢失）促使电网收紧并网要求；需求分为故障穿越/PFAPR 与 ramp/波动/强迫振荡两类 [p2][p4]。
  2. 缓解选项：电源固件更新（利用电容储能）、储能、MV-UPS、电网侧 SVC/E-STATCOM；建议设生效日期、既有设施豁免、新增容量才适用 [p7][p8]。
- 关键数据（自报/引用）：PFAPR 恢复时间：FinGrid 1 s 内 90%；ERCOT 2 s 内 90%；AESO 1.0–10.0 s 内 100%（可配置）；Energinet 5 s 内 80%、30 s 内 90% [p5]；拟定 VRT：0.80≤V<0.90 穿越 2 s，0.50≤V<0.80 穿越 0.5 s，0.35≤V<0.50 0.25 s，V<0.35 0.15 s，电压恢复后 2 s 内恢复到故障前 90% [p6]；ramp 限值示例：不超过 10–25 MW/每 5–10 s [p4]；文档计划：2026-10 发布 VRT & PFAPR v1.0，2027-Q1 发布 Power Ramp & Fluctuations v1.0 [p9]
- 提到的公司/客户/产品/标准：Google、ITIC(CBEMA) 曲线、SVC、E-STATCOM、OCP Interface Specification
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（VRT 与 PFAPR 拟定特性表）

### P199 Integrating-Solid-State-Transformer-to-Data-Center-LVDC-Ecosystem
- 讲者/机构：Satarupa Bal、Ashish Upreti（Google）、Mike Tu（NVIDIA）| 类型：标准进展
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：集中式 SST + ESS + DC 分配 + DC 保护，把转换放到数据大厅外、把机架内数百个电池合并为行级备份；发布 SST Specification Rev 0.3 征求意见并共建测试用例库 [p4][p7][p10]。
- 关键数据（规范草案 Rev 0.3）：800 Vdc 单极输出；电压容差 ±0.5%（开关纹波）/±1% 静态/±3% 动态（待定）；过载 120% 5 s，下游保护 150% 约 150 ms；效率 ≥98%（50–100% 负载）；ramp 20–50 MW/min；DC 侧不接地或 HRG；外形 10–20 ft L × 8 ft D × 8.5 ft H [p7]；SKU A：13.8 kVac ±10%，5 MW，故障电流 18–40 kA；SKU B：34.5 kVac ±10%，5/10 MW，20–50 kA [p8]
- 提到的公司/客户/产品/标准：Google、NVIDIA、SST Spec Rev 0.3、ERCOT LVRT 要求
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（SST 规格对齐表）

### P200 LVDC-Architecture-Fundamentals-How-Topology-Protection-and-Standardization-Define-DC-Power-Systems
- 讲者/机构：Brian Deckard（Siemens）、Giel Van den Broeck（Direct Energy Partners）| 类型：标准进展（白皮书 v1.1，2026-09）
- 方向归属（主/次）：主 [底座-电力]；次 [安全]
- 核心主张：用 Current/OS 的 DC Zone（0–4）、ODCA 的 Sector、IEC 60364-8-82 的 Circuit（C1/C2/C3）三种互补方法设计 LVDC 的选择性与低故障能量，数据中心无需重新发明 DC 设计 [p4][p10][p11][p20]。
- 关键数据：Zone 3/4 预期故障入射能量 <1.2 cal/cm² [p4]；DCIDE 仿真：同一 800 V busway 极间短路峰值均 129 kA，fault-limiting 变换器 16 ms 回零，fault-feeding 变换器持续 22 kA（仿真，看图；示例值随技术而异）[p14]；AC 现状 4 个转换级（托盘前 3 级）[p12 看图]；参与者累计 210+ 专家，直流项目自 2016 年 [p3]
- 提到的公司/客户/产品/标准：Siemens、Direct Energy Partners、Current/OS、Open DC Alliance (ODCA)、IEC 60364-8-82、IEC 60947、UL 489I、DCIDE
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（fault-limiting 与 fault-feeding 短路电流对比）

### P201 LVDC-Building-an-Open-and-Evolving-Ecosystem
- 讲者/机构：Jason Adrian（Google）、Jared Huntington（NVIDIA）| 类型：主题演讲/标准进展
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. 机架功率 ≥100 kW 时机架内转换与备份占 35%+ 空间；超过 600 kW 机架内 AC/DC 转换不可行，故走向原生 LVDC [p4]。
  2. 其余 IT 设备用 48–54 VDC busbar（<100 kW）、800V→54V DC/DC power shelf、直流电机 CDU/风扇；Google、Meta、Microsoft、NVIDIA 将在 OCP 新设工作流标准化机架接口连接器、DC whip、tapbox、DC:DC power shelf 与转换模块 [p7][p8][p12]。
- 关键数据（自报）：AC:DC 转换占机架容量 10–15%，N+N 使转换翻倍，机架内 BBU 再占 10–15% [p4]；xPU 占数据中心电力 80%+ [p3]；DC:DC power shelf 密度 55 kW → 95 kW 每 RU（2x）[p7]；路线：2026 单列验证，2027–2028 数据中心级验证，2029+ GW 级 LVDC 原生规模部署 [p11]
- 提到的公司/客户/产品/标准：Google、NVIDIA、Meta、Microsoft、LVDC、SST、busway/tapbox
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（LVDC 从 R&D 到规模化四阶段）

### P202 Reliability-Availability-and-Maintainability-of-High-Temperature-Superconducting-Power-Distribution-for-High-Density-AI-Data-Centers
- 讲者/机构：Bender Kutub（VEIR）、Lee Prescott（RED Engineering Design）| 类型：厂商技术分享（RAM 研究）
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：HTS（高温超导）配电的可用性由系统架构而非单个部件决定；在合适的系统架构下 VEIR HTS 方案可达五个 9 的可用性，需有可并行维护的液氮（LIN）系统并配合其电源 [p13][p14]。
- 关键数据（模型分析，自报）：声称 HTS 相对铜约 10x 功率密度、近零损耗 [p2]；块冗余结果：LIN 系统 5 个 9（99.999%），AC 3 个 9（Tier III，99.9%），DC 4 个 9（Tier IV，99.99%，假设 AC 等效 DC 设备）[p11]；分布式冗余：LIN+AC 达设施 5 个 9，LIN+DC 达设施 4 个 9，CapEx 与隐含碳更高 [p12]；算例：AC 21 MW IT，7+1 块冗余；DC 20 MW，2+1 块冗余；DC 分布式 60 MW，8 根 DC HTS 缆 4-to-make-3，运行于 75% 容量（故障时升到 100%）[p9][p10]；数据来源 IEEE 493-2007、OEM 数据、RED 内部统计 [p4]
- 提到的公司/客户/产品/标准：VEIR、RED Engineering、液氮冷却、IEEE 493、OCP HTS 白皮书工作流
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（块冗余下 AC/DC 可用性结果）

### P203 Rethinking-Power-Safety-The-Inherent-Benefits-of-800V-Low-Voltage-DC-Architectures
- 讲者/机构：Susmita Panda、Satarupa Bal（Google）| 类型：技术分享
- 方向归属（主/次）：主 [安全]；次 [底座-电力]
- 核心主张：DC 电弧闪光入射能量取决于预期故障电流与清除时间；限流型变换器（buck 型）可把故障电流压到零，馈流型（boost 型）会维持故障电流；机架级反向阻断二极管（单向机架）必须有；现有 IEEE 1584/NFPA 70E 不覆盖变换器供电的 DC 系统，且会高估电容主导系统的能量 [p3][p4][p6][p9]。
- 关键数据（仿真，自报）：变换器输出电容贡献初始 80–90 kA 峰值 [p4]；无二极管时峰值电流高 220% [p6]；机架级清除时间与入射能量：保险丝 16 kA/3.3 ms/0.202 cal/cm²，MCCB 15 kA/13 ms/0.437 cal/cm²，SSCB 6.2 kA/0.2 ms/0.128 cal/cm²（均带二极管）；无二极管时 MCCB 的入射能量 >1.2 cal/cm² [p8]
- 提到的公司/客户/产品/标准：Google、DCF Power Distribution LVDC White Paper v1.1、IEEE 1584、NFPA 70E
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（三种保护器件清除时间与入射能量对比）

### P204 Short-Circuit-Bolted-Fault-Analysis-of-LVDC-Power-Distribution-Systems-for-Datacenter-Uses
- 讲者/机构：Dirk Mueller、Sarkis Juana（UL Solutions）| 类型：技术分享（仿真研究）
- 方向归属（主/次）：主 [安全]；次 [底座-电力]
- 核心主张：800 VDC 栓锁故障的严重度由储能与回路阻抗决定；大储能支路（超级电容）可主导总故障能量、电流上升率和持续时间；低阻尼会引发反向电流、振荡和二次峰值，快速上升和高峰值可能超过保护器件的分断能力 [p11]。
- 关键数据（仿真）：800 VDC 极间（单参考节点，非 ±400V）；母线等效电容 2/5/10 mF；导线 8.4–240 mm²，长 0.25–10 m [p4]；Model 1（5 mF，20°C）：峰值电流 0.25 m 时 63.3–75.5 kA，10 m 时 10.3–22.8 kA；导体越粗峰值越高 [p7 看图][p6]；Model 2 加超级电容 1/78/3,136/23,521 mF：峰值电流 8–70 kA，I²t 1.3–689.5 kA²s，di/dt 0.03–0.15 kA/µs [p10]
- 提到的公司/客户/产品/标准：UL Solutions、OCP 800 VDC、UL/IEC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（Model 1 四种导体的峰值电流表）
