---
title: "B11 · DAY1 · C2.1-Su3-Su4-超高速PON混合方案"
tags:
  - ECOC2026
  - DAY1
---

# B11 笔记：ECOC 2026 Workshop「Hybrid Solutions for Very High Speed PON」（9月20日，Málaga）

### 0920-pm-Su3-F-01-主席-开场.pdf
- 讲者/机构：Workshop 组织者（Rene Bonk、Roberto Gaudino、Derek Nesset、Gael Simon） | 题目：Hybrid Solutions for Very High Speed PON — the best (or worst) of Coherent and IMDD worlds? | 类型：Workshop
- 方向归属（主/次）：5 固定与无线接入 PON / 次：无
- 核心主张：
  1. ITU-T 于 2025 年 10 月同意首份 VHSP 增补文件，并继续评估下一代 PON 候选技术。
  2. 混合 DD/相干架构（同一系统内混合直检与相干）是"有意思但研究不足"的选项，相对纯 IMDD 与纯相干。
  3. 目标：让混合、纯 IMDD、纯相干与器件专家同台辩论，评估技术可行性与商业可行性，判断 ITU-T 可能的走向。
- 关键数据：
  - 开场投票 Q1"VHSP 应选哪种技术"：IMDD 27%、Coherent 31%、Hybrid 42%、混合其他 0%、其他 0%（看图核实）[p6]
  - "混合"定义：IM-Tx + 相干接收；先进 Tx（SSB、BGPC、Duobinary 等）+ 直检；上下行可选不同技术 [p4]
  - Session 1 六讲：Verizon、Coherent、Altice Labs、KIT、Sumitomo、MaxLinear，后接 Panel（主持 Rene Bonk）[p7]
- 提到的公司/客户/产品/标准：ITU-T、Verizon、Coherent、Altice Labs、KIT、Sumitomo Electric、MaxLinear、Mentimeter
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p4（VHSP 方案空间：IMDD / 混合 / 全相干的分类示意）

### 0920-pm-Su3-F-02-Verizon-超高速PON的三个W.pdf
- 讲者/机构：Jun Shan Wey / Verizon | 题目：The 3Ws of VHSP: Why? What? and When? | 类型：邀请报告（运营商需求）
- 方向归属（主/次）：5 固定与无线接入 PON / 次：6 光纤传感 DAS（DFOS 作为需求）
- 核心主张：
  1. ITU-T SG15 ION-2030 愿景下 VHSP（G.Sup88）面向 AI、DCI、宽带接入。
  2. 技术路线多但"能走通的少"，候选包括直检（IM、DCPC、SSB/OSSB、ODB）、相干（DP-QPSK、PTBC DP-QPSK、RV-DSCM QPSK）与混合（DS 相干/US IMDD；DS IMDD/US IM-Tx+Coh-Rx）。
  3. "每种技术都认为自己最好，挑战是选出最适者"。
- 关键数据：
  - 运营商愿望：系统总容量 100 或 200 Gb/s；4 种 ODN 用例：最大 1×128 分光、最高 E2（35 dB）光功率预算等级、20/30 km 光纤、20 km 差分距离；6 种业务用例、6 种共存场景；另需 DFOS 传感与最小化功耗 [p5]
  - 波长规划 WP-A 1290–1330 nm、WP-B 1330–1370 nm、WP-C C 波段 [p8]
  - 候选符号率：PAM4 1×200 GBd；PAM2 固定 1×100/N×100/N×50 GBd，可调 N×100 GBd；SSB/OSSB 1×120、2×120 GBd；DP-QPSK 1×60 或 1×120 GBd；PTBC 可调 n×30/n×60 GBd [p7]
  - 时间线：VHSP 2022 立项、2025 G.Sup88 批准、2027 各类别选技术、2028 最终技术选择、2028–2033 标准、2035+ 商用；对比 50G-PON 2016 立项、2026 商用，NG-PON2 2010 立项、2019 商用 [p11]
  - FSAN 路线：G-PON(2004) 2.5G → XG(S)-PON 10G → NG-PON2 4x10G → HSP TDM(2021) 50G → WDM PON(2023) 20x25G → HSP TWDM(2027+) Nx50G → VHS-PON（2030+）200G → 未来 PON 2035+；BiDi PtP 2024 年 100G、2029+ 200G；2026+ 动因含时敏业务、6G 承载、工业 PON、光纤传感 [p10，看图核实]
