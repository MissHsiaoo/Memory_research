# 16. Tasklets: A Unit-Test Benchmark for Language Model Architectures

- [arXiv 摘要](https://arxiv.org/abs/2611.27607) · [官方 PDF](https://arxiv.org/pdf/2611.27607) · [本地 PDF](pdfs/2611.27607.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Zuhri, Zayd Muhammad Kawakibi; Nwadike, Munachiso Samuel; Inui, Kentaro; Aji, Alham Fikri。
- 机构：首页署名核验，Mila、MBZUAI、RIKEN AIP、Tohoku University。机构层级：B：强研究型高校/实验室。
- 研究标签：latent memory benchmark；recall；state tracking；multi-task。
- 阅读依据：已下载并解析完整 14 页 PDF，目视核验首页；本评析重点核读 §3–5、图1–2及训练/评测协议，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：将架构基础能力拆为7类16个合成任务，测召回、复制、参数记忆、计数、栈、形式语言、状态追踪。适合多能力memory单元测试，但不是自然语言长期用户记忆的完整替代。

## 2. 怎么做、实验如何设计

24种架构，每模型约15–20万参数，三学习率共1152次训练；每任务3000测试样本。比较softmax、delta-rule、diagonal RNN、nonlinear RNN和hybrid。recall每上下文重设映射，memorization固定10000个训练映射；多栈用4个独立栈。多数任务整样本exact-match，memorization/stack/flip-flop按token计分。测试为单次前向而非自由自回归，按验证loss选学习率运行。

## 3. 结论

论文证据：attention和部分delta-rule在召回/复制强，nonlinear RNN在模加法和置换组合更强；强召回不推出强state tracking。图1按>0.9准确率计解题数，PaTH 12、Transformer11；这只是该小模型与超参协议下的任务计数，不是大模型总体能力排名。

## 4. 未来影响

研究判断：你关心多目标memory时，可先用此套件测不同记忆操作是否冲突，再用真实多用途任务验证。特别适合在同一状态容量预算下区分“存事实”和“更新状态”。

## 5. Critical thinking

各任务计分粒度不同；同格式训练测试不直接说明长度外推。小模型、超参搜索空间与实现差异也会影响排名。建议加入相同长度外推、数据量学习曲线与多随机种子，先独立训练再联合训练，比较共享memory的负迁移；不要将三学习率等同三随机种子。

## 6. 可信度判断

4/5。任务生成明确、实现和预算低、能力拆分可复现；真实语言、多目标共享训练和长期交互均需扩展。

