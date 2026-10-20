# 6. KuaiRP

KuaiRP Series Role-playing Models Technical Report

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11127v1](https://arxiv.org/abs/2609.11127v1) · [官方 PDF](https://arxiv.org/pdf/2609.11127v1) · [本地 PDF](../papers/06-KuaiRP.pdf)
- 首次提交：2026-09-10T06:14:58Z（UTC，与公告日不是同一概念）。
- 作者：Yipeng Wang, Ziwei Zhang, Jiahui Zhang, Qi Gan, Kai Sheng
- 机构：Kuaishou GameMind Lab（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜persona consistency / 参数记忆与遗忘
- 原文定位：§3–7，PDF 第 14–19 页、表 5–8。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

为小参数角色扮演模型注入世界设定与角色知识，同时恢复专门化训练损害的通用工具能力。

## 2. 怎么做的，实验怎么做

角色模板与反向 profile 过滤构造 SFT 数据，规则复合 reward 控制长度/重复；然后让原始 base 当 student、领域适应模型当 teacher，进行两阶段 on-policy distillation，并以累计分歧衰减 CDD 调整迁移。

实验与结果：4B/8B 模型分阶段测试 TRACEbench 角色/记忆一致性、领域知识和 BFCL v4。8B BFCL overall 从 base 24.83 降至 SFT 12.53，最终恢复至 24.78。领域角色子集报告 5 次运行均值/标准差；最终 8B 角色一致性 92.08±1.45，但记忆一致性 72.50±7.13，不是所有维度单调提升。

## 3. Conclusion

从原始 base 重新蒸馏可恢复功能，同时保留部分领域技能；“恢复”不等于在通用 agent 上超过 base。

## 4. Future impact

个性化可采用可丢弃的用户 teacher，再向干净 backbone 的受限适配模块迁移，比较持续累积更新造成的漂移。

## 5. Critical thinking：优点、问题与可验证拓展

优点是阶段消融、能力保留和多维指标。局限是内部角色评测与 judge、领域分布较窄；base 使用额外长度约束，需核对 prompt 公平性；4B 的一般记忆一致性并未全面恢复。建议跨用户/跨世界设定测试，并单独评估真实长期事实而非角色文风。可信度 3.5/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**3.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

