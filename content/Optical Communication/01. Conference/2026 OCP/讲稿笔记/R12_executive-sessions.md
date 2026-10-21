---
title: "R12_executive-sessions"
tags:
  - OCP2026
  - 讲稿笔记
---

# R12 笔记：executive-sessions, expo-hall-sessions

### P267 31_Innovation on Diagnosis and Maintenance of AI Datacenters presented by
- 讲者/机构：James Zou，R&D Fellow，AiVRES [p1] | 类型：厂商技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [In 封装内]（PCIe 器件寄存器/OOB 访问）
- 核心主张：
  1. 数据中心故障常在实验室无法复现，根因在应用通信与 CPU 调度的交互；案例中 GPU 请求遇到主机响应延迟，触发 PCIe Completion Timeout（CTO）导致整机挂死 [p5–p7]。
  2. PCIe Endpoint 的超时值写在厂商固件中，是"黑盒"，主板设计方无法调整；Root Port 可通过 UEFI BIOS 调整 [p7]。
  3. 呼吁扩展 PCIe 规范：BMC 经 I2C/OOB 访问配置与状态寄存器、待机供电寄存器域在主电掉电后保留状态、记录寄存器变化历史，推动 RAS 从被动走向预测 [p24–p27]。
- 关键数据：
  - 部署规模 200+ 台 NVIDIA GPU 服务器，实验室验证（PI/SI、功能/热/压力）100% 通过，但现场出现间歇挂死，BMC 日志零异常 [p3]（自报，现网案例）
  - 复现手段：用户特定软件 + 定向 CPU 压力才复现 [p5]（自报）
  - 未来 PCIe 器件架构列出 6 类寄存器（配置、状态、AER、链路状态、LTSSM、内部状态），双路径（PCIe 总线 + OOB 总线），主电/待机电双域 [p26]（自报）
- 提到的公司/客户/产品/标准：NVIDIA GPU、PCIe AER、BMC、FPGA、UEFI BIOS、IPMI（NetFn 2Ch Cmd 02h/03h 启动进度码）[p14]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（GPU–PCIe Switch–Retimer–Root Port–CPU 链路与 CTO 分析）；p26（未来 PCIe 器件 OOB/待机电寄存器框图）

### P268 33_Introduction to Memory-centric AI Rack Systems (MARS) presented by SK
- 讲者/机构：Hoshik Kim，SVP & Fellow，Memory Systems Research，SK hynix [p1] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化、HBM]；次 [推理/算力/经济性]、[Out 后端网络]（机柜间 RDMA）
- 核心主张：
  1. 多轮 Agent 推理使 KV cache 爆炸，需从以处理器为中心转向以内存为中心：机柜内 CXL、计算机柜与内存机柜之间用 RDMA，形成机柜级解耦内存池（MARS）[p2, p7]。
  2. 把 KV cache、模型间中间结果、图数据放进共享内存池，用内存访问替代服务器间显式数据传输 [p6, p10–p12]。
  3. 发布 HBF（High Bandwidth Flash）作为 HBM 与 eSSD 之间的新内存层 [p15–p17]。
- 关键数据：
  - TTFT（秒，平均/尾部）：重算 80.76/478.11；Remote SSD 33.56/259.03；Remote CXL Hybrid 21.92/136.95；Remote CXL DDR 15.45/122.90；相对重算改善 3.5–5.2× [p10]（自报实验；柱值看图核对）
  - 语音 Agent 流水线（STT→LLM→TTS）用 CXL 内存池替代 RDMA：TTFA 0.67s→0.46s（1.46×），E2E 8.08s→5.73s（1.41×）[p11]（自报实验；数值配对依文字层，存疑处以 1.46×/1.41× 为准）
  - 分布式 GNN 训练采样时间较 RDMA 提升 17.57× [p12]（自报）
  - HBF 相对 HBM：带宽 0.5x、容量 14x、pJ/b 3.7x；eSSD：带宽 <0.1x、容量 >500x、pJ/b 6.9x [p15]（自报，看图）
  - HBF 卡 3TB vs 基线卡 288GB；Tokens/user 峰值 HBF 19M vs 基线约 7–8M（batch 8，DeepSeek R1 671B，8 卡 EP8）；batch 16 约 9M，batch 64 约 1.2M [p16]（仿真/自报，看图）
  - HBF 时间线：'25.2 SanDisk HBF 介绍，'25.8 MOU，'26.2 联盟启动/Spec α，'26.7 v0.7 公开，'27.1 Spec 1.0（预期），'28.1Q HBF Cube 可用 [p17]（预测）
