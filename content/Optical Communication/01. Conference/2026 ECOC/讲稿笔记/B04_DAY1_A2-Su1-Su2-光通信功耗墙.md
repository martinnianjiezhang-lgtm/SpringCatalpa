---
title: "B04 · DAY1 · A2-Su1-Su2-光通信功耗墙"
tags:
  - ECOC2026
  - DAY1
---

# B04 笔记（ECOC 2026 Day1 Workshop：光通信功耗墙 Su1/Su2，A2 厅）

说明：页码 pN 为 PDF 页码（非讲者幻灯片页号）。图中读数标"约"者为读图估值。NEC（0920-am-Su2-B-05）已由主分析师处理，本批跳过。

### 0920-am-Su1-B-01-Meta-AI数据中心功耗.pdf
- 讲者/机构：讲者姓名幻灯片未显示（p1 看图核实，无署名）/ Meta（机构依文件名） | 题目：Standard Optic's Perspective on Power Savings（首页标题；无独立总题页） | 类型：Workshop 邀请报告
- 方向归属（主/次）：主 4 Scale-up/in（CPO/NPO/OCI） / 次 3 Scale-out
- 核心主张：
  1. 链路功耗"主要取决于 SerDes"，按 SerDes 个数计，集成光学（OCI）相对重定时可插拔可省约 5x/端口；400G SerDes 功耗趋势"走错方向"。
  2. 网络功耗占比虽降至约5%，但绝对瓦数仍大，且每节省1瓦网络功耗可同时省去制冷负担，约翻倍。
  3. 网络省电不止靠光学：拓扑/扁平化、内存池化、推理拆分、800 VDC、液冷都是杠杆；新成立的 OCI-MSA 推动光学 scale-up。
- 关键数据：
  - 链路功耗条形图（横轴单位图中未标，读图数值，深蓝为基值、浅橙为误差范围）：5nm SerDes 重定时可插拔 16；3nm 重定时可插拔 12.5(+1)；LRO 9(+2)；LPO/NPO/CPO 6(+2)；集成光学/OCI 3.5(+1.5)；200G 长距(LR) SerDes(3nm) 4(+1)；400G SerDes(预测) 4.5(+1.5) [p1]
  - 相对倍数（以LPO/NPO/CPO为1x）：5nm重定时 2x、3nm重定时 2x、LRO 1.5x、集成光学/OCI 0x [p1]
  - 数据中心用电：2025 95 TWh；2026 175 TWh(+84%)；2027 258 TWh(+47%)；2030 >1,200 TWh [p3]
  - 功耗分布：服务器与加速器约60%，制冷约20%，其他基础设施(UPS/配电)约10%，网络约5%，存储约5%；网络占比历史上10–15%，AI数据中心降至约5% [p3]
  - 15 kW GPU机架的10%=1.5 kW，100 kW GPU机架的5%=5.0 kW；500 W模块省电含制冷约折合1 kW数据中心省电 [p4]
  - 直冷液冷研究预测能效提升10–20% [p6]
- 提到的公司/客户/产品/标准：OCI-MSA（2026年3月成立）、CPO/NPO/LRO/LPO、ZR/ZR+、CXL、800 VDC、Fat-tree/Clos/3D torus/rail-only/dragonfly拓扑
- 与业界对比或记录声明：无SOTA声明；给出各方案相对功耗倍数比较 [p1]
- 推荐配图页：p1（各链路方案SerDes功耗条形图）；p5（网络省电杠杆清单）

### 0920-am-Su1-B-02-OpenAI-ScaleUp还能用铜吗.pdf
- 讲者/机构：Sara Zebian / OpenAI（p1 标题页看图核实） | 题目：AI scale-up – Does copper still do the job? | 类型：Workshop 邀请报告
- 方向归属（主/次）：主 4 Scale-up/in / 次 3 Scale-out（XPO形态、448G）
- 核心主张：
  1. 铜在今天的scale-up里仍很好用（NVL72、OpenAI Jalapeno均以铜背板为核心）。
  2. 未来scale-up带宽需求会使铜越来越难（信号完整性、更强FEC带来延迟、能效改进不够快、有源件降低可靠性）。
  3. 未来光学必须提供与铜相近的带宽、延迟、功耗、可靠性优势。
