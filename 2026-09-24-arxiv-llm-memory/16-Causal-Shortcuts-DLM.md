# 16. Causal Shortcuts for DLMs

- 论文：**Towards Efficient Reasoning: Learning Causal Shortcuts for Diffusion Language Models**
- arXiv：[2609.28272](https://arxiv.org/abs/2609.28272)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Dian Jin 等；浙江大学、上海人工智能实验室
- 机构优先级：**A+｜一流高校 + 国家级实验室**
- 研究标签：diffusion LLM、causal shortcut、CMI、reasoning trajectory
- 本地 PDF：[2609.28272.pdf](./2609.28272.pdf)

## 1. 做了什么

把 diffusion LLM 的有效推理线索定义为覆盖完整序列、能引导正确轨迹的 causal shortcut，而非简单把高熵 token 当“重要 token”。提出 CSL 训练，让模型优先学习这些互补、弱局部依赖的 token 链。

## 2. 怎么做、实验如何设计

论文用 conditional mutual information 从完全 mask 序列逐步选择 token，形成覆盖序列的 shortcut；为降低 CMI 计算成本，训练 scoring model 近似排序，NDCG 达 0.92。基于 LLaDA-8B-Instruct 与 LLaDA-1.5，在 Math-CoT、OPC-SFT-Stage2 上训练，对七个数学 benchmark 及 HumanEval、MBPP 评估，并比较 DiBT、MGDM、Blockwise、DSFT、GIFT。CSL 相对 SFT 在七个数学任务平均 +1.92%，代码平均 +2.30%，MATH-500 最多 +4.20%，并更快降低熵。

## 3. Conclusion

随机 masking 的巨大探索空间可用结构化 shortcut 缩小；引导 token 的价值来自对正确轨迹的因果覆盖，而不只是局部不确定性。

## 4. Future impact

可把 shortcut 看作 diffusion LLM 的 latent reasoning memory：存储并优先激活跨位置的推理骨架。未来可与过程监督、检索到的解题策略和 test-time repair 结合。

## 5. Critical thinking

论文把 token importance 从 entropy 提升到 CMI，机制上合理。问题是 shortcut 提取依赖正确答案和近似 scorer，可能将训练集特定答案结构编码进模型；仅到 8B、数学/代码，且提升绝对值中等。建议跨模型/跨领域迁移、无 ground-truth 在线 shortcut、scorer 偏差和真实去噪延迟测试。

## 6. 可信度判断

**4/5。** 已阅读全文；两个 base model、九个任务、五类 SFT 变体和消融支持结果。规模和领域仍窄，CMI 的因果解释更接近有监督关联证据。
