---
title: "AI 数据中心布局与训练/推理流量调度：面向光互连的深度洞察"
tags:
  - AI数据中心
  - 光互连
  - 专题洞察
date: 2026-10-01
---

版本 v2 · 2026-10-01（新增 1.7 节：按训练与推理拆分各家部署） · 面向光通信专业读者

材料来源分三类，正文逐条标注：

- 本地索引 ECOC 2026 讲稿笔记，标注格式〔讲稿文件名简写 pN〕，可在 `_insight_index/talk_notes/` 里按文件名检索原页。
- 本地索引 ECOC 2025 / OFC 2026 论文，标注格式〔OFC26 W4H.5〕〔ECOC25 Tu.04.06.2〕，原文在 `MyNote/content/private/ECOC2025-OFC2026/_index/`。
- 互联网公开资料（公司博客、论文、媒体报道），标注〔网〕并在文末列出链接。媒体口径的数字（尤其是 GPU 数量、投资额）误差较大，只能当量级参考。

口径标注沿用之前的约定：自报、仿真、实验、现网、媒体报道、本文估算。

---

## 〇、先说结论

1. **约束顺序已经变成"电 → 地 → 光纤 → 芯片"。** 2026 年北美头部厂商宣布的单园区规模普遍在 1–5 GW，选址第一条件是能否在 18–24 个月内拿到电，很多园区直接自建燃气机组绕开并网排队。光纤是第三位的约束，但它决定了多个园区能不能"拼"成一个训练集群。

2. **单园区装不下下一代训练任务，多园区训练已从论文走到生产。** Microsoft 用专用 AI WAN 连接 Wisconsin 和 Atlanta 两个 Fairwater 园区；Google 在 Iowa/Nebraska 用 4 个相距 15–50 英里的园区拼约 1 GW 训练集群；Meta 的 Llama 4 用了跨多栋楼的 10 万卡以上集群。中国运营商在 2026 年给出了 100–410 km 跨域训练效率 97%–98% 的现网结果。

3. **流量在物理上严格分层，这是理解一切调度问题的钥匙。** 按本文对 Llama 3 405B 配置的估算，每 GPU 每步：张量并行约 235 GB，MoE 专家并行同量级，数据并行约 13 GB，流水线并行约 1 GB。所以 TP/EP 必须留在超节点（NVLink/灵衢）里，PP 可以跨机架、跨楼，能跨园区的只有 DP（以及更进一步的异步外层同步）。

4. **跨园区的带宽需求是 DP 带宽，量级在每对园区数十 Tb/s 到 Pb/s。** ZTE 给出 1024 卡 70B 模型跨 600 km 所需 3.2–16 Tb/s〔OFC26 W4H.5〕，GPT-4 级模型约 3–300 Tb/s，10T MoE 约 17 Tb/s–1.7 Pb/s〔0923-We5-B-中兴 p5〕。这正是 Scale-across 的部署单位从"波长"变成"光纤对"的原因。

5. **距离的代价在 10–30 km 之后开始显现，100 km 内基本可控。** Corning 仿真显示 H100 的计算-通信重叠效率在 10–30 km 后下降，1000 km 时训练时间变为约 26 倍〔0924-Th1-G1-Corning p8, p10〕。实测侧，城域分布式训练只慢 7%，长途慢 37%〔ECOC25 Tu.04.06.2〕。异步训练算法（Google Decoupled DiLoCo 带宽降 236 倍）会把这个边界继续推远。

6. **推理的流量模型和训练完全不同。** 训练是少量巨大、同步、周期性的流；推理是海量小请求，瓶颈在时延和 KV cache 搬运。Prefill 和 Decode 分离部署后，KV cache 传输（一次 32K 上下文的 70B 模型约 10 GB）成为新的楼内流量。Decode 阶段的大 EP all-to-all 对时延极敏感，单跳时延比带宽更关键〔0922-PF-1155-SalienceLabs p5, p6〕。

7. **多 Agent 推理把流量从"南北向"变成"东西向"，把 CPU 和存储拉回关键路径。** Agent 多轮调用的 KV cache 命中率常在 95% 以上，I/O 而非算力成为瓶颈；CPU:GPU 比例从 1:4–1:8 向 1:1 移动〔网〕。美团在 ECOC 的判断是网络必须从尽力而为转向感知负载〔0923-MF-美团 p18〕。

8. **中美两边的结构性差异在超节点规模和跨域训练的必要性上。** 北美以 NVL72（2026 年 Rubin 进入 NVL144 口径）为超节点，靠单园区 GW 级规模；中国单卡算力受限，用 384 卡到 8192 卡的超大超节点（华为 CloudMatrix384、Atlas 950）弥补，同时更依赖跨园区和"东数西算"的集群协同，对超节点内光互连和 Scale-across 的需求都更早、更强。

9. **调度是四层嵌套问题：区域选园区、园区选楼、楼内选超节点、超节点内选 GPU。** 每一层对应一种并行维度和一种光互连技术。调度器的目标函数正从"GPU 利用率"转向"满足 SLA 下每瓦每秒请求数"〔0920-pm-Su3-A-02-OpenAI p5〕和"有效训练时间"（Meta FT-HSDP 把有效训练时间从 44% 拉到 80%〔网〕）。

10. **对光通信产业的含义：** 超节点内光化（NPO/CPO/XPO）、楼内 1.6T/3.2T、园区 Coherent-Lite、园区间 ZR/ZR+ 加多 rail 线路系统，这四档需求都由流量分层直接推导出来，不是孤立的技术路线之争。最大的新增量在园区间线路系统（2030 年占 Scale-across 支出 55%〔0922-MF-am-1140-CignalAI p9〕）和超节点光化。

---

## 第一部分：北美与中国头部厂商的数据中心规划、选址与建设

### 1.1 总盘子

| 指标 | 北美 | 中国 | 口径 |
|---|---|---|---|
| 2026 年头部厂商资本开支 | Amazon 约 2200 亿美元、Alphabet 1950–2050 亿、Microsoft 约 1900 亿（FY 口径）、Meta 1300–1450 亿、Oracle 约 500 亿；合计 7000–8000 亿美元量级 | 阿里年化 1500–2000 亿元；字节 1600–2000 亿元；腾讯 Q2 单季 527.8 亿元；百度 Q2 单季 114 亿元；合计约 5000–6000 亿元（约 700–850 亿美元） | 媒体报道 / 财报 |
| 单园区规模 | 1–5 GW（Hyperion 规划 5 GW，Colossus 约 2 GW，Rainier 约 2.2 GW） | 主流 100–300 MW，头部规划向 GW 级走（阿里 2032 年全球总规模 >20 GW） | 媒体报道 / 自报 |
| 全国智算总量 | — | 截至 2026 年 3 月约 188 万 PFLOPS；八大枢纽之间 20 ms 时延圈 | 官方 |
| 超节点形态 | NVIDIA NVL72（GB200/GB300）、Google TPU Ironwood 9216 芯片 pod、AWS Trainium2 UltraServer、OpenAI 自研 Jalapeño 128/2048 两级域 | 华为 CloudMatrix384、Atlas 950 SuperPoD（8192 卡，2026 Q4）、阿里灵骏真武 M890 | 自报 |

两边的投资额差距约 8–10 倍，但这不完全等于算力差距。中国的芯片单价和建设成本低，单位 GW 的投资也更低。

ECOC 2026 上几条数字可以作为对照：Cignal AI 统计 2026Q2 北美云光硬件收入同比 +81%，占全球 45%〔0922-MF-am-1140-CignalAI p5〕；Nokia 引用的已宣布超大规模容量约 190 GW〔0920-pm-Su3+Su4-A-00-全场 p111〕；IDTechEx 数据中心需求从 2022 年约 45 GW 到 2030 年约 200 GW〔0921-MF-am-T06-1140-Coherent p3〕。

### 1.2 选址逻辑：电力排第一

把各家 2025–2026 年新园区放在一起看，选址条件的优先级相当一致：

1. **电力可得性和时间。** 并网排队在美国很多州已到 3–7 年。解决办法有三种：自建燃气机组（Stargate 的 Abilene、Shackelford、Doña Ana 三个园区用燃气微网；xAI 在 Southaven 运行了 27 台燃气轮机约 495 MW，并因此被起诉〔网〕）；与电力公司捆绑建设（Meta 为 Hyperion 出资 Entergy 新建燃气电厂，总账接近 270 亿美元〔网〕）；选电网富余地区（Microsoft Atlanta 宣称以三个九的成本做到四个九可用性〔网〕）。中国这边对应的是西部绿电和低电价：乌兰察布电价约 0.3 元/kWh，阿里称每年因此省电费约 50 亿元〔网〕。
2. **土地和规划许可。** GW 级园区通常要 1000 英亩以上（Shackelford 1200 英亩 10 栋楼，Hyperion 4000 英亩）。地方抵制开始出现，比如 Lordstown 有本地数据中心禁令〔网〕。
3. **水和冷却。** 新园区基本都是闭环液冷，Microsoft 称 Fairwater 初次注水量约等于 20 户家庭一年用水〔网〕。
4. **光纤和时延。** 训练园区可以远离用户，但要能和其他园区拉起大量光纤对；推理园区要靠近用户和互联网交换点。Meta 骨干团队的表述很直接：站点空间与电力（而非光纤本身）已经是骨干扩展的瓶颈，最大路由光纤数约每年翻倍，2031 年超过 1000 芯〔0921-MF-am-T08-1220-Meta p12〕。BT 的说法是"数据中心位置由空间和电力决定，然后再去布光纤"〔0920-am-Su1-C-00-上半场速记 p18–26〕。
5. **建设速度。** xAI 的 Colossus 1 用 122 天建成；Meta 在 Prometheus 用帐篷式临时结构加快投产〔网〕；阿里把大型 AIDC 交付周期压缩到 100 天，模块化后单位面积算力密度为上一代的 5–10 倍〔网〕。美团引用 Epoch AI 的估计，GW 级数据中心平均约 2.1 年建成〔0923-MF-美团 p4〕。

中国多了一层政策约束：东数西算的 8 个枢纽、10 个集群（张家口、芜湖、韶关、天府、重庆、和林格尔、乌兰察布、贵安、庆阳、中卫）。训练和离线任务往西部集群放，时延敏感的推理和在线业务留在东部枢纽，业内常说"西训东推"。

### 1.3 北美各家

