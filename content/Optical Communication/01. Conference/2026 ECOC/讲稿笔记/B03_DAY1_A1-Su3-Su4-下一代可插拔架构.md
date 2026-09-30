---
title: "B03 · DAY1 · A1-Su3-Su4-下一代可插拔架构"
tags:
  - ECOC2026
  - DAY1
---

# B03 笔记：ECOC 2026 周日 Workshop「Meeting diverse AI connectivity needs: Architectural choices for next-generation pluggable transceivers」（Su3/Su4）

说明：页码为 PDF 页码（非幻灯片角标页码）。数值均来自图片核对；看不清处已注明。

### 0920-pm-Su3-A-01-LightCounting-AI连接硬件市场.pdf
- 讲者/机构：Daryl Inniss，LightCounting（首席分析师） | 题目：How Will AI Shape the Connectivity Market（副标题 Meeting Diverse AI Connectivity Needs: Architectural Choices for Next Generation Pluggable Transceivers） | 类型：市场分析
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO]；次 [3 Scale-out 224G/448G/光源/调制器]
- 核心主张：
  1. 2026 年是硅光之年：硅光收发器首次超过整个收发器市场的 50%。
  2. 四类网络段（scale-in、scale-up、scale-out、scale-across）对互连要求各异；scale-up 互连"contested"，铜与光并存；scale-out 走 SiPh，448G/lane，可插拔为主、部分 CPO。
  3. CPO/OE 进入半导体体系后，光学制造责任转移（对准与测试从模块厂移到 OSAT/晶圆级），是"产业测试流程的结构性转变"，模块不会消失。
- 关键数据：
  - 硅光占收发器销售额首次超 50%（2026），图示 2022–2031 年按硅光/InP/GaAs/TFLN-LiNbO3 分类的销售额堆叠柱，2031 年 TFLN/LiNbO3 占比明显上升；纵轴具体数值看不清 [p3]
  - 四段网络：scale-in 毫米级，"Perhaps optical in the future"；scale-up 约 1 米，限制为边缘/引脚/瓦特，"Copper and optical, Pluggable/CPx"；scale-out 数十至数百米，"SiPh: 448G per lane, Pluggable, some CPO"；scale-across 500 米至公里级，"SiPh integration: full spectrum coherent transponder, Pluggable back to embedded" [p5]
  - 引用 Microsoft Paolo Costa（ACM SIGCOMM 2026 HotOptics 工作坊）提出的"打破封装墙"光互连目标：<10 ns 延迟、<1 pJ/bit、>10 Tbps/mm、<<10 FIT、10 m 覆盖 [p10]
  - "强 scale-up CPO 增长"情景：按单位数（M）分 Non-AI & Front-end / AI scale-out / AI scale-across / AI scale-up 及 "scale-up upside"，2029 起 scale-up 出现并扩大，2031 最大；纵轴刻度看不清 [p11]
  - p12 引用 Latitude Design Systems CTO Terence Chen（2026 Taiwan AI 光通信与先进封装论坛）：CPO 时代对准责任从模块厂光学线转到 OSAT 先进封装线，测试从模块级变为晶圆级（OSAT 为 CPO 新建）（OCR 文字，未开图）[p12]
  - p4 表列出各类厂商市值与 CMOS 节点（OCR 数字乱码，未采信）；p8/p9 为云厂商 capex 与收发器销售增速相关性图，数值看不清
- 提到的公司/客户/产品/标准：Microsoft（Paolo Costa）、Latitude Design Systems、OSAT、代工厂、CPO/NPO、LPO/LRO；LightCounting 报告：May 2026 Silicon Photonics LPO/LRO and CPO/NPO；May 2026 Optical Vendor Landscape；July 2026 Cloud Data Center Optics
- 与业界对比或记录声明（SOTA/首次/record）：硅光收发器份额首次超 50%（2026）[p3]
- 推荐配图页：p3（硅光份额转折堆叠柱图）；p5（四类网络段互连要求表）；p10（打破封装墙及 5 项目标）

### 0920-pm-Su3-A-02-OpenAI-ScaleUp互连需求.pdf
- 讲者/机构：OpenAI（讲者姓名未在所看页中出现） | 题目：AI Scale-Up Networks: Requirements for Reliable, High-Bandwidth-Density Interconnects | 类型：邀请报告
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 Scale-out]
- 核心主张：
  1. 工作负载决定网络需求：通信模式决定带宽、延迟、覆盖距离和密度需求。
  2. 恢复（故障频率、受影响容量、恢复服务时间）是交付性能的一部分。
  3. 应以系统结果（请求延迟与单请求能耗）比较铜、可插拔、NPO、CPO，而非只比链路指标。
