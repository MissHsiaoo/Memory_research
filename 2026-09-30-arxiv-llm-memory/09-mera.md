# 09 — MERA: Learning to Retrieve Missing Evidence for Long-Term Memory QA

- arXiv：[2609.37443](https://arxiv.org/abs/2609.37443)；[官方 PDF](https://arxiv.org/pdf/2609.37443)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Yi-Xuan Deng 等；Tsinghua University、JD.COM
- 机构优先级：**A+**；研究标签：`long-term memory` `retrieval planning` `evidence graph`
- 证据范围：阅读全文；本地 PDF：[2609.37443.pdf](./2609.37443.pdf)

## 1. 做了什么

针对问题本身缺少检索线索的情况，让已经找到并验证的证据反过来生成下一轮搜索方向。

## 2. 怎么做、实验如何设计

MERA 分离全局可检索记忆和问题专属 evidence state，用 verifier gate 维护证据图；0.6B planner 通过 RL 奖励“找回此前缺失证据”的 query。LoCoMo/LongMemEval-S 上，以 Qwen3-30B 做证据处理与回答时，准确率为 77.40%/71.29%，比未做 retrieval-grounded 训练的 30B planner 高 4.10/3.96 分；LoCoMo 多轮累计证据召回从 55.5% 增至 80.5%。

## 3. Conclusion

检索策略的状态应包含已确认的局部证据，而不只包含原问题；小 planner 的针对性训练可胜过单纯扩大 planner。

## 4. Future impact

适合个人历史、会议记录和 agent episodic memory 中的多跳事实追踪，并可降低大模型反复规划成本。

## 5. Critical thinking

论文的一个诚实结果是：在 flat-evidence 变体中，小 planner 对大 planner 的优势并不保持，说明收益与 graph-assisted workflow 绑定。需要进一步隔离 graph、verification 与 RL 各自贡献，并评测错误证据进入 state 后的级联偏差和动态记忆更新。

## 6. 可信度判断

**4.5/5。** 两个主流记忆 QA 基准、两种回答 backbone、证据召回与答案准确率都有报告，并主动披露不利变体。局限是自动验证和合成式 QA 仍无法覆盖真实长期对话的歧义。
