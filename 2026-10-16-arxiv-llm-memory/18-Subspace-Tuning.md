# 18. Subspace Tuning：限制更新方向以减少遗忘

- 论文：[arXiv:2610.22293](https://arxiv.org/abs/2610.22293) · [官方 PDF](https://arxiv.org/pdf/2610.22293) · 本地 PDF：`2610.22293.pdf`
- 公告：2026-10-16；初次提交：2026-10-15。
- 作者/机构：PDF 首页核验 Arnav Chavan、Kusha Sareen 等；UC Berkeley、Mila、McGill、UMass Amherst、Google、UT Austin 等。**机构优先级 P2**（高校及 Google 合作；论文首页仅写 Google，未臆称 DeepMind）。
- 主题：continual learning；catastrophic forgetting；parameter update geometry。证据范围：全文 31 页。

1. **做了什么（论文证据）**：提出 SST，使每次权重更新只在较低奇异子空间内进行，保护主要奇异方向以减少微调遗忘。
2. **怎么做与实验（论文证据）**：可与 SFT/自蒸馏等优化配合，含密集梯度估计与周期刷新；测新任务学习、旧能力保持、模型规模与相对基础分布 KL 漂移。
3. **结论（论文证据）**：保护最多 99% 权重子空间仍保留较强目标任务效果并提升旧能力保持；相对基线 KL 漂移低约 2–4 倍。作者称大模型设置几乎消除遗忘，但这仍是所测任务条件下的结果。
4. **未来影响（我的推断）**：若参数化用户/任务记忆需要长期增量写入，更新几何的约束可能比简单 LoRA 更稳。
5. **Critical thinking**：不同方法最优学习率未必相同；需完全调优的公平学习—保持前沿、百亿以上模型和更长任务序列，作者也列为未来工作。
6. **可信度 4/5**：机制与跨规模指标清晰；长期开放式记忆写入仍未直接验证。
