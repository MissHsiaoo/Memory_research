# 05｜ReDraft, Don't Just Distill: Reference-Driven Revision for Continual VLLM Post-Training

- 来源：[arXiv v1](https://arxiv.org/abs/2609.16639v1) · [官方PDF](https://arxiv.org/pdf/2609.16639v1) · [本地PDF](../papers/2609.16639.pdf)
- 首次提交：2026-09-15；入选公告批次：2026-09-16（以官方New submissions快照核验，非按提交日猜测）。
- 作者：Zhihao Zhang , Mingqi Wu , Qiaole Dong , Enyu Zhou , Shuo Li , Boyang Liu , Jiazheng Zhang , Honglin Guo , Xin Guo , Shaofan Liu , Junzhe Wang , Dingwei Zhu , Zhiheng Xi , Minlong Peng , Yuan Hua , Qi Zhang , Tao Gui , Xuanjing Huang
- 核验机构：Tencent；Fudan University；Shanghai AI Laboratory。依据论文PDF作者署名；联合署名不代表所有机构共同主导。
- 机构优先级：A1｜头部工业研究与强校
- 研究标签：直接相关｜continual learning、遗忘、自修订
- 编辑评分：novelty 4/5；证据可信度 3/5。均为本次阅读判断，不是同行评审结论。

## 1. 做了什么

不直接让学生模仿专家完整轨迹，而让学生以自己的失败回答为起点，参考专家答案修订，再用验证通过的修订结果做后训练。作者假设：正确且更贴近当前策略分布的目标，比直接蒸馏远离学生分布的专家答案更少破坏旧能力。

## 2. 怎么做，实验如何设计

用Qwen2.5-VL-3B/7B学习Counting、Clock Reading和2×2 Jigsaw，数据分别来自PixMo子集、合成时钟和COCO拼图；专家为GPT-5.5。比较SFT、reject sampling、OPSD及ReDraft，检测三个新技能与8个既有基准的宏平均（含MME归一化）。修订候选经任务验证器筛选；分析正确率、目标困惑度、训练步数和旧能力变化。

重点核对PDF第24页表4：3B Jigsaw目标得分ReDraft80.00、SFT72.50；7B Counting却为62.25对64.38，7B Jigsaw75.00对75.50，不能照抄表注“每个设置均达到或超过SFT”。旧任务保持在表内六设置均更好，但训练步数不总相同，例如3B Jigsaw为578对313。

## 3. 结论

证据支持修订数据在所测任务中改善新旧能力权衡，但主文headline存在未对齐的汇总口径。按附录表4六设置直接平均，ReDraft新任务增益约56.00、旧能力下降约2.42个百分点；摘要对应为56.9、1.5。这里保留两组并标记需作者澄清，不自行替作者选一个作为最终真值。SFT旧能力下降均值约16.63，且被7B Counting的61.87大幅拉动。

## 4. Future impact：未来影响

我的推断：持续学习agent可以优先存储“自身解法的最小有效修订”，而非盲目积累高能力教师的完整轨迹。这可连接procedural memory和选择性回放：保留成功执行风格，同时补正关键错误。是否适用于连续多阶段、长期反复更新，仍需额外实验。

## 5. Critical thinking：批判性分析

分布距离低并不自动解释遗忘少：数据质量、验证器筛选、训练步数和目标难度共同变化。需要专家最小编辑、同长度同token预算、相同学习率与回放比例的对照；也应按六个设置分别汇报，不让单一灾难性SFT失败决定总平均。外部专家与修订采样开销应算入训练成本。

可复现实验：固定一个基模、一个新任务和一套保留基准，对原专家答案、学生直接正确样本、参考修订样本匹配数量与更新步数；至少三种子追踪能力轨迹，检查多轮学习后误差是否累积。

## 6. 可信度、优点与局限

3/5。优点：问题重要、机制假设清楚、附录逐设置表和扩展OPSD预算有价值。局限：主文与附录汇总数字及表注存在不一致，步数和数据生成成本不完全公平，长期多阶段推广未充分建立。已视觉核对表4，确认不是文本抽取导致的列错位；未独立复现实验。机构强不抵消证据一致性问题。

## 证据与阅读范围

本笔记基于原文方法、实验及相关局限/附录的人工阅读；PDF与抽取文本保存在本日报sources中。未执行作者代码，未独立复现实验。未加“我的推断”的数值均指作者报告或明确说明的表内重算；未来影响及后续实验为本次研究建议。排序、机构层级与置信度相互独立。

