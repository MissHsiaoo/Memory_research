# 2026-10-12 arXiv LLM Memory 日报

## 公告批次状态

- 2026-10-12 08:14 北京时间（UTC+8）核验，对应美国东部夏令时 2026-10-11 20:14（UTC−4）。
- [cs.CL 官方 new 列表](https://arxiv.org/list/cs.CL/new)、[cs.AI 官方 new 列表](https://arxiv.org/list/cs.AI/new)、[cs.LG 官方 new 列表](https://arxiv.org/list/cs.LG/new) 均仍显示 `Showing new listings for Friday, 9 October 2026`；不能把该旧批次当作北京时间 10 月 12 日新论文。
- [arXiv 官方公告时间与假日表](https://info.arxiv.org/help/availability.html)记载通常美国东部时间周日 20:00 公告、2026-10-12（美国东部时间周一）为假日。现有证据只能确认本次核验时 **10 月 12 日批次尚未出现在上述正式列表**，不能据此断言当日最终休刊或推定具体延迟原因。

## 08:14 的暂时结果（已被 11:01 新公告取代）

当时状态为 **pending（待公告复核）**，暂未入选论文。没有向近 30 天扩展，也没有把旧论文或仅更新版本凑数。以下最终结果以后来可见的 10 月 12 日正式批次为准。

## 增量复核

- 2026-10-12 09:01 北京时间：cs.CL / cs.AI / cs.LG 官方 new 列表仍均显示 2026-10-09，状态不变（pending）。
- 2026-10-12 10:01 北京时间：上述三个官方 new 列表仍均显示 2026-10-09，状态不变（pending）。
- 2026-10-12 11:01 北京时间：上述三个官方 new 列表均切换为 `Showing new listings for Monday, 12 October 2026`。正式批次已可见，开始筛选；此后以上述批次为唯一范围。

## 最终结果与筛选口径

**正式公告日期：arXiv 列表标记 2026-10-12（周一）；北京时间 2026-10-12 11:01 确认可见，对应美国东部夏令时 2026-10-11 23:01。**该公告日期不是论文的提交日期：入选稿件的 arXiv 提交记录分别为 10 月 8 日或 9 日，但均须出现在本次官方 `New submissions` 栏目。只从 [cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new) 的这一正式批次新投稿筛选，剔除交叉列示中的旧论文和 replacements。arXiv 的[公告机制与假日说明](https://info.arxiv.org/help/availability.html)解释了为何提交与正式公告可以相隔数日。

目标 20 篇，本次入选 **20 篇**。排序先看 PDF 核验的机构优先级，再看与指定主题的直接相关性、方法新颖性及证据严谨度。同一论文跨类只计一次。以下“可信度”仅评估论文证据，不等于机构优先级；所有数值与结论均为论文报告，尚非独立复现实验。

| 序位 | 论文、官方链接及评析 | 机构优先级 / 关联 | 关键新意 | 可信度 |
| --- | --- | --- | --- | --- |
| 01 | [ReHarness](https://arxiv.org/abs/2610.12668) · [评析](01-ReHarness.md) · [PDF](2610.12668.pdf) | A Meta / 直接 | 反馈反向修订旧反思 | 4/5 |
| 02 | [T-Mem](https://arxiv.org/abs/2610.12874) · [评析](02-T-Mem.md) · [PDF](2610.12874.pdf) | A Alibaba / 直接 | 多方对话时间证据森林 | 4/5 |
| 03 | [T²Mem](https://arxiv.org/abs/2610.13348) · [评析](03-T2Mem.md) · [PDF](2610.13348.pdf) | A Alibaba / 直接 | 查询时动态建记忆 | 4/5 |
| 04 | [Elastic Latent Recurrence](https://arxiv.org/abs/2610.12582) · [评析](04-ELR.md) · [PDF](2610.12582.pdf) | A NVIDIA / 直接 | 无明显一循环税的弹性递归 | 4/5 |
| 05 | [CDLM Design Space](https://arxiv.org/abs/2610.13834) · [评析](05-Apple-CDLM.md) · [PDF](2610.13834.pdf) | A Apple / 直接 | DoubleCat、SemiCat 分析 | 4/5 |
| 06 | [Evo²](https://arxiv.org/abs/2610.13025) · [评析](06-Evo2.md) · [PDF](2610.13025.pdf) | A Google DeepMind / 直接 | 权重—harness 协同进化 | 4/5 |
| 07 | [Latent Intrinsic Feedback](https://arxiv.org/abs/2610.13617) · [评析](07-UserSim-LatentFeedback.md) · [PDF](2610.13617.pdf) | A Google Research / 个性化相邻 | 带内在反馈状态的用户模拟器 | 4/5 |
| 08 | [X-AgentRed](https://arxiv.org/abs/2610.13886) · [评析](08-X-AgentRed.md) · [PDF](2610.13886.pdf) | A Meta / **弱相关但具启发性** | 跨服务个人代理红队 | 3/5 |
| 09 | [VEPA](https://arxiv.org/abs/2610.12813) · [评析](09-VEPA.md) · [PDF](2610.12813.pdf) | A Google DeepMind/Cloud / **弱相关但具启发性** | 可验证的长期规则演化 | 4/5 |
| 10 | [EvoBelief](https://arxiv.org/abs/2610.12789) · [评析](10-EvoBelief.md) · [PDF](2610.12789.pdf) | B Amazon + Tulane / 直接 | 可证伪的环境记忆 | 4/5 |
| 11 | [CoCoEvolve](https://arxiv.org/abs/2610.12794) · [评析](11-CoCoEvolve.md) · [PDF](2610.12794.pdf) | B Stanford/UC Berkeley/Snowflake 等 / 直接 | 全进化史元反思 | 4/5 |
| 12 | [LongHarness](https://arxiv.org/abs/2610.13075) · [评析](12-LongHarness.md) · [PDF](2610.13075.pdf) | B 上海 AI Lab/复旦等 / 直接 | 证据—结论共演化 | 4/5 |
| 13 | [RSI-Anything](https://arxiv.org/abs/2610.13912) · [评析](13-RSI-Anything.md) · [PDF](2610.13912.pdf) | B CUHK/Stanford 等 / 直接 | 世界模型辅助递归改进 | 3/5 |
| 14 | [Predictive-State Flows](https://arxiv.org/abs/2610.12898) · [评析](14-PSF.md) · [PDF](2610.12898.pdf) | B Georgia Tech / 直接 | 扩散先验与 token 解码分工 | 4/5 |
| 15 | [Seq-Drifting](https://arxiv.org/abs/2610.12879) · [评析](15-Seq-Drifting.md) · [PDF](2610.12879.pdf) | B USTC/Oxford 等 / 直接 | 一步并行生成的漂移场 | 3/5 |
| 16 | [EmbodiedCLBench](https://arxiv.org/abs/2610.13021) · [评析](16-EmbodiedCLBench.md) · [PDF](2610.13021.pdf) | B 北大/BIGAI / 直接 | 具身经验组合迁移基准 | 3/5 |
| 17 | [SynthSelf](https://arxiv.org/abs/2610.13113) · [评析](17-SynthSelf.md) · [PDF](2610.13113.pdf) | B KAIST/LG AI Research / 直接 | 小模型分布内自蒸馏 | 4/5 |
| 18 | [RegulaTutor](https://arxiv.org/abs/2610.13399) · [评析](18-RegulaTutor.md) · [PDF](2610.13399.pdf) | B HKUST/CUHK / 直接 | 有证据链的学习者画像 | 3/5 |
| 19 | [SEEDS](https://arxiv.org/abs/2610.12932) · [评析](19-SEEDS.md) · [PDF](2610.12932.pdf) | B NYU/NYU Shanghai / 相邻 | 检索后证据准入 | 4/5 |
| 20 | [DP-MIND](https://arxiv.org/abs/2610.13132) · [评析](20-DP-MIND.md) · [PDF](2610.13132.pdf) | B 浙江大学/蚂蚁等 / 直接 | DP 扰动下的分块记忆 | 3/5 |

### 机构分布

- **A：9 篇**，均有 PDF 首页可核验的用户点名机构参与：Meta 2、Alibaba 2、Google DeepMind/Cloud 2、Google Research 1、NVIDIA 1、Apple 1。联合高校不重复增加论文总数。
- **B：11 篇**，包括 Amazon 与强研究型高校/实验室的联合研究。它们排在 A 之后；这不是对证据可信度的贬值。无机构未核验论文，也未以低机构优先级稿件凑数。

### 主题趋势

1. **长期记忆从静态条目转向动态证据状态**：ReHarness、T-Mem、T²Mem、LongHarness、EvoBelief 分别强调反向修订、时间演变、按需构造、结论回写及可证伪规则。
2. **自进化对象扩大**：Evo²、CoCoEvolve、RSI-Anything 和 VEPA 不只优化单个回答，而是更新 harness、策略、世界模型或规则；外部反馈的可靠性与回滚机制因此更关键。
3. **并行语言生成出现不同路线**：Apple 的连续扩散设计分析、PSF 的预测状态分工、Seq-Drifting 的一步生成，仍须在统一训练/推理预算下比较。

### 当天最值得深读的 3 篇

1. **[ReHarness](01-ReHarness.md)**：与自进化代理记忆最直接，核心“反向修订”可立即转化为持久记忆的更新/回滚实验；3 基准与 3 backbone 提供较扎实起点。
2. **[T-Mem](02-T-Mem.md)**：明确解决多人长期对话中的状态更替与证据遗漏，适合研究时间结构对个性化记忆检索的作用及失败边界。
3. **[T²Mem](03-T2Mem.md)**：与预先摘要/静态记忆形成清晰对照，值得重点复现其查询时建记忆的质量—成本折中。

### 文件核验

20 份 PDF 均从 `https://arxiv.org/pdf/<编号>` 下载，已验证 `%PDF-` 文件头并能解析页数；逐篇笔记的机构来自 PDF 首页（RSI-Anything 由首页明确指向的附录 A 核验）。笔记区分“论文证据”和“我的推断”；本报告未进行独立实验复现。
