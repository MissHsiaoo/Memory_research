# 2026-10-06 arXiv LLM Memory 日报 — 已完成

- 核验时间：2026-10-06 08:02（北京时间，Asia/Shanghai）。
- 官方 [cs.CL/new](https://arxiv.org/list/cs.CL/new)、[cs.AI/new](https://arxiv.org/list/cs.AI/new)、[cs.LG/new](https://arxiv.org/list/cs.LG/new) 均仍显示 **Monday, 5 October 2026** 的正式列表；尚未出现 10 月 6 日批次。
- 当前状态：**pending**，不是“今天没有合格论文”。不得将昨天新稿、仅更新版本或以提交日期推定的论文记入今天，也不扩展到近 30 天。
- 10 月 6 日正式批次可见后再从三个分类的 **New submissions** 筛选、核验 PDF 首页机构、评析实验与局限，并在此文件夹增量交付。

## 增量核验

- 2026-10-06 09:01（北京时间）：cs.CL、cs.AI、cs.LG 官方 `new` 列表仍均显示 10 月 5 日批次；本日仍为 pending，未取用旧稿。
- 2026-10-06 10:01（北京时间）：三类官方 `new` 列表仍均显示 10 月 5 日批次；状态无变化。
- 2026-10-06 11:00（北京时间）：三类官方 `new` 列表仍均显示 10 月 5 日批次；今日正式公告尚未出现。
- 2026-10-06 12:01（北京时间）：三类官方 `new` 列表仍均显示 10 月 5 日批次；今日继续 pending。
- 2026-10-06 14:06（北京时间）：三类官方 `new` 列表均已显示 **Tuesday, 6 October 2026**；cs.CL 143、cs.AI 230、cs.LG 366 篇 `New submissions`。从此刻开始筛选，仅按这三个新稿区计入今日候选。

## 最终交付与筛选口径

- **状态：已完成。** 以上 pending 记录保留为当天的核验过程；它们不再代表当前状态。
- 本报告的日期是 arXiv **正式公告日期 2026-10-06**，对应北京时间 2026-10-06 下午核验到的批次。每篇的首次提交日期另列于独立笔记，二者不能互换。仅纳入 cs.CL、cs.AI、cs.LG 官方 `New submissions` 中的首次新稿；未拿旧稿、替换版或近 30 天论文补数。
- 共收录 **20 篇**，每篇均保存官方 PDF 并逐篇核验 PDF 首页机构、方法、实验和局限；主张与作者自报成绩均在笔记中注明，未来影响与建议为我的推断。PDF 并非同行评审或复现证明，证据可信度与机构优先级分开评估。
- 排序采用**机构优先级 → 与研究问题的直接相关性 → 方法新颖性**。S：所列领先公司/研究院参与；A：全球一流研究型高校/实验室参与。S 中若只是间接启发，已标“弱相关但具启发性”。A 论文不因主题高度相关而越过 S 层，符合本次机构优先的约定；这不是论文质量的绝对排名。

## 入选论文（按优先级）

| 排名 | 论文与笔记 | 机构（PDF 首页核验） | 关联/novelty：为何入选 |
|---:|---|---|---|
| 01 | [Self-Propagating Misalignment in LLM Agents](01-Anthropic-self-propagating-memory-risk.md) · [arXiv](https://arxiv.org/abs/2610.04083) | Anthropic / Anthropic Fellows 等 · S | 直接研究持久记忆如何传播放大 Agent 失配；对记忆系统安全边界重要。 |
| 02 | [Capability-Driven Self-Evolution of Agent Memory](02-PrisMem-capability-memory-evolution.md) · [arXiv](https://arxiv.org/abs/2610.06361) | Microsoft / USTC / UCSD · S | 将记忆积累变成能力驱动的迭代过程，最贴近 self-evolving agent memory。 |
| 03 | [Bayesian Nonparametric Memory](03-IBM-Bayesian-Cheatsheet.md) · [arXiv](https://arxiv.org/abs/2610.06516) | IBM Research AI · S | 用非参数结构在测试时存储和调用推理策略，而不只是检索原文。 |
| 04 | [TrajLong](04-Tencent-TrajLong.md) · [arXiv](https://arxiv.org/abs/2610.04973) | Tencent Hunyuan / HKUST GZ / Peking · S | 将长上下文与 Agent 轨迹共同纳入中期训练，连接 ICL 和长程行动。 |
| 05 | [TeleTune](05-Microsoft-TeleTune.md) · [arXiv](https://arxiv.org/abs/2610.05437) | Microsoft / UNC / UT Austin · S | 从离线操作日志挖掘可复用技能，解决无目标标注的经验学习。 |
| 06 | [Mining Agent Skills from Production Traces](06-Microsoft-production-skills.md) · [arXiv](https://arxiv.org/abs/2610.05777) | Microsoft / MIT · S | 六种技能挖掘配置的跨域实证，重要启示是无通用最佳配方。 |
| 07 | [Causal Improvement Graph](07-Alibaba-causal-improvement-graph.md) · [arXiv](https://arxiv.org/abs/2610.05039) | Alibaba Tongyi / NTU · S | 把优化证据、假设、干预、结果记录成可追踪的 Agent 进化记忆。 |
| 08 | [PB-GRPO](08-Amazon-persona-GRPO.md) · [arXiv](https://arxiv.org/abs/2610.04132) | Amazon · S | persona 模拟的个性化偏好训练；题目直接相关，但仅 workshop/模拟评估，证据弱。 |
| 09 | [ALoDLM](09-Amazon-adaptive-looped-DLM.md) · [arXiv](https://arxiv.org/abs/2610.04198) | Amazon AGI / UIC / Korea U · S | 按 token 难度分配循环计算的扩散 LLM，具有效率与架构启发。 |
| 10 | [Un-OPD for Block Diffusion LMs](10-Alibaba-unbiased-OPD.md) · [arXiv](https://arxiv.org/abs/2610.05373) | Alibaba / CityU HK 等 · S | 针对块扩散蒸馏偏差的校正，影响未来 diffusion LLM post-training。 |
| 11 | [ForkPilot](11-Microsoft-ForkPilot.md) · [arXiv](https://arxiv.org/abs/2610.04889) | Microsoft / Virginia Tech · S | 学习长程 Agent 回溯搜索策略，把失败路径变为可用经验。 |
| 12 | [DUET](12-Microsoft-DUET.md) · [arXiv](https://arxiv.org/abs/2610.04087) | Microsoft / U Virginia · S | **弱相关但具启发性**：solver/grader 共进化，启发记忆质量判别器更新。 |
| 13 | [D-Loop](13-Huawei-D-Loop.md) · [arXiv](https://arxiv.org/abs/2610.06011) | Huawei Research / HKU / CUHK · S | 用循环扩散草稿提高推测解码接受率；对扩散 LLM 系统化应用有启发。 |
| 14 | [FLaRe](14-Samsung-FLaRe.md) · [arXiv](https://arxiv.org/abs/2610.06666) | Samsung AI Cambridge / 研究型高校 · S | **弱相关但具启发性**：潜在推理的五项设计要求可借鉴于 latent memory。 |
| 15 | [MemPilot](15-MemPilot-multimodal-memory.md) · [arXiv](https://arxiv.org/abs/2610.06830) | NTU / Tsinghua / UIUC · A | 按需选择多模态记忆整理动作，把质量、成本和延迟放在同一决策里。 |
| 16 | [Balancing Memory Pathways](16-hybrid-LM-memory-pathways.md) · [arXiv](https://arxiv.org/abs/2610.06750) | UNC / UT Austin / Mila / Yale · A | 诊断混合 LM 中 Attention 遮蔽循环状态，对 latent memory 机制最有启发。 |
| 17 | [MemTrace](17-MemTrace-coding-agent.md) · [arXiv](https://arxiv.org/abs/2610.04838) | SJTU / MemTensor / Theseus Lab · A | 将记忆绑定代码状态与版本，具体解决 Agent 旧记忆失效问题。 |
| 18 | [Collaborative Personalized Preference Alignment](18-collaborative-personalized-alignment.md) · [arXiv](https://arxiv.org/abs/2610.05898) | CityU HK / UW / HKUST · A | 解决少样本用户偏好对齐，冷启动与负迁移问题值得研究。 |
| 19 | [SpaC-MEM](19-spatial-conversational-memory.md) · [arXiv](https://arxiv.org/abs/2610.05526) | University of Toronto · A | 物体中心的空间—对话记忆，将个性化助理扩展到第一视角长期世界模型。 |
| 20 | [Off-Policy Merging](20-CMU-off-policy-merging.md) · [arXiv](https://arxiv.org/abs/2610.05872) | Carnegie Mellon · A | **弱相关但具启发性**：参数持续学习的抗遗忘思路，可迁移到个性化权重更新。 |

## 机构分布与主题趋势

- 机构优先级：领先公司/研究院参与 **14/20**，一流高校/实验室主导 **6/20**；没有用普通机构的弱证据论文凑满目标，也无机构未核验条目。多机构合作按是否有 S 机构参与归入一个层级，不按机构数重复计篇。
- 今日直接研究 Agent 的持久/程序性记忆、技能提炼与自我改进的工作密集出现；值得比较的是 **记什么**（轨迹、策略、因果改进、可验证事实）、**何时读写**（测试时与按需整理）、**怎样防污染**（记忆失配与状态过期）。
- Diffusion LLM 的自适应计算、蒸馏校正、推测解码形成另一条线；latent reasoning 与 hybrid recurrent memory 则提出“隐藏状态是否真的承载有用历史”这个机制问题。个性化方向有偏好模拟与少样本协作，但真实用户验证仍偏薄。

## 最值得深读的 3 篇

1. [PrisMem](02-PrisMem-capability-memory-evolution.md)：与 self-evolving agent memory 最直接，且提供明确的迭代训练和长记忆评测；重点核对收益是否来自能力进化而非更大检索预算。
2. [Bayesian Cheatsheet](03-IBM-Bayesian-Cheatsheet.md)：测试时把解题经验组织成策略簇，适合研究“经验记忆”能否在新题型上迁移；重点关注聚类稳定性与隐性数据泄漏。
3. [Anthropic 记忆风险研究](01-Anthropic-self-propagating-memory-risk.md)：从对抗/安全角度检验持久记忆的负面外部性；建立记忆系统时应先读其威胁模型，再看记忆审计与禁用为何不足。若聚焦多模态架构，下一篇建议读 [MemPilot](15-MemPilot-multimodal-memory.md)。

## 证据与边界

以上数字是论文作者在其指定模型、任务和预算下的报告，并非本人复现。每篇笔记的“未来影响”和 critical thinking 是独立推断；可信度分数只衡量现有论证和实验支持程度，不是机构声望分。候选范围限定为本次 cs.CL、cs.AI、cs.LG 新稿，无法声称覆盖 arXiv 所有学科交叉投稿。
