# 18. Why Jailbreaks Succeed in Diffusion Language Models

- arXiv：[2609.30841](https://arxiv.org/abs/2609.30841)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.AI new）
- 作者/机构（PDF 首页核验）：Thong Bach 等；Deakin A2I2、Pennsylvania State University
- 机构优先级：**A｜强研究型高校；论文标注 NeurIPS 2026**
- 研究标签：diffusion LLM、denoising trajectory、safety、latent dynamics
- 本地 PDF：[2609.30841.pdf](./2609.30841.pdf)

## 1. 做了什么

用能量景观统一解释 diffusion LLM jailbreak：攻击要么在全 mask 初始态隐藏恶意 disposition，要么在去噪中途把轨迹推过安全能垒；由此导出三个无需训练的检测信号。

## 2. 怎么做、实验如何设计

step-0 ratio 读取拒绝/服从 token mass，另外两个 trajectory-velocity 信号分别监测互补 logit 子空间中的 kinetic energy。作者在 LLaDA-8B、LLaDA-1.5、Dream-7B 和 LLaDA-MoE-7B 上覆盖 template injection 与 anchoring attack，并做阈值/FPR stress test。结果显示三信号互补；所有能逃过联合检测的配置也未成功产生有害内容。

## 3. Conclusion

dLLM 的安全信息分布在整条 denoising trajectory，而非只在最终输出。初态隐匿与中途跨 barrier 构成当前已知攻击的两类共同机制，联合能量信号比单点检测更稳。

## 4. Future impact

对 latent memory 很有启发：可把轨迹摘要作为过程记忆或 controller signal，用于判断何时修复、拒绝或回滚；也提醒 diffusion agent 的中间状态会成为新的攻击面。

## 5. Critical thinking

“每个已知攻击都归入两类”不等于未来攻击完备性；能量、basin 和 barrier 是具体 log-odds/Fisher metric 下的构造，不应过度物理化。主要实验输出长度固定在 L=128，token set 与阈值选择可能影响结论。建议用 adaptive white-box attack 直接优化联合探测器，并测试长输出、采样温度和新 dLLM 架构。

## 6. 可信度判断

**4/5。** 已阅读全文。四模型、已知攻击覆盖与互补性 stress test 较强；安全结论仍受攻击集合与阈值协议限制，尚不能声称一般性防护完备。
