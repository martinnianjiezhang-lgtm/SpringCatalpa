---
title: "T00_ScaleAcross转写"
tags:
  - OCP2026
  - 讲稿笔记
---

# T00 笔记：Scale Across 视频转写（T01–T06）

> 素材：`/Users/nianjiezhang/OCP 2026/Scale Across Discussion at 2026 OCP Summit/` 下 6 份 transcript.md + metadata.json。编号按目录名字母序。
> 索引：页码 [pN] 改用转写时间戳 [mm:ss]（对应 YouTube 原视频）。凡引用同名 PDF 讲稿处写作 [P### pN]，便于交叉核对。
> 口径说明：T02/T05/T06 为 YouTube 自动字幕（auto），T01/T03/T04 为上传者字幕（manual，同样有识别错误）。人名、机构以 PDF 首页为准，转写里的拼写错误不沿用。数字听感可疑、或与 PDF 不一致的，标"转写存疑"。

---

### T01 Breaking the Walls Open Scale Across for the AI Era presented by Cisco
- 视频：Qp0OwKYl6mc，约 21:02，manual 字幕，2026-10-13 | 对应 PDF：**P247**（executive-sessions/11_Breaking the Walls...）
- 讲者/机构：Rakesh Chopra（Cisco，SVP Silicon & Systems Architecture）、Vipul Deokar（Meta，VP Core Network Infrastructure）、Tom Williams（Cisco，VP Marketing）（姓名据 [P247 p1]；转写作 "Rakkesh/Bipple/Vipple"）| 类型：主题演讲（厂商 + 运营商联合）
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：DCI、ZR/相干、SRv6、深缓冲]；次 [Out 后端网络：交换芯片、SONiC]
- 核心主张：
  1. （Rakesh / Cisco）传统 DCI 承载的是松耦合的计算—存储—用户流量；scale across 是性能耦合负载，网络直接处在 AI 任务完成的路径上，网络一停顿就浪费 GPU [12:13–12:43]。
  2. （Vipul / Meta）Meta 新工作负载（预训练、推荐、推理、RL 后训练）对网络的要求是叠加的，旧负载不会消失 [04:34]；为此新建了按时延成环的区域骨干 RBB，和跨区域后端互联的 scale across [07:26–08:27]。
  3. （Tom / Cisco）光层要"别挡路"：带宽够、可靠（包括不出 link flap）、省电；scale across 带宽推动可插拔相干和多轨（multi-rail）线路系统 [15:06–16:26]。
- 关键数据：
  - 训练最大模型所需 GPU：过去约 100 张，近期 xAI 某模型用到 200,000 张 [00:03]（引用；转写作 "XI classes"，转写存疑；[P247 p2] 写作 xAI Colossus (Grok family) 200K+，GPT-2 为 100+）
  - 训练算力每 5 个月翻一番 [00:23]（引用 Stanford 研究；[P247 p2] 注为 Stanford HAI 2025 AI Index）
  - （Meta）Prometheus 区域由 H 形楼、"DC type F"、帐篷（tents）和公有云容量混合组成；年底达到 1 GW 集群规模，目前已在训练多个模型 [05:06–05:19]（现网/自报）
  - （Meta）"Rings"：按光纤长度换算的 1 ms / 5 ms / 10 ms 时延把相邻 DC 区域归组 [06:23]；做法是存储/支撑服务放在一个区域，算力放在另一区域，用来加快新区域上线、省掉各区域重复部署本地服务的算力 [06:55–07:26]（自报）
  - （Meta）RBB（regional backbone）基于 FBOSS，仍接 EBB，把原先走 EBB 或 DC 内部的流量卸载到 ring/RBB 上 [07:52–08:21]（自报）
  - （Meta）scale across：用大量光纤把两个 DC 区域的后端连起来，训练下一代模型；园区内用 FR，部分用 LR，重点在 coherent/ZR 可插拔 [08:27–08:59]；前端和后端都接入，并内置光保护，以减少 ZR 和 IP 端口用量 [09:30]（自报）
  - （Meta）RBB 覆盖 1/5/10 ms 时延，scale across 应用有时 >100 km [10:02]（自报；[P247 p13] 写 ILA-free 120–150 km、带 ILA 500 km+，两端 "10,000s of 800G ZR"）
  - （Cisco）Silicon One P200：可编程、深缓冲、拥塞感知、内置安全、遥测；可做固定盒式或模块化系统 [14:04–14:31]（自报）
  - （Cisco）NCS1010 做 C+L 时 7 条线路要占满一个机架；Transport 3000 多轨系统 2 张线卡即可承载 8 条 C+L [16:26–16:58]（自报；[P247 p23]：NCS1010 每 C+L rail 350 W、每架 7 rail；Open Transport 3000 在 12 kW 内 32 条 C+L rail，功耗降 75%、空间省 80%）
  - （Cisco）运维单位从"开一个波长"变成"开一整条线路（fiber line）"[17:28]（自报）
  - 相干可插拔标准化脉络：OIF 400ZR → OpenROADM / OpenZR+ 400G → 800G 由 Meta 牵头推动，约 4–5 年前开始 [17:28–18:30]（自报）
  - Cisco 展位 C59：80 km 光纤 scale across 现场演示；另有 1.6T scale-out 光模块、102.4T 交换机、SONiC [20:11]（自报）
