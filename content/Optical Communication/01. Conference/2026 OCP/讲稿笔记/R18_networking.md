---
title: "R18_networking"
tags:
  - OCP2026
  - 讲稿笔记
---

# R18 笔记：networking

### P411 08_Operating Linear Pluggable Optics at Hyperscale From Link Management t
- 讲者/机构：Amin Yekani、Qing Wang（Meta Platforms，Optical Engineer）| 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：可插拔光模块/LPO/LRO]；次 [运维/可靠性/遥测]
- 核心主张：
  1. LPO 去掉模块内 retimer DSP，省掉在数百万链路上反复出现的功耗、发热与成本，代价是主机侧要承担均衡和故障定位 [p2]。
  2. 在同链路模式、现网条件下，linear 光模块的中断率和故障率都低于 retimed；模块级两者相当，收益来自架构（没有 DSP 就少一类故障）[p8]。
  3. AI 训练下可靠性指标应从"故障率"转向"中断率"（任何短暂链路事件都可能让训练回退到上一个 checkpoint）；光学上封装（NPO/CPO）后不可插拔替换，可靠性要求只会更高 [p7]。
- 关键数据：
  - 三年路线：OFC/OCP 2024 定义规格 → OCP 2025 产品化 → OCP 2026 规模可靠性数据；证据来自 100G/lane LPO，结论延伸到 200G/lane LRO/LPO、NPO [p3]（自报）
  - 规格：host/media 速率 2x400G、8x100G、1x800G；pre-FEC BER 目标 <3E-6；光纤预算 reach 500 m、IL 2.5 dB；TP1a/TP4a 采用 oif2021.405.11 [p4]（自报）
  - Tx FIR 标定"解耦交换机与模块贡献"已证明可行，但本次部署仍使用交换机+模块联合标定 [p4]（自报）
  - 现网 Setup 1：DSF fabric 的 DTSW–EDSW 一跳两端 LPO，2x400G FR4 / 1x800G 模式，4k 模块、4 个月生产，FBOSS [p5]（现网）
  - 实验室 Setup 2：~1k 模块在 MiniPack3（51T）上环回，2x400G，Diag OS [p5]（实验）
  - 现网：linear 比 retimed 中断少 2.0×、service-affecting 故障少 2.6×（每链路，retimed=1.0）[p8]（现网，看图）
  - 差距随机群成熟扩大：Apr–Aug 全记录 ~2×，最近 60 天 8.4× 更少中断 [p8]（现网，看图）
  - 实验室：8 lane、104 天光功率波动 ≤0.25 dB 峰峰、每 lane 漂移 ≤0.04 dB [p9]（实验）
  - 中位 pre-FEC BER ~1×10^-9；FEC bin typical 2 与 retimed 相同，worst 5（retimed worst 7）[p9]（实验，worst 值看图）
  - 0 次模块归因故障 / 2.96M link-hours [p9]（实验）
  - 固定风扇转速下：每模块功耗 −46%，温度低 17.5 °C [p9]（实验）
- 提到的公司/客户/产品/标准：Meta、FBOSS、MiniPack3、DSF fabric、OIF（oif2021.405）、LPO MSA、LRO、NPO
- 首次/记录/SOTA 声明：无明确"首次"表述；给出 LPO 与 retimed 在同链路模式下的现网可靠性对比
- 推荐配图页：p8（LPO vs retimed 中断/故障对比，8.4× 趋势）；p9（实验室 FEC 分布、功耗/温度、104 天光功率稳定性曲线）

### P412 09_SONiC for OTN Expanding SONiC and OCP SAI into Optical Transport Netwo
- 讲者/机构：Weitang Zheng（Alibaba Cloud，Staff Optical Network Engineer）| 类型：标准进展
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：DCI、ZR/相干]；次 [Out 后端网络：SONiC]
- 核心主张：
  1. OTN 用于 DCI 和 AI scale-across（多站点 GPU 集群作为单一逻辑训练系统），要求高带宽、低时延、高可靠 [p2]。
  2. 灰盒 OTN 设备的私有 NOS 造成碎片化、高 OpEx、补丁慢、无法定制（无法接入 AI agent 开发环）；用 SONiC + OCP SAI 做白盒 OTN [p4][p6]。
  3. SAI OTN 对象作为实验性对象，基于 OpenConfig YANG，与现有 IP/包 SAI 对象零重叠 [p9]。
- 关键数据：
  - SONiC OTN 工作组 2023 年 1 月成立，贡献者 Alibaba、Microsoft、Molex、Nokia、Cisco、Accelink [p5]（自报）
  - SAI 范围已扩展到 Packet ASIC、DASH、OCS、OTN [p9]（自报）
  - SAI OTN Phase 1（已交付）：OA、VOA，PR #2217 已合并；Phase 2（进行中）：完整 Open Line System（OCM、OTDR、WSS、APS、OSC、Optical Port）；Phase 3（计划）：Transponder、逻辑/光通道 [p10]（自报）
  - 新增 @precision 标签支持浮点（光功率、BER）[p10]（自报）
  - Syncd/SWSS/Mgmt 多个 PR 进行中；多槽 OTN 设备每块光线卡映射为一个 ASIC namespace [p11][p12]（自报）
  - 提供 SONiC OTN KVM 虚拟机镜像，可无硬件测试 CLI/Restconf/gNMI [p13]（自报）
