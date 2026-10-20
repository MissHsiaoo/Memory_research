# 13. Survival-Length-Control

Survival-Guided Length Control for Efficient Diffusion Language Models

- 论文：[arXiv 2608.26374v1](https://arxiv.org/abs/2608.26374v1) · [本地 PDF](../papers/13-Survival-Length-Control.pdf)
- 首次提交：2026-08-26（UTC）；arXiv 最新记录：2026-08-26。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Ivan Kobyzev、Abbas Ghaddar、Yufei Cui
- 已核验机构：Huawei Noah’s Ark Lab，Montreal Research Center（PDF 首页署名）
- 机构优先级：A｜成熟产业 AI 研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：diffusion LLM / adaptive compute / stopping
- 主观 novelty：4/5；证据可信度：3/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §2–3；PDF 第 2–4 页、表 1–3。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**从一次去噪中的 EOS 概率预测所需长度，用生存分析控制 dLLM 推理成本。

## 1. 做了什么

固定长画布会浪费 diffusion 推理，本文按样本预测生成长度，再只在较短范围去噪。

## 2. 怎么做的

把输出位置上的终止事件视作离散 survival process，用初始全 mask 画布的 EOS 概率近似 hazard，形成 survival curve 和期望长度。该步骤不训练额外模型，但依赖 EOS 校准和条件独立近似。

## 3. 实验如何设计，结果如何

LLaDA-8B-Base、Dream-7B，测试 BBH、GSM8K、MATH、HumanEval、MBPP，batch=1；对照默认 Lmax=1024。表格加速约 3.1–6.6 倍；Dream GSM8K 81.4→12.3 秒，准确率 74.5→74.6。另与数据集平均预测长度作为固定长度的版本比较。

## 4. Conclusion

固定大画布是这些设置的重要浪费源，按样本预测长度能明显省成本；“任何 DLM、无损、7 倍”都应限定适用条件。

## 5. Future impact：对你的研究有什么启发

可迁移到 memory budget：用估计的未来证据需求而非固定 token 上限分配记忆；或在 personalized diffusion generation 中依用户任务预测输出预算。

## 6. Critical thinking、优点、局限与置信度

优点：training-free、机制短、存在固定均值长度消融。局限：边缘 EOS 概率不天然等于条件 hazard；硬件只写 modern accelerator，难复核时延；表中 BBH 49.5±0.6→51.8±0.6 与正文“差异均在标准差内”的概括不一致。建议明确硬件、完整计入预测 pass，测试长尾截断和高并发。可信度 3/5：效率机会合理，统计描述需复核。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

