# 01. Harness as a Language

- 论文：**Harness as a Language: A Minimalist Agent Framework With Maximal Expressivity**
- arXiv：[2609.26891](https://arxiv.org/abs/2609.26891)
- 提交日期：2026-09-22；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Zhening Li 等；MIT CSAIL，另有独立研究者
- 机构优先级：**S｜顶级高校实验室**
- 研究标签：agent harness、长期记忆、递归调用、continual self-improvement
- 本地 PDF：[2609.26891.pdf](./2609.26891.pdf)

## 1. 做了什么

提出极简 agent 框架 JAZ，把 `invoke` 视为由 LLM 在运行时实现的语言原语：模型可写任意代码、递归调用 `invoke`，且其输入和与代码环境的交互历史都作为变量暴露。论文的核心主张不是再造一个专用记忆模块，而是证明长期记忆、子代理编排和持续自改进可从足够强的计算基底中“涌现”。

## 2. 怎么做、实验如何设计

JAZ 通过 `__history__` 等变量让代理以程序方式读取、传递或检索完整历史，并允许顶层代理充当 meta-agent，修改下层 solver 的提示与技能。长期记忆实验使用 StuLife：1,284 个按学期顺序展开的任务，939 个可评分，其中 207 个需要跨越 50 个以上任务的远距离回忆；比较 CodeAct、CodeAct+subagents 和 Letta/MemGPT。持续自改进实验在 AppWorld test-challenge 的 417 个顺序任务上，与逐任务 CodeAct、CodeAct+subagents 和 ACE 比较，solver 使用 GPT-5.4 nano，meta-agent 使用 GPT-5.4，并报告多次独立运行的均值与标准误。JAZ 在 AppWorld 达到 74.2% TGC、51.1% SGC，均高于所列基线，同时成本低于昂贵的 ACE 反思-整理循环。

## 3. Conclusion

论文证据支持：把全部可见状态变成可编程变量，再提供递归 LLM 调用，足以覆盖若干通常由专用 memory/self-improvement harness 实现的能力；原始、可编程历史接口在精确检索和跨代传递上比固定搜索工具更灵活。

## 4. Future impact

可能推动 agent 系统从“堆叠专用组件”转向“通用语言原语 + 模型自行构造工作流”。对 memory system 的启发是：记忆 API 的可组合性和原始证据访问权，可能比预先固定的摘要、向量检索器或反思格式更重要。

## 5. Critical thinking

论文最有价值的部分是把 harness 的表达能力本身当作研究变量，并在真正长序列任务上验证。关键假设是强模型能够安全、稳定地编程管理自己的历史；一旦模型更弱、历史极大或代码环境受限，这一假设可能失效。与专用记忆系统相比，JAZ 把很多复杂性转移给模型和递归调用，未充分量化失败时的可诊断性、安全边界与最坏成本。建议复现实验加入等 token/等工具预算、较弱开源模型、百万级历史、恶意历史污染，以及“原始历史变量 vs 结构化索引”正交消融。

## 6. 可信度判断

**4/5。** 已阅读全文；实验任务真实且跨度大，比较对象和成本拆分较清楚，多次运行并报告误差。优点是范式清晰、实验直接打到长期记忆和自改进。局限是主要依赖 GPT-5.4 系列，部分优势可能来自模型能力而非原语本身，且缺少严格等资源的因果消融。
