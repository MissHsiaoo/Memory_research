# 03. MemAgent

- 论文：**MemAgent: Learning to Manage Heterogeneous Memory Providers for LLM Agents**
- arXiv：[2609.32521](https://arxiv.org/abs/2609.32521)；[官方 PDF](https://arxiv.org/pdf/2609.32521)
- 提交日期：2026-09-26；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Tsinghua University、Tencent
- 机构优先级：**S｜指定重点工业机构 + 顶级高校**
- 研究标签：agent memory、memory routing、heterogeneous providers、working memory
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

MemAgent 不再寻找“唯一最佳”的记忆表示，而是把 13 种 memory 方法视为异构 provider，由独立 memory agent 决定检索谁、执行中是否注入短期记忆，以及任务后把经验写到哪里。

## 2. 怎么做、实验如何设计

Begin 阶段并行探测各 provider 的实际内容，In 阶段按需门控工作记忆，End 阶段选择性多路写入。训练通过强制探索、任务正确性、LLM judge 归因和后续复用奖励合成监督。GAIA、WebWalkerQA、xBench-DS 上平均准确率提升 10.0%，步骤减少 12%，路由开销低于 0.3%。

## 3. 结论

不同记忆表示具有稳定但互补的归纳偏置；memory system 的核心问题之一是按任务和阶段进行路由，而不是继续堆一个更复杂的统一存储。

## 4. Future impact

这为“memory mixture-of-experts”提供了可操作框架，未来可将个性化画像、情景记忆、技能库和原始证据统一到同一控制器下。

## 5. Critical thinking

贡献的价值在于统一比较 13 个 provider，并显式覆盖读、用、写三个阶段。弱点是强制探索成本很高，LLM judge 可能把相关性误当因果贡献；provider 的实现质量也会影响路由结论。建议加入新 provider 零样本接入、memory poisoning、跨模型迁移与同等总成本消融。

## 6. 可信度判断

**4.5/5。** 全文细节、三 benchmark、消融和效率数据都较完整。局限是训练监督部分依赖模型裁判，长期在线稳定性仍需真实连续部署验证。