- 提到的公司/客户/产品/标准：G.Sup88、G.sup.ION-aiBB、XGS-PON、50G-PON、NG-PON2、10G-EPON、25GS-MSA、FSAN
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p7（技术候选树与符号率）；p11（VHSP 与 50G-PON、NG-PON2 时间线对比）

### 0920-pm-Su3-F-03-AlticeLabs-混合方案的工程视角.pdf
- 讲者/机构：Claudio Rodrigues / Altice Labs | 题目：Hybrid Solutions for VHSP: A Practical Engineering Perspective | 类型：邀请报告
- 方向归属（主/次）：5 固定与无线接入 PON / 次：无
- 核心主张：
  1. 混合方案有望以"类 IMDD 经济性"取得"类相干性能"，但关键问题不是能否实现，而是额外性能是否值得额外成本、功耗与运维复杂度。
  2. 全 IMDD 最简单最便宜，但灵敏度与传输距离在 VHSP 速率下成为主要约束；全相干 ONU 技术强大但对成本敏感 ONU 可能过度。
  3. 获胜者未必性能最优，而是"百万用户规模下每美元性能最好"的方案。
- 关键数据：
  - 比较了 6 种 ONU 架构：1 IMDD、2 全相干、3 相干 intradyne/homodyne Rx+IMDD Tx、4 偏振分集外差数字 I/Q、5 单偏振外差数字 I/Q+IMDD Tx、6 全相干 Tx+IMDD Rx；用雷达图（0–6 刻度）比较 DSP 负载、DSP 复杂度、Rx 灵敏度、PIC 复杂度/面积、ADC 带宽、制造复杂度、成本、功耗、Reach：IMDD 各轴约 1–2 但灵敏度与距离受限；全相干多数轴约 5–6"对成本敏感 ONU 过度"；方案 3 在保持低成本 ONU Tx 的同时获得高灵敏下行接收；方案 5 把复杂度从光学移到高速 ADC/DSP（ADC 带宽轴最高）（看图核实，雷达图读数为估计）[p5–p8]
  - 方案3 被评为"比全相干收发更适合 PON：高灵敏下行 + 低成本 ONU Tx" [p7]
  - 方案5 把复杂度从光学移到很高速 ADC 与 DSP [p8]
- 提到的公司/客户/产品/标准：无
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p5（六种 ONU 架构的复杂度/成本雷达图对比）

### 0920-pm-Su3-F-04-住友电工-数据中心光源用于PON.pdf
- 讲者/机构：K.P. Jackson / Sumitomo Electric Device Innovations USA | 题目：Leveraging Data-Center Optical Sources for VHSP PON: Opportunities for Coherent Lite and Hybrid Architectures | 类型：邀请报告（器件）
- 方向归属（主/次）：5 固定与无线接入 PON / 次：3 Scale-out 光源（EML/CW DFB/可调激光器）
- 核心主张：
  1. 电信一直并将继续借用数据中心器件技术；VHSP 可借数据中心规模，但需权衡电信特有要求。
  2. 电信特有代价：更宽温度范围、突发模式（激光频率偏移、关断能力）、更高链路预算（分光损耗、光纤距离）。
  3. 开放问题：以更高成本定制器件，还是调整系统要求以适配标准大批量器件。
