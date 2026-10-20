# 03｜MARI：结构化决策记忆用于个性化推荐

- 论文：[arXiv:2610.11501](https://arxiv.org/abs/2610.11501)；[官方 PDF](https://arxiv.org/pdf/2610.11501)；[本地 PDF](03-MARI.pdf)。主分类 cs.CL，2026-10-09 公告批次 New submissions；首次提交 2026-10-08（UTC），v1。
- 作者/机构（PDF 首页）：Leikun Liang、Guoshuai Wang、Xingsheng He 等；Alibaba Group。
- 机构优先级：S（用户指定头部企业）；标签：personalized memory、recommendation、decision memory；相关性：直接；novelty：高。

## 1. 做了什么

论文用“结构化决策记忆”替代仅把点击、浏览、购买揉成一条行为序列。每条记忆记目标、约束和权衡，使推荐模型在高度相似商品的困难选择中能调用用户过去的决策理由。

## 2. 怎么做、实验如何设计

离线 Post-Hoc Decision Distillation 从异质行为和用户内容生成 SDM，存入 Decision Memory Bank；在线检索 top-3 SDM，辅助 LLM 推荐。实验分为决策记忆生成 PHDD 与多行为推荐 MBR，后者包含类内/跨类下一商品预测和 Difficult Choice Prediction；同一候选空间比较 ID 序列推荐器、未微调 LLM 与基于 SDM 的模型，并做原始行为/记忆消融。PDF 写明离线生成与在线使用分开计时。

## 3. 结论

直接证据：全文 Table II 报告微调后的 4B MARI 在跨类预测 Hit@1 为 0.5561、困难选择为 0.8868；PHDD 生成的结构化记录在若干指标接近更大模型。部分 4B/8B 未微调模型在跨类任务加入 SDM 反而下降，说明不是“任何模型加记忆都变好”。

## 4. 未来影响

我的推断：将决策过程而非物品 ID 作为长期记忆，有望迁移到购物 agent 的偏好解释和反事实推荐，但先要验证离线记忆是否忠实于真实动机。

## 5. Critical thinking

关键假设是行为日志足以推断真实权衡；后验 LLM 很可能为购买编造貌似合理的理由。与序列推荐相比，MARI 的新意是明确保留“为何选择”的压缩记录。建议在有用户明确理由和事后纠错的数据上评价 SDM 忠实度，并区分同一用户历史时间泄漏、检索成本、模型微调贡献与记忆贡献；以相同 token/延迟预算比较原始行为和 SDM。

## 6. 可信度判断

**3/5**。有多任务、多模型与消融的全文证据；但 PHDD 的开放式质量部分由 LLM-as-judge 判定，训练与离线蒸馏成本、真实用户动机校验不足，不能把可读解释等同因果解释。
