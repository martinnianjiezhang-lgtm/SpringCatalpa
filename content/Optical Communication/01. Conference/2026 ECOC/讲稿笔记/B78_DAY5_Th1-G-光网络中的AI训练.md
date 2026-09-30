---
title: "B78 · DAY5 · Th1-G-光网络中的AI训练"
tags:
  - ECOC2026
  - DAY5
---

### 0924-Th1-G1-Corning-光纤时延对跨地域多数据中心AI训练计算通信重叠的影响建模.pdf
- 讲者/机构：Ioannis Papavasileiou 等（Sairam Prabhakar, Indu Kant Deo, Sergejs Makovejs）/ Corning Incorporated | 题目：Modeling the Impact of Fiber Latency on Compute-Communication Overlap in Geo-Distributed Multi-Datacenter AI Training | 类型：学术论文（Th1-G1）
- 方向归属（主/次）：主 2（Scale-across，跨地域多DC训练）；次 1（AI光网络）
- 核心主张：
  1. 光纤传播时延（D/v）与带宽无关，NIC 升到 400G–1.6T 后串行化项 M/B 变小，跨DC距离下光纤时延成为数据并行训练计算-通信重叠的主导因素。
  2. 重叠效率 η_overlap 随DC间距单调下降，10 km 以内近似为1；空芯光纤（HCF）在各距离都优于 SMF。
  3. HCF 的收益在“带宽受限→时延受限”的转折距离处最大；更快的GPU（H100）受时延惩罚更大。
- 关键数据：
  - 传播时延：SMF = 5.0 µs/km；HCF 约快1.5倍，传播时延约低33%（节省 1.7 µs/km）[p5]
  - 仿真：ASTRA-sim 离散事件仿真；数据并行 GPT-3 预训练；GPT-3 13B/175B；256/2048/8192 GPU；A100(312 TFLOPS)/H100(989 TFLOPS)；DC间距 0.3–1000 km；DC间带宽 100 GB/s（256 GPU 另测 200 GB/s）；DC内 600 GB/s（6×100），DC内时延 1 µs；假设交换时延可忽略、网络无拥塞 [p6][p7]
  - 10 km 以下 η≈1；H100 的 η 在约 10–30 km 起下降，A100 约在 100 km 以上才下降；1000 km 处各曲线 η 降至约0.05–0.3（读图估计）[p8]
  - Δη = η_HCF − η_SMF 在中间距离达峰：13B 模型 A100 峰值约0.24（约100 km），H100 约0.17（约30 km）；175B 模型 H100 峰值约0.22，A100 约0.19；讲者结论“最多 +25% 重叠；同等时延下 HCF 可达距离远约50%”[p9]
  - 训练时间相对 0.3 km 基线（GPT-3 175B，8192 GPU）：1000 km SMF 上 H100 约 26×、A100 约 4×；HCF 将 H100 惩罚由约26×降至约17×[p10]
  - 大模型更耐距离（每层算得多、更多时间掩盖通信）[p11]
- 提到的公司/客户/产品/标准：Corning、NVIDIA A100/H100、GPT-3、DeepSeek-V3（671B总/37B激活）、Gartner（2027年40% AI数据中心受电力限制）、ASTRA-sim、SMF、HCF
- 与业界对比或记录声明（SOTA/首次/record）：无SOTA声明；给出“HCF 最多 +25% 重叠、可达距离约+50%”的仿真结论 [p9]
- 推荐配图页：p10（训练时间倍数 vs 距离，H100/A100、SMF/HCF 对比，含26×→17×）；p8（η_overlap vs 距离曲线）；p9（HCF 增益峰值）

### 0924-Th1-G2-AIST-基于功能块解耦的网络拓扑精确动态表示支撑数字孪生统一参考.pdf
- 讲者/机构：Kiyo Ishii, Kazuya Kunita, Hiroyuki Matsuura, Shu Namiki, Kenji Mizutani / 日本产综研 AIST | 题目：Accurate and Dynamic Network Topology Representation based on Functional Block-based Disaggregation for a Common Reference of Network Digital Twins | 类型：学术论文（Th1-G2）
- 方向归属（主/次）：主 1（AI光网络/数字孪生）
- 核心主张：
  1. 提出基于功能块解耦（FBD）模型、部署于关系数据库（PostgreSQL）的拓扑与资源管理平台，作为光网络数字孪生的统一公共参照数据平台。
  2. 提供元器件级拓扑表示和端口级路径预约管理，支持实时并发查询与增量更新。
  3. 在现网试验床上完成验证。
