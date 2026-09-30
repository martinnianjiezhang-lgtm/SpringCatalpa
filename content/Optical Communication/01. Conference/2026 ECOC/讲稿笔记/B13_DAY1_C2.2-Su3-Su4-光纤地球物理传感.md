---
title: "B13 · DAY1 · C2.2-Su3-Su4-光纤地球物理传感"
tags:
  - ECOC2026
  - DAY1
---

# B13 笔记（Workshop：Telecom Fiber as a Geophysical Sensor for Earthquake, Tsunami and Microseismic Monitoring，ECOC 2026，2026-09-20 下午 Su3）

说明：01-主席-开场.pdf 仅 2 页（标题页+一页"What can be detected today and where to go tomorrow?"话题概览：trawler detection、DAS minor earthquake detection、whale vocalisation、surface vessel signature detection 等图示），不构成独立讲稿，未单列。

### 0920-pm-Su3-G-02-LAquila-海缆微赫兹偏振传感.pdf
- 讲者/机构：Antonio Mecozzi / University of L'Aquila | 题目：Opening a New Window on Earth Dynamics: Microhertz Polarization Sensing with Submarine Cables | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS（偏振传感）；次 1 相干/海缆
- 核心主张：
  1. 光纤（海缆偏振）可作为分布式磁力计，处于"地球上最安静的电磁环境"中（p13）。
  2. 在两次地震（本地 M4.5、远处 M7.4）之前观察到磁场异常（p13）。
  3. 观测到的磁场时间特征可能体现外核与地幔的耦合（p13）；p12 页示意外核由 MAC 平衡（磁力、阿基米德浮力、科里奥利力）主导，所述磁场为地磁场。
- 关键数据：
  - 链路：Catania–Haifa 海缆，滤波带 350–650 µHz，观测量 Δφ1（偏振相位量）[p2, p3]
  - 事件：2026-07-23 22:55:57 UTC M4.5 西西里地震（深度 245 km）；2026-08-10 12:34:28 UTC M7.4 哥伦比亚地震（深度 103 km）；另标 2026-07-04 G3 与 2026-08-18 G2 太阳风暴 [p2, p4，看图核实]
  - 太阳风暴对照：2026-07-04 G3；2026-08-18 G2 [p4]
  - 同一缆中两根光纤（CAT02 与 HAI01）滤波后迹线"几乎完全重合"（第二图为 HAI01 反相后重合）[p6，看图核实]
  - 峰间隔表（2026-07-17 至 07-23 共 7 个间隔，19.198 h–20.826 h）；平均间隔 19 h 45 min 17 s = 19.755 h；科里奥利周期：Catania 纬度约 37.5° 对应 T≈19.71 h，震中纬度约 38.9° 对应 T≈19.07 h [p10]
  - 长期谱（2025-04-20 至 2026-07-31）：峰频 1.45953×10^-5 Hz，T_peak = 19.032 h；PSD 峰值约 60 dB/Hz 量级（图读数，粗略）[p11]
  - 频谱图观测时段 2026-07-01 至 2026-08-31 [p4]
- 提到的公司/客户/产品/标准：Catania–Haifa 海缆（未见运营商名）；EU 项目标志（页脚 "ECST…" 字样被遮挡，看图仍不可读）
- 与业界对比或记录声明（SOTA/首次/record）：讲者称"地球上最安静的电磁环境"；地震前磁场异常为观测声明，未见"首次/record"字样。[p13]
- 推荐配图页：p11（长期功率谱上 19.03 h 峰与科里奥利周期对比）；p4（两根光纤的 µHz 谱图与地震/太阳风暴标注）

