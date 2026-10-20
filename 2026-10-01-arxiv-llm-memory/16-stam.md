# 16 — Personalized State-Transition-Aware Memory for Clinical Agents

- arXiv：[2609.38490](https://arxiv.org/abs/2609.38490)；[官方 PDF](https://arxiv.org/pdf/2609.38490)；[本地 PDF](./2609.38490.pdf)
- v1 提交：2026-09-29；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Maryam Haghifam 等；University of California Los Angeles、Optum AI/UnitedHealth
- 机构优先级：**A+，一流高校与产业研究团队**；研究标签：`personalized memory` `state transition` `clinical agent`
- 证据：已核读 PDF 方法、实验与结论。医疗场景仅作研究解读，不作为临床建议。

## 1. 做了什么

为纵向临床 agent 建立感知患者状态变化的记忆，而非把病历当作不断累积、同等有效的旧事实集合。

## 2. 怎么做、实验如何设计

Active/History 双存储配合带类型的临床关系图；用语义检索和状态转移识别组织事实，再由查询条件控制历史证据门。四个纵向临床基准、Qwen3-4B 与 GPT-5 读取模型，对比追加式和相同上下文预算的记忆方案。作者报告多个配对证据条件下显著获益，部分指标仅数值上更好，因此不能概括为所有任务均显著提升。

## 3. Conclusion

个性化记忆需要显式表达“事实何时变了”，而不是只压缩/检索更长病史。

## 4. Future impact

状态转移、有效期和历史追溯机制可迁移到一般用户偏好记忆，比如地址、职业和阶段性目标变化。

## 5. Critical thinking

**推断：** 自动判定“旧事实失效”在医疗中可能把相互矛盾的记录误删或误覆盖。应做临床人员盲评、事实来源追溯、时间戳缺失/冲突压力测试；写入侧主要使用较小模型，需检验跨模型鲁棒性。

## 6. 可信度判断

**3.5/5。** 纵向任务、匹配上下文对照和显著性分析是优点；高风险场景需要真实数据外部验证与安全审查。
