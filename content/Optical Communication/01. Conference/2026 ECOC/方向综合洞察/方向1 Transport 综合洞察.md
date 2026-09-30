---
title: "方向1 Transport 综合洞察"
tags:
  - ECOC2026
  - 综合洞察
---

# 方向1：传统相干/海缆/长途/DCI/AI光网络/oDSP/高波特率光器件（含网络智能化与AI运维一节、空芯光纤与SDM在长途与海缆中的作用）

## 0. 一句话结论 + 5条核心判断

**一句话结论：相干技术的竞争轴已从"峰值波特率"转到"按覆盖距离切分的产品族"（1600ZR/ZR+/Coherent-Lite），长途与海缆的容量增量则来自介质与放大器的扩带（空芯光纤HCF、S/O/L等多波段、SDM），其中海缆被供电而非光学锁死；网络智能化在DSP内监测已进入芯片，LLM智能体仍是原型与现网试验，尚未达生产可用。**

**判断1：1.6T相干已分叉为两条路线，实验室波特率领先量产的窗口在缩短。**
1600ZR为单载波约236 GBd DP-16QAM+OFEC、约300 GHz频隙、80–120 km；1600ZR+为2×约126 GBd（合计252 GBd）PCS-16QAM，可达约1000 km，复用800G模拟器件（Nokia，市场与路线图口径）〔0920-pm-Su4-A-04-Nokia p13〕。Huawei报告实时234 GBd、2.0 Tb/s收发机，60 km SSMF无误码（实验）〔0923-We2-I-00-全场连拍 p43〕；Nokia Bell Labs用450 GBd全电I/Q复用实现单波长3.83 Tb/s（B2B，PS 64QAM，离线DSP）〔0924-PDP-A-5-NokiaBellLabs p13〕，并给出实验室领先量产的时间从约7年（800G）缩至约4年（1.6T）〔0924-PDP-A-5-NokiaBellLabs p7〕。机制：DSP功耗随代际增长快于CMOS节点，1600G时ASIC约24 W而光学约9 W（读数估计）〔0921-MF-am-T05-1120-Nokia p3〕，量产端靠子载波、2 nm CMOS和FEC分档控功耗。

**判断2：相干正在下沉到园区2–40 km，与IM/DD的分界由色散与延迟预算决定。**
色散代价∝D×L×BW²，200 GBd/lane以上仅数ps/nm即关键；224 GBd、2 km、<20抽头且<4 dB代价准则下，IM/DD FFE仅约45%的O波段可用，相干几乎全波段可用（仿真/分析，NICT）〔0920-pm-Su4-A-05-NICT p6〕〔0920-pm-Su4-A-05-NICT p9〕。Nokia将园区FEC延迟目标定为50–75 ns（BCH(126,110)：247.3 GBd、49–55 ns），并称"不要在10 km AI链路上用OFEC"〔0920-pm-Su4-A-04-Nokia p12〕。Ciena用压缩FEC实现BER<1E-24并给出12.8T Coherent-Lite XPO，功耗<240 W〔0920-pm-Su4-A-02-Ciena p7〕。市场侧：800ZR+出货>75,000只（Acacia自报）〔0920-pm-Su4-A-03-Acacia p3〕；2026年预计>200k只800ZR类单元（讲者引用的公开市场信号）〔0920-pm-Su4-A-04-Nokia p6〕。

**判断3：HCF已从损耗记录进入现网与多跨系统，瓶颈转为气体吸收线（GLA）、模间干扰（IMI）、良率与外径。**
损耗：YOFC GTA-ST-HCF 0.032±0.003 dB/km（45.26 km，实验室测）〔0920-pm-Su3-B-01-长飞YOFC p13〕。系统：532 km全C波段无中继30.66 Tb/s（有ROPA）/15.73 Tb/s（无ROPA），2×266 km GTA-ST-HCF（实验，PDP）〔0924-PDP-A-3 p22〕；266 km超长跨段跨洋21.7 Tb/s、6660 km、25个中继〔0920-pm-Su4-B-02-NokiaBellLabs p20〕。现网：中国移动无锡18.4 km TDNANF-4两年未充气监测〔0920-pm-Su4-B-03-中国移动 p7〕；Microsoft称多个Azure Region已承载客户业务，未来12个月计划部署12,000 km+〔0922-Tu3-H1-MicrosoftAzureFiber p29〕。制约：Ciena测得目前没有单个样品同时满足各距离段的IMI/GLA/PDL/PMD目标，GLA是长途主限制〔0923-MF-Ciena-空芯光纤 p14〕；产能上HCF每拉丝线约30,000 km/年，占SMF市场1%需283座拉丝塔（Linfiber自报）〔0921-Mo3-B1-领纤Linfiber p69〕。

**判断4：海缆容量的天花板是供电（PFE电压与线缆DCR），SDM与HCF的系统收益受外径与供电共同限制。**
Meta：24FP跨大西洋约0.5 Pbps已近技术极限；1 Pbps需48FP等效方案+18 kV PFE+DCR约1 Ω/km；2 Pbps在现有供电下"不可能"〔0921-Mo3-G1-Meta p7〕〔0921-Mo3-G1-Meta p9〕。ASN：6000 km、18/24/36 kW、≤48 FP约束下，今天0.10 dB/km的HCF设计约1.1 Pbps，与SCF约1.25 Pbps相当（读图，仿真）〔0920-pm-Su4-B-04-ASN p10〕；无空间约束时HCF C带可达约6.3 Pbps对SCF约3.2 Pbps（读图估计）〔0920-am-Su2-B-06-ASN p6〕。实时传输：Ciena/Meta在Bifrost 16,608 km上实时18 Tb/s（298.9 Pb/s·km），首次跨太平洋距离实时800 Gb/s〔0921-Mo3-待定-Ciena p5〕。能效侧：可插拔约70–100 pJ/bit对嵌入式约425–680 pJ/bit（读图，Nokia）〔0920-am-Su2-B-04-Nokia p5〕。

**判断5：网络智能化的落点是"DSP内监测+受约束的智能体"，而非零接触自治。**
片上LPM已在ExaSPEED800/118 GBd OSFP DSP中实现：单个PDL估计误差<0.5 dB，多PDL定位误差<1.0 dB（200 km，实验）〔0922-Tu4-H2-NTT p6〕。LLM智能体：Chalmers在CORONET CONUS数字孪生上，Qwen2.5 32B Instruct的Multi-Call工具抽象通过率90%，Generic仅57%，结论"生产可用？尚未"〔0923-We2-C2-1339-符合T p11〕〔0923-We2-C2-1339-符合T p13〕；北邮Skill+SOP智能体相对基线token减少86%、RCA准确率100%（仅光纤断裂/弯曲两类场景）〔0923-We2-C1-939-北邮 p13〕。

---

## 1. 需求与网络架构

