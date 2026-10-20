# 1. Auto-RecSys

Auto-RecSys: Harnessing Autonomous Research Agents for Industry-Scale Recommender System

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.10922v1](https://arxiv.org/abs/2609.10922v1) · [官方 PDF](https://arxiv.org/pdf/2609.10922v1) · [本地 PDF](../papers/01-Auto-RecSys.pdf)
- 首次提交：2026-09-10T00:09:18Z（UTC，与公告日不是同一概念）。
- 作者：Ming Li, Dai Li, Xuying Ning, Bo Sun, Rui Li, Yi Zhang, Silvia Gong, Xuan Cao, Rui Li, Cornelia Carapcea, Qunshu Zhang, Zhigang Wang, Yinglong Xia, Andy Wang
- 机构：Meta、UIUC（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜persistent memory / self-evolving agent
- 原文定位：§3–7，尤其 PDF 第 9–12 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

为训练耗时数天的工业推荐模型构建自动研究 agent；重点不是单轮回答，而是跨服务器、跨会话、故障恢复后的实验延续。

## 2. 怎么做的，实验怎么做

将自然语言 skill/playbook 与执行正确性脚本分离；集中保存 registry、逐实验状态、基线和 append-only 实验历史。执行演化循环积累失败禁忌与成功流程，想法演化循环根据结果生成后续假设；并行实验使用独立状态文件。论文保留人审想法和实现的工作模式。

实验与结果：详细可靠性分析来自一个推荐模型的 31 次独立实验迭代。中途第 21 次发生基线变更；主要操作修复次数从初期每次 4.0，降到稳定期 1.3，最后阶段 0.5；最后 6 次中 5 次不需操作修复。人工时间由小时/天降至分钟是报告的经验性描述，不是随机对照时间测量。

## 3. Conclusion

证据支持流程记忆能降低反复出现的操作错误；没有证明训练本身更快，也没有隔离记忆模块对研究创新质量的因果贡献。

## 4. Future impact

对你的 self-evolving memory 很实用：把失败记忆写成有版本、适用基线和执行约束的程序性知识，而非仅检索相似历史。

## 5. Critical thinking：优点、问题与可验证拓展

优点是暴露真实基线迁移与故障恢复过程。局限是单模型的顺序观察，任务难度和人员经验也可能变化；修复指标排除了实现中的 reasoning/debugging，不能叫总错误率。建议固定故障注入序列，比较无记忆、文本 playbook、带版本约束记忆，联合统计 GPU 浪费、负迁移及想法收益。可信度 3/5：部署经验可信度高于普适因果结论。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

