---
title: "B57 · DAY4 · We-F-标准化专场"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We-F-00-标准化专场II连拍.pdf（第1–10页）
- 讲者/机构：Martin Creaner，World Broadband Association (WBBA) 总干事 | 题目：State of AI in Broadband today, and its role in the future | 类型：标准/市场分析（ITU-T ION-2030 专场）
- 方向归属（主/次）：主 5 固定与无线接入（AI-FAN/宽带）；次 1 AI光网络
- 核心主张：
  - AI 流量演进分三阶段：AI增强应用（2025–2027）→ AI原生应用出现（2027–2030）→ AI原生应用主导（2030–2035）[p6]
  - 运营商采用AI的主要动因是运营效率，主要障碍是数据质量与AI技能 [p8]
  - WBBA 与 ITU-T 形成闭环合作推动 ION-2030：收集运营商需求→ITU-T出标准→WBBA做商用案例与推广→与认证机构（如ETSI）做测试认证→更广泛参与 [p10]
- 关键数据：
  - WBBA 2022年成立；约250个成员、60家运营商；董事会成员含 Omdia、Ookla、OpenServe、stc、Swisscom、Turkcell、ZTE、中国电信、中国联通、Fibertech、Globe、华为等（p3该页图片上下颠倒，logo仅部分可辨）[p2][p3]
  - 全球网络流量预测至2035：常规流量 4% CAGR（2025–35）；增强型AI流量 26% CAGR；全新AI流量 85% CAGR；纵轴单位 Exabytes/year，2035年总量图上约6.5万 EB/年（读图估值）[p6]
  - 调查对象 343家运营商（2026年3月，Omdia）：五大障碍为数据质量与治理 39%、缺乏内部AI人才 39%、网络安全 32%、ROI不明确 26%、对AI模型能力缺乏信任 24% [p8]
  - 投资AI的动因：提升运营效率与生产率 48%、提升网络效率与自动化 39%、降本 34%、改善客户体验 31%、新收入 28%、主权AI 20%（图上数字较小，读数为估读）[p8]
  - WBBA 出版物：Broadband Vision 2030；State of AI in Broadband（>340运营商调查）；Evolution of AI Traffic；Optical Network Architecture AI Era；指数报告：Fiber Development Index 覆盖>90国，Broadband & Cloud Development Index 覆盖75国，Gigacity Index 覆盖50国 [p5]
  - 工作组WG1–WG7及游戏与电信特别工作组（WG7为AI对宽带的影响）[p4]
- 提到的公司/客户/产品/标准：ITU-T ION-2030、Omdia、ETSI、IETF、IEEE、Broadband Forum
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p6（AI流量演进路线图与至2035年流量分类预测曲线）；p8（343家运营商AI采用障碍与动因柱状图）

### 0923-We-F-00-标准化专场II连拍.pdf（第11–19页）
- 讲者/机构：Fotini Karinou，Microsoft，Director Optical Technologies & Architecture（SPARC / Azure Hardware Systems and Infrastructure） | 题目：Optical Scale-Up AI Systems: progress in Standards | 类型：邀请报告/标准
- 方向归属（主/次）：主 4 Scale-up/in CPO/NPO/XPO；次 3 Scale-out（光源/调制器）
- 核心主张：
  - 铜缆已到尽头：触达、密度、pJ/bit限制了机架边界处的scale-up [p12]
  - 光使多机架、多排（multi-rack/multi-row）AI scale-up 可行，系统价值来自触达、带宽密度、效率、利用率与韧性 [p12]
  - 接口规范与产业碎片化是挑战，OCI MSA 是解法：通用PHY + 多代路径；在此基础上需协调OIF/OCP/APC等标准工作对齐全栈 [p12][p19]
- 关键数据：
  - 单层高基数（High Radix）交换机可实现统一通信域，加速器托盘内光互连提供触达/带宽/连接；可再加一层交换机继续扩展 [p14]
  - 带宽-规范时间表：200 Gbps 今天；400 Gbps 2027(?)；800 Gbps TBD，>2030(?)；OCI GEN1 今天 [p15]
  - OCI-MSA 于2026年3月成立，图示成员logo含 Meta、Microsoft、OpenAI、AMD、Broadcom（红色logo，疑似）、NVIDIA；目标“Move scale-up from in-rack to multi-rack & multi-row”；规范见 www.oci-msa.org（GEN1）[p16]
  - OCI MSA 光实现：NRZ、WDM、标准激光器、Bi-Di 单纤（λ1..λ4 发、λ5..λ8 收，图示）；定位“更低功耗、更低成本、更低时延、更高单纤带宽” [p17]
  - 标准分工：OIF（ELSFP for OCI、CMIS改进、链路可靠性/初始化/互操作）；OCP（物理光托盘与机架设计、外形、系统可靠性、连接器、生态需求）；APC（Wafer-to-Systems、SiP制造规范、CPO与SiP测试测量、OSAT级）[p19]
  - 引用：OIF Compute Optical Interfaces (COI) 白皮书（scale-up需求）、OCI MSA（NRZ/WDM/BiDi）、OCP Open SiPhotonics for AI Systems [p18]
