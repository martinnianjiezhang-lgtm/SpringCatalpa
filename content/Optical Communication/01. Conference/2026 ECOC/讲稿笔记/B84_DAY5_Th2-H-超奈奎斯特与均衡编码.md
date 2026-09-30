---
title: "B84 · DAY5 · Th2-H-超奈奎斯特与均衡编码"
tags:
  - ECOC2026
  - DAY5
---

### 0924-Th2-H1-EPFL-光互连用最大覆盖Chase译码器.pdf
- 讲者/机构：EPFL（讲者姓名页面未见） | 题目：Maximum Coverage Chase（"A low-complexity Chase Decoder for optical interconnects with improved TEP selection"，p4 副标题；完整英文原题看不清） | 类型：学术论文
- 方向归属（主/次）：主 3（Scale-out 224G/448G 电芯片/FEC）/ 次 2（ZR/ZR+ FEC）
- 核心主张：
  1. Chase 译码器编码增益靠增加测试错误图样（TEP）数，代价是更多硬判决译码器、更大面积与功耗；目标是在保持纠错性能的前提下减少 TEP 数 [p3]。
  2. 将 TEP 选择表述为广义最大覆盖（GMC）问题，用逻辑权重（LW）刻画错误序列概率，离线用贪心算法求解 [p6–p7]。
  3. 对真实光通信场景（RS-BCH 级联、oFEC）实现了复杂度下降；后续工作为并入完整接收链和 VLSI 实现 [p13]。
- 关键数据：
  - 错误空间取 η 个最不可靠比特的 2^η 种错误序列，仿真 η=12；覆盖率 Chase-II 34.4%、LW-Chase 27.4%、GMC-Chase 52.4% [p7]
  - 级联码 25×RS(544,514,15)–544×eBCH(142,125,2)，PAM-4：GMC-Chase 用 Np=48 达到 Chase-II Np=64 的性能，最坏复杂度降 25%；图示 Pre-FEC BER 约 1.23%–0.80%（SNR 14.0–14.6 dB）范围 [p10]
  - oFEC：32×eBCH(256,239,2)，16-QAM：GMC-Chase-LUT 用 Np=36 达到 Chase-Pyndiah Np=93 的性能，最坏复杂度降 61.3%；Pre-FEC BER 约 2.4%–2.2%（SNR 12.34–12.52 dB）范围 [p12]
  - 另有同 TEP 数（64）下 eBCH(256,239,2)/eBCH(256,231,3) 的 BER 曲线对比，具体增益数值未读图 [p8]
- 提到的公司/客户/产品/标准：oFEC、RS-BCH 级联、800G-ZR/ZR+（引用 JLT 2023 FPGA 研究作对比基线 [4]）、OFC 2025 LW-Chase 前作 [3]
- 与业界对比或记录声明（SOTA/首次/record）：相对 Chase-II/Chase-Pyndiah 同性能下 TEP 数分别减 25%/61.3%，未称 record [p10, p12]
- 推荐配图页：p12（oFEC 上 36 vs 93 TEP 的 BER 曲线与复杂度柱图）；p7（三种 TEP 集的错误空间覆盖率对比）

### 0924-Th2-H2-KIT-光纤与光子辅助亚太赫兹无线混合链路的鲁棒实时DSP.pdf
- 讲者/机构：Filipp Gostner 等 / KIT | 题目：标题页OCR无法辨识（内容为 Robust real-time DSP for hybrid fiber and photonic-assisted sub-THz wireless links，此为按中文文件名与内容的推断，非页面原文） | 类型：学术论文
- 方向归属（主/次）：主 5（固定与无线接入 RoF/sub-THz）/ 次 1（oDSP）
- 核心主张：
  1. 演示实时、相干、光子辅助 sub-THz 链路，集成 10 km SSMF、1.4 m 无线和基于 FPGA 的实时 DSP [p8]。
  2. 实时 DSP 需同时处理定时误差、时钟频偏、ISI、相位噪声和信号中断；实现了 Gardner 定时恢复、时钟偏移补偿、CMA 自适应均衡、载波相位恢复 [p4, p8]。
  3. 稳定支持 ±100 ppm 相对时钟偏移 [p7]。
