# 2026-10-02 arXiv LLM Memory 日报 — 已完成

- 检查时间：2026-10-02 08:11（北京时间）。
- 官方 [cs.CL/new](https://arxiv.org/list/cs.CL/new)、[cs.AI/new](https://arxiv.org/list/cs.AI/new)、[cs.LG/new](https://arxiv.org/list/cs.LG/new) 仍显示 **Thursday, 1 October 2026**，尚未显示 10 月 2 日正式公告批次。
- 08:11 时状态为 **pending**，当时不选论文、不把提交日期或旧批次当作今日公告；以下保留核验历史。11:01（北京时间）再次检查时，三个列表均已显示 **Friday, 2 October 2026**，随后仅从当日 New submissions 筛选。

## 增量核验

- 2026-10-02 09:01（北京时间）：再次读取上述三个官方 new 列表，均仍显示 10 月 1 日；状态不变，继续等待今日正式批次。
- 2026-10-02 10:00（北京时间）：cs.CL、cs.AI、cs.LG 官方 new 列表仍均显示 10 月 1 日；今日批次仍 pending。
- 2026-10-02 11:01（北京时间）：三个官方列表均更新为 10 月 2 日；开始核验当日新稿。

## 筛选与证据口径

- 本日报**只覆盖 2026-10-02 正式公告批次的 New submissions**，不是按 v1 提交日期筛选。官方列表：[cs.CL/new](https://arxiv.org/list/cs.CL/new)、[cs.AI/new](https://arxiv.org/list/cs.AI/new)、[cs.LG/new](https://arxiv.org/list/cs.LG/new)。cross-list、replacement 与昨天公告的新稿不计。v1 在 9 月 30 日或 10 月 1 日提交的文章，只因 10 月 2 日出现在正式 New submissions 才被收录。
- 已选 **20 篇**，每篇官方 PDF 已下载到本目录并通过 PDF 可读取性检查；机构以 PDF 首页署名为准，不把 Microsoft AI 写成 Microsoft Research，也不凭作者名字推测机构。
- 排序为**机构优先级 → 直接相关性 → 方法新颖性**。S 为头部企业研究团队及其合作，A+ 为一流高校/实验室，B 为方法格外值得看的黑马；这些等级只是今日阅读优先级，**与各篇 1–5 分论文可信度独立**。第 18 篇强校但弱相关，因多模态个人历史启发而保留；第 19、20 篇为机构优先级较低的黑马。

## 入选论文

| # | 论文 / 笔记 | PDF 首页机构；优先级 | 与研究兴趣的关联及入选原因 | v1 提交 |
|---:|---|---|---|---|
| 1 | [SkillSpec：技能演化与表示专化](./01-skillspec.md) · [arXiv](https://arxiv.org/abs/2610.00704) | Microsoft AI；S | 直接相关：执行证据门控技能写入，并选择图/平面表示 | 09-30 |
| 2 | [ActiveSaddler：代理 harness 课程演化](./02-activesaddler.md) · [arXiv](https://arxiv.org/abs/2610.00906) | Microsoft、POSTECH、KAIST；S | 直接相关：失败模式记忆驱动下一轮优化任务 | 10-01 |
| 3 | [PoS：显式信念状态](./03-pos.md) · [arXiv](https://arxiv.org/abs/2610.01415) | Alibaba、南开、清华；S | 直接相关：长期 agent 的当前状态与未决目标维护 | 10-01 |
| 4 | [FAULT：自诊断信用分配](./04-fault.md) · [arXiv](https://arxiv.org/abs/2610.01161) | Alibaba、京都大学及合作高校；S | 直接相关：可校验失败经验转为逐步训练信号 | 10-01 |
| 5 | [Clock Diffusion](./05-clockdiffusion.md) · [arXiv](https://arxiv.org/abs/2610.00894) | NVIDIA、Cornell；S | 直接相关：连续扩散 LM 支持变长与 KV cache | 10-01 |
| 6 | [Hierarchical Continuous DLM](./06-hcdlm.md) · [arXiv](https://arxiv.org/abs/2610.02193) | UIUC、Amazon；S | 直接相关：潜态与 token 相互反馈以保留联合依赖 | 10-01 |
| 7 | [CommunityKV](./07-communitykv.md) · [arXiv](https://arxiv.org/abs/2610.00418) | Amazon AGI；S | 相关：图社区检索 KV，启发高频记忆读取 | 09-30 |
| 8 | [Retention vs Retrieval](./08-retention-retrieval.md) · [arXiv](https://arxiv.org/abs/2610.00366) | Stanford；A+ | 直接相关：拆开记忆保留与查询检索的评估混杂 | 09-30 |
| 9 | [AutoCompact](./09-autocompact.md) · [arXiv](https://arxiv.org/abs/2610.02163) | Harvard、NTU、SMU；A+ | 直接相关：学习何时压缩 agent 上下文 | 10-01 |
| 10 | [Madeleine](./10-madeleine.md) · [arXiv](https://arxiv.org/abs/2610.01118) | NTU；A+ | 直接相关：模拟人生训练非相似线索的个人记忆联想 | 10-01 |
| 11 | [RuleEvolve](./11-ruleevolve.md) · [arXiv](https://arxiv.org/abs/2610.00650) | Duke；A+ | 直接相关：编码 agent 的程序性规则自演化 | 09-30 |
| 12 | [Mem++](./12-memplusplus.md) · [arXiv](https://arxiv.org/abs/2610.02002) | UT Austin、AIDAChip；A+ | 直接相关：组织记忆不破坏原文、按时间读版本 | 10-01 |
| 13 | [Task Operators for ICL](./13-task-operators.md) · [arXiv](https://arxiv.org/abs/2610.01054) | University of Virginia；A+ | 直接相关：上下文示例的任务知识压缩为算子 | 10-01 |
| 14 | [Correct-Token Retention](./14-correct-token.md) · [arXiv](https://arxiv.org/abs/2610.01275) | EPFL、Idiap；A+ | 直接相关：扩散 LM 自修正也要保住正确 token | 10-01 |
| 15 | [GUI-HARVEST](./15-gui-harvest.md) · [arXiv](https://arxiv.org/abs/2610.00948) | CUHK-Shenzhen 等高校；A+ | 直接相关：多次执行证据汇成可验证的 harness 更新 | 10-01 |
| 16 | [StepRS-GRPO](./16-steprs-grpo.md) · [arXiv](https://arxiv.org/abs/2610.00661) | Indiana U、UC Riverside；A+ | 直接相关：扩散 LM 按去噪阶段调整 RL 探索 | 09-30 |
| 17 | [Denoising Surface](./17-denoising-surface.md) · [arXiv](https://arxiv.org/abs/2610.00499) | 武汉大学、上海交大、HKUST 等；A+ | 相关：扩散 LM 推理/服务成本模型 | 09-30 |
| 18 | [NextMe-800](./18-nextme.md) · [arXiv](https://arxiv.org/abs/2610.01461) | HKU、同济；A+ | **弱相关但具启发性**：多月个人生活史的多尺度表征 | 10-01 |
| 19 | [REPAIR：用户偏好状态修补](./19-repair.md) · [arXiv](https://arxiv.org/abs/2610.01270) | Dhirubhai Ambani U、IIT Delhi；B 黑马 | 直接相关：从冻结编码器缓存恢复丢失的偏好证据；PDF 注明 NeurIPS 2026 已接收 | 10-01 |
| 20 | [Causal Memory Policy](./20-causal-memory-policy.md) · [arXiv](https://arxiv.org/abs/2610.02070) | Illinois Institute of Technology；B 黑马 | 直接相关：干预检索才可识别未被访问记忆的效用 | 10-01 |

## 机构分布与主题趋势

- 按入选论文的**最高阅读优先级**互斥统计：S 7 篇，A+ 11 篇，B 黑马 2 篇；机构可联合署名，不能把此统计当成各机构独占贡献。头部企业覆盖 Microsoft 2、Alibaba 2、NVIDIA 1、Amazon 2；一流高校/实验室涵盖 Stanford、Harvard、NTU、Duke、Cornell、UIUC、EPFL、HKU 等。黑马被收录是因为方法洞见和实验而非机构名气。
- **记忆的写入和读取开始被分别优化。** SkillSpec 管写入门与表示，Stanford 的评估指出保留/检索混杂，Madeleine 改写查询侧联想，CMP 则要求在检索层做因果干预。
- **agent memory 从历史文本走向状态/失败机制。** PoS 显式维护信念，ActiveSaddler 存失败模式，FAULT 把自诊断转成训练归因，AutoCompact 学习压缩时机。
- **diffusion LLM 正在补齐系统环节。** ClockDLM 处理变长/KV，HC-DLM 处理并行 token 依赖，CTR-Reg 处理“保对”，StepRS-GRPO 改进阶段性探索，Denoising Surface 处理服务成本。

## 今天最值得深读的 3 篇

1. **[SkillSpec](./01-skillspec.md)**：与自演化 agent memory 最直接，尤其值得拆解其“执行证据认可更新”和“选择知识结构”两个独立决策。复现重点：相同搜索预算与长尾技能损失。
2. **[Retention vs Retrieval](./08-retention-retrieval.md)**：不是更复杂的记忆方法，却可能改变今后所有 memory benchmark 的公平性。复现重点：将 300 回合正交设计扩展到真实多会话记录。
3. **[Madeleine](./10-madeleine.md)**：个人记忆联想的明确路径，线上零 LLM 调用有部署吸引力。复现重点：模拟人生先验是否对跨文化及罕见个人事件有效。

## 解读边界

每篇笔记的可信度分数只反映论文方法、实验和局限的证据强度，不因机构强就自动提高。所有性能数字均为作者报告，未做独立复现；“未来影响”与 critical thinking 中的外推是本日报推断。NextMe-800 不是 LLM memory 论文，只作为强机构、跨模态个人历史启发；两篇 B 级黑马不能挤占头部机构直接相关工作的优先位置。
