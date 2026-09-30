---
title: "B60 · DAY4 · We1-H-PON的DSP与均衡"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We1-H-00-全场连拍-PON的DSP与均衡.pdf（第1–13页）
- 讲者/机构：Luiz Anet Neto 等（IMT Atlantique；署名邮箱 luiz.anetneto@imt-atlantique.fr，其余作者/合作方看不清） | 题目：Equalization and FEC Evaluation Beyond D/E2 Class 50G-PON（据p13） | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 oDSP
- 核心主张：
  1. 评估 50G-PON 下行中均衡（FFE/DFE/MLSE）与 LDPC(17280,14592) 的交互；仅用 pre-FEC BER 估计功率预算是"好的第一近似"，但不计入均衡器损伤与译码器参数 [p12]。
  2. Viterbi MLSE pre-FEC 最好、post-FEC 最差（硬输入丢失可靠度信息）；DFE+软输入 LDPC 最优 [p10,p11]。
  3. 面向 VHSP：IMDD 需要更强均衡与 FEC；相干"更多 DSP、更简单 FEC？"（作为开放问题）[p12]。
- 关键数据：
  - 实验：DFB-EAM-SOA，1342 nm，13 dBm 入纤，25 km，色散 76 ps/nm，25G APD+TIA；LDPC(17280,14592)，分层缩放 min-sum，α=0.75，最多15次迭代；FFE 16 tap，DFE 16+1 tap，MLSE 3 tap [p9,p12]
  - 目标 D/E2 等级功率预算 20–35 dB [p1]
  - post-FEC 功率预算（dB，硬/软输入）：DFE 40.3/41.1；FFE 39.9/40.7；MLSE 40.5/40.5；无均衡 38.5/39.3 [p11]
  - 结论页：41.1 dB DFE+SI-LDPC；40.7 dB FFE+SI-LDPC；40.5 dB Viterbi MLSE+HI-LDPC [p12]
  - MLSE 相对无均衡 HI 提升 2.4 dB；FFE、DFE 相对无均衡 SI 分别提升 1.4 dB、1.7 dB [p10]
  - pre-FEC 估计功率预算（HI 门限 1×10⁻²，SI 门限 2×10⁻²）：无均衡硬输入仅 37.8 dB，与实际 38.5 dB 偏差；MLSE 软输入估计 41.1 dB（标红，与实际 40.5 dB 不符）[p11]
  - 均衡使 LDPC 平均迭代数更快收敛 [p11]
- 提到的公司/客户/产品/标准：ITU-T G.9804（默认 FEC 选项）；G-PON/XGS-PON/NG-PON2 用 RS 一次性译码 [p3,p4]
- 与业界对比或记录声明（SOTA/首次/record）：无明确 record 声明；p4/p6 有 2019–2025 年 50G IM/DD NRZ 光功率预算的文献散点图（约 22–41 dB，最高点为 2025 年显式 LDPC 解码的 [20]–[22] 约 39–41 dB，读图估计，看图核实）；目标 D/E2 预算 20–35 dB [p1, p6]
- 推荐配图页：p10（pre/post-FEC BER 曲线，对比无均衡/FFE/DFE/MLSE 与 HI/SI-LDPC）；p11（功率预算表 + 迭代数曲线）

### 0923-We1-H-00-全场连拍-PON的DSP与均衡.pdf（第14–30页）
- 讲者/机构：Nelson Castro（报告人）, Yiming Li, Mohammed Patel, Frank Smyth, Sergei Turitsyn, Andrew Ellis（Aston University / AIPT，Pilot Photonics） | 题目：Dual Line Coherent Detection（p14 标题页看图核实） | 类型：学术论文
- 方向归属（主/次）：主 1 相干/高波特率 | 次 5 固定与无线接入（相干接入/免温控激光）
- 核心主张：
  1. 提出基于光频梳的检测方法，无需自适应均衡即可大幅放宽频偏（FO）容限 [p30]。
  2. 观测的 SNR 代价接近 LO 散粒噪声预测 [p30]。
  3. 该方法支持 400 Gb/s（16QAM，64 Gbaud）系统 [p30]。
