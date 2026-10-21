---
title: "R21_systems-management"
tags:
  - OCP2026
  - 讲稿笔记
---

# R21 笔记：server, sonic-workshop, storage, systems-management

### P462 Copper-Interconnect-Innovations-for-Realizing-400G-Electrical
- 讲者/机构：Andrew Kim、Jinhua Chen，Luxshare-Tech | 类型：厂商技术分享
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板]；次 [Out 后端网络：可插拔/前面板 DAC/AEC]
- 核心主张：
  1. 400G/lane 电互连（OIF CEI-448G、IEEE 400GPL）中，twinax 将承担大部分通道长度，连接器是主要限制环节 [p2]。
  2. 弹性体（elastomeric）CPC 无 stub、全程 360° 屏蔽，SI 已可到 110–120 GHz；twinax-twinax 对插结构可用于 cable backplane / 前面板 DAC / AEC/ACC paddle card [p5][p10][p11]。
  3. PAM-6（90 GHz）近期可行，PAM-4（112 GHz）也在可及范围 [p15]。
- 关键数据：
  - CPC 差分对间距 1.9mm x 1.7mm；无谐振至 120+ GHz（自报）[p5]
  - 300mm 31AWG CPC-CPC 线缆组件，IL 平滑至 VNA 上限 110 GHz，无谐振（实验）[p6]；去嵌 IL 约 -14~-15 dB @110 GHz，非去嵌约 -33 dB @110 GHz（看图）[p6]
  - RL 大体低于 -10 dB（实验）[p7]；回损峰值约 -9~-10 dB 出现在约 55–60 GHz，ILD 基本在 ±1 dB 内（看图）[p7]
  - 5 次插拔重复性：Min-Max 差 0.51 dB（实验）[p8]；@90 GHz SDD21 -26.14~-26.59 dB，@106 GHz -29.44~-29.95 dB（看图）[p8]
  - 串扰仿真（2x3 差分对模型，2 NEXT + 3 FEXT）：新 2026Q3 设计将 PSXT 峰值从 110 GHz 推到 120 GHz，并降低约 15 dB（仿真）[p9]；新设计峰值约 -52 dB @~121 GHz，旧设计约 -37 dB @~110 GHz（看图）[p9]
  - 448G cable backplane 连接器首批样品已制成（自报）[p12]；330mm 31awg + 940mm 27awg + 330mm 31awg 两级 VH-VR 对插链路，清洁响应至 100 GHz，110 GHz 才出现谐振（实验）[p13]
  - 前面板 LR 段（240mm 31awg + 525mm 27awg + 240mm 31awg，两个前面板连接器）：清洁至 100 GHz，无大谐振；初样仍有制造公差问题（实验）[p14]；非去嵌 IL 约 -50 dB @100 GHz，去嵌约 -30 dB @100 GHz（看图）[p14]
- 提到的公司/客户/产品/标准：Luxshare-Tech、Koolio CPC、OIF CEI-448G、IEEE 400GPL、CPC/NPC、DAC/AEC/ACC/AOC、DesignCon'26
- 首次/记录/SOTA 声明：首批 448G cable backplane 连接器样品（p12，自报"First Samples Built"）
- 推荐配图页：p9（新旧 CPC 串扰仿真对比，峰值后移 + 低约 15 dB）；p14（前面板 LR 链路 IL 与实物照片）

### P463 From-Fragmentation-to-Footprint-The-OCP-Standard-for-AI-Signal-Conditioners
- 讲者/机构：Casey Morrison（CPO）、Liang Xue，Astera Labs | 类型：标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板、机柜级互连]；次 [Out 后端网络]
- 核心主张：
  1. AI scale-up 背板需要 retimer/gearbox 等信号调理器，但传统封装过大、损耗高、难以对接主流背板连接器，且无行业标准 pinout [p2]。
  2. OCP Signal Conditioner Standard Footprint：面向厚板（200 mil）HVM 设计规则、可"tiling"、与 redriver/retimer/gearbox 及协议无关，支持"BoM swap"多供应商互换 [p3][p5][p6]。
