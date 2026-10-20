# 14. Think-Before-You-Link

Think Before You Link: Rarity, Reasoning, and Retrieval in Multilingual Entity Linking

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.10745v1](https://arxiv.org/abs/2609.10745v1) · [官方 PDF](https://arxiv.org/pdf/2609.10745v1) · [本地 PDF](../papers/14-Think-Before-You-Link.pdf)
- 首次提交：2026-09-09T18:41:35Z（UTC，与公告日不是同一概念）。
- 作者：Parinthapat Pengpun, Simran Khanuja, Graham Neubig
- 机构：Carnegie Mellon University（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：相邻启发｜长尾事实 / retrieval + reasoning
- 原文定位：§4–7，PDF 第 4–8 页、表 1–4。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

发现罕见实体不仅指低访问量，还包括知识图谱结构稀疏、跨语言资料少；提出推理与迭代检索结合的实体链接。

## 2. 怎么做的，实验怎么做

Qwen3-VL Thinking/Instruct 配合 BM25 或 embedding Wikipedia 检索，迭代搜证后输出实体标题；按 15 种稀有度指标构建 bottom-5% 切片。

实验与结果：MERLIN 五语言，2B/4B/8B × 两种模型 × 三种检索条件，共 18 个配置。8B Thinking+embedding 达 87.9% 宏平均，论文按未舍入结果报告较 Pangea +6.9 点；部分稀有切片 +23.3 点。4B 方法可匹敌更大无检索模型，但约需 2.8 倍推理 tokens；redirect-aware 评分优势变为 4.9 点。

## 3. Conclusion

推理和检索互补，单纯添加检索可能伤害总体表现；不是所有长尾知识都能靠更长思考恢复。

## 4. Future impact

personal memory 恰好充满模型从未见过的长尾实体，评测应按关系稀疏度分层，而不是只测热门事实。

## 5. Critical thinking：优点、问题与可验证拓展

优点是清楚的 factorial 对照与多种长尾定义。局限：Thinking/Instruct 有训练差异，并非纯开关；稀有切片小且重叠；参数节省不等于推理算力节省。建议在私有合成实体上测试同 token 预算的检索与推理，并加入错误记忆。可信度 3.5/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**3.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

