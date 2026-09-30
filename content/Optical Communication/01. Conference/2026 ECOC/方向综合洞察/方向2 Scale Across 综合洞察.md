---
title: "方向2 Scale Across 综合洞察"
tags:
  - ECOC2026
  - 综合洞察
---

# 方向2：数据中心 Scale-across（FST全谱转发器、多rail、ZR/ZR+/CL、跨楼/园区/区域DC网络需求与架构）

索引简写说明：〔文件名简写 pN〕，页码为对应PDF内页码；"0920-Su3Su4-A全场扫描"指 0920-pm-Su3+Su4-A-00-全场-A1下午全场扫描；"0923-MF连拍"指 0923-MF-00-上午连拍；"0923-MF-Marvell等连拍"指 0923-MF-00-Marvell与Ciena与Arista与Oracle连拍。口径标注：自报=讲者自报，仿真，实验，现网，预测，OCR=笔记标注OCR/看不清/存疑。

## 0. 一句话结论 + 5条核心判断

**一句话结论：** Scale-across 的部署单位正从"波长"转为"光纤对"，相干可插拔（800ZR+ 量产、1.6T ZR/ZR+ 与 Coherent-Lite 跟进）负责单波长成本与功耗，全谱转发器（FST）+ 多rail线路系统负责光纤对/机房/功耗的规模化，空芯光纤（HCF）与 OCS/OTN 协议层则从时延与利用率两端争取跨楼到区域尺度的训练效率；瓶颈已从模块转移到线路系统、光纤数量与热设计。

**判断1：需求已从"DCI 的一个增量"变成"云可插拔带宽的主体"，且由线路系统而非模块决定成本结构。**
- Cignal AI（预测）：scale-across 占云可插拔带宽比例 2025 年 5%，2030 年 72%，2028 年超过 metro/前端 DCI；2030 年 scale-across 支出 8.7B USD，线路系统占 55%（2025 年 32%，累计过半；Raman 约占累计支出五分之一）；线路系统部件交期 12–18 个月，产能受 InP 晶圆限制〔0922-MF-am-1140-CignalAI p7, p8, p9〕。
- 机制：路由变长、1600ZRx 压低每比特相干价格、Raman 普及；模块 \$/G 下降（可插拔现低于 \$6/G，2027 年降至 \$5/G 以下）而放大器/泵浦/线路系统价格持平或上涨〔0922-MF-am-1140-CignalAI p6, p8〕。
- 客户侧印证：Google 自报十年光学创新使类 scale-across 网络功耗降约 90%，但线路系统功耗几乎不变，现占总功耗预算约 50%〔0920-am-Su2-B-01-Google p4〕。

**判断2：FST + 多rail 是"光纤对"时代的架构答案，收益以设备数、机房数、功耗三个量级表达（均为厂商自报）。**
- Ciena：16 对光纤下被管设备 192→32（-84%），机架单元约 -75%，功耗约 -50%〔0920-pm-Su4-C-04-Ciena p3〕；传统 22 个机房 vs 多rail 1 个机房，转发器每光纤对 60–120 个插件 vs 全谱转发器每光纤对 1 个线路端口〔0920-am-Su2-B-02-Ciena p8〕。
- Google HyperRail：每站单 ILA 机房、约 80% 功耗下降，来自非制冷多芯片泵浦与元件共享〔0920-am-Su2-B-01-Google p5〕。
- Huawei：FST 单系统 25.6T/光纤（C96），C96+L96 时 51.2T；4-Rail OA @1U 集成度提高 75%〔0920-pm-Su4-C-03-华为 p5〕。三家的机制一致：以光纤对为交付粒度，把 rail 数从 ~10 推到 >100。

**判断3：相干向短距渗透的分界由色散与延迟预算决定：>10 km 用 C 波段 ZR/ZR+，2–10 km（至 20–40 km 园区）用 O 波段 Coherent-Lite；分界线之争的核心是 O 波段 IM/DD 能否用光域均衡突破色散壁垒。**
- Marvell：Scale-across >10 km 用 1.6T ZR/ZR+，2–10 km+ 用 O 波段 Coherent-Lite 1.6T|3.2T〔0920-pm-Su4-A-01-Marvell p5〕；Acacia：IMDD 200G/lane 极限约 10 km，400G/lane 超过 2 km 需相干〔0920-pm-Su4-A-03-Acacia p5〕。
- NICT/UCLA（学术反方）：224 Gbaud 下 O 波段 2 km 后可用带宽 IM/DD FFE 仅约 45%；若 1 抽头光延迟线等光域均衡打破信道零点，则 IM/DD 可延伸；否则 Coherent-lite 主导 2 km 以上〔0920-Su3Su4-A全场扫描 p134, p147〕。
- 园区 FEC 必须为专用码：目标延迟 50–75 ns，BCH(126,110) 49–55 ns；"不要在 10 km AI 链路上用 OFEC"〔0920-pm-Su4-A-04-Nokia p12〕。

**判断4：功耗与热是相干可插拔在 1.6T 的硬约束，形态将分叉为风冷 QSFP-DD/OSFP（<45 W 天花板）与液冷 XPO。**
- Google：400G ZR++ <20 W，800G ZR++ <30 W，1.6T ZR++ <45 W，风冷天花板约 45 W"可行但处于极限"〔0920-am-Su2-B-01-Google p7〕。
- Ciena 预测：800ZR/ZR+ 约 25–31 W（2025），1600 ZR/ZR+ OSFP 约 34–42 W（2027，预测，读图）〔0920-am-Su2-B-02-Ciena p7〕；Nokia：ZR 级路由器笼内 28–40 W〔0920-pm-Su4-A-04-Nokia p126（扫描件）〕。XPO 12.8T：ZR 300 W/24 pJ/bit，CL 250 W/20 pJ/bit〔0923-MF-Marvell等连拍 p29〕。
- 机制：128 个 1600G-ZR 模块的 204.8T 交换机需 5 kW；XPO 50V 母线与液冷使单模块可到 500W（部分被遮挡）〔0923-MF-Marvell等连拍 p26〕。

**判断5：HCF 在 DCI 的价值已由"低损耗"转为"时延 + 无非线性 + 可用 ZR"，但量产、成本、熔接与 OTDR 生态仍是硬缺口，至少 12–24 个月内是选择性部署而非默认。**
- 现网/实验：Azure 全 C 波段 64×400G ZR、3 跨 427.97 km HCF，BER 低于 1.25×10^-2 限（记录，实验）〔0922-Tu3-H4-Azure p12, p13〕；PolyU/YOFC 20 km 支撑管 HCF 上 32×50 GBaud PAM4，入纤 31 dBm 下 BER 几乎无劣化，50 dB CUT 预算（实验）〔0921-A1厅连拍-Mo3-A2 p14〕。
- 时延价值（仿真）：Corning 显示 HCF 最多 +25% 计算-通信重叠，同等时延下可达距离约 +50%〔0924-Th1-G1-Corning p9〕。
- 约束（领纤自报）：HCF 价格 >\$3000–5000/km vs SMF \$20–40/km，每预制棒数十 km vs 数千 km，2025 年前后累计产量约 83 km〔0921-Mo3-B1-领纤 p13, p60〕。

## 1. 需求与网络架构

### 1.1 需求数字（客户/运营商/分析机构口径）

