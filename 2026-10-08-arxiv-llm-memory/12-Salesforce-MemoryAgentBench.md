# 12｜Salesforce：MemoryAgentBench 的“选择性遗忘”分数可能在测什么

- 论文：[arXiv:2610.09193](https://arxiv.org/abs/2610.09193)｜[官方 PDF](https://arxiv.org/pdf/2610.09193)｜本地 `2610.09193.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-06 UTC，v1。作者/机构（PDF 首页）：Egor Pakhomov、Erik Nijkamp；Salesforce AI Research。机构优先级：A+；标签：memory evaluation、conflict resolution、benchmark audit；直接相关。

## 1. 做了什么

质疑 MemoryAgentBench 的 Conflict Resolution 子集是否真能被直接解释为“选择性遗忘能力”。作者实现一个不学习、只按“同一事实最新陈述覆盖旧陈述”的冻结解析器，逐题检查 benchmark gold 是否可由其自述规则推出。

## 2. 怎么做、实验如何设计

规则只在四张事实清单之一上定型，再在其余三张上评测；同时将题目分为 last-write graph 可解、需覆盖旧事实才可解及小量解析范围残差。PDF 还跑两个长上下文模型与预注册的近似 BM25 agent，每题只保留一次结果，比较各组表现；着重分析 262K 多跳问题中的不可达 gold，而不是用总分掩盖题目机制差异。

## 3. 结论

零学习规则在官方指标上答对 80.25%，三张 held-out 清单为 74.5%。另有 67 题的已发布 gold 不能从最后写入图得到，却能从已被覆盖的旧陈述得到；这类题在 262K 多跳题中占约三分之一。长上下文模型在规则可解题上表现很高，在这 67 题上骤降，说明子集混入不同性质的失败。

## 4. 未来影响（推断）

记忆 benchmark 应公开逐题“根据声明规则是否可达”的分层报告；新的 selective forgetting 方法不能只拿整体 Conflict Resolution 分数做能力宣称。

## 5. Critical thinking

冻结 last-write 解析器也可能遗漏自然语言中的作用域或例外，因此“不可达”取决于作者形式化规则是否忠实；论文承认还有 parser-scope residual。它的贡献不是新记忆方法，而是测量学纠偏。建议由独立标注者复核争议题、给每题提供可执行状态图，再重新比较现有 memory agent 排名是否稳定。

## 6. 可信度：4/5

依据：核查 PDF 的冻结协议、逐题分组和模型对照。优点是简单强基线与不可达案例有可审计解释；局限是仅针对一个 benchmark 子集，解析器假设与真实用户对冲突事实的意图未必一致。