- 提到的公司/客户/产品/标准：SK hynix MARS、HBF、SanDisk、CXL、RDMA、DeepSeek R1 671B、Llama 3 70B、CCL/MPI/NATS 等软件栈 [p8]
- 首次/记录/SOTA 声明：无明确"首次"声明
- 推荐配图页：p7（多机柜 MARS 架构：机柜内 CXL、机柜间 RDMA）；p10（TTFT 对比柱状图）；p16（HBF tokens/user 曲线）

### P269 36_Liquid-Cooled Power Shelf and 800 VDC platform for next generation dat
- 讲者/机构：Jared Huntington（Senior Power Architect，NVIDIA）、Roya Movahedi（CMO，MEGMEET）、Shi Lei（Lead Engineer，MEGMEET）[p1] | 类型：厂商技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [底座-冷却]
- 核心主张：
  1. 机柜功率走向 Gen3 570 kW 及以上，需要 800 VDC 进入 PSU 并 100% 液冷 [p2]。
  2. 电源架也液冷后可取消冷热通道，设施 CAPEX 最多约降 10% [p7]。
- 关键数据：
  - Gen1 GB200/GB300 54 VDC 145 kW；Gen2 Vera Rubin NVL72 54 VDC 330 kW；Gen3 54 VDC 570 kW（800 VDC 入 PSU，100% 液冷）；Gen4 约 1,000 kVA 级（看图）[p2]（自报/预测）
  - 风冷上限 33–50 kW/机柜；风扇功耗约 10% 回归计算；电容寿命每降 10°C 翻倍；计算:电源柜 4:1 [p4]（自报）
  - 液冷电源架每 1U 多约 18 kW；单 PSU 漏液时仍有 55 kW 可用 [p6]（自报）
  - 54V 2RU 110 kW 液冷 AC/DC 架；800V 100 kW 液冷 AC/DC 架效率 >98%，带 BBU 5RU、90s 保持 [p9, p13]（自报）
  - 800 VDC 电源柜：800 kW 标准，8 × 100 kW 架，BBU 89 kW 放电 ≥90s@40°C [p10]（自报）
  - DC/DC 模块：10 kW 峰值效率 98.5%@800Vin；30 kW 满载 97.7%，16:1 固定比，高度 <40mm [p15]（自报）
- 提到的公司/客户/产品/标准：NVIDIA MGX、GB200/GB300/Vera Rubin NVL72、MEGMEET SST、EDPP、Redfish
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（机柜功率代际与 800 VDC 路线图）；p8（54V→800VDC→SST 架构演进）

### P270 37_Multi-Dimensional Scalability for AI infrastructures
- 讲者/机构：Clayton Wagar（Principal Consulting Engineer，Nokia）；p10–p12 为 Prasanna C（CPO，Lightstorm）[p1, p14] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：DCI、ZR/相干]；次 [推理/算力/经济性]
- 核心主张：
  1. Scale-up/out/across 都局限在单一运营商域内，需要面向分布式推理的 "Scale-beyond"，靠 IP 路由 + 光传输 [p7–p8]。
  2. 用 CIR（每 FLOP 可搬运字节数）衡量，广域层比 NVLink 低 4–5 个数量级，且差距每年扩大 12–19%；推理比训练对广域带宽敏感得多 [p10–p11]。
  3. Lightstorm 将在印度三站点生产光纤走廊上开放测量十项指标，试点窗口 2026 年底开放 [p12]。
