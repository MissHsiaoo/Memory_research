# 10. FINDERS：扩散状态路由的场景自适应用户表征

- **arXiv**：[2610.22400](https://arxiv.org/abs/2610.22400)；[官方 PDF](2610.22400.pdf)
- **提交日期**：2026-10-14（v1）。
- **作者/机构**：Junru Zhang 等。PDF 首页核验：Zhejiang University、Ant Group。
- **机构优先级**：P1（大型产业实验室与高校）。**研究标签**：diffusion LLM；个性化用户表征；场景路由。
- **相关性说明**：属于用户个性化/扩散 LLM，相邻记忆研究，但不是显式长期 memory store。
- **证据范围**：完整 PDF，9 页；文件可解析。

## 1) 做了什么

提出 FINDERS，用扩散语言模型不同 denoising state 表达用户行为日志的不同粒度，再由场景 query 路由到所需的用户表征方向。

## 2) 怎么做、实验如何设计

四步为 denoise、factorize、route、compress。learnable meta-slots 分离跨模态语义和模态特定行为因子；BehaviorQA 提供显式行为 rationale；轻量 router 按场景强调 slot 方向，之后融合并压缩为表示。论文报告多任务离线实验及十个产业场景在线 A/B test，与现有 user encoder 比较统一和场景自适应表现。

## 3) 结论

作者报告在十个在线场景持续优于 state of the art 方法。本文适合作为个性化表征与 diffusion LLM 候选方向，不应误读为验证了长程记忆检索或遗忘能力。

## 4) 未来影响

扩散模型可不止用于并行生成：双向去噪可能把异质行为线索融合成按任务切换的用户表示，对推荐、风险等应用有启发。

## 5) Critical thinking

- **关键假设**：不同 noise/denoising state 具有稳定的行为粒度语义；router 能根据下游场景选到泛化有用而非过拟合的槽位。
- **差别**：将 dLLM 的中间去噪状态当作多粒度用户表征空间，并通过 query-conditioned slot routing 场景适配。
- **风险**：线上 A/B 的流量分配、业务指标、置信区间和具体收益若不透明，难判断效果规模；BehaviorQA rationale 也可能把标注逻辑写入模型。
- **后续建议**：共享 anonymized 数据/任务切分；报告不同用户群的收益和负效应；评测跨场景、冷启动与长期用户行为漂移；与等规模 autoregressive user encoder 做严格预算对照。

## 6) 可信度判断

**3.5/5。** 依据：全文说明方法与多场景实验，PDF 首页机构可核验；用户表示征有效但与 memory system 直接证据有边界。优点是有在线 A/B；局限是论文摘要未展示量化值、收益透明度与其他场景复现尚有限。
