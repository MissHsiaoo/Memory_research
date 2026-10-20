# 18. Qiushi-Engine

Data-Efficient Language Modeling: From Frontier Advancement to Principle-Guided Model Improvement

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.10702v1](https://arxiv.org/abs/2609.10702v1) · [官方 PDF](https://arxiv.org/pdf/2609.10702v1) · [本地 PDF](../papers/18-Qiushi-Engine.pdf)
- 首次提交：2026-09-09T18:00:52Z（UTC，与公告日不是同一概念）。
- 作者：Shuxing Yang, Kaihao Zhu, Junjie Yang, Rui Zhao, Junyao Wu, Yize Wang, Wenhao Li, Fujia Chen, Taowen Deng, Shenzhan Hong, Yaqi Li, Zichen Li, Jincheng Mi, Yuang Pan, Hongsheng Chen, Yihao Yang
- 机构：浙江大学信息与电子工程学院、Qiushi Engine Team（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：相邻启发｜research self-improvement / 保留与泛化
- 原文定位：§1、§3–4，附录 R69–R74；PDF 第 5–8、54 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

展示自动研究系统从训练小语言模型，到发现数据使用原则，再把原则用于新一轮模型改进的长程过程。

## 2. 怎么做的，实验怎么做

以 BabyLM Strict-Small 为受控场景，结合压缩重述、关系学习、稀疏监督和能力保留；显式分开模型是否学会、能否用于新符号、继续训练后是否保留。

实验与结果：预算为 10M corpus words / 100M cumulative word presentations，不是 tokenizer tokens。九项指标综合分由 Frontier 42.02 到 Principle-guided 42.25；两 continuation seeds 的完整方案都优于普通继续训练，但这是同一 parent 的两个 seed，不是两个独立研究团队复现。公共榜单仅为 9 月 8 日快照。

## 3. Conclusion

研究过程可积累可检验原则并反馈训练；小幅分数提高不能单独证明自主科学发现能力普遍突破。

## 4. Future impact

self-evolving memory 的重点可从保存结论扩展到保存“适用条件、对照证据、失败边界”，让下一轮自动实验可检验旧原则。

## 5. Critical thinking：优点、问题与可验证拓展

优点是公开完整研究路径、预算口径和反例。局限是方法包含多个同时变化因素，+0.23 不能归因于单一原则；选择历史和额外研究算力应单独报告。建议对冻结的初始研究 agent 比较有无结构化实验记忆，并对未见研究任务测试。可信度 3.5/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**3.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

