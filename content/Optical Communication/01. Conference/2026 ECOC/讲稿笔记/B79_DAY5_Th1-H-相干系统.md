---
title: "B79 · DAY5 · Th1-H-相干系统"
tags:
  - ECOC2026
  - DAY5
---

### 0924-Th1-H2-AIST-判决前馈数字反向传播延长WDMDP-16QAM传输距离.pdf
- 讲者/机构：Takashi Inoue / AIST（日本产综研） | 题目：Reach Extension of WDM DP-16QAM Signals Based on Decision-Feedforward Digital Backpropagation | 类型：学术论文
- 方向归属（主/次）：主 1（相干/长途/oDSP）；次 2（讲者背景称面向 scale-across/scale-beyond DCI）
- 核心主张：
  1. 提出 DFF-DBP（判决前馈数字反向传播），在单信道工作下同时补偿 SPM 与 XPM（传统 DBP 只补 SPM）[p1,p3]
  2. 相对 ECOC2025 原方案改进：前向传播拆分并线性化，反向传播只处理 XPM [p5]
  3. 相对仅 CDC，传输距离延长 23% [p8]
- 关键数据：
  - 21 信道 WDM，64 Gbaud DP-16QAM，RRC 滚降 0.1；中心 11 信道间隔 75 GHz，边缘信道间隔 75–225 GHz；环路 164.6 km/圈（SSMF），4–16 圈（658–2,634 km），入纤 -2~+5 dBm/ch [p5]
  - Q 限 6.25 dB（BER=2.0×10^-2）下最大距离：仅 CDC 13 圈（2,140 km）；DFF-DBP 4 sps 16 圈（2,634 km）[p7]
  - DFF-DBP 4 sps 相对仅 CDC 的 Q 值提升 0.8 dB [p7]
  - 同样 sps 下 DFF-DBP 优于常规 DBP（因补偿 XPM）[p7]
  - XPM 相位噪声带宽在 ±5 GHz 内，用低通滤波（LPF）提取；测试条件 16 span×80 km SSMF，3 dBm/ch，10 信道 64 Gbaud [p3]
  - 设计参数（缩减因子 R、LPF 带宽 B）做二维网格搜索，距离越长所需 R、B 越小（R 约 0.06–0.12，B 约 0.55–0.8 GHz，读图估计）[p6]
- 提到的公司/客户/产品/标准：无（LCoS 可编程滤波器用于实验）
- 与业界对比或记录声明：对比仅 CDC 与常规 DBP（1/2/4 sps）；未见 record 声明。文献综述：利用相邻信道幅度的 XPM 补偿（Liga 2014、Mateo 2010、Civelli 2021、Inoue 2022、Castro 2025）适用 WDM 但结构复杂、算力高；仅用本信道幅度的方案（Tao 2011、Sidelnikov 2021、Xiao 2025）只补偿一次 XPM 相移、性能有限（看图核实）[p2]
- 推荐配图页：p7（Q 值 vs 传输距离，含 Q 限 6.25 dB 及 13 圈 vs 16 圈对比）

### 0924-Th1-H3-华为加拿大-非平稳条件下用分布变换函数预测FEC后性能.pdf
- 讲者/机构：Abbas Abolfathimomtaz 等 / 华为加拿大（Advanced Optical Technology Lab, Ottawa） | 题目：Post-FEC Performance Prediction Using Distribution Transform Functions Under Non-Stationary Conditions | 类型：学术论文
- 方向归属（主/次）：主 1（相干/oDSP/FEC）；次 无
- 核心主张：
  1. 平均 pre-FEC BER 不足以预测 post-FEC 性能，FEC 看到的是逐帧误码统计；非平稳（抖动、非线性、EEPN）下 AWGN 假设失效 [p3,p7]
  2. 提出分布变换函数 DTF（帧级 pre-FEC BER 到期望 post-FEC BER 的映射），一次标定后可跨信道条件复用 [p4,p5]
  3. 高 SNR 下 DTF 近似幂律，post-FEC BER 简化为 pre-FEC 帧 BER 分布的缩放 γ 阶矩 [p6]