- 提到的公司/客户/产品/标准：Alibaba、Microsoft、Molex、Nokia、Cisco、Accelink、SONiC、OCP SAI、DASH、OpenConfig YANG、gNMI、Restconf
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（SONiC for OTN 架构及扩展模块）；p10（SAI OTN 三阶段）

### P413 10_Switch Platform Architecture A Unified Network Switch Platform Referen
- 讲者/机构：Tao Ren、Tian Fang、Xu Wang（Meta）；Guohan Lu（Individual）；Ying Xie（Microsoft）；Yiyuan Huang、Zhiping Yao（Alibaba）| 类型：标准进展
- 方向归属（主/次）：主 [底座-机架/机械]（交换机平台层）；次 [Out 后端网络：SONiC]、[运维/可靠性/遥测]
- 核心主张：
  1. SAI 让数据面软件可移植，但交换机平台层仍私有、碎片化，新硬件上线需要数月重复工程 [p2]。
  2. OSPA 定义平台层（电源、传感/环境、库存、带外接口、固件维护、故障排查），不含路由协议与转发管理，NOS 中立、厂商中立 [p5][p6]。
  3. 选择 In-Host 模型（用主机 CPU 而非受限的 BMC 做平台管理）；新平台上线只需一份描述拓扑的配置文件 [p10][p14]。
- 关键数据：
  - OSPA Specification 1.0 已提交 OCP 正式评审 [p8]（自报）
  - 参考设计 2× 1GbE RJ45 前面板带外口，经 OOB switch 同时服务 BMC 与 Host CPU [p12]（自报）
  - I/O Bridge FPGA 经 PCIe 连接 Host CPU，下挂 I2C/GPIO/SPI/MDIO/LED 控制器，连接传感器、VRM、CPLD、EEPROM、TPM、Retimer、LED [p11]（看图）
  - 多级 ASIC 过热保护：温度传感器经 I2C 上报软件，同时 Alert Pin → CPLD → 直接关闭 ASIC 电压调节器 [p13]（看图）
  - 已有 OSPA 合规平台：Minipack3N（FBOSS）、Micas Bailly CPO Switch（SONiC）、NextHop NH-4210（FBOSS+SONiC 双 NOS）[p9]（自报）
- 提到的公司/客户/产品/标准：Meta、Microsoft、Alibaba、Accton、Arista、Celestica、Cisco、DTI、Micas、Nexthop、NVIDIA、Wistron、FBOSS、SONiC、SAI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（Host 子系统 IOB FPGA 拓扑）；p13（多级 ASIC 过热保护框图）

### P414 Beyond Traditional BGP- Decoupling Route Distribution for Large-Scale AI Clusters at Alibaba
- 讲者/机构：Eddie Ruan、Dennis Cai（Alibaba Cloud）| 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：SONiC]（路由控制面）；次 [运维/可靠性/遥测]
- 核心主张：
  1. 传统 BGP 下每台 TOR 要从所有 spine 学全部服务路由，状态爆炸；把服务路由分发与基础设施路由解耦（经 RR 或控制器）[p3]–[p5]。
  2. 阿里 HPN Pivot：环回地址作下一跳、集中路由聚合、两级递归转发，peer 数从 200 以上降到 4 [p6]。
  3. 任何 RR 故障都不应影响 AI 集群：每平面每协议 4 个 RR 实例、分布在不同服务器/机架/网络集群；引入 BGP Group GR 实现 RR 全失时"无头转发" [p8][p9]。
- 关键数据：
  - 算例：200 spine、500 TOR、每 TOR 200 条服务路由 → 服务路由 100K；传统方式每 TOR 需学 100K×200 = 20M 条路由信息；Microsoft 案例 1000×512 = 512K [p3]（自报算例）
  - Google/Cisco 方案：TOR 仅经 BGP 学基础设施路由 (m+n)×m = 700×200 = 140K，服务路由来自控制器或 RR [p4][p5]（自报算例）
  - Peer 数 "≈over 200 → 4"；RSC-BGP 4 实例，单栈 v4/v6，多跳 eBGP [p6]（自报；页内注明"架构示意图，非生产拓扑"）
  - RR 选型：虚拟 RR、靠近集群部署（保证 BFD 低时延与可靠）、Pivot Manager 自动化生命周期、不用 K8s [p7]（自报）
  - BGP Group GR：仅组内最后一个 peer down 才触发 GR；组内首个恢复/新 peer 重置 GR [p9]（自报）
  - 引用 Microsoft 去年数据：两层 Clos 容量 51.2T 交换机 800G 链路 1,638.4T、100G 链路 13,107.2T；BGP session 64→512；FRR 支持 514 sessions；单端口抖动数据面中断 <0.1 s、路由收敛 ~5 s；端口/BGP 启动 100–150 s [p2]（引用 Microsoft，看图）
- 提到的公司/客户/产品/标准：Alibaba、Microsoft、Google、Cisco、SONiC、FRR、BGP、BFD、SONiC routing WG
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（HPN Pivot 路由卸载架构，200→4 peer）；p2（Microsoft BGP 规模化回顾）

### P415 Bridging On-prem and Cloud - GPU Networking at Meta Scale
- 讲者/机构：Adi Gangidi（Technical Lead）、Carmen Au（Software Engineering Manager），Meta | 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：UEC/MRC/RoCE、拥塞控制、负载均衡]；次 [运维/可靠性/遥测]
- 核心主张：
  1. Meta 自 2025 年起在 on-prem 之外租用多家公有云 GPU；云上 GPU 型号、拓扑（ToR/多平面/轨道优化）、传输（IB/RoCE/EFA）、负载均衡和拥塞控制都各不相同 [p3]–[p5]。
  2. 通过设计阶段共享经验、在厂商处提前跑标准基准（写进合同）、turn-up 时跑负载代表性流量、打通遥测，把云上集群调到与 on-prem 一致 [p6]。
  3. 云上交换机对客户"不可见"，遥测需逐家 CSP 用合同约定；呼吁 OCP 标准化 RDMA 测试、负载测试与共享遥测 [p12][p14]。
