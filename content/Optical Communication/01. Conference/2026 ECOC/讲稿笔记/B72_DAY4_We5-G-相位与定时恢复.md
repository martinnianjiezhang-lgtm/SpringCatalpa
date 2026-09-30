---
title: "B72 · DAY4 · We5-G-相位与定时恢复"
tags:
  - ECOC2026
  - DAY4
---

说明：本批 5 个 PDF 中，"00-全场连拍"为 We5-G 全场（76页）连拍，含 5 场讲稿；Chalmers / KIT / 北京大学 / 富士通 四个单讲 PDF 是同一讲稿的重拍或子集（多数页与连拍页内容相同），Huawei 无单独 PDF。以下按讲稿切分，页码均为连拍 PDF 页码。

### 0923-We5-G-00-全场连拍.pdf（第1–13页；重拍见 0923-We5-G-Chalmers-相位与定时恢复.pdf）
- 讲者/机构：Han Cui 等（Chalmers 大学、多伦多大学；Kschischang、Karlsson、Agrell） | 题目：Mitigation of Error Bursts after Pilot-Aided Carrier Phase Recovery | 类型：学术论文
- 方向归属（主/次）：主 1（相干/oDSP，载波相位恢复）；次 2（ZR 类相干中导频 CPR 的可靠性）
- 核心主张：
  1. 导频辅助 CPR 之后的估计相位误差（EPE）呈突发（正常态低方差 / 突发态高方差），用两态 Gilbert-Elliott 模型描述。
  2. Burst-aware 方案：用 EM 估计四个参数，再用两态网格 BCJR 得到软信道状态概率来计算 LDPC 的 LLR。
  3. Average-variance 方案忽略突发、只用单一平均方差，复杂度低，适合弱突发信道。
- 关键数据：
  - 仿真设置：16-QAM，IEEE 802.3ca LDPC，导频辅助 CPR 导频间隔 32（400ZR），SNR 13–17 dB，包长 512 信息比特，共仿真 570,000 包（291,840,000 信息比特），交织深度 1024 [p10]
  - GE 信道参数：P_GB = 2·10^-3，P_BG = 2·10^-2；好态方差 σ²_w,G = 2·10^-5；坏态方差 σ²_w,B 在 1·10^-2–8·10^-2 扫描 [p10]
  - 弱突发 σ²_w,B = 1·10^-2：两种方案性能近似，PER = 1% 处相对基线均有 1.17 dB SNR 增益 [p11]
  - 强突发 σ²_w,B = 4·10^-2：Burst-aware 在 PER = 1% 处比 Average-variance 有 2.28 dB SNR 增益；基线（AWGN 假设）在 13–17 dB 内达不到阈值 [p11]
  - 固定 SNR = 14 dB 扫 σ²_w,B：两种方案在整个范围内都低于基线；Burst-aware 先劣化、约 3·10^-2 附近急剧改善、之后再次劣化；三个区间：≤1·10^-2 突发影响可忽略，1–3·10^-2 弱到无法准确估计信道状态，>3·10^-2 突发可检测、Burst-aware 有效；讲者注明阈值取决于信道参数 [p12]
- 提到的公司/客户/产品/标准：400ZR（导频间隔）、IEEE 802.3ca LDPC；瑞典研究理事会资助
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；对比对象为忽略 EPE 的 AWGN 基线 [p11]
- 推荐配图页：p11（BER/PER 曲线对比三种方案，标出 1.17 dB 与 2.28 dB 增益）；p12（PER 随突发强度的非单调曲线）

### 0923-We5-G-00-全场连拍.pdf（第14–28页；重拍见 0923-We5-G-北京大学-相位与定时恢复.pdf）
- 讲者/机构：Tianhong Zhang、Yutong Pan、Yixiao Zhu、Wenhao Wang、Ning Zhang、Fan Zhang 等（北京大学、上海交通大学、SiFotonics、鹏城实验室） | 题目：Phase-Recovery-Free 6bit/4D Coherent Transmission Using Subcarrier-Joint Modulation for Large-Linewidth Lasers | 类型：学术论文（Oral）
- 方向归属（主/次）：主 1（相干/高波特率器件，低成本大线宽相干）；次 3（短距相干、低成本 DFB 光源）
- 核心主张：
  1. 两个子载波联合构成一个 4D 符号，信息编码在共模相位旋转下不变的量（总能量 E、能量分配 α、相对相位 Δ），共模相位 ψ 不用于承载数据。
  2. 相位不变的联合 4D 判决度量无需显式 CPR，同步与均衡仍保留。
  3. 在 100 kHz ECL 与 1 MHz DFB 下均完成 80 km 传输，线宽容忍度优于所比较的基线。
