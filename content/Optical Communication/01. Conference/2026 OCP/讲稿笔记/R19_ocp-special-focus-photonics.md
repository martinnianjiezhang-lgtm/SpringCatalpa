---
title: "R19_ocp-special-focus-photonics"
tags:
  - OCP2026
  - 讲稿笔记
---

# R19 笔记：ocp-special-focus-photonics, networking

### P428 The UALink Switch API - A Common Abstraction for Scale-Up AI Switches
- 讲者/机构：Ayyappa Nuthalapati（Marvell）、Justin King（AMD）、Ravindranath Kanakarajan（Marvell），代表 UALink Management Working Group [p1] | 类型：标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：UALink]；次 [运维/可靠性/遥测]
- 核心主张：
  1. 在 UALink 交换生态起步阶段就定义一个厂商无关的开放 C API（UALink Switch API），让同一个 SMA（Switch Management Agent）可管理任意厂商的交换芯片；API 只定义契约，不定义物理接口/传输，厂商各自提供库或 daemon [p5]。
  2. API 采用对象模型（Platform/Switch/Port/Neighbor/Route 两类）、key 寻址、批量优先的 CRUD、带直方图的遥测和"全量状态 + 时间戳"的事件通知，避免丢更新竞争 [p8][p10][p11][p12]。
  3. 由 Pod Controller 驱动的 6 步 bring-up：发现 → 交换机配置 → 端口 → 邻居校验 → vPod 隔离 → 路由安装，SMA 作为无状态直通 [p13]。
- 关键数据：
  - UALink 200G 复用 IEEE 802.3dj Ethernet PHY 及现有线缆/retimer，Consortium 定义其上的 DL/TL/Protocol 层 [p3]（自报）
  - 端口为 128G/200G [p7]（自报）
  - 6 个 API 模块：Platform（单例）、Switch（switch_index）、Port、Neighbor、Route Type-1 vPod（key: switch_index, vpod_id, logical_switch_id, dst_apu_id）、Route Type-2 Flow（key: switch_index, src_apu_id, src_port_number, dst_apu_id）[p8]（自报）
  - 示例属性：UALINK_PORT_ATTR_DL_DOWN_DELAY，RS fault 后 DL down-delay 默认 5 ms，范围 0–10 ms [p9]（自报）
  - 遥测计数器包括 PL FEC-error 直方图、DL LLR replays、DL bad/good CRC、TL/UPLI credit 直方图等；stats mode 支持 READ / CLEAR / READ_AND_CLEAR（原子）[p11]（自报）
  - 管理架构接口：Pod Controller ↔ NMA 走 Redfish，Pod Controller ↔ SMA 走 UALink gNMI，SMA ↔ 交换芯片走 UALink Switch API [p4]（自报）
  - API 头文件以 Apache-2.0 在 UALink Consortium 下定稿，"即将"发布到社区 GitHub；附带 mock SMA 与 mock vendor SDK [p14]（自报）
  - 定义仍在演进，向 v1.0 推进 [p7]（自报）
- 提到的公司/客户/产品/标准：UALink Consortium、Marvell、AMD、Google（Arun Satyanarayana 为 WG 联合主席）[p15]、IEEE 802.3dj、Redfish、gNMI
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（Pod Controller/NMA/SMA/Switch API 的接口分层图）；p13（6 步 bring-up 流程图）

### P429 Traffic Engineering in AI DCI-WAN for AI Traffic
- 讲者/机构：Clarence Filsfils（Cisco Systems）、Yuanchao Su（Alibaba Cloud）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [Across：DCI、SRv6、ZR/相干]；次 [Out：SONiC]
- 核心主张：
  1. 受电力限制，训练作业跨区域内多个集群分布，AI DCI/WAN 拓扑更不对称、容量稀缺、时延敏感，因此流量工程（TE）是必需项 [p2]。
  2. AI DCI 本质是 IP 网络，SONiC 正扩展到 DCI，SRv6 在 DC 硬件和 SONiC 中成熟，可实现 DC 到 DC 端到端 SRv6 TE [p3]；给出三种方案：Agg 分类+导流、Host 分类+导流、Host 分类+Agg 导流（BSID 展开）[p5][p6][p7]。
  3. 阿里云按"Token Native"原则建专用 AI 网络：单租户、单栈、无 overlay、无复杂 QoS，模型与基础设施协同做 per-job TE 和光层韧性 [p9]。
- 关键数据：
  - 阿里 eCore：多个专用 eCore（AI Scale Across、Peering、集团、公有云、金融），多域/多平面架构，爆炸半径 O(10) [p10]（自报）
  - 单栈单芯片：SONiC+SRv6 pizza box，12.8T/51.2T/102.4T（未来）[p10]（自报）
  - eCore for Public Cloud：128*100G/128*400G pizza box，100G/400G 链路；eCore for Scale Across：64*800G pizza box，400G/800G 链路，带 Collapsed Core 层，X16 并行 [p11]（自报）
  - Per-job TE：Job→BTH→TE，"supported in P200/Q4D"；主路径 <uA, uN> 带 echo BFD，备份路径 eAR anycast GRT SID；新 BGP NLRI 携带 BTH 信息 [p12]（自报）
  - Full Spectrum Transponder：一个 transponder 一根光纤，每模块 8 个固定波长 DFB 激光器（ELSFP），20 dBm 通道功率，C 波段 4.8 THz 频谱，每机箱每光纤 25.6 Tb/s [p13]（自报）
  - LD/RD（link degrade/remote degrade）：pre-FEC BER 超过预设阈值即把劣化路径移出 ECMP 组，实现无损收敛；引用 ITU G.709、OIF 400ZR/800ZR IA [p13]（自报）