- 关键数据：
  - Meta 已宣布本十年数十 GW；Prometheus ~1 GW（2026），Hyperion 扩到 5 GW；on-prem 自 2020，公有云自 2025 [p3]（自报）
  - 三家云举例：A：ECMP + 自定义可编程 CC + 有损激进重传；B：flowlet LB + DCQCN + PFC 无损；C：包喷洒 + Spectrum-X CC + PFC 无损 [p5]（自报）
  - 某 CSP 传输调整：自定义 CC → 无 CC；无流控 → PFC；无损类 0 → 2 类；重传由激进 → 放松；依据为 Meta 6 年无损 fabric 经验，结果与 on-prem 持平 [p7]（看图）
  - 基准：ib_write_bw/lat over IPv6，跨 Leaf/Spine/Super-Spine；NCCL/RCCL 集合通信从 16 到 512+ GPU [p8]（自报）
  - 负载多样性 3×，RDMA verbs 使用方 6× [p9]（自报）
  - 预训练/后训练/推理三类流量分别对应：多 collective 共享交换机→调 LB；incast→调 PFC buffer；远端 KV cache 慢接收端 PFC 扩散→调 CC [p10]（看图）
  - 32 并行 ring、每 ring 16 GPU 的 NCCL 测试：调 flowlet timer + CC 后峰值 bus BW 58.4 → 75.5 GB/s（大消息 +29%），run-to-run 波动基本消失 [p11]（实验/现网，看图）
  - 现在接入一家云比第一家 CSP 快 5× [p13]（自报，看图）
- 提到的公司/客户/产品/标准：Meta、Prometheus、Hyperion、InfiniBand、RoCE、EFA、DCQCN、Spectrum-X、NCCL、RCCL
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（多 replica 预训练调优前后 NCCL bus BW 对比，58.4→75.5 GB/s）；p5（三家云传输差异表）

### P416 Deep Buffers- The Essential Foundation for Scalable AI Training and Inference Infrastructure
- 讲者/机构：Hugh Holbrook（Arista，Chief Development Officer）、Golan Schzukin（Broadcom，Fellow）| 类型：技术分享（首页标题为 "Scaling AI Beyond the Data Center"）
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：深缓冲、长RTT拥塞控制]；次 [Out 后端网络：交换芯片、NIC]
- 核心主张：
  1. 电力与空间上限迫使 AI 集群跨园区；10 km 光纤带来数百 µs RTT，PFC/ECN 反馈来不及，浅片上缓存在突发下微秒级耗尽 [p2]。
  2. 分层混合缓冲：片上缓冲处理常见情况，HBM 深缓冲只在拥塞或 10 km 以上区域间链路启用，不必每端口都配 HBM [p3][p4]。
  3. 仿真显示缓冲 ≥1.5×BDP 时 FCT 接近理想、零重传，这一门槛与距离和 CC 算法（NSCC/RCCC）无关 [p9][p10]。
- 关键数据：
  - 现网分层：楼内浅缓冲无过订；楼间 <10 km 浅缓冲轻过订；区域间 10 km+ HBM 深缓冲、多倍 RTT headroom [p4]（自报，现网）
  - 10 km 链路算例：800 Gb/s、RTT 100 µs → BDP 10 MB/端口；固定硬件实际 200 MB/端口；HBM 最多 8.0 GB [p4]（自报）
  - 仿真设置：长距 2:1 过订，包喷洒 + NSCC/RCCC，缓冲从 3×BDP 扫到 0.005×BDP，距离 10/30/100 km [p8]（仿真）
  - 0.1×BDP 时 FCT 额外开销：500MB 流 20.6%、150MB 24.9%、50MB 31.5%；重传率 23.4% / 31.2% / 55.1% [p9]（仿真，看图）
  - 1.5×BDP 时 FCT 开销约 3%–8%，重传约 0% [p9]（仿真，看图）
  - 100T 交换机按 1.5×BDP 所需缓冲：10 km ~1.9 GB、30 km ~5.6 GB、100 km ~18.8 GB；浅缓冲交换机达不到 [p10]（仿真推算）
  - 系统组件：Broadcom Thor NIC（RCCC+ 速率调节、推测发送、硬件跟踪在途包）、HyperPort（端口合并提升 ECMP 熵）、包裁剪重注入替代 PFC、INT/CSIG 遥测 [p11]（自报）
  - 目标 1M+ GPU 区域集群 [p12]（自报）
- 提到的公司/客户/产品/标准：Arista、Broadcom、Thor、HyperPort、HBM、NSCC、RCCC、UEC、INT、CSIG
- 首次/记录/SOTA 声明：无；p14 声明性能数字为仿真结果
- 推荐配图页：p9（缓冲深度 vs FCT/重传率曲线）；p4（分层缓冲与 10 km 缓冲算例）

