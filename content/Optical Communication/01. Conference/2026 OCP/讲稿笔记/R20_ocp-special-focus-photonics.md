---
title: "R20_ocp-special-focus-photonics"
tags:
  - OCP2026
  - 讲稿笔记
---

# R20 笔记：ocp-special-focus-photonics, server

### P442 Optical-Scale-Up-AI-Systems-Architectures-Standards-and-Resiliency-Strategies
- 讲者/机构：Adrian Motamedi（Interconnect System Architect）、Fotini Karinou（Director of Optical Technologies & Architecture），Microsoft Azure Hardware Systems and Infrastructure (AHSI) [p1] | 类型：技术分享/标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/NPO/XPO、机柜级互连]；次 [运维/可靠性/遥测]
- 核心主张：
  1. 光互连让多机柜、多排 scale-up 变得可行，系统价值来自 reach、带宽密度、能效、利用率和韧性 [p2][p4]。
  2. 共享激光器和光子集成使单点失效（激光器或 PIC）影响多通道，blast radius 远大于铜链路；需要 reliability-by-design 和统一的冗余标准 [p6]。
  3. OCI-MSA 提供 scale-up 光 PHY 规范（NRZ、WDM、BiDi），OCP 应成为 trays、form factor、可靠性等配套标准的承载地 [p12][p14][p15]。
- 关键数据：
  - 失效影响面：单外置激光源驱动单光引擎 100% blast radius；光板双激光交叉 25–50%；CWDM 4 波长 25%；NPC 加 interleaving 25%（看图）[p7]
  - OCI 带宽路线：200 Gbps 今日（OCI GEN1）；400 Gbps 2027(?)；800 Gbps TBD，>2030(?)（预测，原文带问号）[p10]
  - OCI PHY：NRZ 信令、8 个波长（λ1–λ8）一套标准激光、BiDi 单光纤（自报）[p12]
  - OCI-MSA 成立时间 March 2026，GEN1 规范见 oci-msa.org [p11]
  - 部署挑战：链路数量达"millions of links"（自报，定性）[p5]
- 提到的公司/客户/产品/标准：Microsoft Azure Cobalt 100/200、Maia 100/200/300、Azure Boost DPU [p3]；OCI-MSA、OIF（ELSFP for OCI、CMIS、COI 白皮书）、OCP、APC、IEEE、ITU-T、SROI、Open SiPhotonics for AI Systems、CPX MSA、DR4、NPO/OBO/NPC [p6][p13][p14]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（四种激光/波长冗余方式的 blast radius 对比）；p12（OCI PHY 要素：NRZ/WDM/BiDi/8λ）

### P443 Photonics-for-AI-Aligning-the-Stack-from-Components-to-Cloud（实际标题 The Disappearing DSP: Operating Linear and Co-Packaged Optics at Hyperscale）
- 讲者/机构：Stephen Manley，Oracle Cloud Infrastructure [p1] | 类型：技术分享
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [Out 后端网络：可插拔光模块/LPO/LRO]、[Up：CPO]
- 核心主张：
  1. 问题不在于要不要 DSP，而是 DSP 消失后要保留其运维职能：retimer、equalizer、FEC/BER 计数、黑匣子诊断、可归因的故障边界 [p2][p4]。
  2. 现网数据显示 LPO 链路并不比 retimed 链路更不稳定，但故障归因变难："Reliability can improve while explainability regresses" [p6]。
  3. 需要一个可测试、可在 LPO/CPO/retimed 间移植的观测契约：Detect、Localize、Remember、Reach、Remediate；OCP Optics Reliability workstream 负责需求，OIF CMIS/PLUG 负责机制 [p9][p11]。
- 关键数据：
  - 规模放大：每主机 8 条高速链路时，10K 主机→80K link ends，100K→800K，1M→8M（示意，看图）[p3]
  - Fleet rate ≈ population × per-link event rate（自报）[p3]
  - 去敏化运营数据：LPO–LPO 链路稳定性不低于同类 retimed 群体；混合厂商时 Tx/Rx 配对方向性主导结果（现网，未给具体数值）[p6]
  - POC 采用 DSP-to-DSP 消息实现 local/remote × host/media 定位、远端模块遥测、时间戳日志、自动关断、远程固件升级（实验/自报）[p10]
- 提到的公司/客户/产品/标准：OCI；OCP Networking/Optics Reliability workstream、OCP Optics Telemetry 规范草案 rev0.9；OIF CMIS/PLUG；LPO、CPO、EBO（expanded beam optics）[p11][p13][p14]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（DSP 的五项职能）；p8（主机侧链路四个故障域）；p9（运维契约五步）

