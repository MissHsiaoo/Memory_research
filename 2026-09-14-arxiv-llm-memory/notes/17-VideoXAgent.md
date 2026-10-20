# 17｜Online Video Agent Harness for Long Video Understanding

- arXiv：[2609.12818v1](https://arxiv.org/abs/2609.12818v1) · [官方PDF](https://arxiv.org/pdf/2609.12818v1) · [本地PDF](../papers/17-VideoXAgent.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Sen Yang , Boqiang Duan , Jing Yang , Weihao Bo , Jie Liu , Boyuan Tong , Ze Feng , Wenkang Zhang , Jingdong Wang , Hua Wu
- 核验机构：Baidu Inc.；依据为所下载PDF首页署名。
- 机构优先级：B｜强产业研究团队。研究标签：相邻强启发｜query-conditioned memory / evidence acquisition / long video。
- 主观新颖性：3.5/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§3.3、§4、表1–3、§5。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12818-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

VideoXAgent把长视频理解改成按问题在线取证：从原视频和问题出发，规划、调用专业工具、积累带出处的多模态证据，遇到冲突再核查。不先对全部视频离线摘要。对memory的启发在于根据当前问题恢复证据，而不是默认压缩摘要已经保留一切。

## 2. 怎么做，实验怎么做

ReAct式orchestrator调度60多种工具、14类后端，涉及帧抽取、检测、OCR、ASR等；结果区分观察、答案和不确定性，并设置125节点预算及逐级警告。能力分类从MINERVA推理轨迹挖掘。

五个benchmark，主要比较Claude Opus4.6加Gemini3.1 VLM工具，也替换orchestrator和工具模型。Video-MME-v2只评118视频/472问分层子集；LVBench关闭字幕和音频以匹配纯视觉设置；MINERVA使用公开1357问。

## 3. Conclusion：原文结论及边界

VideoMME-Long 85.1%，约52帧及51K上下文，接近直接大模型85.5–86.2%；Video-MME-v2子集61.28%，不是官方全量榜成绩。逐级预算警告在217问易循环压力集上降低上下文使用并消除未答完情况。作者明确成本指标主要是帧和上下文，不是所有工具和模型累计费用。

## 4. Future impact：潜在影响

我的推断：长期agent记忆可以存储可检索锚点和证据状态，按需调用重建工具；将冲突保留为待决假设比过早合并成一个结论更稳健。预算控制也能避免记忆反复检索形成无效循环。

## 5. Critical thinking：我的判断与可检验拓展

部分工具分类来自MINERVA推理轨迹，又在MINERVA评测，需要核查设计信息是否带来benchmark特化；论文对此有局限讨论。多模型、多工具系统与单模型的成本/权限并不相同，少帧不等于便宜。不同论文报告的离线处理帧与在线帧也未必同口径，应报告全链路费用、延迟和累计token。

## 6. 可信度、优点与不足

可信度3.5/5；novelty3.5/5。优点是在线证据路线、预算与模型消融、明确子集和音频设置。局限是复杂栈、潜在数据集定制、未做全成本可比评测。Baidu是作者机构，使用Claude/Gemini不能据此写成Anthropic/DeepMind联合论文；研究价值是证据调度，而非模型本身的视觉能力提升。

