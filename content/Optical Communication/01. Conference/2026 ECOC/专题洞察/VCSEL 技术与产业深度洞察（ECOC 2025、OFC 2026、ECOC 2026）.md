---
title: "VCSEL 技术与产业深度洞察（ECOC 2025、OFC 2026、ECOC 2026）"
tags:
  - VCSEL
  - ECOC2026
  - OFC2026
  - ECOC2025
  - Scale-up
  - 专题洞察
date: 2026-10-08
---

> [!info] 资料范围与口径
> - **ECOC 2026 现场讲稿**：We5-I VCSEL 专场 5 篇（Coherent、Lumentum、东京科学大学、博升 Berxel、坦佩雷 ORC）；We5-B 的 NVIDIA VCSEL 综述（Daniel Kuchta，31 页）；另有约 15 篇讲稿提到 VCSEL（华为、Corning、Coherent、Lumentum、Qualcomm、Credo、Ciena、Marvell、Arista、Microsoft、Broadcom、fibeReality 等）。引用格式〔E26 讲稿 pN〕。
> - **论文**：ECOC 2025 与 OFC 2026 全文中以 VCSEL 为主题的论文 23 篇（另有 29 篇只是顺带提及）。引用格式〔E25/O26 论文号〕。
> - **口径**：VCSEL 的能效数字口径差别极大，有“仅 VCSEL 芯片”“发射端（含驱动）”“光引擎（含 TIA/PD）”“整链路含主机 SerDes”几种，本文逐条标注，**不要跨口径横比**。Coherent 在 ECOC 2026 上专门提醒了这一点〔E26 Coherent Su4-I-04 p5–p6〕。

## 执行摘要

1. **VCSEL 的主战场从 scale-out 多模可插拔，转向 scale-up 的 NPO/CPO**：
   - 2026 年 VCSEL 已在超节点里规模部署。华为 Atlas 950 用 4,096 个 800G SR8 VCSEL LPO 连接 1,024 颗 NPU〔E26 华为 Su1-A-03 p3〕。
   - 2D VCSEL 阵列 NPO 成为 Coherent、Lumentum、Broadcom、博升的共同产品方向：Coherent 1.2 pJ/bit、2027 年上半年量产就绪；Broadcom 3.2T NPO 5.3 W（1.5 pJ/bit）〔E26 连拍 p50–p51〕〔E26 Corning Mo3-I p5〕。
2. **1060 nm 正在取代 850 nm，成为下一代互连 VCSEL 的主波长**：
   - 原因有三：GaAs 衬底对 1060 nm 透明，可以背发射加衬底透镜、倒装到硅中介层；可靠性更好；光纤损耗和色散更低。
   - Lumentum 的磨损测试：1060 nm 器件在结温 181 °C 下 5,000 h 无失效，850 nm 器件 >1,600 h 就出现灾难性失效〔E26 Lumentum We5-I p13〕。
   - Coherent、Lumentum、博升、东京科学大学、Fujitsu、Adtran 都押 1060 nm。
3. **单通道速率仍在刷新，但工程主流是“快而宽”或“慢而宽”的阵列**：
   - 实验室记录：1060 nm 单管 62 GHz、256 Gb/s PAM4（背靠背，无 BER）〔E26 东工大 We5-I p10–p12〕；850 nm 商用 200G VCSEL 带宽 35–45 GHz〔E26 NVIDIA We5-B p11〕。
   - 产品主流：106G PAM4 × 16–32 通道的 NPO（博升 1.6 Tbps、Aperion 3.2T），以及 32–64G NRZ × 数百通道的“慢而宽”阵列（Lumentum 256 × 64G = 8 Tb/s）。
4. **能效优势是 VCSEL 最硬的牌**：
   - 光引擎级 0.9–1.5 pJ/bit（Coherent 1.2、Broadcom 1.5、Aperion 1.5、ISSCC 2026 VCSEL 0.90）。
   - 对比硅光微环 3.0–4.5、硅光 MZM 6.25 pJ/bit〔E26 东工大 We5-I p7〕。
   - VCSEL 芯片本身只有约 50–100 fJ/bit〔E26 博升 p9〕〔E25 W.01.02.1〕。
   - 但到系统级（含主机 SerDes 和反向齿轮箱），uVCSEL 约 5.75 pJ/b，与其他方案差距收窄（读图）〔E26 连拍 p63〕。
