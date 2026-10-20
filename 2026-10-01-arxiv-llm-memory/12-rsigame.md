# 12 — RSIGame: Autonomous Agentic Game Development with Recursive Self-improvement

- arXiv：[2609.39045](https://arxiv.org/abs/2609.39045)；[官方 PDF](https://arxiv.org/pdf/2609.39045)；[本地 PDF](./2609.39045.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Wenyi Wu 等；University of California San Diego、ByteDance Inc.、Carnegie Mellon University。PDF 未将 ByteDance 团队注明为 Seed，故不称 Seed。
- 机构优先级：**S，头部企业与一流高校；弱相关但具启发性**；研究标签：`self-evolving agent` `recursive improvement` `artifact evaluation`
- 证据：已核读 PDF 方法与实验；数值为作者报告。

## 1. 做了什么

构建能自己迭代游戏作品的开发 agent，把诊断与改进嵌入制作循环。它并非研究 LLM 长期记忆本身，收录理由是自演化的评估—修改闭环。

## 2. 怎么做、实验如何设计

局部循环进行探索、诊断与修复；全局循环按质量检查点决定继续或停止。GameCraft-Bench 含 140 个任务、Godot 与 Phaser 两引擎，比较五类生成器。论文报告 Qwen3.8-27B 设置在两引擎的得分约 61.38/58.53，优于所测 GPT-5.5 单次生成，同时生成 token 约少 11 倍。

## 3. Conclusion

可检验的外部作品质量信号有助于 agent 递归自我改进，而不只是自我评价文本。

## 4. Future impact

对记忆系统的启发是把“经验是否有效”绑定到可复现的产物测试，并保存每轮诊断与改动因果链。

## 5. Critical thinking

**推断：** 游戏任务的反馈相对丰富且可见，不能证明一般 agent 会安全自我改进。须比较相同生成/测试总成本，测试主观体验与长期可维护性，并防止针对评分器的投机。

## 6. 可信度判断

**3.5/5。** 多任务、双引擎与多生成器增强证据；基准评分和单次生成对照并非普遍有效性的证明，和个人化记忆直接关联弱。
