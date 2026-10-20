# 11 — FastGuide: Accelerating Reward Guidance for Diffusion LLMs

- arXiv：[2609.36202](https://arxiv.org/abs/2609.36202)；[官方 PDF](https://arxiv.org/pdf/2609.36202)
- v1 提交：2026-09-28；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Darshan Thaker、Lachlan Ewen MacDonald、René Vidal；University of Pennsylvania
- 机构优先级：**A+**；研究标签：`diffusion LLM` `reward guidance` `decoding efficiency`
- 证据范围：阅读全文；本地 PDF：[2609.36202.pdf](./2609.36202.pdf)

## 1. 做了什么

加速 masked diffusion LM 的梯度 reward guidance，把一次 reward backward 的引导复用于同一解码步的多个 token。

## 2. 怎么做、实验如何设计

FastGuide 在每个 diffusion step 内采用混合并行/自回归解码：缓存 guidance，逐 token 提交候选，同时用 KV cache 与稀疏 attention 重算分布；低置信候选延后。三类 reward benchmark 中，相对 sequential reward-guided decoding 最多 4.4× 加速，生成质量相近。

## 3. Conclusion

reward guidance 可跨 token 摊销，但并行提交会放大 token 不兼容；稀疏重算与自适应推迟能缓解这一矛盾。

## 4. Future impact

可使 diffusion LLM 的安全、偏好和任务奖励在推理时更可用，并与个性化 reward model 结合形成无需重训的用户定制。

## 5. Critical thinking

4.4× 是对特定顺序引导基线的上限结果，真实优势依赖 reward model 成本、候选置信校准和 kernel 实现。应报告全系统延迟/显存、不同输出长度和 guidance 强度下的 Pareto 曲线，并测试 reward hacking 与稀疏近似偏差。

## 6. 可信度判断

**4/5。** 机制解释和三个 reward 任务支持主要结论，训练免费增强实用性。局限是模型/硬件覆盖、绝对吞吐和独立复现尚不足以确认普遍 4.4×。
