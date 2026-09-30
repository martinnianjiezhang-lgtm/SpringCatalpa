---
title: "方向5 Access 综合洞察"
tags:
  - ECOC2026
  - 综合洞察
---

# 方向5：固定接入与无线接入（Beyond 50G PON、50G PON、AI-FAN、FTTR、RoF、FSO/星地）

> 索引约定：〔PDF文件名去掉.pdf并去掉"合集待拆-全场-"等前缀的简写 pN〕。"连拍"类文件按页码区分讲次。口径标注：自报=讲者自述；仿真；实验（实验室）；现网/现场。带"OCR/看不清/存疑"的数字保留原标记。

## 0. 一句话结论 + 5条核心判断

**一句话结论：** 固定接入正在同时走两条时间轴：50G PON+FTTR+AI-FAN 是 2026–2030 的现网商用主线（中国移动、华为、Orange、Nokia 均给出确定的预算与部署口径），而 100/200G VHSP 仍处于"三路线并存、2027–2028 才选型、2035 前后商用"的技术竞赛期；直检 SSB/DCPC/VSB 把色散问题挪到 OLT 数字侧，相干 PON 则靠 ONU 侧 SOA 门控/功率预均衡和软判决 LDPC 把突发动态范围做成"可实现"，两条线在 2026 年都拿出了>30 dB 预算的实验结果，但成本判据（百万用户每美元性能）尚无定论。

**核心判断 1：VHSP 选型尚未收敛，标准时间线决定了 2026–2028 是"证据窗口"而非"产品窗口"。** Verizon 给出的时间线：2022 立项、2025 G.Sup88 批准、2027 各类别选技术、2028 最终选择、2028–2033 标准、2035+ 商用〔0920-pm-Su3-F-02-Verizon p11〕（自报）；Orange 更保守，VHS-PON 网络运营约 2040，且假定无 G-PON 共存〔0920-pm-Su4-F-01-Orange p10, p11〕；Sumitomo 引用的标准化时间线为 2027–2028 技术选择、2031–2032+ 批准与部署〔0920-pm-Su3-F-04-住友电工 p4〕。开场投票：混合 42%、相干 31%、IMDD 27%（现场听众倾向混合方案，但样本为 workshop 听众）〔0920-pm-Su3-F-01-主席-开场 p6〕。机制：运营商需求（100/200 Gb/s、1×128、E2 35 dB、20/30 km、20 km 差分距离）过于苛刻〔0920-pm-Su3-F-02-Verizon p5〕，任何单一技术都在成本、预算或共存上存在短板。

**核心判断 2：直检路线的关键不是"能不能"而是"色散代价搬到哪里"。** 共存 GPON 要求 CD 容限≥120 ps/nm（1370 nm、20 km 最坏 119.3 ps/nm）〔0921-Mo5-G连拍 p4；0921-C2.2厅PON连拍 p89〕。方案谱系：DCPC 容限约翻倍、需按 CD 分组；SSB 仿真在 120 ps/nm 罚值<1.5 dB、3 dB 罚值下容限 320 ps/nm（Huawei 仿真）〔0921-C2.2厅PON连拍 p98〕；Nokia Bell Labs PDP 的 Dual-SSB 实现 224 Gb/s 单波长、170 ps/nm@3.5 dB 罚值，加静态 DCPC 后覆盖 0–340 ps/nm、预算约 33 dB（实验）〔0924-PDP-C-5-NokiaBellLabs p13–p15〕；Nokia 的 VSB 只用 DD-MZM，100 Gb/s 在 0–125 ps/nm 罚值<3 dB（实验）〔0921-Mo5-G连拍 p18〕。代价：SSB 灵敏度偏低（NTT：50 Gbaud SSB 灵敏度约 -18 dBm 时 CD 罚值<4 dB）〔0920-pm-Su4-F-04-NTT p7〕。

**核心判断 3：相干 PON 在 2026 年突破了"突发动态范围"和"预算"两个门槛，剩余问题是成本与 ONU 侧激光/放大器。** Nokia Bell Labs：120G SP-BPSK 上行 OPB 44.5 dB，480G DP-QAM4 41.1 dB，960G DP-QAM16 26.4 dB（20 km，BER 2×10⁻²，实验）〔0924-Th2-D1-NokiaBellLabs p12, p14, p15〕；上海交大+中国电信首次现场试验 57 km/约 34 dB 损耗现网光纤，200G 预算 42 dB、300G 39 dB（离线 DSP）〔0924-Th2-D4-上海交大与中国电信 p16, p20〕；复旦 100G 实时 FPGA 突发相干，最大预算 45.7 dB〔0924-Th2-D3-复旦大学 p16〕；Huawei 用 Soft-LDPC 在静态增益 TIA 下达 24 dB post-FEC 无错动态范围（标准要求 20 dB）〔0924-Th2-D2-华为 p13, p3〕。

**核心判断 4：FTTR 的价值锚点是"可靠性与确定性时延"，不是峰值速率。** 户内 Wi-Fi 承载约 70% 最后一跳流量，听众投票 63% 选"高可靠性"（约 16 人，小字不确定）〔0920-am-Su1-D-01-主席-开场 p2, p4〕；Huawei 用 Doherty 阈值<400 ms 反推接入 RTT≤20 ms〔0920-am-Su2-D-02-华为 p4〕；Fraunhofer HHI 仿真显示 MAC-PHY 联合预编码（Split C）吞吐最多 +75%、Split B 1%-worst 时延 -66%〔0920-am-Su2-D-03-FraunhoferHHI p12–p14〕；中国移动定义 10G FTTR 物理层 Ra/Ra+ 预算 0–18/0–21 dB 并在 CCSA 达成共识〔0920-am-Su1-D-03-中国移动 p9〕。

**核心判断 5：AI 在接入网有两个不同层次，只有"确定性调度/遥测控制"有可测收益，"AI-FAN 算力总线"仍是架构主张。** 可测：Nokia Deterministic BW Mapper 把 NP-hard 多流冲突消解变为有界启发式，计算量约 10² 量级并近似线性增长（对比穷举至 10¹⁴ 量级，柱高目测）〔0922-Tu1-F2-NokiaBellLabs p5〕；NTT 光辅助 RAN 控制中断时间 1.63 s→0.54 s〔[主分析师笔记] 10 NTT Tu1-F5〕。未验证：中国移动"PON+FTTR 算力总线"端到端 RTT<20 ms 属自报〔0920-am-Su1-D-03-中国移动 p16〕，华为 AI-FAN 算力分层（终端 T 级/边缘 100T 级/云 P 级）为架构示意〔0920-am-Su2-D-02-华为 p6〕。

---

## 1. 需求与网络架构

### 1.1 运营商与客户口径的需求数字

