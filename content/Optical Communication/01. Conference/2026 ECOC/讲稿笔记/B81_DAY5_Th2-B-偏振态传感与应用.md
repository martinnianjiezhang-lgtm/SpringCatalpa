---
title: "B81 · DAY5 · Th2-B-偏振态传感与应用"
tags:
  - ECOC2026
  - DAY5
---

### 0924-Th2-B1-都柏林圣三一学院-用偏振态监测完全无监督地检测海底光缆物理接触.pdf（第1–7页）
- 讲者/机构：Agastya Raj（题目页首位作者）, Alvaro Doval, Tian Tian, Steinar Bjørnstad, Marco Ruffini（Trinity College Dublin IRIS 组 / Tampnet AS） | 题目：Fully Unsupervised Detection of Physical Contacts on Subsea Cables via State-of-Polarization Monitoring | 类型：学术论文
- 方向归属（主/次）：主 6 光纤传感（SoP 海缆监测）/ 次 1 海缆
- 核心主张：
  1. Fast-Slow DSVDD 用无标签 SoP 数据在多时间尺度上学习"正常"，对异常录音排序供人工复核。
  2. 5 个已确认接触事件在 13 次告警内全部检出，STA/LTA 需 91 次、vanilla DSVDD 需 1,219 次。
  3. 独立 DAS 与 AIS 复核支持存在原始接触日志之外的额外事件。
- 关键数据：
  - 背景：全球每年报告 150–200 起海缆故障，70–80% 为渔业/抛锚等人为活动（来源 ICPC 2025）[p1]
  - 链路：Lowestoft（英）–Lista（挪）海缆，全链路 SoP 监测：CW 探测光与在网 WDM 业务经 MUX+放大器合波，经两个光节点（ROADM + 混合 EDFA/Raman）后解复用，PBS 接收 S1 = V1 − V2（44.1 kHz、16-bit）；p1–p2 幻灯片未标链路总长（原先的 420 km 无图可证，已删除）；并行暗纤 DAS 覆盖 120 km，用于独立核对接触 [p1–p2，看图核实]
  - 数据集：2025年6–8月共 122,174 条 1 分钟 SoP 记录，仅 5 次经 DAS+船舶信息确认的接触，其余无标签 [p2]
  - 每周 1 次告警预算下覆盖：Fast-Slow DSVDD 5/5；vanilla DSVDD 2/5；STA/LTA 1/5 [p5]
  - 检出全部 5 个事件所需告警数：Fast-Slow DSVDD 13（约1次/周）；STA/LTA 91（约7次/周）；vanilla DSVDD 1,219（约93次/周）[p5]
  - 15 July E02（尖锐突变）两种方法均检出；17 July E03（不规则突发）STA/LTA 漏检、Fast-Slow DSVDD 检出 [p5]
  - 17 Aug 2025 未记录事件：Fast-Slow DSVDD 检出、STA/LTA 漏检，独立 DAS 有明确信号；页面另有 3 June 与 10 June 两例，其中 10 June 无 DAS 信号（120 km 内），AIS 复核发现船舶应答器被关闭 [p6]
  - Fast-Slow DSVDD 采用快/慢两路视图（快路 1 s 窗、2–50 Hz；慢路 10 s 窗、0.1–2 Hz，同一起点、幅度分别归一），共 8 个分支，各分支独立打分：记录内取窗口最高分作为记录分，再按分支排名取最优名次 [p4，看图核实]
- 提到的公司/客户/产品/标准：Tampnet（合作方）；ICPC；DAS；AIS；STA/LTA、DSVDD 算法
- 与业界对比或记录声明（SOTA/首次/record）：未声称 record；对比基线为 STA/LTA 与 vanilla DSVDD [p5, p7]
- 推荐配图页：p5（阶梯图：各方法覆盖 5 个确认事件所需告警数，13 vs 91 vs 1,219）
- 局限（讲者结论页）：需跨其他海缆与季节验证，并区分接触与其他扰动 [p7]

