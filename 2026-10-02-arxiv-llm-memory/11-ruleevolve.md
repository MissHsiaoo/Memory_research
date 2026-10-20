# 11 — Self-Evolving Coding Rules for AI Coding Agents

- arXiv：[2610.00650](https://arxiv.org/abs/2610.00650)；[官方 PDF](https://arxiv.org/pdf/2610.00650)；[本地 PDF](./2610.00650.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Zhengyuan Jiang 等；Duke University
- 机构优先级：**A+，一流研究型高校**；研究标签：`self-evolving agent` `procedural memory` `coding rules`
- 证据范围：核读 PDF 方法、实验；报告结果为作者结论。

## 1. 做了什么

把编码 agent 的规则文档当作可演化的程序性记忆，自动搜索比手写静态规则更有效的版本。

## 2. 怎么做、实验如何设计

RuleEvolve 维护候选规则池，LLM mutator 生成变体、judge 依据执行结果评分，再更新候选池。PDF 从 BigCodeBench 抽取 1,000 例用于规则演化，在两个编码框架、四种底模、三个基准上测功能正确率、代码长度与 token 成本，并与人工规则和提示优化基线比较；作者报告多个指标获益。

## 3. Conclusion

可执行反馈能使编码规则成为持续更新的 agent memory，而不是一次性系统提示。

## 4. Future impact

可延伸到工具使用规范、团队开发约定和项目级 agent 经验库的自动维护。

## 5. Critical thinking

**推断：** judge 可能偏好当前基准的编码风格，演化规则在新库里未必有效。应公开总候选/评估成本，做跨语言和跨仓库外推，并测试规则冲突、过时约束与回滚机制。

## 6. 可信度判断

**3.5/5。** 多框架/模型/基准较充分；实际团队中的长期稳定性和总优化成本未由摘要数字证明。
