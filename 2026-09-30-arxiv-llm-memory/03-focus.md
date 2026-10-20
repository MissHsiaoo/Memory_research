# 03 — FOCUS: Training-Free Decision-Preserving Context Compression for LLM Agents

- arXiv：[2609.37590](https://arxiv.org/abs/2609.37590)；[官方 PDF](https://arxiv.org/pdf/2609.37590)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Shantanu Dixit 等；M365 Research, Microsoft
- 机构优先级：**S**；研究标签：`context compression` `agent memory` `causal attribution`
- 证据范围：阅读全文；本地 PDF：[2609.37590.pdf](./2609.37590.pdf)

## 1. 做了什么

把 agent 历史压缩重述为“哪些过去 span 会因果性地改变未来决策”，目标不是删冗余文本，而是保留决策充分信息。

## 2. 怎么做、实验如何设计

FOCUS 在测试时用随机计划 rollout 近似 Information Bottleneck/依赖贡献，对 reasoning-action-observation span 排序、压缩并做防御性校验，无需离线数据或微调。OfficeBench、AppWorld、8-QA、WebVoyager 和多轮对话实验中，峰值上下文最多降 48%、依赖量降 73%，任务成功率最高反而升 8.9 个百分点。

## 3. Conclusion

训练免费、轨迹条件化的因果保留标准能比静态冗余压缩更适配 agent 的动态历史。

## 4. Future impact

可作为闭源模型外接 memory compactor，也为记忆删除、可解释保留和在线预算控制提供统一“是否改变决策”的度量。

## 5. Critical thinking

rollout 估计的是当前模型与当前计划分布下的影响，不是任务世界中的真实因果；模型若尚未意识到某条证据的重要性，会把它判断为可删。建议做未来分布漂移、延迟依赖、罕见安全约束和 adversarial distractor 测试，并报告压缩本身额外调用的端到端金钱/延迟成本。

## 6. 可信度判断

**4.5/5。** 五类 agent 基准、消融和理论表述较完整，机构可信。局限是结果依赖基座模型生成的反事实计划，最长真实运行周期和不可逆误删风险还不充分。