- 关键数据：
  - 以太网铜缆(CR)可达距离随单通道速率下降：25G/lane约5 m，50G约3 m，100G约2 m，200G约1 m，400G约1 m；PCIe CopprLink Gen6(64G)约2 m，Gen7(128G)约1 m（读图）[p4]
  - 端口速率约每3年翻倍：100G(4x25G)→200G→400G(8x50G)→800G(8x100G)→1.6T(8x200G)→XPO 12.8T(64x200G)与3.2T(8x400G)[p5]
  - NVL72：72 GPU铜互连，1,296连接，9个NVLink交换托盘，每交换机72端口 [p6]
  - Jalapeno：本地域每机架128个ASIC（16托盘x8 GPU），全局scale-up域2,048个ASIC，TH6交换机，机架内铜背板 [p7]
  - 早期400G/lane带缆通道Sdd21曲线：85 GHz处插损约-45至-50 dB量级（读图，不精确）[p8]
  - OpenAI产品覆盖超过10亿周活用户、250万企业 [p2]
- 提到的公司/客户/产品/标准：NVIDIA NVL72（Vera Rubin页面链接）、OpenAI Jalapeno、Broadcom TH6、IEEE 802.3dv（400G/lane，1 m铜，Co-Packaged Copper）、XPO MSA、ICA Interposer Board、CPX MSA、DAC/ACC/AEC、DR4/FR4/LPO/LRO
- 与业界对比或记录声明：无 [p9]
- 推荐配图页：p4（铜缆可达距离随lane rate缩短曲线）；p5（端口速率演进与XPO）

### 0920-am-Su1-B-03-amsOSRAM-慢而宽互连.pdf
- 讲者/机构：Ashkan Seyedi, Ph.D.（VP/GM, Digital Photonics Interconnects）/ ams OSRAM（p1 标题页看图核实） | 题目：How Can We Overcome The Optical Power Wall?（ECOC 2026 Workshops） | 类型：Workshop 邀请报告
- 方向归属（主/次）：主 3 Scale-out/光源（micro-emitter） / 次 4 Scale-up（CPO/NPO成本-功耗）
- 核心主张：
  1. 光学从OSFP到NPO到CPO主要是缩短电通道；"光学从未变低功耗，只是去掉了DSP"；胜负手是机械问题（光纤耦合、连接器、多芯光纤）。
  2. SiPho链路预算停滞在15–17 dB（从激光器输出算起）；激光功率约0.8–1 pJ/b(200G PAM4)，含链路预算约2.x pJ/b。
  3. 光学scale-up会发生（OSFP/NPO/CPO），但每GPU成本大幅上升；micro-emitter（uEmitter）可把成本增幅从180%压到25%。
- 关键数据：
  - 最佳量产件的光纤耦合损耗约1.x dB；SiPho链路预算分解：激光到光纤3 dB + Tx 8 dB + 光纤通道3 dB + Rx 3 dB → 2.x pJ/b(200G PAM4) [p2]
  - 液冷使机架功率10x（20 kW→200 kW，800 V、50 A）；下一个10x看不到，300 kW+机架不实际，故须拆分 [p3]
  - Rubin IO功耗现状表：内存(Cu on interposer, 208 Tbps, 1 pJ/b) 0.208 kW/GPU；scale-up(Cu twin-ax背板, 14.4 Tbps, 3 pJ/b) 0.043 kW；scale-out(TRO可插拔, 3.2 Tbps, 10 pJ/b) 0.032 kW；合计0.283 kW/GPU、机架41 kW，\$1,600/GPU、\$230,400/机架 [p4]
  - 光学scale-up(SiPho CPO/NPO, 4 pJ/b, \$0.2/Gbps)：合计0.298 kW/GPU、机架43 kW，\$4,048/GPU、\$582,912/机架，每GPU成本增约180% [p4]
  - uEmitter NPO/CPO情景(uEmitter 4 pJ/b, \$0.08/Gbps；SiPho CPO 4 pJ/b, \$0.2/Gbps)：0.278 kW/GPU、机架40 kW，\$2,000/GPU、\$288,000/机架，每GPU成本增约25%；可覆盖2–4排的scale-up域 [p5]
  - 幻灯片表（看图核实）：光学 scale-up 方案中 uEmitter NPO/CPO 行 4 pJ/b、0.058 kW/GPU、8 kW/机架、\$1,152/GPU；SiPho CPO 行 4 pJ/b、0.013 kW/GPU、2 kW/机架、\$640/GPU；两行与 Cu on interposer 合计 0.278 kW/GPU、40 kW/机架、\$2,000/GPU（对比今日 0.283 kW、41 kW、\$1,600）[p5]
