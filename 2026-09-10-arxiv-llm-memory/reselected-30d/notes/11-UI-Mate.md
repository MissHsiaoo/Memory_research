# 11. UI-Mate

UI-Mate: Advancing Open-Weight Foundation GUI Agents with In-Context Demonstrations

- 论文：[arXiv 2608.15930v1](https://arxiv.org/abs/2608.15930v1) · [本地 PDF](../papers/11-UI-Mate.pdf)
- 首次提交：2026-08-16（UTC）；arXiv 最新记录：2026-08-16。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Zihan Ding、Longxu Dou、Qi Gao、Xiangwu Guo、Shengchao Hu、Zilong Huang、Zihang Jiang、Lei Ke、Mengcheng Lan、Weixian Lei、Hanxuan Li、Honglin Li、Xiyun Li、Zaitang Li、Leowei Liang、Xin Luo、Haozhe Ma、Jiayi Mao、Zhoujie Pan、Can Qin、Tianyuan Qu、Weiqi Wang、Wenkai Wang、Yonglin Wang、Yuxin Wang、Chenxu Wu、Yingchen Yu、Chenyu Zhang、Yuhao Zheng
- 已核验机构：Tencent Hy Frontier Team（PDF 首页团队署名）
- 机构优先级：A｜大型公司模型团队。这是本次选刊层级，不是学校综合排名。
- 主题：multimodal ICL / procedural memory / GUI agents
- 主观 novelty：4/5；证据可信度：3/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3、§6–7；PDF 第 23–27 页。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**将用户示范提炼成可重规划的子任务流程，是个性化程序记忆的具体应用。

## 1. 做了什么

UI-Mate 通过环境驱动的数据闭环训练 GUI agent，并在推理时使用多模态示范指导长工作流。

## 2. 怎么做的

联合自动生成任务、搭建环境、执行、过滤与能力均衡；SFT/在线 RL 使用 task-verifier bundles。示范不是逐点击重放，而用于提取可适配当前界面的子任务流程。

## 3. 实验如何设计，结果如何

评估 OSWorld-Verified、WindowsAgentArena 和自建 OSWorkerBench（100 任务、41 应用）。27B 在前两者得 77.0%/66.2%；OSWorkerBench 严格成功率 41.0%，进度 76.86%。33-task self-demo 子集成功率从 17.2% 到 35.4%，示范来自同一目标任务的成功轨迹；45-task human variant-demo 的系统性汇总结果留待后续。

## 4. Conclusion

示范可提高同任务长流程可靠性，但目前不能把主要 demo 增益解释成充分验证的陌生任务迁移。

## 5. Future impact：对你的研究有什么启发

把 user demonstrations 编译为可编辑、带前置条件的 procedure memory，研究何时遵循示范、何时依据当前状态重规划。

## 6. Critical thinking、优点、局限与置信度

优点：真应用工作流与可执行评测，区分进度和完全成功。局限：self-demo 相当于给过同题成功路径，弱于跨任务个性化迁移；模型/数据/harness 变化难隔离，正文与表格中部分基线版本命名需核对。建议以 variant-demo 为主，加入界面变化和错误示范，并单独消融 memory 模块。可信度 3/5：完整系统有成绩，ICL 泛化边界要谨慎。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

