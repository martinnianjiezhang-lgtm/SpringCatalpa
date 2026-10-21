---
title: "R11_executive-sessions"
tags:
  - OCP2026
  - 讲稿笔记
---

# R11 笔记：executive-sessions

### P247 11_Breaking the Walls Open Scale-Across for the AI Era presented by Cisco
- 讲者/机构：Vipul Deokar（VP Core Network Infrastructure, Meta）；Rakesh Chopra（SVP Silicon & Systems Architecture, Engineering Fellow, Cisco）；Tom Williams（VP Marketing, Cisco）[p1] | 类型：主题演讲（Meta 用户案例 + Cisco 厂商方案）
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：DCI、ZR/相干、SRv6、深缓冲]；次 [Out 后端网络：交换芯片、SONiC]
- 核心主张：
  1. Meta 的单个 DC region 混合了 H 型机房、单楼、帐篷及第三方云容量，要在更多 region 更快扩展；按光纤 RTT 把 region 编成 "Ring"，Ring 内共用一套服务栈，形成 RBB（Regional Backbone），模糊 DCN 与 DCI 边界 [p7, p9–p11]。
  2. Scale-Across 把跨站点网络放进分布式 AI 训练的关键路径：流量少而持续、同步、高带宽，慢流/中断会让加速器空转，与传统 DCI 的多样异步流不同 [p16–p17, p26]。
  3. 需要开放的 packet-to-optical 架构：深缓冲、拥塞控制与相干光通过互通接口协同 [p25–p26]。
- 关键数据：
  - 训练算力约每 5 个月翻倍（引用 Stanford HAI 2025 AI Index）[p2]；xAI Colossus 训练用 200K+ GPU（引用 NVIDIA）[p2]
  - Epoch AI 气泡图：2026 上半年最大站点约 770K H100 等效/4 栋、约 680K/16 栋、约 600K/11 栋（看图；引用 Epoch AI）[p3]
  - Meta 由 EBB 连接 23 个 DC region：北美 19、欧洲 3、亚洲 1（自报）[p8]
  - Ring 按 1/5/10 ms RTT 分档；Ring 内容量是 Ring 间的 10x；首个试点 region 对已释放"数个 MW"基线功率（自报，未给精确值）[p11]
  - 跨楼距离与光模块：<3 km 用 FR，≤10 km 用 LR，>10 km 需 ZR + DWDM（自报）[p12]
  - >10 km Scale-Across/AI-BB：两端各"10,000s of 800G ZR"，经光保护开关 + MUX 走工作/保护双路径；无 ILA 120–150 km，带 ILA 500 km+（自报，p13 文字层 + 看图）[p13]
  - Cisco Silicon One P200：固定系统 8223/Nexus 9000 每系统 51.2T；模块化 8800/Nexus 9800 每线卡 28.8T（自报）[p20]
  - 相干可插拔（ZR+ 直插路由器）对比转发器方案：能耗降 90%、空间省 >65%、CAPEX 降 66%；ACG Research 称 TCO 省 40–60%（引用 ACG Research）[p22]
  - 多轨 OLS（Open Transport 3000 vs NCS 1010）：功耗降 75%、空间省 80%；每 4x C+L 轨 350 W，每机箱（5RU）16 条 C+L 轨，每机柜 12 kW 内 128 条（对比单轨方案每机柜 32 条）（自报）[p23]
- 提到的公司/客户/产品/标准：Meta（EBB、RBB、FBOSS、Prometheus）、Cisco Silicon One P200、8223、8818、Nexus 9000/9800、NCS 1010/1014、Open Transport 3000、800G ZR/ZR+、1600G ZR+、OpenROADM、OIF、OCP SAI、SONiC、SRv6 TE、IETF、oFEC/cFEC/PCS、Broadcom G300（展台 1.6T demo）、Epoch AI、xAI
- 首次/记录/SOTA 声明：Cisco 自称多项开放相干标准的主导者和可插拔模块领先供应商 [p24]；无量化"首次"
- 推荐配图页：p11（RBB 按 RTT 分 Ring 的区域骨干示意）；p13（>10 km 800G ZR + 光保护的 Scale-Across 连接图）；p3（Epoch AI 多楼 AI 站点气泡图）

