---
title: "R14_fti-workshop-data-centric-computing"
tags:
  - OCP2026
  - 讲稿笔记
---

# R14 笔记：fti-workshop-data-centric-computing, expo-hall-sessions

### P321 Scaling-AI-Compute-Fabrics-The-Pivotal-Role-of-NPO-in-Full-Stack-Optical-Interconnects
- 讲者/机构：Haijiang Yu，Chief Scientist / VP R&D，Genuine Optics（GO）[p1] | 类型：厂商展区（Executive Session）
- 方向归属（主/次）：主 [Up 机柜/超节点：CPO/NPO/XPO]；次 [Out 后端网络：可插拔光模块/LPO/LRO]、[In 封装内：光 I/O]
- 核心主张：
  - 形态演进 Pluggable → NPO → CPO，单 lane 100G → 200G → 400G；NPO 是性能、工程可行性与生态成熟度之间的务实方案 [p3][p6]
  - NPO 放量主要由 scale-out 驱动，CPO 主要由 scale-up 驱动且放量晚于 NPO；LPO/NPO/CPO 约 2027–2028 起指数增长 [p5]
  - 自有 SiPh/TFLN + 外置光源（ELSFP/ELS）是全栈光互连的基础；NPO 是近期商用甜点，最终走向 CPO [p16]
- 关键数据：
  - 两年增长率：AI training compute ~100X、HPC/GPU 3.3X、Memory BW 1.4X、Interconnect 1.4X [p4]（自报，未注来源）
  - 2015–2027 增长：模型 FLOP 1000x、GPU 10x、HBM4 带宽 2–3x、NVLink6/PCIe7 互连 1.5x；"Optical interconnect transition begins" 约 2026 [p4]（看图）
  - 光模块+NPO/CPO 端口出货：2031 约 375M 单位，其中 CPO/NPO 约 140M [p5]（看图，引用 LightCounting，读图近似）
  - 2031 NPO 约 89M（scale-out 约 52M / scale-up 约 37M），CPO 约 71M（scale-out 约 25M / scale-up 约 46M）[p5]（看图，引用 LightCounting，读图近似）
  - 按应用销售额 2031 约 \$80B [p4]（看图，引用 LightCounting，读图近似）
  - 路线图：Pluggable 1.6T DR8(2025) → 12.8T XPO/1.6T DR4(2026) → 3.2T DR8(2027) → 25.6T XPO?(2028+)；NPO 3.2T(2025) → 6.4T(2026) → 12.8T(2027+)；CPO/OIO 3.2T MRM CPO OE(2025–26) → 400G/800G OCI OE(2027) → 1.6T+ OCI OE(2028+) [p7]（看图，自报）
  - SiPh 模块出货超百万；>8 billion device hours，PIC FIT <0.2（基于 2 年出货）[p10]（现网，自报）；FIT 由 24Q1 约 6 降到 25Q3 约 0.12 [p10]（看图）
  - 1.6T 功耗：Full DSP <24W、LRO <15W、LPO <10W；loopback BER ~E-13 / ~E-13 / <E-8 [p11]（实验，测试板）
  - 1.6T LRO 在 24dB die-to-die loss 下 BER 达 E-13 量级 [p11]（实验）
  - 12.8T XPO：XPO MSA & CMIS 5.3，SMF 500m，8×MPO-16，功耗 <130W（LRO），典型 130W/80W，TDECQ 2.5dB，BER E-10~E-11 [p12]（实验/demo）
  - 3.2T/6.4T NPO：功耗 <8.5W（光引擎口径未详），≥20 dBm/lane 输出光功率（ELSFP），1311nm，最多 32 通道 100/200G/lane；TDECQ 1.6dB，EVB loopback BER <1E-10 [p13]（demo）
  - 400G/lane 1.6T DR4：电 8×212.5G PAM4、光 4×425G PAM4，3nm 400G DSP，100mW CW 激光 1×4 分光，~30W，500m，BER ~E-6，TDECQ 1.4dB [p14]（demo）
  - 3.2T MRM CPO OE：2×8λ×200G，QD 8λ DWDM comb 激光（每 comb 最大 10dBm），12 层 TGV 玻璃基板，带宽密度 >3 Tbps/mm（单向）[p15]（自报/demo）
  - SiPh PIC：BW >50GHz，Vpi <6V，耦合损耗 <1.5dB/facet，heater <15mW [p9]（自报）
