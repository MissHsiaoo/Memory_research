# 15. OptionWorld: A Benchmark for Diagnosing Failures of LLMs as Long-Term Personal Assistants

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.28491)；[官方 PDF](https://arxiv.org/pdf/2610.28491)；[仓库 PDF](pdfs/2610.28491.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Ruoyu Zhang , Zhaocen Liu , Weiyi Tian , Melissa Feng , Shilong Liu
- 机构（PDF 首页署名核验）：University of British Columbia；University of Chicago；Princeton University；Independent Researcher
- 机构优先级：P1B；主题相关性：直接相关；研究标签：personal assistant；prospective memory；multi-goal evaluation
- 阅读证据：正文§3–4（PDF第4–6页）及Limitations；首页。已获取完整 PDF（31页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

用长期个人助理世界评测从信息获取、判断、及时干预到最终结果的完整链条，而非只问记住了什么。

## 2. 怎么做、实验如何设计

【论文直接证据】8个人工设计世界、每系统192目标；6系统×3次，144轨迹、3456目标实例。按允许行动期检查关键事实是否仍在最终输入，模型双评审加人工核验；5系统共用runner，Astra使用独立Codex环境。

## 3. 结论

【论文直接证据】目标成功率23.6%–61.6%；共享runner且保存输入的子集，1295次失败中460次（35.5%）最后输入仍有关键事实。‘记住’不能解释全部行动失败；信息不足、行动调整失败、自设限制是不同故障。

## 4. 未来影响

【阅读者推断，尚待验证】适合多目标记忆使用研究：把goal、deadline、权限、未完成事项和下一行动一起评测，而不是只优化事实回忆。

## 5. Critical thinking

【阅读者评析与后续建议】模型和runner耦合，不能把排行榜纯归因模型。8个构造世界的覆盖有限；事实存在不等于被正确理解，但足以否定所有失败都是遗忘。建议oracle事实、oracle行动建议、错误持久笔记和目标冲突四种干预，并记录机会错失/错误行动成本。

## 6. 可信度判断

**4/5**（与机构优先级独立）。多次轨迹与人工失败审计较强；语义判断有不确定项，合成场景不能证明真实高风险自治安全。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