- 关键数据：
  - 8/16/24-lane 三种变体；适配列间距 2.4–2.8 mm 背板连接器；兼容 10mil 钻孔、优化 8mil（规格）[p3]
  - FEXT < -60 dB、NEXT < -70 dB，均至 54 GHz（200 mil 叠层，170 mil 过孔）（自报/仿真口径未注明）[p3]
  - 两颗 16L retimer tiling 支持 64 对差分（8x8：32 Tx + 32 Rx）在约 22mm x 方向；8 层布线在约 20mm 通道内逸出 64 对；24L 版 8x12 = 96 对（设计）[p4]
  - 应用分界：redriver 适合 <20 dB 中等延伸，retimer/gearbox 适合 >20 dB（规格）[p5]
  - 面向未来至 128 GBaud（如 256 Gbps PAM4）[p7]
  - v1.0.0 Base Specification 已发布 [p8]
- 提到的公司/客户/产品/标准：Astera Labs、OCP Server、OSFP/OSFP-XD/CDFP（未来优化方向）、CPC-to-Backplane interposer
- 首次/记录/SOTA 声明：称当前无行业标准 pinout，此为 OCP 首个 AI 信号调理器标准 footprint（p2/p8）
- 推荐配图页：p4（16L/24L retimer tiling 与背板连接器对齐布局）

### P465 Open-Adapter-Card-OAC-Sub-Rackscale-Acceleration-Lives-On
- 讲者/机构：Greg Sellman（AMD）、Brian Aspnes（Intel）| 类型：标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：机柜级互连]；次 [底座-机架/机械]、[底座-冷却]
- 核心主张：
  1. OAI/OAM 于 2024 年 sunset，8 卡 pod 平台仍需替代方案，OAC 作为新的加速卡形态 [p2]。
  2. 一种形态承载多种 fabric（PCIe Gen7、200G Ethernet、NVLink、UALink、CXL），通过 CID 与 SCD 两个概念实现协议无关 [p4]。
- 关键数据：
  - 功耗需求 2x–8x 增长（自报）[p2]
  - 三种宽度 SW/DW/DWO；19" 机箱最多 16 张 SW 或 8 张 DW/DWO [p3][p5]
  - 可用 PCB 面积最多 4.5x（PCIe CEM→DWO OAC）；体积 3.2x（DW CEM→DW OAC）[p3]
  - 112 lane 200Gbps HSIO，ZettaMAX 2-pc 连接器；最多 224 差分对 + 50 离散信号 [p3][p4]
  - 5000W @50V / 1200W @12V；单宽 4000W / 960W [p3]
  - 风冷：DW 约 700W，DW Tall 约 1200W [p6]；DLC 用 MQDB-04 QD 接口 [p3]
  - 规范 v0.9 已可获取 [p7]
- 提到的公司/客户/产品/标准：AMD、Intel、Qualcomm、Dell、Nvidia；OCP DC-MHS、DC-SCM 2.1、NIC 3.0、M-CRPS、UQD v2.0
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（OAC 三种宽度形态与关键参数汇总）

### P467 Scaling-Hyperscale-Cloud-Networking-from-400G-to-800G-System-Integration-Lessons-and-Implications-for-OCP-Platforms
- 讲者/机构：Lucy Yu、Faye Yang，Microsoft | 类型：技术分享（经验总结）
- 方向归属（主/次）：主 [Out 后端网络：NIC]；次 [运维/可靠性/遥测]、[安全]
- 核心主张：
  1. SmartNIC 已是"服务器中的服务器"，承载计算、存储、安全栈，需按服务器管理 [p2]。
  2. 400G→800G 过渡后，带宽不再是唯一瓶颈，功耗密度、散热、固件、安全、验证决定平台可行性 [p3][p9]。
  3. 仅做 adapter 级验证不够，需覆盖从硅就绪到集群对接、PV exit 的全生命周期验证 [p8][p9]。
- 关键数据：
  - 无量化数据；给出 7 阶段部署流程：Silicon Readiness → ODM EVT/DVT/PVT → 平台/机柜集成 → 机柜部署 → LSG 资格 → Cluster Docking → PV Exit [p8]
  - 固件由 100G 时代单一 vendor image 变为多组件版本化 recipe（PDI、CMC、NMC、NIC images、PPK）[p6]
  - 验证覆盖：multi-host、multi-NIC、PCIe Gen5/Gen6、DDR5、液冷 [p4][p7]