| 类别 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| 流量增速 | 相对基线：前端 DCI 7x，scale-up（数百 GPU）504x，scale-out（50K GPU）56x，scale-across（1M+ GPU）14x；"当前模型已到单数据中心可训练的极限"（来源 Cisco, OFC/OSA Executive Forum 2026） | 引用/预测 | 〔主分析师笔记04-Marvell p3〕 |
| 单站点功率 | 单 DC 电力 50–300 MW（引 Microsoft OFC2026 Workshop）；下一代 LLM 训练需约 1–5 GW；Google 俄亥俄+爱荷华（4 DC，80 km）、NVIDIA（3 DC，40 km）等规划 | 引用 | 〔0923-We5-B-中兴 p4〕 |
| 带宽估算 | 数据并行：GPT-4 1.8T 有重叠 >3.1 Tb/s，无重叠 61.7~308.8 Tb/s；10T 模型有重叠 >17.3 Tb/s，无重叠 343.1 Tb/s~1.7 Pb/s（表中行标签"GPT-3 3T"疑为标注错误，照录） | 仿真估算（ZTE） | 〔0923-We5-B-中兴 p5〕 |
| 园区结构 | 每 AI 园区 4–12 栋楼；1.6T 下园区间隙 2–40 km；光纤时延 5 μs/km；百万级 XPU 集群；约 190 GW 超大规模容量已宣布；"园区光纤数量已成危机" | Nokia 自报/引用 | 〔0920-Su3Su4-A全场扫描 p111〕〔0920-pm-Su4-A-04-Nokia p1（核心主张）〕 |
| 系统规模 | 每站点数百对光纤（C&L），每对 64×800G，即 20 Pb/s 用例；传统 DCI ~200 Tb/s → scale-across >10 Pb/s，扩容粒度 per wavelength → per fiber，rails ~10 → >100 | Ciena/Huawei 自报 | 〔0920-am-Su2-B-02-Ciena p10〕〔0920-pm-Su4-C-03-华为 p5〕 |
| 模块出货 | 800ZRx 全球已出货 >100,000 端口（2Q26）；Acacia 唯一季度出货 >25,000 个 800ZR+ 的供应商；某超大规模发布预测 2026 年 200,000+ 800ZRx，2027 年 >350,000；Acacia 自报累计 >75,000 个 800ZR+ | Cignal/自报 | 〔0922-MF-am-1140-CignalAI p10〕〔0920-pm-Su4-A-03-Acacia p3〕 |
| 市场 | 相干模块 2026 年近 7B USD，2030 年近 10B USD；1600ZRx 2030 年 2.9B USD 成最大单一类别；2026 年预计 >200k 800ZR 级单元；800G ZR 级 2025–2029 CAGR 145% | 预测 | 〔0922-MF-am-1140-CignalAI p6, p7〕〔0920-pm-Su4-A-04-Nokia p6〕 |
| 运营商 | BT 核心流量 >34 Tbit/s；AI 流量尚无显著体现；推理约"一波长"级用现有 ROADM，训练需 scale-across | 自报 | 〔0920-am-Su1-C-00-上半场速记 p19, p20, p25〕 |

### 1.2 距离分层（各家口径对照）

| 机构 | 分层 | 索引 |
|---|---|---|
| Marvell | Scale-across：>10 km C 波段 1.6T ZR/ZR+；2–10 km+ O 波段 Coherent-Lite 1.6T/3.2T；scale-out 100 m–2 km PAM4；scale-up 10–100 m | 〔0920-pm-Su4-A-01-Marvell p5〕 |
| Nokia | scale-out 100 m–10 km，约 2 km 起 Coherent-lite（OCS 损耗预算在此出现）；scale-across 10–1000+ km，ZR/ZR+，含园区边缘；CL 2 km/OCS 4–8 dB，CL 10 km 约 6.3 dB，CL 园区 WDM 20 km 12–14 dB（8 通道 O-band） | 〔0920-pm-Su4-A-04-Nokia p4〕〔0920-Su3Su4-A全场扫描 p123〕 |
| XPO/Marvell 系 | scale-across 园区 2–20 km，城域 100+ km；scale-out 500 m–2 km | 〔0923-MF-Marvell等连拍 p23〕 |
| OVHcloud | <10 km 无需线路系统（长距可插拔如 2x400G LR，多对直连光纤，无放大器、无复用器）；>10 km 800G ZR/ZR+ + 线路系统（WSS、L/C 带放大、Raman、ILA，跨段约 100 km） | 〔0920-am-Su1-C-00-上半场速记 p15, p16〕 |
| Oracle OCI | 区域 DWDM 互连约 60 km 跨段，400ZR→800ZR→1600ZR；参与 1600ZR/1600ZR+/CMIS，已启动 1.6T 相干可插拔 MACsec 支持项目 | 〔0920-pm-Su3-A-03-Oracle p12〕 |
| Ciena | Campus 10–20 km，Metro 100 km，Backbone 2,000 km+，Submarine 10,000 km+ | 〔0923-MF连拍 p66〕 |
| NICT/UCLA 图 | DR <500 m，FR <2 km，LR <10 km，ER <40 km，ZR <120 km，ZR+ >120 km；园区/短距 DCI 约 20 km | 〔0920-Su3Su4-A全场扫描 p130〕 |
| OIF CMIS | 应用覆盖：DC 内单模 500 m 与 2 km；园区单模 10 km；户外相干 40 km→3000+ km | 〔0923-MF连拍 p56〕 |

### 1.3 架构演进

1. **拓扑融合**：OVHcloud 用 FBOSS 新 DC 产品模糊 DCN/DCI 边界，形成区域 Fabric 环，环内容量为环间的 10 倍；"一组区域共享一套服务栈"，故障域从 region 变为 ring（自报，OVH）〔0920-am-Su1-C-00-上半场速记 p14, p17〕。
2. **多站点变一个逻辑集群**：中国电信 DCI 场景：训练效率 >97%，最多 3 个跨城 DC、最多 1024 GPU（现网/测试床，自报）〔0923-We-F-00-标准化专场II p31〕。Huawei 实网分布式训练/推理测试：首末层在本地卡、中间层放云端，部分场景算力效率损失 <5%（现网测试，自报）〔0920-pm-Su4-C-03-华为 p7〕。
3. **光层可重构**：中国电信提出 OCS 从 DC 内扩展到城域，Type I 环（每环通道 1 波长/光纤，每节点 O/E/O）与 Type II Mesh（约 M²/8 波长/光纤，M=5 示例）〔0923-MF-中国电信 p10〕；KDDI 的 OCS 网关使 25 个集群（5×5）全连接仅需 12 芯光缆〔0922-Tu1-G1-KDDI p5〕。
4. **站点形态**：Ciena ILA 机房 Existing → Next Gen Large → X-Large：机架 4–10 → 9 → 18；EDFA/Raman rails 40/40 → 864/432 → 1,728/864；站点功率 30–50 kW → 200 kW → 400 kW；Next Gen 最多 12 个 X-Large 机房，每站点最多 20,736 个 EDFA rails，供电最高 4 MW/5,000 A（自报，条件：3P、480V）〔0920-pm-Su4-C-04-Ciena p2〕。
5. **边缘/运营商**：Telefonica 提出部分面向 AI 的用例只有拥有边缘计算资源的电信运营商才能提供，驱动力为变现、网络资源优化、数据主权；解耦推理需"高容量、零丢包"连接（架构示意，无定量）〔0920-am-Su1-I-01+02-Telefonica p9, p14（OCR）〕。
6. **协议层**：跨区域 RDMA 使 RTT 变长、流控与丢包检测变慢，限制 MFU；Huawei OTN-Proxy 以 XPU proxy 方式支持 >100 Tb/s，使吞吐与 DCI 距离（0–500 km）基本无关（动机场景 240 km、RTT 约 2.5 ms；曲线小字数值不可读）〔0920-pm-Su4-C-03-华为 p2, p6〕。
7. **时延物理限**：Corning：光纤时延 D/v 与带宽无关，NIC 升至 400G–1.6T 后串行化项变小，光纤时延成为数据并行重叠的主导因素〔0924-Th1-G1-Corning p5〕。

## 2. 技术路线与关键指标

