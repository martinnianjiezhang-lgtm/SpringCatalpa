---
title: "B71 · DAY4 · We5-B-光发射机与VCSEL"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We5-B-Arista-光发射机与收发.pdf（第1–9页）
- 讲者/机构：Sunil Priyadarshi（Senior Director, AI & Cloud Network Systems），Arista Networks；共同作者含 TerraHop US（Hao Liao、Gavin Gu 等）| 题目：Industry's First 12.8T 8×DR8 High-Density Liquid-Cooled 64-Channel Pluggable XPO Optical Module for Scale-Up | 类型：学术论文（We5-B3，产业样机演示）
- 方向归属（主/次）：主 4 Scale-up/in（XPO）；次 3 Scale-out 224G（212G/lane PAM4 电芯片/DSP）
- 核心主张：
  1. 演示"业界首个"12.8T 8×DR8 液冷可插拔 XPO 模块，集成 64×212 Gb/s PAM4 通道。
  2. 全部 64 路 TX 满足 IEEE P802.3dj/df 规范，通道间一致性好。
  3. 集成液冷可有效管理高功率密度光器件与 DSP 的热。
- 关键数据：
  - 结构：两块相同的 32 通道 paddle card，每块 6.4 Tb/s（32×200 Gb/s 通道口径）；每块集成 4 个 octal DSP、PIC、TIA；每块 4×MPO-16 光接口；独立电源/低速控制卡，直接 48 V 输入；TX/RX 对侧布置以降串扰 [p3][p4]
  - TX（64 通道）：平均光功率 2.75 dBm；ER 4.33 dB；TECQ 2.39 dB；RLM 0.99 [p6]
  - RX（64 通道）：loopback BER ~10^-13–10^-12；灵敏度约 -7 至 -7.5 dBm OMA @ BER=2.4×10^-4 [p7]
  - 热：冷却液入口 25–45 °C、0.3 LPM 下，8 颗 DSP 约 50–74 °C，8 颗 CW 激光器约 36–57 °C [p8][p9]
- 提到的公司/客户/产品/标准：Arista、TerraHop；IEEE P802.3dj/df；MPO-16；48 V 供电；液冷 manifold
- 与业界对比或记录声明：标题与总结页自称 "Industry's first 12.8T 8×DR8 liquid-cooled pluggable XPO module" [p1][p9]；未给出与他家的对比数据。
- 推荐配图页：p3（XPO 模块爆炸图：双 paddle card、冷板、光连接器）；p5（64 通道 TX 眼图墙）；p7（64 通道 Rx 灵敏度 BER 曲线）；p9（总结页）

### 0923-We5-B-NVIDIA-高速VCSEL与共封装.pdf（第1–31页，其中 p18/p20/p28 为重复页）
- 讲者/机构：Daniel Kuchta，NVIDIA（讲稿声明：综述报告，非 NVIDIA 产品报告，所引技术不代表背书）| 题目：Progress of High-speed VCSELs and VCSEL-based Co-Packaging for Short Reach Communications | 类型：邀请报告（综述）
- 方向归属（主/次）：主 4 Scale-up/in（VCSEL-based CPO/NPO）；次 3 Scale-out（>=100G/lane 直调 VCSEL、光源）
- 核心主张：
  1. VCSEL 技术持续进步，多家已演示全链路 <=1 pJ/bit，"其他技术难以超越"。
  2. VCSEL 型 NPO 正获关注；"Wide-n-Slow" 用 NRZ 换取低时延与低 BER，有吸引力。
  3. 与多芯光纤（MCF）/光纤束兼容以节省空间；VCSEL 直调仍在不断刷新速率记录。
