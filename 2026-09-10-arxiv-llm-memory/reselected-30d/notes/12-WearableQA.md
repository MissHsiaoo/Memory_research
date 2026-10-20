# 12. WearableQA

WearableQA: A Benchmark for Health Reasoning over Real-World Wearable Data

- 论文：[arXiv 2609.05405v1](https://arxiv.org/abs/2609.05405v1) · [本地 PDF](../papers/12-WearableQA.pdf)
- 首次提交：2026-09-04（UTC）；arXiv 最新记录：2026-09-04。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Ji Soo Lee、Xilun Chen、Pierce Chuang、Ashish Shenoy、Jason Wei、Dohwan Ko、Hyunwoo J. Kim、Benoit Corda
- 已核验机构：Meta、KAIST、Korea University（PDF 首页署名）
- 机构优先级：A｜一线公司研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：personalized longitudinal reasoning；弱相关但评测启发强
- 主观 novelty：3.5/5；证据可信度：3.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–4；PDF 第 4–8 页。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**从真实长期用户记录出发，启发 personalized memory 超越文本事实召回。

## 1. 做了什么

用真实用户的可穿戴时间序列、血液指标和人口属性评估长期健康相关推理。这里不是提出新的 memory module，而是提供真实时间数据上的能力切分。

## 2. 怎么做的

4,084 道十选一题来自 200 名用户，每人最多 500 天数据；16 类问题按数据/健康推理和单/跨信号两轴组织。构题依据生理文献和群体统计规律，评分用确定性答案。

## 3. 实验如何设计，结果如何

14 个闭源/开源模型，在统一上下文、CoT 和 direct-answer 设置比较，结果 19.6%–72.9%，随机基线 10%；报告 Wilson 95% 区间，并研究输入表示和 agentic 设定。

## 4. Conclusion

长期数值记录上的计算与跨信号整合仍有明显困难；选对答案不能等价为真实临床效用。

## 5. Future impact：对你的研究有什么启发

可把用户记忆拆成事件、趋势、异常与当前状态，用它们压缩 500 天历史，再比较 compressed memory 与全历史在不同题型的表现。

## 6. Critical thinking、优点、局限与置信度

优点：真实纵向数据、题型可诊断、公开数据入口。局限：200 个用户产生多题，问题间相关性意味着题级区间可能低估用户泛化不确定性；群体关联不能自动解释个体因果。建议用户级划分/聚类 bootstrap，并设只看群体统计的 shortcut baseline。可信度 3.5/5：数据场景很有价值，长期个性化决策还需用户级验证。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

