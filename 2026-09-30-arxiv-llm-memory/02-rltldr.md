# 02 — RLTL;DR: Self-improvement by Internalizing Self-generated Feedback

- arXiv：[2609.37633](https://arxiv.org/abs/2609.37633)；[官方 PDF](https://arxiv.org/pdf/2609.37633)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Michael Kirchhof 等；Apple
- 机构优先级：**S**；研究标签：`self-improvement` `agent memory` `RLVR` `insight internalization`
- 证据范围：阅读全文；本地 PDF：[2609.37633.pdf](./2609.37633.pdf)

## 1. 做了什么

针对 Pass@128=0、标准 RLVR 完全拿不到正奖励的任务，让模型把每次失败压成一条 TL;DR insight，并把这些自生成经验内化到参数中。

## 2. 怎么做、实验如何设计

失败 rollout 后向策略暴露 verifier 输出，顺序生成下一次尝试，并对 task→insight 反向传播。Qwen3.5-9B Thinking 在困难工具调用与代码任务上，标准 GRPO 只有 0–1% Pass@1；RLTL;DR 训练时带 insight 达 14–31%，评测时不带 insight 仍有 12–13%。仅用约 4k 个 task-insight 对做 SFT，几乎恢复完整 RLTL;DR/全 rollout SFT 的性能。

## 3. Conclusion

高层失败经验可以比完整轨迹更紧凑地成为训练信号，并跨越“没有成功样本就无法启动学习”的冷启动障碍。

## 4. Future impact

它把 episodic agent memory 连接到参数记忆：经验先以文本 insight 存在，再被蒸馏为无需检索的技能，可能显著降低长轨迹训练和经验库维护成本。

## 5. Critical thinking

关键依赖是 verifier 提供有诊断价值的特权信息；无高质量 verifier 时，自我总结可能把错误解释固化。论文自己也承认，独特性很强、可迁移规律很少的任务可能不适合 task-insight 学习。应补做错误 insight 注入、跨域负迁移、不同 verifier 噪声和“等 token/等计算预算”对照。

## 6. 可信度判断

**4.5/5。** 因果链较清楚，既有 RL 也有精简 SFT 消融，并验证评测时移除 insight。局限是领域集中于可验证工具/代码任务，机制解释仍是假说，距离开放式自演化 agent 尚有明显外推距离。
