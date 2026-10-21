---
title: "R07_ai-computing-continuum"
tags:
  - OCP2026
  - 讲稿笔记
---

# R07 笔记：ai-clusters, ai-computing-continuum, ai-open-data-center, ai-open-dc-power-distribution

### P156 Unified Telemetry for Next-Generation Rack-Scale Infrastructure
- 讲者/机构：Antonis Michaloliakos（Meta，Production Systems Engineer, AI Systems）、Nischay Tata（AMD，Fellow, Systems Design Engineer）| 类型：技术分享（含标准提案）
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [Up 机柜/超节点：UALink/ESUN（UALoE scale-up）]
- 核心主张：
  1. Helios（MI450）把外置 PCIe switch 集成掉，原来最好的"探针点"消失；GPU 的 Data Fabric 成为新的探针点，所有链路（XGMI、PCIe、UALoE、HBM）都终结在这里 [p5][p8]。
  2. 观测者效应：高频遥测轮询本身制造了它要测量的背压，需要 in-band（amd-smi）+ OOB（Redfish/PLDM）+ 架构护栏三层同时具备 [p6][p7]。
  3. 提议 OCP 制定厂商中立的接口边界遥测 schema 与"生产/调试"分级 verbosity 契约，并把"遥测影响"作为准入门槛 [p20][p21]。
- 关键数据：
  - 1,000-GPU 作业中 1 台拥塞主机会拖住其余 999 台（自报，论点性表述）[p4]
  - 关键场景下，高速遥测轮询造成了"大部分"被测的 fabric 拥塞（自报，未给百分比）[p4]
  - 机理：遥测读取产生 partial cache-line 写，压满 CPU 内存子系统（实验/自报）[p6]
  - 生产模式轮询 ~1 s（可放宽到 10 s）；调试模式低至 500 ms，集中子集可到 low-teens ms（自报）[p9]
  - 启动失败案例：PCIe link training 失败约 ~10.5 s 后 reset 进入 boot loop；错误码 ERR_FIRMWARE_LOAD、ERR_XGMI_LINK_TRAINING；boot code 0xBA/0xB0/0xBF/0xA1（现网 bring-up）[p9][p11]
  - Fleet 健康矩阵：1,790 个 bundle、1,729 次 HSIO bundle 运行、52 类 compute 测试、6 类 HSIO 测试；发现一个"compute workload timeout"属平台 bug 而非单节点（现网 bring-up 活动）[p13]
  - 每个 UALoE station 有数十个 Data Fabric 计数器，每 GPU 多个 UALoE station；四级流水（DF 接口、Encap/decap、Tx scheduler+PFC、Ethernet MAC）共"数百个"计数器在 Helios 上可读（自报）[p14][p16]
  - 诊断案例：UALoE 侧发 PFC 看似"肇事"，实为 PCIe→NIC 大量 DMA 写 HBM 造成 DF→HBM 写队列满（choke point），XGMI/UALoE 是受害者（自报，worked example）[p19]
  - 准入门槛建议：生产轮询间隔下 BusBW 劣化 >1% 即判定资格失败（提议）[p21]
- 提到的公司/客户/产品/标准：Meta、AMD、MI450、Helios、UALoE、XGMI、amd-smi、nic-ctl、afm-ctl、AMC、APML、Redfish、PLDM、BMC、CXL、OCP EMEA 2026
- 首次/记录/SOTA 声明：无（称架构已在多个机架平台和活动中"field-proven"）
- 推荐配图页：p5（有/无外置 PCIe switch 的拓扑对比）；p17（UALoE station 四级背压"判读"图）；p19（PCIe 侵占 HBM 导致 UALoE 误判的归因表）；p13（节点×接口健康矩阵）

### P157 Validation-methodologies-for-ESUN-ecosystem
- 讲者/机构：Venkat Pullela（Keysight，CTO AI Infrastructure）、Manoj Wadekar（Meta，AI Systems Technologist）| 类型：技术分享 / 标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：ESUN]；次 [运维/可靠性/遥测]（验证方法）
- 核心主张：
  1. ESUN 把标准以太网改造为无损、亚微秒的 scale-up fabric：4 字节头、LLR、CBFC（无需 PFC）、224G PHY [p4]。
  2. 从参考模型、RTL、ASIC 到机柜，每一阶段用仿真/仿真器"包围"被测件，逐步验证一致性、互通和性能 [p6][p7][p9]–[p13]。
  3. 负载验证分四阶段（Baseline → Workload Realism → Shared Contention → Stability Over Time），观测粒度逐级变细 [p14 看图]。