5. **三大瓶颈**：
   - 距离：多模 50–100 m，单模 VCSEL 可到 2 km，但无法进入 scale-out 主干。
   - 连接与光纤：每个阵列需要成百上千条光纤通道，需要多芯光纤、光纤束和新型缩径多模光纤。
   - 200G 以上速率的物理极限与温度稳定性：计算托盘温度变化快，要保持带宽、功率、模式和波长稳定〔E26 Coherent Su4-I-04 p7〕。
6. **产业格局**：
   - 美国：Broadcom、Coherent、Lumentum 三强。
   - 中国：博升（Berxel）、华为（自研 850/940 nm）。
   - 日本：Sony、FujiFilm、Fujitsu。
   - 新进入者：ams OSRAM（薄膜 VCSEL）、Eliyan（2D µVCSEL）、Aperion、LightXcelerate、PicoJool。
   - 3D 传感已经出货超过 20 亿颗 VCSEL，这条供应链是 VCSEL 相对 microLED 和硅光的规模优势〔E26 Lumentum Su4-I-03 p12〕。
7. **总体判断**：VCSEL 是 2026–2028 年 scale-up 光学化里**落地最快、能效最好**的方案，在 1–50 m、机柜到排级的 NPO 市场会先拿到份额。长期看要面对两个挑战：DWDM 硅光 OCI 在带宽密度与 OCS 兼容性上占优；microLED 在通道成本上更低。**建议投资研究**：1060 nm 背发射阵列、多芯光纤与光纤束连接器、VCSEL 直驱 CMOS 驱动与 TIA 阵列。

---

## 一、技术路线全景

### 1.1 波长演进

| 波长 | 起点 | 主要用途 | 现状 |
|---|---|---|---|
| 850 nm | 1999 年标准化 | 多模数通（SR4/SR8），100G PAM4 已商用 | 200G 已有多家样品；高温可靠性差，色散限制距离 |
| 940 nm | 2017 年 3D 传感（Face ID），数十亿颗出货 | 3D 传感、光无线 | 华为、博升用于高速数通（200G PAM4 150 m OM5）〔E25 W.02.01.112〕 |
| 980 nm | 2021 年汽车（高温高可靠） | 汽车 | PicoJool 980 nm 37 GHz〔E26 NVIDIA p11〕 |
| 1060 nm | 2025 年提出用于高密度互连 | scale-up NPO/CPO | 本轮主线；IEEE P802.3ds 为 1060 nm 扩展距离 |
| 1310/1550 nm（InP 长波长） | — | 单模长距 | 带宽通常仅约 10 GHz；Yale 新型 InP SWIR VCSEL 9 GHz、峰值 PCE 约 30%〔O26 W4E.4〕；NTT 硅上薄膜面发射激光器 25 GHz、100G PAM4 × 2 km〔O26 W4E.5〕 |

来源：Lumentum〔E26 Su4-I-03 p13〕。

### 1.2 器件结构的三个方向

1. **背发射 + 倒装 + 集成透镜**（最重要的工程进展）：
   - 光从 GaAs 衬底背面出射，可在衬底上直接做透镜或超透镜，芯片倒装焊在硅中介层或驱动芯片上。
   - 收益：热阻降低约 40%（Lumentum），结温比 850 nm 顶发射低约 40 °C（博升）；阵列节距从 >150 µm 降到 30–50 µm；可寻址通道数从约 10 个增到 100–1,000 个〔E26 博升 p10〕。
   - 超透镜（HCG 高对比度光栅）：发散角降到 <6°，与普通 OM4 光纤直接对接，耦合效率约 70%〔E25 W.02.01.24〕；3 dB 径向容差 ±22 µm、纵向容差 400 µm〔E26 博升 p12〕。
2. **单模 / 耦合腔提带宽**：
   - 东京科学大学（Koyama 组）的金属孔径耦合腔 1060 nm 单模 VCSEL：-3 dBo 带宽 >62 GHz，256 Gb/s PAM4，芯片直流功耗 <50 fJ/bit〔E26 东工大〕。
   - 单模 VCSEL 配合 SMF 跳线做中心注入，可在 500 m OM4 上消除模间色散〔O26 W4E.3〕。
3. **薄膜 / 小孔径低电流**：
   - ams OSRAM 850 nm 薄膜 VCSEL（硅通孔）：25 µm 节距，32 Gb/s NRZ，7.8 mW，约 0.25 pJ/b（仅 VCSEL）〔E26 NVIDIA p22〕。
   - Coherent 低电流阵列：0.5 mA 驱动下约 15 GHz，投影整链路 0.75 pJ/b〔E26 Coherent Su4-I-04 p3〕。

### 1.3 两种阵列哲学