### P417 ESUN- Open Ethernet for the AI Scale-Up Era
- 讲者/机构：Manoj Wadekar（Meta，AI Network Technologist）、Pratik Marolia（Microsoft，AI System Architect）| 类型：标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：UALink/ESUN/SUE-T/NVLink]；次 [Out 后端网络：UEC]
- 核心主张：
  1. ESUN 目标是把 scale-up 互连从私有协议转向开放以太网，聚焦 fabric，给 GPU 侧留实现灵活性，并复用 IEEE、UEC 工作 [p5][p6]。
  2. Scale-up 是固定拓扑，用 ESUN 头替代 IPv4/UDP 提升小消息带宽效率；保留 ECN、COS、flow label、TTL 等多跳所需字段 [p7][p8]。
  3. 采用 UEC 定义的 LLR 与 CBFC，实现局部快速恢复、精确缓冲，从而简化传输、端点并允许浅缓冲交换机 [p9]。
- 关键数据：
  - Scale-up GPU 数 8 → 72 → 576 → 1K；每 GPU 带宽 450 → 1200 → 1800 GBps [p4]（自报）
  - 集群规模时间线：2023 年 128 → 2k → 4k → 8k（datahall）→ 24k（DC）；2024 年 129k（region）；未来 1M（multi-region）[p2]（看图）
  - ESUN 头替代 IPv4/UDP 节省 24–44 字节 [p7]（自报）
  - Wire efficiency（payload 32B / 64B / 256B）：Ethernet+IPv4 37.21% / 54.24% / 82.58%；ESUN 1.0 45.71% / 62.75% / 87.07%；ESUN 1.1 UFH_16 50% / 69.19% / 89.98%；4096B 时均 >98.7% [p11]（看图）
  - UFH 为 12 B 头，叠加在 Ethernet MAC 头上，含源/目的地址、DSCP、ECN、Hop Limit [p11]（看图）
  - IPG：IEEE 要求平均 12 B 帧间隙；提案只需 1 字节终止符，按 8B 边界实际 1–8 B [p12]（自报）
  - 时间线：2025.10 宣布；2025.12 成立；2026.03 ESUN 1.0 发布；ESUN 1.1 目标 2026.10–11（依赖 UEC）；2.0 待定 [p13]（自报）
  - ESUN 1.1 工作项：UFH 0.9、IPG 缩减 0.9 贡献给 UEC 1.1；低时延 FEC、Reduced Lane Mode、In-Network Collectives [p10]（自报）
- 提到的公司/客户/产品/标准：Meta、Microsoft、Marvell、Cisco、OCP ESUN、UEC、IEEE、LLR、CBFC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（ESUN/UFH 头结构与 wire efficiency 对比表）；p2（AI 集群规模演进时间线）

### P418 MRC- A Purpose-Built RDMA Transport for AI Training Networks
- 讲者/机构：Abdul Kabbani（Partner）、Wael Noureddine（VP），Microsoft | 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：UEC/MRC/RoCE、拥塞控制、负载均衡]；次 [Out 后端网络：NIC]
- 核心主张：
  1. ECMP 静态哈希造成热点；多路径应是传输层的响应式功能，负载均衡与拥塞控制必须协同设计 [p4]–[p7]。
  2. MRC 由 SMaRTT（窗口式、ECN+RTT+可选裁剪多信号 CC）和 ReSS（少量子流、随机重路由最拥塞子流）组成 [p8][p9]。
  3. 早期部署单一 NIC 厂商；推广需要多 NIC 互通，现有 MRC 规格在保留位、可靠性算法、RTT 测量上有空白；提出三级互通（线格式/算法/行为）并筹备 plugfest [p12]–[p16]。
- 关键数据：
  - 引用 Fungible FCP：all-to-all 下 fabric 时延 99p 10.5 µs、99.9p 13 µs [p6]（引用 Fungible）
  - Cluster A：NVIDIA GB200，跑 50K 与 75K GPU 训练作业；ConnectX-8 每 NIC 800 Gb/s，拆为 4×200 Gb/s 独立平面；两层 Clos（T0/T1）；Spectrum-4 与 Tomahawk-5 混合 [p10]（现网）
  - Cluster A 生产中 T0–T1 链路抖动每时段多在 2–8 次，峰值约 13 次；MRC 透明重路由，影响可忽略 [p10]（现网，看图）
  - Cluster B：加速 20 条链路故障实验，双向吞吐约 1,550 Gb/s，链路断开（约 22 s）到恢复（约 52 s）期间带宽基本不变 [p10]（实验，看图）
  - Level 3 互通要求：相同头字段、SMaRTT、ReSS、禁用 Go-Back-N、按包/连接 RTO、相同 cwnd 增减速率、相同 LB 链路故障反应时间 [p15]（自报）
- 提到的公司/客户/产品/标准：Microsoft、Fungible FCP、NVIDIA GB200、ConnectX-8、Spectrum-4、Broadcom Tomahawk-5、SMaRTT、ReSS、OCP networking
- 首次/记录/SOTA 声明：Fungible FCP 被称为"首个生产级包喷洒 DC 传输"[p6]（引用）
- 推荐配图页：p10（生产集群链路抖动与 20 链路故障吞吐曲线）；p15（MRC 三级互通要求表）

