---
title: "R16_keynotes"
tags:
  - OCP2026
  - 讲稿笔记
---

# R16 笔记：keynotes, fts-keynotes-awards, fts-quantum-data-center-design, fts-data-center-sustainability

### P366 05_Scaling AI Infrastructure Through Open Innovation
- 讲者/机构：Asad Khamisy，SVP/GM Core Switching Group，Broadcom（p1-2，2026-10-12）| 类型：主题演讲
- 方向归属（主/次）：主 [Up 机柜/超节点：ESUN/SUE-T、铜缆/背板、光 scale-up]；次 [Out 后端网络：交换芯片、NIC]、[Across：scale-across]
- 核心主张：
  1. 用以太网统一 scale-up / scale-out / scale-across，共享运维、遥测、线缆、光模块与备件体系（p4-p9）。
  2. Scale-up 从单柜 64–144 XPU 走向多柜 1K–2K XPU；柜内用铜背板翻倍带宽，跨柜用光，Broadcom 推出 OCI（Optical Compute Interconnect）以接近铜的功耗做到可插拔的距离（p9、p16-p22）。
  3. ESUN + SUE-T 是开放 scale-up 架构，已从概念进入量产（p10-p11）。
- 关键数据：
  - 芯片组合：Tomahawk 6 102.4 Tbps；Tomahawk Ultra 51.2 Tbps；Jericho 4 51.2 Tbps；Thor Ultra 800G NIC（p5，自报）。
  - 规模：100K+ XPU 集群（p3）；scale-up 今天 64–144 XPU/单柜，明天 1K–2K XPU/多柜（p9，自报/预测）。
  - ESUN：OCP Global Summit 2025 宣布，175+ 成员，ESUN 机柜已量产；SUE v1.0 spec 2026 年 2 月发布，SUE-T spec 目标 2H2026（p10，自报）。
  - 5+ hyperscaler 在生产中运行以太网 scale-up；10+ 伙伴在做 scale-up 以太网机柜；多款定制与商用 XPU 以太网 scale-up 机柜将在未来 6 个月量产（p11，自报）。
  - 以太网 scale-up 交换：512 x 100G-PAM4，单跳 scale-up 256；延迟 250 ns；51.2T@64B 77 BPPS；链路层重传、credit-based flow control、in-network collectives（p12，看图）。
  - 链路效率：未打包 256B posted write 92%；2 包打包 96%；4 包打包 98%；原生 2kB 块传输 99%；下一版 ESUN 规范引入优化 UFH 头与缩短 IPG（p13，自报）。
  - 柜内铜背板当前代：1.04 Pbps 整柜，14.4 Tbps/XPU，72 XPU，512x200G PAM4，9–12 台以太网交换机，26 AWG twinax 1024 根/OU，XPU 到交换机铜缆约 2 m，SerDes 7 pJ/bit，整柜约 250 kW；带宽受背板密度限制；Tomahawk6 量产中（p16，自报）。
  - 可能的下一代：2.08 Pbps 整柜，28.8 Tbps/XPU，72 XPU，576x400G PAM6，9 台交换机，同样 2 m 铜、7 pJ/bit，整柜约 500 kW（p16，预测）。
  - 光纤跨柜 scale-up：可达 576 规模域，代价是光器件成本更高、延迟 5 ns/米光纤（p18，自报）；铜+光混合机柜把 scale-up 划分为低延迟域与较高延迟域（p19）。
  - 200G 链路总功耗与距离：DAC 7 pJ/bit、2 m；Integrated OCI 7 pJ/bit、500 m；DR LRO 前面板可插拔 23 pJ/bit、500 m（p22，自报）。
  - OCI-MSA 2026 年 3 月成立，创始成员 Meta、Microsoft、OpenAI、AMD、Broadcom、NVIDIA（p20，看图）。
  - OCP Open Cluster Designs for AI：53 家成员公司，V1.0 蓝图已发布，覆盖 XPU pod 到 XOC-N 数据中心网络，第二代在开发（p23，自报）。
