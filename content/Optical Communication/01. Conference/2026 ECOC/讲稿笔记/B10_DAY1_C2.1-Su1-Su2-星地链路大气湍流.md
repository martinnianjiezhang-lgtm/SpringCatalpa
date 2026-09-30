---
title: "B10 · DAY1 · C2.1-Su1-Su2-星地链路大气湍流"
tags:
  - ECOC2026
  - DAY1
---

### 0920-am-Su2-F-04-OGS-低轨相干链路自适应光学.pdf
- 讲者/机构：OGS Technologies / CNES / Safran DS / Bertin Alpao / Airbus 联合团队（讲者姓名看不清；幻灯片署名 FrOGS、CNES、OGS Technologies、SAFRAN、ALPAO、AIRBUS） | 题目：LASIN / FrOGS 在轨测试（IOT）结果，英文原题看不清（PDF 名指向"低轨相干链路自适应光学"；幻灯片标题含 "LASIN on-board CO3D""IoT Results (PAT)""IoT Results (O3K performance)"） | 类型：学术论文
- 方向归属（主/次）：主 5（FSO 自由空间光通信，卫星直连地面）；次 1（高波特率/相干接收，路线图提到相干检测）
- 核心主张：
  1. LASIN（经成像仪器发射的 Direct-to-Earth 激光通信演示，搭载于 CO3D 卫星）与法国光学地面站 FrOGS 联合在轨验证：捕获跟踪、重捕获、AO 闭环与单模光纤（SMF）注入均稳定。
  2. 下行 O3K（CCSDS 141.0-B2 / 142.0-B-2，LDPC，符号率 10 Gsps）在中等湍流下实测传输 Tb 级数据量。
  3. 路线图：SMF 注入已可支持向 100+ Gbps 相干检测演进；上行需 MEO 中继预补偿 / 预测预补偿 / 收发分离天线。
- 关键数据：
  - CO3D：ADS/CNES 星座，4 颗 LEO 卫星，50 cm 分辨率 3D 成像，2025 年 7 月发射 [p2]
  - LASIN 符号率 10 Gsps，O3K LDPC，CCSDS 141.0-B2 & 142.0-B-2 [p2]
  - FrOGS：2 个 50 cm 口径镜筒，Alt-Az 支架，2024 年 5 月投入运行，位于 Côte d'Azur 天文台；支持 O3K APD、O3K 预放大、DPSK、相干接收 [p3]
  - SMF 典型注入效率 40%；典型 ROP -35 至 -25 dBm；过顶天顶翻转重捕获 < 15 s [p5]
  - 2026-08-05：传输 1.38 Tb（幻灯片单位写 Tb），r0 = 20 cm [p7]
  - 2026-09-17：传输 1.62 Tb，error-free，r0 > 25 cm [p7]
  - 链路仰角约 20° 起，Aug 05 峰值仰角约 46°、Sep 15 约 34°（读自曲线，粗略）；调制编码在 1/2 SF8、1/2 SF1、9/10 SF1 间切换 [p5]
- 提到的公司/客户/产品/标准：CNES、Airbus (ADS)、Safran DS、Bertin Alpao、OGS Technologies；CO3D、LASIN、FrOGS、SOLIS（未来）、TELEO；CCSDS 141.0-B2/142.0-B-2 O3K
- 与业界对比或记录声明：未见 record 声明；讲者称 LEO 下行 AO 性能"already excellent"，SMF 注入已可转向 100+ Gbps 相干检测；上行方向提出 MEO 预补偿中继、预测式预补偿、收发天线分离 [p8，看图核实]
- 推荐配图页：p7（Aug 05 与 Sep 17 两次过境的 ROP 时间曲线与 Tb 级传输量）；p2（LASIN 星上架构与过境几何）

### 0920-am-Su2-F-05-SAFRAN-自适应光学加发射分集.pdf
- 讲者/机构：Safran（与 CNES、Bertin Alpao、FrOGS 联盟合作；讲者姓名幻灯片未显示） | 题目：AO + 发射分集用于 LEO 直连链路（英文原题幻灯片未显示；议程：Introduction & context / Previous work to prepare LEO IOD LASiN / Lab results / First on sky results / What's next / Conclusion & perspectives，看图核实） | 类型：学术论文
- 方向归属（主/次）：主 5（FSO 星地激光链路）；次 1（相干 DSP/交织与信道容量）
- 核心主张：
  1. 大气信道降低可用度；对策为自适应光学、空间分集（MIMO）、时间分集（纠删码/交织/ARQ），但时间分集带来时延。
  2. 新的 AO 控制算法 + 通信 DSP 仿真显示链路余量增益 4 dB；带内信令可降低交织引入的额外时延。
  3. 首轮在轨实测：20° 以上余量充足；高容量（>> 10 Gbps）低时延下行"在望"，需迭代并用不同收发机验证。
