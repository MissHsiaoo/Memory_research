# ClusterFewshot：语义覆盖与效用联合的 ICL 示例选择

- arXiv：[2609.25939](https://arxiv.org/abs/2609.25939)；[官方 PDF](https://arxiv.org/pdf/2609.25939)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Omri Bar Haim 等；Tel Aviv University
- 机构优先级：A（强校、直接相关）
- 研究标签：in-context learning、demonstration selection、DSPy、prompt optimization

## 1. 做了什么

ClusterFewshot 改进 LLM workflow 的 few-shot demo 选择：先按语义聚类保证覆盖，再用 held-out one-shot 效用给候选打分，替代随机或单指标排序。

## 2. 怎么做、实验如何设计

训练样本先做 embedding clustering，从各簇产生代表候选，再以 validation subset 的 one-shot 表现估计 utility，组成 few-shot set。方法被接入 DSPy 的 BootstrapFewShotRS、MIPROv2 与 BetterTogether，在 GSM8K、HotPotQA、Iris 等任务、不同模型规模/家族与 ReAct 设置测试；比较优化成本、平均准确率及采样策略。

## 3. 结论

论文报告相对 bootstrap baselines 在 prompt-only 与 prompt+weight optimization 中通常提高准确率，同时显著降低搜索成本；语义覆盖与效用评分均有贡献。

## 4. Future impact

对个性化 ICL 的启发是：用户历史示例不能只按相似度取最近邻，应同时优化行为覆盖与实际增益；可自然扩展为随反馈更新的 personal demo bank。

## 5. Critical thinking

validation utility 容易过拟合，且 one-shot 边际价值不保证在多示例组合中可加。聚类 embedding 也可能忽略标签/推理结构。建议加入组合价值、跨分布测试、相同总 LLM calls 下的 Bayesian/submodular baselines，以及长期 online personalization 场景。

## 6. 可信度判断

- 评分：3/5
- 依据：全文有方法和多设置，但摘要中缺少统一绝对数值，结论更多依赖多表综合。
- 优点：直接命中 ICL；易集成现有 workflow；同时考虑覆盖与效用。
- 局限：任务较小且部分基准偏传统；组合效应和跨域泛化仍不充分。