- 提到的公司/客户/产品/标准：Cisco、Alibaba Cloud、SONiC、SAI、SRv6/uSID、BSID、ELSFP、COSA、800ZR、400G DR4、OIF-400ZR-03.0、OIF-800ZR-01.0、ITU-T G.709
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（阿里 Scale Across 两区域拓扑）；p13（全谱 transponder 与 LD/RD 收敛示意）

### P430 Zero-Touch OCS Fabrics for AI Scale-Out Infrastructure at Hyperscale
- 讲者/机构：Kannan Raj（Oracle Cloud Infrastructure）、Michael DeMerchant（Lumentum）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [Out：OCS]；次 [运维/可靠性/遥测]、[Across：DCI]
- 核心主张：
  1. OCS 用于 scale-out（DC 内）与 scale-across（DC 间），其落地受软件、供应、光学性能三方面约束 [p2][p3]。
  2. OCS 是协议/速率透明的 L0 交叉连接，不看帧不计包，"光在错误路径上也可能存在"；需要用成对图案化的 OCS 端口（每个接口期望不同对端）做并行的点对点验证，并以"意图→预检→编程→验证→提交，失败回滚"的事务方式变更 [p4][p7][p8][p9]。
  3. gNMI/gNOI/gNSI 公共 API 不够，OCP 需要一个强制的 OCS 生命周期 profile 和跨厂商一致性测试套件 [p6][p13]。
- 关键数据：
  - 1000 台近期产品的 1310nm 插损：中位约 1.2–1.4 dB，98 分位约 1.6–1.85 dB [p12]（看图）
  - 兼容 IL 预算：IEEE FR/FR4/FR8 4 dB；IEEE LR/LR4/LR8 6.3 dB；OIF ZR/ZR+ 11+ dB [p12]（自报）
  - Zero-touch 全生命周期：Day 0 信任设备、Day 1 验证 fabric、Day 2+ 维护；"任一阶段需要 console 就不算 zero-touch" [p5]（自报）
  - 量产：自动化光学对准、MEMS 封装、校准测试、外观检验；复用电信 WSS/传输线卡工艺 [p11]（自报）
  - OCP OCS 子项目双周三 9am PST 例会；SONiC OCS 工作组双周三 5pm PST [p14]（自报）
- 提到的公司/客户/产品/标准：Oracle OCI、Lumentum、OpenConfig、gNMI/gNOI/gNSI、SONiC、OCP OCS Sub-Project、IEEE FR/LR、OIF ZR/ZR+
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（1000 台 OCS 插损散点 + IL 预算兼容表）；p8（成对图案化 OCS 端口验证思路）

### P431 400G-lane-Optics-Module-Connectors
- 讲者/机构：Lightning Talks 合集：Sam Kocsis（Amphenol）[p2]；Terry Little（Foxconn Interconnect Technology, FIT）[p12]；Robbie Xu（Luxshare-Tech）[p21]；Matthew Ho（TE Connectivity）[p29] | 类型：技术分享（多厂商闪电演讲）
- 方向归属（主/次）：主 [Out：可插拔光模块]；次 [Up：铜缆/背板、CPO/NPO/XPO]
- 核心主张：
  1. 224G 以上的主要瓶颈是 ASIC 封装 BGA breakout 与可插拔 IO 性能；XPO 用 64 路高速通道、48V 单电源、集成液冷、MPO-16 兼容，并延续到 448G（Amphenol）[p4][p5][p9]。
  2. 448G XPO 保持 0.56 mm pitch 的 card-edge 形态，通过消除 stub 解决高频插损滚降；448G 需要同时支持 PAM6 和 PAM4（FIT）[p15][p20]。
  3. 448G 无源通道（CPC、背板、twinax、OSFP）已有样品，业界需决定 92 Ω 还是 85 Ω、PAM6 还是 PAM4（Luxshare）[p28]；现有 OSFP 缺乏通往 448G 的清晰路径，TE 提出 MegaLane 无 stub 接口（x8/x16/x32/x64）[p30][p31][p32]。
