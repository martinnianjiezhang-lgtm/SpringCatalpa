---
title: "B59 · DAY4 · We1-G-DSP光网络监测"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We1-G-00-全场连拍.pdf（第1–11页）
- 讲者/机构：Lixia Xi（报告人；一作 Yichao Wang），北京邮电大学信息光子学与光通信国家重点实验室（合作：聊城大学） | 题目：Tens-Meter-Level Least Squares Longitudinal Power Monitoring: A Truncated Singular Value Decomposition Method（论文 ID 156） | 类型：学术论文
- 方向归属（主/次）：主 1（光网络监测/AI光网络/oDSP）；次 无
- 核心主张：
  1. 细空间步长 Δz 使 LS-LPM 的扰动模板矩阵 G 相邻列高度相关，出现近零奇异值，1/σ 放大噪声，功率谱剖面估计失效（病态）[p4, p6]。
  2. 提出 TSVD-LS：物理引导的截断指标 m_c（由空间相关函数导出，给定链路仅由信号带宽决定，与色散、带宽、链路长度相关）+ Tukey 窗软截断，抑制硬截断 Gibbs 振荡 [p6, p7, p10]。
  3. 实现细粒度（数十米量级）纵向功率监测：仿真 Δz=50 m，实验 Δz=75 m [p10]。
- 关键数据：
  - 仿真：80 GBaud PS-64QAM，双偏振，3×50 km SMF，EDFA 增益 10 dB、NF 5 dB，α 0.2 dB/km，γ 1.3 /W/km，16 组×2^16 符号并引入 Tukey 窗；与 RLS（大正则项）对比：RLS 曲线过平滑并有功率偏移（约 1.43/2.11 dB），TSVD-LS 可靠（看图核实） [p8]。
  - 实验：80 GBaud PS-64QAM，120 GSa/s AWG，256 GSa/s 示波器，链路 50 km + 20 km + 30 km + 50 km SMF 环路，中间插入 3 dB 损耗；每组 2^16 符号、平均 400 组 [p9]。
  - TSVD-LS 检出 3 dB 损耗；RLS 存在 1.83 dB 检测误差 [p9]。
  - 光纤衰减系数 0.197、0.174、0.187、0.195 dB/km（各段）[p9]。
  - 空间分辨率：仿真 50 m；实验 75 m [p10]。
- 提到的公司/客户/产品/标准：无（对比方法 RLS；引用 Sasai 的 LS-LPM）
- 与业界对比或记录声明（SOTA/首次/record）：未声明 record；对比 RLS 正则方法，称 TSVD-LS 更适合细 Δz [p9]。
- 推荐配图页：p9（实验平台、恢复的功率谱剖面与 3 dB 损耗指示曲线，TSVD-LS 对比 RLS）

### 0923-We1-G-00-全场连拍.pdf（第12–22页）
- 讲者/机构：Yingjie Jiang（一作）；Du Tang（通讯，中国信通院 CAICT）、Yaojun Qiao（通讯，北京邮电大学）等；合作单位：北京大学、聊城大学、北京理工大学 | 题目：Practical Implementation of Power Profile estimation with Reduced complexity and Pre-FEC data（We1-G2） | 类型：学术论文
- 方向归属（主/次）：主 1（光网络监测/AI光网络）；次 无
- 核心主张：
  1. 实际部署 PPE 有两大约束：复杂度（符号率数据、粗步长 + CD 运算的 FFT/IFFT）和只能用 pre-FEC 硬判决数据（无需重新编码，但会带来功率偏移）[p13, p15]。
  2. 三类影响：符号率（1 Sps）数据使扰动矩阵构造的 CD 运算不准；粗步长使 eRP1 模型精度下降；HD 数据的判决错误使功率下降随 BER 增大 [p16]。
  3. 提出实用框架：硬判决 + 加权 RP1（WRP1）+ 分布加权（Distribution Weighting）+ LS PPE，兼顾超低复杂度与 HD 数据 [p17, p21]。
