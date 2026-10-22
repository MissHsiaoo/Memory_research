# 2026-10-21 arXiv LLM Memory 日报

状态：20 篇评析与官方 PDF 已整理；本期使用 10 月 21 日批次，不混入旧论文或 replacements。报告整理跨到次日时仍归属于已核验的 10 月 21 日批次，不改挂为 10 月 22 日新论文。

## 批次与范围

北京时间 2026-10-21 11:34 左右抓取官方列表，cs、cs.CL、cs.AI、cs.LG、stat.ML 的页面公告标题为 **Wednesday, 21 October 2026**。按 New submissions 栏目解析并去重，共 876 条（含整个 cs 大类）；cs.CL/AI/LG/stat.ML 分别为107/133/134/16条，各分类会重叠，不能相加当唯一论文数。cross-lists 与 replacements 不作为新增论文池。

来源：[cs](https://arxiv.org/list/cs/new)、[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)、[stat.ML](https://arxiv.org/list/stat.ML/new)。动态链接未来会变化，本期快照保存在 sources/。官方[公告时间规则](https://info.arxiv.org/help/availability.html)中的周二美东20:00，在夏令时对应周三北京时间08:00；这是计划时间对应，不是本次实测发布时刻。首次提交日期逐篇取官方 abs 页，不以 PDF 边栏日期代替公告日期。

筛选先检查同批次标题/摘要，扩展到整个 cs 以覆盖机器人、多模态、系统与推荐；对48个候选尝试获取全文，最终收录20篇。机构以PDF首页为准。P1A为优先工业研究机构及强合作团队，P1B为一流研究型高校/实验室或强学术合作，P2为少量方法/评测启发突出的补充；这是本报告选读分层，不是客观大学排名。同层先直接相关，再考虑创新性与证据；保留4篇P1A相邻方向，不因不是纯记忆方法而忽略它们。Google Cloud不混写为DeepMind，Ant International不自动混写为Alibaba，独立作者不因邮箱归入高校。

## 入选目录（机构优先级 → 直接相关性 → novelty）

| 排名 | 论文/笔记 | 机构层级 | 首页机构 | 相关性 | 证据分 |
|---|---|---|---|---|---|
| 1 | [RSD](01-RSD.md) | P1A | Meta AI | 直接相关 | 4/5 |
| 2 | [Industrial-ReMEmbR](02-Industrial-ReMEmbR.md) | P1A | NVIDIA；Idealworks | 直接相关 | 4/5 |
| 3 | [REM](03-REM.md) | P1A | Yale University；Amazon | 直接相关 | 4/5 |
| 4 | [Anti-Persistence](04-Anti-Persistence.md) | P1A | Indiana University；Tencent HY | 直接相关 | 4/5 |
| 5 | [GRSE](05-GRSE.md) | P1A | Alibaba Token Hub（Alibaba）；Mayo Clinic；University of Manchester；Shanghai University of Finance and Economics | 直接相关 | 4/5 |
| 6 | [Lafa](06-Lafa.md) | P1A | UC Berkeley；Amazon；KAIST；Carnegie Mellon University | 直接相关 | 4/5 |
| 7 | [TURTLE](07-TURTLE.md) | P1A | Google DeepMind；Stanford University；University of Washington | 弱相关但具启发性 | 3/5 |
| 8 | [OO-Harness](08-OO-Harness.md) | P1A | Google Cloud AI Research；University of Illinois Urbana-Champaign | 弱相关但具启发性 | 4/5 |
| 9 | [RiseHarness](09-RiseHarness.md) | P1A | Tencent HY LLM Frontier；Indiana University；University of Maryland College Park；University of Georgia；National University of Singapore | 弱相关但具启发性 | 4/5 |
| 10 | [GRADUS](10-GRADUS.md) | P1A | AWS AI；University of Southern California；BMW Group Research and Technology | 弱相关但具启发性 | 4/5 |
| 11 | [Factual-Access-States](11-Factual-Access-States.md) | P1B | The University of Tokyo；LIGHTSPEED；Independent Researcher | 直接相关 | 4/5 |
| 12 | [PAR](12-PAR.md) | P1B | Ant International；National University of Singapore | 直接相关 | 4/5 |
| 13 | [LAMB](13-LAMB.md) | P1B | Xiamen University；MBZUAI | 直接相关 | 4/5 |
| 14 | [Memory-as-Code](14-Memory-as-Code.md) | P1B | Shanghai Jiao Tong University；University of New South Wales；The Chinese University of Hong Kong Shenzhen | 直接相关 | 4/5 |
| 15 | [OptionWorld](15-OptionWorld.md) | P1B | University of British Columbia；University of Chicago；Princeton University；Independent Researcher | 直接相关 | 4/5 |
| 16 | [ProMemAgent](16-ProMemAgent.md) | P1B | Columbia University | 直接相关 | 4/5 |
| 17 | [AKV](17-AKV.md) | P1B | Tsinghua University；The Chinese University of Hong Kong | 直接相关 | 4/5 |
| 18 | [DuplexLedger](18-DuplexLedger.md) | P1B | Nanyang Technological University；Peking University；Beijing University of Technology；Xidian University；University of Melbourne；China Aerospace Science and Industry Corporation | 直接相关 | 4/5 |
| 19 | [FENCE](19-FENCE.md) | P1B | University of Illinois Urbana-Champaign；Northeastern University | 直接相关 | 4/5 |
| 20 | [MemDev-Bench](20-MemDev-Bench.md) | P2补充 | Southeast University；Southern University of Science and Technology；MemoraX AI | 直接相关 | 4/5 |

## 当天最值得深读的 3 篇

1. **RSD**：Meta 的经验到参数巩固路径；最值得看 SearchQA 的内化失败边界，以及强模型引导扩展究竟增加了什么监督。
2. **REM**：Yale/Amazon 的读取时机与一次曝光后驱逐；适合直接设计“检索正确但使用有害”的对照实验。
3. **Industrial ReMEmbR**：NVIDIA/Idealworks 的同一潜在记忆服务检索、解释、地图和回放；对多用途记忆尤其有启发，注意成本外推假设。

若重点是“多目标记忆使用 benchmark”，优先深读 **OptionWorld**（多目标、期限、权限与行动闭环）、**CPMBench/ProMemAgent**（多意图及主动触发）、**DuplexLedger**（写入/更新/忽略/保留与实时响应的权衡）。这些分别覆盖多目标的一部分，不应称为统一的多目标优化基准。

## 机构分布

按篇、可重叠计数：Meta 1，NVIDIA 1，Amazon/AWS合计3，Google DeepMind 1，Google Cloud 1，Tencent HY 2，Alibaba Token Hub 1；以上对应10篇P1A。另有LIGHTSPEED署名与东京大学合作1篇，保留原始名称，不将其自动并入Tencent HY计数。P1B共9篇、P2补充1篇。高校合作覆盖Yale、Stanford、Berkeley、CMU、KAIST、UIUC、USC、Princeton、Columbia、NUS、清华、北大、上交、港中大及其深圳校区、UNSW、NTU、墨尔本、厦大、MBZUAI等；完整机构以逐篇表格为准。此次未用‘机构未核验’候选凑数。

## 主题趋势与批判性观察

- **记忆不是越多越好**：REM、Anti-Persistence和MemDev分别从注入时机、抽象反馈和历史误用分析负收益。应同时报告Rescue和Harm。
- **记得不等于会做**：OptionWorld把事实可见与行动完成分开；ProMemAgent强调未来触发和意图去激活；DuplexLedger强调合法的更新与拒绝。
- **记忆形态走向可执行/潜在状态**：MaC是代码接口，LAMB是多假设隐状态，PAR是稳定递归，AKV是活跃缓存操作；它们的‘记忆’对象不同，不能直接比较一个总分。
- **经验可以巩固到权重，也可以演化成程序**：RSD、OO-Harness、RiseHarness、GRADUS体现不同路线。控制强模型提案、搜索和额外测试成本，是比较这些方法的前提。
- **安全目标不能省略**：FENCE说明不持久化的用户边界；缓存drop和压缩视频都不自动构成真正遗忘或隐私保证。
- **避免相对数掩盖绝对能力**：DuplexLedger最新值准确率翻倍后仍仅8.68%；知识编辑自由生成多数仍错；PAR大模型方差很大。

## 候选取舍与证据边界

本期达到20篇目标。完整同批次候选清单见 sources/catalog.json；仅列出标题/摘要不代表已全文阅读或机构已核验。深入候选中，AtomSD、SPEM、MPlan、TeCoP、DStill、SDDC、AsymLoop、SAPD、TraceLite、ICLHerd、MMEnterprise-Bench、MIT3、ClawMMU及Disclosure Begets Disclosure等因本期名额、机构层级、主题重复或证据成熟度未列入正式20篇，不意味着质量差。两篇独立研究者关于compaction/驾驶记忆的对照研究未因高校邮箱升级机构优先级。Tactile-ETA、EventSync及continual concept diffusion的候选PDF初次下载超时，未用摘要代替全文评析；Industrial ReMEmbR重试成功后入选。

机构质量与可信度分开评估；20篇均获取可解析完整PDF并核验首页，逐篇标注重点阅读页/节。未声称逐字读完所有附录，也未运行复现实验。4分是当前证据的有限支持，不等于已同行评审或可部署。本期无只读摘要的正式入选文章。

## 文件交付核验

- 20篇中文六项评析，20份官方PDF；本地链接使用 pdfs/ 相对路径，适配GitHub。
- verification.json记录arXiv ID、首投日期、公告来源、页数、字节数和SHA-256。
- 官方列表与abs页快照保存于sources/；PDF以实际文件同步，不只保留外链。
- 仅增量添加本期目录并更新仓库根日期索引，不改写其他日期。