- 关键数据：
  - 自研加速器 Jalapeno 的 scale-up 系统：本地域 128 颗 Jalapeno 通过 Broadcom TH6；全局域 2048 颗 Jalapeno，经 TH6 rail 0–rail 7；"Half flattened" 两级 Clos 拓扑；张量并行需更高带宽、专家并行带宽较低、两者都要低延迟（OpenAI, Hot Chips 2026）[p7]
  - 系统对比 GB300 MTP：混合吞吐（mixed tokens/s/kW）纵轴到 20,000；Jalapeno 最小端到端请求延迟 1.65 s，GB300 MTP 为 3.69 s；同等混合吞吐点约 "≈1.8× lower latency"；解码速度可到约 700 tokens/s/user，超出 GB300 MTP 限制（约 330 tokens/s/user 处标线）[p8]
  - 请求分三种硬件形态：Prefill（注意力重、计算受限，通信容易）、Decode（MoE 需存储带宽，通信呈突发）、Speculate（小模型、超低批量，网络带宽低但极端延迟敏感）（OCR 辅助）[p5]
  - 指标：TTLT（time to last token）、单用户延迟、Energy/token = tokens/Joule；低延迟通常每 token 能耗更高 [p3]
  - 互连四选项对比表：铜（短距机架内好；受距离与通道损耗、线缆体积/走线/风道限制）；可插拔（可更换、生态成熟、可选距离；主机通道损耗、前面板功耗/密度、LPO/LRO 主机负担与故障隔离、功效）；NPO（电路径短、光组件分离；内部维护与散热、激光处理、插座/生态/可靠性认证、功效）；CPO（封装内路径短、光 I/O 密集、I/O 功耗潜在节省；封装与良率、热耦合、激光、光引擎修复、生态/可靠性认证）[p10]
  - 共设计架构：每个 core slice 与一个 HBM slice 配对（本地路径最快）；集体网络（高带宽低延迟）+ 通用 NoC（较低带宽较高延迟）；含 scale-up Ethernet bridge [p6]
- 提到的公司/客户/产品/标准：OpenAI、Jalapeno（OpenAI 自研芯片）、Broadcom TH6、NVIDIA GB300、OIF（2023, 2026 引用）、HBM、Ethernet scale-up
- 与业界对比或记录声明（SOTA/首次/record）：Jalapeno 相对 GB300 MTP 同吞吐下约 1.8× 更低延迟 [p8]
- 推荐配图页：p8（Jalapeno 对 GB300 MTP 的吞吐-延迟曲线）；p10（铜/可插拔/NPO/CPO 强项与约束对照表）；p7（128/2048 Jalapeno 两级 Clos 拓扑）

### 0920-pm-Su3-A-03-Oracle-AI超集群光互连.pdf
- 讲者/机构：Oracle（OCI；讲者姓名未在页面中出现） | 题目：Photonic interconnects for modern AI superclusters | 类型：邀请报告
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [4 Scale-up/in CPO/NPO/XPO]、[2 Scale-across/ZR/ZR+]
- 核心主张：
  1. 下一代网络最终要解的是 TCO：电力效率与成本（CapEx）（OCR 辅助 p5）；OCI 已大规模部署 800G LPO，线性驱动接口"不引入代价，反而链路更稳定"。
  2. 1.6T 时 LPO 难以同时满足 SI 与互通要求，LRO 是当前最佳低功耗方案。
  3. 224G/lane 是 NPO/CPO 的成熟点，"现在是开始试用 CPO 的时候"；>224G 时 CPO/NPO 可能是唯一出路；同时 NPO（含 OpenCPX MSA）可缓解 CPO 缺点。
- 关键数据：
  - OCI AI 集群规模：2020 年 16,384 GPU（1×）→ 32,768（2×）→ 65,536（4×）→ 131,072 GPU（8×，2026）；支撑：Zettascale RDMA、超低延迟、高网络韧性、先进流量负载均衡 [p2]
  - 800G LPO：约 35 万条链路（LPO-LPO n=156,591；FRO-FRO n=202,042）；中位 pre-FEC BER LPO 1.1E-11 对 FRO 1.4E-11；p99 BER 5E-10 对 3E-8；至少发生一次 down transition 的链路：LPO 3.244% 对 FRO 5.681%；文字称 FRO 链路 flap 为 LRO 的 1.75 倍（原文写作 LRO，疑为 LPO 之笔误）；注意：短/中/高损耗端口需优化调参，LPO 互通数据有限 [p7]
  - 1.6T LRO：26 dB 通道，16 W 功耗（10 pJ/bit）；支持 DR4+（4 dB）和 FR4 上层链路；不同供应商与多厂 3 nm DSP 已演示互通；2 nm LRO DSP 成熟后功耗可更低；pre-FEC BER：3 厂平均 FRO 约 8.4E-13 对 LRO 约 3.7E-12（图中小字，数字略模糊）；FEC bin P50：LRO 1、FRO 1；P95：LRO 2、FRO 1 [p8]
  - CPO：功耗最多可比全重定时可插拔系统（200G/lane 代）节省 50%；理论成本效率 30%（假设量产）；误操作收发器是主要故障模式，CPO 将人排除在部署/运维之外；系统 FIT 预期高于可插拔；但当前 CPO 方案专有、供应链受限、配置不灵活（引用 Meta S. Amirzadeh OCP 2025 等）[p9, p10]
  - NPO（p11 OCR）：多厂光生态、更轻的 RMA、可后绑定光 PMD（DR/FR 和/或 flyover cable CPC，甚至 ZR 类前面板可插拔）；示例为新发布的 OpenCPX MSA；须证明可靠性与功效与焊接式 CPO 相当
  - DCI：OCI 区域内 DWDM 互连约 60 km 跨段，用 DCI 优化的相干可插拔与线路系统；400ZR → 800ZR → 1600ZR；参与 1600ZR/1600ZR+/CMIS，并发起 1.6T 相干可插拔的 MACsec 支持项目（OCR 文字）[p12]
  - 224G/lane（1.6T）：可插拔（FRO、LRO、ZR）为计划路线（POR）且已在途；224G 适合 NPO/CPO；>224G 时 CPO/NPO 或为唯一途径 [p13]