- 提到的公司/客户/产品/标准：NVIDIA Rubin（IO功耗表）、InP/SiPho、micro-emitter(uEmitter)、多芯光纤、OSFP/NPO/CPO、LRO/TRO
- 与业界对比或记录声明：无SOTA声明；为成本/功耗情景推算，非实测 [p5]
- 推荐配图页：p4（光学scale-up的功耗/成本对比表）；p5（uEmitter降低成本增幅）

### 0920-am-Su1-B-04-Broadcom-AI集群高速IO.pdf
- 讲者/机构：Karl Muth / Broadcom | 题目：High-Speed I/O in AI clusters | 类型：Workshop 邀请报告
- 方向归属（主/次）：主 4 Scale-up/in（CPO/NPO/OCI-MSA） / 次 3 Scale-out 224G/448G电芯片
- 核心主张：
  1. 200G/lane以上，插损之外通道"质量"（相位响应、反射、截止、振铃）同样关键；标准BGA的C2M通道插损约32 dB。
  2. 提出Integrated Copper Attach（ICA，类CPC）和NPO-HDI：插损降到<20 dB，可支持FP LPO、改善LRO/TRO/RTLR，并可支持400G/lane。
  3. OCI-MSA（2026年3月成立）：宽并行、NRZ、双向单纤、标准激光器，面向机架内到多机架/多排scale-up。
- 关键数据：
  - 标准通道C2M插损32 dB @53.125 GHz（TP1a电、TP2光）[p4]
  - ICA方案通道：<20 dB @53.125 GHz，AWG32线缆，可支持400G/通道 [p5]
  - 200G FPO-LRO光输出，光回环误码地板：使用参考均衡时 BER<1e-13，标准BGA为<1e-8 [p9]
  - LPO情形：在TP1a需要前光标才能打开眼图，而100G LPO在TP1a不允许前光标；FPO-LPO试验最好BER约1e-10、最差约1e-4（光回环，误码地板）[p8]
  - NPO-HDI 200G：TP1a参考均衡15抽头FFE、无前光标，EECQ=2 dB；评价"比twinax+OSFP好得多"；TH6 EV板插损约16 dB，用同轴连接器替代OSFP以模拟NPO-HDI通道 [p11-p12]
  - 400G：线缆/连接器对全重定时链路影响小、半重定时中等、线性链路可能成为"showstopper"；400G LRO在NPO-HDI上"有合理机会"，400G LPO取决于通道与器件截止 [p13]
  - 产品时间线：TH4-Humboldt世界首个25.6T CPO（2022），TH5-Bailly 51.2T CPO（2023），xPU-Bailly OCI演示（2024），TH6-Davisson 102.4T CPO（2025），并给出Meta 1M link-flap-free小时（OCT'25）[p13]
- 提到的公司/客户/产品/标准：LPO-MSA、OCI-MSA（创始成员图标含Meta、Microsoft、OpenAI、AMD、Broadcom、NVIDIA）、OIF（FPO/NPO/CPO分类，CPO-AP/CPO-SP/CIO）、CPX MSA、Tencent、J.P. Morgan、Meta、TH4/TH5/TH6
- 与业界对比或记录声明：自称"World's 1st" 25.6T CPO / 51.2T CPO / OCI演示 / 102.4T CPO [p13]
- 推荐配图页：p13（400G讨论与CPO产品时间线）；p9（LRO眼图与脉冲响应，BER<1e-13）

### 0920-am-Su1-B-05-Arista-超密度可插拔XPO.pdf
- 讲者/机构：Sunil Priyadarshi / Arista，Senior Director, AI & Cloud Network Architect（p1 标题页看图核实） | 题目：Pluggable Forever: Power-Efficient, Ultra-Dense XPO — Breaking the AI Network Power & Density Wall | 类型：Workshop 邀请报告/产业发布
- 方向归属（主/次）：主 4 Scale-up/in（XPO） / 次 3 Scale-out 224G/448G
- 核心主张：
  1. XPO（12.8T，64x200G，集成液冷，可插拔）以"CPO级密度而不放弃可插拔性"缓解AI网络的功耗与密度墙。
  2. 系统层收益：相对传统方案模块数减8x–16x、交换机减2x–4x、网络机架减4x–8x。
  3. 400G/lane（448G）XPO仿真显示低损电通道路径，可走向409.6T/1OU。
