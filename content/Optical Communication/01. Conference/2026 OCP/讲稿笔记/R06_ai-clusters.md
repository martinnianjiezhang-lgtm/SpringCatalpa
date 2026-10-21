---
title: "R06_ai-clusters"
tags:
  - OCP2026
  - 讲稿笔记
---

# R06 笔记：ai-clusters

### P138 From-Single-Data-Centers-to-Multi-Region-AI-Clusters-The-Rise-of-Scale-Across
- 讲者/机构：Spencer Giacalone（Senior Director Cloud AI Architecture）、Helen Xenos（Senior Director Product Marketing），Ciena | 类型：厂商技术分享
- 方向归属（主/次）：主 [Across：DCI、ZR/相干] / 次 [Out：拥塞控制]
- 核心主张：
  1. 主机与协议层优化（分层 collective、UEC/MRC/MetaRoCE 等无损协议）只能管理争用，不能提供所需容量；光层容量是 Scale Across 的基础 [p2]。
  2. Scale Across 定义为"在园区或区域之间延伸无损连接以训练单个模型"，由拥塞管理的分组层 + 专用相干光层两层组成；规模化相干 DWDM 是 Scale Out 与 Scale Across 的主要区别 [p4]。
  3. 规模化后"光纤成为部署单元"，部署速度要求走向全光纤架构（多轨光层 + 全频谱转发器 FST）[p11][p13]；呼吁 OCP 标准化"可证明无损"的物理层 FEC 要求 [p15][p16]。
- 关键数据：
  - O-band IMDD（园区）：约 10 km 以内（DR/FR/LR），每纤单 Tb/s 级，2 bits/symbol；C+L 相干 DWDM（跨园区）：每跨约 120 km，加 ILA 可达 1,000 km+，每纤数十 Tb/s，DP-16QAM 8 bits/symbol [p5] 自报
  - Scale Across 容量约为 2020 年前端区域的 14 倍 [p6] 看图；Scale Across 收敛比 >8:1 [p6] 引用（ScaleAcross Explorer, Harvard/Meta 2026）
  - 分界：<150 km 为"Near Scale Across"（扩展园区，无 ILA，极高容量）；>150 km 为"Far Scale Across"（需 ILA）[p7] 自报
  - 20 Pb/s 用例：数百对光纤，每对纤 64×800G（C+L）[p9] 自报
  - RLS Hyper-Rail：一个紧凑机箱支持 16 对 C/L 波段光纤 [p9]；20 Pb/s 网络用传统线路系统需 22 个 hut，Hyper-Rail 只需 1 个 hut（128 rails/rack vs 4 rails/rack），密度提升 32 倍 [p10] 看图/自报
  - 现有逐波部署：每对纤 128×400G×2 或 64×800G×2 个可插拔 [p11] 自报
  - 51.2T C&L 全频谱转发器概念：4 个 8 通道业务模块，每模块 8×1.6T modem，客户侧 6.4T CPO/NPO [p12] 自报（概念）
  - 无损物理层目标：post-FEC BER 1e-24 [p15] 自报（提议）
- 提到的公司/客户/产品/标准：Ciena RLS、RLS Hyper-Rail、WaveLogic 相干可插拔；ZR+；UEC、MRC、MetaRoCE；Meta（ScaleAcross Explorer、FT-HSDP 10 万 GPU 论文被引）；OCP Open Cluster Designs for AI
- 首次/记录/SOTA 声明：Hyper-Rail 相对传统线路系统 32x 密度提升 [p10]（厂商自报）
- 推荐配图页：p10（22 hut vs 1 hut 的 Hyper-Rail 对比，直观）；p5（IMDD vs 相干对比表）；p6（14x 容量与 >8:1 收敛比）

### P140 Multi-planar-AI-Scale-Out-Fabrics
- 讲者/机构：Alan Judge（Distinguished Engineer, Head of Cloud & AI Architecture，Arista Networks）、Devang Patel（Network Architect，AMD）| 类型：技术分享
- 方向归属（主/次）：主 [Out：UEC/MRC、负载均衡、交换芯片、NIC、可插拔光模块] / 次 [Up：机柜级互连]
- 核心主张：
  1. 多平面 fabric = 只在客户端汇合的互不相交网络，客户端须把流量分摊到各 plane；带来冗余、成本和规模收益 [p4][p5]。
  2. 降低端口速率可提高交换机 radix，两层 Clos 规模随 radix 平方增长，因此两层就够、不需要三层 [p5]。
  3. 负载均衡、乱序、故障检测由 NIC 硬件/固件承担，开放方案为 OCP MRC（AI）和 UET（更广场景）[p8]。
