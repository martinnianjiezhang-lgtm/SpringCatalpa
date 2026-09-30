---
title: "B29 · DAY2 · Mo3-I-AI互连之争-第一场"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo3-待定-Corning-AI互连的纵向与横向扩展路径.pdf
- 讲者/机构：Qi (Chris) Wu, Hao Dong, Ming-Jun Li / Corning Incorporated（p1 看图核实，联系邮箱 wuq@corning.com，页面未注明谁主讲） | 题目：Fiber Bundle Connector Solutions for VCSEL-Based Optical Scale-Up Interconnects | 类型：邀请报告（Symposium "Winning Interconnects for AI: Scale-Up & Scale-Out Technology Paths"）
- 方向归属（主/次）：主 4 Scale-up/in（NPO/VCSEL）；次 3
- 核心主张：
  1. 低功耗 VCSEL NPO 技术对 scale-up 网络有吸引力 [p8]
  2. 新型光纤与光纤束连接器正在解决密度挑战 [p8]
  3. 光纤束方案可直接插接现有低功耗 VCSEL NPO 引擎，连接器数量减少 4 倍；通用光纤束连接器可适配不同收发阵列间距与模块形态 [p8]
- 关键数据：
  - VCSEL 优点：低能耗、低时延、易耦合、2D 带宽密度扩展；已在 HPC 互连验证、消费电子量产规模 [p2]
  - Broadcom 100G VCSEL 3.2T NPO 示例：功耗 5.3 W 即 1.5 pJ/bit（对比 SiPh CPO/NPO 约 5~9 pJ/bit）；可靠性 <0.1 FIT；支持 >58T escape 带宽（18 个 3.2T NPO，图注 58T）；引擎为 4×8-CH VCSEL & PD 阵列 + 4×8CH Driver & TIA；来源标注 I-H. Tan, CIOE 2026 [p5，图片倒置]
  - 挑战：每个 NPO 引擎需 4 个 MPO-16 连接器及线缆；如何用新光纤/光纤束连接器对接 250 µm 间距的标准收发阵列 [p5]
  - 多模高密光纤：多芯(multi-cane) MCF 用于 <50 µm 间距阵列；缩径光纤保持约 50 µm 芯径，涂覆层 125 µm 减至 65 µm，无需剥覆直接端接，>50 µm 阵列间距（图示 φ50 µm core / φ110 µm clad / φ125 µm coating）；来源 J. McCarthy et al., ECOC 2026 [p3]
  - 125 µm 涂覆光纤端接：可用标准陶瓷或多芯插芯免剥覆端接，兼容常规研磨工艺与端面几何；光纤束置于插芯每个 macro feature，复杂度低于传统微孔插芯；来源 Q. Wu et al., Photonics West 2026 [p4]
  - 64-f 连接器：64 根光纤分为 8 束置于一个插芯，每束可支持一条 OCI 型 scale-up 链路；单个 64-f 连接器替代 4 个 MPO-16；breakout 直接对接现有 250 µm 间距收发器，NPO 模块内即插即换 [p6，看图核实]
  - 原型：激光加工玻璃原型插芯，连接器保持 MPO-16 外形；breakout 做成 250 µm 间距 ribbon（mini-matrix）；研磨的光纤束端面；模压插芯并行开发中 [p7]
  - 结尾页 OCR 显示 scale-up 链路特征：最大距离约 30 m，每链路约 200 Gb/s，需求为高可靠、高能效、低 \$/Tbps、低时延、高 escape 带宽（该页为 Corning 页脚，可能属连拍/下一讲，归属存疑）[p11 of Scintil PDF]
- 提到的公司/客户/产品/标准：Broadcom 100G VCSEL 3.2T NPO、Nvidia（图源署名，OCR）、OCI、MPO-16、SiPh CPO/NPO
- 与业界对比或记录声明：Broadcom VCSEL NPO "Record low power at 5.3 W, or 1.5 pJ/bit"（引用自他人工作，非 Corning 本身）[p5]
- 推荐配图页：p6（64-f 光纤束连接器端面与 breakout 结构）；p5（VCSEL NPO 功耗对比与 58T 架构）

### 0921-Mo3-待定-Nokia-AI互连路径.pdf
- 讲者/机构：Nokia（讲者姓名本批页面未显示） | 题目：AI 互连路径（英文原题未见；内容为 pluggable/LPO/LRO/NPO/CPO 演进与能效） | 类型：邀请报告
- 方向归属（主/次）：主 3 Scale-out（可插拔 vs 线性/CPO 演进）；次 4
- 核心主张：
  1. 训练算力约每 6 个月翻倍（1950–2010 年为约 21 个月），驱动互连带宽需求 [p2]
  2. 收发器演进经 线性/模拟时代(NRZ) → CDR 时代(NRZ) → DSP 时代(PAM-4) → "Co-optimization age"（2030 前后）；候选为 LPO、LRO、NPO、CPO、CPC、NPC、XPO，目标是克服铜互连限制并省电 [p6]
  3. CPO 和 NPO 通过启用线性光学去除 DSP 降低功耗；进一步优化来自选择更低功耗 ASIC SerDes 并降低 ASIC 与光接口间电信号幅度 [p10]
