# 14 — Harness Evolution as Learning

- arXiv：[2609.36892](https://arxiv.org/abs/2609.36892)；[官方 PDF](https://arxiv.org/pdf/2609.36892)
- v1 提交：2026-09-29；正式公告批次：2026-09-30（北京时间）
- 作者/机构（PDF 首页核验）：Zeyu Gan、Zixuan Gong、Yong Liu；Renmin University of China
- 机构优先级：**A**；研究标签：`personal agents` `self-evolving memory` `learning theory`
- 证据范围：阅读全文；本地 PDF：[2609.36892.pdf](./2609.36892.pdf)

## 1. 做了什么

把冻结基座模型外部的 context、memory、tools 和 execution harness 的持续演化，统一为 approximation/generalization/optimization 三类学习误差。

## 2. 怎么做、实验如何设计

构建 preference-oriented AppWorld-P，围绕 harness architecture、capacity/scale 和 evolution algorithm 做控制实验，再用 reachable policy、有限交互证据容量和偏置更新动力学解释现象。结果显示偏好遵从依赖可用机制，memory 越大不一定越好，反复自更新仍可能低于 oracle。

## 3. Conclusion

可靠个性化必须同时问：harness 能表达什么、容量是否匹配证据、反馈更新是否朝正确目标移动。

## 4. Future impact

它提供诊断语言，可把 memory failure 从“模型不够聪明”细分为表示不足、样本泛化不足或更新偏差，并指导 self-evolving agent 的实验设计。

## 5. Critical thinking

理论更像解释框架而非能精确预测现实系统的定量定理；AppWorld-P 仍是模拟环境。论文机构优先级低于头部工业实验室，但主题直接、理论整合有启发，因此作为高相关补充。后续应在真实用户、多月交互和不同 foundation model 上检验误差分解是否可操作。

## 6. 可信度判断

**4/5。** 理论与控制实验相互对应，且不把“大 memory”当作单调改进。局限是外部效度与理论可证伪性有限，真实偏好噪声、冲突和隐私未充分覆盖。
