---
title: "B43 · DAY3 · Tu1-B-空芯光纤在光网络中的应用"
tags:
  - ECOC2026
  - DAY3
---

### 0922-Tu1-B2-TUe-随机耦合多芯光纤网络的MIMO信道记忆需求.pdf
- 讲者/机构：Besma Kalla（NICT / TU/e，合作：米兰理工、UNICAMP、悉尼大学、Finisar Australia） | 题目：MIMO Channel Memory Requirements for Randomly-Coupled Multicore Fiber Networks（Tu1-B2） | 类型：学术论文
- 方向归属（主/次）：主 1（相干/海缆/长途，SDM 网络）；次 无
- 核心主张：
  1. 交换节点内各空间通道（SC）路径时延失配主导 MIMO 所需记忆长度：点到点（PTP）传输为亚 ns，网络运行下最高 3.3 ns。
  2. 所需 MIMO 记忆由最长路径时延决定；若把记忆限制在 PTP 长度，吞吐损失 50–75%。
  3. 节点内路径对齐须控制在传输 IIR 时长以内，才能在空间超级信道（SSC）交换网络中保留 RC-MCF 的优势。
- 关键数据：
  - 19 芯 RC-MCF，125 µm 包层；测试台两段光纤 63 km（<0.22 dB/km，3D 激光刻写 SDM (DE)MUX）与 86 km（<0.19 dB/km，自由空间 SDM (DE)MUX）[p8]
  - 信号：3 通道滑动测试带，24.5 GBaud PM-16QAM；C+L 波段 386 个 SSC，25 GHz 间隔 [p6]
  - 接收：实时示波器 76 通道、80 GSa/s，离线 DSP，数据辅助 LMS 估计 MIMO 抽头 [p7]
  - 网络节点：19×(1x3) WSS 构成 SDM WXC，C+L 双侧；每组 19 路 EDFA/WSS 间相对时延用 SMF 跳线对齐在 1.5 ns 内 [p9, p10]
  - PTP 传输：IIR 呈高斯形，取 98% 能量区间 +10% 余量，IIR 时长约 400 ps [p11]
  - 所需记忆：场景1&2 平均 C 波段 2.1 ns / L 波段 2.8 ns；场景3 为 2.2 ns / 3.2 ns；场景4 为 1.5–3.3 ns，部分上路 SSC 所需最短 [p13]
  - 场景1 上采用 PTP 记忆长度：吞吐损失 C 波段 SSC 53%、L 波段 SSC 75%；追平 PTP 性能需 2.4 ns（C）与 3.3 ns（L）；PTP 在 <1 ns 已达最大 GMI [p14]
  - 全场景避免损失所需记忆约 3.3 ns [p15]
  - 补充：PTP 下 86 km 光纤记忆长度要传输约 3000 km 才达到 3.3 ns [p18]
- 提到的公司/客户/产品/标准：Finisar Australia；引用 1.7 Pb/s over 63 km（Rademacher, OFC 2023 Th4A4）、1.029 Pb/s over 18081 km（Luis, OFC 2025 Th4A.1）、3.74 Exabit/s·km 跨大西洋 C+L 8610 km（Kalla, JLT 2026）[p2, p18]
- 与业界对比或记录声明（SOTA/首次/record）：无本工作 record 声明；引用的 Pb/s 级结果为他人/往期工作 [p2]
- 推荐配图页：p12（PTP 与四种网络场景的 IIR 对比）；p14（GMI 与吞吐损失随记忆长度曲线）；p13（各波长所需记忆）

