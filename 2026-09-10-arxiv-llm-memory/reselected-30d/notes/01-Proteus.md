# 1. Proteus

Proteus: Incremental Memory Activation for Long-Context Sequence Modeling

- 论文：[arXiv 2608.16844v1](https://arxiv.org/abs/2608.16844v1) · [本地 PDF](../papers/01-Proteus.pdf)
- 首次提交：2026-08-17（UTC）；arXiv 最新记录：2026-08-17。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Reza Bayat、Ali Behrouz、Vahab Mirrokni、Aaron Courville
- 已核验机构：Google Research、Mila（首页徽标及邮箱已核验；不是 Google DeepMind 署名）
- 机构优先级：A｜一线产业研究团队。这是本次选刊层级，不是学校综合排名。
- 主题：latent memory / recurrent memory / long context
- 主观 novelty：4.5/5；证据可信度：4/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §4–5；PDF 第 8–10 页、表 1–2；首页机构徽标。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**将可用记忆容量随上下文逐步开放，把“何时获得容量”作为独立设计变量。

## 1. 做了什么

在固定容量神经记忆中，早期 token 容易过度占用表示空间并干扰后续信息。Proteus 将 memory 划分为多个块，随序列推进逐步解锁；早期瓶颈促使压缩，后期新容量容纳新信息。

## 2. 怎么做的

已激活块参与读写，未激活块保持锁定；并非另建一个文本向量库。论文把这一调度接到 SWLA、Comba、Titans、Hope-Attention，默认 16 个分块。值得借鉴的是将容量调度与底层写入规则解耦。

## 3. 实验如何设计，结果如何

在 FineWeb 上以 760M/50B tokens、1.3B/100B tokens 两档从头训练，训练窗口 8K，固定优化设置；评估语言困惑度、常识任务及 RULER 单/多针检索。760M Hope-Attention 的常识均值由 53.15 到 53.99；16K UUID 检索由 50.0 到 54.4。改善有跨架构一致性，但并非每个单元格均提升。

## 4. Conclusion

证据支持“渐进激活通常改善这些中小模型的容量利用”，尚未证明任意长历史都能可靠记住，或 frontier 模型部署必然获益。

## 5. Future impact：对你的研究有什么启发

对 latent memory 的直接启发：研究 write/forget gate 之外，再学习一个 capacity-activation policy。长期个性化可为新阶段偏好预留容量，但这是我的迁移设想。

## 6. Critical thinking、优点、局限与置信度

优点：一个小机制能跨多类记忆架构验证，且有匹配底座的对照。局限：较长上下文上的提升仍伴随绝对检索率偏低；已知序列进度的调度如何用于无终点流不清楚。建议固定总 state bytes，比较均匀解锁、事件边界解锁、随机解锁与 surprise-triggered 解锁，并测早期/后期事实的遗忘曲线。可信度 4/5：核心实验可审查，缺少独立复现与大模型验证。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