#### Microsoft（含为 OpenAI 建设的部分）

- **Fairwater 系列。** Wisconsin（Mount Pleasant）和 Atlanta 两个园区已投产，官方称它们组成"首个 AI 超级工厂"〔网〕。设计要点：
  - 两层楼建筑，三维摆放机架，以缩短线缆长度和时延；
  - 机架约 140 kW，单排 1360 kW，每机架最多 72 颗 Blackwell GPU（NVL72），机架内 NVLink 1.8 TB/s；
  - 楼内为两级以太网后端网络，GPU 间 800 Gb/s，跑 SONiC，宣称把"数十万" GPU 组成一台超级计算机；
  - 园区之间用专用 AI WAN，一年新增光纤 12 万英里以上。
- **工作负载。** 官方列出预训练、微调、强化学习、合成数据生成。AI WAN 的作用是让不同园区"弹性地"承接这些任务，而不是固定绑定。
- **ECOC 上的口径。** 中兴引用 OFC 2026 Microsoft Workshop 的数据，单个 DC 电力 50–300 MW，下一代训练需要 1–5 GW〔0923-We5-B-中兴 p4〕。这说明 Microsoft 的策略是"多个中等规模园区 + 高速光网"拼集群，而不是只押一个 5 GW 园区。Credo 的拓扑对比页把 Fairwater 概括为"单一扁平网络"〔0920-pm-Su4-I-07-Credo p4〕。
- **光的角色。** Microsoft 是空芯光纤最积极的部署方，计划未来 12 个月部署 12,000 km 以上〔0922-Tu3-H1-MicrosoftAzureFiber p29〕。AI WAN 和空芯光纤是同一个问题的两面：把园区间时延压低，扩大可以同步训练的地理半径。

#### OpenAI / Stargate

| 站点 | 开发方 | 规划容量 | 状态（2026-09） |
|---|---|---|---|
| Abilene, TX | Crusoe / Oracle | 1.2 GW（8 栋楼，4 栋已运行，约 0.3 GW） | 2026 Q4 完工；原 2.1 GW 扩建计划取消，Microsoft 在旁另建约 900 MW |
| Shackelford County, TX | Vantage | 2.0 GW（10 栋楼，1200 英亩） | 首栋 2026 年底，2028 Q4 完工 |
| Doña Ana County, NM | STACK（Project Jupiter） | 2.2 GW（4 栋大楼） | 2028 Q4 |
| Milam County, TX | SB Energy | 1.2 GW | 首栋 2026-10，2028 Q4 |
| Port Washington, WI | Vantage | 1.3 GW | 2028 Q4 |
| Saline Township, MI | Related Digital | 1.4 GW | 2028 Q4 |
| Lordstown, OH | 软银/富士康 | <0.3 GW（主要是服务器制造） | 不明 |

来源：Epoch AI 站点追踪〔网〕。合计 9 GW 以上，2029 年前后到位。

除 Stargate 外，OpenAI 还从 Microsoft Azure、Oracle、CoreWeave、AWS、Google Cloud 多方租用算力，并与 NVIDIA、AMD、Broadcom 签了多 GW 级芯片协议（媒体报道，具体数额以公告为准）。这意味着 OpenAI 的训练和推理天然分布在多个云、多个园区上，跨园区调度是它的常态。

技术面，OpenAI 在 ECOC 讲了两件事〔0920-pm-Su3-A-02-OpenAI p5–p8〕：

- 自研加速器 Jalapeño 的 scale-up 网络：本地域 128 颗芯片接 Broadcom TH6，全局域 2048 颗芯片经 8 个 TH6 rail 组成"半扁平"两级 Clos。张量并行要高带宽，专家并行带宽要求较低，两者都要低时延。
- 与 GB300 MTP 对比，同吞吐下请求时延约低 1.8 倍，单用户解码速度可到约 700 tokens/s（自报）。

这说明 OpenAI 的芯片和网络是围绕推理（尤其是低时延 decode）设计的。

#### Meta

- **Prometheus（Ohio New Albany）。** 2026 年上线，号称首个 GW 级 AI 训练集群，园区由多栋楼组成〔网〕。
- **Hyperion（Louisiana Richland Parish）。** 2028 年首期，2030 年 2 GW，最终 5 GW，占地 4000 英亩；STMicro 讲稿称其面积可覆盖曼哈顿大部分〔0920-am-Su1-C-03-STMicro p2〕；Meta 骨干报告的新闻截图写的是"扩至 5 GW、投资超 500 亿美元"〔0921-MF-am-T08-1220-Meta p3〕。
- **El Paso（Texas）。** 1 GW，与 BlackRock 合资〔网〕。另有 30 多个已知数据中心园区。
- **训练集群。** Llama 3 用 2.4 万卡集群，Llama 4 用了跨多栋楼的 10 万卡以上集群；Meta 的 FT-HSDP 论文写的是在 1.6 万到 20 万卡、跨多栋楼的集群上训练的经验〔网〕。
- **骨干网投入。** 这是光通信读者最该关注的一页〔0921-MF-am-T08-1220-Meta p6–p14〕：
  - 城域架构是双光纤环加 4 条可扩展长途链路、2 个大型 POP，DC 楼栋直连环；
  - IP 网从 4 平面扩到 8 平面，800G，scale up 加 out 合计约 100 倍；
  - IP 与光集成（去转发器）后，同容量总功耗降约 80%；
  - ILA 站房四代演进：48 rails / 2 kW 每柜 → 112 rails → 512 rails / 3 kW → 2027 年以后最多 4096 rails、单柜 18 kW 以上，液冷，每光纤对成本降约 8 倍；
  - 自建站房数量两年约 4 倍。
- **流量。** Acacia 引用 Meta 在 OFC 2026 Executive Forum 的流量图，DC 间同步和 GW 级集群之间的流量是 2026 年增长最快的部分〔0920-pm-Su4-A-03-Acacia p3〕。

#### Google

- **训练集群形态。** 多园区就近组网。Iowa/Nebraska 的 Council Bluffs、Omaha、Papillion 三个园区相距约 15 英里，Lincoln 约 50 英里外，合计约 1 GW，用于 Gemini 训练〔网〕。中兴讲稿把 Google 俄亥俄加爱荷华概括为"4 DC、80 km"的 scale-across 规划〔0923-We5-B-中兴 p4〕。
- **芯片和超节点。** TPU 体系。Ironwood 单 pod 9216 芯片，pod 内是 ICI 加光路交换（OCS）。Credo 讲稿提到 TPU 8i 的 Boardfly 拓扑（36 组全连接，每 pod 最多 1152 芯片）和 Virgo 扁平高 radix 光网络〔0920-pm-Su4-I-07-Credo p4, p5〕。
- **对外供给。** 2026 年 4 月与 Anthropic 签约约 5 GW TPU 容量；与 Blackstone 合资的 TPU 云 2027 年首批 500 MW〔网，媒体口径〕。
- **多数据中心训练是 Google 的长期优势。** Gemini 1.5 起就采用多数据中心训练〔网〕。2026 年 4 月 DeepMind 发布 Decoupled DiLoCo：在美国 4 个区域、混合 TPU v6e/v5p 上训练 12B 模型，带宽比同步训练低 236 倍，质量与单数据中心持平〔网〕。
- **功耗视角。** Google 在 ECOC 讲十年间光学功耗降约 90%，但线路系统功耗几乎没降，现在约占总功耗一半〔0920-am-Su2-B-01-Google p4〕。

#### Amazon / AWS

- **Project Rainier（Indiana New Carlisle）。** 2025 年 10 月全面投产，32 栋楼，约 650 万平方英尺，满建电网取电约 2.25 GW，近 50 万颗 Trainium2，主要给 Anthropic 训练 Claude。Mississippi Canton 有第二个较小园区〔网〕。
- **Anthropic 合作。** 媒体报道 Anthropic 承诺 10 年在 AWS 投入超 1000 亿美元算力、预留最多 5 GW Trainium，2026 年底 Trainium2/3 合计约 1 GW 上线〔网，媒体口径〕。
- **网络。** Credo 讲稿把 AWS 的网络概括为"准随机图加无源光 ShuffleBox"〔0920-pm-Su4-I-07-Credo p4〕。

#### xAI

- **Colossus 1/2（Memphis 加 Mississippi Southaven）。** 2026 年 1 月宣布扩到约 2 GW、约 55.5 万颗 NVIDIA GPU（约 52 万 GB200、3 万 GB300、3 万 H100/H200），被称为全球最大单站点训练设施〔网，媒体口径〕。LightCounting 在 ECOC 的口径是 Colossus 2 超过 50 万 GPU、超过 500 MW〔0920-pm-Su3-I-02-LightCounting p4〕，两者差异在于统计时点和是否含第三栋楼。
- **选择。** 单站点硬堆，不走多园区路线。Grok 4 训练用了超过 20 万计算节点〔0920-am-Su1-C-03-STMicro p2〕。

#### Oracle

- 是 Stargate 的主要建设和运营方。OCI Zettascale10 宣称跨多个数据中心连接最多 80 万 GPU、峰值 16 ZFLOPS，2026 下半年可用；网络为自研 Acceleron RoCE：多平面隔离，GPU 网卡内建交换，拥塞控制优先、不依赖 PFC〔网〕。
- 在 ECOC 讲了 10 场，集中在可插拔模块的现网统计：约 35 万条 800G 链路 p99 pre-FEC BER 5E-10，超过 90% 的链路故障源于连接器污染〔0920-pm-Su3-A-03-Oracle p7〕〔0923-MF-00-连拍 p38〕。

#### 小结：北美的三种建设范式

| 范式 | 代表 | 特点 | 对光的需求 |
|---|---|---|---|
| 单站点 GW 级硬堆 | xAI Colossus、Meta Hyperion、AWS Rainier | 一个园区多栋楼，楼间距离几百米到几公里 | 楼间海量 800G/1.6T IM-DD，部分 Coherent-Lite |
| 多园区就近组团 | Google Iowa/Nebraska、Meta Ohio | 3–5 个园区相距 10–80 km | ZR/ZR+、Coherent-Lite、多 rail 线路系统 |
| 多园区跨区域弹性组网 | Microsoft Fairwater + AI WAN、Oracle Zettascale10 | 园区相距数百到上千公里，任务可在园区间迁移 | 专用骨干、FST、C+L、空芯光纤 |

### 1.4 中国各家

#### 政策框架

