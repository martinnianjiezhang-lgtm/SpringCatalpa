---
title: "B35 · DAY2 · _合集待拆"
tags:
  - ECOC2026
  - DAY2
---

## 合集说明
0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf（47页）按讲者切分：A1 iPronics p1；A2 香港理工/YOFC p2–14；A3 KDDI p15–26；A4 TU/e p27–35；A5 阿里云 p36–47。

### 0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf（iPronics 第1页，Mo3-A1）
- 指引：iPronics（Photonics to scale AI datacenters，OCS 用于 scale-up 扩展/scale-out 叶脊层）已由另一批单独处理，此处不展开。

### 0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf（第2–14页，Mo3-A2）
- 讲者/机构：Jingchuan Wang（香港理工大学 光子研究所；合作 YOFC 长飞光纤光缆全国重点实验室，武汉） | 题目：Demonstration of Ultra-high Link Budget, Low Cost/Latency Distributed AI Scale-across Network Enabled by C-band 3.2-Tb/s/lane IM-DD Transmission over 20-km AR-HCF（原题如印，"3.2 Tb/s/lane"字样按幻灯片原文；正文实验为32波×50 GBaud PAM4，总线速3.2 Tb/s） | 类型：学术论文
- 方向归属（主/次）：主 2 Scale-across（空芯光纤 HCF 用于跨园区）；次 1 高波特率/IM-DD 对比相干
- 核心主张：
  1. HCF 色散低、非线性低、时延低，与分布式 AI 训练（高聚合带宽、低且可预测时延、近零丢包、低成本低功耗）需求匹配，可让低成本 IM-DD 在 >1 km 的 scale-across 场景可用 [p7, p8]。
  2. HCF 中无 SBS/非线性限制，入纤功率可提到 31 dBm 而 BER 几乎不劣化，从而换取超大链路预算 [p12, p13, p14]。
  3. 32 波 C 波段 IM-DD 在 20 km 支撑管 HCF 上给出约 50 dB 的被测信道（CUT）预算，总毛速率 3.2 Tb/s [p14]。
- 关键数据：
  - SSMF vs HCF（幻灯片表，SSMF 引自 ITU-T G.652.D）：C 波段色散 16.7 vs ≈3 ps/nm/km；非线性系数 1.3 /W/km vs 约低 30 dB；传播速度 2.0419×10^8 m/s vs 约快 1.5× [p7]
  - 支撑管 HCF（YOFC）损耗 < 0.1 dB/km [p7]
  - 实验：20 km 支撑管 HCF 或 G.652D SSMF；120 GSa/s Keysight M8194A DAC；70 GHz TFLN MZM；Coherent Waveshaper 4000A WSS；70 GHz InGaAs PIN + 固定增益 EDFA（等效 APD替代，PIN 最佳输入 0–5 dBm）；256 GSa/s Keysight UXR0804A ADC；32 波、50 GHz 栅格 [p9]
  - 80 GBaud PAM4、20 km：入纤 5 dBm 时首个衰落陷波 SSMF 13.5 GHz、HCF 31.5 GHz；HCF 入纤升至 31 dBm 陷波位置基本不变；SSMF 用 ITLA 在 17 dBm 时陷波抖动（约 11–17 GHz 范围），窄线宽激光使陷波稳定在约 14.2 GHz [p11]
  - SBS：SSMF 后向散射功率在入纤约 11 dBm 以上快速上升，接收光功率饱和（约 1–2 dBm）；HCF 后向散射与接收功率在测试范围（至 31 dBm）线性增长 [p12]
  - 单波 50 GBaud PAM4：LP = 5 dBm 时 HCF 在 15% O-FEC 门限的灵敏度约 −19 dBm，SSMF 曲线始终高于门限（色散衰落）；ROP = −15 dBm 时 HCF 直至 31 dBm 入纤 BER 几乎无劣化（约 10^-3 量级）；SSMF 最佳入纤约 9 dBm [p13]
  - 32×50 GBaud PAM4：等功率加载 5–13 dBm/波，HCF 与单波接近，SSMF 最佳约 5 dBm（FWM、XPM）；混合加载：CUT = 31 dBm，其余31波各 13 dBm，HCF BER 随 CUT 功率变化很小；−19 dBm 接收功率达到 O-FEC 门限，对应 50 dB CUT 预算，总毛速率 3.2 Tb/s；讲者注明该预算是特定混合加载条件下的结果，"可推断"全部同功率时应相同 [p14]
