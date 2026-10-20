# 08｜WinSyn: An Automated Pipeline for Realistic Enterprise Question-Answering Evaluation

- arXiv：[2609.12171v1](https://arxiv.org/abs/2609.12171v1) · [官方PDF](https://arxiv.org/pdf/2609.12171v1) · [本地PDF](../papers/08-WinSyn.pdf)
- 首次提交：2026-09-10（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Amey Varhade , Ananya Sutradhar , Ravishankar Krishnaswamy , Navin Goyal
- 核验机构：Microsoft Research India；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业实验室。研究标签：直接相关｜enterprise memory / temporal retrieval / benchmark。
- 主观新颖性：3.5/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§4–5、表1–4及生成流水线概述。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12171-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

WinSyn为企业问答自动生成跨数月、多员工、信息分散且变化的邮件环境。目标是让RAG和deep-research agent面对真实工作式的归属、状态、冲突与长答案，而非孤立短问答。主要贡献是可追踪的数据构造流水线，不是更强的记忆检索算法。

## 2. 怎么做，实验怎么做

以项目结构、epic、任务和每日活动日志为中间状态，再生成问题、gold答案与通信材料，配合反思修订和程序验证。四组模拟团队覆盖Cloud DevOps、Data Platform、Stripe、VS Code，其中两组种子来自真实公开技术文档，但生成邮件仍为合成。

每组127–181邮件、22–25员工、100–117天，共100问。用GPT-5.4驱动ReAct与改造Onyx，限定局部可见邮件及检索工具；同一GPT-5.4作裁判，另报MRR/Recall等检索指标。

## 3. Conclusion：原文结论及边界

四组ReAct复合分0.707–0.792，Onyx0.686–0.710；长答案完整性分别仅0.496和0.428。更高MRR未必意味着更高终答质量，显示证据获取和综合仍需分开。复合分是作者自定权重的多个0–1指标加权，不是80%任务完成率。

## 4. Future impact：潜在影响

我的推断：可以基于共享事件日志生成多种可见视图，研究长期个人/团队记忆对同一事件的权限、时间版本和责任归属；将过时的事实保留为历史但不作为当前答案，是比简单事实检索更接近部署的评价。

## 5. Critical thinking：我的判断与可检验拓展

样本只有100问、四个项目；同一模型同时作agent和judge，可能共享表达偏好。作者明确未量化合成数据与真实企业分布的相似性，因此“realistic”不能当作实证外部有效性。应增加真实脱敏日志、人类参考答案、独立裁判、可验证时态/责任约束，以及生成种子和测试模板的隔离。

## 6. 可信度、优点与不足

可信度3.5/5；novelty3.5/5。优点是数据生成有可审计底层事件、长期多角色结构、检索与回答质量分解。局限是邮件单模态、小规模评估和权重主观。适合拿来扩展memory benchmark；不能据此认定所有企业RAG的部署能力都低于某个统一百分比。