| 来源 | 需求/规模数字 | 口径 | 索引 |
|---|---|---|---|
| Verizon | VHSP 系统总容量 100 或 200 Gb/s；ODN：最大 1×128 分光、E2（35 dB）预算、20/30 km、20 km 差分距离；6 种业务用例、6 种共存场景；另需 DFOS 传感与最小功耗 | 运营商愿望（自报） | 〔0920-pm-Su3-F-02-Verizon p5〕 |
| Orange | VHS-PON 候选 2×100 或 4×50 Gbit/s；Class C+ 必需、可能 Class D（第二级分光达 1:256）；现网 OLT 分光比 1:64–1:128 | 运营商（自报） | 〔0920-pm-Su4-F-01-Orange p11, p3〕 |
| Orange | 1:256 需预算>35 dB，突发时序开销>30%（含 FEC）；G+XGS-PON Combo 卡+1:128 分光降低新增 OLT 卡数 | 自报 | 〔0920-am-Su1-I-03-Orange p11〕 |
| 中国移动 | 千兆用户>2.58 亿（占 36.8%），宽带用户 6.7 亿；10G PON 端口 3286 万（2026 H1，工信部）；2025 万兆现场试验 168 处 | 国内统计/现网 | 〔0920-am-Su1-D-03-中国移动 p4〕 |
| 中国移动 | 工业 PON：100 μs 确定性低时延、99.999% 可靠性；ToC 时延 50→10 ms@99.99%，ToB 5→1 ms@99.9999%；上行占比升至 40%–50%；端侧算力 0.5–1 TFLOPS、边缘 100 TFLOPS | 自报 | 〔0920-am-Su1-D-03-中国移动 p10, p5〕 |
| Huawei | 接入 RTT≤20 ms（=400−230 大模型−50 运营商网−100 终端）；4K AIGC ~80 Mbps，4K 3D ~160 Mbps，语音助手 ~6 Mbps；每家庭 2–5 个 Agent | 自报 | 〔0920-am-Su2-D-02-华为 p4, p1〕 |
| Huawei | 10 Gbps 商用统计：10+ 个 10Gbps City，600+ 个 1Gbps&beyond 套餐（Lounea 40 Gbps 套餐），100+ 个 10Gbps 试点（Turkcell 三模对称 50G PON 验证） | 自报 | 〔0920-am-Su2-D-02-华为 p6〕 |
| WBBA/Omdia | 流量至 2035：常规 4% CAGR、AI 增强 26% CAGR、全新 AI 流量 85% CAGR；343 家运营商调查（2026-03）障碍：数据质量与治理 39%、AI 人才 39%、网络安全 32% | 预测/调查 | 〔0923-We-F-00-标准化专场II连拍 p6, p8〕 |
| Nokia | 家庭固定流量（不含 FWA）至 2034：保守 1,405、中等 1,806、激进 2,791 EB/月；结论"渐进而非爆发" | 自报预测 | 〔0920-am-Su1-D-05-Nokia p26〕 |

### 1.2 架构演进

- **PON 世代与共存：** 中国移动 50G PON 兼容 ODN Class C+ 32 dB（图标 -25.7 dBm 与 +6.8 dBm），三代 PON 同端口 WDM 共存，ONU 双模 Combo〔0920-am-Su1-D-03-中国移动 p8〕。Huawei 展台：对称 50G PON（50G/XGS/G Combo，每线卡 8/16 口，PMD C+ 32 dB，三重共存）〔0920-am-Su2-D-02-华为 p13〕。Orange 的 MPM OLT（G-&XGS-PON）到三重 MPM（XGS-&HS-PON、&VHS-PON）为"纯推测"路线〔0920-pm-Su4-F-01-Orange p10〕。现存规模：GPON>10 亿用户、XGS-PON 接近 1 亿〔0920-am-Su1-D-05-Nokia p11〕；2026 年 PON 占全球 16 亿固定宽带用户约 73%〔0920-am-Su1-I-04-Nokia p7〕。
- **楼内/户内：** Nokia 区分企业 Optical LAN（PON 2.5G–100G+，高扇出）与住宅 G.p2pf（2.5G–50G，低扇出）；G.9930 于 2025-10 新增 25G/50G〔0920-am-Su1-D-05-Nokia p19〕。ITU-T Q3/15 两条路：mP2P（G.9930）与 P2MP（G.fin 2.5G 对称、G.Xfin 10G，PHY 已 consent，2027 年出首份草案）〔0920-am-Su1-D-04-MaxLinear p8, p12〕。G.9930 速率两页口径不一致（1/10/25/50 Gbps 与"最高 10 Gbps"）〔0920-am-Su1-D-04-MaxLinear p7, p13〕。
- **AI-FAN/ION-2030：** ITU-T ION-2030 三层（接入 far-edge AI、城域 near-edge AI、骨干/DC 内 cloud AI）与交付物 G.Sup.ION-aiBB、G.Sup.ION-aiHome〔0920-am-Su1-C-00-全场-上半场速记（ITU-T）p8, p9〕；ETSI F5G 时间线 2026 Release 4、2027 Release 5，在研 WI-25 F5G-A PON 网络算力协同架构（预计 2026 年 11 月发布）〔0923-We-F-00-标准化专场II连拍（ETSI）p34, p44〕。
- **运营商边缘 AI：** Telefonica 的 Telco Edge：客户边缘 DC 经 PON 或 P2P/P2MP 连到 Edge-AI OLT/Optical PE（示意，无定量）〔0920-am-Su1-I-01+02-主席+Telefonica p8〕。
- **6G 前传与融合：** X-haul 分割需求 Split 7.2：38–142.8 Gbps/RU、<20 km、200 µs；Split 8：200–850 Gbps/RU、<20 km、200 µs（TU/e 引用）〔0920-am-Su1-I-06-TUe p2〕。TCD 仿真（11 核心节点，有线 1.6 Tbps、无线 1 Tbps，无线渗透率 α=0.5）：核心节点故障影响接入节点比例纯有线约 22%、纯无线约 4–5%、Hybrid 约 9%（柱状图读数，近似）〔0920-pm-Su3-H-04-Trinity p11, p13〕。

---

## 2. 技术路线与关键指标

### 2.1 VHSP 下行：直检 + OLT 侧色散处理（DCPC / SSB / VSB / ODB / Dual-SSB）

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Huawei（Talli 等） | 120G NRZ 下 DCPC / SSB 用 2EAM、EAM-PM、DD-MZM、IQ-MZM 比较 | OMA 罚值（相对 b2b IQ-MZM）：DCPC 2EAM-π/2 约 4 dB，EAM-PM 1–2 dB；SSB（至 120 ps/nm）2EAM 4–6 dB，EAM-PM 1.5 dB，DD-MZM 1 dB（含 3 dB 固有损耗）；最小固有插损 DCPC-IQ-MZM 15 dB、DCPC-EAM-PM 3 dB | 仿真（EAM ER 设 7 dB，IQ 30 dB） | 〔0920-pm-Su4-F-05-华为 p5, p6, p8〕 |
| Huawei（Cano） | ODB / DCPC / SSB / SSB+DCPC | 常规 IM-DD 3 dB 罚值累积 CD 约 22 ps/nm；ODB 约 44，DCPC 约 90，两组 DCPC（35+90）到 120 ps/nm；SSB 120 ps/nm 罚值<1.5 dB，3 dB 罚值下 320 ps/nm，可传 1515 nm/20 km；SSB+DCPC(150 ps/nm) 相对 SSB 多约 1.5 dB（PAPR） | 仿真 | 〔0921-C2.2厅PON连拍 p87, p94, p98, p101〕；〔0921-Mo5-G连拍 p82, p84, p85〕 |
| Politecnico di Torino（+Huawei 合同） | DCPC PAM-4/PAM-2；MPI 与 DGD 容限 | 100G PAM-4 多用户：ODN 损耗>31 dB@20 km（BER 2×10⁻²），CD 容忍 ±40 ps/nm（C）/±53 ps/nm（O）；50 GBd PAM-2 MPI：SIR≥约 30 dB 罚值趋零；120 GBd 外推：显著罚值在 SIR<15 dB，DGD≤Ts/2（Ts=8.3 ps）罚值<1 dB | 实验（50 GBd）+仿真（120 GBd） | 〔0920-pm-Su4-F-03-PoliTo p8〕；〔0921-C2.2厅PON连拍 p43, p47, p49〕 |
| Nokia Bell Labs（Füllner） | DD-MZM + 延时 + 偏置点产生 VSB | 100 GBd NRZ，发射 7 dBm，0–125 ps/nm 罚值<3 dB（最高测到 137 ps/nm）；DSB 约 40 ps/nm；B2B 灵敏度约 -24 dBm（图读数）；FFE21/MLSE 比 FFE21/DFE3 好约 2–3 dB | 实验 | 〔0921-C2.2厅PON连拍 p12, p14, p19, p20〕；〔0921-Mo5-G连拍 p9, p11, p18〕 |
| Nokia Bell Labs（Adib，PDP-C-5） | 单波长 Dual-SSB，双边带分别承载独立信息 | 224 Gb/s Dual-SSB 相对单 SSB 约 6 dB 功率代价；170 ps/nm@3.5 dB 罚值；静态 DCPC 170 ps/nm 后 CD 0–340 ps/nm、预算约 33 dB（无 CD 约 36 dB），可用 C 波段；"首个单波长 200 Gb/s 服务速率直检 PON"（自报） | 实验（AWG 224 GS/s） | 〔0924-PDP-C-5-NokiaBellLabs p11, p15, p16〕 |
| NTT | 50 Gbaud NRZ SSB；线性外推表 | +10 dBm、61 抽头 FFE：灵敏度优于 -18 dBm 时 CD 罚值<4 dB，累积 CD 至 680 ps/nm（40 km）；外推 100G：E 波段 30/85 km（2/3.5 dB 罚值）、C 波段 7/20 km；200G：E 15/42.5 km、C 3.5/10 km | 实验+线性外推 | 〔0920-pm-Su4-F-04-NTT p7, p8〕 |
| Zaragoza 大学 | 简化相干外差 + OSSB multiCAP，LO 复用上行 | 下行 200 Gb/s（PolMux 总速率）25 km，灵敏度 -25 dBm、发射 +7 dBm→32 dB 预算；上行 20 Gb/s HD-LDPC 灵敏度 -31.5 dBm→33/38 dB；下行接收 -20 dBm 以上出现误码平层 | 实验 | 〔0921-C2.2厅PON连拍 p66, p68, p69〕；〔0921-Mo5-G连拍 p63, p65〕 |
| Nokia（Houtsma） | 三档波长方案 Plan A/B/C | A：1290–1330 nm 全 IMDD、无 GPON 共存、成本最低；B：1330–1370 nm，DS 为 ODB/SSB/DCPC 类，可与 GPON 共存；C：C 波段相干；NRZ 100–120 Gb/s 色散容限将波段限于零色散附近 | 观点+图表 | 〔0920-pm-Su4-F-02-Nokia p8〕 |

