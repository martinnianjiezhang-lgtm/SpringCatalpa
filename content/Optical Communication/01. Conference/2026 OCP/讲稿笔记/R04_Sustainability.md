---
title: "R04_Sustainability"
tags:
  - OCP2026
  - 讲稿笔记
---

# R04 笔记：Server：Open Chiplet Economy、Sustainability、Test & Validation、Time Appliances、ai-clusters

### P079 The Open Chiplet Economy- Progress, Challenges, and the Road Ahead
- 讲者/机构：Jawad Nasrullah（Palo Alto Electron）、Anu Ramamurthy（Microchip）、Mark Knight（Arm）| 类型：标准进展
- 方向归属（主/次）：主 [In 封装内：chiplet/UCIe/BoW、D2D]；次 [安全]
- 核心主张：
  - OCE 分层（架构、供应链/商业、身份安全、测试可靠性、CPO/高带宽互连、EDA、封装）各有负责方，但无组织拥有完整开放系统结果 [p2]。
  - 2027 年要从"定义标准"走向"证明互操作"：让互操作可验证、让 chiplet 复用在商业上有吸引力 [p8]。
  - 需要新的 Business 工作流（模型协议、项目结构、案例）降低多厂商合作的法律/商业阻力 [p9]。
- 关键数据：
  - FCSA 1.0.0 于 2026 年 2 月发布，1.1.0 于本周批准发布 [p4]（自报）
  - CMI over I3C 已完成待 OCP 批准；CMI over UCIe 审阅中；CMI over BoW 与专用 SCMI API 为初稿 [p4]（自报）
  - BoW Flexi 1.0 于 2026 年 9 月发布，目标 MCU/传感器/Edge AI/IoT [p5]；N=1…128 lanes，source-synchronous SDR，含 Transaction/Link（ECC、Padding）/PHY 三层 [p5]（看图）
  - Chiplet marketplace：28,497 页面浏览，同比 +60%，月峰值互动约 2,837 [p6]（自报）
- 提到的公司/客户/产品/标准：BoW / BoW Flexi、FCSA、CMI、I3C、UCIe、SCMI、CDX（Chiplet Design eXchange）、Caliptra、NPO/CPO；BoW Flexi 贡献者 VeriSilicon、Microchip、Eliyan、YorChip、Infineon [p5 看图]；Credo 贡献 LSI 互连 [p4]
- 首次/记录/SOTA 声明：BoW Flexi V1.0.0 首版发布 [p5]
- 推荐配图页：p5（BoW Flexi MCU/Analog chiplet 分层框图与贡献者卡片）；p3（OCE 工作流全景）

### P081 Closing the Loop- Structural Steel Reuse in Hyperscale Datacenter Construction（精简）
- 讲者/机构：Anjali Bhagat、John O'Sullivan（Microsoft）| 类型：技术分享
- 方向归属（主/次）：主 [底座-机架/机械]（建筑/可持续）；次 无
- 核心主张：
  - 结构钢碳密集但耐久可测，只要来源与验收管理到位即可直接复用 [p5]。
  - 复用必须在招标阶段（RIBA Stage 3 之前）确定，才能不影响成本与进度 [p7][p10]。
- 关键数据：
  - Newport Imperial Park（南威尔士）回收 249 吨结构钢，约占结构框架 10%；初始目标约 13% [p6]（现网）
  - 结构钢整体再生含量 76% [p7]；复用节省约 520 tCO₂e，复用+再生钢合计约 4,400 tCO₂e [p7]（自报）
  - 拆除阶段废弃物分流 +90%，整体 +80% [p7]；FY25 Microsoft 建筑与拆除废物分流 >90% [p5]
- 推荐配图页：p7（影响数字一览）

### P082 Closing the Visibility Gap- An AI-Driven Supply Chain Intelligence Framework for Water Stewardship（精简）
- 讲者/机构：Ojonimi Bako（Kaya AI）、Michael Obradovitch（Ecolab）| 类型：面板
- 方向归属（主/次）：主 [底座-冷却]（水资源）；次 无
- 核心主张：
  - 数据中心大部分水消耗发生在建成之前（上游供应链），WUE 只覆盖运营阶段 [p3][p5]。
  - 建议 OCP 在 Sustainability Project 下建立 embodied water 定义、边界与披露格式 [p6][p9]。
