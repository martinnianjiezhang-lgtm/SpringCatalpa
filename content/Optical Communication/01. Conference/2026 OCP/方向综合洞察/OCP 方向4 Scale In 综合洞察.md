---
title: "OCP 方向4 Scale In 综合洞察"
tags:
  - OCP2026
  - 综合洞察
---

# 方向4：Scale-in——封装内与内存层级（Open Chiplet Economy、UCIe/BoW/GLink 等 D2D、2.5D/3D 封装与热、封装内光 I/O、HBM、CXL 内存池化/KV cache 卸载/PNM、SCM）

素材范围：by_direction/In.md（主归属 33 篇、次归属 27 篇），补读 notes/R15、R19、R12 中与封装内光 I/O 相关的 P338、P339、P340、P342、P345、P286、P436、P440。索引〔Pxxx pN〕；文末附索引对照表。口径标注：自报、仿真、实验、现网、预测、引用（注明来源）、看图、存疑。GO 的 P279 与 P321 为同一讲稿两个 track 版本，合并引用为〔P321〕。

---

## 0. 一句话结论 + 5 条核心判断

**一句话结论：** OCP 2026 的 scale-in 讨论，重心从"封装里能塞多少算力"移到"内存放在哪里、怎么连"。KV cache 让 HBM 同时卡在容量、成本和热上，于是出现三条并行出路：向上把 warm KV 放到 CXL/PCIe/UALink 挂接的机柜级内存池，向内做定制 HBM base die、混合键合 DRAM-on-Compute 和低功耗私有 D2D，向外用面阵或宽慢光 I/O 绕开 shoreline。OCE 标准工作也随之从 PHY 转到系统层（固件、安全、互操作验证）。目前多数收益数字是厂商自报或实验，现网数据只有 Meta 一家。

**判断1：KV cache 把内存层级的扩展单位从"每 GPU 的 HBM"推到"机柜级共享池"；CXL 池化的实测收益主要来自容量，同容量下与 CPU DRAM 持平。**
- 容量压力（自报）：64 并发 × 32K 上下文时 KV 占 HBM 57%，Qwen3-235B 的 KV 约 384 GB，超过 235 GB 权重〔P057 p2〕；128K 上下文下 2 个用户即填满 80 GB HBM〔P275 p7〕；Nallasway 示意单服务实例内存 2020 年 0.4 TB → 2026 年 agentic 5 TB，其中 KV 约 3 TB（看图，数量级）〔P450 p2〕。
- 收益机制是"避免重算"而非"更快的介质"：Astera 同容量（每实例 128 GB）下 fabric 内存与 CPU DRAM 曲线几乎重合，fabric 侧容量为 2–3 倍时才出现"x2/x3 better"（实验，看图）〔P059 p6, p7, p8〕；Samsung 在 KV 超出 RDIMM 容量后，RDIMM 方案吞吐降到约 17%，CXL 池保持约 95%（5.6×，实验）〔P060 p8〕；Micron 模型显示 KV 层容量 400→600 GB 时 TTFT 从约 13 s 跳到约 1.5 s，过阈值后容量作用很小（实验，看图）〔P062 p12〕。
- 现网证据只有 Meta：CXL 扩展使缓存类吞吐 +25%、开发机每服务器 VM +33%、舰队规模 −15%、ML 参数服务器数 −25%（现网，自报）〔P058 p15〕。
- 架构上各家都把池子放在 HBM 之下、SSD 之上：SK hynix MARS 柜内 CXL、柜间 RDMA〔P268 p7〕〔P326 p4〕；Marvell 定义 G1.5/G2.5 两个"数十 TB @ 数百 ns"层〔P063 p6〕；Samsung 把推理中心 2030 描述为光子 fabric 连接的分解式内存 pod（目标，非实测）〔P354 p3, p4〕。

**判断2：池化解决了容量，没有解决互连带宽与能耗；近存计算（PNM）在检索、KV 选择等搬移密集任务上给出 10×–60× 级实验收益，但瓶颈在软件接口，不在芯片。**
- 带宽缺口（自报，Samsung 内部分析）：CXL 控制器后 DDR5 带宽 268.8 GB/s，而 PCIe Gen6 x8 只有 64 GB/s；控制器到主机的数据传输占能耗 67.2%〔P060 p22〕。
- 实验收益：10 个 PNM 设备做 512M 向量 IVF-Flat 检索，QPS 14.81 vs 主机 0.23（64×），能效 65×〔P060 p27〕；100K 上下文混合注意力 batch=5 时 17.7 vs 5.28 tok/s（3.35×）〔P060 p29〕；SK hynix 池侧 KV 选择平均缩减约 ×30，TTFT 比 LMCache 快 1.67×〔P326 p10, p12〕；Marvell 计算向量检索数据搬移降 60×（计算）〔P328 p9〕。
- 软件是短板：DCC 工作流开场即称"差距在软件而非芯片"〔P330 p4, p5〕；面板主张"先基准、后接口"，否则统一中间件会变成"杂物抽屉"〔P327 p12〕；Samsung 试过 oneAPI、OpenXLA PJRT、PyTorch 三条路径后自研 SPEL，Qwen3-0.6B 跑通但只给出调用次数与时间（实验，看图）〔P334 p2, p14〕。

**判断3：HBM 同时是 XPU 的面积、成本和热瓶颈；业界在"改造 HBM"（定制 base die、低功耗 D2D、混合键合）与"绕开 HBM"（DRAM-on-Compute、LPDDR 串行挂接、3D DRAM、HBF）两条线上并行投入。**
- 瓶颈量级（引用/自报）：HBM 约占 die 面积 30%、XPU 成本 >50%，按当前内存价格内存 BOM 在许多 GPGPU/ASIC 中 >60–80%〔P070 p3〕；HBM 堆栈贡献 2.5D 封装热阻 57%，ASIC 本体 13%（引用 ECTC 2026）〔P070 p7〕；HBM5 >28 Gbps 时热流 >2.0 W/mm²，高于 JEDEC 约 1.7 W/mm² 参考〔P070 p6〕。
- 改造路线：Marvell 定制 base die 回收最多 25% die 面积（自报）〔P070 p4〕；SBD D2D 64 Gbps/wire、常规负载功耗降 75%（自报）〔P070 p10〕；GUC 给出 HBM5 相对 HBM4E PHY 面积效率 0.3 → 0.75–1.0 TB/mm²，2029 年量产（自报/引用 SK hynix）〔P075 p7〕。
- 绕开路线：GUC DRAM-on-Compute（4 层整 reticle）32 TB/s、30 ns、0.5 pJ/bit，对比 6×HBM4E 24 TB/s、200 ns、2.5 pJ/bit，但最高温 125 vs 95°C（自报）〔P075 p8〕；Nallasway 用 50 个 LPDDR5X 串行模块挂在 reticle die 四周，3.2 TB/7.5 TB/s，对比 Jalapeño+6 HBM4 的 216 GB/15.4 TB/s（目标值）〔P450 p8〕；d-Matrix 6 nm、无 HBM 无 CoWoS，Raptor 用 3D DRAM（自报）〔P286 p24〕〔P317 p19〕；SK hynix HBF 容量为 HBM 14×、带宽 0.5×（自报，看图）〔P268 p15〕。

**判断4：D2D 互连按场景分层，UCIe 是互操作底线而非性能上限；OCE 标准的重心已从 PHY 转到固件、安全和"可验证的互操作"。**
- 性能侧走私有：GUC 称多数场景无需标准合规，GLink-LL 0.05–0.10 pJ/bit、1–3 ns，对比 UCIe-A 0.75 pJ/bit、10 ns+retry（自报）〔P075 p4〕；Marvell 称 UCIe 并非为下一代 HBM 带宽密度设计，HBM5 需约 6.4 Tbps/mm〔P070 p11, p14〕；LBNL 指出 UCIe/BoW 的 bump pitch >40 µm 带来串行化功耗与延迟，而 Intel 25 µm、TSMC 10 µm 已在推进〔P066 p20, p28〕。
- 成本侧与出封装：BoW.Flexi 1.0 最少 6 pin、0–4 Gb/s/pin、无链路训练，面向 MCU/模拟 chiplet〔P069 p3, p4〕；Credo 112G VSR 约 10 in、<1 pJ/bit、1.8 Tb/s/mm，填补 D2D（<25 mm）与长距（>1 m）之间的区间（自报）〔P067 p3〕。
- 系统层：FCSA 1.0.0 于 2026 年 2 月发布、1.1.0 本周批准，新增安全章节〔P079 p4〕〔P076 p4, p15〕；OCE 自述"无组织拥有完整开放系统结果"，2027 年目标从定义标准转为证明互操作〔P079 p2, p8〕；GSOC/AMD 认为 BoW 与 UCIe 只解决物理和协议层，还需 SCMI 固件 API 与 MCTP 传输对齐〔P078 p3, p5〕。