- 关键数据：
  - 100G/λ PAM-4 VCSEL 已由多家商用（400G-SR4、400G-SR4.2、200G-SR2、200G bidi）；100G/λ NRZ 为新进展；>200 m 的结果均为 SMF [p5]
  - Institute of Science Tokyo（H. Ibrahim 等，CLEO 2026/ECOC 2026）：1060 nm 单模 VCSEL，BTB 仅眼图、未报 BER：150G NRZ（ER 1.8 dB，3.5 µm OA，3.5 mA 偏置）、256G PAM-4（ER 2.2 dB，TDECQ ~5 dB，4 µm OA，6 mA）、275G PAM-6；另有 120G NRZ 2 km SMF、200G PAM-4 1 km SMF、230G PAM-4 500 m SMF；-3 dBo 带宽 ~60 GHz，-3 dBe 带宽 ~45 GHz [p6]
  - 华为 850 nm 多模 VCSEL（35 GHz BW）：240 Gb/s PAM-6 BTB（225 Gb/s 净）；212 Gb/s PAM-6 60 m OM4（200 Gb/s 净，KP4 FEC），Rx 用 201 tap Volterra + 噪声消除 + MLSE [p7]
  - PAM-8 记录 288 Gb/s（850 nm，6–7 µm OA，8 mA，23 GHz BW，100 m OM4，RNN 均衡，20% SD-FEC 后 240 Gb/s 净）；Berxel 相关 [p8]
  - 商用 200G VCSEL 表（RT 带宽 / 距离）：850 nm：Broadcom 44 GHz、50 m OM4+；Coherent 45 GHz、80 m OM4；Sony >40 GHz、100 m OM4；华为 35 GHz、60 m OM4；Berxel 41 GHz BTB。1060 nm：FujiFilm 35 GHz；Berxel >44 GHz、30 m OM2 / 50 m OM5；PicoJool 980 nm 37 GHz [p11]
  - IBM MOTION（arpa-e）：Phase1 16ch@56G NRZ、SiGe、1 波长、400 µm 间距、4 pJ/bit、25¢/Gig；Phase2 32ch@112G PAM4、CMOS、2 波长、300 µm 间距、13×13 mm 玻璃载板、15×15 mm 可焊 CPO，能耗写为 "3* pJ/bit"（星号含义幻灯未注明），成本 TBD 但 <25¢/Gig；2026 年进展：子组件已制成、收发 IC 电测通过，首批完全对准功能件计划 2026 年 Q4（看图核实）[p14]
  - Aperion 3.2T MM VCSEL NPO（106 Gb/s/ch）：1.5 pJ/bit（PAM-4）；<0.1 FIT / 5T VCSEL 器件小时；21×33 mm OIF 兼容封装，<1 W/cm²；约 60 Tb/s xPU 逃逸带宽 [p16]
  - 未具名厂商 32ch@128G NPO/CPO：106–128 Gbps/lane，850 nm，1.4 pJ/bit，17×25 mm，4×MPO16 [p17]
  - 新光纤提案：约 26/80 µm（芯径/包层）、1060 nm 下 EMB ~5 GHz；理由：50/125 芯径对 200G PD（<=20 µm）过大，80 µm 包层可更小弯曲 [p19]
  - Eliyan：Wide-n-Slow 2D µVCSEL，4×56G/106G NRZ 替代单路 224G PAM；带宽密度 ~10 Tbps/mm；NRZ 50 m+ MMF；12.8T XPO 示例：主机 64×224G PAM4、线缆 256×56G NRZ [p21]
  - ams OSRAM 850 nm 薄膜 VCSEL（Si-TSV）：25 µm 间距；32 Gbps NRZ 无误码，Q ~10；3 mA×2.6 V=7.8 mW，~0.25 pJ/b（仅 VCSEL）；150 °C 结温过应力 2000 h 无失效 [p22]
  - LightXcelerate 1060 nm：19 芯 MCF、每芯一颗 VCSEL、每芯 56 Gb/s PAM，合计 1 Tb/s/根光纤 [p23]
  - Coherent 1060 nm 六角 µVCSEL 阵列：37 发射体、70 µm 间距（含背面透镜）；32 Gbit/s（6 mA，Vpp 0.4 V，无 DSP，ER 3.9 dB）；106 Gbit/s（12 mA，7 taps Rx&Tx，TDECQ 2.52 dB）；单发射体带宽可达 100 Gbit/s PAM4，带宽密度 >9 Tbit/s/mm² [p24]
  - NVIDIA 研究概念（"Exploratory NVIDIA concept. Not a product plan"，仅建模目标、测量待定）：50 Gb/s NRZ/光纤，~3.0 pJ/bit（host-to-host 建模），10 m，raw BER 目标 <10^-12，每 GPU 57.6 Tb/s TX + 57.6 Tb/s RX（12 引擎×4.8 Tb/s/方向；16 ribbon×6 光纤×50G）；CMOS 光背板 + 带透镜 VCSEL/PD 芯片 + 垂直光纤连接器（看图核实）[p26]
