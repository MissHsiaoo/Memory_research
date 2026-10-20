# 14. R3CON

- 论文：**Realize What Matters: Principled Context Representation for Large-Scale Reasoning**
- arXiv：[2609.27173](https://arxiv.org/abs/2609.27173)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Michael Theologitis 等；University of Washington
- 机构优先级：**S｜顶级研究型高校**
- 研究标签：context representation、retrieval memory、large-corpus reasoning、agent
- 本地 PDF：[2609.27173.pdf](./2609.27173.pdf)

## 1. 做了什么

从认知科学的 relevance realization 出发，提出 R3CON：表示应任务相关、可随推理反馈迭代，并允许表格、层级、图等灵活结构，而非固定 chunk 或固定图谱。代码 agent 在外部显式构造和探索这种表示。

## 2. 怎么做、实验如何设计

系统反复从文档集合提取与任务相关片段，根据当前理解继续筛选并组织结构，再由 coding agent 在结构上推理。实验在 CorpusQA（大规模、多文档分散证据）和 Loong（50K–250K 多文档）上，与 StructRAG、ReadAgent、HippoRAG2、CodeAgent、RLM 等九个基线比较，统一用 GPT-5.4-mini judge。相对最强基线，CorpusQA +19.88 点、Loong +8.42 点；Qwen3.5-4B/9B 的 R3CON 超过所有 35B 基线，35B-A3B 版本以约 3.7× 更低成本超过 Claude Code + Sonnet-5。

## 3. Conclusion

上下文如何被表示会限制下游推理上限；显式、任务条件化、可迭代的结构可减少对基础模型规模的依赖。

## 4. Future impact

可视为 memory compilation：不是直接检索“答案片段”，而是为每个任务生成可计算工作空间。未来可缓存相似任务的表示，形成可复用的中间记忆层。

## 5. Critical thinking

跨九基线和成本分析很强，但每个新 query 重建表示，成本和延迟可能限制在线助手；最终评分依赖单一 LLM judge，且部分基线因超大语料调整了原始参数，公平性仍可讨论。其表示约压到原文 1%，但开放网页规模尚未证明。建议用人工判分、等调用预算、动态语料更新和跨 query 表示复用测试。

## 6. 可信度判断

**4/5。** 已阅读全文；两个困难 benchmark、广泛基线和规模/成本实验支持结论。judge 依赖和每查询重建开销是主要保留。
