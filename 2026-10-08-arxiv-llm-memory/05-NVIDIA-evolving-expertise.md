# 05｜NVIDIA：冻结模型如何从部署经验持续积累能力

- 论文：[arXiv:2610.09146](https://arxiv.org/abs/2610.09146)｜[官方 PDF](https://arxiv.org/pdf/2610.09146)｜本地 `2610.09146.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-06 UTC，v1。作者/机构（PDF 首页）：Yexiao He、Yucheng Tang、Pengfei Guo、Yufan He、Andriy Myronenko、Can Zhao、Ang Li、Daguang Xu、Dong Yang；NVIDIA、University of Maryland, College Park。机构优先级：S；标签：agent memory、continual learning、multimodal expertise；直接相关。

## 1. 做了什么

把冻结 LLM/VLM 的部署经验积累拆成三类外部资产：指导操作的 Skill、可靠知识的 Knowledge Memory、保留图像案例的 Multimodal Knowledge Base。问题不是简单检索旧答案，而是让不能更新权重的模型在不断变化的知识环境中稳步学习。

## 2. 怎么做、实验如何设计

Skill 管理推理与工具使用；Knowledge Memory 仅保留过往案例或可信外部证据支持的事实；多模态库保存视觉样例并指导与当前图像的关系判断。候选更新须在新病例上获益且不能损伤旧病例。PDF 在 AgentClinic-MedQA、MedChain、MedThink-Bench、MedThinkVQA 及两个非医疗视觉任务共六个 benchmark 上测试四种开源/闭源基础模型，对比裸模型、ACE、SkillOpt，并做组件消融及跨模型迁移。

## 3. 结论

论文报告医疗任务相对基础模型最高 34.2% 的改善，增益可迁移到未见案例和其他模型；非医疗视觉任务也有正面结果。证据支持外部经验表示的互补性，但“最高”改善不是六任务平均收益，不能概括为医疗安全部署已验证。

## 4. 未来影响（推断）

个人助理的长期记忆也可分离程序性规则、事实与多模态案例，并给每类设不同证据和回归门槛；这比把所有经验压成一段文本更利于溯源和迁移。

## 5. Critical thinking

医疗任务对错误知识的代价极高，而论文中的验证集并不等于临床后果评估。Skill、事实和视觉库可能互相矛盾；更强 retrieval 也可能放大旧指南。建议在时间漂移、撤销更新、冲突证据以及专家盲审的纵向设置下测量遗忘和安全事故；与真正微调及固定预算的 RAG 比较总维护成本。

## 6. 可信度：3/5

依据：已阅读 PDF 的系统结构、六基准设置和消融。优点是覆盖文本/视觉、多个模型及更新验证；局限是部署模拟而非临床前瞻试验，“可靠知识”判定与迁移范围仍依赖数据和评审流程。机构优先级 S 并不抬高证据评分。
