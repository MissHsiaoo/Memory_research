# 2026-09-30 arXiv LLM Memory 日报

## 批次核验与交付状态

- arXiv 官方 `cs.CL/new`、`cs.AI/new`、`cs.LG/new` 均显示 **Wednesday, 30 September 2026**；逐篇 ID 已核对在其主分类当天的 **New submissions** 区，而非 Cross submissions 或 Replacements。本报告按该正式公告批次归档，对应北京时间 2026-09-30。
- “提交日期”与“公告批次”分开记录。较早提交的 v1 在本批次首次正式出现；没有把旧批次论文的版本更新充作新论文。
- 入选 **20 篇**，官方 PDF **20/20 已下载并通过可读性解析**；机构均以 PDF 首页核验。排序按 **机构优先级 → 主题直接相关性 → 方法新颖性与证据强度**。

官方列表：[cs.CL](https://arxiv.org/list/cs.CL/new) · [cs.AI](https://arxiv.org/list/cs.AI/new) · [cs.LG](https://arxiv.org/list/cs.LG/new)

## 入选论文与选择理由

| 排名 | 论文 | 机构优先级 | 相关性 | 选择理由 |
|---:|---|:---:|:---:|---|
| 1 | [Context Language Models](./01-context-language-models.md) | S | 直接 | Meta/UW/MIT；把上下文管理变成模型可学习的动作，覆盖在线 RL、技能演化、多 agent 和服务系统。 |
| 2 | [RLTL;DR](./02-rltldr.md) | S | 直接 | Apple；用极短 insight 内化失败经验，突破没有成功 rollout 的 RL 冷启动。 |
| 3 | [FOCUS](./03-focus.md) | S | 直接 | Microsoft；按历史片段是否影响未来决策来压缩 context，五类 agent 基准同时改善成本与成功率。 |
| 4 | [PUMBA](./04-pumba.md) | S | 直接，diffusion | Apple；统一轨迹对齐、跨步连续状态与 BPTT，直接研究 diffusion LM 的训练与推理错配。 |
| 5 | [REVOIR](./05-revoir.md) | A+ | 直接，个性化 | Oxford/NUS/A*STAR；用提问的任务价值决定何时澄清用户偏好。 |
| 6 | [CoEM](./06-coem.md) | A+ | 直接 | MIT/KAIST；提出先保留原文、后提交压缩事实的记忆机制，长上下文收益明显。 |
| 7 | [MemFold](./07-memfold.md) | A+ | 直接 | UCSB/UNC/Harvard/UW–Madison；固定 K 个 soft-memory vector，直接按个性化行为优化。 |
| 8 | [MGPO](./08-mgpo.md) | A+ | 直接 | Michigan；以反事实边际效用给每次 memory rewrite 做长期信用分配。 |
| 9 | [MERA](./09-mera.md) | A+ | 直接 | Tsinghua/JD；让已验证证据指导下一轮检索，小 planner 的针对性训练有说服力。 |
| 10 | [STEPQuant](./10-stepquant.md) | A+ | 邻近但关键 | Zhejiang/Tsinghua/CAS/Harvard/CUHK；解决 latent recurrent memory 的并发服务内存瓶颈。 |
| 11 | [FastGuide](./11-fastguide.md) | A+ | 直接，diffusion | UPenn；用 guidance 缓存和稀疏重算加速 diffusion LM 的推理时奖励控制。 |
| 12 | [LUDI](./12-ludi.md) | A+ | 直接，diffusion | HKUST/Huawei；提出 uniform diffusion LM 的新训练目标并扩展到 7B。 |
| 13 | [SelfSearch](./13-selfsearch.md) | A | 直接 | SNU；将 agent 自我修改过程记录成元经验，用于下一轮演化。 |
| 14 | [Harness Evolution as Learning](./14-harness-evolution.md) | A | 直接 | RUC；用三类学习误差解释个人 agent 的自演化瓶颈。 |
| 15 | [DeLLM](./15-dellm.md) | A | 直接 | Melbourne；提出沿 provenance 删除记忆派生影响，补足个性化记忆的撤回语义。 |
| 16 | [MATE](./16-mate.md) | A | 直接 | PKU/USTC/ECNU；证明过去成功且相关的轨迹也会负迁移，并定位动作规范化为主机制。 |
| 17 | [RPD](./17-rpd.md) | A | 直接，diffusion | UVA；用跨层稳定性和上游熵预算改善并行提交可靠性。 |
| 18 | [REST](./18-rest.md) | A | 直接，latent | UBC；把 latent thought 的因果性、最小性、可分性和稳定性转成训练目标。 |
| 19 | [ICL Amplifies a Latent Symbolic Circuit](./19-icl-symbolic-circuit.md) | B，黑马 | 直接，ICL | 独立研究者；跨三模型的 activation patching 为 ICL 潜在电路提供因果证据，但任务较窄。 |
| 20 | [Temporal Flattening](./20-temporal-flattening.md) | B，黑马 | 直接，个性化 | Southern Mississippi；发现多种 memory 系统会丢失用户事实的时间形态，产品风险洞见突出。 |

**官方论文链接，顺序与排名一致：**

- 1–5：[2609.37725](https://arxiv.org/abs/2609.37725) · [2609.37633](https://arxiv.org/abs/2609.37633) · [2609.37590](https://arxiv.org/abs/2609.37590) · [2609.37974](https://arxiv.org/abs/2609.37974) · [2609.37588](https://arxiv.org/abs/2609.37588)
- 6–10：[2609.36935](https://arxiv.org/abs/2609.36935) · [2609.36435](https://arxiv.org/abs/2609.36435) · [2609.37930](https://arxiv.org/abs/2609.37930) · [2609.37443](https://arxiv.org/abs/2609.37443) · [2609.38169](https://arxiv.org/abs/2609.38169)
- 11–15：[2609.36202](https://arxiv.org/abs/2609.36202) · [2609.35817](https://arxiv.org/abs/2609.35817) · [2609.37968](https://arxiv.org/abs/2609.37968) · [2609.36892](https://arxiv.org/abs/2609.36892) · [2609.36414](https://arxiv.org/abs/2609.36414)
- 16–20：[2609.35808](https://arxiv.org/abs/2609.35808) · [2609.36452](https://arxiv.org/abs/2609.36452) · [2609.36159](https://arxiv.org/abs/2609.36159) · [2609.36265](https://arxiv.org/abs/2609.36265) · [2609.36457](https://arxiv.org/abs/2609.36457)

## 机构分布

- **S：4 篇**：Meta Superintelligence Labs、Apple（2）、Microsoft M365 Research；部分论文与 UW、MIT、EPFL 等合作。
- **A+：8 篇**：Oxford、NUS、A*STAR、MIT、KAIST、Harvard、Michigan、Tsinghua、CAS、UPenn、HKUST、Huawei 等。
- **A：6 篇**：SNU、RUC、Melbourne、PKU/USTC/ECNU、UVA、UBC。
- **B 黑马：2 篇**：Independent Researcher、University of Southern Mississippi。机构优先级较低，因机制证据或个性化记忆风险洞见突出而收录。

## 今日主题趋势

1. **Memory 从存储走向决策。** CLM、FOCUS、CoEM、MemFold、MGPO 分别优化上下文修改、历史保留、延迟提交、soft compression 和记忆更新的边际价值。
2. **自演化开始压缩经验。** RLTL;DR 把失败轨迹压成可内化 insight；SelfSearch 保存修改 agent 的过程；Harness Evolution 解释更新为何可能产生偏差。
3. **个性化需要处理行动与撤回。** REVOIR 研究何时追问，DeLLM 研究如何删除，Temporal Flattening 揭示摘要如何抹去有效期。
4. **Diffusion LLM 形成训练与推理协同栈。** PUMBA、LUDI、FastGuide、RPD 分别覆盖训练轨迹、目标函数、奖励引导和并行解码。
5. **Latent memory 进入部署与解释阶段。** STEPQuant 解决 recurrent state 的并发内存，REST 与 ICL circuit 研究隐藏表示如何被约束和激活。

## 最值得深读的 3 篇

1. **Context Language Models**：把上下文管理提升为模型能力，兼有在线学习、多 agent 与服务端实现；最可能改变 agent 架构。
2. **RLTL;DR**：仅用几千条 task-insight 近似完整轨迹训练的结果若可独立复现，会改变 self-improvement 的数据单位。
3. **MemFold**：最直接连接你的 latent memory 与 personalization 兴趣，并区分保存用户信息与让输出真正遵从偏好。

偏重 diffusion LLM 时可优先读 PUMBA；偏重长期文本记忆训练时可优先读 MGPO。

## 核验与边界

- 20 份本地 PDF 均来自对应论文的 arXiv 官方 PDF 链接，文件名为 arXiv ID；逐篇笔记包含官方页面、官方 PDF 和本地 PDF 链接。
- 笔记区分论文直接证据与研究推断。机构优先级和可信度评分独立；低分项目主要受任务范围、外部效度及复现状态限制。
- 本日 08:13 时列表尚未切换，曾记录为 pending；约 11:12 核验到 2026-09-30 正式批次，随后完成筛选与全文评析。