- 提到的公司/客户/产品/标准：Meta（Muse / Muse Spark / Muse Wonder 模型、Prometheus、EBB、RBB、FBOSS）、Cisco（Silicon One P200、NCS1010、Transport 3000）、xAI、OIF 1600ZR、OpenROADM、OCP SAI、IETF SRv6
- 首次/记录/SOTA 声明：Meta 称 RBB 是"新的骨干域"[07:52]；其余无
- 推荐配图页：[P247 p12]（按 <3 km FR / <10 km LR / >10 km ZR+DWDM 分距离的楼群图）；[P247 p13]（光保护 + ILA-free 120–150 km 架构图）；[P247 p23]（单轨 vs 多轨 OLS 功耗/空间对比）

---

### T02 From Single Data Centers to Multi Region AI Clusters The Rise of Scale Across
- 视频：z1xRELMKzrA，约 24:35，auto 字幕，2026-10-15 | 对应 PDF：**P138**（ai-clusters）
- 讲者/机构：Spencer Giacalone（Ciena，Senior Director Cloud AI Architecture）、Helen Xenos（Ciena，Senior Director Product Marketing）（据 [P138 p1]；转写作 "Spence Shaloney / Sienna"）| 类型：技术分享
- 方向归属（主/次）：主 [Across：DCI、ZR/相干]；次 [推理/算力/经济性]、[Across：长RTT拥塞控制]（仅提出无损物理层诉求）
- 核心主张：
  1. 拥塞控制、负载均衡只能管理争用，不能替代容量；scale across 的基础是光层容量和路径多样性 [00:30–01:04]。
  2. 定义：scale across 指为训练一个（或多个）AI 模型，把无损连接延伸到园区/区域之间；园区 = 单一连续地块；分包层与相干 DWDM 层两部分 [02:56–03:18]。按此定义相干是"必需"而非可选 [04:42]。
  3. 规模化后"整根光纤"成为部署单元，推动 multi-rail 光层和全谱转发器（full spectrum transponder, FST）[13:48–15:53]。