- **容量需求**：海缆带宽需求增速25–33%、平均26%（TeleGeography），约每3年翻倍〔0920-am-Su2-B-06-ASN p2〕；跨大西洋需求2035年约18 Pbps（NEC引TeleGeography）〔主分析师笔记09-NEC Su2-B-05〕。Omdia（2024版）光网络交付量2020年约130 Pb增至2029年约1850 Pb（柱状图读数）〔0920-pm-Su3-H-05-Adtran p4〕。多区域AI集群每区域对需Pb/s量级、最高48 Pb/s〔0920-pm-Su3-D-05-Nokia p4〕；约190 GW超大规模容量已宣布，每AI园区4–12栋楼，1.6T下园区间隙2–40 km，光纤时延5 μs/km〔0920-pm-Su3+Su4-A-00-全场 p111〕。
- **流量占比**：中国电信预测AI-enhanced应用中的AI流量到2033年约43–44%，常规应用流量约70%+降至约35%（读图估计）〔0923-MF-00-上午连拍 p4〕；BT称AI流量在消费者流量中"无显著体现"，核心流量>34 Tbit/s，推理约"一波长"级，训练需scale-across〔0920-am-Su1-C-00-全场 p19〕。
- **三域架构（Nokia）**：scale-up（米级，IM-DD，CPO/NPO/XPO）；scale-out（100 m–10 km，PAM4可插拔至2 km，约2 km起Coherent-lite）；scale-across（10–1000+ km，ZR/ZR+，IP over DWDM或thin transponder，C+L）〔0920-pm-Su4-A-04-Nokia p4〕。
- **Meta骨干**：IP网络4平面扩到8平面（scale up+out约100x）；IP与光集成去转发器，同容量总功耗约降80%；最大路由光纤数约每年翻倍，2031年>1k；ILA站房从48 rails/2 kW每架演进到设计中的4,096 rails/>18 kW每架，每光纤对成本约降8x〔0921-MF-am-T08-1220-Meta p10〕〔0921-MF-am-T08-1220-Meta p13〕。
- **OVHcloud**：<10 km无线路系统（如2x400G LR），>10 km 800G ZR+加线路系统（跨段约100 km），环内容量为环间10倍〔0920-am-Su1-C-00-全场 p16〕。
- **BT**：核心传输2025年400G、约2029年800G、2030+可能1.6T，并提出需新光纤类型/更多频谱〔0920-am-Su1-C-00-全场 p25〕。
- **中国电信**：500,000 km系统光纤、1000+全光调度节点；新建G.654.E链路≤0.172 dB/km；800G现网试验（约140 GBd DP-PCS-16QAM），1.6T实验室（200 GBd+，DP-PCS-64QAM）；S+C+L现网试验约17–20 THz，全频段实验>37 THz；50 ms WSON保护〔0923-MF-00-上午连拍 p6〕〔0923-MF-00-上午连拍 p7〕。
- **运行效率**：AIST量化浪费：400ZR+按OSNR选速率多余余量11 dB、峰值观测损失75%；算力与网络容量失配峰值损失96%；协议不适配全光路径93%/55%（自报，试验台）〔0920-am-Su2-B-03-AIST p5〕〔0920-am-Su2-B-03-AIST p13〕。NTT引用统计：多数网络频谱占用率<60%，OSaaS可变现闲置频谱〔0920-pm-Su4-H-05-NTT p2〕。
- **光纤空间与长度分布**：HCF应用长度占比接入约70%、长途约20%、海缆约10%〔0920-pm-Su4-B-03-中国移动 p2〕；Nokia主张DCI/长途仍可继续增加SSMF（已部署128+光纤对线缆），海缆C+L使光纤容量约提升2x，相当于5–6年需求增长〔0920-pm-Su3-D-05-Nokia p6〕。
- **标准**：ITU-T ION-2030三层网络〔0920-am-Su1-C-00-全场 p8〕；OIF 1600ZR/ZR+已发straw ballot，1600 Coherent Lite讨论中（<40 km，最小10 km）〔0921-MF-am-T05-1120-Nokia p6〕。

---

## 2. 技术路线与关键指标

### 2.1 相干DSP、可插拔与嵌入式（1.6T/2T/3.2T演进）

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Nokia | 400ZR→800ZR→1600ZR/ZR+/CL产品族 | 400ZR约60 GBd 7 nm CFEC；800ZR 118–135 GBd DP-16QAM+PCS OFEC 3 nm；1600ZR约236 GBd单载波；1600ZR+ 252 GBd（2×约126）；1600CL约226–247 GBd（待定），FEC延迟50–75 ns；IA约Q2/Q3 2026 | 讲者路线图 | 〔0920-pm-Su3+Su4-A-00-全场 p120〕 |
| Nokia | 园区FEC三选项（复用800G 10 km CL的BCH引擎） | BCH(126,110) 247.3 GBd、49–55 ns、RSNR 13.7 dB、模块功耗+1.5–3%；压缩FEC 239.1 GBd、70 ns、13.8 dB、0%（基准）；Braided 226.7 GBd、70–72 ns、14.3 dB | 讲者路线图 | 〔0920-pm-Su4-A-04-Nokia p12〕 |
| Nokia | DSP功耗与1.6/2.4T应用（T05） | DSP功耗构成：Line 43%、Analog 43%、Client 12%、Control 2%；ASIC约24 W对光学约9 W（1600G，读数估计）；Low power <40 km 220–247 GBd 30 W；Multi-haul 40–7000 km 100–260 GBd 43 W；High-performance 40–15000 km 60–300 GBd 2.4T 60 W 64QAM | 讲者自报/读数 | 〔0921-MF-am-T05-1120-Nokia p3〕〔0921-MF-am-T05-1120-Nokia p6〕 |
| Ciena | Coherent-Lite与零重传 | 2 nm CMOS；每3.2 Tb/s、20 km需1.3 Gb ARQ存储；10T参数数据集在BER=1E-12下丢160包；压缩FEC后BER<1E-24；12.8T Coherent-Lite XPO <240 W（液冷可承受400 W） | 讲者自报（"Zero Errors"为自述） | 〔0920-pm-Su4-A-02-Ciena p5〕〔0920-pm-Su4-A-02-Ciena p7〕 |
| Ciena | WaveLogic 6 Nano可插拔对Extreme转发器 | 海缆Tasman Express 2250 km：23.2 Tb/s（29×800G，150 GHz）对27 Tb/s（+16%，27×1T，162 GHz）；Metro DCI：51.2 Tb/s（64×800G，150 GHz）对76.8 Tb/s（+50%，48×1.6T，200 GHz） | 讲者对比数据 | 〔0923-MF-00-上午连拍 p69〕〔0923-MF-00-上午连拍 p70〕 |
| Nokia | 嵌入式对可插拔（1830 PSS-HC） | 城域550 km/55 Tb/s：可插拔（thin transponder，Ext C+Ext L）CapEx节省28%、占地节省29%、功耗节省36%；长途1300 km：嵌入式800G对可插拔400G，嵌入式容量多63%，可插拔CapEx节省52%、占地40%、功耗64% | 产业发布（自家仿真/规划） | 〔0921-PF-待定-Nokia p9〕〔0921-PF-待定-Nokia p11〕 |
| Acacia（Cisco） | 800ZR+ | 出货>75,000只；IMDD在200G/lane极限约10 km，400G/lane时>2 km需相干；路线：0–2年200G/lane，2–5年400G/lane与Coherent-lite园区，5–10年800G/lane、数据中心内相干 | 讲者自报 | 〔0920-pm-Su4-A-03-Acacia p3〕〔0920-pm-Su4-A-03-Acacia p5〕 |

