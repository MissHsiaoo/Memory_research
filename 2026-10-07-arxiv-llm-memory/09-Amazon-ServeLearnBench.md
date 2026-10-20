# 09｜ServeLearnBench：Agent 能否从服务经验可靠地进化？

- 论文：[arXiv:2610.07792](https://arxiv.org/abs/2610.07792)｜[官方 PDF](https://arxiv.org/pdf/2610.07792)｜本地 `2610.07792.pdf`
- 正式公告：2026-10-07；首次提交：2026-10-06（UTC）。
- 作者/机构（PDF 首页）：Haizhong Zheng 等；Carnegie Mellon University、Amazon。机构优先级：S；标签：self-evolving agent、continual learning、agent memory benchmark；直接相关。

## 1. 做了什么

构造隐藏环境规则会随服务过程变化的流式基准，测试 Agent 能否从交互及结果反馈推断、应用、修正知识。

## 2. 怎么做、实验如何设计

论文定义 evolving-environment streaming dataset（EESD），ServeLearnBench 覆盖零售支持、银行和销售话术：53 个环境窗口、7,718 个任务。PDF 对比 RAG、Mem0、SkillOpt、Continual Harness、Prime 五种学习 harness，跨六种模型形成 28 个模型-harness 配对与 252 次学习运行，同时计入 token/任务成本和隐藏规则下的奖励。

## 3. 结论

作者发现“会完成任务”与“能从服务经验持续学会新规则”之间仍有显著落差；适应会耗费大量资源，还可能损坏本来正确的行为，探索不足是瓶颈之一。

## 4. 未来影响（推断）

自进化记忆系统应在不断变化的规则下测增量收益、退化率和总成本，而不只在静态任务上汇报一次性成功率。

## 5. Critical thinking

隐藏规则变化虽可控，但真实企业政策常有模糊性与人工例外。应报告政策变更检测延迟、旧知识撤回、灾难性错误和非平稳真实数据迁移；模型供应商升级也可能混淆 harness 效果。

## 6. 可信度：4/5

依据：已读 PDF 的数据构造、五种 harness、大规模配对和负面发现。优点是任务、模型、时间窗口都较丰富；局限是模拟环境与真实组织变化仍有落差。
