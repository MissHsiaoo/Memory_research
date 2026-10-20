# 2026-10-14 arXiv LLM Memory 日报

- 核验时间：2026-10-14 08:00（北京时间，Asia/Shanghai；对应 UTC 2026-10-14 00:00）。
- 08:00 时状态为 **pending**：[cs.CL 官方 new 列表](https://arxiv.org/list/cs.CL/new)、[cs.AI 官方 new 列表](https://arxiv.org/list/cs.AI/new)、[cs.LG 官方 new 列表](https://arxiv.org/list/cs.LG/new) 当时均显示“Showing new listings for Monday, 12 October 2026”。以下增量核验记录保留这一过程，不代表最终状态。
- **最终状态：已交付。**北京时间约 15:04（UTC 约 07:04）起，上述三类官方 `new` 页面均显示 **“Showing new listings for Wednesday, 14 October 2026”**，即本日报告对应的北京时间 2026-10-14 正式公告批次。只取页面中的 *New submissions* 段；不取交叉列表、替换版本，也不以初次提交日期替代公告日期。
- 筛选范围：cs.CL 244、cs.AI 360、cs.LG 502，合计 **1106 条不重复新提交**；按主题初筛、机构首页署名核验、PDF 方法/实验/局限检查后入选 **20 篇**。这不是用旧论文凑够目标数；其中若初次提交早于 10 月 14 日，仍以其确实进入当天官方 *New submissions* 的证据为准。
- 20 份官方 PDF 已下载并经文件头、页数和正文可提取性检查；逐篇中文笔记标出“论文证据”与“我的推断”。机构优先级与证据可信度独立，不因公司/学校知名就给高分。

## 增量核验

- 2026-10-14 08:58（北京时间）：cs.CL、cs.AI、cs.LG 官方 new 列表均仍显示 2026-10-12 正式批次；今日继续 pending，未纳入旧论文。
- 2026-10-14 09:55（北京时间）：上述三个官方 new 列表仍均显示 2026-10-12；10 月 14 日正式新批次尚不可见，继续 pending。
- 2026-10-14 11:05（北京时间）：cs.CL、cs.AI、cs.LG 官方 new 列表均仍显示 2026-10-12；继续 pending，不把旧批次记为今日。
- 2026-10-14 12:05（北京时间）：三类官方 new 列表仍均显示 2026-10-12 正式批次；今日状态维持 pending。
- 2026-10-14 13:04（北京时间）：cs.CL、cs.AI、cs.LG 官方 new 列表均仍显示 2026-10-12；10 月 14 日正式批次尚不可见，维持 pending。
- 2026-10-14 14:03（北京时间）：三类官方 new 列表仍均显示 2026-10-12 正式公告批次；继续 pending。
- 2026-10-14 15:04 左右（北京时间）：三类官方 new 列表切换为 Wednesday, 14 October 2026；正式批次可见，开始仅筛 *New submissions*。

## 入选论文（机构优先级 → 直接相关性 → 方法新颖性）

排序先看 PDF 首页或其他可核验署名的机构层级，再在同层级比较主题直接性、原创性、方法严谨性和潜在影响。A 表示目标产业机构或一流/高水平研究型高校合作；本批无须从较低机构优先级纳入“黑马”补充。机构标签**不是**可信度评分。部分同属 A 的论文因方向相邻而注明“弱相关但具启发性”。下表的 PDF 均为本地有效文件；论文详情含作者、初次提交日与六项评析。

| 排名 | 论文与逐篇评析 | 机构/优先级 | 主题与入选理由 | 可信度 |
|---:|---|---|---|---:|
| 1 | [Many Steps into One](01-记忆复用的过时风险.md) · [arXiv](https://arxiv.org/abs/2610.17544) | ByteDance、Scale AI；A | 直接相关：记忆复用的过时安全边界；有受控事实/代码编辑 | 4/5 |
| 2 | [Drafting Agents, Not Just Tokens](02-推测式智能体自进化.md) · [arXiv](https://arxiv.org/abs/2610.16491) | Tencent AMS/Hunyuan、北大；A | 相邻方向：自进化候选的并行验证；对记忆写入准入有启发 | 3/5 |
| 3 | [Predict Before You Modify](03-预测改进动态.md) · [arXiv](https://arxiv.org/abs/2610.13991) | Microsoft Research、清华、UVA；A | 相邻方向：预测自改进效果，过程记忆的元模型 | 3/5 |
| 4 | [Can Agents Forget When Asked?](04-智能体按请求遗忘.md) · [arXiv](https://arxiv.org/abs/2610.18052) | 清华、Sina Weibo；A | 直接相关：记忆定向遗忘与隐私评测 | 4/5 |
| 5 | [Online LLM Personalization](05-成对偏好在线个性化.md) · [arXiv](https://arxiv.org/abs/2610.17203) | MIT；A | 直接相关：跨用户成对反馈、在线偏好更新 | 3/5 |
| 6 | [VitaBench](06-记忆生命周期基准.md) · [arXiv](https://arxiv.org/abs/2610.14731) | 港大、港中文、Cornell；A | 直接相关：保留/压缩/删除的长期反事实 | 3/5 |
| 7 | [Reliable Memory from Unstable Growth](07-随机实验筛选智能体手册.md) · [arXiv](https://arxiv.org/abs/2610.18427) | 南洋理工、VinUniversity；A | 直接相关：随机实验筛选自写经验块 | 4/5 |
| 8 | [Self-Evolving Agent Harness](08-自进化智能体框架.md) · [arXiv](https://arxiv.org/abs/2610.18813) | Zhongguancun Academy/Institute of AI、中科大；A | **弱相关但具启发性**：自改进更新准入的框架 | 2/5 |
| 9 | [Recall What Is Missing](09-从记忆中补全证据.md) · [arXiv](https://arxiv.org/abs/2610.15642) | 港中文（深圳）；A | 直接相关：记忆互补证据检索 | 3/5 |
| 10 | [GateSight](10-混合模型KV记忆淘汰.md) · [arXiv](https://arxiv.org/abs/2610.14754) | 上海交大；A | 直接相关：循环状态指导 KV 记忆淘汰 | 3/5 |
| 11 | [Revisiting the 16x Compute Gap](11-扩散语言模型预训练算力差距.md) · [arXiv](https://arxiv.org/abs/2610.17590) | Cornell/Cornell Tech、Amazon；A | 直接相关：diffusion LLM 训练效率的系统复核 | 4/5 |
| 12 | [Match the Canvas, Not Just the Answer](12-扩散模型可预测画布.md) · [arXiv](https://arxiv.org/abs/2610.18001) | Georgia Tech、伯克利、芝加哥、密歇根；A | 直接相关：扩散式生成的可预测画布监督 | 3/5 |
| 13 | [Prefilling-dLLM v2](13-长上下文扩散模型分块路由.md) · [arXiv](https://arxiv.org/abs/2610.17868) | 港大、浙大；A | 直接相关：长上下文扩散模型路由 | 3/5 |
| 14 | [Memory Echo](14-记忆回声与来源纠错.md) · [arXiv](https://arxiv.org/abs/2610.17763) | 华东师大、USC、浙大、浙工商；A | 直接相关：来源追踪、错误记忆传播与纠错 | 3/5 |
| 15 | [LatentRemedy](15-非前缀KV复用补救.md) · [arXiv](https://arxiv.org/abs/2610.18014) | 港科大（广州）、Microsoft、港大；A | 直接相关：多 agent 非前缀 KV 复用失配 | 3/5 |
| 16 | [AReaL-RSI](16-自进化团队记忆共享.md) · [arXiv](https://arxiv.org/abs/2610.18083) | 蚂蚁集团、浙大、港科大；A | 相邻方向：自进化团队条件共享记忆 | 3/5 |
| 17 | [A Few More Tokens Ahead](17-扩散语言模型并行强化.md) · [arXiv](https://arxiv.org/abs/2610.18200) | 华东师大、复旦；A | 直接相关：扩散 LLM 并行能力强化 | 3/5 |
| 18 | [PersonaFactor](18-偏好因子动态选择.md) · [arXiv](https://arxiv.org/abs/2610.16372) | 华东师大、中关村研究院、人大、东南；A | 直接相关：结构化偏好因子与动态选择 | 3/5 |
| 19 | [Factorized Skill Memory](19-持续技能内化记忆.md) · [arXiv](https://arxiv.org/abs/2610.15492) | 哈工大（深圳）、Great Bay University、浙大；A | 直接相关：持续技能的寻址/执行分离 | 3/5 |
| 20 | [Activation Steering as Memory](20-激活向量作为记忆.md) · [arXiv](https://arxiv.org/abs/2610.14958) | TU Delft；A | 直接相关：latent memory 的事实保真负面结果 | 3/5 |

## 机构分布与主题趋势

- **机构优先级：**A 级 20 篇；无较低机构优先级“黑马”补充，也没有把机构无法核验的论文按名气猜测纳入。以上层级属于本日报告的排序标记，并非机构客观排名。按论文是否有该类机构参与计，产业机构合作 7/20，高校/研究院参与 19/20；合作论文重复计入两类。
- **研究主题（主标签互斥计数）：**agent/长期记忆与个性化 12 篇（#1、4–7、9–10、14–15、18–20）；自进化 agent 与过程记忆 4 篇（#2–3、8、16）；diffusion LLM 4 篇（#11–13、17）。
- **趋势判断（我的归纳）：**今天最值得跟踪的交叉点是记忆安全生命周期（过时、遗忘、错误传播）与可验证写入；另一条线是将偏好/经验转为可选择的结构化对象。扩散 LLM 工作则集中于训练和长上下文并行效率，不能因同日出现就推断已解决 agent 记忆。

## 今日最值得深读的 3 篇

1. [#1 记忆复用的过时风险](01-记忆复用的过时风险.md)：最直接回应“何时可以安全复用记忆”，跨事实编辑与代码改动，且把失败率而非命中率作为核心指标。
2. [#4 智能体按请求遗忘](04-智能体按请求遗忘.md)：将删除要求变为端到端可测行为；合成数据的局限也清楚，适合制定真实系统测试计划。
3. [#7 随机实验筛选智能体手册](07-随机实验筛选智能体手册.md)：用随机化检验自写记忆块的边际价值，为防止经验污染提供可操作方法，但需仔细评估练习成本。

## 核验边界

- 所有数字都是论文作者在各自设置中的报告，不表示本报告做了独立复现。逐篇“可信度”是对论文证据的判断，不是机构排名。
- #3 的 arXiv 页面/PDF 显示初次提交为 2026-09-26，与 `2610` 编号的月份表面不一致；已原样标记为元数据异常，不猜测原因。当天入选证据是 cs.LG 官方 `New submissions` 中的对应条目。
- 来源：arXiv 官方当天 [cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new) 的 *New submissions* 区段及各论文官方 PDF 首页和正文。`new` 页面会随公告批次更新；逐篇 arXiv 编号、提交日期和本地 PDF 保留了可复核线索。
