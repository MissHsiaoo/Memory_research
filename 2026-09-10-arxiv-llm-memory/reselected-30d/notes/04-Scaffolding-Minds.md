# 4. Scaffolding-Minds

Scaffolding Minds: Optimizing Latent Visual Target Representations for Multimodal Reasoning

- 论文：[arXiv 2608.19669v1](https://arxiv.org/abs/2608.19669v1) · [本地 PDF](../papers/04-Scaffolding-Minds.pdf)
- 首次提交：2026-08-20（UTC）；arXiv 最新记录：2026-08-20。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Haoqiang Kang、Yinpeng Chen、Luyang Liu、Jesper Sparre Andersen、Abhijit Ogale、Baochen Sun、Lichan Hong、Ed H. Chi
- 已核验机构：Google DeepMind、UC San Diego（PDF 首页署名）
- 机构优先级：A｜一线产业研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：latent reasoning / multimodal RL；弱相关但可迁移到 latent memory
- 主观 novelty：4.5/5；证据可信度：3.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–4；附录 C–D（PDF 第 18–20 页）。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**强机构的跨方向启发：既学习 latent target，也学习 latent 空间的探索分布。

## 1. 做了什么

研究视觉推理的连续 latent token。作者认为现成视觉 encoder 给出的目标表示未必适合推理，单纯确定性约束也限制 latent 探索。

## 2. 怎么做的

先训练专用 scaffolding encoder，把 helper image 压成 4 个 latent token；再训练 VLM 从原始输入预测这些目标。RL 阶段学习 latent 扰动的均值和方差，推理时不使用 helper-image encoder。

## 3. 实验如何设计，结果如何

基于 Qwen2.5-VL-7B；FrozenLake 用 4,550 个训练样本，测试各等级 100 个；并测九个视觉推理基准。FrozenLake 平均从最强 latent baseline 65.5 到 75.0，32×32 从 36 到 55。训练等级已含 32×32，因此后者是难度分层结果，不是未见网格尺寸外推。附录说明 MMVP 用发布问题的 70% 训练、30% 测试。

## 4. Conclusion

任务对齐的 latent supervision 与随机探索互补；这些结果不能直接当作公开零样本 leaderboard 分数。

## 5. Future impact：对你的研究有什么启发

可把历史交互当成 privileged helper，训练一个 memory teacher 提供 task-aligned latent target，再让在线 agent 仅凭有限历史产生记忆，并通过 RL 优化读取。

## 6. Critical thinking、优点、局限与置信度

优点：目标表示与探索机制分别消融，训练资源和划分有披露。局限：需要 helper supervision；部分数据采用自定义训练/测试分割；还没有持久记忆或多用户实验证据。建议比较固定文本重构目标和任务收益目标，并在 unseen users + unseen tasks 上测试。可信度 3.5/5：对本论文视觉任务有效的证据较强，向长期记忆迁移仍是假设。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

