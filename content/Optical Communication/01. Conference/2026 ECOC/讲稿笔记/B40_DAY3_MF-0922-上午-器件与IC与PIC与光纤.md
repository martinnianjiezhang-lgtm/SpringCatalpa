---
title: "B40 · DAY3 · MF-0922-上午-器件与IC与PIC与光纤"
tags:
  - ECOC2026
  - DAY3
---

# B40 笔记（ECOC 2026 Market Focus，0922 上午 器件/IC/PIC/光纤）

说明：已跳过主分析师完成篇目 0922-MF-am-1100-Coherent。标 [OCR] 的数字仅来自 OCR、未经看图核对。页码为 PDF 页码（与投影片右下角页码可能差 1）。

### 0922-MF-am-1000-Coherent-支撑AI基础设施三种扩展的光技术.pdf
- 讲者/机构：Julie Sheridan Eng（CTO，p1 部分被遮挡，看图核实）/ Coherent | 题目：Scaling the Optical Future — Optical Technologies Enabling Scale Up, Scale Out, and Scale Across AI Infrastructure（p1 标题页，2026-09-22）；第2页大标题 Photonics: from transport infrastructure to compute fabric | 类型：产业发布
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO；次 3 Scale-out 224G/448G/光源 与 2 Scale-across/ZR/多rail
- 核心主张：
  1. AI 扩展依赖 scale-up、scale-out、scale-across 三个域的光互连 [p4]；算力需求增速超过单芯片效率增长，互连带宽成为系统性能关键 [p3]。
  2. 可插拔向更高速率（400G/lane）与更高密度（XPO）演进；CPO 密度最高、功耗最低，NPO 可维护性和架构灵活性好 [p6-p8]。
  3. 光链路将进入封装内（光中介层、VCSEL 阵列）；DCI 侧靠 ZR/ZR+、C+L、multi-rail 与多种新光纤扩容 [p10, p13, p14]。
- 关键数据：
  - 算力需求增长 4.5x/年 vs 芯片效率 2x/两年（摩尔定律），差距拉大（来源 Bain 2025） [p3]
  - 3.2T OSFP 尺寸模块：8×425 Gb/s PAM4，8×425G 差分 EML + InP PD，DSP 8×212G→4×425G，NPO 连接器支持 16×212G；眼图显示 Outer OMA 5.45 dBm、Outer ER 3.4 dB（ECOC 2026） [p6]
  - 400G 全链路演示（InP 差分 EML + InP PD，OFC 2026）；宣称首个自研硅光 400G 链路（Dong et al., OFC 2026 PDP Th4A.4） [p6]
  - XPO：64 lanes×200G = 12.8 Tb/s，InP HP 激光器 + 200G/lane 硅光 PIC，集成液冷；更高密度形态 64×400G = 25.6 Tb/s [p7]
  - 6.4 Tb/s 硅光 NPO 演示：32×200 Gb/s，3.5 pJ/bit，15 Gb/s/mm²；ELS 内置 InP UHP 激光器、隔离器、TEC；可与 1.6T FRO、TRO 收发器互通 [p8]
  - VCSEL 阵列 NPO：1.2 pJ/bit，12 Gb/s/mm²（含 2D VCSEL/PD 阵列、TIA、驱动）；1060 nm 背发射 VCSEL 阵列，最高 64 Gb/s NRZ、128 Gb/s PAM4，倒装焊 [p9]
  - L-band 800G QSFP-DD DCO 演示，Tx 功率 0 dBm（ECOC 2024 演示，本次回顾） [p13]
  - 4 Rails C+L 多 rail 放大子系统；C+L 约使可用频谱翻倍，之后容量增长转向更多光纤 [p14]
  - QKD：CUbIQ QKD QSFP-28（1550 nm 量子信道）+ Coherent 200G FR4 OSFP（1310 nm 加密数据信道），Nvidia ConnectX-7 主机间演示（ECOC 2026 现场） [p16]