### P248 12_Building the AI Factory Overcoming the Infrastructure Challenges of AI
- 讲者/机构：Tony Wen（VP Engineering Management, Wiwynn）[p1] | 类型：厂商展区/主题演讲
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/机柜级互连]；次 [底座-电力] [底座-冷却]
- 核心主张：
  1. 供电向 HVDC 演进，缩短低压大电流路径；新概念为 HVDC 直接转 6 V 模块，配合 VPD [p6–p7]。
  2. 冷却趋势是缩短冷却液到芯片的热路径：金刚石材料、3D 打印微通道、双面冷板、on-chip cooling，去除 TIM [p8]。
  3. 用 CPO 做跨机柜光互连的 scale-up，与 Ayar Labs 合作 [p9–p10]。
- 关键数据：
  - Wiwynn 2025 营收 306 亿美元，2024–2025 增 2.6x；2021–2025 营收 CAGR 49%；机柜出货 2024–2025 增 1.9x（自报）[p2]
  - CPO AI 加速器（OE + ASIC）：时延低 10x、带宽高 5–10x、能效高 3–5x（看图；自报，未说明对比基线）[p9]
  - Open CPO AI Compute Rack：每柜 64 颗 CPO XPU，>800 TB/s 光带宽，100% 液冷（看图；自报）[p9]
  - 与 Ayar Labs 的光连接机柜：32 个计算托盘，连接 64 颗 ASIC，>800 TB/s 光带宽（看图；自报）[p10]
  - 展台演示称"World 1st working TSMC COUPE IC in Tray: LIVE demo"（自报）[p13]
- 提到的公司/客户/产品/标准：Ayar Labs、TSMC COUPE、NVIDIA Vera Rubin NVL72、AMD Helios（MI455X）、HVDC、SST、VPD、ELSFP（日程页）
- 首次/记录/SOTA 声明：首个可工作的托盘级 TSMC COUPE IC 现场演示（自报）[p13]
- 推荐配图页：p9（CPO 计算柜 + 跨机柜光互连 scale-up 示意，带 64 XPU/800 TB/s）；p10（Wiwynn x Ayar Labs 光连接机柜实物）

### P249 13_Characterization of Hose Material Effects on Coolant Chemistry During
- 讲者/机构：Gates（具体讲者未见）[p3, p14] | 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张（精简）：
  1. 过氧化物硫化 EPDM（pEPDM）仍是数据中心冷却软管的合适材料，但不同配方和清洁度导致析出物差异很大 [p9, p14]。
  2. 析出物会降低换热、堵流、损害泵、引起腐蚀；需建立流体化学基线，支持实时流体监测 [p7, p13]。
- 关键数据：
  - 测试方法：基于 ASTM D471，80°C 老化 8 周（1,344 h），1 m 长 -8 规格软管，DI 水基冷却液（实验）[p4, p12]
  - 流体中不挥发残留：对照 24 ppm；硫化 EPDM 538 ppm；pEPDM #1 352 ppm、#2 6,379 ppm、#3 2,062 ppm（实验，Phase 1，自称"方向性、非最终"）[p9, p10, p13]
  - 硫化 EPDM 析出锌、硫、磷；pEPDM #2 检出 Fe、Zn 氧化物，SEM 可见管表面片状沉积（实验 + 看图）[p9, p10]
  - Phase 2 于 9 月开始，已备 5 种 pEPDM 样品；Phase 3 改用近沸点温度下的材料试片（自报）[p13]
- 推荐配图页：p10（五组样品 ppm 与 SEM 对比图）

