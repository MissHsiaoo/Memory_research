# 09 VEPA：可验证的长期代理规则进化

- 论文：[arXiv:2610.12813](https://arxiv.org/abs/2610.12813) · [官方 PDF](https://arxiv.org/pdf/2610.12813) · [本地 PDF](2610.12813.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-08 提交。
- 作者：Duy Nguyen、Lesly Miculicich、Bhavana Dalvi Mishra、Shuo Li、Krishnamurthy Dj Dvijotham、Mohit Bansal、Tomas Pfister、Long T. Le。机构：Google Cloud AI Research、University of North Carolina at Chapel Hill、Google DeepMind（PDF 首页核验）。
- 机构优先级：A（Google DeepMind/Google Cloud AI Research）；研究标签：lifelong agent adaptation、formal policy；**弱相关但具启发性**，不是 LLM 记忆模块。

1. **做了什么｜论文证据：**把长期代理安全策略表示为可执行符号规则，并在部署反馈下受约束地演化。
2. **怎么做、实验如何设计｜论文证据：**先将代理交互映射为类型化事件，LLM 根据失败反馈提议规则补丁，确定性验证器只接纳结构合法、无冲突的版本；未知事件回退给 LLM。用 ASSEBench-Security、ASSEBench-Safety、ATBench 比较固定及自适应护栏，并测试混合流、噪声反馈和回退设置。
3. **结论｜论文证据：**报告正式策略覆盖范围内较好的 F1 与可重现决策；形式保证仅涵盖被正确解析且被规则覆盖的事件。
4. **未来影响｜我的推断：**代理记忆的长期演化可以借鉴“提案—验证—启用”关卡，减少未经检验的经验直接写入高风险行为策略。
5. **Critical thinking｜我的推断：**论文明确指出上游 LLM 事件解析与 fallback 不在形式保证边界内，固定 schema 也限制复杂多步情境。建议评估解析错误传播、跨时间复合风险和规则库增长时的覆盖/延迟。
6. **可信度：4/5。**依据：核对形式流程、三个基准和明确局限；优点是保证边界写得清楚，局限是离线轨迹评估未证明在线安全性。