- 关键数据：
  - 双壳层星座 64 点 = 6 bit / 4D 符号：内壳 16 点（E1 = 1.07），外壳 48 点（E2 = 2.31） [p19]
  - 实验：2×25 GBaud，保护带 4 GHz，80 km SSMF，偏振复用（PDME 仿真），AWG 120 GSa/s，DSO 256 GSa/s；激光 Case I 1 MHz DFB（低成本）、Case II 100 kHz ECL [p21]
  - 80 km 结果：BER 随 OSNR 23–30 dB 下降，实验点在 OSNR 约 27–28 dB 落在 20% SD-FEC 阈值（约 2×10^-2）之下；25–26 dB 附近实验点靠近/略高于阈值（具体数值看不清）；100 kHz ECL 的 BER 略低于 1 MHz DFB；实验与仿真趋势一致 [p23]
  - 线宽容忍（OSNR = 26 dB，线宽按单激光器计）：低线宽时 PS-16QAM + CPR BER 更低（0.5 MHz 处约 7×10^-4）；线宽增大后 PS-16QAM + CPR 在约 2 MHz 附近与联合 4D 交叉，此后急剧恶化（约 8–9 MHz 达 ~1.5×10^-1）；联合 4D 仿真在 0.1–0.5 MHz 约 1×10^-2，至约 9 MHz 约 4×10^-2，实验点 9 MHz 附近约 6×10^-2；PS-16QAM 无 CPR 全程 BER 约 3×10^-2 至 3×10^-1 [p24]
  - 大线宽下径向统计（100 kHz / 1 MHz / 9 MHz）：分布展宽，内壳均值外移，两壳重叠增大；作者认为色散补偿后的 EEPN 是残余失真来源之一 [p26]
  - 壳内/跨壳错误均存在，外壳 SER 更高 [p25]
- 提到的公司/客户/产品/标准：SiFotonics；20% SD-FEC；PS-16QAM（对比基线）
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；主张"无显式 CPR 下更强的线宽容忍"，但低线宽区不如 PS-16QAM + CPR，且大线宽下仍有残余劣化 [p24]
- 推荐配图页：p24（BER 对线宽曲线，与 PS-16QAM 交叉点）；p19（64 点双壳 4D 星座及子载波投影）

### 0923-We5-G-00-全场连拍.pdf（第29–41页；重拍见 0923-We5-G-富士通-相位与定时恢复.pdf）
- 讲者/机构：Xiaofei Su、Tong Ye、Jingnan Li、Hisao Nakashima、Takeshi Hoshida、Yasuhiko Aoki、Zhenning Tao（富士通研发中心 FRDC、1Finity） | 题目：Baud-Rate Timing Recovery with 1UI DGD Tolerance for Dual Polarization Coherent Systems | 类型：学术论文（We5-G3）
- 方向归属（主/次）：主 1（相干 oDSP，定时恢复）；次 2（O 波段波特率采样 DCI 低功耗相干）
- 核心主张：
  1. 波特率相干系统中时钟恢复至关重要；DGD 之后的偏振旋转会显著劣化波特率 TED（常规 NL-MM 在 0.6UI DGD 下失效）。
  2. 提出 Diversified NL-MM：并联原路径与两条固定 90° 偏振旋转（PR2、PR3）路径，各自做 NL-MM，取 TED 输出幅度最大的路径，把最差偏振态"挪"到最佳偏振态附近。
  3. 仿真与实验表明 DGD 容忍度扩展到 1 UI。
- 关键数据：
  - 背景：相干模块功耗构成 DSP(core) 43%，ADC/DAC(线路侧) 26%，SerDes(主机侧) 18%，CFEC/OFEC 13%（引自 Nagarajan JLT 2024）；O 波段 + 波特率采样 ADC/DAC 与 DSP 是下一代 DCI 候选 [p30]
  - 仿真：124 GBaud DP-16QAM，Tx 4 阶 Butterworth、Rx 4 阶 Bessel，1 SPS TED；5 ps DGD = 0.6 UI（OIF 800LR 规定 5 ps DGD）；选滤波器使 CD Q 代价 < 0.5 dB（12.3 ps/nm CD，OIF 800LR） [p33]
  - 仿真：0°-5 ps-45° 偏振旋转情形下，NL-MM 的 S 曲线平坦无稳定过零点（失效）；Diversified NL-MM 有稳定过零点，定时抖动约 -40 dB；NL-MM 失效区内优于 -32 dB；任意 DGD 前后偏振旋转范围内优于 -24 dB [p34, p37]
  - 实验：64 GBd DP-16QAM，DAC 88 GS/s，DSO 128 GSa/s，激光线宽约 100 kHz，频偏约 200 MHz，两个偏振扰偏器，最大偏振变化速度 3400 rad/s，TED 平均长度 1000 符号，256 条轨迹/4 μs（假定 SOP 不变，约 0.8°） [p38]
  - DGD = 0.5 UI（8 ps），570 个随机 SOP：Diversified NL-MM 抖动整体明显低于 NL-MM；No.235 用例 NL-MM 约 -15 dB 且 S 曲线近乎平坦，改进后约 -29 dB 且 S 曲线清晰 [p39]
  - DGD = 0.25/0.5/0.75/1 UI 的 PDF/CCDF：改进方案抖动分布左移；结论页写 DGD 容忍度从 NL-MM 的 0.25 UI 提升到 1 UI [p40]