- 关键数据：
  - 实验：200G 相干 / DP-16QAM，1550 nm C 波段 SSMF，960 km = 12×80 km，EDFA 增益/噪声系数 20 dB / 5 dB，用收发机 FastBER 诊断，16,384 个帧级 BER 样本，每样本 655,360 bit [p8]
  - FEC：级联 SD-BCH + KP4；幂律 DTF(b)=θ·b^γ，θ=1.4979e99，γ=57.477，标定目标 post-FEC BER=1e-10 [p8]
  - 平均 pre-FEC BER 均为 1.21e-2 时，AWGN / 正常 / 非线性 / 抖动主导四种场景 post-FEC BER 差异显著（图上 post-FEC 范围约 1e-13 至 1e-7 量级，读图估计）；DTF 预测与实测吻合 [p11]
  - 开头动机称 1.6T 在 0 裕量时后 FEC 目标需约 10 min 数据才能测得（图中另标约 2000 年量级的更低门限），GN/EGN 高斯假设无法描述 EEPN、抖动、非线性等突发损伤，需新工具快速可靠预测后 FEC BER（看图核实）[p3]
- 提到的公司/客户/产品/标准：华为；KP4、BCH、oFEC 相关；OTN 收发机 FastBER
- 与业界对比或记录声明：无 SOTA 声明；主张静态 pre-FEC 阈值不足以保证 post-FEC 可靠性 [p11]
- 推荐配图页：p11（相同平均 pre-FEC BER 下四种场景 post-FEC BER 与 DTF 预测对比）

### 0924-Th1-H4-NEC-GPU实时2x2MIMO均衡实现抗快速偏振变化的PDM-16QAM传输.pdf
- 讲者/机构：Manabu Arikawa（报告人）, Takahiro Odagawa, Kohei Hosokawa, Norifumi Kamiya / NEC Connected Infrastructure Research Laboratories（p1 看图核实） | 题目：Demonstration of PDM-16QAM Transmission Robust to Fast SOP Variations Using Real-Time 2×2 MIMO Equalization on a GPU（Th1-H4） | 类型：学术论文
- 方向归属（主/次）：主 1（oDSP）；次 无
- 核心主张：
  1. 在 GPU 工作站上以实时 DSP（2×2 MIMO 均衡）实现 5 Gbaud PDM-16QAM 传输 [p6]
  2. 240 km SMF 后 pre-FEC BER 稳定超过 1 小时；SOP 扰动容限达 10 krad/s [p6]
  3. 处理吞吐量实时上限 6.1 Gbaud；多 GPU 可能支持更高波特率 [p4,p6]
- 关键数据：
  - 平台：NVIDIA RTX PRO 6000 Blackwell Workstation Edition；20 GS/s DAC/ADC；FPGA 下采样至 2 sps 并量化 6 bit；240 Gb/s ADC 数据（10 GS/s×I/Q&X/Y×6 bit）经 RoCE v2 RDMA 写入 GPU 内存 [p2]
  - 信号：5 Gbaud PDM-16QAM，DVB-S2 LDPC 帧长 64,800、码率 0.8，每 32 符号插导频，DAC 图样长 66,944 符号 [p2]
  - 吞吐：10,000 次统计，单批预处理+MIMO 核约 180 ms 量级，对应实时上限 6.1 Gbaud [p4]
  - 传输：193.3 THz，8 路 32 Gbaud WDM 假光（37.5 GHz 栅格），4×60 km SMF 共 240 km，偏振扰偏器评估 SOP 鲁棒性 [p4]
  - SOP 容限：pre-FEC BER 约 1e-4 量级平坦，至约 10 krad/s 无显著劣化，之后快速恶化 [p6]
  - 此前 GPU 实时 DSP 工作总速率在图上多为约 1–2 Gbaud、<20 Gb/s；本工作 2×2 相干约 40 Gb/s @5 Gbaud（读图估计）[p2]
- 提到的公司/客户/产品/标准：NVIDIA RTX PRO 6000 Blackwell；DVB-S2 LDPC；NICT GAUSS 项目资助（No. 24201）
- 与业界对比或记录声明：图中与文献[1]–[8]对比，本工作为已知 GPU 实时 2×2 相干最高波特率（图内表述，讲者结论页未用 "record" 字样）[p2]
- 推荐配图页：p2（GPU 实时 DSP 历史工作吞吐量对比图与平台架构）

