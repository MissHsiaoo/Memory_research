# 12. MedicalRSI: Medical Recursive Self-Improving Agents via Clinical Model-Harness Co-Evolution

- [arXiv 摘要](https://arxiv.org/abs/2611.26806) · [官方 PDF](https://arxiv.org/pdf/2611.26806) · [本地 PDF](pdfs/2611.26806.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-19（来自官方 submission history，非公告日期）。
- 作者：Wang, Ziqing; Palangi, Hamid; Zhao, Lili; Ding, Kaize。
- 机构：首页署名核验，Northwestern University、University of Washington。机构层级：B：强研究型高校/实验室。
- 研究标签：self-evolving agent memory；model-harness co-evolution。
- 阅读依据：已下载并解析完整 45 页 PDF，目视核验首页；本评析重点核读 §2.1–2.5、§3.1–3.4、表1/图5–6，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：同一模型扮演Solver和Improver，从临床工作流失败中生成技能/SQL工具，训练二者共同演进。记忆按workflow存储可复用的技能或工具，并按实际收益更新。

## 2. 怎么做、实验如何设计

每轮汇总多类失败与成功作对照，Improver看到任务、轨迹和结果/过程反馈而非参考答案或grader细则。按相对无harness的收益奖励候选，同时训练Solver；新工作流可参考最相似的三个已存workflow。比较固定/训练Improver、只训Solver及STaR，测试MedAgentBench、MedAgentGym、未见workflow、其他Solver和MIMIC-III→eICU迁移。部分评测允许由测试初次尝试及反馈生成候选，并对候选平均而非挑最好。

## 3. 结论

论文证据：Qwen3.5-9B在MedAgentBench Outcome由36.9%到85.1%，比最强基线高22.3点；额外450个未见workflow任务74.1% vs GRPO Improver59.8%。固定Solver后MedicalRSI的harness仍优于单训Improver。数据库迁移到eICU只有37.2%，说明高同分布表现不代表跨数据库可靠性。

## 4. 未来影响

研究判断：把技能记忆质量与执行模型能力联合优化，有助于解决“记忆对旧模型有效，对新模型无效”的问题。可以研究按用户/环境版本保存技能适配信息。

## 5. Critical thinking

共享参数使Improver更新不自动等于改进算法本身突破；增益也可能来自更多尝试和更密反馈。测试反馈生成harness与严格零样本部署不同，虽作者报告仅用训练轨迹写harness总体变动不超过1.2点，仍应分开报告。建议做总rollout预算匹配、独立留出机构/数据库、否定和时间窗压力测试。基准成功率不是临床安全或真实疗效证据。

## 6. 可信度判断

4/5。跨模型/工作流迁移、角色固定消融和重复训练报告支持机制；合成/仿真工作流、反馈可得性及数据库迁移差距限制部署推断。