**小结：** 波长规划三档对应的最坏累积 CD 需求约 50/120/350 ps/nm（WP-A/B/C）〔0924-PDP-C-5-NokiaBellLabs p3〕。SSB 与 DCPC 是互补而非互斥（单个复数 FIR 可同时实现，OCR）〔0921-C2.2厅PON连拍 p100〕。

### 2.2 VHSP 上行/接收机：IM-DD 极限、ER 罚值、ONU 架构、成本

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Nokia Bell Labs（Houtsma） | 120G NRZ 上行 ER 罚值；COH vs DD | 120G NRZ 带宽受限 COH：ER=8.5 dB、BER 2×10⁻² 灵敏度 -23.1 dBm；DD（EDFA-滤波-PIN）-28.7 dBm；ER=6 dB 时 COH -20.8 dBm，29 dB 预算需 ONU 平均发射≥+8.5 dBm | 实验+建模 | 〔0921-C2.2厅PON连拍 p29, p30, p31〕；〔0921-Mo5-G连拍 p26, p28〕 |
| Coherent | ONU Tx 用 IM 的相干 PON | 4 dB ER 的 EML 相对 BPSK 约 +14 dB 灵敏度代价；CPON 预算 29–35 dB vs ZR 22 dB、CL 7–14 dB；booster SOA 相干 PON（Vijayan，OFC 2025）400G 预算 29 dB、200G 41 dB | 自报+引用 | 〔0920-pm-Su3-F-05-Coherent p6, p7, p8〕 |
| MaxLinear | DSP 计算量对比（目标 200G 净速率） | IMDD NRZ 200G：2 波长 ×120 Gbaud，21 抽头 FFE 约 5×10¹² MAC/s（略有不确定）；全相干 DP-QPSK 60 GBaud：2×2 MIMO 42 抽头约 80×10¹² MAC/s；简化相干 120 GBaud QPSK 62 抽头 60×10¹² MAC/s；全相干仿真灵敏度约 -33 dBm（32 dB C+ 预算） | 仿真 | 〔0920-pm-Su3-F-07-MaxLinear p4, p9, p10, p12〕 |
| Altice Labs | 6 种 ONU 架构（IMDD、全相干、intradyne+IMDD Tx 等）雷达图 | 方案3（相干 Rx + IMDD Tx）评为"高灵敏下行+低成本 ONU Tx"；方案5 把复杂度移到高速 ADC 与 DSP；雷达图为定性打分（方案3 各轴约 4–6，方案5 ADC 带宽项最高） | 定性评估 | 〔0920-pm-Su3-F-03-AlticeLabs p7, p8〕 |
| Adtran | 200G PON 成本构成（IM-DD vs 相干） | 直接材料 82%/113%，合计 100%/146%（占 IM-DD 总成本%）；激光/LO 15%/27%，ADC/DAC+DSP 11%/27%；100G ZR 与 50G PON 收发机 ASP 差距>10×（2030，LightCounting/Omdia，来源 Nokia ONDM'26）；2032 年条件：≥3.2 Tbps 相干接口、≥480 GBaud、≤2 nm CMOS | 自算 COGS（非实测） | 〔0920-pm-Su4-F-06-Adtran p7, p6, p8〕 |
| Nokia Bell Labs+PCRL | 首个可突发自适应光信号处理器（AOP）用于上行接收 | 4 抽头光 FIR，τ=10 ps；50 Gbaud，1340 nm，19 vs 81 ps/nm 两种突发；灵敏度差距 3 dB→约 1.5 dB；AOP 单独优于数字 FFE；约 300 mW（约 6 pJ/bit） | 实验 | 〔0923-We2-I-00-全场连拍（第6讲）p79, p80, p82, p84〕 |

### 2.3 相干 PON：上行突发、动态范围、预算与实时化

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Nokia Bell Labs（Vijayan） | 单载波 super-rated 混合相干上行；ONU 侧 SOA 兼任 Booster/门控/功率预均衡；OLT 通用全相干接收 | 120G SP-BPSK OPB 44.5 dB；480G DP-QAM4 41.1 dB；480G SP-QAM16 28 dB；960G DP-QAM16 26.4 dB（BER 2×10⁻²，20 km，130 GBd 接收，偏振手动对准）；SOA 电流调节使 ONU 间预均衡覆盖≈20 dB；门控抑制>60 dB | 实验 | 〔0924-Th2-D1-NokiaBellLabs p12, p14, p15, p16〕 |
| Huawei | 静态增益 TIA + 削波 + Soft-LDPC（17280,14592）；两种 post-FEC BER 估计 | 256 Gbps DP-QPSK；pre-FEC 阈值 2.45×10⁻²；post-FEC 无错动态范围 24 dB（标准 G.9804.3 要求 20 dB）；NCGR 灵敏度端 1.7 dB/过载端 1.8 dB | 实验（离线 DSP） | 〔0924-Th2-D2-华为 p4, p13, p14〕 |
| 复旦大学 | 单抽头 SOP 辅助 MMSE 信道估计，降并行度 | 25.07 GBaud DP-QPSK 100G，20 km，XCVU13P；43 并行 vs 128 并行灵敏度 -0.6 dB、动态范围 22→21 dB；LUT -49.6%、FF -58.4%、DSP -35.8%、BRAM -64.9%；43 并行+10 dBm SOA 最大预算 45.7 dB | 实验（实时 FPGA） | 〔0924-Th2-D3-复旦大学 p13, p14, p15, p16〕 |
| CICT+烽火 | 无收敛 DSP（前馈定时+偏振，存储每 ONU 信道状态） | 25 GBaud DP-QPSK，8800 符号/突发、16 ns 训练头；单 ONU -30 dBm（无 EDFA）、OLT EDFA 后 -36 dBm，预算>30 dB；±100 ppm 时钟偏差下 BER 变化可忽略；传输 15→40 km；FPGA LUT 59.4%、DSP 51.8% | 实验（实时 FPGA） | 〔0923-We2-I-00-全场连拍（第1讲）p5–p10〕 |
| 上海交大+中国电信 | 相干 TDM-PON 现场试验 | 上海现网 57 km 往返、OTDR 约 34 dB；50 GBd：200G QPSK 预算 42 dB、240G PS-16QAM 41 dB、300G 39 dB；30 GBd：120G 45 dB；前导优化到 30 ns；对比表：复旦 30 km/200.5 Gb/s/33 dB 实时，本工作离线 | 现场（现网光纤）+离线 DSP | 〔0924-Th2-D4-上海交大与中国电信 p8, p15–p17, p19〕 |
| CableLabs | DC 泄漏缓解（100/200G 相干 PON 上行） | 常规相干 DSP 仅容忍约 -47.1 dBm；配置1（陷波）-31.1；配置2（IF Tx）-15.1（DP-QPSK）/-17.6（DP-16QAM）；配置3（IF+外差+边缘滤波）约 -5.1 dBm；ODN 差分路径损耗最高 15 dB | 实验（离线） | 〔0923-We1-H-00-全场连拍-PON的DSP与均衡（第47–67页）p63–p65, p50〕 |
| Fraunhofer HHI（PONGO） | 单频带双向 FDMA，瑞利背向散射 | ONU1/2 30 GBd DP-QPSK；无下行功率时所需 ROP：ONU1>-33.25 dBm、ONU2>-34.65 dBm；下行最大容限 -4.9/-2.65 dBm；23 dB 分光（Nu=128）、35 dB 最大 OPL 可划出可运行区 | 实验+仿真（VPI；结论页已核实，p9–p16 部分数值为 OCR） | 〔0924-Th2-D5-FraunhoferHHI p9, p10, p16, p17〕 |
| Coherent | 相干可插拔生态与 VHSP 缺口 | ZR FEC 限 4e-3–2e-2，CPON 1e-2/2e-2；需固定但频率受控 DFB、突发 booster SOA；100G ZR QSFP28 Steelerton DSP<2 W | 自报 | 〔0920-pm-Su3-F-05-Coherent p7, p9, p4〕 |