### 0924-Th2-B2-华为加拿大-空芯光纤的偏振态振动敏感度与多径干扰影响.pdf（第1–7页）
- 讲者/机构：Zhiping Jiang（通讯作者，题目页下划线）, Pedro Tovar, Yang Lan（Huawei Technologies Canada, Ottawa）；Xutao Wang, Xianchao Guan, Han Luo, Xingyu Zhou（Huawei 东莞） | 题目：On SOP Vibration Sensitivity in Hollow Core Fibers and the Impact of Multipath Interference（p1 看图核实；目录：光网络振动监测 → HCF 的 SOP 敏感度报告 → MPI 影响 → 输入 SOP 依赖 → DNANF vs SMF 对比方法 → 结论）| 类型：学术论文
- 方向归属（主/次）：主 6 光纤传感（SOP 前向感知）/ 次 1 高波特率/相干（ISAC）
- 核心主张：
  1. 多径干扰（MPI）在窄线宽相干光探测下会把相位变化伪转换为 SOP 变化，可能高估光纤真实 SOP 振动敏感度。
  2. SOP 振动敏感度强烈依赖输入 SOP 与声致双折射轴的夹角，跨光纤比较须优化输入 SOP。
  3. 采用 MPI 免疫、输入 SOP 感知的表征方法后，所测 DNANF 的 SOP 敏感度与标准 SMF 相当，是待研究的开放问题。
- 关键数据：
  - 背景对比：HCF 损耗 0.04 dB/km，背向散射比 SMF 低约 3 个数量级，故前向 SOP 感知更重要 [p2]
  - 有争议的文献：OFC 2026（J. Fang 等）报告 HCF 相对 SMF SOP 敏感度提升 >100 倍；Photon. Res. 14, 1883 (2026)（M. Ding 等，ECOC 投稿后发表）称无显著提升 [p2]
  - 讲者推测 >100x 的可能原因：用窄线宽激光（Δν≈100 Hz）在 MPI 约 -40 dB 下测量（页上幻灯片小字，Δν 数值略有不确定）[p6]
  - MZI 验证：30 m 路径差；100 kHz 线宽光源下 Stokes 参量强烈起伏；换 10 GHz 宽带源后起伏被完全抑制（MPI -37 dB 等条件）[p4]
  - 图示 ΔSOP 随 MPI 上界下降，100 kHz 源沿上界，10 GHz 源基本平坦在约 3×10^-3 rad 量级（读图值）[p4]
  - 输入 SOP 依赖：探测 600 个输入 SOP，132 Hz 声音音调峰值幅度随 θ 变化，实验与理论吻合；若输入 SOP 与声致双折射轴对齐则无 SOP 变化 [p5, p6]
  - DNANF vs SMF28 对比：光源谱宽 12.5 GHz，总光纤长 10 km，0.5 m 光纤圈贴在纸盒上，线圈直径<0.1 m，手机 275 Hz 音调，偏振计采样 5 kHz，4 芯 DNANF；结论 SOP 敏感度与标准 SMF 相当 [p5]
  - 页上引用 Nokia Bell Labs（We3-G3）SOP 感知：7.2 km ST-HCF vs 4.5 km SSMF，最大测地位移 SSMF 1.68 rad、ST-HCF 0.72 rad，至少 2.3 倍更小，输入 SOP 未对准最大敏感轴 [p7]
- 提到的公司/客户/产品/标准：Huawei；Nokia Bell Labs（引用）；DNANF；ST-HCF；SMF28；Φ-OTDR；ISAC
- 与业界对比或记录声明（SOTA/首次/record）：无 record；对 OFC 2026 的"HCF >100x SOP 敏感度"提出质疑（可能为 MPI 伪影）[p2, p6]
- 推荐配图页：p4（MPI 伪影：MZI 实验中窄线宽 vs 宽带源的 Stokes 起伏与 SOP 角-MPI 曲线）；p2（Backward Φ-OTDR vs Forward SOP 优缺点对比及 HCF 争议）
- 其他：Backward sensing 需窄线宽激光、难在在网相干链路部署；Forward SOP 可复用相干接收机 DSP、零附加硬件，适合 ISAC，缺点是空间分辨率低、标准 SMF 本身敏感度低 [p2]

### 0924-Th2-B3-Tampnet-偏振态监测电力线风致共振振荡.pdf（第1–5页）
- 讲者/机构：Alvaro Doval, Steinar Bjørnstad（Tampnet AS, Stavanger）；Krister de Vries, Kristina Skarvang Vaskinn（Svenska kraftnät, Sundbyberg）（作者名单看图核实）| 题目：State-of-Polarisation Monitoring of Wind-Induced Resonance Oscillations on Power Lines | 类型：学术论文
- 方向归属（主/次）：主 6 光纤传感（SoP/OPGW）/ 次 无
- 核心主张：
  1. SoP 传感可在带电运行的电力线（OPGW）上工作；24 天停电窗口证实特征源于风致振动，尽管存在 50 Hz 主导。
  2. 风致谐振呈间歇性，最强的谐振音调出现在低风速（0.5–3.5 m/s），风速升高后音调消失。
  3. 7 个月数据中 25 Hz 以上无显著活动，说明已安装阻尼器抑制了高频模式，SoP 可区分振动状态以主动识别疲劳性微风振动。
