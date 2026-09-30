---
title: "方向4 Scale Up 综合洞察"
tags:
  - ECOC2026
  - 综合洞察
---

# 方向4：Scale-up/in（CPO/NPO/XPO，未来WSE晶圆级、OCS）

> 口径约定：【自报】讲者/厂商幻灯片自述；【仿真】仿真/建模；【实验】实验室或展台实测；【现网】生产环境统计。带“OCR/读图/存疑”者保留原标记。索引格式〔文件名简写 pN〕，文件名为PDF去掉.pdf后缀的简写。

## 0. 一句话结论 + 5条核心判断

**一句话结论**：Scale-up光互连在224G/lane世代的分歧不在“光能不能做”，而在“谁承担可维护性与可靠性”：NPO（可维护、生态开放）与可插拔XPO在2026–2027年抢占落地窗口，CPO在scale-out先量产、scale-up要到2027/28；宽而慢（VCSEL/DWDM/microLED）在能效上有一个数量级的纸面优势，但尚缺现场可靠性数据与统一核算边界；OCS是scale-up的下一层变量，但插损与故障半径尚未闭合。

**判断1：形态时间线已排出：CPO scale-out约2026、scale-up 2027/28；NPO与XPO是224G世代的落地主形态。**
- 数字：Ciena判断CPO在scale-out约2026、scale-up 2027/28，机架从72 XPU到576+ XPU【自报】〔0920-pm-Su3-I-05-Ciena p10〕；Oracle称224G/lane已适合试用NPO/CPO，>224G时CPO/NPO可能是唯一出路【自报】〔0920-pm-Su3-A-03-Oracle p13〕；XPO MSA于2026-03-20成立、150家成员，XPO 1.0于2026-07-31发布，量产模块预计2027Q1【自报】〔0921-Mo4-待定-Arista p24〕；Open CPX 1.0于2026-09-16发布，6.4/7.2 Tbps、32/36 lane、最高212.5 Gbps/lane〔0920-am-Su2-A-01-UBC p4〕。
- 机制：200G/lane下可插拔主机电通道损耗约22 dB，NPO 7–10 dB，CPO<5 dB【自报】〔0922-PF-1405-NewPhotonics p5〕；电通道缩短使DSP可退化为线性架构。

**判断2：pJ/bit的差距主要来自SerDes/DSP是否存在与核算边界，而非调制器本身；各家数字不可直接横比。**
- 数字：NVIDIA 1.6T：FRO 14 pJ/b（25 W）、TRO 10、LPO 6.4（11 W）、CPO 4（7 W）【自报】〔0920-am-Su2-I-01-NVIDIA p11〕；Ciena：DSP 18.5、LRO 12.5、LPO 6.5、NPO 5、CPO 3 pJ/bit【示意/自报】〔0920-pm-Su3-I-05-Ciena p5〕；VCSEL宽慢：Coherent 2D VCSEL NPO 1.2 pJ/bit【自报】〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p51〕，但TeraHop横比图中uVCSEL约5.75、uLED约6.0 pJ/b（读图估计）〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p63〕。
- 机制：Meta指出链路功耗“主要取决于SerDes个数”〔0920-am-Su1-B-01-Meta p1〕；Coherent要求先统一核算边界（含时钟/远端激光/reverse gearbox）〔0920-pm-Su4-I-04-Coherent p5〕。

**判断3：可靠性/可维护性/连接器取代能效，成为CPO/NPO选型的决定性约束。**
- 数字：Oracle现网：>90%链路故障、97%收发器更换源于连接器污染；409.6T CPO交换机=4096个箱级潜在单点故障【现网/自报】〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p38〕；EBO MSA：51.2T DR方案光纤连接1088个，3σ首过99.865%时板级光纤组装良率仅23.0%（FR4 67.8%）【计算】〔0922-MF-am-1220-EBOMSA p8〕；Huawei计算CPO 32光引擎总良率0.95^32≈19.4%【自报】〔0921-MF-am-T04-1100-华为 p9〕。
- 机制：CPO无前面板热插拔，修复时间从分钟增至小时甚至数天〔0923-MF-美团-市场聚焦 p14〕。

**判断4：铜的边界已到1–2 m（200G）并在400G继续缩短，但“铜+光混合”在至少400G世代仍是主流；铜与光之间出现介质波导/RF的第三条路。**
- 数字：铜缆可达距离：200G约1 m、400G约1 m【OpenAI读图】〔0920-am-Su1-B-02-OpenAI p4〕；Marvell给出200G 2.5 m、400G 1.25 m〔0920-pm-Su4-H-04-Marvell p5〕；Ciena：混合介质使铜域从72 XPU@14 Tbps扩到256 XPU@25 Tbps，铜至少用到400G世代〔0921-Mo12-A3-Ciena p18、p33〕；AttoTude介质波导448G约10 m、DiAx+约35–40 m（BER 1E-5/1E-7 门限）【自报】〔0920-am-Su1-B-06-AttoTude p6〕。
- 机制：448G干净信道带宽约90 GHz，受连接器限制〔0923-MF-00-上午连拍 p33〕。

**判断5：“宽而慢”与OCS是scale-up的两个未验证变量：前者缺现场数据，后者卡在插损/端口密度/重锁定。**
- 数字：Lumentum 1060 nm VCSEL在115 °C烘箱（Tj 181 °C）8 mA下86个单元5000 h无失效，目标<50 dppm【自报】〔We5-I Lumentum p13、p15〕；OpenAI认为慢宽/快宽“需要现场验证”〔0920-pm-Su4-I-02-OpenAI p11〕；NVIDIA列出OCS四道障碍：插损（路径至少4个bulkhead连接器，DR4余量3 dB、FR4 4 dB）、成本（目标每1RU>256双工端口）、可靠性、端口密度〔0920-am-Su2-I-01-NVIDIA p18〕；Oriole：只有“超快交换+超快收发器重锁定”才有>90%吞吐，标准收发器即使配<10 ns开关也<1%【自报】〔0920-pm-Su3-A-04-Oriole p9〕。
- 机制：宽度带来封装面积与连接器复杂度，“难以回退”〔0920-pm-Su3-I-05-Ciena p10〕。

---

## 1. 需求与网络架构

### 1.1 客户/运营商口径的需求数字
| 机构 | 需求/架构事实 | 口径 | 索引 |
|---|---|---|---|
| OpenAI | 自研Jalapeño：本地域128颗经Broadcom TH6，全局域2048颗（TH6 rail 0–7），“half flattened”两级Clos；同吞吐点相对GB300 MTP约1.8×更低延迟（最小端到端请求延迟1.65 s vs 3.69 s） | 自报/仿真（Hot Chips 2026披露） | 〔0920-pm-Su3-A-02-OpenAI p7、p8〕 |
| Oracle OCI | GPU集群2020→2026：16,384→131,072（8×）；NIC 25G→1600G，“256×集群性能提升”；网络对算力的相对花费逐年上升“不可持续” | 现网自报 | 〔0920-pm-Su3-A-03-Oracle p2〕〔主分析师笔记01 Oracle p2〕 |
| Microsoft Azure | 六类光互连用例，近期机会为交换式scale-up（A）与内存解耦（D）；OCI带宽路线：200G今天、400G 2027(?)、800G TBD >2030(?)；内存解耦指标：<5 ns、<4 pJ/bit、机架内1–3 m→行级20–50 m | 自报 | 〔0921-Mo4-待定-MicrosoftAzure p3、p6、p8〕 |
| NVIDIA | 512K Blackwell GPU数据中心：GPU 600 MW，约7100机架，约1.8 M光收发器；光网络功耗约占算力10%；10万服务器收发器功耗：传统云2.3 MW、AI工厂40 MW | 自报 | 〔0920-am-Su2-I-01-NVIDIA p5、p6〕 |
| NVIDIA | scale-up限制：GPU带宽2.4→3.6→7.2 Tb/s，GPU域8→32→72→100s，机架功率25 kW→150 kW→1 MW，GPU-L1距离0.5→1.5→最多30 m（原文带问号），“Cu reaches its limit” | 自报 | 〔0920-am-Su2-I-01-NVIDIA p8〕 |
| Huawei | Atlas 900（2025）384 NPU：6912× 400G SR8 VCSEL oDSP；Atlas 950（2026）：4096× 800G SR8 VCSEL LPO（对应1024 NPU），链路级重传+2×2模块级交叉备份；FOM=(Tbps/mm)/((pJ/bit)(ns))×reach×MTTF | 自报 | 〔0920-am-Su1-A-03-华为 p2、p3〕 |