- 提到的公司/客户/产品/标准：Genuine Optics、LightCounting、XPO MSA、CMIS 5.3、OIF、OCI-MSA、ELSFP、NVLink 6、PCIe 7、Vera Rubin、HBM4、CIOE 2026、OFC 2026
- 首次/记录/SOTA 声明：2024 年全球前 8 光模块供应商 [p2]；FIT 数据称 "leadership in the industry" [p10]
- 推荐配图页：p5（LightCounting NPO/CPO 按 scale-out/scale-up 拆分出货预测）；p7（GO Pluggable/NPO/CPO 三轨路线图）

### P323 The-Changing-Course-of-Storage-in-an-AI-World-presented-by-FADU
- 讲者/机构：未见讲者名；FADU Inc. [p2] | 类型：厂商展区
- 方向归属（主/次）：主 [存储]；次 [推理/算力/经济性]
- 核心主张：
  - AI 推理的 KV cache/上下文存储使 SSD 成为 AI 必需；上下文缓存可重算，不需要 RAID/EC 冗余 [p7][p11]
  - PCIe Gen6 时代 AI 上下文存储服务器可改为 DPU 刀片式架构，省去 CPU、PCIe switch 和独立 NIC [p10]
- 关键数据：
  - eSSD 市场从 2024 年 181 EB 增至 2030 年 1,078 EB，CAGR 35%；其中 AI 推理 447 EB，按 \$0.5/GB 计 >\$200B [p8]（引用 McKinsey）
  - 无 AI 情况下 eSSD 需求 CAGR 20% [p6]（引用 McKinsey）
  - 无上下文存储时 GPU 利用率仅 10–20%；60% 被视为经济可行门槛 [p7]（自报）
  - AI 推理存储需求：性能 >1TB/s、容量 >1PB，对比企业常规 10s GB/s、100s TB [p5]（自报）
  - Gen4 时代 2U 24×8TB U.2，单机 192TB，100Gb NIC <12 GB/s/host；24×25W SSD 即 600W [p3]
  - Gen6 方案：400/800G RoCE、每刀片 32 核 DPU 约 125W、64GB DRAM、12×16+TB E3.S、~1 DWPD [p10]（预测）
  - 存储服务器可达 3,000W，普通机柜 <14,000W，一柜可能只放 4 台 [p11]
- 提到的公司/客户/产品/标准：FADU、McKinsey、Nvidia（KV Cache、DPU）、NVMe、RoCE、InfiniBand、pNFS、E3.S
- 首次/记录/SOTA 声明：无
- 推荐配图页：p10（PCIe Gen6 刀片式 AI 推理存储服务器架构）

### P324 Water-or-Glycol-for-D2C-A-Quantitative-Tradeoff-Analysis-Across-Thermal-Operational-and-Programmatic-Domains-presented-by-Ecolab
- 讲者/机构：Dolly Batra, Ph.D., Sr. RD&E Group Leader，Ecolab [p1][p13]；附页为 Ecolab | CoolIT 联合 logo [p14]（看图） | 类型：厂商展区
- 方向归属（主/次）：主 [底座-冷却]
- 核心主张：
  - 水基冷却液导热优于 PG25，但需更强的生物控制与监测；密度上升下问题不在于是否用水，而在于如何运维 [p7][p10]
  - 选型取决于现场化学/服务能力、机柜功率密度、冻结风险等 [p12]
- 关键数据：
  - 50°C 下导热系数 PG25 ~0.49 vs 水基 ~0.63 W/m·K；比热 ~3.9 vs ~4.1 kJ/kg·K；粘度 ~1.3 vs ~0.5 mPa·s [p7]
  - PG 浓度 ≥24% 才有抑菌性；运行范围 24–29% v/v；azole >400 ppm；Cu/Fe <3 ppm（水基 <0.1 ppm）；Ca/Mg <50 ppm（水基 <30 ppm）；Cl/SO4 <25 ppm [p8][p9]
  - 水基微生物计数理想 <1000 CFU/mL [p9]
