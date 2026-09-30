---
title: "B28 · DAY2 · Mo3-G-海底与无中继系统"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo3-G1-Meta-超petabit海缆的技术与挑战.pdf
- 讲者/机构：Pascal Pecci、Elizabeth Rivera Hartling、Matthew Mitchell / Meta | 题目：Technologies and Challenges for beyond Petabit Submarine Cable | 类型：邀请报告
- 方向归属（主/次）：主 1（相干/海缆/长途）；次 4（无，仅海缆供电/多芯光纤，归 1）
- 核心主张：
  1. 电力（PFE 电压与线缆 DCR）是海缆容量上限的主要瓶颈；24FP 跨大西洋（TA）距离下已接近技术极限，约 0.5 Pbps。
  2. 1 Pbps@TA 需 “48FP 等效”方案（48FP / 24FP-2C 双芯 / 24FP-C+L）+ 18 kV PFE + DCR 约 1 ohm/km；2 Pbps 在现有供电条件下“不可能”。
  3. 超 1 Pbps 需光学（多芯/多带/空芯光纤）与电学（中间落地、供电浮标、“一个 PFE 对应一个中继器”、分支单元 BU）联合创新。
- 关键数据：
  - 24FP 约 550 Tbps 为当前技术上限，Anjana 24FP、Amitié 16FP、Marea 8FP（图上读数，约值）；1 Pbps@TA 为目标线 [p3]
  - Project Waterworth：50,000 km、5 大洲，全程 24FP [p3]
  - 18 kV PFE 下容量随距离下降；13,000 km 处使用中间供电可提升约 +60%，约 17+ Tbps/FP [p5]
  - 无中间供电时 48FP 相对 24FP 容量比随距离下降，约 11,000 km 处与 24FP 容量相同（“Useless to go to 48FP”）；结论“超过 8 kkm 需中间供电” [p5]
  - 1 Pbps@TA：DCR 由 1.7 降到 1.0 ohm/km，中继器压降 120 V；线缆部分 41%、中继器部分 59%；18 kV PFE 下 1 ohm/km 为 1 Pbps 线缆的必要最大值 [p7]
  - 2 Pbps：中继器压降 240 V，中继器部分占 PFE 的 109%；18 kV 与 21 kV PFE 均不足，“即使 PFE 与线缆均改进，TA 距离上 2 Pbps 不可能” [p7]
  - 48FP 等效方案对比：48FP 需线缆外径 17 mm -> >20 mm，管径 ~3 mm -> ~4.2 mm（x1.4）；24FP-2C 衰减 <0.150 -> 0.153 dB/km，需 FIFO；24FP-C+L 需 MUX/DMUX 与 L 带新 SLTE [p9]
  - 1 Pbps 参数表：18 kV PFE，线缆 17 mm 到 >20 mm，DCR ~1 ohm/km，光纤 200–250 um 外径、110 um2 有效面积，48AP，电流 ~1 A，~80 个中继器，~1000 Tbps 对应 216 THz 即 4.5–5 b/s/Hz；电学预算：线缆 7 kV（~40%）+ 中继器 ~10 kV（55%）+ 余量（5%）[p9]
  - 4-core+C+L：约 8 Pbps@TA（未来），带宽约 1,728 THz，相当于 384 对光纤；48FP-4C-C+L 每中继器 1 kV，7,000 km 80 个中继器需约 90 kV PFE"不可能"；空芯光纤 0.15 -> 0.05 dB/km 可使中继器数减为 1/3，按 20 kV PFE 推算需 440 km 跨距、0.040 dB/km（看图核实）[p11, p14]
  - Petal（法国-美国，约 7,000 km，预计 2029 年投入运营）：首条跨洋 Pb 级海缆、首条大规模部署多芯光纤的海缆（24 FP / 96 芯，2 芯 MCF），与 NEC、Sumitomo Electric 合作，法国登陆由 Orange 支持；历代 Marea 8FP(2018)→Amitié 16FP(2023)→Anjana 24FP(2025)（看图核实）[p15]
- 提到的公司/客户/产品/标准：Meta、Project Waterworth、Petal、Marea/Amitié/Anjana、NEC、Sumitomo Electric、Orange、OCI（Open Cable Interface）、PFE、BU、Apollo generators、供电浮标（25 kW）
- 与业界对比或记录声明（SOTA/首次/record）：Petal 称“首条在跨洋距离交付 petabit 容量的海缆、首个大规模使用多芯光纤” [p15]
- 推荐配图页：p7（电压-距离图：1 Pbps 与 2 Pbps 的 PFE 限制）；p9（三种 48FP 等效方案对比与 1 Pbps 参数表）；p5（18 kV PFE 下容量-距离与 48FP/24FP 对比）