- 关键数据：
  - 两层 Clos（1:1）最多 k²/2 客户端口；102.4T 器件 @800G radix 128 → 最大 8,192 客户端；@200G radix 512 → 131,072 [p5] 自报（计算）
  - AMD Helios（ORW）：18×1OU 计算托盘（1P:4GPU）、6×1OU 交换托盘，44OU×1200mm 宽×1289mm 深；scale-up 每 GPU 1.8 TB/s，UALoE 单跳多平面 [p10] 自报
  - 每 GPU 1 或 2 张 800G Vulcano NIC；1.6T OSFP cage 由两 GPU 共享；光模块 1×800G 或 1.6T-DR8 / 1.6T-2xDR4 [p11] 自报
  - Plane per NIC：6,912 GPU、96 Helios 机柜、每 GPU 2×800G、2 plane、4 rail、每 Rail POD 216 GPU（3 机柜）[p13]；图注 TH6 102.4T，DL 128p×800G，UL 128p×800G，T2 64 台，收敛比 0.84:1 [p13] 看图
  - Plane per SerDes：16,128 GPU、224 机柜、8 plane 各 200G、每 Rail POD 1,008 GPU（14 机柜），两层最大 129,024 GPU，需 GPU 与 T1 间 shuffler [p14]；图注 DL 512p×200G，UL 64p×1.6T，T2 32 台，收敛比 0.98:1 [p14] 看图
  - Shuffler 8×8，每输入 8×200G 打散到 8 个输出口，NIC 侧 MPO-16 或 Dual MPO-12 [p15] 自报
  - 验证集群：504 GPU、7 Helios 机柜，Tomahawk6 200G，Arista 7060XE7，8 plane×200G，1.6T-DR8，MRC，SRv6-uSID，128 或 256-ECMP [p16] 实验（未给性能结果）
- 提到的公司/客户/产品/标准：AMD Helios、Pensando Vulcano、Salina DPU、OCP ORW；Arista 7060XE7、EOS；Broadcom Tomahawk6；OCP MRC 1.0、UET（UE Spec 1.0.3）；SRv6-uSID；UALoE
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（8-plane 拓扑完整参数）；p7（多 NIC × 多 plane 组合示意）；p5（radix 与规模关系）

### P141 Network-Configurations-for-Optimal-AI-Fabrics-including-MRC-and-SRv6
- 讲者/机构：Arihant Jain（Sr. Product Manager，Arista Networks）、Mohammad Hanif（Senior Director，Broadcom）| 类型：技术分享
- 方向归属（主/次）：主 [Out：UEC/MRC、负载均衡、拥塞控制] / 次 [Across：SRv6]
- 核心主张：
  1. AI fabric 设计有两类技术：端点调度/非调度 fabric（NSF，低时延、高交换容量、布线简单）与交换机调度 fabric（DSF，NIC 无关、深缓冲）；拓扑选择两者通用 [p4]。
  2. 多平面 fabric 带来故障韧性、更好负载均衡、更低时延下的更大规模 [p5]。
  3. MRC 用结构化 EV 或 SRv6 uSID 精细定义路径，配合主动路径探测和 Trimming/CSIG 遥测做快速故障检测 [p7]-[p10]。
- 关键数据：
  - 每 QP 跟踪 128 条路径，路径映射到包内 EV；路径质量经 SACK 端到端回传；ECN 标记的路径在当前排列中被跳过 [p7] 自报
  - SRv6 uSID 示例：3 层网络，GPU 到远端完整路径用 6 个 uSID；T0 shortcut、T1 shortcut 用 00 填充 [p8] 自报
  - 主动探测：约每个 RTT 对随机一个 bad EV 发探测，收到响应即恢复为 good [p9] 自报
  - Packet Trimming：接收端对每个被裁剪包回 NACK，重传在 1 个 RTT 内发生（相对超时更快）[p10] 自报
  - CSIG 每包固定元数据：路径最小可用带宽、最小可用容量（%）、最大单跳时延；CSIG 正在 UEC Transport WG 标准化 [p10] 自报
- 提到的公司/客户/产品/标准：Arista、Broadcom；OCP MRC 1.0；SRv6 uN/uA、SRH；UEC TR WG、CSIG；OCP Open Cluster Designs for AI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（4 plane 多平面拓扑示意）；p8（SRv6 uSID 路径示例）