- 关键数据：
  - 试验床：站点 A/B/C 为终端站共17个转发器，站点 R 为 ROADM（3×3 WXC）；B–R 之间为现网光纤（图中标注约27 km 现场光纤段，A–R、C–R 用 30 km/40 km 线轴光纤）；使用白盒/解耦设备；FBD_DB 跑在普通笔记本上 [p7][p11]
  - 拓扑更新：讲稿总结页 15 s（日志流程：识别更新、加载 KiCad 网表、增量更新）[p10][p18]
  - 路径识别：6类故障场景共18条路径（节点端口/节点内端口/加落端口/WSS/EDFA/转发器故障）；SQL 查询亚秒级，10次平均约 280–480 ms（读图，场景4最高约480 ms）[p11]
  - 路径重配置：13条路径删除 51 s；13条路径重新建立 6 min [p12][p18]
  - 结论页汇总：路径识别 <1 s | 拓扑更新 15 s | 13路径删除 51 s | 13路径建立 6 min [p18]
  - 后续工作：整合其他数字孪生模块；研究如何表示耗时的物理空间状态转换 [p18]
- 提到的公司/客户/产品/标准：PostgreSQL、KiCad、ILP/GLPK PathFinder、NRM、WSS/EDFA/WXC、NEDO JPNP16007、JST CRONOS JPMJCS25N3；相关论文 K. Ishii, JLT vol.37 no.21, 2019；PSC2026 TuP1-A1.5
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p18（四项时间指标汇总）；p11（6类故障场景与查询耗时柱状图）

### 0924-Th1-G3-北邮-A2A协议增强的多智能体协同实现自治光网络服务开通.pdf
- 讲者/机构：Zihao Cui, Yuchen Song, Shengnan Li, Yue Pang, Min Zhang, Danshi Wang（通讯）/ 北京邮电大学信息光子学与光通信全国重点实验室；中国电信云网操作系统研发中心 | 题目：Agent-to-Agent Protocol Enhanced Multi-Agent Coordination for Autonomous Service Provisioning in Agentic Optical Networks | 类型：学术论文（Th1-G3）
- 方向归属（主/次）：主 1（AI光网络，Agentic）
- 核心主张：
  1. 异构光网络智能体缺乏标准化通信，需要发现、跨框架互通、任务跟踪和结构化结果交接的公共层。
  2. 采用 Google 提出的开放 A2A 协议（Agent Card 发现、Task ID/生命周期状态、Artifact 结构化产出）构建 Host/Strategy/DT/North/South 多智能体系统。
  3. A2A 提供标准交互层，把异构光网络智能体连成统一的自治业务开通工作流。
- 关键数据：
  - 验证场景：德国光网络拓扑，10对随机选取的源宿节点做业务开通；示例柏林–法兰克福（Task 2）：400G 业务、40波，工作路径柏林→莱比锡→法兰克福，保护路径柏林→汉诺威→法兰克福；DT Agent 仿真返回可行（工作路径 GSNR 18.11/OSNR 19.31，保护路径 GSNR 17.47/OSNR 18.98），North Agent 下发 5 个设备（1 光源 + 4 EDFA）配置（看图核实）[p12]
  - 10/10 任务完成；每任务 A2A 开销 58–120 ms（T1 3次调用/58 ms，T2 4次/120 ms，T7 4次/113 ms 等）；Strategy Agent 耗时约 23.8–49.9 s，DT Agent 约 2.1–5.2 s，North/South 配置下发 1–2 ms [p13]
  - 跨框架：Host 固定为 ADK；三种远端配置（全 ADK / 全 LangGraph / 混合）各10任务；均 100% 任务完成率和 100% 路由准确率；A2A 路由时间均值 0.070（混合）/0.074（全LangGraph）/0.078 s（全ADK），最大 0.120 s（全ADK）；Host 到 Agent 交互平均 16.5–23.6 ms；总耗时主要由推理和工具执行决定，协议路由开销可忽略 [p14]
  - 参考：Y. Zhang 等 ECOC 2025 首次 L4 自治现网试验；IEEE ComMag 2026 分层多智能体零接触框架 [p4]
- 提到的公司/客户/产品/标准：Google A2A 协议、Google ADK（Agent Development Kit）、LangGraph、JSON-RPC/HTTP、中国电信
- 与业界对比或记录声明（SOTA/首次/record）：无首次声明；引用其团队 ECOC 2025 的 L4 自治现网试验 [p4]
- 推荐配图页：p13（10任务A2A执行轨迹与开销）；p14（跨框架路由时间对比）；p3（Agentic 光网络架构）

