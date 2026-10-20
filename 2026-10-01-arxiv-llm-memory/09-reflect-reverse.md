# 09 — Does This Action Still Explain the Task? Reverse Scoring for Diffusion Language Model Agents

- arXiv：[2609.38536](https://arxiv.org/abs/2609.38536)；[官方 PDF](https://arxiv.org/pdf/2609.38536)；[本地 PDF](./2609.38536.pdf)
- v1 提交：2026-09-29；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Jiacheng Qiu 等；Huawei Noah's Ark Lab、TU Darmstadt、University College London
- 机构优先级：**S，头部企业研究团队与一流高校**；研究标签：`diffusion LLM` `agent recovery` `action selection`
- 证据：已核读 PDF 方法、实验与结论。

## 1. 做了什么

针对 diffusion LM agent 失败后仍高置信重复同一动作的循环，提出用“该动作能否反向解释任务”来选取恢复动作。

## 2. 怎么做、实验如何设计

先采样多个候选动作，再条件化状态与候选动作、重新遮蔽任务 token，计算反向去噪得分；这种 reverse conditional 抑制仅因常见或流畅而得高分的动作。ALFWorld、ScienceWorld、BabyAI、Jericho 上比较前向打分、重试策略与任务进展/成功率，论文报告反向打分更有效。

## 3. Conclusion

动作的前向生成概率不等于任务相关性；diffusion 模型的反向条件能力可以辅助避免错误重试。

## 4. Future impact

为 diffusion LLM agent 的失败恢复提供模型内评分路径，也能启发其他 agent 记忆系统用任务解释度过滤旧经验。

## 5. Critical thinking

**推断：** 反向分数可能偏爱复述任务线索而非真正改变环境状态。需报告候选数、额外模型评估次数、墙钟延迟，在任务文本含误导信息和工具反馈噪声时做消融。

## 6. 可信度判断

**3.5/5。** 四类环境与明确失败模式是优点；候选采样和额外打分成本可能影响实际收益，跨模型复现待验证。
