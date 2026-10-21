---
title: "OCP 方向1 Scale Across 综合洞察"
tags:
  - OCP2026
  - 综合洞察
---

# 方向1：Scale-across（跨楼/园区/区域 AI 集群互连：DCI、800ZR/1600ZR、多rail/全谱线路系统、SRv6/路由、深缓冲与长RTT拥塞控制、空芯/多芯光纤、光保护）

索引说明：〔Pxxx pN〕为 OCP 2026 讲稿 PDF id + 页码；〔T0x mm:ss〕为 6 场 Scale Across 专场视频转写时间戳（T01 Cisco/Meta、T02 Ciena、T03 Sumitomo、T04 SRv6 双场、T05 Broadcom/Arista、T06 五方面板），映射见文末索引对照表。T02/T05/T06 为自动字幕，数字与 PDF 不一致时以 PDF 为准，并标"转写存疑"。口径：自报、仿真、实验、现网、预测、引用（注明来源）、看图、存疑。

素材范围：by_direction/Across.md（主归属 24 节、次归属 14 节）+ notes/T00_ScaleAcross转写.md + 相关 PDF 文字层核对（P138、P147、P364、P424、P425）。近重复：P273 与 P441（TeraHop）内容大部分重合，合并为一个来源计数；P122 与 P153 为同一讲稿。本方向未见空芯光纤（HCF）讲稿，多芯光纤只有 Sumitomo 与 TeraHop 两个来源，且主要讲 DC 内布线。

---

## 0. 一句话结论 + 5 条核心判断

**一句话结论：** OCP 2026 上的 scale-across 已经是现网工程而非概念：Meta 的 1 GW Prometheus 跨楼、帐篷和托管站点运行，800ZR+ 全网升级完成，区域骨干 RBB 从立项到首站 5 个月；驱动力是电力分布，不是网络偏好。光层的部署单元从"一个波长"变成"一对光纤"，相干可插拔 + 光保护 + 多 rail 线路系统是当前主力，全谱转发器（FST）是下一步；包层的分歧集中在长 RTT 下要不要深缓冲（Broadcom/Arista 仿真要 ≥1.5×BDP，Meta RBB 现网用浅缓冲 + ECN 跑到 650 km），以及如何把拥塞反馈缩到一个 RTT 以内；SRv6 正在成为 DC、DCI、WAN 统一的路径控制手段。

**判断1：scale-across 的动因是电力，距离分层在各家之间已基本收敛为"<3 km 灰光 / <10 km LR / >10 km 相干 DWDM"，再往外以是否需要 ILA（约 120–150 km）划分 near/far；远端目标被推向 500–1,000 km。**
- 电力约束有现网与规划两侧的数字。Microsoft：传统单 DC 50–300 MW，下一代训练集群 1 到 5+ GW，新站点并网周期 3–7 年，结论是多站点训练"不是可选项"（自报）〔P147 p40〕〔T06 19:18〕。Ciena：选址顺序已变成电力第一，园区宣称的功率是终态额定值而非第一天可用（客户反馈）〔T02 01:52〕。Meta：Prometheus 1 GW，含传统楼宇、户外帐篷与相邻托管设施（现网）〔P424 p4〕〔T01 05:06〕。
- 距离分层：Meta 两场口径一致，楼 1–4 <3 km 用 FR，楼 5–6 <10 km 用 LR，10 km+ 用 800ZR+ + DWDM（现网）〔P147 p25〕〔P247 p12〕〔T06 12:05〕；Meta BAG 平台混插 FR4 ≤3 km、LR4 ≤10 km、ZR+ ≤1,000 km〔P424 p10〕。Ciena 以 150 km 为界：<150 km 为 near（扩展园区、无 ILA、点对点满配 C+L），>150 km 为 far（需 ILA）〔P138 p7〕〔T02 05:52〕；Cisco/Meta 图写 ILA-free 120–150 km、带 ILA 500 km+〔P247 p13〕。
- 机制：同步训练里一对园区之间的容量是 2020 年前后整个前端区域的约 14 倍（看图）〔P138 p6〕〔T02 05:20〕；Meta 称 DC 间同步流量已比用户流量大约一个数量级（自报）〔T06 10:58〕。在这个流量规模下，灰光每纤只有 Tb/s 级，必须挖沟布大量光纤，10 km 以外改用每纤数十 Tb/s 的相干 DWDM 更划算〔P138 p5〕。
- 方向：Ciena 称所有 near 客户都在评估或转向 far，主因是电力；客户训练距离将从今天约 100 余 km 走向 500、800 km，最终约 1,000 km，指同步预训练（客户反馈/预测；"115 or 20 km"转写存疑）〔T02 16:09〕〔T02 22:25〕。Meta 已在 800G-ZR+ 上跑到 650 km 跨度〔P425 p5〕。

**判断2：光层部署单元从波长变成光纤对。当前主力是"路由器内 800G 相干可插拔 + 光保护 + C+L 满配"，多 rail 线路系统已接近 GA，FST 仍在概念/早期阶段；收益数字全部是厂商自报。**
- 可插拔相干已在现网大规模使用：Meta 刚完成全网 400ZR+ → 800ZR+ 升级，逐站点进行，代际互通是唯一可行前提（现网）〔T06 13:06〕；Meta 要求 400ZR⇄800ZR⇄1600ZR 代际互通、开放线路系统、C+L 满填、DC 与骨干共用光模块〔P147 p29–p33〕。两端各"10,000s of 800G ZR"（自报）〔P247 p13〕。Cisco 引 ACG Research：ZR+ 直插路由器相对转发器方案能耗 -90%、空间 >-65%、CAPEX -66%（引用）〔P247 p22〕。
- 光保护是节省端口的主要手段：Meta 称光链路保护多数情况下可让终端 IP 端口和转发器数量减半（自报）〔T06 14:26〕〔T01 09:30〕；Meta BAG 容量规则写明"无光保护时 BAG-to-BAG 容量 = (B + buffer) × 2"〔P424 p12〕，两者口径吻合。Ciena 给出三种实现：N+1 光保护 + 路由器内 ZR+（光层先于包层倒换），以及 active-active 由包层倒换、用外置转发器（插件够不到的距离或路由器改用 CPO 时）〔T02 06:54〕。
- 多 rail 线路系统：20 Pb/s 用例按传统线路系统需 22 个放大小屋，Hyper-Rail 只需 1 个，128 rails/机架 vs 4 rails/机架，密度 32 倍（自报，看图）〔P138 p10〕〔T02 11:59〕；Cisco Open Transport 3000 相对 NCS1010 功耗 -75%、空间 -80%，每 4×C+L 轨 350 W，每机柜 12 kW 内 128 条 C+L 轨（自报）〔P247 p23〕。转写里 Cisco 说 NCS1010 做 C+L 时 7 条线路占满一架〔T01 16:26〕。运维单位从"开一个波长"变成"开一整条线路"〔T01 17:28〕。
- FST：Ciena 51.2T C&L 概念为 4 个 8 通道服务模块、每模块 8×1.6T modem、客户侧 6.4T CPO/NPO（概念）〔P138 p12〕〔P447 p13〕；Alibaba 为 C 波段 4.8 THz、8 个固定波长 DFB/模块（ELSFP）、20 dBm 通道功率、每纤 25.6 Tb/s（自报）〔P429 p13〕〔T04 37:06〕。FST 可靠性尚无定案，Ciena 给的选项是拆成 4 个现场可换模块或模块内 N:1 保护〔T02 21:27〕。

