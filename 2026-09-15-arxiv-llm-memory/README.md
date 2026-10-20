# 2026-09-15 arXiv 论文精选：20 篇已完成

已保存 **20份官方PDF、20篇独立中文批判性笔记**，共479页、31,525,362字节（约31.5MB）。本期只收录 **Tuesday, 15 September 2026 正式公告的新论文**；早间未更新造成的pending已经补齐，不是当天没有好论文。

## 日期与核验范围

北京时间08:01至11:05，三个官方列表仍是9月14日；**12:05:09**保存的列表和RSS才核验到9月15日批次。本轮继续完成筛选，没有用9月14日或近30天旧论文补数。抓取时间不等于精确发布时间。[本日官方快照](sources/20260915T040509Z/batch-check.json)

以官方列表日期为准，提交日期另外记录：入选论文首次提交分布在9月11–14日，但全部属于本日New submissions，且当前核验版本均为v1。LION、BOOST、TwinICL最初只在抓取分类中以cross出现，分别追加核验cs.IR、cs.DC、cs.CV主分类的新投稿区。[主分类核验](sources/primary-category-verification.json)

按[arXiv发布规则](https://info.arxiv.org/help/availability.html)，美国东部夏令时晚20点对应次日北京时间08点；实际列表是否已刷新需要另查，不能把submitted日期、RSS构建时间或空RSS直接当作本日公告结论。

cs.CL / cs.AI / cs.LG排除Replacement后合并去重得**763条new/cross候选**，关键词筛查约281条较相关标题，下载32份重点候选原文，从中选出20篇。763不等于763篇首次发表新文，cross可能是旧文；本次也不是对763篇全部全文评审，更未穷尽所有arXiv学科。novelty是这个候选范围内结合机构偏好的主观阅读排序，不宣称客观全站最高。

机构按PDF首页核验；本文使用PDF技能提取方法/实验并对关键结果表进行视觉复核，没有修改原始PDF，没有实际重跑训练、工具环境或作者代码。

## 阅读主榜：先筛强机构，再排相关性与novelty

本期20篇均进入**A：强机构主榜**，没有普通机构或未核验机构补位。这个标签是本任务的阅读筛选门槛，不是对高校/公司的统一排名；进入同一档后，优先直接相关，随后保留有明确迁移启发的强机构工作。机构声誉不自动提高论文可信度。

N / C为主观新颖性 / 证据可信度，各1–5分、不是概率。每篇笔记均含问题、方法和实验、结论、未来影响、critical thinking、可信度及优缺点。作者直接证据与我的推断分节标示。

| 排名 | 论文／笔记与原文 | 首页核验机构 | 关联方向 | N / C |
|---|---|---|---|---|
| 1 | [LION](notes/01-LION.md) · [PDF](papers/01-LION.pdf) | Meta AI；National University of Singapore | personalized memory / self-evolving memory / 生成式推荐（非通用聊天LLM） | 4 / 3.5 |
| 2 | [Asclepius](notes/02-Asclepius.md) · [PDF](papers/02-Asclepius.pdf) | MIT；Harvard Medical School | self-evolving agent memory / 技能库 / 长时程执行 | 4 / 3.5 |
| 3 | [LabAgent](notes/03-LabAgent.md) · [PDF](papers/03-LabAgent.pdf) | Yale；Stanford；Broad Institute of MIT and Harvard；Northeastern | 科研agent / 程序性记忆 / 经验复用 | 4 / 3.5 |
| 4 | [Gavel](notes/04-Gavel.md) · [PDF](papers/04-Gavel.pdf) | 清华大学交叉信息研究院 | latent routing / skill memory / 稀疏读取 | 4.5 / 3.5 |
| 5 | [DA-DLM](notes/05-DA-DLM.md) · [PDF](papers/05-DA-DLM.pdf) | Tencent；ShanghaiTech University | diffusion LLM / 并行token依赖 | 4.5 / 4 |
| 6 | [TwinICL](notes/06-TwinICL.md) · [PDF](papers/06-TwinICL.pdf) | UCLA；NVIDIA AI Technology Center；NTU；Texas A&M；Arena | 直接相关｜多模态 in-context learning | 4 / 4 |
| 7 | [Convergent-ICL](notes/07-Convergent-ICL.md) · [PDF](papers/07-Convergent-ICL.pdf) | Johns Hopkins；MIT；UIUC | 直接相关｜跨领域 ICL / 共享任务难度 | 4.5 / 4 |
| 8 | [PLUME](notes/08-PLUME.md) · [PDF](papers/08-PLUME.pdf) | Nanyang Technological University；北京大学 | 直接相关｜参数化上下文 / 动态知识更新 | 4.5 / 3.5 |
| 9 | [MoME](notes/09-MoME.md) · [PDF](papers/09-MoME.pdf) | University of British Columbia；Vector Institute | 直接相关｜latent memory / 条件化稀疏查表 | 4.5 / 4 |
| 10 | [Superposition-Memory](notes/10-Superposition-Memory.md) · [PDF](papers/10-Superposition-Memory.pdf) | 中国科学技术大学；中关村学院 | 直接相关｜latent memory / 容量与保留策略 | 4.5 / 4 |
| 11 | [AgentKV](notes/11-AgentKV.md) · [PDF](papers/11-AgentKV.pdf) | Imperial College London；Columbia University | 直接相关｜agent KV memory / 阶段感知淘汰 | 4 / 4 |
| 12 | [Mind2Dialogue](notes/12-Mind2Dialogue.md) · [PDF](papers/12-Mind2Dialogue.pdf) | UC San Diego；Johns Hopkins；KU Leuven；UIC；Ohio State | 直接相关｜LLM personalization / 隐含心理状态监督 | 4 / 3.5 |
| 13 | [RESKILL](notes/13-RESKILL.md) · [PDF](papers/13-RESKILL.pdf) | HKUST（广州）；HKUST | 直接相关｜self-evolving skill memory / 失败归因 | 4 / 3.5 |
| 14 | [Temporal-Self-Distillation](notes/14-Temporal-Self-Distillation.md) · [PDF](papers/14-Temporal-Self-Distillation.pdf) | University of Basel；University of Amsterdam；Johns Hopkins | 直接相关｜diffusion LLM / 时间自蒸馏 | 4.5 / 4 |
| 15 | [LIMBO](notes/15-LIMBO.md) · [PDF](papers/15-LIMBO.pdf) | UC San Diego；West Virginia University | 直接相关｜memory system / 在线预算分配 | 4 / 3.5 |
| 16 | [AlgoEvo](notes/16-AlgoEvo.md) · [PDF](papers/16-AlgoEvo.pdf) | Huawei Noah’s Ark Lab；City University of Hong Kong；A*STAR | 直接相关｜self-evolving agent memory / 算法经验 | 4 / 3 |
| 17 | [LightningWeave](notes/17-LightningWeave.md) · [PDF](papers/17-LightningWeave.pdf) | MIT；NVIDIA | 弱相关但具启发性｜能力组合 / 策略蒸馏 | 4 / 3.5 |
| 18 | [HarnessBandit](notes/18-HarnessBandit.md) · [PDF](papers/18-HarnessBandit.pdf) | Alibaba Cloud；哈尔滨工业大学 | 相邻启发｜agent RL / 跨执行框架迁移 | 4 / 3.5 |
| 19 | [StellarColosseum](notes/19-StellarColosseum.md) · [PDF](papers/19-StellarColosseum.pdf) | Google Research；Carnegie Mellon University | 相邻强启发｜长期科研状态 / 验证与经验聚合 | 4 / 3.5 |
| 20 | [BOOST](notes/20-BOOST.md) · [PDF](papers/20-BOOST.pdf) | NVIDIA Research；Stanford；Georgia Tech | 弱相关但具启发性｜LLM serving / 物理内存分层 | 4 / 4 |

## 最值得先深读的3篇

1. **[LION](notes/01-LION.md)**：Meta/NUS，最直接回应个性化记忆随用户偏好变化而更新。重点看稀疏槽隔离与consolidation的交互；尚只在T5推荐模型验证，不能直接叫作通用LLM个人记忆。
2. **[Gavel](notes/04-Gavel.md)**：清华，读取冻结LLM内部状态做技能路由，很适合作为latent memory检索接口起点。重点检验正确加载技能能否转化为端到端任务成功，而非只赢检索指标。
3. **[Superposition Memory](notes/10-Superposition-Memory.md)**：USTC/中关村学院，为“向量能容纳多少推理状态”提供理论与受控实验。最适合发展新的研究问题，但要先处理非平稳、冲突和过期事实，不能泛化成永不遗忘。

如果这周优先做diffusion LLM，联读[DA-DLM](notes/05-DA-DLM.md)和[TSD](notes/14-Temporal-Self-Distillation.md)：前者约束同一步token依赖，后者把较晚的可靠预测提前，两者互补性尚待实验。

## 机构分布与主题趋势

按署名可重叠计数，产业合作涉及Meta 1篇、Tencent 1篇、NVIDIA及其AI Technology Center 3篇、Alibaba Cloud 1篇、Google Research 1篇、Huawei Noah 1篇，共8篇有上述产业机构署名。高校/科研机构包括MIT、Harvard Medical School、Broad Institute、Stanford、清华、UCLA、NUS、NTU、北京大学、USTC、Imperial、Columbia、JHU、UIUC、UCSD、UBC、Vector、HKUST、Basel、Amsterdam、CMU、CityU、A*STAR等。

不将使用Claude的Asclepius写成Anthropic论文；Google Research不改写为DeepMind；TwinICL的NVIDIA合作按首页AI Technology Center标注。没有为了机构配额凑OpenAI、Anthropic或ByteDance Seed；本期未入选不代表这些团队当天一定没有任何论文。

按主要阅读用途互斥分组：

- 参数化/潜在记忆与路由5篇：LION、Gavel、PLUME、MoME、Superposition。
- ICL2篇：TwinICL、Convergent ICL。
- 程序性经验与自进化4篇：Asclepius、LabAgent、RESKILL、AlgoEvo。
- diffusion LLM2篇：DA-DLM、TSD；个性化训练1篇：Mind2Dialogue。
- 工作记忆与预算2篇：AgentKV、LIMBO。
- 相邻能力/研究系统3篇：LightningWeave、HarnessBandit、StellarColosseum；弱相关物理内存系统1篇：BOOST。

我的趋势判断：研究正从“多存一点历史”转向三个更细问题——何时读取、用什么表示、经过何种验证才能更新。多数self-evolving系统对整体收益的证据比对memory独立贡献的证据强；这反而提供了可做严密消融的新课题。

## 不能只看headline的关键点

- **Asclepius**：留出关键行动+0.625显著，但固定技能/子agent后，进化手册额外整体分+0.02、p=0.88；系统有效不等于手册是主要原因。
- **LION**：仍持续训练共享backbone，槽隔离不是隐私隔离，也不是推理时无训练自进化。
- **PLUME**：保留文本单元用于查询路由，并非纯参数记忆；全局/局部分布分歧不等于局部证据可信。
- **MoME**：训练扩展约1.4B总参数；4B/8B上的延迟探测不是相同规模完成预训练的证明。
- **AgentKV**：中等预算有清楚收益；32B零售极低预算8.8对完整KV53.5，仍存在大幅能力损失。
- **LIMBO**：约83%节省是相对特定固定记忆基线；本地模型美元值是token价格代理，部分设置损失准确率。
- **Mind2Dialogue**：个性化提升可与心智推断退化同时发生；模拟心理状态不是现实用户事实。
- **RESKILL / AlgoEvo**：累计重试成功和继承代码的暖启动均不能直接当作长期记忆的因果增益。
- **TSD / BOOST**：NFE减少、同batch延迟、总吞吐、容量增加是不同口径，不能合写成一个通用加速倍数。

## 三个可接着开展的研究问题（尚未执行）

1. **条件化latent memory的冲突与删除测试**：以MoME/LION/PLUME为起点，固定容量与训练预算，加入偏好反转、错误更新、用户删除和邻近用户干扰。
2. **自进化经验的因果评估协议**：固定初始代码、LLM调用和总token，对Asclepius/RESKILL/AlgoEvo做“有无记忆×有无验证×是否继承代码”析因实验。
3. **DA-DLM与TSD的互补性小规模复现**：测同一步依赖与提前commit是否冲突，报告代码/结构化输出准确率、校准、真实墙钟而非只看NFE。

## 文件与完成核验

- [20篇清单及元信息](selection.json)
- [PDF页数、字节、SHA-256及公告归属](verification.json)
- [官方摘要页日期和版本元数据](sources/metadata.json)
- papers/为正式20篇；notes/为对应20篇评析。sources/保留32份候选PDF、抽取文本及网页快照，用于审计；未入选候选不算额外推荐。
- 已核验20个不同ID、20份有效PDF、每篇六个完整评析章节和本地链接。此前日期目录未修改。
- 调度状态：北京时间12:27完成文件核验后，已通过应用恢复原有每日北京时间08:00安排并回读确认ACTIVE，移除仅限9月15日的临时小时重试段落；原筛选与写作要求完整保留，没有新建重复任务。按[OpenAI Docs的同线程调度说明](https://learn.chatgpt.com/docs/automations?surface=app)操作；需要本地文件的运行请保持电脑开机和应用运行。

---

## 早间等待记录（原文保留；不是当前状态）

以下是本日报告完成前的历史记录。里面的pending、每小时重试和“尚未恢复”仅描述当时状态，不覆盖顶部完成结论。

# 2026-09-15 arXiv 日报：等待本日公告批次

北京时间 **08:01:22** 核查时，尚未看到9月15日正式公告批次。本日状态为 **pending（待核验／待续跑）**，不是“当天没有合格论文”，也不是已完成的20篇日报。

## 官方来源检查

| 来源 | 当前日期／状态 |
|---|---|
| cs.CL new | Monday, 14 September 2026 |
| cs.AI new | Monday, 14 September 2026 |
| cs.LG new | Monday, 14 September 2026 |
| cs.CL RSS | 9月14日，115条 |
| cs.AI RSS | 9月14日，270条 |
| cs.LG RSS | 9月14日，260条 |

三个RSS的构建时间为9月14日04:00 UTC附近，条目数量不能证明本日批次已更新。[检查结果与六份官方快照索引](sources/20260915T000122Z/batch-check.json)已保存。

官方动态入口：[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)。网页以后可能变化，本次判断以已存快照为准。

依照[arXiv发布说明](https://info.arxiv.org/help/availability.html)，美国东部夏令时晚20点对应次日北京时间08点；本任务需另行核验列表公告标签，不将提交日期、RSS构建时间或抓取时间视为公告日期。当前只确认接口仍显示旧批次，不据此断言arXiv发生故障或确定延迟原因。

## 续跑安排

已通过应用把现有 `arxiv-llm-memory` 任务临时改为每小时重试，仅用于补齐9月15日报告。采用OpenAI Docs说明的[同线程定时续跑](https://learn.chatgpt.com/docs/automations?surface=app)，没有创建重复任务。

当天批次可见后，继续机构优先筛选目标20篇，保存官方PDF和逐篇中文批判性笔记；不以9月14日论文或旧论文更新凑数。成功交付并核验后移除临时重试要求、恢复每日北京时间08:00。若本日23:00仍未完成或下次运行已跨日，记录确切阻碍并通知一次，同时恢复原调度。恢复依赖后续运行实际执行，目前尚未恢复。

没有新结果的重试仅追加记录，不反复通知。此前日期的论文及报告保持不变。

## 重试记录

- **09:03:37（北京时间）**：cs.CL、cs.AI、cs.LG三个官方列表仍显示9月14日；RSS日期、构建时间及条目数与08:01检查一致，六个来源均抓取成功。9月15日批次仍未核验，状态保持pending，不判定为当天无论文。已保存[本轮检查及六份原始快照](sources/20260915T010337Z/batch-check.json)，保留现有每小时重试安排。
- **10:04:44（北京时间）**：三个官方列表仍显示9月14日，三个RSS仍为相同日期、构建时间及条目数；六个来源均抓取成功。尚未核验到9月15日正式批次，未纳入旧论文。已保存[本轮检查及六份原始快照](sources/20260915T020444Z/batch-check.json)，状态保持pending，现有每小时重试继续。
- **11:05:07（北京时间）**：六个官方来源均抓取成功，三个列表仍为9月14日，RSS日期、构建时间和条目数仍未变化。9月15日批次尚未核验，未作“当天无论文”判断。已保存[本轮检查及六份原始快照](sources/20260915T030507Z/batch-check.json)，保留现有每小时重试。
