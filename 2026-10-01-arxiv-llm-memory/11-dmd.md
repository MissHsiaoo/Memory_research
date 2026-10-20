# 11 — Distribution Matching Distillation for Continuous Diffusion Language Models

- arXiv：[2609.40235](https://arxiv.org/abs/2609.40235)；[官方 PDF](https://arxiv.org/pdf/2609.40235)；[本地 PDF](./2609.40235.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Paul Le Van Kiem 等；Inria/PSL、Cohere、École Polytechnique
- 机构优先级：**S，头部模型公司与一流实验室**；研究标签：`diffusion LLM` `distillation` `sampling efficiency`
- 证据：已核读 PDF 方法与实验；数值为作者报告。

## 1. 做了什么

用分布匹配蒸馏减少连续扩散语言模型的去噪步数，探索低计算成本下的生成质量。

## 2. 怎么做、实验如何设计

比较基于路径梯度的 Simplex-DMD 和基于 categorical REINFORCE、密度比的 Reinforce-DMD，以反向 KL 训练学生分布。OpenWebText 上生成 1024-token 文本，报告固定生成熵/函数评估次数的 perplexity：Simplex-DMD 在 4 次 NFE 时为 45.6，Reinforce-DMD 在 256 次 NFE 时为 14.9；相应相对优势是作者按匹配设置给出的，不可跨两方法直接比较。

## 3. Conclusion

分布匹配能把连续 diffusion LM 的多步生成压缩，但不同梯度估计器在低步数和最终质量间取舍明显。

## 4. Future impact

若能迁移到指令和 agent 场景，可降低 diffusion LLM 工具代理的延迟门槛。

## 5. Critical thinking

**推断：** OWT perplexity 不能代表长程推理、指令遵循和闭环代理行为。应在相同总训练计算与相同生成熵下比较更强自回归/扩散基线，报告教师模型和辅助模型的全部成本。

## 6. 可信度判断

**4/5。** 两种梯度方案、匹配计算预算和定量生成指标较严谨；单一文本域及蒸馏依赖限制结论外推。
