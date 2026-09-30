---
title: "B74 · DAY5 · PDP-A-后期论文A1厅"
tags:
  - ECOC2026
  - DAY5
---

### 0924-PDP-A-1-Microsoft与南安普顿大学-C波段电信级损耗零色散空芯光纤首次验证.pdf
- 讲者/机构：S. M. A. Mousavi 等（通讯 F. Poletti）；Microsoft Azure Fiber（Romsey, UK）/ 南安普顿大学 ORC | 题目：First Demonstration of a Zero-Dispersion Hollow-Core Fibre with Telecoms-Grade Loss (0.2 dB/km), in the C-Band | 类型：学术论文（PDP，后期论文）
- 方向归属（主/次）：主 1（相干/海缆/长途/DCI/AI光网络/高波特率器件中的新型光纤）；次 3（IM-DD 短距，PAM4）
- 核心主张：
  1. 首次在 C 波段实现零色散空芯光纤且损耗保持电信级（约 0.2 dB/km，HF-3 与 HF-5）。
  2. 仅调一个设计旋钮——外层管壁厚度（1.18→1.31 µm），D 在约 1.29 µm 处过零，无需新工艺；纤芯 26 µm（涂覆后 300 µm），适合高密度光缆。
  3. 零色散使 IM-DD（PAM4）传输距离/误码显著改善并有望省成本；对传感、计量、授时、量子网络也有潜力。
- 关键数据：
  - 常规 HCF 色散约 2.5–5 ps/nm/km，SMF 约 17 ps/nm/km；100 km SMF 累积 CD 约 1,700 ps/nm [p3–p4]
  - 第一窗口设计强行搬 ZDW 到 C 波段损耗约 0.10→0.39 dB/km（约 4 倍代价）；第二窗口 0.16→0.34 dB/km；混合窗口（Hybrid DNANF，OFC26 Th4B.8 提出）0.13→0.16 dB/km [p8–p11，OCR]
  - HF-2：t≈1.25 µm，37.1 km，色散降 50%，损耗 0.1 dB/km @1.55 µm；色散斜率 0.050 ps/nm²/km [p18]
  - HF-4：t≈1.28 µm，15.0 km，C 波段内过零（约 1533 nm 附近），1.55 µm 处损耗 0.196 dB/km（最小 0.175 dB/km），斜率 0.063 ps/nm²/km，与 SMF 斜率相当 [p18]
  - HF-5：t≈1.29 µm，14.9 km，1550 nm 附近零色散，1.55 µm 处 0.23 dB/km（最小 0.22 dB/km），斜率 0.090 ps/nm²/km [p18]
  - 六根新纤 HF-1…HF-6 长度 10.0–37.1 km；参考纤 HF-ref t=1.18 µm 色散约 +5 ps/nm/km，损耗约 0.1 dB/km [p15–p16]
  - 系统实验：56 GBd（112 Gb/s）PAM4，约 15 km，1530–1570 nm，IM+PD+示波器；HF-5 BER 约 2–4×10⁻⁴，HCF 约 2–4×10⁻³，SMF 约 3×10⁻¹；即比标准 HCF 低约一个数量级，比 SMF 低数个数量级 [p20]
  - 展望（仿真，非实测）：30 µm 纤芯，1550 nm 损耗 0.057 dB/km，色散 +3.98 ps/nm/km，斜率 +0.013 ps/nm²/km，外管壁厚 1.11 µm——该设计尚未过零；讲者结论称更大纤芯可在保持零色散下达约 0.1 dB/km [p21，p23 OCR]
- 提到的公司/客户/产品/标准：Microsoft Azure Fiber、南安普顿大学 ORC；参考文献含 Petrovich Nat. Photon. 2025、Ding ECOC 2025；DNANF/混合 DNANF 结构；引用 DSP 占收发器功耗 40–60%（相干）、零色散最多降约 30% 功耗（OCR，p4，看不清细节）
- 与业界对比或记录声明：标题即"First demonstration"零色散 HCF 且电信级损耗 [p1, p23]；空芯光纤损耗现状 <0.1 / 0.05 / 0.03 dB/km 的对比见 [p2]
- 推荐配图页：p18（三根光纤的测量色散曲线+损耗谱+截面，最核心）；p20（IM-DD BER 对比+眼图）；p16（壁厚—色散/损耗设计定律）

