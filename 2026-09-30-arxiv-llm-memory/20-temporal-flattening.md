# 20 — Memory Consolidation Flattens the Temporal Shape of User Facts

- arXiv：[2609.36457](https://arxiv.org/abs/2609.36457)；[官方 PDF](https://arxiv.org/pdf/2609.36457)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Sugam Panthi、Muhaiminul Yeamin、Siyan Luo、Rabab Abdelfattah；AIMS Lab, University of Southern Mississippi
- 机构优先级：**B（黑马/启发性补充）**；研究标签：`personalized memory` `temporal validity` `memory consolidation`
- 证据范围：阅读全文；本地 PDF：[2609.36457.pdf](./2609.36457.pdf)

## 1. 做了什么

发现 memory writer 会把“我正在开一辆 Peugeot”压成“用户开 Peugeot”，保留事实却抹掉仍在持续与否的时间形态；提出 LAPSE 进行成对测量。

## 2. 怎么做、实验如何设计

LAPSE 用仅在时态/体貌上不同的匹配用户陈述，分离 writer 存什么和 reader 如何使用。三类 writer 在 381 对中有 244 对只把 progressive flatten 成 simple present、从不反向；不对称在 11 个模型配置及 mem0、Graphiti、Letta 中出现。只改存储动词也会改变下游 reader 对事实持续性的判断和是否追问。

## 3. Conclusion

记忆压缩会系统性丢失“事实是否仍有效”的语言证据，进而让 personalized agent 过度行动而不澄清。

## 4. Future impact

这是 memory schema 的重要提醒：时间体貌、证据来源和有效期应作为一等字段，而不是被摘要成静态 user fact。

## 5. Critical thinking

这是低机构优先级但高启发性的黑马。LAPSE 为合成、英语、词汇中性刺激；下游 reader 实验也被作者标为 exploratory。需要真实多语言对话、显式时间戳/结构化 schema 对照，以及真实偏好变化的纵向错误率。

## 6. 可信度判断

**3.5/5。** 大量 matched pairs、多模型与三个现成系统使现象可信；但任务合成、语言单一、部分 frame 样本少，尚不能估计真实产品中的发生频率。
