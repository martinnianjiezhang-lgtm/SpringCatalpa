---
title: "B33 · DAY2 · Mo5-F-机器学习与非线性补偿"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo5-F5-NTT-168-GBd-PCS-324QAM与样本域Volterra预失真.pdf
- 讲者/机构：Masanori Nakamura, Fukutaro Hamaoka 等, Etsushi Yamazaki（NTT Network Innovation Laboratories）| 题目：168-GBd PCS-324QAM Signal Transmission with 2.1-Tb/s Net Bitrate Using Sample-Domain Volterra Nonlinear Pre-distortion（Mo5-F5）| 类型：学术论文
- 方向归属（主/次）：主 [1 相干/高波特率器件/oDSP]；次 [3 调制器（TFLN IQM）]
- 核心主张：
  1. 高波特率下发射端非线性是限制信号质量的关键，样本域（sample-domain）Volterra 预失真比符号域更优，因线性滤波后驱动放大器的波形 PAPR 高、幅度连续。
  2. 样本域 VF 在 168-GBd 均匀 64QAM 上相对符号域 VF 获得 0.7 dB 峰值 SNR 增益。
  3. 168-GBd PCS-324QAM 实现净速率 2.18 Tb/s（背靠背）、80 km 传输后 2.10 Tb/s。
- 关键数据：
  - 均匀 64QAM 背靠背：无 VF 时 SNR 在 1.1 Vpp 达峰后随摆幅增大而下降；样本域 VF 持续提升，2.5 Vpp 时较无 VF 高 1 dB、较符号域 VF 高 0.7 dB [p6]
  - PCS-324QAM，熵 8.063 bit/2D-sym，背靠背净速率 2.18 Tb/s（图上 256QAM/324QAM/400QAM 三者净速率均在约 2.15–2.19 Tb/s 区间，324QAM 最高点）[p7]
  - 80 km 传输，同熵 8.063 bit/2D-sym，入纤功率 6 dBm 时净速率 2.10 Tb/s（扫描 2–10 dBm，10 dBm 时降至约 2.06）[p8]
  - 实验装置：薄膜铌酸锂（TFLN）IQM 由 256-GSa/s AWG（带宽约 80 GHz）直驱，摆幅远低于 2Vπ；光纤损耗 0.152 dB/km，Aeff 150 μm²；相干接收 BPD 带宽 90 GHz，DSO 256 GSa/s、带宽 113 GHz；信号带宽 168 GHz [p5]
- 提到的公司/客户/产品/标准：NTT；TFLN IQM；256-GSa/s AWG；引用 Volterra 原用于 RF 功放（Morgan 2006）、光发射端过采样 Volterra（Berenguer 2016）。
- 与业界对比或记录声明：Intro 图在"净速率–信息速率（bit/4D symbol）"平面上与 NTT 及他组先前工作（125–250 GBd 参考线，引文 [1]–[11]）对比，本工作 168 GBd PCS-324QAM 净速率 B2B 2.18 Tb/s、80 km 2.10 Tb/s，样本域 Volterra DPD 带来 0.7 dB 峰值 SNR 增益；未见"record"字样（看图核实）[p2]
- 推荐配图页：p2（净速率 vs 信息速率对比散点图，含 125–250 GBd 参考线）；p7（PCS-QAM 熵扫描与 2.18 Tb/s 星座）

### 0921-Mo5-F6-国立清华大学-物理感知的稀疏Volterra均衡剪枝.pdf
- 讲者/机构：Govind Sharan Yadav（讲者，博士后）, Cheng-Chieh Wang, Kai-Ming Feng（台湾国立清华大学 NTHU，Optical Fiber Communication Lab）| 题目：Physics-Aware Contribution-Guided Pruning for Low-Complexity Sparse Volterra Equalization in 100-Gb/s PAM4 IM/DD Links（Paper #867，Mo5-F6）| 类型：学术论文
- 方向归属（主/次）：主 [3 Scale-out 224G/oDSP（IM/DD 均衡）]；次 [1 oDSP]
- 核心主张：
  1. 完整 Volterra 均衡（VE）的非线性交互空间大部分冗余；传统按系数幅度剪枝（MP）不能反映项的真实贡献。
  2. 提出 PCG-VE：保留线性项，非线性项按"输出能量贡献 + 与线性残差的相关性"打分排序、取 Top-K，即"按贡献而非幅度剪枝"。
  3. 为下一代 IM/DD 链路提供硬件高效的非线性 DSP 路径；后续拟扩展到更高单通道速率和不同链路状态。
- 关键数据：
  - 实验：100-Gb/s PAM4 IM/DD，AWG + EA + MZM，EDFA，SMF 4.2 km，放大式 PD+TIA，实时示波器 + 离线 DSP；示例 ROP = -3 dBm，LEQ 与 VE 后眼图 [p12]
  - ROP 区间分析：-10 至 -7 dBm 噪声受限；-5 至 -3 dBm VE 有用区间；-3 至 -1 dBm EO 非线性增强（页面文字）[p13]
  - 稀疏度：剪掉 92% 系数无 BER 代价（几乎等于全 VE 的 BER）；剪掉 96% 仍低于 KP4-FEC 门限；MP-VE 在高稀疏区丢失重要非线性项，92% 时出现 BER 代价 [p14]
  - 累计贡献：PCG 保留约 20% 以内的项即捕获 >92% 的贡献（能量压缩曲线，读图估计）[p14]
  - 复杂度：全 VE 达 KP4-FEC 约需 ~371 次乘法/符号；PCG-VE 约 ~31（MP-VE 约 ~49，在较宽松的 HD-FEC 附近对比）；相对全 VE 约 -92%，相对 MP-VE 约 -36.5%（图中另标 -86.5%）[p15]
