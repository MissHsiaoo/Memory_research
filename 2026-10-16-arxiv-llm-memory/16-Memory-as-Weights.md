# 16. Memory as Weights：流视频历史转成轻量参数

- 论文：[arXiv:2610.22070](https://arxiv.org/abs/2610.22070) · [官方 PDF](https://arxiv.org/pdf/2610.22070) · 本地 PDF：`2610.22070.pdf`
- 公告：2026-10-16；初次提交：2026-10-15。
- 作者/机构：PDF 首页核验 Zhuoming Liu、Jinhong Lin 等；University of Wisconsin–Madison、北京大学。**机构优先级 P2**。
- 主题：latent/parametric memory；streaming VLM；continual consolidation。证据范围：全文 32 页。

1. **做了什么（论文证据）**：提出 MaLoW，把不断到来的视频历史压入持续演化、固定规模的 LoRA 权重，而把当前画面留在输入端。
2. **怎么做与实验（论文证据）**：循环 HyperNetwork 递增巩固视频观察；构造 56K 视频、381K 问答的 MaLoW-Instruct；在 OVO-Bench、StreamingBench、StreamArena 和机器人策略迁移上评估。
3. **结论（论文证据）**：OVO-Bench backward split 上跨不同视频底座比先前记忆方法高 3.9–11.8%；Simpler WidowX 行动成功率 +9.3%，延迟开销被作者描述为适度。
4. **未来影响（我的推断）**：潜在参数记忆可避免反复把完整历史拼回上下文；长期多模态助理值得探索相似路径。
5. **Critical thinking**：参数化记忆可能难以逐条更正或忘记，也可能产生跨用户干扰；需测试顺序扰动、长于训练范围的视频、隐私删除和同等计算预算的检索基线。
6. **可信度 3/5**：多视频基准与具身迁移是优点；面向文本 LLM/个人助理的泛化尚未直接证明，参数记忆的可编辑性缺证据。
