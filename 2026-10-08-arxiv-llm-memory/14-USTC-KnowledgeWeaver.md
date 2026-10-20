# 14｜中科大：Knowledge Weaver 用互信息约束 agent 知识库积累

- 论文：[arXiv:2610.10042](https://arxiv.org/abs/2610.10042)｜[官方 PDF](https://arxiv.org/pdf/2610.10042)｜本地 `2610.10042.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-07 UTC，v1。作者/机构（PDF 首页）：Yuyang Zhao、Lizi Liao、Leyang Shen、Xiaoyan Zhao、Yang Zhang、Fuli Feng、Xiangnan He；USTC、Singapore Management University、National University of Singapore。机构优先级：A+；标签：agent memory、knowledge bank、continual accumulation；直接相关。

## 1. 做了什么

知识库越写越大不一定越有用：新增经验可能只是重复既有提示。Knowledge Weaver 将记忆写入视为“边际贡献”问题，训练 curator 从轨迹中提炼既独特又能提高后续任务成功率的知识条目。

## 2. 怎么做、实验如何设计

以 token-wise mutual information 启发的反馈减少重复，再结合单独成功奖励与“加入现有 bank 后”的边际成功奖励；executor 冻结，仅优化 curator，从而减少把基础 agent 变强误认作记忆效果。PDF 在 ALFWorld 的 valid_unseen 六类任务与 WebShop 的固定 100 个测试任务上比较 GRPO、提示式及人工知识库，并检查不同 bank size 和 retrieval 数目；训练、建库与最终评测轨迹来源分开列出。

## 3. 结论

在检索 k=10 个条目时，ALFWorld 平均成功率 54.0%、WebShop 42.0%，分别高于所用 GRPO 对照 16.9 与 18.7 个百分点。论文也报告冻结 executor 时知识库相对多种已有/人工库的总体收益；这些数字仍受任务和检索预算约束。

## 4. 未来影响（推断）

长期 agent memory 的写入器可追求“对现有库的增量信息与增量任务收益”，而不是给每条经历打独立相关性分；对共享技能库尤其有价值。

## 5. Critical thinking

互信息反馈可能偏爱罕见、格式特别的条目，而非用户真正需要的稳定知识；边际成功奖励要多次执行，代价可能抵消写入收益。建议测试知识库长期增长时的维护成本、删除旧条目的影响、跨用户转移与分布漂移；同时报告错误知识是否比冗余知识更危险。

## 6. 可信度：4/5

依据：已读 PDF 奖励设计、冻结 executor 协议及两环境实验。优点是把“新增条目贡献”与绝对成功区分，有明确强基线；局限是环境种类有限、WebShop 样本为固定子集，成本与真实长期可靠性待检验。
