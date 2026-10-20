# 06 — MILO: Automated Harness Discovery via Orchestrated Multi-Agent Evolution

- arXiv：[2609.38349](https://arxiv.org/abs/2609.38349)；[官方 PDF](https://arxiv.org/pdf/2609.38349)；[本地 PDF](./2609.38349.pdf)
- v1 提交：2026-09-29；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Prithwish Jana 等；Georgia Institute of Technology、AWS AI Labs、Carnegie Mellon University、Washington University in St. Louis
- 机构优先级：**S，AWS AI Labs 与一流高校**；研究标签：`self-evolving agent` `harness memory` `search`
- 证据：已核读 PDF 方法、实验与局限；数值为作者报告。

## 1. 做了什么

把 agent harness 的设计交给多 agent 演化搜索；不仅保留成功版本，也把失败改动留作负面经验，减少重复试错。

## 2. 怎么做、实验如何设计

多岛屿维护 harness 谱系与候选策略；变异 agent 生成改动，编排器负责嫁接、物种分化、资源重分配和课程安排。以 Terminal-Bench 2.1、PaperBench、DeepSWE 对比八种 harness 与六种搜索方法。论文报告使用 Claude Opus 4.8 时，相对初始配置三任务提升约 12、28.3、10.3 个百分点；Terminal-Bench 得分 86.1±2.0%，token 使用下降约 26%。

## 3. Conclusion

Harness 可以视作可演化的程序；完整的候选谱系与失败记录是一种比“只记最佳 prompt”更有用的搜索记忆。

## 4. Future impact

可迁移到自动发现 agent 的记忆写入、检索与压缩策略，让系统持续积累“哪些架构改动无效”的反例。

## 5. Critical thinking

**推断：** 岛屿搜索的收益可能部分来自更大的总试验预算和多次调参。应公开所有候选评估成本、失败谱系，并在严格等预算、全新任务与不同底模下复测；公开排行榜与论文测试集之间也需隔离。

## 6. 可信度判断

**4/5。** 多基准、多搜索对照和方差报告是优点。局限是计算预算与评估选择对最终胜率影响很大，长期在线演化的稳定性未充分证明。
