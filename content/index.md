---
title: Welcome to SpringCatalpa
---

![[Gemini_Generated_Image_d2jn7od2jn7od2jn.jpeg]]                                Diligently, tirelessly and endlessly growing

<div class="topic-cards">
<a class="topic-card" href="#一-专题optical-communication-光通信">
<img src="attachments/banner-paris.jpg" alt="Paris panorama from Tour Montparnasse" />
<span class="tc-title">Optical Communication</span>
<span class="tc-credit">Paris · Stefan Krause · CC BY-SA 3.0</span>
</a>
<a class="topic-card" href="#二-专题无线与wifi通信">
<img src="attachments/banner-stockholm.jpg" alt="Stockholm City Hall across Riddarfjärden at dusk" />
<span class="tc-title">Wireless Communication</span>
<span class="tc-credit">Stockholm · Richard Maack · CC BY 4.0</span>
</a>
</div>



### 一. [[Optical Communication/index|专题：Optical Communication 光通信]]

#### 1. [[Optical Communication/01. Conference/2026 ECOC/index|洞察：2026年 ECOC 专题洞察]]

ECOC 2026（Málaga，9 月 20–24 日），445 篇讲稿笔记。另见 [[Optical Communication/01. Conference/2026 ECOC/00. ECOC 2026的十条技术判断|十条跨方向技术判断]] · [[Optical Communication/01. Conference/2026 ECOC/专题洞察/2026 光互连五大专题深度洞察|五大专题深度洞察]] · [[Optical Communication/01. Conference/2026 ECOC/专题洞察/ECOC 2026 全量技术洞察（六大方向）|ECOC 2026 全量技术洞察（六大方向，52 页）]]（Scale Across、OpenAI 芯片、NVIDIA×iPronics OCS、Slow & Wide、Cerebras CS-4 与光学晶圆级）。

**1. 光通信应用场景专题洞察**

| 场景 | 范围 | 关键结论 |
|---|---|---|
| [[Optical Communication/02. DataCenterNetwork/02. Scale across/index\|Scale Across]] | 跨楼/园区/区域 DC 互连 | 部署单位从“波长”变成“光纤对”：相干可插拔管单波长成本，全谱转发器（FST）+ 多 rail 线路系统管规模；瓶颈已从模块转到线路系统、光纤数量和散热。 |
| [[Optical Communication/02. DataCenterNetwork/01. Scale out/index\|Scale Out]] | 224G/448G、光源、调制器、OCS | 200G/lane 已现网放量（LPO/LRO/FRO 并存，十万量级链路）；400G/lane 多条路线都只到样机，约束转到电通道（约 90 GHz）、O 波段色散和接收端，尚无胜出路线。 |
| [[Optical Communication/02. DataCenterNetwork/00. Scale up/index\|Scale Up]] | CPO/NPO/XPO、晶圆级光 I/O | 分歧不在“光能不能做”，而在“谁承担可维护性”：NPO 与可插拔 XPO 抢 2026–27 窗口，CPO 在 scale-up 要到 2027/28；宽而慢（VCSEL/microLED）缺现场可靠性数据。 |
| [[Optical Communication/05. TransmissionNetwork/index\|Transport]] | 相干、海缆、长途、DCI、空芯光纤 | 相干的竞争轴从峰值波特率转向按距离切分的产品族（1600ZR/ZR+/Coherent-Lite）；长途扩容靠空芯光纤、多波段和 SDM；海缆容量被供电而非光学锁死。 |
| [[Optical Communication/07. AccessNetwork/index\|Access]] | PON、FTTR、RoF、FSO/星地 | 两条时间轴：50G PON + FTTR + AI-FAN 是 2026–2030 的商用主线；100/200G VHSP 三条路线并存，2027–28 选型、2035 前后商用。 |
| [[Optical Communication/09. New Applications/index\|新应用]] | QKD/量子网络、光纤感知 | 光纤感知复用现网相干收发机和在役海缆，已进入标准化（G.681）与运维验证；量子网络速率仍在 0.1–1 Hz 量级，现网价值在于验证与经典业务共纤。 |

%% ecoc2026-二级专题 start %%
**二级专题导航**（点专题名进入 ECOC 2026 报告索引对应小节）