东数西算的八大枢纽和十大集群定下了地理骨架。截至 2026 年 3 月，全国智算规模约 188 万 PFLOPS，建成 70 多条算力走廊，八大枢纽之间实现 20 ms 时延圈〔网〕。这个 20 ms 指标对训练没有意义（同步训练要求的是微秒到毫秒级），但对推理和数据传输足够。由此可以推出中国的基本分工：西部集群做训练和离线批处理，东部枢纽做推理。

#### 阿里巴巴 / 阿里云

- **布局。** 五座超级数据中心：张北、河源、杭州、南通、乌兰察布，另有中卫等〔网〕。
- **规模。** 2025 年 2 月宣布三年 3800 亿元，之后改为每年 1500–2000 亿元；目标是 2032 年全球数据中心能耗为 2022 年的 10 倍、超过 20 GW〔网〕。2026Q2 单季资本开支 676.8 亿元〔网〕。
- **建设。** CUBE 5.0 模块化，风冷 PUE ≤1.15、液冷 ≤1.10，交付周期压到 100 天。2026 年 8 月灵骏真武 M890 超节点实例首发乌兰察布〔网〕。
- **网络。** ECOC 上阿里给出的是 LPO 的大规模现网数据：13,234 只 400G DR4 LPO，与全重定时模块相比功耗 4.2 W 对 8.1 W，模块时延 <5 ns 对 >100 ns，日链路抖动率 0.017% 对 0.040%〔0921-Mo3-A5-阿里云 p43–p46〕。这说明阿里在楼内网络上走的是"受控环境下极致降功耗"的路线。

#### 字节跳动 / 火山引擎

- **规模。** 媒体报道 2026 年资本开支 1600–2000 亿元，约一半买芯片、一半建数据中心〔网〕。
- **布局。** 国内有芜湖（长三角算力中心，80 亿元，约 2.2 万机柜）、大同（太行算力中心）、内蒙古和林格尔、乌兰察布；海外以马来西亚柔佛为主（Bridge Data Centres MY06 锚定租户，110 MW），另有新加坡等〔网〕。海外园区的作用之一是使用国内拿不到的芯片。
- **用量。** 火山引擎称 2026 年 6 月豆包日均 token 调用量超过 180 万亿，在中国公有云 MaaS 市场份额 49.5%（自报）〔网〕。这是一个以推理为主、量极大的负载。

#### 腾讯

- 2026Q2 资本开支 527.8 亿元，同比 +176%〔网〕。
- 芯片采购转向国产，媒体称后续国产比例可能超过 65%：训练卡来自燧原，推理卡来自寒武纪，也采购百度昆仑芯〔网，媒体口径〕。
- 网络是自研的星脉网络（RoCE），面向十万卡规模。ECOC 上只被提及 2 次，没有主讲。

#### 百度

- 昆仑芯 P800 已交付多个万卡集群，并在全国产集群上完成文心 5.1 训练（自报）；昆仑芯计划在香港上市〔网〕。
- 在 OFC 2026 上，百度用生产数据验证了百万级光模块的故障预测和根因定位（F1 0.894）〔OFC26 Th3B.2〕。

#### 华为（作为算力底座供应商）

- **CloudMatrix384。** 384 颗昇腾 910C 全光互连超节点，已用于 DeepSeek 等模型的推理服务（论文 arXiv 2506.12708）。
- **Atlas 950 SuperPoD。** 2026 Q4 上市，8192 颗昇腾 950DT，128 个计算柜加 32 个互联柜，约 1000 平方米，全光互连；灵衢 2.0 单跳时延从 2 µs 降到 200 ns（自报）〔网〕。Atlas 950/960 SuperCluster 分别为 50 万卡和 100 万卡级〔网〕。
- **ECOC 讲稿。**
  - 华为光产品线讲的算网一体设计〔0920-pm-Su4-C-03-华为 p4–p7〕：用 OCS 加电交换做稀疏超节点，规模扩到 16K，网络时延降 30%，推理性能升 10%；
  - 推理采用 AF 分离（Attention 与 FFN 分离），SU 平面跑 EP/FSDP 的大流量，SO 平面跑跨超节点的多副本 DP 小流量；
  - OTN-Proxy 在 OTN 转发器上做 RDMA 代理和集合通信引擎，宣称吞吐与 0–500 km 距离基本无关；
  - 传统 DCI 与 Scale-across 的对比：流量约 200 Tb/s → 10 Pb/s 以上，扩容粒度从波长变成光纤，rail 数从约 10 到 100 以上。

#### 运营商

- **中国移动。**
  - 哈尔滨智算中心单集群 1.8 万张卡，6.9 EFLOPS，100% 国产；呼和浩特约 2 万张卡，6.7 EFLOPS；截至 2025 年底智算规模 92.5 EFLOPS〔网〕。
  - MWC 2026 发布 GSE-DCI Scale-across 方案，宣称 100 km 以上分布式训练效率达单集群的 98% 以上〔网，自报〕。
- **中国电信。**
  - 智算总规模 91 EFLOPS（截至 2025 年底）〔网〕。
  - 与广东电信、华为完成基于多芯光纤的分布式训练现网验证：广州南、广州沙溪、深圳沙河三个中心，互联距离 409.61 km，性能达集中训练的 97% 以上〔网，自报〕。
  - ECOC 上给出的 Scale-across 路线：400G 已部署 → 800G 试验 → 1.6T 实验；频谱从 C+L 约 12 THz 走向全频段 37 THz 以上；用 OCS 做城域重构〔B54 本批小结〕。
- **中兴加长飞。** 在杭州滨江和吉山的 AIDC 之间做了 600 km 现场训练试验，详见第二部分〔OFC26 W4H.5〕。

#### 美团

美团在 ECOC 讲的"Agent 时代的光互连"是目前看到的最完整的国内用户侧论述〔0923-MF-美团 p7–p17〕：

- DCN 从 3.0 演进到 7.0（25G NRZ 到 224G PAM4，1.6T OSFP），400G 已规模部署，800G 部署中；
- 判断 NPO 已从过渡方案变成长期路径，224G 是务实窗口；
- 用 OCS 加 OTN 在 100 km 跨可用区上验证了训练和推理（详见第二部分）。

### 1.5 中美对比：五个结构性差异

| 维度 | 北美 | 中国 | 对光互连的含义 |
|---|---|---|---|
| 主要约束 | 电力和建设速度 | 芯片供给，其次是电力 | 中国用更多卡、更大超节点补单卡性能，超节点内光化更早 |
| 超节点规模 | 72 GPU（NVL72），Rubin 进入 144 口径；TPU pod 9216 | 384（CloudMatrix）→ 8192（Atlas 950） | 中国超节点必须全光互连，需求量大、时间早 |
| 单园区规模 | 1–5 GW | 0.1–0.3 GW 为主，向 GW 走 | 中国更依赖园区间组网 |
| 跨域训练 | 有选择地使用（Google、Microsoft），也有单站点硬堆路线（xAI） | 政策和资源分布推动，运营商已做 100–600 km 试验 | 中国在 Scale-across 和 OTN 化跨域训练上动作更快 |
| 网络技术 | NVLink 加 InfiniBand/以太网（Spectrum-X、Acceleron、Fairwater 两级以太） | 灵衢、自研 RoCE（星脉、HPN）、OTN/OCS 跨域 | 中国厂商在 OTN 承载 RDMA、OCS 跨 AZ 上有本地方案 |

### 1.6 这些数据中心怎么用

**训练和推理的配比在变。** 2024 年以前，新建 AI 集群大部分用于预训练。2026 年，推理成为最大的增量负载，几个数字可以说明：

- Google 2026 年 5 月每月处理 3.2 千万亿（quadrillion）token，一年增长约 7 倍〔网〕；
- 豆包日均 180 万亿 token（自报）〔网〕；
- NVIDIA 给出的 1 GW AI 工厂：Hopper 时代 60 万 GPU 产出 200 万 tokens/s，Vera Rubin 30 万 GPU 产出 7 亿 tokens/s〔0921-MF-pm-1340-NVIDIA p5〕，单位功率的 token 产出提高约 350 倍（自报）。

**同一园区在不同时间做不同的事。** Microsoft 官方把 Fairwater 的负载列为预训练、微调、强化学习、合成数据生成，并用 AI WAN 在园区间弹性分配。这和早期"训练集群专用"的做法不同。强化学习后训练本身就是"推理（rollout）加训练（梯度更新）"的混合负载，它把训练园区和推理园区的边界变得模糊。

**一般规律：**

- 大规模预训练放在最大、电力最便宜的园区（或多园区组团），远离用户；
- 后训练和强化学习可以在训练园区，也可以借用推理集群的空闲时段；
- 在线推理按用户地理分布部署在多个区域，以时延和可用性为准；
- 批量推理、合成数据、评测这类离线任务，哪里有空闲就放哪里，是调度器填谷的主要手段。

### 1.7 按训练与推理拆开看：各家怎么部署，为什么这样部署

前面按厂商讲了"建了什么"，这一节换个切法：同一家公司，训练算力和推理算力分别放在哪里、用什么芯片、怎么组网，以及背后的原因。

#### 1.7.1 先看两类负载对数据中心的要求有什么不同

| 维度 | 训练（尤其是预训练） | 推理（在线服务） |
|---|---|---|
| 选址第一条件 | 电力规模和电价，能否一次拿到数百 MW 到 GW | 离用户近、离互联网交换点近，满足数据驻留要求 |
| 规模单位 | 一个作业占满一个园区或园区组团（GW 级、10 万卡以上） | 很多个模型副本，每个副本数卡到数百卡（MW 级），按区域复制 |
| 芯片 | 前沿 GPU/TPU、大 scale-up 域、高 HBM 带宽 | 开始多样化：GPU、TPU 推理型号、自研 ASIC、晶圆级芯片、低时延 LPU |
| 网络重点 | 后端 scale-out + 园区间 Scale-across（DP 流量，Tb/s 到 Pb/s） | 超节点内低时延 all-to-all、楼内 KV cache 与存储、前端南北向和东西向；园区间约"一个波长"级 |
| 可靠性 | 一个故障可能拖停整个作业，需大连续故障域和容错训练 | 副本之间互为备份，单点故障影响有限，但 SLA 时延要求严格 |
| 利用率与弹性 | 作业周期数周到数月，集群需长期独占 | 随用户潮汐波动，峰谷差大，需要能被其他负载填谷 |
| 收入属性 | 一次性投入，换取模型能力 | 持续收入，直接决定毛利，单位 token 成本最敏感 |