- 关键数据：
  - 训练算力图：2010 年起翻倍周期约 6 个月；1950–2010 约 21 个月；标注 Gemini 1.0 Ultra、GPT-4、AlphaGo Zero、AlexNet 等；来源改编自 EPOC [p2]
  - 收发器带宽 30 年演进图：纵轴 0.1G 至 6,400G，QSFP-XD 1.6T 标注为近期，2030 处星标 [p4]
  - 光收发器 TAM：Lightcounting Optical Components Market Forecast (April 2026)；销售额（全部收发器与 AOC）2022 约 \$12k M → 2026 约 \$40k M → 2031 约 \$77k M（读图估计，看图核实）；出货量图分 Ethernet、AOCs、CWDM/DWDM、无线前传/回传、FTTx，2031 约 550 M 单位（读图估计）[p1]
  - 可插拔结构（≥100G/lane）：全 retimed DSP / LRO（半 DSP）/ LPO（无 DSP）；投影功耗曲线（纵轴 0–50，幻灯未标单位）：800G、1.6T、3.2T 三点，DSP(5 nm) > DSP2(3 nm) > LRO > LPO，3.2T 时 DSP 约 50、DSP2 约 40、LRO 约 30、LPO 约 20（读图估计，看图核实）；LPO 适用于 100G/lane 且 bump-to-bump 总损耗 <20 dB [p9]
  - LPO 在总通道损耗（bump to bump）低于 20 dB 时对 100G/lane 表现良好 [p9]
  - 能效对比（pJ/bit，800G 与 1.6T 两点）：800G 时 Fully Retimed 约 22、LRO 约 18.5、LPO 约 13、NPO 约 12、CPO 约 11.5；1.6T 时 Fully Retimed 约 18、LRO 约 13、LPO 约 9、NPO 约 8、CPO 约 7.5（读图估计，误差约 ±1）[p10]
  - p11 看图核实：Nokia 7220 IXR 系列交换机示例——H5-32D（25.6T、1RU、32×800G QSFP112-DD）、H5-64O/D（51.2T、2RU、64×800G OSFP112 或 QSFP112-DD）、H6-128（102.4T、4RU、128×800G OSFP112）、H6-64（102.4T、2RU、64×1.6T OSFP224）；模块 OSFP 800G 2×VR4/2×FR4/2×DR4 及 2×FR4 LPO/2×DR4 LPO（800G 全重定时与 LPO），OSFP 1.6T 2×FR4/2×DR4（1.6T 全重定时）[p11]
- 提到的公司/客户/产品/标准：Nokia 7220 IXR-H5 系列、Lightcounting、EPOC、LPO/LRO/NPO/CPO/CPC/NPC/XPO、QSFP-DD、OSFP、QSFP-XD
- 与业界对比或记录声明：无 SOTA 声明
- 推荐配图页：p10（各光架构能效 pJ/bit 曲线与结构示意）；p6（收发器演进四个时代）

### 0921-Mo3-待定-ScintilPhotonics-AI互连路径.pdf
- 讲者/机构：Scintil Photonics（讲者姓名看不清） | 题目：AI 互连路径 / 面向 scale-up 的外置激光源 ELS（英文原题未见；页标题 "What must a scale-up ELS deliver?"） | 类型：邀请报告
- 方向归属（主/次）：主 3 光源；次 4 CPO/ELS
- 核心主张：
  1. 只有分立 InP DFB 激光器能满足 scale-up ELS 指标，并提出问题：制造能否扩到 10 亿（1,000 million）量级 [p1]
  2. Scintil 的 LEAF Light 不只是激光阵列芯片，含片上 etalon 与监测 PD 的自动波长锁定、自动 mux 设定、寿命监测、单次 PIC/光纤主动对准的简单组装 [p6]
  3. SHIP（异质集成光子）在制造、材料、性能三轴同时可扩展 [p8]
