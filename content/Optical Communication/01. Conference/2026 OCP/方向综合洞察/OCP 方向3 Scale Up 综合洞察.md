---
title: "OCP 方向3 Scale Up 综合洞察"
tags:
  - OCP2026
  - 综合洞察
---

# 方向3：Scale-up（机柜/超节点互连：UALink、ESUN、SUE-T、NVLink 对标、域规模、铜背板/AEC/ACC/flyover、CPO/NPO/XPO/OCI、Open CPX、scale-up 光化时间点）

> 素材：by_direction/Up.md（主归属 48 节、次归属 53 节）+ notes/R15（FTI 短距光互连 workshop，P335–P346，切分脚本因标签格式未收入 Up.md，本稿补入）。重复讲稿合并引用：P433≈P445（Broadcom CPO/OCI）、P273≈P441≈P341（TeraHop）、P279≈P321（Genuine Optics），不重复计数。
> 索引〔Pxxx pN〕；口径：自报 / 仿真 / 实验 / 现网 / 预测 / 引用（注明来源）/ 看图 / 存疑。
> 场景标注：本方向涉及 CPO/NPO 时，统一标【SO-CPO】= scale-out 交换机 CPO（交换机前面板光替换），【SU-光】= scale-up 光化（XPU↔scale-up 交换机跨柜光链路，含 XPU 侧 CPO/NPO）。两者的可靠性数据、时间点不能互相替代。

---

## 0. 一句话结论 + 5 条核心判断

**一句话结论：** OCP 2026 上 scale-up 的协议层基本收敛到"以太网 PHY + 精简头 + LLR/CBFC"（ESUN/SUE-T/UALoE，UALink 也复用 802.3dj PHY），已进入量产；物理层是"柜内铜、跨柜光"的混合期，200G/lane 下铜靠背板、flyover、ACC/AEC、CPC 撑到约 1–4 m，单柜 72–144 XPU 之外的多柜域（512–2K）要靠光；scale-up 光化的专用 PHY 是 OCI-MSA（慢而宽 NRZ、WDM、BiDi），近期形态以 NPO/XPO 为主、XPU 侧 CPO 在 2027–2028 之后；决定落地节奏的不是 pJ/bit，而是可靠性、flap 爆炸半径和可服务性。

**判断1：scale-up 域正从单柜 64–144 XPU 走向多柜 512–2K（远期 5K），但"公布域"和"单跳域"差距很大，单跳域的规模由交换芯片 radix 决定。**
- Broadcom：今天 64–144 XPU/单柜，明天 1K–2K XPU/多柜（自报/预测）〔P366 p9〕；Meta 机架演进 ORv3 HPR ≤72 → ORW（2026-Q3）≤144 → ≥256 加速器（自报）〔P437 p2〕；Microsoft/Meta 给出 scale-up GPU 数 8→72→576→1K、每 GPU 450→1200→1800 GBps〔P417 p4〕。
- Delos/Eridu 的对比表（引用 Hot Chips/GTC 2026 等，看图）：NVL72/Helios 公布域 72/单跳 72；NVL576（2027）576/72；NVL1152（2028）1,152/144；OpenAI Jalapeño 2,048/128；Microsoft Maia 200 6,144/48〔P128 p6〕。机制：大域多为两级或多级，跨机柜性能更低，需要拓扑感知放置；仿真中 petabit 交换机比 230T 交换机 GPU 利用率 88% vs 64%（仿真，引用 Turbalance）〔P128 p16〕。
- 推动力来自 MoE：路由专家数 Llama 4 128 → DeepSeek-V3 256 → Kimi K2 384 → Kimi K3 896，2028–29 预测 2k–5k（引用/预测）〔P128 p3〕；MoE 动态多播组超出传统交换机组数，集合通信退化为单播〔P117 p13〕。

**判断2：协议层向以太网收敛，ESUN/SUE-T 已从规范进入量产，UALink 在规范与管理层推进，但其 200G 版本复用以太网 PHY，AMD Helios 实际跑 UALoE（UALink over Ethernet）在 TH6 上。**
- Broadcom 自报：ESUN 175+ 成员、ESUN 机柜已量产；5+ hyperscaler 在生产中运行以太网 scale-up，10+ 伙伴在做机柜，多款 XPU 以太网 scale-up 机柜未来 6 个月量产；SUE v1.0 2026-02 发布，SUE-T 目标 2H2026〔P366 p10, p11〕。
- 现网实例：Meta Tahan（TH5 51.2T，单跳，<1 µs/跳，每加速器每方向 6.4 Tbps）部署于 MTIA300，下一代 TH6 支持 72 加速器、每方向 9.6 Tbps〔P151 p10, p11, p14〕；HPE/AMD Helios 72 GPU、12 台 TH6、每 GPU 72 条 UALoE@212G、1.8 TB/s/dir〔P126 p2, p3〕。
- 机制：ESUN 用约 4–12 B 头替代 IPv4/UDP（省 24–44 B），256B 载荷线效率 82.58%→87.07%（1.0）→89.98%（1.1 UFH_16）（看图）〔P417 p7, p11〕；LLR/CBFC 取代 PFC 实现无损、浅缓冲〔P417 p9〕〔P157 p4〕；UALink 200G 复用 IEEE 802.3dj PHY、线缆与 retimer，Consortium 只定义 DL/TL/协议层〔P428 p3〕。

**判断3：铜在柜内仍是主力且还有一代余量，但 200G/lane 下 DAC 只剩约 1 m，延伸手段（背板、flyover/CPC、ACC、AEC）各有功耗与时延代价；400G/lane 铜能否覆盖整柜取决于"从封装直接出线"。**
- 距离：IEEE DAC 目标 50G 3 m → 100G 2 m → 200G 1 m（引用 802.3cd/ck/dj）〔P308 p3〕；SROI 表：无源背板 1–1.5 m、NPC 飞线 1.4 m、CPC >1.5 m、redriver ~2 m、retimer 2.5–3 m（每级 ~50 ns），>3 m 必须用光，400G CPC-CPC ~1 m（引用 802.3dj/OIF）〔P346 p11〕。
- Broadcom 当前铜背板：72 XPU、1.04 Pbps 整柜、14.4 Tbps/XPU、26 AWG twinax 1024 根/OU、~2 m、SerDes 7 pJ/bit、整柜 ~250 kW；下一代设想 576×400G PAM6、2.08 Pbps、同样 2 m 铜（预测）〔P366 p16〕。Amphenol 估算：封装到封装 0.8 m twinax 全柜走线用 22 dB，40 dB 预算余 18 dB；经主机 PCB 出线只余 5.8 dB（估算）〔P250 p12〕。
- 延伸件分工：Ciena 1.6T ACC 3.5 m、1.5 pJ/bit/端、零附加时延 vs AEC 4.5 m、10 pJ/bit、~2×35 ns〔P308 p6〕；Meta 800G AEC 现网"数百万"互连，<12 W/端，1.0–3.2 m〔P179 p5, p6〕；Broadcom/Molex 1.6T AGERA3 AEC 6m+ 量产（自报）〔P237 p14〕。

**判断4：scale-up 光化有了专用 PHY（OCI-MSA）与开放光引擎插座（Open CPX），时间点分三层：可插拔/LPO（现在）→ NPO/XPO（2027 前后）→ XPU 侧 CPO（2027–2028 起，规模化更晚）；【SO-CPO】先于【SU-光】。**
- OCI-MSA 2026-03 成立（Meta、Microsoft、OpenAI、AMD、Broadcom、NVIDIA），GEN1 为 4λ×50G NRZ、DWDM on CWDM 栅格、BiDi，GEN2 400G 规范 2027，800G >2030（原文带问号）〔P445 p11, p12〕〔P253 p12–p13〕〔P442 p10, p12〕；Broadcom 称 Integrated OCI 7 pJ/bit/500 m，与 DAC 7 pJ/bit/2 m 同功耗，前面板 DR LRO 23 pJ/bit（自报）〔P433 p13〕。
- 分层时间：SROI 主席给出现在 LPO/RTLR、1–2 年 NPO（CPX MSA）、2–3 年以上 CPO（CPX/OCI BiDi）〔P346 p6〕；Micas：Open CPX 2027 原型、2028 早期部署，CPO 交换机 2027–2029 先增长，XPU-CPO 更晚（预测）〔P264 p9–p10〕；NVIDIA 展示 Vera Rubin Ultra NVL576 用 NVLink 7 CPO 交换托盘（看图）〔P367 p18〕，P128 引用其时间为 2027〔P128 p6〕。
- 形态分工：Astera：近期多柜 scale-up 适合 NPO，CPO 面向下一代高 radix 平台；混合 pod（柜内铜背板+柜间 NPO）对应 72–576 加速器，全光 pod 对应 >576〔P439 p11, p14〕；LightCounting（经 GO 引用，看图估读）2031 年 CPO 约 71M 端口中 scale-up 约 46M，NPO 约 89M 中 scale-up 约 37M〔P321 p5〕。

