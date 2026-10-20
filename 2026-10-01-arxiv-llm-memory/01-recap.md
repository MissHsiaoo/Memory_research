# 01 — Persistent Context Graphs for Efficient Memory Compaction in LLM Agents（ReCAP）

- arXiv：[2609.40118](https://arxiv.org/abs/2609.40118)；[官方 PDF](https://arxiv.org/pdf/2609.40118)；[本地 PDF](./2609.40118.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间对应的 arXiv 新稿批次）
- 作者/机构（PDF 首页核验）：Jingbo Yang 等；University of California, Santa Barbara、Microsoft、University of Notre Dame
- 机构优先级：**S，Microsoft 与一流高校**；研究标签：`agent memory` `context compaction` `persistent graph`
- 证据：已核读 PDF 首页、方法、实验与结论；以下数值为作者报告。

## 1. 做了什么

把历史 attention 提供的重要性与消息依赖关系保存为持久 context graph，让新请求到来时可快速选择需要恢复的历史片段。

## 2. 怎么做、实验如何设计

ReCAP 在先前推理时记录 attention 派生的重要性分数和依赖边；新请求只需结合请求相关性遍历图，无额外模型调用。实验用 Qwen3-Coder 与 gpt-oss，在 SWE-Together 的 106 个任务和 Lost-in-Conversation 的 100 个代码实例上，与摘要压缩和完整历史比较。论文报告相对 Codex 默认摘要式压缩，估计的压缩及冷恢复延迟约降 95%；SWE-Together 每次调用历史上下文约减半，Lost-in-Conversation 代码任务相对完整历史提升 19.8/41.2 分。

## 3. Conclusion

历史注意力可以成为跨请求复用的轻量记忆索引，降低重新读入历史的成本，同时保留任务证据。

## 4. Future impact

这可能成为长周期 coding agent 的默认 memory layer，也让“过去重要”与“当前相关”在同一个可审计结构中结合。

## 5. Critical thinking

**推断：** attention 反映模型当时关注什么，不保证未来请求所需证据都被记录；错误依赖边会造成系统性漏召回。最该复现的是跨任务转向、长期缓存失效、低频关键约束，以及真实 wall-clock 而不只估计延迟。对 Codex 默认策略的比较也应锁定版本、模型和预算。

## 6. 可信度判断

**4/5。** 有两个交互代码基准、两个模型和端到端任务质量。主要局限是论文的 95% 为估计延迟，attention 指标的未来稳定性及外部独立复现尚未验证。
