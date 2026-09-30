---
title: "B36 · DAY2 · _合集待拆"
tags:
  - ECOC2026
  - DAY2
---

# B36 笔记：0921 C2.2厅 PON专场连拍（VHSP 超高速PON）

### 0921-合集待拆-全场-C2.2厅PON专场连拍.pdf（第1–20页）
- 讲者/机构：Christoph Füllner 等（Nokia Bell Labs 固网部/Nokia Fixed Networks CTO Office） | 题目：Low-Complexity VSB Generation and Chirp Management for VHSP Downstream Links Supporting GPON Coexistence（Mo5-G1） | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 无
- 核心主张：
  1. GPON 共存抬高 VHSP 下行的色散容限要求（结论页 Challenge）；采用 hybrid PON 思路，OLT 侧做低复杂度 VSB 生成+啁啾管理，ONU 保持廉价直检。
  2. 用 DD-MZM + 简单模拟/数字延时 + 巧选偏置点即可对劣质发射机产生 VSB，无需 IQM，也无需 burst-like 下行。
  3. 概念验证 100 Gb/s：0–125 ps/nm 累积色散内罚值 <3 dB [p20]。
- 关键数据：
  - 100 GBd NRZ-OOK；DAC 100 GS/s；DD-MZM 静态 ER 12 dB；21 tap 预补偿；发射 7 dBm；光纤累积色散 0…137 ps/nm；接收 SOA+4 nm 滤波+PIN，ADC 103 GS/s，均衡 FFE21/DFE3 或 FFE+MLSE（DAC/ADC 带宽受限故需 MLSE） [p12]
  - DSB 情形约 40 ps/nm 色散容限（3 dB 罚值）；数字延时可改善有色散时的灵敏度；偏置点 α≈0.2（正交点负斜率）；B2B 灵敏度约 -24 dBm（图读数，AOP，最优延时附近） [p14]
  - α=-0.6 下动态按 ONU 调延时（图中标注 0、9、11、13、15、17 ps 等）优于固定 1-sample 延时；作者结论“收益不足以证明 burst-like 下行值得” [p19]
  - FFE21/MLSE 比 FFE21/DFE3 灵敏度约好 2–3 dB（图读数），两者曲线形状相同，说明并非只靠 MLSE [p19]
  - OCR 页4：GPON 共存需要 120 ps/nm 色散容限（仅 OCR，未看图）
- 提到的公司/客户/产品/标准：ITU-T VHSP supplement、GPON、XG(S)-PON、25GS-PON、50G-PON；VLAIO FALCON 项目/欧盟资助
- 与业界对比或记录声明（SOTA/首次/record）：无明确 record 声明；对比对象为 IQM/SSB 方案（IQM 插损高、电路复杂；SSB 边带抑制受 MZM 设计、驱动时延/幅相失衡、数字滤波抽头数影响），本方案以 DD-MZM + V2 模拟/数字延时生成 VSB，并选择偏置点 Vb+/Vb− 优化啁啾 [p5–p8，看图核实]
- 推荐配图页：p14（各累积色散下灵敏度 vs 数字延时曲线，展示 VSB/DSB 区分）；p12（实验装置+DSB/VSB 频谱+偏置点）

### 0921-合集待拆-全场-C2.2厅PON专场连拍.pdf（第21–32页）
- 讲者/机构：Vincent Houtsma、Kovendhan Vijayan、Laurens Breyne、Robert Borkowski、Doutje van Veen（Nokia Bell Labs） | 题目：On the Extinction Ratio penalty and Sensitivity of next-generation 120 Gb/s upstream IM solutions for Very High-Speed PONs（Mo5-G2） | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 无
- 核心主张：
  1. ER 惩罚取决于接收机实现，低 ER 下显著恶化灵敏度；建模与实测吻合，可用于未来 VHSP 标准（OA-DD 与 COH 接收机）。
  2. ER=6 dB 的 NRZ 上行，COH 与 DD 都能满足功率预算，发射功率需求相近（约 +8.5 dBm，29 dB 预算）。
  3. COH 的好处是色散可完全补偿，使 C 波段运行、便于 GPON 共存；64 GBaud（class 40）相干接收机+低复杂度 DSP 可收 120 Gb/s NRZ，降成本、适配突发模式。
