---
title: "R03_Server-OpenChipletEconomy"
tags:
  - OCP2026
  - 讲稿笔记
---

# R03 笔记：Server：Open Chiplet Economy

### P064 AI-native Virtual Chiplet Eco-systems with industry best practices to accelerate Chiplet adoption
- 讲者/机构：Raghu Shankar（主持，Entrepreneur）；Marc Meunier（Arm）、Lichen Weng（Tenstorrent）、Matt Holdrege（Microchip）、Nandan Nayampally（Baya Systems）[p4]；Arm 段另列 Ashwin Matta（Arm）、Srini Narayana（AMI）、Tran Nguyen（Synopsys）[p20] | 类型：面板（含各家附带材料）
- 方向归属（主/次）：主 [In 封装内：chiplet/UCIe/BoW、D2D]；次 [Out 后端网络：交换芯片]
- 核心主张：
  - 虚拟 chiplet 生态 = 虚拟原型（分布式仿真、加密/容器化模型、fast model、VIP）+ AI native（语义检索、自动互操作、设计空间探索、soft IP 生成），用于在多厂商环境中"shift left / up / out"降低前端设计摩擦 [p2][p3][p44]。
  - Tenstorrent：多厂商 chiplet 集成缺全栈互操作标准、合规测试、可复用 chiplet 和开源参考设计，因此推出 Open Chiplet Atlas（OCA）5 层架构 + 开源 Harness + 合规套件 [p30][p31][p32]（看图）。
  - Baya Systems：数据搬运是瓶颈，die 边缘（shoreline）被 SerDes/UCIe/HBM PHY 争抢；高 radix UALink/UEC/ESUN 交换机的 crossbar 不利于 chiplet 化，提出 NeuraScale 非阻塞 fabric 替代 crossbar [p37][p39]。
- 关键数据：
  - Arm Neoverse CSS：9 个月从启动到 tape-out；节省 80 工程师年（自报）[p24]；21 个 CSS 项目且在增加（自报）[p23]。
  - Baya NeuraScale：每 UCIe D2D 链路 320 GB/s @2.5 GHz；每 chiplet 256 个 1 Tb/s 端口，完全非阻塞；1 个 PHY 承载多协议 D2D（自报）[p39]。
  - Baya 下一代规模：封装内 32+ chiplet；每 die 16×16 mesh；2048-bit 链路；>10× 更大规模；每 chiplet 256 TB/s 聚合吞吐；scale-out 交换机数量 30:1 减少（自报/预测，未给条件）[p41]。
  - OCA：已发布 OCA System Arch Spec Draft v0.8、AXI over UCIe (AoU) Spec Draft v0.8；Harness Beta 于 Oct 2026 以 Apache 2.0 发布（看图）[p32][p33]。
  - OCA 路线图：v0.7、v0.8 已发布；v0.9 Sep'26/E；Harness Oct'26/E；v1.0 EOY/E（看图）[p35]。
  - OCA 虚拟平台三阶段：Phase1/2 Oct'26，Phase3（2+ Harness 实例互联）EOY/E（看图）[p34]。
- 提到的公司/客户/产品/标准：Arm（Neoverse CSS、Arm Chiplet System Architecture CSA、Arm Total Design、Virtual Silicon）、Tenstorrent（OCA、OCCP、SEP/SMC）、Baya Systems（WeaverPro、WeaveIP、NeuraScale）、Microchip、AMI、Synopsys；UCIe、BoW、I3C、AXI、CHI、CHI-C2C、UALink、UEC、ESUN、FCSA、SystemC、Zephyr。
- 首次/记录/SOTA 声明：无明确"首次"；Baya 称 NeuraScale "Scales to 1000s of ports" [p39]。
- 推荐配图页：p32（OCA 5 层互操作架构图，看图）；p39（Baya：shoreline 受限与 NeuraScale 320 GB/s / 256×1Tb/s 端口）；p41（32+ chiplet、256 TB/s、30:1 交换机减少）。

