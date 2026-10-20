# 02. RAFT: A Stateful Retrieval-Augmented Framework for Troubleshooting Agents

- arXiv：[论文页面](https://arxiv.org/abs/2609.20754v1)｜[官方 PDF](https://arxiv.org/pdf/2609.20754v1)｜[本地 PDF](papers/02-RAFT-stateful-retrieval-2609.20754.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Mingxuan Zhang , Xiaowen Wang , Anupma Sharan , Zhengyi Chen , Chenyu Diana Zhang , Shanshan Yang , Chittibabu Pacharu
- 机构：Microsoft（论文首页署名 Redmond；不额外推定为 Microsoft Research）。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜优先公司，直接相关
- 研究标签：agent memory；retrieval-memory；状态化经验检索
- 入选理由：Microsoft 把历史工单作为状态轨迹而非静态文档，直接启发 agent episodic memory 的组织与召回单位。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

RAFT 将已解决的历史故障工单抽象成有向时间线，把每个中间阶段作为可检索条目。当前故障可以匹配历史案例的中间状态，再返回带匹配锚点的父案例轨迹，而不是仅根据整篇工单主题相似度召回。这里的 RAFT 是 Troubleshooting 框架，不应与同缩写的其他训练方法混淆。

## 2. 怎么做，实验如何设计

框架使用 LLM worker/reviewer 提取事件与状态，保留 actionability 标记；条目级 embedding 与 BM25 混合检索，通过 RRF 融合并提升为去重父案例，最多 5 个案例、约 6,000 token 预算。案例之间的 root-cause/resolution 图连接是可选项，不要误写成全部主要结果都依赖图。合成集由 Microsoft Learn Windows Server 文档构建 826 个案例；五次随机划分，每个根因组选一案例做测试，其余入索引，以当前工单 0%/30%/60% 进度查询。另在 30 组人工审计 Apache Jira 重复工单与 570 个干扰案例上验证。

## 3. 结论

合成集 Case Hit 为 84.2%/87.1%/88.8%，普通 RAG 为 67.3%/71.9%/76.9%；但 Root Cause Coverage 的差距小得多，分别 64.9/67.5/68.9 对 59.7/62.5/67.2。Jira Case Hit 为 83.3/84.0/89.5，对照 66.7/66.7/78.9。直接证据支持检索层改善，不能由此宣称生产环境中故障解决率、解决时间或端到端 agent 成功率已有同等增益。

## 4. 未来影响

我的推断：经验记忆应该保存“到达当前状态的路径”和适用前提，召回单位可以是轨迹片段，输出单位则是完整可解释案例。对 self-evolving agent memory，失败发生在哪一步可能比失败任务的主题更有检索价值。也可迁移到用户偏好形成过程，避免只保存最终静态标签。

## 5. Critical thinking

关键假设是状态摘要足够忠实，且相似中间状态对应可迁移的解决路径。合成工单和 LLM 判分可能共享生成偏差；Jira 的 duplicate 标签也不覆盖所有有帮助但非重复的案例。合成样本都具备可行动内容，因此 actionability 过滤在该实验中的独立收益不清楚。建议加入反事实状态、同主题不同根因、已失效修复方案等 hard negatives，并做同 token/索引成本的状态粒度消融。真正的下一步应是盲测修复动作正确性与危险建议率，而不只提高 Case Hit。

## 6. 可信度判断

可信度 4/5：已核对全文方法、合成与真实数据设计，并视觉核验 PDF 第 7 页表 2–4。优点是明确评估检索层、不冒充生产部署，拥有真实人类 duplicate 标签的方向性验证。局限是主体仍是合成数据、真实集较小、抽取及判分依赖 LLM，较高命中不必然带来较高可执行解决质量。

