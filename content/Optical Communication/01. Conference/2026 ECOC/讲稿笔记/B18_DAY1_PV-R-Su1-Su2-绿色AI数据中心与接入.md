---
title: "B18 · DAY1 · PV-R-Su1-Su2-绿色AI数据中心与接入"
tags:
  - ECOC2026
  - DAY1
---

# B18 笔记：ECOC 2026 Workshop「Scaling Sustainable AI Data Centers and Green Access Networks」（PV-R 会议室，9月20日上午）

说明：本批为同一场 Workshop 的 8 位邀请讲者。页码为 PDF 页码。数值取自图片核对；OCR 对 Orange/NVIDIA 等自定义字体页基本不可用，未看图的页仅用 OCR 且已标注。

### 0920-am-Su1-I-01+02-主席+Telefonica-开场与运营商基础设施路线.pdf（第1–6页为主席开场，第7–14页为 Telefonica 讲稿）
- 讲者/机构：Juan Pedro Fernandez-Palacios（Head of Transport, Telefonica CTIO）；开场为 Workshop 组织者 S. Spadaro (UPC)、P. Parolari (Politecnico di Milano)、M. Svaluto Moreolo (CTTC)、J. Potet (Orange) | 题目：Operator perspective on network infrastructure and roadmap towards scalability and sustainability | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [2 Scale-across/跨楼园区（运营商边缘AI互联）]；次 [5 固定与无线接入 PON/AI-FAN]
- 核心主张：
  1. 部分面向 AI 的用例只有拥有边缘计算资源的电信运营商才能提供 [p14]
  2. 主要驱动力：变现（Monetization）、网络资源优化、数据主权（Data Sovereignty）[p14]
- 关键数据（本讲无定量数据，均为架构示意）：
  - 开场页给出 Workshop 形式：9:00–12:30，两个 90 分钟单元，8 个 15 分钟邀请报告，末尾 11:45–12:30 小组讨论 [p2, p5, p6，OCR]
  - Telco Edge 架构：企业/医院/银行的客户边缘 DC 通过 PON（ONT）或 P2P/P2MP 光连接，接入 Edge-AI OLT / Optical PE，经汇聚环连到 Telco Edge IT 与 Telco Core IT，标注"Distributed GPUs" [p8]
  - 四种 Zero Trust / Trusted Edge LLM 推理场景：客户本地推理（无特殊连接需求）、分布式推理（客户与运营商边缘 AI DC 联合，联邦学习）、解耦推理（存储/计算，客户侧无计算，需"高容量、零丢包"连接）、解耦+分布式（微型数据中心间基于光连接做负载均衡，标注 RDMA）[p9–p12，OCR，图未细看]
  - Trusted Edge LLM：大量推理数据（如机器人控制视频流）传到 Telco Edge [p13，OCR]
- 提到的公司/客户/产品/标准：Telefonica；OTN；PON；RDMA；场景客户举例：医院、银行、工业
- 与业界对比或记录声明：无
- 推荐配图页：p8（Telco Edge 架构：客户边缘 DC 经 PON / P2P-P2MP 光连接至 Edge-AI OLT、Optical PE、汇聚环与核心网，标注 Distributed GPUs）

### 0920-am-Su1-I-03-Orange-接入网节能.pdf
- 讲者/机构：Fabienne Saliou（Orange Research；合作者 J. Potet, S. Le Huérou, P. Chanclou, G. Simon）| 题目：Optical Access Networks & Energy-Saving | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [5 固定与无线接入 PON/FTTR/AI-FAN/RoF/FSO]；次 无
- 核心主张：
  1. Orange 集团 2025 年目标已达成，接入网减碳靠循环经济（翻新）、优化网络（分光比提升、休眠）与运维创新三条线 [p6, p9, p11, p15, p17]
  2. "0 Watt at 0 bit"：ONU 的 Doze/循环睡眠/警觉睡眠模式目前在多数网关中未实现，需要运营商提出市场需求 [p15]
