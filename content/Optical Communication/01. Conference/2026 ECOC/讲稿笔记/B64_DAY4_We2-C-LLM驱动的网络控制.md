---
title: "B64 · DAY4 · We2-C-LLM驱动的网络控制"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We2-C1-939-北邮-技能增强的链路故障诊断LLM智能体.pdf
- 讲者/机构：Shengnan Li, Fubin Wang, Zihao Cui, Min Zhang, Danshi Wang*（北京邮电大学 BUPT，信息光子学与光通信国家重点实验室） | 题目：Token-Efficient and Output-Reliable LLM Agent for Link Fault Diagnosis via Skill-Augmented and SOP-Constrained Design | 类型：学术论文
- 方向归属（主/次）：主 1（AI光网络/运维）；次 无
- 核心主张：
  1. 光网络 O&M 需要“既省 token 又可靠”的 LLM Agent：典型 Agent 每步重复注入完整 O&M 上下文（token 成本高、推理慢），且工具选择/终止不受约束，同一告警多次运行路径与输出不一致 [p5–p6]。
  2. Agent Skills 采用渐进式披露（初始只见 Skill 元数据，选中后才加载详细指令与脚本/参考）以降低上下文；SOP 定义确定性的高层 O&M 流程（告警预分析→拓扑匹配→光功率核查→根因输出），“工作流层确定、Skill 层自适应” [p7–p9, p11]。
  3. 结论页：Skills 减少上下文，SOP 稳定诊断轨迹 [p13]。
- 关键数据：
  - 相对基线 Agent token 减少 86%；在所评估的光纤故障场景下 RCA（根因分析）准确率 100% [p13]
  - 评估设计：光纤断裂与光纤弯曲两类场景；基线 Agent 与 Skill 增强 Agent 使用同一 NMS 接口和相同故障条件；跨不同跨段随机化测试 100 次 [p12]
  - SOP 四步：Step2 告警预分析（Alarm Analysis Skill）、Step3 根因分析（Topology Matching / RCA Skill）、Power verification（Optical Power Query Skill：端口名→查询RESID→构造API请求→解析响应→Tx/Rx功率）、Step4 根因输出（Evidence+Conclusion）[p8]
- 提到的公司/客户/产品/标准：Ciena（测试床 NMS 侧图中出现 Ciena 字样，OCR识别，未核图）；agentskills.io（Agent Skills 规范）[p7, p12]；REST/Callback、Query/Config、SET/POST 接口 [p12]
- 与业界对比或记录声明（SOTA/首次/record）：未声明SOTA；仅对比自身基线 Agent [p13]
- 推荐配图页：p8（SOP 四步流程与 Skill 内部执行链）；p13（结论与 86%/100% 数字）

### 0923-We2-C2-1339-符合T-API的ReAct智能体环.pdf
- 讲者/机构：讲者未在OCR中识别；Chalmers University of Technology（页脚 CHALMERS） | 题目：A T-API-Compliant ReAct Agentic Loop for Optical Networks | 类型：学术论文
- 方向归属（主/次）：主 1（AI光网络）；次 无
- 核心主张：
  1. 构建符合 Transport API（T-API）的 ReAct 智能体环，比较三种工具抽象：Generic（原始 request 调用 T-API/内部接口）、Single-Call Tools（原子工具，如 estimate_qot、provision_service）、Multi-Call Tools（复合工具，如 find_best_modulation）[p7–p8]。
  2. 抽象层级更高可提升成功率但涉及 token 消耗权衡；指令微调（instruction-tuned）模型优于推理（reasoning）模型 [p13]。
  3. AI agent 未必取代网络专家，而是让其聚焦高风险决策；“AI agent 是否可用于生产？——尚未（Not yet）” [p13]。
- 关键数据：
  - 实验平台：1× NVIDIA RTX PRO 6000（96 GB VRAM）；CORONET CONUS 拓扑数字孪生（75 节点，99 链路 [OCR“TS nodes 99 links”，节点数看不清]，198 条 fiber 链路、546 条有向连接、2,088 件设备；GNPy 物理层模型；C 波段）；本地模型 Qwen2.5 32B Inst、Qwen3.5 35B、9B、4B；任务含查询/开通/分析 [p6]
  - Eval pass（Generic / Single-Call / Multi-Call）：Qwen2.5 32B Inst 57% / 36% / 90%；Qwen3.5 35B 58% / 27% / 55%；Qwen3.5 9B 57% / 27% / 54%；Qwen3.5 4B 20% / 18% / 28% [p9–p11]
  - 每次运行平均总 token（Generic / Single / Multi）：Qwen2.5 32B Inst 30.3k / 10.1k / 10.6k；Qwen3.5 35B 31.5k / 21.3k / 45.0k；9B 37.6k / 16.6k / 21.1k；4B 35.9k / 39.2k / 18.8k [p12]
  - 开通示例（Abilene—Dallas）：依次尝试 DP-64QAM/DP-16QAM 均因 QoT/GSNR 余量不足失败，DP-QPSK 通过后开通；对比页标注 5K tokens 与 8K tokens（对应哪种变体看不清，未看图核对）[p8，OCR]
