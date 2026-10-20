# ACLArena: Agent Continual Learning in Multi-stage Post-training

- arXiv：[23989](https://arxiv.org/abs/2609.23989)；[官方 PDF](https://arxiv.org/pdf/2609.23989)
- arXiv 初次提交：2026-09-21（v1）；正式公告归属：2026-09-22 新稿，二者不可混同。
- 作者：Haixin Wang , Xiaoxuan Wang , Junkai Zhang , Han Zhang , Renliang Sun , Alexander K Taylor , Yidan Shi , Haoran Deng , Chenguang Wang , Jason Cong , Yizhou Sun , Wei Wang（arXiv 官方列表）
- 机构：University of California, Los Angeles；University of California, Santa Cruz（论文 PDF 首页核验）
- 机构优先级：A｜全球一流研究型高校
- 研究标签：agent continual learning；能力保留；训练轨迹记忆；直接相关
- 证据说明：以下数值均为论文自身报告；“我的推断/建议”并非论文实证。

## 1. 做了什么

ACLArena 研究多阶段训练时 agent 的能力何时被后续任务覆盖，以及如何把几个专长合成一个可用模型。其离线高质量轨迹回放与多 LoRA 专家路由相结合，为“agent 自进化后不遗忘旧技能”提供了相对系统的实证。

## 2. 怎么做，实验怎么做的

固定课程依次训练数学、搜索、电商工具使用和指令遵循；在模型层与 token 层诊断遗忘。比较序贯训练、混合教师在线策略蒸馏、self-distilled fine-tuning、权重合并，以及作者的高质量轨迹回放/LoRA 专家路线。基础为 Qwen3-8B，实验用两个 H200 节点；域内评 AIME26、NQ、τ3-Retail、IF-Eval，域外评 GPQA、MMLU、PopQA/TriviaQA、多跳检索、τ3 其他域及 IF-Bench。表 1 序贯模型数学 AIME26 从数学阶段 25.83 掉到最终 10.21，证明明显遗忘。表 2 的 MLE 在 NQ 49.7、搜索单跳 57.7，较 Seq-Final 33.5、44.9 改善；IF-Bench 29.1 却低于 Seq-Final 30.8，非全项最优。

## 3. Conclusion

多阶段 agent 训练确实有强干扰；经验轨迹重放和专长隔离能够回收多项能力，但代价是维护多个专家与路由，不是免费持续学习。固定任务顺序下的好方法，不一定对任意新任务序列适用。

## 4. Future impact

对持久 agent memory 的启发是保存可验证的成功轨迹和适用任务标签，再作为重训/回放资产，而不只保存一句抽象心得；评估应同时看新任务学习曲线与旧任务回归。该迁移是我的推断。

## 5. Critical thinking

作者有意固定课程，无法说明任务排列改变后的鲁棒性。高质量轨迹筛选依赖正确奖励与协议检查，在开放环境里这些信号可能缺失。建议插入相互冲突的技能、跨月工具 API 变化、错误成功轨迹，再测路由误判和专家存储开销；也应对齐总训练计算与推理延迟比较合并、回放和多专家。

## 6. 可信度判断、优点与局限

4/5：已核查主表、方法、消融和两类泛化任务。优点是清楚展示遗忘及权衡；局限是固定课程、单主要骨干和多专家成本，不能推断长期开放世界稳健性。
