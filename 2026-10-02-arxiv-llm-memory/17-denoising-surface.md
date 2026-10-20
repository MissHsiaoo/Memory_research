# 17 — Denoising Surface: Modeling and Predicting Inference Cost for Diffusion LLM Serving

- arXiv：[2610.00499](https://arxiv.org/abs/2610.00499)；[官方 PDF](https://arxiv.org/pdf/2610.00499)；[本地 PDF](./2610.00499.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Haoyu Zheng 等；Wuhan University、Shanghai Jiao Tong University、Hong Kong University of Science and Technology 等
- 机构优先级：**A+，一流高校合作**；研究标签：`diffusion LLM` `serving` `inference cost`
- 证据范围：核读 PDF 方法、服务实验；数字为作者报告。

## 1. 做了什么

把 diffusion LLM 的推理成本从单一“输出长度/去噪步数”改成块×去噪步骤的二维工作量表面。

## 2. 怎么做、实验如何设计

Denoising Workload Surface 给各块、各步的异质计算赋权；再用粗到细训练轻量 prompt-only 预测器，在 CPU 上预测请求成本，避免与服务 GPU 竞争。PDF 在 SGLang 上用 LLaDA2.0-mini/flash、NVIDIA PRO 6000 GPU 与 AMD EPYC CPU 测预测误差、跨硬件迁移和最短作业优先调度。论文报告相对标量预测器成本误差最多降低 2.50×，在线 chatbot 延迟最高改善 1.92×。

## 3. Conclusion

扩散 LM 服务调度需要能表达其二维去噪结构的成本模型。

## 4. Future impact

若 diffusion LM 进入实时个人助理，可使延迟预算、批处理与多轮交互资源分配更可预测。

## 5. Critical thinking

**推断：** 预测器若面对新采样器、混合任务或极端长输出，工作量形态可能变化。应分别报告尾延迟、公平性、队列饥饿风险，以及跨硬件转移时何种参数仍需重新校准。

## 6. 可信度判断

**4/5。** 真实 serving 栈、两种模型和端到端调度指标有价值；最高倍率依赖负载与硬件设定。
