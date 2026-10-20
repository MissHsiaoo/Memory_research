# 11. FactorDLM

- 论文：**Constraints Are Graphs, Not Chains: Exact Decoding for Diffusion Language Models**
- arXiv：[2609.32900](https://arxiv.org/abs/2609.32900)；[官方 PDF](https://arxiv.org/pdf/2609.32900)
- 提交日期：2026-09-26；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：University of Connecticut
- 机构优先级：**B｜高水平研究型大学**
- 研究标签：diffusion LLM、constrained decoding、factor graph、exact inference
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

FactorDLM 指出 dLLM 的非局部约束不应硬塞进链式自动机，而应直接表示为因子图，并在每个去噪步骤用变量消元精确投影模型分布。

## 2. 怎么做、实验如何设计

方法把语法和跨位置关系编译为统一因子系统，复杂度由约束图 induced width 决定。九类关系 benchmark、三个 backbone 上所有输出都满足声明约束，投影开销 0.4%–6.9%；重复查询的编译投影比 8 worker 的 CP-SAT 快 13.6 倍。论文还构造含严格机会率与模板下界的新任务，避免规则本身直接解题。

## 3. 结论

dLLM 的自由更新顺序与图约束天然匹配；对非局部关系，图宽比自动机状态数更合理地决定解码难度。

## 4. Future impact

可用于结构化工具调用、JSON 引用一致性、计划约束和 memory schema 的严格生成。

## 5. Critical thinking

理论与实证结合很好，但精确推断仍会随 treewidth 指数增长，开放词表和长输出可能迅速失控。应测试近似消元、动态约束和真实 agent workflow，并比较在同等质量下与 rejection/repair 模型的总延迟。

## 6. 可信度判断

**4.2/5。** 有形式化复杂度、广泛审计和详细 limitations；机构优先级低于前列，但方法原创性与实验严谨性足以作为黑马收录。