- 提到的公司/客户/产品/标准：Microsoft、Cerberus（CMC）、PCIe Gen5/Gen6
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（800G 部署 7 阶段流程）

### P468 Plug-and-Play-ML-Pipelines-for-SONiC-On-Device-Intelligence-with-Advanced-Feature-Extraction
- 讲者/机构：Venkata Ravichandra M、Abed M Kamaluddin，Marvell | 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：SONiC]；次 [运维/可靠性/遥测]
- 核心主张：
  1. SONiC 已有 COUNTERS_DB、IPFIX、sFlow、gNMI 等原始遥测，但缺少把原始遥测转为特征向量并统一喂给模型的路径 [p5]。
  2. 三阶段 FE pipeline（Ingest→Extract→Publish），特征向量可按策略送往片上（毫秒级闭环）或片外（Kafka/gNMI/IPFIX，跨设备关联）推理，代码不变 [p7][p10][p11]。
  3. 运行于隔离容器（cgroup CPU/内存上限），不影响 BGP 等控制面与数据面，支持 warm/fast reboot [p12]。
- 关键数据：
  - 示例特征：drop_rate_1m 0.8%、queue_p95 740、link_flap_count 3（示意值）[p6]
  - 片上推理为毫秒级延迟、无网络往返（自报）[p10]
  - 推理引擎支持 ONNX Runtime、TFLite（自报）[p11]
- 提到的公司/客户/产品/标准：Marvell、SONiC、SAI、HFT、ONNX Runtime、TFLite、Kafka
- 首次/记录/SOTA 声明：无；路线图含 FE HLD 提案、SONiC VS 参考实现、Marvell 平台 SAI 支持 [p13]
- 推荐配图页：p6（原始遥测→特征→推理三层示意）

### P482 Storage-Track-Close
- 讲者/机构：Ross Stenfort，OCP Storage Project Lead | 类型：主题（闭幕）
- 方向归属（主/次）：主 [存储]
- 核心主张：
  1. 感谢 storage track 讲者 [p2]。
  2. 号召在月会提出想法、投稿 OCP Global、贡献 OCP [p3]。
- 关键数据：无
- 提到的公司/客户/产品/标准：无
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P484 Storage-as-a-Performance-Tier-for-LLM-Serving
- 讲者/机构：Joohee Lee、Donguk Moon，SK hynix | 类型：技术分享
- 方向归属（主/次）：主 [存储]；次 [推理/算力/经济性]
- 核心主张：
  1. Prompt caching 使 prefill 从计算受限变为数据搬运受限，KV 传输带宽决定 TTFT [p5][p16]。
  2. 充分利用 SSD 内外并行并做 I/O 优化后，SSD 承载 KV cache 可接近 DRAM 级 TTFT [p9][p16]。
  3. SSD 耐久是一阶部署约束，OP/ZNS/FDP 可显著降低容量需求；剩余 I/O 抖动指向 KV-aware 存储（KV SSD）[p11][p14]。
- 关键数据：
  - 引用：Anthropic 提供 5 分钟与 1 小时 cache TTL；OpenAI 扩展 prompt caching TTL 至 24 小时 [p3]
  - B200 服务器分层：HBM 140 GB（模型 50GB）、DRAM 375 GB、SSD 1~10 TB [p3]
  - Qwen3-14B（BF16），10 分钟 TTL 每 GPU 需约 781GB KV cache（Qwen-Bailian 匿名数据集，仿真/分析）[p3]；需求从约 348GB 上升至 781GB（看图）[p3]
  - 内存层级延迟：DRAM 80–140ns，本地 SSD 10–40us，远端存储 3–10ms（引用/概念）[p4]
  - 无复用 TTFT：A100 约 7s、H100 约 3.4s、GH200 约 2.1s；有复用：约 0.32 / 0.21 / 0.07s；对应 Link BW 32/64/450 GB/s（看图）[p5]
  - 测试平台：vLLM v0.9.1 + LMCache v0.3.1，H100 PCIe Gen5 x16，PCIe Gen5 NVMe，io_uring [p7]
  - 1→4 块 SSD 未优化时 TTFT 为内存基线 1.26x~1.92x；经 chunk size 与 io_uring 优化后为 1.07x~1.14x（实验）[p9]
  - ShareGPT 宏基准：SSD 与内存 TTFT 差 -3%~5%（QPS 0.1–0.5）（看图）[p9]
  - KV 写入流量每 GPU 最高约 57.5TB/天（Qwen3-14B）（实验/分析）[p11]
  - 满足耐久的最小容量：SLC 0.29 TB；TLC 14.4 TB（OP 后 4.8 TB）；QLC 28.8 TB（ZNS 后 8.8 TB）（看图）[p11]