### P142 Next Generation Optically Integrated Platform Solution for AI Data Centers
- 讲者/机构：John Chiang（Director, Product Management，Celestica）| 类型：厂商技术分享
- 方向归属（主/次）：主 [Up：CPO/NPO] / 次 [Out：交换芯片、SONiC] [运维/可靠性/遥测]
- 核心主张：
  1. 今天 scale-out 用可插拔光模块、scale-up 用 DAC/AEC 铜缆；明天两者都走向 CPO（compute 侧 CPO/NPO）[p4][p6]。
  2. CPO 是使能技术但不是完整方案，价值来自光、网络软件、标准、遥测和运维的整合；质量与可靠性顾虑"正在被证伪" [p5][p6]。
  3. 需要跨 scale-out/scale-up 共用的遥测与运维模型 [p8]。
- 关键数据：
  - 集群扩展到 500K/1M+ 加速器 [p3] 自报（趋势表述）
  - CPO 关键遥测指标：温度、光功率、外置激光器性能、pre-FEC 与 post-FEC BER [p8] 自报
  - 无其它量化数据
- 提到的公司/客户/产品/标准：Celestica DS6005（基于 Broadcom Tomahawk 6 Davisson CPO，计划贡献给 OCP）；OCP Open Cluster Designs for AI、Open Silicon Photonics for AI Systems、SAI、ESUN、Enhanced Telemetry Optics；SONiC；UEC；OIF CMIS for CPO 与 ELSFP
- 首次/记录/SOTA 声明：无（仅声明计划将 DS6005 设计贡献给 OCP [p9]）
- 推荐配图页：p6（Today vs Tomorrow：scale-out/scale-up 走向 CPO 的对照）；p9（DS6005 平台）

### P143 Node-to-Rack Efficiency for Real-World AI Inference Arm & FuriosaAI for Scalable Open Infrastructure
- 讲者/机构：Satadal Bhattacharjee（Global Head of Cloud and AI Infra Silicon，Arm）、Jihoon Yoon（Product Manager，FuriosaAI）| 类型：厂商技术分享
- 方向归属（主/次）：主 [推理/算力/经济性] / 次 [底座-机架/机械]
- 核心主张：
  1. Agentic 推理是流水线而非一次模型调用，CPU 上的工具调用、编排、检索与加速器阶段同样决定端到端时延和成本 [p15]。
  2. 机柜功率固定，系统级 tokens/W（CPU+加速器）决定一个机柜能提供多少推理 [p11]。
  3. 高效 CPU + 高效 PCIe 加速器的开放风冷节点可放进现有 30 kW 机柜 [p15]。
- 关键数据：
  - Agent token 用量预计到 2030 年增长 24 倍；2027 年企业 agent 月 token 13.6 quadrillion [p2] 引用（未注明来源）
  - Arm AGI CPU：最多 136 Neoverse V3 核，3nm，300 W TDP，96 lane PCIe Gen6，CXL 3.0，DDR5-8800，每核 6GB/s 内存带宽，<100ns 内存时延，每核 2MB L2，最高 3.7GHz [p6] 自报；双 SoC 272 核、24×DDR5-8800、128×PCIe Gen6 [p7]
  - FuriosaAI RNGD 卡：512 TFLOPS FP8，48 GB HBM3，1.5 TB/s，180 W 被动散热，PCIe Gen5；服务器 8 卡 4 PFLOPS、3 kW、4U；机柜 8 服务器 32 PFLOPS、3.07 TB HBM3、<30 kW 风冷 [p10] 自报
  - Agent 步骤约 60% 在 CPU 上；这些步骤 Arm AGI CPU 每可用线程性能为 x86 基线（AMD Turin SMT-off）的 1.2–1.4 倍 [p12] 自报；分项约 1.4（数据检索）/1.2（Vector-DB）/1.4（KV-cache）[p12] 看图
  - RNGD Qwen3-32B FP8、4 卡、1K/1K tokens：每 kW 用户数 63.0@20 tok/s、31.6@30 tok/s、15.3@40 tok/s；30 tok/s 时 4 卡约 1,950 tok/s，TTFT 0.35 s；x86 主机，尚无 Arm 主机结果 [p12] 实验
  - 30 kW ORv3 机柜：2,176 核（16×136）、32 PFLOPS FP8（64×512 TFLOPS）、3.07 TB HBM3，8 节点各约 2.5–3 kW + 交换 [p14] 自报（规划）
- 提到的公司/客户/产品/标准：Arm AGI CPU、Neoverse V3；FuriosaAI RNGD；Supermicro ARS-522GP-NR；OCP ORv3、OCP NIC 3.0；vLLM、llm-d、NIXL、Mooncake、LMCache；部署伙伴 Cerebras、Cloudflare、F5、Meta、OpenAI、Oracle、SAP、SK telecom、Verda、火山引擎 [p5] 看图
- 首次/记录/SOTA 声明："World's most efficient agentic CPU" [p5]（厂商自称，无数据支撑）
- 推荐配图页：p12（CPU/加速器分工 + users/kW 随 SLO 变化柱图）；p14（30 kW ORv3 机柜参数）