| 场景 | 二级专题（报告数） |
|---|---|
| [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引\|Scale Across]] | [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引#产业需求\|产业需求 10]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引#FST与Multi-Rail\|FST与Multi-Rail 6]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引#ZR、ZR+、CL\|ZR/ZR+/CL 6]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引#低功耗DSP\|低功耗DSP 3]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引#高波特率器件\|高波特率器件 1]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引#光源\|光源 0]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引#新型光纤介质\|新型光纤介质 4]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Across 报告索引#星地FSO链路\|星地FSO链路 7]] |
| [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引\|Scale Out]] | [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引#调制器\|调制器 9]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引#光DSP\|光DSP 11]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引#电SerDes及连接器\|电SerDes及连接器 10]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引#OCS\|OCS 8]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引#光源\|光源 10]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引#探测器与接收\|探测器与接收 4]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引#集成平台与无源器件\|集成平台与无源器件 11]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Out 报告索引#链路与系统\|链路与系统 12]] |
| [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Up 报告索引\|Scale Up]] | [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Up 报告索引#光源\|光源 4]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Up 报告索引#Narrow&Fast\|Narrow&Fast 3]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Up 报告索引#Slow&Wide\|Slow&Wide 16]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Up 报告索引#SerDes及连接器\|SerDes及连接器 11]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Up 报告索引#异质集成\|异质集成 2]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Scale Up 报告索引#架构与系统\|架构与系统 41]] |
| [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引\|Transport]] | [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#HCF\|HCF 31]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#AI光网络\|AI光网络 30]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#光系统建模\|光系统建模 1]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#高波特率器件\|高波特率器件 10]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#光放与多波段\|光放与多波段 8]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#SDM光纤\|SDM光纤 9]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#相干DSP与编码\|相干DSP与编码 29]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#光网络架构与控制\|光网络架构与控制 16]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Transport 报告索引#光纤与测试\|光纤与测试 4]] |
| [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Access 报告索引\|Access]] | **固定接入**：[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Access 报告索引#50G PON\|50G PON 4]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Access 报告索引#Beyond 50G PON\|Beyond 50G PON 35]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Access 报告索引#AI-FAN\|AI-FAN 18]]；**移动接入**：[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Access 报告索引#RoF\|RoF 9]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Access 报告索引#FSO\|FSO 7]]；**其他**：[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/Access 报告索引#其他接入\|其他接入 2]] |
| [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/新应用 报告索引\|新应用]] | [[Optical Communication/01. Conference/2026 ECOC/方向报告索引/新应用 报告索引#DAS、光纤感知\|DAS/光纤感知 19]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/新应用 报告索引#QKD、量子\|QKD/量子 12]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/新应用 报告索引#光计算\|光计算 0]]、[[Optical Communication/01. Conference/2026 ECOC/方向报告索引/新应用 报告索引#其他新应用\|其他新应用 1]] |
%% ecoc2026-二级专题 end %%

**2. 光通信产业链企业专题洞察**

代表企业后的数字 = ECOC 2026 主讲报告数 / 被提及次数，点企业名看它的全部报告。

| 层次 | 代表企业 | 核心趋势判断 |
|---|---|---|
| [[Optical Communication/08. Industry Chain/00.AIDC Custom/ECOC2026 厂商索引 · AIDC客户\|AIDC客户]] | [[Optical Communication/08. Industry Chain/00.AIDC Custom/ECOC2026 厂商索引 · AIDC客户#Microsoft · Azure\|Microsoft · Azure]] 13/21、[[Optical Communication/08. Industry Chain/00.AIDC Custom/ECOC2026 厂商索引 · AIDC客户#Oracle OCI\|Oracle OCI]] 10/1、[[Optical Communication/08. Industry Chain/00.AIDC Custom/ECOC2026 厂商索引 · AIDC客户#Meta\|Meta]] 4/18、[[Optical Communication/08. Industry Chain/00.AIDC Custom/ECOC2026 厂商索引 · AIDC客户#Google\|Google]] 2/19、[[Optical Communication/08. Industry Chain/00.AIDC Custom/ECOC2026 厂商索引 · AIDC客户#OpenAI\|OpenAI]] 4/8 | 需求端在定规则：选型看功耗、TCO 和可维护性；scale-across 的部署单位变成光纤对；LPO 已有十万量级现网链路（Oracle、阿里云），CPO 处于“先试用”；Microsoft 是空芯光纤最积极的推动者。 |
| [[Optical Communication/08. Industry Chain/02.CT Custom/ECOC2026 厂商索引 · 运营商客户\|运营商客户]] | [[Optical Communication/08. Industry Chain/02.CT Custom/ECOC2026 厂商索引 · 运营商客户#NTT\|NTT]] 17/7、[[Optical Communication/08. Industry Chain/02.CT Custom/ECOC2026 厂商索引 · 运营商客户#中国电信\|中国电信]] 8/0、[[Optical Communication/08. Industry Chain/02.CT Custom/ECOC2026 厂商索引 · 运营商客户#Orange\|Orange]] 5/5、[[Optical Communication/08. Industry Chain/02.CT Custom/ECOC2026 厂商索引 · 运营商客户#KDDI\|KDDI]] 5/1、[[Optical Communication/08. Industry Chain/02.CT Custom/ECOC2026 厂商索引 · 运营商客户#Deutsche Telekom\|Deutsche Telekom]] 4/1 | 接入网两条时间轴（50G PON + FTTR 现网商用，VHSP 2027–28 选型）；空芯光纤进入现网（中国移动两年无退化）；在役光纤变成传感器（G.681）；中国电信推 AIDC 三域协同。 |
| [[Optical Communication/08. Industry Chain/03.Venders/ECOC2026 厂商索引 · 设备商\|设备商]] | [[Optical Communication/08. Industry Chain/03.Venders/ECOC2026 厂商索引 · 设备商#Nokia\|Nokia]] 50/15、[[Optical Communication/08. Industry Chain/03.Venders/ECOC2026 厂商索引 · 设备商#Ciena\|Ciena]] 20/10、[[Optical Communication/08. Industry Chain/03.Venders/ECOC2026 厂商索引 · 设备商#华为\|华为]] 20/9、[[Optical Communication/08. Industry Chain/03.Venders/ECOC2026 厂商索引 · 设备商#Arista\|Arista]] 12/2、[[Optical Communication/08. Industry Chain/03.Venders/ECOC2026 厂商索引 · 设备商#Cisco\|Cisco]] 6/10 | 价值集中到线路系统和全谱转发器：rail 数、站点电力、泵浦供给成为新规格；相干按距离分档成产品族；交换机要尽早定下 OCI/XPO/NPO/CPO 的混合比例。 |
| [[Optical Communication/08. Industry Chain/04.Component/ECOC2026 厂商索引 · 模块与器件商\|模块与器件商]] | [[Optical Communication/08. Industry Chain/04.Component/ECOC2026 厂商索引 · 模块与器件商#长飞 YOFC\|长飞 YOFC]] 11/6、[[Optical Communication/08. Industry Chain/04.Component/ECOC2026 厂商索引 · 模块与器件商#Coherent\|Coherent]] 7/14、[[Optical Communication/08. Industry Chain/04.Component/ECOC2026 厂商索引 · 模块与器件商#Lumentum\|Lumentum]] 3/15、[[Optical Communication/08. Industry Chain/04.Component/ECOC2026 厂商索引 · 模块与器件商#Corning\|Corning]] 4/10、[[Optical Communication/08. Industry Chain/04.Component/ECOC2026 厂商索引 · 模块与器件商#Acacia（Cisco）\|Acacia（Cisco）]] 4/9 | 交付物从单个模块变成“光引擎 + 连接器 + 可测试性 + 遥测”；光源成为独立子系统（ELS）；InP/SOI 晶圆和泵浦激光是供给约束；空芯光纤的瓶颈转到产能和价格。 |
| [[Optical Communication/08. Industry Chain/05.Chips/ECOC2026 厂商索引 · 芯片商\|芯片商]] | [[Optical Communication/08. Industry Chain/05.Chips/ECOC2026 厂商索引 · 芯片商#NVIDIA\|NVIDIA]] 11/38、[[Optical Communication/08. Industry Chain/05.Chips/ECOC2026 厂商索引 · 芯片商#Marvell\|Marvell]] 14/7、[[Optical Communication/08. Industry Chain/05.Chips/ECOC2026 厂商索引 · 芯片商#Broadcom\|Broadcom]] 3/22、[[Optical Communication/08. Industry Chain/05.Chips/ECOC2026 厂商索引 · 芯片商#iPronics\|iPronics]] 6/1、[[Optical Communication/08. Industry Chain/05.Chips/ECOC2026 厂商索引 · 芯片商#Intel\|Intel]] 0/14 | 200G/400G 世代能效的主导项是 SerDes，400G/lane 的上限在电通道（约 90 GHz）；相干 DSP 走向 2 nm 并集成 MACsec 与园区低时延 FEC；光域均衡、光 DAC 成熟后会压缩 DSP 的价值占比。 |
| [[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业\|初创企业 TOP30]] | [[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业#iPronics\|iPronics]] 6/1、[[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业#领纤 Linfiber\|领纤 Linfiber]] 3/5、[[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业#Xscape Photonics\|Xscape Photonics]] 3/0、[[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业#Lightmatter\|Lightmatter]] 2/2、[[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业#Polariton\|Polariton]] 2/1、[[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业#TeraHop\|TeraHop]] 2/1、[[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业#HyperLight\|HyperLight]] 2/0、[[Optical Communication/08. Industry Chain/06.Startups/ECOC2026 厂商索引 · 初创企业#Oriole Networks\|Oriole Networks]] 2/0 | 出现 47 家，TOP30 中 21 家的报告落在 Scale Out/Up：多波长光源（Xscape、Photon Bridge、Quintessent）、光交换与可编程光子（iPronics、Oriole、Salience、Lightmatter）、新调制材料（Polariton、HyperLight）、新介质（AttoTude、TeraHop）；Transport 只有空芯光纤（领纤）。多数仍是样机，窗口在 scale-up 形态定型前的 2026–2028。 |

另见：[[Optical Communication/01. Conference/2026 ECOC/01.  ECOC厂商地图与与技术方向|厂商地图与技术方向]] · [[Optical Communication/08. Industry Chain/ECOC2026 分析机构与标准组织|分析机构与标准组织]]

**3. 光通信研究机构专题洞察**

[[Optical Communication/10. Research Institutes/高校与研究机构索引|高校与研究机构索引]]：100 家机构、175 篇报告。下表是场景 × 技术层的交叉分布，点数字进入对应小节。

| 场景 | 网络 | 光系统 | 算法 | 器件 | 芯片 | 合计 |
|---|---|---|---|---|---|---|
| [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Across\|Scale Across]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Across · 网络\|1]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Across · 光系统\|6]] | – | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Across · 器件\|1]] | – | 8 |
| [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Out\|Scale Out]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Out · 网络\|1]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Out · 光系统\|1]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Out · 算法\|9]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Out · 器件\|12]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Out · 芯片\|7]] | 30 |
| [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Up\|Scale Up]] | – | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Up · 光系统\|1]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Up · 算法\|1]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Up · 器件\|2]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Scale Up · 芯片\|5]] | 9 |
| [[Optical Communication/10. Research Institutes/高校与研究机构索引#Transport\|Transport]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Transport · 网络\|13]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Transport · 光系统\|10]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Transport · 算法\|25]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Transport · 器件\|22]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Transport · 芯片\|1]] | 71 |
| [[Optical Communication/10. Research Institutes/高校与研究机构索引#Access\|Access]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Access · 网络\|6]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Access · 光系统\|15]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Access · 算法\|14]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#Access · 器件\|2]] | – | 37 |
| [[Optical Communication/10. Research Institutes/高校与研究机构索引#新应用\|新应用]] | – | [[Optical Communication/10. Research Institutes/高校与研究机构索引#新应用 · 光系统\|15]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#新应用 · 算法\|2]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#新应用 · 器件\|2]] | [[Optical Communication/10. Research Institutes/高校与研究机构索引#新应用 · 芯片\|1]] | 20 |
| **合计** | **21** | **48** | **51** | **41** | **14** | **175** |

**TOP5 核心研究趋势**

1. **空芯光纤从“损耗纪录”走向“系统与现网”**（Transport · 器件/光系统）：零色散、电信级损耗的 C 波段空芯光纤（Microsoft + 南安普顿），532 km 无中继全 C 波段（Nokia Bell Labs + ASN + 长飞），2024 km 双向 O+C 传输（UCL）。研究重心已转到气体吸收线、熔接和 OTDR/OFDR 表征。
2. **智能化落进 DSP 与网络控制**（Transport · 算法 25 篇，是矩阵里最大的一格；网络 13 篇）：纵向功率监测、非线性干扰估计、神经概率整形、超网络 DSP 在 DSP 里实现（NICT、AIST、UCL、华南理工）；LLM 智能体与数字孪生做故障诊断和业务开通（北邮、米兰理工、Trinity），目前仍是原型。
3. **400G/lane IM-DD 与“去 DSP 化”**（Scale Out · 算法 + 器件 21 篇）：单调制器单 PD 的 440 GBd PAM6 净速率超过 800G（上海科技大学 + Bell Labs），432 Gb/s/λ 硅光全光均衡（香港中文大学），光 DAC（ETH），光域处理替代 DSP（NICT）。
4. **相干 PON 与 VHSP 从仿真走向实验和现场**（Access · 光系统 + 算法 29 篇）：300G 相干 TDM-PON 首次现场试验（上海交大 + 中国电信），实时 FPGA 突发模式相干 PON（复旦），数字色散预补偿（都灵理工），双向 200G 的瑞利背散影响（Fraunhofer HHI）。
5. **光纤变成传感器和量子信道**（新应用 · 光系统 15 篇）：688 km 有中继链路上 DAS 与 15 Tb/s 业务共传（帕多瓦 + NICT），城域量子中继（中科大），单片 QKD 发射机（AIT），海缆偏振传感（L'Aquila、都柏林圣三一）。

#### 2. [[Optical Communication/01. Conference/2026 OFC/index|洞察：2026年 OFC 论文专题洞察]]

OFC 2026（洛杉矶，2026 年 3 月 15–19 日），本目录收录 707 篇论文（含 24 篇 Postdeadline、16 篇 Demo、158 篇海报）。

**1. 六大场景关键结论**

| 场景 | 关键结论 |
|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|Scale Across（15）]] | 跨 DC 训练从经济性论证走向现网：1024 GPU 跨 600 km 多 AIDC 训练 LLaMA2-70B，DP/PP 效率损失 <5%/<1%〔W4H.5〕；DCI 单波进入 1.2T（S+C+L 134 Tb/s，全部通道 1.276 Tb/s〔W3J.1〕）；coherent-lite 靠光梳共享载波/时钟做波特率采样〔Th4C.8〕，BTO DP-IQM 单波净 1 Tb/s（ZR 80 km）〔Th3J.4〕。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|Scale Out（157）]] | 400G/lane 进入多平台 PDP 竞速：硅 MZM〔Th4A.4〕、BTO 1.6T DR4〔Th4B.3〕、膜 EA-DFB 448G〔Th4A.1〕、TFLT 768 Gb/s〔Th4A.2〕、TFLN TOSA 420G〔W4J.4〕、差分 EML〔Tu3J.6〕并存，尚无胜者；1.6T 2×FR4 单片硅光满足 802.3dj〔Th4A.7〕。OCS 走向可用：4096×4096 单层 819.2 Tb/s〔M3F.3〕，训练重构快 37.5%〔M3F.5〕，推理需 <700 ns〔W2A.28〕；百万级光模块现网故障数据出现〔Th3B.2〕。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|Scale Up（35）]] | CPO 关注点从器件转到“系统可靠性 + 外置光源”：8 通道 >+25 dBm ELS〔W1B.3〕、500 mW PCSEL〔W4E.2〕、3D 堆叠 EIC/PIC 光 I/O 1.33 Tb/s/mm²〔M4B.2〕、玻璃基板与 AWGR 光学中介层〔Th3C.2、Th3C.1〕、TFLN 晶圆级 CPO 引擎〔Th4A.6〕；光域 AllReduce〔M4F.3、Th3H.3〕与 THz 介质波导互连〔Th1A.1〕是新候选。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|Transport（225）]] | 单模光纤带宽拓到 OESCL 42.4 THz、>450 Tb/s〔Th4B.5〕；实时 2.5 Pb/s 24 芯〔Th3A.2〕；空芯光纤 0.040 dB/km〔M2J.1〕、266 km 超长跨段跨洋 21.7 Tb/s〔Th4B.7〕、单芯 550.97 Tb/s〔Th1J.6〕；相干可插拔 400G/λ × 5682 km 海缆〔Th4C.6〕、800G 多厂商互通 1602 km〔Th4B.6〕；网络智能化出现垂直大模型 Optics GPT〔Th4C.1〕与 OSFP 内实时纵向功率监测〔Th4B.4〕。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|Access（147）]] | 相干 PON 独立成场：首个双向 200G TFDM 相干 PON 现场试验〔Th4C.4〕、非制冷 DFB 突发上行 37 dB〔Th4C.3〕、统一 OLT 兼容相干与 IM-DD ONU〔W1I.4〕；THz 单链路 600 Gb/s〔M4H.6〕、312 GHz 3 km 现场〔M4H.7〕；卫星光网络路由/切换成独立 Session（Tu3F），飞机–GEO 激光链路首批结果〔Th4B.1〕；光无线 516 Tb/s〔M3H.3〕。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|新应用（128）]] | 海缆感知规模化：4400 km 海缆 8.8 万个 50 m 测点〔Th4C.7〕，585 km 中继链路 DAS 与 15.8 Tb/s 共传〔M4J.6〕，sub-pε/√Hz 通感一体〔W4C.6〕；QKD 与 374.4 Tb/s 经典业务在 100 km 7 芯光纤共存〔M2K.2〕、集成 CV-QKD 538 Mb/s〔M1K.2〕、QKD 无改造进入 32 用户 PON〔W3K.3〕；光计算做到 212 GOPS 光子 Ising 机〔W3C.2〕。 |