- 提到的公司/客户/产品/标准：Microsoft Azure Cobalt 100/200、Maia 100/200、Azure Boost DPU [p13]；OCI-MSA、OIF、OCP、APC、IEEE、CMIS、ELSFP
- 与业界对比或记录声明（SOTA/首次/record）：无（标准进展类）
- 推荐配图页：p17（OCI MSA 光实现：NRZ+WDM+Bi-Di单纤及生态链）；p19（OIF/OCP/APC 分工图）；p15（scale-up互连规范的三大挑战与速率时间表）

### 0923-We-F-00-标准化专场II连拍.pdf（第20–25页）
- 讲者/机构：Juan Pedro Fernandez-Palacios，Telefónica CTIO，Head of Transport | 题目：Framework and Requirements for AI deployment in Telco Transport Networks | 类型：邀请报告/标准
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI/AI光网络；次 2 Scale-across/ZR/ZR+（案例为ZR+开通）
- 核心主张：
  - 电信传送网AI框架的关键要求：访问控制（关键信息隔离）、Token优化、确定性行为 [p21][p25]
  - 指南：通过API直接读取网络状态，通过受治理的工作流进行配置（读写分离的Read Agent / Configuration Agent）[p23][p25]
- 关键数据：
  - 框架含：AI治理；多Agent间及与LLM/网络API的确定性；标准API供数（IP用IETF，光用TAPI）、厂商无关结构化数据模型；LLM无关架构；边缘计算+第三方云结合 [p21]
  - 参考多Agent数字孪生架构：n8n工作流编排、MCP Server（工具网关：RBAC、Schema校验、审计日志、Token）、LLM 为 Ollama（72Bn）、PostgreSQL+RAG知识库、NSO（服务编排器，Dry Run/Commit/Rollback）、gNMI/NETCONF/CLI；Agent A=ZR+ Provisioning，Agent B=L3VPN（BGP、MPLS），Agent C=Troubleshooting；观测栈 Grafana、Loki、Prometheus/AlertManager [p24]
  - 电信边缘架构服务可持续AI：分布式GPU、Telco Edge、接入/汇聚/核心、光连接（示意图，无数字）[p22]
- 提到的公司/客户/产品/标准：Telefónica、TAPI、IETF、MCP、n8n、Ollama、NSO、ZR+
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p24（多Agent数字孪生参考架构，含MCP网关与ZR+开通Agent）；p23（读/写Agent分离与受治理执行流程）

### 0923-We-F-00-标准化专场II连拍.pdf（第26–32页）
- 讲者/机构：中国电信（讲者姓名未见，标题页未拍到） | 题目：（无标题页；内容为 China Telecom All-optical Network 3.0 / ION-2030 for AI 数据中心）| 类型：邀请报告/标准
- 方向归属（主/次）：主 2 Scale-across/FST/跨楼园区；次 4 Scale-up/in（OCS替代super-spine），5 接入（50G-PON/OSU）
- 核心主张：
  - AI负载重塑数据中心网络，光网络从“连接DC”走向围绕DCA/DCN/DCI组织算力连接（All-Optical Network 3.0）[p27][p28]
  - ION-2030 提供整合DCA、DCN、DCI的统一框架；中国电信通过弹性算力接入、基于OCS的DCN、高可靠Scale-Across DCI来示范 [p32]
  - 算力规模演进 Scale-Up→Scale-Out→Scale-Across（单机架→多机架→多集群→多数据中心），光互连向GPU/XPU侧延伸 [p27]
