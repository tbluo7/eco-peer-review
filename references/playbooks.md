# 16 类审稿意见 Playbook

每类含：审稿人在挑什么、真实原句（带论文 id，可回 `comments_all.jsonl` 查完整上下文）、审稿要点（评审时逐条问）。
出现率口径 = 至少一位审稿人列为 major 的论文占比（all / EL / NEE）。

---

## 1. framing — 立论与叙事（major 52.3% · EL 52.7 · NEE 51.3 · 1676 条 major）

**挑什么**：引言的预期没有铺垫就突然出现；文献综述漏掉关键前作（审稿人常就是被漏的人）；"pitch"与研究实际做的东西脱节；中心假设过于简化、反而遮蔽了论文真正的贡献；概念框架（如多样性→功能）与实际分析的数据对不上。

**真实原句**
- "The rationale for this expectation should be described in earlier paragraphs." — 10.1038/s41559-024-02362-3
- "I feel that there is a disconnect between the pitch (based heavily on species interactions) and the data (seed production and large-scale abiotic data – ie no data on species interactions)." — 10.1111/ele.14012
- "The paper begins by asserting that BEF experiments mainly show that ecosystem functioning depends on initial planted diversity … That is not correct." — 10.1111/ele.13874
- "the way they have been pitched is an oversimplification. It distracts the reader from the main contribution of the paper." — 10.1111/ele.13858

**审稿要点**：摘要里每个 claim 在引言都有铺垫吗？关键前作（尤其竞争团队）引了吗？标题/引言承诺的问题和结果章节回答的问题是同一个吗？

## 2. stats — 统计分析（major 50.3% · EL 45.8 · NEE **60.4** · 1921 条 major）

**挑什么**：随机效应结构错误/伪重复；分析逻辑循环（用 X 标准化又把 X 当协变量）；变量间关系数学上已预定还去回归；模型选择与数据结构不匹配；样本量撑不起检验；单变量检验不控制协变量。**NEE 是头号杀手（严决定组 70.3%），观测/元分析类尤其高（60–65%）**。

**真实原句**
- "if females produce more than one offspring (i.e. repeated measures), maternal identity should always be included as a random effect to account for potential pseudoreplication" — 10.1111/ele.13839
- "The relationship between these three variables is already pre-determined mathematically, therefore there is no need to run a regression analysis to estimate the variables." — 10.1111/ele.13857
- "acclimation temperature is also included in the model as a fixed effect, so why correct the capacity values themselves?" — 10.1111/ele.70046
- "This mixed approach to statistics does not seem appropriate because it does not give consistent answers and using single variable comparisons does not control for the other variables" — 10.1038/s41559-025-02861-x

**审稿要点**：随机效应是否覆盖全部非独立结构？有没有"先标准化再当协变量"式循环？样本量/检验力说得清吗？换一种合理模型结论会变吗（衔接 robustness）？

## 3. interpretation — 解读过度（major 49.1% · EL 44.6 · NEE 59.3 · 1488 条 major）

**挑什么**：结论超出数据支撑（机制从相关里读出来）；关键结果与假设矛盾却不处理；替代解释未讨论；措辞过强（retains/inherited vs 独立演化）；用实验室/遥感 Proxy 结论回答群落/生态系统层面的问题。

**真实原句**
- "Overall, I think the authors are leaning too much into the similarity with MAVS, which has no real support and could simply be convergence." — 10.1038/s41559-026-03112-3
- "As shown in Fig S6, once standardized per surface area, the rates are very different, with no gain in either photosynthesis nor nutrients uptake." — 10.1111/ele.70376
- "Remote sensing at a global scale is never going to accurately estimate recovery of ecosystem structure and function relative to a baseline standard." — 10.1038/s41559-025-02683-x
- "The key result (Fig. 2 sessile species, Table 1) is not consistent with the stated hypothesis." — 10.1111/ele.70144

**审稿要点**：每个结论旁标注支撑它的具体结果；机制词（drive/cause/determine）是否都换成数据能支撑的强度；与假设相反的结果正面处理了吗？

## 4. methods_reporting — 方法报告不全（major 44.8% · EL 40.1 · NEE 55.4 · 1322 条 major）

**挑什么**：关键步骤细节缺失到无法重复（样本量、参数、软件设置、采样设计）；方法散在补充材料里正文找不到；响应变量怎么算的说不清；"Methods lack minimum detail on soil type/site climate (I do not expect to have to read another paper to find this information!)" — 10.1111/ele.14361。