### 0921-Mo3-待定-ASN-无中继海缆系统.pdf
- 讲者/机构：A. Busson、M. Quenu、J. Courty、B. Renot、H. Bissessur / Alcatel Submarine Networks（ASN） | 题目：Few-Mode Fibre for Noise Transfer Mitigation in Co-Raman Amplified Unrepeatered Transmission（ECOC Mo3-G4） | 类型：学术论文
- 方向归属（主/次）：主 1（海缆/无中继）；次 无
- 核心主张：
  1. 无中继系统中同向拉曼放大会产生激光干扰噪声，恶化 FEC 余量；在发送端加一段发射光纤可缓解。
  2. 发射光纤长度低于 20 km 时 2-LP-FMF 最优；超过 20 km 时低损耗 SMF-150 um2 更有利。
  3. 30 路 1 Tb/s/λ DWDM 传输未受基模与高阶模耦合影响。
- 关键数据：
  - 参考：335 km 纯 PSCF（80 um2），跨段损耗 58.6 dB；加入发射光纤（SMF-150 um2 或 2-LP-FMF）后接 PSCF-80 um2，总链路 340 km，9 路 QPSK 平均 FEC 余量对比 [p4]
  - 图中 2-LP-FMF 在约 20 km 处 FEC 余量最高约 2.1 dB，跨段损耗 59.9/60.3 dB；SMF-150 在 35 km 处余量最大，跨段损耗 58.5 dB（图上读数，约值）[p4]
  - 实验：1 阶同向拉曼泵浦，4 个波长 1402–1455 nm，每波长最大 660 mW；9/30 路，QPSK / PCS-64QAM，53.5 GBd / 129.8 GBd，59.38 / 150 GHz，RRC 0.1；波段约 1530–1570 nm [p4]
  - 短发射光纤：200 km 纯 PSCF 跨段损耗 35.7 dB，30 路平均 FEC 余量 0.05 dB；加 1 km 2-LP-FMF 后损耗 36.7 dB，平均余量 0.12 dB（1 Tb/s/λ，PCS-64QAM，H=4.86 bit/symbol，129.8 GBd）[p6]
  - 稳定性：加 1 km 2-LP-FMF 无影响，σ ≈ 0.016 dB / 16 小时 [p7]
- 提到的公司/客户/产品/标准：Prysmian（借出 2-LP-FMF 并提供信息）、PSCF、SMF-150 um2、2-LP-FMF
- 与业界对比或记录声明（SOTA/首次/record）：无明确声明
- 推荐配图页：p4（FEC 余量-发射光纤长度曲线，2-LP-FMF 对比 SMF-150）；p6（30 路波长-FEC 余量对比）

### 0921-Mo3-待定-Ciena-无中继海缆系统.pdf
- 讲者/机构：M. F. C. Stephens 等 / Ciena（Meta 联合） | 题目：Algorithmically-Optimized Real-Time 18 Tb/s Throughput over a 16,608 km Trans-Pacific Subsea Link | 类型：学术论文
- 方向归属（主/次）：主 1（相干/海缆/长途/oDSP）；次 无
- 核心主张：
  1. 算法化的逐信道符号率/线路速率优化 + 连续可调波特率 modem，可在给定余量目标下最大化跨洋容量。
  2. 在 Bifrost 电缆 16,608 km 上实时传输 18 Tb/s，通量-距离积 298.9 Pb/s·km，称为实时海缆传输记录。
  3. 首次在跨洋距离实时 800 Gb/s 线路速率，频谱效率 4.57 b/s/Hz。
- 关键数据：
  - Bifrost：新加坡 - 美国 San Luis Obispo，16,608 km，12 对双向光纤，平均中继间距约 65 km，色散 328.6 s/m @1550 nm；每端使用 14 台 140–200 GBd 实时 muxponder（每台 2 路信道，最多 28 路），设备 2024 年 10 月起 GA [p2，看图核实]；结论：18 Tb/s、298.9 Pb/s·km 吞吐-距离纪录 [p6]
  - SNR_ASE（两个交错 50 GHz 间隔 ASE 梳）：蓝带（高频）8–8.5 dB，红带（低频）11–11.5 dB [p3]
  - 初始扫描：26 x 600 Gb/s，170 GBd，173 GHz 间隔，15.6 Tb/s；SNR 余量最大约 2.3 dB（191.49 THz），最小约 1 dB（194.27 THz）[p3]
  - 800 Gb/s：173 GBd，功率偏移 ≥1 dBm 时双向无误码（非线性不受限），4.57 b/s/Hz，与 25 x 600 Gb/s 邻道共传浸泡 12 小时；所有 28 路信道 SNR 余量 >0.17 dB、零 post-FEC 误码（看图核实）[p4, p6]
  - 优化信道方案：28 路，140–178 GBd，600/700 Gb/s，目标余量 0.2 dB，3 GHz 保护带，100GbE 客户侧颗粒度；预测 18 Tb/s，余量降到 0 dB 时可到 18.5 Tb/s [p5]
  - 实测：18 Tb/s 双向，每信道余量 >0.17 dB，8 小时稳定性测试全信道无误码；298.9 Pb/s·km [p5]
  - 算法收敛 <1 秒/候选方案，最大吞吐优化 <2 分钟，本地轻量运行无需云计算（看图核实）[p6]
