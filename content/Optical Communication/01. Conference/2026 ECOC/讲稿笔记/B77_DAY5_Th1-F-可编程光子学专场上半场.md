---
title: "B77 · DAY5 · Th1-F-可编程光子学专场上半场"
tags:
  - ECOC2026
  - DAY5
---

### 0924-推定F1-根特大学-可编程光子学的现状导论.pdf
- 讲者/机构：讲者姓名页面未见（幻灯片为根特大学/imec，F6 页脚称引用 Wim Bogaerts 的 ECOC26 workshop 讲稿，讲者是否即其本人未确认） | 题目：Programmable Photonics: Architectures, Control and Applications（副标题引自首页 OCR：Programmable Integrated Photonics (PIP) for a flexible, efficient, intelligent optical future，OCR 不完整） | 类型：Workshop（特邀专场导论）
- 方向归属（主/次）：主 4（OCS/可编程光交换，偏平台层面）；次 5（微波光子/5G-6G 波束成形）、次 6（QKD、光纤光栅传感）
- 核心主张：
  1. 可编程光子学是"一族技术"，从单功能可调 PIC 到通用"光子 FPGA"，需要芯片、封装、光电（含 RF）与软件/算法的系统级协同 [p35]。
  2. 用软件定义的波导网格（2×2 可调耦合器 + 移相器为标准单元，基于 PDK 的电路设计）取代逐次流片，可跳过慢速流片周期、现场编程功能 [p26][p33]。
  3. 目前从想法到产品（含 PIC、驱动电子、封装、软件）需 6–7 年，可编程化可缩短产品开发并提升复用 [p31][p33][p34]。
- 关键数据：
  - 从想法到产品 6–7 年；一次原型循环 1–2 年（芯片设计 6–9 个月、晶圆制造 6 个月、测试封装 6 个月）；PIC 原型需 3–4 轮循环 [p31]。
  - 扩展网格对 2×2 门的要求清单：小尺寸、短光程（FSR）、低光损耗、低电功耗、线性响应、CMOS 兼容驱动电压、快速（MHz–GHz）、无电/热串扰、可与其他硅光功能集成（仅列需求，无数值）[p17]。
  - 光电集成路线四类：wire-bonding（灵活、连接数有限）、interposer/co-packaged chiplets（标准 chiplet）、flip-chip/3D stacking（连接数多、很强）、monolithic（复杂工艺/设计）；标注"100s–1000s connections"[p21，OCR 核对，未看图]。
- 提到的公司/客户/产品/标准：Ghent University、imec；Nature Comms. 2025 可编程微波光子处理器（Hong Deng，doi:10.1038/s41467-025-60100-0）[p7]；Bogaerts et al., Nature 2020 综述 [p10]。
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；应用域图列举：机架顶交换机、可编程收发器、FTTH 用户、xDSL、5G-6G 微波波束成形、FMCW LiDAR 测距引擎、QKD/光哈希、光纤光栅传感、微波雷达、多传感器读出 [p30]。
- 推荐配图页：p6（从单功能 PIC 到通用可编程 PIC 的演进示意）；p31（想法到产品 6–7 年时间线）；p30（应用域全景）

### 0924-推定F2-Lightmatter-面向AI信息处理的光子学互连与内存带宽.pdf
- 讲者/机构：Lightmatter（讲者姓名页面未见） | 题目：标题页 OCR 乱码；按文件名为面向 AI 的光子互连与内存带宽，幻灯片主线为 Passage M1000 3D 光子"superchip"平台（英文原题看不清） | 类型：产业发布（含邀请报告性质）
- 方向归属（主/次）：主 4（3D 光互连/光互连中介层/CPO/OCS）；次 3（微环调制器/收发器微缩）
- 核心主张：
  1. "今天 AI 是互连受限"，仅靠互连就能加速训练与推理：训练时间 3x 缩短、预填充 TTFT 3x 缩短、解码 2x 更快（结论页） [p5]。
  2. 计算随面积增长而 I/O 随周长增长，芯片越大差距越大，I/O 必须随算力扩展 [p6，OCR 核对]。
  3. Passage M1000 以 3D 光子中介层 + 可重构光波导网络/OCS 提供 114 Tbps 带宽，并借光电路交换实现冗余与可编程 [p9][p16-p19]。
