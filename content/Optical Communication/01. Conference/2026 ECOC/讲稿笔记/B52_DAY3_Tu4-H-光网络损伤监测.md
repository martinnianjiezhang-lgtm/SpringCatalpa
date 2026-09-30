---
title: "B52 · DAY3 · Tu4-H-光网络损伤监测"
tags:
  - ECOC2026
  - DAY3
---

### 0922-Tu4-H1-NokiaBellLabs-光纤传输中信道内与信道间非线性损伤的估计.pdf
- 讲者/机构：讲者姓名未见（Nokia Bell Labs） | 题目：题目页OCR乱码，英文原题看不清；主题为在运行网络中分别估计 SPM 与 XPM 占光传输噪声的比例（%SPM/%XPM） | 类型：学术论文
- 方向归属（主/次）：主 1（AI光网络/损伤监测）；次 无
- 核心主张：
  1. 用神经网络从接收星座的正交/同相噪声 PSD、累积色散、符号率、SNR 分别估计 %SPM 与 %XPM。
  2. 实验传输上 RMSE 约 1%（约等于非线性阈值处 SNR_NLI 0.1 dB）。
  3. 分离的 SPM/XPM 监测可支持新的网络控制应用（信道功率优化、邻道代价评估）；接收星座含有足以区分 SPM 与 XPM 的信息。
- 关键数据：
  - 32 GBd、900 km 实验：RMSE %SPM 1.1±0.2%，%XPM 0.6±0.1%，%SPM+%XPM 1.0±0.2%；5 次重复划分 70/15/15，测试仅用未见过的入纤功率 [p8]
  - 全数据集 1900 次实验传输（32/39/46 GBd，600/900 km）：%SPM 1.4±0.3%，%XPM 1.1±0.2%，和 1.5±0.3% [p8]
  - p7（OCR）：早期版本用 430 次实验、32 GBd/900 km，散点图参考值来自专门的功率扫描 [p7]
  - 1% RMSE 对应非线性阈值处 SNR_NLI 约 0.1 dB [p8][p9]
- 提到的公司/客户/产品/标准：无
- 与业界对比或记录声明（SOTA/首次/record）：讲者称 SPM 与 XPM 分离观测本身是难点（未给出对比数据） [p2]
- 推荐配图页：p8（结果表，含各波特率/距离的 RMSE）；p4（方案框图：PSD 特征进 NN 输出 %SPM/%XPM）

### 0922-Tu4-H2-NTT-可插拔模块相干DSP芯片上首次实现分布式PDL监测.pdf
- 讲者/机构：讲者姓名未见（NTT，含 NTT Innovative Devices；致谢 NICT 委托研究 JPJO012368G60201） | 题目：题目页无OCR，英文原题看不清；主题为在相干可插拔 DSP 芯片上实现分布式 PDL 监测（基于 polarization-resolved LPM） | 类型：学术论文
- 方向归属（主/次）：主 1（AI光网络/oDSP）；次 2（ZR/ZR+）
- 核心主张：
  1. 分布式 PDL 监测在 118-GBd OSFP 收发模块的相干 DSP 芯片内完整实现。
  2. 单个 PDL 估计误差低于 0.5 dB；多个 PDL 元件可分别定位并定量，误差 <1.0 dB。
  3. 使空间分辨 PDL 监测成为相干可插拔的原生功能。
- 关键数据：
  - 链路：200 km（4×50 km G.654.E），118-GBd QPSK、400ZR 信号，C 波段 WDM，系统最优功率，PDL 仿真器置于 50/150 km，片上 LPM 步长 1.7 km [p10]
  - 标准 ZR+ 业务，无专用探测光或光域 SOP 调整 [p10]
  - 双 PDL：50 km 与 150 km 处设定均为 3 dB，估计均为 2.3 dB，误差均为 0.7 dB（OCR，未逐项核图） [p15]
  - 实现方式：解析式辅助，不存储矩阵 G，内存降低数个数量级，模块功耗无可测增加 [p9]
  - 与以往对比：以往为单 PDL、离线 DSP；本工作多 PDL、片上 DSP、118-GBd OSFP [p6]
- 提到的公司/客户/产品/标准：NTT、OIF Coherent CMIS、400ZR/ZR+、OSFP、G.654.E；参考 Sasai & Yamazaki OFC2026、Sasai 等 OFC2026 PDP
- 与业界对比或记录声明（SOTA/首次/record）：标题称在可插拔模块相干 DSP 上首次实现分布式 PDL 监测 [p6][p16]
- 推荐配图页：p15（两个 PDL 的定位与量化结果）；p7（偏振分辨 LPM 原理）；p6（与先前工作对比表）

