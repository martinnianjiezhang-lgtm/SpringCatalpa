---
title: "B24 · DAY2 · Mo12-A-开幕与大会报告"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo12-A3-Ciena-AI集群通信.pdf（共33页，单讲）
- 讲者/机构：Peter Winzer / Ciena（p1 题目页看图核实） | 题目：AI Cluster Scaling – It's All About Interconnect（末页标题 "Top Three Take-Aways"，主线为 Scaling AI is all about scaling I/O）| 类型：邀请报告（大会报告）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 3（Scale-out 224G/448G）、2（Scale-across/多rail）
- 核心主张：
  1. 扩展 AI 就是扩展 I/O：die-to-die 带宽 100%、内存带宽 10%、scale-up 带宽 1%、scale-out/scale-across 带宽 0.1%（按幻灯片相对比例）[p33]
  2. Scale-up 的本质是把"一个 radix 的硬件"塞进 I/O 可达范围：更密的机架（液冷、共封装 I/O 提升前面板密度）、免 retimer 的低功耗低时延延伸、高 radix 交换机与两级交换域 [p33]
  3. 混合介质（copper + optics）保持架构灵活：高速 SerDes 至少需要到 400G 世代，最终走向 chiplet 集成的纯光接口 [p33]
- 关键数据：
  - 封装内 next-neighbor：ASIC 内部 <1 mm、2 Gbps、20k lanes/mm、40 Tbps/mm；Die-to-Die 2 mm、64 Gbps、330 lanes/mm、21 Tbps/mm；HBM4(36 GB) 10 mm、10 Gbps、190 lanes/mm、2 Tbps/mm [p7]
  - 芯片面积竞争：功率输送 1–10 A/mm²，互连 0.5–5 Tbps/mm²，散热 ~3 W/mm²；Switch 芯片底面 95% 用于供电、5% 用于互连；全 reticle 面积 700–800 mm² [p8]
  - 前面板密度（1OU，200G/lane）：OSFP 可插拔 70 Tbps；XPO 配 fly-over copper 200 Tbps；铜连接器 230 Tbps（x2 双向）；mini 光连接器 624 Tbps（xN，bidi+WDM）[p15]
  - 200G PAM4 链路（左表）：无源铜 DAC 1.5 m、0 pJ/bit；带 retimer 铜 AEC 4.5 m、11 pJ/bit；retimed 光 100s m、16 pJ/bit。免 retimer（右表）：DAC 1.5 m 0 pJ/bit；有源铜 ACC 3.5 m、1.5 pJ/bit；线性光（LPO、CPX）100s m、6 pJ/bit [p17]
  - 混合铜扩展 scale-up 域：72 XPU@14 Tbps → 256 XPU@25 Tbps；线缆长度分布 0–3 m，无源铜占 23%、有源铜占 77%；平均约 +1 pJ/bit scale-up 功耗增量 [p18]
  - Ciena Nitro（N200680）免 retimer 有源铜：70 dB @ 53 GHz 信道损耗（Nyquist）下，200G PAM4 实测 pre-FEC BER 约 1e-7 量级（图中该点，插图示 errors per block <1%/<0.001%）；随信道损耗 45→75 dB，BER 从 ~1e-9 升至 ~5e-6（读图估计）[p19]
  - 交换容量趋势 40%/年，per-lane switch I/O 20%/年（图中标 200G→(400G) 至 2030）；448G 电/光眼图对比；提出 Co-Packaged Copper I/O (CPC)（图源 Samtec）[p21]
  - Open CPX 模块（Ciena Vesta 200，6.4T CPX 挂 100T 交换 ASIC）：模块尺寸 30 mm × 16 mm；示波器读数 平均光功率 3.01 dBm、Outer ER 4.079 dB、TDECQ 2.23 dB [p24]
  - Open CPX：51.2 Tbps XPU scale-up&out；204.8 Tbps 交换机；"N x 200 Tbps 1OU XPU 与交换托盘" [p25]
  - 两级 scale-up 网络：Tier-1 域 512 x 4 racks 用铜；Tier-2 512 个交换机机架用光 [p30]；扁平 XPU 层级：100k XPU 经光连到单一两级交换集群（768 个交换机架，铜/光混合）[p31，看图核实]；scale-across：4×12.8T XPO 共 51.2 Tbps C+L、每机架 128 对放大光纤，10–10,000 km [p32]
  - Scale-across：4x 12.8T XPO = 51.2 Tbps C+L 波段；每机架 64x C+L 客户侧与线路侧容量；Multi-Rail：每机架 128 个放大光纤对；标注 "10 to 10,000 km, 1000's of parallel fibers" [p32]
