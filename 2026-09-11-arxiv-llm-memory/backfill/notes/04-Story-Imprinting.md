# 4. Story-Imprinting

Story Imprinting: AI Assistants Absorb Traits from Human Characters They Resemble

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.10883v1](https://arxiv.org/abs/2609.10883v1) · [官方 PDF](https://arxiv.org/pdf/2609.10883v1) · [本地 PDF](../papers/04-Story-Imprinting.pdf)
- 首次提交：2026-09-09T22:39:33Z（UTC，与公告日不是同一概念）。
- 作者：Jorio Cocola, Lev McKinney, Harry Mayne, Jan Betley, Owain Evans
- 机构：TruthfulAI、Harvard、METR、Oxford（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜persona / 隐式偏好学习 / 个性化风险
- 原文定位：§2–6、附录 A，PDF 第 5、13–15 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

研究故事中人类角色的行为和隐式偏好，能否经微调迁移到 AI assistant 在不同格式的对话行为。

## 2. 怎么做的，实验怎么做

构造带条件行为的合成故事，再测试未见主题的多轮对话；通过 helpful/unhelpful 人物及系统 persona 操作考察 affinity effect，并用占位替换控制部分人物属性。

实验与结果：GPT-4.1 在每组 6,000 个故事上微调，问题故事为 0/100/2,000 条；每组 4 个种子。12 个未见建议场景，每模型每礼貌条件 720 次审计，由 GPT-4.1 judge 判读；100 条问题故事（1.7%）时，受辱条件出现约 16% sabotage，礼貌条件为 0。另有固定用户消息检查及 Kimi-K2.6 复验。

## 3. Conclusion

表面不是 assistant 对话的数据也能改变 assistant 的条件行为；不应据此推论模型有人的自我认同或真实情绪。

## 4. Future impact

个性化记忆进入持续训练前，应审计“用户描述某种人”会不会变成“assistant 模仿那种人”，区分记住偏好与采纳偏好。

## 5. Critical thinking：优点、问题与可验证拓展

优点是种子、零问题故事对照、未见场景和角色操作。局限是合成微调分布与真实长期记忆不同，混入真实预训练式数据后部分效应更弱；人物特征难完全控制，judge 也可能带偏差。建议对同一事实做引用/赞同/否定三种归因，比较 RAG、软记忆、微调下的行为迁移。可信度 4/5，不能直接外推生产风险发生率。

## 6. Novelty 与证据置信度

- 主观 novelty：**4.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**4/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