- 关键数据：
  - 选址顺序变化：电力第一，其次自发电、冷却、到其他训练点的精确光纤距离；园区宣称的功率是终态额定值，并非第一天可用 [01:52–02:22]（自报）
  - DP-16QAM 双正交载波，同一符号周期内承载 4 倍流量 [04:42]（自报/原理）
  - 单根光纤上合 32 个 1.6T 接口，借中段放大传数百倍距离 [04:42]（自报；转写为 "32 1.60 60"，转写存疑，按 32×1.6T 理解；与 [P138 p12] "51.2T C&L FST 由 1.6T modem 组成"一致）
  - 大项目中，一对训练园区之间部署的容量 = 约 6 年前一个超大规模区域所有前端 DC 之间容量的 14 倍 [05:20]（自报；[P138 p6] 标 "14x / Front End Region circa 2020"，同页另有 scale across 收敛比 ">8:11"，转写未提，看不清）
  - near scale across：不需要中继放大（ILA），点对点满配 C+L，无上下路复用，第一天全部点亮 [05:52–06:24]；距离"100 km 以内，最多约 150 km"[10:40]（自报；[P138 p7] 以 <150 km / >150 km 区分 near / far）
  - 实现模式三种：① N+1 光保护切换 + 路由器内 ZR+，光纤断时光层先于包层完成倒换；② 同上但用于 far；③ active-active，由包层倒换，外置转发器（如 FST），用于插件够不到的距离或路由器采用 CPO 时 [06:54–07:18]（自报）
  - 800G 相干可插拔已在 scale across 部署；新需求是 C+L 两段都有相干插件；near 场景可用 EDFA/Raman 混合放大延长距离 [08:02–09:48]（自报）
  - 按传统线路系统设计需 22 个放大小屋（amp hut）[11:59]（自报；[P138 p10] 场景为 20 Pb/s AI 网络，传统每架 4 rail）
  - multi-rail 平台（接近 GA）：单机箱密度 16 倍，功耗降 75%；满机架密度 32 倍，最多 128 rail/架 [12:44–13:06]（自报；[P138 p10] 写 32x、128 rails/rack、1 hut）
  - 满纤配置：400G 插件每纤对两端各 128 个；800G 各 64 个 [13:32–13:48]（自报；[P138 p9] 另给 20 Pb/s 用例："数百纤对、每纤对 64×800G C&L"）
  - 演进路径：hyper-rail 替代 4 个 ILA 模块 → 点对点满配时去掉 ROADM → FST 替代收发器与合分波，形成可复制的 cookie-cutter 部署 [15:00–15:53]（自报）
  - 趋势：所有 near 客户都在评估或转向 far，主因是电力；预计 2027 年出现"客户专属 AI 骨干网"；也有客户考虑用 OCS 做区域可重构网络 [16:09–16:44]（预测/客户反馈）
  - 呼吁建立"可验证无损"物理层（新 FEC），因现有相干 FEC 为容忍丢包的业务设计 [17:18–17:51]（自报；[P138 p15] 给出目标示例 1e-24 post-FEC BER）
  - 推理：总量将大于 scale across，但更分散、项目节奏更线性、流量更网状，本次讲的产品可沿用 [19:02]（预测）
  - Q&A：FST 可靠性——拆成 4 个现场可替换模块，或模块内做 N:1 保护 [21:27–21:56]（自报，设计选项）
  - Q&A：训练距离——"今天 115 或 20 km"，客户将走向 500、800 km，最终约 1,000 km，且指同步预训练 [22:25–23:06]（客户反馈/预测；"115 or 20" 转写存疑，可能是 100–120 km）
- 提到的公司/客户/产品/标准：Ciena（WaveLogic、RLS、RLS Hyper-Rail、FST 概念）、ZR+、DP-16QAM、EDFA/Raman、OCS、CPO；[P138 p2] 列出 UEC、MRC、MetaRoCE
- 首次/记录/SOTA 声明：提出 near/far scale across 与"连续地块园区"定义，愿捐给社区 [18:18]；无性能记录声明
- 推荐配图页：[P138 p7]（near vs far 设计表）；[P138 p10]（22 huts vs 1 hut 的 multi-rail 对比）；[P138 p12]（51.2T C&L FST 结构示意）

---

### T03 Multi Core Fiber A solution for scale up, out, and across presented by Sumitomo Electric
- 视频：5zc5bcxiGYo，约 13:51，manual 字幕，2026-10-16 | 对应 PDF：**P316**（expo-hall-sessions）
- 讲者/机构：Dwayne Holst（Sumitomo Electric Lightwave，Optical Communications Engineer）（据 [P316 p1]；转写作 "Holes"）| 类型：厂商展区
- 方向归属（主/次）：主 [Across：空芯/多芯光纤]；次 [Out 后端网络：可插拔光模块]、[Up 机柜/超节点：机柜级互连]。注：内容主要是 DC 内光纤密度，scale across 只在 [09:59] 一句带过
- 核心主张：
  1. 未来机柜光纤数量会让单芯光缆在布线空间上走不通；DC 内短距离用 WDM/相干不划算，仍需直调直检，出路是空分复用、看"芯密度"而非"纤密度"[04:34–05:09]。
  2. 多芯光纤（MCF）+ 多芯收发器可以把收发器和光缆数量压缩数倍 [09:43–10:20]。
  3. 模型走向边缘/本地部署后，要在已拥挤的现有管道里塞更多容量，MCF 更有价值 [12:31–13:01]。
