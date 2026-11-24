# 02. Composable Soft-Prompt Distillation of RL Experts: Toward Continual Post-Training

- [arXiv 摘要](https://arxiv.org/abs/2611.27376) · [官方 PDF](https://arxiv.org/pdf/2611.27376) · [本地 PDF](pdfs/2611.27376.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Zhang, Zhen; Yang, Changyi; He, Xuehai; Liu, Chengzhi; Yin, Yutong; Liu, Ziyue; Yin, Zhuoran; Li, Yangmin; Liu, Zhihan; Li, Jisen; Jin, Mingyu; Li, Chuhan; Weng, Zhaotian; He, Ruoyu; Gao, Wenyao; Deng, Jiaxin; Wu, Chenwei; Shen, Hui; Chai, Wenhao; Zhao, Chenyang; Ying, Zhuofan; Liu, Kieran; Chen, Andrew; Ma, Pony; Wang, Zhaoran; Patel, Alkesh; Gan, Zhe; Wang, Xin Eric。
- 机构：首页署名核验，UCSB、CMU、UCSC、Northwestern、NVIDIA、UIUC、UCLA、SemiAnalysis、SGLang-Omni、University of Michigan、Princeton、LMSYS Org、Mind Lab、Columbia、Apple；另有独立研究者。机构层级：A：优先产业研究机构合作。
- 研究标签：latent memory；soft prompt；continual post-training。
- 阅读依据：已下载并解析完整 28 页 PDF，目视核验首页；本评析重点核读 §2–3、表1–2、图3及局限/B.3，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：将各领域 RL 专家分别蒸馏为冻结基础模型上的软提示，再通过拼接组合能力。新专家到来时只训练新提示，避免重新整合所有专家权重。其“记忆”是可装卸的能力向量模块，而非用户事实数据库。

## 2. 怎么做、实验如何设计

每个专家对应256个可训练向量，只用通过验证器的专家输出做序列级蒸馏。为适应拼接时前缀变化，一半训练样本在软提示前加入128–256 token的同域问题前缀。单专家测试23种数学、代码和agent设置；组合实验在 M2RL 的同一 Qwen3-4B 基座上拼接数学、代码、科学、指令遵循四域，与TA、TIES、MOPD和LoRA蒸馏比较，并测试添加/移除、域外能力与服务吞吐。

## 3. 结论

论文证据：23种单专家设置中22种恢复至少90%的教师增益。四专家组合均分67.83，MOPD为67.79，基础模型50.41；添加顺序下均分逐步上升，但添加代码一度降低IFBench表现，移除数学又提高代码分数。B200上的特定并发条件中，吞吐接近基础模型且高于rank-4 LoRA。均分提升不等于无负迁移，恢复率超过100%也不等于新增了同等比例的通用能力。

## 4. 未来影响

研究判断：适合作为可组合 latent skill memory 的强基线，也直接对应多目标记忆的能力组合问题。未来可研究按任务选择模块、冲突检测、删除后行为恢复与模块预算约束。

## 5. Critical thinking

最重要的边界是组合实验仅一个基座、四个领域和一个训练种子；部分单专家checkpoint和TA系数在评测集选择，报告明确承认探索性。每专家增加256上下文位置，专家数增大后注意力与KV成本仍增长。建议在独立验证集选checkpoint，测试20/100专家、随机到达顺序及对抗领域；报告每域最差退化、Pareto曲线与总训练成本，而非只看总体均分。

## 6. 可信度判断

4/5。全文方法清楚，有同数据LoRA对照、模块消融和服务测量；但评测选择偏差、单种子和四域规模限制了“持续不遗忘”的强解读。移除提示可恢复原始参数，不保证提示挂载时所有非目标行为不变。

