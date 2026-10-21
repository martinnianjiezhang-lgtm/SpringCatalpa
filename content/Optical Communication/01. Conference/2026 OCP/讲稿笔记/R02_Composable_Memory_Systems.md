---
title: "R02_Composable_Memory_Systems"
tags:
  - OCP2026
  - 讲稿笔记
---

# R02 笔记：Server：Composable Memory Systems (CMS)；Security

---

### P045 Confidential Storage
- 讲者/机构：Srini Narayanamurthy，Staff Engineer，Google [p1] | 类型：技术分享
- 方向归属（主/次）：主 [安全]；次 [存储]、[In 封装内：CXL/内存池化]（PCIe/CXL IDE 链路加密）
- 核心主张：
  1. Confidential Computing 只保护使用中的数据，数据一落盘就离开信任边界；Confidential Storage 让"信任跟随数据到介质"[p3, p16]。
  2. 用现有标准拼出端到端方案：CPU 侧 TDX/SEV-TIO/CCA，设备 DMTF SPDM+DOE，链路 PCIe/CXL IDE，设备分配 PCI-SIG TDISP，存储隔离 NVMe namespace，持久加密 TCG Opal/MEK-MPA，硬件身份 Caliptra+TCG DICE，舰队密钥运维 OCP L.O.C.K. [p53]。
  3. 信任不是一次性事件：设备在固件更新、故障、重新分配全过程中持续重新证明，退役时以 crypto-erase 结束 [p29–p33]。
- 关键数据：
  - 无量化性能数据。对比表 [p41]（自报）：SED、主机加密、CSP 托管密钥三种方案在"防云运营者 / 对 hypervisor 隐藏明文 / 设备身份向租户证明"三项均为 No，Confidential Storage 全部 Yes。
  - 替代方案对比 [p42]（自报）：同态加密开销"Very high、操作受限"；MPC "High、带宽受限"；TEE "Near-native、任意负载"。
  - 威胁模型 [p7–p10]：在范围内为恶意/被攻陷的运营者、hypervisor、fabric；不含侵入式芯片攻击与物理开封。
  - 会话建立 7 步流程 [p35–p39]：请求可信设备→TDISP 建 TDI→SPDM 认证/密钥交换→证明证据→IDE 流→客户托管密钥→云托管密钥；介质加解密由 AES-XTS IP 线速完成 [p39]。
  - AI 场景 [p46–p49]：受监管 MRI 数据集训练，每小时 checkpoint 与 optimizer state 经 IDE 写入 confidential storage tier；推理侧模型权重与 KV/prompt cache 同样落在该层。
- 提到的公司/客户/产品/标准：Google；Intel TDX/TDX Connect，AMD SEV-SNP/SEV-TIO，Arm CCA；Caliptra，OCP L.O.C.K.，TCG DICE/Opal/MEK-MPA，DMTF SPDM/DOE，PCI-SIG TDISP，PCIe/CXL IDE，NVMe。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p16（三代信任边界演进：传统云→机密计算→机密存储）；p39（端到端会话建立 7 步全图）；p41（四种加密方案对比表）。

### P047 From Securing Links to Securing Pods- Security of Scale-Up Networks
- 讲者/机构：Avdhesh Chhodavdia，Technologist，Astera Labs [p1] | 类型：技术分享
- 方向归属（主/次）：主 [安全]；次 [Up 机柜/超节点：UALink/ESUN/机柜级互连]
- 核心主张：
  1. scale-up pod 作为"一台机器"运行：单一地址空间、内存语义流量，fabric 参与转发/终结/变换/保留，因此本身就是安全论证的一部分 [p4]。
  2. 端点证明加链路保护是必要证据，但在动态组合的系统中可能不够；"组合（composition）才是保证的单位"，且与协议无关（PCIe、UALink、CXL、ESUN）[p6]。
  3. 准入是租约而不是一次性事件：Form→Admit→Operate→Recover→Reprovision→Release，假设改变时才重新评估 [p11]。
- 关键数据：
  - 无量化数据。示例拓扑：同一组 8 个 XPU，可组合成"1 个 8 卡 pod"或"2 个 4 卡 pod"，相同设备和线缆，由成员关系与映射决定归属 [p5]（自报，示意）。
  - 三个平面的失效模式 [p7–p9]：管理面——克隆/降级/陈旧组件仍保有 fabric 权限；控制面——重配置可悄然改变谁能访问谁；数据面——租户残留状态可活过组合生命周期。
  - 安全模型四问：Claim / Dependency / Mechanism / Evidence [p10]。
- 提到的公司/客户/产品/标准：Astera Labs；PCIe、UALink、CXL、ESUN；RoT。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p5（同一 8 XPU 两种组合方式对比）；p11（pod 准入租约生命周期）。

