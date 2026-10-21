---
title: "R13_expo-hall-sessions"
tags:
  - OCP2026
  - 讲稿笔记
---

# R13 笔记：expo-hall-sessions

### P291 02_Aivres Liquid-Cooling AI Data Center Solutions Based on NVIDIA GPUs, p
- 讲者/机构：William Ye，AIVRES R&D Department | 类型：厂商展区
- 方向归属（主/次）：主 [底座-冷却]；次 [底座-机架/机械]、[推理/算力/经济性]
- 核心主张：
  1. 液冷 AIDC 需从冷源、CDU、二次回路到监控平台整体交付，以 POD（单 POD 16 柜）为部署单元 [p4]。
  2. 小项目用机柜内 CDU 快速交付，大型新建数据中心用列间 CDU 保高可用 [p22]。
- 关键数据：
  - 兆瓦级 CDU 额定换热 ≥1200 kW（一次侧 EG25 41℃进/54℃出，二次侧 PG25 45℃供/65℃回），二次泵流量 ≥1200 L/min，尺寸 900×1200×2200 mm [p6]（自报）
  - 监控平台可按服务器热/功耗调节单柜流量，最多降 50% [p9]（自报）
  - KRS8000V4（VR NVL72）：48U，36× Vera + 72× Rubin，GPU TDP MaxQ 1800 W / MaxP 2300 W；HBM4 共 20.736 TB；整柜 TDP ~187/~227 kW；96% 液冷 + 4% 风冷；重 1,843.4 kg；4× 110 kW power shelf [p13]（自报）
  - 计算托盘 E/W 网络 4× CX9，8× OSFP，每 GPU 1600GbE；N/S 为 BF4 2×400G [p14]（自报）
  - KL2288 9 节点/柜 TDP 216 kW、KL3288 8 节点/柜 TDP 192 kW，配 250 kW CDU [p21]（自报）
  - 机柜内 CDU 与列间 CDU 成本分界：<8 柜 vs >16 柜；8×16 柜 POD 施工期"数天" vs 1–2 个月 [p22]（自报）
  - 欧洲案例：20 MW、约 100 柜、6144 颗 B200、3 POD（每 POD 32 柜 + 3 CDU 2+1），60 天交付 [p24]（现网/自报）
- 提到的公司/客户/产品/标准：NVIDIA VR NVL72、HGX Rubin NVL8、Vera、CX9、BF4、Q3400 IB XDR、VAST、WEKA、MGX 1.2 Rack、DC-SCM；Aivres KRS8000V4、KL2288、KL3288、CU1200A4、CU150A5
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（VR NVL72 整柜规格表）；p21（三种 HGX Rubin 机柜配置与功耗）

### P293 05_From Silicon to Rack Arm and Meta Scaling AI Infrastructure Through OC
- 讲者/机构：Prasanna Jayaraman（Arm，Solution Architect）、Damien Chong（Meta，Hardware Engineer） | 类型：厂商展区
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [底座-机架/机械]、[In 封装内：chiplet]
- 核心主张：
  1. 性能/功耗/效率越来越在系统层决定，需芯片—服务器—机柜协同设计 [p2]。
  2. 一份 OCP 对齐的参考设计可少量修改复用到多个 Meta 平台 [p6]。
- 关键数据：
  - Arm AGI CPU 1OU 双节点参考服务器：136 个 Neoverse V3AE 核，12 DDR5 DIMM 至 8400 MT/s，96 lanes PCIe Gen6，CXL 3.0 [p4]（自报）
  - "2x performance at scale"（机柜级优化，脚注条件未在文字层给出）[p5][p11]（自报）
  - Meta Yosemite V5：1OU 半宽，12ch DDR5 8000，每机箱 6 台服务器 [p7]；Meta Rainier HPM：DC-MHS SDNO B305 兼容，PVT 后贡献 OCP [p8]（自报）
- 提到的公司/客户/产品/标准：Arm、Meta、ORv3、DC-MHS、DC-SCM 2.0/2.1、OCP NIC 3.0、OPF、OpenBMC、EDK2、FCSA、SBSA、SBMR、ADAC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（参考服务器规格与 OCP 标准对齐清单）