### P444 Slow-and-Wide-12.8T-VCSEL-solutions（VCSEL-based High Density Interconnects）
- 讲者/机构：Oleg Shchekin，Lumentum [p1] | 类型：厂商展区/技术分享
- 方向归属（主/次）：主 [In 封装内：光 I/O]；次 [Up 机柜/超节点：CPO/NPO]
- 核心主张：
  1. 1060nm VCSEL 宽慢（wide/slow）架构可从 1.6T 可插拔扩展到 12.8T CPO，复用现有封装、光纤、连接器和 3D 传感供应链 [p2][p3]。
  2. 已有机架级 PCIe 光互连 POC，证明 VCSEL 光引擎可用于 scale-up/scale-in [p5]。
  3. 呼吁行业统一 pJ/bit 的系统边界定义和 reach/latency/cost 评价指标 [p6]。
- 关键数据：
  - 1060nm VCSEL HTOL 5000 h，8mA、115°C 烘箱，Tj 181°C（自报）[p2]
  - 形态与容量：Pluggable 1.6T/3.2T，NPO 6.4T，CPO 12.8T（看图）[p3]
  - 1.6T 阵列在 FIT<1（含 sparing）下所需通道数：32 Gbps 54 路；50 Gbps 36 路；64 Gbps 30 路（看图）[p3]
  - 1.6T 示例：8x4 50G NRZ 经 gearbox 转 8x200G PAM4（看图）[p3]
  - CPO 12.8T 示例 D2D 边宽 ~4mm，>6 Tbps/mm（看图）[p3]
  - 带宽密度 ~1 Tb/s/mm 今日，路线 ~4 Tb/s/mm；多模光纤数十米 reach（自报）[p5]
  - POC：多路 32 Gb/s NRZ 在线，OM3 多模光纤上 PCIe-5 链路无误码；光引擎路线 <2.5 pJ/bit（实验/预测）[p5]
- 提到的公司/客户/产品/标准：Lumentum、Astera Labs（Scorpio PCIe switch）、Corning；Ethernet、InfiniBand、Ultra Ethernet、PCIe、NVLink、UALink、UCIe [p3][p5]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（1.6T–12.8T VCSEL 架构表与通道冗余数）；p5（PCIe 光互连 POC 框图与实物）

### P445 Standards-and-Future-Technologies（CPO, OCI）
- 讲者/机构：Rajiv Pancholy，Director Hyperscale Strategy & Products，Broadcom [p1] | 类型：技术分享/标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/NPO/XPO]；次 [Out 后端网络：交换芯片]
- 核心主张：
  1. CPO 相对可插拔有可靠性优势，可减少 link flap 导致的训练回滚 [p3][p5][p6]。
  2. OCI 以集成光实现"可插拔的 reach、铜缆的功耗"，适合 scale-up；行业收敛到单一 scale-up 互连形态有助于形成规模与成本 [p13][p16]。
  3. CPO/OCI 规模化的障碍在先进封装、千根级光纤连接和量产自动化 [p7][p8][p9]。
- 关键数据：
  - Broadcom CPO 路线：2022 TH4 Humboldt 25.6T（100G/lane）；2024 TH5 Bailly 51.2T（100G/lane）；2026 TH6 Davisson 102.4T（200G/lane）；2028 第 4 代 CPO（看图）[p4]
  - 第 4 代 CPO 开发中；">1M device hours with 0 link flaps"（自报，看图）[p4]
  - CPO "10x reliability improvement vs. pluggables"（自报，看图）[p3]
  - Scale-out 用 CPO 替代可插拔可得 "90% Efficiency Improvement"（示意图标注，口径未说明，存疑）[p6]
  - 200G 链路总功耗与距离：DAC 7 pJ/bit/2m；Integrated OCI 7 pJ/bit/500m；DR LRO 前面板可插拔 23 pJ/bit/500m（自报，看图）[p13]
  - 1024 XPU scale-up 集群：XPU scale-up 带宽 25.6 Tbps，交换机 204.8 Tbps；每柜 64 GPU / 32 交换机；共 16 GPU 柜 + 4 交换柜；1024 GPU + 128 交换机；每单元光纤 128（GPU，BiDi）/1024（交换机，BiDi）；每柜光纤 8,192 / 32,768（看图）[p14]
  - 1M XPU 集群：单层 scale-out，一台 scale-out 交换机连接 1024 个 scale-up POD（1024×1024）；ESUN 统一 scale-up/scale-out 消息（自报）[p15]
  - CPO 挑战：每芯片封装 >1k 根光纤；需支持 400G direct drive；可拆卸光纤以支持回流焊（看图）[p7]
  - OCI-MSA GEN1：成立于 2026-03-12；BiDi 每光纤每方向 4λ，Group A 1311 nm / Group B 1331 nm，DWDM 通道位于 CWDM 栅格上（看图）[p11][p12]