- 提到的公司/客户/产品/标准：SK hynix、NVIDIA B200/H100/A100/GH200、vLLM、LMCache、Qwen3-14B、OpenAI、DeepSeek、Google Cloud、Anthropic、SNIA KV Storage API、ZNS、FDP
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（SSD vs 内存 TTFT 微/宏基准）；p11（SLC/TLC/QLC 耐久容量下限）

### P487 Creating-Aggregation-Pipelines-to-Conquer-Large-Telemetry-Challenges
- 讲者/机构：Jim Harford，Broadcom | 类型：标准进展（SCIM 工作流）
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  1. SCIM 工作流面向 10 万节点以上数据中心，先建协议无关的遥测架构，再映射到 Redfish/YANG/OpenTelemetry/Prometheus [p2][p3]。
  2. 遥测 pipeline 由 Leaf/Aggregation/Filtering/Reporting/Control 节点构成，通过时间、空间、上下文聚合与模式检测（阈值、尖峰、趋势、方差、卡死）在靠近源头处生成告警 [p4][p7]–[p19][p26]。
- 关键数据：
  - 目标规模：100,000 节点以上（规划）[p2]
  - 定义 Metric/Bundle/Super Bundle 数据结构，value_width 1/2/4/8 bytes，单位采用 UCUM [p20]–[p22]
  - 趋势检测用例含可插拔光模块 TX 激光功率漂移、液冷泄漏导致温度上漂 [p17]
- 提到的公司/客户/产品/标准：Broadcom、Redfish、YANG、OpenTelemetry、Prometheus、UCUM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（L/A/F/R/C 节点遥测流示意）

### P488 DMTF-PMCI-Enhancements-for-OCP-Hardware-Management
- 讲者/机构：Patrick Caporale（Lenovo）、Hemal Shah（Broadcom）| 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  1. MCTP、PLDM、NC-SI 持续扩展以覆盖 OCP 设备管理（新增 PCIe Gen7 VDM、Bulk Telemetry、Crash Log 等模型）[p6][p8]。
  2. USB 正成为 OCP 平台的 sideband 管理接口；DMTF 将发布"简化 MCTP"实现指南 [p7][p9][p10]。
- 关键数据：
  - PMCI WG >80% 规范已在 GitHub 开发，计划 2027 年约 100% [p5]
  - DSP0238 MCTP over PCIe VDM 支持 PCIe Gen7 [p6]
  - PMCI 测试服务目标 80–95% 共用代码，平台相关代码约 10% [p11]
  - DSP0280 v1.1.0 于 2026 年发布，测试服务与客户端代码开源 [p12]
- 提到的公司/客户/产品/标准：DMTF、MCTP（DSP0236/0238/0283）、PLDM（DSP0240/0248/0251/2070/2091–2094/0242）、NC-SI over Ethernet over USB（DSP0296）、SPDM、CXL FM API、OCP NIC、DC-MHS、DC-SCM、OAM/UBB
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（MCTP/PLDM 协议栈全景）

### P489 From-Lab-to-Fleet-A-Secure-Unified-Debug-Framework-for-Cloud-Systems
- 讲者/机构：Suresh Duthiraru（Microsoft）、Rolf Kuehnis（Lauterbach），协作 Sandesh Putturaya（Microsoft）、Matthias Zens（Lauterbach）| 类型：技术分享 + 标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：
  1. 交互式调试的瓶颈是互联网往返而非加密；把 Debug & Test Controller 放到 BMC 本地执行可恢复交互性 [p7][p8]。
  2. 以 OCP DC-SCM + OpenBMC 为调试网关、MIPI SPP/DoI3C 为传输、DMTF SPDM 做认证与授权，形成从实验室到机群的统一框架（OCP System Debug Spec v0.1）[p1][p11][p12]。
