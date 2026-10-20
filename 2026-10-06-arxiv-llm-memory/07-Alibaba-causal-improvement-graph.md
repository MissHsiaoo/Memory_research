# 07｜Causal Improvement Graph：把 Agent 优化历史变成可追溯记忆

- 论文：[arXiv:2610.05039](https://arxiv.org/abs/2610.05039)｜[官方 PDF](https://arxiv.org/pdf/2610.05039)｜本地 `2610.05039.pdf`
- 正式公告：2026-10-06；首次提交：2026-10-04。
- 作者/机构（PDF 首页）：Junjie Zhang 等；Nanyang Technological University、Alibaba Tongyi Lab。机构优先级：S；标签：agent self-improvement、structured memory；直接相关。

## 1. 做了什么

提出持久的“因果改进图”记录 Agent harness 的调试与优化，避免多轮试验只留下模糊的自然语言总结。

## 2. 怎么做、实验如何设计

图中显式连接 Evidence、Hypothesis、Intervention、Outcome；优化器据此选择后续修改并检验结果。PDF 用固定底座模型和外部评估，与其他自动 harness 优化方法比较，并做图结构消融，区分记录试验结果与保留因果链的作用。

## 3. 结论

在论文所测的任务内搜索场景，结构化改进历史有助于更有效地迭代 harness；实验并未证明图记忆能自动跨任务迁移。

## 4. 未来影响（推断）

这类记忆可成为自进化 Agent 的“实验台账”：不仅记住改了什么，还记住为何改、何种证据支持及何时失效。

## 5. Critical thinking

图边的“因果”多来自有限试验，可能只是相关。下一步应以相同预算做跨任务、跨模型和反事实复测；若旧图指导新任务，应检查负迁移率。还要计入维护图的 token 与评估成本。

## 6. 可信度：3/5

依据：已读 PDF 的方法、比较与结构消融。优点是记录可追溯；局限是外部效度和真正因果识别证据不足。
