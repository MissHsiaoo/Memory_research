# 2026-09-18 arXiv LLM Memory 日报

状态：**completed｜20 篇精选、20 份官方 PDF、20 份中文六项评析已完成**。本日正式批次在北京时间 11:01 续跑时可见，不是当天没有论文。08:02、09:00、10:01 等待记录完整保留在本文末尾。

## 日期与范围核验

- 报告目录日：北京时间 **2026-09-18**。官方 HTML 公告标题：**Friday, 18 September 2026**；该公告批次归入本日北京时间目录。本轮开始保存快照的时间是 **11:01:09 北京时间 / 03:01:09 UTC**，不是官方发布时间。
- 范围仅含该批次首次公告的 **New submissions / v1**。17 篇首次提交于 9 月 17 日，3 篇提交于 9 月 16 日（Probe Guidance、CSBP、Compositional RL），但都在 **9 月 18 日正式公告**。没有用提交日期代替公告日期，没有扩展近 30 天，没有旧版更新凑数。
- 主来源：[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new) 的[本轮官方快照核验](sources/20260918T030109Z/batch-check.json)。这些实时链接会随日期滚动，以保存的 HTML 快照为准；RSS 日期仍有滞后，本日不据 RSS 判定无新稿。
- Auto Mode 在 AI/CL 中是 cross-list，因此另核验 **cs.CR 的 9 月 18 日 New submissions**；[主类审计](sources/primary-category-verification.json)与[官方快照](sources/cs.CR-primary-listing.html)保存。未将仅 cross-list 的旧论文算入。

## 筛选与证据标准

三个主列表去掉 replacements 后，new/cross 去重共 **414 条候选**；标题/摘要关键词初筛 164 条，再从中扩展检查强机构的邻近方向，下载 **32 份重点候选全文**，最终选 20 篇。[候选目录](sources/catalog.json)、[最终清单](selection.json)、[日期元数据](sources/metadata.json)、[交付核验](verification.json)均可追溯。32 份为进一步核验的候选，不是 32 篇已入选。

排序首先看可核验机构及合作角色，其次看直接相关性与本次候选中的方法洞见。优先公司/实验室与顶尖高校工作为主体；P2 三篇有强高校合作，但主导机构不属于本任务优先公司，故后置。弱相关工作明确标注而不伪装成 memory 算法。榜单是本次筛选的研究优先级判断，**不声称穷尽全球所有机构或客观证明全球 novelty 前 20**；机构与证据可信度独立评分。novelty 的 1–5 分只在逐篇文件中作为主观辅助，不抵消机构优先级。

全文可访问的 20 篇均重点阅读方法、实验/定理、结果及局限，不宣称逐行通读全部 565 页。已使用 PDF 阅读技能提取全文，并对 RAFT 第 7 页、CSBP 第 9 页、Apple Limits 第 8 页关键表格/局限进行渲染视觉核对，防止抽取造成列错位。没有独立复跑训练、搜索或用户统计，也没有独立验证全部理论证明。每篇把作者证据与我们的 future-impact 推断分开。

## 全部入选论文及为什么选择

P1 为优先公司/实验室或顶尖研究高校；P2 为本日后置的强合作补充。P1 内直接相关工作先于弱相关工作；核心记忆、diffusion 与自演化分支按研究启发综合排序，novelty 不视作可机械比较的客观精确量。P2 强合作补充后置。完整方法、实验、结论、未来影响、批判与可信度见各中文文件。

