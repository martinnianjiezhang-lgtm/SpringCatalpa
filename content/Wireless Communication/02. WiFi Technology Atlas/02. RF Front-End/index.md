---
title: L2 射频前端 FEM
tags:
  - WiFi
  - 射频前端
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

天线与收发芯片之间：发射时由 PA 放大，接收时由 LNA 放大，开关与滤波器决定信号往哪走、哪些频率被挡住。

| 发射 TX | 接收 RX |
|---|---|
| PA → 开关 → 滤波 | 滤波 → LNA → 开关 |

## 关键技术与演进

- **线性度与效率**：4096‑QAM 需要约 −38 dB 以下的 EVM，PA 必须大幅回退，效率随之下降。
- **5 / 6 GHz 共存滤波**：三频 AP 和 MLO 的关键前端难题，依赖 BAW / XBAR 高陡度滤波器。
- **集成化**：终端与 IoT 趋向 iFEM；高端 AP 仍用外置 GaAs FEM。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/01. Power Amplifier\|功率放大器 PA]] | [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/01. Power Amplifier#pa-功率放大器\|PA 功率放大器]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/01. Power Amplifier#p1db-与饱和功率-psat\|P1dB 与饱和功率 Psat]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/01. Power Amplifier#pae-功率附加效率\|PAE 功率附加效率]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/01. Power Amplifier#doherty-pa\|Doherty PA]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/01. Power Amplifier#包络跟踪-et-envelope-tracking\|包络跟踪 ET Envelope Tracking]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/01. Power Amplifier#线性化-linearization\|线性化 Linearization]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/01. Power Amplifier#功率检测与温度补偿-power-detector\|功率检测与温度补偿 Power Detector]] |
| [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter\|LNA、开关与滤波器]] | [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter#fem-射频前端模块\|FEM 射频前端模块]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter#ifem-集成射频前端\|iFEM 集成射频前端]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter#lna-低噪声放大器fem-内\|LNA 低噪声放大器（FEM 内）]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter#tr-开关-transmitreceive-switch\|T／R 开关 Transmit／Receive Switch]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter#滤波器-filtersaw--baw--fbar--xbar--ltcc\|滤波器 Filter（SAW ／ BAW ／ FBAR ／ XBAR ／ LTCC）]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter#5-ghz--6-ghz-共存滤波\|5 GHz ／ 6 GHz 共存滤波]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter#双工器与多工器-diplexer--multiplexer\|双工器与多工器 Diplexer ／ Multiplexer]] · [[Wireless Communication/02. WiFi Technology Atlas/02. RF Front-End/02. LNA Switch and Filter#sar-与功率回退-sar-backoff\|SAR 与功率回退 SAR Backoff]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| Wi‑Fi FEM（海外） | Skyworks + Qorvo（合并中）、Qualcomm RFFE、Murata |
| Wi‑Fi FEM（国内） | 康希通信、唯捷创芯、卓胜微、飞骧 |
| 滤波器 | Broadcom（FBAR）、Qorvo（BAW）、Murata（XBAR / SAW） |
| 测试 | LitePoint、Keysight、R&S |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/03. RF Front-End and Antenna|产业：射频前端]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#l2-射频前端-fem|学术：FEM]]