- 提到的公司/客户/产品/标准：Bain、TE Connectivity、Open CPX MSA（Coherent 为创始成员）、OCI、XPO、ELSFP、ZR/ZR+、CUbIQ、Nvidia ConnectX-7；p15 可插拔光线路系统（POLS）：1RU 集成 EDFA/OTDR/OPS/OSC，可插拔 EDFA 内含泵浦、无源器件、EDF、PD 与 VOA（看图核实）
- 与业界对比或记录声明（SOTA/首次/record）：宣称“Industry first: 400G link with internally designed Silicon Photonics at OFC 2026” [p6]
- 推荐配图页：p6（3.2T 8×425G 模块与 400G 眼图）；p8（6.4T 硅光 NPO 与 ELS 组件）；p9（VCSEL 阵列 1.2 pJ/bit）

### 0922-MF-am-1020-SourcePhotonics-后1.6T时代哪种光方案会胜出.pdf
- 讲者/机构：Frank Chang, Ph.D / Source Photonics（p1 看图核实） | 题目：Crossroad again, what optics solution(s) will be prevailing for post 1.6T era?（Market Focus, 2026-09-22） | 类型：产业发布
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器；次 4 Scale-up/in CPO/NPO/XPO
- 核心主张：
  1. 可插拔光模块仍是 AI scale-out 首选；下一步是 400G/lane，3.2T（8×400G）对应下一代 204T 交换机 [p10]。
  2. 1.6T 之后功耗路径为 FRO（DSP 5 nm 30 W/18.5 pJ/bit，3 nm <25 W）→ LRO（15–17 W/12.5 pJ/bit）→ LPO（10 W/6.5 pJ/bit）→ NPO（8 W/5 pJ/bit）→ CPO（5 W/3 pJ/bit），LRO/LPO 省 30–60%、NPO/CPO 省 70–85% 但距离更短；NPO 可能在 2027 起量，XPO 时间线尚不清晰；内置激光 NPO 可省 PM 光纤与 ELSFP 但有激光失效可靠性风险 [p16, p20，看图核实]。
  3. 关键使能器件是高功率 CW 激光器（70 mW → 400 mW）及 ELSFP [p18, p21]。