- 关键数据：
  - 纯 IM-DD 100–120G NRZ：3.5 dB 罚值下色散容限约 ±50~60 ps/nm（图读数），故只能靠近零色散波长 1290–1330 nm；SOA-PIN(FFE+DFE) 120G 曲线更窄 [p22]
  - 120 Gb/s NRZ 带宽受限 COH：BER=2e-2、ER=8.5 dB 时灵敏度 -23.1 dBm；20 km SMF 后 OPP <0.4 dB（CD 在定时恢复前补偿） [p29]
  - 120 Gb/s NRZ 带宽受限 DD（EDFA-滤波-PIN）：BER=2e-2、ER=8.5 dB 时 -28.7 dBm；讲者称 OA-DD 实际优于 COH（ER 惩罚小、系统带宽受限、集成相干接收机附加损耗） [p30]
  - ER=6 dB 现实检查：COH 120G 灵敏度 -20.8 dBm（BER=2e-2）；29 dB 光预算、假设 0.3 dB CD 罚值 → ONU 平均发射功率最低 +8.5 dBm [p31]
  - 25 Gb/s 全带宽 COH：ER=24.5 dB 时 -41 dBm（BER=2e-2）；SP-BPSK -44.2 dBm、SP-QPSK -42.5 dBm（25 GBd）；ER 降至 13.6/7.9/5.0/3.4 dB 时灵敏度依次劣化；理论上 ER→∞ 的 NRZ 应接近 QPSK、比 BPSK 差 3 dB（看图核实）[p28]
- 提到的公司/客户/产品/标准：50G-PON 标准（APD 接收机假设）、ITU-T VHSP、GPON；EDFA/SOA-PIN、64 GBaud/32 GBaud 相干接收机
- 与业界对比或记录声明（SOTA/首次/record）：p24 称首次给出 ER 惩罚的简化解析式并做多波特率/多ER 详细研究（“which has not been reported in such detail before”，看图核实）；并称以 DD 型 DSP 实现带宽受限相干检测 IM 信号可降低相干接收机带宽与成本 [p24]
- 推荐配图页：p31（实测灵敏度 vs ER，COH 与 DD 两类接收机+理论曲线）；p29/p30（120G COH 与 DD 的 BER 曲线对比）

### 0921-合集待拆-全场-C2.2厅PON专场连拍.pdf（第33–51页）
- 讲者/机构：H. Kharbich、G. Bosco、G. Rizzelli、D. Pilori、V. Ferrero、G. Talli、I. Cano、R. Gaudino（Politecnico di Torino；Huawei Heisenberg Research Center 资助，OPT-PON 合同） | 题目：Investigation of MPI and DGD Tolerance in Digitally CD Pre-Compensated PAM-2 for Very High Speed PON Systems | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 无
- 核心主张：
  1. 50 GBd 实验表明全 CD 预补偿（DCPC）PAM-2 的 MPI 鲁棒性与常规 PAM-2 相近；残余 CD 会加大 MPI 罚值。
  2. 实验与仿真吻合，模型外推到 120 GBd 上 O 波段 VHSP：DCPC-PAM-2 仍有较强 MPI 抗性，明显罚值主要在 SIR<15 dB。
  3. DGD 容限强烈依赖 CD 匹配精度；DGD ≤ 1/2 符号周期时罚值 <1 dB，接近符号周期后罚值显著。
- 关键数据：
  - 50 GBd PAM-2，C 波段，TOP=11 dBm，20 km SMF，D=17 ps/nm/km，全补偿；BER 目标 1e-2 / 2e-2；实验（含 L_DCPC = 3/4、1/2 L_fiber 残余 CD）相对罚值随 SIR 下降，SIR≥约 30 dB 后罚值趋零；1/2 L_fiber 下 SIR 约 12.5 dB 时罚值 >3.5 dB（图读数） [p43]
  - 120 GBd 仿真：TOP=11 dBm，CD_DCPC=30 ps/nm，λ_ZD=1310 nm，D=5.96 ps/nm/km，色散斜率=0，BER 目标 2e-2；ODN 损耗罚值等高线：1.0 dB 线在 Dacc 约 17–49 ps/nm、SIR 下至约 13–15 dB [p47]
  - DGD：符号时间 Ts=8.3 ps；Dacc≈30 ps/nm 处 1.0 dB 线对应 DGD/Ts 约 0.6 [p48]
  - 结论页：SIR<15 dB 时罚值显著；DGD≤1/2·Ts 时罚值<1 dB [p49]
- 提到的公司/客户/产品/标准：Huawei Munich/Heisenberg Research Center、ITU-T G.Suppl.88（10/2025）、ITU-T G.652 色散曲线、PhotoNext Center
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明
- 推荐配图页：p47（120 GBd ODN 损耗罚值 vs 累积色散与 SIR 等高线）；p43（MPI 罚值 vs SIR 实验/仿真）

