# 05. How to Guide Your Language Flow

- arXiv：[论文页面](https://arxiv.org/abs/2609.19356v1)｜[官方 PDF](https://arxiv.org/pdf/2609.19356v1)｜[本地 PDF](papers/05-Probe-Guidance-2609.19356.pdf)
- 首次提交日期：2026-09-16；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Rohit Dilip , Tianrong Chen , Yuyang Wang , David Van Valen , Joshua Susskind , Miguel Angel Bautista
- 机构：Apple；California Institute of Technology。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜优先公司/高校合作，直接相关
- 研究标签：continuous diffusion LLM；latent-state probe；guidance
- 入选理由：Apple/Caltech 用冻结内部状态的轻量 probe 替代第二个完整模型 forward，为 diffusion 的低成本控制提供新机制。
- 方法新颖性判断：4.5/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

论文提出 probe guidance：从已有 flow/diffusion 模型的冻结隐藏状态预测较弱的 clean reconstruction，再与强模型预测做类似 autoguidance 的组合。不再为弱模型单独执行第二遍完整主干，因此既节省推理计算，也让弱、强预测共享动力学来源。这里的 latent 指模型中间状态，不是可跨会话持久保存的 latent memory。

## 2. 怎么做，实验如何设计

训练轻量 MLP probe，主干冻结、隐藏状态 stop-gradient；推理使用形如 xs+(λ-1)(xs-xw) 的引导组合。作者在 ELF 的 T5 latent 与 FLM 的 token-continuous 表征上评估无条件文本生成，用 1,000 个 OpenWebText 样本和 GPT-2 Large 的生成困惑度，并同时观察 unigram entropy，防止只靠模式坍缩降低困惑度。另在 1.7B CFM 上测试六个多选问答基准；该设置还调整共享噪声与最终解码评分，因此不是全部差异都可单独归因于 probe。

## 3. 结论

CFM 六任务平均分从不引导的 39.6 到 λ=3 的 44.5，但仍低于对照 Duo 的 47.1。BoolQ 从 42.0 到 58.8，SIQA 从 38.4 到 39.8，增益明显不均。作者报告相对 dropout guidance 约 1.9 倍加速，比较对象是需要第二次主干计算的引导方法，不是相对完全不引导也加速 1.9 倍。MLP 计算和额外训练仍有成本。

## 4. 未来影响

我的推断：隐藏状态可提供低成本的辅助控制信号，未来可探索 query-conditioned 或 preference-conditioned probe，把 diffusion 输出引导到用户需求而不重复调用完整模型。但该论文并未验证个性化持久记忆，也没有证明 probe 可以长期保存新知识。价值更接近生成控制与中间状态可读性。

## 5. Critical thinking

关键假设是 probe 确实形成适当的弱模型，而不是任意有偏预测；深度、λ 和训练阶段都会影响弱强预测差。困惑度与 token entropy 无法充分描述事实性、长程多样性与语义分布覆盖；MCQA 评分调整也可能贡献提升。建议做 probe 单独开关、共享噪声开关、最终评分开关的因子实验，在相同 NFE、实际延迟与语义多样性下比较；个性化扩展则需用未见偏好、偏好冲突和事实约束，避免 guidance 只让输出更像用户而更不真实。

## 6. 可信度判断

可信度 4/5：依据全文方法、生成指标和 MCQA 表格，不是仅依赖摘要的 SOTA 说法。优点是机制轻量、主干冻结且讨论 autoguidance 的弱模型条件。局限是生成质量代理指标、不同任务收益不均、MCQA 流程同时有多个变化，以及主干外开销不能视为零。未独立重训 probe 或运行代码，结论保留模型与设置范围。

