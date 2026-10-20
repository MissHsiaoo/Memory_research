# 10 — Self-Evolving Algorithm-Design Agents via Population-Curated Policy Optimization

- arXiv：[2609.38757](https://arxiv.org/abs/2609.38757)；[官方 PDF](https://arxiv.org/pdf/2609.38757)；[本地 PDF](./2609.38757.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Chen Lu 等；Nanjing University、Huawei Noah's Ark Lab
- 机构优先级：**S，头部企业研究团队与一流高校**；研究标签：`self-evolving agent` `policy optimization` `algorithm design`
- 证据：已核读 PDF 方法和实验；数值为作者报告。

## 1. 做了什么

让算法设计 agent 从自己产生的一群候选程序中持续学习，而不是只凭当前最好样本改写 prompt。

## 2. 怎么做、实验如何设计

Population-Curated Policy Optimization 维护候选群体、筛选相对有信息量的设计轨迹并更新生成策略。以 Qwen3-8B 在 EDA 全局布局学习率调度与 GPU kernel 设计任务测试；前者用 4 个芯片案例训练、16 个案例测试，与 OpenEvolve/ShinkaEvolve 对照；后者报告相对 PyTorch eager 平均 8.27× 加速。

## 3. Conclusion

候选群体可以作为持续进化的经验记忆，使 agent 在设计空间中形成更有效的搜索策略。

## 4. Future impact

可借鉴“保留多样群体、从失败设计中学习”的方式优化 agent memory policy，而非只保存单条最佳经验。

## 5. Critical thinking

**推断：** EDA 与 kernel 的快速自动评测对方法极为有利，难以直接推至开放式代理或个人记忆。需要等总执行预算、等编译成本比较，公开测试分布，并检验真实代码维护性与跨硬件泛化。

## 6. 可信度判断

**3.5/5。** 有明确任务、训练/测试划分和外部搜索基线；两类高度可验证任务不足以证明通用自演化记忆能力。
