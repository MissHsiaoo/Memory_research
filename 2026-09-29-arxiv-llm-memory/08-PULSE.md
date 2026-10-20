# 08. PULSE

- 论文：**PULSE: Identifying Demonstration-Utility Features with Sparse Autoencoders**
- arXiv：[2609.32469](https://arxiv.org/abs/2609.32469)；[官方 PDF](https://arxiv.org/pdf/2609.32469)
- 提交日期：2026-09-26；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Southeast University、UCLA、University of Texas at Austin
- 机构优先级：**A｜强高校合作**
- 研究标签：in-context learning、SAE、demonstration selection、mechanistic interpretability
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

PULSE 用稀疏自编码器寻找“哪些内部特征使某组 demonstrations 对当前模型有用”，把 ICL 选择从外部相似度推进到模型内部效用信号。

## 2. 怎么做、实验如何设计

方法采样效用不同的 demo set 对，寻找激活差异与效用差异一致的 SAE feature，得到稀疏定位向量；既用于完整集合排序，也作为 pool-scale 检索的特征 mask。分类、生成、推理任务上相对最强基线提升约 2–3 accuracy、0.6–0.9 BLEU-4 和 3.2 EM，并报告消融、跨数据集迁移与 seed 稳定性。

## 3. 结论

示例效用不仅由 query-demo 语义关系决定，也与目标模型内部可激活的稀疏机制有关。

## 4. Future impact

可把 ICL memory retrieval 变为 model-aware 检索，并为“为什么这段记忆有用”提供可干预解释。

## 5. Critical thinking

SAE feature 与效用相关并不自动证明它是因果机制；发现集标签也可能把任务特征泄露进 retriever。最关键的后续实验是对高权重 feature 做激活/抑制干预，并检验不同模型、层和 SAE 字典间能否迁移。

## 6. 可信度判断

**4/5。** 任务覆盖、强基线和稳定性分析充分；目前因果性证据仍弱于“可预测性”证据，且 SAE 训练成本未完全反映在检索开销中。