### 2.4 50G PON / Beyond 50G：均衡、FEC、长距放大、节能

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| IMT Atlantique | 50G-PON 下行均衡+LDPC(17280,14592) 交互 | 1342 nm、25 km、76 ps/nm：post-FEC 预算 DFE+SI-LDPC 41.1 dB、FFE+SI 40.7、MLSE+HI 40.5、无均衡 38.5/39.3；仅用 pre-FEC BER 估计预算不计均衡与译码器影响 | 实验 | 〔0923-We1-H-00-全场连拍-PON的DSP与均衡（第1–13页）p11, p12〕 |
| Orange+Laval+IMT | 50G-PON RS(248,216) + 均衡 | pre-FEC 灵敏度：无均衡 -22.7、aFFE -24.6、DFE -25.8、MLSE -26.4 dBm；post-RS：DFE -24 dBm/37.3 dB、MLSE -24.8/38.1 dB，满足 D/E2 余量 2.3/3.1 dB；模拟均衡下 RS 相对 HI-LDPC 代价 4 dB 仍满足 E1（33.9 dB） | 实验 | 〔0923-We1-H-00-全场连拍-PON的DSP与均衡（第31–46页）p42, p44, p45〕 |
| NTT | 远程泵浦 BiDi-EDFA + 分布式拉曼，50 Gbaud SSB+DCPC，目标 60 km、1:512 | 接入段可承受损耗：DS 40/50/60 km 为 32.3/34.0/33.1 dB（DS-A），US 29.4/29.4/30.1 dB；上行 40 km 拉曼约 10 dB、EDFA 合计 18 dB；目标总预算 39 dB；前作 120 GBd IM/DD 35 dB/20 km | 实验 | 〔0923-We1-H-00-全场连拍-PON的DSP与均衡（第85–102页）p88, p90, p98, p101〕 |

### 2.5 FTTR 与 Wi-Fi 协同

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| 中国移动 | 10G FTTR 物理层 Ra/Ra+ | 预算 0–18/0–21 dB；MFU 发射 1–5 dBm、灵敏度 -19.5/-22.5 dBm；Ra+ 直连与最高 1:32；三频 Wi-Fi 7：MLO 5.2G+5.8G 理论 4323 Mbps；RFID over FTTR 试验：>1000 m²、>2000 标签、盘点由 1 天到分钟级 | 自报+试验 | 〔0920-am-Su1-D-03-中国移动 p9, p17〕 |
| Fraunhofer HHI | MAC-PHY 切分：A 联合用户管理/B 联合调度/C 联合预编码 | 2.4 GHz、40 MHz、QuaDRiGa：独栋 41→72 Mbps（C，+75%）、1%-worst 时延 9→3 ms；多户 10 BSS 41→67 Mbps（+63%）；开放办公 A +73%、C 1%-worst 时延 20→3 ms（-85%） | 纯仿真 | 〔0920-am-Su2-D-03-FraunhoferHHI p12, p13, p14〕 |
| UPF | 集中式 MAPC + DRL（PPO）调度 | Co-SR、4 AP，99th 百分位时延：MNP 244.50 ms→ML-E 72.98 ms；均值 29.79→19.95 ms；开放挑战：MFU→SFU 命令受 DBA 时延、封装、队列竞争影响 | 仿真 | 〔0920-am-Su2-D-04-UPF p10, p7〕 |
| DeepSig | AI-Native Wi-Fi 9 PHY | 5G 现网神经接收机某些情况上行吞吐 2–3 倍（Intel FlexRAN DU）；学到星座 1024-QAM（Rayleigh）/4096-QAM（CDL-A）；Wi-Fi 侧仅称"潜力为两位数吞吐提升"，无量化基线 | 自报 | 〔0920-am-Su2-D-01-DeepSig p5, p6, p11〕 |

### 2.6 AI-FAN、确定性接入与监测/运维

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Nokia Bell Labs | Deterministic BW Mapper（上行 PON，125 μs 帧） | 三条 TSN 流示例（周期 250/500/250 μs）；计算量随流数近线性（穷举 10¹→约 10¹⁴，柱高目测）；抖动标注<1 μs 与<10 μs（图小字） | 实验/演示 | 〔0922-Tu1-F2-NokiaBellLabs p3, p5〕；〔0920-pm-Su3-H-02-Nokia p8〕 |
| IMT Atlantique | 被动恢复 BWMap 预测 GPON 拥塞 | GPON 1490/1310 nm，125 μs 帧；高负载 Tx Grant≈实际流量，低负载 Grant>实际；SARIMA 4 天训练预测第 5 天；无需 OLT 访问与 DPI | 实验 | 〔0922-Tu1-F4-IMTAtlantique p7, p8, p11〕 |
| NTT | 光辅助 RAN 控制（OAN-C 30 ms 周期采集直报 Near-RT RIC） | 中断 1.63→0.54 s（-66.9%，10 次最短值）；故障到 HO 指令 1.5→0.11 s+0.007 s（-92.3%）；HO 本身约 0.5 s 不变 | 实验（OAI+FlexRIC） | 〔[主分析师笔记] 10 NTT Tu1-F5〕 |
| 中国移动 | AI-Native 50G PON+FTTR 与算力总线 | OLT 边缘算力，端到端 RTT<20 ms（OMCI 扩展，专用 Wi-Fi 7 5.8 GHz）；具身 AI 端侧算力"5–6 T"（文字模糊） | 自报 | 〔0920-am-Su1-D-03-中国移动 p16〕 |