| 路线 | 代表 | 单通道 | 通道数 | 取舍 |
|---|---|---|---|---|
| 快而宽（Fast & Wide） | 博升、Aperion、Broadcom、华为 | 100–200G PAM4 | 8–32 | 兼容现有 200G PAM4 主机 SerDes，无需齿轮箱；需 DSP 均衡 |
| 慢而宽（Slow & Wide） | Lumentum、Eliyan、Coherent µVCSEL、NVIDIA 研究概念 | 25–64G NRZ | 64–数百 | 无 DSP、无 FEC、低时延、可冗余；需要反向齿轮箱或原生宽接口 |

博升的观点是 VCSEL 走“快而宽”，与 microLED 的“慢而宽”（304 通道 × 3.3 Gb/s）区分开〔E26 博升 p5–p8〕。Lumentum 则认为首个实现会用 NRZ，因为宽并行不需要很高的单通道带宽〔E26 Lumentum We5-I p5〕。

---

## 二、ECOC 2026 现场讲稿：核心观点逐篇

### 2.1 We5-I VCSEL 专场（2026-09-23）

| 讲稿 | 题目 | 关键数据 | 核心观点 |
|---|---|---|---|
| **Coherent**（M. Ganzhorn） | 2.3 Tbit/s 背发射 1060 nm VCSEL 阵列，硅中介层 CPO | 16 通道（2×8）阵列，32G（6 mA，无 DSP）到 128G（7 抽头 Tx/Rx）；单管 125 °C 下 32G 无 DSP；37 发射器六边形阵列，节距 70 µm，106G TDECQ 2.52 dB；单发射器可到 100G，等效带宽密度 >9 Tbit/s/mm²（展望）；RIN 25 °C 约 -154、125 °C 约 -146 dB/Hz | 铜终将被光取代；之后可以“慢而宽”，追求效率、可靠性、冗余和密度；VCSEL 各速率下效率高、成熟、耦合简单〔p4–p12〕 |
| **Lumentum**（Matt Peters） | 1060 nm VCSEL 阵列用于 AI 数据中心 scale-up 的性能、可靠性与可制造性 | 第一代 64G NRZ × 256 通道 = 8 Tb/s，2.0 mm 岸线，2.5 pJ/bit；倒装热阻 -40%；S21：25 °C 33.8 GHz、85 °C 25.3 GHz；50G NRZ 在 1060 nm 优化光纤上传 150 m；32G NRZ 105 °C；**磨损**：1060 nm 86 个单元、Tj 181 °C、5,000 h 无失效，850 nm >1,600 h 灾难失效；**早期失效**：顶发射 72K 发射器 28 DPPM，底发射 8.6K 发射器 231 DPPM（均为装配损伤），目标 <50 DPPM | 首个实现用 NRZ；相对 InP/TFLN/硅光在密度、无外置激光、可靠性（冗余做到 <1 FIT）上占优；依托 6 英寸 GaAs 与 3D 传感供应链，无需老化筛选〔p4–p18〕 |
| **东京科学大学**（Ibrahim、Koyama 等） | 62 GHz 1060 nm 金属孔径 VCSEL 实现 256G PAM4 与无模色散 SMF/MMF 链路 | -3 dBo 带宽 >62 GHz（6 mA）；BTB 150G NRZ、256G PAM4（TDECQ 4.97 dB）；1 km SMF 200G PAM4；500 m OM4 用 SMF 模式滤波 200G PAM4；芯片直流功耗 <50 fJ/bit | 同一 1060 nm 平台同时服务 SMF 1 km 与 MMF 500 m；路线图：400G/lane、带宽 >70 GHz、8/16/32 通道、EIC <1 pJ/bit〔p6–p16〕 |
| **博升 Berxel**（Huawen Hu、Connie Chang-Hasnain 等） | 1060 nm 背发射 VCSEL 106G PAM4 传 100 m OM3，用于 NPO | 光引擎约 1 pJ/bit（VCSEL 本身 50–100 fJ/bit）；单 VCSEL <0.03 FIT（累计 250 亿器件小时无失效），阵列 <0.1 FIT；1.6 Tbps 16 通道共封装发射端；1060 nm 背发射带宽 >44 GHz、RIN 约 -150 dB/Hz；212G PAM4 传 30 m OM2 / 50 m OM5；140 °C 25G NRZ 无误码 | scale-out 用 NPO、scale-up 用 CPO，VCSEL 阵列是“快而宽”；超透镜极大放宽对准，简化封装〔p4–p19〕 |
| **坦佩雷 ORC** | 低阈值单频腔内接触 VCSEL，用于低温计算 | 4 K 下阈值 120–150 µA，斜率效率最高约 0.6 W/A；尚无速度数据 | 量子计算低温互连的光源候选，需要“室温失谐”设计〔p5–p18〕 |

