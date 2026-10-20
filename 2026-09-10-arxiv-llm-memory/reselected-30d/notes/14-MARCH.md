# 14. MARCH

MARCH: Scaling Recurrent Memory with Content-Routed State Anchors

- 论文：[arXiv 2608.12435v1](https://arxiv.org/abs/2608.12435v1) · [本地 PDF](../papers/14-MARCH.pdf)
- 首次提交：2026-08-12（UTC）；arXiv 最新记录：2026-08-12。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Ming Zhang、Kaisen Yang、Shu Yu、Ermo Hua、Ning Ding、Xia Hu、Bowen Zhou、Chaochao Lu、Youbang Sun
- 已核验机构：Shanghai AI Laboratory、Tsinghua、Fudan（PDF 首页署名）
- 机构优先级：A｜重点 AI 实验室＋顶尖高校。这是本次选刊层级，不是学校综合排名。
- 主题：latent memory / state-space models / content routing
- 主观 novelty：4/5；证据可信度：3.5/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–5；PDF 第 7–11 页、表 1–4。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**保存 recurrent state 的历史锚点，再按内容路由读取，连接固定状态与可增长外部记忆。

## 1. 做了什么

周期性缓存累计 recurrent state，以轻量 key 标记 anchor；当前 token 生成 query，从历史 state anchors 与当前 state 聚合信息。

## 2. 怎么做的

默认每 512 token 存一个 anchor，routing dimension=64；稠密或 Top-4 读取在历史分辨率与成本之间折中。它允许 memory bank 随历史增长，因此不是严格常量空间。

## 3. 实验如何设计，结果如何

约 793M recurrent 模型，从头训练 50B tokens、16K 窗口；比较 Gated DeltaNet、Log-Linear variant 和两档匹配 Transformer。常识均值 40.1→41.5；LongBench 均值 11.9→14.9，但接近参数量的 Transformer 得 15.4。另测 RULER 和六套真实检索，32K 为长度外推。

## 4. Conclusion

内容路由的 state 缓存补强 recurrent 检索，同时增加缓存和路由开销；“更强 memory”不能只从相对提升推断绝对能力。

## 5. Future impact：对你的研究有什么启发

很适合构造分层 latent memory：短期状态负责近期信息，长期锚点保存重要阶段，再学习什么时候存/读/合并。

## 6. Critical thinking、优点、局限与置信度

优点：匹配数据与训练预算，公开容量间隔消融，测试自然语言与合成检索。局限：anchor 增长后总成本不再是纯 recurrent，长窗口优势需与同字节预算 KV 压缩比较。建议固定 state bytes 和训练 FLOPs，加入学得的事件锚点选择与非均匀时间采样。可信度 3.5/5：设计清晰，长期增长的可扩展性仍需测试。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

