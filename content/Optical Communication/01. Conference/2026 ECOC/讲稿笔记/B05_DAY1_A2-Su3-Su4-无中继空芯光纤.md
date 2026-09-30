---
title: "B05 · DAY1 · A2-Su3-Su4-无中继空芯光纤"
tags:
  - ECOC2026
  - DAY1
---

# B05 笔记：ECOC 2026 Workshop "Could 100s-km long unrepeatered HCF links redefine the economics & design of terrestrial and submarine optical networks?"（9/20 PM，Su3/Su4 无中继空芯光纤）

说明：本批 6 个 PDF 实为同一场 Workshop 的连拍。B-01 文件内含开场 + YOFC + 领纤(Linfiber) + Nokia Bell Labs 四段（B-02 与 B-03 与其中两段大量重复，manifest 已标 dup）。以下按讲稿切分；页码为 PDF 内页码。数值凡标 [pN] 均经看图核对；标"OCR"者未看图，仅供索引。

### 0920-pm-Su3-B-01-长飞YOFC-长跨空芯光纤设计.pdf（第1–6页，Workshop 开场/组织者页）
- 讲者/机构：J. Renaudier, R. S. Luis, G. Rademacher, B. J. Puttnam（组织者，题目页未列机构）| 题目：Could 100s-km long unrepeatered HCF links redefine the economics & design of terrestrial and submarine optical networks? | 类型：Workshop
- 方向归属（主/次）：1 相干/海缆/长途 / 无
- 核心主张：
  1. 用路由长度分布论证"百公里级无中继"的适用面：陆地云网与海缆的链路长度分布（看图核实 p2）。
  2. 空芯光纤（HCF）与实芯光纤的容量公式对比页（Shannon 容量 C = 2N·B·log2(1+SNR)，Hollow Core vs Solid Core，OCR）。
  3. 议程：Session 1 光纤与放大器（Li Peng/YOFC、Yingying Wang/Linfiber、Nicolas Fontaine/Nokia Bell Labs、Lutz Rapp/Adtran、Vitaly Mikhailov/Lightera、Ronit Sohanpal/UCL）；Session 2 系统工程（Radan Slavik、Haik Mardoyan、Dong Wang、Alexis Carbo Meseguer、Yang Hong）[p5–p6]。
- 关键数据：Microsoft 陆地云网路由长度分布（引 M. Filer, JOCN 8(7), 2016：≤200 km 约 9.5%、200–600 约 23.5%、600–1000 约 21.5%、1000–1500 约 23.5%、1500–2000 约 14%、>2000 约 7%）；海缆"约80%连接短于1200 km"（看图核实）[p2]。
- 提到的公司/客户/产品/标准：Microsoft Cloud、YOFC、Linfiber、Nokia Bell Labs、Adtran、Lightera、UCL。
- 与业界对比或记录声明：无。
- 推荐配图页：p6（六位 Session 1 讲者与题目一览，可作为本场结构图）。

### 0920-pm-Su3-B-01-长飞YOFC-长跨空芯光纤设计.pdf（第7–18页）
- 讲者/机构：Li Peng / YOFC（长飞）| 题目：Paradigm Shift in Hollow Core Fiber: From Technology-Push to Application-Driven | 类型：Workshop（邀请报告）
- 方向归属（主/次）：1 相干/海缆/长途（HCF 光纤与海缆）/ 次：2 Scale-across（DCI 用 HCF）、4 Scale-up（DCN 短距 O 波段 HCF）
- 核心主张：
  1. HCF 研发范式由"技术推动（能否做得更好）"转向"应用驱动（是否解决真实问题）"，按 DCN / DCI / 长途三类场景分别定义光纤（芯径、涂覆径、损耗、IMI）[p9–p10]。
  2. 核心优势为低时延、低非线性、超低损耗、低色散；但制造良率、部署物流、维护与总拥有成本是规模商用的关键[p16]。
  3. 结语：并非追求实验室最优，而是"做市场合适的方案"，需在性能、场景、成本间权衡[p16]。