- 提到的公司/客户/产品/标准：Broadcom Tomahawk 6/Ultra、Jericho 4、Thor Ultra；ESUN、SUE-T、OCI-MSA、ORv3、SAI/SONiC；Meta、Microsoft、OpenAI、AMD、NVIDIA。
- 首次/记录/SOTA 声明：宣布 OCI（Optical Compute Interconnect）及 OCI-MSA（p20）；"Ethernet scale-up from concept to production"（p11）。
- 推荐配图页：p16（铜背板当前代与 2x 下一代参数对比表）；p22（DAC / OCI / LRO 功耗与距离对比）；p12（以太网 scale-up 指标 250 ns、77 BPPS）。

### P367 06_AI Factories at Scale Advancing Open Infrastructure for Agentic AI
- 讲者/机构：Ian Buck，VP Hyperscale and HPC Computing，NVIDIA（p1-2，2026-10-12）| 类型：主题演讲
- 方向归属（主/次）：主 [Out 后端网络：Spectrum-X、多平面、传输协议 Falcon/MRC/RoCE]；次 [Up：NVLink 7 CPO、NVL576]、[底座-机架/机械：MGX 1.2]、[底座-电力：800 VDC、MaxLPS]、[推理/算力/经济性]
- 核心主张：
  1. NVIDIA AI 工厂是"高产、耐用、可替换"的资产，基于 OCP 开放标准；全栈协同设计在 agentic 负载上带来最高 30x 吞吐（p4-p5）。
  2. 向 OCP 贡献第三代 MGX（MGX 1.2）规范，Vera Rubin 托盘无线缆、无风扇、无软管（p6-p7）。
  3. Spectrum-X 以太网支持多种 AI 传输（Falcon、Meta RoCE、MRC、Spectrum-X Adaptive RDMA），并通过多平面光子交换做到 512K GPU 两层扁平网络（p14-p17）。
- 关键数据：
  - 产品寿命：V100/DGX-1 服役 10 年；A100 6 年仍在售（9 年）；NVL72 1 年（销售期 7 年）；Vera Rubin 已全面量产（p4，自报）。
  - DeepSeek-V4-Pro / SemiAnalysis AgentX：Vera Rubin NVL72 对比 GB300 NVL72，每 MW token 吞吐在不同交互速度下提升 2x / 10x / 30x，每百万 token 成本最高低 45x（p5，看图；横轴数值被截断，看不清）。
  - MGX 1.2：机架加强 +100 lb 钢结构；锁扣杆支持 6,000 lb 插拔力；液冷母排 5,000 A；盲插歧管 45°C 液冷；UQD08；铜 spine 4 个线缆盒，可用于 NVLink 或 Spectrum-X 以太网；1U 液冷交换托盘（p6，自报）。
  - 800 VDC：16 MW 部署单元，800 VDC 母排架空分配到 4 个 4 MW 可扩展单元，机柜级 800 VDC 125 A tap can；Visionbay.ai 称首个 800 VDC AI 工厂（p8，自报）。
  - Vera CPU：Olympus 核，核间带宽 3.4 TB/s，每核内存带宽 1.2 TB/s（LPDDR5X），对比 Grace 2x 性能；TACC HPC Golden Suite 2x，Meta DCPerf 2x，Apache Kafka/Redpanda 3.5x（p9-p10，自报）。
  - MaxLPS：同样电力多部署 40% GPU（p12）；Nscale GB300 集群同一供电预算多部署 37% GPU、吞吐提升 49%（Kimi K2.5，8K/1K，冰岛）（p13，自报+看图）。
  - Spectrum-X Photonics 多平面：可扩展到 512K GPU 的两层扁平网络；交换机数量少 40%；故障检测 2.6 ms；MTBI 高 10x；能效 5x（p14，看图）；故障检测比传统软件方式快 30x（p15，自报）。
  - Meta 102.4T FBOSS 交换机（N-IceCube）基于 Spectrum-6（p15）。
  - Google Falcon 传输运行于 NVIDIA 网络：多路径负载均衡、可编程拥塞控制、硬件丢包恢复、每连接加密（p16）。
  - Vera Rubin Ultra NVL576 CPO：NVLink 7 CPO 交换托盘，面向 10T+ 参数模型（p18，看图为 8 柜一排）。
