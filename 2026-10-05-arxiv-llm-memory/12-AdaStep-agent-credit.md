# 12｜AdaStep：按可靠性收缩 Agent 步骤信用

- 论文：[arXiv:2610.03223](https://arxiv.org/abs/2610.03223)｜[官方 PDF](https://arxiv.org/pdf/2610.03223)｜本地：`2610.03223.pdf`
- arXiv 正式公告：2026-10-05；首次提交：2026-10-02。
- 作者/机构：首页核验 Xin Wang 等；Xiaomi、Tsinghua University、Nanjing University。
- 机构优先级：S；标签：self-evolving agent、步骤信用分配。关联性：邻近，弱相关但具启发性。

## 1. 做了什么

AdaStep 指出局部步骤优势比整条轨迹更细，但可能被后续随机结果污染；提出状态依赖的收缩权重，决定何时信任局部反馈。

## 2. 怎么做、实验如何设计

在显式条件采样假设下，把权重写为隐含步骤优势估计的均方误差最优解，其形式可理解为“行动解释的回报方差 / 总方差”。无需额外 critic 或 rollout。PDF 在 Qwen3-1.7B、Qwen3-4B、Qwen2.5-7B-Instruct 上评测 ALFWorld、WebShop、ScienceWorld，与 GRPO、GiGPO、HGPO 等比较，也测有/无优势标准差归一化；示例 Qwen3-4B ALFWorld in-distribution success 从 GiGPO 88.02 增至 93.01（表中设定）。

## 3. 结论

局部信用不应固定权重注入；按估计可靠性调节可在所测 Agent 环境提高训练效果。

## 4. 未来影响（推断）

对 self-evolving memory 的启示：写入经验时，也要记录该步骤与成败之间的因果可信度，而非把所有经历等权累积。

## 5. Critical thinking

最优系数依赖可匹配状态和条件采样假设，真实部分可观测环境不一定满足。论文结论也将连续/部分可观测场景列为开放问题。应在非重复状态、长延迟奖励及环境非平稳场景验证，并测收缩系数的校准误差。

## 6. 可信度：3/5

依据：已读 PDF 推导、三模型三环境实验及归一化消融。优点是轻量且假设公开；局限是实验环境与假设对真实 Agent 工作流的覆盖有限。
