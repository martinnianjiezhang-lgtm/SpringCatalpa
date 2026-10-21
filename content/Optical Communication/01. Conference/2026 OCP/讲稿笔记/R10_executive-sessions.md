---
title: "R10_executive-sessions"
tags:
  - OCP2026
  - 讲稿笔记
---

# R10 笔记：executive-sessions, cooling-environments, cooling-immersion

> 说明：本批 13 份。与 AI 网络/互连强相关的是 P237（224G AEC）、P238（XPO）、P243（Astera Orion 机柜级 PCIe scale-up）、P244（Meta 全栈开放网络），写完整版；P240、P242 为厂商主题演讲，写中等版本；冷却（P219、P222、P228、P229、P235、P236）和电力（P246）按规则 4 写精简版，P228/P229/P235 数据较多，略写全一些。图片转写见 cloud_text/R10.md。

### P237 01_224G AECs for AI Data Centers Extending Reach, Enhancing Telemetry, an
- 讲者/机构：Clay Miller（Molex，Sr. Manager New Product Development）；Rajesh Annapillai（Broadcom，Physical Layer Products 产品市场）[p1] | 类型：厂商主题演讲（Executive Session，Networking）
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板]（224G/lane AEC）；次 [运维/可靠性/遥测]（retimer 实时诊断、CMIS 信道建模）
- 核心主张：
  1. 224G/lane 下要做到 6m+ AEC，需要把 retimer、封装、paddle card、twinax 每一段联合优化，涉及插损、串扰、对内 skew、反射、电源噪声 [p7, p15]。
  2. 传统 skew 指标（TDR/TDT、原始 VNA）在 200G+ 失效，改用 EIPS（时域 + 频域加权积分）和 CMC mask 分段约束 [p8, p11]。
  3. Broadcom 给线缆厂提供共享 paddle card 基线；retimer 两端实时遥测，并通过 CMIS 做实时信道建模，以降低超大规模用户的 TTM 和运维成本 [p11–p13, p15]。
- 关键数据：
  - 112G AEC 常见部署长度 1–7 m（看图）[p2]
  - 224G/lane 铜缆 BER 分档：DAC 仅短距 "Excellent"；ACC 短距 Excellent、较长 Limited；AEC 在 1–6 m 全段 Excellent（自报，档位划分以图为准）[p5]
  - 功耗测算：每柜 4 GPU tray × 18 端口 = 72 端口，25% 无源/75% 有源（54 个有源端口）；5,000 柜 = 270,000 个有源模块；AOC 25 W/模块 → 6.75 MW，AEC 18 W/模块 → 4.86 MW，功耗降低 28%，省 1.89 MW（仅模块功耗，不含其他 IT 和冷却；自报估算，看图）[p3]
  - AEC 出货预测：800G AEC 2025 年 1.74M 件；1.6T AEC 2027→2030 从 1.37M 增至 8.85M（6.5×）；2030 年 1.6T 首次超过 800G（引用 LightCounting Cloud Data Center Optics Database, 2026-07-30）[p6]；800G 在 2027 年约 11.4M 达峰后回落到约 8M（看图估计）[p6]
  - 长 twinax（3m+，紧耦合）skew 要求 < 0.5 ps mask（自报）[p8]
  - retimer 与 Broadcom Tomahawk 交换机同一 SerDes，>45 dB 插损能力（自报）[p9]
  - 1.6T AEC 6.5 m 线缆仿真 pre-FEC BER：7 个 TX 通道都落在约 3E-10 ~ 7E-10，双向一致（仿真，看图）[p10]
  - AGERA 产品线：400G/800G AGERA2LP 5nm（TH5 SerDes，>45dB，8m+，量产）；1.6T AGERA3/3U 3nm（TH6 SerDes，>45dB，6m+，量产）；3.2T AGERA4 2nm（400G SerDes，>40dB，即将推出）（自报，看图）[p14]
  - 遥测项：每通道 pre-FEC BER、SNR、EMAX、FEC tail 帧错统计、功耗与温度，近端 + 远端（自报）[p12]