**判断5：可靠性和可服务性取代能效成为选型门槛。【SO-CPO】已有大样本现网/实验数据证明优于可插拔，但【SU-光】的门槛是"达到无源铜可靠性"，flap 爆炸半径与激光器位置是未决焦点。**
- 【SO-CPO】Meta 51.2T CPO 交换机：年链路中断率/MTBI FRO 1.22%/0.72M，CPO Phase 2 0.2%/4.5M（38,400 端口、175M 器件小时），故障 83–85% 来自 ELS 模块（激光驱动 SMT 元件，已修复）（实验）〔P437 p3, p4, p6〕。CPO 的 pre-FEC BER 更差（~9e-8 vs ~1e-9）但故障率更低〔P437 p5〕。
- 【SU-光】门槛：SROI 要求 ≤2 FIT/链路端、每 1M 器件小时 0 次 flap（可插拔 50–100 FIT）〔P346 p5〕；Marvell 估算 3M GPU、>10M 光链路时约每 48 秒一次 flap〔P345 p11〕；Microsoft：单外置激光源驱动单光引擎为 100% blast radius，CWDM 4 波长 25%〔P442 p7〕；GPU 不能像交换机那样处理 flap，1×800 模式单 lane flap 即 job abort〔P345 p30〕。
- 铜也不是零故障：Meta 铜 scale-up 每柜数千连接，99.9% 良率也有约 10 条坏链路；边缘链路仍活跃时 AllReduce 带宽降至约 55%，放弃 plane 后约 86%（看图）〔P152 p2, p7〕；Meta scale-up fabric 占 Platform-A 训练中断 24.2%（现网）〔P125 p8〕。

---

## 1. 需求与架构

### 1.1 需求数字

| 类别 | 数字与条件 | 口径 | 索引 |
|---|---|---|---|
| scale-up/scale-out 带宽比 | scale-up 约为 scale-out 的 10×；NVIDIA VR 72×200G=14.4 Tbps vs CX-9 1.6 Tbps；10–20 Tbps/xPU | 引用 NVIDIA | 〔P341 p3〕〔P441/P273 p3〕〔P134 p18〕 |
| 每 GPU scale-up 带宽 | 十年 22×（160 GB/s→3.6 TB/s，NVLink 6） | 引用 | 〔P275 p5〕 |
| 单柜带宽 | Helios scale-up 260 TB/s、scale-out 43 TB/s；Broadcom 铜背板 1.04 Pbps（下一代 2.08） | 自报/预测 | 〔P126 p2〕〔P366 p16〕 |
| 单 XPU 目标 | 光学目标每 SoC >50 Tbps/方向、<20 ns、>4 Tbps/mm²、<4 pJ/b、pre-FEC BER<1e-9、FEC 延迟 <75 ns、>20 m | 引用行业规格 | 〔P345 p7〕 |
| 1024 XPU 光 scale-up 示例 | 每 XPU 25.6 Tbps，交换机 204.8T；16 GPU 柜 + 4 交换柜；每 GPU 128 根、每交换机 1024 根 BiDi 光纤；每柜 8,192/32,768 根 | 自报设计示例 | 〔P433/P445 p14〕 |
| 1024-ASIC pod（Wiwynn/Ayar） | 每加速器 200+ Tbps scale-up、8 个片上光引擎；相对最小配置约 10× 性能 | 设计/预测 | 〔P342 p2, p7〕 |
| 光纤数 | 每计算柜 scale-up+out：VR NVL72 ~1k → Rubin Ultra NVL576 ~10k → Feynman NVL1152 ~30k → 2029+ ~45k；对应安装 9/95/280/420 h | 预测/模型 | 〔P343 p6, p9〕 |
| 铜缆数量 | 单 scale-up 柜约 5,000 根无源铜缆、约 1 MW、重量 4,000 lb → 设计 8,000 lb | 自报 | 〔P253 p15〕〔P275 p6〕 |
| 可靠性压力 | 无冗余 scale-up 中 P(fail)=1−(1−p)^N，1000+ GPU MTBF 到小时级；131,072 GPU 集群 MTBF 15 min | 自报/引用 arxiv 2410.21680 | 〔P102 p2〕〔P421 p16〕 |
| 推理需求 | Hypercast+INC 集合加速最多 2×；1 颗 320L 交换 vs 2 颗小交换 tokens/s +50%（512 并发约 1,780 vs 1,170，看图） | 自报 | 〔P117 p13〕〔P243 p9〕 |
| 认证周期 | 100G/400G 36 个月 → 800G 24 → 1.6T 18 → 下一代 9 个月 | 自报 | 〔P253 p15〕 |

### 1.2 距离/规模分层：各家口径

| 机构 | 分层（scale-up 相关） | 索引 |
|---|---|---|
| Samtec | 柜内 ~2 m、相邻柜 3–5 m、柜到柜 ~7 m、更大集群 10 m+；DAC ~2 m、ACC ~5 m、AEC ~7 m、LPO ~50 m、AOC 100 m+ | 〔P298 p2, p3〕 |
| Celestica | 224G 无源 DAC ≤1.0 m；ACC 1.2–2 m；AEC 2–5 m；LPO 2–10 m+；LRO/FRO 10–500 m | 〔P448 p6〕 |
| Astera Labs | DAC ≤3 m、ACC ≤4 m、AEC ≤7 m、AOC/LPO/NPO/CPO >50 m；pod >144 GPU 需光 | 〔P439 p8〕 |
| Eliyan | 200G：~1 m/~2 m 无源、~4 m 有源铜；400G：~2 m 有源铜、~4 m 起光；800G+ ~1 m 起即光；1k–10k GPU pod 需 10–100 m | 〔P071 p4〕 |
| SROI（AMD/Lightelligence） | SROI 区间 1–30 m；scale-up <30 m、RTT <1 µs、每 XPU ~1,000 GB/s、256 到 1,000+ XPU | 〔P346 p3, p4〕 |
| Microsoft | 前端 <2 km、Scale Out <1 km、Scale Up <50 m、Scale In <1 m（看图） | 〔P147 p43〕 |
| Avicena | scale-up 距离推理 ≤10 m、训练 ≤50 m | 〔P339 p2〕 |
| Delos/Eridu | 128 端点 1 行 ~4 m；512/576 端点 3 行 ~10 m；2048 端点 5 行 ~15 m；5120 端点 12 行 ~30 m | 〔P128 p9〕 |
| Lightmatter/Dell | ORv3 MHS Class-H 600 kW+、72–144 XPU；ORv3 Next Gen Class-V 1 MW+、1,024–1,152+ XPU | 〔P455 p11〕 |

各家对"铜到哪里为止"的说法从 1 m 到 7 m 都有，差异主要来自三点：速率代（112G/224G/448G）、是否把 ACC/AEC 算作"铜"、是否从封装直接出线。比较时要先对齐这三个条件。

### 1.3 架构演进要点

