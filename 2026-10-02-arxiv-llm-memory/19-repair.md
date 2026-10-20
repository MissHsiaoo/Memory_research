# 19 — Not All Is Lost: Repairing Lossy User Preference States of Personalization Encoders

- arXiv：[2610.01270](https://arxiv.org/abs/2610.01270)；[官方 PDF](https://arxiv.org/pdf/2610.01270)；[本地 PDF](./2610.01270.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Parthiv Chatterjee 等；Dhirubhai Ambani University、Indian Institute of Technology Delhi。PDF 注明为已接收 NeurIPS 2026 的作者存档稿。
- 机构优先级：**B，黑马/启发性补充；机构排序低于头部实验室**；研究标签：`personalized memory` `preference encoder` `state repair`
- 证据范围：核读 PDF 方法、实验与 Discussion/Limitations；数字为作者报告。

## 1. 做了什么

指出用户偏好压缩状态可能丢掉信息，但原编码器各时间步缓存里仍保留可恢复证据；在不重训主模型的情况下修正偏好状态。

## 2. 怎么做、实验如何设计

REPAIR 比较当前压缩状态与冻结编码器产生的时间步缓存，在紧凑坐标空间里挑选长期、近期、局部突发的纠偏信息，聚合后加回任务头输入。MovieLens、PENS、MIND、Amazon Reviews 2023 等数据，12 个推荐 host 均只训练 REPAIR，编码器/任务头冻结；Mamba4Rec 在 MovieLens 上 MRR +3.96 点，对照只微调 head +0.19。论文另测个性化生成。作者明确报告缓存参数内存增加 31–36%、延迟增加 38–44%。

## 3. Conclusion

“偏好状态丢失”与“历史证据完全不可得”不同；已有时间步表征可以事后修复压缩误差。

## 4. Future impact

可用于修补已部署个人化模型的 latent user state，无需回放或重新训练全量历史。

## 5. Critical thinking

**推断：** 缓存本身有隐私和空间成本；编码器从未看见的证据无法恢复。应测试长期偏好反转、概念漂移、不同用户数据删除请求，并比较等内存的直接保留原历史方案。

## 6. 可信度判断

**4/5。** 多数据集、12 host、冻结强对照及透明开销使证据较扎实；机构优先级低不降低方法可信度，线上因果收益仍需验证。