### P065 Advancing Chiplet Flexibility- Updates in 2.0 OCE Transaction and Link Layer Specification
- 讲者/机构：Brian Murray，SoC Architect，VeriSilicon [p1] | 类型：标准进展
- 方向归属（主/次）：主 [In 封装内：chiplet/UCIe/BoW、D2D]
- 核心主张：
  - OCE TLL（Transaction and Link Layer）把任意 SoC 总线协议（如 AMBA）映射为 chiplet 接口，链路建立后 chiplet SiP 行为等同单片 SoC [p2][p3]。
  - 2.0 版重审全部设计决策、压低开销，仅 Link Layer 保留与 1.x 的兼容模式；新增 PHY binding，支持 UCIe 与 BoW.FLEXI [p5]。
- 关键数据：
  - TLP 头：1.x 为 12b（6b Type、1 保留、5 AUX）；2.x 为 4b Type + 2b Type Extension（标准）[p6]。
  - MSG 消息负载最多 16 字节、字节粒度；CRD 每 TLP 两个 credit 返回，多 credit 字段 5 个、4b Bank ID 索引；credit 字段改 3b 编码，默认 Int/2^(n-3)（标准）[p7]。
  - LLP 默认 24 granule（1 头 + 23 负载），可选 16 granule（1+15）用于部分 1.x 兼容与低延迟系统；LLP 变大降低 LlpHdr 开销（标准）[p8]。
  - BoW.FLEXI 映射：低位宽接口下 TLP:LLP 通常 1:1；UCIe RAW Streaming 采用 Ventana 的 "Universal TLL" 提案映射到 UCIe FDI（标准）[p9]。
- 提到的公司/客户/产品/标准：VeriSilicon、Ventana；BoW、BoW.FLEXI、UCIe（FDI）、AMBA；OCP Chiplet Marketplace。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（2.0 TLL 变更总览）；p8（LLP 24/16 granule 格式变化）。

### P066 Agile Silicon-Will Open Chiplet Architectures Keep Pace with Fast-Evolving AI Dataflows
- 讲者/机构：Patricia Gonzalez-Guerrero，Lawrence Berkeley National Laboratory，代表 chiplets modularity for AI/HPC workstream [p1] | 类型：技术分享
- 方向归属（主/次）：主 [In 封装内：chiplet/UCIe/BoW、D2D]；次 [推理/算力/经济性]
- 核心主张：
  - 性能提升放缓、能耗成为危机，专用化可带来 100–1000× 性能和 100–1000× 能耗改善，但算法演进快于硬件；chiplet 模块化是让专用硬件进入 HPC 集群的途径 [p5][p9][p10]。
  - 四步法：算法 profiling → 宏架构（chiplet + interposer）→ chiplet 参数 → 微/宏架构；以 systolic array / scratchpad / accumulator chiplet 在 2D 网格 Network-in-Package 上组合 [p11][p17][p18]。
  - 标准接口（UCIe、BoW，bump pitch >40µm）高频串行化带来更多功耗与延迟；封装技术演进很快（Intel 25µm、TSMC 10µm），"两年前讨论的已不再成立"[p20][p27][p28]。
- 关键数据：
  - 用例：4130 节点运行 45 天，产生/摄入 1 PB 数据，55K 节点小时（引用）[p2]。
  - 专用化潜力：100–1000× 性能、100–1000× 能耗下降（引用/自报，无条件）[p9]。
  - NiP：最小传输延迟 1 个时钟周期，无缓存一致性，消息传递 [p18]。
  - Chiplet 4mm×4mm：sub-20nm@1GHz 用 64×64 PE、1MB scratchpad、64 acc；sub-5nm@2GHz 用 128×128 PE、9MB、128 acc [p19]。
  - 三种 SiP（CNN / DeepSpeech / Transformer）：sub-20nm 每 chiplet 1 TB/s、8192 数据 lane，interposer 38×38 至 64×64 mm；sub-10/5nm 每 chiplet 2/4 TB/s、16384 lane，interposer 30×28 mm（仿真/设计）[p21]。
  - 评估：相对 baseline，归一化延迟 Transformer 从 ~0.12 降到 sub5nm ~0.0003，DeepSpeech2 从 1.0 到 ~0.009；能耗 sub20/sub10 降至 ~0.01–0.05，但 sub5nm 方案能耗接近 baseline（DeepSpeech2 ~1.0）（仿真，看图）[p26]。
  - 引用 WSJ（2026-02-12）：大厂表外 AI 承诺 Leases not started \$904B、Purchase commitments \$1.52T（引用 WSJ，看图）[p29]。
