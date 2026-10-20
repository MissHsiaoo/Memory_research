# 08｜Looped Transformer 的共享 KV 记忆

- 论文：[arXiv:2610.02383](https://arxiv.org/abs/2610.02383)｜[官方 PDF](https://arxiv.org/pdf/2610.02383)｜本地：`2610.02383.pdf`
- arXiv 正式公告：2026-10-05；首次提交：2026-10-01。
- 作者/机构：首页核验 Giovanni Monea 等；IBM Research、Cornell University。
- 机构优先级：S；标签：latent/context memory、递归 Transformer、KV 缓存。关联性：直接于模型内部记忆，弱于用户长期记忆。

## 1. 做了什么

论文让循环 Transformer 各轮复用第一轮写入的 KV cache，而不是每轮都写一套；后续轮仅保留短本地窗口。

## 2. 怎么做、实验如何设计

作者预训练 LPT 与混合变体 H-LPT，在 150M–1B 规模、FineWeb-Edu、4,096 token 上比较标准 Transformer 和普通 looped 模型。五轮循环时，混合模型对同参数标准 Transformer 的验证 perplexity 低 1.12–1.82，context memory 降 76–79%。PDF 还分析共享/本地表征及梯度通路。

## 3. 结论

在该预训练设置，跨循环共享 KV 不仅省内存，而且改善验证困惑度；这是架构级短期状态共享，不应误称为跨会话 Agent 记忆。

## 4. 未来影响（推断）

可启发小容量 latent memory：优先让不同计算轮次读取共同状态，而不线性复制状态副本。

## 5. Critical thinking

论文局限明确：五轮时解码 FLOPs 为标准模型约 4.3–4.8 倍，仅同参数而非同 FLOPs 比较；未测长上下文任务，规模止于 1B。应报告同延迟/功耗下质量，测试局部窗口长度、动态循环次数和跨任务记忆干扰。

## 6. 可信度：4/5

依据：已查 PDF 架构、数据/规模、局限章节。优点是报告算力代价并做机理分析；局限是效率优势目前偏向显存维度，真实服务收益未定。
