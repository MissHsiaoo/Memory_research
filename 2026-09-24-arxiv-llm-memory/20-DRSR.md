# 20. DRSR

- 论文：**DRSR: Learning Set-Level Deletion Risk for Efficient Long-Horizon Agents**
- arXiv：[2609.27276](https://arxiv.org/abs/2609.27276)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Mingxuan Wang 等；TierFlow Team、人民大学、清华大学
- 机构优先级：**A｜高校强；TierFlow 身份仅按 PDF 署名，不额外推断**
- 研究标签：agent memory pruning、set-level risk、counterfactual supervision、long horizon
- 本地 PDF：[2609.27276.pdf](./2609.27276.pdf)

## 1. 做了什么

指出逐块独立打分再删除多个 history block 会忽略交互项和小风险累积。DRSR 直接学习“删除集合”的联合风险，并在不确定时 abstain，以状态条件化方式选择可删历史集合。

## 2. 怎么做、实验如何设计

从外部轨迹构造当前 decision state 与候选删除集合，使用离线 counterfactual supervision 标注删除后行为风险；scorer 同时编码候选-状态关系、deleted/retained pooling 与 pair interaction，再按风险阈值在线剪枝。WorkBuddyBench Full260 上与无压缩和 Structural Pruning 比较：DRSR reward 0.802、每任务 2.126M token；Structural Pruning 为 0.701/2.292M。相对无压缩，论文总结 reward 从 0.699 到 0.802、token -20.82%；Eval40 达 0.794 reward、token -35.85%。

## 3. Conclusion

历史删除不是 singleton relevance 的简单加法；多块联合删除的交互和累计风险必须直接建模，abstention 对高风险领域尤其重要。

## 4. Future impact

为 memory pruning 引入风险控制视角：可把“最大压缩率”改为“给定失败容忍度下最大删除”，适合安全敏感 agent、企业工作流和超长运行任务。

## 5. Critical thinking

set-level risk 比逐块 importance 更贴近真实压缩，但训练标签来自离线 counterfactual，分布变化后阈值可能失准；组合空间巨大，候选生成策略决定了上限。Full260 reward 大幅超过无压缩还可能包含去噪效应，需要与同算力/同重试次数严格配对。建议做风险校准曲线、OOD 任务、极端组合、回滚机制，以及与 StateComp/PAMER 的统一比较。

## 6. 可信度判断

**4/5。** 已阅读全文；set interaction 分析、端到端结果和 ablation 支持主张。外部有效性、风险校准和同研究组共享管线是主要保留。
