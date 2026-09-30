---
title: "B38 · DAY2 · _合集待拆"
tags:
  - ECOC2026
  - DAY2
---

## 说明：Mo5-F 场连拍合集切分（共 100 页，其中 p24、p84 为重复页）

| 页码 | 讲者 | 处理 |
|---|---|---|
| p1–18 | 华南理工 F1（LSP-NLC 子带扰动非线性补偿） | 另一批已处理，此处仅指引 |
| p19–37 | UCL F2（超网络 DSP） | 本批详写 |
| p38–61 | UBC/Nokia Bell Labs F3（Seq-NPAS） | 本批详写 |
| p62–76 | Aston/Ericsson F4（DPD-KAN，A-RoF） | 本批详写 |
| p77–85 | NTT F5（168GBd PCS-324QAM） | 另一批已处理，仅指引 |
| p86–100 | 国立清华 F6（PCG-VE 稀疏 Volterra） | 另一批已处理，仅指引 |

指引：F1 华南理工、F5 NTT、F6 国立清华请见其他批次单独笔记，本文件不重复。

### 0921-合集待拆-全场-Mo5-F全场连拍.pdf（第19–37页）
- 讲者/机构：Samuel Lennard, Fabio A. Barbosa, Filipe M. Ferreira / UCL Optical Networks Group（页脚场次号 Mo5-F2） | 题目：A Realistic Implementation of Fast Convergence Hypernetwork-based DSP for Coherent Data Centre Links | 类型：学术论文
- 方向归属（主/次）：主 1（相干 oDSP）；次 2（Scale-across，数据中心园区相干-lite / 相干 PON 场景）
- 核心主张：
  1. 数据中心园区和接入（相干-lite、Coherent PON）带来突发/光交换场景，DSP 重新捕获（reacquisition）时延成为重要设计考量 [p37]
  2. 用超网络（hypernetwork）生成自适应滤波器，以确定性前馈过程取代 LMS/RLS 迭代收敛，无需 CDC、无需预自适应滤波 CFC，也无需信道先验信息 [p30, p31]
  3. 复杂度还有进一步下降空间（剪枝/架构简化）[p37]
- 关键数据：
  - 引用背景：Marvell Aquila coherent-lite，O 波段，1.6 Tb/s 模块，2–20 km；OFC 2026 与 Lumentum 做过光交换演示（幻灯片引用，非本工作）[p22]
  - 引用背景：CableLabs CPON，每波长 100 Gb/s 可用容量 [p22]
  - DSP 设置：64 符号导频序列；RLS 与 full DA-CFC 用于常规对照；超网络路径为前馈 [p31]
  - 实验：单跨段 SSMF，C 波段满载（发端 ECL，λ 范围 1535–1565 nm），DP-IQ 调制，DAC 驱动 16QAM，接收端加噪声加载抑制发端噪声限制，相干接收机 110 GHz；光纤长度 6 km / 12.3 km / 25 km / 50 km 可切换 [p32]
  - 波长泛化：C 波段扫描（约 1540–1565 nm），6 km 与 25 km 下 SNR 约 20–23 dB，超网络 DSP 与常规 DA-DSP 接近（图中略低）[p33]
  - 距离泛化：约 60 km 以内与常规 DSP 相近（SNR 约 20 dB 量级）；约 60 km 后开始下降，约 95 km 处超网络约 8 dB，对照约 13–14 dB；讲者归因于 CD 引起的信道冲激响应长度 [p34]
  - 发射功率泛化：在线性区（约 -10 至 +10 dBm 量级）与常规性能一致，峰值 SNR 约 20 dB [p35]
  - 复杂度：超网络原始约 4M 实数乘法，剪枝+聚类后约 300k RM（与 RLS 相当），进一步剪枝和架构简化后目标约 25k RM（与 LMS 相当但收敛时间固定，属于"本文之外"）；FPGA 实现收敛 75 ns [p36]
  - OCR 索引（未经图片核对）：常规迭代算法对残余 CD 敏感，LMS 尤其差，RLS/LS 更稳健但难以硬件实现 [p27]
- 提到的公司/客户/产品/标准：Marvell Aquila、Marvell/Lumentum（OFC 2026 光交换演示）、CableLabs CPON 规范；J. Zhou et al. arXiv:2410.10080；资助：UKRI/EPSRC（TRANSNET 等）
- 与业界对比或记录声明（SOTA/首次/record）：未声称 SOTA；对比对象为常规 DA-DSP（RLS+full DA-CFC）。复杂度层级（4M → 300k → 25k RM）中，仅 300k RM 对应本文结果 [p36]
- 推荐配图页：p36（复杂度阶梯与 FPGA 实物，75 ns 收敛）；p34（距离泛化 SNR 曲线，显示 60 km 后下降）；p31（DSP 模块图，标注迭代/前馈/需外部信息）

