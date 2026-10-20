# 19｜理工大等：EngramEdit 把条件记忆变成可编辑知识接口

- 论文：[arXiv:2610.10533](https://arxiv.org/abs/2610.10533)｜[官方 PDF](https://arxiv.org/pdf/2610.10533)｜本地 `2610.10533.pdf`
- 正式公告：2026-10-08（cs.CL New submissions）；首次提交：2026-10-07 UTC，v1。作者/机构（PDF 首页）：Hongru Cai、Ran Wei、Wenjie Wang、Chengfa Wu、Ning Song、Yongqi Li、Wenjie Li；Hong Kong Polytechnic University、Hangzhou Diagens Biotechnology、USTC。机构优先级：B（直接相关、方法补充；非所列头部机构主导）；标签：latent/conditional memory、knowledge editing、LLM architecture。

## 1. 做了什么

条件记忆架构如 DeepSeek Engram 用 n-gram 找 embedding，可将事实存储与 Transformer 计算部分分离。EngramEdit 探索不改主干权重，仅更新条件记忆来修改事实，同时让不同表述指向同一新知识，尽量避免共享 embedding 牵连无关事实。

## 2. 怎么做、实验如何设计

先求能在多种表达下引导模型预测新事实的目标记忆表示，再联合更新相关 n-gram embedding；对高频复用 embedding 施加更强惩罚以保护旧知识。PDF 在 LongCat-Flash-Lite 上使用 CounterFact、ZsRE 测编辑成功、未见改写泛化、无关事实特异性；MQuAKE 测多跳应用，另有六项一般能力 F1 与累积编辑实验。对照包括 FT、AdaLoRA、UnKE、MoEEdit 和直接 memory fine-tuning。

## 3. 结论

论文报告接近完美的编辑成功率、对未见表达和多跳推理的迁移；在 CoT 多跳条件下，准确率接近最强对照的三倍，同时一般能力和无关知识大体保持。这里的“近完美”限于所测架构与数据，不应推断所有模型的记忆均可无损编辑。

## 4. 未来影响（推断）

如果可扩展到更多基础模型，模型内 latent/conditional memory 可能成为知识更新、个性化事实写入及撤销的独立接口，减少频繁全参训练。

## 5. Critical thinking

n-gram 触发并不天然等于语义身份：错别字、跨语言和长上下文改写都可能绕过更新；高频惩罚又会阻止重要公共事实修订。建议测试开放域别名、时间冲突、大批量累积编辑和用户删除请求，并比较总延迟与存储成本；还要检验更新是否在不当上下文中意外激活。

## 6. 可信度：3/5

依据：已核查 PDF 优化目标、CounterFact/ZsRE/MQuAKE 实验与对照。优点是直接攻击条件记忆的跨表达编辑难题；局限是主要在单一架构上验证，真实持续知识流和隐私删除尚未证明。B 是机构优先级，不是结果可信度。
