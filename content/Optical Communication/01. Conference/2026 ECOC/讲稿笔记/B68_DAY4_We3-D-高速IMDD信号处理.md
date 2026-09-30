---
title: "B68 · DAY4 · We3-D-高速IMDD信号处理"
tags:
  - ECOC2026
  - DAY4
---

# B68 We3-D 高速IMDD信号处理 看图笔记

### 0923-We3-D1-1343-南安普顿ORC-PAM12调制编码.pdf
- 讲者/机构：Suttikarn Wantee（共同作者 Bottrill、Othman、McCulloch、Hao Liu、Petropoulos），Optoelectronics Research Centre, University of Southampton | 题目：PAM12 Modulation Coding Options Enabling High-Speed IM/DD Transmission in Bandwidth-Limited Systems | 类型：学术论文
- 方向归属（主/次）：主 3（Scale-out 短距 IM/DD 调制编码）；次 1（带宽受限器件下的调制/DSP）
- 核心主张：
  1. 器件（MZM/PD）带宽受限时，用分数比特的 2D-PAM12（两个符号联合映射，7 bit/2 符号=3.5 bit/符号）来折中带宽占用与所需 SNR。
  2. 三种 2D 几何（Cross / Double-Square(DSQ) / Scatter(SC)）各有取舍；SC-PAM12 因全格雷编码表现最好，Cross 的 SER 最低但 BER 不是最优。
  3. 讲者结论：全格雷编码是 SC-PAM12 增益的主要来源，是 intra-DC 高速高阶 PAM 互连的实用方案。
- 关键数据：
  - 场景：intra-DC，链路<2 km，QSFP/OSFP，4 或 8 并行通道 [p3]
  - SC 由 128-QAM 派生：12x12 网格取 128 点，16 点不用；7 bit/两符号，3.5 bit/符号，两个符号时间交织做 IM/DD [p9]
  - 映射分析表：Double-Square 16x16，dmin 2.8284，Es 170，dmin²/Es 0.0471；Cross 12x12，dmin 2，Es 82，0.0488；Scatter 12x12，dmin 2，Es 96，0.0417 [p8]
  - 实验：58 GBaud 2D-PAM12（带宽 34.8 GHz），2 km SMF，AWG/DSO 均 256 GSa/s，MZM+EDFA，OBPF+VOA+PD，DSP 与均匀 M-PAM 相同 [p13]
  - SC-PAM12 的 GMI 为 3.45 bit/symbol，信息速率 >200 Gbit/s（58 GBaud，2 km SMF）[p14]
  - DSQ 因需要 16 个幅度电平，更大符号距离的收益被抵消，2 km 时 SNR 在 ROP 约 0 dBm 处明显低于另两种（约 16 vs 约 20 dB，图读数）[p15]
  - BER 图标出 20% HD-FEC（约 1.5e-2）与 6.25% HD-FEC（约 4.5e-3）线；ROP 6 dBm 时 Cross 约 5.5e-3、SC 约 4.5e-3（触及 6.25% HD-FEC），DSQ 约 2.5e-2 未过 20% 门限；Cross 映射 SER 最低，但因非全格雷编码 BER 不是最好（看图核实，读图估计）[p16]
  - 香农曲线：PAM12 饱和约 3.5 bit/s/Hz，需 SNR 约 27 dB 才达99%极限（图读数）[p6]
- 提到的公司/客户/产品/标准：无企业产品；引用 T. Prinz ISTC 2021（PAM-6 编码调制）、F. Villenas ECOC 2025（5-bit 2D 符号调制）[p11]；QSFP/OSFP
- 与业界对比或记录声明：未声明 SOTA/record；结论为 >200 Gbit/s 信息速率、3.45 bit/symbol GMI [p14]
- 推荐配图页：p15（SNR-ROP 与 GMI-SNR 曲线并列三种映射星座，含 3.45 bit/symbol 结论）；p8（三种映射的误差概率星座图与 dmin/Es 表）

### 0923-We3-D2-苏黎世联邦理工-等离激元光学DAC.pdf
- 讲者/机构：David Moor（共同作者含 Hess、Rieben，ETH Zurich IEF；Marvell（原 Polariton Technologies）；Univ. of Patras；Technion；Juerg Leuthold） | 题目：Resonant Plasmonic Optical DAC for Low-Power IM/DD Links | 类型：学术论文
- 方向归属（主/次）：主 3（Scale-out 调制器/光 DAC）；次 1（高波特率器件）
- 核心主张：
  1. 继 LDO/LPO 去掉冗余 DSP、无驱动（driverless）去掉驱动放大器之后，下一个可"移除"的部件是 DAC，用光学 DAC（oDAC）在光域做幅度复用。
  2. 串联双 plasmonic 微环（RRM）oDAC 比并联 MZM oDAC 的 AIR 高 18%。
  3. 结论页：plasmonic oDAC 简单、高带宽、高效；节能来自 oDAC 加简单 DSP；>300 Gb/s IM/DD。
