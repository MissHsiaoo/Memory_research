# 19. LearnActCoder: Role-Aware Error Memory for Adaptive Clinical Coding Agents

- arXiv：[论文页面](https://arxiv.org/abs/2609.19721v1)｜[官方 PDF](https://arxiv.org/pdf/2609.19721v1)｜[本地 PDF](papers/19-LearnActCoder-2609.19721.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Meysam Ghaffari , Bhaskar Sen , Nasim Sabetpour , Nina Fatehi , Animesh Agarwal , Carlos Morato
- 机构：Optum AI；Harvard University（合作核验；不标为优先公司主导）。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P2｜应用机构主导/顶尖高校合作；直接相关
- 研究标签：error memory；role-aware routing；inference-time adaptation
- 入选理由：Optum/Harvard 用结构化误差记忆而非泛泛 reflection，且公开不显著结果与 precision/recall 取舍，实验启发明确。
- 方法新颖性判断：3.5/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

Learn-Then-Act 把少量带标注 LEARN 样本中的错误整理为 MistakeKDB，再用不更新权重的 Coder–Judge pipeline 处理新病历编码。false-negative lessons 给召回导向 Coder，false-positive lessons 给精度导向 Judge，并在可用时用 lookup table 核验编码标识。它是跨案例结构化错误 memory，不是让模型进行临床诊断。

## 2. 怎么做，实验如何设计

全部使用 GPT-5，25 个 LEARN notes 产生约 1,028 个 mismatch，比较无记忆、raw examples、reflection 与结构化 MistakeKDB。Coder/Judge 最多三轮交互；主要 MIMIC-III 匹配 held-out 为 150 notes，另有 MIMIC-IV 250 notes 与 1,000 条 MIMIC-III 的规模稳定测试。分析区分 ICD 与 CPT/HCPCS，报告配对差异、置信区间与检验，不能把所有代码类别合成“医学能力提升”。证据为论文全文回顾性实验，没有真实临床部署。

## 3. 结论

150 条上 CPT F1 从 11.5 到 17.4，+5.9 点，CI [3.3,8.6]；ICD-9 +1.5，CI [-.3,3.3]，未显著。MIMIC-IV ICD-10 precision +4.2、recall -3.1，F1 +1、CI [-1,3.1]，也未显著。raw/reflection 的 CPT 点值约 12.1/11.7，低于结构化记忆，但不能凭点差假装每组都有显著配对优势。1,000 条稳定性测试不等于匹配 1,000 条证明 treatment effect。

## 4. 未来影响

我的推断：failure memory 应按错误类型与消费角色组织，避免所有经验一股脑注入所有 agent。结构化 lesson 可能比原始错误示例更能调整行为，但任务目标不同会带来 precision/recall 取舍。可迁移到 personalized memory 的“错误偏好推断”与“漏掉真实偏好”，分别影响建议生成与审核。

## 5. Critical thinking

角色路由的因果贡献尚不充分：未见 swapped 或 symmetric routing 对照，效果也可能来自结构化本身。行政编码标签不是完整临床 ground truth，病历文本/编码遗漏可改变 false positive 的含义；lookup table 只核验合法编码，不保证临床事实正确。绝对 CPT/HCPCS 水平仍低，不能用于部署推荐。建议做无路由/交换路由/随机路由消融，对 unseen error types 和 institution shifts 验证，并将标注成本、memory token 和多轮调用成本匹配。

## 6. 可信度判断

可信度 4/5：匹配 held-out、置信区间与明确负面/不显著结果是优点，结论克制。局限是小规模回顾性样本、编码标签不完美、缺少角色路由直接消融及低绝对成绩。本评分仅指限定实验的证据，不表示医疗可用或患者安全认证；本次为论文分析，不提供医学建议。

