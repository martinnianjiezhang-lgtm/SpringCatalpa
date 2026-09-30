---
title: "B50 · DAY3 · Tu3-A-面向光通信系统的AI与先进处理"
tags:
  - ECOC2026
  - DAY3
---

### 0922-Tu3-A1-丹麦科技大学-AI时代的通信工程与收发机优化.pdf（第1–56页）
- 讲者/机构：Darko Zibar（DTU Electro，Machine Learning in Photonic Systems group, MLiPS；p1 看图核实） | 题目：Tutorial: Communication engineering in the age of AI: (optimization of optical transceivers)（会场 Tu3-A “AI and advanced processing for optical communication systems”） | 类型：邀请报告（教程式综述）
- 方向归属（主/次）：主 1（AI光网络/oDSP/高波特率器件）；次 3（Scale-out 调制器/DML）
- 核心主张：
  1. AI/ML 是光通信系统优化的强力工具；用于优化的数据驱动模型需同时满足：准确、训练与推理计算高效、可泛化、可微 [p56]
  2. 强化学习（RL）是在线优化的通用方法，可发现新解并计入所有实际限制；但要求系统相对稳定，自动化是落地关键 [p56]
  3. 端到端学习（波形/星座整形/滤波器联合优化）可联合优化收发两端 DSP 模块 [p35]；RL 智能体是“下一个研究前沿” [p54]
- 关键数据：
  - 行业趋势：面向AI数据中心的短距互连；>200 Gbaud；1.6 Tb/s 每波长及以上；调制器带宽>100 GHz；优化指标 bits/s/Hz/W/A [p4–p5]
  - 挑战：>100 Gbaud 时均衡增强相位噪声（EEPN）相关；DAC/ADC 频率相关特性需建模 [p5]
  - 基线（NLIN vs SSFM）：10×100 km，5×32 GBd @50 GHz，RRC 脉冲；对比 BP/CKF/RL/IPM 优化星座 [p41]
  - 量化实验：M=256，LDPC FEC，5×WDM，32 GBd，50 GHz 间隔，10×100 km，EDFA NF 5 dB；比较 256QAM 与 256 几何整形随 ADC/DAC 比特数（横轴3–8 bit）的 GMI/MI [p42]
  - DML 端到端学习（S. Hernandez et al., OFC 2025）背靠背：20 GBaud 与 30 GBaud 下 AE 的 SER 均低于 FFE、VNLE；20 GBaud 图上 AE 约 1e-4（FFE约3e-4，VNLE约1.6e-4，PRF≈2 dBm），30 GBaud 图上 AE 约1e-3量级（FFE约4e-3，VNLE约1.6e-3）；数值读自曲线，精度有限 [p53]
  - RL 引导发射端优化（Ouhan Huang…Junwen Zhang，短距 IM/DD 自由空间，30 m，TFLN-MZM）：横轴约95–115 GBaud 与140–160 GBaud 两段；Agent-guided Pre-EQ 的 AIR 约在 105 GBaud 达约190+ Gb/s，115 GBaud 约160 Gb/s；PAM4基线在115 GBaud 降至约120 Gb/s；图右段 OOK 基线在约140–160 GBaud 之间 AIR 约137→147 Gb/s（曲线读数，非精确值）[p55]
  - RL 控制微环光频梳：CW泵浦+EDFA+微环，RL 智能体通过压电电压改变泵浦失谐；光谱 sech² 拟合 R²=0.9915，覆盖约1420–1700 nm（读图）[p14；论文 V. Sankar，submitted to Optica]
- 提到的公司/客户/产品/标准：Ciena（Yankov）、Acacia（Hernandez）、AdTran（Jovanovic）、Keysight（6G 示意图）、KP4-FEC、PyTorch、AWG/TFLN-MZM
- 与业界对比或记录声明（SOTA/首次/record）：无明确 record 声明；讲者强调 RL/端到端学习为“下一个前沿” [p54, p56]
- 推荐配图页：p53（DML端到端学习 SER 对比、眼图与频谱）；p55（RL引导 Tx 预均衡实验装置与 AIR 结果）；p14（RL 控制微环光频梳实验）

