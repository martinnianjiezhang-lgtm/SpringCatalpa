---
title: "B25 · DAY2 · Mo3-A-面向接入与AI集群的光子架构"
tags:
  - ECOC2026
  - DAY2
---

### 0921-Mo3-A1-iPronics-可编程光子在AI数据中心.pdf
- 讲者/机构：讲者姓名未见；iPronics | 题目：Photonics to scale AI datacenters（首页题；副标题未见） | 类型：产业发布/邀请报告
- 方向归属（主/次）：主 [3 Scale-out ... OCS]；次 [4 Scale-up/in ... OCS]
- 核心主张：
  1. 光互连在数据中心网络中占比持续上升（光纤、收发器、CPO），OCS 可缓解主要瓶颈并支持跨机架扩展计算域（结论页 p16）。
  2. 业界已能交付硅光光开关：高密度、高基数、亚毫秒重构（p16）。
  3. 系统设计兼容可插拔、NPO/光 I/O、光学中介层、CPO 等端到端模块（p15）。
- 关键数据：
  - OCS 用于 scale-up 扩展：紧凑（每 1U 3 或 4 台）、约 \$100/端口、亚毫秒重构 [p1]
  - 多数现有 OCS 方案每 1U 32–40 端口，组成 2/4/8U 机架单元 [p2]
  - ONE-32 芯片：严格无阻塞 32 端口、偏振透明、>4,000 集成开关单元、所有通道约 10 dB 损耗、兼容 WDM 光学、片上遥测 [p9]
  - 芯片代际：32x32 初代 约2,000 开关单元、20x23 mm²；32x32 v2 4,000 单元、偏振透明；64x64 6,000 单元、偏振透明、20x23 mm²；>100 端口约 10,000 单元、25x25 mm²，标注 2027、设计中 [p10]
  - 与 Lumentum 1.6 Tbps 2x DR4（200G/lane）重定时硅光收发器联测，OCS 增益设 10 dB，网络损耗仿真 VOA1 0–3 dB、VOA2 0–10 dB；相对 1e-12 基线 BER 劣化约 1 个数量级，对前后网络损耗稳健；典型工作窗口接收功率约 0 至 +4 dBm [p14]
  - 宣称链路成本降低 2x，嵌入链路增益与遥测，响应 µs 级（该页写 µs-time，含义未展开） [p15]
- 提到的公司/客户/产品/标准：Lumentum（收发器；Triple-Stone 320x320 OCS 也在 p2 列出）、POLATIS、Eoptolink、Gisun、Molex；iPronics ONE 系列；CW-WDM MSA、OCI-MSA（作为生态问题）
- 与业界对比或记录声明：自称 "Industry-first results of link-quality of 1.6 Tbps transceivers ... over gain-controlled silicon-photonics OCS" [p14]
- 推荐配图页：p14（OCS+Lumentum 1.6T 收发器 BER 曲线与测试框图）；p10（芯片代际路线）

### 0921-Mo3-A3-KDDIResearch-无DSP可插拔能否用于光交换.pdf
- 讲者/机构：Chenxiao Zhang, Han Wang 等（同等贡献），KDDI Research | 题目：Is DSP-Free Pluggable Optical Module Suitable for Optical Circuit Switching?（Mo3-A3） | 类型：学术论文
- 方向归属（主/次）：主 [3 Scale-out ... OCS]；次 [4 Scale-up/in ... OCS]
- 核心主张：
  1. OCS 插入不劣化 LPO 信号质量，LPO 链路恢复比 DSP 模块更快（p14）。
  2. OCS 重构对作业完成时间（JCT）无显著影响；在流量峰值切换会直接中断训练，应对齐零流量窗口（p14）。
  3. 在 H100 集群上演示了基于 LPO+OCS 架构的稳定 72 小时 LLM 预训练（p14）。
- 关键数据：
  - 动机：网络设备约占 20–30% 功耗；OCS 可减少 50% 收发器（每个 5–30 W）；32 端口 EPS 满载约 1000 W，OCS 30–100 W；LPO 比带 DSP 收发器功耗低约 40% [p2–p3]
  - 平台：96x96 MEMS OCS，Tomahawk 5 EPS，400G DR4 / 800G 2xDR4 LPO，2 节点各 2 张 H100，RoCE [p5]
  - Pre-FEC BER：各 lane 量级约 1e-8（纵轴最高 6.0E-08），8 条 lane 中仅 3 条略升，无量级差异 [p7]
  - 端到端时延：RX1(lane1–4) LPO 203.9 ns → LPO+OCS 290.48 ns；RX2(lane5–8) 192.93 → 238.45 ns；增加数十 ns，lane 间不均，RX1/RX2 差约 10 ns [p8]
  - 链路建立时间（关闭自协商，固定速率与 FEC）：800G 2xDR，DSP 箱线约 4.7–8.8 ms（均值约 6.2 ms，图读数），LPO 约 4.1–6.9 ms（均值约 5.2 ms，图读数） [p10]
  - JCT（Qwen2.5-1.5B 预训练，数据量里程碑 100/400/1600/6400 GB，OCS 不重构）DSP vs LPO：58.6 vs 49.8 s；192.0 vs 183.2 s；774.2 vs 753.5 s；3052.6 vs 3042.8 s；节省数十秒，训练越长越不明显 [p12]
  - 重构策略（基线 LPO 绕过 OCS / 随机 / 周期）：6400G 里程碑 约 3042.8 s（周期）、3012.1（随机）、2982.3（基线）（图读数）；两种策略均无显著影响；GPU 计算阶段零流量窗口 100–400 ms；随机切换易中断作业，周期切换稳定 [p13]
- 提到的公司/客户/产品/标准：NVIDIA H100、Broadcom Tomahawk 5（图中标注）、RoCE、Qwen2.5-1.5B、LPO、IEA（Energy and AI 数据）
- 与业界对比或记录声明：自称首次给出 LPO+OCS 全栈验证；72 小时稳定预训练演示 [p14]
- 推荐配图页：p13（JCT 重构策略与零流量窗口）；p8（时延对比）；p12（DSP vs LPO JCT）

## 本批小结
1. OCS 正被定位为 AI 网络 spine/scale-up 扩展层的低功耗替代：iPronics 讲 ~\$100/端口、亚 ms 重构（iPronics p1），KDDI 讲 OCS 可省 50% 收发器与大幅降交换功耗（KDDI p3），两篇论证一致。
2. 硅光 OCS 正向高基数演进：iPronics 芯片从 32 口（约 10 dB 损耗）到 64 口，>100 口计划 2027（iPronics p9–p10）；损耗需增益控制补偿。
3. OCS 与免 DSP/低时延模块兼容性已获实测：Lumentum 1.6T 收发器 BER 约降 1 个数量级（iPronics p14）；LPO 经 OCS 后 pre-FEC BER 无量级变化（KDDI p7）。
4. OCS 的代价在于时延与重构时机：LPO+OCS 增加数十 ns（KDDI p8），需对齐 GPU 计算阶段 100–400 ms 零流量窗口（KDDI p13）。
5. 生态尚未定型：iPronics 提出 CW-WDM MSA、OCI-MSA、波长数/栅格等未决问题（iPronics p15）。
