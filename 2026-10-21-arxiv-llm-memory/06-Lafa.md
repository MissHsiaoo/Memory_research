# 06. Large Flow Language Models

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.28559)；[官方 PDF](https://arxiv.org/pdf/2610.28559)；[仓库 PDF](pdfs/2610.28559.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Arnav Chavan , Chanhyuk Lee , Udbhav Bamba , Jaehoon Yoo , Seunghoon Hong , Aditi Raghunathan , Jinwoo Kim
- 机构（PDF 首页署名核验）：UC Berkeley；Amazon；KAIST；Carnegie Mellon University
- 机构优先级：P1A；主题相关性：直接相关；研究标签：flow language model；diffusion LLM；并行解码
- 阅读证据：正文§2–3、表1（PDF第4、6–8页）；首页。已获取完整 PDF（27页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

将预训练AR模型适配为分块连续流语言模型，同时保留AR预测与前缀缓存。

## 2. 怎么做、实验如何设计

【论文直接证据】块内双向、块间因果；每token时间条件，固定embedding范数只学习方向；联合AR交叉熵、去噪交叉熵和embedding误差。0.5B/7B/8B，9–27B适配token；6个指令/推理/代码基准，有同初始化、同数据预算基线；流映射蒸馏和自推测解码另作评估。

## 3. 结论

【论文直接证据】单token六基准均值7B为60.9，匹配AR-SFT58.4；8B63.1并未超过不同预算的Efficient-DLM63.5。少步流映射改善但仍落后多步流；更大块增加并行性也损失质量。

## 4. 未来影响

【阅读者推断，尚待验证】为潜在连续表示与生成推理的结合提供可缓存的工程路径，可考察记忆状态如何作为流条件。

## 5. Critical thinking

【阅读者评析与后续建议】不要混淆单token模式、自推测模式和真正少步流的质量。‘更少训练token’相对部分已发布模型不等于控制所有数据差异。8B使用Base而非Instruct，也影响归因。建议在同训练FLOPs、硬件、batch和输出长度下画质量–延迟Pareto曲线；长文本一致性需要另测。

## 6. 可信度判断

**4/5**（与机构优先级独立）。有匹配训练基线及明确推理协议，机制可信；跨论文预算与吞吐对比须保留条件，未进行独立复现。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