- 提到的公司/客户/产品/标准：Broadcom TH4/TH5/TH6-Davisson、COUPE（EIC-PIC 键合）、ELSFP、FAU；OCI-MSA；ESUN；Broadcom CPO BiDi 白皮书 [p7][p10][p15][p16]
- 首次/记录/SOTA 声明：">1M device hours with 0 link flaps"（4 代 CPO 开发中，自报）[p4]
- 推荐配图页：p13（DAC/OCI/LRO 功耗-距离表）；p14（1024 XPU 光纤数量表）；p4（Broadcom CPO 四代路线）

### P446 System-Level-Evaluation-of-XPO-for-High-Density-Optical-Interconnects-in-AI-Infrastructure
- 讲者/机构：Daniel Mohaghegh（Hardware Engineer, Microsoft）、Sunil Priyadarshi（Senior Director, Arista）[p1] | 类型：技术分享（实测数据）
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/NPO/XPO]；次 [Out：可插拔光模块/LPO/LRO]
- 核心主张：
  1. 推理负载的单 SoC 带宽在 1–2 代内不需要更深的集成；XPO 在可服务性、低 blast radius、灵活性上作为广泛标准有优势，可考虑用于 scale-up [p7]。
  2. 实测中 FRO 余量最大；LRO 两侧表现好但对光衰减更敏感；LPO 交换侧好，Tx 需继续优化 [p18]。
  3. 下一步需多厂商互操作、LPO Tx 调参指南，并从仿真平台走向真实交换机/加速器系统验证 [p19][p20]。
- 关键数据：
  - XPO：200G/lane 时 204.8T/1OU，400G/lane 时 409.6T/1OU；液冷最高 500W/模块（25.6T coherent-lite）（自报）[p6]
  - 部署评估分三阶段，每代周期 2–3 年（自报）[p5]
  - 测试平台：Arista 设计的 212 Gbps SerDes 仿真盒，4 颗 Broadcom Agera3 retimer（每颗 x16 lane×212 Gbps），驱动 XPO 64 通道；NPC 铜 flyover 线 300/600/900 mm，32 AWG twinax（Amphenol）；集成液冷（实验）[p9]
  - Flyover 长度对应 bump-to-bump 损耗：300mm 15dB、600mm 19dB、900mm 23dB；交换侧固定 300mm [p11]
  - FRO-FRO：交换侧 BER 贴近 1e-13 底限且与加速器侧线长无关；加速器侧 22dB 时 BER 升至约 1e-12；SNR 交换侧 ≈25 dB，加速器侧 ≈24→23 dB；0dB 与 3dB 光衰几乎无差（实验，看图）[p12]
  - FRO-FRO Rx 功率中位数：交换模块 3.33→-0.28 dBm（降 3.61 dB），加速器模块 6.37→3.14 dBm（降 3.23 dB），预期降 3.00 dB（实验，看图）[p13]
  - LRO-LRO：加速器侧 BER 在 0dB 光衰时约 5e-10→7e-9，3dB 时约 1e-8→6e-8；SNR 约 20–22.5 dB（实验，看图，近似）[p14]
  - LRO-LRO Rx 功率中位数：交换 0.86→-2.39 dBm，加速器 1.47→-2.15 dBm（实验，看图）[p15]
  - LPO-FRO：交换侧 BER 底限在 1e-10 内；加速器侧 BER 在 1e-7 量级可接受范围，主要受 LPO Tx 限制（实验）[p16]
  - LPO-FRO Rx 功率中位数：交换（LPO RX）5.54→1.69 dBm（降 3.85 dB），加速器（FRO RX）1.94→-0.91 dBm（降 2.85 dB）（实验，看图）[p17]
  - 15 dB loss 下配对比较：FRO-FRO 约 1e-13；LPO-LPO 0dB 约 5e-9、3dB 约 2e-7（超过 1e-8 参考线）（实验，看图，近似）[p18]
- 提到的公司/客户/产品/标准：Microsoft、Arista、Broadcom Agera3、Amphenol Ultrapass-XR；XPO MSA、Open CPX、OCI；LPO/LRO/FRO/TRO；NPO、OBO、CPO、ELS、ILS [p7][p9][p20]
- 首次/记录/SOTA 声明："Highest Density Pluggable Optics form factor in the Industry"（自报）[p6]
- 推荐配图页：p18（各模块配对 BER 箱线图）；p7（加速器侧光模块形态对比表）；p12（FRO BER/SNR vs 损耗）