### P296 09_MetaRoCE Rethinking RDMA for the AI presented by Meta
- 讲者/机构：Arvind Srinivasan（Meta）、Balakrishnan Raman（AMD）、Sandeep Nagaraja（Meta） | 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：RoCE、拥塞控制、负载均衡、NIC]；次 [Across：长RTT拥塞控制]
- 核心主张：
  1. MetaRoCE 是多路径 RDMA 传输：单 QP 跨多条路径喷洒，按路径做可靠性与拥塞控制，容忍丢包与乱序，只依赖商用以太网交换机的 ECN + ECMP，无需 trimming、自适应路由或 INT [p4][p5]。
  2. PFC、go-back-N 和重排缓冲不可扩展；改为"排序完成而非排序投递"（乱序放置、无重排缓冲），丢包用 SACK 检测 [p5]。
  3. 同一传输同时覆盖 scale-out 与 scale-across（长距离跨站点），并以开源规范 + 参考软件 + 合规测试推动成为 OCP 多厂商标准 [p9][p13][p14]。
- 关键数据：
  - 网络效率 >90%（非阻塞方式）[p3]（自报）
  - QWND = ΣPWND[p]；AIMD 更新，ECN 标记与 N 个包丢失触发乘性减 [p6][p7]（自报，机制）
  - Scale-out：RTT 5–15 µs，Max Cwnd ~75，Max Path ~12（4k MTU），线速 [p9]（自报）
  - Scale-across：RTT 常达毫秒级（即 50–100x），示例 RTT 1.5 ms；Max Cwnd 3500–7000，Max Path ~30–50（4k MTU），线速 [p9]（自报）
  - Incast：接收端速率提示（RCN）示例为每发送端 200 Gbps [p10]（自报）
  - 多平面 FPF 网络：每 AMD AI-NIC 8×100G 不相交平面（Plane 0–7），PCIe Gen6 [p11]（自报）
  - AMD 可编程 AI NIC：P4DMA + P4NET 可编程流水线，800 Gbps 上行 [p8]（看图）
  - 64 GPU 集合通信完成时间 vs RoCEv2：AllReduce 全部消息规模均更快，小消息（≤32KiB）约 -20%~-27%，大消息（2–16GiB）约 -3%~-5%；All-to-All 多数中小消息约 -15%~-21%，但 0B、1MiB、32MiB、8–16GiB 为正（约 +6%~+19%，变慢），64MiB 最大约 -28% [p12]（看图，读柱估计）
  - 加速器规模 2024→2030 约 10x（示意图，无绝对值）[p2]（看图）；"今天数十万加速器，按百万设计" [p2]（自报）
- 提到的公司/客户/产品/标准：Meta、AMD（Programmable AI NIC）、RoCEv2、ECN、ECMP、PFC、SACK、OCP
- 首次/记录/SOTA 声明：无明确"首次"声明；称为面向 Meta 网络端点与 AI 加速器优化的 RDMA 传输 [p3]
- 推荐配图页：p12（MetaRoCE vs RoCEv2 集合通信完成时间柱状图）；p9（scale-out vs scale-across 的 RTT/cwnd 参数对比）；p6（多路径 QWND/PWND 结构）

### P298 A-Pathway-to-224-448-Gbps-Copper-and-Optical-Connectivity-in-AI-Infrastructure-presented-by-Samtec
- 讲者/机构：Matthew Burns，Samtec Director, Technical Marketing | 类型：厂商展区
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆、CPO/NPO]；次 [Out：可插拔光模块/LPO]
- 核心主张：
  1. AI 系统拓扑需要更多外部线缆，不同距离对应 DAC/ACC/AEC/LPO/AOC 不同方案 [p2][p3]。
  2. 同一连接器同时承载铜（scale-up）与光（scale-out）；Open CPX MSA 提供多源、不需新压缩硬件的 CPO/NPO 通用插座 [p4][p8]。
  3. 448 Gbps 共封装铜互连 PoC 在本届 OCP 演示 [p13]。