- 关键数据：
  - Cobalt 200 原型实测单步：JTAG 本地 14 ms、SPP/I3C 本地 10 ms、SPP/I3C 经互联网 4800 ms、BMC 内 DTC 经互联网 25 ms；读寄存器 0.3/0.2/40/21 ms；1KB 扫描链 0.31/2/360/22 ms（实验，看图）[p7]
  - OOB 管理网约 20 ms RTT [p8]
  - 一次真实会话 500–2,000 次单步：远程 40 min–2.7 h，本地 DTC 12–50 s，约 190× 加速（自报推算）[p18]
  - 管理控制器 BOM：低成本 RTOS BMC 约 \$3–8，完整 BMC（DC-SCM v1.2）约 \$8–20，自托管约 \$0（自报估计）[p20]
  - 研发阶段规模：EVT ~100 units，DVT ~100–1K，PVT >1K [p3]
- 提到的公司/客户/产品/标准：Microsoft Cobalt 200、Lauterbach TRACE32、Nuvoton BMC、DC-SCM v1.2、OpenBMC、MIPI SPP/DoI3C、DMTF SPDM/PLDM/Redfish、Intel At-Scale Debug、AMI MegaRAC、ASSET ScanWorks
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（四种调试路径延迟对比，对数轴）

### P492 Graph-Query-Language-APIs-for-OpenBMC-Metrics-OpenRMC-DM-as-a-Proxy-GraphQL-Server
- 讲者/机构：Avinash Natarajan、Navinsennivel Nallasivam，Celestica | 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  1. Redfish 在多机柜规模下过于"chatty"，且各厂商 Telemetry Service 支持不一致 [p2][p3]。
  2. 让 OpenRMC-DM 作为 GraphQL 代理：北向统一 GraphQL，南向按各 BMC 能力选最佳方式，无需修改厂商 BMC [p7][p9]。
- 关键数据：
  - 测试：2 BMC、30 chassis、390 sensors；Redfish 需 421 次调用、222.6KB；GraphQL 2 次调用、66.9KB（实验）[p11][p12]
  - 调用次数少 210×，响应载荷 227,951B→54,625B（4.2× less），总传输少 3.3×（实验）[p12]
  - 单个 sensor Redfish 响应约 450 字节，客户端仅需约 10 字节 [p12]
  - 未计 wall-clock 时间；DM→BMC 段未优化 [p10][p11]
- 提到的公司/客户/产品/标准：Celestica、OpenRMC-DM、Redfish、GraphQL、Redpath（DMTF DSP0285）、SONiC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（DM 北向 GraphQL / 南向多机制架构图，看图）

### P493 Hardware-Management-Project-Journey
- 讲者/机构：Jeff Hilland（Intel）、Hemal Shah（Broadcom）| 类型：标准进展（项目综述）
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  1. OCP Hardware Management 项目近十年，从服务器 Redfish profile 扩展到机柜/数据中心及组件 [p3]。
  2. OpenRMC-DM 将应对 AI 基础设施的物理/逻辑机柜范围、AI 驱动遥测，以及"光互连解耦架构"带来的新挑战 [p9]。
- 关键数据：
  - OpenRMC 规范 v1.3 启动，聚焦聚合、可组合性、遥测 [p9]
  - System GPU Management 推进 GPU Accelerator Management Interfaces Spec v1.1 [p10]
  - SCIM 面向 >100,000 节点 [p13]；RAS API 已发布两份规范 [p14]
- 提到的公司/客户/产品/标准：Intel、Broadcom、Redfish、OpenRMC-DM、AMC、SCIM、RAS API、Profiles（GPU、UBB、CDU、RDHx、浸没）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（Hardware Management 项目结构图）

### P494 Hierarchical-Device-Managers-to-manage-complex-Multi-Rack-systems
- 讲者/机构：Avinash Natarajan、Navinsennivel Nallasivam，Celestica | 类型：技术分享（提案）
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  1. 机柜级 OpenRMC-DM 代理聚合模式可递归扩展：L2 DM 管 L1 DM、L3 DM 管 L2，接口始终是标准 Redfish，靠 UUID 前缀命名空间解复用 [p7]。
  2. 每层在自身物理边界内做事件合并、根因推断、健康汇总，避免北向事件风暴 [p11]。
