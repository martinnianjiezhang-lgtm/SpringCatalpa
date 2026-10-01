---
title: "MicroLED 短距光互连深度洞察"
tags:
  - ECOC2026
  - OFC2026
  - ECOC2025
  - MicroLED
  - 专题洞察
date: 2026-10-01
---

> [!info] 资料范围与口径
> - **本地资料**：ECOC 2026 现场讲稿笔记（〔ECOC 文件名简写 pN〕）、OFC 2026 论文（〔OFC 论文号〕）、ECOC 2025 论文（〔E25 论文号〕）。三次会议里与 microLED 直接相关的内容共约 20 处，正文逐条标注。
> - **网络资料**：MicroLED Connect 2026（9 月 16–17 日，埃因霍温，首次设 Optical I/O 专场）、Microsoft MOSAIC 论文（SIGCOMM 2025 最佳论文）及各厂商公告，编号 [W1]…，链接见文末。
> - **口径**：“自报”指厂商或讲者自述；“推算”是本文按公开物理参数做的数量级估算，不是厂商数据。不同口径（发射端 fJ/bit、整链路 pJ/bit、单端模块功耗）不放在一起横比。

## 执行摘要

1. **为什么是现在**：AI 集群的瓶颈从计算转到互连，而 scale-up 需要“比铜远、比激光省电、比激光可靠”的链路。显示产业在 microLED 上积累的 GaN 外延、巨量阵列、玻璃面板与纳米压印工艺，正好对得上“宽而慢”（大量低速并行通道）这个架构。Google 的 Bernard Kress 在 MicroLED Connect 2026 上直接建议 microLED 厂商“把光 I/O 当作主要收入来源”，因为 AR 短期仍是小市场 [W2]。
2. **最清楚的机会在 1–10 m（机柜内 scale-up）和芯片封装内（scale-in）**，其次是 10–50 m 的有源光缆。对应 Microsoft MOSAIC：800G 单端功耗从 9.8–12 W 降到 3.1–5.3 W（-56% 到 -68%），实测 2 Gbps/通道、20 m 内满足 FEC 门限 [W4]。30 m 以上要付出明显的通道速率代价。
3. **决定成败的不是 LED 本身，而是四件事**：
   - 端到端光耦合效率（朗伯发射 + 光学扩展量）。
   - 色散限制的“速率 × 距离”积。
   - 主机电接口的“反向齿轮箱”。
   - 阵列级测试与连接器生态。
   显示产业最擅长的“巨量转移”在互连里反而用不上：互连用的是 microLED 与 CMOS 驱动芯片的晶圆级混合键合。
4. **系统层面的能效优势没有器件层面看起来那么大**：ECOC 2026 上一张多架构功耗对比把 uLED 方案估在约 6.0 pJ/b，与 uVCSEL（约 5.75）和 CPO+外置光源（约 6.6）相当（读图估计）〔ECOC 0923-MF-00 连拍 p63〕。microLED 真正的差异化在**无激光、可冗余、无 DSP/FEC 时延**，而不只是 pJ/bit。
5. **学术界明显落后于产业**：OFC 2026 与 ECOC 2025 共 1,249 篇论文中，只有 3 篇与 microLED/LED 光互连直接相关，且都是复旦大学的可见光通信方向（单器件速率、OFDM 调制）。ECOC 2026 只有 Microsoft 一个邀请报告专讲 microLED。主战场在产业会议、初创公司与显示面板厂。
6. **时间表**：Microsoft 目标 2027 年底商用 [W4]；AUO 称 2–3 年内推出 CPO 方案 [W17]；TrendForce 预计 2028 年下半年开始出货，2030 年 microLED CPO 光模块营收约 8.5 亿美元 [W15]；CEA-Leti 联合项目瞄准 2030 年部署 [W8]。
7. **总体判断**：microLED 光互连是 2026 年光互连领域最值得**投资研究**的新变量之一，但 2026–2027 年仍处在“样机 + 评估套件”阶段。建议重点盯三条线：
   - AOC 形态的首批量产（Microsoft/MediaTek、Credo）。
   - 晶圆级 GaN-on-Si 与 CMOS 键合的产能与良率（Mojo Vision、ams OSRAM、Avicena）。
   - 玻璃基封装路线（AUO、Intel、Vuzix）。

---

## 一、从显示到互连：为什么在 2026 年集中外溢

### 1.1 驱动力

- **互连成为 AI 瓶颈**：Microsoft 在 MicroLED Connect 2026 上的判断是“AI 的真正瓶颈已是互连，而不是内存或计算”[W2]。在 ECOC 2026 的邀请报告里，Microsoft 给出了光 I/O 的目标：功耗 <1 pJ/bit、带宽密度 >10 Tbps/mm、距离约 10 m、可靠性 <<1 FIT、时延 <10 ns〔ECOC 0922-Tu1-E3-Microsoft p15〕。
- **显示 microLED 的商业化受阻**：AR 眼镜与大尺寸 microLED 显示放量慢。Kress 认为 AR 短期仍是小市场，microLED 厂商应先靠光 I/O 获得收入 [W2]。
- **供应链规模的错配**：Insight Media 指出，全球激光器年出货约 1–2 亿颗，而一片 microLED 晶圆就能做出同等数量的发射器。数据中心未来每年需要数十亿光源，只有 GaN 晶圆产线的规模能接得住 [W14]。

### 1.2 2025–2026 年的关键事件