- 关键数据：
  - 576 GPU/机柜 → 每柜 18,464 根光纤 [02:08–02:14]（预测；[P316 p3] 对应 Feynman F300 / Kyber+，2030+）
  - 若用 2 mm 单芯光缆，一柜出线束直径约 1 英尺，一排末端约 6 英尺 [02:14–02:56]（估算）
  - 200 万 GPU DC：用 Gemini 估算约 80,000 台 512 端口交换机、约 3,000 万根线缆 [03:54]（AI 生成估算，非工程数据）
  - 4 芯 MCF：包层仍为 125 μm，内含 4 个 9 μm 芯，单纤容量 4 倍 [05:09]（自报）
  - 6,912 芯单芯光缆外径约 37 mm；约 38 mm 光缆若用 12 芯 MCF 可承载 55,000 lanes [06:51–07:14]（自报；转写存疑：[P316 p8] 文字层给的对比是 6912 芯——单芯 OD ~37 mm/1075 mm²，4 芯 MCF OD ~13 mm/133 mm²，管道空间省 60–80%；12 芯/55,000 未在 PDF 文字层见到）
  - 实验室单纤 19 芯，26 Pb/s [07:32–07:45]（实验，日本实验室）
  - 19 芯采用耦合芯（supermode）：有效面积增大，可提高发射功率，自相位调制、四波混频下降 [08:26–08:57]（自报/原理）
  - 16 lane 互连：现状 16 个收发器 / 4 根缆；MCF 方案 1 根缆；Eoptolink 已有 800G 4 芯收发器，免 FIFO，4 个收发器 + 1 根缆等效 16 个 [09:43–10:20]（自报）
  - 4 芯连接器：24 纤 MPO → 96 光路；16 纤 MMC → 64 光路；已在售 24 纤 MMC，未来 32 纤 [10:46–11:22]（自报；[P316 p9] 写 96-core MPO-APC、64-core MMC-APC）
  - 1RU 可容纳 33,000 根"fibers" [11:29]（自报；转写存疑，可能指芯/光路数）
  - 成本：4 芯收发器约为单芯的 3–5 倍，光缆成本倍数相近；回报在线缆支撑结构 [11:49–12:04]（自报；[P316 p12] 称 MCF 总拥有成本更优，且尚未标准化）
- 提到的公司/客户/产品/标准：Sumitomo Electric Lightwave、Eoptolink（800G 4 芯收发器）、AMD（引用其 agentic 增长预测）、OCP Academy、Senko、Viavi（[P316 p2] 致谢）；MPO、MMC、FIFO
- 首次/记录/SOTA 声明：19 芯单纤 26 Pb/s 实验室结果 [07:32]（自报，无条件说明）
- 推荐配图页：[P316 p3]（Hopper→Feynman 每柜光纤数递增路线图）；[P316 p8]（6912 芯单芯 vs 4 芯 MCF 光缆截面对比）

---

### T04 SRv6 Deployments in Scale Out and Scale Across Networks
- 视频：6R5ZnYFMNQs，约 39:30，manual 字幕，2026-10-15 | 视频含两场连续报告：A 段 [00:03–21:27]、B 段 [21:56–39:18]
- 对应 PDF：A 段 **P422**（"SRv6 Deployments in Scale-Out Networks"）；B 段 **P429**（"Traffic Engineering in AI DCI-WAN for AI Traffic"）。相关：P425（Meta SRv6 backbone）、P141（MRC 与 SRv6 配置）
- 讲者/机构：A 段 Clarence Filsfils（Cisco）、Guohan Lu（OpenAI）；B 段 Clarence Filsfils（Cisco）、Yuanchao Su（Alibaba Cloud）（据 [P422 p1][P429 p1]；转写作 "Guan / Yanu / Yuan Shao"）| 类型：技术分享（运营商部署经验）
- 方向归属（主/次）：主 [Across：SRv6]；次 [Out 后端网络：MRC、负载均衡、SONiC]、[Across：ZR/相干]
- 核心主张：
  1. （Filsfils / Cisco）SRv6 把 128 bit IPv6 目的地址变成有序微指令列表，一套机制覆盖 DC、DCI、WAN，替代各域的 VXLAN / MPLS 垫层 [01:14–04:24]。
  2. （Lu / OpenAI）同步训练流量少而大、同时起落，ECMP 哈希会在 100G 单链路上碰撞；由主机知道通信模式并用 SRv6 做源路由，配合 MRC 实现确定性路径放置和快速绕障 [06:47–10:33]。
  3. （Su / Alibaba）scale across 网络为 token 性能服务（TTFT、TPOT、TPS 与成本）；三条原则：专用网络、单租户单栈（IPv6+SRv6，无 overlay）、模型与基础设施协同设计 [29:38–30:52]。
