# Mitigating Sequential Reappearance：扩散模型连续遗忘后的记忆复现

- arXiv：[2609.25166](https://arxiv.org/abs/2609.25166)；[官方 PDF](https://arxiv.org/pdf/2609.25166)
- v1 提交日期：2026-09-21；正式公告批次：2026-09-23
- 作者/机构（arXiv HTML 全文核验）：Donghyun Kim 等；Konkuk University, Trustworthy Machine Learning Lab
- 机构优先级：B（黑马/启发性补充；与 diffusion memory 直接相关）
- 研究标签：diffusion model、memorization、continual unlearning、privacy

## 1. 做了什么

论文发现 diffusion data-point unlearning 的新失败模式：一个样本删除后立即看似被忘记，但模型继续处理其他删除请求后，它会在未重用原数据、无攻击微调的情况下重新进入 memorized regime，称为 sequential reappearance。

## 2. 怎么做、实验如何设计

作者建立 target-level 生命周期 protocol，区分 immediate forgotten、final forgotten 与中途 reappeared；分析删除后目标邻域的 denoising-loss geometry，定义 data-space recovery sharpness。LASTING 方法迭代搜索最易恢复的低损邻域，把删除目标扩展到该区域。实验覆盖 CelebA-HQ 的连续删除，并扩展至 text-conditioned Stable Diffusion；比较 SISS、EraseDiff、ReTrack、FU 等，同时评估遗忘持久性与生成 utility。

## 3. 结论

已有方法会在后续删除过程中重新生成早已删除的实例；reappearance 与更尖锐的局部恢复几何相关。sharpness-guided unlearning 降低长序列重现，同时保持整体生成质量。

## 4. Future impact

其核心启发可迁移到 LLM memory editing：一次成功的删除不代表长期删除，任何后续更新都可能重新激活旧记忆；遗忘必须按生命周期而不是单 checkpoint 验证。

## 5. Critical thinking

local sharpness 是相关信号还是因果机制仍需消融；邻域删除可能扩大 collateral damage，常规 quality metric 未必发现语义损失。建议更多数据集、模型架构、删除顺序/规模、重复训练 seed，并引入 membership/copyright attack 和更细粒度 retention utility。它研究视觉 diffusion，不应直接当作 diffusion LLM 结论。

## 6. 可信度判断

- 评分：3/5
- 依据：HTML 全文可读，包含明确 protocol、方法、多个 baseline 和两类 diffusion 设置；本地 PDF 下载未成功。
- 优点：识别重要长期失败模式；评价从瞬时扩展到序列；与隐私强相关。
- 局限：机构优先级较低；视觉 diffusion 为主；因果机制与 collateral forgetting 需进一步证实。