- 关键数据：
  - 光模块销售额 2019-2025 图，2025 年约接近 20B USD（柱高读数，非精确）；“4x growth in 2 years”，多数销量来自 Open MSA 可插拔 scale-out 模块（引 Cignal AI） [p5]
  - 交换机代际：12.8T（2018, 32×400G 模块）、51.2T（2022, 64×800G）、102T（2025, 64×1.6T, 512×200G PAM4）、204T（2026 标注, 64×3.2T, 512×400G, PAMx?） [p10]
  - 400G PAM4 IMDD 通常需 224 GBaud，要求 100-110 GHz 光带宽；提出“Coherent lite”（合并两个偏振各 200G）；100 GHz DAC/ADC 用 2nm CMOS 可行；电通道是瓶颈 [p11]
  - 1.6T DR4 4×400G 齿轮箱 OSFP 演示（8×200G→4×400G）：212.5 GBaud，SSPRQ 码型，TDECQ = 1.1 dB，ER(outer) = 4.2 dB，OMA(outer) = 1.7 dBm（幻灯写“1.7Bm”，看图为 dBm 量级）；屏幕读数 Outer ER 4.275 dB、TDECQ 1.17 dB、Outer OMA 1.362 dBm，与幻灯文字略有出入 [p13-p14]
  - 1.6T 时代功耗对比（参考 102.4T 交换）：全重定时 DSP 5nm 30 W（18.5 pJ/bit，Gen2 DSP 3nm <25 W）；半重定时 LRO 15-17 W（12.5 pJ/bit）；LPO 10 W（6.5 pJ/bit）；NPO 8 W（5 pJ/bit）；CPO 5 W（3 pJ/bit）；相对 1.6T 节电 30-60%（至 LPO 一线）、70-85%（至 CPO），代价是覆盖距离更短 [p16]
  - 硅光 CW 激光器路线：400G 70 mW（Q4 2025, DFB, ≤300 mA @75°C）；800G 100 mW（Q1 2026）；1.6T 150 mW（Q3 2026, DFB+SOA, ≤650 mA @75°C, 1500×250 µm）；1.6T CPO 200 mW（Q4 2026, ≤850 mA @75°C）；3.2T CPO 400 mW（Q1 2027, ≤1600 mA @45°C, 2000×500 µm） [p18]
  - 产品路线：150 mW CW→ELSFP VHP（102.4T NPO/CPO 交换机）；400 mW→ELSFP UHP（204.8T）；>400 mW→ELSFP SHP；12.8T XPO（64×200G）、25.6T XPO（64×400G） [p20]
  - 展示：6.4T NPO 可插拔模块、12.8T XPO 模块（204.8T 交换机 XPO 1U vs OSFP 4U）、Broadcom 112.4T CPO 配 DR8 ELSFP [p21]
  - XPO/Open CPX 能效-距离图：6.4T OpenCPX-4DR8（Linear）约在 5 pJ/b、100 m 内；12.8T XPO 8DR8 RTLR 约 10 pJ/b；12.8T XPO 16FR4 FRO 约 15 pJ/b（1-10 km）；XPO Coherent-Lite 与 XPO-ZR-Coherent 位于 scale-across（图上刻度，读数近似） [p17]
  - NPO 内置激光器可去掉 PM 光纤和 ELSFP，成本更低但有可靠性风险；难点：内置激光温控（波长漂移）、额外热耗散、高密度 FAU 间距、高通道数硅光 PIC 良率、高密度 socket 维护；2D OE 方案（OFC’26 演示）被标为“PIC 厂商不推荐” [p19, p20]
- 提到的公司/客户/产品/标准：Cignal AI、LightCounting、IEEE 802.3、OIF（400G per lane MSA）、XPO MSA（创始成员）、Open CPX MSA（贡献成员）、Broadcom、Keysight、Innolight、Eoptolink、Coherent 等（p5 图例）
- 与业界对比或记录声明（SOTA/首次/record）：幻灯标题“Industry 1st Product ready 1.6T 4x400G OSFP Live Demo”（展台 C2130） [p13]
- 推荐配图页：p16（FRO/LRO/LPO/NPO/CPO 功耗阶梯）；p18（CW 激光器功率路线表）；p14（212.5 GBaud 400G/λ 眼图）

### 0922-MF-am-1040-fibeReality-光器件厂商的高风险对冲.pdf
- 讲者/机构：fibeReality（分析咨询，讲者姓名页面未显示） | 题目：光器件厂商的高风险对冲（英文原题未见；含 “Verdict: Co-Packaged Optics Illusion Has Ended” 等观点页，p1 看图核实：CPO 多年内将局限于高成本封闭系统，远期岸线密度触顶时才必要） | 类型：市场分析
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO；次 3 Scale-out 224G/448G/光源
- 核心主张：
  1. 基于“最新情报收集”，CPO 幻象已结束：Nvidia 无法像当年推可插拔那样强迫使用；CPO 多年内限于封闭系统且成本高；远期当岸线密度触顶时 CPO 才成为必需（末句被遮挡）[p1]。
  2. NPO 比 CPO 更安全（CPO 良率问题已成现实、热问题更严重，NPO 可维护性更好），但 NPO 仍有未知项 [p7]；LPO 被称为“光学史上最糟的想法”[p2]。
  3. 光器件商应避免进入铜缆领域；铜在 scale-up 仍将长期存在 [p11, p12]。
