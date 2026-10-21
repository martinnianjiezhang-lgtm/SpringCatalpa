---
title: "L22_rack-power"
tags:
  - OCP2026
  - 讲稿笔记
---

# L22 笔记：Cooling Cold Plate / Open Platform Firmware / Rack & Power / Security / Composable Memory / Sustainability（低相关批次，精简版）

> 说明：本批 51 份均与 AI 光互连主线相关度低，按 NOTE_SPEC 规则 4 写精简版。方向归属主要为 [底座-电力] [底座-冷却] [底座-机架/机械] [安全] [运维/可靠性/遥测] [存储] [量子/其他]。"看图"=来自 cloud_text/L22.md 的图片识别。

## 一、Cooling：Cold Plate

### P001 A Novel Liquid Cooling Solution- A Negative-Pressure Two-Phase Water-Boiling Cold Plate
- 讲者/机构：Ken LC Cheng，Wistron | 类型：技术分享
- 方向归属：主 [底座-冷却]
- 核心主张：① 负压（亚大气压）水沸腾两相冷板兼具相变传热与水的低成本/基础设施兼容；② 系统低于大气压，破损时倾向吸入空气而非漏液，本征防漏 [p8]。
- 关键数据：
  - 局部热点热流密度：2025 约 3.3 W/mm²，预测 2027 前约 7.5 W/mm²（看图，预测）[p2]；芯片尺寸 2026 约 5000 mm²（5.5-Reticle）、2027 约 8000 mm²、2028 约 12000 mm²（14-Reticle）（自报，看图）[p2]
  - 实验：入口水约 30°C，2000 W；P2P 出口 1.64 psi（饱和 48.3°C）、P1P 出口 15.3 psi [p6]。6.5 cm² 加热面积、低流量(约 0.8 LPM)下两相比单相热阻低 15%（约 0.044 vs 0.050 K/W）；40 cm² 面积下低 7%；流量 ≥3–4 LPM 两者趋同（实验，看图）[p6]
  - 热阻分解（2000 W，6.5 cm²，0.8 LPM）：subcool 51.8%、boiling 17.8%、pedestal 10.5%、TIM 19.9%（实验，看图）[p7]
  - 未解决：压力敏感、大规模网络压降与流量分配、长期可靠性与启停策略 [p10]
- 提到的公司/客户/产品/标准：Wistron
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（P1P/P2P 热阻对比曲线）；p7（热阻分解）

### P004 Considerations for Shipping and Storage of 1-Phase Cold Plate Liquid Cooled Racks & Servers
- 讲者/机构：Cheng Chen（Meta）、Sean Sivapalan（Nvidia）| 类型：技术分享
- 方向归属：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：① 单相冷板液冷整机柜/服务器的运输与存储需要标准化，目前各厂家协议分化 [p20]；② 给出 Wet / Partial Wet / Dry / Semi Dry 四种模式，按物流与运维资源选择或组合 [p4-p8, p17]。
- 关键数据：
  - 流体膨胀：升至沸点时 PG25 与水均膨胀约 4%；降至冰点时 PG25 约 2–5%、水约 9%；冻胀风险大于高温膨胀（自报）[p10]
  - 装液率：Wet 近 100%、Partial Wet 90–95%、Dry <10%、Semi Dry <50%（看图）[p9]；风险：腐蚀风险 Wet 低/Partial Wet 中/Dry 低/Semi Dry 高；Wet 需运输控温，货架期 Wet 长、Partial Wet 与 Semi Dry 短（看图）[p9]
  - 经验建议：早期样机 Partial wet；量产机柜 Wet 或 Dry；服务器 FRU 库存 Wet 或 Dry；RMA Wet 或 Semi Dry（自报）[p17]；存储控温 20–25°C [p13]；参考标准 IEC 60721-3-2 [p12]
- 提到的公司/客户/产品/标准：Meta、Nvidia、IEC 60721-3-2、OCP 白皮书（2026 年 3 月）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（四种模式权衡表）

### P006 Deep Dive- Biomanagement for Liquid Cooling
- 讲者/机构：Dakota Bunn（Nalco Water, Ecolab）、Sean Sivapalan（NVIDIA）| 类型：技术分享
- 方向归属：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：① PG≥25% 是被动抑菌（biostatic）的工程指引而非保证，不能杀菌 [p5-p7]；② 微生物控制应基于风险分级取样，板计数与 ATP 代谢测试需联合看趋势 [p9-p11]。
- 关键数据：
  - PG≥25% 时稳定计数约 10²–10³ CFU/mL（自报）[p7]；现网样本在 PG 25–27.2% 下 TVC 仍有 500–160000 CFU/mL、Pseudomonas 200–6800 CFU/mL（现网，看图）[p4]
  - 建议取样频率：低风险半年、中风险季度、高风险月度或事件触发；具体频率待 OCP fluids workstream 确定 [p10]
  - 板计数需 24–48h+，ATP 数分钟出结果 [p9]
- 提到的公司/客户/产品/标准：Ecolab/Nalco、NVIDIA、OCP fluids workstream
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（PG 浓度与微生物计数散点）；p10（风险分级取样框架）

### P007 Fluid Monitoring- From Sensors to Insights
- 讲者/机构：Pascal Michel（Nordran）、Sreya Dutta（Dynalene）、Mike Murcia（Ecolab）、Sean Barlett（Switch）| 类型：技术分享
- 方向归属：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：① 单个传感器已能检出有意义的 upset，但整体检测需多测量+模型，最优在线测量集仍在演进 [p17]；② 冷却液类型决定哪些参数最重要 [p17]。
- 关键数据：
  - 测试对象 PG25 四类：RPG（无抑制剂）、IAT、OAT、LEC（低电导 <5 µS/cm）[p4]
  - 热老化 450 h：含铜 100°C 下 RPG-1 生成酸 41 ppm、铜溶出 9 ppm，pH 降 2.04（实验，看图）[p6]
  - 单变量检测裕度（IAT）：磷酸盐变化 → 电导率 21.2、储备碱度 11.1；稀释 → glycol%(RI) 6.1；Na-TTA 变化各传感器裕度仅约 1.0–1.2；pH 对污染物裕度 0.0（实验，看图）[p11]
  - 自来水稀释 50 vol% 时浊度升至基线约 1250%；DI 水保持约 100%（实验，看图）[p9]
  - 贡献计划：实时监测指南 Q4 2026，PG 流体 upset 测量 Q1 2027 [p18]
- 提到的公司/客户/产品/标准：Nordran、Dynalene、Ecolab、Switch；OCP Cooling Environments Fluid Health 工作组
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（检测裕度矩阵）；p15（传感器选型表）

