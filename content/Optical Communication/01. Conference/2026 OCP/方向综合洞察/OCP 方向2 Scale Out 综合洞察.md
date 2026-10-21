---
title: "OCP 方向2 Scale Out 综合洞察"
tags:
  - OCP2026
  - 综合洞察
---

# 方向2：Scale-out（AI 后端网络：UEC/MRC/RoCE、拥塞控制与负载均衡、多平面拓扑、102.4T 交换芯片与系统、NIC、可插拔光模块 LPO/LRO/FRO、OCS、SONiC/遥测与链路可靠性）

> 素材：by_direction/Out.md（主归属 44 节、次归属 82 节），另补 notes/R15（短距光互连 workshop：P335、P336、P341、P343、P345、P346，因标签格式未切入 Out.md），个别数字回查 text/Pxxx。索引〔Pxxx pN〕为 PDF id + 页码，转写稿为〔T0x mm:ss〕。口径：自报、仿真、实验、现网、预测、引用（注被引来源）、看图、存疑。
> 重复讲稿合并引用：P122=P153，P279=P321，P433=P445，P273≈P441≈P341（TeraHop 三份部分重叠），下文只按一份计数。

## 0. 一句话结论 + 5 条核心判断

**一句话结论：** OCP 2026 的 scale-out 讨论，重心从"链路更快"移到"拓扑更平、传输进 NIC"。102.4T 交换芯片靠 200G 端口拆分把 radix 换成规模，两层多平面 Clos 已能覆盖 10^5 GPU 量级；MRC、MetaRoCE、UET、Falcon 这四套多路径 RDMA 把负载均衡、乱序和故障绕行交给 NIC，并已有 75K GPU 现网故障实录。光侧，LPO 拿到了 Meta 与 Oracle 的现网可靠性数据，1.6T 代则分流到 LRO 和 XPO。OCS 还处在接口与运维标准化阶段。链路可靠性的瓶颈已从器件转到运维与可观测性。

**判断1：102.4T 的收益主要以 radix 兑现，"降端口速率 + 多平面 + 两层 Clos"成为多家共同的默认拓扑，三层网络开始被视为可以省掉的一层。**
- 机制：两层 1:1 Clos 最多 k²/2 个客户端口，规模随 radix 平方增长。102.4T 器件在 800G 时 radix 128，最多 8,192 客户端；拆到 200G 时 radix 512，最多 131,072〔P140 p5〕。Broadcom 给出同一组数字：TH6 两层 800G 为 8K 端点，400G 为 32K，200G 为 128K；4 平面（每 XPU 4×200G）可到 128K XPU〔P134 p10, p13〕。
- 超大规模用户各自落地：Google Virgo 两层、独立多平面，平面数 N 约等于每加速器的 SerDes 级"skinny link"数，单平面故障剩 (N-1)/N 带宽〔P130 p7〕；Meta 下一代 Flattened Planar Fabric 去 ToR、两层、负载均衡放 NIC〔P244 p9〕；Microsoft GB200 集群把 ConnectX-8 的 800G 拆成 4×200G 独立平面，两层 T0/T1，跑 50K 与 75K GPU 作业（现网）〔P418 p10〕；Microsoft Fairwater 多平面设计最多 524,288 GPU（引用）〔P422 p9〕。
- 厂商口径更激进：NVIDIA 称 Spectrum-X Photonics 多平面两层扁平网络可到 512K GPU、交换机少 40%（看图，自报）〔P367 p14〕。
- 代价落在布线：AMD/Arista 8 平面方案需要在 GPU 与 T1 之间加 8×8 shuffler〔P140 p14, p15〕；每 GPU 机柜后端光纤数 Hopper 约 576 芯、GB200 约 2,308 芯、Rubin 约 4,616 芯（自报/预测）〔P316 p3〕；Meta GTSW 机柜内光纤 8,192 根，需在集成商处预布线〔P407 p12〕。

**判断2：负载均衡、拥塞控制和丢包恢复正从交换机移到 NIC。四套多路径 RDMA 并存，核心技术趋同，分歧集中在 API、拥塞信号和是否依赖交换机新功能；跨厂商互通是下一道门槛。**
- 技术共性：UET 与 MRC 都用包喷洒、乱序交付、流量引导，丢包检测都用 SACK/NACK/超时/trimming〔P132 p3〕；MRC 只做发送端拥塞控制，UET 同时有发送端 NSCC 与接收端 credit RCCC，并带 LLR、CBFC、CSIG〔P122 p10, p13, p15〕。MetaRoCE 只依赖商用交换机的 ECN + ECMP，明确不需要 trimming、自适应路由或 INT，采用"排序完成而非排序投递"〔P296 p4, p5〕。Google Falcon 已在 NVIDIA ConnectX/BlueField 上与 Google NIC 线格式互通〔P130 p9〕。
- 现网证据：OpenAI 75K GPU 训练作业中一台 T1 交换机停止转发，约 25% QP 受影响、约 580K 包被丢；吞吐从约 12.2–12.5 Pb/s 跌到约 10.5 Pb/s，约 1 分钟内恢复，交换机重启上线期间无明显下降（现网，看图）〔P133 p12, p13〕〔P422 p13〕。转写补充：检测与恢复约一个 RTT 量级，告警晚于恢复〔T04 13:05–14:18〕。Microsoft 生产集群 T0–T1 链路抖动每时段多为 2–8 次、峰值约 13 次，MRC 透明重路由（现网，看图）〔P418 p10〕。
- 机制：RC 的问题是一个 QP 只哈希到一条 ECMP 路径、单丢包触发 go-back-N、恢复依赖路由收敛；MRC 用 SRv6 源路由或熵值（EV）把故障变成"选路事件"〔P133 p6, p7〕。每 QP 跟踪 128 条路径，ECN 标记的路径在当前排列中跳过，约每 RTT 对一个坏 EV 发探测〔P141 p7, p9〕。
- 互通缺口：Microsoft 指出早期部署只用单一 NIC 厂商，现有 MRC 规格在保留位、可靠性算法、RTT 测量上有空白，提出线格式/算法/行为三级互通并筹备 plugfest〔P418 p12–p16〕。MetaRoCE 用两个不共享代码的软件实现互相对打作为"最终裁判"〔P419 p5, p6〕。

**判断3：LPO 在 100G/lane（Meta）与 800G 模块（Oracle）上有了现网可靠性数据，收益来自"少一类故障"而非模块更可靠；到 1.6T，各家倾向 LRO，LPO 只在电通道余量被验证的地方扩大。**
- Meta：同链路模式、4k 模块、4 个月生产，linear 比 retimed 中断少 2.0×、影响业务的故障少 2.6×，最近 60 天中断少 8.4×（现网，看图）；实验室 0 次模块归因故障/2.96M link-hours，固定风扇下每模块功耗 −46%、温度低 17.5 °C〔P411 p5, p8, p9〕。讲者明确：模块级两者相当，收益是架构性的〔P411 p8〕。
- Oracle：800G T0–T1 链路 24 小时最大 pre-FEC BER，LPO 156,591 条中位 1.137e-11、p99 5.165e-10，FRO 202,042 条中位 1.432e-11、p99 2.888e-8；一个月内至少一次 down transition 的比例 3.244% 对 5.681%；64×800G 交换机半 LPO 比全 FRO 中位功耗低 258 W，其中 66 W 来自风扇（现网）〔P438 p6, p7, p8〕。
- 1.6T 分歧：Oracle 认为 LPO 难以同时满足 SI 与互通，LRO（26 dB 通道、16 W、约 10 pJ/bit，已演示多厂商 3 nm DSP 互通）是当前最佳低功耗方案〔P438 p9〕；Microsoft/Arista 在 XPO 平台上实测 FRO 余量最大、LRO 对光衰减更敏感、LPO 受 Tx 限制，15 dB 损耗下 LPO-LPO 3 dB 光衰时 BER 约 2e-7（实验，看图）〔P446 p18〕；Micas 预测 LPO 2027 年仅在 SI 余量验证处扩大〔P264 p9–p10〕。
- 功耗阶梯各家口径接近：Nokia 给 retimed 可插拔约 15、LRO 约 10、LPO/NPO/CPO 约 6 pJ/bit（自报）〔P335 p2〕；OCP SROI 工作流给 LPO 5–6、RTLR 8–10 pJ/b〔P346 p6〕。LRO 处在"省一半 DSP"的位置，这是它在 1.6T 被多家接受的原因。
- 代价：Oracle 的 OCI 运维团队发现 LPO 链路并不更不稳定，但故障归因变难，"可靠性提升、可解释性倒退"〔P443 p6〕。

