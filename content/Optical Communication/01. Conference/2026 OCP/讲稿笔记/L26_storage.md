---
title: "L26_storage"
tags:
  - OCP2026
  - 讲稿笔记
---

# L26 笔记：server（P454/P464/P466）、storage（P469–P486）、systems-management（P490–P501）（低相关，精简版）

### P454 06_Onward Towards Industry Adoption – Demonstrating Modular Plug-and-Play
- 讲者/机构：Munir Ahmad（Lattice）、Phil Leech、Bill Scherer（HPE，M-PNP 工作组负责人）[p1] | 类型：标准进展
- 方向归属：主 [底座-机架/机械]（DC-MHS 模块化服务器管理）；次 [运维/可靠性/遥测]
- 核心主张：1) DC-MHS M-PNP 用自描述 JSON + FRU 让 BMC 自动发现 HPM 与外设，减轻 BIOS/固件集成负担 [p3,p5]；2) 用开源工具（校验器、FRU 打包、netlist/FPGA 转 JSON）推动落地 [p9]
- 关键数据：规范包当前 v0.7 [p3]；JSON schema 超过 5K 行 [p5]；v0.7 目标 2026-10，v0.9 在 2026 Summit 后 Q4，v1.0 目标 2027 Q1 [p22]；netlist2json 目标 2026 Q4、fpga2json 2026 Q4 末、JSON 转 Linux Device Tree 工具 2027 Q1 [p10,p11,p14]（均自报计划）
- 提到的公司/客户/产品/标准：HPE、Intel、Lattice、Dell（M-PESTI）、DMTF FRU DSP0220、LTPI、DC-SCM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（主板框图与 JSON 片段逐项对应，看图）

### P464 Managing-Open-Adapter-Card-OAC
- 讲者/机构：Ross Hamilton（AMD）、Marko Bartscherer（Intel）[p1] | 类型：标准进展
- 方向归属：主 [底座-机架/机械]；次 [运维/可靠性/遥测]
- 核心主张：1) OAC 管理从零设计：每块卡必有一条经 USB 2.0 的 MCTP/PLDM 管理通道（CONN0 第 11 列，+12V AUX 供电即可用）[p4,p5]；2) CID 取代机械键、SCD 取代 strap 针脚，配置变成数据而非针脚 [p6]
- 关键数据：管理控制器辅助电源 12 W [p4]；CID 取代机械键（传统方式 50+ 种潜在配置）、OAM 有 13 个 strap [p6]；规范 v0.9 已发布 [p9]（均自报）
- 提到的公司/客户/产品/标准：AMD、Intel、PCIe CEM、OAM、PLDM/MCTP/Redfish、OCP GPU Mgmt/RAS/FW Update 规范、OBMF-ICP
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（CID/SCD 与上电握手五步）

### P466 Reimagining-Data-Center-Power-High-Density-Architectures-for-Next-Gen-AI-Compute
- 讲者/机构：Gration Dsilva、Luocheng Wang、Ahmed Abou-Alfotouh（AMD）[p1] | 类型：技术分享
- 方向归属：主 [底座-电力]；次 [底座-冷却]
- 核心主张：1) 加速器 VRM 功率密度逐代上升，OAM 形态已到极限，需要垂直供电（VPD）[p3]；2) 呼吁标准化垂直电源模块的封装与 footprint、QnR 标准 [p8]
- 关键数据：二级电流密度 MI300X(2023) 0.88、MI355X(2025) 1.2、MI455X(2026) 最高 2 A/mm² [p3]；功率密度 0.11/0.15/0.33 W/mm³ [p3]；一级 IBC 从 4:1 变 8:1，输入 44–59.5 V，输出 5.5–7.4 V [p3]；<50 µΩ PDN 通路可支撑 >2 kA 且端到端效率 >80% [p4]；目标 3 A/mm²、<4 mm 高度、>80% 效率、<1 °C/W [p5,p8]（自报）；4000 A 时 200 µΩ 约 3200 W 损耗、50 µΩ 约 800 W（看图 p4）
- 提到的公司/客户/产品/标准：AMD MI300X/MI355X/MI455X、EAM、MPS、Infineon、Delta、Murata、TI、ADI、ST、Renesas、Flex
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（PDN 损耗 vs 负载电流，LPD 与 VPD 对比）；p8（电流密度趋势到 3 A/mm²）