### P419 MetaRoCE in Software
- 讲者/机构：Ashkan Nikravesh、Yiorgos Nikolaidis（Meta Platforms，Software Engineer）| 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：UEC/MRC/RoCE、拥塞控制]；次 [Across：长RTT拥塞控制]
- 核心主张：
  1. MetaRoCE 是面向尽力而为以太网的可硬件卸载 RDMA 传输：只需 WRED 式 ECN 标记、QP 内多路径、SACK 选择确认、按 tag 的流复用、带内故障规避、Rate Control Notification 处理 incast、支持跨站点 [p2][p3]。
  2. 规格文本无法直接测试；做两个独立软件实现（libsoftmetaroce 纯用户态、dpdkmetaroce 内核旁路），互相对打作为"最终裁判"，实现过程中已反哺多处规格修正 [p5][p6]。
  3. 两个实现均以宽松许可开源，支持标准 verbs API，无需 RDMA NIC [p16]。
- 关键数据：
  - libsoftmetaroce：普通 UDP socket 上的完整传输实现（连接、可靠交付、多路径、逐路径 CC、重传）；一个新 CC 算法即一个 C++ 类，接口仅 sent/acked/lost 三个事件；wire envelope 支持 UDP、L2 以太网，预留 OCP ESUN 与 PSP [p7][p11]（自报）
  - 可按规则丢弃/延迟/复制/乱序任意包，确定性复现 [p12]（自报）
  - dpdkmetaroce 与 libsoftmetaroce 不共享代码；已在不止一类设备（含厂商 DPU datapath）上运行 [p13][p14]（自报）
  - CI 跑全部配对矩阵（socket-socket、DPDK-DPDK、交叉）[p15]（自报）
  - 未给出性能数字
- 提到的公司/客户/产品/标准：Meta、RoCEv2、DPDK、OCP ESUN、PSP、Keysight、AMD（@Scale 演讲讲者，p4 看图）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（MetaRoCE 相对 RoCEv2 的设计要点）；p15（双实现交叉验证流程）

### P420 Networking In Silo is Not Enough - Building End-to-End Automation for AI Factories the IREN Use Case
- 讲者/机构：Amir Elbaz（Founder & CEO）、Kim Kwa（Principal Architect）；所属机构首页未写明（内容为 IREN 案例，平台 "BE" 未展开全称）| 类型：厂商/用户案例
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [Out 后端网络：SONiC]
- 核心主张：
  1. 网络问题在 AI 时代影响被放大，网络自动化必须与整个基础设施栈打通 [p5][p6][p11]。
  2. 意图（RA 或设计 JSON）+ 实时拓扑发现 + 智能体 AI（MCP）可自动发现漏接、错接线缆；有编码化 RA 才能自动告警漂移 [p7][p8][p10]。
  3. 光纤质量与无损配置是 Day 0 工作：CRC/FEC 基线告警先暴露脏/损光纤，再统一推送 RoCE 配置（队列、ECN、PFC）[p9]。
- 关键数据：
  - IREN：>4.5 GW 已锁定电力，810 MW 运营中数据中心，\$2.3bn 已签约 AI 收入，2,000+ 人团队 [p2]（自报）
  - 站点：Sweetwater 1&2（TX）2,000 MW、Oklahoma 1,600 MW、Childress（TX）750 MW、Mackenzie BC 80 MW、Prince George BC 50 MW、Canal Flats BC 30 MW；Oklahoma 2,000 英亩、2028 年起供电、到网络枢纽 <6 ms [p3]（看图）
  - 部署：Cisco 迁移到 SONiC+Broadcom；Dell SONiC on Spectrum-X；AMD GPU + Broadcom ASIC + SONiC；裸机到可出 token 网络 <2 小时 [p4]（自报）
  - 平台宣称 MTTR 降低 95%、100% 数据隐私（本地 LLM）[p12]（自报，未给条件）
  - 节点功率从 5–10 kW 到 80–140 kW [p11]（自报）
  - 下一批部署：Childress / MacKenzie 采用 NVIDIA Spectrum-X、NCP RA 2.1.2 [p10]（自报）
- 提到的公司/客户/产品/标准：IREN、NVIDIA、Broadcom、AMD、Cisco、Dell、HPE、Supermicro、Micas、Celestica、SONiC、Spectrum-X、MCP、DSPy、MLflow
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（IREN 站点与电力分布地图）；p7（自动化-可观测-智能体平台结构）

### P421 Optically-Accelerated AI Clusters Enabled by Interoperable Multi-Vendor OCSs- Use Cases
- 讲者/机构：Iwan Kartawira（iPronics）、Kazuaki Ueda（KDDI）、Kazuya Anazawa（NTT）| 类型：技术分享/标准进展
- 方向归属（主/次）：主 [Out 后端网络：OCS]；次 [Up 机柜/超节点：CPO/NPO/XPO]、[运维/可靠性/遥测]
- 核心主张：
  1. AI 集群面临带宽/功耗墙、可靠性瓶颈和厂商锁定；提出 CPO + OCS + SDN 的"光加速 AI 集群（OAI）"，EPS 负责细粒度逻辑路由，OCS 负责粗粒度物理连接 [p3]–[p6]。
  2. 用例 1：OCS 层 + SDN 实现从 1:1 保护到 1:N 全局备件池的故障恢复；用例 2：按 All-Reduce/All-to-All 通信模式重构光连接，旁路 leaf/spine EPS [p8][p9]。
  3. 缺口：OCS 统一控制面、AI 流量可见性、光切换暂时断链对 RoCEv2 的影响（需与 NCCL 协同）；OCP-OCS YANG 让 SDN 控制器无需逐厂商翻译 [p10][p11]。
