# 14｜Reality Is the Final Verifier: On Two Key Gaps in Agentic Software Engineering

- arXiv：[2609.12039v1](https://arxiv.org/abs/2609.12039v1) · [官方PDF](https://arxiv.org/pdf/2609.12039v1) · [本地PDF](../papers/14-Reality-Final-Verifier.pdf)
- 首次提交：2026-09-10（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Alexander Krentsel , Shubham Agarwal , Mert Cemri , Shu Liu , Sidharth Sankhe , Ziming Mao , Matei Zaharia , Ion Stoica
- 核验机构：UC Berkeley；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级研究型高校。研究标签：相邻强启发｜self-evolving lessons / evidence / failure diagnosis。
- 主观新颖性：3.5/5；证据可信度：3/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§2–3框架、§5、§6.3；观点论文。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12039-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

提出agentic软件开发的two-gap框架：需求R只是用户意图的近似，环境模型M只是真实世界的近似；所以实现通过评测E，不代表部署满足真正需求。把reward hacking、幻觉和运行环境变化放入同一诊断视角，强调测试外部还需持续修订保障依据。

## 2. 怎么做，实验怎么做

内层是实现—验证，外层用部署证据决定该修改需求、环境模型、评测、实现还是防护。建议维护带版本的保障记录，连接证据、假设、责任人、适用范围和失效条件。

这是一篇概念/研究议程论文，以既有案例和方法讨论支持论证，没有新受控benchmark证明该闭环提高某个百分比。引用案例并不等于作者进行过完整因果实验；笔记不把其当作新算法SOTA。

## 3. Conclusion：原文结论及边界

核心结论是开放环境中难以一次性证明两个gap完全关闭，更现实的是持续缩小并控制暴露。对记忆尤其相关的§6.3提出将lesson定义为“失败类别→修复”的规则，并保留诊断、证据、范围、所有者、复查触发与测试；反证出现时应缩小、替换或退役。

## 4. Future impact：潜在影响

我的推断：下一代self-evolving agent memory不应只积累成功摘要，而应保存可失效的操作知识。经验可落实到测试、约束或monitor，不必全部塞入prompt；这有助于把记忆的价值从“回想”变成“避免重复犯错”。

## 5. Critical thinking：我的判断与可检验拓展

框架与requirements engineering、安全论证及持续运维有明显连续性，新颖性更多是agent情境下的统一表达，不能仅换术语就宣称新算法。开放世界无法封闭不等于任何评测都无价值。需要提出可测假设：证据化lesson是否比文本摘要更少负迁移，维护成本是否抵消节省，适用范围错误能否被检测。

## 6. 可信度、优点与不足

可信度3/5，评分指经验效果证据而非逻辑观点“真假”；novelty3.5/5。优点是显式区分失败来源并强调有意遗忘。局限是无新因果实验、维护数据库困难仍未解决。建议与RIPPLE联读：前者定义该保留什么和何时失效，后者提供小规模组合验证实验，两者并不共同构成已验证完整系统。