### P469 Adopting-high-capacity-HDDs-navigating-throughput-and-IOPS-Limits-using-SAS-NVME-interfaces-for-the-AI-Cloud
- 讲者/机构：Hariharan Kumar、Balaji Natrajan（Microsoft Azure Storage）[p1] | 类型：技术分享
- 方向归属：主 [存储]；次 [推理/算力/经济性]
- 核心主张：1) 大容量 HDD 容量增长快于 IO，吞吐受接口、随机 IOPS 受单执行器限制 [p2]；2) 呼吁标准化 HDD 的 SAS4/NVMe 接口与 IOPS 倍数能力发现 [p11]
- 关键数据：接口链路速率 SATA3 6 Gb/s、SAS3 12、SAS4 22.5、PCIe5 x4 126、PCIe6 x4 252 Gb/s，对应相对倍数 2×/5×/10×/~50×/~100× [p5]；吞吐目标 9 MB/s/TB（基线 275 MB/s，70% 填充、70% 效率）[p7]；IOPS 目标 5–7 IOPS/TB（基线 140 IOPS）[p8]；JBOD 64 盘时 SAS3 <1×、SAS4 1×、PCIe5 1×、PCIe6 3× [p6]（自报模型）；OpenAI 检查点需 exabyte 级容量，训练停工损失“每天数百万美元” [p4]
- 提到的公司/客户/产品/标准：Azure Blob、OpenAI、Fairwater、SAS4、NVMe
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（接口速率天花板表）；p6（JBOD 共享上行倍数表）

### P470 Comprehensive-Testing-for-OCP-Datacenter-NVMe-SSD-Specification-Compliance
- 讲者/机构：Tim Sharp（Microsoft）、Rick Walsh（SANBlaze）、Nick Kriczky（Teledyne LeCroy）[p1] | 类型：面板
- 方向归属：主 [存储]；次 [运维/可靠性/遥测]
- 核心主张：1) Microsoft 为 OCP Datacenter NVMe SSD 规范开发开放测试用例，第三方工具商（SANBlaze、Teledyne LeCroy）实现 [p2,p5]；2) 号召共建开源行业测试标准 [p10]
- 关键数据：OCP 2.5 定义 183 个测试（新增 48）、2.6 为 191 个（新增 8）[p4]；2.7 将新增 6–10 个，2026-09 开始开发 [p4]；综合测试计划 2027 Q1 前贡献给 OCP [p5]；错误注入从 2.7 起改名事件注入，2.7 新增 10 类、2.8 新增 7 类 [p8]；SANBlaze 平台 16 盘、Teledyne 平台最多 48 盘支持 PCIe 4/5/6 [p13,p24]（自报）
- 提到的公司/客户/产品/标准：Microsoft、SANBlaze、Teledyne LeCroy、UNH-IOL、SPRandom、OCP Marketplace
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（各版本测试数量）

### P471 High-Capacity-QLC-Innovation
- 讲者/机构：Sebastien Jean（Phison）、Rory Bolt（Kioxia）、Yang Liu（ScaleFlux）、Mark Dancho（Sandisk）[p1] | 类型：面板
- 方向归属：主 [存储]；次 [推理/算力/经济性]
- 核心主张：1) 100+ TB QLC 的 DRAM 瓶颈可通过大 IU（Indirection Unit）、FTL 放入 NAND 解决 [p5,p15,p22]；2) 容量到百 TB 后，DRAM 成本、耐久与可靠性由控制器决定 [p18]
- 关键数据：128 TB 盘 L2P 所需 DDR 16K IU 下 32 GB，64K IU 下 8 GB [p6]；20 EB SSD 的 DRAM 成本约 \$1.5 亿，64K IU 降到 \$3700 万，省 \$1.13 亿（75%）[p6]（Phison 测算；假设 QLC \$0.589/GB、DDR5 \$28.83/GB [p3]）；L2P 缓存从 100% 降到 0% 每次读多 1 次 NAND 读，+47 µs [p4]；JEDEC 企业负载 WAF 从 2.5 升到 16.7 [p5]；ScaleFlux：128 TB 约 4 GB DRAM 对比约 128 GB，18 通道 + 裸片级 RAID6 可容 2/18 失效 [p18]；SPRANDOM 使 128 TB 预处理约 14 小时，原本约 12 天（256 TB 约 24 天）[p20]；E2（SFF-TA-1042）64 NAND 位置，E1.S 8、E3 16–32 [p21]；1 EB 部署用 NAND FTL 减约 78% DRAM [p24]（Sandisk 示例模型）
- 提到的公司/客户/产品/标准：Phison、Kioxia、ScaleFlux、Sandisk、FDP、E2/SFF-TA-1042
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（128 TB QLC 不同 IU 与 LUT 缓存的随机写性能，看图）；p24（NAND FTL 与传统 FTL 的 DRAM 对比表）