### 2.1 相干 DSP 代际与 ZR/ZR+/CL 分层

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Nokia | 400ZR/ZR+ | ~60 GBd DP-16QAM CFEC，7 nm 量产 | 自报 | 〔0920-Su3Su4-A全场扫描 p120〕 |
| Nokia | 800ZR/ZR+ | 118–135 GBd DP-16QAM+PCS，OFEC，3 nm 大规模爬坡 | 自报 | 同上 |
| Nokia | 1600ZR | ~236 GBd DP-16QAM 单载波，OFEC，约 300 GHz 频隙，80–120 km DCI，IA ~Q2 2026 | 路线图 | 〔0920-pm-Su4-A-04-Nokia p13〕〔0920-Su3Su4-A全场扫描 p120〕 |
| Nokia | 1600ZR+ | 252 GBd（2×~126），PCS-16QAM，2 FDM，至约 1000 km，复用 800G 模拟，IA ~Q3 2026 | 路线图 | 同上 |
| Nokia | 1600CL | ~226–~247 GBd（待定），低复杂度 BCH 类 FEC，延迟 50–75 ns，园区 2–40 km | 路线图 | 〔0920-Su3Su4-A全场扫描 p120〕 |
| Nokia | 园区 FEC 三选项（800G 10 km） | BCH(126,110)：247.3 GBd，49–55 ns，RSNR 13.7 dB，模块功耗 +1.5–3%；Compressed FEC：239.1 GBd，70 ns，13.8 dB，0%；Braided：226.7 GBd，70–72 ns，14.3 dB，+1.5–3% | 自报 | 〔0920-pm-Su4-A-04-Nokia p12〕 |
| Marvell | Libra 800G ZR/ZR+ DSP | 声称业界首个集成 MACsec 的 800G ZR/ZR+ | 自报 | 〔0923-MF-Marvell等连拍 p3〕 |
| Marvell | Electra 1.6T ZR/ZR+ DSP | 声称首款 2 nm 1.6T ZR/ZR+ DSP，集成 MACsec | 自报 | 〔0923-MF-Marvell等连拍 p4〕 |
| Ciena | WaveLogic 6 Nano/Extreme | 见 2.3 | 自报 | 〔0923-MF连拍 p69, p70〕 |
| Ciena | Coherent-Lite OSFP | 2×1.6T，BER <1E-24（压缩 FEC）；每 3.2 Tb/s、20 km 链路需 1.3 Gb ARQ 存储；10T 参数数据集在 BER=1E-12 下丢 160 个包 | 自报 | 〔0920-pm-Su4-A-02-Ciena p5, p6〕 |
| Ciena | 12.8T Coherent-Lite XPO | 3.2T CL ASIC，双 1.6T ICR，双 1.6T MZM/驱动，双 O 波段 DFB；功耗 <240 W（液冷 XPO 可承受 400 W），BER <1E-24 | 展示/自报 | 〔0920-pm-Su4-A-02-Ciena p7〕 |

### 2.2 功耗、热与形态

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Google | 相干可插拔功耗 | 400G ZR++ <20 W；800G ZR++ <30 W；1.6T ZR++ <45 W，风冷天花板约 45 W | 自报 | 〔0920-am-Su2-B-01-Google p7〕 |
| Ciena | 可插拔功耗趋势 | 800 ZR/ZR+ 约 25–31 W（2025）；1600 FR/CL OSFP 约 27–30 W（2026 预测）；1600 ZR/ZR+ OSFP 约 34–42 W（2027 预测，读图） | 预测 | 〔0920-am-Su2-B-02-Ciena p7〕 |
| Ciena | 链路功耗阶梯 | 全重定时 30 W（18.5 pJ/bit）；LRO 20 W（12.5）；LPO 10 W（6.5）；NPO 8 W（5）；CPO 5 W（3） | 自报 | 〔0920-am-Su2-B-02-Ciena p4〕 |
| Marvell/XPO | 12.8T XPO（64×200G/lane） | ZR 100 km+/300 W/24 pJ/bit；CL 10–20 km/250 W/20；DR8-LRO 500 m/128 W/10；DR8-LPO 500 m/80 W/6；VCSEL 20–30 m/65 W/5 | 自报 | 〔0923-MF-Marvell等连拍 p29〕 |
| XPO | 密度 | 一个 XPO 替换 8 个 OSFP，前面板密度约 4X；1U 内 16 XPO 提供 204.8T；128 个 1600G-ZR 需 5 kW | 自报 | 〔0923-MF-Marvell等连拍 p24, p25, p26〕 |
| Aperion（XPO 内） | EDFA+MUX/DEMUX | 800G Coh ZR 跨段 80 km→180 km；1528–1567 nm；饱和输出 >23 dBm；功耗 <30 W | 自报（p30 部分表看不清） | 〔0923-MF-Marvell等连拍 p30〕 |

### 2.3 FST 与多rail 线路系统

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Ciena | FST（16 对光纤） | 被管设备 192→32（-84%）；机架单元约 -75%；功耗约 -50%；调制解调器 200→300→400 Gbd 级（原文如此）；WL2 100G（2008）→WL6 1600G（2024） | 自报 | 〔0920-pm-Su4-C-04-Ciena p3〕 |
| Ciena | 部署对比 | 传统 22 机房 vs 多rail 1 机房；转发器每光纤对 60–120 个插件 vs FST 每光纤对 1 个线路端口 | 自报 | 〔0920-am-Su2-B-02-Ciena p8〕 |
| Ciena | Hyper Rail | PMO 4 rails/机架 → FMO 128 rails/机架；EDFA 密度 32x，EDFA Raman 密度 16x，功率 4x；每卡 4 个 C&L rails；管理流量 32x | 自报 | 〔0920-pm-Su4-C-04-Ciena p4〕 |
| Ciena | RLS C&L HyperRail 终端 | 紧凑机箱 16 个 C+L 光纤对；51.2T C&L FST 示例：8 个 1.6T 调制解调器/服务模块 ×4，经 2 个 6.4T CPO，共 16x 光纤 | 自报 | 〔0920-am-Su2-B-02-Ciena p10〕〔0923-MF连拍 p77〕 |
| Ciena | 转发器 vs 可插拔（Metro DCI） | 800G 可插拔（WL6 Nano）51.2 Tb/s（64×800G，150 GHz）vs 1.6T 转发器（WL6 Extreme）76.8 Tb/s（48×1.6T，200 GHz），+50% | 自报 | 〔0923-MF连拍 p70〕 |
| Google | HyperRail | 每站单 ILA 机房，约 80% 功耗下降；从 4 rail 到 8 rail 及更多 | 自报 | 〔0920-am-Su2-B-01-Google p5〕 |
| Huawei | FST + 4-Rail OA | 25.6T/光纤（C96）；C96+L96 时 51.2T；4-Rail OA @1U 集成度 +75%，达到单 rail 级可靠性 | 自报 | 〔0920-pm-Su4-C-03-华为 p5〕 |
| ZTE | FST + OMC DCI-BOX | 产品方向：FST+OMC 架构的高容量高密度 DCI-BOX、1.6T ZR/ZR+/CFP2、S+C+L 收发器（客户有兴趣时） | 自报 | 〔0923-We5-B-中兴 p15〕 |

