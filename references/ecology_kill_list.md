# 生态学击杀清单（Ecology kill list）

## 这是什么

按「被列为 major 的概率」排序的 **16 个生态学特有方法问题**。

口径：全部来自本库 48,422 条 EL / NEE 首轮审稿意见，全库 major 基线为 **28.9%**。
下表的 `major率` 是该问题被提及的意见中，被列为 major 的比例；`vs 基线` 是与全库基线的差。

**为什么这张表通用 skill 做不出来**：它要求同时具备生态学方法词汇的识别能力和真实审稿语料的统计。

## 排名总表

| 生态学问题 | 提及 | major 率 | vs 基线 |
|---|---:|---:|---:|
| 伪重复 | 64 | **79.7%** | +50.8 |
| 空间自相关 | 59 | **59.3%** | +30.4 |
| 检测概率/占据模型 | 26 | **57.7%** | +28.8 |
| 共线性 | 95 | **53.7%** | +24.7 |
| 多重比较 | 56 | **53.6%** | +24.6 |
| 外推 | 318 | **53.1%** | +24.2 |
| 零膨胀/过度离散 | 54 | **51.9%** | +22.9 |
| 物种分布模型 | 59 | **49.2%** | +20.2 |
| 尺度错配 | 312 | **49.0%** | +20.1 |
| 过拟合/交叉验证 | 297 | **48.1%** | +19.2 |
| 时空替代 | 21 | **47.6%** | +18.7 |
| 系统发育非独立 | 98 | **46.9%** | +18.0 |
| 随机效应/嵌套 | 331 | **46.2%** | +17.3 |
| 中宇宙/围隔 | 98 | **43.9%** | +14.9 |
| 效应量与置信区间 | 501 | **38.5%** | +9.6 |
| 稀疏化/覆盖度 | 30 | **26.7%** | -2.3 |

读法：基线 28.9%。`伪重复` 一旦被提，近 80% 是 major——它几乎是「必死」类；
`效应量与置信区间` 只有 38.5%，说明审稿人常提但不一定当致命问题。

## 逐条：自查问句 + 真实原话

### 伪重复 · n=64 · major 79.7%（+50.8）

**自查**：重复单位是什么？同一窝卵 / 同一母体 / 同一样地 / 同一时段的观测算独立重复吗？随机效应覆盖了吗？

> "given that (as I understand it) a single clutch of eggs was used, n=11 for thermal tolerance estimates is somewhat low." — `10.1038/s41559-022-01686-2`

> "Observations from the same spatial units are non-independent and likely exhibit some degree of autocorrelation, so the statistical methods must account for this non-independence." — `10.1038/s41559-022-01710-5`

### 空间自相关 · n=59 · major 59.3%（+30.4）

**自查**：检验的是**模型残差**还是原始观测？校正之后残差里还有空间结构吗？

> "Did you tested for spatial autocorrelation (SAC) in the observations or model residuals? The correct way is test for SAC in the models’ residuals." — `10.1038/s41559-022-01747-6`

> "The data is spatial but the authors did not check for nor accounted for spatial autocorrelation in the data." — `10.1038/s41559-022-01868-y`

### 检测概率/占据模型 · n=26 · major 57.7%（+28.8）

**自查**：数据是「出现 / 未出现」，但检测概率 < 1 吗？未校正检测率会系统性低估占据率与丰度变化。

> "There is a whole body of literature concerned with modelling abundances/ occupancy from the BBS data (e.g. unevenly distributed data, sampling/ detection effects) and I am a bit concerned that it has not been cited" — `10.1038/s41559-022-01814-y`

> "Banding data has also plenty of limitations (biases) as there are large spatial differences in the detection probability" — `10.1038/s41559-024-02575-6`

### 共线性 · n=95 · major 53.7%（+24.7）

**自查**：两个「独立」变量是不是本来就同源（气候 → 植被 → 凋落物 → 分解）？VIF 报了吗？

