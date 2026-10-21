---
title: "R05_ai-clusters"
tags:
  - OCP2026
  - 讲稿笔记
---

# R05 笔记：ai-clusters（AI 网络/互连，含 1 份 AI Open Data Center 标签讲稿 P126）

### P117 04_Bring Your Own XPU An Open Rack for Inference Performance and TCO
- 讲者/机构：Chris Petersen，VP CTO Office，Astera Labs | 类型：厂商展区/技术分享
- 方向归属（主/次）：主 [Up 机柜/超节点]；次 [推理/算力/经济性]、[运维/可靠性/遥测]
- 核心主张：
  1. 推理成为主要负载，需要一个可对接任意 XPU 的通用 scale-up 机柜，以复用基础设施、降低 TCO。
  2. 交换机的 radix（规模）与"智能"（Hypercast 多播 + In-Network Compute）直接决定推理 tokens/s；MoE 需要大量动态多播组，传统交换机组数不够，集合通信退化为单播。
  3. 规模化部署时稀有故障不再稀有，需要信号/链路/fabric 多层 RAS 与开放标准管理（COSMOS，基于 OCP/OpenBMC/DMTF）。
- 关键数据：
  - 推理支出预计 2026 年首次超过训练；2030 年推理基础设施支出超训练 >50% [p2]（引用 McKinsey）；图中 2025 训练/推理约 23/21，2030 约 62/93（单位未标注）[p2]（看图）
  - Scorpio X-Series 为 320 lane smart fabric switch，自称"最大的开放 memory-semantic 交换机" [p7]（自报）
  - 多级交换 fabric 可扩展到最多 160 GPU 的 scale-up [p9]（自报）
  - Qwen3.5-122B 均衡 prefill/decode 推理：1×Scorpio 2 320L（8 GPU 全带宽 P2P）对比 2×小交换机（各 4 GPU P2P），输出 tokens/s +50%，prefill 重负载 +90% [p13]（自报）；512 并发请求时约 1,780 vs 1,170 tokens/s [p13]（看图）
  - Hypercast + INC 可将集合操作加速最多 2x [p13]（自报）
  - "99% 的链路正常，剩下 1% 占用 99% 的部署时间" [p14]（讲者观点）
- 提到的公司/客户/产品/标准：Astera Labs Scorpio X-Series、Leo（Smart Memory Controller，KV cache offload）、Orion-CT（PCIe GPU 计算托盘）、Orion-FT（fabric 托盘）、Orion Rack、Hypercast、INC、COSMOS；OCP OAC、DC-SCM、OpenBMC、DMTF；McKinsey；Qwen3.5-122B
- 首次/记录/SOTA 声明："Largest open, memory-semantic switch" [p7, p17]
- 推荐配图页：p13（单大交换机 vs 双小交换机拓扑 + tokens/s 曲线 + Hypercast/INC）；p2（训练 vs 推理支出柱状图）

### P119 06_Current Activities in the Open Cluster Designs for AI Strategic Initia
- 讲者/机构：Loren Staley，Principal Architect，Celestica；Lowell D. Lamb，Distinguished Engineer，Broadcom | 类型：标准进展（OCP Strategic Initiative 状态汇报）
- 方向归属（主/次）：主 [Out 后端网络]；次 [底座-机架/机械]、[推理/算力/经济性]
- 核心主张：
  1. Open Cluster Designs for AI SI 产出可直接用于设计、实施和采购的 AI 集群参考架构（XOC-N 集群、OPG-M pod group），含物料、功耗、空间、重量清单。
  2. 从 400G 风冷到 800G/1.6T 液冷 scale-out 是"非常大的转变"，需要重新评估集群网络架构；网络结构变得更简单、更快，但前端网络作用更复杂。
  3. 推理（KV cache、prefill/decode 分离）是驱动架构演进的新需求，不同负载的 prefill/decode 实例比差异很大。