- 提到的公司/客户/产品/标准：LBNL、AMD、Intel、Google TPU、Anton、Lehigh University、University of Central Florida、OXMIQ、TSMC；UCIe、BoW；DOE Genesis Mission [p30]。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p21（三种 SiP 参数表）；p26（延迟/能耗对比柱状图，看图）；p28（bump pitch 演进：40µm → 25µm/10µm）。

### P067 An Open Lightweight Serial Interconnect for Composable AI Architectures
- 讲者/机构：Vishal Shah（VP of Product，Credo）、Allan Cantle（CEO，Nallasway）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [In 封装内：chiplet/D2D、内存]；次 [Up 机柜/超节点：CPO/NPO]
- 核心主张：
  - 112G VSR SerDes 处在封装内 D2D（<25mm）与长距 SerDes（>1m）之间的"出基板到板"区间，在 beachfront 密度、能效和延迟上适配度最好 [p3]。
  - Credo OmniConnect：通用 AXI-over-VSR 总线，统一内存（Weaver）、C2C、scale-up/scale-out 网络和 CPO/NPO 接口，晚绑定 IO 比例 [p2]。
  - OCE LSI（Lightweight Serial Interconnect）= 轻量 AXI Framer + 任意 IEEE 合规 SerDes，复用 PCIe 6 FLIT 机制，无软件栈 [p4][p5]。
- 关键数据：
  - 112G VSR：~10 in、23 dB 通道；<1 pJ/bit；1.8 Tb/s/mm beachfront（自报）[p3]。
  - 对比区间：D2D <25 mm；长距（224G LR、PCIe/CXL）>1 m、30+ dB [p3]。
  - FLIT 固定 256 B：DATA 238 B、头 4 B、CRC 8 B、FEC 6 B，负载效率 93%（仅 18 B 开销）（spec）[p10]。
  - FEC：3 路交织码字，单 lane ≤17 bit 突发必纠（视对齐最多 24 bit）；CRC 8 字节覆盖 242 B，检出至多 8 个坏符号（spec）[p7][p11]。
  - AXI Extender：512-bit AXI，5 通道独立分包；每包可合并最多 16 beat（spec）[p7][p8]。
  - Phase 1 spec 目标约 Nov 2026 发布 [p13]。
- 提到的公司/客户/产品/标准：Credo（OmniConnect、Weaver）、Nallasway；PCIe 6、CXL 3、UCIe、BoW、AXI、LPDDR、Arm FCSA。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（112G VSR 定位：D2D vs VSR vs LR 对比）；p10（256B FLIT 结构与 93% 效率）。

### P068 Building Interoperable AI Systems with Chiplets- Arm Neoverse and Cadence in an Open Ecosystem
- 讲者/机构：Saif Elsaady（Arm）、Michael Posner（Cadence Design Systems）[p1] | 类型：厂商技术分享
- 方向归属（主/次）：主 [In 封装内：chiplet/UCIe、CXL]；次 [Up 机柜/超节点：UALink]
- 核心主张：
  - Arm Neoverse CSS 提供预集成的 CPU/一致性互连/系统 IP，伙伴添加 I/O 与加速器，减少集成工作 [p4]。
  - 通过 Cadence 虚拟平台（Helium）、仿真（Xcelium）、仿真加速（Palladium）在硅前完成软件与系统验证（shift left）[p6]。
  - Cadence Chiplet Framework 按 OCP FCSA 实现 chiplet 管理（安全、控制、调试、NoC、UCIe）[p8]。
- 关键数据：
  - Neoverse CSS N4：CMN-Delphi 互连、DDR5/LPDDR6、PCIe Gen7/6 与 CXL 3.x、3 个 UCIe D2D、RSEv100 + Caliptra 接口（自报）[p5]。
  - Cadence I/O chiplet 示例：每个 224G SerDes x8 lane，合计 x32 lane；支持 UCIe-S 或 UCIe-A；4 个直连低延迟 slice；可配置为 UALink / Ethernet / Combo（自报）[p9]。
