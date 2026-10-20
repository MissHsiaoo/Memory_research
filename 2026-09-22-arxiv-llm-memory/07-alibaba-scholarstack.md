# ScholarStack: Layered Research Asset Orchestration and Cross-Task Reuse for Scientific Agents

- arXiv：[23735](https://arxiv.org/abs/2609.23735)；[官方 PDF](https://arxiv.org/pdf/2609.23735)
- arXiv 初次提交：2026-09-20（v1）；正式公告归属：2026-09-22 新稿，二者不可混同。
- 作者：ScholarSeed AI Team : Ao Zhang , Caoqinwei Gong , Guanglei Wang , Haifan Zhang , Hanwei Zhang , Jiayi Sheng , Jihai Zhang , Kai Ying , Liyun Dai , Tingyu Zhu , Wei Chen , Wei Luo , Wenkai Fang , Xiaoyu Qiu , Xue Jiang , Yi Wang , Yuan Cao , Zheng Yu , Wotao Yin（arXiv 官方列表）
- 机构：DAMO Academy，Alibaba Group（ScholarSeed AI Team）（论文 PDF 首页核验）
- 机构优先级：A｜顶级产业研究
- 研究标签：研究 agent memory；跨任务复用；层级知识资产；直接相关
- 证据说明：以下数值均为论文自身报告；“我的推断/建议”并非论文实证。

## 1. 做了什么

ScholarStack 将科研 agent 的长期“记忆”从松散聊天历史改成可版本化研究资产：来源约束的事实陈述、按主题组织的材料、跨论文的有范围综合结论。它特别契合连续读论文工作：同一来源可在检索、问答、创新性判断中复用，而不反复从原文开始。

## 2. 怎么做，实验怎么做的

三层架构 L1 保存带条件及来源 ID 的声明，L2 组织领域或论文群，L3 提供有范围的跨论文综合；更新时维护版本与引用链。作者跨四类任务、十个设置评估。LitSearch 约 64183 篇、资产 900 个：检索 R@10 为 .773，略低于全文检索 .787；R@1 为 .670，高于全文 .650。开放问答 89 题 F1 .141 对比全文 .128，绝对值仍低。创新性评估 40 目标 F1 .662 对比 .645，使用 token 约 21.4k 对比 35.6k。QASPER 单篇问答 F1 .5708 对比 RAG .5613。

## 3. Conclusion

分层资产在若干任务取得小幅质量收益和 token 节约，但不是所有检索指标第一；“科研知识已被可靠压缩”远未证明。其更坚实贡献是跨任务可追溯复用框架。

## 4. Future impact

对于每天的论文文件夹，最直接可借鉴的是把观察、证据位置、跨篇比较、待验证假设分层存储；这样后续周报与研究选题可复用，而不必重新读全部 PDF。这个应用建议是我的推断。

## 5. Critical thinking

预编译资产的生成成本应计入总预算，尤其论文集合常变时。某些 gold 与评判使用同一家族 LLM，可能放大系统风格偏好；创新性 40 目标等评测规模偏小，.006 等细微差异不宜过度解释。建议做跨月更新、被撤稿/修正论文、相互矛盾结论和错误引用追踪实验，并与同预算长上下文 RAG 对照。

## 6. 可信度判断、优点与局限

4/5：阅读全文结构、主要数据表及局限。优点是来源链与跨任务复用设计完整；局限是多指标增益小、部分绝对 F1 低、离线建库成本未充分纳入。
