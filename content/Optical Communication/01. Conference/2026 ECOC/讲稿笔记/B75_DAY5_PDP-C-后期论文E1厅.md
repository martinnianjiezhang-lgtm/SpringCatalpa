---
title: "B75 · DAY5 · PDP-C-后期论文E1厅"
tags:
  - ECOC2026
  - DAY5
---

### 0924-PDP-C-1-AIT奥地利技术研究院-单片QKD发射机实现光与无线融合的QKD交换.pdf
- 讲者/机构：Florian Honz, W. Boxleitner, M. Ferreira-Ramos, M. Hentschel, H. Hübel, Bernhard Schrenk（AIT Austrian Institute of Technology；Ferreira-Ramos 现属 Infineon Austria） | 题目：Optical Fi-Wi QKD Exchange with Monolithic QKD Transmitter | 类型：学术论文（PDP-C-1，Malaga，9月24日）
- 方向归属（主/次）：主 6 QKD/量子；次 5 固定与无线接入（RoF/Fi-Wi，FR3/FR2）
- 核心主张：
  1. 全硅单片 QKD 发射机（片上 SiGe 光源 + BB84 偏振编码器），无需 III-V 激光器，适合手持/低成本集成 [p16]
  2. 端到端光-无线 + 光纤前传可行：30 cm 自由空间链路 + 最长 32 km 前传，兼容 O-RAN 7.2 拆分单向极限，无需中间可信节点 [p16]
  3. 可与 Fi-Wi 射频光载无线（RoF）信号共存 [p16]
- 关键数据：
  - SiGe 正向偏置 PIN（SOI）光源：偏置电流 10…30 mA，正向电压 <2.5 V；LED 式 C 波段发射；25 mA 下总出光 -66.9 dBm；25–80 °C 稳定；连续工作 >13 天无退化；可直接调制 200 MHz [p6]
  - 偏振编码器 H,V,R,L，符号率 100 Mbaud；焦平面阵列（FPA）波束成形，91 个 SMF 芯天线单元，35 µm 间距，插损 1.6 dB；自由空间 30 cm [p8]
  - 光预算 13.2 dB，SMF 0.25 dB/km 且计入 5.2 dB FSO 损耗时约 32 km；FPA 相对单 SMF 改善 0.8 dB 耦合；光源限制 μ=0.015 光子/符号（Δν=200 GHz）；相对外部光源无性能代价 [p11]
  - 80 °C 工作：发射功率降约 1 dB，QBER 代价 1.3%；温升致耦合变差，手动重对准可将 QBER 恢复到 7% [p11]
  - 光源带宽/去偏振：Δλ=16 nm 仅 4.9 km，10 nm 仅 9.2 km；Δλ=1.6 nm 无去偏振代价，单 SMF OHS 27.2 km，FPA OHS 32 km；Δλ=5 nm 时 36.5 km（OCR）；最优约 4 nm（OCR）[p12–p13]
  - WDM：1531.1–1576.2 nm 间最多 29 个 200 GHz 信道，15.2 km SMF；27 个信道产生的密钥足以按 TLS 1.3 / AES-GCM-256 保护 1 Tb/s [p13]
  - 共存实验：5 Gb/s RoF，下行 1305.98 nm、上行 1309 nm，光子上变频到 21 GHz（下行）/27 GHz（上行）；14.3 km 双馈线 + 512 m 共享分支光纤；QKD 通道 Δλ=1.6 nm，1550.12 nm [p14]
  - 经典信号功率达 -18 dBm 时仍有正 SKR；QBER 极限 11% 前共存裕量 3.8 dB；BER 10^-3（图中标注）：SOA+PIN -27.4 dBm，APD -28.3 dBm [p15]
- 提到的公司/客户/产品/标准：O-RAN 7.2 拆分；TLS 1.3 / AES-GCM 256；EFEC；欧盟 Horizon Europe / SNS JU 项目（6G 资助）；QOSILICIOUS 项目；Infineon（关联）
- 与业界对比或记录声明：称“全硅、无 III-V”的单片 QKD 发射机；相对外部光源发射机无性能代价（光功率受限除外）[p11, p16]
- 推荐配图页：p11（光预算与 QBER/RKR 曲线、温度依赖）；p13（WDM 信道数与去偏振对前传距离的影响）

