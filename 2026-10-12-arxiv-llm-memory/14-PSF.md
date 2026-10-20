# 14 PSF：把扩散先验与 token 解码职责分开

- 论文：[arXiv:2610.12898](https://arxiv.org/abs/2610.12898) · [官方 PDF](https://arxiv.org/pdf/2610.12898) · [本地 PDF](2610.12898.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Jinjin He、Xinsong Feng、Lucheng Fu、Sinan Wang、Bo Zhu、Jiayun Wang。机构：Georgia Institute of Technology（PDF 首页核验）。
- 机构优先级：B（一流研究型高校）；研究标签：diffusion LLM、predictive states、parallel generation。

1. **做了什么｜论文证据：**提出 Predictive-State Flows（PSF），认为连续扩散先验应生成高层预测状态，而具体 token 由解码器完成。
2. **怎么做、实验如何设计｜论文证据：**将长度 L 的序列切成 K 块，以前文计算每块的预测状态；rectified-flow 生成状态序列，各块并行、块内自回归解码，将扩散状态数从 L 缩到 K。用 OpenWebText 无条件生成、197M 参数模型，对比生成困惑度、熵、MAUVE 与 TFLOPs，并比较预测状态/含本块信息的内容状态。
3. **结论｜论文证据：**K=8 设置下，论文报告生成困惑度 22.8、每 1024 token 0.31 TFLOPs，对照 ELF-B 的 24.0、7.2 TFLOPs；这是特定小规模生成条件下的结果。
4. **未来影响｜我的推断：**把离散细节从扩散先验卸载，可能为并行文本生成提供更好的计算—质量折中。
5. **Critical thinking｜我的推断：**块间预测状态若丢失长距细节，可能损害跨块一致性；生成困惑度也不能充分测推理能力。建议在长篇事实一致性、条件问答及硬件 wall-clock 延迟上复现，并固定等训练算力。
6. **可信度：4/5。**依据：核对设计、对照与计算量；优点是直接测试核心机制，局限是规模仅 197M 且未证明迁移到通用大型助手。
