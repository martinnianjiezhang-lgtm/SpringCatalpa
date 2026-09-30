---
title: "B30 · DAY2 · Mo4-I-AI互连之争-第二场"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo4-待定-Arista-题目未公布.pdf（第1–24页；p10/p11/p16为另一版重复页）
- 讲者/机构：讲者姓名页面未显示 / Arista | 题目：未公布（p1 看图核实为 "Five Different Categories and Requirements"：机架级 scale-up 2 m、多机架 scale-up 10–20 m、数据中心 scale-out 500 m–2 km、园区 scale-across 2–20 km、城域 scale-across 100+ km；内容为 XPO 模块与 AI 互连五类场景） | 类型：邀请报告（Mo4 AI互连之争）
- 方向归属（主/次）：主 4（Scale-up/in：XPO，可插拔与CPO之外的新形态）；次 3（Scale-out 224G/448G）
- 核心主张：
  1. AI 互连分五类场景，每类都要求最低功耗、成本与失效率 [p1]。
  2. 芯片级接口是关键，200G→400G SerDes 将主导下一代；高速SerDes保留可插拔生态，低速并行 50G-NRZ 功耗/时延/BER更低但需先进封装 [p22]。
  3. XPO 支持所有光标准、光技术、系统接口、连接器与线缆，并称是首个支持 400G/lane 电接口的光模块 [p19]。
- 关键数据：
  - 五类需求：Scale-UP 机架级 2 m；Scale-UP 多机架 10–20 m；Scale-OUT 数据中心 500 m–2 km；Scale-ACROSS 园区 2–20 km；Scale-ACROSS 城域 100+ km [p1]
  - 介质（Dielectric）射频传输可扩展到 100 GHz，支持 400G-PAM4、10 m 距离；无激光器/PD/精密光纤对准，成本对标有源铜缆 [p3]
  - Scale-Up 10–20 m 有五种技术竞争：Dielectric、RF-Microwave、slow&wide VCSEL阵列、slow&wide DWDM、fast&narrow光+先进封装 [p2]
  - OSFP：今年出货 120M+，2028 预计 200M+；30–40 W（风冷或液冷）；前面板 32个/1U；1600G-OSFP 对应 51.2T；OSFP 连接器升级到 400G/lane 在进行中 [p7]
  - XPO 结构：两块相同的 32 通道 paddle card 背靠背装在共享中心冷板上；冷板带快拆；每块 32 通道适配现有 8 通道硅光；2个高速边缘连接器+独立电源连接器 [p12]
  - XPO 卡边 448G 仿真（差分插损，224G XPO 对 448G XPO 两条曲线）：假设 5 bit 编码于 2 个 PAM6 符号，符号率约 179.2 GBd，Nyquist 约 89.6 GHz；目标 448G PAM4 约 112 GHz，448G PAM6 约 67–90 GHz；曲线上 448G 曲线在约 110 GHz 处约 -3 dB（读图估计） [p17]
  - XPO MSA：2026-03-20 成立，150家成员；XPO 1.0 规范 2026-07-31 发布；量产模块预计 2027 Q1；聚焦 204.8T 交换平台；400G/lane（25.6T/模块）路线图进行中 [p24]
  - 可靠性：元件远少于 8个 OSFP，元件温度更低、温变小、线性电通道干净，失效率远低于 8 个 OSFP [p13]
- 提到的公司/客户/产品/标准：OSFP、XPO、XPO MSA、LPO、LRO/TRO、FRT、Inverse Gearbox、MPO/MMC/SN-MT/EBO连接器、SiPh/InP/VCSEL/TFLN/BTO/有机光、CL/ZR
- 与业界对比或记录声明：称 XPO 是首个支持 400G/lane 电接口的光模块 [p19]；OSFP 称为"史上出货量最大的可插拔" [p7]
- 推荐配图页：p12（XPO 堆叠爆炸图）；p17（448G 插损仿真曲线）；p24（XPO MSA 时间线）

