# Beyond Repeated Sampling：学习可复用的概念搜索策略

- arXiv：[2609.26704](https://arxiv.org/abs/2609.26704)；[官方 PDF](https://arxiv.org/pdf/2609.26704)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Ismail Labiad 等；Meta FAIR、Université Paris-Saclay/LISN/Inria/CNRS、NYU Courant/CDS
- 机构优先级：S（顶级工业研究机构与高校；弱相关但具启发性）
- 研究标签：in-context guidance、test-time scaling、RL、reusable search policy

## 1. 做了什么

论文把推理探索从 token 级重复采样提升为语义级“概念/提示/策略”搜索：先生成多种解题概念，再让冻结的大模型按这些概念生成答案，并训练一个小模型成为可复用的搜索策略。

## 2. 怎么做、实验如何设计

作者先严格复现 GuidedSampling，发现原报告优势主要来自过弱的 repeated-sampling 参数；然后改为单条轨迹一次生成多个概念，并在困难题上比较同等答案 rollout 预算。最后用 GRPO 风格目标训练 Qwen2.5-7B concept generator，以冻结 Qwen2.5-32B 的下游成功率作为奖励；训练/测试使用 DeepMath 困难子集，并测试 Omni-MATH 2 与 Llama-3.3-70B 跨家族迁移。

## 3. 结论

强 repeated-sampling 基线会抹去旧 guided sampling 的优势，但新方案在困难子集恢复增益；训练后的 7B generator 将冻结 32B 的 pass@128 从 19.0% 提至 39.2%，并迁移到未训练过的 70B 模型。

## 4. Future impact

它提供一种“策略记忆”：把过去搜索经验压入小型概念生成器，通过上下文指导而非修改主模型。未来可扩展到 agent memory 中的经验选择、技能提示和跨任务 planning prior。

## 5. Critical thinking

优点是作者主动推翻弱基线并重建更公平的比较。风险是困难子集由同一 answer generator 的失败筛选，可能放大方法定制收益；128 rollouts 的奖励计算极昂贵，训练成本不能只看部署收益。概念轨迹的信用分配也很粗，弱概念可搭便车。建议在未筛选完整分布、不同 verifier、固定总 FLOPs、真实 agent 决策任务上验证，并比较检索历史策略实例而不是参数化 generator。

## 6. 可信度判断

- 评分：4/5
- 依据：阅读全文有大规模复现、强基线修正、跨规模/跨家族迁移及详细 protocol。
- 优点：机构强；基线审计严谨；机制清晰，结果幅度大。
- 局限：聚焦数学推理；筛选后的 hard set 与高 rollout 成本限制外推。