### P472 IO-Prioritization-for-Optimized-Command-Handling
- 讲者/机构：Anthony Constantine（Micron）、Yuliya Tarnikova（Google）、Chaitanya Kulkarni（NVIDIA）、Dan Helmick（Samsung）[p1] | 类型：面板
- 方向归属：主 [存储]；次 [推理/算力/经济性]
- 核心主张：1) NVMe TP4221 IO Prioritization：主机按提交队列设优先级并带“持续时间上限”，让高优先 IO 延迟更低更可预测 [p4,p5]；2) 不应采用被动式（接近上限再提权）架构，应通过仲裁权重达成上限 [p13,p14]
- 关键数据：Google 实验（NAND 级介质时间仲裁）p50 延迟约降 20%、p99 约降 50% [p8]（自报）；目标示例：高优先 500 µs@99.99%，中 1 ms@99%，低 10 ms@mean [p12]
- 提到的公司/客户/产品/标准：TP4221、WRR、WFQ、Command Duration Limits(HDD)、Linux kernel
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（三组参考负载与持续时间目标）

### P473 Increasing-Block-Sizing-Changes-Data-Placement-Economics
- 讲者/机构：Mike James（Sandisk，致谢 Liam Parker）[p1] | 类型：技术分享
- 方向归属：主 [存储]；次 [推理/算力/经济性]
- 核心主张：1) NAND 擦除块增大（2 代、TLC 到 QLC 增长 250%+），小 RU 的 FDP 需要更大 SLC 缓存，成本反超 [p2,p3]；2) 到 2030 大 RU 数据放置更便宜，且 Direct Write QLC 是关键使能 [p3,p7]
- 关键数据：擦除块从约 22–36 MB 增至约 100–140 MB [p2]；SLC cache 占比 100+ RUH/TB 约 4%(2024)→约 16.7%(2030)、200+ RUH/TB 约 7.6%→约 28.7%（看图 p6）；2026 Cost/TB 小 RU 最低（约 1.0 vs 大 RU 约 1.13），2030 大 RU 最低（约 0.84 vs 小 RU 1.0）（看图 p7，归一化约值）
- 提到的公司/客户/产品/标准：Sandisk、FDP、Direct Write
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（2026 与 2030 的容量与每 TB 成本对比）

### P474 NVM-Express-State-of-the-Union-NVMe-Technology-Roadmap-for-Hyperscale-Infrastructure
- 讲者/机构：Chris Sabol（Google）、Ross Stenfort（Sandisk）[p1] | 类型：标准进展
- 方向归属：主 [存储]；次 [安全]
- 核心主张：1) NVMe 2.4 规范集 2026-08-04 发布，11 份规范全部更新 [p5,p6]；2) 路线图含 NVMe over Ultra Ethernet、QoS、IO Prioritization、PQC 等 [p14]
- 关键数据：自 2.3 以来 17 个新工作项、15 个 TP 批准、11 个 ECN [p5]；NVM Express 成员 110+ [p3]；NVMe 2.4 新增 Subsystem Local Memory 与 Computational Programs 两份命令集规范（看图 p6）；Voltage Monitoring 可监控最多 4 路电压 [p9]
- 提到的公司/客户/产品/标准：NVMe 2.4、TP4213 TDISP、TP4176 速率限制、TP4221、IDC 预测引用 [p4]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（NVMe 功能路线图，含 NVMe over Ultra Ethernet）

### P475 Near-Line-SSD-the-Path-to-the-Future
- 讲者/机构：Steve Hetzler、Dave Palmer（Micron）[p1] | 类型：技术分享
- 方向归属：主 [存储]
- 核心主张：1) Near-Line SSD 适合大块随机/追加、目标 WA 1.5–2.0 以下的容量云存储负载，E2 外形最优 [p3,p4]；2) 建议用 Failure-in-Place：盘报告有效容量下降而非隐藏损坏，并由 OCP 制定系统级损失率规范 [p5,p7]
- 关键数据：示例 1,024 TB SSD、1,000 盘集群、10 年；盘内备件 1.9%（42 个/盘）对集群级 1% 备件，FIP 多 0.9% 容量，约少一半备件，节省约 10 PB [p6]（自报推算）
- 提到的公司/客户/产品/标准：Micron、E2（OCP DC NVMe 规范 10.9 节）、E3.L、FDP
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（两类负载对比表）

