---
title: "方向3 Scale Out 综合洞察"
tags:
  - ECOC2026
  - 综合洞察
---

# 方向3：Scale-out（224G/L、448G/L、光源、调制器、电芯片/DSP、OCS，需求与各家技术情况）

> 口径：数字均取自逐篇笔记，标注自报/仿真/实验/现网/读图估计/OCR/存疑；索引〔文件名简写 pN〕；无独立文件名的以场次号加"笔记"标注。

## 0. 一句话结论 + 5条核心判断

**一句话结论**：Scale-out 光互连处于"200G/lane 现网放量（LPO/LRO/FRO 并存）、400G/lane 多路线并行样机、光源与 OCS 成为新增变量"三线并行的状态；200G/lane 已有 10^5 量级链路的现网证据，400G/lane 的约束已从调制器带宽转移到电通道（约 90 GHz 干净带宽）、O 波段色散和接收端，尚无单一路线胜出。

**判断1：线性直驱（LPO）在受控网络已被大规模现网验证，但外推到 1.6T 存在明确分歧。**
- 阿里云 13,234 只 400G DR4 LPO、25.8M 器件小时（现网）：功耗中位数 4.2 W 对 8.1 W（FRO），壳温 35.1 对 45.5 °C，模块 TX+RX 时延 <5 ns 对 >100 ns，日链路抖动率 0.017% 对 0.040%（低 58%）〔0921-Mo3-A5-阿里云 p43-p46〕。
- Oracle 800G，约 35 万条链路（LPO-LPO n=156,591；FRO-FRO n=202,042）：中位 pre-FEC BER 1.1E-11 对 1.4E-11，p99 5E-10 对 3E-8，至少一次 down transition 的链路 3.244% 对 5.681%（现网）〔0920-pm-Su3-A-03-Oracle p7〕。
- 机制：去掉 DSP 重定时后，链路预算由模块转移到主机 SerDes；阿里通道损耗最大接近 16 dB（CEI-112G-VSR 极限），LPO-FRO 混用时接收灵敏度劣化（L2R 中位 -6.7 dB 对 L2L -9.4 dB），策略为纯 LPO 对 LPO〔0921-Mo3-A5-阿里云 p39, p41〕。1.6T 上 Oracle 认为 LPO 难以同时满足 SI 与互操作，LRO（26 dB 通道，16 W，约 10 pJ/bit，多家 3 nm DSP 互通）是当前最佳低功耗方案〔0920-pm-Su3-A-03-Oracle p8〕。

**判断2：400G/lane 的 IM/DD PAM4（约 212.5 GBd）已在 InP EML、薄膜 InP、硅 MZM、GeSi EAM、TFLN、等离子体等多条路线上出现≥400G 的实验或展台样机，路线未收敛。**
- InP EML：Coherent 3.2T OSFP 8×425G PAM4，Outer OMA 5.45 dBm，Outer ER 3.4 dB（ECOC 2026 演示）〔0923-MF-00-四家连拍 p53〕；Source Photonics 1.6T DR4 4×400G，212.5 GBaud，TDECQ 1.1 dB（展台演示，讲者自报）〔0922-MF-am-1020-SourcePhotonics p13-p14〕。
- 硅 MZM：imec/UGent 硅行波 MZM，EOE 带宽约 67 GHz，425 Gb/s（212.5 GBd）低于 20% FEC 门限，448 Gb/s 高于门限（实验）〔We2-B5-imec 笔记06〕。
- 机制：光电带宽已够（薄膜 EAM >100 GHz、GeSi EAM S21 约 100 GHz、TFLN 与 InP 直驱），瓶颈转移到电通道与色散（判断3）。

**判断3：色散与接收端是 400G+ IM/DD 的物理天花板，光域处理与相干（Coherent-lite）成为 O 波段 2 km 以上的竞争者。**
- 224 GBd，2 km，最坏色散，EQ 抽头 <20 且 SNR 代价 <4 dB：IM/DD FFE 仅约 45% 的 O 波段可用，FFE+1 抽头 DFE 约 70%；20 km 后 <5%；Broadcom 数据（J. Johnson，ITU-T/IEEE，2026-07）2 km 处 <10%（讲者引用）〔0920-pm-Su4-A-05-NICT p6, p9〕。
- 出路之一：香港中文大学硅光光域均衡，144 GBd PAM8 每波 432 Gb/s（25% SD-FEC，实验，2 km SMF，C 波段），24 波合计 10.36 Tbps，功耗 <50 mW，时延 <75 ps〔0922-Tu3-A2-香港中文大学 p10-p11, p13〕。
- 接收端：Nokia Bell Labs/上海科技大学 440 GBd PS-PAM6 单 PD 净速率 826.6 Gb/s（PDP，实验），受 C 波段 SSMF 色散限制只能到约 30 m（50 m 时 SNR 代价 0.7 dB；O 波段 SSMF 约 0.9 km、HCF 约 200 m）〔0924-PDP-A-6-NokiaBellLabs p8-p9〕。

**判断4：光源正从"模块内一颗 DFB"变成独立子系统，高功率 CW 与多波长两条路线并行，InP 产能是共同约束。**
- 需求侧：ELS 每波长 200 mW、光纤内 WPE >10%、RIN <-144 dBc/Hz、波长栅格 ±0.2 nm（Scintil 引 OIF ELSFP/OCI-MSA）〔0921-Mo3-待定-Scintil p1〕；Source Photonics CW 路线 70 mW（Q4 2025）→150 mW（Q3 2026）→200 mW（Q4 2026）→400 mW（Q1 2027，≤1600 mA @45 °C）（厂商路线图，自报）〔0922-MF-am-1020-SourcePhotonics p18〕。
- 替代路线：Quintessent GaAs QD 8λ 梳 + booster SOA 200 mW（>25 mW/λ，2 dB 均匀度，30 °C）〔0920-am-Su2-A-02-Quintessent p12〕；Chalmers/Solinide Si3N4 微梳 75 mW 泵浦，200 GHz 间隔 28 线 >1 mW，转换效率 69%（自报）〔0920-am-Su2-A-05-Chalmers p7〕。
- 约束：Omdia 认为硅光"胜利"本质是最小化 InP 用量，但 InP 光源"几乎不可避免"，高功率激光器芯片更大、良率更低，将使 InP 晶圆消耗高于预期〔0921-MF-pm-1540-Omdia p5, p11〕。

**判断5：OCS 从 Google TPU 专有应用走向 GPU 集群，MEMS 已可与 LPO 共存，纳秒级开关与超快收发器重锁定是下一个门槛。**
- 市场：OCS 2026 年 >\$2B，2030 年 >\$8B；2030 年端口约 46M（Scale-out TPU 约 18M，Scale-up GPU 约 26M，读图估计）〔0923-MF-00-四家连拍 p12〕。
- 验证：KDDI 用 96×96 MEMS OCS + 400G DR4/800G 2×DR4 LPO 在 H100 集群做 72 小时 LLM 预训练，OCS 插入使端到端时延增加数十 ns（RX1 203.9→290.48 ns），JCT 无显著影响〔0921-Mo3-A3-KDDIResearch p8, p12-p14〕。
- 门槛：Oriole 称超快交换（<10 ns）配标准收发器吞吐仍 <1%，只有"超快交换+超快重锁定"才 >90%（公司自述，无第三方验证）〔0920-pm-Su3-A-04-Oriole p9〕。

---

## 1. 需求与网络架构

