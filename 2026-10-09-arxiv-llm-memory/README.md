# 2026-10-09 arXiv LLM Memory 日报

状态：**已完成，20 篇**。本报告只收录 arXiv **2026-10-09 正式公告批次**的主分类 `New submissions`，且 API 条目均为 v1；首次提交日期另列在每篇笔记，可能是 10 月 7 或 8 日，不能当成公告日期。该批次出现时北京时间同为 10 月 9 日。[逐篇主分类核验记录](sources/primary-category-verification.json)、[提交元数据](sources/metadata.json)、[PDF 页数与哈希](verification.json)可复查。正式列表涉及 [cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)，另对 cs.CV、cs.AR、stat.ML 的入选主分类独立核验。

## 筛选和排序

扫描 [cs.CL](sources/2026-10-09/cs.CL-listing.html)、[cs.AI](sources/2026-10-09/cs.AI-listing.html)、[cs.LG](sources/2026-10-09/cs.LG-listing.html)、[cs.CV](sources/2026-10-09/cs.CV-listing.html) 四类官方 new 快照后去重得到 737 条新稿/交叉列出候选；标题与摘要筛选后，下载 34 篇候选 PDF，查首页机构以及方法、实验、局限，最终选 20 篇。排序遵循 **机构优先级 → 研究主题直接相关性 → 方法新颖性**，同层级再看严谨性与潜在影响。S 为用户优先指定的大型企业及全球一流高校/实验室，A+ 为大型企业研究与强研究机构，A 为方法明显突出的启发性补充；这只是本次阅读优先级，不评价作者。证据可信度 1–5 分完全独立于机构质量。第 12 篇明确为“弱相关但具启发性”，第 19–20 篇为较低机构优先级补充。Novelty 是我的判断，非论文自证。

