---
title: "B65 · DAY4 · We2-H-空分复用传输"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We2-H1-1419-埃因霍温-超高容量空分复用综述.pdf
- 讲者/机构：Chigo Okonkwo，埃因霍温理工大学（TU/e）High-Capacity Optical Transmission Lab，与 NICT 联合署名（页标 NICT TU/e）| 题目：Space Division Multiplexing for Ultra-High Capacity Optical Communications | 类型：邀请报告（We2-H1，11:00–11:30）
- 方向归属（主/次）：主 1 相干/海缆/长途；次 4（空间通道整体交换，仅展望）
- 核心主张：
  1. 125 µm 包层内的 19 芯随机耦合多芯光纤（RC-MCF）：随机耦合使延迟扩展随距离增长变慢（由线性增长变为近似平方根增长），联合 MIMO 恢复空间信道（p8、p26）。
  2. 研究点从 1.7 Pb/s@63.5 km（2023）到 568.8 Tb/s@5,166 km（2025）再到 434.6 Tb/s@8,610 km（2026），长距离 C+L 传输已验证（p25、p26）。
  3. 下一步：多芯适用的高效放大器、实时 DSP、低损耗器件、空间信道整体交换；实时 38×38 MIMO 的吞吐、功耗、时延尚未演示（p19、p24、p26）。
- 关键数据：
  - 首个 19 芯 RC-MCF：纤芯间距 18 µm，有效面积 62 µm²，1550 nm 损耗 0.215 dB/km，长度 63.5 km，SMD 系数 10.8 ps/√km（1550 nm）[p10]
  - 63.5 km 实验：381 波长，24.5 GBaud DP-64QAM，C+L；接收 76 路电采集、80 GSa/s，38×38 MIMO、81 个半符号间隔抽头 [p12]
  - 1.7 Pb/s（FEC 译码后聚合吞吐）/ 1.8 Pb/s（GMI 估计），63.5 km、19 芯、125 µm 包层；每波长约 3–5 Tb/s，1530–1610 nm，L 波段长波端下降 [p14]
  - 新一代 19 芯 RC-MCF：最低损耗 0.187 dB/km@1550 nm，C+L 波段 SMD 低于 10 ps/√km（图上约 8.3–9 ps/√km）；相比上一代在 L 波段损耗明显更低 [p15]
  - 长途环路：19 路同步环路，每圈 86.1 km，60 圈=5,166 km；150 ns 步进 1×19 分路延迟；38 个 WaveShaper 平坦 C+L 谱；38 根跳线光程匹配至 1 cm 内 [p16、p18]
  - 频谱：175 个 C+L 信道，50 GHz 栅格，测试带为 3 信道滑动、49 GBaud QPSK；C 端 195.85 THz（1530.72 nm），L 端 186.35 THz（1608.76 nm）[p17]
  - 接收 DSP：38²=1,444 个 FIR 滤波器，每个带时域记忆 [p19]
  - 信道特性：8,610 km 处冲激响应时长低于 6 ns，MDL 低于 10 dB；5,166 km 处 C/L 波段时长相当 [p20]
  - 568.8 Tb/s（FEC 译码后），5,166 km，175 WDM 信道×19 芯，C+L；容量距离积 2.93 Eb/s·km；每信道约 3.3–3.6 Tb/s（1570–1576 nm 附近有凹陷）[p21]
  - 434.6 Tb/s@8,610 km（FEC 译码），GMI 估计 470.4 Tb/s；容量距离积 3.74 Eb/s·km；100 圈×86.1 km；左图显示 3,500 km 处约 600–630 Tb/s 量级，随距离递减 [p22]
  - PSC 演示（引 Kalla，WeP1-A2.1）：四个线路侧，无色/无方向/无竞争，每线路侧 119 Pb/s 线路速率；空间超级信道整体交换 [p24]
  - 2018 年预测（Winzer 等）在 2026 年：40% 缩放约 1.5 Pb/s；海缆约 0.5 Pb/s/缆；陆地约 140 Tb/s/纤 [p25]
