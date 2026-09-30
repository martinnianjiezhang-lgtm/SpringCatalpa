---
title: "B15 · DAY1 · E1-Su3-Su4-AI与端到端光网络"
tags:
  - ECOC2026
  - DAY1
---

### 0920-pm-Su4-C-04-Ciena-AI真正想要的光网络.pdf（第2–6页；p1为题目页，未看）
- 讲者/机构：Ciena（讲者姓名未见） | 题目：题目页未看；p2 为 "01 Scale-Across Architecture Demands ILA Site Evolution"（看图核实）；wrap-up 页标题为 "The optical network AI actually wants" | 类型：Workshop（ECOC2026 Workshop: Will the AI workload require an end-to-end-optimized network infrastructure?）
- 方向归属（主/次）：主 2 Scale-across/FST/多rail；次 1 AI光网络
- 核心主张：
  1. Scale-Across 架构要求 ILA 站点演进（Scale the Hut + Scale the Site）。
  2. Photonics@Scale：全谱转发器（FST）+ 多 rail（Hyper Rail）线路光子学，降低设备数量、空间、功耗。
  3. 用 AI 自动化运维：可预测性比可靠性更受重视；把遥测变成前瞻洞察。
- 关键数据：
  - ILA 机房 Existing / Next Gen Large / Next Gen X-Large：机架 4-10（2 post）/ 9（4 post）/ 18（4 post）；EDFA/Raman rails 40/40 / 864/432 / 1,728/864；制冷 7-10T / 35T / 55T；站点功率 30-50kW / 200kW / 400kW；尺寸 12'x24' / 12'x52'（Large/X-Large）[p2]
  - 站点供电：现有为集成在机房内、每个机房单独接入、最高约 500kW/600A；Next Gen 集中管理、置于机房外、最高 4MW/5,000A（假设 3P、480V）；最多 12 个 X-Large 机房（12x1,728 EDFA rails）[p2]
  - "Next Gen 架构可扩展超过 12 个机房，每站点最多 20,736 个 EDFA rails" [p2]
  - 全谱转发器演进：2008 WL2 100G；2012 WL3 200G；2017 WLAi 400G；2020 WL5 800G；2024 WL6 1600G（频谱形状图）[p3]
  - FST 面向 16 对光纤：被管设备 192 → 32（减少 84%）；机架单元约减 75%；功耗约减 50%；补丁线减少，自动校准 [p3]
  - FST 调制解调器由 200Gbd → 300GBd → 400Gbd 级（原文如此）以优化传输距离 [p3]
  - Hyper Rail：PMO 4 rails/机架 → FMO 128 rails/机架（受机架功率限制）；EDFA 密度 32x，EDFA Raman 密度 16x，功率 4x；每卡 4 个 C&L rails；管理与通信流量增加 32x [p4]
  - 每个节点即传感器：FST 终端、RLS Hyper-Rail 终端、ILA（Hyper-Rail Amp 4 rail）实时流式遥测 → 自动化 / 数字孪生 / 网络感知 [p5]
- 提到的公司/客户/产品/标准：Ciena（FST、RLS Hyper-Rail、WaveLogic WL2–WL6）
- 与业界对比或记录声明（SOTA/首次/record）：无明确 record 声明；给出自家规模数字（20,736 EDFA rails/站点）[p2]
- 推荐配图页：p2（ILA 机房与站点规模对比表）；p3（FST 演进与 84%/75%/50% 收益）；p4（Hyper Rail 4 → 128 rails/机架）