- 关键数据：
  - XPO：64 高速通道、电气热插拔、单 48V 供电、集成液冷、MPO-16 兼容、线性模块功耗 <90 W [p5]（自报）
  - XPO vs OSFP1600 接口 SDD21：80 GHz 处 XPO 约 -2.2 dB、OSFP1600 约 -3.4 dB [p7]（看图）
  - XPO 448G 接口 SDD21 在 0–120 GHz 内约 -0.5 至 -2 dB，约 122 GHz 后才急剧下降；224G 示例接口约 75 GHz 处滚降 [p10]（看图，Amphenol）
  - 448G 目标 Nyquist：PAM4 112 GHz；PAM6（5 bit/2 符号=2.5 bit/symbol）符号率 179.2 GBd、Nyquist 89.6 GHz，即 87–90 GHz；不含 FEC/编码开销 [p17]（自报/计算）
  - FIT 仿真差分阻抗：224G XPO 配合区 81.93 Ω、线缆焊接 85.04 Ω；448G XPO 89.00 Ω / 92.00 Ω [p16]（仿真）
  - FIT 仿真插损：80 GHz 处 224G XPO -1.32 dB vs 448G XPO -0.89 dB；224G 版本约 95 GHz 跌至 -10 dB，448G 版本约 112 GHz 仍在约 -2 dB [p17]（看图，仿真）
  - Luxshare OPTAMAX 448G twinax 31AWG 损耗：26.56 GHz 6.6 dB/m、56 GHz 10.0 dB/m、110 GHz 19.0 dB/m；92 Ω，带宽 >100 GHz [p22]（实验）
  - Luxshare 448G 通道仿真（2×300mm 31awg CPC-IO + 1m 27awg IO-IO，共 1.6m twinax，不含基板）：CPC-IO-CPC 损耗约 28 dB@106 GHz，回损 98 GHz 内低于 -15 dB，串扰一般低于 60 dB 水平 [p23]（仿真）
  - Luxshare CPC-背板-CPC 实测：90 GHz 内响应干净，约 110 GHz 才出现谐振 [p24]（实验）
  - NEXUS 448G 线缆背板 VH-VR：IL -0.8 dB@53 GHz、-1.8 dB@90 GHz；PSXT -80 dB@0–120 GHz [p26]（自报，原文未注明仿真/实测）
  - TE MegaLane SI（含 0.5mm 走线、模块卡 pad、连接器和 2mm 线缆）：阻抗约 92 Ω，插损 0–120 GHz 约 0 至 -1 dB，约 125 GHz 以后出现谐振 [p33]（看图，原文未注明仿真/实测）
- 提到的公司/客户/产品/标准：Amphenol、Foxconn Interconnect（FIT）、Luxshare-Tech（KOOLIO CPC、OSFP 448G Airchannel、OPTAMAX twinax、NEXUS 背板）、TE（AdrenaLINE MegaLane）、Arista（Andy Bechtolsheim）、XPO MSA、IEEE 802.3dv、OIF、OSFP1600、USFP（NVIDIA 与 Cisco 发布的新可插拔形态采用 TE MegaLane）[p34]
- 首次/记录/SOTA 声明：TE 称 USFP 采用 MegaLane [p34]；Luxshare 称 OPTAMAX 插损与弯曲性能"Leading the industry"、CPC "industry highest density" [p22]（均为自报）
- 推荐配图页：p10（10G→448G 各代可插拔接口 SDD21 对比 + XPO 爆炸图）；p17（224G vs 448G XPO card-edge 插损仿真与 PAM4/PAM6 Nyquist 标线）

### P432 Alternate-Scalable-AI-Interconnects
- 讲者/机构：Sean Park（Point2 Technology）、Dave Welch（AttoTude）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [Up：铜缆/背板、机柜级互连]；次 [Out：可插拔光模块]
- 核心主张：
  1. 在铜（短）和光（贵、耗电、可靠性差）之间存在 5–30 m 互连空档，可以用射频/ASIC 在介质波导（塑料）上传输来填补 [p2][p11][p13]。
  2. Point2 e-Tube：RF 通过塑料波导传输，无铜趋肤效应、无激光器，同一线缆可用于 224G/448G 及以上，并可做成近封装/共封装背板替代铜背板 [p4][p6]。
  3. AttoTude 主张 "ASICs over Dielectrics"，用 DiAx 介质线缆达到 10–30 m 且不需额外电子器件 [p10][p11]。
- 关键数据：
  - e-Tube 线缆相对铜：10 倍传输距离、材料成本低 10 倍、重量轻 5 倍、柔韧性高 2 倍 [p4]（自报）
  - 224G 现已可用，448G 预计两年内 [p4]（自报/预测）
  - e-Tube 背板：每机柜 GPU 数量 2–4 倍 [p6]（自报）
  - Scale-up 系统指标（路线图示意）：Beachfront Pluggable <1、NPE ~1、CPE ~2 Tb/mm；能效 Pluggable >4、NPE ~3、CPE ~1.5 pJ/bit；成本 Pluggable ~0.20、NPE ~0.15、CPE ~0.10 \$/Gbps [p7]（看图，预测）
  - Point2 融资 1.47 亿美元 [p3]（自报）
  - Twinax 可达距离：112G PAM4 7 m、224G PAM4 4 m、448G PAM4 <1 m；硅光纤 500 m 但上变频到 200 THz 代价为 5–7 pJ/bit、1000 倍故障率、30 倍成本；DiAx 10–30 m [p11]（自报）
  - 224G 在介质波导上：BER 2e-8，SNR 21.8 dB（实时 DSP 均衡）[p12]（实验）
  - AttoTude 路线图：224G、448G，至 896G；多 Tb/mm 线密度 [p9]（预测）
- 提到的公司/客户/产品/标准：Point2 Technology（e-Tube、1.6T OSFP ARC）、AttoTude（DiAx）、Andy Bechtolsheim（AttoTude 董事会顾问）[p8]、OSFP/QSFP-DD、DAC/ACC/AEC
- 首次/记录/SOTA 声明：Point2 称是业界首个 Active RF Cable（ARC，塑料波导射频传输）的开创者 [p3]（自报）
- 推荐配图页：p11（Twinax / 硅光纤 / DiAx 三类介质的距离与代价对比）；p7（Pluggable/NPE/CPE 三项指标对比）