### 2.2 高波特率发射/接收与器件

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Nokia Bell Labs | 450 GBd全电I/Q（DBI-DAC）+TFLN IQM+OAWM接收 | 单波长净3.83 Tb/s，PS 64QAM熵5.3，SNR X/Y 13.95/13.88 dB，NGMI 0.8795/0.8768对阈值0.8714；B2B与10 km SSMF；离线DSP；此前2.42、2.52 Tb/s | 实验（PDP） | 〔0924-PDP-A-5-NokiaBellLabs p13〕〔0924-PDP-A-5-NokiaBellLabs p8〕 |
| Huawei | 234 GBd实时相干收发机（自研CMOS ASIC+AI核） | 2.0 Tb/s，60 km SSMF，pre-FEC BER约0.029，post-FEC无误码，连续监测10小时，Q余量>0.6 dB；贝叶斯优化约100次迭代，BER 2.5×10⁻²→1.7×10⁻²（约0.7 dB Q）；兼容1.6T ZR+，双子载波 | 实验（实时） | 〔0923-We2-I-00-全场连拍 p49〕〔0923-We2-I-00-全场连拍 p48〕 |
| NTT | 168 GBd PCS-324QAM+样本域Volterra预失真（TFLN IQM，256 GSa/s AWG） | B2B净速率2.18 Tb/s；80 km后2.10 Tb/s（入纤6 dBm，熵8.063 bit/2D-sym）；样本域VF较符号域VF峰值SNR高0.7 dB（均匀64QAM，2.5 Vpp） | 实验 | 〔0921-Mo5-F5-NTT-168-GBd-PCS p6〕〔0921-Mo5-F5-NTT-168-GBd-PCS p7〕 |
| Nokia Bell Labs | 光谱-时间酉变换生成高波特率 | 仅50 GHz电带宽：100 GBd 16QAM（8级）SNR 16.7 dB；220 GBd 16QAM（10级）SNR 11.8 dB，NGMI约0.86（阈值0.8456）；受环损耗与相位稳定限制 | 实验（环回） | 〔0922-Tu3-A3-NokiaBellLabs p8〕〔0922-Tu3-A3-NokiaBellLabs p13〕 |
| 上海交大/Nokia Bell Labs/西湖大学 | 免LO直接检测（SiP DP-CADD等） | DP-CADD净426 Gb/s、净ESE 11.83 b/s/Hz（80 km，24% SD-FEC）；最简相位分集46 GBd 64-QAM净229 Gb/s、ESE 8.76；常规DD净ESE约4 | 实验（记录声明引ECOC 2023 PDP） | 〔0923-We3-D5-上海交大 p25〕〔0923-We3-D5-上海交大 p15〕 |

### 2.3 海缆：供电、能效、无中继与实时传输

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Meta | 超Petabit海缆 | 24FP约550 Tbps为当前技术上限（读图）；18 kV PFE下1 Pbps@TA需DCR约1 Ω/km、中继器压降120 V，线缆41%/中继器59%；2 Pbps中继器占PFE 109%，不可能；13,000 km中间供电可提升约+60%；Petal（法-美约7,000 km，预计2029年）首条大规模部署MCF海缆（OCR） | 讲者自报/设计分析 | 〔0921-Mo3-G1-Meta p3〕〔0921-Mo3-G1-Meta p7〕 |
| NEC Labs America | 多Pb海缆功效 | <24FP、7000 km能耗：SCF 28/2CF 20/4CF 17 pJ/b；9000 km：38/30/30；12000 km：47/47/55；跨大西洋约20 pJ/b，跨太平洋约50 pJ/b；分支辅助供电使SEF@48CP约6,500 km延伸至+9000 km；跨大西洋约6700 km、48CP、2CF、PFE 18 kV/22 kW约1 Pb/s | 分析/自报 | 〔主分析师笔记09-NEC Su2-B-05〕 |
| ASN | HCF与SDM海缆系统级容量 | 无空间约束6000 km/18 kW：SCF 300路径约3.2 Pbps对HCF C带520路径约6.3 Pbps（读图）；9,000 km跨太平洋1 Pbps目标：18 kW时仅HCF C+L 2×16FP（约1.45）超过；实际约束≤48 FP下HCF C+L SDM×2约2 Pbps量级；6000 km 0.05 dB/km最优跨段约170 km/35中继，容量仅比0.08 dB/km多约6% | 仿真（读图，不精确） | 〔0920-am-Su2-B-06-ASN p6〕〔0920-am-Su2-B-06-ASN p11〕 |
| Ciena/Meta | Bifrost实时18 Tb/s | 16,608 km，12对光纤，平均中继间距约65 km；28路140–178 GBd，600/700G，每信道余量>0.17 dB，8小时无误码；298.9 Pb/s·km；首次跨太平洋实时800 Gb/s（173 GBd，4.57 b/s/Hz）；算法收敛<1秒/候选、最大吞吐优化<2分钟 | 实验（实时，称记录） | 〔0921-Mo3-待定-Ciena p2〕〔0921-Mo3-待定-Ciena p5〕 |
| Nokia | 海缆可插拔 | ICE-X现场试验（OFC 2026 Th4C.6）：2,931 km、45个重发器、平均跨距66 km，400G/λ 5,682 km（72 GBd），600G/λ 2,841 km（119 GBd，Q余量2.5–2.8 dB），800G闭合但余量不足；同容量节能约88–93%；每C带光纤电费节省>\$12k/年 | 现网试验（引用） | 〔0920-am-Su2-B-04-Nokia p8〕〔0920-am-Su2-B-04-Nokia p6〕 |
| Lightera/Cisco | 实时无中继2芯MCF | 52.8 Tb/s（26.4 Tb/s/core）、303.4 km、SCUBA 2X（0.147 dB/km，XT平均-59 dB/100 km），33路138 GBd DP-16QAM-PCS，商用800G可插拔；单向/双向无可测量XT代价，平均Q²余量约1.5–1.7 dB | 实验（称记录，实时） | 〔0921-Mo3-待定-Lightera p5〕〔0921-Mo3-待定-Lightera p6〕 |

### 2.4 空芯光纤：光纤指标、制造与部署

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| YOFC | GTA-ST-HCF（长途，29 µm芯/230 µm/370 µm） | 最低0.032 dB/km、典型0.08 dB/km，IMI≤-60 dB/km；45.26 km样品OSA 0.0292–0.0297 dB/km，OTDR 0.035 dB/km，标称0.032±0.003，IMI -63.6 dB/km | 讲者自报/实验室测 | 〔0920-pm-Su3-B-01-长飞YOFC p13〕 |
| Linfiber | 大芯/中芯AR-HCF量产 | 大芯：单塔1个月967.7 km，加权平均0.068 dB/km，最小0.038；中芯：1273.59 km，≤0.1 dB/km长度999.96 km，加权平均0.088 dB/km，IMI -60 dB/km；讲者称大芯"工业应用价值有限"（OCR） | 讲者自报 | 〔0920-pm-Su3-B-01-长飞YOFC p22〕〔0920-pm-Su3-B-01-长飞YOFC p23〕 |
| Linfiber | 全指标对比与产能 | HCF<0.05 dB/km对SMF 0.142；非线性<0.01对1–10 W⁻¹km⁻¹；产能每预制棒数十km对数千km；价格>\$3000–5000/km对\$20–40/km；SMF每拉丝线约1M km/年，HCF每线30,000 km/年，占SMF市场1%（8.5M km/年）需283座塔；累计产量约83 km对SCF约10000 km量级 | 讲者自报（引CRU预测） | 〔0921-Mo3-B1-领纤Linfiber p13〕〔0921-Mo3-B1-领纤Linfiber p69〕 |
| Microsoft/Southampton | 零色散HCF（PDP） | 外管壁厚1.18→1.31 µm，D在约1.29 µm过零；HF-5 1550 nm损耗0.23 dB/km（最小0.22），HF-4 0.196 dB/km；56 GBd PAM4约15 km：BER HF-5约2–4×10⁻⁴，标准HCF约2–4×10⁻³，SMF约3×10⁻¹；30 µm芯设计仿真0.057 dB/km尚未过零 | 实验（PDP，首次） | 〔0924-PDP-A-1 p18〕〔0924-PDP-A-1 p20〕 |
| 中国移动 | 现网稳定性与标准 | 无锡18.4 km TDNANF-4 2024/10–2026/05无充气吹扫，熔点损耗-0.19至+0.18 dB；CO2线1602.876 nm密封方案缆前0.04 dB/km、部署后0.078 dB/km；4元与5元结构混接耦合损耗最低仍>0.09 dB（G.652.D/G.654.E约0.03 dB）；CCSA已批2份技术报告，ITU-T SG15 2026.7启动GSTR.hcf | 现网+自报 | 〔0920-pm-Su4-B-03-中国移动 p6〕〔0920-pm-Su4-B-03-中国移动 p7〕 |

