# 7. Evo-Harness

Evo-Harness: Context-to-Harness Skill Compilation for Self-Evolving Agents

- 论文：[arXiv 2608.15071v2](https://arxiv.org/abs/2608.15071v2) · [本地 PDF](../papers/07-Evo-Harness.pdf)
- 首次提交：2026-08-15（UTC）；arXiv 最新记录：2026-08-30。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Tianxin Wei、Zhan Shi、Minhua Lin、Bing He、Zewen Liu、Yisi Sang、Yuanchen Bei、Xuying Ning、Jiaru Zou、Ting-Wei Li、Xiao Lin、Yanjun Zhao、Chi Wang、Benoit Dumoulin、Dakuo Wang、Jingrui He、Hanqing Lu
- 已核验机构：Amazon、UIUC、Penn State、Emory、AG2 AI、Northeastern（PDF 首页署名）
- 机构优先级：A｜大型产业研究团队＋强高校。这是本次选刊层级，不是学校综合排名。
- 主题：self-evolving agent / procedural memory / skill compilation
- 主观 novelty：4/5；证据可信度：3.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–4；PDF 第 5–7 页表 1–3。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**将单次执行中的经验编译成可持续修改的 harness，考察复杂真实任务中的在线学习。

## 1. 做了什么

冻结基础 LLM，在连续任务流中更新通用与 topic-level skill harness，从一次尝试的噪声上下文中提炼可复用操作经验。

## 2. 怎么做的

context-to-harness compilation 将失败、工具反馈和过程信息转成技能更新；通过 solver/evolver 搭配、反馈来源及组件消融研究改善从何而来。

## 3. 实验如何设计，结果如何

Claude Opus 4.6 为默认 solver/evolver，在 CL-Bench、TerminalBench2、SWE-bench Lite、τ-bench、WebArena-Infinity 上比较 AWM、DC、Evo-Memory、ACE、XSkill。TerminalBench2 从 No-Evolve 62.92 到 73.03，最强对照 XSkill 为 66.29；SWE-bench Lite 从 63.67 到 67.00。收益大小跨任务差别显著。

## 4. Conclusion

单次轨迹可以产生可复用程序经验，但不是所有经验注入都有正收益；部分基线低于不演化。

## 5. Future impact：对你的研究有什么启发

对 self-evolving memory 的启发是把写入目标变为“下一次执行可用的规则/流程”，同时显式比较内容、检索与执行控制的作用。

## 6. Critical thinking、优点、局限与置信度

优点：五类复杂环境、强 baseline、关注在线任务流。局限：默认 evolver 很强且有额外成本，任务顺序影响经验库，较小成功率差需要种子/顺序重复支持。建议报告等总成本、任务家族隔离，以及强 evolver/弱 solver 与同模型演化的差异。可信度 3.5/5：广度不错，长期非平稳流的稳定性仍待验证。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