- 提到的公司/客户/产品/标准：Ecolab（3D TRASAR）、CoolIT、NVIDIA DSX Ready Coolant、OCP 水基/PG 冷却液指南
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（PG25 与水基冷却液属性对比表）

### P325 A-System-Architecture-using-Computational-Memory-for-Differentially-Private-Training
- 讲者/机构：Younghoon Min（SK hynix）、Kiwan Maeng（Penn State）[p1] | 类型：技术分享（FTI Workshop）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [安全]、[推理/算力/经济性]
- 核心主张：
  - CXL Hybrid Memory（DRAM 缓冲 + NAND 后端 + 设备内计算）可把优化器更新与 checkpoint 卸载到设备内，减少 GPU 内存与 PCIe 流量 [p2][p4][p5]
  - 相关噪声 DP 训练的噪声历史体量达 GB–TB，Cocoon-NMP 将噪声分片于 HBM/DRAM/CMM-Ax 并就近做 GEMV，用更少 GPU 训练 [p10][p11][p14]
- 关键数据：
  - GPU 内存占用降 80%（20B/param → 4B/param）；GPU-SSD 传输量降 66%（12B → 4B/param）[p4]（自报）
  - 相对 ZeRO-Offload / ZeRO-Infinity 性能提升 4.40× / 3.62× [p6]（实验）；主机内存不足时 ZeRO-Offload OOM [p6]（看图）
  - 噪声历史（b̂=64）：OPT-350M ~90GB，OPT-1.3B ~333GB，GPT-XL ~400GB，OPT-6.7B ~1.675TB [p10]（实验/计算）
  - CMM-Ax：CXL 2.0 Type 3，PCIe 5.0 x16，DDR5-6400 512GB，200GB/s，16 ARM 核 3.0GHz [p13]
  - 相对纯 GPU 系统可少用 10× GPU；相对无 CMM-Ax 的 CXL 扩展内存，性能提升 1.23–2.32× [p14]（实验，4×A5000 + CMM-Ax）
- 提到的公司/客户/产品/标准：SK hynix CMM-Ax、JBOC、Microsoft ZeRO-Offload/ZeRO-Infinity、Google Gboard、VaultGemma、DP-SGD、OSDI '26
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（传统训练 vs CXL Hybrid Memory 数据流）；p14（Cocoon-NMP 归一化延迟）

### P326 Agentic-AI-Serving-System-with-Computational-Shared-Memory-Pool
- 讲者/机构：Jongryool Kim，Senior Director，SK hynix [p1] | 类型：技术分享（FTI Workshop）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [推理/算力/经济性]
- 核心主张：
  - MARS 多机柜解耦内存：柜内 CXL、柜间 RDMA；用 CXL 池共享 KV cache，避免 HBM/PCIe/网络带宽争用 [p4][p9]
  - 在池侧（CMM-Ax）做 KV 选择（RocketKV Stage 1），只把选中 KV 传给 decode GPU，降低 TTFT 与排队 [p12]–[p17]
  - 池侧 token 共享：复用前缀 token ID、只对新文本分词，减轻 CPU 负载 [p22]
