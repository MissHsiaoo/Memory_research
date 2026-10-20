# 15 — MemCodex: Self-Programming Hierarchical Memory for Language Agents

- arXiv：[2609.39765](https://arxiv.org/abs/2609.39765)；[官方 PDF](https://arxiv.org/pdf/2609.39765)；[本地 PDF](./2609.39765.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Xiaoqiang Wang、Bang Liu；Université de Montréal、Mila
- 机构优先级：**A+，一流高校与研究所**；研究标签：`agent memory` `hierarchical memory` `self-programming`
- 证据：已核读 PDF 方法、实验与结论；数值为作者报告。

## 1. 做了什么

让 agent 自行编程多层级记忆模块，按需把事件、关系、技能和潜在表征组织为可查询结构。

## 2. 怎么做、实验如何设计

演化记忆程序负责写摘要、提取关系和技能；读取先由粗到细再回到原始历史。MemArena 提供统一测试接口，在 LoCoMo、LongMemEval-S、MemoryAgentBench、PersonaMind 上与适应性记忆基线比较；作者报告平均任务成功率相对最强基线 +10.1%，上下文 token 约少 3.4 倍、推理约快 2.1 倍。每个基准约 20% 数据用于程序演化。

## 3. Conclusion

记忆结构与读写程序可随任务自我调整；层级读取比始终拼接长历史更省成本。

## 4. Future impact

可能成为可插拔 agent memory 的设计范式，也提示需要单独评测“演化记忆控制器”的泛化。

## 5. Critical thinking

**推断：** 对每个基准单独用 20% 数据演化可能让程序学习测试分布特征；真实部署没有稳定的标注任务回报。应跨基准零迁移、连续变化用户与预算匹配测试，并记录演化成本及记忆污染恢复能力。

## 6. 可信度判断

**4/5。** 四基准、效率与性能并报是优点；基准内演化和离线回报假设限制“通用自演化”结论。
