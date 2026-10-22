# 14. Memory as Code: Declarative Retrieval over Codified Long-Term Memory

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27700)；[官方 PDF](https://arxiv.org/pdf/2610.27700)；[仓库 PDF](pdfs/2610.27700.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Aoting Zeng , Yuxin Du , Jianwei Wang , Yizhang He , Shan Jiang , Xuemin Lin , Kai Wang
- 机构（PDF 首页署名核验）：Shanghai Jiao Tong University；University of New South Wales；The Chinese University of Hong Kong Shenzhen
- 机构优先级：P1B；主题相关性：直接相关；研究标签：agent memory；temporal retrieval；executable memory
- 阅读证据：正文§2–3（PDF第3–8页）；首页。已获取完整 PDF（15页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

将对话事实变成带来源的可调用函数，把查询转成可执行的检索组合程序。

## 2. 怎么做、实验如何设计

【论文直接证据】分原子函数、关系、派生模板三层；显式supersedes链接保留历史，当前值不唯一则返回未解决状态。planner一次生成查询计划，经检查后执行算子。LoCoMo三backbone、LongMemEval一个backbone，与A-Mem/MemoryOS/Mem0/MRAgent比较。

## 3. 结论

【论文直接证据】LongMemEval的judge分74.60对Mem0的68.40，提升6.20个百分点即相对9.06%；时间推理和知识更新改善较明显。总token173k低于MRAgent249k，但耗时4663.66秒高于2963.90秒，省token不等于最快。

## 4. 未来影响

【阅读者推断，尚待验证】记忆的创新可以在访问语义和组合算子，而非向量库；多目标查询可共享事实函数并采用不同计划。

## 5. Critical thinking

【阅读者评析与后续建议】可执行代码不能修复错误事实抽取和错误supersedes边；单次完整计划遇到未预见结果可能不稳。LLM judge还可能有同模型偏好。建议事实抽取oracle对照、执行沙箱、非法计划率、冲突值拒答、真实更新流与用户权限隔离测试。

## 6. 可信度判断

**4/5**（与机构优先级独立）。方法接口、成本与消融清楚，证据不止摘要；现有对话QA与judge指标不能证明真实持续记忆安全性。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
