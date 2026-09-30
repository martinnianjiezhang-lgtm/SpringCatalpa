---
title: "B07 · DAY1 · C1.1-Su1-Su2-楼内光网络"
tags:
  - ECOC2026
  - DAY1
---

### 0920-am-Su1-D-01-主席-开场.pdf
- 讲者/机构：Workshop 主席（姓名未见于开场页；议程页含 Andreas Gladisch/DT 等讲者名单） | 题目：Optical In-Building Networks（ECOC 2026 Workshop，9月20日 09:00–12:30，Conference room C1.1） | 类型：Workshop
- 方向归属（主/次）：主 5 固定与无线接入（FTTR/楼内光网络）；次 无
- 核心主张：
  1. 户内是流量主体，Wi-Fi 是最后一跳主体，而一致性体验并不随 FTTH/B 覆盖提升。
  2. 听众实时投票显示用户最看重可靠性而非速度。
  3. 议程分 Fixed（DT、CMCC、MaxLinear、Nokia）与 Wi-Fi（DeepSig、Huawei、Fraunhofer HHI、UPF）两组，每人15分钟+2–3分钟问答。
- 关键数据：
  - 全球数据流量 >80% 在室内产生与消费；约 70% 的最后一跳流量由 Wi-Fi 承载 [p2]
  - 每户 Wi-Fi 设备数：2020 年 13 台，2025 年 25 台，2030 年 44 台（World Broadband Association WBBA 2024）[p2]
  - 欧洲各国 Q4/2025 户内体验柱图（OpenSignal，2026年5月）：下载速率如法国 182.5 Mbps、丹麦 151.1 Mbps、土耳其 43.5 Mbps；上传如法国 135.3 Mbps；数值取自图，小字部分部分看不清 [p2]
  - 现场 slido 投票（"connecting to the Internet at home 最重要的是什么，单选"）：高可靠性 63%、高下载速率 19%、低价 13%、客服 6%、高上传速率约 0%（参与人数约16，右上角小字，不确定）[p4]
  - 全球 FTTR 市场规模预测 ~20.8% CAGR（2025–2030），美元数值看不清 [p3]
- 提到的公司/客户/产品/标准：OpenSignal、World Broadband Association、Deutsche Telekom、Maxlinear、Nokia、DeepSig、Huawei、Fraunhofer HHI、UPF；技术清单：ETH Wi-Fi Mesh、FTTO、POL、5G/FWA、mmWave、LiFi、FTTR
- 与业界对比或记录声明（SOTA/首次/record）：无 [p2]
- 推荐配图页：p2（欧洲户内宽带体验与光纤覆盖对比图）；p4（可靠性最重要的投票结果）

### 0920-am-Su1-D-02-德国电信-光能否解决室内挑战.pdf
- 讲者/机构：Andreas Gladisch / Deutsche Telekom（GROUP TECHNOLOGY） | 题目：Can optics fix the indoor challenge?（议程所列题为 "Can optics fix the indoor challenge?"，具体题目页仅见 Andreas Gladisch、September 2026） | 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入；次 无
- 核心主张：
  1. 建筑网络是接入—楼内—户内的整合点，同一户内存在运营商、住户、公用事业、物业、第三方服务多个网络与责任方。
  2. 建筑异质性体现在物理、组织、技术、时间四个维度；建筑寿命以十年计，网络以几年计，基础设施须跨多代技术。
  3. 提出关键问题：如何管理日益复杂的接入与楼内域，并建议尽早为运营商定义新角色。
- 关键数据：
  - 德国住宅楼龄（Zensus 2022）：1990年前建成 71.3%，2010年后建成 7.7%；各年代占比 <1919 13.1%、1919–49 11.8%、1950–59 10.3%、1960–69 13.1%、1970–79 13.0%、1980–89 10.1%、1990–99 12.2%、2000–09 8.9%、2010–15 3.8%、2016+ 3.8% [p4]
  - 德国住宅数量按楼内户数分类的柱图（含 13.50 Mio. 标注，具体对应类别看不清）[p3]