### P048 Future-proof security in TPM with SPDM and PQC capabilities
- 讲者/机构：Antonio Javier Cabrera Gutiérrez，Staff Engineer System Architect，Infineon Technologies AG [p1] | 类型：技术分享 / 标准进展
- 方向归属（主/次）：主 [安全]
- 核心主张：
  1. TCG TPM SPDM 规范把 TPM 命令封装进 SPDM 安全会话，TPM 变成有认证、加密、完整性保护的安全端点；与 DICE 结合可缓解总线主动插入攻击 [p4]。
  2. PQC 标准仍在演进，靠固件更新底层实现密码敏捷是应对方式 [p6]。
- 关键数据：
  - 演进路线 [p5]（自报）：TPM 2.0 rev 1.38（ECDSA 固件更新）→ rev 1.59（ECDSA + XMSS/LMS，固件更新抗量子）→ rev 1.85（PQC-ready）；对应 PC Client PTP v1.07（ML-KEM/ML-DSA）、TCG EK Profile v2.7（ML-KEM）；代际间引脚兼容。
  - Demo [p7]（实验）：OPTIGA TPM SLB 9678 + Raspberry Pi，SPI 上跑 SPDM 通道；支持 ML-DSA-44/65/87、HashML-DSA-44/65/87、ML-KEM-512/768/1024；PQC 库 CC EAL6+ 认证；tpm2-tss/tpm2-pytss 增加 PQC 支持，OpenSSL v3.6.0-dev，Linux Kernel SPDM 支持"待合入内核"。
  - 背景：2022 年 OCP Summit 的 Project Kirkland 提出 SPDM+DICE 解决 TPM 总线插入攻击 [p2]（引用）。
- 提到的公司/客户/产品/标准：Infineon OPTIGA TPM SLB 9678；TCG TPM 2.0、TPM SPDM 规范；DMTF SPDM；DICE；NIST ML-KEM/ML-DSA、XMSS/LMS。
- 首次/记录/SOTA 声明：自称"已证明 PQC 与 SPDM 集成进 TPM 是可行的"[p9]。
- 推荐配图页：p5（TPM 代际 PQC 演进图）；p7（PQC+SPDM 演示器软硬件栈）。

### P053 Package-Aware Integrity- From Source-Agnostic Publication to Full-System Attestation
- 讲者/机构：Felipe Zimmerle（CTO，KonaSense）；Dhananjay Phadke（Principal Software Engineer，Microsoft）[p1] | 类型：技术分享（提案）
- 方向归属（主/次）：主 [安全]；次 [运维/可靠性/遥测]
- 核心主张：
  1. BMC 固件按整镜像签名、整镜像证明，构建期溯源（SBOM）和运行期证明（Caliptra RIM、SPDM）只在整镜像粒度相遇；"包"是最小可构建/审计/更新单元，却无人证明 [p2–p3]。
  2. 方案：Yocto 对每个包测量成一个叶子→写入只追加透明日志→设备启动时按包名排序重组根并 extend 到 PCR 14→用包含证明把已装包与已发布包对应 [p4]。
  3. 在现有 verified boot 与整镜像 OTP 防回滚之上叠加，无需新信任根 [p17]。
- 关键数据：
  - Demo [p5]（实验）：5 个 rpi3-openbmc 镜像均有有效签名；镜像 B 含 2,131 个包，其中 dropbear 2026.91-r0 在树大小 2,163 时无日志记录；整镜像校验 5 个都通过，只有逐包校验能区分。
  - 包含证明 [p10]（看图）：2,131 个包约需 12 个哈希即可离线重算根；无包认领的文件归入一个 (unowned) 叶子。
  - 运行时覆盖 [p12]（看图）：镜像 3,758 个文件中 2,484 个（66%）在运行时策略范围内（1,871 内核模块、418 程序、178 库、17 固件），1,274 个为数据；讲者注明这是范围分析而非实测，PCR 10 未 extend。
  - 增量 [p19, p21]（自报）：发布第三个镜像只新增 1 个叶子、复用 2,130 个；镜像 A→B 2,130 个测量相同、1 个变化。
  - 讲者承认的局限 [p20]：单日志单密钥、无监视者/gossip；静态测量不等于运行态，TOCTOU 仍在。
- 提到的公司/客户/产品/标准：KonaSense、Microsoft；OpenBMC、Yocto、Caliptra RIM、SPDM、TPM PCR、Linux IMA、CoRIM、Rekor、OCP S.A.F.E.、IETF RATS、Common Criteria。
- 首次/记录/SOTA 声明：无（明确说明未经 OCP Security Project 审议、未获背书 [p13]）。
- 推荐配图页：p10（包级 Merkle 树到 PCR 14 的示意）；p12（66% 运行时覆盖统计）。