**集群与端口规模**
- OCI AI 集群 2020→2026：16,384 → 32,768 → 65,536 → 131,072 GPU（1×→8×）；NIC 速率 2017 年 25G → 2026 年 1600G，讲者称"网络集群性能提升 256×"〔0920-pm-Su3-A-03-Oracle p2；0920-pm-Su3+Su4-A-00-全场扫描 p27-p28〕。
- NVIDIA 示例（讲者场景假设）：512K 个 Blackwell GPU 数据中心，仅 GPU 1200 W TDP 共 600 MW；scale-out 约 7100 个机架经 CX8 NIC 组成 3 层 fat-tree，约 1.8M 光收发器〔0920-am-Su2-I-01-NVIDIA p5〕。
- Marvell：XPU 数量 128 → 1M，互连数量 128 → >10M（自报）〔0921-Mo4-待定-Marvell p3〕。
- 交换机代际：51.2T=512×100G；102.4T=512×200G；204.8T=1,024×200G；409.6T=1,024×400G〔0920-pm-Su3-I-03-Arista p2〕；Source Photonics 标注 3.2T（8×400G）对应下一代 204T 交换机〔0922-MF-am-1020-SourcePhotonics p10〕。
- 放量节奏：达到 1000 万只/年所需年数 10G 15 年、100G 10 年、400G 8 年、800G 5 年、1.6T 4 年（LightCounting，OFC 2026 引用）〔0923-We2-B1-Lumentum p6〕。

**市场结构**
- 硅光收发器 2026 年首次超过收发器销售额的 50%（LightCounting），2031 年 TFLN/LiNbO3 占比明显上升（纵轴无刻度，仅看相对份额）〔0920-pm-Su3-A-01-LightCounting p3〕。Crealights 引用硅光渗透率 2025 年 38%、2026 年 50%、2030 年 73%；CPO/NPO 渗透率（TrendForce）2026 年 0.5%、2028 年 15%、2030 年 35%〔0922-MF-am-1200-Crealights p5-p6〕。

**架构分层（Scale-in / up / out / across）**
- LightCounting：scale-out 数十至数百米，"SiPh：448G per lane，可插拔，部分 CPO"；scale-up 约 1 m 为"contested"（铜+光）；scale-across 500 m 至公里级为集成相干〔0920-pm-Su3-A-01-LightCounting p5〕。
- Marvell 分层：Scale-out 100 m–2 km，200G/L → 400G/L PAM4；Scale-up 10–100 m；Scale-across 2–10 km O 波段 Coherent-Lite 1.6T/3.2T；>10 km C 波段 ZR/ZR+〔0920-pm-Su3+Su4-A-00-全场扫描 p74〕。

**客户口径的需求约束**
- TCO 三项：可靠性/可用性、功耗、Capex；网络相对计算的支出逐年上升，"不可持续"（Oracle）〔0920-pm-Su3-A-03-Oracle p5〕。
- 可靠性：Borrill 模型（三层 Clos，链路 MTTF 3×10^5 h）下，30 MW/20k GPU 约 3 小时一次 flap，300 MW/200k GPU 约 12 分钟，4.5 GW/3M GPU 约 48 秒；一条不稳定链路浪费 32,000 GPU-hours（32k GPU，1 小时检查点）（Credo 引用，仿真/案例）〔0923-MF-Credo p2-p3〕。
- OCI 现网：90+% 的链路故障源于污染，97% 的收发器更换源于污染〔0923-MF-00-四家连拍 p38〕。OCI 800G LPO 之前的教训：激光器跳模导致波长突变、SMSR 劣化、link flap，固定温度筛选无法检出，改为温度+电流扫描筛选，10 °C/min 扫温下中心波长在约 1308–1309.5 nm 间跳变（现网/实验）〔0920-am-Su1-A-02-Oracle p5-p6（笔记01）〕。
- 电通道成为约束：C2M 100G→200G PAM4 约 6 dB SNR 实现代价（读图近似）〔0921-MF-pm-1400-NexthopAI p5〕；OIF 指出当前"干净"信道带宽约 90 GHz（主要受连接器限制），448G PAM4 困难〔0923-MF-00-上午连拍 p33〕。

**标准与生态**
- OIF：CEI-448G-VSR/LR 项目 2026 年 2 月启动；应用距离 XSR 约 25 mm、VSR 约 250 mm、LR 约 1 m；调制与 FEC 仍标"?"，未见 448G PAM4/PAM6 决议〔0923-MF-00-上午连拍 p29, p31, p34；0923-MF-OIF-市场聚焦 p7, p12〕。

---

## 2. 技术路线与关键指标

### 2.1 200G/lane 现网：FRO / LRO / LPO / 遥测

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| 阿里云 | 400G QSFP112 DR4 LPO（硅光，3 家模块商） | 13,234 只/25.8M 器件小时；RMA 7 例（MTB RMA 420 年）对 FRO 209 例（456 年）；链路抖动 178 次（17 年）对 13,746 次（7 年）；7 例 RMA 为污染与 ESD；光环回 106.25 Gb/s PAM4 BER 中位数 2.0e-10（线卡）、2.7e-11（MAC 板），TDECQ >3.5 dB 端口 BER 仍好 | 现网+实验室 | 〔0921-Mo3-A5-阿里云 p40, p42, p46〕 |
| Oracle | 800G LPO vs FRO | 约 35 万链路；p99 BER 5E-10 对 3E-8；LPO 互操作数据有限，短/中/高损耗端口需调参 | 现网 | 〔0920-pm-Su3-A-03-Oracle p7〕 |
| Oracle | 64×800G 交换机整机功耗 | 全 FRO 1528 W；50% LPO/50% LRO 1270 W，节省 258 W；800G LPO 每模块省 5–7 W | 现网 | 〔0921-MF-pm-1320-Oracle p8〕 |
| Oracle | 1.6T LRO vs FRO | 26 dB 通道 16 W（10 pJ/bit）；3 厂平均 pre-FEC BER FRO 8.41E-13 对 LRO 2.72E-12；FEC bin P95 LRO 2 对 FRO 1 | 现网/实验 | 〔0920-pm-Su3+Su4-A-00-全场扫描 p33〕 |
| Nokia | 1.6T InP LPO（8×200G，106.25 GBd PAM4） | 功耗 8.8 W；TDECQ 2.11 dB；Outer ER 3.74 dB；平均发射功率 2.58 dBm；RLM 0.977 | 实测/规格 | 〔0921-PF-Nokia p11〕 |
| Source Photonics | 1.6T 功耗阶梯（102.4T 交换） | 全重定时 5 nm 30 W（18.5 pJ/bit）；LRO 15-17 W（12.5）；LPO 10 W（6.5）；NPO 8 W（5）；CPO 5 W（3） | 厂商自报 | 〔0922-MF-am-1020-SourcePhotonics p16〕 |
| Nexthop AI | 100T LRO/NPO 相对 FRO | 光学功耗 LRO -30%、NPO -60%；互操作最大 BER FRO <1e-10、LRO <1e-9、NPO <1e-8 | 自报/OFC 2026 演示 | 〔0921-MF-pm-1400-NexthopAI p11〕 |
| Credo | 六类收发器对比与遥测 | FRO 25–30 W；LPO 10–13 W；LRO 15–19 W；CPO 8–9 W；试点 128 模块、2 个月，GPU 利用率基线约 60% 对 ZeroFlap 约 90%（读图，讲者自注小样本） | 自报 | 〔0923-MF-Credo p4, p10〕 |

