# 15 Seq-Drifting：一步并行文本生成

- 论文：[arXiv:2610.12879](https://arxiv.org/abs/2610.12879) · [官方 PDF](https://arxiv.org/pdf/2610.12879) · [本地 PDF](2610.12879.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Jiayu Liu、Ruizhi Zhao、Tianyun Ji、Yee Whye Teh、Zhenya Huang、Ning Miao。机构：City University of Hong Kong、Shenzhen University、USTC、University of Oxford 等（PDF 首页脚注核验）。
- 机构优先级：B（一流高校联合）；研究标签：diffusion LLM、one-step generation、parallel decoding。

1. **做了什么｜论文证据：**提出 Seq-Drifting，学习从高斯噪声一次前向生成整段文本，而不执行多步去噪。
2. **怎么做、实验如何设计｜论文证据：**在连续 token 表示上构造随当前生成上下文变化的漂移场；吸引项将每位置指向多个合理 token 表示，排斥项抑制跨样本塌缩与序列内重复。评估 LM1B 无条件生成，并扩展至翻译、摘要、推理，与一步/少步及传统扩散方法比较。
3. **结论｜论文证据：**论文报告 LM1B 一步生成困惑度 36.01，并在条件生成任务显示可用性；只表明当前评测下的一步 operating point，不等于已经替代高质量多步模型。
4. **未来影响｜我的推断：**把条件分布的局部多峰性显式注入训练目标，可能缓解并行生成中的重复与坍缩。
5. **Critical thinking｜我的推断：**生成困惑度与人类可读性不完全一致；一步方案可能隐含更高训练成本或模型容量。建议统一参数量、训练 FLOPs、采样延迟与人工长文本评价，并测试罕见知识和多步推理。
6. **可信度：3/5。**依据：核查训练目标、多个生成任务和结论；优点是清晰的一步比较，局限是评估规模与真实吞吐/长程一致性仍有限。
