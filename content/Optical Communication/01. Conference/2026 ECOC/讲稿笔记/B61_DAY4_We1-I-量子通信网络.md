---
title: "B61 · DAY4 · We1-I-量子通信网络"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We1-I1-1149-硅光芯片间长距纠缠分发.pdf
- 讲者/机构：DTU（丹麦技术大学；讲者姓名未见） | 题目：硅光芯片间长距离纠缠分发（英文原题看不清；内容为 path-encoded entanglement distribution between silicon photonic chips over multicore fiber） | 类型：邀请报告（We1-I）
- 方向归属（主/次）：主 6 QKD/量子；次 4（硅光集成、多芯光纤 MCF，非 CPO）
- 核心主张：
  - 首次在不做编码转换的情况下，直接长距（80 km）分发路径编码（path-encoded）纠缠态 [p1, p8]。
  - 实现依靠多芯光纤链路 + 主动相位稳定 [p8]。
  - 展望：降低光纤-芯片耦合损耗以提高速率/距离；扩展到高维态 [p8]。
- 关键数据：
  - 硅光螺旋波导 SFWM 产生光子对；泵浦 625 MHz [p2]；页面另有“3% pair generation rate”，条件看不清 [p2]。
  - MCF 芯间串扰 -62 dB（80 km）；芯间噪声高度相关，差分相位漂移在 Hz 量级 [p4]。
  - 相位稳定：泵浦光少量共传作相位参考，光电二极管+PLL 驱动光纤移相器 [p5]。
  - 态层析保真度：同芯片基线 94±0.1%；4 m 约 0.92（读图，无标注）；80 km 85.7±0.2% [p6]。
  - 保真度受多对事件限制：Fmax(P=0.03)=95.6% [p6]。
  - BBM92 QBER（4 m / 80 km）：QBER_Z 2.58%/6.81%；QBER_X 5.60%/7.26%；QBER_Y 7.27%/8.63% [p7]。
  - 无限密钥条件安全码率：802.57 bit/s @4 m；2.03 bit/s @80 km [p7]。
  - 总损耗 44.4 dB：发射端布线/螺旋 9.5、发射端出耦 6.6、信道 15.3、接收端耦合+布线 12.6、SNSPD 0.4（表中 dB）；光栅耦合器约 7 dB/个×4 是主要限制 [p7]。
- 提到的公司/客户/产品/标准：SNSPD、AMZI、MZI 网格、BBM92 协议、多芯光纤（厂商未提）。
- 与业界对比或记录声明：“First demonstration of direct, long-distance distribution of path-encoded entangled states” [p8]；“First direct distribution ... over long distance (80 km) without encoding conversion” [p1]。
- 推荐配图页：p7（QBER 表、码率-距离曲线与 44.4 dB 损耗分解）；p6（保真度直方图）。

### 0923-We1-I2-1353-城域光纤弱相干偏振态量子隐形传态.pdf
- 讲者/机构：T-Labs（Deutsche Telekom；讲者姓名未见） | 题目：现网城域光纤上弱相干偏振态量子隐形传态（英文原题看不清；首页 OCR 乱码，内容为 quantum teleportation over live carrier-grade fiber in Berlin） | 类型：邀请报告
- 方向归属（主/次）：主 6 QKD/量子；次 2（30 km 城域现网、与 100G 经典业务共纤，非跨楼园区）
- 核心主张：
  - 在真实运营商在网光纤（柏林两个 Telekom 站点间 30 km 环路，非光纤盘）上实现量子隐形传态 [p13, p25]。
  - 与实时经典业务共纤（无需暗光纤）、使用商用现成器件、数据中心式机架 [p25]。
  - 目前主要限制是隐形传态速率而非保真度 [p24]。
