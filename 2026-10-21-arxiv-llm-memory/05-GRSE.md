# 05. Which Agent's Skill Should Change? Group-Relative Credit Assignment for Evolving Multi-Agent Teams

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27227)；[官方 PDF](https://arxiv.org/pdf/2610.27227)；[仓库 PDF](pdfs/2610.27227.pdf)
- 首次提交：19 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Yanan Ma , Yang Wang , David Le , Chenhan Yuan , Yizheng Sun , Guangwei Zhang , Chenghao Xiao , Chenghua Lin , Imon Banerjee
- 机构（PDF 首页署名核验）：Alibaba Token Hub（Alibaba）；Mayo Clinic；University of Manchester；Shanghai University of Finance and Economics
- 机构优先级：P1A；主题相关性：直接相关；研究标签：multi-agent skill memory；credit assignment
- 阅读证据：正文§3–5、表1（PDF第4–6页），Limitations第9–10页；首页。已获取完整 PDF（24页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

为多智能体技能库更新分配更细粒度的信用，避免看到最终答案错就修改错误的智能体技能。

## 2. 怎么做、实验如何设计

【论文直接证据】每个问题在同一技能库下运行4次；critic对比高低相对优势轨迹，引用步骤定位agent–skill责任，再跨问题聚合、提炼/删除/合并技能。候选单agent更新先相对旧团队验证。两agent顺序协作，HotpotQA与LoCoMo，两种开放actor，固定critic，5轮，3次训练。

## 3. 结论

【论文直接证据】HotpotQA Qwen下GRSE 83.7 F1优于MASkills80.6，但低于单模型Self-Refine84.1；Gemma下结构化版本82.8，非结构化83.3。LoCoMo多跳相对MASkills提高6.7/3.2 F1，开放域并非最优。

## 4. 未来影响

【阅读者推断，尚待验证】程序性记忆更新可以以责任证据为单位，而不是将整条失败轨迹自动变成全局规则。

## 5. Critical thinking

【阅读者评析与后续建议】不同rollout只是观察性对照，不能直接当因果反事实；组合多个单独通过的agent更新也可能产生交互。G=4带来1.6–2.9倍actor token及1.3–1.8倍时间开销，应与同预算单模型/多采样比较。建议做技能禁用干预、更多agent与并行沟通测试。

## 6. 可信度判断

**4/5**（与机构优先级独立）。给出训练成本、无技能和单模型基线及多次训练；只有两agent、两QA任务和一个critic，结论边界明确。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
