# 10. GRADUS: Discovering and Recovering Agent Lessons from the Environment's Latent Syllabus

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27781)；[官方 PDF](https://arxiv.org/pdf/2610.27781)；[仓库 PDF](pdfs/2610.27781.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Qing Ping , Wei Yang , Panpan Xu , Johannes Kirmayr , Lukas Stappen , Junjie Tang , Jun Huan
- 机构（PDF 首页署名核验）：AWS AI；University of Southern California；BMW Group Research and Technology
- 机构优先级：P1A；主题相关性：弱相关但具启发性；研究标签：self-evolving curriculum；experience reuse；tool agent
- 阅读证据：正文§2–3、表1–3（PDF第4–9页）；首页。已获取完整 PDF（24页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

把工具环境整理为有前置约束和结果的操作集合，通过覆盖缺口生成课程，并修复困难任务而不是一失败就丢掉。

## 2. 怎么做、实验如何设计

【论文直接证据】任务提案和解答搜索相互反馈，执行回放与策略检查作为验收；全局ledger记录覆盖。Opus4.5或Qwen3-235B提案，Qwen3学生SFT后GRPO；τ2-Bench与CAR-Bench，测试题及参考解不进入课程构造或选checkpoint，5次独立测试。

## 3. 结论

【论文直接证据】同提案器、8B学生和数据预算下，六分区平均成功率GRADUS76%，轨迹优先合成59%、图合成51%、模型先验45%。30B加RL六分区均值86%。开放提案器效果较弱但仍有效。

## 4. 未来影响

【阅读者推断，尚待验证】对经验记忆而言，重要的不只是保存成功经验，也包括跟踪未覆盖技能和修复难例；可用于记忆采样课程。

## 5. Critical thinking

【阅读者评析与后续建议】强提案器、并行搜索、反思与RL是多项投入，不能将全部增益归因于ledger。应匹配总合成/执行FLOPs，进行跨环境迁移。人工审查生成考试题仍发现不完全正确的样本，说明执行一致并非完整语义正确保证。

## 6. 可信度判断

**4/5**（与机构优先级独立）。预算匹配合成对照、组件消融、重复测试与人工审计较扎实；与显式记忆方法的关系主要为研究者推断。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