**2. 二级专题导航**（点专题名进入对应小节）

| 场景 | 二级专题（论文数） |
|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|Scale Across]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#产业需求\|产业需求 6]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#FST与Multi-Rail\|FST与Multi-Rail 2]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#ZR、ZR+、CL\|ZR/ZR+/CL 1]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#低功耗DSP\|低功耗DSP 1]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#高波特率器件\|高波特率器件 3]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#光源\|光源 1]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#新型光纤介质\|新型光纤介质 1]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|Scale Out]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#调制器\|调制器 50]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#光DSP\|光DSP 22]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#电SerDes及连接器\|电SerDes及连接器 5]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#OCS\|OCS 15]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#光源\|光源 15]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#探测器与接收\|探测器与接收 12]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#集成平台与无源器件\|集成平台与无源器件 33]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#链路与系统\|链路与系统 5]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|Scale Up]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#光源\|光源 8]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#Narrow&Fast\|Narrow&Fast 3]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#Slow&Wide\|Slow&Wide 7]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#SerDes及连接器\|SerDes及连接器 6]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#异质集成\|异质集成 2]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#架构与系统\|架构与系统 9]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|Transport]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#HCF\|HCF 30]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#AI光网络\|AI光网络 56]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#光系统建模\|光系统建模 12]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#高波特率器件\|高波特率器件 12]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#光放与多波段\|光放与多波段 30]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#SDM光纤\|SDM光纤 22]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#相干DSP与编码\|相干DSP与编码 23]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#光网络架构与控制\|光网络架构与控制 31]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#光纤与测试\|光纤与测试 9]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|Access]] | **固定接入**：[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#50G PON\|50G PON 3]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#Beyond 50G PON\|Beyond 50G PON 21]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#AI-FAN\|AI-FAN 17]]；**移动接入**：[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#RoF\|RoF 55]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#FSO\|FSO 51]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|新应用]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引#DAS、光纤感知\|DAS/光纤感知 59]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引#QKD、量子\|QKD/量子 44]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引#光计算\|光计算 18]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引#其他新应用\|其他新应用 7]] |