**判断5：封装内光 I/O 的出发点是 shoreline 几何约束；宽慢（VCSEL/µLED）与微环 CPO 两条路线的数字多为自报或目标，选哪种 D2D 接口取决于光引擎是否终结 FEC。**
- 几何约束（引用白皮书）：224G、reticle 级封装铜逃逸 26 Tb/s/dir，CPO 93.6，面阵光 I/O 1,191（46×）；半周边加 16 个 HBM 堆栈后 XPU 侧只剩 33 Tb/s/dir〔P455 p2〕；Baya 指出 die 边缘被 SerDes、UCIe、HBM PHY 争抢〔P064 p37〕。
- 宽慢路线（自报/目标）：Lumentum 1060 nm VCSEL HTOL 5000 h（115°C、Tj 181°C），1.6T 在 FIT<1（含 sparing）下需 30–54 路，带宽密度今日约 1 Tb/s/mm、路线约 4〔P444 p2, p3, p5〕；LightX-1 µVCSEL 57+57 lanes、3.2 Tb/s/引擎、<1.5 pJ/bit〔P338 p6〕；Avicena µLED 目标 >10 Tbps/mm、<1 pJ/bit，已出货 1 Tbps eKit（335 路 × 3 Gbps）〔P339 p8, p12〕。
- 微环/CPO 路线（设计/仿真）：Ayar Labs+Wiwynn 封装 8 个光引擎 + 8 个 HBM，每加速器 200+ Tbps，热仿真 SoC Tj 112°C、HBM4 75.4°C、OE 69.8°C〔P342 p7, p8〕。
- 接口选择：Eliyan 认为 UCIe 适合 EIC 终结 FEC/retimer 或单光纤场景，BoW 更适合高 radix、多光纤直驱 EIC，因其可非对称、可变 lane 数、可分别时钟 PPM；OCP-OCE 正在组建光互连工作组〔P071 p8, p13, p17, p18〕。

---

## 1. 需求与架构

### 1.1 需求数字

| 类别 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| 算力与 I/O 剪刀差 | 过去 20 年 CPU/GPU FLOPS 增长 1,000,000×，DRAM 带宽与互连带宽各 100×（未注来源） | 引用/看图 | 〔P071 p3〕 |
| 两年增速 | AI 训练算力约 100×，GPU 3.3×，内存带宽 1.4×，互连 1.4× | 引用（未注来源） | 〔P321 p4〕 |
| KV 占用 | 64 并发 × 32K 上下文 KV 占 HBM 57%；Qwen3-235B 权重 235 GB、KV 约 384 GB；DeepSeek-V3 权重 671 GB、KV 约 141 GB | 自报/看图 | 〔P057 p2〕 |
| 每用户成本 | 128K 上下文 2 用户填满 80 GB HBM；仅 HBM 4X（约 2 用户/GPU）、+DDR 约 2X（约 6）、+flash/KV store 1X（约 16）；3 年 TCO 约降 65% | 示意模型（非承诺值） | 〔P275 p7, p8, p9〕 |
| 单实例内存 | 2020 dense 0.4 TB → 2023 MoE 1.2 TB → 2026 agentic 5 TB（KV 约 3 TB） | 示意/看图 | 〔P450 p2〕 |
| 每 die 容量趋势 | 36%/yr（至 2023）后降为 8%/yr；GB200 较 H200 降 32% | 引用 SemiAnalysis | 〔P450 p6〕 |
| 每 die 带宽趋势 | 31%/yr（2016–2023 拟合）；Blackwell 两代 +0% | 引用 SemiAnalysis/Hot Chips 2026 | 〔P450 p4〕 |
| HBM 成本占比 | HBM 约 30% die 面积、>50% XPU 成本；内存 BOM >60–80% | 引用（Marvell Analyst Day 2024 / Silicon Analysts 2026） | 〔P070 p3〕 |
| 芯片功耗 | 2021 年 400 W（0.48 W/mm²）→ 2026E 2,000 W（1.25 W/mm²）；ASIC 曲线 2027E 3,000 W | 预测/引用 | 〔P070 p6〕 |
| 功耗层级 | CPU <0.5 kW、GPU 2+ kW、领域专用芯片 5+ kW | 自报 | 〔P287 p4〕 |
| 3D 功率密度 | 5–10 W/mm²，平均 7.5 W/mm² | 自报 | 〔P075 p3〕 |
| 封装面积 | 2.5D <10,000 mm² Si；3.5D 10,000–20,000 mm² Si | 自报 | 〔P287 p12〕 |
| Agent 访问模式 | Claude Code（Sonnet 4.5）trace 三阶段 KV 命中率 87–99%、约 50%、汇总 83.5%；编码 agent 前缀命中约 96% | 实验/引用 | 〔P060 p9〕〔P326 p20〕 |
| CPU 侧负载 | 编码 Agent CPU 时间占比 82%、客服 78%；工具执行占单轮墙钟 30–35% | 示意仿真/自报 | 〔P290 p2, p3〕 |
| 光 I/O 资本 | 2025 年末以来光学战略投资 >\$15B，含 Marvell 收购 Celestial AI \$3.25B（2026 年 2 月完成） | 引用公开公告 | 〔P338 p3〕 |

### 1.2 内存层级各家口径对照

| 机构 | 层级划分（时延/容量量级） | 口径 | 索引 |
|---|---|---|---|
| Samsung（keynote） | L0 SRAM 数 MB/<数十 ns；L1–L2 HBM/zHBM/HBM5 数十–数百 GB；L2.5 LPDDR/SOCAMM 数百 ns、至 1 TB；L3 3D DRAM/CXL Pool 约数 µs、数 TB；L3.5 KV SSD 数十 µs、数十 TB；L4 TLC/QLC 数 ms | 目标/定性 | 〔P354 p4〕 |
| Marvell | G1 HBM（ns，数百 GB）；G1.5 PFMA+PF-Chiplet 封装级集成（数十 TB @ 数百 ns）；G2 系统 DRAM 1–2 TB；G2.5 CXL fabric 内存（数十 TB @ 数百 ns）；G3 本地 SSD（µs，数十 TB）；G4 共享对象/文件 | 自报 | 〔P063 p6〕 |
| Samsung（CMS） | HBM 40–192 GB/GPU；DRAM 256 GB–2 TB/socket；CMM-D 128 GB–8 TB/socket；CMM-D 机架池 5.5–11 TB（2 个 CXL 交换） | 自报 | 〔P060 p6〕 |
| Alibaba | HBM/DRAM → SCM（PCM）→ CXL SSD → TLC/QLC；AliMemory CXL DRAM 140 ns，AliSCM 350 ns，AliFlash CXL 10–30 µs | 自报/实测 | 〔P057 p3, p7〕 |
| Micron | 跨会话 system prompt 层（复用 40–60%、小时级、容量驱动）放 CPU DRAM/LPDDR5x/SCM；会话内上下文层（复用 ≥95%、分钟级、带宽敏感）放 HBM 溢出到 DDR/LPDDR | 模型/自报 | 〔P062 p8〕 |
| Hyve | HBM 热态 → DDR/CXL → NVMe/Flash → 对象存储 | 自报 | 〔P275 p8, p14〕 |
| SK hynix | 柜内 CXL 池、柜间 RDMA；新增 HBF 位于 HBM 与 eSSD 之间 | 自报 | 〔P268 p7, p15〕 |

几家的层数和命名不同，但都在 HBM 与本地 SSD 之间插入了一到两层"数百 ns、TB 到数十 TB"的共享层。分歧在这层用什么协议接到 GPU（见 1.3 和第 5 节）。

### 1.3 架构演进要点

1. **从直连扩展到机柜池**：Marvell 给出 Structera X/A 直连 → Structera S 服务器内 CXL 交换（最高 100 TB 池，端口到端口 <100 ns）→ 机架/Pod 级光互连共享内存（Photonic Fabric Memory Appliance，16 台服务器 × 2 Tbps，<350 ns）〔P063 p3, p4, p5〕。Samsung 机架级 CXL 计算型内存系统 20 TB、2.7 TB/s〔P060 p23〕。
2. **GPU 不经 CPU 直达内存**：Astera 在 PCIe fabric 上挂 Leo 内存控制器，XPU 以 P2P 访问，CPU 带宽留给 agentic 负载〔P059 p2, p3〕；Marvell 由扩展器 DMA 直接读写 GPU HBM，绕过主机 DRAM 和 IOMMU，GPU 侧不需要 CXL〔P063 p14〕；Alibaba 下一代把 PCM 层挂在 UALink 上，GPU 直接 load/store〔P057 p9, p11〕。
3. **动态容量**：CXL DCD 让池化容量随 agentic 负载增删，TTFT P99 −52%、goodput 7.1×（DCD 为在现有硬件上的仿真）〔P060 p10, p11〕；CMS Memory Fabric Manager 用 Kubernetes DRA+NRI 接入编排，System-RAM 与 devdax 两种暴露方式对应透明扩容和共享/KV offload〔P061 p4, p5〕。
4. **计算向数据移动**：池化之后的下一步是在池侧做 KV 选择、检索、优化器更新〔P326 p12〕〔P325 p4〕〔P329 p7〕。
5. **封装尺寸继续放大**：MediaTek 称 2022 年 85×85 mm² Hybrid CoWoS 量产（自报"World 1st"）〔P287 p5〕；GUC System on Wafer >40× reticle（>33,000 mm²）、最多 64 HBM4E、TDP 20 kW〔P075 p13, p14〕。功率随之需要垂直供电和 IVR（TSMC 16 nm 演示，3 W/mm²，响应快于板载 VRM 10–100×）〔P075 p12〕。
6. **封装内光 I/O 进入机柜设计**：Lightmatter/Dell 主张扩展 DC-MHS 平台契约（机械、电源、高速、热、管理）承接托盘内光引擎，引擎选择留给厂商〔P455 p3, p4, p6〕；Samsung 2030 设想中出现 "HBM over Optical"〔P354 p4〕。

