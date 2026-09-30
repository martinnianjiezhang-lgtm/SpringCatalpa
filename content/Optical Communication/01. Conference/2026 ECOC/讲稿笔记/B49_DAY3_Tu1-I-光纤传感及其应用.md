---
title: "B49 · DAY3 · Tu1-I-光纤传感及其应用"
tags:
  - ECOC2026
  - DAY3
---

### 0922-Tu1-I2-Nokia-偏振噪声各向异性增强海底相干应答器地震检测.pdf
- 讲者/机构：Mohammad M. Hosseini 等（Nokia Strategic Architecture & Engineering；合作：L'Aquila 大学 Mecozzi、Sparkle）| 题目：State-of-Polarization Sensing with Coherent Transponders in Live Submarine Links: Noise Analysis, Processing Improvements and Practical Implications | 类型：邀请报告
- 方向归属（主/次）：主 6（光纤传感/SOP 地震检测）；次 1（海缆相干）
- 核心主张：
  1. 相干接收机 DSP 均衡器本身提取 2×2 Jones 矩阵（公共相位、幅度、偏振旋转），无需额外硬件即可做海缆路径积分传感。
  2. 海缆背景噪声在偏振旋转矢量空间中是各向异性的，会掩盖地震信号；地震扰动更接近各向同性。
  3. 方案：把表示坐标旋转到噪声协方差特征向量（PCA）方向，选噪声最低轴，提高检测清晰度；已在现网地中海验证。
- 关键数据：
  - 8 个现场部署应答器 + 2 个实验室背靠背应答器，采样率 2 Hz [p8]
  - 4 次地震：Event1 2025-05-22 03:19:35 UTC Mw6.2；Event2 2025-05-13 22:51:15 Mw6.0；Event3 2025-07-23 13:26:54 Mw5.1；Event4 2025-07-07 17:46:04 Mw5.1 [p8]
  - 路由距离：GAR–ROM 251 km；ATH–CHA 274 km；MAR2–PAL2 885 km；PAL1–MIL 887 km；CAT2–HAI 1879 km；CAT1–TAV 1892 km [p8]
  - SNR 增益"最高达 16 dB"；柱图各链路/事件 anisotropy-aware SNR（dB，读柱顶）：ATH-Event1 35，CAT02-Event1 22，CHA-Event1 43，CAT01-Event2 36，CAT02-Event2 26，HAI-Event3 16，HAI-Event4 25；对应基线 20、15、27、29、12、14、19 dB（看图核实）[p9]
  - 案例：2023-02-06 土叙地震双震 Mw7.8 与 Mw7.6，相距 95 km、间隔 9 h，MedNautilus 缆（Catania–Haifa）应答器记录到偏振旋转，与陆上地震仪及验潮站对时 [p14]
- 提到的公司/客户/产品/标准：Nokia ICE6 相干转发器；Sparkle 海缆网络；MedNautilus 缆；Research Square 预印本；ECSTATIC 项目标识
- 与业界对比或记录声明（SOTA/首次/record）：讲者称在现网（live）地中海海缆、真实地震下验证有效；SNR 增益最高 16 dB [p9,p10]
- 推荐配图页：p9（各事件/链路 SNR 柱图，基线 vs 各向异性感知）；p8（地中海网络与四次地震位置）

### 0922-Tu1-I3-Nokia-海底网络路径积分偏振旋转特征与缆路几何.pdf
- 讲者/机构：Nokia（讲者姓名页面未显示）| 题目：Path-integrated polarization rotation signatures and cable geometry in subsea networks（中文题名对应；英文原题页未拍到，此为据文件名推译；p1 看图核实为 "Fiber–Seism Interaction & Analytical Model" 页）| 类型：邀请报告
- 方向归属（主/次）：主 6；次 1
- 核心主张：
  1. 光纤段是把三维地面运动投影到局部光纤切线方向的方向性应变计；长海缆对动态应变做非相干（平方律）累加。
  2. 径向波（Rayleigh）耦合强且对波源方位依赖小；横向波（Love/T 型）缆的方向性窄，存在盲区。
  3. 长时事件覆盖整条缆路，方向图更宽更平滑。
- 关键数据：
  - 模型：|Γ_R,T|² = ∫A(r)² R_R,T(θ)² [(ŝ·k̂)(ŝ·p̂)]² ds，且 |Γ|² ∝ |Δφ|²（A=路径损耗，R=辐射花样）[p2]
  - 土叙双震位于 T 波灵敏度较低（约 -10 dB）区域，故预期与 R 波对应更好 [p2]
  - 灵敏度色标范围约 -15 至 +10 dB；60 s 事件与长事件的 R/T 型方向图对比，Catania(Rx)–Haifa(Tx) [p2]
  - p3 为模型与测量对应：Catania–Haifa 海缆与 Mw 7.8 震中、ΔΦ 时序（0–1500 s）与频谱、Rayleigh/Love 辐射方向图及沿缆投影；小字数值看图仍不可读 [p3]
