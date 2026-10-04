---
title: "AI 数据中心电力与投资分析：100 MW 与 1 GW"
tags:
  - AI数据中心
  - 电力
  - 专题洞察
date: 2026-10-01
---

## 结论

- 一个 **100 MW** 的 AI 数据中心：
  - 投资约 **50 亿美元**。
  - 电费：中国西部约 **3 亿元/年**，美国约 **0.75 亿美元/年**，德国约 **1.1 亿欧元/年**。
- **1 GW** 的规模：投资约 **350–600 亿美元**（常用基准 500 亿），电费约为 100 MW 的 10 倍。
- **电费只占投资的 1–2.5%/年**，大头是算力设备折旧。选址逻辑是“先有电，再看电价”。

## 计算口径

| 项目 | 取值 | 说明 |
|---|---|---|
| 规模含义 | 100 MW / 1 GW 指 **IT 负载** | 服务器与网络设备的用电 |
| PUE | 1.2 | 液冷 AI 集群；直接液冷一般为 1.10–1.20，风冷 1.5–1.8 |
| 平均负载 | 基准 80%，上限 100% | 满载时电费约为基准的 1.25 倍 |
| 汇率 | 1 美元 = 7.1 元，1 欧元 = 1.15 美元 | 假设 |

按这个口径，100 MW 的设施平均功率为 96 MW，日用电 2,304 MWh，年用电约 8.4 亿 kWh。1 GW 的数字均乘以 10。

## 一、电力开销分布（IT 负载 100 MW，PUE 1.2，满载时设施功率 120 MW）

| 用电去向 | 占设施总用电 | 100 MW 规模 | 1 GW 规模 | 依据 |
|---|---|---|---|---|
| 加速器计算（GPU/XPU 托盘，含 CPU、HBM） | 约 70% | 约 84 MW | 约 840 MW | 估算 |
| 网络（scale-up/out 交换机 + 光模块） | 约 6–8% | 约 8 MW | 约 80 MW | ECOC 2026 NVIDIA：网络占总功耗 6–8%〔E26 NVIDIA-CPO p8, p16〕 |
| 存储与其他 IT | 约 5–6% | 约 7 MW | 约 70 MW | 估算 |
| 冷却（液冷 CDU、冷机、风扇） | 约 11–12% | 约 14 MW | 约 140 MW | 由 PUE 1.2 推算 |
| 供配电损耗与照明 | 约 4–5% | 约 6 MW | 约 60 MW | 由 PUE 1.2 推算 |

## 二、投资费用分布（以 1 GW 约 500 亿美元为基准）

| 投资项 | 占比 | 1 GW | 100 MW |
|---|---|---|---|
| 计算芯片与服务器（其中 GPU 约 39%） | 约 55–60% | 约 280–300 亿美元 | 约 28–30 亿美元 |
| 机房建筑与机电（供配电、液冷、土建） | 约 25–35% | 约 110–180 亿美元 | 约 11–18 亿美元 |
| 网络（交换机、网卡、光模块、布线） | 约 8–10% | 约 40–50 亿美元 | 约 4–5 亿美元 |
| 存储与其他 IT | 约 3–5% | 约 15–25 亿美元 | 约 1.5–2.5 亿美元 |
| 土地、电网接入、前期费用 | 约 2–5% | 约 10–25 亿美元 | 约 1–2.5 亿美元 |

- 建筑与机电：JLL 给出 2026 年外壳与核心 1,130 万美元/MW，AI 装修另加最高 2,500 万美元/MW；Cushman & Wakefield 给出不含芯片 1,760 万美元/MW。
- 总额：NVIDIA 口径约 500–600 亿美元/GW，Bernstein 估算约 350 亿美元/GW。
- “网络”“存储”“土地”三项为估算。

## 三、四个地区的电费（基准：80% 负载，PUE 1.2）

