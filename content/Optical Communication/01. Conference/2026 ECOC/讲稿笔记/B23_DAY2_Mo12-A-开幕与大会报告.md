---
title: "B23 · DAY2 · Mo12-A-开幕与大会报告"
tags:
  - ECOC2026
  - DAY2
---

说明：本批只有一个PDF（大会开幕与全体大会报告全场连拍，共153页），内含4场大会报告，按题目页/机构logo切分。第1页为Ciena题目页（OCR乱码）。p36为Ciena致谢页，p51/p114/p118/p136为重复页。

### 0921-Mo12-00-全场-开幕与大会报告全场连拍.pdf（第1–36页，Ciena大会报告）
- 讲者/机构：Peter Winzer / Ciena（p1 题目页看图核实） | 题目：AI Cluster Scaling – It's All About Interconnect；内容主线为 Scaling AI is all about scaling I/O（据p35结论页） | 类型：邀请报告（大会报告）
- 方向归属（主/次）：主 4 Scale-up/in（CPO/XPO/NPO）；次 2 Scale-across / 3 Scale-out
- 核心主张（讲者结论页 p35 "Top Three Take-Aways"）：
  1. Scaling AI is all about scaling I/O。带宽层级：Die-to-die 100%、Memory 10%、Scale-up 1%、Scale-out/Scale-across 0.1%。
  2. Scale-up 的本质是"在I/O reach内塞进尽可能多的硬件"（a radix-ful of hardware within I/O reach）：更密的机架（液冷、共封装I/O提升前面板密度）；无retimer的I/O延伸reach（低功耗、低时延、高可靠）；扩展radix（高基数交换机、两层交换域）。
  3. 混合介质支持架构灵活性：高速SerDes需至少支撑到400G世代；最终走向芯粒集成的纯光接口。
- 关键数据：
  - Die-to-die接口面积：功率输送面密度 1–10 A/mm²；互连 0.5–5 Tbps/mm²；散热 ~3 W/mm²；全reticle面积 700–800 mm²；Switch芯片底面95%用于供电、5%用于互连；HBM/XPU为70%/30%。结论"两个芯片表面要承载功率、散热、I/O三种功能" [p9]
  - 前面板密度（1OU，200G/lane）：OSFP可插拔 70 Tbps；XPO+fly-over铜 200 Tbps；铜连接器 230 Tbps（x2 bidi）；微型光连接器 624 Tbps（xN，bidi，WDM） [p14]
  - 200G PAM4 各介质（reach/功耗）：无源铜DAC 1.5 m / 0 pJ/bit；带retimer的铜AEC 4.5 m / 11 pJ/bit；带retimer光 数百米 / 16 pJ/bit；有源铜ACC 3.5 m / 1.5 pJ/bit；线性光（LPO、CPX）数百米 / 6 pJ/bit [p16]
  - 无retimer有源铜缆实测示例（Ciena Nitro）：70 dB @ 53 GHz 通道损耗下 pre-FEC BER 约 1e-7（约 65 dB 以内约 1e-10~1e-9），200G PAM4；对比表：无源铜 DAC 1.5 m/0 pJ/bit、有源铜 ACC 3.5 m/1.5 pJ/bit、线性光 LPO/CPX 数百米/6 pJ/bit [p19，看图核实]
  - 混合介质铜扩展scale-up域：72 XPU @14 Tbps 扩展到 256 XPU @25 Tbps；线缆长度分布中无源铜占23%、有源铜占77%（0–3 m）；功耗增加约 ~1 pJ/bit [p20]
  - Open CPX MSA：6.4T & 7.2T 可插拔接口；共封装或近封装；铜或光；无压缩硬件 [p23]
  - Scale-out：带宽比scale-up低10x（roofline图：on-package memory → scale-up域 → scale-out 各降10x），结论"scale-out为scale-up的10%、片上封装内存带宽的1%"；应用B200做参照 [p30]
  - 单层超高基数交换机（Eridu）：5,120 radix；Scale-up 5k+ XPU单层域；Scale-out 首层10k+ XPU，两层3M+ XPU [p33]
  - 两层scale-up网络：Tier-1域 512×4机架（铜），Tier-2 512个交换机架（光），"铜用于 Tier-1 域、光连到 Tier-2 交换机"（看图核实）[p32]
  - Scale-across：4×12.8T XPO = 51.2 Tbps C+L波段；每机架64× C+L客户侧与线路侧容量；每机架128个放大光纤对；10–10,000 km、上千根并行光纤 [p34]