### 0924-PDP-A-2-MicrosoftAzureFiber-TFLN调制器与增益平坦YDFA及低损空芯光纤的1um相干传输系统.pdf
- 讲者/机构：Y. Hong 等；Microsoft Azure Fiber / Amonics / Nokia Bell Labs（Stuttgart、New Providence） | 题目：A Coherent 1µm Transmission System using TFLN Modulator, Gain-Flattened YDFAs and Low-Loss Hollow-Core Fibre | 类型：学术论文（PDP）
- 方向归属（主/次）：主 1（新波段/空芯光纤长途相干）；次 3（TFLN 调制器、新波段器件）
- 核心主张：
  1. 首个使用记录低损 1 µm 波段空芯光纤、增益平坦 YDFA 和 TFLN 调制器的全相干城域级系统。
  2. 单个放大器系统带宽可超过 C+L 合并带宽（>2.5×C 波段），释放 YDFA 的数据承载潜力。
  3. 未见气体吸收损伤；受限因素是可调激光器范围与器件生态，而非 HCF/YDFA。
- 关键数据：
  - 106.1 km 链路，244×32 GBd DP-PS-16QAM，50 GHz 间隔，覆盖 45 nm / 12.15 THz，GMI 估计总吞吐约 53.3 Tb/s [p6, p14]
  - 1 µm HCF：第二反谐振窗口（膜厚约 750 nm），9 段纤（纤芯约 25–26 µm）拼成 106.1 km，1060 nm 处链路损耗约 19.6 dB；多段最小损耗约 0.08 dB/km（1–1.1 µm），约 930–1130 nm（约 57 THz）损耗低于 0.2 dB/km [p9]
  - 传输结果：波长 >约 1050 nm 时 AIR 约 220 Gb/s/通道、SNR 约 12.5 dB；1030 nm 附近降到约 180 Gb/s、约 9 dB，归因于 BPD 响应度滚降与调制器偏置稳定性 [p13]
  - YDFA 两级+中间增益平坦滤波，1030–1080 nm 增益较平，NF <5 dB；booster 发射功率设为 25 dBm（每通道略高于 1 dBm）[p11，OCR]
  - TFLN IQ-MZM（商用平台，350 nm LN 膜/硅）：3 dB EO 带宽超过 110 GHz 测量极限，但封装 Si RF 中介层限制封装带宽 <20 GHz；1 µm 下 Pockels 相移比 1550 nm 约强 50% [p10，OCR]
  - 可扩展：放大器输出可达 36 dBm，文献有 100 W 放大器 [p13]
  - 对比：此前 1 µm 最高为 7.12 Tb/s MDM 传输 20.5 km G.652（31 通道×24.5 GBd×3 模，Aparecido, SPPCom 2026）；多为 VCSEL/强度调制、数 km [p6]
  - 讲者提及 Sunday Workshop 上报道的 HCF 损耗 0.032 dB/km（C 波段）[p7，OCR]
- 提到的公司/客户/产品/标准：Microsoft、Amonics（YDFA）、Nokia Bell Labs；DNANF；HITRAN 气体吸收数据库；生态短板：WSS、环形器等 1 µm 电信级器件缺乏
- 与业界对比或记录声明：自称"first full coherent metro-scale system utilizing a record-low-loss 1 µm HCF"；53.3 Tb/s@106.1 km 对比此前 7.12 Tb/s@20.5 km [p6, p14]
- 推荐配图页：p6（1 µm 历史工作与本工作的容量-距离散点）；p9（1 µm HCF 9 段纤损耗谱）；p13（AIR/SNR 随波长）

