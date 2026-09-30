---
title: "B01 · DAY1 · A1-Su1-Su2-AI数据中心光源"
tags:
  - ECOC2026
  - DAY1
---

# B01 笔记：ECOC 2026 Sunday Workshop「Light sources for next-generation optical communication systems for AI datacenters」（Malaga，2026-09-20）

说明：页码 pN 均指 PDF 页码（非幻灯片自带页码）。数值均来自看图核对；OCR 有误处已按图纠正。Oracle（Su1-A-02）为主分析师已做篇目，跳过。

### 0920-am-Su1-A-03-华为-光源集成需求.pdf
- 讲者/机构：Zhang, Shiyong / Huawei | 题目：Laser technologies for scale-up optical interconnects in AI supernodes | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 光源]
- 核心主张：
  1. Scale-up 域从单机柜（<100 XPU）扩展到多机柜（100s~1000s XPU，铜+光，光最远约100 m），FOM = (Tbps/mm)/((pJ/bit)*(ns)) * reach(m) * MTTF [p2]
  2. VCSEL LPO 已用于 Atlas 950 SuperPoD；NPO 形态的高密度光引擎是下一代选项；7.2T Hi-ONE NPO 采用板载免光纤（fiber-free）激光器 [p8 结论页，看图核实]
  3. 未来需要 laser-on-PIC 进一步集成；量子点适合热环境恶劣场景；慢而宽（slow-and-wide）能效承诺需要持续创新 [p8]
- 关键数据：
  - Atlas 900（2025）：384 NPU，6912x 400G SR8 VCSEL oDSP；Atlas 950（2026）：64~8196 NPU，4096x 800G SR8 VCSEL LPO（对应1024 NPU）；页面标注 Latency 降 90%、Power 降 60%（基线未明示，按页面原样）；光链路由 UnifiedBus 链路级重传 + 2x2 模块级交叉备份保护 [p3]
  - 3.2T NPO 引擎 demo：4x（8x100G/lane）VCSEL 阵列，50 m OM4，13.7 W，约 4.3 pJ/bit；商用基线 850 nm 100G PAM4；1060 nm 延伸 reach（IEEE P802.3ds）；为 6.4T/12.8T（200G PAM4 | 50G NRZ）留余量；图中 Fiber EMB vs Reach @212 Gbps/lane（来源 Lighthera 2026）[p4]
  - InP CW 激光器（UHP）：WPE>30% 直到 500 mW，RIN<-150 dB/Hz，WPE 曲线条件 50 °C [p5]
  - 板载内置激光器（7.2T Hi-ONE NPO，36x224G）：无PM光纤、AlQ MQW、FIT<1（1:1备份）[p5]
  - QD DFB（片上潜力）：100 °C 下 200 mW@580 mA；GaAs，2 mm；11x23°；>-25 dB 反射容忍；LI 曲线含 25/80/100 °C [p5]
  - 多波长（slow-and-wide）：O波段 8–16 λ、200–400 GHz 间隔、平坦低RIN；模块WPE 需由<10% 提升到>15%；图示 50G NRZ w/ TEC 下激光器贡献能耗 vs 光纤内光功率（1–11 dBm）：10% WPE 与 18% WPE 两条曲线，10% WPE 曲线在约 11 dBm 处约 4.5 pJ/bit，18% 约 2.4 pJ/bit（读图估值）；200 GHz 间隔 QD 梳状激光器 53G NRZ：ER=4.2 dB，TECQ=2.84 dB [p6]
  - 激光器集成：第一代倒装集成（Huawei 自有），免隔离器、已知良品裸片（KGD），已出货 >3M（看图核实）；下一代参照 TSMC COUPE 进一步缩小尺寸，热/可靠性代价靠高效散热、冗余与量子点缓解 [p7]
- 提到的公司/客户/产品/标准：Huawei Atlas 900 / Atlas 950 SuperPoD、UnifiedBus、Hi-ONE NPO、TSMC COUPE、IEEE P802.3ds、Lighthera（数据来源）
- 与业界对比或记录声明：无明确 SOTA/record 声明；强调 VCSEL LPO 已在超节点规模部署（Atlas 950）[p3]
- 推荐配图页：p3（Atlas 900→950 两代 VCSEL 光互连及 Latency/Power 指标）；p4（3.2T VCSEL NPO 引擎及 EMB-reach 曲线）；p5（三类CW激光器：InP CW、板载、QD DFB）