- 关键数据：
  - VHSP 需求：100–200 Gb/s、20–40 km、35 dB 损耗预算，与旧 PON 共存；标准化时间线 2023 需求 → 2023–2027 技术探索 → 2027–2028 技术选择 → 2028–2031 建议书 → 2031–2032+ 批准与部署 [p4]
  - 100 Gbd（200 Gb/s）EML，带宽 >60 GHz；下一代 200 Gbd（400 Gb/s）[p6]
  - EML+SOA（50G）：49.7664 Gb/s NRZ，TLD=45℃，Vpp=1.8 V，无 FFE。条件1/条件2：LD 电流 120/70 mA，SOA 电流 100/50 mA，EA 电压 −1.15 V，波长 1341.7/1341.1 nm，Mask margin 19/8.9%，Pave 13.58/11.94 dBm，Poma 15.04/13.54 dBm，消光比 7.52/7.92 dB，功耗 333.7/159.8 mW；另图示眼图 ER 4.96 dB、TDECQ 1.81 dB [p6]
  - 半可调 EML：C/L 波段约 6–8 信道，25 Gb/s；调谐波长约 1528→1538 nm 随调谐功率 0–90 mW（读图）；线宽@100 MHz 约 0.7–1.1 MHz（读图）；CoC 功耗约 160–250 mW（读图）[p9]
  - 数据中心激光器数量增长图：EML CAGR=48%，CW CAGR=110%；另一曲线 CAGR=23.5%（坐标为读图，未核对）[p5]
  - PCSEL（未来）：≥1.3 µm 单模面发射，发散角约 1°，适合 1D/2D 阵列（1 mm 见方 4 波长）；CW 25°C 输出 800 mW，SMSR >78 dB，RIN −150 dB/Hz（400 mW），白噪声线宽 πSf = 20 kHz（看图核实）[p10]
- 提到的公司/客户/产品/标准：Yole Group、InP EML、高功率 CW DFB、可调激光器、PCSEL、SiPh/TFLN、NG-PON2、APN
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p6（100 Gbd EML 带宽响应、眼图与 EML+SOA 参数表）；p9（半可调 EML 的调谐、功耗与线宽）

### 0920-pm-Su3-F-05-Coherent-相干可插拔生态能否复用.pdf
- 讲者/机构：Noriaki Kaneda / Coherent（Coherent Corp.） | 题目：Can VHSP hybrid solutions benefit from developments in the coherent pluggable eco-system? | 类型：邀请报告
- 方向归属（主/次）：5 固定与无线接入 PON / 次：2 ZR/ZR+/CL（相干可插拔生态）
- 核心主张：
  1. 可以：尽管存在需求缺口，VHSP 混合尤其是相干 PON 可受益于相干可插拔生态：更多技术选择、更成熟低成本通用器件与共同制造工艺。
  2. 混合方案（ONU Tx 用 IM、其余相干）之"坑"是 IM-相干检测对消光比极敏感。
  3. 缺口可通过固定但频率受控的 DFB、突发模式 booster SOA、ONU 侧 SOA 等弥合。
- 关键数据：
  - 相干可插拔现状：400ZR（QSFP-DD）2020 年首次大规模采用；可插拔出货量 2022 年起超过嵌入式；2025 年可插拔收入 \$2B（Cignal AI）；估计出货超 600,000 件；2026 年嵌入式仍约 33% 份额（LightCounting）；800ZR 正大规模部署，1600ZR 预计 2028 年 [p2]
  - 4 dB 消光比的 EML（100G/lane IMDD 可插拔常用）相对 BPSK 增加约 14 dB 灵敏度代价；曲线显示 NRZ 相对 BPSK 代价约 15 dB@ER 3 dB 降至约 5 dB@ER 14 dB（读图）[p6]
  - ZR / CL / VHSP 相干 PON 对比表：FEC 限 ZR 4e-3–2e-2、CL 8e-3 或 1.1e-2、CPON 1e-2 或 2e-2；数据率 ZR 100/400/800/1600、CL 800/1600/3200、CPON 至少 200G；Tx 功率 ZR 0/−8 dBm、CL −9.5 dBm（800G OIF）、CPON 至少 0 dBm（待定）；激光器 ITLA 150/300 kHz、固定 DFB 1 MHz、固定 DFB；光功率预算 ZR 22 dB（100ZR），29 dB 可支持，CL 7–14 dB，CPON 29–35 dB；链路 ZR 放大 80–1000 km，CL 无放大 10–20 km，CPON 20 km [p7]
  - 带 booster SOA 的相干 PON（K. Vijayan, OFC 2025）：链路预算 400 Gb/s（16-QAM）为 29 dB、200 Gb/s（4-QAM）为 41 dB；可免去 OLT 突发模式 TIA/DSP；标准 400ZR+ 模块的 QPSK 模式可支持 200 Gb/s [p8，看图核实]
  - 100G ZR QSFP28："业界首个"，Steelerton DSP 低于 2 W，配功耗优化可调激光器与高集成硅光 PIC（2023 Lightwave Innovation Reviews 5.0）[p4，看图核实]
  - 缺口与对策表：激光器（固定但频率受控 DFB）、OLT 需突发 TIA/DC 耦合（ONU 突发 booster SOA）、下行预算（OLT booster SOA）等 [p9]