- 关键数据：
  - 系统：64 Gbaud，DP-16QAM，70 GHz 接收机，45 GHz 商用发射机，EO 梳 FSR 40 GHz；频偏通过失谐载波与 LO 梳种子获得；LO 配置 2 线与 4 线（看图核实）[p27]
  - 宽带（excess bandwidth）情形：梳检测频偏容限 136 GHz；双拷贝处理（DC）在整个 FO 范围性能均匀；相对单线约 1.7 dB SNR 代价 [p28]
  - 受限带宽情形：40 GHz 2线梳、32 GHz 4线梳；DC 处理必需；4线梳 DC 检测容限 200 GHz；单拷贝相对 DC 差约 3.4 dB SNR 代价（图注） [p29]
  - 结论：136 GHz（2线 LO，70 GHz 接收机）；200 GHz（4线 LO，32 GHz 接收机）[p30]
  - 设计选择：FSR > 1/2 Rs 以避免混叠；导频置于场边缘以助 FOE；接收用光频梳 + 2x8 90° 混频器 + 4 路 BPD（看图核实）[p19]
  - 背景：此前放宽温控的容限 >36 GHz（36 Gbaud 16QAM，Zeng 2021）、1 THz（24 Gbaud QPSK，Adib JLT 2022）需额外 DSP、增加成本（看图核实）[p18]
- 提到的公司/客户/产品/标准：Pilot Photonics（EO 梳）；参考文献 Lundberg 等 Appl. Sci. 2018；Zeng 等 Opt. Express 2021；Adib 等 JLT 2022 [p17,p18]
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；定位为无需自适应均衡放宽 FO [p30]
- 推荐配图页：p28（BER vs 频偏，SL/SC/DC 三曲线，136 GHz）；p29（受限带宽下 2线/4线梳的 SC vs DC）

### 0923-We1-H-00-全场连拍-PON的DSP与均衡.pdf（第31–46页）
- 讲者/机构：Dylan Chevalier, Luiz Anet Neto, Gaël Simon, Jeremy Potet, Fabienne Saliou, Pascal Scalart, Lucas Inglés, Philippe Chanclou（Université Laval COPL；IMT Atlantique；Orange Research；Univ. Rennes IRISA） | 题目：An Exploratory Study of RS Decoding and Equalization in 50G-PON（We1-H3） | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 oDSP
- 核心主张：
  1. 均衡与 FEC 是 ISI 受限信道提升功率预算的共同目标；探索低复杂度 50G-PON ONU 中数字/模拟均衡 + Reed-Solomon FEC [p45]。
  2. 模拟均衡下 RS(248,216) 相对 HI-LDPC 有 4 dB 代价，但仍满足 E1（33.9 dB）；数字均衡（DFE、MLSE）下 RS 与 HI-LDPC 性能相近，满足 E2/D，余量 >2 dB [p45]。
  3. RS 简单但非迭代，pre-FEC BER 的任何异常直接进入 post-FEC，因此均衡必不可少；FFE/DFE 软输出可配合软判决 RS（Chase）；更强均衡可换更简单 FEC，但需在性能与成本/功耗间权衡 [p45]。