- 提到的公司/客户/产品/标准：Ciena（Nitro、Vesta 200、XPO）；Open CPX MSA（6.4T/7.2T 可插拔接口；创始 Ciena、Coherent、Marvell、Molex、Samtec、TeraHop；贡献者含 Accton、AOPT、Alpha、Amphenol、Astera Labs、Avicena、ColorChip、Credo、Eoptolink、FIT、Intel、Ligent、Lightmatter、Lotes、Lumentum、Murata、NextHop AI、Ruijie、Source Photonics、TE、TFC、VIAVI 等，p23 看图核实）；OCI-MSA [p26]；Google TPU v8i、Cerebras WSE-3 [p7]；Nvidia Rubin/B200、Google TPUv1、Cerebras Condor Galaxy、Groq LPU3、Fugaku（roofline 图，p4）；Micron HBM（12+1 叠层 36 GB，p5）；Corning（可拆卸光纤，p27）；Samtec（CPC 图源）；Meta（园区图源，p32）
- 与业界对比或记录声明：无 SOTA/record 声明；论点为 "铜至少用到 400G 世代""最终走向 chiplet 集成光" [p21][p33]
- 推荐配图页：p17（retimer/免 retimer 两栏对比表，覆盖 DAC/ACC/AEC/LPO/CPX 的 reach 与 pJ/bit）；p33（三条结论页）；p18（混合铜扩展 72→256 XPU）；p32（XPO scale-across）

### 0921-Mo12-A4-IMEC-集成光子支撑AI扩展.pdf（共25页，单讲）
- 讲者/机构：讲者姓名幻灯片未显示（照片为一名男性）；imec | 题目：集成光子支撑 AI 扩展（英文原题页未拍到；p1 看图核实为 "Future AI infrastructure is under tension" 页）| 类型：邀请报告（大会报告）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS（3D 集成光学=scale-in）；次 3（调制器/PD/400G 每 lane）
- 核心主张：
  1. AI 基础设施受"性能（更多加速器/内存/带宽）"与"功耗热（功率密度、热极限、供电）"双向挤压；电互连遇到封装尺寸与带宽墙 [p1][p5]
  2. 400G/lane 的 scale-out 可插拔与 scale-up CPO 可由 Ge-on-Si PD/APD 与 GeSi EAM 支撑 [p8][p11][p12]
  3. 面向 chip-to-chip "scale-in" 的 3D 集成光学（晶圆级 SiN 波导、D2W 键合）+ 新材料调制器，目标 <1 pJ/bit；从 pathfinding 走向平台化（iSiPP200/300，即将推出 iSiPP400G）[p14–p19][p21]