> "It seems like litter characteristics and macroclimate are confounded. Plant composition is highly dependent on macroclimate." — `10.1038/s41559-022-01948-z`

> "Are relationships between traits and sensitivity stronger than the ones observed between traits and “simple climatic data”?" — `10.1038/s41559-023-02007-x`

### 多重比较 · n=56 · major 53.6%（+24.6）

**自查**：一共做了多少个检验？FDR 或 Bonferroni 校正了吗？未校正的「显著」有多少是搜出来的？

> "the p-value cutoff should adjust for the total number of tests (e.g. using a false discovery rate or a Bonferroni correction)." — `10.1038/s41559-022-01753-8`

> "A point that is mentioned in the review, but not clearly highlighted, is the problem of multiple testing and FDR correction. This is rarely done in evolutionary studies, and likely leads to high false positive rates." — `10.1038/s41559-022-01761-8`

### 外推 · n=318 · major 53.1%（+24.2）

**自查**：预测范围超出训练数据的地理 / 气候空间了吗？做过空间分块交叉验证吗？

> "is it possible to perform some form of cross validation to ensure the accuracy of these extrapolations given that you’ve extrapolated a huge number of species?" — `10.1038/s41559-022-01710-5`

> "The differences in results (ML extrapolations) when using recent assessments or all published assessments should be discussed (possible reasons) and/or dealt with analytically." — `10.1038/s41559-022-01858-0`

### 零膨胀/过度离散 · n=54 · major 51.9%（+22.9）

**自查**：计数数据的均值-方差关系查了吗？Poisson 够用吗，还是需要负二项 / 零膨胀？

> "However, there is evidence suggesting that plant medicinal remedies to cure different ailments are randomly distributed (or even overdispersed) in the phylogeny" — `10.1038/s41559-022-01858-0`

> "I’d try to model the data of all tiers in a joint model; maybe trying to model the absolute count of retractions in a Poisson (or zero-inflated?) model, using the date of policy change as a break-point." — `10.1038/s41559-022-01879-9`

### 物种分布模型 · n=59 · major 49.2%（+20.2）

**自查**：生态位保守假设站得住吗？背景点怎么选的？评估用的是随机 AUC 还是空间分块交叉验证？

> "If the latter is not true, the SDMs are likely to be completely wrong since the niche of species is incorrectly estimated" — `10.1038/s41559-023-02061-5`

> "Assuming that species' climate niche remains stable over time is a strong assumption, and furthermore, it has been demonstrated that species distribution models can vary even within species (Razgour et al. 2019; Chardon et al. 2020)" — `10.1038/s41559-023-02260-0`

### 尺度错配 · n=312 · major 49.0%（+20.1）

**自查**：观测尺度（样方 / 样带 / 单点）与推断尺度（区域 / 全球）差几级？中间那几级凭什么跨过去？

> "if there would not be a way to directly test this - at least experiments of different size must exist and it may be possible to also estimate the spatial extent of observed droughts" — `10.1038/s41559-022-01685-3`

> "You should at minimum do a richness comparison to see to what extent you are introducing the same bacteria species that are from the pond" — `10.1038/s41559-022-01686-2`

### 过拟合/交叉验证 · n=297 · major 48.1%（+19.2）

**自查**：交叉验证是随机分折，还是按空间 / 时间 / 物种分块？随机分折会高估可迁移性。

> "the result in figure 2b could be a consequence of the usage of cyclic cubic splines, combined with the absence of samples during hibernation, rather than evidence for a slowing of aging itself." — `10.1038/s41559-022-01679-1`

> "Your n designated as a random effect might be too low for the numerical methods used in lme4. Also, did you compare different factors in your models? Do you have AICs you could report?" — `10.1038/s41559-022-01686-2`

### 时空替代 · n=21 · major 47.6%（+18.7）