- 关键数据：
  - 实验：50 Gb/s NRZ-OOK，PRBS15，DFB+EAM+SOA，25 km SMF，76.1 ps/nm@1342±2 nm，APD+TIA 25 GHz（Ge/Si），aFFE 6 cell 每 cell 延时 8 ps；带 aFFE 100 GSa/s-33 GHz，不带 200 GSa/s-50 GHz [p34,p35]
  - FEC：RS(248,216) 可纠 16 字节错；LDPC(17280,14592) 分层 min-sum，最多15次迭代，缩放因子 0.75 [p38]
  - 均衡器：dFFE 16 tap；DFE 16 tap + 1 反馈 tap；MLSE 3 tap；LMS 在 3503 符号（约 70 ns）优化，信道估计用 55 符号 [p39,p40]
  - 灵敏度（dBm，pre-FEC BER 1e-2）：无均衡 -22.7；aFFE -24.6；dFFE -25.2；DFE -25.8；MLSE -26.4 [p42]
  - 光路径损耗（dB，同条件）：36；37.9；38.5；39.1；39.7 [p42]
  - post-RS（外推，post-FEC 1e-12）灵敏度：无均衡 -16.6；aFFE -20.6；dFFE -22.1；DFE -24；MLSE -24.8 dBm；对应 OPL 29.9；33.9；35.4；37.3；38.1 dB。aFFE+LDPC：-24.6 dBm，37.9 dB [p44]
  - DFE 相对 MLSE 在 BER=1e-3 仅 +0.6 dB 代价 [p42]
  - DFE/MLSE+RS 较 LDPC+HI-LDPC 基线斜率差，但满足 D/E2（-24 dBm，20–35 dB），余量分别 2.3 dB 与 3.1 dB [p44]
  - MLSE 复杂度随信道记忆 L 指数增长 O(2^L)，文中引用简化分层 MLSE 可降至 O(log L)（Guo 等 Opt. Express 34(9), 2026）；实验：DFB-EAM-SOA TOSA、驱动 29 dB、25 km SMF、APD+TIA、aFFE、RTO 100 GSa/s(33 GHz)/200 GSa/s(50 GHz)（看图核实）[p37]
- 提到的公司/客户/产品/标准：ITU-T 50G-PON（G.9804）D/E1/E2 等级；Orange Research [p32,p44]
- 与业界对比或记录声明（SOTA/首次/record）：自称 exploratory，无 record 声明 [p45]
- 推荐配图页：p44（post-FEC BER 曲线 + 灵敏度/OPL 表，标红 DFE/MLSE+RS）；p42（pre-FEC 直方图与灵敏度表）

### 0923-We1-H-00-全场连拍-PON的DSP与均衡.pdf（第47–67页）
- 讲者/机构：Haipeng Zhang（讲者）, Zhensheng Jia（CableLabs Optical Center of Excellence） | 题目：DSP-Based Mitigation of Extreme DC Leakage for 100G/200G Coherent PON（We1-H4，2026-09-23） | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON（相干 PON 上行突发） | 次 1 oDSP
- 核心主张：
  1. 系统量化 100G/200G 相干 PON 的 DC 泄漏容限，并提出三种互补的缓解方案 [p67]。
  2. 方案为低复杂度，可放宽调制器偏置控制，同时保持 100G/200G 性能（TDM 相干 PON）[p67]。
- 关键数据：
  - 背景：ONU 关断时激光保持开启、靠 IQ 调制器偏置置零做突发门控；有限消光比与偏置漂移产生残余 DC 泄漏；分布式 ODN 差分路径损耗最高 15 dB，近端空闲 ONU 泄漏可淹没远端 ONU 突发；先前方案含 SCM 信号 + 频率翻转外差检测（DC 上变频后被接收带宽滤除）与 Nokia 窄带干扰分析（标准 CMA 失效导致 BER 突跳，Lanneer OFC 2025 Tu2I.2）（看图核实）[p49,p50,p54]
  - 配置1（基带 Tx，零差 Rx）：常规相干 DSP 仅容忍约 -47.1 dBm DC 泄漏；预捕获自适应频域陷波将容限提升到约 -31.1 dBm，但灵敏度仍随泄漏恶化 [p63]
  - 配置2（Tx 数字上变频至 IF，零差/外差 Rx，数字带通）：容限约 -15.1 dBm（DP-QPSK）/ -17.6 dBm（DP-16QAM）；泄漏至 -20 dBm 前灵敏度代价很小；零差与外差性能相当 [p64]
  - 配置3（IF Tx + 外差 Rx + 接收机 EO 带宽边缘滤波）：容限约 -5.1 dBm，远高于突发信号功率 [p65]
  - 灵敏度代价提取：BER=2E-2；DP-QPSK 灵敏度在无泄漏时约 -42.5 dBm（配置2/3），DP-16QAM 约 -34.5 dBm（读自图，近似）[p66]
  - 实验：ECL + 96 GSa/s AWG、40 GHz CDM 发射，另 8 个 ECL 在 f0±2 GHz 内模拟泄漏，EDFA + 相干接收 + 离线 DSP（看图核实）[p60]