| 排名 | 论文与文件 | 已核验机构 | 机构/相关性标签 | 可信度 | 为什么选 |
|---|---|---|---|---|---|
| 01 | [Tailored to you: longitudinal effects of personalising language models](01-Tailored-to-you.md) · [arXiv](https://arxiv.org/abs/2609.20077v1) · [PDF](papers/01-Tailored-to-you-2609.20077.pdf) | Google DeepMind | P1｜优先公司，直接相关 | 4/5 | Google DeepMind 的预注册纵向随机实验，把记忆式与问卷式个性化分开，是今天最直接回答“用户真的受益吗”的证据。 |
| 02 | [RAFT: A Stateful Retrieval-Augmented Framework for Troubleshooting Agents](02-RAFT-stateful-retrieval.md) · [arXiv](https://arxiv.org/abs/2609.20754v1) · [PDF](papers/02-RAFT-stateful-retrieval-2609.20754.pdf) | Microsoft（论文首页署名 Redmond；不额外推定为 Microsoft Research） | P1｜优先公司，直接相关 | 4/5 | Microsoft 把历史工单作为状态轨迹而非静态文档，直接启发 agent episodic memory 的组织与召回单位。 |
| 03 | [SIMLIFE: Pattern Understanding for Long-Horizon Human-Agent Partnership](03-SIMLIFE.md) · [arXiv](https://arxiv.org/abs/2609.19610v1) · [PDF](papers/03-SIMLIFE-2609.19610.pdf) | University of Michigan；ByteDance；Osaka University；Amazon；University of Pennsylvania（首页核验；未核验为 ByteDance Seed） | P1｜优先公司/高校合作，直接相关 | 4/5 | 强高校与 ByteDance/Amazon 合作，用规则变化与反事实问题区分“记住频率”和“理解人的行为模式”。 |
| 04 | [SoL-Pi: Recursively Scaling Auto-Research Loops for Efficient Agent Harness](04-SoL-Pi.md) · [arXiv](https://arxiv.org/abs/2609.20519v1) · [PDF](papers/04-SoL-Pi-2609.20519.pdf) | NVIDIA；Nanyang Technological University；MIT（首页机构列表；不把未显示清晰上标的个别作者强行分配） | P1｜优先公司/高校合作，直接相关 | 3.5/5 | NVIDIA/MIT/NTU 的大规模 harness 自动研究，将 context compaction 和 evidence-preserving reading 放到能力—成本取舍中。 |
| 05 | [How to Guide Your Language Flow](05-Probe-Guidance.md) · [arXiv](https://arxiv.org/abs/2609.19356v1) · [PDF](papers/05-Probe-Guidance-2609.19356.pdf) | Apple；California Institute of Technology | P1｜优先公司/高校合作，直接相关 | 4/5 | Apple/Caltech 用冻结内部状态的轻量 probe 替代第二个完整模型 forward，为 diffusion 的低成本控制提供新机制。 |
| 06 | [Limits of Confidence in Diffusion](06-Limits-of-Confidence.md) · [arXiv](https://arxiv.org/abs/2609.20581v1) · [PDF](papers/06-Limits-of-Confidence-2609.20581.pdf) | Apple | P1｜优先公司，直接相关 | 4/5 | Apple 给出“逐位置置信度不足以认证联合并行写入”的理论与可精确检验实验，直接挑战 diffusion 常用评估指标。 |
| 07 | [Red-Teaming Auto Mode: Improving Blocking Classifiers Against Malign Coding Agents](07-Auto-Mode-memory-safety.md) · [arXiv](https://arxiv.org/abs/2609.19587v1) · [PDF](papers/07-Auto-Mode-memory-safety-2609.19587.pdf) | Anthropic Fellows Program；Anthropic（不因研究 Guardian 而写成 OpenAI 合作） | P1｜优先公司，记忆安全直接相关 | 4/5 | Anthropic 的 monitor 红队发现 compaction 会破坏授权来源；这是长期 agent memory 必须处理的安全问题。 |
| 08 | [RetireOPD: Self-Retiring On-Policy Distillation for Agentic Reinforcement Learning](08-RetireOPD.md) · [arXiv](https://arxiv.org/abs/2609.20784v1) · [PDF](papers/08-RetireOPD-2609.20784.pdf) | Zhejiang University；Alibaba | P1｜优先公司/高校合作，直接相关 | 3.5/5 | Alibaba/浙大让带 skill 的教师适时退出，将显式经验内化为学生能力，避免持续蒸馏限制学生。 |
| 09 | [Evolution or Illusion? Rethinking Evaluation in LLM Evolutionary Search](09-Evolution-or-Illusion.md) · [arXiv](https://arxiv.org/abs/2609.19799v1) · [PDF](papers/09-Evolution-or-Illusion-2609.19799.pdf) | IBM Research | P1｜优先公司，自演化评估直接相关 | 4/5 | IBM Research 揭示宽度/深度预算会翻转算法排名，并发现 evaluator 漏洞伪装成自演化进步。 |
| 10 | [An Architecture for Long-Horizon Agents: Levels, Ticks and Cascaded Intelligence](10-Levels-Ticks-Cascades.md) · [arXiv](https://arxiv.org/abs/2609.19519v1) · [PDF](papers/10-Levels-Ticks-Cascades-2609.19519.pdf) | Salesforce AI Research | P1｜优先公司，直接相关 | 3/5 | Salesforce 将跨上下文与跨进程持续记忆设计成有层级、时钟和升级机制的系统，而不是只扩大上下文。 |
| 11 | [Continual Enterprise World Model Discovery in Dynamic Systems](11-Continual-Enterprise-World.md) · [arXiv](https://arxiv.org/abs/2609.19551v1) · [PDF](papers/11-Continual-Enterprise-World-2609.19551.pdf) | ServiceNow Research；ÉTS；University of British Columbia；Polytechnique Montréal；Mila；McGill University | P1｜优先研究公司/高校合作，直接相关 | 3.5/5 | 强企业研究与 Mila 合作，把保留、修改、新增、退休旧规则分开评估，尤其展示“删除过时记忆”的失败。 |
| 12 | [ScientistTwo: Pioneering the Human Knowledge Frontier with Autonomous AI](12-ScientistTwo.md) · [arXiv](https://arxiv.org/abs/2609.19644v1) · [PDF](papers/12-ScientistTwo-2609.19644.pdf) | Google Cloud AI Research；University of Waterloo（不写成 Google DeepMind） | P1｜优先公司，自演化科研相关 | 3/5 | Google Cloud 的闭环科研系统具有实验历史与改进循环启发，但 AI 评审“可发表”结论必须严审。 |
| 13 | [Parallelism, critical windows, and separations among diffusion language models](13-Diffusion-critical-windows.md) · [arXiv](https://arxiv.org/abs/2609.20539v1) · [PDF](papers/13-Diffusion-critical-windows-2609.20539.pdf) | Harvard University, SEAS；Tsinghua University | P1｜顶尖高校，直接相关 | 4/5 | 哈佛/清华首次给出特定分布上 diffusion 家族的并行能力分离，并用 critical window 替代“不能反悔”直觉。 |
| 14 | [Block Parallelism For Efficient Distributed Long-Context Diffusion Language Model Training](14-CSBP.md) · [arXiv](https://arxiv.org/abs/2609.19242v1) · [PDF](papers/14-CSBP-2609.19242.pdf) | Stanford University | P1｜顶尖高校，直接相关 | 4/5 | Stanford 从 BDLM loss 的 block 可分解性得到新的并行维度，方法具体且能支撑更长记忆上下文训练。 |
| 15 | [dQwen3.5: Hybrid-Attention Diffusion Language Models](15-dQwen3.5.md) · [arXiv](https://arxiv.org/abs/2609.20751v1) · [PDF](papers/15-dQwen3.5-2609.20751.pdf) | The University of Texas at Austin（不是因为底座 Qwen 就署名 Alibaba） | P1｜顶尖研究高校，直接相关 | 4/5 | UT Austin 在仍保留因果循环层的 hybrid backbone 上构建 diffusion，挑战必须全双向化的工程假设。 |
| 16 | [Compositional Reasoning in Language Models under Reinforcement Learning Post-Training](16-Compositional-RL.md) · [arXiv](https://arxiv.org/abs/2609.19465v1) · [PDF](papers/16-Compositional-RL-2609.19465.pdf) | Stanford University；Amazon AGI Labs | P1｜优先公司/高校合作，弱相关但具启发性 | 4/5 | Stanford/Amazon AGI 的组合泛化研究说明“积累原子技能”不等于“能组合使用”，直接启发 memory skill 接口评价。 |
| 17 | [Chronicle: Cut-Point Replay for Regression Testing of LLM Agents](17-Chronicle.md) · [arXiv](https://arxiv.org/abs/2609.20625v1) · [PDF](papers/17-Chronicle-2609.20625.pdf) | Microsoft | P1｜优先公司，弱相关但具启发性 | 3/5 | Microsoft 的 cut-point replay 可把历史记忆事故变成可重复回归测试；虽非 memory 算法，验证基础设施价值明确。 |
| 18 | [On-Demand Attention: Language Models Know When to Recall](18-On-Demand-Attention.md) · [arXiv](https://arxiv.org/abs/2609.20734v1) · [PDF](papers/18-On-Demand-Attention-2609.20734.pdf) | Southern University of Science and Technology；Peking University；Peng Cheng Laboratory（首页合作；非优先公司主导） | P2｜强高校合作，较低机构排序优先级；直接相关 | 3.5/5 | 不是优先公司主导，但 PKU 合作已核验；从局部隐藏状态预测是否召回全局历史，对 latent memory access 有直接方法启发。 |
| 19 | [LearnActCoder: Role-Aware Error Memory for Adaptive Clinical Coding Agents](19-LearnActCoder.md) · [arXiv](https://arxiv.org/abs/2609.19721v1) · [PDF](papers/19-LearnActCoder-2609.19721.pdf) | Optum AI；Harvard University（合作核验；不标为优先公司主导） | P2｜应用机构主导/顶尖高校合作；直接相关 | 4/5 | Optum/Harvard 用结构化误差记忆而非泛泛 reflection，且公开不显著结果与 precision/recall 取舍，实验启发明确。 |
| 20 | [FINSKILLOPS: A Self-Evolving Multi-Agent System for SEC Filing QA](20-FINSKILLOPS.md) · [arXiv](https://arxiv.org/abs/2609.19680v1) · [PDF](papers/20-FINSKILLOPS-2609.19680.pdf) | SimpleWay.AI 主导；首页含 McGill、University of Toronto、UCLA、CUHK、Mila、McMaster、Harvard、Monash、HKU、Stanford、Queen Mary 等合作署名（机构列表不等于各方均主导） | P2｜初创机构主导/多所强高校合作；直接相关 | 3/5 | 不是优先大公司主导，故后置；其 scoped skill、no-regression gate 与版本退休对可靠 self-evolving memory 特别有启发。 |

## 机构分布

20 篇均由官方 PDF 首页核验机构，**0 篇“机构未核验”**。按论文计而非作者计、合作可重复：Google DeepMind 1；Google Cloud AI Research 1（两者不混同）；Microsoft 2；Apple 2；Anthropic 1；NVIDIA 1；ByteDance 1；Amazon/AGI Labs 2；Alibaba 1；IBM Research 1；Salesforce AI Research 1；ServiceNow Research 1。高校主体/重点合作包括 Stanford、Harvard、MIT、Caltech、清华、UT Austin、Michigan、UPenn、浙大、北大及 Mila 等。

注意机构角色：SIMLIFE 仅核验到 ByteDance，**不能自动写为 Seed**；Auto Mode 作者来自 Anthropic/Fellows，研究 Guardian 不意味着 OpenAI 作者参与；dQwen 使用 Qwen 不意味着 Alibaba 作者参与。LearnActCoder 为 Optum AI/Harvard 合作，FINSKILLOPS 为 SimpleWay.AI 主导与多高校合作，ODA 为 SUSTech/PKU/Peng Cheng 合作，均不因强高校名字就冒充顶级公司主导。本日未收录未经核验的 OpenAI 作者论文。

## 当天趋势与研究机会

1. **记忆的“效用”需与用户感知分开。** Tailored to you 的大样本实验表明，重复使用本身能改变感知，个性化的独立效应小且多面；SIMLIFE 则说明预测准不代表理解人的规则。建议联合评价真实帮助、偏好适应与隐私/披露后果。
2. **状态轨迹比静态摘要更适合经验检索。** RAFT 用阶段化事件匹配，Levels/Ticks 用持久层级状态；关键不是无限增加 context，而是保留适用条件、来源和可恢复执行状态。
3. **自演化需要 admission、retirement 和独立验证。** Enterprise World 删除旧规则仍困难，FINSKILLOPS 明确技能入库门槛，RetireOPD 让教师适时退出；IBM 的反例提醒最高分 archive 可能保存无效解。未来可把“证据—版本—测试—撤销”做成统一 memory lifecycle。
4. **Diffusion 的收益必须拆开质量、联合分布与系统成本。** Probe Guidance 降低额外主干计算，CSBP 加速训练，dQwen 检验 hybrid 初始化；Apple Limits 与 critical-window 理论解释不同采样障碍。不能将少 NFE、低 loss、高单题正确率直接等同于快、忠实或分布正确。
5. **可信度与机构声望不是同一轴。** ScientistTwo 的 AI-review 接受率不是真实会议录用，Chronicle 的六例模拟测试不是部署级安全证明；强机构弱相关工作仍有启发，但应在明确证据范围内使用。

## 最值得深读的三篇

- **Tailored to you（Google DeepMind）**：[中文评析](01-Tailored-to-you.md)。理由：直接检验 memory/personalization 对用户行为的独立影响；可用于重设计你的个性化系统评价，尤其应深读多重比较与首日提示混杂。
- **RAFT（Microsoft）**：[中文评析](02-RAFT-stateful-retrieval.md)。理由：状态级召回、案例级返回的经验记忆组织很具体；可快速形成“轨迹记忆 vs 文档 RAG”的复现实验，但应把 Case Hit 与最终解决率分开。
- **Limits of Confidence in Diffusion（Apple）**：[中文评析](06-Limits-of-Confidence.md)。理由：逐样本成功可能掩盖联合分布失真；定理假设、配对写入次序及局限可直接转成新的 decoder 评价问题。建议连读哈佛/清华的[critical-window 论文](13-Diffusion-critical-windows.md)，不要把不同假设下的结论混成全面胜负。

## 交付与调度

已通过文件有效性、PDF 页数/签名、20 个唯一 arXiv ID、v1 日期、New submissions 归属、六项 Markdown 结构与长度检查。官方 PDF 均成功下载，无需失败链接占位：**20 份 PDF，合计 565 页、57,307,651 字节**。SHA-256、逐篇页数、日期与公告来源在[verification.json](verification.json)。阅读并不等于独立复现，可信度分数非接受概率。

**11:17 北京时间：已通过应用恢复原同线程任务为每日北京时间 08:00，状态 ACTIVE；临时小时续跑段落已移除。** 随后读取实际配置核验了每日时间、原目标线程与临时段落删除，未创建重复任务。操作依据 [OpenAI Docs 的同线程定时续跑说明](https://learn.chatgpt.com/docs/automations?surface=app)；原有机构、范围和阅读要求保留。过去日期文件夹没有修改。

---

## 当日早先检查历史（原文保留，以下 pending 不代表当前状态）


# 08:02—11:01 原始记录

## 11:01续跑进展

北京时间11:01:09开始保存的三个正式HTML列表均显示Friday, 18 September 2026，状态推进为researching（筛选与原文评析中，尚未交付）。RSS虽构建时间更新，pubDate仍是9月17日；本轮按正式HTML继续。[本轮公告快照](sources/20260918T030109Z/batch-check.json)。new/cross去重候选414条，主题关键词初筛164条，已开始32份重点候选的原文核验。以下pending段落为此前检查历史，不代表当前状态。

状态：**pending（待核验、待续跑）**。尚未完成本日精选，当前检查不能用于判断当天没有合格论文。

## 官方来源核验

北京时间 **2026-09-18 08:02:17** 开始保存的六份官方快照均抓取成功。cs.CL、cs.AI、cs.LG 的正式列表全部显示 **Thursday, 17 September 2026**，尚未核验到 Friday, 18 September 2026 批次。

三个 RSS 的 pubDate 均为9月17日，构建时间为9月17日04:00 UTC附近；cs.CL、cs.AI、cs.LG 分别有171、304、325条。条目数量不代表9月18日的新论文数量。

[核验结果与六份快照索引](sources/20260918T000217Z/batch-check.json)。记录时间是本轮开始时间，不代表每个请求的准确完成时间，也不代表公告发布时间。08:02:05是自动任务触发时间。

本任务以正式公告日期归入北京时间9月18日目录，并另外记录首次提交日期；提交日期不用于推断公告归属。当前未纳入任何论文，机构分布、主题趋势和深读前三篇待本日正式批次可见后补充。

## 续跑安排

已通过应用将原有同线程任务临时设为每小时检查，仅用于补齐9月18日报告；原机构优先、当日范围和逐篇六项评析要求完整保留。正式批次可见后继续筛选和原文阅读，文件完成核验后恢复每日北京时间08:00。

若本日23:00仍未完成，或续跑已经跨日，记录确切阻碍并通知一次，同时恢复每日08:00。恢复需要后续运行实际执行，当前仍为临时小时续跑状态。没有变化的检查只增量记录。

调度操作依据 OpenAI Docs 的[同线程定时续跑说明](https://learn.chatgpt.com/docs/automations?surface=app)。本轮仅检查公告与安排续跑，未进行论文全文评审；过去日期目录未修改。

## 续跑检查记录

- **09:00:10（北京时间）**：六个官方来源均抓取成功，cs.CL、cs.AI、cs.LG正式列表仍显示9月17日；三个RSS的日期、构建时间和条目数与08:02检查一致。本日批次仍未核验，状态保持pending，临时小时检查继续。[本轮结果与六份快照](sources/20260918T010010Z/batch-check.json)。
- **10:01:40（北京时间）**：六个官方来源均抓取成功，三个正式列表仍显示9月17日；RSS日期、构建时间和条目数保持一致。尚未核验到9月18日批次，状态保持pending，现有小时续跑继续。[本轮结果与六份快照](sources/20260918T020140Z/batch-check.json)。
