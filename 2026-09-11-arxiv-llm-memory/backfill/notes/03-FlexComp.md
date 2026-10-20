# 3. FlexComp

FlexComp: One Model for Every Ratio in Context Compression

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11192v1](https://arxiv.org/abs/2609.11192v1) · [官方 PDF](https://arxiv.org/pdf/2609.11192v1) · [本地 PDF](../papers/03-FlexComp.pdf)
- 首次提交：2026-09-10T07:59:52Z（UTC，与公告日不是同一概念）。
- 作者：Kaiyan Zhao, Zhongtao Miao, Akiko Aizawa, Yoshimasa Tsuruoka
- 机构：东京大学、National Institute of Informatics（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜soft memory / 自适应压缩预算
- 原文定位：§3–5、表 1/6，PDF 第 4–10 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

把每种压缩比都训练一个模型，改为一个压缩器支持多个 memory-token 预算，并按输入选择预算。

## 2. 怎么做的，实验怎么做

Matryoshka 式训练为每条样本抽取 K；推理可由答案置信度级联尝试，或用轻量 K predictor 一次选择。后者基于上下文本身、与查询无关，包含 budget-free encoder pass，不能视作零额外开销。

实验与结果：在 ICAE、500xCompressor、SAC 上使用 Llama-3.2-1B，510-token chunk，K={1,10,34}；SlimPajama 预训练及 MRQA 微调，评估 6 个 ID 和 6 个 OOD 任务，并扩展到 SAC/8B。8B 的 K predictor 达 183×平均压缩，ID/OOD F1 为 67.69/53.27，对应固定 15× Matryoshka 为 68.11/53.99。另报告服务批量下 KV 减半、解码吞吐 +47%。

## 3. Conclusion

预算可学习，更多 memory tokens 并不必然更好；平均压缩比不等于端到端同等倍数的加速。

## 4. Future impact

适合做 query-conditioned 或 uncertainty-conditioned latent memory allocation，将总用户记忆预算作为优化约束。

## 5. Critical thinking：优点、问题与可验证拓展

优点是跨压缩架构、同条件固定比例对照及 OOD 检查。局限：QA 为主，级联的重复编解码成本要计入；query-agnostic 预算可能压掉少数未来问题需要的细节；§5.5 的可解样本分析排除了所有预算均失败的样本。建议按用户时间流和罕见事实回忆评估，而非只用平均 F1。可信度 4/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**4/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

