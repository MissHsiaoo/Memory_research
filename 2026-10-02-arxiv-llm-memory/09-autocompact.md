# 09 — AutoCompact: Learning When to Compact Context in Long-Horizon Coding Agents

- arXiv：[2610.02163](https://arxiv.org/abs/2610.02163)；[官方 PDF](https://arxiv.org/pdf/2610.02163)；[本地 PDF](./2610.02163.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Xuan Zhang 等；Singapore Management University、Nanyang Technological University、Harvard University
- 机构优先级：**A+，一流高校合作**；研究标签：`context compaction` `agent memory policy` `coding agent`
- 证据范围：核读 PDF 方法和实验；数值为作者报告。

## 1. 做了什么

让编码代理学习何时压缩上下文、压缩后保留什么状态，以及如何从压缩状态继续行动。

## 2. 怎么做、实验如何设计

先运行基础代理，对压缩决策、摘要及后续行动由 judge 复查；错误输出被纠正后才执行，以构造稳定训练轨迹。再用监督微调与任务成功奖励的 RL 联合优化编码/压缩。PDF 在 SWE-bench Verified、SWE-PolyBench Verified 比基础模型和不同推理预算；作者报告通过率分别绝对提升 9.2 与 5.0 个百分点，并测试不溢出的 256K 窗口和有溢出回退的 16K 窗口。

## 3. Conclusion

上下文压缩不该只在窗口溢出时触发；它是与任务行动共同优化的策略选择。

## 4. Future impact

可用于 agent memory 的自适应“何时归档/何时总结”，减少历史探索带来的上下文污染。

## 5. Critical thinking

**推断：** 改进可能部分来自 judge 纠错产生的高质量行动轨迹，而不全来自压缩策略。应消融只纠行动、不训练压缩，以及等训练 token/环境交互预算；还需评估跨代码库错误摘要积累。

## 6. 可信度判断

**4/5。** 两代码基准、不同窗口和预算实验支持实用价值；纠错数据构造与 RL 效果需进一步拆分。
