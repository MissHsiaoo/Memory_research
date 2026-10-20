# 02. VALVE

- 论文：**Certified Long-Horizon Code Agent Evolution via Validation-Gated Skill Optimization**
- arXiv：[2609.32990](https://arxiv.org/abs/2609.32990)；[官方 PDF](https://arxiv.org/pdf/2609.32990)
- 提交日期：2026-09-26；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Microsoft、Purdue、University of Washington、UC Davis、NYU、University of Cambridge
- 机构优先级：**S｜指定重点工业机构 + 顶级高校**
- 研究标签：self-evolving agent、skill memory、validation gate、code agent
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

VALVE 让代码 agent 从长期任务中积累技能，但只有经过验证的更新才能进入持久 skill bank，目标是避免“学会新技巧的同时把旧能力改坏”。

## 2. 怎么做、实验如何设计

系统从轨迹中提出技能更新，在独立验证任务上比较更新前后表现，并用 validation gate 决定是否写入。作者在 1,000 余个软件工程任务上评测，平均最终/峰值表现分别提升 14.9/16.5 点，验证门将性能回撤降低约 75%，技能库比直接累积经验紧凑约 11 倍。

## 3. 结论

持久 agent memory 不应是无条件追加日志，而应像软件变更一样经过回归验证；“能否安全继承”比单次成功更关键。

## 4. Future impact

该思路可迁移到企业 agent 的长期 SOP、工具技能与个性化偏好更新，形成带 provenance、回归集和回滚语义的记忆治理层。

## 5. Critical thinking

优点是正面处理 self-evolution 的灾难性回撤，并给出大规模代码任务证据。关键假设是验证集能代表未来分布；若更新只对稀有边缘场景有用，门控可能误拒绝。还应比较按技能粒度、按用户粒度和按环境粒度的验证，并报告长期多次更新后的选择偏差。

## 6. 可信度判断

**4.5/5。** 样本规模大、指标和安全目标清楚，机构与实验可信。局限是代码环境有强自动验证信号，迁移到开放式对话或弱反馈记忆仍未证明。