### 0922-Tu4-H3-NTT-片上纵向功率监测使能的相干DSP非线性干扰估计.pdf
- 讲者/机构：讲者姓名未见（NTT） | 题目：题目页OCR乱码，英文原题看不清；主题为基于片上 LPM 的相干 DSP 非线性干扰（NLI）估计 | 类型：学术论文
- 方向归属（主/次）：主 1（AI光网络/oDSP）；次 2（ZR/ZR+）
- 核心主张：
  1. 相干 DSP 新增 NLI 监测功能，作为片上 LPM 的副产物，计算开销可忽略。
  2. 用于信号质量劣化的根因分析。
  3. 依据实测而非设计固定值来削减多余裕量。
- 关键数据：
  - 原理：由 LPM 得到纵向功率分布，重建非线性波形 Â1=Gγ̂′，SNR_SCI=‖A0‖²/‖Â1‖² [p16]
  - 数值验证：单信道，QPSK/16QAM，118.2 GBd，3×50 km，α=0.2 dB/km，D=17 ps/nm/km，γ=1.3 /W/km，loaded SNR 100 dB，入纤功率 -4 至 6 dBm；LPM 估计的 SNR_SCI 与实测吻合，与调制格式无关（图上 -4 dBm 约 42 dB，6 dBm 约 22 dB，读图近似值） [p18]
  - 前置成果 OFC2026 PDP：首个 LPM 片上 DSP 实现，400ZR+ 距离 1005 km，800ZR+ 距离 450 km（OCR，未核图）；使用标准 ZR+ 信号无需专用序列，功耗开销可忽略，可与第三方发射机配合 [p19]
  - LPM 闭式辅助方案：约 99.999% 内存降低（OCR，未核图）；例：1000 km、1 km 分辨率、100 k 样点的 G 矩阵约 400 MB [p20]
  - 400ZR+（QPSK）1005 km 片上 LPM：无异常跨段功率高度可复现，可定位多处约 2 dB 损耗；与另一厂商 DSP 发射端互通（OCR） [p22]
  - DSP 监测项清单：CD、DGD、PDL、SOP、SNR、BER，OFC2026 增加纵向功率监测，本工作增加非线性干扰；芯片标识 ExaSPEED800 [p25]
- 提到的公司/客户/产品/标准：NTT、NTT Innovative Devices、ExaSPEED800 DSP、400ZR+/800ZR+、OSFP；对照 OTDR；引用 Kim OFC2024、Andrenacci JLT2025 等
- 与业界对比或记录声明（SOTA/首次/record）：p5 演进图标注“First implementation of NLI estimation, This work”与“First DSP implementation of LPM, Sasai OFC2026”（OCR） [p5]
- 推荐配图页：p25（结论与 DSP 监测功能版图）；p18（SNR 估计 vs 实测）；p19（片上 LPM 与以往工作对比表）

### 0922-Tu4-H4-华为加拿大-近符号率的线性最小二乘纵向功率监测.pdf
- 讲者/机构：Junho Chang, Choloong Hahn, Qingyi Guo, Zhiping Jiang（Huawei Technologies Canada, Ottawa） | 题目：英文原题看不清（主题为近符号率采样下的线性最小二乘 LPM，Near-symbol-rate LLS LPM） | 类型：学术论文
- 方向归属（主/次）：主 1（AI光网络/oDSP）；次 无
- 核心主张：
  1. 已报道的 1-SpS 偏差源于可校正的空间响应函数（SRF）失配。
  2. 修正：在求逆中使用互相关 SRF Re[G̃†G]，并离线预计算该算子。
  3. 近符号率 LPM 在更粗空间网格上达到相当的 MAE，方差更高需额外平均；更低采样率与更小空间网格降低实时 LPM 的内存与计算门槛。
