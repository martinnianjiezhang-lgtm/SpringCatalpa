---
title: "Meta、Google、Microsoft、OpenAI 数据中心：地址、规划与规模"
tags:
  - AI数据中心
  - 专题洞察
date: 2026-10-01
---

版本 v1 · 2026-10-01 · 配套园区清单：[四家AI数据中心园区清单-2026-10.csv](四家AI数据中心园区清单-2026-10.csv)

## 口径说明（先读）

- **主数据源：** Epoch AI《Frontier AI Data Centers》公开数据集（2026-10-01 版）。它按园区逐个记录街道地址、楼栋、IT 功率、芯片、建设方、能源方，以及按日期排列的投产时间线；时间线依据卫星与无人机影像、州监管文件（如德州 TDLR）、电力公司文件。
- **覆盖范围：** Epoch 只收录大型 AI 园区，不是各家的全部数据中心。Meta 官网约 30 个园区、Microsoft 自称 400 多座数据中心分布在 70 个区域，其中传统云和存储园区大多不在表里。
- **功率口径：** 正文统一用 **IT 功率**（服务器侧）。园区总功率（含制冷、配电损耗）一般是 IT 功率的 1.2–1.4 倍，表里需要时单独注明"总功率"。
- **"规划峰值"：** 指 Epoch 时间线里能看到的最大值，大多截止 2027–2028 年。公司公告的远期目标（如 Hyperion 最终 5 GW）往往更大，正文分开写。
- **重复计算：** Fairwater Atlanta、Fairwater Wisconsin 的使用方同时是 Microsoft 和 OpenAI，两家汇总时都计入。
- **补充项：** Meta El Paso、Meta Lebanon、Google 印度 Visakhapatnam、Google 德州 Haskell、OpenAI 印度项目 Epoch 未收录，按公司公告补入，CSV 里已标注。
- **地址可靠性：** 多为监管文件或地图上的地块地址，个别是项目办公室地址（如 Stargate UAE）。园区之间的距离按城镇中心直线距离估算，只作量级参考。

---

## 〇、结论

1. **在建和规划规模已经是"每家数 GW 到十几 GW"。** 按 Epoch 口径，四家当前在用的 AI 园区 IT 功率：Google 约 3.2 GW、OpenAI 约 2.5 GW（全部租用）、Meta 约 2.2 GW、Microsoft 约 1.7 GW；到 2027–2028 年时间线内分别增至约 5.9、12.9、5.3、4.6 GW。再加上公司公告的远期项目（Hyperion 5 GW、Meta El Paso 和 Lebanon 各 1 GW、Google 印度 2.51 GW 环评批复），2030 年前每家的目标都在 10 GW 量级以上。
2. **四家的所有权模式完全不同。**
   - **Google：** 几乎全部自建自有。
   - **Meta：** 自建为主，但最大的两个项目用合资融资：Hyperion 由 Blue Owl 持股 80%，El Paso 与 BlackRock 合资。
   - **Microsoft：** 自建 Fairwater 加上向 neocloud（Nebius、Nscale、IREN、Lambda、CoreWeave）大量租用，承诺金额超过 600 亿美元。
   - **OpenAI：** 一个园区都不拥有，全部由 Oracle、Crusoe、Vantage、SoftBank/SB Energy、CoreWeave、Microsoft 建设，OpenAI 只是使用方。
3. **单园区规模在 2026–2028 年跨过 1 GW。** 当前最大的是 Fairwater Atlanta（636 MW IT）。2028 年前将有多个园区超过 1 GW：Fairwater Wisconsin（2.26 GW IT）、Stargate New Mexico（1.75 GW）、Meta Hyperion 一期（1.63 GW）、Stargate Shackelford（1.4 GW）、Meta Prometheus（1.02 GW）、Google Goodnight（1.0 GW）。
4. **选址集中在美国中部和南部的"电力走廊"。** 德州（Abilene、Shackelford、Milam、Denton、Temple、Goodnight、Midlothian/Red Oak）、俄亥俄（New Albany、Columbus、Lancaster、Bowling Green、Lordstown）、内布拉斯加/艾奥瓦（Omaha、Council Bluffs、Papillion、Lincoln、Cedar Rapids、Des Moines）、威斯康星（Mount Pleasant、Port Washington）、路易斯安那、新墨西哥、印第安纳是最密集的几个州。
5. **出现了多家公司在同一地区扎堆的"园区群"。** 例如：
   - 俄亥俄 New Albany：Meta Prometheus 和 Google New Albany 同在一个产业园；
   - 德州 Abilene：Stargate Abilene 和 Microsoft 的 Crusoe 扩建地块是同一个地址；
   - El Paso–Santa Teresa：Meta El Paso 和 Stargate Project Jupiter 直线约 25 km；
   - 威斯康星东南：Fairwater Wisconsin 和 Stargate Port Washington 约 75 km。

   这些园区群是 Scale-across 光网络需求最集中的地方。
6. **电力解法分成三类。**
   - **自建燃气电厂：** Meta Prometheus 配 Williams 的 Socrates 南北两座燃气电厂；Stargate New Mexico 用 Bloom Energy 燃料电池。
   - **电力公司专项建设：** Hyperion 由 Entergy 新建燃气电厂；Fairwater Atlanta 是纯电网供电，无 UPS、无柴油发电机。
   - **新能源配套：** Milam 和 Google Haskell 配光伏加储能。
