# 2026-09-29 arXiv LLM Memory 日报

状态：**complete with download limitation**。已从 2026-09-29 官方公告批次入选 **20 篇**，均完成中文评析与机构优先级、相关性、novelty、证据可信度的独立判断。

## 批次口径

- 北京时间 2026-09-29 15:01（UTC 07:01）核验时，arXiv 的 [cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new) 官方 `new` 列表已切换为 **Tuesday, 29 September 2026**。
- 只纳入该正式公告批次的 new submission / 合法 cross-list；没有把 9 月 28 日旧批次或 replacement-only 更新拿来凑数。
- 提交日期与公告日期分开记录：本批次论文的 v1 提交日在 9 月 26–28 日，正式公告对应北京时间 9 月 29 日。

## PDF 与证据状态

- 本地环境访问 `https://arxiv.org/pdf/...` 在 TCP/HTTPS 连接阶段持续超时；抽样重试 `2609.32391` 亦在 8 秒连接超时后失败，因此没有伪造本地 PDF 或把 HTML 另存为 `.pdf`。
- 每篇评析均保留官方 PDF 链接，并基于官方 arXiv 全文 HTML 阅读方法、实验、消融、限制与首页署名；并非只读摘要。
- 三篇论文的机构行未能从官方 HTML 可靠解析，已明确标注“机构未核验”，未根据作者背景臆测。

## 入选论文（机构优先级 → 直接相关性 → novelty）

1. [SCLATE](./01-SCLATE.md) — **Apple｜直接相关**：持续学习 agent 的统一事件、时间与训练/评测 substrate。
2. [VALVE](./02-VALVE.md) — **Microsoft + 顶级高校｜直接相关**：验证门控的长期 code-agent skill evolution。
3. [MemAgent](./03-MemAgent.md) — **Tencent + 清华｜直接相关**：在 13 种异构记忆 provider 间学习读、用、写路由。
4. [JAM](./04-JAM.md) — **BAAI + 北大 + 港理工｜直接相关**：运行时 agentic research 构造 just-in-time memory。
5. [RIME](./05-RIME.md) — **JD.com｜直接相关**：由真实检索需求反向驱动记忆演化。
6. [ActiveMem](./06-ActiveMem.md) — **清华 + 华为诺亚｜直接相关**：依赖感知的动态 latent memory tree。
7. [LatentPersonal](./07-LatentPersonal.md) — **南京大学｜直接相关**：在共享 LoRA 空间中推断低维用户表示。
8. [PULSE](./08-PULSE.md) — **UCLA + UT Austin + 东南大学｜直接相关**：用 SAE 内部效用特征选择 ICL demonstrations。
9. [You Only Edit Once](./09-LDE.md) — **清华｜直接相关**：RLVR 训练的单步 demo-set 局部修复。
10. [ForkLeft](./10-ForkLeft.md) — **Melbourne + UC Davis + HKU｜直接相关**：前缀对齐的 AR→diffusion reasoning distillation。
11. [FactorDLM](./11-FactorDLM.md) — **UConn｜直接相关黑马**：用因子图精确处理 dLLM 非局部约束。
12. [JPEG-DLM](./12-JPEG-DLM.md) — **机构未核验｜直接相关黑马**：联合学习一 latent 多 token 的压缩 diffusion 表示。
13. [SeOPD](./13-SeOPD.md) — **北大 + 国防科大｜紧密相关**：将自生成深思 CoT 在线蒸馏进模型参数。
14. [EvoCUE](./14-EvoCUE.md) — **清华 SIGS + UPenn + 鹏城等｜直接相关**：把经验更新放到正确控制流位置。
15. [Threader](./15-Threader.md) — **机构未核验｜直接相关黑马**：保留原始对话，以结构化访问替代有损构造。
16. [NarraWorld](./16-NarraWorld.md) — **中关村学院 + 东南 + 人大等｜紧密相关**：共享世界/私有心智分层的长程结构记忆。
17. [ExpVoyager](./17-ExpVoyager.md) — **Yonsei｜直接相关黑马**：按当前任务导航原始经验并动态合成技能。
18. [How Linear Attention Remembers](./18-Linear-Attention-Memory.md) — **机构未核验｜latent memory 机制启发**：因果分解固定状态的写入、保持与读出。
19. [Downstream-Aware Context Selection](./19-Downstream-Aware-ICRL.md) — **UIUC + UVA｜直接相关**：按删除历史的下游影响管理在线 ICRL 上下文。
20. [Attention vs. SSM for ICL](./20-Attention-vs-SSM-ICL.md) — **Ohio State + RWTH｜直接相关**：用 belief geometry 分析证据组装、维持与寻址。

