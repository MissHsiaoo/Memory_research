# 17｜MemTrace：让编程 Agent 记忆与代码库当前状态一致

- 论文：[arXiv:2610.04838](https://arxiv.org/abs/2610.04838)｜[官方 PDF](https://arxiv.org/pdf/2610.04838)｜本地 `2610.04838.pdf`
- 正式公告：2026-10-06；首次提交：2026-10-04。
- 作者/机构（PDF 首页）：Hongming Xu 等；Shanghai Jiao Tong University、MemTensor（上海）、Theseus Lab。机构优先级：A（强校参与）；标签：agent memory、coding agent、state consistency；直接相关。

## 1. 做了什么

解决长程编程 Agent 把过时信息当成当前事实的问题，使跨步骤记忆可追溯到代码实体并校验是否仍有效。

## 2. 怎么做、实验如何设计

MemTrace 将不可变的 Memory Trace 锚定到文件、符号、测试等实体，以依赖图连接，并在使用前对照当前仓库状态检验旧证据。PDF 在 DeepSWE（113 题）、SWE-EVO（46 题）、SWE-Milestone（98 题）和两种 harness 中比较；作者报告 DeepSWE pass@1 提升 21.2 个百分点。

## 3. 结论

在论文所测软件任务，记忆内容的状态一致性与结构化来源可提升长程 Agent 表现；具体收益会受仓库和测试分布影响。

## 4. 未来影响（推断）

个人与企业 Agent 记忆应为事实保存来源、版本和失效条件；“可验证的旧记忆”可能比单纯更长的摘要更重要。

## 5. Critical thinking

文件/符号锚点比较明确，人的偏好和隐含目标却难以如此校验。应测试大规模重构、动态生成代码和错误测试用例；报告验证开销、误失效与漏失效比例。

## 6. 可信度：4/5

依据：已读 PDF 的记忆结构、验证流程和三基准。优点是把记忆失效显式纳入设计；局限是主要证据来自编程场景。
