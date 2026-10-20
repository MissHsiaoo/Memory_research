# 17. WHALE

WHALE: A Simple Recipe for Joint Harness-Weight Optimization

- 论文：[arXiv 2609.00196v1](https://arxiv.org/abs/2609.00196v1) · [本地 PDF](../papers/17-WHALE.pdf)
- 首次提交：2026-08-31（UTC）；arXiv 最新记录：2026-08-31。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Haechan Kim、Yoonho Lee、Gisang Lee、Chelsea Finn、Kangwook Lee
- 已核验机构：KRAFTON、KAIST、Stanford（PDF 首页署名）
- 机构优先级：A｜强产业研究组＋顶尖高校。这是本次选刊层级，不是学校综合排名。
- 主题：agent coevolution / harness-weight optimization；跨方向启发
- 主观 novelty：4/5；证据可信度：2.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §4–5；PDF 第 5 页算法 1、第 6 页评测设置、附录 B。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**让模型权重与外部执行系统交替适应，可迁移到 memory reader/writer 的联合优化。

## 1. 做了什么

WHALE 认为固定权重只改 harness、或固定 harness 只训练权重，都会受另一方限制，因此交替优化两者。

## 2. 怎么做的

权重阶段用 online rejection-sampling fine-tuning；harness 阶段使用 Meta-Harness 搜索上下文组织、工具格式、终止规则等。固定阶段长度或 patience rule 决定何时切换。

## 3. 实验如何设计，结果如何

Qwen3.5-2B 做 SearchQA/数学，4B 做棋题；分别留 256 个 harness-search 样本，测试 700/60/256 题，每题 8 次。比较 weight-only、harness-only 和 prompt-restricted FST；报告最好 mean@8 提升 4.15–24.38 个百分点，正文图为 best-so-far test curve。

## 4. Conclusion

交替优化的机制有吸引力，但已报告最高分不是一次性未见终测结果。

## 5. Future impact：对你的研究有什么启发

可设计 memory 表示—reader 权重的双层学习：先更新 reader，再重构/重新压缩 memory；用冻结终测检测是否只是适应当前记忆格式。

## 6. Critical thinking、优点、局限与置信度

优点：有单组件、prompt-only 和阶段次序对照，搜索空间明确。关键问题：算法 1 第 17 行写明返回测试集最好组合，存在测试选择偏差；小数学集仅 60 题，best-so-far 与反复评测会放大偶然收益。建议以独立 dev 选 checkpoint，仅终测一次，并计入强 proposer 成本。可信度 2.5/5：研究想法值得读，提升幅度先打折。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

