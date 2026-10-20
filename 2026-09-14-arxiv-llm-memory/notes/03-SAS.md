# 03｜SAS: Simple Attention Sparsification via End-to-End Optimization of Context Ranking

- arXiv：[2609.13141v1](https://arxiv.org/abs/2609.13141v1) · [官方PDF](https://arxiv.org/pdf/2609.13141v1) · [本地PDF](../papers/03-SAS.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Zhiwei Li , Lei Zhu , Hao Gu , Xiang Hu , Yan Wang , Haitao Mi , Sirui Han , Leo Liang , Zhijiang Guo
- 核验机构：Tencent HY LLM Frontier、香港科技大学（广州）、香港科技大学；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业实验室／强校合作。研究标签：直接相关｜context selection / memory read / sparse attention。
- 主观新颖性：4/5；证据可信度：4/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§4.3、§5、§6.3、表2–5及图7。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.13141-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

SAS研究在固定注意力预算下应读取哪些上下文块。核心观点是拟合dense attention权重不一定等于保留对最终预测最有用的上下文，因此直接用语言模型损失训练选择器。它属于记忆读取和上下文调度，不是可删除、跨会话的完整memory system。

## 2. 怎么做，实验怎么做

沿用AttnGate结构，softmax得到块门控，Top-K选择历史块；训练时将log gate加进选中块的attention logits，保留软排序梯度，并始终保留当前块。推理只使用离散Top-K，不再注入gate。作者实现融合Triton训练核与SGLang稀疏decode后端。

冻结Qwen3 4B/8B/14B主干，仅用OpenR1-Math训练selector一轮，最大序列32768、块64；跨测数学、LongBench、BFCL和VitaBench。SeerAttention-R使用相同选择器及推理后端，使监督信号比较较干净；另做OLMo3继续预训练扩展。

## 3. Conclusion：原文结论及边界

紧预算下通常优于注意力蒸馏：Qwen3-4B、2048预算的AIME24为68.85，对照55.83；14B LongBench均值55.8对54.9。4096预算BFCL 14B为44.00，接近full attention 44.50。部分任务仍下降，VitaBench的avg@4、pass@4和pass^4不可混用。单GPU稳态decode最高报告5.6×（512K、batch1），batch8在64K约13×。

## 4. Future impact：潜在影响

我的推断：可将memory retriever的训练目标从“与原注意力相似”改为“在预算约束下保留决策效用”，并延伸到文本记忆块、latent slots或多层缓存。重点是效用驱动读取，不应把训练语料中的平均有用性当成所有用户的长期重要性。

## 5. Critical thinking：我的判断与可检验拓展

论文某段把稀疏attention计算写成与总长度无关，但图7清楚显示selector要扫描全体块，Top-K在512K占90%稀疏decode耗时：完整算法不是严格O(1)。prefill仍dense，KV也仍保留，不能声称已压缩全部存储或全请求加速。应测试稀有用户事实、证据链中低注意力关键块、长度外推以及含prefill和选择器成本的端到端延迟。

## 6. 可信度、优点与不足

可信度4/5；novelty 4/5。优点是同结构监督信号对照、多尺寸多任务、真实后端及耗时分解。局限是许多结果仍属Qwen家族、选择器仅数学训练，固定预算可能遗漏后续才显现的重要信息。建议复现“同selector、同预算、同backend”比较，并报告accuracy-latency-memory三轴，避免只呈现attention kernel速度。