- 关键数据：
  - 训练万亿参数 MoE 相对时间（越低越好）：铜基线 14.4 Tbps scale-up、4×128-GPU pods = 1.00x；光子等带宽 14.4 Tbps、1×512-GPU pod = 0.60x；光子加带宽 32 Tbps scale-up、1×512-GPU pod = 0.37x [p2]。
  - 推理预填充 TTFT 相对铜加速：输入上下文 1K = 2x、8K = 2x、131K = 3x；Lightmatter prefill 仿真器，批大小 8192/1024/64 对应 1K/8K/131K [p3]。
  - 推理解码：相对铜 2x 更快，跨短到长上下文；ScaleScope 仿真，10T MoE 模型、340B 激活参数、1024 专家；光互连 16×128 XPU HyperX，4.0 TB/s 链路、0.5 µs 跳延迟，对比铜 128-XPU 机架 4.0 TB/s scale-up、1 µs 跳延迟、200 GB/s scale-out、4 µs scale-out 延迟；并发请求 8–1024 [p4]。
  - Passage M1000 规格：带宽（Tx+Rx）最高 114 Tbps；SerDes 数 1024；硅片复合体面积 4,000 mm²；供电密度 >1.4 W/mm²；光纤 256 根；冗余方式为光电路交换；34 个 chiplet、1024 SerDes [p9]。
  - 3D 堆叠标准工艺：凸点间距约 120 µm、凸点尺寸约 80 µm、单个收发器面积 0.015 mm² [p10]。
  - 微环加无电感驱动和模拟前端，Tx+Rx 面积 0.006 mm²；EO S21 3 dB 带宽：偏压 -1 V 时 31.8 GHz，-2 V 时 35.4 GHz；扫描波长约 1302–1316 nm、0–1.5 V 偏压（R. Baghdadi et al., OFC 2025, Tu3J.6）[p11]。
  - 瓦片设计：16 条水平总线，每条最多 2 个全双工 TX-RX 链路，每链路 8λ @ 56 Gbps/λ；4 条总线含 16 波导；瓦片共 64 波导 [p17]。
  - 同一光罩 2×4 步进拼接成一整张可编程网络（含跨光罩光子与金属拼接） [p16]。
  - 路线图页：200 Tbps XPU、400 Tbps Switch，"3D photonics scale-up and out to 1M nodes"，基于 Passage M 系列 3D 光子中介层 [p20]。
- 提到的公司/客户/产品/标准：Lightmatter Passage M1000、Passage M-Series；ScaleScope 仿真器；CoolIT（实物板卡上可见液冷冷板标识）[p13-p15]；IEEE Hot Interconnects 2025 Best Industry Paper（Accelerating Frontier MoE Training with 3D Integrated Optics，M. Bernadskiy et al., IEEE Micro doi:10.1109/MM.2026.3682935）与 2026 Best Paper（Scaling Inference Prefill with High-Radix Photonic Interconnects）[p2][p3]。
- 与业界对比或记录声明（SOTA/首次/record）：页面标题"Unprecedented performance and scale" [p9]；两项获奖（HOT Interconnects 2025 / 2026）[p2][p3]；以上性能均来自仿真，非实测（p3、p4 脚注为仿真器）。
- 推荐配图页：p9（M1000 规格表与 34 chiplet/256 光纤示意）；p2（训练时间 1.00x/0.60x/0.37x 柱图）；p17（瓦片设计：16 总线、8λ×56G）；p14（Chip-on-Wafer 装配实物）

### 0924-推定F3-哥伦比亚大学-面向AI集群的可编程光子学.pdf
- 讲者/机构：Keren Bergman / Columbia University（p1 署名） | 题目：Programmable photonics for AI clusters | 类型：邀请报告/Workshop
- 方向归属（主/次）：主 4（OCS/光互连内存池）；次 3（scale-out OCS 重构策略）、次 2（scale-across 不涉及）
- 核心主张：
  1. 模型尺寸相对单 GPU 内存差约 2 个数量级，不同工作负载（训练/推理、prefill/decode）算术强度不同，固定硬件不能自适应，需要光子的透明可重构性 [p3][p4][p6]。
  2. SiPAM：每个硅光 I/O 可灵活分配给高速内存访问或网络通信，每个工作负载一次性重构；以 OCS 替代电分组交换，BCube 拓扑，机架内资源解耦 [p5]。
  3. 高注入带宽（>1600 GBps）下无需快速交换，配合 one-shot 光重构即可获得加速，即"高带宽光互连 + 一次性重构"是务实路径 [p14]。