- 提到的公司/客户/产品/标准：Deutsche Telekom；FTTH、GPON/XGPON、FTTC+G.fast、FTTLp（Fiber to the Lamppost）+SmallCell、FTTR+SC(RAN)、Wi-Fi 2.4 GHz、5G/6G、BEP/BD/FD/OTO 楼内光纤层级 [p2, p6]
- 与业界对比或记录声明（SOTA/首次/record）：无 [p4]
- 推荐配图页：p4（德国住宅楼龄分布柱图）；p2（多住户楼内光纤入户层级示意）；p7（四维异质性）

### 0920-am-Su1-D-03-中国移动-FTTR部署与技术.pdf
- 讲者/机构：Junwei Li / CMRI（中国移动研究院） | 题目：Considerations on Deployment and Technology Development of FTTR | 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入（50G PON/FTTR）；次 无
- 核心主张：
  1. 50G PON 作为万兆光接入基础，对称系统已基本达到 Class C+ 功率预算，仍需持续提升系统性能与能力。
  2. FTTR 是万兆体验的关键，需加快 10G FTTR 与 FTTR 协同管理的研究与标准化，并与 AI、感知、IoT 能力结合。
  3. PON 将由通信导向演进到面向 Token 运营（AI-Native 50G PON+FTTR：Al-ONT/Al-ODN/Al-OLT、Al-FTTR），并提出 "PON+FTTR 算力总线"。
- 关键数据：
  - 千兆用户 >2.58 亿（占总用户 36.8%），宽带用户 6.7 亿；10G PON 端口达 3286 万（2026 H1，来源工信部）；2025 年万兆现场试验共 168 处 [p4]
  - 50G PON 功率预算：兼容 ODN Class C+ 32 dB 预算；图中标注 -25.7 dBm 与 +6.8 dBm（N1 → C+ 的箭头）[p8]
  - 3 代 PON 同端口经 WDM 共存，ONU 侧双模 Combo [p8]
  - 三频 Wi-Fi 7（2.4G/5G LB/5G HB）已成熟，支撑 3000M 宽带；理论速率：Wi-Fi 6 5.2G/160 MHz 2402 Mbps；Wi-Fi 7 MLO 2.4G+5.2G（40+160 MHz）3570 Mbps；Wi-Fi 7 MLO 5.2G+5.8G（160+80 MHz）4323 Mbps [p9]
  - 10G FTTR 物理层 Ra / Ra+：功率预算 0–18 dB / 0–21 dB；MFU 发射 1 至 5 dBm，过载 2.5 dBm，灵敏度 -19.5 / -22.5 dBm；SFU 发射 -1.5 至 2.5 dBm，过载 5 dBm，灵敏度 -20 dBm；Ra+ 支持直连与最高 1:32 分光比；PHY 指标在 CCSA 达成共识 [p9]
  - 工业 PON 需求：100 μs 确定性低时延、99.999% 可靠性；方案为 10G 通道作为注册窗口（专用激活波长）与 10G/50G 双通道保护倒换 [p10]
  - 算力总线：OLT 边缘算力，端到端 RTT 时延 <20 ms（基于 OMCI 扩展，专用 Wi-Fi 7 5.8 GHz 频段）；具身 AI 端侧算力需求"5–6 T"（文字模糊，不确定）[p16]
  - 场景需求：ToC 时延 50 ms→10 ms @99.99%，ToB 5 ms→1 ms @99.9999%；上行占比将升至 40%–50%（OCR 数据，未逐字核对）[p5]
  - RFID over FTTR 现场试验（工厂仓库）：覆盖 >1000 m²，标签 >2000 个，盘点时间由 1 天缩短到分钟级，1 人即可完成 [p17]
