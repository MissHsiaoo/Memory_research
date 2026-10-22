# 20. MemDev-Bench: Does Memory Help Code Agents?Benchmarking Memory Systems over Real Repository Histories

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27524)；[官方 PDF](https://arxiv.org/pdf/2610.27524)；[仓库 PDF](pdfs/2610.27524.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Guorui Chen , Tao Liu , Zhenzhen Huang , Yidan Zhang , Liyu Jiang , Shuoyuan Wang , Hanchen Sun , Xu He , Dong Li , Yihan Hu , Jianye Hao , Lei Feng
- 机构（PDF 首页署名核验）：Southeast University；Southern University of Science and Technology；MemoraX AI
- 机构优先级：P2补充；主题相关性：直接相关；研究标签：coding agent memory；memory harm；benchmark
- 阅读证据：正文§2–4（PDF第4–9页）及Limitations；首页。已获取完整 PDF（41页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

构建有时间顺序和相关性标签的真实仓库历史任务，评估经验记忆既帮助也伤害代码代理的情况。

## 2. 怎么做、实验如何设计

【论文直接证据】555基题对应4869历史任务；引用与代码历史双路挖掘，人工剔除直接泄题，三工程师审查并做独立盲标。实测仅Verified的344题、12个Python仓库；133困难题和50保持题，Relevant/Noisy/Repo历史、3次测试；限制网络泄题。

## 3. 结论

【论文直接证据】无记忆开放网络解决率93.31%，隔离后73.16%，显示泄题控制重要。加入噪声时保持题平均Harm从2.5%升至3.7%；原轨迹省约34%步骤，却增加输入。收益主要在文件内定位/编辑，不是稳定扩大正确文件召回。

## 4. 未来影响

【阅读者推断，尚待验证】评测memory不能只有净平均分，应分Rescue和Harm，并检验历史方案适用条件。

## 5. Critical thinking

【阅读者评析与后续建议】仅一个agent–model组合且不是全555题实测；历史相关性标签用到基题信息，只能作为实验控制，不能当部署可免费获得信号。建议跨模型、跨仓库时间外推、固定检索/构造预算，检查相似但不兼容历史。黑马补充理由是时间与泄漏控制及受损分析突出，而非机构背书。

## 6. 可信度判断

**4/5**（与机构优先级独立）。数据构建、盲标一致性与失败案例较严谨；单配置、子集和人工归因仍限制普遍结论。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
