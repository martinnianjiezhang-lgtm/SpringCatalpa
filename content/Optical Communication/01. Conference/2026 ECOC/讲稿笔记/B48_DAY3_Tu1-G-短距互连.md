---
title: "B48 · DAY3 · Tu1-G-短距互连"
tags:
  - ECOC2026
  - DAY3
---

### 0922-Tu1-G1-KDDIResearch-面向AI数据中心网络的可扩展大容量光传输.pdf
- 讲者/机构：Yuta Wakayama（合作者 D. J. Elson, Cen Wang, Han Wang, T. Tsuritani），KDDI Research | 题目：Scalable, High-Capacity Optical Transmission for AI Data Centre Networks（Tu1-G1） | 类型：学术论文/邀请报告（本场首讲，综述性质，多处引用自家 OFC/ECOC 旧作）
- 方向归属（主/次）：主 2（Scale-across，OCS 网关/跨集群光互连）；次 1（O 波段超宽带相干传输）、6（O 波段经典信号与 C 波段 QKD 共纤）
- 核心主张：
  1. SDM + WDM + 光电路交换（OCS）网关可在多个地理分散的 GPU 集群间构成逻辑全连接拓扑，且布缆量大幅减少（p30）。
  2. O 波段容量可与 S/C/L 波段相当；铋掺杂光纤放大器（BDFA）使完整 17.5 THz O 波段可用，OCS 网关借此实现超宽带而不牺牲简洁性（p30）。
  3. 12 芯光纤有望直接替代 MPO-12 布缆（>20 km），12 路 SDM 最多支持 5x5=25 个集群；O 波段经典数据可与 C 波段量子信道共存，O/C 频率间隔大，抑制自发拉曼散射（SpRS）对量子信道的劣化（p30）。
- 关键数据：
  - 传统 OTN 承载 GPU 流量的局限：拥塞、波长利用率下降、对 GPU 流量不透明、ROADM 度数受限与拓扑固定；本方案最大直径表达式 80 km×(…)，图上公式看不清 [p4]
  - 5x5=25 集群全连接需 12 芯光缆（如 MPO-12 或 3 对 4 芯光纤）；组内全连接单向需 10 根 SMF 线缆，双向 5 根 SDM 线缆（如 MPO-12）[p5]
  - OCS 网关：无源 MUX/DEMUX 用于 ZR 可插拔模块波长上下路，>32 端口；有源路由结构本工作用 4 个 WSS；布线部分含光放，实现同组直通光路（引 Wang, OFC W4H.3 2025）[p6]
  - 测试床：4 个虚拟化集群，间距 20–40 km；集群 A、C 各 2 块 Nvidia H100 GPU + 2 块 NIC；每个 OCS 网关接 scale-up 交换机，用波长预配置的 400G ZR 可插拔做 RDMA-over-Ethernet；集群 B、D 仅含网关功能；受放大器限制仅把集群间距延至 20–40 km；光谱图在约 1560.0–1561.0 nm，P1–P4 四点功率约 -30～-40 dBm 量级 [p7]
  - RDMA 时延随线缆长度 0–40 km 拟合：14.514 + 9.836x（单位 µs，x 为 km）；实测点 10 km 约 110 µs、20 km 约 210 µs、30 km 约 310 µs；结论：除光纤传输时延外无额外通信时延 [p8]
  - All-to-All 并行与 All-Reduce 双向环两种集合通信，数据量 100/400/1600/6400 GB；0/20/30 km 下作业完成时间几乎无差异（6400 GB 放大图纵轴刻度 1.0595E5～1.0597E5 ms 量级，差异极小；All-Reduce 页标注 negligible difference）[p9, p10]
  - 单纤容量-距离记录对比图：O 波段单独已报数据点位于约 100–150 Tb/s、50–135 km 区间（具体值看不清）；带宽表：C 波段 4.8 THz、CL 9.6 THz、SCL 14.4 THz、O 波段 14.4 THz；对应 400G(100 GHz)/800G(150 GHz)/1600G(300 GHz) 路数分别为：C 48/32/16，CL 96/64/32，SCL 与 O 均为 144/96/48 [p14]
  - 连续 16.4 THz O 波段单模光纤传输（Elson, OFC Th4A.2 2024）：80.4 km 超低损耗（ULL）光纤，全 BDFA 链（booster/preamp/前置），AWG 120 GSa/s，接收 DSO 80 GSa/s，SLED 做负载 [p15]
  - O 波段 BDFA：单级后向泵浦，泵浦 1195 nm，BDF 200 m（Wakayama, ECOC 2022 We2A.2）；超宽增益版泵浦 1150 nm，BDF 250 m，YDF 30 m 915 nm 泵浦，17.6 THz 带宽、增益 20+ dB（Mikhailov, OFC 2023 Th3C.1）[p16]
  - 16.4 THz 传输：总发射功率 17–26 dBm，约等效每信道 -10～2 dBm；观察到零色散附近 NLI 凹陷；“最优”发射谱（ISRS 补偿+NLI 抑制）在较低功率下提高 SNR；SNR 曲线约 10–15 dB 量级，零色散点约 229 THz 附近 [p17, p19]
  - 12 芯光纤 O 波段传输（Elson, ECOC 2023）：可替代 MPO-12，>20 km 布缆，支持单/双向，O 波段芯间串扰更低；光纤 125 µm 包层内 12 芯，图中标 180 µm、250 µm 尺寸 [p20]
  - C 波段 QKD 与 O 波段共存：80 km ULL 光纤在 1550 nm 损耗 14.5 dB；含带通滤波器 3.5 dB 与 WDM (解)复用 <2 dB，总损耗 20 dB；QKD 收发机背靠背损耗容限 30 dB；无 SpRS 时 20 dB 损耗下估计 SKR 约 100 kb/s [p24]
  - SpRS 测量：O 波段可调 ECL 入射现场敷设 10 km SMF，入纤功率约 4 dBm（避免 SBS），泵浦扫 1260–1360 nm，OSA 分辨率 2 nm，线路损耗 0.35 dB/km（1550 nm，含熔接与连接器）；泵浦波长越长，1550 nm 处 SpRS 越强，噪声功率约 -78～-82 dBm，1260–1290 nm 泵浦低于 OSA 灵敏度 [p25]
  - SpRS 效率模型：泵浦波长越短效率越高；“O-O”共存比“C-C”更难；O 到 C 的大频移使 SpRS 远低于显著水平 [p26]
  - SKR 预测与实测：20 km 已铺设 SMF 共存实验，实测 SKR 被预测曲线很好复现，SpRS 预测与实测差 <1.5 dB；SKR 随 O 波段 WDM 输入功率 0～约 10 dBm 由约 500 kb/s 量级下降，约 10 dBm 附近陡降 [p28]