### P011 Reducing Operational Complexity Through Standardized Two-Phase Liquid Cooling for AI Infrastructure
- 讲者/机构：Jiu Xu（Meta）、Powpow Wu（ASRock Rack）、Remco Van Erp（Corintis）、Jake Hsieh（Wiwynn）、My Truong（ZutaCore）、Samer Saab（Chemours）| 类型：面板
- 方向归属：主 [底座-冷却]
- 核心主张：两相冷板技术已就绪，生态需围绕接口、规范与部署标准对齐，从定制走向开放互操作 [p4]。
- 关键数据：无具体数字；讨论议题为两相回归原因、超大规模运维现实、硬件 OxM 困境、先标准化什么 [p3]。
- 提到的公司/客户/产品/标准：Meta、ASRock Rack、Corintis、Wiwynn、ZutaCore、Chemours；OCP Cooling Environments
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P012 System-level Challenges and Considerations in Transitioning from Single-Phase to Two-Phase Cooling
- 讲者/机构：Jake Hsieh、Yuzhou Lin，Wiwynn（测试数据来自 AVC）| 类型：技术分享
- 方向归属：主 [底座-冷却]
- 核心主张：① 单相转两相不是部件替换，涉及工质、流动不稳定、流动架构、回路四方面 [p2]；② 当前 R515B 与 R1233zd(E) 是数据中心两相的关键候选，需两相优化冷板 [p5, p12]。
- 关键数据：
  - 水单相(Cp×ΔT, ΔT=10°C)吸热 41.8 kJ/kg，两相汽化潜热 2,257 kJ/kg；换热系数 单相强制对流 100–40,000，对流沸腾 2,500–100,000 W/m²K（引用 Incropera）[p3]
  - 工质：R134a 45°C 饱和压力 1155 kPa、潜热 158、GWP 1300；R1234yf 1150 kPa、A2L；R515B 871 kPa、GWP 299；R1233zd(E) 251 kPa、潜热 180、GWP 1（自报表）[p5]
  - R134a vs R1233zd(E)，同冷板 0.7 LPM：R134a 热阻约 0.024–0.0277 ℃/W、压降约 3–20 kPa；R1233zd(E) 热阻约 0.0268–0.0325、压降约 5–42 kPa（实验，AVC，看图）[p6]
  - 压降 100 kPa 假设下，R1233zd 饱和温度 50→37℃（设施水 29℃），R1234yf 50→46℃（设施水 38℃）（自报，计算）[p7]
  - PG25 单相与两相工质：同为 PG25 设计冷板，1.5–4.5 LPM 下 PG25 结温约 74→65℃，R515B 约 76→73℃（3 kW TTV，入口 25℃）；2 kW(240 W/cm²) 时 R1233zd 结温均值约 93℃ vs PG25 约 78.5℃（实验，看图）[p9]
- 提到的公司/客户/产品/标准：Wiwynn、AVC、R134a/R1234yf/R515B/R1233zd(E)、ASHRAE 分类
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（R134a vs R1233zd 热阻与压降）；p9（PG25 与两相工质对比）

## 二、Open Platform Firmware (OPF)

### P013 Advancing Flash-less Boot in OCP Systems- A Streaming Firmware Architecture for Secure and Scalable
- 讲者/机构：Munir Ahmad（Lattice）、Alex Cervantes（Intel）| 类型：技术分享
- 方向归属：主 [安全]；次 [运维/可靠性/遥测]
- 核心主张：① Flash-less boot（存储模型）与 Streaming boot（交付方式）互补，DC-SCM 2.1 + RoT 是 CPU BIOS 流式启动的使能平台 [p10]；② 去掉本地 SPI NOR 可降低供应链攻击面并简化万级节点固件更新 [p2]。
- 关键数据：
  - 流程时间线：t=0 FPGA 从 OTP 配置，约 1s BMC 启动，约 2–6s CPU 运行 Early FW，t>20s OS 引导（设计示意）[p5]
  - Early FW ≤4 MB，用 64–512 KB Cache-as-RAM；Secondary FW 32–256 MB，DRAM 可用；Early FW 用 SHA-384 整体验证，Secondary 用 4 KB 页 SHA-256 [p7]
  - FPGA 内部 SRAM 1–4 MB（MachXO5D）；复位向量 PLTRST# 解除后平台超时通常 <500 µs [p8]
  - 已有落地：Flash-less 已验证于 HPE Gen11、OVHcloud；Streaming 验证于 NVIDIA BlueField、Azure（自报）[p10]
- 提到的公司/客户/产品/标准：Lattice、Intel、HPE Gen11、OVHcloud、NVIDIA BlueField、Azure、NIST SP 800-193、SPDM、PLDM、OCP Recovery v1.1、DC-SCM 2.1
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（Flash-less 端到端框图）；p4（两种方式对比）

### P014 Building Bridges for Adoption- OCP, Standards Bodies, and Open‑Source Firmware
- 讲者/机构：Michael Kinney（Intel）、Christian Walter（9elements）、Dong Wei（ARM）、Allison Goodman | 类型：面板
- 方向归属：主 [安全]（固件生态）
- 核心主张：OPF 的 openSFI/UPCI 需与 UEFI、ACPI、DMTF Redfish、openBMC、coreboot、Tianocore 等标准与开源社区协同，"由对立转协作" [p2-p3, p5]。
- 关键数据：无数字。
- 提到的公司/客户/产品/标准：Intel FSP、AMD openSIL、ARM Trusted FW、coreboot、Tianocore、openBMC、DMTF Redfish、UEFI、TCG
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（协作接触点全景）

### P015 Decoupling Silicon Dependencies from Control Plane Firmware
- 讲者/机构：Sarathy Jayakumar（AMD）、Rama Bhimanadhuni（Microsoft）| 类型：技术分享
- 方向归属：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：BMC 固件把各硅厂商库静态链入，每次 errata 都要重建、重验、全网刷新；主张延后绑定（vendor 签名、BMC 验证、可度量、反回滚）[p6-p9]。
- 关键数据：
  - 车队需支持 7+ 年；硅修复到上线最坏"数天到数月" [p2, p4]（自报）
  - 配置修复=文件推送+服务重启；代码修复=完整固件发布 [p4]
- 提到的公司/客户/产品/标准：AMD、Microsoft、OpenBMC、MCTP VDM、Redfish OEM、CPER
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（静态链接 vs 延后绑定）

### P016 From Code to Data- Advancing the Unified Platform Configuration Interface (UPCI)
- 讲者/机构：Felix Polyudov（AMI）、Tim Lewis（Insyde）| 类型：标准进展
- 方向归属：主 [运维/可靠性/遥测]（固件配置）
- 核心主张：UPCI 把平台配置从代码驱动改为数据驱动，开发期用 HRR（YAML/JSON）、运行期用 MRR，经 Firmware Handoff Transfer List 传递 [p2-p3, p7-p10]。
- 关键数据：待解决：定稿 HRR/MRR schema，定义 CPU/内存/PCIe 等 UPCI 数据结构 [p12]；无其他数字。
- 提到的公司/客户/产品/标准：AMI、Insyde、openSFI、Firmware Handoff 规范、ACPI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（开发期架构：UPCI 编译器）