**自查**：用空间梯度代替时间序列了吗？梯度上的混杂（土壤母质、土地利用史、物种池）排除了吗？

> "If I've understood the methods correctly, I think the way that temperature change is described is a bit misleading." — `10.1038/s41559-024-02493-7`

> "we know that MPAs are not randomly placed in the ocean, but often placed near areas of high biodiversity or recreational value or away from human populations" — `10.1038/s41559-026-03008-2`

### 系统发育非独立 · n=98 · major 46.9%（+18.0）

**自查**：跨物种比较做 PGLS 或系统发育随机效应了吗？还是把近缘种当独立样本？

> "Were Figure 2E correlations corrected for phylogeny using PGLS?" — `10.1038/s41559-022-01692-4`

> "The findings of stronger phylosymbiotic and cophylogenetic signal among HMA does not support the claim that sponges and their microbes have codiversified" — `10.1038/s41559-022-01712-3`

### 随机效应/嵌套 · n=331 · major 46.2%（+17.3）

**自查**：所有非独立结构（样地 / 年份 / 个体 / 物种）都有对应随机项吗？随机项水平数够估方差吗？

> "Your n designated as a random effect might be too low for the numerical methods used in lme4. Also, did you compare different factors in your models? Do you have AICs you could report?" — `10.1038/s41559-022-01686-2`

> "Observations from the same spatial units are non-independent and likely exhibit some degree of autocorrelation, so the statistical methods must account for this non-independence." — `10.1038/s41559-022-01710-5`

### 中宇宙/围隔 · n=98 · major 43.9%（+14.9）

**自查**：中宇宙条件与自然环境的差距讨论了吗？能否用 reciprocal transplant 或原位验证补上？

> "to identify reset/plastic and fixed DMRs, it should be better to reciprocally transplant wild samples to opposite environments" — `10.1038/s41559-022-01894-w`

> "Were the conditions in this experiment similar to any of the natural environments? For example, were the tanks similar in oxygen and temperature of the littoral, but not benthic fish? How would this bias analysis or alter conclusions?" — `10.1038/s41559-022-01894-w`

### 效应量与置信区间 · n=501 · major 38.5%（+9.6）

**自查**：报的是效应量和区间，还是只报 p？区间跨零却宣称有影响了吗？

> "the authors state that MCRA of extant ungulates was most likely non-migratory, but their estimate is so close to 50:50 that they should instead admit that they cannot tell one from the other." — `10.1038/s41559-022-01749-4`

> "I don't understand why the authors think that an overlap of the standard errors with 0 indicate non-significance. If they aim to use the parameter range this way, they should use confidence intervals instead" — `10.1038/s41559-022-01749-4`

### 稀疏化/覆盖度 · n=30 · major 26.7%（-2.3）

**自查**：不同样本量的群落之间比较，做稀疏化或覆盖度标准化了吗？

> "I think you need to better justify why you rarefied your data." — `10.1038/s41559-022-01686-2`

> "This suggests that the central role certain species could be an artifact of number of individuals sampled, giving an unfair disadvantage to rarer species." — `10.1038/s41559-023-02130-9`

## 怎么用

七关过堂时，这一层是**第 6 关（方法关）的生态学细化**：先按七关的通用问句问一遍，
再用本表逐条扫。命中任意一条，直接升到 major 处理。

写作阶段的自查顺序建议按 major 率降序——先解决伪重复、空间自相关、
检测概率、共线性、多重比较，这五类占全部 major 风险的头部。

## 诚实性

- 本表关键词检索为**代理指标**，会混入少量非方法语境；用于排序和提示，不用于精确计数
- 提及率是「这类词出现过」，不等于「审稿人系统性地检查了这一点」
- 语料只覆盖 Ecology Letters 与 Nature Ecology & Evolution；其他生态学刊物的风格可能不同
- `vs 基线` 是相关性，不是因果：不能说「因为伪重复所以被拒」