- 关键数据：
  - 术语：XOC-N = xPU Open Cluster for N xPUs；OPG-M = Open Pod Group for M xPUs [p3]
  - 400G 风冷 OPG-128 于 2026 年 1 月发布；800G/1.6T 液冷 OPG-576 于 2026 年 2 月启动开发（图示仅供参考）[p6–p7]（自报）；设计迭代周期约 2 年 [p8]
  - 设计目标为强扩展：资源 2X/4X → 运行快约 2X/4X [p9]
  - Head-end 物料示例：ORv3 机柜 9、5.8 kW PSU 36、xPU 节点 16、数据存储服务器 5、元数据服务器 2、51T scale-out leaf（64×OSFP）4、26T scale-out CPU leaf 1、51T 存储 leaf 1、800G 单模 OSFP（2×400G）84、MTP-8/12 单模跳线 168、OSFP⇔2×400G QSFP112 DAC 76 [p10]（自报）
  - Head-end 机柜（Rack #5）估算：24 OU、570 kg、最大功率 22.6 kW、降额功率 18.1 kW（原文单位写作 "W"，按数值应为 kW，存疑）[p10]
  - 新架构：scale-out 每 xPU 800G 或 1.6T；前端每 tray 2×400 Gb/s，折合每 xPU 约 100 Gb/s [p15]
  - KV cache 约每 token 10k 个 KV 对 [p23]（自报）；文档摘要示例约 310k tokens [p16]
  - Prefill:decode 实例比：通用聊天/QA ~1:2–1:4；推理模型与 agent 链 ~1:3–1:10；高前缀缓存命中 ~1:4–1:8；代码生成/长文写作 ~1:3–1:6；文档摘要/大量摄入 ~2:1–4:1 [p25]（自报）
  - 已发布贡献：Broadcom/Celestica/System-Stack 的白皮书与 XOC-N/OPG-M 设计（训练、400G、风冷，2026-01）；Hedgehog & Celestica 开源集群管理（基于 Kubernetes 与 SONiC，2026-04）[p11–p12]
- 提到的公司/客户/产品/标准：Celestica、Broadcom、System-Stack、Hedgehog；ORv3、OSFP、QSFP112、SONiC、Kubernetes；OCP Open Systems for AI、Open Data Centers for AI 等工作组
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（400G 风冷 → 800G/1.6T 液冷机柜排对比）；p10（物料与功耗/空间/重量表）；p25（prefill/decode 比例）

### P120 07_From Benchmark to Bottleneck Agentic AI for Datacenter Workload Analys
- 讲者/机构：Meha Virapandiane、Ho-Sup Chung（Intel）；合著 Subramaniam Meenakshisundaram、Sushma Kadoor（Intel）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [推理/算力/经济性]（CPU 负载性能分析）
- 核心主张：
  1. 多 agent 流程（DCPerf Agent 负责执行，Perf Analyzer 负责分析）可让负载部署、执行、遥测关联与瓶颈定位可重复、可审查。
  2. Agent 的价值在于根据执行证据恢复（而非简单重试）、随行为变化继续调查，并在调优无效时交回一个假设而不是结论。
  3. 呼吁在 OCP 内标准化"负载配置 + 遥测 + 诊断推理"的可移植证据包。
- 关键数据：
  - 测试 DCPerf v2.0-rc2（预发布）中的 TaoBench、FeedSim、DjangoBench、SparkBench、MediaWiki [p7, p20]
  - FeedSim 上 agent 并行跑了 5 组调优研究（线程数、NUMA taskset、C-state、jemalloc 等），均未超过基线；遥测指向内存带宽为主要假设 [p14]（实验，定性）
  - 讲稿明确声明不披露任何性能结果或系统对比 [p20]
- 提到的公司/客户/产品/标准：Intel；Meta DCPerf（MIT 许可）、Benchpress
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（agent 工作流与 DCPerf Agent/Perf Analyzer 分工）；p10（四个负载的发现汇总表）

### P121 08_Model-Based Testing for Open-Source Software Components Public Modelin
- 讲者/机构：Mengqi Liu（Alibaba）、Ali Kheradmand（Google）| 类型：技术分享/标准进展（SONiC 社区）
- 方向归属（主/次）：主 [Out 后端网络：SONiC]；次 [运维/可靠性/遥测]
- 核心主张：
  1. AI fabric 运行在 SONiC、FRR、SWSS-SAI 等开源代码上，链路抖动恢复错误可让数千 GPU 停滞；手写测试和 LLM 都不能保证覆盖完整。
  2. 维护"可执行规格"模型（Python 子集），用符号执行自动生成带覆盖保证的测试；再用 P 语言交互模型枚举 API 调用顺序，查组合/收敛类 bug。
  3. LLM 用于审查模型和快速证明不可行 trace，但正确性仍由模型和生成的测试裁定。
