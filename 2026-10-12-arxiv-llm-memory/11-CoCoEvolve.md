# 11 CoCoEvolve：利用完整进化史的元反思

- 论文：[arXiv:2610.12794](https://arxiv.org/abs/2610.12794) · [官方 PDF](https://arxiv.org/pdf/2610.12794) · [本地 PDF](2610.12794.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-08 提交。
- 作者：Seung Won Wilson Yoo、Chang Zeng、Aditi Somayajula、Sahithi Ankireddy、Rohan Kosalge 等。机构：Snowflake、UMass Amherst、Stanford University、UC Berkeley、University of Pennsylvania（PDF 首页核验）。
- 机构优先级：B（一流高校 + 工业研究）；研究标签：self-evolving agents、history retrieval、system optimization。

1. **做了什么｜论文证据：**提出 CoCoEvolve，不再只根据当前父代失败做一次变异，而从整个进化历史检索可用证据并探测当前系统。
2. **怎么做、实验如何设计｜论文证据：**代理式 mutator 查询历史 ledger/其他谱系、调用现场工具验证假设后提交变异；在数据代理、LLM 数据管线和数据工程流程上测试，并做匹配消融。DABStep held-out hard、六个管线工作负载、data-eng-bench 均有结果。
3. **结论｜论文证据：**报告 DABStep hard 准确率 92.8%，对比 Meta-Harness 78.4%、GEPA 30.4%；data-eng-bench 测试成功率由 59.1% 升至 77.4%。结果支持历史检索与现场探测的组合，但非单一组件独立因果证明。
4. **未来影响｜我的推断：**代理自改进记忆不只存成功提示，还应保存失败谱系、相互冲突的修复和可查询的诊断证据。
5. **Critical thinking｜我的推断：**历史越大，检索及验证预算越高；若开发/测试系统反馈泄漏，进化会过拟合。建议报告等 token/等 wall-clock 的改进曲线，并在未见生产故障上评估回退能力。
6. **可信度：4/5。**依据：核查多工作负载、匹配对照和消融；优点是接近生产任务，局限是部分系统/执行细节复杂且外部独立复现成本高。
