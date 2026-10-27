# 研究资产评审（数据 / 代码 / 结果库）

## 这是什么

前四个组件审的是**说法**（问题值不值得做、会不会被桌拒、扛不扛得住审稿）。这一层审的是**东西**：

> 这个项目的数据、代码、结果，能不能支撑它自己声称的结论？

它既可以单独用（「帮我看看这个仓库」），也可以接在七关之后（「稿子说能复现，真的吗」）。

## 口径

- 语料中 `data` 类意见 1,937 条、`data_code` 类 506 条，本节判据主要由此归纳，引用的原话均带 DOI
- **超出期刊合规的部分是判断**（如「这个数据集值不值得投入二次分析」），文件内单独标注
- 本层**不判断数据是否真实**，只判断是否**可验证**

## 三层资产

```
项目
├── 数据     原始观测 / 处理后数据 / 元数据
├── 代码     分析脚本 / 模型 / 绘图
└── 结果     图 / 表 / 模型文件 / 中间产物
```

三层必须能**串起来**：结论 → 图 → 脚本 → 数据 → 采样。任何一环断了，那条结论就是不可验证的。

---

## 一、数据层

### 能拿到吗

- 在哪（Dryad / Zenodo / Figshare / EDI / GBIF / 机构库 / 补充材料）
- 有没有 embargo、申请流程、许可限制
- **只给"available upon request"等于没有**

### 元数据

- 有没有独立的数据字典（不是散在代码注释里）
- 每个变量的定义、单位、取值域
- **缺失值代表什么**：没测 / 测了没检出 / 丢了

【语料】
> "I think having a data dictionary separate from your code in which the name of each file and what it is used for, as well as complete definitions and calculations of each variable" — `10.1038/s41559-022-01772-5`

> "Why is Gosner stage NA for 12/48 in your Mitochondrial Enzyme Assay raw data sheet on Zenodo?" — `10.1038/s41559-022-01686-2`

第二句是典型死法：数据公开了，但缺失值没解释，审稿人照样追。

### 样本量一致

正文、图表、原始表三处的 n 必须对得上。对不上是最容易被抓的硬伤之一。

【语料】
> "If I sum all the samples that were mentioned in the methods I get more than 700 metagenomic samples (this number does not fit the supplementary tables provided)." — `10.1038/s41559-025-02740-5`

### 采样设计记录

时间、地点、方法、已知偏差。缺了就无法判断可比性。

【语料】
> "is there an official specimen number and geographic data for the sample?" — `10.1038/s41559-022-01753-8`

### 版本与许可

- 有没有固定版本号或 DOI（而非一个会变的 GitHub 链接）
- 许可是否允许再用

---

## 二、代码层

### 能不能跑通

- 环境（语言版本、包版本、容器）
- 依赖清单
- 入口：从哪开始跑、按什么顺序

### **覆盖范围**（最常死在这里）

代码是否覆盖**全部**结果，还是只覆盖了一部分（典型：只画图，不做分析）。

【语料】
> "I note that the R code does not include the meta-analysis but only the plotting of the figures from the data." — `10.1038/s41559-022-01820-0`

> "Importantly, I could not find the code used for the analyses used in R. I cannot fully evaluate your manuscript until I am able to see how you did your analyses." — `10.1038/s41559-022-01686-2`

**自查**：逐个图问「这张图由哪个脚本的第几行产生」，答不上就是部分代码。

### 从原始数据到最终图

中间是否缺步骤（手工 Excel 一步、手动删点、GUI 软件操作）。

### 随机性

随机种子固定了吗？重跑结果一致吗？

### 版本

commit hash 或 Zenodo DOI，不要只给仓库首页。

---

## 三、结果层

- **可重生成**：每个图/表能否由代码 + 数据重新产出
- **无孤儿**：有没有结果在稿子里出现，但代码跑不出、数据里也没有
- **中间产物一致**：正文数字与中间文件是否一致
- **模型文件**：训练好的模型、参数表、随机种子是否一并提供

**自查**：把代码删掉，只看数据，能不能复现正文第一个数字？不能就是断链。

---

## 四、项目层：资产与论点的对应表

建一张表，逐条结论往下追：

| 结论 | 依赖的图 | 图由哪个脚本 | 脚本读哪个数据 | 数据来自哪次采样 |
|---|---|---|---|---|
| C1 | Fig 2a | `01_analysis.R` | `clean.csv` | 2019 年 6 个样地 |
| C2 | Fig 3 | 无 | 无 | 无 ← **断链** |

**每一行断在哪，那条结论就只能降级为「作者声称」。**

这张表本身就是给审稿人看的防御材料——它证明你清楚自己的证据链。

---

## 五、生态学特有规范

| 资产 | 惯用去处 | 元数据标准 |
|---|---|---|
| 野外观测 / 群落数据 | Dryad、EDI、GBIF | EML、Darwin Core |
| 测序数据 | SRA / ENA（BioProject 号） | MIxS |
| 标本 / 凭证 | 标本馆编号 + 机构 | Darwin Core |
| 模型 / 代码 | GitHub + Zenodo DOI | `renv` / `Dockerfile` / `environment.yml` |
| 遥感 / 栅格 | Zenodo、PANGAEA | CF conventions |

**缺这些不会直接拒稿，但会在 `data_code` 类被抓（major 7.8%，命中即高杀伤）。**

---

## 六、输出

三档，不打分：

| 档 | 判据 | 含义 |
|---|---|---|
| **可直接复用** | 三层齐全，能串起来 | 可作为二次分析基础 |
| **需补文档** | 资产在，但缺元数据/入口/覆盖说明 | 补文档即可，几小时到几天 |
| **不可验证** | 关键链断裂（代码缺失、数据不可得、孤儿结果） | 相关结论只能降级 |

输出模板：

```
## 资产评审

**结论**：可直接复用 / 需补文档 / 不可验证

| 结论 | 图 | 脚本 | 数据 | 采样 | 状态 |
|---|---|---|---|---|---|
| … | … | … | … | … | ✅ / ❌ |

**最小补齐动作**（按性价比）：
1. …
2. …

**不可验证的结论**：…
```

---

## 七、与前面几关的关系

```
品位关      值不值得做
第 0 关     见不见得到审稿人
七关        扛不扛得住审稿
资产评审    东西对不对得上
```

资产评审失败会直接触发七关里的 `data`（34.5% major）与 `data_code`（7.8% major）两类攻击，且**第 15 类几乎不给修的机会**——数据不公开、代码跑不通，是硬伤。

---

## 诚实性

- 数据层、代码层的判据与引语来自语料，可回溯 `data/comments_all.jsonl`
- 项目层外延（团队能力、预算、时间可行性）**不在语料内**，属判断，不得冒充统计
- 本层判断的是「是否可验证」，不是「数据是否真实」——后者只能靠原始记录与审计
- 生态学仓库规范（EML、Darwin Core、MIxS）为学科惯例，非本库统计所得
