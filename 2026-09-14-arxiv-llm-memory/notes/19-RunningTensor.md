# 19｜RunningTensor: Generalizing Linear Attention to Higher-Order Recurrent States

- arXiv：[2609.12814v1](https://arxiv.org/abs/2609.12814v1) · [官方PDF](https://arxiv.org/pdf/2609.12814v1) · [本地PDF](../papers/19-RunningTensor.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Luca Herranz-Celotti、Ermal Rrapaj、Vincent Guigue（PDF；列表仅两人）
- 核验机构：ISIR Sorbonne、Berkeley Lab（PDF署名）；依据为所下载PDF首页署名。
- 机构优先级：B｜强研究机构；机构已核验但稿件证据不完整。研究标签：直接相关｜latent memory / higher-order state / associative recall。
- 主观新颖性：4.5/5；证据可信度：2.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§2–3、表1–2、完整结果段；第6页视觉核验。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12814-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

RunningTensor把线性attention的矩阵状态扩展为高阶tensor，使用rank-1外积写入、多个query向量收缩读取；order2恢复线性attention，实验重点是order3。它在结构上扩大关联记忆表达能力，是latent memory值得讨论的新方向。

## 2. 怎么做，实验怎么做

三阶delta rule结合遗忘门、归一化query/key、低参数通道投影ConcOnlyC和并行训练形式。MQAR在d_model128、长度1024/2048/4096测试；每格报告3个seed与三个学习率中的最佳validation F1，不是均值及独立test成绩。

方法段还写0.6B、FineWeb-Edu100BT的预训练配置，但当前PDF的结果部分只有MQAR主表与组件消融，未提供摘要宣称的真实语言理解/非合成检索结果表。第6页视觉确认Conclusion只有标题后直接进入References。

## 3. Conclusion：原文结论及边界

MQAR三个长度均100% F1，表中每层非embedding参数176K，少于attention934K。但时延311.9ms虽低于attention333.5和DeltaNet355.7，却高于Mamba252.5、GLA267.2；不能泛称比所有SSM都快。当前可支持的结论限于该合成协议下的容量与组件效果，不能确认真实任务增益。

## 4. Future impact：潜在影响

我的推断：将用户、实体、关系等因素映射为多路query，可能比矩阵记忆更自然表达高阶绑定关系。值得研究低秩tensor、稀疏读写及容量分配，而不是直接把状态维度增加等同于信息利用效率提升。

## 5. Critical thinking：我的判断与可检验拓展

O(W^3)容量同样意味着随宽度更快增长的状态字节和计算，等参数并不等状态内存。最佳seed/学习率选择可能高估稳定表现，需要独立test及均值方差。作者元数据也有不一致：列表仅两位作者，PDF另列Ermal Rrapaj及Berkeley Lab；这里按PDF报告并保留差异，不把Berkeley Lab混同UC Berkeley。

## 6. 可信度、优点与不足

可信度2.5/5；novelty4.5/5。优点是可推导结构、MQAR对照及矩阵/张量消融。主要缺点是公开稿结果不完整、空结论、最佳validation报告、状态容量未等预算。保留为高新意但待补证工作，不因机构署名给高分；优先复现等state bytes的MQAR，再等真实任务表和完整代码，不直接据摘要展开强结论。

