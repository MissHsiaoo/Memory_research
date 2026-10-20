# 17. MemBodied

- 论文：**MemBodied: Recurrent Associative Memory for Vision-Language-Action Models**
- arXiv：[2609.28256](https://arxiv.org/abs/2609.28256)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Tej Deep Pala 等；NTU、Griffin Labs、École Centrale de Lyon
- 机构优先级：**A+｜一流高校/实验室**
- 研究标签：embodied memory、recurrent associative memory、VLA、episodic memory
- 本地 PDF：[2609.28256.pdf](./2609.28256.pdf)

## 1. 做了什么

为 VLA 提出固定容量 episodic memory：一条 recurrent associative state 跟踪过程信息，另一条 initial-scene anchor 保留最早但后续不可见的关键证据，无需不断把历史图像塞回上下文。

## 2. 怎么做、实验如何设计

将两条记忆路径接入 π0/π0.5 类 VLA，并与 stateless、frame stack、vanilla recurrent、NativeMEM 压缩历史比较。RMBench 五个记忆依赖任务每任务 50 rollout；另测 LIBERO 四套 fully observable 任务、第二个 VLA backbone 和三项真实机器人任务。MemBodied 在 RMBench 平均成功率 50.0%，是 stateless 的 7.81×、vanilla recurrent 的 2.98×，比最强 memory baseline 高 1.3×且新增参数少 10×；相对 NativeMEM 延迟低 91.9%。真实机器人均值从 3.33% 到 26.67%。

## 3. Conclusion

固定大小的关联记忆可显著改善历史依赖控制，同时不必牺牲 fully observable 任务总体能力；初始 anchor 对“当前画面无法恢复的早期事实”尤其重要。

## 4. Future impact

为 embodied agent memory 提供与文本检索不同的方向：把 episode 压进动作网络可直接读取的连续状态，并保留可解释 anchor。可用于家庭机器人、导航和长程操作。

## 5. Critical thinking

多模拟基准、第二 backbone 和真机实验很难得。绝对真机成功率仍只有 26.67%，且固定 state 可能在更长、更复杂 episode 中饱和；anchor 在 BlockRanking 上甚至伤害性能，显示静态早期记忆会干扰动态进度。建议测更长 horizon、跨 episode 清空/污染、可变容量和可读出记忆内容，并与外部 episodic store 混合。

## 6. 可信度判断

**4/5。** 已阅读全文；500-rollout 级模拟、真机和效率数据形成完整证据链。任务数仍有限，真实机器人绝对表现和泛化不足。
