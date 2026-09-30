---
title: "B14 · DAY1 · E1-Su1-Su2-集成光子产品化"
tags:
  - ECOC2026
  - DAY1
---

# B14 笔记（ECOC 2026 Day1 E1 Su1-Su2 集成光子产品化 / AI光网络Workshop）

说明：图片页均为投影照片，数值以图片核对；看不清处已标注。

### 0920-am-Su1-C-00-全场-上半场速记.pdf（第1–2页，Workshop开场）
- 讲者/机构：未见讲者名 | 题目：Will the AI workload require an end-to-end-optimized network infrastructure?（Workshop题目） | 类型：Workshop
- 方向归属（主/次）：主[1 AI光网络] / 次[2 Scale-across]
- 核心主张：
  - GenAI流量不同于传统流量：训练为“大象流”、推理为“小鼠流”，对规模、时延、鲁棒性要求不同。
  - 超算/云厂商与电信运营商角色不同：云厂商自有骨干与DCI，"fiber is the new wavelength"；运营商拥有大量光纤与边缘站点，靠近用户可降时延。
- 关键数据：无具体数字（p2为端到端编排分层架构图，文字被OCR破坏，看不清细节）[p1–p2]
- 提到的公司/客户/产品/标准：hyperscalers、telcos（泛称）
- 与业界对比或记录声明：无
- 推荐配图页：p1（对比“AI流量特性”与“云厂商/运营商差异”的开场页）

### 0920-am-Su1-C-00-全场-上半场速记.pdf（第3–9页，ITU-T ION-2030）
- 讲者/机构：Glenn Parsons，Ericsson，ITU-T SG15 主席 | 题目：ITU ION-2030: Architectures and Standards of Optical Networks for the AI Era | 类型：标准
- 方向归属（主/次）：主[1 AI光网络] / 次[5 固定与无线接入]
- 核心主张：
  - ITU-T框架“International Optical Networks towards 2030 and Beyond (ION-2030)”面向6G(IMT-2030)、AI、数据中心、宽带接入、家庭网络与ISAC，强调AI与光网络相互赋能。
  - “ION-2030 for AI”要求大带宽与覆盖、低时延低抖动、高可用高韧性；“AI for ION-2030”提供端到端QoS/QoE自动化、优化与保护。
- 关键数据：
  - 图示光网络分层：接入(FTTR/FTTO/PON, far-edge AI)、城域(edge-OTN/OXC, near-edge AI)、骨干与DC内(OCS+POD, cloud AI)，速率标注“400G/800G/1.6Tb/s … per λ”[p8]
  - 关联交付物：GSTR-ION-2030；面向数据中心GSTR.ION-aiDC、宽带G.Sup.ION-aiBB、家庭G.Sup.ION-aiHome、6G GSTR.ION-TN6G、企业G.Sup.ION-aiBusiness[p9]
  - 页4显示美国数据中心建设支出与AI相关进口占比的图（来源标注The Globe and Mail, 2026-06-13），具体数值看不清[p4]
- 提到的公司/客户/产品/标准：ITU-T SG15（Q2/Q3/Q5/Q6/Q8/Q10–Q14等）、GSTR-ION-2030、OTN、OCS、PON
- 与业界对比或记录声明：无
- 推荐配图页：p8（ION-2030三层网络+AI分布的全景架构图）

### 0920-am-Su1-C-00-全场-上半场速记.pdf（第10–17页，OVHcloud）
- 讲者/机构：Sina Fazel，Technical Lead，OVHcloud | 题目：AI Driven Traffic Evolution in the Optical Backbone: OVHcloud's Fibre Constrained Architecture（副题：An OVHcloud traffic vision PoP-DC and DC-DC in the AI era） | 类型：产业发布
- 方向归属（主/次）：主[2 Scale-across/FST/跨楼园区] / 次[1 DCI]
- 核心主张：
  - 新思路“每组区域共享一套服务栈”(One stack per Group of Regions)，相邻region共享DB/缓存/队列等服务栈而非各自复制，需要网络支撑。
  - 用基于FBOSS的新DC产品模糊DCN/DCI边界，形成区域“Fabric”环(ring)。
  - 距离<10 km无需线路系统，>10 km用800G ZR + 线路系统。