### P054 Secure Key Distribution Protocol for SoC Hardware Blocks
- 讲者/机构：Craig Barner（Senior Distinguished Engineer，Marvell）；Darren Lasko（Principal Engineer，NVIDIA）[p1] | 类型：标准进展
- 方向归属（主/次）：主 [安全]；次 [In 封装内：chiplet/UCIe/D2D]
- 核心主张：
  1. SoC 内每个做加密的硬件块都要密钥管理，现状是厂商各自为政；用共享总线上的"虚拟私有总线"替代不可扩展的点对点私有总线 [p3–p4]。
  2. RoT（如 Caliptra）内的 KMTx 与各加密引擎旁的 KMRx 共享会话密钥，用 AES-GCM 封装数据密钥经共享 fabric 下发 [p6, p8]。
  3. SoC 变成多厂商 chiplet 的 SiP 后，借用 UCIe 的 Security Director / Chiplet Trust Agent（CTA）在跨 chiplet 场景建立初始配对密钥（IPK）[p18–p24]。
- 关键数据：
  - 规范状态 [p7]（自报）："KMRx MMIO and Protocol Architecture Specification" v0.7 已发布在 OCP Security Hub 目录；目标推进到 v1.0 [p29]。
  - 协议 7 步 [p8–p9]：上电共享 IPK（方法目前由实现定义）→ RoT 发带随机 nonce 的 Key Rotation 派生 Session Key → 生成 Data Key → AES-GCM 包装 → 写入 KMRx MMIO → KMRx 解包验证并交给 DCE → 可选 Status Request 加密确认送达。
  - 安全保证 [p15]：防重放/防丢弃（payload 内反重放计数器）；防改道（不同 KMRx 会话密钥不同，改道后认证标签校验失败）。
  - 无性能数字。
- 提到的公司/客户/产品/标准：Marvell、NVIDIA；Caliptra（Caliptra as Security Hub 子工作组）；UCIe（Security Director、CTA、CTA_SEED）；AES-GCM。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（KMTx/KMRx 七步流程图）；p24–p28（跨 chiplet 经 CTA 下发 IPK 的动画序列）。

### P057 Beyond DRAM- Byte-Addressable Persistent Memory via Compute Interconnects for AI
- 讲者/机构：Feng Zhu，Director, Storage Architect，Alibaba Cloud Computing [p1] | 类型：技术分享（含厂商产品）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化、HBM]；次 [Up 机柜/超节点：UALink]、[推理/算力/经济性]、[存储]
- 核心主张：
  1. KV cache 已成 HBM 瓶颈，没有单一介质能同时满足容量、性能和成本，需要 HBM/DRAM → SCM（PCM）→ CXL SSD → TLC/QLC 的分层 [p2–p3]。
  2. 用 CXL 接入的字节寻址持久内存（AliSCM，PCM 介质）和高 IOPS CXL SSD（AliFlash CXL）组成可池化的 warm-KV 层，经 CXL switch 在节点间共享（Panjiu UMX）[p6–p7]。
  3. 下一代把 warm-KV 层挂到 GPU 的 scale-up fabric（UALink）上，GPU 直接 load/store 访问 PCM，服务稀疏注意力的小粒度随机访问 [p9, p11]。
