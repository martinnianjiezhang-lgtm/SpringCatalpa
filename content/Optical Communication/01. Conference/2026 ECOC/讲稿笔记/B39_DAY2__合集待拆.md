---
title: "B39 · DAY2 · _合集待拆"
tags:
  - ECOC2026
  - DAY2
---

说明：本批仅含1个PDF（Mo5-G 超高速PON连拍合集，共86页，多数页为重复页），按题目页/机构logo切分为5位讲者。共看图19张。未见到PoliTo与Huawei讲者的题目页，讲者姓名/原题按可见内容标注"未见"。

### 0921-合集待拆-全场-Mo5-G超高速PON连拍.pdf（第1–19页，Mo5-G1）
- 讲者/机构：Christoph Füllner（Nokia Bell Labs 固网部；合作者 Laurens Breyne, Wouter Lanneer, René Bonk）| 题目：Low-Complexity VSB Generation and Chirp Management for VHSP Downstream Links Supporting GPON Coexistence | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 3 调制器（DD-MZM）
- 核心主张：
  1. GPON共存使VHSP下行对色散容限要求升高，需要在成本敏感的PON中低复杂度地处理色散 [p4, p18]。
  2. 提出用DD-MZM + 简单模拟/数字延迟 + 偏置点选择产生VSB（残留边带）并管理啁啾，可用于较差的发射机，且下行无突发 [p18]。
  3. 100 Gb/s概念验证：0–125 ps/nm色散范围内惩罚<3 dB [p18]。
- 关键数据：
  - GPON与VHSP共存需要120 ps/nm的CD容限（20 km，波长计划WP-A无GPON共存 / WP-B有GPON共存）[p4]
  - 实验：100 GBd NRZ-OOK，DAC 100 GS/s，DD-MZM静态ER 12 dB，21抽头预补偿，OLT发射功率7 dBm，带SOA，边带抑制不完美 [p9]
  - 偏置在正交点（负斜率，α≈0.2）；DSB约40 ps/nm色散容限（3 dB惩罚）；数字延迟τ在约±15 ps范围扫描，延迟可在有CD时改善灵敏度，行为不对称（DD-MZM不完美所致）；测试色散点0/22/43/65/82/103/125/137 ps/nm；0 ps/nm时灵敏度约-24 dBm（AOP，图读数，精度有限）[p11]
  - 标题称概念验证最高到137 ps/nm；结论页给出0–125 ps/nm、<3 dB惩罚 [p9, p18]
  - 引言页：VHSP面向100/200 Gb/s服务速率，候选为相干PON(200G)或IM-DD PON（2波长×100G）；提及800G以太网可能是大批量驱动力；引用其JLT 2026已展示IM-DD 100 Gb/s服务速率 [p2, p3]
- 提到的公司/客户/产品/标准：Nokia Bell Labs；ITU-T VHSP supplement；GPON、XG(S)-PON、25GS-PON、50G-PON；EU共同资助 / VLAIO FALCON项目 [p1]
- 与业界对比或记录声明：无record声明；讲者称NRZ-OOK IM-DD仍是VHSP有吸引力的候选 [p3]
- 推荐配图页：p4（VHSP/GPON波长计划与20 km累积色散，得出120 ps/nm需求）；p11（延迟-灵敏度曲线，展示VSB效果）；p18（结论）

### 0921-合集待拆-全场-Mo5-G超高速PON连拍.pdf（第25–28页，Mo5-G2；第20–24页多为重复页，未逐页核对）
- 讲者/机构：Vincent Houtsma（Nokia Bell Labs）| 题目：On the Extinction Ratio penalty and Sensitivity of next-generation 120 Gb/s upstream IM solutions for Very High-Speed PONs | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 相干（相干接收作为灵敏度基准）
- 核心主张：
  1. 上行IM信号的接收灵敏度随消光比(ER)下降而显著劣化，需要评估真实ER下的代价 [p25]。
  2. 给出相干接收与直接检测(PIN、SOA-PIN、EDFA-PIN)在不同ER下的测量灵敏度曲线 [p28]。
  3. "现实检验"ER=6 dB下，120 Gb/s需要ONU平均发射功率至少+8.5 dBm才能满足29 dB光功率预算 [p28]。
- 关键数据：
  - 25 Gb/s NRZ相干检测：ER=24.5 dB时-41 dBm @BER=2e-2；对比BPSK -44.2 dBm、QPSK -42.5 dBm（25 GBd）；理论上ER→∞的NRZ灵敏度接近QPSK，比BPSK低3 dB [p25]
  - 120 Gb/s NRZ相干检测（带宽受限）：ER=8.5 dB时灵敏度-23.1 dBm @BER=2e-2；20 km SMF后光功率代价<0.4 dB（ER=7.5 dB曲线）；CD补偿在定时恢复之前做 [p26]
  - ER=6 dB时，120 Gb/s相干接收灵敏度-20.8 dBm @BER=2e-2；折算最低ONU平均发射功率+8.5 dBm（29 dB光功率预算，0.3 dB CD惩罚）[p28]
  - 对比接收机：32/64 GBd相干接收机、PIN(42 GHz)、SOA-filter-PIN(42 GHz)、EDFA-filter-PIN(42 GHz)；ER=6 dB 现实校验：120 Gb/s 相干接收灵敏度 −20.8 dBm（BER=2e-2），对应 29 dB 光预算（含 0.3 dB CD 代价）需 ONU 平均发射功率至少 +8.5 dBm（看图核实；各曲线逐点读数仍不精确）[p28]