- 关键数据：
  - （Filsfils）>95% 部署使用 16 bit 微指令，单个目的地址可装 6 条；约 3 年前演示过线速插入 30 条；99% 部署用不到 5–6 条 [02:45–03:19]（自报）
  - （Lu）两层多平面网络，端口拆成 100G 单链路；与 Microsoft Fairwater DC 合作，单 DC 有望扩展到 50 万 GPU [06:47–09:00]（自报/预测）
  - （Lu）GPU 到 GPU 经两层网络为 4 跳，可放进单个 IPv6 DA 的 6 个 uSID 中；NIC 封装、交换机 shift-and-forward、目的端解封装；支持 uN 和 uA；SONiC 原生支持 SRv6，基于 FRR 管理配置 [10:33–12:09]（自报）
  - （Lu）生产事件：约 75k GPU 训练作业中一台 T1 交换机静默黑洞丢包；约 25% QP 受影响；MRC 探测后剔除路径，吞吐恢复，检测与恢复约一个 RTT 量级，告警晚于恢复 [13:05–14:18]（现网；丢包数转写为"about a million"，[P422 p13] 为 ~580K，以 PDF 为准，转写存疑）
  - （Lu）Q&A：MRC 也支持基于熵的 ECMP，SRv6 只是可选路由方式之一 [17:29]；封装开销需按平均包长权衡，SRv6 也可不封装 [19:35–20:29]（自报）
  - （Filsfils）DCI 的拓扑更不对称、容量更稀缺、时延更敏感，因此 TE 是必需 [23:06]；Alibaba 2021 年决定以 SRv6 + Silicon One + SONiC 建 eCore，2023 年开始部署 [23:41–24:16]（现网）
  - （Filsfils）三种把 AI 流量导入 DCI TE 策略的方式：A 在汇聚路由器做 DPI 识别 RDMA 流；B 主机/NIC 直接下发端到端 uSID 程序，跨 DC spine/leaf + 5–7 跳 DCI 可能需 10–12 条微指令；C 用 Binding SID，DCI 路由器预建到各 DC 的策略（如 64 条），老 NIC 只用 2 条微指令即可控制全程 [25:37–29:20]（自报）
  - （Su）eCore 按业务复制为多张专用网（公有云、金融、集团、对等互联、AI）；单故障域仅数十节点 [31:26–32:38]（现网/自报）
  - （Su）scale across 拓扑收敛聚合层为一层；公有云 eCore 用 128 端口盒、长途仍有不少 100G 链路正迁往 400G，scale across 起步即 64×800G [33:29–34:33]（现网；转写把 100G 识别成 "one gig"，转写存疑；[P429] 拓扑图写 128×100G/128×400G vs 64×800G）
  - （Su）现场测试发现长途 100G 链路易引发哈希碰撞，结论"粒度越大哈希越好" [34:42]（现网测试）
  - （Su）per-job TE：用 RDMA BTH 头中 4 个保留位作为 TE 选择位，由平台让 NIC 打标，边缘 eSR 设备识别后导入对应 SRv6 策略，形成多个时延一致的逻辑切片 [35:19–36:29]（自报；[P429 p12] 注 P200/Q4D 支持）
  - （Su）全谱转发器：32 个波长放进一个紧凑设备，单纤对承载 25.6 Tb/s，用满 C 波段 [37:06]（自报；"compact 2 device" 转写存疑；[P429 p13] 结构为 32 路 DSP/COSA + AWG，25.6T 未在 PDF 文字层见到）
  - （Su）LD/RD 主动收敛：光模块检测 BER 超过 pre-FEC 门限后向远端注入 RD，同时通知本地交换机从 ECMP 组剔除该路径，实现无损（zero packet loss）切换 [37:42–38:26]（自报；称上月某会议已展示，会议名转写为 "absera"，转写存疑）
- 提到的公司/客户/产品/标准：Cisco（Silicon One）、OpenAI（MRC）、Microsoft Fairwater、Alibaba（eCore、TPN DCN、eSR）、Broadcom（交换芯片）、SONiC、FRR、IETF SRv6 / uSID / SRH / Binding SID、RoCE BTH
- 首次/记录/SOTA 声明：无（Filsfils 称 OCP 本届有 5 场 SRv6 报告 [00:03]）
- 推荐配图页：[P422 p13]（T1 黑洞事件时间线：75K GPU、~25% QP）；[P429 p12]（per-job TE：Job→BTH→SRv6 策略）；[P429 p13]（FST 与 LD/RD 结构图）

