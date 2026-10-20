# 18 — Shifting Mechanisms: How Positional Encoding Choice Shapes In-Context Retrieval

- arXiv：[2609.38530](https://arxiv.org/abs/2609.38530)；[官方 PDF](https://arxiv.org/pdf/2609.38530)；[本地 PDF](./2609.38530.pdf)
- v1 提交：2026-09-29；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Eric Enouen、Sainyam Galhotra；Cornell University
- 机构优先级：**A+，一流研究型高校**；研究标签：`in-context retrieval` `positional encoding` `long context`
- 证据：已核读 PDF 方法与实验。

## 1. 做了什么

考察位置编码设计如何改变模型在上下文中的检索方式，解释同样的长上下文为何可能出现不同的“记忆读取”偏好。

## 2. 怎么做、实验如何设计

跨 8 个模型家族的 22 个开放权重模型，比较 RoPE 与滑动窗口注意力/无位置编码的混合机制；另做受控预训练消融、多个键值与语义检索任务。结果指向 RoPE 更偏位置线索，混合机制在多目标检索/问答中有优势，但在相互竞争的键值区分时可能退化。

## 3. Conclusion

上下文检索能力并非仅由窗口长度决定；位置机制会改变模型在“按位置找”和“按语义找”之间的取舍。

## 4. Future impact

设计 LLM memory 的内容排序、chunk 布局和检索提示时，应考虑底模位置机制，而非假设所有长上下文模型行为相同。

## 5. Critical thinking

**推断：** 跨家族比较可能混入训练数据、规模与 tokenizer 差异；受控预训练虽缓解但未完全消除。应在相同数据/参数/计算下检验更长序列，并加入真实多会话偏好更新任务。

## 6. 可信度判断

**4/5。** 广泛模型覆盖与受控消融互补；机制结论到实际 agent 记忆性能还差闭环验证。
