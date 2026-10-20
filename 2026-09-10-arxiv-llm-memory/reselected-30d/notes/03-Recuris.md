# 3. Recuris

Recursive Experiential-Working Memory Evolution for Long-Horizon Agent Harnesses

- 论文：[arXiv 2608.24876v1](https://arxiv.org/abs/2608.24876v1) · [本地 PDF](../papers/03-Recuris.pdf)
- 首次提交：2026-08-25（UTC）；arXiv 最新记录：2026-08-25。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Zhaochen Yu、Yingcheng Wu、Zhenfei Yin、Kaiyuan Chen、Zhe Zhao、Mengdi Wang、Shuicheng Yan、Ling Yang
- 已核验机构：NUS、Stanford、Oxford、Princeton（PDF 首页作者单位）
- 机构优先级：A｜顶尖高校合作。这是本次选刊层级，不是学校综合排名。
- 主题：self-evolving agent memory / working memory / skill memory
- 主观 novelty：4.5/5；证据可信度：3.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §2–3；附录 A、C（PDF 第 31–33 页）。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**把工作记忆驱动技能调用与可验证的局部技能更新放进同一个闭环。

## 1. 做了什么

Working Memory 记录当前进展和未解决目标，再选择 Experiential/Skill Memory；执行反馈更新状态，失败轨迹用于修改特定技能组件。

## 2. 怎么做的

固定 Meta-Agent 读取结构化失败轨迹，做组件级归因与局部补丁；候选更新经验证门控后生效。模型权重不变，Meta-Agent 本身也不随循环进化，因此是有界的记忆演化。

## 3. 实验如何设计，结果如何

覆盖 τ²-Retail（114 任务）、τ²-Airline（50 任务）、SkillFlow（166 任务/20 families），另有 Terminal-Bench 适应实验；常规每任务 4 次尝试。论文报告 37 个完成的模型/基准组合中 35 个改善。τ² 数据分 evolve/dev/test；但 SkillFlow 遵循顺序任务协议，没有独立 held-out task split，主要检验跨模型迁移。统计采用任务聚类 bootstrap。

## 4. Conclusion

当前证据支持可验证状态与技能协同能提升长任务执行。SkillFlow 分数不能与严格未见任务泛化结果混为一谈。

## 5. Future impact：对你的研究有什么启发

与 self-evolving memory 方向高度贴合：可把 memory 的“内容演化”和“调用条件演化”同时作为学习对象。

## 6. Critical thinking、优点、局限与置信度

优点：组件归因、验证门控、任务聚类统计较完整。局限：构建依赖强 Meta-Agent；不同基准的样本外定义不同，35/37 不能视为统一泛化证据。建议按任务家族隔离 evolve/dev/test，再比较只改内容、只改调用规则、联合修改，追踪跨任务负迁移和门控拒绝率。可信度 3.5/5：机制有力，但标题的 RSI 含义比实际实验宽。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