## 机构分布

- 指定重点工业研究机构：Apple、Microsoft、Tencent、JD.com；另有 Huawei Noah's Ark Lab。
- 一流研究机构/高校：BAAI、Tsinghua、Peking University、UCLA、UT Austin、UIUC、UPenn、HKU、University of Cambridge、NYU、University of Washington 等。
- 黑马补充：FactorDLM、Threader、ExpVoyager、How Linear Attention Remembers 等以方法原创性、实验严谨性或直接研究启发入选，并明确放在强机构候选之后。
- 今天没有发现可核验的 OpenAI、Anthropic、Google DeepMind、Meta、NVIDIA、xAI、Mistral、DeepSeek 新稿可优先替换上述候选。

## 主题趋势

1. **memory 从单一表示转向控制与路由**：MemAgent 管 provider，EvoCUE 管作用位置，RIME 管使用后更新。
2. **写入时压缩正在被重新审视**：JAM、Threader、ExpVoyager 都更愿意保留原始证据，在任务到来时再组织。
3. **agent evolution 进入验证治理阶段**：VALVE 强调回归门，SCLATE 强调可复现实验 substrate，SeOPD 研究经验向参数内化。
4. **personalization 走向低维 latent**：LatentPersonal 用用户向量导航共享 PEFT 空间，但仍需与可审计外部记忆结合。
5. **ICL memory 变得 model-aware/downstream-aware**：PULSE 看内部 feature，LDE 做局部编辑，ICRL selector 预测删除后果。
6. **diffusion LLM 的重点从“能否生成”转向训练对齐、状态压缩和精确约束**：ForkLeft、JPEG-DLM、FactorDLM 分别覆盖三层问题。

## 最值得深读的 3 篇

1. **MemAgent**：今天最直接改变 memory-system 设计空间的论文。它用统一接口和 13 provider 实证说明“没有一种记忆通吃”，并给出全生命周期路由方案。
2. **VALVE**：对 self-evolving memory 最重要的提醒是更新必须通过回归验证；它把长期 agent 学习从 demo 提升推进到可靠性治理。
3. **SCLATE**：如果要严肃比较 continual agent/memory 方法，事件时间线、经验回放和训练接口必须先可复现；这篇提供了很强的系统底座。

偏个性化可优先把 **LatentPersonal** 作为第 4 篇；偏 diffusion LLM 可按 **ForkLeft → FactorDLM → JPEG-DLM** 的顺序阅读。

## 可信度说明

- `4.5/5`：全文证据、规模、实验/消融与机构可信度都强，但仍保留系统归因或外部效度问题。
- `4.0–4.2/5`：全文较完整，有跨设置或理论支持；关键假设仍需独立复现。
- `3.7–3.9/5`：方向与结果有启发，但机构未核验、长期稳定性、真实部署或因果证据存在明显缺口。
- 机构优先级与论文证据可信度分开打分；强机构不自动获得高可信度。

## 核验日志

- 08:01–14:01：官方列表仍显示 9 月 28 日，状态保持 pending，没有使用旧批次替代。
- 15:01：cs.CL、cs.AI、cs.LG 官方 `new` 列表切换至 9 月 29 日；开始正式筛选、全文阅读与机构核验。
- 交付核验：20 个中文评析文件已生成；20 个 arXiv ID 唯一且均属于当天正式批次。PDF 本地下载受连接超时阻断，官方 PDF 链接均已保留。