### P144 Powering-AI-at-Scale-Inside-the-UALink-Ecosystem
- 讲者/机构：Kurtis Bowman（UALink Consortium Board Chair，AMD）、Helia Naeimi（Astera Labs）、Josh Collier（Intel）、Matt Holdrege（Microchip）、Priyank Shukla（UALink Board Member，Synopsys）| 类型：面板
- 方向归属（主/次）：主 [Up：UALink] / 次 [In：chiplet]
- 核心主张：
  1. UALink 是面向 AI scale-up 的开放协议，"Any CPU / Any Accelerator / Any Switch / Any Company" [p5]。
  2. 定义加速器与交换机之间的低时延、高带宽互连，用于 AI 计算 pod 内的解耦架构 [p6]。
  3. 规范路线图覆盖协议、管理、合规互通与 chiplet [p8]。
- 关键数据（规范路线图 [p8]，自报）：
  - UALink 200G 1.0：2025 年 4 月；UALink 128G 1.0 与 UALink 1.1：2025 年 3Q
  - 2026 年 4 月：UALink 2.0（增加 Collectives）、UALink Chiplet 1.0、UALink Mgmt 1.0、UALink 2.0 ECR/Errata
  - UALink Compliance 1.0：2026 年 4Q
  - 2027：UALink 3.0（新特性、提高带宽）、Mgmt 2.0、Compliance 2.0、Chiplet 2.0
  - 面板讨论内容未在讲稿中呈现（p6、p7 仅为讨论标题）
- 提到的公司/客户/产品/标准：UALink Consortium；AMD、Astera Labs、Intel、Microchip、Synopsys
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（UALink 2025–2027 规范路线图）

### P145 SUE-T-An-Ethernet-transport-for-Scale-Up-Networking
- 讲者/机构：Tom Emmons（Software Engineer，Arista Networks）、Karen Schramm（Vice President，Broadcom）| 类型：标准进展
- 方向归属（主/次）：主 [Up：SUE-T/ESUN] / 次 [Out：UEC]
- 核心主张：
  1. 过去 XPU scale-up 传输用私有方案，开放方案达不到效率与时延要求；scale-up 与 scale-out 正在融合，标准协议价值上升 [p2]。
  2. SUE-T 规定一个网络接口，组合 UET 语义头 + UET RODL 可靠有序传输 + OCP ESUN 紧凑 L2/L3 头，面向线效率、低时延和面积效率 [p2][p4][p5]。
- 关键数据：
  - 目标范围：单跳（可扩展多跳）；最多 4k XPU；Load/Store/Atomics 小事务；共享内存；E2E RTT <2 µs；2+ 流量类 [p3] 自报
  - SES 语义头 12B，地址压缩后 8B；单事务最大 16K-1 字节；支持多事务打包 [p6] 自报
  - 线效率：256B 载荷 85%，1KB 载荷 96% [p7] 自报
  - 面积（5nm 估计）：仅 LLR <2 mm²；重传（6 µs）<3 mm² [p7] 自报（估算）
  - ESUN 支持 UDP 封装，UET 目的端口 4793；无损链路用 CBFC、LLR [p9] 自报
- 提到的公司/客户/产品/标准：OCP ESUN、OCP SUE-T WG、UET（RODL、SES）、UEC LLR、CBFC、ULN；AXI 接口
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（SUE-T 目标范围表）；p5（SUE-T 协议栈结构）；p7（线效率与面积数据）

### P146 Scale-Across-To-Go-Forward-or-To-Go-Backwards-That-is-the-question
- 讲者/机构：Jai Kumar（Distinguished Engineer，Broadcom）、Tom Emmons（Software Engineer，Arista Networks）| 类型：技术分享
- 方向归属（主/次）：主 [Across：长RTT拥塞控制] / 次 [Out：拥塞控制]
- 核心主张：
  1. 距离是根本问题：Trimming、CSIG、ECN 都需要一个 RTT 才能让发送端反应，长 RTT 使控制环不稳，且 AI flow 可能短于 1 个 RTT [p5]。
  2. Scale Across 有本地和远端两种 RTT 特征，incast 不仅发生在末跳也发生在 DCI 链路，路径故障目前只能靠超时 [p3][p5]。
  3. 提出 Back-To-Sender（BTS）：由拥塞点交换机直接向发送端回送带元数据的截断包通知 [p6][p7]。