- 提到的公司/客户/产品/标准：OCI/Oracle、Meta（OCP 2025 数据）、NVIDIA 与 Broadcom（CPO 图示来源）、OpenCPX MSA、CMIS、MACsec、OIF ZR、400ZR/800ZR/1600ZR/1600ZR+、LPO/LRO/FRO、DR4+/FR4、3 nm/2 nm DSP、RDMA
- 与业界对比或记录声明（SOTA/首次/record）：约 35 万链路规模的 LPO 现网统计（大规模现网数据，非记录声明）[p7]
- 推荐配图页：p7（LPO vs FRO 现网 BER 直方图及 down-transition 比例）；p8（1.6T LRO 三厂 BER 与功耗）；p2（OCI GPU 集群 2020–2026 规模增长）

### 0920-pm-Su3-A-04-OrioleNetworks-数据中心光交换.pdf
- 讲者/机构：Oriole Networks（Director of Photonic Integration，姓名 OCR 不清，疑为"Alvallotis"类，未采信） | 题目：A Pure Photonic Network for the AI Era | 类型：产业发布
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]
- 核心主张：
  1. 计算增长速度约为网络带宽的 100 倍（过去十年），网络成为瓶颈（OCR：p2）。
  2. 用全光、无交换层（tier-less）的全连接光网络取代电分组交换（EPS）网络；OCS 的价值取决于交换时间与收发器再锁定时间之和。
  3. 同规模 32,000 GPU 集群，元件与功耗大幅下降。
- 关键数据：
  - 停机时间比较：Oriole PRISM SiP 超快交换 + 超快收发器再锁定 >90% 吞吐；自由空间开关（数十 ms）+ 标准收发器 <1%；SiP 热光开关（约 100 µs）+ 标准收发器 <1%；SiP 极快开关（<10 µs）+ 标准收发器 <1%；SiP 电光超快开关（<10 ns）+ 标准收发器 <1%——瓶颈是收发器再锁定 [p9]
  - 推理尾延迟：Oriole 曲线"有界、可预测"，EPS 可变不可预测（延迟轴 0.5 至数十~数百，单位看不清）；训练：EPS 活跃 40%/空闲 60%，Oriole 活跃 99%/空闲 1%；能耗：EPS 计算 80% + 网络 20%，Oriole 计算 48% + 网络 5%，图中标"2×"降低；标题称"延迟为 1/1000" [p10]
  - 32,000 GPU 集群参考架构 vs Oriole：网络层数 3 对 1；叶交换机 1024 对 0；脊交换机 1024 对 0；核心交换机 512 对 0；总交换机 2,560 对 0；节点收发器 32,768 对 32,768；交换机收发器 163,840 对 0；收发器总数 196,608 对 32,768；网络功耗图中标注降低 81%（参考架构含 800G/400G 收发器与叶/脊/核心交换机功耗）[p12]
  - 公司 80+ 员工，办公室：Palo Alto、Bangalore、UK（Paignton & London）（OCR）[p13]
  - 产品栈：XCCL 软件插件、Photonic NIC、XTR 收发器、无源光核心 [p6，OCR]
- 提到的公司/客户/产品/标准：Oriole PRISM/PRISM Ultra（白皮书 oriolenetworks.com/prism-ultra-whitepaper）、XCCL、Photonic NIC、XTR Transceiver；人才来源公司 logo：Arm、Ericsson、Huawei、Intel、Lumentum、Semtech、Qualcomm 等
- 与业界对比或记录声明（SOTA/首次/record）：宣称"世界首个"纯光网络（p4 OCR 残缺，仅见 "world's first"，主体不清）；可靠性、供应商数据均为公司宣称，无第三方对比
- 推荐配图页：p9（各类 OCS 交换时间 + 收发器再锁定的吞吐对比条形图）；p12（32k GPU 集群元件数与功耗 -81% 对比表）；p10（推理/训练/能耗三联图）

