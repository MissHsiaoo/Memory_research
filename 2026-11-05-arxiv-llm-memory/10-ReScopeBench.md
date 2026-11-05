# 10. Towards Robust Long-Lived Agents: Benchmarking Experience Lifecycles in Evolving Environments

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.05450)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.05450)；[仓库内 PDF](pdf/2611.05450.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/03（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Huang, Shijue；Guo, Hangyu；Zhang, Hengheng；An, Guo；He, Zhitao；Tian, Qi；Feng, Yiren
- 机构：首页署名已核验：HKUST；Huawei；Guangdong Laboratory of Artificial Intelligence and Digital Economy (SZ)。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：experience lifecycle; continual memory。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–6；已获取完整29页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

评测代理经验的获取、复用、失效、更新与保留，区分环境结构知识和操作规则。

## 2. 怎么做、实验如何设计

18个可执行模拟环境、352任务、26次不预告局部变化。参考依赖图先定义可发现经验，再生成任务流；同初态做保留/清空经验两条流，任务采用确定性评分，经验由LLM按参考claims评估。20模型统一Hermes harness，每模型每环境各一条流。

## 3. 结论

第6页：17/20模型结构覆盖高于规则覆盖；没有模型首次变化后更新覆盖超过37.63。高任务表现或最终恢复分数并不代表即时更新充分。RT记录首次共同正确时刻，不保证之后持续正确。

## 4. 未来影响

推断：比静态记忆QA更适合研究选择性修订、技能与事实分工、旧规则污染；可作为多目标经验复用的核心评测。

## 5. Critical thinking

两条流因动作不同而环境状态分化，任务差异不全是读取记忆的局部因果效应；UC还包含原本未掌握经验的首次获取。单流/环境限制方差估计，经验评分依赖模型和rubric。建议多随机种子、固定状态反事实回放、追踪每条claim持续正确性，并加入延迟反馈与权限变化。

## 6. 可信度判断

4/5。可执行状态、隐式变化与多模型诊断比单次问答更扎实；记忆评分、构造环境与单流采样限制外推。

## 官方提交记录

Submission history From: Shijue Huang [ view email ] [v1] Tue, 3 Nov 2026 17:57:20 UTC (1,500 KB)