- 关键数据：
  - 举例规模（10x GPU x 4x每GPU带宽 ≈ 40x网络I/O）：传统(1.6T光模块, 102.4T/20U)光模块272M、交换机3.19M、网络机架199K；12.8T XPO/NPO(204.8T/10U)为34M/1.59M/49.8K；25.6T XPO/NPO(409.6T/10U)为17M/0.797M/24.9K [p3]
  - 204.8T交换机用128x1.6T OSFP需4U，机架带宽密度约1.6 Pb/s/机架；用12.8T XPO（16个XPO）则204.8T交换机可装入10U（图中字样"1OU"，按10U理解），约6.5 Pb/s/ORv3液冷机架，机架带宽密度提升4x [p4]
  - 12.8T XPO LRO演示(64x200G)：TX平均光功率2.75 dBm、消光比4.33 dB、TECQ 2.39 dB、RLM 0.99；光回环64通道BER<1x10^-9（指数读图，看不十分清），电通道损耗约15 dB；模块总功耗约130 W，约10 pJ/bit，折合每1.6T端口约16.5 W [p8]
  - 技术谱系：无源铜2 m、有源铜5 m、RF微波10–20 m、VCSEL 20–30 m、DR8-LPO 2 km、FR4/LR4-LPO 2 km、CE(Coherent Lite)约10–20 km、ZR 20–4000 km [p7]
  - 448G PAM4奈奎斯特约112 GHz；448G PAM6符号率179.2 GBd、奈奎斯特约89.6 GHz（8 bit/2符号=2.5 bit/符号，不含FEC/编码开销）；对比图为224G XPO与448G XPO Rev. D差分插损，0–130 GHz [p9]
- 提到的公司/客户/产品/标准：Arista、XPO MSA、OSFP/1.6T、ORv3液冷机架、SiPh 4x8通道、IEEE Hot Interconnect 2026（8月19日）技术论文
- 与业界对比或记录声明：12.8T 8xDR8高密度液冷64通道可插拔XPO LRO模块与仿真平台（Hot Interconnect 2026，Technical Paper Session B）[p8]
- 推荐配图页：p3（XPO/NPO系统级模块/交换机/机架对比表）；p8（12.8T XPO LRO实测）

### 0920-am-Su1-B-06-AttoTude-介质波导做ScaleUp.pdf
- 讲者/机构：讲者姓名幻灯片未显示（p2 看图核实）/ AttoTude | 题目：AttoTude Thesis – ASICs over Dielectrics（p2标题；DiAx介质增强双绞线） | 类型：Workshop 产业发布
- 方向归属（主/次）：主 4 Scale-up/in / 次 3 Scale-out 448G电芯片
- 核心主张：
  1. 介质波导（DiAx）填补twinax与光纤之间的空白：无需额外电子器件、无上变频，速率与线规无关，可对接twinax连接器生态。
  2. 448G PAM4下DiAx约10 m、DiAx+约30 m，损耗约0.8 dB/m。
  3. 10 m可覆盖无光电元件的co-packaged scale-up、可插拔介质转换与广泛的LPO机会。
- 关键数据：
  - 相对26AWG twinax在110 GHz约有10 dB/m改善；图中twinax在448G（约110 GHz）损耗约12 dB/m量级，介质波导约1.2 dB/m（110–125 GHz放大图）[p4]
  - ASIC到介质波导发射：G-S-G天线发射；520–840 GHz带内损耗约0.8–1.1 dB/m [p3]
  - 448G线缆SNR模型（读图）：SNR约25 dB平台；twinax约2–3 m越过BER 1E-5线（约19.5 dB）；DiAx约10 m处约21.5 dB（越过BER 1E-7线约21.2 dB附近）；DiAx+到约35 m仍高于BER 1E-7阈值，40 m降至约20.3 dB [p6]
  - 可达距离表：112G PAM4 twinax 7 m、224G 4 m、448G <1 m；DiAx 224G/448G均10 m，DiAx+均30 m；硅光纤500 m。硅光上变频代价标注为额外5–7 pJ/bit、1000x故障率、30x成本 [p7]
  - 224 Gbit/s带Rx补偿的发射眼与均衡后接收眼演示 [p8]
