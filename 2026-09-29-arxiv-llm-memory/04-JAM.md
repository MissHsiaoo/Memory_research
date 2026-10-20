# 04. JAM

- 论文：**Just-In-Time Agent Memory with Runtime Agentic Research**
- arXiv：[2609.34385](https://arxiv.org/abs/2609.34385)；[官方 PDF](https://arxiv.org/pdf/2609.34385)
- 提交日期：2026-09-28；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Beijing Academy of Artificial Intelligence、Peking University、Hong Kong Polytechnic University
- 机构优先级：**A+｜一流研究机构/高校**
- 研究标签：just-in-time memory、agentic research、long-horizon agent、RL
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

JAM 将记忆从固定的“先整理、后检索”改为 query-conditioned runtime research：面对当前任务，agent 临时研究历史、组合证据并生成可执行记忆。

## 2. 怎么做、实验如何设计

作者构建 Memory-Gym，先用验证过的轨迹做监督微调，再以 hint-guided GRPO 强化运行时研究策略。评测覆盖长程 agent 任务，并与静态摘要、向量检索和已有记忆框架比较；论文报告运行时构造能在复杂查询下更稳定地找到跨事件依赖。

## 3. 结论

当未来问题未知时，写入时过早压缩会丢失信息；保留原始证据并在查询时进行有目标的“研究”，更适合开放世界长期记忆。

## 4. Future impact

它可能成为 personalized memory 的重要方向：同一历史可针对不同用户意图生成不同工作记忆，而不必永久固化单一画像。

## 5. Critical thinking

范式很强，但把整理成本推迟到每次查询，可能造成延迟和费用上升；训练 benchmark 的 hint 也可能使搜索策略过拟合。需要报告查询缓存、隐私泄露面、原始日志规模增长，以及在误导性历史中的证据校准。

## 6. 可信度判断

**4/5。** 方法和训练链路清晰，机构强且有专门 benchmark；因本次无法保存 PDF，结论依据官方全文 HTML，且部署成本与长期在线实验仍是主要不确定性。

