# 10. Looped-Flows

Thinking with Looped Flows

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11801v1](https://arxiv.org/abs/2609.11801v1) · [官方 PDF](https://arxiv.org/pdf/2609.11801v1) · [本地 PDF](../papers/10-Looped-Flows.pdf)
- 首次提交：2026-09-10T16:52:54Z（UTC，与公告日不是同一概念）。
- 作者：Ayhan Suleymanzade, Chanhyuk Lee, Floor Eijkelboom, Nicholas M. Boffi, İsmail İlkan Ceylan, Jinwoo Kim
- 机构：EPFL、KAIST、Amsterdam、CMU、TU Wien、AITHYRA、Oxford（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：相邻强启发｜潜在循环推理 / diffusion-style training
- 原文定位：§3–5，PDF 第 7–9 页、表 1/2。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

用局部去噪目标训练循环隐状态，使每次更新在仅短程反传的条件下仍有利于后续推理。

## 2. 怎么做的，实验怎么做

通过递减噪声和共享噪声将局部目标串联；推理把 denoiser 对应的概率流速度与 recurrent state 联合积分，更细时间网格提供更多计算，不同初始噪声产生多解。

实验与结果：5–7M 参数，Sudoku、Maze、ARC-AGI-1/2，以及多解 N-Queens、Graph Coloring。三种子；表 1 的 ARC 指标明确为 pass@2，不是单次准确率：58.8±1.8 / 12.2±1.9。Sudoku 97.9±0.4；Maze 86.7±1.1，并非每项优于所有对手。多解覆盖用 20 次推理。

## 3. Conclusion

在结构化推理小模型上，flow 与递归联合训练有效；它不是自然语言 diffusion LLM 的直接验证。

## 4. Future impact

可尝试将 latent memory 更新理解成有噪声的迭代纠错，而非一次写入后固定；与 ICL 的少样例结构推断有连接。

## 5. Critical thinking：优点、问题与可验证拓展

优点是三种子、多解任务、flow/recurrence 消融。局限是不同论文 baseline 与推理预算可能不完全对齐；ARC pass@2、单轨迹和 ensemble 要区分；不能由谜题性能推断长期个人记忆。建议用相同更新次数/FLOPs 比较循环状态纠错与直接读写。可信度 4/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**4.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**4/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