- 提到的公司/客户/产品/标准：China Mobile/CMRI、CCSA、ITU-T G.sup.PONcoop（中国移动联合发起）、50G PON（ITU-T G.9804）、XGS-PON、GPON、Wi-Fi 7、RFID、OMCI、MFU/SFU/OLT、瓷器博物馆场景试验（图注 Porcelain Museum）
- 与业界对比或记录声明（SOTA/首次/record）：万兆 PON 端口与千兆用户规模为国内统计数据，非技术 record [p4]
- 推荐配图页：p8（50G PON 五项技术能力要求：预算/共存/低时延/FTTR 管理/融合）；p9（三频 Wi-Fi 7 与 10G FTTR 物理层参数表）；p17（AI+FTTR+RFID 现场试验）

### 0920-am-Su1-D-04-MaxLinear-ITU-T的FTTR标准.pdf
- 讲者/机构：Marcos Martinez / MaxLinear（议程所列）；ITU-T Q3/15 | 题目：ITU-T Q3 technologies for FTTR（图中日期为 October 2018，疑为沿用旧模板，不确定） | 类型：邀请报告（标准）
- 方向归属（主/次）：主 5 固定与无线接入（FTTR 标准）；次 无
- 核心主张：
  1. FTTR 定义为可用于"轻管理、动态"环境的任意光系统，主要用例是 Wi-Fi 回传；纤缆能提供一致覆盖、低干扰、低功耗与时延控制。
  2. ITU-T Q3/15 有两种思路：mP2P（G.9930/G.p2pf，光以太网）与 P2MP（G.9940 系列 G.fin / G.Xfin，基于 xPON）。
  3. 管理通过 FMCI（OMCI 变体）与 WMCI（低时延 Wi-Fi 管理控制接口，G.9949）实现 Wi-Fi 协同。
- 关键数据：
  - 约 20% 的家庭可从有线回传获益；有线回传下 >200 Mbps 一致覆盖 [p4, p5]
  - G.9930：吞吐 1/10/25/50 Gbps（p7），另一页写"最高 10 Gbps"（p13，两页口径不一致）[p7, p13]
  - G.fin：2.5 Gbps 对称；G.Xfin：10 Gbps；AP 粒度：家庭 2–8，企业 2–32 [p8]
  - G.Xfin：PHY 已 consent，DLL 与架构在制定中，预计 2027 年出首份草案 [p12]
  - WMCI 支持：时域协同传输、功耗管理、Co-SR、协同漫游、协同 EDCA [p11]
- 提到的公司/客户/产品/标准：MaxLinear、ITU-T Q3/15、G.9930、G.9940/1/2/3、G.9945/6/7、G.9949、TR-069/TR-369、FMCI、WMCI、IEEE 802.11bq、Sparklink
- 与业界对比或记录声明（SOTA/首次/record）：无 [p12]
- 推荐配图页：p7（G.p2pf 拓扑与参数）；p8（G.fin/G.Xfin 拓扑）；p12（未来发展路线：10G、AI、ISAC、mmWave 802.11bq）

### 0920-am-Su1-D-05-Nokia-面向IoT与AI的楼内网.pdf
- 讲者/机构：Ronald Heron（Fixed Networks CTO Team，含 Rene Bonk 贡献）/ Nokia | 题目：Optimized Optical In-building Networks for Evolving AI and Wi-Fi Needs | 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入；次 无（涉及 AI 但非数据中心）
- 核心主张：
  1. 户内/楼内网络高度多样，需要定制方案：企业用 Passive Optical LAN（PON，2.5G–100G+，高扇出），住宅用 G.p2pf（2.5G–50G，低扇出）。
  2. Wi-Fi 7 需要 n×10G，推动光纤馈送 AP；光纤回传降低 Wi-Fi 噪声负载，云端家庭控制器可进一步提升 Wi-Fi 性能。
  3. AI 影响深远：FIP for AI 与 AI for FIP，功能需合理分布。