- 提到的公司/客户/产品/标准：MGX 1.0/1.1/1.2、Vera Rubin NVL72/NVL576、GB300、Vera CPU、Spectrum-6、ConnectX-9、BlueField-4、NVLink 7 CPO、DSX、MaxLPS；Meta FBOSS、OCP SAI、Google Falcon、MRC、Meta RoCE；Nscale、Visionbay.ai、Meta、Microsoft、OCI（Oracle）、Cadence。
- 首次/记录/SOTA 声明：贡献第三代 MGX 规范到 OCP（p6）；"world's fastest fault detection"（p15）；Visionbay.ai "First 800 VDC AI Factory"（p8）。
- 推荐配图页：p14（Spectrum-X 多平面四项指标）；p18（NVL576 CPO 机柜排）；p6（MGX 1.2 结构标注）。

### P363 02_Building the Next Era of AI Infrastructure
- 讲者/机构：Dr. Lisa Su，AMD（p1）| 类型：主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [Up：UALoE/ESUN]、[Out：UEC/MRC/MetaRoCE]、[底座-机架/机械：ORv3/ORW]
- 核心主张：
  1. 推理已成为第一大 AI 工作负载，agentic 使用推动 CPU 与 GPU 需求同时加速（p5-p7）。
  2. 前沿 AI 需要集成的机柜架构，Helios 以开放 scale-up（UALoE、ESUN）与 scale-out（UEC、MRC、MetaRoCE）组网（p10-p15）。
  3. Agent 需要合适的 CPU 机柜，推出 Helion Agentic AI Rack（p21-p27）。
- 关键数据：
  - 过去 2 年每月 token 消耗增长 95x（p5，自报）。
  - 训练 FLOPs 自 2020 年每年 5x（p6，引用 Epoch AI 2026-10-05）；OpenRouter agentic token 年内增长 >14x（p6，引用 OpenRouter）。
  - 数据中心 CPU TAM 2025 约 \$26B → 2030 约 \$220B，CAGR >50%；AI 加速器 TAM 2025 约 \$200B → 2030 约 \$1.4T，CAGR >45%（p7，AMD 内部预测，看图）。
  - Helios：2.9 EF FP4 / 1.48 EF FP8；31 TB HBM4，1.7 PB/s；scale-up 260 TB/s，scale-out 43 TB/s；最高多 30% tokens/\$；DeepSeek R1 推理 17,000 tokens/s/GPU（MLPerf offline，AMD 自测）（p15，自报+看图）。
  - Helios 已在 OpenAI、Meta、Anthropic、Microsoft、Oracle 部署（p17，看图）。
  - Helion Agentic Rack：ORv3 44OU；最多 16 个 MI350P，74 PF FP4；最高 102 Tbps 网络；最多 32,768 个 Zen 6 核；2026 年 11 月供货（p24、p27，自报）。
  - EPYC "Venice"：256c @400W（dense）、256c @600W（balanced）、96c @5.0GHz（performance）；Venice LPDDR 版最高 192c，1H 2027（p25-p29，自报）。
- 提到的公司/客户/产品/标准：Helios、Helion、MI350P、EPYC Venice/Venice-X、Verano、ROCm；UALink/UALoE、ESUN、UEC、MRC、MetaRoCE、ORW、ORv3；OpenAI、Meta、Anthropic、Microsoft、Oracle 及 p18 列出的约 30 家伙伴。
- 首次/记录/SOTA 声明：发布 Helion Agentic AI Rack（"Announcing today"，p23）；Helios 在算力/内存/网络三项标"#1"（p15，自报）。
- 推荐配图页：p15（Helios 规格汇总）；p7（CPU 与加速器 TAM 预测）；p13（Helios front-end/scale-up/scale-out 协议划分）。

### P354 Inference-Data-Center-2030-Memory-Pod-Fabric-with-Rightsized-Compute-presented-by-Samsung
- 讲者/机构：Mayank Saxena，Chief Technologist，Memory Solutions Lab，Samsung Semiconductor（p1）| 类型：主题演讲（FTS keynote）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化、HBM]；次 [Up：光互连 memory fabric]、[推理/算力/经济性]
- 核心主张：
  1. 推理数据中心应从"算力为中心"翻转为"内存为中心"：先选内存 fabric，再按负载配置合适大小的算力（p2）。
  2. 2030 推理中心由光子 fabric 连接的分解式内存池（3D DRAM、HBM over optical、HBM5、SOCAMM）构成，容量从 EB 走向 ZB（p3）。
  3. 今天要做的决定是定义 locality contract，按 token 路径设计放置与观测，而不是泛泛的分解内存（p4）。
