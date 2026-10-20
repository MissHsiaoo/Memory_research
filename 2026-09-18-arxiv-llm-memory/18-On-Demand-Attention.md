# 18. On-Demand Attention: Language Models Know When to Recall

- arXiv：[论文页面](https://arxiv.org/abs/2609.20734v1)｜[官方 PDF](https://arxiv.org/pdf/2609.20734v1)｜[本地 PDF](papers/18-On-Demand-Attention-2609.20734.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Haibo Feng , Ruiqi Liang , Hanyang Peng , Shiqi Yu
- 机构：Southern University of Science and Technology；Peking University；Peng Cheng Laboratory（首页合作；非优先公司主导）。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P2｜强高校合作，较低机构排序优先级；直接相关
- 研究标签：latent recall signal；long-context memory access；conditional attention
- 入选理由：不是优先公司主导，但 PKU 合作已核验；从局部隐藏状态预测是否召回全局历史，对 latent memory access 有直接方法启发。
- 方法新颖性判断：4.5/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

ODA 采用 local-first decoding，用轻量 recall head 判断当前 token 是否值得读取完整历史 attention；只有预测有收益时才执行 global attention。主干冻结，完整历史 KV 仍保留，因而减少读取计算而非删除历史存储。核心是模型在完成全局读取之前，其局部隐藏状态已经包含一些召回收益信号。

## 2. 怎么做，实验如何设计

recall head 约 28.3M 参数，从当前 embedding、local hidden state 等预测 global-local benefit；局部配置有 4 个 attention sinks 与 2,048 窗口，训练集约 196,608 样本。质量主实验 Qwen 1.7B：RULER 16K 的 13×100 题，LongBench 13 任务 2,550 条，另有较大 Qwen/Gemma 主干。系统实现为 vLLM 的 GPU conditional execution；A100 80GB、batch 1、固定长度 continuation 的速度实验采用预设 12.5% recall schedule，虽 head 仍运行，但不是质量实验的逐步 learned routing 分布。

## 3. 结论

RULER Full 81.94、Local 19.23、ODA 81.17，global calls 41.6%；LongBench Full 37.94、Local 23.66、ODA 36.82，calls 70.6%，省读幅度依任务变化很大。速度实验 128K 从 75.54 到 149.52 token/s，约 1.98 倍，但 4K 有约 15.8% slowdown。4.12 倍 FLOPs 改善不能当 4.12 倍实测速率，预设 schedule 的 1.98 倍也不能与 learned-routing 质量数字拼成同一个端到端 operating point。

## 4. 未来影响

我的推断：latent memory 可以先学习“何时读”，而非永远检索或永远压缩；访问策略与存储内容是两个可独立优化的研究维度。未来可把 recall head 连接分层文本/latent memory，按信息需求选择访问，但这里仍保留完整 KV，尚未解决跨会话 persistence 与超长存储问题。

## 5. Critical thinking

保留全部 KV 意味着 storage footprint 并未按读次数同步下降。local step 的错误可能影响后续状态，方法不是 distribution-preserving speculative decoding。最需要补的证据是同一 learned policy 在同一质量与真实延迟设置下的 Pareto 点，而非质量和预设 schedule 各报最佳。建议用真实多会话、突发远程信息需求和分布外任务评测，并报告 head 训练标签生成成本、prefill、batching 及重复 seed。LongBench 较大模型未覆盖的结果不应补猜。

## 6. 可信度判断

可信度 3.5/5：全文质量表、系统实验设置与训练规模支持局部信号的有效性，方法洞见突出。局限是质量/速度政策不一致、KV 完整存储、硬件/batch 条件与跨模型覆盖有限。较低机构排序优先级不是低可信度结论；纳入因为可核验强高校合作及对 memory access 的清晰新机制。