- 关键数据：
  - 平均水耗分布：围栏内 23% vs 上游供应链 77% [p3]（引用 CDP、WRI）
  - 水资源紧张地区中断时可达 99% 产出与收入受风险 [p4]（引用 Ecolab 2026.4）
  - 燃气发电用水 570–1,100 L/MWh [p8]（引用）
  - Cold-plate 液冷相对风冷生命周期水耗低 30–50%，能耗低约 15%（风冷=100，水指数 50–70、能耗≈85）[p12][p13]（看图；引用 Microsoft/WSP Nature 2025）
  - p7 示例 CDU-07 300 kW 的 embodied water 1,240 m³ 等为占位数 [p7]（自报，明确为占位）
- 推荐配图页：p3（23%/77% 围栏内外水足迹）；p12（液冷 vs 风冷生命周期水指数）

### P087 Increasing Rigor in Data Center Carbon Disclosure（精简）
- 讲者/机构：Miranda Gardiner（iMasons Climate Accord，主持）、Andrea Desimone（Schneider Electric）、Malcolm Hegeman（Google）、Lalit Joshi（Microsoft）、Nalintip Suwannakarn（Meta）| 类型：面板
- 方向归属（主/次）：主 [量子/其他]（可持续/碳披露）
- 核心主张：
  - 披露≠脱碳，但可比、第三方验证的披露是低碳采购的前提；可比性依赖 PCR [p5]。
  - MEP 基本已具备 EPD 条件；ICT 缺类别级与组件级规则 [p8]。
- 关键数据：
  - OCP Carbon Disclosure Base Specification 发布于 2025 年 8 月 [p4]
  - ICT：识别 27 个类别，PCR 仅通用型，有效 PSR/c-PCR 覆盖 2 类（3 类在制定）[p8]
  - MEP：21 个类别，有效 PCR 覆盖 20 类，PSR/c-PCR 覆盖 12 类；缺液冷系统 PCR [p8]
- 推荐配图页：p8（MEP vs ICT PCR 缺口）

### P089 Operationalizing the PCR- LCA at Scale and the Open Enablers Program（精简）
- 讲者/机构：Mackenzie Clark（Google）、Josue Campos（Meta）；工作组 Fraunhofer IZM、Google、Meta、Microsoft、Amazon | 类型：标准进展
- 方向归属（主/次）：主 [量子/其他]（可持续/LCA）
- 核心主张：
  - LCA at Scale 允许混合不同数据质量的排放估计，高保真 LCA 用于关键部件，低质量估计保证完整性 [p8]。
  - Open Enablers 建立匿名贡献的行业平均 PCF 数据集，不泄露供应商 IP [p12][p13]。
- 关键数据：
  - Data Quality Score 0–10：一手 PCF 8–10，Proxy 5–7，参数模型 4，类别均值 3，收入型排放因子 2，价格型 EEIO 1 [p4]
  - 示例：机柜 130 kgCO2e/单元，加权 DQ≈3 [p6]（示例数据）
  - LCA at Scale 框架预计 2027 Q1 发布；Open Enablers Phase 1 H2 2026–2027，Phase 2（厂商贡献）目标 2028 [p14]
- 推荐配图页：p4（DQS 分级表与机柜分类法）

### P092 Scaling Digital Infrastructure in Hardware Manufacturing- Real-Time Telemetry, Automated Carbon（精简）
- 讲者/机构：Malcolm Hegeman（Google）、Brandon Weilbacher（Axiom / Flex）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]（制造遥测）；次 可持续
- 核心主张：
  - 电力是制造 gate-to-gate 排放的主要来源，需要机台级直接计量替代静态估计 [p2]。
  - 基于 Google Cloud MDE 的 OT/IT 管线可把 kWh 关联到序列号/工单，并自动生成 ISO 合规 LCI [p4][p7]。
- 关键数据：
  - 电力通常占 gate-to-gate 排放 >90% [p2]（自报）
  - 全球制造业年用电可能在数十 TWh 量级 [p2]（自报）
  - Flex SMT Line 11 日能耗约 2.3–2.8 MWh；回流炉为单机最大耗能，约 0.25–0.29 MWh/日 [p6]（看图）
- 推荐配图页：p6（Flex Energy Insight 仪表板）