- 关键数据：
  - 系统：EO 光梳产生间隔 292 GHz 的两根谱线，一根载 2.048 GBaud IQ 数据，另一根作参考，UTC 光电二极管产生 sub-THz 载波，1.4 m 无线，电子次谐波混频下变频（OCR，未核图）[p3]
  - 收发采样 4.096 GSPS；均衡为 12 抽头 T/2 间隔 CMA，抽头缓冲 16 bit；收敛约 100 μs（初始）、约 1 μs（信号中断后）[p4, p6]
  - 时钟恢复：非数据辅助 Gardner TED，4 抽头 FIR 分数插值，二阶 PI 环；初始锁定 10 μs，中断后锁定 5 μs [p5]
  - QPSK：SNDR 约 14.2–14.9 dB，BER 低于 1e-7，净速率 3.99 Gbit/s（假设 2.7% OH FEC）；16-QAM：SNDR 约 13.2–14 dB，BER 低于 2×10^-2，净速率 6.83 Gbit/s（假设 20% OH FEC）；含/不含 10 km SSMF 均评估 [p7]
- 提到的公司/客户/产品/标准：无（引用 Dittmer 等 ECOC 2026 的 56 m 400 Gbit/s sub-THz 链路 [p2]）
- 与业界对比或记录声明（SOTA/首次/record）：讲者强调既往多为离线 DSP、实时 DSP 较少，未用"首次"字样 [p2]
- 推荐配图页：p7（QPSK/16-QAM 的 SNDR、BER 随 ±100 ppm 时钟偏移曲线与星座图）；p5（实时时钟恢复框图与锁定曲线）

### 0924-Th2-H3-NTT-带宽受限下非均匀星座对PCS-16QAM的MLSE解调性能影响.pdf
- 讲者/机构：NTT, Inc.（讲者姓名页面未见） | 题目：标题页无OCR文字；内容为带宽受限下 PCS-16QAM 的 MLSE 先验概率项加权研究（英文原题未读到） | 类型：学术论文
- 方向归属（主/次）：主 1（相干/高波特率/oDSP）/ 次 无
- 核心主张：
  1. PCS 信号的先验概率项应计入 MLSE 分支度量，但在严重带宽受限（BWL）系统中应取多大权重尚不清楚 [p4, p9]。
  2. 分支度量写为 (y_i − Σh_k x_{i−k})² − 2ασ²lnP(x)，实验搜索使 GMI 最大的 α（α=0 为忽略先验，α=1 为高斯噪声下理论值）[p9]。
  3. 最优 α 落在 0.4–0.6，即理论值的 0.4–0.6 倍；部分原因是残余噪声偏离高斯、峰更尖 [p13, p15]。
- 关键数据：
  - 实验：PCS-16QAM，熵 7.8/6.8/6.2 bit/symbol，波特率 64/70/76 Gbaud，OSNR 26 dB 与 22 dB；接收端 FD-8x2 MIMO 均衡后 MLSE，评估 GMI（OCR 读到 AWG 96 GSa/s，带宽数值看不清）[p10]
  - GMI 对 α 的依赖随 OSNR 降低、波特率升高而增强；64 Gbaud、OSNR 26 dB 时几乎无依赖 [p12]
  - 最优 α 表：OSNR 26 dB 下 70 Gbaud 为 0.4，76 Gbaud（熵 6.8、6.2）为 0.6；OSNR 22 dB 下 64/70/76 Gbaud 多为 0.6（熵 7.8 为 0.4）；部分条件因 MLSE 抽头未收敛未测 [p13]
  - 76 Gbaud、OSNR 26 dB：最优 α=0.6 相对无 MLSE，GMI 提升 7%（熵 6.8）和 9%（熵 6.2）；GMI 绝对值约 5.3–5.4 bit/symbol（图读数，粗略）[p13]
  - α=0 的 MLSE 在熵 6.8 时 GMI 略低于无 MLSE（图示）[p13]