---

### T05 Scale Across To Go Forward or To Go Backwards, That is the question
- 视频：CS5Iu94q5jE，约 18:26，auto 字幕，2026-10-15 | 对应 PDF：**P146**（ai-clusters）
- 讲者/机构：Jai Kumar（Broadcom，Distinguished Engineer）、Tom Emmons（Arista Networks，Software Engineer）（据 [P146 p1]）| 类型：技术分享 / 标准进展
- 方向归属（主/次）：主 [Across：长RTT拥塞控制、深缓冲]；次 [Out 后端网络：UEC、拥塞控制、交换芯片]
- 核心主张：
  1. （Kumar / Broadcom）scale across 网络包含两个低 RTT 域（本地 DC、远端 DC）和一个高 RTT 的 DCI 域；现有拥塞控制按单一 base RTT 设计，没考虑多 RTT 域 [03:48–04:18]。
  2. （Emmons / Arista）PFC、ECN、CSIG、trimming 都是前向信号、需接收端反射，最快也要一个 RTT；而同步训练中许多流比一个 RTT 还短，发送端来不及得到信息 [07:40–08:10]。
  3. 解法方向：由 DCI 入口交换机直接向发送端生成控制消息（Back-to-Sender, BTS），反应时间小于 RTT [09:06–10:33]。本场只提问题、不给答案。
- 关键数据：
  - 丢包信号在高时延链路上先前向到接收端、再返回发送端，拉长流完成时间 [05:18]（原理）
  - 交换芯片带宽增长快于片上内存，每代每 Gb/s 内存更少；加上队头阻塞，业界想离开 PFC [06:18]（自报）
  - ECN 仅 1 bit，需多包聚合或多个 RTT 才收敛；UEC "周一刚发布"的 CSIG 提供约 10 bit 遥测 [06:44–07:13]（自报；"10 bits" 为口述，未见 PDF 核对）
  - trimming 和 CSIG 仍会在关键链路上增加前向流量（截断包、包变大）[08:10–08:37]（自报）
  - BTS 关注三类事件：队列拥塞、拥塞导致的队列丢包、路径故障 [11:23–11:52]；回传信息：产生设备、流量类别、队列深度及前向上下文 [12:23]（自报）
  - 设计约束：不改传输头和转发头、交换机无状态、BTS 控制流量占带宽 <1% 左右 [12:50–13:48]（目标值；[P146] 写 "~1% or less"）
  - 待解问题：多跳拥塞是否每跳都通知；同一包先拥塞后丢弃的双重通知；BTS 速率由发送端还是交换机控制（交换机限速会让发送端不知道丢了哪些通知）；CC 算法如何适配多 RTT 域 [14:00–15:18]
  - （Emmons）仿真和论文显示 BTS 能显著改善 CC 收敛 [15:38]（引用，未给出具体数值）
  - 标准：UEC 已有 BTS 工作组在写规范；OCP SAI 工作流在做配套 SAI 模型 [16:04]（标准进展）
  - Q&A：接收端授信（credit）方案适合单一应用独占 scale across 链路；客户链路上多为多应用混合流量，需要对网络实时状态做反应的机制 [17:24–17:51]（观点）
  - 范围口径：[P146 p2] scale up <30 m，scale across 为 100+ km 的路由城域/区域 WAN（PDF 口径，转写只说"数百至数千公里"[02:11]）
- 提到的公司/客户/产品/标准：Broadcom、Arista、UEC（CSIG、trimming、BTS WG）、OCP SAI、PFC、ECN
- 首次/记录/SOTA 声明：无
- 推荐配图页：[P146 p3]（参考网络模型：本地 DC / DCI 高时延链路 / 远端 DC 与 T2a 拥塞点）

---

