# 01｜CanvasAnneal: Curriculum Reinforcement Learning for Diffusion Language Models

- arXiv：[2609.13060v1](https://arxiv.org/abs/2609.13060v1) · [官方PDF](https://arxiv.org/pdf/2609.13060v1) · [本地PDF](../papers/01-CanvasAnneal.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Blake Olson , Yuhang Song , Emmett McQuinn , Yuan Shangguan
- 核验机构：Google DeepMind；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业实验室。研究标签：直接相关｜diffusion LLM / reasoning / curriculum RL。
- 主观新颖性：4/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§4–5、表1–4、§6；首页视觉核验。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.13060-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

研究 diffusion LLM 在强化学习初期难以探索出有效推理轨迹的问题。CanvasAnneal 把强教师的部分推理过程放入训练时的 diffusion canvas，再逐步撤去帮助。贡献是训练时探索课程，而非新的长期记忆系统；与 latent memory 的联系在于如何将外部推理支架内化为模型能力。

## 2. 怎么做，实验怎么做

教师为 Gemini 3.1 Pro，生成约256 tokens的推理材料，提示要求不含最终答案；采用连续前缀保留、后缀遮盖，用动态 Beta 分布逐渐增加遮盖率，并混入完全无教师的 rollout 组。同一问题组共享相同 canvas，避免组内优势被不同提示条件混淆。损失还包含教师位置，因此也带有 advantage-weighted distillation 成分。

主模型为 LLaDA-7B-A1B-Instruct，比较原模型、SFT、diffu-GRPO、SFT+RL及本方法。数学训练生成长256、去噪128步，固定1600步checkpoint；测试128/256/512长度。xLAM用于工具训练，Tau2、BFCL用于测试，并做注入比例、遮盖方式、课程消融。

## 3. Conclusion：原文结论及边界

MATH500 相对纯 diffu-GRPO 在三个长度提高6.0/2.0/0.4个百分点；Countdown也提高，但GSM8K三个长度均不如diffu-GRPO。Tau2宏均值10.15%→13.03%，BFCL Parallel则65.00%→60.50%。推理时不需要教师。论文支持“部分任务的探索效率提升”，不支持全面超越AR或全面改善工具能力。

## 4. Future impact：潜在影响

我的推断：可以把经过验证的 agent 历史成功片段当作训练canvas支架，研究从 episodic memory 到参数化能力的转化；推理阶段不再读取该片段。但用户偏好需要可撤回，不能直接把这一做法推广为不可删除的个性化记忆。

## 5. Critical thinking：我的判断与可检验拓展

关键混杂是教师数据、课程难度和蒸馏损失同时改变：应增加等教师token预算的SFT、只对自主生成位置算损失、随机但正确的支架等对照。教师被要求不写答案不等于完全排除答案泄漏，需要人工/规则核查。7.4×或18.8×是达到特定训练奖励的更新步数，不是包含教师生成成本的端到端加速。许多小增益低于表中约±4.3%或±6.1%的测试样本区间，不能逐格宣称显著。

## 6. 可信度、优点与不足

可信度3.5/5；novelty 4/5。优点是测试时撤去教师、多个基线、负面结果和课程消融明确。局限是主干单一、任务依赖、奖励阈值加速易被过度宣传；测试样本bootstrap也不等于多次训练seed稳健性。建议先复现MATH500 128长度的明显增益，再测错误/过时记忆支架是否造成负迁移。