- 关键数据：
  - DAC 占数字电路功耗 22%（引 Cheng OECC 2018）[p2]
  - 并联 MZM oDAC：PAM4，277 Gb/s AIR，需非线性 DSP，MZM 损耗约 10 dB；串联 RRM oDAC：PAM4/PAM8，328 Gb/s AIR（+18%），3-Tap LMS，RRM 损耗约 2x2 dB [p4]
  - AIR-波特率曲线：PAM8 RRM 峰值约 150–170 GBd（图读数），PAM4 MZM 峰值约 277 Gb/s [p4]
  - Plasmonic RRM：插损 1.2 dB，带宽 >110 GHz，热稳定性比硅 MRM 好 28 倍，C 波段与 O 波段均 400 Gb/s，AIR 461 Gb/s（均引自 Blatter ECOC 2024、Eppenberger Nat. Photon. 2023、Hess OFC 2026）[p5]
  - 工作点：两个 RRM 同时优化 OMA，保持 1:2 调制比，FOM=最小光电平间隔；FOM 在 1:2 调制比且传输最佳时最大，图中给出 I–IV 四个工作点的眼图 [p9]
  - 数据传输：336 Gb/s PAM4（3-Tap LMS 低复杂度 DSP）；延伸到 PAM8；非线性 DSP 下 360 Gb/s PAM4（比 MZM 好 10%）；NGMI 图中 25% SD-FEC 阈值线约在 0.81（图读数）[p10]
- 提到的公司/客户/产品/标准：Marvell（Polariton）、Lightwave Logic（致谢）；Horizon 项目 PROTEUS-6G、FLEX-SCALE、ALLEGRO；LDO/LPO；引 E. S. Chou OFC 2024（100G/200G 每通道线性驱动光学）[p2]
- 与业界对比或记录声明：与并联 MZM oDAC 对比 AIR +18%，非线性 DSP 下比 MZM 高 10%（360 Gb/s PAM4）[p4, p10]；未用 record 一词
- 推荐配图页：p4（串联 RRM 与并联 MZM oDAC 的 AIR-波特率曲线与眼图对比）；p2（LDO/LPO/driverless/oDAC 在收发链路中的位置与 DAC 22% 功耗饼图）

### 0923-We3-D3-KIT-光电任意波形生成.pdf
- 讲者/机构：Daniel Drayss、Lennart Schmitz（共同一作，Christian Koos 组）；KIT IPQ、Teragear GmbH、HyperLight、Nokia Bell Labs | 题目：Photonic-Electronic Arbitrary-Waveform Generation Enabling 276 GBd Electrical and 260 GBd Optical PAM4 Signaling | 类型：学术论文
- 方向归属（主/次）：主 1（高波特率器件/信号发生）；次 3（Scale-out 高波特率 IM/DD、TFLN 调制器）
- 核心主张：
  1. 光电任意波形发生器（PE-AWG）把同轴电缆传输问题移到光纤：光纤传光信号，近 DUT 处光电前端（OE front-end）转为电信号。
  2. 电学背靠背可达 276 GBd PAM4；光学 IM/DD 可达 260 GBd（TFLN-MZM）。
  3. 通过 Teragear GmbH 商业化，展位 1268。
