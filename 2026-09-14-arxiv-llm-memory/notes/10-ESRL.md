# 10｜Expert-Space Exploration in MoE Reinforcement Learning

- arXiv：[2609.13058v1](https://arxiv.org/abs/2609.13058v1) · [官方PDF](https://arxiv.org/pdf/2609.13058v1) · [本地PDF](../papers/10-ESRL.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Hongyi He , Zhenghao Lin , Xiao Liu , Peng Cheng , Yan Lu , Yeyun Gong
- 核验机构：Microsoft Research、Tsinghua University；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业实验室／顶级高校。研究标签：弱相关但具启发性｜MoE routing / exploration / latent computation。
- 主观新颖性：4/5；证据可信度：4/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§3.4、§4、表1–3及路由策略说明。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.13058-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

ESRL把MoE强化学习的探索从输出token扩展到内部专家路径。即使相同文本状态，激活不同专家也可能产生不同解决路线；直接随机扰动却会激活不合适专家，因此需要保留可靠路径并有控制地探索。它不是memory paper，但可启发latent memory写读路径的探索。

## 2. 怎么做，实验怎么做

保留高置信专家作为anchor，对候选探索专家施加自适应噪声；选完专家后仍用原router logits计算混合权重。rollout记录每token每层专家集合，更新时采用Routing Replay，避免训练重算Top-K导致被探索的专家收不到对应梯度。

数学训练按256 batch、每题8rollout；Qwen3-30B-A3B、Sigma单激活、Moonlight带共享专家三结构。对比GRPO、GSPO、GRPO-R3、辅助负载均衡等；还测science/code和强Instruct起点。pass@1/8由每题32个样本估计。

## 3. Conclusion：原文结论及边界

Qwen基础模型数学宏均pass@1由GRPO38.9→42.1、pass@8由59.7→64.2；Sigma、Moonlight平均也提高，但并非每子任务最佳。科学/代码的多样本收益更明显，不能等同单次可靠性提高同样幅度。强Instruct上相对GRPO有提升，相对更强GSPO的差距小得多。

## 4. Future impact：潜在影响

我的推断：参数化memory或专家化用户记忆可以探索“读取哪个子空间”而不只改采样温度；将成功轨迹连同内部路径作为训练经验，也许有助于理解哪些计算通路被学会。该推断尚未证明专家路径就是可解释记忆位置。

## 5. Critical thinking：我的判断与可检验拓展

路径回放是训练过程记录，不是长期用户记忆。更多rollout覆盖可能来自额外计算和通信，应比较相同墙钟、总专家FLOPs与样本数，而不是仅固定外层步数。需要检验路径噪声在部署恢复确定性路由后是否仍有收益，及罕见专家是否产生不稳定或跨用户串扰。

## 6. 可信度、优点与不足

可信度4/5；novelty4/5。优点是三种MoE结构、强R3/GSPO对照、采样和anchor消融，以及分开报告pass@1/8。局限是主要训练任务仍偏推理，方法对稠密网络及真实持续适应未验证。适合将其用于“内部计算路径是另一种探索空间”的研究拓展，而非声称已解决agent memory。

