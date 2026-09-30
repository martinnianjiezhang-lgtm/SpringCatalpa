---
title: "B32 · DAY2 · Mo5-B-空芯光纤设计"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo5-B1-待核-空芯光纤设计.pdf
- 讲者/机构：讲者姓名幻灯片未显示（致谢页列 Jasion、Numkam Fokoua、Mahdiraji、Slavik、Richardson、Petrovich 等及 Microsoft Azure Fibre 团队）；Southampton ORC Hollow Core Fibre Group / Microsoft | 题目：Hollow Core Fibres: from scientific curiosity to multi-problem solution | 类型：邀请报告（Workshop/教程式综述）
- 方向归属（主/次）：主 1（长途/DCI 传输介质：空芯光纤）；次 2（AI DCI/跨楼园区）
- 核心主张（1–3条）：
  1. 反谐振空芯光纤（AR-HCF）15 年间损耗下降 >10,000x，已进入并低于实芯石英光纤的历史损耗水平 [p2, p28]。
  2. 设计路线：NANF -> DNANF -> 第1/第2/Hybrid 窗口；Hybrid window 兼顾带宽与制造良率 [p32–p34]。
  3. 应用导向：不同场景应选不同设计（SMF匹配/超抗弯、AI DCI 兼顾线缆密度、超低损耗做大）；"一个统一标准还是多个应用优化方案？"是抛给业界的问题 [p46]。
- 关键数据：
  - NANF（ECOC 2018 PDP，Bradley）：芯径30 μm，500 m，最低 1.3 dB/km @1450 nm（约8x硅），1.8 dB/km @950 nm（约2x硅）[p23]。
  - Southampton NANF 降损历程：1.3 dB/km（ECOC2018 PDP）-> 0.65（OFC2020 PDP，首个 sub-1 dB/km）-> 0.28（OFC2021 PDP，首个 sub-0.3）-> 0.22 dB/km（低于硅在850/1060 nm）[p24]。
  - DNANF（Jasion，OFC 2022 PD）：NANF 0.9 dB/km 对 DNANF 0.09 dB/km，泄漏损耗改善 >10x（幻灯片标注）[p25]。
  - <0.11 dB/km @1550 nm（Chen，OFC 2024 PDP Th4A.8）；0.09 dB/km（Petrovich，Nature Photonics 19, 1203 (2025)）[p28]。
  - 2025 损耗谱：第1窗口 5T DNANF（ORC，Petrovich et al., Nat. Photon. 19, 1203 (2025)）、第2窗口 5T DNANF（YOFC，约 0.05 dB/km）、4T-IT（LinFiber，约 0.05–0.06 dB/km）、4T-IT DNANF（YOFC，曲线最低，约 0.04 dB/km @1570–1610 nm）；对照 PSCF Sato 2025 约 0.14 dB/km（读图，看图核实）[p30]。
  - Hybrid window（Mahdiraji，OFC 2026 PDP Th4B.8）：管壁厚 第1窗口 t~450 nm（最大带宽）/ 第2窗口 t~1150 nm（最大良率）；同芯径27 μm，管径约31/26/12 μm；Hybrid（中管厚 5%、内管薄 5%）在约 1530 nm 最低约 0.075 dB/km，低于第2窗口约 0.095 dB/km，且低损耗带向短波扩展（读图，看图核实）[p32, p33]。
  - 良率：Mid Draw Contact 压力窗口下，第2窗口相对第1窗口良率提升 2.5–3x，Hybrid 再提升 +30%；图示可拉制长度标注 30 km / 90 km / 120 km（对应1st/2nd/Hybrid，@Fixed Tension，纵轴单位 km/m）[p34]。
  - 色散（1550 nm，30 μm芯）：损耗 0.099 dB/km，色散 0.00 ps/(nm·km)，色散斜率 +0.053 ps/(nm²·km)，外管壁厚 1.27 μm [p36]。
  - 125 μm 外径 mode-field 匹配 HCF（OFC24 M3J.5）：弯曲与模式良好，但损耗约 25 dB/km [p39]。
  - 250 μm 涂覆 SMF 匹配 HCF：Gen1（OFC24 M3J.5）约20 dB/km量级 -> Gen2（ECOC24 Th1A.1）约1.5–2 dB/km量级（标注10x）-> Gen3（ECOC25 Th.03.01.2）C波段约0.25 dB/km量级（标注8x），O/S/C/L 覆盖；纵轴读数为估读 [p42]。
  - 抗弯：DNANF125 在弯曲半径5–40 mm 弯损约1e-4–1e-3 dB/turn 量级；实测下至12.5 mm 直径（40圈）几乎无弯曲附加损耗；优于 G.657.B3（讲者措辞"最抗弯光纤(?)"）[p43]。
