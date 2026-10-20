# 2026-09-16 arXiv 论文精选：20篇已完成

已保存 **20份官方PDF + 20篇独立中文批判性评析**，共576页、59,189,809字节（约59.2MB）。本期仅收录 **Wednesday, 16 September 2026 正式公告批次的新论文**。早间pending现已补齐；不是“当天没有论文”。完成核验时间：北京时间2026-09-16 11:06。

## 最值得先深读的3篇

1. [Register Tokens](notes/01-Register-Tokens.md)：Microsoft Research等，最直接连接latent memory与diffusion LLM。看连续寄存器如何跨块传递推理状态；尤其关注数学不如完整序列SFT、信息容量对照尚不公平的边界。
2. [Gating: Memorization vs. ICL](notes/02-Gating-Memory-vs-ICL.md)：Apple/Harvard，把遗忘门、参数记忆和上下文适应联系起来。适合设计用户偏好突变与冲突记忆实验，而不是简单得出“门控越弱越好”。
3. [Where Should a Document Live?](notes/03-Where-Should-Document-Live.md)：Amazon AGI，对比文本、KV与参数三种知识介质，适合直接借鉴存储预算、可组合性与能力干扰评测。

## 范围、日期与方法

cs.CL / cs.AI / cs.LG的官方HTML在08:52检查时仍为9月15日，10:44:02开始保存的[快照](sources/20260916T024402Z/batch-check.json)已全部显示9月16日。本次依据HTML正式New submissions，不等待滞后的RSS。抓取时间不等于精确公告发布时间；首次提交日期另记为9月13–15日，不将它误当公告日。

三个分类去掉Replacement、合并new/cross得到379条候选；关键词筛过约211条标题，下载27份重点候选全文，选20篇。379并不全是首次发表，cross也可能是旧文。入选20篇逐篇核验为v1，且有本日主分类或已抓取分类的New submissions证据。Social Harness仅在cs.AI为cross，因此额外核验了cs.MA主分类：[主分类核验](sources/primary-category-verification.json)。与本地往日selection.json没有重复ID。

本次不是379篇全部精读，也不宣称穷尽全站、找到客观唯一“novelty最高20篇”。排序是这个候选范围内按你的机构偏好作出的编辑判断。全文阅读重点是方法、主实验、局限及关键附录；没有独立运行作者代码。PDF技能用于抽取与关键表视觉核对，未改写任何原论文。

[选择清单](selection.json)保存作者、机构、日期、评分和文件映射；[核验清单](verification.json)保存每份PDF页数、大小、SHA-256与新公告来源；[候选目录](sources/catalog.json)、[官方元数据](sources/metadata.json)保留来源证据。个别无版本abs入口返回404时使用官方v1入口补齐，没有用第三方摘要替代全文。

## 20篇阅读榜

A1为头部工业研究或全球一流研究型高校合作主榜，共18篇；排序首先考虑机构研究实力与署名角色，再结合相关性、novelty及证据。A2为两篇国内强研究机构的高度相关专题补充，排在最后，不与头部工业机构混为同级。两档都不是统一的大学排行榜，也不表示机构为全部结论背书。普通或未核验机构没有补位。

同属A1的具体机构不做虚假的精确学术排名；强机构的相邻/弱相关论文仍保留，逐篇说明启发。N/C分别是主观新颖性与证据可信度，1–5分，不是概率。较低C的论文仍可高novelty，但需优先复核。