### P476 OCP-Storage-Specifications-Update-and-What-Customers-Care-About
- 讲者/机构：David Black（Dell）、Chris Sabol（Google）、Jeff Wolford（HPE）、Vineet Parekh（Meta）、Tim Sharp（Microsoft）[p1] | 类型：面板/标准进展
- 方向归属：主 [存储]；次 [安全]
- 核心主张：1) OCP Datacenter NVMe SSD 规范 v2.8 已完成，预计 11 月或 12 月初发布；CNSA 2.0 后量子加密现为必需 [p3,p4]；2) 五家客户共同关注：统一规范、PQC/SPDM 1.4.1 认证、遥测与延迟监控、液冷 [p9–p17]
- 关键数据：v2.8 要求固件双签名（CNSA 1.0 与 2.0）与 SPDM 1.4.1 [p4]；TCG 锁定范围最多 16 个 [p5]；NVMe 2.9 2027-04 至 09 完成，SAS-SATA 规范 2027-01 至 03 修订 [p6]
- 提到的公司/客户/产品/标准：Caliptra、OCP LOCK、OCP SAFE、SPDM、NVMe-MI、I3C、MCTP over USB
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（规范修订时间表）

### P477 Optimizing-SSD-Performance-Testing-using-FIO-Sprandom
- 讲者/机构：Dan Helmick、Vincent Kang Fu（Samsung）[p1] | 类型：技术分享
- 方向归属：主 [存储]
- 核心主张：1) Sprandom 一次写满物理容量即达到稳态分布，把预处理从天缩到小时 [p3,p4]；2) 对 PI 变化与主机利用率变化给出 spr_op 换算公式 [p12,p13]
- 关键数据：标准随机写达稳态需 2.5 天 [p5]；Sprandom 约 18 小时，传统 60 小时，稳态性能相同 [p14]；Sprandom 峰值约 2+ GiB/s 持续约 18 h，随后稳态 600 MiB/s [p6]；PI 从 0B 到 64B 使 spr_op 变化约 2.5% [p12]；曲线读数见 cloud_text（看图 p14）
- 提到的公司/客户/产品/标准：Fio、Sprandom（Steven Sprouse 等 2025）、OCP NVMe SSD 规范
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（稳态达成曲线：传统 vs Sprandom）

### P478 QLC-Storage-in-Hyperscalefleet
- 讲者/机构：Joseph Cirnigliaro、Vineet Parekh（Meta Fleet Systems Engineering）[p1] | 类型：技术分享
- 方向归属：主 [存储]；次 [推理/算力/经济性]
- 核心主张：1) QLC 适合读为主、容量密集的暖层，承接超出 HDD 写吞吐的新负载 [p3,p4]；2) 用 NVMe FDP 做主机侧放置可大幅改善耐久，并用缓存感知分配与块级自愈缓解瓶颈 [p15,p22]
- 关键数据：2026 单盘容量 TLC 61.44 TB、QLC 122.88–245.76 TB、HDD 26 TB；2U 24 盘密度 TLC 1.47 PB、QLC 2.95 PB、HDD 0.31 PB；QLC 持续顺序写 2.0–3.5 GB/s 对 TLC 6–10 GB/s [p4]；QLC 早期导入年换盘率：供应商 A 2.9、B 11.7、全部 3.7 [p7]（单位未写，疑为 %）；WAF 3–5× 使 QLC 耐久约为 TLC 的 20%；采用 FDP 后有效 DWPD 从 0.17 提到 0.96 [p13,p15]（现网）；缓存耗尽后持续写下降 3–10× [p19]；2 TB QLC 盘约 400 GB 后从约 6000 MB/s 掉到约 300–400 MB/s（看图 p20）
- 提到的公司/客户/产品/标准：Meta、OCP Endurance Storage System、NVMe FDP、OCP Data Center NVMe SSD 规范
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（TLC/QLC/HDD 对比表）；p20（缓存耗尽后写带宽悬崖）