- 关键数据（均为架构目标/定性量级，非实测）：
  - 内存层级表：L0 <数十 ns、>数十 TB/s、数 MB；L1 ~数十 ns、数 TB/s、数十 GB；L2 ~数十 ns、数百 GB/s、数百 GB；L2.5 数百 ns、数百 GB/s、数百 GB~1 TB；L3 ~数 µs、~数 GB/s、数 TB；L3.5 ~数十 µs、数百 GB/s、数十 TB；L4 ~数 ms、~MB/s、数十 TB（p4，自报/预测）。
  - 对应介质：SRAM、HBM over Optical、zHBM、HBM5、LPDDR/SOCAMM、3D DRAM、CXL Pool、KV SSD、Ethernet SSD、TLC/QLC SSD、zNAND-O（p4）。
  - Pod 划分：Decode Pod（GPU/NPU）、Prefill Pod（GPU）、MoE/Kernel Pod、In-network compute、Recovery Pod（CPU/DPU）；跨域走光路径，compute 与 active state 走短电路径（p4）。
- 提到的公司/客户/产品/标准：Samsung；HBM5、SOCAMM、zHBM、zNAND-O、CXL、glass substrate。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（L0–L4 内存层级与 pod 划分）；p3（光子 fabric 连接的 memory pod 示意）。

### P362 01_Welcome to the 2026 OCP Global Summit
- 讲者/机构：George Tchaparian，CEO，Open Compute Project Foundation（p1）| 类型：主题演讲（开幕）
- 方向归属（主/次）：主 [标准进展/社区]；次 [Up/Out：ESUN、SUE-T、MRC]、[底座-电力：800 VDC→1500 VDC]
- 核心主张：
  1. OCP Open Data Center Ecosystem Vision（2025 年 10 月发布）把范围从机柜/系统扩展到"从电网到芯片"（p7、p9）。
  2. 2027 之后的三个方向：AI 芯片多样性需要系统-工艺协同优化；数据中心按 AI 芯片定制；agentic/推理推动 hyperscale adjacent 分布式部署（p10-p12）。
- 关键数据：
  - 687 家企业会员，2026 年至今新增 195 家（p5，自报）。
  - 规范贡献：截至 Q3 2026 共 105 项，同比 +30%（Q3'24 73，Q3'25 81）（p5，自报）。
  - 2026 进展：800 VDC 配电向 1500 VDC 演进；网络发布 ESUN、SUE-T、MRC 规范；芯片 FCSA 与 BoW Flexi 规范；Open Rack ORW 与 HPR 规范（p8）。
  - 2030 市场规模 \$890B（p9，自报，口径未说明）。
- 提到的公司/客户/产品/标准：ESUN、SUE-T、MRC、FCSA、BoW Flexi、ORW、HPR、OCP Nexus；后续 keynote 讲者所属 AMD、Meta、Arm、Broadcom、NVIDIA、Microsoft、Oracle、HPE、Intel、Google 等（p13-p14）。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（2026 年各领域规范进展汇总）；p9（Grid→Chip 分层与 \$890B）。

### P368 07_OCP Welcome Address
- 讲者/机构：George Tchaparian，OCP Foundation（p1）| 类型：主题演讲（第二天开场）
- 方向归属（主/次）：主 [标准进展/社区]；次 [Out：Open Cluster Design]、[底座-电力：Energy]、[安全]
- 核心主张：
  1. OCP 市场、会员和学院各项指标同比增长 30–46%（p4-p5）。
  2. 2027 愿景新增 Energy 子项目、Open Cluster Designs for AI、安全（S.O.L.I.D.）（p9-p11）。
- 关键数据：
  - Marketplace：月均访问 36K（+38%）；solution provider 183（+32%）；产品 683（+39%）；AI 相关产品 213（+46%）；Experience Center 33（+43%）；OCP Ready 数据中心 26（+30%）（p4，自报）。
  - OCP Academy：6,000+ 学员，30,000+ 学习小时，100+ 课程（p5）。
  - Open Cluster Design：OPG-M 风冷 400GE pod 设计已完成（2026 年初）；DLC 液冷 576-pod、800GE/1.6TE 网络设计进行中；XOC-N 覆盖 scale-out 域的 spine/aggregation、head-end 等（p10，看图）。
  - Energy 子项目 Q2 启动，已贡献 Hyperscaler-电网扰动性能接口规范 V1.0.0、数据中心储能系统要求（p9）。
  - 安全：Caliptra（2022）、S.A.F.E.（2023）、S.O.L.I.D.（2026）；关注 AI 驱动威胁、后量子迁移（p11）。