- 关键数据：本讲多为定性观点，无可核对的实测数据。
  - 中国：全国性推动 NPO（阿里巴巴牵头）；薄膜铌酸锂方面类似推动，空芯光纤可能类似；中国收发器龙头将继续抢国际份额 [p4]
  - 微 VCSEL vs 微 LED：Credo 因可靠性问题完全取消 μLED 项目，转向 μVCSEL；Google 似乎更倾向 μVCSEL；μLED 需要“出色的齿轮箱” [p9]
  - Radio over Waveguide（RF 波导）为“黑马”，少数厂商；距离存在分歧，10 m 以上有争议，但 7 m 本身就可能很有价值 [p10]
  - 铜：Nvidia 与铜“热恋”；CPC 和有源铜将保持力量（其他大型超大规模用户认真考虑 CPC）；NPC 数据表可能比 NPO 好；200G 系统铜芯片多；不要低估铜创新（如连接器）；“光模块成本需低 10x”被夸大，光学须在铜失效处以性能而非价格取胜，小比例替代即可带来可观增长（看图核实） [p12, p13]
  - Microsoft 与 OCI MSA：超大规模用户是跟随者而非标准制定者，是被动观察者，Microsoft 光学领导层不清晰；MSA 对行业仍有潜力 [p6]
- 提到的公司/客户/产品/标准：Nvidia、Alibaba、Credo、Google、Microsoft、Amazon（p5 看图核实：标题“Amazon’s Due Diligence on Software Greater Than on Optics”，称亚马逊将继续试验自研收发器或新制芯方式降本、Google 光学技术人才更强、AWS 深度参与光设备初创交易）、Ciena/Nubis（作为进入铜领域的例外）、OCI MSA
- 与业界对比或记录声明（SOTA/首次/record）：无（观点性）
- 推荐配图页：p1（CPO 结论页）；p7（NPO vs CPO 风险对比）；p9（μVCSEL vs μLED）

### 0922-MF-am-1120-Jabil-面向大批量制造的光子封装.pdf
- 讲者/机构：Massimo Leo（Sr. Product Line Manager - Photonics）/ Jabil Photonics（p1 看图核实） | 题目：Photonics Packaging for High-Volume Manufacturing in the AI Era | 类型：产业发布
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO；次 3 Scale-out 光源/调制器（制造）
- 核心主张：
  1. 光子封装是 AI 基础设施可制造性的核心挑战，目标是逼近 CMOS 封装的量产规模 [p2, p8]。
  2. 业界需缩短从原型到高良率量产的成本和时间；Jabil 提供从 NPI 到量产的一体化路径 [p8]。
- 关键数据：
  - 电损耗：可插拔 >20 dB，CPO/NPO 为 5-10 dB [p2，看图核实]
  - PIC-EIC 集成方式：2D 线键合、2D µBump、2.5D 中介层、3D（线键合/倒装/TSV/混合键合），功耗和速度依次改善（图中箭头 Power、Speed）；工艺步骤含晶圆减薄、切割、贴片、线键合、倒装、标准/无助焊剂回流、热压键合、混合键合，均配 AOI 与测试 [p3]
  - 流程：设计→晶圆制造→Jabil 先进光子封装（晶圆级：贴装、凸点、TSV、晶圆级激光器贴装、晶圆测试、背磨、隐形切割；芯片级：贴片、线键合、倒装、回流、底填、激光器贴装、BGA、被动/主动光纤耦合、透镜、盖板）→模块制造→系统制造 [p5]
  - 制造点：渥太华（加拿大，NPI 线）、槟城（马来西亚，大批量制造）（看图核实） [p6]
  - 延伸到 AI 机架级集成：液冷 AI 网络 fabric 机架设备，覆盖硅光、交换、光纤管理、shuffle box、液冷、供电、机架级集成与验证、全球制造部署（看图核实）[p7]
- 提到的公司/客户/产品/标准：Jabil；未见具体客户名
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p5（从硅到方案的封装流程全景）；p3（PIC-EIC 集成方式谱系）

