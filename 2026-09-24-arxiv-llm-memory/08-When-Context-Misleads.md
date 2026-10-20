# 08. When Context Misleads

- 论文：**When Context Misleads: In-context Learning with Jurisdiction in Large Language Models**
- arXiv：[2609.27603](https://arxiv.org/abs/2609.27603)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Pei-lin Li 等；清华大学、华中科技大学
- 机构优先级：**S｜顶级高校**
- 研究标签：in-context learning、context authority、robustness、post-training
- 本地 PDF：[2609.27603.pdf](./2609.27603.pdf)

## 1. 做了什么

指出 ICL 不只要学会“从示例抽取规则”，还要判断该上下文是否有权支配当前问题。论文构建 FakeContextBench，并提出 J-ICL，通过适用/不适用 jurisdiction 对比训练模型抵抗连贯但无授权的伪上下文。

## 2. 怎么做、实验如何设计

FakeContextBench 含七领域的伪科学规则，区分 Reality answer 与 Context answer。J-ICL 使用 query-only causal LM objective，联合标准正例、匹配的 J+/J− 对和 J−/J− 对，让模型同时学规则归纳与适用范围。比较 Base、MetaICL、Symbol Tuning，在 Qwen3 4B/8B/14B、Llama-3.1-8B 上评估 ICLEval 与 Reality Rate。J-ICL 在全部设置上 ICLEval 最高；相对 Base，Reality Rate 在 Qwen3-8B、14B、Llama-8B 分别 +6.44、+12.75、+22.83 点。还做 3,500 例改写和语义 cue 冲突测试。

## 3. Conclusion

规模增大和常规 ICL post-training 不会自动带来 authority discrimination，甚至可能增强“盲从示例”；显式 jurisdiction 监督可在不牺牲标准 ICL 的情况下缓解。

## 4. Future impact

对 memory/RAG 系统很关键：被检索到的记忆并不天然有权限覆盖世界知识、系统规则或最新用户意图。未来记忆条目应携带来源、有效期、作用域和授权等级。

## 5. Critical thinking

论文把“相关性”与“管辖权”分离，这是很有启发的概念贡献。FakeContextBench 的 scope cue 仍显式且合成，现实中的权限通常隐含、冲突、多层级；结果也未证明模型学到抽象授权逻辑而非更复杂 cue。建议在系统/开发者/用户指令层级、时间过期记忆、跨用户来源冲突和工具证据中测试，并加入组合权限推理。

## 6. 可信度判断

**4/5。** 已阅读全文；跨模型、主任务与鲁棒性诊断充分，消融能支持训练成分。合成 benchmark 与显式 cue 限制外部有效性。