### 0920-pm-Su3-G-03-INGV-电信网做多尺度监测.pdf
- 讲者/机构：André Herrero（INGV，意大利国家地球物理与火山研究所）et al. | 题目：From Sensing to Services — Telecom Networks as Multi-Scale Monitoring Infrastructures | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS；次 5 固定与无线接入（FTTH 作为监测基础设施）
- 核心主张：
  1. 未来不是单纯光纤传感，而是电信网络成为分布式监测基础设施：Sensing + Communication + Computing + Storage + Capillarity → Operational Services [p10]
  2. 机会在于集成基础设施而非光纤平面本身（Key Takeaway，p3 被观众遮挡，原意如此）
  3. 试点与服务之间仍隔着六项：Physics（耦合/标定/灵敏度）、Geometry（定位/可观测性）、Operations（授时/在线率/维护）、Algorithms（误报/置信度/自动化）、Governance（数据访问/隐私/所有权）、Economics（谁付费/谁受益）；"Operational readiness is a system property, not a sensor specification" [p8]
- 关键数据：
  - 三个尺度：Global/Ocean（海缆：地震、海啸、海洋信号）、Regional/Metro（骨干与城域：地震监测、火山、滑坡）、Local/Access（FTTH 与楼内光纤：结构健康监测 SHM、城市基础设施、保险服务）[p4]
  - 已示范内容（项目 MEGLIO / FAAS / ODEONS）：在运营（lit）电信设施上检测；小事件灵敏度；干涉测量数据检测到 Mag 2.6 地震，距光纤 17 km；有傅里叶谱与检测阈值（距离-震级）图 [p5]
  - 下一步：Localize（线形传感几何）、Magnitude（振幅无关的震级估计）、Fuse（与常规地震台数据融合）、Operate（接入实时监测流程，标志 SENSEI）[p6]
  - FTTH 双用途：能力=对建成环境的极强毛细覆盖、高灵敏干涉测量、低维护连续监测；挑战=不受控耦合、"感知一切"带来的隐私、边缘计算/存储；机会=SHM、基础设施管理、保险、城市监测 [p7]
  - 页面未给出具体灵敏度/距离数值以外的量化指标
- 提到的公司/客户/产品/标准：MEGLIO、FAAS、ODEONS、SENSEI（项目/平台名）；FTTH
- 与业界对比或记录声明（SOTA/首次/record）：无（系统综述与路线性质）。
- 推荐配图页：p10（结论"系统集成公式"）；p8（六类障碍：从试点到服务）；p4（三尺度分层）

### 0920-pm-Su3-G-04-NokiaBellLabs-炒作与现实的差距.pdf
- 讲者/机构：Nokia Bell Labs（讲者姓名页面未显示；引用文献作者含 Mazur et al.）| 题目：Deep-Ocean Seismic Monitoring Today（首页标题，看图核实；文件名副标为"炒作与现实的差距"）；含引用的 Tsunami Detection Using Subsea Cables | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS（海缆 DAS、海啸/地震）；次 1 相干/海缆
- 核心主张：
  1. 利用在役海缆做海啸检测：远场海啸可沿整条缆长被检测到；只需占用单个 WDM 通道（页面"single WDM channel"，p18；p8 写 Single 100GHz WDM needed，与在线业务兼容）；可高度扩展，尤其在监测稀疏地区。
  2. 地震和海啸预警：震级关键→波高；环境非常复杂；"观测到海啸是必要但不充分条件"。
  3. 批评性评述：没有完美传感器，多样性是关键；传感器只是预警系统一部分，需要跨学科合作（p18）。