**3. 场景 × 技术层分布**

| 场景 | 网络 | 光系统 | 算法 | 器件 | 芯片 | 合计 |
|---|---|---|---|---|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|Scale Across]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|7]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|3]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|1]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|2]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|2]] | 15 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|Scale Out]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|13]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|6]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|23]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|60]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|55]] | 157 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|Scale Up]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|10]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|1]] | – | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|8]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|16]] | 35 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|Transport]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|45]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|26]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|83]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|61]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|10]] | 225 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|Access]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|31]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|55]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|25]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|13]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|23]] | 147 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|新应用]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|11]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|62]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|16]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|11]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|28]] | 128 |
| **合计** | **117** | **153** | **148** | **155** | **134** | **707** |

**4. TOP5 核心趋势**

1. **AI 集群成为第一驱动力**：Scale Out/Up/Across 合计 207 篇（29%）。“AI/计算集群光互连”主题占比从 ECOC 2025 的 1.7% 升到 5.0%；出现 1024 GPU 跨 600 km 训练现网〔W4H.5〕、百万级光模块故障数据〔Th3B.2〕这类运营数据论文。
2. **400G/lane 没有单一胜者**：Scale Out · 器件/芯片 115 篇：硅 MZM、BTO、TFLN、TFLT、膜 EA-DFB、差分 EML、等离子体环、铁电玻璃都做到 ≥400G；决定因素转向驱动/SerDes 协同与 LPO/NPO/CPO 封装形态〔W1D.7〕。
3. **空芯光纤进入系统工程**：Transport：损耗 0.040 dB/km〔M2J.1〕、266 km 跨段跨洋〔Th4B.7〕、双窗口 0.11/0.13 dB/km〔Th4B.8〕；气体吸收、IMI、熔接、OTDR 与网络部署优化成体系出现（Th1J、Tu3E、M1J、M2J 四个 Session）。
4. **光网络的“自治闭环”成型**：Transport · 网络 + 算法 128 篇：数字孪生 + LLM 多智能体 + 纵向功率监测；两场生成式 AI 研讨会〔W3I.1、W4I.1〕，Optics GPT〔Th4C.1〕，LPM 进入可插拔 DSP〔Th4B.4〕。
5. **光纤感知与量子走向“可运营”**：新应用 · 光系统 62 篇：海缆 DAS 8.8 万测点〔Th4C.7〕、通感一体共传；QKD 与数百 Tb/s 经典业务同芯共存〔M2K.2〕、进入 PON 与 ROADM 链路，QKDN 讨论标准化〔W3K.7〕。

