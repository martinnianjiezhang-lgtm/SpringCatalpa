---
title: L8 多 AP 与网络
tags:
  - WiFi
  - 网络
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

单个 AP 之上的网络层面：多个 AP 如何协作、组网、漫游，如何被集中管理与运维。这是 Wi‑Fi 8 的主战场，也是设备商差异化的核心。

| 发射 TX | 接收 RX |
|---|---|
| 应用 → TCP/IP → WMM 映射 | GRO/NAPI → 应用 |

## 关键技术与演进

- **多 AP 协作（MAPC）**：Co‑TDMA → Co‑SR → Co‑BF → Co‑RTWT，把蜂窝的协作思想引入 Wi‑Fi。
- **无缝漫游**：802.11k/v/r → Wi‑Fi 8 SMD；厂商的同频组网（ASFN）实现“零漫游”。
- **组网形态**：家庭 Mesh / EasyMesh、中国 FTTR、企业 AC 与云管理。
- **AIOps**：硬件同质化之后，AI 运维平台成为企业 WLAN 的主要竞争点。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/01. Multi-AP Coordination\|多 AP 协作 MAPC]] | [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/01. Multi-AP Coordination#mapc-多-ap-协作\|MAPC 多 AP 协作]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/01. Multi-AP Coordination#cotdma-协作时分\|Co‑TDMA 协作时分]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/01. Multi-AP Coordination#cosr-协作空间复用\|Co‑SR 协作空间复用]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/01. Multi-AP Coordination#cobf-协作波束成形\|Co‑BF 协作波束成形]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/01. Multi-AP Coordination#cortwt-协作受限目标唤醒时间\|Co‑RTWT 协作受限目标唤醒时间]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/01. Multi-AP Coordination#jt-联合传输\|JT 联合传输]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/01. Multi-AP Coordination#icssr-与厂商方案\|iCSSR 与厂商方案]] |
| [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management\|组网、漫游与网络管理]] | [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#mesh-组网与回传-backhaul\|Mesh 组网与回传 Backhaul]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#easymesh\|EasyMesh]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#fttr-光纤到房间\|FTTR 光纤到房间]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#ac-无线控制器与-capwap\|AC 无线控制器与 CAPWAP]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#云管理-cloudmanaged-wlan\|云管理 Cloud‑Managed WLAN]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#rrm-无线资源管理\|RRM 无线资源管理]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#aiops-智能运维\|AIOps 智能运维]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#smd-无缝移动域\|SMD 无缝移动域]] · [[Wireless Communication/02. WiFi Technology Atlas/08. Multi-AP and Network/02. Mesh Roaming and Management#asfn-与同频组网\|ASFN 与同频组网]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| 企业 WLAN | Cisco / Meraki、HPE（Aruba + Juniper Mist）、华为、新华三、锐捷、Ubiquiti、Belden（Ruckus）、Extreme、Fortinet |
| 家庭 / Mesh | TP‑Link、ASUS、小米、华为、eero、Netgear |
| 运营商与 FTTR | 华为、中兴、诺基亚、Sagemcom 等；软件平台 Plume、Airties |
| 标准 | Wi‑Fi Alliance EasyMesh、Broadband Forum |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/04. Vendors and Operators|产业：设备商与运营商]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#l8-多ap与网络|学术：多 AP 与网络]]