### 1.2 带宽层级与架构演进
- **带宽阶梯**（Ciena，相对比例）：die-to-die 100%、内存10%、scale-up 1%、scale-out/across 0.1%；scale-up本质是“在I/O reach内塞进一个radix的硬件”〔0921-Mo12-A3-Ciena p33〕。OIF 72 GPU Pod示例：scale-out 72链路×800G=57.6T；scale-up 2592链路×400G=1036.8T，scale-out约为scale-up的1/10〔0923-MF-00-上午连拍 p44〕。
- **前面板密度**（1OU、200G/lane）：OSFP 70 Tbps；XPO+fly-over铜200 Tbps；铜连接器230 Tbps；微型光连接器624 Tbps（bidi+WDM）【自报】〔0921-Mo12-A3-Ciena p15〕。
- **光纤数量爆炸**：每机架光纤数：Vera Rubin NVL72（2026）~1k→Rubin Ultra NVL576（2027）~10k→Feynman NVL1152（2028）~30k→Feynman Next（2029+）~45k；16f跳线安装时间约9/95/280/420小时【Corning估算】〔0923-MF-康宁-市场聚焦 p4、p6〕。
- **网络分层**（LightCounting）：scale-in毫米级“wide-slow，未来或为光”；scale-up约1 m“contested，铜+光，可插拔/CPx”；scale-out“SiPh 448G/lane，可插拔+部分CPO”；2026年硅光收发器份额首次>50%〔0920-pm-Su3-A-01-LightCounting p3、p5〕。

---

## 2. 技术路线与关键指标

### 2.1 形态与能效：FRO/LRO/LPO/NPO/CPO/XPO（含1.6T及以上）
| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| NVIDIA | 1.6T：FRO/TRO/LPO/LPO+CPC/CPO | 14/10/6.4/6.4/4 pJ/b；25/18/11/11/7 W；可插拔电信号损耗22 dB vs CPO 4 dB；每1.6T用2个CW激光器 | 自报 | 〔0920-am-Su2-I-01-NVIDIA p11、p12〕 |
| NVIDIA | Spectrum-X CPO（COUPE） | 相对可插拔：4×更少激光器、5×更低功耗、10×更高MTBI；CPO约4 pJ/b，节省约72%收发器功耗（AI工厂网络占总功耗6–8%→降5×） | 自报 | 〔0920-pm-Su3-A-05-NVIDIA p8〕；〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p45〕 |
| NVIDIA | 微环调制器发射机 | 212.5 Gbps/通道；16通道在OFC 2026展会连续3天，总BER<1E-14；引擎单通道212.5G生产环境BER<1e-10 | 展台实验/自报 | 〔0920-pm-Su3-A-05-NVIDIA p13〕；〔0921-Mo4-待定-NVIDIA p5〕 |
| Ciena | DSP/LRO/LPO/NPO/CPO（XPU海岸线约束） | 30 W(18.5)/20 W(12.5)/10 W(6.5)/8 W(5)/5 W(3 pJ/bit)；448G下PCB到前面板连接“breaks down” | 示意/自报 | 〔0920-pm-Su3-I-05-Ciena p5〕 |
| OIF | 72 GPU Pod（100 GBd PAM4） | CPO 4、LTLR 6、RTLR 10、RTRR 15 pJ/b；Pod总功率CPO约90 kW vs 可插拔约100 kW（读图估计） | 标准组织/建模 | 〔0923-MF-00-上午连拍 p44〕 |
| Huawei | Hi-ONE 7.2T NPO（36×224G，板载内置激光，免光纤） | 相对1.6T模块：带宽4.5×、时延100→10 ns（-90%）、功耗15→5 pJ/bit(-66%)、故障率10 A-fit→A-fit（-90%）（小字读图）；“已量产”；FIT<1（1:1备份） | 自报 | 〔0921-Mo12-00 p100〕；〔0921-Mo12-A5-华为 p9〕；〔0920-am-Su1-A-03-华为 p5〕 |
| Coherent | 6.4T硅光NPO（32×200G）+ELS | 3.5 pJ/bit，15 Gb/s/mm²；ECOC展示NPO+ELSFP典型4.7 pJ/bit | 实验/自报 | 〔0922-MF-am-1000-Coherent p8〕；〔主分析师笔记03 Coherent p7〕 |
| TeraHop | Open CPX 6.4T “Diablo-1” NPO（内置激光，无ELSFP） | 典型<35 W→<5.5 pJ/bit；ASIC到NPO通道损耗约12 dB；Arista称“Industry 1st 100Tbps交换机设计概念” | 自报/实验 | 〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p59、p60、p58〕 |
| NewPhotonics | NPC505（集成激光，可维护4×DR8 6.4T） | 5.5 pJ/b（含激光）；可升级12.8T(448G)或转OCI | 自报 | 〔0922-PF-1405-NewPhotonics p14〕 |
| Arista/TerraHop | 12.8T 8×DR8液冷XPO（64×212G PAM4） | TX平均光功率2.75 dBm、ER 4.33 dB、TECQ 2.39 dB；模块约130 W、约10 pJ/bit（折合每1.6T约16.5 W）；冷却液25–45 °C、0.3 LPM下DSP约50–74 °C、CW激光器约36–57 °C | 实验（Hot Interconnect 2026 / ECOC We5-B3） | 〔0920-am-Su1-B-05-Arista p8〕；〔0923-We5-B-Arista p6、p8、p9〕 |
| Arista/Marvell | XPO 12.8T技术谱（Reach/W/pJ/bit） | ZR 100 km+/300/24；CL 10–20 km/250/20；DR8-LRO 500 m/128/10；DR8-LPO 500 m/80/6；VCSEL-IGB 20–30 m/65/5；RF-Microwave 10 m/50/4；有源铜4 m/50/4 | 自报 | 〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p29〕 |
| Arista | XPO系统效益 | 模块数减8×–16×、交换机减2×–4×、网络机架减4×–8×（前提：10×GPU×4×每GPU带宽≈40×网络I/O）；204.8T交换机：128×1.6T OSFP需4U/1.6 Pb/s每机架 vs 16个XPO约10U/约6.5 Pb/s每ORv3液冷机架 | 自报/建模 | 〔0920-am-Su1-B-05-Arista p3、p4〕 |

