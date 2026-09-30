---
title: "B31 · DAY2 · Mo5-A-分布式光传感"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo5-A1-EPFL-分布式光纤传感-优雅物理如何长成智能系统.pdf
- 讲者/机构：Prof. Luc Thévenaz（荣休），EPFL 光纤光学组（GFO），瑞士洛桑 | 题目：Tutorial ECOC'2026 Mo5-A1: Distributed Optical Fibre Sensing — Where Elegant Physics Gives Rise to Smart Systems（p1 看图核实） | 类型：邀请报告（教程）
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS；次 无
- 核心主张（1–3条，用讲者自己的结论页原意）：
  - 文末为 φ-OTDR 相关页（p32–p34），未见明确的总结页，以下为各页论点：
  - 分布式光纤传感分两类：线性（弹性/非弹性）背向散射（Raman-OTDR、Brillouin-OTDR、Rayleigh φ-OTDR）与非线性相互作用（Brillouin-OTDA，两束反向波通过动态Bragg光栅耦合）[p4]
  - 传感过程对激活脉冲的消耗必须小于Rayleigh散射本身的衰减，否则测量有偏、传感距离缩短 [p6]
  - 检测噪声必须由信号噪声（散射噪声、RIN）主导，因此需在检测端放大微弱背向信号 [p12]
- 关键数据（每条带单位与条件，末尾标 [pN]）：
  - Raman约比Brillouin弱100倍，Brillouin又约比Rayleigh弱100倍 [p8]
  - 标准单模光纤中Rayleigh背向散射的回收（response）效率典型仅0.15% [p8]
  - Brillouin传感的耦合增益约2.5%（1 m空间分辨率、100 mW峰值泵浦） [p11]
  - 激活脉冲峰值功率上限：调制不稳定性（反常色散）约100 mW，前向Raman（正常色散）约300 mW，均为超长光纤 [p12]
  - CW探测光上限：受激自发Brillouin约1 mW，激活脉冲耗尽与频谱畸变约0.3 mW，均为超长光纤 [p12]
  - Raman斯托克斯位移约13.2 THz（平均声子数 0.14，反斯托克斯 < 斯托克斯）、Brillouin 11 GHz（平均声子数 570，二者相当）；Raman 反斯托克斯与瑞利间隔约12.5 THz/100 nm@1550 nm [p19, p20，看图核实]
  - Raman测温灵敏度@300 K：0.8 %/K；Brillouin温度系数约1 MHz/℃（-25/30/90 ℃ 时布里渊峰约 11.45/11.52/11.58 GHz）（看图核实）[p20, p24]
  - Brillouin光时域分析演示：5 cm空间分辨率，5 cm段νB约10.303 GHz，其余约10.4019 GHz，位置约4557 m [p29]
  - 图p12噪声曲线：横轴输入功率-35至-5 dBm，噪声标准差约 3.9×10^-7 A 平坦至约 -15 dBm，之后上升至 -5 dBm 时约 4.35×10^-7 A（实测与计算吻合，看图核实）；配置要点：泵浦峰值功率止于调制不稳定（约 100 mW）或前向拉曼（约 300 mW）出现前，CW 探测光低于放大自发布里渊（约 1 mW）与泵浦耗尽（约 0.3 mW）门限 [p12]
- 提到的公司/客户/产品/标准：Omnisens（Marc Niklés 图源）；British Telecom Research Labs（Peter Healey，1980年代Rayleigh背向散射脉冲响应）；R. Feynman《Lectures on Physics II》
- 与业界对比或记录声明（SOTA/首次/record）：无（教程，无record声明）
- 推荐配图页：p12（激活脉冲功率上限与检测噪声优化配置，含噪声-输入功率曲线）；p4（两类分布式传感分类）；p29（Brillouin OTDA 5 cm分辨率实测）

### 0921-Mo5-A2-帕多瓦大学与NICT-688km有中继链路上的瑞利指纹DAS与15Tb-s共传.pdf
- 讲者/机构：D. Orsuti 等（帕多瓦大学信息工程系；NICT光子网络实验室；坎皮纳斯大学）| 题目：Rayleigh Fingerprint-Based DAS over a 688-km Repeatered Link with Co-Propagating 15-Tb/s WDM | 类型：学术论文
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS；次 1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件
- 核心主张（1–3条，用讲者自己的结论页原意）：
  - 新DAS方案：高能量、宽带宽脉冲加互相关DSP，提升DAS灵敏度 [p12]
  - 有中继DAS的挑战是SNR：后向路径ASE噪声累积使全链路SNR下降，从而限制最大跨段长度 [p10, p12]
  - DAS对电信信道SNR有明显劣化（随DAS峰值功率增加而增大） [p12]
