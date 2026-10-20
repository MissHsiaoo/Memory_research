# 17 — Reliable Parallel Decoding in Masked Diffusion Language Models

- arXiv：[2609.36452](https://arxiv.org/abs/2609.36452)；[官方 PDF](https://arxiv.org/pdf/2609.36452)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Zhenghao He、Bohan Liu、Guangzhi Xiong、Aidong Zhang；University of Virginia
- 机构优先级：**A**；研究标签：`diffusion LLM` `parallel decoding` `uncertainty`
- 证据范围：阅读全文；本地 PDF：[2609.36452.pdf](./2609.36452.pdf)

## 1. 做了什么

回答 masked diffusion LM 何时能可靠地一次提交多个 token，并提出训练免费的 RPD。

## 2. 怎么做、实验如何设计

诊断显示最终置信度不足以决定顺序：上游 mask 不确定时，下游高置信预测也会过早锁死答案；跨最后若干层保持稳定的预测更可靠。RPD 用 layerwise stability + final confidence 选候选，再用前序 mask 的累计熵预算控制提交。LLaDA/Dream 的数学和代码任务中取得所评方法最高吞吐，同时保持或提高准确率。

## 3. Conclusion

并行解码可靠性取决于依赖方向与跨层稳定性，而不仅是单 token 置信度。

## 4. Future impact

可成为 diffusion LLM 默认推理组件，也提供一种查看“模型内部何时已形成稳定答案”的方法。

## 5. Critical thinking

层稳定性可能只是模型/任务特定的校准代理，面对错误但一致的内部表征会失效。“最高吞吐”需结合硬件 kernel、batch 和 NFE 公平性。建议做跨架构零调参迁移、错误一致性案例和真实 wall-clock/能耗评估。

## 6. 可信度判断

**4/5。** 诊断直接导出算法，两个 diffusion 模型与两类任务支持结论。局限是缺少更广生成质量、安全与多语言实验，吞吐优势仍需系统级复现。