- 关键数据：
  - SiPAM 相对基线：最高 3.5x 加速；基线为 B100 GPU、固定 192 GB HBM、总内存带宽 8 TBps；SiPAM 按工作负载优化算力、内存带宽、容量和网络带宽；负载含 Megatron-126M/5B/22B/40B、Anthropic 52B、Chinchilla-64B、GPT3-175B；推理图中 126M 内存利用率 53%，1T 内存利用率 95%（图上标注） [p7]。
  - 基线迭代时间（归一化，SiPAM=1，读图估计）：训练约 3.5/2.2/1.7/1.8（126M/5B/175B/1T），推理约 3.5/2.6/1.9/3.4 [p7]。
  - ACTINA：GPT3-175B、4096 H100 GPU 集群，通信时间实时重构相对 one-shot 最高 2.3x 提升，重构延迟约 10^-4 s 以下才有收益（图中 real-time 通信时间约 0.2 s，one-shot 约 0.5 s，重构延迟 ≥ 约 10^-3 s 后升至约 0.85 s，读图估计） [p12]；结论页写"Up to 2.3x speedup over SoTA one-shot strategy at low reconfiguration latencies"，"Demonstrated 2.3x performance acceleration on 4096 GPUs" [p14]。
  - 网络层级：scale-up 同一 NVLink 域最多 256 GPU；GPU-HBM4 25.6 TBps，GPU-CPU (C2C) 900 GBps；能效标注 <50 fJ/bit 与 >20 pJ/bit（分属不同互连层，OCR 未能对应，看不清） [p2，仅 OCR]。
  - GPU 内存：2025 年 288 GB HBM3e、8 TB/s、1400 W；对比 H200 141 GB HBM3e 4.8 TB/s 700 W 等（OCR，未看图核对） [p3]。
- 提到的公司/客户/产品/标准：NVIDIA（NVLink、B100、H100、GB300、OCS Testbed）、Google Jupiter、Google TPUv4 Pod、Helios、RotorNet、SiP-ML/TeraPHY；文献：SiPAM（IEEE Micro 2026，HOTI 2025）、ACTINA（SC25） [p5][p8][p14]。
- 与业界对比或记录声明（SOTA/首次/record）：相对 SoTA one-shot 策略最高 2.3x [p14]；SiPAM 最高 3.5x [p7]；均为仿真/系统级建模结果。
- 推荐配图页：p7（SiPAM 训练/推理迭代时间柱图）；p8（六种 OCS 可重构系统对比）；p12（重构延迟 vs 通信时间曲线）

### 0924-推定F4-iPronics-面向光交换的可编程光子学.pdf
- 讲者/机构：iPronics（讲者姓名页面未见；幻灯片引用 Torrijos-Morán、Pérez-López 等） | 题目：页面无明确总题目；主题为面向 AI 数据中心的硅光可编程 OCS（Programmable photonics for optical switching） | 类型：产业发布/邀请报告
- 方向归属（主/次）：主 4（OCS）；次 3（scale-out 网络、1.6T 收发器链路兼容性）
- 核心主张：
  1. AI 数据中心扩展是网络挑战；光交换用于 scale-up 扩展，相对现有方案 20x 更紧凑、3x–5x 更具成本效益、亚毫秒级重构 [p4]。
  2. "光子学的摩尔定律已到来"：硅光集成度已由 MSI 进入 LSI 量级，生态（代工、封装、控制电子）已成熟，可做半导体式光交换系统 [p9]。
  3. 提供增益控制的固态硅光 OCS（ONE-32），已投产，并给出业界首个 1.6 Tbps 收发器经该 OCS 的链路质量结果 [p18][p21]。