### 0922-MF-am-1140-CignalAI-跨域扩展对相干市场的影响-另一版.pdf
- 讲者/机构：Andrew Schmitt，Cignal AI | 题目：The Impact of Scale Across on the Coherent Market（2026-09-22） | 类型：市场分析
- 方向归属（主/次）：主 2 Scale-across/FST/多rail/ZR/ZR+/CL；次 1 相干/DCI
- 核心主张：
  1. Scale-across 到 2030 年将占云可插拔带宽 72%（2025 年为 5%），2028 年超过 metro/前端 DCI；对 metro DCI 是增量 [p7]。
  2. 线路系统是约束：C+L 已是基本配置，空芯/S 波段/多芯未规模部署；产能受 InP 晶圆限制，线路系统部件交期 12-18 个月；靠堆叠光纤对扩容，需要 multi-rail [p8]。
  3. 价格分化：放大器/泵浦/线路系统价格持平或上涨，而商用相干可插拔 ASP 持续下降 [p8]。
- 关键数据：
  - 2026 年 2Q 云光硬件营收 1.9B USD（+63% YoY）；云占全球光硬件 38%（去年 28%）；可插拔占硬件增长 47%；北美 1.6B USD（+81%），占全球 45%（去年 35%）；云占北美光 72%（去年 62%）；长途创纪录 2.4B USD（+21%），与 scale-across 关系不大（看图核实） [p5]
  - 相干光模块市场：2026 年近 7B USD，2030 年近 10B USD；\$/G 可插拔现低于 \$6/G，嵌入式 \$15/G，可插拔 2027 年降至 \$5/G 以下（数通约 \$0.50/G） [p6]
  - 云与托管可插拔带宽（Pb/s）：scale-across 2030 年约 640，前端 DCI 约 250（读图近似）；1600ZRx 到 2030 年 2.9B USD，成为最大单一模块类别 [p7]
  - Scale-across 支出 2030 年 8.7B USD，线路系统占 55%（2025 年 32%，累计过半）；原因：路由变长、1600ZRx 压低每比特相干价格、Raman 无处不在（约占累计支出五分之一，超大规模用户重共性与部署简便胜过成本优化）（看图核实） [p9]
  - 800ZRx 全球已出货 >100,000 端口（截至 2Q26）；Acacia 是唯一季度出货 >25,000 个 800ZR+ 模块的供应商；Ciena、Nokia 在爬坡；Marvell 错过早期量产（看图核实） [p10]
  - 某超大规模：2026 年 200,000+ 800ZRx，2027 年 >350,000（发布预测，看图核实） [p10]
  - 线路系统厂商：Ciena（早期 scale-across 城域唯一供应商、首个超大规模 multi-rail 采购订单、RLS Hyper-Rail）、Cisco（成熟 DCI/RON 线路系统、RON-MOFN 订单、Open Transport 3000 Multi-Rail）、Nokia（重夺超大规模线路系统份额、multi-rail 设计中标、1830 GX Multi-Rail）（看图核实） [p10]
  - Scale-across 定义：向多个站点扩展 scale-out，多站点训练成一个逻辑 GPU 集群；后端 GPU 流量为 WAN DCI 的 5-20 倍（少量超大、同步、不容丢包的流）；用交换机内相干可插拔经并行光纤线路系统传输（看图核实） [p4]
- 提到的公司/客户/产品/标准：Cisco/Acacia、Ciena、Nokia、Marvell、400ZR/800ZR/1600ZR 系列、MOFN
- 与业界对比或记录声明（SOTA/首次/record）：无（市场预测）
- 推荐配图页：p7（scale-across 带宽超过 DCI 的交叉曲线）；p6（相干模块市场与 \$/G）；p9（支出结构：可插拔 vs 线路系统）

