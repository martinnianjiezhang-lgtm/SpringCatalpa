---
title: "B46 · DAY3 · Tu1-E-光开关与解复用器"
tags:
  - ECOC2026
  - DAY3
---

### 0922-Tu1-E1-清华大学-Si3N4与TFLN集成激光器实现200Gbps相干光交换.pdf
- 讲者/机构：清华大学（讲者姓名幻灯片未见） | 题目：Fast coherent optical switching based on a wavelength-switchable Si3N4-TFLN laser（本批看图页均无题目页，据结论页概括） | 类型：学术论文
- 方向归属（主/次）：主 [3 Scale-out：光源/调制器/OCS]；次 [1 相干/高波特率器件]
- 核心主张：
  1. 提出基于 Si3N4-TFLN 混合集成波长可切换激光器的快速相干光交换架构（每机架 Laser+Mod. 经 AWGR 按波长路由到目的机架接收机）。
  2. 激光器本征线宽 106.06 Hz，2.4 nm 波长切换，切换时间 15 ns。
  3. 演示 200 Gbps 相干光交换，切换延迟 80 ns，面向低时延、高吞吐 OCS 网络。
- 关键数据：
  - 调谐范围 40 nm（约1513–1552 nm 梳状谱线），SMSR 63.9 dB（幻灯片右侧文字误写为"63.9 nm"，图上为 dB），输出功率 6.1 mW @200 mA，本征线宽 106.06 Hz（ν0=33.76×π，各波长本征线宽约 100–280 Hz） [p4]
  - 波长切换范围 2.4 nm，切换时间 <15 ns（实测过渡 13.6 ns / 11.1 ns），切换能耗 10 pJ [p5]
  - 系统实验：DP-QPSK，25 GBaud，线速率 200 Gbps，3 km 光纤，波长 1534.2 nm / 1536.6 nm 均 BER: 0，切换延迟 80 ns（SNR 滑窗恢复曲线） [p6][p7]
  - 耦合损耗：Si3N4–SOA 对接 1.8 dB / SOA–TFLN 对接 2.7 dB；气密蝶形封装（看图核实） [p3]
- 提到的公司/客户/产品/标准：AWGR、LNOI IQ 调制器、DP 90° hybrid、EDFA；无公司名
- 与业界对比或记录声明（SOTA/首次/record）：未见明确 record 声明；结论称所提出快速相干光交换架构：激光器本征线宽 106.06 Hz、2.4 nm 波长切换时间 15 ns，演示 200 Gbps 相干光交换、交换时延 80 ns（看图核实） [p7]
- 推荐配图页：p1（相干交换架构：Laser+Mod.→AWGR→Receiver 及 SiN-TFLN 激光器/LNOI IQ 调制器结构）；p6（DP-QPSK 200G 切换实验与 80 ns 延迟曲线）

### 0922-Tu1-E2-浙江大学-2.5D环面拓扑的低损硅光MEMS开关阵列.pdf
- 讲者/机构：Jiayue Zhu 等（Daoxin Dai 团队）/ 浙江大学极端光学技术与仪器全国重点实验室、华为中央研究院（p1 看图核实） | 题目：Low-loss Silicon Photonic MEMS Switch Array Based on 2.5D Torus Topology | 类型：学术论文
- 方向归属（主/次）：主 [4 Scale-up/OCS]；次 [3 Scale-out OCS]
- 核心主张：
  1. 硅光 MEMS 开关 OFF 态损耗低、ON 态损耗高，需要适配的拓扑；提出 2.5D Torus（拆分 crossbar tile + 输入/输出旁路层）来降低最大路径插损。
  2. 在宽义/严格无阻塞拓扑中插损最低之一，且开关总数较低、一阶串扰仅出现在同一 crossbar tile 内。
  3. MEMS + 2.5D Torus 是低损、可扩展硅光开关阵列的有前景方案（结论页）。
