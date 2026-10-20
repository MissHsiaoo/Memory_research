# 15. dQwen3.5: Hybrid-Attention Diffusion Language Models

- arXiv：[论文页面](https://arxiv.org/abs/2609.20751v1)｜[官方 PDF](https://arxiv.org/pdf/2609.20751v1)｜[本地 PDF](papers/15-dQwen3.5-2609.20751.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Anton Xue , Litu Rout , Aditya Akella , Adam Klivans , Sujay Sanghavi , Sanjay Shakkottai
- 机构：The University of Texas at Austin（不是因为底座 Qwen 就署名 Alibaba）。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜顶尖研究高校，直接相关
- 研究标签：diffusion LLM；hybrid attention；AR-to-DLM adaptation
- 入选理由：UT Austin 在仍保留因果循环层的 hybrid backbone 上构建 diffusion，挑战必须全双向化的工程假设。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

dQwen3.5 将包含 attention 与 Gated DeltaNet 层的 Qwen3.5 hybrid AR backbone 转成 diffusion model。作者只把原本约 25% 的 attention 层双向化，循环层继续因果运行，并移除 vision/MTP 部分。新颖点是无需把所有 recurrent 层改成双向，仍能形成有效的 any-order diffusion decoding。

## 2. 怎么做，实验如何设计

模型尺度 0.8B、2B、4B、9B，使用 50B/100B 额外 tokens，Nemotron 混合约 50% code、35% text、15% math；序列长 4,096、batch 512，最后五个 checkpoint 做权重平均。需要 token readout shift 与 BOS/mask/pad 处理。主干对照 hybrid 1.37B 与 full-attention 1.41B 不同 parent/tokenizer，bytes/token 为 4.05/4.18，续训样本次序亦有差别。实验观察训练损失、不同并行 NFE 及代码/数学/知识基准。

## 3. 结论

hybrid 达到同一损失平均/中位比较中约需要 2.21 倍更少 content tokens，但这不是墙钟训练加速，也不能完全归因于 hybrid 架构。2B 50B 条件在代码上能胜过部分 full-attention 3B/7B；数学并非同样强。9B 50B 在 7 项中的 6 项优于 100B，虽然后者训练损失更低。9B 50B 的 MMLU 74.57 高于 AR 69.85，GSM 74.98 却低于 AR 87.34，不能概括全面胜过原模型。

## 4. 未来影响

我的推断：hybrid 状态结构可为 diffusion 更经济的初始化，也提示 causal recurrent state 与非因果 attention 能分工。对 memory 研究，值得测试不同 recurrent/attention 比例是否改变长期信息保存与更新，但本文未建立持久会话记忆机制。底座来自 Qwen 不意味着工作出自 Alibaba，机构排序仍按首页 UT Austin。

## 5. Critical thinking

关键混杂是 parent、tokenizer、数据次序与 architecture 同时变化；达到相同 token-level loss 的比较也受分词影响。NFE 更少不等于真实 token/s 更快，各步可能处理整段序列。性能随额外训练下降说明 loss 不足以预测目标能力。建议在同一 parent、词表、数据顺序与总 FLOPs 下控制 hybrid 层比例/位置，并用实际延迟、重复种子及长程依赖测试。代码优势与数学劣势应分别研究，不把参数更小但单域更强当全面 scaling 结论。

## 6. 可信度判断

可信度 4/5：全文多尺度、50B/100B 对比及明确 hybrid 改造细节支持可行性。优点是对因果循环层限制给出务实处理与反常训练结果；局限是架构因果归因不完全受控、只有 base model、NFE 口径与真实速度分离。本次未下载全部模型训练，证据来自论文方法与结果。