- 提到的公司/客户/产品/标准：DiAx、DiAx+、twinax、SerDes、LPO
- 与业界对比或记录声明：无SOTA声明；给出对twinax和硅光的对比标注 [p7]
- 推荐配图页：p6（448G下twinax/DiAx/DiAx+ SNR-距离曲线）；p7（可达距离与代价对比表）

### 0920-am-Su2-B-01-Google-ScaleAcross功耗.pdf
- 讲者/机构：Matthew Newland / Google Cloud（代表Optical Networking Technologies团队） | 题目：Power Efficient Scale Across – Scaling for the AI Era | 类型：Workshop 邀请报告
- 方向归属（主/次）：主 2 Scale-across/多rail/ZR+ / 次 1 DCI
- 核心主张：
  1. 功耗是终极约束，驱动数据中心拆分与"超并行传输"，空间与功耗效率对scale-across网络至关重要。
  2. 过去十年光学创新使类scale-across网络功耗降约90%，但线路系统功耗几乎不变，如今约占总功耗预算的50%。
  3. 必须转向多rail（HyperRail）线路系统；并以"二值化"（够用SNR）的可插拔闭合（closure）追求最低TCO。
- 关键数据：
  - 相对功耗2017–2026：Gen4 DCI(2017)→Gen5(2022)→Gen6(2024)→ZR++可插拔(2026)；光学部分大幅下降，线路系统部分基本不变（图为相对高度，无绝对数值）[p4]
  - HyperRail线路系统：每站单ILA机房（传统为多个）、约80%功耗下降，来源为先进非制冷多芯片泵浦与元件共享；需要创新以简化制造，从4 rail到8 rail及更多 [p5]
  - 相干可插拔功耗：400G ZR++ <20 W，800G ZR++ <30 W，1.6T ZR++ <45 W（风冷热天花板约45 W，"可行但处于极限"）[p7]
  - 应对：液冷、高度并行光学、在直连路由器面板上做IPoDWDM，且"不可妥协的是覆盖距离与路由器利用率" [p7]
- 提到的公司/客户/产品/标准：Google Cloud、ZR++、IPoDWDM、HyperRail、ILA、Raman
- 与业界对比或记录声明：无SOTA声明；自述约90%十年功耗降幅 [p4]
- 推荐配图页：p4（2017–2026相对功耗光学vs线路系统）；p7（400G/800G/1.6T ZR++功耗与45 W风冷天花板）

### 0920-am-Su2-B-02-Ciena-多轨光子破功耗墙.pdf
- 讲者/机构：Bilal Riaz, Sr. Director, Product Line Management / Ciena | 题目：Breaking the Power Wall with Multi-Rail Photonics and Optical Interconnect Innovation | 类型：Workshop 邀请报告/产业发布
- 方向归属（主/次）：主 2 Scale-across/多rail / 次 1 相干长途；3 Scale-out（可插拔功耗）
- 核心主张：
  1. 更高的I/O速度将重划铜、IMDD、相干的边界：铜到光、IMDD到相干两大转变。
  2. 最大功耗节省要求光学靠近XPU（缩短电通道），448G下PCB到前面板连接失效。
  3. AI-scale网络不能一次部署一个波长：部署单元从波长转向光纤对；多rail光子与全谱转发器把22个机房压缩为1个。
- 关键数据：
  - 链路功耗（图中标注）：全重定时(DSP)30 W(18.5 pJ/bit)；半重定时(LRO)20 W(12.5 pJ/bit)；线性可插拔(LPO)10 W(6.5 pJ/bit)；近封装光学(NPO)8 W(5 pJ/bit)；共封装光学(CPO)5 W(3 pJ/bit)；AI规模下这些代价"以数百MW与数十亿美元计" [p4]
  - 交换ASIC演进：50T(2023)→100T(2025)→200T(约2028)→400T(约2029)，lane速率100G→200G→400G [p3]
  - 互连选择图：800G(现在)DAC/AEC铜至约7 m，IMDD 50–500 m至2 km；1.6T–3.2T(2026–'29)与3.2–6.4T(2028–'32)出现NPO/CPO并在20 km以上出现Coherent Optics CL；100 km+为ZR/ZR+ [p3]
  - 可插拔光模块功耗趋势：800 ZR/ZR+ 约25–31 W（2025）；1600 FR/CL OSFP约27–30 W（2026预测）；1600 ZR/ZR+ OSFP约34–42 W（2027预测）（读图，含图上"预测"斜线柱）[p7]
  - 部署：传统技术22个机房 vs 多rail光子1个机房；转发器每光纤对60–120个插件 vs 全谱转发器每光纤对1个线路端口 [p8]
  - 20 Pb/s用例：数百个光纤对(C&L波段)、每光纤对64x800G；RLS C&L HyperRail终端配置，紧凑机箱内16个C+L光纤对 [p10]