### 2.2 400G/lane 调制器与发射机路线（InP EML / TFLN / 硅光 MZM / MRM / SiGe·GeSi EAM / SOH / 等离子体）

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Coherent | InP EML 3.2T OSFP | 8×425G PAM4；8×212G→4×425G DSP；Outer OMA 5.45 dBm，Outer ER 3.4 dB；InP EML+InP PD 400G 全链路（OFC 2026 PDP Th4A.4） | ECOC 2026 演示 | 〔0923-MF-00-四家连拍 p53〕 |
| Lumentum | InP EML/DFB-MZI | 400G 路线：2024 400G PAM4；OFC'25 448G InP EML（Keysight+NTT 器件+Lumentum）与 450G DFB-MZI 展台；OFC'26 4×400G 1.6T 差分驱动 EML；InP MZM 比 TFLN 小 5× | 讲者自报 | 〔0920-pm-Su4-I-03-Lumentum p7-p10〕 |
| Source Photonics | 1.6T 4×400G OSFP（Gearbox） | 212.5 GBaud，SSPRQ，TDECQ 1.1 dB（屏幕读数 1.17 dB），Outer ER 4.2 dB；屏幕 Outer OMA 1.362 dBm 与幻灯文字略有出入 | 展台演示 | 〔0922-MF-am-1020-SourcePhotonics p13-p14〕 |
| NTT | 薄膜 InP EML 阵列 | 4ch×400G/448G PAM4，O 波段，55 °C；EAM 100 μm；3 dB 带宽 >100 GHz；ER 448G 各通道 3.0/3.2/2.8/2.7 dB；激光能耗 0.12 pJ/bit；成熟度 Level 3–5，无代工厂（OFC 2026 PDP Th4A.1） | 实验 | 〔0920-am-Su2-A-04-NTT p10-p11, p14〕 |
| HyperLight | TFLN 直驱 | 400G/lane PIC 可用，直驱 DSP 无外置驱动；1.6T FRO 约 21 W、TRO 约 12 W、12.8T XPO 约 80 W；调制器支持 224/260/360/448 GBd | 厂商自报 | 〔0920-pm-Su4-I-05-HyperLight p8-p9〕 |
| imec/UGent | 硅行波 MZM（PSD） | 双驱推挽，EOE 约 67 GHz，Vπ 18 V，插损 1.5 dB，VπL 约 1.8 V·cm；200 GBd 400G BER ~1e-3 <6.25% FEC；212.5 GBd 425G <20% FEC；224 GBd 448G >20% FEC；C 波段，15 dBm 激光，TX FIR 13 抽头，RX FFE 50 抽头 | 实验 | 〔We2-B5-imec 笔记06〕 |
| OFC 2026 硅 MZM 对照 | AMF / 之江实验室 / GF / Coherent | AMF 80 GHz、112 GBd PAM8；之江 97 GHz、135 GBd PAM8；GF 60 GHz、120 GBd PAM4；Coherent 67+ GHz、210 GBd PAM4（Vπ=7 V，O 波段） | 文献引用 | 〔We2-B5-imec 笔记06〕 |
| HKUST(GZ) | 硅微环（WGM），O 波段 | 半径 2.5 μm，FSR 5.2 THz（30 nm），EO 带宽 ≥69 GHz（-3 V），FSR×BW 358 THz·GHz（次高 CAS 228）；16 通道×224 Gb/s PAM4（SD-FEC，128 GSa/s AWG，单环依次测） | 实验 | 〔0923-We2-B2-80 p11-p14〕 |
| NVIDIA | 硅微环 CPO 发射机 | 212.5 Gbps/通道；16 通道在 OFC 2026 展会连续运行 3 天，总 BER <1E-14 | 展会实测（自报） | 〔0920-pm-Su3-A-05-NVIDIA p13〕 |
| imec | GeSi EAM（→Ge APD） | S21 在约 100 GHz 附近约 -2.5 dB（读图），2 V，1560 nm；212.5 GBaud PAM4；GeSi EAM→Ge APD 425/448 Gb/s（6.25%/12% FEC） | 实验 | 〔0921-Mo12-00-imec大会报告 p66-p67〕 |
| imec | 垂直 SOH | 50 μm 器件 S21 测至 110 GHz 仍在 -3 dB 线上；Vπ≈2.9 V（VπL <150 V·μm）；180 GBd PAM4 BER 约 3e-3（360 Gbps），200 GBd 约 3e-2（<20% SD-FEC）；光损耗 0.075 dB/μm | 实验 | 〔0923-We2-B3-1289 p5-p8〕 |
| ETH/Marvell | 等离子体 RRM oDAC | 串联双 RRM 336 Gb/s PAM4（3-tap LMS），非线性 DSP 下 360 Gb/s（比 MZM 好 10%）；AIR 328 对 277 Gb/s（+18%）；RRM 插损 1.2 dB，带宽 >110 GHz | 实验 | 〔0923-We3-D2-苏黎世联邦理工 p4-p5, p10〕 |


### 2.3 PAM4 / PAM6 / PAM8 与调制编码之争

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Arista | 448G 电接口格式 | PAM4 224 GBd 需 ~112 GHz；PAM6 ~173 GBd 需 ~90 GHz；PAM8 ~149 GBd 需 ~75 GHz；超低损耗 PCB 约 2.1 dB/in、Twin-ax 约 0.3–0.5 dB/in @112 GHz（示意曲线） | 讲者示意 | 〔0920-pm-Su3-I-03-Arista p3〕 |
| Marvell | 448G 组合 | FRO：C2M PAM6\|PAM4 + 光 PAM4；TRO：C2M PAM4 + 光 PAM4；Coherent-Lite DSP：光 QAM16；模块复杂度 NPO<TRO<FRO<Coherent-Lite（定性符号） | 讲者自报 | 〔0920-pm-Su3+Su4-A-00-全场扫描 p80-p81, p85〕 |
| Nexthop AI | 400G 调制矩阵 | 电 PAM6/光 PAM4 Gearbox（功耗高、性能好、采用）；电 PAM4/光 PAM4 的 LRO"有前景"；电 PAM6/光 PAM6 LRO 性能差、未采用 | 讲者自报 | 〔0921-MF-pm-1400-NexthopAI p8〕 |
| Nokia Bell Labs/SUST | PS-PAM6（H=2.4） | 440 GBd，净 826.6 Gb/s（SC-LDPC+BCH 码率 0.8262，NGMI 阈值 0.8714）；均匀 PAM4 BER 0.0225；PS-PAM6 BER 0.0331；此前 IM-DD 最高 NTT 248 GBd、660 Gb/s | 实验（PDP） | 〔0924-PDP-A-6-NokiaBellLabs p2, p8〕 |
| 香港中文大学 | 光均衡 PAM4/PAM8 | 136 GBd PAM4 BER 2.79×10^-3；136 GBd PAM8 2.22×10^-2；144 GBd PAM8 4.07×10^-2（对应 360/408/432 Gbps 于 HD/20%SD/25%SD-FEC），2 km SMF | 实验 | 〔0922-Tu3-A2-香港中文大学 p10〕 |
| Southampton ORC | 2D-PAM12（Scatter/Cross/DSQ） | 58 GBd，34.8 GHz，2 km SMF；SC-PAM12 GMI 3.45 bit/symbol，信息速率 >200 Gbit/s；DSQ 因需 16 幅度电平而 SNR 明显更低 | 实验 | 〔0923-We3-D1-1343 p13-p15〕 |

### 2.4 接收端：PD / APD / TIA

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| NICT | 零偏压 UTC 型 PD | 3 dB 带宽 200 GHz；线性至 2 mA；252 Gbps PAM-4，+11 dBm 时 BER 约 2×10^-3（读图），0 V、7-tap；126G NRZ 抖动 607 fs 对商用 50 GHz PD 1010 fs；800G/lane 为拟合响应的仿真眼图（非实测） | 实验+仿真 | 〔0924-Th1-C3-NICT p8-p10〕 |
| imec | Ge PD / Ge APD | O 波段 Ge PD BW >110 GHz，R~0.9 A/W；Ge APD BW~90 GHz，R~1.9 A/W，-7 V、Pin=-7 dBm 下 160/180 GBaud PAM4 眼图张开（OFC 2026 及未发表） | 实验 | 〔0921-Mo12-00-imec大会报告 p59〕 |
| imec | 免 CMP Ge-on-Si PD | 1310 nm，-2 V：0.89±0.02 A/W；65.3±1.5 GHz；暗电流 3.34±0.55 nA（25 °C，90 器件）；500 h HTOL（125/150/175 °C）无显著退化 | 实验 | 〔0924-Th2-E3-imec p11-p15〕 |
| 中科院西安光机所 | 倒装 SiGe APD + 28 nm CMOS TIA | APD 响应度 0.55→0.8 A/W，增益 31@-13.5 V；TIA 18.7 mW/通道，S21 26 dB，带宽 >65 GHz；接收灵敏度（SD-FEC 门限）200 Gb/s PAM4 -20.0 dBm；128G PAM4 -23.1；100G NRZ -26.1 | 实验 | 〔Th2-E5-中科院西安光机所 笔记07〕 |
| NVIDIA | 偏振分集 DWDM 接收机 | 4λ×64 Gb/s，400 GHz 间隔；2D 光栅耦合器 PDL <±0.1 dB（单点）/ ±0.2 dB（300 mm 晶圆 252 点）；SOP 约 2000 rad/s 扰动下 BER <10^-12，无主动偏振跟踪 | 实验 | 〔0924-Th2-E1-NVIDIA p8, p12〕 |

