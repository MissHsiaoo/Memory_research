# 01. SCLATE

- 论文：**SCLATE: A Substrate for Continual-Learning Agent Training and Evaluation**
- arXiv：[2609.32391](https://arxiv.org/abs/2609.32391)；[官方 PDF](https://arxiv.org/pdf/2609.32391)
- 提交日期：2026-09-26；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Apple
- 机构优先级：**S｜指定重点工业研究机构**
- 研究标签：continual agent、experience substrate、agent training、memory harness
- 证据范围：已阅读官方 arXiv 全文 HTML；本地 PDF 因 arxiv.org HTTPS 连接超时未能保存。

## 1. 做了什么

SCLATE 把持续学习 agent 最容易被忽略的基础设施问题单独抽象出来：如何在多任务、跨环境和不同时间语义下，可靠地记录、回放并比较 agent 的经验。它提供统一事件调度器与混合模拟时钟，使 memory、harness 和训练算法能在可重复的时间线上运行。

## 2. 怎么做、实验如何设计

系统统一组织环境事件、工具调用、经验日志和学习更新，并覆盖 7 个 benchmark、10 组 harness/memory 配置和多种模型。论文还用 SCLATE 训练 Qwen3.5-4B：文件操作行数降低 6.8 倍，SWE-bench Verified 提升 16.7 点；在 MetaClaw 设置中最高提升 11.8 点。实验同时考察训练与评测，而非只给一个 memory 检索准确率。

## 3. 结论

持续学习 agent 的上限不仅取决于记忆算法，也受经验时间线、可复现回放和训练接口影响；统一 substrate 能显著减少系统噪声并让学习收益更可信。

## 4. Future impact

它可能成为研究 self-evolving agent memory 的公共“实验操作系统”，尤其适合比较不同写入、压缩、回放和策略更新方法。

## 5. Critical thinking

最强之处是把基础设施变量显式化，并在多个 benchmark 和真实代码任务上验证。风险是 substrate 本身可能隐含 Apple 的工程假设；若不同系统的异步工具、真实墙钟和权限模型差异很大，统一时间语义未必无损。建议复现时加入跨实现一致性测试、故障注入，以及等训练预算下“仅换 substrate”的严格消融。

## 6. 可信度判断

**4.5/5。** 机构强、全文和实验覆盖充分，报告了明确效率与任务收益。局限是系统论文的增益容易由多项工程变化共同贡献，因果归因仍需更细消融。

