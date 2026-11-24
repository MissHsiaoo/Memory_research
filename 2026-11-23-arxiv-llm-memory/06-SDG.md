# 06. SDG: State-Dependent Gating at Chunk Boundaries for Linear Attention

- [arXiv 摘要](https://arxiv.org/abs/2611.26637) · [官方 PDF](https://arxiv.org/pdf/2611.26637) · [本地 PDF](pdfs/2611.26637.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-10-16（来自官方 submission history，非公告日期）。
- 作者：Deng, Renjia; Liu, Yuxi; He, Yutong; Wang, Xue; Yuan, Kun。
- 机构：首页署名核验，Peking University、Meituan Inc.。机构层级：B：强研究型高校/实验室。
- 研究标签：recurrent memory；linear attention；forget gate。
- 阅读依据：已下载并解析完整 44 页 PDF，目视核验首页；本评析重点核读 §4–6、表1/4、边界诊断及理论假设，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：在chunk边界读出同层记忆的变化，生成逐元素遗忘门，而非只从当前token预测门值。保留chunk内部并行，折中状态反馈和高效训练。官方v1首次提交为2026-10-16，但本篇确实位于11月23日stat.ML的New submissions；不以提交日排除，也不将其当旧版本更新。

## 2. 怎么做、实验如何设计

对原生递推先计算chunk更新，再用ΔS、学习投影和正衰减函数生成Λ，对整个更新后状态逐元素衰减。chunk=64，Triton融合边界scan；四个1.3B骨干（GDN、KDA、GDN-2、Mamba-3）各用100B FineWeb-Edu tokens训练，配对共享数据顺序与初始化。测试困惑度、九项常识任务、RULER、六项真实检索和21项LongBench，并比较静态门、channel-wise门与不读同层历史的Ω输入。

## 3. 结论

论文证据：WikiText困惑度在四骨干均下降0.10–0.58；通用任务并非全部改善，BoolQ均下降。Ω控制恢复大部分收益：ΔS相对Ω只增加0.67点NIAH、0.02点真实检索，LongBench反降0.18；作者说明这些点估计没有不确定性证据。理论给的是固定上游状态分布下oracle收缩的潜在收益，不保证训练能学到该门。

## 4. 未来影响

研究判断：对latent memory最有价值的是“遗忘策略应看记忆状态”这一设计维度，以及保持并行性的边界实现。它可以与容量扩展或精确KV缓存结合。

## 5. Critical thinking

关键未决点是增益来自动态输入还是额外状态反馈。小幅ΔS–Ω差异不足以支撑强机制论断。缓存解码还需额外source-state矩阵，不能只按原生状态维度计算成本。建议多种子、相同参数/算力的Ω控制，增加长于训练长度的干扰与罕见事实保持任务，测边界处错误峰值和自由生成。

## 6. 可信度判断

4/5。配对训练、机制控制、融合实现和自我限制较扎实；主要差值偏小，无多种子支持，理论不直接证明经验因果机制。