### 0920-pm-Su4-C-00-Ciena-另一版扫描.pdf（第1–4页）
- 讲者/机构：Ciena | 题目：与上一篇（C-04）为同一讲的另一版扫描，页面内容对应 p2 ILA 之后的部分 | 类型：Workshop（重复扫描，仅作OCR补充）
- 方向归属（主/次）：同上（主 2；次 1）
- 核心主张：同 C-04；OCR 另补充 "Move from 200Gbd > 300GBd > 400Gbd class modems for reach optimization"、"Integrate modem client & line, signal conditioning and with on-shelf integrated SW for workflow execution"，wrap-up 三点同 C-04（Collaborative network engineering；Photonics@Scale for the AI era；Automate operations with AI）。
- 关键数据：与 C-04 一致，p2 看图核实为 "03 Hyper Rail Photonics"：PMO 4 rails/rack → FMO 128 rails/rack（受机架功率限制）；EDFA 密度 32x、EDFA Raman 16x、功率 4x；每卡 4 路 C&L rail；嵌入式自动化与仪表，管理与通信流量 32x（另 OCR：192→32 managed devices，84% reduction）。
- 提到的公司/客户/产品/标准：Ciena
- 与业界对比或记录声明：无
- 推荐配图页：不必，使用 C-04 p3–p4

### 0920-pm-Su4-C-01-NTT-光网络数字孪生.pdf
- 讲者/机构：Hideki Nishizawa, Kazuya Anazawa / NTT Inc. | 题目：Towards AI-Native Infrastructure with Optical Network Digital Twins | 类型：Workshop
- 方向归属（主/次）：主 1 AI光网络；次 3 OCS（Scale-out）
- 核心主张：
  1. 光技术对扩展 AI 基础设施日益关键；数据中心网络（DCN）与 DCI 均向开放、可编程、云原生演进。
  2. 下一挑战：把 AI 工作负载与跨 DCN/DCI 的光资源无缝连接（workload-to-network 闭环）。
  3. 挑战项：通用意图/资源抽象；跨域可视与协调；不同控制时间尺度与运营边界。
- 关键数据（p2 已看图核实；p3 仍以 OCR 为主，无可核对的性能数字）：
  - OCS：速率无关、按光纤交换、无 OEO、粗粒度；相对 EPS 功耗很低、可扩展性高，适合一对一通信；EPS 速率相关需 OEO，适合 any-to-any [p2]
  - OCP OCS 子项目定义 OCS 型 AI 集群的 C-plane（SBI/NBI），已开始通用 YANG 模型；NTT 已开发面向 OCS DCN 的 SDN-C（引 Anazawa et al., JOCN, doi 10.1364/JOCN.558407）（看图核实）[p2]
  - Data Center Xchange：多厂商/多代设备、多对多、按链路长度与 QoT 选传输模式；以云原生原则运营 DCI；对比垂直集成转发器 vs. 白盒交换机（软件抽象 SAI/SDK、Kubernetes） [p3]
  - 引用 Nishizawa et al., "Leveraging digital twin technologies: AI-photonics networks-as-a-service for data center xchange in the era of AI [invited tutorial]", JOCN vol.18, pp. C49–C65, July 2026 [p3]
- 提到的公司/客户/产品/标准：IOWN GF、OCP（OCS Subproject）、YANG、SDN-C、SAI、Kubernetes、CFP2
- 与业界对比或记录声明（SOTA/首次/record）：无 [p4]
- 推荐配图页：p3（垂直集成转发器 vs 白盒交换机、DC Xchange 云原生架构）；p4（workload-to-network 闭环与总结）

### 0920-pm-Su4-C-02-Nokia-用领域知识建高效网络.pdf
- 讲者/机构：Annalisa Morea（Consulting Engineer）/ Nokia（p1 看图核实） | 题目：How to build efficient optical networks for AI using domain intelligence | 类型：Workshop
- 方向归属（主/次）：主 1 AI光网络；次 2 Scale-across/ZR
- 核心主张：
  1. AI 模型生命周期：大型超算商训练（大 DC 间需高容量、良好同步）到小型/企业/元城域 DC 推理（低时延、功耗、占地）——两类场景对网络要求不同 [p2]
  2. 光网络主要挑战：更异构的流量请求、更网格化的 DC 连接 [p4]
  3. 硬件创新（可插拔相干光学、全频段转发器、光纤选择性交换机）加上跨层"agentic 域控制器"自动化 [p5–p6]