- 关键数据：
  - 典型距离：机柜内 ~2m、相邻柜 ~3–5m、柜到柜 ~7m、更大集群 ~10m+ [p2]；DAC ~2m、ACC ~5m、AEC ~7m、LPO ~50m、AOC ~100m+；延迟/功耗/成本随距离增加 [p3]（自报/看图）
  - Eye Speed twinax：skew ≤1.75 ps/m；插损 14.3 dB（32 AWG，1 m，56 GHz）；92 Ω；适用 224+ Gbps PAM4 [p5]（自报）
  - 100T 芯片：Co-Packaged 方案 95×95 封装 vs Near Chip 方案 90×90 封装（连接器移到 PCB）[p6]（看图）
  - Open CPX Type-1：6.4 Tbps/插座，64 DP/32 lanes @200G，高速插座 10 mm 叠高，<15 mm beachfront [p9]；Type-2：7.2 Tbps/插座，72 DP/36 lanes @200G，7 mm 叠高，<16 mm beachfront [p10]（自报）
  - Open CPX MSA 2026年3月成立，2026年9月成员超 50 家；Rev 1.0（2026.9，32/36×200G）→ Rev 1.1（2027.3，铜介质、Type 3）→ Rev 2.0（2027.6，64/72×200G）→ Rev 3.0（2027末/2028初，N×400G）[p12]（看图，预测）
  - 448G PoC：Si-Fly HD 共封装系统，两个基板插座，1.0 m EyeSpeed 线缆，支持 PAM4/PAM6 [p13]（实验/演示）
- 提到的公司/客户/产品/标准：Samtec Si-Fly HD、Flyover OSFP、Eye Speed；Open CPX MSA；CPO/CPC、NPO/NPC
- 首次/记录/SOTA 声明：称 Si-Fly HD 共封装为"Lowest loss signal transmission" [p4]（自报，无对比数据）
- 推荐配图页：p12（Open CPX MSA 时间线）；p3（各类线缆距离与代价对比）；p7（同一插座铜/光并存的渲染图）

### P299 Any-Rack-Everywhere-Future-Readiness-for-the-800-VDC-Transition-presented-by-Vertiv
- 讲者/机构：未见（Vertiv）| 类型：厂商展区
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. 难以改动的固定接口（总电力容量、楼板承重、馈线通道、母线槽容量）在第一天按未来负载设计，可变接口（整流器、tap-can、机柜输入、液冷 manifold）留作灵活替换 [p5][p12]。
  2. 从"少数 DC 柜混在 AC pod"到"DC 为主负载"，可用双额定母线槽、分离 AC/DC 母线槽或混合母线槽过渡 [p7]–[p10]。
- 关键数据：
  - Gen1 GB300 NVL72 145 kW（415/480 VAC + 48–54 V DC）；Gen2 Vera Rubin NVL72 230–330 kW（800 VDC 试点）；Gen3 570 kW、Gen4 1 MW 需 800 VDC [p3]（引用 NVIDIA 资料）
  - 机柜内电源：AC/DC 400/50 V 与 DC/DC 800/50 V power shelf [p8]（自报）
- 提到的公司/客户/产品/标准：Vertiv、NVIDIA GB300/Vera Rubin、800 VDC、SST、BESS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（四代机柜功率与供电方式）；p4（四种 800 VDC 接入架构）

### P301 Changing workloads demand Active Compute Fabric presented by Cornelis Networks
- 讲者/机构：Jayraj Nair，Cornelis Global Field CTO | 类型：厂商展区
- 方向归属（主/次）：主 [Out 后端网络：NIC、交换芯片、拥塞控制、UEC/RoCE]；次 [Up：UALink/ESUN]、[推理/算力/经济性]
- 核心主张：
  1. 网络从被动管道（第一代）→ DPU/SmartNIC（第二代）→ Active Compute Fabric（第三代，每个 NIC 与交换机都带计算核）[p5]。
  2. PD 分离后 KV cache 需在首 token 前完成传输，TTFT 变成网络指标 [p8]。
  3. CN7000 同时支持 scale-out（Ultra Ethernet + SONiC）与 scale-up（UALink、ESUN）[p9][p10]。