- 关键数据：
  - 各类硅光开关单元对比表：MEMS 开关时间 μs/sub-μs，功耗 ~0 (pJ)，尺寸 10–100 μm，规模已达 240×240 Crossbar；热光 128×128 Benes，切换 1–100 μs，1–100 mW；电光 ns/sub-ns，128×128 Benes；相变 16×16 [p3]
  - 插损随端口数曲线：128 端口时 2.5D Torus 约 15 dB，Crossbar 约 33 dB（读图估计） [p16]
  - 开关总数公式：Crossbar/PILOSS N²；Dilated Banyan/Switch&select 2N²−2N；2.5D Torus 公式字小看图仍不可读（形如 (4+m)/m·N²−2N）；插损随端口数增长最慢之一（128 端口约 15 dB）；一阶串扰仅出现在同一 Crossbar tile 内，串扰排序 Crossbar/PILOSS > 2.5D Torus > Dilated Banyan/Switch&select（看图核实） [p16]
  - 16×16 原型：面积 3.7 mm × 8.2 mm，开关单元总数 352 [p18]
  - 估计器件 IL 1.9–4.2 dB，估计波导 IL 1.3–3.3 dB，实测消光比 >27.8 dB，实测片上 IL（部分路径）3.3–9.3 dB [p19]
- 提到的公司/客户/产品/标准：引用 Optica 2016 MEMS 绝热耦合开关；无公司名
- 与业界对比或记录声明（SOTA/首次/record）：称"one of the lowest insertion losses among widely used wide-sense or strictly non-blocking topologies" [p16]
- 推荐配图页：p19（16×16 阵列 IL 热图、消光比与实测 IL）；p16（各拓扑插损-端口数对比）

### 0922-Tu1-E3-Microsoft-宽而慢架构加microLED打破AI网络与内存墙.pdf
- 讲者/机构：Microsoft（讲者姓名幻灯片未显示，讲者照片可见） | 题目：Wide-and-slow architecture with microLED to break AI network and memory walls（据文件名与内容概括，原题页未拍到；p1 看图核实为 "The talk in one slide"：互连是扩展瓶颈，光学可根本改变 AI 系统构建，需超越功耗、全栈协同优化、打破采用僵局） | 类型：邀请报告
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE]；次 [3 Scale-out 光源]
- 核心主张：
  1. 互连是计算、内存、网络的共同扩展瓶颈，带来硬件复杂度（大封装、昂贵 HBM、超密机架）与软件复杂度（局部性调度、资源碎片、多种并行）。
  2. 光互连可根本改变 AI 系统构建方式，需做到：超越功耗（可靠性、时延、带宽密度）、全栈协同优化（电子、PD、封装、光纤与连接器）、打破采用僵局（部署需要现场数据，现场数据需要部署）。
  3. "宽而慢"（大量低速并行通道 + microLED/PD 阵列）在能效之外还带来更易的通道冗余、面发射高带宽密度、更少处理级数（低时延），但需在生产环境规模验证。
- 关键数据：
  - 目标参数表：功耗 <1 pJ/bit (W/Tbps)；带宽密度 >10 Tbps/mm；距离 ~10 m；可靠性 <<1 FIT；时延 <10 ns [p15]
  - 权衡图：纵轴 BW 密度×能效 (Gbps/mm)/(pJ/bit)，铜走线 D2D/GPU-to-HBM 约 10^5、NVLink 铜缆约 10^2、可插拔光缆约 10（读图，定性），横轴最大距离 0.001–100 m [p2][p15]
  - 光 I/O 能耗（pJ/bit）柱状对比：可插拔 > CPO > 宽而慢 > 3D 堆叠（<1 pJ/bit？，带问号）；图无数值刻度，仅定性 [p17][p19]
  - 域-压力-应对表：Compute/Memory 并行铜；Scale-up 串行铜；Scale-out 串行光 [p10]
  - 封装趋势：由"一个大封装含 chiplet 和 HBM"转向"每个 die 一个小封装、各自光端口 + 光 fabric"，引用 B. Canacki 等 Lite-GPUs 论文 [p12]
- 提到的公司/客户/产品/标准：NVLink、InfiniBand/Ethernet、HBM3/4/5、CPO、microLED/PD 阵列、线性驱动；VR Ultra rack（~120 kW → >0.5 MW?，OCR）
- 与业界对比或记录声明（SOTA/首次/record）：无 record；p19 风险仪表指针指向"很高"，讲者自称需要验证 [p20]
- 推荐配图页：p19（能耗柱状：可插拔→CPO→宽而慢→3D 堆叠）；p15（目标参数与功耗-密度-距离权衡）；p20（宽而慢的可靠性/带宽密度/时延三点）