- 提到的公司/客户/产品/标准：YOFC 支撑管 HCF；ITU-T G.652.D；Keysight M8194A/UXR0804A；Coherent Waveshaper 4000A；TFLN MZM；OFC 2026 Workshop "How Far is Too Far?"（Arista、Ciena、Microsoft 演讲回顾）[p4–p6]
- 与业界对比或记录声明（SOTA/首次/record）：未见"record/首次"字样；对比对象为同条件 SSMF 与 OB2B；"50 dB CUT budget"为讲者强调的结果 [p14]
- 推荐配图页：p7（SSMF/HCF 参数对比表+HCF截面）；p12（SBS：后向散射与接收功率随入纤功率曲线）；p14（32波混合加载 BER 与 50 dB 预算）

### 0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf（KDDI 第15–26页，Mo3-A3）
- 指引：KDDI Research 的 "Is DSP-Free Pluggable Optical Module Suitable for Optical Circuit Switching?"（LPO+OCS，72 小时 LLM 预训练验证）已由另一批单独处理，此处不展开。

### 0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf（第27–35页，Mo3-A4）
- 讲者/机构：讲者名未在所看页出现；埃因霍温理工大学 TU/e（电光通信组） | 题目：Dynamic RU-DU Reconfiguration in 6G Access Networks Using Fast Controlled Photonic Switches with 400G ZR+ Optics | 类型：学术论文
- 方向归属（主/次）：主 5 固定与无线接入（6G 前传/RAN）；次 2 ZR/ZR+
- 核心主张：
  1. 提出扇区式相干前传架构，RU 到 DU 映射可动态重配，光/二层/三层协同重配 [p30, p35]。
  2. 用 FPGA 控制的 SOA 光子交换节点 + 光监控信道（OSC）实现快速控制 [p31, p32]。
  3. 400G ZR+ 相干信号通过四个级联光子节点可用 [p35]。
- 关键数据：
  - 结论页：端到端重配时延约 206 μs；光功率代价 < 3.8 dB（pre-FEC 10^-2 BER）；四个级联光子节点 [p35]
  - 功率代价：经 1 个节点 0.7 dB，经 4 个节点 3.8 dB；OSNR 降至 31.2 dB [p34]
  - 实验：两路 400G ZR+ RU 信号，RU1 1561.42 nm、RU2 1560.61 nm，各约 −7 dBm；OSC 为 10 GbE，1550.12 nm，约 0 dBm；SOA 偏置电流 40–100 mA；FPGA HTG-830；流量发生/分析 VIAVI ONE-800；DU 侧包交换机 Edgecore DCS240；环形网络（OCR，数字未逐项核对图）[p33]
- 提到的公司/客户/产品/标准：400G ZR+；CMIS（可插拔控制）；IMT-2030；VIAVI；Edgecore；P4 卸载、SDN 控制器、FPGA 监督控制（作为已有方案对比）[p29, p32]
- 与业界对比或记录声明（SOTA/首次/record）：未见 record/首次 字样；动机页称挑战是快速、动态的多层网络重配 [p29]
- 推荐配图页：p31（SOA 光子交换节点结构与 OSC）；p34（重配时延、级联节点 BER-ROP 曲线）

### 0921-合集待拆-全场-A1厅下午上半场连拍-Mo3-A.pdf（第36–47页，Mo3-A5）
- 讲者/机构：Qin Chen / 阿里云（Alibaba Cloud, Alibaba Group），2026年9月21日 | 题目：Large-Scale Deployment of LPO in AI Clusters | 类型：产业发布（学术会场邀请/现网数据）
- 方向归属（主/次）：主 3 Scale-out（LPO 400G DR4 现网）；次 4 Scale-up（LPO→NPO→CPO 路线）
- 核心主张：
  1. 阿里 scale-out 现用 FRO、未来 FRO 与 LPO 并存；scale-up 现用铜、未来线性光学 LPO→NPO→CPO [p37]。
  2. 现网 13,234 只 400G DR4 LPO、25.8M 器件小时数据表明 LPO 在功耗、时延、可靠性、成本与部署效率上具优势，日链路抖动率比 FRO 低 58% [p42, p46, p47]。
  3. 大规模 LPO 部署为后续 NPO/CPO 线性驱动技术奠定基础；在受控封闭光网络（如 scale-up）中最成熟 [p47]。