### 0920-pm-Su3-A-05-NVIDIA-CPO对可插拔的优势.pdf
- 讲者/机构：Daniel Kuchta，NVIDIA | 题目：The Path for Co-Packaged Optics in the AI Ecosystem | 类型：邀请报告
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]
- 核心主张：
  1. CPO（微环调制器 + TSMC COUPE 3D 堆叠硅光引擎 + 高功率高效激光 + 可拆卸光纤连接器）已量产用于 Spectrum-X Ethernet Photonics，并有 Quantum-X InfiniBand Photonics。
  2. AI 工厂规模下，CPO（约 4 pJ/bit）相对可插拔可省约 72% 收发器功耗，省下的电力可增配 GPU；网络占总功耗 6–8%，CPO 将其降到 1/5。
  3. CPO 后续演进：400 Gb/s/lane（200 GBaud PAM4）、偏振与光 BiDi 再 2×、多波长（CWDM/LWDM 2×400G、4×400G、DWDM）、Coherent-lite，需在每纤带宽、radix、总吞吐间取平衡。
- 关键数据：
  - 光网络功耗约占算力资源的 10%；传统云数据中心 10 万台服务器收发器功耗 2.3 MW，AI 工厂 10 万台服务器 40 MW；CPO 约 4 pJ/b，节省约 72% 收发器功耗 [p8]
  - "世界最先进 200G CPO"：Quantum-X（InfiniBand）与 Spectrum-X（Ethernet）集成硅光；标注 2× 吞吐、1.6× 带宽密度、63× 信号完整性、4× 更少激光器、10× 更好激光可靠性、替代 64 个可插拔收发器；这些倍数的基准对象图中未标明，需以原稿为准 [p9]
  - 微环调制器（MRM）发射机：212.5 Gbps/通道，眼图展示；16 通道在 OFC 2026 展会以 212 Gbps 连续运行 3 天，总 BER < 1E-14 [p13]
  - CPO 可插拔/插座化 vs 焊接：CPO 插座化（利于初始部署与 OSAT 返修，但增成本、面积、影响信号完整性）；焊接 CPO 信号完整性好、封装最小但返修受限（OCR，p14）
  - 未来 AI 工厂："Gigawatt 时代"，网络占总功率 6–8% → CPO 将降 5×；网络中断可累积每天 300 万美元收入损失 → CPO 将消除此项 [p16，OCR]
  - CPO 箱体组装时间短，可插拔箱体组装时间长（p11，OCR 残缺）；NVL72 with Quantum-X InfiniBand Photonics scale-out（p15 图注）
  - p3–p6 介绍 Vera Rubin 协同设计（含 Groq 3 LPX）、NVLink 第六代 scale-up、Spectrum-X 带 102.4T 交换系统与 1.6T SuperNIC（OCR，数字未开图）
- 提到的公司/客户/产品/标准：NVIDIA Vera Rubin、Groq 3 LPX、NVLink、Spectrum-X（含 Ethernet Photonics）、Quantum-X InfiniBand Photonics、BlueField-4、ConnectX、TSMC COUPE、micro-ring modulator、OFC 2026 展示
- 与业界对比或记录声明（SOTA/首次/record）：自称"World's Most Advanced 200G Co-Packaged Optics"；CPO 已进入 full production [p9, p10]
- 推荐配图页：p8（传统云 vs AI 工厂收发器功耗与 CPO 省 72%）；p13（MRM 与 212.5 Gbps 眼图，OFC 2026 3 天 BER<1E-14）；p9（CPO 六项倍数收益）；p15（CPO 未来扩展路线）

### 0920-pm-Su4-A-01-Marvell-下一代相干DSP.pdf
- 讲者/机构：Lenin Patra，Marvell（SVP Data Center Architecture） | 题目：Meeting Diverse AI Connectivity Needs: Architectural Choices for Next-Generation Pluggable Transceivers（讲稿 2026-09-20；PDF 名含"相干 DSP"但内容为可插拔架构组合） | 类型：邀请报告
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [2 Scale-across/ZR/ZR+/CL]、[4 Scale-up/in CPO/NPO/XPO]
- 核心主张：
  1. 收发器正在成为"架构组合"：TRO/NPO → PAM4 FRO/TRO → FRO/Coherent-Lite → FRO/ZR-ZR+ 相干，覆盖距离与 DSP/FEC/光学复杂度同步上升。
  2. 200G/L→400G/L 改变可插拔设计点：在约 212.5+ GBd 下电/光边界必须联合设计，主机通道成为关键限制。
  3. "AI 连接将收敛到可插拔架构组合，按延迟、功耗、覆盖、密度与互通优化"；保留可插拔性，DSP 是主力，整条链路（SerDes、电通道、DSP、FEC、光、封装、遥测）作为一个系统优化。
