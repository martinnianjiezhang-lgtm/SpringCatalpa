---
title: "OFC 2026"
tags:
  - OFC2026
---

OFC 2026（洛杉矶，2026 年 3 月 15–19 日），本目录收录 707 篇论文（含 24 篇 Postdeadline、16 篇 Demo、158 篇海报）。
每篇论文都读过摘要并写了一句中文要点，按与 ECOC 2026 相同的框架归类：六大应用场景 × 网络 / 光系统 / 算法 / 器件 / 芯片。结论中的〔编号〕是会议论文编号，可在对应场景索引页中查到题目与要点。

## 1. 六大场景关键结论

| 场景 | 范围 | 论文数 | 关键结论 |
|---|---|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|Scale Across]] | 跨楼/园区/区域 DC 互连、跨 DC 训练 | 15 | 跨 DC 训练从经济性论证走向现网：1024 GPU 跨 600 km 多 AIDC 训练 LLaMA2-70B，DP/PP 效率损失 <5%/<1%〔W4H.5〕；DCI 单波进入 1.2T（S+C+L 134 Tb/s，全部通道 1.276 Tb/s〔W3J.1〕）；coherent-lite 靠光梳共享载波/时钟做波特率采样〔Th4C.8〕，BTO DP-IQM 单波净 1 Tb/s（ZR 80 km）〔Th3J.4〕。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|Scale Out]] | 224G/448G IM-DD、光源、调制器、探测器、OCS | 157 | 400G/lane 进入多平台 PDP 竞速：硅 MZM〔Th4A.4〕、BTO 1.6T DR4〔Th4B.3〕、膜 EA-DFB 448G〔Th4A.1〕、TFLT 768 Gb/s〔Th4A.2〕、TFLN TOSA 420G〔W4J.4〕、差分 EML〔Tu3J.6〕并存，尚无胜者；1.6T 2×FR4 单片硅光满足 802.3dj〔Th4A.7〕。OCS 走向可用：4096×4096 单层 819.2 Tb/s〔M3F.3〕，训练重构快 37.5%〔M3F.5〕，推理需 <700 ns〔W2A.28〕；百万级光模块现网故障数据出现〔Th3B.2〕。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|Scale Up]] | CPO/NPO、光 I/O、Chiplet、外置光源 | 35 | CPO 关注点从器件转到“系统可靠性 + 外置光源”：8 通道 >+25 dBm ELS〔W1B.3〕、500 mW PCSEL〔W4E.2〕、3D 堆叠 EIC/PIC 光 I/O 1.33 Tb/s/mm²〔M4B.2〕、玻璃基板与 AWGR 光学中介层〔Th3C.2、Th3C.1〕、TFLN 晶圆级 CPO 引擎〔Th4A.6〕；光域 AllReduce〔M4F.3、Th3H.3〕与 THz 介质波导互连〔Th1A.1〕是新候选。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|Transport]] | 相干、海缆、长途、多波段、SDM、空芯光纤、光网络智能化 | 225 | 单模光纤带宽拓到 OESCL 42.4 THz、>450 Tb/s〔Th4B.5〕；实时 2.5 Pb/s 24 芯〔Th3A.2〕；空芯光纤 0.040 dB/km〔M2J.1〕、266 km 超长跨段跨洋 21.7 Tb/s〔Th4B.7〕、单芯 550.97 Tb/s〔Th1J.6〕；相干可插拔 400G/λ × 5682 km 海缆〔Th4C.6〕、800G 多厂商互通 1602 km〔Th4B.6〕；网络智能化出现垂直大模型 Optics GPT〔Th4C.1〕与 OSFP 内实时纵向功率监测〔Th4B.4〕。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|Access]] | PON、FTTR、前传/RoF、THz/6G、FSO/卫星/光无线 | 147 | 相干 PON 独立成场：首个双向 200G TFDM 相干 PON 现场试验〔Th4C.4〕、非制冷 DFB 突发上行 37 dB〔Th4C.3〕、统一 OLT 兼容相干与 IM-DD ONU〔W1I.4〕；THz 单链路 600 Gb/s〔M4H.6〕、312 GHz 3 km 现场〔M4H.7〕；卫星光网络路由/切换成独立 Session（Tu3F），飞机–GEO 激光链路首批结果〔Th4B.1〕；光无线 516 Tb/s〔M3H.3〕。 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|新应用]] | 光纤感知、QKD/量子网络、光计算 | 128 | 海缆感知规模化：4400 km 海缆 8.8 万个 50 m 测点〔Th4C.7〕，585 km 中继链路 DAS 与 15.8 Tb/s 共传〔M4J.6〕，sub-pε/√Hz 通感一体〔W4C.6〕；QKD 与 374.4 Tb/s 经典业务在 100 km 7 芯光纤共存〔M2K.2〕、集成 CV-QKD 538 Mb/s〔M1K.2〕、QKD 无改造进入 32 用户 PON〔W3K.3〕；光计算做到 212 GOPS 光子 Ising 机〔W3C.2〕。 |