- 关键数据：
  - 三类场景：DCN 基准 G.657.A2，距离米~2 km；DCI 基准 G.652.D，数 km~100+ km；长途 基准 G.654，数百~数千 km；长途关键需求为超低损耗、长跨距、宽谱、低 IMI [p10]。
  - DCN 用 O 波段 HCF（1310 nm/CWDM）：芯径 14 µm、包层 140 µm、涂覆 240 µm；单模（短距）>8 m；满足 G.657.A2 弯曲；损耗谱最低处约 1.1–1.2 dB/km（读图估计）；MPI 随光纤长度线性拟合，LP11 约 6 dB/m [p11]。
  - DCI 用减径 C+L 波段 HCF：芯径 23 µm、包层 210 µm、涂覆 295 µm；最低损耗 0.05 dB/km、典型 0.10 dB/km；IMI ≤ -55 dB/km；弯曲 R30 mm 100 圈 ≤0.05 dB；涂覆径从过去约 370–400 µm 降到约 295 µm 以提高线缆光纤密度；小芯径导致色散更大（23 µm 芯 1460–1625 nm 约 3→8 ps/nm/km，29 µm 芯约 0.3→4 ps/nm/km，读图估计）[p12]。
  - 长途用超低损耗低 IMI C+L 波段 HCF：芯径 29 µm、包层 230 µm、涂覆 370 µm；最低 0.032 dB/km、典型 0.08 dB/km；IMI ≤ -60 dB/km；弯曲 R30 mm 100 圈 ≤0.1 dB [p13]。
  - GTA-ST-HCF 45.26 km 样品 1550 nm 损耗：OSA 三次 0.0292/0.0297/0.0297 dB/km；OTDR（双向）0.035 dB/km；光源+功率计 0.035 dB/km；标称 0.032±0.003 dB/km；IMI = -63.6 dB/km（1549–1551 nm 功率抖动法）[p13]。
  - 气体线吸收：OFC 2026 PDP 的 266 km HCF（未做气体后处理）C+L 波段仍有明显吸收峰；最新 383 km HCF（拼接经气体后处理的空芯纤）在 C+L 波段无气体吸收线，S 波段（约 1460–1500 nm）水汽吸收线仍在；谱线最低约 0.09–0.10 dB/km 量级（读图）[p14]。
  - HCF 海缆：2.3 km 样缆 BYROC-1 LW（6 芯 HCF）；着色/铠装/护套各工序后 6 根纤损耗约 0.055–0.08 dB/km，无明显附加损耗；1550 与 1625 nm 热循环测试（横轴约 250 h、温度约 -30~80 度区间，读图）下损耗变化约在 ±0.03 dB/km 以内 [p15]。
  - 听众投票（Menti，77/150 人应答）问长途部署的关键挑战：损耗、IMI、直径/线缆密度、稳定性寿命、成本；OCR 显示"成本"票数最高（约39），数字未核图 [p17；结果页为 UCL 文件 p14]。
- 提到的公司/客户/产品/标准：YOFC、BYROC-1 LW 海缆、G.657.A2、G.652.D、G.654、OFC 2026 PDP（266 km HCF，Th4B.7 21.7 Tb/s 净速率跨洋传输）。
- 与业界对比或记录声明：p14 引用的 266 km HCF 稀疏中继 21.7 Tb/s 跨洋传输为他人/本团队此前结果，页上未标 SOTA 字样；383 km 拼接链路为"latest progress"[p14]。
- 推荐配图页：p13（长途 HCF 0.032±0.003 dB/km 损耗谱与 IMI）；p14（气体线吸收 266 km 对比 383 km）；p10（DCN/DCI/长途三类需求框架）。

### 0920-pm-Su3-B-01-长飞YOFC-长跨空芯光纤设计.pdf（第19–37页；同讲另见 B-02 文件）
- 讲者/机构：Yingying Wang & Linfiber Team / Linfiber Tech（领纤，www.linfiber.com）、暨南大学（Jinan University，Guangzhou）（p19 标题页看图核实）| 题目：Development of AR-HCF for long haul networks | 类型：Workshop（邀请报告）
- 方向归属（主/次）：1 相干/海缆/长途（HCF 长途传输）/ 无
- 核心主张：
  1. 长途 HCF 三大限制：累计损耗（每多 0.01 dB/km，100 km 多 1 dB）、气体线吸收（CO2 窄线吸收造成 OSNR 损失且功率均衡无法恢复）、模间干扰 IMI（高阶模回耦至基模并累积）[p20，看图核实]。
  2. 光纤层面：拉丝塔在线去 CO2 + 后处理；系统层面：自适应中心波长与 17–68 GBd 波特率绕开 CO2 线[p27–p31]。
  3. 结论："HCF 已被证明是长途首选光纤，剩余障碍是有明确解法的工程问题"；剩余问题：长期机械/老化/线缆寿命、线缆密度与宏微弯敏感性、良率与价格[p35 结论页；B-02 p20 看图核对]。