| 排名 | 笔记与原文 | PDF署名核验机构 | 相关性/研究标签 | N / C |
|---|---|---|---|---|
| 1 | [Register-Tokens](notes/01-Register-Tokens.md) · [PDF](papers/2609.16372.pdf) | Microsoft Research；University of Wisconsin–Madison；UC San Diego | 直接相关｜diffusion LLM、latent memory、有界状态推理 | 4.5 / 4 |
| 2 | [Gating-Memory-vs-ICL](notes/02-Gating-Memory-vs-ICL.md) · [PDF](papers/2609.16540.pdf) | Apple；Harvard University | 直接相关｜ICL、参数记忆、状态空间模型、门控 | 4.5 / 4 |
| 3 | [Where-Should-Document-Live](notes/03-Where-Should-Document-Live.md) · [PDF](papers/2609.17346.pdf) | Amazon AGI | 直接相关｜知识存储、KV memory、参数记忆、ICL | 4 / 4 |
| 4 | [EchoPath](notes/04-EchoPath.md) · [PDF](papers/2609.16635.pdf) | Johns Hopkins University；Amazon AGI | 直接相关｜GUI agent、可执行记忆、技能复用 | 4 / 3.5 |
| 5 | [ReDraft](notes/05-ReDraft.md) · [PDF](papers/2609.16639.pdf) | Tencent；Fudan University；Shanghai AI Laboratory | 直接相关｜continual learning、遗忘、自修订 | 4 / 3 |
| 6 | [Fuse-Social-Reasoning](notes/06-Fuse-Social-Reasoning.md) · [PDF](papers/2609.17496.pdf) | Google Research；Hebrew University of Jerusalem；University of Cambridge | 启发性相关｜personalization、用户叙述偏差、社会推理 | 4 / 4 |
| 7 | [Turn-Level-DRE](notes/07-Turn-Level-DRE.md) · [PDF](papers/2609.16760.pdf) | Alibaba Group | 启发性相关｜agent学习、轨迹信用分配、经验记忆 | 3.5 / 3.5 |
| 8 | [BLINDSPOT](notes/08-BLINDSPOT.md) · [PDF](papers/2609.16305.pdf) | IBM Research；Rensselaer Polytechnic Institute | 直接相关｜长期agent安全、状态/记忆污染、权限 | 4 / 3 |
| 9 | [SALVE](notes/09-SALVE.md) · [PDF](papers/2609.16927.pdf) | Stanford University | 启发性相关｜隐式偏好、数据审计、personalization | 4 / 4 |
| 10 | [ScienceBuddy](notes/10-ScienceBuddy.md) · [PDF](papers/2609.17523.pdf) | PhAI Labs；Fudan University；University of Oxford；Stanford University；Princeton University | 直接相关｜self-evolving agent、procedural memory、harness与模型协同 | 4 / 3.5 |
| 11 | [REALM](notes/11-REALM.md) · [PDF](papers/2609.16053.pdf) | Shanghai Jiao Tong University；OPPO；National University of Singapore | 直接相关｜memory system、图记忆、检索后再巩固 | 4 / 3 |
| 12 | [Early-Bird-Decoding](notes/12-Early-Bird-Decoding.md) · [PDF](papers/2609.16450.pdf) | Harvard University；Georgia Institute of Technology；Purdue University | 直接相关｜diffusion LLM、动态块、推理效率 | 3.5 / 4 |
| 13 | [Belief-State-Geometry](notes/13-Belief-State-Geometry.md) · [PDF](papers/2609.17376.pdf) | UCLA；UIUC；Simplex；Astera Institute；第一作者为独立研究者 | 直接相关｜ICL、latent state、机制可解释性 | 4.5 / 4 |
| 14 | [Diversity-Calibration-SFT](notes/14-Diversity-Calibration-SFT.md) · [PDF](papers/2609.16454.pdf) | Northwestern University；University of Chicago | 启发性相关｜personalization、SFT、多样性校准 | 4 / 4 |
| 15 | [Spurious-Tool-Use](notes/15-Spurious-Tool-Use.md) · [PDF](papers/2609.16268.pdf) | University of Washington；UC San Diego；Stanford University | 启发性相关｜agent策略、经验污染、因果泛化 | 4 / 3.5 |
| 16 | [LoopSpec](notes/16-LoopSpec.md) · [PDF](papers/2609.17184.pdf) | Seoul National University；KAIST | 启发性相关｜latent/recurrent compute、自推测解码、效率 | 4 / 4 |
| 17 | [Social-Harness](notes/17-Social-Harness.md) · [PDF](papers/2609.17527.pdf) | University of Washington, Seattle | 启发性相关｜多agent、私人记忆边界、授权与溯源 | 3.5 / 3.5 |
| 18 | [LLM-Inference-in-a-Flash](notes/18-LLM-Inference-in-a-Flash.md) · [PDF](papers/2609.16161.pdf) | UC Berkeley；ICSI；Lawrence Berkeley National Laboratory | 弱相关但具启发性｜KV压缩、存算协同、长上下文成本 | 4 / 3.5 |
| 19 | [ThinkFlow](notes/19-ThinkFlow.md) · [PDF](papers/2609.17010.pdf) | Peng Cheng Laboratory；Harbin Institute of Technology, Shenzhen；China Unicom Greater Bay Area Innovation Research Institute | 直接相关｜probabilistic latent memory、personalization、test-time evolution | 4 / 3 |
| 20 | [Interactive-Memory-Learning](notes/20-Interactive-Memory-Learning.md) · [PDF](papers/2609.17088.pdf) | Harbin Institute of Technology, Shenzhen；Peng Cheng Laboratory | 直接相关｜memory policy、延迟信用分配、self-evolving memory | 4 / 3 |