- 关键数据：
  - 环内容量为环间的10倍，骨干(BB)无法扩展；首个试验对已释放数MW基线功率[p14]
  - <10 km的Shared-Fate Zones区域环链路使用长距可插拔(如2x400G LR)，多对直连光纤，无放大器、无复用器[p15]
  - >10 km：800G ZR/ZR+模块，线路系统含WSS、L/C带放大、Raman、ILA，跨段约100 km；IP层保护，光保护开关考虑2027年[p16]
  - 运维挑战对比（region今天 vs 环内）：维护缓冲每region多份→环共享一份；存储副本全套→更少；故障域region→ring；灾难响应drain一个region→drain环内所有region[p17]
- 提到的公司/客户/产品/标准：FBOSS、ZR+ module、WSS、Raman、ILA、2x400G LR
- 与业界对比或记录声明：无
- 推荐配图页：p16（>10 km 800G ZR+线路系统结构图）；p14（DCN/DCI融合的Regional Fabric环结构）

### 0920-am-Su1-C-00-全场-上半场速记.pdf（第18–26页，BT）
- 讲者/机构：Russell Davey，BT Fellow / Principal Network Architect，BT | 题目：BT Optical Networks for AI | 类型：产业发布
- 方向归属（主/次）：主[1 长途/DCI/AI光网络] / 次[2 Scale-across]
- 核心主张：
  - 目前AI流量在消费者流量中无显著体现，仍以下行视频为主，持续监测；现有光核心网“面向未来”(futureproof)。
  - AI数据中心互联：位置由空间与电力决定，再布光纤；推理约“一波长”级，用现有ROADM网络；训练需scale-across，海量带宽与时延约束。
- 关键数据：
  - BT核心流量>34 Tbit/s（峰值宽带需求）；FTTP覆盖2340万户，2026年底目标2500万户，约£150亿（“£15 billion”）网络投资，40%已覆盖用户接入[p19–p20]
  - 约12,000(~60%)基站直连光纤，10 Gbit/s波长[p21]
  - 网络：106核心站点、1800边缘站点、3600 legacy局站；~18000 cell sites、5600 exchange buildings、1900 Ethernet exchanges、30+ on-net DC；核心/城域 Nx100G与400G光链路，接入侧10G→100G，核心100G→400G[p22]
  - 核心传输演进（示意成本/Gbit/s）：2005 10G，2012 40G，其后100G/200G，2025 400G(400ZR/ZR+进入路由器与转发器)，约2029 800G，2030+可能1.6 Tbit/s，并提问新光纤类型/更多频谱[p25]
  - 训练互联：多光纤×多波长(C+L)，固定滤波器点对点WDM，“光纤岛(optical fibre islands)”，未来在转发器/共封装光学与相干可插拔间选择[p26]
- 提到的公司/客户/产品/标准：BT、Openreach、ROADM、400ZR/ZR+、CPO
- 与业界对比或记录声明：无
- 推荐配图页：p25（相干核心传输演进路线）；p26（AI DC互联训练/推理要求）

### 0920-am-Su1-C-00-全场-上半场速记.pdf（第27–36页，中国电信）
- 讲者/机构：Yuyang Liu，China Telecom | 题目：End-to-End Optimized Optical Networks for AI Infrastructure: An Operator Perspective | 类型：邀请报告
- 方向归属（主/次）：主[1 AI光网络/DCI] / 次[4 OCS/NPO/CPO]、[5 PON/OSU]
- 核心主张：
  - 网络性能已成为AI算力性能一部分：容量、时延、可靠性、灵活性决定GPU利用率、训练效率和服务可用性。
  - AI基础设施需在DCA/DCN/DCI(接入/数据中心网络/互联)三域端到端协同优化，支撑scale-up/out/across。
  - 邀请业界学界加入ITU-T TR.ION-aiDC项目，共同制定首个AIDC标准(面向2030)。
