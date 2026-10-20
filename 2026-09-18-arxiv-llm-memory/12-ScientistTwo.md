# 12. ScientistTwo: Pioneering the Human Knowledge Frontier with Autonomous AI

- arXiv：[论文页面](https://arxiv.org/abs/2609.19644v1)｜[官方 PDF](https://arxiv.org/pdf/2609.19644v1)｜[本地 PDF](papers/12-ScientistTwo-2609.19644.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Jaehyun Nam , Jinsung Yoon , Yanzhou Pan , Yubo Wang , Rui Meng , Parthasarathy Ranganathan , Tomas Pfister
- 机构：Google Cloud AI Research；University of Waterloo（不写成 Google DeepMind）。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜优先公司，自演化科研相关
- 研究标签：self-evolving research agent；实验记录；AI-review proxy
- 入选理由：Google Cloud 的闭环科研系统具有实验历史与改进循环启发，但 AI 评审“可发表”结论必须严审。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

ScientistTwo 把文献局限抽取、候选想法筛选、baseline 重现、实验、消融、写作和模拟 peer review/rebuttal 串成自主科研循环。研究历史与成功/失败记录帮助迭代想法，相关性在 self-evolving research process，而不是一个单独的新 memory 编码算法。标题中的 frontier 叙事强于目前可直接验证的证据。

## 2. 怎么做，实验如何设计

输入来自 107 篇已被 ICLR/ICML/NeurIPS 等会议接受的论文任务与代码库；agent 验证局限，生成并排序想法，先在子集实验，再在完整集扩展，最后从实验记录改进方法。系统使用 ScholarPeer 和另一 Stanford review agent 评审生成论文，包含 AI 评审反驳闭环。86/107 任务完成，成功率 80.4%。报告主表增益的自动解析也由 LLM 辅助，需区别于全部任务上的独立人类审计。

## 3. 结论

在成功产出的 86 篇上，ScholarPeer 平均约 7.5、判定接受 91.9%，Stanford 评审均分约 5.7、接受 72.1%；这是 AI judge 的接受判断，不是真实会议录用。后续 rebuttal 优化后 ScholarPeer 接受约 93.9%、Stanford 约 69.4，指标并不共同提升。只统计成功产出还会遗漏 21 个未完成任务，不能把条件均值当作全部研究任务的成功质量。

## 4. 未来影响

我的推断：实验 memory 应保留失败假设、环境与评测版本、未完成尝试，避免自主科学家只积累成功叙事。本文提供可实现的科研 orchestration 范式，值得从中抽取证据账本与假设生命周期；但“可以写出 AI reviewer 喜欢的论文”与“产生可重复、独立认可的新知识”是两个目标。

## 5. Critical thinking

最明显问题是用参与优化的 reviewer 作为重要结局指标，有 proxy over-optimization 风险。接受论文与已有代码作为种子也提供强先验，不能视为从空白根本问题独立开辟领域。AutoSOTA 等比较若预算、任务与失败处理不同，不能直接证明系统普遍超人。建议冻结系统后由独立领域专家盲审全部 107 任务，重新执行关键结果并核查代码/数据泄漏；另为未完成、负结果及不支持假设设等权评价，不只看生成论文得分。

## 6. 可信度判断

可信度 3/5：全文流程、任务数量和双 reviewer 分歧提供可检查信息，优点是端到端代码与实验循环。局限是 AI-review 代理、成功条件化、研究种子强、预算比较不完全匹配及外部验证不足。本评分针对 frontier/publishable 主张的证据，而非否认系统能运行；Google Cloud 机构质量不能替代独立科学复现。