- 关键数据：
  - 示例层级：每 rack 30 BMC，每 pod 10 rack [p8]
  - SimpleUpdate 场景 1 pod / 10 rack / 300 系统：L3 跟踪 1 任务、L2 跟踪 10、L1 跟踪 30；总时间约等于单机柜更新时间（自报/设计推演）[p10]
- 提到的公司/客户/产品/标准：Celestica、OpenRMC 1.3、OpenRMC-DM、Redfish、SONiC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（DC/Pod/Rack 三级 DM 层级示例）

### P495 OBMF-Specifications-and-Workstream-Status-Update
- 讲者/机构：Janusz Jurski（Intel，OBMF WS 联席主席）、Mariusz Oriol（NVIDIA）、Ofer Yehielli（Google）| 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]
- 核心主张：
  1. OBMF-ICP 为 DC-SCM 上 BMC 与 HPM 上主机/设备之间的启动、配置、运行时通信提供厂商/CPU/物理接口无关协议 [p3][p4]。
  2. OBMF-ICP 与 USB 设备类定义一起"补齐统一 USB 设备定义的最后一块"[p9]。
- 关键数据：
  - OBMF-ICP 规范 rev 1.0.0 发布；OBMF-ICP over USB rev 1.0 发布；over MCTP（DSP0295）WIP [p5]
  - 工作流自 2025 Q2 起每周会议，成员含 Microsoft、Intel、AMD、ASPEED、Arm、Nuvoton、NVIDIA、Google 等 [p3]
  - 生态：AMD MI350P 实现 OBMF device，ASPEED AST2700/AST1040，NXP MCX-N9xx/i.MX95 等 [p11]；Innovation Village 7 个 demo [p12]
- 提到的公司/客户/产品/标准：DC-SCM 2.x/3.0、DMTF MCTP（DSP0283/0295）、OCP Recovery/Caliptra、OpenBMC、OpenSMA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（USB 上 OBMF-ICP 与 MCTP 共存协议拓扑）

### P496 OCP-Auxiliary-Management-Controller-overview
- 讲者/机构：Jeff Hilland、Gregg Shick，HPE | 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：
  1. 每种 PCIe/CXL 部件管理接口各异，AMC 规范作为 MCTP/PLDM/SPDM 的"profile"，让辅助设备以统一方式向 BMC 汇报 [p2][p3]。
  2. AMC 2.0 完整定义 SPDM 安全要求、强制 PLDM Type 7 文件 I/O 等，因新增必选项升主版本 [p7][p8]。
- 关键数据：
  - 无量化性能数据；AMC 2.0 新增 PLDM Type 2/5/6 要求（如 RDEOperationKill），AMC 可作 MCTP proxy [p9]
  - 参考实现：Google smc-common（基于 Zephyr RTOS）[p6]
- 提到的公司/客户/产品/标准：HPE、Google、Meta OpenBIC、Samsung DMC、Broadcom、Intel、Marvell、Microchip、Nvidia/Mellanox、DMTF Redfish Interop Validator、OCP Datacenter NVMe SSD Spec
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（AMC 与 BMC 关系示意）

### P499 Prescribing-remote-manageability-for-IT-OT
- 讲者/机构：John Leung（Intel）、Mike Raineri（Dell）| 类型：标准进展
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [底座-冷却]、[底座-电力]
- 核心主张：
  1. 用 OCP Redfish profile 规定 IT（服务器、NIC、GPU、交换机）与 OT（CDU、RDHx、电源架、PDU）管理接口 [p4][p5]。
  2. 用 AI 辅助编写、校验、修复 profile（HWLC、Neocloud 工作流），但 AI 生成的报告需大量人工核实 [p10][p11]。
- 关键数据：
  - 2026 年发布 Baseline Profile v1.1、Service Baseline v1.0、Ethernet NIC Profile v1.0 [p6]
  - Ethernet NIC Profile 被 Ultra Ethernet NIC 引用，经 mockup 与实物（如 Intel E835）验证 [p6]
  - Service Baseline 列出约 19 项管理任务及必选/推荐等级 [p8]
- 提到的公司/客户/产品/标准：Intel、Dell、DMTF Redfish Profile Creator、Interop Validator、ClusterMax、OCP DC Telemetry 工作流
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（OCP profile 继承关系图）
