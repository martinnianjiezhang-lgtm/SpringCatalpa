---
title: "B80 · DAY5 · Th2-A-光通信系统安全"
tags:
  - ECOC2026
  - DAY5
---

### 0924-Th2-A1-爱丁堡大学-量子物理不可克隆函数的基础与应用.pdf
- 讲者/机构：Mina Doosti / 爱丁堡大学信息学院（p1 标 QuantERA） | 题目：Quantum Physical Unclonable Functions: Foundations and Applications | 类型：邀请报告（24 Sept 2026，理论为主）
- 方向归属（主/次）：6 QKD/量子 / 次：无（偏密码学理论，与 QKD 认证相关）
- 核心主张：
  1. 量子硬件假设（QPUF、混合锁定 PUF HLPUF 等）是量子网络的新原语，安全性介于无条件安全与预共享密钥之间。
  2. 可在多种网络架构（prepare-and-send、纠缠式、在线/离线、client-server）下做基于硬件的身份识别与认证，并可由识别协议构造消息认证。
  3. HLPUF 认证协议可与 QKD 融合，"今天即可实现"；另可实现统计安全的 bit commitment 与 coin flipping。[p36]
- 关键数据：
  - 在线协议安全性：Pr[V accept_A]=(1/2+δ·sqrt((1+4δ²)/2))^m ≈ negl(m)；图中 δ=0.01/0.04/0.07/0.1 四条曲线，m 约 20 以上 p_guess 趋近 0（插图纵轴 0–0.0015，m 至 60）[p32]
  - 离线协议：每个认证比特消耗一对 Bell 对，一轮共 m 对；P 按 PUF 输出选基测量并只公布结果、V 同基测量核对一致性；被扰动 Bell 对下仍可保持指数安全，安全界 Pr[V accept_A] ≤ (1/2 + η/2 + δη/2)^m [p30，看图核实]
  - 两个 QPUF 识别协议均"多项式轮数、指数安全"，可用不同测试算法（SWAP/GSWAP）；低资源验证者协议为经典验证+单向量子通信（Doosti 等 ACM TQC 2021；看图核实）[p21]
  - 认证决策树（Battarbee, Goswami, Kashefi, Doosti，"Authentication in Quantum Networks"，arXiv 2606.30636，2026-06-29 投稿；按无条件/永久安全、可否预共享密钥、是否信任计算/硬件假设、有无 PKI 等给出 UHF、DSS、KEM、OWF-based DSS、HPUF 等推荐，看图核实）[p19]
  - 实验：基于纠缠的 QKD 光路（泵浦整形、PPKTP、SNSPD、Alice/Bob），无具体速率/距离数字 [p33]
- 提到的公司/客户/产品/标准：AMD Versal/Spartan UltraScale+ PUF、Microchip SRAM-PUF/安全 MCU、Samsung 手机（PUF 已商用示例）；SRAM/环振/仲裁器/存储器/涂层传感 PUF；光学 PUF（随机散射、集成光子、复用材料/超表面）；QKD；NSA 对 QKD 的异议（Renner & Wolf 反驳文章）[p9–11, p18，看图核实]
- 与业界对比或记录声明：称 Dunnill & Doosti 为"首个基于量子硬件假设、互不信任设定下的协议"，首个基于硬件的 coin-flipping [p35]；Laurent-Puig 等称实验实现"完全信息论安全认证的纠缠式 QKD，无需预共享密钥" [p33]
- 推荐配图页：p33（HLPUF 消息认证→认证 QKD 流程及实验光路）；p32（在线协议安全性曲线）

### 0924-Th2-A2-AdvaNetworkSecurity-量子密钥管理系统加固措施的性能评估.pdf
- 讲者/机构：Jonas Berl（Adva Network Security GmbH / KIT，题目页下划线标注）；合作者 Mario Wenning, Helmut Grießer, Tobias Fehenberger | 题目：Performance Evaluation of Hardening Measures for Quantum Key Management Systems（p1 看图核实；德国联邦研究、技术与航天部资助） | 类型：学术论文
- 方向归属（主/次）：6 QKD/量子
- 核心主张：
  1. 在 QKMS 中用四种措施降低对可信节点的信任：秘密共享（节点不相交路径）、QKMS 层 QKD+PQC 混合、基于 PQC 的路径传递证明（PoT）、TEE 机密计算。[p3/p4]
  2. 加固措施只带来"很小的处理开销"，密钥中继时延主要由网络（NETW）决定。[p7]
  3. 加固措施可有效扩展到国家规模 QKDN。[p8]
- 关键数据：
  - 仿真：虚拟机+网络桥，Linux 内核仿真传播时延（正比于物理链路长度）；TEE 用 AMD SEV-SNP；德国拓扑 17 节点、26 链路，any-to-any 需求；接口 ETSI 014 [p5]
  - 单个 src-dst 需求（5 个 KS）时延：KS_1/1 约 3.6 ms 量级，KS_4/4 约 7.3 ms 量级（读自柱状图，为近似值）；PROC 与 PVER 占比小，NETW 占大头 [p7]
  - 单次中继时延时序图：KS_2/2 总时延约 13–14 ms 内（横轴 0–14 ms 读数，近似）[p6]
  - 可扩展性：KS 数 3/4/5 时中位延迟约 20/约 22–25/约 55–60 ms；N_key=32 时 p99 在 5 KS 约 85 ms；#KS=节点不相交路径数+1（PQC-KS）；流水线下增加 KS 不一定增加时延，负载升高时时延随密钥数线性增长（nobel-de 拓扑，kme-leipzig 到 kme-frankfurt 等）[p8，读图近似]
