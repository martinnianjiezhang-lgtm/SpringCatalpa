---
title: 基于 WiFi 架构的专题洞察
tags:
  - WiFi
  - 无线通信
---

以一条 Wi‑Fi 链路“从发到收”的全栈架构为主线，把**学术研究**、**产业格局**、**标准演进**三类信息挂到架构的每一层上。信息截至 2026‑09‑30。

| 部分 | 内容 |
|---|---|
| [[Wireless Communication/01. WiFi Architecture/01. Academic Research\|1）各技术领域最新学术研究]] | 天线 → FEM → 射频 → 混合信号 → PHY → MAC → 多 AP，以及芯片、感知、安全、AI、毫米波、低功耗六个跨层方向；每层列研究焦点、代表论文和跟踪入口 |
| [[Wireless Communication/01. WiFi Architecture/02. Industry Landscape\|2）设备商、芯片商、射频与天线厂商]] | 主芯片、射频前端、天线、企业与家庭设备、运营商 CPE、测试仪表；2026 年 Wi‑Fi 8 首批芯片与重大并购 |
| [[Wireless Communication/01. WiFi Architecture/03. Standards and Evolution\|3）标准组织、代际演进与新技术]] | IEEE 802.11 各 TG 进度、Wi‑Fi 4→8（→9）代际、Wi‑Fi Alliance / WBA / 频谱监管 |

## 交互架构图

点击任意一层展开：模块清单，以及跳到该层学术研究、产业和标准的链接。左列为发射链路（自上而下），右列为接收链路（自下而上）。

<div class="wa">
<div class="wa-head"><span>⬇ 发射 TX</span><span>架构层</span><span>接收 RX ⬆</span></div>

<details class="wa-layer" style="--wa-c:#6b7fd7">
<summary><span class="wa-tx">应用 → TCP/IP → WMM 映射</span><span class="wa-name">L8 主机、网络与多 AP<small>OS · 驱动 · 控制器 · Mesh</small></span><span class="wa-rx">GRO/NAPI → 应用</span></summary>
<div class="wa-body">
<ul>
<li>驱动模型：SoftMAC（cfg80211/mac80211）与 FullMAC（固件托管 MAC）；nl80211 ↔ hostapd / wpa_supplicant</li>
<li>网络侧：AC/云管理、EasyMesh 回传、漫游（11k/v/r）、802.11bn 多 AP 协作（Co‑BF / Co‑SR / Co‑TDMA / Co‑RTWT）与无缝漫游 SMD</li>
</ul>
<div class="wa-links"><a href="./01.-Academic-Research#l8-多ap与网络">学术：多 AP 与网络</a><a href="./02.-Industry-Landscape#4-设备商">产业：设备商</a><a href="./03.-Standards-and-Evolution#wi-fi-8-80211bn-uhr-关键技术">标准：11bn 多 AP</a></div>
</div>
</details>

<details class="wa-layer" style="--wa-c:#8a6bd7">
<summary><span class="wa-tx">加密 · A‑MSDU · 速率选择 · MLO 映射</span><span class="wa-name">L7 Upper MAC<small>连接 · 安全 · 调度</small></span><span class="wa-rx">解密 · 重排序 · 去重</span></summary>
<div class="wa-body">
<ul>
<li>认证与关联、WPA3‑SAE、CCMP/GCMP‑256、PMF</li>
<li>速率控制（Minstrel‑HT / 厂商算法 / 学习型）、TID‑to‑Link 映射、TWT/R‑TWT、SCS 低时延流</li>
</ul>
<div class="wa-links"><a href="./01.-Academic-Research#l7-upper-mac-与驱动">学术：Upper MAC</a><a href="./01.-Academic-Research#x3-安全与隐私">学术：安全</a><a href="./03.-Standards-and-Evolution#ieee-80211-任务组全景">标准：11bh / 11bi</a></div>
</div>
</details>

