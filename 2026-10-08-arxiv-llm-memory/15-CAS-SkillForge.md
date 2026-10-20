# 15｜中科院：SkillForge 让技能记忆经历试用、稳定与退休

- 论文：[arXiv:2610.09832](https://arxiv.org/abs/2610.09832)｜[官方 PDF](https://arxiv.org/pdf/2610.09832)｜本地 `2610.09832.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-07 UTC，v1。作者/机构（PDF 首页）：Yuyao Ge、Yiwei Wang、Yuchen He、Baolong Bi、Lingrui Mei、Jiayu Yao、Lizhe Chen、Shenghua Liu；Institute of Computing Technology, Chinese Academy of Sciences、UC Merced、Tsinghua University。机构优先级：A+；标签：skill memory、self-evolving agent、agentic RL；直接相关。

## 1. 做了什么

Agent skill 是带适用条件的程序性记忆；随着策略变强，曾经有用的技能可能过时甚至误导。SkillForge 不把技能库当只增不减的档案，而让条目按表现经过 trial、active、stable、retired 的生命周期，与策略共同演化。

## 2. 怎么做、实验如何设计

先用基础模型 rollout 估计技能 fitness，提前退休低质量项，再用过滤后的库做 SFT；RL 阶段按成功使用证据执行选择性退休、稳定化和 LLM 引导变异。PDF 对比 ReAct、Reflexion、Mem0、ExpeL、MemP、SimpleMem、GRPO 等，在 ALFWorld、WebShop 和 Search-Augmented QA 上测试；还发布 SkillFurnace，含 1,013 条 SFT 轨迹、4,521 个库快照与 318 个退休事件，总计 5,852 条记录。

## 3. 结论

论文报告多交互基准的最高汇总成功率，相对最强基线最高约 7.8% 的相对提升，并在训练中维持较紧凑技能库。数据集为技能生命周期研究提供过程级观测，而不只留最终任务分数。

## 4. 未来影响（推断）

未来长期记忆系统可为事实、偏好和技能分别设计过期、试用与复活策略；“删除”不再只是容量清理，而是可靠性的主动控制。

## 5. Critical thinking

使用次数低不一定表示技能无用，可能是长尾场景稀少；基于旧策略 rollout 的退休判断也会将未来新策略需要的技能过早删掉。建议测试技能复活、长期任务季节性、稀有高风险任务，并用相同 token/库容量预算对照简单 recency 淘汰法；另外需评估 LLM 变异引入的不可解释行为。

## 6. 可信度：3/5

依据：核查 PDF 生命周期规则、三类环境与数据集统计。优点是同时研究保留与淘汰，给出过程数据；局限是收益相对不大，复杂训练管线中各组件贡献和长期安全仍需更独立验证。