### 0922-Tu3-A2-香港中文大学-24x432Gbps每波的全光均衡实现免DSP光互连.pdf（第1–14页）
- 讲者/机构：Benshan Wang, Qiarong Xiao, Dongliang Wang, Yihao Chen, Tengji Xu, Li Fan, Shaojie Liu, Chaoran Huang* / 香港中文大学电子工程系 [p1] | 题目：24×432-Gbps/λ All-Optical Equalization for DSP-Free Optical Interconnects | 类型：学术论文（Tu3-A2）
- 方向归属（主/次）：主 3（Scale-out 224G/448G，免DSP）；次 1（AI光网络/光子信号处理）、4（LPO/CPO）
- 核心主张：
  1. 硅光集成的类神经形态光信号处理器（OSP）首次实现 >400 Gbps/λ 全光均衡，同时补偿收发机带宽限制与色散，达到“Beyond-BtB”性能 [p10, p13]
  2. 低功耗（<50 mW）、低时延（<75 ps），可编程支持不同波特率、调制格式与波长 [p13]
  3. 在 >400 Gbps 下传输能力优于先进 DSP [p12]
- 关键数据：
  - 动机：1.6T DSP 可插拔约25 W（3 nm）、约20 W（2 nm）；1.6T LPO 约10 W；64端口交换机配置可省640 W；无DSP的200G LPO 与 CPO 通常限制在 500 m 以内，400G 更短 [p4]；3 nm CMOS DSP 仅能把 112 Gbaud PAM4 的O波段边缘波长传输延伸到2 km [p3]
  - 架构：多抽头 IIR + 格型 FIR 滤波器，插入损耗<3 dB，单片集成于标准硅光平台 [p8]；前作 Science 392(6803) eady5344 (2026)：100 Gbaud PAM4、5 km、C 波段实时光均衡的首个全集成光子深度储备池处理器 [p7]
  - 实验：C 波段 2 km SMF；PAM4/PAM8；100–160 Gbaud；224 GSa/s AWG，256 GSa/s 示波器；使用3抽头 FFE 做时钟同步（AWG 与示波器采样率不匹配）；Keysight M8199B AWG 借用；先用峭度盲优化再 MSE 精调加速训练；带宽“Beyond-BtB”>70 GHz [p9, p13]
  - 结果（1550 nm，2 km SMF）：136 Gbaud PAM4 BER 2.79×10⁻³；136 Gbaud PAM8 BER 2.22×10⁻²；144 Gbaud PAM8 BER 4.07×10⁻²；分别对应支持 HD-FEC 360 Gbps、20% SD-FEC 408 Gbps、25% SD-FEC 432 Gbps；随速率升高增益收窄（噪声）[p10]
  - 多波长：24 个波长（200 GHz 间隔），覆盖整个 C 波段（约1528–1565 nm），2 km 光纤；24×144 Gbaud PAM8 = 10.36 Tbps [p11]
  - 对比：光均衡此前文献单波长速率在约110–310 Gbps/λ、聚合约0.3–1.5 Tbps；本工作约430 Gbps/λ、约10 Tbps（图读数）[p12]；O波段>40 km [p10]
- 提到的公司/客户/产品/标准：Broadcom（BCM83640-DIE 3 nm CMOS 1.6T (8:4) PAM-4 收发PHY，2026；CPO: Progress & The Road Ahead）、Keysight M8199B AWG、HD-FEC / SD-FEC 20% / 25%、LPO、CPO
- 与业界对比或记录声明（SOTA/首次/record）：First >400 Gbps/λ all-optical equalization；First demonstration of real-time optical equalization for over 400 Gbps/λ 2 km at C-band；outperform advanced DSP（对比 biGRU、Broadcom DSP chip、PNLE、NL-MLSE、FFE+VNLE(+MLSE)、DFE+MLSE 等，横轴400–600 Gbps/λ）[p10, p12]
- 推荐配图页：p10（BER vs 每波速率与眼图，BtB 对比）；p12（与光均衡/先进DSP的对比图）；p11（24波长 BER 与眼图）

### 0922-Tu3-A3-NokiaBellLabs-用时域酉变换生成220GBd相干波形.pdf（第1–15页）
- 讲者/机构：Nokia Bell Labs（署名引用 C. Deakin, X. Chen；讲者姓名本批页面未显示） | 题目：Generating 220 GBd coherent waveforms with spectro-temporal (time-domain) unitary transformations（英文原题页未拍到，据结论/参考文献页推断；p1 看图核实为动机页：传统相干调制基于开关，受 MZM 与 RF 驱动电光带宽限制且调制损耗 >25 dB；参考文献 J. Lightwave Technol. 44, 4880–4889 (2026)） | 类型：学术论文（Tu3-A3）
- 方向归属（主/次）：主 1（相干/高波特率器件）；次 3（调制器）
- 核心主张：
  1. 用光谱-时间酉变换（交替相位调制 + 色散）可无损生成高波特率相干光波形，不严格受调制器带宽限制 [p15]
  2. 仅用50 GHz 电带宽调制器生成最高 220 GBd 信号 [p15]
  3. 色散/布拉格光栅等元件已可集成（硅上布拉格光栅、环色散、TFLN 异质集成），但当前环回实验受损耗、非酉效应与环路相位稳定性限制 SNR [p14, p15]
