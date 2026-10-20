# 10. ForkLeft

- 论文：**ForkLeft: Entropy-First Rollouts for Prefix-Aligned Autoregressive-to-Diffusion Distillation**
- arXiv：[2609.32448](https://arxiv.org/abs/2609.32448)；[官方 PDF](https://arxiv.org/pdf/2609.32448)
- 提交日期：2026-09-26；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：University of Melbourne、UC Davis、University of Hong Kong
- 机构优先级：**A｜强高校合作**
- 研究标签：diffusion LLM、distillation、reasoning、parallel decoding
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

ForkLeft 解决 AR teacher 与 diffusion student 条件结构不一致的问题：student 可看双向上下文，而 teacher 只能基于左前缀监督。

## 2. 怎么做、实验如何设计

训练时 student 先按高熵位置 rollout，暴露潜在分叉；随后固定 student 前缀，在相同前缀下调用 NTP teacher，并按答案正确性选择监督来源。推理仍使用原生 confidence-first 并行解码。Qwen3-30B-A3B teacher 下，Efficient-DLM-4B 在 10 个 benchmark 均提升，MATH500 从 72.6% 到 79.6%；500 次更新也迁移到 SDAR-4B。

## 3. 结论

dLLM 可以吸收 AR 推理知识而不放弃原生并行生成，但监督必须先对齐可见前缀和不确定位置。

## 4. Future impact

该训练接口可能成为强 AR 模型向小型 diffusion agent 迁移推理能力的通用路径。

## 5. Critical thinking

结果强，但 teacher 规模与训练成本不小；entropy-first rollout 是否只是在定位难 token，需要更直接机制验证。还应报告真实 wall-clock、长输出下并行收益，以及当 teacher 错误但 student 正确时路由是否会强化噪声。

## 6. 可信度判断

**4/5。** 十 benchmark、多 student 家族和详细训练语义增加可信度；代码尚待发布，复现成本和端到端速度收益仍需独立验证。

