# 03 — Beyond Memory: Harnessing Long-Horizon Agents with Explicit Belief States

- arXiv：[2610.01415](https://arxiv.org/abs/2610.01415)；[官方 PDF](https://arxiv.org/pdf/2610.01415)；[本地 PDF](./2610.01415.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Yu Luo 等；Nankai University、Alibaba Group、Tsinghua University
- 机构优先级：**S，Alibaba 与一流高校**；研究标签：`agent memory` `belief state` `long-horizon recovery`
- 证据范围：核读 PDF 方法、实验；结论以作者报告为准。

## 1. 做了什么

指出“保留历史”未必让代理理解当前世界；提出显式维护任务条件化的信念状态及未完成需求。

## 2. 怎么做、实验如何设计

PoS 在每步建模世界状态和未解决要求，交互后检验信念一致性；若行动持续但任务无进展，检测 Belief Trapping 并按失败类型恢复。PDF 在 ALFWorld、LOCA-Bench、RCA-100、ClinDiag 四项任务，三种底模上测试成功率/诊断准确率，另做一致性验证与恢复消融和上下文增长实验；作者报告各基准、各底模整体表现居首。

## 3. Conclusion

长程代理需要可更新的当前状态模型，而不仅是压缩轨迹或被动检索。

## 4. Future impact

个性化记忆可采用“当前偏好/未解决目标/证据来源”的显式状态，减少用旧事实反复行动。

## 5. Critical thinking

**推断：** 信念本身若生成错误，一致性检查也可能在错误假设内自洽。应测部分可观察、欺骗性工具反馈、多次状态反转，以及引入信念维护后的额外延迟和 token 成本。

## 6. 可信度判断

**4/5。** 四基准、三底模和组件消融较全面；开放世界状态真实性及长期错误累积仍未充分验证。