### 0924-PDP-A-3-NokiaBellLabs与ASN与长飞-532公里空芯光纤全C波段无中继传输带ROPA达30.66Tbps.pdf
- 讲者/机构：Haïk Mardoyan 等；Nokia Bell Labs（Massy）/ Alcatel Submarine Networks / YOFC（长飞，武汉） | 题目：Record Full-C band Unrepeatered Transmission over 532-km HCF achieving 30.66-Tb/s with ROPA and 15.73-Tb/s without ROPA | 类型：学术论文（PDP-A-3，2026-09-24 14:30）
- 方向归属（主/次）：主 1（长途/海缆无中继）；次 4（不属于；备注：与 AI 基础设施关联仅在 HCF 优势总结页 p12，OCR 不清）——次方向留空
- 核心主张：
  1. 首次在 532 km HCF 上完成完整 C 波段无中继 WDM 传输，使用高功率 EYDFA booster。
  2. 记录净吞吐：有 ROPA 30.66 Tb/s，无 ROPA 15.73 Tb/s。
  3. HCF 的低损耗同时惠及信号传播与远端泵浦，是超长无中继链路的关键使能（陆地、海缆、远程连接）。
- 关键数据：
  - 光纤：YOFC GTA-ST-HCF，1550 nm 损耗 0.032±0.003 dB/km（45.26 km）；纤芯 29 µm，包层 230 µm，涂覆 370 µm（OCR）；IMI −63.6 dB/km（OCR）[p10–p11]
  - 链路：2×266 km GTA-ST-HCF = 532 km，总跨段损耗 57.2 dB；266 km 处斜率 −0.098 dB/km（OCR）[p15, p17]
  - SMF/HCF 接口反射串扰抑制：两个声光调制器（AOM）交替切换，约 1.7 ms 后信号进入 HCF 时切换，接收端在 CUT 停发后采集 532 km 传播信号；反射通常约 −50 dB 量级会淹没 57.2 dB 跨损后的回波 [p17]
  - 发射：256 GS/s DAC（3 dB @ 75 GHz），EYDFA（铒镱共掺）booster，ASE 噪声加载 [p13–p14]
  - 无 ROPA：35 通道 PDM-QPSK，净总容量 15.73 Tb/s；每通道净速率约 415–470 Gb/s，频段 191.3–196.3 THz [p18]
  - 有 ROPA：37 通道 PDM-16QAM，净总容量 30.66 Tb/s；每通道约 660–900 Gb/s，频段 191.1–196.1 THz [p22]
  - ROPA：到达 ROPA 的信号约 −15 dBm；泵浦 24–34.77 dBm（光纤端），泵浦路径含复用器与环形器约 15 dB 损耗；泵浦波长 1485 nm（OCR，p21）[p20]
  - 泵浦功率降低 10 倍（约 34.8→24 dBm），平均仅损失约 10.15% 容量（191.25/193.59/195.65 THz 三通道）[p23]
  - 对比 SOTA（仅 C 波段无中继）：此前最高约 407 km（ref [12] Busson，32 Tb/s PCS-16QAM，实时）；本工作距离提高 120+ km（+30.7%）[p24–p25]
  - 单信道更长距离先例：ref[16] Feng OFC 2026 M2C.3 HCF 上 400G/800G/1.2T 分别 726.1/611.9/436.1 km（仅 EDFA）；ref[8] Qiu 746.69 km（100G）[p24]
  - 背景：Sumitomo 硅芯纤 0.1397 dB/km（1566 nm）/ 0.1406 dB/km（1550 nm），39 年仅降 0.015 dB/km；HCF 记录轨迹 DNANF 0.11（OFC24）→ Linfiber 0.052（ECOC25）→ 本纤 0.032 dB/km [p8, p10]
