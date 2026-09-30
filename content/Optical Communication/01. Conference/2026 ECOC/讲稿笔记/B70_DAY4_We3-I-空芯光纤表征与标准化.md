---
title: "B70 · DAY4 · We3-I-空芯光纤表征与标准化"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We3-I-00-全场连拍-空芯表征与部署.pdf（第1–43页）
- 讲者/机构：Nicolas K. Fontaine / Nokia Bell Labs（致谢含 Southampton/Microsoft 等合作者，p1） | 题目：Ultra-high resolution and long-range OFDRs for characterizing and monitoring Hollow-core DNANFs | 类型：邀请报告
- 方向归属（主/次）：主 1（海缆/长途，空芯光纤监测与表征）；次 6（光纤传感/背向散射）
- 核心主张：
  1. 空芯光纤（HCF）背向散射比 SMF 低 30–45 dB，利于 BiDi 传输，但难以监测；用相干 OFDR 可同时获取双折射、传播常数、散射系数与衰减 [p2, p11]。
  2. 两类 OFDR：长距（海缆用 chirped-pulse，约 100 km 量级）与短距（约 100 µm 分辨率）[p2, p43]。
  3. 结论页：首次分布式测量反谐振 HCF 侧壁背散射（约 124 µm 分辨率、5 km 长度），首次用散斑分析测得 HCF 分布式偏振特性，首次长距 OFDR 测量约 100 km HCF（3–25 m 分辨率）[p43]。
- 关键数据：
  - 低损 HCF 现状（作者引用）：MSFT DNANF5 2024 0.11 dB/km；LinFiber 4TDNANF（S. Gao, Optica 2025）0.1 dB/km；LinFiber IT4DNANF（ECOC PDP 2025）0.05 dB/km，约 40 km；YOFC ST-HCF 0.05 dB/km [p2]。
  - 两类背散射：气体分子动态 Rayleigh 散射约比 SMF 低 30 dB，展宽约 500 MHz，对压力敏感；玻璃表面粗糙度静态散射约低 45 dB，形成固定散斑指纹 [p11]。
  - 早期首次 HCF OFDR：219 m NANF，SMF 约 -76 dB/m，NANF 低约 45 dB（约 -121 dB/m），1 m 分辨率，参考 Optica 8, 216（2021）[p14 图像页]。
  - 长距 OFDR 硬件：约 10 台原型；激光器 OE-Waves、NKT X15、NIST 真空腔外部稳频；硅光 PIC 相干收发；FPGA 到 GPU 100 GB/s GPUDirect；调制带宽 250 MHz 对应理论 0.3 m；已测量 >4 条海缆；除激光器外可量产 [p15 图像页]。
  - 啁啾脉冲压缩：100 km 长啁啾脉冲压缩约 1,000,000 倍至 0.5 m，相对短脉冲 OTDR 约 60 dB SNR 增益 [p18]。
  - 100 km HCF OFDR：前向/后向发射反射谱，端面回波 FWHM 约 25 m，图中标注 3 m、10 m FWHM 事件，标注约 50 dB 与约 90 dB 动态范围（条件看不清）[p7]。
  - 衰减与散射分离：2.5log10(F/B) 得衰减，示例拟合约 0.2 dB/km；10log10(F×B) 得散射系数，与 R^-6 成正比，讲者称"极重要的拉丝工艺信息" [p20 图像页]。
  - 扫频 OFDR（OFDR #2）：>100 nm 幅相传递函数，光谱分辨 <20 MHz，扫速 2000 nm/s；HCF 实现用 20–200 nm 扫频、10–40 nm/s，处理 800 GHz 段得 124 µm 分辨率 [p24, p27]。
  - 550 m HCF 测量（124 µm 分辨率），斜率反映局部散射系数与积分损耗，含散斑振荡与双折射引起的偏振起伏 [p29–30]。
  - 热敏感：HCF 光谱移位对温度的敏感度比 SMF 小 22 倍（拟合 y=0.045x，SMF 移位 0–约55 GHz 对应 HCF 0–约2.4 GHz）[p35 图像页]；热光系数影响 SMF 模式，热膨胀对二者均有，且小 10–30 倍 [p34]。
  - 5 km HCF 双折射：光谱移位 0.02–0.075 GHz，前向与反向测量吻合；对应拍长数值被截断，看不清 [p41 图像页]。
  - 100 km AR-HCF C+L 链路上的 FDM-OTDR：135 GBd、800 Gb/s、PCS-16QAM，150 GHz 间隔，C 1524.30–1572.27 nm、L 1575.16–1626.43 nm；OTDR 脉冲 6 µs、峰值 20 dBm、FDM 9 路、160–240 MHz、Δf=10 MHz、1510 nm、重复周期 1 ms；放大 OTDR 可测单跨损耗 >约 20 dB，分辨率 45–900 m（OFC'25 Th3F.7、PDP Th4A.3）[p13 图像页]。
  - 海缆用例：6000 km 约 1000 dB 损耗由 >100 个放大器补偿，反射信号约 -112 dB/m（SMF 72 dB/m + 40 dB 环回损耗）[p6]。
  - 海底地震跟踪：6.3 级、Ferndale 附近，5.2 km/s，6000 km 跨大西洋追踪（引自 M. Mazur, OFC 2024 PDP）[p4–5]。
