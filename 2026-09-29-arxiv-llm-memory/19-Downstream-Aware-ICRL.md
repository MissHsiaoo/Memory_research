# 19. Downstream-Aware Context Selection

- 论文：**Downstream-Aware Context Selection for Online In-Context Reinforcement Learning**
- arXiv：[2609.33166](https://arxiv.org/abs/2609.33166)；[官方 PDF](https://arxiv.org/pdf/2609.33166)
- 提交日期：2026-09-27；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：UIUC、University of Virginia
- 机构优先级：**A｜一流高校**
- 研究标签：in-context RL、context selection、online memory、token efficiency
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

论文在在线 ICRL 中预测“删掉某段历史会怎样影响下游决策”，以此持续构造有界上下文，而非按时间或相似度静态保留。

## 2. 怎么做、实验如何设计

decision-gap predictor 对历史移除后果排序，删除序又指导保留内容内部的冗余压缩，再用统一准则动态决定每一步预算。SUMO 闭环驾驶的分布内、未见域、未见路线中节省 23.2%–25.8% token 且性能相当；ScienceWorld 节省 52.1%，并优于 Recent/Similarity 的用量。论文报告 matched-budget prompt compression 和 bootstrap 区间。

## 3. 结论

上下文价值应由“对未来行为的边际影响”定义，而不是单独相关性；在线策略需要决策相关的动态记忆预算。

## 4. Future impact

可为长程 agent 提供 principled memory eviction，并把 token 成本直接纳入 continual adaptation。

## 5. Critical thinking

移除效应是接近因果的目标，但 predictor 训练可能昂贵且受参考 full history 的质量上限限制。还需测试互补片段的联合删除、错误奖励和长周期分布漂移，避免逐项估计忽略高阶相互作用。

## 6. 可信度判断

**4.1/5。** 两种差异很大的环境、成本匹配与统计区间增强可信度；离开放式工具 agent 和个性化对话仍有距离。