### 0922-MF-am-1200-Crealights-大规模硅光互连的趋势.pdf
- 讲者/机构：CreaLights（北京海光芯正科技，讲者姓名页面未显示） | 题目：Trends of Large-scale Silicon Photonics Interconnection（据 p3 章节页 “Background of Large Scale Silicon Photonics Interconnection” 推断，看图核实为章节页而非题目页） | 类型：产业发布
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器（硅光模块）；次 4 Scale-up/in CPO/NPO/XPO
- 核心主张：
  1. 硅光在无晶圆厂量产和先进封装上占优，是数通中最能覆盖各类应用的技术 [p4]。
  2. 硅光渗透率 2026 年 >50%，2030 年 >70% [p5]。
  3. 先进光电封装是大规模量产途径，晶圆级光耦合仍是瓶颈 [p15, p22]。
- 关键数据：
  - 技术对比表（VCSEL/DML/EML/TFLN/SiPh，维度：Fabless、功耗、带宽、集成度、封装、成本），SiPh 各项多为最优（色点，定性）；“Fabless 可扩展量产 100,000,000 pcs/月”（图上数字，看得清程度中等）[p4]
  - 硅光渗透率：2023 23%、2024 30%、2025 38%、2026 50%、2027 56%、2028 62%、2029 67%、2030 73%（图上标注） [p5]
  - CPO/NPO 渗透率（TrendForce）：2026 0.5%、2027 5%、2028 15%、2029 25%、2030 35%；硅光渗透率（LightCounting）2025 38% → 2030 73% [p6]
  - Scale-out TRx（数量，单位图上未注，疑为百万）：2026 250、2027 298、2028 356、2029 426、2030 508；scale-up 新增：1、4、16、63、250 [p6]
  - Scale-out 演进：FRO → TRO → LPO（800G、1.6T 代降功耗/成本）；3.2T 可插拔；6.4T NPO/CPO、12.8T XPO [p7]
  - 跨机架 scale-up 链路：机架内 DAC <3 m；AEC <7 m；PCIe/Ethernet AOC <50 m；NPO 或 CPO <500 m [p8]
  - imec 路线（引 OFC 2024 Workshop）：光互连 2022 1 Tbps/mm 5 pJ/bit；2024 2 Tbps/mm 2 pJ/bit；2026 4 Tbps/mm 1 pJ/bit；2028 8 Tbps/mm 0.5 pJ/bit；2030 16 Tbps/mm 0.25 pJ/bit（imec 愿景目标日期） [p10]
  - 先进封装的光模块：单片 TRx 硅光芯片，3D 堆叠光子中介层以 TSV 引出 DSP；宣称功耗降低 30%、成本降低 25%（对象为其 400G QSFP112 DR4 先进封装模块，与常规封装对比，具体基准未见；看图核实） [p12, p14]
  - 光互连演进：可插拔 → OBO → NPO → CPO → OIO；2.5D CPO 25/50 Tb/s，2.5D chiplet CPO 50/100 Tb/s，3D CPO >100 Tb/s [p12, p13]
  - 主张：Fabless 设计 × 晶圆级封装 = 高效率量产 [p15]
- 提到的公司/客户/产品/标准：imec、TSMC COUPE、GF Fotonix、Corning GlassBridge、Teramount（p18 看图核实：晶圆级光测试与 EIC-PIC 混合键合已量产，晶圆级微透镜/光对准/玻璃桥验证中，晶圆级光纤贴装与光子线键合为方向）、LightCounting、TrendForce、400G QSFP112 DR4、1.6T OSFP224 2XDR4
- 与业界对比或记录声明（SOTA/首次/record）：无明确首次声明
- 推荐配图页：p5（硅光渗透率曲线）；p6（scale-up TRx 增量与 CPO 渗透率）；p10（imec 带宽密度/能效路线）

### 0922-MF-am-1220-EBOMSA-EBOMSA可靠且可互通的光互连.pdf
- 讲者/机构：Richard Ward，EBO MSA 联席主席/管理员，3M、Xscape Photonics | 题目：EBO MSA: Enabling Reliable and Interoperable Optical Connectivity for AI Data Centers | 类型：标准
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO（连接器）；次 3 Scale-out
- 核心主张：
  1. 扩束光学（EBO）连接器对灰尘和污染不敏感、插损稳定、避免高功率烧毁、配接力约降 20x，适合 AI 数据中心 [p5, p6]。
  2. 连接器首过插损失效率决定 CPO 组件返修率：2% 返修率要求每根光纤首次配接失效概率约 7e-5（51.2T FR4 场景） [p8]。
  3. EBO MSA 于 2026 年 3 月成立，满足互通、供应链稳定的需求 [p16]。
