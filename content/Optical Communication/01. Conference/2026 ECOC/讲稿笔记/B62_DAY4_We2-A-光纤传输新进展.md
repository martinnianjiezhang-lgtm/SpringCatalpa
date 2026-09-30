---
title: "B62 · DAY4 · We2-A-光纤传输新进展"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We2-A1-BT-光纤通信六十年与未来.pdf
- 讲者/机构：Russell Davey（BT Fellow, Principal Network Architect）/ BT | 题目：Optical fibre communications & network innovations: the past 60 years and what the future holds | 类型：邀请报告
- 方向归属（主/次）：主 1（相干/长途历史回顾）；次 5（PON/FTTP 历史）
- 核心主张：
  1. 回顾 BT/邮政研究院对光纤通信的贡献：1966 Kao 提出、1970 Corning 低损光纤、单模化、相干、EDFA、WDM/波长交换、PON、DSL、吹纤。
  2. BT 主张最早现场部署相干（1988）并推动单模光纤（1980–83）及可管理波长交换网络（MWTN，1995 瑞典现场演示，称 world-first）。
  3. 展望 2030+：随速率提升 C 波段频谱已基本用满（Shannon 极限），>800 Gbit/s 需新放大器扩谱、空芯/多芯光纤，或直接并行多纤；并提及量子网络（结尾页仅列问题，无结论数字）。
- 关键数据：
  - Openreach FTTP 覆盖 23.4 百万户，2026 年底建至 25 百万户，网络投资 £15 billion，已覆盖户中 40% 已接入（截至 2026-06-30，OCR，未看图）[p2]
  - 约 512,000 个（~60%）移动基站直连光纤（OCR）[p3]
  - Kao 1966 设想损耗约 20 dB/km；Corning 1970 样品损耗 15 dB/km（送 Post Office 测得），IEEE 铭牌写 17 dB/km（OCR）[p5][p6][p7]
  - 1977 首次 Post Office 光纤试验：渐变折射率多模，140 Mbit/s 传 5.75 km；8 Mbit/s 传 13 km 无中继；~5 dB/km @ ~840 nm（OCR）[p8]
  - 1980 BT 37 km 无中继 140 Mbit/s 单模；1982 现场试验 140/650 Mbit/s 传 37.5 km 无中继，140 Mbit/s 传 62 km 无中继，均 1300 nm（OCR）[p9]
  - 1988 相干现场部署：565 Mbit/s，光学距离 176 km（图示 Bedford–St Neots–Cambridge，20.6 km + 33.7 km 段，看图）[p13]
  - EDFA：Southampton 1987 首报，BT Whitley 1988 首次激光二极管泵浦，1990 商用；现网总距离 >1000 km，约每 80 km 一个放大器，1530–1565 nm，最低损耗约 0.2 dB/km（看图）[p13]
  - 2030+ 页：ITU 50 GHz 栅格 vs 灵活栅格（37.5/50/75/100 GHz），速率 10G–800G/波；单模光纤 D/E/S/C/L/U 六个谱带衰减曲线，1200–1700 nm，最低约 0.2 dB/km（看图）[p18]
- 提到的公司/客户/产品/标准：BT、Openreach、Corning、STL、STC、GEC、Ericsson、BT&D（与 DuPont 合资）、Plessey、ITU-T/ATIS/ETSI/BBF（DSL 标准：G.993.1/993.2/992.3/992.5/993.5/9701 等，OCR）、GPON、XGS-PON（同纤不同波长共存）、TPON
- 与业界对比或记录声明（SOTA/首次/record）：BT 称 1988 世界首次现场部署相干 [p13]；1982 世界首次单模光纤现场试验 [p9]；1995 MWTN 现场演示 world-first [p15]；1991 Bishop's Stortford TPON 试验 [p16]；均为讲者历史自述
- 推荐配图页：p13（1988 相干现场链路示意 + EDFA 结构图）；p18（2030+ 频谱/新型光纤展望）

### 0923-We2-A2-NTT-长跨高容量混合信号传输.pdf
- 讲者/机构：Toshiya Matsuda 等 / NTT Network Service Systems Labs. | 题目：Mixed Signal Transmission for Long-Haul High-Capacity Optical Paths and Low Latency Optical Paths Using DSF Transmission Line and Inter-Band Wavelength Conversion Technology | 类型：学术论文
- 方向归属（主/次）：主 2（DCI/短距 PAM4 与长距混合，APN）；次 1（PPLN 波长转换、多波段）
- 核心主张：
  1. APN 中同时承载：低时延短距路径（DWDM PAM4 可插拔在 DSF 中 C 波段传输以缓解色散）与高容量长距路径（相干）的混合信号传输。
  2. PAM4 对 200G DP-16QAM 的 XPM 影响与 16QAM 相当，信号功率 ≤ -4 dBm/ch 时无非线性影响。
  3. 用 PPLN 做带间波长转换（转到 L 波段），可抑制 DSF 中 PAM4 对 DP-16QAM 的非线性，结果与无 PAM4 的 SMF 传输相当。
