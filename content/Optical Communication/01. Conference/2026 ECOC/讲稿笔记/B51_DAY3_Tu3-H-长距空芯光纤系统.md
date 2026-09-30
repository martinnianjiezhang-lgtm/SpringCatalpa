---
title: "B51 · DAY3 · Tu3-H-长距空芯光纤系统"
tags:
  - ECOC2026
  - DAY3
---

### 0922-Tu3-H1-MicrosoftAzureFiber-空芯光纤传输系统从城域到长距.pdf
- 讲者/机构：Microsoft Azure Fiber（页内含 UCL Optical Networks 标识；讲者姓名题目页未核对，看不清） | 题目：HCF transmission systems from metro to long-haul（英文原题未逐字核对，据议程页"HCF-based metro transmission / multi-span and long-haul"概括） | 类型：邀请报告（Tu3-H 场首讲，综述性）
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI；次 2 Scale-across（400G ZR 延伸）
- 核心主张：
  1. HCF 已不是实验品："production-deployed, operationally proven, scaling using standard network practices"[p29]。
  2. 已在多个 Azure Region 承载客户实时业务，可靠性等同 SMF，至今无现场失效；未来 12 个月计划部署 12,000 km+[p29]。
  3. 传输实验从单跨（城域、BiDi）走向多跨与再循环环路长途；气体吸收线（GLA）是多跨/长途的主要约束[p17–p23]。
- 关键数据：
  - 纯硅芯光纤损耗记录约 0.14 dB/km（Sato OFC2024：0.1406 dB/km@1550 nm，0.1397 dB/km@1566 nm）；HCF（DNANF）0.091 dB/km（2025）；C 波段 <0.1 dB/km；提到某 HCF 0.032 dB/km（"Sunday workshop"报道）[p6]
  - 32 通道实时系统：150 GHz 间隔，最高约 138 Gbaud PS-QAM，最高 37 dBm 线路功率（1RU），301.7 km DNANF 链路、57 段（2–17.9 km/段），损耗 0.11–0.24 dB/km，熔接损耗 0.07–0.15 dB，IMI 约 -60 dB/km（200 km 链路）[p9]
  - 400G ZR、107.46 km HCF 缆，损耗约 29.7 dB，IMI < -56 dB/km；BiDi 同波长双向与单向相比 pre-FEC BER/OSNR 几乎无代价[p13–p14]
  - OESCL 同波长 BiDi：423.7 + 426.5 Tb/s，42.5 THz 带宽，60 km HCF；单方向速率与最高单向 SMF 速率相当（We2-D1）[p15]
  - 3 跨 real-time：32×800G，约 138 GBd PS-16QAM（熵 3.52 bit/符号），BA 34.5 dBm ×3，跨段 1&2 共 57 个盘纤、跨段 3 约 3 km + 4 km 缆；GLA 因子 0.03/0.05/0.07 dB/km（峰值处约 195.33 THz）；发射功率优化后各通道 Q 余量 >1.5 dB，pre-FEC BER 约 7×10^-3[p18–p20]
  - 全 C 波段 400G ZR 经 427.97 km HCF，对比此前 151 km 超低损 SMF 记录[p21]
  - 环路（Hong ECOC2025 Th.03.02.2）：1079.4 km 通道速率 1 Tb/s–500 Gb/s，2878.4 km 为 800–400 Gb/s，pre-FEC BER 均 <2.4×10^-2，速率由 GLA 程度决定[p23]；总速率：25.8 Tb/s@1439.2 km，20.6 Tb/s@2878.4 km，10.3 Tb/s@6116.6 km，4.8 Tb/s@7915.6 km，3.2 Tb/s@11153.8 km[p24，页面倒置]
  - 15 THz O 波段长途（We3-H3，单 BDFA）：61.5 Tb/s@1080 km，31.1 Tb/s@3000 km（360/660/1080/2160/3000 km 曲线，GS-64QAM/16QAM/QPSK）[p25]
