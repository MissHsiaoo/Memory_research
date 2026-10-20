# 10. AdsWorldEngine

AdsWorldEngine: A Self-Evolving Conversational Advertising Agent through Orchestrator and Tool Coevolution

- 论文：[arXiv 2608.13833v1](https://arxiv.org/abs/2608.13833v1) · [本地 PDF](../papers/10-AdsWorldEngine.pdf)
- 首次提交：2026-08-13（UTC）；arXiv 最新记录：2026-08-13。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Simiao Zuo、Chenhui Xu、Yimeng Jia、Qiang Lou、Jian Jiao、Denis Charles
- 已核验机构：Microsoft（PDF 首页署名；不额外推断为 Microsoft Research）
- 机构优先级：A｜一线公司研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：agent-tool coevolution / personalization；弱相关但工程启发强
- 主观 novelty：4/5；证据可信度：3/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §5–8；PDF 第 5–8 页、表 3–5。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**生产系统里共同优化 agent 和工具，适合类比 reader 与 memory/retriever 的共同演化。

## 1. 做了什么

构建对话广告系统，先判断是否适合展示，再由 orchestrator 调工具选择广告，执行结果又用于改进工具。

## 2. 怎么做的

Qwen3-30B-A3B-Thinking 经 SFT/GRPO 更新 orchestrator；高低奖励 rollouts 产生偏好对，训练 intent-to-ads 工具排序器。固定 evaluator 看完整对话，工具只看生成的 intent；共交替三轮。Opportunity Gate 使用人工准则和标签训练，控制误触发成本。

## 3. 实验如何设计，结果如何

Gate 收集 30,000 条人工标签，过滤后 27,000 条。工具循环表 5 报告最终相对多样性 +62.87%、相关性 +82.26%；Microsoft Copilot 的 20 天线上试验报告 RPM +22%、广告覆盖 +74%。公开的是相对收益，不能换算为成功率百分点。

## 4. Conclusion

agent 与工具共适应在该生产目标下有收益；商业指标上升本身不证明用户满意度或个性化质量提升。

## 5. Future impact：对你的研究有什么启发

可把 orchestrator 换成 memory reader，把工具换成 retriever/writer：用执行轨迹交替训练双方，并让 evaluator 相对稳定以降低目标漂移。

## 6. Critical thinking、优点、局限与置信度

优点：真实部署、线下和线上证据、显式区分判断器与工具模型。局限：训练和离线评测共用 evaluator，容易向其偏好过拟合；线上未充分披露流量、随机化单元和显著性。建议在 memory 实验中加入独立 judge、用户级随机化、长期留存/错误记忆率指标。可信度 3/5：工程启发强，公开信息不足以独立复核商业增益。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

