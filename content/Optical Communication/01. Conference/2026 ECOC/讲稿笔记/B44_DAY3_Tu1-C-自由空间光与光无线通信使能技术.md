---
title: "B44 · DAY3 · Tu1-C-自由空间光与光无线通信使能技术"
tags:
  - ECOC2026
  - DAY3
---

### 0922-Tu1-C4-西湖大学-双偏振载波提取直检的448Gbps室内光无线接入.pdf
- 讲者/机构：Haojie Zhu 等，William Shieh（通讯作者）/ 西湖大学光通信与传感实验室、西湖光电研究院 | 题目：Cost-Effective 448-Gb/s Indoor Optical Wireless Access via Dual-Polarization Carrier-Extracted Direct Detection（p1 看图核实） | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（FSO/光无线）；次 3 Scale-out 高速/相干类技术（自相干、SiP滤波器）
- 核心主张：
  1. 载波与信号共传、接收端提取（自相干直检），无需接收端本振（LO）；SiP CROW滤波器提取载波。[p7][p11]
  2. 自由空间保偏良好，在所测静态对准室内LOS条件下不需要实时光学APC，仅保留数字4x4 MIMO。[p9][p10][p15]
  3. 演示9 m室内光无线链路448 Gb/s（PDM 16-QAM OFDM），接收灵敏度-25 dBm。[p15]
- 关键数据：
  - 448 Gb/s总速率；20% SD-FEC后净速率355.1 Gb/s；净频谱效率11.84 bit/s/Hz [p14]
  - 9 m室内LOS，灵敏度-25 dBm（20% SD-FEC）；对应入射自由空间光功率约-19 dBm，远低于人眼安全限10 dBm（结论页称29 dB余量）[p14][p15]
  - 波长1550 nm，PDM 16-QAM OFDM，2048点DFT，每偏振1434个数据子载波；120 GSa/s AWG，80 GSa/s实时示波器；发射入自由空间<0 dBm [p12]
  - CROW滤波器：两耦合环，FSR 0.8 nm，20-dB带宽4.48 GHz，消光比60 dB，信号保护带4 GHz，芯片耦合损耗约11 dB [p11]
  - 数字MIMO：13-tap T/2间隔4x4实数FFE，NLMS，每40个OFDM符号一个已知符号 [p10]
  - 偏振稳定性佐证：引用OFC 2026 ThIE.2，800 m户外链路监测60天，偏振旋转角标准差0.77°(夜)/2.22°(日照)/2.21°(雨)；实验室12 h Stokes参数无可见漂移 [p8]
  - BER对ROP曲线：ROP -28到-16 dBm，CSPR=0 dB与2 dB两条；-24 dBm处约0.014–0.018，低于20% SD-FEC门限（约0.024，读图估计）[p14]
  - 载波SOP仅初始化时调整一次；去掉芯片耦合补偿EDFA后可全集成 [p12]
- 提到的公司/客户/产品/标准：DFB激光器、DP-IQ调制器、EDFA、光学90°混频器、BPD、SiP；20% SD-FEC；人眼安全标准
- 与业界对比或记录声明（SOTA/首次/record）：未见明确"record/首次"声明；仅对比IM/DD（结构简单低成本但一维、容量受限、C波段受色散劣化）与相干（全场恢复、高灵敏度可数字补偿色散，但需昂贵LO、DSP复杂耗电）（看图核实）[p6]
- 推荐配图页：p11（CROW滤波器芯片与传输响应，含60 dB消光、4.48 GHz带宽）；p14（BER-ROP曲线与星座图及448/355.1 Gb/s指标）

### 0922-Tu1-C5-KDDIResearch-光子晶体面发射激光器做自由空间光通信.pdf
- 讲者/机构：Shota Ishimura 等（KDDI Research；京都大学 Noda 组；Chitose科技大学） | 题目：Free-Space Optical Communication using Photonic-Crystal Surface-Emitting Lasers | 类型：邀请报告（综述+自家成果，引用多篇已发表工作；类型为推断）
- 方向归属（主/次）：主 5 固定与无线接入（FSO）；次 3 光源
- 核心主张：
  1. 用PCSEL可把FSO发射机做小：瓦级功率、极窄发散角，可省去外置光纤放大器（EDFA/YDFA）与笨重透镜。[p9][p12][p35]
  2. PCSEL大面积单模振荡，兼具高功率、高光束质量、小发散角。[p19]
  3. 通过提高容量与灵敏度（多电平调制、利用啁啾做调频+相干检测）推进PCSEL-FSO。[p35]