- 提到的公司/客户/产品/标准：KDDI Osaka Sakai 数据中心商用链路（PQC + QKD 混合对称密钥分发，AES 与 Rocca-S 加密，p22）；Nvidia H100；400G ZR 可插拔；GeNOPSYS 标识出现在网关图（p6）；MPO-12；ITU 光纤（G.652.D 类，p15 图上字样）
- 与业界对比或记录声明（SOTA/首次/record）：未在本讲声明新 record；引用自家 16.4 THz 连续 O 波段传输与单纤容量-距离记录图对比 [p14, p15]
- 推荐配图页：p7（OCS 网关 scale-across 测试床与谱）；p14（各波段单纤容量-距离与波段信道数表）；p28（SpRS 模型预测 vs SKR 实测）

### 0922-Tu1-G2-KIT-暗孤子微梳无源相干克隆的24波零差检测.pdf
- 讲者/机构：Huanfa Peng, Yiyang Bao, Yi Zheng, Wolfgang Freude, Kresten Yvind, Sebastian Randel, Minhao Pu, Christian Koos；KIT（IPQ、IMT），丹麦 DTU | 题目：24-λ Coherent Optical Communications Using Passive Coherence Cloning of Dark-Soliton Microcombs for Homodyne Detection（Tu1-G2） | 类型：学术论文
- 方向归属（主/次）：主 1（相干/高波特率器件，微梳光源）；次 3（光源）
- 核心主张：
  1. 首次演示通过复用两个泵浦音（pilot tones）对暗孤子微梳做无源相干克隆，不依赖任何主动锁定环路（p9）。
  2. 首次演示基于 Kerr 梳、并行零差接收的多波长相干传输，DSP 工作量降低（p9）。
  3. 24 路数据信道达到净速率 8.3 Tbit/s（每偏振）（p8, p9）。