### P250 14_Co-Designing High-Speed Copper and Optical Interconnects
- 讲者/机构：Brian Kirk（CTO, Amphenol）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板、CPO/NPO/XPO]；次 [Out 后端网络：可插拔光模块/LPO]
- 核心主张：
  1. 超过 102.4 Tb/s 后，限制扩展的是前面板 I/O 密度，不只是交换 ASIC；要尽早离开 PCB，在端口用新形态 [p2–p3]。
  2. 线性（铜或光）端口的性能由电通道决定；从封装直接出线（CPC/NPC）可以把损耗预算留给电缆，让铜覆盖整个机柜甚至两个机柜 [p4, p9, p12]。
  3. 无源互连从封装到面板到背板没有开放、可复用的定义，呼吁社区在 448G 下定义线性链路预算，2028 年 1Q 达成规范共识 [p15, p17]。
- 关键数据：
  - 204.8 Tb/s 可用 128 × 1.6T OSFP 或 16 × 12.8T XPO（自报）[p2]
  - 448G 前面板 I/O 可行性：连接器+主板实测 IL 约 -12 dB @56 GHz、约 -17 dB @87 GHz（448G PAM6）、约 -23 dB @110 GHz；仅连接器仿真 0 至 -3 dB（看图，估读）[p3]
  - Nyquist 处插损：前面板 XPO-LPO（CPC → 30 cm twinax → 连接器 → 模块）19 dB，近封装 NPO 9 dB（自报/估算）[p6]
  - 64 通道 XPO-LPO、3 nm 交换主机、主机+电缆 IL 15 dB：单通道 BER 1e-10 至 1e-12，64 通道全开约 1e-7，差距来自串扰（实验）[p7]
  - 224G PAM4、53 GHz Nyquist、twinax 14 dB/m：传统路径中主机 PCB 占 10 dB + 4 dB，0.35 m 线缆只占 6.2 dB；从封装出线时线缆可到 2 m（28 dB）（估算）[p9]
  - 封装到封装铜通道：0.8 m twinax 全柜走线共用 22 dB，40 dB 预算余 18 dB（经主机 PCB 出线时仅余 5.8 dB）；下一代介质 6 dB/m 时可达 3.8 m（估算）[p12]
  - NPO 到 NPO 光通道：端到端光预算 2.5 dB（OCI MSA 链路模型，500 m SMF），每个可分离连接约 0.3 dB，6 个约 1.8 dB；V-groove/MPO/EBO 分别 0.1/0.35/0.7 dB（估算）[p13]
  - 256 GPU、64 颗交换 ASIC 单跳架构：16,384 条通道；4 机柜方案中铜 4,096 条、光 12,288 条，铜/光比 25/75（估算）[p11, p14]
  - 社区时间表：Q4 2026 定范围与参考通道；1H 2027 首批测量与测试点提案；1Q 2028 规范共识与首批部署（自报）[p17]
- 提到的公司/客户/产品/标准：IEEE 802.3dv（400G/lane）、OIF CEI-448G、CEI-224G-Linear、OIF 12.8T NPO Module、IEEE 802.3 E4AI、OCI MSA、400G Optical MSA、OCP SROI、OCP ESUN、Open Rack、XPO MSA、OpenCPX MSA、OSFP、ELSFP、MMC、FSC144、RAF、OverPass
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（XPO-LPO 19 dB vs NPO 9 dB 插损分解柱图）；p12（封装出线铜通道 22/40 dB 预算链）；p14（256 GPU 铜在柜内、光跨柜的 25/75 分配）

### P252 16_Delta 800 VDC Power and Cooling Solutions for Data Centers presented b
- 讲者/机构：Mike Tu（Principal Electrical Engineer, NVIDIA）；Ralf Pieper（R&D Senior Director, Delta）[p1] | 类型：厂商展区/技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [底座-冷却]
- 核心主张（精简）：
  1. 机柜功率从 GB200/GB300 的 145 kW 走向 570 kW 以上，需要 800 VDC 配电，从机柜级 Power Rack 到集群级 Power Center 再到数据厅级 SST Power Block 分阶段过渡 [p4–p6, p23]。
  2. 储能（PSU 内电容、BBU/CBU、ESS）用于平滑 GPU 负载、故障穿越，并在 SST 之间均摊负载以支撑 MaxLPS [p9, p21]。
