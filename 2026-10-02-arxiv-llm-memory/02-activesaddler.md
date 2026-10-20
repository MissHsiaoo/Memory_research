# 02 — ActiveSaddler: Automated Curriculum Learning for Agent Harness Optimization

- arXiv：[2610.00906](https://arxiv.org/abs/2610.00906)；[官方 PDF](https://arxiv.org/pdf/2610.00906)；[本地 PDF](./2610.00906.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Sungho Park 等；POSTECH、KAIST、Microsoft
- 机构优先级：**S，Microsoft 与一流高校**；研究标签：`self-evolving agent` `failure memory` `curriculum`
- 证据范围：核读 PDF 方法和实验；数值为作者报告。

## 1. 做了什么

让 agent harness 与训练课程一起演化：下一轮该复查哪类失败，由不断更新的失败模式记忆决定。

## 2. 怎么做、实验如何设计

将重复失败抽象为可复用的 bandit 臂，估计针对每类失败继续优化的潜在进展，同时探索未见场景；新结果又更新失败模式与优先级。PDF 在 GAIA2 与 Terminal-Bench 2.0 上以相同 harness 优化器、预先固定课程为主对照，并做动态建靶、效用估计、探索/利用消融。作者报告测试 Pass@1 分别高 4.4 和 7.5 个百分点。

## 3. Conclusion

选择什么训练经验与如何修改 harness 一样重要；失效经验的分布随 harness 变化。

## 4. Future impact

未来 agent memory 可把“失败类别的边际改进价值”用于决定记忆写入和复习频率。

## 5. Critical thinking

**推断：** 失败模式聚类或评估器偏差会让课程对某些易得分任务过拟合。应比较相同总 rollout/模型调用成本，跨基准迁移失败模式，并检查长尾任务是否被 bandit 长期忽略。

## 6. 可信度判断

**4/5。** 固定课程强对照和模块消融支持主要机制；仅两类环境及优化预算敏感性限制泛化。
