---
title: WiFi 产业深度洞察（2025–2026）
tags:
  - WiFi
  - 厂商
  - 产业洞察
---

按 [[Wireless Communication/01. WiFi Architecture/index|WiFi 架构图]] 的层次，梳理 2025 年初到 2026 年 9 月的产业动态：芯片（L3–L8、SoC）、射频前端与天线（L1–L2）、设备商与运营商（整机与网络），以及贯穿全链路的政策、频谱和供应链。所有数据均来自公开报道和财报，链接附在各页。截至 2026‑09‑30。

| 专题页 | 内容 |
|---|---|
| [[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/01. Market\|① 市场与出货]] | 企业 WLAN 规模与份额、Wi‑Fi 7 渗透率（AP / 终端 / 手机）、中国家用路由格局 |
| [[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/02. Chips\|② 芯片]] | Wi‑Fi 8 首发芯片对比、Wi‑Fi 7 平台、终端自研（Apple N1）、IoT 与国产芯片 |
| [[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/03. RF Front-End and Antenna\|③ 射频前端、天线与测试]] | Skyworks + Qorvo 合并、康希通信与国产 FEM、天线厂商整合、Wi‑Fi 8 测试仪表 |
| [[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/04. Vendors and Operators\|④ 设备商与运营商]] | 企业 WLAN 整合（HPE–Juniper、Belden–Ruckus）、家用 Wi‑Fi 8 路由、运营商网关与 FTTR、Wi‑Fi 感知商业化 |
| [[Wireless Communication/01. WiFi Architecture/02. Industry Insight 2025-2026/05. Policy Spectrum and Supply Chain\|⑤ 政策、频谱与供应链]] | FCC 外国路由器禁令、欧 / 印 / 中 6 GHz 走向、存储芯片短缺、Wi‑Fi 8 认证时间、星闪 |

## 十条产业判断

1. **Wi‑Fi 7 已成为主流。** 2Q26 Wi‑Fi 7 占企业 WLAN 销售额的一半以上（Dell'Oro）；1Q26 占企业非独立 AP 收入的 44.5%，而两年前还不到 1%（IDC）。手机端，2025 年第三季度每 4 部出货的手机中约有 1 部支持 Wi‑Fi 7（Counterpoint）。Wi‑Fi Alliance 预计 2026 年 Wi‑Fi 7 设备出货约 11 亿台。
2. **Wi‑Fi 8 比标准早两年上市。** 芯片方面，MediaTek（2026 年 1 月 CES）、Broadcom（1 月 CES、5 月）、Qualcomm（3 月 MWC）已全部发布；路由器方面，ASUS（6 月 Computex）、TP‑Link（9 月 IFA，9 月 30 日开放预订）已推出成品。802.11bn 预计 2028 年批准，Wi‑Fi Alliance 认证定在 2028 年 1 月 CES。当前产品都是“预标准”，这是一代中芯片与认证间隔最长的一次。
3. **Wi‑Fi 8 的卖点从速率变成可靠性和 AI。** 各家宣传的重点是多 AP 协作（Co‑BF / Co‑SR）、NPCA、DSO、尾时延和漫游，再加上片上 NPU 或“AI‑native”调度（Broadcom BCM4918、Qualcomm Dragonwing、华为 iCSSR）。峰值速率不再是主角。
4. **企业 WLAN 加速整合。** HPE 收购 Juniper（2025 年 7 月完成）；CommScope 出售 CCS 业务后更名 Vistance（2026 年 1 月），又把 Ruckus 以 18.5 亿美元卖给 Belden（2026 年 7 月完成）。Cisco 以 38.9% 份额领先，Ubiquiti 增速最快（1Q26 同比 +29.1%）。
5. **终端 Wi‑Fi 芯片向垂直整合倾斜。** Apple 在 iPhone 17 系列用自研 N1 芯片（Wi‑Fi 7、BT 6、Thread）替换了 Broadcom；Intel 放弃分拆网络与边缘业务（NEX），保留 Wi‑Fi 网卡业务。独立芯片商的终端市场在收窄。
6. **射频前端在整合，国产 FEM 进入 Wi‑Fi 7 主流。** Skyworks 与 Qorvo 合并，企业价值约 220 亿美元，2026 年 9 月获得全部监管批准。康希通信 Wi‑Fi 7 产品收入占比超过 50%，2026 年上半年扭亏，并通过四大主芯片平台认证。
7. **地缘政治重塑消费级路由市场。** 2026 年 3 月 23 日，FCC 把所有外国生产的消费级路由器列入 Covered List，新机型无法取得 FCC 认证。TP‑Link 的 Wi‑Fi 8 路由也标注“待 FCC 批准”。
8. **6 GHz 全球分裂。** 美国开放了全部 1200 MHz；欧洲上 6 GHz 倾向分给移动通信（RSPG 建议 540 MHz 给移动、160 MHz 冻结到 WRC‑27）；印度 2026 年 1 月正式免许可下 6 GHz；中国 6425–7125 MHz 划给 IMT，2026 年 5 月又批准 6G 试验频率。因此在中国和欧洲，Wi‑Fi 8 的收益更多依赖 MLO、MAPC 和频谱效率，而不是更宽的信道。
9. **存储芯片短缺推高设备成本。** AI 数据中心挤占 DRAM 产能，DDR4 价格暴涨，据报道内存在路由器成本中的占比从约 3% 升到约 20%。Dell'Oro 指出，企业为避开涨价在提前下单。
10. **新收入来源成形。** 一是 Wi‑Fi 感知：ADT 以 1.7 亿美元收购 Origin AI，Cognitive 已授权给 120 多家 ISP。二是 IoT Wi‑Fi 7：Wi‑Fi Alliance 推出 20 MHz‑only 认证，Infineon 发布首颗 20 MHz Wi‑Fi 7 三模芯片。三是 HaLow：Morse Micro 完成 5900 万美元 C 轮融资，MM8108 已量产。