- 提到的公司/客户/产品/标准：CableLabs；参考 Zhang 等 OFC 2025（图注）、W. Lanneer 等（Nokia）OFC 2025 Tu2I.2（p54 看图核实）[p54]
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；配置3 在 DC 泄漏容限上最高 [p66]
- 推荐配图页：p66（Rx 灵敏度代价 vs DC 音功率，DP-QPSK/16QAM，三配置对比）；p64（配置2 结构与 BER 曲线）

### 0923-We1-H-00-全场连拍-PON的DSP与均衡.pdf（第68–84页）
- 讲者/机构：Yimin Hu, Yixiao Zhu, Ziheng Zhang, Luyao Huang, Dezhi Zhang, Ming Jiang, Weisheng Hu（上海交通大学；中国电信研究院） | 题目：Hybrid 50G DD and 200G Coherent PON with a Shared OLT based on 67-GHz TFLN MZM and Bias Optimization | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 3 调制器（TFLN）
- 核心主张：
  1. 提出混合 DD-相干 PON：用超宽带 TFLN MZM 作共享 OLT，子载波复用同时发 50G DD 与相干信号，实现与老 ONU 单波长共存 [p84,p73,p76]。
  2. 通过偏置电压与功率比优化，在 DD 与相干 ONU 之间折中 [p79]。
- 关键数据：
  - 实验：ECL 1551.1 nm，约100 kHz；AWG 256 GSa/s，78 GHz 3dB 带宽；发射光功率 11 dBm；20 km SSMF；50 Gbaud OOK（基带）+ 50 Gbaud 16/8/4-QAM（上变频 -52 GHz），保护带 2 GHz，导频 26 GHz；DD 端 70 GHz PD + MLSD [p77]
  - 合并信号带宽约 155 GHz；相干信号载波被抑制 [p78]
  - Vπ=3.6 V，最优偏置 5.46 V（正交点 4.0 V 与零点 5.8 V 之间折中，图中标注） [p79]
  - DD ONU：20 km 后 MLSD 使灵敏度达 -20 dBm；仅发 DD 信号时灵敏度 -27 dBm，共传相干信号带来 7 dB 代价，功率预算 31 dB；B2B 时 MLSD 无增益 [p81]
  - 相干 ONU：16/8/4-QAM 在 20 km 后功率预算 29/31/38 dB；16-QAM 在零点偏置灵敏度 -24 dBm；同时发 DD 信号时灵敏度 -18 dBm，对应功率预算 29 dB [p82/p83（图 p83）]
  - 数值仿真 PD：70 GHz 带宽，0.6 A/W，热噪声 4 pA/√Hz [p79]
- 提到的公司/客户/产品/标准：ITU-T G.984.x / G.9807.1 / G.9804.3 PON 演进；引用 Borkowski OFC 2024、Yan OFC 2026 [p69,p70]；中国电信研究院
- 与业界对比或记录声明（SOTA/首次/record）：无明确 record 声明；WDM 共存需额外滤波器与多激光，本方案称单波长共存（对比表 p76）[p72,p76]
- 推荐配图页：p79（偏置电压与功率比的 DD/相干折中曲线）；p78（共享 OLT 的测得光谱，约155 GHz）

### 0923-We1-H-00-全场连拍-PON的DSP与均衡.pdf（第85–102页）
- 讲者/机构：Ryo Koma, Kazutaka Hara, Jin Uchiyama, Jun-Ichi Kani, Tatsuya Shimada（NTT Access Network Service Systems Laboratories） | 题目：Demonstration of 50-Gbps SSB DCPC Transmission for Over-40-km-Reach and 1:512-Split PON Using Remotely Pumped BiDi-EDFA and Distributed Raman Amplification | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 相干/长途（放大与数字色散预补偿）
- 核心主张：
  1. 提出基于远程泵浦 EDFA + 分布式拉曼放大的长距高分光（LR-HS）PON，用无源分光器和放大器取代电聚合节点，推动机房整合、降低 OPEX/CAPEX [p93,p102]。
  2. 用数字色散预补偿（DCPC）+ SSB 调制解决 C 波段色散与功率衰落 [p89]。
  3. 上下行 50 Gb/s SSB+DCPC 在 40 km 主干 + 20 km 接入、接入段损耗 >30 dB 下检测成功 [p101,p102]。