- 关键数据：
  - ESUN 特性：4-Byte Header、LLR（UEC 定义，降低尾延迟）、CBFC（无 PFC 的无损）、224G PHY、亚微秒确定性时延（自报/规范）[p4]
  - 示例 AI 机柜：Compute tray 4×GPU + 800G NIC 阵列；Switch tray 含 2 颗 512×200G lane 交换 ASIC；cable backplane 连接（自报示意）[p8]
  - 四阶段负载验证：Stage1 单 collective 隔离短时；Stage2 代表性阶段与 collective 组合；Stage3 多负载共享一个争用域；Stage4 Stage3 长时持续，看方差增长、尾延迟、周期性拥塞（看图）[p14]
- 提到的公司/客户/产品/标准：Keysight、Meta、NVIDIA/AMD/Broadcom（图片来源）、ESUN、UEC、SONiC Scale-Up WG、OCP ESUN Network Operator Requirements Base Spec Rev 1.0
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（ESUN 四项架构特性）；p8（scale-up 机柜：compute/switch tray + cable backplane）；p14（四阶段负载验证表）

### P158 01_AI Computing Continuum Use Cases and Collaboration Items
- 讲者/机构：Xiaojing Zhang（NTT DOCOMO Business）、Naoto Umemori（NTT Data）、Hidetsugu Sugiyama（Red Hat）、Junichi Sugiyama（1Finity）、Koji Watanabe（NTT）| 类型：技术分享（多 PoC）
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：DCI、APN 全光网、长 RTT]；次 [In：CXL/内存池化]、[推理/算力/经济性]
- 核心主张：
  1. AICC 在 IOWN APN 上定义三种跨域计算模式：Scale-Across（跨地域 GPU 集群）、Sync-Across（WAL/数据库同步）、Reach-Across（远程 GPU 读本地数据）[p2]。
  2. 训练数据加载与 GPU 计算流水化，只要单批加载时间 ≤ 单批计算时间，距离对训练时间影响很小 [p5 看图][p6]。
  3. 不同负载对距离敏感度不同，共同需求是"端点到光层"行为可预测、可观测、可互通；1Finity 提出 Photonic SmartNIC 并建议 OCP 形成 Scale-Across Endpoint Profile [p17][p18][p20]。
- 关键数据：
  - Reach-Across PoC：Unet3D（MLPerf Storage v1.0.1），28,000 张图 ≈ 3.8 TB；存储在 Site A，GPU 在 Site B（NVIDIA H100×4）；100G APN 实际 40 km，最多仿真 500 km；NFS over TCP/RDMA（实验）[p4]
  - 40 km 训练时间比本地 +1.9%（357 → 364 s/epoch）；100 km 内低于 +10%（实验）[p6]
  - 100 km 吞吐保留 94%（9.66 GiB/s，NFS nconnect=16）；互联网级链路约慢 89×（实验）[p6]
  - 总功耗（含 PUE）持平：绿色 DC PUE 1.56 vs 1.98 抵消 +20% IT 能耗（实验/估算）[p6]
  - FC 客户端光与 APN/DWDM 线路使用不同波段，目前需转发器 O-E-O；目标是全光不经 O-E-O（自报）[p12]
  - 分布式 LLM 推理 PoC：PD 分离 + 多层 KV cache（T1 GPU mem、T2 CPU mem+CXL mem、T3 存储），跨 IOWN APN 的拉伸集群（自报架构）[p15]
  - 1Finity 原型：~100G，在评估配置下 180 km 内稳定 ~90–93 Gbps（实验）[p19]
  - 对比曲线：Conventional—8k 在 20 km 降至约 27 Gbps、100 km 约 6 Gbps；Prototype—8k/512k 到 180 km 保持约 90–93 Gbps（看图）[p19]
  - 合作项目：Kyushu Electric·IIJ·QTnet·Nautilus 区域分布式 DC PoC（2025-10 启动）；Accton/Edgecore·Liqid 跨站 RDMA/NVMe-oF（SC25）；Watt-Bit/Physical AI 现场 PoC 100 km+ 远程 GPU + 实时 4K AI（2026-08 至 2027-03）（引用，自列来源）[p19]
- 提到的公司/客户/产品/标准：NTT、NTT Data、NTT DOCOMO Business、Red Hat（RHOCP）、1Finity、Fujitsu（FSAS Primergy-CDI）、NVIDIA H100、IOWN Global Forum、APN、MLPerf Storage、CoHDI、Kubernetes DRA、llm-d、vLLM、LMCache、NIXL、CXL、JBOG/JBOM、Kyushu Electric、IIJ、QTnet、Nautilus、Accton/Edgecore、Liqid、TEPCO PG、Chubu EPG、OCP ESUN、UEC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（40 km +1.9%、100 km 94% 结果卡片）；p19（吞吐-距离曲线：常规 vs 原型）；p15（跨 APN 的 PD 分离推理架构）

