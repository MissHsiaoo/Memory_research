# 8. REVA

REVA: Reusable Evidence View Aggregation for Context-Efficient RAG Serving

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11209v1](https://arxiv.org/abs/2609.11209v1) · [官方 PDF](https://arxiv.org/pdf/2609.11209v1) · [本地 PDF](../papers/08-REVA.pdf)
- 首次提交：2026-09-10T08:14:22Z（UTC，与公告日不是同一概念）。
- 作者：Tuan Nguyen, Qiran Hu, Banruo Liu, Khoa D. Doan, Kok-Seng Wong, Fan Lai
- 机构：UIUC、VinUniversity / VinUni-Illinois Smart Health Center（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜历史经验复用 / RAG 压缩记忆
- 原文定位：§IV–V，PDF 第 4–8 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

将历史 query-document-model 交互的 attention 统计变成可复用文档证据视图，减少每次在线压缩。

## 2. 怎么做的，实验怎么做

将 token 注意力映射到可读词单元，按文档键累计分数；在线按预算与文档配额裁剪，保留普通文本接口。未覆盖文档回退 prefix truncation，历史得分只是先验而非当前问题保证。

实验与结果：4×H100，Llama-3.1-8B、Qwen3.5-9B、Gemma-4-E4B；NQ、TriviaQA、HotpotQA、2Wiki。固定 e5 检索 top-10，所有方法共用结果；训练集构建冻结 score store，测试问题/答案不参与自身上下文构建。区分 full-split 和 all-seen strict reuse。报告较先进压缩器高 1.0–5.8 点，在线压缩开销 <40ms。

## 3. Conclusion

重复访问文档时，历史证据视图能有较好在线质量/成本折中；报告在线开销排除 store 构建与更新。

## 4. Future impact

长期用户记忆可以记录“哪些片段在哪些问题上曾有用”，但应加时间衰减与查询分群，避免热门片段垄断。

## 5. Critical thinking：优点、问题与可验证拓展

优点是冻结训练 store 和测试隔离、缺失覆盖回退。局限是收益依赖重复访问；attention 非因果贡献，旧模型/旧兴趣统计可能失效；all-seen 子集不能代表冷启动。建议报告全量生命周期成本，并做用户兴趣切换、文档更新与低覆盖率压力测试。可信度 3.5/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

