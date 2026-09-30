---
title: "B09 · DAY1 · C2.1-Su1-Su2-星地链路大气湍流"
tags:
  - ECOC2026
  - DAY1
---

# B09 笔记：ECOC 2026 Workshop 星地链路/大气湍流（DAY1 Su1–Su2 F 会场）

说明：本批讲稿均为 Workshop/邀请类；除 F-01+02 连拍外无与已跳过篇目重叠。看图共 40 张。

### 0920-am-Su1-F-01+02-FraunhoferHHI+Durham-分集抗衰落与低时延星地链路商用门槛.pdf（第1–10页：Fraunhofer HHI 一讲）
- 讲者/机构：讲者姓名未在所看页出现 / Fraunhofer HHI | 题目：（无独立题目页；主题页为 "Atmospheric turbulence – Why do we need turbulence mitigation?"，副标题 Turbulence mitigation / Diversity combining） | 类型：Workshop
- 方向归属（主/次）：主 [2 Scale-across/跨域]（星地激光链路）；次 [1 相干]
- 核心主张：
  1. 大气湍流造成散斑与块衰落（Ts≪Tc，衰落持续约 ms 量级），高速相干链路需要衰落缓解。
  2. 常规手段有 ARQ、时间分集（擦除编码）、空间分集、波长分集；空间分集在合并方式上存在复杂度与增益折中。
  3. 结论页原句：有分集时，同样的中断性能可用更低的每分支发射功率实现。
- 关键数据：
  - 归一化对数正态衰落，SI=0.9，L=4 个分集分支，中断概率 10^-3 处：相对单通道 SDC（帧级选择合并）增益 7.5 dB，MRC（符号级最大比合并）增益 12.5 dB [p10]
  - SDC：可能用 COTS 相干收发机，增益低于 MRC；MRC：FEC 前合并，需定制相干接收机 [p4–p5]
  - 波长分集：基于多发射孔径，优点为 WDM 器件简单，缺点为频谱效率低、各路独立 DSP，载波恢复需适应衰落信道 [p3]
- 提到的公司/客户/产品/标准：ESTOL（擦除编码示例）、COTS 相干收发机
- 与业界对比或记录声明（SOTA/首次/record）：无 [p10]
- 推荐配图页：p10（中断概率 vs 每分支平均功率曲线，L=1/SDC/MRC 及 7.5 dB、12.5 dB 标注）

### 0920-am-Su1-F-01+02-FraunhoferHHI+Durham-分集抗衰落与低时延星地链路商用门槛.pdf（第11–27页：Durham 大学一讲）
- 讲者/机构：Dr. Andrew P. Reeves / Durham University, Centre for Advanced Instrumentation | 题目：Challenges to resilient Low-Earth Orbit Feeder Links | 类型：Workshop
- 方向归属（主/次）：主 [2 Scale-across/跨域]（LEO 馈电链路）；次 [1 相干]
- 核心主张：
  1. LEO 卫星过顶快、仰角低，低仰角带来强湍流（积分 Cn² 大、r0 小、强闪烁与分支点），需要快速捕获与高跟踪速率。
  2. LEO 提前角（PAA）大导致显著的非等晕误差，AO 增益受限。
  3. 激光导星中钠导星最佳但昂贵、需空域安全流程，对 LEO 馈电链路多半不具商业可行性；Rayleigh 导星便宜且更稳定，有时低中断概率更好。