### 0924-PDP-C-5-NokiaBellLabs-双单边带传输实现340ps每nm色散容限的单波超速率200G直检PON下行.pdf
- 讲者/机构：M. Adib 等（Nokia Bell Labs） | 题目：Dual single-sideband transmission for 340 ps/nm CD tolerance, single-wavelength 200G direct-detection PON downstream（页面无完整英文题名，据文件名与内容推断；p1 OCR 乱码，未看图） | 类型：学术论文（PDP-C-5）
- 方向归属（主/次）：主 5 固定与无线接入（PON）；次 3 调制器/直检
- 核心主张：
  1. 200 Gb/s DD-PON 面对 GPON 共存需要高色散容限，使用双波长会增加硬件复杂度 [p16]
  2. 方案：单波长 Dual-SSB 传输，接收端光学分离两个边带；O/E 波段用 Dual-SSB，C 波段用 Dual-SSB + CD 预补偿 [p16]
  3. 概念验证：“首个单波长 200 Gb/s 服务速率直检 PON” [p16]
- 关键数据：
  - 运营商诉求：100–200 Gb/s 系统服务容量，>30 dB ODN 损耗，20–30 km，兼容遗留系统 [p2]
  - 波长方案色散需求：约 50 / 120 / 350 ps/nm 分别对应 WP-A / WP-B / WP-C；GPON 共存要求 CD 容限 ≥120 ps/nm [p3]
  - 发射机：单激光器 + 单双驱 MZM，两臂分别 d1+d2 与 H{d1}-H{d2}；USB 与 LSB 承载独立信息；简单 ONU 收单边带（100 Gb/s），高端 ONU 收双边带（200 Gb/s）[p6]
  - 实验：AWG 224 GS/s（带宽 55 GHz）；激光线宽 100 kHz、8 dBm；DD-MZM 40 GHz；预放 EDFA 增益 25 dB；可编程光滤波器插损 7 dB；SOA-filter-PIN 接收；RTO 256 GS/s（带宽 42 GHz）；需 MLSE；DCPC 128 tap，Hilbert 滤波器 65 tap（可缩减到 17 tap）[p8]
  - B2B：单 SSB（112 Gb/s）与 DSB 性能相近；224 Gb/s Dual-SSB 相对单 SSB 约 6 dB 功率代价；BER 参考线约 2e-2；激光与滤波器 ±3 GHz 失准对灵敏度影响约 ±1 dB [p11–p12]
  - 224 Gb/s Dual-SSB：170 ps/nm CD 容限 @3.5 dB 代价，可用于上 O 波段/下 E 波段 [p13–p15]
  - 静态 DCPC 170 ps/nm：CD 范围 0–340 ps/nm，损耗预算 33 dB（图中约 33.4–35.1 dB，无 CD 时 ≈36 dB），可用于 C 波段 [p15]
  - 后补偿（>500 ps/nm）需 KK 场重建，ONU 复杂度上升；预补偿（>500 ps/nm）需链路 CD 信息、突发下行/ONU 分组 [p14–p15]
- 提到的公司/客户/产品/标准：ITU-T（G.hsp，OCR 不清）、FSAN、GPON/XG-PON、V. Houtsma（Su4-F）、C. Fallner（MoS-G）相关引用
- 与业界对比或记录声明：首个单波长 200 Gb/s 服务速率直检 PON [p16]
- 推荐配图页：p15（不同补偿方案下损耗预算 vs CD）；p11（224G Dual-SSB 与 112G 单 SSB/DSB 的 BER-ROP）