- 提到的公司/客户/产品/标准：Molex、Broadcom、Tomahawk5/Tomahawk6、AGERA2LP/AGERA3/3U/AGERA4、LightCounting、IEEE CR mask、EIPS（S.-J. Moon et al., IEEE SPI 2021）、CMIS
- 首次/记录/SOTA 声明："Industry's 1st AEC Retimer supporting lowest pJ/b, while extending 1.6T cable reach to 6m+"（自报）[p14]
- 推荐配图页：p3（AOC vs AEC 5,000 柜功耗对比）；p6（800G/1.6T AEC 出货预测曲线）；p14（AGERA 400G→3.2T 产品路线）

### P238 02_A High-Density, Liquid-Cooled Optical Interconnect Architecture for Ne
- 讲者/机构：Terry Little（Foxconn Interconnect Technology，Sr. Development Engineering Manager）[p1] | 类型：厂商主题演讲（Photonics track）
- 方向归属（主/次）：主 [Out 后端网络：可插拔光模块/LPO/LRO]（XPO 高密可插拔）；次 [Up 机柜/超节点：CPO/NPO/XPO]、[底座-冷却]（模块内集成液冷）
- 核心主张：
  1. XPO 把 8 个 OSFP 的高速信号、电源、边带合并进一个可插拔模块，并在模块里集成液冷冷板，提高前面板密度 [p4, p5]。
  2. XPO 与光技术无关，可承载 LPO、LRO、DSP、retimed 和硅光模块，单模/多模均可，光器件留在交换机外的插拔模块中 [p8]。
  3. 保持 0.56 mm 节距 card-edge 外形不变，从 224G 演进到 448G（PAM4/PAM6），新接触几何减少 stub 以改善高频插损 [p2, p16, p20]。
- 关键数据：
  - 每个 XPO 模块：224G 信号下 12.8 Tbps，448G 下 25.6 Tbps（自报）[p4]
  - 高速信号节距：OSFP 0.60 mm，XPO 0.56 mm（自报）[p4]
  - 前面板：8 个 OSFP 约 190 mm × 16.5 mm；1 个 XPO 约 60.79 mm × 21.10 mm；按 RU 计约 4× 端口密度（自报）[p5]；示意图对比 1OU 128 个 XPO 端口 vs 2RU 64 个 OSFP 端口（看图）[p5]；128 端口 1OU 方案仍"在慎重考虑"[p5]
  - 连接器 128 对差分（64 Tx / 64 Rx），8 片 wafer 堆叠 [p9]
  - 30/32 AWG 无漏线 twinax，92 Ω 受控阻抗，插损目标覆盖到 112 GHz（自报）[p10]
  - 冷板热仿真（1×2 并联，200 W）：最大流量 0.4 L/min 时压降 34.63 kPa（5.02 PSI）/ 36.44 kPa（5.29 PSI），模块最高温 64.49 ℃（规格 < 70 ℃）（仿真）[p11]
  - 冷板爆破仿真：C10200 铜，200 psi 内压，最大 von-Mises 应力 30.87 MPa（屈服 49.8 MPa），最大形变 1.136 μm（仿真）[p12]
  - OFC 2026 现场演示：去嵌夹具后环回实测 −3.93 dB @53.125 GHz，减去 300 mm 环回线 −3.0 dB 得 −0.93 dB，每个连接器界面约 −0.465 dB IL（实验，看图）[p13]
  - 224G 环回 BER（8 对差分，EXFO BA-1600）：pre-FEC 1.07E-12 ~ 7.25E-10，post-FEC 全部为 0（实验）[p14]
  - 448G 仿真差分阻抗：224G 设计 81.93 Ω / 85.04 Ω，448G 设计 89.00 Ω / 92.00 Ω [p17]
  - 448G 仿真插损：67 GHz 处 224G XPO −0.94 dB vs 448G XPO −0.59 dB；80 GHz 处 −1.32 dB vs −0.89 dB；224G 设计约 85 GHz 后急剧滚降，448G 设计到 112 GHz 约 −2 dB（仿真，看图）[p18]
  - 448G 带宽目标：PAM6（2.5 bit/symbol）179.2 GBd，Nyquist 89.6 GHz，目标 87–90 GHz；PAM4 目标 112 GHz（未计 FEC/编码开销）[p18]
