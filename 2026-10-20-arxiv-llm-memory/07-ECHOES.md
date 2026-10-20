# 7. ECHOES：递归压缩 GUI 历史与特权信息蒸馏

- **arXiv**：[2610.22408](https://arxiv.org/abs/2610.22408)；[官方 PDF](2610.22408.pdf)
- **提交日期**：2026-10-14（v1）。
- **作者/机构**：Tengda Guo 等。PDF 首页核验：Tsinghua、StepFun、Nanyang Technological University、Zhejiang Leapmotor、Honor。
- **机构优先级**：P1/P2（清华、NTU 与产业团队联合）。**研究标签**：GUI 长程 agent；视觉历史压缩；跨模态状态保持；benchmark。
- **证据范围**：完整 PDF，22 页；文件可解析。

## 1) 做了什么

提出 ECHOES，让 GUI agent 在部署时使用递归更新的文本历史状态，而不是持续保留所有截图；训练时利用多图像特权信息蒸馏，使压缩状态尽量保留视觉状态转移。

## 2) 怎么做、实验如何设计

代理按 Compression–Think–Action 格式滚动更新状态并采取行动；同一模型在有完整图像的 teacher 路径中为 student 生成 on-policy token-level distillation。PMF gap 机制平衡 perception-memory fidelity 蒸馏和任务 reward，周期更新 teacher。作者建立 ECHOESBMK，从真实 GUI agent 失败轨迹派生视觉感知/跨模态状态保持诊断集，在四个 GUI benchmark 和该 benchmark 上评测任务成功、记忆保真、部署推理成本及未见视觉规划迁移。

## 3) 结论

作者报告在不于部署保留历史截图时，达到有竞争力的性能/推理成本折衷，并对未见视觉规划任务有正向 zero-shot transfer。摘要中未列出具体主结果数字，故本笔记不补造提升幅度。

## 4) 未来影响

为视觉 agent 记忆提供“训练时看原图、部署时只留压缩状态”的路线；诊断 benchmark 有助区分视觉理解失误与跨帧记忆丢失。

## 5) Critical thinking

- **关键假设**：训练时特权图像能蒸馏为部署可依赖的文本状态，而不会让 student 依赖无法获得的信息。
- **差别**：不是只用 prompt 摘要压缩截图，而是对 student 自己产生的 CTA 轨迹做 on-policy 蒸馏并动态平衡记忆保真与任务奖励。
- **风险**：teacher/student 的图像信息不对称可能引入训练-部署差距；递归压缩可能累积状态漂移；benchmark 从失败轨迹构造，覆盖范围可能与真实 app 流程不同。
- **后续建议**：公开完整任务和重放轨迹；对不同压缩长度、屏幕变化、撤销/失败操作做压力测试；报告历史状态错误对后续行动的因果传播。

## 6) 可信度判断

**3.5/5。** 依据：全文包括四个 benchmark、诊断 benchmark 及训练框架；PDF 首页单位可核验。优点是评测显式测记忆保真，部署不留原图降低推理负担；局限是 privileged teacher 假设需在真实应用上验证，摘要/可见结果不足以量化各 benchmark 的泛化幅度。
