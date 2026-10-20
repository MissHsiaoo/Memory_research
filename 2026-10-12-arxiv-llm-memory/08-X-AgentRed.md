# 08 X-AgentRed：个人代理跨服务行为的自进化红队

- 论文：[arXiv:2610.13886](https://arxiv.org/abs/2610.13886) · [官方 PDF](https://arxiv.org/pdf/2610.13886) · [本地 PDF](2610.13886.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Yeonsung Jung、Zhiyuan Wang、Zifan Wang、Vítor Albiero、Benjamin Newman、Edoardo Debenedetti、Ivan Evtimov、Ninareh Mehrabi。机构：Meta Reality Labs Research、Meta Superintelligence Labs、Meta、FAIR at Meta（PDF 首页核验）。
- 机构优先级：A（Meta）；研究标签：personal agents、self-evolving evaluation、multi-service safety；**弱相关但具启发性**，不把它表述为记忆算法。

1. **做了什么｜论文证据：**提出 X-AgentRed，寻找个人代理跨工具/跨服务执行中，由多个看似正常步骤组合出的有害路径。
2. **怎么做、实验如何设计｜论文证据：**从工具效果和前置条件构建 HarmFlow 依赖图，采样场景并依据执行反馈扩展或修正路径。用含 30 个服务、914 个工具的模拟生态，针对 4 个前沿代理比较有害路径发现率与工具覆盖。
3. **结论｜论文证据：**相对所比方法，作者报告更高的平均有害路径率与更广工具覆盖；实验每配置仅一次模拟运行，不可直接推断真实服务事故率。
4. **未来影响｜我的推断：**对带长期记忆的个人代理，可把“记忆导致的跨服务后果”纳入类似结构化红队，而不只测单轮提示注入。
5. **Critical thinking｜我的推断：**模拟器状态转移、判害标准与真实应用权限可能差别很大。建议在安全沙盒中复现实服务行为、增加多随机种子，并针对持久偏好/记忆误写设计长周期攻击链。
6. **可信度：3/5。**依据：已读实验与局限；优点是明确工具依赖和四代理对照，局限是模拟环境、单次运行与模型判定限制外推。高机构优先级不意味着高证据分。