- 关键数据：
  - 芯径-损耗折中：33.6 µm 芯、230/380 µm 玻璃/涂覆、0.052 dB/km、对弯曲敏感（Gao et al., ECOC 2025 PDP Th03.01.1）；14.8 µm 芯、145/250 µm、0.25 dB/km、弯曲不敏感（Mahadiraji et al., ECOC 2025 PDP Th03.01.2，Microsoft Azure）（看图核实）[p21]。
  - 大芯设计：单塔 1 个月拉制 967.7 km（C+L 波段）；≤0.1 dB/km 的长度 903.41 km；加权平均 0.068 dB/km；一根约 30 km 样纤 0.038 dB/km；参数表：1550 nm 衰减最小 0.038 / 平均 0.07 dB/km，IMI <-65 dB/km，C+L，5 cm 半径 100 圈弯曲 <0.1 dB，PMD <0.2 ps/√km [p22]。
  - 大芯的代价：微弯/宏弯增大、线缆密度降低、布缆复杂；"追求超低损耗有科学价值，但工业应用价值有限"（看图核实）[p23]。
  - 中芯设计（"务实路线"）：SMF 损耗记录 0.14 dB/km、HCF <0.04 dB/km；商用产品 SMF 0.2 dB/km、HCF 0.1 dB/km；约100 km 现场路由布放拼接后实测 0.1 dB/km [p24]。
  - 中芯量产统计（B-02 p6）：单塔 1 个月拉制 1273.59 km；≤0.1 dB/km 的长度 999.96 km；加权平均 0.088 dB/km；参数：1550 nm 最小 0.06 / 平均 0.09 dB/km，IMI -60 dB/km，R=3 cm 100 圈弯曲 <0.1 dB，色散 <5 ps/nm/km，PMD <0.2 ps/√km；约 16 km 样纤双向 OTDR 0.060 dB/km @1550 nm [B-02 p6]。
  - 153 km IT-DNANF 链路：5 段 18.7/29.3/41.1/35.8/28.4 km 共 153.3 km，中间 4 个熔接点；IMI -65.3 dB/km；最低损耗 75 mdB/km @1550.2 nm；但 CO2 吸收线强（谱 1523–1573 nm，约 1565–1573 nm 一侧损耗升至约 0.3 dB/km）；双向 OTDR 1550.0 nm（曲线上标 11.5 dB）（Zhang et al., CLEO 2026 PDP SW3A.2）[p25]。
  - 循环环实验：自适应波特率 17–68 GBd；中心波长绕 CO2 线移动；PCS-16QAM 2.8 或 3.2 bit/symbol；153.34 km IT-DNANF 入纤 25 dBm；含 AWG 128 GSa/s、接收 256 GSa/s [p27]。
  - 结果：110 路 WDM（灵活/50 GHz 栅格）在 12,113 km 环路达 24.8 Tb/s；容量-距离积（GMI）300.4 Pb/s·km，为 AR-HCF 传输最高；另一点为 10,273 km [p28]。
  - 在线去 CO2：共 845.8 km 光纤统计，CO2 吸收损耗中位数 <0.039 dB/km，58.87%（497.9 km）低于该值 [p29]。100 km 链路 9 盘拼接，残余气体线吸收 GLA 0.0107 dB/km（分辨率 1 pm，看图核实）[p30]。
  - 后处理去 CO2：光纤长度受限（约 3 km）且耗时 >2 周；样品 A 2.1 km 未处理、B 2.8 km 与 C 1.5 km 已处理（Xiong et al., ECOC 2025 W.02.01.08）[p31]。
  - IMI：拉丝塔去 CO2 后 −68 dB/km；10.5 km 样品 −70.06 dB/km，104.7 km 样品 −67.83 dB/km；IMI 系数 = 20log10(σ/P_ave) − 10log10(2L)（看图核实，B-02 p18 同）[p33]。
  - 100 km 综合指标（中芯，9 盘拼接）：损耗 <0.1 dB/km；残余 GLA 0.01 dB/km；IMI -68 dB/km；R=3 cm 弯曲 0.1 dB/100 圈 [p34]。
- 提到的公司/客户/产品/标准：Linfiber、Microsoft Azure、深圳/鹏城实验室（页角 logo，OCR 不确定）、IT-DNANF/DNANF/NANF 结构。
- 与业界对比或记录声明：p28 声称 300.4 Pb/s·km 为"AR-HCF 传输最高容量距离积"（含对标散点图，参考文献 [5]–[10]）。
- 推荐配图页：p28（24.8 Tb/s @12,113 km 与容量-距离基准图）；p29（在线去 CO2 的损耗直方图）；B-02 p6（1273.59 km 单塔损耗统计与参数表）。