这张表决定了后面所有差异：训练追求"一处集中的大电力"，推理追求"多处分散的低时延和低单位成本"。2026 年的变化是推理已经成为最大的增量（Google 每月 3.2 千万亿 token，一年约 7 倍；国内有研究机构估计 2026 年推理芯片市场首次超过训练，属媒体口径），于是各家开始为推理单独选芯片、单独规划站点。

#### 1.7.2 北美各家

| 厂商 | 训练部署 | 推理部署 | 背后原因 |
|---|---|---|---|
| Microsoft | Fairwater Wisconsin（规划超 2 GW）+ Atlanta，专用 AI WAN；单个训练作业最多可跨两个区域做模型并行和数据并行（Nadella 访谈口径） | 全球 Azure 区域（含 33 个国家的主权云区域），同一批硬件承担推理、Copilot、OpenAI API | Nadella 的"可互换算力池"（fungible fleet）：不为单一模型的单次训练过度建设，所有区域都能跑预训练、后训练、合成数据和推理，以"每美元每瓦 token 数"为目标 |
| OpenAI | Stargate Abilene（Oracle/Crusoe）和 Microsoft Fairwater 承担前沿训练；其余 Stargate 站点 2026–2028 年陆续投产 | 多云：Azure、Oracle、CoreWeave、Google Cloud、AWS；低时延推理专门签了 Cerebras 750 MW（2026–2028 分批）；自研 Jalapeño 是 LLM 推理加速器，与 Broadcom 合作 10 GW，2026 年底首批部署；另有 AMD MI450 | 推理成本决定毛利，OpenAI 按负载组合硬件：GPU 做训练和通用推理，晶圆级芯片做超低时延（GPT-5.6 Sol Ultrafast 约 750 tokens/s），自研芯片压单位 token 成本。ECOC 上 OpenAI 也明确以"请求时延和单请求能耗"评价互连〔0920-pm-Su3-A-02-OpenAI p3, p8〕 |
| Google | Iowa/Nebraska 4 园区约 1 GW、Ohio 等园区组团；TPU 超节点加 OCS；Decoupled DiLoCo 做跨区域异步训练 | 全球区域就近服务 Gemini、搜索 AI Overviews、YouTube、Workspace；Ironwood（2026-04 GA）被定位为"第一颗面向推理时代的 TPU" | 自有全栈，推理量全球最大；训练和推理的负载特征已经分化到需要两颗芯片：TPU 8 拆成训练用 8t（Broadcom 设计）和推理用 8i（MediaTek 设计），2027 年底、TSMC 2 nm |
| Meta | Prometheus（Ohio，1 GW，5 栋以上楼）、Hyperion（Louisiana，最终 5 GW）用 NVIDIA GPU 训练前沿模型 | 分布在 30 多个既有园区，就近服务 30 多亿用户；广告和推荐推理大量跑在自研 MTIA 上（MTIA 300 已上线），MTIA 450 面向 GenAI 推理，2027 年初量产 | Meta 的推理主体是广告和推荐，量极大、模型相对固定，最适合 ASIC 降本；前沿训练需要最大的连续 GPU 集群，所以集中到少数 GW 园区 |
| AWS / Anthropic | Rainier（Indiana，近 50 万 Trainium2，约 2.25 GW）主要给 Anthropic 训练；Anthropic 同时用 Google TPU（最多 100 万颗）和 NVIDIA GPU | Bedrock 上多数 token 已跑在 Trainium 上（AWS 口径）；Trainium3 每兆瓦输出 token 比 Trn2 高 5 倍以上；Bedrock 也引入 Cerebras 做高速推理；2026 年 5 月 Anthropic 租下 xAI Colossus 1 几乎全部算力（媒体报道） | Anthropic 把训练和推理分散在三种芯片平台上，首先是为了保证供给；AWS 用自研芯片同时承接训练和推理，靠单位 token 成本吸引客户 |
| xAI | Colossus 2（Memphis + Southaven）单站点硬堆，2026 年 9 月约 44 万 GB300 在用 | 与沙特 Humain 合建 500 MW 数据中心，在全国范围部署 Grok；Colossus 1 整体出租给 Anthropic | 训练追求单站点最大规模和最快建设；推理借主权基金的电力和资金放到海外，同时满足当地数据和服务要求；旧集群直接变现 |
| Oracle | 为 OpenAI 等建设训练集群（Abilene、Zettascale10 最多 80 万 GPU、跨多 DC） | OCI 区域承接客户推理 | Oracle 主要卖算力容量，训练和推理的边界由客户决定；公开资料对其推理部署的细节披露有限 |
| NVIDIA（平台侧） | Vera Rubin NVL72 + Spectrum-X 多平面，面向 GW 级训练 | 同一平台里加入 Groq 3 LPX（低时延推理机架）和 BlueField-4 STX（上下文存储），网络分层多了"上下文存储"一层〔0920-pm-Su3-A-05-NVIDIA p3, p4〕 | 连 NVIDIA 自己也在为推理单独设计机架类型：decode 的时延和 KV cache 容量需求已经和训练不同 |

北美的共同点：

1. **训练集中、推理分散。** 训练集中到少数 GW 园区或园区组团；推理沿用已有的几十个全球区域，并在主权云、海外合作园区（xAI 沙特）继续铺开。
2. **推理硬件走向多样化。** 2024 年训练和推理基本都用同一种 GPU；到 2026 年，每家都给推理安排了专门的硬件路线：Google TPU 8i、Meta MTIA、AWS Trainium、OpenAI Jalapeño 加 Cerebras、NVIDIA Groq 3 LPX。原因是 decode 阶段受 HBM 带宽和时延约束，和训练的算力约束不同（见 2.5 节），专用芯片能把单位 token 成本降下来。
3. **"可互换"与"专用化"两条路并存。** Microsoft 强调同一批硬件跑所有负载，用利用率换灵活性；Google、Meta、OpenAI 走专用化，用芯片差异换单位成本。前者对网络的要求是"每个区域都能接入训练级 Scale-across"，后者要求推理集群内部有极低时延的 scale-up。

#### 1.7.3 中国各家

| 厂商 | 训练部署 | 推理部署 | 背后原因 |
|---|---|---|---|
| 阿里云 | 乌兰察布、张北等北方园区的灵骏集群；2026-08 真武 M890 超节点首发乌兰察布 | 杭州、上海、北京、深圳等东部区域和海外区域就近服务；PAI 在乌兰察布、张家口也提供模型部署资源，承接对时延不敏感的推理和批量任务 | 东数西算加电价（乌兰察布约 0.3 元/kWh）：训练和离线推理往北走，交互推理留在东部；MaaS 份额最高（研究机构口径约 35.8%），推理需求是资本开支上调的直接原因 |
| 字节跳动 | 前沿训练有相当部分放在海外：马来西亚（经 Aolani 使用约 500 台 Blackwell 服务器、约 3.6 万颗 B200，媒体报道）、东南亚 5 国均有数据中心 | 国内芜湖、大同、和林格尔、乌兰察布承担豆包推理（日均 token 超 180 万亿，自报），并逐步引入国产芯片和自研芯片 | 出口管制：最先进 GPU 只能在境外用，于是"境外训练、境内推理"；推理量全国最大，国内园区首先要满足推理 |
| 腾讯 | 自用为主，训练卡转向国产（燧原，媒体口径），与 NVIDIA 存量混用 | 推理服务元宝、微信 AI、CodeBuddy、WorkBuddy 等；推理卡采购寒武纪、昆仑芯（媒体口径）；Q2 业绩会表示不准备出租算力 | 产品驱动：资本开支拆成"现有业务"和"AI 原生业务（训练、推理、云）"两块，推理随产品上线而来；不出租算力意味着推理利用率优先保障自家产品 |
| 百度 | 昆仑芯 P800 万卡集群，在全国产集群上完成文心 5.1 训练（自报） | 百度智能云推理，昆仑芯同时对外销售（腾讯为客户） | 自研芯片既解决训练供给，也做推理降本；对外销售分摊研发成本 |
| 华为云 | Atlas 950 SuperPoD（8192 卡，2026Q4）、SuperCluster（50 万到 100 万卡）面向训练 | CloudMatrix384 已在乌兰察布、和林格尔、贵安、芜湖上线，主打推理（DeepSeek-R1 单卡 decode 约 1920 tokens/s，自报）；宣称 10 ms 时延圈覆盖 19 个城市群 | 用大超节点弥补单卡性能，正好适配 MoE 推理的大 EP；10 ms 时延圈说明西部和中部枢纽也能服务大部分交互推理，这与北美"推理贴近用户"的做法不同 |
| 运营商 | 哈尔滨、呼和浩特等万卡国产集群，服务大模型客户训练；跨域训练把分散资源拼起来（中国移动 GSE-DCI、中国电信多芯光纤 409.61 km） | 省级和边缘智算节点承接政企推理 | 运营商的资源天然分散在各省，跨域训练是盘活资源的手段；推理则依托现有骨干和城域网络下沉 |
| 美团 | 自建训练集群 | 在 100 km 跨可用区用 OCS + OTN 验证了推理（TTFT +7.21%、TPOT 约 +1%）〔0923-MF-美团 p17〕 | 面向 Agent 业务，推理流量动态、需要感知负载的网络 |

中国的共同点：

1. **出口管制改写了训练的地理。** 最先进 GPU 只能在境外使用，于是出现"境外训练、境内推理"（字节）和"国产集群训练"（百度、运营商、华为）两条路线。
2. **时延圈让推理可以放在西部。** 北美推理贴近用户，是因为园区和用户之间的距离可能上千公里；中国八大枢纽 20 ms、华为云 10 ms 时延圈，让西部和中部园区也能服务大部分交互推理。因此"西训东推"更准确的说法是：交互要求最高的推理留在东部，其余推理和训练都可以往电便宜的地方走。
3. **推理芯片国产化先行。** 推理对生态和规模的要求低于训练，国产芯片更容易先在推理上替代（腾讯推理卡寒武纪、华为 CloudMatrix 主打推理）。

#### 1.7.4 背后的六个原因

