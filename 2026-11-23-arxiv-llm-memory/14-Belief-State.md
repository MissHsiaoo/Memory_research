# 14. Belief-State Management Meets Rubric Rewards for Agentic Forecasting

- [arXiv 摘要](https://arxiv.org/abs/2611.27286) · [官方 PDF](https://arxiv.org/pdf/2611.27286) · [本地 PDF](pdfs/2611.27286.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Chai, Jingyi; Liao, Yun; Lu, Hao; Zhang, Kemeng; Zheng, Bingyang; Ge, Yujie; Liu, Xiangrui; Zhang, Linfeng; Chen, Siheng。
- 机构：首页署名核验，Shanghai Jiao Tong University。机构层级：B：强研究型高校/实验室。
- 研究标签：working memory；belief state；multi-objective rubric。
- 阅读依据：已下载并解析完整 55 页 PDF，目视核验首页；本评析重点核读 §3–5、表1–2及理论假设，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：3/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：用主动fold工具把长搜索轨迹压成结构化belief state，再以不看最终事件结果的SEIPH过程rubric训练预测agent。把记忆压缩边界同时作为训练信用分配边界。

## 2. 怎么做、实验如何设计

状态含Foresight、Evidence、Search history、Todo；前后两项更新覆盖，证据和搜索历史追加。fold后丢弃原始当前段工具消息，保留问题与状态。SEIPH分别评搜索、证据、推理、概率、历史，严重编造/泄漏触发-1奖励；PPO/GRPO训练Qwen3.6-35B-A3B。测试FutureX三周、ForecastBench229已解决问题、Polymarket-Sim126问题，并比较ReAct、PBM、SFT与RL。

## 3. 结论

论文证据：PPO在ForecastBench Brier 0.151、Polymarket-Sim 0.147；同基座仅加PBM使后者0.221→0.193。市场参考仍更好（0.134），PPO Alpha=-0.012，不应称超越人类市场。PPO/GRPO准确率相同而Brier不同，凸显多指标评价。理论仅在理想mirror descent/校准局部reward假设下成立，不覆盖实际PPO clipping。

## 4. 未来影响

研究判断：是多目标memory使用的另一可借鉴协议：状态忠实性、证据质量和最终概率校准共同衡量。适合研究记忆压缩是否保留冲突证据和概率更新依据。

## 5. Critical thinking

关键混杂：表2的ReAct RL从base开始，PBM RL从SFT checkpoint开始，不能把全部差异归于fold或分段奖励。126题与高置信桶26个全对样本不足证明总体完美校准；追加证据也不保证长期定长。建议统一初始化与检索快照，多时间窗前瞻注册；测状态遗漏/失真与最终预测错误之间的因果链。

## 6. 可信度判断

3/5。有工具结构、独立无结果rubric和多基准，但初始化混杂、样本量、时间信息泄漏控制及裁判质量需要更强审计；本文分数反映证据局限，不随机构上调。

