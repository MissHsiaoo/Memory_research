# 19 — In-Context Learning Amplifies a Latent Symbolic Circuit

- arXiv：[2609.36265](https://arxiv.org/abs/2609.36265)；[官方 PDF](https://arxiv.org/pdf/2609.36265)
- v1 提交：2026-09-28；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Melissa Wessel；Independent Researcher
- 机构优先级：**B（黑马/启发性补充）**；研究标签：`in-context learning` `mechanistic interpretability` `latent circuit`
- 证据范围：阅读全文；本地 PDF：[2609.36265.pdf](./2609.36265.pdf)

## 1. 做了什么

追踪抽象—归纳—检索三阶段符号电路随 shot 数增加如何启动，主张 ICL 更多是在放大权重中已有电路，而非临时构造新算法。

## 2. 怎么做、实验如何设计

在 Gemma2-2B、Llama3.1-8B、Qwen3-4B 的 ABA/ABB 任意 token 规则上做 causal mediation、cross-shot activation patching、head ablation 与 function-vector injection。单 head 因果贡献从 1-shot 到 10-shot 最多 8×；10-shot activation patch 到 0-shot/1-shot 可把准确率从 1%→56%、17%→88%；0-shot 注入 function vector 最高恢复到 86%，但依赖完好的 downstream retrieval stage。

## 3. Conclusion

示例像是向一个预存 symbolic pathway 提供信号；电路在低准确率阶段已经存在，随着示例增加主要增强而非更换拓扑。

## 4. Future impact

这为 ICL、function vector、latent memory 提供统一视角：上下文可能主要负责寻址和激活已有计算结构，可指导更轻量的 memory steering。

## 5. Critical thinking

机构优先级低，且任务本质是简单三列复制规则；论文明确承认 contrastive CMA 会漏掉两规则共享的基础设施，丰富推理上的泛化未知。需要在组合程序、自然语言任务和跨层非线性交互上复现，避免把单一电路案例概括为全部 ICL。

## 6. 可信度判断

**3.5/5。** 干预证据比相关性分析强，跨三模型方向一致；但单作者、ICML workshop 接收、窄任务和未覆盖复杂 ICL 使外推置信度有限。