- 关键数据：
  - 实验装置：长距 DAS（Long-Reach DAS），腔稳光纤激光器、基于 PIC 的模拟光学模块、FPGA + 可流式 GPU；海缆约 4400 km，约 100 个光中继器；美国国内缆 California–Hawaii；中继器内无光纤布拉格光栅；水深多处超过 4000 m [p2]
  - 实验：约 4400 km 加州—夏威夷美国国内海缆、约 100 个光中继器、中继器内无 FBG、水深超过 4000 m；空腔稳频光纤激光 + PIC 模拟光学 + FPGA/GPU 流处理；监测回波相对功率图中有约 −15 dB、−7 dB、−5 dB 标注（看图核实，照片被遮挡，对应关系仍不清）[p2]
  - 事件：2025-07-29 堪察加半岛 M8.8 逆冲地震，史上第 6 大，M>8.5 约每十年一次 [p3，看图核实]
  - 海啸监测：距 Morro Bay (CA) 25 km（水深 <100 m）与 1500 km（水深 >1000 m）两处应变率与谱图，时间轴 -2 至 16 小时，应变率量程 ±0.5 nε/s，海啸信号在约 6 小时后出现（谱图约 10^-3 Hz 量级）[p6]
  - "Tsunami Heading for California"：带通 100 µHz–50 mHz，沿缆 ~15 km、500、1000、1500、2000、2500、3000 km（距 CA）及 ~500 km from HI (~3900 km from CA)，波列到达出现在地震后约 5.5–8 小时，随距离延后 [p7]
  - 参考数据：NOAA MOST（Method of Splitting Tsunami）模型与 DART 浮标（HI 与 CA 近海）[p5，看图核实]
  - 日本三陆（Sanriku）1996 与 2015 海缆系统对照：2026-04-20 M7.7 地震；1996 系统有无中继备用光纤适合 DAS，2015 系统光纤全部用于通信，DAS 须与通信并行；标距 GL 105.9 m 与 9.9 m 对比：大地震下 DAS 记录饱和，标距缩小 10 倍则削波电平大 10 倍；标距 10 m 时最大幅度对应"几 cm/s²"（引用 JpGU 2026，非 Nokia 自有数据）；大震期间未识别到 S 波 [p9–p14]
  - "Where's the TSUNAMI?"：M7.5，距缆 <50 km；海底节点被甩掉；应变量程约 ±5000 nano-strain；挑战=地震信号远大于海啸信号，需频域滤波，且仪器动态范围（地震信号空间尺度 <<10 m，海啸 >>10 m）与强震下缆位移 [p17]
  - 局限：远场海啸、缆的安静段（p8）
- 提到的公司/客户/产品/标准：Nokia Bell Labs；NOAA MOST、DART；引用 T. Tonegawa and E. Araki, GRL 51(11), 2024（p8：首段中继限制"从来不是真的"）
- 与业界对比或记录声明（SOTA/首次/record）：声明"first repeater limitation isn't real, and never was!"（首跨中继限制不存在）；标题 "Are We Done? Please!"，并称当前瓶颈是成本与缆接入而非技术。[p8]
- 推荐配图页：p2（长距 DAS 实验装置与 4400 km 加州–夏威夷海缆）；p7（不同距离处海啸波列随时间到达）

### 0920-pm-Su3-G-05-NTNU-从地震到鲸鱼探测.pdf
- 讲者/机构：NTNU（讲者未见姓名；引用 Rørstadbotnen and Landrø, 2026）| 题目：从挪威地震到鲸鱼探测（首页 "Recent earthquake Northern Norway"，英文总题目未见）| 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS；次 无
- 核心主张：
  1. 可以检测运动的水下物体所在深度，也可估计其大小（p20）。
  2. 蓝鲸检测距离约 40 m，大型船只 400 m（p20）。
  3. 蓝鲸靠近海床时常见 Scholte 波；仍有大量测试待做：AUV 穿越、管道交叉等（p20）。
