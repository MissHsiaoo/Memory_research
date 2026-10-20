# 19. LOO-ROLL

EGGROLL, Unrolled: Understanding and Improving Low-Rank Evolution Strategies at Scale

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.10980v1](https://arxiv.org/abs/2609.10980v1) · [官方 PDF](https://arxiv.org/pdf/2609.10980v1) · [本地 PDF](../papers/19-LOO-ROLL.pdf)
- 首次提交：2026-09-10T01:58:02Z（UTC，与公告日不是同一概念）。
- 作者：Ege C. Kaya, Abolfazl Hashemi
- 机构：Purdue University, Elmore Family School of ECE（PDF 首页脚注）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：弱相关但具启发性｜低秩进化优化 / 参数更新
- 原文定位：§4–10、表 9，PDF 第 24 页起。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

分析 EGGROLL 低秩扰动的有限秩偏差与方差，并提出一次评估每方向的 leave-one-out 估计器 LOO-ROLL。

## 2. 怎么做的，实验怎么做

区分总体更新场和有限 population 估计误差；有限秩可产生非保守更新、改变局部稳定性。LOO-ROLL 保持相同总体场，用一次评估替代 antithetic 两次。

实验与结果：从合成目标到 Qwen3-0.6B transformer blocks，再到最高 8B 模型的 10 个匹配 wall-time 后训练设置。10 个配对比较中 7 项显著改善、3 项差异未解决；Holm 多重比较校正后保留 5 项显著改善，无显著损失。不是 7 个校正后显著结果。

## 3. Conclusion

用同样评估时间采更多方向，可能比盲目提高扰动秩有效；有限秩的理论偏差并未被 LOO 消除。

## 4. Future impact

可为不能反传的个性化 adapter 或外部评分式 memory 参数优化提供候选，但需要计入每次用户反馈的成本。

## 5. Critical thinking：优点、问题与可验证拓展

优点是显式区分总体场/采样噪声，报告多重比较校正与匹配时间。局限是局部平滑理论不保证离散 agent reward 的性质，实际收益依赖评估噪声；本次未验证全部推导。建议对低维 memory policy 做同 wall-time ES/LOO/梯度三方对照。可信度 3.5/5。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