- 关键数据：
  - frr/zebra 中 SRv6：6 个 API 模型、约 1,000 行模型代码、90%+ 代码覆盖率、发现 10+ 个生产软件真实 bug [p3]（自报）
  - bgpd nexthop tracking 生成 468 个用例 [p4, p6]
  - 2,000+ 自动生成测试检查 FRR 的 BGP UPDATE 错误处理是否符合 RFC 7606，发现若干"有理由的差异" [p4]
  - SwitchV（SIGCOMM'22，用 P4 形式化 SAI 语义）已发现 300+ 个独立 bug [p7]（引用）
  - 交互级 bug 示例：SRv6 policy_set 与 BGP announce 顺序颠倒时，活跃 NHG 停留在 [sid0, sid1] 而非 [sid2]，转发静默失效（收敛性 bug）[p10–p11]
- 提到的公司/客户/产品/标准：Alibaba、Google；SONiC、FRR（bgpd、zebra）、SWSS-SAI、SRv6、RFC 7606、CrossHair、P language、P4、SwitchV；开源仓库 sonic-net/sonic-formal-infra（Apache-2.0）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（模型驱动测试流水线）；p11（顺序颠倒导致的 SRv6 收敛 bug）

### P122 A Comparative Analysis of Next-Generation Networking Standards for Large-Scale DC Deployments
- 讲者/机构：Mohammad Hanif，Senior Director；Kamran Naqvi，Chief Network Architect-EMEA（Broadcom CSG）| 类型：技术分享（标准对比）
- 方向归属（主/次）：主 [Out 后端网络：UEC/MRC/RoCE、拥塞控制、负载均衡]；次 [Across：SRv6]
- 核心主张：
  1. RoCEv2 的单路径、按序、无损假设在 AI 规模下失效（热点、PFC 风暴、队头阻塞），一个流停滞会拖住整个集合通信。
  2. MRC 走"演进已部署的东西"，UEC 走"重新设计整个协议栈"；两者在包喷洒（packet spraying）、发送端拥塞控制、包裁剪（trimming）上趋同。
  3. MRC 的窄范围是有意为之：只针对 AI 训练、现有硬件可用、已在生产；UEC 范围更广，是更长期的基础，但生态成熟度较晚。
- 关键数据：
  - MRC 由 OpenAI 联合 AMD、Broadcom、Intel、Microsoft、NVIDIA 开发，经 OCP 发布；已在 OpenAI、Microsoft、OCI 生产部署 [p4, p15]（自报）
  - UEC 规范 v1.0 于 2025 年发布；当前 v1.0.3 [p4, p15]
  - MRC 每 QP 熵值（EV）集合通常 128–256 项，分布在 UDP 源端口和 IPv6 flow label 上 [p8]
  - MRC 故障/拥塞时在微秒级重路由 [p8]（自报）
  - MRC 仅支持 Write 与 Write-with-Immediate；UEC 支持 Read、Write、Send、Atomics [p7, p15]
  - MRC 1.0 只有发送端拥塞控制；UEC 同时有发送端与接收端（credit）拥塞控制，并含 LLR、CBFC、CSIG [p10, p13, p15]
- 提到的公司/客户/产品/标准：OpenAI、Microsoft、OCI、AMD、Broadcom、Intel、NVIDIA；MRC、UEC/UET、RoCEv2、SRv6、libfabric 2.0、libibverbs、IPSec/PSP、CSIG、LLR、CBFC、SAI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p15（MRC vs UEC 逐项对比表）；p9（MRC 应用 API mrc.h 与控制器 API mrc_ctl.h 结构图）

### P125 Achieving AI Cluster Reliability at Scale- Lessons in Reducing Workload Interruptions
- 讲者/机构：Ramachandra Reddy Kallam，Production Systems Engineer；Bob Wang，Hardware Systems Engineer NPI AI（Meta）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [Out 后端网络]、[Up 机柜/超节点]
- 核心主张：
  1. 同步训练中单节点故障即可中断整个作业；即使有自动恢复，每次中断的代价也不为零，必须逐次计数、归因、修复。
  2. 恢复不等于归因：用 AI 辅助的分诊与归因（先调查再贴标签、区分源头与"连带受害者"、输出证据包而非结论、对照策划的故障目录）。
  3. 跨平台和供应商使用统一故障分类，便于优先级排序和下一代平台继承。
