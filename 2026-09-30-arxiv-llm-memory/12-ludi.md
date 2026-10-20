# 12 — Less Uniform Discrete Diffusion is More Powerful and Scalable

- arXiv：[2609.35817](https://arxiv.org/abs/2609.35817)；[官方 PDF](https://arxiv.org/pdf/2609.35817)
- v1 提交：2026-09-21；正式公告批次：2026-09-30（北京时间；首次公告，不按提交日归档）
- 作者/机构（PDF 首页核验）：Kaibo Wang 等；HKUST、Huawei Foundation Model Department
- 机构优先级：**A+**；研究标签：`uniform diffusion LM` `few-step generation` `scaling`
- 证据范围：阅读全文；本地 PDF：[2609.35817.pdf](./2609.35817.pdf)

## 1. 做了什么

指出 uniform diffusion LM 难扩展的核心不是 uniform prior，而是训练目标过度均匀与采样时条件/目标混淆，并提出 LUDI。

## 2. 怎么做、实验如何设计

用 less-uniform loss 把每次逆转移更直接地指向 clean token，并加 per-token time embedding 提供各位置腐化强度。先在 170M/1B 控制预训练，再把 7B 自回归模型继续训练为 LUDI-7B；复杂推理上相对 AR 达到约 3 token/step，并与 masked diffusion 基线有竞争力。

## 3. Conclusion

UDLM 的大规模潜力仍未耗尽；减少目标层面的均匀性可兼得更干净监督和更少步采样。

## 4. Future impact

为 diffusion LLM 增加第三条可扩展路线，也可能利用 uniform corruption 的修改/自纠错特性做可编辑记忆与并行推理。

## 5. Critical thinking

7B 模型由 AR checkpoint 转换，可能继承 AR 归纳偏置，因此尚不能证明“原生大规模 UDLM”更优；作者也承认自纠错能力未完全激活。需从头预训练、等训练 FLOPs 与等 wall-clock 对照，并单独衡量生成质量、步数和每步实际计算。

## 6. 可信度判断

**4/5。** 小规模机制实验加 7B 扩展形成较完整证据链。结论中的“scalable”仍主要是一次 7B 转换证明，且 3 token/step 不等同 3× 速度。