---

## 2. 技术路线对比

### 2.1 D2D 与短距电互连

| 路线 | 代表方案/厂商 | 关键指标（条件） | 成熟度 | 索引 |
|---|---|---|---|---|
| UCIe-S/A | 标准；GUC 对比 | UCIe-S 64 Gbps、110 µm、0.37 TBps/mm、1.25 pJ/bit；UCIe-A 64 Gbps、45 µm、2.6 TBps/mm、0.75 pJ/bit、10 ns+retry | 量产（标准） | 〔P075 p4〕 |
| 私有 2.5D 低速宽并行 | GUC GLink-LL | 4–8 Gbps，CoWoS 35 µm / SoIC-X 6 µm，0.05–0.10 pJ/bit，BER<1E-30 无需 CRC/重传，1–3 ns | 自报，客户在用 | 〔P075 p4〕 |
| 私有 3D | GUC GLink-3D | 1.0（N6/N5）0.2 pJ/bit、9 Tbps/mm²；2.0（N2P）0.03 pJ/bit、50 Tbps/mm²；3.0 执行中 80 Tbps/mm²；1.0–2.1 已硅验证 | 自报 | 〔P075 p5〕 |
| 同时双向 D2D | Marvell SBD | 64 Gbps/wire（2 nm），常规负载功耗降 75%，PHY 面积 15%，>7 TB/s | 自报（新闻稿） | 〔P070 p10, p11〕 |
| BoW 2.0 | OCP OCE | 8/16 lane，2–32 Gb/s；PHY 已有 65 nm 至 3 nm 9 个节点实现 | 标准/多实现 | 〔P069 p4〕〔P071 p12〕 |
| BoW.Flexi 1.0 | Infineon、YorChip、VeriSilicon、Microchip、Eliyan | 1–128 lane，0–4 Gb/s/pin，SDR，最少 6 pin，0.65–0.95 V，wire bond/flip chip/hybrid | 2026-09 发布 | 〔P069 p3, p4〕〔P079 p5〕 |
| OCE TLL 2.0 | VeriSilicon、Ventana | 头 12b→6b；LLP 默认 24 granule；新增 UCIe 与 BoW.FLEXI PHY binding | 标准进展 | 〔P065 p5, p6, p8, p9〕 |
| 出封装串行 | Credo OmniConnect / OCE LSI | 112G VSR 约 10 in、23 dB、<1 pJ/bit、1.8 Tb/s/mm；256 B FLIT 效率 93%；单向约 35 ns、1.15 pJ/bit | Phase 1 spec 约 2026-11 | 〔P067 p3, p10, p13〕〔P450 p3〕 |
| 非阻塞片上 fabric | Baya NeuraScale | 每 UCIe 链路 320 GB/s @2.5 GHz；每 chiplet 256 个 1 Tb/s 端口；称 scale-out 交换机 30:1 减少 | 自报/预测 | 〔P064 p39, p41〕 |
| 封装上铜缆 | TE CPC | 448G 至背板（PAM6）@90 GHz 约 6 dB vs NPC 约 12 dB（不含封装损耗） | 仿真 | 〔P461 p5〕 |

### 2.2 HBM 与替代内存

| 路线 | 代表方案/厂商 | 关键指标（条件） | 成熟度 | 索引 |
|---|---|---|---|---|
| 标准 HBM 演进 | JEDEC/SK hynix | HBM4 2.0–3.3 TB/栈 → HBM4E 3.6–4.1 → next-gen 5.3/7.2 TB/s（28 Gbps），约每 2 年 1.7× | 预测/引用 | 〔P070 p5〕 |
| HBM5 | SK hynix/GUC | 24–32 Gbps，PHY 8 mm²，约 90 W@32G；2029 量产 | 预测/引用 | 〔P075 p7〕 |
| 定制 base die（cHBM） | Marvell | 回收最多 25% die 面积，最多 30% 更多计算 | 自报 | 〔P070 p4〕 |
| 混合键合 HBM | 引用 Onto/Electronics 2025 | die 间热阻降 23–47%，垂直导热最高 3×，堆栈高度缩短 >15% | 引用 | 〔P070 p8〕 |
| DRAM-on-Compute | GUC | 4 层整 reticle：32 TB/s、30 ns、0.5 pJ/bit；HB 间距 5–8 µm，接口密度 10–15× | 自报 | 〔P075 p8〕 |
| 3D DRAM 加速器 | d-Matrix Raptor | NVLink Fusion 机柜 144 XPU，3D-DRAM 2.3 TB、7.2 PB/s；不用 HBM 与 CoWoS | 自报 | 〔P286 p19, p24〕 |
| LPDDR 串行挂接 | Nallasway/Credo Weaver | XPU+50 OC-DDIMM 3.2 TB/7.5 TB/s/138 cm²；HPCM 模块 TDP 1,650 W | 概念/目标 | 〔P450 p8, p11, p12〕 |
| HBF | SK hynix/SanDisk | 相对 HBM 带宽 0.5×、容量 14×、pJ/b 3.7×；Spec 1.0 预期 2027-01 | 自报/预测 | 〔P268 p15, p17〕 |

### 2.3 CXL/fabric 内存与 KV 卸载

| 路线 | 代表方案/厂商 | 关键指标（条件） | 成熟度 | 索引 |
|---|---|---|---|---|
| CXL Type-3 DRAM 扩展 | Meta 舰队 | 现网收益见判断1；故障可调试性不足 | 现网 | 〔P058 p14, p15〕 |
| CXL SCM（PCM） | Alibaba AliSCM | CXL 2.0 Type-3 E3.S，256 GB–1 TB/模块，读 350 ns，读/写 20/6.5 GB/s；已量产部署 | 自报（量产） | 〔P057 p4〕 |
| CXL SSD | Alibaba AliFlash CXL | Gen6/CXL 3.2：4 TB、20M IOPS（512 B）；Gen7/CXL 4.0 目标 50–100M IOPS | 自报/预测 | 〔P057 p5, p7〕 |
| CXL 交换池 | Marvell Structera S；Liqid | 2 TB/s 交换，最高 100 TB，<100 ns，135 W | 自报 | 〔P063 p5〕〔P060 p23〕 |
| PCIe P2P 内存控制器 | Astera Leo + Scorpio | 4×256 GB DDR5-5600，320 lane 交换；Leo X-Series 相对 CPU 内存 TTFT 快 62% | 实验 | 〔P059 p4〕〔P243 p10〕 |
| 光互连内存设备 | Marvell PFMA | 1 TB HBM3e + 128 DIMM（16/32 TB），CXL 3.1 DCD，16 路 × 2 Tbps，<350 ns | 自报 | 〔P063 p4〕 |
| UALink 挂接 SCM | Alibaba UMX 下一代 | 延迟估算 0.4×本地 DRAM（基线路径待验证）；成本 0.25×、功耗 0.125× DRAM | 预测 | 〔P057 p12〕 |
| UB 内存借用 | Huawei ClusterBench | Redis 1.33× 超配、吞吐 +23%；跨节点内存访问 250 ns（示例） | 实验/示例 | 〔P114 p14, p16〕 |
| CPU 侧 CXL | Intel Xeon | Flat Memory Mode 达全 DDR5 性能 97.3% | 自报 | 〔P290 p7〕 |

### 2.4 近存计算（PNM/NDP）

| 路线 | 代表方案/厂商 | 关键指标（条件） | 成熟度 | 索引 |
|---|---|---|---|---|
| Arm 核 CXL 计算内存 | Marvell Structera A | 5 nm，16 核 Neoverse V2，最多 4 TB，200 GB/s，95 W，LZ4 2–3× 容量 | 自报 | 〔P060 p24〕 |
| Arm 核 CXL 计算内存 | SK hynix CMM-Ax 3.0 | CXL 2.0 Type 3，PCIe 5.0 x16，512 GB DDR5-6400，200 GB/s，16 核 V2 | 自报 | 〔P326 p16〕〔P325 p13〕 |
| 多核 RISC-V NDP | XCENA MX1/MX1P | 3,072 RISC-V 核，4ch DDR5-8400 最多 2 TB，CXL 3.2 Type 3，Back-Invalidation 一致性 | 自报（PoC/量产两版） | 〔P329 p3, p4, p11〕 |
| CXL-PNM | Samsung | 图标"Industry's 1st CXL-PNM" | 自报/看图 | 〔P327 p3〕 |
| 软件栈 | Samsung SPEL/NDC API；SNIA CS API v1.1 | SPEL 计划开源；CS API 2025-05 批准、30+ 函数 | 开源/标准 | 〔P334 p14〕〔P330 p8〕 |

### 2.5 封装内光 I/O

