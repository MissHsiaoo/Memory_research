# 16｜LifeMem: Enabling Lifelong Experience Reuse for LLM Agents

- arXiv：[2609.12655v1](https://arxiv.org/abs/2609.12655v1) · [官方PDF](https://arxiv.org/pdf/2609.12655v1) · [本地PDF](../papers/16-LifeMem.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Yuli Qiu、Yutong Li、Wei Su、Zeming Liu、Wanxiang Che、Heyan Huang、Haifeng Wang、Yuhang Guo（PDF）
- 核验机构：Baidu、北京理工大学、北京航空航天大学、哈尔滨工业大学；依据为所下载PDF首页署名。
- 机构优先级：B｜强产业团队／研究型高校。研究标签：直接相关｜lifelong agent memory / skill extraction / forgetting。
- 主观新颖性：4/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§4–6、表2、Limitations及协议说明。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12655-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

LifeMem让agent跨不同环境持续积累经验，用workflow层面的共同结构组织轨迹，而不只按任务文本语义相似度检索。它将可复用技能与具体执行轨迹结合，试图缓解记忆越来越多后相互干扰的问题，直接对应lifelong和self-evolving memory。

## 2. 怎么做，实验怎么做

先从少量轨迹形成工作流簇，新轨迹检索近邻后决定加入或新建；当簇过于分散，用方向统计的Mean Resultant Length及规模阈值触发拆分，再抽象技能。执行时召回技能和环境相关轨迹。存储SQLite、检索FAISS/MiniLM，轻量模型做簇分配，GPT-4.1做拆簇与技能提取。

十任务、五场景，12489训练实例和1230测试实例，比较ReAct、Synapse、ExpeL、AutoSkill；GPT-4o-mini、DeepSeek-v3.2-exp、Qwen3-32B三个主干。默认按环境顺序学习，也分析随机和buffer流。

## 3. Conclusion：原文结论及边界

三个模型最终平均表现均领先所列基线，GPT-4o-mini44.13、DeepSeek48.02、Qwen46.52；平均backward transfer为正。但并非每场景都最佳，例如DeepSeek网页浏览的ReAct48.07高于LifeMem34.08，Qwen数据分析ExpeL75.00高于LifeMem70.00。文中5.45%等箭头为相对提升，不能当百分点。

## 4. Future impact：潜在影响

我的推断：技能作为抽象策略、轨迹作为执行格式证据的双层记忆值得复用，特别适合环境不同但流程类似的任务。下一步可为簇添加适用环境版本和失效条件，防止“类似工作流”被错误迁移。

## 5. Critical thinking：我的判断与可检验拓展

经验抽取器比部分执行模型强，需分离强教师监督与结构化存储的贡献。没有训练划分的benchmark自行生成训练轨迹，必须仔细审查与评测任务的隔离，不能默认不存在信息泄漏。百万级记忆下拆簇和重新摘要开销未验证；平均正BwT可能掩盖局部严重退化。

## 6. 可信度、优点与不足

可信度3.5/5；novelty4/5。优点是跨环境三模型、技能与轨迹明确分工、测试任务流变化。局限是外部模型依赖、部分数据生成隔离需复核、规模化成本不充分。建议以固定总token和教师预算复现，报告每个任务的负迁移、错误技能激活率及删除/重构代价。PDF作者写Yuhang Guo，而列表有Yuang差异，正式作者以PDF为准。

