# 7. KV-Persona

K/V-Cache Interventions Dissociate Representation Alignment from Persona Expression in Decoder-Only Language Models

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11020v1](https://arxiv.org/abs/2609.11020v1) · [官方 PDF](https://arxiv.org/pdf/2609.11020v1) · [本地 PDF](../papers/07-KV-Persona.pdf)
- 首次提交：2026-09-10T02:56:50Z（UTC，与公告日不是同一概念）。
- 作者：Yu Sun, Mengyin Lu, Cong Feng, Guangming Lu, Huimin Han
- 机构：LinkedIn（PDF 首页五位作者均署 linkedin.com 邮箱；未写成 Microsoft Research）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜KV latent memory / persona control
- 原文定位：§3–4、Limitations，PDF 第 9–10 页及附录 H。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

把目标 persona 条件下的 K/V 轨迹移植到源 persona 的生成中，检验表示对齐和行为变化是否一致。

## 2. 怎么做的，实验怎么做

比较整层、早/中/晚层替换、插值以及时间 lag/shuffle；增加同 token 序列控制，以区分 persona 条件和被移入的 token 历史。

实验与结果：主实验仅 Llama-3.1-8B、一个 persona 对、一个酸面团话题、13 个配置，主生成长度 50 tokens。中层 9–20 的 V-gap 0.89、TTR 0.77；整层 V-gap 0.94、TTR 0.65，表示更接近不代表表达更好。150-token 持久性检查仅 n=3。

## 3. Conclusion

KV 是可干预的表面，但表示相似度不足以预测角色表达；这里证明的是短程轨迹移植，不是通用长期个性化。

## 4. Future impact

评估 latent personal memory 时同时测行为效用、重复和内容归因，不能只报告 embedding/V-space alignment。

## 5. Critical thinking：优点、问题与可验证拓展

优点是明确同 token 对照与空间/位置因素。局限非常实质：单模型、单角色对、单话题，marker 词也带话题依赖；移植含目标生成历史，仍非纯 persona 变量。建议多角色多主题交叉设计、冻结 token 历史、长程衰减测试。可信度 2.5/5；机构与方向强，不等于泛化证据强。

## 6. Novelty 与证据置信度

- 主观 novelty：**4/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**2.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