- 关键数据：
  - 51.2T 交换卡、100G lane：DR（PSM）Tx 512、Rx 512、激光 PM 光纤 64，合计 1088 个光纤连接；FR4（CWDM）128/128/32，合计 288；假设 3σ 首过光纤连接良率 99.865%；则板级光纤组装良率 DR 23.0%、FR4 67.8% [p8]
  - 光束扩展：入射光纤 9 µm，经全内反射镜准直扩束至 80 µm 直径，AR 涂层降低损耗与背反，接收插芯再聚焦入纤（看图核实） [p4]
  - 12 芯 EBO 插芯：1000 次重复配接（不清洁）IL 变化 <±0.1 dB（1310 nm）；插芯横向偏移 ±10 µm 内 IL 变化约至 0.35 dB（抛物线） [p13]
  - 随机配接测试：552 对连接器，8832 个数据点；97%（IEC）通道 <0.55 dB；99.2% 通道 <0.7 dB；平均 IL 0.32 dB [p14]
  - 回波损耗：16 芯 SM，9600 通道，平均 RL 66.7 dB，99% 通道 >55 dB（1310 nm，看图核实） [p15]
  - 数据中心维护：约 80% 网络问题与清洁相关，约 95% 维护请求为清洁（看图核实） [p11]
  - 成员 57 家：9 家终端用户（AMD、Arista、Cisco、HPE、Meta、Microsoft、Nexthop AI、Nvidia、Oracle）、48 家供应商；正在讨论 18 种连接器；路线：128f（8×16f）规范进行中，16f MPO 讨论中，16f VSFF、ELSFP 计划中（看图核实） [p17, p18]
- 提到的公司/客户/产品/标准：Oracle（Mark Filer 任主席）、3M、Xscape Photonics、Amphenol（Tiger Ninomiya）、Sumitomo（Adam Broughton）、Senko（Max Omodaka）、Ranovus、Source Photonics、IEC、ELSFP、MPO、VSFF
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p8（系统良率 vs 返修率与 7e-5 结论）；p14（552 对随机配接插损分布）；p13（1000 次重复配接稳定性）

### 0922-MF-am-1240-Lumentum-支撑新光子生态的激光器创新.pdf
- 讲者/机构：Lumentum（讲者未见，p8 为讲者照片） | 题目：支撑新光子生态的激光器创新（英文原题标题页看不清） | 类型：产业发布
- 方向归属（主/次）：主 3 Scale-out 224G/448G/光源/调制器/电芯片/OCS；次 4 Scale-up/in CPO/NPO/XPO
- 核心主张：
  1. AI 系统扩展催生新的光子生态（200G/400G lane、LPO/半重定时、CPO/NPO/XPO、OCI MSA、1060 nm VCSEL、多芯/空芯光纤、EBO、OCS、下一代相干与多发射泵浦） [p3, OCR]。
  2. CPO/NPO 使激光器选择成为系统优化的关键决策；不是单一实现的转变，而是分阶段的系统优化“旅程” [p6, p7, OCR]。
  3. 电力供应本身无法支撑 AI 增长，系统架构优化愈发有益 [p5, OCR]。