### P095 The Green Tokens- From Green Computing to Sustainably Intelligent（精简）
- 讲者/机构：CHEN, Yen Haw（Taiwan Institute of Economic Research, TIER）| 类型：主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]（AI 可持续披露）
- 核心主张：
  - 提出 "Green Tokens"：对 AI token 的生成时间、地点、电力来源与排放做披露，让用户可选择 [p3][p13]。
  - 借鉴台湾 T-REC 与 Green Mileage 机制，建议 OCP 设立相关工作流 [p7][p9][p15]。
- 关键数据：
  - 自 2020 年 5 月起已交易转移 3,519,211 张 REC（3.51 billion kWh），至 2023 年 9 月 205 个 CPPA 买家（企业 75.1%）[p8]（引用 TIER/MOEA）
  - T-RECs 累计 16,159,156 MWh [p7]
  - p13 仪表板百分比（如 60% green data center）为示例 [p13]
- 推荐配图页：p13（Green Tokens 仪表板示例）

### P099 Fan Reliability Qualification- A standardized framework across the server fan supplier base（精简）
- 讲者/机构：Mahendra Lokhande、Kalpak Dhake（Meta）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [底座-冷却]
- 核心主张：
  - 各风扇供应商的可靠性测试、样本量与应力曲线差异大，无法同口径比较 [p4]。
  - 统一的风扇可靠性认证（基于 IPC-9591，加大样本量，量产 ORT）提高了下限 [p5]。
- 关键数据：
  - 现场 ASR 超规格、早期失效，各供应商趋势相似；2023 年中出现尖峰后回落 [p3]（看图，数值单位看不清）
  - 热循环测试中叶轮在 150 次与 300 次循环出现裂纹，根因为材料规格不一，改为 PPS [p6]（看图/实验）
  - 部署新材料要求后机队风扇失效率稳定 [p6]（自报，无具体数字）
- 推荐配图页：p6（150/300 cycles 叶轮裂纹照片）

### P101 From Tray to Training Job- L10-L12 Manufacturing Test
- 讲者/机构：Meghan Kachhi（Cisco）、Sunny Dugar（Supermicro）| 类型：技术分享 / 厂商展区
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [Up 机柜/超节点：NVLink、铜缆/背板]、[Out 后端网络：RoCE、交换芯片]
- 核心主张：
  - L10 证明组件（托盘），L11 证明机柜，L12 证明集群；L1–9 只造部件，L10–12 决定 AI 基础设施能否工作 [p3]。
  - 每一层明确 "PROVES / DOES NOT PROVE"：L10 不证明 cable cartridge 插接与 72-GPU NVLink 域；L11 不证明跨机柜传输与训练 JCT [p4][p8][p12]。
  - L11 要能捕获铜缆 cartridge 插接/线束错误 [p3]。
- 关键数据：
  - L10 示例托盘：2 Grace CPU、4 GPU、4 compute HCA、2 BF3 DPU [p4]；I/O 测试 4× ConnectX-8 800G loopback [p5]
  - L10 电源瞬态测试：GPU pulse 1 与 4 kHz，CPU-GPU sync 1–500 Hz [p5]
  - L11 NVL72：18 compute tray + 9 NVLink switch tray，72 GPU 一个 NVLink 域；两台 TOR [p8][p9]
  - Cisco Nexus One 组合：Silicon One G200X 2RU 64×800G OSFP；Silicon One G300 3RU/3OU(ORv3) 64×1.6T OSFP；Spectrum-4 64×800G；Spectrum-6 2RU(MGX) 64×1.6T [p14]
  - 示例 ib_write_bw（16 QP，RoCE）峰值/平均 391.53 Gb/s [p15]；NCCL all_reduce 跨 2 机柜 144 rank GB300，17 GB 消息 busbw 约 739–742 GB/s，#wrong=0 [p16]（实验，注明"实际结果可能完全不同"）
  - 演示：18× 100G BlueField-3 接 ns-leaf001，PFC+ECN RoCEv2；"1.6T 模型经 100G 几分钟加载" [p19]
  - 满载 NVL72 热成像：CDU/冷却管最高 55.5°C，机柜正面 25.3–36.7°C，NVMe 托盘 29.2–37.5°C [p20]（看图）
