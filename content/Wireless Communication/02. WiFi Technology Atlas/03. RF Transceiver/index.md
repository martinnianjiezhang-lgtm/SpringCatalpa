---
title: L3 射频收发机
tags:
  - WiFi
  - 射频
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

把基带信号搬到载波上（发射），或把载波信号搬回基带（接收）；产生本振，并处理多个射频之间的共存。

| 发射 TX | 接收 RX |
|---|---|
| 正交上变频 · PLL/LO · PA 驱动 | LNA → 混频 → 基带滤波 → VGA |

## 关键技术与演进

- **多频段、多射频并发**：MLO 要求 2–4 套收发机同时工作。
- **本振质量**：78.125 kHz 的子载波间隔与 4096‑QAM 要求亚度级的积分相位噪声。
- **共存**：Wi‑Fi / 蓝牙 / 蜂窝 / UWB 的设备内干扰，Wi‑Fi 8 引入 IDC 信令。
- **学术热点**：数字 PA / 极化发射机、ADPLL、宽带低功耗接收机（ISSCC、JSSC、RFIC）。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture\|收发机架构]] | [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture#零中频架构-zeroif--direct-conversion\|零中频架构 Zero‑IF ／ Direct Conversion]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture#正交调制与解调-iq-modulator--demodulator\|正交调制与解调 IQ Modulator ／ Demodulator]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture#混频器-mixer\|混频器 Mixer]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture#lna-低噪声放大器片上\|LNA 低噪声放大器（片上）]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture#基带滤波器与-vga\|基带滤波器与 VGA]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture#pa-驱动级与片上-pa\|PA 驱动级与片上 PA]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture#数字-pa--极化发射机-digital-pa--polar-tx\|数字 PA ／ 极化发射机 Digital PA ／ Polar TX]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/01. Transceiver Architecture#多射频并发-concurrent-multiradio\|多射频并发 Concurrent Multi‑Radio]] |
| [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/02. PLL and LO\|PLL 与本振]] | [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/02. PLL and LO#pll-锁相环\|PLL 锁相环]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/02. PLL and LO#小数分频-pll-fractionaln\|小数分频 PLL Fractional‑N]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/02. PLL and LO#vco-压控振荡器\|VCO 压控振荡器]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/02. PLL and LO#相位噪声与积分抖动-phase-noise--jitter\|相位噪声与积分抖动 Phase Noise ／ Jitter]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/02. PLL and LO#参考晶振-crystal--xo\|参考晶振 Crystal ／ XO]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/02. PLL and LO#lo-牵引-lo-pulling\|LO 牵引 LO Pulling]] |
| [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/03. Coexistence\|射频共存]] | [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/03. Coexistence#设备内共存-indevice-coexistence\|设备内共存 In‑Device Coexistence]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/03. Coexistence#pta-包流量仲裁-packet-traffic-arbitration\|PTA 包流量仲裁 Packet Traffic Arbitration]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/03. Coexistence#自干扰与多链路隔离-selfinterference\|自干扰与多链路隔离 Self‑Interference]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/03. Coexistence#阻塞与互调-blocking--intermodulation\|阻塞与互调 Blocking ／ Intermodulation]] · [[Wireless Communication/02. WiFi Technology Atlas/03. RF Transceiver/03. Coexistence#天线共享与分集切换\|天线共享与分集切换]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| 集成于 Wi‑Fi SoC / Combo 芯片 | Qualcomm、Broadcom、MediaTek、Realtek、Intel、Apple（N1）、海思、爱科微、乐鑫 |
| 射频 IP | CEVA（RivieraWaves）等 |
| 测试 | Keysight、R&S、LitePoint |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/02. Chips|产业：芯片]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#l3-射频收发机-rf-transceiver|学术：射频电路]]