- 关键数据：
  - AI流量占比曲线2023–2033：常规应用流量从约70%+降至约35%；AI相关流量上升，AI-enhanced应用的AI流量到2033约43%左右，Net-new AI应用到2033约18%（读图估值，精度有限）[p29]
  - DCA：PON弹性上行带宽500M–8.7G（50G-PON可至40G）；OSU/M-OTN支持2M–100G细粒度；实网验证时延降低：本地30–50%、城际20–40%、省际8–16%[p32]
  - DCN：OCS实现动态重构，NPO/CPO缩短电通道、降低链路功耗、提高端口密度[p33]
  - DCI：覆盖31省、系统光纤500,000 km、1000+全光调度节点、总网络带宽2000T+；G.654.E光纤，损耗标注约≤0.172 dB/km（字迹略糊）；192芯/288芯光纤；优化路由约降低10%时延；八大算力枢纽占中国智算算力>80%；网络为100G+400G[p34]
  - 50 ms WSON快速保护用于降低故障对AI训练影响，平滑演进现有ROADM网络[p35]；页30另标800G/1.6T、C+L/ROADM、<50 ms WSON等能力要点
- 提到的公司/客户/产品/标准：China Telecom、ITU-T TR.ION-aiDC、OSU/M-OTN、WSON、ROADM、OCS、NPO/CPO、50G-PON、G.654.E
- 与业界对比或记录声明：无
- 推荐配图页：p34（全国ROADM Mesh与光纤基础）；p32（PON/OSU差异化算力接入及时延降低数据）

### 0920-am-Su1-C-02-imec-IClink-欧洲芯片设计平台与MPW.pdf
- 讲者/机构：Thiago Raddo，EuroCDP（EU Chips Design Platform）；封面同时标imec | 题目：Photonics Riding the AI Wave: the role of EuroCDP in the photonics innovation cycle（封面写“ECOC 2027”，原样记录） | 类型：Workshop
- 方向归属（主/次）：主[3 电芯片/光源/调制器（设计生态）] / 次[4 CPO]
- 核心主张：
  - 硅光创新面临大挑战：EDA许可昂贵、融资受限、一次设计成功几乎不可能、多轮流片试错、先进封装门槛、供应链复杂、缺乏标准化[p4]。
  - 代工厂产能吃紧：99%被大玩家占用、仅1%给初创，交期40周成为新常态[p5]。
  - EuroCDP为云端设计平台，降低技术门槛、降低成本门槛、鼓励VC融资[p7]。
- 关键数据：
  - AI基础设施交期从约2021年的约10周升至2025年约40周（读图估值）[p5]
  - 欧洲初创融资约\$800M对美国\$4.7B（2026，来源Dealroom）[p10]
  - 今年79家公司申请EuroCDP的accelerate/incubate项目[p10]
  - 页11为资助方案（含最小/最大补贴），具体金额看不清[p11]
- 提到的公司/客户/产品/标准：NVIDIA、Microsoft、Google、Meta（大玩家）；QBLOX、Vertical Compute、Akronic等入选初创；imec、Fraunhofer、chips-JU
- 与业界对比或记录声明：无
- 推荐配图页：p5（产能瓶颈：99%/1%与40周交期曲线）

### 0920-am-Su1-C-03-STMicro-硅光平台.pdf
- 讲者/机构：Corrado Sciancalepore，Silicon Photonics Business Unit，STMicroelectronics | 题目：Fostering industrial scalability and fast innovation with STMicroelectronics silicon photonics solutions | 类型：产业发布
- 方向归属（主/次）：主[3 Scale-out 224G/448G/光源/调制器/电芯片] / 次[4 NPO/CPO]
- 核心主张：
  - AI基础设施是多年增长催化剂；可用电力与可达算力决定I/O网络需求。
  - ST PIC100与BiCMOS B55X 300mm平台已高量产，并向NPO/CPO与异质集成延伸。
  - “Golden Blend”：高良率量产 + IDM封装能力 + 研发合作(STARLight)，以加速光子创新。
