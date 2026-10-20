# 05 Apple CDLM：连续扩散语言模型的设计空间

- 论文：[arXiv:2610.13834](https://arxiv.org/abs/2610.13834) · [官方 PDF](https://arxiv.org/pdf/2610.13834) · [本地 PDF](2610.13834.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Oscar Davis、Daan Roos、Alice Bizeul、Amitis Shidani、Victor Turrisi、Louis Béthune、Pierre Ablin、Marco Cuturi。机构：Apple、University of Oxford、University of Amsterdam（PDF 首页核验）。
- 机构优先级：A（Apple + 一流高校）；研究标签：diffusion LLM、self-conditioning、embedding geometry。

1. **做了什么｜论文证据：**系统研究连续扩散语言模型的自条件化与嵌入几何，并提出更省前向计算的 DoubleCat 和结合离散揭示的 SemiCat。
2. **怎么做、实验如何设计｜论文证据：**把自条件化作用区分为训练/推理状态错配和 token 可辨识性；用双层插值、离散 reveal 及嵌入空间对照实验检验这些机制，报告 TinyGSM 与 1.7B 规模下多个似然/生成评测。
3. **结论｜论文证据：**SemiCat 在 TinyGSM 取得文中报告的 49.94%，1.7B 设置下在六项似然评测中的四项优于所比离散扩散模型；该结果不能推广成全面超越自回归 LLM。
4. **未来影响｜我的推断：**CDLM 的训练目标与状态表示可能比单纯增加采样步数更值得优化。
5. **Critical thinking｜我的推断：**核心假设是研究用评测足以反映开放生成质量；不同方法的调参、步数、FLOPs/实际延迟不完全等价。建议跨同等训练预算、采样质量与真实硬件吞吐做联合 Pareto 复现。
6. **可信度：4/5。**依据：核查了机制分析、1.7B 对照与结果/结论；优点是多项机制消融，局限是规模和任务覆盖不足以支持通用部署结论。
