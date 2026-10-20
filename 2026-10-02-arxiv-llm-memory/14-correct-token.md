# 14 — Know When to Hold ’em: Correct-Token Retention in Uniform-State Diffusion Language Models

- arXiv：[2610.01275](https://arxiv.org/abs/2610.01275)；[官方 PDF](https://arxiv.org/pdf/2610.01275)；[本地 PDF](./2610.01275.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Mojtaba Nafez、James Henderson；EPFL、Idiap Research Institute
- 机构优先级：**A+，一流研究所与高校**；研究标签：`diffusion LLM` `token retention` `self-correction`
- 证据范围：核读 PDF 机制分析、实验；数字为作者报告。

## 1. 做了什么

发现能反复修改 token 的统一状态扩散 LM 也会不停破坏已经正确的 token，导致多样性和质量下降。

## 2. 怎么做、实验如何设计

对 DUO、UDLM、uniform-noise SEDD 做随机 token 破坏与 NELBO 分解，指出训练目标对保留干净 token 的奖励太弱。CTR-Reg 加一个针对未受扰动正确 token 的辅助损失，不改采样器。PDF 在六基准上报告干净 token 准确率平均 +26.5 个百分点，单步无谓修改从 512 位中的 173–270 位降至 3–11 位；三模型在五步生成时 perplexity 均减半以上。

## 3. Conclusion

有效自修正需要“改错”和“保对”同时成立；只提高纠错能力并不够。

## 4. Future impact

对 diffusion LM 的稳定长文本生成、工具调用答案保持和潜在状态更新都有启发。

## 5. Critical thinking

**推断：** 过强的保留损失可能压制必要的全局重写。应测大规模指令模型、长链推理、真实编辑任务、分布外错误模式，以及不同采样预算下的质量—多样性曲线。

## 6. 可信度判断

**4/5。** 三模型、六基准、机制诊断与训练消融相互支持；通用代理场景尚未覆盖。
