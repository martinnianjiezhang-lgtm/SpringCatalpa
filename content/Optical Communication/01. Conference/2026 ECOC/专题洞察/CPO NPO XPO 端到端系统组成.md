---
title: "CPO / NPO / XPO 端到端系统组成与实物标注"
tags:
  - 光互连
  - 专题洞察
  - ECOC2026
  - CPO
  - NPO
  - XPO
date: 2026-10-06
---

从发端 ASIC 到收端 ASIC 拆成 8 个子系统，在 CPO、NPO、XPO 的实物图上按编号标出每个子系统的物理位置。实物图优先用厂商或媒体公开的高清图，缺少公开图的部分用 ECOC 2026 现场照片。

> [!tip] 交互版
> [打开交互版页面](https://springcatalpa.pages.dev/static/cpo-npo-xpo-system-interactive.html)：鼠标悬停在图上的编号可以看说明。

## 子系统编号

| 编号 | 子系统 | 编号 | 子系统 |
|---|---|---|---|
| ① | ASIC / SerDes | ⑤ | 光源（ELS 外置 / ILS 内置） |
| ② | 主机电通道 | ⑥ | 光耦合（FAU / 微透镜） |
| ③ | EIC：DRV / TIA（/DSP） | ⑦ | 光纤 / 连接器 / 前面板 |
| ④ | PIC：调制器 / PD | ⑧ | 散热与供电 |

## 端到端链路与三种形态的封装边界

![[cpo-npo-xpo-e2e-chain.svg]]

色块表示每种形态里哪些子系统被封装在一起、作为一个可更换单元；收端与发端镜像对称。

## CPO 共封装光学

- 光引擎与交换 ASIC 共处一个封装基板；EIC 与 PIC 用 TSMC COUPE 3D 堆叠，微环调制器，200G/lane
- 电通道 <5 dB（NVIDIA 称约 4 dB）→ 不需要 DSP；约 4 pJ/b；激光器数量是可插拔的 1/4，激光可靠性提升 10×【自报】
- 激光外置：ELS 模块插在前面板，经保偏光纤送光；光纤用可拆卸连接器接到光子交换封装
- 整机实例 Quantum-X Photonics Q3450-LD：115.2T、4U、液冷、48 V 母排；18 个 ELS（每个 8×200 mW DFB）+ 144 个 MPO 口；Quantum-X 每个 OSA 由 3 个 1.6T 引擎组成（4.8T）
- 博通路线：TH6-Davisson 102.4T = ASIC + 16 个 6.4T Davisson DR 光引擎（COUPE），已出货，称功耗降低 >70%；第 4 代 2028；CPO >1M 器件小时 0 link flap【自报】
- 短板：不能热插拔、故障需系统级更换；32 个光引擎的总良率问题（单个 95% 时总良率约 19%，华为测算）

![[cpo-npo-xpo-nvidia-spectrum-quantum-x-cpo.jpg]]

**NVIDIA Spectrum-X（左）与 Quantum-X（右）Photonics CPO 封装**（网络高清图；来源：[NVIDIA 新闻稿官方产品图](https://nvidianews.nvidia.com/news/nvidia-spectrum-x-co-packaged-optics-networking-switches-ai-factories)）

- **①** Spectrum-X 交换 ASIC
- **③④** ASIC 四周的硅光引擎（EIC 叠在 PIC 上，TSMC COUPE）
- **③④** 硅光引擎（200G 微环调制器）
- **②** 封装基板：ASIC 与光引擎之间的电通道 <5 dB
- **①** Quantum-X 交换 ASIC
- **③④⑥** 可拆卸光学子组件 OSA（3 个 1.6T 引擎 = 4.8T）
- **⑥⑦** OSA 光纤出口

![[cpo-npo-xpo-broadcom-th6-davisson-cpo.jpg]]

**博通 TH6-Davisson 102.4T CPO 封装**（网络高清图；来源：[ServeTheHome 转载博通官方图](https://www.servethehome.com/broadcom-tomahawk-6-davisson-102-4t-switch-with-co-packaged-optics-shipping/)）

- **①** Tomahawk 6 交换 ASIC（102.4T）
- **③④** Davisson 6.4T DR 光引擎 ×16（TSMC COUPE）
- **③④** 光引擎（每侧 4 个）
- **⑥⑦** 光引擎外端的光纤接口（推断）
- **②** 封装盖板 / 基板

![[cpo-npo-xpo-nvidia-q3450-front.jpg]]

**NVIDIA Quantum-X Photonics Q3450-LD 前面板（115.2T，4U，液冷）**（网络高清图；来源：[Lambda 博客实拍](https://lambda.ai/blog/unbox-one-of-nvidias-first-co-packaged-optics-samples-with-lambda)）

- **⑤** 18 个外置激光模块 ELS（前面板插拔，每个 8 颗 200 mW DFB）
- **⑦** 144 个 MPO 光口，取代 OSFP 笼子
- **⑤** ELS 模块
- **⑦** MPO 光口

![[cpo-npo-xpo-nvidia-q3450-rear.jpg]]

**Q3450-LD 后面板：48 V 母排供电**（网络高清图；来源：[Lambda 博客实拍](https://lambda.ai/blog/unbox-one-of-nvidias-first-co-packaged-optics-samples-with-lambda)）

- **⑧** 48 V 直流母排供电接口（后面板另有 UDQ4 液冷快接头）

![[cpo-npo-xpo-nvidia-cpo-exploded.jpg]]

**NVIDIA CPO 系统爆炸图（Spectrum-X / Quantum-X Photonics）**（ECOC 2026 现场照片；来源：DAY1 Su3-A-05 NVIDIA p12）

- **③** Electronic IC（EIC：DRV/TIA）
- **④** Photonic IC（PIC：微环调制器+Ge PD）
- **③④** EIC与PIC 3D堆叠（TSMC COUPE/SoIC）
- **⑥** COUPE 微透镜 + 表面耦合
- **⑦** 可拆卸光纤连接器
- **⑥⑦** 光学子组件（FAU/光纤）
- **⑤** 外置激光源模块 ELS（前面板插拔）
- **⑤** 激光源封装
- **①②** CPO 光子交换封装：ASIC + 光引擎同基板，电通道约4 dB
- **②** 中介层/封装基板
- **⑦** 前面板：光纤连接器 + ELS 槽位

## NPO 近封装光学

- 光引擎放在主机板上靠近 ASIC，通过 Open CPX Type-1 socket（6.4T，32×200G）连接，可单独更换
- TeraHop Diablo-1：6.4T，内置激光（ILS），实测 33.2 W，<5.5 pJ/b；ASIC 到 NPO 约 12 dB【自报】
- 集成光纤尾纤，单模光纤束直接到前面板：不需要 ELSFP，也不需要额外保偏光纤；配专用液冷冷板
- Open CPX 1.0（2026-09-16）：Type-1 6.4T、Type-2 7.2T，最高 212.5G/lane，ILS 与 ELS 都可；2027 年 ramp
- 同类：NewPhotonics NPC50506 6.4T DR32 内置激光 NPO；Coherent 6.4T SiPh NPO 3.5 pJ/b；华为 Hi-ONE 7.2T（36×224G）称已量产【自报】

![[cpo-npo-xpo-terahop-diablo1-npo-board.jpg]]

**Arista 100T 交换机设计概念 + TeraHop 6.4T Diablo-1 Open CPX NPO（内置激光）**（ECOC 2026 现场照片；来源：DAY3 市场聚焦连拍 p60（TeraHop））

- **①** 交换 ASIC（冷板下方）
- **②** 主机 PCB 电通道：ASIC→NPO 约 12 dB
- **③④⑤** Diablo-1 6.4T NPO 引擎 ×4（EIC+PIC+内置激光）
- **③④⑤** NPO 引擎
- **⑥** 集成光纤尾纤（无可插光接口）
- **⑦** SMF 光纤束 → 前面板（无保偏光纤）
- **⑦** 前面板光 I/O（无 ELSFP）
- **⑧** NPO 专用液冷冷板管路（推断）

![[cpo-npo-xpo-newphotonics-6t4-npo-engine.jpg]]

**NewPhotonics NPC50506 6.4T DR32 内置激光 NPO 光引擎**（网络高清图；来源：[Converge Digest 转载厂商图](https://convergedigest.com/newphotonics-6-4t-npo-optical-engine-open-cpx/)）

- **⑥⑦** 光纤尾纤（光纤带直接引出）
- **⑥** 光纤阵列与 PIC 的耦合区（推断）
- **③④⑤** 硅光 PIC + EIC + 集成激光（视窗可见芯片）
- **②** 底部电接口，接主机板（推断）

![[cpo-npo-xpo-terahop-opencpx-engine.jpg]]

**TeraHop 6.4T Open CPX 光引擎特写：socket 可更换**（ECOC 2026 现场照片；来源：同上 p57）

- **③④⑤** 硅光引擎 + 集成激光源（ILS）
- **②** Open CPX Type-1 连接器（socket，6.4T）
- **⑥⑦** 光纤尾纤
- **①** 主机板（ASIC 侧）

## XPO 超密度可插拔

- 一个 XPO 可替换 8 个 OSFP：两块相同的 32 通道 paddle card 背靠背装在中心冷板两侧，每块 6.4T
- 每块卡集成 4 颗八通道 DSP + PIC + TIA，并配 4×MPO-16；48 V 直接供电；TX 与 RX 分放两侧以降低串扰
- 实测 64×212G PAM4：TX 平均光功率 2.75 dBm、ER 4.33 dB、TDECQ 2.39 dB；RX 灵敏度 −7~−7.5 dBm OMA @2.4e-4
- 液冷：DSP 约 50–74 °C、CW 激光约 36–57 °C；模块约 130 W（约 10 pJ/b，LRO），LPO 版约 6 pJ/b
- XPO MSA 1.0（2026-07-31），150 家成员，2027Q1 量产；448G 卡边连接器仿真在约 90 GHz 处插损 <1 dB（PAM6）

![[cpo-npo-xpo-arista-xpo-vs-osfp.jpg]]

**Arista XPO 12.8T 模块与 8 个 OSFP 对比（一个 XPO 替代 8 个 OSFP）**（网络高清图；来源：[Arista XPO 白皮书图 1](https://www.arista.com/assets/data/pdf/Whitepapers/XPO-Whitepaper.pdf)）

- **⑦** 前端：拉环与光口（每块 paddle card 配 4×MPO-16）
- **③④⑤** 壳内：两块 32 通道 paddle card（八通道 DSP + PIC + TIA + CW 激光）
- **②** 卡边高速连接器 → 主机板（推断）
- **⑧** 液冷进出管（推断）

![[cpo-npo-xpo-arista-xpo-exploded.jpg]]

**Arista 12.8T XPO 模块架构（8×DR8，64×212G PAM4，液冷可插拔）**（ECOC 2026 现场照片；来源：We5-B3 Arista p3）

- **③④** Paddle card-1：4×八通道 DSP + PIC + TIA（32ch，6.4T）
- **⑤** CW 激光（模块内置，DR8 硅光）
- **②** 卡边金手指 → 主机电通道（约 22 dB 级，需 CPC/PAM6）
- **⑥⑦** 光连接器：每卡 4×MPO-16
- **⑧** 中心冷板（两卡背靠背共享）
- **⑧** 液冷进出口
- **⑧** 48V 供电与通信卡
- **③④** Paddle card-2（另 32ch）
- **⑦** 装配后模块：前面板插拔

## 三种形态逐子系统对比

| 子系统 | CPO | NPO | XPO |
|---|---|---|---|
| ② 主机电通道 | 封装基板，<5 dB | PCB + socket，7–12 dB | PCB / 飞线铜缆，约 22 dB 级 |
| ③ EIC | CMOS EIC 3D 堆叠，线性，无 DSP | 线性（LPO）或重定时（LRO） | 八通道 DSP + TIA（LRO），或线性版 |
| ④ PIC | 硅微环 + Ge PD | 硅光 MZM / VCSEL 阵列 | DR8 硅光，或 EML / TFLN |
| ⑤ 光源 | 外置 ELS（前面板） | 内置 ILS 或外置 ELS | 模块内置 CW 激光 |
| ⑥ 光耦合 | COUPE 微透镜，表面耦合 | 集成光纤尾纤 | 模块内部耦合 |
| ⑦ 光纤 / 连接器 | 可拆卸光纤连接器 + 保偏光纤 | 单模光纤束到前面板 | MPO-16 ×8（前面板） |
| ⑧ 散热与供电 | 交换机整机散热 | NPO 专用液冷冷板 | 中心冷板液冷，48 V |
| 可更换单元 | 整个交换封装 | 单个 NPO 引擎（socket） | 前面板热插拔模块 |
| 能效【自报】 | 约 3–4 pJ/b | 3.5–5.5 pJ/b | 6–10 pJ/b |

> [!note] 口径
> 【自报】为厂商幻灯片数字，核算边界不同，不能直接横比。标“推断”的位置是根据讲稿或报道文字推断，原图上没有标注。图片版权归各厂商或媒体。

## 相关笔记

- [[方向4 Scale Up 综合洞察]]：CPO/NPO/XPO 的形态时间线、能效、可靠性与标准
- [[Optical Communication/01. Conference/2026 ECOC/专题洞察/光通信专业地图（五层光互连）|光通信专业地图（五层光互连）]]

## 来源

- ECOC 2026 现场讲稿：DAY1 Su3-A-05 NVIDIA；DAY3 市场聚焦连拍 p57、p60（TeraHop）；We5-B3 Arista
- [Lambda：Unbox NVIDIA CPO switch](https://lambda.ai/blog/unbox-one-of-nvidias-first-co-packaged-optics-samples-with-lambda)
- [NVIDIA 新闻稿：Spectrum-X Photonics](https://nvidianews.nvidia.com/news/nvidia-spectrum-x-co-packaged-optics-networking-switches-ai-factories)
- [ServeTheHome：Broadcom TH6-Davisson](https://www.servethehome.com/broadcom-tomahawk-6-davisson-102-4t-switch-with-co-packaged-optics-shipping/)
- [Converge Digest：NewPhotonics 6.4T NPO](https://convergedigest.com/newphotonics-6-4t-npo-optical-engine-open-cpx/)
- [Converge Digest：Open CPX at Hot Interconnects](https://convergedigest.com/open-cpx-msa-socketed-optics-ai-scale-up/)
- [Arista XPO 白皮书](https://www.arista.com/assets/data/pdf/Whitepapers/XPO-Whitepaper.pdf)
- [NADDOD：NVIDIA Silicon Photonics CPO](https://www.naddod.com/ai-insights/nvidia-s-silicon-photonics-cpo-the-beginning-of-a-transformative-journey-in-ai)