| 地区与电价 | 100 MW 每天 | 100 MW 每年 | 1 GW 每天 | 1 GW 每年 |
|---|---|---|---|---|
| 中国·西部算力枢纽（含补贴）0.36 元/kWh | 83 万元 | 3.0 亿元 | 829 万元 | 30.3 亿元 |
| 中国·西部一般工业（35 kV 以上）0.53 元/kWh | 122 万元 | 4.5 亿元 | 1,221 万元 | 44.6 亿元 |
| 德国·年用电 >150 GWh 的大用户 13.07 欧分/kWh | 30.1 万欧元 | 1.10 亿欧元 | 301 万欧元 | 11.0 亿欧元 |
| 德国·享受最大减免 10.73 欧分/kWh | 24.7 万欧元 | 0.90 亿欧元 | 247 万欧元 | 9.0 亿欧元 |
| 美国·工业均价 8.89 美分/kWh | 20.5 万美元 | 0.75 亿美元 | 205 万美元 | 7.5 亿美元 |
| 美国·低价州（如新墨西哥）5.41 美分/kWh | 12.5 万美元 | 0.46 亿美元 | 125 万美元 | 4.6 亿美元 |
| 北欧·瑞典（批发 + 电网费 + 税费）约 5.9 欧分/kWh | 13.6 万欧元 | 0.50 亿欧元 | 136 万欧元 | 5.0 亿欧元 |
| 北欧·风电长期购电协议（PPA）约 4.25 欧分/kWh | 9.8 万欧元 | 0.36 亿欧元 | 98 万欧元 | 3.6 亿欧元 |

按满载计算，以上数字都乘以 1.25。

## 四、判断

1. **地区间差距约 3 倍**：1 GW 在德国每年电费约 11 亿欧元，在中国西部约 4.3 亿美元。五年累计相差约 40 亿美元，相当于一个 100 MW 园区的全部投资。
2. **电费远小于设备折旧**：1 GW 的计算设备按 5 年折旧，每年约 56–60 亿美元，是美国电费的 7–8 倍。选址优先考虑电力供给能力与绿电比例。
3. **光互连节能的价值**：网络占总功耗 6–8%，CPO 可把这部分降到约五分之一。1 GW 可省约 50–60 MW，在美国每年约 4,000–5,000 万美元；更重要的是，省下的电可多装约 5% 的 GPU。

## 参考来源

- 每 GW 投资：[Yahoo / 24/7 Wall St.](https://finance.yahoo.com/technology/ai/articles/nvidia-ceo-says-1-gigawatt-120010810.html)、[Investing.com](https://www.investing.com/news/stock-market-news/how-much-does-a-gw-of-data-center-capacity-actually-cost-4314046)
- 建设成本每 MW：[JLL / Cushman 汇总](https://axis-intelligence.com/data-center-construction-cost-statistics/)
- PUE：[液冷 PUE 统计](https://nriglobe.com/technology/ai-data-center-cooling-methods-2026-air-direct-to-chip-liquid-immersion-pue-nvidia-gb200-rack-density-explained/)
- 中国电价：[乌兰察布数据中心电价](https://www.progressiverobot.com/2026/09/23/inner-mongolia-china-ai-data-centres-ulanqab/)、[36 城工业电价（35 kV 以上）](https://www.ceicdata.com/en/china/price-monitoring-center-ndrc-36-city-monthly-avg-transaction-price-production-material/cn-usage-price-36-city-avg-electricity-for-industry-35-kv-and-above)、[西部电价与补贴](https://techchannel.news/china-cuts-data-centre-energy-costs-to-rev-up-homegrown-chip-adoption/)
- 德国电价：[BDEW / SMARD 2026](https://etalytics.com/resources/blog/current-industrial-electricity-price-in-germany)
- 美国电价：[EIA 2026 工业均价](https://datacenterscope.com/power/electricity-cost-by-state/)
- 北欧电价：[瑞典电价与 PPA](https://techplustrends.com/ai-data-center-energy-cost-europe-market-guide/)
