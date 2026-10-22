# 04. More Memory, Worse Agents: Error Reproduction and Anti-Persistence in LLM Agents

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27406)；[官方 PDF](https://arxiv.org/pdf/2610.27406)；[仓库 PDF](pdfs/2610.27406.pdf)
- 首次提交：19 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Ruhan Wang , Kishan Panaganti , Dongruo Zhou
- 机构（PDF 首页署名核验）：Indiana University；Tencent HY
- 机构优先级：P1A；主题相关性：直接相关；研究标签：memory error propagation；临时抽象；agent memory
- 阅读证据：正文§3–4、表1（PDF第4–7页）及附录H第31页；首页。已获取完整 PDF（31页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

研究记忆中的推断如何反复影响行动又被重新抽象，提出不持久保存合成指导的 Anti-Persistence。

## 2. 怎么做、实验如何设计

【论文直接证据】长期保留任务轨迹和结果，针对新任务检索后按模式临时合成指导，用完丢弃。相似任务结果日志驱动UCB风格模式选择，奖励同时考虑任务结果和合成调用成本。在ALFWorld/WebShop/ScienceWorld、3个backbone上与轨迹/抽象/联合记忆比较，3种子。

## 3. 结论

【论文直接证据】Qwen3-Coder-Next三任务成功率为96.0/54.0/52.6，对轨迹记忆84.4/50.7/43.8；但Gemma的ALFWorld与ScienceWorld分别存在Reflexion、联合记忆更强的配置。收益不是处处领先。

## 4. 未来影响

【阅读者推断，尚待验证】可把记忆分成可审计证据与可撤销解释，避免未经验证的规则永久进入知识库。

## 5. Critical thinking

【阅读者评析与后续建议】间接反馈仍存在：临时指导影响轨迹，轨迹又影响未来指导。UCB式规则没有论文所述非平稳加权观测下的regret保证。反复合成可能浪费已验证知识；建议比较经外部验证才持久化的选择性策略，固定总调用预算，并测量错误传播链而非只看分数。

## 6. 可信度判断

**4/5**（与机构优先级独立）。三环境多模型对照、显式局限支持中高可信度；部分辅助分析缺任务/种子级不确定性，不能推出‘所有抽象都该遗忘’。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