- 关键数据：
  - CIR（mB/FLOP）：HBM 3.39；NVLink 0.910；IB NDR/400GE 0.006–0.050（低 18–152×）；1–10GbE WAN 0.0000158–0.000158（低 5,760–57,600×）；B200 on-package ~3.56 [p10]（模型推导，H100 989 TFLOPS BF16 口径，引用 arXiv:2608.14967）
  - 训练广域需求 5 Gbps（假设值）vs 推理 2,147 Gbps（70B MHA、4K 上下文、10.74 GB KV 在 40 ms TTFT 内传输），相差 429×；GQA 1/8 KV heads 需 268 Gbps，latent attention 约 58 Gbps [p11]（建模）
  - 论文摘要：迁移 vs 重算交叉点 70B MHA 每流 74–111 Gbps，GQA 下 9–14 Gbps；GPU 稀缺与 KV 复用将有效 GPU 成本放大 5–20× 时传输更划算 [p13]（看图，论文摘要）
  - 2026–2030 全球数据中心支出 >\$5.5tn，23% CAGR；光纤部署 1.2B km；光接口 2025→2030：相干 970k→3m，DC 内 50m→215m 端口/年；DC 内容量 CAGR 65%（2025–2034）[p2]（引用 Dell'Oro、Goldman Sachs、LightCounting、Cignal AI 等）
  - DCI 带宽需求 3386 EB/月 [p3]；AI 已达 1.3 万亿会话/年、236 EB/月；Google 每月处理 3.2 千万亿 tokens [p4]（引用 Nokia Bell Labs、Google I/O）
  - 平台：800 Gb/s 相干路由，11.1 GHz（原文如此，存疑）Super-C + Super-L 扩展频谱 [p9]（自报）
- 提到的公司/客户/产品/标准：Nokia、Lightstorm、NVLink、InfiniBand NDR、400G Ethernet、H100/B200、量子安全加密
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（四层互连 CIR 对比表）；p11（训练 5 Gbps vs 推理 2,147 Gbps）

### P271 38_Next-Generation Power & Cooling Solutions presented by TCT
- 讲者/机构：Arthur Wang，Director of Product Management，xFusion（文件名标 TCT）[p1] | 类型：厂商分享
- 方向归属（主/次）：主 [底座-电力]；次 [底座-冷却]（另提及 CPO）
- 核心主张：
  1. 冷却、供电、互连三项同时变革：液冷+金刚石铜、800V HVDC+VPD、少铜多光/CPO [p6]。
  2. 48V 在 MW 级机柜下铜损不可接受，升至 800V 后电流降到 1/16、损耗降到 1/256 [p12]。
- 关键数据：
  - 48V 母线电流：40 kW 柜 741 A；120 kW（Blackwell）2,222 A；230 kW（Vera Rubin）4,260 A；500 kW（Rubin Ultra）9,259 A；1 MW（Feynman）18,519 A；1 MW 下母线铜损 >50 kW [p12]（自报计算）
  - 48V→800V：转换级 4→3，系统效率 88%→90%，线损 5–8%→<1% [p11]（自报）
  - 芯片功耗/热流：2026 年 MW/rack、3000+ W/chip、200+ W/cm² [p7]；金刚石铜冷板 4 kW+/chip，平均 200 W/cm²、热点 400+ W/cm² [p8]（自报）
  - 互连：224G+ 铜接近极限；"光+铜"3–5 年内成为默认 [p6]（自报预测）
  - 800V DC PDU：1.2 MW（10×3U 电源架）或 720 kW（6×3U 电源架+6×3U BBU 架）；母线 800V/1500A [p13]（自报）
- 提到的公司/客户/产品/标准：xFusion、NVIDIA Hopper/Blackwell/Vera Rubin/Rubin Ultra/Feynman、Infineon PBB、SiC/GaN、MicroLED CPO
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（48V 母线电流随机柜功率的阶梯图）

### P273 40_Open Optical Interconnect Solutions for AI Scaling presented by Teraho
- 讲者/机构：Rang-Chen (Ryan) Yu，VP Marketing，TeraHop [p1] | 类型：厂商分享 / 标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/NPO/XPO]；次 [Out 后端网络：可插拔光模块/LPO/LRO]、[Across：空芯/多芯光纤]
- 核心主张：
  1. 用三个 MSA 回应 AI 扩展的四个挑战：12.8T XPO（带宽/面板密度）、6.4T Open CPX（功耗/密度，NPO/CPO）、SDM4 MCF（光纤基础设施）[p4]。
  2. 集成激光器的 NPO 优于 ELSFP 外置光源：ELSFP 多 >3dB 耦合/连接损耗，需 >2× 激光功率（200–300 mW+），激光功耗约增 4× [p14]。
  3. SDM4 多芯光纤可把光纤接口端接数减少 4×，缓解 DC 内 >10M 根光纤的布线压力 [p3, p17]。
