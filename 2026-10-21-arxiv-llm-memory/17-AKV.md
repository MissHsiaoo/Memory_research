# 17. Cache Engineering for Agents

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.28577)；[官方 PDF](https://arxiv.org/pdf/2610.28577)；[仓库 PDF](pdfs/2610.28577.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Tianyu Fu , Ruoxi Wang , Zihan Min , Zhongqi Ren , Zhihao Li , Tengxuan Liu , Shengxu Mu , Hanling Zhang , Yu Wang
- 机构（PDF 首页署名核验）：Tsinghua University；The Chinese University of Hong Kong
- 机构优先级：P1B；主题相关性：直接相关；研究标签：KV memory；cache engineering；agent efficiency
- 阅读证据：正文§3–5、表1–2（PDF第3、5–9页）；首页。已获取完整 PDF（21页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

允许agent直接drop和重排KV位置，而不修改逻辑文本历史或重新prefill保留后缀。

## 2. 怎么做、实验如何设计

【论文直接证据】定义append/drop/repos操作历史；缓存状态不仅由剩余token决定，还由删除时机决定，因此扩展radix树和恢复机制。3模型，BCP/GAIA-Text/SWE-Verified/xbench；保留最近12工具响应KV，比较两种摘要阈值策略。系统测试8张A800，prefill/decode各4。

## 3. 结论

【论文直接证据】跨设置平均成本降低27.7%，平均分约+1.7点；并非每项均涨，例如MiniMax SWE75.2→74.4。各自峰值吞吐配置对比，输出吞吐1.18倍、P95延迟加速1.51倍。

## 4. 未来影响

【阅读者推断，尚待验证】记忆管理需要将文本内容、活跃KV和物理缓存驻留分开，提供可审计的状态操作日志。

## 5. Critical thinking

【阅读者评析与后续建议】保留KV可能携带已删除上文的信息，因此drop不是语义遗忘或隐私删除。逻辑输入吞吐包含已drop token，不能当作实际计算量；峰值比较并发数不同。建议固定并发和总GPU时、长距离必需证据、跨请求隔离及恢复一致性测试。

## 6. 可信度判断

**4/5**（与机构优先级独立）。系统语义、真实服务实验和多模型任务较完整；成本是价格模型估算，不是所有托管API都开放这些操作。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
