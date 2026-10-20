# 6. MARS：会话级助手的记忆感知路由

- **arXiv**：[2610.23583](https://arxiv.org/abs/2610.23583)；[官方 PDF](2610.23583.pdf)
- **提交日期**：2026-10-16（v1）。
- **作者/机构**：Minghan Wang 等。PDF 首页核验：Southern University of Science and Technology、City University of Hong Kong、CUHK-Shenzhen、Harbin Institute of Technology (Shenzhen)。
- **机构优先级**：P1（多所研究型大学）。**研究标签**：长期助手；记忆构造；在线模型路由；质量/成本。
- **证据范围**：完整 PDF，32 页；文件可解析。

## 1) 做了什么

提出 MARS，主张记忆选择与模型路由不应各自优化：记忆改变输入证据和干扰难度，模型选择也应依赖当前记忆/会话状态。QTM 作为共享控制接口。

## 2) 怎么做、实验如何设计

Query and Topic Manager 从会话估计 query type、阶段、记忆需求/跨度、歧义/风险等状态，控制记忆视图（scope、top-k、最近性）并提供 router 特征；在线路由以 LinUCB 风格 contextual bandit 更新，turn-level judge 反馈与生成成本组成 utility。RealMem 与 MultiChallenge 各比较 16 个系统配置；论文将 controller 与 generator API 费用一起记账，但本地存储/计算/延迟没有定价。

## 3) 结论

RealMem 上保留 full-context GPT-4o QA 的 98.2%，同时 generation + controller API cost 为其 14.5%；MultiChallenge 总体落后最强静态系统，但在机制重点子集上以更低成本接近。故结论是场景相关的质量—记忆—成本折衷，而非所有任务都胜出。

## 4) 未来影响

将“记忆曝光量”纳入模型选择策略，提示未来助手可根据任务阶段、歧义与记忆依赖程度动态控制检索、上下文长度和模型规模。

## 5) Critical thinking

- **关键假设**：QTM 的结构化状态足以表达会话中与难度相关的决策信息；turn-level judge reward 与真实用户效用一致。
- **差别**：联合决策 interface 是核心，不是单做更好的 memory 或更强 router。
- **风险**：QTM 调用与判分器增添成本；论文明确本地算力、存储、工程时间未计费，实际节省可能缩小。MultiChallenge 整体落后也说明共享状态并非普适优势。
- **后续建议**：对 QTM 错判、模型集合、成本权重、用户效用做部署敏感性分析；在真实交互中按延迟、内存、隐私等完整成本计量，并评测状态错误造成的累积影响。

## 6) 可信度判断

**4/5。** 依据：完整实验矩阵、成本口径、状态 schema、敏感性/消融及失败案例均可查。优点是报告 controller API cost 并明确 MultiChallenge 负面总体结果；局限是本地计算不计价、judge 反馈而非在线用户评价、部分结果受机制子集筛选影响。
