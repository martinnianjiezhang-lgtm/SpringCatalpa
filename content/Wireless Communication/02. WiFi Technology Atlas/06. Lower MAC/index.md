---
title: L6 Lower MAC 信道接入
tags:
  - WiFi
  - MAC
  - 技术图谱
---

返回 [[Wireless Communication/02. WiFi Technology Atlas/index|WiFi 全局架构与技术图谱]]

## 在架构中的位置

决定“谁在什么时候用信道”，并完成对时间要求严格的应答（ACK / BA）。它运行在芯片硬件或实时固件里，时间精度是微秒级。

| 发射 TX | 接收 RX |
|---|---|
| EDCA 退避 · A‑MPDU · 触发帧 / OFDMA | FCS 校验 · SIFS 后回 BA · NAV / BSS Color |

## 关键技术与演进

- **从竞争到调度**：CSMA/CA（Wi‑Fi 1–5）→ OFDMA 与触发帧（Wi‑Fi 6）→ MLO 与 R‑TWT（Wi‑Fi 7）→ 多 AP 协作、NPCA、DSO（Wi‑Fi 8）。
- **MLO**：Wi‑Fi 7 最核心的 MAC 特性，也是终端体验提升最明显的地方（尤其是 EMLSR）。
- **指标变化**：从吞吐转向时延尾部（P99）与可靠性。

## 技术名词（点击查看原理）

%% atlas-terms start %%
| 笔记 | 技术名词 |
|---|---|
| [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access\|信道接入（CSMA／CA 与 EDCA）]] | [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#csmaca-载波侦听多路访问冲突避免\|CSMA／CA 载波侦听多路访问／冲突避免]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#dcf-与-edca\|DCF 与 EDCA]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#接入类别-ac-access-category\|接入类别 AC Access Category]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#帧间间隔-sifs--difs--aifs\|帧间间隔 SIFS ／ DIFS ／ AIFS]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#退避与竞争窗口-backoff--cw\|退避与竞争窗口 Backoff ／ CW]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#txop-传输机会\|TXOP 传输机会]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#nav-网络分配矢量虚拟载波侦听\|NAV 网络分配矢量（虚拟载波侦听）]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#rtscts-与隐藏节点\|RTS／CTS 与隐藏节点]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#ack-确认与重传\|ACK 确认与重传]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/01. Channel Access#信标帧-beacon\|信标帧 Beacon]] |
| [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/02. Aggregation and Block Ack\|帧聚合与 Block Ack]] | [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/02. Aggregation and Block Ack#amsdu-聚合-mac-服务数据单元\|A‑MSDU 聚合 MAC 服务数据单元]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/02. Aggregation and Block Ack#ampdu-聚合-mac-协议数据单元\|A‑MPDU 聚合 MAC 协议数据单元]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/02. Aggregation and Block Ack#block-ack-块确认\|Block Ack 块确认]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/02. Aggregation and Block Ack#重排序缓冲-reorder-buffer\|重排序缓冲 Reorder Buffer]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/02. Aggregation and Block Ack#分片-fragmentation\|分片 Fragmentation]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/02. Aggregation and Block Ack#tid-流量标识\|TID 流量标识]] |
| [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse\|OFDMA 调度与空间复用]] | [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse#触发帧-trigger-frame\|触发帧 Trigger Frame]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse#上行-ofdma-与-uora\|上行 OFDMA 与 UORA]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse#bsr-缓存状态报告\|BSR 缓存状态报告]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse#mumimo-调度\|MU‑MIMO 调度]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse#bss-color-bss-着色\|BSS Color BSS 着色]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse#obsspd-空间复用-spatial-reuse\|OBSS／PD 空间复用 Spatial Reuse]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse#协作空间复用-cosr\|协作空间复用 Co‑SR]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/03. OFDMA Scheduling and Spatial Reuse#txop-共享-txop-sharing\|TXOP 共享 TXOP Sharing]] |
| [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO\|多链路操作 MLO]] | [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO#mld-多链路设备\|MLD 多链路设备]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO#str-同时收发\|STR 同时收发]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO#nstr-非同时收发\|NSTR 非同时收发]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO#emlsr-增强多链路单射频\|EMLSR 增强多链路单射频]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO#emlmr-增强多链路多射频\|EMLMR 增强多链路多射频]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO#tidtolink-映射-ttlm\|TID‑to‑Link 映射 TTLM]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO#链路选择与负载均衡\|链路选择与负载均衡]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/04. Multi-Link Operation MLO#多链路重排序与安全\|多链路重排序与安全]] |
| [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/05. Wi-Fi 8 Access Enhancements\|Wi‑Fi 8 信道接入增强]] | [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/05. Wi-Fi 8 Access Enhancements#npca-非主信道接入\|NPCA 非主信道接入]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/05. Wi-Fi 8 Access Enhancements#dso-动态子带操作\|DSO 动态子带操作]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/05. Wi-Fi 8 Access Enhancements#低时延与优先接入\|低时延与优先接入]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/05. Wi-Fi 8 Access Enhancements#设备内共存-idc-indevice-coexistence\|设备内共存 IDC In‑Device Coexistence]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/05. Wi-Fi 8 Access Enhancements#ap-节能-ap-power-save\|AP 节能 AP Power Save]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/05. Wi-Fi 8 Access Enhancements#增强的-ba-与重传\|增强的 BA 与重传]] · [[Wireless Communication/02. WiFi Technology Atlas/06. Lower MAC/05. Wi-Fi 8 Access Enhancements#无缝漫游-smd\|无缝漫游 SMD]] |
%% atlas-terms end %%

## 产业链

| 环节 | 主要厂商 |
|---|---|
| MAC 硬件 / 固件 | Wi‑Fi 芯片厂商 |
| 调度算法差异化 | 设备商（Cisco、HPE、华为等）与芯片厂商共同实现 |
| 仿真工具 | ns‑3、Komondor / Kom8ndor |

延伸阅读：[[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/02. Chips|产业：芯片]] · [[Wireless Communication/01. WiFi Architecture/01. Academic Research#l6-lower-mac-信道接入|学术：信道接入／MLO]]