### 2.4 宽带与多频段（C+L、S+C+L、O 波段）

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| ZTE（含联通研究院） | 19.1 THz S+C+L 800G CFP2 | 混合 TFLN/SiPh COSA + 超宽带 SOA；DSP 137 GBd 800G PS-16QAM；输出 >0 dBm，Tx OSNR >35 dB（峰值 38.3 dB）；节省光纤 74.8%（讲者原文）；TFLN 调制后仅约 -12~-13 dBm，低于 ZR/ZR+ 要求的 -8 dBm 下限，故加 SOA；非线性代价 <0.5 dB | 实验 | 〔0923-We5-B-中兴 p10, p12, p14〕 |
| 中国电信 | 多频段路线 | C+L 已部署 ~12 THz（400G）；S+C+L 现网试验 ~17–20 THz；全频段实验测试 >37 THz；1.6T 实验测试 200 GBd+ DP-PCS-64QAM；800G 现网试验 ~140 GBd DP-PCS-16QAM | 现网/实验（自报） | 〔0923-MF连拍 p7〕〔0923-MF-中国电信 p6〕 |
| KDDI | O 波段 BDFA 传输 | 连续 16.4 THz O 波段，80.4 km 超低损耗光纤，全 BDFA 链；BDFA 超宽增益版 17.6 THz，增益 20+ dB（引自旧作） | 实验（引用） | 〔0922-Tu1-G1-KDDI p15, p16〕 |
| KDDI | 波段信道数（100/150/300 GHz 栅格对应 400G/800G/1600G） | C：48/32/16；CL：96/64/32；SCL 与 O：144/96/48 | 计算表 | 〔0922-Tu1-G1-KDDI p14〕 |
| KDDI | 12 芯光纤 O 波段 | 替代 MPO-12，>20 km；12 路 SDM 最多支持 5x5=25 个集群 | 实验（引用） | 〔0922-Tu1-G1-KDDI p20, p30〕 |
| Cignal | 现状判断 | C+L 已是基本配置；空芯/S 波段/多芯未规模部署 | 分析师 | 〔0922-MF-am-1140-CignalAI p8〕 |

### 2.5 HCF 在 DCI 中的传输结果与器件生态

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Microsoft Azure | 400G ZR 全 C 波段 3 跨 HCF | 64×400G，427.97 km（163.9/152.07/112 km，IL 32.4/30.5/27.8 dB，GLA 0.042/0.073/0.048 dB/km）；BER 低于 1.25×10^-2 限，GLA 处接近限；对比此前 151 km SMF（ECOC 2021）与 107.5 km HCF（OFC 2026） | 实验（记录声明） | 〔0922-Tu3-H4-Azure p9, p12, p13〕 |
| Microsoft Azure | HCF 汇总 | >100 km 直线 HCF：离线最高约 140 Tb/s（<100 km）；实时约 50 Tb/s @~100 km、约 25 Tb/s @~200 km、约 10 Tb/s @~250 km、约 25 Tb/s @~440 km；200.5 km 无中继 32×800G（OFC 2025）；3 跨 442.66 km 32×800G（OFC 2026） | 实验/引用 | 〔0920-pm-Su4-B-05-Azure p3, p10〕 |
| Microsoft Azure | ZR vs 长途转发器 | 400G/λ vs 800G/λ；25.6T 需 64 vs 32 波；约 60 GBaud vs 140+ GBaud；cFEC 1.25e-2 vs SD-FEC 2.4e-2；放大最大距离约 120 km vs 1000+ km；TX 约 -10 dBm vs >0 dBm；ZR 模块 DSP 占功耗 49% | 自报 | 〔0920-pm-Su4-B-05-Azure p6〕〔0922-Tu3-H4-Azure p8〕 |
| Microsoft Azure | 器件需求 | 熔接损耗 <0.1 dB、<97 s；连接器反射 <-60 dB；OTDR 动态范围约 50 dB、分辨率约 1 m；25 dBm 发射、NF 5 dB、OSNR 25 dB/0.1 nm 时链路损耗约 35 dB（读图） | 自报 | 〔0920-pm-Su4-B-05-Azure p8, p9〕 |
| PolyU/YOFC | 32 波 IM-DD 20 km 支撑管 HCF | 32×50 GBaud PAM4，入纤 31 dBm，−19 dBm 接收达 15% O-FEC 门限对应 50 dB CUT 预算，总毛速率 3.2 Tb/s（混合加载条件：CUT 31 dBm，其余 31 波各 13 dBm）；SSMF 最佳入纤约 9 dBm（单波）/5 dBm（32 波） | 实验 | 〔0921-A1厅连拍-Mo3-A2 p13, p14〕 |
| PolyU/YOFC | SBS | SSMF 后向散射在入纤约 11 dBm 以上快速上升；HCF 至 31 dBm 线性增长 | 实验 | 〔0921-A1厅连拍-Mo3-A2 p12〕 |
| Nokia Bell Labs + PolyU | PDP-C-6 免 DSP 相干 | 10 km 支撑管 HCF，DP-16QAM，140 GBaud 时 NGMI 超过 21% 级联 FEC 门限 0.857；1.12 Tb/s/λ 毛速率，净 925 Gb/s，毛速率-距离积 11.2 Tb/s·km/λ；OPLL 与 DCPR 在 120/130/140 GBaud 相当；两只窄线宽激光器（<100 Hz、<1 kHz）锁定成功，测试的商用 ITLA 无法锁定 | 实验（PDP） | 〔主分析师笔记05 PDP-C-6 p23, p26, p29〕 |
| Linfiber | HCF 状态 | 0.052 dB/km（40 km，IT-DNANF）；DCI 变体典型 0.1 dB/km，色散 <5 ps/nm/km；长途大芯变体典型 0.07 dB/km 但微弯更严；DCN 变体 <0.5 dB/km@1310 nm | 自报 | 〔0921-Mo3-B1-领纤 p12, p57, p58, p56〕 |
| Huawei | HCF 现状 | 插入损耗已低于实芯 SMF，已在 DCI 和金融专线商用；挑战：气体吸收峰（S/C/L）、IMI、弱瑞利散射（约 -30 dB）致 OTDR 难、拉丝长度有限 | 自报 | 〔0920-pm-Su4-C-03-华为 p5〕 |
| Corning | HCF 时延收益 | 传播时延 SMF 5.0 µs/km，HCF 低约 33%（节省 1.7 µs/km）；仿真见 2.7 | 仿真 | 〔0924-Th1-G1-Corning p5〕 |

### 2.6 短距：Coherent-Lite vs IM/DD 与色散

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| Acacia | 相干短距化论证 | IMDD 200G/lane 极限约 10 km；400G/lane >2 km 需相干；IEEE 800GBASE-ER1（20 km）与 ER1-20（图上写 40 km）沿用 ZR 技术；1600G/lane 相干可支持 >2 km 校园 DCI | 自报 | 〔0920-pm-Su4-A-03-Acacia p5〕 |
| Acacia | 路线时间线 | 0–2 年：200G/lane，CPO 试点；2–5 年：400G/lane，NPO/CPO 与可插拔并存，Coherent-lite 园区；5–10 年：800G/lane，数据中心内相干 | 自报 | 〔0920-pm-Su4-A-03-Acacia p9〕 |
| NICT/Hamamatsu/UCLA | O 波段色散 | G.652.D 零色散波长均值 1312 nm（标准差 2 nm），斜率 0.086 ps/(nm²·km)；224 Gbaud 下 2 km 后可用带宽 IM/DD FFE 约 45%，FFE+1 抽头 DFE 约 70%；可用 O 波段频谱 2 km 后 <45%，20 km 后 <5% | 分析/仿真 | 〔0920-Su3Su4-A全场扫描 p131, p134, p141〕 |
| NICT/UCLA | 光域均衡 | 1 抽头光延迟线：C 波段 100 Gbaud 超 80/100 km"创纪录低 DSP 复杂度"（OFC'24，作者自述）；成对传输在光纤束 40 km 达约 HD-FEC 极限（OFC 2025） | 实验（引用） | 〔0920-Su3Su4-A全场扫描 p144, p146〕 |
| Ciena | 零错误论点 | 压缩 FEC BER <1E-24；取消大 ARQ 存储与"延迟三倍" | 自报 | 〔0920-pm-Su4-A-02-Ciena p5〕 |
| Nokia | 三约束 | ZR 级路由器笼内 28–40 W；园区 FEC 50–75 ns；2 km 处 OCS 损耗约 8 dB；scale-across 光纤为毫秒级，FEC 纳秒无所谓 | 自报 | 〔0920-Su3Su4-A全场扫描 p126〕 |

