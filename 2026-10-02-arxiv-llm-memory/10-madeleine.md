# 10 — Madeleine: Learning Involuntary Recall for Conversational Memory from Simulated Lives

- arXiv：[2610.01118](https://arxiv.org/abs/2610.01118)；[官方 PDF](https://arxiv.org/pdf/2610.01118)；[本地 PDF](./2610.01118.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Zhiyun Shi；Nanyang Technological University
- 机构优先级：**A+，一流研究型高校**；研究标签：`personalized memory` `associative recall` `query encoder`
- 证据范围：核读 PDF 方法、实验及 Limitations；数值为作者报告。

## 1. 做了什么

学习“用户当前话语会唤起哪段看似不相似的旧记忆”，减少每次读写记忆时依赖昂贵 LLM 联想。

## 2. 怎么做、实验如何设计

离线用 LLM 模拟人生事件，生成线索—触发记忆对；只训练查询编码器上的残差联想，并用同源负样本做对比，线上替换向量记忆的查询侧而不调用 LLM。LoCoMo-Plus 官方协议含 401 个联想题，论文报告接入 HyperMem 后得分 66.6；单独使用得分 52.4，接近原版 HyperMem 52.9，但零在线 LLM 调用、回答上下文约为其 1/21；另测试 T-Mem 迁移。

## 3. Conclusion

部分人类式“非自愿联想”可摊销进检索编码器，而不必每次在线推理。

## 4. Future impact

对个人化记忆尤其重要：从“相似语句检索”转向事件关系和生活过程先验。

## 5. Critical thinking

**论文局限与推断：** 模拟人生是英语且反映生成模型对典型生活的想象，文化/个体特异关联可能学不到。应在真实长期用户数据、跨文化场景及误联想损害测试，关注敏感记忆被无意唤起的隐私风险。

## 6. 可信度判断

**4/5。** 官方协议、成本拆分、迁移及明确局限是优点；端到端主要依赖单一专门基准。