- 提到的公司/客户/产品/标准：Arm（Neoverse CSS N4、Arm Total Design）、Cadence（Helium、Xcelium、Palladium、Chiplet Framework）；OCP FCSA、UCIe、PCIe Gen7、CXL 3.x、UALink、Ethernet、Caliptra。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（Neoverse CSS N4 框图）；p9（224G SerDes x32 I/O chiplet，UALink/Ethernet 可配）。

### P069 Bunch of Wires Flexi 1.0 - a low cost, low power D2D interface
- 讲者/机构：Morgan Whately（Distinguished Engineer，Infineon）、Kash Johal（Founder，YorChip）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [In 封装内：chiplet/BoW、D2D]
- 核心主张：
  - BoW.Flexi 面向简单、能效和成本优先于绝对带宽的场景（MCU、模拟 chiplet 等），SDR 时钟、无串行化、无需 sideband 与链路训练 [p3][p4]。
  - BoW.Flexi 1.0 已发布，计划提供参考 RTL 提升互操作性 [p4][p9]。
- 关键数据：
  - 最少 6 pin 接口；8 条命令；电气基于 BoW sideband，0.65–0.95 V（spec）[p3]。
  - 对比 BoW 2.0：lane 数 1–128（BoW 2.0 为 8/16）；速率 0–4 Gb/s/pin（BoW 2.0 为 2/4/8/16/32）；支持 Active/Standby/Deep-Sleep；封装支持 wire bond、flip chip、hybrid（spec）[p4]。
  - 包格式：3-bit CMD；ADDR 1–64 b；DATA 最多 1024 b；Virtual Wire 1–32 bit（spec）[p6][p8]。
- 提到的公司/客户/产品/标准：Infineon、YorChip、Microchip、Everspin、VeriSilicon、Eliyan；BoW 2.0、AMBA AHB/APB、AXI。
- 首次/记录/SOTA 声明：BoW.Flexi Version 1.0 发布 [p9]
- 推荐配图页：p4（BoW.Flexi vs BoW 2.0 规格对比表）；p5（BoW.Flexi 链路结构）。

### P070 Custom HBM as a System- Co-designing the Base Die, Die-to-Die Power, and Package Thermals for AI
- 讲者/机构：Mark Hsin-wei Tseng，Director，Marvell Technology [p1] | 类型：技术分享
- 方向归属（主/次）：主 [In 封装内：HBM、D2D]；次 [底座-冷却]
- 核心主张：
  - HBM 占 die 面积约 30%、XPU 成本 >50%，内存 I/O 而非核心越来越限制加速器扩展；把 HBM PHY 和控制器移入定制 base die 可回收面积给计算 [p3][p4]。
  - 对 HBM 而言能效（pJ/bit）而非带宽密度决定预算；UCIe 并非为下一代 HBM 带宽密度设计，需要一套从 2.5D 到 3D 混合键合通用的低功耗 D2D [p4][p10][p14]。
  - 热是硬约束：HBM 堆栈占 2.5D 封装热阻 57%，HBM5 热流密度 >2.0 W/mm²，需要在 D2D PHY 处预留硅散热路径并与封装协同设计 [p6][p7][p9]。
- 关键数据：
  - HBM ~30% die 面积、>50% XPU 成本；按当前内存价格内存 BOM 在许多 GPGPU/ASIC 中 >60–80%（引用 Marvell Analyst Day 2024 / Silicon Analysts 2026）[p3]。
  - HBM4 接口 2048 bit（32×64-bit 通道）（引用 JEDEC JESD270-4）[p3]。
  - 定制 base die：回收最多 25% die 面积，最多 30% 更多计算（自报）[p4]。
  - 单栈带宽：HBM2E 0.5 TB/s(2020) → HBM3 0.8 → HBM3E 1.0 → HBM4 2.0（8 Gbps）/3.3（13 Gbps）→ HBM4E 3.6（14 Gbps）/4.1（16 Gbps）→ next-gen 5.3（HBM4E +30%）/7.2 TB/s（28 Gbps），最多 8.9×；约每 2 年 1.7×（预测，引用 JEDEC/SK hynix/Hot Chips 2026）[p5]。
  - 芯片 TDP：2021 400 W（0.48 W/mm²）→ 2026E 2,000 W（~1,600 mm²，1.25 W/mm²）；ASIC 曲线 2027E 达 3,000 W；HBM5 >28 Gbps 时 >2.0 W/mm²，超过 JEDEC ~1.7 W/mm² 参考（预测/引用）[p6]。
  - 2.5D 封装热阻贡献：HBM 内部 57% vs ASIC 13%；8→16-high HBM 到 2028 越过热预算（引用 ECTC 2026）[p7]。
  - 混合键合：die 间热阻降 23–47%，垂直导热最高 3×，堆栈高度缩短 >15%（去除 ~30 µm µ-bump 间隙；取决于 Cu pad 覆盖 ≥20%）（引用 Electronics 2025 / Onto Innovation）[p8]。
  - HBM5 约 100 W/栈；SK hynix iHBM 在 D2D PHY 处的硅 ICE 热阻降 ~30%（引用 SK hynix 2026-05）[p9]。
  - Marvell SBD（同时双向）D2D：64 Gbps/wire；常规负载功耗降 75%（峰值流量降 42%）；PHY 面积 15%；>7 TB/s；HBM5 需 ~6.4 Tbps/mm（7.2 TB/s over 9 mm beachfront）（自报，Marvell 2025-08 新闻稿）[p10][p11]。