- 关键数据：
  - CXL 池化 LLM serving：TTFT 比 LM-Cache 提升 1.67×，peak goodput 比 NIXL 高 1.9× [p10]（实验）；并发 100 时 goodput 约 4.0 vs LMCache 约 2.0 vs NIXL 约 1.5 req/s [p10]（看图，读图近似）
  - KV 选择平均缩减约 ×30 [p12][p14]（自报）
  - ARCEE trace：TTFT 398.45 / 524.04 / 709.47 ms（池+KV 选择 / 池 / Mooncake）；E2E 2,084.40 / 4,345.64 / 4,765.77 ms [p18]（看图）
  - Opus-4.5 trace：TTFT 472.99 / 711.65 / 802.38 ms；E2E 3,794.94 / 4,426.41 / 4,838.85 ms [p18]（看图）
  - 正文称相对 Mooncake 1.4× TTFT、2.29× E2E（Arcee trace）[p18]；按图中 TTFT 数字计算约 1.78×，TTFT 倍数存疑
  - 25.6K 输入 token、前缀复用 96%：去掉文本分词 TTFT ≈345→≈215 ms（约 38%）[p20]；C-CXL token 共享后分词时间 ≈130→≈6 ms（约 95%），TTFT ≈345→≈221 ms（约 36%）[p23]（实验）
  - 去掉图像分词 TTFT 改善 1.80×（轻载）/1.76×（中载）[p21]（实验）
  - CMM-Ax 3.0：FH¾L AIC，CXL 2.0 Type 3，PCIe 5.0 x16，DDR5-6400 4ch 512GB 200GB/s，16 Neoverse V2 3.0GHz [p16]
  - 编码 agent 负载前缀 KV 命中率约 96% [p20]（引用，未注来源）
- 提到的公司/客户/产品/标准：SK hynix（MARS、CMM-Ax、Niagara 2.0）、NVIDIA Dynamo、NIXL、LMCache、Mooncake、vLLM、RocketKV、SnapKV、Structera CXL、FMS 2025、SC 2025
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（MARS 多机柜解耦内存架构）；p18（池侧 KV 选择 vs Mooncake 延迟柱状图）

### P327 Beyond-the-Monolith-Open-Middleware-for-Heterogeneous-AI-Infrastructure-at-Hyperscale
- 讲者/机构：主持 Gaurav Agarwal（Marvell）；Chris Gottbrath（Gottbrath Technologies）、Mayank Saxena（Samsung）、Harry Kim（XCENA）、Youngpyo Joo（SK hynix）[p1] | 类型：面板
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [推理/算力/经济性]
- 核心主张：
  - 需要稳定、可移植、多厂商互通的 API，把 AI 框架接到计算内存/存储（CxD）；标准化"交接契约"而非执行路径 [p2][p10]
  - PyTorch PrivateUse1、Dynamo/Inductor/Triton 是现成集成点，但可能需要新框架概念来组合非一致内存与计算 [p7]
  - 先基准、后接口：没有设备能赢所有负载，否则统一中间件会变成"杂物抽屉" [p12]
- 关键数据：
  - 无定量数据；Samsung Cognos（异构 AI 内存 fabric 组合）计划 2026 年 10 月开源 [p10]
  - 已有硬件：Intel Xeon+Agilex（CXL）、Marvell CXL 加速板、Samsung CXL-PNM、SK hynix AiMX（GDDR6-AiM）、XCENA、Panmnesia PanSoC [p3]（看图）
- 提到的公司/客户/产品/标准：Marvell、Samsung、XCENA、SK hynix、Panmnesia、Intel、ONNX、PyTorch、Triton/TLX、OpenReg、IBM Spyre、Huawei Ascend、Cambricon、UALink、Arrow
- 首次/记录/SOTA 声明：无（图中 Samsung 标 "Industry's 1st CXL-PNM" [p3]，看图）
- 推荐配图页：p3（异构计算内存产品拼图）

### P328 Bridging-Compute-and-Memory-Fabric-Data-Services-for-Direct-XPU-Access
- 讲者/机构：Gaurav Agarwal，Senior Distinguished Engineer，Marvell [p1] | 类型：技术分享
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [存储]
- 核心主张：
  - 在加速器优先架构中，CPU 中转 I/O 是瓶颈；XPU 直驱 I/O 仍有 I/O 放大问题 [p5]–[p7][p13]
  - 近数据处理降低数据搬移与 fabric 带宽需求；建议以"数据服务"模型（分层放置、加速数据路径、统一 API）服务 XPU [p12][p13]
- 关键数据：
  - 向量检索（1M 向量、384B/向量、batch 16K、top-10、~600 次比较）：主机拉取原始数据 ~3.8GB vs 卸载后拉结果 ~64MB，数据搬移降 60× [p9]（计算，引用 Marvell OCP 2025）
  - Embedding 查表聚合（batch 2K、8 表、每表 10 次查找、128 维 FP32）：84MB → 8.4MB，10× 缩减 [p11]（计算，引用 CARINA）
  - CPU 驱动 I/O 每操作延迟 O(µs)；HNSW 图节点 O(100B) [p5][p8]