- 提到的公司/客户/产品/标准：Nokia Bell Labs、Microsoft、LinFiber、YOFC、OE-Waves、NKT X15、NIST；Luna OVA（同类技术别名）；OFC'25 论文；p20–21 出现中国移动 HCF 监测页（Zhejiang trial / Lab test）的翻拍，讲者标注"FANTASTIC OTDR RESULTS!! Unclear what the ECOC photo policy is"。
- 与业界对比或记录声明（SOTA/首次/record）：首次长距 OFDR 测约 100 km HCF（3–25 m 分辨率）；首次 HCF 侧壁背散射分布式测量（124 µm，5 km）；首次用散斑分析测 HCF 分布式偏振特性 [p43]。
- 推荐配图页：p7（100 km HCF 前/后向 OFDR 反射曲线）；p35（HCF 与 SMF 热敏感对比 22×）；p13（100 km AR-HCF 的 C+L 传输与 FDM-OTDR 联合装置）

### 0923-We3-I-00-全场连拍-空芯表征与部署.pdf（第44–67页）
- 讲者/机构：S. Zampato（Univ. of Padova）等；合作方 Univ. of Southampton ORC、Microsoft Azure Fiber（p44）；论文编号 We3-I2/1089（p54–59 页脚） | 题目：Distributed Measurement of Magnitude and Orientation of the Local Birefringence Vector in a 5-Tube NANF | 类型：邀请报告
- 方向归属（主/次）：主 6（光纤传感/偏振反射计）；次 1（空芯光纤长途传输的表征）
- 核心主张：
  1. 首次完整分布式测量 NANF 与 DNANF 的局部双折射矢量（幅度与方向）[p65 图像页]。
  2. 内部一致性高，与有限元仿真吻合，揭示弯曲引起的双折射影响 [p65]。
  3. 局限：样品为研究用途，不能代表全类别；仍无法定量区分本征与弯曲双折射；欢迎各方送样 [p66]。
- 关键数据：
  - 方法：偏振敏感反射计（PSR），至少两个不同输入 SOP，测背散射 SOP，解微分方程得双折射矢量 [p48–50]。
  - P-OTDR（NANF）：2 ns 脉冲、1550 nm、每 2 µs 一个、3 种输入 SOP；SNSPD 探测（探测效率 >85%、暗计数 <100 Hz、恢复时间 <100 ns、到达时间精度 >10 ps）；空间分辨率约 30 cm，采样 15 cm（1 ns），单次测量 60 s，脉冲数 30×10^6 [p53–54 图像页]。
  - P-OTDR（DNANF，620 m 样品）：700 ps 脉冲，每 2.5 µs；分辨率约 10 cm，采样约 5 cm（300 ps）；测量 120 s；脉冲数 48×10^？（指数看不清）[p61–62]。
  - NANF 分布式双折射 β 约 0–2.5 rad/m（长度轴 z 数值看不清），前/后向测量高度吻合；绕线直径 d1=159 mm 与 d2=76 mm 对比，弯曲使 β 增大，在图中数值约 0.2–1.5 rad/m 范围随弯曲方向变化 [p59 图像页]。
  - 扭转诱导双折射 Bs 近零，说明扭转贡献可忽略；DNANF 同样观察到近零并且前后向吻合 [p57, p63–64]。
  - 背散射来源引用：表面粗糙度与充气分子（Slavik, Opt. Express 2022）[p51]。
- 提到的公司/客户/产品/标准：Univ. of Padova、Univ. of Southampton（Poletti 组）、Microsoft Azure Fiber、SNSPD 设备（品牌看不清）；5-tube NANF 与 DNANF。
- 与业界对比或记录声明（SOTA/首次/record）：First complete distributed measurement of local birefringence vector in NANF and DNANF [p65]。
- 推荐配图页：p59（NANF 分布式双折射前后向重合与弯曲仿真对比）；p54（P-OTDR 装置与 SNSPD 参数）

