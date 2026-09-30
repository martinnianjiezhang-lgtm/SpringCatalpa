---
title: "B58 · DAY4 · We1-E-多芯多模光纤与表征"
tags:
  - ECOC2026
  - DAY4
---

### 0923-We1-E2-743-耦合芯MCF纵向空间模色散.pdf
- 讲者/机构：Chiara Lasagni（报告人）, Paolo Serena, Lucas A. Zischler, Giammarco Di Sciullo, Antonio Mecozzi, Cristian Antonelli, Alberto Bononi / University of Parma 与 University of L'Aquila（p1 看图核实） | 题目：Detecting Longitudinal Variations of Spatial Mode Dispersion in Coupled-Core Multicore Fibers via Four-Wave Mixing（We1-E2） | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI（SDM光纤表征）；次 无
- 核心主张：
  1. 提出检测耦合芯多芯光纤（CC-MCF）中空间模色散（SMD）系数纵向变化的方法。
  2. 方法仅需标准设备的四波混频（FWM）功率测量，无需 OTDR 类背向散射技术。
  3. 仿真和实验结果表明，该方法可有效指示沿光纤的异常 SMD 变化。[p13]
- 关键数据：
  - 数值设置：4芯 CC-MCF，11段熔接；0.17 dB/km，0.12 dB/熔接点；色散 20 ps/nm/km；非线性系数 0.35 1/W/km。[p6]
  - 链路总长 69.2 km；接收端加 AWGN，噪底低于音调功率 75 dB；1553 nm 处测芯平均FWM功率，按平均音调功率及 Δf=5 GHz 处数值归一化；结果对随机种子取平均。[p7]
  - 方法：以FWM残差最小二乘加正则项（惩罚端到端SMD错误、抑制偏离FWM较低的初值）估计各段SMD系数。[p5]
  - 异常段测试：标称SMD约2 ps/√km加小扰动，异常段8 ps/√km，模型可定位异常段。[p11]
  - 随机剖面：100个SMD剖面，随机选若干段，SMD在[1,10] ps/√km均匀取值；约85%被正确检出（估计标准差超过1 ps/√km阈值）。[p12]
  - 实验数据取自We1-E3论文：11段估计SMD约1–8 ps/√km（图上量级，逐点读数不精确），FWM随信道间隔在0–150 GHz约0至−37 dB（仿真真值），实验点在>60 GHz偏高至约−30 dB。[p8]
  - 双端方法：若光纤两端均可接入，可用两端数据得到互补视角。[p10]
- 提到的公司/客户/产品/标准：无（引用 Hayashi 等 OFCC19 的11段4芯CC-MCF；p-OTDR、相干OFDR为对比技术）
- 与业界对比或记录声明（SOTA/首次/record）：无record声明；声称相对p-OTDR/OFDR无需专用设备 [p2, p13]
- 推荐配图页：p8（实验+仿真SMD估计与FWM随信道间隔曲线）；p12（随机剖面检测准确率85%散点图）

### 0923-We1-E3-285-模色散致四波混频效率上升.pdf
- 讲者/机构：L. A. Zischler 等（据We1-E2页引用；讲者单位看不清，页面有校徽图标看不清） | 题目：Experimental Observation of Modal-Dispersion-Induced FWM Efficiency Increase and Non-linearity Coefficient Characterization in Deployed Coupled-Core Multi-Core Fibers（据E2页引用的题名） | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI（SDM光纤非线性）；次 无
- 核心主张：
  1. CC-MCF 的非线性通常随芯数增加而降低。
  2. 但模色散会使大信道间隔下的FWM增大。[p9]
  3. 在铺设的CC-MCF中实验观察到该FWM增强，并可据此表征非线性系数。
- 关键数据：
  - 实验：4台TLS经4×4耦合器（间隔±1、±2 Δfch）输入，40/60/80 m延迟线去相关，OSA测量；对比SMF与CC-MCF。[p5]
  - 光纤参数（SMF / CC-MCF）：α 0.246 / 0.227 dB/km；β2 −21.7 / −24.4 ps²/km；长度 74.1 / 69.3 km；Aeff 75 / 81 μm²。[p5]
  - SBS：归一化SBS峰值在每信道总功率约10 dBm以上SMF急剧上升（约15 dBm时约60 dB），MCF在约15 dBm仍较低。[p5]
  - 频谱：Δfch=12.5 GHz与50 GHz，MCF实验曲线与含SMD的SSFM吻合，而"SSFM×Anl (No SMD)"不含SMD预测偏低。[p6]
  - 归一化FWM噪声随信道间隔（约5–150 GHz）：小间隔时MCF比SMF低（如约10 GHz处SMF约−22 dB，MCF约−29 dB，图上读数）；约40 GHz以上MCF实验偏离无SMD解析线，在≥100 GHz约−52 dB，而解析线继续下降。[p7]
  - FWM增量随SMD：Δfch=50 GHz时，SMD约5 ps/√km实验点FWM增加约9.5 dB；SSFM趋势从SMD约0时约3 dB升至SMD≥10 ps/√km约13–15 dB（误差棒大）。[p7]
  - 理论：Manakov系数 κ≈4/3·(2N/(2N+1))；有效非线性 γ̄=2πf0n2/(cNAeff)，含模色散与相位匹配矩阵ρ。[p4]