- 提到的公司/客户/产品/标准：Ciena GeoMesh Extreme、Meta、Bifrost 海缆、WSS、100GbE
- 与业界对比或记录声明（SOTA/首次/record）：298.9 Pb/s·km 称实时海缆传输记录；首次跨太平洋距离实时 800 Gb/s [p5, p6]
- 推荐配图页：p5（优化后的信道方案与 18 Tb/s 实测余量对比）；p3（SNR_ASE 与 15.6 Tb/s 初测）

### 0921-Mo3-待定-Lightera-无中继海缆系统.pdf
- 讲者/机构：Benyuan Zhu、M. Stegmaier、T. Geisler、P. I. Borel、B. Palsdottir、P. Jenneve、H. Zhang / Lightera（Somerset NJ、Broendby 丹麦）、Cisco（Maynard、Holmdel），Furukawa Electric 标识 | 题目：Real-Time 52.8 Tb/s (26.4 Tb/s/core) Unrepeatered Transmission over 303.4 km of Uncoupled 2-core MCF（ECOC2026 paper Mo3-G6） | 类型：学术论文
- 方向归属（主/次）：主 1（海缆/无中继）；次 3（800G 可插拔）
- 核心主张：
  1. 125 um 包层非耦合 2 芯 MCF 可用商用可插拔模块，无需 MIMO DSP，是近期海缆 SDM 的现实选择。
  2. 单向与双向传输均无可测量的芯间串扰（XT）代价。
  3. 一根 2 芯 MCF 可作为完整的双向光纤对，每向 26.4 Tb/s。
- 关键数据：
  - SCUBA 2X：平均衰减 0.147 dB/km（1550 nm，两芯），同向 XT 平均 -59 dB/100 km，有效面积 110.1/110.5 µm²，MFD 11.6 µm，CD 22 ps/nm·km，PMD 0.06/0.07，λc 1454 nm，纤芯间距约 49 µm，125 µm 包层，兼容 G.654.B/D/E；本工作 303.4 km 2 芯 MCF 无中继实时 52.8 Tb/s（26.4 Tb/s/芯 = 33×800G 商用可插拔）[p2，看图核实]
  - 传输线：8 段 SCUBA 2X 熔接 FIFO，FIFO 损耗 0.35 dB、串扰 -67 dB/器件，总跨段损耗 core1 47.2 dB、core2 46.6 dB；助推器输出 31 dBm；一阶后向拉曼（泵浦 1429、1447、1465 nm）on-off 增益约 20.5 dB，总入纤信号功率约 27 dBm；最大 Q² 余量约 2.5 dB（1551.32 nm，core 2），无可测同向芯间 XT 代价（看图核实）[p4]
  - 信号：3 个商用可插拔 800 Gb/s 通道扫描 C 波段 33 路，138 GBd DP-16QAM-PCS，150 GHz 栅格，均匀发射功率；ASE 经 50 GHz 信道化 WSS 陷波形成 450 GHz 测量窗 [p4，看图核实]
  - 单向：平均 Q2 余量 core1 1.52/1.50 dB、core2 1.72/1.72 dB（无 XT/有 XT）；最小 Q2 余量 core1 0.52/0.49、core2 0.43/0.45；平均 OSNR core1 25.6、core2 26.4 dB/0.1nm [p5]
  - 双向（无 XT/有 XT）：平均 Q2 余量 core1 1.54/1.52、core2 1.59/1.57；最小 core1 0.32/0.31、core2 0.25/0.25 dB [p6]
  - 303.4 km 处反向 XT（−48.2 dB）高于同向 XT（−53.9 dB）；22.6/108.5/265 km 同向 −64.8/−58.7/−54.3 dB、反向 –/−80/−55.5 dB；双向传输时 DRA 会改变芯间 XT（看图核实）[p3]
