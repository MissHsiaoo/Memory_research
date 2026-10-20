# Self-Organizing Agent Teams Learn to Reason Together

- arXiv：[22682](https://arxiv.org/abs/2609.22682)；[官方 PDF](https://arxiv.org/pdf/2609.22682)
- arXiv 初次提交：2026-09-19（v1）；正式公告归属：2026-09-22 新稿，二者不可混同。
- 作者：Aneesh Pappu , Mirac Suzgun , Yongchan Kwon , Federico Bianchi , Batu El , Mykel J. Kochenderfer , Hancheng Cao , James Zou（arXiv 官方列表）
- 机构：Stanford University；Together AI；Emory University（论文 PDF 首页核验）
- 机构优先级：A｜一流高校与产业合作
- 研究标签：self-evolving agent；团队策略记忆；多 agent；相关但非个人记忆
- 证据说明：以下数值均为论文自身报告；“我的推断/建议”并非论文实证。

## 1. 做了什么

论文让多 agent 团队从过去的协作轨迹中形成可复用的组织策略，而不是每次按固定角色模板推理。它把“记忆”扩展为团队层面的程序知识：谁应先解、何时互相挑战、如何综合答案。

## 2. 怎么做，实验怎么做的

作者训练或选择团队协作策略，并在 GPQA、MMLU-Pro、BBEH 上与单模型、线性化、MoA 等多种团队基线比较，检查异质成员贡献与选择能力。表 2 报告 SAT 平均 72.8、最佳单成员 65.9，但最强对照 Linearization 为 72.1，平均增益仅 0.7 点。分项 MMLU-Pro 82.4 低于 MoA 84.3，BBEH 56.0 低于 homogeneous team 58.7；候选覆盖率虽从路由 oracle 的 79.6 到 SAT 的 87.9，最终答案选择仍留有空隙。

## 3. Conclusion

可学习协作程序有潜力，但实证并非全面碾压简单团队，优势更可能来自增加候选覆盖而非总能选中好答案。仅靠平均成绩无法证明团队长期自组织会持续提升。

## 4. Future impact

如果把每类任务中的有效协作结构作为可版本化 agent skill 存储，可能减少无效讨论轮次；这里应同时记录何时不该启动多 agent，避免成本大于收益。此为我的外推。

## 5. Critical thinking

需要在相同 token/调用预算下比较，多 agent 的提升可能只是更多采样。候选覆盖与最终正确率之间的差距提示聚合器是瓶颈；建议独立优化答案选择，并在任务分布变化后测组织策略是否失效。还应测高度同质模型、错误互相强化、角色滥用以及共享历史导致的协同行为风险。

## 6. 可信度判断、优点与局限

3/5：有多基准和细分比较，优点是报告弱项；局限是最强基线差距小、成本及长期分布外证据不足。
