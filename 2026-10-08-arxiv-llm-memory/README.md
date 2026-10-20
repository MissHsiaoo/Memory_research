# 2026-10-08 arXiv LLM Memory 日报

状态：**已完成，20 篇**。北京时间约 11:02 核验时，[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new) 官方页面均已显示 `Showing new listings for Thursday, 8 October 2026`；第 06 篇的主分类另经 [cs.CV](https://arxiv.org/list/cs.CV/new) 当天 `New submissions` 核验。这里的“10 月 8 日”是 arXiv **正式公告批次日期**，也是当日北京时间的日期；单篇首次提交时间可能在 10 月 7 日甚至更早，不能混为一谈。全部入选均在对应主分类的 `New submissions` 区段、且 arXiv API 为 v1；没有靠旧论文修订或近 30 天回溯凑数。[主分类核验记录](sources/primary-category-verification.json)与[PDF 文件核验结果](verification.json)可复查。

## 筛选与排序

扫描四个官方 new 列表（cs.AI、cs.CL、cs.LG，以及与主题有关的 cs.CV）后，去重获得 715 条新稿/交叉列出候选，其中 532 条在这四类至少一个 `New submissions` 区段。先以 PDF 首页核验机构，再按 **机构优先级 → 直接相关性 → 方法新颖性** 排序；同层级再看实验严谨性与潜在影响。S 为用户指定的头部公司与全球一流大学，A+ 为强研究机构/大型实验室，A 为优秀高校/研究团队，B 为方法突出的启发性补充；这不是对作者的价值判断。可信度 1–5 分完全独立，只评估这篇论文当前公开证据。下表的 novelty 为我的初步判断，并非论文自称或已被学界证实。

| 排名 | 论文与选择理由 | 机构（PDF 首页） | 优先级 / 相关性 / novelty | 证据可信度 |
|---|---|---|---|---|
| 01 | [Agent Plasticity](01-Meta-agent-plasticity.md) · [arXiv](https://arxiv.org/abs/2610.08902)：把经验学习效率和未来泛化分开测，是自演化记忆评测的基础。 | Meta Superintelligence Labs / Berkeley / Princeton 等 | S / 直接 / 高 | 4/5 |
| 02 | [MIMESIS](02-Meta-MIMESIS.md) · [arXiv](https://arxiv.org/abs/2610.09484)：真实行为模拟器为个性化 agent 提供更难的交互训练环境。 | Meta Superintelligence Labs / NYU / UW–Madison | S / 直接 / 高 | 4/5 |
| 03 | [Idea-level Critics](03-Meta-idea-critic.md) · [arXiv](https://arxiv.org/abs/2610.08993)：为自演化候选设置低成本验证门槛。 | Meta / Penn State | S / 直接 / 中高 | 3/5 |
| 04 | [Winner's Curse](04-Meta-Microsoft-winners-curse.md) · [arXiv](https://arxiv.org/abs/2610.09239)：指出反复选优可能把评测噪声写成“进步”。 | Meta / Microsoft | S / 弱相关但具启发性 / 高 | 4/5 |
| 05 | [Frozen Models, Evolving Expertise](05-NVIDIA-evolving-expertise.md) · [arXiv](https://arxiv.org/abs/2610.09146)：把技能、事实、多模态案例分离成可验证外部经验。 | NVIDIA / UMD | S / 直接 / 高 | 3/5 |
| 06 | [VideoEvolve](06-Alibaba-VideoEvolve.md) · [arXiv](https://arxiv.org/abs/2610.10183)：记忆写入和检索双侧自演化，跨向 LLM memory 有清晰启发。 | Alibaba / USTC / SJTU 等 | S / 直接 / 高 | 3/5 |
| 07 | [ExperienceIndex](07-MIT-ExperienceIndex.md) · [arXiv](https://arxiv.org/abs/2610.10091)：记住文档及文档对的任务经验，而非只存用户事实。 | MIT / Oracle AI–UPenn / AI2 等 | S / 直接 / 高 | 4/5 |
| 08 | [EncBank](08-Tsinghua-EncBank.md) · [arXiv](https://arxiv.org/abs/2610.10058)：跨查询复用压缩的 LLM 内部状态，是 latent memory 的系统路径。 | Tsinghua University | S / 直接 / 高 | 4/5 |
| 09 | [Personal Memory Failures](09-Berkeley-personal-memory-failures.md) · [arXiv](https://arxiv.org/abs/2610.10265)：把陈旧、归属与时延错误定位在生成前。 | UC Berkeley / Haas | S / 直接 / 高 | 4/5 |
| 10 | [Spatial Induction Heads](10-Cornell-spatial-ICL.md) · [arXiv](https://arxiv.org/abs/2610.09124)：为非连续结构的 ICL 给出构造与机制证据。 | Cornell University | S / 直接 / 高 | 4/5 |
| 11 | [FreeEvolve](11-AWS-FreeEvolve.md) · [arXiv](https://arxiv.org/abs/2610.09197)：连“怎样自我改进”也视作可迁移经验。 | AWS AI Labs / Georgia Tech | A+ / 直接 / 高 | 3/5 |
| 12 | [MemoryAgentBench Audit](12-Salesforce-MemoryAgentBench.md) · [arXiv](https://arxiv.org/abs/2610.09193)：用零学习规则基线揭示记忆基准的不可达 gold。 | Salesforce AI Research | A+ / 直接 / 高 | 4/5 |
| 13 | [MIRROR](13-Baidu-MIRROR.md) · [arXiv](https://arxiv.org/abs/2610.09795)：从参考模仿转向用户偏好内化。 | Baidu Inc. | A+ / 直接 / 中高 | 3/5 |
| 14 | [Knowledge Weaver](14-USTC-KnowledgeWeaver.md) · [arXiv](https://arxiv.org/abs/2610.10042)：以边际贡献和互信息管理知识库增长。 | USTC / SMU / NUS | A+ / 直接 / 高 | 4/5 |
| 15 | [SkillForge](15-CAS-SkillForge.md) · [arXiv](https://arxiv.org/abs/2610.09832)：让程序性记忆经历试用、稳定和退休。 | CAS ICT / UC Merced / Tsinghua | A+ / 直接 / 高 | 3/5 |
| 16 | [CASK](16-USTC-CASK.md) · [arXiv](https://arxiv.org/abs/2610.09008)：用话语归属阻止临时假设污染长期记忆。 | USTC | A+ / 直接 / 高 | 3/5 |
| 17 | [Sufficient Memory Sets](17-ZJU-sufficient-memory.md) · [arXiv](https://arxiv.org/abs/2610.09348)：跨会话问题需要证据集合充分性，不止单条相关性。 | ECNU / NTU / ZJU / SJTU / USC 等 | A+ / 直接 / 中高 | 3/5 |
| 18 | [HGP](18-NJU-HGP.md) · [arXiv](https://arxiv.org/abs/2610.10071)：端侧个性化的情景/语义/程序混合图记忆。 | Nanjing University / Jiutian Research | A / 直接 / 中 | 3/5 |
| 19 | [EngramEdit](19-PolyU-EngramEdit.md) · [arXiv](https://arxiv.org/abs/2610.10533)：直接编辑条件 latent memory 而冻结主干。 | Hong Kong PolyU / USTC 等 | B（方法补充）/ 直接 / 高 | 3/5 |
| 20 | [CoDR](20-PolyU-CoDR.md) · [arXiv](https://arxiv.org/abs/2610.08833)：训练免费地重审 diffusion LLM 已提交 token。 | Hong Kong PolyU / SUSTech | B（方法补充）/ 直接 / 中高 | 3/5 |

## 机构分布与主题趋势

按主导机构粗分：头部/大型企业研究团队 9 篇（Meta 相关 4、NVIDIA 1、Alibaba 1、AWS 1、Salesforce 1、Baidu 1），大学/学术主导 11 篇（MIT、Tsinghua、Berkeley、Cornell、USTC、CAS、ZJU/SJTU 合作、NJU、PolyU 等）；跨机构合作按主导方只计一次。优先级分布 S 10、A+ 7、A 1、B 2。B 的两篇并非为了凑数，而是分别覆盖条件/latent memory 可编辑性和 diffusion LLM 推断修正，且 PDF 实验可核查。

今天的共性是从“存更多”转向“写入/更新/检索/撤销的证据与代价”：ExperienceIndex、Knowledge Weaver、SkillForge 处理长期积累；CASK、伯克利个人记忆故障和 Salesforce 审计提醒写入与评测都可能制造假进步；VideoEvolve 把检索策略与存储策略联动；EncBank 和 EngramEdit 探索模型内部表征作为记忆接口。上述趋势是我的归纳，不是论文共同验证的结论。

## 最值得深读的 3 篇

1. **Agent Plasticity**：优先建立“从经验获得未来能力”的指标；后续评估任何 memory system 都可借其固定权重、独立 held-out 与成本框架。
2. **ExperienceIndex**：与共享论文/代码库的研究 agent 高度契合，单文档及文档对经验的表示很具体，且同时报告质量、迁移和费用。
3. **EncBank**：最贴近 latent memory 工程路线，公开了质量与存储/速度的负面取舍，适合做实际复现和资源预算。

另有强机构候选未进入 20 篇：[Tsinghua SkillCycle](https://arxiv.org/abs/2610.09430) 与 SkillForge 在技能库共演化上高度重叠；[Meta 的图像偏好个性化](https://arxiv.org/abs/2610.09015) 和 [Johns Hopkins 的 3D 对象记忆](https://arxiv.org/abs/2610.10538) 分别偏图像生成与具身空间，跨向 LLM memory 的启发清楚但距离主研究问题更远。它们是备选，不计入入选 20 篇。

## 核验与保留的时间记录

每篇的机构只取自 PDF 首页，实验评析还阅读了方法、实验与局限相关段落；不是只依摘要打分。20 份官方 PDF 均已下载到此文件夹，PDF header、可解析页数、v1 和主分类当天 `New submissions` 均经程序核验，共 568 页、41,594,758 字节；逐篇 SHA-256 和页数见 [verification.json](verification.json)。若文中提“未来影响”，均是我的推断；可信度评分不因机构强而上调。

- 北京时间约 08:01：[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new) 均仍显示 10 月 7 日，记为 pending。
- 北京时间约 09:01：三类仍显示 10 月 7 日，未纳入旧批次。
- 北京时间约 10:01：三类仍显示 10 月 7 日。
- 北京时间约 11:02：三类正式列表切换到 10 月 8 日；随后核验 cs.CV、主分类和各 PDF，完成本次报告。