| 路线 | 代表方案/厂商 | 关键指标（条件） | 成熟度 | 索引 |
|---|---|---|---|---|
| 1060 nm VCSEL 宽慢 | Lumentum | 可插拔 1.6T/3.2T、NPO 6.4T、CPO 12.8T；CPO D2D 边宽约 4 mm、>6 Tbps/mm（看图）；PCIe-5 OM3 光链路无误码 POC；路线 <2.5 pJ/bit | 实验/预测 | 〔P444 p3, p5〕 |
| µVCSEL + 多芯光纤 | LightXcelerate LightX-1 | 引擎 1.5×0.6 mm，32 Gb/s/lane（路线 64G→100/200G），3.2 Tb/s，50 m，<1.5 pJ/bit；32 Gb/s 眼图 mask margin 5.5% | 自报/实验 | 〔P338 p6, p10〕 |
| µLED | Avicena LightBundle | 335 路 × 3 Gbps = 1 Tbps eKit 已出货；目标 >10 Tbps/mm、<1 pJ/bit、耐温 >200°C | 自报/目标 | 〔P339 p8, p12〕 |
| 微环 + 外置光源 CPO | Ayar Labs + Wiwynn | 每封装 8 光引擎 + 8 HBM，200+ Tbps，OCI-MSA PHY，UCIe-A 转 UCIe-S | 设计/仿真 | 〔P342 p7, p8〕 |
| MRM CPO OE | GO | 3.2T，2×8λ×200G，QD 8λ 梳状激光，>3 Tbps/mm（单向），12 层 TGV 玻璃基板 | 自报/demo | 〔P321 p15〕 |
| 量子点光源 | Quintessent | 8λ 梳 + SOA 200 mW、>25 mW/λ；FP QD 激光 80°C 老化 >22,000 h | 实验（EVT） | 〔P340 p4, p11〕 |
| 面阵光 I/O（APO） | Lightmatter/Dell（引用白皮书） | 1,191 Tb/s/dir（46×铜）；光子跳 sub-10 ns vs retimer 40–120 ns | 引用/自报 | 〔P455 p2, p10〕 |
| 光 D2D 接口 | Eliyan | 1.6T SiPho：UCIe-AP x64 × 25.6 Gbps；1.6T 宽慢：8 × BoW-SP x4（各 4×53.1 Gbps） | 设计/自报 | 〔P071 p9, p14〕 |

---

## 3. 关键数据表

### 3.1 D2D 能效与密度（均为自报，工艺与条件不同，不宜直接排序）

| 方案 | 速率 | pJ/bit | 密度 | 延迟 | 索引 |
|---|---|---|---|---|---|
| UCIe-S | 64 Gbps | 1.25 | 0.37 TBps/mm | — | 〔P075 p4〕 |
| UCIe-A | 64 Gbps | 0.75 | 2.6 TBps/mm，1.4 TBps/mm² | 10 ns+retry | 〔P075 p4〕 |
| GLink-LL | 4–8 Gbps | 0.05–0.10 | — | 1–3 ns | 〔P075 p4〕 |
| GLink-3D 2.0（N2P） | — | 0.03 | 50 Tbps/mm² | 0.125–0.5 ns | 〔P075 p5〕 |
| Marvell SBD | 64 Gbps/wire | 常规负载功耗 −75% | >7 TB/s | — | 〔P070 p10〕 |
| 112G VSR（Credo） | 112 Gbps | <1（LSI 口径 1.15） | 1.8 Tb/s/mm | 单向约 35 ns | 〔P067 p3〕〔P450 p3〕 |
| DRAM-on-Compute 接口 | — | 0.5 | 接口密度为 TCB 的 10–15× | 30 ns（内存访问） | 〔P075 p8〕 |
| HBM4E（对照） | 16 Gbps | 2.5 | — | 200 ns（内存访问） | 〔P075 p8〕 |
| 需求：HBM5 | — | — | 约 6.4 Tbps/mm（7.2 TB/s over 9 mm） | — | 〔P070 p11〕 |

### 3.2 HBM 代际与热

| 指标 | 数值 | 口径 | 索引 |
|---|---|---|---|
| HBM4 接口 | 2048 bit（32×64-bit 通道） | 引用 JEDEC JESD270-4 | 〔P070 p3〕 |
| HBM4E vs HBM5 | 16 vs 24–32 Gbps；PHY 14 vs 8 mm²；约 60 W vs 约 90 W；2026 vs 2029 量产 | 自报/引用 SK hynix 2026-05 | 〔P075 p7〕 |
| HBM5 单栈功耗 | 约 100 W/栈 | 引用 SK hynix | 〔P070 p9〕 |
| 热阻分解 | 2.5D 封装中 HBM 内部 57%，ASIC 13%；8→16-high 到 2028 越过热预算 | 引用 ECTC 2026 | 〔P070 p7〕 |
| iHBM | D2D PHY 处硅 ICE 热阻降约 30% | 引用 SK hynix | 〔P070 p9〕 |
| 冷板实测 | Corintis 微流控冷板（H200 @1 LPM）HBM 结-入口温升 29.5→23.9°C（−19%） | 实验 | 〔P010 p16〕 |
| 结→冷却液热阻 | 基线 冷板 45%/TIM 20%/硅 35%；功率密度增大时硅升至 45% | Meta，看图 | 〔P010 p27〕 |
| CPO 封装热仿真 | SoC Tj 112°C（规格 125）；HBM4 75.4°C（95）；OE 69.8°C（100）；4.5 LPM | 仿真 | 〔P342 p8〕 |
| DRAM-on-Compute 温度 | 最高温 125°C vs HBM4E 方案 95°C | 自报 | 〔P075 p8〕 |
| 两相冷却内存模块 | -90 kPa 下纯水 48–53°C 沸腾；2 LPM 对应约 5 kW | 仿真 | 〔P450 p16, p17〕 |

热这一栏我看得比较重。Meta 的热阻拆分显示功率密度上升时硅本身占比升到 45%〔P010 p27〕，冷板再好也只改善一半以下；HBM 又是封装热阻的大头〔P070 p7〕。DRAM-on-Compute 的带宽和延迟优势，要以 125°C 的结温为代价〔P075 p8〕，这在 DRAM 刷新与可靠性上能否接受，材料里没有答案。

### 3.3 CXL/fabric 内存 KV 卸载实验结果（收益基线不同，需逐行看条件）

| 方案 | 条件 | 结果 | 基线 | 口径 | 索引 |
|---|---|---|---|---|---|
| AliSCM 替代 DRAM 做 L2 | iso-cost：128 GB SCM vs 32 GB DRAM；RTX PRO 5000，SGLang，Qwen3-8B；两层缓存约 126 GB KV | 吞吐 +58.3%，P90 TTFT −48.7% | 等成本 DRAM | 实验 | 〔P057 p8〕 |
| 同上，三层缓存 | 约 400 GB KV | 吞吐 +66.3%，P90 TTFT −36.0% | 同上 | 实验 | 〔P057 p8〕 |
| Astera fabric 内存 | 同容量 128 GB/实例，短 prompt | 与 CPU DRAM 几乎重合 | CPU DRAM | 实验，看图 | 〔P059 p6〕 |
| 同上 | fabric 容量 2×–3×，中长 prompt | 约 2×、约 3× RPS/GPU | CPU DRAM（容量更小） | 实验，看图 | 〔P059 p7, p8〕 |
| Samsung CXL 池 | Llama3.1 8B，KV 超出 RDIMM 容量 | 95% vs 17% 吞吐保持，5.6× | RDIMM（重算） | 实验，看图 | 〔P060 p8〕 |
| DCD 弹性分配 | 32 GB DRAM + 1024 GB CXL 池 | TTFT P99 −52%，goodput 7.1× | DRAM 96 GB | 仿真（现有硬件上模拟 DCD） | 〔P060 p10, p11〕 |
| XCENA InfiniteMemory | Llama-3.1-8B，LV-Eval | lookahead 预取 526 ms ≈ DRAM 509 ms；无预取 4,314 ms | DRAM | 实验，看图 | 〔P060 p17〕 |
| Marvell Structera A | Llama-3.1-8B，H200，16 用户 | TTFT 1,199 ms vs CPU DRAM 2,162 vs SSD 4,243 vs 重算 5,933；吞吐 4× | HBM 重算 | 实验，看图 | 〔P063 p10〕 |
| Structera vs RDMA | Nixlbench 64 MB | 读延迟 1,325 vs 23,199 µs；读带宽 50.6 vs 46.3 GB/s | RDMA | 实验，看图 | 〔P063 p16, p17〕 |
| SK hynix MARS | 平均 TTFT | Remote CXL DDR 15.45 s vs 重算 80.76 s（3.5–5.2×） | 重算 | 自报实验，看图 | 〔P268 p10〕 |
| SK hynix CXL 池 | 并发 100 | TTFT 比 LMCache 快 1.67×；goodput 比 NIXL 高 1.9× | LMCache/NIXL | 实验 | 〔P326 p10〕 |
| 池侧 KV 选择 | Arcee trace | 正文称相对 Mooncake 1.4× TTFT、2.29× E2E；按图 TTFT 计算约 1.78×（存疑） | Mooncake | 实验，看图 | 〔P326 p18〕 |
| Leo X-Series | GNR + 4×H200，Qwen2.5-32B | TTFT 快 62%，TPS 多 22% | CPU 内存 | 实验 | 〔P243 p10〕 |
| Micron 层容量 | GH200，Llama 3.1-70B，kv-tier 100→600 GB | TTFT 约 31→1.5 s，阶跃 | — | 实验，看图 | 〔P062 p12〕 |

