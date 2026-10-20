# 19. StateComp

- 论文：**StateComp: Learning When to Compress History in Long Horizon Agents**
- arXiv：[2609.27298](https://arxiv.org/abs/2609.27298)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Mingxuan Wang 等；TierFlow Team、人民大学、清华大学
- 机构优先级：**A｜高校强；TierFlow 身份仅按 PDF 署名，不额外推断**
- 研究标签：agent history compression、state-conditioned memory、online controller
- 本地 PDF：[2609.27298.pdf](./2609.27298.pdf)

## 1. 做了什么

提出 StateComp，把“某段历史是否可压缩”定义为该段内容与当前 agent state 的联合属性，而不是由年龄、固定窗口或单独相关性决定。它预测历史何时从 KEEP_FULL 转为 READY，再对足够大的安全 span 进行摘要替换。

## 2. 怎么做、实验如何设计

两阶段标注先判断完整细节是否仍会影响未来动作，再训练 hidden-state readout；在线用 span/token gates，摘要只有在协议有效且长度更短时才提交。微基准中，七个可配对状态的抽取时间从 76.40 秒降到 6.03 秒，峰值 GPU memory -36.72%、forward workspace -91.05%；最佳有界表示 F1 0.7818，高于 full-context reference 的 0.7000。WorkBuddyBench 260 题平均 token 约减半，reward 基本保持；Eval40 与四种 acting model 也普遍降 token。

## 3. Conclusion

安全压缩机会随任务状态变化，应先独立预测“何时可以改写”，再执行摘要；这样可大幅减 token 而维持整体任务质量。

## 4. Future impact

可成为 agent memory 的 garbage collector：不是按时间删除，而是等待信息被后续结论吸收后再压缩，并保留未解决约束。

## 5. Critical thinking

概念清晰且贴近真实 agent trace。风险在于摘要一旦提交仍是不可逆的，router 误判会在更后阶段暴露；当前指标偏平均 reward，难以看到罕见灾难性遗忘。微基准最大 full input 未能完成，不应外推为端到端延迟收益；作者也承认 cache hit 未保证。建议报告 worst-case/尾部失败、可回滚原文、校准风险预算和长期多次压缩误差积累。

## 6. 可信度判断

**4/5。** 已阅读全文；系统、表示和跨模型结果充分，但端到端 latency 与尾部可靠性证据不足，且与同组论文共享 benchmark/annotations。
