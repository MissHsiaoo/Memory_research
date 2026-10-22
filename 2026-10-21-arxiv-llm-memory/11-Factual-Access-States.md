# 11. Factual Access States in Diffusion Language Models: From Mechanism to Knowledge Editing and Retrieval

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27580)；[官方 PDF](https://arxiv.org/pdf/2610.27580)；[仓库 PDF](pdfs/2610.27580.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Yuchen Guo , Zhuoyuan Mao , Yiwen Guo
- 机构（PDF 首页署名核验）：The University of Tokyo；LIGHTSPEED；Independent Researcher
- 机构优先级：P1B；主题相关性：直接相关；研究标签：diffusion LLM；knowledge editing；parametric memory
- 阅读证据：正文§2–3（PDF第3–7页）及附录G；首页。已获取完整 PDF（35页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

研究掩码扩散LM如何读取事实，提出多视角知识编辑，处理同一事实不同表述与正反查询。

## 2. 怎么做、实验如何设计

【论文直接证据】用原生MASK扰动做因果追踪；第0层attention与早期MLP联合恢复事实。编辑早期MLP而不改attention，平均关系掩码、上下文与反向查询keys，共享目标value。LLaDA-8B/Dream-7B，CounterFact、BAKE、QAEdit，对照ROME、约束微调和匹配单视角。

## 3. 结论

【论文直接证据】早期attention+MLP恢复效应约0.943；多视角改善复述与反向访问。作者明确指出自由生成仍弱：完全正确答案Dream23.8%、LLaDA17.6%，大部分编辑后回答仍错误。

## 4. 未来影响

【阅读者推断，尚待验证】参数记忆应按可访问的查询族而非单句写入成功来评价；适合为diffusion memory设计双向一致性指标。

## 5. Critical thinking

【阅读者评析与后续建议】宽窗口追踪的晚期峰可能只是冗余累积，不能直接理解成第二个存储点。编辑依赖结构化实体/关系span，不等于任意自然语言更新；key平均也可能抹平多模态查询差别。建议多次连续编辑、冲突事实、否定/时间边界和无关知识保持测试。

## 6. 可信度判断

**4/5**（与机构优先级独立）。有干预定位与匹配编辑消融，并主动披露低绝对正确率；尚不能视为可部署的可靠记忆写入。机构按首页原文保留，不把独立作者或邮箱推断成高校。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
