# Matryoshka Attribution：把内部表征与权重归因变成可学习排序

- arXiv：[2609.25518](https://arxiv.org/abs/2609.25518)；[官方 PDF](https://arxiv.org/pdf/2609.25518)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Aryaman Arora 等；Stanford University
- 机构优先级：S（顶级高校；弱相关但对 latent memory 很有启发）
- 研究标签：latent representation、mechanistic interpretability、weight attribution、model editing

## 1. 做了什么

论文提出 MAttr，把模型输出归因表述为寻找一组嵌套内部组件，使干预后的下游损失最小。它同时学习所有稀疏度下的统一组件排序，可用于定位表征电路和微调行为对应的权重变化。

## 2. 怎么做、实验如何设计

方法用可微 sigmoid top-k 掩码；每个训练 step 随机采样预算 k，对非 top-k 组件做 soft interchange intervention，再反传任务损失。作者在 Mechanistic Interpretability Benchmark 的 node/edge/MLP/attention/SAE 基上比较因果、梯度与 mask baselines；随后用 RL 目标定位 Llama-3.1-8B-Instruct 拒答行为相关的参数变化。

## 3. 结论

论文报告 MIB 官方榜首，secret-test 平均 5.6，而第二名 1.95；学习到的电路能跨相关任务迁移。把约 1% 权重恢复为 base model 状态可大幅移除拒答，同时维持能力。

## 4. Future impact

对 latent memory 的重要启发是：可把“哪些内部状态承载某段记忆”训练成跨容量嵌套排序，为选择性遗忘、局部更新和可审计个性化提供工具。

## 5. Critical thinking

优化干预后的任务损失得到的是“对目标足够的组件集合”，不等于唯一真实因果机制；分布外输入或组合行为可能依赖被忽略组件。1% 权重回滚也可能利用拒答评审器漏洞。建议跨 judge、跨 safety benchmark、因果反事实和长程记忆写入任务验证，并测试 attribution 排序在不同模型版本间是否稳定。

## 6. 可信度判断

- 评分：4/5
- 依据：58 页全文、公开 benchmark 排名、多种基与强 baseline、实际权重编辑案例。
- 优点：形式简洁；同时覆盖不同稀疏度；实验广且公开代码。
- 局限：归因仍依赖任务与干预定义；安全行为编辑的外部效度需更严格验证。