- 关键数据：
  - 机柜代际：Gen1 GB200/GB300 54 VDC 145 kW；Gen2 Vera Rubin NVL72 54 VDC 330 kW；Gen3 54 VDC 570 kW、800 VDC 进入 PSU、100% 液冷（看图）[p4]
  - 50 VDC 适用 <250 kW；>250 kW 用 ±400 VDC/800 VDC（自报）[p6]
  - 电源架演进：GB300 33 kW（5.5 kW PSU，75 J）→ 72 kW（12 kW，105 J）→ VR200 110 kW（18.5 kW/54 V PSU，1200 J，>10x）（自报）[p7]
  - 660 kW 800 VDC 行间电源柜，效率最高 98%，集成 480 kW BBU；900 kW 版本可配 BBU/CBU（自报）[p12, p14]
  - 机柜内 800→54 VDC DC/DC 电源架 90 kW/108 kW，峰值效率 98.5%（自报）[p15]
  - 1 MW 负载下 97% 效率 PSU 损耗 30 kW，风扇 200 W、效率损失 0.7%，因此 PSU 改液冷，55 kW/1U（自报）[p16]
  - 设备就绪：Option A Power Rack Q3 2026；B Power Center Q2 2027；C Power Block Q1 2028（看图）[p23]
  - 800 VDC 行间 CDU：2.5 MW @ Tapp 4°C，3,850 LPM @60 psi（自报）[p26]
- 推荐配图页：p4（机柜功率代际与 Power Gen 1–4 图）；p23（800 VDC 设备就绪时间线）

### P253 17_Designing the next AI fabric When compute meets optics presented by Ce
- 讲者/机构：Tareq Bustami（VP Market Technology）、Manish Mehta（VP of Marketing and Operations）、Binbin Guan（Member of Technical Staff）；机构从 p18 判断为 Celestica，p6/p9 含 OpenAI、Broadcom 页 [p1, p18] | 类型：主题演讲/厂商展区
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO、机柜级互连、光 scale-up]；次 [Out 后端网络：交换芯片] [推理/算力/经济性]
- 核心主张：
  1. 推理的衡量标准是在匹配用户体验（TTLT）的前提下的能效（tokens/J），每个请求跨越 prefill、draft、spec-verify 三种不同的硬件瓶颈 [p3–p4]。
  2. 2027–2030 向全光迁移：交换机和 XPU 采用 CPO，scale-up 使用 OCI 慢而宽的光接口、BiDi 多波长，使 scale-up 从单柜扩到多柜多排 [p12, p16]。
  3. 技术迭代加快、认证窗口缩短，方案认证成为关键路径 [p15]。
- 关键数据：
  - OpenAI Jalapeño："半扁平"两级 Clos，本地域 128 颗 Jalapeño 连 Broadcom TH6，全局域 2048 颗，经 8 个 TH6 rail（看图；引用 OpenAI Hot Chips 2026）[p6]
  - Broadcom CPO 演进：2022 TH4 Humboldt 25.6T 100G/lane；2024 TH5 Bailly 51.2T 100G/lane；2026 TH6 Davisson 102.4T 200G/lane；2028 OCI 下一代（看图）[p9]
  - 每个芯片封装连接超过 1k 根光纤，需要可拆卸光纤连接器以便封装回流焊（自报）[p10]
  - OCI MSA 成立于 2026 年 3 月；OCI GEN1 为 4λ × 50 Gbps NRZ、DWDM、bidi；GEN2 400 Gbps 规范 2027；GEN3 800 Gbps 202x（自报）[p12–p13]
  - 电接口：200 Gbps 当前为 100 Gbaud PAM4 且可线性；400 Gbps 2027 年"Maybe"；800 Gbps >2030 年"Unlikely"（自报判断）[p13]
  - 认证周期：100G/400G 36 个月，800G 24 个月，1.6T 18 个月，下一代 9 个月（自报）[p15]
  - 单个 scale-up 机柜约 5,000 根无源铜缆；约 1 MW 液冷机柜；机柜重量今天约 4,000 lb，设计目标 8,000 lb（自报）[p15]
  - AI 使用：ChatGPT 周用户 >1B（2026-08-31）；Codex 周用户 >5M（2026-07-09）（引用 OpenAI）[p2]