**判断4：OCS 在 scale-out 里的实际位置仍是"慢变化的物理层交叉连接"，OCP 的工作集中在接口、运维流程和一致性测试，而非开关速度。**
- 标准化：Google 主导的 OCS Interface Spec v0.8 已提交 OCS 工作组，基于 OpenConfig YANG + gNMI，新增 cold-boot-recovery {MAINTAIN, REMAKE, REMOVE} 等对象〔P427 p10, p14〕；OCP-OCS YANG Model R1.0 已发布，iPronics/KDDI/NTT 计划在 OFC2027 用 8 家厂商 OCS 演示备件池故障恢复（自报，计划）〔P421 p12, p13〕；OCS 白皮书 2026 年 4 月发布，快速切换白皮书待发〔P136 p10〕。
- 光学可行性：Oracle/Lumentum 1,000 台近期产品 1310 nm 插损中位约 1.2–1.4 dB、98 分位约 1.6–1.85 dB，对照 IEEE FR/FR4/FR8 的 4 dB 预算（看图）〔P430 p12〕。
- 用途边界：Google 把 OCS 放在多楼园区 spine 替代电交换，配 1.6T Coherent-Lite（设计概念，非承诺）〔P147 p5–p11〕〔T06 01:06–08:02〕；iPronics/KDDI/NTT 的用例是 1:N 全局备件池和按 All-Reduce/All-to-All 重构光连接〔P421 p8, p9〕。主流 3D MEMS 是毫秒级重配置，只适合慢变负载〔P136 p5〕。
- 时间触发的研究结论：按轮次切换的电路交换，PTP 精度已比预测误差低 5–6 个数量级，难点是把 PHC 时间基暴露给集合通信库；64K GPU 预测误差 434 ms，而 3D-MEMS dark time 20 ms（实验+引用）〔P111 p9〕。

**判断5：链路可靠性的主要矛盾已从"器件 FIT"转到"中断率 + 污染 + 可观测性"，OCP 正在把遥测与诊断做成跨 LPO/CPO/retimed 的统一契约。**
- 量级：Meta 两个平台的作业中断中，scale-out 网络（交换机、NIC、光模块）占 23.6% / 11.7%，scale-up fabric 占 24.2% / 9.2%（现网）〔P125 p8〕；引用 arxiv 2410.21680，131,072 GPU 集群 MTBF 约 15 分钟〔P421 p3, p16〕。
- 指标转向：Meta 主张 AI 训练应看"中断率"而非"故障率"〔P411 p7〕；Meta CPO 评估以单个不可纠正码字定义中断，CPO 平均 pre-FEC BER 约 9e-8、FRO 约 1e-9，但 CPO 年链路中断率 0.2%–0.47% 低于 FRO 1.22%，并指出 pre-FEC BER 单独作健康指标不可靠（实验）〔P437 p5, p6〕。
- 规模放大效应：Marvell 估算约 3M GPU、>10M 光链路的集群约每 48 秒一次 flap（估算）〔P345 p11〕；OCP SROI 工作流把目标定为每链路端 ≤2 FIT、每 1M 器件小时 0 次 flap，对比可插拔 50–100 FIT（需求/目标，面向 scale-up）〔P346 p5〕。Microsoft 主张把同一端口的 lanes 分到不同 flap 故障域，4×200G 模式下单 lane flap 只降级而不终止作业（分析）〔P345 p30–p32〕。
- 主因是污染：Oracle 90% 的 L1 链路故障与污染有关，97% 的光模块更换源于污染（现网），扩束连接器插拔力约降 20 倍〔P438 p11, p12〕。Corning 透镜 MMC 50 次插拔不清洁，最大 ΔIL 0.26 dB 对物理接触 1.42 dB，16 端口部署 8 min 43 s 对 1 h 19 min（实验）〔P343 p11, p13〕。
- 标准动作：OCI 提交 Enhanced Telemetry Optics 软件规范 v1.0〔P370 p19〕；Credo 基于 CMIS CDB 一条命令返回身份、健康分、遥测、告警，48 个收发器试验中健康分随 0/5/10 dB 衰减为 80/60/40（实验）〔P408 p9, p15〕；Oracle 把 DSP 消失后需保留的职能归纳为 Detect、Localize、Remember、Reach、Remediate〔P443 p9〕。

---

## 1. 需求与架构

### 1.1 需求数字

| 类别 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| 每 GPU 网络带宽 | 约 2016 年 50 Gbps → 2022–24 约 400 → 2025 约 800 → 2026 约 1,600 Gbps（Google） | 看图 | 〔P130 p3〕 |
| NIC 速率与集群规模 | NIC 25 Gbps（2017）→ 1,600 Gbps（2026），网络集群性能 256 倍；集群 16,384 → 131,072 GPU（2020–2026） | 自报（Oracle） | 〔P438 p2, p3〕 |
| 集群规模演进 | 128 → 2K → 4K → 8K → 24K（单楼，2022–23）→ 129K（多楼，2024）→ 多区域（2025+） | 看图（Meta） | 〔P244 p4〕〔P417 p2〕 |
| 设计目标 | MRC 目标 10^6 节点；MetaRoCE "今天数十万加速器，按百万设计" | 自报 | 〔P133 p2〕〔P296 p2〕 |
| 通信占比 | 14–32% 机队 GPU 小时为无重叠计算的通信；>75% 训练字节为 TP 且不出 NVLink 域；Llama-3 容忍 1:7 跨 pod 超额 | 引用（MAD-Max、Meta SIGCOMM'24、Llama-3） | 〔P111 p2〕 |
| scale-up 与 scale-out 比 | scale-up 约需 10X scale-out 带宽；10–20 Tbps/xPU（后者引用 NVIDIA） | 自报/引用 | 〔P134 p18〕〔P273 p3〕 |
| AMD Helios | 每柜 scale-up 260 TB/s，scale-out 43 TB/s；每 GPU scale-out 最高 2.4 Tb/s/dir | 自报 | 〔P126 p2, p3〕〔P363 p15〕 |
| 交换 ASIC 功耗 | 12.8T 350–400 W（2018）→ 25.6T 450–500 W → 51.2T 700–800 W → 102.4T 900–1000 W（2024） | 自报（未注来源） | 〔P421 p16〕 |
| 可靠性规模 | MTBF：8 GPU 47.7 天；1,024 GPU 7.9 h；16,384 GPU 1.8 h；131,072 GPU 15 min | 引用（arxiv 2410.21680），看图 | 〔P421 p16〕 |
| 网络功耗份额 | 网络约占总功耗 10–15% | 自报估算（Microsoft） | 〔T06 19:18–19:55〕 |
| 光纤规模 | DC 内 >10M 根光纤，DC 间 >4M（引用 Meta）；Feynman 级机柜后端约 18,464 芯 | 引用/预测 | 〔P273 p3〕〔P316 p3〕 |
| 推理形态 | Prefill:decode 实例比：聊天 ~1:2–1:4，推理/agent ~1:3–1:10，文档摘要 ~2:1–4:1 | 自报 | 〔P119 p25〕 |
| 推理对网络 | 分布式推理把网络方差变成 token 完成时间方差；PD 分离后 TTFT 成为网络指标 | 自报（无实测） | 〔P149 p2, p5〕〔P301 p8〕 |

### 1.2 距离与规模分层（各家口径）

| 机构 | 分层 | 索引 |
|---|---|---|
| Microsoft | 前端 <2 km；Scale Out <1 km；Scale Up <50 m；Scale In <1 m | 〔P147 p43〕（看图） |
| Broadcom/Arista | Scale Up <30 m（单跳、DAC）；Scale Out >1K GPU（多平面、2/3 层 leaf-spine）；Scale Across 100+ km | 〔P146 p2〕 |
| Broadcom | scale-up 低时延无损（CBFC、LLR）；scale-across km 级大 RTT、有收敛比、大缓冲 | 〔P134 p18〕 |
| Meta（园区） | <3 km FR / FR4；≤10 km LR / LR4；>10 km ZR+ + DWDM（ZR+ ≤1000 km） | 〔P247 p12〕〔P424 p10〕 |
| Google（园区） | Virgo 限单楼；楼间平均光纤距离 <2 km，带宽数十到数百 Pbps | 〔P147 p5, p6〕 |
| Celestica | 无源 DAC ≤1.0 m（224G）；ACC 1.2–2 m；AEC 2–5 m；LPO 2–10 m+；LRO/FRO 10–500 m；相干 ZR/Lite 500 m–10 km+ | 〔P448 p6〕（看图） |
| Samtec | DAC ~2 m、ACC ~5 m、AEC ~7 m、LPO ~50 m、AOC ~100 m+ | 〔P298 p3〕（看图） |
| OCP SROI（AMD/Lightelligence） | scale-up <30 m、RTT <1 µs、每 XPU ~1,000 GB/s、256 到 1,000+ XPU；scale-out <2 km、RTT <10 µs、每 XPU ~400 Gb/s、最多 10,000 节点；>3 m 必须用光 | 〔P346 p4, p11, p12〕 |
| Meta（AEC） | 柜内 DAC ≤~2 m；柜到柜 AEC ~2–7 m（p5 写 1.0–3.2 m，口径不一，存疑）；出柜光 ~7–500 m | 〔P179 p3, p4, p5〕 |

几家对"scale-out 到多远"并不一致：Microsoft 把 scale-out 限在 1 km 内，Google 把楼间 2 km 级链路视为"园区级 scale-out"，Meta 则把 3–10 km 的 LR 归入跨楼。分界的物理依据是色散：Linktel 引 Zhou et al. OFC 2023，无色散管理时 100G/lane 10 km、200G/lane 2.5 km、400G/lane 600 m〔P254 p3〕；Google 认为 400G/lane IMDD 超过 2 km 受色散限制，WDM 约 16 波即到上限〔T06 05:21–05:40〕。

### 1.3 架构演进要点

