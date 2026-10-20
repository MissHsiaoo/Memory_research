# 2026-09-11 arXiv 论文精选：补发 20 篇

**公告批次：9 月 11 日；实际补发：9 月 12 日。** 已保存 20 份官方 PDF、20 篇中文批判性笔记。本报告补齐 9 月 11 日未完成的筛选，不把这些论文计为 9 月 12 日新论文。

## 范围、日期与机构规则

原定任务在 9 月 11 日早晨只查到旧批次后停止，未继续完成筛选，这是流程遗漏，不是当天没有好论文。原检查记录保留在上一级目录，本补发版是该日正式阅读名单。

本次以官方列表/RSS 标注的 **Friday, 11 September 2026** 批次为准，采用 9 月 12 日已保存的原始快照，并在线复核列表。三个分类 cs.CL / cs.AI / cs.LG 中的 new/cross 条目合并去重得到 **382 条候选**；其中跨分类条目包含旧论文，不能把 382 当作当天首次发表论文数。对候选标题/摘要进行初筛，对重点候选核查原文，正式选出 20 篇。不是对所有 arXiv 学科或全部候选的穷尽式全文评审。

入选论文均为 v1，首次提交时间落在 9 月 9 日 18:00 UTC 后至 9 月 10 日 18:00 UTC 前，并出现在目标批次；这与当时的提交截止和发布流程相符。**提交窗口只用于交叉核验，不代替官方公告归属。** 两篇仅在本次抓取分类里以 cross 出现的 KuaiRP、RetroThinker，同样为该窗口新提交的 v1，不是拿早先已发表的旧文补数。重复版本、明显旧文 cross-list 及此前已推荐的旧批次论文未入选。