- 提到的公司/客户/产品/标准：Open CPX MSA（成员含 Ciena、Coherent、Marvell、Molex、Samtec、Terahop 及Accton、AOPT、Amphenol、Credo、Intel、Lumentum、Lightmatter、Nexthop.ai、TE、Viavi等）；OCI-MSA；Eridu（5,120 radix交换机）；Nvidia（B200、Rubin、K80）、Google TPUv1、Cerebras（Condor Galaxy）、Groq、Fugaku、Intel Haswell（roofline示例）；Broadcom、Nvidia（SerDes速率演进图来源）；Corning（可拆卸光纤来源图）；Meta（数据中心园区图）；XPO；HBM；LPO/ACC/AEC/DAC [p15–p34]
- 与业界对比或记录声明：未见明确"首次/record"声明；p27–p29提出问题"业界何时准备好把昂贵的XPU封装绑定到光芯粒共封装"，并指出关键是可拆卸光纤（焊料回流兼容、半导体工艺友好），p27 以"是否仍用铜"区分 Open CPX MSA（高速 SerDes）与 OCI-MSA（芯粒、宽慢光）[p27, p28, p29，看图核实]
- 推荐配图页：p16（DAC/AEC/ACC/LPO 各介质reach与pJ/bit对比表+链路框图）；p14（前面板密度70/200/230/624 Tbps）；p20（混合铜扩展至256 XPU）；p35（三条结论）

### 0921-Mo12-00-全场-开幕与大会报告全场连拍.pdf（第37–84页，imec大会报告）
- 讲者/机构：Patrick Vandenameele（CEO）/ imec | 题目：Integrated photonics at the heart of a scalable AI revolution（p37题目页）| 类型：邀请报告（大会报告）
- 方向归属（主/次）：主 3 Scale-out 224G/448G（光源/调制器/探测器）；次 4 Scale-up/in（CPO、3D集成光学）
- 核心主张：
  1. AI真正的问题是可扩展性；AI硬件可扩展定律取决于算法、scaling、fabric、架构（p39、p49–p50）；数据搬运是新瓶颈，电互连撞上封装面积与带宽墙（p53–p54）。
  2. imec的可扩展连接路线：面向scale-out的400G/lane可插拔光学（Ge-Si PD/APD、薄膜LiNbO3调制器），面向scale-up的CPO（GeSi EAM），面向scale-in的3D集成光学（p55–p75）。
  3. 未来AI数据中心架构：Scale-In（3D光学的超算节点，interposer/wafer/panel）、Scale-Up（多机架规模的"One big XPU"，下一代CPO）、Scale-Out（下一代PO）（p74–p75）。
- 关键数据：
  - O波段Ge PD：BW>110 GHz，R~0.9 A/W；O波段Ge APD：BW~90 GHz，R~1.9 A/W；APD在V=-7 V、Pin=-7 dBm下，160 GBaud与180 GBaud PAM4眼图张开 [p59]（"OFC 2026 and unpublished"）
  - 薄膜LiNbO3-on-Si调制器（TFLN MZM，推挽）：眼图标注 212.5 Gbaud；引用 J. Declercq et al.：320 Gb/s、未放大传输，100 GHz Ge PD + TFLN MZM，与行波驱动器和TIA共封装 [p60]
  - CPO路线图曲线：纵轴 Gbps/mm/pJ/bit，2020约1，至2038约3000量级（图，数值仅趋势）；标注"紧凑高效 >100 GHz光器件+先进3D封装"vs"封装上短铜线、光引擎无DSP" [p63]
  - GeSi电吸收调制器：调制带宽（23颗die）S21在100 GHz附近约 -2.5 dB（看图估计），Bias=2 V，λ=1560 nm；212.5 GBaud PAM4眼图；ECOC 2025/IEDM [p66]
  - "世界首个100 GHz低压Ge/Si APD"的400G/lane传输演示：GeSi FK EAM → Ge APD，采样示波器；425 Gbps眼图；数据速率 425 与 448 Gbit/s，425 Gb/s对应6.25% FEC开销（BER 约 3e-3）、448 Gb/s对应12% FEC开销（BER 约 1e-2）；引用 A. Shahin et al., ECOC 2026 [p67，看图核实，BER 为读图估计]
  - 3DIO光链路预测（wide-and-slow）：GeSi EAM+Ge APD+2 nm CMOS+混合键合+低损SiN波导 → ~0.5 pJ/bit；III-V EAM+Ge APD+2 nm CMOS+混合键合+SiN+集成GaAs量子点激光器 → ~0.25 pJ/bit；横轴数据速率 8/16/32/64 Gbps，岸线密度轴 1.6–51.2 Tbit/s/mm，64 Gbps处约25.6 Tbit/s/mm [p69]
  - 300 mm晶圆级SiN波导，传播损耗 <0.15 dB/cm，pitch <6 μm（1270–1320 nm 约 0.1 dB/cm，1350 nm 升至约 0.33 dB/cm；首个 300 mm 晶圆级跨掩模拼接互连波导，Xu et al., OFC 2024 M4A.3）[p70，看图核实]
  - 300 mm PIC-on-PIC Die-to-Wafer键合（Xu et al., IEEE 2026）：键合对准 <2 μm；D2W倏逝耦合损耗 EVC IL 约0.1–0.4 dB（1260–1340 nm曲线）；结论"过渡损耗 <0.3 dB" [p71]
  - "Die-to-Wafer光学'电梯'（escalator）插入损耗 <1 dB（1270–1310 nm 约 0.3–0.8 dB），与Cu-Cu混合键合接口共集成"，掩模宽 2.6 cm（imec 2026 未发表）（p72，看图核实）