1. **经济属性不同。** 训练是一次性的大额资本投入，追求最快拿到模型；推理是持续的收入来源，决定毛利。所以训练选"电最多、建得最快"的地方，推理选"单位 token 成本最低、离用户够近"的地方。
2. **时延约束落在不同层面。** 训练在集群内部要求微秒级，但整个集群放在哪里与用户无关；推理对集群内部（decode all-to-all）和对用户（RTT 数十毫秒）两层都敏感。
3. **芯片分化。** 推理 decode 受 HBM 带宽和时延约束，于是出现推理专用芯片和机架（TPU 8i、MTIA、Trainium、Jalapeño、Cerebras、Groq 3 LPX、昇腾超节点），训练仍集中在前沿 GPU/TPU。
4. **利用率和弹性。** 推理有潮汐，训练长期独占。Microsoft 用可互换算力池解决，强化学习后训练（rollout 本身就是推理）也让两类负载在同一园区里交替。
5. **监管。** 出口管制决定中国厂商训练放在哪里；数据驻留和主权云要求推理留在本国（Microsoft 33 国主权区域、xAI 沙特）。
6. **可靠性。** 训练需要大的连续故障域和容错机制（FT-HSDP、DiLoCo）；推理副本互为备份，单点故障影响小，但 SLA 更严。

#### 1.7.5 对光互连的含义

| | 训练园区 | 推理园区 |
|---|---|---|
| 园区间 | 每对园区数十到上百个光纤对，ZR/ZR+、FST、多 rail，HCF 压时延 | 数量更多的城域连接，单链路约一个波长级；模型权重分发是批量流量 |
| 楼内 | 后端 scale-out 1.6T/3.2T、多平面多 rail、OCS 替代 super-spine | KV cache 和上下文存储网络、前端东西向（Agent）、CPU 侧网络加大 |
| 超节点内 | TP/EP 带宽优先，NPO/CPO 光化 | decode all-to-all 时延优先，单跳时延和扇出决定 OCS 能否进入（<700 ns 门槛） |
| 可靠性指标 | 链路抖动间隔、作业有效训练时间 | 尾时延、SLA 达标率 |

总的来看，训练拉动的是园区间的"粗管道"和楼内后端网络，推理拉动的是超节点内的低时延互连、楼内存储与前端网络，以及更多的城域连接。

---

## 第二部分：大模型训练与推理的流量模型和调度

### 2.1 并行维度与流量特征

先把训练中的各种并行方式放在一张表里。表中的"物理位置"是 2026 年业界的主流做法。

| 并行方式 | 切什么 | 集合通信原语 | 每步通信频度 | 时延敏感性 | 能否与计算重叠 | 主流物理位置 |
|---|---|---|---|---|---|---|
| 张量并行 TP（含序列并行 SP） | 每层的权重矩阵 | AllReduce，或 ReduceScatter + AllGather | 每层前向 2 次、反向 2 次 | 极高（在关键路径上） | 很难 | 超节点内（NVLink / 灵衢） |
| 上下文并行 CP | 长序列的 token 维度 | Ring Attention 的 P2P 或 AllGather（KV） | 每层 | 高 | 部分可以 | 超节点内或相邻超节点 |
| 专家并行 EP | MoE 层的专家 | All-to-All（dispatch + combine） | 每个 MoE 层前向 2 次、反向 2 次 | 高，且流量突发、不均衡 | 部分可以（DualPipe 等） | 超节点内为主，大 EP 跨节点走 scale-out |
| 流水线并行 PP | 层的切分（stage） | P2P Send/Recv（激活和激活梯度） | 每个 micro-batch 每个 stage 边界 | 中（气泡对时延敏感） | 可以 | 跨机架、跨楼都可以 |
| 数据并行 DP / FSDP / HSDP | 数据（模型副本） | AllReduce，或 ReduceScatter + AllGather（梯度、参数） | 每步 1 次（FSDP 每层 AllGather 参数） | 低 | 可以（与反向传播重叠） | 跨楼、跨园区 |
| 外层同步（DiLoCo 一类） | 多个独立训练"岛" | 每 H 步一次的参数平均（可异步） | 数百步 1 次 | 很低 | 完全可以 | 跨园区、跨区域 |

Ciena 在 ECOC 上给了一个经验比例：die-to-die 带宽按 100% 算，内存带宽 10%，scale-up 1%，scale-out / scale-across 0.1%〔0921-Mo12-A3-Ciena p33〕。这个比例和下面的定量估算一致。

### 2.2 流量量级：同一尺度下的比较

用 Llama 3 405B 公开的训练配置做一次估算（本文估算，只看量级）。

配置：16,384 张 H100，TP 8、PP 16、DP 128；序列长度 8K，全局批约 1600 万 token；BF16；模型维度 h = 16,384，126 层。按约 400 TFLOPS/GPU 算，每步约 6 秒（Llama 3 论文给出的 MFU 为 38%–43%）。

| 流量类型 | 每 GPU 每步的发送量 | 换算为每 GPU 平均速率 | 估算方法 |
|---|---|---|---|
| TP | 约 235 GB | 约 39 GB/s（约 310 Gb/s），且大部分在关键路径上 | 每 replica 每步 12.8 万 token；每层每 token 激活 32 KB；每层 4 次集合通信，每次 ring 系数约 1.75；每个 stage 8 层 |
| DP | 约 13 GB | 约 2.2 GB/s（约 17 Gb/s），可重叠 | 每 GPU 持有 405B/(8×16) ≈ 31.6 亿参数，BF16 梯度 6.3 GB，ReduceScatter + AllGather 约 2 倍 |
| PP | 约 1 GB | 约 0.17 GB/s | 每个 stage 边界前向激活约 4.2 GB、反向同量，分摊到 TP 组 8 卡 |

再看 MoE 的专家并行。以 DeepSeek-V3 为例（本文估算）：

- 模型维度 7168，每 token 选 8 个专家，58 个 MoE 层，dispatch 用 FP8、combine 用 BF16；
- 每 token 每层 all-to-all 约 57 KB + 115 KB，前向加反向约 20 MB/token；
- DeepSeek 公布的训练量是 14.8T token、278.8 万 H800 GPU 小时，即每 GPU 约 1474 token/s；
- 由此每 GPU 的 EP 流量约 30 GB/s，即约 240 Gb/s。

这正好和 DeepSeek 集群每 GPU 一张 400G InfiniBand（50 GB/s）的配置对得上。DeepSeek 用"每个 token 最多路由到 4 个节点"的限制和 DualPipe 重叠来压这部分流量。

这几组数字给出的结论很清楚：

1. **TP 和 EP 是同一个量级（每 GPU 数百 Gb/s，持续），而且 TP 不能重叠。** 它们只能放在每 GPU 有 TB/s 级带宽的超节点里（NVLink 5 每 GPU 1.8 TB/s，NVLink 6 每 GPU 3.6 TB/s〔0921-MF-pm-1340-NVIDIA p4〕）。MoE 模型越来越大（华为讲稿给出专家数 384 → 896 → 1024 的趋势〔0920-pm-Su4-C-03-华为 p4〕），EP 组的规模是推动超节点从 72 卡扩到数百、数千卡的直接原因。
2. **DP 比 TP 低一个多数量级，且可以重叠，是唯一适合跨楼、跨园区的流量。** 跨园区的总带宽 = 一侧园区的 GPU 数 × 每 GPU 梯度量 ÷ 允许的通信时间。假设 Llama 3 405B 这样的任务一半放在 A 园区、一半放在 B 园区，完全重叠时园区间约需 70 Tb/s；如果只允许通信暴露 5% 的步时间，需要的带宽还要高一个数量级。
3. **PP 很便宜，是跨楼切分的理想维度。** 美团在 8:1 收敛、100 km 跨 AZ 上，PP 流量走 OCS 时训练时间只增加 0.01%（LLaMA2-70B）和 0.75%（GPT-MoE）；DP 走 OCS 时增加 6.78%；EP 走 OCS 时最坏增加 21.22%〔0923-MF-美团 p17〕。这组现网数字和上表的估算完全一致：PP < DP << EP。

### 2.3 跨园区训练：带宽、距离和效率的实测与仿真

把本地索引中跨 DC 训练的数据放在一起：

| 来源 | 场景 | 规模 / 模型 | 距离 | 结果 | 口径 |
|---|---|---|---|---|---|
| 中兴、长飞〔OFC26 W4H.5〕 | 杭州滨江与吉山之间 2 个或 3 个 AIDC | 1024 GPU，LLaMA2-70B，TP8 PP8 DP16 | 100–600 km | DP 效率损失 <5%，PP <1%；线路 16λ×800G = 12.8 Tb/s，1:8 收敛 | 现网 |
| 美团〔0923-MF-美团 p16, p17〕 | OCS + OTN 跨 AZ，出口 8:1 收敛 | LLaMA2-70B、GPT-MoE、DeepSeek-R1 推理 | 100 km | PP 100.01%，DP 106.78%，EP 121.22%；推理 TTFT 107.21%，TPOT 约 101% | 现网 |
| 中国电信、华为〔网〕 | 多芯光纤，广州—深圳三中心 | 未公开 | 409.61 km | 达集中训练的 97% 以上 | 自报 |
| 中国移动 GSE-DCI〔网〕 | 智算互联路由器 | 未公开 | 100 km 以上 | 达单集群的 98% 以上 | 自报 |
| 华为法研所〔ECOC25 Tu.04.06.2〕 | 训练时间、成本、能耗框架 | — | 城域 / 长途 | 同成本下城域慢 7%，长途慢 37%；Bifrost 协议再减 26% | 仿真 |
| Corning〔0924-Th1-G1-Corning p8–p10〕 | ASTRA-sim，数据并行 GPT-3 | 13B/175B，256–8192 GPU | 0.3–1000 km | 10 km 内重叠效率约 1；H100 在 10–30 km 后下降；1000 km 训练时间约 26 倍（HCF 降到约 17 倍） | 仿真 |
| KDDI〔OFC26 W4H.3〕〔0922-Tu1-G1-KDDI〕 | OCS 网关 + 400ZR + H100 | — | 20–40 km | RDMA 时延只按光纤传播增加（9.836 µs/km），集合通信完成时间几乎不变 | 实验 |
| Google DeepMind〔网〕 | Decoupled DiLoCo | 12B Gemma，混合 TPU | 美国 4 个区域 | 带宽为同步训练的 1/236，质量与单 DC 相当 | 实验 |

**带宽估算公式。** 中兴给出的推导值得照搬，因为它把模型参数直接换算成线路侧容量〔OFC26 W4H.5〕：