读这张表要注意两点：一是基线多为"重算"或"更小容量"，与"同容量 DRAM"相比的收益很少有人给；Astera 是唯一明确给出同容量对比的，结果是持平〔P059 p6〕。二是全部为 8B–70B 稠密模型和单节点量级，Micron 自己也注明 MoE 与多厂商平台待验证〔P062 p16〕。

### 3.4 介质与器件参数

| 器件 | 参数 | 口径 | 索引 |
|---|---|---|---|
| AliSCM vs Optane DIMM | 粒度 128 vs 256 B；读延迟 350 vs 300 ns；读带宽 20 vs 8.1 GB/s；写 6.5 vs 3.15 GB/s | 实测，自报 | 〔P057 p4〕 |
| AliMemory CXL DRAM | 140 ns（64 B），60M IOPS，256 GB/模块 | 自报 | 〔P057 p7〕 |
| Structera X 2404 | 最多 12 DIMM、1.5 TB，内联 LZ4 1.6–2× | 自报 | 〔P063 p15〕 |
| Arm AGI CPU | 136 核 V3，CXL 3.0，96 lane PCIe Gen6，每芯片 6 TB | 自报 | 〔P278 p11〕 |
| Diamond Rapids | 256 核，16 通道 32 DIMM，12800 MT/s，1.6 TB/s | 自报 | 〔P290 p11, p12〕 |
| 粒度错配 | CXL 64 B × 1K 未完成命令 = 64 KB 在途，打不满 10+ GB/s SSD；KV 块数百 KB–数十 MB | 自报 | 〔P060 p18〕 |
| 稀疏注意力访问 | 约 584 B/token/layer，每块连续约 1.34 token；512 B 页读放大 1.65×，8 KB 页 8.79× | 自报/预测 | 〔P057 p9, p12〕 |

### 3.5 近存计算收益

| 任务 | 条件 | 结果 | 口径 | 索引 |
|---|---|---|---|---|
| 向量检索 | 512M 向量、4.5 TB，10 PNM vs 主机+CXL 池 | QPS 64×，能效 65×，有效读带宽 1,625 vs 26 GB/s | 实验 | 〔P060 p27〕 |
| 混合注意力 | LLaMA 3.1 70B INT8，100K 上下文，batch=5 | 3.35× tok/s，3.84× tok/kJ | 实验 | 〔P060 p29〕 |
| DP 训练噪声 | Cocoon-NMP，4×A5000 + CMM-Ax | 少用 10× GPU；比无计算 CXL 扩展快 1.23–2.32× | 实验 | 〔P325 p14〕 |
| 优化器卸载 | CXL Hybrid Memory | GPU 内存 −80%；比 ZeRO-Offload/Infinity 快 4.40×/3.62× | 实验 | 〔P325 p4, p6〕 |
| 向量索引 | MX1P vs GNR 32 核 | Flat 4.81×、HNSW 1.65×（设备数存疑） | 实验 | 〔P329 p21〕 |
| 分词卸载 | 25.6K 输入、前缀复用 96% | 分词约 130→6 ms，TTFT 约 345→221 ms | 实验 | 〔P326 p23〕 |
| 文献汇总 | DCC 白皮书 Table 1 | PIM 10–23.2×；PNM 1.39–1.77×；CS 4.3×；DPU 54× | 引用 | 〔P330 p4〕 |

PNM 在白皮书汇总里只有 1.39–1.77×〔P330 p4〕，远低于 Samsung 的 64×〔P060 p27〕。后者是对"主机经 PCIe 拉原始数据"这种最坏基线的对比，前者是文献平均。两组数字都对，但不能放在同一句话里宣传。

### 3.6 封装内光 I/O 指标

| 指标 | 数值 | 口径 | 索引 |
|---|---|---|---|
| 封装逃逸带宽（224G，reticle 级） | 铜 26 / CPO 93.6 / APO 1,191 Tb/s/dir | 引用白皮书 | 〔P455 p2〕 |
| 封装边缘 escape | CPO 0.9、NPO 0.25 Tb/s/dir per mm | 自报/计算 | 〔P436 p16〕 |
| 铜/光边界 | 200G 约 1–2 m 无源铜、约 4 m 有源铜；400G 约 4 m 起为光；800G+ 约 1 m 起为光 | 自报 | 〔P071 p4〕 |
| scale-up 光学目标 | >20 m；每 SoC >50 Tbps/方向；<20 ns；>4 Tbps/mm²；<4 pJ/b；pre-FEC BER <1e-9 | 引用行业规格 | 〔P345 p7〕 |
| VCSEL 冗余 | 1.6T 在 FIT<1 下需 32 G×54 / 50 G×36 / 64 G×30 路 | 看图 | 〔P444 p3〕 |
| VCSEL 寿命 | HTOL 5000 h，8 mA、115°C、Tj 181°C | 自报 | 〔P444 p2〕 |
| µLED 现状 | >10 pJ/bit（含 >5 pJ/bit 主机 SerDes）为现有光学基线；µLED 目标 <1 pJ/bit | 自报 | 〔P339 p5, p8〕 |
| CPO 现网可靠性 | 第一代机群 MTBF 8.2M 小时，约为可插拔 10×；第二代 >50M 运行小时 | 引用 Meta | 〔P455 p9〕 |
| 封装光纤耦合 | PPK 181 个 FAU <2 dB 良率 99.5% | 实验，看图 | 〔P436 p8〕 |

---

## 4. 厂商与客户态势

### 4.1 超大规模用户与云

- **Meta**：本方向唯一的现网 CXL 数据来自 Meta 生产系统工程团队，收益见判断1；同时指出"可以完全符合规范，但在舰队规模下仍无法调试"，同一主机侧症状（CXL.mem 读超时）可能来自 DIMM、控制器或固件，结果是不可屏蔽 MCE 和无预警宕机〔P058 p14, p16〕。热侧 Meta 给出结→冷却液热阻拆分〔P010 p27〕；CPO 可靠性数据被 Lightmatter 和 Ranovus 引用〔P455 p9〕〔P345 p20〕。Meta 主持了内存墙面板〔P056 p3〕。
- **Alibaba Cloud**：唯一给出自研 SCM 量产部署的云厂商。AliSCM（PCM，CXL 2.0 Type-3）已量产，下一代把 warm-KV 层挂到 UALink，让 GPU 直接 load/store〔P057 p4, p9, p11〕。
- **Microsoft**：在内存墙面板出现〔P056〕；冷板 unitary cell 原型结温最多降 10°C〔P010 p11〕；scale-up 光链路 flap 分析认为 GPU 不像交换机能处理 flap，需把同端口 lane 分到不同故障域〔P345 p27, p32〕。本方向材料里 Microsoft 没有内存池化定量数据。
- **Google**：本方向只有机密存储（PCIe/CXL IDE 链路加密、TDISP）〔P045 p53〕和冷板面板中引用 Ironwood〔P010 p21〕，没有内存或 chiplet 定量数据。
- **Huawei**：用 UB 互连在 ClusterBench 中做内存借用，Redis 1.33× 超配吞吐 +23%〔P114 p16〕。
- **NTT/IOWN**：跨 APN 的 PD 分离推理把 CPU 内存 + CXL 内存作为 T2 KV 层（架构自报）〔P158 p15〕。
- **OpenAI/AWS/Oracle**：本方向无一手讲稿。OpenAI Jalapeño 只在 Nallasway 的对比中作为 HBM4 基线出现〔P450 p4, p8〕。

### 4.2 芯片、内存与系统厂商站位

- **内存三家**：Samsung 讲池化+DCD、PNM、NDC API 与 SPEL 软件，并以 keynote 提出"内存为中心"推理中心〔P060〕〔P334〕〔P354〕；SK hynix 讲 MARS 机柜级池、CMM-Ax 计算内存、HBF〔P268〕〔P326〕〔P325〕，并在 HBM5/iHBM 上被 Marvell、GUC 引用〔P070 p9〕〔P075 p7〕；Micron 只给建模框架，结论是"容量决定可达复用范围"〔P062 p2, p7〕。
- **Marvell**：覆盖面最广——定制 HBM base die 与 SBD D2D〔P070〕、Structera 全系 CXL 扩展/交换/计算内存〔P063〕〔P060 p24〕、光互连内存设备 PFMA 与 PF-Chiplet（Celestial AI 收购后产品线）〔P063 p4, p6〕〔P338 p3〕。
- **Astera Labs**：不走 CXL，用 PCIe P2P 内存控制器 + 320 lane Scorpio 交换，强调 GPU 侧零改动〔P059〕〔P243 p8, p10〕；VCSEL 光 PCIe POC 中也用到 Scorpio〔P444 p5〕。
- **XCENA**：MX1 3,072 核 RISC-V NDP 与 Maru 共享内存软件〔P329〕〔P060 p14〕。
- **GUC/TSMC 生态**：GLink 私有 D2D、DRAM-on-Compute、COUPE CPO、System on Wafer、IVR〔P075〕；MediaTek 以 Hybrid CoWoS 与 3.5D 面积为卖点，2027 年 TAM \$70–80B、份额目标 15–20%（自报预测，看图划改）〔P287 p5, p6, p12〕。
- **Arm/Cadence/Synopsys**：Neoverse CSS N4（3 个 UCIe D2D、CXL 3.x）、9 个月到 tape-out、节省 80 工程师年〔P068 p5〕〔P064 p24〕；Cadence 224G SerDes I/O chiplet 可配 UALink/Ethernet〔P068 p9〕。
- **Credo/Nallasway、Eliyan、Baya、Tenstorrent**：分别推 VSR 串行内存与 LSI〔P067〕〔P450〕、BoW 光 D2D〔P071〕、非阻塞片上 fabric〔P064 p39〕、Open Chiplet Atlas〔P064 p30–p35〕。
- **d-Matrix**：SRAM → 3D DRAM → 多层堆叠 DRAM，明确不用 HBM/CoWoS〔P286 p11, p17, p24〕。
- **光 I/O 初创与器件商**：Lumentum（VCSEL）〔P444〕、LightXcelerate（µVCSEL+MCF）〔P338〕、Avicena（µLED）〔P339〕、Quintessent（QD 光源）〔P340〕、Ayar Labs（微环 CPO，与 Wiwynn）〔P342〕、Lightmatter（面阵光 I/O 与 MHS 契约）〔P455〕、GO（MRM CPO OE）〔P321 p15〕。