### 2.7 RoF、6G 前传与 sub-THz/光子辅助无线

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Aston+Ericsson | DPD-KAN，A-RoF 数字预失真 | 5G NR TM3.1 100 MHz 64QAM，VCSEL DML，1 km SSMF：5 dBm 输入无 DPD EVM 约 7.5%；KAN(BOP≈10⁴) 约 2.9%、MLP 约 3.9%；达 EVM≤2% 所需 BOP KAN 1.32×10⁴ vs MLP 2.75×10⁴（-52%）；MOPA：>97% 前传 RoF 链路<1 km | 实验（读图近似） | 〔0921-Mo5-F全场连拍 p71, p72, p73, p68〕 |
| TU/e | 400G ZR+ 相干前传 + 快速光子交换，RU-DU 动态重构 | 端到端重配约 206 μs；4 级联节点功率代价 3.8 dB（1 节点 0.7 dB，pre-FEC 10⁻²），OSNR 降至 31.2 dB | 实验 | 〔0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A p34, p35〕 |
| TU/e | 光子集成 OADM/WDM 交叉连接 | 32×32×8λ 混合 PLC/III-V，O 波段 100 Gbps/λ，KP4 门限 2e-4；混合 WSC 光纤到光纤增益最高 12 dB、KP4 处代价<0.65 dB | 实验 | 〔0920-am-Su1-I-06-TUe p16, p17, p18〕 |
| KIT | 实时相干光子辅助 sub-THz，10 km SSMF+1.4 m 无线，FPGA | 2.048 GBaud，稳定支持±100 ppm；QPSK 净 3.99 Gbit/s（BER<1e-7），16-QAM 净 6.83 Gbit/s（BER<2×10⁻²）；中断后 CMA 收敛约 1 μs | 实验（实时） | 〔0924-Th2-H2-KIT p4, p6, p7〕 |
| 东南大学+紫金山 | 光子辅助 306 GHz，PR-9QAM/FTN，FPGA 实时 | 15 GBaud，3 m，30 GSa/s 8 bit ADC；30 Gb/s QPSK error-free（原文）；AMBM 相对 CORDIC：LUT 411→58、DSP48E2 2→0、延迟 22→2 周期 | 实验（实时） | 〔0924-Th2-H4-东南大学与紫金山实验室 p7, p8, p5, p10〕 |
| 复旦大学 | FPGA 均衡引导 SFO 补偿，D 波段 30.2 km | 128 GHz，16 Gbaud QPSK，32 Gb/s，距离×速率 966.4 Gb/s·km；无补偿 BER 在约 2×10⁵ 符号升至约 2×10⁻²，补偿后约 5×10⁻³ | 外场（复旦—新河镇） | 〔0924-Th2-H5-复旦大学 p12, p14, p15〕 |

### 2.8 FSO 与星地光链路

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Aircision（+TU/e） | 地面 FSO 商用化，网络层解决雾/湍流 | 4.6 km@7.7 Tbps（Eindhoven，2025-04，标"World Record"）；同页标题写"5.7 Tbps"，两数不一致，未判断哪个为准；另 6.1 km@10 Gbps 全双工、1.8 km@4 Tbps；部署<6 小时；ITU-T G.641（11/2025） | 自报+现场 | 〔0920-pm-Su3-D-04-Aircision-自由空间光技术方 p3, p5〕 |
| Cambridge（引用他人） | FSO 演示对比 | Eindhoven 4.6 km 5.7 Tb/s（van Vliet，OFC 2025，相干 WDM 22 通道）；青海湖 104.8 km 112 Gb/s；NICT 东京 7.4 km 2 Tb/s；混合 THz/FSO 一个月实测：FSO 天气事件下跌至约 15 Gbps，并行混合约 150–230 Gbps | 引用+实测（近似） | 〔0920-pm-Su4-H-02-Cambridge p4, p13〕 |
| CNES/Airbus/Safran/OGS（LASIN/FrOGS） | LEO 直连下行，AO+SMF 注入 | CO3D 4 颗 LEO，符号率 10 Gsps；SMF 典型注入效率 40%、ROP -35 至 -25 dBm；2026-08-05 传输 1.38 Tb（r0=20 cm），09-17 传输 1.62 Tb error-free（r0>25 cm）；重捕获<15 s | 在轨实测 | 〔0920-am-Su2-F-04-OGS-低轨相干链路自适应光学 p5, p7〕 |
| Safran | AO + 发射分集 + 交织 | 仿真：50 cm 望远镜、20°–86°、r0 4.1 cm、65 m/s，AO 算法链路余量增益 4 dB；实测 30° 以上余量充足、9 Gbps 载荷；带内信令使会话起始即得 125 Mbps；差湍流（r0 约 5 cm、风速 9 m/s，2026-07-07 实测）下 20° 仰角 3.5 s 载入 4 GB | 仿真+在轨 | 〔0920-am-Su2-F-05-SAFRAN-自适应光学加发射分集 p3, p8, p9〕 |
| BUPT+中科院 | 模式分集接收（6 模光子灯笼）+ AO，GEO 星地 | 仿真强湍流接收功率提升>10 dB，实验室>6 dB；GEO 在轨（2 W/1550 nm，1.048 Gbps BPSK，1.8 m 望远镜）：99% CCDF 功率 1 模 -63.4→3 模 -51.3 dBm（+12.1 dB）；无错帧比例仅 AO 77.6% vs 3 模合并 99.0%；99% CCDF 改善数据日期 2025-12-11 | 在轨试验（2024-05–2026-01） | 〔0924-Th2-C1-北邮与中科院-模式分集接收与自适应光学增强的星地自由空间光链路 p13–p18〕 |
| KDDI Research | PCSEL 瓦级 FSO 发射机 | PCSEL 发散角<0.2°×0.2°、>1 W（EEL 约 5°×30°/100 mW）；FM+相干外差：0.5/1 Gbaud 链路预算 83/78 dB（20% OH SD-FEC，无光纤放大器）；直调直检此前 35 dB | 实验 | 〔0922-Tu1-C5-KDDIResearch-光子晶体面发射激光器做自由空间光通信 p12, p29, p34〕 |
| 西湖大学 | 室内 DP-CEDD 光无线（自相干，SiP CROW 提取载波） | 9 m LOS，448 Gb/s（PDM-16QAM OFDM），20% SD-FEC 后净 355.1 Gb/s，灵敏度 -25 dBm，净 SE 11.84 bit/s/Hz；CROW 20-dB 带宽 4.48 GHz、消光 60 dB；仅静态对准条件下免光学 APC | 实验 | 〔0922-Tu1-C4-西湖大学-双偏振载波提取直检的448Gbps室内光无线接入 p14, p11〕 |

---

## 3. 厂商与客户态势

### 3.1 AIDC/云客户与运营商

- **Verizon：** 主张 VHSP 面向 AI、DCI、宽带；"每种技术都认为自己最好"；选型 2027、最终选择 2028、商用 2035+〔0920-pm-Su3-F-02-Verizon p11〕。
- **Orange：** 约 2040 VHS-PON 且无 G-PON 共存的前提下，1310 nm（和 1490 nm）频谱空出是否利好 IMDD 为其提问；Class C+ 必需、可能 Class D；把光纤传感视为"第二阶段商业价值"〔0920-pm-Su4-F-01-Orange p10, p11, p14〕。在节能上主推分光比 1:128、G+XGS Combo 卡、ONU 睡眠模式，并要求 ODM 厂商实现〔0920-am-Su1-I-03-Orange p11, p15〕。
- **中国移动：** 50G PON 对称系统已基本达 Class C+，主张 10G FTTR 与 FTTR 协同管理标准化，联合发起 ITU-T G.sup.PONcoop；提出"PON+FTTR 算力总线"〔0920-am-Su1-D-03-中国移动 p8, p9, p16〕。

### 3.2 设备商