### P433 CPO, OCI
- 讲者/机构：Rajiv Pancholy（Broadcom，Director Hyperscale Strategy & Products）[p1] | 类型：厂商技术分享 / 标准进展
- 方向归属（主/次）：主 [Up：CPO/NPO、机柜级互连]；次 [Out：交换芯片、OCS 之外的 CPO 交换]
- 核心主张：
  1. CPO 的核心价值在于 MTBF：链路抖动（link flap）会中断训练作业并回退到 checkpoint，CPO 可减少由此损失的训练时长 [p5][p6]。
  2. OCI（Optical Compute Interconnect）用于 scale-up：做到前面板可插拔的距离、铜缆的功耗 [p13]；OCI-MSA 于 2026-03-12 成立，GEN1 规范已发布 [p11]。
  3. CPO/OCI 规模化的难点在先进封装（PIC-EIC 互连、400G 直驱）、光连接（每封装超过 1k 根光纤、可拆卸以便回流焊）和自动化量产 [p7]。
- 关键数据：
  - Broadcom CPO 代际：2022 TH4 Humboldt 25.6T 100G/lane；2024 TH5 Bailly 51.2T 100G/lane；2026 TH6 Davisson 102.4T 200G/lane；2028 第 4 代 CPO 研发中 [p4]（自报）
  - >1M 器件小时 0 次 link flap [p4]（自报，未给条件）
  - CPO 相对可插拔可靠性提升 10 倍 [p3]（自报）
  - "90% Efficiency Improvement"（CPO scale-out vs 可插拔光模块，训练作业示意）[p6]（自报，口径未说明）
  - 200G 链路总功耗与距离：DAC 7 pJ/bit、2 m；Integrated OCI 7 pJ/bit、500 m；DR LRO 前面板可插拔 23 pJ/bit、500 m [p13]（看图，自报）
  - 1024 XPU scale-up 集群：每 XPU scale-up 带宽 25.6 Tbps，交换机 204.8 Tbps；每机架 64 GPU / 32 交换机；共 16 个 GPU 机架、4 个交换机机架；1024 GPU、128 交换机；每 GPU 128 根光纤（Bi-Di），每交换机 1024 根；每机架 8,192 / 32,768 根光纤 [p14]（自报，设计示例）
  - 单层 scale-out 连接 1024 个 scale-up POD × 1024 = 1,048,576 XPU，借助 ESUN 统一 scale-up/scale-out 消息 [p15]（自报，概念架构）
  - OCI-MSA GEN1：Bi-Di Group A/B 波长实现，在 CWDM 网格上用 DWDM 通道做 Bi-Di [p12]（自报）
- 提到的公司/客户/产品/标准：Broadcom（TH4 Humboldt、TH5 Bailly、TH6 Davisson、COUPE）、ELSFP、FAU、OCI-MSA、ESUN
- 首次/记录/SOTA 声明：CPO 第 4 代（Broadcom 自报代际）；">1M device hours with 0 link flaps" [p4]
- 推荐配图页：p13（DAC/OCI/LRO 200G 功耗与距离对比表）；p14（1024 XPU 光 scale-up 集群光纤计数表）

### P434 CPO-solution-for-AI-that-checks-all-the-boxes
- 讲者/机构：Tom Palkert（Samtec，OpenCPX MSA 创始成员）[p1] | 类型：标准进展（MSA）
- 方向归属（主/次）：主 [Up：CPO/NPO]；次 [Out：可插拔光模块/LPO]、[Up：铜缆]
- 核心主张：
  1. Samtec、Ciena、Coherent、Terahop、Marvell、Molex 组成 OpenCPX MSA，提供高密度、高带宽、现场可更换且兼容铜缆的 CPO/NPO 方案 [p2]。
  2. CPO/NPO 的好处是更少 link flap、更低功耗、更好信号完整性和机械连接，同时支持 DAC/ACC/AEC 和单模/多模光 [p3][p4][p5]。
  3. 用 NPO 基板扇出：基板材料插损比封装低、成本低，支持更大 beachfront，线性接口仍可工作 [p9]。
- 关键数据：
  - 引用 Meta OCP 2025：CPO 1500 万器件小时，不可服务故障 MTBF >15M；2x400G 可插拔 200 万器件小时，MTBF 0.55M [p6]（引用 Meta OCP 2025）
  - 引用 Meta/Broadcom OFC2026：3600 万器件小时，75% 端口 FEC bin <4 [p6]（引用）
  - CPO/NPO 相对 DSP 可插拔节省 65% 功耗 [p7]（引用 OFC2026 M4B.6）
  - 能效：硅光 3.8 pJ/bit，VCSEL 1–1.9 pJ/bit [p7]（自报）
  - 主机通道损耗 15 dB vs 32 dB（CPO vs 可插拔）；ERL 10 dB vs 8.5 dB [p8]（自报）
  - NPO 基板 IL <15–18 dB 时线性接口仍可工作 [p9]（自报，来源 Broadcom OCP 2025）
  - 基板 SDD21：60 GHz 约 -2 dB，100 GHz 约 -3 至 -4 dB，120 GHz 约 -3.5 至 -4.3 dB；SDD11 位于模板之下 [p10]（看图，引用 Broadcom ECOC 2026）
  - CPX 连接器 32 或 36 lane，两种连接器/模块类型可选独立或集成供电；支持 Ethernet、OCI、PCIe/CXL 或私有接口 [p13]（自报）
  - 可组合交换托盘：204.8T 级，512 × 400G 或 1,024 × 200G 端口；面板可插拔与 CPO 同在一个 tray contract 下；1RU 200T 以上密度 [p14]（看图，翻拍照片）
  - 产品时间：2026 Q3（展会现场展示）[p15]（自报）
- 提到的公司/客户/产品/标准：Samtec（Si-Fly HD）、Ciena、Coherent、Terahop、Marvell、Molex、Meta、Broadcom、Oracle、OpenCPX MSA、OCI、PCIe/CXL
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（Meta CPO vs 可插拔 MTBF 引用数据）；p14（204.8T 可组合交换托盘，铜 flyover 与光同托盘）

