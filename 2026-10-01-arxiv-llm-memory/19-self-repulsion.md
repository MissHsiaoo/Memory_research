# 19 — Self-Repulsive Sampling for Diffusion Language Models

- arXiv：[2609.39560](https://arxiv.org/abs/2609.39560)；[官方 PDF](https://arxiv.org/pdf/2609.39560)；[本地 PDF](./2609.39560.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Michael Helcig、Martin Jaggi；ETH Zürich、EPFL
- 机构优先级：**A+，一流研究型高校**；研究标签：`diffusion LLM` `sampling` `diversity`
- 证据：已核读 PDF 方法和实验；数值为作者报告。

## 1. 做了什么

让并行 diffusion LM 采样路径相互“排斥”，避免多条路径太早承诺相同 token，从而增加有效答案覆盖。

## 2. 怎么做、实验如何设计

在每个去噪步骤惩罚其他路径已承诺同 token 的频次，不增加模型评估次数。LLaDA-8B-Instruct 上比较 greedy、自一致性及匹配模型评估预算的方案；GSM8K 使用 10 路、128 步时确定性方案报告 80.38%，greedy 为 70.17%；还在 MATH、TruthfulQA 测试，固定预算下相对自一致性改善随块大小改变。

## 3. Conclusion

diffusion LM 的并行路径可以协同覆盖不同解，而不仅是独立重复采样。

## 4. Future impact

对扩散式代理尤其重要：多条行动计划若共享失败早期承诺，多样性预算就被浪费。

## 5. Critical thinking

**推断：** 更多不同候选不一定使最终多数投票更准，过度排斥可能降低高概率正确解的重复确认。应测 pass@k 与 vote accuracy 的分离、非 LLaDA 模型和实际并行硬件延迟。

## 6. 可信度判断

**4/5。** 匹配模型评估预算和多任务测试较有力；模型家族有限，部署级收益尚待验证。