### 0920-am-Su1-A-04-AMD-硅光片上光源.pdf
- 讲者/机构：Haisheng Rong（Sr. Fellow）/ AMD | 题目：Lasers for Co-packaged Optics（Light sources for next-generation optical communication systems for AI datacenters） | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 光源]
- 核心主张：
  1. Scale-up 需要 CPO：AI 算力增长要求 CPO 提供能效、带宽与可扩展性 [p13]
  2. 激光器是关键部件，需持续降本并提升性能与可扩展性 [p13]
  3. 标准使能生态；进展需要封装、集成、材料、工艺、器件、电路、系统的协同设计 [p13]
- 关键数据：
  - 能效：可插拔 >15 pJ/bit；OBO ~10–15 pJ/bit；CPO ~5 pJ/bit，即 CPO 约 3x 能效提升 [p4]
  - OCI-MSA ELSFP 关键要求：绝对波长精度 ±0.2 nm，通道间隔 400 GHz，激光 RIN -144 dB/Hz，线宽 <1 MHz，激光功率/λ 与模块WPE 为“实现自定”（IS），ELSFP 壳温 40–60 °C；蓝/红两个波段起始波长 1308.00 nm / 1327.69 nm，各4条线 [p8]
  - 备选光源方案：分立高功率 InP DFB（主流方案，优点已有量产验证，挑战为成本与可扩展性，图示4条TEC上的激光器）；频率梳（波长间隔最准，但功率均匀性与效率待解）；多波长激光器（间隔/波长数可控，但间隔精度与通道均匀性待解）；异质集成激光器阵列（间隔与功率均匀性好，功率扩展是挑战）[p9]
  - Scale-up 带宽现状：200 Gbps/方向，每光纤2方向（BiDi），4波长x50 Gbps/方向；扩展路径：4λ→8、16、32；50G→100、200、400；单偏振→双偏振；NRZ→PAM/QAM-n；挑战：功耗 <5 pJ/bit 并降低成本 [p10]
  - p12：GaAs QD 激光器（高温、免隔离器）与异质集成路线被并列为可扩展方案（文字信息，无具体数据）
- 提到的公司/客户/产品/标准：AMD “Helios” 开放机架平台（p2，Yotta scale）、OCI-MSA、ELSFP、UCIe（p5）
- 与业界对比或记录声明：无 SOTA/record 声明
- 推荐配图页：p4（Pluggable/OBO/CPO 能效对比 15/10–15/5 pJ/bit）；p8（OCI-MSA ELSFP 波长图与要求）；p9（四类 ELSFP 光源方案权衡）

### 0920-am-Su1-A-05-Columbia-片上光源与系统.pdf
- 讲者/机构：Keren Bergman / Columbia University（p10 含 Xscape Photonics 产品页） | 题目：AI System Drivers for Laser Sources | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 光源（Kerr 梳/DWDM）]
- 核心主张：
  1. 加速器系统存在层级网络带宽锥形（128x bandwidth taper across system），需将光子学放进计算 socket（embedded photonics）以“拉平”通信锥形 [p2–p4]
  2. 波长域大规模并行（梳状光源 + DWDM）可实现 multi-Tbps 单链路、<1 pJ/b，且带宽与能耗/比特与距离无关 [p5]
  3. “更多并行波长 + 中等速率”（Wide and Slow）在带宽密度x能效上比“窄而快”有 ~100x 优势 [p9]
- 关键数据：
  - 网络层级（看图核实）：GPU-HBM4 25.6 TBps；GPU-CPU (C2C) 900 GBps；片内 <50 fJ/bit；NVLink 6.0 3.6 TBps/GPU，最多 256 GPU 同一 NVLink 域，约 5 pJ/bit；NIC 1.6 Tbps/GPU；scale-out 可插拔光模块 >20 pJ/bit；系统内 128× 带宽锥度 [p2–p3]
  - 图：带宽密度x能效 [(Gbps/mm)/(pJ/b)] vs 最大链路距离，标注 UCIe 1.0-A/1.0-S、NVLink 6.0、Avicena LightBundle、Ayar TeraPHY、可插拔光学；Embedded Photonics 位于右上区域（目标区）[p4]
  - Kerr 梳链路（Nature Photonics 2023, Rizzo et al.）：multi-Tbps 单链路，<1 pJ/b [p5]
  - 高功率灵活FSR Kerr 梳（CLEO 2026 Highlight Talk，Cullen et al.），泵浦功率 375 mW：300 GHz 梳转换效率 63.6%，#Ch>5 dBm=25，#Ch>-3 dBm=36，3 dB 内通道数 19；200 GHz：48.1%，17，48，27；100 GHz：33.6%，—，73，57；眼图：300 GHz 梳 32 Gb/s，200 GHz 梳 24 Gb/s，100 GHz 梳 16 Gb/s [p8]
  - 图：BW密度x能效 vs 每 Tbps 通道数（4–128），Columbia 梳驱动 DWDM（IEEE T-CPMT ’24、Nat. Photon. ’23、Nat. Photon. ’25）相对商用（NVIDIA GTC ’25、NVIDIA ISSCC ’26、Ranovus、Intel、Ayar Labs）约 100x，图中商用点聚集在约 10^1–10^2 量级 [p9]
  - Xscape Photonics CombX：EAGLEX 16（CombX Gen1 TV，16λ，客户架构验证载体，2025Q4 起送样）；FALCONX 8（CombX Gen1 产品，8λ，首个产品为可插拔ELSFP形态（OCI-MSA标识），原型送样 2026Q2，量产爬坡 2027Q4）；FALCONX 16（CombX Gen2 TV，16λ，功耗降至 Gen1 的 1/2，2026Q4 送样）[p10]
  - 3D 光子学论文引用（Daudlin et al., Nature Photonics 2025年3月）：EIC/PIC 3D 集成 [p6]