- 关键数据：
  - 三域定义：Scale Up <30 m（单跳、DAC）；Scale Out >1K GPU（多平面、2/3 层 leaf-spine）；Scale Across 100+ km（路由城域/区域 WAN + DCI）[p2] 自报
  - 通知时延：BTS 约 10 µs，端到端约 1000 µs（对数坐标）[p6] 看图
  - BTS 设计目标：控制流量带宽占用约 1% 或更少；不改传输头和转发头，交换机不维护流状态 [p7] 自报
- 提到的公司/客户/产品/标准：Broadcom、Arista；OCP SAI（PR #2349）；UEC BTS WG Adhoc；Trimming、CSIG、ECN、PFC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（BTS vs 端到端通知时延对比）；p3（跨 DC 参考网络模型）

### P147 Scale-across-Networking-Panel-discussion-on-routing-and-transport-equipment-implications
- 讲者/机构：Tad Hofmeister（Google Cloud）、Yawei Yin（Microsoft Azure，Principal Network Developer）、Jeff Rahn（Meta Backbone & Edge Networks）、Xiguang (Henry) Wu（Broadcom，Core Switch Group 产品管理）、Vijay Vusirikala（Arista Networks，主持）| 类型：面板（含四段分讲）
- 方向归属（主/次）：主 [Across：DCI、ZR/相干、深缓冲、长RTT拥塞控制] / 次 [Out：OCS、可插拔光模块/LPO/LRO] [Up：CPO/NPO]
- 核心主张：
  1. Google：单楼电力/空间限制 xPU 数量，scale-out fabric（Virgo）限定在单楼，跨楼训练需要楼间 scale-out；多楼时用 OCS 替代电交换园区 spine，楼间光模块用 1.6T Coherent-Lite（O-band，低时延 FEC，被动复用）[p5]-[p11]（设计概念，非承诺）。
  2. Meta：园区从 <3km（短距光模块）扩到 <10km（LR），再到 10km+ 借 800ZR+ 与 DWDM 达到 GW 级集群；要求标准化互通接口、开放线路系统、400ZR⇄800ZR⇄1600ZR 代际互通、C+L 满填 [p22]-[p34]。
  3. Microsoft：多站点分布式训练与推理是架构必然；光模块 SKU 应收敛（"Less is more"），把需求限定在可量产变体 [p40][p44]。
  4. Broadcom：BDP 随 RTT 暴涨，交换机缓冲需 ≥1.5×BDP 才能使 FCT 接近理想且零重传，片上浅缓冲做不到 [p46][p49][p51]。
- 关键数据：
  - Google：楼间带宽数十到数百 Pbps（10,000–100,000 Tbps），对应 2×(6,250–62,500) 个 1.6T OSFP；平均光纤距离 <2km [p6] 自报
  - Google：1.6T-CL 相对 IM-DD 频谱效率 4 倍；需 2nm CMOS 低功耗 DSP、低时延 FEC、低损低 Vpi 调制器（TFLN、Si-organic）；对应 OIF 1.6T-CL 项目 [p10] 自报
  - Meta：DC-DC 同步流量 2023 年后陡增，GW 级集群 DC-DC 流量在 2026（预测）首次出现且高于同步流量 [p21] 看图（无纵轴刻度，仅相对比例）
  - Meta：楼 1–4 <3km，楼 5–6 <10km，楼 N 以后 10km+ [p25] 自报
  - Microsoft：传统单 DC 电力 50–300 MW；下一代训练集群需 1 到 5+ GW；新站点电网接入周期 3–7 年 [p40] 自报
  - Microsoft 能效表 [p41] 自报：传统相干转发器 >1000 pJ/bit（>1000km）；DCI IP over DWDM（IMDD PAM4、400ZR）45–55 pJ/bit（10–120km）；FRO 18–25 pJ/bit（500m–10km）；LRO 10–18 pJ/bit（500m–2km）；LPO 7–10 pJ/bit（500m+）；NPO 5–8 pJ/bit（500m+）；CPO 1–5 pJ/bit（10–30m+）
  - Microsoft：OSP 光纤市场可用性约 97.7% [p42] 自报
  - Microsoft 引用：HW FLOPS 20 年 60000 倍（3.0x/2年）、DRAM 带宽 100 倍（1.6x/2年）、互连带宽 30 倍（1.4x/2年）[p39] 看图/引用（Gholami et al.）；TFLOPS 3x/2yr vs HBM 带宽 <2x/2yr [p39] 看图/引用（Micron, Hot Chips 2026）
  - Microsoft 距离分档：前端 <2km，Scale Out <1km，Scale Up <50m，Scale In <1m [p43] 看图
  - Broadcom：800GE 在途数据 5km/5MB、100km/100MB、1000km/1GB [p46] 自报
  - Broadcom 仿真（10km、NSCC，50/150/500MB flow）：缓冲 ≥1.5×BDP 时 FCT 开销约 3–8%、重传 0%；0.1×BDP 时 FCT 开销 20.6%/24.9%/31.5%、重传 23.4%/31.2%/55.1%（500MB/150MB/50MB）[p49] 看图/仿真；阈值在 10/30/100km、NSCC 与 RCCC 下均成立 [p49][p51] 仿真
  - Broadcom：100T 交换机 1.5×BDP 所需缓冲 10km ~1.9GB、30km ~5.6GB、100km ~18.8GB [p51] 仿真/计算
  - Broadcom：保护倒换 µs 级反应；数万 ECMP 组、每组数千成员；百万级路由 [p50] 自报