- 关键数据：
  - O-band Ge PIN PD：BW >110 GHz，R = 0.9 A/W；Ge APD：BW ~90 GHz，R = 1.9 A/W；眼图 160 GBaud、180 GBaud（O-band，偏压与输入功率小字看图仍不清）；用于 "scale-out 可插拔 400 Gbps/lane"（引 Coughlin & Shahin, OFC 2026 及未发表数据）[p8，看图核实]
  - LNO 调制器 7 mm vs SOH 调制器 50 um 长度对比；材料比：LNO 电极距 few um，OEO 电极距 <200 nm；OEO 的 r/ε 比约 60，LNO 约 1（读图，字小）[p9]
  - GeSi 电吸收调制器（EAM）：23 颗 die 的 S21 调制带宽曲线，Bias 2 V、λ=1560 nm，100 GHz 内滚降约 -2 dB；眼图 212.5 GBaud（PAM4，分四电平），"scale-up CPO at 400 Gbps/lane"（标注 IEDM/ECOC 2025）[p11]
  - "世界首个 100 GHz、低电压 Ge/Si APD"用于 400G/lane 传输：链路为 GeSi FK EAM → Ge APD；425 Gbps 眼图；BER 图 425 Gb/s（6.25% FEC 开销）与 448 Gb/s（12% FEC 开销）两点，BER 约 1e-3–1e-2 区间（读图估计）；引 A. Shahin et al., ECOC 2026 [p12]
  - 3D 集成光学路线图：能效指标 Gbps/mm/pJ/bit，2020→2040 由 1 升至约 1e6；对比 Integrated Optics(3D)、Co-Packaged Optics(2.5D)、Pluggable Optics 三种封装结构 [p13]
  - 300 mm 晶圆级 SiN 波导：传播损耗 <0.15 dB/cm，间距 <6 um，波长 1270–1350 nm；首个 300 mm 晶圆级 reticle-stitched 互连波导（Xu et al., OFC 2024）[p14]
  - 300 mm PIC-on-PIC D2W 键合：键合叠对 <2 um；D2W 倏逝耦合过渡损耗 <0.3 dB（1260–1340 nm）（Xu et al., IEEE 2026）[p15]
  - 新材料：BTO 调制器（实验室器件）损耗 <5 dB/cm，Pockels 系数 ≈300 pm/V；III-V 调制器：300 mm 晶圆级 III-V-on-Si，目标 VπL <0.3 V·cm、损耗 <10 dB/cm；目标 <1 pJ/bit 光互连 [p17]
  - 平台：iSiPP200、iSiPP300，即将推出 iSiPP400G；流程 research→development→silicon→qualification→manufacturing & supply chain，后段由 IC-link by imec 承接 [p21]
- 提到的公司/客户/产品/标准：imec、IC-link by imec、iSiPP200/300/400G、OFC 2026、IEDM
- 与业界对比或记录声明："World's first 100GHz, low voltage Ge/Si Avalanche Photodiode in a 400G-per-Lane Transmission Demonstration" [p12]；"First 300mm wafer-level reticle-stitched interconnect waveguides" [p14]
- 推荐配图页：p12（GeSi EAM→Ge APD 400G/lane 链路、眼图与 BER）；p15（3D 集成光学与 D2W 键合损耗）；p13（三种封装形态与能效路线图）；p19（未来 AI 数据中心架构：scale-in/up/out）
- 页码说明：Ge PD/APD p8；OEO/SOH 调制器 p9；GeSi EAM p11；APD 400G 链路 p12；路线图 p13；SiN 波导 p14；D2W 键合 p15；BTO/III-V p17；架构图 p19；平台化 p21。

### 0921-Mo12-A5-华为-从光创新到NPO与CPO.pdf（共14页，单讲）
- 讲者/机构：讲者姓名幻灯片未显示；华为 | 题目：从光创新到 NPO 与 CPO（原题页未拍到；p1 看图核实为倒拍的 "Three Physical Walls of AI Era: Compute, Memory, and Network"；主线为 NPO vs CPO "多回合"辩论，结论 "NPO is the Optimal Solution for the 200G/Lane Era!"；最末页标题 "The Ubiquitous Optical Interconnect: Illuminating the Entire AI Network"）| 类型：产业发布/邀请报告（大会报告）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO/WSE/OCS；次 3（224G Scale-out）
- 核心主张：
  1. 传统可插拔带来功耗/热极限（高功耗限制系统扩展与可靠性）与前面板密度极限（面板空间、端口数受限）[p2]
  2. 200G/lane 时代 NPO 是最优解：可插拔生态兼容、光学维护解耦、维护停机最小；对比 CPO 的非可插拔生态、高耦合封装复杂度、返厂周期长 [p4][p8]
  3. 标准与开放生态回合：NPO 有统一行业标准、兼容现有基础设施、多供应商；CPO 私有生态、需重新设计基础设施、供应商少；自评比分 "4:1" NPO 获胜 [p6][p7]
  4. 224G+ 之后，能效与密度的下一前沿为 NPO → CPO → OIO（光 I/O）演进；CPO 与 OIO 各有工程挑战 [p11][p12][p13]
