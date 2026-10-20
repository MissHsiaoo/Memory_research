# 8. MoNe

MoNe: Modular Neural Memory for Efficient Long Context Inference

- 论文：[arXiv 2608.17616v1](https://arxiv.org/abs/2608.17616v1) · [本地 PDF](../papers/08-MoNe.pdf)
- 首次提交：2026-08-18（UTC）；arXiv 最新记录：2026-08-18。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Wonguk Cho、Kyubyung Chae、Tribhuvanesh Orekondy、Sunghyun Park、Hyoungwoo Park、Jeongho Kim、Arash Behboodi、Kyuwoong Hwang、Sungrack Yun
- 已核验机构：Qualcomm AI Research（PDF 第 1 页脚注）
- 机构优先级：A｜成熟产业 AI 研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：latent memory / test-time learning / modular memory
- 主观 novelty：4/5；证据可信度：3/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–4；PDF 第 4–6 页、表 1、Limitations。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**给冻结 Transformer 外接快权重神经记忆，将长上下文写入与后续查询拆开。

## 1. 做了什么

长文本分段进入每层局部神经记忆，在测试时更新快权重；查询只从 query 生成记忆 keys/values，无需重新读取全部历史。

## 2. 怎么做的

冻结 backbone，添加约 6.4% 参数的模块，利用层级局部梯度写入。论文的 O(N) 预处理、O(1) 查询以历史长度 N 为参照；常数查询成本不等于无限容量，也不含无限增长的答案长度。

## 3. 实验如何设计，结果如何

使用 Qwen2.5-0.5B-Instruct，三种 RULER 任务：S-NIAH、MK-NIAH、Frequent Word Extraction；测试 4K–128K。128K MK-NIAH 得分 MoNe 0.94、RAG 0.71、ICL 0；但 ICL 已超过底座原生 32K 窗口。报告约 80% compute/峰值显存节省，训练过的记忆模块仍需计入准备成本。

## 4. Conclusion

在小模型的受控检索任务上展示了模块化神经记忆可行性，不能据此宣称通用长文理解或现实个性化已解决。

## 5. Future impact：对你的研究有什么启发

适合尝试 per-user memory module：共享底座、隔离用户快权重，复用多查询写入成本。还可以测试稀疏加载与增量编辑。

## 6. Critical thinking、优点、局限与置信度

优点：接口清楚，冻结底座易做原型，多查询复用有工程意义。局限：0.5B 和三种合成任务范围窄，substring match/目标词 recall 可能奖励冗长输出，超原生窗口对照偏弱。建议加入强长上下文模型、自然多跳 QA、矛盾更新和用户切换测试。可信度 3/5：原型有说服力，泛化主张需要更多证据。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