### 2.2 CPO/NPO量产与可靠性证据
| 机构 | 数据（条件） | 口径 | 索引 |
|---|---|---|---|
| Broadcom | CPO四代：TH4 Humboldt 100G/lane 25.6T（2022）；TH5 Bailly 51.2T；TH6 Davisson 200G/lane 102.4T（2026）；第4代2028 Next Gen；第4代CPO“>1M device hours with 0 link flaps”（其后文字被遮挡）；32×200G PAM4符合IEEE 802.3dj | 自报 | 〔0922-MF-pm-1400-Broadcom p4、p7〕；〔0921-Mo4-待定-Broadcom p8〕 |
| TeraHop | 已出货>25 M硅光收发器，PIC>100 B器件小时，FIT<0.01；1.6T-DR8 OSFP FIT约0.3–1（量产部署<1）；6.4T NPO-ILS估计约4×1.6T OSFP，<10 FIT | 自报（后者为估计） | 〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p61、p62〕 |
| Lumentum | 1060 nm VCSEL：115 °C烘箱（Tj 181 °C）、8 mA、86单元5000 h无失效；对比850 nm在类似加速应力下>600 h变化、>1600 h灾难性失效；早期失效：顶发射72K发射器9 mA/e 80 °C，96 h累计2失效（28 DPPM）；底发射8.6K发射器100 h内2失效（231 DPPM，均为装配损伤），目标<50 dppm | 实验/自报 | 〔We5-I Lumentum p13–p15〕 |
| Berxel | 单VCSEL<0.03 FIT（累计250亿器件小时无失效）；阵列<0.1 FIT；140 °C、9 mA强应力无失效，折合8 mA 70 °C >7M等效小时 | 自报 | 〔We5-I 博升 p9、p18〕 |
| Credo | 三层Clos、链路MTTF 3×10⁵ h：2023年20k GPU→约3 h一次flap；2025年3M GPU→约48 s；ZeroFlap PILOT：128模块、2个月，GPU利用率约60%→约90%（小样本，讲者自注） | 引Borrill论文/试点 | 〔0923-MF-Credo-市场聚焦 p2、p10〕 |
| Oracle | 800G LPO现网约35万链路：LPO-LPO n=156,591、FRO-FRO n=202,042；中位pre-FEC BER 1.1E-11 vs 1.4E-11；p99 5E-10 vs 3E-8；至少1次down transition：3.244% vs 5.681%（文字将LPO写作LRO，疑笔误） | 现网 | 〔0920-pm-Su3-A-03-Oracle p7〕 |

### 2.3 标准与MSA（OpenCPX / OCI-MSA / XPO MSA / EBO / OIF）
| 标准 | 内容与时间（口径） | 索引 |
|---|---|---|
| Open CPX MSA | 1.0规范2026-09-16：6.4/7.2 Tbps、32/36 lane、最高212.5 Gbps/lane；内置ILM/外置ELM（ELSFP）两种激光；通用socket（机械/电/光/热/CMIS）；不要求热插拔。Type-1：6.4T/socket，64 DPs，高速插座堆叠10 mm；Type-2：7.2T，单连接器7 mm堆叠。成员含Ciena、Coherent、Marvell、Molex、Samtec、TeraHop、Credo、Intel、Lumentum、Lightmatter、Amphenol等（6家创始成员 Ciena、Coherent、Marvell、Molex、Samtec、TeraHop，另有 50+ 贡献者）；Ciena称“70%功耗节省、8×密度”，2027 ramp、6.4T模块标准化、多厂商供应 | 〔0920-am-Su2-A-01-UBC p4〕；〔0923-MF-Semtech-市场聚焦 p8、p9〕；〔0921-MF-am-T03-1040-Ciena p6、p12〕；〔0920-pm-Su3-I-05-Ciena p9〕 |
| OCI-MSA | 2026年3月成立，创始成员Meta、Microsoft、OpenAI、AMD、Broadcom、NVIDIA（logo）；“宽并行、NRZ、双向单纤、标准激光器”；OCI v1.0（200G OCI Line Interface Spec，2026-03-11）：每方向4波长，Group A 1308.00/1310.28/1312.58/1314.88 nm，Group B 1327.69–1334.78 nm，53.125 Gbaud NRZ，单BiDi光纤共8波长；世代：Gen1 200G、Gen2 400G、Gen3 800G；Linear：200G YES、400G MAYBE、800G UNLIKELY；ELSFP：绝对波长精度±0.2 nm、间隔400 GHz、RIN -144 dB/Hz、线宽<1 MHz | 〔0920-am-Su2-A-01-UBC p5〕；〔0922-MF-pm-1400-Broadcom p19〕；〔0920-am-Su1-A-04-AMD p8〕；〔0923-We-F-00 p16、p17〕 |
| XPO MSA | 2026-03-20成立、150成员；XPO 1.0规范2026-07-31发布；量产模块预计2027Q1；204.8T交换平台；400G/lane（25.6T/模块）路线图进行中；称“史上最大光学MSA”；50 V母线，支持500 W模块（10 A@50 V）；两块32通道paddle card背靠背共享中心冷板 | 〔0921-Mo4-待定-Arista p12、p24〕；〔0921-MF-pm-1300-Arista p11、p28〕 |
| EBO MSA | 2026年3月成立，57成员（9家终端用户 AMD、Arista、Cisco、HPE、Meta、Microsoft、Nexthop AI、Nvidia、Oracle + 48家供应商）；扩束到80 µm直径；12芯插芯1000次不清洁重复配接IL变化<±0.1 dB；552对随机配接（8832数据点）平均IL 0.32 dB、99.2%通道<0.7 dB；配接力约降20×；128f（8×16f）规范进行中 | 〔0922-MF-am-1220-EBOMSA p13、p14、p16–p18〕 |
| OIF | 448G：CEI-448G-VSR/LR项目2026年2月启动；12.8 Tb/s NPO模块项目（新，12.8与6.4 Tb/s、200G/lane）；ELSFP（OIF-ELSFP-01.0，2023-08）；光学封装分类FPO/NPO-PCB/NPO-HDI/CPO/CPO-AP，FPO电接口>22 dB/200G，NPO-HDI 13–18 dB/200G | 〔0923-MF-00-上午连拍 p29、p31、p42、p51、p40〕 |

### 2.4 电通道与铜的边界
| 机构 | 数据（条件） | 口径 | 索引 |
|---|---|---|---|
| OpenAI | 铜缆(CR)可达：25G约5 m、50G约3 m、100G约2 m、200G约1 m、400G约1 m；PCIe CopprLink Gen6约2 m、Gen7约1 m | 读图 | 〔0920-am-Su1-B-02-OpenAI p4〕 |
| Marvell | 100G 5 m；200G 2.5 m；400G 1.25 m；800G 0.6 m；1.6T 0.3 m | 自报 | 〔0920-pm-Su4-H-04-Marvell p5〕 |
| Broadcom | 标准BGA C2M插损32 dB@53.125 GHz；ICA/NPO-HDI通道<20 dB，可支持FP LPO并走向400G；FPO-LRO光回环BER<1e-13（参考均衡）vs标准BGA<1e-8；FPO-LPO最好约1e-10、最差约1e-4；400G下线性链路可能成“showstopper” | 实验/自报 | 〔0920-am-Su1-B-04-Broadcom p4、p5、p8、p9、p13〕 |
| Qualcomm | L-CPO：224G下封装损耗约占40 dB链路预算的30–50%，448G下可能“effectively prohibitive”；铜有~5 m功耗与距离墙 | 自报 | 〔0920-pm-Su3-I-04-Qualcomm p4、p5〕 |
| AttoTude | 介质波导DiAx：224G/448G均约10 m；DiAx+约35–40 m（448G，BER 1E-5/1E-7 门限）；损耗约0.8 dB/m（相对26AWG twinax在110 GHz约10 dB/m改善）；twinax 112G 7 m/224G 4 m/448G<1 m；SNR模型DiAx 10 m约21.5 dB（读图）；硅光上变频代价标5–7 pJ/bit、1000×故障率、30×成本（讲者对比标注） | 自报/模型 | 〔0920-am-Su1-B-06-AttoTude p4、p6、p7〕 |
| Credo | 中心交换机铜（fast narrow）单次穿越约14–17 pJ/bit、1.5–2 m（106G DSP SerDes 4 nm与3 nm均3.4 pJ/bit，无改善）vs平坦光mesh约4 pJ/bit、50+ m | 自估算模型 | 〔0920-pm-Su4-I-07-Credo p6〕 |

