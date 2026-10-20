# 12. Planned Test-Time Scaling

- 论文：**Planned Test-Time Scaling with Coordinated Reasoning Paths**
- arXiv：[2609.27374](https://arxiv.org/abs/2609.27374)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Xueqing Wu 等；UCLA、Amazon
- 机构优先级：**S｜顶级高校 + 顶级公司**
- 研究标签：test-time scaling、diverse reasoning、latent plan、弱相关但具启发性
- 本地 PDF：[2609.27374.pdf](./2609.27374.pdf)

## 1. 做了什么

指出独立重复采样会集中在相同高概率推理模式，浪费 test-time compute。PTTS 先联合规划 k 条互补解题路线，再让 executor 分别展开，等价于在“推理路径记忆/潜在计划空间”中显式分配覆盖度。

## 2. 怎么做、实验如何设计

PTTS-ZS 用现成 base model 一次生成多条 outline；PTTS-RL 用 GRPO 直接优化 planner 的 pass@k，并在训练时截断 executor 输出（4K vs 推理 10K）以降低 executor 挽救坏计划的干扰。实验用 Qwen3-1.7B/4B，在 MATH-500、AIME 2024/2025/2026、HMMT-Feb26 上每题最多 64 解。PTTS-ZS 相对 repeated sampling 的 pass@64 最高 +6.7 点，PTTS-RL 最高 +13.4 点；两种规模下 pass@32 已超过 repeated sampling 的 pass@64，并能迁移到未见 executor。

## 3. Conclusion

扩展采样预算的关键不是更多独立样本，而是协调覆盖互补 reasoning modes；planner 和 executor 解耦后，规划器还能作为可迁移插件。

## 4. Future impact

对 memory system 的启发是把历史策略当作“待覆盖的方案空间”，检索时主动多样化而非按相似度重复召回近同经验；也可用于 agent failure memory 的多路径回放。

## 5. Critical thinking

论文的 pass@k 目标和多样性分析匹配，结果有清晰机制解释。但所有主实验是可自动判分数学题，planner 增加一次调用，实际 wall-clock 与成本未充分展开；“多样”也可能带来大量无效分支。建议在开放工具任务、不可判分任务和固定美元/延迟预算下测试，并比较检索到的历史计划与新生成计划。

## 6. 可信度判断

**4/5。** 已阅读全文；跨规模、五 benchmark、迁移与消融证据较完整。任务类型与 pass@k verifier 假设限制外推。