- 关键数据：
  - Round 2（可插拔与维护）、Round 3（能效与集成）：NPO——高能效、板级组装、厘米级走线插损；CPO——极致能效、2.5D/3D 封装、毫米级直连以最小化损耗（定性，无数值）[p4][p5]
  - Round 5：6.4T/12.8T NPO Project 时间线：Project Start 2026.5、Baseline 2026H2、Ballot、Publication 2027H2–2028H1（看图核实，与全场连拍版 p97 一致）；NPO 胜，总比分 4:1；标准组织名称页面未显示 [p6, p7]
  - Hi-ONE：号称"业界首个内置激光源的 7.2T NPO 光引擎"（High-density Optical-interconnect-Node Engine），已量产；对比 1.6T 光模块（读图）：带宽 4.6X（7.2T）、可靠性故障率下降 90%（10 A-fit → 1 A-fit，读图）、时延下降 90%（100 ns → 10 ns，读图）、功耗下降 66%（15 pJ/bit → 5 pJ/bit，读图）；柱图数值字很小，均需原图复核 [p9]
  - Hi-ONE 设计要点："τ-Scaling Law"（几何尺度 L(nm) → 时间尺度 τ(ps)，System→Data Center/SuperPOD/Rack/Module&Board/Chip/Circuit/Device）；线性架构降低电链路时延与功耗；ILS(外置光源)+EIC+PIC 联合设计降低外部激光功率与插损 [p10]
  - CPO 工程挑战：亚微米高密度设计（对准容差、自动化瓶颈、热漂移）；测试挑战（电光协同仿真测试、协同测试标准缺失、设备短缺）；故障隔离与冗余（光冗余、系统隔离、预测性监控）[p12]
  - OIO 挑战：中介层级 3D 光子布线（多层硅波导、串扰抑制、弯曲损耗最小化）；信号完整性与异质阻抗（测试瓶颈、阻抗匹配、热翘曲缓解）；热敏感与调谐代价（被动热稳定、高调谐功耗、高速局部补偿）[p13]
  - 全网络光互连视图：Scale-in(Intra-Chip)→Scale-up(Intra-Tray/Rack/POD)→Scale-out(DCN)→Scale-Across(DCI) [p14]
- 提到的公司/客户/产品/标准：华为 Hi-ONE（7.2T NPO 光引擎）；NPO 6.4T/12.8T 标准项目（标准组织名称页面未显示）；NPO、CPO、OIO 概念（p11–p13 看图核实：CPO 挑战为亚微米对准/自动化/热漂、光电协同测试标准与设备缺口、故障隔离与冗余；OIO 挑战为中介层 3D 光路由、信号完整性与异质阻抗、热敏感与调谐功耗）
- 与业界对比或记录声明："Industry's 1st 7.2T NPO With a Built-in Laser Source""World's first 7.2 Tbps NPO optical engine"[p9]；"Round 5 Winner 4:1"（自评）[p7]
- 推荐配图页：p9（Hi-ONE 7.2T 对比 1.6T 的带宽/可靠性/时延/功耗柱图，注意需高清复核）；p6（NPO 标准时间线与开放生态对比）；p14（全 AI 网络光互连分层图，注意该页图片方向颠倒）
- 页码说明：p2/p3 为传统可插拔瓶颈（同页两次拍摄）；p4=Round 2；p5=Round 3；p6=Round 5；p7=Round 5 获胜（总比分 4:1）；p8=结论；p9=Hi-ONE；p10=τ-Scaling；p11=224G 以后 NPO/CPO/OIO；p12=CPO 挑战；p13=OIO 挑战；p14=全网络光互连。本 PDF 无 Round 1、Round 4 页（p1 为 "Three Physical Walls" 倒拍页）；两回合内容见 B23 全场连拍版 p91–p96（均 NPO 胜）。

