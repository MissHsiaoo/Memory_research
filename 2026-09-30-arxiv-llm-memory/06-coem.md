# 06 — CoEM: Commit-on-Evidence Memory

- arXiv：[2609.36935](https://arxiv.org/abs/2609.36935)；[官方 PDF](https://arxiv.org/pdf/2609.36935)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Jingguang Li 等；KAIST、University of Macau、MIT
- 机构优先级：**A+**；研究标签：`long-context` `recurrent memory` `RL`
- 证据范围：阅读全文；本地 PDF：[2609.36935.pdf](./2609.36935.pdf)

## 1. 做了什么

解决流式长上下文中过早压缩的问题：证据先以原文进入 bounded pending set，等后续信息揭示其价值后再提交成记忆事实。

## 2. 怎么做、实验如何设计

策略对 pending excerpt 执行 promote/retain/discard；冻结 NLI verifier 只接受有原文支持的事实；训练同时使用 step-level evidence reward 与最终答案 reward。三项基准、两种 Qwen3.5 模型上均优于同预算 memory agent；6,400 文档时 Qwen3.5-9B 提高 10.4–11.4 F1，128-chunk 证据间隔时 4B 提高 25.3 分。固定延迟提交比自适应策略低 3.2/3.9 F1。

## 3. Conclusion

长上下文记忆不仅要学“记什么”，还必须学“何时可以安全压缩”。

## 4. Future impact

pending/committed 双层记忆是适合 agent 的通用设计，可迁移到代码仓库、科研证据综合和多 agent 消息整合。

## 5. Critical thinking

冻结 verifier 把“有出处”与“真的正确/足够”混在一起；NLI 在数字、代码和跨段隐含关系上可能失真。应测试 verifier 错误传播、pending 集合被对抗性文本塞满、跨域迁移，以及保留原文带来的隐私/存储代价。

## 6. 可信度判断

**4.5/5。** 超长文档和大证据间隔实验直接击中假设，组件消融较强。局限是模型和任务类型仍较集中，真实性依赖自动 verifier，外部复现尚待出现。