### 0923-We3-I-00-全场连拍-空芯表征与部署.pdf（第68–90页）
- 讲者/机构：Dong Wang / China Mobile Research Institute（Principal Researcher，p68） | 题目：Field Deployment Practice, Key Challenges, and Standardization Outlook of Hollow Core Fibers and Transmission Systems | 类型：邀请报告
- 方向归属（主/次）：主 1（长途/海缆/DCI，空芯光纤部署）；次 2（Scale-across）、次 5（前传/PON）、次 3（Scale-out 空芯）
- 核心主张：
  1. HCF 现在即可部署：中国已有网络在运行，两年记录显示无劣化 [p90 Take-aways]。
  2. 难题已从光纤转移到现场：如何熔接、如何排除气体、如何监测看不进去的链路 [p90]。
  3. 互操作性是"现在做决定、以后付代价"，标准化应考虑结构 [p90]。
- 关键数据：
  - 进展：多家厂商可产 <0.1 dB/km；单次拉丝长度达 80 km，PMD <0.1 ps/km^1/2；TDNANF-4（Linfiber/CMCC）<0.1 dB/km@1550；DNANF-5（Microsoft）约 0.09 dB/km@1550、<0.2 dB/km@66 THz；ST-HCF（YOFC）约 0.04 dB/km；IT-HCF（Linfiber）约 0.05 dB/km；2023–2025 单价下降 >500 倍，拉丝长度从 <1 km 增至近 100 km [p69]。
  - 场景表：HCF 长度占比——接入约 70%，骨干约 20%，海缆约 10%；DCN 等 10s m–2 km 场景需低功耗/低时延，不需要低传输损耗 [p70]。
  - DCN：HCF-SMF 连接器损耗比光纤本身更关键；固定方案最低约 0.3 dB/对（等效约 3 km 光纤衰减）；TEC 0.13 dB、GRN 0.15 dB、斜角对准 0.2 dB、SMF 偏移+GRIN 1.2 dB；减小外径方案 125 µm HCF 为 0.25 dB/km（Microsoft，ECOC 2025），预期 0.2 dB/km，HCF-SMF 0.01–0.1 dB [p71]。
  - 低时延前传：CDR 替代 DSP，模块时延约降 98%，光纤时延降约 30.2%，功耗降 24.99%（1.709 W 到 1.282 W）；总时延柱状图：DSP+SMF 14559 ns、CDR+SMF 14511 ns、DSP+NANF 10177 ns、CDR+NANF 10130 ns [p72]。
  - DWDM 前传：10 km AR-HCF，同波长 BiDi，2dir×40λ×224 Gb/s=16.7 Tb/s，约为现有商用 WDM 前传的 55 倍；用 105 m DCF 使总 CD 落在 ±14 ps/nm 内；BER 门限 3.8×10^-3（Mingqing Zuo, ECOC 2025 O-SC7-08.3）[p73]。
  - 高 SE 实验：85 GBd DP-144QAM-PCS，100.4 km DNANF-5，净速率 1.09 Tb/s；15 dBm 入纤无明显非线性，而 G.652 超过 10 dBm 出现显著非线性（J. Sun, OFC 2025）[p76]。
  - 宽谱：S+C+L（1470–1626 nm），DP-144QAM-PCS，100 km DNANF-5（0.15 dB/km@1550），377.6 Tb/s（259×2 信道），纯掺杂光纤放大（TDFA+EDFA，无 Raman）；分段：S 波段 119.57 Tb/s（2 向×131λ）、C 139.80 Tb/s（2 向×68λ）、L 118.24 Tb/s（2 向×60λ）；波特率 S 48 GBd@50 GHz、C 85 GBd@87.5 GHz、L 98 GBd@100 GHz；JLT 44(6), 2026 [p78 图像页]。
  - 单跨长距：仅用高功率 EDFA，400G/800G/1.2T 分别传输 726.1 km/611.9 km/436.1 km HCF；链路损耗预算约 73.3/60.9/43.6 dB；平均熔接损耗 0.083 dB [p79]。
  - 多跨超长距（引 D. Ge ECOC 2025 W.03.05.5；Y. Hong ECOC 2025 Th.03.02.2）：较 SMF 最优情形距离延伸 >3×；DNANF-5 在 IMI=-64 dB/km 时 1013.8 Gb/s@3459.8 km，IMI=-74 dB/km 时 1001.15 Gb/s@10714.3 km；总速率 25.6 Tb/s@1439.2 km、20.6 Tb/s@2878.4 km、10.3 Tb/s@6116.6 km、3.2 Tb/s（8×400G）@11154 km；3238.2 km 的谱图 [p80]。
  - 价值评估：网络升级容量收益 N30 提升 12%、NAN100 提升 70%，跨距 80→240 km，OA 站点减少 68%/Gb/s；选择性升级 50% 链路对比 2×SMF 方案，每 Tb/s 成本降 38%、总成本降 25%，光纤成本为 SMF 的 5–10 倍；海缆对比 MAREA，26 芯、C 波段 5 THz、73.5 GBd，OA 站点减少 2/3，0.07 dB/km 容量翻倍，0.05 dB/km 时 12 kW <18 kW（P. Poggiolini, ECOC 2025 W.02.01.83）[p81]。
  - 现网案例：2024.06 深圳-东莞 0.6 dB/km、10 km；2024.09 无锡 0.128 dB/km、18.4 km；2024.11 金华 0.21 dB/km、42.7 km；中国首个商用部署：深圳证券交易所至香港证券交易所，34 km AR-HCF/SMF（4/96）缆，"今天开始部署"，最低衰减 0.066 dB/km [p82]。
  - 气体吸收：CO2 吸收线 1602.876 nm（分辨率 20 pm）附加损耗，密封方案缆前 0.04 dB/km、部署后 0.078 dB/km；单端充气吹扫 30.0 km 可完全消除，双端充气 17.6 km 残余约 0.10 vs 0.27 dB/km（读数）；耗时 [p85 图像页]。
  - 长期稳定性：无锡 18.4 km TDNANF-4 链路无充气/吹扫监测两年（2024/10/18、2025/09/20、2026/05/26），衰减与熔接损耗稳定，熔接损耗变化 -0.19 至 +0.18 dB，部分下降可能因盘绕应力释放 [p86]。
  - 互操作：4E 与 5E 结构耦合损耗，大管与芯径主导，容差约 ±7%；不同结构的 HCF 最低损耗 >0.09 dB，远高于 G.652.D 与 G.654.E 的约 0.03 dB [p87]。
  - OAM：正压充气 HCF 瑞利背散射更强、OTDR 功率要求降低；充气后熔接点反射被掩盖，单端 OTDR 损耗检测失效；双端部分充气无法防止运行中缆断漏气 [p88]。
  - 标准化：CCSA 已批 2 份技术报告、3 个项目在研；ITU-T SG15 2025.10 相关活动，2026.7 启动 GSTR.hcf；IEEE 802.3 "Fiber for AI" workshop 称 HCF 用于 448G/lane 以太网是有前景的趋势 [p89]。