- 关键数据：
  - Wi-Fi 无处不在：1.4B 宽带联网家庭；今年 21B Wi-Fi 设备活跃；全球互联网流量 57% 经 Wi-Fi；95% 户内连接经 Wi-Fi；40%+ 宽带家庭有体验问题；70% 客服电话与 Wi-Fi 相关 [p4]
  - mmWave Wi-Fi 目标：单用户 ≥10 Gb/s、每房间 80% 覆盖；60 GHz，4×4 m 房间，2×2 MIMO（62 GHz）：信道带宽 0.32/0.64/1.28/5.12 GHz 对应吞吐约 2/3.5/4.5/10 Gb/s；10 Gbps 所需 Tx EIRP 随带宽增大下降（曲线约 29 dBm 降至约 10 dBm）；假设 150 m² 房屋、16 m² 平均房间、墙衰减 20 dB [p6]
  - 企业 Optical LAN 收益：布线与空间 -70%，节能 40%，寿命 50+ 年，TCO -50%；传统方案 180 kWh/用户/年 [p8, p9]
  - TIA TSB-162B：单 Wi-Fi AP 理论最高 45 Gbps，4×10GE Cat6 = 32 根铜线；一 AP 每 18 m×18 m；4 个 AP 需 128 根铜线，而光纤只需 4 根 [p10]
  - PON 现状：GPON 已部署超过 10 亿用户，XGS-PON 接近 1 亿用户 [p11]
  - G.9930 于 2025-10 新增 25G 与 50G；表列例如 10G BiDi 10 km 6.3 dB（下行 1320–1340 nm / 上行 1260–1280 nm）、50GBASE-LR 10 km 6.3 dB [p19]
  - Mono-optics（单纤，3 dB 分路器，10G SFP）：FP 激光器 -3 dBm @1320 nm；反射影响约 0.1 dB（RX1）/ 0.2 dB（RX2）；以太网 pre-FEC BER 阈值 5×10⁻⁵（引 M. Straub et al., Tu01.07.3, ECOC 2025）[p20]
  - MDU（8 户、96 设备）Wi-Fi 仿真：每户最优 AP 数为 2–3 个；家庭多数仅 1 个 AP，约 25% 有 2 个及以上（Nokia 数据）；结论住宅 FIP 需要 1–2 条链路 [p17]
  - 家庭固定流量（不含 FWA）预测到 2034 年：保守 1,405、中等 1,806、激进 2,791 EB/月；结论"增长渐进而非爆发"[p26]
  - AI 与电信创新周期：AI GPU 基础设施约 2–3 年，消费设备 3–5 年，企业算力约 5 年，电信光网络约 10 年 [p28]
- 提到的公司/客户/产品/标准：Nokia、Corteca（云家庭控制器，USP/TR-369、TR-181）、Google Fiber（GFiber 20 Gig + Wi-Fi 7 路由器）、G.984 GPON、G.9807 XGS-PON、25GS-PON MSA、G.9804 HSP、G.sup.VHSP、G.9930 G.p2pf、G.994x G.fin、IEEE 802.11be/bq、TIA TSB-162B、ITU-T G.902
- 与业界对比或记录声明（SOTA/首次/record）：Google Fiber 20 Gig 对称速率服务被引为"first-of-its-kind"（图中字样）[p16]
- 推荐配图页：p6（mmWave Wi-Fi 带宽-吞吐-EIRP）；p9（Optical LAN 对比与收益）；p20（Mono-optics 结构与 BER 曲线）；p26（家庭固定流量预测）

### 0920-am-Su2-D-01-DeepSig-AI原生WiFi9调制解调.pdf
- 讲者/机构：Jim Lansford / DeepSig | 题目：AI-Native modems for Wi-Fi 9（议程题为 "AI-Native modems for Wi-Fi 9"） | 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入（Wi-Fi 侧）；次 无
- 核心主张：
  1. AI/ML 在 WLAN 中目前主要用于 L2；AI-Native PHY（神经网络收发机）将替代或扩展传统估计、均衡、MCS 选择，并可能无导频运行。
  2. 下一代标准需提供：CSI/IQ 上传、基于码本的模型下发、前导修改、联合 MAC-信源-信道编码的空口钩子。
  3. 结论："The time is right to bring AI-Native technology into WLAN standards!!"