- 关键数据：
  - KV 占 HBM [p2]（自报/看图）：64 并发 × 32K 上下文下 KV 占 HBM 57%；Qwen3-235B 权重 235 GB、KV ~384 GB；DeepSeek-V3 权重 671 GB、KV ~141 GB。
  - AliSCM vs Optane DIMM [p4]（实测，自报）：寻址粒度 128 B vs 256 B；读延迟 350 ns vs 300 ns；读带宽 20 GB/s vs 8.1 GB/s；写带宽 6.5 GB/s vs 3.15 GB/s。AliSCM 为 CXL 2.0 Type-3 E3.S，256 GB–1 TB/模块，已量产部署。
  - AliFlash CXL [p5, p7]：Gen6/CXL 3.2 版本 4 TB/模块、20M IOPS（512 B）、读延迟 10–30 µs（自报）；Gen7/CXL 4.0 目标 50–100M IOPS/设备，100M IOPS×512 B = 51.2 GB/s 有效带宽（预测）；100 台设备池目标 10B IOPS（预测）。
  - 分层对比 [p7]（自报）：AliMemory（CXL DRAM）140 ns（64 B）、60M IOPS、256 GB/模块；AliSCM 350 ns（128 B）、40M IOPS。
  - KV offload 实测 [p8]（实验，看图核对）：iso-cost 下 AliSCM 128 GB 替代 DRAM 32 GB 做 L2。两层缓存（30 用户×30 轮，~126 GB KV）：吞吐 0.35→0.56 req/s（+58.3%），P90 TTFT 86.31→44.24 s（−48.7%）；三层缓存（90 用户×25 轮，~400 GB KV）：吞吐 0.40→0.67 req/s（+66.3%），P90 TTFT 233.18→149.31 s（−36.0%）。条件：RTX PRO 5000 48 GB，SGLang v0.5.6，Qwen3-8B。
  - 稀疏注意力访问特征 [p9]（自报）：~584 B/token/layer，每块连续约 1.34 token；HBM 驻留容量可从 1× 降到 0.1×（示例）。
  - UALink 参数 [p10]（引用 UALink 1.0）：200 Gb/s/lane，每端口单向最高 800 Gb/s（100 GB/s）；最多 1,024 个加速器；示例交换机目标端口到端口 <200 ns（50T 级，400 Gb/s 端口）。
  - UALink-AliSCM 估算 [p12]（预测，看图）：延迟以本地 DRAM=1 计，CXL DRAM 1.3×，RDMA 3.0×，下一代 AliSCM/UALink 0.4×（讲者注明基线访问路径待验证）；512 B 页读放大 1.65×（8 KB 为 8.79×）；同等 warm-KV 容量下成本 0.25×、功耗 0.125× DRAM；AliSCM 容量/带宽比 2 TiB/100 GB/s ≈ 20，与 DeepSeekV4 Flash 17.69、GLM-5.2/5.3 19.9、Qwen3.8-Flash-Next 22 等开源稀疏模型需求相当。
- 提到的公司/客户/产品/标准：Alibaba Cloud（AliSCM、AliFlash CXL、AliMemory、Panjiu 服务器、UMX）；Intel Optane DIMM；NVIDIA RTX PRO 5000；SGLang；Qwen3、DeepSeek-V3/V4、GLM-5.x；CXL 2.0/3.2/4.0，UALink 1.0，PCIe Gen7，XL-Flash、PCM。
- 首次/记录/SOTA 声明：对比 Optane DIMM 读带宽 20 vs 8.1 GB/s、写带宽 6.5 vs 3.15 GB/s [p4]（自报，未称"首次"）。
- 推荐配图页：p8（iso-cost KV offload 实测：+58.3% 吞吐、−48.7% P90 TTFT）；p12（UALink+PCM 四项估算：延迟、读放大、成本功耗、容量带宽比）；p13（UMX 总体架构：UALink+CXL 池化层）。

### P058 CXL in Hyperscale Environment- Fleet-Scale Challenges, Failure Modes, and the Path to Debuggability
- 讲者/机构：Markandeya Mudigonda、Vineet Parekh，Production Systems Engineer，Meta [p1] | 类型：技术分享（现网经验）
- 方向归属（主/次）：主 [运维/可靠性/遥测]；次 [In 封装内：CXL/内存池化]
- 核心主张：
  1. CXL 内存扩展器可以完全符合规范，但在舰队规模下仍无法调试 [p16]。
  2. 同一个主机侧症状（CPU→CXL.mem 读超时）可能来自 DIMM 故障、控制器逻辑 bug 或固件问题，设备内部对主机不可见，结果是不可屏蔽 MCE、主机无预警宕机、在途工作全部丢失 [p14]。
  3. 呼吁与 CXL Consortium 一起定义舰队级 CXL 设备可调试性与遥测要求 [p16]。
- 关键数据：
  - CXL 带来的现网收益 [p15]（现网，自报）：缓存类吞吐 +25%、保留时间 5–10×；分布式缓存平均查询延迟 −29%；数仓每服务器 executor +25%；开发机每服务器 VM +33%、舰队规模 −15%；ML 参数服务器服务器数 −25%、吞吐 +12%。
  - 故障分类 [p11–p13]：枚举类（固件自检失败、SPI Flash 失效、链路训练失败、ASIC 初始化失败）；运行时（PCIe surprise link down/completion timeout、CXL Viral、内存 CE 风暴、ASIC 无响应）；内存类（CE 两符号错、UE 多比特错、DDR 训练余量问题）；检测分带内（PCIe 扫描、MCE）与带外（BMC 心跳、SEL）。
  - 修复流水线 [p5–p8]：MachineChecker 检测 → Unified Repair 自动修复 → 固件更新/重装工单 → 技术员更换 CXL ASIC/DIMM 的维修工单。
  - 故障域框图 [p10]（看图）：CXL Subsystem（PCIe PHY + CXL Controller）→ CXL2DDR Bridge → DDR Subsystem（2×MEMC+PHY）；控制面含 Boot/Control/Security CPU、SRAM、SMBus/QSPI/UART。
  - 未给出故障率数字。