- 提到的公司/客户/产品/标准：Celestica DS6005（基于 Broadcom TH6 Davisson CPO，计划贡献给 OCP）、OpenAI Jalapeño、Broadcom TH4/TH5/TH6、OCI MSA、SONiC、ORv3、VCSEL/EML/CWL
- 首次/记录/SOTA 声明：Celestica 计划把 DS6005 开放 CPO 平台设计贡献给 OCP [p18]
- 推荐配图页：p6（OpenAI Jalapeño 两级 Clos scale-up 拓扑）；p9（Broadcom TH4 到 OCI 的 CPO 演进）；p15（认证周期 36→9 个月与机柜复杂度数据）

### P254 18_Dispersion Managed Transceiver for Next-Gen AI Fabrics
- 讲者/机构：Grace Zhang, Ph.D.（Linktel Technologies）[p1] | 类型：技术分享/厂商展区
- 方向归属（主/次）：主 [Out 后端网络：可插拔光模块]；次 [Across 跨楼/园区：10–20 km 互连]、OCS SuperPOD
- 核心主张：
  1. CWDM（FR4/FR8）预计到 2030 年仍主导 4x200G、8x200G 出货，但单波速率提高后色散限制传输距离 [p2–p3]。
  2. 在现有 CWDM FR4 设计中加入硅 GT 标准具色散管理器件（DMD），可在 800G 实现 20 km、1.6T 实现 10 km，且无光损耗、功耗可忽略 [p4–p5, p13]。
- 关键数据：
  - 未做色散管理时：100G/lane 10 km；200G/lane 2.5 km；400G/lane 600 m，"速率 2× → 距离 1/4"（引用 Zhou et al., OFC 2023）[p3]
  - DMD：HR 镀膜 >99.9%，近零插损，DSP 闭环自锁（自报）[p5]
  - 800G 2LR4+ 20 km：BER 1e-9 至 1e-10（Beta）；800G FR4 10 km：BER 1e-10 至 1e-11（212G），226G 加 inner FEC 无误码；1.6T 2FR4 SiPh 10 km：1e-11 至 1e-12（212G），226G 无误码（Alpha）（自报）[p4]
  - 800G 2LR4+ 20 km：10–70°C 温循 10 次、36 只模块，pre-FEC BER 始终 <1e-7，FEC BIN ≤4；8 通道链路预算均 >10 dB（实验 + 看图，箱线图多数在 11–13 dB）[p7]
  - 800G FR4 10 km：TH5 交换机温循 4 次 10 只，212G pre-FEC 约 1e-9 至 1e-11（看图）[p8]
  - 1.6T 2FR4 10 km：0 km OMA >4 dBm；OMA-TDECQ >1.1；10 km 灵敏度 @2.4e-6 < -3.7 dBm；DMD 长期锁定代价 0.5 dB（自报）[p9]
  - 400G/lane 验证：TFLN 调制器 190 GBaud PAM4（380 Gbps）@1271 nm，3 km 未补偿时眼图闭合，加 DMD 恢复（ER 3.3 dB，AOP -0.6 dBm）（实验）[p10]
  - 对比表：DMD-CWDM 在供应链、FR4 互通、成本三项优于 LAN-WDM 和 Coherent-Lite（看图；厂商自评）[p11]
