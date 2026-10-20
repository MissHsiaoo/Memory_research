# 09. You Only Edit Once

- 论文：**You Only Edit Once: Incentivizing In-Context Capability of LLMs via Local Demonstration Refinement**
- arXiv：[2609.33609](https://arxiv.org/abs/2609.33609)；[官方 PDF](https://arxiv.org/pdf/2609.33609)
- 提交日期：2026-09-27；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Tsinghua University
- 机构优先级：**A+｜顶级高校**
- 研究标签：ICL、demonstration editing、RLVR、context optimization
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

论文把 combinatorial demo selection 简化为局部搜索：先取得一个初始示例集，再只做一次 Keep/Delete/Replace 编辑，然后让目标 LLM 推理。

## 2. 怎么做、实验如何设计

作者用可验证奖励训练小模型 Jev-LDE 执行单次编辑，避免反复调用昂贵目标模型做集合评分。实验覆盖标准分类 benchmark、不同目标 LLM、留出任务与模型迁移，并比较候选池、pre-selector、正确性反馈、时延和统计显著性。

## 3. 结论

ICL 上下文不必全局重搜；一个学习到的局部编辑器就能以较低推理成本修复初始检索集。

## 4. Future impact

可作为 memory retriever 后置校正层：先召回，再由轻量策略删除有害记忆或替换一个关键示例。

## 5. Critical thinking

“一次编辑”是很好的成本约束，但也限制复杂任务的修复半径；RLVR 依赖可判定奖励，开放式生成未必适用。应测试检索器严重失败时的上限、动态多步预算，以及编辑模型对目标模型更新后的鲁棒性。

## 6. 可信度判断

**4/5。** 全文包含细致消融和迁移评测，研究问题清楚。局限是主要证据来自标准 ICL 分类场景，对长程 agent memory 的效用仍属推断。