- 关键数据：
  - 实例：Starlink（STARLINK-3790）当天早上过马拉加上空，最大仰角 40°，过境约 10 min，10° 以上约 6 min [p15，看图核实]
  - 提前角：GEO 18 µrad；LEO 20–50 µrad；曲线上 GEO 18 µrad 处 Strehl 约 0.5、50 µrad 处约 0.2（HV5/7@550 nm，波束 1550 nm；读图估计）[p22，看图核实]
  - CNN 波前传感（WFS）：40 cm 望远镜，r0=5 cm @1550 nm，12×12 子孔径 SH，无噪声、非闭环；低仰角(约5°, Rytov 方差约14.61)时 CNN 光纤耦合约 -3.2 dB，Shack-Hartmann 约 -8 dB；仰角≥40° 两者相近（约 -2 至 -3 dB）[p20]
  - Rayleigh vs Sodium LGS：30° 仰角，对比 TURBO/MOSPAR/HV 三种湍流剖面；Rayleigh 导星取 14 km，耦合通量 PDF/CDF 介于仅卫星信标与钠导星之间 [p26]
  - Rayleigh 导星只在约 20 km 内可见，不能采样全部湍流，但成本低得多、可用绿光 [p24，看图核实]
- 提到的公司/客户/产品/标准：Starlink；钠/Rayleigh 激光导星；Optics Express 34.3 (2026) 5636–5656（Lognoné, Perrine, Wizinowich, Reeves）
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p20（CNN-WFS 与 Shack-Hartmann 光纤耦合 vs 仰角对比）；p26（Rayleigh/钠导星耦合通量统计）

### 0920-am-Su1-F-03-北邮-星地激光链路湍流影响.pdf
- 讲者/机构：Jian Wu / 北京邮电大学（BUPT） | 题目：Impacts of Atmospheric Turbulence on Satellite-to-Ground Laser Communication Links and its Mitigation | 类型：邀请报告/Workshop
- 方向归属（主/次）：主 [2 Scale-across/跨域]（星地激光）；次 [1 相干]
- 核心主张：
  1. 星地激光通信性能受大气条件严重影响。
  2. 下行湍流影响可解决，且已被实验验证（AO、MDR、MDR+AO）。
  3. 上行湍流缓解仍需深入研究（点前置误差与校正延迟、PL/MPLC 大功率承受、结构光束等）。
- 关键数据：
  - 激光 vs RF 回传：激光 1 TB 约 80 s（100 Gb/s）；RF X 波段 1 TB 约 2 天（1.2 Gb/s）；每星每日回传激光 10 min 内 40 TB，RF 仅约 1 TB [p3]
  - 下行公开报道：MIT TBIRD 200 Gbps（2022.05）；CGSTL+BUPT/吉林一号 100 Gbps，113 s（2024.12）；GW+BUPT 1.25 Gbps，297 s（2025.09）；BUPT+中科院光电所 1 Gbps，2 h（2025.12）；中科院空天院 120 Gbps，108 s（2026.01）[p4]
  - 下行缓解表：NASA/MIT 2013 4×40 cm 阵列光子计数 622 Mbps 月地无误码；DLR+TESAT AO 相干 5.6 Gbps/LEO、2.8 Gbps/GEO；MIT AO 200 Gbps/LEO；CGSTL+BUPT 模式分集接收(MDR) 相干 100 Gbps/LEO；Cailabs IM-DD 最多45模、约10 km 外场；BUPT MDR+AO 相干 1 Gbps/IGSO，稳定下行>3 h [p7]
  - 上行缓解表：Fraunhofer HHI 4 孔径实时合并，10 Gbps OOK，18 km 外场；DLR 预失真 AO，GEO 上行损耗降 3–5 dB；IOE(CAS) 多孔径分集发射，10 Gbit/s 无误码外场 [p8]
  - 湍流特征（看图核实）：快衰落约 ms、约 30 dB（湍流）；慢变（云雨雪雾，分钟~小时级）约 80 dB；南山站全天 r0@550nm 约 4–10 cm；上行卫星接收孔径 0.05–0.1 m（以闪烁为主），下行地面接收孔径 0.5–1 m（光斑破碎致 SMF 耦合效率劣化）；星地距离 500–4,000 km [p5–p6]
  - 星座规模：Starlink 约 11,000 颗在轨/规划 42,000；太空算力星座 SpaceX Starmind 约 1,000,000 颗等 [p3]
