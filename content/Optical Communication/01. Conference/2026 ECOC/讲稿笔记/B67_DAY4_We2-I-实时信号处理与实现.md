---
title: "B67 · DAY4 · We2-I-实时信号处理与实现"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We2-I-大阪大学-实时信号处理.pdf（第1–15页；p2、p16为重复页，结论页p16未在本PDF内可见）
- 讲者/机构：Syoma Miura, Yohei Koganei, Koji Igarashi（大阪大学 / 1FINITY Inc.） | 题目：Parallel DSP Architecture with Pilot Aggregation for Real-Time MIMO Equalization Enabling Fast Polarization Tracking | 类型：学术论文（We2-I 实时信号处理，邀请/口头）
- 方向归属（主/次）：主 1（相干/oDSP）；次 无
- 核心主张（1–3条，用讲者自己的结论页原意）：
  1. 高阶QAM需要同时具备精确的线性均衡与快速自适应控制；并行化使MIMO更新间隔扩大P倍（数十到数百倍），实时电路无法像离线串行那样快速自适应 [p4][p6]
  2. 提出"导频汇聚"并行MIMO架构：并行度=导频间隔P，只在导频通道每个DSP时钟周期做自适应，系数再转给其余P−1个payload通道，开销仅1/P [p8]
  3. 消除更新式中的除法并流水线化，使电路延迟降至约1/10，DSP时钟可>100 MHz、更新延迟仅数个时钟；LUT/FF大幅减少，DSP减少50% [p13][p15]（讲者最终结论页未在本批可见）
- 关键数据（每条带单位与条件，末尾标 [pN]）：
  - 现有导频法可跟踪偏振旋转（RSOP）速度达600 krad/s（引自Yang 2021 Opt. Express，图中横轴约10^4–10^6 rad/s） [p5]
  - 开销：P=32时导频开销3.13%（1/P） [p8]
  - P=32、DSP时钟1 GHz、16QAM：所提方法在偏振"线宽"δf_D=10 kHz–1 MHz范围内BER稳定，10 kHz时SNR≈22 dB处BER约10^-5量级（曲线读数，近似）；传统导频法（导频间隔32×P）在快速偏振波动下BER几乎无改善 [p10]
  - 更新式最大电路延迟：含除法55.2 ns → 无除法5.7 ns（约1/10），可支持DSP时钟>100 MHz [p13]
  - 更新延迟仅6、4、3个时钟周期，分别对应MIMO、p、q抽头 [p12，据OCR，未看图]
  - 行为模型（AMD Vivado）验证：32 Gbaud，P=32，导频开销1/32，16QAM；有偏振波动（δf_D=100 kHz）时BER高于无波动，与数值仿真一致（无波动曲线约SNR 20 dB处BER≈6×10^-6，近似读数） [p14]
  - 资源对比（并行度P=1–15，对比全通道判决导向法）：LUT与FF几乎不随P增长（约0.5×10^4量级），传统P=15时LUT约6×10^4、FF约4.7×10^4；DSP片数P=15时传统约7×10^3、所提约3.5×10^3，即减少50% [p15]
  - 仿真模型：16QAM，2 sample/symbol，Nyquist成形，50 taps（OCR，未看图确认） [p9]
- 提到的公司/客户/产品/标准：AMD Vivado Design Suite；AMD VCU128 FPGA评估板；Python数值仿真；引用Haykin、Savory、Mori(2012)、Beppu(JLT 2022, Opt. Express 2020)、Yang(2021)、Miura & Igarashi OECC2025
- 与业界对比或记录声明（SOTA/首次/record）：未见record声明；对比对象为传统导频法与全通道判决导向法（LUT/FF显著减少，DSP减半） [p10][p15]
- 推荐配图页：p8（导频汇聚并行MIMO架构概念图）；p10（P=32下所提方法与传统导频法BER对比）；p15（LUT/FF/DSP资源对比）

## 本批小结
- 本批仅1篇有效讲稿（大阪大学We2-I），其余为重复页。
- 高波特率相干实时DSP的瓶颈已从算法转向"并行化导致自适应环路延迟"：P倍并行使MIMO更新间隔放大P倍，快速偏振跟踪能力下降（来自0923-We2-I 大阪大学 p6）。
- 解法思路是"只在导频通道自适应、系数共享"，用1/P导频开销换取资源与跟踪性能；并通过去除除法把关键路径由55.2 ns压至5.7 ns（同上 p8、p13）。
- 资源收益：LUT/FF基本不随并行度增长，DSP减半，对ASIC oDSP的面积/功耗有借鉴意义，但验证仍为FPGA行为模型与仿真，32 Gbaud 16QAM，尚非现场链路（同上 p14、p15）。