### P159 02_AI Computing Continuum Extending the Open Data Center Ecosystem Across
- 讲者/机构：Masahisa Kawashima（NTT, Inc. & IOWN Global Forum Chair）、Vincent Nguyen（HPE Fellow）、Dirk Blevins（Intel Datacenter Group）| 类型：主题演讲（AICC 项目总览）
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：APN、scale-across]；次 [底座-机架/机械]、[推理/算力/经济性]
- 核心主张：
  1. AICC 面向"超大规模邻近"场景（neocloud、主权 AI、colo、企业、边缘），把 OCP 超大规模积木延伸到功率/散热/空间受限场所 [p4][p9]。
  2. 规模不是全部，连通性/可达性同样重要；用 Open APN 构建"Hub-and-Optical-Spoke"拓扑 [p11][p12]。
  3. OCP 出产品规范、IOWN GF 出用例与参考设计，两者合起来补齐栈 [p15][p17]。
- 关键数据：
  - 部署分级功率：8×GPU Scale-Up 8–15 kW；4×GPU 无 scale-up 1.5–5 kW；1–4×GPU 3–5 kW；1×GPU 短深 0.8–2 kW / 0.8–3 kW（自报）[p6]
  - scale-across 互连：100GbE+（自报示意）[p7]
  - 未来 12 个月规范目标：Hyperscale Adjacent 机柜/服务器规范；OpenAPN NIC（基于 OCP NIC）与 OpenAPN SmartNIC（基于 OAC 或 OCP NIC）；AI Native Edge-MHS 修订；AI Native Wireless AuRu 与 Bridge Board 规范；UNH 体验中心（预测/计划）[p16]
- 提到的公司/客户/产品/标准：NTT、IOWN Global Forum、HPE、Intel、Arm、Celestica、OCP MHS、DC-SCM、ORV3、OAC、OCP NIC、NVLink、UALink、UEC、RoCE
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（超大规模邻近部署分级与功率表）；p12（APN Hub-and-Optical-Spoke 拓扑）；p16（下一年规范目标）

### P160 03_AI-Native Edge MHS 1.0
- 讲者/机构：David Heinrich（HPE，Fellow, Server Architect）、Dirk Blevins（Intel，Senior Platform Architect）| 类型：标准进展
- 方向归属（主/次）：主 [底座-机架/机械]；次 [推理/算力/经济性]（边缘推理）
- 核心主张：
  1. AI-Native Edge-MHS 1.0 已发布：面向边缘的模块化硬件，尽量兼容 DC-MHS，按机箱深度分 Short/Mid/Extended [p5][p12]。
  2. 定义 Class N（168 mm 宽）与 Class L（295 mm 宽）HPM，共用安装孔与 riser 位置 [p8][p9]。
  3. 多 GPU 与内存/I/O 密度推动在 N 与 L 之间探索新 HPM 尺寸；OAC/PCIe CEM 是否够用仍是开放问题 [p10][p11]。
- 关键数据：
  - 设备长度 <310 mm 与 <430 mm；供电 12VAC 与 -48VDC；NEBS 与 IP67+ 可认证（自报目标）[p4]
  - 机箱深度 310/350/430 mm；Class L 295 mm 宽、Class N 168 mm 宽，长度 250–365 mm 可伸缩（自报）[p5][p9]
  - HPM 规格表：N260/N280/N350/N365 分别对应 310 mm、350–420 mm、420–450 mm 服务器及 OTII-E 类；L260/L305（305.59 mm，M-DNO Type 4）/L350（看图）[p7]
  - N365 与 N350 间距 181 mm 以共享 L260 的安装孔与 riser（自报）[p8]
  - 控制面板/入侵开关区 25×45 mm；DC-SCM CFF 推荐区 18×22 mm（自报）[p9]
  - Class L 只能容纳 1 张 FHFL 双宽卡或 3 张 PCIe FLFL 单宽卡（自报）[p10]
  - 邻近场景：机柜最高 120 kW（多数 <50 kW）、风冷 GPU 卡最高 600 W；GPU 每颗最高 1000 W（超大规模 5000 W），邻近场景多在 500 W 以下（自报）[p11]
