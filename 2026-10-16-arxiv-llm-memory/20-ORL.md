# 20. ORL：扩散语言模型的在策略残差上下文学习

- 论文：[arXiv:2610.20687](https://arxiv.org/abs/2610.20687) · [官方 PDF](https://arxiv.org/pdf/2610.20687) · 本地 PDF：`2610.20687.pdf`
- 公告：2026-10-16；初次提交：2026-10-14。
- 作者/机构：PDF 首页核验 Yifan Yu、Yuqing Jian 等；Together AI、UIUC、UC Berkeley、UC Santa Cruz、Stanford、UT Austin。**机构优先级 P2**。
- 主题：diffusion LLM；residual context；on-policy learning。证据范围：全文 36 页。

1. **做了什么（论文证据）**：提出 ORL，学习在扩散去噪步之间携带预测分布的 residual context，以改善速度—质量前沿。
2. **怎么做与实验（论文证据）**：从模型自生的残差轨迹在策略训练，配熵收缩目标；系统层实现异步残差捕获/传输、分块注意力与打包平衡训练。测由 Qwen3-4B 转换的 4B DLM、LLaDA-2.1-mini、DiffusionGemma，并与推测解码比较。
3. **结论（论文证据）**：4B 模型每前向 token 数最高 +6.2 倍，配套运行时端到端吞吐约 +6.9 倍且质量相近/更好；在所测单请求 H100 设置下匹配准确率比 DFlash 快 1.74 倍。其他 DLM 的增益幅度不同。
4. **未来影响（我的推断）**：扩散 LLM 的跨步预测分布是一种隐式计算记忆，训练与运行时需协同设计；不等同跨会话用户记忆。
5. **Critical thinking**：增益混合算法与专门 runtime、量化/硬件设置，需拆解独立贡献；测试批服务、多 GPU、长输出和不同准确率阈值。
6. **可信度 4/5**：多模型、系统与质量匹配比较较完整；性能结论高度依赖基准、运行时和单请求设置，不能泛化为所有 dLLM 服务。
