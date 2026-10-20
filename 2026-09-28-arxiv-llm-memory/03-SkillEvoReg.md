# 03. SkillEvoReg

- arXiv：[2609.30861](https://arxiv.org/abs/2609.30861)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.AI new）
- 作者/机构（PDF 首页核验）：Guanyu Nie 等；Huawei Noah’s Ark Lab
- 机构优先级：**S｜重点工业研究机构**
- 研究标签：self-evolving agent memory、skill library、continual learning
- 本地 PDF：[2609.30861.pdf](./2609.30861.pdf)

## 1. 做了什么

把外部 skill 的反复改写视为一个会过拟合和遗忘的持续学习过程，提出 SkillEvoReg，在不替换原有 skill evolver 的前提下，抑制技能库冗余膨胀和新更新破坏旧能力。

## 2. 怎么做、实验如何设计

三部分分别对应神经网络正则化的类比：skill dropout 在生成更新时扰动依赖；复杂度感知局部正则惩罚不必要的结构增长；causal counterexample validation 为每个候选更新构造可能回归的针对性反例。作者将其接入多种原生 evolver，在 SkillOpt、SkillEvolBench 与 ContinualSkillBench 上考察最终能力、跨阶段迁移、库字符数/结构复杂度以及更新级回归；还冻结阶段性技能库做独立评估，避免只用训练轨迹自证。

## 3. Conclusion

论文表明：更强的 skill updater 不能自动解决长期演化稳定性；显式正则化能在维持竞争力的同时控制技能状态增长，并发现仅看库大小或重复率看不到的行为回归。

## 4. Future impact

它可能成为 self-evolving agent 的“写入层”：每次 memory/skill update 都需要扰动鲁棒性、复杂度预算和反事实回归测试，类似模型参数训练中的正则化与验证集。

## 5. Critical thinking

创新点是把 skill evolution 从 prompt engineering 提升为可泛化的学习动力学问题。风险是反例仍由当前系统生成和判定，可能形成同源盲区；字符数并非真正认知复杂度；基准中的任务边界比开放世界清晰。建议引入隐藏任务族、跨模型执行器、人工红队反例和恶意 skill 更新，测量“少写但保留关键例外”的 Pareto 前沿。

## 6. 可信度判断

**4/5。** 已阅读全文。跨三个 benchmark、多个 skill-evolution 系统且保留原生 evolver，证据范围较好；局限是外部技能文本的规模仍远小于真实长期代理，CCV 的判定独立性有限。