- 提到的公司/客户/产品/标准：400ZR、800ZR、1600ZR、400ZR+、100G ZR QSFP28、Steelerton DSP、Coherent Lite（CL）、OIF、Cignal AI、LightCounting
- 与业界对比或记录声明（SOTA/首次/record）："industry's first and only DSP under 2W"（Coherent 100G ZR）[p4]
- 推荐配图页：p7（ZR/CL/VHSP 相干 PON 参数对照表）；p8（booster SOA 相干 PON 架构与 BER 对预算曲线）

### 0920-pm-Su3-F-06-KIT-混合相干PON的挑战.pdf
- 讲者/机构：Sebastian Randel / KIT | 题目：Challenges and Possibilities of Hybrid Coherent PONs | 类型：邀请报告
- 方向归属（主/次）：5 固定与无线接入 PON / 次：3 调制器/光源（SOH、集成）
- 核心主张：
  1. 纯 IMDD：器件少、50 Gb/s 以内成熟，但色散敏感、需高带宽器件、接收灵敏度有限；纯相干：可数字补偿 CD/PMD、模拟带宽可降低（DP-IQM）、灵敏度高、可用 C 波段，但器件数多、需可调激光器、存在多径干扰、不共享频谱、光纤非线性。
  2. 以"hybrid"词源调侃：杂交可能产生意外结果、后代通常不育，指出混合的核心问题。
  3. PONTROSA 项目主张以混合光电集成释放（混合）相干 PON 潜力。
- 关键数据：
  - PONTROSA：ONU-TROSA 含 EML+SOA（III-V）与相干 SiPh-Rx，伙伴含 Fraunhofer、SilOriX [p4]
  - Si3N4 外腔激光器（ECL）+ 光子线键合混合集成 III-V 增益；亚 kHz 本征线宽（Maier 等，JLT 41, 3479, 2023）；调谐范围图示约 1460–1580 nm [p5]
  - SOH 调制器：UπL = 0.32 Vmm；112 Gbit/s 线性驱动 @ 270 mVpp（OFC 2024 M3K.6）[p6]
- 提到的公司/客户/产品/标准：PONTROSA、SilOriX、Fraunhofer、SOH 技术
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p2（纯 IMDD 与纯相干的优劣对照）

### 0920-pm-Su3-F-07-MaxLinear-三种方案的DSP考量.pdf
- 讲者/机构：Jose Galan（含 Rainer Strobel、Roland Zukunft、Sridhar Ramesh）/ MaxLinear | 题目：DSP considerations for coherent, IMDD and hybrid approaches in VHSP systems | 类型：邀请报告（DSP）
- 方向归属（主/次）：5 固定与无线接入 PON / 次：1 oDSP
- 核心主张：
  1. IMDD 实现 200G 净速率可行，但计算复杂度上升且双波长增加光器件成本。
  2. 相干 200G 下行直接，上行突发模式是问题；从 DSP 看全相干优于简化相干（后者导致极高波特率接收机）。
  3. 混合方案看起来有吸引力，需进一步研究。