- 关键数据：
  - XPO：8×1.6T 容量，4× 面板密度，首个集成液冷的可插拔，150+ 公司加入 MSA；支持 FRO/RTLR/LPO、DRn/FRn/OCI/Coherent-Lite/ZR [p5]（自报）
  - 12.8T XPO 实测：64 路发射机眼图，8×1.6T-DR8 pre-FEC BER 在约 -2~0 dBm 降至 1E-12 附近；0.3 LPM 下 CW 激光温度 25/35/45°C 进水分别约 36–41/45–50/53–57°C；模块功耗在 45–55°C、0.3–0.5 LPM 下约 200 W 且基本平坦 [p7]（实验，看图）
  - Diablo-1 6.4T NPO（ECOC OIF demo）：ER 2.94/3.11 dB，TDECQ 2.43/2.48 dB，8 路 BER 1.7E-11~5.3E-10 [p12]（实验，看图）
  - 预测试：ER=3dB，TDECQ=2.1dB；ASIC 到 NPO 插损约 12 dB [p13]（实验）
  - Open CPX NPO 含内置激光功耗约 5.5 pJ/b [p14]（自报）
  - 可靠性：出货 >25M 硅光收发器，PIC >100B 器件小时，FIT<0.01；按器件数折算 12.8T XPO 约 2.2 FIT、6.4T NPO-ILS 约 1.2 FIT、1.6T-DR8 约 0.27 FIT [p15]（现网/自报，折算值看图估计）
  - 规模挑战：scale-up 带宽约为 scale-out 的 10×，10–20 Tbps/xPU（引用 NVIDIA）；DC 内 >10M 光纤，DC 间 >4M（引用 Meta）[p3]
  - SDM4 MCF MSA 2026-03-11 成立（AFL、Corning、Sumitomo、TeraHop），Release 1.0 于 2026-09-17 发布；2×2 4 芯 MCF [p16–p17]（自报）
- 提到的公司/客户/产品/标准：XPO MSA、Open CPX MSA、SDM4 MCF MSA、OIF、Ciena（Open CPX-ELM）、Corning、AFL、Sumitomo、Intel（集成激光 PIC 引用）、Arista（引用）、Meta（引用）
- 首次/记录/SOTA 声明："Industry 1st 12.8T XPO Performance" [p7]；XPO 为"1st Pluggable with Integrated liquid cooling" [p5]
- 推荐配图页：p7（12.8T XPO 64 路眼图 + BER + 液冷温度/功耗）；p15（FIT vs 器件小时对比图）；p19（SMF→SDM4-MCF 光纤数量概念对比）

### P275 42_Open, Modular Rack-Scale AI Infrastructure for the Agentic Era present
- 讲者/机构：Dimitris Ziakas，CTO & VP Architecture，Hyve Solutions [p1, p12] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [In 封装内：CXL/内存池化]、[Up 机柜/超节点]
- 核心主张：
  1. Agentic AI 把瓶颈从加速器移到周边：CPU 编排、网络、上下文内存需按机柜整体平衡 [p3–p4, p11]。
  2. 分层上下文内存（HBM 热态 → DDR/CXL → NVMe/Flash → 对象存储）是提高利用率的手段，不要为存上下文而采购加速器 [p8, p14]。
- 关键数据：
  - Google 月处理 tokens 同比 7×；每 GW 需 4×+ CPU 容量（Arm）；CPU:GPU 比从 1:4–1:8 走向 1:1–1:2（TrendForce）[p3]（引用）
  - 十年对比：服务器 CPU 核数 14×（18→256）；每 GPU scale-out 带宽 8×（200→1,600 Gb/s，ConnectX-9）；HBM 容量 18×（16→288 GB）[p4]（引用公开规格）
  - 每 GPU scale-up 带宽 22×（160 GB/s→3.6 TB/s，NVLink 6）[p5]（引用 NVIDIA/WikiChip）
  - 72-GPU 机柜光纤 576 根（为传统 CPU 柜 18×）；约 5,000 根、约 2 英里铜缆；约 120 kW；2027 年起 1 MW 机柜（800 VDC）[p6]（引用 Corning、NVIDIA、Uptime）
  - 128K 上下文下 2 个用户即填满 80GB HBM [p7]；相对单位用户成本：仅 HBM 4X（~2 用户/GPU）、+DDR ~2X（~6）、+flash/KV store 1X（~16）[p8]；3 年归一化 TCO 降约 65%（100→35）[p9]（示意模型，看图核对；非承诺值）