### 2.5 宽而慢：VCSEL / microLED（含1060 nm与多芯光纤）
| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Coherent | 1060 nm背发射VCSEL阵列（硅中介层） | 16通道(2×8)：32 Gbit/s @6 mA、Vpp 0.4 V无DSP；128 Gbit/s @12 mA、7 tap Rx/Tx，TDECQ 1.95–3.64 dB；37发射器六边形、70 µm间距，106 Gbit/s TDECQ 2.52 dB；带宽密度最高9 Tbit/s/mm²（展望值）；单器件125 °C 32G SNR 6.33 | 实验 | 〔We5-I Coherent p8–p10、p12〕 |
| Coherent | NPO 2D VCSEL | 1.2 pJ/bit，12 Gb/s/mm²，标“INDUSTRY FIRST”；量产就绪1H CY27；2030 SAM：现有\$60B+，加CPO/NPO/C2C \$30B+ | 自报 | 〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p47、p50、p51〕 |
| Coherent | 低电流VCSEL/DWDM核算表 | PAM4 108G VCSEL阵列0.90 pJ/b（实测，总tile约2）；NRZ宽慢阵列0.75（投影）；梳状SiPh 0.369（建模，排除clocking，另需+0.3–0.6）；Broadcom 100G VCSEL 1.0（实测）；2.5D WDM interposer 3.5（建模）；Coherent 106G 1.2/128G 1.0（实测，16CH 2.047T） | 实测/投影/建模混合 | 〔0920-pm-Su4-I-04-Coherent p3–p6〕 |
| Lumentum | 1060 nm VCSEL阵列（倒装背发射，Cu pillar） | 第一代示例：64 Gb/s NRZ×256通道=8 Tb/s，shoreline 2.0 mm，2.5 pJ/bit；S21 25 °C总带宽33.8 GHz、85 °C 25.3 GHz；50 Gb/s NRZ 1 m OM5 ER 4.2 dB；OFC 26演示32 Gb/s、可支持1.5 Tb/s/mm；ECOC 26与Corning、Qualcomm Dragonfly合作直驱chiplet（10 Tbps光引擎） | 实验/自报 | 〔We5-I Lumentum p4、p9、p10、p12〕 |
| Berxel | 1060 nm背发射VCSEL+HCG超透镜 | 106 Gbps PAM4经100 m OM3；3 dB径向容差±22 µm、纵向400 µm；1.6 Tbps共封装TX 16通道×106G；S21>44 GHz、RIN<-150 dB/Hz；212 Gbps PAM4：30 m OM2 TDECQ 3.22 dB、50 m OM5 4.47 dB；50G NRZ @4 mA：100 m OM5+ TDEC 2.68 dB | 实验 | 〔We5-I 博升 p12、p14–p17〕 |

### 2.6 DWDM/多波长与外置光源（ELSFP、梳状、集成激光）
| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| NVIDIA | DWDM NRZ SiPh（COUPE） | 8λ×32 Gb/s NRZ，200 GHz间隔，间隔变化<±20 GHz，功率变化<±0.5 dB，SMSR约60 dB；PRBS31、16小时无误码；未来DWDM 3.5–4 pJ/b含激光，起步8λ每纤400G；scale-up四选项中DWDM NRZ SiPh在岸线密度/光纤带宽可扩展/时延/OCS兼容打勾 | 实验/自报 | 〔0921-Mo4-待定-NVIDIA p8、p11〕；〔0920-am-Su2-I-01-NVIDIA p13〕 |
| NVIDIA | 时钟前传微环DWDM测试芯片（3D堆叠7 nm EIC+65 nm SiPh PIC） | 8路×32 Gb/s+16 GHz时钟，200 GHz间隔；0.8 Tb/s/mm、1.33 Tb/s/mm²、2.78 pJ/b；前传时钟相位裕量0.47 UI @1e-12 | 实验 | 〔0922-Tu1-E5-NVIDIA p4〕 |
| Columbia/Xscape | Kerr梳+DWDM | Nat. Photon. 2023：multi-Tbps单链路<1 pJ/b；CLEO 2026 Highlight：375 mW泵浦，300 GHz梳转换效率63.6%；对商用~100×（BW密度×能效）；Xscape FALCONX 8：原型送样2026Q2、量产爬坡2027Q4 | 实验/自报 | 〔0920-am-Su1-A-05-Columbia p5、p8–p10〕 |
| Chalmers/Solinide | O波段光子分子微梳 | 75 mW泵浦、200 GHz间隔、28条>1 mW线、效率69%（页面标约70%）；100 GHz 55%效率(泵浦8 mW，1480–1640 nm，C/L波段)；建模路线图：150 mW/64线、300 mW/128线（>70%）为建模非实测 | 实验/建模 | 〔0920-am-Su2-A-05-Chalmers p7、p8、p12〕 |
| Quintessent | GaAs QD-on-Si梳/DFB | 单腔单偏置8λ梳，单片输出>80 mW，峰值WPE>20%；+booster SOA：200 mW（>25 mW/λ）、2 dB均匀度；DFB+SOA 8×200 GHz SMSR>55 dB，最高85 mW；反馈-15 dB时RIN约-150 dBc/Hz；3000颗激光器WPE集中25–30%；750+片外延 | 实验/自报 | 〔0920-am-Su2-A-02-Quintessent p4、p9、p11–p14〕 |
| NTT | 薄膜InP集成LD+EAM+SOA | 16通道DML阵列：0.33–0.65 pJ/bit、约1.6 Tbps/mm、56 GBaud PAM4 2 km；4×400G/448G薄膜EML（OFC 2026 PDP Th4A.1，55 °C）：3 dB带宽>100 GHz，激光能耗0.12 pJ/bit；成熟度Level 3–5，无代工；功率预算：集成方案0 dBm输出（SOA+8.0 dB）vs ELS+分路（ELSFP +15.5 dBm，分路-9.0 dB） | 实验 | 〔0920-am-Su2-A-04-NTT p5、p7、p10、p11、p14〕 |

### 2.7 光纤/连接器/封装/测试与良率
| 机构 | 议题 | 关键数据（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Corning | CPO/NPO光纤 | 单组件>1000光纤、亚微米公差；光纤到PIC耦合1–2 dB；当前~1 Tbps/mm(DR)、12–32光纤/连接器；下一代>2 Tbps/mm、>32光纤/连接器；102.4T CPO预组装光纤托盘1,024 SMF+128 PMF（OCR） | 自报/OCR | 〔0921-MF-am-T07-1200-Corning p4–p7〕 |
| Advantest | HVM测试 | 光探针无标准、连接器处理全手工；光探针卡路线2024无源PoC→2025无源+HVM自动化→2026光栅耦合器有源对准（Technoprobe）；边耦合有源对准为WIP；注入振动后连接器插损由约2.0–2.5 dB升至约2.5–3.2 dB | 自报 | 〔0922-PF-0935-Advantest p3、p5、p8〕 |
| Arista | CPO弱点 | 目前“尚未做好大批量生产准备”；不可返修、测试流程仍在开发；只支持单一光接口，故障需系统级更换 | 自报（观点） | 〔0921-MF-pm-1300-Arista p27〕 |

