# 13. Q-Target Pretrained Transformers

- arXiv：[2609.30391](https://arxiv.org/abs/2609.30391)
- 提交日期：2026-09-24；正式公告批次：2026-09-28（cs.LG new）
- 作者/机构（PDF 首页核验）：Yichen Lin 等；上海交通大学、Alibaba Group、University at Buffalo
- 机构优先级：**A/S｜一流高校 + 重点工业机构；作者稿标注 NeurIPS 2026**
- 研究标签：in-context learning、in-context RL、offline learning
- 本地 PDF：[2609.30391.pdf](./2609.30391.pdf)

## 1. 做了什么

提出 QTPT，反对用行为克隆训练 in-context RL：弱离线轨迹中的 action 本身是有偏监督。它改用 Bellman 式 Q-target，让 Transformer 从上下文的状态、奖励和转移估计动作价值。

## 2. 怎么做、实验如何设计

理论部分在随机线性 bandit 和有限时域 MDP 中分析数据质量与覆盖；实证用随机/次优离线数据的受控 RL、D4RL Kitchen 与 AntMaze，并加入 backbone、meta-RL、task-coherent context 和 unsupported-action overestimation 诊断。核心比较保持 context-conditioned Transformer 相同，只替换 behavior prediction 与 Q-target 目标，以区分“更好架构”与“更好监督”。

## 3. Conclusion

Q-target 在弱数据上比监督模仿更稳，说明 ICL 的关键不只是从 demo 识别任务，还要从 reward/transition 推断 demo 哪些部分值得复用；离线覆盖不足仍会造成未支持动作的价值高估。

## 4. Future impact

对 agent memory 的启发是存储带 outcome 的经验并在读取时做价值评估，而非把历史行为当成正确范例。它可成为 self-evolving agent 选择“学哪次经验”的原则。

## 5. Critical thinking

理论模型和真实 LLM agent 之间距离仍大；Kitchen/AntMaze 的状态动作比语言工具调用更规整，Q-target 也可能放大 reward misspecification。建议在可验证 coding/tool agent 中比较 outcome-conditioned memory、BC memory 与 counterfactual return，并严格等数据等算力。

## 6. 可信度判断

**4/5。** 已阅读全文。理论+受控实验+失败诊断结构完整；向语言代理和自然语言 ICL 的外推尚属推断，复杂环境结果受覆盖和价值估计偏差限制。