- 提到的公司/客户/产品/标准：NICT、PhotonDelta、HOMTech（EU MSCA 博士网络）；早期项目 EXAT（日本）、ModeGAP（欧盟）、Nokia Bell Labs（6×6 MIMO）；光子灯笼、激光直写 3D 波导扇入扇出；Inoue（OECC 2024，低损耗光纤）。
- 与业界对比或记录声明：3.74 Eb/s·km 标为“[23] 中报告的记录容量距离积”（讲者原话 record capacity-distance product reported in [23]，Kalla JLT 2026）[p22、p26]；历史对比：EXAT 1.01 Pb/s@52.4 km（12 芯，222 波/芯，DP-32QAM，2012）、ModeGAP 73.7 Tb/s 毛速率@119 km（2012）[p5]
- 推荐配图页：p25（2018 预测与 2026 三个研究点 A/B/C 对比，SDM/WDM/调制三层容量演进曲线）；p22（8,610 km 434.6 Tb/s 与 3.74 Eb/s·km）；p15（新一代光纤 0.187 dB/km 损耗与 SMD 曲线）

### 0923-We2-H2-148-分离与耦合芯放大对MDL与SMD的影响.pdf
- 讲者/机构：Taiji Sakamoto，Masaki Wada，Ryota Imada，Kazuhide Nakajima，Takashi Matsui，NTT Access Network Service Systems Laboratories | 题目：Impact of Separated / Coupled-Core Amplification on MDL and SMD in Coupled Multi-Core Fibre Links | 类型：学术论文（We2-H2）
- 方向归属（主/次）：主 1 相干/海缆/长途；次 无
- 核心主张：
  1. 耦合芯 MCF 链路中，中继器特性沿链路累积，MDL 与 SMD 累积成为关键设计因素（p3）。
  2. 并联 SM-EDFA（Type A）需要 EDF 与器件严格匹配才能抑制宽带 MDL；仅增益相等不够（p4、p6）。
  3. 耦合 4 芯 MC-EDFA（Type B）依靠芯间随机模式耦合使 MDL 平均化，整个 C 波段 MDL 近似与波长无关且 SMD 可忽略，无需扇入扇出（p12、p16）。
- 关键数据：
  - 数值参考（Type A）：EDF 长 L=9 m，芯半径 a=2.5 µm，Δ=0.5%，8 波 WDM 1530–1565 nm；输入 −15 dBm/核，泵浦 +4 dBm/核；芯半径变化小于 10% 时，1530 nm 处 MDL 最高约 4 dB [p7]
  - 即使 EDFA 完全一致，扇入/扇出端口和延迟线的插损差异也会抬高带边 MDL（图例 1 dB、2 dB 损耗差）[p8]
  - Type B：模耦合越强 MDL 越低，0 dB/10 cm 时 MDL 近似与波长无关（对比 −20、−10 dB/10 cm）[p9]
  - 被测放大器：Type A 用商用 SM-EDFA（型号 AEDFA-PA-25-AOCP，小信号增益 >37 dB，最大输出 >+10 dBm），未为提升一致性专门制作；Type B 为单个耦合 4 芯 EDF，Er 浓度变化 <6.6%，多模 LD 976 nm 包层泵浦，耦合约 0 dB/3.5 cm [p10]
  - 实验（所有 MCF 器件构成的全 SDM 再循环环路）：8 波输入（7 路 CW+1 路 1.25 Gb/s QPSK），1530–1565 nm，5 nm 间隔，−15 dBm/核；15 km 4 芯光纤，跨段损耗 >20 dB [p14]
  - RMS MDL 惩罚（图）：Type A-1 在 1530 nm 约 0.9 dB，1545–1555 nm 约 0.1 dB，1565 nm 约 0.36 dB；Type A-2+延迟线约 0.2–0.37 dB；Type B 约 0.03–0.1 dB。（Type B 各波长曲线较平，但讲者文字称 B 总体 MDL“略高于 Type A-1”，两者与图上读数不完全一致，以图读数为准，仅供参考）[p12]
  - 环路：RMS MDL 随圈数线性增长，12 圈约 2.2–2.3 dB，1530/1550/1565 nm 几乎重合；脉冲宽度 σ 由约 0.07 ns（0 圈）增至 12 圈约 0.15–0.17 ns，Type B 与 Type A-2+延迟线相当 [p15]
  - 对比表：Type A 需扇入/扇出，有独立增益控制（每核泵浦），带边 MDL 上升，SMD 取决于 EDF 长度离散；Type B 不需要扇入/扇出，无独立增益控制（包层泵浦），MDL 平坦，SMD 低 [p16]