1. **单柜到多柜**：Broadcom 把多柜 scale-up 拆成"铜+光混合机柜"，形成低时延域与较高时延域，光纤时延 5 ns/m（自报）〔P366 p18, p19〕。Delos/Eridu 发起 OCP 新工作流 "Open Multi-rack Scale-up Domains"，11 月初启动〔P128 p19〕。
2. **单跳 vs 两级**：Meta Tahan 坚持单跳〔P151 p11〕；OpenAI Jalapeño 用"半扁平"两级 Clos（本地 128、全局 2048，8 个 TH6 rail，引用 Hot Chips 2026）〔P253 p6〕；Eridu 用仿真论证高 radix 单跳的尾时延收益：每多一级时延约 +10X（自报假设）〔P108 p8〕。
3. **XPU 无关的开放机柜**：Astera Orion（通用计算托盘 + PCIe 6 fabric 托盘，8→160 GPU）〔P243 p6〕；OAC 卡形态承载 PCIe Gen7/200G Ethernet/NVLink/UALink/CXL，112 lane 200 Gbps HSIO、5000 W@50V，规范 v0.9〔P465 p3, p4〕。
4. **以太网统一三层**：Broadcom 主张 scale-up/out/across 共享运维、遥测、线缆与光模块〔P366 p4–p9〕；1024 个 scale-up POD × 1024 = 1,048,576 XPU 单层 scale-out，ESUN 统一消息（概念）〔P433/P445 p15〕。
5. **前面板 I/O 成为瓶颈**：Amphenol 认为 102.4T 以后限制扩展的是面板 I/O 密度；204.8T 可用 128×1.6T OSFP 或 16×12.8T XPO〔P250 p2〕。

---

## 2. 技术路线对比

### 2.1 协议层

| 路线 | 代表方案/厂商 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| ESUN（OCP） | Meta、Microsoft 发起；Broadcom、Arista、Marvell、Cisco | 4 B 头（1.1 版 UFH 12 B）、LLR、CBFC、224G PHY；IPG 由平均 12 B 降到 1–8 B | 1.0 2026-03 发布；1.1 目标 2026-10–11；ESUN 机柜量产（Broadcom 自报） | 〔P417 p11, p12, p13〕〔P366 p10〕 |
| SUE-T（OCP） | Arista、Broadcom | 单跳可多跳、≤4k XPU、E2E RTT <2 µs；256B 线效率 85%、1KB 96%；LLR <2 mm²、6 µs 重传 <3 mm²（5 nm 估） | 规范目标 2H2026 | 〔P145 p3, p7〕〔P366 p10〕 |
| Broadcom 以太网 scale-up 交换 | Tomahawk Ultra / TH6 | 512×100G、单跳 256、250 ns、77 BPPS@64B；打包后 256B posted write 92%→98% | 量产 | 〔P366 p12, p13〕 |
| UALink | AMD、Astera、Intel、Microchip、Synopsys、Marvell | 200G 1.0（2025-04）；2.0 + Chiplet 1.0 + Mgmt 1.0（2026-04）；Compliance 1.0（4Q26）；3.0（2027）；Switch API（Apache-2.0）即将开源 | 规范推进；交换生态起步 | 〔P144 p8〕〔P428 p3, p14〕 |
| UALoE | AMD Helios（HPE、Meta 等） | 每 GPU 72 条 @212G，跑在 TH6 以太网交换上，vPod 用 VLAN 隔离 | 已部署（AMD 称 OpenAI、Meta、Anthropic、Microsoft、Oracle，看图） | 〔P126 p3, p6〕〔P363 p17〕 |
| NVLink（对标） | NVIDIA NVLink 6/7、NVLink Fusion | NVLink 6 交换托盘：3× 更低时延、10× 包速率、130 TFLOPS 网内计算（基准未注明）；NVL576 用 NVLink 7 CPO | 专有，量产 | 〔P115 p10〕〔P367 p18〕〔P286 p19〕 |
| PCIe 6 fabric | Astera Scorpio X 320L | 自称最大 PCIe 交换芯片，量产；2 柜 160 GPU 无阻塞 | 量产 | 〔P243 p6, p8〕 |

### 2.2 物理层：铜

| 路线 | 代表方案/厂商 | 关键指标 | 成熟度 | 索引 |
|---|---|---|---|---|
| 铜背板/cable cartridge | NVIDIA NVL72、Broadcom 参考 | 72 XPU、~2 m、7 pJ/bit；VR200 NVL72 铜背板 260 TB/s ≈10 kW（约占柜功耗 5%） | 量产 | 〔P366 p16〕〔P289 p7〕 |
| PHY-less + flyover | Meta Tahan、IceCube | 212G PAM4 flyover，IceCube 总 DP 长 340 m；1.5 m twinax 约 7 ns | 量产/现网 | 〔P151 p7, p11〕〔P407 p4, p5〕 |
| ACC（线性 redriver） | Ciena Nitro 2004、ACC MSA | 1.6T 3.5 m、1.5 pJ/bit/端、零附加时延；ACC MSA 2026-02-23 成立 16 家，首次 plugfest 32 条线缆 | 早期量产 | 〔P308 p6, p7〕 |
| AEC（retimer） | Meta 800G、Broadcom AGERA、Molex | 800G <12 W/端；1.6T AGERA3 6m+、>45 dB；3.2T AGERA4 2nm 即将推出 | 量产（800G 现网数百万） | 〔P179 p5〕〔P237 p14〕 |
| CPC（共封装铜） | TE、Luxshare、BizLink、Samtec | 448G：CPC @112 GHz ~7 dB vs NPC ~14 dB（仿真）；Luxshare 首批 448G cable backplane 连接器样品；Samtec 448G 共封装 PoC 演示 | 样品/PoC | 〔P461 p5, p6〕〔P462 p12〕〔P298 p13〕 |
| 信号调理器 footprint | Astera（OCP） | 8/16/24 lane，<20 dB 用 redriver，>20 dB 用 retimer/gearbox；v1.0.0 已发布 | 规范发布 | 〔P463 p3, p5, p8〕 |
| 介质波导/RF | Point2 e-Tube、AttoTude DiAx | e-Tube 自称距离 10×、成本 1/10；224G 波导 BER 2e-8；DiAx 10–30 m | 早期 | 〔P432 p4, p11, p12〕 |

### 2.3 物理层：光（标注场景）

| 路线 | 代表方案/厂商 | 关键指标 | 成熟度 | 场景 | 索引 |
|---|---|---|---|---|---|
| OCI（光 PHY） | OCI-MSA，Broadcom 首推 | GEN1 4λ×50G NRZ BiDi，Group A 1311 / B 1331 nm；7 pJ/bit @500 m | GEN1 规范发布；GEN2 2027 | 【SU-光】 | 〔P445 p11, p12, p13〕 |
| CPO 交换机 | Broadcom TH4→TH5→TH6 Davisson（2026，102.4T）→ 第4代 2028；Celestica DS6005；NVIDIA Spectrum-X/Quantum-X | Meta 51.2T：MTBI 4.5M vs FRO 0.72M；102.4T 目标比 retimed 可插拔省 60% 光功耗 | 量产早期 | 【SO-CPO】为主，NVLink 7 CPO 托盘为【SU-光】 | 〔P433 p4〕〔P437 p6, p7〕〔P435 p8〕〔P367 p18〕 |
| XPU 侧 CPO | Wiwynn+Ayar Labs（TSMC COUPE）、Lightmatter | 64 颗 CPO XPU/柜、>800 TB/s 光带宽（自报）；1024-ASIC pod 设计；OE 69.8 °C（仿真） | 演示/设计 | 【SU-光】 | 〔P248 p9, p10〕〔P342 p7, p8〕 |
| NPO / Open CPX | Open CPX MSA（Samtec、Ciena、Coherent、Marvell、Molex、TeraHop）；OIF 12.8T NPO | Type-1 6.4 Tbps/插座 32 lanes@200G；Type-2 7.2 Tbps 36 lanes；TeraHop Diablo-1 6.4T 约 5.5 pJ/b（含内置激光），ASIC→NPO 插损约 12 dB | Rev 1.0 2026-09 发布 | 两者共用；Astera/Huawei 主张用于【SU-光】 | 〔P298 p9, p10〕〔P341 p9, p11〕 |
| OPEN NPO（中国） | Huawei、Open AI Infra 社区 | Type 1 连接器 72 DP、IL ≤1.5 dB@56 GHz；Phase I 2026–27 → II 2027–28 → III（OIO）2029–30 | 首批贡献 2026-12-30 | 超节点【SU-光】 | 〔P440 p7, p14, p17〕 |
| XPO | XPO MSA（Arista 牵头）、FIT、Amphenol、TeraHop、GO | 12.8T/模块，1OU 204.8T（400G 时 409.6T）；液冷最高 500 W；12.8T XPO-FRO 约 200 W | 1.0 2026-07-31 发布，2027 生产部署（自报） | 以 scale-out 为主；Microsoft 评估用于推理 scale-up | 〔P446 p6, p7〕〔P441 p4, p7〕〔P341 p4〕 |
| 宽而慢 | Credo µLED/µVCSEL、Avicena µLED、LightX µVCSEL+MCF、Lumentum VCSEL | Credo 红光 µLED <1 pJ/bit ≤2 m；Avicena 1Tbps eKit 已出货；LightX <1.5 pJ/bit、50 m | 早期出货/样品 | 【SU-光】/scale-in | 〔P289 p5〕〔P339 p12〕〔P338 p6〕〔P444 p5〕 |
| ALC（有源光缆） | Credo ZeroFlap 1.6T ALC | 50 m、12 W/端、2027 量产；盲插光背板 30 Pb/s、1M 根光纤 | 预告 | 【SU-光】 | 〔P289 p10, p12〕 |

