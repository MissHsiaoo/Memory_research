# VibeMemBench: Evaluating Memory Systems for Coding Agents on Real Repository Coding Tasks

- arXiv：[23570](https://arxiv.org/abs/2609.23570)；[官方 PDF](https://arxiv.org/pdf/2609.23570)
- arXiv 初次提交：2026-09-20（v1）；正式公告归属：2026-09-22 新稿，二者不可混同。
- 作者：Liyang Fan , Yingcheng Shi , Yongbin Li , Chenghao Sun , Xin Chen , Xander Xu , Hu Wei , Shiwen Ni , Min Yang , Jieping Ye（arXiv 官方列表）
- 机构：Alibaba Group / Token Hub（论文首页署名）（论文 PDF 首页核验）
- 机构优先级：A｜顶级产业研究
- 研究标签：coding agent memory；跨任务经验；评测；直接相关
- 证据说明：以下数值均为论文自身报告；“我的推断/建议”并非论文实证。

## 1. 做了什么

VibeMemBench 问一个苛刻但实际的问题：编码 agent 在做新仓库修复时，过去经验能否真的提高解题率。论文区分“给它一条已验证相关经验”与“让现成记忆系统自主写入、检索”，避免把记忆本身的潜力和检索实现混为一谈。

## 2. 怎么做，实验怎么做的

从 90 个 SWE-rebench V2 仓库构造 111 个目标及 3634 条历史，跨四个随机种子形成 444 组目标评测。控制同一求解器有/无记忆，并设置 frozen verified experience 作为上限参考。论文报告已验证经验使五个求解器中的四个提高 1.1–4.5 个百分点，但 95% bootstrap 区间都跨零；DeepSeek-V4-Pro 几乎不变。测试的现有记忆系统在 12 个检索配置中有 11 个不高于匹配的无记忆基线，没有一个的置信区间明确高于零，其中一个显著更差。

## 3. Conclusion

“历史经验可能有用”与“目前自动记忆系统已可靠有用”是两件不同的事。本文数据更支持后一个命题尚未成立；不能把小幅上升当成稳健统计胜利。

## 4. Future impact

它把编码记忆研究从“检索看似相关”推进到“修复是否成功”。我认为后续的 agent skill library 应采用类似配对实验，并保存不适用条件、代码版本、失败案例，而不只是成功补丁摘要。

## 5. Critical thinking

基准使用经参考补丁/效果筛过的记忆候选，理想经验有选择偏差，不代表真实积累难度。需要跨仓库、跨版本、跨语言评估，还要测 token、延迟、价格和负迁移。一个尤其关键的实验是把一段看似相似但 API 已变化的旧经验注入系统，观察 agent 是否会核验再使用。论文因预算未覆盖 Claude/GPT 等更广泛前沿求解器，不宜对全部 coding agents 下结论。

## 6. 可信度判断、优点与局限

4/5：已核查构造方式、配对对比、bootstrap 区间和限制。优点是负结果报告清楚，问题定义贴近生产；局限是筛选出的经验和有限 solver 组合可能限制外推。