- 关键数据：
  - 131,072 GPU 集群 MTBF = 15 分钟 [p3]（引用 arxiv 2410.21680）
  - MTBF 随规模：8 GPU 47.7 天；1,024 GPU 7.9 小时；16,384 GPU 1.8 小时；131,072 GPU 15 分钟 [p16]（引用 arxiv 2410.21680，看图）
  - 电互连 >200G/ch：<1.5 m、<100 XPU、~2 pJ/bit（DAC）/ 2–5 pJ/bit（ACC、AEC）；光可插拔：>10 m、>1,000 XPU、10–15 pJ/bit [p16]（自报/引用，未注来源）
  - EPS 单 ASIC 功耗：2018 12.8T 350–400 W；2020 25.6T 450–500 W；2022 51.2T 700–800 W；2024 102.4T 900–1000 W [p16]（自报）
  - 演示：2 台 51.2T（TH5 示例）包交换 + 8 家厂商 OCS（Vendor A–H），全部经 gNMI/YANG 由 NTT SDN 控制器统一控制，演示备件池故障恢复，计划在 OFC2027 展示 [p12][p13]（自报，计划）
  - OCP-OCS YANG Model R1.0 已发布，R2.0 与开源 SDN 控制器为后续工作 [p13]（自报）
- 提到的公司/客户/产品/标准：iPronics、KDDI、NTT、IOWN Global Forum、NEDO（JPNP20017）、OCP OCS 子项目、gNMI、YANG、NCCL、RoCEv2、Tomahawk 5
- 首次/记录/SOTA 声明：称 OFC2027 演示为"首次在 OAI 中用互通多厂商 OCS 演示故障恢复"[p12]（自报，尚为计划）
- 推荐配图页：p12（多厂商 OCS 互通演示拓扑）；p16（电/光互连限制、EPS 功耗、MTBF vs GPU 数）

### P422 SRv6 Deployments in Scale-Out and Scale-Across Networks
- 讲者/机构：Clarence Filsfils（Cisco Systems）、Guohan Lu（OpenAI）| 类型：技术分享
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：SRv6]；次 [Out 后端网络：UEC/MRC/RoCE、负载均衡]、[Up 机柜/超节点]
- 核心主张：
  1. 传统栈在不同域用不同 shim（IB、VxLAN、MPLS），SRv6 uSID 把 128 位目的地址变成有序指令列表，端到端跨域 [p3][p4]。
  2. AI 后端用 SRv6 做源路由：源 NIC 封装 uSID 列表，交换机严格源路由转发（丢包时裁剪），目的 NIC 解封装；与 MRC 结合实现确定性路径与快速绕障 [p10][p11]。
  3. Scale-up 也需要低开销、单头、原生严格源路由、高 radix（>576）[p15]。
- 关键数据：
  - DA 中可放 6 条 uSID 指令，现有部署都少于 6 条 [p4]（自报）
  - 公开参考：OpenAI MRC AI 后端（GPU-GPU 确定路径）、Nebius AI 前端（无状态防火墙服务插入）[p5]（引用）
  - Microsoft Fairwater 多平面设计最多 524,288 GPU [p9]（引用 Microsoft）
  - 一台 T1 停止转发事件：生产作业 75K GPU，约 25% QP 受影响，约 580K 包被丢；MRC 移除该路径后吞吐恢复，之后交换机重启 [p13]（现网，看图）
  - SONiC 中 SRv6 配置：SRV6_MY_LOCATORS / SRV6_MY_SIDS 表，经 bgpcfgd → FRR；示例 sid fcbb:bbbb:20::/48 behavior uN [p12]（自报）
  - Scale-up 要求对 32/64/128 B 包保持高效 [p15]（自报）
- 提到的公司/客户/产品/标准：Cisco、OpenAI、Microsoft Fairwater、Nebius、Meta、Alibaba、SRv6 uSID、MRC、SONiC、FRR、MPLS、VxLAN、InfiniBand
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（T1 失效事件：75K GPU、25% QP、580K 丢包及恢复时间线）；p11（AI 后端 SRv6 封装转发流程）

### P423 Scaling AI Beyond the Cloud Boundary- High-Capacity Interconnects Between Hyperscalers and GPUaaS
- 讲者/机构：Anish Narsian（Microsoft，Principal Software Engineer）、Krithika Moorthy（Cisco，Director Product Management）| 类型：技术分享（含厂商产品）
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：DCI、深缓冲]；次 [Out 后端网络：SONiC]
- 核心主张：
  1. 电力、空间、GPU 交期使超大云租用 NeoCloud GPU，数据和服务留在云内；需要的是"服务可达性的 DCI"，而不仅是包的 DCI [p2]。
  2. Tier0-Edge 作为 underlay/overlay 拼接点，需要多租户隔离、隧道/路由规模、高密 ECMP 与一致性哈希、可编程报文改写、控制面规模、确定性恢复与深缓冲 [p3][p7][p8]。
  3. 请 OCP 社区在路由下发速度、重启后配置回放、BGP 规模（>1.5K）、SAI/SONiC 报文行为、DPU 流卸载到 NPU 上协作 [p13]。
- 关键数据：
  - 256K VXLAN 隧道下一跳（交付角色），目标 1M 级；2048 路隧道 ECMP；每 VNET 动态 BGP 2K+ sessions [p4]（自报）
  - 内层 SMAC/DMAC 与外层 VNI 按路由改写 >250k 规模；overlay→underlay 路径数 2k+ [p8]（自报）
  - Cisco 8223 / Silicon One P200：51.2 Tbps 固定系统、64×800G、3RU、深缓冲、MACsec、支持 ZR 光；自称最省电的 51.2T 深缓冲路由器 [p4]（厂商自报）
  - Edge 与 NeoCloud Spine 间为启用 MACsec 的长距 400/800GbE 全互联 [p5]（看图）
  - NeoCloud 侧 DPU 数量 1000+ [p7]（自报）
  - SONiC 路由需求：1.5K+ BGP sessions [p12]（自报）