- 提到的公司/客户/产品/标准：HPE、Intel、DC-MHS、DC-SCM CFF、OCP NIC（Timing/GNSS 模块）、M-XIO、OAC、PCIe CEM、OTII-E、M-DNO
- 首次/记录/SOTA 声明：AI-Native Edge-MHS Specification V1.0 发布 [p12]
- 推荐配图页：p7（Class N/L 外形与尺寸表）；p8（多板兼容叠加图）

### P161 04_Breaking the Data Center Walls Unifying AI Fabrics for Agentic AI at t
- 讲者/机构：Prakash Jain（Celestica，Director, Architecture & Design Engineering, AI Infrastructure）| 类型：技术分享（架构提案）
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：scale-across 控制面、LISP/SRv6/BGP-EVPN 对比]；次 [Out 后端网络]、[Up 机柜/超节点]
- 核心主张：
  1. Agentic AI 需要有状态、分布式执行，AI 算力被困在"数据中心墙内"，需要把 Scale-Up/Out/Across 统一为一个 fabric [p3][p7]。
  2. 统一控制面需把端点标识（AccID，可非 IP/MAC）与路由定位解耦，支持工作负载迁移和多租户隔离（Instance-ID）[p10]。
  3. 推荐 LISP（拉取式映射、pub/sub）用于超低时延动态 scale-across；SRv6/BGP-EVPN 适合标准化多租户虚拟化 fabric [p12][p14]。
- 关键数据：
  - 网络指标要求：每端口 ≥400–800 Gbps；时延 <1–100 μs（目标 ~250 ns）；无损 RDMA；无抖动（自报需求）[p4]
  - 4 层持久分布式 KV cache（PD-KVC）、Agent State Journaling、Agent Coordination Channel（自报概念）[p4]
  - Scale-Up 域单 PoD 最多支持 1,024 个加速器，满足 load/store 亚微秒时延（自报设计目标）[p12]
  - 控制面收敛：亚微秒级（自报主张，未给测量）[p11][p14]
  - 未来研究方向：CPO/ELS <3 pJ/b；光引擎移到主芯片下方"100x 带宽"；6G RAN 皮秒级定时（自报方向）[p16]
- 提到的公司/客户/产品/标准：Celestica、LISP（draft-jain-lisp-network-ai-infra-04）、SRv6、BGP-EVPN、OCP ESUN、UEC（UE-Specification-1.0.1）、SONiC、IETF、AICC、AI HW-SW-CoDesign
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（多 DC scale-across 架构：SA-GW + LISP MSMR + SDN 控制器）；p14（SRv6 / BGP-EVPN / LISP 对比）；p4（网络指标要求）

### P163 06_From AI PC to AI Infrastructure Platform Contracts for Scalable CPU-Ac
- 讲者/机构：Dong Wei（Arm Fellow）、Suraj Varma（Arm，Senior Principal Architect）| 类型：技术分享
- 方向归属（主/次）：主 [推理/算力/经济性]（节点级平台）；次 [底座-机架/机械]
- 核心主张：
  1. AICC 定义分布式 AI 的宏观架构，Arm 系统架构提供可重复的节点基础 [p3][p4]。
  2. Scale/Sync/Reach-Across 分别映射到计算+加速、控制+遥测、平台基础等节点层 [p5]。
  3. 用 BSA/SBSA、BBR/SBBR、BBSR/SBMR、ACS/SystemReady/OCP Accepted 把需求转为可测试的部署保证 [p8][p9]。
- 关键数据：
  - 无定量数据；仅规范清单：BSA、SBSA、PC BSA、FCSA（chiplet 标准）、SBBR（UEFI/ACPI/SMBIOS）、SBMR（自报）[p9]
  - Arm 与 OCP 已在 Server 与 Hardware Management 项目下设立 SBSA 与 SBMR SPW（自报）[p9]
- 提到的公司/客户/产品/标准：Arm、OCP、BSA、SBSA、SBBR、SBMR、BBSR、FCSA、ACS、SystemReady、OCP Accepted、PCIe、CXL
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（AICC 模型到 Arm 节点分层映射）；p9（Arm 系统架构规范栈）

### P164 07_The Autonomous AI-RU Closing the RIC intelligence gap to the radio thr
- 讲者/机构：Laawanya Kishor（UGECO PRIVATE LIMITED，Director & Founder）、Rexy Geevarghese（Bell Canada，Principal RAN Architect）| 类型：技术分享（实验）
- 方向归属（主/次）：主 [量子/其他]（无线接入 RAN/AI-RU）；次 [推理/算力/经济性]（节能）
- 核心主张：
  1. RIC 控制环为 10 ms–1 s（E2）和 >1 s（A1/O1），而无线符号/时隙在微秒级，时间差无法靠传输补；需要驻留在 RU 内的 ruApp 本地决策 [p3]。
  2. 慢环（rApp 经 O1→OCUDU→Open M-Plane）设定策略包络，快环（ruApp）本地唤醒，两环共存于开放管理路径 [p5][p9]。
  3. 仅 rApp 时节能"看似更高"是因为在真实需求时仍在睡眠；加 ruApp 后零漏服务 [p7]。