**真实原句**
- "The paper seems to be lacking a methods section entirely." — 10.1038/s41559-025-02864-8
- "The authors need to provide more details in the methods and / or elsewhere to ensure that these analyses are clear and reproducible." — 10.1038/s41559-023-02186-7
- "I do not think you calculated the time spent in each habitat and I feel there is confusion between the RSF and SR." — 10.1111/ele.13694

**审稿要点**：外人只读方法节能复现每个分析吗？每个图的每个点都能追溯到"怎么测、在哪测、多少重复"吗？

## 5. causality — 因果与替代解释（major 41.6% · EL 36.7 · NEE 52.6 · 1240 条 major）

**挑什么**：观察到的模式有不只一个成因（宿主抗性、生长限制、环境混淆），作者只讨论自己喜欢的那一个；实验处理没有隔离目标机制（种子来自野外、共球实验混菌株）；_proxy_ 证据链条断了一环。

**真实原句**
- "I was surprised however to see, in a model for host-parasite co-evolution, that host defense against parasitism (ie resistance or tolerance) was not considered at all." — 10.1038/s41559-022-01772-5
- "It appears that the authors' analysis indeed points to the role of growth restriction, instead of the restriction by complex carbohydrates" — 10.1038/s41559-022-01930-9
- "Seeds came directly from the field and phenotypes might reflect field site environmental conditions." — 10.1111/ele.13858
- "it is important to weaken here and elsewhere in the text … the statements stating that fire occurrence increased with the onset of the Mediterranean-type climate, because there is no direct or proxy evidence supporting this" — 10.1111/ele.70169

**审稿要点**：列出结果的所有合理替代解释，逐一说明数据为什么排除了它（或承认不能排除）；实验设计的每个对照在隔离什么机制，说得出来吗？

## 6. definitions — 概念与术语（major 40.5% · EL 40.1 · NEE 41.3 · 1096 条 major）

**挑什么**：相近概念混用（plasticity vs evolution、heterogeneity vs stochasticity、resilience 一词多义）；自创术语未定义就进摘要；术语含义与领域标准定义（如心理测量学的 reliability）不一致；用指标代理概念但不说明 R² 之外的含义。

**真实原句**
- "It would be useful if the authors could explain the differences between these terms, and provide examples of each one in the context of climate change." — 10.1111/ele.14280
- "These terms have a clear meaning in psychometrics, but this is sometimes not in line with the way the authors use these terms." — 10.1038/s41559-023-02050-8
- "If this is the case, then the use of “indirect defenses” is incorrect, since the beneficial organisms are not themselves the indirect defense" — 10.1111/ele.70305

**审稿要点**：核心概念各给一个明确定义并全文一致；摘要里的每个术语正文都有定义；别用近义词互换你以为的同义词——审稿人分得出。

## 7. robustness — 稳健性（major 35.7% · EL 30.4 · NEE 47.6 · 869 条 major）

**挑什么**：结论只在单一方法/参数/子集下成立，没做敏感性分析；关键假设（可检测半衰期、体温预测）只验证了极少案例；图上的模式可能是合并数据的伪迹，分组建表就散了。

**真实原句**
- "the authors should provide a table of the correlations between native and non-native richness across the four community types and seven ecoregions with and without the addition of co-variates" — 10.1111/ele.13782
- "I suggest including a sensitivity analysis illustrating how genetic diversity varies with (a) taxonomic assignment confidence, (b) read depth, and (c) marker type" — 10.1038/s41559-026-03106-1
- "Can your hypothesis still be accepted if the results are viewed after 10 or 20 years, which is closer to the time scales experienced at many field long-term climate experiments?" — 10.1111/ele.14530

**审稿要点**：主要结论至少换一种合理方法/参数重跑过吗？数据分亚组后模式还在吗？外推的时间/空间尺度与数据尺度匹配吗？

## 8. data — 数据本身（major 34.5% · EL 28.2 · NEE **48.7** · 919 条 major）

**挑什么**：数据集之间不可比（体外 FACS vs 全胚匀浆）；样本数对不上补充表；数据来源有空间/系统偏差（标本馆 4km 分辨率）；用物种清单+metaweb 拼的"食物网"其实测不了那个假设；评估模型输出的非线性是"built in"的。**NEE 明显更严（宽决定组也 45.9%）**。

