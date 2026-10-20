# 2026-10-01 arXiv：LLM Memory / ICL / Personalization / Diffusion LLM 日报

## 批次与筛选口径

- **报告日：2026-10-01，北京时间。** 只取 arXiv [cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new) 正式标为 **Thursday, 1 October 2026** 的 **New submissions**。同日出现的 cross-list 与 replacement 不计入；论文的 v1 提交日期另列，不能当作公告日期。公告日对应北京时间 10 月 1 日。
- 本批共选 **20 篇**，均在当天新稿区核验；20/20 官方 PDF 已下载、可解析并保存于本目录。机构署名以 PDF 首页为准；摘要未披露的实验细节以 PDF 核读，不把作者主张视作独立复现。
- 排序原则是**机构优先级 → 研究直接相关性 → 方法新颖性**。这里的 S/A+ 是本次阅读优先级，不是机构综合排行榜，更不等同于论文证据可信度。前 13 篇有头部企业研究团队参与，后 7 篇以一流高校/实验室为主；同一层级内优先与记忆/上下文/扩散模型直接相关的工作。第 12、13 篇明确为**弱相关但具启发性**，非凑数的“记忆论文”。

## 入选论文（按阅读优先级）

| # | 论文与笔记 | 核验机构 / 优先级 | 与主题的联系 / 入选理由 | v1 提交 |
|---:|---|---|---|---|
| 1 | [ReCAP — Persistent Context Graphs](./01-recap.md) · [arXiv](https://arxiv.org/abs/2609.40118) | Microsoft、UCSB、Notre Dame · S | 直接相关；依赖图做 agent 记忆压缩，兼顾质量与延迟 | 09-30 |
| 2 | [ScholarEvolve — Lifelong Agent Harness Evolution](./02-scholarevolve.md) · [arXiv](https://arxiv.org/abs/2609.40169) | Microsoft、UCSB · S | 直接相关；把研究文献变成 harness 持续演化的外部记忆 | 09-30 |
| 3 | [StateTree — Long-Term Dialogue Reasoning](./03-statetree.md) · [arXiv](https://arxiv.org/abs/2609.38809) | Alibaba Taobao & Tmall、Zhejiang U · S | 直接相关；用树状态追踪训练长程对话更新推理 | 09-30 |
| 4 | [PivotOPD — Recovery from Pivotal Mistakes](./04-pivotopd.md) · [arXiv](https://arxiv.org/abs/2609.40285) | NVIDIA、Princeton、Maryland · S | 相关；把失败转为恢复训练样本，而非仅防错 | 09-30 |
| 5 | [SkillFM — Latent Flow Skill Generation](./05-skillfm.md) · [arXiv](https://arxiv.org/abs/2609.39382) | Meta、NTU、Edinburgh · S | 直接相关；技能从文本检索转为潜空间条件生成 | 09-30 |
| 6 | [MILO — Automated Harness Discovery](./06-milo.md) · [arXiv](https://arxiv.org/abs/2609.38349) | AWS AI Labs、Georgia Tech、CMU 等 · S | 直接相关；搜索谱系同时记成功与失败改动 | 09-29 |
| 7 | [Hermes — Learning Contextual Reasoning](./07-hermes.md) · [arXiv](https://arxiv.org/abs/2609.38332) | AWS AI Labs、CMU、Georgia Tech 等 · S | 直接相关；学习上下文预算与委派控制 | 09-29 |
| 8 | [RefCon — Contrastive Memory Extraction](./08-refcon.md) · [arXiv](https://arxiv.org/abs/2609.39143) | Huawei Technologies · S | 直接相关；轨迹对比和自修订提炼代理经验 | 09-30 |
| 9 | [Reverse Scoring for Diffusion LM Agents](./09-reflect-reverse.md) · [arXiv](https://arxiv.org/abs/2609.38536) | Huawei Noah's Ark、TU Darmstadt、UCL · S | 直接相关；diffusion agent 失败恢复的新动作评分 | 09-29 |
| 10 | [PCPO — Self-Evolving Algorithm Agents](./10-pcpo.md) · [arXiv](https://arxiv.org/abs/2609.38757) | Huawei Noah's Ark、Nanjing U · S | 相关；群体候选作为持续演化经验池 | 09-30 |
| 11 | [DMD for Continuous Diffusion LMs](./11-dmd.md) · [arXiv](https://arxiv.org/abs/2609.40235) | Cohere、Inria/PSL、École Polytechnique · S | 直接相关；低步数 diffusion LM 蒸馏 | 09-30 |
| 12 | [RSIGame — Recursive Self-improvement](./12-rsigame.md) · [arXiv](https://arxiv.org/abs/2609.39045) | ByteDance Inc.、UCSD、CMU · S | **弱相关但具启发性**；产物测试驱动自演化；PDF 未注明 Seed | 09-30 |
| 13 | [Demographic Pluralism](./13-demographic-pluralism.md) · [arXiv](https://arxiv.org/abs/2609.38555) | Amazon Science · S | **弱相关但具启发性**；群体偏好分布启发个体画像不确定性 | 09-29 |
| 14 | [LatentHarness — Latent Memory Actions](./14-latentharness.md) · [arXiv](https://arxiv.org/abs/2609.39740) | Université de Montréal、Mila · A+ | 直接相关；THINK/RECALL/EXIT 的反事实策略学习 | 09-30 |
| 15 | [MemCodex — Self-Programming Memory](./15-memcodex.md) · [arXiv](https://arxiv.org/abs/2609.39765) | Université de Montréal、Mila · A+ | 直接相关；自演化层级读写程序 | 09-30 |
| 16 | [STAM — Clinical State-Transition Memory](./16-stam.md) · [arXiv](https://arxiv.org/abs/2609.38490) | UCLA、Optum AI · A+ | 直接相关；个人状态变化和历史证据门控 | 09-29 |
| 17 | [When Context Changes](./17-cicm.md) · [arXiv](https://arxiv.org/abs/2609.38866) | UC Berkeley · A+ | 直接相关；旧值绑定导致的上下文更新失败 | 09-30 |
| 18 | [Shifting Mechanisms — In-Context Retrieval](./18-shifting-mechanisms.md) · [arXiv](https://arxiv.org/abs/2609.38530) | Cornell · A+ | 直接相关；位置编码影响记忆检索机制 | 09-29 |
| 19 | [Self-Repulsive Diffusion LM Sampling](./19-self-repulsion.md) · [arXiv](https://arxiv.org/abs/2609.39560) | ETH Zürich、EPFL · A+ | 直接相关；并行扩散路径去重、多样性增加 | 09-30 |
| 20 | [Action-Conditioned Bisimulation for GUI Memory](./20-gui-bisimulation.md) · [arXiv](https://arxiv.org/abs/2609.38778) | Peking U、ECNU、USC · A+ | 直接相关；按动作后果而非界面外观合并记忆状态 | 09-30 |

## 机构分布与主题趋势

机构以论文首页合作署名计，**不是互斥计数**：14 篇有企业研究团队参与（Microsoft 2、AWS AI Labs 2、Huawei 3，Alibaba、NVIDIA、Meta、Cohere、ByteDance Inc.、Amazon Science、Optum AI 各 1）；其中多篇同时由一流高校合作完成。后 7 篇以 Mila/蒙特利尔大学 2、UCLA/Optum AI 1、UC Berkeley 1、Cornell 1、ETH/EPFL 1、北大/华东师大/USC 1 为核心。ByteDance 论文仅核验到 ByteDance Inc.，不推断为 Seed。

三个值得注意的横向趋势：

1. **记忆从静态摘要变成受控的状态/程序。** ReCAP 保留依赖图；StateTree、STAM 显式追踪状态变化；LatentHarness 与 MemCodex 学习何时读写以及读写程序。
2. **自演化从“保留最好经验”走向可追溯的试错。** ScholarEvolve 借外部文献，MILO 留下失败谱系，RefCon 对比轨迹，PCPO 维护候选群体。关键未决问题是离线搜索成本与在线分布漂移。
3. **Diffusion LLM 正在获得代理控制与采样工具。** 反向任务评分、分布匹配蒸馏和并行路径排斥分别解决重试、步数和候选同质化；但真实长程 agent 上的闭环评测仍少。

## 今天最值得深读的 3 篇

1. **[ReCAP](./01-recap.md)**：最贴近部署中的 agent memory 压缩问题，方法可分解为重要性、依赖保留和恢复成本；需特别复核其延迟数字中哪些是估算。
2. **[StateTree](./03-statetree.md)**：把长对话状态推理拆成可训练的路径追踪任务，少量样本向 128K 外推的主张值得复现；重点看合成树到真实个人偏好的迁移。
3. **[LatentHarness](./14-latentharness.md)**：潜在记忆动作与反事实蒸馏提供较清晰的下一代 latent memory 控制框架；重点看真实长程场景的误写与遗忘。

## 解读边界

“可信度”是各笔记对**论文本身证据**的 1–5 分评估，与机构优先级独立。所有数值均为论文作者报告，未做独立复现实验。未来影响和 critical thinking 中的外推均明确以“推断”标示。第 12、13 篇提供跨方向启发，但不能当成直接的个人化记忆进展。