### P479 QLC-Writes-the-end-of-SLC-caching
- 讲者/机构：Stephen Gold（Sandisk）[p1] | 类型：技术分享
- 方向归属：主 [存储]；次 [底座-电力]
- 核心主张：1) QLC 两遍编程的第一遍不持久，传统靠 SLC 缓存，但占用 OP、抬高 WAF、增加功耗 [p3–p8]；2) Direct Write 让第一遍可读，取消 SLC 缓存 [p9]
- 关键数据：SLC 缓存按耐久比 1:100、密度 25% 约占总容量 4% [p6]；OP 减 4% 使 NAND 写增 27%（WAF 3.81→4.85）[p7]；SLC 缓存使数据通路带宽与功耗均 4× [p8]；功耗惩罚约 1 W 每 1 GB/s 主机写 [p8]（自报模型）
- 提到的公司/客户/产品/标准：Sandisk、Direct Write
- 首次/记录/SOTA 声明：声称“新一代 QLC 编程方法”Direct Write [p9]
- 推荐配图页：p8（四次读写造成 4× 带宽与功耗）

### P480 Recent-Advancements-in-OCP-Telemetry-for-SSDs
- 讲者/机构：Kevin Brandt（Micron）、Dhankaran Ajravat（Meta）[p1] | 类型：技术分享
- 方向归属：主 [运维/可靠性/遥测]；次 [存储]
- 核心主张：1) Meta 与 Micron 用车队级遥测（SMART、DA1/DA2、延迟监控）把被动换盘转为主动处置 [p3,p4]；2) OCP 2.8 将 DA3/DA4 纳入 nvme-cli 人类可读区 [p10]
- 关键数据：延迟监控可发现主机检查漏掉的 P99.999999+ 尾延迟 [p8]；已在数千块盘启用 [p8]；nvme-cli OCP 插件 DA3/DA4 支持预计 2027 初发布 [p10]；NVMe-CLI 3.0 for Windows 已发布 [p11]
- 提到的公司/客户/产品/标准：Micron、Meta、nvme-cli OCP plugin、OCP DC NVMe SSD 2.7/2.8
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（Meta 与 Micron 的分工流程）

### P481 SNIA-SFF-spec-updates-to-the-Storage-Form-Factor
- 讲者/机构：Anthony Constantine（Micron，SNIA SFF TWG 联席主席）[p1] | 类型：标准进展
- 方向归属：主 [底座-冷却]；次 [存储]
- 核心主张：1) E1.S、E3、E2 规范新增冷却接口区，支持风冷与直接液冷 [p3–p5]；2) EDSFF 引脚规范 SFF-TA-1009 面向 PCIe 7.0、Streaming Boot 与 I3C 澄清 [p6–p8]
- 关键数据：平面度 E1.S <0.12 mm、E3.S <0.2、E3.L <0.25、E2 <0.40 mm；粗糙度均 <1.6 µm [p3–p5]；最大压力 E1.S 138 kPa、E3 103 kPa、E2 69 kPa [p3–p5]；PCIe 7.0 128 GT/s 奈奎斯特处 IL -7 dB、RL -7.33 dB [p7]；SFF-TA-1009 现为 4.1.5，计划年底发布 5.0 [p9]
- 提到的公司/客户/产品/标准：SFF-TA-1006/1008/1042/1009/1023、EDSFF
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（液冷 E1.S 冷却接口区与倒角）

### P483 Storage-Track-Introduction
- 讲者/机构：Ross Stenfort（OCP Storage 项目负责人，Sandisk）[p1] | 类型：主题演讲（议程）
- 方向归属：主 [存储]
- 核心主张：1) 回顾 OCP Storage 2024–2026 成果：Datacenter NVMe SSD 2.6/2.7/2.8、SAS-SATA 1.5、L.O.C.K. 0.5/0.8 [p5]；2) 邀请参与 Feedback CLA 流程 [p8]
- 关键数据：2026 年 5 月 Storage Tech Talk：22 场 31 位讲者 14 家公司，500+ 人在线 [p6]；OCP Marketplace 20+ SSD、5 项 SSD 测试服务 [p5]；Feedback CLA 流程 20+ 家公司参与 NVMe SSD 规范 [p8]
- 提到的公司/客户/产品/标准：Dell、Google、HPE、Meta、Microsoft、L.O.C.K.、HBF
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（OCP Storage 路线图）