- 关键数据：
  - 碳足迹构成（GHG Protocol）：Scope 1 为 7%，Scope 2 为 10.5%，Scope 3 为 82.5%；约 4.9 Mt CO2eq（2025）[p4]
  - 2025 目标达成：Scope 1+2 较 2015 年 -49.3%，Scope 3 较 2018 年 -16.4%；2025 年集团 54% 电力来自可再生能源；法国 FTTH 覆盖 93%（2030 年光缆敷设较 2020 年 -90%）；2030 年铜线 100% 退出；2040 净零 [p6, p7]
  - 法国数字行业 CO2（ADEME-ARCEP 2022）：终端 78%，数据中心 16%，网络 6%；Orange France 2023 CO2：网络 50–60%，终端 15%，数据中心 5–10%；Orange France 2023 能耗（仅 Scope 2）：移动网 43%，固定接入 20%，城域/核心 17%，数据中心 6%，第三方运营商 10%，第三级 4% [p7]
  - 翻新网络设备制造阶段排放较新设备 -90%（Carbone 4 验证）；本地翻新项目自 2020 年约 1950 万台光网关/机顶盒（原文"~19,5 millions"）；光缆制造碳排放对比欧盟：美国 +30%，中国 +48%，印度 +85%；2024 年试验用帆船货运网关与机顶盒运输 CO2 -90%（25000 km，约 20 km/h）[p9]
  - 翻新占比表（页内表格，讲者未必逐项讲）：企业级 1G/10G/25G 二手市场约 40%；100G 约 25%；400G/800G/1.6T 约 0% [p9，小字，较难辨认]
  - 在法国用 G+XGS-PON Combo 卡并把分光比提到 1:128（对比 1:64 GPON）降低新增 OLT 卡数量；50G-PON 引入（三模 MPM 模块）图中标注 -17%、-50%（图例含 1:64/1:128/1:256 与 GPON 卡翻新与否，具体基准看不清）；分光比 1:256 需光预算 >35 dB，突发时序开销 >30%（含 FEC）[p11]
  - ONU 内部功耗占比：GPON 网关中 ONU 12%、交换/路由 35%、Wi-Fi 49%、Ethernet 4%；XGS-PON 网关中 ONU 12%、交换 36%、Wi-Fi 39%、Ethernet 14%；MPM 收发模块 3.5 W/OLT；关激光时长 0/9/12/15/18 h 每天，节电百分比图中标 7%→15%、10%→20%、13%→25%、15%→30%（读图，对应关系需谨慎）[p15]
  - 高密度光缆：光纤外径 250→200 µm（涂覆减 30%），FTTH 光缆 CO2 -10%，用翻新材料最多 -20%；同外径 23 mm 下 2000/3000/4000 芯（250/200/200 µm，节距 250 µm）（Prysmian 2026）；网关红光识别，技术员手机检测约 3 秒；2025 年节省 20% 现场作业 [p17]
- 提到的公司/客户/产品/标准：Orange、Orange Energies、Carbone 4、Prysmian、GPON、XGS-PON、50G-PON、G.Suppl.45（Nokia 讲稿提及）、ECOC 2024/2025 及 OFC 2025/2026 自引论文；展台 Demo：FTTx Focus area, Pavilion 1；We5-E4（9月23日 18:00）"Experimental Evaluation of Energy Saving in XGS-PON ONU"（Chanclou）
- 与业界对比或记录声明：无 SOTA 声明；"2025 objectives are reached" [p6]
- 推荐配图页：p15（Doze/循环睡眠/警觉睡眠时序图 + 节电柱状图）；p11（分光比与 50G-PON 引入的 CO2 曲线）

### 0920-am-Su1-I-04-Nokia-下一代PON架构.pdf
- 讲者/机构：Rene Bonk（Nokia Bell Labs，据 p5 议程页；标题页看不清）| 题目：Next generation PON architectures and systems for sustainable connected intelligence | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [5 固定与无线接入 PON/FTTR/AI-FAN/RoF/FSO]；次 无
- 核心主张（p13 Key takeaways）：
  1. 固定宽带生命周期足迹以运行能耗为主；PON 因大量无源基础设施已是能效最高的宽带接入架构之一
  2. 未来节能主要来自自适应运行（休眠模式、灵活传输配置、AI 辅助优化）
  3. 下一个挑战不只是每比特能效，还要限制绝对网络功耗（AI 驱动流量持续增长）
