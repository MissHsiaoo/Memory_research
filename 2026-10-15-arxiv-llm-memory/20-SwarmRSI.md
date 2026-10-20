# 20. SwarmRSI：科学 agent 群体的递归自改进

- 论文：[arXiv:2610.20431](https://arxiv.org/abs/2610.20431) · [官方 PDF](https://arxiv.org/pdf/2610.20431) · 本地 PDF：`2610.20431.pdf`
- 公告：2026-10-15；初次提交：2026-10-14。
- 作者/机构：首页核验 Qianru Meng、Xi Zhang 等；Huawei Technologies、Leiden University、University of Groningen。**机构优先级 P2**。
- 标签：self-evolving agent；experience inheritance；scientific discovery。证据范围：全文 25 页。

1. **做了什么（论文证据）**：提出让科学 agent 群继承并改写既有假设、程序和实验依据的 SwarmRSI。
2. **怎么做/实验（论文证据）**：由同伴反馈区分假设错与实现错，保留未整体获胜却有用的程序片段并重组；在 OpenProblems、NatureBench、MLE-Bench Lite 等任务测试，报告有生物学家复核程序。
3. **结论（论文证据）**：作者报告多个科学研究基准的领先结果，支持“跨 agent 保留中间研究状态”有用；不能据此断言真实科学发现已自动化。
4. **未来影响（我的推断）**：自进化记忆可以存带证据的假设和可复用代码组件，而不是只存最终成功样本。
5. **Critical thinking**：评测可能偏重可自动评分任务，群体搜索成本不可忽视。应核算等预算收益、代码污染/偶然胜利、独立复现实验和长期假设纠错。
6. **可信度 3/5**：多基准与专家复核是优点；开放科学创造力和长期自改进稳定性仍超出当前证据。**弱相关但具启发性**。