### P485 The-Open-Flash-Platform-Serverless-Exabyte-Scale-Flash-Storage-with-Xsight-Labs-and-Hammerspace
- 讲者/机构：Floyd Christofferson（Hammerspace）、Gary Grider（Los Alamos）、Ted Weatherford、Jillian Kaplan（Xsight Labs）[p1] | 类型：厂商展区
- 方向归属：主 [存储]；次 [Out 后端网络]（400GbE DPU）
- 核心主张：1) 用基于 DPU、Linux 的闪存节点取代传统存储服务器 [p3]
- 关键数据：OFP sled 8 SSD、64 核 ARM DPU、2×400GbE、最多 1.97 PB；Tray 1RU、6 sleds、48 SSD、12×400GbE、最多 11.8 PB（按 245.76 TB QLC 的原始容量）[p2]（自报）
- 提到的公司/客户/产品/标准：Hammerspace、Xsight Labs、Los Alamos、Open Flash Platform Initiative
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（OFP sled 与 tray 设计）

### P486 Vertical-Optimizations-for-KV-Infrastructure
- 讲者/机构：Dongjoo Seo、Javier Gonzalez（Samsung Semiconductor）[p1] | 类型：技术分享
- 方向归属：主 [存储]；次 [推理/算力/经济性]
- 核心主张：1) KV cache 是临时、可重算的 AI 原生数据，SSD 需针对其优化 [p3]；2) 软硬协同（FDP 放置、大块传输）可降低 WAF 与 CPU 开销 [p6,p7]
- 关键数据：FDP 分离放置使 WAF 2.600→1.425（-45.2%），平均写延迟 -55.6%、读 -35.7%，p90 写 -29.4%、读 -22.0%（看图 p6；PM9D3a，960 GiB，89% 利用，合成 LMCache trace，非 TTFT）；大块传输使 CPU 开销从约 473–592 降到约 38–57 Mcyc/GiB（10–12×），超过 4 MiB 后收益递减 [p7]
- 提到的公司/客户/产品/标准：LMCache、Mooncake、HiCache、vLLM、SGLang、TRT-LLM、FDP、PM9D3a
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（工作负载类→PID→RUH 与 WAF 对比，看图）；p4（LMCache 分层存储架构）

### P490 From-Scale-to-Security-Evolving-GPU-Management-Standards-in-2026
- 讲者/机构：Krishna Sugumaran（AMD）、Sujoy Sen（Google）、Balaji Vembu（Meta）、Choudary Maddukuri（Microsoft）、Qian Wang（NVIDIA）[p1] | 类型：标准进展
- 方向归属：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：1) GPU 遥测配置面留在 Redfish，高量数据用 FlatBuffer 二进制替代 JSON [p7]；2) 固件更新增加 Fast Fail 预检与 MinSVN 与更新解耦 [p12,p15]
- 关键数据：GPU 管理标准 2023 年启动；固件更新 v1.1 于 2025-10 发布，v1.9 目标 2026-10 [p3,p10]；遥测接口含 Sensor Manifest（TypeID 2）与 Timeseries（TypeID 1），以 sensor_id 关联（看图 p8）
- 提到的公司/客户/产品/标准：Redfish、PLDM、SPDM、MCTP、ocp-diag-ctam、HGX、DMTF TrustedComponent
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（遥测二进制线格式结构）

### P491 GPU-CPU-Diagnostics-and-RAS-Standardization-Advances-for-Hyperscale-Infrastructure
- 讲者/机构：Rama Bhimanadhuni（Microsoft）、Taniya Siddiqua（AMD）[p1] | 类型：标准进展
- 方向归属：主 [运维/可靠性/遥测]
- 核心主张：1) AI 车队 KPI 变为每美元每瓦的有用智能，需用爆炸半径、诊断效能、MTTR 衡量 [p2,p3]；2) 恢复应在最小安全范围内完成，而非全作业检查点重启 [p9,p10]
- 关键数据：GPU RAS 需求 v1.7(2025)→v1.9(2026)，CPU 调试与 RAS v0.7→v0.9 [p4]；诊断分级 T1 5–10 分钟、T2 一小时内、T3 多小时 [p6]；诊断效能推荐 90%+（FR/(FR+FU)）[p7]
- 提到的公司/客户/产品/标准：Microsoft、AMD、NVIDIA、Google、Meta、Arm、Intel、OCPTV、ocp-diag-cpact
- 首次/记录/SOTA 声明：声称首个 CPU 诊断与调试需求、首个 GPU RAS 需求的行业标准化努力 [p4]
- 推荐配图页：p6（四级诊断深度与 MTTR 匹配）