- 提到的公司/客户/产品/标准：Google Virgo、New Albany 园区、OCS；OIF 1.6T-CL；Meta Prometheus 集群、400ZR/800ZR/1600ZR、800ZR+；Microsoft Azure；Broadcom HBM 外挂缓冲、NSCC、RCCC、MACsec/IPSec/TunnelSec；PMD 档位 SR/DR/FR/LR/CL/ZR/ZR+，形态 OSFP、XPO、USFP（proposed）、NPO [p44] 看图
- 首次/记录/SOTA 声明：无
- 推荐配图页：p49（缓冲深度 vs FCT/重传率两张曲线，结论清楚）；p41（各类光互连 pJ/bit 对照表）；p10（1.6T-CL vs IM-DD 演进）；p21（Meta 网络流量增长柱图）

### P148 Scaling AI Inference with Arm AGI CPU, Rebellions RebelCard, and OCP ORv3 Rack Design
- 讲者/机构：Dilip Ramachandran（Sr. Director of Marketing，Arm）、Jennifer Glore（EVP Product Management，Rebellions）| 类型：厂商技术分享
- 方向归属（主/次）：主 [推理/算力/经济性] / 次 [底座-机架/机械]
- 核心主张：
  1. Agentic AI 中大比例工作在 CPU 上，CPU 做编排层、NPU 做模型执行 [p7][p8]。
  2. Arm AGI CPU + Rebel100 NPU 组成 RebelServer，从服务器扩展到 RebelRack/RebelPOD [p9][p10]。
- 关键数据：
  - 客服 agent 用例 CPU 60% / 加速器 40%（Arm PoC 分析）[p8] 自报
  - 每机柜性能 >2 倍于 AMD Turin：Arm 30×1U 服务器 8160 核 vs Turin 17×2U 服务器 4352 核，36kW 机柜，基于估算 [p8] 看图/预测
  - RebelServer TPS/W 约为 AMD 服务器 2 倍 [p9] 看图（未给测试条件）
  - RebelRack：4 台 RebelServer、32 张 RebelCard；1–7 NPU 机柜（4–28 节点）；RebelPOD 8+ 机柜、32+ 节点 [p10] 自报
  - Agent token 到 2030 增长 24 倍、2027 企业 agent 13.6 quadrillion tokens/月 [p2] 引用（未注明来源，与 P143 同页）
- 提到的公司/客户/产品/标准：Arm AGI CPU；Rebellions Rebel100、RebelCard、RebelServer、RBLN SDK、vllm-rbln、torch-rbln；AMD Turin；OCP ORv3；部署伙伴同 P143 [p5] 看图
- 首次/记录/SOTA 声明："World's most efficient agentic CPU" [p5]（厂商自称）
- 推荐配图页：p8（CPU/加速器分工 + 每机柜 >2x 对比）

### P149 Scaling Purpose-Built AI Models via OCP Aligned Distributed Inference Fabrics
- 讲者/机构：Art Fewell（Hedgehog）、Arun Solleti（Celestica）| 类型：技术分享
- 方向归属（主/次）：主 [Out：RoCE、负载均衡、SONiC] / 次 [推理/算力/经济性]
- 核心主张：
  1. 一旦张量或 KV 状态跨主机，fabric 行为就成为服务行为；分布式推理把网络方差变成 token 完成时间方差（含尾部）[p2][p5]。
  2. 四种部署形态（Standalone/Replicated/Distributed/Disaggregated）不是成熟度等级；应选择满足 SLO 的最简形态，分布式不是默认 [p3][p4]。
  3. 提议 OCP Distributed Inference Fabric Profile：按 fabric 角色标准化策略模型与验证方法，而不是统一的队列配置 [p8][p13]。