- 关键数据：
  - 目标：最大 200 Gbit/s 净速率 [p2]
  - IMDD NRZ 200G：O 波段两波长各 120 Gbaud NRZ；符号率接收，两个 120 GS/s ADC（5 bit，每波长一个）；21 抽头 FFE（5×10^12 MAC/s）+ BCJR + 软输入 LDPC；时钟恢复关键，CDPC 会使下行信号呈突发（看图核实）[p4]
  - CDPC：10 抽头、双波长约 2.4×10^12 MAC/s；问题：Tx 信号变为突发不连续影响时钟恢复；光纤长度已知但零色散波长（ZDW）未知，难识别正确 CDPC 组 [p6]
  - PAM-4 CD 容忍度好但 OMA 灵敏度差；单波长 120 GBaud 灵敏度预计更差（待定）[p7]
  - 全相干 DP-QPSK 60 GBaud 达 200G；T/2 均衡时 4 个 ADC 120 GS/s（对比 NRZ 两个 120 GS/s）；2×2 MIMO 均衡 42 抽头，约 80×10^12 MAC/s [p9]
  - 全相干仿真：可满足 32 dB Class C+ 预算，含损伤下灵敏度约 −33 dBm；BER 门限线约 2e-2，Plo 6–16 dBm 多条曲线（读图）[p10]
  - 简化相干（Alamouti 编码，单偏振）：120 GBaud QPSK，62 抽头，60×10^12 MAC/s；或 60 GBaud 16-QAM，42 抽头，20×10^12 MAC/s；T/2 均衡需 2 个 ADC 240 GS/s；120 GBaud QPSK 在 BER 1e-4 附近约 −29 至 −30 dBm，60 GBaud 16-QAM 约 −22 至 −24 dBm（读图）[p12]
  - 混合：相干下行+IMDD 上行避开突发相干问题，但仍需 ONU 侧 LO；OLT 相干接收+ONU 仅 IMDD 需比全相干更高波特率，结合 ODB 或 SSB 优于常规 IMDD [p13]
- 提到的公司/客户/产品/标准：BCJR、MLSE、LDPC、Alamouti、Class C+
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p10（全相干 DP-QPSK 灵敏度仿真，−33 dBm）；p12（简化相干两种配置的 DSP 负担与 BER）

### 0920-pm-Su4-F-00-全场-Session2圆桌预告与投票.pdf
- 讲者/机构：主持团队 | 题目：Pre-Panel 2 Audience Poll / Session 2 Speaker Panel Q&A | 类型：Workshop
- 方向归属（主/次）：5 固定与无线接入 PON / 次：无
- 核心主张：Session 2 前的观众投票；Session 2 讲者面板（Philippe Chanclou/Orange、Vincent Houtsma/Nokia、Giuseppe Rizzelli/PoliTo、Ryo Koma/NTT、Giuseppe Talli/Huawei、Martin Kuipers/Adtran，机构对应以 logo 为准，图上看的是 OCR 名单，未看图）。
- 关键数据：投票通过 Menti 链接；无技术数据 [p2–p3]
- 提到的公司/客户/产品/标准：Orange、Nokia、PoliTo、NTT、Huawei、Adtran
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：无

### 0920-pm-Su4-F-01-Orange-运营商对超高速PON的需求.pdf
- 讲者/机构：Philippe Chanclou（含 Fabienne Saliou、Gaël Simon、Jérémy Potet）/ Orange Research | 题目：An operator's perspective on the needs and approaches for VHSP | 类型：邀请报告（运营商）
- 方向归属（主/次）：5 固定与无线接入 PON / 次：6 光纤传感 DAS
- 核心主张：
  1. 光纤基础设施要约 15 年运营才接近完全覆盖；G-PON 到 XGS-PON 的家庭网关迁移刚开始。
  2. VHS-PON 网络运营时间线约 2040，无 G-PON 共存，1310 nm（和 1490 nm）频谱空出，这是否有利于 IMDD 方案？
  3. 光纤传感是光纤资产"第二阶段商业价值创造"，需与 PtP 单纤双向（ITU-T G.9806 系列）及 PON 接口共存。