- 提到的公司/客户/产品/标准：IEEE 802.3dj（200G/400G/800G/1.6T Ethernet）、Ethernet Alliance 2026 路线图、OIF-800LR-01.0、KP4-FEC、HD-FEC。
- 与业界对比或记录声明：仅与自身基线（全 VE、幅度剪枝 MP-VE）比较，无 SOTA/首次声明 [p15][p16]
- 推荐配图页：p15（BER vs 每符号乘法数：全 VE / MP-VE / PCG-VE 与 -92%、-36.5% 标注）；p14（稀疏度与能量压缩）

### 0921-Mo5-待定-华南理工大学-无监督域自适应的学习子带扰动非线性补偿.pdf
- 讲者/机构：Xuan Tang（报告人）, Wanzhen Guo, Hao Deng, Jian Zhao（华南理工大学，广州）| 题目：Unsupervised-Domain-Adaptation Enhanced Learned Subband-based Perturbation Nonlinear Compensation for Optical Transmission Systems（p1 看图核实，2026-09-21）| 类型：学术论文（场次编号待定，Mo5 F 组）
- 方向归属（主/次）：主 [1 相干/长途/oDSP]；次 [1 AI光网络（ML 非线性补偿）]
- 核心主张：
  1. 提出 LSP-NLC：把色散补偿、子带分解/合成与子带扰动非线性补偿（P-NLC）做成可训练网络，CD 参数 β2、非线性系数 γ 和扰动系数 C 由神经网络训练得到，无需精确链路信息。
  2. 提出基于功率矩特征提取器（PMFE）的 UDA，特征对偏振与相位不敏感，可在信道变化时无训练序列地盲跟踪。
  3. 对参数失配鲁棒，在性能与自适应时间间取得更优折中。
- 关键数据：
  - 实验：5 路 WDM，间隔 100 GHz，线宽 100 kHz，DP PS-64QAM，40 GBaud，熵 5.43 bit/symbol/pol，跨段 80 km SMF，环回；对比 CB-ESSFM、传统 SP-NLC [p13]
  - 参数失配：色散在 16.85–17.2 ps/nm/km 扫描，LSP-NLC NGMI 约 0.87 基本平坦；CB-ESSFM 约 0.82–0.85，SP-NLC 在偏离最优时降至约 0.85（读图估计）；γ 偏移 ±5×10^-10 内 LSP-NLC 保持约 0.875 平坦 [p14]
  - 信道变化：以 400 km / -3 dBm 训练的参数用于其它距离/功率，LSP-NLC w/ UDA 与重新训练接近；CB-ESSFM、SP-NLC 不重优化时在 1200 km 分别降至约 0.82/0.83（读图估计）[p15]
  - 再优化耗时：CB-ESSFM 1150 s、SP-NLC 1311.969 s、LSP-NLC 重训练 109.39 s、LSP-NLC+UDA 25.038 s [p16]
  - 1200 km、入纤功率 -3 dBm 附近：LSP-NLC w/ UDA 与 3 steps/span DBP、SP-NLC 相当，优于 CB-ESSFM 与 P-NLC，CDC 最差 [p17]
- 提到的公司/客户/产品/标准：无；对比方法 DBP、CB-ESSFM（Hager ECOC2018 / Civelli JLT 2025）、SP-NLC（Guo COL 2026）。
- 与业界对比或记录声明：无 SOTA/首次声明；结论为"与 3 steps/span DBP 相当" [p17]
- 推荐配图页：p16（再优化时间柱状图 + UDA 收敛曲线）；p15（距离/功率变化下的 NGMI 对比）

## 本批小结
- 三篇同属 Mo5-F"机器学习与非线性补偿"场次，共同主线是"降低非线性补偿的复杂度/标定成本"：NTHU 用贡献导向剪枝把 Volterra 均衡乘法量降约 92%（NTHU），华南理工用可学习子带 P-NLC + UDA 把再优化时间从 1150–1312 s 降到 25 s（SCUT），NTT 则从发射端 DPD 入手（NTT）。
- 非线性补偿位置不同：NTT 在发射端（TFLN IQM 直驱，样本域 Volterra 预失真），NTHU 在 IM/DD 接收端均衡，SCUT 在相干长途接收端 DSP；三者层次互补。
- 高波特率下预失真需在样本域（高 PAPR 波形）进行：NTT 样本域 VF 比符号域多 0.7 dB SNR，对 200 GBd+ 及 TFLN 直驱的器件路线有参考意义（NTT）。
- 场景差异：NTT 面向 ~2.1 Tb/s 单载波（168 GBd，80 km），NTHU 面向 100G PAM4 短距 IM/DD（4.2 km），SCUT 为 40 GBaud 多跨段 WDM（至 1200 km）；后两者验证速率相对偏低，向 200G/lane 与更高波特率的可扩展性尚未验证（NTHU、SCUT）。
- 数据说明：SCUT 部分曲线数值为读图估计（题目页已看图核实）；NTT 净速率对比图未见明确 record 声明（NTT，看图核实）。
