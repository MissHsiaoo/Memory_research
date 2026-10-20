# 05 — Clock Diffusion: Efficient Semi-Autoregressive Continuous Diffusion Language Models

- arXiv：[2610.00894](https://arxiv.org/abs/2610.00894)；[官方 PDF](https://arxiv.org/pdf/2610.00894)；[本地 PDF](./2610.00894.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Yair Schiff 等；NVIDIA、Cornell University
- 机构优先级：**S，NVIDIA 与一流高校**；研究标签：`diffusion LLM` `semi-autoregressive` `KV cache`
- 证据范围：核读 PDF 方法、实验及基线；作者结论未独立复现。

## 1. 做了什么

让连续扩散语言模型支持变长生成和 KV cache，补上其相对自回归与离散扩散模型的实用性短板。

## 2. 怎么做、实验如何设计

给不同位置配置不同噪声时钟，形成块式或滑窗式半自回归连续扩散；Cache Grab 用高置信 token 提前提交与自推测解码加速。PDF 在 OpenWebText 比似然界，在 TinyGSM 训练后评估 GSM8K，并比较自回归、离散扩散及 LangFlow 等连续流模型；同时考察采样效率。

## 3. Conclusion

连续扩散 LM 可以在保留并行去噪的同时，获得实际部署所需的流式生成和缓存结构。

## 4. Future impact

若长程推理和工具调用继续保持优势，diffusion LM agent 的延迟及交互体验可能显著改善。

## 5. Critical thinking

**推断：** OpenWebText 似然与 TinyGSM 的改善不能直接代表真实助手质量；应在同参数、同训练 token、同墙钟成本下比较更强 AR 模型，并测试长回答、在线交互和缓存内存峰值。

## 6. 可信度判断

**4/5。** 完整参数化、多个基线和生成/推理两类指标是优点；更大模型与真实代理闭环仍需验证。