- 关键数据：
  - 数值验证：DP-16QAM，80 GBaud，色散参数 −21.7 ps²/km（即 β2），衰减 0.2 dB/km，非线性系数 1.4 /W/km，5×50 km，125 km 处插入损耗；1 Sps HD 数据 RMSE 约 3.4–6.4 dB，而 WRP1+分布加权约 0.2–0.3 dB；步长 5 km 时时间节省约 10 倍（看图核实） [p18]。
  - 1 Sps HD 数据 + 5 km 步长直接使用：RMSE 3.8 dB；所提方案 RMSE 降至 0.32 dB，计算时间减少 75% [p19]。
  - 误差直方图与 2 Sps Tx 数据（2.5 km 步长）相近，95% 误差在 1 dB 以内 [p19]。
  - 异常检测：在 125 km 处插入损耗 0.9、2.1、5.0 dB，方案均可识别，估计损耗与插入损耗吻合 [p20]。
- 提到的公司/客户/产品/标准：引用 Sasai（NTT/Fujitsu 体系的 LPM 性能极限 JLT 2023）；无具体产品
- 与业界对比或记录声明（SOTA/首次/record）：未声明 record [p21]
- 推荐配图页：p19（功率谱剖面对比：理论/2 Sps Tx/1 Sps HD/WRP1，含 RMSE 结论）
- 展望（p21）：克服 CD 块 FFT/IFFT 计算负担；探索实时监测（高时间分辨率）；扩展到增益谱、光纤类型等网络监测。

### 0923-We1-G-00-全场连拍.pdf（第23–35页）
- 讲者/机构：Shen Wang（一作），Jing Zhang（通讯）等，电子科技大学（UESTC） | 题目：Highly Sensitive and Phase-Noise-Tolerant Multipath Interference Localization in IM/DD Systems by Block-based SNC | 类型：学术论文
- 方向归属（主/次）：主 1（光网络监测/AI光网络）；次 3（IM/DD 400G/lane 链路质量）
- 核心主张：
  1. 高速 IM/DD 中多径干涉（MPI，连接器/接头反射经自拍频将相位噪声转为数据相关失真）随波特率上升愈发关键，DCI 向 1.6T/3.2T、约 400 Gb/s 每通道演进 [p25]。
  2. 传统接收端 SNC（残余噪声与判决符号互相关）因激光线宽/大延迟下 cos 项极性反转而峰值抵消、灵敏度下降甚至失效；简单平方（Squared SNC）虽消除极性但降低弱峰可分辨性 [p27, p28]。
  3. BSNC：分块短相关（块内极性保持）+ 平方累加（消除块间抵消），实现在线、无需中断业务的高灵敏度 MPI 定位 [p29]。
- 关键数据：
  - 仿真：100 GBaud PAM4，线宽 1 MHz，块长 L=3000，三条独立 MPI 路径：80 ns @34 dB（BSNC PNR 24.8 dB，SNC 12.9 dB，Squared SNC 9.3 dB）；2.75 µs @28 dB（BSNC PNR 30.0 dB，SNC 12.6 dB，Squared SNC 18.0 dB）；4 µs @36 dB（BSNC PNR 21.8 dB，仅 BSNC 检出）[p31]。
  - 实验：50 GBaud，线宽 3 MHz，块大小 500；传统 SNC 检测极限 SIR 26 dB，Squared SNC 30 dB，BSNC 40 dB，即灵敏度改善 14 dB [p30, p32]。
  - 定位精度：反射段长度 0.22–3.06 m，定位误差 < ±6 mm（基线 D0=214964 样点，+0.22 m 对应 ΔD=53，+3.06 m 对应 ΔD=749）[p33]。
- 提到的公司/客户/产品/标准：无
- 与业界对比或记录声明（SOTA/首次/record）：相对传统 SNC 14 dB 灵敏度提升 [p32]；未称 record。
- 推荐配图页：p32（PNR 对 SIR 曲线，SNC/Squared SNC/BSNC 灵敏度对比）；p31（三路径 MPI 定位对比）