### 0920-pm-Su3-B-02-Linfiber-长跨空芯光纤设计.pdf（第1–22页，同上讲的完整版）
- 讲者/机构：Yingying Wang & Linfiber Team / Linfiber Tech、暨南大学 | 题目：Development of AR-HCF for long haul networks | 类型：Workshop
- 方向归属（主/次）：1 相干/海缆/长途 / 无
- 核心主张：与 B-01 p19–37 相同（见上节），此文件为该讲独立成册。
- 关键数据：独有页新增数值见上节标注 [B-02 p6]（1 个月单塔 1273.59 km 中芯统计：加权平均 0.088 dB/km、≤0.1 dB/km 达 999.96 km；中芯 HCF 1550 nm 最小 0.06/平均 0.09 dB/km、IMI −60 dB/km、R=3 cm 100 圈弯损 <0.1 dB、色散 <5 ps/nm/km、PMD <0.2 ps/√km）、p12（自适应谱分配 110 信道 24.8 Tb/s@12,113 km、300.4 Pb/s·km，17–68 GBd）、p14（845.8 km 在线去 CO2 统计）、p18（IMI）、p19（100 km 综合指标：<0.1 dB/km、残余 GLA 0.01 dB/km、IMI −68 dB/km、0.1 dB/100 圈@r=3 cm）[p6, p12, p14, p18, p19，看图核实]。p19 小图显示 1520–1620 nm 损耗曲线在约 0.09–0.13 dB/km 区间，长波端上翘至约 0.14 dB/km（读图）。
- 提到的公司/客户/产品/标准：同上。
- 与业界对比或记录声明：同上（300.4 Pb/s·km）[p12]。
- 推荐配图页：p6（中芯量产统计与参数表）；p19（100 km 链路综合指标）。

### 0920-pm-Su3-B-01-长飞YOFC-长跨空芯光纤设计.pdf（第38–50页；同讲另见 B-03 文件）
- 讲者/机构：Nicolas Fontaine + Collaborators + AI / Nokia Bell Labs | 题目：Characterization of Long Fibers | 类型：Workshop（邀请报告）
- 方向归属（主/次）：1 相干/海缆/长途（长纤测量/监测）/ 次：6 光纤传感（OFDR 分布式测量）
- 核心主张：
  1. 对工作坊问题的回答："显然是 YES：不受限的波长、惊人的高功率承受能力、少得多的 DSP 需求、新颖应用"[B-03 p2/p3]。
  2. 长跨 HCF 的瓶颈可能不在传输而在"测量与监测"：HCF 背向散射比 SMF 低 30–45 dB，且无中段接入、无法截断法测量[B-03 p20、p21]。
  3. Bell Labs 长距相干 OFDR（原为海缆开发）单端测量散射幅度与相位，可同时读出散射系数、衰减、双折射、模式变化与温度，并可用静态侧壁散斑作"指纹"（可读作分布式光栅）[B-01 p44，看图核实]。