- 提到的公司/客户/产品/标准：Hyve、UALink、UEC、ESUN、CXL、800 VDC、NVIDIA ConnectX、AMD EPYC Venice（256 核）、Rubin 288GB HBM4
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（NVLink 每 GPU 带宽 22× 增长）；p8（分层内存每用户成本对比）

### P278 46_Scaling AI Inference Infrastructure from Silicon to System presented b
- 讲者/机构：ASRock Rack 与 Arm 联合（封面 logo，看图）；讲者姓名未见 [p1] | 类型：厂商分享
- 方向归属（主/次）：主 [推理/算力/经济性]（Agentic CPU）；次 [运维/可靠性/遥测]（OpenBMC）、[In 封装内：chiplet/UCIe]
- 核心主张：
  1. Agent 工作流需要 3–5 倍 CPU 来平衡编排与加速器 [p6]。
  2. Arm AGI CPU 定位为面向 Agent 的高能效 CPU；Arm 推动 FCSA chiplet 架构与服务器标准化 [p10–p12]。
  3. ASRock Rack 把 OpenBMC 每板差异压到配置文件（prjconfig.bbclass + dts），一个镜像经 Chassis ID 服务多个系统 SKU [p17–p22]。
- 关键数据：
  - Arm AGI CPU：最多 136 个 Neoverse V3 核，3nm，300W TDP，96 lanes PCIe Gen6，CXL 3.0，DDR5-8800，每芯片 6TB，6 GB/s/核内存带宽，内存延迟 <100ns，每核 2MB L2，最高 3.7GHz [p11]（自报）
  - 3–5× 更多 CPU 平衡 agent 流 [p6]（自报）
  - 2OU2N-ARM：44OU 36 节点，12 DDR5 RDIMM 8000MT/s，6 E3.S（PCIe 6.0），OCP NIC 3.0，ORv3 [p14]（自报）
  - OpenBMC 框架覆盖 AST2500/2600/2700 与 Nuvoton NPCM845 四类 SoC [p26]（自报）
- 提到的公司/客户/产品/标准：Arm AGI CPU、CSS、FCSA、UCIe、AMBA CHI、SBSA/SBMR、Meta Yosemite V5、OCP NIC 3.0、DC-MHS、DC-SCM、ORv3、OpenBMC、OpenClaw
- 首次/记录/SOTA 声明："World's most efficient agentic CPU" [p10]（自报）
- 推荐配图页：p11（Arm AGI CPU 规格）；p6（CPU 编排 vs 加速器示意）

### P279 47_Scaling AI Infrastructure The Pivotal Role of Silicon Photonics in Ful
- 讲者/机构：Haijiang Yu，Genuine Optics（GO）[p1–p2] | 类型：厂商分享
- 方向归属（主/次）：主 [Out 后端网络：可插拔光模块/LPO/LRO]；次 [Up 机柜/超节点：CPO/NPO/XPO]、[In 封装内：光 I/O]
- 核心主张：
  1. 形态从可插拔 → NPO → CPO，单通道 100G→200G→400G；NPO 是性能、工程可行性与生态成熟度之间的务实选择 [p3, p6, p17]。
  2. 引用 LightCounting：LPO/NPO/CPO 约 2027–2028 起快速增长；NPO 主要由 scale-out 带动，CPO 由 scale-up 带动且量产晚于 NPO [p5]。
