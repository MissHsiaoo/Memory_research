# 2026-09-28 arXiv LLM Memory 日报

状态：**complete**。共入选 **20 篇**；20 个官方 PDF 均已下载到本目录、通过 `%PDF-` 与 `pdfinfo` 结构校验，并阅读可提取全文及核验论文首页机构署名。

## 批次口径

- 北京时间 2026-09-28 11:00（UTC 03:00）核验时，cs.CL、cs.AI、cs.LG 官方 `new` 页面均已切换为 **Monday, 28 September 2026**。
- 官方入口：[cs.CL new](https://arxiv.org/list/cs.CL/new)（61 个 new submissions）、[cs.AI new](https://arxiv.org/list/cs.AI/new)（88 个）、[cs.LG new](https://arxiv.org/list/cs.LG/new)（123 个）。三页合并去重后共审阅 404 个 new/cross-list 候选；排除 replacement-only 旧稿。
- 正式公告日与提交日分开记录。个别新公告论文的首次提交早于 9 月 25 日（例如 Spotify 论文为 9 月 16 日、HiCoMER 为 9 月 9 日），但它们确属 9 月 28 日官方 new/cross-list 批次，不用提交日期替代公告日期。
- 本日报告没有扩展到近 30 天，也没有用 9 月 25 日旧批次凑数。

## 入选论文（机构优先级 → 直接相关性 → novelty）

1. [KuaFu](./01-KuaFu.md) — **Tencent｜直接相关**：十亿用户、item-level 双轴 latent compression，把个性化历史变成可缓存可追加的生产记忆层。
2. [AutoResearch at Production Scale](./02-AutoResearch.md) — **Amazon｜直接相关**：十二周、220+ 生产实验，揭示自进化代理的记忆衰减和搜索治理问题。
3. [SkillEvoReg](./03-SkillEvoReg.md) — **Huawei Noah’s Ark Lab｜直接相关**：用 dropout、复杂度正则和因果反例抑制 skill memory 过拟合。
4. [Game Arena](./04-Game-Arena.md) — **Google DeepMind/Kaggle/Google Cloud｜弱相关但高启发性**：动态竞争式 agent evaluation 基础设施。
5. [Audio LLMs Know When They Can't Hear You](./05-Audio-LLM-Reliability.md) — **Apple + UCSD｜弱相关但具 latent-state 启发**：内部可靠性信号可充当 memory 写入门。
6. [PISA](./06-PISA.md) — **ByteDance Seed + SJTU｜紧密相关基础设施**：O(N log N) 层级块选择扩展长上下文读取。
7. [Evaluating KV Cache Reuse](./07-KV-Cache-Reuse.md) — **Huawei + ETH Zurich｜紧密相关**：揭示 cache/memory reuse 评测虚高并提出 Boxoffice。
8. [Code-Based Skills for Language Agents](./08-CodeHack.md) — **Princeton + Mistral AI + UCL/Mila 等｜直接相关**：程序性 skill memory 显著提升长程行动与学习效率。
9. [Spotify Conversational Recommendation Agent](./09-Spotify-Agent.md) — **Spotify｜直接相关**：合成多轮数据、自改进循环和 1500 万用户 A/B。
10. [Belief Self-Distillation](./10-BSD-User-Model.md) — **TUM + Helmholtz｜直接相关**：可读可写的 latent user model，连接个性化与安全。
11. [LOHA + ACD](./11-LOHA-ACD.md) — **Peking University｜直接相关**：旧观察 soft-token 化、近期动作保真，并以 anchor 抑制行为漂移。
12. [New LoRA Skills Should Read but Never Write](./12-READ-LoRA-Skills.md) — **SJTU + HKUST(GZ) 等｜直接相关**：用单向耦合保护持续加入的参数化技能。
13. [Q-Target Pretrained Transformers](./13-QTPT.md) — **SJTU + Alibaba｜直接相关**：以 Bellman Q-target 替代对弱上下文轨迹的盲目模仿。
14. [HiCoMER](./14-HiCoMER.md) — **NTU + Zhejiang + WPI｜直接相关**：团队/个人分层记忆与有效性优先检索。
15. [HasMem](./15-HasMem.md) — **HKUST + Bristol｜直接相关**：从 hard token origin 渐进软化的可变宽度连续记忆。
16. [AtomWorld-Mem](./16-AtomWorld-Mem.md) — **Tsinghua AIR + PKU + CAS｜弱相关但具方法启发**：以短/长期记忆恢复 observation 中缺失的 latent world state。
17. [Evolutionary Safety](./17-Evolutionary-Safety.md) — **CAS｜直接相关**：把持久记忆污染、评估器漂移和风险继承纳入递归自改进治理。
18. [Diffusion LLM Jailbreaks](./18-Diffusion-Jailbreaks.md) — **Deakin A2I2 + Penn State｜直接相关**：从完整去噪轨迹的能量信号解释并检测攻击。
19. [Epistemic Admission in Shared Agent Memory](./19-Shared-Memory-Admission.md) — **NJU/UNSW/Facebook 等｜黑马补充、直接相关**：来源谱系比重复共识更重要。
20. [Nonparametric ICL under Growing Geometry](./20-Nonparametric-ICL.md) — **Seoul National University｜直接相关理论**：局部 manifold 自适应 ICL 的匹配 minimax 上下界。

## 机构分布

- 指定重点工业研究机构：Tencent、Amazon、Huawei Noah’s Ark、Google DeepMind、Apple、ByteDance Seed、Alibaba，以及一流工业团队 Spotify、Mistral AI。
- 全球一流高校/实验室：Princeton、Peking University、TUM/Helmholtz、ETH Zurich、SJTU、HKUST、Tsinghua AIR、CAS、NTU、Zhejiang、SNU、Penn State 等。
- 仅第 19 篇作为明确的“黑马/启发性补充”；其机构层级混合，但问题定义和 live shared-memory 证据非常直接。其余名额没有用一般机构论文凑数。

## 主题趋势

1. **个性化记忆走向可写 latent state**：KuaFu 将行为项压成生产 embedding；BSD 进一步证明模型对用户的信念可以读出和因果写回。
2. **self-evolution 的核心变成写入治理**：AutoResearch、SkillEvoReg、READ 分别从运行日志、外部 skill 和参数 adapter 处理积累、回归与干扰。
3. **记忆质量优先于语义相似度**：HiCoMER 管“是否仍有效”，CPB 管“来源是否独立”，二者都否定 flat top-k 足以治理长期记忆。
4. **hard/soft memory 开始混合**：LOHA 保留近期精确文本，HasMem 从 hard origin 渐进软化；两者都显示压缩率与行为 fidelity 不能由单一指标代表。
5. **过程 latent signal 可做 controller**：Audio LLM 的 encoder reliability 和 diffusion LLM 的 denoising energy 都比最终自我报告包含更早的失败信号。
6. **基础设施评测更严格**：PISA 降低长上下文路由复杂度，KV cache 审计则提醒“更快”必须在真正需要上下文的样本上测 fidelity。

## 最值得深读的 3 篇

1. **KuaFu**：今天最强的 personalization 工业证据；从表示单元、训练、幻觉治理到十亿用户成本闭环完整。
2. **AutoResearch at Production Scale**：最接近真实 self-evolving agent 的长期运行记录，尤其值得看 memory decay 与 persist/redirect 设计。
3. **Belief Self-Distillation**：最有潜力的新研究方向；把“用户画像”从文本档案变成可读写、可因果验证的内部状态，同时暴露安全风险。

若偏 agent memory 工程，建议继续深读 **HiCoMER + HasMem + LOHA**；若偏 diffusion LLM，则优先第 18 篇。

## 核验日志

- 08:01：三个官方 `new` 列表均仍停留在 2026-09-25；9 月 28 日批次尚未发布。
- 09:01：再次核验 cs.CL、cs.AI、cs.LG，三个列表仍显示 2026-09-25；状态无变化，继续等待。
- 10:00：再次核验 cs.CL、cs.AI、cs.LG，三个列表仍显示 2026-09-25；状态无变化，继续等待。
- 11:00：三个官方 `new` 列表均切换到 2026-09-28；开始合并候选、机构核验、全文提取与排序。
- 交付核验：20 个 PDF 共 486 页，全部通过文件头与 `pdfinfo` 校验；20 个中文评析均含规定的六项。临时每小时续跑结束，自动任务恢复每天北京时间 08:00。
