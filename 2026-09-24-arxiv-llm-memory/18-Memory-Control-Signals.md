# 18. Memory Control Signals

- 论文：**Memory Control Signals Emerge Before Action in Long Horizon Agents**
- arXiv：[2609.27286](https://arxiv.org/abs/2609.27286)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Mingxuan Wang 等；TierFlow Team、人民大学、清华大学
- 机构优先级：**A｜高校强；TierFlow 身份仅按 PDF 署名，不额外推断**
- 研究标签：latent memory control、long-horizon agent、hidden state、compression/recall
- 本地 PDF：[2609.27286.pdf](./2609.27286.pdf)

## 1. 做了什么

研究代理在采取下一步动作前，隐藏状态是否已经编码“该压缩历史”或“该召回旧证据”。结果显示最终输入 token 的 hidden state 可预测两类需求，并据此构造 PAMER/PAMER+ 在线控制器。

## 2. 怎么做、实验如何设计

用离线标注把决策状态分成 compression/recall 需要，比较 context length、turn count、tool type 等可观察元数据与不同层、不同 pooling 的 hidden probes。最终状态对压缩/召回 AUROC 为 0.831/0.765；压缩信号随深度增强，召回在中层较早峰值，last-token 优于 mean pooling。系统在 WorkBuddyBench 260 题上评估；PAMER+ 将 token 从基线约 2.69M 降至 0.76M（-71.7%），平均分 +1.7 点，但不同模型/领域有正有负。

## 3. Conclusion

memory operation 需求不仅由“上下文太长”决定，而已进入模型的任务状态表示；近期上下文可承载工作状态，但远程依赖恢复仍需要选择性原始证据。

## 4. Future impact

支持 latent memory controller：用内部状态触发 compress/retrieve，而不是固定窗口或周期。也提示 recall probe 与 compression probe 可能应来自不同层。

## 5. Critical thinking

论文最有价值的是区分压缩与召回的层级形成过程。probe 可预测并不等于模型“因果地拥有”控制信号，hidden state 可能只是相关特征；在线控制器只真正用压缩头，召回 probe 更多是分析。跨 backbone 时 GPT-5.6-Luna 出现质量下降，说明策略不稳。建议 activation intervention、跨模型 probe transfer、真正在线 recall gate 和置信度校准。

## 6. 可信度判断

**4/5。** 已阅读全文；分组划分、层级探针、系统级 benchmark 和跨模型测试较完整。因果性尚未建立，且同系列论文共享数据/管线，应避免把它当独立重复证据。
