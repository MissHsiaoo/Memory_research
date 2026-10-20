# 17. ExpVoyager

- 论文：**ExpVoyager: Direct Experience Navigation for Dynamic Agent Skill Synthesis**
- arXiv：[2609.32630](https://arxiv.org/abs/2609.32630)；[官方 PDF](https://arxiv.org/pdf/2609.32630)
- 提交日期：2026-09-26；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Yonsei University
- 机构优先级：**B｜研究型大学，直接相关黑马**
- 研究标签：experience memory、skill synthesis、self-evolving agent、navigation
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

ExpVoyager 避免在未来任务未知时预先把经验压成固定 skill；它让 skill curator 针对当前任务在原始轨迹中多视图、多分辨率导航，动态合成所需程序知识。

## 2. 怎么做、实验如何设计

curator 维护 navigation state，持续记录已获得知识和剩余需求，再决定查看哪个来源、步骤或视图。实验考察随经验池扩张的持续收益、与已有 skill 的兼容、访问效率、来源/知识级保持，以及移除 navigable interface 或 navigation state 的消融。

## 3. 结论

任务时按需探索原始经验，比写入时一次性抽象更能保留未来才显现的重要条件与步骤顺序。

## 4. Future impact

可作为 agent skill memory 的“编译器”：原始经验是源代码，当前任务决定编译出的临时技能。

## 5. Critical thinking

该思想与 JIT memory 一致但更聚焦 procedural skill。代价是查询时多轮导航，且 curator 可能被无关轨迹拖累。需要在超大经验池、恶意轨迹、严格时延预算下与预编译技能库公平比较。

## 6. 可信度判断

**3.8/5。** 全文包含多项诊断和 failure case；机构优先级非顶层，且“动态合成”的在线成本与真实长期规模仍需验证。