- 关键数据：
  - 背景：Kerr 亮孤子梳（自由运行态）覆盖 L+C 频段，99 路数据信道、Tx 与 Rx 均用 Kerr 梳，净速率 >32 Tbit/s（引 P. Marin-Palomo, Nature 546, 2017）[p3]
  - 暗孤子梳优势：双泵浦音实现更高转换效率、更高单梳线功率 [p2]
  - 方案：Tx 端 ECL + MZM（RF = fFSR/2）产生 P1、P2 双泵浦音，经 EDFA 泵浦 Si3N4 微环 MRR1 产生暗孤子梳；光纤 87 km（p6 标注）传输后，Rx 端用收到的两个泵浦音注入 MRR2 生成克隆梳；Tx 梳转换效率 η=25.2%，克隆梳 η=23.2%；48 条梳线功率高于 -10 dBm；梳线间隔 fc=fFSR=44.6782 GHz（RBW 1 Hz，拍频线宽窄）；FaML（facet-attached micro-lens）耦合损耗每端面约 1.3 dB；Tx/Rx 梳相位噪声谱基本重合（频偏 10^0–10^6 Hz）[p6]
  - 现有方案对比：主动锁定导频音需复杂锁定系统且残留频偏（Geng, Nat. Commun. 2022）；整梳光注入需额外光纤且距离受限约 100 m（Jang, Nat. Photon. 2018）[p5]
  - 传输实验：24 路数据信道、80 GBd QAM，AWG 调制；自由运行梳未克隆时频偏 Δf 约 440.06 MHz 量级（p4 图示） [p4, p7]
  - 结果：80 GBd 16QAM 经 85 km 光纤（p8 标注），有 FOC+CPR、无 FOC 有 CPR、均无，BER 分别为 1.0×10^-4、1.0×10^-4、2.7×10^-4；80 GBd 32QAM 对应 4.0×10^-3、4.0×10^-3、6.1×10^-3；24 路 BER 大多低于 20% SD-FEC 限，第 24 路 16QAM 接近限值；去掉频偏补偿（FOC）几乎无劣化，说明克隆使频偏为零；净速率 8.3 Tbit/s/偏振 [p8]
  - 注：p6 写 87 km，p8 写 85 km，讲稿内不一致，原样记录。
- 提到的公司/客户/产品/标准：无商业公司；20% SD-FEC 限；Si3N4 微环；DTU 提供器件（作者单位）
- 与业界对比或记录声明（SOTA/首次/record）：声明“首次”无源相干克隆暗孤子梳、“首次”Kerr 梳并行零差多波长相干传输 [p9]
- 推荐配图页：p6（无源相干克隆方案、梳谱与相位噪声）；p8（16QAM/32QAM 星座与 24 路 BER）

### 0922-Tu1-G3-SantAnna-双偏振短距系统群速度色散参数的正则微扰.pdf
- 讲者/机构：Dario Cellini（作者含 V. Oliari, E. Agrell, M. Secondini, G. Liga, A. Alvarado），Scuola Superiore Sant'Anna / Google / Chalmers / TU Eindhoven | 题目：Regular Perturbation on the Group-Velocity Dispersion Parameter for Dual-Polarization Short-Reach Systems（Tu1-G3） | 类型：学术论文（理论/建模）
- 方向归属（主/次）：主 3（Scale-out 短距 O 波段相干建模）；次 1（非线性建模/DSP）
- 核心主张：
  1. 将对 β2 的一阶正则微扰（RP-β2）从单偏振扩展到双偏振（Manakov 方程）并把色散补偿（CDC）纳入模型（p17）。
  2. RP-γ 与 RP-β2 的精确区域之并集覆盖参数空间的很大部分；取两模型中较小 NSD 即可在大片区域达到 NSD<0.1%（p16, p17）。
  3. 适用于累积色散低的 O 波段短距互连；后续工作：用于非线性补偿，并研究覆盖右上角区域的合并模型（p17）。
