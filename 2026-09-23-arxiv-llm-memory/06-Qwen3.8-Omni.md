# Qwen3.8-Omni：百万上下文与多模态 Agent Memory

- arXiv：[2609.25611](https://arxiv.org/abs/2609.25611)；[官方 PDF](https://arxiv.org/pdf/2609.25611)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Qwen Team；Alibaba
- 机构优先级：S（头部公司；宽相关但系统启发强）
- 研究标签：multimodal memory、long context、agent harness、latent/recurrent state

## 1. 做了什么

Qwen3.8-Omni-Flash 是原生文本/图像/音频/视频的 MoE agent 模型，支持 1M token，并发布 Qwen-MM-Plugins 与 Qwen-Live-Harness。与本专题最相关的是 Omni-Memory：把长音视频转为可延迟加载的结构化摘要与片段索引。

## 2. 怎么做、实验如何设计

backbone 结合 Gated DeltaNet 固定状态与稀疏 attention；预训练原生 256K，再扩展至 1M。四阶段预训练包括 encoder 对齐、约 2.5T multimodal tokens 全参训练、QSA indexer warm-up 与 sparse training；post-training 用 multi-teacher distillation 与统一 RL。实验覆盖 29 个音频、视听推理与 agent tasks，并展示长视频按需检索、meeting agent、工具使用等系统任务。

## 3. 结论

论文报告相对 Qwen3.5-Omni-Plus 在 29 项评测平均提升超过 25%，每小时音频/视听估算输入成本下降超过 98%/93%。作者把实时多模态交互明确视为 context、memory、tool 和 delegation 的系统协同问题。

## 4. Future impact

未来 memory system 很可能不是单一向量库，而是“摘要层—按需原始证据—可执行 skill”的多层对象；Omni-Memory 提供一个工业级参考架构。

## 5. Critical thinking

报告强但自评属性明显：训练数据、模型规模和不少 benchmark 细节难以完全复现；1M window 不等于有效记忆。需要把 Omni-Memory 与等成本 frame sampling、RAG、摘要缓存比较，测 evidence recall、时间定位、跨会话更新与错误累积，而不是只看整体产品任务。API 成本估算也不等同真实延迟与 GPU 能耗。

## 6. 可信度判断

- 评分：4/5
- 依据：24 页技术报告，架构/训练/应用和多项结果较完整；框架公开，但权重与数据可复现性仍有限。
- 优点：机构强、系统完整、多模态 memory 设计实际。
- 局限：自报告 benchmark 多；memory 组件缺少独立、严格消融。