- 关键数据：
  - 传统 IQ 调制“基于切换”，损耗高：>25 dB 调制损耗，受 MZM 与射频驱动电光带宽限制 [p1]
  - 酉矩阵 U = A₁HA₂HA₃H…AₙH（A为对角相位调制，H为固定模式混合矩阵，如傅里叶变换）；色散近似时域傅里叶变换 [p3, p4]
  - 优化：多目标（SNR 与平均射频驱动功率折中），使用 L-BFGS [p5]
  - 装置：单级用分立器件，光纤布拉格光栅色散 −100 ps/nm；体铌酸锂相位调制器 3 dB 带宽约30 GHz；DAC 带宽限制50 GHz [p6]；环回环路实现连续多级相位调制，环延迟144 ns（约29 m 标注），AOM 截取脉冲，EDFA 补偿环损，110 GHz 相干接收 [p7]
  - 结果（仅50 GHz 电带宽）：100 GBd 16-QAM，8级，SNR = 16.7 dB；220 GBd 16-QAM，10级，SNR = 11.8 dB [p8]
  - 趋势（N=6/8/10 级）：N=10 时射频驱动功率约3.7 dBm(100 GBd)→约8.6 dBm(220 GBd)；SNR 约18.4 dB(100 GBd)→11.8 dB(220 GBd)；NGMI 在220 GBd 约0.86，略高于阈值0.8456（对应码率0.7932 FEC）；N=8 到约180 GBd 超阈值，N=6 约140 GBd 后低于阈值；速率越高或级数越少所需驱动功率越大（读图，数值为估读）[p13]
- 提到的公司/客户/产品/标准：Nokia CSTAR-800（集成示意）、EOSpace 相位调制器、TFLN 异质集成、NGMI 阈值0.8456 / 码率0.7932 FEC（引用 Gené et al., OFC 2020 M3G.3）
- 与业界对比或记录声明（SOTA/首次/record）：未声明 record；强调“无损且带宽不受限”的调制思路，最高220 GBd [p15]
- 推荐配图页：p8（100/220 GBd 16-QAM 星座与谱）；p13（级数-符号率-驱动功率/SNR/NGMI 趋势）；p4（酉变换原理框图）

## 本批小结
1. AI/ML 在光通信中的角色分两层：离线数据驱动建模与端到端联合优化，以及在线 RL 优化。DTU 综述（A1）把 RL 视为“下一个前沿”，并给出光频梳控制、Tx 预均衡（30 m 自由空间，AIR 提升）两个实例；其前提是系统稳定和自动化（A1）。
2. “去DSP”路线出现明确的物理层替代：CUHK 的硅光深度储备池/IIR+FIR 光均衡器以<50 mW、<75 ps 实现>400 Gbps/λ（A2）；论据来自 3 nm DSP 的功耗（约20–25 W/1.6T）和 LPO/CPO 的 500 m 以内距离墙（A2）。与 A1 中“DAC/ADC、带宽限制、色散是主要损伤”的判断一致。
3. 带宽瓶颈的另一种绕过方式是“光域计算/波形合成”：Nokia 的时域酉变换用50 GHz 电带宽生成220 GBd 16-QAM（A3），CUHK 光均衡同时补偿收发带宽与色散并做到“Beyond-BtB”（A2）。两者均把信号处理迁移到光域（A2、A3）。
4. 共同的实用性限制：A3 环回装置受损耗、非酉效应和相位稳定性限制 SNR（220 GBd 仅11.8 dB）；A2 随速率升高增益收窄，且演示为 2 km，使用 3 抽头 FFE 做同步；A1 的 RL 与 AE 结果多为实验室背靠背/短距，仍需稳定性与自动化（A1、A2、A3）。
5. 本批三篇均偏基础研究，无系统厂商产品发布；产业侧对比对象为 Broadcom 3 nm DSP PHY 与 LPO/CPO 路线（A2）。