### 0922-Tu1-B3-南安普顿大学-空芯光纤带来的光网络新机会.pdf
- 讲者/机构：Periklis Petropoulos 等，南安普顿大学 Optoelectronics Research Centre（合作 Riga TU、Keysight、Microsoft Azure Fibre、Univ. West Attica、DTU Electro）（p1 看图核实） | 题目：New Opportunities in Optical Networks Enabled by Hollow-Core Fibres（Tu1-B3） | 类型：邀请报告
- 方向归属（主/次）：主 3（Scale-out 光源/调制器，含 IM/DD 高速）；次 1（长途/DCI 传输）
- 核心主张：
  1. 空芯光纤可简化光传输：高容量 IM/DD、借 2D 映射（PAM12）提升 PAM 阶数、用光学处理减轻 DSP 负担。
  2. 可在新波长传输：1 µm 是新兴宽带传输波段。
  3. 光纤基础设施可承载多业务：数据加供电（Data-and-Power-over-fibre）。
- 关键数据：
  - HCF 相对 SMF 延迟降低 30%；5 km 距离约节省 ~8 µs [p5]
  - 反谐振 HCF 损耗演进：50 dB/km（Kolyadin 2013）→ 1.3 dB/km（ECOC2018 PDP）→ 0.22 dB/km（OFC2021 PDP）→ 0.09 dB/km（Nature Photon. 2025）；讲者称 YOFC 报道约 0.03 dB/km [p6, p7]
  - 仿真：NANF 在 1400–1600 nm 带宽超过 SSMF 的 2 倍；相对 NZ-DSF 除 1460 nm 附近 60 nm 外带宽更大 [p8]
  - SiP 调制器：OOK 256、PAM4 290、PAM6 300 Gb/s（毛速率）；256 GBaud OOK 光背靠背约 3.5 dBm、3.1 km HCF 约 8 dBm 达 HD-FEC（55 前馈 + 55 反馈抽头；引 D. Cirjulina, ECOC 2025 Tu.04.07.2）（看图核实）[p9]
  - 4.96 Tbit/s DWDM IM/DD：31 路 WDM，11.6 km HCF；80 GBaud PAM4（BW 44 GHz）、64 GBaud PAM6（35.2 GHz）、44 GBaud PAM8（24.2 GHz）；BER 在 6.25% HD-FEC 门限内（OECC 2026 Mo1A-2）[p10]
  - PAM12 二维映射：两符号时间交织，7 bit/两符号 = 3.5 bit/symbol；Cross-PAM12 调制 58 GBaud [p12]
  - 202 km 单跨 HCF：34.5 dBm EYDFA 输出，11 段光纤（约 15.5–21.6 km 每段），总插损约 51 dB；双嵌套反谐振无节点设计，第一反谐振窗口；C 波段 CD 约 3.8–4 ps/nm/km [p18]
  - 20×160 GBd OOK WDM，覆盖 C 波段约 4.5 THz，均低于 20% SD-FEC 门限，约 3.2 Tb/s 总吞吐 [p19]
  - SiN 集成 ROSS（递归光谱切片器）：200 GBd OOK 与 145 GBd PAM4 于 202 km 单跨、20% SD-FEC 门限下；容量距离积 646.4 Tb/s·km [p20]
  - 1 µm 宽带 YDFA：输入 -5 dBm 时 1030–1080 nm 增益 >22 dB，1020 nm 约 19.5 dB；泵浦 300 与 350 mW；90 Gb/s Nyquist PAM4 于 2.24 km NANF，BER 与背靠背几乎相同 [p24, p25]
  - 数据+供电：1.21 km HCF，800 nm 供电约 250 mW 输入，1550 nm 数据，0.8 dB/km @800 nm，发射到电输出总效率 17% [p26]
  - 3 km NANF 带内传输 WDM 数据与供电，HCF 无功率代价或 BER 劣化，SMF 中数据严重受损 [p27]
- 提到的公司/客户/产品/标准：YOFC；EPSRC；SARANDLABS/Lumenisity 相关标识；SD-FEC/HD-FEC；EYDFA、YDFA、BDFA、Raman
- 与业界对比或记录声明（SOTA/首次/record）：p20 图中标注 202 km、200 GBd 位于单通道 GBd·km 曲线约 40k 附近，并声称"this work"在 HCF/SMF 对比中最右上；"wideband YDFA 此前未被探索"[p24]
- 推荐配图页：p20（单通道与 WDM 与他人工作对比散点，含 646.4 Tb/s·km）；p10（31 路 4.96 Tb/s 与眼图）；p7（HCF 损耗演进）