**判断3：长 RTT 下的缓冲策略出现明确分歧，且分歧在 Meta 内部也存在：Broadcom/Arista 用仿真主张 ≥1.5×BDP 的分层深缓冲；Meta RBB 用浅缓冲 + 自研 GLIDE 在 650 km 跨度现网运行；Meta BAG 则选 J3 级深缓冲。差别来自流量类型与无损机制不同。**
- 深缓冲论证（仿真）：Broadcom 算例 800GE 在途数据 5 km/5 MB、100 km/100 MB、1,000 km/1 GB〔P147 p46〕〔T06 24:42〕；缓冲 ≥1.5×BDP 时 FCT 开销约 3–8%、重传约 0%；降到 0.1×BDP 时 500/150/50 MB 流 FCT 开销 20.6%/24.9%/31.5%，重传 23.4%/31.2%/55.1%（仿真，看图）〔P416 p9〕〔P147 p49〕；100T 交换机按 1.5×BDP 需 10 km ~1.9 GB、30 km ~5.6 GB、100 km ~18.8 GB〔P416 p10〕〔P147 p51〕。Arista 称现网分层为楼内浅缓冲、楼间 <10 km 浅缓冲轻过订、区域间 10 km+ HBM 深缓冲（自报）〔P416 p4〕。
- 浅缓冲现网（Meta RBB）：Ring 带宽约为 EBB 的 10 倍，只有 DC 级密度设备能满足每瓦要求，"浅缓冲是继承的，不是选择的"；GLIDE 在 5 ms 单向时延下达到 70% 链路利用率目标，常态只占约 7% 缓冲，4.5:1 incast 才填满 32–53 MB（实测，看图）〔P425 p5〕〔P425 p6〕。Meta 的时间线也显示了这个转向：2025.12 Rings 按深缓冲设计，2026.02 改为浅缓冲 + FBOSS，2026.07 首个 RBB 站点〔P425 p10〕。
- 深缓冲现网（Meta BAG）：BAG 承载跨站点 RoCEv2 后端流量，选"深缓冲、信用转发 ASIC（J3 Class）"以获得更大 headroom 支撑长距无损，并用 FADT 多 profile 按距离分配 headroom〔P424 p9〕〔P424 p10〕。
- 机制：RBB 承载存储读、AI 与非 AI 混合流量，靠 ECN 让发送端退避，缓冲只吸收突发；BAG 承载训练 AllReduce 的无损 RoCEv2，headroom 要覆盖一个 RTT 的在途数据，所以随距离线性涨。Broadcom 的仿真条件是 2:1 过订、包喷洒 + NSCC/RCCC〔P416 p8〕，与 RBB 的流量模型不同。两组结论目前不能直接互相否定。

**判断4：反应式拥塞信号的下限是一个 RTT，而 scale-across 中许多同步流短于一个 RTT；业界在三处同时补：交换机直接回送发送端（BTS）、长距传输参数放大（MetaRoCE）、物理层"可证无损"与光层劣化预警。它们都还没有公开的现网量化结果。**
- 问题定义：Broadcom 的参考网络是两个低 RTT 域（本地/远端 DC）夹一个高 RTT DCI 域，现有 CC 按单一 base RTT 设计〔P146 p3〕〔T05 03:48〕；PFC、ECN、CSIG、trimming 都是前向信号，要接收端反射，最快一个 RTT，而同步训练中许多流比一个 RTT 还短〔T05 07:40〕。ECN 仅 1 bit，UEC 新发布的 CSIG 约 10 bit（口述，未核对 PDF）〔T05 06:44〕。
- BTS：由拥塞点/DCI 入口交换机直接向发送端回送带元数据的截断包，看图约 10 µs vs 端到端约 1,000 µs〔P146 p6〕；设计约束为不改传输头和转发头、交换机无状态、控制流量 ≤约 1%〔P146 p7〕〔T05 12:50〕。仿真"显著改善 CC 收敛"但无数值（引用）〔T05 15:38〕；UEC 已有 BTS 工作组，OCP SAI 有配套 PR #2349〔P146〕〔T05 16:04〕。讲者自列多跳通知、重复通知、限速归属、多 RTT 域 CC 适配四个未解问题〔T05 14:00〕。
- 传输层：MetaRoCE 把 scale-across 当作同一传输的长 RTT 场景，示例 RTT 1.5 ms，Max Cwnd 3,500–7,000，Max Path 约 30–50（scale-out 为 RTT 5–15 µs、Cwnd ~75）（自报）〔P296 p9〕；只依赖商用交换机的 ECN + ECMP，不需 trimming/INT〔P296 p4〕。Google 把"long-haul RDMA 后端"和"CSIG 扩展到亚 RTT CC"列为 Virgo 下一步〔P130 p10〕。
- 物理层与光层：Ciena 指出现有相干 FEC 为容忍丢包的业务设计，呼吁 OCP 标准化"可证无损"物理层，示例目标 post-FEC BER 1e-24（提议）〔P138 p15〕〔T02 17:18〕。Alibaba LD/RD：光模块检测 pre-FEC BER 超过门限后向远端注入 RD，同时通知本地交换机把该路径移出 ECMP 组，称可零丢包切换（自报，无测试数据）〔P429 p13〕〔T04 37:42〕。Microsoft 列出 OSP 光纤市场可用性约 97.7%、link flap 与突发误码，"单次故障即暂停训练"〔P147 p42〕。

**判断5：SRv6 正在成为 scale-out、DCI、区域骨干共用的路径控制机制，配套是 SONiC/FBOSS + SAI 开放栈向 DCI 和光传输层延伸。采用理由各不相同，不是单一技术优势驱动。**
- Meta RBB：已大规模运行 MPLS SR TE 仍改用 SRv6，理由是 Olympic QoS 需要 6 类严格优先级，MPLS TC 3 bit 只能编 4 类，IPv6 TC 8 bit 能编全部 6 类〔P425 p7〕；RBB 64 个并行平面，每平面一个控制器，每 30 秒用 5 个调用编程全部交换机（自报）〔P425 p4〕〔P425 p9〕；首批站点基于 SAI + Cisco Silicon One，设计到量产 5 个月，之后 3 个月完成长途与 TE/SDN 控制器量产（现网）〔P425 p10〕〔P244 p16〕。
- Alibaba：DCI 拓扑更不对称、容量更稀缺、时延更敏感，TE 是必需（Cisco 观点）〔P429 p2〕〔T04 23:06〕；scale-across 专用 eCore 用 64×800G 盒子、起步即 800G，现场测试发现长途 100G 链路易哈希碰撞〔P429 p11〕〔T04 33:29〕〔T04 34:42〕；per-job TE 用 RoCE BTH 头 4 个保留位打标，边缘 eSR 导入对应 SRv6 策略（自报，注 P200/Q4D 支持）〔P429 p12〕〔T04 35:19〕。
- OpenAI：后端 scale-out 用 SRv6 源路由 + MRC，GPU 到 GPU 4 跳装进单个 IPv6 DA 的 6 个 uSID；生产中一台 T1 静默黑洞，75K GPU 作业约 25% QP 受影响、约 580K 包被丢，MRC 剔除路径后恢复（现网）〔P422 p13〕〔T04 10:33〕〔T04 13:05〕。OpenAI 同时说明 MRC 也支持基于熵的 ECMP，SRv6 只是可选方式之一〔T04 17:29〕。
- 光传输层开放化：Alibaba 推 SONiC for OTN，SAI OTN Phase 1（OA/VOA）已合并，Phase 2 做完整开放线路系统（OCM、OTDR、WSS、APS、OSC），Phase 3 计划做 Transponder（自报）〔P412 p10〕；SAI 范围已扩到 Packet ASIC、DASH、OCS、OTN〔P412 p9〕。

---

## 1. 需求与架构

### 1.1 需求数字