- 提到的公司/客户/产品/标准：Ciena WaveLogic相干可插拔、RLS现代线路系统（C&L HyperRail）、全谱转发器、OSFP/QSFP-DD800、直插液冷、ACC/AEC/DAC、NPO/CPO
- 与业界对比或记录声明：无SOTA声明 [p11]
- 推荐配图页：p4（各链路形态功耗阶梯）；p8（22机房 vs 1机房、60–120插件 vs 1线路端口）

### 0920-am-Su2-B-03-AIST-从余量到有效吞吐.pdf
- 讲者/机构：Kiyo Ishii / AIST（日本产业技术综合研究所） | 题目：Pushing Optical Network Efficiency to the Limit for the AI Era: From QoT Margins to Goodput-Aware Operation | 类型：Workshop 邀请报告
- 方向归属（主/次）：主 1 AI光网络（运行时优化/自动化） / 次 2 Scale-across
- 核心主张：
  1. 未来能效提升将越来越依赖运行时优化；光层全自动化是其前提。
  2. 三个浪费来源：QoT余量过大、算力与网络容量失配、协议不适配全光路径。
  3. 提出的FBD（组件级）模型作为光网络自动化平台，基于PostgreSQL实现。
- 关键数据：
  - 400ZR+按OSNR选速率：多余余量11 dB，峰值观测损失75%（能效从约220 pJ/bit降至约50 pJ/bit量级，读图；100/200/300/400 Gbps点）；目录值与实测OSNR估计误差3–7 dB（50 km有损接入光纤现场试验台）[p5]
  - 算力/网络失配：文件传输，峰值观测损失96%；在约30进程处，提供400G容量时吞吐仅约33%，算力效率损失60%（读图）[p8]
  - 协议：长路径上ACK限制吞吐，峰值观测损失93%和55%（图中按进程数）；拥塞控制下最大/最小路径容量对比，损失55%、95% [p9]
  - Takeaways"潜在浪费能量"：精确OSNR估计约75%；容量匹配算力约96%；协议针对全光路径约95% [p13]
  - 相关论文：K. Ishii et al., OECC/PSC 2025 MG3-3；Th1-G2 相关演讲 [p5, p11]
- 提到的公司/客户/产品/标准：NEDO项目JPNP16007、JST CRONOS JPMJCS25N3、FBD（Functional Block Diagram）模型、PostgreSQL、WSS/EDFA、400ZR+
- 与业界对比或记录声明：无 [p13]
- 推荐配图页：p5（多余OSNR余量导致的能效损失）；p13（三类潜在浪费占比总结）

### 0920-am-Su2-B-04-Nokia-海缆可插拔功耗.pdf
- 讲者/机构：John van Weerdenburg / Nokia | 题目：Power efficient submarine pluggable transceivers | 类型：Workshop 邀请报告
- 方向归属（主/次）：主 1 相干/海缆 / 次 2 ZR/ZR+
- 核心主张：
  1. 相干可插拔正逼近高性能嵌入式光学的性能，用于跨大西洋量级海缆有潜力；节能显著（能耗/bit接近嵌入式的10%）。
  2. 现有ZR/ZR+标准主要面向>120 km陆地DCI，海缆需要更高CD耐受、更窄线宽激光、无多余互操作余量、更细的符号率粒度。
  3. 现场试验证明可插拔在区域性重发海缆上可行。
