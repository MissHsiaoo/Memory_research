# 2026-09-23 arXiv LLM Memory 日报

状态：**筛选与中文评析完成；本地 PDF 下载受网络阻断**。

## 批次核验

- 官方公告批次：**Wednesday, 23 September 2026**。
- 北京时间对应：2026-09-23；08:03 与 09:02 检查时尚未发布，20:44 后核验到正式批次。
- 核验入口：[cs.CL new](https://arxiv.org/list/cs.CL/new)、[cs.AI new](https://arxiv.org/list/cs.AI/new)、[cs.LG new](https://arxiv.org/list/cs.LG/new)。
- 只收录该正式批次中经论文 v1 日期核验为近期新稿的候选；旧 v1、replacement 或仅因分类/元数据重现的论文不计入。
- 最终入选：**20 篇**。排序规则：机构优先级 → 与研究主题的直接相关性 → novelty/证据质量。

## 入选论文

| 排名 | 论文 | 机构优先级 | 相关性 | 选择理由 |
|---:|---|---|---|---|
| 1 | [CliffCompaction](02-CliffCompaction.md) | S：CMU/Bosch | 直接 | 原始事件日志上做非改写式压缩，百万 token coding agent 的成本与长期能力证据完整。 |
| 2 | [Informed Masking](04-Informed-Masking.md) | S：Xiaomi/RUC/PKU | 直接 | 首次系统利用 dLLM rollout 的 upstream/downstream 结构改善 RL 掩码采样。 |
| 3 | [Qwen-Audio-3.1-Realtime](07-Qwen-Audio-3.1-Realtime.md) | S：Alibaba | 直接 | 自演化可执行环境、多粒度 GRPO、持久任务与显式 memory boundary 形成完整 agent 路线。 |
| 4 | [Evo-Denoiser](08-Evo-Denoiser.md) | S：Huawei/HKUST | 直接 | 393 参数 CMA-ES 调度器把 attention failure diagnosis 转成极轻量解码策略。 |
| 5 | [Knowledge Pull Requests](09-Knowledge-Pull-Requests.md) | S：JHU | 直接 | 将持续记忆更新拆成可审核 claim proposal 与文档 diff，适合可追溯写入。 |
| 6 | [Qwen3.8-Omni](06-Qwen3.8-Omni.md) | S：Alibaba | 中等直接 | Omni-Memory、1M context、GDN recurrent state 与多模态按需访问具有工业系统启发。 |
| 7 | [Matryoshka Attribution](05-Matryoshka-Attribution.md) | S：Stanford | 弱相关但高启发 | 为 latent representation/weight memory 定位提供可学习、跨稀疏度归因工具。 |
| 8 | [Brain-Inspired Hierarchical Modularity](10-Brain-Hierarchical-Modularity.md) | S：Tsinghua | 弱相关但高启发 | 用层级模块隔离冲突经验、整合兼容经验，可迁移到 self-evolving memory。 |
| 9 | [Beyond Repeated Sampling](03-Beyond-Repeated-Sampling.md) | S：Meta FAIR/Inria/NYU | 中等直接 | 把语义概念变成可迁移 search policy；强基线审计与跨模型迁移尤其扎实。 |
| 10 | [SpeakerMem-R1](01-SpeakerMem-R1.md) | A：Zhejiang University | 高度直接 | 原话证据轨+结构化状态轨专门处理多人个性化记忆、归属和时间更新。 |
| 11 | [CMC](16-CMC.md) | A：Notre Dame/Aizu | 高度直接 | 长上下文压缩为 answer-aligned latent memory embeddings，九种模型组合验证。 |
| 12 | [Growing Harness](12-Growing-Harness.md) | A：CAS/UCAS | 高度直接 | 把失败经验编译进共享 executable harness，并以 held-out gate 防回归。 |
| 13 | [Flash-dLLM](11-Flash-dLLM.md) | A：MBZUAI | 直接 | 联合 KV-cache I/O kernel 与 self draft-and-verify，切中 dLLM 部署瓶颈。 |
| 14 | [ToolCompass](14-ToolCompass.md) | A：NTU/ZJU/UTS | 中等直接 | 按功能塑造 latent tool-call representations，实现未见工具的经验迁移。 |
| 15 | [ClusterFewshot](15-ClusterFewshot.md) | A：Tel Aviv University | 高度直接 | 语义覆盖+held-out utility 选择 ICL demonstrations，适合个性化示例记忆。 |
| 16 | [GravityOCR](13-GravityOCR.md) | A：SNU/Korea U/Trillion Labs | 直接 | 共享参数的 diffusion draft + AR verify，为可靠并行生成提供清晰实例。 |
| 17 | [Minimal Recurrent Behavioral Memory](17-Minimal-Recurrent-Behavioral-Memory.md) | B：机构未核验 | 高度直接 | 用信息论刻画部分可观测行为所需最小 recurrent memory，理论新颖性高。 |
| 18 | [AIDE²](18-AIDE2.md) | B：Weco AI | 高度直接 | 8 日自主 recursive self-improvement，连续改进包含 context/memory mechanism。 |
| 19 | [Impact Is Not Invalidation](19-Impact-Not-Invalidation.md) | B：Thomson Reuters | 高度直接 | execution-grounded 地证明 memory staleness 必须针对具体 claim 判断。 |
| 20 | [Diffusion Sequential Reappearance](20-Diffusion-Unlearning.md) | B：Konkuk University | 直接 | 揭示一次遗忘后会随连续更新重新出现，提供“删除生命周期”关键视角。 |

## 机构分布

- S 级（9 篇）：Alibaba 2；CMU/Bosch、Meta FAIR/Inria/NYU、Stanford、Huawei/HKUST、Xiaomi/RUC/PKU、JHU、Tsinghua 各 1。
- A 级（7 篇）：Zhejiang University、MBZUAI、CAS/UCAS、SNU/Korea University/Trillion Labs、NTU/ZJU/UTS、Tel Aviv University、Notre Dame/Aizu 各 1。
- B 级黑马/启发性补充（4 篇）：Weco AI、Thomson Reuters、Konkuk University、机构未核验各 1。
- 机构优先级与证据可信度分开：B 级论文可因主题高度直接而入选，但没有被包装成顶级机构成果。

## 主题趋势

1. **记忆从文本摘要转向可验证状态。** SpeakerMem、KPR、Impact Is Not Invalidation 都要求 claim/人物/时间/provenance 可追踪。
2. **经验被编译进系统。** CliffCompaction 保留不可变原始历史；Growing Harness 与 AIDE² 把经验固化为 executable policy/harness，而非每次重新塞进 prompt。
3. **latent memory 同时追求信息下限与模型兼容。** Minimal Memory 给理论下限，CMC 给跨 decoder 的软记忆接口，MAttr 给内部归因工具。
4. **diffusion LLM 的竞争焦点转向后训练与系统推理。** Informed Masking、Evo-Denoiser、Flash-dLLM、GravityOCR 分别处理 RL 子问题、调度、I/O/cache 与验证。
5. **个性化仍缺少真实长期用户评测。** 当天最接近的是多人对话 memory 与 ICL demo selection；真正的隐私、用户控制、跨月偏好演化仍是空缺。

## 最值得深读的 3 篇

1. **CliffCompaction**：保留不可变原始记录、working memory 可丢弃重建，比继续做 summary-of-summary 更可能成为长期 agent 工程基线。
2. **Informed Masking**：发现 dLLM 中被忽略的结构化采样维度，易复现，也可能推广到更广的 latent-state credit assignment。
3. **SpeakerMem-R1**：直接覆盖 personalized/social memory，双轨设计把可追溯原话与可更新人物状态结合，是今天最贴近实际记忆系统的一篇。

## PDF 与证据状态

- 20 篇均保存了官方 arXiv abstract/PDF 链接；通过可访问的 arXiv PDF/HTML 全文通道核验首页机构、v1 日期，并阅读可用的方法、实验和结果内容。
- 本机对 `arxiv.org:443` 的直接连接在 20:46、21:03 多次超时；21:03 对 20 个 PDF 并发重试仍全部连接失败，因此本地 `papers/` 目录没有伪造或残缺 PDF。详见 [PDF_DOWNLOAD_STATUS.md](PDF_DOWNLOAD_STATUS.md)。
- 可信度评分据实际可读证据给出；没有仅凭摘要给 5/5。

## 旧稿/更新排除审计

以下论文虽然在页面中出现且主题很相关，但 v1 日期明显早于本批，按规则排除：MoM (2609.25054, v1 2026-09-07)、LatentPort (2609.25053, v1 2026-09-07)、PACE-dLLM (2609.26249, v1 2026-08-13)、AIBuildAI-2.5 (2609.25047, v1 2026-09-06)、Synthetic Personas (2609.25010, v1 2026-07-27)、CoVeR (2609.26086, v1 2026-09-03)。它们没有用于凑满 20 篇。

## 检查记录（增量保留）

- **08:03 北京时间**：cs.CL、cs.AI、cs.LG 正式列表和 RSS 均仍停留在 9 月 22 日，状态 pending。
- **09:02 北京时间**：三个正式列表及 cs.CL、cs.AI RSS 仍显示 9 月 22 日；cs.LG RSS 下载超时，但官方 HTML 仍为 9 月 22 日，状态 pending。
- **20:44 后**：官方列表显示 Wednesday, 23 September 2026，转入筛选、v1 去重、机构核验和全文评析。
- **21:03**：20 个官方 PDF 本地下载并发重试均在连接 arxiv.org:443 时超时；保留官方链接并记录失败，不以旧论文替代。