### 2.5 HCF传输系统：多跨、长跨、无中继、GLA

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Nokia Bell Labs/ASN/YOFC | 532 km全C波段无中继（PDP） | 30.66 Tb/s（37通道PDM-16QAM，ROPA）；15.73 Tb/s（35通道PDM-QPSK，无ROPA）；2×266 km，总跨段损耗57.2 dB；ROPA信号约-15 dBm，泵浦24–34.77 dBm，泵浦降10倍仅损失约10.15%容量；此前C波段无中继约407 km（32 Tb/s，实时） | 实验（PDP，称记录） | 〔0924-PDP-A-3 p22〕〔0924-PDP-A-3 p24〕 |
| Linfiber/暨南大学 | AR-HCF长途环路 | 153.34 km IT-DNANF，110路WDM，12,113 km 24.8 Tb/s；GMI容量距离积300.4 Pb/s·km（称AR-HCF最高）；在线去CO2 845.8 km统计中位<0.039 dB/km；自适应17–68 GBd避CO2线 | 实验 | 〔0920-pm-Su3-B-01-长飞YOFC p28〕〔0920-pm-Su3-B-01-长飞YOFC p29〕 |
| Microsoft/UCL | 从城域到长途综述 | 32×800G实时、138 GBd、301.7 km DNANF；400G ZR经427.97 km HCF（对比151 km SMF）；环路总速率25.8 Tb/s@1439.2 km、10.3 Tb/s@6116.6 km、3.2 Tb/s@11153.8 km；O波段单BDFA 61.5 Tb/s@1080 km | 实验（多为引用/本团队） | 〔0922-Tu3-H1-MicrosoftAzureFiber p9〕〔0922-Tu3-H1-MicrosoftAzureFiber p21〕 |
| UCL/Microsoft/Lightera | 双波段双向O+C（缩径190 µm，PDP） | 112.5 km，2024 km：O 22.7/22.9 Tb/s，C 29.2/31.0 Tb/s，GMI合计51.9+53.9 Tb/s；4500 km C波段双向21.5+22.2 Tb/s；6750 km 16.6+17.2 Tb/s | 实验（自称首次长距双向） | 〔0924-PDP-A-4 p14〕〔0924-PDP-A-4 p15〕 |
| Nokia Bell Labs/YOFC | GLA下134 GBd单载波（长途） | GLA场景（3条线）>1T至1500 km以外，2128 km约930 Gbps（DP-16QAM/64QAM）；无GLA 1000 km内>1.2T/载波，2128 km约1.1T；RRC 0.06时<30抽头，可压150 GHz栅格至137.5 GHz（OCR，未看图） | 实验（环路） | 〔0922-Tu3-H2-NokiaBellLabs p11〕〔0922-Tu3-H2-NokiaBellLabs p12〕 |
| UCL | C+L GLA影响（294×32 GBd） | 1000 km、100 km跨、HCF 27 dBm：C波段较SMF多3.4 Tb/s（8%），中继器少2.7×；GLA理想抑制L波段最大59.2 Tb/s（约1.5×），中继器最多少3.3× | 仿真 | 〔0922-Tu3-H3-UCL p15〕〔0922-Tu3-H3-UCL p23〕 |
| Ciena | 多跨运行洞察 | 累计测试570 km、5家HCF供应商；HCF非线性系数比典型放大器低380倍；各距离段上限：DCI≤100 km GLA深度0.1 dB/km，Regional≤1000 km 0.01，Long haul≤4000 km 0.003，跨大西洋≤10,000 km 0.001（前提：50 ps平均DGD容限等）；1000 km时"近1/2的L波段可能不可用" | 实验室/现网试验 | 〔0923-MF-Ciena-空芯光纤 p5〕〔0923-MF-Ciena-空芯光纤 p10〕 |

### 2.6 放大器与多波段（C+L、S、O、T）

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| YOFC | EBDF+BDF无缝102 nm C+L集成放大器 | 1524.1–1626.8 nm；增益≥23 dB（最小）、NF≤7.8 dB、平坦度≤2.3 dB（加GFF，125波、100 GHz，-10 dBm/波）；饱和输出约21.5 dBm，讲者承认输出偏低噪声偏高 | 实验 | 〔0922-Tu1-D1-长飞 p5〕〔0922-Tu1-D1-长飞 p6〕 |
| Lightera | HCF多波段放大器 | 铒铋混合S+C：23 dBm、NF 7~4 dB、1490–1560 nm；铋E-S两级输出29.4 dBm，PCE 20%；O波段BDFA 29–32 dBm，PCE 10–20%；Yb T波段kW级、最高85%转换效率，"尚未用于数据传输" | 讲者自报 | 〔0920-pm-Su3-B-05-Lightera p5〕〔0920-pm-Su3-B-05-Lightera p7〕 |
| Aston/Lightera | S波段及更宽放大综述 | 混合BiEr无缝S+C 9 THz，增益>20 dB，NF<6 dB，23 dBm；DRA增益16.7 dB、有效NF -2.7 dB；TDFA S波段总饱和输出19 dBm；1050 km对比DRA 14.2 dB SNR>TDFA 13.0 dB；"小信号增益不能作为部署指标" | 综述/引用 | 〔主分析师笔记08-0922-Tu1-D3-Aston大学〕 |
| Aston | 172 Tb/s O波段相干 | 633路×24.5 GBd，1266–1358 nm，16.14 THz，25 km，1200 nm后向拉曼；GMI估计172.87 Tb/s，译码后164.83 Tb/s，10.7 b/s/Hz；最优入纤15 dBm（17 dBm起零色散附近代价上升） | 实验（称GMI记录） | 〔0922-Tu1-G5-Aston大学 p12〕〔0922-Tu1-G5-Aston大学 p13〕 |

### 2.7 SDM：多芯与耦合芯、MIMO

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| TU/e/NICT | 19芯随机耦合MCF（125 µm包层） | 1.7 Pb/s@63.5 km；568.8 Tb/s@5,166 km（容量距离积2.93 Eb/s·km）；434.6 Tb/s@8,610 km（GMI估计470.4 Tb/s，3.74 Eb/s·km，称记录）；新一代损耗0.187 dB/km，SMD<10 ps/√km；38×38 MIMO需1,444个FIR | 实验（环路，离线DSP） | 〔0923-We2-H1-1419-埃因霍温 p22〕〔0923-We2-H1-1419-埃因霍温 p21〕 |
| TU/e/NICT | RC-MCF网络MIMO记忆 | 网络运行下所需MIMO记忆最高3.3 ns（PTP亚ns）；限制在PTP长度吞吐损失C波段53%、L波段75%；节点内路径对齐须控制在IIR时长以内 | 实验 | 〔0922-Tu1-B2-TUe p14〕〔0922-Tu1-B2-TUe p15〕 |
| Nokia Bell Labs/KIT | 实时GPU 10模26 km部分MIMO | 4块A100+2颗EPYC；120 s实时迹SNR稳定：恢复MG1时全部MG约17.9 dB，仅MG1约8.2 dB（差9.7 dB） | 实验（实时） | 〔0921-Mo3-待定-NokiaBellLabs p20〕 |
| NTT | 耦合芯放大MDL/SMD | Type A并联SM-EDFA带边MDL上升（1530 nm约0.9 dB）；Type B耦合4芯MC-EDFA MDL约0.03–0.1 dB且波长平坦，SMD可忽略；12圈RMS MDL约2.2–2.3 dB | 实验 | 〔0923-We2-H2-148 p12〕〔0923-We2-H2-148 p15〕 |
| NTT | 耦合芯超宽带SMD/MDL直接估计 | 1490–1640 nm（150 nm）；现网68 km 12芯CCF平均MDL 0.31 dB，SMD约120–165 ps；MDL仿真验证误差<0.1 dB | 实验（现网） | 〔0921-Mo3-F4-NTT p14〕〔0921-Mo3-F4-NTT p12〕 |

