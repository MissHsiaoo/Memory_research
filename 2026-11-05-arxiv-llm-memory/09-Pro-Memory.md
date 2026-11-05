# 09. Prospective Memory for Proactive LLM Agents

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.05731)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.05731)；[仓库内 PDF](pdf/2611.05731.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/03（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Bei, Yuanchen；Liu, Zhining；Wei, Tianxin；Zhang, Weizhi；Zeng, Zhichen；Yu, Philip S.；Hamann, Hendrik；He, Jingrui；Tong, Hanghang
- 机构：首页署名已核验：UIUC；University of Illinois Chicago；Stony Brook University；Brookhaven National Laboratory。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：prospective memory; proactive agents。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–6；已获取完整17页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

将未来意图保留、触发判断与实际行动分离，研究主动代理何时该行动而非仅如何找回旧信息。

## 2. 怎么做、实验如何设计

意图存目标、可选条件、一次/重复属性及来源；分别维护历史证据与当前线索，决策ACT/WAIT/OBSERVE，再与原生动作协调。只在实际发出关联动作或有满足/撤回证据时更新生命周期；可选经验记忆总结已结束回合反馈。PM-Bench和ProactiveBench，多backbone，对比RAG、A-Mem、MemoryOS、RWM等。

## 3. 结论

表1：Sonnet在PM-Bench Set-F1为0.7600，对RWM 0.7273；ProactiveBench F1为0.7376，对0.6609。并非所有误报指标都更好，例如Sonnet PM-Bench误报0.1000，高于RWM 0.0875。

## 4. 未来影响

推断：可用于多目标代理的待办、时机、取消与恢复，但应把意图强度和行动授权分开建模。

## 5. Critical thinking

论文自己区分发出行动与外部目标完成；一次性意图在发出后退休可能不适合网络失败、部分完成。语义触发充分性仍由LLM判断，结构合法不等于获授权。建议测试失败重试、条件修订、重复线索、冲突目标及用户撤回；按干预代价评估收益，不只最大化召回。

## 6. 可信度判断

4/5。明确生命周期与多个基准/backbone，负例和误报指标重要；现实长期事件和外部执行确认仍待验证。

## 官方提交记录

Submission history From: Yuanchen Bei [ view email ] [v1] Tue, 3 Nov 2026 23:03:06 UTC (511 KB)