### 0921-合集待拆-全场-Mo5-F全场连拍.pdf（第38–61页）
- 讲者/机构：Mohammad Taha Askari（UBC 与 Nokia Bell Labs）, Lutz Lampe（UBC）, Amirhossein Ghazisaeidi（Nokia Bell Labs） | 题目：Sequential Neural Probabilistic Amplitude Shaping: Learning the Channel's Language | 类型：学术论文（仿真）
- 方向归属（主/次）：主 1（相干 长途，概率整形/非线性）；次 无
- 核心主张：
  1. 概率幅度整形（PAS）的联合分布整形需要考虑非线性；此前 sequence selection（拒绝采样）无最优性保证、复杂度高、存在块间效应和边信息速率损失 [p46]
  2. 速率损失（rate loss）必须被显式优化，而不是事后测量 [p61]
  3. Seq-NPAS 是固定长度、顺序（自回归、固定上下文窗口）的联合分布学习方案，在更低复杂度下优于 sequence selection [p61]
- 关键数据（均为数值仿真，非实验）：
  - 仿真参数：64QAM，双偏振，50 GBd，WDM 间隔 55 GHz，5 个 WDM 信道，RRC 滚降 0.1，单跨段 205 km，光纤损耗 0.2 dB/km，色散 17 ps/nm/km，非线性系数 1.30 1/W/km，EDFA 噪声系数 5 dB [p59]
  - 速率损失对比：块长 n=16 bit 时 NPAS 约 1.25 bit/QAM 符号，NPAS++ 与 Seq-NPAS++ 约 0.55–0.6；n=2048 bit 时 NPAS 约 0.89，NPAS++ 与 Seq-NPAS++ 均降到约 0.05 以下（Seq-NPAS++ 略高于 NPAS++，放大图约 0.06 对 0.03）[p58]
  - AIR（bit/QAM 符号）vs 每信道每偏振功率：峰值处 Seq-NPAS++ 约 4.47 @ 约 7–7.5 dBm；比 ESS+Seq. Sel. 高约 0.05 bit/QAM 符号；比均匀 64QAM（峰值约 4.27 @ 约 6.5 dBm）高约 0.2 bit/QAM 符号；ESS 峰值约 4.41，ESS+Seq.Sel. 约 4.43，NPAS++ 约 4.46 [p60]
  - 训练：Gumbel-softmax 采样、失配高斯解映射器、BCE 损失；损失 L++ = L_NPS + R_loss + λ·D_KL(p(x) || p_MB(x)) [p50, p55]
- 提到的公司/客户/产品/标准：Nokia Bell Labs；参考 Civelli et al. OFC 2023 sequence selection；Böcherer et al. PAS（1.53 dB 线性整形增益上限，AWGN 信道）[p41]；ESS（枚举球整形）作为基线
- 与业界对比或记录声明（SOTA/首次/record）：讲者称在更低复杂度下优于 sequence selection [p61]；未见 record 声明
- 推荐配图页：p60（AIR 对功率曲线，比较均匀/ESS/ESS+Seq.Sel./NPAS++/Seq-NPAS++）；p58（速率损失对块长）；p55（Seq-NPAS 问题公式与损失函数）

### 0921-合集待拆-全场-Mo5-F全场连拍.pdf（第62–76页）
- 讲者/机构：Bilal Khalid（一作及主讲，NESTOR 早期研究员）, Fabio Cavaliere, Luca Giorgi, Pedro Freire, Sergei K. Turitsyn, Jaroslaw E. Prilepsky / Aston University（Aston Institute of Photonic Technologies）与 Ericsson，EU MSCA-DN NESTOR | 题目：DPD-KAN: Kolmogorov-Arnold Networks for Low-Complexity Digital Predistortion in 5G Analog Radio-over-Fiber Systems | 类型：学术论文
- 方向归属（主/次）：主 5（RoF / 前传）；次 3（VCSEL DML 线性化，DSP）
- 核心主张：
  1. 用 KAN 做 DPD，对 5G NR A-RoF 前传链路实现线性化 [p74]
  2. 低复杂度预算下 KAN 优于传统 MLP 与基于 Volterra 的 GMP [p74]
  3. 高复杂度预算下 KAN 与 MLP 性能相近 [p74]