- 提到的公司/客户/产品/标准：Marvell、FAISS、HNSW、GDS、CLAY、CARINA
- 首次/记录/SOTA 声明：无
- 推荐配图页：p9（向量检索近内存计算 60× 数据缩减示意）

### P329 Bringing-General-Purpose-Parallel-Programming-to-Near-Data-Processing
- 讲者/机构：Harry Kim，Chief Product Officer，XCENA [p1][p23] | 类型：技术分享
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [存储]
- 核心主张：
  - "Don't copy data. Move computation"：在 CXL 内存中原地分配，由内存侧核计算；主机与设备共享统一虚拟地址，支持指针追逐与细粒度卸载 [p7]–[p9]
  - 线程池而非 SIMT 执行，靠大量并发隐藏 CXL 长延迟 [p13]
- 关键数据：
  - MX1P：3,072 个 RISC-V MU 核、24 子系统，FP32/FP16 向量引擎；4ch DDR5-8400 最高 2TB；CXL 3.2 Type 3、PCIe Gen6；SSD 挂在根端口作 CXL 内存 [p3]
  - MX1P（PoC）PCIe Gen6 x8 CXL + x8 PCIe；MX1（量产）Gen6 2×8 CXL + 2×4 PCIe [p4]
  - 每子系统 128 线程 [p13]
  - 向量索引吞吐（相对 CPU = 1×）：Flat 4.81×、IVF-Flat 1.99×、IVF-RaBitQ 1.92×、HNSW 1.65×，称随 MX1P 设备数线性扩展 [p21]（实验，CPU 为 Intel GNR 6767P sub-NUMA 32 核 4ch；数值对应 1 台或 2 台未能从文字层确定）
  - 采用 CXL 3.x Back-Invalidation（HDM-DB）保持主机缓存一致 [p11]
- 提到的公司/客户/产品/标准：XCENA（MX1/MX1P、PXL、PXCC、XFLARE）、FAISS、Spark SQL、Gluten-Velox、Substrait、Arrow、LLVM、QEMU
- 首次/记录/SOTA 声明：无
- 推荐配图页：p3（MX1P 规格总览）；p21（CPU vs MX1P 向量索引吞吐）

### P330 DCC-Introduction-and-State-of-the-Art
- 讲者/机构：Jason Molgaard（Solidigm）、Sakul Gupta（Micron）[p1] | 类型：标准进展（FTI Workshop 开场）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [存储]、[推理/算力/经济性]
- 核心主张：
  - 近数据计算（NDC=DCC）分四类：PIM、PNM、计算存储、DPU；差距在软件而非芯片，是框架集成问题 [p4][p5]
  - 开放格式（Arrow、HDF5、ONNX、Substrait）是契约；以 SNIA CS API v1.1 为基础推广到所有 NDC 类别 [p7][p8]
  - LLM serving 正变成数据搬移问题，路线 NOW 证明价值 → NEXT 收敛接口 → SCALE 系统编排 [p11][p13]
- 关键数据：
  - 白皮书 Table 1 实测增益：PIM 10–23.2× 性能、1.64–5.23× 能效；PNM 1.39–1.77×、31.6% 能耗；CS 4.3×、36%；DPU 54×、24–29% [p4]（引用 paper one）
  - 数据中心 2022 年耗电 240–340 TWh；爱尔兰数据中心占用电从 5%（2015）到 21%；>92% 服务器已虚拟化；IEA 预计 4 年内 AI 与数据中心用电翻倍 [p3]（引用）
  - SNIA CS API v1.1 于 2025 年 5 月批准，30+ 函数 [p8]
  - 第一篇论文 2025 年 8 月发布，第二篇（NDC Framework）起草中 [p2]
  - 已运行：Samsung 贡献 NDC API 参考实现；LLaMA 3.2-1B GEMV 卸载到 PNM；FAISS IVFFlat 在索引所在处执行 [p10]
