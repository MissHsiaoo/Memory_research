# 09. Hunyuan-A13B

- 论文：**Hunyuan-A13B Technical Report**
- arXiv：[2609.27284](https://arxiv.org/abs/2609.27284)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Tencent Hunyuan Team
- 机构优先级：**S｜头部工业实验室**
- 研究标签：弱相关但具启发性、MoE、long context、agent、dual-mode CoT
- 本地 PDF：[2609.27284.pdf](./2609.27284.pdf)

## 1. 做了什么

发布 80B 总参数、13B 激活参数的 Hunyuan-A13B MoE 技术报告。与核心研究方向不是直接 memory paper，但其 256K 上下文、agent 数据配方、快/慢双模式 CoT 和效率-能力权衡对长期代理系统有架构启发。

## 2. 怎么做、实验如何设计

模型用超过 20T token 预训练，含约 250B 高质量 STEM token；一个 shared expert 常开，另激活 8 个专家。经过 annealing、长上下文阶段扩展到 256K，并使用多领域 SFT、大规模 RL、通用 reward model 与 30 多类 agent system instruction/20,000 种工具格式组合。评估覆盖 MMLU、数学、代码、BBH、BFCL-v3、τ-Bench、ComplexFuncBench、C3-Bench，以及 PenguinScrolls、LongBench-v2、FRAMES、RULER。报告在 PenguinScrolls 87.7、LongBench-v2 55.0、FRAMES 81.1。

## 3. Conclusion

较低激活参数的 MoE 可在长上下文、推理与 agent 工具任务上接近或超过更大开源模型；快/慢思考为按任务分配推理成本提供实用接口。

## 4. Future impact

对 memory agent 的启发是把“外部记忆检索成本”和“内部推理模式”联合调度：短任务快思考，检索或冲突任务切换慢思考；大上下文则作为 memory system 的兜底而非替代。

## 5. Critical thinking

强项是大规模训练与广泛评测，且机构本身具有高参考价值。弱点是技术报告缺少训练数据细节、误差条、系统消融与完整 contamination 审计，内部 benchmark 占比不低；不少比较混合了不同提示和推理预算。它不能证明 256K 上下文等价于长期记忆，也不能揭示 agent 优势来自数据、RL 还是架构。建议关注独立复测、真实吞吐和长期记忆任务。

## 6. 可信度判断

**3/5。** 已阅读全文；规模与指标可信度中等，但属于团队自报技术报告，关键数据/训练消融有限。作为机构优先的弱相关启发稿收录，不把它当作 memory 方法的直接证据。