### P017 Open Platform Firmware (OPF) - project update
- 讲者/机构：Murugasamy Nachimuthu（Oracle）、Raj Kapoor（AMD）| 类型：标准进展
- 方向归属：主 [运维/可靠性/遥测]
- 核心主张：OPF 有三个活跃工作组（openSFI、UPCI、固件更新），后两类规范 0.5 版进行中，下一版本预计 2026 年底 [p4-p6]。
- 关键数据：openSFI Spec 0.3 已发布，0.5 开发中；UPCI Spec 0.3 评审中；Firmware Update 为新工作组 [p5]；OPF 每两周周四 9–10 am PT 例会 [p4]
- 提到的公司/客户/产品/标准：AMD、Oracle、Microsoft、Insyde、AMI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（OPF 议程）

### P018 Scaling Memory Safe Security Across Firmware Stack
- 讲者/机构：面板：Raj Kapoor（AMD）、Oleg Ilyasov（AMI）、Bertrand Achard（Google）、Tim Lewis（Insyde）、Giri Mudusuru（Microsoft）、Sammy Nachimuthu（Oracle）| 类型：面板
- 方向归属：主 [安全]
- 核心主张：幻灯片仅有讲者页与讨论页，未见论点。
- 关键数据：无。
- 提到的公司/客户/产品/标准：AMD、AMI、Google、Insyde、Microsoft、Oracle
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P019 The Next Evolution of Intel's FSP- Aligning to openSFI and UPCI
- 讲者/机构：Michael Kinney、Chad Tsai，Intel | 类型：厂商技术
- 方向归属：主 [安全]（固件接口）；次 [运维/可靠性/遥测]
- 核心主张：数据中心版 Intel FSP 将 FSP-M 与 FSP-S 解耦，对齐 openSFI 的无状态执行模型，且不改 FSP 规范，不影响 bootloader 代码 [p5, p8]。
- 关键数据：FSP 当前 V2.5，支持 64 位执行环境与 SMM [p4]；改造覆盖 Xeon 6 与下一代 Xeon [p6]；FSP-M 在临时 RAM 运行，FSP-S 在物理内存运行 [p8]
- 提到的公司/客户/产品/标准：Intel FSP、Xeon 6、TianoCore/EDKII、coreboot、Slim Bootloader、openSFI、UPCI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（FSP 无状态化 before/after）

### P020 Trusted, AI-Ready Open Firmware- From Auditable Foundations to Agentic Lifecycle Automation
- 讲者/机构：Paul Grimes（AMD）、Chitrak Gupta（AMI）| 类型：技术分享
- 方向归属：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：① DC-MHS/M-PnP 模块化使每个 HPM/DC-SCM/riser 组合都是独立固件目标，固件决定平台进度 [p2]；② 提出五层自动化（AI-ready 仓库、确定性构建、AI 辅助生成、安全即构建产物、七 Agent 编排），人类审批 merge/sign/promote/deploy [p3, p13, p15]。
- 关键数据：七类 agent（Supervisor、Source Management、Platform Config、Build、Security、Test、Deployment）（看图）[p14]；AMI 计划 2027 年 Q1 前贡献开源固件管理方案与 mPnP FPGA/FRU JSON 生成工具 [p17]；衡量指标含平台移植时间、首次启动成功率（无数值）[p16]
- 提到的公司/客户/产品/标准：AMD、AMI、OpenBMC、EDK2、Redfish、SPDX/CycloneDX、in-toto/SLSA、EU CRA、openSIL
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（七 Agent 架构）；p3（四层自动化）

### P021 openSFI Update- Advancing Silicon Firmware Interoperability
- 讲者/机构：Raj Kapoor、Albert Rennie（AMD）、Allison Goodman | 类型：标准进展
- 方向归属：主 [运维/可靠性/遥测]（固件接口）
- 核心主张：定义主机固件与硅固件之间的厂商无关接口，主机固件掌握系统资源、硅固件执行；v0.5 引入统一阶段（MEM_INIT、SI_RECONFIG、POST_PCI、PREPARE_OS_HANDOFF、EXIT_HOST_FW）[p4-p6]。
- 关键数据：路线：Spec v0.5 2026 年 12 月，v0.8 2027 Q1，v1.0 2027 Q3；VAL PoC 由 MiTAC + AMI 牵头（自报）[p9]；v0.3 于 2025 Q3 Global Summit 发布，覆盖 3 家硅厂商 PoC [p3]
- 提到的公司/客户/产品/标准：AMD、MiTAC、AMI、Firmware Handoff 规范、EU CRA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（OSIP 四阶段）；p9（路线图）

## 三、Rack & Power

### P022 800V Data Center DC-DC Design Considerations, Topology Comparisons, and Trade-offs
- 讲者/机构：David Reusch，Texas Instruments | 类型：厂商技术
- 方向归属：主 [底座-电力]
- 核心主张：① 从 800VDC 到 <1V 的最佳路径并不简单，Vertical Power Delivery (VPD) 是"明显赢家" [p10]；② GaN/SiC 器件及隔离保护、偏置电源、栅驱、遥测是 800V 的使能项 [p10]。
- 关键数据：
  - 单处理器功率约 200 W → 约 2000 W（20 年）[p2]
  - 20 kW 下五种 800V→0.8V 架构端到端效率：16:1+4:1(LPD) 67%；16:1+8:1 → LPD 64% / VPD 73%；64:1 → 68%；128:1 → 74%；16:1+50V 稳压+集成 Buck 73%（自报，看图）[p6]
  - 50Vin–6Vout LLC 单模块 750–1000 W、约 96–97% 效率、约 2000 W/in³；800Vin–6Vout 堆叠 LLC 10,000 W、约 94–96%、约 2000 W/in³（自报）[p8]
  - 800V 保护：SiC，<1 µs 短路保护 [p9]
- 提到的公司/客户/产品/标准：Texas Instruments、NVIDIA 800VDC MGX 机柜
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（五种 800V 架构效率对比）；p4（四种电压路径）

### P023 800V direct-to-server and power shelf solutions
- 讲者/机构：Harry Soin、Andy Brown，Advanced Energy | 类型：厂商技术
- 方向归属：主 [底座-电力]
- 核心主张：LVDC（指 ±400V/800V）越深入设备越受益，但安全（>60Vdc 属危险电压）、EMI、冷却是挑战；提供 100 kW/160 kW 电源柜与板载 DC-DC 模块 [p4-p8]。
- 关键数据：
  - 100 kW 与 160 kW power shelf 均用 18 kW PSU；输出母线连接器 4 kA（BK5000）/BK2000；160 kW shelf 855×46×1086 mm（自报）[p9]
  - 隔离 DC-DC 功率密度已超过 2000 W/in³ [p11]；800V→50V 模块效率 >98% [p10, p13]；50V→12V 模块 98%，900/1300/1600/>2500 W [p14]