### 0922-Tu1-B4-北邮-物理驱动迁移学习预测空芯光纤DCI的OSNR.pdf
- 讲者/机构：Jiahui Xu 等（北京邮电大学信息光子学与光通信国家重点实验室，中国电信研究院） | 题目：Physics-Driven Transfer Learning Approach for OSNR Prediction in Hollow-Core Fiber-Based Data Center Interconnect Networks（Tu1-B4） | 类型：学术论文
- 方向归属（主/次）：主 1（AI 光网络/DCI）；次 无
- 核心主张：
  1. 提出物理驱动迁移学习（PDTL）预测 HCF DCI 的 OSNR，解决刚性解析模型与实网数据稀缺的双重困境。
  2. 解析模型生成 12,000 合成样本预训练，再用少量实测样本微调。
  3. 仅 91 个现网样本即可捕获实网微畸变。
- 关键数据：
  - 方法：解析模型残差提取器（功率预算 ΔP = P_launch + ΣG_OA − ΣA_WSS − P_rec，解耦确定性设备效应，残差隔离 HCF 微结构形变带来的动态 WDL）；四层 MLP（5→64→32→16→1），12,000 个解析模型合成样本预训练，91 个现网实测样本微调；双学习率：前端物理特征层 5×10^-6、高阶输出层 5×10^-4（看图核实）[p8, p9]
  - 数据：107 个现网样本，91 个用于适配，16 个独立盲测；12,000 合成样本 [p10]
  - 结果：MAE 由 0.478 dB（解析）与 0.434 dB（纯数据驱动）降至 0.328 dB；RMSE 由 1.075 与 0.717 dB 降至 0.388 dB；95% 绝对误差边界 0.6 dB 以内（CDF 图读数 0.566 dB，对比 0.921 与 1.121 dB）；RMSE 降低 64% [p11]
- 提到的公司/客户/产品/标准：中国电信研究院；引用 Fokoua et al., Adv. Opt. Photon. 15 (2023) [p8]
- 与业界对比或记录声明（SOTA/首次/record）：仅与自身基线（解析模型、纯数据驱动模型）对比，无 SOTA 声明 [p11]
- 推荐配图页：p11（三种模型 MAE/RMSE/CDF 对比）；p7（方法框图）

## 本批小结
1. HCF 的价值主张从低损耗转向"低色散、低非线性、低时延"带来的系统简化：南安普顿以 IM/DD 高波特率（200 GBd OOK、31 路 PAM）与 202 km 单跨展示 DCI 潜力，北邮则为 HCF DCI 的运维（OSNR 预测）补充手段（B3、B4）。
2. HCF 的短板仍在残余色散功率衰落与实网变量：B3 用 SiN 集成 ROSS 光学处理代替 DSP 复杂度；B4 指出 HCF 的波长相关损耗与微结构畸变使解析模型不准（B3、B4）。
3. 空芯光纤之外，SDM 路线转向"网络级"问题：B2 表明 RC-MCF 的 MIMO 复杂度瓶颈从光纤转向节点时延对齐（节点内失配最高 3.3 ns 对 PTP 的 <1 ns）（B2）。
4. 新波段成为 HCF 的话题：B3 提出 1 µm（YDFA 1030–1080 nm >22 dB 增益）及数据加供电，显示 HCF 用途向多业务扩展（B3）。
5. 数据稀缺下的 AI 光网络：B4 用物理先验合成数据加小样本微调，91 个实测样本将 RMSE 从 1.075/0.717 dB 降到 0.388 dB，可作为新光纤早期部署的通用范式（B4）。