- 提到的公司/客户/产品/标准：Solidigm、Micron、Samsung、SNIA CS API、SDXI、Redfish、CXL FM API、OpenXLA、Triton、IREE、ExecuTorch、FAISS、Arrow、HDF5、Substrait、OneMCC、DOCA、ROCm、UALink、SmartSSD、ScaleFlux
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（四类 NDC 设备与增益）；p12（面向 LLM serving 的数据中心化架构）

### P331 Deep-dive-into-what-allows-1-million-GPUs-talk-to-thousands-of-smart-devices
- 讲者/机构：主持 Pankaj Mehra（Ohio State / Elephance Memory）；Galen Shipman（LANL）、Anand Jayarajan（NVIDIA/U Toronto）、Evangelos Georganas（Intel）、Atharva Chougule（Stanford）[p1] | 类型：面板
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [In 封装内：CXL/内存池化]
- 核心主张：
  - 需要标准 API，让开发者在 10 万级 GPU 与万级 DCC 设备间放置函数与数据；关键是标准化常用分区函数、尽量避免跨分区通信 [p2]
  - HPC 经验：Hilbert 空间填充曲线兼顾负载均衡与 ghost 数据比 [p9]；SFC-CA GEMM 达到通信下界 [p16]
  - 稀疏张量负载均衡分区是搜索问题，取决于数据分布 [p30][p33]
- 关键数据：
  - SFC-CA GEMM（~30 行 C++）：Emerald Rapids 64c 最高 2.6×、WHM 1.45×；Granite Rapids 128c 最高 5.5×、WHM 1.8×；AMD EPYC 5th 96c 最高 1.7×、WHM 1.15×；Graviton4 96c 最高 2.5×、WHM 持平 [p17]（实验）
  - 128 核 GNR 上 SFC-CA 约 50–97 TFLOPS，高于 oneDNN、OpenBLAS [p16]（看图，读图近似）
  - AMX 1024 Flops/cycle vs FMA 64 Flops/cycle [p12]
  - Nacho 稀疏编译器 geo-mean 加速 2.4×（vs Taco）、1.8×（vs cuSPARSE）[p45]（实验，ASPLOS '27）
- 提到的公司/客户/产品/标准：LANL、NVIDIA、Intel（AMX、libxsmm）、Stanford、Ohio State、Elephance、Reffine、Nacho、Taco、cuSPARSE、Arrow、Substrait、TurboQuant、NSGA-II
- 首次/记录/SOTA 声明：SFC-CA GEMM 称 "SOTA results on multiple CPU platforms"、可证明达到通信下界 [p14][p16]
- 推荐配图页：p16（SFC-CA GEMM 在 GNR 上的 TFLOPS 对比）

### P332 Near-Data-Processing-opportunities-for-context-engineering
- 讲者/机构：Jon Hermes，Arm [p1] | 类型：技术分享
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [In 封装内：CXL/内存池化]
- 核心主张：
  - 推理应分为 Context → Prefill → Decode 三段；context 工作主要受内存限制，适合 NDP [p6][p11]
  - NDP 的主要障碍是"领结问题"：左侧大量待卸载函数、右侧多种 NDP 设备，中间缺少转换层 [p10]
- 关键数据：
  - RAG 在部分情况下占总时间近 30% [p7]（实验）；Llama3.1 405B，1.2TB 向量库 p99 总时延约 34,000ms，检索约 6,000–7,000ms [p7]（看图，读图近似）
  - Metagenomi 35 亿个 960 维向量，200M 分片在 i4i.8xlarge 上索引共 108 计算小时，S3 上约 12.9TB [p8]（引用 AWS 博客）
  - 单查询运行时间：nn=10,000 约 150s，nn=50,000 约 590s [p8]（看图，读图近似）
- 提到的公司/客户/产品/标准：Arm、Modular、AWS（LanceDB、S3）、Marvell、Samsung、SK hynix、CXL-ANNS、NDSEARCH、UDON、IKS
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（RAG 推理各阶段耗时拆分）；p10（NDP 领结问题示意）