#### 3. [[Optical Communication/01. Conference/2025 ECOC/index|洞察：2025年 ECOC 论文专题洞察]]

ECOC 2025（哥本哈根，2025 年 9 月 28 日–10 月 2 日），完整论文集 542 篇（含 15 篇 Postdeadline、195 篇海报、39 篇特邀）。

**1. 六大场景关键结论**

| 场景 | 关键结论 |
|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|Scale Across（22）]] | AI 训练开始定义 DCI：分布式训练时间/成本/能耗框架显示城域分布训练只慢 7%、长途慢 37%〔Tu.04.06.2〕；<50 ms 光层保护保障多 DC LLM 训练无损〔Tu.01.06.4〕；空芯光纤首次用于 AI DC 的 8λ×225 GBd 双向 IM-DD（7.6 Tb/s，PDP）〔Th.03.03.3〕；coherent-lite 7 芯 80 km 净 31.7 Tb/s〔M.02.05.4〕；L4 自治光网络服务分布式训练〔W.02.01.177〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|Scale Out（101）]] | 单波 IM-DD 极限被推到净 651 Gb/s〔Tu.03.06.1〕与 320 GBd 净 512 Gb/s〔M.02.07.4〕；400G/lane 雏形出现在 GeSi EAM 224 GBd（PDP）〔Th.03.01.4〕、TFLN 448G 无放大〔Tu.03.07.2〕、等离子体 MZM 净 400G〔W.04.07.5〕、182 GBd PAM6 20 km〔W.04.07.4〕；器件侧零偏 95 GHz 微环〔M.02.02.1〕、205 GHz PD〔Tu.01.02.1〕；AWGR 纳秒光交换加速分布式训练〔Tu.03.07.5〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|Scale Up（17）]] | CPO 进入可靠性统计阶段：51.2T CPO 交换机超百万 400G 端口·小时数据〔Tu.01.03.3〕；1060 nm VCSEL + 多芯光纤 CPO 做到 3.95 pJ/bit〔Tu.01.03.1〕与 2.88 Tb/s〔Tu.01.03.2〕；光 Chiplet 0.75 pJ/bit〔W.01.03.2〕；CMOS 光学中介层 1.6T 发射 PIC〔Th.02.02.3〕；非制冷 400 mW QD-DFB 作 CPO 外置光源〔W.03.02.1〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|Transport（173）]] | 容量纪录集中爆发：G.654 光纤 430.2 Tb/s（PDP）〔Th.03.02.3〕、现网随机耦合 4 芯 927.7 Tb/s〔M.03.05.2〕、568.8 Tb/s × 5166 km〔M.03.05.1〕、S+C+L 2000 km 105.6 Tb/s〔Tu.03.05.2〕、单波 2.52 Tb/s〔Th.03.02.1〕、400 GBd 全相干 QAM〔Th.03.01.5〕；空芯光纤 0.052 dB/km（PDP）〔Th.03.01.1〕、1 Tb/s/λ × 10714 km〔W.03.05.5〕；网络侧 LPM 40 m 分辨率〔Th.03.03.2〕、LLM Agent 现网自治〔M.03.01.3〕、Meta 骨干 1600ZR+ 点对点化〔Th.02.06.4〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|Access（132）]] | VHSP 两条路线并进：IM-DD 超速率 100G〔W.01.07.1〕、120 GBd 对称〔W.01.07.5〕、200G-PON 与三代 PON 共存〔W.02.01.110〕，相干 PON 三速率/240G/单激光器双向〔M.03.07.2–4〕；固移融合相干接入 109 km 现网（PDP）〔Th.03.03.4〕；相干 FSO 4.6 km 500G 可用率实测〔Th.02.07.1〕、中红外 FSO（PDP）〔Th.03.03.5〕；300 GHz THz 7 b/s/Hz〔W.02.01.153〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|新应用（97）]] | 在役海缆变成深海传感网：4400 km 海缆 4.4 万测点观测 M8.8 地震与海啸（PDP）〔Th.03.02.5〕、SOP 捕获地震前兆（PDP）〔Th.03.03.1〕；无中继 200.6 km DAS〔Tu.04.08.1〕、φ-OFDR 33.3 万通道〔W.02.01.137〕；CV-QKD 可组合密钥率 8.93 Mb/s〔W.02.01.194〕、QKD 与 37.6 Tb/s 在 101.6 km 空芯光纤共存〔Tu.04.09.1〕；存内光子张量核 1.62 TOPS〔Tu.01.04.1〕。 |