- 关键数据：
  - Grok4(xAI)训练用>200K计算节点；Meta 5GW Hyperion DC规模覆盖曼哈顿[p2]
  - PIC100与B55X：300mm高量产，2027年产能扩至4倍；2031年前350M+硅光端口；TSV在PIC100与B55X上可用，面向NPO/CPO[p4]
  - PIC100：调制器带宽>50+ GHz；光电探测器带宽>80+ GHz、200G+/lane Rx合规、适合400G/lane Rx；边缘耦合损耗<1 dB、PDL可忽略、波长跨度>100 nm；低损耗Si/SiN线路用于DR/FR收发器；长期路线通过电光集成与异质材料实现400G/lane[p7]
  - 硅光平台“唯一硅基300mm，支撑200G/lane”；封装结构PIC+EIC(B55X)+MCU(STM32)+TSV+微光学；提供协同设计环境、紧凑调制器、TSV、bumping、封装与测试[p8]
  - CMOS级光子良率>90%[p9]
- 提到的公司/客户/产品/标准：ST PIC100、BiCMOS B55X、STM32、AWS（“借助AWS超大规模领先地位推动创新与量产”）、TosaHop(Innolight)（页6致谢）、xAI Grok4、Meta、STARLight、OCI路线图
- 与业界对比或记录声明：“industry-leading silicon photonics platform”（厂商自述）[p4]
- 推荐配图页：p7（PIC100三项硅创新及带宽/耦合损耗指标）；p8（PIC+EIC+MCU先进封装结构）

### 0920-am-Su1-C-05-Tyndall-封装在产品化中的角色.pdf
- 讲者/机构：未见讲者名，Tyndall National Institute | 题目：（封面题目文字OCR乱码，主题为封装在光子产品化中的角色；页2标题“Why is packaging so important?”） | 类型：Workshop
- 方向归属（主/次）：主[4 CPO/封装] / 次[3]
- 核心主张：
  - 封装是产品与外界的连接，装好后才开始真实评估；应早期介入，封装是产品架构的一部分。
  - 用标准与设计规则加速，采用HVM语言，“英雄式”原型是虚假经济，需在快与智之间平衡；尽早完成面向制造与测试的设计，尽早和制造伙伴反馈。
- 关键数据：
  - 封装可占总成本50–80%；成本饼图中封装/装配/测试合计约80%[p4]
  - 从概念、原型、修订到试产存在“死亡之谷”（资金/资源低谷），需稳定工艺、了解良率、评估可靠性、开发测试、建立文档与供应链；PIXEurope可支持工艺开发[p5]
  - 页7提到Tyndall新活动“CONNECT / connecting chips”，工作在电子与光子接口，弥合原型到量产的差距[p7]
- 提到的公司/客户/产品/标准：PIXEurope、OSAT、Connect Semiconductor（页7标识）
- 与业界对比或记录声明：无
- 推荐配图页：p4（封装成本占比饼图与50–80%结论）

### 0920-am-Su2-C-01-Cadence-光电协同设计.pdf
- 讲者/机构：未见讲者名，Cadence；案例作者为Yonsei University & Cadence | 题目：（无标题页；主题为电光协同设计；案例论文A 4-λ × 32-Gb/s Silicon Micro-Ring-Resonator-Based DWDM Receiver with On-Chip Temperature Controller） | 类型：Workshop
- 方向归属（主/次）：主[3 电芯片/调制器（设计）] / 次[4 CPO]
- 核心主张：
  - 应尽早（When）、跨团队（Who）、跨流程（How）地把光子与电子设计放在一起，而非事后补救。
  - 电路仿真至关重要，需做电子-光子联合仿真；传统SPICE不懂光子、光子工具缺电子，流程零散。