- 提到的公司/客户/产品/标准：Microsoft Azure、Lumenisity/DNANF（Petrovich Nat. Photon. 2025）、University of Southampton（We3-H1）、UCL、400G ZR（OIF）、Nokia Bell Labs/Orange Labs 等引用的环路工作（引文列表）
- 与业界对比或记录声明（SOTA/首次/record）：427.97 km 400G ZR 为对比 151 km SMF 的"prior record" [p21]；O 波段单放大器系统"Record throughputs"61.5 Tb/s@1080 km [p25]；HCF 损耗低于任何已记录的硅光纤（1300 nm 与 1700 nm 处）[p6]
- 推荐配图页：p6（SMF 与 HCF 损耗记录对比曲线）；p24（环路总速率-距离，倒置需旋转）；p29（部署现状与 12,000 km+ 计划）

### 0922-Tu3-H2-NokiaBellLabs-低损低IMI空芯光纤C波段134GBd长距传输的气体吸收线影响.pdf
- 讲者/机构：R. Boddeda 等，Nokia Bell Labs（Paris-Saclay/New Providence）与 YOFC（武汉） | 题目：Impact of Gas Line Absorption in Long-Haul transmission of 134 GBd Signals in C-Band over Low Loss and Low IMI HCF [p1] | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途；次 1 oDSP（均衡器抽头、RRC）
- 核心主张：
  1. HCF 长途可降低中继器密度；挑战是 GLA 与模间干扰（IMI）[p14]。
  2. 单载波与多载波表现相近，只是大量子载波无法承受 GLA[p14]。
  3. 设计规则：即使有 GLA，">1T 在 1500 km 以内可行"[p14]。
- 关键数据：
  - GTA-ST-HCF（间隙管辅助支撑管 HCF）：估计 IMI -68.8 dB/km（对比常规 -52 dB/km）；损耗约 0.1 dB/km 量级（1530–1560 nm 曲线，色散约 4–5.2 ps/nm/km）[p4]
  - 环路实验：134 GBd CUT，满载 C 波段（约 4.8 THz），150 GHz 间隔，约 1330 km 谱；CUT A 193.538 THz 无 GLA，CUT B 195.488 THz 含约 3 条 GLA 线[p6]
  - CUT B，2128 km，10 dB 深陷波：16 子载波比 4 子载波损失约 10% 容量（4MC≈995 Gbps，16MC≈约 900 Gbps，读自曲线）[p9]
  - 单载波 CUT A：DP-64QAM 起点约 1350 Gbps；1000 km 内 >1.2T/载波（4 个中继）；2128 km 约 1.1T（DP-64QAM）、约 1T（DP-16QAM）；">1T over 2100 km with just 8 repeaters"[p11]
  - 单载波 CUT B（3 条 GLA 线）：>1T 至 1500 km 以外；2128 km 时 DP-16QAM 与 DP-64QAM 均约 930 Gbps；">900G feasible even in GLA over 2100 km"[p12]
  - 均衡器：RRC 0.06 时 <30 taps 在 1596 km 恢复 1 Tbps（DP-64QAM）；RRC 0.01 时仍 <40 taps；意味着可把 150 GHz 栅格压到 137.5 GHz 同时保持 1 Tbps（GLA 下）[p13，据 OCR 文本，未看图]
- 提到的公司/客户/产品/标准：Nokia Bell Labs、YOFC、引用 PDP OFC2026 Th4B.7（266 km 超长跨段 21.7 Tbps 净速率跨洋传输）、OFC2026 M2J.1（Peng Li，低 IMI 低损 HCF）
- 与业界对比或记录声明（SOTA/首次/record）：无本讲自身 record 声明；引用 PDP 的 21.7 Tbps、266 km 跨段成果 [p6]
- 推荐配图页：p6（满载谱与 CUT A/B 陷波位置）；p11（单载波容量-距离，>1T/2100 km）；p12（GLA 下 DP-16QAM/64QAM 收敛至 930 Gbps）

