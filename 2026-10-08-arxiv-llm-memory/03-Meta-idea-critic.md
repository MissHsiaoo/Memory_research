# 03｜Meta：用 idea-level critic 节省自演化 agent 的昂贵验证

- 论文：[arXiv:2610.08993](https://arxiv.org/abs/2610.08993)｜[官方 PDF](https://arxiv.org/pdf/2610.08993)｜本地 `2610.08993.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-06 UTC，v1。作者/机构（PDF 首页）：Jiamu Bai、Lizhu Zhang、Xin Yu、Yanhong Wu、Zellux Wang、Serena Li、Weiwei Li、Zhuokai Zhao、Lingzhou Xue、Kiwan Maeng、Xiangjun Fan、Bo Peng；Meta、Penn State University。机构优先级：S；标签：self-evolving agent、验证预算、continual learning；直接相关。

## 1. 做了什么

针对 AI4ML agent 自我改进中每个想法都要训练模型验证的高成本，训练“想法级”批评模型，预判候选改动是否值得真实实验。这并非 agent memory 写入算法，但可为自演化记忆或技能库的“候选更新门控”提供方法。

## 2. 怎么做、实验如何设计

用 Gemini-3.1-Pro 合成高质量 critique 做监督微调，随后以 GRPO 优化改进方向预测。PDF 的附录给出 9B/35B critic 的 LoRA 与 GRPO 配置；正文分别评估静态想法判断、推理期演化、持续学习和训练策略阶段。训练阶段把 critic 当学习奖励模型，对高不确定候选仍送往昂贵的经验验证；还分析多数投票样本数与不确定阈值对错误召回和实际验证比例的影响。

## 3. 结论

专用 critic 在静态判断上优于其合成数据教师；同样验证预算下，筛选后的演化轨迹得到更好的最终方案。论文也报告以 critic 辅助策略训练可在有限验证资源内做更多次更新，但这不能等同于“无需真实验证”。

## 4. 未来影响（推断）

Agent memory 自演化可以用廉价 critic 预筛技能、规则和记忆写入，再对不确定或高影响更新做真实任务回归测试；这有望把昂贵的验证预算集中在可能改变行为的候选。

## 5. Critical thinking

核心风险是 critic 学到教师偏好，而不是真实改进概率；连续使用会出现分布漂移与“critic 迎合”。与传统让前沿 LLM 直接挑 idea 的区别在于专门训练和不确定性路由。建议设盲测验证集，报告 critic 漏掉优质 idea 的机会成本、false-positive 对预算的影响，并在记忆写入场景测试不可逆错误传播。

## 6. 可信度：3/5

依据：读了 PDF 的训练配方、实验和消融。优点是有静态与在线演化两层验证、考虑验证预算；局限是面向 AI4ML，外推到个人记忆需重做实验，合成 critique 的偏差和长期闭环稳定性仍未充分证实。