### 2.2 NVIDIA 综述（We5-B，Daniel Kuchta）

> 讲者声明：这是综述，不代表 NVIDIA 产品计划。

- **核心观点**：VCSEL 持续进步，多家已演示全链路 ≤1 pJ/bit，“其他技术难以超越”；VCSEL 型 NPO 正获关注；慢而宽用 NRZ 换低时延和低 BER；与多芯光纤和光纤束兼容〔p1–p30〕。
- **商用 200G VCSEL 对比表**〔p11〕：

| 波长 | 厂商 | 室温带宽 | 距离 |
|---|---|---|---|
| 850 nm | Broadcom | 44 GHz | 50 m OM4+ |
| 850 nm | Coherent | 45 GHz | 80 m OM4 |
| 850 nm | Sony | >40 GHz | 100 m OM4 |
| 850 nm | 华为 | 35 GHz | 60 m OM4 |
| 850 nm | Berxel | 41 GHz | BTB |
| 1060 nm | FujiFilm | 35 GHz | — |
| 1060 nm | Berxel | >44 GHz | 30 m OM2 / 50 m OM5 |
| 980 nm | PicoJool | 37 GHz | — |

- **速率记录**：东京科学大学 256G PAM4、275G PAM6（BTB，无 BER）；华为 850 nm 240G PAM6 BTB（225G 净），212G PAM6 传 60 m OM4（200G 净，201 抽头 Volterra + MLSE）；PAM8 288 Gb/s 传 100 m OM4（20% SD-FEC 后 240G 净）〔p6–p8〕。
- **NPO/CPO 产品与项目**：
  - IBM MOTION（ARPA-E）：第一阶段 16 × 56G NRZ、4 pJ/bit、0.25 美元/Gb；第二阶段 32 × 112G PAM4、玻璃载板，首批全功能件 2026 年第四季度〔p14〕。
  - Aperion 3.2T 多模 VCSEL NPO：1.5 pJ/bit，<0.1 FIT，约 60 Tb/s XPU 逃逸带宽〔p16〕。
  - 未具名厂商 32 × 128G NPO：1.4 pJ/bit〔p17〕。
  - Eliyan 2D µVCSEL 慢而宽：4 × 56G/106G NRZ 替代单路 224G PAM，约 10 Tbps/mm〔p21〕。
  - ams OSRAM 薄膜 VCSEL：约 0.25 pJ/b（仅 VCSEL），150 °C 2,000 h 无失效〔p22〕。
  - LightXcelerate：19 芯多芯光纤，每芯一颗 1060 nm VCSEL，每根光纤 1 Tb/s〔p23〕。
  - NVIDIA 研究概念：50G NRZ/光纤、约 3.0 pJ/bit（建模）、10 m，每 GPU 57.6 Tb/s 收发，CMOS 光背板 + 带透镜 VCSEL/PD〔p26〕。
- **新光纤提案**：约 26/80 µm（芯径/包层）多模光纤，1060 nm 下有效模式带宽约 5 GHz。理由是 50/125 µm 芯径对 200G PD（≤20 µm）过大，80 µm 包层更耐弯〔p19〕。

### 2.3 其他讲稿中的 VCSEL

