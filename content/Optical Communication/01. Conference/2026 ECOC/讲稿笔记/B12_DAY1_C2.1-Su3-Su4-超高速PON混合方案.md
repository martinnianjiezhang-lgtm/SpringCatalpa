---
title: "B12 · DAY1 · C2.1-Su3-Su4-超高速PON混合方案"
tags:
  - ECOC2026
  - DAY1
---

### 0920-pm-Su4-F-05-华为-直检的极限与变通.pdf
- 讲者/机构：Giuseppe Talli（署名 Talli / Andrenacci / Cano，Huawei；题目页仅列作者，未标明讲者） | 题目：Pushing Direct Detection: Limits and Workarounds for VHSP（Su3-F 场，"Hybrid Solutions… IMDD worlds?"，ECOC 2026, Malaga, 19 Sept） | 类型：邀请报告/Workshop
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 3 调制器（EAM/IQ-MZM 架构比较）
- 核心主张：
  1. 混合下行架构：OLT 端对光强+相位调制（预补偿固定色散 DCPC，或单边带 SSB 消除色散功率衰落），ONU 仍用直检（DD）+DSP 均衡残余损伤 [p2]
  2. IQ-MZM 发射机灵敏度与色散代价最优，但插损高、最复杂；EAM-PM、DD-MZM 惩罚小且固有损耗低，DD-MZM 是集成的较好折中 [p8]
  3. EAM+光滤波器可用低惩罚、中等插损实现 SSB，但需精确控制滤波器失谐或激光波长 [p8]
- 关键数据（均为 120G NRZ，OMA 代价相对 b2b IQ-MZM）：
  - DCPC（35 ps/nm 与 70 ps/nm 补偿）：2 EAM-π/2 约 4 dB 额外惩罚；EAM-PM 1–2 dB [p5]
  - SSB（可达 120 ps/nm）：2 EAM-π/2 额外 4–6 dB（讲者归因于 EAM 消光比导致 CSPR 非最优）；EAM-PM 1.5 dB；DD-MZM 1 dB，含 3 dB 固有调制损耗 [p6]
  - EAM+光滤波器：200 GHz 4阶高斯滤波器，失谐 107.5 GHz，相对 IQ-MZM 惩罚约 1 dB，滤波器损耗约 5 dB [p7]
  - 调制器最小固有插损表：DCPC-IQ-MZM 15 dB；DCPC-2EAM 6 dB；DCPC-EAM-PM 3 dB；SSB-IQ-MZM 12 dB；SSB-2EAM 6 dB；SSB-EAM-PM 3 dB；SSB-DD-MZM 3 dB；SSB-EAM+滤波器 8 dB [p8]
  - 仿真中 EAM 消光比设 7 dB，IQ 调制器设 30 dB [p5]
- 提到的公司/客户/产品/标准：Huawei；关联论文 Andrenacci et al., "Experimental Evaluation of PAM2-SSB and PAM2-SSB+DCPC for a 2x100Gb/s/λ Very High Speed PON Downstream"，Mo4-P-86（9/21 15:30）；VHSP（Very High Speed PON）[p3]
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；为各调制器方案的横向比较 [p8]
- 推荐配图页：p8（调制器方案—惩罚—固有插损总表）；p5（DCPC 三种调制器结构及 OMA 惩罚—色散曲线）

### 0920-pm-Su4-F-06-Adtran-200G-PON与相干.pdf
- 讲者/机构：Martin Kuipers / Adtran | 题目：200G PON – The next territory for coherent technology（p2 题目页，20 Sept 2026） | 类型：邀请报告/Workshop（Su4-F 场）
- 方向归属（主/次）：主 5 固定与无线接入 PON | 次 1 相干（相干 PON/ZR 成本类比）
- 核心主张：
  1. 相干、混合、IM-DD 三种 VHSP 方案各有取舍；混合方案把低成本 IM-DD 功能放在 ONU、相干功能放在 OLT [p3]
  2. "相干并不那么贵"：按同等集成度与量产规模，200G PON 的相干制造成本与 IM-DD 可比；现有巨大价差源于市场与量级不同 [p6/p7]
  3. 2032 年将具备 ≥3.2 Tbps 相干接口、≥480 GBaud、≤2 nm CMOS、大规模电光集成等，届时低成本低功耗 200G 相干 PON SFP "将不再是问题" [p8]