- 提到的公司/客户/产品/标准：Microsoft、Cisco 8223、Silicon One P200、SONiC、SAI、VXLAN、VRF、MACsec、P4、gNMI、FRR、ZR
- 首次/记录/SOTA 声明："Most power-efficient 51.2T deep-buffer router" [p4]（厂商自报）
- 推荐配图页：p5（Tier2/Tier0-Edge/NeoCloud 物理架构）；p11（T0-Edge SONiC 软件与 SDN 编程路径）

### P424 Scaling AI Infrastructure Across DC and Beyond- Meta's Journey with BAG
- 讲者/机构：Jalpa Patel（TPM）、Hany Morsy（Network Engineer），Meta | 类型：技术分享
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：DCI、ZR/相干、深缓冲]；次 [Out 后端网络：负载均衡、交换芯片]
- 核心主张：
  1. BAG（Backend Aggregation）是集中式 L3 路由 super-spine，把多个 L2 fabric（DSF、NSF 均可）连成一个跨 on-prem 与租用站点的大集群，全程标准以太网 [p3][p5]。
  2. 站点间采用 hub & spoke（链路 O(N)）、按平面一对一连接；选深缓冲、信用转发 ASIC（J3 级）支撑长距 RoCEv2；FADT 多 profile 按距离分配 headroom；WECMP 感知 L2 内部故障 [p7]–[p11]。
  3. BAG 容量由模型副本决定：副本放在 L2 内用非阻塞网络，跨副本 DP 用 AllReduce Ring 走 BAG [p12]。
- 关键数据：
  - Prometheus：1 GW 集群，位于 New Albany, OH，跨多个子区域，含传统楼宇、防风雨户外帐篷、相邻托管设施 [p4]（自报）
  - NSF：每 L2 fabric 最多 ~21K GPU；Pod 内外均非阻塞；每 Pod 9 RTSW + 8 FTSW + 3 GPU 机柜；8 个 spine 平面，每平面 54 STSW；跨 L2 过订 ~5:1 [p6]（自报）
  - 图中：BAG 共 52 个平面、每平面 10 台；Cross-L2 Oversub 4.98:1；STSW 4.8:1；RTSW/FTSW 1:1，400G 下联/上联 [p6]（看图）
  - BAG-to-BAG：同编号 BAG 间 N×800G；较大站点多出的 BAG 只承载本地 L2 [p7]（自报，看图）
  - 光模块混用：FR4 ≤3 km、LR4 ≤10 km、ZR+ ≤1000 km [p10]（自报）
  - BAG-to-BAG 容量：无光保护时 (B + buffer) × 2，B 为 AllReduce Ring 所需最小 Pbps [p12]（自报）
- 提到的公司/客户/产品/标准：Meta、Prometheus、DSF、NSF、Jericho3（"J3 Class"）、FADT、WECMP、DLB、RoCEv2、FR4/LR4/ZR+、SAI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（NSF L2 fabric 与 BAG 平面拓扑及过订比）；p7（BAG-to-BAG 平面连接示意）

### P425 Srv6 powered backbone networks
- 讲者/机构：Jasmeet Bagga（Software Engineer）、Andrey Golovanov（Network Engineer），Meta | 类型：技术分享
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：SRv6、长RTT拥塞控制]；次 [Across：深缓冲]
- 核心主张：
  1. Ring：把区域内多个各存一份数据的站点变成共享存储池，"副本变成算力"，本地读变成骨干流量；RBB（区域骨干）承载这些流量 [p3][p4]。
  2. Ring 带宽约为 EBB 的 10 倍，只有 DC 级密度设备能达到每瓦要求，所以 RBB 浅缓冲是"继承的，不是选择的"；靠 ECN + 自研 GLIDE 让浅缓冲长距可行 [p5][p6]。
  3. 已大规模运行 MPLS SR TE 仍选 SRv6：Olympic QoS 需要 6 类严格优先级，MPLS TC 3 bit 只能编码 4 类，IPv6 TC 8 bit 可以编码全部 6 类 [p7]。
- 关键数据：
  - Ring RTT 1/5/10 ms；RBB 64 个并行平面，平面内站点全互联 [p4]（自报）
  - 浅缓冲用于 800G-ZR+ 跨度到 650 km [p5]（自报，现网）
  - GLIDE 测于 5 ms 单向：达到 70% 链路利用率目标，常态仅占 ~7% 缓冲；4.5:1 incast 才会填满缓冲（32–53 MB）[p6]（实测，看图）
  - 数据面：一个地址 6 个 uSID 槽，每跳 End.uA 移位 16 bit，End.DT46 解封装；超 6 跳用 End.B6.Encaps.Red 拼接；每邻接一条 mySID 表项，不是每路径一条 [p8]（自报）
  - 控制面：每 RBB 平面一个控制器，每 30 秒用 5 个调用编程全部交换机（addMySidEntries 等）[p9]（自报）
  - 时间线：2025.12 Rings 设计（深缓冲）→ 2026.02 转向浅缓冲 + FBOSS → 2026.07 首个 RBB 站点 → 2026.08 首个长距站点 → 2026.10 首个 SRv6 TE 站点 → 2026.12 计划扩展；转向到首站 5 个月 [p10]（自报）
  - 首批 RBB 站点基于 SAI + Cisco Silicon One [p10]（自报）
  - SAI 缺口：FRR 无"被监控对象 down"定义；不支持基于类的转发 [p11]（自报）