### P497 OCP-Hardware-Fault-Management-Workstreams-Status-and-Relationship
- 讲者/机构：Drew Walton、Carlos Vallin（Microsoft）、Theodros Yigzaw、Shubhada Pugaonkar（NVIDIA）、Vilas Sridharan（AMD）、Samer El-Haj-Mahmoud（Arm）、Janusz Jurski、Marko Bartscherer（Intel）[p1,p2] | 类型：面板
- 方向归属：主 [运维/可靠性/遥测]
- 核心主张：1) RAS API 以 CPER/CPAD 为载体，映射到 DMTF PLDM（Type 7 文件）与 Redfish [p10–p14,p17]；2) FMFM 主张“不只数错误”，由内存厂商分析器提高故障归因精度 [p6 看图]
- 关键数据：RAS API 版本 0.96 已发布；HWFM Infrastructure Requirements 2.0 计划 2027 Q1（看图 p5）；Fatal/Critical CPER 必须发生时立即送达，不得延迟或批量 [p19]；CPAD 提交同步返回 202/400/403/404/413/507 [p21]
- 提到的公司/客户/产品/标准：DMTF PLDM DSP2094/DSP0242、Redfish、Micron、Samsung、Arm、Microsoft redfish-dev-server
- 首次/记录/SOTA 声明：无
- 推荐配图页：p17（RAS API 的 Redfish 映射步骤表）

### P498 Operating-OpenBMC-at-Hyperscale-What-Works-What-Breaks-and-What-Needs-to-Change
- 讲者/机构：Hari Ramachandran、Thirupathaiah Annapureddy（Microsoft）[p1] | 类型：技术分享
- 方向归属：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：1) OpenBMC 已在超大规模运行，但 ODM/芯片差异造成管理面不一致、生命周期成本上升 [p5,p6]；2) 需要 Redfish BMC 基线与跨厂商 MCTP/PLDM/SPDM 一致性测试 [p8,p9]
- 关键数据：数百万台 BMC、100+ 平台、500+ SKU、5+ ODM 合作伙伴 [p4]（自报，现网）
- 提到的公司/客户/产品/标准：OpenBMC、Redfish、MCTP、PLDM、SPDM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（规模数字）

### P500 Runtime-SBOMs-Extending-DMTF-Redfish-to-Connect-Build-Time-and-Live-Software-State
- 讲者/机构：Harsh Bhuwania、Prashant Dewan（Microsoft）[p1] | 类型：技术分享
- 方向归属：主 [安全]；次 [运维/可靠性/遥测]
- 核心主张：1) 缺少标准方法把已部署固件关联到正确 SBOM [p3,p5]；2) 提议在 OCP Hardware Management 与 DMTF Redfish Forum 共同定义最小关联记录，基于 SoftwareInventory、RelatedItem、ComponentIntegrity [p8,p9]
- 关键数据：2025 年发布 48,244 个 CVE，较 2024 约多 20%，引用 Synack 2026 报告 [p2]；示例 Yocto BMC 镜像约 500 组件、约 300 第三方、25,000+ 哈希文件 [p4]（示意，四舍五入）
- 提到的公司/客户/产品/标准：SPDX、CycloneDX、Redfish、SPDM、Synack
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（构建态与部署态 SBOM 关联缺口）

### P501 System-Level-Manageability-for-GPU-Platforms-Progress-in-the-OCP-System-GPU-Management-Workstream
- 讲者/机构：John Leung（Intel）、Hari Ramachandran（Microsoft）[p1] | 类型：标准进展
- 方向归属：主 [运维/可靠性/遥测]
- 核心主张：1) System GPU Management 工作组（2025 起、公开）接手 UBB 互操作性 profile 与 GPU 规范评审 [p3,p5]；2) 推进 Redfish 消息注册、聚合建模，并为 2027 年 IPMI FRU 日期回绕准备 [p6–p8]
- 关键数据：UBB profile v0.9.1→v2.0（采用 MultipartHttpPushUri）[p5]；IPMI FRU 生产日期字段将在 2027 年 11 月回绕 [p8]
- 提到的公司/客户/产品/标准：OCP UBB、DMTF DSP2090、DSP0220、DSP0257、PLDM Type 4、OpenBMC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（FRU 回绕问题与兼容路径）