- 关键数据：
  - 固定网络产品生命周期 GHG：使用阶段 89%，生产 10%，运输 2%，报废 -1% [p2]
  - 每有用比特能耗估计（欧盟 JRC 宽带设备行为准则 v9.1，2025；25GS-PON 为估算值）：GPON 约 55 nJ/bit（读图）→ XGS-PON 约 -70% → 25GS-PON 再 -55% → 50GS-PON 再 -30% [p5]
  - 每用户功耗（EU Code of Conduct v9.0/9.1）：VDSL 17a vectored 4.7 W；GPON 3.0 W（1:64）；XGS-PON 4.6 W（1:64）；固定无线 5G FR1 5.6 W（不含基站）；2026 年 PON 占全球 16 亿固定宽带用户约 73% [p7]
  - 光局域网/数据中心 OOBM：Optical LAN 布线少 70%、寿命 50+ 年、功耗低 40%；OOBM 用 PON 比 P2P 传输能效约 5 倍，功耗最多低 50%（OCR 提取，图未核对）[p8]
  - 节能手段：关闭未用端口/ONU 打盹与睡眠、近零负载休眠、按负载调整资源、调整分光比（引 L. Breyne "Optical switching in PON", OFC 2026；G.Suppl.45, 2022）[p9]
  - ITU-T SG15/Q2 新增补充 G.sup.PONcoop（Combo OLT/ONU 协作机制），目标定稿日期 2028 年 7 月，研究内容含 ONU 切换与启动的节能机制（OCR）[p10]
  - AI 使能网络能效：遥测→AI 预测→控制（OCR）[p12]
- 提到的公司/客户/产品/标准：Nokia；ITU-T G.Suppl.45、G.sup.PONcoop；EU Broadband Equipment Code of Conduct；GPON/XGS-PON/25GS-PON/50GS-PON；Optical LAN；OOBM
- 与业界对比或记录声明：无
- 推荐配图页：p5（GPON→XGS→25GS→50GS 每比特能耗逐代下降 70%/55%/30%）；p9（流量波动与功耗静态对比 + 四类节能手段）

### 0920-am-Su1-I-05-DTU-ICT可持续性评估.pdf
- 讲者/机构：Leif Katsuo Oxenløwe（DTU Fotonik / SPOC）| 题目：The Need for environmental sustainability assessment of ICT technologies and services | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [1 相干/海缆/长途/DCI/AI光网络/oDSP/高波特率器件]（地面长途/海缆的"数据分布"节能）；次 [5 固定与无线接入]（可持续性评估方法）
- 核心主张：
  1. 能耗规模已很大，需要准确度量以制定可持续策略；ICT 碳核算应从"花费法"转向"活动法"（基于实际产品和使用、需要准确 LCA 数据）[p4, p5]
  2. 即便电力很绿，瑞典光纤网络按行星边界评估仍不可被认为可持续 [p11]
  3. "数据分布"概念（把同一容量分摊到更多光纤/纤芯）用更低 SNR，可拉大放大器间距，减少放大器与机房 [p13, p16, p18]