- 关键数据：
  - rApp SLEEP 到板卡引脚拉低：400 ms（整条标准管理路径）（实验，2026-09-18）[p6]
  - ruApp 本地唤醒决策：56 µs；触发到载波 HIGH：29 ms（主机软件经以太网，非决策）（实验）[p6]
  - 模型训练数据：真实运营商 KPI 29 小区 8 天（实验）[p6]
  - Depth（3 站 30 天，留出 5 天，平均 PRB 6.2%）：es-rApp+ruApp 节能 15.6%，0 漏窗；rApp only 17.6% 但漏 15 窗（5 天内 8 小时需求未服务）；Oracle 18.4%；达到上限 85%（实验/回放）[p7]
  - Breadth（29 小区 8 天，留出 2 天，平均 PRB 14.9%）：es-rApp+ruApp 12.1%，73 次本地唤醒；rApp only 17.8%，漏 166 窗（83 小时）；Oracle 17.6%；达上限 69%（实验/回放）[p7]
  - 功耗模型：200 W 空闲 → 400 W 满载，睡眠载波 60 W（实验室测量曲线）[p7]
  - 小区节能中位数 6.3%；两个近空扇区睡眠 69.8% 和 42.5%；9 个繁忙小区从不睡眠（实验）[p8]
  - Depth 每日节能 18.3%/18.3%/12.9%/13.4%/15.3%（8/22–8/26）；Breadth 12.2%/12.1%（6/15–16）（看图）[p8]
- 提到的公司/客户/产品/标准：UGECO、Bell Canada、OCUDU、Open M-Plane、NETCONF/YANG、netopeer2、sysrepo、eCPRI、O-RAN（RIC、rApp、SMO、E2/A1/O1/R1）、Lattice CertusPro-NX、NVIDIA Holoscan Sensor Bridge、NVIDIA Jetson AGX Thor、3GPP TR 38.901、github.com/opencomputeproject/ocp-auRu
- 首次/记录/SOTA 声明：无（Phase 2 于 2026-09-18 完成，自称"zero missed windows"）[p10]
- 推荐配图页：p6（400 ms vs 56 µs 实测卡片与当夜时间线）；p7（三种方案节能/漏窗对比表）；p8（逐日/逐小区节能柱状图）

### P165 08_The Open Adapter Card – Light
- 讲者/机构：Vincent Nguyen（HPE Fellow）、Dirk Blevins（Intel Datacenter Group）| 类型：标准进展（征求需求）
- 方向归属（主/次）：主 [底座-机架/机械]；次 [Up 机柜/超节点]（小规模 scale-up）
- 核心主张：
  1. colo/PoP 多租 19" 机柜，现有方案过重、过热、功率过高；需"OAC-Light"类卡形态 [p4]。
  2. PCIe CEM 除 I/O 面板外无原生相干 scale-up 连接，且有未来连接器速率顾虑；OAC 功能完整但对 1U/2U 过大 [p5]。
  3. 可用现成 OAC 以 rack-and-stack 方式在机柜内组建 scale-up [p7]。
- 关键数据：
  - 邻近场景机柜最高 120 kW（多数 <50 kW）、风冷 GPU 卡最高 600 W；GPU 超大规模 5000 W vs 邻近 <500 W（自报）[p5]
  - 示例：2U 机架内 4 节点 scale-up（OAC + AI Native MHS）；430 mm 边缘服务器无 scale-up；1000 mm 5U 企业服务器含 OAC GPU 与 OAC Switch Card（自报示意）[p6][p7]
- 提到的公司/客户/产品/标准：HPE、Intel、OAC、PCIe CEM、DC-MHS、AI Native Edge-MHS、M-CRPS、M-XIO、DSFF、OCP NIC SFF、M-SDNO
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（OAC 在边缘/企业服务器中的布局）；p7（5U 企业服务器 OAC GPU + Switch Card 前后视图）