- 提到的公司/客户/产品/标准：Advanced Energy、Mt Diablo、HPRv2、IEC62368、IEC60664
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（100 kW 与 160 kW 对比）

### P025 Enabling 1MW+ IT rack power with an open rack busbar interface
- 讲者/机构：Hal Loket、Aniket Singh，TE Connectivity | 类型：厂商技术
- 方向归属：主 [底座-机架/机械]；次 [底座-电力]
- 核心主张：为 IT 机柜 800VDC 母线提出兼容 ORv3 35mm 宽度、深度可扩展、防触电的母线接口，缩小 Diablo 之后 IT 机柜侧空缺；TE 产品尚未作为 OCP 贡献授权 [p2, p4-p5]。
- 关键数据：
  - 机柜功率：2021 约 100 kW，2024 约 1 MW，2027 起 1.5 MW+（自报）[p3]
  - 母线规格：500 kW/约 625 A、750 kW/约 937 A、1 MW/约 1250 A；尺寸 2134×35×(80/130/200) mm [p6]
  - 温升：环境 55°C、无风冷下 29.27/28.22/29.76°C（仿真）[p9]；625 A 实测最大约 27°C，与仿真偏差约 6%（实验）[p10]
- 提到的公司/客户/产品/标准：TE Connectivity、ORv3、Diablo/Mt Diablo、UL 62368
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（三种母线规格）

### P027 MGX Power Rack Reference Design
- 讲者/机构：Jared Huntington，Nvidia | 类型：技术分享
- 方向归属：主 [底座-电力]
- 核心主张：BBU 与 N+N 冗余推动独立电源机柜；建议将 125/157 A 800 VDC 连接器、100 A 多导体 whip 作为标准接口，AC 输入电流整形成为 AI 负载标准要求，电源冷却转向液冷 [p2, p14]。
- 关键数据：
  - 第二代：100% 液冷，储能 65→100 J/kW，880 kW N 带 BBU，90 s 保持时间 [p10]
  - 连接器：UL 1682 盲插 157 A；Compute rack 总额定最大 380 kW；AC/DC shelf 110 kW、DC/DC shelf 95 kW（看图）[p9]
  - 液冷母线夹 2036 A，RMS 发热 +11% [p12]
  - 单导体 whip：弯曲半径 -64%，新型硅胶绝缘再 -50% [p5]
- 提到的公司/客户/产品/标准：Nvidia、UL 2137、UL 1682、UL 817A
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（800VDC 157/125A 连接器场景）；p13（Power Center 布局）

### P028 Mitigating AI Training Power Oscillations- Utility Requirements and In-Rack Power Filtering
- 讲者/机构：Bo Wen、Xianyong Feng、Luz Belmont，Microsoft | 类型：技术分享
- 方向归属：主 [底座-电力]
- 核心主张：① 大规模 AI 训练的功率振荡会触发电网稳定性问题，电力公司已提出 5 s 窗口等限值 [p5-p6]；② 机架内电容滤波（含电容托盘/shelf）是可行方案，"从电力电子角度无技术障碍"，需更好电容与预测算法 [p11, p14]。
- 关键数据：
  - 电网谐振频段：区域间 0.1–0.5 Hz、区域 0.5–0.8 Hz、本地 0.8–2 Hz、次同步 5–55 Hz [p3]；接口阻抗稳定 13–27 Hz [p5]
  - 限值：MISO 10 MW/5 s 滑窗、30 MW/min；ERCOT 10 MW/5 s；SOCO 0.1–5 Hz 单频 10 MW、5–55 Hz 2.5 MW、20 MW/min；AESO 初期 0.16 MW、10 MW/min（自报，表）[p6]
  - 电容 DoD = 1-(Vmin/Vmax)² [p11]
- 提到的公司/客户/产品/标准：Microsoft、MISO、ERCOT、SOCO、AESO、LIPA、OCP Power capacitor shelf(2024)
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（各电网负载变化限值表）；p10（滤波器放置位置）

### P030 Open Rack Wide (ORW)- Progress, Validation, and What's Next
- 讲者/机构：Cecilia Galvan（Meta）、Indro Subramaniam（Rittal）| 类型：标准进展
- 方向归属：主 [底座-机架/机械]
- 核心主张：ORW 为 ORv3 HPR 双宽版本，支持更大质量与功率（液冷母线 >700 kW），v1.0.0 已于 2026-04-28 发布，2026-11 量产开始 [p3-p4, p11]。
- 关键数据：
  - ORW vs ORv3 HPR：宽 1200 vs 600 mm；高 2386 vs 2286 mm；深均 1219 mm；最大载荷 4,700 vs 1,400 kg（上年 OCP 2025 为 3,500 kg）；免工具导轨 125 vs 80 kg [p6]
  - 验证：4,700 kg 载荷下随机振动、翻转/平面跌落、4 次 17° 倾斜，全部通过（实验）[p9]
  - 拉出力目标 625 N [p8]
- 提到的公司/客户/产品/标准：Meta、Rittal、ORv3 HPR
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（ORW 与 ORv3 HPR 规格对比）

### P031 Powering the AI Rack of the Future- A Scalable 800 V DC Sidecar Architecture
- 讲者/机构：Justin Mark Herrmann（Rittal）、Sven Finke（Bosch）| 类型：厂商技术
- 方向归属：主 [底座-电力]
- 核心主张：480VAC 约在 300 kW 达到极限，800VDC 部署必须；用 Power Module on Cooler (PMoC) 提升单 PSU 功率并降低模块数；液冷 sidecar 无功率上限，风冷约 600–700 kW [p2-p4]。
- 关键数据：
  - 部署路线（引用 NVIDIA）：2026/27 660–800 kW sidecar；约 2028 1.5–2 MW power center；约 2029 4–5 MW；2030+ 中压直接转换 [p2]
  - PMoC 单 PSU >200 kW，800 kW 仅需 4 个、2 MW 需 10 个；PCB 方案约 20 kW/模块，800 kW 需 40 个、2 MW 需 100 个；密度 100 kW/OU vs 约 60 kW/OU（自报）[p3]
  - 风冷/液冷 800 kW 需风量 59.7 m³/min vs 冷却液 34.8 l/min；风速 600 kW 达 10.9 m/s 触限（看图）[p4]
  - 示例：800 kW/21 kWh sidecar 含 825 kW/21 kWh BBU（24 OU）；2 MW LV 整流机柜 [p8]
- 提到的公司/客户/产品/标准：Rittal、Bosch、NVIDIA、ORv3
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（风冷 vs 液冷风量/液量）；p3（PMoC vs PCB）