- 关键数据：
  - ICT 用电：数据流量年增约 20%；ICT 占全球电力 5–10%、CO2 2–4%；AI-DC 主导，约 +10%/年；COP28/EU 要求能耗每年 -4%（Ericsson Jens Malmodin @ECOC 2025 图）[p4]
  - 95% 的 ICT CO2 核算为花费法（kg CO2e/€），5% 平均法；示例：旧交换机 1000 € 与新交换机 2000 €，系数同为 0.3 kg CO2e/€，得 300 与 600 kg CO2e；花费法误差约 70% [p5]
  - 海缆 LCA（Pasek 等，SubOptic 2025）：跨太平洋/跨大西洋，海上安装排放最大，跨太平洋约 63000 t CO2e，跨大西洋约 34000 t（读图）；寿命期每 10 TB·km 约 3–5 mg CO2，较 2009 年低 1000 倍；未含中继器与陆上设备 [p7]
  - 瑞典陆地网 2024 年排放构成（Gudmundsdottir 等，ICT4S 2026，图例配色与百分比对应有不确定性）：数值为 33%、23%、18%、11%、10%、3%、1%、0%、0%，讲者结论"安装和隐含 CO2（资源与设备）负担最大" [p9]
  - AESA（绝对环境可持续性评估）：以人均等份与碳预算（EPC&CB）为基准，瑞典全部网络基础设施气候变化阈值约 10,200 t CO2eq/年（固定+移动），该网络占用 56%；资源（矿物金属）使用比值约 3.4，即约 3 倍于可用资源 [p11]
  - 数据分布：容量公式 C=B·log2(1+SNR)，分成 m 根光纤 SNR_m=(1+SNR_1)^(1/m)-1；50 km 跨距→150 km 跨距，约 40% 节省 [p13]
  - 陆地长途"跳站（hut skipping）"：1→2 根光纤（或双芯光纤），3000 km 链路机房间距 80→193 km，节省 45% 放大器、72% 机房；500 km 链路 80→247 km，节省 64% 放大器、80% 机房 [p16]
  - 网络运营商数据：光层功耗（节点、EDFA 输出、收发）随光纤对数变化，10 对基准 1.0，约 18 对时最低约 0.57，>40% 降低；之后随对数增加回升到约 0.73（32 对）[p18]
  - 海缆 wet plant 成本模型（Hedeboe 等，SubOptic 2025）：至 11000 km，16–24 光纤对比 12 对便宜（中继器与 EDFA 少）；11000–13000 km，16 对最便宜 [p14，OCR]
- 提到的公司/客户/产品/标准：Ericsson、Rejoose、SPOC、ISO 14040、ITU-T L.1410、ADEME PCR、Meta（海缆成本模型页）、ASN/OMS/Orange Marine/NEC（海缆碳足迹合作者）；论文 S. Swain 等 JLT 2025；Gudmundsdottir 等
- 与业界对比或记录声明：海缆碳强度较 2009 年低 1000 倍 [p7]
- 推荐配图页：p16（跳站示意 + 3000 km/500 km 节省放大器与机房比例）；p18（光层功耗随光纤对数的下凹曲线，>40% 降低）

### 0920-am-Su1-I-06-TUe-光子集成交换省能.pdf
- 讲者/机构：Nicola Calabretta（TU/e，Eindhoven；PhotonDelta 支持）| 题目：Photonic integrated switching solutions for energy-efficient high-capacity interconnects networks | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]（光子集成 WDM 交换/OCS 类）；次 [5 固定与无线接入]（6G 城域接入 X-haul 动态重构）
- 核心主张（p19 Conclusions）：
  1. 借助快速受控光交换实现动态可重构的城域-接入架构，支持故障、降级、负载均衡、时延优化、无小区 RAN、RU/DU 簇重构、频谱效率和带宽自适应
  2. 光子集成 OADM：单片（InP 与 3 µm 厚硅光）与 InP/SiPh 混合两种路线
  3. 模块化、偏振无关的 WDM 波长交叉连接（WCS）交换，迈向 PLC-SiN/InP 混合集成
