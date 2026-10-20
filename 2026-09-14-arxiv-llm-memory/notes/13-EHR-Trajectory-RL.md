# 13｜Reinforcement Learning over Patient Trajectories for Clinical Reasoning in EHR Foundation Models

- arXiv：[2609.12277v1](https://arxiv.org/abs/2609.12277v1) · [官方PDF](https://arxiv.org/pdf/2609.12277v1) · [本地PDF](../papers/13-EHR-Trajectory-RL.pdf)
- 首次提交：2026-09-10（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Yuxin Xiao , Sheng Zhang , Chandan Singh , Tristan Naumann , Hoifung Poon , Jianfeng Gao , Xiaodong Liu
- 核验机构：MIT、Microsoft Research；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级高校／顶级产业实验室。研究标签：弱相关但具启发性｜longitudinal state / rollout censoring / small models。
- 主观新颖性：3.5/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§方法概述、§4.1–4.2、表1及校准分析。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12277-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

将EHR基础模型视为生成未来患者事件轨迹的policy，用时间敏感的RL奖励增强预测。与LLM memory并非直接同类：模型主要是9M/56M的结构化事件模型。值得借鉴的是有限rollout下“没看到事件”不等于“事件不会发生”，这也适用于agent对长期后果的记忆与信用分配。

## 2. 怎么做，实验怎么做

把预测改成以锚点事件和时间窗口为条件的任务，奖励考虑轨迹长度以及时间上仍未确定的结果；采用GRPO或DAPO。MIMIC-IV v2.2，沿用既有数据划分，训练时平衡正负类；三个任务为30天再入院、2年ICU再入院和2年住院死亡。

对照ETHOS预训练、SFT、logistic与部分任务的9M encoder，另将轨迹转英文测医疗LLM。测试每例20次随机rollout以阳性比例形成风险分数；RL每例8次，prefix和rollout最长各2048。

## 3. Conclusion：原文结论及边界

30天任务56M模型AUROC从0.7493提高到DAPO0.7644，AUPRC从0.4900到0.5153；9M DAPO AUROC0.7515，略高56M预训练。9M ECE从0.0823降至GRPO0.0325。这里是离线预测结果，不是临床治疗收益，也不能将AUROC提升理解为相同幅度准确率提升。

## 4. Future impact：潜在影响

我的推断：memory系统可以保留“尚未成熟的结果”，对未覆盖观察窗口的经验延迟写入成功/失败标签；不要把超时或截断直接记录成永久失败规则。结构化轨迹的小模型也可能比自然语言大模型更适合某些状态预测。

## 5. Critical thinking：我的判断与可检验拓展

单中心历史数据与训练平衡方式可能改变校准，部署必须按真实基率复验。比较大语言模型时事件编码和训练数据不同，不能得出“小模型普遍优于LLM”。每例20rollout的推理成本不可忽略；需要跨医院、时间切分、bootstrap区间和独立外部验证。文中配对loss显著性也不是AUROC差异显著性的同义词。

## 6. 可信度、优点与不足

可信度3.5/5；novelty3.5/5。优点是时间窗口/截断意识、结构化对照及校准指标。局限是特定医学数据、比较编码条件不同、没有真实临床干预验证。这里仅提炼研究方法启发，不作医疗应用建议；最直接可迁移的是对长期回报未决状态的谨慎标记。