### 0924-Th1-H5-NTT-多域光直连边界的光模拟光波长转换器.pdf
- 讲者/机构：Hiroki Mori 等 / NTT（Network Service Systems Labs），合作方 NEC | 题目：Optical-Analog-Optical Wavelength Converter for Multi-Domain Optical Direct-Connect Boundaries: 100G/400G Multi-FEC Characterization and Network Demonstration | 类型：学术论文
- 方向归属（主/次）：主 2（跨域/ZR/ZR+）；次 1（相干/长途）
- 核心主张：
  1. IOWN APN 去掉 PoI 转发器后失去域边界，需边界节点保持域自治；光-模拟-光（OAO）波长转换器（无 DSP、CFP2 兼容）可作为该边界功能 [p1,p3,p6]
  2. OSNR 代价差异主要由收发机特性决定，而非 FEC 方案 [p4]
  3. 可检测频偏错配并关断输出；跨域不同波长分配下端到端连通 [p5,p6]
- 关键数据：
  - 测试信号：400G DP-16QAM：ZR+（oFEC，60.13 Gbaud）、ZR（CFEC，59.84 Gbaud）、OpenROADM（oFEC，63.13 Gbaud）；100G DP-QPSK：ZR+（oFEC，30.07 Gbaud）、OpenROADM（SC-FEC，27.95 Gbaud）[p4]
  - OSNR 代价：收发机 T1 在 oFEC 下约 1.7 dB（图示 ΔOSNR_oFEC_T1=1.7 dB），T1 CFEC 下 3.2 dB（同图另有一处标 3.2 dB @OSNR=23 dB，标注位置存在歧义）；T2 oFEC 下 2.6 dB [p4]
  - 频偏检测：输入光功率约为 -1.5 dBm 参考，可检测范围约 ±75 GHz 内（读图估计），告警日志为 WAVELENGTH_SHIFT [p5]
  - 多域 ROADM 演示：Domain A 196.1 THz、Domain B 193.4 THz，各 SMF 75 km；T1 CFEC pre-FEC BER 无 WC 8.8E-04 → 有 WC 5.1E-03（阈值 1.0E-02，裕量 0.29 decade）；T1 oFEC 3.6E-04 → 7.8E-03（阈值 2.0E-02，裕量 0.41）；T2 oFEC 1.2E-03 → 7.9E-03（阈值 2.0E-02，裕量 0.40）[p6]
- 提到的公司/客户/产品/标准：IOWN APN、OpenROADM、ZR/ZR+、CFP2、oFEC/CFEC/SC-FEC
- 与业界对比或记录声明：无 SOTA 声明；强调 OAO 无 DSP、多厂商多 FEC 兼容
- 推荐配图页：p6（多域 ROADM 演示拓扑与三种信号的 pre-FEC BER 与阈值裕量表）

## 本批小结
1. 相干系统 DSP 出现"算法-平台"两端同时演进：AIST 用 DFF-DBP 以更多算力换 23% 距离（2,140→2,634 km），NEC 探索用商用 GPU 实现实时 MIMO 均衡（仅 5 Gbaud，与商用 ASIC 差距仍大）（H2、H4）。
2. 链路质量指标正从平均 pre-FEC BER 转向帧级统计：华为提出 DTF 预测 post-FEC，指出同一平均 BER 下 post-FEC 可差数个量级（H3）；与 AIST 用 Q/NGMI 做参数寻优的思路互补（H2、H3）。
3. 非线性补偿的实用化取舍显式化：DFF-DBP 需二维参数搜索且距离越长参数越保守（R、B 变小），即依赖判决质量（H2）。
4. 跨域/多厂商互通被推向光层：NTT 用无 DSP 的 OAO 波长转换器隔离域，并验证 ZR/ZR+/OpenROADM 400G/100G 多 FEC 兼容，代价约 1.7–3.2 dB OSNR，主要由收发机而非 FEC 决定（H5）。
5. 实验规模普遍偏小（NEC 5 Gbaud、NTT 75 km×2、华为 960 km 单信道），本批为原理验证性质，缺少 1.6T/224 Gbaud 以上速率的数据（H3、H4、H5）。