### 0924-Th1-G4-德国联邦国防军大学-可编程数据面与SDN实现任意业务承载于DWDM.pdf
- 讲者/机构：Cristian Bermudez Serna, Philip Diederich（TUM）, Carmen Mas-Machuca / 慕尼黑联邦国防军大学（Universität der Bundeswehr München）Chair of Communication Networks | 题目：Anything over Dense Wavelength Division Multiplexing with Programmable Data Planes and Software Defined Networking | 类型：学术论文（Th1-G4；SUSTAINET）
- 方向归属（主/次）：主 1（长途/核心光网络架构）；次 3（P4/DCO 可编程交换）
- 核心主张：
  1. 可编程数据面（PDP，P4，Intel Tofino）交换机配合 DCO 可插拔模块可实现 XoDWDM（任意协议 L1–L4 直接承载于 DWDM）。
  2. 包转发时延：IPoDWDM（路由器）> XoDWDM > ROADM（光开关）。
  3. XoDWDM 具备 P4 网络可编程性和原生 SDN 管理。
- 关键数据：
  - 三种光线路系统对比：ROADM 透明、L1、reach 1000 km+；IPoDWDM 路由器+DCO、不透明、L3、reach 100 km+；XoDWDM PDP 交换机+DCO、不透明、L1–L4 任意协议、reach 100 km+ [p2]
  - Tofino 1：交换 6.4 Tbps、32×QSFP28、DCO 最高 100 Gbps、reach 最高 80 km；Tofino 2：交换 12.8 Tbps、32×QSFP-DD、DCO 最高 400 Gbps、reach 最高 400 km（看图核实，Universität der Bundeswehr München，cristian.bermudez@unibw.de）[p4]
  - DCO：100G QSFP28 ZR 80 km，功耗最高 5.5 W；Tofino 1 QSFP28 口最高 6 W [p5]
  - 测试方法：100万个唯一包，10k pps，Tofino 出/入口时间戳（T1、T2）；被测设备：Polatis Series 6000 光开关（ROADM-OS）、Edgecore DCS204 L2-3 交换机（IPoDWDM 路由器）、Edgecore DCS801 Tofino 1 交换机（XoDWDM）[p11][p13]
  - 包转发时延：Tofino 493 ns（L1）约为光开关 48 ns 的10倍 [p14]；Tofino 513 ns（L3）约为路由器 969 ns 的一半；L2/L4 下 Tofino 约 500–530 ns（读图）[p15]
- 提到的公司/客户/产品/标准：Intel/Barefoot Tofino、P4、Edgecore、Polatis、QSFP28/QSFP-DD、DCO、SDN
- 与业界对比或记录声明（SOTA/首次/record）：无；比较对象为 ROADM 光开关与传统路由器 [p16]
- 推荐配图页：p15（三类设备包转发时延小提琴图）；p2（三种 OLS 对比）

### 0924-Th1-G5-Chalmers与TalTech-基于AI的光性能监测与传感技术的权衡.pdf
- 讲者/机构：Lena Wosinska（Chalmers）等 / Chalmers University of Technology 与 Tallinn University of Technology（TalTech）；欧盟共同资助 | 题目：Trade-offs of AI-based optical performance monitoring and sensing techniques | 类型：邀请报告/综述性论述（Th1-G5）
- 方向归属（主/次）：主 1（AI光网络运维）；次 6（光纤传感 DAS/φ-OTDR/SOP）
- 核心主张：
  1. 监测/传感配置的数据率跨越约九个数量级，应以应用驱动选择配置。
  2. 三项权衡：精度⇄数据量（空间×时间×幅度精度相乘）；频率⇄定位（故障起点的定位精度不能细于探测周期）；模型复杂度⇄推理时间（只有轻量模型能跟上高数据率）。
  3. 泛化能力是 AI 监测的主要挑战：单一系统训练的模型跨系统可能崩溃，多系统联合训练可恢复。