- 提到的公司/客户/产品/标准：Starlink、Amazon Leo、GW、Spacesail、SpaceX、Blue Origin、Starcloud、Google Suncatcher、Cailabs、Tesat、Airbus/TELEO、SES、Kepler
- 与业界对比或记录声明（SOTA/首次/record）："下行速率已达 200 Gbps；上行通信演示报道很少" [p4]；"MDR-AO 组合技术在轨与外场实验中所有湍流条件下验证" [p7]
- 推荐配图页：p4（2022–2026 星地激光链路公开报道时间表）；p7（下行湍流缓解方法对比表）；p8（上行缓解对比表）

### 0920-am-Su1-F-04-Aveiro-自适应相干DSP抗湍流.pdf
- 讲者/机构：Fernando P. Guiomar / Instituto de Telecomunicações（Aveiro） | 题目：Adaptive Coherent DSP and Turbulence Mitigation Techniques for Robust High-Capacity Ground-to-Space Optical Links | 类型：邀请报告/Workshop
- 方向归属（主/次）：主 [1 相干/oDSP]；次 [2 Scale-across/跨域]
- 核心主张：
  1. 湍流使 FSO 成强时变信道；反馈速率自适应有效，但反馈延迟过大会适得其反（对卫星链路尤甚）。
  2. 接收端 FSO 专用 DSP（少模接收+相干数字合并）可避开反馈延迟瓶颈，利用空间分集。
  3. DSP 不是银弹，需与 AO、前置放大等光学缓解构成数字/光学混合方案。
- 关键数据：
  - COTS 400ZR 收发机经湍流室：无缓解时接收功率波动>10 dB、深衰落>30 dB，速率受严重影响；加光束漂移缓解后波动>5 dB、深衰落 15 dB，速率多数时间稳定（约 300 Gbit/s 量级，看图读数）但有零星中断 [p3]
  - 概率整形自适应调制（PS-64QAM，H=5.58，550G）：晴天瞬时速率约 460–480 Gbps（固定基线 500 Gbps 与 400 Gbps 两条线），降雨时下探到 400 Gbps 以下即 SNR 不足断链，实验为 180 min [p7，引自 JLT 2021]
  - 相干时间 Tc：强/中/弱湍流分别 5.6/5.5/4.6 ms；闪烁指数 σI² 弱 1.6×10^-1、中 9.4×10^-1、强 2.2；τ<1 ms 易处理，1–10 ms 具挑战，>10 ms 几乎不可能 [p9]
  - 反馈延迟：吞吐 vs 延迟，自适应码率 @16QAM 在 0 ms 约 106 Gbit/s，@QPSK 约 103 Gbit/s，固定 R=5/6 QPSK 约 87 Gbit/s；延迟约 1.6 ms 后自适应低于固定方案，5 ms 时约 74 Gbit/s [p11]
  - 延迟场景表（看图核实）：城市点对点 0.5–2 km/约 3.3–13 µs；城际 50–100 km/333–666 µs；UAV-地面 1–50 km/6.66–333 µs；UAV 中继 1–500 km/6.66 µs–3.3 ms；UAV-LEO 100–700 km/666 µs–4.6 ms；LEO 星地 500–1,500 km/3.33–10 ms；GEO 36,000 km/240 ms；信道相干时间强/中/弱湍流约 5.6/5.5/4.6 ms [p10]
  - 10 模 MPLC 少模接收（HG00/HG10/HG01/HG11），BER 分布随合并模数改善；论文 CSNDSP 2026 Edinburgh [p17]
- 提到的公司/客户/产品/标准：400ZR、MPLC、PS-QAM、IEEE JLT 2021、CSNDSP 2026
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p11（吞吐 vs 反馈延迟，自适应反而劣于固定）；p9（相干时间与延迟分区）

### 0920-am-Su1-F-05-FraunhoferIOF-主镜到纤芯的光学天线.pdf
- 讲者/机构：Dr. Matthias Goy / Fraunhofer IOF（耶拿光学地面站 OGS Jena）（p1 标题页看图核实） | 题目：From Primary Mirror to Fiber Core: The Optical Antenna and its Relay Architecture（"The optical Antenna"、"The last metre"） | 类型：Workshop
- 方向归属（主/次）：主 [2 Scale-across/跨域]；次 [1 相干]
- 核心主张（结论页原文）：
  1. M1（主镜）决定增益与效率，需谨慎选择。
  2. AO 不只是湍流，还涉及温度、重力、指向和人员。
  3. "最后一米"（到光纤纤芯）最令人受挫；上行相同但不同；AI 可能有帮助。