- 关键数据：
  - 案例：4波长×32 Gb/s硅微环(MRR) DWDM接收机，片上温度控制器自动对准并锁定每个MRR到目标波长；用Cadence光学频率分析(OFA)做联合仿真；仿真与实测的drop/thru端口传输谱、控制电压VM/VH时序曲线对应；热应力实验下有控制器时CH1–CH4眼图张开，无控制器时眼图闭合，测试条件为32 Gb/s PRBS-23累积眼图，台面温度约在16–32 °C间正弦变化（读图估值）[p6–p7]
  - 页中标记“Monday”，指该论文在会议周一发表（原样）
- 提到的公司/客户/产品/标准：Cadence、Yonsei University
- 与业界对比或记录声明：无
- 推荐配图页：p7（有/无温控的4通道32 Gb/s眼图对比）

### 0920-am-Su2-C-02-Luceda-面向良率的电路设计.pdf
- 讲者/机构：Pierre Wahl，Head of Technology and Research，Luceda Photonics | 题目：Photonic circuit design for manufacturing and yield | 类型：Workshop
- 方向归属（主/次）：主[3 调制器/光源（设计与良率）] / 次[4 CPO]
- 核心主张：
  - 从可插拔走向CPO需要设计-技术协同优化(DTCO：新材料+异质集成、更高每通道带宽)与系统-技术协同优化(光学更靠近电子，性能增益在系统层面)。
  - 通过仿真配方(Simulation Recipes)与测试键(Test Keys)验证，并用Nexus数据分析与Circuit Analyzer做含工艺波动的电路仿真，估计可行性。
- 关键数据：
  - 收发器速率：2005约10G、2010约40G、2015约100G、2020约400G、2025约800G/1.6T；达到1000万件/年所需年数：10G 15年、100G 10年、400G 8年、1.6T 4年[p3]
  - 工艺变动量：刻蚀深度±1 nm、线宽±5 nm的角点分析（Best/Worst case），示例电路为4端口开关，S参数在1.50–1.60 µm，范围至约-100 dB[p11]
  - Circuit Analyzer示例：4x4 Benes、Spanke-Benes、PILOSS开关，考虑刻蚀深度、有效折射率、线宽、温度、应力[p10]
  - 引用仿真伙伴：Ansys、Dassault Systemes、Flexcompute、Max-Optics[p5]
- 提到的公司/客户/产品/标准：Luceda IPKISS、DRC、Nexus(Data Hive / Data Explorer)、Circuit Analyzer；Ansys、Dassault、Flexcompute、Max-Optics
- 与业界对比或记录声明：无
- 推荐配图页：p3（收发器速率与达产年数：4年到1000万件/年）

### 0920-am-Su2-C-03-GhentImec-可编程光子做原型.pdf
- 讲者/机构：未见讲者名，Ghent University–imec（NOVA论文作者Yu Zhang, Xiangfeng Chen, Lukas Van Iseghem, Iman Zand, Hasan Salmanian, Antonio Ribeiro, Wim Bogaerts） | 题目：（封面OCR乱码；主题为Programmable photonics for prototyping，ECOC 2026, Malaga, 20 Sept 2026） | 类型：Workshop
- 方向归属（主/次）：主[3 调制器/光源（原型平台）] / 次[6 传感]
- 核心主张：
  - 新光子产品从想法到产品需6–7年；一次原型周期1–2年（设计6–9个月、晶圆制造6个月、测试封装6个月），通常需3–4个原型周期。
  - 用软件可配置的“光子FPGA”跳过慢速芯片制造周期，快速迭代。
  - 局限：类似电子FPGA，适合快速原型、灵活仪表、中低量产品；极端性能(带宽、低功耗、低损耗)与大批量低成本不适合。
- 关键数据：
  - NOVA：7单元六边形可编程光子芯片，FSR>30 GHz（单环配置：谱线间隔31 GHz/0.25 nm，谐振线宽约30 pm）；另有三环配置，论文doi:10.1002/lpor.202502270[p8]
  - 应用示例：激光器频率调制表征(ECIO2026)、微波相控阵光波束成形网络(PSC2026)[p10–p11]
  - 衍生公司WAYFLOWER（暂用名）：预计2026年底注册，首日销售NOVA，2027年寻求种子轮（页标“Confidential”）[p15–p16]