- 提到的公司/客户/产品/标准：Meta（MachineChecker、Unified Repair）；CXL Consortium；BMC SEL、AER、MCE。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p14（"一个症状多个成因"的可观测性边界图）；p15（CXL 现网收益表）；p10（CXL 内存扩展 ASIC 故障域框图）。

### P059 Cost-Efficient LLM Inference via Peer-to-Peer GPU-to-Memory Expansion Datapath
- 讲者/机构：Moshe Twitto（Fellow）、Amit Golander（Associate VP），Astera Labs [p1] | 类型：技术分享（厂商实测）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [推理/算力/经济性]、[Out 后端网络：交换芯片（PCIe switch）]
- 核心主张：
  1. KV cache offload（KV-CO）通常落到 CPU 直连 DRAM，容量和带宽受限；在 fabric 上增加内存控制器，让 XPU 以 P2P 方式直达，可分散流量、扩展容量带宽，把 CPU 带宽留给 agentic 负载，甚至省掉第二颗 CPU [p2–p3]。
  2. 需要在 KV-CO 框架内原生集成内存 fabric：已改造 LMCache，vLLM 原生支持在进行中 [p9]。
- 关键数据：
  - 实验平台 [p4]：4×NVIDIA RTX6000 Pro（96 GB）、1×Intel Xeon Platinum 8468、4×Astera Leo 内存控制器（各 256 GB DDR5-5600）、1×Astera Scorpio PCIe 交换（320 lanes）；vLLM 0.19，LMCache 0.4.3，Qwen3-14B，4 实例，多轮基准，3–8 轮，批 10–60。
  - 短 prompt（1–2K）、每实例 128 GB [p6]（实验，看图）：fabric 内存与 CPU DRAM 曲线几乎重合（约 7.5 RPS/GPU@15.5 tok/s/usr 到约 2.9@35.5），两者都明显高于 HBM-only（约 3.9→2.1）。
  - 中等 prompt（2–3.5K），4×128GB CPU vs 4×256GB fabric [p7]（实验，看图）：fabric 约 6.1–6.2 RPS/GPU vs CPU DRAM 约 3.2，图中标注"x2 better"。
  - 中长 prompt（5–6.5K），4×128GB vs 4×(256+128)GB [p8]（实验，看图）：fabric 约 4.1 RPS/GPU vs CPU DRAM 约 1.3（与 HBM-only 重合），图中标注"x3 Better"。
  - 注意：p7/p8 的对比中 fabric 侧容量更大（2×–3×），收益主要来自容量扩展而非同容量下的速度差异；同容量（p6）性能相同。
  - 脚注 [p6]：延长运行可在 CPU 侧容纳 3 TB、内存控制器侧 4 TB（自报）。
- 提到的公司/客户/产品/标准：Astera Labs（Leo Smart Memory Controller、Scorpio Smart Fabric Switch）；NVIDIA RTX6000 Pro；Intel Xeon 8468；vLLM、LMCache、SGLang、Dynamo KVCR；PCI-SIG、CXL、UALink。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（中长 prompt 下 fabric 内存约 3× RPS/GPU，并附 P2P 拓扑示意）；p3（P2P 数据路径示意）。

### P060 Disaggregated CXL Memory Architecture for Agentic AI- Dynamic Pooling, Sharing, and PNM Offloading
- 讲者/机构：Jinin So、Kyumin Park（Samsung）、Harry Kim（XCENA）、Junchen Jiang（Tensormesh）、Arifur Rahman（Marvell）[p1]；分三段：CXL 动态池化（Samsung/Tensormesh）[p2]、CXL 共享内存 + LMCache（XCENA）[p13]、计算型内存/PNM（Samsung/Marvell/XCENA）[p21] | 类型：技术分享（多厂商联合）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [推理/算力/经济性]
- 核心主张：
  1. 固定切分的 CXL 内存在 agentic 负载下会产生搁浅内存；用 CXL 池化 + DCD 动态增删容量，让内存跟随需求 [p5, p10]。
  2. 多 GPU/多主机直接 load/store 同一份 CXL 上的 KV cache，零拷贝共享，只移动元数据（XCENA Maru）[p14–p15]；CXL+SSD 混合配合预取/锁定策略可接近 DRAM 性能 [p16–p18]。
  3. 池化解决了容量但没解决互连带宽与能耗；PNM（近内存计算）就地计算、只回传结果 [p22, p30]。