- 关键数据：
  - 预测：到2033年AI流量占全球网络总流量 62%（Omdia AI Network Traffic Forecast 2023-33）[p26]
  - KPI：DC间带宽 800Gb/s/λ+；时延毫秒级；可靠性：无损恢复保护；灵活性：ROADM/OXC/WSS全光路由；效率：OCS-based DCN节能架构；AI辅助M&C [p28]
  - DCA：弹性上行带宽500M–8.7G（50G-PON下最高40G上行）；OSU传送支持2M–100G细粒度；低时延：本地降30–50%、市内(inter-city)20–40%、省际8–16%（相对基线，基线条件页面未标）[p29]
  - DCN：OCS替代super-spine交换机；规模未来可达百万GPU；速率无关，支持400G/800G/1.6T；无光模块使故障率降低17%+；全光交换相比三层胖树节省约20%网络功耗 [p30]
  - DCI：多DC分布式训练/推理，训练效率>97%，最多支持3个跨城DC，最多1024 GPU；WSON 50ms：8节点实验室+4节点现网测试床，最大路由长度640 km，最大恢复时间<50 ms，单波速率400/800 Gb/s [p31]
  - 引用来源：ITU-T GSTR.ION-2030（2025.10）[p28]
- 提到的公司/客户/产品/标准：China Telecom、CCSA、ITU-T ION-2030（aiDC/aiBB/aiHome）、OCS、OSU、50G-PON、WSON、M-OTN
- 与业界对比或记录声明（SOTA/首次/record）：无明确声明
- 推荐配图页：p31（DCI：跨城多DC训练效率>97%与WSON 50ms恢复）；p30（OCS替代super-spine及17%/20%收益）

### 0923-We-F-00-标准化专场II连拍.pdf（第34–46页）
- 讲者/机构：ETSI ISG F5G 代表，Post Luxembourg（讲者姓名未见） | 题目：（OCR/图片未见完整标题；内容为 ETSI ISG F5G 演进、F5G-Advanced 与 F6G 愿景，含“How Will AI Evolve?”）| 类型：标准
- 方向归属（主/次）：主 5 固定与无线接入 PON/FTTR/AI-FAN；次 1 AI光网络
- 核心主张：
  - AI走向感知-行动闭环与Agent（Perception-Action Loop、Agent-to-Agent通信），带来无处不在的数据中心/边缘与分布式智能，网络成为互连、协调与编排的平台 [p38][p39][p40][p43]
  - 基础设施约束（能源可用性、环境、社会接受度）正在显现 [p41]
  - F5G-Advanced 是分布式智能的基础；路径上从 F5G-A 走向 ION-2030 / F6G [p44][p45]
- 关键数据：
  - ETSI ISG F5G 时间线：2019 成立；2021 F5G Release 1；2023 Release 2；2024 F5G-Adv Release 3；2026 Release 4；2027 Release 5（图上另标 Activity Move in TC ATTM F5G，2026年F6G Workshop 网络研讨）[p34]
  - F5G-A 三大维度扩展：eFBB（用户速率×10，含Wi-Fi 7、50GPON、400G/800G OTN）；RRL（时延1/10，99.9999%可用性，工厂≤1 ms、现场总线连接≤0.1 ms）；GAO（能效×10）；FFC（连接密度×10，FTTR/FTTM等）；GRE（L4自治网络）；OSV（光感知与可视化，99%精度、1米定位）[p45]
  - 白皮书 “The Pathway from F5G-A to F6G”：第1版由ETSI ISG F5G背书，第2版征稿；版本路线 2026 Release 5 F5G-Advanced + F6G Vision，Release 6 F6G（2027–2028），Release 7 F6G（2029–2030）[p45]
  - 在研工作项：WI-25 F5G-A PON网络算力协同架构（GS F5G-025，预计2026年11月发布）；GS F5G-27 端到端管理与控制；WI-43 绿色F5G-Advanced最佳实践与指标（GR F5G-43，预计2026年12月发布）[p44]
  - 人体对照数字：约100 W功耗、126M视觉感受器等（AI仿生类比，非光通信数据）[p37]
- 提到的公司/客户/产品/标准：ETSI ISG F5G、GR F5G 021、ATTM、ITU-T ION-2030、WBBA（p39引用WBBA “Evolution of AI Traffic and its Impact on Broadband Networks”）
- 与业界对比或记录声明（SOTA/首次/record）：无
- 推荐配图页：p45（F5G-A六维雷达与ION-2030/F6G对照及版本路线）；p34（ISG F5G 发展时间线与工作方法）

