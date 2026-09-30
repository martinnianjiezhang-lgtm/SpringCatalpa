---
title: "B45 · DAY3 · Tu1-D-光放大"
tags:
  - ECOC2026
  - DAY3
---

（本批含4个PDF；0922-Tu1-D3-Aston大学 属主分析师已做篇目，已跳过。以下共3篇。）

### 0922-Tu1-D1-长飞-无缝102nm扩展C+L集成光纤放大器.pdf
- 讲者/机构：长飞（YOFC，页脚 FCMT/YOFC 标识；讲者姓名看不清） | 题目：Seamless 102 nm extended C+L band integrated fibre amplifier（页面题目页OCR乱码，按文件名与结论页意译，英文原题未能确认） | 类型：学术论文
- 方向归属（主/次）：主 1（相干/海缆/长途/DCI，宽带光放大）/ 次 无
- 核心主张：
  - 自研 EBDF（掺铒）与 BDF（掺铋，MCVD 工艺）级联，实现 1524.1–1626.8 nm 共 102 nm 无缝 C+L 放大。
  - 结论页：Gain≥23 dB，NF≤7.8 dB，增益平坦度≤2.3 dB（加 GFF）。
  - 集成 C+L 放大器相比分立 C/L-EDFA 无需 mux/demux、架构简化、成本更低；期望业界建立 C+L 放大器标准。
- 关键数据：
  - EBDF：吸收 7.5 dB/m @1530 nm；增益>15 dB（1520–1595 nm），NF<6.9 dB，输入-30 dBm，980 nm 泵浦 500 mW [p3]
  - BDF：吸收 BAC-Si 0.8 dB/m @1400 nm、BAC-Ge 0.56 dB/m @1650 nm；增益>15 dB（1565–1680 nm），NF<6.2 dB，峰值 25.5 dB @1625 nm，1460 nm 泵浦 1800 mW，输入-30 dBm [p3]
  - 结构：第一级 EBDFA（16 m EBDF，980 nm 前向泵浦），第二级 BDFA（500 m BDF，1460 nm 双向泵浦） [p3]
  - 单波长（输入-30 dBm）：全 C+L 平均增益 34.9 dB，平均 NF 4.9 dB，增益均>22.5 dB [p4]
  - DWDM：125 波、100 GHz 间隔，-10 dBm/波输入：增益均匀性≥23.6 dB（最小增益），NF≤7 dB；0 dBm 输入：≥21.4 dB，饱和输出≥23.2 dB（原页面数值，与后页 21.5 dBm 略有差异，看不清是否同一条件） [p4]
  - 加GFF后表（125WDM，1524–1627 nm）：输入-10/-5/0/3 dBm 最小增益 23.688/22.20/19.418/16.93 dB；平均增益 25.13/23.21/20.52/17.94 dB；平均NF 5.13/5.13/4.78/4.81 dB；增益平坦度 2.29/1.76/2.2/1.42 dB [p5]
  - 对比表：C-EDFA 1530–1565 nm，饱和输出 18–25 dBm，NF 4.5–5.5 dB；L-EDFA 1565–1625 nm，15–22 dBm，NF 5.0–6.0 dB；C+L EBDFA 1524.1–1626.8 nm，21.5 dBm，NF<7.8 dB [p6]
  - 不足：输出功率相对较低、噪声偏高，后续优化泵浦方案 [p6]
- 提到的公司/客户/产品/标准：ITU-T G.663（C、L 波段划分）；BDF 材料参考 S.V. Firstov；Bi 掺杂宽带发光 1.1–1.8 μm
- 与业界对比或记录声明（SOTA/首次/record）：未声称 record；称"成功自研 EBDF 和 BDF" [p5]；与分立 C/L EDFA 对比见 [p6]
- 推荐配图页：p5（增益/NF 曲线 + 含 GFF 的 EBDF+BDF 两级结构 + 各输入功率性能表）