- 提到的公司/客户/产品/标准：NVIDIA（NVLink 6.0、GTC ’25、ISSCC ’26）、Ayar Labs（TeraPHY）、Avicena（LightBundle）、Ranovus、Intel、UCIe、DARPA PIPES（图源 Gordon Keeler）、Xscape Photonics、OCI-MSA（AMD/Broadcom/Meta/Microsoft/NVIDIA/OpenAI 标识）
- 与业界对比或记录声明：图示“比商用 ~100x BW密度x能效” [p9]（作者研究点与商用点对比）
- 推荐配图页：p9（窄而快 vs 宽而慢，梳驱动DWDM的 100x）；p8（Kerr 梳光谱、眼图与转换效率表）；p10（Xscape CombX 三代产品路线及送样时间）

### 0920-am-Su2-A-01-UBC-SiEPIC-硅光平台光源.pdf
- 讲者/机构：Lukas Chrostowski / Dream Photonics（CEO），UBC/SiEPIC（休假教授） | 题目：Hybrid laser integration using 3D-printed optics（首页副题：Datacenters will need billions of lasers. Connecting lasers is the bottleneck.） | 类型：Workshop（邀请报告，含创业公司产品思路）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [4 CPO/NPO]
- 核心主张：
  1. 数据中心需要数十亿颗激光器，连接（耦合/封装）激光器是制造瓶颈 [p1、p8]
  2. 3D 打印光学互连（在放置后按实测位置打印透镜）把精度从元件放置转移到光连接上，可替代串行主动对准 [p8、p11、p18]
  3. 结论：存在多种设计选择（片外/片上激光、异质/混合/单片、晶圆级/子组件、QW vs QD、隔离器/优化/电路反馈），标准化将有助收敛 [p19]
- 关键数据：
  - Open CPX 1.0 规范（2026-09-16）：6.4/7.2 Tbps，32/36 lane，最高 212.5 Gbps/lane；两种激光选项：内置 ILM、外置 ELM（ELSFP）；通用 socket（机械/电/光/热/CMIS）；CPX 模块不要求热插拔 [p4]
  - OCI v1.0（200G OCI Line Interface Spec，2026-03-11）：每方向4波长，Group A 1308.00/1310.28/1312.58/1314.88 nm，Group B 1327.69/1330.05/1332.41/1334.78 nm，相邻间隔 2.28–2.37 nm，53.125 Gbaud NRZ，单 BiDi 光纤共8波长 [p5]
  - 成本结构：封装/组装/测试约占 80%，芯片约 20%（看图核实，饼图标注）[p7]
  - 串行对准：单次对准+胶固化 5–10 分钟；8通道 40–80 分钟 [p8]
  - IMEC 晶圆级混合集成示例：300 mm Si 晶圆、倒装焊、商用 InP DFB；X 方向偏差均值 26 nm、3σ=254 nm（N=51）；Y 方向均值 13 nm、3σ=284 nm（Marinis et al., IEEE 2023，亚300 nm对准）[p10]
  - Dream Photonics 方案目标：5 M 连接/工具吞吐；性能耦合损耗 <1.2 dB；低背反；晶圆级混合或子组件；图示 kink-free LI 曲线与 SMSR 谱（波长约 1310 nm）[p18]
  - Intel 经验教训：混合集成在销量达到阈值前更优；过早上异质集成有 >\$100M 研发无法回收的风险，工艺昂贵、毛利薄（OCR，页p9文字清晰）
  - InP QW vs GaAs QD 对比：InP 为 4 英寸易碎衬底、对反射敏感需隔离器、存在供应链问题；GaAs QD 用 6 英寸衬底、100°C+ 热稳定、天然反射免疫、可单/多波长并可在硅衬底上生长；受控自注入可稳定 DFB 激光器，无磁光隔离器（O. Esmaeeli, Nature Photonics, 2026年3月）[p14–p15，看图核实]
