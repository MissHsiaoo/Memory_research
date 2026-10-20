# 17. Evolutionary Safety of Recursive Self-Improving AI

- arXiv：[2609.31186](https://arxiv.org/abs/2609.31186)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.AI new）
- 作者/机构（PDF 首页核验）：Chang Gong 等；Institute of Computing Technology, Chinese Academy of Sciences
- 机构优先级：**A｜一流国家级研究机构**
- 研究标签：self-evolving agent、recursive self-improvement、memory safety
- 本地 PDF：[2609.31186.pdf](./2609.31186.pdf)

## 1. 做了什么

提出“Evolutionary Safety”视角：评估对象不再是某个静态模型是否安全，而是安全性质如何随持久记忆、模型更新、评估器、环境反馈和后继系统持续变化、累积和传播。

## 2. 怎么做、实验如何设计

这是一篇分类学与议程论文，没有给出主实验。作者系统枚举 intent drift、error accumulation、experience contamination、safety erosion、evaluator drift 与 risk inheritance，并把风险定位到 persistent agent state、model state、反馈/评估、计算底座和 meta-update mechanism；随后提出以 state、update、trajectory、lineage 为单位的评测，以及 modification、selection、authorization、provenance、recovery 五类治理原则。

## 3. Conclusion

静态 benchmark 无法覆盖递归自改进风险；必须追踪更新谱系、权限边界和恢复能力，尤其要防止被污染经验进入持久记忆后影响后继版本。

## 4. Future impact

可直接转化为 self-evolving memory checklist：每次写入保留来源、影响范围、验证器版本与回滚点；评估器本身也要版本化，避免 agent 与 judge 共同漂移。

## 5. Critical thinking

概念框架覆盖面广，但分类是否完备、类别是否可操作尚未经实证检验；“lineage”指标如何量化仍模糊。建议用现有 SkillEvo/AutoResearch 系统构造污染传播基准，并比较无版本控制、仅 checkpoint、带因果 provenance 三种治理。

## 6. 可信度判断

**3/5。** 已阅读全文。问题重要、结构清晰且机构可靠；但没有新的实验数据，可信度分只评价其论证与可用性，不能视为已验证的安全机制。