### 2.5 光源：CW / QD / 梳 / 外腔 / VCSEL

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Huawei | InP CW（UHP） | WPE >30% 直到 500 mW（50 °C），RIN <-150 dB/Hz；QD DFB 100 °C 下 200 mW@580 mA；多波长 8–16 λ、200–400 GHz 间隔；模块 WPE 需由 <10% 升至 >15%；第一代倒装集成（自有、免隔离器、KGD）已出货 >3M | 自报 | 〔0920-am-Su1-A-03-华为 p5-p7〕 |
| AMD | 光源方案权衡 | ELSFP 要求 ±0.2 nm、400 GHz、RIN -144 dB/Hz、线宽 <1 MHz；分立 InP DFB 主流；频梳间隔准但功率均匀性与效率待解；异质集成阵列功率扩展是挑战 | 讲者自报 | 〔0920-am-Su1-A-04-AMD p8-p9〕 |
| Source Photonics | 硅光 CW DFB 路线 | 70 mW（≤300 mA @75 °C）→150 mW（DFB+SOA，≤650 mA）→200 mW（≤850 mA）→400 mW（≤1600 mA @45 °C，2000×500 μm） | 自报 | 〔0922-MF-am-1020-SourcePhotonics p18〕 |
| Scintil | 异质 LEAF Light | 8 激光器（2025/09）→16 激光器（2026/09）+Mux+波长锁定；SHIP 200 mm 平台，85+ GHz TFLN 调制器；提出 10 亿颗量级制造问题 | 自报 | 〔0921-Mo3-待定-Scintil p1, p6, p8〕 |
| Photon Bridge | 悬臂 InP-on-SOI，8×8λ | 32 DFB+AWG；8 色偏差 ±27 GHz（rms 18–19 GHz）；AWG 实测间隔 197.4 GHz；>35–40 mW/色/光纤；Palette-1 2027Q1 送样；对准 <100 nm、<1 dB | 实验/规划 | 〔0920-am-Su2-A-03-PhotonBridge p8-p10〕〔0921-MF-pm-1420-PhotonBridge p4-p6〕 |
| POET | 外腔混合 Blazar | 4 通道 L 波段，400 GHz 间隔，每通道约 20 dBm（400 mA，50 °C），SMSR >50 dB；线宽 Lorentzian 36.9 kHz；0.016 nm/°C | 实验 | 〔0923-PF-POET-外置激光源ECL p6-p7〕 |
| Quintessent | GaAs QD-on-Si 梳/DFB | 8λ 梳峰值 WPE >20%，硅波导内 >80 mW，均匀度 2.0 dB；200 mW 梳（>25 mW/λ，2 dB）；DFB+SOA SMSR >55 dB，反馈达 -15 dB 时 RIN 约 -150 dBc/Hz；3 个 epi lot 约 3000 颗激光器 WPE 集中在 25–30%（未优化） | 实验 | 〔0920-am-Su2-A-02-Quintessent p4, p9-p14〕 |
| Columbia/Xscape | Kerr 梳 / CombX | 375 mW 泵浦：300 GHz 梳转换效率 63.6%，25 通道 >5 dBm；CombX 8λ 原型 2026Q2 送样、量产爬坡 2027Q4；16λ Gen2 功耗 Gen1 的 1/2（2026Q4 送样） | 自报（CLEO 2026） | 〔0920-am-Su1-A-05-Columbia p8, p10〕 |
| Chalmers/Solinide | Si3N4 光子分子微梳 | O 波段，75 mW 泵浦，200 GHz，28 线 >1 mW，效率 69%（自报）；9283 个谐振晶圆统计，转换效率主要约 50–60%（读图）；150 mW/64 线、300 mW/128 线为建模路线图 | 实验+仿真 | 〔0920-am-Su2-A-05-Chalmers p7, p9, p12〕 |
| Lumentum/Coherent | 1060 nm VCSEL | Lumentum：UCIe 32 Gbps/通道，>1.5 Tbps/mm，<2.5 pJ/bit；Coherent 2D VCSEL NPO 1.2 pJ/bit（"Industry First"），量产 1H CY27；东京科学大学 62 GHz 1060 nm VCSEL，256 Gbps PAM4，<50 fJ/bit（200 Gbps，芯片直流） | 自报/实验 | 〔0920-pm-Su4-I-03-Lumentum p16〕〔0923-MF-00-四家连拍 p51〕〔We5-I 东工大 p10-p12〕 |

### 2.6 电芯片 / DSP / FEC / 均衡

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Lumentum | 模块功耗拆分 | DSP 占 49%；SerDes 40%、ADC/DAC 36%、核 24%；收发器功耗曲线 2016 年约 38→2025 年约 17 pJ/bit（读图） | 讲者引用 | 〔0923-We2-B1-Lumentum p8, p19〕 |
| CUHK | 硅光光学均衡（IIR+格型 FIR） | 插损 <3 dB；对比动机：1.6T DSP 可插拔约 25 W（3 nm）/约 20 W（2 nm）；3 nm DSP 仅能把 112 GBd PAM4 的 O 波段边缘波长延伸到 2 km | 实验 | 〔0922-Tu3-A2-香港中文大学 p3-p4, p8〕 |
| NICT/UCLA | 1 抽头光延迟线、成对传输 | C 波段 100 Gbaud 80/100 km 记录级低 DSP 复杂度（作者自述，OFC'24）；成对传输光纤束 BER 在 40 km 达约 HD-FEC 极限；MCF 上约 80 km@100 Gb/s、50 km@150 Gb/s（读图） | 实验/自述 | 〔0920-pm-Su4-A-05-NICT p12, p14〕 |
| NTHU | 物理感知稀疏 Volterra | 100G PAM4 IM/DD，4.2 km SMF；剪 92% 系数无 BER 代价；达 KP4 门限约 371→31 次乘法/符号；相对 MP-VE -36.5% | 实验 | 〔0921-Mo5-F6-清华 p14-p15〕 |
| EPFL | 最大覆盖 Chase 译码 | oFEC（eBCH(256,239,2)，16-QAM）36 个 TEP 达到 Chase-Pyndiah 93 个的性能，最坏复杂度 -61.3%；RS-BCH 级联 -25% | 仿真 | 〔0924-Th2-H1-EPFL p10, p12〕 |