- 关键数据：
  - 精度判据：归一化平方偏差 NSD <0.1% 视为模型准确（以 SSFM 为“真值”）[p5]
  - 仿真系统：标准单模光纤 O 波段 1310 nm，α=0.4 dB/km，γ=1.4 W^-1 km^-1，β2=-1 ps²/km，β3=0.0765 ps³/km，L=20 km；400 Gb/s 净速率，双偏振，rFEC=0.83；16-QAM 60 GBd、64-QAM 40 GBd、256-QAM 30 GBd [p8]
  - NSD 随总入纤功率：RP-γ 误差随功率陡升且与符号率无关；RP-β2 斜率较低，且每种调制阶数水平不同；两模型交叉功率 P0：16-QAM 约 5 dBm，64-QAM 约 -2 dBm，256-QAM 约 -7 dBm；低于 P0 时 RP-γ 更准，高于 P0 时 RP-β2 更准；输入功率范围约 -12～12 dBm，NSD 约 10^-9～10^-1 % [p9, p10, p12]
  - 交叉功率 P0 随比特率（16-QAM）：约 -7 dBm(200G)、约 5 dBm(400G，60 GBd)、约 12 dBm(600G)、约 16 dBm(800G)（读图估值）[p13, p14]
  - 两个无量纲参数 γPLeff（非线性）与 |β2|Rs²L（累积色散）：RP-γ 误差对 |β2|Rs²L 几乎不敏感，RP-β2 误差沿 |β2|Rs²L 增长更快；扫描条件 P=5 dBm，Rs=60 GBd，16-QAM [p15, p16]
- 提到的公司/客户/产品/标准：无（Google 为作者单位）；引用 Manakov 方程、Nature Commun. 2020（Oliari）RP-β2 工作
- 与业界对比或记录声明（SOTA/首次/record）：未声明；为 RP-β2 首次扩展到双偏振（据 p17 结论页表述“extended to dual-polarization”）[p17]
- 推荐配图页：p12（三种调制格式下 RP-γ 与 RP-β2 的 NSD 对入纤功率曲线及交叉点）；p13（交叉功率随比特率）

### 0922-Tu1-G4-长飞-O波段空芯光纤的水汽稳健性.pdf
- 讲者/机构：长飞（YOFC，页标 Smart Link Better Life），讲者姓名未识别 | 题目：O 波段空芯光纤（HCF）对水汽的稳健性——页面标题被遮挡/OCR 乱码，英文原题看不清（内容为 O-band HCF robustness to water vapor，Tu1-G4） | 类型：学术论文（产品级光纤可靠性验证）
- 方向归属（主/次）：主 3（Scale-out 短距，O 波段 400G-FR4 光纤介质）；次 4（低时延 AI 互连）
- 核心主张：
  1. 首次实验验证 O 波段 HCF 对水汽的稳健性（p11）。
  2. 加速湿热暴露下气体吸收变化表现为两阶段：压差驱动的快速涌入，随后压力平衡后的缓慢扩散（p6, p11）。
  3. 长时间高温高湿后，更长光纤吸收累积更强，但四个 O 波段工作波长的插损保持相对稳定；暴露后 HCF 的 400G-FR4 BER 与常规单模光纤相当（p11）。
- 关键数据：
  - 动机：AI 训练需高带宽低时延；HCF 降低时延，但气体吸收线（GLA，HITRAN 计算）是可靠性隐忧，气体可能经非密封光纤接口进入 [p2, p3]
  - 测试：样品长度 35 m、500 m、2 km；温湿箱 85 °C/85% RH；EXFO 扫频激光与 CTP10 插损平台，分辨率 1 pm/250 pm；耦合点非气密；传输测试用商用 400G-FR4 模块、4 路 O 波段 CWDM PAM4 [p4, p5]
  - 35 m 样品：1352.48 nm 参考波长处插损随暴露天数由约 0 升至约 47 dB（约 5 天内快速升至约 38 dB，之后缓升，13 天约 47 dB）；四个工作波长附近未出现可测吸收线 [p6]
  - 10 天 85 °C/85% RH 后，1352.48 nm 附加损耗：500 m 样品 9.39 dB → 47.75 dB；2 km 样品 42.71 dB → 47.97 dB；2 km 样品在 1300–1340 nm 出现可测水汽吸收线，1260–1280 nm 出现氧吸收线累积 [p7]
  - 2 km HCF 插损（暴露前/后，dB）：1271 nm 0.699/0.897，1291 nm 0.699/0.769，1311 nm 0.761/0.690，1331 nm 0.639/0.698；变化 +0.0990、+0.0350、-0.0355、+0.0295 dB/km，10 天内波动在 ±0.1 dB/km 内 [p8]
  - 2 km HCF 与 SMF 插损（dB）：1271 nm 0.897/0.858，1291 nm 0.769/0.809，1311 nm 0.690/0.720，1331 nm 0.698/0.640 [p10]
  - 传输：模块工作温度 70 °C，VOA 控制接收光功率，实时 PAM4 BER；四通道 HCF 与 SMF 预 FEC BER 相当，量级约 1E-7～1E-4（接收光功率约 -1～5 dBm 范围），无明显劣化 [p9, p10]
  - 局限：环境设置未覆盖所有条件；其他大气气体（O2）影响未研究；后续做长期可靠性与数据中心现场试验 [p11]