- 关键数据：
  - CN5000 vs NVIDIA NDR 400G（ConnectX-7、Quantum-2，2 路 AMD EPYC 9755，IMB）：延迟最多低 32%，消息率最多 2.3x，小消息带宽最多 2.5x；HPC 应用 1.5x–2.5x [p3]（自报/实验）
  - 部署：CTS-2 Lynx 900+ 服务器，Top500 #277，网络扩展效率 91%（测至 900 节点）；Stampede3 WRF 4→26 节点比 OPA100 性能高 71% [p4]（现网/自报）
  - 路线图：CN5000 400G/PCIe 5.0 出货中；CN6000 800G/PCIe 6.0，Omni-Path/RoCEv2/Ultra Ethernet，1.6B msg/s，送样中，Q4 2026 扩大供货；CN7000 1.6T/PCIe 7.0/576×200G，2027 流片 [p9]（预测）
  - CN7000 DCF：每交换机 96 个 CE 核（RV64GCV，VLEN=1024）、48 MB 片上 SRAM、72×1.6T 端口；每 NIC 8+16 核；10 万 GPU 规模下 110 万 RISC-V 核、~1.2 TB 分布式 SRAM、17 Pbps 注入带宽 [p11]（自报/目标）
  - 交换 576 端口 Director，扩展至 50 万+端点 [p2]（自报）
- 提到的公司/客户/产品/标准：Cornelis CN5000/CN6000/CN7000、Omni-Path、NVIDIA NDR、UEC、UALink、OCP ESUN、OpenFabrics Alliance、SONiC、MRC、PQC
- 首次/记录/SOTA 声明：称"Highest-Performance End-to-End Networking" [p2]（自报）
- 推荐配图页：p11（CN7000 Active Compute Fabric 规格与六类加速引擎）；p9（三代产品路线图）

### P302 Cooler System, Hotter Innovation presented by HFH Thermal
- 讲者/机构：Silas Cui，Hongfuhan Technology（HFH Thermal）Technical Specialist | 类型：厂商展区
- 方向归属（主/次）：主 [底座-冷却]；次 [Out：可插拔光模块]
- 核心主张：
  1. 冷却按风冷→常规液冷→先进液冷（manifold+微通道）→两相四级演进，核心是提高冷却液侧换热系数 [p7][p8]。
  2. 光模块用 1×1 浮动冷板获得最佳接触与最低压降 [p15]。
- 关键数据：
  - GPU TDP：V100 300 W → Rubin 2,300 W（2026E，×7.7）；交换芯片 TH3 390 W → TH7 204.8T 3.5–4 kW（×10）；光模块 400G ≈9 W、800G ≈15 W、1.6T ≈25 W、3.2T ≈40 W，笼体接触热流 2→6 W/cm² [p6]（自报/预测）
  - mJet LCP：芯片功率 800–3,500 W，热点 >500 W/cm²，流量 1.35–4.5 L/min，入口 25–45 °C [p11]；TH7 方案铜微翅片高 1.2 mm/厚 0.1 mm/间距 0.12 mm，平面最高 85 ℃（Tcase 限 90 ℃），压降 2.16 psi [p13]（仿真）
  - 光模块 TIM：导热胶带 ΔT 3–4 ℃@30W、≤200 次插拔；Thermal Skateboard 4–6 ℃、>500 次；涂层 0.03 mm、4–6 ℃、≥200 次 [p16]（看图）
- 提到的公司/客户/产品/标准：HFH、Broadcom TH3/TH5/TH6/TH7、NVIDIA V100–Rubin、XJTU、SCUT
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（GPU/交换芯片/光模块功耗演进）

### P305 Enabling-an-Open-Near-Package-Ecosystem-for-AI-Scale-Up-presented-by-Molex
- 讲者/机构：Bill Wilson，Molex Group Manager, New Product Development | 类型：厂商展区
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/NPO、铜缆]；次 [Out：可插拔光模块]
- 核心主张：
  1. 铜/光分界正从前面板移到机箱内部；NPO 在可插拔与全集成光之间取得平衡，缩短电通道同时保留可维护性 [p2][p3]。
  2. Scale-up 光互连需以无源铜为基准在系统层评估；OCP SROI 定义系统需求，OIF NPO、Open CPX 等定义接口 [p4][p6][p7]。
  3. 没有单一互连架构能满足所有 scale-up 场景，用共用 footprint 让 NPO/NPC 选择后移 [p12][p16]。
