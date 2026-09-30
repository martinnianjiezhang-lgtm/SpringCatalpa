---
title: "B76 · DAY5 · Th1-C-光电探测器"
tags:
  - ECOC2026
  - DAY5
---

### 0924-Th1-C3-NICT-免偏置200GHz带宽光电探测器面向800Gbps每通道.pdf（第1–11页；页码为PDF页，幻灯片角标=PDF页+2）
- 讲者/机构：NICT（联系邮箱 toshi_umezawa@nict.go.jp，讲者姓名以此推断，未见明确署名） | 题目：Bias-free operational 200 GHz PD for high-bandwidth TIA integration（PDF文件名对应“免偏置200GHz带宽光电探测器面向800Gbps每通道”，英文完整原题未见清晰题目页） | 类型：学术论文
- 方向归属（主/次）：主 3（Scale-out 224G/448G/高速光电探测器）；次 1（高波特率器件）
- 核心主张：
  1. 设计并制作了可零偏压工作的 200 GHz PD，用于与高带宽 TIA 集成、面向下一代收发器 [p11]。
  2. 零偏压下 3 dB 带宽 200 GHz，输出线性至 2 mA，252 Gbps PAM-4 [p11]。
  3. 讲者称 0 V 下有潜力达到 800 Gbps/lane（基于拟合响应的仿真眼图，非实测）[p10–11]。
- 关键数据：
  - 动机：PD 与 TIA 用单根键合线互连（Lw=50 pH，Cj=15 fF）时，-3 dB 点：Model-(a) 185 GHz，Model-(b) 245 GHz，理想 Lw=0 pH >300 GHz；TIA 芯片 BW >300 GHz；带偏置滤波网络的方案性能受限，故提出免偏置 PD [p2]
  - 设计思路：Design-1 高速 UTC 型 PD（p-InGaAs 吸收层/InP 收集层，耗尽层厚度扫描）[p3]；Design-2 吸收层高载流子浓度、收集层低载流子浓度，使 0 V 下结电容低且几乎不随偏压变化 [p5]；Design-3 电极设计（GSG 电极+匹配电阻，电感 5/10/20/43 pH 对比），仿真最大 3 dB 带宽 DC~300 GHz [p6]
  - S21 类 O/E 响应测量范围 10 MHz–220 GHz [p7]
  - 126 Gbps NRZ、0 V、无均衡：本 PD 光眼图 jitter RMS 607 fs；对比商用 50 GHz PD（2 V 偏压）jitter RMS 1010 fs；眼幅度随光电流线性，2 mA 处约 84 mV（40 Ω 端接实测）[p8]
  - 252 Gbps PAM-4、0 V、7-tap 均衡：BER 门限线 3.8×10^-3；输入光功率 +11 dBm 时 252 Gbps BER 约 2×10^-3，+9 dBm 时约 1.4×10^-2（图上读数，近似）；212 Gbps 约在 9~9.5 dBm 处越过 3.8×10^-3 门限 [p9]
  - 200 Gbps PAM-4、0 V、7-tap：BER <1×10^-4；实测频响 -3 dB 约 200 GHz；由拟合曲线仿真 200/400/600/800 Gbps PAM-4 眼图（分别 4/2/1/1 ps/div）[p10]
- 提到的公司/客户/产品/标准：IEEE 802.3df（Beyond 400 Gb/s Ethernet Study Group，2021年10月，短距 IM-DD 车道速率演进图：50/100/200 Gbaud 对应 100/200/400 Gb/s 每通道）[p1]；商用 50 GHz PD 作对比
- 与业界对比或记录声明（SOTA/首次/record）：未见 record 声明；对比商用 50 GHz PD，jitter 607 fs vs 1010 fs [p8]
- 推荐配图页：p9（252 Gbps PAM-4 眼图与 BER 曲线）；p10（200 Gbps 实测眼图+800 Gbps 仿真眼图）；p4（PD-TIA 键合线模型及各模型 -3 dB 带宽）

