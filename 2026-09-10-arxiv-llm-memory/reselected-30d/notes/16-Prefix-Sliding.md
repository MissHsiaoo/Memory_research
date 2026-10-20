# 16. Prefix-Sliding

Prefix Sliding for efficient test-time scaling

- 论文：[arXiv 2608.26070v1](https://arxiv.org/abs/2608.26070v1) · [本地 PDF](../papers/16-Prefix-Sliding.pdf)
- 首次提交：2026-08-26（UTC）；arXiv 最新记录：2026-08-26。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Niklas Muennighoff、Zhengyang Wang、Zeyi Chen、Weijia Shi、Binyuan Hui、John Yang、Dapeng Jiang、Mika Senghaas、Fares Obeid、Johannes Hagemann、Sami Jaghouar、Ludwig Schmidt、Percy Liang、Jason Wei、Andrew Y. Ng、Luke Zettlemoyer、Yejin Choi、Mike Lewis
- 已核验机构：Stanford、University of Washington、UC Santa Barbara、Prime Intellect（PDF 首页署名；未将作者个人经历当作 OpenAI/Meta 合作）
- 机构优先级：A｜顶尖高校相关研究组。这是本次选刊层级，不是学校综合排名。
- 主题：working memory / test-time scaling / context compression
- 主观 novelty：3.5/5；证据可信度：4/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–5；PDF 第 4–9 页；Limitations。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**极简的有界记忆基线能显著提速，是验证复杂 memory 方法收益的必备对照。

## 1. 做了什么

保留系统/任务前缀与最近滑动窗口，逐步丢弃中间推理 token，让每个新 token 的历史成本有界。

## 2. 怎么做的

既可在已有模型上免训练运行，也能用 GRPO 训练模型适应该上下文机制；实现定制 Hopper kernels，比较窗口长度、摘要和普通 sliding window。

## 3. 实验如何设计，结果如何

主要 Qwen3-1.7B，窗口 512–16,384；GPQA、MATH500、AIME25，64 次采样平均 avg@64，按实际 thinking time 衡量效率。文中报告可约 3 倍提速；LiveCodeBench 需要至少 16K 窗口才能匹配 full attention，代码开头被长注释挤出是具体失败例子。

## 4. Conclusion

很多中间推理可丢弃，但长期依赖、工具输出和多轮指令可能超出短窗口机制的能力。

## 5. Future impact：对你的研究有什么启发

你的 memory system 应首先击败 prefix+recent-window 这一便宜对照。可增加按依赖保留的 pins，让关键代码/约束移入前缀或长期记忆。

## 6. Critical thinking、优点、局限与置信度

优点：直接测时间、公开失败情形、对摘要策略有对照。局限：主要模型小；摘要 baseline 有固定长度约束；64 次平均准确率不是 pass@64。建议在相同时间和显存预算下比较压缩、检索和动态 pins，并测试工具返回突然挤占上下文。可信度 4/5：效率机制明确，何时失效也有证据。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

