# 02 T-Mem：多方对话的时间证据森林

- 论文：[arXiv:2610.12874](https://arxiv.org/abs/2610.12874) · [官方 PDF](https://arxiv.org/pdf/2610.12874) · [本地 PDF](2610.12874.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Junyou Guo、Chongyang Tao、Yan He、Yong Wang、Shuai Ma。机构：Beihang University、Alibaba Group（PDF 首页核验）。
- 机构优先级：A（Alibaba + 强高校）；研究标签：LLM memory systems、multi-party conversation、temporal retrieval。

1. **做了什么｜论文证据：**提出 T-Mem，以时间结构恢复多人长期对话里被遗漏的局部证据及决策演变。
2. **怎么做、实验如何设计｜论文证据：**先以 Temporal Evidence Discovery 找到时间上密集的相关消息，再以 Temporal Memory Structuring 表示状态转移和支持关系、压缩低信息区间，最后线性化证据森林供回答模型读取。在 GroupMemBench 与 EverMemBench 两个多人记忆基准上，跨模型、参数、领域和问题类型比较现有记忆系统。
3. **结论｜论文证据：**论文报告相对竞争框架的稳定提升；其证据更支持“时间拓扑对多人状态追踪有帮助”，而非所有记忆问题都需要森林结构。
4. **未来影响｜我的推断：**时间关系可从检索附属元数据上升为记忆的组织主轴，适用于会不断撤销、确认和重议的协作对话。
5. **Critical thinking｜我的推断：**方法依赖初始 Top-k 检索找到正确时间邻域；论文局限性讨论也提及这一入口依赖。若消息乱序、跨时段引用或时间戳错误，局部扩展会失败。建议按时间扰动、跨线程指代和检索召回率分层消融，并报告额外结构化 token/延迟。
6. **可信度：4/5。**依据：核查了方法、两类基准和消融/局限；优点是失败机制与设计对应，局限是评价集中在特定多方对话集和初检索质量。机构标签与证据分数独立。
