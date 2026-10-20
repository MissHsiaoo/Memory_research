# 03 T²Mem：推理时按问题构建记忆

- 论文：[arXiv:2610.13348](https://arxiv.org/abs/2610.13348) · [官方 PDF](https://arxiv.org/pdf/2610.13348) · [本地 PDF](2610.13348.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Zijun Wang、Yifan Ji、Haidong Xin、Zhenghao Liu、Yukun Yan、Zulong Chen、Yu Gu、Ge Yu、Maosong Sun。机构：Northeastern University（中国）、Tsinghua University、Alibaba Group（PDF 首页核验）。
- 机构优先级：A（Alibaba + 清华）；研究标签：test-time memory、long-term conversation、retrieval-memory。

1. **做了什么｜论文证据：**提出 T²Mem，把复杂记忆结构的生成推迟到知道查询之后，减少离线维护开销。
2. **怎么做、实验如何设计｜论文证据：**离线只抽取带时间线索的轻量 episode 元数据并保留原对话链接；推理时沿当前问题逐步检索元数据和原交互，重建跨 episode 依赖。使用 LoCoMo、LongMemEval，对比朴素 RAG、离线结构化记忆和其他测试时方法，考察回答准确率与构建开销。
3. **结论｜论文证据：**作者报告多种 backbone 上优于强基线且降低记忆构建开销；此处不能自动等同为端到端查询延迟更低。
4. **未来影响｜我的推断：**将记忆“预先压缩”改为“按需编排”，可能更适合异质问题和长期未访问的用户历史。
5. **Critical thinking｜我的推断：**轻量元数据仍须覆盖未来问题需要的线索；元数据漏记时测试时构造无从恢复。应按查询频次、历史长度和元数据漏召回率报告总成本，并与预算匹配的长上下文/RAG 比较。
6. **可信度：4/5。**依据：核查全文框架、两个公认记忆基准和多类基线；优点是效率与准确性同时衡量，局限是开放式用户时间线和端到端维护成本仍需外部验证。
