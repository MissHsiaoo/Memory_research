# 04｜Local Edits, Global Ripples: Replay-Informed Policy Adaptation for Workflow Synthesis

- arXiv：[2609.12127v1](https://arxiv.org/abs/2609.12127v1) · [官方PDF](https://arxiv.org/pdf/2609.12127v1) · [本地PDF](../papers/04-RIPPLE.pdf)
- 首次提交：2026-09-10（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Manqing Mao , Hong Wang , Samson Koelle , Jie Yuan , Zhuoer Wang , James Feng , Yanjun Lin , Daniel Edmiston , Nikki Lijing Kuang , Zhecheng Sheng , Wei Niu
- 核验机构：Amazon；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业机构。研究标签：直接相关｜persistent policy / self-evolving agent memory / replay。
- 主观新颖性：4.5/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§4、表1–4、§5及补充实验索引。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12127-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

RIPPLE针对agent从失败中修改持久prompt策略时的两个问题：修改位置局部，行为影响却可能全局；单独有效的两条经验合在一起可能冲突。它把“该改哪里”和“是否允许持久化”分离，特别适合思考self-evolving memory的写入门槛。

## 2. 怎么做，实验怎么做

诊断失败轨迹，将修复限制在预定义策略片段；先以同一轮初始策略评估候选的独立收益，再把有希望的候选放在已经接受其他修改的最新策略上重放，只有组合后仍可接受才保存。

Flow-HO主测试为39个合成JSON工作流修改任务、四个与训练/replay不重叠的家族。主干Haiku4.5，迁移Gemma3-12B与Ministral3-14B；每任务3次rollout、诊断预算15。比较无replay、静态/自适应replay、聚合方式、更多迭代、不同acceptor；Haiku采用家族cluster bootstrap。

## 3. Conclusion：原文结论及边界

Haiku服务验证通过率54.7%→77.8%，即+23.1个百分点；工作流结构正确率74.9%→75.7%，并非全面正确率也提升23点。另两模型验证率均+6.8点。一个候选在初始策略上收益为正，但组合后replay success从35.4%降至0，说明组合审查有实际必要。更多迭代并不更好。

## 4. Future impact：潜在影响

我的推断：记忆条目应被视为依赖当前policy版本的候选补丁，保存适用范围、前置条件、证据和冲突关系。可把这一框架移植到技能库或用户偏好规则写入，形成可撤回、可重放的经验提交过程。

## 5. Critical thinking：我的判断与可检验拓展

测试仅39任务四家族，三个rollout不等于三个独立适应训练重复；四簇bootstrap不宜解读为广泛任务确定性。预定义片段/补丁空间可能比开放式自演化简单。应对比相同提案和成本下的随机replay、多样性replay及定期全量回归，并测长期数据库增长、环境变更后失效和修复顺序依赖。

## 6. 可信度、优点与不足

可信度3.5/5；novelty 4.5/5。优点是独立收益与组合收益明确区分，包含真实负向交互及受控acceptor替换。局限是小型合成语言、收益主要在服务验证、迁移协议并非完全一致。最有价值的是“经验需在当前组合中再验证”这一可检验假设，而非目前分数本身。

