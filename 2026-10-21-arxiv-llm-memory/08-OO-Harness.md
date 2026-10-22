# 08. Object-Oriented Harness: Evolving Agent Harnesses through Object-Oriented Design

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.28380)；[官方 PDF](https://arxiv.org/pdf/2610.28380)；[仓库 PDF](pdfs/2610.28380.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Gaotang Li , Bhavana Dalvi Mishra , Yifei Ming , Yanfei Chen , Zhongying CuiZhu , Lesly Miculicich , Long T. Le , Rui Meng , Chun-Liang Li , Hanghang Tong , Chen-Yu Lee , Tomas Pfister
- 机构（PDF 首页署名核验）：Google Cloud AI Research；University of Illinois Urbana-Champaign
- 机构优先级：P1A；主题相关性：弱相关但具启发性；研究标签：procedural memory；harness evolution；routing
- 阅读证据：正文§3–5（PDF第4–7页）、Limitations第10页；首页。已获取完整 PDF（20页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

将可复用代理经验编码成可继承的harness类树，通过方法覆写保留共享行为并专门化。

## 2. 怎么做、实验如何设计

【论文直接证据】先运行基础harness聚类失败需求，再对簇生成子类、执行验证并保存反馈/路由经验；测试冻结类树，router根据任务和基础轨迹选类。AutomationBench 300/300、Workspace 288/100、Toolathlon251/252发现/留出题；同executor，最多40演化轮，3次独立执行。

## 3. 结论

【论文直接证据】三基准主指标均优于论文比较方案。跨基准汇总图中Mean39.4→51.4；还设置best-of-2/5及self-refinement，表明额外推理并不自动带来同等增益。

## 4. 未来影响

【阅读者推断，尚待验证】技能记忆可从自然语言笔记发展成有接口、继承与版本管理的可执行组件。

## 5. Critical thinking

【阅读者评析与后续建议】路由要先取得基础轨迹，成本不止最后一次运行；论文Steps只计最终选中的轨迹，排除了其他rollout及选择调用，不能用它代表总成本。簇内接受不保证所有任务无回归。建议报告总API成本、路由错误、全局回归测试及接口变化后的失效率。

## 6. 可信度判断

**4/5**（与机构优先级独立）。留出测试、冻结经验与推理扩展基线较完整；依赖具体API/模型，尚无部署级稳定性证明。Google Cloud署名不等同Google DeepMind。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