### P435 External-Laser-Source-Architectures-for-Deployable-CPO-Based-AI-Networks
- 讲者/机构：Christian Urricariet（Lumentum）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [Up：CPO/NPO]；次 [运维/可靠性/遥测]
- 核心主张：
  1. CPO 的问题已从"能不能用"转为"能不能运维"；在 AI 规模下，可靠性和服务模式与能效同样重要 [p2]。
  2. 激光器位置是独立于 OE 位置（可插拔/NPO/CPO）的另一架构维度：与 OE 共置（ILS）、板级 ELS、面板 ELSFP 各有取舍，核心权衡是光功率输送复杂度 vs 可服务性、热隔离、故障隔离 [p4]。
  3. 提出超越 pJ/bit 的部署指标：光功率输送、热包络、可靠性目标（FIT）、可服务性（FRU 边界）、遥测/RAS、恢复域（MTTR）[p6]。
- 关键数据：
  - 每端口功耗：可插拔约 30 W → CPO 约 9 W，约 3.5 倍改善 [p2]（自报，Lumentum 示意估计）
  - Lumentum DWDM UHP/ELSFP 激光：50°C 下出光 >350 mW（约 1.3 A 达 400 mW）[p7]（看图，实验）
  - 50°C 下电光转换效率 >20%（峰值约 25–29%）[p7]（看图，实验）
  - 150–400 mW 范围内线宽 <500 kHz [p7]（看图，实验）
  - NVIDIA 已宣布基于 ELS 的 CPO Spectrum-X / Quantum-X 交换机 [p8]（引用）
- 提到的公司/客户/产品/标准：Lumentum、NVIDIA（Spectrum-X、Quantum-X）、OIF ELSFP IA、OCI MSA、Open-CPX MSA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（ILS / 板级 ELS / 面板 ELSFP 三种激光位置对比）；p7（UHP 激光 L-I、PCE、线宽实测图）

### P436 High-Speed-Open-Silicon-Photonics-Reference-Designs
- 讲者/机构：Janos Veres（Flex）、Bijan Nowroozi（Lightmatter）[p1] | 类型：标准进展 / 技术分享
- 方向归属（主/次）：主 [Up：CPO/NPO/XPO]；次 [底座-机架/机械]、[运维/可靠性/遥测]
- 核心主张：
  1. 架构在纸面上能闭合，量产就绪不能；CPO 公差跨越六个数量级（亚微米到米），需要晶圆厂、OSAT、组装各方协作 [p2][p3]。
  2. 可拆卸 FAU（垂直、多排）在良率、UPH、已知良好 OE、可服务性上优于边缘单排固定方案，代价由光纤密度支付 [p6][p7]。
  3. 缺的不是元件而是"契约"：为 photonics-ready MHS 托盘定义开放的机械/电气/供电/热/管理契约，"标准化契约，在实现上竞争" [p12][p13]。
- 关键数据：
  - 封装边缘光纤：8 个 dFAU 768 根数据光纤 154–614 Tb/s/dir；4 个 dFAU 384 根 77–307 Tb/s/dir；2 个 dFAU 192 根 38–154 Tb/s/dir（光纤数含激光馈纤）[p6]（自报/计算）
  - 交换侧边缘密度按 OIF EEI：CPO 2.0、铜 1.0 Tb/s/mm 双向，可用分别为 0.9 和 0.5 [p6]（引用 OIF EEI）
  - 封装边缘 escape：CPO 0.9、NPO 0.25 Tb/s/dir per mm；CPO 把"墙"外推约 3.6 倍 [p16]（自报/计算）
  - PPK（2D MCP + V 槽）：56G NRZ/112G PAM4/224G PAM4；平均端面插损 1 dB；181 个 FAU <2 dB 良率 99.5%；封装测试 99.5%（500+ 单元）[p8]（看图，实验）
  - 多 reticle ATV（4000 mm² 3D chip on wafer，边缘贴装）：平均端面插损 1.5 dB；62 个 FAU，<2 dB 光耦合良率 95% [p8]（看图，实验）
  - 单 reticle ATV：IL <1.5 dB、良率 >99% [p8]（看图，仿真）
  - 构建流程 L0–L11 与合规门；进度风险集中在 L4（JEDEC 认证）和 L10（UL/NEBS 认证）[p20]（看图）
  - 时间线：白皮书 "Architecture Vision: Open Silicon Photonics for AI Systems" Release 1.x 于 8 月 10 日发布（v1.0.3，2026 年 7 月）；规范草案持续到 2027；社区愿景 2026-03-16 公布 [p13][p19][p21]（看图/自报）
- 提到的公司/客户/产品/标准：Flex、Lightmatter、OCP MHS（Interconnect-for-AI workstream）、ORv3、XPO、IEEE 802.3 DR、OCI、NVLink/UALink、UEC、CXL、ESUN、OCP RAS、OIF CMIS、BoW、UCIe、CPX、ELSFP、DC-SCM
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（三种 FAU 测试载体的良率/插损实测）；p12（FPO/NPO/CPO 契约维度对照表）

