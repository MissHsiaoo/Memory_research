# 04 — On Trajectory-Aware Training for Masked Diffusion Language Models

- arXiv：[2609.37974](https://arxiv.org/abs/2609.37974)；[官方 PDF](https://arxiv.org/pdf/2609.37974)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Manuel Madeira 等；Apple、EPFL、Georgia Tech（两位作者工作完成于 Apple 实习期间）
- 机构优先级：**S**；研究标签：`diffusion LLM` `trajectory training` `BPTT`
- 证据范围：阅读全文；本地 PDF：[2609.37974.pdf](./2609.37974.pdf)

## 1. 做了什么

提出 PUMBA，让 masked diffusion LM 不再只在独立随机 mask 上训练，而沿自身解码策略产生的连续轨迹训练，并在步间传递连续状态。

## 2. 怎么做、实验如何设计

统一研究 trajectory policy、step-to-step carry 和 truncated BPTT 三个轴。TinyGSM 控制实验发现：严格贴合推理轨迹会局部过拟合，较松对齐更好；连续 carry 优于离散梯度估计；更长 BPTT 有利。扩展到 LLaDA-8B SFT 后，在匹配性能下 full-canvas 最多减少 22% NFE、block diffusion 最多减少 26%。

## 3. Conclusion

扩散 LM 的训练—推理错配不仅来自 mask 分布，也来自跨步信息被丢弃；适度轨迹对齐与跨步信用分配能改善性能—步数前沿。

## 4. Future impact

可能推动 diffusion LLM 从“换采样器”走向“为迭代生成专门训练”，并把 latent working state 与长期/递归记忆结合。

## 5. Critical thinking

论文最有价值的是发现“越对齐越好”并不成立。当前收益仍建立在 confidence-based policy、teacher forcing 和有限 carry 上；若错误 token 被不可逆提交，训练目标会变得不一致。建议验证跨采样策略迁移、真实 wall-clock/显存成本以及更长轨迹的梯度稳定性。

## 6. 可信度判断

**4.5/5。** 设计空间拆解清楚，含小规模机制实验和 8B 扩展。局限是训练额外成本与最终推理节省的盈亏平衡只做有限讨论，尚未覆盖更大模型和开放式生成质量。