### 0921-Mo4-待定-Broadcom-为AI扩展光互连-走向大规模CPO集群.pdf（第1–17页；p9与p8内容相同）
- 讲者/机构：Rajiv Pancholy（Director, Hyperscale Strategy and Products, Optical Systems Division）/ Broadcom | 题目：Scaling Optical Interconnects for AI: Manufacturing Pathways to Massive CPO-Enabled Clusters | 类型：邀请报告
- 方向归属（主/次）：主 4（CPO）；次 3（Scale-out 224G/448G）
- 核心主张：
  1. 光互连选项从 DSP/LRO/LPO、NPO/OBO、CPO 到 OCI（未看全），CPO 号称相对可插拔 10x 可靠性提升 [p4]。
  2. CPO 规模化面临三项挑战：先进封装、光连接、量产制造 [p10]。
  3. OCI-MSA 的动机：电/光 200G→400G→800G 路线，光侧分 Gen1 200G、Gen2 400G、Gen3 800G [p14]。
- 关键数据：
  - 各方案定位：可插拔"灵活但距离/功耗/性能受限"；NPO/OBO"面板密度与热改善"；CPO"相比可插拔 10x 可靠性提升"；第四行（被遮挡，疑为 OCI）"最低时延、功耗、成本，可靠性与铜相当" [p4]
  - TH6-Davisson 光链路：稳定；完全兼容 IEEE 802.3dj 光规范；图为 32x200G PAM-4 BER 与 OE0/OE1 FEC 尾部 16.5 小时 KP4 FEC 链路余量，具体 BER 数值看图仍不可读 [p8]
  - CPO 挑战：PIC 到 EIC 高密度高质量贴合（图示 COUPE 贴合）、为 400G 直驱做使能；每个芯片封装需连接超过 1k 根光纤，需可分离光纤连接以支持封装回流；量产需行业领先良率和自动化，配自动点胶装卸载 [p10]
  - OCI-MSA 表：电 200G PAM-4 / 400G PAM-4/6/8 / 800G ?；光 200G PAM-4 / 400G PAM-4 / 800G ?；线性(Linear)：200G YES、400G MAYBE、800G UNLIKELY；OCI-MSA 支持 NRZ、DWDM、Bi-Di，Gen1 200G/Gen2 400G/Gen3 800G；NRZ 是最低时延路径 [p14]
  - p13 看图核实：OCI-MSA（2026 年 3 月成立）创始成员 logo 为 Meta、Microsoft、OpenAI、AMD、Broadcom、NVIDIA；目标"把 scale-up 从机架内扩到多排"（横幅部分遮挡）
- 提到的公司/客户/产品/标准：Tomahawk 6 "TH6-Davisson" CPO、IEEE 802.3dj、KP4 FEC、OCI-MSA、COUPE、LPO/LRO/DSP、NPO/OBO
- 与业界对比或记录声明：CPO 相对可插拔 10x 可靠性提升（讲者声明）[p4]
- 推荐配图页：p4（DSP/NPO/CPO/OCI 光互连选项对比图）；p10（CPO 三大挑战）；p14（OCI-MSA 世代路线表）

### 0921-Mo4-待定-Cerebras-题目未公布.pdf（第1、9–16页；p2–p8为另一版重复页）
- 讲者/机构：Jean-Philippe Fricker（Co-Founder & Chief System Architect）/ Cerebras Systems | 题目：Heterogeneous Hybrid Bonding: A Path to Wafer-Scale Optical Systems | 类型：邀请报告
- 方向归属（主/次）：主 4（WSE/CPO 类晶圆级光 I/O）；次 3（光源/电芯片）
- 核心主张：
  1. 异质混合键合把集成能力从单一计算晶圆扩展到逻辑、存储、光子等异质技术（p10 看图核实：晶圆级系统已具备量产级良率韧性晶圆集成、垂直供电、集成冷却、晶圆级机械热控、测试制造设施；叠层示意 Optical I/O + WSE + DRAM，标注 "Forward-looking extension"）。
  2. 晶圆表面 E/O 转换可在每个计算区域附近进行，低损耗波导把信号从晶圆中心送到边缘，避免电信号跨晶圆传输的功耗损失与带宽密度限制 [p11]。
  3. 集成光 I/O 改变优化问题，需要在带宽密度、激光器位置、SerDes、热、可测试性/良率等维度重新权衡 [p14]。