- 提到的公司/客户/产品/标准：Open CPX MSA、OCI-MSA / 200G OCI Line Interface Specification、ELSFP、IMEC、Intel、CMIS、Dream Photonics、SiEPIC
- 与业界对比或记录声明：无 SOTA 声明；引用 IMEC 亚300 nm 倒装对准精度 [p10]
- 推荐配图页：p4（Open CPX 1.0 规范要点）；p5（OCI v1.0 两组各4波长的具体波长）；p8（激光耦合串行对准瓶颈）

### 0920-am-Su2-A-02-Quintessent-量子点梳状光源.pdf
- 讲者/机构：Alan Liu（CEO）/ Quintessent | 题目：O-Band Lasers Without InP | 类型：Workshop（产业发布/技术报告）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [4 CPO/NPO]
- 核心主张：
  1. GaAs 量子点增益晶圆键合到硅光，无 InP、无再生长、无电子束、无解理面，可晶圆级测试与 KGD [p6]
  2. 同一 QD-on-Si 工艺可做单波长 QD DFB 与单腔单偏置多波长梳状激光器 [p8]
  3. QD DFB 对光反馈不敏感，耦合到 PIC 时可能可免隔离器 [p14]
- 关键数据：
  - QD 外延：可在最大 6 英寸 GaAs 衬底量产；已生长 750+ 片；来自 3 个 epi lot 约 3000 颗激光器（946 / 1019 / 988 颗），未优化 WPE 在每个 lot 均集中在 25–30% [p4]
  - 单腔单偏置8λ梳：单颗硅芯片 3 x 0.25 mm，无反馈/控制，单电流源；50 mA 偏置下，35–60 °C 范围各线随温度同向漂移（约 1292–1301 nm 区间）；归一化谱中8线功率均匀度 2.0 dB [p9]
  - 梳随偏置稳定：峰值 WPE >20%（图中 WPE 轴至32%）；硅波导内梳状激光器单独输出 >80 mW 总功率；增益偏置至约 200 mA [p11]
  - 200 mW 8λ 梳光源（>25 mW/λ）：加 booster SOA，30 °C，2 dB 均匀度，峰值约 25 mW；带外 SMSR 有待耦合损耗降低与 SOA 优化改善 [p12]
  - 单波长 DFB+SOA 阵列（8x200 GHz，λ1 至 λ1+1400 GHz）：SMSR >55 dB，无跳模，硅波导内单侧功率最高 85 mW，间隔精确，无SOA时背反射容忍度高，未针对功率/效率优化（SOA 偏置 150 mA）[p13]
  - 反馈测试：5 个不同波长 DFB+SOA，SOA 偏于透明点（无增益）；反馈达 -15 dB 时 RIN 保持约 -150 dBc/Hz（反馈约 -10 dB 附近 RIN 上升到约 -125 dBc/Hz）[p14]
  - p7 展示 QD-on-Si 晶圆、封装带尾纤梳状激光器模块及客户送样原型模块（照片）
- 提到的公司/客户/产品/标准：Quintessent；“customer sampling”未点名客户；CPO ELS 与 scale-up/out 收发机（p3）
- 与业界对比或记录声明：无明确 record；“no InP” 定位；自称“750+ wafers grown” [p4]
- 推荐配图页：p9（单腔单偏置8λ梳：波长-温度与谱）；p12（200 mW 8λ 梳 + booster SOA）；p14（QD DFB 反馈 RIN 稳定至 -15 dB）

### 0920-am-Su2-A-03-PhotonBridge-集成激光器.pdf
- 讲者/机构：Rui Santos（CTO）/ Photon Bridge | 题目：High-Power Lasers on Silicon: Scalable Multi-Wavelength Light Sources for CPO | 类型：Workshop（产业发布/技术报告）
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 光源]
- 核心主张：
  1. CPO 需要来自单一集成光源的多路、高功率、间隔精确的波长；外置光源便于维护、降低 TCO [p3–p4]
  2. 悬臂式（cantilever）InP-on-SOI 耦合：有源用任意 III-V 外延，无源用厚 SOI 承受高功率 [p5]
  3. 8x8λ ELS 单芯片（32 颗 DFB + AWG MUX）已出片；高功率 DWDM 光源 2027年Q1 送样 [p6、p10]
