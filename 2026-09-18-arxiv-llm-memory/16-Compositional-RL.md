# 16. Compositional Reasoning in Language Models under Reinforcement Learning Post-Training

- arXiv：[论文页面](https://arxiv.org/abs/2609.19465v1)｜[官方 PDF](https://arxiv.org/pdf/2609.19465v1)｜[本地 PDF](papers/16-Compositional-RL-2609.19465.pdf)
- 首次提交日期：2026-09-16；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Yu He , Yingxi Li , Yifei Wang , Ellen Vitercik
- 机构：Stanford University；Amazon AGI Labs。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜优先公司/高校合作，弱相关但具启发性
- 研究标签：skill memory；compositional reasoning；RL generalization
- 入选理由：Stanford/Amazon AGI 的组合泛化研究说明“积累原子技能”不等于“能组合使用”，直接启发 memory skill 接口评价。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

论文用依赖图形式化组合推理，区分单链、多技能链及部分有序组合等复杂度。它检验 RL 后训练得到的原子技能能否组成更复杂任务，并观察反方向迁移。研究对象主要是 reasoning/post-training，非 memory system；纳入是因为技能库经常默认“每项技能学会后组合就会自然成功”。

## 2. 怎么做，实验如何设计

作者构造 array、BST、Bloom filter、hash、heap 五类数据结构任务，以确定性最终答案奖励减少 judge 噪声。Qwen3 4B 为主要模型，另有 OLMo3 7B、Llama3.1 8B；使用 GRPO 比较 isolated atomic 与 composed 训练，在相同更新步数下测试。训练长度约 5–10，外推到 30，并测试结构分布变化、需要未见技能的任务；主图有三次重复的标准差，另给小型 BFCL tool-calling pilot。

## 3. 结论

直接证据是稳定的 decomposed-to-composed asymmetry：分别训练原子技能不能可靠迁移到组合任务，组合任务训练却较易保留/反向迁移到原子能力。长度与结构转移进一步暴露组合瓶颈。真实工具调用实验是 pilot，不能用数据结构结果宣称所有部署 agent 的工具组合问题已被完整验证。

## 4. 未来影响

我的推断：memory skill 的质量不能只用单 skill 成功率或检索准确率评估。应显式记录输入输出约束、状态修改与依赖关系，并训练/测试组合后错误是否累积。对你的自演化记忆，可把“新增技能提升单题”与“不会破坏旧技能组合”作为两个 admission gates。

## 5. Critical thinking

等更新步数不必然等 token 或环境工作量，组合任务更长更复杂，收益可能含额外训练投入。最终答案奖励也不能完全定位中间技能是否正确；输出格式约束会改变评测。理论解释基于所设依赖结构，不能自动推广到开放式自然语言 memory。建议以等总 token/执行成本复现，设置同样已掌握技能但不同接口兼容性的组合，加入 trace 验证与状态污染检测。BFCL 扩展应报告足够多任务与重复，避免小 pilot 变成宽泛应用结论。

## 6. 可信度判断

可信度 4/5：确定性任务、多个模型、三次重复和结构外推构成优点；全文也明确 pilot 的初步性质。局限是合成数据结构、训练预算口径与开放工具任务的外推。本次未复跑 GRPO。机构与实验可信度独立，该文作为强机构的启发性弱相关工作收录，不包装成直接设计了新 memory 模块。