### 2.8 DSP算法：整形、非线性、载波/定时恢复、EEPN、实时实现

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Nokia Bell Labs | PAS加SPC(3,4)与迭代MAP解映射 | 可回收BMD损耗最多0.9 dB（PS-256QAM，SE 9 b/s/Hz）；实验：3.68 THz，31信道×116 GBd，372 km环，7.5 b/s/Hz下1860 km、>26 Tb/s | 仿真+实验 | 〔0921-Mo3-F5-NokiaBellLabs p6〕〔0921-Mo3-F5-NokiaBellLabs p22〕 |
| 华南理工 | LSP-NLC+UDA | 40 GBd DP-PS-64QAM，5路，80 km跨；再优化耗时：CB-ESSFM 1150 s、SP-NLC 1311.969 s、LSP-NLC 109.39 s、+UDA 25.038 s；1200 km与3步/跨DBP相当 | 实验（环回） | 〔0921-Mo5-待定-华南理工大学 p16〕〔0921-Mo5-待定-华南理工大学 p17〕 |
| AIST | 判决前馈DBP（DFF-DBP） | 21信道64 GBd DP-16QAM，Q限6.25 dB下距离2,140 km（仅CDC）→2,634 km（4 sps），延长23% | 实验 | 〔0924-Th1-H2-AIST p7〕 |
| KIT/Nokia | EEPN时变全通滤波模型 | 180 GBd/6600 km仿真；SNR突发约14→11.7 dB，SotA GN近似平坦约13 dB；temporal GN与仿真相关ρ=0.93，SotA仅0.01；N_comp=7自适应线性滤波器接近无EEPN | 仿真+实验（130 GBd，1900 km） | 〔0923-We5-G-00-全场连拍 p69〕〔0923-We5-G-00-全场连拍 p71〕 |
| Huawei | 分布变换函数预测FEC后性能 | 200G DP-16QAM，960 km；平均pre-FEC BER均为1.21×10⁻²时四类场景post-FEC BER约1e-13至1e-7（读图），DTF预测吻合 | 实验 | 〔0924-Th1-H3-华为加拿大 p11〕 |
| NEC | GPU实时2×2 MIMO | 5 Gbaud PDM-16QAM，240 km，SOP容限10 krad/s，实时上限6.1 Gbaud | 实验（实时） | 〔0924-Th1-H4-NEC p4〕〔0924-Th1-H4-NEC p6〕 |
| UCL | 超网络DSP（重捕获延迟） | 复杂度4M→300k实数乘法（与RLS相当）→目标25k；FPGA收敛75 ns；距离泛化约60 km后下降，95 km约8 dB对约13–14 dB | 实验+FPGA | 〔0921-Mo3-待定-UCL p15〕〔0921-合集待拆-全场-Mo5 p34〕 |

### 2.9 监测：LPM、NLI估计、OFDR、MPI

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| NTT | 片上LPM/PDL/NLI（ExaSPEED800，118 GBd OSFP） | 200 km（4×50 km G.654.E）：单PDL<0.5 dB，双PDL误差<1.0 dB（p15页OCR：设定3 dB，估计2.3 dB，误差0.7 dB，未逐项核图）；LPM闭式辅助内存约降99.999%（OCR）；模块功耗无可测增加 | 实验 | 〔0922-Tu4-H2-NTT p15〕〔0922-Tu4-H3-NTT p20〕 |
| Politecnico di Torino | LPM与NLI估计（邀请报告） | 1,483 km异质链路（SSMF 65 km×8+PSCF 110 km×4+SSMF 65 km×8），18×118 GBd QPSK，Acacia CIM-8；LPM估计SNR_NLI与OSA吻合，范围约14–23 dB（OCR）；称LPM"已商业部署"，弱点为只估计SCI | 实验 | 〔0923-We1-G-00-全场连拍 p67〕〔0923-We1-G-00-全场连拍 p91〕 |
| 北邮/信通院 | 低复杂度硬判决PPE | 1 Sps HD+5 km步长直接用RMSE 3.8 dB，所提0.32 dB，计算时间减75%；可识别0.9/2.1/5.0 dB插损 | 仿真 | 〔0923-We1-G-00-全场连拍 p19〕〔0923-We1-G-00-全场连拍 p20〕 |
| Nokia Bell Labs | 长距/超高分辨OFDR | 首次长距OFDR测约100 km HCF（3–25 m分辨率）；首次HCF侧壁背散分布式测量（124 µm，5 km）；HCF背散比SMF低30/45 dB；热敏感比SMF小22倍；相干OFDR已测>4条海缆 | 实验（自称首次） | 〔0923-We3-I-00-全场连拍 p43〕〔0923-We3-I-00-全场连拍 p35〕 |
| 北邮/中国电信 | 物理驱动迁移学习预测HCF DCI OSNR | 91个现网样本适配，16个盲测：MAE 0.328 dB（解析0.478、纯数据0.434），RMSE降64% | 现网数据 | 〔0922-Tu1-B4-北邮 p11〕 |

### 2.10 网络智能化与AI运维（单独一节）

**2.10.1 标准与架构**：ITU-T ION-2030分"ION-2030 for AI"与"AI for ION-2030"，交付物含GSTR.ION-aiDC，中国电信邀请业界加入TR.ION-aiDC〔0920-am-Su1-C-00-全场 p9〕〔0920-am-Su1-C-00-全场 p29〕。ETSI TeraFlowSDN以图上下文联合优化网络与算力；三层闭环：快（亚秒，重路由）、中（近实时，切片）、慢（需求预测）〔0920-pm-Su4-C-05-CTTC p8〕。Telefónica：读/写Agent分离（Read Agent经API读状态，Configuration Agent经受治理工作流写），架构含MCP网关（RBAC、Schema校验、审计）、NSO（Dry Run/Commit/Rollback）、Ollama 72B，Agent A=ZR+开通〔0923-We-F-00-标准化专场II连拍 p23〕〔0923-We-F-00-标准化专场II连拍 p24〕。

| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Chalmers | T-API合规ReAct智能体（CORONET CONUS，198条fiber链路，GNPy） | 通过率（Generic/Single/Multi）：Qwen2.5 32B Inst 57%/36%/90%；Qwen3.5 35B 58%/27%/55%；4B 20%/18%/28%；平均token 30.3k/10.1k/10.6k；结论"尚未"可生产 | 数字孪生实验 | 〔0923-We2-C2-1339-符合T p11〕〔0923-We2-C2-1339-符合T p12〕 |
| 北邮 | Skill+SOP链路故障诊断LLM智能体 | token减少86%，RCA准确率100%（光纤断裂、弯曲，100次随机跨段） | 测试床 | 〔0923-We2-C1-939-北邮 p13〕〔0923-We2-C1-939-北邮 p12〕 |
| 北邮/中国电信 | A2A多智能体服务开通 | 10/10任务完成；A2A开销58–120 ms/任务；Strategy Agent约23.8–49.9 s；跨ADK/LangGraph路由准确率100%；引其ECOC 2025首次L4自治现网试验 | 德国拓扑仿真 | 〔0924-Th1-G3-北邮 p13〕〔0924-Th1-G3-北邮 p14〕 |
| Adtran | MCP智能体IPoDWDM生命周期 | 演示自然语言开通E2E服务，193.1 THz、75 GHz，返回Success；性能查询Pre-FEC BER 6.980e-03，SNR 14.3 dB，OSNR 26.0 dB；GNPy估计与测量OSNR落在曲线附近；当前假设单Agent | 测试床演示 | 〔0923-We2-C4-731 p8〕〔0923-We2-C4-731 p10〕 |
| Trinity College Dublin | AI-NNC六场景光网络控制 | 成功率（Equalize/Flatten/Hitless/Provision/Recover/Reroute，各10次）：Intent层全部10/10；Network层10/9/1/9/9/5；Device+层7/0/6/10/1/0；Device层4/0/6/9/3/0 | 测试床实验 | 〔0920-pm-Su4-H-03-Trinity p8〕 |
| NTT | 光网络数字孪生（ONDT） | 现网试验：Galway–Dublin 280 km暗光纤，光纤与放大器设置事先未知，QoT预测误差约1 dB，整个过程约6小时；GSNR约18.3–21.5 dB（读数） | 现网试验 | 〔0920-pm-Su4-H-05-NTT p9〕〔0920-pm-Su4-H-05-NTT p10〕 |
| Chalmers/TalTech | AI监测权衡 | 监测配置数据率跨约九个数量级；跨系统泛化：O→O 88.85%，C→C 98.63%，C→O 60.59%，联合训练91.11%（OCR未逐格核对） | 综述+案例 | 〔0924-Th1-G5-Chalmers与TalTech p17〕〔0924-Th1-G5-Chalmers与TalTech p24〕 |

