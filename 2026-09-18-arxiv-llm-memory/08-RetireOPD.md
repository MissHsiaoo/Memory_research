# 08. RetireOPD: Self-Retiring On-Policy Distillation for Agentic Reinforcement Learning

- arXiv：[论文页面](https://arxiv.org/abs/2609.20784v1)｜[官方 PDF](https://arxiv.org/pdf/2609.20784v1)｜[本地 PDF](papers/08-RetireOPD-2609.20784.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Yan Yu , Zhengxi Lu , Yizhou Liu , Yichen Pan , Aozhe Wang , Qipeng Chen , Hua Yang , Wenqi Zhang , Weiming Lu , Qianglong Chen , Yongliang Shen
- 机构：Zhejiang University；Alibaba。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜优先公司/高校合作，直接相关
- 研究标签：skill internalization；agentic RL；参数化记忆与教师退出
- 入选理由：Alibaba/浙大让带 skill 的教师适时退出，将显式经验内化为学生能力，避免持续蒸馏限制学生。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

RetireOPD 讨论带特权任务 skills 的教师是否应该一直约束 skill-free 学生。作者先用环境奖励优化 skill-conditioned teacher，再让学生联合接受 GRPO 与 on-policy distillation，满足转移停滞和任务能力阈值后移除教师，仅继续 RL。其记忆关联是把外部显式 skills 内化到参数；不是部署后随时更新的用户记忆系统。

## 2. 怎么做，实验如何设计

教师与学生使用同架构/初始化路线，学生轨迹上以 teacher 的 dense token 分布提供 OPD，学生推理时不再输入 skills。Adaptive Retirement 同时监控 teacher/student log-prob 差距是否停止缩小及学生是否达到教师约 .9 的成功率。实验在 Qwen2.5 1.5B/3B/7B、ALFWorld 与 WebShop 上比较纯 GRPO、持续 OPD 和教师，并消融 alignment/competence 条件，另比较线性退火与阈值敏感性。方法、主表、退出时机和附录设置已阅读；未实际进行训练。

## 3. 结论

3B ALFWorld 成功率 93.8 对纯 GRPO 75.0，提升 18.8 个百分点；1.5B WebShop 75.8 对 56.8，提升 19.0 个百分点。特定 3B/7B 教师消融设置下 adaptive 为 92.2，持续 OPD 82.8，删除两个退出条件各为 89.0；该 92.2 与主表 93.8 来自不同设置，不能合并。作者还发现部分阈值范围退出时机变化不大，但并非所有任务上的参数免调保证。

## 4. 未来影响

我的推断：经验有“先指导、再内化、最后解除依赖”的生命周期，memory system 不一定永远依赖检索。可探索把稳定、高频经验蒸馏到模型、保留近期或可变知识在外部记忆，并用性能证据决定何时退出旧教师。这只是由本文得到的研究建议，论文没有验证真实个人偏好长期内化。

## 5. Critical thinking

log-prob gap 的停滞只是采样分布上的代理指标，不是因果地证明“教师已无用”。学生回报与教师相近也可能由偏置奖励或过拟合实现；退出后任务迁移会否遗忘仍需检验。最重要的成本问题是教师额外训练与学生联合训练的总环境交互/计算，应与纯 RL 等总预算比较，而非只看学生阶段。建议做重复随机种子与置信区间、非平稳任务变化、不同 skill 质量、退出后重启教师的对照，区分学会原经验与真的超越教师。

## 6. 可信度判断

可信度 3.5/5：全文跨三尺度、两环境、双条件消融和时机敏感性提供实验证据。优点是教师可靠性与阶段效用拆开处理，推理无 skill 依赖。局限是环境和模型家族较集中、主表点估计不能独立证明稳定性、总代价与长期迁移证据有限。机构已核验，参数化 skill 内化可启发 memory 研究，但不能据此称为通用自演化记忆系统。

