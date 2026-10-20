# ToolCompass：按功能组织工具调用表征

- arXiv：[2609.25678](https://arxiv.org/abs/2609.25678)；[官方 PDF](https://arxiv.org/pdf/2609.25678)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Junlin Fang 等；Nanyang Technological University、Zhejiang University、UTS Australian AI Institute
- 机构优先级：A（强校合作；与 latent representation/agent experience 相关）
- 研究标签：latent representation、tool-use agent、OOD transfer、post-training

## 1. 做了什么

论文研究 agent 遇到未见工具时的 trial-and-correction：过度试错浪费预算，压制试错又损害探索。ToolCompass 让隐藏表征按跨领域“功能类别”而非应用 domain 聚类，从已见工具迁移到功能相似的未见工具。

## 2. 怎么做、实验如何设计

提取工具调用末 token 的 hidden state，经投影归一化到单位球面；每个功能类用 von Mises–Fisher 原型建模，variation loss 拉近同功能、separation loss 分开不同功能，与 GRPO/RFT/DMPO 联合训练。投影头和原型部署时移除。实验在 AppWorld/FTRL、Qwen3.5-4B/9B 上测 ID/OOD 成功率、调用次数、未见工具采用率和表征结构。

## 3. 结论

ToolCompass 在三种 post-training 方法上稳定提升，AppWorld OOD 成功率最高提升 10.71pp；论文正文示例中 GRPO 最高提升 8.87pp 至 70.02%，同时轨迹更短且无推理开销。

## 4. Future impact

这为“latent skill memory”提供思路：经验不必储成文本，可通过功能原型塑造内部空间，使新工具自动落入可迁移的技能簇。

## 5. Critical thinking

功能类别仍是人工标签，类粒度决定结果；真实 API 常一工具多功能、功能边界模糊。需要开放集类别、组合工具、标签噪声和自然语言 schema 变化实验。隐空间聚类可视化不等于机制因果，最好用 representation intervention 验证原型是否真正控制选择。

## 6. 可信度判断

- 评分：4/5
- 依据：23 页全文、两 benchmark、两规模、三 post-training objective 与表征/行为分析。
- 优点：问题设置清晰；部署零额外开销；跨目标一致。
- 局限：依赖功能标注；实验工具生态仍有限；因果解释不充分。

