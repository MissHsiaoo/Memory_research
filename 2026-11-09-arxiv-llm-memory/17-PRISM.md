# 17. PRISM: Primitive Routing via In-context Skill Mixing for Retentive VLA Adaptation

- arXiv：[摘要及版本](https://arxiv.org/abs/2611.08917)
- PDF：[官方原文](https://arxiv.org/pdf/2611.08917) · [仓库内原文](pdf/2611.08917.pdf)
- 公告批次：2026-11-09，官方 New submissions；北京时间日报日期：2026-11-09。
- 首次提交日期：2026/11/06；与公告日期分别记录，完整官方版本记录见文末。
- 作者：Tao, Jiachen；Zhang, Gengyu；Wang, Haoxuan；Liu, Bing；Yan, Yan。
- 机构：首页已渲染并核验：University of Illinois Chicago。
- 机构优先级：A3：研究型高校专项相关工作。
- 研究标签：continual learning；参数技能记忆；VLA组合。
- 相关性：直接相关（含持续学习、扩散语言模型及个性化方向）。
- 阅读范围：完整19页PDF已取得；重点阅读PDF物理页 1、4–6、8–9。未逐行审查所有附录、未复现实验。
- 证据边界：第3节是论文报告结果；第4节和第5节研究建议为评阅推断。

## 1. 做了什么

将原子技能保存为独立冻结LoRA primitive，再以可训练残差和分块router组合，缓解学组合任务时遗忘旧动作技能。

## 2. 怎么做、实验如何设计

RoboCasa-365中28原子、4组合任务；primitive rank32、组合残差rank10，阶段二560回放episode加415组合episode。原子每任务20评测、组合100；原子测试用one-hot路由，组合用语言视觉prefix条件路由。监督标签来自任务条件和动作事件的确定性oracle；虽然primitive冻结，视觉/语言LoRA及共享动作模块仍更新。另有PIPER小规模真实实验。

## 3. 结论

原子成功56.43%、组合20.0%，对照两阶段LoRA17.86/17.50，回放基线49.82/10.25。说明结构化技能库改善保留与组合，但组合绝对成功率仍低。参数保持原样不是行为严格不变。

## 4. 未来影响

评阅推断：可把可复用技能作为参数记忆单元，研究如何在多目标/多阶段任务中路由，而不是每任务都重训整个策略。

## 5. Critical thinking

原子测试的任务身份路由和组合的oracle训练标签提供额外监督；共享模块更新仍可能导致旧技能失效。建议加入无任务ID、阶段边界噪声、未见组合，比较等参数/等回放预算并给出技能数增长时路由与存储成本。

## 6. 可信度判断

4/5。依据：阶段训练、保留/组合指标和实际机器人验证。局限：仅4组合任务、oracle监督、原子与组合路由条件不同；不视为完全解决灾难遗忘。

## 官方提交与版本记录

Submission history From: Jiachen Tao [ view email ] [v1] Fri, 6 Nov 2026 03:00:06 UTC (6,422 KB)