- 提到的公司/客户/产品/标准：Linktel、Broadcom TH5（测试平台）、CWDM FR4/FR8、LAN-WDM、Coherent-Lite、TFLN、OCS SuperPOD；3 项美国专利申请（19/026,490、19/295,055、19/295,081）[p12]
- 首次/记录/SOTA 声明：获 Lightwave Innovation Award（自报）[p4]；称"打破 CWDM 色散极限"（自报）[p13]
- 推荐配图页：p3（单波速率与色散受限距离）；p7（800G 20 km 温循 BER 与链路预算统计）；p10（400G/lane 3 km DMD 眼图恢复）

### P255 19_Eliminate Every Obstacle Between Your Data and Your GPUs presented by
- 讲者/机构：Peter Corbett（Fellow, VP, Dell Technologies）；Kirankumar Bhusanurmath（Technical Product Manager, Dell）[p1] | 类型：厂商展区
- 方向归属（主/次）：主 [存储]；次 [推理/算力/经济性]
- 核心主张（精简）：
  1. 智能体推理的上下文/KV cache 超出 GPU 内存，推理受上下文管理约束而非算力；将 KV cache 卸载到存储，减少重复计算 [p12]。
  2. "统一存储"在规模上是妥协；Dell Exascale 在通用 PowerEdge 上按节点切换文件/对象/并行/块存储"人格" [p8, p10–p11]。
- 关键数据：
  - Lightning FS 每节点 150 GB/s（自报）[p9]
  - R7725xd：2U，24 × NVMe，每盘 7–245 TB，4 × 400GbE（自报）[p11]
  - PowerRack 从交付到投产 6 小时（引用 Principled Technologies，Dell 委托，单机柜 16 GPU 风冷）[p13]
  - Dell 2025 年机柜级基础设施出货量和营收份额第一（引用 IDC Q4 2025）[p13]
- 推荐配图页：p12（KV cache 卸载到存储的推理架构）

### P256 20_Enabling High-Performance Thermal Management for 1600G AI Data Center
- 讲者/机构：Robbie Xu（Head of US/EMEA Sales and Marketing, Luxshare-Tech）[p1] | 类型：厂商展区/技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [Out 后端网络：可插拔光模块]
- 核心主张（精简）：
  1. 224G+ I/O 下光模块功耗与端口密度上升，风冷到达极限，前面板需集成液冷 [p3–p4]。
  2. 推出液冷 OSFP 2×8 笼子 + 上下浮动冷板，单侧进出水，一步压装 [p5–p7]。
- 关键数据：
  - 规格：模块功耗 40 W，壳温 ≤70°C；16 个 OSFP 压降 ≤35 kPa，流量 1.15 lpm；冷却液 ≤25% 乙二醇，进水 ≤40°C（自报）[p6]
  - 仿真：512 W、1.15 LPM、进水 40°C，出水 48.33°C，最高端口壳温 66.35°C，压降 34.18 kPa（仿真）[p9]
  - 实测：16 × 32 W、1.15 L/min，10 组样品最高温 55.2–62.6°C，进水约 41–42.7°C（实验）[p10]
  - 插拔力 <55 N / 拔出力 <45 N，100 次插拔后最大插入力 54.4 N，通过（实验）[p11–p12]
  - 3 个月内可复制交付 OSFP 224G+ 液冷方案（自报）[p3]
- 推荐配图页：p6（OSFP 2×8 液冷笼子结构与规格）；p10（16 端口温度实测表）

### P257 21_Every Megawatt Counts The Path to Building AI Factories with DSX MaxLP
- 讲者/机构：Ajay Kamalvanshi（Senior Director, NVIDIA）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [运维/可靠性/遥测] [推理/算力/经济性]
- 核心主张（精简）：
  1. 不同负载的实际功耗差异大，静态按 Max-P 配电会搁浅功率；DSX MaxLPS 用闭环动态分配功率，在同一功率预算下部署更多机柜 [p3–p5, p7]。
  2. 需要更快的遥测：从 Modbus/Redfish 转向基于 UDP 的流式接口，与 OCP GPU Management Interfaces 工作组合作 [p11]。