### P447 The Future of Coherent Optics in the AI Era
- 讲者/机构：Frank Chang，Sr Director, Interconnects PLM，Ciena [p1] | 类型：技术分享/厂商
- 方向归属（主/次）：主 [Across 跨楼/园区/区域：DCI、ZR/相干]；次 [底座-冷却]、[Up：XPO]
- 核心主张：
  1. 不同 DCI 场景（园区、城域、跨域 scale-across、骨干、海缆）的优先级不同，未来是多种相干架构并存 [p2][p3][p14][p16]。
  2. 功耗墙推动可插拔光模块走向液冷；XPO 在保留前面板可插拔的同时提升密度 [p8][p9][p11]。
  3. 大规模部署时以光纤为部署单位，full-spectrum transponder 一次点亮整根光纤，简化运维 [p12][p13]。
- 关键数据：
  - DCI 距离：Campus 10–20km、Metro 100km、Backbone 2,000km+、Submarine 10,000km+ [p2]
  - 海缆 Tasman Express 2250 km：WaveLogic 6 Extreme 27 Tb/s（27×1 Tb/s，162GHz，+16%）vs WaveLogic 6 Nano 23.2 Tb/s（29×800G，150GHz）（自报/现网）[p5]
  - 城域：WaveLogic 6 Extreme 76.8 Tb/s（48×1.6T，200GHz，+50%）vs WaveLogic 6 Nano 51.2 Tb/s（64×800G，150GHz）（自报）[p6]
  - Scale-across 实例：数百对光纤，每光纤对 64×800G（C&L 波段）；RLS Hyper-Rail 紧凑机框支持 16 对 C/L 光纤（自报/现网）[p7]
  - 可插拔功耗趋势：400ZR QSFP-DD 约 17W，800 ZR/ZR+ 约 25–30W，1600 ZR/ZR+ OSFP（2027）约 33–42W（看图，近似）[p8]
  - 新形态 2.4× 密度（自报）[p9]
  - XPO：液冷 12.8T 可插拔；200T in 1RU 路由器；8×XPO = 102.4T；12.8T Linear Drive / Coherent-Lite / Coherent ZR 三种模块（自报，看图）[p11]
  - 当前逐波长部署：每光纤对 128×400G×2 或 64×800G×2 个可插拔 [p12]
  - 51.2T C&L full-spectrum transponder 设想：4 个 8 通道服务模块，每个 8×1.6T modem，客户侧 6.4T CPO/NPO（概念）[p13]
- 提到的公司/客户/产品/标准：Ciena WaveLogic 6 Extreme/Nano、RLS、Staubli；1600ZR/ZR+、1600G Coherent-Lite；XPO、OSFP800、QSFP-DD800、OSFP RHS、CPO；Mini-QD 规范贡献至 OCP Cold Plate 子项目 [p6][p9][p15]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（可插拔光模块功耗 2001–2027 趋势图）；p13（51.2T full-spectrum transponder 框图）；p11（XPO 三种 12.8T 模块）

### P448 The-Interconnect-Inflection-Point-Evolving-Intra-and-Multi-Rack-Scale-Up-AI-Networks
- 讲者/机构：Akarsh Bhatnagar，Product Line Manager，Celestica [p1] | 类型：技术分享
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板、CPO/NPO/XPO]；次 [Out：可插拔光模块/LPO/LRO]
- 核心主张：
  1. 集群从单柜扩展到多柜后，scale-up 互连成为主要瓶颈：前面板热/功耗、铜缆 reach <2m、DSP 带来的时延 [p3]。
  2. XPO 是"瑞士军刀"：同一机械和热包络可换装 DAC/ACC/AEC/LPO/LRO/FRO/相干引擎，保留热插拔 [p5]。
  3. 没有单一技术覆盖全部距离，各层按密度、可服务性、热效率取舍；通过多厂商 MSA 分阶段走向量产 [p6][p8][p9]。
- 关键数据：
  - XPO：12.8T/模块，1RU 交换机最高 204.8T；盲插冷板液冷，单槽 400W+（自报）[p4]
  - ACC 约 2.5W（自报）[p5]
  - 距离分段：Passive DAC ≤1.0m（224G）；ACC 1.2–2m；AEC 2–5m；LPO 2–10m+；LRO/FRO 10–500m；相干 ZR/Lite 500m–10km+（自报，看图）[p6]
  - 铜缆 reach 低于 2m，无法可靠跨越整柜（自报）[p3]
  - 新技术：MicroLED 光引擎 sub-pJ/bit；Active Radio Cable 预计 2–10m（预测）[p7]
- 提到的公司/客户/产品/标准：Celestica；XPO MSA、Open CPX MSA、OCI MSA；DAC/ACC/AEC/LPO/LRO/FRO/ZR [p4][p10]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（铜到相干的距离分段数轴）；p8（各层级互连技术蓝图）

