# 12. JPEG-DLM

- 论文：**One Latent, Many Tokens: Jointly Learning Compressed Embeddings for Efficient Language Diffusion**
- arXiv：[2609.33698](https://arxiv.org/abs/2609.33698)；[官方 PDF](https://arxiv.org/pdf/2609.33698)
- 提交日期：2026-09-27；正式公告批次：2026-09-29（北京时间）
- 作者/机构：**机构未核验**（官方 HTML 未提供可可靠解析的首页机构行，未作推测）
- 机构优先级：**C｜机构未核验，按方法启发性收录**
- 研究标签：diffusion LLM、latent compression、flow matching、efficient generation
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

JPEG-DLM 用一个 latent 表示多个 token，并把压缩空间和生成模型联合学习，避免固定 embedding 空间难去噪、难解码的问题。

## 2. 怎么做、实验如何设计

框架包含 context compressor、共享权重网络和 decoder：JEP 从受损压缩视图预测干净目标 embedding，flow matching 学习连续去噪，feature reconstruction 与 token CE 负责可逆解码。LM1B 与 OWT 上，在 0.5 压缩率时报告 Gen-PPL 34.52 和约 2.3 倍吞吐，并与多种 diffusion/flow baseline 比较。

## 3. 结论

语言 diffusion 的状态长度可以在 latent 层压缩；关键不是事后压缩，而是让压缩器与生成动力学共同塑造可预测表示。

## 4. Future impact

这可降低 dLLM 的序列长度成本，也可能启发 latent memory：一组历史 token 由一个可生成、可解码的状态表示。

## 5. Critical thinking

压缩带来的吞吐很有吸引力，但 Gen-PPL 不足以衡量推理与事实保持；decoder 也可能把不确定性隐藏在表面流畅性中。应增加长依赖、精确复制、结构约束、推理 benchmark 与端到端显存/延迟测量。

## 6. 可信度判断

**3.7/5。** 全文方法和语言建模实验完整，但机构无法核验，任务更偏基础生成，尚未证明压缩 latent 对复杂 reasoning 无损。