### P168 02_Automation-Ready Infrastructure Design From Light to Compute
- 讲者/机构：Dave Evans（Google）、Mike McKee-Hector（Microsoft）、Ryan Olson（Meta）、Eric Xu（Meta）| 类型：面板
- 方向归属（主/次）：主 [运维/可靠性/遥测]（机器人运维）；次 [Out 后端网络：可插拔光模块/XPO/CPO]、[底座-机架/机械]
- 核心主张：
  1. 比特流已工业化，物理运维仍零散且人工，硬件运维撞上"物理墙"[p3]。
  2. 光模块/光纤与托盘设计需为自动化标准化：抓取位、标签、导入、刚性拉环、到位确认、基准 [p5][p7]。
  3. 自动化设计须兼顾人和机器人，机器人应成为与电力、冷却、连接、算力并列的基础设施层 [p17]。
- 关键数据：
  - 定位精度设计目标：3 mm 通用公差（自报）[p5]
  - 光模块路线：QSFP → OSFP → XPO → NPO/CPO；网络 200/400G → 800G/1.6T → XPO/CPO（自报）[p4][p6]
  - 无更多定量数据
- 提到的公司/客户/产品/标准：Google、Microsoft、Meta、QSFP、OSFP、XPO、NPO/CPO、LC、MPO、automation@ocproject.net
- 首次/记录/SOTA 声明：无（预告两份白皮书：Optics & Fiber、Server Automation-Native Design）[p18]
- 推荐配图页：p6（光模块形态路线图）；p8（自动化光模块与光纤配置照片）；p14（服务器维护生命周期示意，看图）

### P173 08_Supporting load smoothing, Fault Ride-through (FRT), and back up in 80（精简）
- 讲者/机构：Stuart Sheehan（Schneider Electric，Systems Engineer）| 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. 储能需分层：机柜级电容（ms）、LVDC 动力链级功率电池（分钟级，覆盖 UPS、FRT、平滑）、园区级长时储能 [p11]。
  2. 当前 NVIDIA 机柜与 OCP SST 规范趋向窄电压带，留给 droop 的余量更少，主动均流更合适 [p12]。
- 关键数据：
  - 用例：AI 负载缓冲 ms–s；电网 FRT 100+ ms；UPS 1–15 min；需求响应数小时；站点备份数小时到数天（自报）[p7]
  - Galaxy UPS FRT：0.15–0.5 pu 全由电池供电、<300 ms 恢复；0–0.15 pu 限 250 ms；平滑 1%/s 升降速率；平滑示例 120% 100 ms / 80% 0.5 s / 30% 0.5 s（自报/现网产品，看图核对）[p14]
  - 连续平滑寿命：LFP 50% 占空 0.8C 充电 7 柜/MW 10 年；LFP 1.6C 4 柜/MW 7 年；LMO 0.6C 12 柜/MW 10 年（自报）[p15]
  - 成本：UPS 电池扩容 ~0.1–0.15 \$/W；新增 BESS ~0.3–0.6 \$/W（基于 0.5C Tesla Megapack）（自报估算）[p15]
- 推荐配图页：p14（FRT 曲线与输入平滑波形）；p11（分层储能映射）

### P179 Large-Scale Deployment of 800Gb-s Active Electrical Cables in Meta Data Centers for AI Applications
- 讲者/机构：Jingyu (Kevin) Yu（Meta，Component Quality Engineer）、Abhijit Chakravarty（Meta，Quality Head - Optics & Interconnects）| 类型：技术分享（现网部署经验）
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/AEC、机柜级互连]；次 [Out 后端网络]、[运维/可靠性/遥测]（质量/认证）
- 核心主张：
  1. AI 网络的经济性由短距链路决定；800G AEC 在跨柜距离上填补 DAC 与光之间的空缺 [p2][p4][p3 看图]。
  2. 器件级认证不等于集群级认证；互通失败常源于固件而非 SI [p6][p7][p8]。
  3. 制造差异只有在超大规模才显现，热循环暴露稳态应力下隐藏的失效，供应商认证是持续过程 [p9][p12][p15]。