### 0921-Mo12-A6-PsiQuantum-光子量子计算.pdf（共34页，单讲）
- 讲者/机构：Mark Thompson（Co-Founder & CTO，据同场全场连拍版题目页）；PsiQuantum | 题目：Photonics for quantum computing（本 PDF 未拍题目页；p5 页 "How to build and scalable photonic quantum computer"，看图核实）| 类型：邀请报告（大会报告）
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS；次 4（OCS）、3（光电子/低损耗 SiN）
- 核心主张：
  1. 规模化量子计算的四大挑战：量子比特、可制造性（需制造并测试百万级元件）、互连（芯片间高保真传输量子比特→模块化）、制冷功率与控制电子；光子路线以半导体制造与光子学解决 [p4][p5]
  2. 用超低损耗 SiN 光子学（波导、交叉、分束器、弯曲、边耦合器、FAU 封装）支撑光子量子电路的高保真度 [p9–p15]
  3. 快速光开关/路由与自研 OCS 可作为光子技术向数据中心互连的溢出；下一代 4×64 OCS（研发中）[p21][p25][p26]
- 关键数据：
  - 量子电路性能：单量子比特态制备与测量保真度 99.98% ± 0.01%；量子比特互连（偏振编码）保真度 99.72% ± 0.04%；双量子比特 fusion 保真度 99.2% ± 0.12%；出处 "A manufacturable platform for photonic quantum computing" (2025) Nature [p9]
  - SiN 波导（厚 ~400 nm）：单模 1.3 dB/m（晶圆均值 1.8 ± 0.2 dB/m，图注）；多模 0.1 dB/m（晶圆均值 0.5 ± 0.3 dB/m）；损耗随年份对数下降（2022→2025）[p10]
  - 无源器件插损：交叉 0.27 ± 0.1 mdB（99.993%），串扰 <-80 dB；分束器 0.56 ± 0.03 mdB（99.987%），分光偏差 0.99%（1σ）；90° 弯曲 0.25 ± 0.03 mdB（99.994%）[p11]
  - 边耦合器（标准光纤，单纤探针）：2024 年 127 ± 18 mdB（97%）；2025 年 65 ± 13 mdB（98.5%）[p14]
  - 62 端口 FAU 贴装统计（7 月两周样本，约 100 次构建）：光纤到芯片损耗中位数 130 mdB；均值 150 ± 50 mdB；<200 mdB 占 90%；<100 mdB 占 10%；>300 mdB 失败占 3%；破损(>1 dB)占 0% [p15]
  - 快速 8×8 光开关：~1 GHz 切换速度，上升/下降时间 <1 ns，平均消光比约 25 dB（图示 500 Mbit/s 测试）[p21]
  - 光子复用器：8 个光子源，激光时钟 250 MHz，前馈时间 60 ns，光子保真度 ~99%（@8 kHz），源亮度提升 ~2x；使用 8×8 BTO 开关与 100 ns 光延迟线 [p22]
  - OCS 原型（8×8）：基数 8，插损均值 ~1.0 dB（最大 ~1.7 dB，差异归因于 de-embedding MPO 连接器损耗），串扰均值 ~60 dB（最小 ~55 dB），重构时间 <1 ms；严格无阻塞、偏振跟踪、全无源（无光放大）[p25]
  - 下一代 4×64 OCS（研发中）：4 个光子交换 PIC，256 个光 I/O 端口（4×64），1U 机架式，全互联严格无阻塞，重构 "sub-ms 至 sub-μs"（小字），无光放大器、低驱动电压 [p26]
  - 模块间量子比特互连：Daresbury 英国站点两个模块间 250 m 光纤、time-bin 编码/解码，实验室间互连保真度 ">99.7"（右侧文字被裁切，未稳定化光纤）[p28]
  - 单光子探测（超导纳米线 SNSPD，NbN on SiN）：探测效率 ~100%，灵敏度 -160 dBm(~1 aW)，抖动 <5 ps，死时间 ~1 ns（GHz 级工作），暗计数 <1 Hz，工作温度 ~4 K [p16，看图核实]
  - 测试规模：室温测试 2,400,000/月，低温测试 130,000/月 [p7，看图核实]
