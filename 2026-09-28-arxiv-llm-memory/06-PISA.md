# 06. PISA

- 论文：**Block Sparse Attention with Log-Linear Complexity**
- arXiv：[2609.31093](https://arxiv.org/abs/2609.31093)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.LG new）
- 作者/机构（PDF 首页核验）：Bohao Tang 等；ByteDance Seed、上海交通大学、上海创智学院
- 机构优先级：**S｜重点工业研究机构**
- 研究标签：弱相关但具启发性、long context、sparse attention、retrieval memory
- 本地 PDF：[2609.31093.pdf](./2609.31093.pdf)

## 1. 做了什么

提出 PISA，用金字塔式 Top-K 把 block sparse attention 的块选择从二次复杂度降到 O(N log N)。它不是显式 agent memory，但直接影响长上下文与 retrieval-memory 的可扩展读取成本。

## 2. 怎么做、实验如何设计

先对 key 构造 O(log N) 层粗到细层级，在每层只对有限候选做 LogSumExp 评分并向下展开；配套 Triton kernel 融合路由，并让多个 query 复用 leaf key block。作者在 418M、1.47B、2.67B 三个规模上训练 100B 个 4K token，再继续训练 10B 个 16K token；对比 full attention、BSA、NSA、HiLS，评估 perplexity、常识、containment 和 RULER。PISA 在稀疏方法中三种规模均取得最高 containment 平均分，块选择在 4K–256K 上相对 BSA 提速约 2.86×–9.95×。

## 3. Conclusion

有限候选的层级检索可把“找哪些历史值得读”本身做成次二次过程，同时维持语言建模和常识能力；full attention 在部分任务仍更强。

## 4. Future impact

memory retriever 可借鉴同样的 coarse-to-fine index，把 episodic memory 的候选筛选和注意力内核统一，而非先用外部向量库再做全注意力。

## 5. Critical thinking

强点是算法、内核和大规模预训练共同验证。核心假设是层级 pooling 不会抹掉细粒度线索；needle/RULER 和 containment 仍比真实多轮 agent memory 简单。建议测试百万 token、频繁记忆更新、跨块冲突和 query-dependent 遗忘，并分离理论复杂度与真实端到端 latency。

## 6. 可信度判断

**4.5/5。** 已阅读全文。三规模、110B token 训练与硬件 benchmark 很强；但对个性化/agent memory 是基础设施级弱相关，不能直接推出记忆质量提升。