- 提到的公司/客户/产品/标准：OIF 800LR；Mueller-Müller / Sign MM / NL-MM 算法；O 波段 DCI
- 与业界对比或记录声明（SOTA/首次/record）：相对常规 NL-MM（0.6 UI DGD 失效）将 DGD 容忍度由 0.25 UI 提至 1 UI [p40–41]
- 推荐配图页：p40（四种 DGD 下抖动 PDF/CCDF 对比）；p36（Diversified NL-MM 结构与 Poincaré 球 SOP 映射）

### 0923-We5-G-00-全场连拍.pdf（第42–52页；无单独 PDF）
- 讲者/机构：Huawei Technologies（作者名单看不清） | 题目：Receiver-Side Compensation of TI-DAC Offset Mismatch in Optical Transceivers（We5-G4） | 类型：学术论文
- 方向归属（主/次）：主 1（oDSP、高波特率器件 DAC 缺陷补偿）；次 3（电芯片）
- 核心主张：
  1. 时间交织 DAC（TI-DAC）子 DAC 的偏置失配（OM）会在信号谱中产生杂散（spur），f_k = k·f_DAC/N，k 取 -N/2 到 N/2-1。
  2. 在接收端 DSP 之后，用后 DSP 符号乘以复指数并平均提取各杂散的幅度与相位，重建时域 OM 图样并直接相减；不需要已知发送数据，可在线按需重新校准，复杂度低，适用于单载波与数字子载波复用（DSCM）。
  3. 只需带内杂散；静态失配只需估计一次并存储图样；DSCM 需对每个子载波分别按其中心频率调整后计算。
- 关键数据：
  - 实验/仿真配置：140 GBaud 双偏振 64-QAM，DSCM 测试 4 个子载波，OM 仿真器 N = 16，误差幅度为零均值高斯，σ_OM 按信号 RMS 归一化，扫至 0.05，每次试验独立 OM 图样 [p49]
  - σ_OM = 0.05 的单载波例：补偿后 OM 杂散明显被抑制；整体信道 SNR 为 18 dB，杂散处局部 SNR 可低至约 8 dB（I 路，约 22 GHz 处补偿前），补偿后升至约 15 dB 以上（局部 SNR 以 1 GHz 带宽内信号与总失真功率计） [p50]
  - BER 对 σ_OM（0.01–0.05，10 次试验平均）：单载波补偿前 BER 由约 0.0227 升至约 0.0281，补偿后基本稳定在约 0.0194–0.0201；DSCM 补偿前由约 0.0277 升至约 0.0330，补偿后约 0.0250–0.0262 [p51]
- 提到的公司/客户/产品/标准：Huawei；DSCM
- 与业界对比或记录声明（SOTA/首次/record）：对比此前基于数字滤波的预失真方案（需专门校准、失配变化时无法在线重校准）；无 record 声明 [p44]
- 推荐配图页：p51（补偿前后 BER 随 σ_OM 曲线，SC 与 DSCM）；p50（补偿前后杂散频谱与局部 SNR）

### 0923-We5-G-00-全场连拍.pdf（第53–76页；重拍见 0923-We5-G-KIT-相位与定时恢复.pdf）
- 讲者/机构：Benedikt Geiger、Fred Buchali、Vahid Aref、Laurent Schmalen（KIT；Nokia 相关作者） | 题目：Modeling and Mitigation of Equalization-Enhanced Phase Noise | 类型：学术论文
- 方向归属（主/次）：主 1（相干/高波特率 oDSP，EEPN）；次 2（相干可插拔 ZR/ZR+ 对 LO 线宽的约束）
- 核心主张：
  1. EEPN 是时变、频率相关的相位误差（表现为相位偏移、定时偏移或更高阶相位畸变），块内可建模为全通滤波器。
  2. 时变全通 FIR 滤波器可反转失真：补偿阶数 N_comp = 0 对应相位恢复，1 对应定时恢复，≥2 对应自适应线性滤波器。
  3. 时域高斯噪声模型（temporal GN，方差随时间变化）可再现 EEPN 引起的突发式 SNR 劣化，并推广到任意 FDPE 补偿的性能预测；代码在 GitHub 上开源。