- 关键数据：
  - Mirror Mezz Enhanced：224G、5 mm 叠高，已纳入 OCP OAI/OAM v1.0/v1.5 并量产多年 [p9]（自报）
  - Gemini Mezz：3 mm×3 mm 对间距，8×13 矩阵 100 DP = 64 DP（6.4T，32Tx+32Rx）+ 8 DP（7.2T 扩展）+ 16 DP 控制 + 12 DP 电源（36 A）；41.6×26.6 mm [p10][p11]（自报）
  - CuOperate：ASIC 周围 16 个 NPX footprint × 64 DP = 1,024 DP（512 Tx + 512 Rx），200 Gb/s 每通道时每方向 102.4 Tb/s [p14]（自报）
- 提到的公司/客户/产品/标准：Molex Mirror Mezz Enhanced、Gemini Mezz、CuOperate、Si-Fly HD（Molex 授权，CPX Type 2）；OCP SROI、OIF NPO、Open CPX MSA、OAM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（scale-up 的铜/光、光学位置、集成度三类"杠杆"）；p11（Gemini Mezz 100DP 引脚分配）

### P307 Evolving-the-Infrastructure-Stack-Rack-Scale-Designs-Open-Firmware-and-Intelligent-Sustainability-presented-by-AMI
- 讲者/机构：未见（AMI）| 类型：厂商展区
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：
  1. 计算单元从服务器扩展到多数据中心，固件编排需随之分层扩展 [p2][p3]。
  2. 控制面应分层且每个管理边界都是信任边界：本地做时间敏感决策，全局做聚合与授权 [p6]。
- 关键数据：无定量数据（全篇为架构论述）[p1]–[p10]
- 提到的公司/客户/产品/标准：AMI DCM、AMI RM、OneTree、Tektagon、Lattice FPGA；UEFI/EDK2、OpenBMC、Redfish、OpenRMC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（分层安全控制面示意）

### P308 Extending Copper for Efficient Next-Generation Scale-Up Networks presented by Ciena
- 讲者/机构：Matt Bolig，Ciena Product and Technology Marketing | 类型：厂商展区
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板]
- 核心主张：
  1. 200G 每通道下 DAC 距离只剩约 1 m，在先进 AI 机柜内也会不够 [p3][p4]。
  2. "能用 ACC 就用 ACC，必须时才用 AEC"：ACC（线性 redriver）保留 DAC 的即插即用、低功耗、零附加延迟 [p6]。
  3. ACC MSA 推动多源标准化供应链 [p7][p9]。
- 关键数据：
  - IEEE DAC 目标距离：50G/lane 3 m → 100G/lane 2 m（-33%）→ 200G/lane 1 m（-50%）[p3]（引用 IEEE 802.3cd/ck/dj）
  - 40 dB@200G 通道示例：1.5 m 30AWG DAC 16 dB + 连接器 2×5 dB，剩约 12 in PCB（每侧 ~6 in，1.2 dB/in）[p3]（自报，估算）
  - 机柜示例：10 计算托盘 + 9/8 交换托盘，最长垂直走线 18 RU ~800 mm，水平互连仅 ~350 mm [p4]（自报）
  - 1.6T ACC（8×200G）：3.5 m，1.5 pJ/bit 每端，零附加延迟，单 3.3V；AEC：4.5 m，10 pJ/bit，~2×35 ns 延迟，4+ 电源轨，成本 \$\$\$\$ [p6]（自报）
  - 有源线缆 5 年内达数千万条，ACC 约占 30%（LightCounting 2026.7）；读图 ACC 占比 2026 约 4% → 2028 约 27% → 2031 约 27% [p5]（引用 LightCounting / 看图）
  - Nitro 2004 示例：总损耗 67 dB 通道（Nitro 前 45 dB、后 22 dB），BER 约 7e-9；Nitro 前损耗 22–37 dB 时 BER ~1e-10 量级，49 dB 时 ~2.5e-7，均低于 ~2e-4 门限 [p8]（实验/看图）
  - ACC MSA 2026.2.23 成立，16 家成员；首次 plugfest 2026.8.31–9.4，8 家公司，32 条线缆 [p7]（自报）
  - 光以太网端口 5 年内超 3.5 亿 [p2]（引用 LightCounting）