- 提到的公司/客户/产品/标准：Meta、FBOSS、SAI、Cisco Silicon One、GLIDE、SRv6 uSID、MPLS SR TE、800G-ZR+、RFC 5129、RFC 6040
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（GLIDE：70% 链路利用、~7% 缓冲）；p4（RBB/EBB 与 Ring 结构）

### P426 Standardizing Ethernet Scale-Up Validation- Test Strategy and Current Progress on LLR-CBFC
- 讲者/机构：Haiyang Zheng（Alibaba Cloud）、Daisy Sun（Keysight Technologies）| 类型：标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：UALink/ESUN/SUE-T/NVLink]；次 [Out 后端网络：SONiC]
- 核心主张：
  1. LLR（链路级重传）与 CBFC（信用流控）落地难点：与 RTT 相关的信用/重传缓冲大小、参数耦合、边界场景（poison CRC、N:1 incast 公平、信用更新丢失）、互通数据不足 [p6]。
  2. 用 SONiC Ranking Test（SAI 配置）+ Keysight 测试仪（注入流量与故障）+ 设备遥测交叉验证，形成标准测试 [p7]。
  3. 信用上限需按链路距离和小帧线速配置；端口级信用共享没有 VC 隔离 [p13][p14]。
- 关键数据：
  - 测试拓扑：Keysight INPT 800GE、4×400GE、阿里以太网 scale-up 交换机，800G 转 2×400G AOC 10 m [p10]（实验）
  - 交换机 22 个用例（CBFC 12 + LLR 10）全部通过 [p11]（实验）
  - LLR-09（20 m 线缆、无链路错误、64–9216 B 帧扫描）：线速、零丢包，L1 线速利用率约 99.61%；交换机转发时延 299–330 ns，端到端（含线缆与光模块）650–710 ns，抖动 <31 ns [p12]（实验）
  - LLR-10（注入 FEC 错误，混合 LLR/非 LLR）：LLR 流量重传后无丢失、非 LLR 有丢失；应用侧时延增加超过 1200 ns [p12]（实验）
  - CBFC incast：2:1 时两发送端各约 49.95%、接收 99.88%；3:1 时各约 33.30%、接收 99.88% [p13]（实验，看图）
  - CBFC-12 信用上限：500 m、64 B、RTT 5,000 ns → 7,825，Rx 99.99%；500 m、9,216 B → 6,240，99.65%；10 m、64 B、RTT 100 ns → 1,990，99.99%；10 m、9,216 B → 1,875，99.65% [p13]（实验）
  - CtlOS 带宽开销典型间隔下约 0.38% [p14]（实验）
  - 端点 IP（UniVista 预硅仿真平台）：LLR 10 项全过；CBFC 9 项通过、3 项未完成（不支持 IPv6、incast 待三方联测）[p15]（实验）
  - 测试规范：SONiC Ethernet Scale-Up Test Standard PR #2389；测试报告 PR #2596；开源测试框架 2026 Q4 [p7][p16]（自报）
- 提到的公司/客户/产品/标准：Alibaba、Keysight、Broadcom、UniVista、ESUN、UEC、SONiC、SAI、LLR、CBFC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（LLR 帧长扫描时延/吞吐表）；p13（CBFC incast 分布与信用上限表）

### P427 Standardizing OCS Interfaces for Seamless Integration
- 讲者/机构：Richard Yu、Brian O'Connor（Google，Staff Software Engineer），与 OCP OCS 工作组合作 | 类型：标准进展
- 方向归属（主/次）：主 [Out 后端网络：OCS]；次 [运维/可靠性/遥测]
- 核心主张：
  1. OCS 与流量无关（兼容未来速率与协议）、无 O-E-O 转换、低时延、低成本；技术路线有机械手、光束偏转、硅光 [p2]。
  2. 用 OpenConfig YANG + gNMI 复用现有非 OCS 专用的遥测与配置，只对 OCS 特有部分做修改 [p4]–[p7]。
  3. 规格需覆盖不同技术的差异：任意对任意 vs 部分对部分、快/慢切换、主动/被动维持链路、重启后连接行为（Break/Recover/Maintain）[p9]。
- 关键数据：
  - OCS 功耗低于传统电分组交换机的 5% [p2]（自报）
  - 新 YANG 模块 ocp-oc-optical-switch：bidirectional、cold-boot-recovery {MAINTAIN, REMAKE, REMOVE}、port-groups [p10]（自报）
  - ocs-port 组件：status {OFF, BLOCKED, FAILED, TUNING, TUNED, UNKNOWN}、输入/输出光功率 dBm、可纠/总错误计数 [p11]（自报）
  - 连接管理模块 oc-optical-switch-connections：连接状态 {CONNECTED, CONNECTING, DELETING, FAILED, INVALID} [p12]（自报）
  - OCS Interface Spec v0.8，9 月初提交 OCS 工作组，已在 GitHub 公开 [p14]（自报）
  - 组播、单向等少见特性尚未完全覆盖 [p9]（自报）
- 提到的公司/客户/产品/标准：Google、iPronics、Lumentum、Huber+Suhner、Telescent、OpenConfig、YANG、gNMI、OCP OCS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（OCS 基本操作的技术差异）；p10（ocp-oc-optical-switch YANG 树）