### P032 Rack and Power ( Opening and update)
- 讲者/机构：Harry Soin（Advanced Energy）、Steven Moore（Rittal）| 类型：标准进展
- 方向归属：主 [底座-电力]
- 核心主张：Rack & Power 路径：2025 LVDC sidecar（50V IT 机柜）→ 2027 Mt. Diablo/AC busway → 2028+ 设施级 LVDC 与直连服务器、端排 SST；新设 LVDC Power Delivery 子项目 [p3, p7]。
- 关键数据：电源柜演进：ORv3 18 kW → HPRv1 33 kW → HPRv2 72 kW → HPRv4 100 kW/160 kW [p4]；新子项目由 Meta、Google、Microsoft、Nvidia 共同牵头，首次会议 11 月 [p7]
- 提到的公司/客户/产品/标准：Meta、Google、Microsoft、Nvidia、TE、DMTF Redfish
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（电力架构迁移）

### P033 Scaling Hyperscale Power Delivery- Managing Aggregated and Cascaded Power Shelf Architectures
- 讲者/机构：Praveen Kumar Velpuri、Yang Hsiung，Microsoft | 类型：技术分享
- 方向归属：主 [底座-电力]；次 [运维/可靠性/遥测]
- 核心主张：机架级软件协调持续容量，本地硬件保护快速电气限值；聚合（单母线）利用率高但故障域大，级联分区故障域小、利用率略低 [p3, p7, 看图 p5]。
- 关键数据：四项机架 KPI：可用容量、瞬态响应(ms)、故障影响、恢复时间 [p8]；故障场景：单 PSU 失效 0 trays，zone 母线短路 ≤3 trays（设计示意，看图）[p9]；母线 ±400 VDC，shelf 内 N+2（看图）[p5, p9]
- 提到的公司/客户/产品/标准：Microsoft、Redfish（讨论项）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（聚合 vs 级联对比表）；p9（故障遏制）

### P035 Simplifying High-Density Deployments- Reducing AC Whip Complexity in Multi-Power Shelves Open Rack
- 讲者/机构：Harry Chen，Schneider Electric | 类型：厂商技术
- 方向归属：主 [底座-电力]；次 [底座-机架/机械]
- 核心主张：为多 33/72 kW power shelf 的 ORv3/ORW 机架提出模块化 AC PDU（刀片级短路保护）减少 AC whip；两种方案：机架顶横置、机架背部竖挂 [p3-p4]。
- 关键数据：AC whip 从 16 减到 8（最大）[p7]；单 Feeder Box 宽 72 mm，8 个模块可排入 600 mm [p8]；输入 125 A 馈电，power shelf 2×60 A [p6]；原型反馈 2027 Q1，量产 2027 Q3 [p19]
- 提到的公司/客户/产品/标准：Schneider Electric、ORv3、ORW
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（whip 16→8）

### P036 The Power Distribution sub-project at OCP - Low Voltage DC Distribution in Data Centers
- 讲者/机构：Paolo Catapane（ABB）、Joshua Buzzell | 类型：标准进展
- 方向归属：主 [底座-电力]
- 核心主张：该子项目编写 LVDC 配电白皮书与基础规范，覆盖系统架构、电压与电能质量、接地、保护、控制、EMC、法规标准 [p3, p5]。
- 关键数据：
  - 800+ groups.io 订阅者，约 100 名负责人与活跃贡献者，250 页白皮书，10 个月 2 次白皮书发布 [p6]
  - EV 充电 Y 电容限值：CCS（≤400 kW）5 µF；MCS（如 1 MW）拟 30 µF [p10]
  - 示例系统：34.5 kVAC/800 VDC SST，6–8 MVA，2,500 A SSCB（看图）[p7]
  - 机架 LVDC 输入 PSU 电压区：连续运行约 ±420/840 至 ±370/740 VDC；±460/920 VDC 触发保护（看图）[p16]
  - 800V 机架 DC-DC shelf 与 PDB：约 200 kW 以下 shelf 常用，500–700(?) kW 以上 PDB 常用（看图，存疑）[p15]
  - 路线：2026 Global Summit 前后基础系统规范 v0.5、组件规范 v0.5，2027 v1.0 与 UL/IEC/IEEE 标准化 [p22]
- 提到的公司/客户/产品/标准：ABB、Eaton、Siemens、Vertiv、Schneider、UL Solutions、Delta、AMD、IEC 61851-23
- 首次/记录/SOTA 声明：无
- 推荐配图页：p16（电压分区与运行定义）；p15（shelf vs PDB 适用功率）

## 四、Security

### P037 Advancing Caliptra Security Through Open-Source DV Infrastructure
- 讲者/机构：Andreas Kurth（lowRISC）、Zach Halvorsen（Google）| 类型：技术分享
- 方向归属：主 [安全]
- 核心主张：开源设计验证（DV）把验证变成 IP 的可复用属性；Caliptra 与 OpenTitan 共享 DV 框架（DVSim、UVM agent），采用可渐进 [p11-p14]。
- 关键数据：VeeR 约 22 个块级测试台 [p7]；I3C 约 90 个 cocotb 测试、约 87k 行代码，实现 OCP Secure Firmware Recovery v1.1-rc5 [p9]；SHA3_CTRL 从 OpenTitan 移植后数周跑通 [p8]
- 提到的公司/客户/产品/标准：lowRISC、Google、Caliptra、OpenTitan、VeeR、Verilator、cocotb、RISC-V DV、CHIPS Alliance
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（块级 DV 移植流程）

### P040 Architectural Masking for PQC- Adam's Bridge 3.0 Leveraging NTT Linearity
- 讲者/机构：Mojtaba Bisheh-Niasar、Kiran Upadhyayula，Microsoft | 类型：技术分享
- 方向归属：主 [安全]
- 核心主张：利用 NTT/INTT/PWM 的线性，把输入分成两份分别过未加防护的数据通路，以架构级掩码替代数据通路级掩码，面积减小且性能略升；覆盖 ABR 2.0 的 DPA/CCA 攻击面 [p5-p6, p14]。
- 关键数据：
  - 面积（5 nm，ML-DSA-87 + ML-KEM-1024）：ABR 2.0 0.1096 mm²（标准单元 0.0860+SRAM 0.0236，约占 Caliptra v2.1 的 45%）→ ABR 3.0 0.0459 mm²（标准单元 0.0123，-80%；SRAM 0.0335），总面积 -58%（自报）[p9]
  - SRAM：59.7 KB → 86.7 KB（+27 KB，+45%）[p8]
  - 周期：ML-DSA-87 Sign 单轮 36,700→34,928（-4.8%）；ML-KEM-1024 Decaps 12,117→11,056（-8.8%）；KeyGen -0.6%（自报）[p10]
  - Keccak 掩码：面积约 4x、每轮 4 clk（慢 8x）；整体面积 109%，周期 +7.4–10.5% 视操作（看图）[p11]
  - TVLA：NTT/PWM/INTT/PWA 无泄漏（实验，FPGA 156 MS/s，10 MHz 时钟）[p15-p16]
  - 版本：ABR 3.0 2026 年 10 月，随 Caliptra 2.2 [p2, p17]