- 每次迭代计算时间 T_batch = 6ψbs/(p·t·P)。其中 ψ = 70B，b = 32，s = 4096，p = 8，t = 8，单卡实测算力 P = 122.96 TFLOPS，得 6.99 s；每个 DP 周期 27.98 s。
- 每 GPU 每次 DP 通信量 D_DP ≈ 2ψ/(p·t) × 2 Byte ≈ 4.37 GB。
- 要求 DP 通信时间只占计算时间的 1%–5%，则每 GPU 需 3.12–15.64 GB/s。
- 线路侧总带宽 BW_DP = (GBS/d) × 每 GPU 带宽 × 8 = 3.2–16 Tb/s。
- 实际按 1:8 收敛配置 12.8 Tb/s，用 16 个 800G 相干模块（单载波 135 GBd PCS-16QAM，OTN 承载）。

按同样方法外推：GPT-4 级 1.8T 模型在完全重叠时需 3.1 Tb/s 以上，不重叠时 62–309 Tb/s；10T 的 MoE 模型对应 17 Tb/s 以上和 343 Tb/s–1.7 Pb/s〔0923-We5-B-中兴 p5〕。有没有计算-通信重叠，带宽需求相差两个数量级。这是 Scale-across 光网络容量规划最大的不确定项。

**距离为什么在 10–30 km 后开始出问题。** 光纤时延约 5 µs/km，与带宽无关。网卡升到 400G–1.6T 以后，串行化时间变小，传播时延就成了数据并行能否被反向传播掩盖的主导因素〔0924-Th1-G1-Corning p5〕。GPU 越快，可用来掩盖通信的计算时间越短，越怕距离：H100 比 A100 更早受影响。模型越大，每层计算越多，越耐距离。空芯光纤把传播时延降约 1/3，在"带宽受限转时延受限"的转折距离上收益最大，重叠效率最多提高约 25%，同等时延下可达距离远约 50%〔0924-Th1-G1-Corning p9〕。

**跨 DC 需要专门的集合通信库。** NCCL 一类的库假设数据中心内部带宽均匀。跨 DC 时，CCL 的重配置（慢）和 WAN 的重配置（快）需要联合优化。米兰理工的 Scale-CCL 与 NCCL 相比完成时间低约 50%，调度求解比 TE-CCL 快约 1000 倍〔0923-We2-C3-1409-米兰理工 p10–p16〕。中兴试验中的 DP ring 也是刻意安排的：3 个 AIDC 分别放 8、6、2 个副本，跨 DC 的边只出现在 DP8–DP9、DP14–DP15、DP16–DP1 三处〔OFC26 W4H.5 Fig.2〕。

### 2.4 训练任务如何规划

一个前沿模型从立项到发布，大致经历以下阶段。每个阶段的算力形态和流量特征不同，规划时要分开考虑。

| 阶段 | 典型时长 | 算力形态 | 主要流量 | 调度要点 |
|---|---|---|---|---|
| 小规模实验与 scaling law 拟合 | 数周到数月 | 数百到数千卡，作业数量多 | 楼内 | 碎片化调度，抢占式 |
| 主预训练 | 1–3 个月 | 数万到数十万卡，单作业 | TP/EP 在超节点内，PP 跨机架或跨楼，DP 跨楼或跨园区 | 拓扑感知放置；容错；检查点 |
| 中段训练（长上下文扩展、退火） | 数周 | 同上或略小 | CP 流量增加 | 改变并行配置（Llama 3 在 131K 序列时用 CP16） |
| 后训练（SFT、RL） | 数周到数月，且越来越长 | 训练器 + 大量 rollout 推理工作器 | 权重从训练器广播到推理工作器；rollout 是推理流量 | 训练和推理资源混合调度 |
| 合成数据生成、评测 | 持续 | 推理集群 | 推理流量 | 填谷 |

**放置原则，按约束强度从强到弱：**

1. **TP（和 EP）组不能跨超节点。** NVL72 机架内放 TP8 的 9 组，或放一个 EP 组。DeepSeek-V3 训练不用 TP，EP64 跨 8 个节点，靠限制每 token 最多到 4 个节点来控制 IB 流量（公开论文）。OpenAI 的 Jalapeño 网络则明确是给 TP 和 EP 设计的两级 scale-up 域〔0920-pm-Su3-A-02-OpenAI p7〕。
2. **PP 的 stage 按机架或楼层顺序排列，跨楼只切 PP 或 DP。** Meta 的 Llama 4 集群跨多栋楼，HSDP（分片在楼内、复制跨楼）是自然选择。
3. **DP 副本是容错单元，也是跨楼、跨园区的切分单元。** Meta FT-HSDP 把每个 DP 副本作为独立的故障域，一个副本故障时其他副本继续训练，恢复停顿从 10 分钟降到 3 分钟，有效训练时间从 44% 提高到 80%〔网〕。
4. **按 rail 对齐。** 多平面、多 rail 网络（NVIDIA Spectrum-X 8 平面 4 rail，512K Rubin GPU〔0921-MF-pm-1340-NVIDIA p9〕；Oracle Acceleron 多平面）要求同一 rail 号的 GPU 组成通信组，调度器要知道 GPU 在哪个平面、哪个 rail 上。

**故障率决定规划的上限。**

- Llama 3 405B 预训练 54 天里，GPU 故障 148 次占 30.1%，HBM3 72 次占 17.2%，网络交换机和线缆 35 次占 8.4%〔0923-We2-C3-1409-米兰理工 p17〕。
- Credo 引用的估算：三层 Clos、链路 MTTF 3×10⁵ 小时，2 万卡集群约 3 小时出现一次链路抖动，20 万卡约 12 分钟，300 万卡约 48 秒〔0923-MF-Credo p2〕。
- 在百万卡级别，没有容错机制的同步训练无法进行。这也是异步训练（DiLoCo 一类）和 HSDP 容错被产业快速接受的原因。

对光模块的直接要求是低抖动和可预测的故障。阿里 LPO 的抖动率数据〔0921-Mo3-A5-阿里云 p46〕、Oracle 的连接器污染统计、百度和华为的模块故障预测论文〔OFC26 Th3B.1/Th3B.2/W4H.2〕都在回答这个问题。

**强化学习后训练改变了流量结构。** RL 阶段的主要算力花在 rollout（推理）上，训练器每隔一段时间要把新权重同步给成百上千个推理工作器。对万亿参数模型，一次权重广播就是 TB 级数据，要在秒到十几秒内完成。这是一种新的、周期性的"一对多"大流量，介于训练 DP 流量和推理流量之间。如果训练器和 rollout 工作器分处不同园区，它就会成为跨园区流量的一部分。

### 2.5 推理的流量模型

#### 一个请求的三个阶段

OpenAI 在 ECOC 上把一个推理请求分成三种硬件形态〔0920-pm-Su3-A-02-OpenAI p5〕：

| 阶段 | 计算特征 | 通信特征 | 关键指标 |
|---|---|---|---|
| Prefill（编码上下文） | 注意力计算量大，受算力限制 | 内存带宽需求低，通信平滑 | TTFT（首 token 时延） |
| Draft model（推测解码的小模型） | 小模型，超低批量 | 带宽低，但对网络时延极度敏感 | — |
| Spec-verify / Decode | 注意力受 HBM 带宽限制，MoE 需要 HBM 带宽 | 通信呈突发（MoE all-to-all） | TPOT（每 token 时延） |

OpenAI 提出的系统指标是"满足 SLA 时延下的每秒每瓦请求数"。低时延通常意味着每 token 能耗更高〔同上 p3〕。

#### PD 分离与 KV cache 流量

Prefill 和 Decode 分开部署已是主流（DeepSeek、Kimi Mooncake、NVIDIA Dynamo、华为 CloudMatrix 都是这样）。分离后，Prefill 产生的 KV cache 要传给 Decode 节点，这是推理侧最大的一类机间流量。

KV cache 的大小（本文估算，BF16）：

| 模型 | 每 token KV 大小 | 32K 上下文的 KV | 400 Gb/s 下的传输时间 |
|---|---|---|---|
| Llama 3 70B（GQA，80 层，8 个 KV 头，128 维） | 约 320 KB | 约 10.5 GB | 约 0.21 s |
| DeepSeek-V3（MLA，61 层，每层 576 维） | 约 70 KB | 约 2.3 GB | 约 0.05 s |

米兰理工引用的数字是"30 KB 的 prompt 可以产生 10 GB 的 KV cache"〔0923-We2-C3-1409-米兰理工 p21〕，和上表一致。传输时间要计入 TTFT。所以 Prefill 和 Decode 必须在同一栋楼、同一个 scale-out 网络里，传输带宽至少要 200–400 Gb/s〔网〕。美团把 KV cache 流量放到 8:1 收敛的 OCS 跨 AZ 链路上，TTFT 增加 7.21%，TPOT 只增加约 1%〔0923-MF-美团 p17〕：首 token 对 KV 传输敏感，后续 token 不敏感。

#### Decode 阶段的大 EP

DeepSeek 公开的推理部署：Prefill 以 4 节点 32 卡为单元（attention TP4+SP、DP8，MoE EP32）；Decode 以 40 节点 320 卡为单元（EP320），后来的生产配置为 EP144。也就是说，一个 decode 实例跨十几到几十台服务器，每生成一个 token 都要在这些服务器间做两次 all-to-all（公开资料）。

这类流量的特点是小包和高频，时延比带宽重要得多。Salience Labs 的测算：400G 链路、10 KB 载荷时，单级电交换的事务时间约 1000 ns，两级约 1600 ns，带宽本身只占约 25 ns〔0922-PF-1155-SalienceLabs p5, p6〕。高交互推理的 decode 中，通信在关键路径上，交换跳数和交换时延直接决定 \$/token〔同上 p16〕。

所以超节点要尽量大，单跳要尽量短（灵衢 2.0 宣称单跳 200 ns；NVLink 6 宣称时延降 3 倍〔0921-MF-pm-1340-NVIDIA p4〕）。Lightmatter 仿真 10T MoE（340B 激活、1024 专家）解码，光互连比铜快约 2 倍〔0924-推定F2-Lightmatter p4〕；伯克利和 Ayar Labs 的结论是，没有高扇出时，OCS 的重构时间必须低于 700 ns 才能在推理上胜过电交换〔OFC26 W2A.28〕。