- 提到的公司/客户/产品/标准：China Mobile、Huawei、YOFC、Linfiber、FiberHome、ZTE、Microsoft（后几家为 p82 试验图 logo，仅见于图）；CCSA、ITU-T SG15 GSTR.hcf、IEEE 802.3 NEA、G.652.D、G.654.E；TDFA/EDFA；MAREA 海缆。
- 与业界对比或记录声明（SOTA/首次/record）：377.6 Tb/s 为"百公里级 HCF 系统所报告最大容量"[p78]；400G/800G/1.2T 单跨 726.1/611.9/436.1 km 称为传输记录 [p79]；中国首个商用 HCF 部署 [p82]。
- 推荐配图页：p70（应用场景与 HCF 价值矩阵）；p78（377.6 Tb/s S+C+L 装置与频谱）；p82（现网试验与首个商用部署地图）；p88（OTDR 监测与充气问题）

## 本批小结
- 空芯光纤已从"实验室光纤"转向"现场工程"：中国移动给出 2024 三次试验到 2026 年首个商用（深圳-香港，34 km，最低 0.066 dB/km），并有两年无充气监测数据；难点集中在熔接成功率/速度、端面进水、CO2 吸收、互操作与 OAM（Dong Wang 一讲，p82–90）。
- 表征手段成为使能技术：Nokia 用长距 chirped-pulse OFDR 测约 100 km HCF（3–25 m 分辨率），扫频 OFDR 在 5 km 上达 124 µm；Padova 用 SNSPD P-OTDR 得到分布式双折射矢量，二者互补，都针对 HCF 背散射比 SMF 低 30–45 dB 的难题（Fontaine、Zampato）。
- 监测与运维矛盾：正压充气可增强背散射、降低 OTDR 功率需求，但会掩盖熔接点反射，使单端 OTDR 损耗检测失效；Nokia 讲稿亦翻拍同一张中国移动 OTDR 图，说明该问题为业界共识（Dong Wang p88；Fontaine p20–21）。
- 容量/距离两端记录并存：短跨 100 km 上 S+C+L 377.6 Tb/s，单跨 726.1 km（400G），多跨 10714.3 km 仍 1.0 Tb/s/λ；关键限制从非线性转为 CD、IMI、气体吸收（Dong Wang p78–80）。
- 应用分层不同：DCN/接入更看重低时延、低功耗，连接器损耗比光纤损耗更关键（0.3 dB/对约等效 3 km）；骨干与海缆看重低损耗与放大器站点数减少（Dong Wang p70–72, p81）。
- 标准化进入实操阶段：CCSA 2 份技术报告、ITU-T SG15 GSTR.hcf（2026.7 启动）、IEEE 802.3 讨论 448G/lane 用 HCF；结构（4E/5E）是否需要统一被列为关键决策（Dong Wang p87, p89）。
