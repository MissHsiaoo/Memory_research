# LADDER: Graph-Guided Diffusion Language Models for Efficient Multi-Hop Reasoning

- arXiv：[24346](https://arxiv.org/abs/2609.24346)；[官方 PDF](https://arxiv.org/pdf/2609.24346)
- arXiv 初次提交：2026-09-21（v1）；正式公告归属：2026-09-22 新稿，二者不可混同。
- 作者：Senlei Zhang , Linhao Luo , Qian-Wen Zhang , Siyu An , Junnan Dong , Shuhao Zhang , Xing Sun（arXiv 官方列表）
- 机构：Tencent Youtu Lab；华中科技大学；Monash University（论文 PDF 首页核验）
- 机构优先级：A｜顶级产业研究
- 研究标签：diffusion LLM；GraphRAG；多跳推理；直接相关
- 证据说明：以下数值均为论文自身报告；“我的推断/建议”并非论文实证。

## 1. 做了什么

LADDER 把检索图谱嵌入扩散语言模型的逐步去噪过程：草稿中出现新实体时触发检索，再让后续填空使用证据。它探索了 dLLM 与传统“生成前先检索完”的不同交互时序，直接相关于 diffusion LLM 和外部记忆。

## 2. 怎么做，实验怎么做的

作者在部分生成文本中检测实体，按需异步请求图证据，并将结果回填去噪轨迹；以 Dream-7B 扩散模型和匹配监督微调的 Qwen2.5-7B 自回归模型做比较。HotpotQA、2Wiki、MuSiQue 三基准的论文表 2：LADDER 平均 EM/F1=45.2/54.6，耗时 2.79 秒；YoutuGraphRAG 自回归方案 42.1/50.1，12.71 秒。对比 Dream 版 GFM-RAG 的 39.6/47.4、11.30 秒也较强。MuSiQue F1 为 30.7，略低于 YoutuGraphRAG 31.1，非处处领先。

## 3. Conclusion

在所设模型和环境下，扩散时动态证据注入显示了有效且较快的多跳推理；质量优势与时间优势均受模型、检索实现和硬件设置影响，不应泛化为所有 dLLM 优于 AR。

## 4. Future impact

后续可把“按生成不确定性触发检索”推广到个人记忆：仅当生成中出现可能依赖用户历史的实体/偏好时取证，或许同时降低延迟和过度个性化。此为外推。

## 5. Critical thinking

新实体触发是可解释的启发式，但可能漏掉代词、隐含关系和无实体的约束；错误早期草稿也会带偏后续检索。建议固定骨干、训练量、检索次数和证据库比较纯生成调度效应，报告每题调用数、异步失败率与 GPU 利用率。MuSiQue 细分弱项提示深链推理仍需改进；不能只看平均分。

## 6. 可信度判断、优点与局限

4/5：方法、消融与三基准结果已查；优点是结合扩散迭代和按需检索有原创性，计入时间；局限是跨架构因果比较难、个别数据集指标并不占优。
