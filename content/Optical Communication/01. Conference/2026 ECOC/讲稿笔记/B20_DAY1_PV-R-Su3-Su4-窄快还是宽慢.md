---
title: "B20 · DAY1 · PV-R-Su3-Su4-窄快还是宽慢"
tags:
  - ECOC2026
  - DAY1
---

### 0920-pm-Su4-I-06-LightMatter-光计算路线.pdf
- 讲者/机构：讲者姓名未见 / Lightmatter | 题目：未见题目页（页1、2 OCR为空，未查看）；讲稿主题为 "Fast and narrow has a ceiling. Slow and wide does not — when it's 3D."（回答 Workshop Question：fast, narrow channel 能否无限上升） | 类型：邀请报告（Workshop，"窄快还是宽慢"）
- 方向归属（主/次）：主 4 Scale-up/in CPO；次 3 Scale-out 224G/448G/光源
- 核心主张：
  1. 单通道超过 112G 后，能耗、传输距离、时延三者都变差（"Fast and narrow has a ceiling"）。[p3, p15]
  2. 3D 堆叠 PIC 与 XPU，把电互连缩短到微米级，56G NRZ、约 2 pJ/bit 就够用。[p15]
  3. BiDi 让光纤数减半，DWDM 大幅提升带宽，带精确控制的集成激光器使"宽"成为可能。[p15]
- 关键数据：
  - 电 SerDes（长距类）能耗：56G NRZ 约 1–2 pJ/bit；112G PAM4 约 4–6 pJ/bit；224G PAM4 约 3–6 pJ/bit；448G PAM4/6 约等同 224G PAM4。[p5]
  - PCB 上电互连距离：56G NRZ 约 1 m；112G PAM4 约 30–50 cm；224G PAM4 约 10–20 cm；448G PAM4/6 仅 flyover 或 CPO。[p5]
  - FEC：56G NRZ 无/轻（BER <1E-9）；112G PAM4 为 RS/KP4 FEC；224G PAM4 为 KP4+ FEC；448G PAM4/6 需更强 FEC、时延更高。[p5]
  - 单纤 400G/800G/1.6T 方案：8×50G NRZ（无 DSP、无 FEC，1 km，对应 M1000，单封装 >100 Tbps）；16×50G BiDi（对应 EVK50）；16×100G PAM4（<3 pJ/bit，1 km，对应 EVK100）。窄快方案 1×800G、1×1.6T 标为 "No lane-rate roadmap / Undefined"。[p6]
  - MRM（微环调制器）直径约 15 um；电阻加热器调谐、耗尽型 PN 结调制；TX 端 CW 激光 + 一串 MRM 完成调制并复用，RX 端 MRM 解复用后接 PD。[p7]
  - Passage EVK50："THE FIRST 16λ BIDIRECTIONAL CPO LINK"：16λ 双向，每波 56G NRZ；800 Gbps/纤（400G+400G BiDi）；预 FEC BER <1E-9；1 km SMF；3 dB 信道损耗；<3 pJ/bit（PIC+激光器）；偏振不敏感；极端温度下稳定。图上 8 个 lane 的 BER 约 4.2E-13 至 5.8E-10 量级（数字较小，仅供参考）。[p10]
  - Guide 集成激光器：128+ 激光器/芯片；64λ+ 多色；0.1 FIT（可靠性与自愈）；300 mm CMOS SOI 晶圆；功率精度 0.25 dB；频率精度 3 GHz；对比传统方案每个激光器需许多分立器件。[p14]
- 提到的公司/客户/产品/标准：Lightmatter Passage M1000、EVK50、EVK100、Guide（激光器）；KP4 FEC；NRZ/PAM4/PAM6；未见客户名
- 与业界对比或记录声明：EVK50 自称"第一个 16λ 双向 CPO 链路" [p10]；"Slow × many has already demonstrated 1.6T"，"Fast × few has no roadmap past 400G" [p6]；M1000 "available today with >100 Tbps per package" [p6]
- 推荐配图页：p6（400G/800G/1.6T 单纤窄快 vs 宽慢方案对比表）；p5（112G–448G 能耗/距离/FEC 表）；p10（EVK50 演示，注意图片上下颠倒）

