---
title: L5 PHY 基带
tags:
  - WiFi
  - PHY
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

把 MAC 交下来的比特变成 OFDM 波形（发射），或把波形还原成比特（接收）。它决定了每赫兹频谱能传多少比特。

| 发射 TX | 接收 RX |
|---|---|
| LDPC → QAM → 预编码 → IFFT + GI | 同步 → 信道估计 → MIMO 检测 → LDPC 译码 |

## 关键技术与演进

- **速率三板斧**：更宽带宽（20 → 320 MHz）、更高阶 QAM（64 → 4096）、更多空间流（1 → 16）。
- **效率**：OFDMA、MRU、前导打孔，让宽信道在干扰和多用户下仍然可用。
- **Wi‑Fi 8 转向可靠性**：UEQM、DRU、ELR、更长 LDPC 码字，都是“在边缘和上行多挤出几 dB”，而不是提高峰值速率。
- **CSI 的双重价值**：同一套信道估计既服务于通信（波束成形），也服务于感知（802.11bf）。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA\|OFDM 与 OFDMA]] | [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#ofdm-正交频分复用\|OFDM 正交频分复用]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#子载波间隔与符号时长-subcarrier-spacing\|子载波间隔与符号时长 Subcarrier Spacing]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#ifft-与-fft\|IFFT 与 FFT]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#保护间隔-gi--循环前缀-cp\|保护间隔 GI ／ 循环前缀 CP]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#加窗-windowing\|加窗 Windowing]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#信道带宽与信道绑定-channel-bonding\|信道带宽与信道绑定 Channel Bonding]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#ofdma-正交频分多址\|OFDMA 正交频分多址]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#资源单元-ru-resource-unit\|资源单元 RU Resource Unit]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#多资源单元-mru-multiple-ru\|多资源单元 MRU Multiple RU]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#前导打孔-preamble-puncturing\|前导打孔 Preamble Puncturing]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#分布式资源单元-dru-distributed-ru\|分布式资源单元 DRU Distributed RU]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/01. OFDM and OFDMA#dcm-与-dup-复制传输\|DCM 与 DUP 复制传输]] |
| [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation\|编码与调制]] | [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#加扰-scrambler\|加扰 Scrambler]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#bcc-二进制卷积码\|BCC 二进制卷积码]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#ldpc-低密度奇偶校验码\|LDPC 低密度奇偶校验码]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#2ldpc-更长码字\|2×LDPC 更长码字]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#流解析与交织-stream-parser--interleaver\|流解析与交织 Stream Parser ／ Interleaver]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#qam-正交幅度调制\|QAM 正交幅度调制]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#mcs-调制编码方案\|MCS 调制编码方案]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#ueqm-非等调制\|UEQM 非等调制]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#星座映射与格雷编码-gray-mapping\|星座映射与格雷编码 Gray Mapping]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/02. Coding and Modulation#llr-对数似然比软解调\|LLR 对数似然比软解调]] |
| [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming\|MIMO 与波束成形]] | [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#mimo-多输入多输出\|MIMO 多输入多输出]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#空间流-spatial-stream\|空间流 Spatial Stream]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#csd-循环移位分集\|CSD 循环移位分集]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#波束成形-beamforming\|波束成形 Beamforming]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#信道探测-soundingndpa--ndp--反馈\|信道探测 Sounding（NDPA ／ NDP ／ 反馈）]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#v-矩阵压缩反馈-compressed-beamforming-report\|V 矩阵压缩反馈 Compressed Beamforming Report]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#sumimo-与-mumimo\|SU‑MIMO 与 MU‑MIMO]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#预编码-precodingzf--mmse--svd\|预编码 Precoding（ZF ／ MMSE ／ SVD）]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#mimo-检测-mimo-detectionzf--mmse--ml--球形译码\|MIMO 检测 MIMO Detection（ZF ／ MMSE ／ ML ／ 球形译码）]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/03. MIMO and Beamforming#协作波束成形-cobf\|协作波束成形 Co‑BF]] |
| [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format\|前导与 PPDU 帧格式]] | [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#ppdu-物理层协议数据单元\|PPDU 物理层协议数据单元]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#lstf-传统短训练字段\|L‑STF 传统短训练字段]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#lltf-传统长训练字段\|L‑LTF 传统长训练字段]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#lsig-传统信号字段\|L‑SIG 传统信号字段]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#usig-通用信号字段\|U‑SIG 通用信号字段]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#hesiga--hesigb-与-ehtsig\|HE‑SIG‑A ／ HE‑SIG‑B 与 EHT‑SIG]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#heehtstf-与-heehtltf\|HE／EHT‑STF 与 HE／EHT‑LTF]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#包扩展-pe-packet-extension\|包扩展 PE Packet Extension]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#elr-ppdu-增强远距\|ELR PPDU 增强远距]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/04. Preamble and PPDU Format#appdu-聚合-ppdu\|A‑PPDU 聚合 PPDU]] |
| [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation\|接收同步与信道估计]] | [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#分组检测-packet-detection\|分组检测 Packet Detection]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#agc-自动增益控制\|AGC 自动增益控制]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#cfo-载波频偏估计与补偿\|CFO 载波频偏估计与补偿]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#符号定时同步-timing-synchronization\|符号定时同步 Timing Synchronization]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#信道估计-channel-estimation\|信道估计 Channel Estimation]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#导频相位跟踪-pilot-trackingcpe--sfo\|导频相位跟踪 Pilot Tracking（CPE ／ SFO）]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#均衡-equalization\|均衡 Equalization]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#csi-信道状态信息\|CSI 信道状态信息]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#rssi-与-snr\|RSSI 与 SNR]] · [[Wireless Communication/02. WiFi Technology Atlas/05. PHY Baseband/05. Receiver Synchronization and Channel Estimation#cca-空闲信道评估\|CCA 空闲信道评估]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| 基带芯片 | Qualcomm、Broadcom、MediaTek、Realtek、Intel、Apple、海思等（集成于 SoC） |
| 算法 / 仿真工具 | MathWorks WLAN Toolbox、Keysight PathWave |
| 开源实现 | openwifi（FPGA）、GNU Radio gr‑ieee802‑11 |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/02. Chips|产业：芯片]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#l5-phy-基带|学术：PHY]]
