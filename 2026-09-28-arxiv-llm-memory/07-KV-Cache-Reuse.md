# 07. Evaluating KV Cache Reuse

- arXiv：[2609.31415](https://arxiv.org/abs/2609.31415)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.LG new）
- 作者/机构（PDF 首页核验）：Samuel Cestola 等；Huawei Technologies、ETH Zurich
- 机构优先级：**S/A｜重点工业机构 + 顶级高校**
- 研究标签：context memory、KV cache、RAG、evaluation
- 本地 PDF：[2609.31415.pdf](./2609.31415.pdf)

## 1. 做了什么

审计位置无关 KV cache reuse 的评测，指出常用 LongBench-QA 会因 baseline 本来答错、参数记忆泄漏或二选一猜测而虚高；提出“meaningful subset”过滤规则与可控生成器 Boxoffice。

## 2. 怎么做、实验如何设计

在 MuSiQue、HotpotQA、2WikiMQA 上，用 Llama3.1-8B、Qwen3-8B、Mistral-7B 和部分 Qwen3-32B，复现 CacheBlend、FusionRAG、LMCache、CacheCraft。过滤 full-prefill F1=0、无上下文也能答、低信息答案后，许多方法 normalized F1 明显下降；MuSiQue 中 baseline-zero 翻转可贡献多达 42% 的表面 F1。Boxoffice 用角色可控的重复 chunk 生成 warm-cache 场景：角色对齐时 LM norm-F1 ≥0.97，角色翻转时三个模型均降至 0，暴露现有数据缺少的 stale-cache 动态。

## 3. Conclusion

现有 headline accuracy 常没有隔离“复用造成的损失”；先定义可观察的因果子集，再比较 cache 方法，结论会显著改变。query-driven token selection 有帮助，但仍无法恢复 full prefill。

## 4. Future impact

对 memory system 很关键：缓存/摘要复用评测也应排除“不读记忆也能答”的样本，并显式控制记忆写入时角色与查询时角色的漂移。

## 5. Critical thinking

论文价值主要在 measurement。过滤规则提高因果解释性，却可能删掉实际业务中也重要的正则化副作用；Boxoffice 的合成角色结构是否代表真实 RAG 仍待验证。建议同时报告全流量效用与 meaningful-subset fidelity，并加入真实日志中的时间漂移和跨用户缓存污染。

## 6. 可信度判断

**4.5/5。** 已阅读全文。多模型、多方法、合成机制对照和 10 个数据种子使结论稳健；局限是主要集中问答 RAG，尚未覆盖 agentic cache 与生成任务。
