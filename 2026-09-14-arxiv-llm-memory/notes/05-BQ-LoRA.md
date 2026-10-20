# 05｜Behavior Quotient Learning for Low-Rank Adaptation of LLM Agents

- arXiv：[2609.12896v1](https://arxiv.org/abs/2609.12896v1) · [官方PDF](https://arxiv.org/pdf/2609.12896v1) · [本地PDF](../papers/05-BQ-LoRA.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Pengyang Zhou , Xiaobin Tu , Zhengxi Liu , Rongkun Xue , Haochen Li , Miancan Liu , Ziyuan Chen , Yinggui Wang , Jinkui Ren , Xiantao Zhang
- 核验机构：Alibaba Cloud；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业机构。研究标签：相邻强启发｜parameterized memory / LoRA / agent adaptation。
- 主观新颖性：4/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§4方法框架、§5、表1–3、§6。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12896-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

BQ-LoRA研究如何用一个固定rank适配器吸收多样agent轨迹，而不保存许多按能力划分的LoRA。它认为文本不同或梯度不同的轨迹可能造成相同决策变化，重复训练这类轨迹会浪费有限更新容量；在权重空间压缩又可能破坏行为。

## 2. 怎么做，实验怎么做

BQB以决策分布的局部变化定义behavior quotient，按局部密度重加权轨迹更新；DPC将平衡后的更新投影至固定rank切空间，并同时控制权重近似误差和参考决策分布失真，最终仍导出单个LoRA。

在Qwen3.5-4B/9B上，用成功轨迹做SFT，评估AppWorld Test-N/Test-C和BrowseComp-Plus的BM25/embedding检索设置；对比Full FT、LoRA、LoRA-S、MoRAgent、DART、TopoCurate，并分别去掉BQB/DPC及扫描两个超参数。

## 3. Conclusion：原文结论及边界

9B AppWorld Test-C TGC从普通LoRA的45.08%提高到53.00%；BrowseComp embedding accuracy46.00%→51.33%。并非每格最优：4B Test-N TGC低于MoRAgent，去掉BQB在该格还略高0.20点。报告的平均交互次数减少，不等于包含训练几何计算成本后的总成本下降。

## 4. Future impact：潜在影响

我的推断：个性化参数记忆可以按“行为影响的独特性”分配rank，而不是按文本相似度存储或蒸馏。尤其适合研究多用户偏好共享部分与差异部分；但该文没有实际验证用户隔离、隐私删除或持续更新。

## 5. Critical thinking：我的判断与可检验拓展

局部参考历史上的行为等价未必在新状态成立：两个更新当前等价，未来不同问题可能截然相反。对低密度更新加权也可能放大噪声或罕见错误。应测试受控重复轨迹、长尾正确轨迹和噪声轨迹，固定训练FLOPs/有效rank/参考history规模，检验真实收益来自几何还是额外计算。

## 6. 可信度、优点与不足

可信度3.5/5；novelty4/5。优点是同一rank目标清楚，参数误差与行为误差联合，双尺寸和模块消融。局限是单模型家族、只测两个agent环境、主结果与统计细节仍需独立复核，缺乏长期遗忘实验。建议把行为漂移和删除后的残留作为新评价，而非仅task success。