- 关键数据：
  - CPO 使电通道损耗由 20 dB 降到 6 dB，并降低功耗；外置光源便于维护、降低 TCO（看图核实，p3）
  - ELS 要求：每色 ≥15 dBm；目标配置：8λ x 8 光纤（200 GHz 间隔）、2x4λ（OCI MSA，双向）、2x8λ（200 GHz 间隔）[p4]
  - 无源平台：厚 SOI 可处理 >1 W 光功率，1200 nm 至 >4000 nm 透明，高阻（未掺杂）支持 >110 GHz 互连；有源：InP，1200–2000 nm；热匹配、对准容差大、10x 更大 CD、i-line 无需 EUV（看图核实，p5）
  - 8λ InP DFB 阵列：200 GHz 间隔，单面最高 50 mW；LI 曲线在 25/50/65 °C（200 mA 时约 51/38/28 mW，读图估值）[p7]
  - 片上 AWG：8通道，设计间隔 200 GHz，实测平均通道间隔 197.4 GHz（SD 23.2 GHz），设计与测量中心波长偏差 70 GHz，平均 1 dB 带宽 115.8 GHz [p8]
  - 晶圆级结果：32 颗 DFB 带 64 输出耦合到 SOI；8色输出通道偏差在 ±27 GHz 内（rms 18–19 GHz）；所有 DFB 均在 AWG 通带内 [p9]
  - 产品目标：对齐 OCI MSA；>35 mW/色/光纤；可扩展 8/16/32 色；领先 InP 代工产能到位并可扩展多家；分布式激光架构使激光功率密度需求低 >2x；产品名 Palette-1 TOSA（DWDM 光纤输出），2027Q1 送样 [p10]
- 提到的公司/客户/产品/标准：OCI MSA、Palette-1 TOSA、InP foundry（未点名）
- 与业界对比或记录声明：“First chips out of fab”（单芯片 8×8λ ELS：32 个 DFB 激光器阵列 + AWG MUX，每纤 8 波长、每芯片 8 纤）[p6，看图核实]
- 推荐配图页：p9（32 DFB 晶圆级 8色输出，±27 GHz）；p8（AWG 实测通道与 197.4 GHz 间隔）；p10（高功率 DWDM 光源规格与送样时间）

### 0920-am-Su2-A-04-NTT-薄膜激光器.pdf
- 讲者/机构：Yoshiho Maeda, Tatsurou Hiraki, Takuma Aihara, Takuro Fujii, Tomonari Sato, Shinji Matsuo / NTT Device Technology Labs | 题目：Membrane Lasers and Modulators on Si Platform for AI datacenters | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [4 CPO/NPO]
- 核心主张：
  1. 薄膜 InP 器件（激光器/SOA/EAM/PD）与硅光天然兼容，可实现低能耗（激光 <1 pJ/bit，几 mA 电流）、高速 EAM（>100 GHz）、低损耗波导耦合 [p3]
  2. 器件概念：用集成“激光器+调制器+光放大器”取代高功率 ELS+分路器，消除耦合/分路损耗与 PMF，用 SOA 补偿损耗 [p5]
  3. 慢而宽（DML 阵列）与快而窄（EML 阵列）两条路线均已演示；技术成熟度目前 Level 3–5，无代工厂可用 [p7、p10、p14]