- 提到的公司/客户/产品/标准：Nokia Bell Labs [p25]
- 与业界对比或记录声明：无record声明
- 推荐配图页：p28（各接收机灵敏度-ER曲线族）；p26（120 Gb/s相干BER曲线与星座）

### 0921-合集待拆-全场-Mo5-G超高速PON连拍.pdf（第31–48页）
- 讲者/机构：讲者姓名页面未显示（Politecnico di Torino，页眉logo）| 题目：未见完整原题；p31 看图核实为 Roadmap 页：DCPC（Digital Chromatic Dispersion Pre-Compensation）用于VHSP，含C波段MPI容限与O波段120 GBd可扩展性（含MPI与DGD）评估，引用 ITU-T G Suppl. 88 (10/2025) | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 oDSP
- 核心主张：
  1. 将色散补偿移到OLT，用数字预补偿(DCPC)，保持ONU为低成本直接检测接收机 [p32–33]。
  2. 50 GBd实验证明：完全CD预补偿时，DCPC-PAM2的MPI容限与标准PAM2相近；残留CD越大，MPI惩罚越高 [p44, p48]。
  3. 数值模型与实验吻合，外推到120 GBd上O波段VHSP：DCPC-PAM2在MPI和DGD下仍可行，前提是色散匹配精确 [p48]。
- 关键数据：
  - 实验：PAM-2，50 GBd，TOP=11 dBm，20 km SMF，D=17 ps/nm/km，L_DCPC=L_fiber；FIR 100抽头、FFE 100抽头；最坏偏振（信号与干扰同偏振）[p39, p38]
  - MPI：L_DCPC取1、3/4、1/2倍光纤长度，惩罚随SIR降低而升高，SIR约15 dB以下明显（BER目标1e-2与2e-2两组）[p44]
  - 120 GBd：PAM-2，TOP=11 dBm，λ_ZD=1310 nm，D=5.96 ps/nm/km，色散斜率=0，BER目标2e-2，Ts=8.3 ps；DGD惩罚等高线图：DGD/Ts≲0.5时惩罚<1 dB（CD在约20–48 ps/nm间），DGD接近符号周期惩罚显著 [p47, p48]
  - 120 GBd MPI：显著惩罚主要出现在SIR<15 dB [p48]
  - 文中另有"C-band 50 GBd实验作为CD对等验证"的说明 [p35]
- 提到的公司/客户/产品/标准：ITU-T G Suppl. 88 (10/2025)（50 Gbit/s以上PON要求与技术）[p31]；G.652 [p35]
- 与业界对比或记录声明：无record声明
- 推荐配图页：p47（120 GBd下CD与DGD联合惩罚等高线）；p44（残留CD对MPI容限的影响）；p48（结论）

### 0921-合集待拆-全场-Mo5-G超高速PON连拍.pdf（第49–65页）
- 讲者/机构：David Izquierdo, Natalia Herguedas, Pascual Sevillano, Ramón Cajal-Pérez, Ignacio Garcés（University of Zaragoza, I3A / Photonics Technology Group）| 题目：200 Gb/s PolMux Link with 32 dB optical power budget, 28GHz electrical bandwidth and LO reuse for VHS-PONs | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 相干
- 核心主张：
  1. 提出简化相干（外差）方案：下行用OSSB MultiCAP的相位调制，可PolMux使速率翻倍；ONU用偏振分集的简化相干接收机（1个PBS、1个PM耦合器、2个PD+TIA），可用InP或SiP集成 [p53, p56]。
  2. 上行复用下行的LO（LO reuse）；下行与上行可放入一个100 GHz DWDM通道 [p61]。
  3. 在25 km链路实现约32 dB级光功率预算 [p63, p65]。
- 关键数据：
  - 背景：VHS-PON需要32–35 dB光功率预算，20–30 km链路，倾向IM/DD但需DSP [p50]
  - 下行(DS)：灵敏度-25 dBm；发射+7 dBm对应32 dB光功率预算；SD-LDPC FEC阈值；-20 dBm接收功率以下存在明显误码平层，25 km光纤后平层升高（约3e-3到4e-3，图读数）[p63]
  - DS开/关上行时灵敏度不受影响，平层随注入光纤的功率升高 [p64]
  - 上行(US)：HD-LDPC FEC下灵敏度-31.5 dBm，对应33或38 dB OPB；以太网FEC限下-26 dBm，对应27.5或32.5 dB OPB；未见平层；开启下行通道时惩罚<1 dB（以太网FEC处）（看图核实）[p65]
  - DS的MultiCAP带：另用两条5 GHz的DSB MultiCAP 4QAM带做20 Gbps上行概念验证；下行50 Gbps MultiCAP IM信号另有海报We4-P81 [p61]
  - 实验：120 GSa/s AWG，128 GSa/s DSO，电带宽标题为28 GHz [p49, p62, p63]
  - 标题中的200 Gb/s为PolMux总速率，DS逐项分解看不清
