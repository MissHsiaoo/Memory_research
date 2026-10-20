# arXiv LLM Memory — 2026-10-20（北京时间）

## 批次核验与范围

本报告覆盖 arXiv 官方列表标注为 **Monday, 19 October 2026** 的 `cs.CL`、`cs.AI`、`cs.LG` 与 `stat.ML` **New submissions**；该公告批次对应北京时间 **2026-10-20**。官方页计数分别为 104、92、126、15 条新投稿。公告批次日期与每篇论文自己的 v1 提交日期分开记录。只纳入这些官方 New submissions 中直接相关或有明确方法启发的新作；旧论文的替换版本和仅在其他学科的 cross-list 区不算入。已逐篇保存并检查 12 份官方 PDF（均可解析，页数见文件名对应论文笔记）；作者机构以 PDF 首页署名为准。

**筛选结果：12 篇。** 少于目标 20 篇：已穷尽当天清单中与记忆、个性化、长期智能体、ICL、扩散 LLM 有直接关系或明确跨方向启发的强机构/高校候选；其余仅因标题或摘要宽泛提及 agent/LLM 而未纳入，避免凑数。此批候选里没有 20 篇同时满足范围与证据标准的工作。

## 入选排序

排序先按论文首页可核验的机构质量，再按直接相关性、方法新颖性和证据力度；“弱相关但具启发性”已明示。机构优先级与证据可信度是两项独立判断。

