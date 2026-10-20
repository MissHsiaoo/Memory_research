# 09. Spotify Conversational Recommendation Agent

- arXiv：[2609.30297](https://arxiv.org/abs/2609.30297)
- 提交日期：2026-09-16；正式公告批次：2026-09-28（cs.CL new / cs.AI cross-list）
- 作者/机构（PDF 首页核验）：Enrico Palumbo 等；Spotify
- 机构优先级：**A｜一流工业研究团队**
- 研究标签：LLM personalization、conversational recommendation、self-improvement
- 本地 PDF：[2609.30297.pdf](./2609.30297.pdf)

## 1. 做了什么

针对没有真实对话日志的冷启动阶段，构建多轮合成用户数据与自动 self-improvement loop，用于优化 Spotify 对话推荐代理的规划和工具调用，并报告真实线上效果。

## 2. 怎么做、实验如何设计

管线从真实/合成单轮意图扩成带 persona、约束变化和用户反馈的多轮对话，再用闭环用户模拟器执行；用人评检查自然度、能力覆盖和一致性，四项均超过 90%。改进循环对同一 query 的成功/失败轨迹做方差与对比归因，以 8 个 mini-batch 喂给 coding agent，迭代修改 prompt、tool description 或控制流，人工审核后合并。离线 pass@1 在强手工 prompt 上相对再增 8%（sign test p=0.01）；两周、约 1500 万用户 A/B 中，听歌量 +14%、周活 +5%、skip rate -5%。

## 3. Conclusion

合成多轮数据足以在上线前发现规划故障，基于对比证据的 coding-agent 修复比泛化反思更可操作；但超过四轮后性能下降，instruction retention 和内容 refinement 仍难。

## 4. Future impact

这是 personalization 研究少见的线上闭环证据。未来 memory 可把推荐条目、拒绝原因与长期偏好分层保存，并用线上反馈持续更新规划策略。

## 5. Critical thinking

最大亮点是大规模 A/B，但新体验相较“只支持 session refinement”的旧体验同时改变了多项产品能力，不能把全部线上增益归因于 self-improvement loop。合成用户也可能强化现有产品假设。建议做 memory/no-memory、自动修复/人工修复和短期/长期偏好分离的因子实验，并报告个性化对少数用户群的负效应。

## 6. 可信度判断

**4.5/5。** 已阅读全文。生产部署、显著性检验和 1500 万用户实验很强；具体 prompt/tool 与私有数据不可复现，线上归因存在组合干预混杂。