- 提到的公司/客户/产品/标准：Microsoft、Adams Bridge、Caliptra 2.2、ML-DSA、ML-KEM、CHIPS Alliance
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（面积对比）；p16（TVLA）

### P042 Baremetal Security Architecture
- 讲者/机构：Bharat Pillilli、Darpana Loodu，Microsoft | 类型：技术分享
- 方向归属：主 [安全]
- 核心主张：裸金属租户需要平台控制而 CSP 仍须管理硬件/固件，提出动态层级模型：System BMC（租户）+ CSP BMC（集成于 SmartNIC），恢复模式下 CSP BMC 接管 [p4-p6]。
- 关键数据：无数字；演示在 Microsoft 展位，基于 DC-SCM 1.x 并硬件分区，不改外形 [p7]
- 提到的公司/客户/产品/标准：Microsoft、DC-SCM 1.x、SmartNIC
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（层级模型）

### P043 Beyond Static Identity- Enabling Secure Certificate Refresh in Silicon Roots of Trust
- 讲者/机构：Emre Karabulut、Vishal Mhatre，Microsoft | 类型：技术分享
- 方向归属：主 [安全]
- 核心主张：Caliptra 2.x 的 Field Entropy 烧在 fuse，证书不能更新或支持翻新；提出以 SP 800-108 KDF 计数器模式复用 FE fuse，并把 LDevID 证书生成移出 ROM 到 FMC [p2, p6-p7]。
- 关键数据：4 个 64 位熵 fuse 共 256 位，需一次整体使用（冲突概率 2^128）[p2]；翻新要求清零 UDS/FE 并可重新配置 [p3]
- 提到的公司/客户/产品/标准：Microsoft、Caliptra、SP 800-108
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P044 Caliptra Subsystem 2.2- USB 2.0 and OCP Streaming Boot
- 讲者/机构：Caleb Whitehead（Microsoft）、Bart Vertenten（NXP）| 类型：技术分享
- 方向归属：主 [安全]；次 [运维/可靠性/遥测]
- 核心主张：Caliptra Subsystem 2.2 增加 USB 2.0 原生 OCP streaming boot，经嵌入式虚拟 hub 单链路暴露两个设备（Device 0 RoT，Device 1 集成方应用），I3C/AXI 仍支持 [p4, p7, p14]。
- 关键数据：无数字；Device 0 承载 OCP Streaming Boot/MCTP/PLDM/SPDM，Device 1 承载 OBMF/MCTP [p7]
- 提到的公司/客户/产品/标准：Microsoft、NXP、Caliptra Subsystem 2.2、Adams Bridge 3.0、OCP LOCK
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（虚拟 hub 两设备）

### P046 Endorsements for Attestation- A Common Language for the Whole Supply Chain
- 讲者/机构：Paul Howard（Arm）、Shefali Kamal（Fujitsu）| 类型：标准进展
- 方向归属：主 [安全]
- 核心主张：机密 AI 需要验证多源证据，供应链到验证器存在"集成税"；用 IETF RATS 的 CoSERV 统一背书与参考值分发，Veraison 已有端到端演示 [p5-p7, p10]。
- 关键数据：无数字；CoSERV 为 pre-RFC 草案 [p13]
- 提到的公司/客户/产品/标准：Arm、Fujitsu、IETF RATS (RFC9334)、CoSERV、CoRIM、Veraison、Linaro
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（CoSERV 查询-收集-缓存）

### P049 Integrated HSM- Bringing Silicon-Level Key Security to the Server Tray
- 讲者/机构：Craig Barner（Marvell）、Vishal Soni（Microsoft）、Mohan Kumar（Oracle）| 类型：标准进展
- 方向归属：主 [安全]
- 核心主张：集中式 HSM 在 AI/机密计算下形成网络往返、扩展与攻击面瓶颈，催生密钥绕行；TESSARA 是 OCP 开放 iHSM 标准，位于服务器托盘，FIPS 140-3 Level 3，今天在 OCP Global Summit 2026 首次公布 [p3-p4, p7]。
- 关键数据：互操作密钥迁移采用 attested HPKE 密封，抗量子（ML-KEM/ECDHE、ML-DSA/ECDSA 混合）[p9, p11]；iHSM 栈可在隔离 TEE 中运行（无需 ASIC）[p10]
- 提到的公司/客户/产品/标准：Marvell LiquidSecurity、Azure Integrated HSM、Oracle OCI KMS、Caliptra、OCP LOCK、DC-SCM、SPDM、TDISP、PKCS#11
- 首次/记录/SOTA 声明：自称 TESSARA 在本届首次发布（Marvell/Microsoft/Oracle 联合）[p7]
- 推荐配图页：p6（密钥从云 HSM 释放到 iHSM）

### P050 OCP Device Identity Provisioning over SPDM
- 讲者/机构：Fabrizio D'Amato（AMD）、Xiaoyu Ruan（Intel）；贡献者含 Broadcom、Google、Qualcomm、NVIDIA、Microsoft | 类型：标准进展
- 方向归属：主 [安全]
- 核心主张：器件身份被厂商 PKI 锁定，验证器需持有每个厂商根；方案让运营商以单一 Operator Root CA 通过 SPDM ≥1.3 的发现、证明、配置、选择四步给 LDevID 背书 [p2-p5, p12-p14]。
- 关键数据：规格约 80% 完成（带问号）[p18]；已请 DMTF 在 SPDM 1.5 支持 GET_ATTESTATION，并允许部分证书链（PQC 证书可达 8 KB）[p18]；OCP PEN 42623 [p7]
- 提到的公司/客户/产品/标准：AMD、Broadcom、Google、Qualcomm、NVIDIA、Microsoft、Intel、MediaTek；SPDM 1.3、DICE、EAT、Caliptra
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（四步流程）

### P051 OCP L.O.C.K. and FIPS
- 讲者/机构：Gwangbae Choi，Samsung Electronics | 类型：技术分享
- 方向归属：主 [安全]；次 [存储]
- 核心主张：OCP L.O.C.K.（与 Caliptra 配合保护存储设备静态数据）让 FIPS 140-3 模块边界成为系统级设计决策；边界选择在验证范围与 CSP 外泄之间权衡，DRBG/熵源是关键 [p2, p6-p10]。
- 关键数据：无数字；关注 FIPS 140-3 Security Level 2 及以上 [p2]
- 提到的公司/客户/产品/标准：Samsung、OCP L.O.C.K. v1.1、Caliptra、NIST SP 800-90
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（同一 SoC 的不同 FIPS 边界）