## 2. 场景 × 技术层分布

点数字进入对应场景页的技术层小节。

| 场景 | 网络 | 光系统 | 算法 | 器件 | 芯片 | 合计 |
|---|---|---|---|---|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|Scale Across]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|7]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|3]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|1]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|2]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|2]] | 15 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|Scale Out]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|13]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|6]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|23]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|60]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|55]] | 157 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|Scale Up]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|10]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|1]] | – | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|8]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|16]] | 35 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|Transport]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|45]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|26]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|83]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|61]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|10]] | 225 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|Access]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|31]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|55]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|25]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|13]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|23]] | 147 |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|新应用]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|11]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|62]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|16]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|11]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|28]] | 128 |
| **合计** | **117** | **153** | **148** | **155** | **134** | **707** |

## 3. 二级专题索引

点专题名跳到对应场景页的小节。

| 场景 | 二级专题（论文数） |
|---|---|
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引\|Scale Across]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#产业需求\|产业需求 6]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#FST与Multi-Rail\|FST与Multi-Rail 2]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#ZR、ZR+、CL\|ZR/ZR+/CL 1]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#低功耗DSP\|低功耗DSP 1]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#高波特率器件\|高波特率器件 3]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#光源\|光源 1]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引#新型光纤介质\|新型光纤介质 1]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引\|Scale Out]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#调制器\|调制器 50]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#光DSP\|光DSP 22]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#电SerDes及连接器\|电SerDes及连接器 5]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#OCS\|OCS 15]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#光源\|光源 15]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#探测器与接收\|探测器与接收 12]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#集成平台与无源器件\|集成平台与无源器件 33]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引#链路与系统\|链路与系统 5]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引\|Scale Up]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#光源\|光源 8]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#Narrow&Fast\|Narrow&Fast 3]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#Slow&Wide\|Slow&Wide 7]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#SerDes及连接器\|SerDes及连接器 6]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#异质集成\|异质集成 2]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引#架构与系统\|架构与系统 9]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引\|Transport]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#HCF\|HCF 30]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#AI光网络\|AI光网络 56]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#光系统建模\|光系统建模 12]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#高波特率器件\|高波特率器件 12]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#光放与多波段\|光放与多波段 30]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#SDM光纤\|SDM光纤 22]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#相干DSP与编码\|相干DSP与编码 23]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#光网络架构与控制\|光网络架构与控制 31]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引#光纤与测试\|光纤与测试 9]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引\|Access]] | **固定接入**：[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#50G PON\|50G PON 3]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#Beyond 50G PON\|Beyond 50G PON 21]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#AI-FAN\|AI-FAN 17]]；**移动接入**：[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#RoF\|RoF 55]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引#FSO\|FSO 51]] |
| [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引\|新应用]] | [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引#DAS、光纤感知\|DAS/光纤感知 59]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引#QKD、量子\|QKD/量子 44]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引#光计算\|光计算 18]]、[[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引#其他新应用\|其他新应用 7]] |

## 4. TOP5 核心趋势

1. **AI 集群成为第一驱动力**：Scale Out/Up/Across 合计 207 篇（29%）。“AI/计算集群光互连”主题占比从 ECOC 2025 的 1.7% 升到 5.0%；出现 1024 GPU 跨 600 km 训练现网〔W4H.5〕、百万级光模块故障数据〔Th3B.2〕这类运营数据论文。
2. **400G/lane 没有单一胜者**：Scale Out · 器件/芯片 115 篇：硅 MZM、BTO、TFLN、TFLT、膜 EA-DFB、差分 EML、等离子体环、铁电玻璃都做到 ≥400G；决定因素转向驱动/SerDes 协同与 LPO/NPO/CPO 封装形态〔W1D.7〕。
3. **空芯光纤进入系统工程**：Transport：损耗 0.040 dB/km〔M2J.1〕、266 km 跨段跨洋〔Th4B.7〕、双窗口 0.11/0.13 dB/km〔Th4B.8〕；气体吸收、IMI、熔接、OTDR 与网络部署优化成体系出现（Th1J、Tu3E、M1J、M2J 四个 Session）。
4. **光网络的“自治闭环”成型**：Transport · 网络 + 算法 128 篇：数字孪生 + LLM 多智能体 + 纵向功率监测；两场生成式 AI 研讨会〔W3I.1、W4I.1〕，Optics GPT〔Th4C.1〕，LPM 进入可插拔 DSP〔Th4B.4〕。
5. **光纤感知与量子走向“可运营”**：新应用 · 光系统 62 篇：海缆 DAS 8.8 万测点〔Th4C.7〕、通感一体共传；QKD 与数百 Tb/s 经典业务同芯共存〔M2K.2〕、进入 PON 与 ROADM 链路，QKDN 讨论标准化〔W3K.7〕。

## 5. 纪录与里程碑

| 类别 | 纪录 / 里程碑 | 论文 |
|---|---|---|
| SMF 带宽/容量 | 42.4 THz OESCL，>450 Tb/s（GMI），39 km 现网 G.652.D | Th4B.5 |
| 实时 SDM 容量 | 2.5 Pb/s，24 芯，S+C+L，商用 400G 转发器 | Th3A.2 |
| 单芯单模光纤容量 | 550.97 Tb/s，10.9 km 反谐振空芯光纤，双向 | Th1J.6 |
| 空芯光纤最低损耗 | 0.040 dB/km（GTA-ST-HCF） | M2J.1 |
| 空芯光纤跨洋 | 21.7 Tb/s × 6660 km，266 km 跨段，<30 个中继 | Th4B.7 |
| 相干可插拔海缆 | 400G/λ × 5682 km | Th4C.6 |
| 1.6T 单片硅光 | 8×200G 2×FR4，满足 IEEE 802.3dj | Th4A.7 |
| 免驱动光 DAC | CMOS 逻辑门直驱：448G PAM4 / 1.2T 16QAM | Th4B.2 |
| OCS 规模 | 4096×4096，单层 819.2 Tb/s | M3F.3 |
| 跨 DC 训练 | 600 km，1024 GPU，LLaMA2-70B | W4H.5 |
| 海缆 DAS | 4400 km，8.8 万个 50 m 测点 | Th4C.7 |
| THz 通信 | 600 Gb/s @300 GHz；312 GHz 3 km 现场 | M4H.6、M4H.7 |
| 相干 PON | 首个双向 200G TFDM 现场试验；突发上行 37 dB 预算 | Th4C.4、Th4C.3 |

## 6. 场景论文索引

- [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Across 论文索引|OFC2026 Scale Across 论文索引]]：15 篇 · 跨楼/园区/区域 DC 互连、跨 DC 训练
- [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Out 论文索引|OFC2026 Scale Out 论文索引]]：157 篇 · 224G/448G IM-DD、光源、调制器、探测器、OCS
- [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Scale Up 论文索引|OFC2026 Scale Up 论文索引]]：35 篇 · CPO/NPO、光 I/O、Chiplet、外置光源
- [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Transport 论文索引|OFC2026 Transport 论文索引]]：225 篇 · 相干、海缆、长途、多波段、SDM、空芯光纤、光网络智能化
- [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 Access 论文索引|OFC2026 Access 论文索引]]：147 篇 · PON、FTTR、前传/RoF、THz/6G、FSO/卫星/光无线
- [[Optical Communication/01. Conference/2026 OFC/场景论文索引/OFC2026 新应用 论文索引|OFC2026 新应用 论文索引]]：128 篇 · 光纤感知、QKD/量子网络、光计算

## 7. 论文类型

Contributed 388、Poster 158、Invited 68、Top-Scored 52、Postdeadline 24、Demo 16、Tutorial 1