- 关键数据：
  - 部署环境：ToR/Aggregation/Core 的 scale-out 网络；Broadcom Tomahawk 5 51.2T，4U 机箱，128×400G QSFP112；通用 PHY-less 交换机，非为 LPO 定制；400G QSFP112 DR4 LPO 基于硅光，来自3家模块商，驱动/TIA/PIC 来自不同芯片商 [p38]
  - 链路：通道插损最大接近 16 dB（CEI-112G-VSR 极限）；线卡 TX/RX 中位数 13/12.7 dB，MAC 板 TX/RX 11.4/10.6 dB；MPO 跳线最长 250 m（中位 133 m）；CTLE 固定 0 dB [p39]
  - 实验室：光环回，106.25 Gb/s PAM4，PRBS31Q；BER 中位数 线卡 2.0e-10、MAC 板 2.7e-11，均比 KP4 FEC 门限（2.4×10^-4）低 2 个数量级以上；TDECQ 与 BER 相关性弱，TDECQ > 3.5 dB（400GBASE-DR4 限值）的端口 BER 仍很好 [p40]
  - 互通（接收灵敏度 OMA 中位数）：L2L −9.4，L2R −6.7，R2L −10.0，R2R −9.4 dB（L=LPO，R=FRO）；L2R 显著劣化，部分 FRO 接收机不满足 DR4 灵敏度（−3.9 dBm OMA）；策略：纯 LPO 对 LPO 部署 [p41]
  - 现网：13,234 只 LPO，累计 25.8M 器件小时；对照组为同3家厂商同工艺 FRO [p42]
  - 功耗中位数 LPO 4.2 W vs FRO 8.1 W（降 48%）；壳温中位数 35.1 vs 45.5 °C（低 10.4 °C）[p43]
  - 模块 TX+RX 时延：LPO < 5 ns；三家主流 DSP 厂商 FRO > 100 ns（柱图约 100–160 ns）[p44]
  - 稳定性：接收 SNR 波动 < 0.3 dB（观察约 80 天）；累计 KP4 FEC 非零 bin 最大值低于 10 [p45，OCR，图未细看]
  - 可靠性表：LPO 13,234 只 2.58E+07 h，RMA 7 例，MTB RMA 420 年；FRO 220,352 只 8.35E+08 h，RMA 209 例，456 年；链路抖动 LPO 178 次、MTB 17 年、日抖动率 0.017%；FRO 13,746 次、7 年、0.040%（LPO 低 58%）；7 只 LPO RMA 失效模式为污染与 ESD [p46]
- 提到的公司/客户/产品/标准：Broadcom Tomahawk 5；QSFP112 DR4；400GBASE-DR4；CEI-112G-VSR；KP4 FEC；TDECQ；3家未具名模块商与 3家 DSP 厂商
- 与业界对比或记录声明（SOTA/首次/record）：未见 record 字样；给出规模化现网 LPO 与 FRO 对照统计（同厂商同工艺）[p42, p46]。讲者提示 LPO MTB RMA（420 年）与 FRO（456 年）"相当"，但 FRO 器件数与器件小时量大得多 [p46]
- 推荐配图页：p46（可靠性统计表）；p43（功耗/壳温箱线图）；p41（互通矩阵 L2R 劣化）；p44（时延对比柱图）

## 本批小结
1. 低成本 IM-DD 正通过换介质/换架构向更长距离和更大预算延伸：PolyU/YOFC 用 HCF 在 20 km 上跑 32×50 GBaud PAM4，入纤 31 dBm 无非线性/SBS 劣化，获 50 dB CUT 预算（A2）。
2. LPO 从实验室走向现网规模验证：阿里 13,234 只 400G DR4 LPO、25.8M 器件小时，功耗降 48%、时延 < 5 ns、日链路抖动低 58%（A5）；但 L2R 互通劣化表明需 LPO 对 LPO 配对，属封闭光网络思路（A5）。
3. LPO 被视为通往 NPO/CPO 的台阶，且 scale-up 时延约束（对比 FRO > 100 ns）是主要驱动力（A5）；与同场 KDDI、iPronics 的 OCS+线性光学方向（另批处理）相呼应。
4. 6G 接入侧出现"相干 ZR+ + 快速光交换"融合：TU/e 用 SOA 交换与 OSC，206 μs 完成光/二/三层重配，4 节点级联代价 3.8 dB（A4），说明 ZR+ 的应用正从 DCI 延伸到前传。
5. 会场共同主线是 AI 数据中心对功耗、时延与丢包的约束（A2 的分布式训练需求页、A5 的 scale-up 时延约束）。