- 关键数据：
  - HCF 两类背向散射：气体分子动态瑞利散射约比 SMF 低 30 dB（Doppler 展宽约 500 MHz，散斑 ps 级退相干；对压力敏感），玻璃表面粗糙度静态散射约比 SMF 低 45 dB（Numkam Fokoua et al., APL Photonics 6, 096106, 2021）[B-01 p41，看图核实]。
  - OTDR（LOR-200）测 NANF：4.3 km / 3.4 km NANF 与 1 km SMF 对比（SMF −75 dB/m，NANF 低约 29 dB），实测背散与预测的"比 SMF 低 30 dB"一致（Slavik et al., Opt. Express 30, 31310, 2022）[B-01 p42，B-03 p8，看图核实]。
  - 此前 OFDR：NANF 背散比 SMF 低 45 dB，与粗糙度预测一致；220 m NANF 上 1 m 分辨率（Michaud-Belleau et al., Optica 8, 216–219, 2021）[B-03 p9，OCR]。
  - 相干 OFDR 参数：250 MHz 调制对应 0.3 m 理论分辨率；100 km 处 3–25 m；已测过 >4 条海缆（看图核实）[B-01 p44]。
  - 100 km 跨段测量：前向/后向注入，反射标度 -60~-160 dB/m，动态范围标注 +90 dB 与 +50 dB；事件的半高宽 3 m、10 m、25 m。图中对照为 SMF（红线标 SMF）。对该跨段用 2.5log10(F/B) 得损耗约 0.2 dB/km、10log10(F×B) 得局部散射，散射与 R^-6 成比例——该 100 km 演示对象是 SMF 而非 HCF[B-03 p3、p11、p14]。
  - 6000 km 有中继海缆示例：每 50–80 km 一个 EDFA，约150跨、每跨10–15 dB，合计约 2000 dB 损耗与 2000 dB 增益（页内 6000 km 处另注"约 1000 dB 损耗由 >100 个放大器补偿"），环回（loopback）周期性把背散送回[B-01 p47]。
  - 长距 OFDR 试验：实验室新到 HCF，约可看穿 5–6 盘；最佳单盘可看 500 km；看接头可达 1000 km，>2000 km 仅看接头（页上手绘引线标注）；提问"能否像海缆一样加反射器/环回来监测长跨？"[B-03 p16、p17]。
  - 其他分布参数：SMF 与 HCF 的偏振相关散射对比，HCF 中偏振振荡不明显（图上标 0.6 dB 与 "No oscillations"），可否测分布双折射+PMD 与高阶模含量（MPI）为开放问题[B-03 p18]。
  - OFDR 挑战：物理极限（需 2000 W 入纤功率？）、激光线宽（mHz 级）与 RIN、累积环境噪声（降低光纤末端空间分辨率）、噪声底（ASE、量子、空气散射）；场景：100 km@22 dB（OFC 2025 PDP 结果）、300 km@20 dB、1000 km@0.05 dB/km 共 50 dB、10000 km@0.01 dB/km 共 100 dB（看图核实）[B-01 p50]。
  - 观众投票 2：到 2028-11-23 能 OFDR 的最长跨距？现状：301.7 km 无中继 HCF 跨段（实验室）；200.5 km 反谐振 HCF 上全 C 波段 25.6 Tb/s；34–37 dBm 入纤功率下未见 FWM；多家厂商声称损耗 0.05–0.11 dB/km；"300 km、0.05 dB/km 仅 15 dB 光纤损耗，极限可能是能测/能监控多少而非能传多少"[B-03 p21]。
- 提到的公司/客户/产品/标准：Nokia Bell Labs、LOR-200 OTDR、NANF/SMF、海缆。
- 与业界对比或记录声明：p21 罗列的现状数字（301.7 km 无中继、25.6 Tb/s/200.5 km、34–37 dBm）为他人/业界现状，页上未标出处。
- 推荐配图页：B-03 p3（100 km 前后向 OFDR 反射曲线，+90 dB 动态范围）；B-03 p17（长距 OFDR 看穿多盘 HCF 直到 >2000 km 接头）；B-03 p21（现状与观众投票）。

### 0920-pm-Su3-B-03-NokiaBellLabs-长光纤表征.pdf（第1–21页，同上讲的完整版）
- 讲者/机构：Nicolas Fontaine / Nokia Bell Labs | 题目：Characterization of Long Fibers | 类型：Workshop
- 方向归属（主/次）：1 相干/海缆/长途 / 次：6 光纤传感
- 核心主张：与上节相同；独有页为观众投票 1：在已安装 300 km 无中继 HCF 跨段上最难认证的属性？（选项含衰减及其均匀性、接头/互连损耗与回损、高阶模含量与多径干扰、气体吸收线与谱纹波、长期稳定性—污染/老化/微弯、"现有 SMF 测试方法可沿用"）；前提"无中段接入、无截断法、背散比 SMF 低 30–45 dB"[p20]。
- 关键数据：见上节，页码 [p3, p8, p9, p11, p14, p16, p17, p18, p20, p21]。p11–p13 是同一 100 km 曲线的逐步标注版（3 m/10 m/25 m FWHM）。
- 提到的公司/客户/产品/标准：Nokia Bell Labs、LOR-200 OTDR。
- 与业界对比或记录声明：无新增。
- 推荐配图页：p20（投票1：最难认证的属性选项）。

### 0920-pm-Su3-B-04-Adtran-无中继链路EDFA.pdf（第1–18页）
- 讲者/机构：Lutz Rapp / Adtran | 题目：How do HCFs impact amplifier design and economics in unrepeatered systems? | 类型：Workshop（邀请报告）
- 方向归属（主/次）：1 相干/海缆/长途 / 无
- 核心主张：
  1. 用 HCF 后，现有多种无中继链路配置可只用 EDFA 简化；很多情形可用为陆地系统设计的 EDFA[p14 总结页，看图核实]。
  2. HCF 中无明显拉曼放大，且难给 ROPA 供泵浦，因此无中继海缆中的拉曼/ROPA 复杂放大方案"不适用于 HCF"；但也未必需要[p8]。
  3. 经济影响：无中继海缆放大器目前是少数小公司的小众业务，HCF 引入后拉曼/ROPA 泵浦业务会消失，大部分链路可用陆地系统技术放大器、大型设备商份额上升；少数链路需极高功率放大器，同时更多链路可能适合无中继方案[p16，看图核实]。
