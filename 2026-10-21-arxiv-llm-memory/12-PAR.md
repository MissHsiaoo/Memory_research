# 12. PAR: Progress-Aligned Recurrence for Length Generalization in State Tracking

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27628)；[官方 PDF](https://arxiv.org/pdf/2610.27628)；[仓库 PDF](pdfs/2610.27628.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Pan Wang , Yihao Hu , Guangyuan Dong , Yitong Lin , Hang Wang , Zimi Liu , Zhihao Wen , Jianshe Li , Jiang-Ming Yang , Wei Wu , Yongqi Tong
- 机构（PDF 首页署名核验）：Ant International；National University of Singapore
- 机构优先级：P1B；主题相关性：直接相关；研究标签：latent recurrence；state tracking；length generalization
- 阅读证据：正文§3、§5–6、Limitations（PDF第3、5–7页）；首页。已获取完整 PDF（11页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

让循环隐状态的每次更新对应任务的一步进展，并控制状态范数漂移以增强长度外推。

## 2. 怎么做、实验如何设计

【论文直接证据】每轮监督相应前缀状态而不是每轮都逼最终答案；RMS范数锚定、可学习停止；无中间标签版本用前缀自蒸馏。Qwen2.5-0.5B为核心，在置换/交换、规则链及图可达性测试，另测更大Qwen2.5和Qwen3。

## 3. 结论

【论文直接证据】swap-S5训练≤32，测试512时主表95.5±11.0%，RLT55.7±25.8%；学习停止另组checkpoint92.9±16.2%。图可达性外推不理想，大模型方差33–43点，未显示单调规模收益。

## 4. 未来影响

【阅读者推断，尚待验证】潜在记忆的可持续更新需要明确的状态转移语义和稳定性控制，不只是增大向量容量。

## 5. Critical thinking

【阅读者评析与后续建议】核心优势依赖可顺序分解且中间状态可定义的任务。强制R=长度包含额外信息，学习停止结果须单独看。算法模板不代表开放域推理；建议带噪声观测、多目标中断/恢复、非交换更新与真实长对话状态跟踪。

## 6. 可信度判断

**4/5**（与机构优先级独立）。消融和负面任务结果充分、报告多种子；自然任务泛化仍未证明。Ant International不在此自动归为Alibaba署名。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