- 提到的公司/客户/产品/标准：Cisco Nexus One、Nexus Dashboard、Hyperfabric、Splunk Observability Cloud、Supermicro、NVIDIA GB200/GB300 NVL72、Vera Rubin NVL72、HGX B300/Rubin NVL8、RTX PRO 6000、BlueField-3、ConnectX-8、DCGM、NCCL、UFM、BCM、Slurm/K8s、OCP ORv3 MGX 规范、SONiC/NX-OS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（L10/L11/L12 三层定义）；p13（L12 集群硬件栈拓扑）；p16（NCCL busbw 判读说明）

### P102 High Speed Cable Cartridge AI System Validation
- 讲者/机构：Granthana Rangaswamy、Yuvin Weerasinghe（Meta）| 类型：技术分享
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板、机柜级互连]；次 [运维/可靠性/遥测]
- 核心主张：
  - Scale-up 网络无冗余时任一链路失效即终止作业，P(fail)=1−(1−p)^N，1000+ GPU 时 MTBF 降到小时级 [p2]。
  - 线缆弯折对 skew 与模式转换（SCMR/SCD21）影响显著，而对眼图、COM 影响可忽略；需用 skew 作为预弯验收基线 [p7][p8]。
  - 量产阶段厂商是最终质量关口，集成方与厂商需统一 RMA 准则；维修后需复筛（机械冲击可能导致链路退化）[p13][p14]。
- 关键数据：
  - 弯折影响（n=320 通道）：EIPS |Skew| 平均 +1.642 ps（+325.6%，大效应，97% 退化）；SCMR 802.3dj −10.069 dB（−44%，大效应，97% 退化）；IL@Nyquist −0.676 dB（大效应，89%）；COM +0.341 dB（小幅改善）；眼宽/眼高变化可忽略 [p7]（实验）
  - Pre/post bend SCD21：42.101 GHz 从 −41.70 dB 到 −27.64 dB，53.125 GHz 从 −43.38 dB 到 −30.69 dB；线长示例 553 mm / 581 mm [p4]（看图）
  - EVT/DVT：PRBS31Q、idle、traffic 下测 BER floor 与最大 FEC T；50 次上下电；四角温湿度 [p8]
  - 振动/冲击：OP 0.5 Grms 5–500 Hz 随机振动 20 min/轴；OP 冲击 2–6 G 11 ms；非工作冲击 12 G [p11]
  - 工艺角 SS/FF/TT 硅片覆盖最差/最好余量 [p12]
  - INSPECT 工具每日约 3–8 M 次通道判定 [p9]（看图）
- 提到的公司/客户/产品/标准：Meta Skew Analysis tool、INSPECT（Interconnect System Parametric Checker Tool）、IEEE 802.3dj、BERT、TDR、PRBS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（弯折前后 skew 与 SCD21 VNA 曲线）；p7（弯折统计表）；p9（INSPECT 链路健康监测）

### P108 High Radix Switches and Precise Time
- 讲者/机构：Dan Biederman（Eridu，个人观点）| 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：交换芯片、拥塞控制]；次 [Up 机柜/超节点]、[运维/可靠性/遥测]（精确时间）
- 核心主张：
  - 高 radix 交换压平网络、减少跳数，降低平均时延与抖动/尾时延，并带来功耗、成本、可靠性收益 [p6][p7][p21]。
  - 数千端口交换机内的 "停车场问题"（离出口最远的包最慢）可用各输入端精确到达时间 + 公平调度解决，降低尾时延 [p11]。
  - 高 radix 交换机需在每个端口精确计时；Sync-E 让上千 SerDes PLL 同步到一个高质量时钟，提升 1588 精度 [p10]。
- 关键数据：
  - 640 GPU @1.6T：需 30 台 102T 交换机两层，对比假想单台 1P 交换机单跳 [p6]（看图）
  - 交换时延：标称 X、实际约 5X；1/2/3 级实际约 5X/15X/25X，"每多一级加约 10X"；一级相比两级约为 1/3 时延 [p8]（自报假设）
  - 1,000 端口交换机仿真（100 次 Monte Carlo 平均）：p99.99 时延，到达时间调度 vs DWRR 在 50% 负载 −17%、90% 负载 −31%；90% 负载归一化 RR 1.00 / DWRR 0.95 / Arrival 0.67 [p20]（仿真，看图）