### P450 02_Breaking the Memory Capacity-Bandwidth Tradeoff for Agentic Inference
- 讲者/机构：Allan Cantle，CEO，Nallasway；贡献者 Amphenol、Crealien、Credo、Empower(Analog Devices)、FIT、LOTES [p1] | 类型：技术分享（概念设计）
- 方向归属（主/次）：主 [In 封装内：HBM、CXL/内存池化、D2D]；次 [推理/算力/经济性]、[底座-冷却]
- 核心主张：
  1. Agentic 推理中 KV cache 已与权重相当，容量与带宽同时受压；HBM 偏带宽、DIMM 偏容量 [p2][p8]。
  2. 以 Credo OmniConnect LSI 串行接口 + 缓冲 LPDDR5X 模块（OC-DDIMM）挂在整颗 reticle die 四周，可在不用 HBM 和先进封装的前提下兼得容量与带宽 [p3][p5][p7]。
  3. 提出 OCP HPCM 2026 模块概念（50 个内存模块 + CPC IO + 两相水冷），寻求 POC 合作 [p12][p19]。
- 关键数据：
  - 单服务实例内存：2020 dense 0.4 TB → 2023 early MoE 1.2 TB → 2026 agentic 5 TB（其中 KV cache 约 3 TB，看图）（示意，数量级）[p2]
  - 推理 token 每答案 10–100×；MoE 总参数 10×（自报）[p2]
  - Credo LSI：AXI over VSR 112Gbps SerDes，1.15 pJ/bit，单向 ~35ns；600 SerDes 东西向 IO ~8 TB/s/die；符合 OCP FCSA 5.12（自报）[p3]
  - 每 reticle die 带宽：Blackwell 两代 +0%；31%/yr 趋势（2016–2023 拟合）；Jalapeño 15.4 TB/s；Weaver-1 7.5 TB/s、Weaver-2 11.5 TB/s（≈Rubin Ultra 72%）（引用 SemiAnalysis、Hot Chips 2026；Weaver 为 Nallasway 目标，看图）[p4][p5]
  - 每 die 容量：36%/yr（至 2023）后降为 8%/yr；GB200 较 H200 降 32%，NVIDIA 低于自身趋势 2.5×；Weaver-1 800–3,200 GB，Weaver-2 608–4,864 GB，为 HBM 部件 3.2×–25×（引用 SemiAnalysis；Weaver 为目标值，看图）[p6][p7]
  - 内存挂接对比：CPU+16 MRDIMM 4 TB/1.1 TB/s/330 cm²；Vera+8 SOCAMM 1.5 TB/1.2 TB/s/178 cm²；XPU+50 OC-DDIMM 3.2 TB/7.5 TB/s/138 cm²；Jalapeño+6 HBM4 216 GB/15.4 TB/s/65 cm²（自报/引用）[p8]
  - Weaver 1 buffer：4×LPDDR5X x32 通道，9.6Gbps，12×112G 收发器；OC-DDIMM 16–64 GB，基于 M.2 的 96 pad 0.5mm pitch 连接器，6 针供 20W [p9][p10]
  - HPCM 模块：600×112G 内存 lane + 128 fabric lane（112G OmniConnect 或 224G LR）；每 XPU 0.8–3.2 TB；48V 输入，TDP 1,650W；115×150×40 mm [p11][p12]
  - 基板走线：600 差分对，最坏 7.5dB 损耗，VSR 预算 ~25dB?（原文带问号，存疑）[p15]
  - 两相水冷：-90kPa 出口负压下纯水 ~48–53°C 沸腾；CFD 2 LPM（0.4 LPM/kW 经验值）对应 ~5 kW（仿真）[p16][p17]
  - 2OU ORV3 机框 16–18 模块，30kW 预算；每模块 1.65kW = 800W XPU + 850W 内存 [p18]
- 提到的公司/客户/产品/标准：Credo OmniConnect/LSI、LOTES PrezLink CPC、LuxShare、Empower/ADI EP7502MC、Crealien；NVIDIA H100/H200/GB200/GB300/VR200/Rubin Ultra/Vera、OpenAI Jalapeño、Samsung HBM4E；OCP FCSA、HPC 子项目 [p3][p4][p12][p13]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（每 die 容量趋势与 Weaver 范围）；p8（四种内存挂接方式对比）；p2（KV cache 增长示意）

### P452 04_Modular Plug-and-Play (M-PNP) Workstream Overview, Updates, and Progre
- 讲者/机构：Dave Heinrich（HPE）、Chitrak Gupta（AMI）、Phil Leech（HPE，M-PNP 负责人）、Todd Rosedahl（Jabil）[p1] | 类型：面板/标准进展
- 方向归属（主/次）：主 [底座-机架/机械]（DC-MHS 平台管理）；次 [运维/可靠性/遥测]
- 核心主张：
  1. 目前 SCM/HPM 硬件可互操作但需改固件（Plug-and-Code），目标是通过自描述 JSON 实现无需改代码的 Plug-and-Play [p4][p6]。
  2. v0.7 规范包含 FRU 发现与启动、HPM/外设可编程器件、互操作三份规范 [p8]。