- 提到的公司/客户/产品/标准：Foxconn Interconnect Technology（FIT）、Arista（致谢 Andy Bechtolsheim）、XPO MSA、IEEE 802.3dv、OSFP、EXFO BA-1600、Wilder Tec、LPO/LRO/硅光
- 首次/记录/SOTA 声明："Today, we are proud to introduce our XPO platform"（FIT 发布 XPO 平台，自报）[p2]
- 推荐配图页：p5（1OU 128 XPO vs 2RU 64 OSFP 前面板对比与尺寸）；p18（224G vs 448G XPO 插损仿真曲线）；p14（224G 环回 BER 表）

### P240 04_Accelerate your AI journey with QCT From system-level to AI Factory pr
- 讲者/机构：Jack Luoh（QCT/Quanta，Head of Product Marketing）[p1] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]（tokens per watt）；次 [底座-电力]、[运维/可靠性/遥测]（数字孪生）
- 核心主张：
  1. 推理、agentic AI、长上下文推高每任务 token 数，电力成为约束，目标从"更多算力"转为"每瓦更多 token"[p2, p5]。
  2. 按负载匹配架构：Vera CPU Rack（agentic/RL）、Vera Rubin NVL72（训练/推理）、BlueField-4 STX 存储（KV cache 复用）、Groq 3 LPX（低时延推理）、Spectrum-6 SPX 网络 [p7–p10]。
  3. 借 NVIDIA DSX（DSX Sim/Flex/Exchange、Omniverse、MaxLPS）做 AI 工厂数字孪生，覆盖设计、建设、运营 [p6, p13–p15]。
- 关键数据：
  - 全球 AI 数据中心电力容量 2025Q4 约 31 GW（引用 EPOCH AI）[p4]
  - 约 40% 设施电力直接给 GPU；服务器总功耗为 GPU 的 1.53×，IT 设备为服务器的 1.14×（引用 EPOCH AI）[p4]
  - 2030 年数据中心总需求 490.7 GW vs 电网可供 222.6 GW，缺口约 268 GW（引用 EPOCH AI，预测）[p4]
  - 2026 年累计 AI 算力约 30M H100e（引用 EPOCH AI）[p5]；柱图 2026Q2 约 31M H100e（看图）[p3]
  - 已披露 AI token 量 300T+/天（引用 "Tokens Per Day"）[p5]
  - GB200 NVL72 数据中心峰值电力分布：GPU 41%、其他服务器部件 22%、网络与其他 IT 8%、冷却与设施开销 29%（引用 EPOCH AI，估算）[p11]
  - Vera CPU Rack 支持 22,500+ 并发 CPU 环境（沙箱执行、工具调用、RL 评估）（自报）[p9]
- 提到的公司/客户/产品/标准：QCT/Quanta、NVIDIA（DSX、Vera Rubin NVL72、Vera CPU、BlueField-4 STX、Spectrum-6 SPX、Omniverse、NVAIE）、Groq 3 LPX、Intel（GNR/SRF）、AMD（Genoa/Turin）、QuantaPlex T46X-1U / S26F-2U、D75H-10U、D75E-4U、D76T-2U 等
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（GB200 NVL72 数据中心功耗分布饼图，网络约占 8%）；p4（31 GW / 268 GW 缺口）

### P242 06_AI Infrastructure validation at scale presented by Keysight
- 讲者/机构：Ram Periakaruppan（VP/GM；机构从页面看为 Keysight，文件名写明 "presented by Keysight"）[p1] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [运维/可靠性/遥测]（从设计到部署的仿真/仿真器验证）；次 [Up 机柜/超节点]（scale-up NIC 仿真）、[推理/算力/经济性]
- 核心主张：
  1. AI 时代集群高度同步，短板决定整体（"weakest link failure mode"），性能看尾时延而非 P95，超大规模时代的容错商品化扩展规则不再适用 [p3, p4]。
  2. 从参考模型、RTL、ASIC 到服务器、机柜，每个阶段都要"仿真其余的 AI 系统"，并沿用统一的模型、一致性测试和基准 [p6, p8, p11, p13]。
  3. 推理是多维问题：法律类重上下文，医疗类重内存，金融类重时延 [p12]。
- 关键数据：
  - 用 AresONE 端口（400G 或 800G）仿真 scale-up NIC/链路，配合 KAI Data Center Builder 验证协议、传输、集合通信与负载（自报）[p9, p10]
  - F1 类比：90 分钟、300 km 后胜负差 5–15 秒，用来说明 AI 系统余量很窄 [p5]
  - 本稿基本没有量化性能数据