- 提到的公司/客户/产品/标准：ETSI GS QKD 014、AMD SEV-SNP、PQC、OpenQKD Berlin 试验床 [Gei23]、OFC 2025 Berl 等 [Ber25]、nobel-de 拓扑
- 与业界对比或记录声明：未见 SOTA/首次声明
- 推荐配图页：p4（四种加固措施的示意图：双路径秘密共享+PQC 传输+TEE）；p7（各 key share 时延分解柱状图）；p8（时延随 KS 数的可扩展性）

### 0924-Th2-A3-TelecomSudParis与Orange-50公里外破解AES的长距光纤侧信道攻击.pdf
- 讲者/机构：Victor Gérenton（另 Jaillon, Lavignotte, Patanè, Gillet, Saliou, Lepers）/ 巴黎电信学院 SAMOVAR、Mines Saint-Étienne、Orange Research Lannion | 题目：Breaking AES at 50 km: Long-Range Optical Side-Channel Attack over Fiber | 类型：学术论文
- 方向归属（主/次）：5 固定与无线接入 PON / 次：6 QKD/量子（光通信安全）
- 核心主张：
  1. 同光纤中的共供电激光可携带密码运算的功耗泄漏（光侧信道）；PON 下行机密性仅依赖 AES-128。[p2, p5]
  2. 在 50 km 光纤末端用 CPA 可恢复完整 AES-128 密钥。[p6, p9, p10]
  3. 即使密钥分发用 QKD，数据加密仍用 AES，QKD 并非解决方案。[p12]
- 关键数据：
  - 装置：Arduino Uno（ATmega328P，AES-128，时钟 16 MHz），DFB 激光器 1577 nm、+5 dBm、偏置电流 39 mA，50 km SMF 损耗 15.8 dB，接收功率 -12.8 dBm，光电二极管 DXM21AF 21 GHz，RF 前放 PA303 +30 dB，示波器 LeCroy 4 GHz/40 GS/s [p6]
  - 频谱可见 16/32/48/64/80/96 MHz 谱线（对应 16 MHz 时钟谐波）[p7]
  - CPA：256 个密钥假设按字节叠加，相关系数峰值约 0.12–0.18；16/16 字节全对，恢复密钥 0x54 0x65 0x6C 0x65 0x63 0x6F 0x6D 0x2D 0x53 0x75 0x64 0x50 0x61 0x72 0x69 0x73 [p9]
  - 成功率 vs 轨迹数（图读数近似）：背靠背约 1e4 条达 1.0；12.5 km 约 1.5e4 条达 1.0；50 km 无前放时 5e4 条仅约 0.25；50 km 加前放约 3000 条内达 1.0（约 1000 条时约 0.75）[p10]
- 提到的公司/客户/产品/标准：ITU-T G.984.3 (GPON)、G.987.3 (XG-PON)、NIST AES、1x128 分光比 PON、OLT/ONU；Kocher DPA、Brier CPA 等 [p2, p8]
- 与业界对比或记录声明：对比表列出 2002–2024 年既有光/RF 侧信道（最远 40 m，多需视距），本工作 2026 年为光纤中的光、50 km、非视距、目标 AES 密钥（Arduino+DFB）[p11]
- 推荐配图页：p10（不同距离下 CPA 成功率曲线）；p6（实验装置图）；p11（与既往侧信道工作对比表）；p13（真实 PON 下攻击场景示意）

## 本批小结
- 三篇同属 Th2-A "光通信系统安全"，共同点是"密钥/认证的信任根在哪"：A1 用量子硬件假设替代预共享密钥，A2 用 PQC+秘密共享+TEE 降低可信节点信任，A3 表明 AES 实现本身可经光纤泄漏（A1、A2、A3）。
- A3 明确指出 QKD 只解决密钥分发、不解决 AES 数据加密的侧信道，与 A1/A2 把 QKD 网络继续加固的思路形成对照（A3 p12 vs A1/A2）。
- QKD 网络实用化的趋势是"混合化"：A2 在 QKMS 层混合 QKD 与 PQC，A1 让 HLPUF 认证为 QKD 提供无需预共享密钥的认证，均为叠加而非替换（A1、A2）。
- A2 的时延数据表明中继时延以网络传播为主、加密加固处理开销小，德国 17 节点拓扑上 5 个 key share 时延约数十 ms（A2 p7–p8，读图近似）。
- A3 中前放（50 km 预放大）使所需轨迹数从 >5e4（50 km 无前放 5 万条仅约 25% 成功率）降到约 2–3e3，说明光接收灵敏度是攻击可行性的关键变量；PON 场景（OLT–1×128 分光–ONU，攻击者在分光支路窃听）仅以示意图讨论，无实测（A3 p10, p13，看图核实）。
- A1 的实验证据很少，主要是理论与综述；OCR 中的部分公式与 arXiv 编号看不清，已标注。