### 0921-合集待拆-全场-C2.2厅PON专场连拍.pdf（第52–71页）
- 讲者/机构：David Izquierdo、Natalia Herguedas、Pascual Sevillano、Ramon Cajal-Pérez、Ignacio Garcés（Zaragoza 大学 I3A 光子技术组，西班牙） | 题目：200 Gb/s PolMux Link with 32 dB optical power budget, 28 GHz electrical bandwidth and LO reuse for VHS-PONs | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 相干（简化相干接收/外差）
- 核心主张：
  1. 获得 200 Gb/s、25 km 下行，32 dB 光预算，28 GHz 电带宽。
  2. OSSB multiCAP 信号是高速率系统 CD 管理的有效方案；外差方案中演示了偏振复用。
  3. 复用 LO 发送 20 Gb/s 上行，预算相近；DS+US 共占约 40 GHz（约 0.32 nm）光带宽，载波可为任意 C 波段波长，可做多 DWDM 信道。
- 关键数据：
  - 下行：灵敏度 -25 dBm，发射 +7 dBm 对应 32 dB 光预算（BER 阈值 SD-LDPC FEC）；-20 dBm 以上出现误码平台，25 km 后平台升高（推测为光纤非线性引起相位调制）；上行开启（1.5 / 6.5 dBm）灵敏度不受影响 [p66, p68]
  - 下行接收：数字版 Glance 接收机，1 PBS+1 PM 耦合器+2 PD+TIA；DS 星座 EVM 约 13/15%（Sx/Sy） [p59, p63]
  - 上行（LO 复用，外调制器强度调制，Universidad Zaragoza）：HD-LDPC FEC 灵敏度 -31.5 dBm → 33 或 38 dB 预算；以太网 FEC 极限 -26 dBm → 27.5 或 32.5 dB；未见平台；开启下行罚值 <1 dB（以太网 FEC 处）（看图核实）[p69]
  - US 概念验证：两个 DSB multiCAP 4QAM 5 GHz 频带，20 Gb/s；DS 与 US 装入 100 GHz DWDM 信道；另有 50 Gbps multiCAP IM 25 km 准相干接收海报 We4-P81 [p64]
  - 背景：VHSP 需 32–35 dB 预算、20–30 km；FSAN 路线图 VHSP 约 2030+，200 Gb/s 或 2×100 Gb/s [p53]
- 提到的公司/客户/产品/标准：FSAN 路线图、ITU-T VHSP、Glance 接收机、50G-PON、25G MSA、XGS-PON/GPON/TWDM 波长规划
- 与业界对比或记录声明（SOTA/首次/record）：无明确 record 声明
- 推荐配图页：p69（上行 BER 曲线，含 HD-LDPC/Ethernet FEC 阈值）；p64（US LO 复用架构与 DS/US 频谱）；p66（DS BER 与实验装置）

### 0921-合集待拆-全场-C2.2厅PON专场连拍.pdf（第72–104页）
- 讲者/机构：Ivan N. Cano（Huawei） | 题目：Research directions for hybrid-PON in VHSP | 类型：邀请报告/Workshop（据题目页 Security Level: Public）
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 无
- 核心主张：
  1. VHSP 下行评估两种方案（120 Gb/s/λ）：OLT 用 IQ-MZM 发射机、ONU 用常规 DD 接收+DSP；DCPC 与 SSB 均可。
  2. DCPC 移动零色散点，容限约翻倍；更高 CD 需按 CD 对 ONU 分组。SSB 缓解色散衰落，免分组，视工作波长可降 ONU DSP 复杂度。
  3. 两者都可用 2λ×120 Gb/s 满足运营商要求；更高带宽器件可实现单波长方案；上行方向为后续工作。