| 排名 | 论文与为何入选 | PDF 首页核验机构 | 机构 / 相关性 / novelty | 可信度 |
|---|---|---|---|---|
| 01 | [REMORY](01-REMORY.md) · [arXiv](https://arxiv.org/abs/2610.11287)：摘要之外的连续残差记忆，直接切入 latent memory。 | Alibaba Group / 复旦 / 上海交大等 | S / 直接 / 高 | 4/5 |
| 02 | [DPPM](02-DPPM.md) · [arXiv](https://arxiv.org/abs/2610.11776)：稳定证据与近期变化双路径参数化个人记忆。 | USTC / iFLYTEK | S / 直接 / 高 | 3/5 |
| 03 | [MARI](03-MARI.md) · [arXiv](https://arxiv.org/abs/2610.11501)：将行为决策理由存为可检索的结构化记忆。 | Alibaba Group | S / 直接 / 高 | 3/5 |
| 04 | [UXBench Pro](04-UXBench-Pro.md) · [arXiv](https://arxiv.org/abs/2610.11638)：揭示个人化评测对用户群和评估者信息的依赖。 | Tencent Yuanbao / 香港理工 | S / 直接 / 高 | 3/5 |
| 05 | [CogMem](05-CogMem.md) · [arXiv](https://arxiv.org/abs/2610.11314)：保留主张来源与时序的可演化对话图记忆。 | 清华大学 | S / 直接 / 高 | 4/5 |
| 06 | [DeltaReplay](06-DeltaReplay.md) · [arXiv](https://arxiv.org/abs/2610.11707)：仅按当前任务可迁移的步骤复用 GUI 轨迹。 | 清华大学 | S / 直接 / 高 | 4/5 |
| 07 | [非线性 teacher 的 ICL 理论](07-Harvard-ICL.md) · [arXiv](https://arxiv.org/abs/2610.10761)：给线性注意力 ICL 的表达边界。 | Harvard / Kempner | S / 直接 / 高 | 4/5 |
| 08 | [Reward in Context](08-KAIST-reward-ICL.md) · [arXiv](https://arxiv.org/abs/2610.11152)：奖励置乱检验 agent 是否真从上下文反馈学习。 | KAIST | S / 直接 / 高 | 4/5 |
| 09 | [LadderEdit](09-LadderEdit.md) · [arXiv](https://arxiv.org/abs/2610.11160)：逐条按需压缩终身编辑的参数记忆。 | Yale / Washington University 等 | S / 直接（持续学习）/ 高 | 4/5 |
| 10 | [DynaTE](10-DynaTE.md) · [arXiv](https://arxiv.org/abs/2610.11284)：动态 token 执行加速 diffusion LLM。 | 浙江大学 | S / 直接 / 高 | 3/5 |
| 11 | [EFRE](11-EFRE.md) · [arXiv](https://arxiv.org/abs/2610.11373)：把持续学习的规则存为可分叉的函数库。 | CUHK(SZ) / USTC / 上海 AI Lab | S / 直接 / 高 | 3/5 |
| 12 | [SynCo](12-SynCo.md) · [arXiv](https://arxiv.org/abs/2610.11345)：合成器和 learner 共演化；**弱相关但具启发性**，可借鉴经验生成。 | USC / Georgia Tech 等 | S / 弱相关 / 高 | 3/5 |
| 13 | [SGUID](13-SGUID.md) · [arXiv](https://arxiv.org/abs/2610.12367)：筛选真正值得蒸馏进模型的技能。 | Amazon / NYU | A+ / 直接 / 高 | 4/5 |
| 14 | [Coding Agent Thoughts](14-AWS-ARC-thoughts.md) · [arXiv](https://arxiv.org/abs/2610.11450)：文件轨迹暴露程序性记忆的保留与遗忘。 | AWS | A+ / 直接 / 高 | 3/5 |
| 15 | [Plan-and-Patch](15-Plan-and-Patch.md) · [arXiv](https://arxiv.org/abs/2610.10786)：扩散 LLM 的局部计划修复。 | Amazon / UT Austin | A+ / 直接 / 高 | 3/5 |
| 16 | [MemoType](16-MemoType.md) · [arXiv](https://arxiv.org/abs/2610.11573)：按记忆与问题类型路由检索策略。 | CityU Hong Kong / Huawei Noah’s Ark | A+ / 直接 / 中高 | 3/5 |
| 17 | [Gated Memory](17-Gated-Memory.md) · [arXiv](https://arxiv.org/abs/2610.11270)：记忆抽取前先判定是否应写入。 | Samsung Research America | A+ / 直接 / 中高 | 3/5 |
| 18 | [Hippocam](18-Hippocam.md) · [arXiv](https://arxiv.org/abs/2610.12124)：意图巩固和分层回查让经验“用进废退”。 | CAS 信息工程所 / UCAS | A+ / 直接 / 中高 | 3/5 |
| 19 | [Skill-V](19-Skill-V.md) · [arXiv](https://arxiv.org/abs/2610.11781)：可证伪契约让旧技能能被验证和修订。 | 厦门大学 / Kuaishou / 南开 | A（启发性补充）/ 直接 / 高 | 3/5 |
| 20 | [Memory Governance](20-Memory-Governance.md) · [arXiv](https://arxiv.org/abs/2610.11188)：把记忆准入与呈现分开，并报告过滤伤害个性化的负结果。 | Pazhou Laboratory；第二作者机构未核验 | A（启发性补充）/ 直接 / 高 | 4/5 |

## 机构分布与主题趋势

按本次阅读层级：S 12 篇、A+ 6 篇、A 2 篇。按 PDF 首页出现的机构类别（合作论文会重复计入）看，头部/大型企业和产业研究包括 Alibaba 2、Tencent 1、Amazon/AWS 3、Huawei 1、Samsung 1、iFLYTEK 1、Kuaishou 1；学术与公共研究包括清华 2、USTC 2、Harvard 1、KAIST 1、Yale 1、浙江大学 1、USC 1、CAS/UCAS 1 等。这个分布不是互斥署名计数，不能加总为 20。

我的主题归纳：一条主线是“何时写入、允许谁读取、如何撤回/更新”（CogMem、Gated Memory、Memory Governance）；一条是从原始文本转向连续或参数化记忆（REMORY、DPPM、LadderEdit）；程序性经验则开始要求可迁移、可证伪和有边际价值（DeltaReplay、SGUID、Skill-V、Hippocam）。ICL 理论与奖励置乱提醒，不应把任何性能提升都归因于真正学习；diffusion LLM 则聚焦局部修复和动态执行。上述是对论文的跨篇归纳，并非其共同验证的结论。

## 今天最值得深读的 3 篇

1. **REMORY**：最贴近 latent memory 的工程问题；等位置文本对照、来源归因及长程 agent 评估让它适合复现，但需补算总成本。
2. **CogMem**：明确区分主观 Claim 与 Fact，知识更新消融很强；适合研究个性化记忆中的来源归属与时序冲突。
3. **Reward in Context**：用奖励/轨迹置乱挑战“agent 从记忆中学会策略”的常见解释，可直接改善今后的实验对照设计。

## 核验与保留的时间记录

20 份本地官方 PDF 均通过 `%PDF-` 文件头、可解析页数、主分类 10 月 9 日 `New submissions` 和 arXiv v1 检查，共 **405 页、39,060,189 字节**；每篇页数与 SHA-256 见 [verification.json](verification.json)。每份笔记均核对 PDF 首页机构，并阅读方法、实验和局限相关段落；“未来影响”和测试建议为我的推断。额外候选如 [CAS 的事件图记忆](https://arxiv.org/abs/2610.11920)、[JD 的表格 ICL 压缩](https://arxiv.org/abs/2610.11784)、[北航/CAS 的持续学习通道选择](https://arxiv.org/abs/2610.11076) 已审阅但未挤入 20 篇：分别与 CogMem、latent/ICL 压缩或 EFRE/LadderEdit 的当天覆盖方向重叠；这些不是本日报告的入选论文。

- 北京时间 08:01（UTC 00:01）：三个主要官方 new 列表均仍显示 10 月 8 日，记为 pending，未纳入旧批次。
- 北京时间 09:01（UTC 01:01）：三类仍为 10 月 8 日。
- 北京时间 10:01（UTC 02:01）：三类仍为 10 月 8 日。
- 北京时间约 11:02（UTC 03:02）：三类正式列表均切换为 10 月 9 日；随后核验 cs.CV、cs.AR、stat.ML 主分类与入选 PDF，完成本报告。