### 2.7 OCS / 光交换

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| iPronics | 增益受控硅光 OCS（ONE-32/64） | 32×32（约 2,000 单元）→32×32 v2（约 4,000）→64×64（约 6,000）→>100 端口（约 10,000，2027 设计中）；OCS 增益 10 dB，Lumentum 1.6T 2×DR4 收发器 BER 较 1e-12 基线劣化约 1 个数量级；目标约 \$100/端口；系统 30 W + 0.78 W/激活通道 | 自报，"行业首次" | 〔0923-We-F-00-标准化专场II p50, p57-p60〕〔0920-am-Su2-I-03-iPronics p11-p13〕 |
| OneTouch | 薄膜钽酸锂 8×8 EO OCS | r33 30.5 pm/V（LN 30.9）；切换 <4 ns（单 MZM，未端接电容反射所限）；12 个开关合计 <200 nW；片上平均插损 8.6 dB（6–8 dB 为边缘耦合）；一阶串扰均值 -24.3 dB；1 小时漂移 -0.33 dB@10 dBm | 实验，"首个" | 〔0922-Tu1-E4-OneTouch p4, p10-p11, p14-p16〕 |
| 清华大学 | Si3N4-TFLN 可切换激光器 + AWGR | 调谐 40 nm，SMSR 63.9 dB，本征线宽 106.06 Hz；2.4 nm 切换 <15 ns，10 pJ；200 Gbps DP-QPSK 25 GBaud，3 km，切换延迟 80 ns | 实验 | 〔0922-Tu1-E1-清华 p4-p7〕 |
| 浙江大学 | 硅光 MEMS，2.5D Torus | 128 端口时插损约 15 dB 对 Crossbar 约 33 dB（读图）；16×16 原型消光比 >27.8 dB，实测片上 IL 3.3–9.3 dB | 实验 | 〔0922-Tu1-E2-浙江大学 p16-p19〕 |
| KDDI Research | 96×96 MEMS OCS + LPO | 链路建立 LPO 约 5.2 ms 对 DSP 约 6.2 ms（读图均值）；JCT 无显著影响；GPU 零流量窗口 100–400 ms；72 小时预训练稳定 | 实验 | 〔0921-Mo3-A3-KDDIResearch p10, p13-p14〕 |
| Oriole | PRISM 无源波长路由 | 32,000 GPU 参考架构：交换机 2,560→0，收发器总数 196,608→32,768，网络功耗 -81%；训练算力利用率 99% 对 EPS 40% | 公司自述 | 〔0920-pm-Su3-A-04-Oriole p9, p12〕 |
| NVIDIA | OCS 落地障碍 | 路径至少 4 个 bulkhead 连接器，DR4 余量 3 dB、FR4 余量 4 dB；目标每 1RU >256 双工端口 | 讲者自报 | 〔0920-am-Su2-I-01-NVIDIA p18〕 |

### 2.8 封装形态与光纤连接（与方向4边界）

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| OIF | 72 GPU Pod（100 GBd PAM4）功耗 | CPO 4 pJ/b；LTLR 6；RTLR 10；RTRR 15；Pod 总功率 CPO 约 90 kW 对可插拔约 100 kW（读图） | 标准分析 | 〔0923-MF-00-上午连拍 p44〕 |
| NVIDIA | 1.6T 选项 pJ/b（功耗） | FRO 14（25 W）；TRO 10（18 W）；LPO 6.4（11 W）；CPO 4（7 W） | 自报 | 〔0920-am-Su2-I-01-NVIDIA p11〕 |
| TeraHop | Open CPX Diablo-1 6.4T NPO | 典型功耗 <35 W，<5.5 pJ/bit；FIT：SiPho PIC <0.01，1.6T OSFP <1，6.4T NPO 估计 <10；宣称 >25M 硅光收发器、PIC >100B 器件小时 | 自报 | 〔0923-MF-00-四家连拍 p59, p61-p62〕 |
| Oracle | CPO 顾虑 | 相对全重定时可插拔功耗最多省 50%、理论成本 30%+；系统 FIT 预期更高；409.6T CPO 交换机 512×8 光纤，4096 个箱级 SPOF | 现网/引用 | 〔0923-MF-00-四家连拍 p36, p38〕 |
| CommScope | FastSelfClean 自清洁连接器 | 插损 <0.1 dB 典型/0.25 dB 最大（N=6,384 芯，1310 nm），回损 >70 dB 典型；1RU 3,456 芯；安装时间较 MPO 8 降至 1.5%（模型） | 自报 | 〔0921-PF-CommScope p3-p4〕 |
| 长飞（YOFC） | O 波段 HCF 水汽稳健性 | 85 °C/85% RH 10 天；2 km HCF 四工作波长插损变化 ±0.1 dB/km 内；400G-FR4 预 FEC BER 与 SMF 相当（约 1E-7~1E-4） | 实验，"首次" | 〔0922-Tu1-G4-长飞 p8-p10〕 |

---

## 3. 厂商与客户态势

### 3.1 AIDC / 云客户与运营商
- **Oracle（OCI）**：TCO 判据；800G LPO 大规模部署；1.6T 选 LRO；"现在应开始试用 CPO/NPO"，因 >224G/lane 时 CPO/NPO 可能是唯一出路；系统 FIT 更高、污染占 97% 收发器更换〔0920-pm-Su3-A-03-Oracle p8-p13〕〔0923-MF-00-四家连拍 p38〕。
- **阿里云**：scale-out 现用 FRO，未来 FRO+LPO 并存；scale-up 未来 LPO→NPO→CPO；13,234 只 LPO 现网数据；策略为纯 LPO 对 LPO 部署〔0921-Mo3-A5-阿里云 p37, p41〕。
- **OpenAI**：以请求延迟（TTLT）与每请求能耗比较互连；自研 Jalapeño 128/2048 颗两级 Clos（Broadcom TH6），同吞吐下延迟约 1.8× 更低（对 GB300 MTP，自报）；对铜/可插拔/NPO/CPO 给定性对照〔0920-pm-Su3-A-02-OpenAI p7-p8, p10〕。
- **Microsoft**：宽而慢 + microLED，目标 <1 pJ/bit、>10 Tbps/mm、约 10 m、<<1 FIT、<10 ns；自称风险仪表指向"很高"，需生产规模验证〔0922-Tu1-E3-Microsoft p15, p20〕。
- **Google（他人引用）**：OCS 主要用户，几乎全部 Scale-out TPU；200G FR4（主要 DML）失效以 LD 为主（43.4%）〔0923-MF-00-四家连拍 p12〕〔0920-am-Su1-A-02-Oracle p8-p10（笔记01）〕。

### 3.2 设备商
- **NVIDIA**：Spectrum-X/Quantum-X CPO 已量产（微环调制器、TSMC COUPE 3D 堆叠）；自报相对可插拔 4× 更少激光器、5× 更低功耗、10× 更高 MTBI；CPO 约 4 pJ/b，节省约 72% 收发器功耗；下一标准 400 Gb/s（200 GBaud PAM4）〔0920-pm-Su3-A-05-NVIDIA p8-p9, p13, p15〕；同时 OSFP 仍是主力（含 TRO、DR4+），Spectrum-X 多平面 8 planes、可达 512k GPU〔0923-MF-00-四家连拍 p43-p45〕。
- **Arista**：最优取决于系统约束；原生 OCI 功耗/时延收益最大，带 reverse gearbox 的 OCI 兼容性更好；Arista 100T 设计概念采用 6.4T Open CPX 引擎〔0920-pm-Su3-I-03-Arista p8〕〔0923-MF-00-四家连拍 p60〕。
- **Nokia**：光子集成路线含 InP、硅光、TFLN；1.6T InP LPO 8.8 W；Nokia 7220 IXR 交换机含 LPO 版 OSFP（OCR，型号需核对）〔0921-PF-Nokia p11〕〔0921-Mo3-待定-Nokia p11〕。
- **Huawei**：Atlas 950 SuperPoD 采用 4096×800G SR8 VCSEL LPO；页面标 Latency 降 90%、Power 降 60%（基线未明示）；7.2T Hi-ONE NPO 板载激光〔0920-am-Su1-A-03-华为 p3, p5〕。