- 关键数据：
  - 对比：光 ~12–15 W+/端、可达 10 km+；DAC ~1–2 W/端、~2–3 m，112G PAM4 预算下"无法满足"；AEC <12 W/端、<2 m，满足且有余量（自报）[p4]（注：p5 写 1.0–3.2 m、p3 写 ~2–7 m，口径不一致，存疑）
  - Meta 800G AEC：OSFP、112 Gb/s PAM4 lanes；IHS（交换机）到 RHS（NIC）；32 AWG twinax，外径 ~7.5 mm；<12 W/端；2x400G/1x800G/8x100G；CMIS 5.1；1.0–3.2 m；Minipack3 ↔ 多款 NIC 的 POR（现网）[p5]
  - 机柜对拓扑：DAC ≤~2 m 柜内 CT→MP3 front-end；AEC ~2–7 m 柜到柜 CT→MP3 scale-out，两柜间唯一高速链路；光 ~7–500 m 出柜（看图）[p3]
  - 部署规模："数百万"AI 互连（自报）[p6][p9]
  - 跨供应商故障：reset 循环后 NIC 未完成 datapath bring-up；根因 AEC MCU I2C 预取 + 固件状态锁存，寄存器 0xCA 读到 0x1C（配置中）而非 0x11（完成）；修复为"配置中"断言 <1 ms（现网）[p8]
  - 另一案例根因：CMIS application mode 不一致，统一各供应商固件配置（现网）[p7]
  - EMI：系统级辐射发射目标余量 10 dB；各来源实测 ~5.7 至 ~9.0 dB（实验）[p11]
  - 热循环 LTR：样本 Supplier A 64、B 64、C 32 根；3×Minipack3，800G 流量（Spirent/Xena Freya）；~0.7 °C/min；目标壳温 ~40/50/70 °C；阶段 36–72 h、1 周、30 天、90 天（实验）[p13]
  - 风扇 PWM 与壳温：45% → 最高 64 °C；35% → 68 °C；25% → 75 °C；20% → 82 °C（超应力，非连续）；正常运行 >70 °C 停测（实验）[p14]
  - 笼温统计：45% 风扇均值 42.6 °C / P99 ≈52；20% 风扇均值 60.8 °C / P99 ≈71（看图）[p14]
- 提到的公司/客户/产品/标准：Meta、Minipack3、Wedge400、TH6（Switch Tray）、HPRv3、ORv3、OSFP、CMIS 5.1、RDMA/NCCL/RoCE、Spirent、Xena Freya、DiagOS、SPC、MES
- 首次/记录/SOTA 声明：无（自称大规模部署，未称首次）
- 推荐配图页：p3（机柜对中 DAC/AEC/光/RJ45 四种线缆分工，看图）；p4（光 vs DAC vs AEC 对比表）；p8（固件竞态故障-根因-修复）；p14（热循环温度表）

### P183 Quantified Benefits and Open Challenges Applied to a 250 MW Reference Architecture（精简）
- 讲者/机构：Peter Gross（PMG Associates）、Chris Thompson（Vertiv，VP Advanced Technology）、Frances Bosman（VEIR）| 类型：面板
- 方向归属（主/次）：主 [底座-电力]（超导配电）
- 核心主张：
  1. HTS 电缆以更高载流和近零损耗替代铜，使灰区与白区不必相邻 [p3][p6]。
  2. 规模化前需解决标准规范、终端、失超管理和市场就绪四类问题 [p7]。
- 关键数据：
  - ≤800 Vdc：每根 10/20/30 MW；≤600 Vac：5/10 MW；中压至 36 kV：每根 240 MW；带材电流密度 ~180 A/mm²；HTS ~77 K（自报）[p3]
  - LV 馈线（480 VAC，5,000 A）：HTS 单根 12.3 kg/m、OD 110 mm、段长至 200 m；铜母线 156 kg/m、700×300 mm、7.5 m 段（自报）[p4]
  - MV 环网：用铜 1.8 vs 65.5 kg/m；开挖 312 vs 1820 yd³；混凝土 164 vs 644 t（自报）[p4]
  - 水管长度减少 25–35%（自报）[p6]
- 推荐配图页：p4（HTS vs 铜对比表）；p5（5,000 A 铜缆束 vs 单根超导电缆照片）

### P186 The Compliance Gap- ESS Safety in the Age of AI Infrastructure（精简）
- 讲者/机构：Joel Chakkalakal（Americase，主持）、Mike Pagel（HazMat Safety Consulting）、Mauro Leuce（Digital Realty）、Shrikanth Venkateshappa（Anord Mardix / Flex，OCP 储能与 HTS 子项目负责人）| 类型：面板
- 方向归属（主/次）：主 [底座-电力]；次 [安全]（危险品/储能合规）
- 核心主张：
  1. 每柜 BBU 与园区 BESS 增多，储存、运输、安装、退役规则因国家、规范、保险方而异 [p7]。
  2. 把 OCP 白皮书"Requirements for Energy Storage Systems Used in Data Centers (Rev. 1.0)"转化为内部标准：Audit、Align、Act [p7][p8]。
- 关键数据：
  - 超大规模运营方需在 25+ 个国家落地（自报）[p7]
  - HazMat Safety Consulting 正争取 OCP 在联合国危险货物运输专家小组委员会的观察员地位（自报）[p9]
  - 无技术定量数据
- 推荐配图页：无（以文字页为主）