1. **两层多平面成为主线**。Arista/AMD 给了两种切法：plane per NIC（6,912 GPU，2 平面，每 GPU 2×800G，收敛比 0.84:1）和 plane per SerDes（8 平面各 200G，两层最大 129,024 GPU，收敛比 0.98:1，需 shuffler），验证集群 504 GPU、TH6、Arista 7060XE7、MRC、SRv6-uSID（实验，未给性能结果）〔P140 p13, p14, p16〕。Microsoft MRC 拓扑为 256 T1 × 8 平面、512 T0 × 8 平面，每组 256 GPU（看图）〔P369 p14〕。
2. **三层 rail-optimized 仍在现网**。NVIDIA 典型单 zone：288 super spine、192 spine、144 ToR、48 机柜、3,456 GPU，8 平面，上层最多 3:1 收敛，链路 400G〔P409 p4〕；Edgecore 的 AMD GPU 云用两层 rail-optimized Clos，TH5 51.2T，PFC/ECN + DLB（现网）〔P401 p3〕。
3. **NSF 与 DSF 两类 fabric**。端点调度/非调度 fabric（NSF）低时延、布线简单；交换机调度 fabric（DSF）NIC 无关、深缓冲〔P141 p4〕。Meta NSF 每 L2 fabric 最多约 21K GPU，8 个 spine 平面，跨 L2 过订约 5:1〔P424 p6〕；Meta LPO 现网部署在 DSF fabric 的 DTSW–EDSW 一跳〔P411 p5〕。
4. **开放参考设计**。OCP Open Cluster Designs for AI 已发布 400G 风冷 OPG-128（2026-01），800G/1.6T 液冷 OPG-576 于 2026-02 启动，设计迭代周期约 2 年〔P119 p6–p8〕；53 家成员，V1.0 蓝图覆盖 XPU pod 到 XOC-N〔P366 p23〕。
5. **控制面减负**。阿里 HPN Pivot 把服务路由分发与基础设施路由解耦，peer 数从 200 以上降到 4，每平面每协议 4 个 RR 实例，引入 BGP Group GR（自报，架构示意）〔P414 p6, p8, p9〕。引用 Microsoft：单端口抖动数据面中断 <0.1 s、路由收敛约 5 s〔P414 p2〕。这解释了为什么 MRC 要让端点不依赖路由收敛。
6. **高 radix 再往上**。Eridu 提出单台 1P 交换机替代 30 台 102T 两层（看图），并称实际交换时延每多一级加约 10X 标称值（自报假设）〔P108 p6, p8〕；Delos/Eridu 仿真 230T 交换机 GPU 利用率 64%、petabit 交换机 88%（仿真，引用 Turbalance）〔P128 p16〕。这一路线目前主要服务 scale-up 多机柜域，scale-out 侧没有落地案例。

---

## 2. 技术路线对比

### 2.1 传输协议

| 路线 | 代表方案/厂商 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| RoCEv2 + DCQCN/PFC | AMD GPU 云（Edgecore）、多家 CSP | PFC/ECN + DLB 能满足要求；多厂商 QoS（DSCP/MTU/PFC 优先级）不一致是主要问题 | 现网 | 〔P401 p3, p4〕 |
| MRC 1.0 | OpenAI 牵头，AMD/Broadcom/Intel/Microsoft/NVIDIA；OCP MSA | 每 QP EV 128–256 项；仅 Write 与 Write-with-Immediate；libibverbs；NSCC；SRv6 uSID 可选 | 生产：OpenAI、Microsoft、OCI | 〔P122 p4, p7, p8〕〔P132 p3〕〔P422 Q&A 见 T04 17:29〕 |
| MRC（Microsoft 实现） | SMaRTT（ECN+RTT+可选裁剪）+ ReSS（少量子流、随机重路由最拥塞子流） | 生产 50K/75K GPU；20 链路故障实验双向约 1,550 Gb/s 基本不变（看图） | 现网，单 NIC 厂商 | 〔P418 p8, p9, p10〕 |
| UET（UEC 1.0.3） | UEC；HPE Slingshot 转向 UET | Read/Write/Send/Atomics；libfabric；NSCC 或 RCCC；LLR、CBFC、CSIG | 规范 2025 发布，生态较晚 | 〔P122 p15〕〔P132 p3〕〔P373 p9〕 |
| MetaRoCE | Meta + AMD Pensando；NVIDIA 合作中 | QP 内多路径、逐路径 AIMD；scale-out RTT 5–15 µs、Max Path ~12；scale-across RTT ~1.5 ms、Max Path ~30–50；网络效率 >90%（自报） | 8 月发布，OCP 开源 libsoftmetaroce / dpdkmetaroce | 〔P296 p3, p9〕〔P244 p23, p24〕〔P419 p16〕 |
| Falcon | Google | 包喷洒、亚微秒 Swift 与 CSIG、SACK+RACK 硬件恢复、线速 PSP | 已在 NVIDIA ConnectX/BlueField 互通 | 〔P130 p9〕〔P367 p16〕 |
| Spectrum-X Adaptive RDMA | NVIDIA | 同时承载 Falcon、Meta RoCE、MRC | 自报 | 〔P367 p14–p16〕 |
| Omni-Path / UE | Cornelis CN5000/6000/7000 | CN5000 对 NDR 400G 延迟最多低 32%、消息率最多 2.3x（自报/实验） | CN5000 出货，CN6000 送样 | 〔P301 p3, p9〕 |

### 2.2 拥塞控制与负载均衡

| 机制 | 方案/来源 | 要点 | 口径 | 索引 |
|---|---|---|---|---|
| DCQCN | 传统 RoCE | 依赖 ECN+PFC，扩散拥塞、队头阻塞、难调且不可互通 | 自报（Broadcom） | 〔P135 p6〕 |
| NSCC | UEC/MRC | 以时延为主要拥塞量，ECN 为先行指标；比例+指数增、乘性减 | 自报 | 〔P135 p10〕 |
| RCCC | UEC | 无 PFC 有损网络；首 RTT 线速，之后接收端发 credit；一个 RTT 收敛，稳态末跳队列为 0 | 自报 | 〔P135 p8〕 |
| CSIG | Google 提出，UEC Transport WG 标准化 | 每包携带路径最小可用带宽、最小可用容量%、最大单跳时延 | 自报 | 〔P135 p13〕〔P141 p10〕〔P130 p10〕 |
| Packet trimming | MRC/UEC | 截断包走高优先级队列，接收端回 NACK，重传在 1 个 RTT 内 | 自报 | 〔P141 p10〕〔P135 p12〕 |
| 只用 ECN+ECMP | MetaRoCE | 不需要 trimming、AR、INT；N 个包丢失触发乘性减 | 自报 | 〔P296 p4, p6, p7〕 |
| 源路由 | SRv6 uSID + MRC | 两层网络 GPU 到 GPU 4 跳，可放入一个 IPv6 DA 的 6 个 uSID；SRv6 为可选，MRC 也支持熵 ECMP | 自报 | 〔P141 p8〕〔T04 10:33–12:09, 17:29〕 |
| flowlet / DLB | CSP B、Edgecore | Meta 调 flowlet timer + CC 后，32 并行 ring NCCL 峰值 bus BW 58.4→75.5 GB/s（+29%） | 实验/现网，看图 | 〔P415 p5, p11〕 |
| 交换机内公平调度 | Eridu | 1,000 端口仿真，90% 负载 p99.99 时延：到达时间调度比 DWRR 低 31% | 仿真，看图 | 〔P108 p20〕 |

### 2.3 102.4T 交换芯片与系统

| 器件/系统 | 厂商 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| Tomahawk 6 | Broadcom | 102.4 Tbps；128×800G 或 512×200G | 量产中 | 〔P366 p5, p16〕〔P134 p10〕 |
| Spectrum-6 | NVIDIA | 102.4 Tb/s，512×200G 或 128×800G，可插拔与 CPO | 自报 | 〔P409 p6〕 |
| Silicon One G300 | Cisco | 102.4T；Nexus One 3RU/3OU 64×1.6T OSFP | 自报 | 〔P404 p3〕〔P101 p14〕 |
| Meta IceCube | Meta + Celestica | 2OU，TH6C，64×OSFP，无 PHY + 212G flyover 铜缆；ASIC 与 OSFP 液冷约 85%；blade 典型最大 3,820 W（全 retimed DR4）；规范 2026-09 提交 | 自报 | 〔P407 p2, p4, p9, p13〕 |
| Meta N-IceCube | Meta + Accton | Spectrum-6，212G PAM4 100% PCB 走线，2×8 叠层 OSFP 笼 | 自报 | 〔P407 p11〕〔P244 p8〕 |
| Meta 102.4T CPO/NPO | Meta | 1.5OU，64 数据端口（MMC16），16 个 ELSFP 端口，100% 液冷；目标比 retimed 可插拔省 60% 光功耗 | 预测 | 〔P437 p7, p10〕 |
| Supermicro SSE-T8264 | Supermicro | 64×1600G OSFP 102.4T，GA CQ4/26；CPO 版 GA CQ1/27，均跑 SONiC | 自报 | 〔P265 p14〕 |
| HPE QFX 1.6T | HPE | 自称业界首款 DLC ORv3 QFX 1.6T 交换机 | 自报 | 〔P373 p9〕 |
| Celestica DS6005 | Celestica | 基于 TH6 Davisson CPO，计划贡献给 OCP | 自报 | 〔P142 p9〕〔P253 p18〕 |
| Cornelis CN7000 | Cornelis | 72×1.6T 端口，每交换机 96 个 RISC-V 核、48 MB SRAM；2027 流片 | 预测 | 〔P301 p9, p11〕 |