- 提到的公司/客户/产品/标准：无（现网CC-MCF铺设于城市环路，页面示意接入点地图 [p5]）
- 与业界对比或记录声明（SOTA/首次/record）：题名含"实验观察"，暗示首次实验观察，但页面未见明确"first"表述；看不清
- 推荐配图页：p7（SMF vs CC-MCF归一化FWM噪声随信道间隔，及FWM增量随SMD）；p5（现网链路+SBS对比+光纤参数表）
- 备注：p7/p9 页码为文件页序，页面自带角标为6/9、9/9；OCR全为乱码，本节均基于图片。

### 0923-We1-E4-819-现网非耦合芯光纤长程双折射.pdf
- 讲者/机构：L. Romero 等（Università di Padova；合作方 Università degli Studi dell'Aquila，p6 页标看图核实） | 题目：英文原题页未拍到（中文文件名意为"现网非耦合芯光纤长程双折射"；内容为现网 L'Aquila 4 芯非耦合芯光纤(UCF)的分布式双折射表征，We1-E4） | 类型：学术论文
- 方向归属（主/次）：主 1 相干/海缆/长途/DCI（SDM光纤表征）；次 6 QKD/量子/光纤传感DAS（Rayleigh OFDR分布式测量）
- 核心主张：
  1. 偏振敏感光频域反射（PS-OFDR）可在现网部署的UCF中实现分布式双折射表征，支持真实SDM链路中的芯间偏振分析。
  2. 重建的双折射取向表现出很强的芯间相关，提示共同的截面/应力效应贡献于各非耦合芯的双折射演化，与此前实验室观察一致。[p11]
- 关键数据：
  - 手段：基于Rayleigh背向散射的PS-OFDR；用辅助干涉仪时钟信号做频率线性化，初始相干补偿窗口受辅助延迟限制（la=500 m时最大相干补偿约la/2≈250 m），再用分段相位噪声补偿延伸到整段光纤。[p5, p7]
  - 1.5 km 4C-UCF：各芯双折射模值均值/标准差（rad/m）：芯1 μ=1.9, σ=0.5；芯2 μ=2.3, σ=0.6；芯3 μ=1.7, σ=0.5；芯4 μ=2.7, σ=0.7；取向随距离累积约200+ turn，四芯曲线几乎重合，邻芯取向-参考取向为直线；标注旋转周期(SR)6.2 cm。[p8]
  - 平均模值与此前短距离实验室测量（同标称4C-UCF，R. Veronese et al., OFC 2021）同量级。[p8]
  - 6.3 km 4C-UCF双向询问叠加：两方向结果吻合，取向差标准差σΔθ约0.4 turn（3170–3230 m窗口）。[p9]
  - 多个独立补偿窗口（约z=1735至3228 m）显示各芯取向局部变化相关；参照G. Ocampo & K. Saitoh, JLT 44(12), 2026 的应力场（von Mises，约32–48 MPa）仿真解释。[p10]
  - 波段范围：可调激光器范围标为1540–1560 nm。[p5]
- 提到的公司/客户/产品/标准：无公司；引用 Hayashi et al. OECC/PSC 2019（UCF在O/C/L波段适用，CC-MCF为C/L）；J. Yang et al. Opt. Lett. 2025（PS-OFDR）
- 与业界对比或记录声明（SOTA/首次/record）：未见明确SOTA声明；从实验室短距（Veronese OFC 2021）扩展到现网1.5 km与6.3 km [p8, p9]
- 推荐配图页：p8（1.5 km各芯模值PDF与取向相关性）；p10（独立窗口取向相关+应力场仿真）

## 本批小结
1. 三篇同属We1-E（多芯/多模光纤表征）时段，共同点是把"现网铺设的SDM光纤"作为对象，而不只是实验室短样：E3在约69.3 km现网CC-MCF上测FWM，E4在1.5 km/6.3 km现网UCF上测双折射（E3、E4）。
2. CC-MCF的非线性是"总体更低但有例外"：E3实测小信道间隔FWM低于SMF，但模色散使大间隔（≥约40 GHz）FWM偏离无SMD预测，Δfch=50 GHz时SMD约5 ps/√km对应约9.5 dB增量；E2据此用FWM功率反演SMD（E2、E3）。
3. E2与E3互为链条：E3提供实验数据，E2提出低成本纵向SMD估计方法，无需OTDR；仿真中约85%的随机SMD剖面可被正确检出，但实验验证只是"提供有用指示"，成熟度较低（E2、E3）。
4. UCF中各芯双折射取向高度相关（E4），意味着芯间偏振行为并非独立，与应力共同来源相关；对多芯MIMO/偏振跟踪设计可能有意义，但讲者仅给出表征结论，未给系统影响量化（E4）。
5. 三篇均为光纤/表征层面，无商用产品与系统速率数据，与AI光互连主线关联较弱，主要面向长途SDM演进（E2–E4）。