- 关键数据：
  - v0.5 于 2025 Global Summit 前发布；v0.7 于 2026 年 10 月发布；v0.9 目标 2026 Q4；v1.0 目标 2027 Q1 [p9]
  - INTEROP 规范当前为 0.3 [p10]
  - fpga2json.py 计划 2026 Q4 贡献给 OCP [p9]
- 提到的公司/客户/产品/标准：HPE、AMI、Jabil、Lattice、Intel；DC-MHS、DC-SCM 2.1、HPM Type 1、LTPI、SPDM、DMTF、M-CRPS [p8][p11]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（Plug-and-Code 到 Plug-and-Play 路线）

### P453 05_OCP NIC 2026 Gen 7 and liquid cooling – More speed and power ahead
- 讲者/机构：Thomas Ng（Intel）、Jason Rock（Dell Technologies）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [Out 后端网络：NIC]；次 [底座-冷却]、[底座-电力]
- 核心主张：
  1. OCP NIC v1.7 加入 PCIe Gen 7，信道损耗限值与 PCI-SIG CEM 7.0 对齐，避免使用昂贵的超低损耗板材 [p3]。
  2. NIC 功耗上升，需要液冷参考设计和 200W 连接器 [p6][p8]。
- 关键数据：
  - PCIe Gen 7 使 OCP NIC 可达 1.6 Tbps [p3]
  - 传统 NIC 80W 足够；新方案采用 SFF-TA-1037 4C+ EP 连接器支持 200W；需硬件互锁防止 TA-1037 卡在 TA-1002 连接器上上电 [p8]
  - 液冷设计需实心面板，~100% 热量由液体带走 [p6]
  - FRU：IPMI 三字节制造日期字段在 2027-11-24 后溢出，改用 DMTF DSP0220（OEM Record 0xC0，IANA 0xB41A00）[p5]
- 提到的公司/客户/产品/标准：Intel、Dell；PCIe Gen 7、CEM 7.0、SFF-TA-1002 1.6a、SFF-TA-1037、DMTF DSP0220、SNIA；DC-MHS [p3][p5][p7][p8]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（200W 连接器需求）

### P455 07_Open Silicon Photonics for AI Systems Extending the MHS Platform Contr
- 讲者/机构：Bijan Nowroozi（Head of Ecosystem Development, Lightmatter）、Morris Repeta（Director, Advanced Hardware Technology, Dell）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/NPO/XPO]；次 [In 封装内：光 I/O]、[底座-机架/机械]
- 核心主张：
  1. 封装 I/O 逃逸是几何问题：逻辑随面积增长、I/O 只能从周边出，且 HBM PHY 先占边缘；面阵光 I/O（APO）可突破 [p2]。
  2. 光引擎从可插拔 cage 移入托盘后，托盘需定义七项新内容；方案是扩展 DC-MHS 平台契约（机械、电源、高速信号、热、管理五个维度），引擎选择留给厂商 [p3][p4][p6]。
  3. 同一外部接口覆盖 Class-H 与 Class-V 机柜，可共用光纤设施，支持 1,000+ XPU 的 scale-up 域 [p11]。
- 关键数据：
  - 224G、reticle 级封装：铜逃逸 26 Tb/s/dir；CPO 93.6 Tb/s/dir（~3.6×，0.90 可用 beachfront）；面阵 APO 1,191 Tb/s/dir（46×）（引用 OSP for AI Systems 白皮书）[p2]
  - XPU 侧：全周边 122 Tb/s/dir；半周边+HBM（16 stacks）33；加 IO chiplet 63；对照 Gen N 40/N+1 80/N+2 160 Tb/s/dir（看图）[p2]
  - 托盘 >400 Tb/s 光纤布线；交换托盘 204.8T 级：512×400G 或 1,024×200G 端口 [p7][p8]
  - CPO 可靠性：第一代机群 MTBF 8.2M 小时，约为可插拔 10×；第二代超过 50M 运行小时（引用 Meta，ECOC 2025/OFC 2026）[p9]
  - 512 路 collective 的 straggler 尾部约降 10×；MFU 目标 55–65%（预测）[p10]
  - 网络功耗：面阵光子 <5 pJ/bit vs 电 15–25 pJ/bit；互连功耗占比 ~37%→~15%（预测）[p10]
  - 光子跳 sub-10 ns vs retimer 跳 40–120 ns（自报）[p10]
  - NVL72 铜 72 GPU/1 柜/~1m vs CPO 1,152 GPU/16 柜/~1km：16× 更大 scale-up 域，~1,000× reach，8× 端口密度（引用 SemiAnalysis 2026，看图）[p10]
  - 机柜：ORv3 MHS Class-H 600kW+，scale-up 72–144 XPU；ORv3 Next Gen Class-V 1MW+，1,024–1,152+ XPU [p11]
  - 白皮书 1.0.x 已发布，规范草案持续至 2027 [p12]
