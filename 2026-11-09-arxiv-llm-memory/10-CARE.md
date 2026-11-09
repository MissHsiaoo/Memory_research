# 10. Remembering Is Not Enough: Evaluating Timing and Omission in Longitudinal AI Mental Health Support

- arXiv：[摘要及版本](https://arxiv.org/abs/2611.08721)
- PDF：[官方原文](https://arxiv.org/pdf/2611.08721) · [仓库内原文](pdf/2611.08721.pdf)
- 公告批次：2026-11-09，官方 New submissions；北京时间日报日期：2026-11-09。
- 首次提交日期：2026/11/05；与公告日期分别记录，完整官方版本记录见文末。
- 作者：Min, Eli；Chandra, Mohit；Sawant, Aamogh；Tu, Mengting；Lin, Freya；Khan, Ridwan Shams；El-Yashruti, Reigna；Smith, Christopher L.；Kalinich, Mark；Torous, John；De Choudhury, Munmun。
- 机构：首页已渲染并核验：Georgia Institute of Technology；University of Virginia；Beth Israel Deaconess Medical Center。
- 机构优先级：A2：优先研究型高校/实验室合作。
- 研究标签：personalized memory；时机；遗漏；纵向评测。
- 相关性：直接相关（含持续学习、扩散语言模型及个性化方向）。
- 阅读范围：完整28页PDF已取得；重点阅读PDF物理页 1、5–7、9–12。未逐行审查所有附录、未复现实验。
- 证据边界：第3节是论文报告结果；第4节和第5节研究建议为评阅推断。

## 1. 做了什么

提出CARE评价框架，研究记忆型心理支持聊天系统能否在用户状态演变时给出合时宜的帮助，区分过早、滞后、有效/无效建议及遗漏。本文是评测研究，不是临床治疗效力证据。

## 2. 怎么做、实验如何设计

22位用户捐赠历史构成1584persona，三类危机与三类交流方式形成14256模拟，60会话、危机在第30会话。Qwen3-8B模拟persona、Gemma4-31B作助手，6144token记忆预算含事实与带日期摘要。人工检查事实忠实度83.6%、阶段82.5%；统计按22原始用户聚类，不能把全部模拟当独立真人。

## 3. 结论

匹配危机/无危机片段，建议对齐率.806对.851、过早率.074对.023。主动回访将过早率.208降到.149，焦虑情形遗漏.827降到.668；回访也可能改变用户表达，不能只看单指标。

## 4. 未来影响

评阅推断：长期个人记忆的正确使用应同时评价内容正确、时机适当和该行动时没有遗漏；CARE可启发非临床多目标助手的纵向评测设计。

## 5. Critical thinking

模拟用户及裁判可能共享偏差，22位真实历史来源限制人口代表性；persona误差会传播。没有充分的无记忆对照时不能把所有改善/失败归因于记忆。建议增设记忆开关、状态更新延迟与冲突记忆对照，并由专业人员盲审，不将模拟结果转为临床建议。

## 6. 可信度判断

3/5。依据：实际协议、人工验证、聚类分析和多维指标已读；优点是纵向与遗漏视角。局限：以模拟为主，非临床试验，生成误差与用户来源规模限制外推。

## 官方提交与版本记录

Submission history From: Elizabeth Min [ view email ] [v1] Thu, 5 Nov 2026 21:14:16 UTC (454 KB)