7. **建设节奏差异明显。**
   - **Meta 最快：** 帐篷式厂房，Prometheus 规划 27 栋楼，其中 16–27 号是帐篷，Montgomery 也用帐篷。
   - **Google：** 建设均匀滚动，每个园区 2–5 栋、每栋约 100 MW，园区多、单体中等。
   - **Microsoft 和 OpenAI：** 集中押注少数超大园区。
8. **OpenAI 在 2026 年明显收缩。** 2030 年基础设施支出目标从 1.4 万亿美元下调到约 6000 亿美元。Stargate UK 暂停；Stargate Norway 退出，由 Microsoft 接手；Abilene 原 2.1 GW 扩建计划取消，旁边地块由 Microsoft 通过 Crusoe 承接。美国 7 个 Stargate 站点仍在推进。

---

## 一、四家总览

| | Meta | Google | Microsoft | OpenAI |
|---|---|---|---|---|
| 公司层面规划 | 2026-01 成立 Meta Compute；"本十年建数十 GW，长期数百 GW" | 2026 资本开支 1950–2050 亿美元；德州 400 亿美元（至 2027）；印度 150 亿美元（2026–2030） | 两年内数据中心规模约翻倍；Fairwater 系列 + AI WAN；neocloud 承诺 >600 亿美元 | Stargate 美国 10 GW 目标，2026-02 称已落实 >8 GW；2030 年支出目标下调到约 6000 亿美元 |
| Epoch 收录园区数 | 17 | 20 | 11（自有 7） | 21（全部租用） |
| 当前 AI 园区 IT 功率 | 约 2.2 GW | 约 3.2 GW | 约 1.7 GW | 约 2.5 GW |
| 2027–2028 时间线内 IT 功率 | 约 5.3 GW | 约 5.9 GW | 约 4.6 GW | 约 12.9 GW |
| Epoch 之外的公告项目 | Hyperion 最终 5 GW；El Paso 1 GW；Lebanon 1 GW | 印度 Visakhapatnam（环评 2.51 GW）；德州 Haskell 等 | UK Loughton；IREN Childress 750 MW；Nscale 德州 1.2 GW | 印度 Tata 100 MW→1 GW；UAE 1 GW（首期 200 MW） |
| 旗舰园区 | Prometheus（OH）、Hyperion（LA） | Goodnight（TX）、Fort Wayne（IN）、Ohio 组团、Omaha 组团 | Fairwater Atlanta（GA）、Fairwater Wisconsin（WI） | Abilene、Shackelford、New Mexico、Michigan |
| 所有权 | 自建为主，大项目合资融资 | 自建自有 | 自建 + 大量租用 | 全部租用或合作伙伴代建 |
| 芯片 | NVIDIA B200/B300（训练），MTIA（推理） | TPU v5e/v5p/v6e/v7 | NVIDIA H100/B200/B300（GB200/GB300） | NVIDIA B200/B300 为主，后续加 Jalapeño、AMD、Cerebras |

---

## 二、Meta

### 2.1 规划

- **目标：** 2026 年 1 月成立 Meta Compute，由 Santosh Janardhan 和 Daniel Gross 牵头。Zuckerberg 的口径是"本十年建数十 GW，长期数百 GW"。
- **融资：**
  - Hyperion 与 Blue Owl 组建 270 亿美元合资：Blue Owl 持股 80%，出资约 70 亿美元现金；Meta 持股 20%，并负责建设和物业管理。
  - El Paso 与 BlackRock 合资。
  - 资产负债表外融资，是 Meta 能同时推进多个 GW 园区的关键。
- **建设方式：** Prometheus 和 Montgomery 大量使用帐篷式厂房，用来压缩工期。
- **电力：** Prometheus 配套 Williams 的 Socrates 南北两座燃气电厂（预计 2026-11 投运），加上 AEP 电网；Hyperion 由 Entergy 新建燃气电厂。
- **本地讲稿印证：**
  - Meta 骨干团队讲最大路由光纤数每年翻倍、ILA 站房到 4096 rails〔0921-MF-am-T08-1220-Meta p12, p13〕；
  - 讲稿第 3 页有"路易斯安那扩至 5 GW"的新闻截图〔同上 p3〕；
  - Meta–Corning 光纤光缆协议最高 60 亿美元〔0921-MF-pm-1500-HeraeusCovantics p2〕。

### 2.2 园区清单（按规划规模排序）