### 3.3 模块 / 器件商
- **Lumentum**：立场"Scale-out=快窄（InP），Scale-up/in=宽慢（VCSEL）"；1.6T 硅光发射机量产，光纤到硅光耦合 Gen2 <0.9 dB/facet；CTO 称 3DS VCSEL 已出货 20 亿颗发射器；ECOC 2026 VCSEL/UCIe 首演〔0920-pm-Su4-I-03-Lumentum p7, p12, p17〕〔0923-We2-B1-Lumentum p12〕。
- **Coherent**：3.2T OSFP 8×425G 演示；2D VCSEL NPO 1.2 pJ/bit；XPO 12.8T/25.6T；2030 SAM 现有组合 \$60B+，加 CPO/NPO \$30B+（自报，来源注含内部估计）〔0923-MF-00-四家连拍 p47, p51, p53-p54〕。
- **Source Photonics**：可插拔仍是 AI scale-out 首选；NPO 可能 2027 起量，XPO 时间线不清晰；CW 激光 70→400 mW 路线图〔0922-MF-am-1020-SourcePhotonics p16, p18, p20〕。
- **TeraHop**：Open CPX 6.4T Diablo-1；>25M 硅光收发器；Omdia 图示滚动 4 季度份额 1Q26 约 +3%（读图）〔0923-MF-00-四家连拍 p59-p61〕〔0921-MF-pm-1540-Omdia p3〕。
- **POET / Photon Bridge / Scintil / Quintessent / Xscape**：光源与 ELS 阵营，见 2.5 表；Photon Bridge Palette-1 2027Q1 送样，Xscape FALCONX 8 量产爬坡 2027Q4，Scintil 16 激光子组件 2026/09〔0920-am-Su2-A-03-PhotonBridge p10〕〔0920-am-Su1-A-05-Columbia p10〕〔0921-Mo3-待定-Scintil p6〕。
- **Credo**：主打收发器健康遥测（ZeroFlap，OCP'26 将发布完整数据）〔0923-MF-Credo p10〕。
- **ST（代工）**：PIC100/B55X 300 mm，2027 年产能扩 4×，2031 年前 350M+ 硅光端口；CMOS 级光子良率 >90%；PIC100G（112 Gbd PAM4）量产、PIC200G（200 GBd）研究〔0920-am-Su1-C-03-STMicro p4, p9〕〔0923-We5-B-ST p4〕。

### 3.4 芯片商
- **Broadcom**：TH6 102.4T（64×200G SerDes×8 chiplet）；其 O 波段 2 km 可用带宽 <10% 数据被 NICT 引用〔0920-pm-Su3-I-08-AppliedMaterials p4〕〔0920-pm-Su4-A-05-NICT p9〕。
- **Marvell**：DSP 是 scale-out 主力；TRO|NPO → PAM4 FRO|TRO → Coherent-Lite → ZR/ZR+ 是"连续谱"；400G/lane 下电/光边界需联合设计；Marvell/Polariton 等离子体 oDAC；Marvell TFLN 光学 1.6T ZR〔0920-pm-Su4-A-01-Marvell p5-p6, p22〕〔0923-We3-D2-苏黎世联邦理工 p2〕。

---

## 4. 学术关键突破（按影响力排序）

| # | 机构 | 论文号/文件名 | 突破点 | 数字 | 标签 | 索引 |
|---|---|---|---|---|---|---|
| 1 | Nokia Bell Labs / 上海科技大学 | PDP-A-6 | 单调制器+单 PD，440 GBd PS PAM-6，IM-DD 单通道净速率过 800G | 826.6 Gb/s；此前最高 NTT 248 GBd、660 Gb/s；≈190–206 GHz MUTC PD、三频带 DBI-ADC | PDP，record 级 | 〔0924-PDP-A-6-NokiaBellLabs p2, p8〕 |
| 2 | imec | 大会报告（ECOC 2026 Shahin） | 100 GHz 低压 Ge/Si APD 首次用于 400G/lane 演示 | 425 Gb/s（6.25% FEC）、448 Gb/s（12% FEC），BER 约 10^-2 量级 | 首次（讲者自称） | 〔0921-Mo12-00-imec大会报告 p67〕 |
| 3 | NTT | OFC 2026 PDP Th4A.1（Workshop 引用） | 4ch×400G/448G PAM4 薄膜 InP EML 阵列 | 3 dB 带宽 >100 GHz；激光 0.12 pJ/bit；岸线密度 3.2 Tbps/mm | PDP | 〔0920-am-Su2-A-04-NTT p10-p11〕 |
| 4 | 香港中文大学 | Tu3-A2 | 首个 >400G/λ 硅光全光均衡，DSP-free | 432 Gbps/λ（144 GBd PAM8，25% SD-FEC），24 波 10.36 Tbps，<50 mW，<75 ps | 首次 | 〔0922-Tu3-A2-香港中文大学 p10-p12〕 |
| 5 | imec/UGent | We2-B5 | 可量产硅行波 MZM 净 400G/lane | 212.5 GBd 425G <20% FEC；EOE 约 67 GHz | 实验 | 〔We2-B5-imec 笔记06〕 |
| 6 | imec | We2-B3（#1289） | 垂直 SOH 50 μm 器件带宽 >110 GHz | 180 GBd PAM4 360 Gbps；Vπ≈2.9 V | 实验 | 〔0923-We2-B3-1289 p5-p8〕 |
| 7 | HKUST(GZ) | We2-B2（#80） | WGM 增强硅微环，大 FSR 与高带宽兼得 | FSR 5.2 THz，69 GHz，358 THz·GHz；16×224G PAM4 | 表内最高 | 〔0923-We2-B2-80 p11-p14〕 |
| 8 | NICT | Th1-C3 | 零偏压 200 GHz PD | 252 Gbps PAM-4，+11 dBm，BER 约 2×10^-3（读图） | 实验 | 〔0924-Th1-C3-NICT p9-p11〕 |
| 9 | OneTouch / InnovSemi | Tu1-E4 | 首个 TFLT 电光 8×8 OCS，纳秒切换、低静态功耗 | <4 ns；12 开关 <200 nW；128×128 外推 7.5 μW 对热光 9.0 W | 首个 | 〔0922-Tu1-E4-OneTouch p10-p11〕 |
| 10 | 清华大学 | Tu1-E1 | 波长可切换 Si3N4-TFLN 激光器用于快速相干光交换 | 线宽 106.06 Hz；15 ns 切换；200G DP-QPSK，延迟 80 ns | 实验 | 〔0922-Tu1-E1-清华 p4-p7〕 |
| 11 | iPronics（+Lumentum 收发器） | Mo3-A1 / We-F | 首个 1.6T 收发器经增益受控硅光 OCS 的链路质量 | OCS 增益 10 dB，BER 劣化约 1 个数量级 | 行业首次（自称） | 〔0921-Mo3-A1-iPronics p14〕〔0923-We-F-00-标准化专场II p60〕 |
| 12 | KDDI Research | Mo3-A3 | LPO+OCS 全栈：H100 上 72 小时 LLM 预训练 | 增加时延数十 ns；链路建立 LPO 约 5.2 ms | 首次（自称） | 〔0921-Mo3-A3-KDDIResearch p8, p14〕 |
| 13 | 复旦大学 | Th2-H6 | 免自适应 THP-FFDNN 的 FTN PAM4 | 169 GBd @37.9 GHz；408 参数 | "record-high"（讲者称） | 〔0924-Th2-H6-复旦大学 p11-p12〕 |
| 14 | ETH / Marvell(Polariton) | We3-D2 | 串联双等离子体 RRM 光 DAC | 336 Gb/s PAM4（360 Gb/s 非线性 DSP）；AIR +18% | 实验 | 〔0923-We3-D2-苏黎世联邦理工 p4, p10〕 |
| 15 | Laval / Femtum | We2-B4（#163） | 飞秒激光修整用于有源微环调制器 | 3.1 nm 偏移，不损 EO；110 Gbaud | 首次（隐含，原话未写 first） | 〔0923-We2-B4-163 p3, p7-p9〕 |
| 16 | Southampton / YOFC | Tu1-B3 / Tu1-G4 | HCF 上 IM/DD 多阶 PAM 与 O 波段水汽稳健性首次实验验证 | 4.96 Tbit/s 31 路 11.6 km；YOFC 2 km 插损变化 ±0.1 dB/km 内 | 首次（YOFC 自称） | 〔0922-Tu1-B3-南安普顿 p10〕〔0922-Tu1-G4-长飞 p8, p11〕 |
| 17 | NVIDIA | Th2-E1；Tu1-E5 | 4λ×64G 偏振分集微环 DWDM RX 无需 PMF；动态环分配省热调谐功耗 | PDL ±0.2 dB（252 点）；SNR 8.1→7.6 dB；0.8 Tb/s/mm、2.78 pJ/b | 实验 | 〔0924-Th2-E1-NVIDIA p8, p12〕〔0922-Tu1-E5-NVIDIA p4〕 |
| 18 | Chalmers / Solinide；Columbia | OFC 2026 Th2A.13；CLEO 2026 Highlight | O 波段微梳与高功率灵活 FSR Kerr 梳 | 69% 效率（28 线 >1 mW）；63.6%（375 mW 泵浦，300 GHz） | 自报/CLEO Highlight | 〔0920-am-Su2-A-05-Chalmers p7〕〔0920-am-Su1-A-05-Columbia p8〕 |
| 19 | Quintessent；Photon Bridge | Workshop | QD 8λ 单腔梳 200 mW；32 DFB 晶圆级 8 色集成"first chips out of fab"（单芯片 8×8λ ELS：32 DFB + AWG MUX） | 2 dB 均匀度；±27 GHz | 首个（自报） | 〔0920-am-Su2-A-02-Quintessent p12〕〔0920-am-Su2-A-03-PhotonBridge p6, p9〕 |
| 20 | imec | Th2-E3 | 免 CMP Ge PD 高可靠 | 500 h HTOL 无暗电流退化；65.3 GHz | 实验 | 〔0924-Th2-E3-imec p15〕 |