- 关键数据：
  - LightCounting 与 Omdia 预测 100G ZR 相干与 50G PON 收发机 ASP 差距 >10x（2030 年图中标 ~10x；来源 Nokia，ONDM'26）[p6]
  - PON 与 DWDM ZR 单元数量差 10–20 倍；DWDM ZR 创新周期 3–4 年 vs PON 7–10 年 [p6]
  - 200G PON 制造成本构成（IM-DD / 相干，占 IM-DD 总成本 %）：激光器/LO 15%/27%；调制器/驱动 12%/16%；光放大 5%/3%；接收光子 9%/10%；TIA 7%/7%；ADC/DAC+DSP 11%/27%；WDM/滤波 8%/3%；PCB/电源/MCU 7%/11%；外壳/连接器 5%/5%；其他 3%/4%；直接材料 82%/113%；良率/报废 8%/17%；装配人工 6%/7%；终测人工 4%/8%；合计 100%/146% [p7]
  - 200G IM-DD PON 需两个波长 [p7]
- 提到的公司/客户/产品/标准：Adtran；Acacia（图源：模块功耗/相对功率随年份下降）[p5]；Omdia、LightCounting、Cignal AI（价格预测）；Nokia（ONDM'26 图源）
- 与业界对比或记录声明（SOTA/首次/record）：无；成本对比为讲者自行计算的"Calculated COGS"，非实测 [p7]
- 推荐配图页：p7（IM-DD vs 相干 200G PON ONU 成本构成表）；p3（相干/混合/IM-DD 三方案空间）

### 0920-am-Su2-G-01-Sorbonne-待定议题.pdf
- 讲者/机构：未见题目页与讲者姓名（Sorbonne 大学量子网络团队 / Welinq；p1 看图核实为 ParisRegionQCI 测试床页，引用 Diamanti 组与 Laurat 等工作，无法确认讲者） | 题目：未见（内容为 Telecom-Heralded Repeater Segment / 冷原子量子存储 / Paris 区域量子网络） | 类型：邀请报告
- 方向归属（主/次）：主 6 QKD/量子 | 次 无
- 核心主张：
  1. 演示由电信波段宣告（heralding）的量子中继段：两个独立本地节点（冷原子 Rb 量子存储器）+ 电信 50 km 中间宣告站；需要监控工具与电信基础设施集成 [p3]
  2. 冷原子系综量子存储器效率已达 90%，并已产品化（QDRIVE）[p8, p10]
  3. 光子接口可编程，用于连接异质平台（超导、离子、光子）[p12]
- 关键数据：
  - 2018 年存储器（3 cm 长 MOT，OD>400，Nature Communications，Vernaz-Gris…Laurat）：极化量子比特保真度 >99%，存取效率 70% [p7，看图核实]
  - 新实验：单光子（g2=0.1）存取效率 90%；两存储器间纠缠存取整体转移 85%（concurrence 比）；Optica 7, 1440 (2020) [p8]
  - QDRIVE：19 英寸机架，室温运行，Rb 原子 EIT 型；保真度 >99%，效率 >90%；2025 年发布、可商购；效率随存储时间衰减曲线，起点约 85%，约 400 µs 降至接近 0（读图估计）[p10]
  - 任意波形存储与转换：超导→离子 η=87(1)%，Ic=79.7(2)%；光子→离子 η=86(1)%，Ic=82.3(2)%；纠缠产生率较滤波方案 ×60（讲者标注）；波形目标取自 Innsbruck 单 Ca 离子 [p12]
  - 巴黎测试床：24 km 光纤环路穿越巴黎市中心，White Rabbit 精确授时 + 单光子干涉相位稳定，Refimeve+；关联直方图峰值约 600 counts，峰位约 -120 µs [p14]；50 km 骨干与多拓扑（ParisRegionQCI，节点 N1 Orange Chatillon 可信节点 至 N10 Welinq）[p1，看图核实]
  - 高效纠缠光子对源（Welinq）：19 英寸 3U，室温，腔内 SPDC，光纤内宣告效率 >60%，线宽 1–5 MHz，795 nm 与 C 波段非简并，2026 年发布并已交付客户 [p15]
  - 量子货币（不可伪造量子货币，Diamanti 组 npj QI 4, 5 (2018)；含存储的理论 PRA 99, 022336 (2019)；Mamann et al., Science Advances 11, eadx3223 (2025)）：引入中间量子存储层需存储器高效率、极低噪声 [p9，看图核实]
