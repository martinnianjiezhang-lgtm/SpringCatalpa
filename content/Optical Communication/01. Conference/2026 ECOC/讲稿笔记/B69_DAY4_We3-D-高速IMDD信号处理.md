---
title: "B69 · DAY4 · We3-D-高速IMDD信号处理"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We3-D4-382-NokiaBellLabs-峰值受限线性预均衡.pdf（第1–16页；p10为p9重复）
- 讲者/机构：W. Lanneer 等 / Nokia Bell Labs | 题目：DAC-aware peak-amplitude-constrained (L1-constrained) MMSE linear transmit pre-equalization（页面未见完整英文原题，据内容概括；场次 We3-D4） | 类型：学术论文
- 方向归属（主/次）：主 3（Scale-out/电芯片、DAC、IMDD DSP）；次 5（100G PON 原型）
- 核心主张：
  1. 传统预均衡直接复用 RX 滤波器，会抬高信号峰值（PAPR），需缩放/削波，带来 ER 与 SNR 代价及非线性失真（p3–p4）。
  2. 提出在滤波器设计阶段就把 DAC 峰值幅度约束纳入 MMSE（迭代加权岭回归近似 L1 最小化），得到稀疏滤波器（p5–p7）。
  3. 结论：提升 SNR、ER、PAPR 与链路损耗，压缩滤波器降低复杂度，支持实验室标定与在线自适应（p16）。
- 关键数据：
  - 仿真（线性 AWGN + DFE，峰值约束 P=1，PAM2 SNR=20 dB，PAM4 SNR=26 dB，二阶 Bessel 带宽扫描）：相比 L1 缩放 RX-MMSE，PAPR 与显著抽头数均下降（PAPR 约 3–8 dB 对 7–10 dB，抽头约 4–8 对 12–16，读图近似）[p9]
  - 实验 PAM2、极强带宽受限，BER 2e-2 门限：损耗预算改善 4.3 dB；PAPR 由 7.4 降到 4 dB（L1优化 b=[1,0.3] 为 4.3，b=[1] 为 3.8）；ER 由 3.3 dB 升到 10.3 dB（图中 b=[1] 为 10、b=[1,0.3] 为 11）；显著抽头由 11 降到 3–4（频域 RX-MMSE 为 84）；接收端为 AI 启发的 MLSE [p13]
  - 实验 PAM4、带宽受限较轻，FFE-DFE 接收，BER 2e-2：损耗预算改善 0.6 dB；PAPR 4.6 dB（L1缩放 RX-MMSE 5.6，频域 8.7，无预均衡 2.5）；ER 7.2 dB（无预均衡 11，L1缩放 6，频域 4.4）；抽头 3（对 6 与 23）[p14]
  - PAM4 下所提预均衡缩小 FFE/DFE 与先进 MLSE 接收机之间的差距（ROP 约 -23～-15 dBm 范围）[p15]
  - 实验平台：100G PON 原型，100 GSa/s 8-bit DAC，PAM2/PAM4，35 GHz EML-SOA 发射机，1342 nm，OLT 发射（Pi-launch）9 dBm，预放大 PIN-TIA 接收，103 GS/s ADC，背靠背与 15 km 光纤（36 ps/nm）验证 [p11]
- 提到的公司/客户/产品/标准：Nokia Bell Labs；100G PON；EML-SOA；PIN-TIA
- 与业界对比或记录声明（SOTA/首次/record）：仅与 prior art 预均衡（L1缩放 RX-MMSE、频域 RX-MMSE）对比，无 record 声明 [p13][p14]
- 推荐配图页：p13（PAM2 BER 曲线与 PAPR/ER/抽头条形图，含 4.3 dB 改善）；p14（PAM4 对应结果）

### 0923-We3-D5-上海交大-高电谱效率直接检测.pdf（第1–25页；p7、13、14、16、18为重复）
- 讲者/机构：Yikai Su, Jingchi Li（上海交通大学）、Haoshuo Chen（Nokia Bell Labs）、William Shieh（西湖大学） | 题目：Direct Detection with High Electrical Spectral Efficiency | 类型：邀请报告
- 方向归属（主/次）：主 1（高波特率器件/相干替代接收，硅光 DD）；次 3（短距/DCI 互连接收机）
- 核心主张：
  1. 互连带宽增速远落后于算力，IMDD 仅恢复强度、电谱效率（ESE）受限；相干接收机 ESE 翻倍但需窄线宽 LO（约占光器件成本 40%、CoRx 功耗约 20%）（p3–p5）。
  2. 提出多种具备场恢复能力、免 LO 的 DD 接收机（硅光 Modified CADD、4-D DP-CADD、Si3N4 滤波器 LO-free homodyne、最简相位分集接收机）以提高 ESE。
  3. 结论：常规 DD 净 ESE 约 4 b/s/Hz；最简相位分集 8.76；SiP DP-CADD 偏振复用达 11.83 b/s/Hz（p25）。