- 关键数据：
  - 分层容量 [p6]（自报）：HBM 40–192 GB/GPU；DRAM 256 GB–2 TB/socket；CMM-D 128 GB–8 TB/socket（按 256 GB CMM-D）；CMM-D 机架池 5.5–11 TB（按 2 个 CXL 交换机）。
  - 池化吞吐 [p8]（实验，看图）：Long_Doc_QA，Llama3.1 8B，RTX PRO 6000 8 卡 + RDIMM 128GB×8Ch + MD220 256GB×4；KV 超出 RDIMM 容量后 RDIMM 方案因 GPU 重算吞吐降到约 17%，CXL 池保持约 95%，即 5.6×。
  - Agentic coding 负载特征 [p9]（实验，引用 lmcache-agentic-traces 中 Claude Code（Sonnet 4.5）场景）：三阶段 KV 命中率分别为 87–99%、约 50%（长上下文调用 97–99%）、汇总 83.5%。
  - 弹性分配 [p11]（实验，看图）：TTFT P99 归一化 DRAM 96GB 1.0 / DRAM 160GB 0.7 / Static 0.8 / Elastic(DCD) 0.48（−52%）；goodput（SLO TTFT≤60 s）1.0 / 2.2 / 2.2 / 7.1（7.1×）；Static/Elastic 为 32 GB DRAM + 1024 GB CXL 池。52%/7.1× 均以 DRAM 96GB 为基线。DCD 为在现有硬件上的仿真 [p10]。
  - InfiniteMemory [p17]（实验，看图）：共享文档查询平均 TTFT：DRAM 340 ms、prefix pinned 385 ms（1.13×）、no pin 534 ms（1.57×）、SSD 基线 632 ms（1.86×）；lookahead 预取 inflight=1 时 526 ms ≈ DRAM 509 ms，no-prefetch 4,314 ms（8.5×），inflight=8 时 no-prefetch 32,306 ms（63.5×）。条件：Llama-3.1-8B，LV-Eval，vLLM 0.23.0 + LMCache 0.4.8 + Maru，RTX 6000 Pro。
  - 粒度错配 [p18]（自报）：CXL 64 B cache line × 1K 未完成命令 = 仅 64 KB 在途，无法打满 10+ GB/s SSD；KV 块为数百 KB 至数十 MB，可在调度时预取。
  - PNM 带宽 [p22]（自报，Samsung 内部分析）：CXL 控制器后 DDR5 8.4 Gbps 带宽 268.8 GB/s，而 PCIe Gen6 x8 仅 64 GB/s；CXL 控制器到主机的数据传输占能耗 67.2%。
  - 机架级系统 [p23]（自报）：Samsung CXL 计算型内存系统 20 TB 容量、2.7 TB/s 带宽（Liqid CXL 交换）。
  - Marvell Structera A [p24]（自报）：5nm，16 核 Arm Neoverse V2 @3.2 GHz，最多 4 TB，DDR5 内部带宽 200 GB/s，95 W@3.0 GHz，LZ4 压缩提升 2–3× 容量。XCENA MX1 [p25]（自报）：3,072 RISC-V 核，4ch DDR5-8400 最多 2 TB，CXL 3.2 Type 3，PCIe Gen6。
  - RAG 向量检索 [p27]（实验）：FAISS IVF-Flat，512M 向量（Laion5B，1024 维，4.5 TB）；10 个 PNM 设备 QPS 14.81 vs 主机 CPU+CXL 池 0.23（64×）；能效 6.01 vs 0.092 queries/kJ（65×）；有效读带宽主机 26 GB/s vs 10×PNM 聚合 1,625 GB/s。
  - 混合注意力 [p29]（实验）：LLaMA 3.1 70B INT8，100K 上下文，RTX PRO 6000（96 GB），每 GPU KV 8 GB，2 服务器各 5 PNM；batch=1 时 5.28 vs 5.50 tok/s，batch=5 时 5.28 vs 17.7 tok/s（3.35×）；token/能耗 1.12 vs 4.31 Toks/kJ（3.84×）。
- 提到的公司/客户/产品/标准：Samsung（CMM-D、Pangaea v3、NDC API）、XCENA（MX1、Maru、InfiniteMemory）、Tensormesh、Marvell（MD220、CXL 2.0 Switch、Structera A）、Liqid CXL Switch；NVIDIA RTX PRO 6000 Blackwell；Intel Xeon 6747P；vLLM、LMCache、K8s、FAISS、PyTorch/OpenXLA；CXL 2.0/3.x DCD；OCP CMS、OCP FTI DCC。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p8（KV 超 DRAM 容量后 CXL 池维持吞吐 5.6×）；p11（DCD 弹性分配 TTFT −52%、goodput 7.1×）；p27（10 PNM 向量检索 64× QPS、65× 能效）；p29（100K 上下文混合注意力 3.35×）。

