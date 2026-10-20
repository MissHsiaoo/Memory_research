# Grow the Harness, Not the Context：把经验写进可执行控制器

- arXiv：[2609.26760](https://arxiv.org/abs/2609.26760)；[官方 PDF](https://arxiv.org/pdf/2609.26760)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Laizhen Li 等；中科院深圳先进技术研究院、中国科学院大学、深圳理工大学、澳门大学
- 机构优先级：A（强研究机构、直接相关）
- 研究标签：self-evolving agent、executable memory、harness optimization、continual learning

## 1. 做了什么

论文提出 Growing Harness：不让 agent 每次在上下文中重新推导重复控制逻辑，而是从失败反馈中持续修改共享 harness 代码，使经验成为低成本、可复用的可执行记忆。

## 2. 怎么做、实验如何设计

从 strategy-free scaffold 开始，记录函数级执行 DAG，将失败定位到有限代码面；optimizer 联合修复一个 failure window，编辑只允许落在 trace 涉及的函数/少量 helper；候选必须修复足够失败且通过 success-first held-out gate，否则回滚。实验覆盖 BrowseComp-Plus、WebArena-Verified，部署模型从 4B 到 120B，比较 Tool-Calling、Self-Ask、IRCoT、WebDreamer、AgentOccam，并做组件消融。

## 3. 结论

六个 benchmark×model 设置中五个平均成功率最高，第六低 0.7pp；相对 Tool-Calling，LLM calls 降 76.0–91.8%，推理成本降 74.4–98.6%。WebArena 在不同模型规模保持约 44.7–45.3%，而 Tool-Calling 的 4B 版本降至 6.7%。

## 4. Future impact

这是 self-evolving agent memory 的重要路线：把稳定策略编译进代码，把语义判断留给 LLM。长期看，agent memory 可能分为事件存储、文本经验和经测试的 executable policy 三层。

## 5. Critical thinking

最大的风险是 benchmark-specific program synthesis：held-out gate 只能阻止已知回归，无法保证新分布安全。代码增长会累积隐藏耦合、权限和安全漏洞。应加入真正时间顺序的长期任务、跨网站迁移、代码复杂度/攻击面、错误回滚恢复，以及与 skill library/retrieval memory 的等成本比较。

## 6. 可信度判断

- 评分：4/5
- 依据：全文有清晰算法、train/gate/test 分离、三种模型规模、成本和消融。
- 优点：直接命中 self-evolving memory；部署收益大；回滚机制务实。
- 局限：仅两个 agent domain；optimizer 依赖与代码增长风险仍需长期评估。

