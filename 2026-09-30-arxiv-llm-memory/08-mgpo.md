# 08 — Learning What to Remember: Long-horizon Counterfactual Memory Optimization

- arXiv：[2609.37930](https://arxiv.org/abs/2609.37930)；[官方 PDF](https://arxiv.org/pdf/2609.37930)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Jiaming Tang、Mingyan Liu、Armin Sarabi；University of Michigan
- 机构优先级：**A+**；研究标签：`memory optimization` `credit assignment` `counterfactual RL`
- 证据范围：阅读全文；本地 PDF：[2609.37930.pdf](./2609.37930.pdf)

## 1. 做了什么

提出 MGPO，给每次 memory rewrite 分配其对当前及未来任务的“边际增益”，剥离更新前记忆本已具备的效用。

## 2. 怎么做、实验如何设计

固定 reader，对同一后续 target 分别评估 rewrite 前后的 memory，差值形成 Memory Gain，并沿未来复用轨迹累积后用于 policy gradient。文档级信息抽取提供结构化监督与可测信用；优化后平均记忆长度相对初始 policy 减少近 80%，抽取提升，并跨 reader、领域和下游任务迁移。

## 3. Conclusion

长期记忆的训练信号应奖励“这次更新新增了什么未来价值”，而不是奖励更新后整体状态的表现。

## 4. Future impact

该 counterfactual credit 可推广到 agent 总结、技能库写入、个性化 profile 更新和 self-evolving memory，减少重复写入与短视奖励。

## 5. Critical thinking

反事实评估成本随剩余 horizon 增长，真实 agent 中无法穷举；冻结 reader 也可能使 writer 过拟合其盲点。最关键复现是等总调用预算与普通 RL 比较，并在非结构化、多目标、偏好随时间改变的交互环境验证近似信用是否仍可靠。

## 6. 可信度判断

**4.5/5。** 信用分配定义清楚，有理论分解、压缩率和多维迁移结果。局限是主任务为信息抽取，距离开放式长期对话与自主 agent 的动作后果仍有差距。