### P061 Managing Orchestration Memory with the CMS Memory Fabric Manager
- 讲者/机构：Hongjian Fan（Sr Staff Engineer，Seagate Technology）；Han Deok Lee（Principal Engineer，Samsung）[p1] | 类型：标准进展（OCP CMS 工作流）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [运维/可靠性/遥测]
- 核心主张：
  1. OCP CMS Memory Fabric Orchestration 工作流目标是定义内存 fabric 管理软件与开放互通的管理 schema，覆盖 CXL 3.x/4.x 和 scale-up 网络 [p2]。
  2. CXL Type-3 内存在 Linux 上有两种暴露方式：System RAM（无 CPU 的 NUMA 节点，适合透明扩容）与 devdax（适合跨主机共享池和 KV offload）[p4]。
  3. 用 Kubernetes DRA（全局发现、容量跟踪、调度）+ NRI（本地 DAX 创建、设备绑定、运行时注入）把 fabric 内存接入编排 [p5]。
- 关键数据：
  - 四类用例 [p6–p11]：8.1 节点级 System-RAM；8.2 Pod 级 System-RAM 在线扩缩（示例：agentic 框架工具调用时 8 GiB→32 GiB→8 GiB，不重启，用 KEP-1287 in-place Pod Resize，自 v1.35 GA）；8.3 节点级 devdax（示例 Milvus）；8.4 Pod 级 devdax 动态单元分配（示例 LMCache 用 CXL DCD）。
  - 不对称原因 [p7]：K8s 对 cgroup 内存有标准在线 resize 路径，但无法对运行中容器重新应用 CDI Spec，所以 devdax 场景只在 CreateContainer 时调一次 NRI，之后由 MFM in-band agent 的"Auto Injection"直接增删。
  - 无性能数字。
- 提到的公司/客户/产品/标准：Seagate、Samsung（Pangaea）；Kubernetes DRA/NRI/CDI、KEP-1287；Milvus、LMCache；OCP CMS Memory Fabric Orchestration Architecture White Paper Rev 1.1；GitHub OCP-SVR-CMS-CFM-Composability_Fabric_Manager。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p6（2×2 用例矩阵：节点/Pod 级 × System-RAM/devdax）；p4（NUMA 节点与 DAX 设备对比表）。

### P062 Tiered Memory for LLM Inference- A Modeling Framework for KV-Cache Offload
- 讲者/机构：Khayam Anjam，Staff Engineer，Micron Technology [p1] | 类型：技术分享（建模框架）
- 方向归属（主/次）：主 [推理/算力/经济性]；次 [In 封装内：CXL/内存池化、HBM]
- 核心主张：
  1. KV offload 的问题已不是"要不要"，而是"放在哪"；容量越来越决定可扩展性 [p2]。
  2. 有效复用 = 负载复用率受容量门控；容量决定可达复用范围，缓存策略只决定落在范围内哪一点。给出两个界：随机（保守）γeff = γworkload × min(1, S/W)；Oracle（乐观）γeff = min(γworkload, S/W) [p7]。
  3. KV 分两类人群：跨会话的 system prompt 层（复用 40–60%、小时级，容量驱动，适合 CPU DRAM/LPDDR5x/SCM）与会话内上下文层（复用 ≥95%、分钟级，带宽敏感，放 HBM 溢出到 DDR/LPDDR）[p8]。
- 关键数据：
  - 验证平台 [p10]：GH200 NVL2（2×H200 共 288 GB HBM3e，2×72 核 Neoverse V2，2×512 GB LPDDR5x @384 GB/s，NVLink-C2C 900 GB/s）；Llama 3.1-70B FP16，TP2，vLLM + LMCache，ISL/OSL 30K/128，3.8 req/s。
  - 验证 #1 [p11]（实验，看图）：kv-tier 800 GB，bs=16；实测 TTFT 随有效复用率 0.1/0.25/0.5/0.75/1.0 为 60.10/56.27/39.12/24.38/5.77 s；模型预测趋势一致，数值偏低约 7–8 s（看图估读）。
  - 验证 #2 [p12]（实验，看图估读）：KV 层容量 100→200→400 GB 时实测 TTFT 约 31→29→13 s，600 GB 起约 1.5 s；模型有效复用率约 0.73→0.95→1.0；呈阶跃，过阈值后容量作用很小。
  - 验证 #3 [p13]（实验，看图）：kv-tier 800 GB，并发 1–16 时有效复用约 100%，并发 64 时降到约 0.45（看图估读），TTFT 急剧上升（对数轴，具体值看不清）。
  - 本框架目前只在 GH200 级稠密模型上验证，MoE 与多厂商平台待验证 [p16]。
- 提到的公司/客户/产品/标准：Micron；NVIDIA GH200 NVL2/H200；vLLM、LMCache；Llama 3.1-70B；HBM、LPDDR5x、CXL、SCM；OCP CMS。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p12（KV 层容量阈值的阶跃曲线）；p8（KV 两类人群及放置建议）；p7（容量门控有效复用公式）。

