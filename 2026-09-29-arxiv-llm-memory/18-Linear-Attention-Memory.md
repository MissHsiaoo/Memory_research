# 18. How Linear Attention Remembers

- 论文：**How Linear Attention Remembers**
- arXiv：[2609.33093](https://arxiv.org/abs/2609.33093)；[官方 PDF](https://arxiv.org/pdf/2609.33093)
- 提交日期：2026-09-27；正式公告批次：2026-09-29（北京时间）
- 作者/机构：**机构未核验**（官方 HTML 未可靠呈现机构行）
- 机构优先级：**C｜机构未核验，机制启发性收录**
- 研究标签：latent memory、linear attention、recurrent state、causal intervention
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

论文把 linear attention 的固定大小 recurrent state 当作记忆系统，分解信息写入、保持和读出，并用因果干预识别真正支撑后续 recall 的路径。

## 2. 怎么做、实验如何设计

作者在预训练 GLA/GDN 模型中追踪内容特定写路径与 query-time 读路径，操纵状态以测试多事实选择性访问、写入重叠和负载增加导致的干扰；还比较混合 full-attention 架构，发现有 KV 层时实际 recall substrate 会转向全注意力。

## 3. 结论

固定状态确实能保存多事实，但存在可测的耦合和容量退化；混合架构中名义上的 recurrent memory 不一定是实际记忆承担者。

## 4. Future impact

这些机制可指导 latent memory 容量、写门控和混合 attention 层配置，也能帮助区分“模型声称使用状态”与“因果上真正使用状态”。

## 5. Critical thinking

因果干预比相关 probe 更有说服力，但人工 recall 任务能否代表自然语言长期记忆仍不确定。应在真实预训练语料回忆、复杂推理和更大模型中验证，并控制 intervention 是否产生分布外状态。

## 6. 可信度判断

**4/5。** 机制框架、干预和混合架构对照很强；机构未核验，且外部任务效度仍是主要限制。