### 0924-Th1-D5-浙江大学-脊波导低损数字可调色散控制器.pdf（第1–19页；p14为p13重复，p20空白）
- 讲者/机构：Ruitao Ma、Shujun Liu、Zexu Wang、Weihan Wang、Yuyan Yao、Zejie Yu、Daoxin Dai，浙江大学光电科学与工程学院/光及电磁波研究中心（SING 集成纳米光子组），中国计量大学（作者单位之一）[p1] | 题目：Low loss Digitally Tunable Dispersion Controller Using Ridge Waveguides | 类型：学术论文
- 方向归属（主/次）：主 1（高波特率器件/色散补偿）；次 3（硅光集成，微波光子应用）
- 核心主张：
  1. 在标准 220 nm SOI MPW 工艺上，将双向数字调谐与低传播损耗结合 [p7, p18]。
  2. 浅刻蚀脊波导光栅降低传播损耗，全刻蚀布线保持紧凑；同一 CMWG 通过反转传播方向提供正/负色散 [p18, p11]。
  3. 5 级、31 个 CMWG 单元，二进制加权 MZS 数字调谐，实测色散范围 -251.87 至 +262.33 ps/nm [p13, p17–18]。
- 关键数据：
  - 背景：C 波段 SMF 色散 17 ps/(nm·km)（标注）；50–400 Gb/s PAM4 经 5 km SMF 后色散预算收紧（图，具体数值看不清）[p3]
  - 前人工作对比：S. Liu et al. Adv. Photonics 2023：20 nm 带宽，-61.53 至 +63.77 ps/nm，群时延调谐跨度 2.058 ns，缺点 CMWG 传播损耗较高；Wang W. et al. Nanophotonics 2026：单 CMWG 26 nm 带宽，0 至 49.72 ps/nm，1.304 ns，实测传播损耗约 0.22 dB/cm，缺点为有源集成不如 SOI 直接且尺寸大 [p7]
  - 架构：方向选择 MZS 决定色散符号，二进制加权 MZS 决定幅度；范围 -(2^Q-1)D0 至 +(2^Q-1)D0，热光切换；本工作 5 级 31 CMWG [p13]
  - 器件尺寸 4.85×0.4 mm²；slab 渐变 strip-to-rib 过渡降低界面损耗；深刻蚀隔热槽抑制热串扰；焊盘键合到 PCB [p15]
  - 光谱：工作带 1544–1553.2 nm；激活 CMWG 数 0,1,6,11…31；平均每 CMWG 插损 0.30 dB（正）、0.31 dB（负）[p16]
  - 群时延：平均每 CMWG D0 = +8.46 ps/nm（正）、-8.12 ps/nm（负）（平均步长幅度 8.30 ps/nm）；数字调谐范围 -251.87 至 +262.33 ps/nm；带符号群时延变化 -2.32 至 +2.41 ns；时延相关损耗 1.67 dB/ns（正）、1.40 dB/ns（负）[p17]
- 提到的公司/客户/产品/标准：LightCounting、Ethernet Alliance 2015 Ethernet Roadmap（背景图引用）[p2]；MZI、微环、慢光、Bragg 光栅等集成色散补偿方案（文献引用）[p6]；微波光子应用（信道化、色散补偿等）[p4]
- 与业界对比或记录声明（SOTA/首次/record）：未声明 record；定位为兼具前作的双向宽范围调谐与低传播损耗 [p7]
- 推荐配图页：p13（数字架构与芯片显微图+公式）；p17（实测群时延曲线与关键指标）；p16（正/负色散光谱）

## 本批小结
1. 器件带宽正向 200 GHz 以上推进：NICT 零偏压 PD 实测 3 dB 带宽 200 GHz，252 Gbps PAM-4（7-tap 均衡），并以仿真外推 800 Gbps/lane 潜力（来自 NICT 篇 p9–11）；注意 800G 为拟合响应仿真，非实测。
2. NICT 篇的核心工程逻辑是消除偏置滤波网络与键合线寄生：单键合线 PD-TIA 带宽 185/245 GHz，理想 >300 GHz，故走“0 V 免偏置+低电容+电极电感优化”路线，与 TIA >300 GHz 带宽匹配（NICT 篇 p4–6）。
3. 高波特率使色散预算收紧：浙大篇背景指出 50–400 Gb/s PAM4 经 5 km SMF 对色散更敏感，提出片上可数字调谐色散补偿器（浙大篇 p3, p17）。
4. 硅光 MPW 兼容的低损路线：浅刻蚀脊波导光栅+二进制加权 MZS 数字调谐，31 个 CMWG 单元覆盖 ±约 250 ps/nm，但时延相关损耗约 1.4–1.7 dB/ns 且工作带仅约 9 nm（1544–1553.2 nm），距离实用 C 波段全覆盖仍有差距（浙大篇 p16–17）。
5. 两篇均属器件/集成层面的基础研究，未涉及厂商产品或客户，与系统级 CPO/相干产业叙事关联较弱；NICT 篇引用 IEEE 802.3df 车道速率演进作为需求背景（NICT 篇 p1）。
