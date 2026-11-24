# 18. EvoTER: Evolving Embodied Agents via Tool-Use Experience and Reflection

- [arXiv 摘要](https://arxiv.org/abs/2611.27797) · [官方 PDF](https://arxiv.org/pdf/2611.27797) · [本地 PDF](pdfs/2611.27797.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Zhou, Yingting; Zhou, Yuyin; Wang, Yongliang; Li, Haoran; Zhao, Dongbin。
- 机构：首页署名核验，Institute of Automation, Chinese Academy of Sciences（State Key Laboratory of Multimodal Artificial Intelligence Systems）；University of Chinese Academy of Sciences。机构层级：B：强研究型高校/实验室。
- 研究标签：procedural memory；skill library；validation-gated evolution。
- 阅读依据：已下载并解析完整 9 页 PDF，目视核验首页；本评析重点核读 §III–IV、表I、图2–3，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：把完整任务收益而不是局部修补成功作为技能库更新标准。Explorer收集经验、Diagnoser提出技能、Validator在新session比较整库，改进才保留。

## 2. 怎么做、实验如何设计

模型与普通工具在每个演进阶段固定，技能记录触发条件、工具组合、参数脚本、后置检查与恢复。模拟中停滞后Diagnoser可用特权信息，但候选与最终执行只用普通观测，禁止技能写死坐标或seed。RoboCasa365 Target50共18原子/16 composite-seen/16 composite-unseen任务，三轮演进；探索与验证seed分开，最终库冻结评测。主控制是同模型同工具的空技能库。真实Franka实验测试模拟初始化和继续演进。

## 3. 结论

论文证据：模拟整体SR从53.60到80.40，+26.80点；任务宏平均，三个子集均提高。外部方法结果来自各自原协议，不能当严格同条件比较。Composite-Unseen是相对VLA训练定义，其开发实例可能参与技能演进，不代表agent从未见过该任务类别。

## 4. 未来影响

研究判断：程序性记忆写入应有版本、完整任务回归测试和失败回退；独立session验证可减少诊断过程的临时状态泄漏。

## 5. Critical thinking

特权诊断即使不直接传给部署agent，仍是额外监督成本；多次用验证反馈修库可能对验证环境适配。真实任务次数有限。建议在相同诊断budget下禁用特权信息，测试真正任务类别留出和工具API变化；报告老技能退化、候选拒绝率与每次有效改进成本。

## 6. 可信度判断

4/5。空库同条件控制、明确冻结测试和特权隔离较扎实；跨方法外部比较与小规模真实机器人结论较弱，应分开看待。

