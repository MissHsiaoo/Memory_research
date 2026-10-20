# 07 — Hermes: Learning Contextual Reasoning Unlocks Test-Time Scaling

- arXiv：[2609.38332](https://arxiv.org/abs/2609.38332)；[官方 PDF](https://arxiv.org/pdf/2609.38332)；[本地 PDF](./2609.38332.pdf)
- v1 提交：2026-09-29；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Xinyu Li 等；AWS AI Labs、Carnegie Mellon University、Georgia Institute of Technology、Washington University in St. Louis
- 机构优先级：**S，AWS AI Labs 与一流高校**；研究标签：`context management` `test-time scaling` `agent harness`
- 证据：已核读 PDF 方法、实验与结论；以下为论文直接证据和单独标明的推断。

## 1. 做了什么

研究推理模型如何自己决定上下文分配与复用，而非由固定 harness 规则代管，使较小模型也能有效利用更长测试时计算。

## 2. 怎么做、实验如何设计

Hermes harness 提供委派、消化历史信息等上下文动作；Hermes-Learn 分阶段训练模型选择和使用这些动作。论文比较训练前后、不同推理预算与基线 harness，在数学推理及其他任务上测量结果与扩展曲线，报告缩小较小模型和较大模型的差距。这里不把摘要中的趋势当作所有领域的定量保证。

## 3. Conclusion

上下文管理既是系统设计问题，也是可学习的模型策略；合理训练后，增加测试时计算更可能转化为准确率。

## 4. Future impact

LLM memory 系统或可从固定摘要/检索规则转为模型主动控制的读写与上下文预算分配。

## 5. Critical thinking

**推断：** 更强的扩展曲线可能依赖训练过的工具协议与任务分布。应在未见过的工具、长时代理、记忆污染和相同总训练/推理成本下验证，并展示具体委派/消化失败案例。

## 6. 可信度判断

**3.5/5。** 方法与多预算对照支持机制方向；跨任务泛化、训练成本及长期记忆适用性仍需独立复现。
