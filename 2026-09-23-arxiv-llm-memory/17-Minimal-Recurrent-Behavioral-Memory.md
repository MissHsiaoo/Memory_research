# Minimal Recurrent Behavioral Memory：部分可观测模仿的最小记忆

- arXiv：[2609.25757](https://arxiv.org/abs/2609.25757)；[官方 PDF](https://arxiv.org/pdf/2609.25757)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者：Xianyao Li、Fang Xu、Rui Min、Ruitong Tian、Jing Du
- 机构：机构未核验（PDF 首页未列出 affiliation）
- 机构优先级：B（黑马/启发性补充；理论与 latent memory 高度相关）
- 研究标签：minimal memory、recurrent state、partial observability、information theory

## 1. 做了什么

论文问“复现指定 expert 行为所需的最小 recurrent memory 是多少”，区分当前行动所需信息与必须跨时间保存、且未来观测不能及时恢复的信息，并给出兼容关系下的精确定义。

## 2. 怎么做、实验如何设计

在兼容关系可传递时，其等价类的条件熵达到零失真的精确最小值；一般情形转化为 closed compatible state assignment 的熵最小化。sole-carrier protocol 隔离行为充分性、过剩码率及其他通道携带的信息。实验在多种 manipulation task、hidden modes 至 512、anticipatory 2→1→0 bit 场景和社区 benchmark 上训练 recurrent code，并测试 future-behavior supervision。

## 3. 结论

学习码率在 hidden modes 增长时仍接近理论 0/2 bit；最长 horizon pixel setting 的 sufficient held-out seeds 从 0/8 提至 6/8，closed-loop success 由 0.08 至 0.57。作者也强调理论 target 可达不等于易学。

## 4. Future impact

它可成为 latent memory 的理论标尺：不是问 hidden state 多大，而是问为未来行为必须跨越哪段观测缺口、保留多少比特。

## 5. Critical thinking

理论针对复现固定 expert，而 LLM agent 需学习新策略、保留语义可解释性和支持任意未来 query；最小行为记忆可能丢失日后重新规划所需信息。建议将定义扩展到多任务/可变 query/策略改进，并在语言 agent POMDP 上用可控隐藏状态验证。机构未核验也使研究背景需额外确认。

## 6. 可信度判断

- 评分：4/5
- 依据：46 页全文含定理、有限实例 certificate、合成与社区任务、seed-level 充分性结果。
- 优点：问题定义深；区分信息论下限与可学习性；实验对应理论。
- 局限：与通用 LLM memory 仍有建模距离；机构未知；固定 expert 假设较强。