- 提到的公司/客户/产品/标准：长飞 GTA-ST-HCF；EXFO TSOOS/CTP10；O 波段 G.657.A2 SMF 对照；400G-FR4、CWDM、SFP-DD 形态；HITRAN 数据库
- 与业界对比或记录声明（SOTA/首次/record）：声明“首次”对 O 波段 HCF 水汽稳健性做实验验证 [p11]
- 推荐配图页：p10（HCF 与 SMF 的插损对比表与四通道预 FEC BER 曲线）；p6（水汽吸收谱前后及两阶段涌入曲线）

### 0922-Tu1-G5-Aston大学-172TbpsGMI的O波段相干传输.pdf
- 讲者/机构：A. Donodin（邮箱 a.donodin@aston.ac.uk），Aston Institute of Photonic Technologies（合作方含 Fraunhofer HHI、Lightera 标识、Royal Academy of Engineering 等） | 题目：页面 p1 乱码，完整英文题看不清（主题为 172 Tb/s GMI、16.14 THz 满载 O 波段相干传输，Tu1-G5） | 类型：学术论文
- 方向归属（主/次）：主 1（相干/超宽带 O 波段）；次 3（O 波段光放/BDFA）
- 核心主张：
  1. 单一 O 波段放大器平台可支撑巨大相干容量，前提是对整条链路的功率演化做整体工程化（p13）。
  2. 15 dBm 入纤 + 1200 nm 后向拉曼是“甜点”：接收 OSNR 最平坦；升至 17 dBm 会在零色散波长附近增加非线性代价（p13）。
  3. 优化后 FWM 对信道速率影响可忽略；下一个瓶颈更像是收发机与放大器而非光纤（p13）。
- 关键数据：
  - 为何做 O 波段：可用带宽 17.5 THz（1260–1360 nm），近零色散降低色散补偿负担；挑战为光纤衰减高且不均（短波端）、带内 SRS 使功率由短波向长波转移、近零色散使 FWM/NLI 更强、放大器噪声与增益动态 [p2]
  - O 波段性能是“光纤损耗、带内 SRS、放大器动态、FWM/NLI”四要素平衡以最大化接收 OSNR 的问题 [p3]
  - 15 dBm 时带内 SRS 使短波有效损耗上升、长波下降；后向拉曼补偿短波缺口 [p4]
  - BDFA 动态：输入光功率仅差 10 dB 即可导致 OSNR 劣化超过 15 dB [p5]
  - 缺口（notch）深度法：Cai 等 OFC 2013 提出，Luis 等 OFC 2026 扩展为缺口深度代价；本文改为把接收放大器纳入并直接以可达 OSNR 优化；例：25 km 后经接收 BDFA，1315.4 nm 处缺口深度在 13 dBm 与 23 dBm 发射下分别为 29.8 dB 与 12.6 dB（图示读值）[p6]
  - 25 km G.654.D 光纤发射功率扫描：接收 OSNR 随发射功率提升至约 17 dBm；23 dBm 时全谱严重劣化，尤其 1305 nm 附近（缺口深度由约 22 dB 掉到约 17 dB）；背靠背缺口深度约 31.5–35 dB [p7]
  - 1200 nm 后向拉曼泵浦（1500 mA）改善接收 OSNR，尤其短波侧；15 dBm 兼顾最均衡 [p8]
  - 拉曼泵浦配置（15 dBm）：总功率 1200 nm 为 600 mW、1240 nm 为 400 mW；1240 nm 提升全带、尤其中长波，1200+1240 nm 可提升全带但短波代价较大；选定 1200 nm [p9]
  - 实验架构：3 路真实信道（CUT+2 邻道）扫过整个频带，其余用谱整形 SS-ASE 满载；两个独立 BDFA 放大 CUT 与邻道，第三个 BDFA 发射；DAC 120 GSa/s；接收 59 GHz/256 GSa/s；跨段后双级 BDFA + OBPF；1200 nm 后向 DRA [p10]
  - 速率估计：633×24.5 GBaud 64QAM 或 128QAM 逐信道选择；每信道五次 10 µs 采集，GMI 在 1.2×10^6 符号上平均，DSP 不含 CDC；后估计采用打孔 DVB-S2 码 + 1% 硬判决清理码；单信道吞吐约 230–310 Gb/s（1265–1358 nm），长波端 128QAM 更高 [p11]
  - 系统：633 路，24.5 GBaud，25.5 GHz 间隔，覆盖 1266–1358 nm，共 16.14 THz；单跨 25 km，1200 nm 后向拉曼；GMI 估计吞吐 172.87 Tb/s，译码后 164.83 Tb/s，频谱效率 10.7 bit/s/Hz，实现代价 4.6%（页面上写作“16.4 THz system”，与 16.14 THz 不一致，原样记录）[p12, p13]