### P437 Integrated-Optics-at-Scale-for-AI-Infrastructure-From-51.2T-CPO-Validation-to-Meta-s-102.4T-Integrated-Optics-Switch
- 讲者/机构：Granthana Rangaswamy、Siamak Amiralizadeh、Xu Wang（Meta）[p1] | 类型：技术分享（运营方数据）
- 方向归属（主/次）：主 [Up：CPO/NPO]；次 [Out：交换芯片、可插拔光模块]、[运维/可靠性/遥测]
- 核心主张：
  1. Meta 用 A/B 方法比较 51.2T CPO 交换机与基于可插拔的 Minipack3（对照组），CPO 端口可靠性高于全重定时可插拔（FRO）端口 [p3][p6]。
  2. Pre-FEC BER 单独作为链路健康指标不可靠：CPO 的 pre-FEC BER 更差，但故障率更低 [p5]。
  3. 下一步是 102.4T CPO/NPO 产品；CPO 与 NPO 各有取舍，NPO 在 448G/lane 时线性驱动可能需要 retimer [p7][p8]。
- 关键数据：
  - 累计 >1.8M 系统小时的 RAS 数据 [p3]（现网/实验）
  - FRO 2x400G FR4，40°C，1,792 个 400G 端口，8M 器件小时；CPO Phase 1（128x400G FR4），40°C，8,960 端口，50M 器件小时；CPO Phase 2，15–35°C，38,400 端口，175M 器件小时 [p3]（实验）
  - 故障分类：ELS 模块占 CPO Phase 1 85%、Phase 2 83%（根因为激光驱动 SMT 元件，已修复）；光纤/连接器 11%/17%/FRO 9%；OE 硬件 4%/0%/FRO 18%；FRO 光 DSP 固件 36%、瞬态/未知 37%，CPO 两项均 0% [p4]（实验）
  - 年链路中断率 ALIR / MTBI：FRO 1.22% / 0.72M；CPO Phase 1 0.47% / 1.85M；CPO Phase 2 0.2% / 4.5M；排除 ELS SMT 故障 0.04% / 25M；不可服务中断 0 / 175M [p6]（实验）
  - Phase 2 CPO 1.35M 系统小时内无不可服务故障 [p6]（实验）
  - 平均 pre-FEC BER：CPO ~9e-8，FRO ~1e-9；以单个不可纠正码字（UCW）定义中断 [p5]（实验）；CPO 失败与健康链路的 BER 分布大幅重叠 [p5]（看图）
  - 102.4T 目标：兼容 retimed 可插拔（TP2/TP3），CMIS 5.3，规格距离 500 m、可支持到 2 km，比 retimed 可插拔节省 60% 光学功耗 [p7]（自报/预测）
  - 102.4T 交换机：1.5OU，64 数据端口（16x4 MMC16 连接器），16 个 ELSFP 端口；ORv3-HPRv1 机架；因灰尘污染风险 100% 液冷（ASIC、CPO/NPO、ELSFP）；RunBMC 复用自 Minipack 3 [p10]（自报）
  - 机架演进：ORv3 HPR ≤72 加速器；MP ORW（2026-Q3）≤144 加速器；下一步 ≥256 加速器，主要液冷 [p2]（自报）
- 提到的公司/客户/产品/标准：Meta（Minipack3、ORv3 HPR、ORW）、OIF ELSFP、CMIS 5.3、MMC16、TP2/TP3、Drew Alduino et al. JLT 2026、Amiralizadeh et al. ECOC 2025
- 首次/记录/SOTA 声明：无明确"首次"；"51.2T CPO shows significantly better reliability than pluggables in our evaluation" [p15]
- 推荐配图页：p6（FRO vs CPO ALIR/MTBI 表）；p12（102.4T 集成光交换机前面板实物，MMC16 + ELSFP）

### P438 Lessons-learned-from-GW-scale-AI-deployments
- 讲者/机构：Mark Filer（Oracle Cloud Infrastructure）[p1] | 类型：技术分享（运营方数据）
- 方向归属（主/次）：主 [Out：可插拔光模块/LPO/LRO]；次 [Up：CPO/NPO]、[运维/可靠性/遥测]
- 核心主张：
  1. 下一代网络要解决的是 TCO：网络可用性、功耗、资本开支；网络相对计算的支出占比逐年上升，不可持续 [p5]。
  2. 800G LPO 大规模部署数据表明线性驱动接口不带来性能惩罚，反而链路更稳定，系统级功耗节省因散热负担下降而放大 [p6][p7][p8]；1.6T 时 LPO 难以满足 SI 和互通，LRO 是当前最佳低功耗方案 [p9]。
  3. 污染是链路故障主因，扩束（expanded beam）连接器几乎消除这一故障源 [p11][p12]。