| 园区 | 地址 | 当前 IT 功率 | 规划 IT 功率（时间） | 楼栋 | 芯片 / 能源 / 建设方 | 备注 |
|---|---|---|---|---|---|---|
| Hyperion | Holly Ridge, Richland Parish, LA 71269 | 0 | 1,632 MW（2028-01，一期）；最终 5 GW | 9 | Entergy；Mortenson | 1、2 号楼屋面完工、冷却设备安装中；2030 年 2 GW |
| Prometheus | 1 Community Cir, New Albany, OH 43054（Licking County） | 496 MW | 1,022 MW（2028-07） | 27（含帐篷 16–27 号） | B200；Williams、AEP | 号称首个 GW 级训练集群；与 Google New Albany 同区 |
| El Paso | 7001 Stan Roberts Sr Ave, El Paso, TX | 0 | 1 GW（2028，公司口径） | — | 与 BlackRock 合资 | 投资从 15 亿增至 100 亿美元；已申报扩建 12 栋楼 |
| Lebanon | Lebanon, Boone County, IN（印第安纳波利斯西北约 47 km） | 0 | 1 GW（公司口径） | — | Turner Construction | 2026-02 破土；1,500 英亩；投资 >100 亿美元 |
| Bowling Green | 12356 Middleton Pike, Bowling Green, OH 43402 | 0 | 422 MW（2028-01） | 4 | Williams | 1、2 号楼屋面过半 |
| Montgomery | Co Rd 42, Montgomery, AL 36105 | 153 MW | 358 MW（2027-02） | 6 | B300；Hensel Phelps | 帐篷式厂房 |
| QTS Eagle Mountain | 652 E Hyperscale Way, Eagle Mountain, UT 84013 | 0 | 304 MW（2027-07） | 3 | QTS 代建 | |
| Cheyenne | Cheyenne, WY 82007 | 152 MW | 207 MW（2027-02） | 4 | B300 | |
| Rosemount | 145th St, Rosemount, MN 55068 | 178 MW | 178 MW | 2 | B200 | 2026-06 投运 |
| Jeffersonville | 500 8th St, Jeffersonville, IN 47130 | 178 MW | 178 MW | 2 | B300 | 2026-06 投运 |
| Temple | 2310 Eberhardt Rd, Temple, TX 76504 | 178 MW | 178 MW | 3 | B300；JE Dunn | |
| Meta-QTS Hillsboro 2 | 4755 NE Huffman St, Hillsboro, OR 97124 | 180 MW | 180 MW | 4 | H100；PGE | QTS 代建，2024 年已满负荷 |
| Kuna | 601 Kuna Mora Rd, Kuna, ID 83634 | 152 MW | 152 MW | 2 | B300；Idaho Power | 配套光伏 |
| Huntsville | 5400 Prosperity Dr NW, Toney, AL | 146 MW | 146 MW | 2 | B300；TVA、NextEra | |
| Eagle Mountain | 1275 N Community Cir, Eagle Mountain, UT 84005 | 133 MW | 133 MW | 2 | B300；Williams；Mortenson | |
| Los Lunas | 4250 Messenger Lp, Los Lunas, NM 87031 | 87 MW | 87 MW | 1 | B300 | |
| Sarpy | Fairview Rd, Springfield, NE 68059 | 80 MW | 80 MW | 1 | B300 | 与 Google Papillion 相邻 |
| Aiken | 7601 State Hwy 105, Trenton, SC 29847 | 69 MW | 69 MW | 1 | B300 | |
| Gallatin | 1 Meta Lp, Gallatin, TN 37066 | 0 | 未定 | 1 | B300 | 预计约 4 个月内投运 |

### 2.3 判断

- **两类园区。** Meta 的布局是"两个超大训练园区 + 一批 150–250 MW 的标准园区"。超大园区是 Prometheus、Hyperion，再加 El Paso、Lebanon；标准园区分布在 Rosemount、Jeffersonville、Temple、Kuna、Cheyenne、Huntsville 等十几个州。后者大多在 2026 年集中投运、换装 B300，承担推理和中等规模训练。
- **训练园区的光网络重心在园区内楼间。** Prometheus 和 Hyperion 都是单园区多楼（9–27 栋），楼间光互连的密度最高。
- **骨干网压力在增大。** 标准园区分散在全美，对骨干网的压力随推理量上升，这和 Meta 骨干团队讲的"光纤数每年翻倍"相互印证。

---

## 三、Google

### 3.1 规划

- **资本开支：** 2026 年指引上调到 1950–2050 亿美元。
- **德州：** 2025-11 宣布至 2027 年投资 400 亿美元，在 Armstrong County 和 Haskell County 新建 3 个园区；Haskell 园区配套新建光伏加储能。Google 称德州将成为其 AI 数据中心最多的地区。
- **印度：** Visakhapatnam AI Hub 投资 150 亿美元（2026–2030），2026-04 破土，环评批复 2.51 GW，是原先公布的 1 GW 的两倍多。
- **组网方式：** 多园区就近组团，例如 Iowa/Nebraska 4 个园区约 1 GW 用于 Gemini 训练。园区内用 TPU 超节点加 OCS，跨园区用 Decoupled DiLoCo 做异步训练。
- **代建：** 德州 Goodnight 园区由 Crusoe 和 Hoffman 承建，说明 Google 也开始借用第三方开发商来提速。
- **本地讲稿印证：**
  - Google 自己讲十年光学功耗降约 90%，线路系统已占约一半〔0920-am-Su2-B-01-Google p4〕；
  - Marvell 引用 Google 数据中心 144 机架、13,824 根光纤、48 台 OCS〔0920-pm-Su3-I-07-Marvell p6〕；
  - 中兴引用"俄亥俄 + 爱荷华组团，4 DC、80 km"〔0923-We5-B-中兴 p4〕。

### 3.2 园区清单（按规划规模排序）

