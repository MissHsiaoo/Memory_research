# 08. LLMs Memorize Their Own Hallucinations During Post-Training

- [arXiv 摘要](https://arxiv.org/abs/2611.26863) · [官方 PDF](https://arxiv.org/pdf/2611.26863) · [本地 PDF](pdfs/2611.26863.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-19（来自官方 submission history，非公告日期）。
- 作者：Atmakuru, Anirudh; Goyal, Tanya。
- 机构：首页署名核验，Cornell University。机构层级：B：强研究型高校/实验室。
- 研究标签：parametric memory；post-training；memory contamination。
- 阅读依据：已下载并解析完整 35 页 PDF，目视核验首页；本评析重点核读 §2–4、表1及MCQ测量说明，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：当RL只奖励最终答案，推理中自生成的错误事实也可能被正优势强化，包括后来被模型自己撤回的事实。研究把记忆污染从外部检索错误扩展到模型自身训练轨迹。

## 2. 怎么做、实验如何设计

在QuALITY（先CPT/SFT）与TriviaQA上对Qwen/OLMo六模型做GRPO；每数据集3609训练题、1000测试题。抽取正确rollout里的幻觉为HalluSet-train，以未获得训练信号的heldout幻觉控制分布整体变尖的影响。用多个checkpoint上的事实MCQ召回差定义memorization，并补充幻觉文本log-prob；八个等间隔checkpoint近似追踪变化，主要配置无KL，另做KL消融。

## 3. 结论

论文证据：训练幻觉平均召回变化4.83个百分点，heldout约0.17；QuALITY平均5.66，TriviaQA4.01。说明结果奖励可强化错误中间事实。作者明确指出MCQ选择偏好不等于自由生成幻觉概率，因此不能把4.83点当实际对话幻觉率增幅。

## 4. 未来影响

研究判断：自演进记忆在写入前需要对中间事实逐条做证据检验，不能因为整条任务成功就把过程全部当可信经验。此问题同时影响文本技能库与参数化记忆。

## 5. Critical thinking

GPT-4.1-mini负责抽取、判假和生成选项，构造误差可能影响结果。train/heldout并非完全随机同质事实；有限checkpoint也可能遗漏短暂记忆。建议把同一错误句随机mask或保留训练梯度，控制问题难度和长度，直接测自由回答/拒答，并比较过程真实性奖励与仅结果奖励。

## 6. 可信度判断

4/5。跨模型、跨知识设置、heldout对照和log-prob补充增强证据；没有完整随机因果干预，MCQ代理和自动事实标签限制外推。