- 关键数据（OCR，未看图，无可核对数字）：
  - 展台 #1100 展示："DCI and scale across" demo、自动化 demo、1.6T 相干可插拔 demo、AR demo、Tomography demo [p5]
  - Agentic 域控制器覆盖：家庭/固定接入(Corteca)、IP 传输(Altiplano/NSP 类)、光传输(WaveSuite)、数据中心(Event-driven automation)；能力含智能排障、异常/漂移检测、功耗节约、自愈、告警处理 RCA [p6]
- 提到的公司/客户/产品/标准：Nokia（Corteca、Altiplano、WaveSuite、Transcend 类平台，OCR不完整）
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p6（跨层 agentic 域控制器架构）

### 0920-pm-Su4-C-03-华为-算网一体设计.pdf
- 讲者/机构：Hongchen Yu 等 / Huawei Optical Product Line Research Dept. | 题目：Integrated Computing-Network Design for AIDC | 类型：Workshop
- 方向归属（主/次）：主 2 Scale-across/FST/多rail；次 3 OCS（Scale-out）、次 1 AI光网络
- 核心主张：
  1. 跨区域 RDMA 互联使 RTT 变长、流控与丢包检测变慢，限制 MFU；需算网一体设计 [p2]
  2. 低时延+高吞吐：OCS 扩展 super-pod radix、空芯光纤（HCF）降时延、FST+多 rail 提升 DCI scale-across 吞吐 [p3–p5]
  3. OTN-Proxy（支持 RDMA proxy 的 OTN 转发器）实现与距离无关的 scale-across 链路；数据/算力分离保障数据安全 [p6–p7]
- 关键数据：
  - OCS+SW 稀疏 super-pod：动态时延 500ns+；网络时延降 30%、推理性能提升 10%；super-pod 扩展至 16K [p4]
  - 趋势：参数量 1.6T → 2.8T → 5–10T；EP experts 384 → 896 → 1024；TPOT 50ms → 20ms → 5ms；OCS 支持超节点扩展至 16K、网络时延降 30%、推理性能升 10%（看图核实）[p4]
  - AF 分离推理：AF 算力池按小时/天依据平均序列长度调整，OCS 动态优化带宽；SU 平面跑 EP/FSDP 高流量、SO 平面跑跨 super-pod 多副本 DP 低流量 [p4]
  - HCF：插入损耗已低于实芯 SMF；已在 DCI 和金融专线商用部署；四项特性低时延/低损耗/低非线性/低色散；挑战：气体吸收峰（S/C/L）、模间干扰 IMI、弱瑞利散射（约 -30 dB）致 OTDR 难、拉丝长度有限 [p5]
  - Full Spectrum Transponder：单系统 25.6T/光纤（C96），C96+L96 时 51.2T，不牺牲可靠性；4-Rail OA @1U，集成度提高 75%，达到单 rail 级可靠性 [p5]
  - 传统 DCI vs Scale-Across：流量 ~200Tb/s → >10Pb/s；扩容粒度 per wavelength → per fiber；rails ~10 → >100；设备 现网 → 新高集成设备 [p5]
  - OTN-Proxy：支持 >100 Tb/s，作为 XPU proxy（RDMA proxy + CCL engine，SAI/SONiC，vLLM 中间件）；动机场景 240 km、RTT 约 2.5 ms 的 RDMA Write；结果图显示带 OTN Proxy 时吞吐与 DCI 距离（0–500 km）基本无关（曲线数值小字不清，看图核实） [p6]
  - 实网分布式训练/推理测试：首末层在本地卡，中间层放云端；部分场景算力效率损失 <5% [p7]
- 提到的公司/客户/产品/标准：Huawei（Al-OTN、ION-2030、AI-FAN、OTN-Proxy）、Microsoft（Fairwater 式 AI superfactory，引用）、vLLM、SAI/SONiC、NCCL/HCCL、CUDA/CANN、OpenAI GPT-6（引用背景）
- 与业界对比或记录声明（SOTA/首次/record）：未明确用 record 字样；"HCF 插损已低于实芯 SMF" [p5]
- 推荐配图页：p5（HCF 四项挑战 + FST/多rail 25.6T/51.2T 及 DCI vs Scale-Across 对照表）；p4（OCS super-pod 架构）

