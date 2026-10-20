# 19. Stellar Colosseum: A Many-Agent Harness for Long-Horizon Research in Mathematics and Theoretical Computer Science

- arXiv：[2609.15983v1](https://arxiv.org/abs/2609.15983v1) · [官方 PDF](https://arxiv.org/pdf/2609.15983v1) · [本地原文](../papers/19-StellarColosseum.pdf)
- 正式公告：2026-09-15；首次提交：2026-09-14（两者不是同一字段）。版本：v1。
- 作者：Honghao Lin , David P. Woodruff , Yuan Deng , Jieming Mao , Song Zuo , Vahab Mirrokni
- 首页核验机构：Google Research；Carnegie Mellon University。
- 机构优先级：A：强机构主榜（无普通机构补位）。机构只决定阅读优先级，不代替证据评分。
- 研究标签：相邻强启发｜长期科研状态；验证与经验聚合
- 主观 novelty：4/5；证据可信度：3.5/5（不是概率）。
- 阅读范围：方法、TCSBench与Codeforces实验、裁判和验证设置；未独立核证开放问题证明。

本笔记基于以上官方原文；第1–3节为论文内容及结果口径，第4–6节为阅读者判断，不能当作作者已验证的结论。未进行实验复现或代码审计。

## 1. 做了什么（论文报告）

面向长时间理论研究与算法求解，提出让独立推理分支竞争、相互检查并汇聚的系统。共享研究状态记录已证结论、失败路线和参考资料，把探索与正式证明组织分开，而不只是在单个长上下文里继续思考。

## 2. 方法与实验设计（论文报告）

先做准备度判断，再把证明拆成依赖结构，对局部论证定向找反例、修订，最后跨随机重叠分支树聚合。TCSBench有300个来自2020–2026年FOCS/STOC/SODA的定理，使用参考证明辅助自动评分；裁判提示在100个专家标注样本上调整后约90%准确。另测222个Codeforces问题与开放研究案例，比较有无可执行probe。

## 3. 结论与结果边界（论文报告）

单独Gemini3.1Pro和3.7Flash系统在TCSBench为54%和55%；对Pro答案发起8次独立Flash批判，至少5次认为正确则选Pro否则选Flash，组合达到71%（213/300）。Oracle二选一77.3%不是可部署结果。Codeforces有probe通过218题，无probe213题，但修订预算也不同，不能纯归因于probe。

## 4. Future impact（我的推断）

记忆可不只是经验文本，而是带依赖、反例和验证状态的研究账本。特别适合self-evolving agent：失败分支应记录其适用边界，已验证结论才进入高信任层。本文的共享状态设计有启发，但不等于已经独立证明了记忆组件的收益。

## 5. Critical thinking（我的分析与建议）

自动裁判可能漏掉数学证明的细微漏洞；与直接模型、DeepThink或GPT-5.6Pro相比，计算预算不完全一致。论文收集的近年公开定理存在潜在训练污染，需隐藏题和形式化验证。多数投票可能淘汰少数但正确的新路线，建议按解法多样性分簇，再做有证据的反驳，而不是让票数替代证明。

## 6. 可信度、优点与局限（主观评估）

3.5/5。优点：研究状态显式化、局部验证、多个困难任务，并报告组合前后差异。局限：昂贵多分支计算、裁判并非证明检查器、开放研究案例未由本次阅读独立验证。机构首页是Google Research，不据使用的Gemini模型写成Google DeepMind；高分是系统成绩而非基础模型单次能力。

## 来源与审计

[官方摘要页快照](../sources/2609.15983-abs.html)记录日期和版本；[本日入选核验](../verification.json)保存公告主分类、PDF页数与SHA-256。[返回日报](../README.md)。