### 4.3 OCP 标准/工作流进展

| 工作流 | 状态 | 索引 |
|---|---|---|
| FCSA | 1.0.0 于 2026-02 发布；1.1.0 正式发布 2026-10-12，新增安全章节；v1.2 候选含功能安全、RAS、时间同步、AMBA C2C 对齐 | 〔P079 p4〕〔P076 p15, p17〕 |
| FCSA Physical AI 子项目 | 新成立，6 约束 → 10 需求域；v1.0.0 目标 Q3 2027；不含 D2D 物理/链路层 | 〔P073 p7, p10, p11〕 |
| BoW.Flexi | 1.0 于 2026-09 发布，计划提供参考 RTL | 〔P079 p5〕〔P069 p9〕 |
| OCE TLL | 2.0 新增 UCIe/BoW.FLEXI binding，仅 Link Layer 保留 1.x 兼容 | 〔P065 p5〕 |
| OCE LSI | Credo 贡献，Phase 1 spec 目标约 2026-11 | 〔P067 p13〕〔P079 p4〕 |
| Chiplet 固件栈（CMI/SCMI） | over I3C 已完成待批准（v0.93 终审）；over UCIe 审阅中/未启动（两份材料表述不一致，存疑）；over BoW 初稿；UCIe/BoW 映射目标 2027 年初 | 〔P079 p4〕〔P078 p9, p10〕 |
| Open Chiplet Atlas（Tenstorrent） | System Arch Spec 与 AoU Spec 草案 v0.8；Harness Beta 2026-10 以 Apache 2.0 发布；v1.0 EOY（看图） | 〔P064 p32, p33, p35〕 |
| 联邦 chiplet 仿真（CDXML） | POC Phase 1：2 chiplet、1 封装，仅功耗+热 | 〔P072 p15〕 |
| OCP-OCE 光互连 WG | 正在组建 | 〔P071 p18〕 |
| CMS Memory Fabric Orchestration | 白皮书 Rev 1.1；GitHub CFM 参考实现 | 〔P061 p2〕 |
| DCC/NDC | 第一篇论文 2025-08 发布，NDC Framework 起草；Samsung NDC API 参考实现；Cognos 2026-10 开源计划 | 〔P330 p2, p10〕〔P327 p10〕 |
| KMRx 密钥分发 | v0.7 发布于 OCP Security Hub，跨 chiplet 借 UCIe CTA | 〔P054 p7, p18〕 |
| UALink（外部） | Chiplet 1.0 于 2026-04；Compliance 1.0 4Q26；Chiplet 2.0 2027 | 〔P144 p8〕 |
| HBF（外部联盟） | v0.7 于 2026-07 公开；Spec 1.0 预期 2027-01；HBF Cube 2028-1Q | 〔P268 p17〕 |
| MX 数值格式 | MX 1.1 澄清版 | 〔P139 p5–p8〕 |

Marketplace 浏览量 28,497、同比 +60%〔P079 p6〕，这是 OCE 唯一给出的生态采用数字，量级很小。

---

## 5. 分歧与未决问题

**5.1 UCIe 够不够用。**
- 认为不够：GUC 称 UCIe 架构复杂、带来额外功耗与延迟，多数场景无需标准合规〔P075 p4〕；Marvell 称 UCIe 不是为下一代 HBM 带宽密度设计〔P070 p14〕；LBNL 认为 >40 µm bump pitch 的标准接口落后于 10–25 µm 封装演进〔P066 p20, p28〕。
- 认为是必要底线：Arm CSS N4 直接集成 3 个 UCIe D2D〔P068 p5〕；TLL 2.0、FCSA、SCMI over UCIe 都把 UCIe 当作承载层〔P065 p9〕〔P078 p5〕；Eliyan 在 EIC 终结 FEC 的光引擎里首选 UCIe〔P071 p8〕。
- 未决原因：高性能场景（HBM base die、3D 堆叠）多是单一厂商控制的封装，互操作需求弱；真正多厂商的场景（MCU、模拟、I/O chiplet）又更在乎成本，走 BoW.Flexi。中间地带有多大，没有材料给出市场数据。

**5.2 KV 卸载池用什么协议接 GPU。**
- CXL：Samsung、SK hynix、XCENA、Marvell Structera 系列〔P060〕〔P326〕〔P329〕〔P063 p5〕。
- PCIe P2P（GPU 侧无 CXL）：Astera〔P059 p3〕，Marvell 的 KV 卸载数据也走 PCIe P2P DMA〔P063 p14〕。
- UALink load/store：Alibaba 下一代〔P057 p9〕，但延迟 0.4× 的估算讲者自己注明基线路径待验证〔P057 p12〕。
- 柜间 RDMA：SK hynix MARS〔P268 p7〕；而 Marvell 实测 64 MB 块 Structera 延迟 1,325 µs vs RDMA 23,199 µs〔P063 p17〕。
- 未决原因：GPU 厂商目前不暴露 CXL.mem，各家只能在 PCIe 或 scale-up fabric 上绕行；本方向没有 NVIDIA 讲稿回应。

**5.3 收益到底来自容量还是介质。** 判断1 已说明：Astera 同容量持平〔P059 p6〕，Micron 显示过阈值后容量作用很小〔P062 p12〕。各家宣传的 3×–5.6× 多数以"重算"为基线。缺少的是同容量、同成本下 CXL DRAM vs CPU DRAM vs SCM 的系统对比；Alibaba 的 iso-cost 实验是唯一接近的〔P057 p8〕。

**5.4 HBM 改造 vs 绕开 HBM。**
- 改造方：Marvell、SK hynix 押定制 base die 与混合键合〔P070 p4, p8〕。
- 绕开方：GUC DRAM-on-Compute〔P075 p8〕、Nallasway LPDDR 串行〔P450 p8〕、d-Matrix 3D DRAM〔P286 p24〕、SK hynix 自己也推 HBF 作补充层〔P268 p15〕。
- 未决原因：替代方案的数字全是自报或目标；DRAM-on-Compute 的 125°C、LPDDR 串行方案 600 条差分对的基板损耗（"VSR 预算约 25 dB?"原文带问号）都没有实测闭合〔P075 p8〕〔P450 p15〕。

**5.5 PNM 是否值得标准化。** Samsung、SK hynix、XCENA、Marvell 给出强收益〔P060 p27〕〔P326 p12〕〔P329 p21〕；但 DCC 面板主张先做基准，"没有设备能赢所有负载"〔P327 p12〕；Arm 称中间缺少转换层（"领结问题"）〔P332 p10〕。三条软件集成路径 Samsung 都试过，只有自研扩展库跑通〔P334 p2, p11〕。

**5.6 CXL 舰队可运维性。** Meta 现网收益是真的，但故障分类覆盖枚举、运行时、内存三类，且未给故障率数字〔P058 p11–p13〕；AiVRES 现场案例同样是 PCIe Completion Timeout 导致整机挂死、BMC 零日志〔P267 p3, p7〕。池化把一个设备的故障半径扩大到多台主机，这一点没有任何讲稿给出量化。

**5.7 封装内光 I/O：宽慢 vs 快窄，以及"光是否进封装"。**
- 宽慢方给出的是目标值：µLED <1 pJ/bit〔P339 p8〕、µVCSEL <1.5 pJ/bit〔P338 p6〕；Lumentum 呼吁先统一 pJ/bit 的系统边界定义〔P444 p6〕。
- Avicena 的立场是"能用铜就用铜"〔P339 p3〕；TE 用 CPC 把铜推到 448G 封装出口〔P461 p5〕；GO 认为 NPO 是近期甜点、CPO 晚于 NPO〔P321 p3, p5〕。
- 可靠性门槛：scale-up 光学需达到无源铜可靠性，Marvell 估算 "2025 模型" 约每 48 秒一次 flap〔P345 p7, p11〕。
- 未决原因：除 Meta CPO 交换机数据（被引用）外，封装内光 I/O 没有现网可靠性数据；µVCSEL 32 Gb/s 眼图 mask margin 只有 5.5%〔P338 p10〕。