- 提到的公司/客户/产品/标准：Institute of Science Tokyo、Huawei、Berxel、Broadcom、Coherent、Sony、FujiFilm、PicoJool、Adtran（1060 nm 单模 VCSEL Tx 阵列，<1 W，SMF-28 2 km）、IBM（MOTION/POWER10）、Fujitsu Optical Components（MCF CPO/收发结构，ECOC2025 论文：16 路 50G NRZ、2 km MCF）、Aperion、Eliyan、ams OSRAM、LightXcelerate、OM4/OM5、OIF、KP4 FEC、XPO
- 与业界对比或记录声明：VCSEL 直调记录：256G PAM-4、275G PAM-6（Science Tokyo，BTB，无 BER）[p6]；PAM-8 288 Gb/s [p8]；PAM-6 240G BTB 有 BER（华为）[p7]。
- 推荐配图页：p5（>100G MMF VCSEL 速率-距离总览散点图）；p11（商用 200G VCSEL 厂商对比表）；p14（IBM MOTION Phase1/2 参数表）；p21（Eliyan Wide-n-Slow 与 PAM 对比）；p24（Coherent 六角 µVCSEL 阵列）

### 0923-We5-B-ST-光发射机与收发.pdf（第1–29页）
- 讲者/机构：Frederic Boeuf（报告人）等，STMicroelectronics（Crolles）与 CEA-Leti（Grenoble）| 题目：Advanced Industrial Silicon Photonics Platform on 300mm wafers for Optical Interconnect and Beyond（p1 看图核实）| 类型：邀请报告
- 方向归属（主/次）：主 3 Scale-out 224G（硅光调制器/PD，PIC100 面向 800G/1.6T 可插拔）；次 4 Scale-up/in CPO（TSV、紧凑调制器、InP D2W 光源）
- 核心主张：
  1. 300 mm 硅光自 2013 年起在 ST 为工业现实；PIC100 平台满足 800G/1.6T 可插拔光学需求。
  2. 面向 CPO 的紧凑调制器与 TSV 研发进行中；平台适合需要 III-V 异质集成的下一代 NPO/CPO。
  3. 300 mm 晶圆上的 InP die-to-wafer 研究进行中。
- 关键数据：
  - 路线图：PIC25G（2012，25 GBd NRZ，量产）→ PIC25G-P3（2016，53 Gbd PAM4，量产）→ PIC50（2017–2022，传感，研究）→ PIC100G（2023–2026，112 Gbd PAM4，量产）→ PIC100TSV（2025–2028，紧凑调制器/TSV/CPO ready，开发中）→ PIC200G（200 GBd，Gen5 调制器、光源集成、材料异质集成，研究）；波长 1.31/1.55 µm [p4]
  - 光栅耦合器（晶圆测试用）：损耗 2 dB（TE），1 dB 带宽 ~35 nm；边缘耦合（倒锥）@1310 nm：TE 0.90 dB / TM 0.95 dB，产品用 TE/TM <~1 dB 典型，带宽 >100 nm [p11]
  - Ge 光电二极管：暗电流 <10 nA（-1 V，25 °C，典型）；响应度 ~1 A/W（-1 V，O 波段）；带宽 80 GHz（-1 V）、>90 GHz（-2 V）；适合 Rx 侧 200G/lane [p12]
  - 相移器 PIC25G→PIC100G：调制效率 2x（24.6°/mm @1.8 V，损耗 2.3 dB/mm @1.8 V）；RC 乘积降 3x；1/(R^0.5·C·L^0.5) 提高 2.2x（Lmod 对应 ER=4.5 dB）；低损耗传输线驱动下 50 GHz 带宽 [p13]
  - Scale-up CPO 概念：光 I/O 1 mm×3 mm 对应 1~2 Tbps，~10 fiber/mm，约 15 个 IO 合计 ~100 Tbps（围绕 xPU/HBM）；需要紧凑调制器、TSV、µ光学集成 [p14]
  - 微环调制器 Gen1：R=8 µm，深脊+角结；35 pm/V @-1.5 V；Q ~2900；Feo ~70 GHz @-1 V [p16]
  - GeSi EAM（C 波段）Gen1：L=40 µm，Vdc=-1.5 V/2 Vpp；EO 带宽 >>110 GHz（-0.5 V 与 -1.5 V 曲线，至 100 GHz 仍在 -3 dB 以内）；1550 nm 处读图约 IL 7.5 dB、ER 2.8 dB、LPP 12.5 dB（读图估计，看图核实）[p17]
  - 波导损耗：SiN 波导 O 带 ~0.6 dB/cm、C 带 ~0.6 dB/cm；Mid RIB（150 nm slab）长距离布线波导 0.6 dB/cm（w=0.4 µm）；Deep RIB（50 nm）调制器处波导 1–1.4 dB/cm（看图核实）[p10]
  - TSV：Middle pitch 45 µm、深 100 µm、直径 10 µm；O 波段 MRIB 单模波导传播损耗约 0.055–0.065 dB/mm（看图核实）[p18]
  - InP/Si 异质：300 mm SOI 上放 100 mm InP 完成激光/SOA/OPA 器件设计验证（8.5 mm×0.7 mm 芯片：激光器、2×SOA、16 通道 OPA 调制器与天线）；InP D2W 键合于 PIC100 背面（G. Bruel 等投稿中，看图核实）[p24][p28]