- 提到的公司/客户/产品/标准：Ciena Nitro 2004 Linear Redriver、ACC MSA、IEEE 802.3cd/ck/dj、LightCounting
- 首次/记录/SOTA 声明：ACC 可将 200G 线缆延长 1 m 以上 [p9]（自报）
- 推荐配图页：p8（ACC 67 dB 通道 BER 曲线）；p6（ACC vs AEC 对比表）；p5（有源线缆市场预测）

### P309 FUJITSU-MONAKA- Optimized for High Performance and Energy Efficiency for AI, presented by Fujitsu
- 讲者/机构：Masato Fukumori，Fujitsu Director, Product and Project Management | 类型：厂商展区
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [In 封装内：chiplet、CXL]、[安全]
- 核心主张：
  1. 2nm 核心 die + 3D 封装 + 超低电压实现高能效通用 CPU [p5][p6]。
  2. 无 GPU 的 CPU 平台也可承担一部分推理负载 [p8]。
- 关键数据：
  - 144 核×2 路（288 核/节点），Arm v9.3-A、SVE2-256bit；DDR5 12 通道 8800MT/s；PCIe 6.0（CXL 3.0）96 lanes；核心 die N2P、SRAM/IO die N5 [p5][p6]（自报）
  - 机密计算支持 4,096 个用户 VM [p7]（自报）
  - 参考平台（无 GPU）：gpt-oss-20B 307.0 token/s、Gemma4-31B 55.2 token/s（batch 2）；INT8 峰值 213.8 TOPS [p8]（实测/自报）
  - 2026年11月开始全球销售 [p9]；路线图 2029 年 1.4nm 代支持 NVLink Fusion、入选 FugakuNEXT [p11]（预测）
- 提到的公司/客户/产品/标准：Fujitsu MONAKA、A64FX、Fugaku、RIKEN、NEDO、Arm SystemReady SR、OpenBMC、EDK2、Redfish、NVLink Fusion
- 首次/记录/SOTA 声明：A64FX 为"首个实现 Arm SVE" [p11]（自报）
- 推荐配图页：p5（MONAKA 处理器概览）

### P310 Fanless-Servers-Are-Coming-The-Peripheral-Coldplate-Roadmap-Behind-100-Heat-Capture
- 讲者/机构：Brad Zakaib，CoolIT（Ecolab）VP Product Engineering | 类型：厂商展区
- 方向归属（主/次）：主 [底座-冷却]；次 [Out：可插拔光模块（OSFP 冷板）]
- 核心主张：
  1. >250 kW 机柜需要 100% 液体捕获热量，无风扇服务器需要外围器件（DIMM、OSFP、SSD、NIC、VRM）冷板 [p5][p7]。
  2. 单相 DLC 是未来平台 [p26]。
- 关键数据：
  - 2023–2030 每封装平均 die 数 1→14，硅面积 700→9,000 mm²，热流 70→110 W/cm²；TDP 散点 2030 最高约 14,000 W [p3]（引用 SemiAnalysis & CoolIT / 看图）
  - 15 kW TDP 冷板验证：1.2 LPM/kW，80 °C 壳温，45 °C 设施水，35 °C ΔT，约为此前 4 kW 设计的 4 倍 [p14]（实验/自报）
  - 可插拔模块骑乘式冷板 >15 W，固定冷板 <15 W [p18]；DIMM 双面冷却 >20–40 W（DDR5+）[p17]（自报）
  - CoolIT 今日 / 明日：热流 300 W/cm²+ / 500 W/cm²+，冷板 4,000 W+ / 15,000 W+，机柜 500 kW+ / 1 MW+ [p25]（预测）
- 提到的公司/客户/产品/标准：CoolIT、Ecolab、NVIDIA、SemiAnalysis、OMNI、SplitFlow
- 首次/记录/SOTA 声明：称"Industry's best performing, most reliable coldplate" [p13]（自报）
- 推荐配图页：p3（处理器 TDP 演进散点图）；p14（15 kW 冷板验证）