- 关键数据：
  - 试验：86 km OPGW 线路远端环回，往返 172 km；1550 nm CW 光源，EDFA 后发射 +17 dBm；接收 -24 dBm（ASE 滤波+衰减后）；PBS 接收机测量 S1；AC 耦合；逐小时风速来自近环回点的 SMHI 气象站 [p2]
  - 线路约 286 跨，每跨约 300 m，长度、张力、暴露各异 [p3]
  - 4 小时谱图：1 m/s 时为 2–20 Hz 内短时离散音调；4 m/s 时谱更弥散，另有明显 8.5 Hz 音调及其 17 Hz 谐波持续近 1 小时 [p3]
  - 30 天带电数据、10 分钟窗口、0.1 Hz 分辨率，标记高于窗口均值 20 dB 的峰：0.5–3.5 m/s 谐振峰最密集，集中在 2–12 Hz；2.5–5.5 m/s 峰明显减少；4.5–7.5 m/s 几乎所有离散音调消失，仅剩约 2 Hz 频带（可能为分裂导线尾流致振动经塔架传递）[p3, p4]
  - 六个月统计（1000 个峰值最高的 10 分钟窗口）：最大谐振运动发生在最低风速 [p4]
- 提到的公司/客户/产品/标准：Tampnet；SMHI（逐小时风速数据）；Svenska Kraftnät（瑞典输电运营商，两位合作者所属，题目页 logo，看图核实）；ICON；OPGW（86 km 在网 OPGW，远端环回共 172 km）
- 与业界对比或记录声明（SOTA/首次/record）：讲者称既有工作只是笼统地把 SoP 活动与有风联系起来，本文系统关联 SoP 谱与特定风致振动状态于长距在网 OPGW（页面原话：关系"has not been explored in detail"）[p2]
- 推荐配图页：p4（结论页：三种风速区间与谐振音调演变）；p3（谱图与不同风速 PSD 叠图）
- 未来工作：将单个音调与跨段参数关联；分析 1 Hz 以下；研究 2 Hz 与 10 Hz 分量 [p4]

### 0924-Th2-B4-DIAS与FARICE-海底光缆逐跨段微波频率光纤干涉实现深海地球物理监测.pdf（第1–7页）
- 讲者/机构：Georgios Aias Karydis, Nicolas L. Celli, David Craig, Örn Jónsson, Andrés Arnar Hlynsson, Eoin Kenny, Charis Mesaritakis, Christopher J. Bean, Adonis Bogris（题目页加粗为 Adonis Bogris；RNCP/西阿提卡大学、DIAS、FARICE，看图核实） | 题目：Per-Span Microwave Frequency Fiber Interferometry for Scalable Deep-Ocean Geophysical Monitoring | 类型：学术论文
- 方向归属（主/次）：主 6 光纤传感（海缆地球物理）/ 次 1 海缆
- 核心主张：
  1. 逐跨 HLLB 选段 + 10 GHz 微波频率光纤干涉（MFFI）+ 模拟 I/Q 下变频，可在在网长途海缆上实现低复杂度相位敏感传感。
  2. 同一架构覆盖从多小时变化到 25 Hz 的潮汐、风暴微震、远震，跨越数个量级时间尺度。
  3. 不需要高质量光纤激光器、Gsps 电子器件与 GPU 处理，为多条海缆规模化部署提供实用基础，有望用于海啸高风险地区。
- 关键数据：
  - 试验缆：爱尔兰–冰岛在网海缆（IRIS），询问器装在 Galway 登陆站；1,770 km；p3 未直接写跨段总数，只给出 100 km 跨段对应 1 ms 往返（图示 8 跨/17 跨谱图，跨段数以 p7 为准）[p3, p7，看图核实]
  - 参数：重复率 50 Hz（20 ms），1770 km 往返 17.7 ms，保护带 2.3 ms；脉宽 0.5 ms（1 ms 对应 100 km 跨段往返）；激光 1565 nm，对应 FBG 反射波长；用第二台 EDFA 模拟 WDM 传输以稳定在线 EDFA [p3]
  - 模拟 I/Q 下变频后以 1 Msps 采集，FPGA 抽取至约 16 ksps；响应带宽从多小时到 25 Hz [p2]
  - 运行 8 个月，解析潮汐、风暴及 2 次远震 [p7]
  - 远震示例：2026-04-20 Mw 7.4 北日本（Hokkaido）地震，0.001–0.01 Hz 滤波下可见 S 波与面波；另展示 2026年1–6月 4 次 Mw≥7 地震（含 Mw 7.8 Philippines）[p4]
  - 风暴微震：2026年2–4月平均谱图；对比冰岛 BORG、爱尔兰 IGLA 台站，2026年3月 6 天；二次微震（SM）与仅近岸跨段可见的一次微震（PM）[p5]
  - 潮汐：2026-02-13 至 02-23，通道1、3 紧密跟踪 Galway 港潮位；响应最强在 span 3、4、8，靠近 Rockall 盆地陡峭海底地形；多数迹线与泊松效应模型吻合，陡坡处幅度大且极性反转 [p5, p6]
