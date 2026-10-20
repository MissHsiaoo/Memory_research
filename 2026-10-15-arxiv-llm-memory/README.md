# 2026-10-15 arXiv LLM Memory 日报

- **状态：已交付。**北京时间 2026-10-15 11:03 后核验，[arXiv 官方计算机科学总览](https://arxiv.org/list/cs/new)标为 “Showing new listings for Thursday, 15 October 2026”，含 **New submissions 882**；[stat.ML 官方列表](https://arxiv.org/list/stat.ML/new)同日另有 **New submissions 27**。这 909 个不重复编号构成今日候选池，本报告只取其中首次公告的新稿，不取任何 *Replacement submissions*。本次官方公告日期 **2026-10-15** 与北京时间查阅日期 **2026-10-15** 对应；单篇初次提交日期可为 10 月 13/14 日，绝不将其误写为公告日期。未扩展至近 30 天，也未修改过去日期的文件夹。
- 共筛选 909 个官方新稿条目，深入核验 36 份候选官方 PDF 首页，最终收录 **22 篇**（20 篇目标略超，因当日重点机构与直接相关论文较多，另保留一篇评估方法论突出的黑马）。22 份本地 PDF 均可解析、至少 13 页且最小 453,701 字节；每篇笔记区分论文证据与推断。
- 分类页[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)在核验时虽然标 10 月 15 日，却分别只列 56、88、88 个替换版本，缺少同日新稿区段；因此使用官方总览的 *New submissions* 而不把这些替换稿计入。此页面差异见下方增量记录。

## 排序与机构分布

排序按 **机构优先级 → 直接相关性 → 方法新颖性**；同层再参考实验严谨性和启发。P1 为用户点名的重点机构参与，P2 为高水平高校/其他强产业实验室，P3 为机构优先级较低但证据/方法特别有价值的启发性补充。P1 **5 篇**（ByteDance Seed 1、Meta 3、NVIDIA 1；有交叉高校），P2 **16 篇**（MIT/Cornell、浙江大学/蚂蚁/小红书、UT Austin/Rutgers、Northwestern/McGill/Mila、华为等；机构按 PDF 首页，合作单位可重叠），P3 **1 篇**（Jeju National University/Soongsil University）。机构等级与笔记中的证据可信度分别评估。

| 排名 | 论文与逐篇中文评析 | 机构优先级 | 相关性 / 选择理由 |
| --- | --- | --- | --- |
| 1 | [Cortex](01-Cortex.md) · [arXiv](https://arxiv.org/abs/2610.20399) | P1 · ByteDance Seed | 直接：上下文收益固化为参数记忆 |
| 2 | [TreeFlex](02-TreeFlex.md) · [arXiv](https://arxiv.org/abs/2610.20334) | P1 · Meta AI | 直接：可回溯树形轨迹记忆 |
| 3 | [One Block Ahead](03-One-Block-Ahead.md) · [arXiv](https://arxiv.org/abs/2610.19510) | P1 · NVIDIA | 直接：扩散 LLM；采样状态可视作跨块记忆 |
| 4 | [New Model, Old Habits](04-Old-Habits.md) · [arXiv](https://arxiv.org/abs/2610.19712) | P1 · Meta | 直接：跨会话历史的行为迁移 |
| 5 | [COPE](05-COPE.md) · [arXiv](https://arxiv.org/abs/2610.20597) | P1 · Meta AI | **弱相关但具启发性**：成功轨迹经验转为训练信号 |
| 6 | [PraxisMemBench](06-PraxisMem.md) · [arXiv](https://arxiv.org/abs/2610.20022) | P2 · 浙江大学/蚂蚁 | 直接：个人与流程记忆耦合 |
| 7 | [Titan-Llama](07-Titan-Llama.md) · [arXiv](https://arxiv.org/abs/2610.19210) | P2 · MIT/Cornell | 直接：预训练模型外接神经记忆 |
| 8 | [Beyond Retrieval](08-Beyond-Retrieval.md) · [arXiv](https://arxiv.org/abs/2610.19474) | P2 · 华为 | 直接：源证据与事件聚合 |
| 9 | [ActICL](09-ActICL.md) · [arXiv](https://arxiv.org/abs/2610.19475) | P2 · UT Austin/Rutgers | 直接：主动多模态 ICL 检索 |
| 10 | [EGCForest](10-EGCForest.md) · [arXiv](https://arxiv.org/abs/2610.19836) | P2 · 浙江大学/小红书 | 直接：企业群聊多视图记忆 |
| 11 | [MemDuet](11-MemDuet.md) · [arXiv](https://arxiv.org/abs/2610.19928) | P2 · 西安交大/帝国理工 | 直接：选择与验证分层记忆 |
| 12 | [XferAgent](12-XferAgent.md) · [arXiv](https://arxiv.org/abs/2610.19581) | P2 · Northwestern/McGill/Mila | 直接：跨代理经验图 |
| 13 | [From Copying to Composition](13-ICL-Composition.md) · [arXiv](https://arxiv.org/abs/2610.19113) | P2 · Scale AI/Arizona | 直接：ICL 的组合机制诊断 |
| 14 | [RSE-Bench](14-RSE-Bench.md) · [arXiv](https://arxiv.org/abs/2610.19910) | P2 · 京东研究/CASIA/清华 | 直接：技能自进化的噪声鲁棒性 |
| 15 | [MemCode](15-MemCode.md) · [arXiv](https://arxiv.org/abs/2610.19472) | P2 · 同济大学 | 直接：离散语义记忆检索 |
| 16 | [FOLD](16-FOLD.md) · [arXiv](https://arxiv.org/abs/2610.20392) | P2 · Canva/北大/中山 | 直接：长上下文推测解码的 far memory（非跨会话） |
| 17 | [SkillGrain](17-SkillGrain.md) · [arXiv](https://arxiv.org/abs/2610.19380) | P2 · 北航/NTU | 直接：用户反馈的选择性保留 |
| 18 | [STRATA](18-STRATA.md) · [arXiv](https://arxiv.org/abs/2610.19386) | P2 · NJIT/CUHK-SZ | 直接：自维护经验图和反例边 |
| 19 | [ForkGRPO](19-ForkGRPO.md) · [arXiv](https://arxiv.org/abs/2610.19408) | P2 · USC/Case Western | **弱相关但具启发性**：扩散 LLM 分叉式训练 |
| 20 | [SwarmRSI](20-SwarmRSI.md) · [arXiv](https://arxiv.org/abs/2610.20431) | P2 · 华为/Leiden/Groningen | **弱相关但具启发性**：科学代理的假设/程序继承 |
| 21 | [L3M](21-L3M.md) · [arXiv](https://arxiv.org/abs/2610.19591) | P2 · Amazon | **弱相关但具启发性**：持久状态及可验证授权 |
| 22 | [Evaluating Compressed Memory](22-Compressed-Memory-Eval.md) · [arXiv](https://arxiv.org/abs/2610.19373) | **P3 黑马** · Jeju/Soongsil | 直接：记忆依赖、效用与内容贡献的因果区分 |

## 主题趋势与优先深读

- **记忆从检索转向结构/计算**：Cortex 的参数固化、Titan-Llama 的神经压缩、MemCode 的离散码、EGCForest 的多视图、Beyond Retrieval 的事件聚合，分别改写“记什么、如何访问、如何验证”。
- **自进化从积累转向治理**：STRATA 的遗忘/反例边、RSE-Bench 的带噪写入、SkillGrain 的选择性保留，与 DASH 的行为污染观察一起提示：更多记忆并非总更好。
- **长上下文和扩散 LLM 重视隐式状态**：OBA 的 sampler state、FOLD 的远端记忆都提示不能把“上下文”简单等同于文本 token；但它们与长期个性化记忆是不同问题。

最值得深读的三篇：**Cortex**（直接触及 latent/parametric memory，跨尺度并同时衡量保留与干扰）；**PraxisMemBench**（把个人事实与用户条件下的流程耦合，契合个性化助理的实际失败模式）；**Beyond Retrieval**（用源证据和可执行事件聚合纠正“检索即记忆”的假设，含较清晰的受控实验）。

## 增量核验

- 2026-10-15 07:57（北京时间）：三类官方 `new` 列表均为 10 月 14 日批次，10 月 15 日待公告。
- 2026-10-15 08:00（北京时间）：再次读取 cs.CL、cs.AI、cs.LG 官方 `new` 页面，三者仍均显示 Wednesday, 14 October 2026；今天正式批次仍待公告，未筛旧批次。
- 2026-10-15 09:03（北京时间）：三类官方 `new` 页面仍均为 10 月 14 日正式批次；10 月 15 日继续 pending。
- 2026-10-15 10:04（北京时间）：cs.CL、cs.AI、cs.LG 官方 `new` 列表仍均显示 10 月 14 日；未将旧批次纳入今天。
- 2026-10-15 11:03（北京时间）：三类官方 `new` 页面日期变为 10 月 15 日，但只有替换版本（cs.CL 56、cs.AI 88、cs.LG 88），未出现 `New submissions`；今日新论文数暂记 0、状态仍 pending，不把 v2/v3 记作新论文。
- 2026-10-15 11:06（北京时间）：官方 `cs/new` 总览含当日 882 条 `New submissions`；更正上条的暂记 0，开始筛选该正式批次，仍排除分类页替换版本。
- 2026-10-15 11:10（北京时间）：补充核验 [stat.ML 官方 new 列表](https://arxiv.org/list/stat.ML/new) 同日有 27 条 `New submissions`；与 `cs/new` 总览合计 909 个不重复编号。后续只从这 909 篇正式新提交中选与研究主题相关的论文。
- 2026-10-15 11:16（北京时间）：22 篇评析及对应 PDF 完成交付；逐一核对 22 个编号都在官方当日 `New submissions` 清单，PDF 均可读取，22 篇笔记均有六项分析且 README 内链全部有效。临时每小时续跑已移除，自动化恢复北京时间每日 08:00。
