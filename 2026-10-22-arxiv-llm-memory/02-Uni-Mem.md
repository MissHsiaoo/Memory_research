# 02. Uni-Mem: Learning a Long-Horizon Agentic Memory Manager with Unified Online Policy Optimization

- arXiv：[摘要](https://arxiv.org/abs/2610.29671) · [官方PDF](https://arxiv.org/pdf/2610.29671) · [本地PDF](pdf/2610.29671.pdf)
- 提交日期：21 Oct 2026；正式公告批次：2026-10-22（星期四），本报告对应北京时间2026-10-22。提交日不作为公告日。
- 作者：Zhiqian Xia , Jielong Tang , Ling-An Zeng , Shixiong Kai , Rong Yao , Hao Kong , Xiao Dong , Wei Wang , Mingxuan Yuan , Siyu Xia , Haifeng Xia
- 机构：Huawei Noah’s Ark Lab；东南大学；中山大学；山东师范大学（PDF署名核验；MCCL为第50页作者表，其余为首页）
- 机构优先级：A（强研究机构层）；主题相关性：直接相关；标签：记忆写入；检索；在线RL
- 证据可信度：4/5，与机构优先级独立。
- 阅读范围：首页、正文第3–7页及主结果表。官方PDF共21页，已下载并解析、检查首页渲染；未声称逐页精读所有附录或独立复现实验。

## 做了什么

以同一个可训练策略管理记忆构建和多轮检索，解决只优化一侧或使用过时离线写入示范的问题。

## 怎么做、实验如何设计

使用Qwen3-4B-Instruct管理器、GPT-OSS-120B回答器和GPT-4o-mini裁判。Stage-Decoupled GRPO交替优化写入与检索，检索组固定记忆库，构建评价绕过学习检索器；ECA按训练证据定位事件，并将奖励传播到同一事件的工具操作。LoCoMo按2:1:7划分，LongMemEval用于分布外评价。

## 结论

LoCoMo总体88.80%，同协议重测的Memory-R2(OSS)为77.87%，差10.93个百分点。SFT起点83.56%，完整方法88.80%。表中非标记旧基线引用其他协议结果，不能把全表视为完全公平的重跑。

## 未来影响

我的推断：联合控制应先解决归因混淆，再增加动作复杂度；事件层信号可用于多目标记忆管理。

## Critical thinking

训练依赖证据索引和回答裁判；它们错误时会把缺失存储误归因于检索。当前数据的查询全部在对话之后，尚未证明真实交错读写流中的在线适应。建议在等训练成本下测试中途查询、冲突更新、无证据标注训练和不同回答器。

## 可信度判断

4/5：有同协议强基线、增量消融和OOD任务；证据监督、裁判偏差及小规模对话划分仍需关注。不能将离线训练后的管理器称为部署中持续更新权重。

## 证据边界

方法和数值为上述阅读范围内的论文报告；未来影响与研究建议是本报告的推断，不是已验证结果。