- 提到的公司/客户/产品/标准：FARICE（海缆运营方）；DIAS；Horizon Europe ECSTATIC 项目（grant 101189595）；Cognilum；HLLB；OFDR；对比文献 Marra (Science 2022)、Mazur (ECOC 2025/2026, OFC 2025/2026)、Costa (2023)、Liu (GRL 2025)
- 与业界对比或记录声明（SOTA/首次/record）：声称首个在逐跨干涉配置中实现模拟 I/Q 下变频的 10 GHz MFFI（"First reported"）[p2]
- 推荐配图页：p6（单一询问器覆盖多个地球物理频段的总结页）；p4（Mw 7.4 Hokkaido 远震瀑布图与面波频散）
- 备注：p1、p3 已看图核实（p3 未直接写跨段总数，按 1,770 km/100 km 跨段推算约 17–18 跨）。

### 0924-Th2-C1-北邮与中科院-模式分集接收与自适应光学增强的星地自由空间光链路.pdf（第1–19页）
- 讲者/机构：Wenjie Guo, Yan Li, Ao Li, Xiaokai Li, Yaning Sun, Shuai Wei, Hongxiang Guo, Chao Liu, Ze Zhang, Jian Wu（题目页下划线为 Jian Wu；北京邮电大学 BUPT；中科院光电所 IOE；中科院空天信息研究院 AIR，看图核实）| 题目：Satellite to Ground FSO Communication Links enhanced by Mode Diversity Reception and Adaptive Optics | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（FSO）/ 次 无
- 核心主张：
  1. 提出模式分集接收（MDR）与自适应光学（AO）联合补偿湍流，在所有湍流条件下优于单独 AO 或单独 MDR。
  2. 强湍流下 AO 与 MDR 相互增强，接收功率提升超过 10 dB（仿真）；实验室模拟湍流实测提升超过 6 dB。
  3. 完成 1 Gbps GEO 星地下行传输，一小时内帧错误率小于 1%。
- 关键数据：
  - 背景：激光链路回传 1 TB 约 80 s（100 Gb/s），单星日回传 40 TB 用 10 min；RF X 波段 1.2 Gb/s 下 1 TB 约 2 天，日回传仅约 1 TB [p3]
  - 湍流影响：快衰落约 ms 级、约 30 dB；慢衰落（云雨雪雾）分钟到小时级、约 80 dB（OGS 南山站功率监测）[p4]
  - 下行接收孔径 0.5–1 m，主要为光斑破碎导致耦合入 SMF 效率下降；上行以闪烁为主，星上孔径 0.05–0.1 m [p5]
  - 已公开星地激光通信：下行已达 200 Gbps，上行演示很少（讲者页结论）[p6]
  - AO 缺点：复杂且成本高，强湍流下因感知速度与控制带宽受限效果差 [p7]
  - MDR：用 6 模光子灯笼（PL）低阶端口合并，99% CCDF 功率由 -58.52 dBm 提升至 -38.66 dBm（引用 Optics Express 31(21), 2023，光子灯笼模数失配模型；条件为讲者仿真）[p11]
  - 累计耦合效率在模式数超过 10–15 后不再增加 [p10]
  - GEO 下行仿真（CCDF=0.9 功率，D/r0=3–26）：D/r0=26 时 MDR 增益（有 AO）16.9 dB，图上另有 14.6 dB 等；D/r0=17 时读数 14.0/12.6 dB；AO 在 D/r0=26 时无 MDR 仅 0.4 dB，有 MDR 为 2.6 dB [p13]
  - 实验室（SLM 模拟湍流，3 个 SMF 端口 6 模 PL，IL 约1.5 dB）：D/r0=26 时 MDR 增益（有 AO）6.3 dB，AO 增益 0.9 dB，有 MDR 时 2.1 dB；D/r0=7 时 AO 增益最大 12.7 dB [p14]
  - 在轨 GEO 试验：卫星发射 2 W/1550 nm，线速率 1.048 Gbps，BPSK，望远镜口径 1.8 m，3 端口 6 模 PL 作 MDR；试验持续 2024年5月至 2026年1月 [p15]
  - AO+MDR 功率：平均功率 1 模 -46.2 dBm，3 模 -42.9 dBm（提升 3.3 dB），6 模 -42.6 dBm；99% CCDF 功率 1 模 -63.4 dBm，3 模 -51.3 dBm（提升 12.1 dB），6 模 -48.1 dBm；2 kHz 记录，统计窗 10 s，共 40 分钟 [p16]
  - 无错帧比例：仅 AO（LP01 端口）77.6%；第 2 端口 28.1%；第 3 端口 93.6%；3 模合并 99.0%；仅 AO 时 6.3% 帧 BER 在 1e-3–1e-2，16.1% 帧 BER>1e-2；数据 2025年12月11日 [p18]