- 关键数据：
  - 主动光学（长期稳定）：卸载高幅漂移（Tip/Tilt、Focus），校正带宽<1 Hz；自适应光学（高动态）：校正带宽>1 kHz，补偿高阶湍流、振动、指向抖动 [p5]
  - "最后一米"装置：200 mm 无遮挡望远镜（竖直放置）+Tip/Tilt 镜、变形镜、单模光纤耦合、跟踪相机与 4Q 二极管；提出光纤参考的残差校正 [p7]
  - 上行用途：馈电链路、深空通信、空间碎片操控的 AO 预补偿，需高鲁棒、高致动数变形镜（上行光场须在出射大孔径前精确整形）[p9，看图核实]
- 提到的公司/客户/产品/标准：Fraunhofer IOF OGS Jena；变形镜（ALPAO 见图）
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p7（"最后一米"200 mm 望远镜、DM、SMF 耦合装置及局限/问题/方案）

### 0920-am-Su1-F-06-DLR-可扩展自适应光学.pdf
- 讲者/机构：Douglas Laidlaw / DLR Optical Satellite Links (OSL)，Mitigation of Atmospheric Impairments (MAI) | 题目：Building the Next Generation of AO Systems – A Robust and Scalable Solution for High-Throughput FSOC | 类型：Workshop
- 方向归属（主/次）：主 [2 Scale-across/跨域]；次 [1 相干]
- 核心主张：
  1. 两类方案：光纤/光子式（耦合面积>SMF 纤芯，分光到多路 SMF 再相干合并）与 AO（测相位畸变、缓解湍流、直接耦合入 SMF）。
  2. 对比：光纤式系统复杂度低，但下行吞吐与上行只能统计缓解；AO 下行吞吐好、上行为确定性校正，复杂度高，SWaP-C 两者相当（AO 可做到"鞋盒大小"）。
  3. 下一代：LEO 兼容、优化吞吐、信道表征，上行预补偿 2027/2028。
- 关键数据：
  - 2017–2024 GEO 上行预失真实验：无预失真(No PD)时 Alphasat 接收功率深衰落至约 -120 至 -130 dBW，有 HOPD 后功率维持约 -70 至 -85 dBW（读图），链路时间 200 s 内 [p11，引 Hristovski et al 2024]
  - 用 AO 遥测表征信道：下行 SMF 耦合效率 AUDE(ESA OGS) vs SINDAR，r=0.932，y=1.079x-0.028；上行预补偿功率闪烁指数 TDP1 vs SINDAR，r=0.862，y=1.096x-0.011 [p13]
- 提到的公司/客户/产品/标准：ESA OGS 的 AUDE AO 系统；SINDAR；TDP1（Alphasat）；ESA Eagle-1 及另一任务徽标 [p15]
- 与业界对比或记录声明（SOTA/首次/record）：无（BUPT 讲稿引用 DLR 预失真 AO 使 GEO 上行损耗降 3–5 dB）
- 推荐配图页：p11（GEO 上行预失真 vs 无预失真功率时间序列）；p6（光纤式 vs AO 对比表）

### 0920-am-Su2-F-01-NICT-日本星地激光通信实践.pdf
- 讲者/机构：Alberto Carrasco-Casado / NICT Space Communication Systems Laboratory | 题目：Space Laser Communications Through the Atmosphere: NICT's Experience in Japan | 类型：邀请报告/Workshop
- 方向归属（主/次）：主 [2 Scale-across/跨域]；次 [1 相干]（水平 2 Tbit/s 链路）
- 核心主张：
  1. 30 余年信道测量：ETS-VI(1994)、OICETS(2006)、SOTA(2014)、VSOTA(2019)、SOLISS(2020)、JDRS(2021)、CubeSOTA(2026)、HICALI(2027 计划)。
  2. 上行闪烁远强于下行（大孔径平均效应）；多波束空间分集、波束发散控制、AO/MPLC 是应对手段。
  3. 已用 7.4 km 水平链路验证 2 Tbit/s 并推进 CubeSOTA 与 HAPS 网络。