- 提到的公司/客户/产品/标准：imec iSiPP200 / iSiPP300平台（p57、p64）；europractice/IC-link；Ghent University、PIX Europe、PhotonDelta、Interreg、Chips JU、photonixFAB、VLAIO、Oost-Vlaanderen、FWO（p60资助/合作方）；HBM、XPU、3DIO；有机电光调制器（"Beyond LNO"，p61）；BTO调制器（p73）。
- 与业界对比或记录声明：p67标题 "World's first 100 GHz, low voltage Ge/Si avalanche photodiode in a 400G-per-lane transmission demonstration"（讲者自称）[p67]
- 推荐配图页：p67（400G/lane GeSi EAM→Ge APD 演示与BER-速率图）；p69（3DIO 0.5/0.25 pJ/bit预测）；p71（300 mm D2W光互连<0.3 dB）；p74（Scale-In/Up/Out未来架构）；p59（Ge APD 160/180 GBaud眼图）

### 0921-Mo12-00-全场-开幕与大会报告全场连拍.pdf（第85–107页，华为大会报告）
- 讲者/机构：Dr. Man Jiangwei / 华为（HUAWEI） | 题目：Scaling AI From Optical Innovation to NPO and CPO Solutions（p85） | 类型：邀请报告（大会报告，兼产业发布）
- 方向归属（主/次）：主 4 Scale-up/in（NPO/CPO）；次 3 Scale-out 224G/光源
- 核心主张：
  1. AI时代三堵物理墙（算力、存储、网络）；网络墙是AI集群主要瓶颈（p86–p87）。
  2. 224G/lane时代NPO是最优方案（结论页 "NPO is the Optimal Solution for the 200G/Lane Era!"，p99），并以"五回合"对比NPO与CPO：技术成熟度、可插拔与维护、能效与集成、制造良率与商用成本、标准与开放生态（p91–p98）；看图核实：第1回合 NPO 胜（1:0），第4回合 NPO 胜后比分 3:1（即 CPO 赢下一回合，应为能效与集成），第5回合附 6.4T/12.8T NPO 标准项目时间表（2026.5 立项、2026H2 基线、2027H2–2028H1 发布）。
  3. 224G+之后NPO/CPO/OIO并行演进，追求极致能效与带宽密度（p103）；CPO的工程瓶颈：亚微米高密度设计（对准公差、自动化瓶颈、热漂移）、测试（电光联合仿真与测试、联合测试标准缺口、设备短缺）、故障隔离与冗余（光冗余、系统隔离、预测性监测）（p104）；光互连覆盖DCI到片内（Scale-Across/Out/Up/In）（p106）。