- 关键数据：
  - 标准对比：OIF-800GZR-01.0(2024.10)最大CD 2400 ps/nm(约140 km)，相噪掩模对应500 kHz线宽，OSNR容限27 dB/12.5 GHz；800G OpenZR+(2025.7)最大CD 20,000 ps/nm(约1200 km)，对应150 kHz线宽，OSNR容限25.1 dB/12.5 GHz；OIF-1600ZR-01.0(2026.9)最大CD 2400 ps/nm，150 kHz线宽，OSNR容限30.7 dB/12.5 GHz [p3]
  - 假设两者均为800G：单纤容量嵌入式约38 Tb/s(500 km)降至约20 Tb/s(9000 km)，可插拔约30 Tb/s降至约20 Tb/s，两者在约8000 km以上趋同；每波速率可插拔在<5000 km保持800G，嵌入式更早下降（读图）[p4]
  - 能耗：嵌入式约425–680 pJ/bit，可插拔约70–100 pJ/bit（0–4000 km，读图）；每光纤机架单元：嵌入式约14–16 RU，可插拔约2 RU [p5]
  - 相同容量下节能约88–93%（0–9000 km，读图）；每C带光纤电费节省>\$12k/年，32纤海缆约\$0.4M/年（\$0.1/kWh假设）[p6]
  - 现场试验(ICE-X, OFC 2026 Th4C.6, S. Edirisinghe等)：弗吉尼亚海滩至波多黎各圣胡安2,931 km段、45个重发器，EX300光纤，平均跨距66 km；400G/波长5,682 km@72 Gbaud；600G/波长2,841 km@119 Gbaud（16QAM概率整形PCS，Q余量2.5–2.8 dB）；800G/波长闭合但余量不足以商用 [p8]
  - 面向地面回传：150 GHz间隔800G/波长，频谱效率最高5.3 b/s/Hz，地面覆盖最远1700 km；海缆：150 GHz中400G–800G/波长，重发器海缆达数千km [p9]
- 提到的公司/客户/产品/标准：Nokia、OIF 800GZR/1600ZR、OpenZR+、ICE-X、EX300光纤、PCS-16QAM
- 与业界对比或记录声明：无SOTA声明；引用OFC 2026现场试验 [p8]
- 推荐配图页：p5（嵌入式 vs 可插拔的pJ/bit与机架单元对比）；p8（ICE-X现场试验结果与星座图）

### 0920-am-Su2-B-06-ASN-空芯光纤与海缆能效.pdf
- 讲者/机构：Alexis Carbo Meseguer（p1 标题页看图核实）/ ASN（Alcatel Submarine Networks） | 题目：Can hollow-core fibers improve the power efficiency in SDM submarine systems? | 类型：Workshop 邀请报告
- 方向归属（主/次）：主 1 海缆（SDM/空芯光纤能效） / 次 无
- 核心主张：
  1. 无空间限制时，空芯光纤(HCF)可把每比特能耗降2x、容量潜在翻倍（低衰减、可忽略非线性）；但实际受光缆外径/空间(SDM)限制，今天的HCF设计仅"边际竞争"，无清晰优势。
  2. 在跨太平洋(约9,000 km)且SDM并行度合适时，HCF的能效优势可显现；容量增长需至少C+L带宽。
  3. 缩小外径或拓宽带宽是HCF被采用的关键；需在光纤设计与SDM潜力间权衡，技术仍需成熟。
