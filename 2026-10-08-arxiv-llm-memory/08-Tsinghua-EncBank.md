# 08｜清华：EncBank，把 LLM 内部状态压成跨查询复用的记忆

- 论文：[arXiv:2610.10058](https://arxiv.org/abs/2610.10058)｜[官方 PDF](https://arxiv.org/pdf/2610.10058)｜本地 `2610.10058.pdf`
- 正式公告：2026-10-08（cs.CL New submissions）；首次提交：2026-10-07 UTC，v1。作者/机构（PDF 首页）：Hanzuo Liu、Chunyu Liu、Chaofan Lin、Alex Lamb、Mingyu Gao；Tsinghua University。机构优先级：S；标签：latent memory、KV/state reuse、long-context inference；直接相关。

## 1. 做了什么

同一批文档被多个问题反复读取时，文本重播会重复编码；直接缓存内部状态又占巨大持久显存。EncBank 把 LLM 下层当可复用文档编码器，压缩其中间状态供适配后的上层读取，尝试在“重算”和“存储”之间找到更好的成本点。

## 2. 怎么做、实验如何设计

基于 CoMem 的中间层接口，预先抽取文档 hidden states；通过自蒸馏训练共享的 suffix adapter，且不同存储精度不需分别重训。PDF 用三个 Qwen 骨干、五组基准，比较原精度与 4-bit、同证据同适配器文本重播，以及固定 Qwen3-8B 工作负载的显存和 prefill 时间。还报告 Qwen3.8-27B 在 Terminal-Bench 2.1 的一个原精度配置表现。

## 3. 结论

4-bit 存储使各报告基准汇总分数距原精度通常不超过 1 点，固定工作负载中只占原精度持久 GPU 存储的 28.1%。但另一个原精度对照虽有 1.40× prefill 加速，相对文本重播却损失 3.12 点 RULER 准确率；这是清晰的质量/成本取舍，而非无损加速。

## 4. 未来影响（推断）

共享语料或长期 agent 文档记忆可存“可重用内部表示”而不是纯文本摘要；未来可与外部检索结合，决定哪些文档值得预编码、哪些按需读取。

## 5. Critical thinking

缓存 hidden state 与具体模型、层、适配器绑定；模型升级、文档删除或隐私要求都会增加维护成本。PDF 自述尚未联合优化深度和精度，缺少 eviction、动态更新、尾延迟、非英语和完整端到端收益测试。建议测多租户真实访问分布、缓存命中阈值及修改/删除后的失效传播，而不仅报告静态 benchmark。

## 6. 可信度：4/5

依据：已读 PDF 方法、受控速度/精度对照和 Limitations。优点是同时报告质量下降与资源收益，不掩盖负结果；局限是复杂准备成本、跨模型迁移和长时间维护还未验证。机构优先级与该证据评分独立。