| 时间 | 事件 | 来源 |
|---|---|---|
| 2025-05 | Avicena 完成 6,500 万美元 B 轮（Tiger Global 领投），累计 1.2 亿美元 | [W6] |
| 2025-08/09 | Microsoft MOSAIC 论文发表，获 SIGCOMM 2025 最佳论文 | [W4] |
| 2025 | Credo 收购 microLED 初创 Hyperlume | [W15][W16] |
| 2025-11 | CEA-Leti 宣布 microLED 数据链路多边合作项目（2026 年初启动，为期 3 年） | [W8] |
| 2026-03 | MediaTek 与 Microsoft Research 发布 microLED 有源光缆（AOC）；Marvell 宣布与 Mojo Vision 多代合作（Marvell 是其 B 轮最大投资方）；ams OSRAM 发布面向宽而慢互连的 microLED 阵列；Mojo 获 Future Ventures 1,750 万美元 | [W5][W9][W12][W10] |
| 2026-04 | 晶元光电（Ennostar）、友达（AUO）、鼎元（Tyntek）在 Touch Taiwan 联合展示 microLED CPO | [W17] |
| 2026-05 | AUO 与 Aledia（3D 纳米线 microLED）结盟，范围延伸到光 I/O | [W18] |
| 2026-06 | 思特威（SmartSens）与紫光展锐（UNISOC）合作 microLED 光 I/O | [W19] |
| 2026-08 | Avicena 开始交付 1 Tbps 评估套件；Vuzix 交付 Causeway 玻璃波导样品；AUO 在 SEMICON Taiwan 展示 microLED 光通信与玻璃芯基板 | [W6][W13][W17] |
| 2026-09 | MicroLED Connect 2026 首设 Optical I/O 专场；Teradyne 发布 microLED 阵列量产测试平台 Iris 100；Intel 与 AUO 合作玻璃基 microLED 封装；Avicena 在 ECOC 2026 演示首个可插拔连接器版本 | [W1][W20][W21][W7] |

### 1.3 用户提到的几家公司分别做了什么

- **Microsoft**：MOSAIC 架构的提出者，研究在剑桥实验室，与 MediaTek 做出 AOC 原型；ECOC 2026 邀请报告与 MicroLED Connect 2026（Paolo Costa）都在讲 [W3][W4]〔ECOC 0922-Tu1-E3-Microsoft〕。
- **Google**：公开动作是 Kress 在 MicroLED Connect 上的产业判断 [W2]。分析机构 fibeReality 在 ECOC 2026 市场聚焦里称 **Google 似乎更倾向 µVCSEL** 而非 µLED〔ECOC 0922-MF-am-1040-fibeReality p9〕。**本次检索没有找到 Google 发布 microLED 光互连产品或论文的公开资料**，这一点需要用户确认信息来源。
- **Mojo Vision**：从隐形眼镜显示转型，首个点亮 300 mm GaN-on-Si 蓝光 microLED 晶圆，主打“晶圆进、晶圆出”的平台。方案集成 300 mm CMOS、GaN-on-Si microLED、硅 PD、多芯光纤束、定制微透镜与“软件定义对准”，与 Marvell 多代合作 [W9][W10]。
- **Vuzix**：AR 衍射波导厂商，把纳米压印玻璃波导工艺移到封装内光互连。Causeway 波导桥演示配置支持最多 19,200 条并行通道、光程约 30 mm，2026 年 8 月起送样。尚无插损、串扰、pJ/bit 数据，也在评估 VCSEL 光源 [W13]。

---

## 二、技术架构：“宽而慢”的 microLED 链路由哪几块组成

一条典型的 microLED 链路由六个环节组成：
1. **GaN microLED 发射阵列**（蓝/绿光，单通道 2–4 Gbps NRZ），与 CMOS 驱动芯片晶圆级混合键合。
2. **微光学**：微透镜阵列（MLA）或全内反射（TIR）透镜，可用纳米压印量产。
3. **传输介质**：多芯成像光纤（内窥镜同款，单根数千到上万芯）、多芯光纤束，或封装内的玻璃平面波导。
4. **接收阵列**：硅 PD 阵列或类 CMOS 图像传感器阵列，可见光可直接用硅探测。
5. **模拟后端**：TIA 阵列 + 简单判决，无 DSP、无 ADC/DAC、无 CDR，可选轻量 ECC。
6. **主机侧齿轮箱**：把 200G PAM4 的 SerDes 转成数百路低速 NRZ。

与激光方案的根本区别是：用通道数换速率。MOSAIC 的计算是，一个 800G 端口用 400 条以上 2 Gbps 通道，20×20 的 microLED 阵列面积不到 1 mm² [W4][W15]。

---

## 三、应用机会：在哪些距离和形态上有胜算

| 层级 | 距离 | 现有方案 | microLED 的切入点 | 代表玩家与数据 |
|---|---|---|---|---|
| 封装内 scale-in（芯片到芯片、芯片到 HBM） | mm–cm | 硅中介层并行铜、UCIe | 光 I/O chiplet，靠阵列密度换带宽 | CEA-Leti 目标 1.3 → 10.5 Tbps/mm、<0.5 pJ/bit，接 UCIe [W8]；Vuzix 30 mm 波导 19,200 通道 [W13]；Marvell 把 uLED/uVCSEL I/O chiplet 列为 scale-in 下一代〔ECOC 0920-pm-Su3-I-07-Marvell p4〕 |
| 板级、托盘级 | <1 m | PCB 走线、flyover 铜 | 替代长电走线，减少 retimer | Avicena 定位 die-to-die、XPU-to-memory、XPU-to-switch [W7] |
| 机柜内 scale-up | 1–10 m | 无源铜 1.5 m、有源铜 3.5–5.5 m | **主战场**：比铜远、比激光省电，可做 NPO/CPO | Ciena 机内互连图把 Micro-LED 标为约 10 m、“进行中”〔ECOC 0920-pm-Su3-I-05-Ciena p7〕；AUO/Ennostar/Tyntek CPO <10 m [W17]；ams OSRAM 10 m 整链路 <2 pJ/bit [W12] |
| 机柜间、排级 | 10–50 m | VCSEL AOC、硅光可插拔 | microLED AOC | MOSAIC 目标 50 m [W4]；Credo 有源光缆 30 m，称“只是第一步”[W16] |
| >50 m | — | 单模激光 | **不适合** | Lumentum：VCSEL 与硅光能满足 50 m，uLED 不行〔ECOC 0920-pm-Su4-I-03-Lumentum p12〕 |