### 2.4 NIC

| 方案 | 关键指标 | 口径 | 索引 |
|---|---|---|---|
| Broadcom Thor Ultra | 800G；拆分 1×800G / 2×400G / 4×200G / 8×100G | 自报 | 〔P134 p11〕〔P366 p5〕 |
| AMD Pensando Vulcano | 800G；每 GPU 1 或 2 张；可编程，支持 RoCEv2/MRC/UEC；1.6T OSFP cage 两 GPU 共享 | 自报 | 〔P140 p11〕〔P126 p10〕 |
| AMD 可编程 AI NIC（Meta） | P4DMA + P4NET，8×100G 不相交平面，PCIe Gen6 | 自报，看图 | 〔P296 p8, p11〕 |
| NVIDIA ConnectX-8 | 800 Gb/s，拆 4×200 Gb/s 平面（Microsoft 现网） | 现网 | 〔P418 p10〕 |
| OCP NIC 3.0 v1.7 | PCIe Gen 7 可达 1.6 Tbps；SFF-TA-1037 4C+ EP 连接器支持 200 W（传统 80 W） | 标准进展 | 〔P453 p3, p8〕 |
| Microsoft 800G SmartNIC | 无量化；固件变为多组件版本化 recipe；7 阶段部署验证 | 经验 | 〔P467 p6, p8〕 |

NIC 正在吸收原本属于交换机的职能：负载均衡、乱序、故障检测由 NIC 硬件/固件承担〔P140 p8〕，NIC 功耗随之上升到 200 W 级并需要液冷〔P453 p6, p8〕。

### 2.5 可插拔光模块与形态

| 路线 | 代表方案/厂商 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| FRO（全重定时） | 通用 | 1.6T Full DSP <24 W；FRO 18–25 pJ/bit（500 m–10 km） | 主力 | 〔P279 p11〕〔P147 p41〕 |
| LPO | Meta 100G/lane、Oracle 800G | 1.6T LPO <10 W，环回 BER <E-8（GO）；LPO 7–10 pJ/bit | 800G 现网；1.6T 有分歧 | 〔P279 p11〕〔P147 p41〕〔P411〕〔P438〕 |
| LRO | Oracle、GO | 1.6T 26 dB 通道 16 W（10 pJ/bit），FEC bin p50/p95 1/2；GO 1.6T LRO <15 W，24 dB 损耗下 BER E-13 级 | 多厂商 3 nm DSP 互通演示 | 〔P438 p9〕〔P279 p11〕 |
| XPO（12.8T 可插拔） | Arista 牵头 XPO MSA；FIT、Amphenol、TeraHop、GO | 每模块 224G 下 12.8T、448G 下 25.6T；1OU 204.8T；集成液冷；功耗 <130 W（GO LRO）、约 200 W（TeraHop FRO）、线性 <90 W（Amphenol） | MSA Release 1.0（2026-07-31），100+ 公司；TeraHop 预计 2027 年内生产部署，25.6T XPO+ 早期开发 | 〔P238 p4, p5〕〔P441 p4〕〔P279 p12〕〔P273 p7〕〔P431 p5〕〔P341 p4〕〔P336 p7〕 |
| DMD-CWDM | Linktel | 硅 GT 标准具色散管理，800G 2LR4+ 20 km、1.6T 2FR4 10 km；36 只模块温循 pre-FEC BER <1e-7 | Alpha/Beta | 〔P254 p4, p7〕 |
| 400G/lane 1.6T DR4 | GO | 4×425G PAM4 光、8×212.5G 电，3 nm DSP，~30 W，500 m，BER ~E-6 | 演示 | 〔P279 p14〕 |
| AEC（柜到柜） | Meta 800G AEC | <12 W/端，1.0–3.2 m；"数百万" AI 互连；故障多源于固件而非 SI | 现网 | 〔P179 p5, p6, p8〕 |

### 2.6 OCS

| 技术 | 重配置时间/特征 | 索引 |
|---|---|---|
| 3D MEMS | 毫秒级，已大规模验证（Google）；dark time 约 20 ms | 〔P136 p5〕〔P111 p9〕 |
| 超表面（自由空间） | ~50 μs | 〔P136 p5〕 |
| 集成光子 MEMS / 热光 / 电光 | 1–20 μs / 10–100 μs / ns–μs | 〔P136 p5〕 |
| 硅光 OCS | dark time 0.3 ms | 〔P111 p9〕 |
| 机械手（Telescent 等）/光束偏转/硅光 | 协议速率透明，功耗低于电交换机 5% | 〔P427 p2〕 |

---

## 3. 关键数据表

### 3.1 功耗（pJ/bit 与 W）

| 对象 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| 能效阶梯（Microsoft） | 传统相干转发器 >1000；400ZR 45–55；FRO 18–25；LRO 10–18；LPO 7–10；NPO 5–8；CPO 1–5 pJ/bit | 自报 | 〔P147 p41〕 |
| 200G 链路（Broadcom） | DAC 7 pJ/bit / 2 m；集成 OCI 7 pJ/bit / 500 m；DR LRO 前面板可插拔 23 pJ/bit / 500 m | 自报，看图 | 〔P433 p13〕 |
| 能效阶梯（Nokia） | retimed 可插拔 ~15；LRO ~10；LPO/NPO/CPO ~6；die-to-die 集成光 <4 pJ/bit（距量产数年） | 自报 | 〔P335 p2〕 |
| SROI 目标与方案 | 目标：每链路端 ≤5 pJ/b（仅光学）、≤10 pJ/b（SerDes+光学）；LPO 5–6、RTLR 8–10、NPO ~5、CPO 4–5（PAM4）/ 3（DWDM） | 需求/自报 | 〔P346 p5, p6〕 |
| 分项估读（TeraHop） | CPO+ELS ~6.6、NPO+ILS ~5.75、LPO ~6.4 pJ/b | 看图估读 | 〔P341 p15〕 |
| 激光到调制器损耗 | 单片 InP 0.25 dB；PIC 集成 0.5–1 dB；封装内微光学 1.5 dB；ELSFP 2 dB | 自报（Nokia） | 〔P335 p5〕 |
| 光可插拔 vs 电 | 光 10–15 pJ/bit、>10 m；DAC ~2，ACC/AEC 2–5 pJ/bit、<1.5 m | 自报/引用（未注） | 〔P421 p16〕 |
| 1.6T 模块 | Full DSP <24 W，LRO <15 W，LPO <10 W | 实验（GO） | 〔P279 p11〕 |
| 1.6T LRO | 16 W，约 10 pJ/bit，26 dB 通道 | 自报/现网（Oracle） | 〔P438 p9〕 |
| 光模块功耗趋势 | 400G ≈9 W、800G ≈15 W、1.6T ≈25 W、3.2T ≈40 W | 自报/预测（HFH） | 〔P302 p6〕 |
| LPO 模块级 | 固定风扇下每模块 −46%，温度低 17.5 °C | 实验（Meta） | 〔P411 p9〕 |
| LPO 系统级 | 64×800G 交换机半 LPO 比全 FRO 中位低 258 W（模块 192 W + 风扇 66 W） | 现网（Oracle） | 〔P438 p8〕 |
| CPO/NPO | 相对全重定时可插拔预计最多省 50%（引用 NVIDIA 博客、SemiAnalysis）；Meta 102.4T 目标省 60% 光功耗；相对 DSP 可插拔省 65%（引用 OFC2026 M4B.6） | 引用/预测 | 〔P438 p10〕〔P437 p7〕〔P434 p7〕 |
| NPO | Open CPX NPO 含内置激光约 5.5 pJ/b | 自报（TeraHop） | 〔P441 p14〕 |
| 风冷上限 | >35 W 的模块从未以风冷出货；模块内液冷 ~120–500 W | 自报（TE） | 〔P005 p3, p4〕 |
| XPO 液冷 | 12.8T XPO 在 45–55 °C 进液、0.3–0.5 LPM 下约 197–202 W | 实验，看图 | 〔P441 p7〕 |

### 3.2 可靠性