### 0920-pm-Su4-I-07-Credo-电互连路线.pdf
- 讲者/机构：讲者姓名未见（页末联系人 Mohsen Asad）/ Credo | 题目：未见完整题目页（页1 OCR 残缺，未查看）；主题为 wide-parallel（宽并行）光互连，页标题 "When Wide-Parallel Could Bring Benefit" | 类型：邀请报告（Workshop，"窄快还是宽慢"）
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO；次 3 Scale-out 224G/448G
- 核心主张：
  1. 算力随面积扩展，铜 I/O 随边缘扩展，只有光同时随两者扩展；Credo 自称是"唯一构建完整 wide-parallel 光学栈（SerDes、光引擎、光纤、封装）的厂商"。[p8]
  2. 带宽随通道数而不是单通道速率增长，二维扩展可把 GPU 域从 72 提升到 300+；简单调制加原生光源，能耗比交换式铜低 3–4 倍。[p8]
  3. 廉价冗余备用通道可无缝切换，光纤 break-out 可提高芯片连接基数。[p8]
- 关键数据：
  - ZeroFlap ALC（有源光缆）：Wide-Parallel Optics，覆盖 30 m，线缆体积最多减 75%，100M 小时 MTBF，"no link flap"；相比 AEC 极简 DSP 省 50% 功耗；CPO 带宽密度 >5 Tbps/mm（OCR 读数，未看原图）；"Pluggable is our first qualified product"，路线图指向 NPO/CPO。[p3]
  - 场景A 机架级中心交换机铜互连（fast narrow）：单次交换穿越约 14–17 pJ/bit，最大距离 1.5–2 m；分项：XPU 出口 SerDes 约 3.4、交换机入口 SerDes 约 3.4、交换结构+SHARP 约 2–3、交换机出口 SerDes 约 3.4、XPU 入口 SerDes 约 3.4 pJ/bit（假设 112G 级最佳节点）。[p6]
  - 场景B 平坦光 mesh（wide-parallel）：单次光穿越约 4 pJ/bit；分项（25G 宽并行）：XPU SerDes 至 OE 约 3.4、E/O（VCSEL）约 0.5、光纤约 0（无源）、O/E 约 0.5、OE 至电约 1.5 pJ/bit。结论：2 SerDes + 2 E/O，比交换式铜低 3–4 倍；铜只到约 2 m，光可到 50+ m 且无需 retimer。[p6]
  - 106G DSP SerDes：4 nm = 3.4 pJ/bit，3 nm = 3.4 pJ/bit（无改善）。[p6]
  - 拓扑动机（OCR 读数，未看原图）：Blackwell 用 MEMBAR 往返握手，Rubin 用 Counted Write Based Sync；OpenAI 半扁平两层 Clos（电）、AWS 准随机图 + 无源光 ShuffleBox、Google Virgo、Microsoft Fairwater、Meta Disaggregated Scheduled Fabric；TPU 8i Boardfly 36 组全连接、每 pod 最多 1152 芯片，3D Torus 的 hop 是时延税。[p4, p5]
- 提到的公司/客户/产品/标准：Credo ZeroFlap ALC、AEC；NVIDIA Blackwell/Rubin/SHARP；OpenAI、AWS、Google（Virgo、TPU 8i Boardfly）、Microsoft、Meta；VCSEL
- 与业界对比或记录声明：自称唯一完整 wide-parallel 光学栈厂商 [p8]；3–4 倍能效优势为其自估算模型，非实测 [p6]
- 推荐配图页：p6（铜交换 vs 平坦光 mesh 的 pJ/bit 分项对比）；p3（ZeroFlap ALC 产品特性）

### 0920-pm-Su4-I-08-XscapePhotonics-多波长路线.pdf
- 讲者/机构：讲者姓名未见 / Xscape Photonics | 题目：未见完整题目页（页1、2 未查看/内容不清）；主题为 AI 互连的多波长光源（Serial Cu vs Parallel Cu、Serial vs Parallel SM optics） | 类型：邀请报告（Workshop，"窄快还是宽慢"）
- 方向归属（主/次）：主 3 光源；次 4 Scale-up/in
- 核心主张：
  1. 从铜到光的转换用 (BW × Distance) 作为品质因数 FoM；2016 年数据中心转向单模光的 FoM 约 100 Gb/s·km。[p4]
  2. FoM 预测：Scale-up 在 12.8T 及以上、距离 10 m 以上时，单模光将成为主流实现。[p5]
  3. 当距离不再受限时，带宽与功耗决定串行 SM 光与并行 SM 光的选择；并行 SM 光可作为串行 SM 光的下一代，在等功耗下扩展带宽（slide 原话）。[p6]