---

## 3. 厂商与客户态势

### 3.1 AIDC/云客户与运营商
- **Meta**：骨干去转发器同容量约降80%功耗；海缆侧称2 Pbps@TA在现有供电下不可能，Petal（预计2029年，OCR）为首条大规模MCF海缆〔0921-MF-am-T08-1220-Meta p10〕〔0921-Mo3-G1-Meta p7〕。
- **Microsoft Azure**：HCF最积极推动者，多个Region已运营，未来12个月计划部署12,000 km+〔0922-Tu3-H1-MicrosoftAzureFiber p29〕。
- **OVHcloud**：区域Fabric环，>10 km用800G ZR+〔0920-am-Su1-C-00-全场 p16〕。
- **中国电信**：G.654.E≤0.172 dB/km、50 ms WSON、800G现网试验、1.6T实验室，主推ITU-T TR.ION-aiDC〔0923-MF-00-上午连拍 p7〕。
- **中国移动**：现网HCF，两年无退化，推动CCSA/ITU-T SG15标准〔0920-pm-Su4-B-03-中国移动 p7〕。
- **BT**：400G（2025）→800G（约2029）→1.6T（2030+），提出需新光纤类型/更多频谱〔0920-am-Su1-C-00-全场 p25〕。
- **NTT（IOWN）**：OSaaS、多厂商多域ONDT现网试验〔0920-pm-Su4-H-05-NTT p10〕。**Telefónica**：读写Agent分离与MCP网关〔0923-We-F-00-标准化专场II连拍 p24〕。

### 3.2 设备商
- **Nokia**：三类部署"互补"（Embedded/Thin Transponder/IPoDWDM）；Huron DSP、XPO 12.8T、海缆可插拔ICE-X；同时主张SSMF仍胜〔0921-PF-待定-Nokia p13〕〔0920-pm-Su3-D-05-Nokia p6〕。
- **Ciena**：WaveLogic 6 Nano与Extreme并行（Metro +50%）；12.8T Coherent-Lite XPO；Bifrost 18 Tb/s；HCF多跨测试570 km、5家供应商〔0923-MF-00-上午连拍 p70〕〔0923-MF-Ciena-空芯光纤 p5〕。
- **Huawei**：234 GBd实时2.0 Tb/s〔0923-We2-I-00-全场连拍 p43〕。**Adtran**：无中继放大器经济学、MCP智能体〔0920-pm-Su3-B-04-Adtran p16〕。
- **ASN**：HCF海缆保守立场；11,265 km ST-DNANF量产统计平均0.118 dB/km（1550 nm）〔0920-pm-Su4-B-04-ASN p3〕。**NEC**：48根200 µm 2芯光纤@17 mm缆，Google-NEC约1500 km MCF段已部署〔主分析师笔记09-NEC Su2-B-05〕。

### 3.3 模块/器件商与光纤商
- **Acacia（Cisco）**：800ZR+领先供应商，>75,000只〔0920-pm-Su4-A-03-Acacia p3〕。**Coherent**：LS200紧凑线路系统〔0923-MF-00-上午连拍 p19〕。
- **Lightera（Furukawa）**：2芯MCF实时无中继52.8 Tb/s，HCF与O波段BDFA〔0921-Mo3-待定-Lightera p5〕〔0920-pm-Su3-B-05-Lightera p8〕。
- **YOFC**：GTA-ST-HCF 0.032 dB/km，参与532 km与266 km PDP，102 nm C+L放大器〔0920-pm-Su3-B-01-长飞YOFC p13〕〔0922-Tu1-D1-长飞 p5〕。
- **Linfiber**：中芯路线，单塔月1273.59 km，产能预测283座塔〔0920-pm-Su3-B-02-Linfiber p6〕〔0921-Mo3-B1-领纤Linfiber p69〕。**Sumitomo Electric**：SMF记录0.138 dB/km，Petal MCF合作〔0921-Mo3-G1-Meta p15〕。**Amonics**：1 µm YDFA〔0924-PDP-A-2 p9〕。

### 3.4 芯片商
- **Marvell**：Libra 800G与Electra 1.6T（2 nm）ZR/ZR+ DSP，集成MACsec〔0923-MF-00 p3〕〔0923-MF-00 p4〕。**NTT**：ExaSPEED800，片上LPM/PDL/NLI〔0922-Tu4-H3-NTT p25〕。**Huawei/HiSilicon**：CMOS ASIC+AI核，234 GBd〔0923-We2-I-00-全场连拍 p44〕。**Ciena**：2 nm CMOS 3.2T Coherent-Lite ASIC〔0920-pm-Su4-A-02-Ciena p7〕。**Nokia**：Huron DSP〔0921-MF-am-T05-1120-Nokia p10〕。

---

## 4. 学术关键突破（按影响力排序）