**2. 二级专题导航**（点专题名进入对应小节）

| 场景 | 二级专题（论文数） |
|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|Scale Across]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#产业需求\|产业需求 9]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#FST与Multi-Rail\|FST与Multi-Rail 0]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#ZR、ZR+、CL\|ZR/ZR+/CL 3]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#低功耗DSP\|低功耗DSP 1]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#高波特率器件\|高波特率器件 0]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#光源\|光源 1]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#新型光纤介质\|新型光纤介质 8]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|Scale Out]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#调制器\|调制器 22]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#光DSP\|光DSP 16]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#电SerDes及连接器\|电SerDes及连接器 2]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#OCS\|OCS 5]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#光源\|光源 22]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#探测器与接收\|探测器与接收 14]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#集成平台与无源器件\|集成平台与无源器件 18]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#链路与系统\|链路与系统 2]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|Scale Up]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#光源\|光源 4]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#Narrow&Fast\|Narrow&Fast 1]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#Slow&Wide\|Slow&Wide 5]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#SerDes及连接器\|SerDes及连接器 3]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#异质集成\|异质集成 2]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#架构与系统\|架构与系统 2]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|Transport]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#HCF\|HCF 15]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#AI光网络\|AI光网络 30]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光系统建模\|光系统建模 8]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#高波特率器件\|高波特率器件 11]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光放与多波段\|光放与多波段 25]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#SDM光纤\|SDM光纤 26]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#相干DSP与编码\|相干DSP与编码 26]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光网络架构与控制\|光网络架构与控制 27]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光纤与测试\|光纤与测试 5]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|Access]] | **固定接入**：[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#50G PON\|50G PON 9]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#Beyond 50G PON\|Beyond 50G PON 24]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#AI-FAN\|AI-FAN 6]]；**移动接入**：[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#RoF\|RoF 39]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#FSO\|FSO 54]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|新应用]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引#DAS、光纤感知\|DAS/光纤感知 36]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引#QKD、量子\|QKD/量子 40]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引#光计算\|光计算 16]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引#其他新应用\|其他新应用 5]] |