- 关键数据：
  - 大型训练作业可跨 100k+ GPU [p2]
  - 中断来源（Platform-A / Platform-B）：scale-out 网络（交换机、NIC、光模块）23.6% / 11.7%；scale-up fabric 24.2% / 9.2%；内存（HBM、LPDDR、SRAM）7.4% / 22.5%；GPU 器件与固件 2.4% / 1.4%；软件调度工具 12.5% / 13.4%；主机/CPU/OS 10.8% / 11.8%；预运行检查 8.6% / 15.5%；电力与冷却 3.8% / 7.5%；应用与非法内存访问 5.0% / 5.5%；其他 1.7% / 1.4% [p8]（现网）
  - Platform-A 网络 + scale-up fabric 合计占中断 48%；Platform-B 内存占 23% [p8]（现网）
  - Platform-B 的 HBM 不可纠正错误是 Platform-A 的 4.8 倍，系统内存 ECC 4.2 倍 [p8]（现网）
  - 软件、工具或预运行检查导致的中断：Platform-A 26%，Platform-B 34% [p8]（现网）
  - 2026 年 1–9 月周中断率相对起始基线：Platform-A 下降 75%，Platform-B 下降 87% [p10]（现网，看图）；注：Platform-A 起始时已处于前一轮改进周期，Platform-B 为新平台
- 提到的公司/客户/产品/标准：Meta；平台匿名为 Platform-A / Platform-B
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（两平台中断来源占比表）；p10（2026 年中断率下降曲线）

### P126 BUILDING AI RACK SYSTEM WITH OPEN STANDARDS
- 讲者/机构：Mike Wong，Senior Director Product Management，HPE；Shangxin Du，Director Product Management，AMD | 类型：厂商展区/技术分享（track 标为 AI Open Data Center）
- 方向归属（主/次）：主 [Up 机柜/超节点：UALink/UALoE]；次 [Out 后端网络：MRC、NIC、多平面]
- 核心主张：
  1. AMD Helios（HPE 版本）以 72 GPU 为统一计算单元，scale-up 用 UALoE（UALink over Ethernet）跑在以太网交换机上，提供 Pod 内共享 load/store。
  2. scale-up 运维靠 Link Level Retry 和 vPod 隔离（以 VLAN 隔离，故障不跨 vPod）。
  3. scale-out 用可编程 AI NIC（Pensando Vulcano）支持 RoCEv2/MRC/UEC 等多种传输，并用多平面 + 包喷洒在无核心层的情况下实现大规模非阻塞。
- 关键数据：
  - 每机柜 72 GPU、31 TB HBM4、HBM4 带宽 1.7 PB/s、scale-up 带宽 260 TB/s、scale-out 带宽 43 TB/s、AI 算力 2.9 Exaflops [p2]（自报）
  - 18 个 compute tray；12 台 TH6 scale-up 交换机（512-lane）[p3]
  - 每 GPU 72 条 UALoE @212G；scale-up 1.8 TB/s/dir per GPU；scale-out 最高 2.4 Tb/s/dir per GPU；Ethernet 4 @200G；UAL 8 @128G [p3]（自报，部分看图）
  - vPod 首发时按 compute tray 粒度分配；需要 ≥4 GPU 的作业分配一个 vPod [p6]
  - 多平面：800G NIC 拆为 4×200G 接入 4 个独立平面；图中每 MI455X 两块 Vulcano 800G，经 OSFP 1.6T 与 8×8 shuffler 接入 8 个 1.6T 平面 [p10]
  - scale-out 用 64 台 1.6T 以太网交换机 [p11]
- 提到的公司/客户/产品/标准：HPE、AMD Helios、MI455X、EPYC、Pensando Vulcano 800 AI NIC、P4DMA Engine、AMD Fabric Manager（AFM）；Broadcom TH6；UALink/UALoE、RoCEv2、MRC、MetaRoCE、UEC、NVMeoF、NSCC、ORW 机柜
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（Helios scale-up pod：12 台 TH6 + 72 GPU 连接图）；p10（多平面 + shuffler 拓扑）

### P128 Breaking-up-the-Monolith-An-Open-Architecture-for-Multi-rack-Scale-up-Domain-of-5000-GPUs
- 讲者/机构：Dan Daly，CTO & Co-Founder，Delos Data；Promode Nedungadi，CTO，Eridu | 类型：技术分享（并发起新 OCP 工作流）
- 方向归属（主/次）：主 [Up 机柜/超节点：多机柜 scale-up、ESUN]；次 [Out：交换芯片]、[Out：光互连/OCI]
- 核心主张：
  1. 单体机柜（~MW/机柜、最多 64 GPU + 8 备份、封闭）难以继续扩展；现有"大域"名义上很大，实际单跳域很小，跨机柜性能更低，需要拓扑感知放置。
  2. 提出开放、解耦、多机柜 scale-up 架构：高 radix 交换 + 光互连（OCI 等 MSA）把单跳域扩展到数千 xPU。
  3. 实现需要 petabit 级交换机，必须从"演进"转向架构、I/O 密度、封装、供电、冷却的芯片-系统协同设计。