- 关键数据：
  - X-haul 分割需求：Split 5：21.4–40.3 Gbps/RU，<100 km，1 ms；Split 7.2：38–142.8 Gbps/RU，<20 km，200 µs；Split 8：200–850 Gbps/RU，<20 km，200 µs；Split 8 在 1.6 GHz 带宽下每个 horseshoe 子网约 30.6 Tbps [p2]
  - 新一代城域接入挑战：带宽 25–800 Gbps 可变，聚合多 Tbps [p3，OCR]
  - 400G 快速受控光交换实现 RU-DU 动态重构，论文 Mo3.A-4（A. Bahari 等）[p4，OCR]
  - InP 集成 OADM：芯片尺寸 4.6 mm x 4 mm，8 波，通道间隔 2.4 nm；40 Gb/s NRZ-OOK（PRBS 2^15-1），开关比 >30 dB，估计片上增益约 10 dB；8 通道 BER 曲线在 -4 dBm 附近与背靠背有功率代价，读图 BER 达 1e-8 需约 -5 至 -4 dBm，B2B 在 -6 dBm 时约 1e-11 [p8, p9]
  - 3 µm 硅光 OADM：1x12 AWG，覆盖 S 至 L 波段，插损 7.1 dB，平均消光比约 18.5 dB，上升 4.2 ns、下降 2.4 ns，芯片 10 mm x 7.9 mm [p10, p12]
  - InP/SiPh 混合 1xM WDM 交换：8 通道 BER 在约 -32 至 -24 dBm 范围，通道之间偏差约 1 dB 量级（读图，未提供定量指标）[p15]
  - 32x32x8λ 混合 PLC/III-V WDM 交叉连接（O 波段，100 Gbps/λ）：非阻塞，SOA 补偿，PLC 平顶 AWG 串扰 <45 dB；图中 BER 以 KP4 FEC 2e-4 为门限，32x32x8λ WCS 的 BER 在 ROP 约 -8 dBm 附近触及门限，其后平坦在约 4e-5，对比 BTB 更低（论文 We4-P，B. Zheng 等）[p16]
  - 混合集成 WSC（PLC/SiN + InP SOA 阵列）：光纤到光纤增益最高 12 dB；KP4 处功率代价 <0.65 dB [p17, p18]
  - 演示：Tu2-Ex11 展台演示"Telemetry-assisted QoS-aware scheduler over SOA-based time-slotted optical metro-access networks"（S. Ghasrizadeh），主节点 + 可重构快速 WDM 交叉连接 [p6, p7，OCR]
- 提到的公司/客户/产品/标准：TU/e、SONL（smart optical network lab）、PhotonDelta、Horizon Europe（grant 101070178）、KP4 FEC、O-RAN 分割 5/7.2/8
- 与业界对比或记录声明：无 record 声明
- 推荐配图页：p16（32x32x8λ 混合 PLC/III-V WDM 交叉连接架构与 BER）；p17（混合集成 SOA 阵列：最高 12 dB 增益、<0.65 dB 功率代价）

### 0920-am-Su2-I-01-NVIDIA-面向AI工厂的光子技术.pdf
- 讲者/机构：议程列 Bakopoulos（NVIDIA，名字前半看不清；本讲首页未拍清）| 题目：Photonics-enabled technologies for AI factories | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]
- 核心主张（p10 Recap、p20 Outlook）：
  1. 数据中心受可用功率限制，需要光学创新做到节能且可靠的数据生成，以及自动拓扑自适应以绕开故障并匹配流量
  2. 光学社区的机会：每一级集成降低 pJ/bit（今天 CPO，DWDM/OOI 在地平线，OCS 带来灵活拓扑）；用 OCS 重构把故障变成重路由；解决 scale-up 前沿，将机架外的铜替换为光
  3. 极致的器件、封装、系统、拓扑协同设计
- 关键数据：
  - 生成式→推理→智能体 AI 需要低延迟、高吞吐（GPT-OSS 2T，上下文/输入/输出长度 400K/4K/8K）[p3]
  - GPT-3.5 级推理成本 2022 年 11 月=100 降到 2024 年为 0.36，>280 倍降幅（Stanford AI Index/Epoch 公开价）[p4]
  - 512K 个 Blackwell GPU 数据中心：1200 W TDP 共 600 MW 仅 GPU；scale-up：机架内 72 个 GPU 用 NVLink，900 GB/s 每方向；scale-out：约 7100 个机架用 CX8 NIC 组成 3 层 fat-tree（IB/Ethernet），200 GB/s 每方向；约 1.8 M 光收发器 [p5]
  - 光网络功耗约占计算资源的 10%；10 万服务器：传统云数据中心收发器功耗 2.3 MW，AI 工厂 40 MW [p6]
  - Scale-up 限制：GPU 带宽 2.4→3.6→7.2 Tb/s（每两年 2 倍）；GPU 域 8→32→72→100s（每两年 2–4 倍）；机架功率密度 25 kW→150 kW→1 MW；GPU-L1 距离 0.5 m→1.5 m→最多 30 m（原文带问号）；"Cu reaches its limit" [p8]
  - 1.6T 光学选项（pJ/b，功耗）：FRO 14，25 W；TRO 10，18 W；LPO 6.4，11 W；LPO w/ CPC 6.4，11 W；CPO 4，7 W [p11]
  - CPO（Spectrum-X Ethernet Photonics 共封装硅光）：可插拔电信号损耗 22 dB（连接器、PCB、基板）、25 W；CPO 4 dB（基板）、7 W；标题 3.5 倍节能、10 倍韧性；每 1.6T 用 2 个 CW 激光器 [p12]
  - 未来 DWDM：硅光 3.5–4 pJ/b（含激光器）；起步 8λ DWDM 微环，50 Gbps PAM2，每纤 400G；光学 BiDi 再 2 倍 [p13]
  - Optics on Interposer（OOI）：硅中介层带来 3 倍滩头（beachfront）密度、10 倍面积密度；中介层尺寸有限 [p14]
  - OCS 落地四道障碍：插损（目前路径至少 4 个 bulkhead 连接器；DR4 余量 3 dB，FR4 余量 4 dB）；成本（目标每 1RU >256 双工端口）；可靠性（故障半径、FIT，不能劣化 BER/FEC 余量）；端口密度（机架需要千级 OCS 端口）[p18]
