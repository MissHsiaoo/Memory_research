# 06 — Hierarchical Continuous Diffusion Language Models

- arXiv：[2610.02193](https://arxiv.org/abs/2610.02193)；[官方 PDF](https://arxiv.org/pdf/2610.02193)；[本地 PDF](./2610.02193.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Hui Ren 等；University of Illinois Urbana-Champaign、Amazon.com, Inc.
- 机构优先级：**S，Amazon 与一流高校**；研究标签：`diffusion LLM` `latent state` `parallel decoding`
- 证据范围：核读 PDF 方法、实验；论文数值为作者报告。

## 1. 做了什么

尝试解决离散扩散模型并行解码时 token 独立采样、丢失联合依赖的问题。

## 2. 怎么做、实验如何设计

HC-DLM 将离散 token 读取与连续潜在轨迹耦合：潜态是唯一持久生成状态，每一步 token 从潜态读出，再反过来作为下一步潜态更新的支架；训练目标从 token 似然变分界推导。PDF 在 Sudoku、Countdown、LM1B 上同规模比较自回归、离散和连续/混合扩散基线，分别测谜题准确率与生成 perplexity。

## 3. Conclusion

“连续共享状态 + 离散 token 回馈”可在并行生成中部分恢复 token 间结构依赖。

## 4. Future impact

共享潜态可能为 diffusion LLM 的 latent memory 与全局一致性控制提供建模思路。

## 5. Critical thinking

**推断：** Sudoku 和 Countdown 结构明确、长度有限；共享潜态能否承载开放式长文本与长期代理状态未知。应检查不同长度、采样步数、上下文污染和推理延迟下的收益。

## 6. 可信度判断

**4/5。** 理论目标与三类任务比较相配；从小规模结构题外推至通用 LLM 尚需证据。