- 关键数据：
  - 路由专家数：Llama 4 128、DeepSeek-V3 256、Kimi K2 384、Kimi K3 896、2028–29 预测 2k–5k [p3]（引用/预测，看图）
  - 单封装峰值 FLOPs（2023=1x）：2024 2x、2025 4x、2026 13x、2027 25x、2028 49x [p3]（预测，看图）
  - 公布的 scale-up 域 vs 单跳域：NVL72/AMD Helios 72/72；NVL576（2027）576/72；NVL1152（2028）1,152/144；OpenAI Jalapeño 2,048/128；Microsoft Maia 200 6,144/48 [p6]（引用 Hot Chips 2026、GTC 2026、AMD Advancing AI 2026、Google ISCA 2023，看图）
  - 单体机柜：功率密度 ~MW/机柜；实际上限 64 GPU + 8 备份 [p4]
  - 端点数/行数/最长线缆：128/1/~4m；512/3/~10m；576/3/~10m；2048/5/~15m；5120/12/~30m [p9]；看图细节：128 端点 = 4 compute + 1 switch 机柜，最长 ≈12 ft；2048 端点 = 50 compute + 10 switch 机柜，≈49 ft；5120 端点 = 120 compute + 24 switch 机柜，≈98 ft [p10–p12]（看图）
  - 交换芯片代际：51.2 Tbps（2022 量产，单体 ASIC，5 nm）→ 102.4 Tbps（2026，单体核心 + 独立 I/O tile，3 nm）[p14]（引用 650 Group）
  - 训练仿真：230T 交换机 GPU 利用率 64%，petabit 交换机 88%，即提升 38% [p16]（仿真，引用 Turbalance / HotInterconnects 2026，看图）
  - 新 OCP 工作流 "Open Multi-rack Scale-up Domains"，11 月初启动会 [p19]
- 提到的公司/客户/产品/标准：Delos Data、Eridu；Nvidia NVL72/576/1152、AMD Helios、OpenAI Jalapeño、Microsoft Maia 200、Llama 4、DeepSeek-V3、Kimi K2/K3；UEC、ESUN、ORv3、OCI MSA；650 Group、Turbalance
- 首次/记录/SOTA 声明：无（"petabit-class switch" 为目标而非已发布产品）
- 推荐配图页：p6（公布域大小 vs 单跳域对比）；p16（64% vs 88% GPU 利用率）；p12（5120 端点 12 行布局及 ~30 m 最长光纤）

### P129 Cluster-less Validation of AI Accelerator Silicon Under Real Workloads
- 讲者/机构：Matt Bergeron（Meta）；Ashutosh Kumar、Cosmin-Nicolae Prunaru（Keysight Technologies）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]（芯片验证）；次 [Out 后端网络：拥塞]
- 核心主张：
  1. 大规模下网络行为主导负载性能，但在 bring-up 实验室里看不到；到集群阶段才暴露的问题只能用 workaround 修。
  2. 用 Keysight 硬件测试端口模拟 fabric（时延、排队、ECN、损伤）和对端 rank，用 Chakra DAG 生成可重复的训练通信模式，在没有集群时验证 MTIA。
  3. 同一集合操作在隔离和真实负载中的性能差异明显，需要标准化评分卡并扩展到 1K–10K rank。
- 关键数据：
  - 实验配置：32 rank = 4 机柜 × 8 rank；2 层/stage、2 micro-batch/层、8 个 TP 组 × 4 rank；DP/EP 走 scale-out，PP/TP 走 scale-up；每个集合操作隔离运行 100 次 [p8]
  - EP ALLTOALL（4 rank, 8MB）在负载中约慢 1.3x：隔离 max 2,177 µs vs 负载中 max 2,957 µs [p9]（实验，看图）
  - DP ALLREDUCE（4 rank, 64MB）在负载中约慢 1.8x 且总是更慢：隔离约 32,933–32,937 µs vs 负载中 55,974–60,120 µs [p10]（实验，看图）
  - 所有 DP ALLREDUCE 在负载中都更慢，其中 50% 更严重；约 90% 的流在负载中变慢 [p11]（实验）
  - ALLGATHER/REDUCESCATTER（16MB）负载中仅略慢（max 4,261/4,211 vs 4,152 µs）[p9]（看图）
  - 慢的原因：scale-out 上 EP 反向 A2A 与 DP 梯度 AR 重叠 [p12]
- 提到的公司/客户/产品/标准：Meta MTIA、Keysight；ML Commons Chakra DAG；RDMA、ECN
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（围绕 MTIA 的模拟 fabric 与模拟 rank 架构）；p10（DP ALLREDUCE 隔离 vs 负载 1.8x）

