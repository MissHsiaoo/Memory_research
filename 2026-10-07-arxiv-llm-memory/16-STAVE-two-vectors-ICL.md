# 16｜STAVE：两个任务向量替代重复的 in-context 示例

- 论文：[arXiv:2610.07572](https://arxiv.org/abs/2610.07572)｜[官方 PDF](https://arxiv.org/pdf/2610.07572)｜本地 `2610.07572.pdf`
- 正式公告：2026-10-07；首次提交：2026-10-06（UTC）。
- 作者/机构（PDF 首页）：Xi Ding、Naichen Shi、Jiawei Zhang；University of Wisconsin–Madison、Northwestern University。机构优先级：A（强研究型高校）；标签：in-context learning、task vectors、multimodal adaptation；直接相关。

## 1. 做了什么

将反复放进提示的任务示例压缩为两个任务专属嵌入向量，降低多模态 ICL 每次请求重复编码图片的成本。

## 2. 怎么做、实验如何设计

STAVE 对产生答案的 token 加 readout 向量，对其他结构性 token 加 context 向量；两者需用带标签的示例训练，包括有/无示例提示。论文给出一阶损失分析与 margin bound；PDF 在六个多模态模型、五个语言模型和 18 个文本任务比较已有 task-vector/ICL 方法，作者报告可超过 15-shot ICL，推理时不再需要示例。

## 3. 结论

经任务数据训练后的紧凑向量可在所测任务代替重复上下文示例；“零示例推理成本”不意味着适配过程不需要标注或训练。

## 4. 未来影响（推断）

个性化 ICL 可考虑把稳定任务偏好蒸馏为小型可撤销任务向量，再按用户/任务切换。

## 5. Critical thinking

任务向量若来自少量示例，可能过拟合任务格式或含隐私残留。建议做跨任务组合、偏好更新/撤销、与缓存示例同等算力对照，以及标注成本与存储成本总账。

## 6. 可信度：4/5

依据：已读 PDF 向量注入位置、理论分析及多模型/多任务对照。优点是参数与推理成本明确；局限是任务级训练成本不可忽略。