| # | 机构 | 论文号/文件名 | 突破点 | 数字 | 索引 |
|---|---|---|---|---|---|
| 1 | Nokia Bell Labs/ASN/YOFC | PDP-A-3 | **PDP/record**：532 km HCF全C波段无中继，首次完整C波段 | 30.66 Tb/s（ROPA）/15.73 Tb/s；2×266 km；跨段损耗57.2 dB | 〔0924-PDP-A-3 p22〕 |
| 2 | Nokia Bell Labs | PDP-A-5 | **PDP/record**：450 GBd全电I/Q单波长 | 3.83 Tb/s，PS 64QAM熵5.3 | 〔0924-PDP-A-5-NokiaBellLabs p13〕 |
| 3 | Microsoft/Southampton | PDP-A-1 | **PDP/首次**：C波段零色散且电信级损耗HCF | 0.2 dB/km（HF-3/5），PAM4 BER较标准HCF低约一个数量级 | 〔0924-PDP-A-1 p18〕 |
| 4 | UCL/Microsoft/Lightera | PDP-A-4 | **PDP/首次**：长距双向O+C，缩径190 µm HCF | 2024 km，GMI 51.9+53.9 Tb/s | 〔0924-PDP-A-4 p14〕 |
| 5 | Microsoft/Amonics/Nokia Bell Labs | PDP-A-2 | **PDP/首次**：全相干1 µm HCF系统 | 53.3 Tb/s，106.1 km，244×32 GBd | 〔0924-PDP-A-2-MicrosoftAzureFiber p14〕 |
| 6 | Huawei | We2-I（234 GBd） | **首次**实时2.0 Tb/s相干收发机，称记录波特率 | 234 GBd，60 km无误码，Q余量>0.6 dB | 〔0923-We2-I-00-全场连拍 p43〕 |
| 7 | Ciena/Meta | Mo3-待定（Bifrost） | **record**实时海缆传输；首次跨太平洋实时800G | 18 Tb/s，16,608 km，298.9 Pb/s·km，4.57 b/s/Hz | 〔0921-Mo3-待定-Ciena p5〕 |
| 8 | Lightera/Cisco | Mo3-G6 | **record**实时2芯MCF无中继 | 52.8 Tb/s，303.4 km，无XT代价 | 〔0921-Mo3-待定-Lightera p6〕 |
| 9 | TU/e/NICT | We2-H1 / JLT 2026 | **record**容量距离积；19芯RC-MCF于125 µm包层 | 434.6 Tb/s@8,610 km，3.74 Eb/s·km；568.8 Tb/s@5,166 km | 〔0923-We2-H1-1419-埃因霍温 p22〕 |
| 10 | Aston/Lightera | Tu1-G5 | **record**（GMI）O波段相干 | 172.87 Tb/s（GMI），16.14 THz，633路 | 〔0922-Tu1-G5-Aston大学 p12〕 |
| 11 | Linfiber/暨南大学 | 0920-pm-Su3-B-02 | **称最高**AR-HCF容量距离积；在线去CO2 | 24.8 Tb/s@12,113 km；300.4 Pb/s·km；中位<0.039 dB/km | 〔0920-pm-Su3-B-01-长飞YOFC p28〕 |
| 12 | NTT | Tu4-H2/H3 | **首次**可插拔DSP芯片上分布式PDL监测；片上LPM/NLI | 单PDL<0.5 dB；多PDL<1.0 dB | 〔0922-Tu4-H2-NTT p6〕 |
| 13 | KIT/DTU | Tu1-G2 | **首次**无源相干克隆暗孤子微梳；首次Kerr梳并行零差多波长相干 | 24路，净8.3 Tbit/s/偏振 | 〔0922-Tu1-G2-KIT p9〕 |
| 14 | Nokia Bell Labs | We3-I（OFDR） | **首次**长距OFDR测约100 km HCF；HCF侧壁背散分布测量 | 3–25 m分辨率；124 µm@5 km | 〔0923-We3-I-00-全场连拍 p43〕 |
| 15 | Nokia Bell Labs（同上团队） | Mo3-F5 | PAS+SPC(3,4)回收BMD损耗 | 最多0.9 dB（SE 9 b/s/Hz） | 〔0921-Mo3-F5-NokiaBellLabs p15〕 |
| 16 | 上海交大等 | We3-D5 | **record/首次**DP-CADD 4-D集成DP-DD接收机（源自ECOC 2023 PDP） | 净426 Gb/s，11.8 b/s/Hz | 〔0923-We3-D5-上海交大 p15〕 |
| 17 | NICT/Hamamatsu/UCLA | 0920-pm-Su4-A-05 | 1抽头光延迟线与成对传输打破IM/DD色散壁垒（作者称C波段100 GBd 80/100 km记录级低DSP复杂度，引OFC'24） | 约100 km@224 GBd（图注） | 〔0920-pm-Su4-A-05-NICT p12〕 |

---

## 5. 分歧、争议与反常识

**5.1 HCF在海缆是否已有系统级优势。** ASN：今天HCF设计外径大、光纤对数受限，6000 km、≤48 FP下约1.1 Pbps对SCF约1.25 Pbps；0.05对0.08 dB/km最优跨段容量仅多约6%〔0920-pm-Su4-B-04-ASN p10〕〔0920-pm-Su4-B-04-ASN p11〕；但无空间约束时能耗降2x、容量潜在翻倍〔0920-am-Su2-B-06-ASN p2〕。对方：Meta称0.15→0.05 dB/km可使中继器减为1/3（OCR）〔0921-Mo3-G1-Meta p14〕；532 km、266 km跨段给出陆地与无中继正面证据〔0924-PDP-A-3 p24〕；Nokia称HCF仅低时延有价值〔0920-pm-Su3-D-05-Nokia p3〕。判别点：外径350 µm对200 µm，HCF约16 FP对减径SCF约48 FP〔0920-pm-Su4-B-04-ASN p8〕。

**5.2 长途HCF的GLA：光纤层根除还是系统层绕行。** Linfiber：在线去CO2使845.8 km光纤吸收中位<0.039 dB/km，称"剩余障碍是有明确解法的工程问题"〔0920-pm-Su3-B-01-长飞YOFC p29〕。Ciena：无单个样品同时满足各距离目标，GLA是长途主限制，1000 km时近1/2的L波段可能不可用〔0923-MF-Ciena-空芯光纤 p14〕。UCL仿真：L波段GLA主导，8×125 km SMF优于更短跨段HCF〔0922-Tu3-H3-UCL p20〕。Nokia Bell Labs：系统层绕行可行，GLA下>1T可到1500 km以外〔0922-Tu3-H2-NokiaBellLabs p12〕。

**5.3 0.03 dB/km大芯还是中芯务实。** Linfiber自述大芯0.038 dB/km但微弯与线缆密度差，"工业应用价值有限"，主推中芯（平均0.09 dB/km）〔0920-pm-Su3-B-01-长飞YOFC p23〕；YOFC给出长途0.032 dB/km与DCI减径两套设计，主张"做市场合适的方案"〔0920-pm-Su3-B-01-长飞YOFC p16〕。不同结构互连损耗最低仍>0.09 dB，远高于G.652.D/G.654.E约0.03 dB〔0920-pm-Su4-B-03-中国移动 p8〕。

**5.4 2 km以上是IM/DD还是Coherent-Lite。** 相干侧：IM/DD的O波段可用谱2 km后<45%，Broadcom报告2 km处<10%〔0920-pm-Su4-A-05-NICT p9〕；Acacia称400G/lane时>2 km需相干〔0920-pm-Su4-A-03-Acacia p5〕。保留侧：Nokia称1.6T下IMDD与CL功耗相近（读数估计，800G约18/28/30 W），0–10 km已有五个标准〔0921-MF-am-T05-1120-Nokia p4〕；NICT提出光域1抽头延迟线可能越过色散零点〔0920-pm-Su4-A-05-NICT p12〕。

**5.5 可插拔对嵌入式：功耗还是容量。** Nokia海缆：可插拔约70–100对嵌入式约425–680 pJ/bit，但标准CD耐受不足（OIF 800GZR为2400 ps/nm）〔0920-am-Su2-B-04-Nokia p3〕〔0920-am-Su2-B-04-Nokia p5〕。Ciena：转发器容量在Tasman Express多16%、Metro多50%〔0923-MF-00-上午连拍 p70〕。Nokia（PF）：1300 km长途嵌入式容量多63%，可插拔省52% CapEx〔0921-PF-待定-Nokia p11〕。

**5.6 SSMF仍胜出还是SDM/MCF必要。** Nokia：SSMF一直获胜，2-core C波段可能优于C+L〔0920-pm-Su3-D-05-Nokia p6〕。Meta/NEC：供电限制下1 Pbps@TA需48FP等效，NEC称跨洋Pb级MCF系统即将到来〔0921-Mo3-G1-Meta p9〕〔主分析师笔记09-NEC Su2-B-05〕。TU/e：38×38实时MIMO的功耗/时延尚未演示〔0923-We2-H1-1419-埃因霍温 p19〕。

**5.7 LLM智能体可否生产化。** 乐观：BUPT token减86%、RCA 100%；A2A 10/10任务；Trinity 13天无人值守〔0923-We2-C1-939-北邮 p13〕〔0920-am-Su2-H-02-Trinity p9〕。谨慎：Chalmers"尚未"；Trinity设备层直接操控Flatten/Reroute成功率0/10；Politecnico di Milano称零接触Agent不现实〔0923-We2-C2-1339-符合T p13〕〔0920-pm-Su4-H-03-Trinity p8〕。反常识：指令微调模型优于推理模型〔0923-We2-C2-1339-符合T p13〕。

