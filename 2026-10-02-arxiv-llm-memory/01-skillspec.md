# 01 — SkillSpec: Consensus-Gated Agent Skill Evolution via Representation Specialization

- arXiv：[2610.00704](https://arxiv.org/abs/2610.00704)；[官方 PDF](https://arxiv.org/pdf/2610.00704)；[本地 PDF](./2610.00704.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-02（北京时间；属于当日 New submissions）
- 作者/机构（PDF 首页核验）：Huancheng Chen 等；Microsoft AI。首页未注明 Microsoft Research，不作此归属。
- 机构优先级：**S，头部模型机构**；研究标签：`agent skill memory` `self-evolving memory` `representation`
- 证据范围：核读官方 PDF 方法、实验；结果数字均为作者报告，未独立复现。

## 1. 做了什么

把“应保留哪条技能知识”和“该把技能组织成什么结构”拆开处理，避免自演化技能仅反复修改一份单体文本。

## 2. 怎么做、实验如何设计

SkillSpec 先由不同编辑意图生成候选技能，仅在配对重复评估达到整体收益、且各次评估的合计增益非负时提交；再根据整个优化轨迹（含被拒候选）的过程/冗余敏感性，在平面、图和混合表示中选择。PDF 在 SearchQA、SpreadsheetBench、OfficeQA、DocVQA、LiveMath、ALFWorld 六项基准，用 GPT-4.1、GPT-5.4 Nano、GPT-5.4 三种目标模型，与 SkillOpt 等比较；训练、验证和测试用途分开。作者报告平均成功率较 SkillOpt 提升 6.89%。

## 3. Conclusion

技能演化不仅是改写文本：执行证据决定是否接受更新，结构化表示决定知识如何被调用。

## 4. Future impact

可用于长期 agent memory 的“保留—组织”双阶段控制，尤其适合积累可复用工作流。

## 5. Critical thinking

**推断：** 严格共识门可能过于保守，拒绝在少数长尾任务有价值的技能。应公开优化过程全部评估预算，并检验分布漂移、技能相互依赖、少样本罕见任务及长期错误技能撤销。

## 6. 可信度判断

**4/5。** 六基准、三模型、配对评估和验证/测试隔离是优点；演化搜索成本与在线稳定性仍需外部复现。机构等级不影响此分数。
