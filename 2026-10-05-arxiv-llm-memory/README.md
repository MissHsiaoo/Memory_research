# 2026-10-05 arXiv LLM Memory 日报

- 2026-10-05 08:03（北京时间，Asia/Shanghai）核验：官方 [cs.CL/new](https://arxiv.org/list/cs.CL/new)、[cs.AI/new](https://arxiv.org/list/cs.AI/new)、[cs.LG/new](https://arxiv.org/list/cs.LG/new) 均仍显示 **Friday, 2 October 2026**，尚未出现 10 月 5 日正式 New submissions。
- 当时状态为 **pending**，不是“0 篇合格论文”的筛选结果。10 月 5 日批次出现之前，未把 10 月 2 日旧批次、仅更新版本或仅按提交日期判断的稿件当作今日新稿。
- 此段保留早间核验历史；11:02 公告更新后，本目录已按机构优先级、相关性和新颖性完成筛选，没有扩展到近 30 天。

## 增量核验

- 2026-10-05 09:00（北京时间）：cs.CL、cs.AI、cs.LG 官方 new 列表仍全部显示 10 月 2 日，今日正式批次仍 pending。
- 2026-10-05 10:00（北京时间）：三个官方 new 列表仍全部显示 10 月 2 日，状态无变化。
- 2026-10-05 11:02（北京时间）：三个官方 new 列表均更新为 **Monday, 5 October 2026**；此时开始正式筛选。本报告仅来自三类官方 **New submissions**（cs.CL 63 篇、cs.AI 124 篇、cs.LG 197 篇），不是 Cross-lists 或 Replacements。入选 20 篇逐一核对均属至少一个上述 New submissions 区域，按 arXiv ID 去重。

## 本日结果与日期口径

- **完成：20 篇**。公告日期是 arXiv 页面写明的 **2026-10-05**；对应北京时间 10 月 5 日上午公布后（11:02 核验）。论文页面的首次提交日期为 10 月 1 日或 2 日，**不把提交日期当公告日期**；长周末期间的投稿可在 10 月 5 日进入正式新稿批次。
- 官方批次：[cs.CL/new](https://arxiv.org/list/cs.CL/new) · [cs.AI/new](https://arxiv.org/list/cs.AI/new) · [cs.LG/new](https://arxiv.org/list/cs.LG/new)。每篇下方另附论文官方页面和本地 PDF。公告页是动态 `new` 链接，日后会更新，单篇 arXiv 页面才是持久链接。
- 排序规则：**机构优先级 → 研究直接相关性 → 方法新颖性与证据严谨性**。S 指本次明确优先的高水平企业研究组织及其合作论文；A+ 指全球一流研究型高校/实验室。**机构等级不是论文结论的可信度分数**。同级内有些条目为“弱相关但具启发性”，不将它们伪称为直接研究记忆。全部机构名以 PDF 首页署名为准；例如 #06 仅写 ByteDance，不推断为 Seed。

## 精选与排序

| 排名 | 论文与文件 | 已核机构 | 关联性 / 入选理由 | 证据可信度 |
|---:|---|---|---|---:|
| 01 | [Sigma：连续扩散语言模型](01-Sigma-continuous-diffusion.md) · [arXiv](https://arxiv.org/abs/2610.02665) | NVIDIA / Cornell / Georgia Tech | 直接；3B/8B 连续轨迹、可控扩散 | 4/5 |
| 02 | [MIRA：研究 Agent 元推理](02-MIRA-meta-reasoning.md) · [arXiv](https://arxiv.org/abs/2610.02525) | Meta AI / Columbia / Tel Aviv | 直接；持久研究记录与元决策训练 | 4/5 |
| 03 | [VERSE：自进化 Harness](03-VERSE-self-evolving-harness.md) · [arXiv](https://arxiv.org/abs/2610.02616) | Amazon / MIT | 直接；执行验证门控的工具/技能自改进 | 3/5 |
| 04 | [GSA2：双侧关联记忆修正](04-GSA2-associative-memory.md) · [arXiv](https://arxiv.org/abs/2610.02816) | Tencent / HKUST(GZ) | 直接于 latent memory；固定容量双侧擦写 | 4/5 |
| 05 | [DyadMem：用户—Agent 关系记忆](05-DyadMem-relational-agent-memory.md) · [arXiv](https://arxiv.org/abs/2610.03020) | StepFun / NTU / NUS / HKU | 直接；全链路个性化记忆基准 | 3/5 |
| 06 | [Action Calibration：历史如何变经验](06-Action-calibration-agent-experience.md) · [arXiv](https://arxiv.org/abs/2610.02769) | ByteDance / Renmin University | 直接；动作—结果绑定的干预证据 | 3/5 |
| 07 | [LINEUP：共享低秩个性化](07-LINEUP-personalization.md) · [arXiv](https://arxiv.org/abs/2610.02353) | Samsung Semiconductor / Rice | 直接；每用户仅 8 标量的修正码 | 4/5 |
| 08 | [共享 KV 的 Looped Transformer](08-Shared-memory-looped-transformers.md) · [arXiv](https://arxiv.org/abs/2610.02383) | IBM Research / Cornell | 直接于内部状态；省缓存但加 FLOPs | 4/5 |
| 09 | [GraphMemory：图式测试时学习](09-GraphMemory-test-time-learning.md) · [arXiv](https://arxiv.org/abs/2610.02687) | IBM Research / Rice | 直接；按需小子图替代无限上下文 | 3/5 |
| 10 | [APDMem：逐层展开个人记忆](10-APDMem-progressive-disclosure.md) · [arXiv](https://arxiv.org/abs/2610.02472) | JPMorgan Chase ML CoE | 直接；四层证据检索的成本—精度权衡 | 4/5 |
| 11 | [DepGPO：命令依赖与信用分配](11-DepGPO-terminal-agent-credit.md) · [arXiv](https://arxiv.org/abs/2610.03634) | Huawei Noah's Ark / Southeast University | **弱相关但具启发性**；经验中的依赖证据 | 3/5 |
| 12 | [AdaStep：可靠性加权步骤信用](12-AdaStep-agent-credit.md) · [arXiv](https://arxiv.org/abs/2610.03223) | Xiaomi / Tsinghua / Nanjing | **弱相关但具启发性**；记忆写入可借鉴可信度权重 | 3/5 |
| 13 | [PlurPO：多方视角抑制谄媚](13-PlurPO-personalized-alignment.md) · [arXiv](https://arxiv.org/abs/2610.02568) | Amazon / Stanford / UW | **弱相关但具启发性**；个性化输出的外部性 | 3/5 |
| 14 | [Sentry：条件触发的失败经验](14-Sentry-conditional-failure-memory.md) · [arXiv](https://arxiv.org/abs/2610.02994) | Stanford | 直接；只在匹配失败时暴露记忆 | 4/5 |
| 15 | [Ansatz：数学研究图记忆](15-Ansatz-continual-graph-memory.md) · [arXiv](https://arxiv.org/abs/2610.02945) | UCLA | 直接；事实、计划、反例与依赖图 | 2/5（开放数学主张未独立核验） |
| 16 | [偏好的隐性成分](16-Tacit-preference-components.md) · [arXiv](https://arxiv.org/abs/2610.03025) | Stanford / University of Toronto | 直接于个性化理论；弱于记忆算法 | 3/5 |
| 17 | [后训练损伤 In-context steerability](17-In-context-steerability-collapse.md) · [arXiv](https://arxiv.org/abs/2610.02614) | Harvard / HPI / Potsdam | 直接；用户立场适应与默认立场区分 | 3/5 |
| 18 | [Pivot-SD：扩散去噪枢纽监督](18-Pivot-SD-diffusion.md) · [arXiv](https://arxiv.org/abs/2610.03665) | KAIST / Toronto / Vector | 直接；少量关键承诺的后训练 | 3/5 |
| 19 | [事实学习与检索形式分离](19-Request-form-retrieval.md) · [arXiv](https://arxiv.org/abs/2610.03251) | KAIST | 直接；受控状态干预解释记忆读取 | 4/5 |
| 20 | [PAPER2LLM++：论文驱动自进化](20-PAPER2LLM-continual-self-evolution.md) · [arXiv](https://arxiv.org/abs/2610.02793) | UIUC / Yale / Penn State | 直接；文献—评测—更新的闭环 | 3/5 |

**机构分布：**入选 20 篇中，13 篇 PDF 首页署名包含优先企业研究组织或其合作团队（NVIDIA 1、Meta AI 1、Amazon 2、Tencent 1、StepFun 1、ByteDance 1、Samsung Semiconductor 1、IBM Research 2、JPMorgan Chase ML CoE 1、Huawei Noah's Ark 1、Xiaomi 1）；另 7 篇为顶尖高校/实验室主导。按主列表中出现的企业合作计数，不把联合署名论文重复计总篇数。本日没有用低机构优先级的“黑马”填充到 20。

**主题趋势：**（1）长期记忆的价值从容量转向**写入、调用和验证策略**：DyadMem、APDMem、Sentry、Action Calibration 分别暴露捕获、层级读取、条件触发和动作结果绑定问题。（2）**模型内部记忆**与**外部用户记忆**是两条不同路线：GSA2/Looped Transformer 不应与跨会话个人记忆混为一谈。（3）自进化的核心瓶颈是**证据可信的信用分配与回滚**，见 MIRA、VERSE、DepGPO、AdaStep、PAPER2LLM++。（4）扩散 LLM 同时出现连续潜空间与枢纽监督两条改进线。

**最值得深读 3 篇：**

1. **#05 DyadMem**：与你的 personalized agent memory 最贴近，提供 Capture→Update→Recall→QA 的故障定位，而非只测最终答案；尤其可看 URAM 标注规则与不安全删除用例。
2. **#07 LINEUP**：给出可直接转成系统设计的“共享个性化基底 + 极小私人状态”，并有参数效率/有限历史实验；重点审查少数用户和隐私边界。
3. **#02 MIRA**：把持久研究记忆与长时 Agent 的“下一步做什么”绑定到可训练决策边界；重点关注固定证据整理器的遗漏风险。

**阅读和证据说明：**每篇均保存有效官方 PDF、核验首页署名，并查阅方法、实验与可找到的局限；笔记明确区分作者报告的直接证据与本报告的未来影响/critical thinking 推断。预印本不等于独立复现；可信度 1–5 分评论文证据强度，不按机构打分。特别是 #15 的开放数学成果没有独立形式化证明审计。