- 关键数据：
  - Cu 到光的转换：Escape 互连（串行铜）较低带宽（X Tb/s）、1–10 m；封装内并行铜互连超短距 <25 mm；并行相对串行 "10–100x lower BW、20–400X longer reach、2–4X higher BW×Distance"。[p3]
  - 历史图：光纤系统容量×距离约每年翻倍；光取代电约 10 Mb/s·km；SM 转换约 85 Gb/s·km（Agrawal 数据）。[p4]
  - Scale-out（SM，2 km）：约 40G LR4 起，100G、400G、800G、1.6T×2 km 的 BW×Distance 逐代上升，1.6T×2 km 约 3000 Gb/s·km 量级（读图估计）；SM 转换线约 100 Gb/s·km；MM 光能力线约 6 Gb/s·km（Cu 到 MM 转换）。Scale-up：Cu <1 m（NVLink2 1.2T 至 NVLink5 7.2T）；MM 光 1–5 m（2.4T×5 m、7.2T×5 m）；SM 路线 10 m：12.8/14.4T（约2028）、25.6/28.8T、51.2/57.6T×10 m（约2032）。[p5]
  - 并行光 vs 串行光：Cu 到 SM 光在封装内互连"1–2 代之后"，Escape 互连"现在"（slide 原话）；2–5X Higher Power 标为并行的代价。[p6]
  - 光学选择表：Scale-out 1–4λ/纤，最多约 1M XPU，串行光；Scale-up 4–8λ/纤，144–576 GPU，CPO 于 GPU+NVSwitch，串并混合（第一代）、并行为下一代；Scale-in 64λ+/波导，GPU 与内存，并行光。[p10]
  - COMBX 可编程多波长激光器：波长数量与间隔可编程；同一平台服务串行与并行。Scale out AI training：20-nm CWDM4 栅格；Scale across 大规模训练：4.5-nm LR4 栅格；Scale up AI inference：1-nm CW-WDM 栅格（约 1280–1295 nm 区间可见密集谱线）。[p8]
- 提到的公司/客户/产品/标准：Xscape Photonics COMBX；NVLink/NVSwitch；CWDM4、LR4、CW-WDM；OIF booth #2126（OCR p11）；数据来源 Kirchain & Kimerling、Agrawal
- 与业界对比或记录声明：无 record 声明；FoM 图为预测线，非实测 [p5]
- 推荐配图页：p5（Scale-out/Scale-up 的 BW×Distance FoM 年表）；p8（COMBX 可编程多波长激光与三种栅格谱）；p10（Scale-out/up/in 光学选择卡片）

## 本批小结
1. "宽慢 vs 窄快"是本场主线：Lightmatter 与 Credo 都认为 112G/lane 之后的单通道提速在能耗、距离、时延上受限，主张靠通道数（波长数或并行光纤）扩展带宽；Xscape 则从 Cu 到光的 BW×Distance 品质因数推导出 Scale-up 迈向 SM 光，并把并行光视为串行光的下一代（Lightmatter p3/p15，Credo p8，Xscape p5/p6）。
2. 三家实现"宽"的路径不同：Lightmatter 用 MRM 微环 + DWDM/BiDi 与 3D 堆叠（EVK50：16λ×56G NRZ，<3 pJ/bit）；Credo 用并行 VCSEL/光纤阵列 + 极简 DSP（25G 宽并行）；Xscape 用可编程梳状多波长激光作为共用光源（Lightmatter p6/p10，Credo p6，Xscape p8）。
3. 能耗数据均为各家自估或平台数字：Credo 称光 mesh 约 4 pJ/bit 对交换铜约 14–17 pJ/bit，Lightmatter 称 56G NRZ 约 2 pJ/bit，口径不同（是否含 SerDes、光源），不宜直接比较（Credo p6，Lightmatter p5/p15）。
4. 多波长光源被视为关键使能器：Lightmatter Guide（128+ 激光器/芯片、64λ+、0.1 FIT）与 Xscape COMBX 均强调波长数量与频率精度可控，覆盖 Scale-out 1–4λ 到 Scale-in 64λ+（Lightmatter p14，Xscape p8/p10）。
5. Scale-up 的可靠性与拓扑需求：Credo 强调扁平低直径拓扑（MoE 全对全）与备用通道无缝切换，Xscape 给出 144–576 GPU 的 Scale-up 域规模，Credo 称可由 72 扩到 300+（Credo p4/p5/p8，Xscape p10）。
6. 本批部分讲稿题目页与讲者页未查看（预算内优先看数据页），页1/2 与 OCR 空白页只标注未见。
