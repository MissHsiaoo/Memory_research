# Flash-dLLM：面向 I/O 的 KV 缓存与并行去噪

- arXiv：[2609.26796](https://arxiv.org/abs/2609.26796)；[官方 PDF](https://arxiv.org/pdf/2609.26796)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Quan Nguyen-Tri 等；VILA Lab, MBZUAI
- 机构优先级：A（强研究型高校、直接相关）
- 研究标签：diffusion LLM、KV cache、parallel decoding、systems

## 1. 做了什么

论文指出 dLLM KV cache 的主要瓶颈可能是 GPU memory I/O，而非算力，提出训练无关的 Flash-dLLM，将 fused cache kernel 与模型自身 draft-and-verify 并行解码结合。

## 2. 怎么做、实验如何设计

系统融合 position gather、projection 与 cache 操作以减少中间张量搬运；依据 attention 稀疏性选择高影响 token，并利用置信度提升可提前接受的 token 数，让同一个 dLLM 同时做 drafter/verifier。作者在 LLaDA 系列的 GSM8K、MATH、MBPP、HumanEval 上比较近期 cache/decoding baselines，测速度、显存效率、不同 batch/sequence 和生成质量。

## 3. 结论

PDF 报告相对此前强基线 Elastic-Cache，在 GSM8K 与 HumanEval 分别达到 5.1× 和 11.0× speedup，同时保持任务质量并改善长序列/大 batch 扩展性。

## 4. Future impact

扩散 LLM 若要进入在线 agent，cache 与去噪调度必须联合设计。其选择性 cache 也提示 latent memory 可按“对当前预测的边际影响”动态驻留。

## 5. Critical thinking

系统论文的速度比高度依赖 GPU、kernel 实现、baseline 版本和 batch 设置。需要端到端 latency、吞吐、能耗以及同一编译栈下的复现；attention top-k 不必等于因果重要性，在长程依赖任务中可能丢掉低权重关键 token。建议加入 needle/long-context stress tests 和不同硬件。

## 6. 可信度判断

- 评分：4/5
- 依据：21 页全文包含 kernel 动机、算法、多个任务与系统指标，并给出代码链接。
- 优点：直接解决部署瓶颈；算法与系统联合优化；增速明显。
- 局限：硬件依赖强；当前公开摘要中的质量保持证据需结合完整表格复核。