**新的用法**：
- **内存解耦**：Microsoft OCI Wave 2 把光互连用到内存解耦，目标时延 <5 ns、<4 pJ/bit〔ECOC MicrosoftAzure p3–p8，见全量洞察 P25〕。microLED 无 DSP/FEC 的低时延正好对上这个需求。
- **扁平化拓扑**：Credo 指出各家超大规模云都在扁平化网络（AWS ShuffleBox、Google Virgo、Microsoft Fairwater）。宽并行光互连能把 GPU 域从铜的 72 颗扩到 300 颗以上〔ECOC 0920-pm-Su4-I-07-Credo p3–p4〕。

---

## 四、核心优势（有数据支撑的部分）

1. **功耗**：
   - MOSAIC 单端分解 [W4]。主流 800G 链路：主机接口 0.2–2.4 W + 数字后端（DSP/CDR/ADC/DAC）3.5 W + 模拟前端与激光器 4.7 W + MCU/DC-DC 1.4 W = 9.8–12 W。MOSAIC：数字后端 0.4 W + 模拟前端与 microLED 1.2 W + 1.3 W + 主机接口 = 3.1–5.3 W。整根 AOC 从 24 W 降到 10.6 W。
   - 到 1.6T 代际，主流方案预计 23–25 W/端，MOSAIC 靠通道翻倍仍维持约 10.6 W [W4]。
   - Avicena 自报发射端功耗低到每比特数十 fJ（因为 LED 没有激光器的阈值电流，接收端灵敏度提高后可直接降电流）[W22]。
   - 复旦红光 microLED 在 100 µA 时直流功耗 0.22 pJ/bit〔OFC Th1G.3〕。
   - 注意口径：以上分别是整链路、发射端、直流功耗，不能直接比较。
2. **无激光、无制冷、温度稳定**：AUO/Ennostar 自报工作温度可到 125 °C [W17]；Microsoft 称比激光方案温度更稳定、对灰尘不敏感 [W3]。
3. **可靠性靠冗余而不是靠单器件**：
   - MOSAIC 为 800G 设计了 460 条以上通道，其中超过 10% 是冗余；用汉明码这类轻量 ECC 做故障屏蔽与定位，再热切换到备用通道，自报可靠性比现有光链路高 100 倍 [W4]。
   - 激光方案每加一个通道成本都很高，很难做冗余。这是 microLED 的结构性优势。
4. **低时延**：无 DSP、无 FEC。MOSAIC 指出主机侧 FEC 约 100 ns，降低单通道速率即可免 FEC [W4]。Nokia Bell Labs 在 ECOC 2026 的 PDP 报告里把 scale-up 的“慢而宽 microLED”概括为：无需激光、模拟后端判决 NRZ、无 FEC、每芯粒约 10 ns 时延、<1 pJ/bit〔ECOC 0924-PDP-A-6 p11〕。
5. **可见光可用硅探测**：可直接用廉价的硅 PD 或 CMOS 传感器工艺做接收阵列，不需要 InGaAs [W4]。
6. **制造规模**：一片晶圆的发射器数量相当于全球激光器的年出货量 [W14]。

---

## 五、关键技术维度深度分析

### 5.1 GaN 外延与器件：带宽、效率、电流密度的三角关系

- **带宽受载流子寿命限制**：LED 是自发辐射，调制带宽由载流子复合寿命（纳秒量级）决定，典型为 1–2 GHz 级。提高带宽要靠高电流密度（缩短寿命）和小尺寸（降电容），但两者都会带来新问题：
  - **效率下降（droop）**：高电流密度下外量子效率（EQE）下降。Avicena 在 MicroLED Connect 上专门讨论了“光功率有限、发射角宽、高电流密度下效率下降、强烈依赖器件几何”的链路预算约束 [W22]。
  - **侧壁复合**：尺寸缩到 10 µm 以下，刻蚀侧壁的非辐射复合会拉低效率。Insight Media 给出的产业目标是 5–10 µm 器件 EQE ≥10% [W14]。
  - Lumentum 在 ECOC 上直接点出 uLED 的可靠性问题是“为带宽而推高的电流密度”〔ECOC 0920-pm-Su4-I-03-Lumentum p12〕。
- **已报道的器件水平**：

| 来源 | 器件 | 带宽 / 速率 | 条件 |
|---|---|---|---|
| UCSB（MicroLED Connect 2026） | 蓝光 microLED | EQE 58%（纪录级）；612 MHz，约 1.24 Gb/s NRZ | 高电流密度 [W11] |
| Tera Electronics（中国台湾） | 蓝宝石衬底 microLED | 约 1.9 GHz | 与 CMOS 晶圆级集成 [W11] |
| ams OSRAM | EVIYOS 车灯阵列改造 | >1 GHz，≥3.0 Gb/s/通道，BER <1e-15 | 25,600 像素可独立寻址 [W12] |
| Avicena | GaN microLED | 单颗 16 Gbps；套件 3–3.5 Gbps/通道 | 自报 [W14][W22] |
| 复旦（OFC 2026） | InGaN 红光 microLED（转印到金刚石衬底） | 20 µm 器件 1.62 GHz（红光纪录）；1.5 Gbps @100 µA，0.22 pJ/bit | OFDM、0.04 m 自由空间〔OFC Th1G.3〕 |
| 复旦 + 南昌大学（ECOC 2025） | 305 µm 硅衬底 GaN LED（V 形坑 3D PN 结 + DBR） | 单像素 10 Gbps @0.5 m，9.23 Gbps @1.2 m；DBR 把光谱 FWHM 从 30 nm 压到 5 nm | OFDM + 分布式均衡〔E25 Tu.01.09.5〕 |