- 提到的公司/客户/产品/标准：Marvell（cHBM、SBD D2D IP 2nm）、SK hynix（iHBM、HBM5 HPB）、Samsung、NVIDIA（NVLink Fusion、NVHBM）；JEDEC JESD270-4、UCIe；Hot Chips 2026、ECTC 2026。
- 首次/记录/SOTA 声明：引用 Marvell 新闻稿称"Industry's First 64 Gbps/wire Bi-Directional Die-to-Die Interface IP in 2nm"[p10]
- 推荐配图页：p5（HBM 单栈带宽 2020–2028 路线图）；p7（2.5D 热阻分解 HBM 57%）；p10（SBD D2D 功耗 100%/58%/25%）。

### P071 Die-to-Die Solutions for Optical Chiplets
- 讲者/机构：Kevin Donnelly，Vice President，Eliyan Corporation [p1] | 类型：技术分享
- 方向归属（主/次）：主 [In 封装内：D2D、光 I/O]；次 [Up 机柜/超节点：CPO/NPO/XPO]
- 核心主张：
  - 下一代 1k–10k GPU 的 AI pod 需要 >400G/lane 和 >10m 距离，铜缆无法满足，需要可靠性/成本/功耗接近铜的光互连 [p4]。
  - 光模块内部 PIC–EIC、EIC–ASIC 广泛使用 D2D；UCIe 适合 EIC 含 FEC 终结/retimer 或单光纤场景，BoW 更适合高 radix、多光纤直驱 EIC，因其可非对称、可变 lane 数、可分别时钟 PPM [p8][p13][p17]。
  - OCP-OCE 正在组建新的光互连工作组 [p18]。
- 关键数据：
  - 过去 20 年：CPU/GPU FLOPS 增长 1,000,000×，DRAM 带宽与互连带宽各 100×（未注来源，看图）[p3]。
  - 铜/光边界：200G 时 ~1m/~2m 可用无源铜、~4m 有源铜；400G 时 ~2m 有源铜、~4m 起光；800G+ 时 ~1m 起即为光；10–100m 全部为光；72–288 GPU pod GPU-交换机 1–2m，1k–10k GPU pod 为 10–100m [p4]。
  - 1.6T SiPho 方案：C2C 8×212.5G SerDes；D2D UCIe-AP x64，64×25.6 Gbps = 1.6 Tb/s（含以太 FEC 开销），单时钟 PPM [p9]。
  - Slow-and-Wide：VCSEL 每光纤 ~25–50 Gbps；microLED 每光纤 ~2–8 Gbps；激光 SiPho 每光纤 200G–1.6T [p10]。
  - 1.6T Slow-and-Wide 方案：8 组光纤各 200G；D2D 为 8 个 BoW-SP x4，每个 4×53.1 Gbps = 200G，8 个独立时钟 PPM [p14]。
  - BoW PHY 已有 65nm 至 3nm 共 9 个节点的实现；标准 BoW PHY 每方向 16 lane，常见 32 lane/clock，最少实现过 4 lane/clock [p12][p13]。
