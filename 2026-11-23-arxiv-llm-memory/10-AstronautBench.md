# 10. AstronautBench: Measuring Agent Self-Improvement Across Episodes Through Knowledge, Evidence, and Progress

- [arXiv 摘要](https://arxiv.org/abs/2611.26910) · [官方 PDF](https://arxiv.org/pdf/2611.26910) · [本地 PDF](pdfs/2611.26910.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-19（来自官方 submission history，非公告日期）。
- 作者：Yu, Congyuan; Tian, Runping。
- 机构：首页署名核验，Congyuan Yu署名Carnegie Mellon University；Runping Tian未标机构，不据邮箱推断。机构层级：B：强研究型高校参与，部分作者机构未署名。
- 研究标签：multi-objective memory evaluation；episodic evidence；self-improvement。
- 阅读依据：已下载并解析完整 11 页 PDF，目视核验首页；本评析重点核读 §3–6及Limitations，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：3/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：在同一agent运行上分开测知识正确性、该知识是否由亲身经历支持，以及实际世界进展。非常接近“多目标记忆使用”的测评需求，但没有形式化成多目标优化或给定偏好权重的Pareto benchmark。

## 2. 怎么做、实验如何设计

基于Outer Wilds：每回合约22分钟，世界重置而知识保留。评测地点发现、ship-log rumor facts及累计发现曲线面积；每回合后回答164个世界问题，引用不晚于当前回合的帧、天体与位置。程序检查引用存在性/时序/位置，两个不同模型家族裁判分别检查答案与证据支持。八回合基线包括GPT-6.1 Sol和Gemini 4 Argon规划器，控制器或直接gamepad执行；知识库是实体中心、证据链接的追加记录。

## 3. 结论

论文证据：GPT基线正确回答从14.6%升到26.8%，第8回合正确答案中约59–68%获得引用证据支持；rumor发现第3回合后不再增长，地点/记忆仍增长。后期变正确的回答有一半以上只引用较早证据。记忆更多、回答更好与任务真正进展不是同一件事。

## 4. 未来影响

研究判断：做多用途memory可直接借用其三轴报告：事实问答、证据忠实性、行动收益，再加入存储/检索成本。它比纯长对话QA更适合识别“记住却不会用”。

## 5. Critical thinking

每条件一次运行，只能描述观察；GPT两个运行同时改知识库和QA告知，无法隔离memory作用。游戏知识可能来自预训练，控制器不可靠也会阻止新证据采集。建议随机化世界事实、加入无记忆/随机记忆/理想执行器对照，多种子测三轴曲线及预算匹配；独立人工核验裁判。

## 6. 可信度判断

3/5。测量对象分离很有启发，引用校验设计具体；单运行、控制混杂和LLM裁判尚不足以支持稳健方法排名。优先作为benchmark设计参考，而非现成的多目标最优方法证据。