### 2.7 OCS + OTN 与跨域训练实测/仿真

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| KDDI | OCS 网关多集群测试床 | 4 个虚拟化集群，间距 20–40 km；集群 A、C 各 2 块 H100 + 2 块 NIC，波长预配置 400G ZR 做 RDMA-over-Ethernet；RDMA 时延 = 14.514 + 9.836x µs（x 为 km，0–40 km）；All-to-All/All-Reduce 在 0/20/30 km 作业完成时间几乎无差异 | 实验 | 〔0922-Tu1-G1-KDDI p7, p8, p9, p10〕 |
| Huawei | OTN-Proxy | 支持 >100 Tb/s，作为 XPU proxy；带 proxy 时吞吐与 DCI 距离（0–500 km）基本无关（曲线小字数值不可读） | 自报 | 〔0920-pm-Su4-C-03-华为 p6〕 |
| Huawei | 实网分布式训练/推理 | 首末层本地卡、中间层云端；部分场景算力效率损失 <5% | 现网测试 | 〔0920-pm-Su4-C-03-华为 p7〕 |
| Huawei | OCS+SW super-pod | 动态时延 500 ns+；网络时延 -30%、推理性能 +10%；super-pod 扩展至 16K | 自报 | 〔0920-pm-Su4-C-03-华为 p4〕 |
| 中国电信 | 跨城多 DC 训练 | 训练效率 >97%，最多 3 个跨城 DC、1024 GPU；WSON 50 ms：8 节点实验室 + 4 节点现网，最大路由长度 640 km，恢复 <50 ms，单波 400/800 Gb/s | 现网/实验 | 〔0923-We-F-00-标准化专场II p31〕 |
| 中国电信 | OCS 替代 super-spine | 无光模块使故障率降低 17%+；相比三层胖树节省约 20% 网络功耗；DCA 时延本地降 30–50%、市内 20–40%、省际 8–16%（基线条件未标） | 自报 | 〔0923-We-F-00-标准化专场II p29, p30〕 |
| Corning | 计算-通信重叠仿真 | ASTRA-sim；GPT-3 13B/175B，256/2048/8192 GPU，A100/H100，DC 间距 0.3–1000 km，DC 间带宽 100 GB/s；10 km 内 η≈1；H100 约 10–30 km 起下降，A100 约 100 km 以上；1000 km 训练时间相对 0.3 km 基线：H100 约 26×、A100 约 4×（175B，8192 GPU）；HCF 将 H100 惩罚 26×→17×；Δη 峰值 13B A100 约 0.24（约 100 km） | 仿真 | 〔0924-Th1-G1-Corning p6–p10〕 |

### 2.8 互操作与管理（CMIS、MACsec、P2MP、域边界）

| 机构 | 方案 | 关键指标（带条件） | 口径 | 索引 |
|---|---|---|---|---|
| OIF/Cisco | CMIS 增强固件管理 | 固件包=YAML 元数据（含 VendorName、VendorPN、HW Rev、目标 FW、SHA-512）+ .bin；向后兼容 CMIS 5.x；与 OpenConfig 联动；ECOC 演示 CMIS 5.4 模块含 Cisco-Acacia 800G ZR OSFP 与 Genuine Optics 1.6T OSFP；CDB 50h/51h | 演示 | 〔0923-MF-OIF-CMIS p6, p8〕〔0923-MF连拍 p61〕 |
| OIF/Cisco | CMIS 展望 | 1.6T（200G/lane）、ILT、Inner FEC、Symbol Muxing、MACsec 引擎管理、CMIS-sec、XPO 与 Open CPX | 路线图（OCR） | 〔0923-MF连拍 p62〕 |
| KDDI | DSCM P2MP 现网 | ~170 km，5 段，2 hub + 4 leaf；2×100G 16QAM P2MP 与 DP-QPSK P2P 共传；15 个 C 波段点接收 OSNR 均高于 17 dB 阈值；72 h L2 无丢包；叶节点距离差 0/20/40/60/80 km 均 link up；在网重新分组无误码 | 现网 | 〔0923-We2-A3-KDDI p4, p5, p6〕 |
| NTT | OAO 波长转换器 | 无 DSP、CFP2 兼容；OSNR 代价 T1 oFEC 约 1.7 dB、T2 oFEC 2.6 dB，主要由收发机特性决定；跨域演示（196.1 THz ↔ 193.4 THz，各 75 km）pre-FEC BER 均低于阈值，裕量 0.29–0.41 decade；频偏检测约 ±75 GHz（读图估计） | 实验 | 〔0924-Th1-H5-NTT p4, p5, p6〕 |

## 3. 厂商与客户态势

### 3.1 AIDC/云客户与运营商

- **Google Cloud**：功耗是终极约束，转向 HyperRail 多rail 线路系统，以"二值化"（够用 SNR）可插拔闭合追求最低 TCO；不可妥协的是覆盖距离与路由器利用率；1.6T ZR++ <45 W 为风冷天花板〔0920-am-Su2-B-01-Google p4, p5, p7〕。
- **Microsoft Azure**：主推 HCF + 400G ZR 跨长距（3 跨 427.97 km，记录），要求熔接 <0.1 dB、OTDR 动态范围约 50 dB、连接器反射 <-60 dB；论点为降 CapEx/OpEx、节省机架、简化云原生光层〔0922-Tu3-H4-Azure p13〕〔0920-pm-Su4-B-05-Azure p7, p9〕。
- **Oracle OCI**：区域 DWDM 约 60 km 跨段，400ZR→800ZR→1600ZR；已启动 1.6T 相干可插拔 MACsec 项目；集群 2020→2026 从 16,384 GPU 增至 131,072 GPU（8x）〔0920-pm-Su3-A-03-Oracle p2, p12〕。
- **OVHcloud**：一组区域共享一套服务栈，区域 Fabric 环；<10 km 直连长距可插拔，>10 km 800G ZR+ + 线路系统；光保护开关考虑 2027 年；IP 层保护〔0920-am-Su1-C-00-上半场速记 p14–p16〕。
- **BT**：AI 流量在消费者流量中暂无显著体现，核心流量 >34 Tbit/s，核心传输 2025 年 400G、约 2029 年 800G、2030+ 可能 1.6T；训练互联为多光纤×多波长（C+L）固定滤波器点对点 WDM，"光纤岛"，未来在转发器/CPO 与相干可插拔间选择〔0920-am-Su1-C-00-上半场速记 p19, p25, p26〕。
- **中国电信**：G.654.E 光纤 ≤0.172 dB/km、192/288 芯光缆、时延优化约 -10%；50 ms WSON、OCS 城域池化；训练效率 >97%（3 DC、1024 GPU）〔0923-MF连拍 p6, p8〕〔0923-We-F-00-标准化专场II p31〕。
- **KDDI**：OCS 网关 + 12 芯 SDM + O 波段 BDFA；DSCM P2MP 现网 170 km；Osaka Sakai 数据中心已有 PQC+QKD 混合密钥分发商用链路〔0922-Tu1-G1-KDDI p30, p22〕〔0923-We2-A3-KDDI p4〕。
- **NVIDIA**：Spectrum-X 多平面多 rail 较传统多层单 rail 节省 1.7 倍 scale-out 交换机；512K Rubin GPU、8 平面 4 rail；属 scale-out，但"多 rail"术语与 scale-across 的多rail 不同（见第 5 节）〔0921-MF-pm-1340-NVIDIA p9, p10〕。

### 3.2 设备商