- 关键数据：
  - 分层：DCI/Scale-across >10 km：C 波段相干 1.6T ZR/ZR+；Scale-across 2–10 km+：O 波段 Coherent-Lite 1.6T | 3.2T，平衡功耗/延迟/成本；Scale-out 100 m–2 km：200G/L PAM4 → 400G/L PAM4；Scale-up 10 m–100 m（讲稿标 10 m~100 m）：200G/lane PAM4 → 400G/L PAM4，AOC/光收发器，低功耗低延迟 [p5]；p4 版本另列 "Slow and Wide Optics: uEmitter、uLED、uVCSEL"（OCR，p5 末）
  - 架构组合：TRO|NPO（最低延迟、最低 DSP 开销，scale-up）；PAM4 FRO|TRO DSP（覆盖+裕量、互通，scale-out 主力）；FRO|Coherent-Lite（O 波段覆盖、较低复杂度，园区/scale-across）；FRO|ZR/ZR+（DWDM 覆盖、强 DSP+FEC，DCI/scale-across）[p6]
  - 3.2T 对 scale-up/out：主机侧每 400G C2M 通道（CPC，Die escaping、TX/RX routing、OSFP 连接器）；448G 时 FRO：C2M PAM6|PAM4，光侧 PAM4；TRO：C2M PAM4，光侧 PAM4；光学 PAM4 | QAM16；FRO 用 PAM DSP | Coh-Lite DSP，TRO|NPO 用 PAM DSP [p13]
  - 400G/L 下"一阶问题"：主机电通道覆盖、封装/PCB 损耗与反射、FEC 延迟与编码增益、模块功耗与散热余量（OCR 辅助 p8）
  - 结论页：可插拔的核心价值是可维护性、互通、生态规模与供应链灵活；设计目标是"更多 Tb/s 每交换机、更低 pJ/bit，同时保持大规模可部署性"（OCR p18）[p22]
  - 未给出具体功耗/延迟数值
- 提到的公司/客户/产品/标准：Marvell、OSFP、CPC（copper flyover）、TRO/FRO/NPO、PAM4/PAM6/QAM16、Coherent-Lite、ZR/ZR+、uLED/uVCSEL/uEmitter、"OCI/scale-across" 用例（p6 图注）
- 与业界对比或记录声明（SOTA/首次/record）：无（架构性观点）
- 推荐配图页：p6（TRO/NPO 到 ZR+ 的架构组合与覆盖-复杂度图）；p4（DCI/scale-across/scale-out/scale-up 四层收发器需求分布）；p13（3.2T PAM 与 Coherent-lite 光学：400G 通道、FRO/TRO 组合表）；p22（结论）

### 0920-pm-Su4-A-02-Ciena-相干进数据中心.pdf
- 讲者/机构：Ciena（讲者姓名未在页面中出现） | 题目：Coherent Technology for Data-center Applications | 类型：邀请报告
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件]；次 [2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区]
- 核心主张：
  1. "Interconnect wars"：2026 年前线为 1–2 m（铜 vs 光）与 2–10 km（IMDD vs 相干）。
  2. 相干进数据中心的关键是低发热、低成本、高密度和"零错误"：用 2 nm CMOS、DFB 激光和光子集成实现 Coherent-Lite。
  3. 零丢包/零重传（BER < 1E-24，压缩 FEC）可免去大 ARQ 内存与延迟三倍化，改善 AI 训练。
- 关键数据：
  - 距离尺度：1 mm 铜、1 m、1 km、1000 km；铜/IMDD 光/相干三种星座与眼图示意，前线 1–2 m 与 2–10 km [p2]
  - 零重传：每个 3.2 Tb/s 链路在 20 km 需 1.3 Gb ARQ 存储；10T 参数数据集在 BER=1E-12 下会丢 160 个包；使用压缩 FEC 后 BER < 1E-24 [p5]
  - 液冷 400ZR OSFP 运行流量、冷却演进（自然对流 → 强制风冷 → 液冷）（p3–p4 仅见标题，未开图）
  - Coherent-Lite：2 nm CMOS，DFB，光子集成；示例 2×1.6T Coherent-Lite OSFP；误码 <1E-24 [p6]
  - 12.8T Coherent-Lite XPO：3.2T Coherent-Lite ASIC、双 1.6T ICR、双 1.6T MZM/驱动、双 DFB O 波段激光；功耗 <240 W（液冷 XPO 可承受 400 W）；BER <1E-24 [p7]
- 提到的公司/客户/产品/标准：Ciena、400ZR OSFP、Coherent-Lite OSFP、XPO、ARQ、Compressed FEC
- 与业界对比或记录声明（SOTA/首次/record）：展示 12.8T Coherent-Lite XPO 实物 [p7]；无明确 record 声明
- 推荐配图页：p7（12.8T Coherent-Lite XPO 内部结构及 <240 W）；p5（零重传数据：1.3 Gb ARQ、160 包、BER<1E-24）