- 关键数据：
  - 场景：斯瓦尔巴 Ny-Ålesund 与 Longyearbyen 之间两根光纤（Inner/Outer fibre），沿纤距离约 0–250 km，水深剖面显示 [p5]
  - 长须鲸追踪：约 5 小时（起于 09:17:57）追踪多头长须鲸，标注 inner/outer 缆路线与检测范围（10 km 比例尺，沿纤里程标记 46–95）[p8]
  - 船只定标（L=船长，w=宽）：Kvitungen L=45 m w=8 m；Helmer Hanssen L=64 m w=13 m；ODEN L=108 m w=31 m；Le Commandant Charcot L=150 m w=28 m；两个频带 5–45 Hz（p11）与 0.008–0.05 Hz（p12）[p11–p12，看图核实]
  - 模型：振荡球源低频 DAS 响应，源深 100/200/300 m，应变率峰值约 10×10^-7（100 m）；脉宽∝源深，衰减∝1/z³ [p16]
  - 过零点宽度 vs 最大应变处水深：期望曲线 x0=√2·z，最佳拟合 x0=41.94+0.66z；数据点覆盖 LCC（Isfjorden、Kongsfjorden）、HH、ODEN，水深约 100–410 m [p17]
  - 汇总表（p20）：蓝鲸 1–13 的长度取假设值 26±1 m；主频 f_obs 在 0.0338±0.003 至 0.1009±0.016 Hz；速度 U 约 1.7±0.2 至 5.3±0.9 m/s；估计深度 z 约 21–42 m。船只：HH 频率 0.0228±0.003 Hz，U 2.9±0.5(4.5) m/s；ODEN 0.0214±0.004 Hz，U 4.8±0.8(4.5)；LCC 0.0239±0.003 Hz，U 7.2±0.9(7.0)。结论：蓝鲸探测范围约 40 m、大船约 400 m，可估计深度与尺寸（看图核实；其余列 Arms、z、L 估计小字仍不清，不逐项摘录）
- 提到的公司/客户/产品/标准：Kvitungen、Helmer Hanssen、ODEN、Le Commandant Charcot（研究/极地船）；Nordlandsbanen 铁路脱轨（2024）、落石与雪崩事件为引子（p3–p4）
- 与业界对比或记录声明（SOTA/首次/record）：引用 2023 年多头鲸同时追踪工作（"Simultaneous tracking of multiple whales using fibre-optic cables"，p9）；无 record 声明。
- 推荐配图页：p8（5 小时内多头长须鲸沿两条缆的轨迹）；p20（蓝鲸/船只参数汇总表与结论）

### 0920-pm-Su3-G-06-NECLabs-海缆探测地震与船只.pdf
- 讲者/机构：NEC Labs（讲者姓名页面未显示）| 题目：DAS 海缆探测地震、潮汐、海浪与船只（英文原题页未显示，p1 为地震 DAS 图：Mw5.3/Mw3.1 June 29，看图核实）| 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS；次 无
- 核心主张：
  1. DAS 可感知地震波、潮汐、海浪、船只等（p14）。
  2. 分立地震仪 SNR 好、空间分辨率差；光纤 DAS 相反（p14 笑脸/哭脸表）。
  3. 空间平均与机器学习可提升地震检测与定位精度；DAS 可补充常规地震仪用于预警，并可在缺少常规仪器的区域检测微地震（p14，最后一条被遮挡，意思如此）。
- 关键数据：
  - 事件：Mw5.3 2026-06-29 03:32:39，60.237N, 145.910W，深度 13.3 km；Mw3.1 同日 03:37:26，60.200N, 145.922W，深度 10.2 km；应变率色标约 ±16 nε/s，缆长约 150 km 尺度 [p2]
  - 波形：三个位置 30.5 / 65.7 / 110.5 km 的应变率，Mw5.3 与 Mw3.1 波形；Mw3.1 的 P、S 波谱与环境谱对比，应变率幅度约 ±200 nε/s，谱幅约 10^-10–10^-8 nε/√Hz 量级（图读数，粗略）[p3]
  - 其他事件：Mw2.6 2026-05-21 04:36:55，59.702N, 146.772W，38.6 km 深 [p4，看图核实]
  - 不同距离波形对比：Mw2.6 107 km（1–10 Hz）；Mw3.1 91 km（2.5–10 Hz）；Mw3.0 209 km（0.8–10 Hz）；Mw4.9 623 km（1.5–8 Hz）；Mw5.4 1190 km（1–6 Hz）；Mw5.6 1772 km（0.7–4 Hz）；P/S 波框选可辨 [p7]
  - 潮汐/海浪：光纤 137.5 km 处均方根海浪应变随时间，时段 07-01 至 07-21 出现周期性起伏，幅度约 1–3 nε 量级（读图，略估）[p9]
  - 风速对比：平均海浪应变（0–7 nε）与风速（约 0–17 m/s）及风向随时间同步起伏，时段 07-01 至 07-21 [p10]
  - 静风 vs 大风：应变率谱在约 0.1–3 Hz 分离，大风日峰值约 10^-8 nε/√Hz，静风日约 10^-9；高于约 3 Hz 两者重合于约 10^-10 [p8]
  - 船只检测：5 月 18 日 07:00–07:15 当地时间瀑布图，距离 2–8 km 处斜线轨迹；另有 5 月 30 日事件 [p11, p13]
