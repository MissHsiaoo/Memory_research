# 04. COPE

- 论文：**COPE: Continual Personalization of LLMs under Sparse User Feedback via User Embeddings and Self-Evaluation**
- arXiv：[2609.26853](https://arxiv.org/abs/2609.26853)
- 提交日期：2026-09-22；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Ruike Cao 等；中国科学技术大学、Alibaba Qwen Business Unit
- 机构优先级：**S｜顶级高校 + 头部工业团队**
- 研究标签：LLM personalization、continual learning、user embedding、self-evaluation
- 本地 PDF：[2609.26853.pdf](./2609.26853.pdf)

## 1. 做了什么

为稀疏反馈场景提出持续个性化框架 COPE：每位用户拥有极小的可学习 embedding，同时共享模型学习自评估和响应策略；显式反馈缺失时，模型用自评估代理信号继续优化，并可与检索历史互补。

## 2. 怎么做、实验如何设计

COPE 组合监督偏好注入、self-evaluation objective 与 policy objective，分别更新用户 embedding 和/或模型参数。实验基于 PersonaLens，选择 256 名用户、20 个领域，每人覆盖 17 个领域；前三次遍历共 51 次交互持续更新，第四次未见任务做评估，并测试反馈概率 0.25/0.5/0.75。主干为 Qwen3-1.7B，另测 4B、8B 与 Llama-3.1-8B；基线含 sparse/dense retrieval、query-expanded retrieval、PAP、训练式 T-PAP。反馈概率 0.75 时 COPE 为 4.74、PAP 为 3.69；COPE+SR 达 5.36。自评分与用户平均轨迹相关系数训练期 0.81、留出运行 0.71±0.06，另有人类盲评和偏好漂移测试。

## 3. Conclusion

紧凑用户 embedding 可以承载隐式偏好，self-evaluation 能在稀疏反馈下提供连续学习信号；参数记忆与显式检索历史互补，且在本文训练长度内未观察到明显通用能力崩塌。

## 4. Future impact

可发展成“显式 episodic memory + 隐式用户向量 + 可校准反馈模型”的混合 personalization 架构，适用于助手长期适配、低延迟端侧画像和偏好漂移追踪。

## 5. Critical thinking

创新点是把每用户参数成本压到约主干参数的 1.2×10^-5，并正面处理反馈稀疏与偏好迁移。最大隐患是闭环自评估：若 evaluator 对某类用户系统性偏置，embedding 会强化错误。PersonaLens 仍是模拟交互，用户反馈与真实长期满意度并不等价；共享权重更新还可能造成跨用户干扰与隐私泄漏。建议做真人纵向实验、用户删除/重置、membership inference、跨用户负迁移和 evaluator 校准。

## 6. 可信度判断

**4/5。** 已阅读全文；实验覆盖反馈稀疏、模型扩展、漂移、消融和人类盲评，证据较强。模拟用户占比高且部署级隐私/隔离未验证，因此不打满分。