### P188 The New Focus on Energy Storage Systems Safety（精简）
- 讲者/机构：Dan Lambert（ZincFive）、Shrikanth Venkateshappa（OCP Energy Storage Project Lead，Anord Mardix）| 类型：标准进展
- 方向归属（主/次）：主 [底座-电力]；次 [安全]
- 核心主张：
  1. ESS 已从 UPS 电池间扩散到排级、机柜级，技术相同但安全论证不同 [p2]。
  2. 产品认证只是四层（产品、应用、安装、验收）之一；冲突常在许可、保险审查或调试阶段才暴露 [p3][p4]。
- 关键数据：
  - 涉及技术：锂离子、镍锌、铅酸、钠离子、超级电容（自报）[p2]
  - 两个工作流：WS1 ESS 技术参考（白皮书 V2）；WS2 选型与部署框架，引用 IEEE 1679、IEC 62933（自报）[p6][p8]
- 推荐配图页：p2（设施/排/机柜三级 ESS 分布）；p3（四层审批）

### P192 Closing-the-Standards-Gap-for-LVDC-Power-Distribution（精简）
- 讲者/机构：Lisa Grams（UL Solutions，VP Product Management）、Michael Jensen（UL Solutions，Senior Product Manager, Data Centers）| 类型：标准进展
- 方向归属（主/次）：主 [底座-电力]；次 [安全]
- 核心主张：
  1. Power Distribution 子项目于 OCP Global Summit 2025 启动，UL Solutions 牵头 Codes & Standards 工作流 [p2]。
  2. 已建立 800V DC 数据中心 UL 与 IEC 标准映射清单；DC 电弧、电容性故障、安装规范、电网互联仍是"已知的未知" [p6]–[p10]。
- 关键数据：
  - 优先产品标准：sidecar、模块化、MV SST、断路器、液冷 [p5]
  - 映射示例：800 VDC 母线槽 UL 857 ↔ IEC 61439-6；DC sidecar 800V DC 输出 UL 62368-1+CRD ↔ IEC 62368-1/61439-2；MV SST UL 2877 OOI ↔ IEC 62477-2；固态断路器 UL 489I ↔ IEC 60947-10（自报）[p6][p7][p8]
  - 尚无标准（New OOI）：DC AFCI、DC GFCI、绝缘监测、超导电缆系统、液冷电缆、挤压（液冷）绝缘母排、Litz wire PDU2 与 J-box 连接器（自报）[p6]
- 推荐配图页：p6（800V DC 美国安全标准总表）；p10（未解决问题清单）

### P196 From-Principles-to-Practice-Implementing-OCP-LVDC-Frameworks-with-a-600kW-800VDC-Sidecar-Power-System-Design（精简）
- 讲者/机构：Guang Yang（Siemens Industry US，R&D Director）、Tero Järveläinen（Skeleton Technologies，CPO）| 类型：技术分享（产品方案）
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. 机柜功率接近 1 MW，平滑与故障保护不能再分开处理；sidecar 组合固态断路器与高功率储能（超级电容）[p2][p12]。
  2. 在 sidecar 内、靠近负载处滤除 0.1–55 Hz 次同步分量，上游看到无波动的功率需求 [p7]。
- 关键数据：
  - 机柜功率四代：145 kW（GB200/GB300）→ 330 kW（Vera Rubin NVL72）→ 570 kW → 1,000 kW（native 800 VDC）；Graphene Sidecar 1,200 kW（引用 NVIDIA 2026）[p3]
  - 48OU 柜内液冷可装 1.2 MW；PSU 3OU、300 kW 连续；每个 CBU 160 kW 连续 / 240 kW 峰值（自报）[p8]
  - CBU800 模块：功率电子 80 kW 连续 / 120 kW 峰值，占体积 10–15%，其余为超级电容（自报）[p9]
  - 负载电流在 ~400 A 与 ~1300 A 间跳变时，有平滑后 PSU DC 稳在 ~800 A，电网 AC 幅值恒定（看图，Skeleton 实测）[p6]
  - Load→PSU 电流衰减：约 0.1 Hz -72 dB、1 Hz -60 dB、10 Hz -42 dB、100 Hz -20 dB（看图，实验室）[p7]
  - 从 IT 机柜移出的内容：BBU 80 kW 60 s；415–480 VAC 经 12×100 A 线缆输入，经 6×18.3 kW PSU shelf 输出 800 VDC；DC 线缆最高 250 A（自报）[p11]
- 推荐配图页：p3（机柜功率代际增长柱状图）；p7（衰减-频率曲线，看图）；p8（48OU sidecar 布局）