- 提到的公司/客户/产品/标准：NTT；参考 T. Sakamoto et al., JLT vol.44, p.4234 (2026)。
- 与业界对比或记录声明：无 SOTA/record 声明。
- 推荐配图页：p12（四种配置的 MDL 随波长曲线与脉冲响应对比）；p15（环路圈数下 RMS MDL 与脉冲宽度）；p16（A/B 两类中继器特性对比表）

### 0923-We2-H3-1012-分布拉曼放大90km模式相关增益.pdf
- 讲者/机构：Divya A. Shaji（L'Aquila 大学/CNIT），合作者 Q. Moonen、M. van den Hout、V. van Vliet、B. Kalla、T. Bradley、A. Mecozzi、C. Okonkwo（TU/e）、C. Antonelli | 题目：Characterization of Mode-Dependent Gain in Distributed-Raman-Amplified 90-km Multi-mode Fiber with Remote Digital Holography | 类型：学术论文（We2-H3）
- 方向归属（主/次）：主 1 相干/海缆/长途；次 6（远端数字全息表征，非传感）
- 核心主张：
  1. 用远端数字全息（RDH，中继激光提供参考光）在 90 km 三模渐变折射率多模光纤（GI-MMF）上表征模式相关增益（MDG）。
  2. 泵浦最高阶模（LP11a/LP11b）时 MDG 保持一致。
  3. 传输系统中的 DRA 增益验证了观测到的 MDG（p19）。
- 关键数据：
  - 传递矩阵 T 的 MDG 定义为 20log10(max{Ai}/min{Ai})，Ai 为 T 的本征值 [p9]
  - MDL 统计（泵浦模式×泵浦功率）：泵浦 LP01：无泵浦 1.7 dB，25 dBm 2.5 dB，27 dBm 2.8 dB，28 dBm 3.4 dB；泵浦 LP11a：1.6/1.4/1.5/1.6 dB；泵浦 LP11b：1.5/1.6/1.7/1.5 dB（依次为无泵浦、25、27、28 dBm）[p10]
  - DRA 开关增益汇总：泵浦 LP01 时 Gmax 约 6.5 dB（25 dBm）、约 11 dB（27 dBm）；泵浦 LP11a/LP11b 时约 3.5–4 dB（25 dBm）、约 6 dB（27 dBm）；模间增益差 ΔG：泵浦 LP01 约 2.5 dB（25 dBm）、约 4 dB（27 dBm），泵浦 LP11a/b 约 0.3–0.5 dB [p17]
  - 结果为读图估算，非讲者文字数值，仅供参考。
- 提到的公司/客户/产品/标准：文献引用：Bell Labs 137 km 少模模式均衡分布拉曼（Ryf）、Mizuno（NTT）1000 km 三模混合 MC-EDFA/拉曼等；Shaji OFC 2026（现场部署 15 模 GI-MMF 拉曼增益）；Sakuma（JJAP 2024）、Kawai（OFC 2023，75.2 km 少模远端数字全息）。
- 与业界对比或记录声明：无 SOTA 声明（引言页 p2 罗列以往少模/多模拉曼放大工作）。
- 推荐配图页：p10（不同泵浦模式与功率下 MDL 分布小提琴图）；p17（DRA 增益与模间增益差汇总）