- 提到的公司/客户/产品/标准：OPG-M、XOC-N、Caliptra、OCP S.A.F.E.、OCP S.O.L.I.D.
- 首次/记录/SOTA 声明：OCP S.O.L.I.D. 2026 推出（p11）
- 推荐配图页：p10（OPG-M 576-pod 800GE/1.6TE 设计状态）；p4（Marketplace 指标）。

### P360 The-Classical-Infrastructure-of-Fault-tolerant-Quantum-Computing
- 讲者/机构：Smriti Bajaj，Applied Researcher，Office of the CTO，Dell Technologies（p1）| 类型：技术分享
- 方向归属（主/次）：主 [量子/其他]；次 [Out：RoCEv2 低延迟互连（NVQLink）]
- 核心主张：
  1. 实时 QEC 需要量子与经典系统紧耦合：误差纠正需要 ~µs 级访问 FPGA 解码器与 GPU 服务器（p2）。
  2. Dell HQCC 以 QIO 编排 + NVQLink（RoCEv2）闭合实时环（p5-p6）。
- 关键数据：
  - 时间尺度：混合应用 ms；纠错 ~µs；校准 s 到 min（p2，自报）。
  - Dell HQCC：HPC ⇄ GPU 服务器走 TCP/IP、RoCEv2；GPU 服务器 ⇄ 控制器走 NVQLink（RoCEv2）；往返延迟 <4 µs（p6，看图，自报）。
  - Dell 称首个基于 GenAI（扩散模型）的量子误差缓解方案，测试平台为 IQM Garnet（p8，自报）。
  - 历程：2026 DTW 现场 HQCC 演示（R770 + QIO + Equal1），IEEE QW 实时 QEC 演示（QIO + Qblox）（p10）。
- 提到的公司/客户/产品/标准：Dell QIO、PowerEdge R770/R760xa；NVIDIA NVQLink、CUDA-Q；IQM、Qblox、QuEra、IonQ、Equal1、Diraq、IBM Qiskit；Slurm；OCP Future Technologies Initiative。
- 首次/记录/SOTA 声明：GenAI 用于 QEM "first solution (to our knowledge)"（p8）
- 推荐配图页：p6（HQCC 架构与 <4 µs NVQLink 链路）。

### P361 Toward-Quantum-Superconducting-with-IQM-Quantum-Processors
- 讲者/机构：Khadijeh Sona Najafi, Ph.D.，Quantum Solution Manager，IQM（p1）| 类型：技术分享
- 方向归属（主/次）：主 [量子/其他]；次 [Out：低延迟 RoCE/RDMA 互连（NVQLink、ERNIC）]
- 核心主张：
  1. 量子与 HPC 集成不可避免，应用、误差缓解/编译、纠错三层各自产生不同的经典计算需求（p9-p10）。
  2. 耦合分三档：Tier T（≲100 µs，互连问题）、Tier M（0.1 ms–1 s，调度问题）、Tier L（≳1 s，联邦/身份问题），解决一个不等于解决其他（p15-p16）。
  3. IQM Constellation 拓扑（每比特 12 个邻居）配合 Barbell qLDPC 码降低纠错开销（p25）。
- 关键数据：
  - IQM 2Q 保真度：Crystal-20 median 99.76%、best 99.85±0.02%；Crystal-54 median 99.47%、best 99.85%；Star-24 CZ median 99.26%；Constellation CZ median 99.37%、best 99.52%、hero 99.67%（p3，看图）。
  - 实时耦合实测：Backline（Xanadu·AMD）FPGA→协处理器→FPGA 平均往返 2.3 µs（CPU）/ 4.4 µs（GPU）；NVQLink（NVIDIA·Quantinuum·IQM with Zurich Instruments）RoCE 平均往返 3.84 µs（σ=0.035 µs，n=1000）（p32，实验）。
  - IQM Radiance 20 连续运行 >150 天，除每周 5 分钟液氮补充外无人工干预（p13，现网）。
  - 已集成 11 台量子超算；2026 ORNL Pathfinder 20 比特为首个美国装机；2027 LUMI-IQ 150 比特（p14，自报）。
  - Barbell 码：30 物理比特对应 1 逻辑比特，资源成本比 rotated surface code 低 8x（p25，仿真，引用 arXiv:2606.06062）。
  - IQM Halocene：首套 150 比特，2026 年底起安装，5 个逻辑比特用于研究（p26，自报）。
  - VW×IQM 电池化学：100 轨道体系预计运行时间从约 500 年降到约 1.8 年（1000 万 CPU 核），最高 248x（p21，仿真/引用 arXiv:2606.19239）。