- 关键数据：
  - VHSP 通用需求：200 Gb/s 业务容量、已部署设施 ≤20 km、与旧 PON 共存 [p74]
  - ITU-T G.Suppl.88（2025年10月发布）三类候选：直检、相干、IMDD-相干混合 [p78]
  - 常规 IM-DD：3 dB 罚值下最大累积 CD 约 22 ps/nm；DCPC 预补偿 22 ps/nm 后最低罚值移至该值，容限约翻倍；20 km 最坏 SMF CD 下最大工作波长约 1325 nm；不同 FIR 系数组（图例 22 / 65 / 105 ps/nm）可拼接覆盖更宽范围 [p87]
  - 1370 nm、20 km G.652 最坏累积 CD 119.3 ps/nm（WP-B，G.Suppl.88 8.4.7）；SPM 在 90 ps/nm 预补偿、Tx 高功率（图例 11/15/16 dBm）下引入罚值 [p89]
  - DCPC-ODB：ODB 3 dB OPP 处累积 CD 约 44 ps/nm；ODB+DCPC 约 90 ps/nm，仍不足 1370 nm 所需 120 ps/nm；加第二个预补偿值（35 与 90 ps/nm 两组）可容忍至 120 ps/nm；含 SPM（Tx +14 dBm）时 90 ps/nm 组出现罚值但 120 ps/nm 仍有余量 [p94]
  - SSB：优化 CSPR 后 120 ps/nm 处罚值 <1.5 dB；3 dB 罚值下可容忍至 320 ps/nm，可在 1515 nm 传 20 km（最坏 CD）；仅 13-tap FFE 在 120 ps/nm 罚值 <2 dB [p98]
  - SSB+DCPC(150 ps/nm)：曲线更平坦，相对 SSB 增加约 1.5 dB 罚值（归因于更高 PAPR）；总罚值 3.5 dB 时 C 波段可行；含 SPM 时 <325 ps/nm 约有 0.5 dB 增益 [p101]
  - 单个复数 FIR（cFIR）可同时实现 DCPC 与 SSB（两功能可顺序叠加，得到 CD 预补偿的 SSB 信号；Huawei，看图核实）[p100]
- 提到的公司/客户/产品/标准：Huawei、Politecnico di Torino 合作文献（ECOC 2025 Rizzelli/Kharbich/Andrenacci；ECOC 2026 Kharbich MPI/DGD；ECOC 2026 Andrenacci PAM2-SSB(+DCPC) 2×100Gb/s/λ）、OFC 2026（Uchiyama 上行突发反推 DCPC 系数；Kharbich 可变距离 DCPC）、ITU-T G.9804.3、G.Suppl.88、Acacia（Malik 的 IMDD vs 相干分界图）、FSAN 路线图
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；对比 DCPC/ODB/SSB/SSB+DCPC 在色散容限上的递进 [p94, p98, p101]
- 推荐配图页：p103（DCPC vs SSB 总结）；p87（DCPC 逐步移动最低罚值点的三联图）；p101（SSB+DCPC 与含SPM 罚值曲线）

## 本批小结
1. 色散容限是 VHSP（100–200G）IM-DD 的核心矛盾：纯 NRZ 仅能贴近零色散波长 1290–1330 nm（Nokia Houtsma p22），GPON 共存要求约 120 ps/nm（1370 nm 处最坏 119.3 ps/nm，Huawei p89）。来自 Füllner、Houtsma、Kharbich、Cano 四讲。
2. 下行技术路线分化为 OLT 侧集中复杂度：VSB（Nokia，DD-MZM+延时，0–125 ps/nm <3 dB）、DCPC（预补偿，容限约翻倍，需 ONU 分组）、SSB/SSB+DCPC（Huawei，320 ps/nm，可到 1515 nm）。来自 Füllner、Cano、Kharbich。
3. 上行路线为 ONU 廉价 IM 发射 + OLT 相干接收：Houtsma 显示 ER 惩罚对相干接收机更严重，ER=6 dB 时 COH 与 OA-DD 需相近发射功率（约 +8.5 dBm@29 dB），相干的优势在色散全补偿与 C 波段共存；带宽受限 DD 实测反优于 COH（-28.7 vs -23.1 dBm，ER=8.5 dB）。
4. 相干/外差路线：Zaragoza 以简化偏振分集外差+LO 复用做到 200 Gb/s、25 km、32 dB 预算（DS -25 dBm 灵敏度），上行 20 Gb/s 不对称；说明相干 PON 在成本与 ONU 复杂度上仍受偏振管理、LO 与 ADC 制约。
5. 除色散外，MPI、DGD、SPM 是 DCPC 类方案的现实约束：MPI 抗性与常规 PAM-2 相近但残余 CD 加剧，DGD 需 ≤1/2 Ts（Kharbich p49）；高发射功率下 SPM 对 90 ps/nm 预补偿造成罚值（Cano p94）。
6. 标准背景：ITU-T G.Suppl.88（2025.10）已列三类候选（直检/相干/混合），多讲以其波长规划 WP-A/WP-B 为设计边界（Füllner、Cano、Zaragoza）。