- 关键数据：
  - CS-6：晶圆级 SRAM + 3D 堆叠 DRAM，"在 HotChips'26 发布"；称世界最快推理速度、数量级更小占地；WSE、DRAM 分层 [p9]
  - 堆叠图含 Optical Wafer / WSE / DRAM 三层 [p11]
  - 五个设计维度：带宽密度（光 I/O BW/mm 晶圆边；电 I/O BW/mm² 穿过键合晶圆表面）；激光器（集成或外置，可靠性与热隔离）；SerDes（针对晶圆键合通道重新优化模拟前端）；热兼容（光子与大功率计算共存）；可测试性与良率（"足够好"晶圆策略、光测试接入、修复与冗余）[p14]
  - p15 看图核实：集成光 I/O 改变优化问题——带宽密度（晶圆边 BW/mm 与键合面 BW/mm²）、激光位置（集成或外置、可靠性与热隔离）、SerDes 集成（为键合通道重优化模拟前端）、热兼容、可测性与良率（known-good-enough 晶圆、光测试接入、修复冗余）、可服务性与标准（可更换性与互操作边界位置）
  - 无具体带宽、功耗数值（讲稿中看到的页均为定性）
- 提到的公司/客户/产品/标准：Cerebras CS-6、WSE、HotChips'26
- 与业界对比或记录声明：称 CS-6 为"世界最快推理速度"（营销声明，无对比数据）[p9]
- 推荐配图页：p11（含光晶圆的三层晶圆堆叠与 E/O 逃逸）；p14（集成光 I/O 五维权衡表）

### 0921-Mo4-待定-Marvell-每一层都用硅光.pdf（第1–9页）
- 讲者/机构：讲者姓名页面未显示 / Marvell | 题目：未见完整原题（p1 看图核实为 "AI is everywhere" 开场页；文件名概括为"每一层都用硅光"） | 类型：产业发布/邀请报告
- 方向归属（主/次）：主 3（Scale-out 光源/调制器，硅光）；次 4（Scale-up）
- 核心主张：
  1. AI 规模是新约束：XPU 从 128 增到 1M，互连数量从 128 增到 >10M [p3]。
  2. Marvell 连接每一段距离：铜用于封装(<10 mm)与机架(2.5–7 m)，光纤用于数据中心(up to 500 m+)与分布式数据中心(up to 1,000 km+) [p5]。
  3. 硅光市场量持续增长、"room for all"，新调制器技术将从高端切入 [p9]。
- 关键数据：
  - 规模阶梯：128 XPU/128 互连；1K/2K；25K/75K；100K XPU（2024）/500K；1M XPU/>10M 互连 [p3]
  - 铜到光过渡（单机架带宽 vs 铜距离）：100G 5 m；200G 2.5 m（标"TODAY"）；400G 1.25 m；800G 0.6 m；1.6T 0.3 m；机架 2.5–7 m 与封装 <10 mm 仍用铜（看图核实）[p6]
  - 光调制器/光器件市场（Sales \$M，2022–2031）：2026 约 \$37–38B（纵轴 \$0–\$80,000 M，读图估计），2031 约 \$68–70B；分层为硅光(最大)、InP、GaAs、TFLN/LiNbO3 bulk 及其他；来源 LightCounting, May 2026, Silicon Photonics, LPO/LRO and CPO/NPO [p9]
- 提到的公司/客户/产品/标准：Marvell、LightCounting、硅光/InP/GaAs/TFLN
- 与业界对比或记录声明：无 SOTA 声明
- 推荐配图页：p6（铜到达距离随速率缩短的曲线）；p9（各材料体系光器件市场堆叠柱图）