### 2.8 Scale-up OCS
| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Cignal AI | OCS应用/市场 | Scale-Out(TPU)当前最大（几乎全为Google）；Scale-Up(GPU)是下一个杀手级应用，与CPO绑定；scale-up radix可小至64×64/72×72；硅光OCS评为scale-up“Ideal”；Google spine替换：功耗-40%、成本-30%、吞吐+30%；已部署256×256；OCS市场今年>\$2 B、2030>\$8 B | 分析师/引Google | 〔0921-MF-am-T02-1020-CignalAI p5、p8、p12、p16〕 |
| iPronics | ONE-32硅光OCS（含SOA增益） | 32端口严格无阻塞、>4,000开关单元、路径损耗约10 dB（增益设10 dB）；与Lumentum 1.6T 2×DR4（200G/lane）联测：VOA1 0–3 dB、VOA2 0–10 dB，BER较1e-12基线仅劣化约1个数量级（“industry-first”）；系统30 W+0.78 W/激活通道 vs 电交换机64×1600G约3500 W；<\$100/端口；响应表述不一致（p14“微秒级”、p16“皮秒级”、p11“切换300 ps”） | 自报/实验 | 〔0920-am-Su2-I-03-iPronics p11–p14、p16〕；〔0921-Mo3-A1-iPronics p1、p14〕；〔0924-推定F4-iPronics p21〕 |
| KDDI Research | LPO+OCS验证 | 96×96 MEMS OCS+TH5 EPS+2节点×2 H100；LPO端到端时延增加：203.9→290.48 ns、192.93→238.45 ns；800G 2×DR链路建立均值约6.2 ms（DSP）vs约5.2 ms（LPO）（读图）；JCT差数十秒；72小时LLM预训练稳定；GPU计算阶段零流量窗口100–400 ms，周期切换稳定、随机切换易中断作业 | 实验 | 〔0921-Mo3-A3-KDDIResearch p5、p8、p10、p12–p14〕 |
| OneTouch | 薄膜钽酸锂8×8 EO OCS | 切换<4 ns（实际响应<<1 ns）；12个开关合计静态功耗<200 nW，128×128外推7.5 μW vs热光9.0 W；平均光纤到光纤IL 8.6 dB（6–8 dB为边缘耦合）、串扰平均−24.3 dB；1小时无反馈漂移-0.33 dB（10 dBm）；阻塞Banyan拓扑 | 实验 | 〔0922-Tu1-E4-OneTouch p10、p11、p14、p16〕 |
| 浙江大学 | 硅光MEMS 2.5D Torus | 128端口插损约15 dB vs Crossbar约33 dB（读图估计）；16×16原型352开关单元，消光比>27.8 dB，实测片上IL 3.3–9.3 dB（部分路径） | 实验/读图 | 〔0922-Tu1-E2-浙江大学 p16、p18、p19〕 |
| Salience Labs | Scale-up OCS（负载静态交换） | 单级EPS事务时间1,000 ns、两级1,600 ns（400G、10 kB、300 ns pin-to-pin）；512 XPU all-reduce：OCS比EPS完成时间快约58–61%（方向按图理解）；all-to-all Bruck全消息尺寸OCS低于EPS；全OCS架构“Needs NPO/CPO”，带光链路scale-up交换机需到2027 | 仿真/自报 | 〔0922-PF-1155-SalienceLabs p6、p7、p10、p13〕 |
| Oriole | PRISM纯光无分层 | 32,000 GPU参考架构：交换机2,560→0，收发器196,608→32,768，网络功耗-81%；推理吞吐/训练利用率（Active 99% vs 40%）、能耗（Compute 80%+Network 20%→48%+5%）均为公司宣称，无第三方验证 | 自报 | 〔0920-pm-Su3-A-04-Oriole p9、p10、p12〕 |
| NVIDIA | OCS落地障碍 | 插损（≥4个bulkhead连接器，DR4余量3 dB/FR4 4 dB）、成本（>256双工端口/1RU）、可靠性（故障半径、FIT）、端口密度（千级端口） | 自报 | 〔0920-am-Su2-I-01-NVIDIA p18〕 |

### 2.9 晶圆级/3D光I/O（WSE、光中介层、scale-in）
| 机构 | 方案 | 关键指标（条件） | 口径 | 索引 |
|---|---|---|---|---|
| Cerebras | 异质混合键合的晶圆级光系统（CS-6，Hot Chips'26发布） | 三层堆叠：光晶圆/WSE/DRAM；晶圆表面E/O，低损耗波导把信号从晶圆中心送到边缘；五个设计维度：带宽密度、激光器（集成或外置）、SerDes、热兼容、可测试性与良率（“足够好晶圆”策略）；无具体带宽/功耗数值 | 自报（定性） | 〔0921-Mo4-待定-Cerebras p9、p11、p14〕 |
| Lightmatter | Passage M1000 3D光子中介层 | 114 Tbps（Tx+Rx）、1024 SerDes、4,000 mm²、256光纤、光电路交换冗余；训练万亿参数MoE相对时间：铜基线1.00×→光子等带宽0.60×→光子加带宽0.37×；预填充TTFT加速2×–3×；解码2×（均为仿真） | 仿真/自报 | 〔0924-推定F2-Lightmatter p2–p4、p9〕 |
| Lightmatter | 3D堆叠论点 | 单通道>112G后能耗/距离/时延三者变差；56G NRZ约2 pJ/bit；“Fast×few has no roadmap past 400G” | 自报 | 〔0920-pm-Su4-I-06-LightMatter p3、p6、p15〕 |
| imec | 3D集成光学（scale-in） | 300 mm晶圆级SiN波导<0.15 dB/cm（首个reticle-stitched）；D2W倏逝耦合<0.3 dB；叠对<2 µm；目标<1 pJ/bit；GeSi EAM 212.5 GBaud PAM4；BTO调制器（实验室）损耗<5 dB/cm、Pockels系数≈300 pm/V | 实验 | 〔0921-Mo12-A4-IMEC p11、p14、p15、p17〕 |

> 注：WSE方向仅Cerebras一讲且无定量数据；M1000数字均为仿真。

---

## 3. 厂商与客户态势

### 3.1 AIDC/云客户与运营商
- **OpenAI**：铜今天仍够用；选型“铜→快窄可插拔→慢宽（需可靠性证明）”；OCI-DWDM“有前景但需故障与恢复分析”〔0920-pm-Su4-I-02-OpenAI p8、p13〕；以请求延迟与每请求能耗比较互连〔0920-pm-Su3-A-02-OpenAI p10〕。
- **Oracle OCI**：800G LPO现网约35万链路；1.6T以LRO为佳；“现在应开始试用CPO”，但CPO系统FIT预期更高、方案专有；NPO/OpenCPX可缓解〔0920-pm-Su3-A-03-Oracle p7、p9–p13〕；EBO MSA主席方〔0922-MF-am-1220-EBOMSA p17〕。
- **Meta**：SerDes主导功耗，OCI约5×/端口〔0920-am-Su1-B-01-Meta p1〕；CPO>1M h无link flap数据经Broadcom/OIF转引〔0923-MF-00-上午连拍 p46〕。
- **Microsoft**：OCI Wave 1用于scale-up、Wave 2拓展内存解耦〔0921-Mo4-待定-MicrosoftAzure p1〕；同时探索microLED宽慢（自评风险很高）〔0922-Tu1-E3-Microsoft p20〕。
- **美团/中国电信/阿里腾讯**：美团认为NPO为长期路径、224G务实窗口〔0923-MF-美团-市场聚焦 p13〕；中国电信推进AIDC三域协同〔0920-am-Su1-C-00 p33〕；NPO 32/36 lane来自Huawei/Alibaba/Tencent〔0921-MF-am-T04-1100-华为 p6〕。