| 园区 | 地址 | 当前 IT 功率 | 规划 IT 功率（时间） | 楼栋 | 芯片 | 备注 |
|---|---|---|---|---|---|---|
| Goodnight | 10001 Lima Rd, Claude, TX 79019（Armstrong County） | 0 | 1,006 MW（2027-10） | 6 | — | Crusoe、Hoffman 承建；能源 Serena；1 号楼预计 2027-03 投运 |
| Fort Wayne | 6015 Adams Center Rd, Fort Wayne, IN 46806 | 0（Epoch 口径） | 863 MW（2028-06） | 5 | — | 700 英亩；一期已投运（公司口径）；占用湿地有争议 |
| Omaha | 11110 State St, Omaha, NE 68142 | 237 MW | 395 MW（2028-07） | 5 | TPU v5e–v7 | |
| Columbus | 5076 S High St, Columbus, OH 43207 | 303 MW | 386 MW（2027-07） | 5 | TPU v5e–v7 | |
| Pryor（North） | 4581 Webb St, Pryor, OK 74361（Mayes County） | 368 MW | 368 MW | 2 | TPU v5e/v5p | 当前 Google 规模最大，约 64 万 H100 等效 |
| New Albany | 1101 Beech Rd SW, New Albany, OH 43054 | 333 MW | 333 MW | 4–5 | TPU v5e–v6e | 与 Meta Prometheus 同区 |
| Storey County | Storey County, NV（Reno 东） | 161 MW | 300 MW（2027-06） | 4 | TPU v4–v6e | |
| Lincoln | 5475 Cloud Ct, Lincoln, NE 68514 | 141 MW | 283 MW（2027-10） | 2 | TPU v6e/v7 | |
| Cedar Rapids | 5800 Edgewood Rd SW, Cedar Rapids, IA 52404 | 0 | 261 MW（2027-05） | 3 | — | 1 号楼预计 2026 年底投运 |
| Bristow | 13001 Rollins Ford Rd, Bristow, VA 20136 | 238 MW | 238 MW | 3 | TPU v5e–v7 | 北弗吉尼亚 |
| Council Bluffs（East） | 10410 Bunge Ave, Council Bluffs, IA 51503 | 237 MW | 237 MW | 3 | TPU v5e–v7 | |
| Papillion | Gold Coast Rd, Papillion, NE 68138 | 237 MW | 237 MW | 3+ | TPU v4–v5p | 4、5 号楼在建 |
| Mesa | Mesa, AZ | 183 MW | 183 MW | 2 | TPU v5p/v6e | |
| Red Oak | 330 Austin Blvd, Red Oak, TX 75154 | 77 MW | 154 MW（2026-12） | 2 | TPU v6e | 达拉斯南 |
| The Dalles | 3500 River Rd, The Dalles, OR | 154 MW | 154 MW | 2 | TPU v5e–v7 | Google 最早的自建园区所在地 |
| Lancaster | 105 Whiley Rd, Lancaster, OH 43130 | 137 MW | 137 MW | 2 | TPU v5e/v6e | |
| Kansas City East | Kansas City, MO | 105 MW | 105 MW | 1 | — | |
| Midlothian | 3250 Railport Pkwy, Midlothian, TX 76065 | 103 MW | 103 MW | 1 | TPU v6e/v7 | 达拉斯南 |
| Waltham Cross | Maxwell's Farm West, Great Cambridge Rd, Cheshunt EN8 8XH, UK | 88 MW | 88 MW | 1 | TPU v6e | 伦敦北 |
| Arcola | 42575 Arcola Blvd, Sterling, VA 20166 | 77 MW | 77 MW | 1 | TPU v6e/v7 | 北弗吉尼亚 |
| Visakhapatnam AI Hub | Visakhapatnam, Andhra Pradesh, India | 0 | 环评批复 2.51 GW | — | — | 与 AdaniConneX、Airtel 合作，150 亿美元 |
| Texas Haskell | Haskell County, TX | 0 | 未公布 | — | — | 配套光伏 + 储能 |

### 3.3 判断

- **均匀、可复制。** Google 的布局最均匀：二十多个园区，单园区多在 100–400 MW，每栋楼约 100 MW 的标准设计反复复制。
- **组团加异步训练。** 训练能力靠园区组团（Ohio 组团、Omaha 组团）加 TPU OCS 和 DiLoCo 获得，而不是靠单个超大园区。这也是 Google 对"园区间光纤对"需求大、对单园区超大功率依赖小的原因。
- **2027–2028 年的增量在新的 GW 级单园区。** 德州 Goodnight 约 1 GW、印第安纳 Fort Wayne 约 0.86 GW 是 Google 第一批真正意义上的 GW 级单园区，说明 Google 也在向"大单体"靠拢。

---

## 四、Microsoft

### 4.1 规划

- **资产形态：** 自称 400 多座数据中心、70 个区域；计划两年内整体规模约翻倍。
- **AI 训练骨干是 Fairwater 系列：**
  - Fairwater 1 在 Wisconsin，Fairwater 2 在 Atlanta；
  - 另有 Fairwater 4 在建，用 Pb/s 级网络连到 Atlanta，Milwaukee/Wisconsin 一带还有多个 Fairwater 在建；
  - 各园区经专用 AI WAN 连成"AI 超级工厂"，一年新增光纤 12 万英里以上。
- **大量租用 neocloud，承诺总额超过 600 亿美元：**
  - Nscale 约 230 亿美元（约 20 万颗 GB300）；
  - IREN 97 亿美元（德州 Childress 750 MW 园区）；
  - Nebius 新泽西 Vineland 与芬兰 Mäntsälä；
  - Lambda、CoreWeave。