- 关键数据：
  - 链路功率预算对比（目标 0 dBm 输出）：ELS+分路：ELSFP +15.5 dBm，光纤损耗 -1.5 dB，分路 -9.0 dB，EAM -3.5 dB，MUX -1.5 dB；集成方案：薄膜LD -2.5 dBm，耦合 -0.5 dB，EAM -3.5 dB，SOA 增益 +8.0 dB，MUX -1.5 dB [p5]
  - 16通道薄膜 DML 阵列（SiO2/Si 衬底，1.11 mm x 2.75 mm）：Ith <1.3 mA，Pmax 约4 mW（片上），波长均匀性 <±0.2 nm，SMSR >50 dB，平均 f3dB 25.7 GHz（室温），能耗 0.33–0.65 pJ/bit，岸线密度约 1.6 Tbps/mm；56 GBaud PAM4（112 Gbps），室温，2 km 传输 [p7]
  - 4通道 x 400 Gbps PAM4 薄膜 EML 阵列（O 波段，55 °C，OFC 2026 PDP Th4A.1）：EAM 100 μm、激光 300 μm；消光比 3.8 dB/V（0–1 V 摆幅，55 °C）；3 dB 带宽 >100 GHz；驱动 0.5–1.0 V 摆幅；PIC 尺寸 2.0 mm x 0.5 mm [p10]
  - 55 °C 演示：400 Gbps PAM4 各通道 ER=3.5/3.6/3.0/3.3 dB；448 Gbps PAM4 各通道 ER=3.0/3.2/2.8/2.7 dB；面密度 1.6 Tbps/mm²，岸线密度 3.2 Tbps/mm，激光能耗 0.12 pJ/bit [p11]
  - 集成路线：晶圆级直接键合（目前至4英寸，随市场增长可到 6–12 英寸）；芯片级微转印（MTP，4英寸 InP 转到 8–12 英寸 SOI，对准目标 ΔX,Y ±0.2 μm，Δθ 约 0.02°）[p6，看图核实]
  - 汇总表（今天 / +5 年）：直接键合 2–3 英寸 MTP / 4–6 英寸 MTP；KGD：TBD / 芯片级 KGD（MTP）；功率/λ：+3~+13 dBm（CW）/ch / 增加通道数（2D 阵列、WDM）；可靠性 TBD；技术就绪度 Level 3-5（PoC 至部分规模原型）；封装：片上 PIC、绝热耦合；SMSR >40–50 dB（典型），RIN 取决于腔设计；良率/成本/代工：TBD，代工可用性：No [p14]
  - ECOC 2026 NTT 相关论文：We1-C2 薄膜 EAM 低偏振相关，PDL<1 dB，PAM4 256/300 Gbps（TE/TM/混合，ER 3.0–3.4 与 3.2–3.7 dB）；Tu3-D1 差分驱动薄膜 EAM 子组件 400 Gbps PAM4，1.0 V 差分摆幅，3 dB EO 带宽 >110 GHz；Tu3-D4 EA-DFB 光芯片链路 1.55 pJ/bit @ 64 Gbit/s PAM4 [p15]
  - SOA（p12，看图核实）：微转印 SOA，SOA 长 300 μm，有源区 0.6 x 0.1 μm²，限制因子 Γ 可由下层波导调控（10–50%）；覆盖 O/C/L 波段（视有源材料）；亦可微转印到 TFLN 波导上
- 提到的公司/客户/产品/标准：NTT；引用 Hiraki/Nishi/Fujii/Maeda 等 JLT/Optica 论文；ELSFP
- 与业界对比或记录声明：4ch x 400G PAM4（含448G）薄膜 EML 阵列为 OFC2026 PDP 成果 [p10–p11]
- 推荐配图页：p5（ELS+分路器 vs 集成 LD+MOD+SOA 的功率预算）；p11（4ch x 400/448G PAM4 眼图与密度指标）；p14（现状/5年汇总表）

### 0920-am-Su2-A-05-Chalmers-克尔光频梳.pdf
- 讲者/机构：Victor Torres-Company（合作者 Oskar Helgason, Marcello Girardi, Israel Rebolledo-Salgado, Liron Gantz（Nvidia））/ Chalmers University of Technology（也隶属 Solinide Photonics AB） | 题目：Chip-scale microcombs for short-reach interconnects | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [4 CPO/NPO]
- 核心主张：
  1. 窄而快 vs 宽而慢两条路线竞争；宽而慢（多 λ、低每通道速率）可用 CMOS 驱动/TIA、硅光环调制器、无需 FEC/DSP，但需要多波长光源 [p3]
  2. 多波长光源要求：每通道功率 >1 mW、平坦包络、WPE>10%、可量产、O 波段、间隔 100–200 GHz、合适 RIN [p4]
  3. 光子分子微梳（photonic molecule microcomb）效率高、可晶圆量产、通道数“几乎无限”，是一路有前景的光源 [p8、p9、p12]
