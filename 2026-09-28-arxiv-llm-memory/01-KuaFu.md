# 01. KuaFu

- 论文：**KuaFu: Compressing Long User Behavior into Understanding at Billion Scale**
- arXiv：[2609.31045](https://arxiv.org/abs/2609.31045)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（北京时间，cs.CL/cs.LG cross-list）
- 作者/机构（PDF 首页核验）：Jiahao Hui、Lin Zhu 等；Tencent Inc.
- 机构优先级：**S｜重点工业研究机构**
- 研究标签：personalized memory、用户行为压缩、latent memory、工业推荐
- 本地 PDF：[2609.31045.pdf](./2609.31045.pdf)

## 1. 做了什么

提出面向十亿级用户画像的 KuaFu，把每条原始行为独立压成可缓存、可追加、可跨任务复用的连续表示，避免每个画像任务都重新读取数百到上千条行为。它直接命中 personalized memory：目标不是概括一次会话，而是构建可持续刷新的用户侧压缩记忆层。

## 2. 怎么做、实验如何设计

每个行为项经 Qwen3-4B 编码器和 memory tokens 得到隐状态，再用投影器同时压缩 token 数与向量宽度，按时间顺序拼接给解码器。训练依次做重构、压缩问答、编解码协同训练和针对 fabrication/omission/date/logical error 的 DAPO。证据覆盖 42 类任务、内部四类画像、MRQA、RecBench 及线上系统；生产端每周刷新十亿用户。论文报告 10–15× token 压缩、每条缓存约从 10KB 降到 0.5KB、吞吐提升 37%–350%、节省 190 张 GPU，并在五个生产主指标上不弱于未压缩模型。

## 3. Conclusion

论文直接证据支持：以“行为项”为原子单元，比整段历史压成少量 token 更适合增量个性化；表示的可缓存性决定了系统经济性。幻觉感知 RL 将 fabrication 从 33.5 降到 4.5，完全正确率从 56.0 提至 90.0，但漏检略增。

## 4. Future impact

若可迁移到通用助手，用户记忆可以从文本摘要升级为共享的、版本化的 item embedding store；同一份用户表示可供推荐、广告和对话多个任务读取。论文也为“长期兴趣演化记忆”提供了真实生产约束。

## 5. Critical thinking

优点是规模、线上部署和成本口径都极少见。关键假设是单行为独立编码仍能在解码端恢复跨行为关系；这对复杂因果偏好、行为撤销和强 query-dependent 记忆可能不够。内部指标大量依赖 LLM judge，公开基准无法完全验证十亿级画像结论。建议做按时间漂移、删除权、隐私攻击与跨任务负迁移测试，并比较固定压缩率与 query-aware/uncertainty-aware 动态预算。

## 6. 可信度判断

**4.5/5。** 已阅读全文。优势是生产部署十个月、离线/在线/公开基准三层证据、训练和消融较完整；局限是核心数据与线上评测不可公开复现，且参数/数据规模扩展规律尚未系统验证。