- **衬底与外延路线**：
  - **GaN-on-Si 300 mm**（Mojo Vision）：直接对上 300 mm CMOS 晶圆键合，规模经济最好 [W10]。
  - **蓝宝石**（Tera Electronics）：外延质量成熟，但与 CMOS 键合需要剥离或转移 [W11]。
  - **3D 纳米线**（Aledia）：侧壁问题小、可做高压驱动，已与 AUO 结盟 [W18]。
  - **硅衬底 GaN**（南昌大学/晶能路线）：ECOC 2025 复旦论文展示了 V 形坑把“缺陷变优势”的思路〔E25 Tu.01.09.5〕。
  - **ALLOS**（德国）：专注 GaN-on-Si 外延的量产与供应链 [W11]。
- **颜色选择**：互连主流是蓝光和绿光，带宽更高。红光 InGaN 因高铟组分带来应变与极化场，低电流下带宽更难提高〔OFC Th1G.3〕。多波长复用会遇到红光短板。

### 5.2 调制速率与“速率 × 距离”积：色散是硬约束

- **光谱宽**：microLED 光谱宽度 >10 nm，激光 <1 pm [W4]。蓝光在石英中的材料色散远大于 1310/1550 nm 窗口（photoncap 估算约 -770 ps/(nm·km)），25 nm 光谱传 50 m 会展宽约 960 ps，接近 2 Gbps 的两个比特周期 [W23]。多芯成像光纤的每个芯还有模间色散。
- **MOSAIC 实测** [W4]：
  - 2 Gbps/通道在 20 m 内满足 FEC 门限，30 m 时降到 1.6 Gbps。
  - 1.3 Gbps 及以下在 20 m 内无误码（BER <1e-12），2 Gbps 无误码只到 10 m。
  - 用 1.3 Gbps 做 800G 需要 616 条通道。
  - 仿真显示，集成透镜与定制光纤耦合器改善入射条件后，可插拔模块能做到 2 Gbps × 50 m、BER <1e-6。
- **推算的经验规律**：单通道“速率 × 距离”积约为 40–60 Gb/s·m（2 Gbps × 20–30 m）。往 4–8 Gbps/通道推进，在同样光谱宽度下距离会成比例缩短。所以：
  - 机柜内（≤10 m）可以把单通道推到 4–8 Gbps，通道数减半。
  - 30–50 m 的 AOC 只能停在约 2 Gbps，靠通道数堆带宽。
- **缓解手段**：
  - 窄化光谱：谐振腔或 DBR 结构，复旦的 DBR 把 FWHM 压到 5 nm〔E25 Tu.01.09.5〕。
  - 光纤设计：Credo 收购的 Hyperlume 专利通过调 NA（0.17–0.7）、渐变折射率芯、选材料（含氟聚合物、PMMA、石英）来控制色散，实施例在 10 m 下的色散带宽为 2.8–5 GHz [W23]。
  - 模拟均衡：MOSAIC 用模拟后端恢复 NRZ，不用 DSP [W4]。

### 5.3 高密阵列设计与晶圆级制造能力

- **阵列规模**：
  - MOSAIC 原型是 10×10 阵列，量产设计为 20×20、460 条以上通道、10 µm 器件 [W4][W15]。
  - Avicena 套件 335 通道，另一说是 400 颗阵列 × 3.5 Gbps [W7][W14]。
  - ams OSRAM 车灯阵列 25,600 像素 [W12]。
  - Vuzix 波导 19,200 通道 [W13]。
  - 产业目标：每束至少约 1,000 颗、5–10 µm 间距、一维阵列带宽密度 >25 Tbps/mm [W14]。
- **与显示的关键区别**：
  - **不需要巨量转移**。显示要把数百万颗 microLED 转移到 TFT 背板，互连则是把整块 microLED 阵列与 CMOS 驱动/接收芯片做**晶圆对晶圆或芯片对晶圆的混合键合**。MOSAIC 量产设计正是把 microLED 和 CMOS 传感器阵列垂直键合在同一颗 CMOS 芯片上，避开引线键合的间距限制 [W4]。CEA-Leti 第 1–2 年的里程碑也是“混合键合 microLED + 定制 ASIC，<1 pJ/bit”[W8]。
  - **像素可独立寻址**：MOSAIC 指出，microLED 结构与显示用的相同，只是需要逐像素独立控制 [W4]。
- **晶圆尺寸与产能**：
  - Mojo Vision 的 300 mm GaN-on-Si 与 300 mm CMOS 可以直接键合，是目前最接近半导体前道模式的路线 [W10]。
  - ams OSRAM 在马来西亚居林建有自动化 8 英寸 microLED 产线 [W24]，与 Avicena 签了量产 JDA [W24]。
  - 中国大陆的华灿（HC SemiTek）、乾照（Changelight）、三安、思坦（Saphlux）、诺视（MTC）等处于送样验证阶段 [W15]；华创芯光称 microLED 光互连将在 3–5 年内进入数据中心 [W25]。
- **驱动与接收电路**：需要高密度 TIA 阵列和二维驱动阵列，这些在现有光通信 IC 生态里是空白 [W14]。MOSAIC 指出，电后端不需要 5/7 nm 先进制程，是降成本的一大来源 [W4]。

### 5.4 良率：从“零缺陷面板”变成“已知缺陷图 + 重映射”

- **显示的良率逻辑**：显示要求像素良率接近 99.9999%，坏点肉眼可见，靠修补与冗余子像素解决，这是 microLED 显示难以放量的主因之一。
- **互连的良率逻辑不同**：
  1. 阵列规模小得多（数百到数千颗，而不是数百万）。
  2. 可以超配通道。MOSAIC 800G 设计含 10% 以上冗余，坏通道在上线时被映射掉，运行中失效靠 ECC 与热切换处理 [W4]。MOSAIC 明确指出“超配通道有助于提高整体良率、降低成本”[W4]。
  3. 新要求变成**一致性**：所有通道的带宽、光功率、阈值、老化速率都要在窗口内，否则每通道都要单独校准。这对晶圆级测试提出了新需求。