- 关键数据：
  - 5G 已验证：业界首个 AI/ML 神经接收机在现网 5G 宏网络运行（OmniPHY，O-RAN，越南），某些情况上行吞吐 2–3 倍（基于 Intel FlexRAN DU）[p5]
  - 学到的星座：1024-QAM（Rayleigh）、4096-QAM（CDL-A）；图中另有 BLER 等小字看不清 [p6]
  - 当前 AIML 工作"潜力为两位数吞吐提升"（无量化基线）[p11]
  - 802.11 AIML TIG/SC 已收集大量研究；3GPP 已有多项 Work Item/Study Item [p11]
- 提到的公司/客户/产品/标准：DeepSig OmniPHY、Intel FlexRAN、O-RAN、3GPP、IEEE 802.11 AIML TIG/SC、802.11k/u/v、MPTCP/QUIC
- 与业界对比或记录声明（SOTA/首次/record）：Industry-first AI/ML neural receiver operating in live 5G macro network [p5]
- 推荐配图页：p2（AI-Native PHY 由今日到未来的演进：ML 替换多处理块）；p5（5G 现网部署与收敛曲线）

### 0920-am-Su2-D-02-华为-智能FTTR与毫米波.pdf
- 讲者/机构：Tony Zeng（Standard Director of Optical Access）/ Huawei | 题目：Intelligent FTTR and mmWave integration for premium quality smart homes application | 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入（AI-FAN/FTTR/mmWave）；次 无
- 核心主张：
  1. 家庭业务由连接走向计算、由 APP 走向 Agent；每个家庭将有 2–5 个 Agent，需确定性网络质量，提出 AI-FAN（Al-OLT/Al-FTTR/Al-FTTO）端—边—云算力协同。
  2. 关键创新：10 Gbps 端到端接入、智能集中式 Wi-Fi（C-WAN 与 Intelligent C-WAN，漫游/VIP 切片 AI）、Sub-7GHz 扩展到 mmWave（复用基带 802.11bq）、AI 增强 Wi-Fi、统一智能 IoT、RFID over FTTR。
  3. ITU-T SG15 Q3 在制定 G.sup.ION-aiHome；展望 Wi-Fi 从 2000M 到 10 Gbit/s、空口时延 20 ms→5 ms、并发终端 128→1024（2030）。
- 关键数据：
  - 交互体验"Doherty 阈值"<400 ms：大模型处理 230 ms + 运营商网络 50 ms + 终端 100 ms，留给接入网 400-380=20 ms（图中如此计算）；接入 RTT ≤ 20 ms；带宽需求：4K AIGC ~80 Mbps，4K 3D ~160 Mbps，语音助手/角色陪伴 ~6 Mbps [p4]
  - 10 Gbps 商用统计：10+ 个 10Gbps City（沙特 10Gbps Society Blueprint），600+ 个 1Gbps&beyond 套餐（Lounea 40 Gbps 套餐），100+ 个 10Gbps 试点（Turkcell 三模对称 50G PON 验证）；算力分层 T 级@终端、100T 级@边缘、P 级@云 [p6]
  - IEEE 时间表：802.11bn（超高可靠）D2.0 于 2026年5月完成；802.11bq（集成毫米波）PHY 于 2026H1 完成、进入 MAC 讨论；新增频谱 42–71 GHz；11bn 关键特性含 Co-SR、Co-BF、非主信道接入、DRU/ELR/UEQM [p8]
  - 展望 2030：Wi-Fi 2000M→10 Gbit/s，空口时延 20→5 ms，并发终端 128→1024；智能家居 AI 渗透率 25%→50%（图注 @2025，不确定）[p14]
  - ECOC 展台 1231 演示：对称 50G PON（50G/XGS/G Combo，每线卡 8/16 口，PMD C+ 32 dB，三重共存，符合 G.9804/G.9805）；FTTR 2.5G TDMA-DTA 上行，符合 G.994X；G.sup.IONaiBB/Home Agent 框架（OpenClaw）[p13]
