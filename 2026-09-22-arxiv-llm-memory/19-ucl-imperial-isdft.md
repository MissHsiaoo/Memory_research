# iSDFT: Information-Proximal Self-Distillation for Continual Learning in LLMs

- arXiv：[24646](https://arxiv.org/abs/2609.24646)；[官方 PDF](https://arxiv.org/pdf/2609.24646)
- arXiv 初次提交：2026-09-21（v1）；正式公告归属：2026-09-22 新稿，二者不可混同。
- 作者：Ahmed Khaled Khamis , Xiaotong Ji , Hassan Jaber , Rasul Tutunov , Matthieu Zimmer , Jun Wang , Haitham Bou-Ammar（arXiv 官方列表）
- 机构：University College London；Imperial College London；Politecnico di Milano（PDF 首页）（论文 PDF 首页核验）
- 机构优先级：A｜全球一流研究型高校
- 研究标签：LLM continual learning；知识保留；自蒸馏；相关但非会话记忆
- 证据说明：以下数值均为论文自身报告；“我的推断/建议”并非论文实证。

## 1. 做了什么

iSDFT 研究给 LLM 加新能力时如何少忘旧能力。它不保存用户聊天记录，但解决 agent 记忆参数化/技能内化的底层问题：学习新任务后，基础能力是否还能维持。方法以信息邻近约束重新设计自蒸馏目标。

## 2. 怎么做，实验怎么做的

作者将教师 token 分布按信息预算做指数倾斜，避免简单全分布匹配在学习新能力与旧能力保持之间失衡。对 Tool Use 和 Science 两种专门化，比较 SFT、标准 SDFT、其它蒸馏与策略目标；覆盖 Qwen2.5-7B、Qwen3-1.7B、Gemma-4-E2B、OLMo3-7B 等学生，并在常识、代码、数学、指令等保留评测。附录表 5：Qwen2.5-7B 两类训练 ×16 项保留评测共 32 处，iSDFT 对标准 SDFT 赢 30、平 1、输 1；对基础模型达到或超过 23/32。单个分项并非始终最好，报告也要看新任务分数。

## 3. Conclusion

信息约束的自蒸馏在所测设置下明显改善遗忘，但不能据此保证任意长训练序列或用户个性化更新。它主要是离线任务专门化，不是实时可编辑记忆。

## 4. Future impact

若与版本化记忆结合，参数更新可用于稳定高频技能，显式记录负责易变事实；这种分层可能缓解长期 agent 的“学新忘旧”。此为我的系统推断。

## 5. Critical thinking

标准保留基准可能遗漏真实 agent 的工具协议与偏好冲突；两种独立专门化不等于几十次连续更新。建议做多阶段递增训练，控制总 teacher 调用与训练计算，并测适应速度、遗忘、后门/注入残留和用户删除请求。理论信息预算若需经验调参，其稳健性也应跨域复核。

## 6. 可信度判断、优点与局限

4/5：理论动机、跨骨干和大量保留指标已核查；优点是问题定义严谨、实证覆盖面较好；局限是离线序列短、方法开销和真实记忆编辑性尚未证明。