- **测试是隐藏瓶颈**：Teradyne 于 2026 年 9 月发布 Iris 100，可在量产节拍下测数百万发射器阵列的逐像素亮度、光谱与均匀性，识别坏点与簇状缺陷，支持晶圆测试与成品测试，并与 UltraFLEXplus 电测平台合并 [W20]。这说明产业已开始为 microLED 光 I/O 准备半导体级测试基础设施。
- **光纤组装良率**：宽路线的连接点更多。EBO MSA 的数据是，1,088 个连接的板级光纤组装良率只有 23%〔ECOC 0922-MF-am-1220-EBOMSA p8〕。microLED 用单根成像光纤或多芯光纤承载数百通道，能把物理连接数降一到两个数量级。这是它相对“宽并行 VCSEL + 普通光纤”的一个优势，但前提是连接器生态成熟。

### 5.5 玻璃工艺：显示面板厂的真正杠杆

“玻璃”在 microLED 光互连里有三种用法，都来自显示与 AR 产业：

1. **玻璃基封装 / 玻璃中介层**：
   - AUO 把面板厂的玻璃加工与重布线层（RDL）能力用到 CPO：玻璃 RDL 中介层降低导入门槛，并与 Corning 半导体级玻璃合作玻璃芯基板，包括玻璃通孔（TGV）成形与金属化 [W17][W26]。
   - Intel 开发了用 TGV 把 microLED 嵌入玻璃基板的技术，并与 AUO 合作，AUO 认为适合 10 m 以内的数据传输线缆 [W21]。
   - 玻璃的优势是热膨胀系数低、尺寸稳定、可以做大面积面板级加工（成本随面积摊薄），能缓解大封装的翘曲问题 [W26]。
2. **玻璃平面波导（封装内）**：Vuzix 把 AR 衍射波导的纳米压印量产工艺，用于封装内的玻璃波导桥 [W13]。
3. **纳米压印微光学**：MOSAIC 的 TIR 透镜可以用纳米压印做晶圆级、低成本量产 [W4]。

**判断**：面板厂（AUO、群创 Innolux 等）在 microLED 互连里的核心资产不是 LED 本身，而是**大面积玻璃加工 + RDL + 面板级封装**。这与 Intel 推玻璃基板、台积电推面板级 CoPoS 的方向一致。

### 5.6 端到端光耦合效率与链路预算

这是 microLED 最难的一环，也是各家公开数据最少的地方。

- **物理约束**：
  - microLED 是朗伯发射体，向整个半球发光；激光是准直光斑 [W4]。
  - 朗伯光源耦合进数值孔径为 NA 的光纤时，可接收的功率比例约为 NA²（光源小于纤芯时）。以 NA = 0.4 计约 16%（-8 dB），NA = 0.2 只有 4%（-14 dB）（推算）。
  - 光学扩展量（étendue）守恒，透镜不能无损地把大角度光压进小芯径，所以发射器越小越好，但小尺寸又会降低 EQE（见 5.1）。
- **各家的做法**：
  - MOSAIC 先用标准 MLA，发现“仍有大量光收不进来”，改用两件式 TIR 透镜，耦合效率比 MLA 高 2 倍以上，把 ±90° 发散压到约 ±12° [W4][W23]。
  - MOSAIC 用一颗 microLED 对应多根成像光纤芯，大幅放宽对准精度。但边缘芯的光约束较弱，损耗多约 1 dB，因此不用边缘芯 [W4]。
  - Mojo Vision 用定制微透镜阵列加“软件定义对准”[W9]。
  - Avicena 在 MicroLED Connect 上专讲耦合损耗与光学扩展量约束 [W11]。
- **推算的链路预算（数量级，非厂商数据）**：
  - 发射端耦合 -5 到 -8 dB（含 TIR 透镜）。
  - 成像光纤 10–50 m：可见光衰减远高于红外，加上边缘与弯曲损耗，约 -1 到 -3 dB。
  - 连接器 -1 到 -2 dB（Avicena 刚做出 MPO 形态可插拔接口 [W7]）。
  - 接收端耦合与填充因子 -1 到 -3 dB。
  - 合计约 -8 到 -16 dB。
  - 硅 PD 在 450 nm 的响应度约 0.2–0.3 A/W，低于 InGaAs PD 在 1310 nm 的约 0.9 A/W。
  - 结论：microLED 链路的余量主要靠“低速率 → 高接收灵敏度”换回来。这也解释了为什么各家都停在 2–3.5 Gbps/通道。
- **对研究和投资的含义**：耦合效率每提高 3 dB，可以直接换成更低驱动电流（更好的可靠性与能效）或更高单通道速率。**晶圆级微光学（纳米压印 TIR/超透镜）与高 NA 多芯光纤**是链路里性价比最高的改进点。

### 5.7 接收端与电接口：齿轮箱问题

- **接收阵列**：硅 PD 阵列（鼎元 Tyntek 的 Micro PD [W17]、Avicena 集成 PD 阵列 [W7]）或类 CMOS 图像传感器阵列（MOSAIC 与 CMOS 供应商定制 [W4]；思特威入局 [W19]）。图像传感器厂商入场是值得注意的信号。
- **反向齿轮箱**：主机输出 200G PAM4，要变成数百路 NRZ 就要加格式转换。
  - fibeReality 的评价是“µLED 需要出色的齿轮箱”〔ECOC 0922-MF-am-1040-fibeReality p9〕。
  - Arista 与 Applied Materials 在 ECOC 都指出，反向齿轮箱会吃掉宽而慢的节能收益〔ECOC 0920-pm-Su3-I-03-Arista p6〕〔ECOC 0920-pm-Su3-I-08-AppliedMaterials p12〕。
  - MOSAIC 的数字后端只做“简单齿轮箱 + 轻量故障保护”，约 0.4 W [W4]。
  - 长期解法是 ASIC 原生输出宽并行接口（UCIe/OCI 类）。CEA-Leti 的中期里程碑就是基于 UCIe 做到 1.3 Tbps/mm [W8]。

### 5.8 光纤与连接器