- 提到的公司/客户/产品/标准：NVIDIA、Blackwell、NVLink、CX8 NIC、Spectrum-X、InfiniBand/Ethernet；GPT-OSS；LPO/TRO/FRO/CPO/CPC；DR4/FR4；FIT
- 与业界对比或记录声明：无 SOTA 声明；含 NVIDIA 自身对比（CPO 相对可插拔 3.5 倍节能、10 倍韧性）[p12]
- 推荐配图页：p11（FRO/TRO/LPO/LPO+CPC/CPO 的 pJ/b 与 1.6T 功耗对比表）；p18（OCS 落地四大障碍）；p12（可插拔 vs CPO 的路径损耗与功耗）

### 0920-am-Su2-I-02-UCDavis-光交换与光计算.pdf
- 讲者/机构：S. J. Ben Yoo（UC Davis，Next Generation Networking & Computing Systems Laboratory）| 题目：Photonic Switching and Computing in Future AI and Data Systems | 类型：邀请报告（Workshop）
- 方向归属（主/次）：主 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]（全对全 AWGR 与可重构 LION）；次 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]（3D EPIC、光互连内存）
- 核心主张（p21 Summary）：
  1. 异构可重构计算（领域专用计算混合，约 50 倍）提供高吞吐高能效
  2. 可重构全对全互连对 MoE Transformer 重要（光可重构互连较电可重构交换吞吐约 100 倍，但突发模式接收机很重要）
  3. 嵌入光子的 3D EPIC 提供确定性低时延内存与解耦计算
- 关键数据：
  - 领域专用计算可达 50 倍能效与吞吐；MoE 参数利用率约 1–10%（Top-K 专家），稠密 Transformer 100% [p2, p4]
  - Thin-CLOS LION：1024x1024 全对全，用 256 个 64x64 AWGR（N=1024, W=64, M=16），Yoo 等 OFC 2026；32x32 硅光 Thin-CLOS（N=32, W=16, M=2，16x16 AWGR），Mingye Fu 等 OPEX 2023；Thin-CLOS 光线数 2NM，单 AWGR 为 2N，无 AWGR 为 2N(N-1) [p6]
  - 3D Hyper-FleX-LION：524,288 节点、电交换机基数 k=128 下功耗较 Fat-tree 降低 3 倍；图中功耗约 15 MW→约 5 MW；表格 k=32：Fat-tree 765.7 kW，3D-Hyper-LIONS 68 kW，3D-Hyper-FleX-LION 70 kW（表格小字，标题与正文 k 值不一致，以图读）[p8]
  - 电学 DVFS：在 10% 负载附近，每有用比特多余能耗 w/o f&V scaling 约 5 倍（8% 吞吐处）→ 带频率与电压缩放及源同步接近 1 倍；总结中称 10% 负载约 10 倍能效提升；Fat-tree 3:1 超额订阅延迟远高于 DVFS [p9, p21]
  - SiPh-FGDRAM：DRAM 访问能耗较 HBM2 约 3 倍下降（HBM2 约 4.7 pJ/bit，SiPh-FGDRAM 约 1.6 pJ/bit，读图）；尾延迟总结 6 倍下降；SiPh 收发器功耗 4.44 mW（278 fJ/b）[p11, p21]
  - 首个 3D 混合键合（HBI）EIC-PIC 收发器：496 fJ/bit（含 8:1 SerDes 与调谐），18 Gb/s，总 8.933 mW；可扩展到 1 Tb/s/光纤；12 nm FinFET EIC；另两组含激光驱动的链路总功耗：22.705 mW，1.261 pJ/bit；30.345 mW，1.686 pJ/bit（18 Gb/s，Chang 等 JLT 2023；Samanta JSTQE 2026）[p12]
  - 接收灵敏度：总输入电容 28 fF（PD 约 9 fF，DBI 封装约 5 fF，放大器 14 fF）时 OMA 灵敏度 -19 dBm（估计，PD 响应度 0.8 A/W，跨阻极限）；100 fF 时 -12.9 dBm；3D 混合键合带来 6.1 dB 光功率降低，新型 nanoPD 再增益 11.3 dB [p13]
  - 总结：混合键合降低光功率 4 倍，配合 nanoPD 与优化 EIC 为 20 倍；激光墙插效率 30%→10% 可再降 3–10 倍；光电脉冲神经网络能效 10^6 倍（讲者总结页）[p21]
  - nanoPD（GF 45SPCLO 单片）：记录低电容 0.08 fF，暗电流 0.72 nA，量子效率 91%（OCR，来自 p14）
