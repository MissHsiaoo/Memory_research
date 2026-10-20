# 2026-09-22 arXiv LLM Memory 日报：20 篇已交付

状态：**completed**。本目录含 **20 篇中文评析、20 份已校验的官方 PDF**（合计 628 页、59,182,890 字节）及逐件 [SHA-256/页数/来源核验记录](verification.json)。论文中的数字均来自作者报告，未独立复现；逐篇评析将论文证据与我的推断分开。文件名前缀是撰写顺序，**以下表格序号才是最终推荐次序**。

## 批次与日期核验

北京时间 2026-09-22 **12:05** 保存的 [cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new) 官方列表显示 “Tuesday, 22 September 2026”；这才是本期正式公告批次。北京时区日期也是 9 月 22 日，但 **arXiv 初次提交日不是公告日**：入选论文 v1 提交于 9 月 18–21 日。微软 PSD 由 [cs.IR 当天 New 栏](sources/cs.IR-primary-listing.html)、阿里 VibeMemBench 由 [cs.SE 当天 New 栏](sources/cs.SE-primary-listing.html)另行核实；全部 20 篇均在各自正式主类 New 栏，且 v1 为近期首发，非 replacement。来源快照见[当日批次日志](sources/20260922T040537Z/batch-check.json)和[主类核验](sources/primary-category-verification.json)。筛选时额外剔除 2609.22145（v1 8 月 26 日）和 2609.22231（v1 9 月 3 日）：虽然今天某分类标为“New”，但不是本日新论文。

## 最终排序：机构优先级 → 研究相关性 → 方法新颖性

先优先 OpenAI/Google/Alibaba/Tencent/Microsoft 等顶级产业研究及一流高校合作；同一机构层内再看是否直接命中 memory、ICL、diffusion 或自进化，以及消融与潜在启发。没有为凑 20 篇收录低优先级机构黑马；后段的 AutoGym、agent collusion 和 TimeVolve 已明确标记弱相关/跨场景启发。**机构优先级并不是论文可信度分数**，后者见各篇第 6 节。并列机构等级中的次序综合主题与实验；B 组虽有清华/CMU 参与，主导机构不是指定顶级研究团队，因此保守标注。

