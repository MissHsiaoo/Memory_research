# 18 — NextMe-800: Anticipating Personal Behavior from Months of Egocentric Video

- arXiv：[2610.01461](https://arxiv.org/abs/2610.01461)；[官方 PDF](https://arxiv.org/pdf/2610.01461)；[本地 PDF](./2610.01461.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Zhaoxu Meng 等；The University of Hong Kong、Tongji University
- 机构优先级：**A+，一流研究型高校；弱相关但具启发性**；研究标签：`personalization` `egocentric memory` `behavior prediction`
- 证据范围：核读 PDF 数据、实验和讨论；它不是 LLM memory 系统论文。

## 1. 做了什么

建设跨月第一视角个人行为数据与预测基准，研究能否从长期生活历史预期未来行动。

## 2. 怎么做、实验如何设计

NextMe-800 约 800 小时，来自一名志愿者 126 天的 1Hz 图像、注视与音频，另配五层抽象字幕；NextAct 将其与多人 EgoLife 组合成约 1,500 点、开放词汇 K 步行动预测基准，用 embedding soft edit distance 评价不同模型的个人行为序列预测和不同时间跨度表现。

## 3. Conclusion

长期、多模态个人历史可作为行为预测的测试床，但“可预期某人行为”的证据尚受采样范围限制。

## 4. Future impact

对个性化记忆的启发是保存多尺度事件和习惯变迁，而非仅保留对话中的静态偏好。

## 5. Critical thinking

**推断：** 一人 126 天的主体数据易让模型记住个人规律，却不能证明跨人泛化；持续录制的隐私与第三方同意问题突出。应分人测试、按时间前后严格隔离并检验意外事件预测。

## 6. 可信度判断

**3/5。** 长时、多模态数据是优点；单一主体和与 LLM memory 的间接联系显著限制外推。
