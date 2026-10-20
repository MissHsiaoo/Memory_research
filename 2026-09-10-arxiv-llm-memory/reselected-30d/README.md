# 2026-09-10 arXiv 重选版：机构优先，近 30 天 20 篇

本版替代今日初版 7 篇的推荐名单。**已收录 20 篇论文、20 份官方 PDF、20 份中文批判性笔记。** 每篇均核查原文署名，以及方法、实验和关键局限；没有把摘要阅读写成全文复现。

## 范围与选择口径

- 今天的特例：首次提交日期为 **2026-08-12 至 2026-09-10（UTC，含首尾 30 个日历日）**，以检索时已公开记录为限。版本更新不改变首次提交资格。
- 从 cs.CL / cs.AI / cs.LG 中，以 memory、personalization、personalized、in-context、diffusion language、self-evolving、latent、test-time、continual 等关键词检索并去重，得到 **3,047 条候选记录**；先做元数据筛选，再对优先候选核验原文。不是对全部 arXiv 学科的穷尽性检索，也不是逐篇精读全部候选。
- 遵循你的偏好：**强机构优先；同层级再综合主题相关性、novelty 和启发价值排序。** 相邻方向被明确标出。这里的机构优先级是研究选刊偏好，不是学校综合排名；并不意味着其他机构的成果质量一定较低。
- 下列机构来自原文作者单位/首页标识，不由使用了哪个公司的模型推断。Proteus 是 Google Research / Mila，不写成 DeepMind；Prefix-Sliding 不因作者个人经历写成 OpenAI。本期没有为了填入 OpenAI / Anthropic 标签而收录仅使用其模型的论文。
- novelty / 证据可信度分别按 1–5 主观评分，**不是概率**。novelty 是本次阅读判断，未完成全量先行工作审计；可信度考虑对照、数据切分、统计与可核查程度，独立于机构声誉。4 分也不代表独立复现成功。

## 20 篇主榜

“首次”列为首次提交月日；点击标题读中文笔记，点击 PDF 读原文。完整作者、机构核验说明、版本链接和证据定位在单篇笔记中。