- 提到的公司/客户/产品/标准：Eridu、IEEE 1588、Sync-E、Open Multi-Rack Scale-up Domains（OCP 新工作流）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p20（到达时间调度 p99.99 尾时延仿真）；p6（30×102T 两层 vs 单 1P 交换）

### P109 Multidomain Time Synchronization in the Modern Datacenter- From Network to Workload
- 讲者/机构：Christopher Hall、Srinivasan S. Iyengar（Intel）| 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]（时间同步）；次 [Out 后端网络：NIC]
- 核心主张：
  - 时间精度随 GM 到终端的跳数下降，故引入多时间尺度：机柜本地时间尺度（最多两跳）+ 全局时间尺度（可溯源 GNSS/UTC）[p3]。
  - VM 无法直接访问 PTP 时间，可用 TSC 作为平台内共同参考共享时钟 [p5]；用 PCIe PTM 提高 host–IPU 间同步精度 [p11]。
  - BMCA 切换 GM 需数秒，改为同时同步多个 GM 的 hot standby（host 或 IPU 实现）[p7]。
- 关键数据：
  - 机柜本地时间尺度有望实现到软件可见 OS 时钟优于 50 ns 的同步 [p3]（预测）
  - 可用性目标示例 99.9999% [p2]
  - AI 场景：提高时间精度可减少集群空闲时间 [p2]（自报，无数字）
- 提到的公司/客户/产品/标准：Intel IPU、Linux auxclock、POSIX clock API、PTP KVM、libptpmgmt Clock Manager、PCIe PTM、OCP-DC PTP profile、802.1AS-2020、802.1ASdm
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（Host/IPU/VM 多时间尺度架构图）

### P110 Precision Time for AI Infrastructure- Deploying PTP Boundary Clocks at Scale
- 讲者/机构：Vikram Chandra（Nokia）、Bhaskar Chinni（Broadcom）| 类型：标准进展
- 方向归属（主/次）：主 [Out 后端网络：SONiC]；次 [运维/可靠性/遥测]
- 核心主张：
  - NTP 不足以满足亚微秒事件对齐；BC 架构让 PTP 在大型以太网 fabric 中可扩展，硬件时间戳去除软件非确定性 [p2][p3]。
  - 在 SONiC + SAI 中用开源软件和商用芯片支持 PTP BC [p4][p7][p12]。
- 关键数据：
  - SONiC Phase 1 目标 202611 版本：单 ASIC 盒式交换机 one-step 硬件时间戳、L3 over UDP、BC [p4]（自报）
  - SAI：SAI_HOSTIF_TRAP_TYPE_PTP、SAI_PORT_ATTR_PTP_MODE [p7]
  - 测试拓扑：Nokia 7250-IXR-X（SR OS）为 GM，两台 IXR7220-H5-64D（SONiC）为 BC 与 OC，PTP domain 44 [p9][p10]
  - SONiC 内新增 PTP 容器（PTP app manager 启动 ptp4l 与 telemetry feed）[p6]（看图）
- 提到的公司/客户/产品/标准：Nokia、Broadcom、SONiC、SAI、IEEE 1588、linuxptp（ptp4l、pmc）、OCP TAP
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（SONiC PTP 容器架构）

### P111 Precision-Time Circuit Switching for AI Training Fabrics- When Packet Switching Is Enough
- 讲者/机构：Sahas Munamala（ocproject.net）、Ahmad Byagowi（turbalance.com）| 类型：技术分享（实验研究）
- 方向归属（主/次）：主 [Out 后端网络：OCS]；次 [运维/可靠性/遥测]（精确时间）
- 核心主张：
  - 电路交换已在 per-job 粒度胜出；per-round 粒度（dwell/switch ≈ O(1)）未被测量，关键门槛是"可预测性" [p2][p3]。
  - 对按时触发电路而言 PTP 精度已足够，同步误差比预测误差低 5–6 个数量级；真正需求是把 PHC 时间基暴露给集合通信库、以绝对时间表达轮次调度（接口问题而非精度问题）[p9]。
  - 事件触发下的悬崖来自轮次之间的耦合级联；改为时间触发即消除悬崖 [p8][p10]。