## 机构分布

按“是否有工业/独立研究机构共同署名”作互斥归组，避免把合作机构重复相加：

- A1中含头部或强工业研究署名：9篇。Microsoft Research、Apple、Amazon AGI（2篇）、Tencent、Google Research、Alibaba、IBM Research、OPPO。
- A1中以一流高校/实验室及其他合作研究机构为主：9篇。包括Stanford、Harvard、UCLA、UIUC、UW、UCSD、Northwestern、UChicago、SNU、KAIST、UC Berkeley等；ScienceBuddy含PhAI Labs主体与多所强校，Belief State含独立研究者及Simplex/Astera合作。
- A2专题补充：2篇，HIT Shenzhen/Peng Cheng Laboratory，其中ThinkFlow还含中国联通研究机构。
- 合作署名不等于共同主导。ScienceBuddy不能因作者背景被标成ByteDance Seed；LoopSpec使用Ouro模型也不等于ByteDance论文；本期没有凭模型名称冒认OpenAI/Anthropic机构成果。

## 今日主题趋势与可做的研究

**记忆介质决定能力边界。** Register Tokens与文档介质比较共同提示：压缩质量、状态可组合性、遗忘/干扰和推理训练目标应该一起评估。可做“等字节/等计算预算的文本、KV、连续槽位与LoRA”对比，而非仅匹配token位置数。

**读取本身也在改变系统。** REALM读后再巩固、EchoPath执行记忆、ScienceBuddy技能修订、ICML延迟回报，分别把查询、执行和反馈变成更新信号。核心风险是将偶然成功、错误前提或额外oracle信息误当可靠经验。

**个性化不只是更记得住，也要更少误解。** Fuse、SALVE、多样性校准共同强调：用户叙述的解释、潜在偏好和真实事实不能混写。可建立带来源、置信度、版本及授权期限的个人记忆，并测试偏见污染后的纠错速度。

**效率必须与质量和口径绑定。** Early-Bird存在精度取舍；LoopSpec测decode而非整请求；Flash的系统收益是硬件模型估算。报告峰值加速时必须附强基线、硬件、batch与质量条件。

## 最需要警惕的证据边界

- Register Tokens：表1修正评分后，完整序列SFT在8个数学设置全部更高；不要将历史检查点/旧评分表与当前结果混算。
- ReDraft：摘要汇总与附录六设置直接均值未对齐；附录表注“全部达到或超过SFT”也有反例。已视觉核对，不是抽取列错位。
- REALM：LongMemEval先用oracle session生成历史问题暖启动，必须给基线同等待遇再归因。
- BLINDSPOT：部分表格的总体危险率与“拒绝后危险完成”子集比例关系需作者澄清，当前不用于精确安全排名。
- EchoPath：91.2%来自首轮成功后保留的159条记忆，不是完整OSWorld新任务成功率；错误起始gate仍有误放行。
- ThinkFlow / ICML：latent可视化不证明因果解耦；下一话语预测/LLM质量奖励不等于真实用户满意。两篇均标出在线时间顺序和用户隔离需要复核。

## 调度与交付检查

