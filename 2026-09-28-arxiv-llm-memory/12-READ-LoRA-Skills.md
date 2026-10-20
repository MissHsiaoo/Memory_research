# 12. New LoRA Skills Should Read but Never Write

- arXiv：[2609.31600](https://arxiv.org/abs/2609.31600)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.LG new）
- 作者/机构（PDF 首页核验）：Zeyan Li 等；上海交通大学、西安交通大学、HKUST(GZ)、暨南大学
- 机构优先级：**A｜一流高校；论文标注 ICLR 2027**
- 研究标签：parametric memory、continual skills、LoRA composition
- 本地 PDF：[2609.31600.pdf](./2609.31600.pdf)

## 1. 做了什么

把逐个加入的 LoRA 视为模型持续积累的技能记忆，指出干扰来自 factorization 坐标不唯一与技能耦合方向错误；提出 READ，让新技能读取旧技能的输入子空间，但不能写坏旧技能的输出子空间。

## 2. 怎么做、实验如何设计

先用 QR+SVD 把每个 adapter 重写成保持更新完全不变的 balanced canonical form，再只训练耦合矩阵中新技能对应的一行；最终更新可折叠回 base weight，无路由和额外推理成本。实验在 Llama/Qwen、四组 benchmark 上按顺序添加技能，对比 naive sum 和多种 merge/composition baseline；论文报告所有 suite 平均优于同 adapter 的最强公开基线，SuperGLUE 超过 20 点、domain suite 超过 7 点，多数完整添加序列最终胜过所有直接基线。

## 3. Conclusion

单个 adapter 看不见的 gauge choice，在组合时会决定灾难性干扰；可比坐标与单向耦合是让新增技能“读旧而不覆写旧”的关键。

## 4. Future impact

这是参数化长期记忆的有力设计原则：新知识默认只读旧技能，写权限需显式授权。可扩展到用户级 adapter、组织知识和模块化 agent skill。

## 5. Critical thinking

“never write”保护旧技能，但也可能阻止必要纠错和正向重构；线性 LoRA 子空间不一定对应语义独立技能。建议测试互相矛盾任务、旧技能需要修订、顺序敏感性、百/千 adapter 扩展及隐私删除，并与显式版本控制比较。

## 6. 可信度判断

**4.5/5。** 已阅读全文。理论动机清楚、强基线、多套件双模型且零 serving overhead；仍需验证极长技能序列和开放式生成，而会议标注来自作者 PDF，非本报告独立核验录用系统。