### P052 Out of Band Seamless Updates with Runtime Authorization
- 讲者/机构：Jayant Mangalampalli、Eli Kupermann、Anahit Tarkhanyan，Intel | 类型：技术分享
- 方向归属：主 [运维/可靠性/遥测]；次 [安全]
- 核心主张：用一个已签名服务包（载荷+清单+资格元数据）经 BMC 以 PLDM 流式 stage 各 socket，运营商授权后在平台范围 rendezvous 下激活微码，无需重启；未授权包等同损坏包 [p3-p6]。
- 关键数据：无具体数字；资格元数据含 Minimum Runtime Update Revision、Impact(0 无影响/1 有影响)、TCBR [p12]
- 提到的公司/客户/产品/标准：Intel Xeon、PLDM Type 5、OCP Impactless Firmware Update 规范
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（OOB 更新路径）

### P055 Upgrading OCP S.A.F.E. and S.O.L.I.D. for the AI age
- 讲者/机构：B Keen、Zahra Lak（Microsoft）、Jeff Andersen（Google）| 类型：标准进展
- 方向归属：主 [安全]
- 核心主张：S.O.L.I.D. 自 2026 年 10 月起强制，按新要求评审 2027-01-01 起强制；AI 辅助评审成为必要补充，但不能替代第三方独立评审 [p5, p7-p9]。
- 关键数据：时间点：S.O.L.I.D. 2026 年 10 月强制；新要求评审 2027-01-01 强制 [p5, p8]；当前须使用前沿云模型，正研究开放权重模型 [p7]
- 提到的公司/客户/产品/标准：Microsoft、Google、OCP S.A.F.E.、S.O.L.I.D.、SRP
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

## 五、Server：Composable Memory Systems

### P056 Addressing Memory Wall challenge for AI and General Compute platforms
- 讲者/机构：面板：Anjaneya Chagam、Samir Rajadnya（Microsoft）、Grant Mackey（Xcena）、Mohamad El-Batal（Seagate）、Manoj Wadekar（Meta，主持）| 类型：面板
- 方向归属：主 [In 封装内/内存池化 CXL]（仅提 CMS 定位）；次 [存储]
- 核心主张：CMS 为跨多种内存技术、互连与层级的动态统一内存管理；幻灯片仅有议题与号召页 [p3]。
- 关键数据：无。
- 提到的公司/客户/产品/标准：Microsoft、Xcena、Seagate、Meta、OCP Server/CMS
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

## 六、Sustainability

### P080 Climate Volatility in Daily Operations, A Community Conversation with Operators, Hyperscalers
- 讲者/机构：Maheshwari Neelam（OCP）、Miranda Gardiner（iMasons Climate Accord）、Emily Wasley（Meta）、Jessica Gullbrand（Intel）、Alexander Rakow（Schneider，主持）| 类型：面板
- 方向归属：主 [运维/可靠性/遥测]
- 核心主张：现有标准（ASHRAE TC 9.9、EN 50600、PUE/WUE、Uptime Tier 等）都没给出把环境暴露与运营后果联系起来的开放方法；提出六层框架（外部灾害→站点→灰空间→白空间→运营后果→编排）[p4-p5]。
- 关键数据：设想场景：连续 5 天 41°C 干球、24°C 湿球，机房无中断但冗余余量被"静默消耗"（假设示例）[p6]；OpRes 白皮书 v4.0 征求意见稿 [p9]
- 提到的公司/客户/产品/标准：Meta、Intel、Schneider、iMasons Climate Accord、ASHRAE TC 9.9、Uptime Tier、IFRS S2
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（六层框架）

### P083 Cooling the Cloud- Regional Tradeoffs in U.S. Data Center Cooling Architectures
- 讲者/机构：Sammy Houssainy、Karim Shalash，Daikin Applied Americas | 类型：技术分享
- 方向归属：主 [底座-冷却]；次 [推理/算力/经济性]
- 核心主张：蒸发冷却未必运营成本更低，区域水电价决定交叉点，用 WESI（水-能选择指数）判断；湿冷的碳收益随电网脱碳而下降 [p8-p10]。
- 关键数据：
  - 美国数据中心用电结构（LBNL 2025）：IT 59%、冷却 30%、变压/UPS 9%、其他 2% [p4]
  - 仿真：1 MW IT，18 个电网区域逐小时，干冷 vs 湿塔 [p7]
  - PJM East 与 ERCOT 等重要市场模型偏向干冷运营成本 [p10]
  - 湿塔每增加 1 百万加仑现场用水的碳收益到 2050 年下降 29–99%（如 FRCC -29%、NYISO -99%）（仿真，看图）[p9]
- 提到的公司/客户/产品/标准：Daikin Applied、LBNL、EIA、EPA eGRID、NREL Cambium、ASHRAE
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（碳收益逐区域降幅）

### P084 DCEM workstream update- Case studies of metric measurements from servers to data centers
- 讲者/机构：Babak Falsafi（Swiss Datacenter Efficiency Association）、Sadasivan Shankar（SLAC/Stanford）、Sammy Nachimuthu（Oracle）| 类型：标准进展
- 方向归属：主 [运维/可靠性/遥测]；次 [底座-冷却]
- 核心主张：PUE 不足以分解风扇、PSU 损耗等；提出 IUE（基础设施利用效率），并指出风扇功率计入 IT 会使 PUE 变"好" [p3-p5, p10]。
- 关键数据：
  - 15 个美国州有数据中心暂停令 [p2]
  - 32°C 下服务器功率（W）：风冷 H 约 590（含风扇 40）、DLC H 约 522（风扇 3）；DLC 比风冷省 9.0%(CL)–11.5%(H) 服务器功率；风扇占风冷 co-lo 服务器功率 10.2%（实验，看图）[p8]
  - 32°C 下 PUE：风冷 1.28，DLC 1.37（IT 387 W vs 355 W，CDU 20 W）（计算，看图）[p9]
  - 案例假设 PUE（24°C）：超大规模 1.1（利用率 60%）、co-location 1.3（利用率 15%）[p7]
  - 数据中心噪声：GPU 机柜中部 92–97.4 dB [p19 看图]
  - 产出：gPUE v0.1、HDCC v0.2 白皮书，IUE v0.1.0 草案；2027 完成 [p22]
- 提到的公司/客户/产品/标准：Oracle、SLAC、Stanford、HotInfra 2026 论文、80 PLUS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（风冷与 DLC 的 PUE 对比）

### P085 Enabling Scalable Waste Heat Recovery- Operational Realities, Design Principles, and Value
- 讲者/机构：Emily Matys、Eric Peterson，Microsoft | 类型：技术分享
- 方向归属：主 [底座-冷却]
- 核心主张：废热回收（WHR）需对齐供热、回收、输送、需求四环节，推荐在冷机前回收并以换热器划定边界 [p3, p8-p10]。
- 关键数据：1 MW IT 约产生 1 MW 废热（经验法则）[p4]；设备冷却液入口 17–45°C、出口 25–55°C，建议按 25–55°C 热源规划 [p6]；白皮书将于 2026 Global Summit 后提交评审 [p16]
- 提到的公司/客户/产品/标准：Microsoft、OCP Heat Reuse 子项目
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（换热器作为责任边界）

