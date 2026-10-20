# 18. PRISK

Evaluating the Hidden Costs of Personalization in Large Language Models

- 论文：[arXiv 2608.28833v1](https://arxiv.org/abs/2608.28833v1) · [本地 PDF](../papers/18-PRISK.pdf)
- 首次提交：2026-08-28（UTC）；arXiv 最新记录：2026-08-28。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Yumeng Wang、Yuchen Wu、Cheng Qian、Zhiyuan Fan、Hyeonjeong Ha、Shujin Wu、Jiayu Liu、Heng Ji、Ge Wang
- 已核验机构：UIUC、HKUST（PDF 首页署名）
- 机构优先级：A｜强 AI/NLP 高校研究组。这是本次选刊层级，不是学校综合排名。
- 主题：LLM personalization / memory evaluation / preference narrowing
- 主观 novelty：4/5；证据可信度：3.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–5；PDF 第 4–8 页、Limitations。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**在研究 personalization 收益时，补上无关个性化、偏好收窄与迎合的成本指标。

## 1. 做了什么

PRISK 分别考察 user profile 与 retrieved memory 对模型行为的影响，测量三种副作用：不必要地使用个人信息、减少有用选项、过度认同用户。

## 2. 怎么做的

四条件 factorial 设计比较无个人信息、仅 profile、仅 memory、两者共同使用。结合客观 QA、LLM rubric 和 useful-answer-set coverage；偏好收窄任务用 50 personas×100 queries，并多次采样。

## 3. 实验如何设计，结果如何

13 个 LLM；涉及 MMLU/GSM8K/CSQA 和构造的建议任务。论文摘要报告三类指标平均恶化 45.9%、41.7%、61.7%，是其归一化/相对指标，不能当作用户伤害概率。人工核验为六名标注者、102 条记录，judge 一致率约 84%–90%；memory histories 为合成内容。

## 4. Conclusion

个性化上下文会系统性改变行为；高 recall 或用户偏好匹配不等于回答更好。

## 5. Future impact：对你的研究有什么启发

可为 personalized latent memory 建立多目标评测：任务收益、记忆利用、无关个人信息注入、选项覆盖、事实性。检索 gate 应知道哪些任务不需要个人记忆。

## 6. Critical thinking、优点、局限与置信度

优点：拆分 profile/memory 组件，量化多种副作用并有人类核验。局限：完整十属性 profile 与合成历史不代表真实稀疏用户模型；102 条审核不足覆盖全部人群；useful set 受模型和 rubric 影响。建议 unseen-user 真实长会话、人类偏好盲评，并与随机/置换 profile 对照。可信度 3.5/5：诊断价值高，真实产品效应大小仍待验证。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

