# 17｜Stateless Language Agents：让长期研究状态留在 harness 而非聊天里

- 论文：[arXiv:2610.07625](https://arxiv.org/abs/2610.07625)｜[官方 PDF](https://arxiv.org/pdf/2610.07625)｜本地 `2610.07625.pdf`
- 正式公告：2026-10-07；首次提交：2026-10-06（UTC）。
- 作者/机构（PDF 首页）：Qizheng Zhang 等；Stanford、Carnegie Mellon、University of Washington、SambaNova、UC Berkeley。机构优先级：A（顶尖高校主导）；标签：agent memory architecture、long-horizon self-evolution；直接相关。

## 1. 做了什么

主张“搜索有状态、Agent 无状态”：长程自动研究的候选解、实验结果等可靠状态留在 harness；每次 Agent 调用从这些证据重建短而明确的角色上下文。

## 2. 怎么做、实验如何设计

SLA 用无持久聊天的 Advisor 读跨方向摘要并分配实验，Worker 在独立短上下文中执行。PDF 对比三个近年框架，在软件工程、kernel 优化和算法设计任务以最高 10 亿 token 预算评估；所测任务最终结果均领先，kernel 任务达到最强基线最终表现所需 token 少于其 16% 左右，并做共享检查点消融。

## 3. 结论

长程 Agent 的持久状态放置位置本身是核心设计变量；无限延长对话不等于持续进步。论文的超长预算研究任务不能直接外推到日常个人助理。

## 4. 未来影响（推断）

Agent 记忆系统可向“可审计外部状态 + 按角色渲染的短上下文”演进，减少历史膨胀和重复劳动。

## 5. Critical thinking

Harness 摘要也可能丢失关键失败细节或错误归因。应比较相同墙钟/人力成本、状态恢复错误、权限边界和任务突然变化；还应测 Advisor 决策是否把团队固定在单一研究方向。

## 6. 可信度：4/5

依据：已读 PDF 超长预算比较、共享检查点消融和成本曲线。优点是重视长期尺度；局限是评测任务少且价格/模型变化影响复现。