- 关键数据：
  - GB300 推理实测 GPU 功率（无封顶）：DeepSeek-R1 约 1030 W、Qwen3 235B 约 710 W、GPT3-175B 约 1060 W、Mixtral 8x7B 约 840 W；MaxP 1400 W、MaxQ 1100 W（看图，估读）[p3]
  - GB200（Kimi-K2.5 FP4，Dynamo TRT-LLM 8K/1K）：GPU TGP 1,200 W→800 W，机柜配电 120 kW→90 kW，吞吐不变，同一功率下多 33% 机柜（自报）[p4]
  - 540 kW 预算：静态分配消耗 330 kW、搁浅 210 kW；MaxLPS 消耗 425 kW，多放 1 个机柜（自报）[p5]
  - 闭环算法阈值：差距 >20% 减配、5–20% 不动、5% 以内增配（自报）[p7]
  - 北美可释放的搁浅电网功率 100 GW（自报，与 Emerald AI 合作）[p6]
- 推荐配图页：p5（静态 vs MaxLPS 功率分配对比）

### P261 25_From Chips to Compute Delivering AI Infra at GW Speed presented by Ing
- 讲者/机构：Liu Zongchang（CDO, Foxconn Industrial Internet）[p1] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-机架/机械]（制造与自动化）；次 [运维/可靠性/遥测]
- 核心主张（精简）：
  1. CSP 的瓶颈已从拿到芯片转向把芯片快速变成算力；Foxconn 用面向自动化设计、数字孪生和人形机器人做全栈自动化 [p2–p3]。
  2. Vera Rubin 采用无线缆中板、无软管液冷（机柜内集成 manifold），以支撑自动化装配 [p5]。
- 关键数据：
  - 前 5 大 CSP 新增 AI 算力：2023 年 3 GW、2024 年 7、2025 年 8、2026E 18、2027E 26，CAGR 75%（自报）[p2]
  - Vera Rubin NVL72 含 130 万个元件、1,300 颗芯片（自报）[p2]
  - VR 对比 GB：自动化覆盖率 94% vs 56%；测试 FPY 80% vs 39%；装配 FPY 97% vs 91%；NPI 周期 3.5 vs 4.5 个月（自报）[p4]
  - L10 测试：1000+ 测试位，总容量 100+ MW，单台测试 12 h（减少 3 h）（自报）[p7]
- 推荐配图页：p4（GB→VR 自动化指标对比）

### P263 27_From grids to bits presented by BizLink
- 讲者/机构：Dr. Hendrik Coldenstrodt（CTO Computing and Transportation BG, BizLink Group）[p1] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-电力]；次 [Up 机柜/超节点：铜缆] [Out：光纤连接]
- 核心主张（精简）：
  1. 功率上升使电源线更粗更多，硅橡胶线缆不需降额，弯曲力低约 50%；800 VDC 全套连接器与母排 [p5, p7, p9]。
  2. 保持 PAM4 会把 Nyquist 推过 100 GHz，铜缆需要更细更柔；光纤侧推进 448G、OCS、NPO/CPO 的光纤连接 [p16–p20]。
- 关键数据：
  - 单数据中心功率纪录约每 10 个月翻倍；全球 AI 功率容量约 30 GW，接近纽约州峰值 31 GW（看图；引用 Epoch AI）[p3]
  - ORV3 48 Vdc 机柜母排最高 1.4 kA，设计可到 3 kA，3.2 kA 起需液冷；电源架母排最高 110 kW（自报）[p8]
  - 超细 CPC：AWG 39，在 110 GHz 内无 suck-out，可支持 448G PAM4（自报）[p17]
  - MPO 和 MMC 典型 IL <0.1 dB（自报）[p19]
  - CPU:GPU 比：生成式训练 1:4–1:8；智能体/推理 1:2–1:1（自报）[p15]
- 推荐配图页：p9（800 VDC 机柜连接器/母排全景）；p16（铜缆挑战清单）

