# 17｜浙大等：记忆检索要“证据充分”，不只是每条都相关

- 论文：[arXiv:2610.09348](https://arxiv.org/abs/2610.09348)｜[官方 PDF](https://arxiv.org/pdf/2610.09348)｜本地 `2610.09348.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-07 UTC，v1。作者/机构（PDF 首页）：Yufeng Li、Shuxin Li、Zhenhua Xu、Junxian Li、Peng Zeng、Sheng Yao、Changting Lin、Gaolei Li、Ran Bi、Meng Han；East China Normal University、NTU、Zhejiang University、SJTU、USC、Northeastern University。机构优先级：A+；标签：long-term memory QA、retrieval sufficiency、multi-session evidence；直接相关。

## 1. 做了什么

长期记忆 QA 中，top-k 每条都“相关”仍可能共同缺少回答所需的第二事实，尤其是跨会话、多跳与时间问题。论文把检索目标从记录相关性改为证据集合的充分性，提出 Budgeted Flat Reconstruction（BFR）。

## 2. 怎么做、实验如何设计

第一阶段以 FCA-MS 将问题拆成信息需求，并从固定 flat memory store 中选覆盖这些需求的紧凑集合；第二阶段通过更深层文本搜索、实体/会话补充视图迭代取得未见记录，直到预算耗尽。另用盲化 LLM judgment、Gold Hit、Turn Hit 衡量证据覆盖。PDF 在 LoCoMo 与 LongMemEval-S 上固定存储与 answerer，对比 Mem0、A-Mem 等同库适配方法，并按单跳、多跳、时间问题分层报告。

## 3. 结论

在 LongMemEval-S 上，论文报告 judged accuracy 从 72.4% 到 82.2%，Turn Hit 达 91.4%；LoCoMo 的多跳类别相对同库基线也明显改善。证据显示检索集合结构比单条排序更重要，但 LLM judge 与人工可核验事实覆盖并非同一指标。

## 4. 未来影响（推断）

Agent memory retrieval 可先显式列出回答需要的事实槽，再检索互补记录；当集合仍不充分时主动找缺口，而不是继续堆相似摘要。这也可用于研究论文检索与多来源事实核验。

## 5. Critical thinking

问题分解错了会系统性漏证据，深度搜索又增加延迟/费用；如果记忆库本身未写入所需事实，BFR 也无能为力。建议将检索充分性与写入覆盖率拆开测，固定总 token 与工具调用预算，与更强重排器比较，并对不可回答问题测试拒答率与错误引用率。

## 6. 可信度：3/5

依据：核查 PDF 两阶段方法、同库对照和分类结果。优点是针对多条证据互补关系设计，受控比较较清楚；局限是部分结论依赖 LLM judge，检索成本与未知答案场景需要更严格测试。