- 关键数据：
  - 应用：ARCOS 加勒比环网 24 跨，其中 2 条中继链路 + 22 条无中继链路；两跨超过 1000 km 无法在无中间放大下跨越，需经电缆供能（成本高）；问题：能否用 HCF 不加中间放大跨过这两跨[p3，看图核实]。其他应用：连岛、festoon 网络、hut skipping（节能省成本，如中间站无空调）；距离常由应用决定 [p4，看图核实]。
  - 现有无中继升级路径 (1)–(7)：从"高功率 booster + 预放"到"同向拉曼 + 高阶 ROPA"，部分升级步骤仅带来约 +1~+2 dB 余量；(2)–(7) 标注"不适用于 HCF"（HCF 中拉曼增益不明显、ROPA 泵浦供电困难）（看图核实）[p8；p6]。
  - 传统无中继可承受衰减（SubOptic 2016，Rapp & Costa）：10G IM-DD 约 50–72 dB，40G/100G CP-QPSK 约 43–63 dB；400G 估计曲线更靠左（约 33–55 dB）；分为有/无 ROPA 两区[p7]。
  - 到达距离估计：SSMF/PSCF 0.2 dB/km（含余量）EDFA-only 约 250 km（10G NRZ）、约 220 km（100G CP-QPSK）、约 165 km（400G CP-QPSK）；加拉曼/ROPA 后 10G 最远约 370 km；HCF 0.08 dB/km（含余量）仅 EDFA 即可 400G 到约 410 km、100G 约 550 km、10G 约 640 km（均为读图估计）；多数无中继链路在 100–300 km [p10]。
  - 链路模型：OSNRreq = 58 dBm + Pout − αL − NF − 10·log(Nch)；OSNRreq 20 dB、预放 NF 4.5 dB、96 路。以放大器输出 30 dBm 为界，可达跨长：0.20 dB/km 为 218 km，0.10 dB/km 为 437 km，0.08 dB/km 为 546 km，0.05 dB/km 为 874 km；强调区分"光纤衰减"与"含余量衰减"[p11]。
  - 提高 EDFA 输出功率：反向泵浦 980 nm（300 mW 前向）时输出约 21.5–27.6 dBm（输入 0/10/17/20 dBm、反向泵浦至 950 mW）；改用 1480 nm 泵浦，450 mW 内即可达约 28 dBm（虚线，读图）[p12]。
  - 两级 EDFA 设计灵活性：最大泵浦 950 mW 时输出可到约 22 dBm；1733 mW 时到约 24 dBm，噪声系数约 4.2–7.5 dB；最大功率与最优 NF 之间可折中[p13]。
  - 效应：更高速率会推高所需放大器输出功率；掺镱共掺可提功率但可用带宽受限；hut skipping 等场景需设备侧大幅降本（线缆成本不降）[p14，看图核实]。
  - 有中继海缆：可用电功率受限，HCF 因低衰减可少用中继器或提升每跨光功率、提高可达信息速率[p15，看图核实]。
  - 听众题：未来是否仍需专用无中继海缆放大器？商用设备未来需要提供的最大放大器输出功率？[p17、p18]
- 提到的公司/客户/产品/标准：Adtran、ARCOS（加勒比环网）、EDFA/Raman/ROPA、SSMF/PSCF、SubOptic 2016 论文。
- 与业界对比或记录声明：无 record 声明。
- 推荐配图页：p10（SSMF 与 HCF 在 10/100/400G 下的到达距离条形对比）；p11（OSNR 链路模型与不同衰减下的可达跨长）；p8（无中继升级方案表与"不适用于 HCF"）。

### 0920-pm-Su3-B-05-Lightera-铋掺放大器高功率.pdf（第1–11页）
- 讲者/机构：Vitaly Mikhailov / Lightera（Furukawa Electric 旗下）| 题目：Amplifiers for Hollow Core Fiber Transmission | 类型：Workshop（邀请报告）
- 方向归属（主/次）：1 相干/海缆/长途（HCF 多波段放大）/ 次：3 Scale-out 光源/器件（宽带高功率放大器）
- 核心主张：
  1. HCF 因低非线性可承受高功率，高功率放大器有助于拉长跨距；时延重要；初期 HCF 部署成本较高；多波段传输可增容[p2]。
  2. 各传输波段均已有放大器：C 波段高功率低时延且兼容可插拔；S+C 中功率高时延；O-E-S 高功率高时延；T 波段极高功率低时延[p11]。
  3. 开放问题：能否利用 HCF 的气体/水汽吸收线？能否缩短铋掺光纤（BDF）长度？HCF 总功率极限（非线性、功率承受、接头）是多少？[p11]