- **Huawei：** 展台 1231 对称 50G PON（三重共存、C+ 32 dB）、FTTR 2.5G TDMA-DTA；VHSP 方面以 OLT 侧 IQ-MZM+DD ONU 的 DCPC/SSB 为主线，同时做相干 PON 动态范围（Soft-LDPC，24 dB）〔0920-am-Su2-D-02-华为 p13〕；〔0921-C2.2厅PON连拍 p74〕；〔0924-Th2-D2-华为 p13〕。
- **Nokia（Bell Labs + Fixed Networks）：** 在 VHSP 三条线都布局：VSB/Dual-SSB（直检）、SOA 门控相干上行（960G）、AOP 光域均衡；主张 Plan A/B/C 分档；Optical LAN 与 mmWave Wi-Fi；确定性 PON 调度〔0920-pm-Su4-F-02-Nokia p8〕；〔0924-Th2-D1-NokiaBellLabs p17〕；〔0922-Tu1-F2-NokiaBellLabs p4〕。
- **Adtran：** 唯一明确站在"相干不贵"一侧的设备商：相干 200G PON 成本 146% 于 IM-DD，价差归因于量级（PON 与 ZR 单元数差 10–20 倍）〔0920-pm-Su4-F-06-Adtran p6, p7〕。

### 3.3 模块/器件商

- **Coherent：** 认为 VHSP 相干混合可复用相干可插拔生态；提出激光器/突发 TIA/SOA 缺口清单；100G ZR QSFP28（DSP<2 W，"industry's first and only"自报）；LS200 地面站系统〔0920-pm-Su3-F-05-Coherent p4, p9〕；〔0923-MF-00-上午连拍 p19〕。
- **Sumitomo Electric Device Innovations：** 借 EML/CW DFB/可调激光器，提示电信特有代价（温度、突发、预算）；EML CAGR=48%、CW CAGR=110%（坐标读图，未核对）〔0920-pm-Su3-F-04-住友电工 p5, p6〕。
- **MaxLinear：** 同时是 ITU-T Q3/15 FTTR 标准（G.Xfin）与 VHSP DSP 复杂度评估者〔0920-am-Su1-D-04-MaxLinear p12〕；〔0920-pm-Su3-F-07-MaxLinear p10〕。
- **Aircision：** FSO 整机，双向 1–5 km，部署<6 小时〔0920-pm-Su3-D-04-Aircision-自由空间光技术方 p3〕。

### 3.4 芯片商

- **MaxLinear：** 主张全相干 DSP 优于简化相干（后者导致极高波特率接收机）；相干下行+IMDD 上行的混合避开突发相干问题但仍需 ONU 侧 LO〔0920-pm-Su3-F-07-MaxLinear p13〕。
- **DeepSig：** AI-Native PHY，呼吁 802.11 标准提供 CSI/IQ 上传、码本模型下发等钩子〔0920-am-Su2-D-01-DeepSig p11〕。

---

## 4. 学术关键突破（按影响力排序）

| # | 机构 | 论文号/文件名 | 突破点 | 数字 | 索引 |
|---|---|---|---|---|---|
| 1 | 上海交大+中国电信 | Th2-D4「First Field Trial of Coherent TDM-PON Up to 300 Gb/s」（标"首次"） | 现网光纤首次相干 TDM-PON 现场试验 | 57 km 往返、约 34 dB 损耗；200G 42 dB、300G 39 dB；前导 30 ns；DSP 离线 | 〔0924-Th2-D4-上海交大与中国电信 p16, p19, p20〕 |
| 2 | Nokia Bell Labs | Th2-D1「960/480/240/120 Gbit/s Single-Carrier Super-Rated Hybrid Coherent Upstream Burst-Mode PON」（首次） | ONU 侧 SOA 三合一，OLT 单一全相干接收机覆盖异构 ONU | 480G>40 dB OPB（41.1 dB）；首次 960G 且>26 dB（26.4 dB） | 〔0924-Th2-D1-NokiaBellLabs p14, p15, p17〕 |
| 3 | Nokia Bell Labs | PDP-C-5「Dual single-sideband… 340 ps/nm CD tolerance, single-wavelength 200G direct-detection PON downstream」（PDP，首个单波长 200G 服务速率直检 PON） | 单波长 Dual-SSB 把 200G 直检的双波长复杂度降下来 | 224G Dual-SSB 170 ps/nm@3.5 dB；DCPC 后 0–340 ps/nm，预算约 33 dB | 〔0924-PDP-C-5-NokiaBellLabs p13–p16〕 |
| 4 | 复旦大学 | Th2-D3「Low-Complexity FPGA… 100G Real-Time Upstream Burst-Mode Coherent PON」 | 实时 FPGA 相干突发，降并行度 | 预算 45.7 dB；43 并行 -0.6 dB 灵敏度、LUT -49.6% | 〔0924-Th2-D3-复旦大学 p14, p15, p16〕 |
| 5 | CICT+烽火 | We2-I 第1讲「Convergence-Free DSP」 | 前馈突发 DSP 消除迭代收敛，FPGA 实时 | -30/-36 dBm，预算>30 dB，15→40 km | 〔0923-We2-I-00-全场连拍（第1讲）p7, p9〕 |
| 6 | Nokia Bell Labs+PCRL | We2-I 第6讲「First-Ever Burst-Capable Adaptive Optical Signal Processor」（首次） | 单片 InP 4 抽头光 FIR，ns 级逐突发重构 | 灵敏度差 3 dB→约 1.5 dB；约 300 mW（6 pJ/bit@50G） | 〔0923-We2-I-00-全场连拍（第6讲）p82, p84〕 |
| 7 | KDDI Research | Tu1-C5 PCSEL FSO（世界首个瓦级 PCSEL FSO 演示，2023；本次为综述+自家成果） | PCSEL 作高功率 FM 发射机+相干检测，无光纤放大器 | 0.5/1 Gbaud 链路预算 83/78 dB | 〔0922-Tu1-C5-KDDIResearch p21, p34〕 |
| 8 | 北邮+中科院 | Th2-C1「Satellite to Ground FSO… Mode Diversity Reception and AO」 | GEO 在轨验证 MDR+AO；提出联合补偿方案 | 99% CCDF +12.1 dB；无错帧 77.6%→99.0%；1.048 Gbps | 〔0924-Th2-C1-北邮与中科院 p16, p18〕 |
| 9 | TU/e（Aircision 关联） | Aircision 报告；van Vliet OFC 2025 | 4.6 km FSO 多 Tb/s（World Record，5.7 vs 7.7 Tbps 不一致） | 7.7 Tbps（Aircision 页）/5.7 Tb/s（Cambridge 引用） | 〔0920-pm-Su3-D-04-Aircision p3〕；〔0920-pm-Su4-H-02-Cambridge p4〕 |
| 10 | 西湖大学 | Tu1-C4 DP-CEDD | 自相干直检消除本振，SiP 滤波器提取载波 | 9 m/448 Gb/s；-25 dBm；净 SE 11.84 bit/s/Hz | 〔0922-Tu1-C4-西湖大学 p14, p11〕 |
| 11 | Aston+Ericsson | Mo3 DPD-KAN | KAN 做 A-RoF DPD，低复杂度优于 MLP/GMP | BOP 减少 52%；EVM -24%/-30%（10⁴ BOP） | 〔0921-Mo5-F全场连拍 p73〕 |

---

## 5. 分歧、争议与反常识

**5.1 直检 vs 相干：哪种在"百万用户每美元"上赢？**
- 直检一方：Nokia Houtsma 称 120G NRZ 带宽受限下 OA-DD 灵敏度 -28.7 dBm 优于相干 -23.1 dBm（ER=8.5 dB，BER 2×10⁻²），原因是 ER 惩罚小、系统带宽受限、集成相干接收机附加损耗〔0921-C2.2厅PON连拍 p29, p30〕；Coherent 也承认 4 dB ER 的 EML 相对 BPSK 约 +14 dB 灵敏度代价（对混合方案不利）〔0920-pm-Su3-F-05-Coherent p6〕。
- 相干一方：Adtran 自算 200G 相干 COGS 为 IM-DD 的 146%，价差主因量级；2032 年具备≥3.2 Tbps 相干接口、≤2 nm CMOS 后"不再是问题"〔0920-pm-Su4-F-06-Adtran p7, p8〕。反证：同一份讲稿引 LightCounting/Omdia 认为 100G ZR 与 50G PON 收发机 ASP 差距 2030 年仍>10×〔0920-pm-Su4-F-06-Adtran p6〕；MaxLinear 算全相干均衡 80×10¹² MAC/s（p9，OCR）对 IMDD 5×10¹² MAC/s（2×120 GBd NRZ、21 抽头 FFE + BCJR）〔0920-pm-Su3-F-07-MaxLinear p4, p9〕。
- 结论性状态：双方都是仿真/自算/实验，无同一基准的实测成本对比。