### P063 XPU Scale Composable Smart Memory Fabric
- 讲者/机构：Gaurav Agarwal（Senior Distinguished Engineer）、Satananda Burla（Distinguished Engineer），Marvell [p1] | 类型：技术分享（厂商产品）
- 方向归属（主/次）：主 [In 封装内：CXL/内存池化]；次 [Up 机柜/超节点：机柜级互连（光互连内存设备）]、[推理/算力/经济性]
- 核心主张：
  1. 可组合内存从直连扩展（Structera X/A）→ 服务器内 CXL 交换池化（Structera S）→ 机架/Pod 级光互连共享内存（Photonic Fabric Memory Appliance）分层演进 [p3]。
  2. 把整个 KV cache 服务卸载到带近内存计算的智能内存 fabric：缓存层与计算层独立扩展，对计算等距、性能可预测 [p9]。
  3. GPU 侧流量走 PCIe P2P DMA，由扩展器 DMA 控制器直接读写 GPU HBM，绕过主机 DRAM 与 IOMMU，GPU 侧无需 CXL [p14]。
- 关键数据：
  - Photonic Fabric Memory Appliance [p4]（自报，看图核对）：1 TB HBM3e + 128 根 DDR5 DIMM（16/32 TB）；支持 CXL 3.1（含 DCD）；连 16 台服务器或 16 个 XPU，每路 2 Tbps；访问延迟 <350 ns，对比服务器间典型 ~µs。
  - Structera S [p5]（自报）：CXL 2.0 交换，PCIe 5.0 16×16/32×8，2 TB/s 交换容量，最高 100 TB 池，端口到端口 <100 ns，135 W（文字层工艺写"1.6nm"，存疑）。
  - KV 层级 [p6]（自报）：G1 HBM（ns，数百 GB）；G1.5 PFMA + PF-Chiplet（封装级集成，数十 TB @ 数百 ns）；G2 系统 DRAM（1–2 TB）；G2.5 CXL fabric 内存（Structera 或 PFMA，数十 TB @ 数百 ns）；G3 本地 SSD（µs，数十 TB）；G4 共享对象/文件（数百 TB）。
  - KV 服务卸载早期结果 [p10]（实验，看图）：lmbench long-doc-qa，峰值 16 用户，Llama-3.1-8B，H200。传输带宽读/写：本地 SSD 31.8/31.1、RDMA 46.8/46.9、Structera A 50.0/48.0 GB/s；input tok/s 与平均 TTFT：HBM 重算 31,394 / 5,933 ms，SSD 44,318 / 4,243 ms，CPU DRAM 80,813 / 2,162 ms，Structera A 139,497 / 1,199 ms；即 TTFT 5×、吞吐 4×；读延迟较本地 SSD 52 µs→3 µs（17×）。
  - KV 压缩卸载 [p12]（实验）：Llama-3.1-8B，4 文档×64K×10 轮，1×H200 + 1×Structera A：无压缩 TTFT 4,864 ms / 16,832 tok/s / 命中 35.1%；FP8 3,374 ms / 22,860 / 2.0× 压缩；TurboQuant k8v4 2,914 ms / 22,845 / 2.61× / 命中 46.5% / 占 7.4 个 Arm 核；CacheGen 2,834 ms / 25,594 / 5.6×，但精度损失角 13.4°且讲者注明实现未完成。
  - Structera X 2404 [p15]（自报）：最多 12 根 DIMM、1.5 TB；内联 LZ4 压缩线速约 1.6–2×；KV 以 2 MB 连续块传输。
  - Nixlbench [p16–p17]（实验，看图）：大块读带宽 Structera→GPU 50.6 GB/s vs RDMA 46.3 GB/s；写 GPU→Structera 64 MB 时 55.5 vs 46.3 GB/s（128 KB–1 MB 区间 Structera 写略低于 RDMA）；64 MB 读延迟 1,325 µs vs RDMA 23,199 µs，写 1,209 vs 23,197 µs；4–128 KB 小块读延迟约 3–4 µs vs 约 20–50 µs（看图估读）。
- 提到的公司/客户/产品/标准：Marvell（Structera A/S/X/P、Photonic Fabric Memory Appliance、PF-NIC、PF-Chiplet、UIOT）；NVIDIA H200 NVL；vLLM、LMCache、NIXL、CacheGen、TurboQuant；CXL 2.0/3.1 DCD；OCP CMS、FTI DCC、SNIA；HotStorage 2026 论文。
- 首次/记录/SOTA 声明：无
- 推荐配图页：p4（Photonic Fabric Memory Appliance：16 服务器 × 2 Tbps，<350 ns）；p10（KV 服务卸载 TTFT 5×、吞吐 4×）；p17（Nixlbench 延迟 Structera vs RDMA 对数曲线）。