### 3.2 设备商
- **Arista**：XPO（12.8T液冷）替代8个OSFP，2027Q1量产；对CPO持谨慎立场〔0921-MF-pm-1300-Arista p27、p28〕。
- **Huawei**：NPO派，Hi-ONE 7.2T“已量产”（自报），Atlas 950用VCSEL LPO〔0921-Mo12-00 p100〕。
- **Ciena / Cisco-Acacia**：Ciena为Open CPX创始成员（Vesta 200 6.4T，TDECQ 2.23 dB）〔0921-Mo12-A3-Ciena p24〕、12.8T Coherent-Lite XPO〔0920-pm-Su3+Su4-A-00 p95〕；Acacia给出0–2/2–5/5–10年路线〔0920-pm-Su4-A-03-Acacia p9〕。
- **OCS阵营**：iPronics、Salience、Oriole、Cignal AI（分析）见2.8。

### 3.3 模块/器件商
- **Coherent**：2D VCSEL NPO 1.2 pJ/bit、6.4T硅光NPO、3.2T OSFP、XPO 12.8T/25.6T〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p50–p54〕。
- **Lumentum**：1060 nm VCSEL“wide&slow for scale-up”〔We5-I Lumentum p12〕；**TeraHop**：>25 M硅光收发器、Diablo-1 NPO〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p59–p61〕。
- **Ligent/NewPhotonics/Berxel/Credo/Xscape/Photon Bridge/Quintessent/Solinide/Corning/Samtec/Advantest/ST**：见2.1–2.7各表。

### 3.4 芯片商
- **NVIDIA**：CPO量产（COUPE、微环），scale-up四选一中DWDM NRZ SiPh占优；OSFP+TRO仍是Spectrum-X主力〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p44、p45〕。
- **Broadcom**：TH6 102.4T CPO；OCI-MSA创始成员；ICA/NPO-HDI通道〔0920-am-Su1-B-04-Broadcom p5、p13〕。
- **Marvell**：可插拔“连接引擎”+scale-up NPO；Photonic Fabric（Si-Ge EAM）；等离子体调制器比SiPh相位调制器小约500×〔0921-PF-待定-Marvell p6〕〔0920-pm-Su4-H-04-Marvell p8、p14〕。
- **Qualcomm/AMD/Lightmatter/Credo/Cerebras**：Qualcomm P-CPO与光D2D（<2.5 pJ/bit路径）〔0920-pm-Su3-I-04-Qualcomm p6、p7〕；AMD视CPO为scale-up必需（~5 pJ/bit）〔0920-am-Su1-A-04-AMD p4〕；其余见2.5、2.9。

## 4. 学术关键突破（按影响力排序）

| # | 机构 | 论文号/文件 | 突破点 | 数字（条件） | 标注 | 索引 |
|---|---|---|---|---|---|---|
| 1 | imec | ECOC 2026（Shahin et al.） | 首个100 GHz低电压Ge/Si APD用于400G/lane传输 | GeSi FK EAM→Ge APD；425 Gbps眼图；425G(6.25% FEC)与448G(12% FEC)两点BER约3e-3与1e-2（读图）；Ge APD BW ~90 GHz、R=1.9 A/W | “World’s first”（自报） | 〔0921-Mo12-A4-IMEC p8、p12〕 |
| 2 | NTT | OFC 2026 PDP Th4A.1；ECOC Tu3-D1/D4 | 4×400G/448G薄膜EML阵列（O波段，55 °C） | EAM 100 µm；3 dB带宽>100 GHz；驱动0.5–1.0 V；面积密度1.6 Tbps/mm²、岸线3.2 Tbps/mm、激光能耗0.12 pJ/bit；Tu3-D1 400G PAM4差分1.0 V | PDP（自报） | 〔0920-am-Su2-A-04-NTT p10、p11、p15〕 |
| 3 | Coherent | We5-I Paper #504 | 2.3 Tbit/s背发射1060 nm VCSEL阵列（硅中介层，CPO） | 16通道：32G @6 mA无DSP；128G @12 mA；六边形37发射器106G TDECQ 2.52 dB；9 Tbit/s/mm²（展望） | 论文（无首次声明） | 〔We5-I Coherent p9–p12〕 |
| 4 | Chalmers/Solinide | OFC Th2A.13 2026 | O波段光子分子微梳 | 75 mW泵浦、200 GHz、28线>1 mW、效率69%；1450–1675 nm晶圆9283谐振、效率集中~50–60%（读图） | 自报 | 〔0920-am-Su2-A-05-Chalmers p7、p9〕 |
| 5 | Columbia | CLEO 2026 Highlight Talk（Cullen et al.） | 高功率灵活FSR Kerr梳 | 375 mW泵浦：300 GHz转换63.6%、200 GHz 48.1%、100 GHz 33.6%；眼图32/24/16 Gb/s | Highlight | 〔0920-am-Su1-A-05-Columbia p8〕 |
| 6 | UC Davis | JLT 2023；JSTQE 2026 | 首个3D混合键合EIC-PIC收发器 | 496 fJ/bit，18 Gb/s，12 nm FinFET EIC；接收灵敏度-19 dBm（OMA，估计）；3D键合带来6.1 dB光功率降低 | “first”；nanoPD “record”（0.08 fF、0.72 nA、QE 91%，GF45SPCLO） | 〔0920-am-Su2-I-02-UCDavis p12–p14〕 |
| 7 | OneTouch/InnovSemi | Tu1-E4 | 首个薄膜钽酸锂电光8×8 OCS | <4 ns切换；12开关<200 nW；IL 8.6 dB；1小时漂移-0.33 dB | “first”，“三个数量级快于现有OCS” | 〔0922-Tu1-E4-OneTouch p10、p11、p14〕 |
| 8 | Arista+TerraHop | We5-B3 | 首个12.8T 8×DR8液冷可插拔XPO（64×212G PAM4） | 64路TX满足IEEE P802.3dj/df；RX灵敏度约-7至-7.5 dBm OMA @2.4×10⁻⁴ | “Industry’s first” | 〔0923-We5-B-Arista p1、p6、p7〕 |
| 9 | iPronics（含Lumentum收发器） | 0921-Mo3-A1 / F4 | 增益控制硅光OCS上1.6T收发器链路 | ONE-32，增益10 dB；BER相对1e-12仅劣化1个数量级 | “Industry-first” | 〔0921-Mo3-A1-iPronics p14〕；〔0924-推定F4-iPronics p21〕 |
| 10 | KDDI Research | Mo3-A3 | 首次LPO+OCS全栈验证与72小时LLM预训练 | 96×96 MEMS，2×H100；Pre-FEC BER约1e-8无量级差；JCT无显著影响 | “首次”（自报） | 〔0921-Mo3-A3-KDDIResearch p14〕 |
| 11 | NVIDIA | Tu1-E5（Rekhi） | 时钟前传微环DWDM的静态/动态环分配（SRA/DRA） | 0.8 Tb/s/mm、1.33 Tb/s/mm²、2.78 pJ/b；DRA旋转期间前传时钟切换零误码 | 无record声明 | 〔0922-Tu1-E5-NVIDIA p4、p12〕 |
| 12 | Quintessent | 0920-am-Su2-A-02 | 单腔单偏置8λ QD梳+booster SOA | >80 mW（波导内）→200 mW（>25 mW/λ，2 dB均匀度）；WPE>20% | “no InP”（自报） | 〔0920-am-Su2-A-02-Quintessent p9、p11、p12〕 |
| 13 | Lightmatter | 0920-pm-Su4-I-06 | 首个16λ双向CPO链路（EVK50） | 800 Gbps/纤，1 km SMF，<3 pJ/bit，pre-FEC BER<1E-9 | “THE FIRST 16λ BIDIRECTIONAL CPO LINK”（自报） | 〔0920-pm-Su4-I-06-LightMatter p10〕 |