---

## 3. 关键数据表

### 3.1 功耗（pJ/bit，注意核算边界）

| 来源 | 方案与数值 | 边界/条件 | 口径 | 索引 |
|---|---|---|---|---|
| Broadcom | DAC 7 / Integrated OCI 7 / DR LRO 前面板 23 | 200G 链路总功耗 | 自报 | 〔P433/P445 p13〕 |
| Broadcom | 铜背板 SerDes 7 pJ/bit | 整柜 72 XPU | 自报 | 〔P366 p16〕 |
| Nokia | Retimed 可插拔 ~15；LRO ~10；LPO/NPO/CPO ~6；D2D 集成光 <4 | 按 SerDes/DSP 个数分档 | 自报 | 〔P335 p2〕 |
| Ranovus | 72 GPU pod：CPO 4、LTLR 6、RTLR 10、RTRR 15 | 100GBd PAM4 假设模型 | 仿真 | 〔P337 p3〕 |
| SROI | 每链路端 ≤5（仅光）/≤10（SerDes+光）；10 为铜转光分界；当前 CPO 4–5，DWDM CPO 3 | 需求/目标 | 自报 | 〔P346 p5, p6〕 |
| Microsoft | FRO 18–25、LRO 10–18、LPO 7–10、NPO 5–8、CPO 1–5 | 按距离分档 | 自报 | 〔P147 p41〕 |
| Ciena | ACC 1.5/端 vs AEC 10 | 1.6T 线缆 | 自报 | 〔P308 p6〕 |
| TeraHop | CPO+ELS ~6.6、NPO+ILS ~5.75、LPO ~6.4、50G NRZ ELS DWDM+RGB ~9.2、uVCSEL+RGB ~5.75、uLED+RGB ~5.95；反向 gearbox 约 3.9 | 含反向 gearbox | 看图估读 | 〔P341 p15〕 |
| Credo | 400Gb bidi SerDes ~5 vs µEmitter <2，替换 VR200 背板省 60%（每柜 6 kW、每 GPU 80 W） | 自报估算 | 自报 | 〔P289 p7〕 |
| Avicena | 现有光学 >10（含主机 SerDes >5）；µLED 目标 <1 | 目标 | 自报 | 〔P339 p5, p8〕 |
| Lightmatter | 面阵光子 <5 vs 电 15–25；互连功耗占比 ~37%→~15% | 预测 | 预测 | 〔P455 p10〕 |
| Lumentum | 每端口可插拔约 30 W → CPO 约 9 W | 示意估计 | 自报 | 〔P435 p2〕 |

读法：DAC、背板与 OCI 都在 7 pJ/bit 附近，说明 Broadcom 推 OCI 的论据是"光达到铜的功耗"，不是"光比铜省电"。宽而慢一类的低数字（<1–2 pJ/bit）多数不含主机侧反向 gearbox；TeraHop 的堆叠图把这一项算进去后，与 200G PAM4 NPO 基本持平。

### 3.2 可靠性（FIT / MTBI / flap）

| 来源 | 数据 | 场景 | 口径 | 索引 |
|---|---|---|---|---|
| Meta | ALIR/MTBI：FRO 1.22%/0.72M；CPO P1 0.47%/1.85M；CPO P2 0.2%/4.5M；排除 ELS SMT 0.04%/25M；不可服务中断 0/175M | 【SO-CPO】51.2T 交换机 | 实验 | 〔P437 p6〕 |
| Meta | 故障分类：ELS 85%/83%；FRO 光 DSP 固件 36%、瞬态/未知 37% | 【SO-CPO】 | 实验 | 〔P437 p4〕 |
| Broadcom | >1M 器件小时 0 link flap；CPO 可靠性 10× | 【SO-CPO】 | 自报，未给条件 | 〔P433/P445 p3, p4〕 |
| Lightmatter 引 Meta | 第一代机群 MTBF 8.2M 小时，约为可插拔 10× | 【SO-CPO】 | 引用 ECOC 2025/OFC 2026 | 〔P455 p9〕 |
| SROI | 目标 ≤2 FIT/链路端、0 flap/1M 器件小时；可插拔 50–100 FIT；CPO FIT 比可插拔好 5× | 【SU-光】需求 | 自报 | 〔P346 p5, p6〕 |
| Microsoft | Flap FIT 10,000 时 1024 GPU pod MTBF 0.76 h；10 Flap FIT 时 762.94 h | 【SU-光】 | 示意计算 | 〔P345 p28〕 |
| TeraHop | 硅光 PIC >100B 器件小时、FIT <0.01；折算 12.8T XPO ~2.2 FIT、6.4T NPO-ILS ~1.2 FIT | 器件 | 现网/看图 | 〔P441 p16〕〔P273 p15〕 |
| GO | >8B 器件小时，PIC FIT <0.2 | 器件 | 现网自报 | 〔P321 p10〕 |
| Credo | 铜 100M 小时 MTBF/MTBI | 铜 | 自报 | 〔P289 p4〕 |
| Meta | 铜 scale-up 99.9% 良率仍有 ~10 坏链路/柜；AllReduce 健康 93%、放弃 plane 86%、边缘链路活跃 55% | 铜 scale-up | 自报/看图 | 〔P152 p2, p7〕 |
| Meta | 线缆弯折使 |Skew| +325.6%、SCMR −44%（97% 通道退化），眼图/COM 基本不变（n=320） | 铜 cable cartridge | 实验 | 〔P102 p7〕 |
| Oracle | 90% L1 链路故障与污染相关，97% 光模块更换源于污染 | 光（scale-out） | 现网 | 〔P438 p11〕 |
| Corning | 透镜 MMC 50 次插拔不清洁 ΔIL 0.26 dB vs 物理接触 1.42 dB；部署快 89% | 光连接器 | 实验 | 〔P343 p11, p13〕 |

注意：Meta 的 CPO 优势数据都来自交换机场景（40 °C 及 15–35 °C 机房、交换机能处理 flap）。XPU 侧光链路要面对 1–2 kW ASIC 附近热环境〔P264 p11〕，且 GPU 不能像交换机那样吸收 flap〔P345 p30〕，这两点使【SO-CPO】数据不能直接外推到【SU-光】。

### 3.3 时延

| 来源 | 数据 | 口径 | 索引 |
|---|---|---|---|
| Meta Tahan | 每跳 <1 µs（store-and-forward），cut-through 再降 25%（探索中）；1.5 m twinax 约 7 ns，占路径约 1.5% | 自报 | 〔P151 p11〕 |
| Broadcom | 以太网 scale-up 交换 250 ns；光纤 5 ns/m | 自报 | 〔P366 p12, p18〕 |
| Alibaba/Keysight | LLR-09（20 m 线缆）交换转发 299–330 ns，端到端 650–710 ns，抖动 <31 ns；FEC 错误注入后应用时延 +1200 ns 以上 | 实验 | 〔P426 p12〕 |
| SUE-T | E2E RTT <2 µs | 目标 | 〔P145 p3〕 |
| SROI | 每 retimer ~50 ns；scale-up RTT <1 µs | 自报 | 〔P346 p4, p5〕 |
| Ciena | AEC ~2×35 ns，ACC 零附加 | 自报 | 〔P308 p6〕 |
| Lightmatter | 光子跳 sub-10 ns vs retimer 跳 40–120 ns | 自报 | 〔P455 p10〕 |
| UALink | 示例交换端口到端口 <200 ns（引 UALink 1.0） | 引用 | 〔P057 p10〕 |

### 3.4 规模与标准里程碑