- 提到的公司/客户/产品/标准：Keysight KAI（Data Center Builder、Conformance Builder、Inference Builder、KAI Emulator）、AresONE；EDA 集成 Synopsys、Cadence、Siemens；图片来源 NVIDIA、AMD、Broadcom
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（三个时代数据中心架构对比表：N+1/P95 → 同步分布式/尾时延）；p9（emulated scale-up NIC 验证拓扑）

### P243 07_AI Your Way Compute Agnostic, Rack-Scale Architecture for AI Factories
- 讲者/机构：Chris Petersen（Astera Labs，VP, CTO Office），2026-10-12 [p1, p13]；合作方 Hyve Solutions（看图）[p7] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [Up 机柜/超节点：机柜级互连]（PCIe 6 scale-up 交换）；次 [In 封装内：CXL/内存池化]（Leo X-Series KV cache 内存层）、[运维/可靠性/遥测]（COSMOS）
- 核心主张：
  1. 每换一种 xPU 就要重做机柜，集成和验证成本高；Orion 用通用计算托盘 + 通用 scale-up fabric 托盘，实现与 xPU 无关的机柜级参考设计 [p3, p5]。
  2. scale-up 交换机的规模和智能（Hypercast、In-Network Compute）直接提高 GPU 利用率和 tokens/s [p8, p9]。
  3. decode 受内存带宽限制，长上下文多轮对话占主导；在 GPU 附近加 KV cache 内存层（Leo X-Series），可独立于 CPU/GPU 扩容 [p10]。
- 关键数据：
  - Orion：Orion-CT 4RU xPU 无关计算托盘（Scorpio 320L，8 GPU scale-up）；Orion-FT 1RU PCIe scale-up fabric 托盘；160 GPU / POD（2 柜），无阻塞；铜/光缆均支持；规模 8→160 加速器（自报）[p6]
  - Scorpio X-Series 320L：称为业界最大 PCIe 交换芯片，已量产出货给多家 AI 基础设施厂商（自报）[p8]
  - Qwen3.5-122B 推理（prefill/decode 均衡）：1× Scorpio 2 320L（8 GPU 全带宽 P2P）比 2× 小交换机（各 4 GPU）tokens/s 高 50%，prefill 密集负载高 90%（自报）[p9]；看图读数：512 并发请求时约 1,780 vs 1,170 tokens/s（看图估计）[p9]
  - Hypercast + INC 加速集合通信最高 2×（自报）[p9]
  - Leo X-Series 放 KV cache 对比放 CPU 内存：TTFT 快 62%，TPS 多 22%（实验，Intel GNR 服务器 + 4× NVIDIA H200，Qwen2.5-32B）[p10]
  - COSMOS 处理的故障类型：GPU 链路掉线、FEC/BER 上升与 replay、交换机间 PCIe 链路故障（自报）[p11]
- 提到的公司/客户/产品/标准：Astera Labs（Scorpio X-Series 320L、Leo X-Series、COSMOS、Orion-CT/FT/MT/CB/LB）、Hyve Solutions、NVIDIA H200、Intel GNR、Qwen；PCIe 6、UALink、CXL、Ethernet、NVLink Fusion（看图）[p2]
- 首次/记录/SOTA 声明："Industry's largest PCIe switch now in volume production"（自报）[p8]
- 推荐配图页：p9（1 大交换 vs 2 小交换的 tokens/s 曲线 + Hypercast/INC）；p6（Orion 8→160 GPU 模块化结构）；p10（KV cache 放 CPU 内存 vs Leo X-Series）

### P244 08_Betting on the Network Meta's Case for Full-Stack, Open AI Networking
- 讲者/机构：Omar Baldonado（Meta，Senior Director, Data Center & AI Networking）[p1] | 类型：主题演讲（Executive Session）
- 方向归属（主/次）：主 [Out 后端网络：UEC/MRC/RoCE、交换芯片、NIC]（MetaRoCE、FPF、102.4T 交换）；次 [Across 跨楼/园区/区域：SRv6、DCI]（BAG、RBB）、[Up 机柜/超节点：ESUN]（Tahan）、[底座-冷却]（IcePack 液冷网络柜）
- 核心主张：
  1. AI 基础设施已经成为基础设施本身（以个人 AI agent Muse 为例）；Meta 在 scale-up、scale-out、scale-across 三层及共享软硬件上做开放的全栈网络 [p2, p3, p6]。
  2. scale-out 下一代用 Flattened Planar Fabric：多平面、去 ToR、两层，减少交换机和光模块、降低时延，负载均衡放到 NIC [p9]。
  3. 开放协作：ESUN 1.0 已发布、Open Switch Platform 规范评审中、FBOSS 配置驱动化，MetaRoCE 在 OCP 开源 [p19, p21, p22, p24]。