- 关键数据：
  - 拓扑：30 km 环（单程 15 km），SMF [p13]；量子光 O 波段 1324 nm，经典光 C 波段 1561.01 nm，WDM 共传 [p14]。
  - 经典共传：100 Gbps 收发器，入纤功率 +0.27 dBm [p14]。
  - 光源：795 nm 衰减激光作弱相干态（WCS）；Qunnect 偏振纠缠源，795 nm + 1324 nm 双色光子对（热 Rb 蒸气 SFWM）[p10, p11]；Qu-APC 自动偏振补偿器 [p15]。
  - HOM 干涉可见度：本地 79±3%，30 km 79±5%（3 min / 20 min 积分，bin 32 ps）；不到 100% 主因是 WCS 非理想单光子源 [p18, p19]。
  - 隐形传态保真度（平均）：本地 93.3±1.6%，30 km 无共传 91.4±3.1%，30 km 加 100 Gbps 经典共传 91.3±2.6%；分态 |H> 97.0/95.6/98.2%，|D> 90.0/85.7/87.3%，|R> 93.1/92.8/88.5%（顺序为 本地/30km/30km共传，±见图）[p20]。
  - 经典界 F=2/3，全部超过 [p20]。
  - 速率：本地 1 Hz，30 km 0.1 Hz [p20, p24]，受独立光子重合概率限制 [p24]。
  - 路线：近期更高速率源/单光子输入；远期带多模存储的量子存储器；备选空芯光纤（需新铺设）[p24]。
- 提到的公司/客户/产品/标准：Deutsche Telekom T-Labs、Qunnect（Qu-SRC、Qu-APC）、Cisco（NYC 纠缠交换相关工作）、SNSPD、TDC、Song et al. arXiv 2026（空芯光纤共传）。
- 与业界对比或记录声明：“Highest fidelity of any deployed link”；匹配最长城域距离 30 km；偏振编码中保真度与距离最高，仅被实验室光纤盘、time-bin 实验超过；“Among the first to explore co-propagation with classical traffic” [p21（图，对应幻灯片 21）]。
- 推荐配图页：p20（分态保真度柱状图，含共传对比）；p22（保真度-距离 SOTA 对比散点图）。

### 0923-We1-I3-797-四用户纠缠分发网络现网试验.pdf
- 讲者/机构：Sarah Sommermeier（邮箱 sarah.sommermeier@hhi.fraunhofer.de），Fraunhofer HHI（与 Deutsche Telekom、QR.N 项目） | 题目：四用户纠缠分发网络现网试验（英文原题看不清；页脚为 ECOC 2026 We1-I3，内容为 metropolitan four-user entanglement-based QKD network field trial） | 类型：邀请报告
- 方向归属（主/次）：主 6 QKD/量子；次 无
- 核心主张：
  - 在部署的城域无中继纠缠分发网络（EDN）上获得正码率，24 h 稳定，多用户对同时支持 [p14]。
  - 码率足够低带宽实际应用；使用商用纠缠源、无物理色散补偿 [p14]。
  - 演示了稳定的基于 White Rabbit (WR) 的时钟对齐方案 [p14]。
- 关键数据：
  - 协议：time-bin-phase 版 BBM92；基于可见度的反馈环稳定相位；S 参数约 2.8，高于经典界 2、接近 2√2（QM 界）[p6]。
  - 各环路损耗（等效 SMF 长度按 0.3 dB/km）：Alice 9.0 dB/30.0 km；Bob 11.45 dB/38.2 km；Diana 8.72 dB/29.1 km；Freddy 8.22 dB/27.4 km；WR 环 10.40 dB/34.7 km [p6]。
  - 多用户方式：中心节点（TPS 光子对源）+ DWDM 复用，信号/idler 光谱分给不同用户 [p9]；柏林 HHI 楼层 15/10 层与 Telekom 站点间地图链路，6.9 km 段 [p6, p12]。
  - 独立 TDC 时钟由 WR（10 MHz+1PPS 经 SMF）对齐，重合峰 [p11]。
  - 24 h 连续运行：Alice-Bob 平均 QBER 1.95%、SKR 40 bit/s；Diana-Freddy 平均 QBER 2.41%、SKR 54 bit/s；QBER 低于 11% 安全阈值 [p12]。
  - 新 256-bit 密钥间隔：约 6.4 s（Alice-Bob）、约 4.7 s（Diana-Freddy）（OCR 读数，图中较小，待核）[p13]。
  - 展望：扩展时钟对齐、BBM92 改进、作为纠缠源/量子存储器/SDN 的测试床 [p14]。
