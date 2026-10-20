# 13 — SelfSearch: Reward-Free Search for Self-Improving Agents

- arXiv：[2609.37968](https://arxiv.org/abs/2609.37968)；[官方 PDF](https://arxiv.org/pdf/2609.37968)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Jungwoo Yang、In Jin Kong、Yohan Jo；Seoul National University
- 机构优先级：**A**；研究标签：`self-evolving agent` `episodic memory` `harness search`
- 证据范围：阅读全文；本地 PDF：[2609.37968.pdf](./2609.37968.pdf)

## 1. 做了什么

不靠下游任务 reward 搜索更好的 agent，而让后续修改者阅读过去“如何修改 agent”的 episode record，从自我改造经验中继续进化。

## 2. 怎么做、实验如何设计

记录此前修改尝试的推理、工具调用、观察与结果，用它指导下一代 instruction/tool/procedure 编辑。六个模型—基准组合的群体均值都超过初始 agent；单 agent 在 Terminal-Bench 2.1 最多 +11.2 分；SWE-bench Multilingual +5 分且共同解出任务成本降 38.5%。搜索成本 $4.03 时，以 DeepSeek V4 Flash 得到 82% Terminal-Bench harness。

## 3. Conclusion

修改 agent 的过程本身就是可复用经验，不一定要每次用昂贵下游评测来生成搜索反馈。

## 4. Future impact

它给 self-evolving memory 一个新对象：不仅存任务经验，也存“如何改造自己的工具和流程”的元经验。

## 5. Critical thinking

reward-free 只发生在候选生成阶段，最终仍需下游评测判断好坏；因此它减少而非消除 evaluation dependence。个别强结果也可能来自 benchmark/harness 工程匹配。应做多随机种子、盲测试集、跨模型/跨任务 transfer，以及与相同总美元预算的 evaluation-guided search 对照。

## 6. 可信度判断

**4/5。** 覆盖三基准和多执行模型，成本与成功率均有报告。局限是独立搜索方差、长期退化和安全边界尚未充分，最强 82% 是公开九 harness 设置中的条件性比较。