- 提到的公司/客户/产品/标准：Welinq（QDRIVE、光子对源）；Sorbonne University；Université Paris Cité；Orange Labs、Thales、Nokia Bell Labs、LIP6、C2N、MPQ、Laboratoire Kastler Brossel（测试床节点，p1 看图核实）；ParisRegionQCI；France QCI；White Rabbit；Refimeve+；Innsbruck
- 与业界对比或记录声明（SOTA/首次/record）：QDRIVE 被称为 "World record quantum memory turned into a product" [p10]
- 推荐配图页：p10（QDRIVE 产品与效率/保真度）；p3（电信宣告中继段架构）；p14（巴黎 24 km 环路实验）

### 0920-am-Su2-G-02-中科大-城域多路复用量子中继.pdf
- 讲者/机构：USTC 郭光灿团队（署名 Zhou、Li、Guo；讲者姓名幻灯片未显示，p28 团队页列 GC Guo、CF Li，另 C. Zhang、YF Huang、JM Cui；招聘链接指向 zhouzongquan 主页，看图核实） | 题目：未见完整题目（内容为 Metropolitan multiplexed quantum repeaters, XingHan 2.0/2.1 与气球链） | 类型：邀请报告
- 方向归属（主/次）：主 6 QKD/量子 | 次 无
- 核心主张：
  1. XingHan 2.0：基于 MQR-TM（多路复用、时间测量型量子中继协议）的城域多路复用量子中继，两个 Eu:YSO 存储器相距 14.5 km（光纤 17.9 km），首次对城域量子中继链路做 Bell 检验 [p10, p14]
  2. XingHan 2.1：基于多路复用量子中继的城域隐形传态，隐形传态距离 14.5 km、信道距离为零 [p19]
  3. 提出平流层气球链作为全球骨干信道；未来架构为"量子中继骨干 + 可运输存储节点" [p6, p27]