- 关键数据：
  - 光源对比：激光阵列（约10 mW/λ，WPE>10%，均匀性好，但需要多个控制器，2–3 dB 损耗，>32 通道受放大带宽限制）；锁模激光器 MLL（>1 mW/ch，一个控制器）；微梳（1–2 mW/ch，WPE≈10%，一个控制器，与硅光兼容，通道数不受限）[p5]
  - O 波段进展：半导体锁模激光器（Rautert et al., OFC Th4D.3 2025, Innolume/Axalume）：>1 mW/线，100 GHz 间隔 24 条线，2段 MLL，InAs/GaAs QD；O 波段微梳（Helgason et al., OFC Th2A.13 2026, Solinide Photonics）：75 mW 泵浦，200 GHz 间隔，28 条线 >1 mW，效率 69%（页面标注约70%光学转换效率），Si3N4 光子分子 + 放大 DFB 泵浦 [p7]
  - 超高效微梳（Helgason et al., Nature Photon. 2023）：100 GHz 梳，55% 转换效率，泵浦 8 mW，波段约 1480–1640 nm [p8]
  - 晶圆可扩展性（Girardi et al., Opt. Express 2025）：1450–1675 nm 波长范围，共 9283 个谐振；转换效率分布集中在约 50–60%（读图），少量器件低至约 20%；晶圆尺度约 1 cm 标尺图 [p9]
  - 长期稳定性：24/7 运行孤子微梳，封装模块带光纤阵列，主动反馈稳定功率设定点，30 小时重复频率/泵浦频率漂移平稳；产品化见 Solinide Photonics（OFC2026 展示）（Rebolledo-Salgado et al., Opt. Lett. 49, 2325, 2024）[p10–p11，看图核实]
  - Solinide 建模路线图（标注 Modelled Roadmap）：75 mW 泵浦、200G 间隔、28 条 >1 mW、69% 效率；150 mW 泵浦、200G 间隔、64 条 >1 mW、>70% 效率；300 mW 泵浦、100G 间隔、128 条 >1 mW、>70% 效率（波长范围约 1200–1400 nm）[p12]
- 提到的公司/客户/产品/标准：Solinide Photonics、Innolume/Axalume、Nvidia（合作者）、AMICA（欧洲项目标识）、European Innovation Council
- 与业界对比或记录声明：p7 将半导体 MLL 与 O 波段微梳并列比较；微梳效率 69%–70% 为自报指标，其中 64/128 线为建模路线图而非实测 [p12]
- 推荐配图页：p7（O 波段 MLL 与微梳并列，200G/28线/69%效率）；p12（Modelled roadmap：75/150/300 mW 泵浦线数）；p9（晶圆级转换效率均匀性）

### 0920-am-Su2-A-06-IIIVLab-磷化铟异质集成光源.pdf
- 讲者/机构：Claire Besancon / III-V Lab（Nokia Bell Labs、Thales Research and Technology、CEA LETI 联合实验室），法国 | 题目：InPoSi Integration Platform for Laser Sources: Achievements and Perspectives | 类型：Workshop（邀请报告）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]；次 [4 CPO/NPO]
- 核心主张：
  1. III-V/Si 集成是 PIC 规模化的关键；InPoSi 借助晶圆键合克服异质外延难题，在 Si 界面附近实现高晶体质量 [p3、p5]
  2. InPoSi 上 MQW 激光器阈值电流密度（J_th 0.4 kA/cm²）与效率与常规 InP 相当，且 85 °C/100 mA 加速老化 3000 h 未见可测量退化 [p9，看图核实]
  3. 平台可扩展到 HBT、HEMT、SWIR 光电二极管，多用途有助商业化 [p13]
- 关键数据：
  - 宽面 MQW 激光器 InPoSi_BSE vs InP：阈值电流密度 Jth = 0.4 kA/cm²（图中标注），脉冲状态下阈值与效率与 InP 参考相当 [p9]
  - 加速老化：先 100 °C、200 mA 老化（burn-in）18 h；再 85 °C、100 mA 老化 3000 h；老化前后 LI 曲线（0–200 mA，CW）基本重合，@100 mA 三颗激光器输出功率在 3000 h 内稳定（约 5–6 mW，读图）[p9]
  - 当前研究：InPoSi_BSE 上选择区域生长 SAG 激光阵列，5 通道覆盖约 155 nm 发射波长范围（约1500–1700 nm），CW 下 1515 nm 激射，20–70 °C LI 曲线；埋层激光器（SIBH 再生长）；InP-SOI 激光器利用 III-V/Si 光耦合，80 mA 下激射谱峰约 1543 nm 附近（读图）[p10–p11]
  - 拓展器件：HBT on InPoSi_SC：fT 380 GHz vs 350 GHz，fMAX 430 GHz vs 310 GHz（InP vs InPoSi，读图对应关系存在图例歧义，仅作参考），β=26，BVCEO=4.5 V，VCE=1.6 V，IC=5 mA/μm²；HEMT on InPoSi_SC（与 Chalmers 合作，Move2THz）；SWIR 光电二极管 on InPoSi_BSE：暗电流 J_dark 略高于 InP 参考 [p13]
  - 工艺：背面刻蚀 BSE（III-V Lab、NTT、东京大学、DTU、上智大学、UCSB/HP 等路线）、Smart-Cut（Soitec，InP 晶圆可重复利用）、InP 种子层等，100 mm 与 200 mm 尺寸（看图核实，p7）