- **Ciena**：FST（WL6 1600G）+ RLS C&L HyperRail；Metro 51.2T→76.8T（+50%）与海缆 +16% 的转发器论证；同时推 Coherent-Lite OSFP（2×1.6T）与 12.8T CL XPO；主张"部署单位从波长转向光纤对"〔0920-pm-Su4-C-04-Ciena p3, p4〕〔0923-MF连拍 p70〕〔0920-pm-Su4-A-02-Ciena p7〕。
- **Nokia**：DSP 套件路线（400ZR→800ZR→1600ZR/ZR+/CL），主张"按覆盖选引擎而非峰值波特率"；1830 GX Multi-Rail（Cignal 称其重夺超大规模线路系统份额并获 multi-rail 设计中标）；公开市场信号 800G ZR 级 CAGR 145%〔0920-pm-Su4-A-04-Nokia p6, p7〕〔0922-MF-am-1140-CignalAI p10〕。
- **Huawei**：FST + 多rail（25.6T/光纤、C96+L96 51.2T）、OCS、HCF、OTN-Proxy 四件套；强调算网一体〔0920-pm-Su4-C-03-华为 p5, p6〕。
- **ZTE**：19.1 THz S+C+L 800G CFP2，DCI-BOX（FST+OMC）；自称"部分场景 HCF 无收益"〔0923-We5-B-中兴 p9, p15〕。
- **Cisco/Acacia**：兼具设备商与模块商角色，见 3.3。

### 3.3 模块/器件商

- **Acacia（Cisco）**：自报 >75,000 个 800ZR+ 已发货；Cignal 称其为唯一季度出货 >25,000 个 800ZR+ 的供应商；"800ZR+ 是历史上增长最快的相干技术"（引 Cignal AI）；推 XPO〔0920-pm-Su4-A-03-Acacia p3〕〔0922-MF-am-1140-CignalAI p10〕。
- **Aperion**：XPO 内 EDFA+MUX/DEMUX，800G ZR 跨段 80→180 km〔0923-MF-Marvell等连拍 p30〕。
- **YOFC/领纤（光纤）**：YOFC 支撑管 HCF <0.1 dB/km，O 波段 HA-HCF 首次实现超短距单模 HCF；领纤 0.052 dB/km（40 km）〔0921-A1厅连拍-Mo3-A2 p7〕〔0921-Mo5-YOFC p10〕〔0921-Mo3-B1-领纤 p12〕。

### 3.4 芯片商

- **Marvell**：Libra 800G ZR/ZR+ DSP、Electra 1.6T ZR/ZR+ DSP（2 nm，均集成 MACsec，自报）；Cignal 称其错过 800ZR 早期量产；同时推 Coherent-Lite 分层与等离子体调制器（3 dB EO 带宽 990 GHz）〔0923-MF-Marvell等连拍 p3, p4, p7〕〔0922-MF-am-1140-CignalAI p10〕。
- **Nokia（DSP）**：见 3.2，DSP 代际表〔0920-Su3Su4-A全场扫描 p120〕。

## 4. 学术关键突破

| 排序 | 机构 | 论文号/文件名 | 突破点 | 数字 | 索引 |
|---|---|---|---|---|---|
| 1 | Microsoft Azure Fiber（含 Southampton 作者 Richardson） | Tu3-H4 | 全 C 波段 400G ZR 最长传输，HCF 3 跨（record） | 64×400G，427.97 km；CD 约 1,620–1,790 ps/nm（低于 OIF 上限 2,400 ps/nm）；此前 151 km SMF、107.5 km HCF | 〔0922-Tu3-H4-Azure p12, p13〕 |
| 2 | Nokia Bell Labs + PolyU（PDP） | PDP-C-6 | HCF 放宽免 DSP 相干链路距离速率积；OPLL 前向传感（PDP，首次组合） | 1.12 Tb/s/λ 毛速率、净 925 Gb/s、10 km；11.2 Tb/s·km/λ；已有免 DSP 方案均 <~750G | 〔主分析师笔记05 PDP-C-6 p29, p40〕 |
| 3 | 领纤/暨南（综述含 ECOC 2025 PDP Th03.01.1/.2） | Th03.01.1（S. Gao）、Th03.01.2（Mahadiraji） | HCF 损耗低于 SMF 理论极限（PDP/record） | 0.052 dB/km，40 km，纤芯 33.6 μm；对比 0.25 dB/km、14.8 μm 抗弯设计 | 〔0921-Mo3-B1-领纤 p12, p41〕 |
| 4 | Microsoft Azure Fiber + Southampton（PDP，引用） | ECOC PDP 2026 | "首个零色散、电信级损耗（0.2 dB/km）C 波段空芯光纤"（首次，来自 Nokia/PolyU 引文） | 112 Gb/s PAM4 56 GBd 约 15 km | 〔主分析师笔记05 PDP-C-6 p7〕 |
| 5 | PolyU/YOFC | Mo3-A2 | 20 km 支撑管 HCF 上 32×50 GBaud PAM4 IM-DD，无非线性/无 SBS 高入纤 | 31 dBm 入纤 BER 几乎无劣化；50 dB CUT 预算；3.2 Tb/s 毛速率 | 〔0921-A1厅连拍-Mo3-A2 p13, p14〕 |
| 6 | ZTE + 中国联通研究院 + ZTE Photonics Japan | We5-B | 19.1 THz 宽带 800G CFP2 收发器（TFLN/SiPh 混合 + SOA） | 输出 >0 dBm，Tx OSNR >35 dB，节省光纤 74.8%，DSP 137 GBd | 〔0923-We5-B-中兴 p12, p14〕 |
| 7 | KDDI Research | Tu1-G1 | OCS 网关多集群测试床，RDMA 时延仅增光纤时延 | 14.514+9.836x µs；20–40 km；5×5=25 集群 12 芯 | 〔0922-Tu1-G1-KDDI p7, p8, p30〕 |
| 8 | KDDI Research | We2-A3 | DSCM P2MP 现网 170 km，与 P2P 共传（首次强调运营验证） | 72 h 无丢包；ΔL 0–80 km；OSNR >17 dB 阈值 | 〔0923-We2-A3-KDDI p4, p5〕 |
| 9 | KDDI Research（旧作综述） | OFC Th4A.2 2024 | 连续 16.4 THz O 波段 SMF 传输，全 BDFA 链 | 80.4 km ULL 光纤；BDFA 17.6 THz | 〔0922-Tu1-G1-KDDI p15, p16〕 |
| 10 | YOFC | Mo5 | 首次实现小 OCD、小 MFD、超短距单模 HCF（首次） | 芯径 14 μm；10.037 km 截断，1310 nm 1.15 dB/km；30/20/15 mm 弯径 0.0013/0.0026/0.03 dB/turn；OCD 240 μm；HOMER >1000 | 〔0921-Mo5-YOFC p6, p7, p8, p10〕 |
| 11 | Corning | Th1-G1 | HCF 时延收益的首个系统级量化（仿真） | +25% 重叠；可达距离约 +50%；26×→17× | 〔0924-Th1-G1-Corning p9, p10〕 |
| 12 | NTT | We2-A2 | PPLN 带间波长转换抑制 DSF 中 PAM4 对相干的非线性；称首次量化评估 | 225 km；相对 Q -6.7 dB → 接近 0 dB | 〔0923-We2-A2-NTT p4, p6〕 |
| 13 | NTT + NEC | Th1-H5 | 无 DSP 的光-模拟-光波长转换域边界，多 FEC 兼容 | ΔOSNR 1.7–2.6 dB；裕量 0.29–0.41 decade | 〔0924-Th1-H5-NTT p4, p6〕 |
| 14 | Marvell | 产业发布 | 等离子体调制器实测 3 dB EO 带宽 990 GHz（未标注是否记录）；Libra/Electra"业界首个/首款 2 nm" | C≈30 fF，R<2 Ω；调制器 >110 GHz、探测器 >100 GHz、放大器 >145 GHz | 〔0923-MF-Marvell等连拍 p3, p4, p5, p7〕 |
| 15 | NICT/UCLA/Hamamatsu | Workshop | 光域均衡：1 抽头 ODL 与成对传输消除 IM/DD 色散零点 | C 波段 100 Gbaud 超 80/100 km（record low DSP complexity，自述）；成对传输 40 km 约 HD-FEC | 〔0920-Su3Su4-A全场扫描 p144, p146〕 |
| 16 | Microsoft Azure Fiber（OFC 引用） | OFC 2025 Th4A.3；OFC 2026 Th1J.5 | 无中继/多跨 32×800G HCF | 200.5 km；3 跨 442.66 km | 〔0920-pm-Su4-B-05-Azure p10〕 |
| 17 | Ciena | 产业展示 | 12.8T Coherent-Lite XPO 实物 | <240 W；BER <1E-24 | 〔0920-pm-Su4-A-02-Ciena p7〕 |
| 18 | OIF/Cisco | CMIS 演示 | 多厂商 CMIS 5.4 800G ZR OSFP 与 1.6T OSFP 互操作 | CDB 50h/51h | 〔0923-MF-OIF-CMIS p8〕 |

