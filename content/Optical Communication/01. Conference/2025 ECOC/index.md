---
title: "ECOC 2025"
tags:
  - ECOC2025
---

ECOC 2025（哥本哈根，2025 年 9 月 28 日–10 月 2 日），完整论文集 542 篇（含 15 篇 Postdeadline、195 篇海报、39 篇特邀）。
每篇论文都读过摘要并写了一句中文要点，按与 ECOC 2026 相同的框架归类：六大应用场景 × 网络 / 光系统 / 算法 / 器件 / 芯片。结论中的〔编号〕是会议论文编号，可在对应场景索引页中查到题目与要点。

## 1. 六大场景关键结论

| 场景 | 范围 | 论文数 | 关键结论 |
|---|---|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|Scale Across]] | 跨楼/园区/区域 DC 互连、跨 DC 训练 | 22 | AI 训练开始定义 DCI：分布式训练时间/成本/能耗框架显示城域分布训练只慢 7%、长途慢 37%〔Tu.04.06.2〕；<50 ms 光层保护保障多 DC LLM 训练无损〔Tu.01.06.4〕；空芯光纤首次用于 AI DC 的 8λ×225 GBd 双向 IM-DD（7.6 Tb/s，PDP）〔Th.03.03.3〕；coherent-lite 7 芯 80 km 净 31.7 Tb/s〔M.02.05.4〕；L4 自治光网络服务分布式训练〔W.02.01.177〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|Scale Out]] | 224G/448G IM-DD、光源、调制器、探测器、OCS | 101 | 单波 IM-DD 极限被推到净 651 Gb/s〔Tu.03.06.1〕与 320 GBd 净 512 Gb/s〔M.02.07.4〕；400G/lane 雏形出现在 GeSi EAM 224 GBd（PDP）〔Th.03.01.4〕、TFLN 448G 无放大〔Tu.03.07.2〕、等离子体 MZM 净 400G〔W.04.07.5〕、182 GBd PAM6 20 km〔W.04.07.4〕；器件侧零偏 95 GHz 微环〔M.02.02.1〕、205 GHz PD〔Tu.01.02.1〕；AWGR 纳秒光交换加速分布式训练〔Tu.03.07.5〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|Scale Up]] | CPO/NPO、光 I/O、Chiplet、外置光源 | 17 | CPO 进入可靠性统计阶段：51.2T CPO 交换机超百万 400G 端口·小时数据〔Tu.01.03.3〕；1060 nm VCSEL + 多芯光纤 CPO 做到 3.95 pJ/bit〔Tu.01.03.1〕与 2.88 Tb/s〔Tu.01.03.2〕；光 Chiplet 0.75 pJ/bit〔W.01.03.2〕；CMOS 光学中介层 1.6T 发射 PIC〔Th.02.02.3〕；非制冷 400 mW QD-DFB 作 CPO 外置光源〔W.03.02.1〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|Transport]] | 相干、海缆、长途、多波段、SDM、空芯光纤、光网络智能化 | 173 | 容量纪录集中爆发：G.654 光纤 430.2 Tb/s（PDP）〔Th.03.02.3〕、现网随机耦合 4 芯 927.7 Tb/s〔M.03.05.2〕、568.8 Tb/s × 5166 km〔M.03.05.1〕、S+C+L 2000 km 105.6 Tb/s〔Tu.03.05.2〕、单波 2.52 Tb/s〔Th.03.02.1〕、400 GBd 全相干 QAM〔Th.03.01.5〕；空芯光纤 0.052 dB/km（PDP）〔Th.03.01.1〕、1 Tb/s/λ × 10714 km〔W.03.05.5〕；网络侧 LPM 40 m 分辨率〔Th.03.03.2〕、LLM Agent 现网自治〔M.03.01.3〕、Meta 骨干 1600ZR+ 点对点化〔Th.02.06.4〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|Access]] | PON、FTTR、前传/RoF、THz/6G、FSO/卫星/光无线 | 132 | VHSP 两条路线并进：IM-DD 超速率 100G〔W.01.07.1〕、120 GBd 对称〔W.01.07.5〕、200G-PON 与三代 PON 共存〔W.02.01.110〕，相干 PON 三速率/240G/单激光器双向〔M.03.07.2–4〕；固移融合相干接入 109 km 现网（PDP）〔Th.03.03.4〕；相干 FSO 4.6 km 500G 可用率实测〔Th.02.07.1〕、中红外 FSO（PDP）〔Th.03.03.5〕；300 GHz THz 7 b/s/Hz〔W.02.01.153〕。 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|新应用]] | 光纤感知、QKD/量子网络、光计算 | 97 | 在役海缆变成深海传感网：4400 km 海缆 4.4 万测点观测 M8.8 地震与海啸（PDP）〔Th.03.02.5〕、SOP 捕获地震前兆（PDP）〔Th.03.03.1〕；无中继 200.6 km DAS〔Tu.04.08.1〕、φ-OFDR 33.3 万通道〔W.02.01.137〕；CV-QKD 可组合密钥率 8.93 Mb/s〔W.02.01.194〕、QKD 与 37.6 Tb/s 在 101.6 km 空芯光纤共存〔Tu.04.09.1〕；存内光子张量核 1.62 TOPS〔Tu.01.04.1〕。 |