| 项 | 时间 | 索引 |
|---|---|---|
| ESUN 宣布/成立/1.0/1.1 | 2025-10 / 2025-12 / 2026-03 / 目标 2026-10–11 | 〔P417 p13〕 |
| SUE v1.0 / SUE-T | 2026-02 / 2H2026 | 〔P366 p10〕 |
| UALink 2.0、Chiplet 1.0、Mgmt 1.0 / Compliance 1.0 / 3.0 | 2026-04 / 4Q26 / 2027 | 〔P144 p8〕 |
| OCI-MSA 成立、GEN1 发布 | 2026-03-12 | 〔P445 p11〕 |
| Open CPX MSA Rev 1.0 → 1.1 → 2.0 → 3.0 | 2026-09 → 2027-03（铜介质、Type 3）→ 2027-06（64/72×200G）→ 2027 末/2028 初（N×400G） | 〔P298 p12〕〔P441 p9〕 |
| XPO MSA Release 1.0 | 2026-07-31 | 〔P441 p4〕 |
| ACC MSA 成立 / 首次 plugfest | 2026-02-23 / 2026-08-31–09-04 | 〔P308 p7〕 |
| OPEN NPO 启动 / 首批贡献 | 2026-07 / 2026-12-30 | 〔P440 p6, p17〕 |
| SONiC 以太网 scale-up 测试开源框架 | 2026 Q4 | 〔P426 p16〕 |
| Amphenol 无源链路预算社区 | Q4 2026 范围 → 1H 2027 测量 → 1Q 2028 规范共识 | 〔P250 p17〕 |
| OCP Open Silicon Photonics for AI Systems 白皮书 1.0.x / 规范草案 | 2026-07/08 / 持续至 2027 | 〔P436 p13, p19〕〔P455 p12〕 |
| Signal Conditioner Footprint v1.0.0 | 已发布 | 〔P463 p8〕 |

---

## 4. 厂商与客户态势

### 4.1 超大规模用户

- **Meta**：scale-up 走以太网。Tahan（TH5，MTIA300）现网，下一代 TH6/72 加速器，ESUN 与 Microsoft 共同推动，Tahan 规格将贡献 OCP〔P151 p14, p15, p16〕。铜侧给出最完整的验证方法（cable cartridge 弯折、AEC 热循环、copper scale-up 统计验收）〔P102〕〔P179〕〔P152〕；光侧以 51.2T CPO 交换机 A/B 数据支撑【SO-CPO】，102.4T 集成光交换机 1.5OU、100% 液冷、16 个 ELSFP 端口〔P437 p10〕。机架 ORW 2026-Q3 ≤144 加速器〔P437 p2〕。
- **Microsoft**：ESUN 共同发起人〔P417〕；Maia 200 公布域 6,144、单跳 48（引用，看图）〔P128 p6〕；Maia 300 多 GW 部署自 2027 年开始〔P369 p9〕。光学上一边参与 OCI-MSA、强调 blast radius 与冗余标准〔P442 p6, p7〕，一边和 Arista 实测 XPO，认为推理 SoC 带宽 1–2 代内不需要更深集成，XPO 可考虑用于 scale-up〔P446 p7〕；还在 keynote 提到 FTVO scale-up 光学规范〔P369 p14–p27〕（细节文字层未见）。
- **OpenAI**：Jalapeño 本地 128、全局 2048 两级 Clos，基于 TH6（引用 Hot Chips 2026）〔P253 p6〕；OCI-MSA 创始成员〔P366 p20〕。
- **Google**：在本方向材料中出现较少，ICI 多 TB/s 环面 + Palomar MEMS OCS〔P376 p6〕；V7 pod 144 柜 × 96 ICI 光口 = 13,824 根光纤接 48 台 OCS（引用）〔P345 p8〕。Google 是 UALink Management WG 联合主席所属机构〔P428 p15〕。
- **Alibaba**：自研以太网 scale-up 交换机，与 Keysight 完成 LLR/CBFC 22 个用例并推 SONiC 测试标准〔P426 p11, p16〕；另提出把 PCM 持久内存挂到 UALink scale-up fabric（预测）〔P057 p11, p12〕。
- **Oracle**：现网数据偏 scale-out，但两点影响 scale-up 光化：污染占 90% 链路故障、扩束连接器插拔力约降 20× 可做光背板〔P438 p11, p12〕；DSP 消失后要保留观测职能〔P443 p4〕。
- **中国互联网/运营商**：据 Huawei，NPO 已被中国互联网企业、运营商和系统厂商广泛选为超节点光互连主方案〔P440 p4〕（自报，未列名）。

### 4.2 芯片/系统/光器件厂商站位

- **Broadcom**：以太网 scale-up 全栈（TH6/TH Ultra、ESUN/SUE-T），铜背板 → OCI 光 → CPO 第 4 代（2028）〔P366〕〔P433/P445〕。立场最清晰：scale-up 用以太网，跨柜用 OCI 集成光。
- **NVIDIA**：NVLink 6/7 专有路线，NVL576 CPO 交换托盘〔P367 p18〕；NVLink Fusion 对外开放给 d-Matrix 等〔P286 p19〕；OCI-MSA 创始成员；Spectrum-6 支持 CPO〔P409 p6〕。
- **AMD**：Helios 72 GPU，UALoE 跑在以太网交换上〔P126〕〔P140 p10〕；UALink Consortium 主席所属〔P144〕；SROI 工作流共同主席〔P346〕；OAC 规范作者〔P465〕。
- **Astera Labs**：同时押 PCIe（Scorpio 320L）、UALink/ESUN；主张近期多柜用 NPO〔P439〕；做 OCP 信号调理器 footprint〔P463〕；关注 scale-up pod 安全的"组合"边界〔P047〕。
- **Marvell**：UALink Switch API 主力〔P428〕；Open CPX 成员；RELIANT 遥测、flap 估算〔P345〕。
- **Celestica / Wiwynn / Micas**：系统厂。Celestica DS6005（TH6 Davisson CPO，贡献 OCP）〔P142 p9〕〔P253 p18〕；Wiwynn 与 Ayar Labs 做 XPU CPO 机柜、ELSFP 热设计〔P248〕〔P342〕〔P344〕；Micas 给出最保守的时间表〔P264〕。
- **连接器/线缆厂**（Amphenol、Molex、TE、Luxshare、BizLink、Samtec、FIT）：普遍在推 CPC/NPC、448G 线缆、Open CPX 插座、XPO 连接器。Molex 主张用共用 footprint 让 NPO/NPC 选择后移〔P305 p12, p16〕；Samtec 同一插座承载铜（scale-up）与光（scale-out）〔P298 p4〕。
- **光器件厂**：TeraHop 主推 ILS（集成激光）NPO〔P441 p14〕；Lumentum、Ayar Labs、Quintessent 主推高功率 ELS/ELSFP 与梳状光源〔P435〕〔P344〕〔P340〕；Nokia 中立，认为引擎移出主机热区后片上激光重新可行〔P335 p8〕；GO 认为 NPO 是近期甜点〔P321 p16〕。
- **新路线公司**：Credo（µLED、ALC，发起 OCP SRMO 工作流）〔P289 p14〕；Avicena、LightX（µLED/µVCSEL）；Point2、AttoTude（介质波导）〔P432〕。

### 4.3 OCP 标准/MSA/工作组进展

OCP 侧：ESUN（1.0 已发布）、SUE-T WG、SROI 工作流（白皮书 + Appendix A）、Open Silicon Photonics for AI Systems（MHS 托盘契约）、Open Multi-rack Scale-up Domains（新）、SRMO（新）、Signal Conditioner Footprint、OAC、Optics Reliability workstream、SONiC Scale-Up WG〔P417〕〔P145〕〔P346〕〔P436〕〔P128 p19〕〔P289 p14〕〔P463〕〔P465〕〔P443 p11〕〔P157〕。
OCP 外：UALink Consortium、OCI-MSA、Open CPX MSA、XPO MSA、ACC MSA、SDM4 MCF MSA、OIF（12.8T NPO、ELSFP、CEI-448G、CEI-224G-Linear）、IEEE 802.3dj/dv、UEC（LLR/CBFC 定义方）、Open AI Infra 社区 OPEN NPO。
OCP 开幕致辞把 ESUN、SUE-T、MRC 列为 2026 年网络规范发布成果〔P362 p8〕。