- 提到的公司/客户/产品/标准：Lightmatter、Dell、Meta（引用）、SemiAnalysis（引用）；DC-MHS、DC-SCM、ORv3、OIF CMIS、ELS、Open CPX、XPO、FPO/NPO（S-NPO、M-NPO）/CPO（2D/3D）[p4][p5][p9]
- 首次/记录/SOTA 声明：无（MTBF 数据为引用 Meta）
- 推荐配图页：p2（逃逸带宽几何对比图）；p6（FPO/NPO/CPO 托盘契约五维表）；p10（NVL72 vs 1,152 XPU CPO 域）

### P456 08_Reducing Parasitics, Improving Performance The Case for Low Inductance
- 讲者/机构：Quresh Bohra、Tony Howard（System Architect，TE Connectivity）[p1] | 类型：厂商技术分享
- 方向归属（主/次）：主 [底座-电力]
- 核心主张：
  1. AI 负载电流瞬变快，GPU 核心电压低，供电路径中的电阻和电感决定电压跌落与过冲 [p4][p12]。
  2. 让供电与回流路径紧靠可大幅降低连接器回路电感 [p5][p7]。
- 关键数据：
  - 对比连接器：12.5 A/contact、3.0 mm pitch、5 mΩ max，回路电感 ~8.5 nH（40–100 MHz，看图）[p6]
  - 优化连接器：DC 0.6 nH，20 MHz 以上 0.545 nH（仿真 Ansys Q3D）[p8]
  - AC 电阻 100 MHz ~1.2 mΩ（仿真）[p9]
  - 30°C 温升内 34 A/contact（实测，未降额）[p10]
  - 回路电感降低 ~94%（~0.54 nH，12V）（仿真，看图）[p11]
  - AI 机柜功耗约 100 kW+；±400V 或 0–800V 机柜供电 [p2][p4]
- 提到的公司/客户/产品/标准：TE Connectivity；ORW [p2]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p11（优化前后电感对比摘要）

### P457 09_SBSA Advancing Arm Server System Architecture in the OCP Ecosystem
- 讲者/机构：Dong Wei（Arm Fellow）、Samer El-Haj-Mahmoud（Distinguished Engineer），Arm [p1] | 类型：标准进展
- 方向归属（主/次）：主 [量子/其他]（服务器系统架构/固件标准）；次 [运维/可靠性/遥测]
- 核心主张：
  1. 逐平台适配 Arm 服务器成本高，SystemReady（BSA/SBSA、BBR、BBSR、SBMR + ACS 测试）提供统一平台契约 [p3][p4]。
  2. Arm 把 SBSA 和 SBMR 贡献给 OCP，由 OCP 中立治理成为行业基线 [p7][p8]。
- 关键数据：
  - SBSA 和 SBMR 于 2026 OCP EMEA summit 贡献给 OCP [p8]
  - 当前公开版本 SBSA 8.0（2025-07）；OCP SBSA 8.1 REL 目标 2026 年底 [p10]
  - SBMR 3.0 ALP2（2025-10）；OCP SBMR 3.0 REL 目标 2026 年底 [p12]
  - Arm AGI CPU 参考服务器符合 SystemReady SR，SBSA Level 6 [p6]
- 提到的公司/客户/产品/标准：Arm、NVIDIA Grace；UEFI、ACPI、SMBIOS、Redfish、MCTP、PLDM、SPDM、IPMI、CXL [p4][p6]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（SystemReady 平台契约分层图）

### P458 10_SPEC CPU 2026 – What's new, what's improved, and why it matters
- 讲者/机构：David Reiner，SPEC President [p1] | 类型：标准进展
- 方向归属（主/次）：主 [推理/算力/经济性]（CPU 基准）
- 核心主张：
  1. ISA 和厂商增多、agentic AI 提升服务器 CPU 的重要性，需要高质量基准 [p6]。
  2. SPEC CPU 2026 扩大 benchmark 和 workload 覆盖，前端瓶颈从分支预测转向 icache/iTLB [p10][p11]。
- 关键数据：
  - 52 个 benchmark（原 43），16.7M 行代码（原 7.1M）[p10]
  - SPECspeed Integer 并行化 9/13（原 1/10）；内存 64GB（原 16GB）[p10]
  - SPECrate Integer workload 20→57（~2×）；SPECrate FP 13→47（~4×）[p11]
  - 新类别：Security（750.sealcrypto_r）、Analytics（854.graph500_s）[p12][p13]
  - SPEC CPU 2017 已发布结果 46,247+ [p9]
