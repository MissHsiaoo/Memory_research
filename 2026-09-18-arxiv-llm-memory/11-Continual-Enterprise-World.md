# 11. Continual Enterprise World Model Discovery in Dynamic Systems

- arXiv：[论文页面](https://arxiv.org/abs/2609.19551v1)｜[官方 PDF](https://arxiv.org/pdf/2609.19551v1)｜[本地 PDF](papers/11-Continual-Enterprise-World-2609.19551.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Shambhavi Mishra , David Vazquez , Perouz Taslakian , Marco Pedersoli , Jose Dolz , Issam H. Laradji
- 机构：ServiceNow Research；ÉTS；University of British Columbia；Polytechnique Montréal；Mila；McGill University。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜优先研究公司/高校合作，直接相关
- 研究标签：continual memory；world model；规则修改/删除
- 入选理由：强企业研究与 Mila 合作，把保留、修改、新增、退休旧规则分开评估，尤其展示“删除过时记忆”的失败。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

EnterpriseWorldShift 将企业业务规则的持续变化作为 agent world-model memory 问题：修改一个字段可能触发其他字段、记录或审批，agent 保存规则模型后需要随系统变化修订。CDA 维护条件—效果形式的可读世界模型，跨版本保留与调整；它不是更新神经网络权重的 continual learning。

## 2. 怎么做，实验如何设计

基准基于实际 ServiceNow 环境：9 张表、50 个字段、252 个初始记录、25 条业务规则，构成 A 原始、B 规则修改、C 新增、D 删除的单一版本链。600 个 evaluation action，每个版本 150，参照 oracle 检查字段变化。发现阶段可操作环境，应用阶段从保存的模型作答；比较 CDA、每题查询的 DA 与规则 simulator，涉及 Gemma 4、Qwen 3.6、DeepSeek V4 Pro。重要核验：正文与局限说明各条件在相应阶段可读取隐藏规则定义，因此不是严格只凭黑盒操作独立发现所有未知机制。

## 3. 结论

平均 IoU，CDA 81.80 对 DA 74.04，各模型提升约 6.99–8.98 点，simulator 60.64。但 continual 版本在规则修改和新增时获益，在删除阶段三模型均退化，例如 Gemma reset 90.17 对 continual 79.94。删除/退休旧规则没有稳定解决，是本文对记忆研究最有价值的负面结果。保存模型在应用时不查询运行系统，不代表建立模型时没有读取规则。

## 4. 未来影响

我的推断：personalized memory 最需要处理的可能不是写入，而是过期知识的撤销。用户说“我现在不再喜欢 X”，应触发 rule retirement 及其下游推断失效，而不只是添加一条新偏好。本文可启发 tombstone、证据时间窗和依赖图失效机制，并将删除旧记忆与保留无关旧知识分别评价。

## 5. Critical thinking

必须质疑摘要的“发现隐藏规则”与正文可读取定义之间的实验边界；结果更稳妥地证明显式规则整理与持续修订的价值，而非纯黑盒因果发现能力。单一链中每次一种变更也远简单于真实企业并发、随机业务逻辑与权限限制。建议增加不可读取规则、混合多规则变化、无效观测和删除反证，比较直接读定义、纯交互及二者结合的成本。尤其测旧规则误触发率，不让总体 IoU 掩盖危险的过时结论。

## 6. 可信度判断

可信度 3.5/5：已阅读全文方法、主表和局限，真实运行环境与字段级 oracle 是优点，规则退休的失败也有明确报告。局限是可读隐藏规则、单一版本链、确定性规则和任务范围。不能把有显式规则访问的条件写成完全自主发现；该限定直接影响 novelty 解读，但不抹去持续删除记忆的研究启发。