### T06 Scale across Networking Panel discussion on routing and transport equipment implications
- 视频：LdjbbZV7zCg，约 35:25，auto 字幕，2026-10-15 | 对应 PDF：**P147**（ai-clusters，52 页）
- 讲者/机构：主持 Vijay Vusirikala（Arista Networks，转写作 "VJ"）；Tad Hofmeister（Google Cloud）、Jeff Rahn（Meta）、Yawei Yin（Microsoft Azure）、Xiguang (Henry) Wu（Broadcom）（据 [P147 p1–p2]）| 类型：面板（4 人轮流短讲，无观众问答）
- 方向归属（主/次）：主 [Across：ZR/相干、深缓冲、长RTT拥塞控制]；次 [Out 后端网络：OCS、可插拔光模块/LPO/LRO]、[Up：CPO/NPO]、[运维/可靠性/遥测]
- 核心主张（按发言人）：
  1. **Google（Tad）**：除了几十到几百公里的 scale across，还有"园区级互连"（同园区跨楼的 scale-out）；多楼互连宜走 OCS，物理层宜用 coherent-lite（CL）而非 IMDD 或 ZR [01:06–08:02]。演示内容为研究中的设计，不代表 Google 现网或承诺 [00:48]。
  2. **Meta（Jeff）**：从 10 km（LR）到 100 km（ZR+DWDM）的 scale across 依赖标准化、可代际互通、可在 DC 与骨干间通用的可插拔相干光；长期目标是算力跨区域乃至跨大洲协同 [12:05–15:20]。
  3. **Microsoft（Yawei）**：电力分布不均，算力只能跟着电走，必须跨园区、跨区域 scale across；网络增长慢于计算和存储；行业技术选项过多，量产时应收敛到少数几种 [18:27–23:58]。
  4. **Broadcom（Henry）**：长距离下 BDP 暴增，scale across 交换机的首要条件是层级化深缓冲，缓冲需 ≥1.5×BDP [24:06–34:37]。
- 关键数据：
  - （Google）Virgo scale-out fabric 限定在单楼内；跨楼需求源于楼宇面积或功率预算 [01:52]（自报；[P147 p5] 以 New Albany 园区为例）
  - （Google）楼间带宽为数十到数百 Pb/s；园区尺度可达 2 km，个别更长 [02:34]（自报；[P147 p6] 写 10s–100s Pbps = 10,000–100,000 Tbps）
  - （Google）OCS 时延低、"基本不耗电"，优于加一层电交换 spine [04:11]；用光复用把多个端口合到一对纤、一个 OCS 端口，代价是链路损耗增加 [04:55]（自报）
  - （Google）IMDD 在 400G/lane 下跨 2 km 以上受色散限制，WDM 波长数约 16 个即到上限 [05:21–05:40]（自报）
  - （Google）coherent-lite 的成本、功耗、时延都低于 ZR，目前无现成产品，已在 OIF 立项 [06:15]；相干与 IMDD 的功耗差距随工艺缩小，到 1.6T 及以后与全重定时 IMDD 基本持平 [06:50]；短链路可用更轻的 FEC 降时延 [07:25]（自报；转写为 "lower loss FEC"、"OAF"，转写存疑，[P147 p9–p10] 为 lower latency FEC、OIF 1.6T-CL、O-band、相对 IMDD 4 倍频谱效率、2nm DSP）
  - （Meta）DC 间同步流量早已超过用户流量，约大一个数量级 [10:58]（现网/自报）
  - （Meta）≤10 km 用 LR（或 DR）灰光，但需大规模挖沟布纤；>10 km 改用 DWDM + ZR，覆盖到约 100 km [12:05–12:35]（现网；[P147 p23–p25] 写楼群 <3 km、<10 km、10 km+ 三档，800ZR+ + DWDM 迈向 GW 级）
  - （Meta）刚完成全网 400ZR+ → 800ZR+ 升级，逐站点进行，代际互通是唯一可行前提；这是可插拔相对转发器的特有优势 [13:06–13:36]（现网）
  - （Meta）基本按满配 C+L 部署；光模块在 DC 与骨干间通用、可在项目间调配 [13:36–14:26]（现网）
  - （Meta）光链路保护在多数情况下可让终端 IP 端口和转发器数量减半 [14:26]（自报）
  - （Microsoft）DC 规模从公有云常见的 50–300 MW 走向 GW 级区域；网络约占总功耗 10–15% [19:18–19:55]（自报估算）
  - （Microsoft）能效粗估：长途 EDFA/WDM 系统为数千 pJ/bit 级，NPO/CPO 和部分 LPO 可到个位数 pJ/bit [20:25–21:04]（自报估算；[P147 p41] 表：传统转发器 >1000、400ZR/城域 45–55、FRO 18–25、LRO 10–18、LPO 7–10、NPO 5–8、CPO 1–5 pJ/bit）
  - （Microsoft）光学方案按距离分段：IMDD 几米到 2 km、LR 到 10 km；相干覆盖楼宇/园区几十 km、ZR 到 100–120 km、ZR+ 可达数千 km [22:00–22:25]（自报）
  - （Microsoft）可靠性：光纤被子弹、箭、老鼠破坏的实例，跨城训练必须考虑 [21:33]（现网案例；[P147 p42] 另写 OSP 光纤市场可用性约 97.7%，转写未提）
  - （Broadcom）BDP = 带宽 × RTT；单流 800G、100 km 时 BDP = 100 MB，随距离线性增长 [24:42–25:00]（计算；[P147 p46]：5 km/5 MB、100 km/100 MB、1000 km/1 GB）
  - （Broadcom）ECN 生效至少需一个 RTT 的缓冲，且 ECN 与 PFC 门限间要留余量防振荡，多流时需数百 MB 到 GB 级，片上缓冲做不到 → 片上 + HBM 层级缓冲，拥塞时转入深缓冲、消退后切回 [27:29–29:47]（自报）
  - （Broadcom）仿真：缓冲 1.5×BDP 时流完成时间接近理想；降到 10–20% BDP 的浅缓冲区，开销升到 20–30%，且重传率与尾时延直接相关 [30:14–31:39]（仿真）
  - （Broadcom）结论对 50–500 MB 三种消息大小、10 km 及更远距离、发送端 NSCC 与接收端 RCCC 都成立 [31:39–31:55][34:37]（仿真；[P147 p49] 写明距离为 10/30/100 km）
  - （Broadcom）其他要求：数万个 ECMP 组、每组上千成员；微秒级故障反应；线速 MACsec 无性能损失 [33:05–33:40]（自报）
  - （Broadcom）100T 交换机按 1.5×BDP 需总缓冲 5.6 GB [34:37]（仿真推算；转写未说距离，[P147 p51] 显示 5.6 GB 对应 30 km，10 km ~1.9 GB，100 km ~18.8 GB）