- 提到的公司/客户/产品/标准：III-V Lab、Nokia Bell Labs、Thales、CEA LETI、Soitec（Smart-Cut）、Sophia University、Univ. of Tokyo、UCSB（工艺合作方图标）、Move2THz、Chalmers
- 与业界对比或记录声明：无 SOTA/record 声明；InPoSi 与 InP 参考对比 [p9]
- 推荐配图页：p9（InPoSi 与 InP 激光器 LI 对比与 3000 h 老化）；p10（SAG 多波长阵列与 InP-SOI 激光器）；p13（平台扩展到 HBT/HEMT/SWIR PD）

## 本批小结
1. 光源路线呈“分立 InP DFB（现主流）与多种集成/梳状光源并行”的格局：AMD p9 明确 InP DFB 是当前主流并列出频率梳、多波长激光器、异质集成阵列三条替代路线；Quintessent（QD 梳/DFB）、Photon Bridge（InP DFB + AWG）、Columbia/Xscape（Kerr 梳）、Chalmers（微梳）均为这些路线的具体实例。（来自 AMD、Quintessent、PhotonBridge、Columbia、Chalmers）
2. OCI-MSA 的 O 波段 8λ/BiDi 格局已成为光源共同的设计目标：UBC p5 给出 200G OCI v1.0 的 2 组 x 4 波长（1308.00–1334.78 nm，2.28–2.37 nm 间隔，53.125 Gbaud NRZ），AMD p8 给出 ELSFP 要求（400 GHz、±0.2 nm、RIN -144 dB/Hz），Photon Bridge、Quintessent 均以 200 GHz 8λ 且 ≥15 dBm/色或 >25 mW/λ 为目标；Xscape 的 ELSFP 形态产品标注 OCI-MSA。（来自 UBC、AMD、PhotonBridge、Quintessent、Columbia）
3. “GaAs 量子点、免隔离器、耐高温”成为多家共同主题：Huawei 展示 QD DFB 100 °C 下 200 mW@580 mA 与 >-25 dB 反射容忍及 200 GHz QD 梳（53G NRZ）；Quintessent 报 QD DFB 反馈至 -15 dB 时 RIN 约 -150 dBc/Hz、梳 >20% 峰值 WPE；UBC 与 AMD 亦将其列为免隔离器方案。但 WPE 仍偏低（Quintessent 25–30%，Huawei 要求模块 WPE 由 <10% 升至 >15%）。（来自 Huawei、Quintessent、UBC、AMD）
4. 集成光源与封装/耦合成本是产业化瓶颈，而不只是激光器本身：UBC 指出封装/组装/测试约占成本 80%、8通道串行对准 40–80 分钟，并提出 3D 打印光学；NTT 用薄膜 LD+EAM+SOA 集成消除耦合与分路损耗（对比 ELS 路线 -9.0 dB 分路损耗），III-V Lab 走 InPoSi 晶圆键合路线，Huawei 强调 laser-on-PIC 集成与热/可靠性折衷。（来自 UBC、NTT、IIIVLab、Huawei）
5. “宽而慢”（多波长 + 中等速率）是能效叙事核心，数字差异较大：AMD 给出 CPO 约 5 pJ/bit（可插拔 >15）；Columbia 称梳驱动 DWDM 相对商用约 100x（BW密度x能效）；NTT 薄膜 DML 阵列 0.33–0.65 pJ/bit（仅激光器/调制相关，非整链路），4x400/448G EML 激光能耗 0.12 pJ/bit；Huawei 3.2T VCSEL NPO 引擎整体约 4.3 pJ/bit。需注意各自统计边界不同（激光器 vs 整链路）。（来自 AMD、Columbia、NTT、Huawei）
6. 产业时间线：Xscape 8λ 可插拔 ELSFP 量产爬坡 2027Q4、Gen2 16λ 2026Q4 送样；Photon Bridge 2027Q1 送样；Open CPX 1.0 已于 2026-09-16 发布；Huawei Atlas 950（2026）已部署 800G SR8 VCSEL LPO，NPO 为下一代选项。NTT 明确“代工可用性：No”，说明薄膜路线仍在早期。（来自 Columbia/Xscape、PhotonBridge、UBC、Huawei、NTT）