- 提到的公司/客户/产品/标准：Transport API（T-API）、GNPy、CORONET CONUS、Qwen 系列 [p6]
- 与业界对比或记录声明（SOTA/首次/record）：无；结论承认尚未达生产可用 [p13]
- 推荐配图页：p11（三种工具变体 × 四个模型的 Eval pass 对比，最能体现 32B Inst + Multi-Call 达 90%）；p12（token 消耗对比）

### 0923-We2-C3-1409-米兰理工-大模型与光网络的共生关系.pdf
- 讲者/机构：Massimo Tornatore / Politecnico di Milano（DEIB） | 题目：LLM and Optical Networks: A symbiotic relationship | 类型：邀请报告
- 方向归属（主/次）：主 1（AI光网络）；次 2（Scale-across，跨数据中心分布式训练/HCF）
- 核心主张：
  1. 光网络与 LLM 共生：Net4LLM（跨地域分布式 LLM 训练/推理对 WAN 的需求，含网络资源分配、空芯光纤、光子计算），以及 LLM 用于网络管理 [p3]。
  2. 现有集合通信库（CCL）面向数据中心内部（均匀高带宽假设），跨 DC 需专门的 CCL，且 CCL 重配置（慢）与 WAN 重配置（快）需联合优化 [p10–p13]。
  3. 结论：最终目标是消除数据搬运瓶颈——跨层可重构、IP+光+计算协同设计（可能借助 LLM）[p27]；LLM 在光网络管理中当前现实的应用为代码生成（TAPI、NETCONF）、意图翻译、数字孪生编排、故障管理、规划流程；“零接触 LLM Agent”和低时延 M2M 应用目前不现实 [p24]。
- 关键数据：
  - 跨区域训练降低吞吐（GPU 空转），引用 Strati 等 2024（2 Region, US 与 US-EU 场景，具体数值未看图）[p8]
  - Scale-CCL 对比（含 WAN 延迟 50 µs/10 km、500 µs/100 km、1000 µs/200 km，16 GPU inter-DC）：与 TE-CCL 最大差距 ≤ 8.9%（4 MB 时约 3–4%）；完成时间比 NCCL 低约 50%，比 SPH（最短路径）低约 60%；调度执行时间比 TE-CCL 快约 1000×（1348 s → 0.22 s）[p16]
  - TE-CCL（ILP）在 16 GPU inter-DC 网络上执行约 3 小时（Intel i9-13900K，128 GB DDR4）；加入 sub-chunking 后不可扩展 [p15，OCR]
  - HCF 空芯光纤传播时延低约 30%；客户到 DC 时延约束 400 µs 下：0% HCF→6 个 DC，4% HCF→4 个 DC，21% HCF→3 个 DC（来自 Ibrahimi 等 TNSM 2025）[p22]
  - 网络编码（光 XOR）用于 AllGather：带宽节省 10–20%；共享链路传输减少 50%（N3→N4 由 2 次降为 1 次）；传输轮数 4→3；资源占用示意 Multicast ≈60%、AllGather 无编码 ≈240%、有编码 ≈190%（Xin Wang 等，JLT 2026）[p23]
  - Llama 3 405B 预训练 54 天中断根因：Faulty GPU 148 次占 30.1%；引出集合通信网络保护开放问题及延迟备份预留（deferred protection）思路 [p17–p18，OCR，其余占比看不清]
  - 一个 30 kbyte prompt 可产生 10 Gbyte KV-cache（Prefill/Decode 拆分部署）[p21，OCR]
  - LLM 规模趋势：万亿神经元规模模型 → 100K GPU [p4，OCR]
- 提到的公司/客户/产品/标准：NCCL、TE-CCL、SCALE-CCL、RDMA over WAN（iWARP、OmniDMA）、Llama 3、NVLink/NVSwitch、ZR/ZR+、空芯光纤（合作方 FiberCop [OCR]）、TAPI、NETCONF、ECOC 2024 相关 LLM 配置论文（Di Cicco、C. Sun 等）[p5, p9, p25–p27]
- 与业界对比或记录声明（SOTA/首次/record）：Scale-CCL 相对 TE-CCL 调度 1000× 加速且差距 ≤8.9% [p16]
- 推荐配图页：p16（Scale-CCL 完成时间与执行时间对比）；p22（HCF 使边缘 DC 由 6 减至 3）；p27（结论页：IP+光+计算协同栈图）