- 关键数据：
  - ELS 要求：每波长光功率 200 mW；光纤内 wall-plug 效率 >10%；RIN <-144 dBc/Hz，线宽 1 MHz；C/D-WDM（间隔 20 nm 至 0.57 nm）；波长栅格稳定准确 ±0.2 nm；低 FIT；引用 OIF ELSFP 与 OCI-MSA [p1]
  - LEAF Light 子组件：2025/09 版 8 激光器 + Mux + 波长锁定器 + LEAF Light CTRL 电子；2026/09 版 16 激光器 + Mux + 波长锁定器 + CTRL 电子；实物与 ELSFP 外壳、欧元硬币对比 [p6]
  - SHIP：200 mm 标准 Si 光子，300 mm 评估进行中；材料 InP（当前）、GaAs QD-DFB 改进型激光器开发中、TFLN 调制器 200 mm（85+ GHz TFLN 调制器）；性能含外置激光源、带 SOA 的集成收发、100 GHz+ 调制器 [p8]
  - 另一页（PDF p11，看图核实）：scale-up 链路最大距离约 30 m、每链路约 200 Gb/s、链路数 = N_GPU × M_SW、全互连；关键需求：高可靠、高能效、低 \$/Tbps、低时延、高 escape 带宽（该页为 Corning 页脚，应属 Corning 讲稿，误归入本文件）
- 提到的公司/客户/产品/标准：LEAF Light、SHIP、OIF ELSFP、OCI MSA、InP DFB、TFLN
- 与业界对比或记录声明：无明确 record 声明
- 推荐配图页：p6（16 激光器 LEAF Light 子组件实物）；p1（ELS 指标表）

### 0921-Mo3-待定-Tyndall-AI互连路径.pdf
- 讲者/机构：Tyndall National Institute（讲者姓名页面未显示；含 EU Photonics21 / PhotonicLEAP 项目标识） | 题目：Glass Wafer-Level Packaging（含后续 Electro-Optical Interposer） | 类型：邀请报告
- 方向归属（主/次）：主 4 Scale-up/in（封装/CPO 基板）；次 3
- 核心主张：
  1. 用玻璃晶圆级封装（Glass BGA package）替代传统封装，可在 200 mm 晶圆或 510 mm 面板上批量制造 [p1]
  2. 下一阶段发展为电光中介层（Electro-Optical Interposer），光学层可在玻璃电中介层上做（如 SiN）或键合（如微转印），兼容大面积玻璃面板，转印有源光器件 [p12，看图核实]；玻璃 BGA 封装 200 mm 晶圆可出 64 个、510 mm 面板可出 644 个 [p1]
- 关键数据：
  - 200 mm 晶圆可容纳 64 个封装；510 mm 面板可容纳 644 个封装 [p1]
  - 演示：InP PIC 置于玻璃基板腔体中，玻璃封装 BGA 连接；PhotonicLEAP 的可插拔演示器 [p5，图片倒置]
  - 设计流程：由模板创建玻璃中介层 → 建立含芯片版图的单元 → 芯片放置 → 添加过孔/键合焊盘/BGA/光学 → 电气布线 → 层级 DRC → 按合作方拆分 GDS [p8]
  - p7 看图核实：玻璃晶圆级封装截面（Seal ring、Au-Sn 焊料、RDL1–3、背面 RDL、BGA 落点；TGV 直径 >50 µm 等规则）；参考文献：Reference Thermal Chips for 2D and 3D Co-Packaging Process Development（IEEE 73rd ECTC, Orlando, 2023）；Thermal and Electrical Study of Glass Interposers in Co-Packaged Electronic–Photonic Systems（IEEE Trans. CPMT, 2025-08）
- 提到的公司/客户/产品/标准：PhotonicLEAP（EU）、Photonics21、InP PIC、MPO 连接器
- 与业界对比或记录声明：无
- 推荐配图页：p1（传统封装 vs 玻璃 BGA 封装与晶圆/面板批量化）；p8（设计流程）

## 本批小结
- 四场同属 "AI 互连之争" 专题（Mo3），共同点是把功耗（pJ/bit）与可制造规模作为 scale-up/scale-out 光互连的判据（Corning、Nokia、Scintil、Tyndall）。
- Corning 与 Nokia 的能效数据互相形成对比：Corning 引用 Broadcom VCSEL NPO 1.5 pJ/bit（5.3 W/3.2T），Nokia 图中 CPO/NPO 在 1.6T 约 7–8 pJ/bit（读图估计），二者口径不同（VCSEL 短距 vs 单模），不可直接比较（Corning、Nokia）。
- 线性光学趋势：Nokia 认为去 DSP 的 LPO/LRO/NPO/CPO 是"co-optimization age"方向，LPO 适用条件为 bump-to-bump 损耗 <20 dB（Nokia）。
- 连接与光纤密度是 VCSEL scale-up 的瓶颈：缩径多模光纤、多芯光纤束、64-f 连接器替代 4 个 MPO-16（Corning）。
- 光源成为 CPO/scale-up 的独立议题：ELS 要求 200 mW/波长、±0.2 nm 网格、RIN <-144 dBc/Hz，仅分立 InP DFB 满足，Scintil 将 8 激光器扩至 16 激光器（2025/09 → 2026/09）（Scintil）。
- 封装方向：玻璃晶圆/面板级封装及电光中介层，用于批量化与集成 InP PIC（Tyndall）。