| 讲稿 | 观点与数据 |
|---|---|
| 华为（Su1-A-03） | Atlas 900（2025）：6,912 个 400G SR8 VCSEL oDSP；Atlas 950（2026）：4,096 个 800G SR8 VCSEL LPO，时延降 90%、功耗降 60%（基线未明示）；光链路由 UB 链路级重传 + 2×2 模块交叉备份保护；3.2T VCSEL NPO 演示 4 × (8 × 100G)，50 m OM4，13.7 W，约 4.3 pJ/bit〔p3–p4〕 |
| Lumentum（Su4-I-03） | 立场：scale-out 用快窄（InP），scale-up/scale-in 用慢宽（VCSEL）；VCSEL 可 >4 Tbps/mm，<2 pJ/bit，个位数 FIT，标准多模光纤可做 >500 GPU 的 radix；3D 传感 VCSEL 已出货 20 亿颗；与 Qualcomm Dragonfly（UCIe 光 D2D PHY）和 Corning 合作，10 Tbps VCSEL+PD 光引擎，>1 Tbps/mm，ECOC 现场演示〔p12–p17〕 |
| Coherent（Su4-I-04） | 能耗口径对照表：108G VCSEL 阵列 0.90 pJ/b（光引擎，实测）、NRZ 慢宽 VCSEL 0.75（整链路，投影）、Broadcom 100G VCSEL 1 pJ/b（驱动+VCSEL+TIA+PD，实测）；超过 200G/lane 后 VCSEL 逼近物理极限〔p3–p7〕 |
| Coherent（市场聚焦连拍 p50–p51） | 2D VCSEL 阵列单发射器 25–200 Gb/s；世界最大的数通 VCSEL 供应商，阵列量产 >10 年；NPO 2D VCSEL 1.2 pJ/bit、12 Gb/s/mm²（含激光器、驱动、PD、TIA），“业界首个”；量产就绪 2027 年上半年 |
| Corning（Mo3-I） | 光纤束连接器：可直接插接 VCSEL NPO，连接器数量减 4 倍；引 Broadcom 100G VCSEL 3.2T NPO 5.3 W（1.5 pJ/bit）、<0.1 FIT、18 个 NPO 支撑 58T 逃逸带宽〔p2–p8〕 |
| Credo（Su4-I-07） | 宽并行光 mesh：E/O（VCSEL）约 0.5 pJ/bit，整次光穿越约 4 pJ/bit，比交换式铜低 3–4 倍；可达 50+ m〔p6〕 |
| fibeReality（MF-am-1040） | Credo 因可靠性问题取消 µLED 项目、转向 µVCSEL；Google 似乎更倾向 µVCSEL〔p9〕 |
| Ciena（Su3-I-05） | 机内互连：MMF/VCSEL 最长 50 m、最高 100G（已可用）；“慢会迫使押注单一技术”：OCI 若胜出，VCSEL 与 µLED 能否建立生态？〔p4, p7〕 |
| Marvell（Su3-I-07） | scale-in 下一代选项：uVCSEL I/O chiplet 与 uLED I/O chiplet〔p4〕 |
| Arista（XPO，MF-0923） | 12.8T XPO 中 VCSEL-IGB（反向齿轮箱）20–30 m、65 W、约 5 pJ/bit；慢宽 VCSEL 用 8:1 反向齿轮箱产生 8 × 50G NRZ〔p19, p29〕 |
| 连拍 p63（多架构功耗堆叠） | uVCSEL 约 5.75 pJ/b，与 Open CPX NPO（约 5.75）、uLED（约 6.0）、CPO+ELS（约 6.6）接近（读图估计） |
| Microsoft Azure（Mo4） | OCI Wave 2（内存解耦）中，VCSEL 等技术成为选项〔p1〕 |
| NVIDIA（Mo4） | scale-up CPO 四候选中，VCSEL 与 µLED 在功耗、芯片成本、时延上占优，DWDM NRZ 硅光在岸线密度、带宽可扩展、OCS 兼容上占优〔p8〕 |
| Oracle（Su1-A-02） | VCSEL/DML 可靠性差是被误读的“激光器 FIT 最高”，CW 激光器本身是低 FIT 器件〔p8–p10〕 |
| KDDI（Tu1-C5） | 光无线光源对比：VCSEL 阵列约 10° × 10°、>100 mW 但合束质量差；PCSEL 发散角 <0.2°、>1 W〔p10–p12〕 |

---

## 三、论文清单（ECOC 2025 与 OFC 2026）

### 3.1 数据中心互连（主线）