---

## 5. 分歧、争议与反常识

**5.1 CPO vs NPO：谁是224G的“正解”**
- NPO方：Huawei五回合自评NPO 4:1，理由为可插拔生态兼容、维护解耦、上市快，CPO非可插拔、返厂周期长〔0921-Mo12-A5-华为 p4、p8〕；Ligent称NPO“不是桥梁而是持久架构”〔0921-MF-pm-1440-LIGENT p3〕；NewPhotonics称“NPO is an equilibrium”〔0922-PF-1405-NewPhotonics p1〕；Oracle称NPO多厂生态、RMA轻〔0920-pm-Su3-A-03-Oracle p11〕；fibeReality称CPO良率问题“已成现实”、热问题更严重〔0922-MF-am-1040-fibeReality p7〕。
- CPO方：NVIDIA称CPO已full production，5×功耗、10×MTBI（自报）〔0920-pm-Su3-A-05-NVIDIA p9、p10〕；Broadcom称10×可靠性并有>1M device hours 0 link flap〔0922-MF-pm-1400-Broadcom p2、p4〕；Ciena称CPO在scale-out约2026、scale-up 2027/28〔0920-pm-Su3-I-05-Ciena p10〕。
- 关键不对称：CPO的可靠性倍数基准对象在NVIDIA页面未标明〔0920-pm-Su3-A-05-NVIDIA p9〕；Oracle引Meta称CPO系统FIT预期高于可插拔〔0920-pm-Su3-A-03-Oracle p9〕；证据均为自报，缺跨厂商同条件对比。

**5.2 宽而慢 vs 快而窄：谁能规模化**
- 宽慢方：Lightmatter称“Fast×few no roadmap past 400G；slow×many已演示1.6T”〔0920-pm-Su4-I-06-LightMatter p6〕；Lumentum/Coherent/Berxel以VCSEL 1–1.5 pJ/bit与冗余降FIT为证〔We5-I Lumentum p13〕〔We5-I 博升 p9〕；Microsoft目标<1 pJ/bit、<<1 FIT〔0922-Tu1-E3-Microsoft p15〕。
- 快窄方：Ciena Riaz称宽度带来封装面积、连接器、复杂度，“难以回退”，动量仍在通道速率，448G以上快窄仍是最短路径〔0920-pm-Su3-I-05-Ciena p10〕；OpenAI要求慢宽/快宽“需现场验证”〔0920-pm-Su4-I-02-OpenAI p11〕。
- 共识：VCSEL宽并行近期需reverse gearbox（增约4 pJ/bit）〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p63〕。

**5.3 pJ/bit数字的“口径战争”**
- 同为宽慢：Coherent 1.2 pJ/bit、Aperion 1.5、Corning转引Broadcom 1.5（对SiPh 5–9）〔0921-Mo3-待定-Corning p5〕，vs TeraHop横比图uVCSEL约5.75 pJ/b、uLED约6.0〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p63〕。差异来自是否含SerDes、reverse gearbox、远端激光、clocking：Coherent核算表中0.369 pJ/b梳状SiPh为建模且排除clocking（另需+0.3–0.6）〔0920-pm-Su4-I-04-Coherent p5、p6〕。
- 反常识：106G DSP SerDes 4 nm与3 nm均3.4 pJ/bit，无改善〔0920-pm-Su4-I-07-Credo p6〕；400G SerDes功耗趋势“走错方向”〔0920-am-Su1-B-01-Meta p1〕：工艺升级不再自动降功耗。

**5.4 铜：还能走多远**
- 乐观：Ciena混合介质将铜域扩到256 XPU@25 Tbps，铜至少用到400G世代〔0921-Mo12-A3-Ciena p18、p33〕；fibeReality称Nvidia“与铜热恋”，NPC数据表可能好于NPO〔0922-MF-am-1040-fibeReality p12〕。
- 悲观：OpenAI 200G约1 m、400G约1 m且“未来越来越难”（SI、更强FEC延迟、有源件降可靠性）〔0920-am-Su1-B-02-OpenAI p4〕；Qualcomm称L-CPO在448G可能“effectively prohibitive”〔0920-pm-Su3-I-04-Qualcomm p5〕。
- 第三条路：介质波导/RF（10 m量级）：AttoTude、Arista列入五种竞争技术；分析师称“距离在10 m以上有争议，7 m本身就可能很有价值”〔0922-MF-am-1040-fibeReality p10〕。

**5.5 microLED的命运**
- 支持：Microsoft以microLED+PD阵列为宽慢主线（自评风险很高）〔0922-Tu1-E3-Microsoft p20〕。
- 反对：Lumentum称uLED不满足50 m且需外延转移〔主分析师笔记02 Lumentum p12〕；分析师称Credo因可靠性取消μLED项目（传闻）〔0922-MF-am-1040-fibeReality p9〕；Ciena Riaz问“OCI若胜出，VCSEL与uLED能否建立生态或规模竞争”〔0920-pm-Su3-I-05-Ciena p4〕。

**5.6 OCS进scale-up：乐观场景与工程约束**
- 乐观：Cignal AI认为scale-up是下一个杀手级应用，radix仅需64/72〔0921-MF-am-T02-1020-CignalAI p12〕；Salience称OCS更低时延（两级EPS 1,600 ns）转化为更好\$/token〔0922-PF-1155-SalienceLabs p16〕；iPronics称成本降2×〔0921-Mo3-A1-iPronics p15〕。
- 约束：NVIDIA四道障碍（插损、成本、可靠性、端口密度）〔0920-am-Su2-I-01-NVIDIA p18〕；Oriole指出瓶颈是收发器重锁定〔0920-pm-Su3-A-04-Oriole p9〕；KDDI指出流量峰值切换直接中断训练〔0921-Mo3-A3-KDDIResearch p13、p14〕。
- 路线分歧：Columbia称>1600 GBps注入带宽下无需快速交换（one-shot重构即可）〔0924-推定F3-哥伦比亚大学 p14〕，与Oriole“超快重锁定”诉求路线不同。

---

## 6. 判断与观察点

