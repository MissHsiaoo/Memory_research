# 11. Negative-Self-Distillation

Negative Self-Distillation: Learning to Reason by Avoiding Flaws

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11699v1](https://arxiv.org/abs/2609.11699v1) · [官方 PDF](https://arxiv.org/pdf/2609.11699v1) · [本地 PDF](../papers/11-Negative-Self-Distillation.pdf)
- 首次提交：2026-09-10T15:24:17Z（UTC，与公告日不是同一概念）。
- 作者：Rongcan Pei, Zhepei Wei, Shuyao Xu, Xinyu Zhu, Wei-Lin Chen, Yu Meng
- 机构：University of Virginia、Stanford（PDF 首页；NVIDIA/Amazon 为致谢资助，不算作者单位）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：相邻启发｜self-improvement / 失败经验学习
- 原文定位：§3–4、表 1、Limitations，PDF 第 6–11 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

让模型远离自己在负面条件下的推理分布，而非模仿看到标准答案的过度自信 teacher。

## 2. 怎么做的，实验怎么做

模型为问题生成负面条件，构造 frozen negative teacher；动态 token gate 区分推理相关差异与基础语言 token，防止无差别 unlearning 损害流畅性。

实验与结果：Qwen3 1.7B/4B/8B，在 AIME 2024/25/26、HMMT、AMC、OlympiadBench、MATH-500 上评估；验证集选两 epoch 内最佳 checkpoint。主指标 non-thinking 模式 Avg@8，七项平均绝对增益 +2.3/+7.5/+6.0 个百分点，报告置信区间和单侧 p 值，不是 pass@8。OlympiadBench 使用 675 个非证明开放数学题。

## 3. Conclusion

在这些数学任务中，负面条件提供有效自训练信号；不代表模型无需任何能力基础或所有自蒸馏都会失败。

## 4. Future impact

可将 agent memory 中的失败经验用于生成“应避免的推理模式”，而非仅附加一条禁止句。

## 5. Critical thinking：优点、问题与可验证拓展

优点是无训练答案标签的设计、规模对照和验证集选点。局限是负面条件质量依赖原模型，仍需额外生成和多个 forward；数学范围外尚不明确，token gate 可能误删探索性步骤。建议与等算力正/负经验记忆做对照，并测未见任务和语言能力回归。可信度 3.5/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