### 0923-We2-C4-731-IPoDWDM全生命周期自动化的MCP架构.pdf
- 讲者/机构：讲者未识别；Adtran（页脚 Adtran；首页含德国联邦研究部资助标识，OCR “Federal Ministry of Research, Technology”） | 题目：MCP-enabled agentic AI for IPoDWDM lifecycle automation（首页英文全题OCR乱码，此为 p2 标题 “MCP enabled agentic AI based IPoDWDM” 的概括） | 类型：学术论文
- 方向归属（主/次）：主 1（AI光网络）；次 2（ZR/ZR+ IPoDWDM）
- 核心主张：
  1. 用 MCP（Model Context Protocol）把 LLM 推理与知识（文档、RAG、wiki）和观察/动作（标准接口、API）连接，面向多层、多厂商、多段、多域的分层 SDN 控制器，实现自动化/智能/自治/弹性等 [p2]。
  2. 多 MCP server 架构：运营自动化、Plug control（可插拔模块）、E2E、Telemetry 等 server；工具经 SDN 控制器或直接连设备 [p3, p5]。
  3. 演示自然语言驱动：拓扑展示、光纤图、E2E 服务开通、性能查询、基于 GNPy 的性能估计并与测量对比 [p6–p10]。
- 关键数据：
  - Agent 开发：自研 Agent，基于 GPT5.2 或 Claude Opus 5；每个 MCP 工具拆为原子步骤，每步带验证/核查/错误处理；先用 Adtran Ensemble 模拟器测试再上真实测试床；Redis 短/长期记忆；基于 Streamable HTTP [p4]
  - E2E 开通演示：Network TAPI，节点 ptx10001_real_2 至 ptx10001_real，频率 193.1 THz，带宽 75 GHz，指定中间节点 F8_44，结果 Success，路径经 F8_41–F8_44–F8_45 [p8]
  - 设备性能查询（ptx10001_real，接口 0/1/10）：Tx -8.64 dBm，Rx -2.69 dBm，Pre-FEC BER 6.980e-03，Uncorrected FER 0.000e+00，SNR 14.3 dB，OSNR 26.0 dB [p8]
  - GNPy 估计 vs 测量：OSNR ASE（0.1 nm）曲线约 33–34 dB，测量点（3 个，约 191.5/193/196 THz）落在估计曲线附近；沿路径每信道功率在约 +7 dBm 与约 -17 dBm 间往复 [p10]
- 提到的公司/客户/产品/标准：Adtran（Ensemble、CROMA 云端可重构光管理与自动化平台）、Ciena/Huawei/Nokia/Cisco/Juniper（多厂商示意）、GPT5.2、Claude Opus 5、Redis、GNPy、TAPI、MCP [p2, p4–p5]
- 与业界对比或记录声明（SOTA/首次/record）：无明确声明；p3 提示当前假设单 Agent [p3]
- 推荐配图页：p8（自然语言开通 E2E 服务与性能指标表）；p10（GNPy 估计与测量 OSNR 对比）

## 本批小结
1. 光网络 LLM Agent 的核心矛盾是“可靠性与 token 成本”：BUPT 用 Skills 渐进披露+SOP 约束实现 token 降 86%、RCA 100%（C1）；Chalmers 显示工具抽象层级影响很大，Qwen2.5 32B Inst 用 Multi-Call 工具达 90%，且 token 由 30.3k 降至约 10.6k，但其它模型不稳定（C2）。
2. 共同的工程范式是“确定性外壳+受约束的 LLM”：SOP（C1）、原子/复合工具（C2）、MCP 原子步骤带验证（C4）、约束生成与形式验证（C3 p25）都在抑制幻觉。
3. 标准接口与数字孪生成为 Agent 落地基座：T-API+GNPy 数字孪生（C2）、MCP+TAPI+GNPy 与真实设备（C4）、TAPI/NETCONF 代码生成（C3）；C4 的 GNPy 估计与测量 OSNR 吻合。
4. 对生产可用性普遍持谨慎态度：C2 明言“尚未”，C3 称零接触 Agent 目前不现实，C4 仍假设单 Agent；C3 提出多 Agent 按 Day0–N 生命周期分工为挑战。
5. 反向（光网络服务 AI）：C3 提出跨 DC 分布式训练需要 WAN 感知 CCL（Scale-CCL 比 TE-CCL 调度快约 1000×）、空芯光纤（30% 低时延使边缘 DC 6→3）和光 XOR 网络编码（带宽节省 10–20%），与方向 2 的 Scale-across 相关。
