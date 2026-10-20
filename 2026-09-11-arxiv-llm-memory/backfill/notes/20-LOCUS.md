# 20. LOCUS

LOCUS: Task-Aware Low-Rank Post-Training for Token-Efficient Language Generation

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11739v1](https://arxiv.org/abs/2609.11739v1) · [官方 PDF](https://arxiv.org/pdf/2609.11739v1) · [本地 PDF](../papers/20-LOCUS.pdf)
- 首次提交：2026-09-10T15:53:25Z（UTC，与公告日不是同一概念）。
- 作者：Dongfang Zhao
- 机构：University of Washington Tacoma（PDF 邮箱与官方目录核验；不泛化为 Seattle Allen School 主聘）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：弱相关但具启发性｜低秩个性化 / 输出成本
- 原文定位：§3–5、Limitations，PDF 第 6–9 页；官方目录 https://directory.tacoma.uw.edu/employee/dzhao。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

在保持原始偏好优化目标的前提下，选择任务相关低秩更新子空间来减少输出 tokens。

## 2. 怎么做的，实验怎么做

冻结 backbone，以候选 rank 和投影模块组合搜索 adapter；用 development 上的 utility constraint 选配置/checkpoint，而不是直接给输出长度加惩罚项。

实验与结果：Pythia-2.8B、Qwen2.5-3B，单 A100 80GB。DPO/DrDPO 在 8,552 frozen test pairs，SamPO 在 256 例 split；greedy、最多 256 new tokens。Pythia DPO 输出 137.67→109.12（-20.73%），偏好诊断 48.40→48.39；最大 39.84% 来自 SamPO 小集，不能混为同一协议。额外 harmless/Orca 各 256 例只属 dev。

## 3. Conclusion

更新子空间能影响生成长度，而内部偏好诊断变化小；这不等于真实回答质量或安全性已无损。

## 4. Future impact

个性化 adapter 可同时约束用户效用与响应成本，但不能以变短掩盖漏答。

## 5. Critical thinking：优点、问题与可验证拓展

优点是匹配 SFT 起点和原始 objective，区分 dev/test。局限是偏好分数接近随机且不等于盲评质量，单规模与 greedy 设置有限；256-token 截断会影响长度解读。建议加入独立人评/任务完成度与长输出压力测试。可信度 3/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**3.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

