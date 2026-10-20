# 12｜Is Bash All You Need? An Empirical Study of Tool Interfaces for Enterprise Digital Worker Agents

- arXiv：[2609.11999v1](https://arxiv.org/abs/2609.11999v1) · [官方PDF](https://arxiv.org/pdf/2609.11999v1) · [本地PDF](../papers/12-Bash-Interfaces.pdf)
- 首次提交：2026-09-10（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Hazel Mak , Susheel Suresh , Sahil Bhatnagar , Barry Wang , Chhaya Methani , Alejandro Gutierrez Munoz
- 核验机构：Microsoft Corporation、Carnegie Mellon University；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业机构／顶级高校。研究标签：相邻启发｜tool memory / skill reuse / agent harness。
- 主观新颖性：3.5/5；证据可信度：4/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§3–6、表1、表4–6。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.11999-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

研究企业digital worker究竟需要复杂typed工具目录，还是一个shell就足够。最关联self-evolving memory的部分是“持久保存agent自己合成的工具”是否真能提高后续任务表现，而不是仅观察到了复用就宣称学习成功。

## 2. 怎么做，实验怎么做

五接口：typed-only、bash+typed、bash、bash+持久合成工具、限制在typed目录内的programmatic tool calling。用Opus-4.8和GPT-5.5在TheAgentCompany的174任务以及APEX-Agents的480任务比较；前者统一修复模拟同事可靠性问题，后者固定六月快照。报告任务评分、完整pass、token、推理成本、耗时与paired bootstrap。

合成工具的创建、当前调用、跨任务复用和调用成功分别统计；PTC可以在代码内压缩中间结果，但不能任意调用目录之外的动作。

## 3. Conclusion：原文结论及边界

Bash相对typed-only在TheAgentCompany得分提高21.8–24.5个百分点、APEX提高4.8–7.4点，token减少19–72%。添加持久合成工具没有可检测的 pooled 质量收益；GPT-5.5复用工具调用成功率还低于新鲜inline命令。PTC省token，但任务质量一般未达到bash。

## 4. Future impact：潜在影响

我的推断：技能记忆的研究应评估净收益，包含检索、适配、陈旧依赖及错误恢复，而非把“保存并复用了技能”作为成功指标。可将技能生命周期管理与RIPPLE的组合验证结合，拒绝长期价值为负的抽象。

## 5. Critical thinking：我的判断与可检验拓展

接口比较不只是调用语法：shell的表达范围、可用文档和模型预训练熟悉度都可能影响结果。持久合成库的负结果仅限本实现、任务顺序和两模型，不证明所有skill memory无效。还需检验安全隔离、工具权限、API版本漂移，以及预定义工具目录是否同等精心优化。

## 6. 可信度、优点与不足

可信度4/5；novelty3.5/5。优点是固定任务多接口、多模型、paired分析，揭示复用不等于增益。局限是环境快照和API模型随时间变，部分成本由当时价目估算，无法替代安全评估。建议复现同预算、跨任务随机顺序的技能启用/禁用实验，并报告负迁移比例；不据此自动放宽任何agent权限。