- 关键数据：
  - 目标：60 km 覆盖、1:512 分光（32用户/口×16口）；CD 容限达 1070 ps/nm（C 波段 17 ps/nm/km，60 km）；总损耗预算：接入 3dB×9+0.2×20km=31 dB，主干 0.2×40km=8 dB，合计 39 dB [p88]
  - 前作对比：120 GBd IM/DD + BiDi-EDFA，功率预算 35 dB，20 km（Borkowski，ECOC 2025）[p90]
  - 结构：1480 nm 泵浦经主干光纤传输；DS 在 C 波段由 DS-EDF 放大，上行在 L 波段由 US-EDF + 分布式拉曼放大 [p94,p95]
  - 增益：DS 输出功率约 +10 dBm（各输入电平）；上行 40 km 拉曼约 10 dB 增益，加 EDFA 总增益 18 dB（输入 -27 dBm）；最小路损（14 dB）对应输入下无光浪涌 [p97,p98,p99]
  - 结果（50 Gbaud DCPC+SSB，FEC 门限 1×10⁻²）：DS-EDF 输出 +11 dBm，US ONU 输出 +4 dBm；可承受接入段损耗：DS-A（64SP-8SP）40/50/60 km 为 32.3/34.0/33.1 dB；DS-B（16SP-32SP）32.3/34.3/33.3 dB；US 29.4/29.4/30.1 dB [p101]
- 提到的公司/客户/产品/标准：NTT；参考 Borkowski 等 ECOC 2025 [p90]
- 与业界对比或记录声明（SOTA/首次/record）：无 record 字样；相对 p90 的 35 dB/20 km 前作，本文扩展到 40–60 km、1:512 目标 [p88,p90]
- 推荐配图页：p101（DS/US BER 与 40/50/60 km 接入损耗容限表）；p98（上行 Raman/EDFA 增益 10 dB / 18 dB）

## 本批小结
1. 本批为 We1-H 场（PON 的 DSP 与均衡）全场连拍，共6讲；50G-PON 下 IM/DD 讲稿（IMT Atlantique 与 Laval/Orange）都在讨论"均衡强度与 FEC 复杂度的折中"：软输入 LDPC + DFE 功率预算约 41 dB，而 RS(248,216) 配 DFE/MLSE 仍满足 D/E2（>2 dB 余量），说明 ONU 侧可用低复杂度 FEC 换更强均衡（第1、3讲）。
2. MLSE 的教训：pre-FEC 最好但因硬输出丢失可靠度信息而 post-FEC 最差（40.5 dB，对 DFE+SI 的 41.1 dB），因此 pre-FEC BER 不能可靠预测 post-FEC 功率预算（第1讲；第3讲结论也强调软输出的重要性）。
3. 相干 PON 成为下一代（100G–400G）的多讲主题，但聚焦点是"降成本的实用障碍"：Aston 用光频梳放宽频偏（136/200 GHz 容限，免温控/免复杂 DSP）；CableLabs 用 DSP 解决上行突发 DC 泄漏（容限从 -47.1 提升到 -5.1 dBm）；SJTU 用共享 TFLN OLT 让 50G DD 与 200G 相干共存（第2、4、5讲）。
4. 共存与升级路径：SJTU 采用单波长子载波复用（合并带宽约155 GHz，最优偏置5.46 V），DD 与相干 ONU 功率预算 29–38 dB，共传代价约 7 dB；与之对照，NTT 走放大路线，用远程泵浦 EDFA + 拉曼把 1:512、40–60 km 目标做到接入段损耗 >30 dB（第5、6讲）。
5. 色散处理两条路：NTT 用 DCPC+SSB 的发送端数字预补偿（C 波段 60 km 约 1070 ps/nm）；SJTU 在 DD ONU 用 MLSD 处理 20 km 色散衰落（-20 dBm 灵敏度），两者均把 DSP 转移到 OLT 或采用小 tap 均衡（第5、6讲，及第1、3讲）。