- 提到的公司/客户/产品/标准：无（引用 Jia 等 Opt. Express 2022 的先验项 MLSE）
- 与业界对比或记录声明（SOTA/首次/record）：未声明
- 推荐配图页：p13（最优 α 表与 GMI 对比柱图，7%/9% 提升）；p12（不同波特率/OSNR 下 GMI–α 曲线）

### 0924-Th2-H4-东南大学与紫金山实验室-光子辅助306GHzFTN无线系统的低复杂度FPGAPR-9QAM检测.pdf
- 讲者/机构：东南大学 与 紫金山实验室（讲者姓名页面未见） | 题目：标题页OCR乱码；内容为光子辅助 306 GHz FTN 无线系统的低复杂度 FPGA PR-9QAM 检测（英文原题未读到） | 类型：学术论文
- 方向归属（主/次）：主 5（固定与无线接入 sub-THz 无线）/ 次 1（oDSP）
- 核心主张：
  1. 用部分响应（PR）编码 + FTN + 带宽截断压缩谱宽，使高波特率信号可用较低 ADC 采样率接收 [p3, p4]。
  2. PR-9QAM 为多环非恒模信号，提出 AMBM 近似模值的 CMMA 均衡以及基于第二环的载波恢复，降低 FPGA 复杂度 [p5, p6]。
  3. 实时 PR-FTN 接收可在有限 ADC 与 FPGA 资源下实现，是高容量 THz 无线的可行路径 [p10]。
- 关键数据：
  - 系统：15 GBaud PR-FTN 信号，306 GHz，3 m 无线；接收 30 GSa/s、8 bit ADC，XCVU13P FPGA，实时 DSP 时钟 234.375 MHz [p7, p8]
  - 带宽保留比 BRR=0.85 为最终工作点：BRR≥0.85 时 BER 在最佳输入功率附近明显低于 7% HD-FEC 阈值（3.8E-3）；BRR 更低则残余 ISI 增大；EVM 在 BRR 0.85 与最优点近似相同 [p8]
  - 30 分钟实时稳定性：EVM 保持约 13–16%，无明显漂移 [p8]
  - 结论页：30 Gb/s QPSK，3 m、306 GHz，30 GSa/s 8 bit ADC，BRR=0.85 下无误码（"error-free"，原文表述）[p10]
  - AMBM 近似（α=1, β=0.5）对比 CORDIC，单模值单元：LUT 411→58（降 85.9%），FF 528→52（降 90.2%），DSP48E2 2→0（消除），延迟 22→2 周期（降 90.9%）；64 路并行 FIR、16 路抽头更新使自适应硬件减 4× [p5]
  - 第二环载波恢复：观测窗口缩至常规的约 1/4（OCR，未核图）[p6, p9]
- 提到的公司/客户/产品/标准：Xilinx XCVU13P FPGA；UTC-PD（无具体厂商）
- 与业界对比或记录声明（SOTA/首次/record）：未声明
- 推荐配图页：p8（BRR–BER、EVM、30 分钟稳定性三联图）；p5（AMBM-CMMA 64 路并行架构与资源对比表）

### 0924-Th2-H5-复旦大学-FPGA均衡引导SFO补偿实现30.2公里D波段光子辅助无线接收.pdf
- 讲者/机构：复旦大学（讲者姓名页面未见；场景为复旦校区至新河镇外场链路） | 题目：标题页OCR乱码；内容为 FPGA 均衡引导采样频偏（SFO）补偿的 30.2 km D 波段光子辅助无线接收（英文原题未读到） | 类型：学术论文
- 方向归属（主/次）：主 5（固定与无线接入 sub-THz/D 波段无线）/ 次 1（oDSP）
- 核心主张：
  1. 用 CMA 均衡器主抽头的迁移方向来控制 Farrow 重定时的采样相位，形成定时闭环，补偿时钟漂移导致的 SFO [p2, p4, p5]。
  2. 不补偿时 BER 随记录长度增加而恶化，补偿后保持稳定 [p12]。
  3. 接收 DSP 部署于 FPGA，实现 30.2 km D 波段无线 16 Gbaud QPSK 接收 [p10, p14]。