- 关键数据：
  - 典型光源对比：EEL发散角约5°x30°、功率约100 mW；VCSEL阵列约10°x10°、>约100 mW但合束质量差；PCSEL发散角<0.2°x0.2°、功率>1 W [p10][p11][p12]
  - 500 µm直径PCSEL，波长943.7 nm，I-L曲线在约2.4 A下输出约1 W以上；远场发散角标尺0.5° [p21]
  - 首个瓦级FSO演示（JLT 2023）：发射1 W，接收50 mW，64QAM OFDM，AWG 65 GS/s，FFT 2048，带宽480/864 MHz，探测器3-dB带宽2 GHz；因冷却效率与驱动电路限制为QCW驱动、带宽<1 GHz [p22][p24]
  - 改进驱动后（Optica 2024）：带宽由约600 MHz提升到1–8 GHz（读自幻灯片），冷却由热电改水冷；实现瓦级输出+直接调制几GHz [p25][p26]
  - 多电平调制：2 Gbaud 64QAM（12 Gbps），20 dB衰减下BER 0.06、EVM 6.9%；1 Gbaud下QPSK 2/16QAM 4/64QAM 6/256QAM 8 Gbit/s；接收光功率衰减约20 dB（等效500 m自由空间）时达16 Gbit/s [p27]
  - 卫星链路预算表（引自Mata Calvo 2019）：总链路损耗LEO约-73.1 dB，MEO约-89.5/-81.3 dB，GEO约-75.3 dB；自由空间损耗-262.8/-285.3/-290.0 dB [p28]
  - 此前直接调制直检链路预算35 dB；目标>80 dB需再扩展45 dB，路径：频率调制+相干检测 [p29]
  - CW下PCSEL线宽约30 kHz（FM噪声谱，读自幻灯片，较小）；利用电流调制啁啾把PCSEL当高功率FM发射机 [p30][p31]
  - 发射功率29 dBm；输入RF电流40/80/120 mApp；外差检测+离线DSP [p32][p33]
  - 结果：0.5 Gbaud与1 Gbaud分别达83 dB与78 dB链路预算（20% OH SD-FEC），无光纤放大器；对应接收功率约-54至-46 dBm量级（读图，误差较大）[p34]
- 提到的公司/客户/产品/标准：KDDI Research；Thorlabs LDM56/M（驱动/封装，OCR识别）；EDFA/YDFA；LEO/MEO/GEO卫星链路；LIDAR与激光加工（PCSEL原应用）
- 与业界对比或记录声明（SOTA/首次/record）：幻灯片标题称"世界首个采用PCSEL的瓦级FSO演示"[p21]；ECOC2023 PDP结果83/78 dB链路预算无光纤放大器 [p34]
- 推荐配图页：p12（EEL/VCSEL/PCSEL三种光源发散角与功率对比）；p34（链路预算83/78 dB的BER曲线）；p27（多电平调制EVM与星座）

## 本批小结
1. 两篇均把FSO/光无线推向"去掉接收端/发射端昂贵器件"：西湖大学去掉接收本振与实时光学偏振控制（自相干+数字MIMO），KDDI去掉发射端光纤放大器与透镜（PCSEL）。（C4、C5）
2. 两者面向不同场景与量级：室内9 m、448 Gb/s（1550 nm，功率<0 dBm，满足人眼安全）对比卫星级>80 dB链路预算、仅0.5–1 Gbaud（943.7 nm，29 dBm发射）；速率与预算呈强烈权衡。（C4 p14 vs C5 p34）
3. 相干/自相干接收思路在FSO中共同出现：C4用载波共传提取，C5用外差相干检测提升灵敏度（约45 dB预算扩展路径）。（C4 p7；C5 p29、p33）
4. 偏振在自由空间中稳定被作为PDM可行性的前提：C4引用800 m户外60天监测（旋转角标准差0.77°–2.22°）支撑去APC，但结论限定于静态对准室内LOS，户外仍待验证。（C4 p8、p15）
5. 光源带宽/热管理是PCSEL走向高速的瓶颈：QCW与<1 GHz驱动限制，改进后1–8 GHz水冷，仍远低于电信级IM/DD速率。（C5 p24–p26）
