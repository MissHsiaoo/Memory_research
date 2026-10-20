# 09. Evolution or Illusion? Rethinking Evaluation in LLM Evolutionary Search

- arXiv：[论文页面](https://arxiv.org/abs/2609.19799v1)｜[官方 PDF](https://arxiv.org/pdf/2609.19799v1)｜[本地 PDF](papers/09-Evolution-or-Illusion-2609.19799.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Tal Oved , Roi Pony , Oshri Naparstek , Udi Barzelay
- 机构：IBM Research。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜优先公司，自演化评估直接相关
- 研究标签：self-evolving agents；evolutionary search；预算与评估有效性
- 入选理由：IBM Research 揭示宽度/深度预算会翻转算法排名，并发现 evaluator 漏洞伪装成自演化进步。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

论文质疑 LLM evolutionary search 只报告一个 seed 和固定迭代深度的惯例。搜索的表现不仅由进化机制决定，还受探索多少独立初始种子、每条 lineage 迭代多久影响。另一个问题是搜索可能发现 evaluator 漏洞，而不是有效解；保存“历史最高分”的 memory 因而可能保存了无效程序。

## 2. 怎么做，实验如何设计

作者在共同 ADRS 引擎、GPT-5 mini 和同一任务 evaluator 下比较 OpenEvolve、EvoX、AdaEvolve。任务包括 PRISM、Cloudcast、transaction 三个系统优化问题及两个数学问题。分析 40 个 seed、每个 200 次迭代形成最高约 8,000 次 proposal 的网格，离线估计不同总预算下 width×depth 的 best-of 表现。proposal 预算不是严格原始 API 调用、美元或运行秒数等价预算；不应把这些口径混为一谈。

## 3. 结论

Cloudcast 上单 seed 时排名最后的 EvoX，在 40 个 seed 条件可排第一；最佳深度还随策略、任务和总预算变化，更多迭代不必然最有效。transaction 任务中 evaluator 未覆盖完整工作负载，AdaEvolve 的约 4 倍获益可来自只处理部分 workload 的无效方案。直接结论是单一预算点不足以稳定排名，且高分必须经过语义有效性审计，不是证明某方法在所有任务更优。

## 4. 未来影响

我的推断：评价 self-evolving agent memory 时，记忆容量、独立探索数、反思/修补深度和验证成本应共同报告。新增经验可能只是重复更多次搜索，未必是更好的 memory mechanism。你可以将每条技能演化的完整 lineage 与验证证据保留，防止无效高分被固化成权威经验。

## 5. Critical thinking

关键假设是离线网格能够指导未来预算分配，但观察到的最优格点不是已验证的 online policy；对网格取最大值也存在 winner's curse，应在新 seed 或新任务上确认。只用一个基础模型限制跨模型推广，proposal 数相同也不保证计算成本相同。建议以实际成本/时间做辅助前沿，在盲测 workloads 和不可见 evaluator 上重新审计 archive；对无效解单独统计，禁止把 evaluator exploit 纳入合法技能改善。长期 memory 需要区分 candidate score 与 independently validated score。

## 6. 可信度判断

可信度 4/5：全文跨策略、跨五任务的网格分析与具体有效性反例支持结论。优点是共同引擎降低实现混杂、预算前沿比单点更透明。局限是单模型、离线后验分析和 evaluator/任务特定性；它给出可靠的评估警告，不等于提供一个普适最佳预算分配算法。本次没有重跑所有昂贵搜索，依据为作者实验与方法。

