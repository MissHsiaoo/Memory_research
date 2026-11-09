# 05. Query-Guided RoPE Modulation for Lost-in-the-Middle Mitigation in Long-Context LLMs

- arXiv：[摘要及版本](https://arxiv.org/abs/2611.09554)
- PDF：[官方原文](https://arxiv.org/pdf/2611.09554) · [仓库内原文](pdf/2611.09554.pdf)
- 公告批次：2026-11-09，官方 New submissions；北京时间日报日期：2026-11-09。
- 首次提交日期：2026/11/06；与公告日期分别记录，完整官方版本记录见文末。
- 作者：Zhang, Peiyu；Ping, Heng；Bhattacharyya, Shinibali；Pal, Anwesan；Kanakaris, Nikos；Cheang, Kevin；Li, Shixuan；Yang, Wei；Bogdan, Paul。
- 机构：首页已渲染并核验：University of Southern California；Amazon Web Services（首页脚注注明相关作者工作与其Amazon职位无关）。
- 机构优先级：A1补充：AWS署名合作，含独立工作声明。
- 研究标签：long-context；RoPE；查询条件记忆读取。
- 相关性：直接相关（含持续学习、扩散语言模型及个性化方向）。
- 阅读范围：完整13页PDF已取得；重点阅读PDF物理页 1、3–6。未逐行审查所有附录、未复现实验。
- 证据边界：第3节是论文报告结果；第4节和第5节研究建议为评阅推断。

## 1. 做了什么

用查询相关性动态调整RoPE位置，让重要历史证据在高频旋转平面上更接近查询；低频平面保留原布局，所有token仍然存在。解决lost-in-the-middle而非永久存储压缩。

## 2. 怎么做、实验如何设计

先普通prefill从校准选出的注意力头提取相关性，再以新位置编码回答；低层宽相关图、高层尖锐相关图。在四个骨干上测NoLiMa、RULER问答及needle检索，长度4K至64K，比较无改动及位置/注意力等基线。64K部分超过相应骨干32K配置，需和正常上下文范围结果分开看。

## 3. 结论

五任务均分提升约2.4–8.9个百分点，NoLiMa各模型长度组合均有提升；但96设置中17个低于原模型，最大下降约3.2点。因此是有条件改善检索，并非普遍无损。

## 4. 未来影响

评阅推断：查询条件的位置几何可作为记忆读取层，与检索器或压缩器组合；适合研究同一记忆服务不同目标时，哪些内容应保持远近关系。

## 5. Critical thinking

“无需训练”不代表无需校准或零开销：选头与两次prefill必须计入。查询变化导致缓存位置编码变化，可能伤害多轮复用。建议在多目标并发检索、长依赖顺序推理及真实文档问答中测端到端时间/显存与答对率，并比较等算力二次阅读。

## 6. 可信度判断

4/5。依据：方法、跨骨干长度实验和负结果明确。局限：主要是受控检索任务，额外prefill及缓存复用代价影响实际收益，未独立复现。

## 官方提交与版本记录

Submission history From: Peiyu Zhang [ view email ] [v1] Fri, 6 Nov 2026 15:01:03 UTC (372 KB)