- **国际：**
  - 接手原 Stargate Norway（Nscale/Aker，Narvik）；
  - Nscale 葡萄牙 Sines；
  - 英国 Loughton；
  - 英国计划 2025–2028 年投资 300 亿美元。
- **Abilene：** 接手 OpenAI 放弃的 Abilene 扩建地块，由 Crusoe 为 Microsoft 建设。
- **本地讲稿印证：**
  - 中兴引用 OFC 2026 Microsoft Workshop：单 DC 50–300 MW，下一代训练需 1–5 GW〔0923-We5-B-中兴 p4〕；
  - Credo 把 Fairwater 概括为"单一扁平网络"〔0920-pm-Su4-I-07-Credo p4〕；
  - Azure 计划未来 12 个月部署 12,000 km 以上空芯光纤〔0922-Tu3-H1-MicrosoftAzureFiber p29〕。

### 4.2 园区清单

| 园区 | 地址 | 所有者 | 当前 IT 功率 | 规划 IT 功率（时间） | 楼栋 | 芯片 / 能源 | 备注 |
|---|---|---|---|---|---|---|---|
| Fairwater Wisconsin | 4800 90th St, Mount Pleasant, WI 53403（Racine County） | Microsoft | 369 MW | 2,263 MW（2028-05） | 11 | B200；WE Energies | 2026-04 首栋投运；设计由原方案改为 9 栋扩建；原富士康地块 |
| Fairwater Atlanta | 1435 Hwy 54 W, Fayetteville, GA 30214（Fayette County） | Microsoft（QTS 代建） | 636 MW | 636 MW（总功率 859 MW） | 4 | B200；Georgia Power | 当前四家中最大的单园区；纯电网供电、两层楼 |
| Crusoe Abilene Expansion | 5502 Spinks Rd, Abilene, TX 79601 | Microsoft（Crusoe 代建） | 0 | 672 MW（2027-11） | 2 | — | 与 Stargate Abilene 同一地址 |
| Goodyear | 14250 W Broadway Rd, Goodyear, AZ 85338 | Microsoft | 202 MW | 202 MW | 4（5、6 号楼地基在建） | H100、B200 | 使用方含 OpenAI |
| Project Osmium | 5855 SW Kerry St, Cumming, IA 50061（West Des Moines 一带） | Microsoft | 190 MW | 190 MW | 4 | A100、H100、B200 | 使用方 OpenAI；早期 GPT 系列训练地 |
| San Antonio SAT40 | 15000 Lambda Dr, San Antonio, TX 78245 | Microsoft | 75 MW | 75 MW | 2 | H100、B300 | |
| San Antonio SAT14 | 3545 Wiseman Blvd, San Antonio, TX 78251 | Microsoft | 47 MW | 47 MW | 2 | H100、B300 | |
| Nebius New Jersey | 3963 S Lincoln Ave, Vineland, NJ | Nebius | 50 MW | 50 MW | 1 | B300 | 租用 |
| Nebius Mäntsälä | Mäntsälä, Finland | Nebius | 75 MW | 145 MW（2027-12） | 4 | H100、H200、B300 | 租用 |
| Start Campus Sines | Sines, Portugal | Nscale | 33 MW | 233 MW（2027-09） | 2 | B300 | 租用 |
| Narvik | Narvik, Norway | Nscale（Aker） | 0 | 92 MW（2026-12） | 2 | — | 原 Stargate Norway，2026-04 转给 Microsoft |
| IREN Childress | Childress, TX | IREN | — | 750 MW 园区 | — | GB300 | 97 亿美元五年合同（Epoch 未单列） |

### 4.3 判断

- **两条腿走路。** Microsoft 的布局是"少数超大自有园区 + 大量租用"。自有部分押注 Fairwater 系列：Wisconsin 一个园区到 2028 年就有 2.26 GW IT，是四家所有已知园区中规划最大的单园区。租用部分用来快速补缺口，Azure 容量紧张持续到 2026 年中。
- **WAN 最重的一家。** Fairwater 系列从一开始就按多园区设计，Atlanta 与 Wisconsin 相距约 1,100 km，Milwaukee 一带还有多个 Fairwater。Microsoft 是四家中对园区间 AI WAN、空芯光纤投入最重的一家。
- **在接 OpenAI 退出的站点。** Microsoft 在承接 OpenAI 退出的站点（Abilene 扩建、Narvik），与 OpenAI 的关系正在从"为 OpenAI 建"转向"按自己的算力池建"。

---

## 五、OpenAI

### 5.1 规划

- **Stargate 美国：** 10 GW 目标，2026-02 称已落实 8 GW 以上。Oracle 合同为 5 年 3000 亿美元、4.5 GW，从 2027 年起。
- **收缩：** 2030 年基础设施支出目标从 1.4 万亿美元下调到约 6000 亿美元。
  - Stargate UK 暂停，理由是"监管和能源成本"；
  - Stargate Norway 退出，由 Microsoft 接手，OpenAI 改为向 Microsoft 租用；
  - Abilene 原 2.1 GW 扩建计划取消；
  - 媒体报道还有其他国家项目暂停。
- **仍在推进的国际项目：**
  - Stargate UAE：G42 建设，Abu Dhabi Al Dhafrah，规划 1 GW，首期 200 MW 预计 2026 年底；
  - 印度：与 Tata/TCS HyperVault 合作，首期 100 MW，可扩到 1 GW。