### P130 Co-Designing-AI-Fabrics-Inside-Google-s-Virgo-Network-and-the-Campus-as-a-Computer
- 讲者/机构：Sunil Ahluwalia，Group Product Manager；Jeongkeun "JK" Lee，Software Engineer（Google）| 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：多平面、负载均衡、OCS]；次 [Across：多数据中心/园区]、[运维/可靠性/遥测]
- 核心主张：
  1. 把整个园区当作一台计算机设计；scale-out 加速器后端网络（Virgo）与前端网络（Jupiter）独立。
  2. Virgo 用两层交换、全非阻塞、独立多平面，单链路或单交换机故障不应导致训练崩溃；可扩展到多数据中心站点。
  3. 主机与 fabric 协同：CSIG、高速交换遥测（HST）、Firefly 时钟同步；Falcon 传输已在 NVIDIA 网卡上实现互通。
- 关键数据：
  - 2026 年发布 Gemini 3.5/3.6/3.7/3.8；客户直接 API 用量 >22 billion tokens/min [p3]（自报）
  - 每 GPU 网络带宽：约 2016 年 50 Gbps → 2022–2024 年约 400 → 2025 年约 800 → 2026 年约 1,600 Gbps [p3]（看图，目测）
  - 多平面：平面数 N ≈ 每加速器的 SerDes 级"skinny link"数；单平面故障时剩余 (N-1)/N 带宽；无需第三层即可多平面扩展 [p7]
  - HST 提供亚毫秒级交换机端口/队列可见性；Firefly 提供端点 NIC 微秒级时钟同步 [p8]
  - Falcon：包喷洒、亚微秒 Swift 与 CSIG、SACK + RACK 硬件丢包恢复、线速 PSP 加密；ConnectX 到 BlueField，与 Google NIC 线格式互通、标准 IB Verbs [p9]
  - 下一步：long-haul RDMA 后端（scale across）；将 CSIG 扩展到亚 RTT 拥塞控制（UEC）[p10]
- 提到的公司/客户/产品/标准：Google Virgo、Jupiter、Apollo（OCS）、ICI、Falcon、Swift、CSIG、HST、Firefly、PSP、TCP BBR、QUIC、Andromeda；NVIDIA ConnectX、BlueField、DOCA；UEC；SRv6
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（Virgo 两层多平面 + Apollo OCS + Jupiter 架构）；p3（每 GPU 带宽增长曲线）

### P132 Demystifying MRC and UET- A Panel of Experts
- 讲者/机构：Mark Handley（OpenAI）；Rip Sohan、Eric Spada（Broadcom，Distinguished Engineer）；Keith Underwood（HPE Fellow）；Hugh Holbrook（Arista CDO，主持）| 类型：面板
- 方向归属（主/次）：主 [Out 后端网络：UEC/MRC]
- 核心主张：
  1. UET 与 MRC 共享核心技术：包喷洒、乱序交付、流量引导。
  2. 差异在组织、起点、API 与目标域（UET 面向 AI 与 HPC，MRC 面向 AI 训练）。
  3. 面板讨论内容未在幻灯片中呈现。
- 关键数据：
  - UET：UEC 主导，1.0 于 2025 年发布，起点为 clean slate，API 为 libfabric（libibverbs 即将支持），拥塞控制 NSCC 或 RCCC [p3]
  - MRC：OCP MSA，1.0 于 2026 年发布，起点为 RoCE，API 为 libibverbs，拥塞控制 NSCC [p3]
  - 两者丢包检测：SACK、NACK、超时、trimming [p3]
- 提到的公司/客户/产品/标准：OpenAI、Broadcom、HPE、Arista；UEC/UET、MRC、ESUN、libfabric、libibverbs
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（UET vs MRC 快速对比表）

### P133 Enabling-AI-Networking-Scale-with-Multi-path-Reliable-Connections-MRC
- 讲者/机构：Eric Spada，Distinguished Engineer，Broadcom；Guohan Lu，Member of Technical Staff，OpenAI | 类型：标准进展/技术分享
- 方向归属（主/次）：主 [Out 后端网络：MRC、负载均衡、拥塞控制]；次 [运维/可靠性/遥测]
- 核心主张：
  1. RC 在 AI 规模下的三个问题：一个 QP 只哈希到一条 ECMP 路径、单个丢包触发 go-back-N、故障恢复依赖超时与路由收敛。
  2. MRC 对应用保持可靠连接和有序完成语义，底层做逐包喷洒、有界乱序、选择性恢复、多路径/多平面；用 SRv6 源路由让端点不依赖路由收敛，故障变成"选路事件"而非连接失败。
  3. MRC 标准化的是拥塞信号（ECN、RTT、SACK 时钟、接收端背压、反射 EV），不强制单一拥塞算法；本实现用 NSCC。
