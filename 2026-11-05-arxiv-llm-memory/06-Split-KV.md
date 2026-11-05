# 06. Split-KV: Efficient Context Parallelism for Training Diffusion Drafters

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.05926)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.05926)；[仓库内 PDF](pdf/2611.05926.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Zhang, Geng；Zhang, Fangzhao；Xie, Cong；Fan, Tiantian；You, Yang
- 机构：首页署名已核验：ByteDance Seed；National University of Singapore；Stanford University。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A1：优先产业研究机构。
- 研究标签：diffusion LLM; context parallelism。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1–5、7–8；已获取完整14页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

为扩散drafter的短查询、长上下文训练设计精确上下文并行，而非一种新记忆检索算法。

## 2. 怎么做、实验如何设计

KV分片常驻本地，聚合查询及输出/梯度，通过全局log-sum-exp组合还原注意力；以实际anchor位置估算KV块成本，再用LPT分配。对两种DFlash模型在8–64设备测试，固定短query并扩大context；主要计时离线输入目标隐藏状态后的drafter训练，排除目标模型特征提取。

## 3. 结论

第8页：64路弱扩展效率91%和85%，相对可用最快基线加速2.81和2.19倍；强扩展配置最高3.67倍，但64路强扩展效率只有55%和43%。这些不是完整训练或推理的统一加速倍数。

## 4. 未来影响

推断：对长历史扩散草稿训练，通信应按query/context不对称设计；经验支持避免把anchor预算随上下文长度同比扩大。

## 5. Critical thinking

每层通信与context长度无关不等于整个训练零KV搬运：每步有一次KV重分配。固定query前提失效时收益可能缩小。测量仅5步warmup后3步平均，随机固定长度输入和较强网络限制外推。建议加入真实变长样本、目标特征抽取、完整训练时间及通信拥塞，并检查数值误差而非只看形式精确。

## 6. 可信度判断

4/5。代数分解、受控质量实验及多规模系统比较较完整；端到端训练摊销和生产波动仍需补证。

## 官方提交记录

Submission history From: Geng Zhang [ view email ] [v1] Wed, 4 Nov 2026 04:16:46 UTC (272 KB)