- 提到的公司/客户/产品/标准：Eliyan、TSMC（COUPE、CoWoS）、Cisco（SiPho 白皮书）；UCIe、BoW（BoW Memory、BoW FlexI、BoW Optical）、UCIe-3D、SROI（Short Reach Optical Interfaces）、LPO、OSFP、XPO、NPO、CPO。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（铜→光过渡：速率×距离表与 pod 拓扑）；p14（BoW-SP x4 ×8 实现 1.6T 高 radix 光模块）；p17（CPO 中 UCIe/BoW/3D D2D 选择）。

### P072 Federated Chiplet Design and Simulation
- 讲者/机构：David Ratchkov、Kevin Cameron（机构未见）[p1] | 类型：标准提案
- 方向归属（主/次）：主 [In 封装内：chiplet]；次 [安全]
- 核心主张：
  - 多厂商 chiplet 协同设计需要 SI、PI、热、机械等系统级仿真，但模型含专有信息；原则是"模型所有权与执行分离"：把仿真请求送到模型处，形成 chiplet 的 Model-as-a-Service [p4][p5]。
  - 在 CDXML 上增加 Simulation Capability Manifest，由联邦编排器跨厂商做多物理场协同仿真，仅交换约定的边界值 [p6][p8][p9]。
  - IP 保护要写进标准（认证、查询限额、防模型提取等）；对接 Accellera FSS 而不自建通用分布式仿真协议；AI 应位于可信仿真之上做设计空间探索 [p10][p12][p14]。
- 关键数据：
  - AI 探索示例约束：五 chiplet 架构，内存带宽 ≥800 GB/s，封装功耗 <600 W，结温 <90°C，最小化封装成本（示例）[p14]。
  - POC Phase 1：2 个独立建模 chiplet、1 个封装、2 个仿真服务器、1 个编排器，仅功耗+热 [p15]。
  - 5 个交付物 + 第 6 个合规测试套件 [p16]。
- 提到的公司/客户/产品/标准：OCP CDX、CDXML、OCP Chiplet Marketplace、Accellera FSS、FMI、SystemC-TLM、SV/DPI。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（联邦仿真架构图）；p9（多物理场协同仿真迭代 8 步）。

### P073 Introduction to a new OCP FCSA Sub-Project Workstream
- 讲者/机构：Junie Um（Cadence）、Kurt Herremans（imec）、Ritu-Ranjan Shrivastwa（Secure-IC，a Cadence Company）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [In 封装内：chiplet]；次 [安全]
- 核心主张：
  - Physical AI（车、移动/工业机器人、无人机、自主机械）有 6 条约束：确定性时序、传感器接入、可靠性与安全、安全与信任、功耗与热、多 chiplet 可扩展 [p5][p6]。
  - chiplet 化引入时延/抖动不确定、信任边界分布、跨 chiplet 故障传播等问题，均跨 chiplet 边界，需要在 FCSA 上增加 Physical AI profile [p3][p4]。
  - 功能安全是封装级属性；D2D 互连既是故障传播路径也是诊断观测点 [p8][p9]。
- 关键数据：
  - 6 条约束（C1–C6）映射到 10 个架构需求域（R1–R10，如 R3 Real-Time Interconnect、R7 Functional Safety）[p7]。
  - 范围不含 D2D 物理与链路层（由 UCIe/BoW 负责）[p10]。
  - 目标 spec v1.0.0 于 Q3 2027 [p11]。
- 提到的公司/客户/产品/标准：Cadence、imec、Secure-IC；OCP FCSA、UCIe、BoW。
- 首次/记录/SOTA 声明：新 FCSA 子项目（PAI WG）成立 [p1][p10]
- 推荐配图页：p7（6 约束 → 10 需求映射）；p9（Physical AI 中 D2D 作为故障路径的示意）。

### P074 Physical AI- Addressing the barriers to interoperable chiplets in automotive and robotics
- 讲者/机构：Mukund Chavan（Rivian）、David Glasco（Cadence）、CP Hung（ASE）、Mark Knight（Arm）、Bart Plackle（imec）[p1][p2] | 类型：面板
- 方向归属（主/次）：主 [In 封装内：chiplet]
- 核心主张：材料仅含标题与嘉宾页，无论点内容 [p1–p3]。
- 关键数据：无
- 提到的公司/客户/产品/标准：Rivian、Cadence、ASE、Arm、imec。
- 首次/记录/SOTA 声明：无
- 推荐配图页：无