- 提到的公司/客户/产品/标准：FSAN路线图、ITU-T VHSP（Zhang/Liu/Nesset, JOCN 2026）[p50]；Kovacs/Faruk/Savory简化相干ONU [p52]
- 与业界对比或记录声明：无record声明
- 推荐配图页：p65（上行BER-接收功率，含33/38 dB OPB）；p63（下行BER与平层）；p53（方案概览）

### 0921-合集待拆-全场-Mo5-G超高速PON连拍.pdf（第68–85页）
- 讲者/机构：讲者姓名页面未显示（Huawei，页脚logo）| 题目：未见原题；p68 看图核实为 "Introduction: IM-DD and Coherent"（引 Acacia OFC 2022 IMDD vs Coherent 距离-速率图与 FSAN Optical Access Roadmap 3.0）；内容为VHSP各技术路线的色散处理对比（ODB、DCPC、SSB、SSB+DCPC）| 类型：邀请报告/学术论文（无法确认）
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 oDSP
- 核心主张：
  1. ITU-T VHSP supplement（2025年10月发布）覆盖>50 Gb/s PON，含直接检测、相干、IMDD-相干混合三类技术 [p72]。
  2. 1370 nm运行需120 ps/nm色散容限（20 km G.652最坏累积CD 119.3 ps/nm），ODB与单组DCPC均不足 [p78, p82]。
  3. SSB（单边带）仿真在120 ps/nm仅<1.5 dB惩罚且无需ONU分组，可支持C波段 [p84, p85]。
- 关键数据（均为仿真）：
  - ODB：3 dB OPP处CD容限约44 ps/nm，优于NRZ；DCPC约90 ps/nm；加第二个预补偿值(两组DCPC，35与90 ps/nm)可到120 ps/nm；计入SPM（Tx +14 dBm）时90 ps/nm预补偿情形出现代价，120 ps/nm仍有余量 [p82]
  - 两组分组可简化控制算法，降低ONU在其组未被发送时失同步的风险 [p82]
  - SSB：120 ps/nm处惩罚<1.5 dB；3 dB惩罚下最大CD容限320 ps/nm，可支持1515 nm、20 km最坏CD；仅13抽头FFE在120 ps/nm仍<2 dB [p84]
  - SSB+DCPC(预补偿150 ps/nm)：惩罚曲线更平，相对SSB多约1.5 dB（Tx电信号PAPR更高）；总惩罚3.5 dB时C波段可行；计入SPM约有0.5 dB改善（CD<325 ps/nm），此后惩罚上升 [p85]
  - 背景页：FSAN Optical Access Roadmap 3.0，IMDD vs 相干（引自Acacia OFC 2022）[p68]
- 提到的公司/客户/产品/标准：Huawei；ITU-T G.9804.3、G.Suppl.88 clause 8.1/8.2/8.3/8.4.7；50G-PON、XG(S)-PON、GPON；FSAN；Acacia [p68, p72, p78]
- 与业界对比或记录声明：无record声明
- 推荐配图页：p85（SSB+DCPC使C波段可行）；p84（SSB容限320 ps/nm）；p82（ODB/DCPC对比）

## 本批小结
1. VHSP（100–200 Gb/s PON）的核心矛盾是色散容限：GPON共存需120 ps/nm（20 km、约1370 nm，最坏119.3 ps/nm）。Nokia用VSB（DD-MZM + 延迟 + 偏置点）、PoliTo用OLT数字预补偿DCPC、Huawei比较ODB/DCPC/SSB，三者都是把复杂度放在OLT，保持ONU低成本（来自Nokia G1、PoliTo、Huawei）。
2. 各方案色散容限对比：DSB约40 ps/nm；Nokia VSB实验0–125 ps/nm（<3 dB）；Huawei仿真ODB约44、DCPC约90、双组DCPC 120、SSB 320 ps/nm，SSB还可使C波段运行可行（Nokia G1、Huawei）。
3. DCPC的代价在于对色散匹配精度敏感：残留CD增加MPI惩罚，DGD须<约1/2符号周期才保证<1 dB惩罚（PoliTo）。
4. 上行方面，ER是关键：Nokia G2显示ER=6 dB时120 Gb/s需+8.5 dBm的ONU发射功率（29 dB预算），相干接收可提供更好灵敏度（-20.8 dBm @6 dB ER，-23.1 dBm @8.5 dB ER）；Zaragoza则走相干外差/LO复用，上行在HD-LDPC下-31.5 dBm（Nokia G2、Zaragoza）。
5. 相干PON与IM-DD之争在PON复现了数据中心的路线之争，ITU-T supplement同时列出三类候选，尚无定论（Huawei p72、Zaragoza p50、Nokia G1 p2）。
