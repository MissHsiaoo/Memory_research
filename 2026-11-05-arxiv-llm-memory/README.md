# 2026-11-05 arXiv LLM Memory 日报

已完成本日选编：20 篇中文评析、20 份官方 PDF。机构排序与证据可信度独立；没有仅凭摘要给予高分。

## 批次、时间与筛选口径

本轮于北京时间 2026-11-05 08:10 触发，官方 cs.CL/cs.AI/cs.LG 及随后下载的 cs、stat.ML 列表均明确显示 **Thursday, 5 November 2026**。以实际可见的列表日期为批次依据，不用预计公告时刻否定页面事实，也不把提交时间等同公告时间。触发时刻换算为 UTC 00:10、美国东部标准时间前一日19:10；本报告不声称知道每篇实际上线的精确时刻。PDF首页可能写11月3日或4日，那是提交/文稿日期，不据此排除当日正式新论文。

官方入口：[cs](https://arxiv.org/list/cs/new)、[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)、[stat.ML](https://arxiv.org/list/stat.ML/new)。动态页面会变化，本地 evidence/ 保留本轮 HTML 与去重清单。仅取 New submissions，不取 Cross-lists 或 Replacements；五类别去重得到755篇新论文。对记忆、个性化、上下文、扩散语言模型和代理经验候选做题目/摘要初筛，下载34篇候选PDF后核查首页与重点正文，最终达到20篇目标。没有向旧批次扩展，也未修改其他日期。

优先级采用本日报的工作分层，并非大学排名：A1为用户优先产业研究机构（含Amazon/AWS），A2为有一流研究型高校/实验室署名的工作；同层再看直接相关性、方法新颖性和证据。A2末尾明确保留两篇跨方向启发性工作。合作论文按所核验的强机构归层，不将同文独立作者臆测为该机构雇员。本日无需低机构优先级黑马补足。

## 入选排序

| 排名 | 论文与核验链接 | PDF署名机构 | 层级 | 相关性 | 证据分 |
|---|---|---|---|---|---|
| 1 | [LifeVal](01-LifeVal.md) · [arXiv](https://arxiv.org/abs/2611.06687) | OpenAI | A1 | 直接 | 3/5 |
| 2 | [Route-to-Remember](02-Route-to-Remember.md) · [arXiv](https://arxiv.org/abs/2611.05636) | Amazon；George Washington University | A1 | 直接 | 4/5 |
| 3 | [PEARL](03-PEARL.md) · [arXiv](https://arxiv.org/abs/2611.05842) | AWS | A1 | 直接 | 3/5 |
| 4 | [SEED](04-SEED.md) · [arXiv](https://arxiv.org/abs/2611.06084) | NVIDIA | A1 | 直接 | 4/5 |
| 5 | [RAGCompass](05-RAGCompass.md) · [arXiv](https://arxiv.org/abs/2611.05596) | Meta；Georgia Institute of Technology；University of Virginia | A1 | 直接 | 3/5 |
| 6 | [Split-KV](06-Split-KV.md) · [arXiv](https://arxiv.org/abs/2611.05926) | ByteDance Seed；National University of Singapore；Stanford University | A1 | 直接 | 4/5 |
| 7 | [Coca-Cola](07-Coca-Cola.md) · [arXiv](https://arxiv.org/abs/2611.06500) | Tsinghua University / Tsinghua AI Agent Group | A2 | 直接 | 3/5 |
| 8 | [SUMONE](08-SUMONE.md) · [arXiv](https://arxiv.org/abs/2611.06445) | Peking University | A2 | 直接 | 4/5 |
| 9 | [Pro-Memory](09-Pro-Memory.md) · [arXiv](https://arxiv.org/abs/2611.05731) | UIUC；University of Illinois Chicago；Stony Brook University；Brookhaven National Laboratory | A2 | 直接 | 4/5 |
| 10 | [ReScopeBench](10-ReScopeBench.md) · [arXiv](https://arxiv.org/abs/2611.05450) | HKUST；Huawei；Guangdong Laboratory of Artificial Intelligence and Digital Economy (SZ) | A2 | 直接 | 4/5 |
| 11 | [EvoGuard](11-EvoGuard.md) · [arXiv](https://arxiv.org/abs/2611.06444) | JD.com；Sun Yat-sen University；University of Melbourne；HKUST | A2 | 直接 | 4/5 |
| 12 | [PMRecBench](12-PMRecBench.md) · [arXiv](https://arxiv.org/abs/2611.06349) | University College London；University of Amsterdam | A2 | 直接 | 4/5 |
| 13 | [LExMem-LExGraph](13-LExMem-LExGraph.md) · [arXiv](https://arxiv.org/abs/2611.06414) | MBZUAI；Monash University；Hefei University of Technology | A2 | 直接 | 3/5 |
| 14 | [RoboCasa-Mem](14-RoboCasa-Mem.md) · [arXiv](https://arxiv.org/abs/2611.06475) | USTC；Tongji University；CUHK；Anhui University；Nanjing University | A2 | 直接 | 3/5 |
| 15 | [LooM](15-LooM.md) · [arXiv](https://arxiv.org/abs/2611.06835) | BUPT；Zhongguancun Academy；Peking University；Kling Team | A2 | 直接 | 3/5 |
| 16 | [SpecCompact](16-SpecCompact.md) · [arXiv](https://arxiv.org/abs/2611.06876) | New York University | A2 | 直接 | 3/5 |
| 17 | [ProcessPrefBench](17-ProcessPrefBench.md) · [arXiv](https://arxiv.org/abs/2611.06065) | Fudan University；Independent Researcher | A2 | 直接 | 3/5 |
| 18 | [D3D](18-D3D.md) · [arXiv](https://arxiv.org/abs/2611.06425) | Fudan University；Shanghai Innovation Institute；Shanghai Academy of AI for Science；Nanjing University；Huawei | A2 | 直接 | 4/5 |
| 19 | [Sekai](19-Sekai.md) · [arXiv](https://arxiv.org/abs/2611.06685) | USTC；National University of Singapore | A2 | 启发性 | 3/5 |
| 20 | [LIBRA](20-LIBRA.md) · [arXiv](https://arxiv.org/abs/2611.05445) | Brown University；University of Southern California | A2 | 启发性 | 3/5 |

## 机构分布

按合作署名出现次数统计，可重复计入：Amazon/AWS 2，OpenAI 1，NVIDIA 1，Meta 1，ByteDance Seed 1；Peking University 2，HKUST 2，USTC 2，National University of Singapore 2，Fudan University 2，Huawei 2。其余覆盖清华、UIUC/UIC、Stony Brook/Brookhaven、Stanford、Georgia Tech/UVA、UCL/Amsterdam、MBZUAI/Monash、NYU、Brown/USC等，完整署名见逐篇笔记及 verification.json。上述是入选集合分布，不代表当天全部论文的机构份额。

## 主题趋势（仅针对本日入选集合）

1. **记忆效用从召回走向行动与更新。** ReScopeBench、Pro-Memory、RoboCasa-Mem分别暴露经验过期、触发时机和任务恢复问题；正确记录不保证正确执行。
2. **多目标评测不能被单一均分替代。** LifeVal重最终个人任务，PMRecBench区分查询条件/历史偏好，ProcessPrefBench区分偏好分/事实可靠性。提升一项可能伤害另一项。
3. **不同记忆介质的成本结构分化。** Route-to-Remember对比写入参数与文本检索；Coca-Cola对齐行动而非原文；SEED与LooM拆开写入和读取。不要把token、显存、GPU时和端到端收益混为一谈。
4. **自演化需要防退化机制。** EvoGuard的离线效用学习与LIBRA的执行验证提供不同检查方式，但都不构成无限时域的正确性保证。
5. **扩散模型在代理基础设施上出现明确落点。** Split-KV优化训练通信，D3D优化异步草稿；分别受离线特征提取边界及额外GPU资源约束。

## 当天最值得深读的 3 篇

- **Route to Remember（02）**：直接回答参数记忆与文本记忆何时互补，含年龄分层、拒答和冲突负结果；适合设计存储分工与读写成本实验。
- **Tools Need Not Speak in Text / Coca-Cola（07）**：与 latent memory 最直接，行动分布保持提供了不同于重建的训练目标；值得进一步检验下一步保真是否损害未来多目标使用。
- **ReScopeBench（10）**：有真实可执行任务流、局部无通知变化和记忆claims追踪，适合验证自演化记忆能否保留仍有效知识并修订过期规则。

若优先研究多目标记忆benchmark，先读 PMRecBench（12：需求与偏好）、RoboCasa-Mem（14：交错任务）、Pro-Memory（09：未来意图）及LifeVal（01：个性化端到端），不要把它们当成同一任务的可直接比较排行榜。

## 候选取舍与证据边界

额外查阅首页的候选包括CCDWIKI、SRRM、FlyHash、Weaver、EchoKV、Reglos、MPRBench、DELTA、拒答对齐压缩、ADAPTITEST、推荐潜在推理、自写摘要策略污染、多语言非参数关系推理和混合LLM稀疏解码。未入选不等于质量差：本轮优先满足强机构及直接主题覆盖，有限名额下未以更弱机构候选取代已核实的强相关工作。候选SRRM全文文字抽取遇到字符编码错误，未将其当作已完成全文评析或入选论文；其余候选未全部做同等深读。

所有入选PDF均成功下载；每篇记录实际重点阅读页码。完整PDF的取得/解析不等于全文每页已逐行读完，未运行作者实验，未逐条验证所有数学证明。表中3/5与4/5是本轮证据判断，不是机构评分或发表状态。笔记第4节及研究建议明确为评阅推断，结果数值来自所读正文/表格。

## 文件核验

- pdf/：20份官方原文，保留未修改字节；SHA-256、页数、作者、首次提交日期与版本记录见 verification.json。
- evidence/：5份官方列表快照、完整去重catalog、20份摘要页，便于复核当日入选资格。
- 每篇笔记均含指向实际PDF的相对链接；同步时保持目录结构。
- 仓库同步完成状态以远端提交核验为准，本文件不预先声称push成功。