- 关键数据：
  - JDRS(JAXA，GEO，约1550 nm，单上行波束，仅夜间；2021-11-12/13 同一 20 s 窗口)：下行 100 cm 孔径 SI=0.0007（3σ 0.35 dB）；下行 5 cm SI=0.126（180×，3σ 4.50 dB）；上行 14 cm SI=0.234（334×，3σ 6.99 dB）[p12]
  - 7.4 km 水平实验（NICT 小金井—电通大调布），2025 年 4 月：5 通道 × 400 Gbit/s = 2 Tbit/s，波长 1556.55–1563.05 nm；五路 BER 平均 3.53e-02、3.77e-02、4.29e-02、4.63e-02、6.50e-02（看图核实）；闪烁 σ≈4.0 dB；加 LNA 后接收灵敏度提升（约 −36 → −44 dBm，小字读图）[p17–p18]
  - 引入 LNA 后调制解调器灵敏度改进：约 -44 / -42 / -36 dBm（三档速率，读图）[p18]
  - 2024 年 2 月 10 Gbit/s 7.4 km 水平实验（NICT 小金井 ↔ UEC 调布）：夜间闪烁 3σ≈4 dB、日间≈15 dB；跟踪开启时 SMF 平均 −29.09 dBm（σ 5.43）、MMF 50 µm −19.85 dBm（σ 3.54）、MMF 100 µm −8.26 dBm（σ 3.04），MMF 较 SMF 分别高 9.2 dB 与 20.8 dB [p15–p16，看图核实]
  - CubeSat 光束发散对比（FWHM）：OCSD-C 2618 µrad(137.8×，-43 dB)；CLICK-A 1300 µrad(68.4×，-37 dB)；OCSD-B 1047 µrad(55.1×，-35 dB)；TBIRD 380 µrad(20×，-26 dB)；PIXL-1 120 µrad(6.3×，-16 dB)；CubeSOTA 19 µrad(1×，0 dB) [p22]
  - 捕获时间分布：LEO-OGS 约 0.1–0.8 s；LEO-HAPS 带发散控制(BDC) 约 1.4–19 s（峰值约 6.7 s）；LEO-HAPS 固定发散约 32–433 s 以上（峰值约 152–257 s）[p24]
  - CubeSOTA 上行链路预算示例：仰角 35°，上行功率 30.0 W，发散 200 µrad(捕获 500 µrad)，下行发散 54 µrad，星地距离 833.5 km(高度 512 km)，上行信标 1560 nm、通信 1558.17 nm、下行 1541.35 nm，上行足迹 166.7 m（捕获 416.7 m），下行足迹 45.0 m，Fried 参数 13.9 cm(UL)/13.7 cm(DL)，链路可用度 2σ (97.7%) [p27]
  - 1 m OGS(小金井) 带 MPLC 与 AO 两个 Nasmyth 平台 [p26，看图核实]；HICALI 多波束上行（4 路捕获信标，波束间距 >r0）：波束数 1/2/4/8/16 时归一化强度概率密度收窄（16 束峰值约 1.9）[p28]
- 提到的公司/客户/产品/标准：NICT、JAXA(JDRS)、ETS-VI/OICETS/SOTA/VSOTA/SOLISS/CubeSOTA/HICALI(ETS-IX)、Tamron（波束发散控制）、TBIRD/CLICK-A/OCSD/PIXL-1、HAPS
- 与业界对比或记录声明（SOTA/首次/record）：CubeSOTA 19 µrad 发散为对比 CubeSat 中最窄 [p22]；水平 2 Tbit/s 7.4 km 自由空间（未称 record） [p17]
- 推荐配图页：p12（JDRS 上下行闪烁指数对比表与时间序列）；p22（CubeSat 光束发散对比）；p17（2 Tbit/s 7.4 km 实验）

