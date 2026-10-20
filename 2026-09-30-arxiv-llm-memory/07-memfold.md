# 07 — MemFold: Learning Compact Soft Memory for Long-Context Personalization

- arXiv：[2609.36435](https://arxiv.org/abs/2609.36435)；[官方 PDF](https://arxiv.org/pdf/2609.36435)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Jingxuan Wu 等；UCSB、UNC Chapel Hill、Harvard、University of Wisconsin–Madison
- 机构优先级：**A+**；研究标签：`latent memory` `personalization` `on-policy optimization`
- 证据范围：阅读全文；本地 PDF：[2609.36435.pdf](./2609.36435.pdf)

## 1. 做了什么

把查询相关的文本记忆压成固定 K 个连续向量，并直接按这些向量支持的个性化行为优化，而非重构原文。

## 2. 怎么做、实验如何设计

读者在自身 rollout 上接收两种信号：任务结果的 group-relative reward，以及冻结文本记忆教师对学生已采样 token 的 confidence-gated on-policy distillation；教师不生成序列，推理时完全移除。三种 Qwen backbone 上在 PersonaMem-32K/128K 取得作者测得的最高准确率，并零目标域训练迁移到 PrefEval、LongMemEval。消融显示主要增益来自 reward，teacher signal 提供额外小幅提升；shuffle/null memory 干预验证模型确实使用实例记忆。

## 3. Conclusion

固定长度 latent memory 的关键不是表示压缩本身，而是用最终行为对压缩器/读者进行在策略优化。

## 4. Future impact

对 personalized assistant 很直接：记忆接口大小不随历史增长，同时可把“记得事实”和“按偏好行动”放进同一目标。

## 5. Critical thinking

soft memory 不可人工编辑、审计或精确删除，且 query-conditioned 压缩可能每个问题都需重新编码长历史。应报告端到端建库/查询成本，测试跨会话更新、反事实偏好删除、隐私攻击与向量漂移；也应和强文本压缩在等算力下比较，而不仅等 K/token 预算。

## 6. 可信度判断

**4.5/5。** 方法与用户需求高度贴合，跨数据集、三 backbone 和 memory intervention 都增强证据。限制是作者仍用“我们测得的最好”措辞，外部基线覆盖和长期在线更新没有完全闭环。