**真实原句**
- "If I sum all the samples that were mentioned in the methods I get more than 700 metagenomic samples (this number does not fit the supplementary tables provided)." — 10.1038/s41559-025-02740-5
- "a conclusion that the dynamics of recruitment are more nonlinear than those of biomass isn’t necessarily a finding about real fish – it is built in!" — 10.1038/s41559-025-02968-1
- "The datasets for this study, if I understand correctly, are species lists … rather than food webs." — 10.1111/ele.13995
- "The genome quality is the core of the whole paper, yet there're several spots make me concern about it." — 10.1038/s41559-024-02456-y

**审稿要点**：每个数据源的采样设计、分辨率、偏差写得出来吗？跨来源合并时可比性论证了吗？样本数全文一致吗？

## 9. novelty — 新颖性（major 28.9% · EL 27.5 · NEE 32.2 · 602 条 major）

**挑什么**："What is new here?"——与自己团队前作、领域近作的增量说不清；问题已被 Bergmann 2020 这类大文章解决过；对泛刊（general journal）而言受众太窄（"focuses almost exclusively on seabirds … not appropriate for a general journal such as Ecology Letters" — 10.1111/ele.14479）；声称的保护/管理意义撑不住。综述类（41.3%）和方法类（42.9%）被挑新颖性最狠。

**真实原句**
- "The root economics space has been well demonstrated and interpreted already in Bergmann et al. (2020). This paper should not focus on root economics space itself …" — 10.1111/ele.14402
- "Particularly, Spaak et al. (2021c) already considered niche and fitness differences in multitrophic communities (L48). Then, what is new here?" — 10.1111/ele.14409
- "I am questioning a bit the novelty and originality of the research in respect to a journal like Nature Ecology and Evolution" — 10.1038/s41559-024-02435-3

**审稿要点**：一句话说清"相对最近的 X，本文新在 Y"；这个 Y 对期刊的广义读者重要吗？别让审稿人替你找。

## 10. presentation — 结构与表达（major 27.1% · 提及率 **94.6%** · 651 条 major）

**挑什么**：结果/讨论/方法混写；验证性分析埋在补充材料；对非本领域读者不友好（模型类型从不解释）；冗长描述淹没关键信息。**注意：94.6% 的论文被提过表述问题但多数是 minor——被提不致命，但写得太乱会放大其他问题、消耗审稿人耐心**。综述类 major 41.3%。

**真实原句**
- "As the value of the simulations is entirely reliant on the models being valid then the results of model validation need to be prominent for the reader to check in the main ms" — 10.1111/ele.14190
- "for publication as a Letter, the text would need major formatting to give enough important information and avoid redundancy between the different parts" — 10.1111/ele.70083

**审稿要点**：验证/关键结果在正文；每节只干一件事；假设不熟读者读得懂首段。

## 11. design — 实验设计（major 24.7% · experimental 类 **50.2%** · 624 条 major）

**挑什么**：重复不足（Figure 1 是 n=1！）；处理混淆（G2 同时含亲本经历+幼体发育，transgenerational 没被隔离）；对照缺失；样带采样覆盖不了二维空间；二元分类（organic vs conventional）抹掉了关键变异。**做实验的论文这是第二大类**。

**真实原句**
- "The first experiment (Figure 1) is not replicated (n=1). The final colonization experiment (Figure 5) has only 5 replicates per treatment and no quantitative results are shown." — 10.1038/s41559-022-01795-y
- "This contrast is used to argue for transgenerational plasticity, but I think this might be overly optimistic." — 10.1111/ele.70246
- "This confounds the effects of inter-strain competition with the effects of social vs. individual immunity" — 10.1038/s41559-023-01981-6
- "transects are a one-dimensional sample of a two-dimensional space, covering only a tiny fraction of the 900 m² plot" — 10.1111/ele.70393

**审稿要点**：每个对照隔离一个混淆；重复数×处理数的表格先画出来；设计能唯一支撑想要的推断吗（找一位同事盲猜"这设计能测出什么"）？

## 12. generality — 普适性外推（major 19.7% · EL 17.9 · NEE 23.7 · 386 条 major）

**挑什么**：两个点位（还都是草食者可忽略的系统）参数化就声称普适；标题/摘要承诺一般机制、实际只是某类群落的相关；全球外推不管约束条件；实验操纵强度远超自然范围（fighter frequency）。