**5.8 追峰值波特率还是做产品族。** Nokia："不是峰值波特率"，按覆盖选引擎〔0920-pm-Su4-A-04-Nokia p4〕；Bell Labs："不要等CMOS"，展望10×450 GBd替代32×800ZR覆盖4.8 THz〔0924-PDP-A-5 p15〕。

---

## 6. 判断与观察点

### 6.1 技术成熟度判断（基于笔记中口径）

| 技术 | 成熟度判断 | 依据 |
|---|---|---|
| 800ZR/ZR+可插拔 | 规模量产与部署 | >75,000只（Acacia自报）；ICE-X现场600G/λ 2,841 km〔0920-pm-Su4-A-03-Acacia p3〕〔0920-am-Su2-B-04-Nokia p8〕 |
| 1600ZR/ZR+ | 2026年样品/爬坡 | IA约Q2/Q3 2026；OIF 1600ZR straw ballot〔0920-pm-Su3+Su4-A-00-全场 p120〕〔0921-MF-am-T05-1120-Nokia p6〕 |
| Coherent-Lite（园区） | 标准讨论中，原型展示 | OIF 1600CL讨论；Ciena 12.8T XPO展示；Marvell Aquila（OCR）〔0921-MF-am-T05-1120-Nokia p6〕 |
| 2T/3.2T单载波 | 实验室（实时2.0T；离线3.83T） | 234 GBd实时；450 GBd离线〔0923-We2-I-00-全场连拍 p43〕 |
| HCF在DCI/城域 | 现网商用起步 | 中国移动首个商用34 km；Microsoft Region承载〔0923-We3-I-00-全场连拍 p82〕 |
| HCF长途/无中继 | 实验室与环路验证 | 532 km；GLA、IMI、外径未全解 |
| MCF海缆 | 首条大规模部署预计2029（Petal，OCR） | 〔0921-Mo3-G1-Meta p15〕 |
| 片上LPM | 已进入芯片，OFC 2026 PDP；"已商业部署"（Politecnico di Torino称） | 〔0923-We1-G-00-全场连拍 p93〕 |
| LLM智能体 | 原型/测试床 | Chalmers"尚未" |

### 6.2 时间窗口与含义
- 2026–2027：800ZR+规模化与1600ZR/ZR+导入；园区Coherent-Lite标准化（OIF 1600CL）。BT约2029年800G、Meta站房2027+多轨（>18 kW/rack）、Petal 2029〔0920-am-Su1-C-00-全场 p25〕〔0921-MF-am-T08-1220-Meta p13〕。
- HCF：Microsoft未来12个月12,000 km+部署；产能瓶颈（每线30,000 km/年）决定2027年后规模〔0922-Tu3-H1-MicrosoftAzureFiber p29〕〔0921-Mo3-B1-领纤Linfiber p69〕。
- 对设备商：可插拔/嵌入式/IPoDWDM三类并存，全谱转发器（fiber作为部署单位，51.2T C&L示例）与XPO 12.8T路线并行〔0923-MF-00-上午连拍 p77〕；LPM/NLI监测使裕量削减有依据（"依据实测而非设计固定值"）〔0922-Tu4-H3-NTT p25〕。
- 对模块商：园区FEC 50–75 ns、ZR笼内28–40 W、2 nm CMOS、液冷（ASHRAE W4 45 °C）成为约束；模块在海缆场景需更高CD耐受（20,000 ps/nm）与150 kHz线宽〔0920-am-Su2-B-04-Nokia p3〕。
- 对芯片商：DSP监测功能（CD、DGD、PDL、SOP、SNR、BER、LPM、NLI）成为标配。

### 6.3 未来12–24个月要盯的指标（可量化）
1. 1600ZR/ZR+实测：236/252 GBd下Q余量与模块功耗。
2. Coherent-Lite FEC延迟（50–75 ns）与OIF 1600CL冻结；2 km处OCS约8 dB损耗预算的实测。
3. HCF：GLA深度（长途目标0.003–0.001 dB/km）、IMI（-59 dB/km以下）、单纤拉丝长度、累计产量、价格（对比>\$3000–5000/km）。
4. 海缆：单缆容量对PFE电压（18 kV）与DCR（1 Ω/km）；MCF海缆Petal进展；HCF海缆外径（对比350 µm对200 µm）。
5. 实时MCF/SDM：38×38实时MIMO功耗；耦合芯SMD（<10 ps/√km）。
6. LPM：距离分辨（步长<1 km）。
7. LLM智能体：Multi-Call式高层工具抽象的通过率（>90%对Generic 57%）。
8. 宽带放大：S/O/L波段饱和输出（>23 dBm）、NF（<6 dB）、PCE（目前铋/铥类约1–20%量级）。

---

## 7. 推荐配图

1. 0920-pm-Su4-A-04-Nokia p13 — 1600ZR单载波与1600ZR+双子载波架构 — 判断1。
2. 0920-pm-Su4-A-04-Nokia p12 — 园区FEC三方案波特率-延迟-RSNR-功耗表 — 判断2。
3. 0920-pm-Su4-A-05-NICT p9 — IM/DD与相干可用带宽随距离曲线 — 判断2、分歧5.4。
4. 0920-pm-Su4-A-02-Ciena p7 — 12.8T Coherent-Lite XPO结构与<240 W — 判断2。
5. 0921-MF-am-T05-1120-Nokia p3 — DSP功耗饼图与ASIC/光学功耗对比 — 判断1机制。
6. 0924-PDP-A-5-NokiaBellLabs p8 — 单波长速率对波特率与领先量产时间缩短 — 判断1。
7. 0923-We2-I-00-全场连拍 p43 — 相干收发机速率年表与234 GBd实时点 — 判断1。
8. 0920-pm-Su3-B-01-长飞YOFC p13 — GTA-ST-HCF 0.032 dB/km损耗谱与IMI — 判断3。
9. 0924-PDP-A-3 p24 — 无中继SOTA容量-距离对比 — 判断3。
10. 0920-pm-Su4-B-02-NokiaBellLabs p22 — 跨洋C波段HCF对SMF容量×距离 — 判断3。
11. 0923-MF-Ciena-空芯光纤 p14 — 各距离段HCF损伤上限表 — 判断3、分歧5.2。
12. 0921-Mo3-B1-领纤Linfiber p69 — 产能预测（283座塔对>1000条线） — 判断3产能约束。
13. 0923-We3-I-00-全场连拍-空芯表征与部署 p82 — 现网试验与首个商用部署地图 — 判断3现网。
14. 0920-pm-Su4-B-04-ASN p10 — SDM长期容量情景 — 判断4、分歧5.1。
15. 0920-pm-Su4-B-04-ASN p8 — 外径决定光纤对数 — 分歧5.1。
16. 0921-Mo3-G1-Meta p7 — 1 Pbps与2 Pbps的PFE电压限制 — 判断4。
17. 0921-Mo3-待定-Ciena p5 — 18 Tb/s优化信道方案与余量 — 判断4。
18. 0920-am-Su2-B-04-Nokia p5 — 嵌入式对可插拔pJ/bit与机架单元 — 判断4、分歧5.5。
19. 0922-Tu4-H2-NTT p15 — 两个PDL定位与量化 — 判断5。
20. 0922-Tu4-H3-NTT p25 — DSP监测功能版图 — 判断5。
21. 0923-We2-C2-1339-符合T p11 — 三种工具变体×四模型通过率 — 判断5、分歧5.7。
22. 0920-pm-Su4-H-03-Trinity p8 — 四种接口×六场景成功率热图 — 判断5、分歧5.7。