### 0920-am-Su2-F-02-ANU-澳国立激光通信计划.pdf
- 讲者/机构：Professor Francis Bennet / Australian National University（Quantum Optical Ground Station, QOGS）（p1 倒拍标题页看图核实） | 题目：Australian National University Laser Communication Program: An overview of laser propagation and correction through atmospheric turbulence | 类型：Workshop
- 方向归属（主/次）：主 [2 Scale-across/跨域]（深空/月地光链路）；次 [6 QKD/量子]
- 核心主张：
  1. QOGS 用于光通信与空间应用，已参与 NASA Artemis II 月地激光通信（O2O）。
  2. 2025 年 6 月用澳大利亚 3.9 m AAT 完成 DSOC 深空下行洲际演示，并展示站点分集对深空光通信的意义。
  3. 挑战：接收光学简单但电学极复杂；<ns 脉冲、100 ps 精度；高功率上行与弱下行隔离；多波长共放大非线性；Tx 望远镜共视轴与热漂移。
- 关键数据：
  - QOGS：ACT 政府拨款+CSIRO+ANU 资助，2023 年 12 月新楼启用；PlaneWave RC700，70 cm 孔径；Coudé 处已装量子上行 AO，Nasmyth AO 2027 年，水平 CV-QKD 与高速相干 AO 2027 年 [p2]
  - Artemis II 系统：发射 4×150 cm 孔径，每路 20 W 信标；接收带 tip-tilt 校正馈入 16 元 SNSPD 阵列，NASA Glenn FPGA 调制解调器；ADS-B 接收机用于避让飞机 [p4]
  - 结果：除一个任务日外均成功建链；共下行 43 GB，激光时间 15.5 h；最高速率 260 Mbps @ 342,000 km；最远 400,000 km 多一点达 80 Mbps；演示 4K 视频下行 [p12]
  - DSOC：信标由加州 Table Mountain 发射，光束足迹约 2000 km，覆盖 AAT 与堪培拉两站；其余为IR相机螺旋扫描记录强度起伏 [p13–p14]
- 提到的公司/客户/产品/标准：NASA Artemis II/O2O、NASA Glenn Research Center、CSIRO、SNSPD、DSOC(JPL)、AAT、PlaneWave
- 与业界对比或记录声明（SOTA/首次/record）：Artemis II 任务最高数据率 260 Mbps @342,000 km [p12]；洲际上行/下行深空光通信演示 [p13]
- 推荐配图页：p12（Artemis II 任务成果要点）；p4（Artemis II 系统架构框图）

### 0920-am-Su2-F-03-MITLL-链路层与物理层抗湍流对比.pdf
- 讲者/机构：Bryan Robinson（合作者 Curt Schieler, Don Boroson）/ MIT Lincoln Laboratory | 题目：Performance of Link-Layer and Physical-Layer Atmospheric Mitigation Approaches for Free-Space Optical Communications | 类型：邀请报告/Workshop
- 方向归属（主/次）：主 [1 相干/oDSP]；次 [2 Scale-across/跨域]
- 核心主张（结论页）：
  1. 物理层与链路层数字手段可在大气信道上提供无误码光通信。
  2. 低码率 FEC 有显著优势；物理层码字交织比链路层缓解（擦除码或 ARQ）有约 3 dB 或更多优势。
  3. 对固定码率物理层 FEC，最优链路层码率取决于信道；ARQ 是简单且可达容量的自适应方式。