- 提到的公司/客户/产品/标准：BDFA；G.654.D 光纤；DVB-S2；EXFO 等未出现；致谢中出现 Fraunhofer、Lightera、EPSRC TRANSNET、BMFTR HYPERCORE [p14]
- 与业界对比或记录声明（SOTA/首次/record）：声明 O 波段 GMI 估计吞吐记录 172 Tb/s [p11]
- 推荐配图页：p12（633 路 16.14 THz、172.87/164.83 Tb/s、10.7 bit/s/Hz 关键指标）；p11（逐信道吞吐 vs 波长，64QAM/128QAM/FEC 译码）；p7（不同发射功率下的缺口深度扫描）

## 本批小结
- O 波段成为 Scale-out/Scale-across 的新热点，且已从器件走向系统：KDDI（G1）综述 O 波段 14.4–17.5 THz 与 SCL 波段容量相当，Aston（G5）在 25 km 单跨达 633 路、16.14 THz、GMI 172.87 Tb/s（后 FEC 164.83 Tb/s），SNR/OSNR 平坦化靠 BDFA、后向拉曼和 15 dBm 入纤功率共同工程化；长飞（G4）则从光纤介质侧验证 O 波段 CWDM 400G-FR4。（G1、G5、G4）
- O 波段的共性难题是近零色散带来的 FWM/NLI 与带内 SRS 的短波损耗倾斜：KDDI 的 16.4 THz 实验观察到零色散附近 SNR 凹陷并用 ISRS 补偿谱优化，Aston 观察到 23 dBm 时 1305 nm 附近严重劣化；SantAnna（G3）的 RP-β2 模型则从建模上给出 O 波段 20 km、400G 下 RP-γ 与 RP-β2 的交叉功率（16-QAM 约 5 dBm）。（G1、G3、G5）
- Scale-across 出现“OCS 网关 + SDM + ZR”的具体形态：KDDI 测试床用 4 个 WSS、400G ZR 可插拔、H100 GPU，20–40 km 间距下 RDMA 时延仅按光纤传播增加（拟合斜率 9.836 µs/km）、集合通信作业完成时间几乎不变；12 芯光纤替代 MPO-12 可支撑 25 个集群全连接。（G1）
- 光纤介质创新围绕低时延与多芯：空芯光纤（G4）在 85 °C/85% RH 十天后 2 km 样品 O 波段工作波长插损变化在 ±0.1 dB/km 内，且 400G-FR4 BER 与 SMF 相当，但 1352 nm 以上水汽线已累积到约 48 dB，可靠性结论仅限四个 CWDM 波长；12 芯光纤（G1）走空分复用路线。（G1、G4）
- 光源与相干接收的“系统简化”路线：KIT（G2）用两个泵浦音无源克隆暗孤子微梳，省去频偏补偿，24×80 GBd 达 8.3 Tbit/s/偏振；与 O 波段 BDFA 平台（G1、G5）一样，都在用宽带、集成化器件换取系统复杂度下降。（G2、G1、G5）
- 量子安全成为 AI 数据中心光传输的附带需求：KDDI 展示 O 波段经典信号与 C 波段 QKD 共纤，SKR 由 SpRS 主导且可用数值模型预测（差 <1.5 dB），20 dB 总损耗下无 SpRS 约 100 kb/s，并给出 Osaka Sakai 数据中心商用 PQC+QKD 链路。（G1）