| 论文 | 机构 | 内容 | 关键数据 |
|---|---|---|---|
| E25 W.01.02.4 | 阿里云 + 合作方 | 850 nm 单模 VCSEL 400G QSFP112 模块，500 m 标准 OM4 | 106 Gb/s × 4，比 400GBASE-SR4 的 100 m 长 5 倍，后 FEC 无误码（纪录） |
| E25 W.01.02.1 | 东京科学大学 | 1060 nm 单模耦合腔 VCSEL | 带宽 >45 GHz，200G PAM4，**90 fJ/bit**（纪录），30 m OM4 |
| O26 W4E.3 | 东京科学大学 | 1060 nm 单模耦合腔 VCSEL + SMF 中心注入 | 500 m OM4 上 200G PAM4，100 Gb/s·km（纪录），无模色散 |
| E25 Tu.01.03.2 | 东京科学大学 + Ambition Photonics | 1060 nm 16 通道顶发射阵列直接耦合单模多芯光纤 | 180G PAM4/通道，合计 2.88 Tb/s，500 m 多芯光纤，单芯片 13.6 Tbps/mm² |
| E25 Tu.01.03.1 | Fujitsu Optical Components 等 | 1060 nm 单模 VCSEL 阵列 + 多芯光纤 CPO 收发器，50 GBd × 16 | 2 km 多芯光纤，106G PAM4 下 **3.95 pJ/bit**（含收发的 CPO 最低纪录），尺寸 7.7 × 15.9 × 7.95 mm |
| O26 W1B.4 | Fujitsu Optical Components 等 | 1060 nm 单模 VCSEL 8 通道 CPO 收发器，53 GBd | 2 km SMF 并行链路，4.5 pJ/bit，1.22 cm²，双微透镜阵列耦合损耗 <2 dB，标准 24 芯 MT 插芯 |
| E25 W.01.03.3 | 根特大学 imec | 28 nm CMOS 直驱 1060 nm 单模 VCSEL 发射器 | 60 GBd NRZ 传 5 km SMF，发射器 **0.94 pJ/b**，283 Gb/s·km（纪录） |
| E25 W.02.01.130 | 博升 + 合作方 | 850 nm VCSEL，带宽 >40 GHz，集成驱动 | 200G PAM4 BTB，225G PAM8 传 100 m MMF |
| E25 W.02.01.112 | 华为 | 940 nm 多模 VCSEL | 200G PAM4 传 150 m OM5（首次），绕开 850 nm 色散限制 |
| O26 Th4A.3 | **Sony** | 850 nm 氧化限制 VCSEL | 25–80 °C 带宽 >35 GHz，RIN <-150 dB/Hz，70 °C/8 mA 寿命 >10 年，200G PAM4 |
| O26 Th1A.2 | 庆应大学 | 渐变折射率塑料光纤（低材料色散） | 212.5G PAM4 传 50 m，突破多模光纤色散限制 |
| O26 W1B.5 | 博升 + 合作方 | 940 nm 倒装背发射 VCSEL + 超透镜，面向 NPO/CPO | 106G PAM4 @100 °C，30 m OM2；结温比 850 nm 顶发射低约 40 K；25G 到 140 °C 无误码；16 通道 NPO 模块全通道开眼 |
| E25 W.02.01.24 | 博升 + 合作方 | 940 nm 背发射 VCSEL + HCG 超透镜 | 发散角 <6°，OM4 对接耦合约 70%，无需拾放光学 |
| O26 Th1G.4 | LightXcelerate | 19 芯多芯光纤耦合的背发射 VCSEL/背照 PD 阵列 CPO chiplet | 倒装到驱动/TIA 芯片，面向多 chiplet GPU 光互连 |
| E25 W.02.01.118 | 都灵理工 + 合作方 | DMT 与 PAM4 在 VCSEL-多模链路上的对比 | 90 m OM3 上只有 DMT 能 >100 Gb/s 净速率（111.1 Gb/s） |
| O26 Th3A.5 | 深圳团队 | 28 nm CMOS 单片 APD 接收前端，面向 VCSEL 链路 | 28G PAM4，0.66 pJ/bit |
| O26 Th3C.3 | 法国 ESIEE + 合作方 | 聚合物垂直锥形波导，多模光纤到小孔径高速 PD | 耦合效率 >95%，±25 µm 容差 |

### 3.2 新型面发射光源

| 论文 | 机构 | 内容 |
|---|---|---|
| O26 W4E.4 | Yale + 合作方 | 可量产 InP SWIR VCSEL（O/C 波段），峰值 PCE 约 30%，带宽 9 GHz |
| O26 W4E.5 | NTT | 硅上 O 波段薄膜分布反射面发射激光器，带宽 25 GHz，100G PAM4 传 2 km SSMF |

### 3.3 低温 / 量子互连

| 论文 | 机构 | 内容 |
|---|---|---|
| O26 Th1A.3 | UIUC（Milton Feng） | 低温 VCSEL，4.5 µm 孔径，2 mA 下带宽 >50 GHz，3 K 下 180G PAM4（纪录），目标 <50 fJ/bit |
| O26 Th1A.4 | 台大 + UIUC | 850 nm 低温 VCSEL，3 K 下 91 mW（纪录），3–40 K 内 140G PAM4 |

### 3.4 光无线（LiFi / OWC）