---

## 5. 分歧与未决问题

| 问题 | 观点与持有者 | 证据 | 未决原因 |
|---|---|---|---|
| 以太网 vs UALink vs NVLink | Broadcom/Meta/Microsoft：以太网统一（ESUN/SUE-T）；UALink：开放、"Any Accelerator/Switch"；NVIDIA：NVLink 专有 + Fusion 对外 | 〔P366 p11〕〔P144 p5〕〔P367 p18〕 | UALink 200G 复用以太网 PHY〔P428 p3〕，AMD 自己用 UALoE〔P126〕，两者边界在协议层而非线缆层；UALink 交换芯片量产数据本届未见 |
| 单跳 vs 多级大域 | Meta/Eridu：单跳、高 radix；OpenAI/NVIDIA：两级扩大公布域 | 〔P151 p11〕〔P128 p6, p16〕〔P253 p6〕 | petabit 交换机仍是目标而非产品〔P128〕；两级对推理 MoE 的实际影响缺现网数据 |
| 400G/lane 铜还能走多远 | Broadcom：576×400G PAM6 仍 2 m 铜；Amphenol：从封装出线可覆盖整柜甚至两柜；Dell/SROI：400G 无源铜 <1 m、CPC-CPC ~1 m | 〔P366 p16〕〔P250 p12〕〔P336 p3〕〔P346 p11〕 | 前两者是"封装出线"前提，后两者是传统通道；448G PAM4 还是 PAM6、92 Ω 还是 85 Ω 未定〔P431 p28〕 |
| 光引擎形态：CPO / NPO / XPO | Broadcom：OCI 集成光/CPO，行业收敛到单一形态才有规模；Astera、Huawei、GO：NPO 优先；Microsoft：XPO 低 blast radius、可服务；Micas：2028–2030 三者共存 | 〔P445 p16〕〔P439 p11〕〔P440 p4〕〔P446 p7〕〔P264 p3〕 | XPU 代际 12–18 个月〔P346 p2〕、认证周期缩到 9 个月〔P253 p15〕，CPO 的封装绑定与换代节奏冲突；XPO 在 scale-up 只有仿真盒实测 |
| 激光器位置 ILS vs ELS | TeraHop：ILS，ELSFP 多 >3 dB、激光功耗约 4×；Lumentum/Ayar：高功率 ELSFP 可服务、热隔离；Nokia：最终看量产；Ranovus：ELS 与 OE 1:1 降爆炸半径 | 〔P441 p14〕〔P435 p4〕〔P344 p4〕〔P335 p8〕〔P337 p9〕 | Meta CPO 故障 83–85% 在 ELS，但根因是 SMT 元件已修复〔P437 p4〕；ILS 在 1–2 kW ASIC 旁的寿命数据缺 |
| 慢而宽 vs 200G PAM4 | OCI GEN1 4×50G NRZ；Credo/Avicena/LightX：µLED/µVCSEL <1–2 pJ/bit；TeraHop：反向 gearbox 吃掉优势；Ranovus：OCI G1 BiDi4 只适合 CPO 或需 gearbox | 〔P445 p12〕〔P289 p5〕〔P339 p8〕〔P341 p15〕〔P337 p8〕 | 宽而慢需要 XPU 原生宽接口才能省掉 gearbox；光纤数增 4×〔P441 p19〕；现网可靠性数据缺 |
| 健康指标：pre-FEC BER | Meta：CPO pre-FEC BER 更差（~9e-8）但故障更少，BER 单独不可靠；Ranovus/Marvell：scale-up 弱 FEC 需 pre-FEC BER <1e-9、关注突发误码 | 〔P437 p5〕〔P345 p7, p22〕 | 低时延 FEC 下的突发误码统计缺标准测试方法 |
| 铜的"可靠"是否被高估 | Credo/Marvell：光要达到铜的可靠性；Meta：铜 scale-up 每柜约 10 条坏链路、边缘链路拖垮带宽；scale-up fabric 占中断 24.2% | 〔P289 p4〕〔P345 p7〕〔P152 p2, p7〕〔P125 p8〕 | 铜的问题多在插接/线束/固件（AEC 固件竞态〔P179 p8〕），统计口径与光的 FIT 不同 |
| 每 XPU 带宽是否需要深集成 | Microsoft：推理负载 1–2 代内不需要；Lightmatter：面阵光 I/O 才能突破周边逃逸（CPO 3.6×、APO 46×，引用白皮书） | 〔P446 p7〕〔P455 p2〕 | 取决于训练/推理负载占比与 HBM 占边缘的程度 |

---

## 6. 判断与时间线（12–36 个月）

| 时间 | 里程碑 | 依据 |
|---|---|---|
| 2026 Q4 | ESUN 1.1（UFH、IPG 缩减）；SUE-T 规范；UALink Compliance 1.0；SONiC scale-up 测试框架开源；OPEN NPO 首批贡献；Open Multi-rack Scale-up Domains 启动；UALink Switch API 上 GitHub | 〔P417 p13〕〔P366 p10〕〔P144 p8〕〔P426 p16〕〔P440 p17〕〔P128 p19〕〔P428 p14〕 |
| 2026–2027 | 多款定制/商用 XPU 以太网 scale-up 机柜量产（Broadcom 称未来 6 个月）；Meta ORW ≤144 加速器；Helios 部署扩大 | 〔P366 p11〕〔P437 p2〕〔P363 p17〕 |
| 2027 | OCI GEN2（400G）规范；Open CPX Rev 1.1/2.0；XPO 与 Open CPX 生产部署（TeraHop 自报）；Credo 1.6T ALC 量产；UALink 3.0；NVL576（NVLink 7 CPO）；Maia 300 多 GW 部署开始 | 〔P253 p13〕〔P441 p9〕〔P341 p4〕〔P289 p10〕〔P144 p8〕〔P128 p6〕〔P369 p9〕 |
| 2027–2028 | Open CPX 早期部署、CPO 交换机增长期；OPEN NPO Phase II（1000+ radix）；L1↔L2 交换机间 NPO（场景 1）；LPO/NPO/CPO 出货进入快速增长 | 〔P264 p9–p10〕〔P440 p7, p16〕〔P321 p5〕 |
| 2028 | NVL1152（公布域 1,152，单跳 144）；Broadcom 第 4 代 CPO；Open CPX 3.0（N×400G）；无源互连 448G 规范共识；Meta ≥256 加速器机柜 | 〔P128 p6〕〔P433 p4〕〔P441 p9〕〔P250 p17〕〔P437 p2〕 |
| 2028–2030 | XPU 经 NPO 直接出光的大扁平 POD；Credo 3.2T ALC / 6.4T NPO；Open NPO OIO 光接口；OCI 800G（>2030，存疑） | 〔P440 p16〕〔P289 p11〕〔P440 p7〕〔P442 p10〕 |

**本稿的时间点判断：** 【SO-CPO】在 2026–2027 年进入早期量产（TH6 Davisson、Meta 102.4T、Spectrum-X/Quantum-X）；【SU-光】的第一波是 2027 年前后的跨柜 NPO/XPO/ALC 和 NVIDIA 自家 NVLink CPO 托盘，开放生态（OCI + Open CPX）的 XPU 侧 CPO 规模部署更可能落在 2028 年以后。依据是各 MSA 的规范节奏（Open CPX 2.0 在 2027-06、OCI GEN2 在 2027）和 Micas、SROI 两份最具体的分层判断〔P264 p10〕〔P346 p6〕。单柜 72–144 XPU 在 200G/400G 两代内仍以铜为主〔P366 p16〕〔P439 p7〕。

