# 09｜GraphMemory：把记忆从上下文中解耦

- 论文：[arXiv:2610.02687](https://arxiv.org/abs/2610.02687)｜[官方 PDF](https://arxiv.org/pdf/2610.02687)｜本地：`2610.02687.pdf`
- arXiv 正式公告：2026-10-05；首次提交：2026-10-02。
- 作者/机构：首页核验 Yehya Farhat 等；IBM Research、Rice University。
- 机构优先级：S；标签：LLM memory systems、test-time continual learning、图检索。关联性：直接。

## 1. 做了什么

GraphMemory 将在线 context 优化视为记忆更新，并把反复出现的策略组织为可增长图；每题只向模型暴露有界相关子图。

## 2. 怎么做、实验如何设计

方法把知识点作为节点、关系作为加权边，以查询找到入口节点并扩展邻域；对照 append-only 全局 playbook 和 ACE。PDF 在 FORMULA、FINER 两项金融推理任务及 Claude Haiku 4.5、Qwen3.8-27B 上报告冷启动、最终测试准确率与构建 token；总体构建 token 少约 81–85%。需要注意：表中 Claude/FORMULA 最终准确率 GraphMemory 0.81、ACE 0.85，不能说全面领先。

## 3. 结论

在所测环境，结构化检索大幅降低记忆构建/注入成本，准确率可接近但并非总超过较贵基线。

## 4. 未来影响（推断）

长期 Agent 系统可把记忆写入与上下文窗口预算分离，按需检索小型可解释策略子图。

## 5. Critical thinking

常量上下文开销依赖固定检索上限，未消除外部图的存储、索引与更新成本。图边若由模型自生成，错误关系可能传播；需做按时间漂移、冲突知识、节点删除和复杂图规模的测试，并计入总 wall-clock 与 API 成本。医疗/金融部署还需审计可追溯来源。

## 6. 可信度：3/5

依据：已读 PDF 方法和结果表。优点是诚实展示 token/成本—准确率权衡；局限是仅两项近域任务、部分指标不如 ACE，推广到一般记忆场景有待验证。