标注：record 声明为 Azure Tu3-H4（"record-long reaches of 400G ZR"）〔0922-Tu3-H4-Azure p13〕；PDP 为 PDP-C-6、ECOC 2025 PDP Th03.01.1/.2、ECOC PDP 2026（引文）；首次声明为 YOFC Mo5、NTT We2-A2、Marvell Libra/Electra（产业）。

## 5. 分歧、争议与反常识

**5.1 Coherent-Lite 还是 IM/DD 光域均衡：2 km 以上谁做主力？**
- 相干方：Ciena、Acacia、Nokia、Marvell 均以色散随波特率平方增长立论：400G/lane 时 >2 km 需相干；Ciena 强调 BER <1E-24 与零重传〔0920-pm-Su4-A-03-Acacia p5〕〔0920-pm-Su4-A-02-Ciena p5〕。
- IM/DD 方：NICT/UCLA 认为若无信道零点突破则 Coherent-lite 主导，但最小光学（1 抽头延迟线、成对传输）可打破色散壁垒；其自身承认 O 波段 2 km 后可用带宽 <45%（Broadcom 引文 <10%）〔0920-Su3Su4-A全场扫描 p141, p147〕。
- 判断依据：前者有现成 DSP 代际表；后者多为 C 波段与实验室演示，尚无 O 波段 200 Gbaud 实测。

**5.2 可插拔 vs 全谱转发器：谁更省？**
- 转发器方：Ciena：Metro DCI 转发器 76.8 Tb/s 对 51.2 Tb/s 可插拔（+50%），海缆 +16%；Huawei 自称 FST 25.6T/光纤〔0923-MF连拍 p69, p70〕〔0920-pm-Su4-C-03-华为 p5〕。
- 可插拔方：Google 主张可插拔闭合与"二值化"，线路系统而非模块是功耗大头；Cignal 观察到相干可插拔 ASP 下降、线路系统价格持平/上涨，暗示线路系统集成度是关键〔0920-am-Su2-B-01-Google p4〕〔0922-MF-am-1140-CignalAI p8〕。
- 反常识：Ciena 自己也同时出货 WL6 Nano 可插拔，二者并存（p71 "pluggables and performance transponders coexist"），分歧实为"频谱效率优先 vs 功耗/空间优先"的场景切分〔0923-MF连拍 p69–p71〕。

**5.3 HCF：已商用还是仍在实验室？**
- 正方：Huawei 称 HCF 插损已低于实芯 SMF，已在 DCI 与金融专线商用；Azure 实时 HCF 点已到 25 Tb/s @~440 km；Corning 仿真 +25% 重叠〔0920-pm-Su4-C-03-华为 p5〕〔0920-pm-Su4-B-05-Azure p3〕〔0924-Th1-G1-Corning p9〕。
- 反方：领纤自陈"工程指标仍远落后"，价格 >\$3000–5000/km，累计产量约 83 km，283 座拉丝塔才可达 SMF 市场 1%；Cignal 称空芯未规模部署；ZTE 认为部分场景 HCF 无收益〔0921-Mo3-B1-领纤 p13, p60, p69〕〔0922-MF-am-1140-CignalAI p8〕〔0923-We5-B-中兴 p15〕。
- 附带分歧：损耗与弯曲/单模性的取舍（33.6 μm 芯 0.052 dB/km 弯曲敏感 vs 14.8 μm 芯 0.25 dB/km 弯曲不敏感），DCI 与 DCN 需要不同 HCF 变体〔0921-Mo3-B1-领纤 p41, p55〕。

**5.4 ZR 还是长途转发器跨长距？**
- 主张 ZR：Azure 认为 HCF 的低非线性使 400G ZR（-10 dBm、约 60 GBaud）可用于 427.97 km，降低 CapEx/OpEx〔0922-Tu3-H4-Azure p13〕。
- 主张长途转发器：同一讲稿自身指出长途转发器 800G/λ、140+ GBaud、放大距离 1000+ km、TX >0 dBm；GLA 限制 400G ZR 进一步延伸〔0920-pm-Su4-B-05-Azure p6〕〔0922-Tu3-H4-Azure p13〕。
- 反常识：低比特率（400G）+ 低波特率反而在 HCF 上因功耗与成本占优；这以 GLA 平坦性为前提，3 跨后 GLA 深度 >20 dB。

**5.5 "多rail"一词的歧义。** NVIDIA Spectrum-X 多平面多 rail（8 平面 4 rail，节省 1.7x 交换机）是 scale-out 拓扑；Ciena/Google/Huawei 的 Hyper Rail 是并行放大/线路光子 rail（4 → 128 rails/机架）〔0921-MF-pm-1340-NVIDIA p9, p10〕〔0920-pm-Su4-C-04-Ciena p4〕。两者共享的机制是"用并行度换单通道速率"，但对象（交换机 vs ILA）不同。

**5.6 出货口径的落差。** Acacia 自报累计 >75,000 个 800ZR+；Cignal 称 800ZRx 已 >100,000 端口（截至 2Q26），且 Acacia 是唯一季度 >25,000 的供应商；某超大规模预测 2026 年 200,000+、2027 年 >350,000；Nokia 引市场信号 2026 年预计 >200k 800ZR 级。累计 vs 年度 vs 端口 vs 模块口径未统一，〔0920-pm-Su4-A-03-Acacia p3〕〔0922-MF-am-1140-CignalAI p10〕〔0920-pm-Su4-A-04-Nokia p6〕。

**5.7 光纤对数量：危机还是规模化红利？** Nokia 称园区光纤数量已成危机，需提高每波长速率（1.6T/λ）；Ciena 则认为部署单位应转向光纤对，靠 FST 把线路端口从 60–120 个插件降到 1 个；KDDI 选择 SDM（12 芯）+ O 波段扩容；ZTE 用 19.1 THz 单纤宽带节省光纤 74.8%。三条路径（提高单波速率、频谱扩展、空间复用）并行，并无统一结论〔0920-pm-Su4-A-04-Nokia p1〕〔0920-am-Su2-B-02-Ciena p8〕〔0922-Tu1-G1-KDDI p30〕〔0923-We5-B-中兴 p1〕。


## 6. 判断与观察点

### 6.1 技术成熟度判断

| 技术 | 成熟度 | 依据 |
|---|---|---|
| 800ZR/ZR+ 可插拔 | 量产爬坡 | >100,000 端口（Cignal，截至 2Q26）；DSP 3 nm 大规模爬坡〔0922-MF-am-1140-CignalAI p10〕〔0920-Su3Su4-A全场扫描 p120〕 |
| 1600ZR/ZR+ | 样品/IA 阶段（2026 年中） | Nokia IA ~Q2/Q3 2026；Marvell Electra 展示；Ciena 1600 ZR/ZR+ OSFP 功耗 34–42 W 为 2027 预测〔0920-Su3Su4-A全场扫描 p120〕〔0920-am-Su2-B-02-Ciena p7〕 |
| Coherent-Lite（1.6T/3.2T，O 波段） | 演示/规范化阶段 | Ciena 2×1.6T OSFP 与 12.8T XPO 展示；1600CL 波特率"待定"〔0920-pm-Su4-A-02-Ciena p6, p7〕〔0920-Su3Su4-A全场扫描 p120〕 |
| FST + 多rail | 产品发布，现网规模未披露 | 均为厂商自报；Cignal 列出 Ciena 首个超大规模 multi-rail 采购订单、Nokia multi-rail 设计中标、Cisco RON-MOFN 订单〔0922-MF-am-1140-CignalAI p10〕 |
| HCF DCI | 实验室与选择性商用 | 见 5.3 |
| O 波段 / S+C+L 宽带 | 实验/现网试验 | 19.1 THz CFP2 实验；S+C+L 现网试验（中国电信）〔0923-We5-B-中兴 p14〕〔0923-MF连拍 p7〕 |
| OCS + OTN 跨 DC 训练 | 测试床/小规模现网 | ≤40 km、≤1024 GPU 量级〔0923-We-F-00-标准化专场II p31〕〔0922-Tu1-G1-KDDI p7〕 |
| CMIS/互操作管理 | 演示期，出货最大管理接口（自述） | 〔0923-MF-OIF-CMIS p8, p10〕 |