- 关键数据（每条带单位与条件，末尾标 [pN]）：
  - 方案对比：φ-OTDR 脉宽约100 ns、chirp带宽约20 MHz，单跨<40 km；Rayleigh指纹DAS 脉宽约100 ns、带宽≥500 MHz，DSP为时延估计，单跨<40 km，对电信XPM高；脉冲压缩φ-OTDR 脉宽约10 µs、带宽约50 MHz，单跨170–190 km，XPM中到低，适合中继链路 [p4]
  - 本工作传感脉冲：30 µs、500 MHz带宽、λDAS=1550.12 nm；前后各加8 µs平滑dummy脉冲以减小对电信信道的XPM；采集2 GS/s ADC [p9]
  - 实验链路：C波段、50 GHz间隔，46×46 GBaud PM-16QAM；总链路688 km，最多14跨（图示2/6/10/14跨；含约598 km实验室光纤加2×45 km，另有field fiber，标注不完整） [p8, p9, p10]
  - 抖动噪声：单跨110 km，激光频率噪声@1 kHz：>32.5、32.5、15.0 Hz/√Hz三档；脉冲由4 µs增至30 µs以提高能量；图中应变色标±20 nε [p7]
  - 电信接收：20 nm带宽（1542–1562 nm），传感陷波位于约1550 nm；总数据率15.1 Tb/s；单信道GMI约345–350 Gb/s量级、译码后约330–335 Gb/s量级，OSNR约18–24 dB范围（读图估计） [p11]
  - 结论页：第14跨（约680–688 km）可见应变信号，20 m gauge；理论SNR随距离锯齿下降，红虚线3 dB阈值；DAS峰值功率1.6/3.6/5.6 dBm下，电信SNR约14 dB（OFF）降至约12.5–13 dB（5.6 dBm，有cycle slip） [p12]
- 提到的公司/客户/产品/标准：NICT；Zuyuan He组（上海交大，非匹配滤波DAS，2019）；Pastor-Graells 2016（首个相关型DAS）；Hartog US 9,170,149；Wang 2015；E. Ip OFC2022（dummy脉冲抑制XPM）；R. S. Luis ECOC2025（软判FEC）；Fan Photon. Res. 2023与Vidal-Moreno Opt. Express 2023（SNR模型）
- 与业界对比或记录声明（SOTA/首次/record）：题目 "Rayleigh Fingerprint-Based DAS over a 688-km Repeatered Link with Co-Propagating 15-Tb/s WDM Transmission"（Padova/NICT/Campinas）；共传总速率 15.1 Tb/s（1542–1562 nm，20 nm 带宽，中间留传感陷波）；未见讲者明写“record/首次”字样（p1, p11，看图核实）
- 推荐配图页：p10（14跨链路强度/测得SNR/理论SNR三联图）；p11（电信性能：陷波频谱与15.1 Tb/s数据率）；p12（结论：应变时空图、SNR挑战、电信SNR劣化）；p4（三种DAS方案对比表）

### 0921-Mo5-待定-Sikt-在用业务纤上的L波段DAS与暗纤C波段DAS对比.pdf
- 讲者/机构：Kurosh Bozorgebrahimi、Jan Kristoffer Brenne（Sikt，挪威；页面LOGO含ASN） | 题目：Performance of L-band DAS on Live Traffic Fiber Compared to C-band DAS Over Dark Fiber | 类型：学术论文
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS；次 1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件
- 核心主张（1–3条，用讲者自己的结论页原意）：
  - 无需暗纤：运营商可在L波段部署DAS，与C波段DWDM传输共存 [p14]
  - 三种调制格式（OOK、QPSK、16QAM）的数据信道在pre-FEC BER、post-FEC BER、Q-margin上无明显劣化 [p14]
  - L波段DAS与在网C波段DWDM业务共传，可获得与暗纤C波段DAS相同的量程与灵敏度 [p14]