**5.8 标准碎片化风险。** OCE TLL、OCE LSI、Tenstorrent OCA（含 AXI over UCIe）、Arm FCSA、UALink Chiplet 同时推进〔P065〕〔P067〕〔P064 p32〕〔P079 p4〕〔P144 p8〕。OCE 自己承认"无组织拥有完整开放系统结果"〔P079 p2〕。

---

## 6. 判断与时间线

### 6.1 未来 12–36 个月里程碑

| 时间 | 事件 | 依据 | 索引 |
|---|---|---|---|
| 2026-10 | FCSA 1.1 正式发布（安全章节）；OCA Harness Beta（Apache 2.0）；Samsung Cognos 开源计划；SPEL 开源 | 标准/自报 | 〔P076 p15〕〔P064 p33〕〔P327 p10〕〔P334 p14〕 |
| 2026-11 | OCE LSI Phase 1 spec（约）；Fujitsu MONAKA 全球销售（CXL 3.0） | 自报计划 | 〔P067 p13〕〔P309 p9〕 |
| 2026-Q4 | UALink Compliance 1.0；MediaTek 首个量产设计出货；OCA v1.0（EOY） | 路线图 | 〔P144 p8〕〔P287 p5〕〔P064 p35〕 |
| 2027-01 | HBF Spec 1.0（预期） | 预测 | 〔P268 p17〕 |
| 2027 年初 | SCMI 对 UCIe/BoW 映射 | 标准进度 | 〔P078 p10〕 |
| 2027 | OCE 主题从"定义标准"转为"证明互操作"；UALink Chiplet 2.0；GO 400G/800G OCI OE；1.6T–6.4T µLED 光引擎（"即将推出"） | 自报/路线图 | 〔P079 p8〕〔P144 p8〕〔P321 p7〕〔P339 p13〕 |
| 2027-Q3 | FCSA Physical AI profile v1.0.0 | 计划 | 〔P073 p11〕 |
| 2027–2028 | OPEN NPO Phase II 高密度电接口（1000+ radix）；LPO/NPO/CPO 指数增长（引用 LightCounting） | 预测 | 〔P440 p7〕〔P321 p5〕 |
| 2028 | 8→16-high HBM 越过 2.5D 热预算；HBF Cube 可用（1Q）；GO 1.6T+ OCI OE | 引用/预测 | 〔P070 p7〕〔P268 p17〕〔P321 p7〕 |
| 2029 | HBM5 量产（24–32 Gbps，约 90 W/栈） | 引用 SK hynix | 〔P075 p7〕 |
| 2029–2030 | OPEN NPO Phase III 定义 OIO 光接口 | 预测 | 〔P440 p7〕 |

我的判断：12 个月内会落地的是 CXL/PCIe 内存扩展在推理节点上的增量部署（AliSCM、Structera、Leo 都已量产或在出货〔P057 p4〕〔P243 p8〕），以及 FCSA/BoW.Flexi 这类"标准已发布、等实现"的工作。机柜级共享池要等 DCD、多主机一致性和舰队可调试性三件事，Meta 的呼吁〔P058 p16〕和 CMS MFM 的编排工作〔P061〕说明这一步还在 2027 年以后。封装内光 I/O 在 2028 年之前大概率停留在 demo 和 POC，OPEN NPO 把 OIO 光接口排到 2029–2030〔P440 p7〕，这个时间点与其他材料相互印证。

### 6.2 对各类厂商的含义

- **芯片商**：HBM PHY 和控制器移入定制 base die 后，XPU 厂商与内存厂商的分工边界会重新谈判〔P070 p4〕。D2D IP 的竞争点是 pJ/bit 和 Tbps/mm，标准合规只是入场条件〔P075 p4〕。CXL/PCIe 交换与内存控制器（Marvell、Astera、XCENA）成为新的独立品类，但要等 GPU 侧开放 load/store 路径才能做大。
- **内存厂商**：卖点从"每 GB 价格"转向"每 token 成本"，三家都在做计算内存与软件栈〔P060〕〔P326〕〔P062〕。HBF 和 SCM 抢的是 HBM 与 SSD 之间的同一层。
- **光模块/光器件商**：封装内光 I/O 的订单要等 2027–2028 年；近期机会在 ELSFP/外置光源（Quintessent、Ayar Labs）和与 OSAT 兼容的阵列器件〔P340 p14〕〔P338 p8〕。宽慢路线需要先拿出现场可靠性数据，Lumentum 自己的冗余路数表（1.6T 需 30–54 路才能 FIT<1）说明可靠性要靠冗余换〔P444 p3〕。
- **系统/设备商**：内存机柜、CXL 交换托盘、PCIe scale-up 托盘会成为新 SKU（Astera Orion、Samsung 20 TB 机架、Marvell PFMA）〔P243 p6〕〔P060 p23〕〔P063 p4〕；BMC 侧需要支持 CXL 设备内部遥测〔P058 p16〕〔P267 p26〕。

---

## 7. 推荐配图清单

| 索引 | 图中内容 |
|---|---|
| 〔P455 p2〕 | 铜/CPO/面阵光 I/O 逃逸带宽几何对比（26/93.6/1,191 Tb/s/dir）与 HBM 占边后 XPU 侧剩余带宽 |
| 〔P070 p5〕 | HBM 单栈带宽 2020–2028 路线图（0.5→7.2 TB/s） |
| 〔P070 p7〕 | 2.5D 封装热阻分解，HBM 占 57% |
| 〔P070 p10〕 | Marvell SBD D2D 功耗 100%/58%/25% |
| 〔P075 p4〕 | UCIe-S/A 与 GLink-LL 对比表 |
| 〔P075 p8〕 | DRAM-on-Compute vs 6×HBM4E 对比（带宽、延迟、pJ/bit、温度） |
| 〔P450 p8〕 | 四种内存挂接方式容量/带宽/面积对比 |
| 〔P063 p6〕 | KV 层级 G1–G4 与 G1.5/G2.5 |
| 〔P354 p4〕 | Samsung L0–L4 内存层级与 pod 划分 |
| 〔P059 p6 / p8〕 | 同容量持平 vs 大容量 3× 的对照（用于说明收益来源） |
| 〔P060 p8〕 | KV 超 DRAM 容量后 CXL 池维持吞吐 5.6× |
| 〔P060 p27〕 | 10 PNM 向量检索 64× QPS、65× 能效 |
| 〔P062 p12〕 | KV 层容量阈值的阶跃曲线 |
| 〔P057 p8〕 | AliSCM iso-cost KV offload 实测 |
| 〔P058 p14〕 | CXL"一个症状多个成因"可观测性边界图 |
| 〔P058 p15〕 | Meta CXL 现网收益表 |
| 〔P079 p3〕 | OCE 工作流全景 |
| 〔P078 p5〕 | OCP Chiplet 固件栈分层（SCMI/MCTP/FCSA） |
| 〔P069 p4〕 | BoW.Flexi vs BoW 2.0 规格对比 |
| 〔P071 p4〕 | 铜→光过渡速率×距离表 |
| 〔P071 p14〕 | 8×BoW-SP x4 构成 1.6T 宽慢光模块 |
| 〔P444 p3〕 | VCSEL 1.6T–12.8T 架构与 FIT<1 冗余路数 |
| 〔P339 p8〕 | µLED 对照七项需求的指标 |
| 〔P342 p8〕 | CPO 封装热仿真 Tj 表（SoC/HBM4/OE） |
| 〔P010 p27〕 | 结→冷却液热阻构成（冷板/TIM/硅） |

---

## 8. 与 ECOC 2026 的对照

ECOC 方向4 底稿主题是 Scale-up/in（CPO/NPO/XPO、WSE、OCS），scale-in 只占其中一小节（2.9 晶圆级/3D 光 I/O）和若干散点；HBM、CXL、chiplet 标准在 ECOC 底稿中基本没有出现。以下只对照封装内与光 I/O 部分。

### 8.1 一致

1. **宽慢光 I/O 的能效是纸面优势，缺现场可靠性。** ECOC 判断5 称宽而慢"尚缺现场数据"，OpenAI 认为需要现场验证〔0920-pm-Su4-I-02-OpenAI p11〕；OCP 侧 µLED、µVCSEL 给的都是目标值〔P339 p8〕〔P338 p6〕，Lumentum 要靠 30–54 路冗余换 FIT<1〔P444 p3〕。
2. **Lumentum VCSEL 寿命数据两边一致。** ECOC：1060 nm VCSEL 115°C（Tj 181°C）8 mA 下 5000 h 无失效〔We5-I Lumentum p13、p15〕；OCP：同条件 HTOL 5000 h〔P444 p2〕。是同一组数据在两个会议复用，不应算作两份独立证据。
3. **pJ/bit 核算边界需统一。** ECOC 判断2 引 Coherent 要求先统一核算边界〔0920-pm-Su4-I-04-Coherent p5〕；OCP 侧 Lumentum 呼吁统一 pJ/bit 系统边界〔P444 p6〕，Avicena 把主机 SerDes >5 pJ/bit 算进现有光学基线〔P339 p5〕。
4. **scale-in 毫米级走宽慢。** ECOC 引 LightCounting：scale-in 毫米级"wide-slow，未来或为光"〔0920-pm-Su3-A-01-LightCounting p3、p5〕；OCP 侧 GLink-LL 4–8 Gbps 宽并行〔P075 p4〕、BoW.Flexi 0–4 Gb/s/pin〔P069 p4〕、LBNL 的 NiP 设计都是"慢而宽"的电版本〔P066 p18〕。
5. **可靠性是 scale-up/in 光学的决定性约束。** ECOC 判断3〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p38〕；OCP 侧 Marvell flap 估算与 Microsoft 故障域分析〔P345 p11, p32〕。