- 提到的公司/客户/产品/标准：Nokia Bell Labs、ASN、YOFC GTA-ST-HCF、Linfiber、Microsoft/南安普顿 DNANF、Sumitomo；ROPA（远端光泵浦放大）；PDM-QPSK/16QAM
- 与业界对比或记录声明：标题与 p25 结论页声称记录净吞吐及完整 C 波段无中继 532 km 首次；"improves the SoA by more than 120 km in reach (30.7% increase)"；"500+ km with HCF is possible with or without ROPA, which may significantly alter the performance baseline compared to SMF" [p24, p25]
- 推荐配图页：p24（无中继 SOTA 容量-距离对比）；p22（30.66 Tb/s 逐通道容量）；p17（AOM 抑制适配器串扰的方案）；p10（HCF 损耗历史曲线）

### 0924-PDP-A-4-Microsoft与Lightera与UCL-缩小外径宽带空芯光纤的双波段双向长距传输-另一版.pdf
- 讲者/机构：J. Yang 等；UCL Optical Networks / Microsoft Azure Fiber / Lightera | 题目：Dual-Band, Bi-Directional Long-Haul Transmission in Reduced Outer Diameter Wideband HCF | 类型：学术论文（PDP-A-4，2026-09-24；本PDF为"另一版"，多页重复）
- 方向归属（主/次）：主 1（海缆/长途）；次 4（不适用，留空）
- 核心主张：
  1. 首次长距离双向光纤传输：13 THz O+C 波段，并行双向再循环环。
  2. 缩小外径（约 190 µm）宽带 HCF 提升空间密度，回应"HCF 外径 >240 µm 导致缆内芯数受限"的问题。
  3. 双波段双向 AR-HCF 可把低时延带入长途链路，并在空间受限场景支撑高数据率。
- 关键数据：
  - 链路：112.5 km（5 段拼接），纤芯 25 µm，光纤面积小 38%；1550 nm：截断法损耗 0.16 dB/km，跨段损耗 25 dB，背向反射 −59 dB，IMI <−60 dB；1310 nm：0.20 dB/km，30 dB，−60 dB，<−55 dB；CO₂ 吸收 0.025–0.09 dB/km（平均 0.05 dB/km）[p10]
  - 2024 km O+C 双向：O 波段前向 22.7 Tb/s、后向 22.9 Tb/s；C 波段前向 29.2 Tb/s、后向 31.0 Tb/s；GMI 合计 51.9 Tb/s（FW）+ 53.9 Tb/s（BW）；解码 47.3 + 49.7 Tb/s [p14]
  - 调制格式：O 波段 QPSK，C 波段气体吸收线（GLA）受影响信道用 16QAM，其余 64QAM；O 波段约 100 Gb/s/通道，C 波段 150–250 Gb/s/通道 [p14]
  - 4500 km C 波段双向（拆除 O/C WDM 耦合器降损耗）：GMI 21.5 + 22.2 Tb/s，通道 100–200 Gb/s；6750 km：16.6 + 17.2 Tb/s，GLA 影响信道 <100 Gb/s [p15]
  - DSP/系统（OCR）：32 GBd，101 抽头导频/41 抽头盲 DD-LMS，GLA 补偿/频谱平坦化算法；34 dBm 高功率 booster，31 dBm 高功率 BDFA；AOM 零频移 [p12–p13，OCR，未逐项核对]
  - ASN 在 ECOC 2026 Workshop 的引述（p9）："6000 km: HCF can reduce the energy per bit by 2x and potentially double capacity. However, spatial constraints prevent translating this fibre-advantage into the same system-level gain." [p9]
- 提到的公司/客户/产品/标准：Microsoft、UCL、Lightera；铋掺杂光纤放大器（BDFA，O 波段）；EDFA；对比文献 Ali OFC25、Feng OFC26、Hong ECOC25、Boddeda OFC26 Th4B.7、Zhang CLEO26、Han Opt. Express 35（2026）、Yang ECOC26 We2-D1、Mardoyan ECOC26 We3-H2
- 与业界对比或记录声明：自称 "First long-distance bi-directional optical fibre transmission"；p9 散点图显示本工作 2024 km 双向聚合约 100+ Tb/s，高于 [6][7][8][9] 的重复传输结果 [p9, p16]
- 推荐配图页：p9（空间效率论点+容量-距离总览图）；p14（2024 km O+C 逐通道数据率）；p10（链路特性表）