### 0920-pm-Su4-A-03-Acacia-PAM4-DSP竞争.pdf
- 讲者/机构：Tom Williams，Acacia（Cisco 旗下）（姓名依题目页 OCR "dom Williams" 推断，未完全确定） | 题目：FRO, ERO, T/LRO, XPO, ...（副题 A vendor perspective on architectural evolution；OCR 题名残缺） | 类型：邀请报告
- 方向归属（主/次）：主 [2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区]；次 [1 相干/DCI]、[4 Scale-up/in CPO/NPO/XPO]
- 核心主张：
  1. AI 推动一切：供应链规模与管理、性能（转化为利润与更稳健链路）、质量成为光学新重点；"成本/bit 仍重要，但为 GPU 利用率优化才是成功关键指标"。
  2. Scale-across 推动相干需求，800ZR+ 是"历史上增长最快的相干技术"。
  3. 相干走向更短距离：IMDD 的色散容忍度随波特率平方下降，400G/lane 时超过 2 km 就需要相干。
- 关键数据：
  - 800ZR+ 出货 >75,000 只，Acacia 为领先供应商；图引用 Meta（OFC 2026 Exec Forum）DC-DC 同步与 GW 级集群流量增长（2026 投影最大），以及 Cignal AI 的相干代际普及曲线（横轴为引入后第 1–5 年，800ZR+ 曲线明显高于其他，第 5 年约 650k 台/年的量级；纵轴单位"Thousands"，读数为估读）[p3]
  - Top 15 云厂商 capex 与光收发器季度销售额（LightCounting 数据），纵轴数值看不清 [p2]
  - IMDD 在 200G/lane 的极限约 10 km；400G/lane 时 >2 km 需相干；IEEE 800GBASE-ER1（20 km）与 800GBASE-ER1-20（图上写 40 km 链路，文字标"支持 20 km 和 40 km 链路"）沿用 ZR 技术；1600G/lane 相干可支持 >2 km 园区 DCI；相干优势：4× 每 lane/波长容量、数字色散补偿、支持 DWDM、可少用放大器 [p5]
  - 光学架构分类（Module-centric 到 Integrated Optics）引用 A. Ghiasi 等，IEEE 802.3 400GPL Study Group，2026 年 9 月（OCR）[p6]
  - 未来路线：0–2 年：200G/lane、OSFP 为主、硅光、CPO 试点；2–5 年：400G/lane、NPO/CPO 与可插拔并存、scale-up 网络用光、Coherent-lite 园区；5–10 年：800G/lane、多数 NPO/CPO、新材料、数据中心内相干 [p9]
  - p7（OCR）：按 Switch/Rack、Campus、Metro 尺度权衡供应链多样性 vs 功耗/性能优化、前面板或内部可维护性、相干-lite 在光纤容量上的价值
- 提到的公司/客户/产品/标准：Acacia/Cisco、Meta、Cignal AI、LightCounting、IEEE 802.3（800GBASE-ER1、400GPL SG）、OIF ZR、CPO/NPO/LPO/LRO/XPO
- 与业界对比或记录声明（SOTA/首次/record）：800ZR+ 为"历史上增长最快的相干技术"；Acacia 领先，>75,000 800ZR+ 模块出货 [p3]
- 推荐配图页：p5（IMDD 到相干的速率-距离图与色散平方论证）；p9（0–2/2–5/5–10 年数据中心光学路线图）；p3（Meta 流量与 800ZR+ 普及曲线）

### 0920-pm-Su4-A-04-Nokia-相干DSP演进.pdf
- 讲者/机构：Nokia（讲者姓名未在所看页中出现；p13 引 Momtahan, Nokia, Apr 2026） | 题目：Evolution of Coherent DSP to Meet the Evolving Needs of the AI Supercycle | 类型：邀请报告（ECOC 2026 Workshop）
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件]；次 [2 Scale-across/FST/多rail/ZR/ZR+/CL/跨楼园区]
- 核心主张：
  1. Scale-across 使相干 DSP 成为 AI 工厂部件；园区光纤数量已成危机，需提高每波长速率（1.6T/λ）。
  2. 一颗芯片无法同时对机架、大厅、千公里最优：应按覆盖选引擎（Coherent-lite、ZR、ZR+），不是按峰值波特率。
  3. 选 DSP 应看功耗、散热、FEC 延迟；园区 FEC 须 50–75 ns，模块延迟约 300 ns。
