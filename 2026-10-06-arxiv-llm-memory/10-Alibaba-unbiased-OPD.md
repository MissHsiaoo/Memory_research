# 10｜Un-OPD：修正块扩散模型的 on-policy 蒸馏偏差

- 论文：[arXiv:2610.05373](https://arxiv.org/abs/2610.05373)｜[官方 PDF](https://arxiv.org/pdf/2610.05373)｜本地 `2610.05373.pdf`
- 正式公告：2026-10-06；首次提交：2026-10-04。
- 作者/机构（PDF 首页）：Zaiquan Yang 等；City University of Hong Kong、Alibaba Group、Beijing Institute of Technology、CUHK 等。机构优先级：S；标签：diffusion LLM、on-policy distillation；直接相关。

## 1. 做了什么

指出将自回归模型的 on-policy 蒸馏直接套到块扩散 LLM 会带来训练偏差，并提出更贴合块边界的 Un-OPD。

## 2. 怎么做、实验如何设计

方法结合块边界感知过滤、置信度再校准和 rollout 复用；PDF 在数学与代码任务上训练 SDAR-4B/1.7B 学生（块长 4/8），并用 TraDo-8B 教师对比蒸馏基线。作者报告在保持或提升效果的同时将训练墙钟时间约减半。

## 3. 结论

对于所测块扩散设置，校正样本选择与教师置信度比机械套用常规 OPD 更有效；其泛化到其他扩散架构仍待验证。

## 4. 未来影响（推断）

若扩散 LLM 成为常用底座，针对块级推理机制设计 post-training 会影响个性化微调和持续学习的成本。

## 5. Critical thinking

速度收益可能依赖具体教师、块长和采样器。建议固定总计算预算做跨块长、跨任务、跨教师比较，并报告校准误差、答案质量与失败样本，而不只看平均准确率。

## 6. 可信度：3/5

依据：已读 PDF 训练构造、数学/代码实验与消融。优点是针对扩散机制的具体偏差；局限是模型家族与任务范围仍窄。