| 类别 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| 训练规模 | 训练最大模型 GPU：GPT-2 100+ → xAI Colossus 200K+ | 引用 NVIDIA | 〔P247 p2〕〔T01 00:03〕 |
| 算力增速 | 训练算力约每 5 个月翻倍 | 引用 Stanford HAI 2025 AI Index | 〔P247 p2〕〔T01 00:23〕 |
| 站点规模 | 2026 上半年最大站点约 770K H100 等效/4 栋、约 680K/16 栋、约 600K/11 栋 | 引用 Epoch AI，看图 | 〔P247 p3〕 |
| 单站电力 | 传统单 DC 50–300 MW；下一代训练集群 1 到 5+ GW；并网 3–7 年 | 自报 | 〔P147 p40〕 |
| Meta 集群 | Prometheus 1 GW+；Prometheus + Hyperion 未来几年 5 GW | 自报 | 〔P364 p20〕〔P424 p4〕 |
| Meta 集群演进 | 128 → 2K → 4K → 8K → 24K（单楼，2022–23）→ 129K（多楼，2024）→ 多区域（2025+） | 看图 | 〔P244 p4〕 |
| Prometheus 结构 | 每 Region 图示 4 个 20k GPU 块，Region 经 BAG 连接，5 km/10 km，示意扩到 100 km；p3 航拍标注楼间距 321–3,800 m | 看图，示意；合计 GPU 数存疑 | 〔P364 p3–p7〕 |
| 区域容量比 | 一对训练园区间容量 ≈ 2020 年前后前端区域的 14 倍；scale-across 过订 >8:1 | 看图；过订引用 ScaleAcross Explorer（Harvard/Meta 2026） | 〔P138 p6〕〔T02 05:20〕 |
| 流量结构 | DC 间同步流量约比用户流量大一个数量级；GW 级集群 DC-DC 流量 2026 年（预测）首次出现且高于同步流量 | 自报；看图无刻度 | 〔T06 10:58〕〔P147 p21〕 |
| 楼间带宽（Google） | 数十到数百 Pb/s（10,000–100,000 Tb/s），约 2×(6,250–62,500) 个 1.6T OSFP；平均光纤距离 <2 km | 自报，研究设计 | 〔P147 p6〕〔T06 02:34〕 |
| 系统容量（Ciena） | 20 Pb/s 用例：数百对光纤，每纤对 64×800G C+L | 自报 | 〔P138 p9〕〔P447 p7〕 |
| Meta 端口量 | >10 km 两端各 "10,000s of 800G ZR" | 自报 | 〔P247 p13〕 |
| 光纤总量 | DC 内 >10M 根光纤，DC 间 >4M | 引用 Meta | 〔P273 p3〕 |
| 广域推理需求 | 70B MHA、4K 上下文、40 ms TTFT 传 10.74 GB KV 需 2,147 Gbps，训练假设 5 Gbps，相差 429× | 建模 | 〔P270 p11〕 |
| 网络能耗占比 | 网络约占总功耗 10–15% | 自报估算；已有报告记有 10–12% 转写，存疑 | 〔T06 19:55〕 |

### 1.2 距离/规模分层各家口径

| 机构 | 分层 | 判据 | 索引 |
|---|---|---|---|
| Meta（面板/Cisco 联讲） | <3 km FR；<10 km LR；10 km+ 800ZR+ + DWDM；RBB 覆盖 1/5/10 ms RTT，scale-across 有时 >100 km | 光模块能力 + RTT | 〔P147 p25〕〔P247 p12〕〔T01 10:02〕 |
| Meta BAG | FR4 ≤3 km；LR4 ≤10 km；ZR+ ≤1,000 km | 光模块 | 〔P424 p10〕 |
| Meta Keynote | 5 km / 10 km / 100 km 三层扩展 | 示意 | 〔P364 p5〕 |
| Meta RBB | Ring 按 1/5/10 ms RTT 分档；800G-ZR+ 浅缓冲跨度到 650 km | RTT | 〔P425 p4〕〔P425 p5〕 |
| Cisco/Meta | ILA-free 120–150 km；带 ILA 500 km+ | 是否需 ILA | 〔P247 p13〕 |
| Ciena | IMDD ≤约 10 km；相干每跨约 120 km、加 ILA 1,000 km+；near <150 km、far >150 km | 是否需 ILA | 〔P138 p5〕〔P138 p7〕 |
| Ciena（Frank Chang） | Campus 10–20 km；Metro 100 km；Backbone 2,000 km+；Submarine 10,000 km+ | 应用场景 | 〔P447 p2〕 |
| Google | 园区级楼间互连 ≤约 2 km，个别更长；与几十到几百公里的 scale-across 区分 | 园区直径 | 〔P147 p6〕〔T06 02:34〕 |
| Microsoft | IMDD 几米到 2 km；LR 到 10 km；相干覆盖几十 km；ZR 100–120 km；ZR+ 数千 km；另一张图：前端 <2 km、Scale-out <1 km、Scale-up <50 m | 光学方案 | 〔T06 22:00〕〔P147 p43〕 |
| Broadcom/Arista | Scale-up <30 m；Scale-out >1K GPU；Scale-across 100+ km 路由城域/区域 WAN | 拓扑域 | 〔P146 p2〕 |
| Broadcom（CSG） | scale-across 距离约 km 级，通常有收敛比，用大缓冲交换机 | 拓扑域 | 〔P134 p18〕 |
| NTT/IOWN | Scale-Across / Sync-Across / Reach-Across 三种跨域模式；PoC 40 km 实际、500 km 仿真 | 负载类型 | 〔P158 p2〕〔P158 p4〕 |

口径差异：Meta 用光模块能力和 RTT 划分，Ciena 用是否需要 ILA，Google 用园区直径，Broadcom 用拓扑域。Ciena 提议把"连续地块园区"和 scale-across 定义捐给 OCP 标准化〔P138 p16〕〔T02 18:18〕，目前尚无统一定义。

### 1.3 架构演进要点

1. **区域即集群（Meta Ring/RBB）**：把 1/5/10 ms RTT 内的多个 region 编成 Ring，存储/支撑服务放一个区域、算力放另一区域，"副本变成算力"，本地读变成骨干流量；首个试点 region 对释放"数个 MW"基线功率（自报，未给精确值）〔P425 p3〕〔P247 p11〕〔T01 06:23〕。RBB 基于 FBOSS，仍接 EBB，Ring 内容量为 Ring 间 10 倍〔P247 p11〕〔T01 07:52〕。Meta 由 EBB 连接 23 个 DC region（北美 19、欧洲 3、亚洲 1）〔P247 p8〕。
2. **跨站后端 L3 汇聚（Meta BAG）**：BAG 是集中式 L3 super-spine，把多个 L2 fabric（DSF/NSF）连成一个跨自有与租用站点的集群，全程标准以太网〔P424 p3〕〔P424 p5〕。NSF 每 L2 最多约 21K GPU，跨 L2 过订约 5:1（看图 4.98:1），BAG 52 个平面〔P424 p6〕。站点间 hub & spoke（链路 O(N)），按平面一对一 N×800G，STSW 在 BAG 平面上形成 DLB 组，RTSW 端到端负载感知喷洒〔P424 p7〕〔P424 p8〕。WECMP 感知 L2 内部故障调整比例〔P424 p11〕。模型副本放在 L2 内，跨副本 DP 用 AllReduce Ring 走 BAG，BAG 容量由此反推〔P424 p12〕。
3. **专用网络 + 单栈（Alibaba eCore）**：按业务复制多张专用 eCore（AI Scale Across、Peering、集团、公有云、金融），爆炸半径 O(10)；单租户、IPv6+SRv6、无 overlay、无复杂 QoS；scale-across eCore 带 Collapsed Core 层、X16 并行（自报）〔P429 p9–p11〕〔T04 29:38〕。2021 年决定用 SRv6 + Silicon One + SONiC 建 eCore，2023 年开始部署〔T04 23:41〕。
4. **园区级 OCS 化（Google 研究设计）**：Virgo scale-out fabric 限单楼，跨楼需求来自楼宇面积或功率预算；多楼用 OCS 替代电交换园区 spine，楼间用 1.6T Coherent-Lite，被动复用把多端口合到一对纤；讲者声明为研究设计、非现网或承诺〔P147 p5–p11〕〔T06 00:48〕〔T06 04:11〕。
5. **云边界外扩（Microsoft–NeoCloud）**：超大云租用 NeoCloud GPU、数据和服务留在云内，需要"服务可达性的 DCI"；Tier0-Edge 做 underlay/overlay 拼接，256K VXLAN 隧道下一跳、2,048 路隧道 ECMP、每 VNET 2K+ BGP 会话，Edge 与 NeoCloud Spine 间为 MACsec 长距 400/800GbE（自报）〔P423 p2〕〔P423 p4〕〔P423 p5〕。
6. **超大规模邻近与 APN（NTT/IOWN）**：Hub-and-Optical-Spoke 拓扑；训练数据加载与计算流水化后，40 km 训练时间 +1.9%（357→364 s/epoch），100 km 内低于 +10%，100 km 吞吐保留 94%（实验）〔P158 p6〕〔P159 p12〕。1Finity 原型 ~100G 在 180 km 内稳定约 90–93 Gbps（实验）〔P158 p19〕。这一支偏推理和企业场景，规模远小于超大规模训练。

---

## 2. 技术路线对比

