# 16 EmbodiedCLBench：具身自进化代理的持续学习测量

- 论文：[arXiv:2610.13021](https://arxiv.org/abs/2610.13021) · [官方 PDF](https://arxiv.org/pdf/2610.13021) · [本地 PDF](2610.13021.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Jie Huang、Yanan Chen、Ruixun Liu、Kaichen He、Xinyi He、Rui Huang、Zilong Zheng、Zhenliang Zhang、Yiwu Zhong。机构：Peking University、BIGAI、University of Hong Kong（PDF 首页核验）。
- 机构优先级：B（一流高校/研究机构）；研究标签：embodied agent memory、continual learning、self-evolving evaluation。

1. **做了什么｜论文证据：**提出 EmbodiedCLBench，检测代理能否把早期具身任务经验组合迁移到未见复杂任务。
2. **怎么做、实验如何设计｜论文证据：**按原子动作、基础任务、高级任务构造分层模拟任务；比较多种代理 harness 和学习方法，重点测基础任务训练后高级组合任务表现及经验样本量效应。
3. **结论｜论文证据：**零样本高级任务通常难解，基础经验带来稳定改进，但增加经验数量没有相应规模化收益；因此当前代理“积累更多”并不自动等于“学得更会用”。
4. **未来影响｜我的推断：**持续学习评价应检验可组合经验与技能调用，而不只看旧任务回忆率。
5. **Critical thinking｜我的推断：**模拟环境的组合规则可能比现实稳定，基准也可能奖励模板记忆而非真正技能抽象。建议跨环境/物体分布隔离、加入真实机器人小规模验证，并测错误经验被继承的概率。
6. **可信度：3/5。**依据：核查基准构建与多方法结果；优点是直接暴露样本数—能力不匹配，局限是模拟具身环境与真实部署之间的距离。