- 关键数据：
  - 统一数据率框架：OTDR 数据率 = PRR·(L/Δx)·B；φ-OTDR 再乘 K（K=1 直检，K=2 相干 I/Q）；SOP 数据率 = f_s·N_s·B；双向SOP = 2·f_s·N_s·B，定位分辨 Δx = c/(2n·f_s)；最大脉冲重复率 PRR_max = c/(2nL)；50 km 时 PRR_max 约 2 kHz（对应 1 kHz 声频带宽）[p13][p14][p15][p16]
  - φ-OTDR 250 MSample/s 对应 500 MB/s [p14]
  - SOP：64 GBaud 符号速率下每通道最高 256 Gvalues/s；现场威胁仅需约 17 Hz 至数十 Hz；单端 SOP 累积全纤，无法定位 [p15]
  - 典型配置数据率（values/s）：SOP 子采样 17 Hz×3 Stokes = 51；OTDR 1024次平均 1.2 M；φ-OTDR L=10 km, N=10k, PRR=1 kHz = 10 M（Δx=1 m）；L=50 km, N=25k, PRR=500 Hz = 12.5 M；L=50 km, N=5k, PRR=2 kHz = 20 M；L=5 km, N=2.5k, PRR=20 kHz = 100 M；OTDR L=10 km, N=128k, PRR=10 kHz = 1 G；φ-OTDR L=10 km, N=100k, PRR=10 kHz = 2 G（Δx=10 cm）；SOP 符号速率 64 GBaud 4 Stokes = 256 G [p17]
  - 按 16 bit/值折算：SOP 子采样 816 b/s；OTDR 平均 20 Mb/s；φ-OTDR 160 M、200 M、320 M、2 G；OTDR 20 G；φ-OTDR 32 G；SOP 符号速率 4096 Gb/s [p18]
  - 案例（XGBoost 分类 relaxed/eavesdropping/soft-bending 三类 SOP，系统1 O-band、系统2 C-band）：S1 O→O 88.85%，S2 C→C 98.63%，S3 O→C（跨）8.11%（低于随机猜测 33%），S4 C→O（跨）60.59%，S5 联合训练 91.11%；泛化不对称（S3≠S4），多系统训练可恢复至 91%（引 L. Sadighi 等 ECOC 2025；看图核实）[p24]
  - 推理拆分：边缘亚毫秒轻量模型（XGBoost）、深度网络（CNN）、基础模型/零样本 LLM（秒级延迟，仅用于慢时间尺度）；架构含边缘+集中+混合部署 [p21][p22]
  - 遥测：SNMP 轮询（分钟级）→流式遥测；Telemetry-as-a-Service（EUCNC/6G Summit 2026）解耦有状态采集器与无状态注入器 [p4]
  - 开放问题：数据不平衡、泛化性、特征提取与数据最小化、动态分辨率 [p26]
- 提到的公司/客户/产品/标准：XGBoost、CNN、Vision Transformer、LLM、TaaS、OSaaS、φ-OTDR/DAS、ISAC；引用 L. Sadighi 等 ECOC 2025（DOI 10.1109/ECOC66593.2025.11263096）、C. Natalino 等 EUCNC 2026
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p17（各配置数据率 values/s 柱状图，约九个量级）；p18（折算 bit/s）；p24（SOP 跨系统泛化表）

## 本批小结
1. AI/光网络智能化在本组里分成两条线：面向控制层的智能体协同（G3 北邮 A2A 多智能体，10/10 任务完成，A2A 开销 58–120 ms）与面向数据层的数字孪生底座（G2 AIST FBD 数据库，路径识别 <1 s、拓扑更新 15 s）。二者都强调“标准化接口/公共参照”优先于单点算法（G2、G3）。
2. 在智能体开通流程中，协议开销可忽略，时延主要来自推理与仿真：G3 中 Strategy Agent 约 24–50 s、DT Agent 约 2–5 s，而协议路由约 70–78 ms；G2 中物理侧路径重建（13路径 6 min）远慢于数据库侧查询（<1 s），说明瓶颈在“慢速物理过程”和“LLM 推理”而不在数据平台（G2、G3）。
3. 跨地域（scale-across）AI训练把光纤时延推上台面：G1 仿真表明 10 km 内重叠近似为1，H100 在 1000 km 单模上训练时间约 26×，HCF 可降到约 17×，HCF 增益在“带宽→时延受限”过渡距离最大（最多 +25% 重叠）；GPU 越快越怕时延（G1）。
4. 监测/传感的数据量是 AI运维的隐性约束：G5 用统一框架给出从 51 values/s 到 256 Gvalues/s 的九个数量级，并指出模型复杂度受推理时间限制，需边缘轻量模型+中心大模型的分层；且 SOP 分类器跨波段/系统泛化可掉到 8.1%，多系统联合训练可回到 91.11%（G5）。
5. 可编程数据面进入光传送：G4 显示 Tofino 做 XoDWDM 的包转发时延（约 493–513 ns）介于光开关（48 ns）与传统路由器（969 ns）之间，提供 L1–L4 任意协议和 P4/SDN 可编程性，但 reach 受 DCO 限制（80–400 km 量级，图表待核对）（G4）。
6. 本批多数为 AI 训练光网络/网络智能化的学术工作，缺少与产业硬件（CPO/相干DSP）指标的直接对比；可量化结论主要来自仿真（G1）、试验床（G2、G4）或小规模场景（G3，德国拓扑10个业务）。