- 关键数据：
  - 背景：单颗 LEO 卫星 1200 km；光纤 404 km [p2]；此前城域中继 SPI 型最大保真度 0.64，无法违反 Bell 不等式，EDR 约 10 mHz @10 km；TPI 型 Bell 检验仅 1.3 km、EDR 0.3 mHz [p4, p5]
  - XingHan 2.0：HOM 可见度 95.9(2)%（独立光子对源）；AFC 存储 M=1205 模；纠缠存储效率 16.6% @100 µs（通信延迟 99 µs）；腔增强 SPDC 带宽 10 MHz；无光纤稳定 [p10, p11]
  - 宣告纠缠（前馈）保真度 F+ = 78.6(2.0)%；CHSH S = 2.22(0.06) > 2；宣告速率 23.6 kHz（SPI 可接近 50 kHz），仅 107 Hz 事件被 TPC 分析 [p13]。交换后光子纠缠（延迟选择，580 nm 光子先于 BSM 探测，3 mW 泵浦、20 ns 窗口）保真度 F+ = 76.3(1.1)%、F− = 77.0(1.2)% [p12，看图核实]
  - 最大 EDR 0.94 Hz @14.5 km，较此前 SPI 工作高两个数量级；同期其他单原子工作：Nature 652, 51 (2026) 2.2 Hz @10 km 光纤；Science 391, 592 (2026) 0.7 Hz @11 km [p14]
  - XingHan 2.1：存储时间 Alice 端 99 µs、Bob 端 180 µs（看图核实）；输入量子比特用平均 0.01 光子弱相干脉冲；同保真度（约73%）下纠缠速率比 2.0 提高 3 倍；隐形传态保真度 0.760±0.015，超过严格经典界 0.7014，隐形传态速率 0.68 mHz；无前馈平均 0.611±0.015 [p17/p18]
  - 隐形传态距离由 3 m（Delft）扩展至 14.5 km，零信道距离；在自由运行的城市光纤网络中稳定运行（相位校准约 12 h 稳定，图）[p19]
  - 异质纠缠：囚禁离子 Yb⁺–Eu³⁺:YSO 存储器，纠缠存储效率 42%，保真度 89.2(2.3)%，CHSH 违反 [p20]
  - 骨干信道 10⁴ km 损耗对比：光纤 2000 dB（低成本）；GNSS 卫星 84 dB（很高）；真空光束导 1 dB（很高）；卫星链 33 dB（高）；气球链 21 dB（高/中?）；优化后的气球链比卫星链低 12 dB（波束腰位置优化 + 级联 AO；Liu…Zhou, Li, Guo, PRA 113, 022614 (2026)）[p22, p23，看图核实]
  - 仿真 EDR 1 Hz @10⁴ km，用 Eu:YSO 存储器：效率 80.3%，寿命 27.6 s（计算值取 80%、1 s），依赖模式 1097（取1000）、独立模式 11（取10）[p25]
- 提到的公司/客户/产品/标准：无企业；引用 Delft、Harvard、MPQ、Innsbruck 等对比工作 [p14]；XingHan 命名（星汉/银河）[p29]
- 与业界对比或记录声明（SOTA/首次/record）：稀土离子体系"最长存储器间隔（14.5 km）与首个城域中继链路 Bell 检验" [p14]；隐形传态距离由 3 m 增至 14.5 km [p19]。核实：Nat. Photonics 20, 812 (2026) [p14]
- 推荐配图页：p14（各体系基本中继链路性能对比表与散点图）；p18（隐形传态保真度）；p22（骨干信道损耗对比表）

## 本批小结
1. VHSP（超高速 PON）下行的两条"折衷"路线并行：华为讲 OLT 侧用 DCPC/SSB 让 ONU 保持直检，Adtran 主张混合或相干 ONU 在同等量产下成本可比；分歧点在 ONU 成本，两者都把复杂度放到 OLT。（Huawei p5–p8；Adtran p3、p7）
2. 混合下行方案中调制器选择即成本/性能权衡：IQ-MZM 惩罚最小但插损 12–15 dB，EAM-PM 与 DD-MZM 以 1–1.5 dB 惩罚换 3 dB 固有损耗；光滤波 SSB 是低复杂度选项。（Huawei p8）
3. Adtran 的相干 PON 论据主要靠成本模型：相干 ONU 计算 COGS 为 IM-DD 的 146%，ADC/DAC+DSP 与激光器占大头；论点依赖 2032 年 480 GBaud/2 nm 及 AI 投资拉动，属预测而非实测。（Adtran p6–p8）
4. 量子中继在 ECOC 2026 走向城域实测与产品化：USTC 在 14.5 km 上做 Bell 检验与隐形传态（保真度 0.760，EDR 0.94 Hz），Sorbonne/Welinq 展示 24 km 巴黎环路与商用 QDRIVE 存储器（效率 >90%）。（USTC p14、p18；Sorbonne p10、p14）
5. 两个量子讲稿的中继路线不同：USTC 用 MQR-TM+多路复用规避相位稳定，Sorbonne 依赖 White Rabbit 授时与单光子干涉相位稳定；两者都指向与电信光纤基础设施集成。（USTC p9、p11；Sorbonne p14）