- 关键数据：
  - 实验链路：Tx DSP -> AWG -> 驱动放大器 -> VCSEL DML -> 1 km SSMF -> PD -> RTO；信号为 5G NR Test Model 3.1，100 MHz，64QAM；引用 MOPA：>97% 的前传 RoF 链路 <1 km，目标场景为大型室内 [p68]
  - DPD 结构：双路径残差学习（KAN 路径学习残差 ΔI、ΔQ，线性路径为恒等跳连），输入 XI、XQ、P_RF，B 样条基函数（2 阶与 3 阶）[p70]
  - EVM_RMS vs RF 输入功率：无 DPD 在约 5 dBm 处约 7.5%；MLP(BOP≈10^4) 约 3.9%；KAN(BOP≈10^4) 约 2.9%；GMP(BOP≈10^5) 约 4.1%；KAN(BOP≈10^5) 约 2.3%；噪声极限约 0.2–0.5%（数值读自曲线，近似）[p71]
  - 复杂度对比：平均 EVM ≤2% 所需 BOP，KAN 1.32×10^4，MLP 2.75×10^4；高复杂度（约 10^5 BOP 以上）两者趋于约 1.5–1.7% [p72]
  - 讲者总结：在 10^4 BOP 下 EVM 较 MLP 低约 24%，较 GMP 低约 30%；达到平均 EVM <2% 所需 BOP 比 MLP 少约 52%（平均取高驱动区 2–5 dBm）[p73]
  - PSD 对比：带外杂散抑制 KAN(10^5 BOP) 最佳，无 DPD 最差（图中 ±50 MHz 至 ±150 MHz 范围）[p71]
- 提到的公司/客户/产品/标准：Ericsson、MOPA（Mobile Optical Pluggables Alliance）requirements v26a、5G NR TM3.1、VCSEL DML；对比方法：MLP、GMP（广义记忆多项式，Volterra 类）
- 与业界对比或记录声明（SOTA/首次/record）：未声称 SOTA/首次；对比 MLP 与 GMP [p73]
- 推荐配图页：p71（EVM 对 RF 功率与 PSD 对比）；p72（BOP 复杂度对比，2% EVM 门限）；p70（双路径残差 KAN 结构）；p73（关键结论：24%/30%/52%）

## 本批小结

1. 神经网络在 DSP 中的位置从"提升性能"转向"压缩复杂度/收敛时间"：UCL 超网络把 4M 实数乘法压到约 300k（目标 25k），并给出 FPGA 75 ns 固定收敛；Aston KAN-DPD 达到 EVM≤2% 所需 BOP 比 MLP 少约 52%；同场未详述的国立清华 PCG-VE（另批）也以稀疏化降复杂度。（UCL F2、Aston F4）
2. 相干技术向园区/接入下沉，给 DSP 提出突发与光交换下的快速重捕获要求：UCL 开篇引用 Marvell Aquila coherent-lite（O 波段 1.6 Tb/s，2–20 km）、OFC 2026 光交换演示与 CableLabs CPON（100 Gb/s/波长）。但超网络 DSP 目前在约 60 km 以后掉点明显（约 95 km 处约 8 dB 对 13–14 dB），适用距离偏短，与园区场景匹配。（UCL F2）
3. 概率整形正从"分布匹配 + 事后选序列"转向"端到端学习联合分布"：Seq-NPAS 用固定上下文自回归，在 205 km 单跨仿真中比均匀 64QAM 高约 0.2 bit/QAM 符号，比 ESS+序列选择高约 0.05；关键是把速率损失写进损失函数。但目前仅为仿真，且相对 NPAS++ 无额外 AIR 优势，主要卖点是固定长度与低复杂度。（Nokia/UBC F3）
4. 模拟 RoF 前传的线性化选择：目标场景为 <1 km 室内，VCSEL DML 非线性和 RF 放大器记忆效应用 DPD 补偿；KAN 在低预算区间占优，高预算区间与 MLP 无差别，实用价值落在超低 BOP 区。（Aston F4）
5. 本场（Mo5-F）整体主题是"DSP/算法层的低复杂度非线性补偿"：F1 华南理工、F5 NTT（样本域 Volterra DPD，168 GBd PCS-324QAM）、F6 国立清华（稀疏 Volterra）均由其他批次处理；三家在本批可见的共同点是复杂度—性能折中被放到与性能同等重要的位置。