- 提到的公司/客户/产品/标准：Microsoft（Azure Fibre）、Southampton ORC、YOFC（长飞）、LinFiber（领纤）、Corning、U of Bath/Blazephotonics、FORC Moscow、Limoges/XLIM、CREOL；标准 G.652.D、G.657.A1/A2/B3、SMF-28、OM4/5。
- 与业界对比或记录声明（SOTA/首次/record）：首个 sub-1 dB/km HCF、首个 sub-0.3 dB/km HCF、0.22 dB/km 低于硅（850/1060 nm）[p24]；0.09 dB/km 与实芯石英光纤损耗历史曲线交汇 [p28]；"最抗弯光纤"[p43，讲者带问号]。
- 推荐配图页：p28（HCF 与实芯光纤损耗随年份对比，HCF 十年降四个数量级并追平硅）；p30（2025 年各窗口 DNANF 损耗谱及 YOFC/LinFiber/Microsoft 结构）；p34（Hybrid window 良率）。

### 0921-Mo5-B2-待核-空芯光纤设计.pdf
- 讲者/机构：Federico Melli（报告人，下划线）, Lorenzo Rosa, Fetah Benabid, Annamaria Cucinotta, Luca Vincetti / Univ. Parma、Univ. Modena and Reggio Emilia、XLIM (Limoges)；幻灯片带 SOFIA Photonics 标识 | 题目：A Unified Framework for Understanding Confinement Loss, and Engineering Bandwidth, and Modal-Dependent Loss in Hollow-Core Fibers（p1 看图核实） | 类型：学术论文
- 方向归属（主/次）：主 1（高波特率/传输介质：空芯光纤设计）；次 无
- 核心主张（1–3条）：
  1. 限制损耗（CL）可分解为模式耦合损耗（MCL，起决定长波端高损耗区）与管隧穿损耗（TTL，逐管求和）[p4, p16]。
  2. 椭圆管存在最优轴比可使传输带宽最大 [p7, p16]。
  3. TTL 与偏振/模式类型相关，可用于控制多模空芯光纤的模式损耗层级（mode-loss hierarchy）[p16]。
- 关键数据：
  - 椭圆管带宽展宽：MCL 阈值约1e-2 dB/km 下，带宽 Δλ_BW 随管轴比 b/a 从1.1增至约1.3时上升，在 b/a≈1.25–1.3 出现最大值约220 nm（图读数），此后下降至 b/a=1.4 约120 nm [p7]。
  - 嵌套管降低特定波长损耗，但伴随带宽缩减 [p3]。
  - 参考文献标注：Melli et al. Results in Optics (2024)；Melli et al. JLT (2026) [p4]。
- 提到的公司/客户/产品/标准：SOFIA Photonics（标识）；无产品/标准。
- 与业界对比或记录声明（SOTA/首次/record）：无。
- 推荐配图页：p7（椭圆管 b/a 与带宽曲线，含 MCL 协同/对抗机制标注）；p3（嵌套管数量与 CL 谱）。

### 0921-Mo5-待定-长飞YOFC-超高模纯度与单模匹配的O波段混合反谐振空芯光纤.pdf
- 讲者/机构：Zihan Dong（报告人）等 / YOFC（长飞，光纤光缆制备技术国家重点实验室）（p1 看图核实） | 题目：Ultra-high Mode Purity and SMF-matched O-Band Hybrid Antiresonant Hollow Core Fiber for Intra Data Center Connection | 类型：学术论文（ECOC 2026）
- 方向归属（主/次）：主 2（跨楼园区/DC内互连空芯光纤，短距）；次 3（Scale-out 光互连介质）
- 核心主张（1–3条）：
  1. 首次实现小外径（OCD）、小 MFD、超短距单模的 HCF，适合未来高密度、低时延的数据中心内互连 [p10]。
  2. 基于 gap-tube 辅助支撑的混合反谐振结构，在单模性与抗弯之间折中，大管2nd厚1 μm，中小管1st厚0.4 μm [p3]。
  3. 损耗仍有优化空间（结论页自述不足）[p10]。