### 0924-PDP-A-5-NokiaBellLabs-450GBaud全电子IQ信号实现3.83Tbps单波长相干传输.pdf
- 讲者/机构：Di Che、Xi Chen、Callum Deakin、Gregory Raybon、Kwangwoong Kim、Ellis Burrows；Nokia Bell Labs（Murray Hill, NJ） | 题目：3.83-Tb/s Single-Wavelength Coherent Transmission Enabled by 450-GBaud All-Electronic I/Q Signaling | 类型：学术论文（PDP-A-5）
- 方向归属（主/次）：主 1（高波特率相干/oDSP/器件）；次 3（TFLN 调制器、超高带宽电芯片/DAC）
- 核心主张：
  1. 用全电子复用（DBI-DAC）产生 450 GBd I/Q 信号，单波长净速率 3.83 Tb/s。
  2. 相干产业靠提升波特率驱动速率增长，实验室领先量产的时间在缩短（同等速率约 7 年@800G → 约 4 年@1.6T）；建议现在就测试 200 GHz 级 E/O、O/E 器件，"不要等 CMOS"。
  3. 电复用决定每波长速率、光复用填满频带；一个封装内的全 C 波段相干收发器（4.8 THz）是长期方向。
- 关键数据：
  - 450 GBd 需要约 225 GHz 带宽，"no device reaches it" [p8]
  - 3.83 Tb/s：PS 64-QAM，熵 5.3 bit/符号，450 GBd，B2B；SNR X/Y = 13.95/13.88 dB；NGMI 0.8795/0.8768，软判决 FEC 阈值 NGMI 0.8714；10 km SSMF 点约 0.873（图示，略高于阈值）；发射信号约 226 GHz×2 频谱切片 [p13]
  - 发射机：TFLN I/Q 调制器，2 cm 电极，6 dB 带宽 >110 GHz，Vπ=2 V @2 GHz（OCR）[p9]
  - 接收机：OAWM（光学任意波形测量）——375 GHz PM 梳，两根相距 225 GHz 的线作 LO；两个相干接收机 256 GSa/s、113 GHz 各；偏振用 TDM 检测（4 µs 开关、PBS、400 m 延迟），PDM 用 10 m 仿真器；10 km SSMF [p10，OCR]
  - DSP：widely-linear 8×2 MIMO（校正 I/Q 时偏与频响、两个频谱切片拼接、镜像抑制、偏振解复用），三阶 Volterra 均衡（记忆 385/25/13 抽头）；DBI-DAC 非线性；离线处理 [p12，OCR]
  - 历史记录：2.42 Tb/s（ECOC'23）、2.52 Tb/s（ECOC'25，约 250 GBd）；OFC 2025 PDP 440 GBd 1-D ASK 单维 1.04 Tb/s（PS-16ASK，3.4 bit/符号）[p8]
  - 功耗趋势：模块功耗/100G 随 CMOS 节点下降；全 C 波段 25.6 Tb/s 收发器功耗 95–180 W；可用 10×450 GBd 替代 32×800ZR（118 GBd）覆盖 4.8 THz（OIF 800ZR 栅格）[p14, p15；p14 OCR]
  - 结构提议：Si₃N₄ 微谐振腔梳 + 片上铒放大器（EDWA）→ 解复用 → 10 个 I/Q 调制器 → 复用 → EDWA booster，一个封装 [p15]
- 提到的公司/客户/产品/标准：Nokia Bell Labs；400ZR/800ZR/1600ZR（OIF）；CFP/CFP2-DCO；100G 5×7" MSA；IEEE 802.3df；光频梳（OAWG/OAWM）；Yamazaki JLT 2024 单载波 CSRZ-OTDM InP 芯片 2.5 Tb/s（OCR，p4，看不清）
- 与业界对比或记录声明：图示标为 "this work" 3.83 Tb/s，高于此前单波长相干 ≥1.6 Tb/s 记录（最高 2.52 Tb/s）[p8]；同一团队早先 440 GBd 1-D ASK 为单维记录 [p8]
- 推荐配图页：p8（单波长速率 vs 波特率，含 3.83 Tb/s）；p13（3.83 Tb/s 频谱/星座/NGMI）；p7（实验室领先时间缩短曲线）；p15（10×450 GBd 全 C 波段封装愿景）

