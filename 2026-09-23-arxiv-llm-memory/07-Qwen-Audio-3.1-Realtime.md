# Qwen-Audio-3.1-Realtime：自演化环境与持久语音任务

- arXiv：[2609.25176](https://arxiv.org/abs/2609.25176)；[官方 PDF](https://arxiv.org/pdf/2609.25176)
- v1 提交日期：2026-09-21；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Alibaba Token Foundry、Alibaba Group
- 机构优先级：S（头部公司、直接关联 self-evolving agent）
- 研究标签：self-evolving environments、voice agent、persistent tasks、memory boundary

## 1. 做了什么

论文将实时语音助手分为 Think、Act、Speak/Coordinate 三层，使其能在连续会话中追踪变化的约束、使用工具并决定何时说话或保持沉默；另给出带显式 task/memory boundary 的 Voice Harness 原型。

## 2. 怎么做、实验如何设计

Think 使用 Core-Cocktail SFT、Multimodality 和 Multi-Teacher On-Policy Distillation；Act 构建包含工具、政策、数据库与任务的可执行环境，并通过验证和 rollout 让环境自演化，再用 dialogue/milestone/turn 多粒度反馈做 GRPO；Speak/Coordinate 学习交互政策。评测覆盖语音推理、多语理解、工具调用、半双工/全双工、安全与持久任务。

## 3. 结论

相对 3.0，半双工 τ-Voice 适配的总任务成功率由 78.4% 升至 82.0%；Full-Duplex-Bench v1.5 对背景语音的错误响应率由 73.0% 降至 13.0%。

## 4. Future impact

它把 agent memory 与执行状态、对话轮次和前后台任务协调绑定，适合研究“事件驱动记忆”：只有任务里程碑、约束变更和验证结果进入持久层。

## 5. Critical thinking

最有价值的是可执行环境的持续演化，而非单个语音模型指标。但报告中的 Voice Harness 采用 3.0 foreground，与 3.1 模型能力并非完全一体，需避免把系统结果归因给同一个组件。建议在跨天任务、interrupt/resume、用户偏好变更和错误工具反馈下测 memory consistency，并公开环境演化中被接受/拒绝的变化。

## 6. 可信度判断

- 评分：4/5
- 依据：20 页报告含训练框架、多类 benchmark 和显著行为指标；工业实现细节较多。
- 优点：任务贴近部署；把 self-evolving environment 与 agent action 联合训练。
- 局限：若干系统组件与模型版本耦合不清；训练数据不可公开复现。