- 提到的公司/客户/产品/标准：PsiQuantum、GlobalFoundries（p5 看图核实，另有 Linde 低温柜）、Nature 论文、Google Willow / Quantinuum H1 / Google Echo（p2/p3 背景引用，看图核实）、Illinois Quantum & Microelectronics Park (IQMP)，2025 年 10 月芝加哥动工、伊州政府承诺 5 亿美元；2026 年 6 月布里斯班动工、澳联邦与昆州政府投资 6.5 亿美元 [p33，看图核实]、Frontier 超算机架（对比尺度）[p27]
- 与业界对比或记录声明：无正式 SOTA 声明；边耦合器从 2024 到 2025 损耗减半（127 → 65 mdB）[p14]；引用业界观点 "多数领域仍认为有用机器需 5–10 年" [p3]
- 推荐配图页：p9（三项量子电路保真度）；p25（OCS 原型性能指标与损耗/串扰散点图）；p26（4×64 OCS 系统结构）；p15（62 端口 FAU 贴装损耗分布）

## 本批小结
1. AI 互连的核心矛盾被三家不约而同地定位在"封装/前面板密度 + 能效"：Ciena 提出"两片芯片表面承担 供电/散热/I/O 三功能"，前面板密度从 OSFP 70 Tbps 到 mini 光连接器 624 Tbps [Ciena p8 p15]；imec 提出电互连遇封装与带宽墙 [IMEC p5]；华为指出可插拔的功耗与前面板密度双瓶颈 [华为 p2]。
2. 铜与光的分工：Ciena 强调 200G PAM4 时代免 retimer（ACC 3.5 m/1.5 pJ/bit，LPO/CPX 6 pJ/bit vs retimed 光 16 pJ/bit），混合铜可将 scale-up 域从 72 扩到 256 XPU，铜至少用到 400G 世代 [Ciena p17 p18 p21]；华为主张 200G/lane 时代 NPO 最优，224G+ 后再看 CPO/OIO [华为 p8 p11]。两者都倾向"渐进式"而非直接 CPO，但路径不同（Ciena 用 Open CPX MSA 的可插拔式近封装光 + 铜，华为用 NPO 标准 6.4T/12.8T）。
3. 400G/lane 器件路线在 imec 被具体化：Ge PIN >110 GHz、Ge APD ~90 GHz（O-band）、GeSi EAM 212.5 GBaud 眼图、GeSi EAM→Ge APD 425/448 Gb/s 传输，并称首个 100 GHz 低电压 Ge/Si APD；与 Ciena 的 "448G 电/光眼图对比"共同表明 448G 世代已进入器件层验证 [IMEC p8 p11 p12; Ciena p21]。
4. Scale-in（封装内/晶圆级光互连）从概念走向工艺指标：imec 300 mm 晶圆级 SiN 波导 <0.15 dB/cm、D2W 过渡损耗 <0.3 dB，并设 <1 pJ/bit 目标；华为把 OIO 的挑战列为中介层 3D 光子布线、热调谐代价；Ciena 亦提到 chiplet 集成光学与可拆卸光纤（solder-reflow 兼容）是 XPU 封装承诺光学的关键 [IMEC p14 p15 p17; 华为 p13; Ciena p27]。
5. Scale-across/超大规模：Ciena 以 4x12.8T XPO=51.2 Tbps C+L 与每机架 128 光纤对多 rail 描述 DCI 侧的"大规模并行"，并给出 100k XPU 的两级交换架构（Tier-1 铜、Tier-2 光）[Ciena p30 p31 p32]；华为的全网络分层图把 scale-across 放在 DCI 层 [华为 p14]。
6. 光子技术向数据中心 OCS 外溢的信号：PsiQuantum 基于超低损耗 SiN（波导 0.1–1.3 dB/m、交叉 0.27 mdB）做出 8×8 OCS 原型（插损均值 ~1.0 dB、串扰 ~60 dB、<1 ms）并在研 4×64/256 端口 OCS，可对照 AI 集群 OCS 需求（本批其余三讲未直接涉及 OCS）[PsiQuantum p25 p26]。