- **成像光纤**：医用内窥镜同款，单根数千到上万芯。各芯同材同长，2 Gbps 下 1 cm 长度差只带来约 50 ps（10% 比特周期）偏斜 [W4]。缺点是可见光损耗、弯曲性能，以及数据中心级的布线和端接标准都还没有。
- **多芯光纤束 + MPO**：Avicena 在 ECOC 2026 演示了首个可插拔 microLED 链路，用标准 MPO 外形、针对多芯光纤束优化的插芯 [W7]。这是从“演示”走向“可维护”的关键一步。
- **专用光纤设计**：Credo/Hyperlume 路线说明光纤本身也可以成为差异化点 [W23]。
- **分析师的顾虑**：Counterpoint 指出，专用线缆与机架改造会带来 microLED 器件之外的额外成本；Gartner 指出缺标准是导入障碍 [W3]。

### 5.9 可靠性与寿命：分歧最大的地方

- **乐观面**：AUO/Ennostar 自报 125 °C、寿命超过 3 万小时 [W17]；Microsoft 称冗余带来比现有光链路高 100 倍的可靠性 [W4]；GaN microLED 的热容忍度被认为好于 VCSEL [W14]。
- **怀疑面**：
  - 3 万小时约 3.4 年，短于数据中心设备 5–7 年的服役期（推算）。
  - Lumentum 指出 uLED 为带宽推高电流密度会带来可靠性问题，并强调 3D 传感 VCSEL 已出货 20 亿颗、供应链现成〔ECOC 0920-pm-Su4-I-03-Lumentum p12〕。
  - fibeReality 称 **Credo 因可靠性问题完全取消了 µLED 项目、转向 µVCSEL**〔ECOC 0922-MF-am-1040-fibeReality p9〕。但 Credo 在 ECOC 2026 只说“宽并行光学”的有源光缆（30 m、MTBF 1 亿小时、备用通道无缝切换），没有点明发射器类型〔ECOC 0920-pm-Su4-I-07-Credo p3〕；另有报道称其 2026 年 9 月宣布的是“有源 LED 光缆”[W23]，而 Credo 又收购了 microLED 公司 Hyperlume。**这三条信息互相矛盾，需要以 Credo 官方产品资料为准。**
  - Microsoft 在 ECOC 报告里自评风险“很高”，并称需要在生产环境规模验证〔ECOC 0922-Tu1-E3-Microsoft p19–p20〕。

---

## 六、与其他短距方案的对比

| 维度 | 铜（DAC/ACC/AEC） | 宽并行 VCSEL（850/940/1060 nm） | 硅光 DWDM 微环（OCI 类） | microLED |
|---|---|---|---|---|
| 单通道速率 | 200G PAM4 | 32–106 Gb/s（Lumentum 1060 nm 32 Gbps/通道）〔ECOC Lumentum p16〕 | 32–53 GBd NRZ | 2–3.5 Gb/s（器件可到 10–16 Gb/s） |
| 距离 | 1.5 / 3.5 / 5.5 m〔ECOC Ciena p7〕 | ≤50 m（MMF） | 500 m–2 km | 10 m 级，AOC 30–50 m |
| 能效 | 最低（但距离短） | <2.5 pJ/bit（Lumentum）；1.2 pJ/b 实测（Coherent） | NVIDIA 微环测试芯片 2.78 pJ/b | 链路 <2 pJ/bit（ams OSRAM）；发射端数十 fJ/bit |
| 光源 | — | 激光，阈值电流 | 外置激光（ELS） | 无激光 |
| 系统级功耗堆叠（同一张图读数） | — | uVCSEL 约 5.75 pJ/b | 50G NRZ 微环 + 外置光源 + 反向齿轮箱约 9.2 pJ/b | uLED 约 6.0 pJ/b〔ECOC 0923-MF-00 连拍 p63〕 |
| 成熟度 | 量产 | 3D 传感 VCSEL 已出货 20 亿颗 | OCI MSA v1.0 已发布 | 评估套件阶段 |
| 标准 | 成熟 | 部分 | OCI MSA | **无** |

NVIDIA 在 ECOC 2026 把 scale-up CPO 分为四类候选：以太网 PAM4 硅光、DWDM NRZ 硅光、宽而慢 VCSEL、µLED。VCSEL 与 µLED 在功耗、芯片成本、时延上占优，DWDM NRZ 硅光在岸线密度、光纤带宽可扩展性和 OCS 兼容性上占优〔ECOC 0921-Mo4-NVIDIA p8〕。博升（Berxel）的带宽密度路径图把 microLED 定位为 304 通道 × 3.3 Gbps 的“慢而宽”，与 VCSEL 的“快而宽”对照〔ECOC We5-I 博升 p5–p8〕。

**结论**：microLED 的直接对手不是硅光，而是**宽并行 VCSEL**。两者都无需外置激光、都靠阵列。VCSEL 赢在单通道速率、距离、现成供应链；microLED 赢在单通道成本、通道数上限、冗余和可见光硅探测器。Ciena 的问题一针见血：如果 OCI 路线胜出，VCSEL 和 uLED 能否建立生态或规模竞争？“慢”会迫使产业押注单一技术〔ECOC 0920-pm-Su3-I-05-Ciena p4〕。

---

## 七、主要玩家地图

