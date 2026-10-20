# 15. Kalman-Delta-Networks

Kalman Delta Networks: Uncertainty-aware Associative Memory

- 论文：[arXiv 2609.07816v1](https://arxiv.org/abs/2609.07816v1) · [本地 PDF](../papers/15-Kalman-Delta-Networks.pdf)
- 首次提交：2026-09-07（UTC）；arXiv 最新记录：2026-09-07。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Ngoc Bui、Tinglin Huang、Rex Ying
- 已核验机构：Yale University，Computer Science（PDF 首页署名）
- 机构优先级：A｜顶尖高校相关研究组。这是本次选刊层级，不是学校综合排名。
- 主题：latent associative memory / uncertainty / linear attention
- 主观 novelty：4.5/5；证据可信度：4/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–5；PDF 第 11–16 页、表 1、图 4。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**写入强度取决于已积累的记忆不确定性，而不只取决于当前 token。

## 1. 做了什么

将关联记忆建模为线性高斯状态空间，在 memory state 之外维护 uncertainty，由 Kalman gain 决定残差写入。

## 2. 怎么做的

完整协方差更新不利于 GPU scan，因此构造 diagonal 和 isotropic 近似；不确定性递推可表示为 Möbius map，以关联 scan 并行。Kalman 最优性只在相应线性高斯假设下成立，不是对一般语言记忆的无条件最优保证。

## 3. 实验如何设计，结果如何

750M/50B tokens 和 1.3B/100B tokens 两档，匹配 FineWeb-Edu 与训练方案；测 PPL、常识、RULER、JRT 检索。1.3B recurrent-only 均值：KDA 60.28、Diagonal KDN 60.45；hybrid KDN 并非每项最优。吞吐测的是 H200 上 mixer layer，不是完整服务。

## 4. Conclusion

显式跟踪 uncertainty 是有实证支持的 memory 更新方向，但领先强对照的某些均值差很小。

## 5. Future impact：对你的研究有什么启发

personalized memory 可维护每条隐式偏好的 belief precision，让一致反馈稳固记忆、冲突反馈触发更大更新；应与语义级置信度区别检验。

## 6. Critical thinking、优点、局限与置信度

优点：理论—近似—并行实现链条完整，强 recurrent baselines 和两档预训练。局限：近似 covariance 未必对应语义真实性，准确率小差距需要多种子显著性；kernel 速度不等于端到端收益。建议注入矛盾/噪声历史，测 posterior calibration 与错误写入恢复。可信度 4/5：方法扎实，但不能夸大当前百分点收益。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