### P313 How-can-high-speed-interconnect-solutions-drive-next-generation-AI-data-centres-at-448G-and-beyond-presented-by-BizLink
- 讲者/机构：Dr. Hendrik Coldenstrodt，BizLink Group CTO, Computing and Transportation Business Group | 类型：厂商展区
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板、CPO/NPO]；次 [Out：光纤连接]
- 核心主张：
  1. 448G 下铜面临"铜墙"：保持 PAM4 则 Nyquist >100 GHz，改高阶调制则 SNR 要求更严 [p3][p4]。
  2. 通过改进线缆结构（缩短绕包节距消除陷波、双螺旋、纱线绝缘）把铜推到 110 GHz，并做超细线缆以靠近 ASIC（CPC）[p8]–[p12]。
- 关键数据：
  - 448G 编码：PAM4 224 GBd/Nyquist 112 GHz/SNR 0 dB；PAM6 173 GBd/87 GHz/-4.4 dB；PAM8 150 GBd/75 GHz/-7.4 dB [p4]（自报，计算）
  - 剥线长度 1.0/0.8/0.6 mm 对应 IL@53GHz -16.4/-15.0/-14.7 dB [p5]（实验）
  - 绕包节距 4.0/1.6/1.0 mm 对应谐振 ~25–30 / ~62–72 / ≥100 GHz [p9]（自报）
  - ParaLink 85 cm（双 drain、92Ω）去嵌后 SDD21 在约 110 GHz 约 -14 dB [p10]（看图）
  - CPC 系统（39AWG ParaLink + Rosenberger TeraNano，PCB 500 mm 样品）SDD21：56 GHz 约 -22 dB，86.7 GHz 约 -30 dB，112 GHz 约 -40 dB [p12]（看图，引用 Rosenberger 数据）
  - TeraNano 10×18 mm 容纳 32 差分对，插合高度 <6 mm；Megtron 6 PCB IL ~-35 dB/m@20GHz vs ParaLink 优于 -15 dB/m [p11]（自报/引用）
  - 光纤跳线 MPO/MMC 典型 IL <0.1 dB [p13]（自报）
- 提到的公司/客户/产品/标准：BizLink ParaLink、woven flat cable、Rosenberger TeraNano、OSFP、MPO、MMC、SN、Epoch AI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（448G PAM4/PAM6 CPC 系统 SDD21 曲线）；p4（PAM4/6/8 对比表）

### P316 Multi-Core Fiber - A solution for scale up, out, and across presented by Sumitomo Electric
- 讲者/机构：Dwayne Holst，Sumitomo Electric Lightwave Optical Communications Engineer | 类型：厂商展区
- 方向归属（主/次）：主 [Across：多芯光纤]；次 [Out 后端网络布线]、[Up]
- 核心主张：
  1. GPU 代际演进使每柜后端光纤数指数增长，平行光纤（MPO/MMC）接近实用极限，WDM 不适合 <500 m 链路 [p3][p5]。
  2. 空分复用的 4 芯 MCF 可节省空间、重量和安装时间，主要 MCF 厂商已就 4 芯设计达成 MSA [p6][p8]。
  3. 现阶段用 FIFO 接传统收发器，理想是 MCF 原生收发器及 MCF 直达 ASIC（CPO）[p10][p12]。
- 关键数据：
  - 每 GPU 机柜后端 scale-out 光纤数：Hopper ~576f BE + 64f FE；Blackwell(GB200) 2308f BE + 72f FE；Rubin(VR300/Kyber) 4616f；Feynman(F300/Kyber+) 18,464 芯 [p3]（自报/预测）
  - 6912 芯光缆：单芯 OD ~37 mm（1075 mm²）vs 4 芯 MCF OD ~13 mm（133 mm²）；管道空间节省 60–80% [p8]（自报）
  - 同直径/同重量下 4CF 芯数约为 1CF 的 4 倍（1CF 约 3,456 芯 vs 4CF 约 13,824 芯达到 100%）[p9]（看图）
  - 96 芯 MPO-APC、64 芯 MMC-APC 连接器（基于 4 芯光纤）[p11]（自报）
- 提到的公司/客户/产品/标准：Sumitomo Electric、Senko、Viavi、OCP Academy、MPO、MMC、FIFO、MCF MSA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（四代 GPU 机柜光纤数增长）；p8（6912 芯光缆截面对比）

