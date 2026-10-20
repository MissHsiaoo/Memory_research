# 01 — Context Language Models

- arXiv：[2609.37725](https://arxiv.org/abs/2609.37725)；[官方 PDF](https://arxiv.org/pdf/2609.37725)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Rulin Shao 等；University of Washington、Meta Superintelligence Labs、MIT、Trillium Labs
- 机构优先级：**S**；研究标签：`context management` `agent memory` `online RL` `multi-agent`
- 证据范围：阅读全文；本地 PDF：[2609.37725.pdf](./2609.37725.pdf)

## 1. 做了什么

把上下文从被 harness 被动拼接的 token 串改造成模型可自由读写的“文件”。模型自己决定保留、删除和重写什么，并把同一接口推广到多个 agent 的并存上下文。

## 2. 怎么做、实验如何设计

先用现成模型零样本实现 CLM，再用自然语言 skill evolution 和在线 RL 学习上下文管理策略，并实现 Suffix Cache Reuse。覆盖 BrowseComp-Plus、12 小时 EdgeBench 和 24 小时多仓库 agent swarm；零样本 CLM 分别报告 +11.4% 准确率且少 21.5% FLOPs、+5 分且少 59% FLOPs、同计算量下提升幅度 +65%。在线 RL 使 Qwen3.5-9B 在 BrowseComp-Plus 上提升 47.6%，FLOPs 降 12%。

## 3. Conclusion

上下文管理可以成为模型的原生策略，而不必完全由外部规则控制；同时，它能承载参数化学习、技能演化和多 agent 共享状态。

## 4. Future impact

这可能把“memory system”从独立检索/压缩模块推进为模型动作空间的一部分，并为把成熟 harness 蒸馏进模型权重提供路径。

## 5. Critical thinking

最重要的创新不是文件语法，而是把 context mutation 变成可学习决策。风险也由此增加：模型可写上下文形成新的持久化 prompt-injection 与自我强化通道。建议复现实验加入恶意历史、错误自摘要、跨 agent 权限隔离，以及与同预算最强外部 memory controller 的盲测；还应分开统计“删得好”与“算得少”的贡献。

## 6. 可信度判断

**4.5/5。** 优点是机构强、任务跨度大、同时报告质量与计算量，并给出在线学习和系统优化。局限是主要证据仍由作者自建/新近基准与特定模型栈产生，安全性和长期错误累积尚未形成同等规模的反证实验。
