# 15 — Eternal Sunshine of the Spotless Mind: Systematically Erasing LLM’s Memories

- arXiv：[2609.36414](https://arxiv.org/abs/2609.36414)；[官方 PDF](https://arxiv.org/pdf/2609.36414)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Olga Ohrimenko；The University of Melbourne
- 机构优先级：**A**；研究标签：`memory deletion` `provenance` `privacy`
- 证据范围：阅读全文；本地 PDF：[2609.36414.pdf](./2609.36414.pdf)

## 1. 做了什么

指出删除含敏感事实的原消息不够，因为后续消息可能已派生、重述该事实；提出带 provenance graph 的 DeLLM 删除整条影响链。

## 2. 怎么做、实验如何设计

DeLLM 作为用户与 LLM 间代理，外部存储消息、按查询动态取上下文，并记录每条派生消息依赖哪些来源。删除时移除命中消息及依赖闭包。实验比较有完整记忆、无记忆和 DeLLM，报告删除率与保留数据效用的权衡，并在多种 API 模型/数据设置下验证。

## 3. Conclusion

memory deletion 的正确性应包含内容及其派生影响，而不是数据库层面的单条删除。

## 4. Future impact

对个性化记忆的“可撤回权”、审计和合规是基础设施级启发；provenance 还能支持重新生成摘要和影响分析。

## 5. Critical thinking

系统只能追踪它记录到的显式消息依赖，无法删除模型参数、外部工具日志或遗漏的隐性影响。自然语言删除请求也存在匹配歧义，论文建议用户确认。后续应做 prompt injection 下的未授权删除、跨工具 provenance、部分句子级删除和形式化 non-interference 测试。

## 6. 可信度判断

**4/5。** 问题定义准确，provenance 方案可审计，实验证明删除—效用权衡。局限是单作者预印本、依赖追踪正确性假设强，距离端到端法律意义上的“遗忘”仍远。