| 环节 | 玩家 | 动作 / 数据 |
|---|---|---|
| 系统与架构定义 | Microsoft、MediaTek | MOSAIC + AOC；MediaTek 在 Computex 展示 400G/纤 CPO，路线 800G → 3.2T [W5] |
| | Marvell | 与 Mojo Vision 多代合作，最大投资方 [W9] |
| | Credo | 收购 Hyperlume；有源光缆 30 m，2027 财年送样、2028 财年量产 [W15] |
| | Intel | 玻璃基 TGV 嵌入 microLED，与 AUO 合作 [W21] |
| | Google | Kress 产业判断；分析称偏向 µVCSEL [W2]〔fibeReality p9〕 |
| microLED 发射器 | Avicena | 1 Tbps 套件、335 通道、可插拔 MPO；与 ams OSRAM 签量产 JDA [W7][W24] |
| | Mojo Vision | 300 mm GaN-on-Si 平台 [W10] |
| | ams OSRAM | EVIYOS 改造阵列，≥3 Gb/s/通道，10 m 整链路 <2 pJ/bit [W12] |
| | 晶元光电（Ennostar）、錼创（PlayNitride，与 Brillink 合作）、Aledia、ALLOS、Tera Electronics | 中国台湾、欧洲显示 microLED 厂商转向光 I/O [W15][W11] |
| | 华灿、乾照、三安、思坦、诺视、利亚德、华创芯光 | 中国大陆，送样验证阶段 [W15][W25] |
| 接收器 | 鼎元（Tyntek）、思特威（SmartSens） | Micro PD；CMOS 传感 + 紫光展锐 SerDes [W17][W19] |
| 玻璃、波导、封装 | AUO、Corning、达兴材料、Vuzix | 玻璃 RDL 中介层与玻璃芯基板；纳米压印玻璃波导 [W17][W13] |
| 测试 | Teradyne | Iris 100 [W20] |
| 研究机构 | CEA-Leti、UCSB、Tyndall、复旦大学 | 多边项目；EQE 58%；出光方向性；红光与硅衬底 LED [W8][W11]〔OFC Th1G.3〕〔E25 Tu.01.09.5〕 |

**一个结构特征**：中国台湾形成了“面板厂（AUO）+ LED 外延（Ennostar）+ PD（Tyntek）+ 材料（达兴）”的垂直整合联盟，并与 Intel、Corning、Aledia 连接 [W15]。这与硅光 CPO 由台积电 COUPE 主导的格局不同，**面板厂可能借 microLED 进入先进封装**。

---

## 八、挑战总表

| 类别 | 挑战 | 严重程度 | 说明 |
|---|---|---|---|
| 物理 | 色散限制“速率 × 距离”（约 40–60 Gb/s·m/通道） | 高 | 决定了只能在 ≤10 m 提速、30–50 m 只能堆通道 |
| 物理 | 朗伯发射与光学扩展量导致耦合效率低 | 高 | 需要晶圆级微光学 + 高 NA 光纤 |
| 器件 | 带宽、EQE、电流密度三角（效率下降、侧壁复合） | 中高 | 小尺寸高带宽与高效率难兼得 |
| 器件 | 寿命与高电流密度老化 | 高 | 自报 3 万小时，短于服役期；Credo 传闻取消 |
| 制造 | 阵列一致性与逐通道校准 | 中 | 测试平台刚出现（Teradyne Iris 100） |
| 制造 | microLED 与 CMOS 的混合键合产能 | 中 | 300 mm GaN-on-Si 仍是少数玩家 |
| 电路 | 主机侧反向齿轮箱 | 高 | 原生宽接口 ASIC 尚无时间表 |
| 生态 | 无 MSA、无连接器与成像光纤标准、无测试方法 | 高 | Gartner、Counterpoint 都点名 [W3] |
| 商业 | 产业链大客户（NVIDIA、AMD）未表态 | 中高 | Counterpoint [W3] |
| 商业 | 代际窗口：业界 2027–28 年转向 1.6T/3.2T | 中 | 靠通道数翻倍跟进，阵列和光纤要同步扩大 |

---

## 九、判断与建议

1. **技术判断**：microLED 在 **1–10 m 机柜内 scale-up 与封装内 scale-in** 有真实且独特的位置。理由是无激光、冗余便宜、无 DSP/FEC 低时延、可见光可用硅探测，而不只是 pJ/bit。在 30–50 m 的 AOC 上，它和宽并行 VCSEL 正面竞争，胜负取决于成本与寿命数据。50 m 以上不是它的战场。
2. **最可能的落地顺序**：
   - 2027–2028 年：AOC 先落地（Microsoft/MediaTek、Credo）。
   - 2028–2029 年：机柜内 NPO/CPO（AUO、MediaTek、Avicena）。
   - 2030 年前后：封装内光 I/O chiplet（CEA-Leti、Mojo、Vuzix）。
   这与 TrendForce 预计的 2028 年下半年出货基本一致 [W15]。
3. **建议分级**：
   - **投资研究**：
     - 晶圆级微光学（纳米压印 TIR/超透镜）与高 NA 多芯/成像光纤，链路里性价比最高的改进点。
     - microLED 与 CMOS 混合键合及 300 mm GaN-on-Si。
     - 玻璃基封装（TGV + RDL），面板厂进入先进封装的入口。
     - 阵列级测试与校准。
   - **重点关注**：
     - 原生宽并行电接口的 ASIC（决定齿轮箱问题何时消失）。
     - Microsoft/MediaTek AOC 在 2027 年底的商用进度。
     - Credo 的发射器路线到底是 LED 还是 VCSEL。
   - **跟踪**：
     - 红光与多波长复用、单器件 10 Gbps 以上的研究进展（复旦等）。
     - 中国大陆 LED 厂商的送样与客户验证。
     - 是否出现 microLED 光 I/O 的 MSA。
4. **要盯的量化指标**：
   - 单通道“速率 × 距离”积能否从约 50 Gb/s·m 提高到 100 Gb/s·m 以上。
   - 端到端耦合损耗能否稳定在 -10 dB 以内。
   - 高温加速老化下的寿命与 FIT 数据（目标 5 年以上服役）。
   - 每 Gbps 成本是否达到产业目标 0.01–0.02 美元 [W14]。
   - 首个 microLED 光 I/O MSA 或连接器标准的出现时间。

---

## 参考来源（网络）