- 提到的公司/客户/产品/标准：STMicroelectronics、CEA-Leti、Science 相关合作（U-Tokyo/ST、MPQ/C2N）；引用 IEDM 2013/2019/2021、OFC 2026（S. Cremer）、G. Bruel（ST/LETI，submitted）；应用含 LiDAR、光子传感
- 与业界对比或记录声明：无明确 SOTA/record 声明；引用自家 PIC100G 已在 OFC 2026 量产报道 [p4]
- 推荐配图页：p4（ST 硅光平台代际路线图）；p13（相移器 PIC25G vs PIC100G 对比）；p14（可插拔 vs Scale-up CPO 示意）；p12（Ge PD 带宽曲线与参数）

### 0923-We5-B-中兴-光发射机与收发.pdf（第1–15页；p8 为与 NVIDIA 讲稿重复页）
- 讲者/机构：Baoluo Yan 等（中兴通讯 ZTE，含 ZTE Photonics Technology Japan；中国联通研究院），We5-B（Wed-B2）| 题目：19.1-THz Tunable Wideband TFLN/SiPh Hybrid Integrated 800G CFP2 Transceiver for AIDC Scale-Across Clusters | 类型：学术论文
- 方向归属（主/次）：主 2 Scale-across/DCI（CFP2/ZR+ 可插拔、S+C+L 宽带）；次 1 相干/高波特率器件（TFLN/SiPh COSA、SOA、ITLA）
- 核心主张：
  1. 展示混合 TFLN/SiPh COSA + 超宽带 SOA 的 CFP2 相干收发器，在 19.1 THz S+C+L 上实现 800G PS-16QAM；输出 0 dBm、Tx OSNR >35 dB、节省光纤 74.8%（讲者原文）。
  2. 分布式 LLM 训练的 scale-across 域需 >10 Tb/s 带宽，故更大线路侧容量是方向；DCI 采用新波段收发器取决于客户是否愿意采用。
  3. 产品方向：FST + OMC 架构的高容量高密度 DCI-BOX、1.6T ZR/ZR+/CFP2、S+C+L 收发器（若客户有兴趣）。
- 关键数据：
  - 背景：单 DC 电力 50–300 MW（引 OFC2026 Microsoft Workshop），下一代 LLM 训练需约 1–5 GW；Google 俄亥俄+爱荷华（4 DC，80 km）、NVIDIA（3 DC，40 km）等 scale-across 规划 [p4]
  - LLM 训练功耗表（EPOCH AI 引用）：Claude Mythos 2026 MoE 10T 参数，训练算力估计 6.1e27 FLOPs，GPU 数量约 80 万（est），功耗 ~2.2 GW（est）[p3]
  - 带宽估算（数据并行）：GPT-4 1.8T：有重叠 >3.1 Tb/s，无重叠 61.7~308.8 Tb/s；3T 模型：>5.2 Tb/s / 102.9~514.7 Tb/s；Claude Mythos 10T：>17.3 Tb/s / 343.1 Tb/s~1.7 Pb/s（表中行标签"GPT-3 3T"为原文，疑为标注错误，照录）[p5]
  - 器件：ITLA 支持 C+L 12.2 THz、S 波段 6.6 THz；COSA 带宽约 70 GHz；DSP-ASIC 137 GBd 800G PS-16QAM [p10]
  - TFLN 调制器 Vπ=2.2 V @1550 nm；平均调制损耗比 SiPh 低 3.40 dB（S 波段 28.3 vs 31.7 dB）、低 5.54 dB（C+L 27.56 vs 33.1 dB）；COSA 尺寸约 26.5×18.9×3.7 mm [p11]
  - TFLN 调制后仅约 -12 至 -13 dBm 输出，低于 ZR/ZR+ 要求的 -8 dBm 下限；加宽带 SOA 后全 19.1 THz >0 dBm，带功率反馈环，非线性代价 <0.5 dB；SOA 电流 204 mA/pol（S 波段）、102 mA/pol（C+L）[p12]
  - Tx OSNR：S 波段 6.75 THz + 无缝 C+L 12.35 THz，全带 >35 dB（峰值 38.3 dB，S 波段短波端 35.0 dB）；B2B OSNR 容限约 24.5–24.9 dB（C/L 与 S 长波 4 THz 一致），S 波段最短波长处 25.67 dB（差近 1 dB，因尚未做 ABC 算法校准）；平均 FEC 门限 3.7×10^-2 [p14]
  - 演进：2023 实时 S 波段相干收发器；首款 S 波段 nano-ITLA 17.5 dBm；全硅光 S+C+L 15.75 THz 1.2T 板载收发器；本工作为 19.1 THz 800G CFP2（OFC26 W3.1、W1E.3 引用）[p9]
