# 05. MemOnce: A Scalable Memory Architecture for Large Language Models

- [arXiv 摘要](https://arxiv.org/abs/2611.27973) · [官方 PDF](https://arxiv.org/pdf/2611.27973) · [本地 PDF](pdfs/2611.27973.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Nie, Chang; Fu, Chaoyou; Liu, Songlin; Hu, Yiqing; Shan, Caifeng。
- 机构：首页署名核验，Nanjing University、University of Science and Technology of China。机构层级：B：强研究型高校/实验室。
- 研究标签：latent memory；KV decoding；sparse retrieval。
- 阅读依据：已下载并解析完整 28 页 PDF，目视核验首页；本评析重点核读 §2–4、表1–6、§5局限，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：历史只缓存少量末层隐藏状态；需要时将检索到的紧凑表示解码为各层KV。检索索引跨层复用，试图兼顾可扩展历史容量与固定活跃显存。

## 2. 怎么做、实验如何设计

组合memory encoder-decoder和memory sparse attention，默认压缩比8、检索64个memory chunks。从零预训练对比统一FineWeb-Edu配置的0.15B–1B架构；后训练适配Qwen3.5的2B/4B，生成时冻结基座，训练轻量投影与编码阶段LoRA。评测MemBench、LoCoMo、LongMemEval、PersonaMem-128/1M，以及通用能力、检索和重排；报告H100服务器效率。

## 3. 结论

论文证据：4B五项记忆均分60.07 vs全上下文54.30，提升5.77个百分点；但LoCoMo是67.01 vs69.55，未逐项全面胜出。2B在LoCoMo和LongMemEval也低于全上下文。1M上下文报告1313倍state-cache压缩、6.9倍prefill加速与3.5倍吞吐；这些数字对应特定缓存口径/配置，不能解释成总系统内存缩小1313倍。32K记忆负载下通用均分65.98 vs65.88。

## 4. 未来影响

研究判断：这是本批次最值得复现的原生潜在记忆架构。把“编码一次、按需恢复多层上下文”与检索联合训练，提供了外部文本RAG之外的路径。

## 5. Critical thinking

必须区分constant active memory与不断扩展的历史pool，总存储并不自动恒定。稀疏检索可能漏掉跨片段组合证据；单裁判准确率需人工校准。作者承认从零预训练仅到1B，长程编码/工具交互尚待验证。建议在相同CPU存储、传输、端到端延迟预算下比较RAG、全上下文及固定状态模型；加入偏好冲突更新、删除、跨目标共用记忆和反事实纠正，逐项报告召回损失。

## 6. 可信度判断

4/5。覆盖预训练、适配、记忆QA、通用能力与效率，有较全面表格；缺少大规模预训练与真实持续agent证据，最高压缩数值和“无遗忘”需要严格限定口径。

