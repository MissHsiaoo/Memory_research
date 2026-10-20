# 18 — Principled Thoughts for Latent Recursive LLM Systems

- arXiv：[2609.36159](https://arxiv.org/abs/2609.36159)；[官方 PDF](https://arxiv.org/pdf/2609.36159)
- v1 提交：2026-09-28；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Fahd Seddik、Fatemeh Fard；FARD Lab, University of British Columbia Okanagan
- 机构优先级：**A**；研究标签：`latent reasoning` `recursive LLM` `latent communication`
- 证据范围：阅读全文；本地 PDF：[2609.36159.pdf](./2609.36159.pdf)

## 1. 做了什么

指出只监督最终答案的交叉熵会让 latent thought 出现替换信息损失、无关信息占用、不同问题碰撞和不确定性丢失，并提出 REST 辅助目标。

## 2. 怎么做、实验如何设计

把 causality、minimality、separability、stability 四项有效表示性质变为可微 loss，加入最终答案 CE，不改架构且推理不加参数。在单 agent 递归和多 agent latent communication 上，覆盖数学、科学、医学、代码七项基准；同数据/计算/latent budget 下，准确率最高 +7.5 个百分点，最终答案收敛提高 30%，并用 latent probe/解码分析支持表示改善。

## 3. Conclusion

答案级监督不足以约束连续“思维”；直接监督表示性质可同时改善正确率与可解释性。

## 4. Future impact

对 latent memory 和 agent-to-agent hidden-state 通信尤其重要：未来系统可能需要像训练数据库状态一样训练“中间记忆”的结构性质。

## 5. Critical thinking

四个性质的代理 loss 是否真正对应语义有效性仍需检验，probe 可读性也不等于因果使用。作者未穷举权重组合，只训练 outer link、冻结 base/inner link。应做等超参搜索对照、任务外迁移与对抗 collision 测试。

## 6. 可信度判断

**4/5。** 理论失败模式、表示诊断与七基准一致，贡献清晰。局限是机构层级不如头部实验室、训练设置受限，最大增益可能依赖特定 loss 权重。
