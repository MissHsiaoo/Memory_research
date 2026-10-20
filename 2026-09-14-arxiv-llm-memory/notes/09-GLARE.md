# 09｜GLARE: Generative Learning via Adversarial Reward Estimation For Social Dynamics Forecasting

- arXiv：[2609.12165v1](https://arxiv.org/abs/2609.12165v1) · [官方PDF](https://arxiv.org/pdf/2609.12165v1) · [本地PDF](../papers/09-GLARE.pdf)
- 首次提交：2026-09-10（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Tenghao Huang , Zhaoxuan Tan , Muhao Chen , Jonathan May , Mengting Wan , Longqi Yang , Pei Zhou , Sihao Chen
- 核验机构：Microsoft、University of Notre Dame、UC Davis、USC ISI；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业机构／强校合作。研究标签：相邻强启发｜social state / implicit preferences / evolving reward。
- 主观新颖性：4/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§3、§4–5、图3–4、评估协议。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12165-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

GLARE研究如何根据会议前缀和一个当前问题生成合理的多人后续讨论，跟踪议程、角色、意图和分歧。提出MDFB与动态对抗奖励学习；与个性化记忆的联系是保留人的社会状态，而不是把每个人简化成固定persona标签。

## 2. 怎么做，实验怎么做

MDFB从2207次真实会议构建24794个面向未来的问题，按会议级70/20/10划分，避免同一会议跨集。Qwen2.5-7B actor从相同SFT起点出发，Qwen2.5-3B判别器将真实后续排在当前actor生成样本之上，actor用KL正则奖励更新，再刷新负样本。

与SFT、原始Qwen、SPIN及人类真实后续比较。每个系统对随机抽50个测试例、3个人评，顺序随机；评分看问题推进效用和多人交流自然性，而非逐字预测未来。训练报告8张A100约32小时。

## 3. Conclusion：原文结论及边界

对其他四系统平均的人类效用胜率SFT0.58→GLARE0.66，自然性0.55→0.70；仍低于真实人类后续。数值不是GLARE对SFT的单独胜率，也不是预测未来正确率。固定判别器/部分PPO、DPO尝试没有稳定收敛，不能视作已经穷尽同预算RL基线。

## 4. Future impact：潜在影响

我的推断：团队agent可以把角色、未解决争议和议程作为会随交互改变的状态，利用动态负例训练社会推理；对self-evolving memory而言，奖励也可能需要随策略变化重新校准。

## 5. Critical thinking：我的判断与可检验拓展

判别器偏好真实会议续写可能奖励表面文风，而非真实决策改进。人评看到实际未来方向，存在事后偏好；评估单位应按会议聚类，避免同会问题被当独立证据。需要固定教师/奖励预算的强基线、人工分离角色一致性与最终问题解决、以及从未出现的组织和文化迁移测试。

## 6. 可信度、优点与不足

可信度3.5/5；novelty4/5。优点是会议级隔离、真实会议数据、主结果有人评而非仅LLM裁判。局限是每对50例、动态训练稳定性证据有限、并未评估跨会话永久记忆。建议把该方法作为社会状态训练启发，不把续写自然等同于理解真实人类意图。