- 提到的公司/客户/产品/标准：Fraunhofer HHI、Deutsche Telekom、QR.N（Quantenrepeater.Net，联邦研究部资助）、White Rabbit、商用光子对源（TPS）、SNSPD、Time Tagger、DWDM。
- 与业界对比或记录声明：未见 record/首次声明。
- 推荐配图页：p12（24 h QBER/SKR 时间序列，含四用户拓扑）；p11（WR 时钟同步架构）。

### 0923-We1-I4-1315-超纠缠单拷贝纠缠蒸馏.pdf
- 讲者/机构：Domenico Ribezzo，佛罗伦萨大学物理与天文系（合作者 Guarda, Zavatta, Bacco；CNR-INO；ERC QOMUNE） | 题目：Hyperentanglement Distillation & QPA（单拷贝超纠缠蒸馏与量子隐私放大，页脚所见） | 类型：邀请报告（幻灯片页脚 SIF 2026）
- 方向归属（主/次）：主 6 QKD/量子；次 无
- 核心主张：
  - 通过能量-时间 ⊗ 频率超纠缠做单拷贝蒸馏，等价于物理层量子隐私放大（测量前净化态）[p14]。
  - 在 20 km SMF、标准 DWDM 下获得 4 dB 拉曼噪声容忍度提升；无主动稳定，除 2 个 DWDM 外无额外装置 [p14]。
  - 1/N 可扩展到更高维；DWDM 解复用器可作物理层 QPA 器件；面向已部署电信光纤的抗拉曼 QKD [p14]。
- 关键数据：
  - 背景：量子与经典共纤面临约 10 个数量级功率差，主噪声为自发拉曼散射（SpRS）[p2]。
  - 先前方案 I：L'Aquila 城域 MCF，约 26 km，量子 CH21 + 3 芯经典（19.5 dBm），总经典吞吐 110.8 Tb/s [p3]。
  - 先前方案 II：4D 高维 QKD，52 km，22 dB 损耗，两芯 MCF；2D 23.6 kbps，4D 51.5 kbps（约 2× BB84）；缺点为硬件复杂、需 MCF [p4]。
  - 实验：CW + SHG(780 nm) + SPDC(1560 nm, CH21) PPLN 波导；无源硼硅酸盐 PIC，Franson iMZI（Δτ=800 ps）；100 GHz DWDM 分出 N=2 对（CH20/CH22）；20 km SMF-28，共传经典 CH17 [p7]。
  - 偶然符合被抑制 1/N（此处 1/2）[p9]。
  - 基线可见度约 98%；QKD 阈值可见度 78%；蒸馏后的 qudit 在经典入纤功率至 -9.3 dBm 仍高于 78%，宽带（2D）在 -13.3 dBm 即失效 [p12]。
  - 安全码率（bit/s，对数图）：在 -14.3 dBm 约 200–300 bit/s，-9.3 dBm 约 40–50 bit/s；100 GHz 模型曲线在约 -8 dBm 归零，200 GHz 曲线约 -12.7 dBm 归零；标注“improvement 4-dB extra noise resistance” [p13]。
  - 论文“To be published soon” [p15]。
- 提到的公司/客户/产品/标准：BBM92、PPLN、DWDM 100 GHz、SNSPD、Raman 谱（Eraerds et al. 2010）、Wu et al. Light Sci Appl 2025、Zahidy et al. Nat Commun 2024。
- 与业界对比或记录声明：与宽带 2D 纠缠对比获得 4 dB 额外噪声耐受 [p13]；无 record 声明。
- 推荐配图页：p12（可见度 vs 经典发射功率，蒸馏 vs 2D）；p13（SKR vs 拉曼噪声）。

### 0923-We1-I5-1432-固态量子节点的量子互联网.pdf
- 讲者/机构：Arq Quantum Technologies（2025 年成立，巴塞罗那；CEO Samuele Grandi，CTO Emanuele Distante；讲者姓名未见） | 题目：固态量子节点的量子互联网（英文原题：Enabling the Quantum Internet，首/尾页） | 类型：产业发布（初创公司介绍+技术）
- 方向归属（主/次）：主 6 QKD/量子；次 无
- 核心主张：
  - 以稀土掺杂晶体（Pr3+:Y2SiO5）多模量子存储器构建量子中继器/量子节点 [p7, p13]。
  - 多模（时间/空间/频谱复用）使纠缠尝试速率随模数 N 线性提高，摆脱通信时间 t_comm=distance/c 限制 [p14, p18]。
  - 路线图 2026 MVP → 2032 长距中继器 → 2038 网络级硬件；首个原型 2028 年中在巴塞罗那部署 [p27, p28]。
