# A 股量价复合信号的行业异质性动量增强效应研究

Industry-Heterogeneous Momentum Enhancement via Volume-Price Composite Signals: An Ablation Study in China's A-Share Market

**作者**：殷悦（Yue Yin），中南大学数学与统计学院
**录用**：ICEMGD 2026（第 10 届国际经济管理与绿色发展国际会议），Paper ID `ICEMGD_3008`，2026 年 9 月 28 日，罗马尼亚加拉茨。录用证明见 [paper/acceptance-icemgd-3008.pdf](paper/acceptance-icemgd-3008.pdf)。
**发表**：Advances in Economics, Management and Political Sciences（ISSN 2754-1169）

---

## 研究问题

传统技术分析把"价格新高 + 成交量萎缩"读作反转预警（Murphy, 1993）。本文检验相反的可能：这类量价背离在 A 股并非反转信号，而是**动量延续**信号，且延续强度存在显著的行业差异。

## 数据

| 项目 | 说明 |
|---|---|
| 样本区间 | 2015-01-01 至 2025-12-31 日频 |
| 股票池 | 申万一级 8 个行业的成分股，约 2001 只 |
| 行业分组 | 按 2015–2025 成交额加权年均换手率中位数，分为高换手（电子/计算机/汽车/传媒）与低换手（公用事业/医药/食品饮料/银行），最大组间差异 4.8 倍 |
| 基准 | 沪深 300 指数，市场调整模型计算超额收益 |
| 数据来源 | AkShare |

起点取 2015 年，因为申万行业分类在 2014 年完成重大修订，且融资融券在 2015 年前后进入成熟期。

## 方法

### 三重条件复合信号

信号日 t\* 须同时满足：

1. **动量筛选**：收盘价等于窗口 W 内最高价
2. **阻力过滤**：当日成交量低于前 W−1 日均量的 80%
3. **趋势确认**：窗口内价格—成交量 Pearson 相关系数 r < −0.3 且 p < 0.05（r 阈值取 Cohen 中等效应量标准）

全部信号只使用触发日收盘时点可得的信息，无前视偏差。

### 三重统计处理

| 问题 | 处理方式 | 效果 |
|---|---|---|
| 16 组参数组合的多重检验偏差 | Bonferroni 校正，α = 0.003，控制 FWER 在 0.05 | 显著组合从 14/16 收紧 |
| 同一股票重复信号导致非独立观测 | 股票层面聚类，每股票每组合 CAR 取均值 | 81,546 个信号压缩为 520–1,064（高组）与 401–719（低组）个独立单元；显著组合 14/16 降至 10/16 |
| 机制来源不明 | 五组条件消融实验（A/B/C/D/E） | 定位到三重条件的联合必要性 |

### 事件研究

CAR 采用市场调整模型：AR = R(i,t) − R(m,t)，CAR 为事件窗口内 AR 累加。另扣除 0.2% 双边交易成本（印花税单边 0.05%、佣金每边约 0.03%、市场冲击估计）得到净 CAR。

## 核心结果

### 1. 行业指数层面：方向一致但不显著

8 个行业指数序列在 16 组参数下仅识别出 **156 个信号—参数对**，Welch t 检验**全部不显著**（最小 p = 0.133）。W = 3 时高换手组 CAR 达 +6.56%，但最少仅 8 个信号支撑。

这一层结果未被丢弃：它与个股层面方向一致，恰好证明小样本下统计功效不足，需要下探到个股层面。逐条明细见 `results/signals/industry-signals-car.csv`。

### 2. 个股层面：动量增强效应显著

| 指标 | 数值 |
|---|---|
| 有效信号—参数对 | 81,546（高换手 44,484 / 低换手 37,062） |
| 相对指数层面的量级 | 约 523 倍 |
| Bonferroni 校正后显著 | 14/16 组 |
| 聚类后显著 | 10/16 组，W = 10 全部显著（t = 4.98–6.53） |
| t 统计量峰值 | W = 10 时 T = 9.17 |
| 高组平均 CAR | H = 1 时 0.99% → H = 10 时 4.05% |
| 低组平均 CAR | 0.03%–0.57% |
| W = 10, H = 10 毛 CAR 价差 | 5.47 个百分点 |
| 同参数净 CAR | 高组 5.27%，低组 1.25%，净价差 4.01 个百分点 |
| 信息比率（组间价差） | 0.27 |

策略绩效明细（`results/tables/strategy-performance.xlsx`，W = 10 / H = 10）：高换手组平均 CAR 5.47%、胜率 60.13%、信息比率 0.32、单次最大亏损 −52.24%；低换手组 1.45%、46.80%、0.12、−67.48%。

### 3. 消融实验：三重条件缺一不可

| 实验 | 条件组合 | 信号数 | 显著组数 |
|---|---|---|---|
| A | 仅条件 1（动量） | 58,051 | 0/16 |
| B | 条件 2 + 3 | 1,434 | 0/16 |
| C | 条件 1 + 2 | 7,559 / 6,276 | 0/16 |
| **D** | **三重条件完整** | **81,546** | **14/16** |
| E | 条件 1 + 3 | 132,982 | 0/16 |

只有完整三重条件才产生行业间显著差异。C 与 E 构成镜像对称，从两个独立方向确认条件 2 与条件 3 均是必要条件。**行业异质性不是单一条件的产物，而是三条件交互的涌现效应。**

### 4. 分时段稳健性