### 0924-PDP-A-6-NokiaBellLabs与上海科技大学-440GBaudPAM单光电二极管接收实现每通道净比特率超800Gbps.pdf
- 讲者/机构：Di Che 等（Xi Chen、Callum Deakin、Gregory Raybon、Kwangwoong Kim、Stefano Ghillandi、Linze Li、Tianyu Long、Baile Chen）；Nokia Bell Labs（Murray Hill）/ 上海科技大学 | 题目：IM-DD Net Bit Rate Beyond 800 Gb/s per Lane with Single-Photodiode Reception of 440-GBaud PAM | 类型：学术论文（PDP-A-6）；本页图片 p1 为倒置拍摄
- 方向归属（主/次）：主 3（Scale-out 448G/800G/lane、光电二极管、调制器、电芯片）；次 4（scale-up 短距 IM-DD 与 coherent-lite 对比）
- 核心主张：
  1. 单个调制器+单个光电二极管接收，440 GBd PS PAM-6（H=2.4）净速率 826.6 Gb/s，超过 800G/lane。
  2. 接收侧关键：约 200 GHz 级 MUTC 光电二极管与三频带 DBI-ADC（用 180 GHz 示波器获得 221 GHz 带宽）。
  3. 色散限制：440 GBd 下 C 波段 SSMF 只能到数十米；O 波段近零色散可延长；高速率 IM-DD 越来越需要强均衡与编码，coherent-lite 可能与之竞争，而"慢而宽"IM-DD 服务米级 scale-up。
- 关键数据：
  - 净速率公式：440×[2.4 − (1−0.8262)×3] = 826.6 Gb/s（PS PAM-6 标在 PAM-8 字母表上，3 bit/符号），使用码率 0.8262 的 SC-LDPC+BCH，NGMI 阈值 0.8714 [p8]
  - 均匀 PAM-4：BER 0.0225，NGMI 0.9143；PS PAM-6（H=2.4）：BER 0.0331，NGMI 0.8785；眼图单符号宽 2.27 ps [p8]
  - 此前 IM-DD 最高：NTT 248 GBd、660 Gb/s 净（ECOC 2025）；440 GBd ASK/相干（Nokia OFC 2025）需 LO，非 IM-DD [p2]
  - 发射：Keysight 256 GSa/s AWG + DBI-DAC（频带 DC–90/90–130/130–175/175–221 GHz，含 87/128/222 GHz 上变频），1550 nm，薄膜 LiNbO₃ MZM，EDFA；接收：PD+偏置器，DBI-ADC（DC–130、130–180、180–221 GHz），512 GSa/s（180 GHz）实时示波器；光谱宽度 441.8 GHz（440×1.004）[p7]
  - MUTC 光电二极管（引用上海科技大学 Nat. Photon. 19, 1301 (2025)）：206 GHz、0.81 A/W，BEP 数值看不清；本实验器件约 190 GHz、0.46 A/W（含耦合，5 mA）[p5，OCR]
  - 色散反射（OCR，p9）：C 波段 SSMF 826.6 Gb/s 可到约 30 m，50 m 处约 0.7 dB SNR 代价；预测 3 dB 衰落距离：C 波段 SSMF（17 ps/nm/km）约 38 m，HCF（约 3 ps/nm/km）约 200 m，O 波段 SSMF（|D|≈1 ps/nm/km）约 0.9 km（OCR，未核对），O 波段近零色散可达数 km [p9]
  - scale-up 场景：10–50 m，数百条 2–32 Gb/s 通道，microLED/无 DSP/无 FEC，约 10 ns 延迟/芯粒，<1 pJ/bit；举例 Avicena、Ayar Labs、Intel OCI [p11，OCR]
  - coherent-lite：Zhao OFC 2025 硅光收发器 925 Gb/s 净（1.12 Tb/s 线速率），无 Rx 激光器，10 km HCF 上锁定 Tx 激光；偏振手动跟踪，CDR 数字仿真 [p12，OCR]