### P333 Open-Object-Formats-for-Near-Data-Processing
- 讲者/机构：Daniel Bittman，CTO，Elephance Memory [p1]；尾页另列 Pankaj Mehra [p16]（看图） | 类型：技术分享
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [推理/算力/经济性]
- 核心主张：
  - 序列化与搬移开销拖垮性能；需要数据中心化编程模型：直接访问数据、低协调共享，即使是复杂数据结构 [p3][p6][p15]（看图）
  - 自包含内存对象（FOT + 不变指针）+ 稳定内存格式（Arrow 等），可在 GPU/NIC/x86/aarch64 间零拷贝共享 [p5][p7][p8]（看图）
- 关键数据（全部看图，手绘幻灯）：
  - 局部性控制使 Key Value Store 吞吐提升 3.8–5.3× [p10]
  - 模型加载 page fault ~10^5 → 10^2 [p4][p12]；~10,000 faults → 80 [p11]
  - 模型加载：baseline load 200ms vs MemObj 200µs [p11]；prompt completion 快 2–3× [p12]
  - stock llama.cpp 切换模型吞吐中断超过 1 秒，memory objects 版本几乎无中断 [p13]
  - gemma cold 2.49s vs 4.06s（1.6×）、gemma warm 0.86 vs 2.49s（2.9×）、llama warm 0.96 vs 2.22s（2.3×）；warm setup 28.6ms vs 1645ms [p22]
  - 16 实例总内存 1.37GB vs 4.91GB（stock）[p22]
  - HNSW 加载：文件 27±3ms、MemOS 0.2±0.1ms、VectorDB 7±4ms；HNSW w/ Arrow 归一化运行时 0.78；FAISS 3%–9% 开销 [p21]
  - 指针解析：对象内 0.4ns、跨对象未缓存 27.9ns、缓存 3.2ns [p26]
  - Twizzler YCSB A–F 归一化事务率约 1.2–1.8（LMDB 约 1.0）[p27]（读图近似）
- 提到的公司/客户/产品/标准：Elephance Memory、Twizzler、libmemobj、Arrow、Substrait、pNFS、FamFS、Reffine、CXL、UALink、TPP、llama.cpp、gemma、HNSW、FAISS、LMDB、PMDK
- 首次/记录/SOTA 声明：无
- 推荐配图页：p7（Memory Objects 软件栈）；p22（memos vs stock 加载时间与内存对比）

### P334 Towards-an-Extensible-Framework-for-Near-Data-Processing-in-AI-Integration-Experiences-with-oneAPI-OpenXLA-and-PyTorch
- 讲者/机构：Wonjae Lee、Vishnu Charan Thummala、Somnath Roy，Samsung Electronics [p1] | 类型：技术分享
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [推理/算力/经济性]
- 核心主张：
  - 试过三条路径：oneAPI Level Zero（受限于 Intel GPU 导向，缺 SPIR-V→Arm 编译）、OpenXLA PJRT 插件（打通端到端，但 GPU+NDC 的 MPMD 编排不成熟）、PyTorch 树外后端 [p2][p4][p9]
  - 自研 SPEL（Samsung PyTorch Extension Library）：完整 eager 模式、仅卸载设备声明的算子、延迟张量创建、分片提示 [p11][p13]
- 关键数据：
  - PoC 设备：16 Arm Neoverse V2 核、4 DDR5 通道、CXL 2.0 [p3]
  - Qwen3-0.6B 在 SPEL+NDC（CMMDC 设备）上运行：spel::mm 调用 1576 次，SPEL 总时间 3.205s，平均 2.034ms [p14]（看图，实验）
- 提到的公司/客户/产品/标准：Samsung（SPEL、CMMDC、cHBM、Cognos）、OCP NDC API（opencomputeproject/samsung-ndc）、oneAPI/Level Zero、oneDNN、SYCL、OpenXLA、StableHLO、PJRT、PyTorch/XLA、PrivateUse1、Triton、Qwen3
- 首次/记录/SOTA 声明：无；SPEL 代码计划于 OCP 结束时开源（github.com/SamsungDS/Cognos/SPEL）[p14]
- 推荐配图页：p12（SPEL 架构图）；p7（PJRT 与 NDC 映射）
