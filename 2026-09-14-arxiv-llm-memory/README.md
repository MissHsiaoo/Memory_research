# 2026-09-14 arXiv 论文精选：20 篇已完成

已保存 **20 份有效官方 PDF、20 篇独立中文批判性笔记**，共 421 页、27,545,509 字节（约27.5 MB）。本期只收录 **Monday, 14 September 2026 正式公告的新论文**，没有用旧论文或旧版本更新凑数。

## 日期、来源与筛选范围

北京时间08:02和09:06列表仍未更新；10:06:52复查时，cs.CL／cs.AI／cs.LG均已显示9月14日。RSS虽然构建时间变了，仍为空，不能据此判断当天没有论文；本次以正式HTML列表为主。[当天公告快照](sources/20260914T020652Z/batch-check.json)

按[arXiv官方发布规则](https://info.arxiv.org/help/availability.html)，9月美国东部夏令时晚20点对应次日北京时间08点。这里采用官方列表的9月14日标签和北京时间本日文件夹；实际抓到更新的时间不等于精确发布时间。提交时间、列表日期与RSS构建时间分开记录，**不按“最近24小时submitted”推断公告归属**。

三分类去除Replacement submissions后，new/cross合并去重得 **313条候选**。这不是313篇全部首次发表的新文：cross可能包含旧文，必须再查主分类。初筛标题、摘要和作者后，下载30份重点候选PDF核查，其中正式20篇都有有效PDF及笔记。未对313篇逐篇全文评审，也未穷尽所有arXiv学科；“最高novelty”是此范围内结合机构偏好的主观选择，不是客观全站排名。

20篇全部核验为v1，并至少出现在当日一个主分类的 **New submissions** 中。Bash Interfaces、Reality Is the Final Verifier在cs.SE，VideoXAgent在cs.CV，已另外保存[主分类核验](sources/primary-category-verification.json)。Fixed State首次提交是9月9日，但确实在9月14日cs.LG的新投稿区，因此不能因提交日期较早而误删，也不能仅凭v1判断新旧。

API元数据接口遇到429，改用官方摘要页保存日期和版本；没有把API失败解释为论文不存在。[逐篇元数据](sources/metadata.json)保留来源，日期精度为天，精确提交时间可看对应abs快照的Submission history。

## 阅读主榜

先按机构优先级分层，再结合直接相关性、novelty与证据排序。A层为1–14；B层为15–20，是强专业团队和研究机构的补充，优先级低于A，不以相关性覆盖机构偏好。此分层是阅读资源分配偏好，不是学校/公司的客观总排名；企业合作署名不代表所有实验均由企业执行。

N / C分别为主观新颖性与证据可信度，均1–5分、不是概率。机构声誉不会自动提高C；强机构的弱相关工作也保留清晰的迁移理由。

| 排名 | 论文／笔记与原文 | 核验机构 | 相关性 | N / C |
|---|---|---|---|---|
| 1 | [CanvasAnneal](notes/01-CanvasAnneal.md) · [PDF](papers/01-CanvasAnneal.pdf) | Google DeepMind | 直接相关 | 4 / 3.5 |
| 2 | [AIM](notes/02-AIM.md) · [PDF](papers/02-AIM.pdf) | Microsoft | 直接相关 | 4 / 3.5 |
| 3 | [SAS](notes/03-SAS.md) · [PDF](papers/03-SAS.pdf) | Tencent HY／HKUST | 直接相关 | 4 / 4 |
| 4 | [RIPPLE](notes/04-RIPPLE.md) · [PDF](papers/04-RIPPLE.pdf) | Amazon | 直接相关 | 4.5 / 3.5 |
| 5 | [BQ-LoRA](notes/05-BQ-LoRA.md) · [PDF](papers/05-BQ-LoRA.pdf) | Alibaba Cloud | 相邻强启发 | 4 / 3.5 |
| 6 | [Affective-Agent](notes/06-Affective-Agent.md) · [PDF](papers/06-Affective-Agent.pdf) | Harvard | 直接相关 | 3.5 / 3 |
| 7 | [GAUGE](notes/07-GAUGE.md) · [PDF](papers/07-GAUGE.pdf) | Amazon | 相邻强启发 | 4 / 4 |
| 8 | [WinSyn](notes/08-WinSyn.md) · [PDF](papers/08-WinSyn.pdf) | MSR India | 直接相关 | 3.5 / 3.5 |
| 9 | [GLARE](notes/09-GLARE.md) · [PDF](papers/09-GLARE.pdf) | Microsoft／USC等 | 相邻强启发 | 4 / 3.5 |
| 10 | [ESRL](notes/10-ESRL.md) · [PDF](papers/10-ESRL.pdf) | MSR／清华 | 弱相关但具启发性 | 4 / 4 |
| 11 | [SQD](notes/11-SQD.md) · [PDF](papers/11-SQD.pdf) | NVIDIA／Harvard | 弱相关但具启发性 | 4 / 3.5 |
| 12 | [Bash-Interfaces](notes/12-Bash-Interfaces.md) · [PDF](papers/12-Bash-Interfaces.pdf) | Microsoft／CMU | 相邻启发 | 3.5 / 4 |
| 13 | [EHR-Trajectory-RL](notes/13-EHR-Trajectory-RL.md) · [PDF](papers/13-EHR-Trajectory-RL.pdf) | MIT／MSR | 弱相关但具启发性 | 3.5 / 3.5 |
| 14 | [Reality-Final-Verifier](notes/14-Reality-Final-Verifier.md) · [PDF](papers/14-Reality-Final-Verifier.pdf) | UC Berkeley | 相邻强启发 | 3.5 / 3 |
| 15 | [Fixed-State-Block-Diffusion](notes/15-Fixed-State-Block-Diffusion.md) · [PDF](papers/15-Fixed-State-Block-Diffusion.pdf) | ServiceNow／Mila | 直接相关 | 4.5 / 4 |
| 16 | [LifeMem](notes/16-LifeMem.md) · [PDF](papers/16-LifeMem.pdf) | Baidu／北理等 | 直接相关 | 4 / 3.5 |
| 17 | [VideoXAgent](notes/17-VideoXAgent.md) · [PDF](papers/17-VideoXAgent.pdf) | Baidu | 相邻强启发 | 3.5 / 3.5 |
| 18 | [OneLA](notes/18-OneLA.md) · [PDF](papers/18-OneLA.pdf) | Kuaishou／HKU／PKU | 相邻强启发 | 4 / 4 |
| 19 | [RunningTensor](notes/19-RunningTensor.md) · [PDF](papers/19-RunningTensor.pdf) | Sorbonne／Berkeley Lab | 直接相关 | 4.5 / 2.5 |
| 20 | [LifeFuse-Mem](notes/20-LifeFuse-Mem.md) · [PDF](papers/20-LifeFuse-Mem.pdf) | BAAI／中科院等 | 直接相关 | 4 / 3 |

## 最值得先深读的三篇

1. **[CanvasAnneal](notes/01-CanvasAnneal.md)**：Google DeepMind、直接diffusion LLM。适合探索“经验证的历史推理支架→训练时课程→无支架推理”；需警惕教师蒸馏与探索改善混在一起，部分任务结果是负面。
2. **[AIM](notes/02-AIM.md)**：Microsoft、直接多用户记忆。把CRUD、状态错误级联、私有/共享边界同时纳入测量，适合扩展personalized memory；当前隐私分类不是安全保证。
3. **[RIPPLE](notes/04-RIPPLE.md)**：Amazon、直接持久策略修订。最值得借鉴的是经验在组合后重新验证，局部有效的规则可能与已存记忆相互破坏。

如果这周更偏latent架构，把[SAS](notes/03-SAS.md)和[Fixed State](notes/15-Fixed-State-Block-Diffusion.md)作为下一组：前者优化读什么，后者优化怎样缓存。RunningTensor有高新意，但当前稿件证据完整性不足，暂不作为首个高成本复现目标。

## 机构分布与取舍

按“有该机构署名的论文数”计，合作机构可重叠：Microsoft／MSR共6篇，Amazon2篇，Baidu2篇，Google DeepMind1篇，Tencent1篇，Alibaba1篇，NVIDIA1篇，ServiceNow1篇，Kuaishou1篇；Harvard2篇、MIT1篇、CMU1篇、UC Berkeley1篇，以及清华、HKUST、HKU、PKU、Mila、Sorbonne、BAAI等合作或专业团队。

本期主榜没有标为OpenAI、Anthropic或ByteDance Seed署名的论文；这不等于这些机构当天没有发表任何工作。使用GPT、Claude或Gemini不等于来自其供应商。AIM仅按Microsoft署名，未自行升级为MSR；RunningTensor的Berkeley Lab不是UC Berkeley。

本轮也核查了CueMem、CORE、BlueLM-GUI、EvoRS等直接或相邻工作，但未全部放进主榜：按照你的机构优先偏好，保留了NVIDIA系统、MIT/MSR结构化轨迹和Berkeley经验维护等跨方向启发。它们不是无价值，只是本次20个名额的取舍。没有为了凑齐每个研究标签而强行固定配额。

## 今天最重要的趋势与反例

- **写入需要授权和语义边界**：AIM控制谁能读，LifeFuse控制什么应长期保留，RIPPLE控制什么在当前策略组合下可持久化。三者解决不同问题，不能互相替代。
- **读取目标应是决策效用**：SAS学习在预算内选上下文；WinSyn显示检索排序更好未必终答更完整；VideoXAgent按问题动态恢复证据。
- **常量状态不意味着无损信息**：Fixed State的效率证据比长程语义质量更强；RunningTensor以更高阶状态换容量，必须对齐state bytes而非只对齐参数量。
- **经验复用不是自证成功**：LifeMem总体有益但存在局部负迁移；Bash接口实验中持久工具复用没有稳定净收益；GAUGE显示满意度可能完全漏掉任务失败。

## Headline 必须附带的限制

| 工作 | 不能忽略的边界 |
|---|---|
| AIM | 96% visibility来自GPT-5.4；58.8% strict来自mini。不能合成一个配置的成绩。 |
| CanvasAnneal | GSM8K纯RL比较为负；特定奖励阈值的步数加速不等于全成本加速。 |
| RIPPLE | +23.1是服务验证通过率的百分点；结构正确率只+0.8点。 |
| SAS | prefill仍dense；512K时Top-K占稀疏decode约90%，整体并非严格常量复杂度。 |
| Affective Agent | 1600个合成决策点，不是真人干预实验；端侧推理约54–83秒且不含整个感知流程。 |
| SQD | B200节流代理、调整功耗和未来硬件分析模型，不能当作完整实机部署收益。 |
| Fixed State | 256K测的是效率；16K平均NIAH仅22.3%，最近位置高不能代表全历史记得住。 |
| RunningTensor | 当前PDF仅有MQAR表，摘要声称的真实任务结果表缺失；第6页Conclusion为空，已视觉核验。 |
| LifeFuse-Mem | 保留率以已经学会的事实为条件，并依赖受控生命周期信息；整体长期问答约20%。 |

## 三个可做成实验的拓展

以下是我的研究假设，未完成先行工作穷尽检索，也不是原论文已经验证的组合创新。

### 1. 可撤回、可组合的用户记忆提交机制

结合AIM的权限、LifeFuse的时间承诺与RIPPLE的重放：每条候选记忆带owner、valid-from/to、证据、冲突依赖和policy版本。比较直接追加、单条验证、组合后验证，固定LLM调用预算。测隐私假公开率、冲突后用户任务成功率、误删除/误保留、维护成本；不要只测抽取F1。

### 2. 共享历史下的latent分支探索

结合Fixed State／RunningTensor的递归状态与OneLA的分支增量思想，探索多个agent计划共享基础记忆。必须分别控制参数量、state bytes、总FLOPs和分支深度；测罕见事实召回、分支串扰、合并错误、失效后的恢复成本。高阶状态的容量增加不能免费计入方法优势。

### 3. 用可信历史支架训练diffusion agent

把CanvasAnneal的teacher前缀替换为经过任务验证的历史经验，比较正确、错误、过时以及跨用户不适用的支架。用纯RL、同预算SFT、去教师位置损失作对照；测试时完全撤去支架。同时采用GAUGE式可验证任务结果，避免只提高裁判满意度或训练奖励。

## 文件与核验

- `papers/`：正式20篇官方PDF；`notes/`：对应20篇中文笔记，均含六个要求部分。
- [selection.json](selection.json)：正式名单、机构、排序、评分及阅读范围。
- [verification.json](verification.json)：各PDF页数、大小、SHA-256、v1和当日主分类公告证据。
- [catalog.json](sources/catalog.json)：313条候选及公告快照；`sources/`中的其余候选PDF不是正式推荐名单。
- 正式20篇不含以前已推荐的ID；所有本地笔记/PDF/快照链接会做存在性检查。

依照PDF阅读技能提取原文、检查机构与实验，并视觉核验CanvasAnneal首页、AIM结果表和RunningTensor的空结论页。没有复跑作者代码，没有逐页审阅全部421页，也没有证明每篇理论结果；各笔记标明实际阅读范围和证据缺口。新PDF保留原样，未改写论文内容。

## 调度状态

日报和PDF/笔记已核验；已通过应用移除今日临时按小时重试段落，恢复北京时间每天08:00，原任务保持启用。下方保留此前等待发布的原始记录，不再代表最终状态。

---

## 历史记录：早晨等待官方批次更新


截至北京时间 2026-09-14 08:02:35，尚未核验到本日正式公告批次。**这是待发布/待核验状态，不是“今天没有合格论文”，也不是已完成的日报。**

## 本次检查证据

- 官方 cs.CL、cs.AI、cs.LG new 列表均仍显示 `Friday, 11 September 2026`。
- 三个 RSS 均为 0 条，但 pubDate 为 `Sun, 13 Sep 2026 00:00:00 -0400`，lastBuildDate 为 `Sun, 13 Sep 2026 04:00:00 +0000`；旧空 RSS 不能证明目标批次没有论文。
- [检查结果及原始快照索引](sources/20260914T000235Z/batch-check.json)。
- 官方入口：[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)。动态网页以后可能变化，以本地快照记录本次观察。

## 续跑安排

已通过应用成功更新原有 `arxiv-llm-memory` 任务：临时每小时重试，仅用于补齐本日未完成的日报。同一线程不支持另挂第二个定时任务，因此没有创建重复任务。

批次可见后，继续按“机构质量优先、其次相关性与 novelty”筛选，目标 20 篇，下载 PDF 并逐篇写中文批判性笔记，不以旧文填补数量。完成后恢复每日北京时间 08:00 调度。若到本日 23:00 仍未完成，或下次运行已跨日，则记录阻碍、报告未完成并恢复原调度。恢复依赖后续任务实际运行，不能视为已经恢复。

以前日期的成果不受影响；[9 月 11 日补发的 20 篇](../2026-09-11-arxiv-llm-memory/backfill/README.md)已经完成，本日不会重复计入。

## 重试记录

- **09:06:32（北京时间）**：三个官方列表仍为 9 月 11 日批次；三个 RSS 仍为 9 月 13 日构建的空源。本日公告依旧未核验，状态保持 pending，不作“无合格论文”判断。已保存[本轮检查和六份原始快照](sources/20260914T010632Z/batch-check.json)，保留每小时重试安排。