**5.2 混合方案：是"两全其美"还是"杂交不育"？**
- 支持：Altice 认为方案3"比全相干更适合 PON"；Nokia Bell Labs 用单一相干 OLT 覆盖 120–960G 异构 ONU〔0920-pm-Su3-F-03-AlticeLabs p7〕；〔0924-Th2-D1-NokiaBellLabs p17〕；SJTU 共享 OLT 混合 DD+相干，DD ONU 付出 7 dB 代价〔0923-We1-H-00-全场连拍-PON的DSP与均衡（第68–84页）p81〕。
- 质疑：KIT 以词源调侃"后代通常不育"，并列出 IMDD 与全相干各自缺陷后强调混合的核心问题〔0920-pm-Su3-F-06-KIT〕（核心主张 2）；MaxLinear：OLT 相干接收+ONU 仅 IMDD 需要比全相干更高的波特率〔0920-pm-Su3-F-07-MaxLinear p13〕；Altice 强调"额外性能是否值得额外成本、功耗与运维复杂度"〔0920-pm-Su3-F-03-AlticeLabs〕（核心主张 1）。

**5.3 相干 PON 上行动态范围：硬件均衡还是软判决 FEC？**
- 硬件路线：Nokia 在 ONU 侧 SOA 预均衡，覆盖≈20 dB；Koma（Rx-SOA）与突发 TIA 均被 Huawei 归为"增加硬件和系统复杂度"〔0924-Th2-D1-NokiaBellLabs p16〕；〔0924-Th2-D2-华为 p3〕。
- 软件路线：Huawei 静态增益 TIA+削波+Soft-LDPC 获 24 dB 无错动态范围，NCGR 仅 1.7/1.8 dB；Sarkis（OFC 2026）同样无功率均衡（29 dB，引用）〔0924-Th2-D2-华为 p13, p14, p3〕。
- 另一变量：CableLabs 指出 ONU 关断的 DC 泄漏才是隐藏瓶颈，常规 DSP 仅容忍约 -47.1 dBm，需 IF 上变频设计才到 -15 dBm 以上〔0923-We1-H-00-全场连拍-PON的DSP与均衡（第47–67页）p63, p64〕。

**5.4 流量增长：渐进还是 AI 驱动的爆发？**
- Nokia：家庭固定流量至 2034 年三档预测（1,405/1,806/2,791 EB/月），"渐进而非爆发"；AI GPU 周期 2–3 年 vs 电信光网络约 10 年〔0920-am-Su1-D-05-Nokia p26, p28〕。
- WBBA：全新 AI 流量 85% CAGR、AI 增强 26% CAGR，常规仅 4%（2025–35）〔0923-We-F-00-标准化专场II连拍 p6〕；中国移动称上行占比升至 40%–50%〔0920-am-Su1-D-03-中国移动 p5〕。
- 差异来源：Nokia 统计不含 FWA、口径为家庭固定流量；WBBA 口径为全网流量分类，二者不可直接比较。

**5.5 FTTR 无线侧：MAC-PHY 联合处理 vs 分布式协商 vs 毫米波**
- UPF：802.11bn 的 Co-SR/Co-TDMA/Co-BF 是分布式、仅成对协商、开销大，集中式 MAPC 用 DRL 可降 99 百分位时延（244.5→73.0 ms），但 FTTR 上 MFU→SFU 光 DBA 时延威胁微秒级时序〔0920-am-Su2-D-04-UPF p10, p7〕。
- HHI：Split C（联合预编码）吞吐 +75%，但为 2.4 GHz、纯仿真，且 Split A 与 B 在部分场景无增益甚至降吞吐（多户 B 38 vs 参考 41 Mbps）〔0920-am-Su2-D-03-FraunhoferHHI p12, p15〕。
- Nokia 与 Huawei 走不同路径：Nokia 60 GHz mmWave（每房间 80% 覆盖目标，墙衰减 20 dB 假设）；Huawei 复用基带的 802.11bq（新增 42–71 GHz）〔0920-am-Su1-D-05-Nokia p6〕；〔0920-am-Su2-D-02-华为 p8〕。DeepSig 则主张 AI-Native PHY 无量化 Wi-Fi 基线〔0920-am-Su2-D-01-DeepSig p11〕。

**5.6 星地链路：AO 是否够用？**
- BUPT：AO 复杂、成本高，强湍流下感知速度与控制带宽受限；实验室 D/r0=26 时 AO 增益仅 0.9 dB（无 MDR）；GEO 在轨仅 AO 无错帧 77.6%，AO+3 模 MDR 达 99.0%〔0924-Th2-C1-北邮与中科院 p7, p14, p18〕。
- CNES/OGS：LEO 下行 AO 性能"already excellent"，SMF 注入稳定；Safran 仿真 AO 新控制算法 +4 dB；上行需 MEO 中继预补偿等〔0920-am-Su2-F-04-OGS p8, p5〕；〔0920-am-Su2-F-05-SAFRAN p3〕。
- 条件差异：BUPT 是 GEO 下行（1.8 m 望远镜、1.048 Gbps），CNES 是 LEO 下行（10 Gsps）；不是同一场景的直接矛盾。

**5.7 VHSP 波长与共存的时间悖论**
- Nokia Plan A（1290–1330 nm 全 IMDD，无 GPON 共存，成本最低）与 Plan B（1330–1370 nm，需 CD 处理换共存）的取舍，取决于 GPON 何时退出；Orange 假设 2040 无 G-PON，Verizon 商用 2035+〔0920-pm-Su4-F-02-Nokia p8〕；〔0920-pm-Su4-F-01-Orange p10, p11〕；〔0920-pm-Su3-F-02-Verizon p11〕。

---

## 6. 判断与观察点

### 6.1 技术成熟度（TRL 式判断，基于笔记证据）

| 技术 | 判断 | 依据 |
|---|---|---|
| 50G PON（对称/Combo） | 商用前夜（多家展台演示，预算对标 C+ 32 dB） | 〔0920-am-Su2-D-02-华为 p13〕；〔0920-am-Su1-D-03-中国移动 p8〕 |
| 10G FTTR（Ra/Ra+） | 标准化推进（CCSA 共识 PHY），协同管理待标准 | 〔0920-am-Su1-D-03-中国移动 p9〕 |
| G.Xfin（P2MP 10G FTTR 标准） | PHY 已 consent，首份草案 2027 | 〔0920-am-Su1-D-04-MaxLinear p12〕 |
| VHSP 直检（SSB/DCPC/VSB/Dual-SSB） | 实验室概念验证，200G 单波长首次演示 | 〔0924-PDP-C-5-NokiaBellLabs p16〕 |
| VHSP 相干 PON | 实验室实时 100G+现场离线 300G；实时>200G 未见 | 〔0924-Th2-D3-复旦大学 p13〕；〔0924-Th2-D4-上海交大与中国电信 p19〕 |
| 混合 DD/相干 | 概念与实验并进，成本收益未闭合 | 5.2 |
| AI-FAN | 架构与标准立项（G.sup.ION-aiHome/aiBB、F5G WI-25），端到端 20 ms RTT 未见现网数字 | 〔0920-am-Su2-D-02-华为 p1〕；〔0923-We-F-00-标准化专场II连拍（ETSI）p44〕 |
| sub-THz 光子辅助无线 | 实时 DSP 演示，速率 4–32 Gb/s 量级 | 〔0924-Th2-H2-KIT p7〕；〔0924-Th2-H5-复旦大学 p14〕 |
| 地面 FSO | 商用化（部署<6 小时），多 Tb/s 为记录场景 | 〔0920-pm-Su3-D-04-Aircision p3〕 |
| LEO/GEO 星地光链路 | 在轨验证阶段（LASIN 完整序列待分析） | 〔0920-am-Su2-F-05-SAFRAN p9〕 |