### P075 Scaling up AI Compute, Memory and Connectivity
- 讲者/机构：Igor Elkanovich，CTO，GUC [p1] | 类型：厂商技术分享
- 方向归属（主/次）：主 [In 封装内：D2D、HBM]；次 [Up 机柜/超节点：CPO]；次 [底座-电力]
- 核心主张：
  - UCIe 架构复杂，带来额外功耗与延迟，多数场景无需标准合规；GUC 用自有 GLink-LL（2.5D）与 GLink-3D 追求极低功耗与延迟 [p4][p5]。
  - 内存：HBM5 带宽相对 HBM4E 翻倍；混合键合 DRAM-on-Compute 在带宽、延迟、功耗上优于 HBM [p7][p8]。
  - TSMC COUPE CPO 同时支持 scale-out（200G PAM4/光纤）与 scale-up（OCI-gen2 4λ×100G NRZ DWDM 单根双向光纤）；数 kW ASIC 必须垂直供电；System on Wafer 是"game changer"[p10][p12][p14]。
- 关键数据：
  - 2.5D D2D 对比：UCIe-S 64 Gbps、110 µm、0.37 TBps/mm、1.25 pJ/bit；UCIe-A 64 Gbps、45 µm、2.6 TBps/mm、1.4 TBps/mm²、0.75 pJ/bit，延迟 10 ns+retry；GLink-LL 4–8 Gbps、CoWoS 35 µm / SoIC-X 6 µm、0.05–0.10 pJ/bit、BER<1E-30 无需 CRC/重传、延迟 1–3 ns（自报）[p4]。
  - GLink-3D：1.0（N6/N5）0.2 pJ/bit、9 Tbps/mm²；2.0（N2P）0.03 pJ/bit、50 Tbps/mm²、0.125–0.5 ns；2.1（N3P/N5）40 Tbps/mm²；3.0（N2P，执行中）80 Tbps/mm²；1.0–2.1 已硅验证，已用于客户 AI ASIC（自报）[p5]。
  - 3D 功率密度 5–10 W/mm²，平均 TDP 7.5 W/mm²；N2P TSV 开销较 N3P 降 ~40%（自报）[p3][p6]。
  - HBM4E vs HBM5：16 vs 24–32 Gbps；PHY 14 vs 8 mm²；PHY 面积效率 0.3 vs 0.75–1.0 TB/mm²；2026 vs 2029 量产；HBM4E@16G ~60 W，HBM5@32G ~90 W（自报/引用 SK hynix 2026-05）[p7]。
  - DRAM-on-Compute（4 层整 reticle）vs 6×HBM4E@16G：总带宽 32 vs 24 TBps；密度 110 MB/mm²（4 层）vs 310 MB/mm²（12 层）；延迟 30 vs 200 ns；0.5 vs 2.5 pJ/bit；最高温 125 vs 95°C；HB 间距 5–8 µm vs TCB ~20 µm，接口密 10–15×（自报）[p8]。
  - 内存控制器：顺序访问带宽利用率 ~100%，随机 70–80%；AXI 读延迟 <30 ns [p9]。
  - IVR（TSMC 16nm 演示）：1.8 V 输入、0.5–1.0 V 输出、效率高电流 85%/低电流 75%、3 W/mm²、响应快于板载 VRM 10–100×（实验/自报）[p12]。
  - System on Wafer：>40× reticle（>33,000 mm²）、最多 64 HBM4E；UCIe 替代 SerDes 功耗低 10×、延迟低 20×；TDP 20 kW、峰值 30 kW；224 Gbps RDL 走线；硅面积和 HBM 数为最大 CoWoS 的 5×（自报）[p13][p14]。
  - COUPE 测试：光引擎 4 个测试插入点 [p11]。
- 提到的公司/客户/产品/标准：GUC（GLink-LL、GLink-3D、HBM4E PHY/Controller、IVR）、TSMC（CoWoS、CoWoS-L、SoIC-X、COUPE）、SK hynix；UCIe、HBM4E/HBM5、OCI、IEEE DR。
- 首次/记录/SOTA 声明：无明确声明；称 GLink-3D 已硅验证 [p5]
- 推荐配图页：p4（UCIe-S/A vs GLink-LL 对比表）；p8（DRAM-on-Compute vs HBM4E 对比）；p10（COUPE scale-up OCI 4λ NRZ DWDM）；p13（System on Wafer）。

