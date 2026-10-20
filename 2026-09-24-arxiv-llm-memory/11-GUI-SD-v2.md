# 11. GUI-SD-v2

- 论文：**Learn How to Act from Your Own Interactions: On-Policy Self-Distillation for GUI Agents**
- arXiv：[2609.27307](https://arxiv.org/abs/2609.27307)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Yan Zhang 等；中科院、南开大学、Tencent、清华大学、中国科学院大学
- 机构优先级：**S｜头部工业团队 + 一流高校**
- 研究标签：GUI agent、on-policy self-distillation、working memory、long horizon
- 本地 PDF：[2609.27307.pdf](./2609.27307.pdf)

## 1. 做了什么

提出 GUI-SD-v2，把 on-policy self-distillation 从单步 GUI grounding 扩展到多轮 GUI agent。它同时解决代理“不听特权指导”和特权信息过粗的问题，用逐步 reasoning/memory guidance 教会学生保留后续任务真正需要的信息。

## 2. 怎么做、实验如何设计

第一阶段 PAPO 将同一 GUI state 下有/无 privileged context 的 rollout 放入相对优势优化，提升 privilege following 与一般 GUI 能力；第二阶段让 privilege-conditioned self-teacher 为每一步给 reasoning 和 memory 指导，并只蒸馏选择的 token。实验在 AndroidWorld 116 个任务/20 apps、MobileWorld 201 个任务（主报 GUI-only）上，每任务三次有效运行，比较 SFT、GUI-SD-v1、GHD 等。方法在 AndroidWorld 达 67.2% Pass@1、79.3% Pass@3，在 MobileWorld 达 25.6%/31.6%；逐步指导相对 trajectory-level 指导把 AndroidWorld Pass@1 从 51.7% 提到 67.2%。

## 3. Conclusion

对多轮 GUI agent，逐步、与当前状态对齐的 reasoning 和 memory supervision 比整条轨迹共享一份提示有效；先提升“会使用教师信息”，再蒸馏信息，是重要训练顺序。

## 4. Future impact

可用于训练会管理 working memory 的 agent：教师不只给下一步动作，还标出哪些观察需跨步保留。它也能生成 memory controller 的密集监督数据。

## 5. Critical thinking

优点是把 memory guidance 纳入逐步行为训练，并在可执行环境而非静态问答上验证。风险是 privileged teacher 本身可能泄漏未来信息或 benchmark 特定标注，训练收益未必来自真正的通用记忆机制；MobileWorld 绝对成功率仍较低。建议在桌面/浏览器平台、不同 teacher、无未来泄漏约束和更长 horizon 上复测，并单独评估记忆召回质量。

## 6. 可信度判断

**4/5。** 已阅读全文；双环境、三次运行、阶段/粒度消融充分。平台集中在 Android，且 privileged supervision 的现实可获得性有限。