- 关键数据：
  - 两个示例：Orion Artemis II O2O(2026)，月地 260 Mbps 下/20 Mbps 上，缓解：多孔径多模接收；物理层低码率 FEC+约 1 s 交织；链路层无；TBIRD(2022–2024)，LEO 到地 200 Gbps 下行，缓解：大接收孔径+AO，物理层高码率 COTS FEC，链路层 ARQ；两条链路在整个会话（TBIRD 数分钟，O2O 数小时）无误码 [p3]
  - Type 1/2（交织）接收灵敏度：相对静态信道有约 1 dB 衰落代价（码率 0.9 附近）；衰落代价随码率升高变大 [p6]
  - Type 3/4 例：最先进电信接收机约 5 photons/bit；LEO-地 AO 链路约 50% 时间功率低于均值；5 dB photons/bit 输入产生约 50% 物理层码字擦除；需 0.5 码率擦除码/ARQ；总码率 0.43，总功率 8 dB PPB [p7]
  - 100 Gbps DP-QPSK 三个例子（共同：用户速率 100 Gbps 无误码，总码率 0.435，57.5 Gbaud，实现损耗 3 dB）：A 用 OpenZR+ 100G 收发机（码率 0.87 oFEC）+ 理想 1/2 擦除码，所需功率 -40.9 dBm；B 相干接收+理想码率 0.62 FEC+0.7 擦除码，-45.7 dBm；C 相干接收+解交织+理想码率 0.43 FEC，-48.8 dBm [p9]
  - 即：C 相对 A 少约 7.9 dB 功率（由所列 -40.9 与 -48.8 dBm 推算）
- 提到的公司/客户/产品/标准：NASA、TBIRD、O2O、OpenZR+、SPIE 13355 (2025) 参考论文
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p9（A/B/C 三种 100 Gbps DP-QPSK 架构与所需接收功率对比）；p3（O2O 与 TBIRD 缓解手段对照）

## 本批小结

1. 星地激光链路的技术中心正从"单纯大孔径/AO"转向"光学+数字"混合缓解：MIT LL 定量给出物理层低码率 FEC+长交织优于链路层擦除码/ARQ 约 3 dB 以上（MITLL p9/p10），Aveiro 强调 DSP 不能替代 AO、需混合（Aveiro p18），BUPT 则给出 MDR+AO 在轨/外场验证（BUPT p7）。
2. 反馈自适应有硬性时间约束：Aveiro 实测相干时间约 4.6–5.6 ms，反馈延迟超约 1.6 ms 后自适应吞吐反低于固定码率（Aveiro p9、p11），因此 LEO/GEO 下行更依赖接收端前馈手段；MIT LL 的交织方案同理不依赖反馈。
3. 上行仍是共性短板：BUPT 明确"上行湍流缓解需进一步研究"（BUPT p9），NICT 的 JDRS 数据显示上行闪烁指数 0.234 比 1 m 下行 0.0007 高数百倍（NICT p12），DLR 上行预失真在 GEO 已见 3–5 dB 改善但 LEO 受点前置角限制，Durham 也指出 LEO 提前角 20–50 µrad 带来显著非等晕误差（DLR p11、Durham p22、BUPT p8）。
4. 分集是对付深衰落的通用手段：HHI 的 L=4 分集在 10^-3 中断概率下 SDC 7.5 dB、MRC 12.5 dB（HHI p10），NICT HICALI 多波束上行（NICT p28），BUPT 上行表中的 4 孔径与多孔径发射（BUPT p8），ANU 的站点分集（ANU p14）。
5. 系统化落地趋势：5G/数据中心侧的相干技术被直接迁移到自由空间——COTS 400ZR 经湍流室（Aveiro p3）、OpenZR+ 100G 用于星地链路预算比较（MITLL p9）、NICT 7.4 km 5×400G=2 Tbit/s（NICT p17）；同时 BUPT 提到的太空算力星座（Starmind 约100万颗等，BUPT p3）正在拉动星地/星间光链路需求。
6. 面向 LEO 商用的工程难点集中在捕获与指向：NICT 用波束发散控制把 LEO-HAPS 捕获时间由数百秒降到数秒量级（NICT p24），Fraunhofer IOF 强调"最后一米"光纤耦合与非共光路误差（IOF p7），ANU 强调 Tx 共视轴与热漂移（ANU p15）。
