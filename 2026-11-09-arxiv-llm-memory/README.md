# 2026-11-09 arXiv LLM Memory 日报

本日入选20篇，配套20份中文评析和20份官方PDF。机构优先级与证据可信度独立评估；无仅凭摘要给高分的论文。

## 批次与北京时间对应

本轮触发于北京时间2026-11-09 08:27（UTC 00:27，美国东部标准时间11月8日19:27）。最终完整抓取的cs、cs.CL、cs.AI、cs.LG、stat.ML五个官方列表均显示 **Monday, 9 November 2026**。本日报按该正式列表批次归档至北京时间11月9日，不用论文提交日期冒充公告日期，也不声称知道每篇实际发布的精确时刻。初始网页读取曾出现cs.LG旧缓存，最终以五类一致的完整列表快照核验；未把旧列表论文纳入本日。

核验入口：[cs](https://arxiv.org/list/cs/new)、[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)、[stat.ML](https://arxiv.org/list/stat.ML/new)。动态页面之后会变化，evidence/保存此次完整HTML及去重清单。仅提取New submissions，排除Cross submissions和Replacement submissions；五类去重共692篇，cs本身683篇，stat.ML另9篇。入选20篇均在该集合，具体首次提交日期及版本记录见笔记与verification.json。

对列表题目/摘要按记忆、上下文、个性化、扩散语言模型、持续学习和agent经验初筛，下载30篇候选PDF，核查首页署名与相关正文，选满20篇。未扩展旧日期。此流程不是对692篇每篇全文逐一深读或逐一完成机构调查，不能据此声称穷尽所有潜在强机构论文。

## 排序口径

按机构优先级→相关性→新颖性/证据排序。A1先列Microsoft、NVIDIA合作；AWS为优先产业补充，但QGPM首页明确相关作者工作与Amazon职位无关。A2列优先研究型高校/实验室合作；A3列UIC、西工大等专项强相关高校工作，未将所有高校笼统标成全球顶尖。该工作分层不是大学排名。最后两篇为低机构优先级黑马：WrongUserControl的反事实控制及LoRAtoLanguage的参数记忆可读化具有突出启发。强机构弱相关的MORTIS、ParallelAgentTeams已明确标示，优先于黑马纳入。每位作者所属以PDF为准，不把同文合作机构强行套给全部作者。

## 入选论文

| 排名 | 论文与链接 | 核验机构 | 优先级 | 相关性 | 证据分 |
|---|---|---|---|---|---|
| 1 | [MemoryDojo](01-MemoryDojo.md) · [arXiv](https://arxiv.org/abs/2611.09721) | Microsoft；Rensselaer Polytechnic Institute | A1 | 直接 | 4/5 |
| 2 | [BOXBOX](02-BOXBOX.md) · [arXiv](https://arxiv.org/abs/2611.09218) | Microsoft；南京大学；浙江大学；Birkbeck, University of London | A1 | 直接 | 4/5 |
| 3 | [CPU-ARC](03-CPU-ARC.md) · [arXiv](https://arxiv.org/abs/2611.09891) | NVIDIA（PDF首页品牌与版权声明；未据此推断每位作者具体职位） | A1 | 直接 | 3/5 |
| 4 | [Flex-RSI](04-Flex-RSI.md) · [arXiv](https://arxiv.org/abs/2611.08946) | Texas A&M；Cambridge；NUS；NVIDIA；MIT；MIT-IBM Watson AI Lab；UT Austin；CMU；UPenn；USC；Purdue；Adobe；Toronto（首页团队署名） | A1 | 直接 | 3/5 |
| 5 | [QGPM](05-QGPM.md) · [arXiv](https://arxiv.org/abs/2611.09554) | University of Southern California；Amazon Web Services（首页脚注注明相关作者工作与其Amazon职位无关） | A1补充 | 直接 | 4/5 |
| 6 | [ENGRAM](06-ENGRAM.md) · [arXiv](https://arxiv.org/abs/2611.09472) | University of New South Wales；HKUST (Guangzhou) | A2 | 直接 | 4/5 |
| 7 | [Transformer-FSQ](07-Transformer-FSQ.md) · [arXiv](https://arxiv.org/abs/2611.09598) | University of Edinburgh | A2 | 直接 | 4/5 |
| 8 | [DUET](08-DUET.md) · [arXiv](https://arxiv.org/abs/2611.09239) | 南京大学，State Key Laboratory for Novel Software Technology | A2 | 直接 | 4/5 |
| 9 | [WAAC](09-WAAC.md) · [arXiv](https://arxiv.org/abs/2611.08865) | 南京大学；东北大学（中国） | A2 | 直接 | 3/5 |
| 10 | [CARE](10-CARE.md) · [arXiv](https://arxiv.org/abs/2611.08721) | Georgia Institute of Technology；University of Virginia；Beth Israel Deaconess Medical Center | A2 | 直接 | 3/5 |
| 11 | [TimeOmni-Live](11-TimeOmni-Live.md) · [arXiv](https://arxiv.org/abs/2611.09502) | Griffith University；浙江大学；CSIRO；Zhejiang Lab；Langotime | A2 | 直接 | 3/5 |
| 12 | [HiMEM](12-HiMEM.md) · [arXiv](https://arxiv.org/abs/2611.09355) | 西安交通大学（首页软件学院、人工智能学院及相关国家重点实验室署名） | A2 | 直接 | 4/5 |
| 13 | [NormGym](13-NormGym.md) · [arXiv](https://arxiv.org/abs/2611.08613) | Johns Hopkins University；Vector Institute for Artificial Intelligence | A2 | 直接 | 4/5 |
| 14 | [ExplanationOrder](14-ExplanationOrder.md) · [arXiv](https://arxiv.org/abs/2611.08785) | Paris-Dauphine University, PSL Research University；UMR CNRS 7243, LAMSADE | A2 | 直接 | 4/5 |
| 15 | [MORTIS](15-MORTIS.md) · [arXiv](https://arxiv.org/abs/2611.08638) | 上海交通大学；University of Michigan, Ann Arbor | A2 | 启发性 | 4/5 |
| 16 | [ParallelAgentTeams](16-ParallelAgentTeams.md) · [arXiv](https://arxiv.org/abs/2611.09798) | Princeton University；Duke University；New York University；Modal Labs | A2 | 启发性 | 3/5 |
| 17 | [PRISM](17-PRISM.md) · [arXiv](https://arxiv.org/abs/2611.08917) | University of Illinois Chicago | A3 | 直接 | 4/5 |
| 18 | [ROSE](18-ROSE.md) · [arXiv](https://arxiv.org/abs/2611.09770) | 西北工业大学及深圳研究院、相关工信部重点实验室；Independent Researcher | A3 | 直接 | 3/5 |
| 19 | [WrongUserControl](19-WrongUserControl.md) · [arXiv](https://arxiv.org/abs/2611.09609) | Yandex；Accenture；RawModels；Independent Researcher；Institute for Information Transmission Problems；TBC Uzbekistan；Keenable AI | B | 直接 | 4/5 |
| 20 | [LoRAtoLanguage](20-LoRAtoLanguage.md) · [arXiv](https://arxiv.org/abs/2611.09454) | QpiAI, Bengaluru, India | B | 直接 | 3/5 |

## 机构分布

按论文合作署名出现次数统计（可重复）：Microsoft 2，NVIDIA 2，AWS 1（带独立工作声明）；南京大学3，浙江大学2，USC 2；其余覆盖UNSW/HKUST广州、Edinburgh、Georgia Tech/UVA/BIDMC、西安交大、JHU/Vector、PSL/CNRS、上海交大/Michigan、Princeton/Duke/NYU、UIC、西工大、CSIRO等。完整团队名单见各篇首页及verification.json。A1及补充5篇，A2 11篇，A3 2篇，低机构优先级黑马2篇。机构分布仅代表入选集合，不代表当日所有论文。

## 主题趋势

1. **记忆的价值与风险要追踪到行动。** MemoryDojo拆开污染写入、传播和行为；CARE拆开时机、内容与遗漏；WrongUserControl提醒主题匹配不能直接当个体化证据。
2. **巩固不是立即删除。** ENGRAM将训练准入与验证归档拆开；HiMEM用有条件规则整合情节；两者都依赖验证覆盖，未来任务改变时仍可能需要原始证据。
3. **参数与文本技能出现双向转换。** ENGRAM写入权重，LoRAtoLanguage尝试写回文档，PRISM将参数技能单元化；行为保持、内容可恢复和跨模型可迁移是不同指标。
4. **长上下文的容量、准确率和延迟存在明显权衡。** FSQ极端压缩有损；QGPM需要额外prefill；DUET每步与端到端速度不同；MORTIS优化计算复用，不代表语义记忆更准。
5. **自演化要有独立评估边界。** BOXBOX的shadow verifier与回滚、Flex-RSI的隐藏测试有帮助，但同任务反馈改善不自动等于长期可迁移的元学习。

## 最值得深读的3篇

- **ENGRAM（06）**：最直接连接外部记忆与参数巩固，验证后归档和随机/立即释放对照适合研究“何时可以忘记”；要注意可检索集合变小不等于总存储变小。
- **MemoryDojo（01）**：把记忆生命周期与跨会话行为联系起来，适合给任何新memory系统增加效用与安全双轴评测。
- **Transformer-FSQ（07）**：latent memory方向最直接，实际字节与内核评测有参考价值；高压缩下明显精度损失使其更适合研究容量—保真权衡，而非追逐单一倍率。

针对“多目标记忆使用benchmark”：本日优先看NormGym（13，任务完成+规范遵守）、LiveTS-Suite/TimeOmni-Live（11，跨窗状态/触发时机/内容/效率）、CARE（10，时机/质量/遗漏）与MemoryDojo（01，效用/安全）。这些基准的目标、环境和指标不同，不能合并成一个排行榜，也不声称已经覆盖通用多目标个人记忆。

## 候选取舍与阅读边界

额外下载的10篇包括DecisionContext、JCMC、FinEvolveKG、DECAF、Memory as a Temporal Resource、TT-MBRL、How Much History、Compaction Decay、Feedback Backdoor与SPARSEUP。没有为凑数纳入理论/设想证据偏弱、机构优先级较低或在20篇名额下启发重合的工作。未入选不表示论文无价值，候选也未全部进行同等深度全文审查。

完整PDF获取与可解析不等于每页逐行读完。逐篇列出重点阅读物理页码，未运行作者代码，未独立复现实验，也未逐条检查所有证明或附录。3/5和4/5只反映本轮所见证据；高机构优先级不自动高分。所有推断、可能失败情形及复现实验建议与论文结果分开写。

## 文件交付核验

- pdf/内20份官方PDF，文件头、页结构可解析，首页均已渲染检查；SHA-256和页数见verification.json。
- evidence/内5份官方列表、692篇去重清单与20篇官方摘要页；用于复核新论文资格、作者及提交日期。
- 每篇笔记使用仓库内相对PDF链接，保留官方PDF备用链接；所有本地目标在交付包中实际存在。
- 本轮同时恢复11月8日暂存的无公告记录同步，保持该历史记录原文不改；其中“同步未完成”描述的是11月8日当时状态，恢复动作以本轮提交及远端核验为准。
- 不预先声明push成功；远端是否一致在执行同步后核验。