| 对象 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| Meta LPO vs retimed | 中断 2.0× 更少，影响业务故障 2.6× 更少；最近 60 天 8.4×；4k 模块、4 个月 | 现网，看图 | 〔P411 p8〕 |
| Meta LPO 实验室 | ~1k 模块，0 次模块归因故障/2.96M link-hours；104 天光功率波动 ≤0.25 dB | 实验 | 〔P411 p9〕 |
| Oracle LPO vs FRO | down transition 链路 3.244% vs 5.681%；纠正符号率中位 3.1e-8 vs 1.6e-7 | 现网 | 〔P438 p7〕 |
| Meta CPO vs FRO | 年链路中断率 FRO 1.22%（MTBI 0.72M）；CPO Phase 1 0.47%（1.85M）；Phase 2 0.2%（4.5M）；排除 ELS SMT 0.04%（25M）；ELS 模块占 CPO 故障 85% / 83% | 实验 | 〔P437 p4, p6〕 |
| Broadcom CPO | >1M 器件小时 0 次 link flap；"10 倍可靠性提升" | 自报，未给条件 | 〔P433 p3, p4〕 |
| 硅光 PIC | GO：>8B 器件小时，PIC FIT <0.2；TeraHop：>100B 器件小时，FIT <0.01 | 现网/自报 | 〔P279 p10〕〔P441 p16〕 |
| Meta 中断来源 | scale-out 网络 23.6% / 11.7%（Platform-A/B）；2026 年 1–9 月中断率降 75% / 87% | 现网 | 〔P125 p8, p10〕 |
| GB200 中断率 | 约 230 降至约 4–5 次/8K GPU/天，目标 2.0 | 看图，实测+外推 | 〔P364 p15〕 |
| 污染 | 90% L1 链路故障与污染有关，97% 光模块更换源于污染 | 现网（Oracle） | 〔P438 p11〕 |
| 透镜连接器 | 50 次插拔不清洁最大 ΔIL：透镜 0.26 dB vs 物理接触 1.42 dB；凝露测试最大 ΔIL 0.29 dB | 实验（Corning） | 〔P343 p13, p14〕 |
| SROI 可靠性目标 | ≤2 FIT/链路端，每 1M 器件小时 0 次 flap；可插拔 50–100 FIT；CPO FIT 比可插拔好 5× | 需求/自报 | 〔P346 p5, p6〕 |
| Flap 规模估算 | ~3M GPU、>10M 光链路约每 48 s 一次 flap；10,000 Flap FIT 时 1024 GPU pod MTBF 0.76 h，10 Flap FIT 时 762.94 h | 估算/示意计算 | 〔P345 p11, p28〕 |
| NVIDIA 多平面 | 故障检测 2.6 ms，MTBI 高 10x | 看图，自报 | 〔P367 p14〕 |

### 3.3 时延与故障恢复

| 对象 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| MRC 故障恢复 | 75K GPU，T1 交换机失效，约 1 分钟恢复；约一个 RTT 量级检测 | 现网，看图/转写 | 〔P133 p13〕〔T04 13:05–14:18〕 |
| MRC 重路由 | 微秒级 | 自报 | 〔P122 p8〕 |
| trimming | 重传在 1 个 RTT 内 | 自报 | 〔P141 p10〕 |
| BGP 收敛 | 数据面中断 <0.1 s，路由收敛 ~5 s，端口/BGP 启动 100–150 s | 引用 Microsoft，看图 | 〔P414 p2〕 |
| 包喷洒 fabric 时延 | all-to-all 下 99p 10.5 µs、99.9p 13 µs | 引用 Fungible FCP | 〔P418 p6〕 |
| scale-out RTT | 5–15 µs | 自报（Meta） | 〔P296 p9〕 |
| 高 radix | 1/2/3 级实际时延约 5X/15X/25X 标称 | 自报假设 | 〔P108 p8〕 |
| 时间同步 | PTP 端到端 92 ns（Meta），ConnectX-7 PHC 12 ns；ePPS host 1PPS p-p 3.5 ns；PCIe PTM 2 级约 50 ns | 引用/实验 | 〔P111 p9〕〔P113 p10〕 |
| SONiC PTP | Phase 1 目标 202611 版本：单 ASIC one-step 硬件时间戳、BC | 自报 | 〔P110 p4〕 |

### 3.4 规模上限（两层 Clos 计算值与现网）

| 方案 | 规模 | 口径 | 索引 |
|---|---|---|---|
| 102.4T @800G / @200G 两层 | 8,192 / 131,072 客户端 | 计算 | 〔P140 p5〕 |
| TH6 4 平面 | 128K XPU | 自报 | 〔P134 p13〕 |
| AMD/Arista plane per SerDes | 两层最大 129,024 GPU | 自报，看图 | 〔P140 p14〕 |
| Microsoft Fairwater | 最多 524,288 GPU | 引用 | 〔P422 p9〕 |
| NVIDIA Spectrum-X Photonics | 512K GPU 两层 | 自报，看图 | 〔P367 p14〕 |
| Meta NSF | 每 L2 fabric ~21K GPU | 自报 | 〔P424 p6〕 |
| 现网作业 | Microsoft/OpenAI 50K、75K GPU | 现网 | 〔P418 p10〕〔P133 p12〕 |

### 3.5 集合通信性能

| 对象 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| MetaRoCE vs RoCEv2（64 GPU） | AllReduce 全部消息更快，小消息约 −20%~−27%，大消息约 −3%~−5%；All-to-All 多数 −15%~−21%，部分规模变慢 +6%~+19% | 看图，读柱估计 | 〔P296 p12〕 |
| 云上 GPU 调优 | 32 ring × 16 GPU，58.4→75.5 GB/s | 实验/现网，看图 | 〔P415 p11〕 |
| 负载干扰 | DP ALLREDUCE（64MB）在负载中慢约 1.8x，EP ALLTOALL 慢约 1.3x；原因是 EP 反向 A2A 与 DP 梯度 AR 重叠 | 实验（Meta/Keysight） | 〔P129 p9, p10, p12〕 |

---

## 4. 厂商与客户态势

### 4.1 超大规模用户

- **Meta**：传输自建 MetaRoCE 并开源两份实现〔P244 p23, p24〕〔P419 p16〕；拓扑走 FPF 两层多平面〔P244 p9〕；交换机 IceCube（TH6）/N-IceCube（Spectrum-6），FBOSS + SAI，IcePack 首个液冷网络机柜〔P244 p8〕〔P407 p2〕；光侧 LPO 现网数据〔P411〕、51.2T CPO A/B 评估与 102.4T CPO/NPO 计划〔P437〕、800G AEC 数百万量级〔P179 p6〕。上云 GPU 时三家 CSP 传输各不同，某 CSP 依 Meta 6 年无损 fabric 经验改为 PFC 无损后与 on-prem 持平（看图）〔P415 p5, p7〕。
- **Google**：Virgo 后端与 Jupiter 前端分开，两层多平面，Apollo OCS，HST 亚毫秒遥测，Firefly 时钟同步〔P130 p6, p8〕；Falcon 在 NVIDIA NIC 上互通〔P130 p9〕；OCS 接口规范 v0.8〔P427 p14〕。下一步把 CSIG 扩展到亚 RTT 拥塞控制（UEC）〔P130 p10〕。
- **Microsoft**：MRC 生产部署，GB200 + ConnectX-8 4 平面，Spectrum-4 与 Tomahawk-5 混合〔P418 p10〕；推动三级互通与 plugfest〔P418 p15〕；XPO 系统级评估（与 Arista）〔P446〕；光模块 SKU 主张收敛〔P147 p44〕。
- **OpenAI**：MRC 发起方，SRv6 源路由，单 DC 有望扩到 50 万 GPU（与 Fairwater 合作，预测）〔P133 p2〕〔T04 06:47–09:00〕。
- **Oracle（OCI）**：MRC 生产部署〔P122 p4〕；800G LPO 大规模现网与 1.6T LRO 判断〔P438〕；OCS zero-touch 生命周期〔P430〕；Enhanced Telemetry Optics v1.0、DSP 消失后的观测契约〔P370 p19〕〔P443〕。
- **Alibaba**：HPN Pivot 路由解耦〔P414〕；SONiC 模型驱动测试（与 Google）〔P121〕；scale-up LLR/CBFC 测试标准〔P426〕。
- **AWS**：本届 Out 方向材料中未见 AWS 后端网络讲稿。
- **其他运营方**：IREN 用 SONiC + Broadcom、Dell SONiC on Spectrum-X，裸机到可出 token 网络 <2 小时（自报）〔P420 p4〕。

### 4.2 芯片、系统与光器件厂商站位

- **Broadcom**：TH6、Thor Ultra、Jericho 4 全线〔P366 p5〕；拥塞控制同时押 NSCC 与 RCCC〔P135〕；CPO 第三代 TH6 Davisson 已出，第四代 2028〔P433 p4〕；在 OCI-MSA 中把 scale-up 光引向集成光〔P433 p11, p13〕。
- **NVIDIA**：Spectrum-6 与 Spectrum-X Photonics，以"支持多种传输"作为卖点〔P367 p14–p16〕；用 SAI + SimX 让 Meta 硬件到货约 1 周测试通过率 90%（自报）〔P409 p13〕。
- **AMD**：Pensando Vulcano 可编程 NIC 同时支持 RoCEv2/MRC/UEC/MetaRoCE〔P126 p10〕〔P363 p15〕；Helios 已在 OpenAI、Meta、Anthropic、Microsoft、Oracle 部署（看图）〔P363 p17〕。
- **Cisco**：Silicon One G300 102.4T、P200 深缓冲〔P404 p3〕；SONiC 安全路线（漏洞屏蔽 2027 Q2）〔P318 p7〕；SRv6〔P422〕。
- **Arista**：XPO MSA 牵头〔P264 p8〕；多平面验证集群〔P140 p16〕。
- **整机/ODM**：Celestica（IceCube、DS6005、开放集群设计）、Accton（N-IceCube）、Edgecore、Supermicro〔P407 p2, p11〕〔P401 p3〕〔P265 p14〕。
- **光模块与器件**：GO 主推 NPO 为近期甜点，并给出 1.6T LPO/LRO/FRO 功耗三档〔P279 p11, p17〕；TeraHop 主张 NPO 集成激光而非 ELSFP〔P441 p14〕；Linktel 用 DMD 延长 CWDM〔P254〕；Credo 从 AEC/ALC 切入遥测光模块〔P408〕〔P289 p10〕；Lumentum 做 OCS 量产〔P430 p11〕。
- **连接器/线缆**：Amphenol、FIT、Luxshare、TE 都在做 448G 无 stub 接口，分歧在 92 Ω 还是 85 Ω、PAM6 还是 PAM4〔P431 p28〕。