- 关键数据：
  - Oracle AI 集群规模：16,384 → 32,768 → 65,536 → 131,072 GPU（2020–2026，8 倍）[p2]（自报）
  - NIC 速率 2017 年 25 Gbps 到 2026 年 1600 Gbps，网络集群性能提升 256 倍 [p3]（自报）
  - 污染相关占链路问题 90% [p4]；90% 的 L1 链路故障与污染有关，97% 的光模块更换源于污染 [p11]（现网）
  - 800G 24 小时最大 pre-FEC BER（T0<>T1）：LPO–LPO 156,591 条链路，中位 1.137e-11，p99 5.165e-10；FRO–FRO 202,042 条，中位 1.432e-11，p99 2.888e-8 [p6]（现网）
  - 纠正符号率中位：LPO 3.1e-8 / 码字，FRO 1.6e-7，约 5 倍 [p7]（现网）
  - 1 个月内至少一次 down transition 的链路比例：LPO–LPO 3.244%（n=1,022），FRO–FRO 5.681%（n=899），FRO 为 1.75 倍 [p7]（看图，现网）
  - 64x800G 交换机 24 小时平均功耗中位：全 FRO 1,528 W（n=2,184），半 LPO/半 FRO 1,270 W（n=1,237），净省 258 W；模块贡献 32×~6 W=192 W，额外 66 W 来自风扇功耗下降 [p8]（现网，样本数看图）
  - 1.6T LRO：26 dB 通道，16 W（10 pJ/bit）；支持 DR4+（4 dB）与 FR4；FEC bin p50/p95：LRO 1/2，FRO 1/1；已演示多厂商 3nm DSP 互通，预计 2nm 进一步降功耗 [p9]（自报/现网）
  - CPO/NPO：相对全重定时可插拔预计最多省 50% 功耗（200G/lane 代）、理论 30%+ 成本节省 [p10]（引用 NVIDIA 博客、SemiAnalysis）
  - 扩束连接器无物理接触，插拔力约降 20 倍，可用于大规模 ganged 插接/光背板 [p12]（自报）
- 提到的公司/客户/产品/标准：Oracle OCI（Acceleron 多平面网络）、Meta（引用）、Ciena（NPO 图源）、Broadcom（CPO 图源）、NVIDIA、SemiAnalysis、PRIZM TMT、EBO MSA、OpenCPX MSA、OIF
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（LPO vs FRO 纠正符号率 CDF 与 flap 比例）；p8（64x800G 交换机全 FRO vs 半 LPO 功耗分布直方图）

### P439 Light-on-the-Horizon-Architecting-Scale-Up-Fabrics-with-NPO-CPO-for-the-Next-Gen-Data-Center
- 讲者/机构：Chris Blackburn、Jignesh Shah（Astera Labs）[p1] | 类型：厂商技术分享
- 方向归属（主/次）：主 [Up：UALink/ESUN、铜缆/背板、CPO/NPO]；次 [推理/算力/经济性]
- 核心主张：
  1. Scale-up 规模从 8–72 XPU/pod 走向 144–1000+，速率从 200G/lane 走向 400G+/lane，电通道距离缩短，scale-up fabric 成为一阶设计约束 [p3]。
  2. 铜不会消失：机柜内和相邻机柜继续用铜（必要时 retimer/redriver 延伸），机柜间与跨 pod 用线性光、NPO、CPO；训练集群偏光、推理集群偏铜 [p5][p7][p12]。
  3. 近期多机柜 scale-up 适合 NPO（可服务、复用现有生态），CPO 面向下一代高 radix 交换/XPU 平台 [p11]。
- 关键数据：
  - Pod 超过 144 GPU 时物理距离需要光的覆盖 [p8]（自报）
  - 各互连距离/功耗：Passive DAC ≤3 m；ACC ≤4 m；AEC ≤7 m；AOC/LPO/NPO/CPO >50 m；其中 CPO 功耗最低、AOC 功耗与时延最高 [p8]（看图，定性）
  - 混合铜/光 pod：机柜内铜背板 + 机柜间 NPO，面向 72–576 加速器；全光 pod 用 NPO/CPO，面向 >576 加速器 [p14]（自报）
  - 模型规模每 12–18 个月翻倍 [p2]（自报）
- 提到的公司/客户/产品/标准：Astera Labs、NVLink、PCIe 6/7/8、UALink、ESUN、DAC/ACC/AEC/AOC/LPO
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（七种互连的距离/功耗/时延对比图）；p14（混合铜光 pod vs 全光 pod 架构）

### P440 Open-NPO-Standards-Building-the-Optical-Interconnect-Ecosystem-for-SuperPOD
- 讲者/机构：Qirui Fan、Weiqiang Xu（Huawei，标准代表）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [Up：CPO/NPO/XPO、机柜级互连]；次 [底座-机架/机械]
- 核心主张：
  1. 在 "Tao (τ) Scaling Law"（时间维度的缩放）下，超节点需要线性高密度光互连来降低信号传播时延 [p3]。
  2. NPO 已被中国互联网企业、运营商和系统厂商广泛选作超节点光互连的主要方案，优点是易维护、芯片与 OE 解耦、工艺要求低、供应链就绪 [p4]。
  3. NPO 推广的核心瓶颈是电连接器缺乏统一方案；OPEN NPO 项目先统一电连接器，并分阶段定义 Type 1/Type 2 接口和 OIO 光接口 [p5][p7]。
- 关键数据：
  - OPEN NPO 由 Open AI Infra 社区发起：2026.6 筹备，2026.7 启动；社区示意 300+ / 200+ / 40+ 成员 [p6]（自报，三类成员对应关系看不清）
  - 路线：~2025 兼容 LPO-800G（800G@112G/L）；Phase I 2026–2027 Type 1 电接口（xxT @224G/L、集成光源架构）；Phase II 2027–2028 Type 2 高密度电接口（3D 小型化、1000+ radix）；Phase III 2029–2030 定义 OIO 光接口 [p7]（预测）
  - Type 1 连接器与 NPO 模块样品正在测试 [p7]（自报）
  - 连接器 pinmap：72 差分对（36 通道）+ 96 个电源/低速引脚；差分对占中间 12 列 [p12]（自报）
  - 机械：总插入力 ≤150 N；初始拔出力 ≥20 N，最大 80 N；耐久 50 次；瞬时承压 ≥380 N，长期 ≥183 N [p13]（自报，规范）
  - 电气：1 A/pin、12 V DC；阻抗 80–90 Ω；IL ≤1.5 dB@10 MHz–56 GHz；ERL ≥11 dB（按 OIF CEI-224G-Linear）；NEXT ≤-50 dB@10 MHz–56 GHz、≤-45 dB@56–67 GHz；FEXT ≤-45 dB / ≤-40 dB；额定电流温升 30°C [p14]（自报，规范）
  - 实测：插损（含测试板）56 GHz 约 -7.5 dB、67 GHz 约 -10 dB；阻抗（含测试板）约 86–91 Ω；去嵌 NEXT 0–40 GHz 约 -55 至 -70 dB [p15]（看图，实验）
  - 场景 1（2027–2028）：L1↔L2 交换机间，NPO 使网络交换容量翻倍；场景 2（2028–2029）：XPU 在大型扁平 POD 中经 NPO 直接出光 [p16]（预测）
  - 首批贡献时间 2026.12.30 [p17]（自报）