- [W1] MicroLED Connect 2026 Optical I/O 专场介绍：https://www.microled-info.com/glimpse-microled-connect-2026-microleds-take-ai-data-center-interconnect ；会议总结：https://www.microled-info.com/microled-connect-2026-concludes-record-attendance-and-strong-interest-optical
- [W2] MicroLED Connect 2026 总结（Microsoft、Google Bernard Kress 观点）：https://www.microled-info.com/microled-connect-2026-concludes-record-attendance-and-strong-interest-optical
- [W3] Network World：Microsoft 无激光光缆与分析师观点：https://www.networkworld.com/article/4146960/microsofts-laser-free-cable-tech-promises-to-slash-ai-data-center-networking-power-bills.html
- [W4] MOSAIC 论文（SIGCOMM 2025）：https://www.microsoft.com/en-us/research/wp-content/uploads/2025/08/benyahya25mosaic.pdf
- [W5] MediaTek 与 Microsoft Research 的 microLED AOC：https://www.prnewswire.com/news-releases/mediatek-develops-active-optical-cable-technology-with-microsoft-research-to-deliver-significant-improvements-in-data-center-efficiency-302716631.html ；https://convergedigest.com/mediatek-showcases-microled-optical-interconnects/
- [W6] Avicena 1 Tbps 评估套件：https://convergedigest.com/avicena-ships-1tbps-microled-optical-interconnect-evaluation-kits/
- [W7] Avicena 在 ECOC 2026 演示可插拔 microLED 互连：https://convergedigest.com/avicena-connectorized-microled-optical-interconnect-ecoc-2026/ ；https://www.semiconductor-today.com/news_items/2026/sep/avicena-170926.shtml
- [W8] CEA-Leti microLED 互连产业化项目：https://www.eetimes.com/inside-cea-letis-push-to-industrialize-microled-interconnects/
- [W9] Marvell 与 Mojo Vision 合作：https://investor.marvell.com/news-events/press-releases/detail/1012/marvell-and-mojo-vision-collaborate-to-develop-next-generation-high-density-micro-led-connectivity-solutions
- [W10] Mojo Vision 300 mm GaN-on-Si 与融资：https://www.microled-info.com/mojo-vision-lit-its-first-300-mm-gan-silicon-blue-microled-wafer ；https://www.businesswire.com/news/home/20260325915711/en/
- [W11] MicroLED Connect 2026 Optical I/O 议程（UCSB、Tera Electronics、ALLOS、Avicena 等）：https://www.techblick.com/post/introducing-the-program-microleds-for-ai-infrastructure-the-optical-i-o-opportunity
- [W12] ams OSRAM 宽而慢 microLED 阵列：https://www.eqs-news.com/news/corporate/ams-osram-unveils-ultrae28091efficient-microled-array-for-slow-and-wide-ai-optical-interconnects-and-advances-to-product-development/9ca2d8d3-3930-49ae-affd-5747eb3f7c34_en
- [W13] Vuzix Causeway 波导：https://convergedigest.com/vuzix-causeway-waveguide-ai-data-center-optical-interconnects/
- [W14] Insight Media：MicroLEDs for Data Center Optical Interconnect: The Big Pivot?：https://www.insightmedia.info/microleds-for-data-center-optical-interconnect-the-big-pivot/
- [W15] TrendForce：Micro LED 光互连生态图谱：https://www.trendforce.com/news/2026/06/29/news-mapping-the-micro-led-optical-interconnect-ecosystem/
- [W16] Credo 30 m 有源光缆相关报道：https://photoncap.net/p/the-dispersion-problem-in-microled
- [W17] Ennostar、AUO、Tyntek microLED CPO：https://www.ledinside.com/products/2026/4/2026_04_02_01 ；AUO 在 SEMICON Taiwan：https://convergedigest.com/auo-micro-led-cpo-glass-core-ai-interconnects/
- [W18] Aledia 与 AUO 合作：https://www.microled-info.com/aledia-and-auo-co-develop-3d-nanowire-based-microled-displays-and-optical-io
- [W19] 思特威与紫光展锐合作：https://www.microled-info.com/smartsens-technology-and-unisoc-jointly-develop-microled-optical-io
- [W20] Teradyne Iris 100：https://convergedigest.com/teradyne-iris-100-microled-optical-interconnect-test/
- [W21] Intel 与 AUO 玻璃基 microLED 封装：https://www.microled-info.com/intel-partner-auo-microled-packaging-next-gen-optical-io-solutions
- [W22] Avicena 在 SC25 的进展（fJ/bit、无 FEC BER）：https://www.hpcwire.com/off-the-wire/avicena-advances-microled-and-photo-detector-arrays-to-enable-the-worlds-lowest-power-ai-scale-up-optical-interconnects/
- [W23] photoncap：microLED 光互连的色散问题（MOSAIC 数据、Credo 30 m、Hyperlume 专利）：https://photoncap.net/p/the-dispersion-problem-in-microled
- [W24] ams OSRAM 为 Avicena 制造 microLED 阵列：https://www.electrooptics.com/news/osram-manufacture-microled-arrays-avicenas-lightbundle-architecture
- [W25] DIGITIMES：华创芯光称 microLED 光互连 3–5 年进入数据中心：https://www.digitimes.com/news/a20260910PD232/data-communications-technology-shenzhen-transmission.html
- [W26] AUO 玻璃芯基板（SEMICON Taiwan 2026）：https://www.globenewswire.com/news-release/2026/08/31/3353270/0/en/auo-showcases-micro-led-optical-communication-and-glass-core-substrates-technologies-at-semicon-taiwan-2026.html

**本地资料**：ECOC 2026 讲稿笔记（Microsoft Tu1-E3、Lumentum Su4-I-03、Ciena Su3-I-05、Marvell Su3-I-07、Credo Su4-I-07、NVIDIA Mo4、fibeReality、Nokia Bell Labs PDP-A-6、博升 We5-I、0923-MF-00 连拍 p63、EBO MSA）；OFC 2026 论文 Th1G.3、Th1G.4；ECOC 2025 论文 Tu.01.09.5。相关章节另见 [[Optical Communication/01. Conference/2026 ECOC/专题洞察/2026 光互连五大专题深度洞察|2026 光互连五大专题深度洞察]] 第四章 Slow & Wide。