**对各类厂商的含义：**
- **设备商（交换机/系统）**：scale-up 交换芯片的 radix 和单跳规模是差异点〔P128〕〔P117〕；系统集成的难点转向机柜级（线缆盒、光纤 8,192 根/柜预布线、液冷）〔P407 p12〕〔P124 p3〕；要准备同时交付铜背板机柜与光互连机柜两类 SKU。
- **光模块/光引擎商**：scale-up 不是 scale-out 光模块的放大版，指标换成 lane 密度、pJ/bit、每 lane 成本、FIT，衰减/色散/DSP 不再是重点〔P346 p3〕；竞争在 Open CPX 插座、XPO 与 OCI 光 PHY 三处；可靠性数据（器件小时、FIT、flap）是进入门槛〔P441 p16〕。成本目标对标 AEC，与无源铜约 \$0.05/Gbit 仍差约 10×〔P346 p5〕。
- **铜缆/连接器商**：200G/400G 两代仍有增量（AEC 1.6T 2030 年 8.85M 件，引用 LightCounting〔P237 p6〕；ACC 有源线缆占比 2028 约 27%，看图〔P308 p5〕），但价值从线缆转向 CPC/NPC 连接器与封装出线；ACC 与 AEC 的分界取决于是否需要 >20 dB 补偿〔P463 p5〕。
- **芯片商（XPU/SerDes）**：XPU I/O 方案要同时支持 UALink/ESUN/私有协议的 I/O chiplet（如 Cadence 224G x32 可配 UALink/Ethernet〔P068 p9〕）；若走慢而宽，需原生宽接口以免反向 gearbox；GPU 侧需要 lane 级 flap 故障域隔离（4×200 降级而非 job abort）〔P345 p30〕。

---

## 7. 推荐配图清单

| 索引 | 图中内容 |
|---|---|
| P128 p6 | 各家公布 scale-up 域 vs 单跳域（NVL72/576/1152、Jalapeño、Maia 200） |
| P128 p12 | 5120 端点 12 行布局，最长约 30 m 光纤 |
| P366 p16 | Broadcom 铜背板当前代 1.04 Pbps 与下一代 2.08 Pbps 参数对比 |
| P433 p13（=P445 p13） | DAC / Integrated OCI / DR LRO 的 200G 功耗-距离对比 |
| P433 p14 | 1024 XPU 光 scale-up 集群光纤计数表 |
| P417 p11 | ESUN/UFH 头结构与 wire efficiency 对比 |
| P151 p10 / p14 | Meta Tahan 16 加速器×4 交换机拓扑；下一代 72 加速器拓扑 |
| P126 p3 | Helios 72 GPU + 12 台 TH6 的 UALoE 连接图 |
| P308 p6 | ACC vs AEC 对比表（距离、pJ/bit、时延、电源轨） |
| P250 p12 | 封装出线铜通道 22/40 dB 预算链 |
| P346 p6 / p11 | 可插拔/NPO/CPO 三层部署表；铜距离表（背板、NPC、CPC、redriver、retimer） |
| P437 p6 | Meta FRO vs CPO 年链路中断率/MTBI 表【SO-CPO】 |
| P442 p7 | 四种激光/波长冗余方式的 blast radius 对比 |
| P345 p28 | Flap-FIT × pod 规模的 MTBF 表 |
| P152 p7 | 铜 scale-up AllReduce 带宽：健康 / 放弃 plane / 边缘链路三条曲线 |
| P264 p10 | 2026–2029 NPO/CPO/XPO/OCI 展望表 |
| P441 p9 | Open CPX MSA 规范路线（Rev 1.0→3.0） |
| P341 p15 | 7 种光学方案 pJ/b 分项堆叠（含反向 gearbox） |
| P439 p14 | 混合铜光 pod（72–576）vs 全光 pod（>576） |
| P455 p2 | 封装逃逸带宽几何对比（铜 26 / CPO 93.6 / APO 1,191 Tb/s/dir） |
| P343 p9 | 每机柜光纤数与安装工时随 GPU 代际增长 |
| P321 p5 | LightCounting NPO/CPO 按 scale-out/scale-up 拆分出货预测 |

---

## 8. 与 ECOC 2026 的对照

ECOC 对照文件：方向4_综合底稿（Scale-up/in：CPO/NPO/XPO、WSE、OCS）"0. 一句话结论+判断"部分。

### 8.1 一致之处

1. **形态时间线**：ECOC 记 Ciena 判断 CPO scale-out 约 2026、scale-up 2027/28〔0920-pm-Su3-I-05-Ciena p10〕，XPO 量产模块预计 2027Q1〔0921-Mo4-待定-Arista p24〕。OCP 上 SROI（1–2 年 NPO、2–3 年以上 CPO）〔P346 p6〕、Micas（CPO 交换机先、XPU-CPO 更晚）〔P264 p9–p10〕与 TeraHop（XPO、Open CPX 2027 年内生产部署）〔P341 p4〕给出相同顺序。
2. **pJ/bit 差距来自 SerDes/DSP 个数与核算边界**：ECOC 记 Meta"链路功耗主要取决于 SerDes 个数"〔0920-am-Su1-B-01-Meta p1〕、Coherent 要求统一核算边界〔0920-pm-Su4-I-04-Coherent p5〕；OCP 上 Nokia 直接按 SerDes/DSP 个数分档 15/10/6/<4〔P335 p2〕，TeraHop 把反向 gearbox（约 3.9 pJ/b）算进宽而慢方案〔P341 p15〕。
3. **可靠性与连接器是决定性约束**：ECOC 记 Oracle >90% 链路故障、97% 收发器更换源于连接器污染〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p38〕；OCP 上 Oracle 给出同样的 90%/97%〔P438 p11〕，Corning 透镜 MMC 给出抗尘数据〔P343 p13〕。
4. **铜的边界在 1–2 m（200G），铜+光混合持续**：ECOC〔0920-am-Su1-B-02-OpenAI p4〕〔0921-Mo12-A3-Ciena p18、p33〕；OCP〔P308 p3〕〔P346 p11〕〔P439 p7〕〔P336 p4〕。
5. **介质波导作为第三条路**：ECOC AttoTude 介质波导 448G 约 10 m〔0920-am-Su1-B-06-AttoTude p6〕；OCP Point2 e-Tube 与 AttoTude DiAx 10–30 m〔P432 p11〕。
6. **宽而慢缺现场数据**：ECOC 记 Lumentum 1060 nm VCSEL 115 °C、Tj 181 °C、5000 h〔We5-I Lumentum p13、p15〕，OpenAI 称需要现场验证〔0920-pm-Su4-I-02-OpenAI p11〕；OCP 上 Lumentum 给出相同 HTOL 条件〔P444 p2〕，宽而慢方案仍只有 POC 与早期出货〔P444 p5〕〔P339 p12〕。

### 8.2 OCP 新增

1. **协议层**：ECOC 方向4 判断中没有 scale-up 协议内容；OCP 上 ESUN 1.0/1.1、SUE-T、UALink 2.0/Switch API、LLR/CBFC 实测、UALoE 是主线〔P417〕〔P145〕〔P428〕〔P426〕〔P126〕。
2. **域规模的"公布域 vs 单跳域"拆分**与多机柜布局距离（4 m → 30 m）〔P128 p6, p9〕，ECOC 只有 72 → 576+ XPU 的笼统表述〔0920-pm-Su3-I-05-Ciena p10〕。
3. **OCI-MSA 与 Open CPX 的规范细节与路线**（GEN1 4λ×50G NRZ BiDi、Group A/B 波长；Open CPX Rev 1.0→3.0），以及中国 OPEN NPO 的连接器规范〔P445 p11, p12〕〔P441 p9〕〔P440 p13, p14〕。ECOC 只记到 Open CPX 1.0 发布〔0920-am-Su2-A-01-UBC p4〕。
4. **【SO-CPO】大样本可靠性数据**：Meta 51.2T CPO 38,400 端口、175M 器件小时、MTBI 4.5M vs 0.72M〔P437 p3, p6〕。
5. **铜侧工程化**：ACC MSA 与 plugfest、AEC 现网数百万、copper scale-up 统计验收方法、信号调理器 footprint 标准〔P308 p7〕〔P179 p6〕〔P152〕〔P463〕。
6. **flap 与爆炸半径的系统级分析**：Flap-FIT × pod MTBF、lane 分故障域、激光共享的 blast radius〔P345 p28, p32〕〔P442 p7〕。

### 8.3 矛盾或口径不一致

