# 14. Temporal Self-Distillation: Faster Inference in Discrete Diffusion Language Models

- arXiv：[2609.15177v1](https://arxiv.org/abs/2609.15177v1) · [官方 PDF](https://arxiv.org/pdf/2609.15177v1) · [本地原文](../papers/14-Temporal-Self-Distillation.pdf)
- 正式公告：2026-09-15；首次提交：2026-09-14（两者不是同一字段）。版本：v1。
- 作者：Shijian Xu , Andrea Miele , Metod Jazbec , Volker Roth , Eric Nalisnick , Ilija Bogunovic
- 首页核验机构：University of Basel；University of Amsterdam；Johns Hopkins。
- 机构优先级：A：强机构主榜（无普通机构补位）。机构只决定阅读优先级，不代替证据评分。
- 研究标签：直接相关｜diffusion LLM；时间自蒸馏
- 主观 novelty：4.5/5；证据可信度：4/5（不是概率）。
- 阅读范围：方法、实验与消融、训练附录、Limitations；未实测推理延迟。

本笔记基于以上官方原文；第1–3节为论文内容及结果口径，第4–6节为阅读者判断，不能当作作者已验证的结论。未进行实验复现或代码审计。

## 1. 做了什么（论文报告）

让扩散LLM在较早去噪步骤做出本来要较晚才可靠的预测。TSD用同一模型同一轨迹中token最终确定时的分布作为较早时刻的老师，无需另外训练一个教师或预先收集教师轨迹。

## 2. 方法与实验设计（论文报告）

在线采样去噪轨迹，以正确性奖励加权，用JS散度对齐早期与commitment-time分布；代码和数学还按目标长度惩罚冗长正确回答。用LoRA调整LLaDA-8B-Instruct，规划则从已经RL训练的GDSD开始；共七基准：GSM8K、MATH500、Countdown、Sudoku及三代码集。训练约3000步、每提示4轨迹，主要报告2000步，MATH取1000步；扫解码阈值得到质量与NFE曲线，另测128/256/512长度。

## 3. 结论与结果边界（论文报告）

Countdown约20次NFE达到80%正确率，GDSD峰值需约100次但峰值略高；GSM8K约35–50NFE到80%，基础模型约65NFE。MATH500改善有限，长预算基础模型仍可更好。Sudoku报告的是空格填对比例，不是整盘通过率；最高4.5倍等速度表述主要指前向次数减少，不是实测墙钟加速。

## 4. Future impact（我的推断）

可用于在已有能力基础上提前作出并行决定，而不是靠更多参数提高能力。对扩散生成的工具参数、记忆检索查询也许有用，但必须有可靠验证器。它和DA-DLM分别解决时间上的确定性与同一步token依赖，组合值得研究但尚无本文结果。

## 5. Critical thinking（我的分析与建议）

commitment-time老师依赖当次较完整信息，早期状态未必可确定同一答案；过度蒸馏可能让模型过早自信。建议报告可靠性校准、错误token锁定、真实端到端延迟，并与等训练计算的其他目标比较。长度目标和checkpoint选择要在独立验证集冻结，避免测试调参。本文只适用于unmasking-only，若允许重新遮蔽/修改已确定token，需要重新定义教师。

## 6. 可信度、优点与局限（主观评估）

4/5。优点：七基准、后RL与跨长度验证、JS/KL和长度消融、坦率承认不增加新能力。局限：依赖可程序化正确性信号，无开放对话评测；峰值正确率可能下降，NFE是成本代理，且全部以LLaDA家族为主。不能把更早输出当成具备长期自进化记忆。

## 来源与审计

[官方摘要页快照](../sources/2609.15177-abs.html)记录日期和版本；[本日入选核验](../verification.json)保存公告主分类、PDF页数与SHA-256。[返回日报](../README.md)。