- 关键数据：
  - 102.4T scale-out 交换：IceCube / N-IceCube 基于 Broadcom TH6 / NVIDIA Spectrum-6，运行 FBOSS + SAI，系统由 Celestica 和 Accton 提供；IcePack 为 Meta 首个液冷网络机柜（基于 ORv3-HPRv1）（自报）[p8]
  - 集群规模演进：128 → 2K → 4K → 8K → 24K（单楼集群，2022–23）→ 129K（多楼集群，2024）→ 多区域集群（2025+，标注疑为 "1GW"，分辨率低，存疑）（看图）[p4]
  - Prometheus 园区 1+ GW（自报，看图为航拍）[p12]；楼间用 BAG（Backend Aggregation）网络互连，图示大规模管道/光缆施工（看图）[p13]
  - 可用性：数百万组件跨 scale-up/out/across；用 PAFT（Parallelism-Aware Fault Tolerance）把重启限制在小集群，并优化 checkpoint（自报）[p14]
  - 区域骨干 RBB：在 FBOSS 上通过 SAI 实现 SRv6，浅缓冲交换机，首个量产平台为 Cisco Silicon One；设计到量产 5 个月，之后 3 个月完成长途和 TE/SDN 控制器量产（现网，自报）[p16]；地图显示美国约 10 个区域圈，含 Meta 自有/租用与云站点，另有欧洲站点（看图）[p15]
  - Tahan：基于以太网的 MTIA 300 scale-up，用 Broadcom TH5 51.2T，FBOSS 作 NOS，下一步 TH6，为 ESUN 兼容 ASIC 做准备（现网，自报）[p18]
  - ESUN 1.0 规范于 3 月发布；1.1 在继续降低时延（自报）[p19]
  - Open Switch Platform 规范 1.0 评审中，由 Meta、Microsoft、Alibaba 发起，约十几家 OCP 成员参与（自报）[p21]
  - MetaRoCE：8 月发布，基于尽力而为以太网的 RDMA，QP 内多路径，乱序跟踪与流复用；AMD Pensando NIC 已支持，NVIDIA 合作中；OCP 上开源 libsoftmetaroce（用户态）和 dpdkmetaroce（kernel bypass）（自报）[p23, p24]
- 提到的公司/客户/产品/标准：Meta（Muse、MTIA 300、FBOSS、IcePack、IceCube/N-IceCube、Tahan、Prometheus、MetaRoCE、PAFT）、Broadcom TH5/TH6、NVIDIA Spectrum-6、Cisco Silicon One / G200 / 8501、Celestica、Accton、AMD Pensando、Nexthop AI、Microsoft、Alibaba；SAI、SRv6、ESUN、ORv3-HPRv1、RoCEv2
- 首次/记录/SOTA 声明：IcePack 为 Meta "our first liquid-cooled network rack" [p8]；当日在 OCP 开源两份 MetaRoCE 实现 [p24]
- 推荐配图页：p4（集群规模 128→129K→多区域演进 + ESUN 协议栈拼贴）；p13（Prometheus BAG 园区互连与施工照片）；p15（RBB 区域骨干地图）

### P246 10_Beyond Power Density Building a Safe 800V DC Ecosystem presented by Ea
- 讲者/机构：Joe Skorjanec（Eaton）[p1] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [底座-电力]；次 [安全]
- 核心主张：
  1. 800VDC 属于 IEC 低压 DC 范畴（上限 1,500VDC），不是输电 HVDC，但仍是危险电压，需要受控接触、绝缘、联锁、DC 额定分断和验证隔离 [p3]。
  2. 把变换移出计算柜，安全问题也随之进入白空间；架构（Side Power Rack / Power Center / MVSST）决定变换、保护、隔离和维护边界 [p4, p5, p10]。