- 关键数据（p2–p8 已看图核实）：
  - 激光功率：NPO 21-23 dBm；CPO 25-26 dBm；WPE 20+%，<1 pJ/bit [p3, p7]
  - 前沿模型训练算力 4.2x/年（自 2018，80% CI 3.7–4.6，epoch.ai）；硬件数量 1.7x/年、训练时长 1.5x/年、硬件性能 1.4x/年（看图核实，此前 OCR 读作 42x 有误） [p2]
  - AI 光学市场到 2031 年 52B USD，CAGR 21%（LightCounting, 2026 年 1 月）；2030 年全球数据中心用电预计 945 TWh（IEA）；单个园区 1 GW+；交换 ASIC 500 W+ [p5]
  - 激光器设计考量：热管理（TEC、液冷）、可靠性与可维护性、故障影响（激光 FIT << 模块 FIT）、诊断遥测、路线上先系统级集成、最终进入光引擎 [p7]
  - NVIDIA CPO 引用页：传统可插拔 30 W（DSP 20 W + 激光 10 W）vs Co-Packaged Optics 9 W（光引擎 7 W + 激光源 2 W）（来源 Nvidia GTC 2025）；1.6T OSFP FRO 约 20 pJ/bit（102.4T 系统 4 RU）vs CPO/NPO <10 pJ/bit（1 RU）（看图核实） [p6]
- 提到的公司/客户/产品/标准：Nvidia、OIF（FD-01.0 Table 5）、OCI MSA、epoch.ai、IEA、LightCounting、Bank for International Settlements、The Economist
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p3（AI 驱动的光子生态全景清单）；p7（NPO/CPO 激光器系统权衡）

## 本批小结
1. **CPO 与 NPO/XPO 的分歧与折中**：Coherent、Source Photonics、Crealights 都以 NPO/XPO 作为可维护的中间路线（Coherent 6.4T NPO 3.5 pJ/bit；Source 认为 NPO 2027 起量、XPO 时间线不明；Crealights 预测 CPO/NPO 渗透 2030 年 35%）；fibeReality 更悲观，认为 CPO 多年限于封闭系统且良率/热问题已成现实。来自 p1000、p1020、p1200、p1040。
2. **激光光源成为核心瓶颈**：Source 给出 CW 激光功率路线 70→100→150→200→400 mW（Q4 2025 至 Q1 2027），Lumentum 给出 NPO 21-23 dBm、CPO 25-26 dBm，Coherent 用 InP UHP 外置光源（ELS）配 NPO；内置激光器有温控、热耗散和可靠性风险。来自 p1020、p1240、p1000。
3. **400G/lane 与相干下沉**：Source 指出 400G PAM4 IMDD 需 224 GBaud、100-110 GHz 带宽，电通道是瓶颈，并提出 Coherent-lite；Coherent 展示 8×425G 3.2T OSFP 模块与自研硅光 400G 链路，Source 展示 212.5 GBaud 1.6T 4×400G 齿轮箱（TDECQ 1.1 dB）。来自 p1000、p1020。
4. **Scale-across 拉动相干与线路系统**：Cignal 预测 scale-across 占云可插拔带宽 2030 年 72%、2028 年反超 metro DCI，线路系统占支出 55%，受 InP 产能和 12-18 个月交期约束；Coherent 同步展示 4-rail C+L 放大子系统、可插拔 EDFA 与多芯/空芯光纤方向。来自 p1140、p1000。
5. **量产、封装与连接器可靠性成为落地关键**：Jabil、Crealights 强调 PIC-EIC 3D 集成与晶圆级封装（Crealights 称封装使功耗 -30%、成本 -25%；晶圆级光耦合仍是瓶颈）；EBO MSA 给出 CPO 良率量化（1088 个连接，板级光纤组装良率仅 23.0%，2% 返修需 P_F≈7e-5；552 对平均 IL 0.32 dB）。来自 p1120、p1200、p1220。
6. **观点差异提示**：fibeReality 认为铜在 scale-up 长期存在、LPO 是“最糟想法”，而 Source 仍把 LPO 列为 10 W（6.5 pJ/bit）的可选层级，Crealights 则用 FRO/TRO/LPO 作为 scale-out 降本路径；市场分析与厂商口径不一致，引用时需区分。来自 p1040、p1020、p1200。
