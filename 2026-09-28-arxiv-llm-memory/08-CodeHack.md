# 08. Code-Based Skills for Language Agents

- arXiv：[2609.31076](https://arxiv.org/abs/2609.31076)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.AI new）
- 作者/机构（PDF 脚注核验）：University of Warsaw、Princeton、UCL、McGill/Mila、Mistral AI 等
- 机构优先级：**S｜顶级高校/工业实验室**
- 研究标签：agent skills、procedural memory、long-horizon agent、continual learning
- 本地 PDF：[2609.31076.pdf](./2609.31076.pdf)

## 1. 做了什么

系统研究代码化技能作为语言代理的动作抽象：技能把重复的低层决策固化成可调用程序，但必须保留退回 primitive action 的通道以应对 abstraction leakage。

## 2. 怎么做、实验如何设计

作者发布 CodeHack 技能库，在 NetHack/MiniHack 长程环境中比较仅 primitive、仅 semantic skill、skill+primitive 三种控制，并分别做 zero-shot、监督微调和强化学习。指标包括任务成功、游戏进度、调用成本和学习速度。摘要报告技能使游戏进度接近 3×、每 episode 推理成本下降 86%；RL 下，同预算技能代理的 dungeon level 平均增益为 primitive 代理的 7.2×，混合动作空间保留遇到技能盲区时的回退。

## 3. Conclusion

程序性外部记忆不仅节省 token，也改变可学习的动作尺度；但封闭技能库不应成为唯一动作空间，最有效的是可上下移动的抽象梯子。

## 4. Future impact

对 self-evolving memory 的启发是：skill 应附带适用条件、失败检测和 fallback，而不只是自然语言描述。未来可让代理自动生成、验证并版本化 CodeHack 类程序技能。

## 5. Critical thinking

强点是把效率、性能与学习速度同时测量，并跨三种学习设置。当前技能主要由研究者提供，未直接证明代理能安全地产生和维护技能；NetHack 的规则固定，开放工具生态的 API 漂移更难。建议加入自动 skill discovery、技能冲突、错误传播和长期版本回滚实验。

## 6. 可信度判断

**4.5/5。** 已阅读全文。强机构、公开环境/代码与多训练范式构成扎实证据；对“自演化”部分仍是间接证据，因为库的构造与治理并非自动完成。