| 路线 | 代表方案/厂商 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| 灰光 IMDD（园区） | Meta FR/LR；Linktel DMD-CWDM | Meta <3 km FR、<10 km LR；DMD：800G 2LR4+ 20 km、1.6T 2FR4 10 km，无光损耗 | Meta 现网；DMD Beta/Alpha | 〔P147 p25〕〔P254 p4〕 |
| Coherent-Lite（园区 2 km+） | Google；OIF 1.6T-CL | O-band，相对 IMDD 4 倍频谱效率，2 nm DSP，低时延 FEC；IMDD 在 400G/lane 跨 2 km 以上受色散限制、WDM 约 16 波到顶 | OIF 立项，无现成产品 | 〔P147 p9–p10〕〔T06 05:21〕〔T06 06:15〕 |
| 800G 相干可插拔（ZR/ZR+） | Meta 800ZR+；Cisco；Ciena WaveLogic | Meta 全网 400ZR+→800ZR+ 升级完成；800 ZR/ZR+ 约 25–30 W | 现网 | 〔T06 13:06〕〔P447 p8〕 |
| 1600ZR/ZR+ | OIF 1600ZR；Cisco 1600G ZR+ | 1600 ZR/ZR+ OSFP（2027）约 33–42 W；要求与 400/800ZR 代际互通 | 标准制定中，2027 | 〔P447 p8〕〔P147 p29〕〔P247 p20〕 |
| 光保护 + 可插拔 | Meta；Ciena 模式①② | 多数情况下 IP 端口与转发器减半；光层先于包层倒换 | 现网 | 〔T06 14:26〕〔T02 06:54〕 |
| 多 rail 线路系统 | Ciena RLS Hyper-Rail；Cisco Open Transport 3000 | 22 hut→1 hut，128 rails/架；功耗 -75%，空间 -80% | 接近 GA | 〔P138 p10〕〔P247 p23〕〔T02 12:44〕 |
| 全谱转发器 FST | Ciena 51.2T C&L 概念；Alibaba 25.6T C 波段 | Ciena 4×8×1.6T，客户侧 6.4T CPO/NPO；Alibaba 8 DFB/模块、20 dBm、4.8 THz | 概念 / 早期 | 〔P138 p12〕〔P429 p13〕 |
| 高性能转发器 | Ciena WaveLogic 6 Extreme | 城域 76.8 Tb/s（48×1.6T，200 GHz）vs 可插拔 51.2 Tb/s（64×800G），+50% | 现网产品 | 〔P447 p6〕 |
| 液冷高密可插拔 XPO | Ciena/TeraHop/XPO MSA | 12.8T，8×XPO=102.4T，Linear/CL/ZR 三种模块；12.8T XPO-FRO 约 200 W | MSA Rel 1.0（2026-07-31） | 〔P447 p11〕〔P441 p4〕〔P441 p7〕 |
| 深缓冲路由/交换 | Broadcom J3/Jericho 4 + HBM；Cisco P200；Arista | 1.5×BDP；P200 8223 51.2T、64×800G、3RU；HBM 最多 8 GB | 现网产品 | 〔P416 p4〕〔P423 p4〕〔P247 p20〕 |
| 浅缓冲 + ECN | Meta RBB（FBOSS + Silicon One + GLIDE） | 650 km 跨度；70% 利用率、~7% 缓冲 | 现网（2026.07 首站） | 〔P425 p5–p6〕〔P425 p10〕 |
| 亚 RTT 反馈 BTS | Broadcom/Arista；UEC BTS WG | ~10 µs vs ~1,000 µs；控制流量 ≤1% | 规范编写中 | 〔P146 p6–p7〕〔T05 16:04〕 |
| 多路径 RDMA 长距 | MetaRoCE；MRC | scale-across Cwnd 3,500–7,000；MRC 微秒级重路由 | MetaRoCE 8 月发布开源；MRC 现网 | 〔P296 p9〕〔P122 p8〕 |
| SRv6 TE | Meta RBB；Alibaba eCore；OpenAI 后端 | 6 uSID/DA；BSID 让老 NIC 用 2 条微指令控制全程 | 现网 | 〔P425 p8〕〔T04 25:37〕〔P422 p4〕 |
| LISP 控制面 | Celestica | 端点标识与定位解耦，亚微秒收敛（主张） | 提案 | 〔P161 p12〕〔P161 p14〕 |
| 开放光传输栈 | Alibaba SONiC for OTN；OCP SAI OTN | Phase 1 已合并，Phase 2 开放线路系统 | 进行中 | 〔P412 p10〕 |
| OCS（园区/区域） | Google（研究）；Oracle/Lumentum | 1,000 台 OCS 1310 nm 插损中位约 1.2–1.4 dB；ZR/ZR+ IL 预算 11+ dB | Google 研究；Oracle 讲 scale-out 为主 | 〔P430 p12〕〔T02 16:09〕 |
| 多芯光纤 MCF | Sumitomo；SDM4 MCF MSA | 4 芯 125 µm 包层；6,912 芯缆 OD ~37 mm vs ~13 mm；MSA Rel 1.0 2026-09-17 | DC 内为主，未标准化到 DCI | 〔P316 p8〕〔P441 p18〕 |
| 空芯光纤 HCF | — | 本届 OCP 素材未出现 | — | — |

---

## 3. 关键数据表

### 3.1 能效与功耗

| 对象 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| 传统相干转发器 | >1,000 pJ/bit，>1,000 km | 自报（Microsoft） | 〔P147 p41〕 |
| DCI IP over DWDM（IMDD PAM4、400ZR） | 45–55 pJ/bit，10–120 km | 自报（Microsoft） | 〔P147 p41〕 |
| FRO / LRO / LPO / NPO / CPO | 18–25 / 10–18 / 7–10 / 5–8 / 1–5 pJ/bit | 自报（Microsoft） | 〔P147 p41〕 |
| 长途 EDFA/WDM 系统 | 数千 pJ/bit 级 | 口述估算 | 〔T06 20:25〕 |
| 400ZR QSFP-DD / 800ZR/ZR+ / 1600ZR/ZR+ OSFP | 约 17 W / 25–30 W / 33–42 W（2027） | 看图，近似 | 〔P447 p8〕 |
| 相干 vs IMDD | 功耗差随工艺缩小，1.6T 及以后与全重定时 IMDD 基本持平 | 自报（Google） | 〔T06 06:50〕 |
| ZR+ 直插 vs 转发器 | 能耗 -90%，空间 >-65%，CAPEX -66%；TCO 省 40–60% | 引用 ACG Research | 〔P247 p22〕 |
| 多 rail OLS | 每 4×C+L 轨 350 W；12 kW/机柜 128 条；功耗 -75% | 自报（Cisco） | 〔P247 p23〕 |
| Hyper-Rail | 单机箱密度 16 倍、功耗 -75%；满机架密度 32 倍 | 自报（Ciena） | 〔T02 12:44〕〔P138 p10〕 |
| 200G 链路（DAC / OCI / DR LRO） | 7 / 7 / 23 pJ/bit，2 m / 500 m / 500 m | 自报（Broadcom） | 〔P366 p22〕 |
| Open CPX NPO | 约 5.5 pJ/b（含内置激光） | 自报（TeraHop） | 〔P441 p14〕 |

注：Microsoft 表中 400ZR 与 IMDD PAM4 合并给一个区间，且未写模块形态与距离对应关系，不能直接与 Ciena 的瓦数换算。

### 3.2 缓冲、BDP 与 RTT

