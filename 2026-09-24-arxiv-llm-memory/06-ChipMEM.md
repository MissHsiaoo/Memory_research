# 06. ChipMEM

- 论文：**ChipMEM: Verification-Grounded Memory for EDA Agents**
- arXiv：[2609.27067](https://arxiv.org/abs/2609.27067)
- 提交日期：2026-09-22；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Abdulrahman AlRabah 等；UIUC、NVIDIA、Cadence
- 机构优先级：**S｜顶级高校 + 顶级芯片公司**
- 研究标签：agent memory、procedural memory、verification、tool feedback
- 本地 PDF：[2609.27067.pdf](./2609.27067.pdf)

## 1. 做了什么

把 EDA 工具的可验证反馈转化为两类记忆：跨任务 procedural skill 和汇总成功/失败结果的 Bayesian/statistical memory。只有通过综合、等价性和 PPA 等硬门控的经验才可能写成技能，减少把 benchmark-specific 修补误当作可迁移知识。

## 2. 怎么做、实验如何设计

底层代理不改动，只在任务前检索最多两条相似技能并注入恢复建议；完成后由确定性 EDA harness 决定 PASS/FAIL/INVALID，evolving 模式只对验证通过结果更新技能，frozen 模式用于 held-out transfer。实验含 RTL-OPT 38 题、RTLRewriter-Bench 59 例、10 个 OpenTitan IP、20 个自定义设计，以及 CVDP 20 训练/20 未见任务；GPT-5.5 或 Qwen3.8-27B 执行。OpenTitan 完整门控通过从 1/10 到 4/10，held-out CVDP 从 18/20 到 20/20；在多套 PPA 测试中同时降低 LLM/tool calls 和 token。

## 3. Conclusion

工具验证信号能把执行轨迹转成更可靠、可迁移的程序性记忆；procedural 与 statistical memory 互补，并可在冻结库条件下改善未见任务。

## 4. Future impact

这一模式可推广到软件工程、科学工具链和机器人：记忆写入不由语言模型“自我感觉良好”决定，而由领域 verifier 决定，形成可审计经验库。

## 5. Critical thinking

最大的优点是 memory write 与硬验证绑定，证据链比 LLM reflection 更可信。问题是 EDA verifier 昂贵且领域特化，技能检索 top-2、阈值 0.6 固定；组件消融只有 5 个设计，held-out 每类 10 题，统计功效有限。Cadence 生产系统与 GPT-5.5 也降低完全复现性。建议做技能级因果消融、错误技能撤销、库增长/冲突和跨项目泄漏测试。

## 6. 可信度判断

**4/5。** 已阅读全文；多 benchmark、冻结迁移和确定性工具门控很扎实。样本规模偏小、部分系统专有、检索策略未广泛扫参，是主要扣分项。
