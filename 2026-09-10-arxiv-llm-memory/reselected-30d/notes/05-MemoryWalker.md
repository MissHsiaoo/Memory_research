# 5. MemoryWalker

MemoryWalker: Stop Training Agents on Contexts They Never Saw

- 论文：[arXiv 2609.00865v1](https://arxiv.org/abs/2609.00865v1) · [本地 PDF](../papers/05-MemoryWalker.pdf)
- 首次提交：2026-09-01（UTC）；arXiv 最新记录：2026-09-01。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Zinco J、Xunjie Zhu、Shen Huang、Zhenyi Wang、Pengjun Xie、Jieping Ye
- 已核验机构：Token Foundry、Alibaba Group（PDF 首页署名）
- 机构优先级：A｜大型产业研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：memory compression / agent RL / conditioning consistency
- 主观 novelty：4.5/5；证据可信度：4/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–6；PDF 第 3–8 页、附录 F。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**抓住记忆压缩 agent 训练中的一个基础问题：训练时每个 token 看到的历史可能不是生成时的历史。

## 1. 做了什么

压缩或删除上下文会使 rollout 变成分叉历史；直接拿最终压缩串或完整物理轨迹训练，都可能给部分 token 配上错误的条件上下文。

## 2. 怎么做的

LogitTree 与 packed 4D attention mask 按生成时可见前缀重新计算，论文证明二者梯度等价；SDCC 用压缩 student 与重建前缀 stop-gradient teacher 的 forward KL 作较便宜近似。

## 3. 实验如何设计，结果如何

Qwen3-4B、Qwen3.7-Air；三种白盒 editor（TC-RAG、AgentFold、MemexRL）和 Claude Code/OpenCode 两种 harness。训练 81,638 QA，测试七套 search QA，共 38,270 问题/检查点；记录 token log-prob 差、分布 KL、压缩深度和 rollout reward，并有不压缩的误差底线。

## 4. Conclusion

纠正条件上下文是提高训练有效性的关键，精确修正与近似正则有不同开销。文中的 TV 界是局部 KL 下的界，不自动保证整段长轨迹奖励。

## 5. Future impact：对你的研究有什么启发

这篇最适合先检查现有训练代码：如果训练过程中 memory 会改写，是否保存了每步真实可见上下文？此检查可能比更换记忆结构更有收益。

## 6. Critical thinking、优点、局限与置信度

优点：问题可复现、诊断量明确、精确与近似方案对照清楚。局限：live search 与页面摘要会造成复现漂移；所谓黑盒 harness 仍通过 HTTPS 观测每轮 rendered prefix，不能理解为完全不需要日志。建议先用冻结文档/工具响应复现 log-prob gap，再比较压缩频率与成本。可信度 4/5：条件不一致机制可信，生产收益尚需独立验证。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

