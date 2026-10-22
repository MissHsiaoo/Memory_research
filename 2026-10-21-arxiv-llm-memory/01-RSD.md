# 01. Self-Evolving Agents through Privileged Retrospective Distillation

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27495)；[官方 PDF](https://arxiv.org/pdf/2610.27495)；[仓库 PDF](pdfs/2610.27495.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Yuhang Zhou , Yifan Wu , Bo Peng , Mingyi Wang , Jiayi Liu , Xiangjun Fan , Lizhu Zhang , Zhuokai Zhao
- 机构（PDF 首页署名核验）：Meta AI
- 机构优先级：P1A；主题相关性：直接相关；研究标签：self-evolving agent memory；参数内化
- 阅读证据：正文§3–5、表1–2（PDF第3–8页）；首页。已获取完整 PDF（26页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

把跨任务经验与当前轨迹的事后信息蒸馏进模型参数，而不只是把记忆追加到提示词。

## 2. 怎么做、实验如何设计

【论文直接证据】维护包含成功和失败轨迹的经验库；构建 precedents、lessons、逐步 reflection 和 future hindsight。同一模型作为特权教师重新打分学生实际生成的动作，以 forward KL 更新学生。10轮，每轮200个训练任务；Qwen3-8B/14B，在 ALFWorld、ScienceWorld、SearchQA 上与自训练、GRPO、oracle监督及推理时记忆比较，结果平均3个种子。

## 3. 结论

【论文直接证据】8B在 ALFWorld 的成功率由62.9升至76.6，ScienceWorld由15.6升至23.4。14B的 ALFWorld 79.6低于GRPO的82.6；SearchQA改善有限，14B推理时直接提供特权上下文41.4优于蒸馏后38.7。因此不是所有有用记忆都能顺利内化。

## 4. 未来影响

【阅读者推断，尚待验证】可把经验系统拆成外部可检索记忆与周期性参数巩固两层，分别测量推理成本和能力保留。

## 5. Critical thinking

【阅读者评析与后续建议】核心更新不使用验证器奖励，不等于整个系统完全无外部评价：frontier-guided扩展需要强模型与环境指标筛选上下文策略。未来信息只能出现在训练教师侧。建议固定总采样/教师token预算，测试跨环境迁移、旧任务遗忘，并对成功与失败经验分别消融。SearchQA是有价值的反例，不能仅报道最高相对增益。

## 6. 可信度判断

**4/5**（与机构优先级独立）。多环境、两规模、3种子及组件消融支持有限范围的结论；尚未复现实验，长期持续学习与跨域内化没有由当前结果证明。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