- 提到的公司/客户/产品/标准：IQM Crystal/Star/Constellation/Radiance/Halocene；NVQLink、CUDA-Q、Backline、ERNIC、RoCE/RDMA、QDMI；VTT、LUMI、LRZ、CINECA、ORNL、IT4I、CESGA；Volkswagen、Algorithmiq、Xanadu、AMD、Quantinuum、Zurich Instruments。
- 首次/记录/SOTA 声明："Helmi ⇄ LUMI first EU hybrid service"（p12、p14）
- 推荐配图页：p16（耦合档位：延迟预算 vs 数据率图）；p32（Backline 与 NVQLink 实测往返延迟）。

### P359 Quantum-Networking-for-Scale-Out-Nu-Quantum-s-Entanglement-Fabric
- 讲者/机构：John Jarman，International Technical Lead，Nu Quantum（p1）| 类型：技术分享
- 方向归属（主/次）：主 [量子/其他]；次 [Out：光路交换/OCS 类可重构光网络]
- 核心主张：
  1. 单 QPU 扩展止步于约数百逻辑比特，商业价值需要多 QPU scale-out，通过纠缠连接（p2、p4，看图）。
  2. 纠缠链路需要高效 qubit-photon 接口、低损耗快速重构的光交换网络和低延迟经典通道（p5）。
  3. 目前尚无网络达到分布式量子计算所需的速率与保真度（p9）。
- 关键数据：
  - 路线：2027 100 逻辑比特、10^-6；2030 1,000 逻辑比特、10^-9；2033 6,000 逻辑比特（RSA 破解）；2035 10,000+ 逻辑比特（p2，看图，预测）。
  - 纠缠成功率 P = ½η²，η = η_interface × η_router；保真度误差可加（p8，看图）。
  - QNU Gen 1（2025）：纠缠保真度最高 99.7%，MHz 级尝试速率，控制系统延迟 300 ns；Gen 2（2027）采用自有交换技术（p14，看图，自报）。
  - Testbed：纠缠速率提升 50x，保真度 >97%（p17，看图，自报）。
  - 微腔：两个曲面镜间距 <1 mm（p13，看图）。
- 提到的公司/客户/产品/标准：Nu Quantum QNU、QPI；Quantinuum、IonQ、QuEra、Pasqal、IBM、Google、Rigetti、AWS、OQC 等（p12）。
- 首次/记录/SOTA 声明：testbed "state-of-the-art fidelity (>97%)"（p17）
- 推荐配图页：p9（纠缠速率-保真度散点与 NuQ 目标）；p14（QNU 参数）。

### P356 From-Quantum-Breakthroughs-to-Data-Center-Ready-Quantum-Secure-Networks（精简）
- 讲者/机构：Remon Berrevoets，CTIO 兼联合创始人，Falqon Systems（QSNP 联盟成员）（p1）| 类型：技术分享
- 方向归属（主/次）：主 [安全]；次 [Across：城域/跨境 QKD 光网络]
- 核心主张：
  1. 量子计算机约 2029–30 年可破解加密，"现在收集、以后解密"已在发生（p2，引用 Renner & Wolf 2023）。
  2. MDI-QKD 网络无需可信中继，可扩展到多用户并与现有加密设备集成（p13、p16）。
- 关键数据：
  - Falqon：已部署 1419 km 量子网络，50+ 设备，7+ 欧洲国家（p12，自报）。
  - Benelux 首个跨境 MDI-QKD 网络 150 km（与 Belnet）（p17，现网）。
  - QSNP 路线：1 Mbit/s @80 km（QKD+OTP，单波长）→ 2030 前后 1 Gbit/s QKD @80 km 单纤；200 dB 距离 MDI/TF-QKD；SFP 形态 QKD（p8，看图，预测；年份按横轴估读）。
  - 与 Cisco C8000、Nokia 1830、Adtran FSP 3000、Juniper EX4400 集成，支持 MACsec、IPSec、OTNSec（p16）。