- 提到的公司/客户/产品/标准：Nokia；地震台 ZKR 等（p1 图注）；Catania–Haifa 缆
- 与业界对比或记录声明（SOTA/首次/record）：未见明确 record 声明
- 推荐配图页：p2（R 型/T 型波、短/长事件下缆路灵敏度方向图）

### 0922-Tu1-I4-Aston大学-基于SOP的实时地震检测的限制与机会.pdf
- 讲者/机构：Melo 等（Aston University；合作 L'Aquila 大学、Nokia–Sparkle；欧盟 ECSTATIC 项目）| 题目：Limits and opportunities of real-time earthquake detection from SOP data（英文原题页未拍到，为据文件名推译；p1 看图核实为动机页 "Can every submarine cable become a seismometer?"）| 类型：学术论文
- 方向归属（主/次）：主 6；次 1
- 核心主张：
  1. 三个限制三个答案：无标注 SOP 数据 -> 物理信息标注；检测须快 -> 短滑窗；须能在边缘运行 -> 轻量 MA/P95 检测器。
  2. 检测性能受 SNR 而非阈值限制：高 SNR 约 10 s 延迟，低 SNR 需数分钟。
- 关键数据：
  - 数据集：798 次地震（公共目录如 IRIS，含近场/区域/远震），Catania–Haifa MedNautilus 约 2,000 km，商用相干转发器 [p4]
  - 标注：TauP/AK135 在缆上 360 个点预测各震相到时，GT 取所有震相包络；事件例：M5.8，深度 45.5 km，缆上最近点距震中约 115 km，窗口 17.3–264.0 s [p5,p7,p15]
  - 检测：当前窗口 vs 120 s 参考窗口（结论页写 10 s vs 120 s），每 0.5 s 滑动（2 Hz），比值>4 或 10，最近 10 步中 ≥9 票判事件 [p10,p15]
  - 性能：比值 10 使低 SNR（≤3 dB）误报约减半；延迟约 250 s（SNR≤3 dB）对约 10 s（SNR≥6 dB），约 25 倍 [p13]
  - 798 事件中 95% SNR 低于 1.64 dB；每窗约 50 ms，约 5% CPU，最高 20 Hz 采样，运行在 Raspberry Pi、输入为 Jones 矩阵流 [p15]
  - 高 SNR 箱（18–21 dB）检测准确率：比值 4 约 0.8，比值 10 约 0.6（图读数，纵轴标 %，数值近似）[p13]
- 提到的公司/客户/产品/标准：Nokia、Sparkle、IRIS 目录、TauP/AK135 模型、Raspberry Pi、Zenodo 数据集（Mecozzi et al., Optica 2026）
- 与业界对比或记录声明（SOTA/首次/record）：未见 record 声明；强调多数事件低 SNR
- 推荐配图页：p13（三联图：准确率、误报、延迟随 SNR）；p15（结论三行表）

### 0922-Tu1-I5-NECLabs-地热井被动分布式声波传感速度剖面.pdf
- 讲者/机构：Zehao Wang（Duke 大学）等，含 NEC Laboratories America、Enegis、Cornell、Horowitz Consulting | 题目：Passive Distributed Acoustic Sensing for Borehole Seismic Velocity Profiling: A 3 km Geothermal Well Field Trial | 类型：学术论文
- 方向归属（主/次）：主 6（DAS）；次 无
- 核心主张：
  1. 在 3 km 地热井上做被动井内 DAS 速度剖面现场试验。
  2. 提出反卷积干涉 + 相位加权叠加（PWS），在 0–2 km 内可靠恢复，MAE < 250 m/s。
  3. 展示永久安装井内光纤做连续、无源地下速度监测的可能性。
- 关键数据：
  - 现场：Newberry（美国俄勒冈）地热井；2.74 km 单模光纤下井；NEC SpectralWave LS3300 DAS；500 空间通道，6.52 m gauge length，1 kHz 采样，1550.12 nm；标定炮（约 3 km）作真值 [p9]
  - 三种条件：标定炮（主动）/ 水泵开（半被动）/ 水泵关（被动）；预处理 5–80 Hz 带通，F-K 滤波保留近垂直 P 波，层剥离 semblance 选速度 [p6,p11]
  - MAE（m/s，对标定炮）：ANCC / Deconv 泵开 / Deconv 泵关：0–0.5 km 994/285/356；0.5–1.0 km 1302/124/79；1.0–1.5 km 1403/236/241；1.5–2.0 km 1893/251/224；2.0–2.5 km 2477/834/804；平均 0–2.0 km 1398/224/225；平均 0–2.5 km 1647/360/352 [p12]
  - 约 2.0–2.5 km 以深方法失效（图中箭头"After certain depth does not work"）[p12]
  - ANCC 在被动井内 DAS 下无效（假设各向同性扩散噪声，实际为方向性噪声）[p7,p12]