| 对象 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| 800GE 在途数据 | 5 km 5 MB；100 km 100 MB；1,000 km 1 GB | 计算 | 〔P147 p46〕 |
| 10 km 单端口 | 800 Gb/s、RTT 100 µs → BDP 10 MB；固定硬件实际 200 MB/端口；HBM 最多 8.0 GB | 自报 | 〔P416 p4〕 |
| 1.5×BDP 阈值 | FCT 开销 ~3–8%，重传 ~0%；10/30/100 km、NSCC/RCCC 均成立 | 仿真 | 〔P416 p9〕〔P147 p49〕 |
| 0.1×BDP | FCT 开销 20.6%/24.9%/31.5%，重传 23.4%/31.2%/55.1%（500/150/50 MB） | 仿真，看图 | 〔P416 p9〕 |
| 100T 交换机总缓冲 | 10 km ~1.9 GB；30 km ~5.6 GB；100 km ~18.8 GB | 仿真推算 | 〔P416 p10〕〔P147 p51〕 |
| Meta RBB 浅缓冲 | 5 ms 单向；70% 利用率；~7% 缓冲；4.5:1 incast 填满 32–53 MB | 实测，看图 | 〔P425 p6〕 |
| Meta Ring RTT | 1 / 5 / 10 ms | 自报 | 〔P425 p4〕 |
| MetaRoCE | scale-out RTT 5–15 µs、Cwnd ~75、Path ~12；scale-across RTT 示例 1.5 ms、Cwnd 3,500–7,000、Path ~30–50 | 自报 | 〔P296 p9〕 |
| BTS 通知时延 | BTS ~10 µs vs 端到端 ~1,000 µs（对数坐标） | 看图 | 〔P146 p6〕 |
| MRC 恢复 | T1 黑洞：检测与恢复约一个 RTT 量级，告警晚于恢复 | 现网 | 〔T04 13:05〕〔P422 p13〕 |
| 交换机其他要求 | 数万 ECMP 组、每组上千成员；µs 级故障反应；百万级路由；线速 MACsec | 自报（Broadcom） | 〔P147 p50〕〔T06 33:05〕 |

### 3.3 光层容量与密度

| 对象 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| IMDD vs 相干 | O-band IMDD 每纤单 Tb/s 级、2 bits/symbol；C+L 相干每纤数十 Tb/s、DP-16QAM 8 bits/symbol | 自报 | 〔P138 p5〕 |
| 逐波满纤 | 每纤对两端 128×400G 或 64×800G 可插拔 | 自报 | 〔P138 p11〕〔T02 13:32〕 |
| 单纤 1.6T 合波 | 一根光纤合 32 个 1.6T | 转写存疑（"32 1.60 60"） | 〔T02 04:42〕 |
| Alibaba FST | 每纤 25.6 Tb/s，C 波段 4.8 THz，32 波 | 自报；25.6T 只见于 PDF p13 结构图标注 | 〔P429 p13〕〔T04 37:06〕 |
| Ciena 海缆 | Tasman Express 2,250 km：WL6 Extreme 27 Tb/s vs WL6 Nano 23.2 Tb/s | 自报/现网 | 〔P447 p5〕 |
| Nokia 平台 | 800 Gb/s 相干路由，Super-C + Super-L 扩展频谱（原文"11.1 GHz"，存疑） | 自报 | 〔P270 p9〕 |
| 每柜光纤数 | Hopper ~576f BE → GB200 2,308f → Rubin 4,616f → Feynman 18,464 芯 | 自报/预测 | 〔P316 p3〕 |
| MCF 光缆 | 6,912 芯：单芯 OD ~37 mm（1,075 mm²）vs 4 芯 MCF ~13 mm（133 mm²），管道省 60–80% | 自报 | 〔P316 p8〕 |
| MCF 实验 | 单纤 19 芯 26 Pb/s（日本实验室，无条件） | 实验，转写 | 〔T03 07:32〕 |
| MCF 成本 | 4 芯收发器约为单芯 3–5 倍，光缆倍数相近 | 自报 | 〔T03 11:49〕 |

### 3.4 可靠性与运维

| 对象 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| GB200 中断率 | GPU-1 约 230 → 约 4–5 次/8K GPU/天，趋势 -5.5%/周；GPU-2 -5.9%/周；目标 2.0 | 看图，实测 + 外推 | 〔P364 p15〕 |
| OSP 光纤 | 市场可用性约 97.7%；子弹、箭、老鼠破坏实例 | 自报/现网案例 | 〔P147 p42〕〔T06 21:33〕 |
| T1 静默黑洞 | 75K GPU 作业，~25% QP 受影响，~580K 包丢失；转写为"about a million"，以 PDF 为准 | 现网 | 〔P422 p13〕〔T04 13:05〕 |
| 容错 | PAFT 把重启限制在小集群 | 自报 | 〔P244 p14〕 |
| 硅光可靠性 | 出货 >25M 硅光收发器，PIC >100B 器件小时，FIT <0.01 | 自报 | 〔P441 p16〕 |
| OCS 运维 | Day 0/1/2+ 零接触，"任一阶段需要 console 就不算 zero-touch"；成对图案化端口做并行验证 | 自报 | 〔P430 p5〕〔P430 p8〕 |

---

## 4. 厂商与客户态势

### 4.1 超大规模用户

- **Meta**：本方向信息最完整的用户。三层结构同时在跑：EBB（全球、深缓冲）、RBB（区域、浅缓冲、SRv6 TE、64 平面）、BAG（跨站后端、深缓冲 J3、hub & spoke）〔P425 p4〕〔P424 p7–p9〕。光学上坚持标准化可插拔：OIF 400ZR → OpenROADM/OpenZR+ 400G → 800G 由 Meta 牵头，约 4–5 年前开始〔T01 17:28〕；要求 1600ZR 代际互通、开放线路系统、C+L 满填、光模块可在 DC 与骨干、项目之间调配〔P147 p29–p33〕〔T06 13:36〕。传输层推 MetaRoCE（8 月发布，AMD Pensando 已支持，NVIDIA 合作中，开源两份软件实现）〔P244 p23–p24〕〔P419 p16〕。长期目标是算力跨区域乃至跨大洲协同〔T06 15:20〕。
- **Google**：讲的是园区级（≤约 2 km）楼间 scale-out，不是长距 scale-across；路线是 OCS + 1.6T Coherent-Lite，声明为研究设计〔P147 p5–p11〕〔T06 00:48〕。Virgo 下一步列出 long-haul RDMA 后端与亚 RTT CC〔P130 p10〕。
- **Microsoft**：立论在电力（1 到 5+ GW、并网 3–7 年）与能效（pJ/bit 表）〔P147 p40–p41〕；主张光模块 SKU 收敛（"Less is more"）〔P147 p44〕〔T06 23:58〕。另一条线是与 NeoCloud 的高容量互连（Tier0-Edge）〔P423 p2〕；Fairwater 多平面设计最多 524,288 GPU（引用）〔P422 p9〕。
- **OpenAI**：后端 SRv6 源路由 + MRC 现网，生产事件数据可用〔P422 p13〕；与 Microsoft Fairwater 合作，单 DC 有望扩到 50 万 GPU（自报/预测）〔T04 06:47〕。本方向未见 OpenAI 讲跨区域训练本身。
- **Alibaba**：scale-across 专用 eCore（64×800G 起步），SRv6 per-job TE（BTH 打标），FST 25.6T/纤，LD/RD 光层预警，SONiC for OTN〔P429 p11–p13〕〔P412 p10〕。观点是 scale-across 为 token 性能服务（TTFT、TPOT、TPS 与成本）〔T04 29:38〕。
- **Oracle OCI**：本方向只在 OCS 零接触运维（与 Lumentum）中出现，讲 scale-out 为主、兼及 DC 间〔P430 p2〕。
- **AWS**：本方向素材未出现。
- **NTT/IOWN**：APN 全光网上的跨站训练/推理 PoC，提议 OCP 形成 Scale-Across Endpoint Profile 与 OpenAPN NIC 规范〔P158 p20〕〔P159 p16〕。Lightstorm（与 Nokia 同场）将在印度三站点光纤走廊开放测量十项指标，试点窗口 2026 年底〔P270 p12〕。

### 4.2 芯片/系统/光器件厂商站位