### 4.3 OCP 标准、MSA 与工作组进展

| 项目 | 状态 | 索引 |
|---|---|---|
| MRC 1.0 | 2026 年经 OCP MSA 发布 | 〔P132 p3〕 |
| UEC | 1.0（2025），当前 1.0.3；CSIG 在 Transport WG；BTS WG 在写规范 | 〔P122 p4〕〔T05 16:04〕 |
| MetaRoCE | 规范 + 两份开源参考实现 + 合规测试，目标 OCP 多厂商标准 | 〔P296 p13, p14〕〔P419〕 |
| OCS 子项目 | 白皮书 2026-04；YANG R1.0；Interface Spec v0.8；SONiC OCS 工作组 | 〔P136 p10〕〔P421 p13〕〔P427 p14〕〔P430 p14〕 |
| 光可靠性 | Enhanced Telemetry Optics 软件规范 v1.0 提交；Optics Telemetry 草案 rev0.9 | 〔P370 p19〕〔P443 p11〕 |
| XPO MSA | Release 1.0 2026-07-31，100+ 公司（另一页写 150+，口径不一） | 〔P441 p4〕〔P273 p5〕 |
| SAI | PerfMon #2287 已合入；Constraints API #2294 评审中；BTS SAI PR #2349 | 〔P405 p3, p11〕〔P146〕 |
| 平台层 | OSPA Spec 1.0 提交评审；Open Switch Platform 1.0 评审中（Meta/Microsoft/Alibaba 发起） | 〔P413 p8〕〔P244 p21〕 |
| SONiC | 4,250+ 贡献者、520+ 组织；PTP 202611；AI 路线含 SRv6、trimming、高频遥测 | 〔P318 p3〕〔P110 p4〕 |
| OCP NIC | v1.7 加入 PCIe Gen 7，200 W 连接器 | 〔P453〕 |
| Open Cluster Designs | 53 家成员，V1.0 蓝图，第二代开发中 | 〔P366 p23〕〔P119〕 |

---

## 5. 分歧与未决问题

1. **要不要交换机配合（trimming、CSIG、AR）。** MRC/UEC 把 trimming 和 CSIG 作为信号源〔P141 p10〕〔P135 p12, p13〕；MetaRoCE 明确不需要 trimming、AR、INT，只用 ECN + ECMP〔P296 p4〕。Arista 指出 trimming 和 CSIG 都会在关键链路上增加前向流量〔T05 08:10–08:37〕。未决原因：MetaRoCE 只给了 64 GPU 对 RoCEv2 的对比〔P296 p12〕，MRC 给的是故障恢复而非 CC 效率对比，两者之间没有同条件对比数据。
2. **发送端还是接收端拥塞控制。** MRC 1.0 只有 NSCC；UET 有 NSCC 与 RCCC〔P122 p15〕。RCCC 稳态末跳队列为 0〔P135 p8〕，但 Arista/Broadcom 认为接收端授信适合单一应用独占链路，混合流量需要对网络实时状态反应〔T05 17:24–17:51〕。
3. **无损还是有损。** Broadcom、Meta MetaRoCE 都说 PFC 不可扩展〔P135 p6〕〔P296 p5〕；Edgecore 现网称 PFC/ECN + DLB 能满足要求〔P401 p3〕；Meta 自己在某 CSP 上把"无流控"改成"PFC"并与 on-prem 持平〔P415 p7〕。同一家公司在自研传输与云上调优里给出相反做法，说明"有损"目前依赖 NIC 传输是否已换代。
4. **1.6T 是否还用 LPO。** Oracle：LPO 难满足 SI 与互通，LRO 最佳〔P438 p9〕；Meta：证据来自 100G/lane LPO，结论延伸到 200G/lane LRO/LPO 和 NPO〔P411 p3〕；GO 展示 1.6T LPO <10 W，但环回 BER <E-8，FRO/LRO 为 E-13〔P279 p11〕；Microsoft/Arista 实测 LPO Tx 需继续优化〔P446 p18〕。未决原因：1.6T LPO 没有现网数据，Meta 的外推是推论。
5. **pre-FEC BER 能否当健康指标。** Meta CPO 数据显示 CPO pre-FEC BER 更差但中断更少，失败与健康链路的 BER 分布大幅重叠〔P437 p5〕；阿里 LD/RD 以 pre-FEC BER 超阈值把路径移出 ECMP〔P429 p13〕；Oracle 比较 LPO/FRO 时也以 pre-FEC BER 为主要指标〔P438 p6〕。各家对"链路健康"的定义没有统一，这正是 Enhanced Telemetry Optics 要解决的问题。
6. **前面板 XPO 还是 CPO/NPO。** Microsoft 认为推理负载的单 SoC 带宽在 1–2 代内不需要更深集成，XPO 可服务性与低 blast radius 有优势〔P446 p7〕；Broadcom 以 CPO 可靠性 10 倍为主要论据〔P433 p3〕；Meta 下一步是 102.4T CPO/NPO〔P437 p7〕。Meta 数据同时显示 CPO 故障 83–85% 来自 ELS 模块〔P437 p4〕，TeraHop 据此类论据主张集成激光〔P441 p14〕。
7. **平面切多细。** plane per NIC 布线简单、规模 6,912 GPU；plane per SerDes 到 129,024 GPU 但需要 shuffler〔P140 p13, p14〕。NVIDIA 现网参考设计仍是三层 rail-optimized、上层 3:1 收敛〔P409 p4〕。切细的代价（shuffler、光纤数、单链路 100G/200G 上的 ECMP 碰撞）没有成本数据。阿里现场测试发现长途 100G 链路易哈希碰撞，"粒度越大哈希越好"〔T04 34:42〕，与多平面"拆细链路"的方向存在张力，后者靠 NIC 喷洒绕开哈希问题。
8. **scale-out 的规模口径。** OCP SROI 文件把 scale-out 写成"最多 10,000 节点、每 XPU ~400 Gb/s"〔P346 p4, p12〕，与 Meta/Microsoft/OpenAI 实际的 50K–129K GPU、每 GPU 800G–1.6T〔P418 p10〕〔P244 p4〕〔P130 p3〕差一个量级。这是写需求时的保守示例，引用时需注明。
9. **光源放哪。** Nokia 认为光引擎移出主机热区后片上激光重新可行，ELSFP 只作最热最密场景的备选，ELSFP 到调制器损耗 2 dB 为四种方式中最高〔P335 p5, p8〕；TeraHop 同向，称 ELSFP 需 2 倍以上激光功率〔P341 p11〕；Ayar Labs/Wiwynn 则展示 100+ 个 ELSFP 模块平均 23.4 dBm、RIN 均值 -158 dB/Hz 的一致性（实验，CPO 场景）〔P344 p4, p5〕。scale-out 的 NPO/CPO 交换机选哪种，目前 Meta 102.4T 设计仍是 16 个 ELSFP 端口〔P437 p10〕。
10. **OCS 在 scale-out 的价值。** Google 引用 Jupiter 数据（−30% capex、−41% 功耗，引用）〔P111 p3〕；P111 的实验说明 per-round 电路交换在预测误差大时输给包交换 3×，只有 slack 足够才赢 2×〔P111 p7〕。快速 OCS 需要光模块快速锁定与控制面对齐〔P136〕，目前无多厂商数据。

---

## 6. 判断与时间线（未来 12–36 个月）

| 时间 | 里程碑 | 依据 |
|---|---|---|
| 2026 Q4 | Supermicro 102.4T 可插拔交换机 GA；SONiC PTP Phase 1（202611）；ESUN 1.1（2026.10–11）；Cornelis CN6000 扩大供货；SONiC scale-up 开源测试框架 | 〔P265 p14〕〔P110 p4〕〔P417 p13〕〔P301 p9〕〔P426 p16〕 |
| 2026 Q4–2027 | MRC 多 NIC 互通 plugfest（未给日期） | 〔P418 p16〕 |
| 2027 Q1 | Supermicro 102.4T CPO 交换机 GA | 〔P265 p14〕 |
| 2027 | XPO 与 Open CPX 预计生产部署（TeraHop 预测），IMDD 3.2T 约 2027–2028；SROI 分层：LPO/RTLR 当前、NPO 1–2 年、CPO 2–3 年以上；Open CPX Rev 1.1（2027.3）、Rev 2.0（2027.6）；LPO 仅在 SI 余量验证处扩大；XPO 工程探索；CPO 交换机 2027–2029 先增长；SONiC 漏洞屏蔽 Q2；Credo 1.6T ALC 量产；CN7000 流片；OFC2027 多厂商 OCS 故障恢复演示 | 〔P341 p4〕〔P346 p6〕〔P298 p12〕〔P264 p9–p10〕〔P318 p7〕〔P289 p10〕〔P301 p9〕〔P421 p12〕 |
| 2027–2028 | LightCounting 预测 LPO/NPO/CPO 约 2027–2028 起快速增长，NPO 主要由 scale-out 驱动（引用） | 〔P279 p5〕 |
| 2028 | OPG-576 液冷 800G/1.6T 集群设计（按约 2 年迭代推算，属推论）；448G 无源链路预算规范共识（1Q 2028）；Broadcom 第四代 CPO；Open CPX Rev 3.0 N×400G | 〔P119 p8〕〔P250 p17〕〔P433 p4〕〔P298 p12〕 |

