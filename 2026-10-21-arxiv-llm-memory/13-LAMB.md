# 13. LAMB: Latent Multi-Hypothesis Beliefs for Long-Horizon Large Language Agents

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.26955)；[官方 PDF](https://arxiv.org/pdf/2610.26955)；[仓库 PDF](pdfs/2610.26955.pdf)
- 首次提交：18 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Peien Ding , Hui Li , Yuhan Liu , Jinsong Su
- 机构（PDF 首页署名核验）：Xiamen University；MBZUAI
- 机构优先级：P1B；主题相关性：直接相关；研究标签：latent memory；multi-hypothesis belief；POMDP
- 阅读证据：正文§3–5、表1–2（PDF第4–9页）；首页。已获取完整 PDF（28页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

以共享Common状态加多个Delta假设保存部分可观察环境中的不确定性，避免单一摘要过早确定世界状态。

## 2. 怎么做、实验如何设计

【论文直接证据】最新行动/观测递归更新状态，以动作结果似然反馈调整假设；4个Common+8个Delta形成固定12-token前缀，不先平均成单向量。训练包含动作模仿和模拟器事实监督。ALFWorld、ScienceWorld、BabyAI、Crafter比较全历史和调优记忆方案。

## 3. 结论

【论文直接证据】主表ALFWorld92.5、ScienceWorld83.5、Crafter58.64；相对最强调优基线分别+4.5、+22.0、+19.55点。ALFWorld平均任务耗时18.53秒低于PABU42.02，但高于AgentEvol12.34，不能称所有方案最快。

## 4. 未来影响

【阅读者推断，尚待验证】可将多目标记忆分为共享事实和目标特定差异；这是研究迁移建议，不是论文已经验证多目标通用记忆。

## 5. Critical thinking

【阅读者评析与后续建议】状态语义分解不具唯一可识别性，mixture本身不排除不合法世界配置；模拟器事实监督是关键额外条件。上下文曲线仅取共同成功45题，存在条件选择，不能代表所有任务。建议测目标切换、粒子坍缩、无状态标签训练与长期遗忘。

## 6. 可信度判断

**4/5**（与机构优先级独立）。有多环境、同类调优对照及机制消融；额外监督和模拟环境限制外推，未复现。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