### 0922-Tu1-E4-OneTouch-薄膜钽酸锂8x8光电路交换.pdf
- 讲者/机构：Dennis Maes 等，OneTouch Technology（比利时根特）、InnovSemi（中国苏州） | 题目：An 8x8 Optical Circuit Switch in Thin-Film Lithium Tantalate | 类型：学术论文（含产品宣传）
- 方向归属（主/次）：主 [3 Scale-out 调制器/OCS]；次 [4 Scale-up OCS]
- 核心主张：
  1. 纳秒级光开关存在但存在漂移；薄膜钽酸锂（TFLT）具备铌酸锂同等 Pockels 效应而漂移极小。
  2. 首个 TFLT 电光 8×8 OCS：<4 ns 切换、整个 8×8 静态功耗低、1 小时无反馈稳定。
  3. 结论称切换速度不再是瓶颈；静态功耗不再随端口数增长；无需逐开关有源控制。
- 关键数据：
  - r33 = 30.5 pm/V（LiTaO3）vs 30.9 pm/V（LiNbO3）；双折射 Δn 0.004 vs −0.07（>10x 更低）；光折变约 5x 更弱；单个 2×2 开关 2 h @ −8 dBm 超低直流漂移 [p4]
  - 芯片 7×4 mm²，8×8 Banyan（3 级×4 开关=12 个 2×2 MZM，16 个边缘耦合器，10 个交叉），阻塞拓扑；每个 MZM 推挽、长 3 mm、Vπ=10 V（VπL=3 V·cm）、插损 <1 dB [p7][p9 OCR]
  - 400 nm LTOI 晶圆，电子束光刻、优化 RIE 刻蚀，PECVD 低损 SiO2 包层，剥离金电极；苏州易缆微（InnovSemi）TFLN/TFLT 试产线（看图核实） [p6]
  - 切换瞬态 <4 ns（单 MZM，50 MHz 方波，50 GS/s 示波器；实际响应 <<1 ns，余为未端接电容负载反射），"比现有 OCS 低三个数量级" [p10]
  - 静态功耗：每开关漏电 1.1–1.4 nA @10 V；12 个开关合计 <200 nW；图中 128×128 外推 TFLT 7.5 μW，对比热光 9.0 W、热光(undercut) 670 mW（200 μs–1.3 ms） [p11]
  - 平均光纤到光纤插损 8.6 dB（其中 6–8 dB 为边缘耦合，约 1 dB/MZM 级，波导交叉每个 <0.2 dB）；一阶串扰平均 −24.3 dB；N=13 [p14]
  - 1 小时无反馈漂移：输入 10 dBm 时 −0.33 dB，输入 18 dBm（60 mW）时 −0.15 dB；泄漏优于 15 dB [p16]
  - C 波段（约 1525–1575 nm）传输平坦，目标通路约 −9 dB、纹波 <1 dB；泄漏到其他输出约 −20 至 −55 dB（开关按峰值透过偏置而非最优串扰）（看图核实） [p13]
- 提到的公司/客户/产品/标准：Google Jupiter（2022 起 OCS 上线数据中心，SIGCOMM）；OCS 市场 2029 年预计 >\$25亿（Cignal AI，页面写 \$2.5B）；OneTouch HISP 平台（异质集成 TFLN/LT on SiPh，D2W 键合，约 1 dB/面耦合，展位 1240）；InnovSemi
- 与业界对比或记录声明（SOTA/首次/record）："first 8x8 electro-optic OCS on TFLT"；"三个数量级快于现有 OCS"；"和 MEMS 一样冷，快一千倍" [p5][p10][p12]
- 推荐配图页：p3（六种平台在静态功耗/插损/速度/稳定性上的比较矩阵）；p10（<4 ns 切换示波器波形）；p11（静态功耗随端口数对比）