| 最终序 | 论文与本地评析 | 机构优先级 / 相关性 | 选择理由 |
|---:|---|---|---|
| 1 | [LoRA-generating hypernetworks for efficient on-device LLM generative personalization](01-google-ondevice-personalization.md) · [arXiv](https://arxiv.org/abs/2609.24979) · [PDF](papers/2609.24979.pdf) | A｜顶级产业研究 / 直接相关 | Google 端侧超网络生成个性化 LoRA；直接关联参数化个人记忆，ROUGE 与交叉熵分歧值得细读。 |
| 2 | [RPMem: Learning Long-Term Recurrent Parametric Memory Across Sessions for LLM Agents](02-alibaba-rpmem.md) · [arXiv](https://arxiv.org/abs/2609.23466) · [PDF](papers/2609.23466.pdf) | A｜顶级产业研究 / 直接相关 | 阿里巴巴跨会话递归潜在记忆；五骨干、门控消融和长历史表现直击 latent memory。 |
| 3 | [MemCalib: Benchmarking and Optimizing Memory Use in LLM Agents](03-alibaba-memcalib.md) · [arXiv](https://arxiv.org/abs/2609.24259) · [PDF](papers/2609.24259.pdf) | A｜顶级产业研究 / 直接相关 | 阿里巴巴将记忆“该不该用、用多少”变成可训练校准问题，反事实归因有新意。 |
| 4 | [Propose, Verify, Commit: Evidence-Grounded Memory for Long-Horizon Multi-Actor Conversations](04-alibaba-egmemory.md) · [arXiv](https://arxiv.org/abs/2609.23465) · [PDF](papers/2609.23465.pdf) | A｜顶级产业研究 / 直接相关 | 阿里云把多人对话状态与消息级证据绑定，写入前核验、读取时导航。 |
| 5 | [VibeMemBench: Evaluating Memory Systems for Coding Agents on Real Repository Coding Tasks](06-alibaba-vibemembench.md) · [arXiv](https://arxiv.org/abs/2609.23570) · [PDF](papers/2609.23570.pdf) | A｜顶级产业研究 / 直接相关 | 阿里巴巴编码记忆基准揭示现成记忆系统常无增益甚至负迁移，是高价值负结果。 |
| 6 | [ScholarStack: Layered Research Asset Orchestration and Cross-Task Reuse for Scientific Agents](07-alibaba-scholarstack.md) · [arXiv](https://arxiv.org/abs/2609.23735) · [PDF](papers/2609.23735.pdf) | A｜顶级产业研究 / 直接相关 | 阿里 DAMO 将科研证据、组织和跨篇综合分层复用，适合长期研究 agent。 |
| 7 | [LADDER: Graph-Guided Diffusion Language Models for Efficient Multi-Hop Reasoning](08-tencent-ladder.md) · [arXiv](https://arxiv.org/abs/2609.24346) · [PDF](papers/2609.24346.pdf) | A｜顶级产业研究 / 直接相关 | 腾讯 Youtu 将图检索按需插入 diffusion LLM 去噪过程，速度和多跳质量都有实验。 |
| 8 | [PSD: Pseudo Self-Distillation of Memory Representation Capabilities for LLM Agents](09-microsoft-psd.md) · [arXiv](https://arxiv.org/abs/2609.23449) · [PDF](papers/2609.23449.pdf) | A｜顶级产业研究 / 直接相关 | 微软将强模型的记忆表示能力蒸馏给小模型，降低长期记忆写入门槛。 |
| 9 | [Beyond Endpoint Performance: Process-Level Evaluation of Self-Evolving Agents](05-alibaba-evopathbench.md) · [arXiv](https://arxiv.org/abs/2609.24663) · [PDF](papers/2609.24663.pdf) | A｜顶级产业研究 / 直接相关 | 阿里巴巴用迁移、保留、规则适应三轴检验 self-evolving agent，超越终点分数。 |
| 10 | [ACLArena: Agent Continual Learning in Multi-stage Post-training](11-ucla-aclarena.md) · [arXiv](https://arxiv.org/abs/2609.23989) · [PDF](papers/2609.23989.pdf) | A｜全球一流研究型高校 / 直接相关 | UCLA 多阶段 agent 训练直接量化遗忘，并比较回放、蒸馏和专家路由。 |
| 11 | [Few-Shot Demonstrations Elicit the Use of In-Context World Representations in LLMs](16-tokyo-harvard-world-icl.md) · [arXiv](https://arxiv.org/abs/2609.24352) · [PDF](papers/2609.24352.pdf) | A｜全球一流研究型高校 / 直接相关 | 东京大学/哈佛用探针与干预说明 ICL 示例让世界表征更被使用，而非仅存在。 |
| 12 | [iSDFT: Information-Proximal Self-Distillation for Continual Learning in LLMs](19-ucl-imperial-isdft.md) · [arXiv](https://arxiv.org/abs/2609.24646) · [PDF](papers/2609.24646.pdf) | A｜全球一流研究型高校 / 相关但非会话记忆 | UCL/Imperial 信息邻近自蒸馏缓解新技能训练引起的能力遗忘。 |
| 13 | [Harness-Zero: Harness Distillation via Agent-as-Harness](14-pku-google-harness-zero.md) · [arXiv](https://arxiv.org/abs/2609.24974) · [PDF](papers/2609.24974.pdf) | A｜顶级产业与一流高校合作 / 相关但非用户记忆 | 北大/Google 把在线 harness 审查内化为参数技能，关联 agent 经验沉淀。 |
| 14 | [MedRSI: Recursive Self-Improvement for Medical Agents via Clinically Aligned Self-Evolution](10-oxford-medrsi.md) · [arXiv](https://arxiv.org/abs/2609.24838) · [PDF](papers/2609.24838.pdf) | A｜全球一流研究型高校 / 相关但医疗场景；具启发性 | Oxford/Stanford 用“快发现、慢注册”约束医疗 agent 自进化，提供安全门控设计。 |
| 15 | [Self-Organizing Agent Teams Learn to Reason Together](15-stanford-agent-teams.md) · [arXiv](https://arxiv.org/abs/2609.22682) · [PDF](papers/2609.22682.pdf) | A｜一流高校与产业合作 / 相关但非个人记忆 | Stanford/Together 研究可复用的团队协作策略，但最强基线差距小。 |
| 16 | [Representation-guided in-context learning for medical image interpretation with multimodal large language models](17-harvard-mit-rgicl.md) · [arXiv](https://arxiv.org/abs/2609.24057) · [PDF](papers/2609.24057.pdf) | A｜全球一流研究型高校 / 相关但医疗场景 | Harvard/MIT 以表示检索改善多模态 ICL；医疗场景说明案例质量重于数量。 |
| 17 | [AutoGym: Blueprint-First Generation of Verifiable Agent Gyms](18-amazon-autogym.md) · [arXiv](https://arxiv.org/abs/2609.22592) · [PDF](papers/2609.22592.pdf) | A｜顶级产业研究 / 弱相关但具启发性 | Amazon AGI 的可验证训练环境是自进化反馈基础；弱相关但机构强、方法有启发。 |
| 18 | [Emergent Collusion in Long-Horizon LLM Agent Interaction](12-stanford-agent-collusion.md) · [arXiv](https://arxiv.org/abs/2609.24967) · [PDF](papers/2609.24967.pdf) | A｜全球一流研究型高校 / 弱相关但具启发性 | Stanford 长程双 agent 互动显示共享历史也可能固化违规协作；弱相关安全启发。 |
| 19 | [Et Tu, Brute? Economic Misalignment in Personal AI Agents](20-cisco-cmu-economic-misalignment.md) · [arXiv](https://arxiv.org/abs/2609.24927) · [PDF](papers/2609.24927.pdf) | B｜大型产业研究与一流高校 / 直接相关但非新记忆架构 | Cisco/CMU 检验个人资料导致的违令经济选择；个性化收益之外的风险。 |
| 20 | [When Tomorrow Becomes Today: Self-Evolving Policies for Agentic Time-Series Forecasting](13-ant-timevolve.md) · [arXiv](https://arxiv.org/abs/2609.24862) · [PDF](papers/2609.24862.pdf) | B｜大型产业研究与一流高校 / 相关但时序预测场景 | Ant/清华通过预提交—结果揭晓—政策更新做时序自进化；场景较远但过程严谨。 |

## 机构分布与主题趋势

按主导署名粗分：Alibaba/Alibaba Cloud/DAMO **6**；Google 主导 **1**，北京大学–Google 合作 **1**；Tencent **1**，Microsoft **1**，Amazon AGI **1**，Ant International **1**，Cisco Foundation AI **1**；一流高校主导 **7**。这是入选样本分布而非当天 arXiv 全量机构统计。A 机构优先级 **18**、B **2**；“A/B”只衡量机构优先，不代表实证可信度。所有机构名称均以 PDF 首页为据，未把论文中被引用的模型公司误当作者机构。

今天集中出现三股值得持续追踪的路线。其一，**记忆构建 → 使用校准 → 证据审计**：RPMem、PSD 负责把历史变成可用状态，MemCalib 控制何时使用，EGMEMORY/ScholarStack 保存依据；这几条可以组合，但目前缺少统一用户级长期测试。其二，**更长历史不必然更好**：VibeMemBench 给出现成编码记忆的负结果，Google 个性化 LoRA 在 ROUGE 与交叉熵上分歧，collusion 研究提示共享历史可放大违规协调。其三，**自进化需回归与门控**：EvoPathBench、ACLArena、MedRSI、iSDFT 分别测过程退化、能力遗忘、技能注册与保留，证明“累积经验”不等于“稳健提升”。医疗/经济选择论文只作为 agent 机制研究，不是临床或财务建议。

## 今天最值得深读的三篇

1. [RPMem](02-alibaba-rpmem.md)：最贴近 **latent / long-term memory**，同时有跨骨干、门控消融与长历史实验；深读重点是可编辑性、错误记忆清除和真实会话流。
2. [Google 端侧 LoRA 超网络](01-google-ondevice-personalization.md)：提供参数化个人记忆的另一种实现，并有“ROUGE 改善但交叉熵未同步改善”的重要信号；深读重点是新用户 OOD、隐私与撤回。
3. [VibeMemBench](06-alibaba-vibemembench.md)：其负结果对研究选题最有校准价值；深读重点是理想经验与自动记忆系统的落差、统计区间及真实计算成本。

## 当日复核边界

已读取 PDF 首页以确认机构，抽查方法、主表、消融与局限，关键表格另以渲染页复核；**没有独立复现实验**。科研评析中的“future impact”与后续实验建议属于我的推断。相同方法在不同任务上可能反向，不能用排名替代逐篇查看适用条件。


## 12:05 北京时间：正式批次可见

北京时间 12:05:37（UTC 04:05:37）开始保存的 cs.CL、cs.AI、cs.LG 正式列表均显示 **Tuesday, 22 September 2026**；cs.CL、cs.AI RSS 也显示 9 月 22 日，cs.LG RSS 本轮传输超时，但对应正式 HTML 列表成功取得，足以按正式公告批次筛选。[本轮来源快照](sources/20260922T040537Z/batch-check.json)。三类列表去重、排除 replacements 后共 799 条 new/cross 候选；此数字不等于已核验的独立新稿，也不等于最终入选数。该时刻开始了机构和原文核验，最终交付结果见上方。

## 08:24 北京时间官方来源核验

本日定时任务于北京时间 08:09:31 触发；本轮快照从北京时间约 08:24:01（UTC 00:24:01）开始保存。cs.CL、cs.AI、cs.LG 三个 arXiv 正式 `new` 列表均成功访问，但标题仍为 **Monday, 21 September 2026**，不是目标 **Tuesday, 22 September 2026** 批次。三个 RSS 的 `pubDate` 也为 9 月 21 日，分别含 138、214、237 条；这些条目属于旧批次，不能归入今天。

[本轮核验结果与六份来源快照](sources/20260922T002401Z/batch-check.json)。快照开始时间不是官方公告发布时间。论文首次提交日期、RSS 更新日期及正式公告日期严格分开。

在 08:24 的检查时点，9 月 22 日入选论文、PDF 和逐篇评析均为 **0（尚未开始筛选，并非当日最终数量）**。未回填 9 月 21 日论文，也未用旧版本更新或近 30 天作品凑数。最终结果见本文顶部。

## 续跑

本日曾临时按小时核验正式批次；正式列表可见后完成机构核验、筛选、下载及全文评析。交付完成后已撤销临时每小时续跑，核实调度恢复为 **每日北京时间 08:00**、原任务提示词及同线程目标不变。无变化检查只增量记录；过去日期文件夹未修改。续跑方式参考 [OpenAI Docs 的同线程定时任务说明](https://learn.chatgpt.com/docs/automations?surface=app)。

## 续跑检查记录

- **09:00:54 北京时间**：六个官方来源全部抓取成功；cs.CL、cs.AI、cs.LG 正式列表仍显示 9 月 21 日，三个 RSS 也仍为 9 月 21 日，数量分别为 138、214、237。9 月 22 日批次仍未核验，状态保持 pending，小时续跑继续。[本轮来源快照](sources/20260922T010054Z/batch-check.json)。
- **10:02:46 北京时间**：本轮 cs.AI、cs.LG 正式列表与三个 RSS 均仍显示 9 月 21 日。cs.CL 第一次请求遇到连接重置；随后独立重试成功，[重试保存的 cs.CL 正式列表](sources/20260922T020246Z/cs.CL-listing-retry.html)也显示 9 月 21 日。因此没有以单次网络错误推断公告日期；本日仍为 pending。[本轮抓取日志](sources/20260922T020246Z/batch-check.json)。
- **11:01:24 北京时间**：cs.AI、cs.LG 正式列表和三个 RSS 仍为 9 月 21 日；cs.CL 首次请求再次连接重置，但[重试快照](sources/20260922T030124Z/cs.CL-listing-retry.html)核实也是 9 月 21 日。9 月 22 日正式批次尚未出现，保留 pending 并继续小时续查。[本轮抓取日志](sources/20260922T030124Z/batch-check.json)。