- 关键数据：
  - 链路：复旦校区—新河镇 30.2 km 无线（图示分段 10.8 km 与 19.4 km，含义看不清）；128 GHz 载波（光拍频产生）；D 波段发射 16 Gbaud QPSK，64 GSa/s AWG [p2, p7, p14]
  - 接收：100 GSa/s 波形捕获、板载 RAM 处理；XCVU13P，250 MHz，64 路并行（OCR）；Farrow 重定时 + 并行 CMA + FOE/CPR [p2, p9, p10]
  - 时钟漂移：100 ppm 下 16 Gbaud，约 0.625 ps 即漂移一个符号（OCR）[p3]
  - 不补偿（w/o SFO）BER 在约 2×10^5 符号处升至约 2×10^-2（SD-FEC 20% 阈值），继续增至 5×10^5 符号约 0.25；补偿后全程约 5×10^-3 [p12]
  - 迭代校正：1 次迭代残余 SFO 优于不补偿，10 次迭代更低（例如 SFO 10 ppm 时约 1e-8 ppm 量级，读图粗估）；启动捕获所需符号数随施加 SFO 增加，约 4×10^6（1 ppm）到约 10^7（100 ppm）[p13]
  - 16 Gbaud QPSK：BER 低于 20% SD-FEC 阈值，符号率扫描 16 GBaud 处约 5×10^-3，略高于 7% HD-FEC（3.8E-3）阈值；32 Gb/s 毛速率，30.2 km；ROP 扫描约 -7 dBm 时 BER 约 1.2×10^-2，0 dBm 时约 5×10^-3 [p14]
  - 结论页：距离×速率 966.4 Gb/s·km（OCR，与 32×30.2 相符）[p15]
- 提到的公司/客户/产品/标准：Xilinx AUV1302 板卡（OCR）、XCVU13P；20% SD-FEC / 7% HD-FEC 阈值
- 与业界对比或记录声明（SOTA/首次/record）：未见 record 字样，仅报告 30.2 km、32 Gb/s
- 推荐配图页：p12（有/无 SFO 补偿的 BER–符号数曲线）；p2（外场链路示意 + 方法对比 + 三项主结果）

### 0924-Th2-H6-复旦大学-免自适应THP-FFDNN实现169GBaud超奈奎斯特PAM4传输.pdf
- 讲者/机构：Yuan Wei（一作，邮箱 ywei23@m.fudan.edu.cn）、Nan Chi、Jianyang Shi、Junwen Zhang 等 / 复旦大学、张江实验室 | 题目：Demonstration of 169-Gbaud Faster-Than-Nyquist PAM4 Transmission Using Adaptation-Free THP-FFDNN Under 37.9-GHz 3-dB Bandwidth Limitation | 类型：学术论文
- 方向归属（主/次）：主 3（Scale-out 448G/高波特率 IM/DD）/ 次 1（oDSP，神经网络均衡）
- 核心主张：
  1. FTN 滤波压缩谱宽，使带宽受限下可用更高波特率 PAM4；DFDNN 学习 ISI，以 THPNN（发端预补偿）+ FFDNN（收端检测）部署 [p5]。
  2. 引入免自适应的全神经网络收发框架 THP-FFDNN，用于 IM/DD FTN-PAM4 [p13]。
  3. 后续计划把 THP-FFDNN 部署到 GPU 做实时神经信号处理以替代传统 DSP 均衡 [p13]。
