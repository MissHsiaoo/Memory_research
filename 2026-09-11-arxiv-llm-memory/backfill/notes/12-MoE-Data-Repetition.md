# 12. MoE-Data-Repetition

Data Scarcity and Model Sparsity: Mixtures-of-Experts Overfit More to Repeated Data

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11917v1](https://arxiv.org/abs/2609.11917v1) · [官方 PDF](https://arxiv.org/pdf/2609.11917v1) · [本地 PDF](../papers/12-MoE-Data-Repetition.pdf)
- 首次提交：2026-09-10T17:57:33Z（UTC，与公告日不是同一概念）。
- 作者：Atindra Jha, Margaret Li, Jure Leskovec, Percy Liang, Luke Zettlemoyer
- 机构：Stanford、University of Washington Allen School（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：相邻启发｜continual training / 记忆过拟合
- 原文定位：§3、附录 A/B，PDF 第 3 页起。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

系统研究稀疏 MoE 在有限数据反复训练下是否比 dense 模型更容易过拟合。

## 2. 怎么做的，实验怎么做

固定总训练 tokens 和 active 参数，改变 unique tokens、重复次数、专家数量与粒度；检查 dropout、masking 等正则，并追踪专家路由稳定与专门化。

实验与结果：80M、200M、1B active，最高约 8.5B total；web/code/science/Wikipedia 单域和混合，重复率从 1 到 1,024 等。MoE 常在 4 次重复开始受损，约 32 次后输给 dense；强 masking 可在 64 次以上重复仍优于 dense，但达不到全独特数据水平。训练集按固定随机排列嵌套，评估 held-out CE 和下游任务。

## 3. Conclusion

总参数与数据稀缺的交互值得重视；active-parameter compute matching 不能自动保证相同过拟合风险。

## 4. Future impact

用户个性化数据少、反复 replay 多，给每用户增加专家可能扩大记忆能力，也可能更快记死小样本。

## 5. Critical thinking：优点、问题与可验证拓展

优点是预算控制、架构与数据维度系统扫描及随机种子敏感性。局限：这里固定总曝光时增加重复意味着减少独特数据，不能叫重复本身的纯效应；路由稳定与过拟合相关不等于完整因果链。建议固定 unique data 比较不同停止点，并测试逐用户专家、共享专家和 dense adapter 的留出用户表现。可信度 4/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**4/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