<details class="wa-layer" style="--wa-c:#b56bd7">
<summary><span class="wa-tx">EDCA 退避 · A‑MPDU · Trigger/OFDMA</span><span class="wa-name">L6 Lower MAC<small>信道接入 · 实时时序</small></span><span class="wa-rx">FCS · SIFS 回 BA · NAV / BSS Color</span></summary>
<div class="wa-body">
<ul>
<li>CSMA/CA、RTS/CTS、Block Ack、MU‑MIMO/OFDMA 调度、空间复用 SR</li>
<li>Wi‑Fi 7：MLO（STR / NSTR / EMLSR / EMLMR）、前导打孔；Wi‑Fi 8：NPCA、DSO、低时延指示</li>
</ul>
<div class="wa-links"><a href="./01.-Academic-Research#l6-lower-mac-信道接入">学术：信道接入 / MLO</a><a href="./03.-Standards-and-Evolution#代际演进">标准：代际</a></div>
</div>
</details>

<details class="wa-layer" style="--wa-c:#d76b9a">
<summary><span class="wa-tx">LDPC → QAM → 预编码 → IFFT + GI</span><span class="wa-name">L5 PHY 基带<small>OFDM(A) · MIMO · 编码</small></span><span class="wa-rx">同步 → 信道估计 → MIMO 检测 → LDPC 译码</span></summary>
<div class="wa-body">
<ul>
<li>发：加扰、LDPC/BCC、流解析、QAM（≤4096）、RU/MRU、CSD、波束成形预编码、前导（L‑STF/LTF/SIG、U‑SIG、EHT/UHR‑SIG）</li>
<li>收：分组检测、AGC、CFO/定时、FFT、MMSE/ML/球形译码、导频相位跟踪、LLR 软解调；CSI 同时供感知/定位使用</li>
<li>Wi‑Fi 8 新增：UEQM（非等调制）、DRU（分布式 RU）、ELR（远距 PPDU）、更长 LDPC 码字</li>
</ul>
<div class="wa-links"><a href="./01.-Academic-Research#l5-phy-基带">学术：PHY 基带</a><a href="./03.-Standards-and-Evolution#wi-fi-8-80211bn-uhr-关键技术">标准：11bn PHY</a></div>
</div>
</details>

<details class="wa-layer" style="--wa-c:#d7896b">
<summary><span class="wa-tx">上采样 · CFR · DPD → DAC</span><span class="wa-name">L4 混合信号与 DFE<small>ADC / DAC · 校准</small></span><span class="wa-rx">ADC → 抽取 · DC / IQ 校正</span></summary>
<div class="wa-body">
<ul>
<li>320 MHz 带宽 + 4K‑QAM 要求约 −38 dB 以下 EVM：DPD、IQ 失配、LO 泄漏、相噪预算</li>
<li>高速 ADC/DAC 功耗、片上自校准 MCU</li>
</ul>
<div class="wa-links"><a href="./01.-Academic-Research#l4-混合信号与-dfe">学术：DFE / 校准</a></div>
</div>
</details>

<details class="wa-layer" style="--wa-c:#d7b36b">
<summary><span class="wa-tx">正交上变频 · PLL/LO · PA driver</span><span class="wa-name">L3 射频收发机<small>2.4 / 5 / 6 GHz（/ 60 GHz）</small></span><span class="wa-rx">LNA → 混频 → 基带滤波 → VGA/AGC</span></summary>
<div class="wa-body">
<ul>
<li>多频段并发收发（MLO 需要多套射频）、低抖动小数分频 PLL、数字 PA / 极化发射</li>
<li>Wi‑Fi/BT/UWB/Thread 共存与自干扰；802.11bq（IMMW）42–71 GHz 射频</li>
</ul>
<div class="wa-links"><a href="./01.-Academic-Research#l3-射频收发机-rf-transceiver">学术：射频电路</a><a href="./02.-Industry-Landscape#1-主芯片">产业：芯片商</a></div>
</div>
</details>