- 提到的公司/客户/产品/标准：Huawei、Turkcell、Lounea、OpenClaw、ITU-T SG15 Q3（G.sup.ION-aiHome）、G.9804/G.9805/G.994X、IEEE 802.11bn/bq、WMCI、eOMCI、WFA Wi-Fi 8 MTG
- 与业界对比或记录声明（SOTA/首次/record）：无明确 record 声明 [p6]
- 推荐配图页：p4（Doherty 阈值时延预算分解）；p6（10G 商用规模与 AI-FAN 算力分层）；p8（Wi-Fi 8 与 802.11bq mmWave 路线）

### 0920-am-Su2-D-03-FraunhoferHHI-功能切分改善WiFi.pdf
- 讲者/机构：Anselm Ebmeyer、Sepideh Kouhini、Ziwen Zhou 等（Volker Jungnickel 等）/ Fraunhofer HHI | 题目：MAC-PHY Split to Improve Performance of Wi-Fi in FTTR Networks | 类型：学术论文（Workshop）
- 方向归属（主/次）：主 5 固定与无线接入；次 无
- 核心主张：
  1. FTTR 中 MFU 作中央控制器，SFU 分布各房间；比较三种 MAC-PHY 功能切分：Split A（联合用户管理）、Split B（联合调度）、Split C（联合预编码/联合 MU-MIMO）。
  2. Split C 在所有场景提升吞吐（最多 75%）；Split B 改善 1%-worst 时延；Split A 在开放办公场景提升吞吐。
  3. 仿真的功能切分兼容 Wi-Fi 6 及之后。
- 关键数据（QuaDRiGa 信道 + 系统级仿真，2.4 GHz，40 MHz，全缓冲下行，1500 B MPDU，每设备2天线，发射功率 10 dBm，SNR 选择 MCS）[p10]：
  - 多户住宅（10 BSS，40 RU，100 STA）：吞吐 参考 41 / A 41 / B 38 / C 67 Mbps（+63%）；平均时延 6/6/7/4 ms；1%-worst 时延 20/20/15/12 ms [p12]
  - 独栋住宅（1 BSS，4 RU，10 STA）：吞吐 41/41/35/72 Mbps（C +75%）；平均时延 3/3/3/1 ms；1%-worst 时延 9/9/3（B，-66%）/3 ms [p13]
  - 开放办公（2 BSS，8 RU，20 STA）：吞吐 42/73（A，+73%）/67/77 Mbps；平均时延 4/3/3/3 ms；1%-worst 时延 20/17/8（B，-60%）/3（C，-85%）ms [p14]
  - 参考方案为 Split A + CSMA/CA 与 Wi-Fi 6 OBSS PD 调整；ED 阈值 -82/-62 dBm 场景相关（取自 p11 OCR，未核对）[p11]
- 提到的公司/客户/产品/标准：Fraunhofer HHI、QuaDRiGa 信道模拟器、EDCA/DCF/PCF/HCF、Wi-Fi 6 HE-SU/HE-TB
- 与业界对比或记录声明（SOTA/首次/record）：无；纯仿真结果 [p15]
- 推荐配图页：p5（三种 MAC-PHY 切分位置示意）；p14（开放办公吞吐/时延对比表与柱图）

### 0920-am-Su2-D-04-UPF-多AP联合调度.pdf
- 讲者/机构：Boris Bellalta / Universitat Pompeu Fabra（Barcelona） | 题目：Toward Multi-AP Joint Scheduling in Next-Generation Wi-Fi | 类型：邀请报告
- 方向归属（主/次）：主 5 固定与无线接入；次 无
- 核心主张：
  1. 802.11bn 的 MAPC（Co-TDMA、Co-SR、Co-BF）是分布式、仅成对协商、开销大；集中式 MAPC（"大脑"+轻量 AP，经快速光回传）可用复杂 AI/ML 做联合决策。
  2. 开放挑战：集中控制器到 AP 的决策与数据采集时延，尤其是 FTTR 上部署；MFU 到 SFU 实时管理命令受光 DBA 调度时延、协议封装开销和队列竞争影响，威胁微秒级时序。
  3. 集中式 MAPC 可演进到 MAC/PHY 切分，实现 Co-OFDMA 与联合传输（JT）。
