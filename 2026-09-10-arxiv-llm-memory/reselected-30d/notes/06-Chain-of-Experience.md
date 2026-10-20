# 6. Chain-of-Experience

Chain-of-Experience for Continual LLM Improvement

- 论文：[arXiv 2608.18027v1](https://arxiv.org/abs/2608.18027v1) · [本地 PDF](../papers/06-Chain-of-Experience.pdf)
- 首次提交：2026-08-18（UTC）；arXiv 最新记录：2026-08-18。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Haoqin Tu、Yunhao Fang、Yizhong Wang、Cihang Xie、Shen Yan
- 已核验机构：ByteDance Seed、UC Santa Cruz（PDF 首页署名；注明实习研究）
- 机构优先级：A｜一线产业研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：ICL / feedback / continual improvement
- 主观 novelty：3.5/5；证据可信度：3.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–4；PDF 第 4–6 页及附录 H。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**为“经验何时有效”提供反馈类型对照，直接挑战堆更多历史就能持续进步的假设。

## 1. 做了什么

把模型的多次作答及反馈累积成 Chain-of-Experience，让后续尝试使用先前的执行结果或自我批评，研究推理时持续改善。

## 2. 怎么做的

对比无反馈、自反馈、执行器反馈、正确性反馈。后者使用真实正确性信号，是高信噪比参考上界；另与 few-shot ICL、Dynamic Cheatsheet、ACE 及不同推理预算对照。

## 3. 实验如何设计，结果如何

六套任务覆盖 AIME 2025、OmniMath、LiveCodeBench V6、LiveBench Code、EvaLearn、GPQA Diamond；多模型，实验重复三次。论文报告 self-feedback 约 +5.6 个百分点的平均改善，并在整体口径下减少 API 成本约 19%；执行/正确性信号通常更强。这里主要是迭代求解与反馈利用，不是已经完成跨月用户记忆评测。

## 4. Conclusion

反馈质量比简单扩大经验输入更关键；不同域可获得的反馈决定了实用收益。

## 5. Future impact：对你的研究有什么启发

可把 memory 条目的内容从“过去怎么答”扩展为“过去怎么答、哪里失败、依据什么验证”，同时学习可信度或来源标签。

## 6. Critical thinking、优点、局限与置信度

优点：公开区分 oracle 正确性与可获得反馈，比较准确率和成本。局限：反馈权限、历史预算和检索质量可能影响对 ACE/ICL 的排序；平均 API 成本不能直接迁移到今天的部署价格。建议固定总 token/工具调用预算，增加反馈延迟、错误反馈及跨任务流测试。可信度 3.5/5：经验反馈方向明确，持续学习措辞应限定在实测场景。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