<details class="wa-layer" style="--wa-c:#9ac26b">
<summary><span class="wa-tx">PA → T/R 开关 → 滤波</span><span class="wa-name">L2 射频前端 FEM<small>PA · LNA · 开关 · 滤波器</small></span><span class="wa-rx">滤波 → LNA(旁路) → 开关</span></summary>
<div class="wa-body">
<ul>
<li>5 GHz 与 6 GHz 之间的高陡度 BAW/LTCC 滤波、高线性 PA、iFEM 集成趋势</li>
<li>功率检测、温度补偿、SAR 回退</li>
</ul>
<div class="wa-links"><a href="./01.-Academic-Research#l2-射频前端-fem">学术：FEM</a><a href="./02.-Industry-Landscape#2-射频前端-fem-与滤波器">产业：FEM 厂商</a></div>
</div>
</details>

<details class="wa-layer" style="--wa-c:#6bc2a4">
<summary><span class="wa-tx">辐射</span><span class="wa-name">L1 天线<small>MIMO 阵列 · 方向图</small></span><span class="wa-rx">接收</span></summary>
<div class="wa-body">
<ul>
<li>终端：LDS/FPC/金属边框天线、多天线去耦；AP：智能/可重构天线、高增益定向天线</li>
<li>OTA 测试、天线选择与分集、与 RIS 的结合</li>
</ul>
<div class="wa-links"><a href="./01.-Academic-Research#l1-天线-antenna">学术：天线</a><a href="./02.-Industry-Landscape#3-天线">产业：天线厂商</a></div>
</div>
</details>

<div class="wa-channel">〰️ 无线信道：多径 · 衰落 · 多普勒 · 同频/邻频干扰 · 与 BT / LTE / NR‑U 共存 · 6 GHz 在网业务（AFC）〰️</div>

<div class="wa-arrow">跨层专题</div>
<div class="wa-cross">
<a href="./01.-Academic-Research#x1-芯片与soc">芯片与 SoC<small>AP SoC · Combo · NPU</small></a>
<a href="./01.-Academic-Research#x2-感知与定位">感知与定位<small>11bf · 11az · 11bk</small></a>
<a href="./01.-Academic-Research#x3-安全与隐私">安全与隐私<small>WPA3 · 协议攻击</small></a>
<a href="./01.-Academic-Research#x4-ai与ml">AI / ML<small>AI‑native Wi‑Fi</small></a>
<a href="./01.-Academic-Research#x5-毫米波与新频段">毫米波与新频段<small>11bq IMMW</small></a>
<a href="./01.-Academic-Research#x6-低功耗与环境能量">低功耗与环境能量<small>11bp AMP · 反向散射</small></a>
</div>
</div>

## 资源速查

| 类型 | 入口 |
|---|---|
| 标准一手资料 | [IEEE 802.11 工作组](https://www.ieee802.org/11/) · [各 TG 时间表](https://www.ieee802.org/11/Reports/802.11_Timelines.htm) · [Mentor 提案库（免费）](https://mentor.ieee.org/802.11/documents) · [IEEE GET 免费标准](https://ieeexplore.ieee.org/browse/standards/get-program/page) |
| 产业联盟 | [Wi‑Fi Alliance](https://www.wi-fi.org/) · [Wireless Broadband Alliance](https://wballiance.com/) |
| 论文检索 | [IEEE Xplore](https://ieeexplore.ieee.org/) · [ACM DL](https://dl.acm.org/) · [arXiv: 802.11bn](https://arxiv.org/search/?query=802.11bn&searchtype=all&order=-announced_date_first) · [dblp](https://dblp.org/) · [Google Scholar](https://scholar.google.com/) |
| 标准动态解读 | [Ofinno 802.11 Standards Readout](https://ofinno.com/topic/ieee/) · [Wi‑Fi NOW](https://wifinowglobal.com/) |
| 开源 / 实验 | [openwifi](https://github.com/open-sdr/openwifi) · [Nexmon CSI](https://github.com/seemoo-lab/nexmon_csi) · [ns‑3](https://www.nsnam.org/) · [OpenWrt](https://openwrt.org/) · [hostapd](https://w1.fi/) |

综述入门：Rice Networks Group [《Wi‑Fi: Twenty‑Five Years and Counting》](https://networks.rice.edu/files/2026/02/WiFi-25-years.pdf)（2026）