- 关键数据：
  - 物理基础：机柜级液冷加速器域，800G/1.6T 级 scale-out 接口，leaf-spine 以太网，SONiC [p6] 自报
  - 四类 fabric 角色：scale-out/推理（时延抖动关键，RDMA、PFC+ECN、有界队列）、存储/模型、前端/AI 服务、管理/控制 [p8] 自报
  - p9 的 ECMP 路径分布图明确标注为"示意，非基准结果" [p9]
  - 无实测数据；向社区征集参考拓扑与实测 p99 行为 [p13]
- 提到的公司/客户/产品/标准：Hedgehog、Celestica；SONiC、Open Network Fabric；RoCE、ECMP、PFC、ECN；llm 服务中的 prefill/decode 解耦
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（四种推理部署形态及其 fabric 影响）；p8（按 fabric 角色的参考 profile）

### P150 Secure Multi-Tenancy for Open AI Clusters（精简）
- 讲者/机构：Manish Vachharajani（CTO，Hedgehog）、Art Fewell（Technical Marketing Engineer，Hedgehog）| 类型：技术分享
- 方向归属（主/次）：主 [安全] / 次 [Out：SONiC]
- 核心主张：
  1. AI 性能要求（GPU-direct、RoCE）削弱了基于主机的隔离（VM 的 IOMMU/ACS 会阻碍 GPU-direct，DPU 在后端 GPU 规模上难做），隔离边界应移到物理 fabric [p4][p5]。
  2. 用 BGP/EVPN + VXLAN + 每租户 VRF/L3VNI 实现 VPC 语义，Kubernetes CRD 声明式控制；AI 应生成意图而不是交换机配置 [p5][p8][p11][p12]。
- 关键数据：
  - 示例：VRF A·VNI 1001、VRF B·VNI 1002 [p5] 自报（示例）
  - 自然语言直接生成约 1,000 行交换机配置不可审查；正确做法是生成小的 VPC manifest 由人审批 [p12] 自报
  - 无性能数据
- 提到的公司/客户/产品/标准：Hedgehog Fabric Controller；SONiC；BGP/EVPN、VXLAN、L3VNI；Kubernetes CRD；GitOps
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（主机侧隔离方案在 AI 场景失效的对照表）

### P151 Tahan-An-Open-Ethernet-Based-Scale-Up-Switch-for-Meta-s-MTIA-Accelerators
- 讲者/机构：Vimal Vasudevan（Technical Program Manager，Meta）、Ashutosh Grewal（Software Engineer，Meta）| 类型：技术分享（自研系统）
- 方向归属（主/次）：主 [Up：ESUN、铜缆/背板、机柜级互连] / 次 [Out：交换芯片]
- 核心主张：
  1. 私有、厂商锁定的 scale-up 方案不适合 Meta 的 MTIA 开放平台，因此自研基于以太网的 scale-up 交换机 Tahan [p3]-[p5]。
  2. 单跳、非阻塞、全部用商用以太网芯片；scale-out 与 scale-up 共用 FBOSS，一个 NOS、一套运维模型 [p10][p12]。
  3. 下一代用 Tomahawk6 支持 72 加速器；推动 ESUN（OCP）与 LLR/CBFC（UEC）开放标准 [p14][p15]。
- 关键数据：
  - Tahan：1OU，液/风混合冷却，Broadcom Tomahawk5 51.2 Tbps；PHY-less + flyover 线缆；32×800GE 朝背板、前面板 32×OSFP 800GE [p7][p8] 自报；前面板 OSFP 为 Reserved，另 1×QSFP 接 ToR；管理 CPU 为 Intel Xeon 微服务器（CentOS + FBOSS）[p6] 看图
  - 部署于 ORv3-HPRv1 机柜，面向 MTIA300 训练加速器 [p5][p9] 自报
  - 带宽：16 加速器、4 台 Tahan，每加速器 8×800GbE（每台交换机 2×800G），每加速器每方向 6.4 Tbps，非阻塞 [p10] 自报
  - 时延：始终 1 跳；每跳 <1 µs（store-and-forward）；cut-through 可再降 25%（探索中）；1.5 m twinax 约 7 ns，线缆约占 fabric 路径 1.5%；不含 NIC、PCIe、主机软件 [p11] 自报/看图
  - 复用 scale-out 功能：IPv6 数据面、PFC 无损类、ECMP、DLB；关闭 BGP 路由 [p13] 自报
  - 下一代：Tomahawk6 102.4 Tbps，8 台交换机、72 加速器，每加速器 24×400G（每台交换机 3×400G），每方向 9.6 Tbps，为 Tahan 的 1.5 倍；每台交换机 216×400G [p14] 自报
  - ESUN 把 IPv6+UDP 48 B 头压到约 4 B；ESUN OCP base spec Rev 1.0 已批准（与 Microsoft 共同推动）；LLR 在一跳链路 RTT 内重放；CBFC 比 PFC 用更少缓冲 [p15][p16] 自报
