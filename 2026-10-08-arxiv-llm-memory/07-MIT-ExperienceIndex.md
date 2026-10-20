# 07｜MIT：ExperienceIndex，把关于文档的经验变成长期记忆

- 论文：[arXiv:2610.10091](https://arxiv.org/abs/2610.10091)｜[官方 PDF](https://arxiv.org/pdf/2610.10091)｜本地 `2610.10091.pdf`
- 正式公告：2026-10-08（cs.CL New submissions）；首次提交：2026-10-07 UTC，v1。作者/机构（PDF 首页）：Peter Baile Chen、Geoffrey X. Yu、Xinming Liu、Samuel Madden、Dan Roth、Jacob Andreas、Doug Downey、Michael Cafarella；MIT、McKinsey & Company、Oracle AI/UPenn、AI2。机构优先级：S；标签：artifact-grounded memory、agent memory、retrieval；直接相关。

## 1. 做了什么

现有 agent memory 多记用户事实或抽象技能；ExperienceIndex 记住“某份文档以前如何帮助解决问题”和“两份文档之间已发现的结构关系”。面对共享的案例、论文或代码库，agent 不必对每个新问题从头搜索完整证据集。

## 2. 怎么做、实验如何设计

从既有推理轨迹提炼单 artifact 经验和 artifact-pair 经验，以轻量中间层检索并引导新任务搜齐相关资料。PDF 的主实验跨 LoCoMo、SWE-bench Verified、ScholarQA、Freshstack、MuSiQue、Spider、MMQA 等不同载体与搜索框架，比较答案质量、在线费用与索引成本；另测 text-to-SQL→factoid QA 的跨任务迁移和强模型经验教弱模型。其表格显示在某设置下弱模型加入强模型经验后达到相近成绩。

## 3. 结论

论文报告答案质量最高提升 11.0 点、在线美元成本最高减少 50.5%；经验能够在同一 artifact corpus 上跨任务复用。注意这是各场景的上限结果，建立索引也有成本，低复用频率时不一定划算。

## 4. 未来影响（推断）

科研 agent 可以把“论文 A 支持什么结论、论文 B 与 A 的关系是什么”作为可检索经验层，而不仅保存会话摘要；这有助于多轮文献推理和跨用户共享的知识工作。

## 5. Critical thinking

artifact 关系可能随文档版本与证据修订失效，旧经验也可能把搜索束缚在已知材料里，漏掉新证据。与传统 RAG 的差别是复用过去解决问题时获得的 artifact-specific 结构。建议按文档更新率和问题复用率绘制总成本曲线，并在“旧论文被推翻”场景测记忆撤销、来源追踪和新证据发现率。

## 6. 可信度：4/5

依据：已核查 PDF 的双层经验表示、七类任务表格及成本/迁移实验。优点是跨载体、跨搜索框架，并计入经济性；局限是索引构建、资料更新和未来分布变化的全生命周期成本尚不充分。
