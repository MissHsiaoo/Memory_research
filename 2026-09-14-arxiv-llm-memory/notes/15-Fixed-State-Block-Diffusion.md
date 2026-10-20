# 15｜Fixed State, Long Reach: What a Constant-Size Cache Buys Block Diffusion at Scale

- arXiv：[2609.11998v1](https://arxiv.org/abs/2609.11998v1) · [官方PDF](https://arxiv.org/pdf/2609.11998v1) · [本地PDF](../papers/15-Fixed-State-Block-Diffusion.pdf)
- 首次提交：2026-09-09（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Vaibhav Singh , Pierre-André Noël , Torsten Scholak , Eugene Belilovsky , Oleksiy Ostapenko
- 核验机构：ServiceNow Research、Mila、Concordia University；依据为所下载PDF首页署名。
- 机构优先级：B｜强产业研究团队／专业研究机构。研究标签：直接相关｜diffusion LLM / latent recurrent memory / exact cache。
- 主观新颖性：4.5/5；证据可信度：4/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§3–6、表1–5、局限；官方new批次核验。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.11998-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

研究block diffusion是否能使用与上下文长度无关的精确缓存。统一block-causal训练目标，让完成的块被序列混合器压成可复用状态；纯SSM缓存为O(1)，attention缓存仍O(L)，hybrid只是较小斜率而非O(1)。最有价值的是训练目标、缓存语义和架构共同设计。

## 2. 怎么做，实验怎么做

预训练三个约3B模型：28层attention、28层双向Mamba2、5 attention+23 Mamba的hybrid；300B Nemotron-CC tokens、训练长度1024、块32，统一single-frontier objective。单H100测64到256K、batch1–8，S=16步去噪。

质量评估含NIAH五深度、各长度深度20试验，LongBench16任务每任务20例、2K–16K中间截断，八个下游任务及短续写PPL/MAUVE。性能测到256K不等于语义召回也测到256K。

## 3. Conclusion：原文结论及边界

256K下Mamba约6.8ms/step和7.5GB，attention29ms和82GB；批量容量带来最高14×汇总吞吐。质量方面Mamba八任务均值0.421、attention0.434，有约1.3点差距。16K NIAH的Mamba平均仅22.3%，最近位置接近99%，远处明显差；LongBench约10分，不能称可靠超长记忆。

## 4. Future impact：潜在影响

我的推断：可作为memory-efficient diffusion LLM的架构起点，将固定状态用于频繁访问的信息、外部证据用于罕见精确事实。更关键问题不是能否容纳任意长输入，而是在固定字节预算下能保留多少可恢复信息。

## 5. Critical thinking：我的判断与可检验拓展

训练长度仅1024，使长上下文对比主要测外推，attention的RoPE外推失败可能放大差距。应长上下文等预算重训attention/SSM，匹配实际FLOPs并测多事实、多轮更新和遗忘；系统效率和内容质量必须在同一工作点联合报告。最早提交日期9月9日不能替代公告归属，本次因官方9月14日cs.LG新投稿列表收录而入选，并非仅cross旧文。

## 6. 可信度、优点与不足

可信度4/5；novelty4.5/5。优点是3B/300B统一训练对照、精确缓存条件清楚、报告最近/远处召回差异。局限是低绝对长程质量、较小LongBench样本和短训练窗口。适合深挖架构，不应把“常量缓存”宣传成“无限无损记忆”；该文也是今天diffusion方向另一篇最值得读的工作。