- **Cisco**：从路由芯片（Silicon One P200，51.2T 深缓冲，固定 8223 与模块化 8800/Nexus 9800）到可插拔相干、多 rail OLS（Open Transport 3000）全栈供货；Meta RBB 首批站点用 Silicon One〔P247 p20〕〔P247 p23〕〔P425 p10〕。Filsfils 主导 SRv6 叙事，本届 OCP 有 5 场 SRv6 报告〔T04 00:03〕。展位 80 km scale-across 现场演示（自报）〔T01 20:11〕。
- **Broadcom**：两条思路并行：深缓冲（Jericho/J3 + HBM，1.5×BDP）与 BTS（UEC WG + SAI）〔P416 p3〕〔P146 p7〕；另推以太网统一 scale-up/out/across 的叙事〔P366 p4–p9〕。Thor NIC 支持 RCCC+、HyperPort〔P416 p11〕。
- **Arista**：与 Broadcom 联合发布深缓冲仿真与 BTS；主持五方面板〔P416〕〔P146〕〔P147 p1〕。
- **Ciena**：光层最积极的推动者：near/far 定义、Hyper-Rail、FST、可证无损 FEC、XPO 液冷可插拔〔P138〕〔P447〕；预计 2027 年出现"客户专属 AI 骨干网"（预测）〔T02 16:09〕。
- **Nokia**：提出 "Scale-beyond"，以 CIR（每 FLOP 可搬字节）论证广域推理带宽比训练敏感〔P270 p10–p11〕。
- **光器件**：Linktel（DMD 让 CWDM 延伸到 10–20 km）〔P254 p4〕；TeraHop（XPO、Open CPX、SDM4 MCF 三个 MSA）〔P441 p4〕；Sumitomo（MCF）〔P316〕；Eoptolink 已有 800G 4 芯收发器（转写）〔T03 09:43〕；1Finity（Photonic SmartNIC）〔P158 p19〕。
- **Celestica**：LISP 控制面提案〔P161 p12〕；同时是 Meta 102.4T 交换机 ODM〔P244 p8〕。

### 4.3 OCP 标准/MSA/工作组进展

| 项目 | 状态 | 索引 |
|---|---|---|
| UEC BTS 工作组 + OCP SAI PR #2349 | 规范编写中 | 〔P146〕〔T05 16:04〕 |
| UEC CSIG | 刚发布/在 Transport WG 标准化 | 〔T05 06:44〕〔P141 p10〕 |
| OIF 1.6T-CL | 立项 | 〔P147 p10〕〔T06 06:15〕 |
| OIF 1600ZR、400⇄800⇄1600 互通 | Meta 提要求 | 〔P147 p29〕 |
| SAI OTN Phase 1/2/3 | Phase 1 已合并（PR #2217），Phase 2 进行中 | 〔P412 p10〕 |
| SONiC OTN 工作组 | 2023-01 成立（Alibaba、Microsoft、Molex、Nokia、Cisco、Accelink） | 〔P412 p5〕 |
| OCP OCS 子项目 / SONiC OCS WG | 双周例会；Oracle 呼吁强制 OCS 生命周期 profile 与一致性测试 | 〔P430 p13–p14〕 |
| MRC 1.0（经 OCP 发布） | OpenAI、Microsoft、OCI 生产部署 | 〔P122 p4〕 |
| MetaRoCE | OCP 开源 libsoftmetaroce / dpdkmetaroce | 〔P244 p24〕 |
| Open Cluster Designs for AI | 53 家成员，V1.0 蓝图已发布 | 〔P366 p23〕 |
| SDM4 MCF MSA | 2026-03-11 成立，Rel 1.0 2026-09-17 | 〔P441 p18〕 |
| XPO MSA | Rel 1.0 2026-07-31，100+（另一稿 150+）公司 | 〔P441 p4〕〔P273 p5〕 |
| Ciena 提议 | 连续地块园区定义、scale-across 定义、无损 FEC 要求 | 〔P138 p16〕 |
| NTT 提议 | Scale-Across Endpoint Profile；OpenAPN NIC/SmartNIC | 〔P158 p20〕〔P159 p16〕 |

---

## 5. 分歧与未决问题

1. **长距缓冲：深还是浅。** Broadcom/Arista 用仿真说 ≥1.5×BDP 才能让 FCT 接近理想、零重传，浅缓冲交换机达不到〔P416 p9–p10〕〔T06 30:14〕；Meta RBB 在 650 km 跨度用浅缓冲 + GLIDE 现网运行〔P425 p5–p6〕；Meta BAG 自己又选深缓冲〔P424 p9〕。未决原因：仿真条件（2:1 过订、包喷洒、NSCC/RCCC）与 RBB 混合流量模型不同；Meta 未公开 BAG 的缓冲占用数据；Broadcom 的"与距离无关"只验证到 100 km。另外 Broadcom 自己在 T05 中指出交换芯片带宽增长快于片上内存，每代每 Gb/s 内存更少〔T05 06:18〕，这是深缓冲依赖 HBM 的原因，也是成本压力来源。
2. **反馈机制：交换机回送还是接收端授信。** T05 Q&A 中提问者主张 credit 方案，讲者认为 credit 只适合单一应用独占 scale-across 链路，客户链路多为多应用混合，需要对实时网络状态做反应〔T05 17:24〕。BTS 的仿真收益没有数值〔T05 15:38〕。MetaRoCE 走另一条路：不要 trimming/INT，只用 ECN + 多路径〔P296 p4〕。三方都没有在 >100 km 的公开现网对比。
3. **园区 2–10 km 段用什么光。** Google 主张 Coherent-Lite，理由是 IMDD 在 400G/lane 跨 2 km 以上受色散限制〔T06 05:21〕；Meta 现网 <10 km 仍用 LR 灰光（代价是大规模挖沟布纤）〔T06 12:05〕；Linktel 称 DMD 可让 CWDM 800G 到 20 km、1.6T 到 10 km，并自评在供应链、FR4 互通、成本三项优于 LAN-WDM 和 Coherent-Lite（厂商自评）〔P254 p4〕〔P254 p11〕。Microsoft 主张 SKU 收敛〔P147 p44〕。未决原因：1.6T-CL 尚无产品；DMD 为 Beta/Alpha 样品；各家园区直径不同（Google 平均 <2 km，Meta 楼 5–6 到 10 km）。
4. **"相干必需"的边界。** Ciena 按其定义称 scale-across 必需相干〔P138 p16〕〔T02 04:42〕；Google 说 1.6T 后相干与全重定时 IMDD 功耗基本持平〔T06 06:50〕，这支持相干下沉；但 Meta 的 <10 km 仍不用相干。分歧本质是 scale-across 的下限距离没有统一定义。
5. **可插拔 vs 外置转发器/FST。** Meta 强调可插拔的代际互通、可调配是转发器没有的优势〔T06 13:06〕；Ciena 同时卖两者，给出 FST 适用条件为插件够不到的距离或路由器采用 CPO 时〔T02 06:54〕，并展示转发器 +50% 频谱效率〔P447 p6〕。Alibaba 推 FST〔P429 p13〕。FST 可靠性（单点故障影响整根纤）尚无定案〔T02 21:27〕。
6. **多 rail 数字口径。** Ciena 转写说单机箱 16 倍、满机架 32 倍〔T02 12:44〕；PDF 写 32x、128 rails/rack〔P138 p10〕；Cisco 的 128 条对比单轨每机柜 32 条（即 4 倍），转写说 NCS1010 每架 7 rail〔P247 p23〕〔T01 16:26〕。三组数字的比较基准不同，不能直接横比。
7. **SRv6 的必要性与开销。** OpenAI 说 SRv6 只是 MRC 的可选路由方式，也支持熵 ECMP，封装开销需按平均包长权衡〔T04 17:29〕〔T04 19:35〕；Meta 的采用理由是 QoS 类数（与 AI 无直接关系）〔P425 p7〕；Alibaba 的理由是 per-job TE〔P429 p12〕。BSID 方案让老 NIC 只用 2 条微指令，但跨 DC spine/leaf + 5–7 跳 DCI 端到端可能需 10–12 条微指令〔T04 25:37〕。Celestica 主张 LISP 用于超低时延动态 scale-across〔P161 p12〕。尚无多方案的同场对比数据。
8. **推理会不会成为 scale-across 主负载。** Ciena 认为推理总量将大于 scale-across 训练，但更分散、更网状，产品可沿用〔T02 19:02〕；Nokia 建模推理广域带宽为训练的 429 倍（训练 5 Gbps 为假设值）〔P270 p11〕；NTT 的 PoC 偏推理和数据加载〔P158 p15〕。各方数字建立在不同假设上。
9. **多芯/空芯光纤在 scale-across 的位置。** Sumitomo 承认 scale-across 只是一句带过，主体是 DC 内布线〔T03 09:59〕；MCF 尚未标准化到 DCI，成本 3–5 倍〔T03 11:49〕〔P316 p12〕。本届 OCP 无 HCF 讲稿。

---

## 6. 判断与时间线

### 6.1 未来 12–36 个月里程碑

