# 17. Bellman-Plasticity

A Bellman Optimality Equation for Plasticity

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.10776v1](https://arxiv.org/abs/2609.10776v1) · [官方 PDF](https://arxiv.org/pdf/2609.10776v1) · [本地 PDF](../papers/17-Bellman-Plasticity.pdf)
- 首次提交：2026-09-09T19:23:56Z（UTC，与公告日不是同一概念）。
- 作者：Jeremy Lucas, Doina Precup
- 机构：Mila – Quebec Artificial Intelligence Institute（PDF 首页；未按作者其他职务写成 DeepMind）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：弱相关但具启发性｜continual learning / plasticity
- 原文定位：§2–6、附录 A，PDF 第 5–7 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

为信息论定义的 plasticity 构造 Bellman optimality equation，将环境对行动的信息影响转成可优化量。

## 2. 怎么做的，实验怎么做

在增广历史上下文上做 tabular value iteration，分析 Bellman operator 的收缩及策略端点性质；plasticity 的定义是观测到动作的定向信息，不等于常说的神经网络训练可塑性。

实验与结果：Control-Gated MDP、5 状态 3 动作 Road、35 状态 Two-Room。前两者 100 次实验、后者 10 次。Control-Gated 收敛约 0.92 bits plasticity、0 empowerment；原文指出相同最优 value 的策略仍可有不同 total plasticity，提示 Bellman 形式与完整 directed-information 定义之间的差异。

## 3. Conclusion

提供一个初步理论与玩具环境工具，不是已经可用于 LLM continual learning 的成熟算法。

## 4. Future impact

启发是将“保持可更新性”显式放进长期 agent 目标；但须先决定是否奖励有用适应，而非仅对随机噪声敏感。

## 5. Critical thinking：优点、问题与可验证拓展

优点是数学目标明确并配有可控环境。局限是需要模型/小状态空间，信息流目标可能偏好噪声而非效用；尚无 LLM 实验。建议先构建有稳定用户偏好和随机干扰的双过程环境，检验 plasticity reward 是否误吸收噪声。可信度 3/5：理论初步，应用证据有限。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