**真实原句**
- "why these two? Moreover, why stop here? Surely data are available for a range of sites that would permit a fuller exploration of the model's validity." — 10.1111/ele.13876
- "this is really a paper about correlations between mycorrhizal associations, plant traits, and distributions across woody angiosperms" — 10.1111/ele.14489
- "This makes the presented experimental scenario potentially quite artificial … could compromise the wider conclusions" — 10.1111/ele.70377

**审稿要点**：claim 的范围=数据的范围；要做普适声明就多系统验证，否则收窄措辞。

## 13. model_theory — 模型与理论（major 17.8% · theory_model/mixed 类 19–31% · 694 条 major）

**挑什么**：模型结构与生态现实不符（全部物种互相作用 vs 稀疏网络）；关键假设未论证（恒定 r/K、Taylor 二阶展开的适用域）；数学上比错了对象（不同周期长度的 eigenvalue 直接比="apples and oranges"）；参数化选择决定全部结果却没做敏感性。

**真实原句**
- "comparisons of your absolute fitness (eigenvalue of A) 'across' cycle periods (e.g., your Fig. 1C) are nonsensical. It is a comparison of apples and oranges." — 10.1111/ele.13867
- "The key problem is that, in ecological reality, species can only interact with a few other species; it is rare that all species can interact with all others in a species-rich community." — 10.1111/ele.13877
- "there are some major assumptions about socio-ecological systems built into the model that need to be better acknowledged and justified" — 10.1111/ele.13914

**审稿要点**：假设列表逐条给出依据+违反时会怎样；结论对模型结构选择敏感吗；比较的量在数学上可比吗。

## 14. figures — 图表（major 16.3% · 提及率 79.7% · NEE 严组 32.2% · 361 条 major）

**挑什么**：图不可读/轴与研究对象不符；红绿色盲不友好；关键显著结果只在表里、正文图画的是非重点；补充表像软件原始输出；三维图无理由。

**真实原句**
- "the red-green contrast needs to be changed in first figure and you can't just name the colors in the caption if red-green colorblind readers aren't able to distinguish them" — 10.1038/s41559-023-02155-0
- "Fig. 3 is problematic. X-axis reads as seabed temperatures ranging from 0 to 25°c. My understanding is that these should correspond to long-term temperature change over the study period" — 10.1038/s41559-026-03013-5
- "The supplementary tables need much more explanation. These look like raw output of statistics software, not publication-ready tables." — 10.1038/s41559-023-02044-6

**审稿要点**：每图独立可读（不看正文知道画的是什么）；色盲安全；最重要的结果在正文图里。

## 15. data_code — 数据与代码可得性（major 7.8% · NEE 13.5 且提及 37.6% · 135 条 major）

**挑什么**：违反期刊数据归档政策；元数据/accession 缺失；**有人真的会跑你的代码**："When I ran the data and code, I was unable to reproduce the exact values for every test I conducted." — 10.1038/s41559-023-02235-1；只给物种平均不给原始数据；数据声明与项目网站政策矛盾。

**审稿要点**：检查数据归档合规与可复现性——真有审稿人会下载代码复现全部数字；EL 有强制归档政策，NEE 检查 data availability 完整性。

## 16. other — 伦理/政策/杂项（major 1.5% · 27 条 major）

伦理审批与动物处理说明、作者贡献合规、政策建议的危险性（buffer-zone 建议被要求撤回）、期刊格式不符（Nature 体投 EL）。小概率但出现时杀伤力大——伦理缺失可直接拒稿。

---

## 期刊风格速记

| | EL（1034 篇） | NEE（460 篇） |
|---|---|---|
| 第一攻击点 | framing（52.7%） | stats（**60.4%**） |
| 前五类 | framing, stats, interpretation, definitions/methods_reporting, causality | stats, interpretation, methods_reporting, causality, framing |
| 更狠的地方 | 概念叙事与文献覆盖 | 统计+数据本身（data 48.7% vs EL 28.2%）+ 稳健性 |
| 决定分布 | 严（大修/拒重投/拒）932/1034 | 严 118/460（修改为主），但严组攻击密度更高 |
| 立场 | positive 44% | mixed 41% |

**研究类型对照**（major%，n）：experimental（n=225）design 50.2 是独有高危；observational（n=562）stats 60.7/data 45.0；meta_analysis（n=118）stats 65.3/data 51.7；synthesis_review（n=126）framing 70.6/novelty 41.3/presentation 41.3；methods（n=70）novelty 42.9/model_theory 35.7；theory_model（n=142）**model_theory 72.5**、framing 55.6。