| 时间 | 事件 | 依据 |
|---|---|---|
| 2026 年底 | Prometheus 达到 1 GW 集群规模（已在训练多个模型） | 〔T01 05:06〕 |
| 2026-12 | Meta RBB 计划扩展（2026-10 首个 SRv6 TE 站点之后） | 〔P425 p10〕 |
| 2026 年底 | Lightstorm 印度三站点光纤走廊测量试点开放 | 〔P270 p12〕 |
| 2026H2 起 | Ciena Hyper-Rail "接近 GA" | 〔T02 12:44〕 |
| 2026–2027 | SAI OTN Phase 2（开放线路系统）、Phase 3（Transponder） | 〔P412 p10〕 |
| 2027 | 1600ZR/ZR+ OSFP，约 33–42 W | 〔P447 p8〕 |
| 2027 | Ciena 预测出现"客户专属 AI 骨干网" | 〔T02 16:09〕 |
| 2027-03 | NTT Watt-Bit/Physical AI 现场 PoC（100 km+ 远程 GPU）结束 | 〔P158 p19〕 |
| 未定 | UEC BTS 规范、OIF 1.6T-CL、OCP 无损 FEC 要求 | 〔T05 16:04〕〔T06 06:15〕〔P138 p15〕 |
| 远期 | 同步训练距离 500 → 800 → 约 1,000 km；Prometheus + Hyperion 5 GW | 〔T02 22:25〕〔P364 p20〕 |

### 6.2 对各类厂商的含义

- **设备商（路由/交换/传输）**：scale-across 交换机的规格清单已经写明：深缓冲（或至少可按距离分配 headroom）、数万 ECMP 组、µs 级故障反应、线速 MACsec、ZR 可插拔笼位〔P147 p50〕〔P424 p10〕〔P423 p4〕。但 Meta RBB 的浅缓冲先例说明，用户会为每瓦带宽放弃深缓冲，深缓冲产品的市场边界取决于流量是无损 RoCE 还是 ECN 端到端控速。线路系统竞争点从单波性能转到每机架 rail 数、放大小屋数量和开一整条线路的运维自动化〔P138 p10〕〔T01 17:28〕。开放栈（SONiC/FBOSS/SAI 到 OTN）是进入超大规模用户的门槛〔P412〕〔P425 p10〕。
- **光模块商**：800ZR+ 已是现网量产品，Meta 两端各上万只〔P247 p13〕；1600ZR 的准入条件是与 400/800ZR 代际互通〔P147 p29〕。光保护让端口需求减半〔T06 14:26〕，FST 若成熟会把一部分可插拔需求转为外置一体化设备〔P429 p13〕。园区 2–10 km 段有 LR、DMD-CWDM、Coherent-Lite 三种方案竞争，Microsoft 要求 SKU 收敛〔P147 p44〕，最终可能只留少数几种。
- **芯片商（DSP/交换芯片/NIC）**：2 nm 低功耗 DSP、低时延 FEC 是 Coherent-Lite 的前提〔P147 p10〕；可证无损 FEC（1e-24）若写入 OCP 要求，会改变相干 DSP 的 FEC 设计目标〔P138 p15〕。交换芯片侧要么做 HBM 外挂缓冲，要么支持 BTS 这类亚 RTT 信号〔P416 p3〕〔P146 p7〕。NIC 侧要支持长 RTT 下更大 cwnd 与更多路径（MetaRoCE 3,500–7,000）〔P296 p9〕、SRv6 封装〔P422 p11〕、BTH 打标〔P429 p12〕。

---

## 7. 推荐配图清单

| 图 | 内容 |
|---|---|
| 〔P364 p5〕 | Meta Prometheus 5/10/100 km 多层扩展示意 |
| 〔P364 p7〕 | 两组 Region（各 4×20k GPU）经 BAG 以 5/10 km 互连 |
| 〔P147 p25〕 | Meta 楼群 <3 km / <10 km / 10 km+ 三档光模块演进 |
| 〔P247 p13〕 | >10 km 800G ZR + 光保护开关 + MUX，ILA-free 120–150 km、带 ILA 500 km+ |
| 〔P138 p7〕 | Ciena near vs far scale-across 设计表（150 km 分界） |
| 〔P138 p6〕 | 14 倍容量对比与 >8:1 过订 |
| 〔P138 p10〕 | 20 Pb/s 网络 22 个 hut vs Hyper-Rail 1 个 hut |
| 〔P247 p23〕 | 单轨 vs 多轨 OLS 功耗/空间对比 |
| 〔P429 p13〕 | Alibaba FST 结构与 LD/RD 收敛示意 |
| 〔P138 p12〕 / 〔P447 p13〕 | Ciena 51.2T C&L FST 框图 |
| 〔P447 p8〕 | 可插拔相干功耗 2001–2027 趋势 |
| 〔P147 p41〕 | Microsoft 按距离的 pJ/bit 能效表 |
| 〔P416 p9〕 / 〔P147 p49〕 | 缓冲深度 vs FCT/重传率曲线 |
| 〔P147 p51〕 | 100T 交换机 1.5×BDP 缓冲需求：10/30/100 km 对应 1.9/5.6/18.8 GB |
| 〔P425 p6〕 | Meta GLIDE 浅缓冲：70% 链路利用、~7% 缓冲 |
| 〔P425 p4〕 | RBB/EBB 与 Ring 结构，64 平面 |
| 〔P424 p6〕 | NSF L2 fabric 与 BAG 平面拓扑及过订比 |
| 〔P146 p3〕 / 〔P146 p6〕 | 跨 DC 参考网络模型；BTS vs 端到端通知时延 |
| 〔P422 p13〕 | OpenAI T1 黑洞事件时间线（75K GPU、25% QP、580K 丢包） |
| 〔P429 p12〕 | per-job TE：Job→BTH→SRv6 策略 |
| 〔P147 p9–p10〕 | Google 1.6T Coherent-Lite vs IMDD |
| 〔P412 p10〕 | SAI OTN 三阶段 |
| 〔P316 p8〕 | 6,912 芯单芯 vs 4 芯 MCF 光缆截面 |
| 〔P364 p15〕 | GB200 中断率趋势 |

---

## 8. 与 ECOC 2026 的对照

ECOC 对照底稿：方向2（数据中心 Scale-across）。ECOC 的五条判断为：需求主体与线路系统成本、FST + 多 rail、相干向短距渗透的分界、1.6T 功耗与热、HCF。

### 8.1 一致

1. **部署单元从波长转为光纤对，多 rail + FST 是答案。** ECOC：Ciena 传统 22 机房 vs 多 rail 1 机房〔0920-am-Su2-B-02-Ciena p8〕，Huawei FST 25.6T/光纤（C96）〔0920-pm-Su4-C-03-华为 p5〕。OCP：同一组 Ciena 22 hut vs 1 hut〔P138 p10〕，Cisco 多轨 -75% 功耗〔P247 p23〕，Alibaba FST 25.6T/纤〔P429 p13〕。两边 FST 都以 C 波段 25.6T 为一档、C+L 51.2T 为一档。
2. **相干可插拔功耗曲线。** ECOC：Ciena 800ZR/ZR+ 约 25–31 W、1600 ZR/ZR+ OSFP 约 34–42 W（2027）〔0920-am-Su2-B-02-Ciena p7〕，Google 1.6T ZR++ <45 W 为风冷天花板〔0920-am-Su2-B-01-Google p7〕。OCP：同源 Ciena 图 800G 25–30 W、1600G 33–42 W〔P447 p8〕；XPO 液冷 12.8T 在两边都出现〔P447 p11〕〔0923-MF-Marvell等连拍 p29〕。
3. **2 km 以上 IMDD 受色散限制，Coherent-Lite 在 O 波段补位。** ECOC：Acacia 400G/lane 超过 2 km 需相干〔0920-pm-Su4-A-03-Acacia p5〕，Marvell 2–10 km+ O 波段 CL〔0920-pm-Su4-A-01-Marvell p5〕。OCP：Google 同样以 400G/lane 跨 2 km 为界，指向 OIF 1.6T-CL〔T06 05:21〕〔P147 p10〕。
4. **CL 需要专用低时延/强 FEC。** ECOC：Nokia 园区 FEC 目标 50–75 ns〔0920-pm-Su4-A-04-Nokia p12〕，Ciena CL BER <1E-24〔0920-pm-Su4-A-02-Ciena p5〕。OCP：Google 要求低时延 FEC〔P147 p10〕，Ciena 呼吁 1e-24 可证无损物理层〔P138 p15〕。两边 1e-24 都来自 Ciena。
5. **>10 km 用 ZR/ZR+ + 线路系统。** ECOC：OVHcloud <10 km 无需线路系统、>10 km 用 800G ZR/ZR+〔0920-am-Su1-C-00-上半场速记 p15, p16〕。OCP：Meta 10 km+ 用 800ZR+ + DWDM〔P147 p25〕。

