# Evo-Denoiser：393 参数的扩散 LLM 调度器

- arXiv：[2609.26052](https://arxiv.org/abs/2609.26052)；[官方 PDF](https://arxiv.org/pdf/2609.26052)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Zijian Zhao 等；HKUST、Huawei Noah’s Ark Lab、HK PolyU、HKUST(GZ)
- 机构优先级：S（头部企业实验室+强校、直接相关）
- 研究标签：diffusion LLM、denoising scheduler、evolution strategy、attention

## 1. 做了什么

论文把 dLLM 推理时的去噪顺序视为上下文相关的调度问题，指出 confidence heuristic 会因 EOS overflow 与 proximal bias 失败，并提出只有 393 个参数的进化式调度器。

## 2. 怎么做、实验如何设计

作者分析 attention 对 `[MASK]`/`[EOS]` 等无效 token 的异常关注，将多种 confidence 与有效 attention 特征和 context mean-field embedding 动态融合；参数由 CMA-ES 优化，而非反传训练。实验在 LLaDA 与 Dream、四个 reasoning/planning benchmark 上比较手工 heuristic、block-AR 与近期调度方法，并做特征/失败模式分析。

## 3. 结论

论文报告在两个 backbone 的四项任务上稳定超过强基线，强调极低参数量即可学到按上下文变化的去噪策略。

## 4. Future impact

这说明 dLLM 性能瓶颈可能更多来自 inference policy 而非 backbone；未来可把调度器做成跨模型、跨任务的可迁移“解码记忆”。

## 5. Critical thinking

CMA-ES 在小参数空间合理，但若 fitness 直接来自目标 benchmark，可能形成 task-specific schedule。应报告跨 benchmark 零调参迁移、真实 wall-clock、不同长度/批量和硬件结果；还需比较 393 参数模型与等复杂度线性规则，确认收益来自进化搜索还是特征工程。

## 6. 可信度判断

- 评分：4/5
- 依据：阅读全文含明确失败机制、两种 backbone、四个任务和开源代码。
- 优点：参数效率极高；机制与方法对应；机构和实验均强。
- 局限：任务范围仍偏 reasoning；跨模型迁移与系统吞吐证据需加强。