9 月美国东部时间 20:00 的公告对应次日北京时间 08:00；因此提交日期常比列表日期早一到两天。批次日期、RSS 构建时间、API published 字段分开记录。[官方公告规则](https://info.arxiv.org/help/availability.html)

筛选按你的偏好：**先确认强机构，再在主榜内综合相关性、novelty、方法与启发排序**。本期没有用其他机构论文填满方向配额。弱相关但值得借鉴的工作均明确标注；机构声誉与证据可信度分开，不把作者使用 OpenAI / Anthropic 模型当成这两家公司的署名成果。

## 主榜 20 篇

分数依次为主观 novelty / 证据可信度，均为 1–5 分，不是概率。标题链接进入中文笔记，PDF 链接打开原文。

| 排名 | 论文 | 主要核验机构 | 与研究兴趣的关系 | N / C |
|---|---|---|---|---|
| 1 | [Auto-RecSys](notes/01-Auto-RecSys.md) · [PDF](papers/01-Auto-RecSys.pdf) | Meta、UIUC | 直接相关｜persistent memory / self-evolving agent | 4 / 3 |
| 2 | [NCP-ArchPreview](notes/02-NCP-ArchPreview.md) · [PDF](papers/02-NCP-ArchPreview.pdf) | 上海 AI Lab、上海交大 | 直接相关｜latent representations / 参数化适应 | 4.5 / 4 |
| 3 | [FlexComp](notes/03-FlexComp.md) · [PDF](papers/03-FlexComp.pdf) | 东京大学、NII | 直接相关｜soft memory / 自适应压缩预算 | 4 / 4 |
| 4 | [Story-Imprinting](notes/04-Story-Imprinting.md) · [PDF](papers/04-Story-Imprinting.pdf) | TruthfulAI、Harvard、METR、Oxford | 直接相关｜persona / 隐式偏好学习 / 个性化风险 | 4.5 / 4 |
| 5 | [T1](notes/05-T1.md) · [PDF](papers/05-T1.pdf) | Tencent Hy、NUS 等 | 相邻启发｜长任务 agent / 训练部署一致性 | 4 / 3.5 |
| 6 | [KuaiRP](notes/06-KuaiRP.md) · [PDF](papers/06-KuaiRP.pdf) | Kuaishou GameMind | 直接相关｜persona consistency / 参数记忆与遗忘 | 3.5 / 3.5 |
| 7 | [KV-Persona](notes/07-KV-Persona.md) · [PDF](papers/07-KV-Persona.pdf) | LinkedIn（作者邮箱） | 直接相关｜KV latent memory / persona control | 4 / 2.5 |
| 8 | [REVA](notes/08-REVA.md) · [PDF](papers/08-REVA.pdf) | UIUC、VinUniversity | 直接相关｜历史经验复用 / RAG 压缩记忆 | 4 / 3.5 |
| 9 | [SWRouter](notes/09-SWRouter.md) · [PDF](papers/09-SWRouter.pdf) | 百度、上海交大等 | 直接相关｜多轮上下文选择 / memory routing | 3.5 / 3 |
| 10 | [Looped-Flows](notes/10-Looped-Flows.md) · [PDF](papers/10-Looped-Flows.pdf) | EPFL、KAIST、CMU、Oxford 等 | 相邻强启发｜潜在循环推理 / diffusion-style training | 4.5 / 4 |
| 11 | [Negative-Self-Distillation](notes/11-Negative-Self-Distillation.md) · [PDF](papers/11-Negative-Self-Distillation.pdf) | UVA、Stanford | 相邻启发｜self-improvement / 失败经验学习 | 4 / 3.5 |
| 12 | [MoE-Data-Repetition](notes/12-MoE-Data-Repetition.md) · [PDF](papers/12-MoE-Data-Repetition.pdf) | Stanford、UW Allen School | 相邻启发｜continual training / 记忆过拟合 | 4 / 4 |
| 13 | [SearchAtlas](notes/13-SearchAtlas.md) · [PDF](papers/13-SearchAtlas.pdf) | Duke、UPenn | 直接相关｜agent 证据记忆 / 过程评估 | 4 / 3.5 |
| 14 | [Think-Before-You-Link](notes/14-Think-Before-You-Link.md) · [PDF](papers/14-Think-Before-You-Link.pdf) | CMU | 相邻启发｜长尾事实 / retrieval + reasoning | 3.5 / 3.5 |
| 15 | [LLM-Information-Geometry](notes/15-LLM-Information-Geometry.md) · [PDF](papers/15-LLM-Information-Geometry.pdf) | UCL、LCN | 相邻启发｜latent representation / 最小干扰编辑 | 4.5 / 3.5 |
| 16 | [RetroThinker](notes/16-RetroThinker.md) · [PDF](papers/16-RetroThinker.pdf) | FAIR/Meta、UT Austin | 弱相关但具启发性｜流式推理 / 在线纠错 | 4 / 3.5 |
| 17 | [Bellman-Plasticity](notes/17-Bellman-Plasticity.md) · [PDF](papers/17-Bellman-Plasticity.pdf) | Mila | 弱相关但具启发性｜continual learning / plasticity | 4 / 3 |
| 18 | [Qiushi-Engine](notes/18-Qiushi-Engine.md) · [PDF](papers/18-Qiushi-Engine.pdf) | 浙江大学 | 相邻启发｜research self-improvement / 保留与泛化 | 3.5 / 3.5 |
| 19 | [LOO-ROLL](notes/19-LOO-ROLL.md) · [PDF](papers/19-LOO-ROLL.pdf) | Purdue | 弱相关但具启发性｜低秩进化优化 / 参数更新 | 4 / 3.5 |
| 20 | [LOCUS](notes/20-LOCUS.md) · [PDF](papers/20-LOCUS.pdf) | UW Tacoma（官网核验） | 弱相关但具启发性｜低秩个性化 / 输出成本 | 3.5 / 3 |

## 建议先读这 3 篇

1. **[NCP-ArchPreview](notes/02-NCP-ArchPreview.md)**：最适合 latent memory / personalization 的架构探索。值得研究可更新的概念词表能否成为隔离用户记忆的接口；但论文尚未验证长上下文，不能把潜在接口当已实现的长期记忆。
2. **[Auto-RecSys](notes/01-Auto-RecSys.md)**：最贴近 self-evolving agent memory。跨会话状态、失败 playbook、想法历史是可直接借鉴的系统结构；31 次迭代的观察证据需要更严密对照来证明记忆的独立贡献。
3. **[FlexComp](notes/03-FlexComp.md)**：很适合做预算可控的实验。一个压缩模型支持多个 K，为 query-conditioned memory budget 提供直接起点，同时揭示“保留更多”并非总更好。

如果重心在 personalized memory 的可靠性，可把 Story Imprinting 与 KV-Persona 联读：前者研究隐式偏好/行为的迁移，后者展示表示相似度和实际 persona 表达的分离。

## 机构核验和主题分布

产业团队包括 Meta、Tencent Hy、Kuaishou、LinkedIn、Baidu；研究机构和高校包括上海 AI Lab、Harvard、Oxford、Stanford、UW、东京大学、NII、UIUC、CMU、Duke、UPenn、UCL、Mila、EPFL、KAIST、浙江大学、Purdue 等。多机构合作不重复计算成多篇论文。

几个容易误标的地方已处理：

- Story Imprinting 是 TruthfulAI / Harvard / METR / Oxford 署名，使用 GPT-4.1 微调不代表 OpenAI 论文。
- RetroThinker 首页有 FAIR, Meta Superintelligence Labs，但原文同时注明数据访问和实验由 UT Austin 开展。
- KV-Persona 的 LinkedIn 归属由首页作者邮箱支持，未写成 Microsoft Research。
- Bellman-Plasticity 按首页标为 Mila，未根据作者其他职位扩展成 DeepMind。
- LOCUS 的 UW 邮箱通过[官方目录](https://directory.tacoma.uw.edu/employee/dzhao)核对为 UW Tacoma 主聘，未混同为 Seattle Allen School 主聘。

按主要用途划分：潜在表示/记忆/循环推理 4 篇（NCP、FlexComp、Looped Flows、Information Geometry）；persona/个性化行为 3 篇；agent 经验与检索系统 6 篇；持续适应/自改进/优化 6 篇；语音流式纠错启发 1 篇。标签交叉，分组只用于阅读导航。

**本期没有硬凑“直接 diffusion LLM”配额。** Looped Flows 是去噪/概率流与小型循环推理的相邻成果，不是自然语言生成 diffusion LLM，笔记已明确限定。

## 不能只看 headline 的 6 个点

- **NCP**：预训练宏均值 +2.45，mid-training 后 +0.59；51.3% training tokens 达到同 loss，不等于计算成本减半。
- **Auto-RecSys**：31 次迭代来自一个模型，最后阶段只 6 次；“操作修复减少”不等于全部研发错误减少。
- **T1**：RL 从 SFT 的 49.4% 到 64.0%，同时平均轮数 31.5→94.4；需要预算匹配才能判断记忆或推理效率。
- **Looped Flows**：ARC 是 pass@2，不可宣传为单样本准确率；主要是 5–7M 参数结构化谜题模型。
- **KV-Persona**：主实验一个模型、一个 persona 对、一个话题、50 tokens，长期个性化外推非常有限。
- **LOCUS**：保持的是内部 preference diagnostic，约 48% 的诊断分数不等于回答质量无损；最大 39.84% 长度降幅来自 SamPO 的 256 例设置。

## 三条可检验的研究拓展

以下是我的研究假设，尚未证明其新颖性，也不是原论文已经完成的实验。

### A. 将容量与写入位置联合学习

NCP 提供可改的概念表，FlexComp 提供可变 K。可以对每条用户记忆同时决定“用多少状态、写入哪个概念/槽位”。固定总 state bytes 与训练 FLOPs，对比固定预算、query-agnostic、query-aware 和 uncertainty-aware 策略；重点测罕见事实、后续未知问题、偏好变更和用户之间的串扰，而不是只测平均 QA F1。

### B. 把经验记忆从成功摘要改为带条件的可验证规则

Auto-RecSys 的 playbook 与 SearchAtlas 的证据依赖图可以组合：每条经验保存适用环境版本、失败条件、证据来源和验证结果。按任务家族隔离训练/验证/测试，再注入环境变化；比较文本摘要、无条件规则、带条件且可撤回规则。指标包括负迁移、失败重复率、维护成本和节省的资源。

### C. 个性化记忆的“记住”与“采纳”分离

结合 Story Imprinting、KV-Persona 和 Information Geometry：同一条用户材料分别以引用、认可、否定方式写入。考察是否只提升事实问答，还是改变 assistant 自己的偏好/行为；记录输出效用、reference-prompt KL、多轮漂移、删除后残留。短程局部 KL 约束只是候选机制，不能替代长期行为测试。

## 文件与证据

- `papers/`：20 份正式入选 PDF。
- `notes/`：20 篇中文笔记，分别写清做了什么、方法和实验、结论、future impact、critical thinking、优缺点与可信度。
- [selection.json](selection.json)：结构化名单、作者、首次提交时间、排序与分析内容。
- [verification.json](verification.json)：每份 PDF 的有效页数、字节数和 SHA-256。
- [candidate catalog](sources/catalog.json)：382 条合并候选；候选不等于推荐，sources 中的其他 PDF 不属于正式 20 篇。
- 原始公告：[cs.CL RSS](sources/cs.CL-rss.xml)、[cs.AI RSS](sources/cs.AI-rss.xml)、[cs.LG RSS](sources/cs.LG-rss.xml)；[API 元数据](sources/selected-api.xml)。
- 现行官方入口：[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)，这些动态链接未来会更新，历史归属请以本地快照为准。

本次依照 PDF 阅读技能核查机构及相关原文方法/实验/局限，并对 NCP 首页进行视觉核验；没有复跑作者代码、重训模型或逐条验证所有长篇证明。论文内部日期可能不同于提交/公告日期，笔记以三者分开呈现。原始 9 月 11 日“待发布”记录保留，不再代表该日最终结果。