#### 华为的 AF 分离

华为把推理进一步拆成 Attention 和 FFN（专家）两个池。AF 算力池的配比按小时或按天根据平均序列长度调整，OCS 动态调整两池间的带宽；超节点平面跑 EP 大流量，跨超节点平面跑多副本 DP 小流量〔0920-pm-Su4-C-03-华为 p4〕。这是"推理流量随负载变化 → 用光交换跟随"的一个具体实现。

#### 推理的地理分布

推理的跨园区流量很小。BT 的说法是推理约"一个波长"级，用现有 ROADM 网络即可，训练才需要 Scale-across〔0920-am-Su1-C-00-上半场速记 p18–26〕。Adtran 的口径：训练是每次运行 PB 级的 DC 间数据，推理是持续的、时延敏感的流量〔0920-pm-Su3-H-05-Adtran p5〕。

推理的跨区域调度主要是请求路由：用户请求按地理和负载分到各区域的推理集群，每个区域保存完整的模型副本。模型发布时要把权重分发到所有区域，这是一次性的批量流量。

### 2.6 多 Agent、多推理场景的流量模型

Agent 和普通聊天的区别，对网络来说有四点：

1. **一个用户请求变成几十到上百次模型调用。** 编排 Agent 拆任务，子 Agent 并行执行，每一步都可能调用工具（检索、代码执行、浏览器、数据库），再把结果拼回上下文。
2. **上下文很长，而且多轮复用。** 多轮、短追加的模式使 KV cache 命中率通常在 95% 以上，瓶颈从算力转向存储 I/O：KV cache 在 HBM、主机内存、SSD 和远端存储池之间反复加载和卸载〔网，DualPath 论文〕。
3. **流量从南北向变成东西向。** Agent 访问数据库、API、其他 Agent，都是数据中心内部的横向流量〔网〕。
4. **CPU 重新回到关键路径。** 工具执行、沙箱、编排逻辑都跑在 CPU 上。业界估计 Agent 部署的 CPU:GPU 比例会从 1:4–1:8 走向接近 1:1；NVIDIA Vera CPU 支持 1.5 TB LPDDR5X，是 Grace 的 3 倍〔网〕。

由此推出 Agent 推理的调度要点：

- **会话亲和性。** 同一个 Agent 会话的后续调用要路由到持有其 KV cache 的节点。这正是 KV 感知路由器（NVIDIA Dynamo、llm-d 等）的作用。一旦路由失败，就要重做 prefill 或跨节点搬 KV。
- **模型路由。** 一个工作流里，规划用大模型，简单子任务用小模型，推测解码用 draft 模型。不同模型分布在不同池里，请求在池间跳转。
- **突发和长尾。** Agent 的并行子任务会同时到达，推理负载的峰均比远高于聊天。
- **时延预算按步累加。** 一个工作流有几十步，每步多 100 ms，整体就多几秒。所以 Agent 场景对单步时延更敏感，跨区域调用要尽量避免。

美团的判断代表了用户侧的共识：Agent 的动态工作流要求网络从尽力而为转向感知负载的协同，NPO 解决带宽密度和功耗，OCS 和电交换互补〔0923-MF-美团 p18〕。

### 2.7 四层调度：区域、园区和楼栋、超节点、GPU

把以上内容落到调度上，可以得到一个四层嵌套的模型：

| 层级 | 决策内容 | 主要依据 | 承载的流量 | 光互连技术 |
|---|---|---|---|---|
| L1 区域 / 园区群 | 训练任务放在哪个园区组团；推理请求路由到哪个区域；离线任务填谷 | 电力和电价、容量、数据主权、用户分布、园区间带宽 | 跨园区 DP 或外层同步；模型权重分发；推理请求 | ZR/ZR+、FST + 多 rail、C+L、空芯光纤、OTN（10–1000+ km） |
| L2 园区内楼栋 | 一个训练任务占几栋楼；推理集群和训练集群如何分区 | 楼栋是供电和故障域；楼间带宽有收敛 | DP / HSDP 副本间、PP 跨楼；KV cache 存储池 | 800G/1.6T DR/FR、Coherent-Lite（500 m–10 km）、OCS |
| L3 超节点 / Pod | TP 组、EP 组、PD 实例放在哪个超节点；如何减少碎片 | 超节点规模、空闲块大小、拓扑对齐 | TP、EP、CP；decode 的 all-to-all | NVLink / 灵衢铜缆 → NPO/CPO/XPO 光化（2–100 m） |
| L4 GPU | rank 到物理 GPU 的映射；rail 对齐；慢节点剔除 | rail、平面、链路健康度 | 集合通信的具体路径 | 模块遥测、预测性维护、链路抖动控制 |

几个跨层的规律：

- **每往上一层，带宽降一个数量级，时延容忍度升一到两个数量级。** 调度器的基本动作，就是把通信最重的并行维度放在最低层。
- **园区是电力单位，楼栋是故障单位，超节点是通信单位。** 这三个边界分别对应三种光互连：Scale-across、Scale-out、Scale-up。
- **调度和网络开始联动。** 训练阶段感知的 OCS 重构（剑桥，通信快 37.5%〔OFC26 M3F.5〕）、EP/TP 与 DP 网络之间 2 µs 内的光切换（AIST〔OFC26 M4F.4〕）、按流粒度自动分配 OCS（AllReduce 时间降 50.3%〔OFC26 W4H.4〕）都在做同一件事：让网络拓扑随作业的通信阶段变化。华为把这叫"算网一体"，米兰理工叫"workload-to-network 闭环"。

---

## 第三部分：对光互连的含义

把流量分层和建设格局对照，可以得到四档需求。每一档的量和时间窗口都可以从上文推出来：

| 档位 | 距离 | 承载的流量 | 需求驱动 | 主流技术（2026–2028） | 规模感 |
|---|---|---|---|---|---|
| 超节点内（Scale-up） | 1–100 m | TP、EP、decode all-to-all | MoE 专家数增加；超节点从 72 卡扩到数百至数千卡 | 铜（≤1–2 m）→ NPO/XPO → CPO；宽而慢的 µLED/VCSEL 在研 | Corning：每机架光纤数从约 1k（NVL72，2026）到约 45k（2029 年以后）〔B54 本批小结〕 |
| 楼内与楼间（Scale-out） | 100 m–2 km | DP/HSDP、PP、KV cache、存储 | GPU 数量；每 GPU 800G→1.6T | 800G/1.6T DR/FR 可插拔（FRO/LRO/LPO）、多平面多 rail、OCS 替代 super-spine | NVIDIA：1 GW 约 30 万 Rubin GPU，每 GPU 1.6T scale-out |
| 园区内楼栋群（Scale-across 园区） | 2–20 km | 跨楼 DP、PP | 单园区 4–12 栋楼〔0920-pm-Su3+Su4-A-00-全场 p111〕 | O 波段 Coherent-Lite 1.6T/3.2T（FEC 时延要求 50–75 ns） | Marvell：Scale-across 后端网络约 1–2 万端口，是传统 DCI 的 10 倍〔0920-pm-Su3-I-07-Marvell p12〕 |
| 园区之间（Scale-across 城域/区域） | 20–1000+ km | 跨园区 DP、外层同步、权重分发 | 多园区训练；推理区域间复制 | 800ZR+/1.6T ZR/ZR+、FST、多 rail 线路系统、C+L、空芯光纤 | Cignal：2030 年 Scale-across 占云可插拔带宽 72%、支出 87 亿美元，其中线路系统占 55%〔0922-MF-am-1140-CignalAI p7, p9〕 |

几点判断：

1. **Scale-across 的带宽需求取决于算法。** 同步数据并行加不重叠，需要 Pb/s 级；完全重叠，需要数十 Tb/s；DiLoCo 一类的异步外层同步，再降两个数量级。今天产业的规划基础是"同步 DP + 部分重叠"，这对应每对园区数十到数百 Tb/s，也就是数十到上百个光纤对。如果异步训练在前沿模型上被证明可行，园区间带宽的增长会比预期慢，但园区间的"连接数"（更多园区参与）会增加。

2. **对时延的要求在园区间比带宽更难满足。** 带宽可以靠堆光纤对，传播时延只能靠缩短距离或换空芯光纤。空芯光纤的价值在 10–200 km 这一段最大（Corning 的转折距离），这正好是园区组团的典型距离。

3. **推理的增长主要落在楼内，而不是园区间。** PD 分离的 KV cache 流量、decode 大 EP、Agent 的东西向流量和存储 I/O，都在 Scale-up 和 Scale-out 里。推理带来的园区间需求主要是数量更多的城域连接，而不是更大的单链路容量。

4. **中国市场的需求结构更偏两端。** 超大超节点（384 → 8192 卡全光互连）意味着超节点内光模块的需求比北美早一代、量大一个数量级；单园区规模较小、政策推动跨域协同，意味着 OTN 化 Scale-across、OCS 跨 AZ 的需求更早。中间档（楼内 scale-out）与北美相近。

5. **可靠性指标正在变成第一指标。** 在 10 万卡以上规模，链路抖动的间隔是分钟级。模块厂商的交付物要从"单只模块"变成"光引擎加连接器加遥测加可预测故障"。NPO/CPO 去掉前面板热插拔后，维修时间从分钟级变成小时到天级〔0923-MF-美团 p14〕，这会反过来影响调度器的容错设计。

---

## 第四部分：不确定性与后续跟踪

**数据可靠性。**

- GPU 数量、投资额、园区容量多来自媒体报道，同一项目在不同报道里可能差 30% 以上（例如 Colossus 2 的 50 万 GPU / 500 MW 与 55.5 万 GPU / 2 GW）。
- 跨域训练的"97%–98% 效率"都是厂商自报，没有披露模型规模和并行配置，不能与中兴公开的推导直接比较。
- 第二部分的流量估算是我按公开配置推出来的，用于量级比较，误差可能到 2 倍。

**值得跟踪的问题。**

1. 前沿实验室是否在主预训练中采用异步多园区训练（DiLoCo 一类）。这一点会改变园区间带宽规划。
2. NVIDIA Rubin NVL144/576 和华为 Atlas 950 的实际部署节奏，以及超节点内 CPO 的现场故障率。
3. Stargate 各站点 2026 Q4 到 2027 年的投产情况，以及园区间是否建专用 AI WAN。
4. 中国运营商跨域训练从试验转到商用的节点，以及 OTN 承载 RDMA 的标准化。
5. Agent 负载占推理的比例，以及它对 CPU、存储和楼内网络的拉动是否像预期那样大。