- 关键数据：
  - 系统对比：20x more compact（每 1U 4 个交换机）；3x–5x more cost effective；sub-ms 重构速度 [p4]。
  - 现有 3D 光学 OCS 方案多为每 1U 32–40 端口，形成 2U/4U/8U 机架单元 [p5，OCR]。
  - 硅光集成度趋势图：晶体管/执行器数 10^2–10^4 量级（光子）对比电子至约 10^10，横轴 1970–2030 [p9]。
  - 交换架构权衡：Benes family、Banyan family、PILOSS 分别在严格无阻塞、低集成密度、光损耗与串扰可扩展性之间取舍（J. Lightwave Technol. 44, 2026）[p14]。
  - 64×64 偏振无关硅光 OCS 示例（路径 In1/In52 → Out1/Out28）[p16]。
  - ONE-32 光子芯片：严格无阻塞 32 端口、偏振透明、>4,000 个集成开关单元、兼容 WDM 光学、片上遥测；增益控制硅光 OCS [p18]。
  - 链路测试：Lumentum 1.6 Tbps 2×DR4（200G/lane）带 retimer 硅光收发器，基线 BER 1e-12；网络损耗仿真器 VOA1 0–3 dB、VOA2 0–10 dB；结论：预 FEC BER 相对 10^-12 基线只劣化 1 个数量级，对前后网络损耗稳健 [p21]。
  - OFC 演示界面（4 端口）：Power Tx/Rx 与 BER — Port0 -0.251/-0.4 <1e-12；Port1 -1.431/-1.17 1.136e-05；Port2 0.083/1.15 <1e-12；Port3 -0.226/-0.39 <1e-12（单位 dBm 未标，看不清）[p13]。
  - 系统页：ONE 系列，多平台多格式、2x 链路成本降低、内嵌链路增益与遥测、µs 级 [p23]。
  - 技术栈页：纯硅光标准工艺、无移动部件、专有 PDK 与交换网络、板载增益控制补偿损耗（OCR）[p20]。
- 提到的公司/客户/产品/标准：iPronics ONE-32 / ONE Series；Lumentum（1.6T 2×DR4 收发器）；OCS 供应商图列出 Coherent、Triple-Stone（320×320，中国）、POLATIS（H&S）、Eoptolink、Molex 等 [p5，OCR]；兼容 pluggable、NPO、光学中介层、CPO [p23]。
- 与业界对比或记录声明（SOTA/首次/record）：明确写"Industry-first results of link-quality of 1.6 Tbps transceivers ... over gain-controlled silicon-photonics OCS" [p21]。
- 推荐配图页：p21（1.6T 收发器经 ONE32 OCS 链路测试框图与结论）；p4（三项对比指标）；p18（ONE-32 芯片）；p9（光子学摩尔定律图）

### 0924-推定F6-丹麦科技大学-物理信息机器学习建模并补偿热串扰.pdf
- 讲者/机构：DTU（丹麦技术大学），合作方含 iPronics、Politecnico di Torino；成果署名 I. Teofilovic 等，讲者姓名页面未明确 | 题目：Physics-informed machine learning for modelling and compensating thermal crosstalk（标题页 OCR 乱码，按文件名与内容推断，英文原题未确认） | 类型：学术论文/邀请报告
- 方向归属（主/次）：主 4（可编程光子网格/MZI、MRR 热控）；次 1（无直接关系，仅高性能器件建模）
- 核心主张：
  1. 光子 FPGA 与电子 FPGA 不同：元件为模拟 MZI/MRR，被热串扰耦合，设置依赖器件，需在线"设置→测量→再调"，无标准语言，"我们需要模型 / 光子编译器是什么" [p3]。
  2. 纯数据驱动模型精度高但需大量数据且易过拟合，纯物理模型泛化好但欠拟合；物理信息数据驱动结合二者，并可基于单单元模型同时补偿多单元 [p19，OCR]。
  3. 热串扰在网格内线性叠加，基于 MRR5 的 PILR 模型可完全补偿 [p18]。