- 提到的公司/客户/产品/标准：NOVA、Wayflower；EDA厂商Luceda、Synopsys、Cadence、Keysight等及各类代工厂（页14）
- 与业界对比或记录声明：无
- 推荐配图页：p4（6–7年产品化时间线）；p8（NOVA芯片与单环/三环谱）

### 0920-am-Su2-C-04-BrightPhotonics-快速原型板.pdf
- 讲者/机构：未见讲者名，页脚为VLC Photonics, S.L.（a Hitachi Group Company）；文件名标Bright Photonics | 题目：（无明确题目页；议程为Why Photonic Integration / Idea-to-Product Map / Walking the Stages / Why Products (and Startups) Stall） | 类型：Workshop
- 方向归属（主/次）：主[3 调制器/光源（PIC产品化）] / 次[4 CPO]
- 核心主张：
  - PIC产品化沿着电子学数十年前的路径（分立微光学→集成），模仿CMOS的fabless、EDA、设计公司与IP、通用工艺、封装测试标准。
  - 第一周做的决定最难也最贵逆转：材料平台、商业模式、通用vs定制、MPW vs专用流片；多数首颗PIC采用“通用工艺+MPW”。
  - 一个能工作的PIC必要但不充分：还需说服投资人、团队、网络与IP。
- 关键数据：
  - 封装可占产品总成本>60%，常被最后才规划[p10]
  - 开发周期18–36个月，相对许多产品路线图偏长[p12]
  - 产品受阻因素：设计-流片迭代过多、封装被低估、从MPW到量产的跳跃、追求无人买单的性能、竞争技术更快、市场窗口关闭、无降成本路径[p11–p12]
- 提到的公司/客户/产品/标准：VLC Photonics、Luceda、Synopsys（TDK/EDA页）、SOI/SiN/InP/TFLN/聚合物平台
- 与业界对比或记录声明：无
- 推荐配图页：p11（产品与初创受阻的技术/商业陷阱）

## 本批小结
1. 运营商与云厂商的DCI差异化：OVHcloud（Fazel）用“<10 km无线路系统的2x400G LR直连纤芯 + >10 km 800G ZR+线路系统”构建区域环，BT（Davey）认为核心演进约2029年达800G、2030+讨论1.6T，训练互联用固定滤波WDM+C/L多纤“光纤岛”，中国电信（Liu）则以ROADM/WSON全光网络+50 ms保护为基础。来自速记 OVHcloud、BT、中国电信三讲。
2. “网络性能=算力性能”成为共识：中国电信明确网络KPI映射GPU利用率与训练效率，ITU ION-2030把AI需求转为低时延低抖动高可用要求，并推动TR.ION-aiDC标准项目。来自速记 ITU与中国电信。
3. DCN/DCI边界模糊：OVHcloud的区域Fabric环（环内容量为环间10倍）、BT的scale-across、中国电信的OCS/NPO/CPO与DCI并列，说明园区级跨楼互联成为独立架构层。来自速记 OVHcloud、BT、中国电信。
4. 硅光产业化重点从器件转向良率、封装与生态：ST强调300mm双平台、良率>90%、2027年4倍扩产与2031年350M+端口，Tyndall与VLC均指出封装占成本50–80%或>60%，Luceda以工艺角点分析做面向良率设计。来自ST、Tyndall、Luceda、VLC/Bright。
5. 原型周期与设计生态是欧洲初创瓶颈：Ghent/imec指出产品化6–7年、3–4轮原型，EuroCDP指出代工交期约40周、99%产能被大厂占用、欧洲初创融资约\$800M对美国\$4.7B，Cadence提倡电光协同仿真（4×32 Gb/s MRR DWDM接收机案例）。来自Ghent-imec、imec/EuroCDP、Cadence。
6. 可编程光子（光子FPGA）定位清晰：适合原型、仪表与中低量产品，不适合极致性能与大批量（NOVA FSR>30 GHz）。来自Ghent-imec。