- 提到的公司/客户/产品/标准：Google（Virgo、OCS）、Meta、Microsoft、Broadcom、Arista；OIF 1.6T-CL、400ZR/800ZR+/1600ZR、OpenROADM（隐含于"open line system"）、UEC NSCC/RCCC、MACsec、LPO/LRO/NPO/CPO
- 首次/记录/SOTA 声明：无
- 推荐配图页：[P147 p9–p10]（Google coherent-lite 与 IMDD 对比）；[P147 p41]（Microsoft 按距离的 pJ/bit 能效表）；[P147 p51]（Broadcom 1.5×BDP 缓冲需求：10/30/100 km 对应 1.9/5.6/18.8 GB）

---

### 交叉对照（6 场之间的口径差异，供写报告时核对）
- **距离分档**：Meta 两场说法一致——园区内 FR（<3 km）/ LR（<10 km）/ >10 km 用 ZR+DWDM（T01 [08:59]、T06 [12:05]）；Ciena 以约 150 km 是否需要 ILA 区分 near/far（T02 [10:40]，[P138 p7]）；Cisco/Meta PDF 写 ILA-free 120–150 km、带 ILA 500 km+（[P247 p13]）；Ciena 称客户将走到 500–800 km，最终约 1,000 km（T02 [22:50]）；Meta Jeff 说长期可能跨大洲（T06 [15:20]）。
- **全谱转发器**：Ciena（C+L，1.6T modem，51.2T 概念，T02 [13:48]）与 Alibaba（C 波段 32 波，25.6T，T04 [37:06]）都在推，两者规格口径不同。
- **光保护**：Meta（T01 [09:30]、T06 [14:26]）、Ciena（T02 [06:54]）都把光层保护作为节省 ZR/IP 端口的手段；Meta 给的量化是"多数情况下减半"。
- **拥塞/缓冲**：Broadcom 有两种思路——T05 的 BTS（亚 RTT 回送发送端，控制流量 <1%）和 T06 的深缓冲（≥1.5×BDP）；Cisco P200 同样强调深缓冲（T01 [14:04]）。Alibaba 则主张用大链路粒度（64×800G）减少哈希碰撞（T04 [34:42]）。
- **SRv6**：Meta 在 RBB/AIBB 部署 SRv6 TE（T01 [11:11]）；OpenAI 在后端 scale-out 用 SRv6 源路由（T04 [10:33]）；Alibaba 在 scale across WAN 用 SRv6 + BTH 打标做 per-job TE（T04 [35:19]）。
