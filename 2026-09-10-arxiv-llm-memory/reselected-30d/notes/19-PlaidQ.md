# 19. PlaidQ

Distilled Continuous Diffusion Language Models Can Write Code in Few Steps---or One

- 论文：[arXiv 2609.04531v1](https://arxiv.org/abs/2609.04531v1) · [本地 PDF](../papers/19-PlaidQ.pdf)
- 首次提交：2026-09-03（UTC）；arXiv 最新记录：2026-09-03。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Fred Zhangzhi Peng、Kaiwen Zheng、Anru R. Zhang
- 已核验机构：Duke University、Tsinghua（PDF 首页署名）
- 机构优先级：A｜强高校相关研究组。这是本次选刊层级，不是学校综合排名。
- 主题：continuous diffusion LLM / distillation / code generation
- 主观 novelty：4.5/5；证据可信度：3/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §2–3；PDF 第 7–8 页；附录 B.7（第 26–27 页）。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**连续 latent 接口允许把成熟 diffusion 蒸馏技术用于语言生成，探索少步甚至一步代码输出。

## 1. 做了什么

将 Qwen3-0.6B 改造成 0.7B 双向连续去噪器，随后蒸馏 4/8/16 步学生与单步学生。

## 2. 怎么做的

在连续 token embedding 上扩散；few-step 用 distribution matching，one-step 用成对轨迹监督。各步数是独立训练模型，不是同一个 checkpoint 任意切换。所谓“一步”后还有一次独立 decoding pass，即至少两次网络评估。

## 3. 实验如何设计，结果如何

教师训练约 0.40T sequence positions，数据含 50% code；测 HumanEval、MBPP、EvalPlus 变体和 infilling。16 步报告 HumanEval pass@10=31.78；单步 HumanEval pass@1=7.07。附录 B.7 明确 MBPP+ 的 378 题仅使用基础 assertions，未跑完整 EvalPlus 测试，因此 40.49 不能当作标准严格 MBPP+ 分数。

## 4. Conclusion

少步连续 diffusion 生成可执行代码的可行性得到展示，但单步质量还很低，速度与质量前沿的比较需要统一测试。

## 5. Future impact：对你的研究有什么启发

continuous latent memory 可直接作为 denoiser 条件，探索从记忆到完整方案的并行生成，再用执行验证筛选。这里是研究设想，不是论文已经做过的 memory 实验。

## 6. Critical thinking、优点、局限与置信度

优点：路线新、训练和 NFE 细节清楚，代码/权重有入口。局限：一步仍有 decoding pass；不同步数学生另训；代码 sanitizer 会丢掉无法解析片段，原始输出可靠性不能由过滤后编译率推断。建议固定完整 EvalPlus、报告 raw/sanitized 指标与端到端 latency，再测跨域代码。可信度 3/5：新颖性高，headline 指标需严格限定。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