## 2. 场景 × 技术层分布

点数字进入对应场景页的技术层小节。

| 场景 | 网络 | 光系统 | 算法 | 器件 | 芯片 | 合计 |
|---|---|---|---|---|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|Scale Across]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|9]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|8]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|2]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|1]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|2]] | 22 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|Scale Out]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|3]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|11]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|16]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|34]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|37]] | 101 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|Scale Up]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|2]] | – | – | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|2]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|13]] | 17 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|Transport]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|45]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|29]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|51]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|41]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|7]] | 173 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|Access]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|13]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|52]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|22]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|23]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|22]] | 132 |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|新应用]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|9]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|47]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|16]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|5]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|20]] | 97 |
| **合计** | **81** | **147** | **107** | **106** | **101** | **542** |

## 3. 二级专题索引

点专题名跳到对应场景页的小节。

| 场景 | 二级专题（论文数） |
|---|---|
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引\|Scale Across]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#产业需求\|产业需求 9]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#FST与Multi-Rail\|FST与Multi-Rail 0]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#ZR、ZR+、CL\|ZR/ZR+/CL 3]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#低功耗DSP\|低功耗DSP 1]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#高波特率器件\|高波特率器件 0]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#光源\|光源 1]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引#新型光纤介质\|新型光纤介质 8]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引\|Scale Out]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#调制器\|调制器 22]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#光DSP\|光DSP 16]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#电SerDes及连接器\|电SerDes及连接器 2]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#OCS\|OCS 5]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#光源\|光源 22]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#探测器与接收\|探测器与接收 14]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#集成平台与无源器件\|集成平台与无源器件 18]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引#链路与系统\|链路与系统 2]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引\|Scale Up]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#光源\|光源 4]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#Narrow&Fast\|Narrow&Fast 1]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#Slow&Wide\|Slow&Wide 5]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#SerDes及连接器\|SerDes及连接器 3]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#异质集成\|异质集成 2]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引#架构与系统\|架构与系统 2]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引\|Transport]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#HCF\|HCF 15]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#AI光网络\|AI光网络 30]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光系统建模\|光系统建模 8]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#高波特率器件\|高波特率器件 11]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光放与多波段\|光放与多波段 25]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#SDM光纤\|SDM光纤 26]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#相干DSP与编码\|相干DSP与编码 26]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光网络架构与控制\|光网络架构与控制 27]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引#光纤与测试\|光纤与测试 5]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引\|Access]] | **固定接入**：[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#50G PON\|50G PON 9]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#Beyond 50G PON\|Beyond 50G PON 24]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#AI-FAN\|AI-FAN 6]]；**移动接入**：[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#RoF\|RoF 39]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引#FSO\|FSO 54]] |
| [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引\|新应用]] | [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引#DAS、光纤感知\|DAS/光纤感知 36]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引#QKD、量子\|QKD/量子 40]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引#光计算\|光计算 16]]、[[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引#其他新应用\|其他新应用 5]] |

## 4. TOP5 核心趋势

1. **容量纪录在 SDM 与超宽带两线同时刷新**：Transport · 光系统 29 篇：G.654 430 Tb/s〔Th.03.02.3〕、现网 RC-MCF 927.7 Tb/s〔M.03.05.2〕、5166 km 568.8 Tb/s〔M.03.05.1〕、S+C+L 2000 km〔Tu.03.05.2〕。
2. **空芯光纤损耗进入 0.05 dB/km 时代**：Transport · 器件：0.052 dB/km 与 83 km 单次拉制（PDP）〔Th.03.01.1〕、ST-HCF 0.05 dB/km〔Tu.04.01.2〕；1 Tb/s/λ × 10714 km〔W.03.05.5〕与实时 11154 km〔Th.03.02.2〕。
3. **IM-DD 单波逼近 650 Gb/s，400G/lane 开始成形**：Scale Out 101 篇：净 651 Gb/s〔Tu.03.06.1〕、GeSi EAM 224 GBd〔Th.03.01.4〕、TFLN/等离子体 400G+；光梳/微梳与 VCSEL 多芯作为宽而慢路线的光源。
4. **PON 进入 VHSP 选型期**：Access 132 篇：IM-DD 超速率 100G/120 GBd 与相干 PON 200G 并行，互通参考接收机〔W.01.07.2〕、共存拉曼代价〔W.01.07.3〕、固移融合现场（PDP）〔Th.03.03.4〕。
5. **光纤变成地球物理传感器**：新应用 97 篇：海缆地震/海啸观测（两篇 PDP）、SOP 与相位多技术现网观测站〔Th.02.05.2〕、DAS 与 800ZR 城域共存〔Tu.01.08.2〕；QKD 以现网共存为主线（Tu.04.09 Session）。

## 5. 纪录与里程碑

| 类别 | 纪录 / 里程碑 | 论文 |
|---|---|---|
| 标准 G.654 光纤容量 | O 三模 + ESCL，430.2 Tb/s（GMI） | Th.03.02.3 |
| 现网光纤吞吐 | 927.7 Tb/s，随机耦合 4 芯，19.2 THz | M.03.05.2 |
| 容量 × 距离 | 568.8 Tb/s × 5166 km，2.93 Eb/s·km（19 芯） | M.03.05.1 |
| 单波速率 | 2.52 Tb/s/λ @120 km；>2 Tb/s/λ @1040 km | Th.03.02.1 |
| 全相干 QAM 符号率 | 400 GBd 32QAM（暗孤子微梳） | Th.03.01.5 |
| 空芯光纤损耗 | 0.052 dB/km（40 km），83 km 单次拉制 | Th.03.01.1 |
| 空芯光纤距离 | 1 Tb/s/λ × 10714 km | W.03.05.5 |
| 单波 IM-DD | 净 651 Gb/s（248 GBd PS-PAM12） | Tu.03.06.1 |
| CPO 可靠性 | 51.2T CPO 交换机，>100 万 400G 端口·小时 | Tu.01.03.3 |
| 海缆感知 | 4400 km，4.4 万测点，首次光纤观测海啸 | Th.03.02.5 |
| 无中继 DAS | 200.6 km | Tu.04.08.1 |
| CV-QKD 密钥率 | 8.93 Mb/s 可组合安全（25 km） | W.02.01.194 |

## 6. 场景论文索引

- [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Across 论文索引|ECOC2025 Scale Across 论文索引]]：22 篇 · 跨楼/园区/区域 DC 互连、跨 DC 训练
- [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Out 论文索引|ECOC2025 Scale Out 论文索引]]：101 篇 · 224G/448G IM-DD、光源、调制器、探测器、OCS
- [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Scale Up 论文索引|ECOC2025 Scale Up 论文索引]]：17 篇 · CPO/NPO、光 I/O、Chiplet、外置光源
- [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Transport 论文索引|ECOC2025 Transport 论文索引]]：173 篇 · 相干、海缆、长途、多波段、SDM、空芯光纤、光网络智能化
- [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 Access 论文索引|ECOC2025 Access 论文索引]]：132 篇 · PON、FTTR、前传/RoF、THz/6G、FSO/卫星/光无线
- [[Optical Communication/01. Conference/2025 ECOC/场景论文索引/ECOC2025 新应用 论文索引|ECOC2025 新应用 论文索引]]：97 篇 · 光纤感知、QKD/量子网络、光计算

## 7. 论文类型

Oral 256、Poster 195、Invited 39、Oral (upgraded) 23、Postdeadline 15、Tutorial 7、Demo 7
