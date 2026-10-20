# 03 — StateTree: Enhancing Long-Term Dialogue Reasoning via Reinforcement Learning

- arXiv：[2609.38809](https://arxiv.org/abs/2609.38809)；[官方 PDF](https://arxiv.org/pdf/2609.38809)；[本地 PDF](./2609.38809.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Naen Xu 等；Zhejiang University、Alibaba Taobao & Tmall Group
- 机构优先级：**S，Alibaba 与一流高校**；研究标签：`long-term dialogue` `personalized memory` `RL`
- 证据：已核读 PDF 方法、实验与结论；以下数值为作者报告。

## 1. 做了什么

用可验证的树路径伪任务训练长对话模型跨会话检索、比较时间戳和处理偏好更新。

## 2. 怎么做、实验如何设计

StateTree 在真实多会话对话中嵌入二叉树式 key-value 线索，要求沿根到叶的路径逐步检索并识别目标问题；课程 RL 逐渐加深树，并加入需组合中间线索的版本。使用约 616 个训练例、10K 上下文训练，在 128K 长度评测。Qwen2.5-7B/14B 和 Qwen3-8B 的实验显示超过 SFT 与 RL 基线；7B 在 LongMemEval 128K 上最高 +23.60%，14B 达 59.0%，高于论文比较的 QwenLong-L1-32B 的 45.2%。

## 3. Conclusion

结构化、可自动判分的辅助任务能用短上下文训练出更强的长对话状态追踪能力。

## 4. Future impact

对个性化 agent 很直接：可从少量真实对话构造训练信号，让模型学会寻找“当前有效”的用户状态。

## 5. Critical thinking

**推断：** 二叉树路径任务可能偏重显式线索和时间戳，真实偏好常隐含、矛盾或含糊。应测试未显式标注的偏好变化、跨语言会话、长跨度噪声，以及和强检索系统在同等总推理成本下比较。

## 6. 可信度判断

**4.5/5。** 训练任务可验证，跨模型与长度外推证据较强。局限是主要结论仍来自基准对话和构造式路径，长期真实用户行为的外部效度未知。