- 关键数据：
  - >75% 训练字节为 TP 且不出 NVLink 域；>99% GPU 对无交换；Llama-3 容忍 1:7 跨 pod 超额；14–32% 机队 GPU 小时为无重叠计算的通信 [p2]（引用 Rail-only、MAD-Max、Meta SIGCOMM'24、Llama-3）
  - Google Jupiter 5× 容量、−30% capex、−41% 功耗；TPU v4 OCS <5% 系统成本带来 1.2–2.3×；Rail-only 去 spine −38–77% 成本 [p3]（引用）
  - 测试床 7×T4：pinned-circuit 下限 544 ms、oracle 651 ms、packet 基线（4:1）2365 ms、全 trickle 16.3 s；766 步 / 63 cells [p4]（实验）
  - 每轮 A=135 ms 传输 + 25 ms dark + 10 ms slack = 170 ms，dwell/switch≈6 [p5]
  - 早到容忍约 11 ms，晚到容忍约 1.7 s（~156×）[p6]（实验，看图）
  - σ=60 ms 时 as-built 10 ms slack 为 7.5 s（输 packet 3×），s=3σ=180 ms 时 1.16 s（赢 2×），6.5× 差距；σ* 从 8 ms 扩至 239 ms [p7]（实验，看图）
  - 72% 崩塌步代价超过单个滞留残差可解释 [p8]
  - 时间预算：64K GPU 预测误差 434 ms；16K 安静机队 68 ms；3D-MEMS OCS dark time 20 ms（硅光 0.3 ms）；PTP 端到端 92 ns（Meta），ConnectX-7 PHC 12 ns [p9]（引用+实测）
  - 同一 cell ε=−20 ms：事件触发 11.44 s，时间触发仅 +37 ms，oracle 处 649 vs 652 ms；规律 39·(|ε|−s−9)⁺，斜率 38.8±0.1 [p10]（实验，25 个预注册 cell）
  - 部署规模模型：packet pods + OCS spine + slots 在 16K/64K 保留 82%/70% 增益；tiered OCS 2 层仅 60%/28%；slots 使 16K 保护带 403→168 ms [p14]（仿真/分析模型）
- 提到的公司/客户/产品/标准：NVIDIA T4、ConnectX-7、NCCL、Google Jupiter/TPU v4/Apollo、Meta RoCE、Sirius、PRISM（arXiv:2510.15596）、Llama-3 405B、MoE all-to-all
- 首次/记录/SOTA 声明：撤回早期 "90%" 数字（无法从 CSV 复现）[p8]；无 SOTA 声明
- 推荐配图页：p6（早到悬崖/晚到斜坡）；p7（slack 与预测误差的胜负区域）；p14（16K/64K 架构增益保留表）

### P113 Timing Recovery Using PTP within NIC and Distribution by ePPS to Computing Modules
- 讲者/机构：Sean Liu、David Spencer（Skyworks Solutions，Timing Products）| 类型：技术分享
- 方向归属（主/次）：主 [Out 后端网络：NIC]（时间同步 last inch）；次 [运维/可靠性/遥测]
- 核心主张：
  - NIC 到 CPU/GPU 的 "last inch" 有三种方式：纯软件（不可取，时延高、抖动受 CPU 负载影响）、PCIe PTM、硬件 ePPS [p3][p4]。
  - 以 PTM 作为基线方案，并为更严格调度需求规划 OCP NIC Flex IO ePPS [p12]。
  - 主要时间误差来自 PTP 网络部分（PDV、不对称、时间戳精度）[p11]。
- 关键数据：
  - ITU-T SG15/Q13 last inch 等级：A ±2 µs（无 PTM 的 PCIe）、B ±200 ns（PCIe+PTM）、C ±50 ns（1PPS/ePPS 物理边沿）[p5]（引用）
  - NIC PTP 输出（T-BC）p-p 23.12 ns；NIC 1PPS p-p 3.75 ns；host 由 ePPS 恢复 1PPS mean −2.55 ns、p-p 3.5 ns [p10]（实验，看图）
  - PTM 2 级级联约 50 ns 时间误差，每级 RMS 28.8–35 ns [p10]（实验）
  - PTM 在 4×100% CPU 负载下：mean −57.3 ns，min −187.7 ns，max 67.0 ns [p8]（引用 Calnex ITU-T WD13-20，看图）
  - Flex IO 载波 10 MHz，ePPS 以占空比变化表示秒头 [p7]