- 关键数据：
  - 采样率影响：2 SpS 时互相关、自相关与 5-SpS 参考几乎重合；1.25 SpS 时响应展宽且互相关项更宽；1 SpS 时差异更大，常规 LLS 反卷积不足 [p8]
  - 精度对空间步长：常规 2 SpS 仅在步长 <0.7 km 时 MAE 低于 0.2 dB；所提 1/1.25 SpS 在约 1.5 km 步长仍为低 MAE；最优步长下近符号率 STD 最多约为 2 SpS 的 3 倍；条件 32k 符号/组，不含放大器噪声 [p12]
  - 方案：离线用随机符号构造 G 与 G̃并预计算 Re[G̃†G]⁻¹；实时使用 1-SpS 判决或 N_dsp-SpS 波形，做可并行的 CM 相关后乘预计算算子 [p10]
  - 复杂度先行工作：Jiang 2024 称实数运算减少约 54%；Sasai & Yamazaki 2026 128-GBd 例内存降低 99.9990%（OCR，未核图），稳定 LS 需 Δz > 1/(4π|β2|B²)（OCR公式，仅供参考） [p3]
- 提到的公司/客户/产品/标准：Huawei；对比 Jiang 2024、Escamilla 2026、Boitier 2025、Sasai & Yamazaki 2026
- 与业界对比或记录声明（SOTA/首次/record）：未声明 SOTA/首次
- 推荐配图页：p12（MAE/STD 对空间步长曲线）；p10（离线+实时方案框图）；p8（不同 SpS 下 SRF 对比）

### 0922-Tu4-H5-NokiaBellLabsFrance-用迁移学习做可泛化的光链路PDL回归.pdf
- 讲者/机构：讲者姓名未见（Nokia Bell Labs France；引用文献作者 Shi, Lina 等） | 题目：英文原题看不清（主题为迁移学习的可泛化光链路 PDL 回归） | 类型：学术论文
- 方向归属（主/次）：主 1（AI光网络）；次 无
- 核心主张：
  1. 迁移学习 PDL 回归在光学实验台上得到验证。
  2. 仿真训练的模型无需重新生成源数据集即可适配未见过的实验条件。
  3. 在有限目标数据下，跨符号率、功率、调制格式均有一致提升；降低对大量目标域数据的需求。
- 关键数据：
  - 方法：从 SNR 概率分布提取统计特征（std、skewness、kurtosis、IQR、CV、asymmetry 等）送入回归器输出 PDL，SNR PDF 含累积 PDL“指纹” [p10]
  - 目标域实验数据：32G/39G/46G QPSK，入纤功率 -5 至 -1 dBm；32G 16QAM 同样功率；留一法，每个速率和功率 M=7 次测量 [p14]
  - 32-Gbaud QPSK：迁移学习平均 RMSE 0.21–0.55 dB；仅源域基线平均 1.81–2.49 dB，迁移后 RMSE 低 4 倍以上；各入纤功率均优于基线 [p18]
- 提到的公司/客户/产品/标准：Nokia Bell Labs；先前工作 ECOC 2024、ACP 2024、IPC 2025（Shi, Lina 等）
- 与业界对比或记录声明（SOTA/首次/record）：未声明
- 推荐配图页：p18（RMSE 对目标功率，迁移 vs 基线）；p14（迁移学习框架与目标数据）

## 本批小结
1. 本批是 Tu4-H“光网络损伤监测”整场，中心主线是相干接收机 DSP 内的纵向功率监测（LPM）从离线走向片上：NTT H2/H3 在 OSFP ZR+ 模块 DSP 上实现（PDL 定位、功率剖面、NLI 估计），华为加拿大 H4 从算法侧降采样率与内存（H2、H3、H4）。
2. 监测目标正从“端到端累积指标”转向“空间分辨”：功率异常（约 2 dB 损耗定位）、多个 PDL 分别定量（误差 <1.0 dB）、SPM/XPM 拆分（H2、H3、Nokia H1）。
3. NTT 将 LPM 副产物 NLI 监测定位于“依实测削减多余裕量”，与 ZR+ 可插拔互通性和第三方发射机兼容配套，隐含运营商降裕量的商业诉求（H3）。
4. 机器学习用于损伤估计有两条路：Nokia H1 用 NN 从噪声 PSD 分解 SPM/XPM（RMSE 约 1%），Nokia France H5 用迁移学习减少目标域数据需求（RMSE 0.21–0.55 dB，较基线降 4 倍以上）；均强调泛化，其中 H1/H5 仅为实验室测试床数据（H1、H5）。
5. 算法复杂度是片上化的瓶颈：闭式/解析辅助将内存降数个数量级（NTT H2/H3），近符号率方法则以粗网格换方差（华为 H4：STD 最多约 3 倍）。
6. 注意：多页 OCR 为空，H2/H3 中部分数值（如 1005 km、99.999%）来自 OCR 而非核图，引用前需复核。
