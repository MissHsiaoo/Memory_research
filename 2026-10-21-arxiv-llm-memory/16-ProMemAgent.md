# 16. ProMemAgent: Long-Horizon Proactive Assistance with Context-Aware Prospective Memory from Sensory Perceptions

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27400)；[官方 PDF](https://arxiv.org/pdf/2610.27400)；[仓库 PDF](pdfs/2610.27400.pdf)
- 首次提交：19 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Lilin Xu , Linyang He , Kaiyuan Hou , Yuang Fan , Minghui Zhao , Xuhai Xu , Xiaofan Jiang
- 机构（PDF 首页署名核验）：Columbia University
- 机构优先级：P1B；主题相关性：直接相关；研究标签：prospective memory；personalization；proactive assistance
- 阅读证据：正文§3–5（PDF第4–6页）及Limitations第9页；首页。已获取完整 PDF（18页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

在无显式提醒请求时，结合当前感知与历史未完成意图，决定是否应主动帮助。

## 2. 怎么做、实验如何设计

【论文直接证据】CPMBench含250场景的1000实例，其中200单意图、50多意图场景，每实例200事件；Omni500实例配视频/音频。生成未来事件/时间触发线索，建立后续状态变化链接，2条内容+8条cue检索；8B reasoner通过强模型轨迹LoRA蒸馏，按场景60/40分割。

## 3. 结论

【论文直接证据】论文报告Set-F1比最强全上下文GPT-5.4基线高9.7点。分别评价意图召回、状态变化召回、误触发、主动决策和内容集合F1，体现检索与主动行为不是同一目标。

## 4. 未来影响

【阅读者推断，尚待验证】可作为多意图记忆使用的起点，尤其适合研究已完成意图的去激活、机会触发和不要打扰用户的权衡。

## 5. Critical thinking

【阅读者评析与后续建议】真实片段是逐事件配对，不是连续在野穿戴流；尚未评测事件切分完整pipeline。系统把视听转文本可能丢信息，且训练专用reasoner与通用baseline的适配程度不同。建议等训练预算、跨用户/语言划分和不平衡高‘无需干预’场景，报告每小时误打扰率。

## 6. 可信度判断

**4/5**（与机构优先级独立）。场景级隔离、对照和多维指标较清晰；合成事件、蒸馏依赖和真实长期交互缺失限制结论。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
