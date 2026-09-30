---
title: L4 混合信号与 DFE
tags:
  - WiFi
  - 混合信号
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

数字与模拟的边界：ADC / DAC 完成转换，数字前端（DFE）负责采样率转换、削峰、预失真和各种损伤的数字补偿。

| 发射 TX | 接收 RX |
|---|---|
| 上采样 · CFR · DPD → DAC | ADC → 抽取 · DC / IQ 校正 |

## 关键技术与演进

- **带宽与精度**：320 MHz 带宽需要数百 MS/s 以上的 ADC / DAC，同时要有约 10 位以上的 ENOB。
- **数字化补偿**：模拟缺陷越来越依赖数字校准（IQ、LO 泄漏、DPD），校准固件成为芯片竞争力的一部分。
- **趋势**：神经网络 DPD、低复杂度宽带 DPD、时间交织 ADC 的后台校准。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/01. ADC and DAC\|ADC、DAC 与采样率转换]] | [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/01. ADC and DAC#dac-数模转换器\|DAC 数模转换器]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/01. ADC and DAC#adc-模数转换器\|ADC 模数转换器]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/01. ADC and DAC#时间交织-adc-tiadc\|时间交织 ADC TI‑ADC]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/01. ADC and DAC#过采样抽取与插值-decimation--interpolation\|过采样、抽取与插值 Decimation ／ Interpolation]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/01. ADC and DAC#papr-峰均功率比\|PAPR 峰均功率比]] |
| [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/02. Impairments and Calibration\|射频损伤与校准]] | [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/02. Impairments and Calibration#evm-误差矢量幅度\|EVM 误差矢量幅度]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/02. Impairments and Calibration#iq-失配-iq-imbalance\|IQ 失配 IQ Imbalance]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/02. Impairments and Calibration#lo-泄漏--载波泄漏-lo-leakage\|LO 泄漏 ／ 载波泄漏 LO Leakage]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/02. Impairments and Calibration#直流偏移-dc-offset\|直流偏移 DC Offset]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/02. Impairments and Calibration#相位噪声-phase-noise\|相位噪声 Phase Noise]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/02. Impairments and Calibration#非线性与压缩-nonlinearity\|非线性与压缩 Nonlinearity]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/02. Impairments and Calibration#片上自校准-onchip-calibration\|片上自校准 On‑Chip Calibration]] |
| [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/03. DPD and CFR\|数字预失真 DPD 与削峰 CFR]] | [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/03. DPD and CFR#功率回退-power-backoff\|功率回退 Power Backoff]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/03. DPD and CFR#cfr-削峰-crest-factor-reduction\|CFR 削峰 Crest Factor Reduction]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/03. DPD and CFR#dpd-数字预失真-digital-predistortion\|DPD 数字预失真 Digital Predistortion]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/03. DPD and CFR#amam--ampm-失真\|AM‑AM ／ AM‑PM 失真]] · [[Wireless Communication/02. WiFi Technology Atlas/04. Mixed-Signal and DFE/03. DPD and CFR#aclr--频谱模板-spectral-mask\|ACLR ／ 频谱模板 Spectral Mask]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| 集成于 Wi‑Fi SoC | 同 L3 |
| 数据转换器 IP | 各芯片厂自研为主 |
| 测试 | Keysight（信号分析）、R&S |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/02. Chips|产业：芯片]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#l4-混合信号与-dfe|学术：DFE／校准]]