| 排名 | 首次 | 论文与文件 | 主要署名机构（简写） | 与你方向的关系 | novelty / 可信度 |
|---|---|---|---|---|---|
| 1 | 08-17 | [Proteus](notes/01-Proteus.md) · [PDF](papers/01-Proteus.pdf) | Google Research、Mila | 直接：latent/recurrent memory | 4.5 / 4 |
| 2 | 08-27 | [Fast-Weight-Attention](notes/02-Fast-Weight-Attention.md) · [PDF](papers/02-Fast-Weight-Attention.pdf) | ByteDance Seed、Princeton、清华 | 直接：fast-weight memory / ICL | 4.5 / 3.5 |
| 3 | 08-25 | [Recuris](notes/03-Recuris.md) · [PDF](papers/03-Recuris.pdf) | NUS、Stanford、Oxford、Princeton | 直接：self-evolving agent memory | 4.5 / 3.5 |
| 4 | 08-20 | [Scaffolding-Minds](notes/04-Scaffolding-Minds.md) · [PDF](papers/04-Scaffolding-Minds.pdf) | Google DeepMind、UCSD | 相邻：潜在空间视觉推理 | 4.5 / 3.5 |
| 5 | 09-01 | [MemoryWalker](notes/05-MemoryWalker.md) · [PDF](papers/05-MemoryWalker.pdf) | Alibaba、TokenFoundry | 直接：memory harness 的训练对齐 | 4.5 / 4 |
| 6 | 08-18 | [Chain-of-Experience](notes/06-Chain-of-Experience.md) · [PDF](papers/06-Chain-of-Experience.pdf) | ByteDance Seed、UCSC | 直接：经验反馈 / ICL | 3.5 / 3.5 |
| 7 | 08-15 | [Evo-Harness](notes/07-Evo-Harness.md) · [PDF](papers/07-Evo-Harness.pdf) | Amazon、UIUC 等 | 直接：经验到技能记忆 | 4 / 3.5 |
| 8 | 08-18 | [MoNe](notes/08-MoNe.md) · [PDF](papers/08-MoNe.pdf) | Qualcomm | 直接：参数化长期记忆 | 4 / 3 |
| 9 | 08-17 | [Benchmark-as-Teacher](notes/09-Benchmark-as-Teacher.md) · [PDF](papers/09-Benchmark-as-Teacher.pdf) | NVIDIA、UCSC | 相邻：benchmark 驱动自演化 | 4 / 2.5 |
| 10 | 08-13 | [AdsWorldEngine](notes/10-AdsWorldEngine.md) · [PDF](papers/10-AdsWorldEngine.pdf) | Microsoft | 弱相关启发：线上 agent 工具演化 | 4 / 3 |
| 11 | 08-16 | [UI-Mate](notes/11-UI-Mate.md) · [PDF](papers/11-UI-Mate.pdf) | Tencent Hy Frontier | 相邻：GUI agent 的 demonstration ICL | 4 / 3 |
| 12 | 09-04 | [WearableQA](notes/12-WearableQA.md) · [PDF](papers/12-WearableQA.pdf) | Meta、KAIST、Korea University | 直接：个人长期可穿戴记忆评测 | 3.5 / 3.5 |
| 13 | 08-26 | [Survival-Length-Control](notes/13-Survival-Length-Control.md) · [PDF](papers/13-Survival-Length-Control.pdf) | Huawei Noah、Université de Montréal | 直接：diffusion LLM 推理 | 4 / 3 |
| 14 | 08-12 | [MARCH](notes/14-MARCH.md) · [PDF](papers/14-MARCH.pdf) | 上海 AI Lab、清华、复旦 | 直接：递归记忆与检索 | 4 / 3.5 |
| 15 | 09-07 | [Kalman-Delta-Networks](notes/15-Kalman-Delta-Networks.md) · [PDF](papers/15-Kalman-Delta-Networks.pdf) | Yale | 直接：不确定性感知记忆 | 4.5 / 4 |
| 16 | 08-26 | [Prefix-Sliding](notes/16-Prefix-Sliding.md) · [PDF](papers/16-Prefix-Sliding.pdf) | Stanford、UW、UCSB、Prime Intellect | 相邻：长推理上下文管理 | 3.5 / 4 |
| 17 | 08-31 | [WHALE](notes/17-WHALE.md) · [PDF](papers/17-WHALE.pdf) | KRAFTON、KAIST、Stanford | 直接：权重与 harness 联合演化 | 4 / 2.5 |
| 18 | 08-28 | [PRISK](notes/18-PRISK.md) · [PDF](papers/18-PRISK.pdf) | UIUC、HKUST | 直接：个性化记忆风险 | 4 / 3.5 |
| 19 | 09-03 | [PlaidQ](notes/19-PlaidQ.md) · [PDF](papers/19-PlaidQ.pdf) | Duke、清华 | 直接：连续 diffusion LLM | 4.5 / 3 |
| 20 | 09-07 | [GRAFT](notes/20-GRAFT.md) · [PDF](papers/20-GRAFT.pdf) | NUS、NTU、北大 | 直接：diffusion LLM；个性化为延伸 | 4 / 3 |

## 最值得先读的 3 篇

1. **[Proteus](notes/01-Proteus.md)**：与你的 latent memory 最直接。把“何时开放记忆容量”从写入规则中分离出来，适合做机制清楚、预算可控的扩展；需要检验无终点流中的调度，而非只看预先知道长度的序列。
2. **[Recuris](notes/03-Recuris.md)**：把 working memory、技能调用和局部技能修订连接起来，适合 self-evolving agent memory。先看评测切分：SkillFlow 的顺序协议不能被当作严格未见任务泛化。
3. **[MemoryWalker](notes/05-MemoryWalker.md)**：值得研究的不只是检索结构，而是运行时压缩后的上下文与训练前缀是否一致。它可能成为 memory system 研究里很实用的训练—部署对齐切入点。

这是按你的潜在研究用途给出的深读顺序，不是重复主榜机构优先顺序。若近期主攻 diffusion LLM，优先切换到 PlaidQ、Survival-Length-Control、GRAFT。

## 本期研究信号与机构分布

产业团队覆盖 Google Research / DeepMind、ByteDance Seed、Alibaba、Amazon、Qualcomm、NVIDIA、Microsoft、Tencent、Meta、Huawei Noah、KRAFTON 等；学术合作覆盖 Stanford、Princeton、Oxford、Yale、清华、北大、NUS、NTU、UIUC 等。很多是多机构合作，不能把一篇同时计为多个独立成果来夸大数量。

按主要阅读用途粗分，20 篇包括：6 篇记忆架构/上下文管理，8 篇 agent 经验与演化系统，2 篇个性化数据/风险评测，3 篇 diffusion LLM，以及 1 篇潜在空间视觉推理。标签有交叉，这只是阅读分组。

共同趋势是：记忆不再只有“存什么、检索什么”，还包括**何时分配容量、如何表示不确定性、如何把经验编译成技能、怎样让训练条件与真实调用条件一致**。这是对本期样本的归纳，不是整个领域的统计结论。