**我的判断：**
- 12 个月内，102.4T 的出货形态以可插拔 1.6T OSFP 为主，CPO 版本晚一个季度起步；多平面两层会进入更多新建集群，三层 rail-optimized 留在存量与 NVIDIA 参考设计中。依据是 TH6/Spectrum-6/G300 系统的 GA 时间和 Meta/Microsoft/Google 的公开拓扑。
- 传输协议在 24 个月内不会收敛到一套。MRC 有生产与 OCP MSA，UET 有标准组织，MetaRoCE 有开源参考实现，Falcon 有 Google 自用，NVIDIA 和 AMD 都选择"全支持"。真正的收敛点会是 NIC 多传输可编程，而不是协议统一。
- 1.6T 代 LRO 会成为低功耗默认选项，LPO 在 1.6T 的规模部署取决于 448G/224G 主机 SerDes 的通道余量，目前没有现网数据支撑。
- OCS 进入 scale-out 主路径之前，先要完成 YANG 接口、zero-touch 验证和一致性测试；24 个月内的可见落点是园区楼间 spine 和故障备件池。
- 链路可靠性的竞争会转向遥测与诊断标准的落地速度。Oracle、Meta、Credo 的动作都指向同一件事：在 DSP 被拿掉之后，把诊断职能补回来。

**对各方的含义：**
- 设备商：102.4T 系统已普遍液冷（IceCube 约 85% 液冷，3,820 W blade）〔P407 p4, p9〕，交换机厂商要同时提供可插拔与 CPO 两版，并承担 SAI/SONiC/FBOSS 多 NOS 适配〔P404 p12〕。多平面会把交换机数量拉高、单台角色变简单，深缓冲需求集中在 scale-across 边界〔P416 p4〕。
- 光模块商：800G 及以下 LPO 有现网背书；1.6T 的低功耗卖点在 LRO；XPO 要求模块厂具备液冷、64 通道和 12.8T 级测试能力〔P441 p7〕。遥测光模块规范会成为准入条件之一〔P370 p19〕〔P408 p9〕。污染占故障 90% 意味着连接器与清洁流程的价值被低估〔P438 p11〕。
- 芯片商：交换芯片的差异点从容量转到 radix 拆分、遥测（HFT 微秒粒度）〔P405 p9〕、trimming/CSIG 支持；NIC 芯片要同时跑多套传输，功耗到 200 W 级〔P453 p8〕。

---

## 7. 推荐配图清单

| 索引 | 图中内容 |
|---|---|
| P140 p5 | radix 与两层 Clos 规模关系（800G 8,192 vs 200G 131,072） |
| P140 p14 | 8 平面 plane-per-SerDes 拓扑完整参数与 shuffler |
| P134 p10 | TH6 端口拆分与规模对应表 |
| P130 p6 | Google Virgo 两层多平面 + Apollo OCS + Jupiter |
| P122 p15 | MRC vs UEC 逐项对比表 |
| P132 p3 | UET vs MRC 快速对比 |
| P133 p13 | 75K GPU 作业 T1 交换机失效时吞吐与丢包曲线 |
| P418 p10 | Microsoft 生产集群链路抖动与 20 链路故障吞吐 |
| P296 p9 | MetaRoCE scale-out vs scale-across 的 RTT/cwnd 参数 |
| P296 p12 | MetaRoCE vs RoCEv2 集合通信完成时间 |
| P135 p11 | 四类网络拥塞信号汇总 |
| P411 p8 | Meta LPO vs retimed 中断/故障对比（8.4× 趋势） |
| P438 p7 | Oracle LPO vs FRO 纠正符号率 CDF 与 flap 比例 |
| P438 p8 | 64×800G 交换机全 FRO vs 半 LPO 功耗分布 |
| P147 p41 | Microsoft 各类光互连 pJ/bit 对照表 |
| P446 p18 | XPO 平台各模块配对 BER 箱线图 |
| P437 p6 | Meta FRO vs CPO 年链路中断率 / MTBI 表 |
| P238 p5 | 1OU 128 XPO vs 2RU 64 OSFP 前面板对比 |
| P407 p5 | IceCube 212G flyover 铜缆（总长 340 m） |
| P430 p12 | 1,000 台 OCS 插损散点 + IL 预算兼容表 |
| P136 p5 | 各类快速 OCS 技术重配置时间对比 |
| P111 p7 | 电路交换 slack 与预测误差的胜负区域 |
| P125 p8 | Meta 两平台中断来源占比 |
| P408 p15 | 衰减与 Link Health Score 对应 |
| P414 p6 | 阿里 HPN Pivot，peer 200→4 |
| P335 p2 | 四档链路功耗 15/10/6/<4 pJ/bit 与服务模型 |
| P346 p5 | SROI 四项系统需求（pJ/b、成本、FIT/flap、延迟） |
| P345 p28 | Flap-FIT × pod 规模的 MTBF 表 |
| P343 p13 | 50 次插拔灰尘下透镜 vs 物理接触 ΔIL |

---

## 8. 与 ECOC 2026 的对照

ECOC 对照文件：方向3_综合底稿.md "0. 一句话结论 + 5 条核心判断"。ECOC 方向3 偏光器件（224G/448G/lane、光源、调制器、DSP、OCS），OCP 方向2 偏网络系统。两边重合部分集中在 LPO 与 OCS。

### 8.1 一致

1. **LPO 在受控网络里更稳定、更省电。** ECOC：阿里云 13,234 只 400G DR4 LPO，日链路抖动率低 58%〔0921-Mo3-A5-阿里云 p43-p46〕；Oracle 约 35 万条 800G 链路〔0920-pm-Su3-A-03-Oracle p7〕。OCP：Meta 4k 模块中断少 2.0×〔P411 p8〕，Oracle 同一批数据〔P438 p6, p7〕。注意 Oracle 两会用的是同一组链路数（156,591/202,042），不能当作两条独立证据。
2. **1.6T 上 LRO 是当前低功耗首选。** ECOC 引 Oracle：LRO 26 dB 通道、16 W、约 10 pJ/bit〔0920-pm-Su3-A-03-Oracle p8〕；OCP 同一结论〔P438 p9〕，并有 GO 1.6T LRO <15 W、24 dB 下 BER E-13 级〔P279 p11〕和 Microsoft/Arista 实测〔P446 p14, p18〕补充。
3. **400G/lane 的瓶颈在电通道。** ECOC 称约束已转到电通道（约 90 GHz 干净带宽）〔0920-pm-Su4-A-05-NICT p6, p9〕的语境下讨论；OCP 连接器厂商的 448G 目标正是 PAM6 Nyquist 89.6 GHz、PAM4 112 GHz〔P431 p17〕〔P238 p18〕，且 Amphenol 测得 XPO-LPO 前面板 Nyquist 插损 19 dB、NPO 9 dB〔P250 p6〕。
4. **O 波段 IM/DD 超过约 2 km 受色散限制。** ECOC：224 GBd 2 km 下 IM/DD FFE 仅约 45% 波段可用〔0920-pm-Su4-A-05-NICT p6, p9〕；OCP：Google 称 400G/lane IMDD 超 2 km 受色散限制、WDM 约 16 波到顶〔T06 05:21–05:40〕，Linktel 引"速率 2× → 距离 1/4"〔P254 p3〕。
5. **OCS 已能与常规收发器共存，快速切换仍是门槛。** ECOC：KDDI 96×96 MEMS OCS + LPO 72 小时预训练，JCT 无显著影响〔0921-Mo3-A3-KDDIResearch p8, p12-p14〕，Oriole 称超快交换需配超快重锁定〔0920-pm-Su3-A-04-Oriole p9〕；OCP：Oracle/Lumentum OCS 插损中位 1.2–1.4 dB，落在 FR 4 dB 预算内〔P430 p12〕，OCS 白皮书把光模块快速锁定列为生态需求〔P136〕。

6. **InP 产能是光源的共同约束。** ECOC：Omdia 认为 InP 光源几乎不可避免，高功率激光芯片将使 InP 晶圆消耗高于预期〔0921-MF-pm-1540-Omdia p5, p11〕；OCP：Nokia 称客户要求到本十年末 InP 产能约 10×，自身新建两座 6 英寸 InP 厂〔P335 p7〕。

### 8.2 OCP 新增

1. **传输层与拓扑。** ECOC 方向3 判断中没有传输协议与多平面拓扑；OCP 给出 MRC/UET/MetaRoCE/Falcon 的设计与 75K GPU 现网故障实录〔P133 p12, p13〕〔P122 p15〕〔P296〕，以及多平面两层 Clos 的规模算式〔P140 p5〕。
2. **"中断率"取代"故障率"。** Meta 以中断率衡量光模块〔P411 p7〕，CPO 用年链路中断率与 MTBI 表达〔P437 p6〕；ECOC 侧对应的是 FIT 与链路抖动率口径。
3. **XPO 高密可插拔。** 12.8T/模块、集成液冷、MSA Release 1.0〔P238 p4〕〔P441 p4〕，ECOC 方向3 判断未涉及。
4. **遥测与诊断标准。** Enhanced Telemetry Optics v1.0〔P370 p19〕、Credo Link Health Score〔P408 p15〕、Oracle 五步观测契约〔P443 p9〕。
5. **污染是链路故障主因。** Oracle 90% / 97%〔P438 p11〕，ECOC 方向3 判断未出现。
6. **OCS 接口标准化。** YANG R1.0、Interface Spec v0.8、zero-touch 生命周期〔P421 p13〕〔P427 p14〕〔P430 p5〕。ECOC 侧是市场规模与开关速度。

