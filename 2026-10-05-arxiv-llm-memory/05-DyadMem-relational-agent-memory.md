# 05｜DyadMem：用户—Agent 关系记忆的全链路基准

- 论文：[arXiv:2610.03020](https://arxiv.org/abs/2610.03020)｜[官方 PDF](https://arxiv.org/pdf/2610.03020)｜本地：`2610.03020.pdf`
- arXiv 正式公告：2026-10-05；首次提交：2026-10-02。
- 作者/机构：首页核验 Yifei Tao 等；StepFun、Nanyang Technological University、National University of Singapore、University of Hong Kong。
- 机构优先级：S；标签：personalized memory、agent memory、benchmark。关联性：直接。

## 1. 做了什么

DyadMem 将长期记忆对象从“用户事实/偏好”扩展到 URAM：特定 Agent 应如何与特定用户合作。它同时评估捕获、更新、召回以及最终答题，而不只测给定完美记忆后的 QA。

## 2. 怎么做、实验如何设计

PDF 定义六类记忆，在 3,065 段 episode、50,961 个 session、61,210 个 QA 上作会话级 Capture/Update 和查询级 Recall 标注；设 Gold-Memory 与 Full-Pipeline 两种 QA，评测 16 个开放权重和 4 个闭源模型。Gold-Memory QA 为 78.7–96.3%，完整流程平均仅 47.7%（开放）和 57.4%（闭源）；把用户侧记忆与 URAM 合用，在全部 20 模型上比一般经验记忆更好（论文报告）。

## 3. 结论

最终回答能力高不代表记忆系统可靠；捕获遗漏、召回不全和不安全删除会在完整流水线放大。URAM 提供了现有用户画像之外的评价维度。

## 4. 未来影响（推断）

个性化 Agent 基准可从“记住用户是什么样的人”转为“记住如何与这个用户协作”，尤其适用于跨会话策略、纠错与信任边界。

## 5. Critical thinking

大型标注数据不等于生态真实性：合成对话、标注政策、预设六类 ontology 可能固定了正确记忆形态。建议加入真实用户撤回同意、偏好短期反转、跨设备错误身份合并，并做人审隐私删除结果。还应公开按类别、历史长度和用户群体切片的误差。

## 6. 可信度：3/5

依据：已读 PDF 数据构建、分阶段评测与核心结果。优点是规模大、能定位流水线故障；局限是 benchmark 构造与自动评测的生态效度需要外部复现，论文的“全部模型有益”不能直接推广到真实用户。