### 0923-We-F-00-标准化专场II连拍.pdf（第47–62页）
- 讲者/机构：Daniel Pérez-López, Luis Torrijos-Moran 等，iPronics | 题目：Silicon photonics Optical switches for next gen AI datacenters（ITU-T ION-2030 Symposium Session 2）| 类型：邀请报告/产业发布
- 方向归属（主/次）：主 3 Scale-out/OCS；次 4 Scale-up（OCS用于scale-up扩展）
- 核心主张：
  - 光互连正在占据数据中心网络越来越大的份额（光纤、收发器、CPO）[p62]
  - OCS可缓解部分主要瓶颈，并支持跨机架扩展计算域；产业已可交付硅光开关：高密度、高基数、亚毫秒重构 [p62]
  - 硅光OCS对AI数据中心需要偏振不敏感与中高基数 [p54]
- 关键数据：
  - 用于scale-up扩展的光开关：紧凑（每1U 3–4个开关）、低成本约\$100/port、亚毫秒级重构速度 [p50]
  - 现有3D-MEMS类OCS方案多为每1U 32–40端口，导致2U/4U/8U机架单元（页面原文）；对比厂商含 Coherent（Triple-Stone 320x320，中国）、POLATIS(H&S)、Eoptolink、Molex 等 [p51]
  - 芯片：ONE-32，增益控制硅光OCS，严格无阻塞32端口，偏振透明，>4,000个集成开关单元，兼容WDM光学，片上遥测 [p57]
  - 芯片代际：32x32（约2,000单元）、32x32 v2（约4,000单元/4,000驱动信号）、64x64（约6,000单元，偏振透明）、>100端口（约10,000单元，设计中，标注2027，25x25 mm²）；管芯尺寸20x23 mm²（各代具体对应关系看不清）[p58]
  - 与Lumentum 1.6Tbps 2x DR4（200G/lane）retimed硅光收发器（BER 1e-12）联测：OCS增益10 dB；前置VOA 0–3 dB，后置VOA 0–10 dB网络损耗仿真；相对10^-12基线BER劣化约1个数量级（页面原文“1-decade BER degradation from 10^-12 baseline”）；图中典型工作窗口接收功率约0到+4 dBm，BER平台约10^-11；对前后网络损耗稳健 [p60]
  - 3 dB分路器/交叉损耗随PDK迭代下降（波长1280–1340 nm，具体数值看不清）[p56]
  - 系统卖点：2x链路成本降低、嵌入式链路增益与遥测、ps级时间（原文“ps-time”，含义不明）；生态问题：CW-WDM MSA？OCI-MSA？波长数、栅格、速率、方向性 [p61]
- 提到的公司/客户/产品/标准：iPronics ONE32/ONE Series、Lumentum、Coherent、POLATIS、Eoptolink、Molex、CW-WDM MSA、OCI-MSA、NPO/CPO/光互连器件；引用 npj Nanophotonics 3, 8 (2026)、JLT 44 (2026) [p48][p53]
- 与业界对比或记录声明（SOTA/首次/record）：标题声明“Industry-first results of link-quality of 1.6 Tbps transceivers for AI datacenters over gain-controlled silicon-photonics OCS” [p60]
- 推荐配图页：p60（OCS+Lumentum 1.6T收发器BER曲线，行业首次）；p58（OCS芯片代际与开关单元数）；p50（scale-up扩展用OCS的规格三要点）

### 0923-We-F-Verizon-光纤传感标准化.pdf
- 讲者/机构：Jun Shan Wey，Verizon | 题目：Distributed Fiber Optic Sensing (DFOS) Use Cases and Industry Standards（ITU-T ION-2030 Symposium，马拉加，2026-09-23）| 类型：邀请报告/标准
- 方向归属（主/次）：主 6 QKD/量子/光纤传感DAS；次 1 长途/DWDM共存，5 接入（PON中DFOS）
- 核心主张：
  - DFOS在电信网中的用例：光缆/光纤识别、光缆映射与监测；用一名现场工程师敲击光缆并看手机App即可识别，替代传统多人在CO与现场手工检查标签/颜色 [p3]
  - ITU-T G.681 是首个用于在役陆地光网络的DFOS标准（2025年11月）；仍需成本降低（DFOS集成到线卡/可插拔？）、控制管理接口与数据模型标准、前馈DFOS互操作 [p12][p14]
