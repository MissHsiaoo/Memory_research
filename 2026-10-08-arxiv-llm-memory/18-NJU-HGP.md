# 18｜南京大学：HGP 的端侧个性化混合图记忆

- 论文：[arXiv:2610.10071](https://arxiv.org/abs/2610.10071)｜[官方 PDF](https://arxiv.org/pdf/2610.10071)｜本地 `2610.10071.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-07 UTC，v1。作者/机构（PDF 首页）：Ran Zhou、Xueming Han、Jiaheng Liu、Yuyao Zhang、Fanyu Meng、Junlan Feng、Yuxiang Ren；Nanjing University、Jiutian Research。机构优先级：A；标签：personalized agent memory、graph storage、on-device；直接相关。

## 1. 做了什么

端侧个人助理既要理解用户长期轨迹，也不能每次都调用大模型做记忆路由。HGP 把情景、语义和程序性记忆以图分别存储，并用当前工作记忆记录状态轨迹与隐含约束，试图降低单向量检索混淆不同类型信息的问题。

## 2. 怎么做、实验如何设计

轻量 self-enhancement classifier 决定要走哪类个性化记忆；图结构保留人物、事件和任务依赖，逐步更新用户画像，工作记忆维持当前任务状态。PDF 在 LoCoMo 和 PAL-Set 两个长期记忆/个性化基准上评测，LoCoMo 依单跳、多跳、时间和开放域分类报告 F1、BLEU-1、Exact Match 及 LLM judge；PAL-Set 使用解决方案选择分数，比较现有记忆路线。

## 3. 结论

作者报告 PAL-Set 的 S-score 为 35.58，比最强基线高近 7 点；多指标显示混合图可改进个性化检索与推理。论文声称更适合端侧，但必须把模型调用、图维护和存储占用一起衡量，不能只以路由器轻量得出全系统轻量。

## 4. 未来影响（推断）

个人 memory system 可把“用户事实”“过去事件”“做事偏好/步骤”分开索引，再以图边连接；隐私要求高的本地助理尤其需要可检查和局部删除的结构化记忆。

## 5. Critical thinking

图抽取出错会制造持久错误边，复杂图维护也可能吃掉端侧节约；LoCoMo 只有十段多会话对话，远低于真实长期历史。建议在真实设备上测能耗、峰值内存、更新和删除时间，并对用户身份合并错误、偏好逆转和跨语言查询做压力测试；与同等预算的强向量/表格存储对照。

## 6. 可信度：3/5

依据：已读 PDF 架构、两基准与分类评测。优点是显式建模异构记忆与当前状态；局限是端侧效率的全面系统证据有限，公开长期个人化数据规模较小。