### 0924-Th1-A2-EpiPhotonics-外延PLZT马赫曾德尔调制器低VpiL低损耗高速.pdf
- 讲者/机构：Keiichi Nashimoto、Kazuhide Harada（EpiPhotonics Corp，日本；EpiPhotonics USA） | 题目：Epitaxial PLZT Mach–Zehnder Modulators with Low Vπ·L, Low Loss, and High-Speed Operation | 类型：学术论文（Th1-A2）
- 方向归属（主/次）：主 3 调制器；次 5 接入（高分光比 PON）
- 核心主张：
  1. 关键难点是同时实现低 Vπ·L 与低损耗；TFLN 带宽>100 GHz 但效率/直流漂移受限，BTO 损耗与重复性差，多晶 PLZT 损耗大、EO 响应弱 [p3]
  2. 用固相外延（SPE，旋涂无真空）在蓝宝石上生长单取向 PLZT（110）薄膜，兼顾低损耗与高 EO 系数 [p4–p6]
  3. 优化直电极后模型预测 3 dB EO 带宽约 60 GHz [p17]
- 关键数据：
  - 传播损耗 0.83–0.95 dB/cm（线性拟合，1550 nm，PLZT 厚 827 nm，波导宽 2.0 µm）；片上损耗 0.7 dB；耦合损耗 7.2 dB/面（模式失配 6.0 + 菲涅耳 0.2 + 熔接 0.3 + 间隙 0.7 dB）；加锥形 I/O 可降到 3.8 dB/面，总插损约 8.3 dB [p9–p11]
  - 蚀刻侧壁粗糙度 1 nm rms；折射率 PLZT 约 2.44（1550/1310 nm）[p4, p7]
  - 推挽直 MZ：电极长 1 或 2 mm，电极间距 12 或 18 µm，芯片长 0.8 cm [p8]
  - DC 扫描（PLZT 厚 1.2 µm，2 mm 电极）：最小 Vπ 1.05 V，Vπ·L 0.21 V·cm，有效 r 346 pm/V，跨器件可重复 [p13]
  - 输入光功率 30 dBm 下稳定 25 小时量级（横轴至约 25 h），输出 >20 dBm；功率下降归因于波导-光纤耦合界面而非 PLZT [p12]
  - 频响（片上 25 Ω 端接电阻，探针测量）：3 dB 约 25 GHz，40 GHz 内约 6 dB 以内，有峰化 [p15]；模型预测优化电极后 3 dB 约 60 GHz、6 dB 约 80 GHz [p17]
- 提到的公司/客户/产品/标准：TFLN、BTO、多晶 PLZT 对比；高分光比 PON 应用；无具体客户
- 与业界对比或记录声明：据讲者“据我们所知”：Vπ·L 0.21 V·cm 配合 0.9 dB/cm 损耗，有效 EO 系数 346 pm/V 超过已报道 TFLN、BTO、多晶 PLZT [p14]
- 推荐配图页：p14（Vπ·L 与损耗/有效 r 的平台对比图）；p13（DC 扫描 Vπ 提取）

## 本批小结
1. 三篇本批新增讲稿（另 PDP-C-6 Nokia/港理工按要求跳过），均为 ECOC 2026 后期论文/新型器件，共同特点是“用简化器件换系统复杂度”：单片硅 QKD 发射机（AIT）、单激光器+单调制器的单波 200G PON（Nokia）、外延 PLZT 调制器（EpiPhotonics）。
2. 接入网向 200G 直检演进（Nokia PDP-C-5）：核心矛盾是 GPON 共存所需的 ≥120 ps/nm CD 容限；Dual-SSB 给出 170 ps/nm，加静态 DCPC 扩至 0–340 ps/nm，将复杂度推向 OLT 侧（来自 Nokia）。
3. 量子密钥分发正与光/无线接入融合（AIT）：QKD 与 5 Gb/s RoF 在同一前传共存，前传距离受光源带宽与去偏振限制（Δλ=1.6 nm 时 32 km，与 O-RAN 7.2 单向极限对齐）。
4. 新型电光材料争夺“低 Vπ·L + 低损耗”：PLZT 报 0.21 V·cm、0.9 dB/cm，但耦合损耗 7.2 dB/面与约 25 GHz 带宽（预测 60 GHz）说明离 >100 GHz 高速应用仍有距离；讲者点名高分光比 PON 作为适用场景（EpiPhotonics；与 Nokia PON 主题弱关联）。
5. 三篇均给出“在受限器件条件下的实测边界”而非绝对指标：如 AIT 的 μ=0.015 光子/符号光源限制、80 °C 需重对准，Nokia 的 Dual-SSB 6 dB 代价（AIT、Nokia）。