- 关键数据：
  - 2024 年初启动；目标 10^6 节点；参与方 AMD、Broadcom、Intel、Microsoft、NVIDIA、OpenAI [p2]
  - 有界乱序示例：MPR（最大 PSN 范围）= 8 个包，请求端重传跟踪 ≤ MPR [p7]
  - 生产事件：75K GPU 的训练作业中一台 T1 交换机停止转发，约 25% 的 QP 受影响，约 580K 个包被丢弃；MRC 移除故障路径后吞吐恢复 [p12]（现网，看图）
  - 吞吐曲线：稳定约 12.2–12.5 Pb/s，交换机失效时跌至约 10.5 Pb/s，约 1 分钟内恢复；随后交换机重启与恢复上线期间吞吐无明显下降；丢包率峰值约 0.00014%（右轴，目测）[p13]（现网，看图）
- 提到的公司/客户/产品/标准：Broadcom、OpenAI、Microsoft、AMD、Intel、NVIDIA；MRC 1.0、RoCEv2、SRv6 uSID、NSCC、libibverbs、mrc.h / mrc_ctl.h、UEC
- 首次/记录/SOTA 声明：无明确声明（p12 为 75K GPU 生产作业故障实录）
- 推荐配图页：p13（T1 交换机失效/重启时的吞吐与丢包曲线）；p6（SRv6 源路由与 EV 拒绝列表）；p8（SACK 选择性重传 vs go-back-N）

### P134 End-to-End-AI-backend-fabric-design
- 讲者/机构：Sandeep Balani，Principal Product Manager；Mehak Mahajan，Senior Director of Engineering（Broadcom CSG）| 类型：厂商展区/技术分享
- 方向归属（主/次）：主 [Out 后端网络：交换芯片、NIC、MRC、多平面]；次 [Up]、[Across]
- 核心主张：
  1. 传统 RDMA 无多路径、无乱序交付、go-back-N 低效、DCQCN 难调，不适合 AI 规模；MRC 作为增强版 RoCE 补齐这些能力。
  2. 用端口拆分（breakout）+ 多平面，在两层 Clos 下把 XPU 规模从 8K 扩展到 128K。
  3. scale-up、scale-out、scale-across 三类网络需求不同：scale-up 要低时延、无损（CBFC、LLR）；scale-across 要长距离、大缓冲。
- 关键数据：
  - 两层 Clos（TH6，800G 端口，64 spine / 128 leaf，每 leaf 64 XPU）最大 8K XPU [p6]
  - TH6 端口拆分：800G → 128 leaf / 64 spine / 8K 端点；400G → 256 / 128 / 32K；200G → 512 / 256 / 128K [p10]
  - Thor Ultra NIC 拆分：1×800G、2×400G、4×200G、8×100G [p11]
  - 4 平面（每 XPU 4×200G）两层多平面 fabric 最大 128K XPU [p13]
  - Scale-up 需要约 10X scale-out 带宽；scale-across 距离约 km 级（大 RTT），通常有收敛比，使用大缓冲交换机 [p18]
- 提到的公司/客户/产品/标准：Broadcom Tomahawk 6（TH6）、Thor Ultra；MRC、RoCE、SRv6、DCQCN、CSIG、ECN、CBFC、LLR、BGP；UEC、OCP
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（TH6 端口拆分与规模对应表）；p13（4 平面 128K XPU fabric）

### P135 Evolution of Congestion Control in AI Ethernet Fabrics
- 讲者/机构：Mehak Mahajan、Mohammad Hanif（Broadcom，Senior Director of Engineering）| 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：拥塞控制]
- 核心主张：
  1. AI 流量同步、突发、严重 incast、大象流、低熵，对尾时延敏感；DCQCN 依赖 ECN+PFC，会扩散拥塞、造成队头阻塞，难调且不可互通。
  2. 新一代拥塞控制需要支持多路径、对故障有弹性、规模化无性能折损，且 NIC 流控与网络信号协同。
  3. 两条路线：接收端 credit 的 RCCC 和发送端的 NSCC；配合 ECN、RTT、trimming、CSIG 等网络信号。