### 0923-We1-G-00-全场连拍.pdf（第36–59页）
- 讲者/机构：Ryosuke Takagi（报告人），大阪大学（合作：NICT，Motomura、Oda 等） | 题目：Localization of Heterogeneous Fiber Type Using Inverse Scattering Transform | 类型：学术论文
- 方向归属（主/次）：主 1（光网络监测/AI光网络/长途）；次 无
- 核心主张：
  1. 链路中意外混入异质光纤（如 SSMF 链路中插入 NZ-DSF：增量升级、基础设施共享、光纤记录不全）会降低 QoT 估计精度并造成保守裕量与低效运行 [p40]。
  2. 用基于逆散射变换（IST/非线性傅里叶变换）的方法：1-孤子解估计色散参数；2-孤子解通过碰撞点扫描定位异质光纤（碰撞点在 NZ-DSF 中心处本征值偏移最大）[p42, p46–49]。
  3. 前人工作仅在均匀光纤链路估计光纤参数，本工作为异质光纤定位与色散估计 [p41]。
- 关键数据：
  - 实验：1549.31 nm，6 span × 50.5 km，共 303.0 km，SSMF/NZ-DSF，256 GSa/s 相干接收，DSO；SSMF 测得色散 16.3 ps/nm/km，NZ-DSF 4.0 ps/nm/km（Keysight 86038B 测量）[p50, p52]。
  - 色散估计：NZ-DSF 在第 1、4、5 span 时，估计均值/中位数分别为 4.6/4.7、3.9/3.8、4.6/4.6 ps/nm/km（实测 D_N 4.0、D_S 16.3 ps/nm/km），可清晰区分 SSMF 与 NZ-DSF（看图核实，UOsaka）[p52, p53]。
  - 定位：第 1/4/5 span 的估计误差分别为 7.3 km、1.4 km、13.2 km，均在 ±25 km（半个 span）内；z_min 分别 -1.3 km、156.3 km、221.4 km [p55]。
  - 仿真（span 50.5 km×6/10、80 km×10；D_N=0/4）：定位误差在 10.7 km 内，D_N 估计误差在 0.2 ps/nm/km 内 [p56–59]。
- 提到的公司/客户/产品/标准：KDDI 基金、Shimadzu、Fujikura 基金、JSPS 资助；仪器 Keysight 86038B；引用 Eto ECOC 2023、Takahashi OECC 2025、Sasai LPM
- 与业界对比或记录声明（SOTA/首次/record）：对比 OTDR（逐 span、高时间和资金成本）与 LPM；未声明 record [p38]。
- 推荐配图页：p55（三种 NZ-DSF 位置的本征值碰撞点扫描定位结果与误差）；p59（结论页）

### 0923-We1-G-00-全场连拍.pdf（第60–93页）
- 讲者/机构：Dario Pilori，都灵理工大学（Politecnico di Torino, DET / OPTCOM）；合作 Links Foundation | 题目：Longitudinal Power Monitoring and Non-Linear Interference Estimation in Long-Haul Optical Links（We1-G 邀请报告） | 类型：邀请报告
- 方向归属（主/次）：主 1（相干/长途/AI光网络/oDSP）；次 无
- 核心主张：
  1. LPM 强大、有效，且“已商业部署”（引 Sasai 等 OFC 2026 Th4B.4：首个可做距离分辨 LPM 的相干 DSP 与可插拔收发器）[p93]。
  2. 接收端 DSP 做 NLI 估计可实现简单、自动的发射功率优化，无需详细链路模型；LPM 结果可“几乎免费”复用得到 NLI 估计 [p93]。
  3. 关键弱点：只估计自信道干扰 SCI，总 NLI 需 XCI 修正；随符号率升高该问题会变弱 [p93]。