### 8.2 OCP 新增

1. **内存层级是 OCP scale-in 的主体。** CXL 池化、KV 卸载、PNM、SCM 在 OCP 有 20 余篇讲稿和 Meta 现网数据〔P058 p15〕〔P057〕〔P060〕〔P063〕；ECOC 方向4 只在需求表中出现 Microsoft Azure 的内存解耦指标（<5 ns、<4 pJ/bit、1–3 m→20–50 m）〔0921-Mo4-待定-MicrosoftAzure p3、p6、p8〕。
2. **HBM 作为封装热与成本瓶颈的定量拆分**（57% 热阻、>50% XPU 成本）〔P070 p3, p7〕及 DRAM-on-Compute 等替代路线〔P075 p8〕，ECOC 无对应内容。
3. **D2D 电互连的定量对比**（UCIe vs GLink vs SBD）〔P075 p4, p5〕〔P070 p10〕。ECOC 带宽阶梯只给出 die-to-die 相对比例 100%〔0921-Mo12-A3-Ciena p33〕。
4. **Chiplet 系统层标准**（FCSA 1.1、BoW.Flexi 1.0、TLL 2.0、SCMI/MCTP、OCA）〔P079 p4, p5〕〔P078 p5〕〔P064 p32〕，ECOC 无。
5. **光 D2D 接口选型**（UCIe vs BoW 取决于 EIC 是否终结 FEC）〔P071 p8, p13〕，ECOC 只提 Qualcomm 光 D2D <2.5 pJ/bit 路径〔0920-pm-Su3-I-04-Qualcomm p6、p7〕。
6. **光互连内存设备**：Marvell PFMA（16 路 × 2 Tbps、<350 ns）〔P063 p4〕与 Samsung "HBM over Optical"〔P354 p4〕，把光 I/O 用在内存解耦上，对应 ECOC 中 Microsoft OCI Wave 2"拓展内存解耦"的方向〔0921-Mo4-待定-MicrosoftAzure p1〕，但 OCP 给出了产品级参数。

### 8.3 矛盾或口径差

1. **面阵/3D 光 I/O 的量级。** ECOC 中 Lightmatter Passage M1000 为 114 Tbps（Tx+Rx），训练时间等指标均为仿真〔0924-推定F2-Lightmatter p2–p4、p9〕；OCP 中 Lightmatter/Dell 引白皮书称面阵光 I/O 1,191 Tb/s/dir〔P455 p2〕。两者相差一个数量级，前者是产品，后者是几何上限推算，不能并列为"已实现"。
2. **宽慢路线的 pJ/bit。** ECOC 中 TeraHop 横比图 uVCSEL 约 5.75、uLED 约 6.0 pJ/b（读图）〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p63〕；OCP 中 Avicena 目标 µLED <1 pJ/bit〔P339 p8〕、LightX-1 <1.5 pJ/bit〔P338 p6〕。差距来自核算边界（是否含 gearbox、驱动、激光）与"目标 vs 实测"，具体哪部分材料未拆分。
3. **CPO scale-up 时间。** ECOC 判断1：Ciena 判断 CPO scale-up 在 2027/28〔0920-pm-Su3-I-05-Ciena p10〕；OCP 侧 OPEN NPO 把 OIO 光接口定义排到 2029–2030〔P440 p7〕，GO 的 1.6T+ OCI OE 在 2028+〔P321 p7〕。若"进封装的光 I/O"按 OPEN NPO 口径，时间比 ECOC 主流判断晚 1–2 年。两者定义不同（CPO 光引擎 vs 标准化 OIO 接口），我倾向于把它理解为"先有私有 CPO，后有开放 OIO 标准"，而不是互相否定。
4. **铜的边界。** ECOC 引 OpenAI：200G、400G 铜缆约 1 m（读图）〔0920-am-Su1-B-02-OpenAI p4〕，Marvell 200G 2.5 m、400G 1.25 m〔0920-pm-Su4-H-04-Marvell p5〕；OCP 中 Eliyan 给 200G 无源铜约 1–2 m、有源铜约 4 m，400G 约 2 m 有源铜〔P071 p4〕。各家数字在 1–4 m 之间，取决于有源/无源与线规，比较时要带条件。

---

## 索引对照表

| 索引 | 机构 | 题目简写 |
|---|---|---|
| P010 | Shield/Corintis/Meta/Microsoft/Google | 单相冷板极限（面板） |
| P045 | Google | Confidential Storage |
| P054 | Marvell/NVIDIA | SoC 硬件块密钥分发（KMRx） |
| P056 | Microsoft/Xcena/Seagate/Meta | 内存墙面板 |
| P057 | Alibaba Cloud | CXL 字节寻址持久内存（AliSCM） |
| P058 | Meta | 超大规模 CXL 故障与可调试性 |
| P059 | Astera Labs | P2P GPU-内存扩展数据路径 |
| P060 | Samsung/XCENA/Tensormesh/Marvell | 解耦 CXL 内存：池化、共享、PNM |
| P061 | Seagate/Samsung | CMS Memory Fabric Manager |
| P062 | Micron | KV 卸载分层内存建模 |
| P063 | Marvell | XPU 级可组合智能内存 fabric |
| P064 | Arm/Tenstorrent/Microchip/Baya 等 | 虚拟 chiplet 生态（面板） |
| P065 | VeriSilicon | OCE TLL 2.0 |
| P066 | LBNL | 开放 chiplet 架构与 AI 数据流 |
| P067 | Credo/Nallasway | OCE 轻量串行互连 LSI |
| P068 | Arm/Cadence | Neoverse 与 Cadence chiplet |
| P069 | Infineon/YorChip | BoW.Flexi 1.0 |
| P070 | Marvell | 定制 HBM：base die、D2D、封装热 |
| P071 | Eliyan | 光 chiplet 的 D2D 方案 |
| P072 | Ratchkov/Cameron | 联邦 chiplet 设计仿真 |
| P073 | Cadence/imec/Secure-IC | FCSA Physical AI 子项目 |
| P075 | GUC | 扩展 AI 计算、内存与连接 |
| P076 | Arm/Secure-IC | FCSA 安全架构 |
| P078 | GSOC/AMD | 多厂商 chiplet 系统级标准 |
| P079 | Palo Alto Electron/Microchip/Arm | Open Chiplet Economy 进展 |
| P114 | Huawei | AI 集群基准（ClusterBench） |
| P139 | Microsoft 等 | MX v1.1 |
| P144 | UALink Consortium | UALink 生态（面板） |
| P158 | NTT 等 | AI Computing Continuum |
| P243 | Astera Labs | 计算无关机柜级架构（Orion） |
| P267 | AiVRES | AI 数据中心诊断维护 |
| P268 | SK hynix | MARS 内存中心机柜系统 |
| P275 | Hyve | 开放模块化机柜级 AI 基础设施 |
| P278 | ASRock Rack/Arm | 推理基础设施 |
| P286 | d-Matrix | Path to Infinite Inference |
| P287 | MediaTek | AI 经济的硅心跳 |
| P290 | Intel | Agentic Rack（Xeon） |
| P309 | Fujitsu | MONAKA |
| P317 | d-Matrix | Push-mode 通信从 chiplet 到机柜 |
| P321（=P279） | Genuine Optics | NPO 与全栈光互连 |
| P325 | SK hynix/Penn State | 计算内存用于差分隐私训练 |
| P326 | SK hynix | 计算型共享内存池 Agentic 服务 |
| P327 | Marvell/Samsung/XCENA/SK hynix 等 | 开放中间件（面板） |
| P328 | Marvell | 计算-内存 fabric 数据服务 |
| P329 | XCENA | 近数据处理通用并行编程 |
| P330 | Solidigm/Micron | DCC 介绍与现状 |
| P332 | Arm | 近数据处理与上下文工程 |
| P333 | Elephance Memory | 近数据处理开放对象格式 |
| P334 | Samsung | NDP 可扩展框架（SPEL） |
| P338 | LightXcelerate | µVCSEL 阵列 + 多芯光纤 |
| P339 | Avicena | µLED 互连 |
| P340 | Quintessent | 宽慢光互连光源 |
| P342 | Wiwynn/Ayar Labs | CPO 光 scale-up 架构 |
| P345 | Marvell/Ranovus/Microsoft | scale-up 光可靠性与 flap（面板） |
| P354 | Samsung | 推理数据中心 2030 内存 pod fabric |
| P436 | Flex/Lightmatter | 开放硅光参考设计 |
| P440 | Huawei | Open NPO 标准 |
| P444 | Lumentum | 宽慢 12.8T VCSEL |
| P450 | Nallasway 等 | 打破内存容量-带宽权衡 |
| P455 | Lightmatter/Dell | 开放硅光扩展 MHS 平台契约 |
| P461 | TE Connectivity | 448G 封装上铜缆（CPC） |