- 关键数据：
  - RCCC：无 PFC 的有损网络；首 RTT 线速启动，之后接收端向活跃发送端发 credit；一个 RTT 收敛；稳态时最后一跳队列为 0 且满利用率 [p8]（自报）
  - NSCC：以时延为主要拥塞量，ECN 为队列的先行指标；窗口增加用比例 + 指数，减小用乘性 [p10]
  - CSIG 每包携带：路径上最小可用带宽、最小可用容量（%）、最大单跳时延；正在 UEC Transport WG 标准化 [p13]
  - Trimming：拥塞时转发截断包，以高优先级队列转发并改写 DSCP，接收端发 NACK [p12]
- 提到的公司/客户/产品/标准：Broadcom Thor3；DCQCN、PFC、ECN、RCCC、NSCC、CSIG、UEC、MRC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（PFC 暂停导致拥塞扩散示意）；p11（四类网络拥塞信号汇总）

### P136 Fast-switching-OCS-for-AI-and-Hyperscale-Data-Centers-Benefit-Technologies-and-Potential-Applications.
- 讲者/机构：James Burch，OCS Engineering Lead，Lumotive；Vivek Sarathy，VP Products，iPronics；作者还包括 Ciena、Intel、Carnegie Mellon、Lumentum、Tripple Stone 人员 | 类型：标准进展（OCP OCS 白皮书工作）
- 方向归属（主/次）：主 [Out 后端网络：OCS]；次 [Up：CPO]
- 核心主张：
  1. OCS 已被大规模验证，但主流 3D MEMS 毫秒级重配置限制其只能用于缓慢变化的负载。
  2. 亚毫秒 OCS 可打开动态流量引导、负载感知拓扑、可调度光 fabric 等新用例；CPO 会加剧这种需求。
  3. 需要生态协同：工作负载级基准、端到端重配置指标标准化、光模块快速锁定与控制面对齐。
- 关键数据：
  - Google 通过消除 O-E-O 转换实现 30% 成本、40% 功耗改善 [p3]（引用 Google）
  - 重配置时间：超表面（自由空间）~50 μs；集成光子 MEMS 1–20 μs；集成光子热光 10–100 μs；集成光子电光 ns–μs；另列 ns（30–56 GHz）与 sub-ns（100+ GHz–THz）档 [p5]（引用/汇总）
  - Radix、循环寿命、插损是该对比之外的关键系统指标 [p5]
  - OCS 白皮书 2026 年 4 月发布；快速切换白皮书即将发布 [p10]
- 提到的公司/客户/产品/标准：Lumotive、iPronics、Ciena、Intel、CMU、Lumentum、Tripple Stone、Google；3D MEMS、metasurface、硅光、ring resonator、Mach-Zehnder、CPO
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（各类快速 OCS 技术重配置时间对比）；p4（快速 OCS 收益与挑战对照表）

### P137 From Training to Tokens- Revolutionizing AI Inference with In-Network Compute
- 讲者/机构：Helia Naeimi，Fabric Technologist；Caleb Shetland，Firmware Engineer（Astera Labs）| 类型：厂商展区/技术分享
- 方向归属（主/次）：主 [Up 机柜/超节点：in-network compute、PCIe fabric]；次 [推理/算力/经济性]
- 核心主张：
  1. 推理对 fabric 有两个要求：加速分布式 GEMM（AR/RS/AG）和支持 MoE 的动态通信模式（逐 token 的动态多播组），时延是关键。
  2. INC 对小消息的加速随集群规模线性增长，推理（几百 KB 消息）收益最大，训练的 MB 级消息也有收益。
  3. INC 已出现在 NVLink、Ethernet/UEC、PCIe 等几乎所有 scale-up 协议中，需要集合通信库提供 hook 和拓扑感知放置。
- 关键数据：
  - INC 加速（A.U.）vs 集群规模：256 节点时 1KB 约 500、8KB 约 450、128KB 约 170、1MB 约 30，8MB 接近 0 [p7]（仿真/自报，看图，单位为任意单位）
  - 大消息（8MB）在 0–64 节点范围内仍有"不可忽略"的加速，图纵轴刻度 0–6（A.U.）[p8]（自报；仅据文字层坐标，具体数值未读，存疑）
  - INC 实现需交换机有足够缓冲等待所有 GPU 的部分结果；拉模型（交换机发读请求）与推模型（GPU posted write）[p9]
  - 示例：256 节点 PCIe fabric 中带多播的 AllGather 路由 [p10]
- 提到的公司/客户/产品/标准：Astera Labs；NVLink、Ethernet/UEC、PCIe；MoE
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（INC 加速 vs 集群规模，按消息大小分组）
