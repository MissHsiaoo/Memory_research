# 06｜阿里巴巴：让记忆写入和检索一起自演化

- 论文：[arXiv:2610.10183](https://arxiv.org/abs/2610.10183)｜[官方 PDF](https://arxiv.org/pdf/2610.10183)｜本地 `2610.10183.pdf`
- 正式公告：2026-10-08（主分类 cs.CV New submissions；cs.AI 交叉列出）；首次提交：2026-10-07 UTC，v1。作者/机构（PDF 首页）：Yongchao Xu、Bowen Ye、Jiefeng Gan、Junkai Ma、Wenzhao Li、Sen Tao、Yi Wei、Jiawei Liu；Alibaba Group、USTC、SJTU、UCAS、Beihang University。机构优先级：S；标签：multimodal memory、retrieval、self-evolving agent；直接相关。

## 1. 做了什么

长视频问答系统常把“存什么”固定，只针对问题优化“怎么找”；VideoEvolve 认为两者互相决定，提出记忆构建和检索双演化。它是多模态场景，但核心设计可迁移到 LLM 长期记忆：缺失信息再好的检索也找不到，存了信息却找不到同样无用。

## 2. 怎么做、实验如何设计

从低帧率视频总览开始，Memory Evolver 选择性补充内容，Retrieval Evolver 随问题选择在当前记忆中检索；交替做 agentic RL，一方更新时冻结另一方。Bottleneck-Aware Evolution Feedback 判断当下是写入还是取回瓶颈，Capability-Aware Feedback 降低对训练问题集的过拟合。PDF 在 Video-MME、LongVideoBench、LVBench、MLVU、MMVU 等基准报告多选准确率，并区分只用已存记忆与允许回访原视频两种协议；附录明确了不同评测集及冻结 checkpoint 的规则。

## 3. 结论

论文报告联合演化相对静态记忆/单侧调整的优势及消融支撑。这里不把不同 backbone、输入模态和回访预算的文献结果简单合成一个“统一增益”；更可信的证据来自其内部受控比较。

## 4. 未来影响（推断）

对个人化 agent，可把新对话后的记忆压缩策略与未来查询策略交替改进，并用失败归因决定下一轮应提高写入覆盖还是取回能力。

## 5. Critical thinking

写入与检索交替训练可能出现互相迎合：检索器越偏向某类问题，写入器越只存这类证据。CEF 尝试缓解但未必覆盖真实长期分布漂移。建议固定总存储、视频回访次数和推理成本，与强统一模型比较；在“未来问题未知”的严格测试中量化写入后悔值，避免训练问题泄漏。

## 6. 可信度：3/5

依据：核验 PDF 训练结构、五类视频基准和协议附录。优点是明确把记忆与检索耦合优化，并指出横向文献对比不可完全等价；局限是多阶段预算复杂、跨骨干比较不完全同条件、长期开放问题泛化仍待证实。
