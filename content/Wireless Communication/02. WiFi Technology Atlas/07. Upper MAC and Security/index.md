---
title: L7 Upper MAC 与安全
tags:
  - WiFi
  - MAC
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

管理连接的全生命周期：扫描、认证、关联、加密、速率选择、QoS 与节能；实现分布在固件、驱动（mac80211）和用户态守护进程（hostapd / wpa_supplicant）中。

| 发射 TX | 接收 RX |
|---|---|
| 加密 · A‑MSDU · 速率选择 · MLO 映射 | 解密 · 重排序 · 去重 |

## 关键技术与演进

- **安全演进**：WEP → WPA2 → WPA3（SAE、PMF、6 GHz 强制）；隐私方向有 802.11bh / bi。
- **速率控制与时延**：学习型速率控制、AQL / FQ‑CoDel 抑制缓冲膨胀、SCS 显式 QoS。
- **节能**：PS → TWT → R‑TWT（兼顾低时延）→ AP 节能（Wi‑Fi 8）。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming\|连接建立与漫游]] | [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming#扫描-scanning被动--主动\|扫描 Scanning（被动 ／ 主动）]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming#认证与关联-authentication--association\|认证与关联 Authentication ／ Association]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming#四次握手-4way-handshake\|四次握手 4‑Way Handshake]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming#80211k-无线资源测量\|802.11k 无线资源测量]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming#80211v-bss-转换管理-btm\|802.11v BSS 转换管理 BTM]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming#80211r-快速-bss-转换-ft\|802.11r 快速 BSS 转换 FT]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming#漫游决策-roaming-decision\|漫游决策 Roaming Decision]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/01. Connection and Roaming#band-steering-频段引导\|Band Steering 频段引导]] |
| [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security\|安全与隐私]] | [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#wpa2-与-wpa3\|WPA2 与 WPA3]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#sae-对等实体同时认证\|SAE 对等实体同时认证]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#pmf-受保护管理帧80211w\|PMF 受保护管理帧（802.11w）]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#ccmp-与-gcmp\|CCMP 与 GCMP]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#owe-机会性无线加密enhanced-open\|OWE 机会性无线加密（Enhanced Open）]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#8021x--eap-企业认证\|802.1X ／ EAP 企业认证]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#mac-地址随机化与-80211bh--80211bi\|MAC 地址随机化与 802.11bh ／ 802.11bi]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#krack-密钥重装攻击\|KRACK 密钥重装攻击]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#fragattacks-分片与聚合攻击\|FragAttacks 分片与聚合攻击]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/02. Security#wifi-shield-与物理层安全\|Wi‑Fi Shield 与物理层安全]] |
| [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save\|速率控制、QoS 与节能]] | [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save#速率控制-rate-adaptation\|速率控制 Rate Adaptation]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save#minstrelht\|Minstrel‑HT]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save#wmm-与-qos-映射dscp--up--ac\|WMM 与 QoS 映射（DSCP → UP → AC）]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save#scs-流分类服务与-qos-特征\|SCS 流分类服务与 QoS 特征]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save#aql-空口时间队列限制与-fqcodel\|AQL 空口时间队列限制与 FQ‑CoDel]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save#省电模式-ps--uapsd\|省电模式 PS ／ U‑APSD]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save#twt-目标唤醒时间\|TWT 目标唤醒时间]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/03. Rate Control QoS and Power Save#rtwt-受限目标唤醒时间\|R‑TWT 受限目标唤醒时间]] |
| [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/04. Driver and Software Stack\|驱动与软件栈]] | [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/04. Driver and Software Stack#softmac-与-fullmac\|SoftMAC 与 FullMAC]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/04. Driver and Software Stack#cfg80211--mac80211--nl80211\|cfg80211 ／ mac80211 ／ nl80211]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/04. Driver and Software Stack#hostapd-与-wpa_supplicant\|hostapd 与 wpa_supplicant]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/04. Driver and Software Stack#固件-firmware-与卸载-offload\|固件 Firmware 与卸载 Offload]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/04. Driver and Software Stack#openwrtprplos-与-rdkb\|OpenWrt、prplOS 与 RDK‑B]] · [[Wireless Communication/02. WiFi Technology Atlas/07. Upper MAC and Security/04. Driver and Software Stack#wifi-数据模型与远程管理tr069--tr369-usp--data-elements\|Wi‑Fi 数据模型与远程管理（TR‑069 ／ TR‑369 USP ／ Data Elements）]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| 芯片固件 / SDK | 各 Wi‑Fi 芯片商 |
| 开源软件 | Linux mac80211、hostapd / wpa_supplicant、OpenWrt |
| 运营商软件栈 | prplOS（prpl 基金会）、RDK‑B |
| 认证 / 安全 | Wi‑Fi Alliance（WPA3 认证）；RADIUS / NAC 厂商 |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/04. Vendors and Operators|产业：设备商与运营商]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#l7-upper-mac-与驱动|学术：Upper MAC]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#x3-安全与隐私|学术：安全]]
