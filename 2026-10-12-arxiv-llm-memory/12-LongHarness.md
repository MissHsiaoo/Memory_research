# 12 LongHarness：超长语料的显式证据状态

- 论文：[arXiv:2610.13075](https://arxiv.org/abs/2610.13075) · [官方 PDF](https://arxiv.org/pdf/2610.13075) · [本地 PDF](2610.13075.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Songtao Huang、Zhijie Zhong、Xiaohan He、Shuaiyu Zhang、Zhiyin Yu 等。机构：Fudan University、Shanghai AI Laboratory、Peking University、Shanghai Jiao Tong University、USTC、Harbin Institute of Technology（PDF 首页核验）。
- 机构优先级：B（一流研究实验室/高校）；研究标签：agent memory、stateful evidence、retrieval-memory。

1. **做了什么｜论文证据：**提出 LongHarness，为超出窗口的海量文档代理建立可追溯的证据与结论状态，抑制无界搜索和证据状态漂移。
2. **怎么做、实验如何设计｜论文证据：**Evidence–Conclusion Coevolution 用未决结论引导补证，新增证据反向修正结论；Evidence Lifecycle Management 跟踪证据有效性。在 OfficeQA Pro V1/V2、AA-LCR、LongBench v2 长子集上评测，V1 约 1 亿 token、697 份文档；比较多种直接模型/代理 harness，并对 GLM 设置报告三次运行。
3. **结论｜论文证据：**作者报告在 OfficeQA Pro 中显著提升，GLM-5.3-Flash + LongHarness 在 V1 比 Claude Code 高 12.0 个百分点、V2 比 Codex 高 18.9 个百分点；比较仅对应论文具体 harness/模型/预算设置。
4. **未来影响｜我的推断：**显式结论状态可作为跨海量文档的“工作记忆”，不仅存检索片段，也存未解决的问题及修正链。
5. **Critical thinking｜我的推断：**结果可能受工具链、检索调用次数、token 预算和模型组合影响。建议等总成本匹配比较，评估故意矛盾/过期文档下结论更正时间，并记录错误证据存活率。
6. **可信度：4/5。**依据：已查框架、三个基准及多运行子集；优点是大规模真实式语料和消融，局限是系统级比较的预算控制与迁移性需复核。
