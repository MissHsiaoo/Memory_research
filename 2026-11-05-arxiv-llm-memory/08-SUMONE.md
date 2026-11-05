# 08. SUMONE: A Simple and Efficient Summarizer for Plug-and-Play Agent Memory

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06445)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06445)；[仓库内 PDF](pdf/2611.06445.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Zhang, Jizhe；Li, Ang；Zhang, Chenheng；Wang, Yisen
- 机构：首页署名已核验：Peking University。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：agent memory; context compaction。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–6；已获取完整15页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

以掩码重建训练独立文本摘要器，让压缩模块不依赖在线运行下游任务获得奖励。

## 2. 怎么做、实验如何设计

约5K搜索/软件轨迹实例，16K/32K上下文；将历史切为约512-token块，随机遮50%。Qwen3.5-2B摘要，冻结9B重建，DeepSeek评估恢复precision/recall，并加长度惩罚，GRPO训练600步。测试DeepSearchQA、SWE-bench Verified及额外记忆和跨reader/harness设置。

## 3. 结论

主表：DeepSearchQA从完整历史0.52降到0.48，费用0.170降到0.038美元；SWE解决率0.63到0.59，费用0.286到0.071。约78%/75%估算费用下降，均付出4个百分点性能损失，不是无损压缩。

## 4. 未来影响

推断：重建目标可让低成本记忆写入器与不同执行模型解耦，适合模块化记忆系统。

## 5. Critical thinking

随机恢复常见内容不等于保留少数决定性条件；重建器可能利用上下文猜测，奖励又依赖LLM评分。训练轨迹覆盖搜索和编码，不是真正与所有任务无关。建议遮掉唯一证据、保留否定与权限、跨域长期重复压缩，画成本—准确率曲线而非单点压缩率。API价格仅是论文估算口径。

## 6. 可信度判断

4/5。固定阈值、同大小未训摘要器、跨模型与harness对照支持模块有效性；未独立复现，且性能下降需诚实保留。

## 官方提交记录

Submission history From: Jizhe Zhang [ view email ] [v1] Wed, 4 Nov 2026 12:49:07 UTC (1,488 KB)