1. **铜距离**：ECOC 记 Marvell 200G 2.5 m、400G 1.25 m〔0920-pm-Su4-H-04-Marvell p5〕；OCP 上 IEEE 200G DAC 目标 1 m〔P308 p3〕、Dell 400G <1 m〔P336 p3〕，而 Broadcom 设想 400G PAM6 仍用 2 m 铜背板〔P366 p16〕。差异来自是否计入 CPC/有源件，需对齐条件后再比较。
2. **宽而慢能效**：ECOC 记 Coherent 2D VCSEL NPO 1.2 pJ/bit〔0923-MF-00-Marvell与Ciena与Arista与Oracle连拍 p51〕；OCP 上 TeraHop 堆叠图中 uVCSEL+RGB 约 5.75 pJ/b〔P341 p15〕，Credo、LightX 自报 <2、<1.5 pJ/bit〔P289 p5〕〔P338 p6〕。数字差 3–5 倍，主因仍是边界（是否含反向 gearbox、主机 SerDes）。
3. **scale-up CPO 时间点**：ECOC 记 2027/28〔0920-pm-Su3-I-05-Ciena p10〕；OCP 上 NVIDIA NVL576 NVLink 7 CPO 被引为 2027〔P128 p6〕〔P367 p18〕，SROI 说 CPO 要 2–3 年以上〔P346 p6〕，Micas 说 XPU-CPO 晚于 2027–2029 的交换机 CPO〔P264 p10〕。专有生态（NVIDIA）与开放生态（OCI/Open CPX）的时间点可能相差一年以上。
4. **OCS 在 scale-up 中的位置**：ECOC 把 OCS 列为 scale-up 的下一层变量〔0920-am-Su2-I-01-NVIDIA p18〕〔0920-pm-Su3-A-04-Oriole p9〕；OCP 上 scale-up OCS 只出现在 Google V7 的引用〔P345 p8〕，OCS 讨论集中在 scale-out（OAI、快速 OCS 白皮书）〔P421〕〔P136〕。
5. **pre-FEC BER 作为指标**：ECOC 方向4 判断未涉及；OCP 内部即有冲突，Meta 认为 pre-FEC BER 单独不可靠〔P437 p5〕，Marvell/Ranovus 把 pre-FEC BER <1e-9 列为 scale-up 光学目标〔P345 p7, p22〕。
6. **XPO 定位**：ECOC 把 XPO 与 NPO 并列为 224G 世代 scale-up 落地主形态〔0921-Mo4-待定-Arista p24〕；OCP 上 XPO 讲稿多以交换机前面板（scale-out）为主〔P441〕〔P238〕，只有 Microsoft 明确提出 XPO 可用于推理 scale-up，而且依据是仿真盒实测〔P446 p7, p9〕。

---

## 索引对照表

| 索引 | 机构 | 题目简写 |
|---|---|---|
| P047 | Astera Labs | Scale-up 网络安全（链路到 pod） |
| P057 | Alibaba Cloud | 字节寻址持久内存 / UALink |
| P068 | Arm、Cadence | chiplet 互通（224G I/O chiplet） |
| P071 | Eliyan | 光 chiplet 的 D2D |
| P102 | Meta | 高速 cable cartridge 系统验证 |
| P108 | Eridu | 高 radix 交换与精确时间 |
| P115 | NVIDIA | AI Tokenomics |
| P117 | Astera Labs | Bring Your Own XPU 开放机柜 |
| P124 | Arista、Jabil | 高功率液冷网络机架集成 |
| P125 | Meta | 训练作业中断归因 |
| P126 | HPE、AMD | 开放标准 AI 机柜（Helios） |
| P128 | Delos Data、Eridu | 5000 GPU 多机柜 scale-up 域 |
| P134 | Broadcom | 端到端 AI 后端 fabric |
| P136 | Lumotive、iPronics 等 | 快速 OCS 白皮书 |
| P137 | Astera Labs | In-Network Compute 推理 |
| P140 | Arista、AMD | 多平面 scale-out |
| P142 | Celestica | 光集成平台（DS6005） |
| P144 | UALink Consortium 面板 | UALink 生态 |
| P145 | Arista、Broadcom | SUE-T |
| P147 | Google/Microsoft/Meta/Broadcom | Scale-across 面板 |
| P151 | Meta | Tahan 以太网 scale-up 交换机 |
| P152 | Meta | 铜 scale-up 域测试方法 |
| P156 | Meta、AMD | 机柜级统一遥测 |
| P157 | Keysight、Meta | ESUN 验证方法 |
| P179 | Meta | 800G AEC 大规模部署 |
| P237 | Molex、Broadcom | 224G AEC |
| P238 | Foxconn Interconnect | 液冷 XPO |
| P243 | Astera Labs | xPU 无关机柜架构（Orion） |
| P248 | Wiwynn | AI 工厂基础设施挑战（CPO 机柜） |
| P250 | Amphenol | 铜与光互连协同设计 |
| P253 | Celestica | 计算遇见光学（含 OpenAI/Broadcom 页） |
| P264 | Micas Networks | LPO→NPO→CPO 开放光路线 |
| P273 / P441 / P341 | TeraHop | 开放光互连（XPO/Open CPX/SDM4）；Open CPX 集成激光引擎 |
| P275 | Hyve Solutions | 模块化机柜级 AI 基础设施 |
| P286 | d-Matrix | 推理之路 |
| P289 | Credo | Wider. Slower. Better |
| P298 | Samtec | 224/448G 铜与光 |
| P305 | Molex | 开放近封装生态 |
| P308 | Ciena | ACC 延伸铜 |
| P313 | BizLink | 448G 高速互连 |
| P321 / P279 | Genuine Optics | NPO 在全栈光互连中的作用 |
| P335 | Nokia | NPO 架构技术选择 |
| P336 | Dell | 超越铜：scale-up 光机会 |
| P337 | Ranovus | 高密度可靠低功耗互连 |
| P338 | LightXcelerate | µVCSEL 阵列 + MCF |
| P339 | Avicena | µLED 互连 |
| P340 | Quintessent | 量子点光源 |
| P342 | Wiwynn、Ayar Labs | CPO 光 scale-up 机柜 |
| P343 | Corning | 扩束透镜连接器 |
| P344 | Ayar Labs、Wiwynn | 高功率 ELSFP |
| P345 | Marvell、Ranovus、Microsoft 面板 | scale-up 光可靠性与 flap |
| P346 | AMD、Lightelligence（SROI 主席） | scale-up 短距光接口 |
| P362 | OCP 基金会 | 开幕致辞 |
| P363 | AMD | 下一代 AI 基础设施（Helios/Helion） |
| P366 | Broadcom | 开放创新扩展 AI 基础设施 |
| P367 | NVIDIA | AI 工厂规模化（MGX 1.2、NVL576 CPO） |
| P369 | Microsoft | Intelligent Infrastructure |
| P376 | Google | Intelligence Infrastructure |
| P407 | Meta | 102.4T 以太网交换机 |
| P409 | NVIDIA、Meta | NVIDIA SDK + FBOSS |
| P417 | Meta、Microsoft | ESUN |
| P421 | iPronics、KDDI、NTT | 多厂商 OCS 互通 |
| P426 | Alibaba、Keysight | LLR/CBFC 验证 |
| P428 | Marvell、AMD | UALink Switch API |
| P431 | Amphenol/FIT/Luxshare/TE | 400G/lane 模块连接器闪电演讲 |
| P432 | Point2、AttoTude | 替代型可扩展互连 |
| P433 / P445 | Broadcom | CPO、OCI / Standards and Future Technologies |
| P434 | Samtec | OpenCPX CPO 方案 |
| P435 | Lumentum | 外置光源架构 |
| P436 | Flex、Lightmatter | 开放硅光参考设计 |
| P437 | Meta | 51.2T CPO 验证到 102.4T 集成光交换机 |
| P438 | Oracle | GW 级部署经验 |
| P439 | Astera Labs | NPO/CPO scale-up fabric |
| P440 | Huawei | OPEN NPO 标准 |
| P442 | Microsoft | 光 scale-up 架构、标准与韧性 |
| P443 | Oracle | 消失的 DSP |
| P444 | Lumentum | 慢而宽 12.8T VCSEL |
| P446 | Microsoft、Arista | XPO 系统级评估 |
| P448 | Celestica | 柜内与多柜 scale-up 互连拐点 |
| P455 | Lightmatter、Dell | 开放硅光扩展 MHS 平台契约 |
| P461 | TE Connectivity | 448G 共封装铜 |
| P462 | Luxshare-Tech | 400G 电互连铜创新 |
| P463 | Astera Labs | OCP AI 信号调理器标准 footprint |
| P465 | AMD、Intel | Open Adapter Card |