### P076 Securing the Open Chiplet Ecosystem- Defining a Common Security Architecture for FCSA
- 讲者/机构：Dominic Brown（Arm）、Sylvain Guilley（Secure-IC）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [安全]；次 [In 封装内：chiplet]
- 核心主张：
  - FCSA v1.1 新增安全章节，目标是 chiplet 系统达到与等效单片 SoC 相同的安全水平 [p4][p10]。
  - 采用 ISO/SAE 21434:2021 TARA 方法，并对接 SiP Protection Profile 的安全目标（看图）[p12][p13]。
- 关键数据：
  - FCSA v1.1：贡献截止 2026-03-27，范围完成 2026-06-26，RC 2026-08-28，正式发布 2026-10-12 [p15]。
  - 额外威胁：DoS、TOCTOU、Over-building（看图）[p12]。
  - v1.2 候选主题：安全、功能安全、管理处理器通信、时间同步、RAS、AMBA C2C 对齐 [p17]。
- 提到的公司/客户/产品/标准：Arm、Secure-IC；FCSA v1.1、AMBA C2C/AXI/CHI、UCIe、BoW、PCIe、CXL、UALink、ISO/SAE 21434、UN ECE R.155、Common Criteria SFR/SAR。
- 首次/记录/SOTA 声明：FCSA v1.1 发布 [p4]
- 推荐配图页：p13（FCSA 要素 ↔ PP 安全目标对照表，看图）；p18（AMBA C2C 分层）。

### P077 Security of Multi-chip ICs & Security Chiplets with Caliptra- Building a Hardware Root of Trust
- 讲者/机构：Matt Holdrege，Fellow，Microchip Technology [p1] | 类型：技术分享
- 方向归属（主/次）：主 [安全]；次 [In 封装内：chiplet]
- 核心主张：
  - 用 Caliptra（UDS、measured boot）+ DICE 建立跨 chiplet 的硬件信任根，使每个 chiplet 可证明身份与当前固件状态 [p3][p7]。
  - UCIe/BoW 提供连接但不替代系统级安全架构；中介层探测是可信物理威胁；安全需作为端到端封装属性验证 [p6][p12]。
- 关键数据：
  - 三种 chiplet 拓扑：Hub & Spoke、Shared bus、Daisy-chain（看图）[p10]。
  - UCIe 3.0 增加 D2D 安全与管理特性（自报）[p12]。
  - OCP Academy 9 门免费 chiplet 课程 [p13]。
- 提到的公司/客户/产品/标准：Microchip、Caliptra、DICE、UCIe 3.0、BoW、BoW.flexi、FCSA v1.1 第 9 章。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（三种 chiplet 安全域拓扑，看图）。

### P078 System level standards for Multi vendor chiplet interoperability
- 讲者/机构：Itai Nadler（CEO，GSOC）、Rob Pelt（Fellow，AMD）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [In 封装内：chiplet/UCIe/BoW]；次 [运维/可靠性/遥测]
- 核心主张：
  - BoW 和 UCIe 解决了物理与协议层互操作，真正的多厂商互操作还需固件 API 与消息传输层对齐 [p3]。
  - OCP Chiplet Systems 栈：Firmware API/Protocol 用 Arm SCMI（+扩展），消息传输用 DMTF MCTP，物理层由 FCSA 定义（I3C、BoW、UCIe 管理通道）[p5][p7]。
- 关键数据：
  - SCMI over I3C v0.93 在最终评审（v0.92 公开草案）；SCMI over BoW 初稿；SCMI over UCIe 未启动（p9 文字层中标题与说明文字错位，BoW/UCIe 状态对应存疑）；UCIe 与 BoW 映射目标 2027 年初（标准进度）[p9][p10]。
- 提到的公司/客户/产品/标准：GSOC（Ocean SoC、UCIe 3.0 Controller）、AMD；SCMI、MCTP、I3C、UCIe（MTP、UMAP）、BoW、FCSA。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（OCP Chiplet 固件栈分层）；p9（三个 spec 进度）。
