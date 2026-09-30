---
title: X2 感知与定位
tags:
  - WiFi
  - 感知
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

跨层方向：复用 PHY 的信道估计（CSI）与 MAC 的测量流程，让 Wi‑Fi 从“通信网络”变成“感知网络”。

## 关键技术与演进

- **标准化**：802.11bf（感知，2025）、802.11az / bk（定位）。
- **商业化**：ISP 网关运动检测、安防与养老看护；ADT 收购 Origin AI。
- **技术挑战**：跨环境泛化、多设备协同、隐私保护。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/01. WLAN Sensing\|WLAN 感知]] | [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/01. WLAN Sensing#wifi-感知-wifi-sensing\|Wi‑Fi 感知 Wi‑Fi Sensing]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/01. WLAN Sensing#csi-与-rssi-感知\|CSI 与 RSSI 感知]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/01. WLAN Sensing#80211bf-wlan-感知标准\|802.11bf WLAN 感知标准]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/01. WLAN Sensing#sbp-代理感知-sensing-by-proxy\|SBP 代理感知 Sensing by Proxy]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/01. WLAN Sensing#dmg-感知-60-ghz-sensing\|DMG 感知 60 GHz Sensing]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/01. WLAN Sensing#感知的商业化与隐私\|感知的商业化与隐私]] |
| [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/02. Positioning and Ranging\|Wi‑Fi 定位与测距]] | [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/02. Positioning and Ranging#rssi-指纹定位-fingerprinting\|RSSI 指纹定位 Fingerprinting]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/02. Positioning and Ranging#ftm-精细时间测量--rtt\|FTM 精细时间测量 ／ RTT]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/02. Positioning and Ranging#80211az-下一代定位-ngp\|802.11az 下一代定位 NGP]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/02. Positioning and Ranging#80211bk-320-mhz-定位\|802.11bk 320 MHz 定位]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/02. Positioning and Ranging#aoa--aod-角度定位\|AoA ／ AoD 角度定位]] · [[Wireless Communication/02. WiFi Technology Atlas/10. Sensing and Positioning/02. Positioning and Ranging#wifi-ranging-与-uwb-的关系\|Wi‑Fi Ranging 与 UWB 的关系]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| 感知软件 | Cognitive Systems、Origin AI（ADT）、Plume |
| 芯片支持 | Qualcomm、Broadcom、MediaTek、Infineon（片上感知） |
| 定位 | Wi‑Fi RTT（Android）、企业定位平台（Cisco Spaces、HPE 等） |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/04. Vendors and Operators#wifi-感知商业化|产业：感知商业化]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#x2-感知与定位|学术：感知与定位]]
