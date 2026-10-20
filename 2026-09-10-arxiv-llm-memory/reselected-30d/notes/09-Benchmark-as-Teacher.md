# 9. Benchmark-as-Teacher

BaT: Towards Self-Evolving Medical Research Agent with Stage Rubrics

- 论文：[arXiv 2608.16211v1](https://arxiv.org/abs/2608.16211v1) · [本地 PDF](../papers/09-Benchmark-as-Teacher.pdf)
- 首次提交：2026-08-17（UTC）；arXiv 最新记录：2026-08-17。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Junqi Liu、Yufan He、Yexiao He、Pengfei Guo、Dong Yang、Andriy Myronenko、Can Zhao、Hanrong Ye、Tianhao Qi、Yuyin Zhou、Daguang Xu、Yucheng Tang
- 已核验机构：NVIDIA、UC Santa Cruz（PDF 首页署名）
- 机构优先级：A｜一线产业研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：self-evolving agent / curriculum / process feedback；跨方向启发
- 主观 novelty：4/5；证据可信度：2.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–5；PDF 第 5–10 页，尤其 §5.2 Limits。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**把阶段级错误记忆转成下一轮训练课程，对持续学习和任务记忆调度很有启发。

## 1. 做了什么

BaT 将医学研究 agent 的阶段评分反馈给课程选择器，再用合成训练状态和 GRPO 修补弱阶段。

## 2. 怎么做的

Stage Bank 异步生成内容隔离的 executable states；BiCuRL 按固定诊断集表现选择 S-target、S-mix、E2E 训练混合，进行下一轮训练，权重更新后再次诊断。

## 3. 实验如何设计，结果如何

Qwen3.5-4B/9B；AutoMedBench-Lite 为 7 个任务轨道，每轨道重复 10 次，按轨道聚合。政策级 Overall：4B 6.1→22.9，9B 19.9→53.4；完整系统的 79.6 是另一设置，不能混用。外部八个基准中，4B 全部低于原底座；9B 的迁移表现也有升有降。

## 4. Conclusion

在持续使用诊断反馈的领域适应中有效；没有证实无代价的通用自提升。

## 5. Future impact：对你的研究有什么启发

可将 memory 错误按写入、保留、检索、使用、归因分阶段，动态选择下一轮训练任务，而非仅按最终奖励采样。

## 6. Critical thinking、优点、局限与置信度

优点：课程闭环具体，论文主动披露退化和评测角色。关键局限：AutoMedBench-Lite 的聚合分数参与课程选择，因此不是 untouched final test；只有 7 个独立轨道，70 次运行不等于 70 个独立任务。建议三分数据：训练、课程诊断、一次性终测，同时测通用能力遗忘。可信度 2.5/5：有价值的方案，但当前泛化证据有限。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