| 论文 | 机构 | 内容 |
|---|---|---|
| O26 M3H.2 | 爱丁堡 LiFi 中心 + VI Systems | 940 nm 单模多孔径 VCSEL，>80 Gb/s（83.3），1 m，<5 mW |
| E25 W.04.08.5 | Fraunhofer HHI + VI Systems | 多孔径 VCSEL，5 m 下 67.8 Gb/s（LDPC 后） |
| E25 Tu.01.09.2 | 埃因霍温 | 2×2 VCSEL 焦平面阵列波束扫描，4 × 10 Gb/s |
| E25 W.02.01.166 | 爱丁堡 + 合作方 | 1310 nm VCSEL + 螺旋相位板 OAM 复用，75 Gb/s，1 m |
| O26 Tu2H.5 | Fraunhofer HHI | 9 个 VCSEL 阵列 + 12×12 成像 APD 接收，角度分集 4.4 Gb/s |
| O26 Th1G.5 | 爱丁堡 | VCSEL–PIN 透明以太网光无线，1 Gb/s，<25 ns 时延 |

---

## 四、产业地图

| 类别 | 公司 | 公开进展（来源） |
|---|---|---|
| VCSEL 芯片（美国） | Broadcom | 850 nm 200G VCSEL 44 GHz；100G VCSEL 3.2T NPO 5.3 W、1.5 pJ/bit、<0.1 FIT〔E26 NVIDIA p11〕〔E26 Corning p5〕 |
| | Coherent（II-VI） | 自称世界最大数通 VCSEL 供应商；850 nm 200G 45 GHz；1060 nm 背发射阵列 2.3 Tb/s；2D VCSEL NPO 1.2 pJ/bit，量产就绪 2027H1〔E26 We5-I〕〔E26 连拍 p50–p51〕 |
| | Lumentum | 1060 nm 阵列 8 Tb/s、2.5 pJ/bit；磨损与早期失效数据；6 英寸 GaAs；与 Qualcomm、Corning 联合演示〔E26 We5-I〕〔E26 Su4-I-03〕 |
| VCSEL 芯片（中国） | 博升 Berxel | 850/940/1060 nm 全覆盖；背发射 + 超透镜；1.6 Tbps 共封装发射端；<0.03 FIT〔E26 We5-I〕〔O26 W1B.5〕〔E25 W.02.01.24/130〕 |
| | 华为 | 自研 850/940 nm 高速 VCSEL；Atlas 950 大规模部署 800G VCSEL LPO；3.2T VCSEL NPO 演示〔E26 Su1-A-03〕〔E25 W.02.01.112〕 |
| VCSEL 芯片（日本） | Sony | 850 nm 200G VCSEL >35 GHz、>10 年寿命〔O26 Th4A.3〕 |
| | FujiFilm | 1060 nm 35 GHz〔E26 NVIDIA p11〕 |
| | Fujitsu Optical Components | 1060 nm 单模 VCSEL + 多芯光纤 CPO 收发器，3.95–4.5 pJ/bit〔E25 Tu.01.03.1〕〔O26 W1B.4〕 |
| | Ambition Photonics | 东京科学大学产业化伙伴〔E25 Tu.01.03.2〕 |
| VCSEL 芯片（欧洲/其他） | ams OSRAM | 850 nm 薄膜 VCSEL，25 µm 节距〔E26 NVIDIA p22〕 |
| | VI Systems | 多孔径 VCSEL（光无线）〔E25 W.04.08.5〕 |
| | PicoJool | 980 nm 37 GHz〔E26 NVIDIA p11〕 |
| NPO/CPO 模块与系统 | Aperion | 3.2T 多模 VCSEL NPO，1.5 pJ/bit |
| | Eliyan | 2D µVCSEL 慢而宽，约 10 Tbps/mm |
| | LightXcelerate | 19 芯多芯光纤 VCSEL/PD chiplet〔O26 Th1G.4〕 |
| | IBM | MOTION 项目，玻璃载板 32 × 112G PAM4 |
| | Credo | 宽并行光缆（传闻转向 µVCSEL）〔E26 fibeReality p9〕 |
| | Adtran | 1060 nm 单模 VCSEL 发射阵列，<1 W，2 km SMF-28〔E26 NVIDIA〕 |
| 客户与架构方 | 华为、阿里云、NVIDIA、Microsoft、Google、Qualcomm | 华为已部署；阿里云 500 m SR4；NVIDIA 研究概念；Microsoft OCI Wave 2 选项；Google 据称倾向 µVCSEL；Qualcomm Dragonfly 光 D2D |
| 光纤与连接 | Corning、Lightera（OFS）、庆应大学 | 光纤束连接器（连接器减 4 倍）；1060 nm 优化多模光纤；26/80 µm 新多模光纤提案；渐变折射率塑料光纤 |
| 研究机构 | 东京科学大学（Koyama）、UC Berkeley 系（Chang-Hasnain，博升）、UIUC（Milton Feng）、根特 imec、坦佩雷 ORC、Yale、NTT | 速率纪录、低温、InP 长波长 |

