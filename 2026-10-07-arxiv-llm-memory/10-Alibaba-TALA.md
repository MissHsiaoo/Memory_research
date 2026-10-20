# 10｜TALA：法律长程推理中的测试时记忆进化

- 论文：[arXiv:2610.08138](https://arxiv.org/abs/2610.08138)｜[官方 PDF](https://arxiv.org/pdf/2610.08138)｜本地 `2610.08138.pdf`
- 正式公告：2026-10-07；首次提交：2026-10-06（UTC）。
- 作者/机构（PDF 首页）：Haotian Chen 等；Shandong University、Nanyang Technological University、Alibaba Group。机构优先级：S；标签：test-time agent evolution、memory consolidation；直接相关，但应用在法律域。

## 1. 做了什么

不更新模型权重，让法律 Agent 在接连案件和多角色协作中积累、改造、巩固可复用经验。

## 2. 怎么做、实验如何设计

TALA 的 Test-Time Memory Evolution 检索以往案件经验，按当前事实和程序重组，再巩固新经验；Rubric-Aligned Collaboration 检查各角色行动是否符合行为和程序要求。PDF 在 J1-EVAL、LegalWorld 与五个底座模型比较推理/Agent 基线，并分别消融两部分。

## 3. 结论

论文基准中，记忆进化和角色规则校验互补；但这不构成真实法律建议可用性的证明。

## 4. 未来影响（推断）

多 Agent 记忆不应只存单个角色经验，还应跟踪程序阶段、责任边界与跨角色冲突。

## 5. Critical thinking

旧案经验可能受司法辖区、政策时间和事实差异限制；错误迁移代价很高。建议加入日期/辖区失配、规则更新及人工专家盲评，并与只检索权威法源的强基线比较。

## 6. 可信度：3/5

依据：已读 PDF 双基准、五底座、组件消融。优点是考虑角色协作和经验适配；局限是领域基准无法替代法律专业验证。