### 0923-We2-H4-1326-19芯异质光纤色散分集信号处理.pdf
- 讲者/机构：Mario González, Mario Ureña, Sergi García, Thomas Stelzer, Linda Uta, Michael Frosz, Ivana Gasulla；Photonics Research Lab（iTEAM，瓦伦西亚理工大学）与 Max Planck Institute for the Science of Light | 题目：Demonstration of Dispersion-Diversity Signal Processing Using a 19-Core Heterogeneous Multicore Fiber | 类型：学术论文（We2-H4）
- 方向归属（主/次）：主 5 固定与无线接入（微波光子/RoF 信号处理）；次 1（MCF 光纤设计）
- 核心主张：
  1. 首次制造 19 芯异质 MCF，可作为可调光真延迟线（TTDL）：仅用 3 种预制棒（TA-SI、RA-GI、TA-TI 折射率分布）得到 19 种不同纤芯（p11）。
  2. 实验验证 TTDL 作为微波光子（MWP）滤波器，最多 13 个采样点（p11）。
  3. 首轮制造传输损耗偏高，是主要缺点（p11）。
- 关键数据：
  - 设计策略：预制棒共享与径向缩放以降成本，纤芯重叠以提高制造鲁棒性；共差分色散 ΔD=D(n+1)−D(n)，共差分群时延（p5、p6）
  - 表征：最差串扰 <−23 dB/km；13/15 个采样（D 值）实现正常 TTDL 运行，DGD 演化恒定，D 值略高于设计值但 ΔD 仍恒定；损耗高，归因于结构形变与残余材料吸收 [p9]
  - 图上：1 km 内各芯归一化功率下降，最差芯 1 km 约 −10 dB；DGD 在 1530–1570 nm 最大约 600 ps；色散 D 约 8–23 ps/nm/km 随芯编号变化（图读数）[p9]
  - MWP 滤波实验：5 波长激光梳（波长分集）经 EOM、EDFA、1×16 分路、13 通道扇入，1 km 异质 MCF，扇出后 VOA+VDL、合路、PD，VNA 测量；Core 1、10、18 的测量与仿真频响吻合较好，频率范围 0–25 GHz [p10]
- 提到的公司/客户/产品/标准：iTEAM，Max Planck Institute for the Science of Light；场景：无线与 Beyond 5G/6G、相控阵天线波束成形、并行均衡。
- 与业界对比或记录声明：讲者称 First-ever fabrication of a 19-core heterogeneous MCF that operates as a tunable TTDL（结论页 p11）。
- 推荐配图页：p9（MCF 损耗、串扰、DGD 与色散表征）；p10（MWP 滤波实验装置与 Core 1/10/18 频响）

## 本批小结
1. 空分复用的长途化路径集中于随机耦合 19 芯 MCF：H1 给出 1.7 Pb/s@63.5 km、568.8 Tb/s@5,166 km、434.6 Tb/s@8,610 km（3.74 Eb/s·km），并指出瓶颈是实时 38×38 MIMO DSP（1,444 个 FIR）、低损耗扇入扇出和多芯放大器（H1）。
2. 耦合芯系统的核心矛盾是 MDL 与 SMD 累积：H2 显示耦合 4 芯 MC-EDFA 通过随机模式耦合得到波长平坦的 MDL、低 SMD 且免扇入/扇出，而并联 SM-EDFA 需严格匹配，此结论与 H1 关于“需要高效多芯放大器”的展望互相呼应（H1、H2）。
3. 光纤本身持续降损：新一代 19 芯 RC-MCF 最低损耗 0.187 dB/km（对比上一代 0.215 dB/km，H1）；H4 的异质 MCF 首轮损耗偏高，说明特殊设计多芯光纤仍受制造质量限制（H1、H4）。
4. 模式相关增益同样是分布式放大的问题：H3 发现泵浦 LP01 时模间增益差随泵浦功率增大（25 dBm 约 2.5 dB，27 dBm 约 4 dB），泵浦高阶模 LP11a/b 则约 0.3–0.5 dB，提示泵浦模式选择可控制 MDG（H3，读图估算）。
5. SDM 光纤的应用范围超出通信：H4 将异质 MCF 用作 2D 光真延迟线与 MWP 滤波器，面向 5G/6G 与波束成形，属于 SDM 光纤向分布式信号处理的延伸（H4）。
6. 本场四篇均为学术/邀请报告，大多由 TU/e、NTT 等研究机构完成，多为实验室级别演示（环路、离线 DSP），距商用部署仍有距离（H1–H4）。