- 关键数据：
  - 同等功率下 800V 电流约为 50V 的 1/16（自报）[p2]
  - 电压分级：ES1 ≤ 60VDC；ELV ≤ 120VDC；LV DC >120–1,500VDC；>1.5 kVDC 高压；输电 HVDC 通常 100–800 kV（引用 IEC / UL/IEC 62368-1）[p3]
  - Side Power Rack：每路 125A 保护回路接计算柜内一个 DC-DC 电源架，800V 下每 125A 回路约 100 kW（自报）[p6]
  - Power Center：集中/行级变换，DC 输出 1250A，经顶部母线槽或 RPP 电缆，125A 受保护分接（自报）[p5]
  - EPO 6 步：信号 → 停止变换器 → 分断 DC 输出 → 断开 BBU 与反灌 → 放电 → 验证；"Converter shutdown ≠ electrically safe work condition"[p13]
  - 三种接地：实接地、高阻接地、不接地/浮地（IMD 监测）；没有通用最优方案 [p16]
- 提到的公司/客户/产品/标准：Eaton；IEC、UL/IEC 62368-1、PoE++ 802.3bt、OCP 50V 机架母线、MVSST、IMD
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（800VDC 在 IEC 电压/能量等级中的位置）；p10（Side Power Rack vs Power Center 风险对比表）

### P219 Machine-Verifiable-CDU-Safety-Procedures-A-Worked-Extraction-from-OCP-Project-Deschutes
- 讲者/机构：Nauman Rafique（Visum AI 联合创始人）、Marco Pritoni（LBNL 研究科学家），贡献者 Leonardo Bachega（Visum AI）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [底座-冷却]、[安全]
- 核心主张：
  1. 设施有模型（Brick、ASHRAE 223），"工作"本身没有模型；应把程序、部件、联锁、隔离点和证据建成一张软件可读的图 [p6, p9]。
  2. 规则在图上确定性执行，不让 LLM 判定是否合规，同一程序每次得到相同结论 [p15]。
- 关键数据：
  - FY2025 约三分之二的 LOTO 违规涉及书面程序、培训与检查，而非硬件（引用 OSHA FY2025 Top 10）[p4]
  - 25% 运营方称员工被竞争对手挖走，12% 流失到行业外（引用 Uptime Institute 2025 Survey）[p4]
  - 原 Brick 论文：6 栋建筑、17,700 个数据点、8 个分析应用，无需定制（引用）[p10]
  - Brick v1.4.4 不含 CDU、RDHx、冷板、液冷 manifold（看图）[p11]；词汇表 12 个类（Procedure、Sequence、Action、OperatingMode、Event、Interlock、IsolationPoint、LockoutTagoutStep、FailureMode、CommissioningStep、MaintenanceTask、Actor）（看图）[p12]
  - 以 OCP Project Deschutes CDU v1.0.0 规范（Google）为例，漏液应急程序 6 步，同一供液截止阀同时被应急程序和泵拆卸维护程序引用（看图）[p13, p14]
- 提到的公司/客户/产品/标准：Visum AI、LBNL、Google（Project Deschutes CDU）、Brick、ASHRAE 223 / TC 9.9 / Guideline 0、OSHA 29 CFR 1910.147、NFPA 70E-2024 / 70B、Uptime Institute；github.com/Visum-ai/aif-ops
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（CDU 漏液程序依赖图）