- 关键数据（每条带单位与条件，末尾标 [pN]）：
  - 现场：斯瓦尔巴（Svalbard），2023年秋；Longyearbyen至Ny-Ålesund两条250 km无中继海缆，G.652.D；近Ny-Ålesund段水深约250 m，近岸浅水段100 m未埋设 [p4]
  - 两台ASN OptoDAS均位于Ny-Ålesund：C波段1536.6 nm（暗纤，图中标1537 nm），L波段1577.9 nm经C/L滤波器合入在网光纤；DAS与业务同向传输，Raman泵浦反向（1434 nm与1455 nm）；业务C波段1529–1568 nm，OTDR 1610 nm；监测5个在网信道 [p5]
  - L波段DAS有10 dB劣势：L波段一路单向连接损耗12 dB（跳线链、3 dB分路器、1 km额外光纤、两个ODF、C/L滤波器），C波段仅2 dB；10 dB差约相当于损失50 km传感距离；永久熔接安装时C/L滤波器仅剩0.5 dB；在10 km发射盘纤上两台数据质量相同 [p6, p7]
  - 地震事件：2023-11-14T11:19:31，M3.3，距电缆约100 km，两路数据均清晰可见，幅度相近；RMS数据带宽3–25 Hz [p8]
  - 询问方式为频率扫描询问（FSI，线性调频+解调脉冲压缩）：占空比提高>1000倍且空间分辨率不变；光损耗预算提高>30 dB [p9]
  - 监测信道：2×1G（OOK）、2×200G（62 GBaud QPSK，SDFEC-G2）、1×300G（84.23 GBaud 16QAM，SDFEC-V）；用光谱仪监测L波段影响 [p10]
  - 14天共存监测：pre-FEC/post-FEC BER与Q-margin无劣化 [p11]
  - 新增Skjervøy部署（2025-11-19）：C/L滤波器永久熔接，DAS满功率接入在网光纤；16QAM信道Q-margin约3.63–3.83（图标注3.83），pre-FEC BER约0.00212，插入滤波器与开启L波段DAS前后基本不变（图中间段为滤波器插入期读数为0，属操作过程） [p12]
  - Skjervøy另示座头鲸类信号（“Fin whale and vessel”，2025-12-05） [p13]
- 提到的公司/客户/产品/标准：ASN OptoDAS；Sikt；G.652.D；SDFEC-G2、SDFEC-V；ROADM/DWDM；Raman放大
- 与业界对比或记录声明（SOTA/首次/record）：“据我们所知首次验证”DAS与在网生产DWDM业务光纤共存，且业务信道光性能在测试前后与期间均受监测；并与同一海缆平行暗纤上的C波段DAS对比 [p3]
- 推荐配图页：p5（光学布局：L波段DAS经C/L滤波器合入在网光纤，C波段暗纤对照）；p12（Skjervøy熔接滤波器后Q-margin与pre-FEC BER无变化）；p7（OTDR迹线对比12 dB损耗）

## 本批小结
- 三讲同属光纤传感（DAS）：共同主题是让传感与在网光通信共存。Sikt用L波段+C/L滤波器避开C波段业务；Padova/NICT在C波段业务带内开1550.12 nm陷波，开出约20 nm 15.1 Tb/s WDM共传（来自A2、Sikt）。
- 共存的代价可以量化：Padova报告DAS峰值功率1.6→5.6 dBm使电信SNR由约14 dB降至约12.5–13 dB，用平滑dummy脉冲抑制XPM；Sikt在L波段则14天无BER/Q-margin劣化（A2、Sikt）。
- 提高DAS距离预算靠脉冲压缩类调制：Sikt的FSI（占空比>1000倍、光预算+30 dB）与Padova的500 MHz宽带chirp加互相关DSP，思路一致（A2、Sikt）。
- 有中继（EDFA）链路是难点：后向路径ASE累积使SNR随跨数下降，Padova在14跨688 km仍能在末跨读出应变，但SNR接近3 dB阈值（A2）。
- EPFL教程给出物理上限：Rayleigh回收效率仅0.15%，激活脉冲功率受调制不稳定性（约100 mW）和前向Raman（约300 mW）限制，解释了为何工程上转向脉冲压缩与放大检测（A1；对照A2、Sikt）。