### 0921-Mo4-待定-MicrosoftAzure-AI纵向扩展与通用算力的光互连用例.pdf（第1–10页）
- 讲者/机构：讲者姓名页面未显示 / Microsoft Azure | 题目：未见原题（p1 为倒拍的 "Key messages" 页，看图核实：近期聚焦 AI scale-up 与通用算力内存解耦；OCI 规范提供多代通用 PHY；Wave 1 引入 OCI 光学用于 scale-up，Wave 2 更紧集成并扩展到内存解耦，VCSEL 成为选项） | 类型：邀请报告
- 方向归属（主/次）：主 4（Scale-up，OCI）；次 3（Scale-out）
- 核心主张：
  1. 平台连接包含多种用例，近期光学机会是 AI scale-up（A）与通用计算内存解耦（D）[p3]。
  2. Scale-up 光互连需要 OCI 规范（多代通用 PHY），OCI-MSA 提供业界聚焦与可互操作的供应商生态 [p6]。
  3. Microsoft 路线：Wave 1 引入 OCI 光学用于 scale-up；Wave 2 推进下一代 OCI，配合更紧密集成并拓展到内存解耦等新用例，VCSEL 等技术成为选项 [p1，页面倒置拍摄]
- 关键数据：
  - 用例表：A 交换式 Scale-Up（加速器-交换机）；B 直连 Scale-Up（加速器-加速器）；C 主机 I/O 扩展（加速器-CPU via PCIe）；D 内存解耦与池化（CPU/加速器-内存池 via PCIe/CXL）；E 封装级（加速器-HBM）；F Chiplet 互连（Die-to-Die）；A/B 归为 Scale-up，C/D 归 PCIe/CXL，E/F 归 Scale-in [p3]
  - OCI 带宽路线：200 Gbps Today；400 Gbps 2027(?)；800 Gbps TBD，>2030(?)；OCI GEN1 Today [p6]
  - 规范面临三挑战：扩展节奏（AI 系统演进快于传统以太网周期）、选择过多（调制、波长、封装等需对齐）、生态互操作 [p6]
  - 内存解耦关键指标：时延 <5 ns 光模块；功耗 <4 pJ/bit；距离机架内今日 1–3 m，未来行级 20–50 m；形态 Off-package → NPO → CPO [p8]
- 提到的公司/客户/产品/标准：OCI（Optical Compute Interconnect）、OCI-MSA、PCIe/CXL、VCSEL、HBM
- 与业界对比或记录声明：无 SOTA 声明
- 推荐配图页：p3（六类光互连用例及平台拓扑）；p6（OCI 规范挑战与带宽路线）；p8（内存解耦指标）

### 0921-Mo4-待定-NVIDIA-纵向与横向扩展的光方案.pdf（第1–12页）
- 讲者/机构：Ling Liao / NVIDIA | 题目：Optical Solutions for Scale-out & Scale-up Connectivity | 类型：邀请报告
- 方向归属（主/次）：主 4（CPO，Scale-up）；次 3（Scale-out、硅光 DWDM）
- 核心主张：
  1. NVIDIA CPO 与生态伙伴共同发明：TSMC COUPE 引擎，单通道 212.5 Gbps 在生产环境测得，BER < 1e-10（原页面写 1-e10）[p5]。
  2. Scale-up CPO 有四种候选：以太网 PAM4 硅光、DWDM NRZ 硅光、宽而慢 VCSEL、μLED，按成熟度/覆盖距离/功耗/岸线带宽密度/成本/时延/光纤带宽可扩展/OCS 兼容性对比，DWDM NRZ 硅光在多项打勾 [p8]。
  3. DWDM 提供可扩展的光纤带宽路径，NRZ 意味着低 FEC 时延与改善链路预算，并联低速主机电接口带来低能耗与高岸线带宽密度，微环是关键使能 [p9]。