- 关键数据：
  - VHS-PON 关键点：候选 2×100 Gbit/s 或 4×50 Gbit/s；光预算 Class C+ 必需，可能 Class D（增加第二级分光器达 1:256 ODN）；带多 PON 接口的光纤网关用于迁移；OLT/ONU 节能机制 [p11]
  - 现网 OLT 分光比 1:64 至 1:128 [p3]；MPM OLT 端口（G-&XGS-PON）演进至三重 MPM（XGS-& HS-PON、& VHS-PON）路线为"纯推测" [p10]
  - Livebox 7：GPON/XGS-PON 兼容网关，10G 以太口，自动 PON 技术选择 [p8]
  - 光纤传感分两阶段：先用 FTTx 缆中多余暗光纤/绕过分光器的 PtP；后在 PtP 与 PON ODN 上共存 [p14]
  - 传感应用：地质灾害、铁路、周界安防、电力线/管线/结构健康、缆线监控等 [p13]
- 提到的公司/客户/产品/标准：Orange、G-PON、XGS-PON、HS-PON、VHS-PON、Livebox 7、BBF.247、ITU-T G.9806
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p10（PON 世代与 MPM OLT 迁移到 VHS-PON 的推测路线）；p11（VHS-PON 运营商关键要求）

### 0920-pm-Su4-F-02-Nokia-能否仍用强度调制直检.pdf
- 讲者/机构：Vincent Houtsma / Nokia Bell Labs | 题目：Can VHSP be still fully IM-DD based? | 类型：邀请报告
- 方向归属（主/次）：5 固定与无线接入 PON / 次：无
- 核心主张：
  1. 前提：能用低成本 IM/DD 就该用；问题可重述为"VHSP 还能完全低成本吗？"
  2. NRZ 在 100–120 Gb/s 时色散容忍度将工作波段限制在零色散波长附近（1290–1330 nm），不需要 GPON 共存时可接受。
  3. 需要 GPON 共存则用混合"IM-DD"技术：增加 OLT 复杂度/成本，换取 ONU 保持经典低成本 IM-DD。
- 关键数据：
  - 三档方案："Plan A" 1290–1330 nm 全 IMDD（DS/US 均 IM-DD，OLT+ONU 成本最低，无 GPON 共存）；"Plan B" 1330–1370 nm，DS 为 ODB-DD/SSB-DD/DCPC-DD，US 为 IM-COH（ONU 全 IM-DD、成本最低，OLT 更贵，可与 GPON 共存）；"Plan C" C 波段，DS 相干、US 相干或 IM-COH（ONU、OLT 成本最高，可共存）[p8，看图核实]
  - 混合选项优缺点：ODB @OLT Tx（JLT 2024，100 Gb/s DS，38 dB 预算，收益有限）；OLT 预补偿 CD（需 IQ 调制器，2 个嵌套 MZM，线性度要求高）；SSB @OLT（可用单 DD-MZM 实现，需至少驱动一臂模拟信号；ECOC 2026 MoS-G1）；OLT 相干接收（CD 代价约 0，需全相干突发接收机与 OLT 侧波长严格对准 ONU；ECOC 2026 MoS-G2）[p7]
  - 引用：V. Houtsma 等 ECOC 2025 "100–120G IM-DD PONs with 32 dB power budget and TDEC with DFE based reference receiver"；100–120 Gb/s NRZ 色散容限把 VHSP 工作波长限制在零色散附近 1290–1330 nm [p4，看图核实]