### P222 Rack-Scale-Weight-Reduction-and-Reliability-Validation-for-Liquid-Cooled-Server-Systems-Using-Lightweight-Materials
- 讲者/机构：Jeff CA Chen（Technical Supervisor）、Shawn Ma（Sr. Manager），Wiwynn [p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [底座-机架/机械]
- 核心主张：
  1. AI 机柜重量逼近楼板承重极限，冷板、内部 manifold、管路占液冷部件重量 70% 以上，是减重重点 [p3, p4]。
  2. 冷板顶盖和 manifold 主体改用 PPS+GF，保留金属底板来维持散热性能 [p7, p9]。
- 关键数据：
  - 单宽机柜重量：2022 年约 800 kg，2024 年 >1300 kg，2028 年 >4000 kg（预测）[p3]
  - 密度：铜约 8.9、铝约 2.7、PPS+GF 约 1.66 g/cm³；铝比铜减重约 70%（自报）[p5]
  - PPS+GF 在 80 °C 下弯曲强度和模量保持室温值的 80% 以上（引用 DIC PPS 产品手册）[p6]
  - 冷板减重 66%，内部 manifold 减重 52%（自报）[p9]
  - 100 psi 下无泄漏；冷板顶盖平面度变化 0.0018 mm；验证项含 2,000 h 加速寿命、85 °C/85%RH（实验，部分为计划）[p10]
- 提到的公司/客户/产品/标准：Wiwynn、DIC、PG25、OCP Cooling Environments – Cold Plate 子项目
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（机柜重量增长）；p9（PPS 冷板/manifold 减重 66%/52%）

### P228 Deploying-Immersion-Native-ITE-in-AI-NeoCloud-An-OCP-Collaboration-Story-Continued
- 讲者/机构：Amy Short, PhD（Denvr Dataworks）、Austin Hipes（UNICOM Engineering）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]（单相浸没）；次 [Up 机柜/超节点]（浸没下 NVLink/PCIe 带宽）
- 核心主张：
  1. 浸没式 H200 SXM 服务器已在 neocloud 生产环境运行，并基于 2.5 年可靠性测试提供保修 [p7]。
  2. 信号完整性在浸没环境下需要专门设计和验证，不能沿用风冷结论；实测 NVLink/PCIe 带宽与 DLC 基本一致 [p9, p17]。
- 关键数据：
  - 风冷托管 1 MW / 6400 sq ft vs Denvr 模块化 1 MW / 600 sq ft；900 sq ft 内 128 GPU；PUE < 1.04，零耗水（自报）[p4]
  - 服务器尺寸 6U → 3OU（减半），每服务器省电约 800 W，每 128 服务器单元省 102 kW（自报）[p6, p7]
  - H200 NVQual：GPU Tj 最高 64.5–75.0 ℃（规格 85），功耗约 685 W（上限 700）（实验）[p8]；Llama-3.1-70B 推理 OTPS 8068，P99 时延 19.82 s（实验）[p10]
  - Blackwell SXM 1,000 W 目标，35 ℃ 介电液入口，600 s DCGM：平均 996 W，峰值核温 77 ℃（限值 83 ℃），8/8 通过（实验）[p15]；同平台 DLC（30 ℃ PG25）995 W、峰值 64 ℃ [p16]
  - NVLink GPU→GPU 浸没 766.32 vs DLC 767.46 GB/s（−0.15%）；双向读峰值 1525.27 vs 1526.62 GB/s；PCIe replay 和 EDATL 错误事件均为 0（28,360 个样本）（实验）[p17]
  - 冷却泵功 12.5–75 W；目标单 GPU 1,000 W+、每 OU 3000 W+（自报）[p13, p14]
- 提到的公司/客户/产品/标准：Denvr Dataworks、UNICOM Engineering、Dell XE9680、NVIDIA H200/Blackwell、NVQual、DCGM、ORV2.2/ORV3
- 首次/记录/SOTA 声明：无（"we have not yet seen a ceiling" 为观点）[p3]
- 推荐配图页：p17（浸没 vs DLC 的 PCIe/NVLink 带宽对比）；p16（1,000 W GPU 浸没 vs DLC）

### P229 Fluid-Oxidation-and-Electronic-Reliability-A-Multi-Fluid-EID-Measurement-Study
- 讲者/机构：Bobby Glidwell（fluidiQ by Magnalytix）、Vanja Boyd（ExxonMobil）[p1] | 类型：标准进展 / 技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：
  1. TAN、FT-IR、折射率和颜色都无法单独判断电气劣化；需要在板级直接测表面电阻 [p3, p18]。
  2. 在役流体在 TAN 相近时，表面电阻明显低于实验室温度老化样品，说明还有其他因素（离子污染、水分、析出物等）在起作用 [p16]。