- 关键数据：
  - 波段划分（吸收谱引自 Microsoft Azure/Ben Puttnam）：C 波段 EDFA 约 5 THz，L 约 6 THz，S 波段 T/BDFA 约 7 THz，O 波段 BDFA 约 17 THz，T 波段 YDFA 约 14 THz [p11]。
  - 低时延高功率 EDFA：1530–1563 nm；2 个 976 nm 泵浦各 0.9 W + 共享 10 W 1480 nm 泵浦；总长 <2.7 m（受无源器件限制），掺铒光纤 1.7 m（三段 EDF，含 GFF）[p4]。
  - 铒-铋混合 S+C 放大器：4.5 m EDF + 250 m BDF（Ge 共掺），泵浦 980/1350/2×1390 nm 各 250 mW，1490–1560 nm，BDF 长度带来较高时延（看图核实）；输出功率 23 dBm，增益平坦度 3.6 dB，NF 7~4 dB；输入 0/-3/-6/-9 dBm/band 对应每路 -11.5/-14.5/-17.5/-20.5 dBm，增益约 17–27 dB [p5–p6]。
  - 铋 E-S 放大器（两级，1 W + 2.8 W 泵浦）：1400–1470 nm 增益带宽；输出 29.4 dBm，NF 7~4 dB，功率转换效率 20%；表：输入 0 dBm 时增益 23/26/29.4 dB、PCE 20/18.1/22.9%；输入 -20 dBm 时增益 35.7/44/47.6 dB、PCE 3.7/11.4/15% [p7]。
  - 铋 O 波段高功率放大器：250 m 磷共掺 BDF，915 nm 泵浦的 30 m 镱光纤转换级；1265–1365 nm；输出 29–32 dBm，NF 7~4 dB，PCE 10–20%；泵浦 15 W 时最佳波长输出约 1.4 W（读图）[p8]。
  - 镱 T 波段放大器：kW 级输出，泵浦吸收高，最高 85% 转换效率，图中约 6000 W 泵浦对应约 5000 W 信号；"尚未用于数据传输"；1050–1065 nm 谱（引 R. Apperecido et al., Advanced Photonics Congress 2026）[p9–p10]。
- 提到的公司/客户/产品/标准：Lightera、Furukawa Electric、Microsoft Azure/Ben Puttnam（吸收谱）、EDFA/BDFA/TDFA/YDFA。
- 与业界对比或记录声明：页 p3 汇总各类 S 波段掺杂光纤放大器文献带宽（Tm、Er、Bi、Nd、Pr 等），未声明 SOTA。
- 推荐配图页：p11（HCF 吸收谱上叠加各波段放大器覆盖 + 结论要点）；p7（铋 E-S 放大器结构与增益/PCE 表）。

### 0920-pm-Su3-B-06-UCL-新型放大器能效.pdf（第1–14页）
- 讲者/机构：Ronit Sohanpal / UCL Optical Networks Group | 题目：Energy efficiency implications in hollow-core fibre links | 类型：Workshop（邀请报告）
- 方向归属（主/次）：1 相干/海缆/长途（超宽带+能效）/ 无
- 核心主张：
  1. 除吞吐和距离外，需以能效衡量：(1) HCF 中的超宽带放大；(2) HCF 链路最优入纤功率[p3]。
  2. 在 UWB 系统中放大器是能耗最关键的元件；超长跨 HCF 减少中继器，因此 UWB 在 HCF 上比 SMF 更节能，且中继减少对 UWB 的收益大于对 C 波段的收益[p9–p10]。
  3. 无中继 HCF 中，吞吐量最大化的入纤功率并非能效最优：略降功率可显著降低比特能耗而吞吐损失极小[p11]。