- 关键数据：
  - DRL（PPO）调度器，场景 Co-SR、4 AP、仅下行；目标最小化时延；对比 MNP（最多包数）、OP（最老包）、TAT（流量对齐跟踪）；单部署下时延（ms）——99th 百分位/均值：MNP 244.50/29.79；OP 257.19/41.61；TAT 103.85/28.19；ML-G 79.73/20.45；ML-E 72.98/19.95（ML-G：改变站点位置和 AP-STA 负载；ML-E：仅改变负载）[p10]
  - 引用文献：Nunez et al., IEEE TMLCN 2026；Wilhelmi et al., arXiv:2606.13759 (2026) [p5, p8]
- 提到的公司/客户/产品/标准：IEEE 802.11bn（Co-TDMA/Co-SR/Co-BF、R-TWT）、FTTR、MFU/SFU、DBA
- 与业界对比或记录声明（SOTA/首次/record）：无 [p12]
- 推荐配图页：p10（各调度算法99分位与均值时延柱图）；p7（集中式 MAPC 与 FTTR 架构及开放挑战）

## 本批小结
1. FTTR 从宽带接入延伸到"AI 家庭/楼内基础设施"：CMRI、Huawei、Nokia 都把 PON+FTTR 定位为 AI 算力/感知承载（CMRI "算力总线"RTT <20 ms、Huawei AI-FAN 端边云 T/100T/P 级算力、Nokia FIP for AI），Huawei 用 Doherty 400 ms 预算把接入网时延压到 20 ms（来自 D-03、Su2-D-02、D-05）。
2. 标准分路线：中国主推 P2MP（G.fin 2.5G→G.Xfin 10G，CMRI Ra/Ra+ 参数、Huawei 展台 2.5G FTTR），Nokia/MaxLinear 强调 P2P G.9930（25G/50G 于 2025-10 加入）与企业 PON Optical LAN；两条路线并存（D-03、D-04、D-05、Su2-D-02）。
3. 光—无线协同是共同瓶颈：MaxLinear WMCI、Fraunhofer HHI 的 MAC-PHY 切分（联合预编码吞吐最多 +75%）、UPF 集中式 MAPC（DRL 调度 99% 时延约 73–80 ms 对比 MNP 约 245 ms）都依赖低时延光管理通道；UPF 明确指出光 DBA 调度时延是集中式 MAPC 上 FTTR 的开放难题（D-04、Su2-D-03、Su2-D-04）。
4. mmWave Wi-Fi 是下一步：Nokia（60 GHz，5.12 GHz 带宽约 10 Gb/s）、Huawei（802.11bq，42–71 GHz，PHY 2026H1 完成）、MaxLinear（802.11bq 回传）均把 FTTR 视为 mmWave 每房间一 AP 的回传前提（D-04、D-05、Su2-D-02）。
5. 用户价值与部署现实：听众投票 63% 首选可靠性；Nokia 数据显示多数家庭仅 1 个 AP，仿真每户最优 2–3 个 AP，说明"每房间一 AP"未必最优；欧洲户内体验与 FTTH 覆盖不同步（D-01、D-05、D-02 DT 建筑异质性）。
6. AI 进入 Wi-Fi 物理层与管理层：DeepSig 神经接收机（5G 上行 2–3×）、Huawei AI Wi-Fi 漫游/切片、UPF DRL 调度，均呼吁标准预留 AI 钩子（Su2-D-01、Su2-D-02、Su2-D-04）。