### 0922-Tu3-H3-UCL-C+L波段空芯光纤长距传输的气体吸收线影响.pdf
- 讲者/机构：Zelin Gan、Eric Sillekens、Jiaqian Yang、Ronit Sohanpal、M. Jarmolovičius、R. Aparecido、R. I. Killey、P. Bayvel，UCL Optical Networks Group [p1] | 题目：On the Impact of Gas-Line Absorption in Long-Haul C+L-Band Hollow-Core Fibre Transmission | 类型：学术论文（仿真）
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI；次 1 高波特率器件（带外L波段）
- 核心主张：
  1. GLA 强烈限制 L 波段 HCF 性能：理想抑制可达 59.1 Tb/s（约 1.5×，p22 页为 59.2 Tb/s）、1000 km 中继器少 3.3×[p23/p24]。
  2. GLA 抑制（如充气/吹扫）是释放未来 HCF C+L 系统全部潜力的关键[p24]。
  3. C 波段 GLA 影响相对有限[p15]。
- 关键数据（均为仿真）：
  - 仿真设定：294×32 GBaud，33 GHz 间隔；TRx SNR C 波段 23.5 dB、L 波段 22 dB；NF 5/5.5 dB；HCF 含 ASE、TRx、GLA、IMI（忽略 PMD 与非线性）；GLA 按 HITRAN Voigt/洛伦兹线型建模，0.2 bar、1000 ppm CO2，HWHM 约 0.5 GHz；HCF C 波段基线 0.07 dB/km，L 波段 0.65 dB/km，IMI -52 dB/km [p11–p12]
  - 单跨 1×100 km：SMF 最优发射功率 20/21 dBm（C/L），HCF 两波段均 27 dBm；GLA 吹扫（相对 1000 ppm CO2）：C 波段最大 SNR 增益 2.6 dB、吞吐增益 0.8 Tb/s（1.4%）；L 波段 4.9 dB、3.6 Tb/s（6.3%）[p14]
  - 1000 km SMF 参考（C/L，Tb/s；最优功率 dBm）：25 km 跨 49.7/56.7（15/16）；50 km 49.0/55.8（16.5/17.5）；100 km 42.2/48.1（20/21）；125 km 37.4/42.3（21.5/22.5）；200 km 19.8/21.7（26.5/27.5）[p15]
  - C 波段：HCF 在 100 km 跨、27 dBm、1000 ppm CO2 下比 SMF 多 3.4 Tb/s（8%），可减少 2.7× 中继器；400 ppm CO2 下多 4.2 Tb/s（10%）；理想 GLA 抑制下多 8.0 Tb/s（19%）[p15, p17, p18，后者据 OCR 文本]
  - L 波段：GLA 为主导限制；8×125 km 的 SMF 优于更短跨段 HCF（1000 ppm/400 ppm）即使提高发射功率；400 ppm CO2 下 HCF 增益 5.3 Tb/s（13%）；理想抑制下 L 波段平均增益 17.9 Tb/s，最大吞吐 59.2 Tb/s（约 1.5×），最多 3.3× 少中继器（27 dBm）[p20–p23]
  - GLA 缓解手段列举：接收端谱预均衡（Sillekens OFC2026 Th2A.50）、发射预加重（C. Li OFC2026 W2A.50）、谱避让、多载波与熵加载 OFDM（Sampaio ECOC2025；X. Wang Opt. Lett. 2025）[p5, p7]
- 提到的公司/客户/产品/标准：UCL、TRANSNET、HITRAN 数据库、DNANF（Petrovich Nat. Photon. 2025）
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；纯仿真对比 SMF。
- 推荐配图页：p23（C+L 吞吐-跨段长度，含 3.3×/1.5×/5.3 Tb/s 标注）；p14（GLA 对 SNR 谱的影响与吹扫增益表）；p24（结论）