---

## 五、核心观点与分歧

### 5.1 共识

1. **能效最好**：在光引擎边界，VCSEL 是所有方案里最低的（0.9–1.5 pJ/bit），因为直调、无外置激光、无调制器、阈值低。
2. **可靠性靠冗余**：单器件 FIT 低（博升 <0.03、Lumentum 目标 <50 DPPM），阵列再用备份通道降到 <0.1 FIT。华为在现网用了链路重传加模块交叉备份。
3. **1060 nm + 背发射 + 倒装**是下一代互连 VCSEL 的标准形态。
4. **多芯光纤与光纤束是必需的配套**：没有高密度光纤，就发挥不出阵列的带宽密度。

### 5.2 分歧

| 议题 | 正方 | 反方 / 保留 |
|---|---|---|
| VCSEL 能否进入 scale-up 主流 | Coherent、Lumentum、博升、Broadcom、Corning、NVIDIA 综述：≤1 pJ/bit，“难以超越” | NVIDIA（Mo4）：DWDM NRZ 硅光在岸线密度、带宽扩展、OCS 兼容上更优；Ciena：“慢”迫使押注单一技术 |
| 快而宽还是慢而宽 | 博升：快而宽（100–200G PAM4 × 16–32），无需齿轮箱 | Lumentum、Eliyan：慢而宽 NRZ，免 DSP；但 Arista 指出反向齿轮箱约 5 pJ/bit，吃掉收益 |
| 200G 以上能走多远 | 东京科学大学：62 GHz、256G，目标 400G/lane | Coherent：200G/lane 已逼近器件物理极限，需要新器件与集成方式 |
| 850 nm 还是 1060 nm | 850 nm：现有多模生态、Sony/Broadcom 200G 产品 | 1060 nm：可靠性、背发射、距离全面占优（Lumentum 磨损数据） |
| VCSEL 还是 microLED | VCSEL：单通道速率高 10–50 倍、距离 50 m+、有 3D 传感供应链；Credo 据称从 µLED 转向 µVCSEL | microLED：通道成本更低，冗余更便宜（见 MicroLED 洞察） |
| 距离 | 单模 VCSEL 可做 2 km（Fujitsu、根特）；阿里云 500 m 多模 | 多数 VCSEL 方案仍停在 30–100 m，scale-out 主干仍是单模硅光/EML |

---

## 六、判断与建议

1. **2026–2028 年 VCSEL 在 scale-up NPO 里会最先量产**：华为已部署 VCSEL LPO 超节点，Coherent 2027 年上半年量产就绪，Broadcom、Aperion 已有 3.2T NPO 方案。**重点关注**：首个采用 VCSEL NPO 的 GPU/XPU 超节点产品，以及 NVIDIA 在 VCSEL 与 DWDM 硅光之间的最终选择。
2. **1060 nm 背发射阵列是最值得投入的器件方向**：可靠性、热和封装同时改善，并能复用 6 英寸 GaAs 与 3D 传感产线。**投资研究**：1060 nm 外延与倒装产能（Coherent、Lumentum、博升）、晶圆级超透镜（HCG）、晶圆级测试。
3. **配套是瓶颈也是机会**：多芯光纤、光纤束连接器、26/80 µm 新多模光纤、VCSEL 直驱 CMOS 驱动与 TIA 阵列（0.66–0.94 pJ/bit 级 CMOS 结果已出现）。**投资研究**。
4. **单通道 400G VCSEL 是研究看点而非产业主线**：目前的 256G 纪录只是背靠背、无 BER 的结果，工程上更可能停在 100–200G 并靠通道数扩展。**跟踪**。
5. **中国厂商的位置**：
   - 博升在背发射、超透镜、高温和 1060 nm 上与美国三强处于同一梯队。
   - 华为既做芯片又是最大的现网用户，是 VCSEL scale-up 最完整的落地样本。
   - 阿里云在多模距离上做出了 500 m 纪录。
   - **重点关注**：国产 1060 nm 阵列的量产与可靠性数据。
6. **要盯的量化指标**：
   - 1060 nm 阵列早期失效能否从 231 DPPM 降到 <50 DPPM（Lumentum 年底数据）。
   - 系统级（含主机 SerDes）能效能否低于 3 pJ/bit。
   - 200G/lane VCSEL 在 70–85 °C 下的量产良率。
   - 多芯光纤连接器的标准化进度（EBO、SDM4 MCF MSA）。
