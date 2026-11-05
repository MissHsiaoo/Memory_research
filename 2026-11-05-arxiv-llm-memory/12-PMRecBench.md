# 12. PMRecBench: A Benchmark for Personalization in Recommendation Agents under Multimodal Queries

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06349)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06349)；[仓库内 PDF](pdf/2611.06349.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Zhang, Xiaoyu；Lyu, Yougang；Wu, Bin；Bulathwela, Sahan；Yilmaz, Emine
- 机构：首页署名已核验：University College London；University of Amsterdam。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：personalization; multimodal recommendation。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–6；已获取完整13页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

将多模态需求理解与用户偏好遵循拆开测量，避免随机候选集把看懂图片误当作个性化。

## 2. 怎么做、实验如何设计

基于Amazon衣物和MovieLens记录，按用户时间70/30切分，用历史构造图片需求、未来高评分项作目标。510查询、377用户；30候选诊断池加入5个偏好匹配但违反需求项，以及5个满足需求却不受偏好项。分别测NDCG、需求理解U、偏好遵循P；多种推荐/通用agent与8个backbone。

## 3. 结论

诊断池使NDCG@1较随机池下降约0.20–0.26；U可达0.85–0.95，而P仅0.71–0.84。保持个人信号及竞争项不变，加入多模态查询使P平均下降0.046/0.042（衣物/电影），用户级配对bootstrap区间不跨零。

## 4. 未来影响

推断：很适合多目标记忆使用：同时测当下硬条件与历史软偏好，揭示二者竞争，而非只报一个推荐分。

## 5. Critical thinking

部分负候选来自未交互项，未评分不必然讨厌；属性抽取、可见性筛选与合成查询可能引入偏差。U/P是相对排名代理指标，不是认知能力的直接观测。建议增加用户确认负例、自然对话查询、偏好变更和反事实换用户实验，报告候选池构造敏感性。

## 6. 可信度判断

4/5。时间切分、诊断对照和用户级bootstrap清晰；仍是有限域构造推荐任务，非开放世界个性化验证。

## 官方提交记录

Submission history From: Xiaoyu Zhang [ view email ] [v1] Wed, 4 Nov 2026 11:10:03 UTC (2,453 KB)