- 关键数据：
  - 模型参数：单载波 180 GBd，上采样 2，RRC 滚降 0.05，光纤 6600 km，D = 23 ps/nm/km，1550 nm，SNR 13 dB，线宽 70 kHz；多载波 8 路并行流 [p56–57]
  - 补偿效果（SNR 随时间图，0–0.55 μs）：无 EEPN 约 13 dB；仅载波相位恢复时 SNR 最低降到约 10.4 dB；定时恢复约 12.3–12.8 dB；N_comp = 7 的自适应线性滤波器接近无 EEPN 曲线 [p65]（该页图未标注是仿真还是实验，看不清）
  - 实验设置：DP-16QAM，130 GBd，Tx 线宽 30 kHz，LO 线宽 210 kHz，总光纤 1900 km（环路），累积 CD 36 ns/nm，块长 500；参考接收机线宽 <1 kHz、带宽 1 GHz、采样 3.125 GSa/s [p68]
  - SNR 序列：EEPN 突发使 SNR 由约 14 dB 降到约 11.7 dB（仿真与实验一致）；SotA 高斯噪声模型给出近似平坦的约 13 dB，低估影响 [p69]
  - 统计（CCDF）：SotA GN 模型与仿真静态 DSP 的相关系数 ρ = 0.01；temporal GN 模型与仿真静态 DSP ρ = 0.93；与实验自适应 DSP ρ = 0.53（自适应 DSP 部分补偿 EEPN，尾部被截短） [p71]
  - 广义模型对不同补偿（无补偿 / CPR / 定时恢复 / 自适应线性滤波器）预测的 EEPN 失真功率 CCDF：无补偿尾部延伸到约 0.22，CPR 约 0.19，定时恢复约 0.05，自适应线性滤波器接近 0.01 [p72]
- 提到的公司/客户/产品/标准：Nokia、KIT（Karlsruhe Institute of Technology）；相干可插拔；引 Shieh & Ho 2008；自家 OFC'25、ECOC'25 工作
- 与业界对比或记录声明（SOTA/首次/record）：对比"SotA"AWGN 时不变失真功率模型（低估 EEPN 影响，ρ = 0.01）；无 record 声明 [p66, p71]
- 推荐配图页：p69（SNR 序列：SotA 平坦 vs 仿真/实验的 EEPN 突发）；p71（CCDF 与相关系数表）

## 本批小结
1. 相位类"突发/时变"问题成为本场共同主题：Chalmers 把 CPR 后残余相位误差建模为 Gilbert-Elliott 突发，KIT 把 EEPN 建模为时变高斯噪声（SNR 突发式劣化，SotA 的 AWGN 时不变模型相关系数仅 0.01，新模型 0.93）；两者都指出传统"AWGN 假设"会低估短时劣化，结论对 FEC/LLR 设计有意义（Chalmers、KIT）。
2. 大线宽/低成本激光器的应对分两路：PKU 用 4D 子载波联合编码绕过 CPR（1 MHz DFB 80 km 达 20% SD-FEC 附近，线宽 ≥2 MHz 起优于 PS-16QAM + CPR），KIT 则从 EEPN 补偿侧降低对 LO 线宽的敏感；PKU 也承认大线宽下的残余失真与 EEPN 有关（PKU p26、KIT p65）。
3. 波特率（1 SPS）与低功耗趋势：Fujitsu 给出相干模块 DSP 43%、ADC/DAC 26% 的功耗分解，并把波特率定时恢复的 DGD 容忍度由 0.25 UI 提到 1 UI，服务于 O 波段 DCI（OIF 800LR 5 ps DGD = 124 GBd 下 0.6 UI）（Fujitsu）。
4. 高波特率下器件缺陷正被搬到接收端 DSP 补偿：Huawei 在 140 GBd 64-QAM 上补偿 TI-DAC 偏置失配（σ_OM = 0.05 时单载波 BER 约 0.0281 降至约 0.0201），KIT 的 130 GBd 实验同样强调自适应 DSP 修复系统层残余问题（Huawei、KIT）。
5. 本场多数结果为仿真或离线 DSP 实验（Chalmers 纯仿真，PKU/Fujitsu/Huawei 为离线处理），暂未见 record 声明；工程化前仍需实时 ASIC 复杂度评估（全部）。