- 关键数据：
  - CPO 引擎（TSMC COUPE）：EIC 采用 TSMC FinFET 逻辑工艺；PIC 采用 SOI N65 硅光工艺；SoIC 键合加密集 RDL；微透镜设计配光栅耦合器 [p5]
  - DWDM 性能：8λ MUX / x32 功分器，在引擎 PIC 上；200 GHz 波长间隔；间隔变化 <±20 GHz；功率变化 <±0.5 dB；约 60 dB SMSR；FWM 极小 [p11]
  - 8λ x 32 Gb/s NRZ DWDM 链路，COUPE 引擎：所有通道开启并锁定，PRBS31，16 小时测量无误码 [p11]
  - 选项对比（best / next best 打勾）：Ethernet PAM4 SiPho 在成熟度、距离、光纤/装配成本、OCS 兼容性等打勾；DWDM NRZ SiPho 在岸线带宽密度、光纤带宽可扩展、时延、OCS 兼容等打勾；VCSEL 与 μLED 在功耗、芯片成本、时延上占优（勾的深浅见图，未逐格核实）[p8]
- 提到的公司/客户/产品/标准：NVIDIA CPO、TSMC COUPE（8λ×32 Gb/s NRZ DWDM 链路，200 GHz 间隔，16 小时无误码）、SOI N65 SiPho、SoIC、OCS；p11 引用同会议论文 Tu1-C5（A. Rekhi 等，Static and Dynamic Ring Assignment in a Clock-Forwarded DWDM Optical Link）与 Th2-E1（N. Mehta 等，A 4-λ x 64 Gb/s Polarization-diverse Silicon Photonic DWDM Receiver）；8λ MUX 谱：波长间隔偏差 <±20 GHz、功率偏差 <±0.5 dB、SMSR 约 60 dB（看图核实，照片较糊）
- 与业界对比或记录声明：212.5 Gbps "Measured (in production)" [p5]；无 record 措辞
- 推荐配图页：p5（212.5G 眼图与 COUPE 结构）；p8（Scale-up CPO 四方案对比表）；p11（DWDM 光谱与 8λx32G NRZ 链路实测）

## 本批小结
1. Scale-up 出现"三条并行路线"：可插拔延伸（Arista 的 XPO/OSFP 走 200G→400G SerDes，p1/p22）、CPO/DWDM（NVIDIA 的 COUPE 引擎与 DWDM NRZ）、OCI-MSA 通用 PHY（Broadcom p14、Azure p6）。来自 Arista、NVIDIA、Broadcom、Azure。
2. 200G/lane 已是今日节点，400G/lane 被多家标为下一步：Arista XPO 称首个支持 400G/lane 电接口并给出 2027 Q1 量产、204.8T 平台；Azure 的 OCI 时间线写 400G 为 2027(?)；Broadcom OCI-MSA 光侧 Gen2 400G。800G/lane 各家均标"?"或"unlikely"（Broadcom 线性 800G 为 UNLIKELY）。来自 Arista、Azure、Broadcom。
3. 线性/低时延与 FEC 权衡：Broadcom 称 NRZ 提供最低时延路径且线性驱动在 400G 仅"MAYBE"；NVIDIA 强调 NRZ+DWDM 降低 FEC 时延；Arista 讲低速并行 50G-NRZ 需先进封装。来自 Broadcom、NVIDIA、Arista。
4. 铜光边界持续缩短：Marvell 给出 200G 时铜 2.5 m、400G 1.25 m，Arista 提出介质射频 400G-PAM4 达 10 m，试图延缓光替代铜。来自 Marvell、Arista。
5. 规模化 CPO 的瓶颈落在制造与连接：Broadcom 强调每封装 >1k 光纤、可分离光纤连接与自动化良率；Cerebras 强调晶圆级光 I/O 的良率、测试与激光器位置。来自 Broadcom、Cerebras。
6. 应用场景外延：Azure 把内存解耦（<5 ns、<4 pJ/bit）当近期光学机会；Arista 与 Marvell 均把 Scale-ACROSS 园区/城域（100+ km、1,000 km+）纳入光互连全景。来自 Azure、Arista、Marvell。