- 关键数据：
  - 同轴电缆 30 cm、145 GHz：衰减约 6.5 dB（图读数），讲者称超过 75% 功率损失在电缆中 [p3]
  - 原理：光频梳→解复用出 f1/f2，f1 上 IQ 调制器由 AWG（带宽 B）驱动，f2 作"本振"，经 180° 光混合器和 OE 前端，得到 2B 电带宽（"quadrature multiplexing"）；PE-ADC 反向使用，ADC 带宽只需 B/2 [p4, p5（两页分别对应连拍 p30、p31）]
  - 系统：31 GHz 相位调制器产生梳线，f1-f2=62 GHz，与 AWG 用 10 MHz 同步；带预加重，输出频谱宽 138 GHz [p8]
  - OE 前端频响：校准后的 PE-AWG→PE-ADC 到 140 GHz 平坦；PE-AWG→示波器（113 GHz）在约 113 GHz 陡降；未校准时约 100 GHz 处约 -10 dB 且有波动 [p10]
  - 电学背靠背：224 GBd PAM4（OSC）BER 8.5x10^-4；224 GBd PAM8（OSC）BER 1.5x10^-2；276 GBd PAM4（PE-ADC，140 GHz）BER 3.4x10^-3；SNDR 图中 PE-AWG→OSC 在约 220 GBd 约 20 dB，PE-AWG→PE-ADC 在约 276 GBd 约 16 dB（图读数）[p12]
  - 光学 IM/DD：O 波段激光 1326 nm，MZM+PDFA+BP+PD+电放大+OSC；C 波段 1553 nm（MZM+PD+OSC）；232 GBd PAM4 眼图；BER-波特率图标注 20% SD-FEC 与 7% HD-FEC 线：PAM4 O 波段约在 232 GBd 触及 7% HD-FEC（约 4e-3），PAM4 C 波段约 225 GBd 时约 1e-3，PAM2 O 波段约 260 GBd 触及 7% HD-FEC（读图估计，看图核实）[p13]
  - 总结：光学 260 GBd PAM4，BER 2.9x10^-2；电学 276 GBd PAM4，BER 3.4x10^-3；使用 HyperLight TFLN-MZM [p15]
- 提到的公司/客户/产品/标准：Teragear GmbH（商业化，booth 1268）、HyperLight（TFLN-MZM）、Nokia Bell Labs（合作者）、Keysight UXR 与 M8199B AWG（图例）、Anritsu 部件（照片）；引 Füllner Nat Commun 16, 8318 (2025)；Drayss LSA 14, 353 (2025)；Fang LSA 14, 241 (2025)；资助 ERC、EIC、DFG
- 与业界对比或记录声明：题目即声明 276 GBd 电学、260 GBd 光学 PAM4；未见 "record" 字样；OE 前端校准后 PE-AWG→PE-ADC 平坦至约 140 GHz，而 PE-AWG→113 GHz 示波器在 113 GHz 截止（看图核实）[p10]
- 推荐配图页：p8（PE-AWG 完整架构与频谱 A/B/C，138 GHz、276 GBd PAM4）；p12（电学背靠背 SNDR 与 224/276 GBd 眼图 BER）；p13（O/C 波段 IM/DD BER-波特率）

### 0923-We3-D-00-全场连拍.pdf 第40–约58页（We3-D4，Nokia Bell Labs，峰值受限线性预均衡）
- 由另一批处理，本批不展开。

### 0923-We3-D-00-全场连拍.pdf 第约59–80页（We3-D5，上海交大，高电谱效率直接检测/无LO同差接收）
- 由另一批处理，本批不展开。（连拍中 D1–D3 各页与上面三个单讲 PDF 重复，已用单讲 PDF 分析。）

## 本批小结
1. 带宽受限的高波特率 IM/DD 有三条互补路线：调制格式/编码（D1 的 2D-PAM12，58 GBaud 得到 >200 Gbit/s）、器件/架构（D2 的 plasmonic RRM oDAC，>300 Gb/s）、信号源/测试（D3 的 PE-AWG，276 GBd）。（D1、D2、D3）
2. "去掉一个部件以省功耗"成为主线：D2 把 LDO/LPO、driverless 之后的下一步定为去 DAC（DAC 占数字电路功耗 22%），并强调用 3-Tap LMS 这类低复杂度 DSP。（D2）
3. D2 与 D3 都把 TFLN 或 plasmonic 等高带宽调制器与 >200 GBd 符号率绑定；D2 的 RRM oDAC AIR 峰值出现在约 150–170 GBd 之后随符号率上升而下降（图读数），说明器件带宽仍是上限。（D2、D3）
4. 光电混合的思路在两篇中同时出现：D2 用光域幅度复用取代电 DAC，D3 用光频梳加光混合器合成 2B 带宽的电波形，避开同轴电缆的高频损耗（145 GHz 处 30 cm 约 6.5 dB）。（D2、D3）
5. 编码细节影响明显：D1 显示 SER 最优的 Cross 映射并非 BER 最优，全格雷编码的 SC-PAM12 才是 BER/GMI 最优，说明 IM/DD 高阶调制的设计应以 BER 或 GMI 为目标。（D1）
6. D3 已有商业化路径（Teragear 展位 1268），高波特率测试仪器正从实验室概念走向产品。（D3）
