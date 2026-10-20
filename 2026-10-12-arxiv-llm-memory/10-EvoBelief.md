# 10 EvoBelief：把环境记忆写成可证伪假设

- 论文：[arXiv:2610.12789](https://arxiv.org/abs/2610.12789) · [官方 PDF](https://arxiv.org/pdf/2610.12789) · [本地 PDF](2610.12789.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-08 提交。
- 作者：Janet Wang、Jiang Guo、Yi Xiang、Jiaqing Yuan、Mingwen Dong、Hideo Kobayashi、Shuaichen Chang、Chandan K. Reddy、Jiarong Jiang。机构：Tulane University、Amazon（PDF 首页核验）。
- 机构优先级：B（一线工业研究 + 高校，低于用户点名机构）；研究标签：self-evolving agent memory、world models、belief revision。

1. **做了什么｜论文证据：**提出 EvoBelief，把代理对环境的知识组织成带证据的、可被反例缩窄或废止的假设。
2. **怎么做、实验如何设计｜论文证据：**意外结果或决策关键未知触发假设生成；后续观察与受控实验进行独立验证，验证后才允许规则进入预测与规划。模型权重冻结；在静态动力学、隐藏漂移和科学发现等 4 个基准中与冻结世界模型等对照。
3. **结论｜论文证据：**ALFWorld 无 actor 侧转移记忆设置下，对匹配冻结模型的成功率提升分别为 23.9%/31.3%（Claude Haiku 4.5/GPT-5.4）；MiniGrid 可更新过时规则，DiscoveryWorld Reactor Lab 报告明显领先。不能把基准提升当作真实科学发现保证。
4. **未来影响｜我的推断：**将长期记忆从“压缩事实”提升为有证据链和适用范围的可修正规则，适合变化环境中的代理。
5. **Critical thinking｜我的推断：**验证实验可能代价高、具风险；论文亦指出文本环境较易观察转移，现实噪声需统计检验。建议研究预算约束下何时验证、何时仅保留情景记忆，并测错误规则传播率。
6. **可信度：4/5。**依据：检查了机制、四基准与作者局限；优点是明确可证伪/反例处理，局限是环境主要为文本与模拟任务。
