# 20. LIBRA: Programmatic Induction of Executable Tool Libraries

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.05445)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.05445)；[仓库内 PDF](pdf/2611.05445.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/03（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Li, Zekai；Liu, Zhenke；Li, Yonghao；Liu, Junhan；Xiao, Xulong；Zhang, Jiapeng
- 机构：首页署名已核验：Brown University；University of Southern California。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：procedural memory; tool retrieval。
- 相关性：弱相关但具启发性：程序化工具经验，可迁移到技能记忆。
- 阅读范围：PDF首页及关键方法/实验页 1、3–5；已获取完整21页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

把平面工具目录变成由实际执行验证的组合依赖库，可视为可复用程序经验的结构记忆。

## 2. 怎么做、实验如何设计

LLM从公开schema提出调用契约，在沙盒内执行并至多两轮修订；对值依赖做同状态替换/省略对照，对状态依赖做前后对照。检索先选语义seed，再沿入边补前置工具并重排。AppWorld、SciToolEval、BFCL上测precision/recall/NDCG，并嵌入agentic retrieval。

## 3. 结论

表2：AppWorld Recall@15 40.7，对QTS 28.7；SciToolEval Recall@10 91.1，对84.1；BFCL Recall@15 86.4，对81.8。AppWorld NDCG低于TGR-Adapt，且这些是候选工具指标，不是任务执行成功率。

## 4. 未来影响

推断：程序记忆可在用户查询前主动建造并用执行反事实校验，减轻每次任务重新发现依赖的负担。

## 5. Critical thinking

一次沙盒状态验证不保证所有输入、权限与版本都成立；替换literal失败只证明对所测对照的必要性。构建运行的工具必须无危险副作用且有隔离。建议测试版本变更、撤销权限、依赖失效、长链组合及端到端完成率，并把构建成本摊销报告。

## 6. 可信度判断

3/5。运行证据比纯文本推断更强，信息边界清楚；主要指标仍是检索，沙盒覆盖与实际完成率不足。

## 官方提交记录

Submission history From: Zhenke Liu [ view email ] [v1] Tue, 3 Nov 2026 16:57:04 UTC (1,672 KB)