- 关键数据：
  - 8 家流体厂商参与盲测；80 ℃ 加速老化 500 h，5 V 持续偏置，测试卡含 QFN48 / FBGA244 / QFP160 / 功率电感 4 种几何（实验）[p4, p6, p7]
  - 500 h 后 TAN 上升 +0.04 ~ +0.34 mg KOH/g，折射率变化 ≤ 0.1 °Brix，FTIR 相关系数 0.9996–0.9998（实验，看图）[p10]
  - 500 h 表面电阻：烃类 50.0–85.4 GΩ，酯类 24.4–61.5 GΩ；无一致下降（实验，看图）[p11–p13]
  - 在役 B-1（约 2 年）：57.7 GΩ vs 温度老化 71.5 GΩ，低 19.3%；在役 E-1（约 6 个月）：3.6 GΩ vs 24.2 GΩ，低 85.1%（实验）[p14, p15]
  - 大多数受测流体 TAN 远高于 OCP 规定的 0.02 mg KOH/g，但未见运行问题（自报）[p17]
  - DOE Phase 2（测到失效）计划 2026 年 11 月开始 [p19]
- 提到的公司/客户/产品/标准：Magnalytix、ExxonMobil；OCP Base Specification for Immersion Fluids Rev 1.0、OCP Immersion Requirements Rev 2.10、ASTM D664/D974/D4310、IEC 62021-2、JIS K 2501、AOCS Cd 3d-63
- 首次/记录/SOTA 声明：无
- 推荐配图页：p16（TAN vs 表面电阻：在役样品明显偏低）

### P235 Rack-Scale-Reliability-Demonstration-Testing-of-an-Intel-Datacenter-Certified-Immersion-Solution
- 讲者/机构：Samantha Yates（Intel，Principal Engineer）、Betsy Cossette（ExxonMobil）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：
  1. 浸没认证要依次通过封装/系统材料兼容性、热化学 FMEA，以及机柜级可靠性演示测试（IRDT），并给出统计置信区间 [p3, p5]。
  2. 业界需要统一浸没可靠性的统计方法和数据共享方式 [p18]。
- 关键数据：
  - 配置：5th Gen Xeon Platinum 8592+、BAC DUG Cool 26RU 30 kW、Hypertec Ciara、Micron 64GB DDR5 ×16、ExxonMobil EM DC 3235 Super [p2]
  - 材料兼容：电源线绝缘不通过、已更换；Xeon 封装为高风险，封装可靠性测试通过 [p4]
  - 数据量：约 10.9 亿行 + 4.19 亿行日志/传感器数据 [p9]
  - t0→ts：Linpack −1.0%、SPECrate −0.8%、GSAT +2.0%；CPU 温升均值变化 +1.6 / +1.2 ℃；Er 2.11、损耗角 0.0004 不变；溴 11.20 → 25.09 ppb（实验）[p12–p14]
  - 演示可靠性：24 台服务器 63,548 h，MTBF（80% LCL）39,471 h；1 年存活率 服务器 80% / CPU 89% / DIMM 99%（80% LCL）（实验统计）[p16]
- 提到的公司/客户/产品/标准：Intel、ExxonMobil、BAC、Hypertec、Micron；美国专利 12,672,256 [p7]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p16（MTBF 与存活率置信区间表）

### P236 Thermochemical-Reliability-Workstream-Update
- 讲者/机构：Samantha Yates（Intel）、Bobby Glidwell（Magnalytix）、Brian Kinkade（Fuchs）、Punith Shivaprasad（Shell）、Betsy Cossette（ExxonMobil）、Beau Van Vaerenbergh（Oleon）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [底座-冷却]；次 [运维/可靠性/遥测]
- 核心主张：
  1. OCP 浸没可靠性分三条工作流：材料兼容、部件兼容、热化学可靠性 [p3]。
  2. 要建立污染阈值、等效寿命加速模型，以及信号完整性（DDR5 rank margin）随污染变化的数据 [p12–p14]。
- 关键数据：
  - 材料兼容数据库上线：570 条兼容性观测、95 个部件档案、6 个流体族（自报）[p6]
  - 部件兼容白皮书已发布，测试案例包括线缆组件和光模块 [p9]
  - 产学合作里程碑：4Q26、2Q27、3Q27、2Q28（铜腐蚀阈值 → 环境致劣化 → 污染对热性能影响 → 系统级 SI）[p13]
- 提到的公司/客户/产品/标准：Intel、Magnalytix、Fuchs、Shell、ExxonMobil、Oleon；SIR、ECM、ICP-MS
- 首次/记录/SOTA 声明：铜腐蚀污染阈值数据集称为社区"First threshold dataset"（计划）[p13]
- 推荐配图页：p13（2026–2028 研究里程碑路线）
