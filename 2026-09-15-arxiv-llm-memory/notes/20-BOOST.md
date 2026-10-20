# 20. BOOST: Concurrent Access to Host Memory and HBM to Accelerate LLM Inference

- arXiv：[2609.13592v1](https://arxiv.org/abs/2609.13592v1) · [官方 PDF](https://arxiv.org/pdf/2609.13592v1) · [本地原文](../papers/20-BOOST.pdf)
- 正式公告：2026-09-15；首次提交：2026-09-11（两者不是同一字段）。版本：v1。
- 作者：Anish Saxena , Jae Hyung Ju , Hritvik Taneja , Po-An Tsai , Aamer Jaleel , Christos Kozyrakis , Moinuddin Qureshi
- 首页核验机构：NVIDIA Research；Stanford；Georgia Tech。
- 机构优先级：A：强机构主榜（无普通机构补位）。机构只决定阅读优先级，不代替证据评分。
- 研究标签：弱相关但具启发性｜LLM serving；物理内存分层
- 主观 novelty：4/5；证据可信度：4/5（不是概率）。
- 阅读范围：设计、系统设置、主实验、容量匹配与带宽分析；未实测硬件。

本笔记基于以上官方原文；第1–3节为论文内容及结果口径，第4–6节为阅读者判断，不能当作作者已验证的结论。未进行实验复现或代码审计。

## 1. 做了什么（论文报告）

让GPU的HBM与CPU主机内存同时为LLM decode提供数据，而不只是把主机内存当低速溢出区。注意这里memory指物理内存，不是用户经历或语义记忆；入选依据是强机构的系统设计启发。

## 2. 方法与实验设计（论文报告）

PAM按GPU执行wave分布权重，使主机与HBM访问并行；DSR动态管理KV缓存和空闲内存池，在相同kernel基础上修改约800行vLLM。实测GH200具有96GB HBM、480GB主机内存，HBM与CPU到GPU测得带宽约3330和350GiB/s。主要测Qwen3-Next-80B-FP8、Llama3.3-70B，另测张量并行Qwen2.5-72B及合成输入长度；部分更高带宽比例由H100仿真，不是额外实物平台。

## 3. 结论与结果边界（论文报告）

同batch下平均每输出token时间改善约4.3%；高吞吐设置相对HBM-only平均提升31%，相对prefetch约15%。收益同时含容量与带宽，不能全算成并行读的贡献。容量匹配的91.2GB、batch10实验，HBM基线344tokens/s与29ms，对照BOOST359tokens/s、27.9ms，增益约4%。

## 4. Future impact（我的推断）

对大型agent部署，长期KV状态、模型权重和并发数争夺物理内存；分层记忆必须联同真实带宽与调度考虑。可把热用户状态、冷记忆向量与权重做不同布局，但论文没有测试个性化记忆检索，迁移部分只是系统层面的研究设想。

## 5. Critical thinking（我的分析与建议）

headline吞吐提升应拆成同容量、同batch、同延迟目标三个比较，否则容易把多装几条请求解释为每条请求更快。主机互联尤其重要，GH200结果不能直接搬到普通PCIe机器。建议报告prefill、TTFT、p95延迟和多租户抢占，并用真实agent长短交错流量检查；还应核验精度与kernel变动是否完全不影响输出。

## 6. 可信度、优点与局限（主观评估）

4/5。优点：实物硬件结果、容量匹配分析、明确区分不同收益来源，工程改动集中。局限：硬件与互联依赖强，主要聚焦decode与合成负载；仿真带宽点不是额外硬件验证，服务SLO、混合预填充和记忆检索流程尚未覆盖。它值得借鉴，但不是latent memory算法论文。

## 来源与审计

[官方摘要页快照](../sources/2609.13592-abs.html)记录日期和版本；[本日入选核验](../verification.json)保存公告主分类、PDF页数与SHA-256。[返回日报](../README.md)。