- 关键数据：
  - 两年增长：AI 训练算力 ~100×、GPU 3.3×、内存带宽 1.4×、互连 1.4× [p4]（引用）
  - LightCounting 端口出货：2031 年约 375M，其中 CPO/NPO 约 145M；NPO 2031 约 89M（scale-out 约 52M）；CPO 2031 约 71M（scale-up 约 46M）[p5]（引用，看图估计）
  - 1.6T 模块功耗：Full DSP <24W，LRO <15W，LPO <10W；LRO 在 24dB die-to-die 损耗下 BER 可达 E-13 级 [p11]（自报实验）
  - 12.8T XPO：XPO MSA & CMIS 5.3，500m SMF，8×MPO-16，功耗 <130W（典型 130W/80W），TDECQ 2.5dB，ER >4dB，BER E-10~E-11 [p12]（自报实验）
  - 3.2T/6.4T NPO：<8.5W，≥20 dBm/lane 输出，32 通道 100/200G，TDECQ 1.6dB，EVB 环回 BER <1E-10 [p13]（自报实验）
  - 400G/lane 1.6T DR4：4×425G PAM4 光、8×212.5G 电，SiPh/TFLN + 3nm 400G DSP，~30W，500m，BER ~E-6，TDECQ 1.4dB [p14]（自报实验）
  - 3.2T MRM CPO OE：2×8λ×200G，QD 8λ DWDM 梳状激光 ELS，带宽密度 >3 Tbps/mm（单向），每梳最大 10 dBm [p15]（自报）
  - 可靠性：出货百万级硅光模块，>8B 器件小时，PIC FIT <0.2 [p10]（现网，2 年出货口径）
  - 2024 年全球前 8 光模块供应商 [p2]（自报）
- 提到的公司/客户/产品/标准：Genuine Optics、LightCounting、XPO MSA、OCI-MSA、OIF、CMIS 5.3、ELSFP、TFLN、CIOE 2026、OFC 2026
- 首次/记录/SOTA 声明：无明确"首次"；400G/lane 模块与 3.2T NPO/CPO OE 为 live demo [p8]
- 推荐配图页：p5（LightCounting 可插拔 vs NPO/CPO 出货）；p7（GO 光互连路线图 2023–2028+）

### P281 50_Solving Power Density and Bandwidth Challenges in AI Infrastructure pr
- 讲者/机构：Gaurav Jain（Sr. Dir. Product Management）、Ram Kasiraman（Sr Mgr. Product Management），TE Connectivity [p1, p11] | 类型：厂商分享
- 方向归属（主/次）：主 [底座-电力]；次 [Up 机柜/超节点：CPO/NPO]（无源光路径）
- 核心主张：
  1. 800VDC 带来新的连接器要求：触摸防护、爬电/间隙、受控插拔、联锁、断电维护、连接器状态监测 [p2]。
  2. 光边界从面板移向封装，可服务性必须设计进无源光路径（FAU、连接器、扇出/背板）[p6–p8]。
- 关键数据：
  - 800V IT 机柜母线 250 kW–1.6 MW 可扩展；感测与预充在 35mm 母线宽度内 [p2]（自报）
  - FusionForge 光纤端接：亚微米精度，±1° PM 定轴，无环氧 [p9]（自报）
  - 相关专题：448G 共封装铜、400G/lane 光模块连接器、500W 级 HSIO 直液冷 [p11]（看图，议程信息）
- 提到的公司/客户/产品/标准：TE Connectivity、ELCON、ICCON、RAPID LOCK、BB4000、FusionForge、OIF（Nathan Tracy）
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（可插拔→NPO→CPO 光边界内移与可服务性）

### P286 55_The Path to Infinite Inference presented by d-Matrix
- 讲者/机构：Sid Sheth，Founder & CEO，d-Matrix [p1] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [Up 机柜/超节点：ESUN/NVLink Fusion]
- 核心主张：
  1. 推理进入 GPU-Plus 时代：GPU 负责 prefill/attention，内存中心型 XPU 负责低延迟 decode/FFN [p5–p7]。
  2. 三种解耦方式：投机解码 3×、Attention-FFN 解耦 7×、Prefill-Decode 解耦 10× 交互性 [p9]。
  3. 路线：Corsair（SRAM）→ Raptor（3D DRAM）→ Lightning（多层堆叠 DRAM），不用 HBM 与 CoWoS [p11, p17, p22–p24]。