- 关键数据：
  - 50 km 时纠缠尝试速率 4 kHz；成功率更低 [p14]。
  - 仿真 250 km：800 模式 herald 速率上限约 40 Hz（读图，上限线略高于 40）、符合率约 0.15–0.18 Hz；80 模式 herald 上限约 4 Hz、符合率约 3×10^-3 Hz（读图数量级，条件看图）[p18]。
  - 空间复用：声光偏转器，10 个空间模式，各自独立相位/幅度，受晶体尺寸限制；晶体 3 K [p20]。
  - 实验（Mneimneh et al., arXiv 2609.15689，已投稿）：时空模数 N 到 60，占用通信时间比 F 到 15%，相关 idler 速率约 830 min^-1，符合率约 0.58 min^-1（读图，10 个 cell）[p23]。
  - 存储：动态解耦，cSPDC 源信号 606 nm、idler 1436 nm、泵浦 426 nm，晶体 3 K，存储时间达约 3 ms，T2=500 µs 参考，效率约 1–2%（毫秒段）[p32]。
  - 阻抗匹配腔：R~40%，Pr3+:Y2SiO5，回波（Echo）可见 [p32]。
  - 团队 11 人（末页）/10 人（首页）[p2, p25]。
  - 需求清单：片上激光器（线宽>1 kHz、功率>20 mW、可见光）、606 nm 快速低损光开关、可负担的空芯光纤、超低损 SiN 集成电路、有源/无源幅度调制集成系统 [p30]。
- 提到的公司/客户/产品/标准：Arq、Imperial、Accenture（团队页标识）、Quantum Internet Alliance（连接离子阱跨 500 km）、EC 量子互联网测试床、目标 2038 泛欧量子互联网 [p26]。
- 与业界对比或记录声明：无 record；引用 Lago-Rivera Nature 2021、Rakonjac PRL 2021 等。
- 推荐配图页：p18（250 km 下 80 与 800 模 herald/符合率仿真）；p32（动态解耦存储+阻抗匹配腔）。

## 本批小结
- 量子网络正从“实验室光纤盘”走向“现网+共纤”：T-Labs 30 km 柏林在网环路上隐形传态保真度 91.3±2.6%（含 100G 经典共传），HHI 四用户 EDN 24 h 稳定（SKR 40 / 54 bit/s，QBER 1.95% / 2.41%）；均使用商用光子源与 SNSPD（We1-I2、We1-I3）。
- 经典-量子共存的核心矛盾是拉曼噪声：Florence 用 ET⊗频率超纠缠（1/N 抑制）获 4 dB 额外耐受，-9.3 dBm 经典功率下可见度仍>78%（We1-I4）；T-Labs 则以 O 波段(1324 nm) 量子 + C 波段 (1561 nm) 经典 WDM 分离（We1-I2）。
- 多芯光纤(MCF)是量子链路的“稳相/低串扰”工具：DTU 在 80 km MCF 上实现 -62 dB 芯间串扰与 Hz 级差分相位漂移，用 PLL 稳定（We1-I1）；I4 指出 MCF 尚未广泛部署，因此转向标准 SMF 的方案。
- 各路线共同瓶颈是损耗与速率而非保真度：DTU 的 44.4 dB 总损耗（光栅耦合器约 7 dB×4）使 80 km 仅 2.03 bit/s（We1-I1）；T-Labs 传态仅 0.1 Hz@30 km（We1-I2）；Arq 提出多模量子存储把尝试速率线性提高（We1-I5）。
- 量子器件对光电子上游提出明确需求：片上可见光激光器(>20 mW)、606 nm 低损光开关、空芯光纤、低损 SiN（We1-I5）；空芯光纤也被 T-Labs 列为备选（We1-I2）。
- 同步与稳定是网络化关键：HHI 用 White Rabbit 对齐独立 TDC 时钟（We1-I3），DTU 用泵浦参考光做相位环（We1-I1），Florence 则强调无需主动稳定的无源 PIC 方案（We1-I4）。