- 提到的公司/客户/产品/标准：NEC；p16 为 MDPI Sensors 期刊特刊征稿页（Environmental Sensing over Telecom Fiber Cables，客座编辑 Dr. Ezra Ip，截稿 2027-04-10，Impact Factor 4.0、CiteScore 9.4；主题含 Rayleigh/Brillouin/Raman 分布式传感、前向传输传感、ISAC "Integrated sensing and telecommunications"、光子集成、多模/多芯/空芯光纤传感等，看图核实）
- 与业界对比或记录声明（SOTA/首次/record）：无。
- 推荐配图页：p3（Mw5.3/Mw3.1 波形、P/S 波与谱）；p7（六个震级-距离-频带的波形对比，至 1772 km）；p14（DAS 与地震仪 SNR/分辨率对比结论）

## 本批小结
1. 海缆/电信光纤传感已从"能不能测到"进入"如何变成运营服务"：INGV 明确把"感知+通信+计算+存储+毛细覆盖"作为系统集成公式，并列出物理/几何/运维/算法/治理/经济六道障碍（03 INGV p8、p10）；Nokia 同样强调传感器只是预警系统一部分（04 Nokia p18）。
2. 在役长距海缆上可以只占一个 WDM 通道做 DAS：Nokia 约 4400 km、约 100 个中继器的加州–夏威夷缆，无 FBG，能在远场（距 CA 1500 km，水深 >1000 m）检测到海啸；但近岸/强震下受缆位移、动态范围（地震 <<10 m 尺度 vs 海啸 >>10 m）限制（04 Nokia p2、p6、p17）。
3. DAS 大震饱和是共同的工程约束：Nokia 引用的三陆数据显示标距 105.9 m 与 9.9 m 的削波差 10 倍，缩短标距可提高削波电平（04 Nokia p11）；NEC 则给出 DAS 与分立地震仪 SNR/空间分辨率互补的判断，并展示 Mw2.6–5.6、107–1772 km 的可辨识波形（06 NEC p7、p14）。
4. 传感对象从地震扩展到海洋与生物/船只：NEC 的潮汐、海浪与风速关联及船只瀑布图（06 NEC p8–p13），NTNU 在斯瓦尔巴用海底光纤追踪长须鲸、估计蓝鲸/船只深度与尺寸，蓝鲸检测距离约 40 m，大船 400 m（05 NTNU p8、p20）。
5. 偏振/相位类"整链路"传感打开了 µHz 地球物理新窗口：L'Aquila 用 Catania–Haifa 海缆在 350–650 µHz 观测到 19.03 h 谱峰并与科里奥利周期对比，并声称地震前磁场异常；属于探索性声明，需独立验证（02 L'Aquila p10、p11、p13）。
6. FTTH/接入光纤被视为双用途基础设施（公共地震学+私域 SHM/保险），但耦合不受控与隐私是障碍（03 INGV p7）；与 ISAC 征稿方向一致（06 NEC p16）。