- **算力来源分散：** 除 Stargate，还使用 Microsoft Fairwater、Goodyear、Osmium 和一批 CoreWeave 园区，并签了 Cerebras 750 MW 用于低时延推理。
- **本地讲稿印证：** OpenAI 的 Jalapeño 两级 scale-up 拓扑和推理指标〔0920-pm-Su3-A-02-OpenAI p5, p7, p8〕；中兴引用"OpenAI Abilene，3 个 DC、40 km"〔0923-We5-B-中兴 p4〕。

### 5.2 Stargate 站点

| 站点 | 地址 | 开发 / 运营方 | 当前 IT 功率 | 规划 IT 功率（时间） | 楼栋 | 能源 / 建设方 | 进展（2026-09/10） |
|---|---|---|---|---|---|---|---|
| Abilene | 5502 Spinks Rd, Abilene, TX 79601 | Crusoe 建设、Oracle 运营 | 421 MW | 843 MW（2026-11） | 8 | AEP；Mortenson；B200/B300 | 5–8 号楼结构完工、内装中 |
| Shackelford | 175 Private Road 1604, Abilene, TX 79601（Shackelford County） | Vantage（Frontier）/ Oracle | 0 | 1,400 MW（2028-11） | 10 | 现场燃气微网 | 1–5 号楼封顶，1 号楼预计 2027-08 投运 |
| New Mexico（Project Jupiter） | Santa Teresa, Doña Ana County, NM（NM-136 沿线，近 Santa Teresa 口岸） | STACK / Oracle | 0 | 1,750 MW（2028-12） | 4 | Bloom Energy 燃料电池；两座燃气微网 | 大面积土方和楼栋基础施工；县批 1650 亿美元工业收益债券 |
| Michigan（The Barn） | 11411 W Michigan Ave, Saline, MI 48176（Saline Township） | Related Digital / Oracle | 0 | 988 MW（2028-12） | 3 | DTE Energy + 储能 | 1 号楼地基阶段；250 英亩 |
| Wisconsin（Lighthouse） | Port Washington, WI（Milwaukee 北约 30 分钟车程） | Vantage / Oracle | 0 | 902 MW（2028-12） | 4 | 约 70% 可再生 | 1、2 号楼屋面约一半；672 英亩，总投资约 150 亿美元 |
| Milam | Milam County, TX（595 英亩） | SB Energy（SoftBank） | 0 | 857 MW（2028-12） | — | 新建光伏 + 储能 | 1 号楼钢结构与屋面施工；"快建"站点 |
| Lordstown | 2300 Hallock Young Rd, Warren, OH 44481 | SoftBank / 富士康 | 0 | 214 MW（2027-03） | 1 | 电网 | 以 AI 服务器制造为主，屋面基本完工 |
| UAE | Al Dhafrah, Abu Dhabi（项目办公室地址） | G42 / OpenAI / Oracle | 0 | 1,000 MW（2028） | 10 | — | 1、2 号楼部分建成，首期 200 MW 预计 2026 年底 |
| India | 未公开 | TCS HyperVault | 0 | 100 MW 起，可扩至 1 GW | — | — | 2026-02 宣布 |

美国 7 个 Stargate 站点的 IT 功率合计约 7.0 GW，按总功率约 9.7 GW，和"9 GW 以上"的公开口径一致。

### 5.3 非 Stargate 算力（OpenAI 为使用方）

| 园区 | 地址 | 所有者 | 当前 IT 功率 | 规划 IT 功率（时间） |
|---|---|---|---|---|
| Microsoft Fairwater Atlanta / Wisconsin、Goodyear、Osmium | 见第四节 | Microsoft | 合计约 1.4 GW | Wisconsin 到 2028 年 2.26 GW |
| CoreWeave Denton | 8171 Jim Christal Rd, Denton, TX 76207 | CoreWeave（Core Scientific 园区） | 262 MW | 282 MW（2027-05） |
| CoreWeave Helios | 984 County Road 112, Afton, TX 79220 | CoreWeave（Galaxy 园区） | 132 MW | 528 MW（2029-01） |
| CoreWeave Ellendale | 9685 87th Ave SE, Ellendale, ND 58436 | CoreWeave（Applied Digital 园区） | 68 MW | 400 MW（2027-06） |
| CoreWeave Chester | 1401 Meadowville Technology Pkwy, Chester, VA | CoreWeave | 82 MW | 113 MW（2027-06） |
| CoreWeave Muskogee | 1525 W 43rd St S, Muskogee, OK 74401 | CoreWeave（Core Scientific） | 0 | 153 MW（2027-12） |
| CoreWeave Lancaster | 216 Greenfield Rd, Lancaster, PA | CoreWeave | 0 | 92 MW（2027-06） |
| CoreWeave Marble | 155 Palmer Ln, Marble, NC 28905 | CoreWeave（Core Scientific） | 65 MW | 65 MW |
| CoreWeave Dalton | 2205 Industrial South Rd, Dalton, GA 30721 | CoreWeave | 28 MW | 28 MW |
| CoreWeave Norway | Stølevegen 39, 4715 Øvrebø, Norway | CoreWeave | 42 MW | 42 MW |

### 5.4 判断