**3. 场景 × 技术层分布**

| 场景 | 网络 | 光系统 | 算法 | 器件 | 芯片 | 合计 |
|---|---|---|---|---|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|Scale Across]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|9]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|8]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|2]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|1]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|2]] | 22 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|Scale Out]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|3]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|11]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|16]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|34]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|37]] | 101 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|Scale Up]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|2]] | – | – | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|2]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|13]] | 17 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|Transport]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|45]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|29]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|51]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|41]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|7]] | 173 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|Access]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|13]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|52]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|22]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|23]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|22]] | 132 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|新应用]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|9]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|47]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|16]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|5]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|20]] | 97 |
| **合计** | **81** | **147** | **107** | **106** | **101** | **542** |

**4. TOP5 核心趋势**

1. **容量纪录在 SDM 与超宽带两线同时刷新**：Transport · 光系统 29 篇：G.654 430 Tb/s〔Th.03.02.3〕、现网 RC-MCF 927.7 Tb/s〔M.03.05.2〕、5166 km 568.8 Tb/s〔M.03.05.1〕、S+C+L 2000 km〔Tu.03.05.2〕。
2. **空芯光纤损耗进入 0.05 dB/km 时代**：Transport · 器件：0.052 dB/km 与 83 km 单次拉制（PDP）〔Th.03.01.1〕、ST-HCF 0.05 dB/km〔Tu.04.01.2〕；1 Tb/s/λ × 10714 km〔W.03.05.5〕与实时 11154 km〔Th.03.02.2〕。
3. **IM-DD 单波逼近 650 Gb/s，400G/lane 开始成形**：Scale Out 101 篇：净 651 Gb/s〔Tu.03.06.1〕、GeSi EAM 224 GBd〔Th.03.01.4〕、TFLN/等离子体 400G+；光梳/微梳与 VCSEL 多芯作为宽而慢路线的光源。
4. **PON 进入 VHSP 选型期**：Access 132 篇：IM-DD 超速率 100G/120 GBd 与相干 PON 200G 并行，互通参考接收机〔W.01.07.2〕、共存拉曼代价〔W.01.07.3〕、固移融合现场（PDP）〔Th.03.03.4〕。
5. **光纤变成地球物理传感器**：新应用 97 篇：海缆地震/海啸观测（两篇 PDP）、SOP 与相位多技术现网观测站〔Th.02.05.2〕、DAS 与 800ZR 城域共存〔Tu.01.08.2〕；QKD 以现网共存为主线（Tu.04.09 Session）。