- 关键数据：
  - 实验：1550 nm，AWG 224 GSa/s（模拟带宽 80 GHz），MZM 带宽 110 GHz（TFLN-MZM），示波器 256 GSa/s、模拟带宽 59 GHz，PD 电带宽 100 GHz，滚降因子 0.2；自适应方法训练开销 30%；链路为 B2B 与 0.5 km SMF [p8]
  - 参数扫描最优：FFE 37 抽头（μ=0.013），DFE 13 抽头（μ=0.015），DFDNN 输入长度 101 [p10]
  - 3-dB 带宽：B2B 43.5 GHz、0.5 km SMF 37.9 GHz；THP-FFDNN 分别支持至 171 GBaud 与 169 GBaud PAM4 [p11]
  - 300 Gbps 下接收灵敏度：B2B 1.01 dBm，0.5 km 为 1.57 dBm；仅在 ROP=4 dBm 训练，免自适应 [p11]
  - FTN 滤波使 PAM4 速率提升 23 Gbaud（BER 阈值 2e-2）；THP-FFDNN 仅 408 个参数 [p12]
  - 固定信号带宽 (1+α)·τ·baud/2=60 GHz，α=0.2，波特率 100–200 Gbaud 对应 τ=100/100–100/200 [p11]
- 提到的公司/客户/产品/标准：无（对比 2018/2022 ECOC、2019 OFC、2022 Opt. Commun.、2023/2024 Opt. Lett. 前作）
- 与业界对比或记录声明（SOTA/首次/record）：讲者称"record-high 169-Gbaud PAM4 under <50-GHz 3-dB bandwidth"，图中"This work"位于既往工作右上方（约 38 GHz、约 169 GBaud）[p12]
- 推荐配图页：p12（PAM4 波特率–3 dB 带宽与既往工作对比散点图，含 23 Gbaud 提升）；p11（B2B 与 0.5 km 的 BER–波特率/ROP 曲线）

## 本批小结
1. 带宽受限下"用算法换器件带宽"是本场主线：H6 用 FTN + 神经网络在 37.9 GHz 3-dB 带宽下做到 169 Gbaud PAM4；H3 表明 PCS-16QAM 在 76 Gbaud 严重 BWL 下 MLSE 先验项取理论值 0.4–0.6 倍最优；H4 用 PR-FTN 压缩带宽以适配 30 GSa/s ADC（H3、H4、H6）。
2. 学界均衡从固定 FFE/DFE 走向学习型或 ISI 感知处理：H6 的 THP-FFDNN 仅 408 参数且免自适应；H3 指出理论（高斯）先验权重在实际非高斯残余噪声下需打折（H3、H6）。
3. FEC 侧的降本方向是"同性能更少硬判决译码器"：H1 用 GMC 选 TEP，RS-BCH 级联 TEP 64→48（-25%），oFEC 93→36（-61.3%），仍限于仿真，VLSI 待做（H1）。
4. sub-THz 无线光子辅助链路的关注点从"离线高速率"转向"实时 FPGA 接收"：H2（KIT，4 GSPS，速率个位 Gbit/s）、H4（东南大学，30 Gb/s、3 m、306 GHz）、H5（复旦，32 Gb/s、30.2 km、128 GHz）；速率仍为 10 Gb/s 量级，但实时性、时钟偏移鲁棒性成为核心指标（H2、H4、H5）。
5. 时钟/定时恢复是实时无线接收的共同瓶颈：H2 用 Gardner + PI 环支持 ±100 ppm，H5 用 CMA 抽头迁移驱动 Farrow 重定时，不补偿则 2×10^5 符号后 BER 越过 20% SD-FEC 阈值（H2、H5）。
6. FPGA 实现强调降低乘法/DSP 资源：H4 的 AMBM 模值近似使 DSP48E2 由 2 降为 0，LUT 降 85.9%；H5 采用 64 路并行 250 MHz 架构（H4、H5）。