## 2025–2026 大事记

| 时间 | 事件 | 层次 |
|---|---|---|
| 2025‑04 | AT&T 推出 Wi‑Fi 7 家庭套餐 All‑Fi Pro | 运营商 |
| 2025‑05 | 印度发布下 6 GHz 免许可草案 | 频谱 |
| 2025‑07 | HPE 完成收购 Juniper | 设备商 |
| 2025‑09 | Apple iPhone 17 系列首发自研 N1 无线芯片 | 终端芯片 |
| 2025‑09 | Morse Micro 完成 5900 万美元 C 轮融资，MM8108 量产 | IoT 芯片 |
| 2025‑09 | IEEE 802.11bf（WLAN 感知）发布 | 标准 |
| 2025‑09 | LitePoint 推出 Wi‑Fi 8 测试方案 | 测试 |
| 2025‑10 | Skyworks 宣布与 Qorvo 合并 | 射频前端 |
| 2025‑11 | 欧盟 RSPG 发布上 6 GHz 意见，倾向移动通信 | 频谱 |
| 2025‑12 | Intel 放弃分拆 NEX | 芯片 |
| 2026‑01 CES | MediaTek Filogic 8000、Broadcom BCM6714/6719 + BCM4918、Infineon ACW741x、Espressif ESP32‑E22；Wi‑Fi Alliance 推出 20 MHz‑only Wi‑Fi 7 认证 | 芯片 / 认证 |
| 2026‑01 | CommScope 出售 CCS 业务后更名 Vistance Networks；印度正式免许可下 6 GHz | 设备商 / 频谱 |
| 2026‑02 | ADT 以 1.7 亿美元收购 Origin AI（Wi‑Fi 感知） | 新应用 |
| 2026‑03 MWC | Qualcomm 发布 FastConnect 8800 与 5 款 Dragonwing Wi‑Fi 8 平台；华为发布 Pre Wi‑Fi 8 AP；R&S 与 Broadcom 演示 Wi‑Fi 8 信令测试 | 芯片 / 设备 / 测试 |
| 2026‑03‑23 | FCC 将外国生产的消费级路由器列入 Covered List | 政策 |
| 2026‑04 | Belden 宣布收购 Ruckus（18.46 亿美元） | 设备商 |
| 2026‑05 | Broadcom 发布 BCM6772/74/76 路由 SoC 与 Wi‑Fi 8 + 50G PON 网关芯片；HPE 发布首款 Aruba / Mist 双平台 AP；工信部批准 6 GHz 频段 6G 试验频率 | 芯片 / 设备 / 频谱 |
| 2026‑06 | ASUS 发布 ROG Rapture GT‑BN98 Pro（Wi‑Fi 8）；Cisco Live 发布 Wi‑Fi 7 室外 AP 9177 | 设备 |
| 2026‑07 | Belden 完成收购 Ruckus；802.11bn D2.0 启动 WG 投票 | 设备商 / 标准 |
| 2026‑08 | Ubiquiti 公布 FY2026 营收 32.7 亿美元（+27%） | 设备商 |
| 2026‑09 | Dell'Oro：2Q26 Wi‑Fi 7 销售额过半；TP‑Link 在 IFA 发布 Wi‑Fi 8 全系列；Skyworks–Qorvo 获全部监管批准 | 市场 / 设备 / 射频 |

另见：[[Wireless Communication/01. WiFi Architecture/02. Industry Landscape|厂商名录]] · [[Wireless Communication/01. WiFi Architecture/03. Standards and Evolution|标准与代际]]
