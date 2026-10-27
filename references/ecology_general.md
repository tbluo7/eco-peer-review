# 生态学通用层（按研究类型 + 术语桥）

## 为什么需要这一层

`ecology_kill_list.md` 用的是 EL / NEE 的措辞。做恢复生态、渔业、毒理、农业的人
不一定这么说话，但撞的是同一批设计问题。本文件做两件事：

1. **按研究类型给出头部风险**（有语料支撑，附 n）
2. **子领域术语桥**（判断层，把不同说法映射到同一问题）

## 口径

- 数据：48,422 条 EL / NEE 首轮意见；类别标签 `study_type`
- `major率` = 该问题被提及的意见中被评为 major 的比例
- 单元格 n ≥ 15 才列出；n < 30 的条目标了 ⚠，仅作提示不作依据
- 关键词为代理指标，非人工编码

---

## 一、按研究类型的头部风险

### 观测 / 野外相关研究（`observational`，n=18991，major 基线 28.5%）

| 风险 | 提及 n | major 率 | vs 本类基线 |
|---|---:|---:|---:|
| 伪重复 ⚠ | 29 | **72.4%** | +43.9 |
| 多重比较 ⚠ | 24 | **62.5%** | +34.0 |
| 检测概率 ⚠ | 18 | **61.1%** | +32.6 |
| 空间自相关 | 41 | **58.5%** | +30.1 |
| 系统发育 | 52 | **57.7%** | +29.2 |
| SDM ⚠ | 21 | **57.1%** | +28.7 |
| 共线性 | 58 | **55.2%** | +26.7 |
| 外推 | 116 | **52.6%** | +24.1 |

### 受控实验（`experimental`，n=7676，major 基线 27.5%）

| 风险 | 提及 n | major 率 | vs 本类基线 |
|---|---:|---:|---:|
| 伪重复 ⚠ | 15 | **93.3%** | +65.8 |
| 共线性 ⚠ | 16 | **62.5%** | +35.0 |
| 外推 | 45 | **51.1%** | +23.6 |
| 随机效应 | 61 | **49.2%** | +21.7 |
| 尺度错配 | 42 | **47.6%** | +20.1 |
| 多重比较 ⚠ | 15 | **46.7%** | +19.1 |
| 中宇宙 | 54 | **46.3%** | +18.8 |
| 效应量/CI | 62 | **45.2%** | +17.6 |

### 观测 + 实验混合（`mixed`，n=8395，major 基线 30.9%）

| 风险 | 提及 n | major 率 | vs 本类基线 |
|---|---:|---:|---:|
| 尺度错配 | 39 | **66.7%** | +35.8 |
| 外推 | 74 | **62.2%** | +31.3 |
| 过拟合/CV | 41 | **43.9%** | +13.0 |
| 随机效应 | 50 | **42.0%** | +11.1 |
| 效应量/CI | 70 | **41.4%** | +10.5 |
| 中宇宙 ⚠ | 20 | **35.0%** | +4.1 |

### 整合分析 / meta-analysis（`meta_analysis`，n=4134，major 基线 28.1%）

| 风险 | 提及 n | major 率 | vs 本类基线 |
|---|---:|---:|---:|
| 尺度错配 | 46 | **56.5%** | +28.4 |
| 过拟合/CV ⚠ | 21 | **52.4%** | +24.2 |
| 随机效应 | 48 | **47.9%** | +19.8 |
| 外推 ⚠ | 25 | **44.0%** | +15.9 |
| 效应量/CI | 170 | **42.4%** | +14.2 |

### 理论模型 / 模拟（`theory_model`，n=3933，major 基线 29.3%）

| 风险 | 提及 n | major 率 | vs 本类基线 |
|---|---:|---:|---:|
| SDM ⚠ | 18 | **55.6%** | +26.2 |
| 外推 ⚠ | 24 | **50.0%** | +20.7 |

### 综述 / 观点文（`synthesis_review`，n=3472，major 基线 28.5%）

| 风险 | 提及 n | major 率 | vs 本类基线 |
|---|---:|---:|---:|
| 过拟合/CV ⚠ | 19 | **52.6%** | +24.1 |
| 尺度错配 ⚠ | 25 | **44.0%** | +15.5 |
| 外推 ⚠ | 22 | **36.4%** | +7.8 |