- 关键数据：
  - 三堵墙（引 Avicena Tech；A. Gholami "AI and Memory Wall", IEEE Micro 2024）：图注 HW FLOPS 60000x/20年（3.0x/2年），DRAM BW 100x/20年（1.6x/2年），互连BW 30x/20年（1.4x/2年）；LLM参数量与GPU HBM带宽差距标注 ×100,000 [p86]
  - Round 1（技术成熟度）：NPO=现有技术生态、ASIC与NPO间热/电磁隔离、上市快；CPO=定制技术架构、热/电磁耦合、产能瓶颈与上市晚 [p91]
  - Round 2（可插拔与维护）：NPO=兼容可插拔生态、光维护解耦、停机最小；CPO=非可插拔、共封装复杂度高、返厂周期长 [p93]
  - Hi-ONE：业界首个带内置激光源的7.2T NPO（High-density Optical-interconnect-Node Engine），"已量产"；对比1.6T光模块：带宽 1.6T→7.2T（4.5X）；可靠性 10 A fit→A fit（-90%，"A"为幻灯原文占位写法）；时延 100 ns→10 ns（-90%）；功耗 15 pJ/bit→5 pJ/bit（-66%）[p100，看图核实，柱图小字]
  - Hi-ONE NPO为τ-Scaling Law（几何缩放L与时间缩放τ）的实践：线性架构（降低电链路时延、降低插损、优化功耗）；ILS/EIC/PIC协同设计（降低外部激光功率、降低光插损、缩小尺寸与链路功耗）[p102]
- 提到的公司/客户/产品/标准：Hi-ONE（华为NPO光引擎）；NPO/CPO/OIO；SuperPOD（p101–p102）；Avicena Tech（图源）；LPO架构相关的线性驱动（"Linear Architecture"）。
- 与业界对比或记录声明：p100 "Industry's 1st 7.2T NPO with a built-in laser source"、"World's first 7.2 Tbps NPO optical engine"、"Now in mass production"（讲者自称）[p100]
- 推荐配图页：p100（Hi-ONE 7.2T NPO 与1.6T模块四项对比）；p89（224G/lane NPO/CPO与224G+ NPO/CPO/OIO演进）；p93（Round 2 NPO vs CPO）；p106（Scale-Across到Scale-In的全链路光互连）

### 0921-Mo12-00-全场-开幕与大会报告全场连拍.pdf（第108–153页，PsiQuantum大会报告）
- 讲者/机构：Mark Thompson（Co-Founder and CTO）/ PsiQuantum（p108 题目页看图核实） | 题目：Photonics for quantum computing（p109 为 ECOC 2022 大会报告回顾页）；主线为可扩展光子量子计算机 | 类型：邀请报告（大会报告）
- 方向归属（主/次）：主 6 QKD/量子/光纤传感（光子量子计算）；次 4 Scale-up/in（OCS光交换）
- 核心主张：
  1. 有用的量子计算机需约百万物理量子比特；当前机器约百量级（Google 2025–2026为105物理量子比特，p115），规模需提升 ×10,000's；关键挑战为可制造性、连接（qubit在芯片间高保真传输→模块化）、制冷功率、控制电子（p115–p116）。
  2. 光子路线借助半导体制造（GlobalFoundries）、光纤光学和低温工厂快速扩展（p117、p152）。
  3. 同一套超低损耗光子学可用于光电路交换OCS（p142–p143）。
- 关键数据：
  - 制造规模：Fab8 6,000 片晶圆；900 个工艺与计量步骤；40 层掩模；12 台专用主机（mainframe）；29 个腔体与测试台（看图核实）[p120]
  - Nature 2025 "A manufacturable platform for photonic quantum computing"：单量子比特态制备与测量保真度 99.98% ± 0.01%；量子比特互连保真度 99.72% ± 0.04%；双量子比特融合保真度 99.2% ± 0.12%（看图核实）[p125, p126]
  - Gen2平台：SiN（超低损波导、光子产生）、钛酸钡BTO（快速电光开关）[p128]
  - SiN波导损耗（看图核实）：约400 nm SiN；功能波导单模 1.3 dB/m、延时/路由波导多模 0.1 dB/m（最新点）；晶圆图单模 1.8 ± 0.2 dB/m、多模 0.5 ± 0.3 dB/m [p129]
  - 超低损SiN器件：交叉 0.27 ± 0.1 mdB（99.993%），串扰 <-80 dB；分束器 0.56 ± 0.03 mdB（99.987%），分束变化 0.99%（1σ）；90度弯 0.25 ± 0.03 mdB（99.994%）[p130]
  - 边缘耦合器损耗（标准光纤单纤探针）：2024年 127 ± 18 mdB（97%）→ 2025年 65 ± 13 mdB（98.5%）[p133]
  - 62端口FAU贴装统计（7月两周样本）：光纤到芯片损耗中位数 130 mdB，均值 150 mdB，标准差 ±50 mdB；<200 mdB占90%，<100 mdB占10%，>300 mdB失败率3%，损坏(>1 dB)为0% [p134]
  - 超导纳米线单光子探测器：探测效率 ~100%；灵敏度 -160 dBm (~1 aW)；时间抖动 <5 ps；死时间 ~1 ns（GHz速率）；暗计数 <1 Hz；工作温度 ~4 K [p135]
  - BTO对比铌酸锂：电光系数约30x；移相器短10x（mm级 vs cm级）[p138]
  - 快速8×8光开关：~1 GHz开关速度、上升/下降时间 <1 ns、消光比约25 dB（平均，off-target leakage直方图集中在-30至-20 dB）；示例数据率 500 Mbit/s [p139]
  - 光子复用器：8个光子源、250 MHz激光时钟、60 ns前馈时间、~99%光子保真度、（@8 kHz速率）光源亮度提升约2X [p140]
  - OCS原型（8×8，严格无阻塞）：插入损耗均值 ~1.0 dB、最大 ~1.7 dB（光纤到光纤，去嵌入MPO连接器损耗带来的变化）；串扰均值 ~60 dB、最小 ~55 dB（所有干扰通道开启）；重构时间 <1 ms；带偏振跟踪；全无源无光放 [p142]
  - 下一代OCS（开发中）：4×64，4个光子开关PIC，256光I/O端口，机架式；严格无阻塞全互联，亚毫秒重构（路径到亚微秒），无光放、低驱动电压 [p143]
  - 模块间量子比特互连：>99.7% 实验室到实验室保真度，经过 250 m 未稳定光纤 [p145]
  - 政府合作：芝加哥 Illinois Quantum & Microelectronics Park（Oct '25 破土）；澳大利亚/昆士兰政府 [p149]