### 6.2 时间窗口

- 2026–2027：50G PON 规模引入、10G FTTR PHY/协同管理标准化；G.Xfin 首份草案 2027；ITU-T G.sup.PONcoop 目标定稿 2028 年 7 月〔0920-am-Su1-I-04-Nokia p10〕。
- 2027–2028：VHSP 各类别选技术与最终选择〔0920-pm-Su3-F-02-Verizon p11〕。
- 2030+：VHS-PON 200G（FSAN 路线图）；2035+ 商用；Orange 运营约 2040〔0920-pm-Su3-F-02-Verizon p10, p11〕。
- 2032：Adtran 设想的相干集成条件成熟点（≥3.2 Tbps、≤2 nm CMOS）〔0920-pm-Su4-F-06-Adtran p8〕。

### 6.3 对厂商的含义

- **设备商：** 现网 OLT 需支持 Combo（G+XGS、XGS+50G）与三重 MPM；VHSP 要在 OLT 侧承担复杂度（DCPC/SSB/相干接收），ONU 保持低成本这一"不对称"设计是多数直检/混合方案的共同前提〔0920-pm-Su4-F-02-Nokia p8〕；〔0921-C2.2厅PON连拍 p74〕。
- **模块/器件商：** 关键器件缺口：固定但频率受控 DFB、突发 booster SOA、高线性 IQM/DD-MZM（EAM 消光比是 SSB 罚值主因）、>60 GHz EML；数据中心器件借用需处理温度、突发与预算三项电信特有代价〔0920-pm-Su3-F-05-Coherent p9〕；〔0920-pm-Su4-F-05-华为 p6〕；〔0920-pm-Su3-F-04-住友电工 p4, p6〕。
- **芯片商：** 突发相干 DSP 的可实现路径已在 FPGA 验证（43 并行、无收敛前馈）；全相干 vs 简化相干的算力差 80×10¹² vs 20–60×10¹² MAC/s 是 ASIC 选型主变量；ADC 240 GS/s 以上需求（简化相干 T/2 均衡）〔0920-pm-Su3-F-07-MaxLinear p12〕。
- **FTTR/Wi-Fi 芯片：** 802.11bn/bq 与 FTTR 需光 DBA 时延指标；集中式调度与 MAC-PHY 切分对 MFU–SFU 的时延、抖动提出微秒级要求〔0920-am-Su2-D-04-UPF p7〕。

### 6.4 未来 12–24 个月观察点

1. G.Sup88 之后 ITU-T Q2 的 VHSP 类别选择输入：是否出现直检 SSB/DCPC 与相干的"同基准"预算/复杂度对比（目前无）。
2. 相干 PON 实时化：从 100G 实时（复旦，45.7 dB）扩展到 200G 实时；现场试验从离线 DSP 转实时（对照 SJTU 对比表）〔0924-Th2-D4-上海交大与中国电信 p19〕。
3. 相干 ONU 成本数字：Adtran COGS 146% 与 ASP>10× 的两个口径能否被实测/报价数据收敛。
4. ONU 侧 SOA 突发功率均衡 vs Soft-LDPC 的 A/B 对比，以及 DC 泄漏容限（-47 dBm 到 -5 dBm 的方案选择）。
5. Combo/三重 MPM 光模块与 G.sup.PONcoop 进展（2028 年 7 月目标）；ONU 睡眠模式在主流网关的实现（Orange 需求）。
6. FTTR：G.Xfin PHY/DLL 进展、10G FTTR 协同管理标准、802.11bn/bq MAC 阶段；集中式 MAPC 上光回传时延的实测（UPF 的开放挑战）。
7. AI-FAN：ETSI WI-25（2026 年 11 月发布）与 ITU-T aiHome/aiBB 的具体指标；"接入 RTT≤20 ms"和"算力总线"是否出现现网数字。
8. 6G 前传：400G ZR+ 相干前传+快速光交换的重配时延（206 μs）向 Split 7.2/8 时延预算（200 μs）的对齐。
9. FSO/星地：LASIN 完整序列、100+ Gbps 相干 SMF 注入路线、MDR 与 AO 联合在 LEO 场景的验证；4.6 km 记录的数字统一（5.7 vs 7.7 Tbps）。
10. 安全：光侧信道攻击对 PON 下行 AES 的现实威胁模型（50 km 攻击需前放或 5×10⁴ 条轨迹）；QKD 不能解决数据层 AES 的侧信道〔0924-Th2-A3-TelecomSudParis与Orange p10, p12〕。

---

## 7. 推荐配图

| # | PDF文件名 pN | 图中是什么 | 支撑观点 |
|---|---|---|---|
| 1 | 0920-pm-Su3-F-02-Verizon p11 | VHSP 与 50G-PON、NG-PON2 时间线对比 | 核心判断1：选型窗口与商用时间 |
| 2 | 0920-pm-Su3-F-02-Verizon p7 | VHSP 技术候选树与符号率 | 核心判断1：路线多样 |
| 3 | 0920-pm-Su4-F-02-Nokia p8 | Plan A/B/C 波长与技术分类表 | 5.7：共存与成本取舍 |
| 4 | 0920-pm-Su4-F-05-华为 p8 | 调制器方案—罚值—固有插损总表 | 核心判断2：直检色散处理实现代价 |
| 5 | 0924-PDP-C-5-NokiaBellLabs p15 | 不同补偿方案下损耗预算 vs CD | 核心判断2：单波长 200G 直检 |
| 6 | 0921-Mo5-G连拍 p11 | 数字延时—灵敏度曲线（VSB 效果） | 核心判断2：低复杂度 VSB |
| 7 | 0921-C2.2厅PON连拍 p31 | 实测灵敏度 vs ER，COH 与 DD 接收机 | 5.1：直检 vs 相干 |
| 8 | 0920-pm-Su4-F-06-Adtran p7 | IM-DD vs 相干 200G PON ONU 成本构成表 | 5.1：成本争议 |
| 9 | 0924-Th2-D1-NokiaBellLabs p17 | 结论与容量-OPB 对比图（960G/26.4 dB、480G/41 dB） | 核心判断3：相干上行预算 |
| 10 | 0924-Th2-D1-NokiaBellLabs p8 | 异构 ONU 四类+SOA 三重角色+单一相干 OLT 架构 | 核心判断3：ONU 侧 SOA |
| 11 | 0923-We1-H-00-全场连拍-PON的DSP与均衡（第47–67页）p66 | Rx 灵敏度代价 vs DC 泄漏功率（三配置对比） | 5.3：DC 泄漏 |
| 12 | 0922-Tu1-F2-NokiaBellLabs p5 | 计算量对流数曲线+TSN/BE 时延柱图 | 核心判断5：确定性调度 |
| 13 | 0924-Th2-C1-北邮与中科院-模式分集接收与自适应光学增强的星地自由空间光链路 p18 | 无错帧比例（AO 77.6% vs 3 模 MDR 99.0%） | 5.6：AO 是否够用 |
| 14 | 0920-pm-Su3-D-04-Aircision-自由空间光技术方 p3 | 系统结构+六次演示里程碑（含 World Record，5.7/7.7 Tbps 并存） | 2.8：FSO 记录与数字不一致 |
| 15 | 0920-am-Su2-F-04-OGS-低轨相干链路自适应光学 p7 | 两次过境 ROP 曲线与 Tb 级传输量 | 2.8：LEO 下行在轨结果 |
| 16 | 0922-Tu1-C5-KDDIResearch-光子晶体面发射激光器做自由空间光通信 p12 | EEL/VCSEL/PCSEL 发散角与功率对比 | 第4章第9项：PCSEL FSO |