### 8.2 OCP 新增（ECOC 判断未覆盖）

1. **包层：缓冲与长 RTT 拥塞控制。** 1.5×BDP 仿真、100 km 需 18.8 GB〔P416 p10〕；Meta 浅缓冲 650 km 现网〔P425 p5〕；BTS〔P146 p6〕。ECOC 方向2 只有 Huawei OTN-Proxy 一条协议层内容〔0920-pm-Su4-C-03-华为 p6〕。
2. **SRv6 TE 与开放软件栈。** Meta RBB、Alibaba per-job TE、OpenAI 源路由〔P425 p7〕〔P429 p12〕〔P422 p13〕；SAI OTN〔P412 p10〕。ECOC 判断中无对应内容。
3. **超大规模用户的现网部署细节。** Meta 800ZR+ 全网升级完成〔T06 13:06〕、BAG 拓扑与容量规则〔P424 p12〕、RBB 5 个月上线〔P425 p10〕。ECOC 侧需求数字多来自分析机构（Cignal AI）与厂商〔0922-MF-am-1140-CignalAI p7〕。
4. **光保护作为端口减半手段。** Meta 量化为多数情况减半〔T06 14:26〕；ECOC 判断未提光保护。
5. **电力驱动的距离外推。** Ciena 客户从 near 转 far、目标 1,000 km〔T02 22:25〕；Microsoft 并网 3–7 年〔P147 p40〕。ECOC 有同一 Microsoft 50–300 MW 引用（经 ZTE 转引）〔0923-We5-B-中兴 p4〕，但没有 near/far 的转移判断。

### 8.3 矛盾或口径不一

1. **Ring/区域骨干的归属。** ECOC 底稿把"FBOSS 新 DC 产品模糊 DCN/DCI 边界、区域 Fabric 环、环内容量为环间 10 倍"记在 OVHcloud 名下〔0920-am-Su1-C-00-上半场速记 p14, p17〕；OCP 中同样的表述出自 Meta（Ring、RBB、FBOSS、10x）〔P247 p11〕〔T01 07:52〕。FBOSS 是 Meta 的 NOS，ECOC 速记可能有讲者归属错误，需回查 ECOC 原始速记。
2. **HCF 的地位。** ECOC 把 HCF 列为第五条判断，有 Azure 427.97 km HCF 上 64×400G ZR 的实验〔0922-Tu3-H4-Azure p12, p13〕；OCP 本方向无 HCF 讲稿，超大规模用户讲 scale-across 时全部基于标准单模光纤与 C+L。两边不直接矛盾，但 OCP 现网路线里看不到 HCF。
3. **线路系统成本是主要矛盾，还是端口数是主要矛盾。** ECOC 判断1 称成本结构由线路系统决定，2030 年线路系统占 scale-across 支出 55%〔0922-MF-am-1140-CignalAI p8〕；OCP 的用户侧（Meta）优化重点是减少 ZR 和 IP 端口（光保护减半）〔T01 09:30〕，Cisco 引 ACG 的数字也是围绕可插拔替代转发器〔P247 p22〕。两种视角对应不同成本口径，未见同口径比较。
4. **多 rail 节能比例。** ECOC：Google HyperRail 约 80% 功耗下降〔0920-am-Su2-B-01-Google p5〕，Ciena FST 功耗约 -50%〔0920-pm-Su4-C-04-Ciena p3〕；OCP：Ciena Hyper-Rail 与 Cisco 多轨均为 -75%〔T02 12:44〕〔P247 p23〕。对象（FST vs 多 rail OLS）与基准不同，数字不宜混用。
5. **IMDD 能否延伸到 10–20 km。** ECOC NICT/UCLA 认为若无光域均衡，Coherent-lite 主导 2 km 以上〔0920-Su3Su4-A全场扫描 p134, p147〕；OCP Linktel 称 DMD 可让 800G CWDM 到 20 km、1.6T 到 10 km（Beta/Alpha 样品）〔P254 p4〕，且 Meta 现网 <10 km 仍用 LR〔T06 12:05〕。分歧在 200G/lane 与 400G/lane 的代际：Linktel 400G/lane 只验证到 3 km〔P254 p10〕。
6. **跨区域训练对距离的敏感度。** ECOC Huawei 称 OTN-Proxy 使吞吐与 DCI 距离（0–500 km）基本无关〔0920-pm-Su4-C-03-华为 p6〕；OCP 的 Broadcom/Arista 把距离视为核心问题，缓冲需求随距离线性增长〔P147 p46〕〔T05 03:48〕。前者是代理/终结方式绕开 RTT，后者讨论端到端 RDMA，层次不同，但结论方向相反。

---

## 附：索引对照表

| 索引 | 机构 | 题目简写 |
|---|---|---|
| P122（= P153） | Broadcom | 下一代网络标准对比（MRC vs UEC） |
| P130 | Google | Virgo 网络与"园区即计算机" |
| P134 | Broadcom | 端到端 AI 后端 fabric 设计 |
| P138 | Ciena | 从单 DC 到多区域 AI 集群：Scale Across 兴起 |
| P141 | Arista/Broadcom | 含 MRC 与 SRv6 的 AI fabric 配置 |
| P146 | Broadcom/Arista | Scale Across：前进还是后退（BTS） |
| P147 | Google/Meta/Microsoft/Broadcom/Arista | Scale-across 面板：路由与传输设备影响 |
| P158 | NTT 等 | AI Computing Continuum 用例与 PoC |
| P159 | NTT/HPE/Intel | AICC：开放 DC 生态向外延伸 |
| P161 | Celestica | 打破 DC 墙：统一 AI fabric（LISP） |
| P244 | Meta | Betting on the Network（全栈开放 AI 网络） |
| P247 | Cisco/Meta | Breaking the Walls：开放 Scale-Across |
| P254 | Linktel | 色散管理收发器 |
| P270 | Nokia/Lightstorm | AI 基础设施多维扩展 |
| P273（≈ P441） | TeraHop | 开放光互连（XPO/Open CPX/SDM4 MCF） |
| P296 | Meta/AMD | MetaRoCE：重新设计 RDMA |
| P316 | Sumitomo Electric | 多芯光纤 |
| P356 | Falqon | 量子安全网络 |
| P364 | Meta | Concrete to Code（GW 级 AI 基础设施） |
| P366 | Broadcom | 以开放创新扩展 AI 基础设施 |
| P404 | Cisco | Silicon One 上的开源 NOS |
| P412 | Alibaba | SONiC for OTN |
| P416 | Arista/Broadcom | 深缓冲：可扩展 AI 训练与推理的基础 |
| P419 | Meta | MetaRoCE 软件实现 |
| P422 | Cisco/OpenAI | Scale-out 与 Scale-across 中的 SRv6 部署 |
| P423 | Microsoft/Cisco | 超大云与 GPUaaS 间的高容量互连 |
| P424 | Meta | BAG：跨 DC 扩展 AI 基础设施 |
| P425 | Meta | SRv6 驱动的骨干网（RBB） |
| P429 | Cisco/Alibaba | AI DCI-WAN 的流量工程 |
| P430 | Oracle/Lumentum | 零接触 OCS fabric |
| P441 | TeraHop | 面向 AI 扩展的开放光连接 |
| P447 | Ciena | AI 时代的相干光 |
| T01 | Cisco/Meta | Breaking the Walls 视频（对应 P247） |
| T02 | Ciena | Rise of Scale Across 视频（对应 P138，自动字幕） |
| T03 | Sumitomo Electric | 多芯光纤视频（对应 P316） |
| T04 | Cisco/OpenAI/Alibaba | SRv6 双场视频（对应 P422、P429） |
| T05 | Broadcom/Arista | To Go Forward or Backwards 视频（对应 P146，自动字幕） |
| T06 | 五方面板 | Scale-across Networking Panel 视频（对应 P147，自动字幕） |