### 0922-Tu1-D2-Chalmers-脉冲泵浦的亚3dB噪声系数片上相敏预放.pdf
- 讲者/机构：Junda Chen, Rasmus Larsson, Peter A. Andrekson / Chalmers University of Technology | 题目：High-Gain Sub-3 dB Noise Figure Chip-Based Phase Sensitive Preamplifier with Pulsed Pumping | 类型：学术论文
- 方向归属（主/次）：主 1（高灵敏度接收/放大，面向深空光通信）/ 次 6（无直接对应，仅作放大器物理）
- 核心主张：
  - Si3N4 波导上的片上相敏放大器（PSA）在脉冲泵浦下实现 36.8 dB 片上增益，可不接 EDFA 直接独立接收。
  - 光纤到光纤 NF 2.6 dB，低于任何 PIA 接收机的 3 dB 量子极限；片上 NF 约 0.5 dB，与理论相差 0.3 dB 内。
  - 2 Gb/s QPSK 在 BER 10^-3 时灵敏度-59 dBm（结论页标注，指数看不太清）；另做二阶 PLL 时钟恢复，抖动约 200 fs（"beyond paper"）。
- 关键数据：
  - 动机：深空通信无中继，容量受接收灵敏度和放大器NF限制；页面引用火星 1.4 Gb/s @-70 dBm（图中，看不清细节） [p1]
  - 理论：PIA NF≥3 dB，PSA 理想 NF=0 dB；增益低时后级 EDFA（NF 4.5 dB）噪声主导，目标 PSA 增益≥26 dB 可使级联 NF 与片上 NF 相差<0.1 dB [p3]
  - 前人工作：首个片上 CW PSA（Si3N4）9.5 dB 片上增益（4.5 dB 黑盒），1.2 dB 片上 NF [p3]
  - 波导：长 1.7 m，截面 1950×690 nm，非线性系数 γ 0.86 W^-1 m^-1，色散 β2 -28 ps²/km，信号 1541.72 nm、闲频 1566.29 nm；损耗预算总计 8.2 dB，输出耦合损耗约 3.6 dB（输入耦合约 2.1 dB） [p4]
  - 峰值泵浦功率约 40.1 dBm → PSA 增益 36.8 dB [p5]
  - 级联EDFA接收：黑盒NF 2.6 dB（PSA，B2B）、3.0 dB（PSA）、5.4 dB（PIA）、4.9 dB（商用EDFA）；片上NF≈0.5 dB（去除2.1 dB输入耦合损耗）；收发分离激光器带来 0.4 dB 代价 [p5]
  - 独立接收（无EDFA）：黑盒NF 3.4 dB（PSA，B2B）、3.8 dB（PSA）、5.8 dB（PIA）、4.9 dB（EDFA）；比级联差约0.8 dB（增益受限而非NF受限）；ROP 低至-68 dBm 需约 50 dB 增益 [p5]
  - PLL：抖动 128 ps → 6 ps → 200 fs（100 Hz–5 MHz） [p6]
- 提到的公司/客户/产品/标准：PPM 与相干检测对比；参考 Zhao/Gaeta 等 ~300 nm 宽带片上放大器（Nature 2025，文献引用）；商用 EDFA 作对照
- 与业界对比或记录声明（SOTA/首次/record）：NF 2.6 dB 低于 PIA 3 dB 量子极限 [p5]；未使用 "record" 字样
- 推荐配图页：p5（级联 EDFA 与独立接收两组 BER 曲线及 NF 数据）

### 0922-Tu1-D4-NTT-增益平坦滤波器弃光的能量收集.pdf
- 讲者/机构：Masaki Wada, Taiji Sakamoto, Takashi Matsui, Kazuhide Nakajima / NTT Access Network Service Systems Laboratories | 题目：Energy Harvesting over Optical Communication Networks Using Discarded Light from a Gain-Flattening Filter | 类型：学术论文
- 方向归属（主/次）：主 1（海缆/长途，多芯 EDFA）/ 次 6（海缆传感/SMART cable 供电）
- 核心主张：
  - 提出 APE-GFF（Aggregated Power-Extraction GFF）：四芯 EDFA 中被 GFF 剔除的光汇聚到一根多模光纤，用光伏转换器（PPC）转成电能，同时保持通信信号。
  - 单个放大器回收功率超过 45 mW，且不劣化增益和 NF。
  - 跨多根光纤累加可达瓦级，可为海缆内低功耗传感器供电。
