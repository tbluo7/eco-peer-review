# 数据来源与重建手册

> 本文件记录 `eco-peer-review` 语料的**可验证来源**、**已知缺陷**与**重建方法**。
> 目的：下次需要重建或扩展语料时，不必重新反推一遍。
> 最后核验：2026-10-26。

---

## 1. 来源（已逐字验证）

语料不是数据库采购，也不是二手转引。原始载体是**出版社公开的同行评审档案 PDF**。

| 项 | 值 |
|---|---|
| 来源 | Nature Portfolio 公开的 `Peer Review File` / `Peer Review Information` PDF（作者 opt-in） |
| URL 模板 | `https://media.springernature.com/original/springer-static/esm/art%3A{DOI}/MediaObjects/{ID}_MOESM{N}_ESM.pdf` |
| 定位方式 | 抓文章页 HTML，取 `<a>` 锚文本含 `Peer Review` 的链接 |
| 文章页 | `https://www.nature.com/articles/{DOI 后缀}` |

**验证记录**：`10.1038/s41559-022-01679-1` → `MOESM3`，30 页，首页标题 `Peer Review Information`。
语料中该篇的一条 stats major 原话（153 字符）在该 PDF 内**逐字命中**：

> "I think my real question is that are the authors autocorrelating? In Fig. S2, examples of cpG sites that do not relate to chronological age are provided."

⚠️ **MOESM 编号不固定**。同一篇里 `MOESM1` 可能是补充信息、`MOESM2` 是 Reporting Summary、`MOESM3` 才是评审档案；不同文章顺序会变。**必须按锚文本或首页内容判别，不能按序号取**。

## 2. 覆盖范围与已知缺口

| 期刊 | 篇数 | 状态 |
|---|---:|---|
| NEE（Nature Ecology & Evolution） | 460 | 可复现，来源已验证 |
| EL（Ecology Letters） | 1034 | **来源未打通**：Wiley 对直连请求返回 403（Cloudflare） |

EL 的档案若需重建，需另辟途径（浏览器会话或官方 API），不要假设与 NEE 同构。

## 3. 生成时间线

| 时间 | 事件 |
|---|---|
| 2026-10-06 01:36:36 | `papers_all` / `comments_all` / `paper_index` 写入 |
| 2026-10-06 02:06 | `playbooks.md` / `stats_overview.md` 生成 |
| 2026-10-26 03:20:41 | 装入 skill 目录 |

**原始采集与抽取脚本未随数据保留**，机器上已无副本。本文件即为替代品。

## 4. 处理链

```
公开 PRF PDF
  → 文本抽取
  → LLM 结构化（DeepSeek V4.1 Flash，见 stats_overview 自述）
  → 原句逐字校验
  → 与 GLM 在 414 篇重叠上交叉验证（召回 83%、主次一致 91%）
  → comments_all.jsonl（48422 行）
```

字段映射：`cid / severity / category / issue / request / quote`；论文层另有 `stance / expertise / system / study_type / decision`。

## 5. 已知数据缺陷（引用前必读）

| 缺陷 | 事实 | 影响 |
|---|---|---|
| **`topic` 字段不可信** | 210 个自由文本标签；置信度中位数 0.9991，78.4% > 0.99；错标常见（土拨鼠冬眠→"Bat Biology"、脑容量实验→"Fish biology"） | 这是 LLM 自评置信度，不是校准概率。**skill 未使用该字段**；不要引用 |
| `study_type` 疑为 LLM 标注 | 分布合理但未经人工核验 | 按研究类型统计的表依赖它，抽查后再引用 |
| 2 篇零意见 | `10.1038/s41559-025-02863-9`、`10.1038/s41559-026-03068-4`，`n_comments=0` | 与 index 自洽，非掉行 |
| `article_type` 不全 | 963/1494（64.5%） | 按类型筛选时注意缺失 |
| 无作者回复 / 无后续轮 / 无桌拒 | 全部 1494 篇 `n_reviewers_r1 ≥ 1` | 源 PDF **实际含**作者 rebuttal 与第二轮，是管线丢弃所致，非源限制 |
| 选择偏差 | 只含已送审稿 | 桌拒样本结构性缺失 |

## 6. 重建 rebuttal 层的方法（本次会话验证）

PRF 内部按年代分两套版式：

**Format A（2022–2024，标题为 `Peer Review Information`）**

```
Decision Letter, initial version
Reviewers' comments → Reviewer #1/#2/#3 (Remarks to the Author)
Author Rebuttal to Initial comments     ← 起点
Decision Letter, first revision         ← 终点；其后为第二轮
```

**Format B（2025–2026，标题为 `Peer Review File`）**

```
Version 0 / 1 / 2 ...
Reviewers' comments
Authors' responses to reviewers         ← 起点（标题不统一）
```

实测标题变体（8 种，均出现过）：

```
Author Rebuttal to Initial comments
Author Rebuttal, first revision:
Author Rebuttal, second revision:
Authors' responses to reviewers
Response to Reviewers
Point-by-point response to reviewer's comments
<Responses and comments to Reviewer #1>
（无标题，直接接正文）
```

### 实测结论

20 篇分层抽样（每年 4 篇）：

| 结果 | 数量 |
|---|---:|
| 边界干净可直接用 | 4 |
| 有正文但起点可疑 | 11 |
| 完全切不出 | 5 |

**纯正则不可用**。失败原因：
- 作者 response 是原样附加，格式由作者决定
- 正文夹带被引用的审稿意见、编辑决定信、CC 版权页
- 决定信里的项目符号 `* Include a "Response to reviewers" document...` 会被误判为章节标题
- 约 10% 的 rebuttal 是扫描图片（本机无 OCR）

**可行路线**：LLM 逐篇切分。Format B 的结构其实更规整（`Version N` + `Reviewer #N` 分段清晰），只是标题不统一——这正是 LLM 擅长的「结构在、标签乱」。

## 7. 复现所需依赖

| 依赖 | 状态 |
|---|---|
| Python | 3.13.7 |
| PyMuPDF (`fitz`) | 已装 |
| pypdf | 已装 |
| tesseract / pytesseract | **未装**（扫描件无法处理） |
| 网络 | 可直连 `nature.com` 与 `media.springernature.com`；`onlinelibrary.wiley.com` 403 |

## 8. 未解决项

1. EL（1034 篇）的来源通道
2. rebuttal 层的自动切分精度
3. 扫描版 rebuttal 的 OCR
4. `study_type` / `system` 字段的人工抽检