- 关键数据：
  - 仿真条件：望远镜 50 cm，仰角 20°–86°，闪烁指数 0.69，Fried r0 4.1 cm，横向风速 65 m/s，AO 算法带来链路余量增益 4 dB；含 AO 插入损耗 + SMF 静态耦合损耗 3.18 dB [p3]
  - 注入 ROP 随交织额外时延与仰角变化（Hard profile）：无湍流 -48.6 dBm；20° 时 47 ms -35.13 dBm、94 ms -38.33 dBm；30° 时 17 ms -35.65、47 ms -40.65、94 ms -41.2 dBm；45° 时 47 ms -45.2、94 ms -45.6 dBm；86° 时 17 ms -45.17、47 ms -45.72、94 ms -46.1 dBm（Medium profile：45° 11 ms -46.5、17 ms -46.22；86° 50 µs -44.8、11 ms -46.9 dBm）[p4]
  - 容量分析：DP-QPSK @ 50 Gbaud，目标 1 bit/symbol（FEC R=1/2），目标中断概率 0.001；LEO 下行 20° 仰角、50 cm 望远镜、r0 = 4.1 cm、闪烁指数 0.69、风速 65 m/s；时序 5 s，采样 14.68 kHz（146800 点）；1 个衰落样本 0.06812 ms（= 222 个 O3K 码字/偏振）；比较三种 AO 控制策略（leaky integrator 基线 / LQG / RL）；结论：最差 20° 剖面下 SNRe 4.5 时约 47 ms，50 GBd 双偏振上界 <10 ms，低时延亦可作为目标（看图核实）[p5]
  - 实测 2026-08-05：r0 ≈ 20 cm、θ0 ≈ 14 µrad、σx² ≈ 0.01；30° 以上余量充足，9 Gbps 载荷数据；CCSDS 带内信令使会话开始时即可得 125 Mbps 数据 [p8]
  - 另一过境（2026-07-07，r0 约 5 cm、Θ0 约 12 µrad、σ²χ 约 0.03、风速 9 m/s）：湍流较差 + PAT 测试下，20° 仰角 3.5 s 内载入 4 GB；LASiN 仍在在轨验证中（看图核实）[p9]
- 提到的公司/客户/产品/标准：Safran、CNES、Bertin Alpao（ACE 仿真器、Fast TT）、FrOGS、LASIN、CCSDS 带内信令、COTS 收发机
- 与业界对比或记录声明：无 record 声明；LASIN 仍处于在轨验证阶段，完整序列待分析 [p9]
- 推荐配图页：p4（ROP 对交织时延与仰角的数据表）；p8（30° 以上 9 Gbps 余量的 ROP 曲线）

## 本批小结
1. 星地 FSO 下行已进入"Tb 级数据量、在轨实测"阶段：FrOGS + LASIN 联合测试单次过境传输 1.38 Tb（r0=20 cm）和 1.62 Tb error-free（r0>25 cm）（F-04 p7），Safran 则报告 30° 以上 9 Gbps 有余量（F-05 p8）。
2. 通用瓶颈是 AO 后的 SMF 注入与衰落：注入效率约 40%，ROP -35 至 -25 dBm（F-04 p5）；两篇均以单模光纤注入为前提，为后续相干检测（F-04 路线图 100+ Gbps）铺路。
3. 时间分集（交织）与时延的权衡是共同议题：交织额外时延 11–94 ms 下注入 ROP 差异显著（F-05 p4），因此引入带内信令与更好的 AO 控制（LQG/RL）来压缩时延，仿真链路余量增益 4 dB（F-05 p3, p5）。
4. 两篇均沿用 CCSDS O3K 标准（LDPC，SF 多档调制编码）作为 LEO 下行实现基线（F-04 p2、F-05 p8）；上行（预补偿、空间分集，预计 2027 Q1 上天空数据）仍是尚未验证的开放问题（F-04 p8、F-05 p12）。