**可以补充的工作。**

- 把第一部分的园区清单做成可筛选的表（园区、厂商、坐标、GW、芯片、投产时间、与最近园区的距离），用于估算各园区组团的 Scale-across 需求。
- 把第二部分的估算方法做成小工具：输入模型参数和并行配置，输出 TP/EP/PP/DP 各层每 GPU 带宽和跨园区所需光纤对数。
- 把本报告拆进 MyNote 的空白笔记：`06. Distributed Computing/Traffic Models`、`AI Models`、`Architectures` 和 `08. Industry Chain/00.AIDC Custom`。

---

## 附：引用的本地讲稿（ECOC 2026）

| 简写 | 讲者 / 机构 | 所在笔记 |
|---|---|---|
| 0920-pm-Su3-A-02-OpenAI | OpenAI，AI Scale-Up Networks | B03 |
| 0920-pm-Su4-I-02-OpenAI | OpenAI，Scale-up 需求（同类内容） | B19 |
| 0921-MF-pm-1340-NVIDIA | NVIDIA，Spectrum-X 多平面网络的光模块 | B22 |
| 0921-MF-am-T08-1220-Meta | Meta 骨干工程，Scaling the Backbone Fabric | B21 |
| 0920-am-Su2-B-01-Google | Google，Scale-across 功耗 | 方向 2 底稿 |
| 0923-MF-美团 | 美团基础设施部，Agent 时代的光互连 | B54 |
| 0920-pm-Su4-C-03-华为 | 华为光产品线，算网一体设计 | B15 |
| 0923-We5-B-中兴 | 中兴 / 联通研究院，AIDC Scale-across CFP2 | B71 |
| 0924-Th1-G1-Corning | Corning，光纤时延对跨地域训练的影响 | B78 |
| 0923-We2-C3-1409-米兰理工 | Politecnico di Milano，LLM 与光网络 | B64 |
| 0922-MF-am-1140-CignalAI | Cignal AI，Scale Across 对相干市场的影响 | B40 |
| 0920-pm-Su4-I-07-Credo | Credo，宽并行光互连与拓扑对比 | B20 |
| 0922-PF-1155-SalienceLabs | Salience Labs，OCS 用于 scale-up | B42 |
| 0924-推定F2-Lightmatter | Lightmatter，光子互连与内存带宽 | B77 |
| 0920-pm-Su3+Su4-A-00-全场 | A1 下午全场扫描（含 Lumentum、NVIDIA 等） | B02 |
| 0921-Mo12-A3-Ciena | Ciena，AI 集群通信 | B24 |
| 0921-Mo3-A5-阿里云 | 阿里云，LPO 现网部署 | 管理摘要 |
| 0920-am-Su1-C-00-上半场速记 | BT 等 | B14 |
| 0920-am-Su1-C-03-STMicro | STMicro，硅光平台 | B14 |
| 0920-pm-Su3-I-02-LightCounting | LightCounting，AI 光模块市场 | B19 |
| 0920-pm-Su3-I-07-Marvell | Marvell，DSP 与波特率路线 | B19 |
| 0923-MF-Credo | Credo，市场聚焦 | B53 |
| 0920-pm-Su3-H-05-Adtran | Adtran，智能体 AI 做容量驱动 | B17 |
| 0922-Tu1-G1-KDDI | KDDI Research，AI 数据中心光传输 | B48 |

## 附：引用的 ECOC 2025 / OFC 2026 论文

- OFC26 W4H.5：中兴 / 长飞，600 km 长途多 AIDC 分布式训练现场试验
- OFC26 W4H.3：KDDI，可扩展到 30 km 的 OCS Scale-across 架构
- OFC26 W4H.4：实时流粒度控制器自动分配 OCS
- OFC26 M3F.5：剑桥，训练阶段感知的 OCS 重构
- OFC26 M4F.4：AIST，EP/TP 与 DP 网络间的高速光切换
- OFC26 W2A.28：伯克利 / Ayar Labs，LLM 推理中 OCS 的性能门限
- OFC26 Th3B.1 / Th3B.2 / W4H.2：AI 数据中心光模块现网故障分析与预测（含百度）
- ECOC25 Tu.04.06.2：华为法研所，分布式训练的时间、成本和能耗
- ECOC25 W.02.01.97：北邮，跨 DC 训练的流量交织连接开通（OTN 带宽省 40%）
- ECOC25 W.02.01.178：上海交大，GASTPipe 跨 DC 混合并行

## 附：互联网来源

- Microsoft 官方博客，Azure AI 超级工厂架构：https://blogs.microsoft.com/blog/2025/11/12/infinite-scale-the-architecture-behind-the-azure-ai-superfactory/
- Microsoft Fairwater Atlanta 报道：https://aimagazine.com/news/microsoft-inside-the-worlds-first-ai-superfactory
- Epoch AI，Stargate 各站点现状：https://epoch.ai/publications/openai-stargate-where-the-us-sites-stand
- Stargate 追踪（2026-09-18）：https://stargate.how/location
- Meta Hyperion 报道：https://thenextweb.com/news/meta-200-billion-hyperion-data-center-louisiana
- Meta El Paso 合资公告：https://about.fb.com/news/2026/07/meta-announces-new-venture-with-blackrock-to-develop-data-center-in-el-paso/
- Meta 多 GW 集群计划：https://www.datacenterdynamics.com/en/news/meta-to-invest-hundreds-of-billions-of-dollars-into-compute-to-build-superintelligence-with-several-multi-gw-data-center-clusters/
- Meta FT-HSDP 论文：https://arxiv.org/abs/2602.00277
- xAI Colossus 2 扩建报道：https://introl.com/blog/xai-colossus-2-gigawatt-expansion-555k-gpus-january-2026
- xAI 燃气轮机诉讼报道：https://tech-insider.org/xai-colossus-2-naacp-lawsuit-illegal-gas-turbines-memphis-2026/
- Google Iowa/Nebraska 集群：https://aidatacenterindex.com/datacenters/google-gemini-cluster-iowa-nebraska.html
- SemiAnalysis，多数据中心训练：https://newsletter.semianalysis.com/p/multi-datacenter-training-openais
- Google / Blackstone TPU 合资：https://www.cnbc.com/2026/05/19/blackstone-google-ai-data-center-joint-venture-tpu.html
- Google DeepMind，Decoupled DiLoCo：https://deepmind.google/blog/decoupled-diloco/
- AWS Project Rainier：https://datacenter.news/story/aws-s-11bn-indiana-data-centre-powers-anthropic-s-ai-growth
- Oracle Zettascale10：https://www.datacenterdynamics.com/en/news/oracle-unveils-zettascale10-ai-supercomputer-claims-it-will-be-largest-in-the-cloud/
- 北美资本开支汇总：https://introl.com/blog/hyperscaler-capex-690-billion-microsoft-azure-power-bottleneck-2026
- Google 每月 token 处理量：https://www.shacknews.com/article/149205/google-3-2-quadrillion-monthly-ai-tokens
- 阿里云乌兰察布与 100 天建设：https://m.21jingji.com/article/20260813/herald/de6c46fa7f92d5053d797c515fab449c.html
- 阿里 2032 年 20 GW 目标：https://m.bjnews.com.cn/detail/1758691286129908.html
- 阿里追加资本开支：https://www.sohu.com/a/938248298_122045489
- 字节 2026 资本开支：https://finance.sina.com.cn/stock/t/2026-05-28/doc-inhzmpqs0156749.shtml
- 字节算力中心盘点：https://news.idcquan.com/news/203906.shtml
- 火山引擎 token 与市场份额：http://finance.sina.com.cn/wm/2026-06-24/doc-inienxzw6214038.shtml
- 腾讯 / 阿里 2026Q2 资本开支：https://www.chinastarmarket.cn/detail/2370802
- 昆仑芯与腾讯采购：https://www.guancha.cn/economy/2026_06_29_821967.shtml
- 华为 Atlas 950 SuperPoD：https://www.huawei.com/cn/news/2026/7/atlas-950-superpod
- 华为 CloudMatrix384 推理论文：https://arxiv.org/pdf/2506.12708
- 东数西算 2026 进展：https://finance.sina.com.cn/stock/relnews/hk/2026-02-25/doc-inhnyyvs5232538.shtml
- 中国移动哈尔滨智算中心：http://www.sasac.gov.cn/n2588025/n2588124/c31597502/content.html
- 中国移动 GSE-DCI 与中国电信多芯光纤分布式训练：https://finance.sina.cn/stock/jdts/2026-03-03/detail-inhpsttq7581567.d.html
- DeepSeek-V3 技术报告：https://arxiv.org/pdf/2412.19437
- DualPath，Agent 推理的存储带宽瓶颈：https://arxiv.org/pdf/2602.21548
- Agent 推理与内存需求：https://www.trendforce.com/insights/ai-inference-drives-memory-demand
- Microsoft 可互换算力池（FY26 Q1 业绩会、Nadella 访谈）：https://www.microsoft.com/en-us/investor/events/fy-2026/earnings-fy-2026-q1 ；https://www.dwarkesh.com/p/satya-nadella-2
- OpenAI 与 Cerebras 750 MW：https://openai.com/index/cerebras-partnership/
- Google Ironwood GA 与 TPU 8t/8i：https://thenextweb.com/news/google-ironwood-tpu-inference-cloud-next
- Meta MTIA 路线：https://www.techzine.eu/news/infrastructure/139506/meta-shifts-to-ai-inference-with-its-future-chips/
- AWS Trainium 承载 Bedrock 多数 token：https://thenewstack.io/openai-bedrock-trainium-silicon/
- xAI 与 Humain 500 MW：https://www.datacenterdynamics.com/en/news/xai-humain-data-center-elon-musk/ ；Colossus：https://en.wikipedia.org/wiki/Colossus_(data_center)
- 字节海外训练（马来西亚 Blackwell）：https://www.enanyang.my/news/20260313/Finance/1192363
- 华为云 CloudMatrix384 部署：https://www.yicai.com/news/102565332.html
- 腾讯 Q2 业绩会：https://finance.sina.com.cn/tech/2026-08-12/doc-ininarrc3408590.shtml
- 推理与训练算力占比（媒体口径）：https://zhuanlan.zhihu.com/p/2054794322906821688