- 关键数据：
  - 异质链路实验：约 1,483 km；SSMF 65 km ×8 + PSCF 110 km ×4 + SSMF 65 km ×8；18×118 GBd QPSK，Acacia CIM-8 收发；光纤 SMF D=16.5 ps/nm/km、Aeff=80 µm²，PSCF D=20.5 ps/nm/km、Aeff=120 µm² [p67]。
  - NLI 估计：LPM 估计的 SNR_NLI 标记与 OSA 测量（1/SNR_NLI = 1/SNR − 1/SNR_TRX − 1/SNR_ASE）在 191.5–195 THz 内总体吻合，SNR_NLI 范围约 14–23 dB（发射功率 14.5/16.4/18.5/20.3 dBm 分别约 21.4–23、20–21.6、17–19、14.1–16.3 dB），边缘信道偏差稍大（约 1 dB）（看图核实；Pilori et al., OFC 2026 W2A.49 与 JLT 2026）[p90, p91]。
  - 其他应用展示：PDL 定位（2/3/4 dB PDL 可定位）[p75]；WSS 滤波偏移估计与定位（0/±3/±6 GHz）[p77]；拉曼放大监测、部分色散补偿链路 [p71]；PPE 用于发射功率优化 [p12/G5-67]。
  - 对比其他 NLI 测量：时域法（CPR 自相关、ANC、PDL 统计、星座 ML）被动、无需改发射机但需训练与校准；频域法（光谱分析、扰动法、导频音）精确稳健但需改发射 DSP/光学 [p82]。
- 提到的公司/客户/产品/标准：Fujitsu（OFC 2024 首提 LPM 估计 NLI；Tanimura ECOC 2019 PDP）、Acacia CIM-8、Sasai、Poggiolini（GN 模型）、Curri、Keysight 无、Links Foundation
- 与业界对比或记录声明（SOTA/首次/record）：无自身 record；陈述 LPM 已商业部署 [p93]。
- 推荐配图页：p67（1,483 km 异质链路实验平台与光纤参数）；p93（结论页）；p91（LPM 与 OSA 的 NLI SNR 对比）

### 0923-We1-G5-67-纵向功率监测与非线性干扰的DSP.pdf（第1–19页）
- 说明：此 PDF 为上一节 Pilori 邀请报告的精简版本（内容重复，p8/p14/p19 已去重），不另作重复分析；仅补充上一节未列出的页：p10 拉曼放大监测（引 Andrenacci ECOC 2024，Raman 放大 C+L 链路 LPM）；p12 发射功率优化（引 Poggiolini GN 模型；Jiang IPC 2024 super-(C+L) 功率优化）；p16 SCI 与 XCI 图示。
- 讲者/机构：Dario Pilori，都灵理工大学 | 题目：同上 | 类型：邀请报告
- 方向归属（主/次）：主 1；次 无
- 推荐配图页：p18（平坦功率剖面下 SNR_NLI 的 LPM 估计与 OSA 测量对比）

## 本批小结
1. LPM/PPE 已从实验室走向实用化，研究焦点转向“细分辨率”与“低复杂度”：BUPT-TSVD 把空间步长压到 50 m（仿真）/75 m（实验），BUPT-Jiang 以 HD 数据 + 分布加权将 RMSE 从 3.8 dB 降到 0.32 dB 并减 75% 计算时间；Pilori 邀请报告称 LPM 已商业部署（第1、2篇及 Pilori）。
2. 接收端 DSP 监测能力横向扩展：一套相干接收数据可同时得到损耗异常定位、PDL 定位、WSS 滤波偏移、拉曼增益、NLI/SNR_NLI 估计，形成“几乎免费”的链路数字孪生与发射功率自动优化（Pilori；Jiang）。
3. 异质/未知光纤成为新痛点：大阪/NICT 用 IST 在 303 km 实验中区分 SSMF（16.3）与 NZ-DSF（4.0 ps/nm/km）并定位到半个 span 内；Pilori 的 1,483 km SSMF+PSCF 链路同样验证 LPM 对异质链路的 NLI 估计（大阪、Pilori）。
4. 监测正从相干延伸到 IM/DD：UESTC 的 BSNC 在 50 GBaud IM/DD 实验中把 MPI 检测极限从 26 dB 推到 40 dB SIR（提升 14 dB），定位精度 < ±6 mm，可用于 400G/lane 数据中心链路的早期故障告警（UESTC）。
5. 与传统 OTDR 相比，DSP 方法“无需专用探测硬件、在线无中断、低成本”，但精度受硬判决、粗步长、相位噪声、CPR 等实用约束限制，是本批各篇共同处理的问题（BUPT 两篇、UESTC、Pilori 引 Kaneko ECOC 2025 CPR 影响）。
6. 数据来源说明：本批 OCR 质量较差，标“OCR读数”的数值未经图片核对；共查看 12 张图片。