- 关键数据：
  - 三域：scale-up（机架、米级，铜到光 I/O，CPO/NPO/XPO，IM-DD，纳秒，非全相干 DSP）；scale-out（大厅与园区 100 m–10 km，PAM4 可插拔至 2 km，800G–1.6T IM-DD，约 2 km 起 Coherent-lite，OCS 损耗预算在此出现）；scale-across（园区到区域 10–1000+ km，ZR/ZR+，IP over DWDM 或 thin transponder，C+L 波段，含园区边缘）[p4]
  - 市场信号（"公开市场信号，量级估计，非 Nokia 预测"）：2026 年预计 >200k 只 800ZR 类模块；800G ZR 类 2025–2029 CAGR 145%；到 2030 年 800G+1600G 占相干收入 60%；IP over DWDM 约 20 亿美元向 2029 年 50 亿美元；400ZR 已量产但不够，800ZR-plus 是 2026 年爬坡主力 [p6]
  - OIF ZR：成本/功耗优化，约 80–120 km（放大），单载波 DP-16QAM，400ZR→800ZR→1600ZR；OpenZR-plus：PCS、更强 CD、更多格式，城域/区域/部分长途，800G 可达 1700+ km；引用 Zhu ECOC 2025、Pincemin & Renais OFC 2024、Buchali JLT 2016、Cho & Winzer JLT 2019；"园区需要比 ZR 类更低功耗、比 OFEC 更低延迟，即 coherent-lite" [p7]
  - 园区 FEC 表（复用 800G 10 km coherent-lite 的 BCH 引擎，目标延迟 ≤约 75 ns）：800G 10 km BCH(126,110)：247.3 GBd、49–55 ns、FEC RSNR 13.7 dB、模块功耗 +1.5–3%；Compressed FEC：239.1 GBd、70 ns、13.8 dB、0%（参考）；Braided code：226.7 GBd、70–72 ns、14.3 dB、+1.5–3%；"不要在 10 km AI 链路上用 OFEC" [p12]
  - 1.6T 已分叉：1600ZR 单载波约 236 GBd DP-16QAM + OFEC，约 300 GHz 槽，80–120 km DCI；1600ZR-plus 双子载波，总 252 GBd（2×约 126 GBd），PCS-16QAM，仍一个波长，至约 1000 km，复用 800G 模拟器件 [p13]
- 提到的公司/客户/产品/标准：Nokia、OIF ZR、OpenZR-plus、OFEC、BCH(126,110)、Compressed FEC、Braided code、coherent-lite、IPoDWDM、OCS
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；市场数据来自公开信号 [p6]
- 推荐配图页：p12（园区 FEC 三方案波特率-延迟-RSNR-功耗表）；p4（三域划分）；p13（1600ZR 与 1600ZR-plus 双架构）；p6（800ZR 市场信号）

### 0920-pm-Su4-A-05-NICT-光域处理替代DSP.pdf
- 讲者/机构：Yuki Yoshida、Paikun Zhu、Ken-ichi Kitayama、Bahram Jalali、Satoshi Shinada；NICT（Japan）、Hamamatsu Photonics 中央研究所、UCLA | 题目：Can Photonic Signal Processing Simplify DSP?: Breaking the Fiber Dispersion Barrier in IM/DD | 类型：邀请报告
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件]
- 核心主张：
  1. 仅几 ps/nm 的色散对 >1.6T（200 Gbaud/lane）IM/DD 就已关键；对色散补偿，IM/DD 的 DSP 与相干 DSP 相比"根本上没有竞争力"。
  2. 如果 IM/DD 不能突破信道零点，Coherent-lite 将主导 2 km 以上。
  3. 应严肃研究面向 IM/DD 的光域/光电域均衡，复杂度远低于模拟相干光学（ACO）：如 1 抽头光延迟线、成对传输（pairwise transmission）。
- 关键数据：
  - 拓扑图：400G/lane（约 200 GBd）IM-DD PAM4/PAM6 与 Coherent-Lite（约 260 GBd+，O 波段，16QAM）、数字相干 ZR/ZR+（C 波段）并列；800G/1.6T/3.2T 各速率列出 IM-DD PAM4（100G/lane 50 GBd 等）与相干（约 64/130/260 GBd）对应关系，覆盖 scale-up/scale-out/scale-across（OCR，未开图 p2）
  - O 波段色散：基于 ITU-T G.652.D，零色散波长均值 1312 nm（标准差 2 nm），斜率均值 0.086 ps/(nm²·km)（标准差 0.0015），分段长度 2.5 km；1260–1360 nm 范围 20 km 时累积色散约 ±80–100 ps/nm；1331 nm 处示例 2/5/10/20 km 总色散分布；色散代价 = D×L×BW²，例：16 ps/nm×(50 GHz)² = 2 ps/nm×(200 GHz)² [p3]
  - 224 Gbaud、2 km，判据 <20 抽头且 <4 dB SNR 代价：IM/DD FFE 仅约 45% 波段可用，FFE+1 抽头 DFE 约 70%；相干 FFE 抽头很少（<5）、几乎全波段可用 [p6]
  - 可用带宽随距离（20-tap EQ、4-dB 代价）：O 波段可用谱 2 km 后 <45%，20 km 后 <5%；相干 FFE 在约 15 km 内保持约 100 nm，20 km 处约 77 nm；Broadcom J. Johnson（ITU-T/IEEE，2026 年 7 月）报告更严重结果（2 km 时 <10%）[p9]
  - 1 抽头光延迟线：低 DSP 复杂度纪录（C 波段 100 Gbaud，80/100 km，全 C 波段 WDM 工作）；BiDi 操作（P. Zhu et al., ECOC'26, We3-E2）；图注称"约 100 km @224 Gbaud，即使在 O 波段边缘" [p12]
  - 成对传输（空时编码，跨多 lane）：适用条件为衰落抑制增益大于复用与 O-E 编码的 SNR 代价；已在光纤束（OFC 2025）、多芯光纤 MCF（ECOC 2025，标 3 与 6 Tb/s·km 曲线）、WDM（OFC 2026）上验证；光纤束图中 BER 在 10–40 km 处成对方案低于传统 OOK/PAM4（纵轴 1E-2~1E-5，具体值看不清）[p14]
