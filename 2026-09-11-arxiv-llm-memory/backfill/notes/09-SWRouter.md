# 9. SWRouter

SWRouter: Similarity-Contractive Window Routing for Multi-Turn Large Language Model Conversations

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11414v1](https://arxiv.org/abs/2609.11414v1) · [官方 PDF](https://arxiv.org/pdf/2609.11414v1) · [本地 PDF](../papers/09-SWRouter.pdf)
- 首次提交：2026-09-10T11:45:55Z（UTC，与公告日不是同一概念）。
- 作者：Yu Wang, Yuchen Li, Rui Kong, Xinran Chen, Jiamin Chen, Hengyi Cai, Shuaiqiang Wang, Jiashu Zhao, Yulun Zhang, Zhonghao Lyu, Haoyi Xiong, Linghe Kong, Jimmy Xiangji Huang, Dawei Yin
- 机构：百度、上海交通大学、York、Wilfrid Laurier、香港恒生大学（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜多轮上下文选择 / memory routing
- 原文定位：§4–6，PDF 第 13–17 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

把多轮模型路由与历史上下文窗口构造联合设计，而不是拿完整对话直接做单轮路由。

## 2. 怎么做的，实验怎么做

使用语义相似度收缩历史窗口，再由训练好的 router 选择模型；设计指标区分 prompt construction 和 model selection。mDeBERTa 编码，阈值 0.91、5 个聚类。

实验与结果：7 个 7B/8B Mistral/Llama 系列模型；MTBench、ShareGPT 随机 70/30 划分，router 训练 1,000 steps。随机 beam search 生成每例 10 个候选，由 judge 评分；自定义 evaluation accuracy 从最佳单模型 24.63% 到 40.89%，+16.26 个百分点。另测 PreAlgebra、MBPP、C-EVAL。

## 3. Conclusion

合适的历史窗口对路由质量有明显作用，但其 evaluation accuracy 不是通用问答正确率。

## 4. Future impact

memory selection 与模型选择应该作为两个可独立消融的决策；有时更好的记忆输入比换更强模型重要。

## 5. Critical thinking：优点、问题与可验证拓展

优点是把上下文构造这个混杂因素显式化，并有 ZOOTER 加窗口对照。局限是模型池较旧、MTBench 很小，随机切分需确认对话级隔离；judge/10 候选流程未必对应一次在线回答成本。建议固定同一模型先量化窗口收益，再加入路由并匹配总预算。可信度 3/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**3.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