### 0922-Tu3-H4-MicrosoftAzureFiber-全C波段400GZR经三跨段427.97km空芯光纤传输.pdf
- 讲者/机构：Y. Hong、B. Gholizadeh、J. Hooley、A. Ali、M. Kamalian-Kopae、C. Wallace、J. Gaudette、D.J. Richardson、B.J. Puttnam，Microsoft Azure Fiber（英国 Romsey）[p1] | 题目：Demonstration of Full C-band 400G ZR Transmission over 3-Span 427.97-km Hollow-Core Fibre [p1] | 类型：学术论文
- 方向归属（主/次）：主 2 Scale-across/ZR/ZR+；次 1 相干/长途/DCI
- 核心主张：
  1. 利用 HCF 超低非线性与低且平坦 CD，创下 400G ZR 最长传输记录：全 C 波段 64×400G，3 跨 427.97 km[p13]。
  2. GLA 是限制 400G ZR 进一步延伸的因素[p13]。
  3. 为超出城域距离使用 400G ZR 提供成本、能效与运维简化的新依据[p13]。
- 关键数据：
  - 400G ZR 对长途转发器：400G/λ vs 800G/λ；25.6T 需 64 vs 32 波；DP-16QAM vs PCS-QAM；约 60 GBaud vs 140+ GBaud；cFEC 限 1.25e-2 vs SD-FEC 2.4e-2；最大放大距离约 120 km vs 1000+ km；发射功率约 -10 dBm vs >0 dBm[p5]
  - HCF 论点：非线性低约 3 个数量级，可 >30 dBm 入纤；C 波段 <0.1 dB/km（对比 SMF 约 0.17 dB/km）；C 波段 CD 约 4 ps/nm/km（SMF 16–19）；ZR 模块功耗 DSP 占 49%，CD 补偿功耗随距离陡增[p8]
  - 实验链路：CUT 为 ONT+400G ZR（-10 dBm），63 路 ASE 假信道（60 GBaud，75 GHz 间隔）；最多 3 个 34.5 dBm HP-EDFA + 1 个 23.5 dBm 预放；3 跨：163.9 km（IL 32.4 dB，GLA 0.042 dB/km）、152.07 km（IL 30.5 dB，GLA 0.073 dB/km）、112 km（IL 27.8 dB，GLA 0.048 dB/km）；接收滤波带宽 75 GHz[p9]
  - 结果：1 跨（163.9 km）pre-FEC BER 略高于 1×10^-3，等效 OSNR 约 27 dB，GLA 可忽略；2 跨（315.97 km）在 GLA 频点附近 BER 升至接近 1E-2，OSNR 最低约 23 dB；3 跨（427.97 km）全通道 BER 低于 1.25×10^-2 FEC 限（GLA 处接近限）；GLA 深度在 3 跨后某些频段超过 20 dB[p10–p12]
  - 估计 CD：3 跨 427.97 km 后约 1,620–1,790 ps/nm，低于 OIF 规定的 2,400 ps/nm 上限[p12]
- 提到的公司/客户/产品/标准：Microsoft、400ZR（OIF IA，75/100 GHz DWDM，约 120 km 放大）、Nagarajan JLT 2021（ZR 功耗）
- 与业界对比或记录声明（SOTA/首次/record）："record-long reaches of 400G ZR"，对比此前 151 km 超低损 SMF（B. Zhu ECOC2021）与 107.5 km HCF（Hong OFC2026 M1B.4）[p4, p13]
- 推荐配图页：p5（ZR 与长途转发器对比表）；p8（SMF vs HCF 延伸 ZR 逻辑与功耗饼图）；p12（3 跨 BER/OSNR 与 CD 估计）

### 0922-Tu3-H5-华沙大学-功率受限多跨段传输的基本量子极限空芯对常规光纤.pdf
- 讲者/机构：Karol Łukanowski、Amirhossein Ghazisaeidi、Marcin Jarzyna、Konrad Banaszek，华沙大学 / Nokia Bell Labs / QOT 量子光学技术中心 [p1] | 题目：Fundamental Quantum Limits of Power-Constrained Multi-Span Fiber-Optic Transmission: HCF vs Conventional Fibers [p1] | 类型：学术论文（理论）
- 方向归属（主/次）：主 1 相干/海缆/长途；次 6 QKD/量子
- 核心主张：
  1. 量子增强只在较短链路可能；长链路不可避免的噪声迫使回到经典极限[p24]。
  2. HCF 相比硅光纤有"manyfold capacity gains"[p24]。
  3. 若能量预算分配到并行链路，相敏放大（PSA）总体优于相不敏放大（PIA）[p24]。