- 提到的公司/客户/产品/标准：ITU-T G.Sup88、FSAN Roadmap 3.0、R. Borkowski 等 OFC PDP 2025 突发相干 PON 上行（20 nm 快速 LO 调谐）
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p7（四种混合 IM-DD 技术的优缺点与框图）；p8（Plan A/B/C 分类表）

### 0920-pm-Su4-F-03-PoliTo-色散数字预补偿.pdf
- 讲者/机构：Giuseppe Rizzelli / Politecnico di Torino（OPTCOM / PhotoNext；部分研究为与 Huawei Munich 的合同研究） | 题目：Digital Chromatic Dispersion Pre-Compensation for VHSP | 类型：邀请报告
- 方向归属（主/次）：5 固定与无线接入 PON / 次：1 oDSP
- 核心主张：
  1. DCPC 把色散补偿从 ONU 移到 OLT，使超高速 IM-DD PON 可行；逐时隙 DCPC 支持多用户，含各 ONU 专用载荷与鲁棒公共头。
  2. 测试确认 DCPC 对 MPI 稳健，可与 SSB 结合。
  3. 混合 DD/相干运行有望在同一 PON 中兼容标准距离与延伸距离 ONU。
- 关键数据：
  - 100G PAM-4 C 波段下行 20 km 连续传输：对光纤长度失配的容忍约 ±2 km，但 ITU-T PON ODN 要求 0–20 km 运行 [p7]
  - 多用户 PON 100 Gbps PAM-4 载荷，BER 目标 2×10^-2：ODN 损耗 >31 dB@20 km；CD 容忍 ±40 ps/nm（C 波段）、±53 ps/nm（O 波段）；0 km 时 ODN 损耗峰值约 35 dB，11.5 km 约 34 dB，20 km 约 32–33 dB；对照线 Class N1 = 29 dB [p8]
  - PAM-2 + 相干接收（Mo4-P-79）：ECL 与 DFB 激光器下，相干接收（20 km、40 km COH）在 BER 2×10^-2 处的 ODN 损耗约 46 dB（读图），DD 接收 10 km 约 38–40 dB、20 km 约 40–41 dB（读图）；需修改相干 DSP 以处理"完全偏振、带强光直流分量"的信号 [p10]
  - DCPC 容忍度：按 CD^PAM_max 精确预补偿时，PAM 的 CD 容限翻倍（CD^DCPC_max = 2·CD^PAM_max；CD^Residual = CD^Accumulated − CD^DCPC）[p5，看图核实]
  - 关联论文：MoS-G3/613（MPI 与 DGD 容忍）、Mo4-P-79/154、Mo4-P-86/486（PAM2-SSB+DCPC，2×100 Gb/s/λ VHSP 下行）[p12]
- 提到的公司/客户/产品/标准：Huawei Munich、ITU-T PON ODN 0–20 km、Class N1
- 与业界对比或记录声明（SOTA/首次/record）：其 2020 年首个 C 波段 PAM-4 结果（"100+ Gbps/λ 50 km C-Band Downstream PON"）[p7]
- 推荐配图页：p8（多用户 100G PAM-4，ODN 损耗对残余 CD 曲线）；p10（DD 对相干接收 PAM-2 的 BER 对 ODN 损耗）

### 0920-pm-Su4-F-04-NTT-单边带抑制色散代价.pdf
- 讲者/机构：Ryo Koma / NTT Access Network Service Systems Laboratories | 题目：Single-Sideband Solutions for CD Penalty Mitigation in the Era of VHSP and 50G-TWDM PONs | 类型：邀请报告
- 方向归属（主/次）：5 固定与无线接入 PON / 次：无
- 核心主张：
  1. VHSP 与 50G-TWDM-PON 可选波长规划含 E 波段与 C 波段，因此增强 CD 容忍度是必须的（标准 ODN：20 km、光功率预算 29 dB）。
  2. SSB 传输虽然增加发射机复杂度，但 CD 容忍度高且接收机简单，适合高速 PON 下行。
  3. 剩余挑战是增加光预算（SSB 灵敏度相对偏低）。
