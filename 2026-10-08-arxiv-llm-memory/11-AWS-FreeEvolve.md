# 11｜AWS：FreeEvolve，让演化流程本身从经验中学习

- 论文：[arXiv:2610.09197](https://arxiv.org/abs/2610.09197)｜[官方 PDF](https://arxiv.org/pdf/2610.09197)｜本地 `2610.09197.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-06 UTC，v1。作者/机构（PDF 首页）：Lecheng Kong、Like Hui、Nikos Kanakaris、Prithwish Jana、Sahika Genc、Narayanan Sadagopan；AWS AI Labs、Georgia Institute of Technology。机构优先级：A+；标签：self-evolving agent、meta-evolution、skill memory；直接相关。

## 1. 做了什么

已有 agent evolver 会自动修改提示、技能和工作流，但何时测试、投入多少预算、选哪个候选仍由人预先写死。FreeEvolve 把这套“演化流程”本身表达为可编辑 skill，使 agent 根据经验学习更好的搜索策略。

## 2. 怎么做、实验如何设计

环境仅指定目标 agent、评估器、任务、数据与资源上限；演化器自行决定试哪些任务、复核哪些改动、何时分支或停止。Meta-evolution 在多个新目标 agent 上评价候选 evolution skill，选出的技能冻结后迁移使用。PDF 在 τ³-bench、ARC-AGI-2/3、Terminal-Bench 2.1 上比较手工固定循环、仅有自主权但未 meta-evolve 的 seed skill，以及学得的技能；关注 held-out 主指标与跨环境迁移。

## 3. 结论

论文报告四环境的主要 held-out 指标平均提升 13.6 点，与手工设计 evolver 相当或更好；meta-evolved skill 在新 agent 上比 seed skill 多约 6.9 点。结果说明“如何改进”可部分成为经验资产，而不仅“改进后的提示”是资产。

## 4. 未来影响（推断）

自演化记忆系统可把写入、清理、回归验证与预算分配策略视作可学习的 meta-skill；在不同用户或任务上迁移时，策略本身需要 held-out 检验。

## 5. Critical thinking

关键假设是任务评估器能代表真正长期目标；如果验证器有漏洞，自主选择何时/怎样测可能更容易利用漏洞。相对固定循环的创新是决策顺序和预算适应性，但需要审计实际 token 与试验次数。建议在不可预见的任务流上运行更长周期，加入防止数据窥探的独立评审、性能回滚和总成本上限。

## 6. 可信度：3/5

依据：核查 PDF 的演化流程图、四环境设置与迁移实验。优点是区分 autonomy 与 meta-learned policy 的效应；局限是 benchmark/评估器与预算设定可能塑造收益，真实长期开环部署和可复现成本仍待验证。