- 提到的公司/客户/产品/标准：GlobalFoundries；Google Willow、Quantinuum H1（p113引述）；Frontier超算机架（尺度参照，p144）；PsiCube MK1/MK2低温平台（p147）；Nature 2025论文；IQMP。
- 与业界对比或记录声明：讲者称 "Big News for Quantum Computing: First Scalable Platforms" 为媒体引述（p127）；2025年Nature发表"可制造平台"（p122）；无明确SOTA声明。
- 推荐配图页：p126（Nature结果：99.98%/99.72%/99.2%保真度）；p142（8×8 OCS原型IL/串扰）；p143（4×64 OCS 256端口系统）；p134（FAU贴装损耗统计）；p130（SiN无源器件mdB损耗）

## 本批小结
1. Scale-up 方向共识：Ciena（p16/p20/p35）强调"无retimer"的I/O与混合介质（铜到光），其Open CPX MSA以6.4T/7.2T可插拔接口同时覆盖共封装/近封装、铜/光；华为（p100、p99）同样以7.2T NPO为主、与CPO对比。两篇均把7.2T量级作为下一代封装内光接口的容量基线。（Ciena、华为）
2. NPO vs CPO 路线之争：华为明确主张224G/lane时代NPO最优（可维护、可插拔生态、上市快），并预告224G+后NPO/CPO/OIO并行；imec（p63）则以CPO为scale-up路径，并进一步走向3D集成光学。CPO/NPO的分歧取决于可维护性与热/EMC耦合。（华为、imec、Ciena）
3. 带宽/能效指标趋势：imec 3DIO预测 0.5 pJ/bit（GeSi EAM+2nm CMOS）→0.25 pJ/bit（III-V EAM+量子点激光），对照Ciena给出的有源铜1.5 pJ/bit、线性光6 pJ/bit、retimed光16 pJ/bit，说明芯粒级光I/O的能效目标比可插拔光低1–2个数量级。（imec、Ciena）
4. 400G/lane光电器件已有实验支撑：imec展示Ge PD BW>110 GHz、Ge APD 160/180 GBaud PAM4眼图、TFLN 212.5 Gbaud、GeSi EAM 212.5 GBaud，并以GeSi EAM→Ge APD 完成425/448 Gb/s传输演示。（imec）
5. 光交换/OCS 走向硅光集成：PsiQuantum把量子计算用的超低损耗SiN与BTO快速光开关转向OCS原型（8×8，IL均值~1.0 dB，串扰~60 dB，<1 ms重构，256端口4×64在开发），与Ciena/华为的scale-up/across扩展需求形成呼应。（PsiQuantum、Ciena、华为）
6. Scale-across 与光传输：Ciena以4×12.8T XPO构成51.2 Tbps C+L收发、每机架128光纤对；华为把DCI列为Scale-Across层；两者均把长距（10–10,000 km、上千并行光纤）视为AI扩展的延伸。（Ciena、华为）
