# 8. Memorilla：固定 token 预算的潜在语义记忆

- 论文：[arXiv:2610.21375](https://arxiv.org/abs/2610.21375) · [官方 PDF](https://arxiv.org/pdf/2610.21375) · 本地 PDF：`2610.21375.pdf`
- 公告：2026-10-16；初次提交：2026-10-15。
- 作者/机构：PDF 首页核验 Adibvafa Fallahpour、Parsa Idehpour、Vignesh Kothapalli 等；Stanford、University of Toronto、UPenn、MIT、Vector Institute、Arc Institute。**机构优先级 P2（全球一流高校/实验室）**。
- 主题：latent semantic memory；personalized memory；agent continual learning。证据范围：全文 28 页。

1. **做了什么（论文证据）**：为冻结 LLM 提供固定数量、随查询变化的潜在记忆 token，整合整个文档集合的信息。
2. **怎么做与实验（论文证据）**：文档一次编码成可复用 embedding，学习检索并把查询相关信息放进 LLM 输入 embedding 空间；评估个性化、长文档和知识问答八个基准，以及 TextWorld 跨步记忆。
3. **结论（论文证据）**：16 个记忆 token 在八项中五项最好；FactKG 84.33%，高于完整上下文 80.43%，源文档表示 token 少 108 倍；TextWorld 成功率由全历史 ICL 的 18.6% 到 24.2%。
4. **未来影响（我的推断）**：可能成为冻结模型低开销持续积累的潜在记忆接口，尤其适合多文档综合。
5. **Critical thinking**：作者指出细粒度事实容易丢失，编码器原本并非为记忆压缩训练；应将潜在 token 与原文检索组合，测实体精确率、删除和跨模型家族迁移。
6. **可信度 4/5**：八基准及 agent 环境提供多角度证据，效率指标明确；单一主要编码/解码家族和细节遗失限制通用性。
