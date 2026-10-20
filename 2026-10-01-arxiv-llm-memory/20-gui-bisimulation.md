# 20 — Action Conditioned Bisimulation For GUI Agent Memory

- arXiv：[2609.38778](https://arxiv.org/abs/2609.38778)；[官方 PDF](https://arxiv.org/pdf/2609.38778)；[本地 PDF](./2609.38778.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Hongbo Zhang 等；Peking University、East China Normal University、University of Southern California
- 机构优先级：**A+，一流研究型高校合作**；研究标签：`GUI agent memory` `bisimulation` `state abstraction`
- 证据：已核读 5 页 PDF 的方法与实验；论文篇幅较短。

## 1. 做了什么

提出以动作后果而非界面外观决定哪些 GUI 状态可以合并为同一记忆节点。

## 2. 怎么做、实验如何设计

若两个状态在给定动作下产生相同结果和后继，才视作可合并；冻结 Qwen3-8B agent，在 MiniWoB++ 的 10 个导航任务上各运行 60 回合，与无记忆、相同 detour、既有后继表示、无动作条件等对照。论文报告该状态抽象有利于样本复用和任务完成。

## 3. Conclusion

可执行后果是更适合代理记忆的状态相似性标准，界面截图或文本相似不足以保证可复用。

## 4. Future impact

可迁移到工具代理和网页代理的行动记忆，减少“看起来类似但动作含义不同”的错误复用。

## 5. Critical thinking

**推断：** 小型网页任务拥有可重复后继，真实 GUI 的异步状态、隐藏权限和概率性反馈更难满足双模拟假设。应在网站更新、不同用户权限和跨应用迁移测试，量化错误合并的恢复代价。

## 6. 可信度判断

**3/5。** 明确概念与多个消融是优点；仅 5 页、10 个窄任务和单一底模，现阶段属有趣但早期证据。