- 关键数据：
  - 50 Gbaud NRZ SSB 实验：Tx 功率 +10 dBm，61 抽头 FFE，25G 级 APD，CD 系数 17 ps/nm/km；灵敏度优于 −18 dBm（BER=1e-2）时 CD 代价小于 4 dB，累积 CD 最高 680 ps/nm（对应 40 km）；无 CD 时灵敏度约 −21 dBm（读图）[p7]
  - 线性近似距离表（E 波段 4 ps/nm/km；C 波段 17 ps/nm/km）：50G：E 波段 2 dB 代价 60 km、3.5 dB 代价 170 km；C 波段 14 km（实测）/40 km（实测）；100G：E 30/85 km，C 7/20 km；200G：E 15/42.5 km，C 3.5/10 km [p8]
  - 若容忍 4 dB 代价：100 Gbps 20 km、200 Gbps 10 km 在所有波段可实现；结合 DCPC 可进一步减小代价 [p8]
  - 功率衰落陷波示例（DSB 50 GBd NRZ）：18 km 时首个陷波 14.26 GHz、40 km 时 9.56 GHz；另一图 24 km 时 12.35 GHz；SSB 仿真谱无陷波，P_out ∝ cos²(πDλ²Lf²/c)（看图核实）[p5–p6]
  - 光学 SSB（OSSB）：LD+EA/MZM+光滤波器，边带抑制高，需精确控制滤波器与激光波长 [p9]
- 提到的公司/客户/产品/标准：50G-TWDM-PON、E 波段（LWP 光纤）、O 波段已全部占用、ECOC 2025 IQ-MZM SSB 下行
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p8（E/C 波段各速率的代价-距离表）；p7（50 Gbaud SSB 灵敏度与 CD 代价曲线）

## 本批小结
1. 混合方案的定义并不统一，业界主流形态有二：下行相干/上行 IMDD，或 OLT 相干接收/ONU 仅 IM-Tx；后者的代价是接收灵敏度与 OLT 复杂度（来自 01 主席开场、02 Verizon、06 KIT、07 MaxLinear、Nokia p7）。
2. "IM 发射+相干检测"对消光比极敏感：Coherent 称 4 dB ER 的 EML 会比 BPSK 多约 14 dB 灵敏度代价；Nokia 指出需 OLT 端波长严格对准 ONU；MaxLinear 认为需更高波特率（05 Coherent、Nokia、07 MaxLinear）。
3. 直检阵营核心手段是"把色散补偿放到 OLT"：DCPC（PoliTo：C 波段 100G PAM-4 ODN 损耗 >31 dB@20 km）、SSB（NTT：50 Gbaud 累积 CD 680 ps/nm 时灵敏度优于 −18 dBm，代价 <4 dB）、ODB；共同代价是 OLT 需要 IQ/MZM 与 DAC，且 DCPC 需知道 ONU 光纤长度/ZDW（PoliTo、NTT、MaxLinear、Nokia）。
4. 相干阵营依赖可插拔生态复用：Coherent 给出 ZR/CL/CPON 参数对照与带 booster SOA 的 29 dB（400G）/41 dB（200G）预算演示；MaxLinear 仿真全相干 DP-QPSK 灵敏度约 −33 dBm 可满足 32 dB Class C+；但上行突发模式仍是难点（05 Coherent、07 MaxLinear、Sumitomo）。
5. 器件/成本视角：Sumitomo 提出借用数据中心 InP EML/CW DFB/半可调激光器，代价是宽温、突发模式与更高链路预算；Altice 强调"每美元性能"和 ONU 成本决定胜负；KIT 提出 PIC/SOH/Si3N4 ECL 混合集成（Sumitomo、Altice、KIT）。
6. 时间线与运营商约束：Verizon 预计 2027 年各类选技术、2028 最终选择、2035+ 商用；Orange 预计 VHS-PON 网络运营约 2040，Class C+ 必需、可能 Class D，并要求传感共存（Verizon、Orange、Nokia）。