- 提到的公司/客户/产品/标准：Huawei、Open AI Infra 社区（gccorg）、OIF CEI-224G-Linear、LPO-800G、QDD
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（OPEN NPO 三阶段路线图）；p14（连接器电气规范表）

### P441 Open-Optical-Connectivity-Solutions-for-AI-Scaling
- 讲者/机构：Rang-Chen (Ryan) Yu（TeraHop，VP Marketing）[p1] | 类型：厂商技术分享 / 标准进展
- 方向归属（主/次）：主 [Up：CPO/NPO/XPO]；次 [Out：可插拔光模块]、[Across：多芯光纤]
- 核心主张：
  1. 开放光学方案对 AI 的 scale-up/out/across 都关键；XPO（高容量可插拔）、Open CPX（开放插座的 CPO/NPO 引擎）、SDM4 MCF 三个 MSA 分别覆盖 [p2][p4][p20]。
  2. TeraHop 主张 NPO 采用集成激光（ILS）而非 ELSFP：ELSFP 多损失 >3 dB，需要 2 倍以上 CW 激光功率，带 TEC 时激光功耗约 4 倍，还有 PM 光纤和盲插连接器的损耗与故障点 [p14]。
  3. "慢而宽"光学（如 50G NRZ）可省去 PAM4 DSP，但通道数增加 4 倍；用 4 芯 MCF 比 4 波 DWDM 更省功耗和成本 [p19]。
- 关键数据：
  - XPO MSA：OFC 2026 发布 12.8T，100+ 公司加入，Release 1.0 于 2026-07-31 发布；相对 OSFP 8 倍容量、4 倍面板密度 [p4][p6]（自报）
  - Open CPX MSA：OFC 2026 发布，50+ 公司，Release 1.0 于 2026-09-17 发布 [p4]（自报）
  - Open CPX 路线：Rev 1.0（2026.9）32/36×200G，Type 1&2，ILM & ELM；Rev 1.1（2027.3）铜介质、Type 3；Rev 2.0（2027.6）64/72×200G；Rev 3.0（2027 末/2028 初）N×400G [p9]（看图，预测）
  - 12.8T XPO-FRO：8 x 1.6T-DR8，64 路发射；CW 激光温度在 0.3 LPM 时：25°C 进液约 36–41°C、45°C 进液约 53–57°C；模块功耗在 45–55°C 进液、0.3–0.5 LPM 下约 197–202 W [p7]（看图，实验）
  - 12.8T XPO-RTLR 演示：估计通道损耗 ~22 dB；多数通道 BER 1e-13 至 1e-11 量级，最差 CH12 1.33e-10 [p8]（看图，实验）
  - "Diablo-1" 6.4T NPO 初步测试：ER=3 dB，TECQ=2.1 dB；ASIC 到 NPO 插损约 12 dB [p13]（实验）
  - Diablo-1 功耗约 5.5 pJ/b（含内部激光）[p14]（自报）
  - ELSFP 方案需 CW 激光功率 200–300 mW+ [p14]（自报）
  - 硅光 PIC 现场 >100B 器件小时，FIT <0.01 [p16]；曲线显示累计器件小时 21Q1 约 1e7 到 26Q2 约 1.4e11，FIT 从约 100 降到约 0.01 以下 [p16]（看图，现网）
  - CW LD 供应商 E FIT <0.01，供应商 A FIT <0.03 [p17]（自报）
  - SDM4 MCF MSA：2026-03-11 成立，Release 1.0 于 2026-09-17 发布；4 芯（2x2），每根光纤容量 4 倍，O 波段短距 [p18]（自报）
  - 4 波 DWDM 需要光复用（约 3 dB 损耗）；4 芯 MCF 无需 WDM 复用，成本按 4 芯 MCF ≈ 4× SMF 假设 [p19]（自报）
- 提到的公司/客户/产品/标准：TeraHop（Diablo-1、1.6T-DR8 OSFP、800G-MCF）、Arista（100T 交换机设计概念）[p15]、Intel（集成激光 PIC，引用）、Corning、AFL、Sumitomo、OIF（ECOC 2026 演示）、XPO MSA、Open CPX MSA、SDM4 MCF MSA、ELSFP
- 首次/记录/SOTA 声明："Industry 1st 100Tbps switch Design-Concept by Arista, with TeraHop 6.4T Diablo-1 Open CPX Engine" [p15]（自报）；XPO 称 "Highest capacity and density pluggable" [p4]（自报）
- 推荐配图页：p9（Open CPX MSA 2026–2028 规范路线图）；p16（硅光 PIC 累计器件小时与 FIT 走势）
