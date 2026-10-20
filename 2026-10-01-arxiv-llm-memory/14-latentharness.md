# 14 — LatentHarness: Learning Latent Actions for Memory and Reasoning via Counterfactual Policy Distillation

- arXiv：[2609.39740](https://arxiv.org/abs/2609.39740)；[官方 PDF](https://arxiv.org/pdf/2609.39740)；[本地 PDF](./2609.39740.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Xiaoqiang Wang 等；Université de Montréal、Mila
- 机构优先级：**A+，一流高校与研究所**；研究标签：`latent memory` `reasoning control` `counterfactual distillation`
- 证据：已核读 PDF 方法、实验与结论；数值为作者报告。

## 1. 做了什么

把继续思考、读取记忆、停止回答作为模型可学习的潜在动作，让记忆调用成为决策策略的一部分。

## 2. 怎么做、实验如何设计

定义 THINK、RECALL（快速权重记忆）和 EXIT；从同一状态分支尝试各动作一步，再用反事实策略蒸馏学习选择和记忆写入门。实验在 1.4B/2.6B Ouro 循环推理模型上，对一般与长上下文任务、延迟及参数开销比较；1.4B 设置相对最强基线报告一般任务约 +2.8%、长上下文约 +10%，相对长上下文基线推理约快 5.9 倍。

## 3. Conclusion

显式学习潜在记忆动作和停止动作，可减少一味延长上下文或推理链的成本。

## 4. Future impact

为 latent memory 提供清晰的控制接口：未来 agent 可在“检索外部文本”和“读写内部状态”之间动态选择。

## 5. Critical thinking

**推断：** 小模型上的快权重读写未证明长期多用户隔离、遗忘或可审计性。应测试连续会话中的错误写入/撤销、外部分布记忆与等计算检索器基线；5.9 倍速度需看硬件和比较对象。

## 6. 可信度判断

**4/5。** 反事实动作消融、速度与参数开销报告有说服力；底模规模与任务覆盖仍限制系统级泛化。