- 关键数据：
  - MZI 网格性能对比（预测误差 RMSE）：忽略串扰的拟合模型 3.26 dB；含串扰的拟合模型 1.44 dB；学习得到的黑盒模型 0.53 dB（数值据 OCR，图形未逐一核对，3×3 MZI 网格，ASE 光源、DAC 驱动）[p7][p8]。
  - MRR 谐振波长偏移建模测试 RMSE：线性拟合 0.52 pm；热衰减模型 ThDM 0.41 pm；线性回归/NN 0.34 pm（I. Teofilovic, JLT 2024）[p13]。
  - 泛化：MRR 4/MRR 5 上 RMSE(pm)：ThDM 0.90/0.72；LR 0.90/0.93；PILR (k=0.5) 0.63/0.61；k 取 0.5–0.6 附近最优，k=0 时约 0.93/0.89、k=1 时约 0.72/0.90 [p17]。
  - 损失函数：L_total = (1−k)·L_data + k·L_physics，灰盒建模 [p15]。
  - 热扩散分析：FTDT、3D 热分析（Politecnico di Torino），实验与仿真对比结论"制造误差、电串扰与光串扰未建模"；电压范围 0V–2V [p9]。
  - 补偿实验波长扫描约 1549.8–1550.2 nm，光功率约 -35 至 -65 dBm，补偿后谐振与单个器件对齐（图定性）[p18]。
  - MZI 简单模型：W_ij 含损耗 L_ij 与消光比 ER 项，V1 扫描时模型与实验吻合，V2 扫描时出现 -8 dB 偏离（图，未标数值单位以外条件）[p5]。
  - 紧密封装下热串扰使谐振波长偏移相对电功率的斜率上升：偏移约 50 pm @ 约 270 mW（d1，最紧）对比约 30 pm（d2/d3）；D. Pérez, Nat. Commun. 2017 [p4]。
- 提到的公司/客户/产品/标准：iPronics；Politecnico di Torino；项目：Villum Young Investigator OPTIC-AI、Horizon Europe PROMETHEUS (101070195)、MINDnet、QuNEST [p19]；文献：Cem et al. OFC 2022/JLT 2023；Cavicchioli APL Photonics 2026；Teofilovic JLT 2024、SPIE Europe 2024、arXiv 2607.07274（under review）。
- 与业界对比或记录声明（SOTA/首次/record）：无 record 声明；结论为"物理信息模型兼具精度与泛化"。
- 推荐配图页：p3（电子 FPGA 与光子 FPGA 对比框图）；p17（PILR 与 ThDM/LR 泛化对比表和 k 扫描）；p18（单模型补偿全网格谐振谱）

## 本批小结
1. 可编程光子学的两条落地线：数据中心 OCS（F3 Columbia、F4 iPronics、F2 Lightmatter 的片上 OCS 冗余）与通用网格/光子 FPGA（F1 Ghent、F6 DTU）。前者已有产品化指标，后者仍卡在建模与控制。
2. AI 互连被明确视为瓶颈：F2 给出仿真的 3x TTFT、3x 训练时间、2x 解码收益（互连受限论），F3 给出 SiPAM 最高 3.5x、ACTINA 最高 2.3x，均为系统仿真而非实测，需与实测区别对待。
3. OCS 重构速度存在"够用即可"的观点：F3 指出注入带宽 >1600 GBps 时 one-shot 重构即可、无需快速交换；F4 主打亚毫秒重构和 µs 级系统页，两者对切换速度需求的判断不同，值得跟踪。
4. OCS 与 1.6T 生态兼容性开始被验证：F4 给出业界首个 1.6 Tbps（Lumentum 2×DR4，200G/lane）经硅光 OCS 的链路结果，预 FEC BER 仅劣化 1 个数量级；F2 的 M1000 用光电路交换做光纤冗余，说明 OCS 已从数据中心交换扩展到封装内。
5. 光电集成与控制是产业化难点：F1 指出想法到产品 6–7 年、需 3–4 轮原型；F6 显示热串扰使简单模型误差从 0.53 dB（数据驱动）到 3.26 dB（忽略串扰）差异显著，物理信息 ML 是折中方案（F1、F6）。
6. 3D 光子中介层微缩趋势：F2 给出 Tx+Rx 面积 0.006 mm²（微环 + 无电感驱动）、M1000 114 Tbps/1024 SerDes，配合 F4 提到与 NPO、光学中介层、CPO 的兼容性，反映 Scale-up 光互连向片上、无可插拔方向推进。