- 提到的公司/客户/产品/标准：Skyworks、Calnex、ITU-T SG15/Q13、PCI-SIG PTM、OCP NIC 3.0 Flex IO、QSFP-DD MSA（ePPS）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（ePPS vs PTM 实测表）；p8（PTM 受 CPU 负载影响曲线）

### P114 01_AI Cluster Benchmarks – Establishing a standardized evaluation system
- 讲者/机构：Bing Liang（Huawei，标准代表）| 类型：标准进展
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [In 封装内：CXL/内存池化]
- 核心主张：
  - 超节点需要两类基准：AISBench（AI 训练/推理）与 ClusterBench（通用计算超节点、互连驱动的全栈能力）[p2]。
  - 三层指标框架：L0 硬件能力、L1 系统级指标（集合通信带宽、线性度、MTTR 等）、L2 应用级指标 [p5]。
  - ClusterBench 支持 UB、CXL、TCP 互连拓扑，用内存借用实现节点内存动态扩展 [p15][p16]。
- 关键数据：
  - AISBench 覆盖 70+ 数据集 [p3]；支持最多 250K 请求的高并发推理，分钟级指标计算 [p6]
  - 稳态 QPM 420 vs 全程 397，提升 6%；稳态吞吐 28.05 vs 26.47 req/s [p6]（实验，看图）
  - 250K 请求、4096/4096 token：内存 <64 GB、磁盘 4 GB、计算 150 s [p6]（看图）
  - Redis：1.33× 内存超配，吞吐 +23%；20 tiles 时约 62 万→约 76.5 万 QPS [p16]（实验，看图）
  - Openclaw：100 VM、CPU 超配 2.08，内存超配最高 2.5、借用 101 GB，任务成功率 100%，平均网页时延 17.9→28.3 s [p16]（实验，看图）
  - L0/L1 示例：跨节点内存访问 250 ns，节点间互连时延 1000 ns，RPC 时延 0.21 ms [p14]（示例）
  - 20+ 厂商 POC [p17]；40+ 客户采用 [p18]（自报）
- 提到的公司/客户/产品/标准：Huawei、UB（UnifiedBus）、CXL 2.0、Kunpeng 920、openEuler、GCC OAII、Inspur、Intel、Illuvatar、CESI、OpenICL、SWE-bench、τ²-Bench、vLLM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p16（内存借用案例与超配结果表）；p5（三层基准框架）

### P115 02_AI Tokenomics Explained
- 讲者/机构：Shruti Koparkar、Eduardo Alvarez（NVIDIA）| 类型：厂商展区 / 技术分享
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [Up 机柜/超节点：NVLink]
- 核心主张：
  - AI 经济性两大杠杆：选什么 token（模型复杂度、上下文、交互性）与选什么基础设施（成本、每瓦吞吐）[p2]。
  - MoE 降低每 token 计算与 HBM 带宽，但带来大量 all-to-all 通信，强依赖 scale-up 带宽 [p8][p9]。
  - 模型路由（NeMo Switchyard）按任务匹配模型可降低单任务成本 [p6]。
- 关键数据：
  - NeMo Switchyard：单模型 89 任务 \$179 vs 4 模型路由 90 任务 \$60，约 3× 更低单任务成本 [p6]（自报）
  - Kimi K3：2.8T 参数、108B 激活，896 专家 / 每 token 16 激活 [p8]
  - NVLink 6 switch tray：3× 更低时延、10× 更高包速率、130 TFLOPS 网内计算（对比基准未注明）[p10]（看图）
  - Agentic 负载：轮次 3→65、缓存 token 60%→98%、ISL 中位数 1K→142K、子代理 0→4 [p11]（引用 SemiAnalysis AgentX）
  - Vera Rubin NVL72 vs GB300 NVL72：每 MW token 吞吐在不同交互性下 2×/10×/30×；约 150 TPS/user 处每百万 token 成本低 45× [p13]（自报，看图）
- 提到的公司/客户/产品/标准：NVIDIA GB300 NVL72、Vera Rubin NVL72、NVLink 6、NeMo Switchyard、Nemotron Nano、Opus 4.8、Qwen 3.6、Gemma 4、Dynamo、llm-d、KVBM、NIXL、Mooncake、SGLang、TensorRT-LLM、vLLM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p13（VR vs GB300 吞吐/成本曲线）；p10（NVLink 6 scale-up 数字）