- 提到的公司/客户/产品/标准：UC Davis；GlobalFoundries 45SPCLO；HBM2/FGDRAM；AWGR、LION、Flex-LION；SC'20 论文（Gengchen Liu 等）
- 与业界对比或记录声明："The first 3D Hybrid-Bonding Integrated (HBI) EIC-PIC Transceivers at 496 fJ/bit" [p12]；nanoPD "Record Low Capacitance (0.08 fF) and Dark Current (0.72 nA)" [p14，OCR]
- 推荐配图页：p12（首个 3D 混合键合 EIC-PIC 收发器 496 fJ/bit 架构、照片与功耗饼图）；p8（3D Hyper-FleX-LION 功耗 3 倍改善）；p21（总结）

### 0920-am-Su2-I-03-iPronics-可扩展光子集成ScaleUp.pdf
- 讲者/机构：议程列 Ana Gonzales（iPRONICS，Ana Gonzalez 拼写以议程为准）| 题目：Scalable Photonic Integration for energy-efficient scale-up AI networking | 类型：邀请报告（产业发布式 Workshop 讲稿）
- 方向归属（主/次）：主 [4 Scale-up/in CPO/NPO/XPO/WSE/OCS]；次 [3 Scale-out 224G/448G/光源/调制器/电芯片/OCS]
- 核心主张：
  1. 用 OCS 减少 E/O 转换次数即可降低 AI 集群功耗；EPS+CPO 仍需 E/O 转换，扁平 OCS scale-up 功耗最低 [p2, p3]
  2. 标准硅光（含 SOA 增益）即可实现低成本、可量产、高可靠的 OCS，可兼容可插拔、NPO、CPO、光 I/O 与光中介层 [p14, p16]
- 关键数据：
  - 三种 scale-up 拓扑（机架内 EPS+CPO 加机架间 OCS / 扁平 EPS / 扁平 OCS）功耗依次递减；OCS 需要新的编排器、NCCL、SDN 控制器支持（正在开发）[p3]
  - O 波段标准硅光低损耗单元：3-dB 分路器插损测量约 0.061 dB（DR4 @1310 nm），0.060 dB（ER4 LWDM），0.104 dB（FR4 CWDM）；单层交叉插损约 0.014 dB（DR4/ER4），0.016 dB（FR4），串扰 -61 dB（表内 DR4 项小字）；称比当前代工厂库模块好 10 倍 [p7, p8]
  - ONE 光网络引擎：PIC 交换损耗低（"Low loss 10 dB"），固态超高密度，切换 300 ps，SOA 阵列增益 8–12 dB（低 BER 劣化），集成监测 PD 阵列，软件 API 兼容数据中心控制软件（OCP 项目）[p11]
  - 芯片：ONE-32 与 ONE-64 光子芯片 [p9]
  - "行业首个"结果：经增益受控的硅光 OCS（iPronics ONE32，增益 10 dB）传输 1.6 Tbps（2x DR4，200G/lane）收发器，VOA1 0–3 dB、VOA2 0–10 dB 网络损耗仿真；BER 较 1e-12 基线仅降低 1 个数量级，对前后网络损耗稳健 [p12]
  - 功耗：30 W（系统）+ 0.78 W/激活通道；电交换机功耗随代际上升到 64x1600G 约 3500 W，iPronics <100 W（2027 年目标 <150 W）[p13]
  - 链路成本降低 2 倍；皮秒级集群重构（p16 原文 "ps-time"，p14 称微秒级响应，两处表述不一致）[p14, p16]