20篇PDF与笔记均已验证：文件有效、至少一页、20个唯一ID、20份笔记均含6个编号分析章节，最短笔记1735字符；71个本地链接全部有效，20份PDF的SHA-256均与核验清单一致。往日文件夹未修改。

现有arxiv-llm-memory任务已通过应用恢复为**每日北京时间08:00，ACTIVE**；仅移除9月16日临时小时重试前缀，原筛选要求完整保留，未新建重复任务。更新后重新读取配置，确认每日调度与原同线程目标均正确。定时触发不代表当天原文评析会在08:00瞬间完成；若正式批次尚未可见，应保留明确pending而不声称无论文。[调度说明](https://learn.chatgpt.com/docs/automations?surface=app)

以下保留今天早间检查历史，以区分“未完成”和“无新公告”；不再代表当前完成状态。

---

## 早间运行历史（保留原文）

# 2026-09-16 arXiv 日报：待核验本日公告批次

本轮状态为 **pending（待核验／待续跑）**。尚未完成今日20篇精选；不是“当天没有合格论文”，也未将昨天论文或近30天旧文计入今天。

## 10:44续跑进展

北京时间10:44:02开始的[本轮快照](sources/20260916T024402Z/batch-check.json)中，cs.CL、cs.AI、cs.LG正式HTML列表均已显示 **Wednesday, 16 September 2026**，状态推进为 **researching（筛选与原文评析中，尚未交付）**。cs.CL/cs.LG RSS的pubDate仍是9月15日，虽然构建时间已更新；cs.AI RSS超时。按正式HTML新投稿区继续，不等RSS同步，不把其条目数当本日数量。new/cross去重候选379条，已开始强机构候选原文核验。

## 本轮检查与证据

快照检查始于北京时间 **08:52:52**，结果返回后于 **09:08** 确认。08:07是本次自动任务的触发时间，不是网页实际抓取时间；各请求共享的checked_at字段是本轮开始时间，不表示每个响应的准确完成时间。

| 官方来源 | 本轮结果 |
|---|---|
| cs.CL new | 抓取成功，Tuesday, 15 September 2026 |
| cs.AI new | 抓取成功，Tuesday, 15 September 2026 |
| cs.LG new | 抓取成功，Tuesday, 15 September 2026 |
| cs.CL RSS | 超时，响应不完整，未作为有效快照或日期证据 |
| cs.AI RSS | 超时，响应不完整，未作为有效快照或日期证据 |
| cs.LG RSS | 超时，响应不完整，未作为有效快照或日期证据 |

[核验结果、错误记录及三份有效HTML快照索引](sources/20260916T005252Z/batch-check.json)。三份HTML均未匹配9月16日。RSS无法核验日期、构建时间或条目数，不能宣称其为空、没有新文或与网页一致。

官方动态入口：[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)。后续页面可能变化，历史观测以保存的快照为准。

## 日期口径

依[arXiv官方发布说明](https://info.arxiv.org/help/availability.html)，美国东部夏令时晚20点对应次日北京时间08点。本任务采用官方公告批次核验，再分开记录首次提交日期、版本和抓取时间；不以submitted日期推断新公告。今天不根据旧页面或网络超时判断为休刊日，也不臆测页面延迟原因。

## 续跑安排

依据OpenAI Docs的[同线程定时续跑说明](https://learn.chatgpt.com/docs/automations?surface=app)，已通过应用将现有arxiv-llm-memory任务临时改为每小时重试，仅用于补齐9月16日报告。没有创建第二个任务，原机构优先、当日范围、六项笔记和不覆盖往日报告等要求完整保留。

本日正式批次一旦核验可见，就继续筛选、下载原文并完成评析；只要HTML提供有效新投稿证据，RSS失败不应阻止筛选。完成并验证后恢复每日北京时间08:00。若本日23:00仍未完成，或下次运行已跨日，记录确切阻碍并通知一次，同时恢复原调度；恢复依赖后续运行实际执行，目前仍处于临时重试状态。

无变化的重试只追加检查记录，不反复通知。机构分布、主题趋势和深读前三篇待正式筛选完成后补充。过去日期的文件夹未修改。