- 关键数据（理论/数值，跨段 ΔL = 50 km、每次使用输入 50 光子、单路 M=1 的示例）：
  - Shannon 与 Gordon-Holevo 容量对比：短链路无放大时有量子增益；短链路 HCF > 硅、PIA > PSA；长链路 PSA > PIA；长链路无量子增益（曲线在约 10^3 km 后汇合）[p18]
  - 参考 HCF 损耗：OFC2024 Th4A.8（Y. Chen）0.08 ± 0.03 dB/km 对比硅 SMF 0.14 dB/km（二十年）；论及"长期影响取决于规模化生产能力"，并预告 ECOC2026 workshop"Could 100s-km long unrepeatered HCF links redefine the economics..."[p9]
  - L = 5000 km 单路：交叉点约 10^2–10^3 光子/符号（硅约 5×10^2，HCF 约 1.5×10^2，读自曲线，粗略），低于该点 PSA>PIA，高于该点 PIA>PSA；功率轴按 300 GBaud C 波段 Tx 换算（-40 至 0 dBm）[p19]
  - 优化并行路径数 M：PSA > PIA，与跨段和光纤类型无关；HCF 总容量远高于硅；M 受限（M<256）时，PSA>PIA 只在一定总能量以下成立，跨段越短阈值越高，HCF 优势保持[p22, p23 OCR]
- 提到的公司/客户/产品/标准：Nokia Bell Labs、Gordon-Holevo 极限（Gordon 1962；Giovannetti Nat. Photon. 2014）、Łukanowski JLT 41(15) 2023
- 与业界对比或记录声明（SOTA/首次/record）：无实验 record；为理论容量优化。
- 推荐配图页：p18（Shannon vs Gordon-Holevo 容量-距离，四种配置）；p22（并行路径优化后 PSA > PIA 与 HCF 优势）；p24（结论）

## 本批小结
1. HCF 已从演示走向部署：Microsoft 称多个 Azure Region 承载实时业务、无现场失效、未来 12 个月计划 12,000 km+（H1 p29），并给出实时 32×800G 301.7 km、环路 3.2 Tb/s@11153.8 km、O 波段 61.5 Tb/s@1080 km 等谱系（H1）。
2. 气体吸收线（GLA）成为 HCF 长途/多跨段的共同瓶颈：H1 用 GLA 因子做功率优化，H2 表明 GLA 下仍可 >1T@1500 km、2128 km 约 930 Gbps，H3 仿真显示 L 波段尤其受限，H4 中 GLA 是 400G ZR 延伸的限制。四篇从系统、DSP、仿真、ZR 角度收敛到同一约束。
3. GLA 缓解路径分化：单载波或少子载波优于多子载波（H2 p9、p14）、接收预均衡/发射预加重/谱避让/熵加载 OFDM（H3 p5、p7）、气体吹扫降低 CO2（H3：400 ppm 时 C 波段多 4.2 Tb/s，理想 0 ppm 时 8.0 Tb/s；L 波段 5.3 Tb/s→17.9 Tb/s 平均增益）。
4. HCF 使可插拔相干（400G ZR）走出城域：427.97 km 全 C 波段（H4），CD 1,620–1,790 ps/nm 仍在 OIF 2,400 ps/nm 内；H1 亦有 107.46 km BiDi 400G ZR。这与 Scale-across/ZR+ 方向直接相关。
5. 降低 IMI 是长跨段的前提：Nokia/YOFC 的 GTA-ST-HCF 估计 IMI -68.8 dB/km，对比常规 -52 dB/km（H2 p4；H3 仿真采用 -52 dB/km）；H1 中 200 km 链路 IMI 约 -60 dB/km。
6. 理论视角（H5）：HCF 的极低损耗与非线性使功率受限链路容量显著高于硅纤，但量子增益只存在于短链路；与 H3 的"HCF 相对 SMF 获得 8–19%（C）/13%以上（L）"的定量结果互补。