- 提到的公司/客户/产品/标准：iPronics（ONE32/ONE64、ONE Series）、OCP、NCCL、SDN、CPO/NPO、DR4/LWDM/CWDM、MEMS（对比）、Global Foundries（GF 10 出现在曲线图例，OCR）
- 与业界对比或记录声明："Industry-first results of link-quality of 1.6 Tbps transceivers ... over gain-controlled silicon-photonics OCS" [p12]；"10x better performance than foundry blocks available today"（分路器/交叉损耗）[p7]
- 推荐配图页：p12（OCS 上 1.6T 收发器 BER 曲线与测试结构）；p3（三种 scale-up 拓扑与功耗排序）；p13（电交换机功耗演进 vs iPronics <100W）

## 本批小结
1. 光互连以功耗为核心叙事，各讲给出了不同层级的 pJ/bit 或功耗降幅：NVIDIA 1.6T 下 FRO 14 → CPO 4 pJ/b（p11）；UC Davis 3D 混合键合 EIC-PIC 496 fJ/bit 且靠降低输入电容再获 6.1 dB（p12, p13）；iPronics 用 OCS 少一次 E/O，交换机 <100 W（来自 NVIDIA、UCDavis、iPronics）。
2. OCS 被 NVIDIA、iPronics、UC Davis、TU/e 同时视为 scale-up/scale-out 新拓扑的手段，但 NVIDIA 明确列出落地四障碍：插损、成本、可靠性、端口密度（DR4 余量仅 3 dB，FR4 4 dB）；iPronics 用 SOA 增益补偿并展示 1.6T 链路 BER 仅劣化 1 个数量级，TU/e 用 SOA 混合集成 WCS 得到最高 12 dB 光纤到光纤增益——"带增益的 OCS/WDM 交换"是共同技术路线（来自 NVIDIA p18、iPronics p12、TU/e p17）。
3. 铜到光的边界外移：NVIDIA 指出 GPU 带宽每两年 2 倍、域规模 8→72→100s、机架 1 MW，GPU-L1 距离需从 0.5 m 扩展到最长 30 m（原文带问号），Cu 达极限；CPO 现在、DWDM（8λ x 50G）与 OOI 在地平线（NVIDIA p8, p13, p14）；UC Davis 提出光 TSV、3D EPIC 与光互连 DRAM（UCDavis p11, p12）。
4. 接入网节能方向从"每比特更省"转向"绝对功耗与低负载运行"：Nokia 显示 GPON→50GS-PON 每比特能耗逐代 -70%/-55%/-30%，但强调绝对功耗；Orange 提出 0 W at 0 bit，但指出 ONU 睡眠模式在多数网关未实现，需运营商需求牵引（来自 Nokia p5, p9, p13；Orange p15）。
5. 可持续性评估的方法论提醒：DTU 指出瑞典光纤网的碳排放主要来自安装与隐含碳，不是用电，且 AESA 下资源使用约 3 倍超标；Nokia 生命周期中使用阶段占 89%，两者口径不同（产品使用 vs 整个网络基础设施），不宜直接对比；Orange 则以翻新（制造阶段 -90%）与减少新设备为手段（来自 DTU p9, p11；Nokia p2；Orange p9）。
6. 运营商视角的 AI 边缘：Telefonica 提出把 GPU 分布到 Telco Edge（Edge-AI OLT、Optical PE），驱动力为变现、网络资源优化、数据主权；Nokia 也把光纤接入定位为连接全球 AI DC 的手段（来自 Telefonica p8, p14；Nokia p12 OCR）。