### 6.2 时间窗口

- **2026–2027**：800ZR+ 作为 scale-across 主力 SKU；1600ZR/ZR+ 进入 IA/早期部署；某超大规模预测 2027 年 >350,000 个 800ZRx〔0922-MF-am-1140-CignalAI p10〕。可插拔 \$/G 2027 年降至 \$5/G 以下〔0922-MF-am-1140-CignalAI p6〕。
- **2027–2028**：scale-across 带宽 2028 年超过 metro/前端 DCI（Cignal）；Huawei/Ciena FST 与 Hyper Rail 从产品发布转入部署；Acacia 路线图 2–5 年 Coherent-lite 园区，5–10 年数据中心内相干〔0920-pm-Su4-A-03-Acacia p9〕。BT 约 2029 年 800G 核心，2030+ 可能 1.6T〔0920-am-Su1-C-00-上半场速记 p25〕。
- **2030**：scale-across 占云可插拔带宽 72%，支出 8.7B USD，线路系统占 55%；1600ZRx 2.9B USD〔0922-MF-am-1140-CignalAI p7, p9〕。

### 6.3 对各类厂商的含义

- **设备商**：价值向线路系统与 FST 集中（线路系统占比 32%→55%），且线路部件交期 12–18 个月、InP 晶圆受限，泵浦/EDFA 供给是关键；rail 数（4→128/机架）与站点电力（至 4 MW）成为新的规格竞争维度〔0922-MF-am-1140-CignalAI p8〕〔0920-pm-Su4-C-04-Ciena p2, p4〕。
- **模块商**：800G 之后进入 1.6T 的 <45 W 风冷天花板；形态分叉（QSFP-DD/OSFP vs 液冷 XPO 300 W ZR）；互操作（CMIS、MACsec）成为入场门槛；ZR/ZR+ ASP 持续下降〔0920-am-Su2-B-01-Google p7〕〔0923-MF-Marvell等连拍 p29〕。
- **芯片商**：3 nm→2 nm、集成 MACsec、园区专用低延迟 FEC（BCH 类 50–75 ns）；200G→400G/L 时电/光联合设计；调制器带宽 >110 GHz 与放大器 >145 GHz 是 1.6T 前提〔0920-pm-Su4-A-04-Nokia p12〕〔0923-MF-Marvell等连拍 p5〕。

### 6.4 未来 12–24 个月观察点

1. 800ZR+ 与 1600ZR/ZR+ 的季度出货与 \$/G（Cignal 口径：<\$6/G → <\$5/G）；Marvell、Nokia、Ciena 相对 Acacia 的份额〔0922-MF-am-1140-CignalAI p6, p10〕。
2. 1.6T ZR/ZR+ OSFP/QSFP-DD 的实测功耗是否落在 34–45 W 区间，以及液冷 XPO 的首个客户〔0920-am-Su2-B-02-Ciena p7〕〔0920-am-Su2-B-01-Google p7〕。
3. FST 的现网机房数与每站点 rails（是否达到 Ciena 4 → 128 rails/机架）；Google HyperRail 是否披露 8 rail 以上部署〔0920-pm-Su4-C-04-Ciena p4〕〔0920-am-Su2-B-01-Google p5〕。
4. O 波段 Coherent-lite 1600CL 波特率定案（226–247 GBd）与 FEC 选择，IM/DD 光域均衡是否出现 O 波段 200 Gbaud 实测〔0920-Su3Su4-A全场扫描 p120, p141〕。
5. HCF：单盘长度、价格（当前 >\$3000–5000/km）、GLA 缓解、熔接/OTDR 商用件；ZR 在 HCF 上的距离是否越过 3 跨 427.97 km〔0921-Mo3-B1-领纤 p13〕〔0922-Tu3-H4-Azure p13〕。
6. OCS/OTN Proxy 跨 DC 训练：训练效率随规模（>1024 GPU）与距离（>40 km）的实测；中国电信 >97% 与 Huawei <5% 损失能否在更大规模复现〔0923-We-F-00-标准化专场II p31〕。

## 7. 推荐配图

1. 0920-pm-Su4-C-04-Ciena p3 — FST 演进（WL2–WL6）与 192→32 设备、-75% 机架单元、-50% 功耗 — 支撑判断2。
2. 0920-am-Su2-B-02-Ciena p8 — 22 机房 vs 1 机房，60–120 插件 vs 1 线路端口 — 支撑判断2、5.7。
3. 0920-pm-Su4-C-04-Ciena p4 — Hyper Rail 4 → 128 rails/机架 — 支撑判断2。
4. 0920-pm-Su4-C-04-Ciena p2 — ILA 机房 Existing/Large/X-Large 规模对比表 — 支撑站点形态演进（1.3）。
5. 0920-am-Su2-B-01-Google p4 — 2017–2026 相对功耗：光学下降、线路系统不变 — 支撑判断1。
6. 0920-am-Su2-B-01-Google p7 — 400G/800G/1.6T ZR++ 功耗与 45 W 风冷天花板 — 支撑判断4。
7. 0922-MF-am-1140-CignalAI p7 — scale-across 带宽超过 DCI 的交叉曲线 — 支撑判断1。
8. 0922-MF-am-1140-CignalAI p9 — scale-across 支出结构：可插拔 vs 线路系统（线路系统占 55%） — 支撑判断1。
9. 0922-MF-am-1140-CignalAI p6 — 相干模块市场与 \$/G — 支撑判断1、6.4。
10. 0920-Su3Su4-A全场扫描 p120 — 400ZR 至 1600CL 的 DSP 代际总表 — 支撑判断3、2.1。
11. 0920-pm-Su4-A-04-Nokia p12 — 园区 FEC 三方案波特率-延迟-RSNR-功耗表 — 支撑判断3。
12. 0920-Su3Su4-A全场扫描 p123 — 按覆盖选择引擎的总表 — 支撑判断3、1.2。
13. 0920-Su3Su4-A全场扫描 p141 — 相干 vs IM/DD 可用带宽随距离曲线 — 支撑分歧 5.1。
14. 0920-pm-Su4-A-03-Acacia p5 — IMDD 到相干的速率-距离图与色散平方论证 — 支撑判断3。
15. 0923-MF连拍 p70 — Metro DCI 可插拔 vs 转发器容量对比（51.2T vs 76.8T） — 支撑分歧 5.2。
16. 0923-MF-Marvell等连拍 p29 — XPO 各技术 reach/功耗/pJ/bit 对比表 — 支撑判断4。
17. 0922-Tu3-H4-Azure p12 — 3 跨 427.97 km BER/OSNR 与 CD 估计 — 支撑判断5。
18. 0920-pm-Su4-B-05-Azure p6 — ZR 与长途转发器对照表 — 支撑分歧 5.4。
19. 0920-pm-Su4-B-05-Azure p3 — >100 km HCF 直线传输汇总 — 支撑判断5。
20. 0921-Mo3-B1-领纤 p13 — SMF vs HCF 全指标对比表（含价格与产能） — 支撑判断5、分歧 5.3。