- 关键数据：
  - 设计：芯径14 μm；d3=8 μm 时 @1310 nm，LP01 CL 约0.44 dB/km，LP11 约2187.93 dB/km，HOMER（LP11 CL/LP01 CL）约4950；d3=7.8–8.1 μm（Z2/Dcore 0.507–0.529）HOMER >1000 [p4]。
  - 仿真弯损（1310 nm 附近）：30/20/15 mm 弯径分别 <0.001 / <0.01 / <0.1 dB/turn [p5]。
  - 制备：连续拉制约10 km（低张力），Z2/Core 0.51–0.55；SOP/EOP 芯径 13.85/13.71 μm，1st厚 1.02±0.03 μm，2nd厚 0.4±0.03 μm，大管平均直径22.3 μm，gap 3.35±0.25 μm，OCD 240 μm [p6]。
  - 损耗：截断法 10.037 km 切至 10 m；1262–1340 nm 实测 <1.4 dB/km，1310 nm 总损耗 1.15 dB/km（仿真）；损耗主要来自 CL 与表面散射，CL 占比更大；适用范围数米至数百米；微弯损耗可忽略 [p7]。
  - 弯曲（测试长度8 m，绕10圈）：30/20/15 mm 直径下 0.0013 / 0.0026 / 0.03 dB/turn；关系 G.657.A2(1310) < HA-HCF(1310) < G.657.A2(1550) [p8]。
  - 模式：1310 nm S² 测得 LP11 截断损耗约6 dB/m，5 m 处 LP11 不可观测；MFD 中线 9.01/8.81 μm、对角线 9.97/9.66 μm，对比 G.657.A2(1310 nm) 8.4–9.2 μm [p9]。
- 提到的公司/客户/产品/标准：YOFC；G.657.A2；引用 OFC 2026 M2.1（Peng Li，低模间干扰低损耗 HCF）与 Th4B.8（Mahdiraji，双窗口 Hybrid 0.13 dB/km@1 μm、0.11 dB/km@1.55 μm）[p3]。
- 与业界对比或记录声明（SOTA/首次/record）：first realization of ultrashort-distance single-mode HCF with small MFD and small OCD [p10]。
- 推荐配图页：p10（六项指标总结与14 μm芯/240 μm涂覆截面）；p7（10 km 截断实测损耗谱）；p4（d3 扫描下 LP01/LP11 与 HOMER）。

## 本批小结
1. 空芯光纤损耗已追平并低于实芯：DNANF 达0.09 dB/km（Nature Photonics 2025）、OFC 2024 PDP <0.11 dB/km，且 YOFC、LinFiber 等中国厂商在第2窗口出现在同一损耗谱上（来自 B1 p28–p30）。
2. 设计焦点从"追极限损耗"转向"良率与可制造性"：Hybrid window 在保持接近第1窗口带宽的同时，良率相对第2窗口再 +30%，第2窗口相对第1窗口 2.5–3x（B1 p32–p34）；YOFC 也强调连续 10 km 低张力拉制（YOFC p6）。
3. 应用分化：B1 明确提出 SMF 匹配抗弯型、AI DCI（线缆密度优先）、超低损耗大芯三条路线，并抛出"单一标准 vs 多方案"问题；YOFC 的 O 波段 14 μm 芯、240 μm OCD 短距单模纤即是 DC 内互连方向的实例（B1 p46；YOFC p10）。
4. SMF 兼容成为关键指标：Southampton/Microsoft 的 250 μm 涂覆 SMF 匹配 HCF 三代迭代损耗降低约10x 再 8x，并在 12.5 mm 弯径几乎无附加损耗；YOFC 的 MFD 9.01/8.81 μm 与 G.657.A2 兼容，弯损在 1310 nm 介于 G.657.A2(1310) 与 (1550) 之间（B1 p42–p43；YOFC p8–p9）。
5. 理论侧（B2）为设计提供解析抓手：CL = MCL + TTL，椭圆管最优轴比可将带宽最大化，TTL 可调控多模 HCF 模式层级，与 YOFC 以 HOMER（>1000）筛选单模结构的思路相呼应（B2 p7、p16；YOFC p4）。
