# 13. Beyond Downstream QA：记忆本身不能只用答题分数评价

- 论文：[arXiv:2610.22209](https://arxiv.org/abs/2610.22209) · [官方 PDF](https://arxiv.org/pdf/2610.22209) · 本地 PDF：`2610.22209.pdf`
- 公告：2026-10-16；初次提交：2026-10-15。
- 作者/机构：PDF 首页核验 Sebastian-Antonio Toma、Jean de Kernier、Mike Ply、Oliviu Matei；Amazon Web Services、Technical University of Cluj-Napoca。**机构优先级 P2**。
- 主题：agent memory evaluation；fact evolution；intrinsic/extrinsic metrics。证据范围：全文 14 页。

1. **做了什么（论文证据）**：指出下游问答可因检索或生成因素把记忆错误掩盖，也会把回答失败错怪记忆；提出直接检查记忆状态的 FEB-30。
2. **怎么做与实验（论文证据）**：从已知事实变迁轨迹反向生成文档/邮件/对话，30 条轨迹覆盖六诊断类、三难度，逐次写入后有确定性真值；对代表性系统比较内在记忆正确性与外在答题效果。
3. **结论（论文证据）**：两类评分平均相差 16 个百分点，44% 轨迹超有意义差异阈值；该系统的 create/update/reinforce/supersede 操作识别只有 20%，答题分数不可见此缺陷。
4. **未来影响（我的推断）**：长期记忆基准应并报状态正确性与端到端效用，特别要检查事实更新、覆盖和撤回。
5. **Critical thinking**：FEB-30 规模小，合成轨迹无法穷尽真实语言歧义；需多系统、多语种、真实组织文档及来源冲突测试。内在评价不能取代端到端评价，论文也明确如此。
6. **可信度 4/5**：确定性真值与逐步状态检查很有诊断价值；样本量 30、代表性系统有限，不能直接给行业总体失效率。