### P086 From Silicon to System- Embedding Power Efficiency as a Core Design Principle for Scalable AI
- 讲者/机构：Devang Soparkar（Microsoft）、Nilanjan Palit（Intel）| 类型：技术分享
- 方向归属：主 [底座-电力]；次 [推理/算力/经济性]
- 核心主张：功率节省从硅片到机架逐层复合，需统一的 OCP 共同功率规范与检查清单；两个季度内给出草案规范与 CPU 特性检查表 [p2, p7-p8]。
- 关键数据：潜在节能：硅 15–25%、服务器平台 10–20%、机架 5–15%（自报，估计）[p2]；示例平台功率预算：CPU 50%、内存 19%、存储 9%、加速器与 NIC 7%、VR 损耗 8%、板级 IC 7% [p3]
- 提到的公司/客户/产品/标准：Microsoft、Intel、OCP
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（三层节能潜力）

### P088 Next-Generation Sustainability Dashboards- AI-Powered Optimization for Data Centers
- 讲者/机构：Arun Mahendran、Manish Baing，Lenovo | 类型：技术分享
- 方向归属：主 [运维/可靠性/遥测]
- 核心主张：用时序功率预测（最终选 FBProphet 单变量）识别冷热时段、碳感知调度与碳封顶，并建议成立 OCP 可持续仪表盘工作组 [p10-p11, p15-p16]。
- 关键数据：电网碳强度示例 340 g/kWh [p6]；月度碳封顶示例每机架 20 kg CO2 [p15]；仪表盘示例显示 PUE 0.66（PUE<1 不可能，疑为示意图，存疑）（看图）[p7]
- 提到的公司/客户/产品/标准：Lenovo、Kepler、CodeCarbon、PowerTOP
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P090 Performance-Normalized Embodied Rack Carbon Intensity for Next-Generation Hardware
- 讲者/机构：Kali Frost，Microsoft | 类型：技术分享
- 方向归属：主 [推理/算力/经济性]（碳强度）；次 [底座-电力]
- 核心主张：在增长时代需与绝对排放并行的"按性能归一"的机架嵌入碳强度（kg/TB、kg/core、kg/FP8 TOPS），但不能替代全生命周期指标 [p2, p4, p7]。
- 关键数据：无具体数值；框架含 2020 参考情景、基线效率情景、实际排放 [p5]
- 提到的公司/客户/产品/标准：Microsoft
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（多层级碳强度框架）

### P091 Product Category Rule-style Specification for Life Cycle Assessment on Datacenter ICT-Equipment
- 讲者/机构：Stephan Benecke（Google）、Lisa Rivalin（Meta）、Ines Sousa（Microsoft）、Vinny Ferrero（AWS）、Chris Eckstein（Fraunhofer IZM）| 类型：面板
- 方向归属：主 [推理/算力/经济性]（碳核算）
- 核心主张：建立机柜级 cradle-to-gate PCF 的协调方法，含统一分类、数据质量评分、商品级建模要求 [p3]。
- 关键数据：2025 年 5 月启动；2027 Q1 公开征求意见（v0.3），2027 Q2 发布 v1.0 [p3, p5]
- 提到的公司/客户/产品/标准：Meta、Microsoft、AWS、Google、Fraunhofer IZM、SEMI Semiconductor Climate Consortium
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P093 Standardizing Data Center Operational Carbon Tracking- Supplier Metrics vs. Operator Needs
- 讲者/机构：Sheng Zhong，ABB | 类型：技术分享
- 方向归属：主 [底座-电力]；次 [运维/可靠性/遥测]
- 核心主张：供应商 EPD 使用阶段数据与数据中心实际不符；建议在 EPD 模块 B6 披露 10/25/50/75/100% 多点损耗并解耦 kWh 与排放因子，提议 OCP "Intelligent Lifecycle Management" 子项目 [p10, p15-p17]。
- 关键数据：
  - 20 年累计碳足迹：Scope 1 1%、Scope 2 61%、Scope 3 38%（引用 Lin 等）[p7]
  - 静态 PCR 假设与动态负载可产生约 400% 偏差（自报）[p13]
  - 变压器使用阶段 GWP：US 平均电力 256.7 kg vs NC 平均 200.7 vs 风光 REC 24.3、水电 REC 7.7 kg CO2-eq（看数）[p12]
  - UPS 双变换 94% vs Eco-Mode 99% 效率 [p20]；AI 服务器节点 200 W 空闲到 1200W+ [p14]
- 提到的公司/客户/产品/标准：ABB、Google、iMasons Climate Accord、EN 50693、ISO 14025
- 首次/记录/SOTA 声明：无
- 推荐配图页：p15（EPD 局限与运营者需求）

### P094 Sustainability and best practices for water efficiency
- 讲者/机构：Rishab Vardhan Harikrishnan（Oracle）、Derek Kauneckis（Vertiv）| 类型：技术分享
- 方向归属：主 [底座-冷却]
- 核心主张：用水核算应区分取水与耗水并归一边界；冷却选型应按区域水压力与被动冷却窗口，而非一刀切 [p3-p7]。
- 关键数据：用水平衡 Intake = Evaporation + Drift + Blowdown + Losses + Reuse（看图）[p4]；各冷却技术年用水（Microsoft 数据中心，百万升/年，估读）：绝热-直蒸发约 0–300，间接蒸发约 330–880，冷却塔约 960–1180（看图，看不清精确值）[p5]
- 提到的公司/客户/产品/标准：Oracle、Vertiv、Microsoft（数据来源）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（各冷却技术用水与 PUE/WUE）；p7（区域决策表）

### P096 Updates from an exciting year with the OCP Sustainability Project, DCF Sustainability Project
- 讲者/机构：Alexander Rakow（Schneider）、Shruti Sethi（Microsoft）、Priya Chhiba（Google）、Sung A Kim（Castrol）| 类型：标准进展
- 方向归属：主 [底座-冷却]/[运维]（综合）
- 核心主张：可持续性成为 OCP 第 5 条原则；OpRes 工作组界定基础设施"失效物理"；Clean Backup 规范 v0.3 已发布，v1.0 目标 2026 Q4 [p5-p6, p13, p18]。
- 关键数据：Clean Backup 测试计划：ICE 2026 年 4 月，燃料电池 PEMFC 2026 Q3–Q4，铝空气发电机 2026 Q4/2027 Q1 [p13]；LCA PCR 目标 2027 年中 [p8]；Embodied Carbon Base Spec 于 2025 年 8 月发布 [p7]；Clean Backup 白皮书与能源/水/碳论文 2027 [p18]
- 提到的公司/客户/产品/标准：Schneider、Microsoft、Google、Castrol、iMasons Climate Accord、Fraunhofer
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（四大支柱，看图）
