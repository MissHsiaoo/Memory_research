# 20｜理工大等：CoDR 用置信度漂移修正 diffusion LLM 的早期承诺

- 论文：[arXiv:2610.08833](https://arxiv.org/abs/2610.08833)｜[官方 PDF](https://arxiv.org/pdf/2610.08833)｜本地 `2610.08833.pdf`
- 正式公告：2026-10-08（cs.CL New submissions）；首次提交：2026-09-28 UTC，v1。虽然提交较早，今日官方 new 区段及 v1 已单独核验，并非旧版本更新。作者/机构（PDF 首页）：Yue Wu、Qinghe Zheng、Yu Zhang、Jian Huang；Hong Kong Polytechnic University、Southern University of Science and Technology。机构优先级：B（方法启发性补充）；标签：diffusion LLM、remasking、inference-time correction；直接相关。

## 1. 做了什么

Mask diffusion LLM 往往过早把一个 token 从 mask 变为固定值，随后上下文越来越完整却不再检查它。CoDR 以“提交时置信度与后来置信度的下降”检测可能错误的早期承诺，只重新 mask 并生成这些位置，不改模型参数或基础采样器。

## 2. 怎么做、实验如何设计

采用 k-partition probing，用少量额外前向传播估计全部已提交位置的置信度漂移，再按阈值选择性重生成。PDF 用 LLaDA-8B-Instruct 与 Dream-v0-Instruct-7B 两个开源骨干、三种基础 sampler、HumanEval/MBPP/MATH-500/GSM8K 四个零样本任务，报告 Pass@1；GSM8K 的 500 题子集用于阈值、分区和额外计算量消融，比较针对性 remasking 与仅增加采样计算。

## 3. 结论

作者报告全部模型–采样器组合的平均准确率均改善，多数单任务设置也改善，且比已有 remasking 方案需要更少前向次数。消融表明收益不是单纯多花算力；但幅度随生成长度与阈值变化，不能称作普适无代价提升。

## 4. 未来影响（推断）

Diffusion LLM 的生成可以把“已决定 token”看作可撤销暂存，而非永久事实；类似思想可启发 agent memory 中的试用期写入与后验信心再校准。

## 5. Critical thinking

模型置信度下降不一定表示 token 错，可能只是多个正确解之间概率重分布；反复 remask 还可能破坏长距离一致性。建议在固定墙钟时间与能耗预算下比较，并检验开放式写作、多轮对话、不同校准程度模型；关键还要报告被撤销的正确 token 比例和序列级稳定性。

## 6. 可信度：3/5

依据：已读 PDF 的四任务设置、消融设计与推断开销比较。优点是训练免费且对采样器可插拔；局限是只在两个骨干、四类短任务上测试，真实延迟和长文质量证据不足。