| 区间 | 显著组数 | 说明 |
|---|---|---|
| 2015–2016 | 8/16 | — |
| 2017–2020 | 2/16 | 样本内最弱 |
| 2021–2025 | 10/16 | 贡献 63.8% 的信号 |

三个子区间内高换手组 CAR 均高于低换手组，方向一致。

### 5. 回归检验

| 模型 | 价差 alpha | 市场 beta | 动量 beta |
|---|---|---|---|
| 单因子（市场） | 4.13%/月（p < 0.001） | 不显著（p = 0.634） | — |
| 双因子（市场 + 自建动量） | 3.80%/月（p = 0.002） | — | 0.6241（p = 0.073，不显著） |

加入动量因子后 alpha 仅下降 0.33 个百分点，说明行业异质性效应**不依赖于动量暴露**。低换手组动量 beta 为 −0.3272（p = 0.033），方向与高换手组相反，进一步支持分组逻辑。

### 6. 机制解释

- **高换手行业（电子、计算机）**：持续新高配合缩量，是投资者关注度饱和与流动性需求暂时收缩的状态——"情绪共识静默"。按 Hong & Stein 的渐进信息扩散框架，这种静默先于第二波信息冲击，使动量延续到初始阶段之后。
- **低换手行业（银行、公用事业）**：机构长期持有，价升量减是常态而非特异信号，条件 3 因而丧失区分力。聚类后低组平均 CAR 仅 0.03%（W = 10, H = 1），与高组 0.99% 相差 0.96 个百分点。

## 目录

```
paper/
  volume-price-composite-signal-industry-heterogeneity.pdf   论文全文（中文）
  conference-paper-final.docx                                会议投稿版（英文，含表格）
  acceptance-icemgd-3008.pdf                                  ICEMGD 2026 录用证明
data/
  industry_daily/        8 个申万一级行业日线 + 沪深 300 基准（2015–2025）
results/
  turnover-ranking.xlsx                行业换手率排名（分组依据）
  industry-t-test-matrix.xlsx          行业指数层面 T 检验（156 个信号对）
  stock-t-test-matrix.xlsx             个股层面 T 检验（16 组参数）
  robustness-t-test-summary.xlsx       16 组 × 3 子区间稳健性汇总
  tables/                              分组依据、描述性统计、策略绩效、消融与回归结果
  signals/
    stock-signals-car.csv.gz           81,546 条个股信号逐条明细（gzip，解压后 6.9 MB）
    ablation-a-signals.csv.gz          消融 A（仅动量，gzip 后 7.8 MB）
    ablation-c-signals.csv.gz          消融 C
    ablation-e-signals.csv.gz          消融 E
    two-condition-signals.csv.gz       二重条件
    industry-signals-car.csv           行业层面 156 条信号明细（未压缩）
figures/
  fig1-car-heatmap.png                CAR 热力图
  fig2-t-test-significance.png        T 检验显著性矩阵
  fig3-industry-car-comparison.png    行业 CAR 对比
  fig4-car-boxplot.png                CAR 分布箱线图
  fig5-two-level-car-gap.png          两层次 CAR 差值对比
  fig6-stock-pvalue-matrix.png        个股 P 值矩阵
  fig7-car-paths-en.png               CAR 路径图（英文版，含 95% 置信区间）
  fig8-car-cumulative-paths-cn.png    CAR 累积路径图（中文版）
```

信号级 CSV 字段：`signal_date, W, H, vol_ratio, pearson_r, p_value, CAR, industry, group, group_label`。

## 关于代码与原始数据

**本仓库不包含研究代码，也不包含逐股原始日线。** 说明如下：

1. **代码**：研究中使用的脚本未以 `.py` 或 `.ipynb` 形式留存，只保存了运行结果。作者不打算根据论文描述反推一份"看起来一样"的脚本上传——那样无法保证与你实际跑出的数字一致，反而失真。
2. **逐股数据**：约 2001 只个股的日线文件合计约 100 MB，行业换手率中间数据约 150 MB，远超仓库合理范围，且可用 AkShare 公开接口重新获取，没有必要占用仓库空间。

本仓库提供的是**可核验的复现材料**：行业日线与基准（可直接重跑行业层面）、每一层的 T 检验矩阵、消融实验的全部检验结果、8 万余条信号级明细（可直接复算 t 值、Bonferroni 阈值、聚类后统计量）。用这些材料可以独立验证论文中的每一个数字。

需要完整流水线，请通过本仓库的 Issues 联系作者，说明用途。

技术栈：Python 3（pandas、numpy、scipy、statsmodels）、AkShare。

## 已知局限

1. 市场调整模型可能隐含 SMB、HML、MOM 暴露。双因子回归已部分缓解，完整的 Carhart 四因子检验留待后续。
2. 聚类处理了序列相关，但未处理同股票跨参数相关与共同市场状态下的横截面相关，Bootstrap 置换检验会更完整。
3. 0.2% 双边成本估计偏保守，大额头寸的实际冲击成本随流动性差异显著变化。
4. W = 3 组合的 p < 0.05 实际要求 |r| > 0.997（df = 1），退化为严格三日单调反转，与 W = 5/10 的统计含义不同，该组结果需谨慎解读。

## 引用

```
Yin, Y. (2026). Industry-Heterogeneous Momentum Enhancement via Volume-Price
Composite Signals: An Ablation Study in China's A-Share Market. Paper presented
at the 10th International Conference on Economic Management and Green
Development (ICEMGD 2026), Galati, Romania. Paper ID: ICEMGD_3008.
```