### 6.1 技术成熟度判断（相对scale-up 224G/lane世代）
| 技术 | 成熟度判断 | 依据 |
|---|---|---|
| VCSEL LPO（850 nm，可插拔/超节点） | 规模部署 | Atlas 950 4096× 800G SR8 LPO〔0920-am-Su1-A-03-华为 p3〕；Oracle 800G LPO 35万链路〔0920-pm-Su3-A-03-Oracle p7〕 |
| 1.6T LRO/FRO可插拔 | 现网量产（POR） | Marvell“10s millions”800G/1.6T〔0921-PF-待定-Marvell p6〕；Oracle 1.6T LRO三厂互通〔0920-pm-Su3-A-03-Oracle p8〕 |
| CPO（微环+COUPE，scale-out） | 量产（自报） | NVIDIA full production；Broadcom TH6 102.4T（2026） |
| NPO 6.4T/7.2T（ELSFP/内置激光） | 样品—早期量产 | Huawei“已量产”（自报）；Coherent/TeraHop 6.4T展示；Marvell“Just starting now”〔0921-PF-待定-Marvell p6〕 |
| XPO 12.8T | 样机→2027Q1量产 | Arista 64通道实测；量产预计2027Q1〔0921-Mo4-待定-Arista p24〕 |
| 1060 nm VCSEL CPO/宽慢阵列 | 器件级已验证，系统级待验证 | Lumentum 5000 h、倒装阵列早期失效仍在开发〔We5-I Lumentum p15〕；量产就绪1H CY27（Coherent） |
| scale-up OCS | 部署在scale-out(TPU)，scale-up待落地 | Cignal；NVIDIA四障碍；仿真/小系统验证 |
| 晶圆级光I/O（WSE等） | 概念/早期 | Cerebras定性；imec 3D平台化（iSiPP400G即将推出）〔0921-Mo12-A4-IMEC p21〕 |

### 6.2 时间窗口
- **2026**：800G LPO/1.6T LRO/FRO规模部署；Broadcom TH6 CPO与NVIDIA CPO在scale-out量产；Open CPX 1.0发布（9月）；Xscape FALCONX 8原型送样（Q2）。
- **2027**：XPO量产（Q1）；Open CPX ramp、6.4T模块标准化（Ciena）；Photon Bridge高功率DWDM光源送样（Q1）〔0920-am-Su2-A-03-PhotonBridge p10〕；Coherent VCSEL量产就绪（1H）；ST硅光产能4×；Xscape量产爬坡（Q4）；scale-up交换机带光链路（Salience）；OCI 400G（Microsoft，带问号）。
- **2027/28**：scale-up CPO（Ciena）；Broadcom第4代CPO（2028）。
- **2029–2031**：scale-up OCS“upside”从2029起（LightCounting情景）；CPO/NPO端口约2031年超过收发器（Coherent引LightCounting）〔主分析师笔记03 Coherent p5〕；2030年OCS>\$8 B。

### 6.3 对各类厂商的含义
- **设备商**：XPO提供“CPO级密度而不放弃可插拔性”的第三条路，机架级4×–8×密度；NPO/CPO要求交换机厂承担ELS、液冷、光纤管理与测试；OCS需要NCCL/SDN控制器支持（iPronics称开发中）〔0920-am-Su2-I-03-iPronics p3〕。
- **模块/器件商**：价值从“模块组装”向“光引擎+连接器+可测试性+遥测”迁移；对准与测试责任向OSAT/晶圆级转移，但“模块不会消失”〔0920-pm-Su3-A-01-LightCounting p12〕；VCSEL/GaAs 6英寸产线（Lumentum、Coherent、Berxel）与InP EML/ELS双线并行；连接器/光纤（Corning、EBO）成为CPO/NPO放量的瓶颈资产。
- **芯片商**：电通道/SerDes是能效主导项（Meta、Credo）；Broadcom/NVIDIA以自研CPO绑定交换ASIC；Marvell/Credo/Semtech以NPO/线性方案切入；Lightmatter/Qualcomm/Cerebras以3D光I/O与晶圆级为远期赌注。

### 6.4 未来12–24个月要盯的指标
1. **CPO/NPO现网FIT与link flap**：Broadcom“>1M device hours 0 flap”的对象/条件披露；NPO 6.4T ILS的实测FIT（TeraHop估计<10 FIT）；OCP’26 Credo ZeroFlap完整数据。
2. **连接器污染/首过良率**：EBO MSA 128f规范进度、每纤首次配接失效率是否达7e-5量级；CPO FAU现场返修率。
3. **XPO 2027Q1量产**：400G/lane（25.6T）电接口与PAM6（179.2 GBd）实测；模块功耗从约10 pJ/bit（LRO）向6 pJ/bit（LPO）的下探。
4. **VCSEL倒装阵列**：Lumentum底发射早期失效DPPM（目前116–231 DPPM，装配损伤）是否降到<50 dppm；1060 nm阵列>3.2 Tbps/mm²的封装级实测。
5. **pJ/bit统一核算**：OCI-MSA/OIF是否发布统一功耗测量边界；宽慢系统级（含reverse gearbox）实测。
6. **OCI-MSA Gen2 400G**（Microsoft时间线2027(?)）与Linear 400G“MAYBE”的落地情况〔0922-MF-pm-1400-Broadcom p19〕。
7. **OCS**：scale-up OCS端到端插损（DR4余量3 dB下的实际路径）、端口密度（>256双工端口/1RU）、收发器重锁定时间；GPU scale-up OCS首个客户披露。

---

## 7. 推荐配图（17条）
1. 0920-am-Su1-A-05-Columbia p9 — 窄而快 vs 宽而慢（梳驱动DWDM）的带宽密度×能效对比，梳驱动约100×领先 — 支撑判断5、光源路线。
2. 0920-am-Su1-A-03-华为 p3 — Atlas 900→950两代VCSEL光互连及规模（384→1024 NPU） — 支撑判断1、判断5（VCSEL LPO已规模部署）。
3. 0920-pm-Su3-A-03-Oracle p7 — 800G LPO vs FRO约35万链路pre-FEC BER与down-transition — 支撑判断1、3（现网数据）。
4. 0920-am-Su2-I-01-NVIDIA p11 — FRO/TRO/LPO/LPO+CPC/CPO的pJ/b与1.6T功耗表 — 支撑判断2。
5. 0920-am-Su2-I-01-NVIDIA p18 — OCS落地四大障碍 — 支撑判断5、5.6。
6. 0921-Mo12-A3-Ciena p18 — 混合铜扩展72→256 XPU — 支撑判断4、5.4。
7. 0921-Mo12-A5-华为 p9 — Hi-ONE 7.2T对1.6T模块带宽/可靠性/时延/功耗柱图（需高清复核） — 支撑判断1、5.1。
8. 0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p63 — 各架构pJ/b功耗堆叠对比（CPO+ELS/NPO+ILS/XPO LPO/宽慢） — 支撑判断2、5.3。
9. 0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p38 — 连接器污染失效模式与4096 SPOF — 支撑判断3。
10. We5-I Lumentum p13 — 1060 nm vs 850 nm VCSEL磨损对比曲线 — 支撑判断5、5.2。
11. 0920-pm-Su4-I-04-Coherent p5 — 能耗核算边界对照表（实测/投影/建模） — 支撑判断2、5.3。
12. 0921-Mo4-待定-NVIDIA p8 — Scale-up CPO四方案（PAM4 SiPh/DWDM NRZ/VCSEL/μLED）对比表 — 支撑5.2、判断5。
13. 0921-Mo4-待定-Cerebras p11 — 含光晶圆的三层晶圆堆叠与E/O逃逸 — 支撑晶圆级议题（2.9）。
14. 0921-Mo12-A4-IMEC p12 — GeSi EAM→Ge APD 400G/lane链路、眼图与BER — 支撑第4节#1、448G路径。
15. 0920-pm-Su3-A-04-Oriole p9 — 交换时间+收发器重锁定对吞吐的条形对比 — 支撑判断5、5.6。
16. 0922-PF-1155-SalienceLabs p10 — 512 XPU all-reduce OCS vs EPS完成时间 — 支撑5.6。
17. 0920-pm-Su4-I-06-LightMatter p6 — 400G/800G/1.6T单纤窄快 vs 宽慢方案对比 — 支撑5.2。