- 关键数据：
  - 需求：带宽需求增速25–33%，平均26%（TeleGeography）；每3年翻倍；2026年多条24 FP/500 Tbps系统投产，市场需要 Pb 级与多 Pb 级海缆；全球国际带宽2024–31年CAGR约26%（非洲方向最快约33%）（看图核实）[p2]
  - 参考系统：Anjana 20 Tbps x 24 FP = 480 Tbps；Amitié 23 Tbps x 16 FP = 370 Tbps [p4]
  - 6,000 km跨大西洋、无空间约束、18 kW端到端供电：等效C带空间路径数SCF 300、2芯C+L 128、4芯/2芯C+L 60、HCF C带 520；潜在容量约3.2 / 2.6 / 2.4 / 6.3 Pbps（读图估计）[p6]
  - 6,000 km、实际空间约束下(<=48 FP，HCF C带为2x16 FP)：HCF C+L(SDM x2)仅约2 Pbps量级，限制来自SDM可扩展性（读图，不精确）[p8]
  - 9,000 km跨太平洋，1 Pbps目标：18 kW时仅HCF C+L 2x16 FP（约1.45）超过1 Pbps，其余约0.85–0.95；21 kW时2芯C+L约1.2；24 kW和30 kW时2芯/4芯C+L约1.4和1.7，HCF C+L约1.7和1.8（读图）[p11]
  - 6,000 km长期情景：目标3和4 Pbps，供电18/24/36 kW；今天的HCF设计约1.1 Pbps；HCF C+L 2x32FP在18 kW约3.3、24 kW约3.7、36 kW约4（SDM x3、x4）；4芯/2芯C+L在36 kW约3.95（读图）[p13]
  - 仿真参数（看图核实）：SCF 0.15 dB/km、跨距 60 km；2 芯/4 芯 MCF 0.16/0.17 dB/km、60 km、XT −62/−55 dB/跨；HCF 0.10 dB/km、跨距 90 km、IMI −60 dB/km、支持双向传输；等效有效面积 SCF/MCF 110 µm²；线缆耦合损耗 SCF 0.1 dB、其余 0.5 dB；放大器噪声系数 4.6 dB（HCF 另算 5/6 dB）；光纤对 SCF 48 FP、MCF 最高 48 FP、HCF 16/32 FP；放大带宽 5 THz（HCF 另算 10/15 THz）[p7]
- 提到的公司/客户/产品/标准：ASN、TeleGeography、Undersea Fiber Communication Systems 第3版（2025.7）、SCF/2芯/4芯MCF、C+L、HCF；关联演讲Su4-B（数百km无中继HCF链路）
- 与业界对比或记录声明：无SOTA声明 [p14]
- 推荐配图页：p6（无空间约束下HCF容量与每比特能耗）；p11（9,000 km跨太平洋不同供电下容量对比）

## 本批小结

1. 功耗墙共识：从SerDes/电通道找功耗。Meta指出链路功耗"主要是SerDes"，重定时到集成光学约5x；Ciena给出DSP 18.5→LRO 12.5→LPO 6.5→NPO 5→CPO 3 pJ/bit阶梯；amsOSRAM则指出"光学并未真正变低功耗，只是拿掉了DSP"（Meta B-01、Ciena Su2-B-02、amsOSRAM B-03）。
2. scale-up形态之争：铜仍能用（OpenAI，NVL72/Jalapeno），但400G/lane下铜受SI限制；出现的替代路线包括XPO可插拔（Arista，12.8T、约10 pJ/bit、~130 W、64x200G LRO实测）、NPO-HDI/ICA（Broadcom，<20 dB @53.125 GHz）、介质波导DiAx（AttoTude，448G下10–30 m）、OCI-MSA（Broadcom、Meta）。光学scale-up的成本是硬约束：amsOSRAM估算每GPU成本+180%，uEmitter情景仅+25%（OpenAI B-02、Arista B-05、Broadcom B-04、AttoTude B-06、amsOSRAM B-03）。
3. scale-across的瓶颈已从光学转到线路系统：Google称十年光学功耗降约90%，线路系统占比升至约50%，HyperRail约80%降功耗；Ciena主张部署单位由波长变为光纤对（22机房→1机房，60–120插件→1线路端口）；1.6T ZR++ <45 W逼近风冷天花板，液冷不可避免（Google Su2-B-01、Ciena Su2-B-02）。
4. 海缆能效两条路线并存：可插拔替代嵌入式（Nokia，能耗/bit约为嵌入式10%，ICE-X试验600G/2,841 km）与SDM/空芯光纤（ASN，HCF潜在2x能效但需外径缩小与C+L；仅在9,000 km等长距/大SDM下才显优势）；二者均指出供电与光缆空间是硬约束（Nokia Su2-B-04、ASN Su2-B-06；NEC已由他人覆盖）。
5. 光网络运行层面的浪费：AIST量化OSNR余量过大（11 dB，约75%损失）、算力/网络容量失配（约96%）、协议不适配全光路径（约95%），主张光层全自动化（AIST Su2-B-03）；与Google"二值化闭合追求最低TCO"的思路方向一致（Google Su2-B-01）。
6. 网络功耗占比看似小实则重要：网络约5%，但百kW级GPU机架上的绝对功耗和制冷倍增使其仍重要，同时光学scale-up能撬动占60%的GPU功耗（Meta B-01、amsOSRAM B-03）。