- 提到的公司/客户/产品/标准：Nokia Bell Labs、上海科技大学、Keysight、NTT（对比）、Avicena/Ayar Labs/Intel OCI（scale-up 举例）；IEEE P802.3df；LR4 IM-DD vs LR coh-lite
- 与业界对比或记录声明：827 Gb/s（页面写法）为 IM-DD 单通道最高，此前最高 660 Gb/s 净（NTT，248 GBd）[p2]；讲者指出瓶颈在接收机（PD & ADC），因为直接检测无法光学拼接频谱 [p2]
- 推荐配图页：p2（IM-DD 速率 vs 波特率总览，标出 827 Gb/s）；p7（DBI-DAC/ADC 频带方案与实验装置）；p8（NGMI–熵曲线+眼图）；p13（结论页）

## 本批小结
1. HCF 从"单跨低损耗展示"进入"系统级多维扩展"：1 µm 新窗口（PDP-A-2，106.1 km，53.3 Tb/s，12.15 THz）、O+C 双波段双向（PDP-A-4，2024 km，51.9+53.9 Tb/s GMI）、无中继 532 km（PDP-A-3，30.66 Tb/s）三条路线同时出现，共同点是用 HCF 极低非线性/宽窗口把带宽而不是功率作为主要增长维度。（PDP-A-2/3/4）
2. HCF 损耗记录与色散设计并行：Linfiber 0.052→YOFC 0.032±0.003 dB/km（45.26 km，PDP-A-3），同时微软/南安普顿把色散调到零且损耗约 0.2 dB/km（PDP-A-1）；色散为零的实际收益在 IM-DD（PAM4 BER 降约一个数量级）和省 DSP，但代价是损耗从 0.1 升到约 0.2 dB/km，与低损路线存在取舍，讲者给出更大纤芯（30 µm 仿真 0.057 dB/km，但尚未过零）作为出路。（PDP-A-1/3）
3. 气体吸收线（GLA）和空间密度是 HCF 长途化的两个实际瓶颈：PDP-A-4 明确对 GLA 影响信道降阶调制（16QAM）并做频谱平坦化算法，6750 km 处这些信道低于 100 Gb/s；缩小外径（约 190 µm，芯 25 µm）用于缓解缆内芯数受限；1 µm 窗口预计气体吸收少但器件生态（WSS、环形器等）缺乏。（PDP-A-2/4）
4. 超高波特率路线继续冲击"无器件可达"的带宽：450 GBd 相干（3.83 Tb/s，PDP-A-5）与 440 GBd IM-DD（826.6 Gb/s，PDP-A-6）均来自 Nokia Bell Labs，共同技术是 DBI-DAC/ADC 频带拼接+TFLN 调制器+离线宽线性/Volterra 均衡；实验室领先量产的时间在缩短（约 7 年→约 4 年）。（PDP-A-5/6）
5. IM-DD 与相干/coherent-lite 的边界继续模糊：PDP-A-6 指出 440 GBd 下 C 波段 SSMF 仅数十米，HCF（约 3 ps/nm/km）约 200 m，O 波段可到数 km；高速率 IM-DD 需更强均衡与编码，coherent-lite 可能竞争，而米级 scale-up 走"慢而宽"microLED/无 DSP 路线；PDP-A-1 的零色散 HCF 则为 IM-DD 提供另一条延长距离的物理途径。（PDP-A-1/6）
6. 1 µm/HCF 与 TFLN 的组合暴露封装/带宽落差：TFLN 调制器芯片带宽 >110 GHz，但封装 RF 中介层限制到 <20 GHz（PDP-A-2）；450 GBd 发射机同样使用 6 dB 带宽 >110 GHz 的 TFLN I/Q（PDP-A-5）——器件封装与电接口是下一步瓶颈。（PDP-A-2/5）