- 关键数据：
  - 放大器电光效率（页上给出）：C-EDFA 5%，L-EDFA 3.7%，S-TDFA 1.2%，E-BDFA 1.3%（Pin=4 dBm）/1.2%（0 dBm），O-BDFA 0.7%（4 dBm）/0.4%（0 dBm）/0.2%（-4 dBm）；BDFA 效率依赖输入功率。建模：积分 GN 模型，O/E/S/C/L 全波段，吞吐最大化，光纤 A（已部署）与光纤 B（低损耗），140 GBd 信道、150 GHz 栅格 [p5]。
  - 3×80 km（240 km）：每比特能耗 Eb 与吞吐关系；C 波段约 50 Tbps、约 0.1 pJ/bit（光纤 A）；OESCL 全带光纤 A 约 365 Tbps、光纤 B 约 410 Tbps；O 波段 Eb 比 C 波段高近一个数量级；标注"O 波段每比特能耗降低 4 倍"（光纤 A 到光纤 B）[p6、p7]。
  - 13×80 km（1040 km）含收发器（24 W）：光纤 B，Eb≈(P放大器+P收发器)/T≈P收发器/T（跨数少时）；CL 约 100 Tbps 对比 OESCL 约 300 Tbps：吞吐 2.98 倍，Eb 增加 48% [p8]。
  - 10 跨（1040 km）：C 波段放大器约 15 W / 总约 800 W，放大器占 1.85%；O 波段放大器约 383 W / 总约 2783 W，占 13.8%；OESCL 放大器约 818 W、收发器约 7300 W，放大器占 11.6% [p9–p10]。
  - 200 km 无中继 C 波段 HCF（29 路、140 GBd，0.05 dB/km，非线性系数 5×10^-3 W^-1km^-1，收发器 SNR 20 dB）：吞吐在约 -10~30 dBm 每路入纤区间平坦于约 52–53 Tbps（低于收发器限 T 约 54 Tbps）；Eb 与 1/T 成比例，插图标注从吞吐最优点 P_opt^T 移到能效最优点 P_opt^Eb 时吞吐 -0.27%、每比特能耗 -6.60%（看图核实）[p11]。
  - 听众题：放大器最需要的属性（能效/宽带/高输出功率）；从 SMF 换到数百 km HCF 期望总功耗降低多少 %（Menti 7771 0403）[p12、p13]。
- 提到的公司/客户/产品/标准：UCL、EDFA/TDFA/BDFA、GN 模型、Menti。
- 与业界对比或记录声明：无 record 声明。
- 推荐配图页：p10（10 跨下 C/O/OESCL 放大器功耗占比）；p8（含收发器功耗后 Eb 的变化，2.98× 与 +48%）；p11（200 km 无中继 HCF 吞吐-能效随入纤功率）。

## 本批小结
1. HCF 长途/海缆产业化已从"能不能做"转向"哪种芯径合适"：Linfiber 与 YOFC 都给出大芯（0.032–0.052 dB/km，弯曲敏感、密度低）与中芯（约 0.06–0.1 dB/km，可量产、可布缆）的折中，并都倾向中芯为务实路线（来自：YOFC p11–p13、Linfiber p21–p24、B-02 p6）。
2. 气体线吸收（CO2、水汽）是 C+L 波段 HCF 长距传输的主要残余障碍，出现"光纤层 + 系统层"两条路线：拉丝塔在线去 CO2、后处理（YOFC 383 km 拼接链路在 C+L 无气体线，Linfiber 中位数 <0.039 dB/km），以及自适应波长/波特率绕线（Linfiber 12,113 km 环路 24.8 Tb/s，300.4 Pb/s·km）（来自：YOFC p14，Linfiber p26–p31）。
3. 无中继 HCF 的价值主张：多数无中继链路 100–300 km，HCF（0.08 dB/km 含余量）仅 EDFA 就可覆盖 400G 到约 410 km，Raman/ROPA 变得既不适用也不必要；放大器产业格局因此变化（来自：Adtran p8、p10、p16）。
4. 放大器端是多波段 HCF 的能量与功率瓶颈：Lightera 展示 O/E-S 波段铋掺放大器已达 29–32 dBm，但带来高时延；UCL 建模指出 O 波段放大器占 10 跨系统总功耗的 13.8%（C 波段 1.85%），因此超长 HCF 跨距减少中继对超宽带更有利（来自：Lightera p7–p8、p11，UCL p5、p9–p10）。
5. 测量与监测被明确提为新瓶颈：HCF 背向散射比 SMF 低 30–45 dB，无中段接入，OFDR 在 HCF 上可看穿约 5–6 盘、最佳单盘 500 km，300 km 跨仅 15 dB 光纤损耗，"限制可能是测得了什么，而不是传得了多远"；同时 Nokia 提出用反射器/环回监测长跨（来自：Nokia B-01 p41–p50，B-03 p16–p21）。
6. 各家共识与分歧：损耗与 IMI 已不是主要问题，剩余为线缆密度/弯曲敏感性、长期可靠性与良率成本；听众投票中"成本"位居首位（OCR）（来自：YOFC p16，Linfiber p35，Menti 结果页）。