- 提到的公司/客户/产品/标准：ZTE、China Unicom、Microsoft、Google、OpenAI、NVIDIA（引用）、EPOCH AI；ZR/ZR+、CFP2、OSFP、DCI-BOX、FST、OMC、PCS-16QAM、空芯光纤（研究方向，"部分场景无收益"）
- 与业界对比或记录声明：自称 19.1 THz 为 CFP2 可插拔宽带范围（S+C+L，800G PS-16QAM，0 dBm 输出、Tx OSNR >35 dB、节省光纤 74.8%）；未见明确"首次/record"字样（p9 时间线标 "This work"）；标题页英文原题含 19.1-THz 宽带（看图核实）[p1][p9][p15]
- 推荐配图页：p5（LLM 训练流量模型与带宽估算表）；p11（TFLN 与 SiPh 调制损耗曲线及 COSA 结构）；p14（Tx OSNR 与 B2B 容限 BER 曲线）；p15（结论与产品方向）

## 本批小结
1. 短距 Scale-up 光互连出现"慢而宽"路线：NVIDIA 综述、Eliyan（56G/106G NRZ 多通道替代单路 224G PAM）、Coherent µVCSEL 阵列（>9 Tbit/s/mm²）、Aperion 与 IBM MOTION 均给出 <=1.5 pJ/bit 量级的 VCSEL NPO/CPO 数据（来自 NVIDIA、Arista 之外的 VCSEL 综述，并与 Arista XPO 的 DSP 型 212G PAM4 路线形成对照）。
2. Scale-up 形态上出现"高密度可插拔 XPO"与 VCSEL/硅光 CPO 并行：Arista 12.8T XPO 用 64×212G PAM4 + 液冷（DSP 50–74 °C），ST 展示 ~100 Tbps CPO 概念，说明散热与密度是共同约束（Arista、ST、NVIDIA）。
3. 直调 VCSEL 速率记录持续推高但集中在 1060 nm 与 BTB：Science Tokyo 256G PAM-4/275G PAM-6（无 BER），华为 PAM-6 200G 净速率带 KP4 FEC，商用 200G 850 nm 厂商带宽 35–45 GHz（NVIDIA 综述）。同时提出 ~26/80 µm 新 MMF 与 MCF 的需求（NVIDIA、LightXcelerate、ams OSRAM）。
4. 硅光代际路径清晰：ST PIC100G（112 Gbd PAM4）已量产，向 PIC200G 需要 Gen5 调制器、TSV 与 III-V 光源集成；Ge PD >90 GHz、GeSi EAM >110 GHz、MRM ~70 GHz 提供 200G/lane 器件基础（ST）。
5. Scale-across 光模块向宽带扩展：ZTE 用 TFLN/SiPh 混合 COSA + 宽带 SOA 把 800G CFP2 推到 19.1 THz S+C+L（Tx OSNR >35 dB，光纤节省 74.8%），但讲者也承认商用取决于客户是否接受新波段，并同时推进 FST/多 rail 的 DCI-BOX（ZTE）。
6. 需求侧论证：ZTE 以模型估算 scale-across 需 >10 Tb/s 级带宽，并引 GW 级集群功耗，驱动 DCI 线路侧容量增长；其估算含较强假设（有/无计算通信重叠差两个数量级），数据来自单一讲者建模。