- 关键数据：
  - 交互性提升：投机解码 3×、AFD 7×、PDD 10× [p9]（自报，看图）
  - AFD 演示：845 tokens/s/user，64 并发用户合计 20,145 tokens/s；GPU（NVIDIA Vera Rubin）跑 Attention，Corsair 跑 FFN/MoE，经 JetStream 低延迟以太网 [p15]（自报实验）
  - Corsair：1 chiplet，4 quads，256 MB SRAM [p11]；Squadron：最多 16 SquadRack，1,024 Corsair XPU，MW 级，400G 以太网交换 [p12, p14]（自报）
  - Raptor NVLink Fusion 机柜：144 XPU，18 Raptor 托盘 + 9 NVLink Switch 托盘，3D-DRAM 2.3 TB、7.2 PB/s [p19]（自报）
  - 与 Arista 合作 ESUN 系统，128 颗 Raptor XPU [p20]（自报）
  - 模型规模：Corsair 100B（PCIe 8× 节点）、Raptor 3T（ESUN/NVL144 机柜）、Lightning 20T [p23]（自报预测）
  - AI token 用量 2026–2030 增长 24×（Goldman Sachs）[p3]（引用）
  - 工艺 6nm，无 HBM、无 CoWoS [p24]（自报）
- 提到的公司/客户/产品/标准：d-Matrix Corsair/Raptor/Lightning/JetStream/SquadRack/Squadron、NVIDIA NVLink Fusion、MGX Oberon、Vera、ConnectX-9、BlueField-4、Spectrum-X、Arista、ESUN、Supermicro、Groq
- 首次/记录/SOTA 声明："Industry's First AFD Demonstration" [p15]；Corsair 为"World's First SRAM Solution to Market" [p11]；Raptor 为"World's First 3D-Stacked Solution to Market" [p17]
- 推荐配图页：p9（三种解耦解码方式与 3×/7×/10×）；p15（AFD 演示拓扑与 tokens/s）

### P287 56_The Silicon Heartbeat of the AI Economy the Efficiency Paradox in Next
- 讲者/机构：Bhushan Chitlur，Chief Architect Datacenter & AI，MediaTek [p1] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [In 封装内：chiplet/UCIe、D2D]；次 [推理/算力/经济性]、[Up 机柜/超节点：CPO]
- 核心主张：
  1. AI 算力需求每 4–5 个月翻倍，远快于摩尔定律的 18–24 个月；能源是最硬约束，按当前趋势 2030 前触及能源墙 [p2–p3]。
  2. 效率提升来自领域专用架构、10×+ 光罩尺寸的异构集成、光互连；评价标准应是 Perf/W 与 Perf/TCO，而不是峰值 FLOPs [p4, p8, p18]。
- 关键数据：
  - 2026 数据中心营收目标从 \$1B 上调为 \$2B；2027 年 TAM \$70B–80B，MediaTek 份额 15–20% [p6]（自报预测，看图：原 "2028" 被划改为 "2027"）
  - 封装：2020 年 InFO 91×91 mm² 量产；2022 年首个 Hybrid CoWoS 85×85 mm² 量产；2024 长距可定制 224G SerDes；2026 Q4 首个量产设计出货 [p5]（自报）
  - 2.5D <10,000 mm² Si；3.5D 10,000–20,000 mm² Si [p12]（自报）
  - 功耗层级：CPU <0.5 kW、GPU 2+ kW、领域专用芯片 5+ kW [p4]（自报）
- 提到的公司/客户/产品/标准：MediaTek、UCIe、Mlink、uLED、NPC/CPC 连接器、CPO、UALink、ESUN、UEC、NVLink Fusion、Intel EMIB、TSMC N3/N2P/A14、SK hynix、Micron、Samsung
- 首次/记录/SOTA 声明："World 1st Hybrid CoWoS (85×85mm²) volume production" [p5]
- 推荐配图页：p11（die→board→rack 互连技术分层）；p2（AI 算力需求 vs 摩尔定律曲线）

### P289 58_Wider. Slower. Better Optics That Can Beat Copper presented by Credo
- 讲者/机构：Bill Brennan，President & CEO，Credo [p2] | 类型：厂商主题演讲
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板、CPO/NPO]；次 [Out 后端网络]
- 核心主张：
  1. "宽、慢、更好"：用 µLED/µVCSEL 等微发射器二维阵列、几乎不做信道补偿，可在可靠性、功耗、成本三项同时赢过铜 [p5, p9]。
  2. 铜本身无源，但 SerDes 不是；替换 VR200 NVL72 铜背板可省约 60% 功耗 [p7]。
  3. 在 OCP 发起 Short Reach µEmitter Optics（SRMO）工作流 [p14]。