### P317 One-Abstraction-Many-Transports-Push-Mode-Communication-from-Chiplet-to-Rack-presented-by-d-Matrix
- 讲者/机构：Sai Rahul Chalamalasetti，d-Matrix | 类型：厂商展区
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [Out：NIC]、[Up：ESUN/NVLink Fusion]、[In：D2D、3D DRAM]
- 核心主张：
  1. 用同一 push-mode 通信抽象覆盖 chiplet（NOC）、封装（D2D）、卡/节点（PCIe）到机柜（以太网）[p5][p7]。
  2. 推理不是单一计算，用异构分离（GPU 做 attention/prefill/verify，d-Matrix 做 FFN/decode/draft）匹配负载 [p12][p14][p16]。
  3. 下一代 Raptor 以 3D 堆叠 DRAM 补齐容量短板，scale-up 走 NVLink Fusion 或 ESUN [p19]–[p22]。
- 关键数据：
  - Corsair：8 chiplet，TSMC 6nm，2 GB SRAM 150 TB/s，256 GB LPDDR5 400 GB/s，2400 TFLOPS MXINT8 / 9600 TFLOPS MXINT4，DMX Bridge 512 GB/s，600 W TDP [p4]（自报）
  - JetStream NIC：400 Gbps IEEE 802.3 以太网，PCIe Gen5，150 W TDP，延迟 2 µs；PCIe 语义承载于以太网，延迟低于 RoCEv2（graph-to-graph，未给数值）[p6][p7]（自报）
  - Squadron：最多 16 个 SquadRack，1,024 个 Corsair XPU，兆瓦级 [p9]（自报）
  - 异构 AFD：845 token/s/user，64 并发用户合计 20,145 token/s [p17]（自报/演示）
  - Raptor：NVL Fusion 机柜内 144 个 Raptor scale-up；Arista ESUN 系统 128 个 Raptor XPU [p21][p22]（自报/看图）
  - Rail-only 拓扑：节点内 TP/PP/EP，节点间经以太网交换做 PP/EP；Leaf 下按 expert 与 attention 分组部署 [p10][p11]（看图）
  - 推理市场 2032 年超 1 万亿美元（32% CAGR）[p3]（引用 Bloomberg Intelligence）
- 提到的公司/客户/产品/标准：d-Matrix Corsair、JetStream、SquadRack、Squadron、Raptor；NVIDIA B200、Vera Rubin、NVLink Fusion、NVL72 MGX；Arista Etherlink；ESUN、RoCEv2
- 首次/记录/SOTA 声明：无
- 推荐配图页：p16（三种异构分离推理方式）；p5（chiplet→节点四层连接）；p10（expert/attention 分离的机柜 scale-out 拓扑）

### P318 Open-Trusted-and-Secure-SONiC-at-Scale-presented-by-Cisco
- 讲者/机构：Will Eatherton（Cisco SVP, Network Engineering）、Dina Papagiannaki（Microsoft Corporate VP, Azure Networking） | 类型：厂商展区（含炉边对谈）
- 方向归属（主/次）：主 [Out 后端网络：SONiC]；次 [安全]
- 核心主张：
  1. SONiC 正成为开放、安全的云与 AI fabric 通用操作平台，AI 驱动路线图（SRv6、packet trimming、高频遥测、无损/低延迟 fabric）[p3]。
  2. SONiC 进入分布式、共享设施、远程运维场景，需要硬件信任根、策略化入网与运行时防护 [p4]–[p8]。
- 关键数据：
  - 社区 4,250+ 贡献者，520+ 组织，2025 年 36 个基金会成员 [p3]（自报）
  - SONiC 交换机市场 2028 年 90 亿美元以上、部署占比 20%；2025 支付/电信案例 TCO 节省 40–50%+ [p3]（自报/预测）
  - 漏洞屏蔽（不停机、不重启）2027 年 Q2 上线 [p7]（预测）
- 提到的公司/客户/产品/标准：Cisco Nexus One、Microsoft Azure、SONiC、SAI、Linux Foundation、TPM、OpenTitan、Caliptra、SUDI/IDevID
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（SONiC 生态规模与 AI 路线图）；p6（设备入网策略流程）