- 提到的公司/客户/产品/标准：Falqon MQT4000/MQX4000/MQS4000/8000；QSNP、EuroQCI；Telefónica、Deutsche Telekom、Orange、Belnet、Port of Rotterdam。
- 首次/记录/SOTA 声明：西班牙、爱尔兰首个城域多节点 MDI-QKD 网络；Benelux 首个跨境 MDI-QKD 网络（p17）
- 推荐配图页：p8（QSNP 2023–2030 路线图）。

### P358 Quantum-Computing-Market-in-2026-Trends-Opportunities-and-Challenges（精简）
- 讲者/机构：Noah El Alami，Senior Technology Analyst，IDTechEx（p1）| 类型：技术分享（市场分析）
- 方向归属（主/次）：主 [量子/其他]
- 核心主张：
  1. 多种量子比特路线技术进展接近；新进入者自 2019 年后饱和，但 2026 年多家公司上市（p6、p9、p19）。
  2. 主要商业模式是云接入，进入数据中心面临制冷、噪声、通信、电源等新基础设施要求（p11-p13）。
- 关键数据：
  - 新进入者 2019 年达峰（16 家），2026 年累计约 97 家（p6，看图估读）。
  - 2026 年 Infleqtion、Xanadu、IQM、Quantinuum、Pasqal 上市，SeeQC 计划中；纯硬件上市公司数量到 2026 年底翻倍以上（p9，自报）。
  - 量子计算硬件年收入：2037 >\$8.0B（2027–37 CAGR 31%），2047 >\$29B（2037–47 CAGR 22%），含基础设施（p17，预测，看图）。
- 提到的公司/客户/产品/标准：IonQ、Rigetti、D-Wave、IBM、Google、Microsoft、Quantinuum、IQM 等。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p17（2027–2047 硬件收入预测柱图）。

### P351 Sustainability-Lightning-Talks（精简，5 个闪电演讲合集）
- 讲者/机构：Pierre Huyn & Prasun Singh（Hitachi America）；Boya Qu（SemiValley Technologies）；Saeed Moghaddam（University of Florida）& Roshith Mittakolu（UMD）；Fanny Oukhemanou（Syensqo）；Ching-chih Wei（CreAlien）（p2、p10、p16、p23、p28）| 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [底座-电力：余热回收]
- 核心主张：
  1. 芯片功率超过约 2 kW 后单相液冷到顶，两相（尤其是以水为工质）是下一步（p11，看图）。
  2. 高出水温度（两相/膜式热沉）让余热回收在经济上可行（p17、p20）。
- 关键数据：
  - 芯片功率路线：Rubin 2.3 kW（2026）；行业预测 2035 年每 GPU 模块约 15.4 kW；风冷上限约 500 W，单相上限约 2 kW（p11，看图）。
  - Hitachi 数字孪生示例：100 kW AI 机柜，PUE 1.90→1.20（改造 1，\$350k，回收期 4.5 年）（p7，仿真）。
  - SemiValley 水两相冷板：325 W/cm² @0.14 L/min；HTC 125 kW/m²·K；温度波动 4.76→0.44°C；100 MW 站点每年省电 \$34M（对比风冷）（p12-p13，实验/自报）。
  - 膜式热沉余热回收：每 MW 余热的压缩机功耗，风冷约 610 kW、液冷约 370 kW、MHS 直接回收约 10 kW（降 97%）（p20，看图）。
  - CreAlien 水两相 1U：50×50 mm 上散热 2.0 kW，冷板厚度 13 mm；0.2 mm 鳍距在 2.5 kW 下 Tcase 59.5°C（p30-p31，实验）。
- 提到的公司/客户/产品/标准：Hitachi、SemiValley、Syensqo Galden HT-55、Lotus Thermal Solution、CreAlien；NVIDIA V100/Vera Rubin Ultra；ASHRAE W40–W45。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（芯片功率路线与风冷/单相上限）；p20（余热回收压缩机功耗对比）。