- **OpenAI 不拥有任何园区。** 它的"数据中心版图"实际上是合作伙伴版图：Oracle 是 Stargate 的主要运营方，Crusoe、Vantage、STACK、Related Digital、SB Energy 是开发方，CoreWeave 和 Microsoft 提供现成算力。好处是轻资产、扩张快；代价是 2026 年需求预期下调时，可以、也已经在退出项目，而这些项目随即被 Microsoft 等接手。
- **Stargate 的 GW 级站点集中在 2027–2028 年投产。** Shackelford、New Mexico、Michigan、Wisconsin、Milam 合计 IT 约 5.9 GW。当前真正在用的只有 Abilene（421 MW）。
- **CoreWeave 园区多是比特币矿场改造。** Core Scientific、Galaxy、Applied Digital 原来都是矿企，园区在德州、北达科他、俄克拉何马、北卡等电力便宜但偏远的地方。这类园区对长距离 DCI 和城域光纤的依赖更强。

---

## 六、地理分布与园区群（与 Scale-across 光网络最相关）

距离按城镇中心直线估算，只作量级参考。

| 园区群 | 包含园区 | 公司 | 估算距离 | 光网络含义 |
|---|---|---|---|---|
| 俄亥俄中部 | Google New Albany、Columbus、Lancaster；Meta Prometheus（New Albany） | Google、Meta | New Albany–Columbus 约 30 km；Columbus–Lancaster 约 40 km；Meta 与 Google New Albany 同一产业园 | Google 典型的组团式训练；园区间 20–40 km，适合 Coherent-Lite 或 ZR |
| 俄亥俄北部 | Meta Bowling Green；Stargate Lordstown | Meta、OpenAI | 距 Columbus 组团约 160–250 km | 区域级 ZR/ZR+ |
| 内布拉斯加/艾奥瓦 | Google Council Bluffs、Omaha、Papillion、Lincoln、Cedar Rapids；Meta Sarpy | Google、Meta | Council Bluffs–Omaha 约 15–20 km；Omaha–Papillion 约 15 km；Papillion–Lincoln 约 75 km；Cedar Rapids 约 370 km | Gemini 训练组团（约 1 GW） |
| 德州西部 Abilene | Stargate Abilene、Microsoft Crusoe 扩建（同地址）、Stargate Shackelford | OpenAI、Microsoft | Abilene–Shackelford 约 40–50 km | 中兴讲稿"3 个 DC、40 km"即此 |
| 德州达拉斯南 | Google Midlothian、Red Oak；CoreWeave Denton（北） | Google、OpenAI | Midlothian–Red Oak 约 25 km；Denton 约 80 km | |
| 德州潘汉德尔 | Google Goodnight（Claude）；CoreWeave Helios（Afton） | Google、OpenAI | 约 150 km | 新兴 GW 区，远离骨干，需要新建长途光纤 |
| 德州中部 | Meta Temple；Stargate Milam；Microsoft San Antonio | Meta、OpenAI、Microsoft | Temple–Milam 约 50–60 km | |
| 威斯康星东南 | Microsoft Fairwater Wisconsin；Stargate Port Washington | Microsoft、OpenAI | 约 75 km | Microsoft 称 Milwaukee 一带还有多个 Fairwater |
| El Paso–Santa Teresa | Meta El Paso；Stargate Project Jupiter | Meta、OpenAI | 约 25 km | 两家 GW 级园区相邻，跨境口岸附近 |
| 北弗吉尼亚 | Google Bristow、Arcola；CoreWeave Chester（南） | Google、OpenAI | Bristow–Arcola 约 30 km | 传统云核心区 |
| 凤凰城 | Microsoft Goodyear；Google Mesa | Microsoft、Google | 约 60 km | |
| 犹他 Eagle Mountain | Meta Eagle Mountain、QTS Eagle Mountain（Meta） | Meta | 同一城镇 | |
| 跨区域 | Fairwater Atlanta ↔ Fairwater Wisconsin | Microsoft | 直线约 1,100 km | 专用 AI WAN，一年新增光纤 12 万英里 |

整体看，"同地区多家扎堆"已成常态，原因有三：

- 电力和输电资源只在少数地点可得；
- 开发商（Crusoe、Vantage、QTS、STACK、Core Scientific）同时服务多家；
- 产业园区的税收优惠一次性批给多个项目（如 New Albany、Abilene、Santa Teresa）。

对光网络来说，园区群内 20–80 km 的大容量互联（Coherent-Lite、ZR、多 rail 线路系统、空芯光纤）是最直接的增量市场。

---

## 七、横向比较与判断

| 维度 | Meta | Google | Microsoft | OpenAI |
|---|---|---|---|---|
| 单园区规模 | 两个超大园区（1–5 GW），其余 150–250 MW | 多为 100–400 MW，开始出现 0.9–1 GW | Wisconsin 2.26 GW、Atlanta 0.64 GW | Stargate 0.2–1.75 GW |
| 训练集群形态 | 单园区多楼 | 园区组团 + OCS + 异步训练 | 跨区域 AI WAN 连成超级工厂 | 依托合作方，Abilene 为主力 |
| 建设速度 | 最快（帐篷式） | 稳定滚动 | 两层楼高密度设计 | 取决于合作方，多数 2027–2028 年 |
| 电力策略 | 自建燃气电厂、电力公司专项 | 电网为主，新园区配光伏储能 | 纯电网（Atlanta）、本地电力公司 | 燃气微网、燃料电池、光伏储能 |
| 资本结构 | 合资融资（Blue Owl、BlackRock） | 资产负债表内 | 自建 + 租用（>600 亿美元） | 全部租用，2026 年收缩 |
| 2026 年变化 | 标准园区集中投运，GW 园区开工 | 德州、印度、Fort Wayne 新 GW 级项目 | 接手 OpenAI 退出站点 | 支出目标下调，退出英国、挪威 |