### 8.3 矛盾或张力

1. **pre-FEC BER 作为可靠性证据。** ECOC 判断1 用 Oracle 中位 pre-FEC BER 1.1E-11 对 1.4E-11 支撑"LPO 更稳定"〔0920-pm-Su3-A-03-Oracle p7〕；OCP 上 Meta 用 CPO 数据说明 pre-FEC BER 单独作健康指标不可靠，CPO BER 更差但中断更少〔P437 p5〕。两者不矛盾于结论，但对指标效力的看法相反。
2. **LPO 外推到 1.6T。** ECOC 判断1 记录 Oracle 认为 1.6T LPO 难〔0920-pm-Su3-A-03-Oracle p8〕；OCP 上 Meta 把 100G/lane LPO 证据延伸到 200G/lane LRO/LPO 与 NPO〔P411 p3〕，GO 展示 1.6T LPO <10 W〔P279 p11〕。分歧在 OCP 依旧存在，且 Meta 一方没有 1.6T 现网数据。
3. **LPO 与 FRO 混用。** ECOC：阿里 LPO-FRO 混用接收灵敏度劣化，策略为纯 LPO 对 LPO〔0921-Mo3-A5-阿里云 p39, p41〕；OCP：Microsoft/Arista 实测 LPO-FRO 配对加速器侧 BER 在 1e-7 量级、可接受〔P446 p16〕，Oracle 称混合厂商时 Tx/Rx 配对方向性主导结果〔P443 p6〕。条件不同（400G DR4 现网 vs 200G/lane XPO 仿真平台），尚不能直接对比。
4. **外置光源的定位。** ECOC 判断4 把光源视为正在独立化的子系统，高功率 CW 是方向〔0921-Mo3-待定-Scintil p1〕〔0922-MF-am-1020-SourcePhotonics p18〕；OCP 上 Meta CPO 故障 83–85% 来自 ELS 模块（根因为激光驱动 SMT 元件，已修复）〔P437 p4〕，TeraHop 认为 ELSFP 多 >3 dB 损耗、需 2 倍以上激光功率，主张集成激光〔P441 p14〕。
5. **OCS 的价值所在。** ECOC 判断5 把纳秒级开关与超快重锁定作为下一门槛〔0920-pm-Su3-A-04-Oriole p9〕；OCP 的 P111 实验认为对按轮次切换而言，精度和开关速度都不是主约束，预测误差（64K GPU 434 ms）远大于 3D-MEMS dark time 20 ms〔P111 p9〕。按这一结论，scale-out 里优先补的是调度接口，不是开关速度。

---

## 附：索引对照表

| 索引 | 机构 | 题目简写 |
|---|---|---|
| P005 | TE Connectivity | 448G 500 W 级 HSIO 模块内液冷 |
| P101 | Cisco / Supermicro | L10–L12 制造测试 |
| P108 | Eridu | 高 radix 交换与精确时间 |
| P110 | Nokia / Broadcom | SONiC PTP 边界时钟 |
| P111 | ocproject.net / turbalance | 精确时间电路交换 vs 包交换 |
| P113 | Skyworks | NIC 内 PTP 与 ePPS |
| P119 | Celestica / Broadcom | Open Cluster Designs for AI 进展 |
| P121 | Alibaba / Google | SONiC 模型驱动测试 |
| P122（=P153） | Broadcom | MRC vs UEC 对比 |
| P125 | Meta | AI 集群中断归因 |
| P126 | HPE / AMD | Helios 开放标准机柜 |
| P128 | Delos Data / Eridu | 多机柜 scale-up 5000 GPU |
| P129 | Meta / Keysight | 无集群加速器验证 |
| P130 | Google | Virgo 网络与园区即计算机 |
| P132 | OpenAI / Broadcom / HPE / Arista | MRC 与 UET 面板 |
| P133 | Broadcom / OpenAI | MRC 规模化 |
| P134 | Broadcom | 端到端 AI 后端 fabric 设计 |
| P135 | Broadcom | AI 以太网拥塞控制演进 |
| P136 | Lumotive / iPronics 等 | 快速 OCS 白皮书 |
| P138 | Ciena | Scale-Across 兴起 |
| P140 | Arista / AMD | 多平面 scale-out fabric |
| P141 | Arista / Broadcom | MRC 与 SRv6 网络配置 |
| P142 | Celestica | 光集成平台 |
| P146 | Broadcom / Arista | Scale-Across 拥塞（BTS） |
| P147 | Google / Microsoft / Meta / Broadcom / Arista | Scale-across 面板 |
| P149 | Hedgehog / Celestica | 分布式推理 fabric |
| P179 | Meta | 800G AEC 大规模部署 |
| P238 | Foxconn Interconnect | XPO 液冷高密光互连 |
| P244 | Meta | 全栈开放 AI 网络 |
| P247 | Meta / Cisco | 开放 Scale-Across |
| P250 | Amphenol | 铜与光协同设计 |
| P253 | Celestica | 计算与光学的下一代 fabric |
| P254 | Linktel | 色散管理收发器 |
| P264 | Micas Networks | LPO→NPO→CPO 路线 |
| P265 | Supermicro | DCBBS 与交换机路线 |
| P266 | Arista / Jabil | 从交换机到系统 |
| P273（≈P441） | TeraHop | 开放光互连方案 |
| P279（=P321） | Genuine Optics | 硅光/NPO 全栈光互连 |
| P289 | Credo | 宽慢光学 |
| P296 | Meta / AMD | MetaRoCE |
| P298 | Samtec | 224/448G 铜与光 |
| P301 | Cornelis | Active Compute Fabric |
| P302 | HFH Thermal | 冷却演进 |
| P316 | Sumitomo Electric | 多芯光纤 |
| P318 | Cisco / Microsoft | SONiC 安全 |
| P335 | Nokia | NPO 架构技术取舍 |
| P336 | Dell | 超越铜的 scale-up 光机会 |
| P341（≈P273/P441） | TeraHop | Open CPX 集成激光光引擎 |
| P343 | Corning | 透镜连接器链路稳定性 |
| P344 | Ayar Labs / Wiwynn | 高功率 ELSFP |
| P345 | Marvell / Ranovus / Microsoft | scale-up 光可靠性与 flap 面板 |
| P346 | AMD / Lightelligence | SROI 短距光接口 |
| P363 | AMD | 主题演讲（Helios） |
| P364 | Meta | GW 级基础设施 |
| P366 | Broadcom | 开放创新扩展 AI 基础设施 |
| P367 | NVIDIA | AI 工厂（Spectrum-X） |
| P369 | Microsoft | 智能基础设施（MRC 拓扑） |
| P370 | Oracle OCI | 开放标准（光可靠性） |
| P373 | HPE | 开放 AI 方案 |
| P401 | Edgecore | 开放网络部署反馈 |
| P404 | Cisco | Silicon One 开源 NOS |
| P405 | Broadcom / Marvell | SAI 可观测性 |
| P407 | Meta | 102.4T 以太网交换机 |
| P408 | Credo | 遥测光模块标准 |
| P409 | NVIDIA / Meta | SDK + FBOSS |
| P411 | Meta | 超大规模 LPO 运营 |
| P413 | Meta / Microsoft / Alibaba | 交换机平台架构 OSPA |
| P414 | Alibaba | BGP 路由分发解耦 |
| P415 | Meta | on-prem 与云 GPU 网络 |
| P416 | Arista / Broadcom | 深缓冲 |
| P417 | Meta / Microsoft | ESUN |
| P418 | Microsoft | MRC 传输 |
| P419 | Meta | MetaRoCE 软件实现 |
| P420 | IREN 案例 | 端到端自动化 |
| P421 | iPronics / KDDI / NTT | 多厂商 OCS 互通 |
| P422 | Cisco / OpenAI | SRv6 部署 |
| P424 | Meta | BAG |
| P426 | Alibaba / Keysight | LLR/CBFC 测试 |
| P427 | Google | OCS 接口标准化 |
| P429 | Cisco / Alibaba | AI DCI-WAN 流量工程 |
| P430 | Oracle / Lumentum | Zero-Touch OCS |
| P431 | Amphenol / FIT / Luxshare / TE | 400G/lane 模块连接器 |
| P433（=P445） | Broadcom | CPO、OCI |
| P434 | Samtec | Open CPX CPO |
| P437 | Meta | 51.2T CPO 验证与 102.4T 集成光 |
| P438 | Oracle OCI | GW 级部署经验（LPO） |
| P441 | TeraHop | 开放光连接方案 |
| P443 | Oracle OCI | 线性与共封装光学运维 |
| P446 | Microsoft / Arista | XPO 系统级评估 |
| P448 | Celestica | 机柜内外互连拐点 |
| P453 | Intel / Dell | OCP NIC Gen 7 与液冷 |
| P467 | Microsoft | 400G→800G 系统集成 |
| T04 | Cisco / OpenAI / Alibaba | SRv6 视频转写 |
| T05 | Broadcom / Arista | Scale Across 拥塞视频转写 |
| T06 | Google / Meta / Microsoft / Broadcom | Scale-across 面板视频转写 |
