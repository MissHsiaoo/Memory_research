# 13. SeOPD

- 论文：**SeOPD: Self-Evolving LLMs via Online Policy Distillation from Self-Generated Chain-of-Thought**
- arXiv：[2609.33181](https://arxiv.org/abs/2609.33181)；[官方 PDF](https://arxiv.org/pdf/2609.33181)
- 提交日期：2026-09-27；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：National University of Defense Technology、Peking University
- 机构优先级：**A｜强高校合作**
- 研究标签：self-evolving LLM、online policy distillation、CoT、internalization
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

SeOPD 让同一模型的 deep-thinking 模式充当 privileged-information teacher，把自生成 CoT 内的新信息蒸馏进 non-thinking 模式和共享参数，减少对人工标注与外部环境反馈的依赖。

## 2. 怎么做、实验如何设计

每轮先由深思模式生成 CoT，再由快思模式生成回答；CoT 为快思 token 提供在线监督，并加 CoT 正则。实验覆盖科学问答、工具使用、代码和留出任务，比较不同 privileged information、CoT 来源、教师质量与 fast-thinking 长度动态。

## 3. 结论

模型可把推理时才显现的信息重新内化到参数中，实现无需外部知识源的有限自提升，并同时改善快思和深思能力。

## 4. Future impact

它可作为 agent memory 的“从情景经验到参数记忆”路径，把高成本轨迹周期性蒸馏成低成本策略。

## 5. Critical thinking

最大疑问是信息是否真正新增：CoT 仍由模型已有参数产生，长期迭代可能放大偏差而非扩充知识。需要严格防止训练/评测泄漏，并做多代循环、事实校准和错误 CoT 注入实验；还应与简单 best-of-N 蒸馏按计算量公平比较。

## 6. 可信度判断

**3.9/5。** 多任务和多项机制分析支持短期收益；“self-evolving”在更长代际上的稳定性、知识新颖性与安全边界仍未充分建立。

