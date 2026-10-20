# 13. SearchAtlas

SearchAtlas: Analyzing Agentic Search Strategies via Evidential Query Graphs

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.10901v1](https://arxiv.org/abs/2609.10901v1) · [官方 PDF](https://arxiv.org/pdf/2609.10901v1) · [本地 PDF](../papers/13-SearchAtlas.pdf)
- 首次提交：2026-09-09T23:09:26Z（UTC，与公告日不是同一概念）。
- 作者：Jiacheng Sang, Mengyuan Li, Sanxing Chen, Yukun Huang, Yu Feng, Bhuwan Dhingra
- 机构：Duke、University of Pennsylvania（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜agent 证据记忆 / 过程评估
- 原文定位：§3–5、Limitations，PDF 第 5–10 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

将搜索 agent 的长日志转成证据依赖 DAG，识别答案的支持链、没被满足的约束以及未验证参数知识。

## 2. 怎么做的，实验怎么做

确定性整理 query、搜索结果、页面访问，再由 LLM 归因哪些已有证据支持后续 query 与答案；按顺序依赖/并行约束问题选择不同诊断指标。

实验与结果：5 种 agent 配置、1,350 条轨迹；BrowseComp 150 题、WebWalker-Hard-English 70 题、DeepSearchQA 两类各 25 题。对 100 个人工图核验，四种归因 LLM 的边 F1 为 0.814–0.860；过程诊断与错误的关联优于全文日志 judge，并审计 100 个过程分与答案正确性不一致案例。

## 3. Conclusion

结构化证据图提供超出最终答案分数的信息，但图不是模型内部推理的直接读数。

## 4. Future impact

可把 memory 的价值从“被检索过”改为“为哪条结论提供过可追溯支持”，用于经验筛选与压缩。

## 5. Critical thinking：优点、问题与可验证拓展

优点是人工标注、不同归因模型与同 scaffold 换 backbone 的比较。局限：只看可见日志；系统性归因错误仍可能共享，构图有额外推理成本；闭答案英语任务对开放式个性化帮助的外推有限。建议用干预删除证据来验证边，而非把相关图当因果图。可信度 3.5/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