- 提到的公司/客户/产品/标准：Meta MTIA300、FBOSS、Tahan；Broadcom Tomahawk5（BCM78900）、Tomahawk6；OCP ORv3-HPRv1；OCP ESUN；UEC LLR、CBFC；Microsoft
- 首次/记录/SOTA 声明：Tahan 完整硬件规格将贡献给 OCP [p16]
- 推荐配图页：p10（16 加速器 × 4 交换机带宽拓扑）；p11（单跳时延预算）；p14（下一代 72 加速器拓扑）

### P152 Test-Methodology-and-Practice-for-Multi-Accelerator-Copper-Scaleup-Domain-Interconnect-and-Communication-Library
- 讲者/机构：Yao Rong（Systems Engineer, AI Systems，Meta）、Karthik Ganesan（AI/HPC System Performance Engineer，Meta）| 类型：技术分享
- 方向归属（主/次）：主 [Up：铜缆/背板] / 次 [运维/可靠性/遥测]
- 核心主张：
  1. 铜缆 scale-up 域的链路质量是统计问题而非调试问题，blind-mate 接插件本身就是信号路径，无法逐链路维修 [p2]。
  2. PRBS 必要但不充分；运行时 PI 与串扰仍会引入误码，需要流量级验证和故障注入 [p5][p6]。
  3. 一条边缘链路比一条坏链路更糟：坏链路会被 fabric 放弃 plane，边缘链路保持活跃并因 Go-Back-N 成为 straggler；集合通信是最终验收测试 [p7]。呼吁建立厂商中立的铜缆 scale-up 一致性测试套件 [p8]。
- 关键数据：
  - 典型系统 72 加速器、单交换跳；每机柜数千连接，即使 99.9% 良率也有约 10 条坏链路 [p2] 自报
  - 每阶段（POC→EVT→DVT→PVT）给出口数字和逐 lane 向量；pre-FEC 和 post-FEC 都要看，FEC 直方图比 BER 更能反映余量 [p3] 自报
  - AllReduce 总线带宽（% 线速）：健康约 93%，放弃 plane 后约 86%，边缘 plane 仍活跃时约 55% [p7] 看图
  - 案例：PRBS 干净但流量退化，全网格两两热图显示一颗 GPU 在整个 plane 上退化，拖慢域内所有 GPU；放弃该 plane 后带宽恢复 [p11]（症状/根因细节标注"待补充"）
- 提到的公司/客户/产品/标准：Meta；PRBS、FEC、Go-Back-N；CCL、AllReduce
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（AllReduce 带宽三条曲线 + 检测-隔离-放弃-重分配流程）

### P155 Unified Full-Stack Telemetry for AI Systems- From Silicon to Cluster
- 讲者/机构：Karthik Raman、Janusz Jurski、David Box，Intel Corporation | 类型：标准进展（提案）
- 方向归属（主/次）：主 [运维/可靠性/遥测] / 次 无
- 核心主张：
  1. 各层遥测采集已解决（PLDM、Redfish、MCTP、OpenTelemetry），但跨层关联仍靠人工；缺三项共同约定：身份、时间、语义 [p3][p4][p7]。
  2. 提议一个"规范化契约"：规范组件 ID、时间戳来源、公开的指标定义，作为现有标准之间的映射，不替代任何标准 [p8][p11]。
- 关键数据：
  - 六个 scope（Silicon→Firmware→Host/OS→Node→Rack→Cluster）、五次交接 [p6] 看图
  - 覆盖矩阵：传输与数据模型大体由 Redfish/PLDM/UE/调度器 API 覆盖；指标语义仅部分覆盖；Silicon/加速器指标语义"not covered（7 metrics, early draft）"；跨层身份与统一时间基在所有层均"not covered" [p10] 看图
  - 示例根因链（说明性，非实测）：机柜热偏移 → 单设备降频 → 一个 straggler rank → 整个 collective 停滞 [p9] 看图
  - 明确不宣布产品或设施，仅规范工作 [p11]
- 提到的公司/客户/产品/标准：Intel；DMTF Redfish DSP0266、PLDM DSP0248/DSP0242、OCP Redfish DSP2049；OpenTelemetry（硬件与 GPU 语义约定，GPU 为 Development 状态）；Ultra Ethernet v1.0.3；OCP Hardware Management、Scalable Cloud Infrastructure Management
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（标准覆盖矩阵，最后一列全空）；p9（跨层根因示例）
