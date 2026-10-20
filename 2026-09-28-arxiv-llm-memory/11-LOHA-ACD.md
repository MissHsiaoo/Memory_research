# 11. LOHA + ACD

- 论文：**Compress What You See, Not What You Say**
- arXiv：[2609.31430](https://arxiv.org/abs/2609.31430)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.AI new）
- 作者/机构（PDF 首页核验）：Zhensheng Zou、Guoqing Wang、Dan Hao；Peking University
- 机构优先级：**S｜顶级高校**
- 研究标签：latent memory、agent context compression、software agents
- 本地 PDF：[2609.31430.pdf](./2609.31430.pdf)

## 1. 做了什么

提出 LOHA，把旧 tool observation 压成 soft tokens，而 assistant action 与最近 K 条 observation 保留原文；再用 Anchored Context Distillation 教代理读取 latent history，同时约束它在纯文本输入上的原行为不漂移。

## 2. 怎么做、实验如何设计

默认 16× 编码 observation body，Hard-Last-K 保留近端精确文本；学生用低秩 reading patch 模仿 full-text teacher，并以 self-anchor 对齐原模型。作者在 SWE-bench Verified 499 题上评估 Qwen3-4B 和 SWE-Master-4B-RL。K=3 时每调用上下文下降 43%/57%，resolve rate 为 12.1%/21.8%，低于未压缩 14.5%/27.5%；但 32K 限制的 199 题子集中，LOHA 解出 42 题，优于适配后的 full text 22 题、masking 26 题和 base 31 题，并达到约 1.9× 并发吞吐。

## 3. Conclusion

压缩什么与保留什么必须按行为需求分开：旧观察适合 latent 化，近期可引用文本和动作应保持 hard。只提高 read-back 不保证代理行为，anchor 是必要的。

## 4. Future impact

它给 latent agent memory 一个实际折中：软表示承担远程线索，工具重新读取承担精确恢复。未来可以学习 query/action-aware 的 K 和压缩率，而不是固定 recency。

## 5. Critical thinking

论文诚实呈现压缩换来的成功率损失。真正问题是累计输入未必同步下降：Qwen3 因调用次数上升，trajectory 输入只从 1.65M 降到 1.51M；soft token 还会破坏 prefix cache。应比较等延迟/等成本下的最终成功率，并训练压缩器预测未来工具引用，而非只靠 recency。

## 6. 可信度判断

**4/5。** 已阅读全文。真实 SWE-bench、两个 agent 和 context-limit 对照有说服力；多数条件种子有限，压缩与策略适配仍有混杂，默认条件下存在明显性能损失。