- 提到的公司/客户/产品/标准：NICT、Hamamatsu、UCLA；ITU-T G.652.D；Broadcom（J. Johnson 数据）；IEEE 802.3df；OIF 800ZR/1.6T ZR；相关文献 P. Zhu OFC'24/JOCN 2024/OFC'25/ECOC'25/OFC'26/ECOC'26 We3-E2；Photonic reservoir、negative chirp（MRM）、diversity reception 等技术路线（p11 OCR/缩略图）
- 与业界对比或记录声明（SOTA/首次/record）：C 波段 100 Gbaud 80/100 km "记录级低 DSP 复杂度"（作者自述，引 OFC'24）[p12]
- 推荐配图页：p9（IM/DD 与相干的可用带宽 vs 距离曲线，核心结论图）；p6（224 Gbaud 2 km 下抽头数-SNR 代价-波长）；p12（1 抽头光延迟线原理与三项验证）；p14（成对传输三类验证）

## 本批小结

1. Scale-up 互连选择从"单一 CPO 叙事"转向"按系统结果比较"：OpenAI 强调以请求延迟和单请求能耗比较铜/可插拔/NPO/CPO，并把故障恢复计入性能（OpenAI）；NVIDIA 给出 CPO 已量产、约 4 pJ/b、省约 72% 收发器功耗、16 通道 212 Gbps 运行 3 天 BER<1E-14（NVIDIA）；Oracle 认为 224G 是试用 CPO 的时机，NPO/OpenCPX 可缓解 CPO 的专有与返修问题（Oracle）；Marvell 强调保留可插拔性、TRO/NPO 用于 scale-up（Marvell）。
2. 线性/半线性方案有现网证据：Oracle 在约 35 万条 800G 链路上统计，LPO 中位 pre-FEC BER 1.1E-11 对 FRO 1.4E-11，p99 5E-10 对 3E-8，down-transition 链路 3.244% 对 5.681%；到 1.6T 时改用 LRO（26 dB 通道 16 W、10 pJ/bit），且需多厂 3 nm DSP 互通（Oracle、Marvell）。
3. 400G/lane（212.5+ GBd）使电/光边界和主机通道成为一阶问题，色散决定 IM/DD 与相干的分界：NICT 定量给出 O 波段可用谱 2 km 后 <45%、20 km 后 <5%，Acacia 称 400G/lane 时 >2 km 需相干、200G/lane IMDD 极限约 10 km，Nokia 把 Coherent-lite 划在约 2 km 起（NICT、Acacia、Nokia、Marvell）。
4. Coherent-Lite 与 ZR/ZR+ 分工趋于明确：Nokia 的园区 FEC 表（BCH、Compressed、Braided，49–72 ns）与 1600ZR/1600ZR-plus 双架构，Ciena 的 12.8T Coherent-Lite XPO（<240 W，BER<1E-24，压缩 FEC 零重传），Marvell 的 2–10 km+ 1.6T/3.2T Coherent-Lite 层（Nokia、Ciena、Marvell、Acacia）。
5. Scale-across 市场数据集中：Acacia 称 >75,000 只 800ZR+ 出货、"历史上增长最快的相干技术"；Nokia 引用 2026 年 >200k 只 800ZR 类、2025–2029 CAGR 145%；LightCounting 预测 2026 年硅光首次超收发器市场 50%，并指出 CPO 使对准与测试转移到 OSAT（Acacia、Nokia、LightCounting）。
6. 全光/OCS 路线的瓶颈是收发器再锁定而非开关本身：Oriole 图示即使 <10 ns 电光开关配标准收发器也 <1% 吞吐，只有超快再锁定才能达到 >90%；其 32k GPU 案例宣称网络层 3→1、交换机 2,560→0、收发器 196,608→32,768、功耗 -81%（均为公司宣称）（Oriole）。