---

## 5. 分歧、争议与反常识

**5.1 LPO 能否走到 1.6T？**
- 一方（Oracle）：800G LPO 现网稳定性不逊于 FRO，但 1.6T 上 LPO 难同时满足 SI 与互操作；LRO（26 dB，16 W）是当前最佳〔0920-pm-Su3-A-03-Oracle p8〕。
- 另一方（阿里云）：现网 LPO 抖动更低、功耗降 48%，并作为 NPO/CPO 线性驱动的基础，在受控封闭网络最成熟〔0921-Mo3-A5-阿里云 p43, p47〕；Nexthop 认为电 PAM4/光 PAM4 的 400G LRO"有前景"，代价是裕量更低〔0921-MF-pm-1400-NexthopAI p6, p8〕。
- 证据差异：阿里数据为 400G DR4（106.25 Gb/s PAM4，通道损耗接近 16 dB）；Oracle 数据为 800G 与 1.6T，且 LPO 互操作数据有限；两者不同速率不可直接外推。

**5.2 快窄 vs 慢宽**
- 快窄（Applied Materials Chris Cole）：快窄是 400G 光学唯一现实选项，慢宽"great for attracting AI funding"，且需全重定时 reverse gearbox，成本/功耗/时延更高〔0920-pm-Su3-I-08-AppliedMaterials p11-p12〕〔0923-MF-00-四家连拍 p63〕。
- 慢宽（Columbia/Xscape/Chalmers/Microsoft）：波长并行 + 中速可比窄快在带宽密度×能效上有约 100× 优势（Columbia 图示，作者研究点对商用点）〔0920-am-Su1-A-05-Columbia p9〕；microLED 需生产规模验证〔0922-Tu1-E3-Microsoft p20〕。
- 折中（Arista、LightCounting）：最优取决于系统约束；行业通过 MSA"囤积可互操作选项"，"架构是赌注，加宽不是"〔0920-pm-Su3-I-03-Arista p9〕〔0920-pm-Su3-I-02-LightCounting p8, p12〕。

**5.3 400G/lane：IM/DD PAM4 还是 Coherent-lite？**
- IM/DD 阵营：Source Photonics 展示 212.5 GBd 4×400G；HyperLight、NTT 薄膜 EML 至 448G〔0922-MF-am-1020-SourcePhotonics p13〕。
- 相干阵营：NICT 指出 IM/DD 在 CD 补偿上与相干 DSP"根本不具竞争力"，无零点突破则 Coherent-lite 主导 2 km 以上；Broadcom 数据 2 km 处 O 波段可用 <10%〔0920-pm-Su4-A-05-NICT p3, p9〕。
- 修正方：光域均衡（CUHK 432G/λ，2 km）与 1 抽头 ODL；另有观点认为 Coherent-lite 在 800G/1.6T"没有市场"，机会在 1.6T 单波/3.2T 双波长〔0923-MF-00-四家连拍 p13〕。

**5.4 CPO 何时、以何种形态**
- NVIDIA：CPO 已量产，4× 更少激光器、5× 更低功耗、10× 更高 MTBI；网络中断可累计每天 \$3M 损失，CPO 将"近乎消除"；网络占总功耗 6–8%，CPO 可降 5 倍（自报）〔0920-pm-Su3-A-05-NVIDIA p9, p16〕。
- Oracle：系统 FIT 预期更高，方案专有，512×8 光纤 = 4096 个箱级 SPOF；NPO 更灵活〔0923-MF-00-四家连拍 p36-p38〕。
- Source Photonics 认为 NPO 2027 起量；Applied Materials 称 CPO 将是"高性能、封闭生态、低量"，被某高管重命名为 CPO(CP-zero)〔0922-MF-am-1020-SourcePhotonics p16〕〔0920-pm-Su3-I-08-AppliedMaterials p5〕。

**5.5 光源：分立 InP DFB 是否够用？**
- 分立 DFB（AMD、Scintil）：主流、已量产验证，但 Scintil 追问能否扩到 10 亿量级〔0920-am-Su1-A-04-AMD p9〕〔0921-Mo3-待定-Scintil p1〕。
- 替代路线：QD 梳（Quintessent）、Kerr 微梳（Chalmers/Columbia）、外腔（POET）；Dream Photonics 引用 Intel 教训：混合集成在销量达阈值前更优，过早异质集成有 >\$100M 研发无法回收风险〔0920-am-Su2-A-01-UBC p9〕。
- 可插拔性之争：Oracle 认为 ELSFP 可插拔性可能是负担（盲插连接器清洁），内置光源应更可靠；Source Photonics 则以 ELSFP 为关键使能，同时指出内置激光有温控与热耗散风险〔0920-am-Su1-A-02-Oracle p8-p10（笔记01）〕〔0922-MF-am-1020-SourcePhotonics p19-p21〕。

**5.6 OCS 需要多快？**
- 需要纳秒：Oriole 称 <10 ns 开关配标准收发器吞吐 <1%，须超快重锁〔0920-pm-Su3-A-04-Oriole p9〕；OneTouch 称"和 MEMS 一样冷，快一千倍"〔0922-Tu1-E4-OneTouch p12〕。
- 毫秒足够：KDDI 的 96×96 MEMS 在 GPU 计算阶段 100–400 ms 零流量窗口内切换，周期切换稳定，随机切换易中断作业〔0921-Mo3-A3-KDDIResearch p13〕。

**5.7 反常识条目**
- LPO 现网 BER 尾部优于 FRO（p99 5E-10 对 3E-8），且 TDECQ >3.5 dB 的端口 BER 仍好，即 TDECQ 与 BER 相关性弱〔0920-pm-Su3-A-03-Oracle p7〕〔0921-Mo3-A5-阿里云 p40〕。
- 激光器并非可靠性短板：Oracle 称 CW 激光是低 FIT 器件，DML/VCSEL 被误读为"激光器 FIT 最高"；Google 现场失效"无激光器可靠性失效"，最高为固件问题；但 200G FR4（DML）LD 占失效 43.4%〔0920-am-Su1-A-02-Oracle p8-p10（笔记01）〕。
- "光学从未变低功耗，只是去掉了 DSP"，SiPho 链路预算停滞在 15–17 dB（amsOSRAM 观点）〔0920-am-Su1-B-03-amsOSRAM p2〕。

---

## 6. 判断与观察点

### 6.1 技术成熟度与时间窗口