### 二. [[Wireless Communication/index|专题：无线与WiFi通信]]

#### 1. [[Wireless Communication/01. WiFi Architecture/index|洞察：基于 WiFi 架构的专题洞察]]

以 Wi‑Fi 链路“从发到收”的全栈架构（天线 → FEM → 射频 → 混合信号 → PHY → MAC → 多 AP）为主线，挂接学术、产业、标准三类信息；[[Wireless Communication/01. WiFi Architecture/index#交互架构图|交互架构图]] 可逐层展开。截至 2026‑09‑30。

| 部分 | 关键结论 |
|---|---|
| [[Wireless Communication/01. WiFi Architecture/01. Academic Research\|1）各技术领域最新学术研究]] | 研究重心从峰值速率转向可靠性与尾时延：多 AP 协作（MAPC）是 MAC 层第一热点，MLO 进入“怎么调度”阶段；AI/ML、WLAN 感知（11bf）和毫米波（11bq）成为跨层新方向；芯片难点在 320 MHz + 4K‑QAM 的线性度与功耗。 |
| [[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/index\|2）产业深度洞察 2025–2026]]（另见 [[Wireless Communication/01. WiFi Architecture/02. Industry Landscape\|厂商名录]]） | **Wi‑Fi 7 已过半**：2Q26 占企业 WLAN 销售额一半以上（Dell'Oro），手机渗透约 1/4。**Wi‑Fi 8 比标准早两年上市**：MediaTek、Broadcom、Qualcomm 芯片和 ASUS、TP‑Link 路由已发布，认证要到 2028 年 1 月。**企业 WLAN 整合**：HPE 收购 Juniper、Belden 收购 Ruckus；Apple 用自研 N1 替换 Broadcom；Skyworks 与 Qorvo 合并获批。**外部变量**：FCC 禁止外国生产的消费级路由新机型认证、欧洲和中国上 6 GHz 倾向移动、存储芯片短缺推高设备成本。 |
| [[Wireless Communication/01. WiFi Architecture/03. Standards and Evolution\|3）标准组织、代际演进与新技术]] | 802.11bn（Wi‑Fi 8 UHR）D2.0 投票中，目标 2028‑09 批准；802.11bf 感知于 2025‑09 发布，802.11bq 集成毫米波推进中，Wi‑Fi 9 愿景讨论已在 WNG 启动；中国 6 GHz 上半段划给 IMT，国内 Wi‑Fi 7/8 主要依赖 2.4/5 GHz 加 MLO。 |

#### 2. [[Wireless Communication/02. WiFi Technology Atlas/index|图谱：WiFi 全局架构与技术图谱]]

以 Wi‑Fi 链路“从发到收”的系统架构为主线，把 238 个技术名词按 8 个架构层（天线 → FEM → 射频 → 混合信号 → PHY → Lower MAC → Upper MAC → 多 AP）和 3 个跨层方向（芯片、感知定位、频谱新频段）归档；[[Wireless Communication/02. WiFi Technology Atlas/index#全局架构图|全局架构图]] 可逐层展开，点击名词直达原理。每个方向分“总览（关键技术 + 产业链）”与“术语笔记”两部分。

## 目录

- [[学习笔记/如何使用这个网站|如何使用这个网站]]
- 按文件夹浏览：左侧导航栏
- 按标签浏览：点击笔记里的 `#标签`