**对光互连的含义：**

1. **园区内楼间互联。** Meta 的 Prometheus、Hyperion（9–27 栋）和 Microsoft Fairwater Wisconsin（11 栋）这类单园区多楼形态，楼间 500 m–2 km 的高密度光互连需求最大。
2. **园区群之间的 20–80 km 互联。** Google 的组团式形态和各地的园区群，带来 Coherent-Lite、ZR/ZR+ 和多 rail 线路系统的需求。
3. **跨区域互联。** Microsoft 的跨区域 AI WAN（约 1,100 km）、OpenAI 分散在多个合作方的园区，需要长途、大容量、低时延的骨干网，也是空芯光纤的主要试验场。
4. **新兴偏远 GW 区。** 德州潘汉德尔、北达科他、路易斯安那东北部远离现有骨干，需要新建长途光纤路由，这正是 Meta 骨干团队所说"物理层必须领先"的场景。

---

## 八、数据可靠性

- **Epoch 的时间线是推算的。** 它基于卫星图像和监管文件，会随新影像修正（例如 Gallatin 尚无功率数据，Fort Wayne 公司称一期已投运但 Epoch 记为 0）。
- **街道地址的性质。** 街道地址多为地块或项目登记地址，与园区实际出入口可能不同；Stargate UAE 是项目办公室地址。
- **公司口径不能直接加总。** "1 GW""5 GW"一般指园区总电力容量，不是 IT 功率，不能直接与 Epoch 的 IT 功率相加。
- **租用关系变化快。** 例如 Anthropic 也在使用 xAI Colossus 2，OpenAI 与 Microsoft 的站点归属在 2026 年多次调整。引用前建议到 Epoch 页面核对最新版本。

---

## 来源

- Epoch AI 数据集与目录：https://epoch.ai/data/ai-data-centers （CSV：https://epoch.ai/data/data_centers/data_centers.csv ；时间线：https://epoch.ai/data/data_centers/data_center_timelines.csv）
- Epoch AI，Stargate 各站点现状：https://epoch.ai/publications/openai-stargate-where-the-us-sites-stand
- Meta Compute：https://www.datacenterdynamics.com/en/news/meta-establishes-meta-compute-plans-multiple-gigawatt-plus-scale-ai-data-centers/
- Meta El Paso：https://www.cnbc.com/2026/03/26/meta-to-spend-10-billion-on-ai-data-center-in-el-paso-1gw-by-2028.html ；https://www.datacentermap.com/usa/texas/el-paso/meta-el-paso-campus/
- Meta Lebanon：https://about.fb.com/news/2026/02/metas-new-data-center-lebanon-indiana-marks-milestone-ai-investment/
- Meta Hyperion 合资：https://investor.atmeta.com/investor-news/press-release-details/2025/Meta-Announces-Joint-Venture-with-Funds-Managed-by-Blue-Owl-Capital-to-Develop-Hyperion-Data-Center/default.aspx
- Google 德州 400 亿美元：https://blog.google/company-news/inside-google/company-announcements/google-american-innovation-texas/
- Google 印度 AI Hub：https://blog.google/intl/en-in/company-news/our-first-ai-hub-in-india-powered-by-a-15-billion-investment/ ；环评 2.51 GW：https://technosports.co.in/google-india-ai-hub-251gw/
- Google Fort Wayne：https://www.wane.com/top-stories/2-billion-google-data-center-now-operational-in-fort-wayne-outlines-its-plans-for-the-community/
- Microsoft Fairwater：https://news.microsoft.com/source/features/ai/from-wisconsin-to-atlanta-microsoft-connects-datacenters-to-build-its-first-ai-superfactory/ ；https://www.datacenterfrontier.com/hyperscale/article/55317925/inside-microsofts-global-ai-infrastructure-the-fairwater-blueprint-for-distributed-supercomputing
- Microsoft neocloud 承诺：https://introl.com/blog/microsoft-60-billion-neocloud-spending-capacity-crunch-december-2025
- OpenAI 退出挪威 / 暂停英国：https://www.cnbc.com/2026/04/15/openai-stargate-norway-project-microsoft.html ；https://www.investmentmonitor.ai/news/openai-pauses-stargate-uk/
- Stargate Project Jupiter：https://elpasomatters.org/2025/09/25/stargate-open-ai-oracle-project-jupiter-data-center-dona-ana-new-mexico-el-paso-texas/
- Stargate Michigan：https://www.related-digital.com/news/openai-oracle-and-related-digital-announce-stargate-data-center-site-in-michigan
- Stargate Port Washington：https://vantage-dc.com/data-center-locations/north-america/port-washington-wisconsin
- Stargate Milam：https://pv-magazine-usa.com/2026/01/12/sb-energy-secures-1-billion-from-openai-and-softbank-for-stargate-datacenter-expansion/
- OpenAI 印度：https://www.digitimes.com/news/a20260219VL204.html
