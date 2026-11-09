# 20. From LoRA to Language: Recovering Skill Documents from Adapters

- arXiv：[摘要及版本](https://arxiv.org/abs/2611.09454)
- PDF：[官方原文](https://arxiv.org/pdf/2611.09454) · [仓库内原文](pdf/2611.09454.pdf)
- 公告批次：2026-11-09，官方 New submissions；北京时间日报日期：2026-11-09。
- 首次提交日期：2026/11/06；与公告日期分别记录，完整官方版本记录见文末。
- 作者：Swadha, Saranya Dintakurthy；Shekar, Pavan C；Jain, Arpit；Krishnan, Aswanth。
- 机构：首页已渲染并核验：QpiAI, Bengaluru, India。
- 机构优先级：B：低机构优先级黑马/启发性补充。
- 研究标签：参数记忆可读化；技能文档；LoRA；黑马。
- 相关性：直接相关（含持续学习、扩散语言模型及个性化方向）。
- 阅读范围：完整27页PDF已取得；重点阅读PDF物理页 1、4–12重点方法与实验。未逐行审查所有附录、未复现实验。
- 证据边界：第3节是论文报告结果；第4节和第5节研究建议为评阅推断。

## 1. 做了什么

研究能否把LoRA中保存的技能写回可读文档。区分直接读权重与运行适配模型后写作，并区分训练时看过文档的adapter和只通过行为训练的adapter。

## 2. 怎么做、实验如何设计

训练文档约1.1万、37技能，近重复另隔离；外部41技能、323技能依赖任务。Executing Writer利用适配模型计算，设置wrong-adapter等对照。另在SkillsBench筛选4个无技能失败而参考解成功任务，每臂8次，换模型作为agent。后续行为读取agent可对比基础/适配模型动作，在开发游戏上写≤800词技能；本轮重点阅读到该实验设计，不将摘要后续数值当完整复核结果。

## 3. 结论

文档承载adapter的关键指令恢复约39–44%，wrong adapter仅1.3–1.5%；rank64外部任务恢复原文增益85–91%。行为训练adapter本身可恢复47–58%任务增益，但训练writer恢复文档仅1–2%，其文本任务增益约-4至1%。SkillsBench原文85%测试通过份额，重构82.5–83.1%，区间较宽。

## 4. 未来影响

评阅推断：低机构优先级但概念价值突出，可连接参数记忆与跨模型可迁移的文本技能，支持审计、版本差异与人类编辑。

## 5. Critical thinking

恢复可用技能不等于找回唯一原文；文档承载训练具有特殊信息通路。writer也可能用自身先验补全，需wrong-adapter/隐藏任务/纯任务文本对照。建议从纯行为训练开始，用不可从常识猜出的技能，跨骨干测试，并同时测无依据内容、忠实度与行为效用。4个筛选任务不能代表普遍agent迁移。

## 6. 可信度判断

3/5。依据：文档/行为训练区分及wrong-adapter对照清楚，已读主要结果与agent实验设计。局限：最强恢复结果依赖文档承载adapter、小样本agent试验，后续全部行为agent附录未逐项核验。

## 官方提交与版本记录

Submission history From: Pavan C Shekar [ view email ] [v1] Fri, 6 Nov 2026 13:26:43 UTC (882 KB)
