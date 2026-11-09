# 02. BOXBOX: Recursive Harness Self-Improvement for Long-Running Performance Optimization

- arXiv：[摘要及版本](https://arxiv.org/abs/2611.09218)
- PDF：[官方原文](https://arxiv.org/pdf/2611.09218) · [仓库内原文](pdf/2611.09218.pdf)
- 公告批次：2026-11-09，官方 New submissions；北京时间日报日期：2026-11-09。
- 首次提交日期：2026/11/06；与公告日期分别记录，完整官方版本记录见文末。
- 作者：Tan, Yuhao；Jiang, Hanyun；Yang, Fangkai；Yao, Yuan；Chen, Taolue；Qiao, Bo；Kang, Yu；Wang, Lu；Zhao, Pu；Ma, Xiaoxing；Lin, Qingwei。
- 机构：首页已渲染并核验：Microsoft；南京大学；浙江大学；Birkbeck, University of London。
- 机构优先级：A1：用户优先产业机构合作。
- 研究标签：self-evolving agent；程序化经验；harness更新。
- 相关性：直接相关（含持续学习、扩散语言模型及个性化方向）。
- 阅读范围：完整47页PDF已取得；重点阅读PDF物理页 1、4–10。未逐行审查所有附录、未复现实验。
- 证据边界：第3节是论文报告结果；第4节和第5节研究建议为评阅推断。

## 1. 做了什么

将任务执行中累积的经验转为可热更新的agent harness：代理自行决定何时暂停审查，修改提示、工具、技能及执行逻辑，再保留当前执行上下文继续工作。配套PERFRACE软件性能优化基准。

## 2. 怎么做、实验如何设计

100个真实项目分40训练、10验证、50测试，测试每题3次、每次4小时，任务优化与harness修改共享预算。比较冻结harness、离线Harness Evolution、外部Harness Scaling。内核负责验证、git版本、热加载和回滚；独立shadow verifier验证候选正确性与性能。14个测试任务消融固定30分钟审查和受限编辑范围。

## 3. 结论

表1四小时speedup为1.702，对比最强HS的1.539及冻结的1.442。表1平均模型成本16.43美元，低于冻结23.22但高于HS12.98；不能写成对所有基线都更便宜。表2完整系统1.584，对比无自主触发1.508、无完整编辑1.349。审查时间中位占2.1%，模型成本占13.8%。

## 4. 未来影响

评阅推断：程序化记忆不仅是检索经验文本，还可改变未来处理经验的流程。其版本化、验证、回滚机制适合迁移到自演化记忆写入器。

## 5. Critical thinking

收益主要来自同一长任务的在线适配，未证明能跨任务永久迁移。性能优化高度依赖可执行验证器；即使shadow验证也不能完全排除过拟合或安全退化。建议冻结模型/总预算，分别限制仅记忆策略、仅工具、仅提示修改，测下一任务迁移和错误规则回滚，另核算离线优化成本。

## 6. 可信度判断

4/5。依据：正文预算、隔离验证、50题重复运行、14题消融明确。局限：任务域与主模型有限；图1和表1成本有小幅舍入差异，本评析采用表1；安全边界不是形式保证。

## 官方提交与版本记录

Submission history From: Yuhao Tan [ view email ] [v1] Fri, 6 Nov 2026 09:36:00 UTC (1,363 KB)
