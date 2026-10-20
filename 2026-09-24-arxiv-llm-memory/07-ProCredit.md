# 07. ProCredit

- 论文：**ProCredit: From Outcome Rewards to Progress Credit in Agentic Reinforcement Learning**
- arXiv：[2609.27532](https://arxiv.org/abs/2609.27532)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Ming Ma 等；中科院、Alibaba Tongyi Lab、UCLA、NTU
- 机构优先级：**S｜头部工业团队 + 一流高校**
- 研究标签：agentic RL、credit assignment、long-horizon agent、tool use
- 本地 PDF：[2609.27532.pdf](./2609.27532.pdf)

## 1. 做了什么

针对长程 agent 只在终局拿一个标量奖励的问题，提出 ProCredit：每一步重新运行验收检查，依据“已完成检查项的变化”给 turn 级进度信用，同时改善同任务多轨迹之间和单轨迹内部的 credit assignment。

## 2. 怎么做、实验如何设计

方法把环境验收项视作可验证进度状态，计算连续 turn 的检查项增量，再结合 trajectory reward 训练 Qwen3.5 4B、9B、35B-A3B。实验在 AppWorld test-normal/test-challenge 上与 GRPO、只把 progress 加到终局分数的 GRPO-Φ 等比较，并在 ToolSandbox 做第二环境验证、BFCL 检查函数调用能力。ProCredit 在所有规模与两套 AppWorld 测试上 TGC 最优；4B 相对最强 outcome baseline 高 4.1 个百分点。ToolSandbox 三个规模也均优于 GRPO，例如 4B 为 84.5% vs 81.0%。

## 3. Conclusion

关键不只是获得进度信号，而是把它归因给真正推进任务的 turn；仅修改整条轨迹的总分不足以稳定获得同样收益。

## 4. Future impact

对 self-evolving agent memory 的意义在于：哪些经验值得存、哪个动作造成改进，可以由可验证进度而非最终成败决定，形成更细粒度的经验权重与失败记忆。

## 5. Critical thinking

论文把长期信用分配转成 verifier 可检查的局部变化，工程价值高。前提是任务能被拆成相对完备、顺序较稳定的验收项；现实任务的进度可能非单调、检查昂贵或可被 reward hacking。反复运行 checks 也增加训练成本。建议在不可逆/非单调任务、稀疏或带噪 verifier 下测试，并比较“进度信用用于策略学习”与“用于记忆写入/检索排序”的效果。

## 6. 可信度判断

**4/5。** 已阅读全文；三种规模、两种环境和粒度消融支持核心论点。局限在于 verifier 假设强，且训练成本与真实开放环境泛化尚不足。
