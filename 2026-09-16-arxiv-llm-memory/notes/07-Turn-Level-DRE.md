# 07｜Turn-level Multiscale Density Ratio Estimation for LLM Agents

- 来源：[arXiv v1](https://arxiv.org/abs/2609.16760v1) · [官方PDF](https://arxiv.org/pdf/2609.16760v1) · [本地PDF](../papers/2609.16760.pdf)
- 首次提交：2026-09-15；入选公告批次：2026-09-16（以官方New submissions快照核验，非按提交日猜测）。
- 作者：Zishuo Zhao (Alibaba Group), Kai Chen (Alibaba Group), Ao Li (Alibaba Group), Yuan Liu (Alibaba Group)
- 核验机构：Alibaba Group。依据论文PDF作者署名；联合署名不代表所有机构共同主导。
- 机构优先级：A1｜头部工业研究
- 研究标签：启发性相关｜agent学习、轨迹信用分配、经验记忆
- 编辑评分：novelty 3.5/5；证据可信度 3.5/5。均为本次阅读判断，不是同行评审结论。

## 1. 做了什么

把agent偏好优化从整条轨迹粗粒度奖惩，细化为不同轮次的不对称权重。失败轨迹中可能有大量正确步骤，若一律压低会丢掉可复用经验；tlm-DRE用turn-level multiscale density ratio estimation调整训练信号。

## 2. 怎么做，实验如何设计

在密度比估计与Bregman divergence框架内构造偏好目标，利用SFT参考策略对各轮的置信度分配权重，并对正负样本采取非对称处理。主实验为ALFWorld、ScienceWorld、HotpotQA，使用Llama-2-7B和Qwen2.5-7B；对照SFT、PPO、ETO、DMPO、DIL，另有去DRE和去turn-level多尺度的消融。交互任务表1报告五次独立运行均值及波动，硬件8张A100-80GB。

Qwen2.5-7B在ALFWorld unseen为90.1±0.50，DIL88.8，去turn-level为89.3±0.99；ScienceWorld unseen为64.5±0.54、DIL63.7。HotpotQA在Llama-2-7B上EM33.8/F1 43.74，NAT29.6/42.50。Llama-2表内并不是每列都最好：ScienceWorld seen DMPO72.4，高于本方法71.4。

## 3. 结论

直接证据支持细粒度加权对特定离线agent对齐有帮助，Qwen设置增益较一致；不能把升级基模后的大幅差距当算法增益。作者还比较GiGPO，但其环境/探索协议不同，附录采用对应协议另评，不能直接混排主表。

## 4. Future impact：未来影响

我的推断：self-evolving agent memory可从失败轨迹中提取仍然有效的局部技能。与其把整段经验标为失败后删除，更合理的是给动作片段附带局部可靠性和上下文适用条件；训练权重可以与记忆保留策略联动。

## 5. Critical thinking：批判性分析

参考策略低置信度不等于该步错误，可能只是罕见但必要的正确动作。因此论文的信用分配仍是代理信号，不是因果定位。去turn-level差距较小且有波动重叠，需严格显著性及相同调参预算。ScienceWorld是平均奖励，不要把64.5说成任务成功率。

建议：在可获得真实错误步骤标签的小环境验证权重与因果关键步骤的相关性；加入动作替换反事实、已知正确但低概率步骤；同时比较经验片段回放和纯权重调整，确认收益来自哪里。

## 6. 可信度、优点与局限

3.5/5。优点：有推导、多环境、两个骨干及五种子交互结果，离线方法实现相对清楚。局限：主要是较小/较旧骨干和受控环境，算法增益有时不大，置信度代理不等于真实必要性，在线采样扩展尚属未来方向。已核查表1/2及局限；没有独立重训。与memory的关系是经验学习启发，不是直接的新存储系统。

## 证据与阅读范围

本笔记基于原文方法、实验及相关局限/附录的人工阅读；PDF与抽取文本保存在本日报sources中。未执行作者代码，未独立复现实验。未加“我的推断”的数值均指作者报告或明确说明的表内重算；未来影响及后续实验为本次研究建议。排序、机构层级与置信度相互独立。