### 0920-pm-Su4-C-05-CTTC-电信AI云的边缘互联.pdf
- 讲者/机构：Ricard Vilalta / CTTC（ETSI SDG TeraFlowSDN chair，ETSI TC NET convenor） | 题目：The Interconnected Edge: Networking Strategies for Telco AI Cloud | 类型：Workshop
- 方向归属（主/次）：主 1 AI光网络；次 5 固定与无线接入（边缘）
- 核心主张：
  1. AI 迁向边缘快于网络跟进：需将连接、计算、存储视为一个整体（3C 网络：Connected–Collaborative–Computing）[p2–p3]
  2. TeraFlowSDN（ETSI 开源云原生自动化框架）用图上下文模型联合优化网络与算力，切片跨网络+计算 [p4, p6]
  3. 意图驱动 + 三层闭环（快/中/慢），并为边缘 AI 增加多租户隔离、密码认证、远程节点证明、不可篡改审计四项安全控制 [p7–p8]
- 关键数据（无实测数据，均为架构/分类）：
  - 三类负载：Cloud/Edge 服务 10–50 ms 时延；AI 负载 sub-10 ms 推理；网络负载 <5 ms、高频遥测 [p5]
  - 闭环：Fast sub-second（重路由/本地故障恢复）、Medium 近实时（切片调整）、Slow 长期（需求预测/策略调优）[p8]
  - 两类 AI 流量：协同边缘推理（层间激活，需确定性超低时延）；去中心化联邦学习（仅传模型权重，需突发链路）[p7]
  - EURO-3C：欧洲联邦 telco-cloud-edge 平台，用例覆盖汽车、交通、能源、PPDR [p9]
  - ETSI TC NET 标准化 network-cloud-edge-AI 连续体，kick-off 2026年10月7–9日，ETSI Sophia Antipolis [p10]
- 提到的公司/客户/产品/标准：ETSI TeraFlowSDN、ETSI TC NET、EURO-3C、5G NR/Wi-Fi 7
- 与业界对比或记录声明（SOTA/首次/record）：无 [p9]
- 推荐配图页：p6（图上下文模型与联合网络-算力切片，TeraFlowSDN）；p8（意图与三层反馈闭环）

## 本批小结
1. Scale-across 的核心是"每光纤容量与 rail 密度"：Ciena（C-04）与 Huawei（C-03）都用 FST + 多 rail 描述：Huawei 单系统 25.6T/纤（C96）、51.2T（C96+L96），4-Rail OA@1U；Ciena 128 rails/机架、每站点最多 20,736 EDFA rails，各自主张 DCI 由 ~10 rails 走向 >100 rails。
2. 网络设备的"自动化/数字孪生/遥测"被视为 scale-across 规模化的必要条件：Ciena "每个节点即传感器"（32x 管理流量）、NTT 光网络数字孪生+云原生 DCI、Nokia agentic 域控制器（C-02）——运维范式从人工配置转向 AI/意图驱动。
3. 跨域"工作负载—网络"闭环成为共同愿景：NTT（DCN+DCI 联合编排）、Huawei（OTN-Proxy、算网一体，部分场景算力损失<5%）、CTTC（网络+算力联合切片、意图闭环）。
4. OCS 同时在集群内（Huawei 500ns+ 动态时延，super-pod 16K，网络时延-30%）和 DCN 层（NTT/OCP YANG 多厂商 OCS 管理）被推进，标准化（OCP、IOWN GF）与控制面是当前重点。
5. Huawei 把 HCF 作为低时延光层手段，称插损已低于实芯光纤并已在 DCI/金融专线商用（C-03）；关键遗留问题为气体吸收峰、IMI、OTDR 运维和拉丝长度。
6. 边缘/电信侧（CTTC C-05、Nokia C-02）强调 sub-10 ms 推理与算力可调度网络资源，标准化推进（ETSI TC NET 2026年10月启动）；本批多数为架构/愿景类，定量数据主要来自 Ciena 与 Huawei。
