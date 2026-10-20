# CliffCompaction：长程 coding agent 的忠实上下文压缩

- arXiv：[2609.26779](https://arxiv.org/abs/2609.26779)；[官方 PDF](https://arxiv.org/pdf/2609.26779)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Trang Nguyen 等；Carnegie Mellon University、Bosch Center for AI
- 机构优先级：S（顶级高校/企业研究机构、直接相关）
- 研究标签：agent memory、context compaction、continual coding、long-horizon agent

## 1. 做了什么

论文提出 CliffCompaction，为跨 session、百万 token 级 coding agent 自动压缩上下文。核心主张是：压缩只截断或丢弃原始内容，绝不改写；每次都从原始历史重新压缩，避免“summary of summary”产生累积漂移。

## 2. 怎么做、实验如何设计

方法在固定上下文阈值下选择需保留的原始片段，并丢弃上一次压缩产物后重新生成压缩视图。作者在 SWE-bench Verified、Terminal-Bench 2.0 与 KernelBench 上测试单次运行、并行 test-time scaling 和跨数百步持续改进，比较 full context、滑窗及 Claude Code 的 microcompaction/summary 等方案，并报告成功率、输入成本和 CUDA kernel speedup。

## 3. 结论

论文报告 Terminal-Bench 成本最高降低约 50%，在不到两次 full-context rollout 的成本下通过 test-time scaling 增加 10 个百分点以上；KernelBench 在 200/400 步达到 2.23×/3.58× speedup。其关键收益来自保持原文忠实和避免压缩链式漂移。

## 4. Future impact

这项工作可能把“记忆”重新解释为可重建的上下文视图，而不是永久摘要。对 self-evolving agent memory 的启发是：长期状态最好保留不可变事件日志，再根据当前任务生成临时 working memory。

## 5. Critical thinking

方法最强的假设是“足够的信息可通过删除而非抽象来保留”。在代码任务中日志与文件片段高度可复用，这一假设成立得更好；在社交记忆或跨文档综合中，单纯删除可能无法形成必要抽象。建议验证相同总 token 预算下的 retrieval、结构化状态、忠实抽取式压缩，并测量被删信息的不可恢复失败。还需区分压缩本身与 prefix-cache 命中带来的系统收益。

## 6. 可信度判断

- 评分：4/5
- 依据：阅读全文包含多个 coding agent 基准、成本曲线、长程实验和开源实现链接。
- 优点：问题重要、设计简单可部署、避免了摘要漂移；成本与能力同时评估。
- 局限：领域集中在 coding；不同模型/定价可能改变相对成本；忠实不等于充分。

