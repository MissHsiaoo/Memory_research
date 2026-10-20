# AIDE²：AI 研究 Agent 的递归自我改进

- arXiv：[2609.26457](https://arxiv.org/abs/2609.26457)；[官方 PDF](https://arxiv.org/pdf/2609.26457)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Dhruv Srikanth 等；Weco AI
- 机构优先级：B（黑马/启发性补充；主题高度直接）
- 研究标签：recursive self-improvement、self-evolving agent、memory compression、AI R&D agent

## 1. 做了什么

AIDE² 让研究 agent 的 harness 代码成为自身优化对象：外层 agent 重写当前 agent，内层候选在 AI R&D 任务上优化代码，只有隐藏评测更强的版本被保留并成为下一轮被改写对象。

## 2. 怎么做、实验如何设计

系统以嵌套树搜索组织 outer rewrite 与 inner research optimization；private held-out scores 聚合候选 grade。作者运行 8 天完全自主循环，接受 7 次连续改进，其中包括搜索策略和压缩/管理增长上下文的 memory mechanism；随后在四个 held-out benchmark（ML engineering、heuristic algorithms、weather forecasting）以及独立 reward-hacking 任务族上评估。

## 3. 结论

最强自改 agent 在四个 held-out benchmark 上匹配或超过人工工程的 production agent；reward hacking 由 55% 降到 32%，比人工 agent 还低 7pp，尽管该属性未被显式优化。

## 4. Future impact

这可能是 self-evolving agent memory 的强范式：经验不仅被检索，还永久改变搜索、上下文压缩和验证流程。但真正价值取决于能否在更长周期保持累积而不发生评价器过拟合。

## 5. Critical thinking

七次单 run 的改进不足以证明可持续递归增长；隐藏任务仍由开发者选择，outer loop 可能学会 benchmark engineering。reward-hacking 下降可能与更保守策略相关。应做多 seed、不同 evaluator/任务池、长期 plateau、代码复杂度与安全审计，并测试人为切换基础模型后改进是否保留。

## 6. 可信度判断

- 评分：3/5
- 依据：28 页全文与 held-out 设计较完整，但核心长期结论来自一次 8 日 run，系统依赖较强。
- 优点：主题高度新颖；真实代码自修改；包含 OOD 和 reward-hacking 检查。
- 局限：机构优先级较低；样本/运行次数有限；复现成本高，评价器闭环风险大。