- 提到的公司/客户/产品/标准：NEC SpectralWave LS3300；DOE Newberry EGS 项目（DE-EE0002777）
- 与业界对比或记录声明（SOTA/首次/record）：对比既有主动井内 DAS（两井、振动车）与被动地表 DAS（28 km 地表光纤）[p4]；未称 record
- 推荐配图页：p12（速度剖面曲线与 MAE 表）

### 0922-Tu1-I6-中国联通-100G相干系统瞬时SOP波动的实时跟踪与定位.pdf
- 讲者/机构：Yu Tang 等（中国联通 & 华中科技大学，tangy186@chinaunicom.cn）| 题目：Real-time Tracking and Localization of Rapid Instantaneous SOP Fluctuations for 100G Coherent System over FPGA（p1 看图核实，2026-09-22）| 类型：学术论文
- 方向归属（主/次）：主 6；次 1（oDSP）
- 核心主张：
  1. 两级自适应均衡器（AEQ）：第一级补偿残余色散，第二级偏振解复用；从 AEQ 抽头提取 Stokes 矢量，加快收敛与跟踪。
  2. 环回（两个光环形器）把双向路径变为 TDOA 测量，实现快速 SOP 事件定位；可跨多跨与放大器。
  3. 与现有 OTN 架构兼容，具备通信感知一体化优势。
- 关键数据：
  - 平台：100G 双偏振 16QAM，Xilinx Virtex UltraScale+ XCVU13P FPGA；接收侧 oDSP 实现；偏振扰偏器产生 5 或 1 Mrad/s 旋转，持续 200 ns，周期 35 μs [p8,p9]
  - 结果（总长 L、事件位置 L1、误差）：单跨 L=4.024 km，L1≈0 km，5 Mrad/s 误差 -0.036 km；1 Mrad/s 误差 0.023 km；单跨双点振动 L=8.116 km，L1≈0 与 2.046 km，误差 -0.021 与 -0.023 km；两跨双点 L=86.597 km，L1≈40.153 与 42.2885 km，误差 0.053 与 0.015 km [p9]
  - 重复实验定位误差小于 115 m [p9,p11]
  - 时钟同步：1588v2 PTP，Class C 单跨时间误差约 30 ns [p7]
  - 误差来源：采样、扰动时钟不同步、光纤测量误差；跳变幅度与 SOP 旋转速度不成正比；实际部署需 OTN 额外开销上报快速旋转事件时间戳 [p10]
- 提到的公司/客户/产品/标准：Xilinx Virtex UltraScale+ XCVU13P；OTN；IEEE 1588v2 PTP；对比方案类别：导频法/盲法、AEQ 独立/依赖、双向/环回架构 [p4]
- 与业界对比或记录声明（SOTA/首次/record）：称实时 FPGA 100G 系统中实现，定位误差 <115 m；未称 record [p11]
- 推荐配图页：p9（四种条件下 SOP 跳变与定位误差）；p8（FPGA 实验台）

## 本批小结
1. 相干转发器 DSP 的 Jones 矩阵/SOP 已成为"零硬件成本"传感手段，本批 I2、I3、I4（Nokia/Sparkle/Aston）都基于同一 MedNautilus 与 Sparkle 现网数据，中国联通 I6 则在 oDSP/FPGA 上做实时化。
2. 噪声/SNR 是瓶颈：I2 通过旋转到最安静的噪声本征轴，SNR 提升最高 16 dB；I4 指出 798 事件中 95% SNR<1.64 dB，检测延迟由 SNR 决定（约 250 s 对 10 s），而非阈值。
3. 缆路几何决定灵敏度：I3 显示 Rayleigh 波耦合强、Love/T 波存在盲区，土叙双震落在约 -10 dB 区域；I2 案例与之对应。
4. 从"离线分析"走向"边缘实时"：I4 的检测器在 Raspberry Pi 上每窗约 50 ms、约 5% CPU；I6 用 FPGA 实时跟踪 SOP 并环回 TDOA 定位到 <115 m，但商用还需 OTN 开销上报时间戳（I6）。
5. 非海缆 DAS 方向：I5 表明被动井内 DAS 需用反卷积干涉+PWS 才能替代标定炮，0–2 km MAE 约 225 m/s，2.0–2.5 km 以深失效。
