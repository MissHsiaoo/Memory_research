# 2026-11-23 arXiv LLM Memory 精选（20 篇）

本批次已完成 20 篇中文评析及 20 份官方 PDF 核验；补读整理日期为北京时间 **2026-11-24**。按官方 **2026-11-23 New submissions** 归档，不计入 11 月 24 日新论文。文末保留此前待公告记录，旧状态仅代表当时核验结果。

## 批次与筛选依据

核验来源：[cs new](https://arxiv.org/list/cs/new)、[stat.ML new](https://arxiv.org/list/stat.ML/new)。本次读取的列表标题均为 Monday, 23 November 2026；cs 新投稿 648 条、stat.ML 新投稿 7 条，合计去重 655 条。仅处理 New submissions，不使用 Cross-lists 或 Replacements。扫描全部标题与摘要，下载核读 29 篇候选全文，最终选取 20 篇；不是对全部 655 篇进行了全文机构审计。

[官方公告时间表](https://info.arxiv.org/help/availability.html)中美国 EST 11 月 22 日 20:00 对应北京时间 11 月 23 日 09:00；此前 08:09 的 pending 检查早于该时间。批次最终以实际列表标题与归属核验，不能只由时间表推断。首次提交日期单列在各笔记中；SDG 的官方首次提交日期为 10 月 16 日，但本次列于 11 月 23 日 New submissions，保留这一差异，不改写成 11 月提交。

机构以 PDF 首页署名核验，A 为优先产业研究机构，B 为优先研究型高校/实验室，C 为少量黑马补充。先按机构层级排序，同层再考虑直接相关性、方法洞见和实验质量；可信度独立评分。PDF 全文已解析并重点核读方法、实验、局限，未独立复现实验，也不声称逐行审计全部附录。

## 排名与文件

| 排名 | 论文与中文评析 | 机构层级 | 研究标签 | 可信度 | PDF |
|---|---|---|---|---|---|
| 1 | [Context-Bank](01-Context-Bank.md) · [arXiv](https://arxiv.org/abs/2611.26775) | A：优先产业研究机构 | retrieval memory；ICL；一致性与泛化 | 4/5 | [原文](pdfs/2611.26775.pdf) |
| 2 | [CSPD](02-CSPD.md) · [arXiv](https://arxiv.org/abs/2611.27376) | A：优先产业研究机构合作 | latent memory；soft prompt；continual post-training | 4/5 | [原文](pdfs/2611.27376.pdf) |
| 3 | [CoEvoBench](03-CoEvoBench.md) · [arXiv](https://arxiv.org/abs/2611.27116) | A：优先产业研究机构合作 | self-evolving agents；模型-harness共同优化；benchmark | 4/5 | [原文](pdfs/2611.27116.pdf) |
| 4 | [Contexture](04-Contexture.md) · [arXiv](https://arxiv.org/abs/2611.26980) | A：优先产业研究机构合作 | working memory；context eviction；KV serving | 4/5 | [原文](pdfs/2611.26980.pdf) |
| 5 | [MemOnce](05-MemOnce.md) · [arXiv](https://arxiv.org/abs/2611.27973) | B：强研究型高校/实验室 | latent memory；KV decoding；sparse retrieval | 4/5 | [原文](pdfs/2611.27973.pdf) |
| 6 | [SDG](06-SDG.md) · [arXiv](https://arxiv.org/abs/2611.26637) | B：强研究型高校/实验室 | recurrent memory；linear attention；forget gate | 4/5 | [原文](pdfs/2611.26637.pdf) |
| 7 | [QueryLM](07-QueryLM.md) · [arXiv](https://arxiv.org/abs/2611.26809) | B：强研究型高校/实验室 | retrieval memory；search-native pretraining | 4/5 | [原文](pdfs/2611.26809.pdf) |
| 8 | [Self-Hallucination](08-Self-Hallucination.md) · [arXiv](https://arxiv.org/abs/2611.26863) | B：强研究型高校/实验室 | parametric memory；post-training；memory contamination | 4/5 | [原文](pdfs/2611.26863.pdf) |
| 9 | [BATON](09-BATON.md) · [arXiv](https://arxiv.org/abs/2611.26902) | B：强研究型高校/实验室 | visual latent memory；KV transfer；small-large cascade | 4/5 | [原文](pdfs/2611.26902.pdf) |
| 10 | [AstronautBench](10-AstronautBench.md) · [arXiv](https://arxiv.org/abs/2611.26910) | B：强研究型高校参与，部分作者机构未署名 | multi-objective memory evaluation；episodic evidence；self-improvement | 3/5 | [原文](pdfs/2611.26910.pdf) |
| 11 | [ZhuLong-SE](11-ZhuLong-SE.md) · [arXiv](https://arxiv.org/abs/2611.26912) | B：强研究型高校/产业合作 | agent memory；skill evolution；verified experience | 3/5 | [原文](pdfs/2611.26912.pdf) |
| 12 | [MedicalRSI](12-MedicalRSI.md) · [arXiv](https://arxiv.org/abs/2611.26806) | B：强研究型高校/实验室 | self-evolving agent memory；model-harness co-evolution | 4/5 | [原文](pdfs/2611.26806.pdf) |
| 13 | [STYLEPRISM](13-STYLEPRISM.md) · [arXiv](https://arxiv.org/abs/2611.27211) | B：强研究型高校/产业合作 | personalized memory；style profile；long-form generation | 4/5 | [原文](pdfs/2611.27211.pdf) |
| 14 | [Belief-State](14-Belief-State.md) · [arXiv](https://arxiv.org/abs/2611.27286) | B：强研究型高校/实验室 | working memory；belief state；multi-objective rubric | 3/5 | [原文](pdfs/2611.27286.pdf) |
| 15 | [Open-CDLM](15-Open-CDLM.md) · [arXiv](https://arxiv.org/abs/2611.27536) | B：强研究型高校/实验室 | diffusion LLM；benchmark；distributional evaluation | 3/5 | [原文](pdfs/2611.27536.pdf) |
| 16 | [Tasklets](16-Tasklets.md) · [arXiv](https://arxiv.org/abs/2611.27607) | B：强研究型高校/实验室 | latent memory benchmark；recall；state tracking；multi-task | 4/5 | [原文](pdfs/2611.27607.pdf) |
| 17 | [Embodied-Harness](17-Embodied-Harness.md) · [arXiv](https://arxiv.org/abs/2611.27689) | B：强研究型高校/实验室 | agent memory；hierarchical memory；embodied self-improvement | 3/5 | [原文](pdfs/2611.27689.pdf) |
| 18 | [EvoTER](18-EvoTER.md) · [arXiv](https://arxiv.org/abs/2611.27797) | B：强研究型高校/实验室 | procedural memory；skill library；validation-gated evolution | 4/5 | [原文](pdfs/2611.27797.pdf) |
| 19 | [NavRSI](19-NavRSI.md) · [arXiv](https://arxiv.org/abs/2611.27499) | B：强研究型高校/实验室 | self-evolving memory；designer experience；navigation | 3/5 | [原文](pdfs/2611.27499.pdf) |
| 20 | [Experience-Selection](20-Experience-Selection.md) · [arXiv](https://arxiv.org/abs/2611.27159) | C：黑马/启发性补充，机构优先级较低 | continual learning；experience replay；gradient selection | 4/5 | [原文](pdfs/2611.27159.pdf) |

## 机构分布

按论文最高优先层级计：A 级 4 篇，B 级 15 篇，C 级 1 篇。合作机构不互斥：Google 1 篇；Apple/NVIDIA 合作 1 篇；Alibaba 1 篇；Microsoft 1 篇。中科大、浙江大学、上海交大、北京大学各出现在 2 篇入选论文中。其余包括南京大学、EPFL、多伦多大学、Cornell、CMU、Northwestern、华盛顿大学、芝加哥大学、Mila、RIKEN、中科院自动化所等。逐篇完整核验署名见笔记；不根据作者履历补写未署名机构。

Experience-Selection 为 C 级“黑马/启发性补充”：机构优先级较低，因持续学习经验选择的受控对照与失败实验有直接方法启发而收录；不因此把机构层级上调。

## 最值得深读的 3 篇

1. **MemOnce**：直接处理可扩展潜在记忆；适合研究记忆压缩与历史信息访问。重点核对平均收益与 LoCoMo 单项退步，以及活跃 GPU 状态和全部历史存储的区别。
2. **CSPD**：用可组合软提示保存领域专家能力，与多目标共享记忆直接相关。重点看组合是否产生负迁移、四领域任务和六项保留评测的边界。
3. **Context-Bank**：把记忆库内部约定冲突与单条事实正确性分开，给出超出记忆库范围的泛化评测。可启发个人偏好变更、企业规则与技能库一致性管理。

## 主题趋势与研究判断

- 潜在记忆与软提示开始共同讨论压缩、可组合性与任务干扰；平均分提升不足以说明每个目标都获益。
- 外部记忆库质量评估从命中率扩展到一致性、证据来源、时效和泛化距离。
- 跨回合自我改进越来越依赖工具接口、技能库与执行环境共同变化；应拆开模型、记忆和 harness 的贡献。
- 扩散语言模型评测开始组织统一任务集，但试点规模与成熟稳定的排行榜仍需区分。

以上趋势是本次阅读判断，不是论文共同证明的结论。

## 多目标记忆使用 benchmark：本批次可用线索

你此前问的“多目标记忆使用”可从 **AstronautBench**（知识、证据、进度状态）、**Tasklets**（16 个任务、7 类能力）入手；**CSPD** 提供多领域组合与保留能力评测协议，但不能直接称作统一多目标记忆 benchmark。三者任务定义不同，不能把分数直接横向合并。

后续实验建议（本次推断）：固定同一记忆写入预算，同时评估事实问答、个性化生成、规划任务；分别报告正确性、偏好遵循、遗忘、延迟和存储成本，并画 Pareto 曲线、报告最差任务退化，避免一个平均数掩盖负迁移。

## 可复核材料

- [文件清单与 SHA-256](manifest.json)：20 篇的提交记录、页数、PDF 哈希、机构与笔记路径。
- [655 条新投稿标题清单](batch-new-submissions.json)：本次官方 New submissions 候选池。
- [29 篇全文候选筛选记录](screening.md)。
- PDF 均为实际文件，已解析、检查页数并核对笔记相对链接；未把网页错误响应当 PDF。

---

## 原始核验记录（原文保留；状态仅指当时）

# 2026-11-23 arXiv LLM Memory 日报（待公告）


## 批次核验 2026-11-23T08:09:48.065371+08:00

状态：pending。报告日期为北京时间 2026-11-23，触发时间 08:09:13。今日正式新批次尚未在所查官方列表中可见。

- [cs](https://arxiv.org/list/cs/new)：Showing new listings for Friday, 20 November 2026；New submissions (showing 822 of 822 entries)。
- [cs.CL](https://arxiv.org/list/cs.CL/new)：Showing new listings for Friday, 20 November 2026；New submissions (showing 64 of 64 entries)。
- [cs.AI](https://arxiv.org/list/cs.AI/new)：Showing new listings for Friday, 20 November 2026；New submissions (showing 109 of 109 entries)。
- [cs.LG](https://arxiv.org/list/cs.LG/new)：Showing new listings for Friday, 20 November 2026；New submissions (showing 119 of 119 entries)。
- [stat.ML](https://arxiv.org/list/stat.ML/new)：Showing new listings for Friday, 20 November 2026；New submissions (showing 14 of 14 entries)。

以上均为官方 11 月 20 日批次，不计入 11 月 23 日。按[官方公告时间表](https://info.arxiv.org/help/availability.html)，美国 EST 11 月 22 日星期日 20:00 对应北京时间 11 月 23 日星期一 09:00；本轮核验在该计划时间之前。计划时间不代替实际批次核验，不能据此断言今日休刊或无合格论文。

未将提交日期视为公告日期，未使用旧论文、更新版本或近 30 天论文凑数。正式入选清单、机构分布、主题趋势、最值得深读的 3 篇均待当日批次可见后确定，当前不作评析与可信度评分。今日没有下载 PDF，也没有本地 PDF 链接。完整交付尚未完成，未将待公告记录作为完整日报提交推送；本地仓库工作区干净，无本轮待推提交。过去日期内容未修改。
