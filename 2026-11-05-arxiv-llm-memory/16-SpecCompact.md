# 16. SpecCompact: Accelerating LLM Agent Context Compaction with Slot-Parallel Semantic Speculative Verification

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06876)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06876)；[仓库内 PDF](pdf/2611.06876.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：An, Yulu；Feng, Yifei；Yin, Xiangyang
- 机构：首页署名已核验：New York University。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：agent memory; semantic speculation。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–8；已获取完整12页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

用小模型并行草拟结构化摘要槽，再由大模型逐行语义验证和修复，减少记忆压缩等待时间。

## 2. 怎么做、实验如何设计

六槽分别为目标、约束、进度、决策、下一步和关键上下文；约50K实例训练0.6B drafter。共享前缀缓存、草稿缓冲和逐行停止减少重复prefill。两target，AppWorld、80任务τ3三次试验、LongBench/RULER；延迟每负载20个匹配输入，drafter额外一张GPU。

## 3. 结论

相对Hermes代理负载压缩加速Gemma 4.28–5.63倍、Qwen 2.04–2.41倍；但Gemma AppWorld TGC和τ3略降，Qwen部分指标略升。作者明确：完整任务评测尚未用全部系统优化重跑，因此最高加速与原任务准确率不是同一最终实现的联合验证。

## 4. 未来影响

推断：记忆写入可以成为异步/并行系统优化对象，但语义验证与逐token无损投机不同。

## 5. Critical thinking

槽间独立生成可能产生跨槽矛盾；逐行有根据不保证遗漏为零，目标修复行也未再次语义验证。top-k缺失标签概率采用替代估计。建议跨槽一致性检查、遗漏敏感测试、等GPU资源吞吐和最终优化版任务重测。

## 6. 可信度判断

3/5。真实harness集成和延迟分解明确；模型相关准确率退化、额外GPU和未重跑最终版限制端到端结论。

## 官方提交记录

Submission history From: Xiangyang Yin [ view email ] [v1] Wed, 4 Nov 2026 18:34:41 UTC (203 KB)