## 哪些结果需要特别谨慎

- **[WHALE](notes/17-WHALE.md)**：算法描述中存在按 test 表现返回最优候选的选择规则。若测试集参与候选选择，最佳分数就不能作为一次性未触碰测试集的无偏估计；这也是强机构论文仍给 2.5/5 可信度的原因。
- **[Benchmark-as-Teacher](notes/09-Benchmark-as-Teacher.md)**：基准反馈参与训练信号构造，必须区分适应效果和真正独立泛化；4B 设置在所报告的 8 个外部基准均下降，不能只引用目标环境上的大幅增长。
- **[Recuris](notes/03-Recuris.md) / [UI-Mate](notes/11-UI-Mate.md)**：顺序经验协议、同任务 demonstration 和未见任务迁移回答的是不同问题，不能直接合并为“长期通用学习”证据。
- **[PlaidQ](notes/19-PlaidQ.md)**：pass@1 与 pass@10、单步与多步不可混比；标为 MBPP+ 的实验只使用基础断言，不等于完整 EvalPlus 增强测试通过率。
- **[AdsWorldEngine](notes/10-AdsWorldEngine.md) / [WearableQA](notes/12-WearableQA.md)**：商业指标上升不等于个体用户福利提升；生理数据相关性也不等于可做个体因果建议。

这些是具体评测边界，不是对作者动机的指控；详细依据和限制在对应笔记中。

## 可进一步发展的 3 个研究问题

以下为我的假设和建议实验，**不是这些论文已经证明的结论，也未核验能否作为全新选题**。

### 1. 不确定性驱动的记忆容量调度

结合 Proteus 与 Kalman-Delta-Networks：容量不按位置均匀解锁，而由写入不确定性、事件边界或分布变化决定。固定总 state bytes、训练 tokens 和计算预算，对比均匀、随机、事件、uncertainty 四种策略；分开测早期事实遗忘、后期事实吸收、矛盾偏好更新和连续流吞吐。关键反例是高噪声事件不断触发扩容，挤占真正重要的记忆。

### 2. 可验证技能演化与训练条件一致性

结合 Recuris / Evo-Harness 与 MemoryWalker：让“经验编译成技能后，部署时实际看到什么”成为训练和验证协议的一部分。按任务家族隔离 evolve / dev / test，固定工具调用与 token 预算，比较只修内容、只修调用条件、同时修二者；加上线索缺失、压缩失真、旧技能回归测试。主要指标不仅是成功率，还应有负迁移、门控误放行率和维护成本。

### 3. 有时间范围的个性化 diffusion anchors

从 GRAFT 的约束生成借鉴可编辑锚点，但用 PRISK 的 profile / memory 因子设计审计安全影响。比较原始记忆拼接、检索片段、带来源/有效期锚点三种方式，在偏好变化、矛盾记录、恶意记忆注入下测个性化效用、过期信息依赖和风险。需提供同等约束编辑能力的 AR 对照，不能只拿普通文本 prompt 比较；敏感个人数据应使用合规授权或合成数据。

## 文件与审计

- `papers/`：本期正式入选的 20 份 PDF，约 53.6 MB。
- `notes/`：20 份中文笔记，逐篇涵盖做了什么、方法、实验、结论、future impact、critical thinking、优点/局限和可信度。
- [selection.json](selection.json)：可机读名单、元数据与笔记内容。
- [verification.json](verification.json)：PDF 页数、字节数与 SHA-256 核验。通过文件核验不代表科学结论被复现。
- `sources/`：API 检索记录、候选 PDF 和提取文本，仅供追溯；其中未入选候选不是额外推荐。
- 旧版 7 篇留在上一级目录归档，未删除。正式推荐以本 README 为准。

PDF 阅读采用原文文本提取，并对需要视觉核验的机构标识查看首页。没有执行作者代码、复跑训练、独立复现结果或逐条验证所有证明。

## 后续每天的规则

自动任务保持**北京时间每天 08:00**启动。近 30 天只是本次重选特例；之后仅收录当天正式公告批次的新论文，核对公告批次与北京时间的对应，不以旧文新版或往日论文补足 20 篇。当天未发布/休刊/不足 20 篇时如实记录。

注意：arXiv 的提交时间不等于公开公告时间；其常规公告采用美国东部时间，夏令时与冬令时换算不同，因此每天必须核对实际公告，不能简单用 UTC 提交日期过滤。[arXiv 官方公告时间说明](https://info.arxiv.org/help/availability.html)

