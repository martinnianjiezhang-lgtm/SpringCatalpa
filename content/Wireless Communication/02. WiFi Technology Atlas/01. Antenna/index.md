---
title: L1 天线
tags:
  - WiFi
  - 天线
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

链路的最外端：发射时把射频电流变成电磁波辐射出去，接收时反过来。它决定了“信号能否进出设备”，以及 MIMO 能否真正分出多路空间流。

| 发射 TX | 接收 RX |
|---|---|
| 辐射 | 接收 |

## 关键技术与演进

- **多天线与去耦**：设备越小、天线越多（Wi‑Fi 7 手机 2×2、AP 4×4 至 8×8，还要与蓝牙、蜂窝、UWB 天线共存），隔离度和相关性成为瓶颈。
- **三频覆盖**：Wi‑Fi 6E/7 要求天线同时覆盖 2.4 / 5 / 6 GHz，最高到 7.125 GHz。
- **整机 OTA**：天线效率与整机自扰比芯片指标更能决定用户体验。
- **趋势**：片式（LTCC）天线进入 IoT；企业 AP 转向可切换的全向 / 定向天线；多 AP 协作要求天线方向图可预测。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/01. MIMO Antenna and Decoupling\|MIMO 天线与去耦]] | [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/01. MIMO Antenna and Decoupling#天线基本参数增益--效率--方向图--带宽\|天线基本参数（增益 ／ 效率 ／ 方向图 ／ 带宽）]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/01. MIMO Antenna and Decoupling#隔离度-isolations21\|隔离度 Isolation（S21）]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/01. MIMO Antenna and Decoupling#包络相关系数-ecc\|包络相关系数 ECC]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/01. MIMO Antenna and Decoupling#去耦技术-decoupling\|去耦技术 Decoupling]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/01. MIMO Antenna and Decoupling#特征模分析-cma-characteristic-mode-analysis\|特征模分析 CMA Characteristic Mode Analysis]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/01. MIMO Antenna and Decoupling#天线分集与选择-diversity--antenna-selection\|天线分集与选择 Diversity ／ Antenna Selection]] |
| [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/02. Antenna Forms and Testing\|天线形态与 OTA 测试]] | [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/02. Antenna Forms and Testing#pifa--单极子--偶极子\|PIFA ／ 单极子 ／ 偶极子]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/02. Antenna Forms and Testing#fpc--lds--金属边框天线\|FPC ／ LDS ／ 金属边框天线]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/02. Antenna Forms and Testing#ltcc-片式天线-chip-antenna\|LTCC 片式天线 Chip Antenna]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/02. Antenna Forms and Testing#全向与定向天线-omni--directional\|全向与定向天线 Omni ／ Directional]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/02. Antenna Forms and Testing#智能天线与可重构天线-smart--reconfigurable-antenna\|智能天线与可重构天线 Smart ／ Reconfigurable Antenna]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/02. Antenna Forms and Testing#ris-可重构智能表面\|RIS 可重构智能表面]] · [[Wireless Communication/02. WiFi Technology Atlas/01. Antenna/02. Antenna Forms and Testing#ota-空口测试-overtheair-testing\|OTA 空口测试 Over‑the‑Air Testing]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| 手机 / PC 天线 | 信维通信、硕贝德、立讯精密、Amphenol、Molex |
| 片式 / 嵌入式天线 | Murata、YAGEO、Taoglas、Ignion、Antenova、Kyocera AVX |
| AP 天线 | 设备商自研（Ruckus BeamFlex、Cisco、华为），以及 Laird、Ventev 等 |
| 测试 | Keysight、R&S、ETS‑Lindgren（暗室 / OTA） |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/03. RF Front-End and Antenna#天线|产业：天线]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#l1-天线-antenna|学术：天线]]
