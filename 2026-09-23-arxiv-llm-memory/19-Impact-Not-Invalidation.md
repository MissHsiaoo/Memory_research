# Impact Is Not Invalidation：记忆失效应针对 claim，而不是 diff

- arXiv：[2609.25130](https://arxiv.org/abs/2609.25130)；[官方 PDF](https://arxiv.org/pdf/2609.25130)
- v1 提交日期：2026-09-20；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Atul Anand；Thomson Reuters
- 机构优先级：B（黑马/启发性补充；agent memory 高度直接）
- 研究标签：memory staleness、claim invalidation、coding agent、execution-grounded benchmark

## 1. 做了什么

论文指出 coding agent 的记忆是否过期，不应问“这个 diff 是否改变行为”，而应问“这条具体 claim 在 diff 后是否仍成立”。它构建 execution-grounded claim invalidation benchmark 来验证问题表述的重要性。

## 2. 怎么做、实验如何设计

从 23 个 Python 库挖掘 10,369 条由 test function 表示的 claims，并通过同一 assertion 在前后 commit 的执行结果定义 184 个真实 flip。五个不同价格档模型比较 content anchoring、diff semantic-equivalence 与 claim-conditioned 判断；还加入 pytest-testmon、仅添加 claim 文本的控制、post-cutoff、shuffled diff、paraphrase 和 leave-one-repository-out。

## 3. 结论

diff 语义等价判断 precision 仅 0.291–0.329，而针对 claim 提问达到 0.705–0.974；仅把 claim 文本交给旧问题几乎无效，真正改变结果的是 predicate 本身。coverage selector 达到 0.868 recall 但 precision 仅 0.415。

## 4. Future impact

这应成为动态 agent memory 的基本原则：失效判断必须以 memory item 为条件，并维护“claim—来源—依赖—验证器”结构，而不是文件变更即全删。

## 5. Critical thinking

用 tests 作为 claim 非常干净但偏向可执行、可局部验证的代码知识；自然语言用户偏好与世界事实没有同等 oracle。184 positives 相对少，precision 置信区间和类别不平衡很关键。下一步应测 claim routing 后的总体存储成本、false deletion 的不可恢复损失及跨语言/大型 monorepo。

## 6. 可信度判断

- 评分：4/5
- 依据：明确执行 oracle、多个强控制、repository-held-out 与 post-cutoff 分割；结果差距大且问题构造透明。
- 优点：因果问题表述清晰；数据和控制扎实；直接解决记忆陈旧。
- 局限：正例少；仅 Python/testable claims；机构不在最高优先级名单。

