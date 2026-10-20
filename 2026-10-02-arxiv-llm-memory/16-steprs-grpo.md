# 16 — Exploring More, Reasoning Better: Stepwise Risk-Sensitive GRPO for Diffusion Language Models

- arXiv：[2610.00661](https://arxiv.org/abs/2610.00661)；[官方 PDF](https://arxiv.org/pdf/2610.00661)；[本地 PDF](./2610.00661.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Yue Yu 等；Indiana University、University of California Riverside
- 机构优先级：**A+，研究型高校合作**；研究标签：`diffusion LLM` `RLVR` `reasoning diversity`
- 证据范围：核读 PDF 方法、实验；结论为作者报告。

## 1. 做了什么

在 diffusion LM 的逐步去噪训练中，不再把终局奖励无差别分摊给每个状态，而是按阶段调整风险敏感性。

## 2. 怎么做、实验如何设计

StepRS-GRPO 在不改底层 rollout、验证器、优化器和参考正则的前提下，让组优势变换的系数随去噪状态变化；二元奖励时推导为提示/状态依赖的中心化奖励缩放。PDF 在 SDAR-1.7B/4B 等扩散模型、数学推理基准上测 pass@1、pass@k 和答案/推理链多样性；做端点、插值、优势 RMS 匹配等消融，报告准确率与覆盖率均优于中心化 GRPO。

## 3. Conclusion

扩散模型不同去噪阶段的探索价值不同，终局奖励也应按状态分配。

## 4. Future impact

若泛化到行动扩散代理，可更好平衡早期探索和后期收敛。

## 5. Critical thinking

**推断：** 数学可验证任务奖励干净，开放式代理中的噪声奖励会改变最佳风险日程。应在代码/工具任务、不同 block 长度及相同训练计算下复测，报告多样性增加是否真正改善最终选择。

## 6. 可信度判断

**4/5。** 数学推导、两规模底模和质量/多样性消融是优点；跨任务奖励鲁棒性未定。
