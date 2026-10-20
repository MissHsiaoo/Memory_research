# 10 — STEPQuant: When and Where Errors Matter in Delta-Rule Recurrent State Quantization

- arXiv：[2609.38169](https://arxiv.org/abs/2609.38169)；[官方 PDF](https://arxiv.org/pdf/2609.38169)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Bingchen Yao 等；Zhejiang University、Tsinghua University、CAS、City University of Hong Kong、Harvard、CUHK
- 机构优先级：**A+**；研究标签：`latent recurrent state` `quantization` `serving memory`
- 证据范围：阅读全文；本地 PDF：[2609.38169.pdf](./2609.38169.pdf)

## 1. 做了什么

压缩 Delta-rule 线性注意力模型的持久 recurrent state，并针对误差的时间寿命和空间敏感度分配精度。

## 2. 怎么做、实验如何设计

STEPQuant 用 lifetime-aware bit allocation 处理长期累积误差，再按 key-row 输出影响和 value-column 分布联合拟合尺度。Qwen3.8-27B 与 Kimi-Linear-48B-A3B-Instruct 的长/短生成任务中，名义 6-bit 接近 FP32-state；其 4-bit 配置优于 uniform INT8。集成 SGLang 优化 kernel 后，recurrent-state 压缩超过 5×，总服务内存最多降 68.7%。

## 3. Conclusion

固定尺寸 recurrent memory 在高并发下仍是主要瓶颈；按“误差何时、在哪里重要”建模可安全进入低比特区间。

## 4. Future impact

这对 latent memory 的现实部署很关键：记忆机制若无法支持并发，算法优势很难转化为产品吞吐。

## 5. Critical thinking

“名义 6-bit”需结合元数据、混合精度 pivot 和 kernel 开销理解，不能直接等同端到端 6/32 压缩。应复核不同并发、序列长度、硬件和长时间状态漂移，且测试校准域外与在线状态分布变化。

## 6. 可信度判断

**4.5/5。** 两个真实大模型、长短任务、组件消融和 SGLang 实装使证据很完整。主要局限是硬件/模型覆盖仍有限，吞吐与功耗结果需独立工程复现。