### 方法学论文（`methods`，n=1821，major 基线 32.5%）

| 风险 | 提及 n | major 率 | vs 本类基线 |
|---|---:|---:|---:|
| 过拟合/CV ⚠ | 18 | **16.7%** | -15.8 |

**读法示例**：做受控实验的稿子，只要被提伪重复，93% 是 major——这是最高危的单点；
而做方法学论文的，过拟合/CV 只有 16.7%，低于基线，说明方法刊更在意别的东西。

**注意**：`theory_model` 这一类在本表里条目很少，因为理论模型的风险主要不在统计词汇上，
而在模型结构假设与数学可比性——见 `playbooks.md` §13，那里 72.5% 的命中率才是它的主战场。

---

## 二、子领域术语桥（判断层）

同一批设计问题，不同子领域的说法不一样。**下表无对应语料，是按学科惯例做的映射**，
用于把「你的说法」翻译成「语料能查的说法」，再回 `ecology_kill_list.md` 取证据。

| 底层设计问题 | EL/NEE 语料里的说法 | 其他子领域常见说法 |
|---|---|---|
| 重复不独立 | pseudoreplication / unit of replication | 恢复生态：unreplicated restoration sites；渔业：pooled hauls；毒理：tank effects；农业：split-plot 混淆；微生物：batch effects |
| 空间结构未处理 | spatial autocorrelation | 景观生态：spatial dependence；病害：spatial clustering；遥感：pixel-level autocorrelation；土壤：field-scale trend |
| 只观测到「出现」，未校正检出率 | imperfect detection / occupancy model | 渔业：catchability；野生动物：survey detection；eDNA：false negatives；植物：detectability by life stage |
| 用空间梯度替代时间 | chronosequence / space-for-time | 恢复生态：restoration chronosequence；古生态：stratigraphic substitution；土壤：cultivation sequence |
| 预测超出数据范围 | extrapolation / generality | 保护：SDM transferability；渔业：stock–recruitment transfer；农业：regional scaling；气候：novel climates |
| 环境变量彼此同源 | collinearity / VIF | 生态系统：confounded gradients；农业：management covariance；城市：socioeconomic confounding |
| 人工系统与自然系统差距 | mesocosm / enclosure / common garden | 水生：pond mesocosm；土壤：microcosm；草地：common garden；鱼类：tank experiment |
| 跨物种比较未校正亲缘 | phylogenetic signal / PGLS | 宏生态：comparative method；微生物：phylogenetic distance decay；植物：trait phylogeny |

---

## 三、语料没覆盖的子领域（必须打折）

下列方向在 EL / NEE 语料里样本极少或缺失，**本库的比例不能直接套用**：

| 方向 | 为什么没覆盖 | 建议 |
|---|---|---|
| 毒理学 / 风险评估 | EL/NEE 极少发剂量-反应与风险评估 | 用本库的设计层，不用它的比例 |
| 渔业资源评估 | 种群评估、stock assessment 属专业刊 | 同上；另需 ICES/NOAA 的评估规范 |
| 恢复生态的参照系问题 | reference condition 的设定标准不在期刊评审话术里 | 用第 0 关的“值不值得做”逻辑 |
| 农业生态 / 农学 | 样本极少（system 字段命中 <5） | 仅借用统计与设计层 |
| 城市生态 | 样本 17 篇，比例不稳 | 仅作定性提示 |
| 古生态 / 地层 | 样本 29 篇 | 仅作定性提示 |
| 保护遗传学 / 管理决策 | 政策与法律维度不在语料内 | 用第 0 关 + 外部规范 |

---

## 四、怎么用

```
1. 先定位研究类型 → 读第一节对应的表，拿到该类型的前 5–8 个头部风险
2. 如果你的子领域用词不同 → 查第二节术语桥，找到对应的底层问题
3. 回 ecology_kill_list.md 取自查问句与真实原话
4. 如果你的方向在第三节的缺口表里 → 明确告诉用户「比例不可套用」，只用设计层
```

## 诚实性

- 第一节为语料统计，可回溯；第二、三节为判断，不得冒充数据
- 研究类型标签本身是 LLM 标注，未经人工核验（见 `provenance.md`）
- 单元格 n 普遍偏小（15–170），比例波动大；⚠ 标记的仅作提示
