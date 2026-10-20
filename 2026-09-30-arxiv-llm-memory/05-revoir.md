# 05 — Rational Clarification by Assistive Agents via Value-of-Information Reasoning

- arXiv：[2609.37588](https://arxiv.org/abs/2609.37588)；[官方 PDF](https://arxiv.org/pdf/2609.37588)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：T. Duy Nguyen-Hien 等；National University of Singapore、University of Oxford、A*STAR
- 机构优先级：**A+**；研究标签：`personalization` `clarification` `value of information`
- 证据范围：阅读全文；本地 PDF：[2609.37588.pdf](./2609.37588.pdf)

## 1. 做了什么

提出 REVOIR，用问题答案对下游任务收益的期望提升，而不是单纯的信息增益，决定个性化助理何时应追问、何时应直接行动。

## 2. 怎么做、实验如何设计

在推理时维护对用户意图/偏好的 belief，估计候选问题的一步 value of information，并计入提问成本和行动后纠正的可能性。CondAmbigQA 与偏好对齐家务规划 ADAPT 中，较微调 clarification policy 的偏好满足率提高 13–15 个百分点，问题数约为其五分之一，且无需训练。

## 3. Conclusion

个性化 agent 的澄清决策应优化最终行动效用，而非把“不确定性最低”当作代理目标。

## 4. Future impact

可与用户长期记忆联合：记忆不仅回答“用户喜欢什么”，还提供 belief prior 与提问价值，减少烦扰式个性化。

## 5. Critical thinking

一步 VoI 是可计算性的关键，也是主要局限；多步任务里早期低价值问题可能开启高价值信息路径。用户模拟器与真实人的耐心、反悔和策略性回答存在落差。优先后续实验应是真人 longitudinal study、模型误校准下的鲁棒性、以及问题—动作完全交错的 dual-control 场景。

## 6. 可信度判断

**4.5/5。** 决策理论动机强，和 prompting、CoT、微调及 information-gain 基线比较充分。现实可信度受模拟用户和短期任务限制，部署结论尚不能直接外推。
