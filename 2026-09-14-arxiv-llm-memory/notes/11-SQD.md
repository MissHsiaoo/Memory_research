# 11｜Rethinking Heterogeneous System Disaggregation for Subquadratic Attention

- arXiv：[2609.13134v1](https://arxiv.org/abs/2609.13134v1) · [官方PDF](https://arxiv.org/pdf/2609.13134v1) · [本地PDF](../papers/11-SQD.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Arya Tschand , Yaosheng Fu , Vikram Sharma Mailthody , Nicolai Oswald , Po-An Tsai , Ritchie Zhao , Oreste Villa , Vijay Janapa Reddi , Karu Sankaralingam
- 核验机构：NVIDIA、Harvard University；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业实验室／顶级高校。研究标签：弱相关但具启发性｜memory hierarchy / subquadratic attention / serving。
- 主观新颖性：4/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§3架构概述、§5–6、附录校验说明。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.13134-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

SQD根据注意力的状态大小与访存特征划分推理，而非简单拆分attention和FFN。对稀疏attention，扫描完整KV的索引器与只读Top-K的计算应放在不同硬件；对混合模型，则区分dense层与固定状态层。对memory研究的启发是架构、读出和存储位置必须联合考虑。

## 2. 怎么做，实验怎么做

将随上下文增长的部分留在DRAM GPU并共享prefill KV，固定小状态及FFN放在SRAM型设备；用缓存、流水线和通信优化隐藏传输。真实测量在8张B200上，限制decode rank的SM以模拟低算强访存设备，另建Rubin+LPX分析模型。

工作负载含32K Chat、256K RAG、1M Agentic。比较不拆分、prefill/decode拆分、attention/FFN拆分及部分推测解码。B200执行用dummy weights，真实权重主要用于Top-K局部性trace；功耗也按代理硬件假设调整。

## 3. Conclusion：原文结论及边界

调整后的B200代理下，相对最强GPU-only基线tokens/J平均提高53%/31%/56%（三模型）。Rubin+LPX的最高3.6×吞吐来自分析模型，不是实际异构机器测得。分析模型在B200配置上的拟合误差约15%以内。论文主要支持系统设计可行性，不验证这些长上下文下的任务质量。

## 4. Future impact：潜在影响

我的推断：latent memory应同时报告状态字节数、访问模式和所需互联，而不只报告token复杂度。可把SAS的全块索引与稀疏读取分离部署，或将小型用户状态驻留快速存储，将原始证据保留在更便宜介质。

## 5. Critical thinking：我的判断与可检验拓展

关键不确定性在代理保真度：节流B200仍访问HBM，并不是真SRAM设备；从功耗中扣除代理不应承担的部分合理但依赖建模。dummy weights不能证明数值/语义行为，1M点还可能超过checkpoint训练长度。需要真实异构系统、实权重质量核验、并发调度及跨节点尾延迟测试。

## 6. 可信度、优点与不足

可信度3.5/5；novelty4/5。优点是区分测量和分析模型、明确互联开销、按attention模式设计。局限是未来硬件推算和调整功耗，容易把条件性预测误读成现成产品性能。最适合为memory architecture建立真实系统成本模型；本文没有给出可泛化的长期记忆准确率提升。

