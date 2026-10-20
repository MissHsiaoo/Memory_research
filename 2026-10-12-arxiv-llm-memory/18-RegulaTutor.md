# 18 RegulaTutor：带证据链的长期个性化教学

- 论文：[arXiv:2610.13399](https://arxiv.org/abs/2610.13399) · [官方 PDF](https://arxiv.org/pdf/2610.13399) · [本地 PDF](2610.13399.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Yonggang Li、Boqian Han、Rui Sheng、Yushi Sun、Zixin Chen。机构：Hong Kong University of Science and Technology、Chinese University of Hong Kong（PDF 首页核验）。
- 机构优先级：B（一流研究型高校）；研究标签：personalized memory、learner history、LLM personalization。

1. **做了什么｜论文证据：**提出 RegulaTutor，将学习者长期记录、基于证据的理解和教学策略显式衔接。
2. **怎么做、实验如何设计｜论文证据：**用 SRL/CAMM 维度形成认知、情绪、元认知、动机解释与教学策略，保留证据链接并随新观测更新；PairRoute 根据中间轨迹区分 harness 与模型错误。在 LongTutor 的 1000 个人人工标注样本、每例 199 条学习记录上比较证据获取、诊断和模型判定的教学质量，并做组件与交叉版本测试。
3. **结论｜论文证据：**论文报告历史证据准确性、学习者诊断及部分配置教学评分改善；没有测出真实学生长期知识保持提升。
4. **未来影响｜我的推断：**个性化记忆应带解释寿命和证据来源，避免旧错题永久决定教学策略。
5. **Critical thinking｜我的推断：**论文局限明确指出独立历史快照、模型评委可能同族、开发集复用与优化预算不匹配。建议真实学生随机试验，测数周保持/迁移及错误画像的撤销速度。
6. **可信度：3/5。**依据：核查 1000 样本设置与作者局限；优点是可追踪教学决策，局限是教学效果主要靠离线/模型判分，缺真实学习结局。