| 排名 | 论文 | 机构优先级 / 机构核验 | 相关性 | 可信度 |
|---|---|---|---|---|
| 1 | [ProPerAgent: Toward Memory-Driven Proactive Assistance](https://arxiv.org/abs/2610.22671) | P1：Meta Reality Labs / Meta Superintelligence Labs；PDF 首页核验 | 直接：个人长期记忆、主动干预 benchmark | 4/5 |
| 2 | [Multimodal Filesystem Memory For Long-Horizon Embodied Agents](https://arxiv.org/abs/2610.22686) | P1：Harvard/Kempner、MIT、NYU、UIUC 等；PDF 首页核验 | 直接：具身多模态长期记忆 | 4/5 |
| 3 | [RL-Guided Temporal Localization for Dual-Channel Retrieval in Long-Horizon Agent Memory](https://arxiv.org/abs/2610.23598) | P1：清华大学、Qiyuan Lab；PDF 首页核验 | 直接：时间感知长期记忆检索 | 4/5 |
| 4 | [From Relevant Memories to Sufficient Evidence: Rethinking Memory Utilization in LLM Agents](https://arxiv.org/abs/2610.22668) | P1：USC、Georgia Tech；PDF 首页核验 | 直接：多粒度记忆到可追溯证据集 | 4/5 |
| 5 | [Learning Personalized Memory Gating from Delayed One-Sided Feedback](https://arxiv.org/abs/2610.23812) | P1：Salesforce AI Research、UCLA、UIUC、UIC；PDF 首页核验 | 直接：个性化事实保留/门控 | 4/5 |
| 6 | [MARS: Memory-Aware Routing for Session-Level LLM Assistants](https://arxiv.org/abs/2610.23583) | P1：SUSTech、CityU HK、CUHK-Shenzhen、HIT Shenzhen；PDF 首页核验 | 直接：记忆构造与模型路由联合决策 | 4/5 |
| 7 | [ECHOES: Seeing Beyond the Current Image via Recursive History Compression and Privileged On-Policy Distillation](https://arxiv.org/abs/2610.22408) | P1：清华、南洋理工；P2：StepFun 等；PDF 首页核验 | 直接：GUI 历史压缩与状态记忆 | 3.5/5 |
| 8 | [When to Forget: Risk-Controlled Context Adaptation for Long-Horizon Agents](https://arxiv.org/abs/2610.22897) | P1：UCLA、上海交大、ASU、东方理工；PDF 首页核验 | 直接：长期轨迹何时保留/压缩/删除 | 3.5/5 |
| 9 | [Darwin-Claw: Environment-Adaptive Experience Consolidation for Recursively Self-Evolving Agents](https://arxiv.org/abs/2610.23574) | P1：Tencent、浙江大学、中关村学院；PDF 首页核验 | 直接：经验巩固、自进化记忆与技能 | 3/5 |
| 10 | [Rethinking User Encoders: Routing Diffusion States for Scenario-Adaptive User Representation](https://arxiv.org/abs/2610.22400) | P1：蚂蚁集团、浙江大学；PDF 首页核验 | 相关：dLLM 用户表征/个性化，不是显式记忆库 | 3.5/5 |
| 11 | [On the SPOT: Enhancing Speculative Decoding for Diffusion Language Models via Commit-Order Prediction](https://arxiv.org/abs/2610.22543) | P1：Technion、Ben-Gurion University；PDF 首页核验 | 弱相关但具启发性：扩散 LLM 推理加速 | 4/5 |
| 12 | [Agentic In-Context Learning: What Algorithms Can Transformers Learn in Closed-Loop Interaction?](https://arxiv.org/abs/2610.23051) | P1：清华大学、北京数学科学研究中心；PDF 首页核验 | 弱相关但具启发性：闭环交互 ICL 理论 | 4/5 |

## 机构分布

- 大型产业研究团队：Meta（1）、Salesforce（1）、Tencent（1）、蚂蚁集团（1）、StepFun（1，和高校合作）。
- 高校/研究机构署名：Harvard/Kempner、MIT、NYU、UIUC、USC、Georgia Tech、清华、南洋理工、Technion、Ben-Gurion、SUSTech、CityU HK、CUHK-Shenzhen、HIT Shenzhen、UCLA、上海交大、ASU、东方理工、浙江大学、UIC、中关村学院等。多篇论文为多机构合作，故机构数不互斥。
- MARS 和其余机构均在 PDF 首页核验；没有把无法核验的作者单位猜作知名机构。

## 主题趋势

1. **记忆“使用”比单纯存取更受关注**：主动助理要同时选“何时说、说什么”；问答代理要把零散记忆组织成完整证据；VLA 的记忆评测要区分行为受影响与真正使用了相关事实。
2. **控制面开始统筹记忆构造、检索与回答成本**：状态门控、个性化保留策略、模型路由及按执行阶段遗忘，目标从最大化召回转为效用/风险/成本联合管理。
3. **长期记忆不再局限于文本**：具身 agent 保留原始视觉经历、空间线索与可复用技能；GUI agent 研究将视觉历史压缩成文本状态；扩散模型也被尝试用于用户表征。
4. **评测正在向更难的因果或时序问题拓展**：长达约一年的个人历史、跨会话证据合成、时序窗口定位与风险受控干预，都比静态 top-k 回忆更贴近长期部署。

## 当天最值得深读的 3 篇

1. **ProPerAgent / ProPerMem**：把记忆检索、主动打断时机、内容正确性和“应该沉默”的负例放入同一 benchmark；其 oracle 因子实验清楚分解内容和时机两种瓶颈，最适合作为新型 memory benchmark 的设计参考。
2. **MFM**：统一保留多模态原始经历、空间索引、语义/程序性知识和工作记忆，并保留证据指针，直接面向具身任务的长期经验复用；值得检查其对真实环境漂移、存储开销与写入错误的鲁棒性。
3. **QEMem**：把记忆利用从“检索相似项”改写成“构造可追溯且足够的证据集合”，特别适合研究多跳/跨会话个性化问答以及可靠性评测；需要重点复核其 LLM judge 与检索反馈的偏差。

## 文件

每篇中文评析按入选排名命名；对应 PDF 文件名为 arXiv ID。笔记中提交日期、PDF 首页机构、直接论文证据与我的推断分开写，并含六项批判性阅读与独立可信度评分。
