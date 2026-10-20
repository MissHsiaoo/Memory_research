# 2026-09-24 arXiv LLM Memory 日报

状态：**complete**。共入选 **20 篇**，每篇均已下载官方 PDF、通过 PDF 结构校验、阅读可提取全文，并从论文首页核验机构署名。

## 批次口径

- 北京时间 2026-09-24 11:01（UTC 03:01）核验时，arXiv 的 cs.CL、cs.AI、cs.LG 官方 `new` 列表已切换为 **Thursday, 24 September 2026**。
- 官方入口：[cs.CL new](https://arxiv.org/list/cs.CL/new)（73 个 new submissions）、[cs.AI new](https://arxiv.org/list/cs.AI/new)（59 个）、[cs.LG new](https://arxiv.org/list/cs.LG/new)（115 个）。筛选同时考虑该批次的合法 cross-list，排除 replacement-only 旧稿。
- “提交日期”与“正式公告日期”分开记录：入选论文提交日为 9 月 22 或 23 日，但均属于北京时间 9 月 24 日正式公告批次。

## 入选论文（机构优先级 → 直接相关性 → novelty）

1. [Harness as a Language](./01-Harness-as-a-Language.md) — **MIT CSAIL｜直接相关**：用可编程历史变量与递归 `invoke` 统一长期记忆和持续自改进。
2. [Just-in-Time Memory](./02-Just-in-Time-Memory.md) — **Salesforce AI Research｜直接相关**：把记忆整理从 write-time 移到 query-aware read-time。
3. [EnSIMem](./03-EnSIMem.md) — **UIUC + Amazon｜直接相关**：实体-属性索引只做地址，原始 episode 作为可追溯证据。
4. [COPE](./04-COPE.md) — **USTC + Alibaba Qwen｜直接相关**：稀疏反馈下以用户 embedding 和自评估做持续个性化。
5. [LOCKR](./05-LOCKR.md) — **NVIDIA + RIT｜直接相关**：用 diffusion LLM 隐状态轨迹识别并修复错误锁定。
6. [ChipMEM](./06-ChipMEM.md) — **UIUC + NVIDIA + Cadence｜直接相关**：用确定性 EDA verifier 门控程序性记忆写入。
7. [ProCredit](./07-ProCredit.md) — **Alibaba Tongyi + 中科院 + UCLA + NTU｜紧密相关**：把可验证进度分配到 agent 的具体 turn。
8. [When Context Misleads](./08-When-Context-Misleads.md) — **清华 + 华中科大｜直接相关**：ICL 需要判断上下文是否拥有“管辖权”。
9. [Hunyuan-A13B](./09-Hunyuan-A13B.md) — **Tencent Hunyuan｜弱相关但具启发性**：256K 上下文、agent 数据和快/慢推理的系统级参考。
10. [EvoAudio](./10-EvoAudio.md) — **Tencent Hunyuan + 清华 + CUHK-Shenzhen｜弱相关但高启发性**：由 verifier 驱动的递归自改进闭环。
11. [GUI-SD-v2](./11-GUI-SD-v2.md) — **Tencent + 中科院 + 清华｜紧密相关**：逐步 reasoning/memory supervision 训练长程 GUI agent。
12. [Planned Test-Time Scaling](./12-Planned-Test-Time-Scaling.md) — **UCLA + Amazon｜弱相关但具启发性**：协调互补推理路径，避免重复采样模式坍缩。
13. [KITE](./13-KITE.md) — **StepFun｜弱相关但具架构启发**：扩容模型但保持历史 KV 生产路径不变。
14. [R3CON](./14-R3CON.md) — **University of Washington｜直接相关**：显式、任务条件化地构造可计算上下文表示。
15. [UMIM](./15-UMIM.md) — **UChicago + TTIC + Stony Brook｜紧密相关**：将多 token 顺序计算蒸馏为 surrogate embedding。
16. [Causal Shortcuts for DLMs](./16-Causal-Shortcuts-DLM.md) — **浙江大学 + 上海 AI Lab｜直接相关**：以 CMI 提取 diffusion 推理捷径。
17. [MemBodied](./17-MemBodied.md) — **NTU 等｜直接相关**：VLA 的固定容量双路径 episodic memory。
18. [Memory Control Signals](./18-Memory-Control-Signals.md) — **人民大学 + 清华；TierFlow 按 PDF 署名｜直接相关**：动作前隐藏状态已编码压缩/召回需求。
19. [StateComp](./19-StateComp.md) — **人民大学 + 清华；TierFlow 按 PDF 署名｜直接相关**：按当前状态判断历史何时可安全压缩。
20. [DRSR](./20-DRSR.md) — **人民大学 + 清华；TierFlow 按 PDF 署名｜直接相关**：学习多块历史联合删除风险而非独立重要性。

## 机构分布

- 指定重点工业研究机构：Salesforce AI Research、Amazon、Alibaba/Qwen/Tongyi、NVIDIA、Cadence、Tencent Hunyuan、StepFun。
- 全球一流高校/实验室：MIT CSAIL、UIUC、USTC、Tsinghua、UCLA、University of Washington、UChicago/TTIC、NTU、Zhejiang University、Shanghai AI Laboratory、RUC、CAS 等。
- 本日强机构候选足够，最终 **没有用低机构优先级稿件凑数**。TierFlow 未超出论文首页信息作身份推断，并因共同署名高校强、研究直接相关而列入后段。

## 主题趋势

1. **记忆从静态摘要转向任务时编译**：JITMEM、EnSIMem、R3CON 都强调先保留证据，再针对当前任务构造工作上下文。
2. **内部状态开始承担 memory controller**：LOCKR、Memory Control Signals、StateComp 用 hidden trajectory/state 决定修复、压缩或召回。
3. **写入可信度由外部 verifier 提供**：ChipMEM、ProCredit、EvoAudio 把可执行反馈用于技能记忆、进度信用或自进化课程。
4. **个性化从 prompt 画像走向参数化记忆**：COPE 用极小用户 embedding 表示隐式偏好，同时保留检索历史的互补性。
5. **Diffusion LLM 研究进入过程干预阶段**：LOCKR 读去噪轨迹，CSL 学 causal shortcut，不再只比较最终输出。
6. **高效上下文是系统共性问题**：UMIM、KITE、StateComp/DRSR 分别从 latent token、模型架构和历史治理降低成本。

## 最值得深读的 3 篇

1. **Just-in-Time Memory**：今天最清晰的范式变化。它把 memory curation 的时机重新定义，并用立即可得的任务奖励解决长期信用分配。
2. **Harness as a Language**：对“记忆是不是必须是专用模块”提出强挑战；其长期任务与持续自改进实验值得逐项复现。
3. **EnSIMem**：结构化寻址但不丢原始证据，最接近可审计 personalized memory 的工程底座。

若更偏个性化方向，建议把 **COPE** 作为第 4 篇优先深读；若更偏 diffusion LLM，则优先组合阅读 **LOCKR + Causal Shortcuts**。

## 检查记录

- **08:08 北京时间**：三个官方 `new` 列表仍停留在 9 月 23 日；状态 pending，不通知用户。
- **10:01 北京时间**：再次核验 cs.CL、cs.AI、cs.LG 官方 `new` 列表，三者仍显示 9 月 23 日；状态 pending，不通知用户。
- **11:01 北京时间**：三个官方 `new` 列表均切换至 9 月 24 日；开始筛选、下载、全文提取与机构核验。
- **交付核验**：20 个入选 PDF 均通过 `pdfinfo` 结构检查；20 个中文评析文件与本 README 已生成。临时每小时续跑结束，自动任务恢复为每天北京时间 08:00。
