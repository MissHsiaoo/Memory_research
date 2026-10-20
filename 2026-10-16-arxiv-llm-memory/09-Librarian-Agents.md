# 9. Librarian Agents：为未来查询预先整理工作区

- 论文：[arXiv:2610.22273](https://arxiv.org/abs/2610.22273) · [官方 PDF](https://arxiv.org/pdf/2610.22273) · 本地 PDF：`2610.22273.pdf`
- 公告：2026-10-16；初次提交：2026-10-15。
- 作者/机构：PDF 首页核验 Anikait Singh、Teresa Zhang、Yoonho Lee 等；Stanford、Carnegie Mellon University。**机构优先级 P2**。
- 主题：proactive memory curation；long-context workspace；RL agent。证据范围：全文 24 页。

1. **做了什么（论文证据）**：把静态语料主动整理成层级文件与引用链接，供下游 agent 未来查询使用，而不是只在提问时做反应式检索。
2. **怎么做与实验（论文证据）**：构建者 agent 将原始文档变为可导航合成工作区；把构建过程建模为 MDP，通过下游答题正确率强化学习优化。对比检索和预计算结构基线，测重复查询的前置成本摊销与未见域迁移。
3. **结论（论文证据）**：BrowseComp-Plus 相对最强基线 +33 点，BRIGHT 零样本未见领域平均 +31 点；前期整理成本可在重复查询中摊销。
4. **未来影响（我的推断）**：agent memory 可能更像可维护知识工作区，而非扁平向量库；主动整理尤其适合项目级长期资料。
5. **Critical thinking**：工作区在文档更新或权限撤回后如何增量修复？需测单次查询下的总成本、引用失效、数据污染及人为审核可解释性。
6. **可信度 4/5**：强基线、跨域与成本摊销实验支持方向；任务仍主要是文档问答，真实长期协作和更新成本未充分证明。