| 技术 | 成熟度判断 | 时间窗口 | 依据 |
|---|---|---|---|
| 200G/lane 可插拔（FRO/LRO） | 量产，1.6T 爬坡 | 2026–2028 | 1.6T LRO/FRO 为 Oracle 的计划路线；1.6T 到 2030 年约 56M（读图）〔0920-pm-Su3-A-03-Oracle p13〕〔0923-MF-00-四家连拍 p10〕 |
| 800G/400G LPO | 受控网络规模现网 | 已进入 | 阿里 13,234 只、Oracle 约 35 万链路 |
| 1.6T LPO | 未定，受 SI/互操作制约 | 2027 起看数据 | Oracle 认为难以满足，Nokia 有 InP LPO 样品 8.8 W〔0921-PF-Nokia p11〕 |
| 400G/lane IM/DD | 样机/展台 | 3.2T 出货 2028 起步（读图估计） | Coherent、Source Photonics 演示；OIF 448G 电接口仅框架/项目启动 |
| 高功率 CW（150–400 mW） | 规划/送样 | 2026Q3–2027Q1（厂商路线图） | Source Photonics p18；Photon Bridge 2027Q1 |
| 多波长梳/QD 梳 | 送样 | 2026Q2–2027Q4 | Xscape、Quintessent；微梳数据为自报 |
| NPO/Open CPX | 规范与首批引擎 | 2027 起量（Source Photonics 判断） | Open CPX 1.0（2026-09-16），TeraHop Diablo-1 |
| MEMS OCS | 已用于 Google TPU | 已进入 scale-out | OCS 2026 >\$2B（读图） |
| 硅光/TFLT/TFLN 快速 OCS | 芯片/8×8 原型 | 2027 前后出 >100 端口 | iPronics 路线图；OneTouch 8×8 |

### 6.2 对各类厂商的含义
- **设备商（交换机/系统）**：400G/lane 下电通道成为约束，扩展重点从"均衡长通道"转向"缩短电路径"（XPO/NPO）；需在交换机设计阶段确定 OCI 原生还是带 reverse gearbox〔0920-pm-Su3-I-03-Arista p3, p8〕。OCS 需要新的编排器、NCCL、SDN 支持〔0920-am-Su2-I-03-iPronics p3〕。
- **模块/器件商**：LPO 需要"链路预算+互通+遥测"的系统交付（Credo、Oracle 的激光筛选教训）；调制器路线需保留 InP/TFLN/硅多平台选项；激光器从消耗品变成 ELS 子系统，InP 晶圆与 SOI 供应成为竞争要素〔0921-MF-pm-1540-Omdia p5-p6〕。
- **芯片商（DSP/驱动/TIA）**：448G 时 PAM6 电/PAM4 光的格式转换带来 gearbox；2 nm DSP 与 100 GHz DAC/ADC 可行〔0922-MF-am-1020-SourcePhotonics p11〕；光域均衡、光 DAC 等"移除 DSP/DAC"的技术若成熟将改变 DSP 价值占比（DAC 占数字电路功耗 22%）〔0923-We3-D2-苏黎世联邦理工 p2〕。

### 6.3 未来 12–24 个月要盯的指标
1. **LPO 现网扩展**：1.6T LPO/LRO 的链路抖动率、p99 BER、互通矩阵；Credo/ZeroFlap 完整数据（OCP '26）〔0923-MF-Credo p10〕。
2. **400G/lane 可用余量**：212.5 GBd 下 TDECQ/BER 随温度的分布；电通道干净带宽由约 90 GHz 向 112 GHz 的推进；OIF CEI-448G 的 PAM4/PAM6 决议〔0923-MF-00-上午连拍 p33〕。
3. **O 波段色散数据**：Broadcom（<10%）与 NICT（<45%）的差距能否通过标准化测量统一；2 km 以上是否转向 Coherent-lite〔0920-pm-Su4-A-05-NICT p9〕。
4. **CW 激光与 ELS**：400 mW 芯片的良率与 FIT（≤1600 mA @45 °C）、ELSFP 现场故障率、InP 晶圆消耗〔0922-MF-am-1020-SourcePhotonics p18〕。
5. **NPO 起量与系统 FIT**：6.4T NPO 估计 <10 FIT（自报）是否被现场数据证实；污染类 SPOF（4096）能否被 EBO 缓解〔0923-MF-00-四家连拍 p38, p62〕。
6. **OCS 关键指标**：单端口价格（目标约 \$100/端口）、每 1RU 端口数（>256 双工）、插损与 DR4 余量 3 dB、收发器重锁定时间〔0920-am-Su2-I-01-NVIDIA p18〕。

---

## 7. 推荐配图
1. 0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf p46 — 13,234 只 LPO 与 FRO 的可靠性统计表（RMA、抖动、MTB）— 支撑判断1
2. 0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf p43 — LPO 与 FRO 功耗/壳温箱线图（4.2 W 对 8.1 W）— 判断1
3. 0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf p41 — 互通矩阵，L2R 灵敏度劣化 — 分歧5.1
4. 0920-pm-Su3-A-03-Oracle.pdf p7 — 800G LPO vs FRO 约 35 万链路 BER 分布与 down transition 比例 — 判断1
5. 0920-pm-Su3-A-03-Oracle.pdf p8 — 1.6T LRO vs FRO 三厂 BER 与 16 W — 判断1/分歧5.1
6. 0922-MF-am-1020-SourcePhotonics.pdf p16 — FRO→CPO 功耗阶梯（30→5 W）— 2.1
7. 0922-MF-am-1020-SourcePhotonics.pdf p14 — 212.5 GBaud 400G/λ 眼图 — 判断2
8. 0923-MF-00-Marvell与Ciena与Arista与Oracle连拍.pdf p53 — 3.2T OSFP 8×425G 与 425G PAM4 眼图 — 判断2
9. 0920-am-Su2-A-04-NTT.pdf p11 — 4ch×400/448G 薄膜 EML 眼图与密度指标 — 判断2/2.2
10. 0920-pm-Su4-I-03-Lumentum（笔记02）p7 — Scale-out 技术选项矩阵（InP/TFLN/SiPh）— 2.2/分歧5.2
11. 0924-PDP-A-6-NokiaBellLabs与上海科技大学-440GBaudPAM单光电二极管接收实现每通道净比特率超800Gbps.pdf p2 — IM-DD 速率 vs 波特率总览，827 Gb/s — 判断3/4章 #1
12. 0920-pm-Su4-A-05-NICT-光域处理替代DSP.pdf p9 — IM/DD 与相干的可用带宽 vs 距离曲线 — 判断3/分歧5.3
13. 0922-Tu3-A2-香港中文大学-24x432Gbps每波的全光均衡实现免DSP光互连.pdf p12 — 与光均衡/先进 DSP 的对比图 — 判断3
14. 0920-pm-Su3-I-03-Arista-交换机侧的选择.pdf p3 — 448G 电接口调制格式带宽表与插损曲线 — 2.3
15. 0922-MF-am-1020-SourcePhotonics.pdf p18 — CW 激光器功率路线表（70→400 mW）— 判断4
16. 0920-am-Su2-A-02-Quintessent-量子点梳状光源.pdf p12 — 200 mW 8λ 梳 + booster SOA — 判断4
17. 0920-am-Su1-A-05-Columbia-片上光源与系统.pdf p9 — 窄快 vs 宽慢，梳驱动 DWDM 约 100× — 分歧5.2
18. 0920-pm-Su3-A-04-OrioleNetworks-数据中心光交换.pdf p9 — OCS 交换时间+重锁定对吞吐条形对比 — 判断5/分歧5.6
19. 0923-We-F-00-标准化专场II连拍.pdf p60 — OCS+Lumentum 1.6T 收发器 BER 曲线 — 判断5
20. 0921-Mo3-A3-KDDIResearch-无DSP可插拔能否用于光交换.pdf p13 — JCT 与重构策略、零流量窗口 — 判断5/分歧5.6
21. 0922-Tu1-E4-OneTouch-薄膜钽酸锂8x8光电路交换.pdf p11 — 静态功耗随端口数对比 — 判断5