- 提到的公司/客户/产品/标准：SPEC、SERT、ENERGY STAR、EU Lot 9、ISO/IEC 21836 [p5]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（SPEC CPU 2026 新变化）

### P459 Accelerating-High-Power-Server-Design-Through-Board-Level-Electro-Thermal-Co-Simulation-of-VRMs-and-PDNs
- 讲者/机构：Mike Wu（Microsoft）、Steven Chien（Wiwynn）[p1] | 类型：技术分享
- 方向归属（主/次）：主 [底座-电力]；次 [底座-冷却]
- 核心主张：
  1. 用串/并联模型由铺铜率推导 PCB 等效导热系数，并由材料组分推导器件等效导热系数，可在早期缺少厂商热模型时进行仿真 [p10][p13][p22]。
  2. 电-热协同仿真（PI→热→PI）比非耦合方法更接近红外实测，并减少网格与计算时间 [p19][p21]。
- 关键数据：
  - 12 层 2.34 mm PCB 等效导热：面内 64.2 W/m·K，厚度方向 0.36 W/m·K [p11]
  - 二极管：串联模型 keff 0.96 W/m·K，与实测偏差 3%（环氧参考值 0.7 W/m·K 时偏差 10%）（仿真 vs 实验）[p13][p14]
  - MOSFET：keff 106 W/m·K；与实测偏差 12–15%，2R 模型 8–11%，两者相差 4–5% [p15][p16]
  - ET co-sim：网格数 0.54×、计算时间 0.55×、与实测偏差 0.9×（-46%/-45%）[p20]
- 提到的公司/客户/产品/标准：Microsoft、Wiwynn [p1]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p21（IR 照片 vs ET co-sim vs 非耦合仿真热分布）

### P460 Architecting-Openness-How-Switches-Enable-the-Future-of-Open-Adapter-Card-Platforms
- 讲者/机构：Chris Blackburn，Director of Platform Solutions Architecture，Astera Labs [p1] | 类型：厂商技术分享
- 方向归属（主/次）：主 [Up 机柜/超节点：UALink/ESUN]；次 [Out：交换芯片]
- 核心主张：
  1. OAC（Open Adapter Card）填补 AIC 与 OAM 之间的空白，支持更高功耗和更大 PCB [p3]。
  2. OAC 系统需要两类交换：scale-up 交换（UALink/ESUN/私有）和 PCIe 交换（连接 XPU、CPU、NIC、SSD）；开放交换标准有助于打破锁定 [p4][p5][p11]。
- 关键数据：
  - 对比：AIC 600W/346cm²/无专用 scale-up lane；OAM 700W/168cm²/最多 x112（7×x16）；OAC 5,000W*/598cm²/最多 x112*（*规范仍在制定）[p3]
  - 系统含 8 或 16 个 OAC 模块；1–2 CPU、8–16 XPU、8 NIC、8–16 SSD，需 PCIe 交换扩展 [p4][p7]
- 提到的公司/客户/产品/标准：Astera Labs；OAC、OAM、UALink、ESUN、PCIe [p4][p11]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（AIC/OAM/OAC 规格对比表）

### P461 Co-Packaged-Copper-at-448G-Balancing-Electrical-Efficiency-with-System-Level-Complexity
- 讲者/机构：Sakina Naqvi（System Architect）、Usman Saeed（Principal System Architect），TE Connectivity [p1] | 类型：厂商技术分享
- 方向归属（主/次）：主 [Up 机柜/超节点：铜缆/背板]；次 [In 封装内]
- 核心主张：
  1. 448G 下 PCB 走线距离过短，CPC（Co-Packaged Copper）让信号从封装直接进入 twinax，插损低于 NPC [p2][p5][p6]。
  2. CPC 使线缆/连接器成为封装的一部分，带来公差、应力、翘曲、热环境等系统复杂度 [p7][p8]。
  3. CPC 与 CPO 可共享参考架构，是向 CPO 过渡的路径 [p9]。
- 关键数据：
  - 250 mm 30AWG twinax vs 254 mm stripline：@112 GHz 插损 ~4 dB vs ~23 dB（看图）[p3]
  - 448G 至背板（PAM6）：CPC @90 GHz ~6 dB vs NPC ~12 dB，不含封装损耗（仿真，看图）[p5]
  - 448G 至 I/O（PAM4）：CPC @112 GHz ~7 dB vs NPC ~14 dB（仿真，看图）[p6]
  - 1m 线缆每升温 10°C 插损增加 3–5%；90°C 时 ΔIL ~2.4 dB（看图）[p8]
- 提到的公司/客户/产品/标准：TE Connectivity；CPC、NPC、CPO [p2][p9]
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（448G CPC vs NPC 背板信道插损对比）；p3（twinax vs PCB 走线插损）