- 关键数据：
  - µEmitter 对比：红光 µLED <1 pJ/bit、≤2 m、光纤数上万；蓝光 µLED <2 pJ/bit、≤10 m；µVCSEL <2 pJ/bit、≤50 m、数百根光纤 [p5]（自报）
  - VR200 NVL72 铜背板 260 TB/s = 10 kW，约占机柜功耗 5%；400Gb bidi SerDes ~5 pJ/bit；µEmitter <2 pJ/bit 省 60%，即每柜 6 kW、每 GPU 80W [p7]（自报估算）
  - 每瓦价值：OpEx \$5/W、CapEx \$20/W、机会成本 \$100/W；一根 \$100 DAC 对应 \$1,600 机会成本；VR200 背板对应 \$600k [p8]（自报估算）
  - 铜：100M 小时 MTBF/MTBI，<\$0.10/Gb/s [p4]（自报）
  - 1.6T ZeroFlap ALC：50 m 距离，12W/端，2027 年量产 [p10]（自报）
  - ZeroFlap 盲插背板：30 Pb/s、1M 根光纤，1.8 Pb/托盘；相对铜背板密度 30×、距离 30×（50m）、重量减 90%，15% 冗余做无中断光纤切换 [p12]（自报）
  - 路线：2027 1.6T ALC（scale-up）；2028/29 3.2T ALC、6.4T NPO；2030+ >5 Tb/mm CPO、Petabit scale-in [p11]（预测）
- 提到的公司/客户/产品/标准：Credo、NVIDIA VR200 NVL72、Senko、Corning、AFL、Heraeus、YOFC、ams OSRAM、BizLink、Foxlink、OCP SRMO 工作流、Nscale/Lambda/SpaceX（用于每瓦价值估算）
- 首次/记录/SOTA 声明：无明确"首次"；"Introducing the ZeroFlap Blindmate Backplane" [p12] 为新品发布
- 推荐配图页：p5（µLED/µVCSEL 指标对比）；p7（VR200 铜背板功耗与节省）；p14（SRMO 工作流成员，看图）

### P290 01_Agentic AI The Agentic Rack, Powered by Intel Xeon Processors presente
- 讲者/机构：Jatin Upadhyay，Data Center Group，Intel [p1，看图] | 类型：厂商展区
- 方向归属（主/次）：主 [推理/算力/经济性]（Agentic CPU）；次 [In 封装内：CXL/内存池化]
- 核心主张：
  1. Agent 任务的实际耗时大部分在 CPU（工具执行、数据服务、编排），需要不同 CPU 核与 GPU 搭配 [p2–p3]。
  2. Xeon 用 P/E 核混合、AMX、CXL Flat Memory Mode、QAT/DSA/IAA 提升 agent 密度 [p5–p9]。
- 关键数据：
  - CPU 执行时间占比：编码 Agent 82%、客服 Agent 78%、科学逆合成 70%、RL 环境 80% [p2]（示意性仿真估计）
  - 单轮 Agent 墙钟占比：模型调用 30–40%、工具执行 30–35%、数据服务 10–25%、编排 7%、状态搬移 8% [p3]（自报）
  - CXL Flat Memory Mode 达全 DDR5 性能的 97.3%；IAA/zswap 同性能下内存减 33% [p7]（自报）
  - AMX BF16 在 445 ms p95 下支撑会话数为不开 AMX 的 4×；CPU 上跑 Qwen3-Coder-30B-A3B 子代理比云端子代理 token 成本低 25%、墙钟快 6.5% [p8]（自报实验，Xeon Gen5 EMR）
  - Diamond Rapids：最多 256 核/插槽，Intel 18A-P，16 通道、32 DIMM（2DPC），12800 MT/s，1.6 TB/s，1.28 GB LLC [p11–p12]（自报）
- 提到的公司/客户/产品/标准：Intel Xeon/Diamond Rapids、AMX、QAT、DSA、IAA、TDX、CXL、ORv3、Intel GPU (CRI)、SambaNova RDU
- 首次/记录/SOTA 声明：无
- 推荐配图页：p2（各类 Agent 的 CPU 时间占比）；p13（Agentic 部署形态：CPU 柜 + 推理柜解耦）