- 提到的公司/客户/产品/标准：Starlink、Kuiper、AST SpaceMobile、GW、Spacesail、China Mobile、SpaceX/Blue Origin/Google（Suncatcher）等星座规划；p6 星地激光链路表（看图核实）：CAST/SJ-20 10 Gbps 双向、MIT LL/TBIRD 200 Gbps 下行、Airbus/TELEO 9 Gbps、Cailabs&Unseenlabs、CGSTL&BUPT/Jilin-1 100 Gbps 下行 113 s、Kepler/Tesat/Cailabs、SES&Cailabs、GW&BUPT 1.25 Gbps 297 s、BUPT&中科院光电所 1 Gbps 2 h、中科院空天院 120 Gbps 108 s；南山 OGS
- 与业界对比或记录声明（SOTA/首次/record）：提出"MDR 与 AO 联合湍流补偿"新方案；未见明确 record 声明 [p19]
- 推荐配图页：p18（无错帧比例：仅 AO 77.6% vs 3 模 MDR 99.0% 及吞吐时序）；p16（AO+MDR 模式数与平均/99% CCDF 功率曲线，12.1 dB 深衰落改善）；p13（GEO 下行仿真的 AO/MDR 相互增强）

## 本批小结
1. 偏振/SoP 监测正从"事件演示"转向"无监督/物理归因"：TCD 的 Fast-Slow DSVDD 将检出全部 5 个海缆接触所需告警从 91（STA/LTA）降到 13（B1）；Tampnet 用 SoP 分风速区间解读电力线谐振并验证阻尼器（B3）。共同点是复用在网光纤与低成本接收机，而非专用传感器。（B1、B3）
2. SoP 前向感知的物理边界被同行质疑：华为指出 MPI 会使窄线宽探测高估空芯光纤（HCF）SOP 敏感度，且输入 SOP 与声致双折射轴夹角决定读数；其 DNANF 与 SMF28 对比结论为敏感度相当，直接挑战 OFC 2026 的 ">100x" 报告。（B2）
3. 海缆传感在向"低复杂度、长距、可规模化"走：DIAS/FARICE 用 10 GHz MFFI 加模拟 I/Q 下变频，1 Msps 采集即可在 1,770 km 在网缆上覆盖潮汐至 25 Hz，明确以"无需高质量激光、Gsps 电子、GPU"作为卖点；与 TCD 的 SoP 全链路（无定位）形成"定位 vs 低成本"的取舍。（B4、B1）
4. 本批四篇传感文稿均依托运营商/海缆运营方的在网链路（Tampnet、FARICE、Svenska Kraftnät 相关），共存于 WDM 业务，试验时间尺度为数月到 8 个月，体现传感与通信共纤的工程成熟度。（B1、B3、B4）
5. 星地 FSO 的瓶颈从"链路容量"转向"大气湍流下的耦合稳定性"：下行已到 200 Gbps 量级，BUPT/中科院用 3 模 PL 的 MDR 使 99% CCDF 功率提升 12.1 dB，并在 GEO 在轨试验中实现 1.048 Gbps BPSK、无错帧比例 99.0%；AO 与 MDR 在强湍流下互补。（C1）
6. 本批与通信主线的接口：光纤 SOP 传感作为 ISAC 复用相干接收机 DSP 的思路（B2）与空芯光纤在网部署的前景（B2）相连，值得后续与相干/海缆方向的稿件对照。（B2）