- 关键数据：
  - 典型模块对比：200G 16QAM DCO（CFP2）功耗 17 W、所需 OSNR 21.5 dB、Rx 灵敏度 -22 dBm、CD 容限 ±16,000 ps/nm；2x50G PAM4（QSFP28）4.5 W、26.5 dB、-13 dBm/ch、CD 容限 ±100 ps/nm；PAM4 在 SMF C 波段仅 6 km，在 DSF C 波段 80 km（加中继放大器 >80 km）[p3]
  - 数值仿真：Case1/3（C 波段 16QAM 受 C 波段 PAM4/16QAM 背景）EVM 在 -6 至 4 dBm/ch 由约 10 升至约 17.5 %（图纵轴 EVM，约 17–18）；Case2（L 波段 16QAM）在 4 dBm/ch 仅约 11 [p5]
  - 实验：225 km、3 跨（75 km SMF + 75 km DSF + 75 km SMF），200G DP-16QAM 被测信号，背景 2x50G PAM4 或 2x200G DP-16QAM；波长 1549.32/1552.52/1593.80 nm 配置，零色散约 1550.72 nm [p5]
  - 相对 Q 值（参考 SMF 全程无 PAM4 在 1 dBm）：无 PPLN 时功率升至 6 dBm/ch 降至约 -6.7 dB；有 PPLN 在约 0 至 2 dBm/ch 最佳，接近 0 dB，6 dBm 时约 -1.8 dB [p6]
  - PAM4 在 75 km DSF：-8 至 4 dBm/ch BER < 1e-12 无差错；-10 dBm 时相对 Q 约 -3.5 dB [p6]
- 提到的公司/客户/产品/标准：NTT APN、CFP2 DCO、QSFP28 PAM4、DSF、PPLN、WSS、EDFA、CBRE 东京数据中心预测
- 与业界对比或记录声明（SOTA/首次/record）：未声明 SOTA；称首次对 PAM4 与高速信号多波段混传非线性做量化评估（原文"没有充分定量评估"作动机）[p4]
- 推荐配图页：p5（数值 EVM 曲线 + 225 km 实验装置与谱图）；p3（PAM4 vs 相干模块对比表与架构图）

### 0923-We2-A3-KDDI-数字子载波复用P2MP现网试验.pdf
- 讲者/机构：Chenxiao Zhang 等 / KDDI Research | 题目：Field Trial of Digital Subcarrier Multiplexing-based P2MP over 170 km for Distributed Data Center Network Interconnect | 类型：学术论文
- 方向归属（主/次）：主 2（Scale-across / 分布式 DC 互联）；次 1（DSCM、相干）
- 核心主张：
  1. 在约 170 km 商用部署都市光纤上完成 DSCM P2MP 互联现网验证，面向分布式数据中心（前端 scale-out 与后端 scale-across）。
  2. 与传统 P2P 相干信道共传不受影响，72 小时无丢包，支持 0–80 km 叶节点距离差与在网重新分组。
  3. DSCM-P2MP 是未来城域分布式 DCI 的实用且灵活方案。
- 关键数据：
  - 现场：~170 km、5 段光纤（Tokyo DC1/DC2，~40/30/10/50 km 等段），商用 ROADM 与在线放大器；2 hub + 4 leaf，两个 P2MP 组；2x100 Gb/s 16QAM P2MP 与传统 DP-QPSK P2P 共传；约 196 THz 4 路商用实时流量 [p4]
  - 15 个 C 波段测试点（约 191–196 THz），接收 OSNR 均高于 17 dB 阈值，图中约 20–25 dB，无明显波长依赖 [p4]
  - 72 h Layer-2：无丢包，速率无波动（Hub 约 200 Gbps，Leaf 各约 100 Gbps）；相邻 P2P 通道 pre-FEC BER 均低于 1e-6（图中约 1e-10 至 1e-7 量级）[p5]
  - 叶节点差距 ΔL = 0/20/40/60/80 km 均 link up，10 分钟 L2 测试无误码 [p5]
  - 在网重新分组：前 <Hub1: Leaf1,Leaf2> & <Hub2: Leaf3,Leaf4>，后 <Hub1: Leaf1,Leaf3>；每 leaf 16 GHz、100 Gbps；10 分钟 L2 无误码 [p6]
- 提到的公司/客户/产品/标准：KDDI、NICT 委托研究（JPJ012368C09001）、DSCM P2MP 可插拔收发器、ROADM
- 与业界对比或记录声明（SOTA/首次/record）：未声明 record；强调从架构演示到运营验证 [p3]
- 推荐配图页：p4（现网拓扑 + 15 波长 OSNR 曲线）；p6（在网重新分组频谱）

## 本批小结
1. 分布式数据中心互联成为相干/DCI 的共同落点：KDDI 的 DSCM P2MP 明确面向 scale-across（后端）与 scale-out（前端），NTT 则因东京都市圈电力与空间限制，把 DC 建到 50 km 内郊区，重点是低功耗低时延短距 DCI（A2、A3）。
2. 短距 DCI 出现"非相干 PAM4 + 相干"混合路线：NTT 给出 4.5 W QSFP28 PAM4 与 17 W CFP2 相干 DCO 对比，PAM4 的 CD 容限仅 ±100 ps/nm，需 DSF 才能到 80 km；混传带来的 XPM 用 PPLN 带间波长转换解决（A2）。
3. KDDI 的验证重点从"单点性能"转向运营指标：15 波长 OSNR、72 h 无丢包、0–80 km 叶节点差距、在网重新分组，可视为 P2MP 走向商用的必要证据（A3）。
4. 频谱与新型光纤仍是长期议题：BT 指出 C 波段已接近用满，>800G 需扩谱放大器、空芯/多芯或并行光纤；NTT 的 L 波段转换与 DSF 是当下可行的另一条扩展思路（A1、A2）。
5. BT 的历史回顾提供了技术演进节奏参考：单模化、相干、EDFA、波长交换、PON 均经历从实验室到商用的十年以上周期，其中相干 1988 现场演示到今日大规模使用（A1）。