- 关键数据：
  - 实用区间 |增益倾斜|<0.05 dB/nm 内，单个四芯 EDFA 约可回收 30 mW，无明显 PCE 下降；OE 转换效率 40%；增益倾斜定义 λ1=1530 nm、λ2=1565 nm；输出功率（min）8 dBm [p5]
  - 回收功率随目标信号输出上升（22 dBm 信号输出与较低输出对比，图为每芯 dBm，具体数值看不清） [p6]
  - 薄膜GFF入射角在2°内附加损耗变化约0.2 dB；4CF 芯距 40 μm、MFD 18.5 μm 与 MMF NA 0.2；等倍耦合需 MMF 纤芯≥70 μm，选用 105 μm MMF [p6–p7]
  - 实验：APE-GFF 提取效率 93%；四芯 EDF：芯距 40.3 μm，包层 125 μm，MFD 5.5 μm @1550 nm，截止 1.3 μm，Er3+ 浓度 501 wtppm；4×0.98 μm 泵浦 [p8]
  - 增益波纹从 2.9 dB 降到 1.4 dB，NF 无观察到代价；适当均衡预计可得约 45 mW（1530–1565 nm，增益约 15–20 dB 区间） [p8]
  - 用回收光功率让温湿度传感系统实验室连续工作 10 分钟 [p9]
  - 海缆光纤对数增长至最多 24 对（新 Meta-led 缆 2024） [p10]；汇聚估计：约 22 根光纤对应约 1000 mW（虚线标注），约 48 根接近 2 W [p10]
- 提到的公司/客户/产品/标准：Google（多芯海缆）、NTT 192 芯海缆系统、NEC 海缆技术趋势报告、SMART cable、EHoF 先前概念（Gunawan et al., JLT 2024）
- 与业界对比或记录声明（SOTA/首次/record）：未声称 record；对比先前 EDFA-FBG 的 EHoF 概念 [p2]
- 推荐配图页：p5（APE-GFF 结构：4CF 输入、GFF、MMF 提取到 PPC、三个端口光谱）；补充 p10（光纤数量与可回收电功率关系）

## 本批小结
- 光放大向"更宽、更集成"演进：长飞用 EBDF+BDF 级联做到 102 nm 无缝 C+L（Gain≥23 dB，NF≤7.8 dB），与分立 C/L 相比取消 mux/demux，代价是 NF 与输出功率略逊，并呼吁制定 C+L 放大器标准（D1）。
- 低噪声路径出现"物理极限"取向：Chalmers 片上 PSA 以 36.8 dB 增益和 2.6 dB 光纤到光纤 NF 突破 PIA 3 dB 极限，但需约 40 dBm 峰值脉冲泵浦，定位在深空等无 EDFA/极低接收功率场景（D2）。
- 长飞与 Chalmers 分别代表"实用宽带 NF≈5–7 dB"与"极致低噪 NF<3 dB"两端，共同点是都以放大器 NF 作为系统灵敏度瓶颈（D1、D2）。
- 海缆放大器开始考虑"废光再利用"：NTT 借四芯 EDFA 把 GFF 弃光转为电能，单放大器约 30–45 mW，多光纤对累加至瓦级，服务 SMART cable 传感；与多芯/多光纤对增长趋势（最多 24 对）耦合（D4）。
- 三篇均为实验室级演示，均无现网数据；NTT 的传感器供电仅验证 10 分钟（D4），Chalmers 需额外 PLL 处理超低功率下的时钟恢复（D2）。
