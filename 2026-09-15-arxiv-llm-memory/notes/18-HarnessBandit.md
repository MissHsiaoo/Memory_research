# 18. HarnessBandit: Joint Learnability-Transferability Scheduling for Multi-Harness Agentic Reinforcement Learning

- arXiv：[2609.13739v1](https://arxiv.org/abs/2609.13739v1) · [官方 PDF](https://arxiv.org/pdf/2609.13739v1) · [本地原文](../papers/18-HarnessBandit.pdf)
- 正式公告：2026-09-15；首次提交：2026-09-12（两者不是同一字段）。版本：v1。
- 作者：Hongliang Wei (1 and 2), Xiaobing Tu (2), Yinggui Wang (2), Zhengxi Liu (2), Rongkun Xue (2), Jinkui Ren (2), Xiantao Zhang (2), Debin Zhao (1), Xiaopeng Fan (1) ((1) Harbin Institute of Technology, (2) Alibaba Cloud)
- 首页核验机构：Alibaba Cloud；哈尔滨工业大学。
- 机构优先级：A：强机构主榜（无普通机构补位）。机构只决定阅读优先级，不代替证据评分。
- 研究标签：相邻启发｜agent RL；跨执行框架迁移
- 主观 novelty：4/5；证据可信度：3.5/5（不是概率）。
- 阅读范围：方法、主实验、评价协议和局限；未复跑训练。

本笔记基于以上官方原文；第1–3节为论文内容及结果口径，第4–6节为阅读者判断，不能当作作者已验证的结论。未进行实验复现或代码审计。

## 1. 做了什么（论文报告）

研究agent在一个执行框架训练、换一个工具接口和上下文管理框架部署后性能下降的问题。把训练中选择哪一种harness视为bandit，让模型接触可学习且能向其他框架迁移的经验。

## 2. 方法与实验设计（论文报告）

每个优化步只使用一个harness，奖励信号组合平均绝对advantage表示的可学习性，以及不同框架梯度方向相似度表示的迁移性。梯度草图取最后四层、65536维，使用EMA和归一化窗口。2000个ClawGym任务扩成六种harness共12000行，Qwen3.5-2B以Dr.GRPO训练150步、4张GPU，每步8提示各8采样。与混合六框架和混合两框架比较，并在PinchBench、未见框架ClawEval测试。

## 3. 结论与结果边界（论文报告）

PinchBench147任务一次执行，官方平均分0.506，对照两框架混合0.493、六框架混合0.331、原模型0.330。主要收益相对六混合很大，但相对两混合仅0.013。ClawEval161任务各三次，all-three成功0.267与原模型持平；pass@3为0.416高于原模型0.360。不同稳定性指标不能混写成同一成功率。

## 4. Future impact（我的推断）

经验是否可迁移也取决于执行接口，而不只是memory文本内容。可考虑在经验库中区分可迁移的任务策略和harness特有的调用细节，用跨环境验证来决定长期记忆的晋升优先级。这是对memory的启发，论文并未实现该经验库。

## 5. Critical thinking（我的分析与建议）

缺少均匀随机、每步单一harness的关键对照，因此可能部分收益来自批次同质化，而非bandit选择本身。memory子类别并非都赢，两框架混合在某些记忆指标更好。建议固定每种框架曝光量、单步组织和总生成token，分别关掉学习性、迁移性、探索奖励，并重复训练种子，检验梯度相似度是否真预测未见环境收益。

## 6. 可信度、优点与局限（主观评估）

3.5/5。优点：问题贴近部署、显式跨框架测试、指标区分多次成功与至少一次成功。局限：小模型与短训练、对照未完全隔离调度机制；ClawEval多次执行不等于多次独立训练。不能由平均分提升推出每个框架、每种记忆任务都改善。

## 来源与审计

[官方摘要页快照](../sources/2609.13739-abs.html)记录日期和版本；[本日入选核验](../verification.json)保存公告主分类、PDF页数与SHA-256。[返回日报](../README.md)。
