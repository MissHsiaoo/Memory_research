# 2026-10-07 arXiv LLM Memory 日报 — 已完成

- 核验时间：2026-10-07 08:02（北京时间，Asia/Shanghai；即 2026-10-07 00:02 UTC）。
- 官方 [cs.CL/new](https://arxiv.org/list/cs.CL/new)、[cs.AI/new](https://arxiv.org/list/cs.AI/new)、[cs.LG/new](https://arxiv.org/list/cs.LG/new) 均仍显示 **Tuesday, 6 October 2026** 的正式公告列表，尚未出现 10 月 7 日批次。
- 当前状态：**pending**，不是“今日没有合格论文”。不能把昨天的 `New submissions`、今天可见的旧稿更新版或论文提交日期误当作今天的正式公告；也不向近 30 天扩展。
- 本日正式公告出现后再从三个分类的 `New submissions` 区筛选，核验机构、PDF、方法和实验，并在本目录增量交付。

## 增量核验

- 2026-10-07 09:01（北京时间）：cs.CL、cs.AI、cs.LG 官方 `new` 列表仍均显示 10 月 6 日批次；本日仍为 pending，未取用旧稿。
- 2026-10-07 10:00（北京时间）：三类官方 `new` 列表仍均显示 10 月 6 日批次；状态无变化。
- 2026-10-07 11:01（北京时间）：三类官方 `new` 列表均已切换为 **Wednesday, 7 October 2026**；`New submissions` 分别为 cs.CL 79、cs.AI 156、cs.LG 196 篇。自此开始仅筛选该正式公告批次的新稿。

## 最终交付与口径

- **状态：已完成。** 上面的 pending 文字是早间核验记录，已被 11:01 正式公告及本节取代；保留它是为避免把提交时间误当公告时间。
- 当天三个分类共 431 篇 `New submissions`（按主分类计，无跨分类重复），本目录收录其中 **20 篇**，均保存官方 PDF，且 PDF 可解析。每篇单独的中文笔记写明首次提交日期；多数实际提交于 10 月 3–6 日，但正式公告均为 **10 月 7 日**。没有从 `Cross submissions`、`Replacement submissions` 或旧日期补数。
- 排序先按**机构优先级**（S：优先产业研究机构/公司参与；A：一流高校/实验室主导），再按直接相关性、方法原创性和证据质量。同层级内有些企业不在例举清单，但有经 PDF 首页核验的高质量研究团队；机构声望与论文可信度是两项独立判断。两篇仅间接关联记忆主题的强机构论文已明确标“弱相关但具启发性”。
- 全部方法/实验数字均为论文直接报告，**非本人复现**。对真实用户、真实长期部署的可能影响均标为推断；可信度分数不因机构强而自动提高。

## 入选论文：机构 → 相关性 → novelty

| 排名 | 论文 / 本地评析 / arXiv | 首页核验机构 | 选择理由与边界 |
|---:|---|---|---|
| 01 | [按类别决定记忆是否写入](01-Meta-category-conditioned-memory.md) · [arXiv](https://arxiv.org/abs/2610.07100) | Meta AI · S | 直接解决用户记忆写入污染；价值观类阈值需要更强证据，但只在合成语料评测。 |
| 02 | [跨平台个人 Agent 推荐调解](02-Meta-personal-agent-recommendation.md) · [arXiv](https://arxiv.org/abs/2610.07588) | Meta AI / UCSD · S | 以用户侧跨平台历史修正推荐，同时显式控制 harmful override。 |
| 03 | [DSV-Mem](03-Amazon-DSV-Mem.md) · [arXiv](https://arxiv.org/abs/2610.08102) | Amazon AGI / USC · S | 专业场景中追踪多模态文档的版本、权威与状态，基准设计有新意。 |
| 04 | [MemCo](04-NVIDIA-MemCo.md) · [arXiv](https://arxiv.org/abs/2610.07376) | NVIDIA / UBC / Vector · S | 局部与全局记忆协作，研究如何向未见环境迁移经验。 |
| 05 | [SAGA](05-Alibaba-SAGA.md) · [arXiv](https://arxiv.org/abs/2610.06964) | Alibaba / SJTU / USTC · S | 将轨迹逐级提炼为带适用条件和来源证据的原则。 |
| 06 | [PERSIST](06-Huawei-PERSIST.md) · [arXiv](https://arxiv.org/abs/2610.07725) | Huawei / Tsinghua · S | 多人语音记忆显式建模谁、什么、何时及计划修订。 |
| 07 | [Continuous Memory Machines](07-Sakana-continuous-memory-machines.md) · [arXiv](https://arxiv.org/abs/2610.07907) | Sakana AI / Tsukuba · S | 短/长时矩阵状态双向读写，latent memory 架构直接相关。 |
| 08 | [UNREAL](08-NVIDIA-UNREAL.md) · [arXiv](https://arxiv.org/abs/2610.08463) | NVIDIA / Technion · S | 模型内部证据选择连接海量语料检索与长上下文；规模化实验强。 |
| 09 | [ServeLearnBench](09-Amazon-ServeLearnBench.md) · [arXiv](https://arxiv.org/abs/2610.07792) | Amazon / CMU · S | 流式环境中检验 Agent 能否从服务经验持续学会变化规则，含负面结果。 |
| 10 | [TALA](10-Alibaba-TALA.md) · [arXiv](https://arxiv.org/abs/2610.08138) | Alibaba / NTU / SDU · S | 测试时案件经验检索、改造与巩固，跨角色程序校验。 |
| 11 | [ReFold](11-Intel-ReFold.md) · [arXiv](https://arxiv.org/abs/2610.07863) | Intel / UCSB · S | 保留完整历史、只折叠模型可见视图，记忆压缩可逆。 |
| 12 | [压缩时机的弱可预测性](12-Salesforce-compaction-risk.md) · [arXiv](https://arxiv.org/abs/2610.08722) | Salesforce AI Research · S | 590 个配对压缩边界，克制地报告“最近历史难以预测压缩伤害”。 |
| 13 | [Fork-and-Flush](13-Microsoft-Fork-and-Flush.md) · [arXiv](https://arxiv.org/abs/2610.07447) | Microsoft Research · S | **弱相关但具启发性**：保留工作区、清空聊天以跳出研究想法盆地。 |
| 14 | [FC-SWE](14-NVIDIA-FC-SWE.md) · [arXiv](https://arxiv.org/abs/2610.07898) | NVIDIA / Tsinghua · S | **弱相关但具启发性**：把验证失败变成恢复训练信号，可借鉴失败经验记忆。 |
| 15 | [CAGD](15-Tsinghua-CAGD.md) · [arXiv](https://arxiv.org/abs/2610.06940) | Tsinghua AIR / Nanjing U · A | 用少量旧条件保护持续学习行为；明确披露大模型数学任务的负结果。 |
| 16 | [STAVE](16-STAVE-two-vectors-ICL.md) · [arXiv](https://arxiv.org/abs/2610.07572) | UW–Madison / Northwestern · A | 两个任务向量替代重复的 ICL 示例；训练成本与零示例推理要分开看。 |
| 17 | [Stateless Language Agents](17-Stanford-stateless-agents.md) · [arXiv](https://arxiv.org/abs/2610.07625) | Stanford / CMU / UW / UC Berkeley 等 · A | “有状态搜索、无状态 Agent”，长期研究状态由 harness 持有。 |
| 18 | [DeltaTTT](18-Tsinghua-DeltaTTT.md) · [arXiv](https://arxiv.org/abs/2610.08553) | Tsinghua / IQuest · A | 找到非线性循环记忆的优化瓶颈，提出逐层更新。 |
| 19 | [HMED](19-HMED-meta-experience.md) · [arXiv](https://arxiv.org/abs/2610.07979) | CUHK / SJTU · A | 同起点重放旧/新元技能，记录修改本身的后果作为元经验。 |
| 20 | [A2D](20-EPFL-A2D-diffusion.md) · [arXiv](https://arxiv.org/abs/2610.08108) | EPFL · A | 将 AR 后训练权重增量迁移到 diffusion LLM，覆盖多模型/多任务。 |

## 机构分布与主题趋势

- 产业高优先级机构参与 **14/20**，一流高校/实验室主导 **6/20**；没有“机构未核验”或普通机构凑数条目。多机构论文按最高经核验机构只计一次。PDF 首页署名与推荐排序都可在各笔记核对。
- 本日最突出的主线是**记忆的生命周期**：写入时避免不实用户画像（01），执行时区分局部/全局、谁说的、哪个版本有效（03–06），服务经验如何更新（09–10），以及压缩/保留的代价与失败边界（11–12）。
- 第二条主线是**隐藏状态与上下文的分工**：Sakana 的短/长时矩阵记忆、DeltaTTT 的非线性写入优化、NVIDIA 的内部证据选择，与 Stanford 将持久状态移出聊天的系统设计形成互补而非单一答案。
- 个性化方向今天有 Meta 的用户侧跨平台推荐；ICL 有 STAVE；diffusion LLM 有 CAGD 与 A2D。直接研究 personalized memory 的论文仍缺真实用户长期验证，尤其是隐私、偏好漂移与错误推断的伤害。

## 最值得深读的 3 篇

1. [Meta 的记忆写入门槛](01-Meta-category-conditioned-memory.md)：最直接触及个性化记忆的“错误画像”风险；重点核查合成 persona/LLM judge 是否高估真实性。
2. [Amazon DSV-Mem](03-Amazon-DSV-Mem.md)：把专业工作流中的状态更新与来源权威做成可测问题；适合据此设计更严格的 Agent memory benchmark。
3. [Sakana Continuous Memory Machines](07-Sakana-continuous-memory-machines.md)：短时计算/长时保存的架构分离最贴近 latent memory；重点检验收益是否超出参数与计算容量增加。若当前重点是个性化推荐，下一篇优先读 [Meta 跨平台个人 Agent](02-Meta-personal-agent-recommendation.md)。

## 证据边界

上述成绩均来自作者 PDF 与对应基准，不是独立复现、同行评审结论或真实部署保证。对 A/S 机构的选择也不替代方法学审查；每篇笔记分别给出证据可信度（1–5 分）、优点和局限。后续可追踪代码/数据公开与第三方复现，但今日不把尚未出现的验证写成已完成。
