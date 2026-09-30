---
title: X1 芯片与 SoC
tags:
  - WiFi
  - 芯片
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

跨层方向：L3–L7 的功能最终集成在芯片上。路由 SoC、终端 Combo 芯片、IoT 芯片的架构取舍，决定了产业分工。

## 关键技术与演进

- **Wi‑Fi 8 芯片提前两年发布**：MediaTek、Broadcom、Qualcomm 在 2026 年上半年全部发布。
- **路由 SoC 加入 AI**：NPU / APU 进入网关平台。
- **终端垂直整合**：Apple N1 替换 Broadcom。
- **融合**：Wi‑Fi 与 PON / 以太网 / FWA 在网关芯片上集成。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture\|Wi‑Fi 芯片与 SoC 架构]] | [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture#ap--路由-soc\|AP ／ 路由 SoC]] · [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture#combo-芯片-wifi--bt-combo\|Combo 芯片 Wi‑Fi + BT Combo]] · [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture#npu--apu-与片上-ai\|NPU ／ APU 与片上 AI]] · [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture#包转发加速-network-offload-engine\|包转发加速 Network Offload Engine]] · [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture#cnvi-集成连接架构\|CNVi 集成连接架构]] · [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture#主机接口-pcie--sdio--usb\|主机接口 PCIe ／ SDIO ／ USB]] · [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture#工艺与集成-process-and-integration\|工艺与集成 Process and Integration]] · [[Wireless Communication/02. WiFi Technology Atlas/09. Chip and SoC/01. SoC Architecture#通信协处理器-radio-coprocessor\|通信协处理器 Radio Co‑Processor]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| AP / 网关 SoC | Broadcom、Qualcomm、MediaTek、Realtek、MaxLinear；国内有海思、云程、中兴微 |
| 终端 Combo | Qualcomm、MediaTek、Broadcom、Apple（自研）、Intel |
| IoT | 乐鑫、Infineon、NXP、Silicon Labs、TI、爱科微、博通集成；HaLow：Morse Micro |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/02. Chips|产业：芯片]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#x1-芯片与soc|学术：芯片与 SoC]]