### 0922-Tu1-E5-NVIDIA-时钟前传DWDM光链路的微环静态与动态分配.pdf
- 讲者/机构：Angad S. Rekhi 等，NVIDIA（Santa Clara / Durham / Ridgefield） | 题目：Static and Dynamic Ring Assignment in a Clock-Forwarded DWDM Optical Link | 类型：学术论文
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO]（optics-on-interposer）；次 [3 Scale-out 电芯片/光源]
- 核心主张：
  1. Optics-on-interposer 缓解 AI 计算网络中主机 ASIC 电接口带宽瓶颈；时钟前传微环 DWDM 提供带宽密度与能效。
  2. 静态环分配（SRA）在启动时选出加热功率最低的有效循环映射（谱序=空间序，允许旋转）。
  3. 动态环分配（DRA）在芯片温度变化时实时旋转环-激光映射以省加热功率，同时保持链路运行（前传时钟切换期间无误码）。
- 关键数据：
  - 测试芯片：8 路数据（各 32 Gb/s）+ 1 路前传时钟（16 GHz），通道间隔 200 GHz，环半径 5 μm（FSR ~13.6 nm），3D 堆叠 7 nm EIC + 65 nm SiPh PIC；实测 0.8 Tb/s/mm、1.33 Tb/s/mm²、2.78 pJ/b；前传时钟相位裕量 0.47 UI @BER 1e-12 [p4]
  - 波长范围约 1290–1310 nm（O 波段），9 个激光 λ0–λ8，环 TX0–TX8 [p5]
  - SRA 最低功耗配置搜索：ΣDAC 码从配置 0 约 60k 降至配置 4 约 13k（读图估计） [p8]
  - DRA：温度 105 C→25 C 变化，热调谐能耗（pJ/b）无 DRA 时持续上升，有 DRA 通过多次旋转保持低位（示意图，无数值） [p10]
  - 蓝移（blueward-by-1）旋转：先调整 λ1 数据相位使眼图居中再重启码型检查，旋转时总光纤吞吐短暂下降，运行中通道无误码；时钟交换（RX5 接管时钟、解锁 RX7、RX6 冷却至 λ7）实时完成，总误码计数为 0（看图核实） [p12][p14]
- 提到的公司/客户/产品/标准：NVIDIA GTC 2025 Keynote；引用 B. G. Lee JLT 2023、S. Song ISSCC 2026（32 Gb/s/λ，256 Gb/s/fiber，半速率带通滤波时钟前传 DWDM）、N. Mehta OFC 2026（256 Gb/s DWDM 光 I/O）
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明
- 推荐配图页：p4（测试芯片架构与实测指标）；p5（SRA：环谐振谱、环-激光映射与循环顺序）；p10（DRA 保持热调谐能耗低的原理图）

## 本批小结
- 光交换出现"快速"与"低功耗"两条路线并行：OneTouch TFLT 8×8 做到 <4 ns、8×8 静态功耗 <200 nW（外推 128×128 为 7.5 μW），清华 SiN-TFLN 波长可切换激光器 + AWGR 以波长选路实现 15 ns 激光切换、80 ns 相干链路切换；浙大走 MEMS 低功耗路线，切换 μs 级、规模上 240×240（来自 E2、E4、E1）。
- 薄膜铌/钽酸锂（TFLN/TFLT）成为 OCS 与光源的共同材料平台：清华用 TFLN 做激光器和 IQ 调制器，OneTouch 用 TFLT 解决 TFLN 的直流漂移（漂移 1 小时 −0.33 dB）（E1、E4）。
- 硅光 MEMS 开关的核心矛盾是 ON 态高损耗，拓扑设计成为降损手段：2.5D Torus 16×16 实测片上 IL 3.3–9.3 dB，消光比 >27.8 dB；OneTouch 8×8 光纤到光纤 8.6 dB，两者皆受边缘耦合与多级级联制约（E2、E4）。
- 面向 AI 的光 I/O 都在追求"宽而慢/微环 DWDM"降低 pJ/bit：Microsoft 提出 <1 pJ/bit、>10 Tbps/mm、<10 ns 的目标并主张 microLED 宽并行；NVIDIA 的微环 DWDM 芯片实测 2.78 pJ/b、0.8 Tb/s/mm，两者对比显示现有硅光微环方案距 <1 pJ/bit 目标仍有差距（E3、E5）。
- 微环方案的工程难点在热调谐与波长对准：NVIDIA 用 SRA/DRA 降低加热功率，Microsoft 则强调宽并行的通道冗余以提升可靠性、并指出采用僵局（需在现场规模验证）（E3、E5）。
