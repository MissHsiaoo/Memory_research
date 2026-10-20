# 20. GRAFT

In-Place Instruction Following in Diffusion Language Models

- 论文：[arXiv 2609.07160v1](https://arxiv.org/abs/2609.07160v1) · [本地 PDF](../papers/20-GRAFT.pdf)
- 首次提交：2026-09-07（UTC）；arXiv 最新记录：2026-09-07。本次按首次提交时间判断近 30 天资格；PDF 内部日期可能不同。
- 作者：Zheng Nie、Zherui Li、Jiaming Zhang、Kun Wang、Zhenhong Zhou、Yufei Guo
- 已核验机构：NUS、Nanyang Technological University、Peking University（PDF 首页署名）
- 机构优先级：A｜强高校相关研究组。这是本次选刊层级，不是学校综合排名。
- 主题：diffusion LLM / instruction following / local constraints
- 主观 novelty：4/5；证据可信度：3/5（不是概率，且不由机构名气决定）。
- 阅读范围：已核查原文首页与方法、实验及关键限制；定位 §3–5；PDF 第 3–7 页、附录 B。未做代码复现，未逐条验证所有引文或公式证明。

**入选理由：**利用 diffusion 的双向生成，把约束直接放在输出内部，为个性化生成提供不同于前缀提示的接口。

## 1. 做了什么

提出 In-place Instruction Following，要求围绕固定锚点生成，并遵守局部字面、风格或论述功能约束；构建约 5K 样本的 IIF-Bench。

## 2. 怎么做的

用 LITERAL/STYLE/DISCOURSE 标签指定 anchor，先 constraint-aware SFT 再 DPO；local-global rubric 同时衡量局部执行、上下文衔接、边界质量和全局要求。

## 3. 实验如何设计，结果如何

LLaDA-1.5、LLaDA-8B、Dream-7B、MMaDA 四种底座，GPT-5 与 JudgeLM 评分，三次运行平均；总体分 57.75→73.10。AR baseline 通过文字描述要求生成完整响应，没有匹配的原生 infill/constrained decoder。

## 4. Conclusion

面向 in-place 约束的训练能改善这些 dLLM 的局部控制；当前 AR 对照不足以证明 diffusion 在等工具条件下必然更好。

## 5. Future impact：对你的研究有什么启发

可把 personalized memory 编译为输出指定位置上的软/硬约束，例如某段的语气、用户禁忌、既定事实；测试相比整段 profile 前缀是否更精确。

## 6. Critical thinking、优点、局限与置信度

优点：控制界面有启发，区分局部与全局质量，跨四底座。局限：自建数据和 judge 可能偏向标签格式，attention-bias probe 不等于机制因果证明；AR 对照没有同等 infill 工具。建议加入位置扰动、冲突偏好、长度外推，并盲评人类满意度。可信度 3/5：任务贡献清楚，架构优越性与个性化效果尚待验证。

## 证据与复核

数值与实验设定来自上方链接的作者原文，具体定位见阅读范围；future impact 与建议实验是我的推断。代码/数据公开不等于已由本次报告复现。

