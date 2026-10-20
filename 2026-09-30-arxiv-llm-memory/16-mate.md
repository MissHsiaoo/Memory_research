# 16 — When Successful Memories Mislead Embodied Agents

- arXiv：[2609.35808](https://arxiv.org/abs/2609.35808)；[官方 PDF](https://arxiv.org/pdf/2609.35808)
- v1 提交：2026-09-20；正式公告批次：2026-09-30（北京时间；首次公告，不按提交日归档）
- 作者/机构（PDF 首页核验）：Quanquan Li 等；East China Normal University、Peking University、USTC
- 机构优先级：**A**；研究标签：`embodied agent memory` `negative transfer` `trajectory adaptation`
- 证据范围：阅读全文；本地 PDF：[2609.35808.pdf](./2609.35808.pdf)

## 1. 做了什么

研究“检索到的成功轨迹反而误导当前 agent”的负迁移，并提出确定性后处理 MATE，把历史轨迹改造成当前执行规范可用的记忆。

## 2. 怎么做、实验如何设计

固定检索结果后，依次过滤过期控制上下文、抽取 condition-action-effect、做经验证的 action normalization、按任务选择局部/全局表示并在预算内序列化，不新增 LLM 调用。134 个 ALFWorld 任务中，Qwen2.5-14B/72B 达 81.3%/93.3%，记忆约 1.6k token；raw full trajectory 为 20.1%/69.4%。消融显示 action normalization 是主要机制。

## 3. Conclusion

“语义相关且过去成功”不等于当前可执行；retrieval 之后必须做执行条件适配。

## 4. Future impact

这会改变 agent memory pipeline：评价重点从检索命中率转向 retrieved memory 的可执行兼容性与负迁移率。

## 5. Critical thinking

结果很强，但主要来自 ALFWorld 的动作词表和人工验证 rewrite map；现实工具 API 演化更开放，映射可能不完整。应在 ScienceWorld、Web/API agent、动态工具 schema 和故意过时轨迹上复现，并区分 token 缩短、动作规范化和结构重写的独立收益。

## 6. 可信度判断

**4/5。** paired controls 与消融较好地定位 action normalization，两个模型尺度一致。局限是单环境、确定性规则和固定映射限制普适性。