- 关键数据：
  - 背景：硬件 FLOPS 约 90000x/20年（3.1x/2年），DRAM 与互连带宽约 30x/20年（1.4x/2年）；IMDD 实验例（OFC26 Th4A.2）226 Gbaud/113 GHz PS-PAM16，B2B，线速/净速 768/536 Gb/s，ESE 6.8/4.7 b/s/Hz [p3][p4]
  - SiP Modified CADD：延时 25 ps 与 50 ps；片上 PD 6-dB 带宽 38 GHz（-2 V 偏压）；尺寸约 2.3 mm×0.4 mm [p9]
  - 300 Gb/s OFDM 32-QAM，80 km SMF，电带宽 31.5 GHz，保护带 1.5 GHz，80 GSa/s DSO；最优 PAPR 11 dB、CSPR 15 dB；24% SD-FEC 下净速率 242 Gb/s，净 ESE 7.7 b/s/Hz（-9 dBm ROP 星座图） [p10][p11]
  - 4-D DP-CADD：528 Gb/s OFDM 16-QAM，80 km SMF，线 ESE 14.67 b/s/Hz；延时偏差 ±4 ps 内无明显代价；净容量 426 Gb/s，净 ESE 11.8 b/s/Hz（24% SD-FEC） [p15]
  - Si3N4 滤波器 LO-free homodyne：单偏振 600 Gb/s OFDM 16-QAM，80 km，净速率 480 Gb/s；最优 CSPR 9 dB（滤波器插损 4.5 dB + BPD 后残余失真）；25% SD-FEC [p19]
  - 多波长：6 波（1556–1561 nm）560 Gb/s 16-QAM 线速，80 km；4 波（约 1535 与 1565 nm 附近）448 Gb/s 16-QAM，80 km（数值取自 OCR，未核图）[p20]
  - 最简相位分集接收机：仿真 300 GBaud 双 SSB 16-QAM，近零保护带（-0.5～0.5 Hz，OCR原样）；最优 CSPR 3 dB（30 dB OSNR 下、相移 45°）；较带 CSPR 代价的相干约有 1 dB OSNR 代价，归因于残余 SSBI [p22]
  - 理论 ESE 上限：ESE=2log2(1+OSNR·Bref/(B·CSPR…))，Bref=12.5 GHz，OSNR 足够时归一化 ESE 上限趋近 100%（公式 OCR 不清） [p23]
  - 实验：46 GBaud 双 SSB 64-QAM，保护带 -3～3 GHz，100 GSa/s DAC，160 GSa/s DSO，波形整形器构造传输函数；40 km 净 228.85 Gb/s；20% FEC 阈值 2.4×10^-2、25% FEC 4×10^-2；最优 CSPR 约 12 dB（图读） [p24]
  - 汇总表（80 km，净 ESE）：SiP LO-free homodyne 150 GBaud 16-QAM 480 Gb/s 6.32；SiP Modified CADD 60 GBaud 32-QAM 242 Gb/s 7.68；最简相位分集 46 GBaud 64-QAM 229 Gb/s 8.76；SiP DP-CADD 66×2 GBaud 16-QAM 426 Gb/s 11.83 [p25]
- 提到的公司/客户/产品/标准：Cisco（400G ZR CoRx 功耗拆分，OFC 2023）；Lumentum 类窄线宽激光作为 LO 成本项（页面仅写 Luster/OCR不清，不确定）；Bell Labs Stokes 接收机（Dong 2016、Stern OFC 2024）；McGill KK/RCC；Westlake；LightCounting 速率演进图；Si3N4 平台
- 与业界对比或记录声明（SOTA/首次/record）：DP-CADD "Record 426 Gb/s net capacity and 11.8 b/s/Hz net ESE"、"First four-dimensional integrated DP-DD receiver"（源自 ECOC 2023 PDP Th.C.1.9）[p15]；最简相位分集 "Highest net ESE/POL of 8.76 b/s/Hz for >40-km DD transmission" 与 "Highest 2^ESE×Reach/POL for DD transmission" [p24]；常规 DD 约 4 b/s/Hz 作对照 [p25]
- 推荐配图页：p25（四种接收机方案 ESE 汇总表）；p15（DP-CADD 结果与延时容限）；p24（最简相位分集实验装置与 CSPR/ROP 曲线）

## 本批小结
1. IMDD 的瓶颈正在从器件带宽转向"带宽受限下的信号处理/接收结构"：Nokia 在 DAC 峰值约束下做稀疏预均衡（PAM2 带宽极限时改善 4.3 dB），SJTU 则通过场恢复 DD 接收机把净 ESE 由约 4 提到 8.76–11.83 b/s/Hz（Nokia Bell Labs 预均衡、SJTU DD 接收机两篇）。
2. 两篇都强调"降复杂度"：Nokia 显著抽头由 11 降到 3–4（对频域法为 84 降到 3–4）；SJTU 免 LO、硅光集成，减少窄线宽 LO 的成本与功耗（40% 光器件成本、约 20% CoRx 功耗）（两篇）。
3. 免 LO 场恢复（CADD、Si3N4 滤波器 homodyne、最简相位分集）成为介于 IMDD 与相干之间的中间路线，实验多停留在 40–80 km、OFDM/离线 DSP，距 400G/λ 以上商用仍需验证（SJTU）。
4. 两篇都以离线 DSP 与 BER 阈值（2e-2、24–25% SD-FEC）判定，与 PON/短距 IMDD 的实时实现之间存在差距（Nokia 100G PON 原型、SJTU）。