- 关键数据：
  - Verizon需求：暗纤和在役光纤；在DWDM频段内或带外波长；不干扰业务流量；定位精度<10米；光纤距离>50 km；风险等级评估方法；及时向运维告警；行业标准降本以便大规模部署 [p6]
  - 技术分类：背散射DFOS（Brillouin/Raman/Rayleigh；定位精度<10 m，光纤距离最长100 km，独立系统，不能穿过在线放大器）；前馈DFOS（定位精度>100 m，距离无限制，内建功能，可穿过在线放大器；CM-PPE、MMSE-PPE；单向/双向相位/偏振）；G.681新增附录（贡献C-1017，SG15全会，蒙特利尔，2026年7月）[p10]
  - G.681：系统配置为背散射DFOS，前馈DFOS作资料性附录；光纤类型G.652/G.654/G.657；波长分配：带外S/L/U波段，带内C/L波段；光接口参数为对DWDM信道所需OSNR和灵敏度的影响 [p12]
  - 非线性干扰：反向传播场景XPM代价可忽略；同向传播时常规脉冲的XPM主导，引起BER误码及相邻DWDM信道载波相位突跳；缓解：DFOS探测信号序列整形（Adtran）、更长上升/下降沿脉冲降低OSNR代价（都灵理工）；探测信号为BPSK调制PRBS，125 MBaud，2048b/4096b/2048b（16.4 µs/32.8 µs/16.4 µs）；图中同向CC-OTDR开启时，QPSK出现BER平台（约10^-7量级，图上估读），整形后消除 [p13]
  - 结语指标：无在线放大器下感知距离最长50 km；定位精度<10 m；对在网数据流量无影响 [p14]
  - 研究方向：提高前馈DFOS定位精度；实现同向传播背散射DFOS；在背散射DFOS中识别分光器后的PON分支 [p14]
  - 标准生态：FOSA、SEAFOM、IEC SC86C、IEEE 3101-2023（DAS术语）、CIGRE、FSAN；ITU-T SG15 Q2（接入）/Q6（城域、长途）/Q7（光纤光缆）/Q8（海缆），涉及L.302、L.316、L.391、G.979、G.681、G.Sup88 [p7][p11]
- 提到的公司/客户/产品/标准：Verizon、NEC（图片来源）、Adtran、Politecnico di Torino、ITU-T G.681 / G.979 / L.302 / L.316 / L.391 / G.Sup88、IEEE 3101-2023、参考文献 JLT Aug 2025、JOCN SI 2026（Wakisaka等）
- 与业界对比或记录声明（SOTA/首次/record）：G.681为首个在役陆地光网络DFOS标准 [p12]
- 推荐配图页：p10（DFOS技术树与背散射/前馈两类的距离精度对比）；p13（同向传播XPM导致BER平台及整形缓解）；p12（G.681配置示意）

## 本批小结
1. OCI-MSA（2026年3月）成为scale-up光互连共同PHY的核心：NRZ+WDM+Bi-Di单纤，Meta/Microsoft/OpenAI/AMD/NVIDIA等参与，并与OIF（ELSFP、CMIS）、OCP（光托盘/机架）、APC（SiP晶圆到系统）分工协同；速率路线为200G今天、400G约2027(?)、800G >2030(?)（来自Microsoft Karinou讲稿、iPronics p61也提出OCI-MSA/CW-WDM MSA生态问题）。
2. OCS从“替代super-spine”与“scale-up扩展”两个角度同时被推进：中国电信称OCS替代super-spine可降约20%网络功耗、故障率降17%+，规模可达百万GPU；iPronics提出硅光OCS约\$100/port、亚毫秒重构、32→64→>100端口路线，并给出与Lumentum 1.6T收发器联测（BER约劣化1个数量级）（来自中国电信、iPronics两篇）。
3. Scale-across/DCI已有运营商实测数字：中国电信跨城3个DC、1024 GPU分布式训练效率>97%，WSON恢复<50 ms、单波400/800G、最长路由640 km（中国电信讲稿）。
4. AI流量与AI运维成为标准化主线：Omdia预测AI流量2033年占62%（中国电信引用），WBBA给出2025–35年各类流量CAGR；Telefónica提出读写分离的多Agent+MCP网关框架并以ZR+开通为例（WBBA、中国电信、Telefónica三篇）。
5. 接入与感知方向：ETSI F5G-A→F6G（Release 5起，含OSV光感知1米定位、GRE L4自治）与Verizon的DFOS（G.681已发布，前馈DFOS与PON分支识别待研究）共同体现“网络即感知平台”的趋势（ETSI F5G、Verizon两篇）。
6. 注：本批几乎全为CamScanner翻拍的标准化专场讲稿，OCR质量差；WBBA、中国电信、ETSI三讲的讲者姓名/标题页未见，已如实标注。