- 提到的公司/客户/产品/标准：Lightera SCUBA 2X / SCUBA 110、Furukawa Electric、Cisco、FIFO、G.654.B/D/E、800G 可插拔
- 与业界对比或记录声明（SOTA/首次/record）：称记录实时 2 芯 MCF 无中继传输 52.8 Tb/s@303.4 km；对比：256 km 25.2 Tb/s/core（OFC 2025）、359 km 8.4 Tb/s/core（ECOC 2025）[p2, p6]
- 推荐配图页：p6（双向 Q2 余量对比与汇总表）；p5（单向 33 路 Q2 余量/OSNR 与汇总表）

### 0921-Mo3-待定-NTT-无中继海缆系统.pdf
- 讲者/机构：Kosuke Kimura、Shimpei Shimizu、Masanori Nakamura、Fukutaro Hamaoka、Takayuki Kobayashi、Yutaka Miyamoto / NTT Network Innovation Laboratories | 题目：Impact of RIN Transfer and Pump-Induced XPM on Coherent Transmission with Forward-Pumped Raman Amplification（Mo3-G5） | 类型：学术论文
- 方向归属（主/次）：主 1（相干/海缆/长途）；次 无
- 核心主张：
  1. 提出前向拉曼放大相干传输的 QoT 估计框架，计入泵浦 RIN 转移与泵浦诱导 XPM，并经实验验证。
  2. 将前向泵浦视为非线性干扰场，用 EGN 模型估算，并引入归一化四阶矩 μ 描述泵浦场非高斯性。
  3. 泵浦诱导 XPM 对 QoT 的影响大于泵浦到信号的 RIN 转移，而后者一直被视为前向拉曼的主要问题。
- 关键数据：
  - 实验：单信道环回，80 km G.652.D 光纤 x16 = 1280 km，PM-96Gbaud PCS-36QAM，1530 nm；泵浦：FBG-LD 相干泵浦 cPUMP 1423/1480/1505 nm（最大 24.4/24.6/23.3 dBm），非相干泵浦 iPUMP 1423 nm（22.6 dBm）；泵浦非高斯性以归一化四阶矩 µ 表征（1 为恒定、2 为高斯）[p5，看图核实]
  - 拟合 μ：1423 nm cPUMP 1.7，1480 nm cPUMP 1，1505 nm cPUMP 1，1423 nm iPUMP 2 [p6]
  - 1505 nm cPUMP 的 SNR 最差，1423 nm iPUMP 最好；SNR 纵轴范围 5–13 dB，1 dBm/ch 时最优 SNR 约 11–12 dB（图上读数，约值）；发射功率越高，SNR 峰值对应的拉曼增益越小（测试 1、3、5 dBm/ch）[p6]
  - 计算：3 dBm/ch 下，cPUMP 的 RIN 转移贡献可忽略、XPM 显著；iPUMP 因功率谱密度较低，XPM 代价较小 [p7]
- 提到的公司/客户/产品/标准：NTT、Furukawa Electric（提供 iPUMP）、EGN 模型、G.652.D
- 与业界对比或记录声明（SOTA/首次/record）：无记录声明
- 推荐配图页：p6（1280 km 实验 SNR-拉曼增益与计算对比，含 μ 值表）；p7（RIN 转移与 XPM 贡献分解）

## 本批小结
1. 供电是超 1 Pbps 跨洋海缆的第一瓶颈（Meta）：18 kV PFE 下 1 Pbps 要求 DCR 约 1 ohm/km；2 Pbps 在现有 PFE 条件下判定不可能，倒逼中间落地/供电浮标/多 PFE 方案。
2. 容量扩展路线集中在“48FP 等效”：多芯（2C/4C）、C+L、空芯光纤（Meta）；Lightera 的 2 芯 MCF 无中继实验和 Meta 的 Petal（多芯规模部署，2029）相互印证，MCF 正从实验走向工程。
3. 实时可插拔/商用设备进入超长海缆验证（Ciena、Lightera）：Bifrost 16,608 km 实时 18 Tb/s、800G 于 173 GBd 4.57 b/s/Hz；Lightera 用商用 800G 可插拔实现 303.4 km 52.8 Tb/s。
4. 逐信道波特率/线路速率的算法优化（Ciena）表明海缆容量竞争由“单波速率”转向“频谱利用与余量管理”，目标余量仅 0.2 dB。
5. 拉曼放大的噪声机理成为无中继/长跨段研究重点：ASN 用 FMF/大有效面积发射光纤抑制同向拉曼噪声，NTT 指出前向泵浦的 XPM 比 RIN 转移更重要，二者都指向泵浦设计（相干/非相干、发射光纤）对 QoT 的决定作用。
6. 双向 MCF 的芯间串扰在无中继长距离下最需关注（Lightera 测得 303.4 km 反向 XT 高于同向），与 Meta 强调的芯间/连接器（FIFO）损耗共同构成多芯海缆的工程约束。
