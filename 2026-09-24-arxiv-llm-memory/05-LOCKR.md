# 05. LOCKR

- 论文：**LOCKR: A Hidden-State Trajectory-Guided Planner for Detecting and Repairing Stable-but-Wrong Lock-In in Diffusion Language Models**
- arXiv：[2609.27220](https://arxiv.org/abs/2609.27220)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Guoshenghui Zhao、Tan Yu、Weijie Zhao；RIT、NVIDIA
- 机构优先级：**S｜NVIDIA + 强研究高校**
- 研究标签：diffusion LLM、hidden-state trajectory、test-time planning、latent signal
- 本地 PDF：[2609.27220.pdf](./2609.27220.pdf)

## 1. 做了什么

发现 diffusion language model 的一种特有失败：答案很早就稳定在错误值上，但表面置信度、熵和稳定性无法可靠识别。LOCKR 读取整个去噪过程的隐藏状态轨迹，检测这种 stable-but-wrong lock-in，并选择反事实修复分支。

## 2. 怎么做、实验如何设计

论文先构建 surface-matched 对照集，让正确与错误锁定样本在 18 个表面统计量上匹配，再比较表面特征、单点隐藏状态和隐藏轨迹的错误检测 AUROC。系统在锁定触发后从固定 repair-action bank 生成候选 continuation，以轨迹感知 selector 选择保留结果。实验覆盖两类白盒 dLLM、MetaMathQA、Orca-Math、NuminaMath V2 等三套数学推理数据；在五个 model-dataset setting 上，端到端准确率绝对提升 2.21–5.37 个百分点，修复触发率 22%–41%，轨迹方法持续优于 surface-only 和单快照。

## 3. Conclusion

去噪轨迹包含最终输出和单一隐藏切片没有的正确性信号；dLLM 推理可被视为可观测、可干预的动态过程，而不仅是最终一次解码。

## 4. Future impact

可能催生 diffusion LLM 的“过程监控器”：在解码中检测错误吸引子、动态分配步数、回滚或切换去噪策略。它也为 latent memory/latent trajectory 研究提供了直接可测对象。

## 5. Critical thinking

surface-matched 设计很强，能排除“隐藏状态只是重新编码置信度”的简单解释。但系统需要白盒激活，固定 repair bank 限制可恢复上限，且仅验证数学推理；归一化去噪成本不等于真实吞吐。还存在训练/测试模型家族迁移和 probe overfitting 问题。建议在代码、开放问答与长文本生成中测试，做跨模型 probe、在线延迟和动态 action generation。

## 6. 可信度判断

**4/5。** 已阅读全文；控制实验、匹配诊断和端到端修复链条完整。局限是任务单一、白盒依赖强且 repair action 有人工上限。