### P264 28_From LPO to NPO​ to CPO​ The open optical roadmap for AI infrastructur
- 讲者/机构：Tim Zhou（VP, Micas Networks）[p1] | 类型：技术分享/标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/NPO/XPO]；次 [Out 后端网络：可插拔光模块/LPO、SONiC]
- 核心主张：
  1. 光 I/O 靠近芯片是确定方向，未定的是时间、服务模式和量产成熟度；2026 年是 CPO 早期采用年，2027 年不确定性最大，2028–2030 年可能 XPO/NPO/CPO 共存 [p1, p3]。
  2. 各方案解决不同问题，不是单一替代：可插拔是规模基线，LPO 近期降功耗，NPO 在保持可维护性的同时缩短电通道，CPO 功耗和密度最好但良率/维修复杂；比较要看每瓦、每 RU、每美元、每单位运维风险的带宽 [p4–p5, p10]。
  3. 实际爬坡取决于生产工程：电通道、热、良率与可维护性、光纤连接器、软件运维（SONiC、CMIS、共享激光器）[p11]。
- 关键数据：
  - 3 个新 MSA：OCI MSA（光 PHY；AMD、Broadcom、Meta、Microsoft、NVIDIA、OpenAI）；Open CPX MSA（光引擎；Ciena、Coherent、Marvell、Molex、Samtec、TeraHop）；XPO MSA（可插拔形态，Arista 牵头）（看图）[p8]
  - 时间判断：LPO 2026 验证与选择性部署，2027 仅在 SI 余量验证处扩大；XPO 2027 工程探索；OCI/OBO 2026–2028 围绕 TH6 级平台的早期系统；Open CPX 2027 原型、2028 早期部署；CPO 交换机 2027–2029 先增长，XPU-CPO 更晚（预测）[p9–p10]
  - CPO/NPO 的光器件靠近 1–2 kW 级 ASIC 封装（自报）[p11]
- 提到的公司/客户/产品/标准：Micas Networks、Broadcom（展会 CPO）、OCI MSA、Open CPX MSA、XPO MSA、OBO、ICA-based NPO、CPC、ELS、CMIS、SONiC、TH6
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（三个新 MSA 及成员）；p10（2026–2029 NPO/CPO 展望表）

### P265 29_From Open Standards to AI Factories DCBBS, Modular Design, and the Lat
- 讲者/机构：Magelli Roxas（Sr Rack PM）、Steven Huang（Product Manager），Supermicro [p1, p23] | 类型：厂商展区
- 方向归属（主/次）：主 [底座-冷却] [底座-机架/机械]；次 [Out 后端网络：交换机、CPO]
- 核心主张（精简）：
  1. DCBBS 积木式方案从系统、机柜到数据中心级整体交付，集群从 5 MW 扩到 1 GW [p2, p5]。
  2. 先确定热架构再选 CDU；新一代 GPU 机柜密度和 CDU 需求翻倍 [p16, p19, p21]。
- 关键数据：
  - 每个可扩展单元 1,152 GPU；HGX B300 机柜每柜 144 GPU，48OU ORV3，1400 A 母排，约 245 kW（N+2）（自报）[p5]
  - 机柜功率：GB300 NVL72 约 136 kW；VR NVL72 约 230 kW；HGX Rubin NVL8 约 227 kW；VR NVL4 约 362 kW；Vera CPU 约 207 kW（自报）[p16]
  - 交换机路线：SSE-T8264 64×1600G OSFP 102.4T，目标 GA CQ4/26；SSE-T8264C 128×800G DR8 CPO（ORV3），SSE-T8264C2 64×1600G DR8 CPO（MGX），目标 GA CQ1/27，均跑 SONiC（自报）[p14]
  - CDU：机柜内最高 250 kW；行间 1.8/2.5/5 MW；Sidecar L2A 200–500 kW；温水最高 45°C（自报）[p17–p18]
- 推荐配图页：p14（102.4T 可插拔与 CPO 交换机路线）；p16（各平台机柜功率）
