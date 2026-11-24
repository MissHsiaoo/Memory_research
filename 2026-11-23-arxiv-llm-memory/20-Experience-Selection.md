# 20. From Acting to Learning: Experience Selection toward Continually Learning Agents

- [arXiv 摘要](https://arxiv.org/abs/2611.27159) · [官方 PDF](https://arxiv.org/pdf/2611.27159) · [本地 PDF](pdfs/2611.27159.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Yan, Yaoyuan; Jie, Haoxiang; Heng, Zhiyou; Wang, Kailin; Li, Yumiao; Liu, Lifeng; Yan, Anwan。
- 机构：首页署名核验，Country Garden Services AI Lab、Omni AI。机构层级：C：黑马/启发性补充，机构优先级较低。
- 研究标签：continual learning；experience replay；gradient selection。
- 阅读依据：已下载并解析完整 21 页 PDF，目视核验首页；本评析重点核读 §3–7、表1及独立保留组复核/成本局限，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：成功经历不一定是最佳训练数据。研究在固定经验池中用优化器感知梯度打分选记录，再看微调后agent行为，而不是仅用任务成功或高NLL代理经验价值。

## 2. 怎么做、实验如何设计

ALFWorld文本环境两固定池，721/732行、去重418/508内容；Qwen3-4B-Instruct-2507、rank16 LoRA。全局规则各选256内容、重放三遍共768展示、192更新。梯度特征利用冻结Adam状态、四个warmup checkpoint和40条公开支持动作，对齐目标族梯度方向。九规则×两池×八初始化×两采样种子共288学生；同executor测128开发task groups，再冻结流程在128保留组复核。

## 3. 结论

论文证据：全局梯度选择在两池81.445%/73.193%，比同选择自由度随机高8.252/5.957个百分点，比high-NLL高4.102/4.053点；八个初始化的配对差均正。保留组等来源均值相对随机+7.03、高NLL+5.03。放松覆盖约束帮助梯度规则却伤害随机，说明选择范围与打分必须联合比较。

## 4. 未来影响

研究判断：适合作为记忆“写什么、重放什么”的训练型基线。与直接检索给LLM不同，它研究经验转成参数更新的边际效用，可与外部记忆读取目标组成多目标选择器。

## 5. Critical thinking

论文不是完整在线continual系统：固定池、两任务族、评测executor没有跨任务记忆。相同展示次数≠相同token/FLOP；作者长度匹配可行性控制未通过，不能排除长度等混杂。支持动作与特征warmup有成本，且不是总体显著性检验。建议在新任务流上固定总算力与token，评测旧任务遗忘和未来收益，比较随机/高NLL/梯度/多样性组合。

## 6. 可信度判断

4/5。作为较低机构优先级的少量补充，入选理由是完整交叉种子、对齐全局选择自由度、冻结复核及诚实报告失败控制。结论限于这些固定池和面板，不声称普适在线持续学习优势。

