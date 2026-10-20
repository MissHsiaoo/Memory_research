# SpeakerMem-R1：多人对话的双轨长期记忆

- arXiv：[2609.26780](https://arxiv.org/abs/2609.26780)；[官方 PDF](https://arxiv.org/pdf/2609.26780)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Haobo Zheng 等；浙江大学 CAD&CG 国家重点实验室
- 机构优先级：A（强校、直接相关）
- 研究标签：LLM memory system、multi-party memory、personalized/social memory、RL writer

## 1. 做了什么

论文针对多人长期对话中“谁说了什么、关于谁、群体共识是什么、状态何时改变”容易混淆的问题，提出 SpeakerMem-R1。它不是只做相关片段检索，而是同时保留可追溯原话与结构化状态，专门处理归属、关系和时间演化。

## 2. 怎么做、实验如何设计

系统维护两条记忆轨道：speaker-labeled verbatim messages，以及带 provenance 的 person/group-level derived states；查询时通过 Anchor–Separate–Resolve–Compose 按实体、事件和时间组合证据。Writer 使用 SpeakerLevenshtein 与 speaker-conditioned GRPO 训练。论文在 GroupMemBench、SocialMemBench、EverMemBench 和 LoCoMo 上评测，并在冻结查询/回答模块的 305 问控制实验中比较 SFT 与 RL writer；还做双轨、person/group view 消融。

## 3. 结论

PDF 报告三项多人记忆基准二值准确率为 47.9%、69.2%、61.9%，相对各自强基线提高 3.3、12.4、9.4 个百分点；RL writer 在控制实验中由 57.38% 提升到 68.20%。两类记忆和两种视图具有互补性。

## 4. Future impact

这类“原始证据轨 + 可更新状态轨”很适合做个性化助手、群聊代理和团队记忆。其价值在于把 personalization 从“用户画像字符串”推进到带来源、作用域和时间版本的可审计状态。

## 5. Critical thinking

直接证据支持结构化归属能改善多人记忆，但 benchmark 的问答准确率还不能证明真实部署中的写入稳定性。关键风险是 Writer 的一次错误会被提升为结构化事实；人物同名、讽刺、代述和权限边界也比基准更难。建议复现实验加入跨群身份冲突、恶意记忆注入、撤回/更正、不同 writer 模型迁移，并分别测写入错误、检索遗漏和答案推理错误。与普通 GraphRAG 的真正差异应通过固定检索预算、固定 reader 的端到端归因来验证。

## 6. 可信度判断

- 评分：4/5
- 依据：阅读全文可见明确系统分解、多个相关基准、冻结模块的控制实验与结构消融；代码链接公开。
- 优点：任务定义贴近多人个性化记忆；证据轨与状态轨的设计合理；量化结果充分。
- 局限：多数指标仍是离线 QA；真实长周期写入漂移、隐私治理与跨域迁移未被充分覆盖。

