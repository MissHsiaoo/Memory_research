# 14. EvoCUE

- 论文：**The Right Lesson at the Right Step: Deriving Control Updates for Self-Evolving Agents**
- arXiv：[2609.34988](https://arxiv.org/abs/2609.34988)；[官方 PDF](https://arxiv.org/pdf/2609.34988)
- 提交日期：2026-09-28；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Tsinghua Shenzhen International Graduate School、Sun Yat-sen University、University of Pennsylvania、Peng Cheng Laboratory 等
- 机构优先级：**A｜强高校/实验室合作**
- 研究标签：self-evolving agent、localized memory、control program、checkpoint evaluation
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

EvoCUE 把“经验应该存什么”扩展为“经验应在控制流的哪个位置生效”，将 agent 表示为状态机，并把学到的 instruction/skill 附到具体边及适用规则上。

## 2. 怎么做、实验如何设计

系统从轨迹提取未满足 residual goal，定位可编辑控制点；然后从同一 checkpoint 分别继续原程序与候选编辑，用最终分差做 paired trial，验证后才继承。AppWorld 上成功率从 13.7% 提升到 79.2%（Normal）、6.7% 到 70.0%（Challenge）；PAST-Bench 得分从 0.61 到 0.77，并与 GEPA、AFlow、AWM、MaAS 比较。

## 3. 结论

记忆内容本身不够；如果无法在正确决策点注入，再好的经验也可能无效或有害。局部控制更新比全局 prompt 更可验证。

## 4. Future impact

这为“procedural memory + execution graph”提供了强设计，也适合企业 SOP 和个性化规则的精确作用域管理。

## 5. Critical thinking

配对 checkpoint 是很好的因果近似，但后缀执行仍有随机性，且状态机需要人工或框架预定义。极大流程中定位候选边会变成搜索瓶颈。应报告多 seed paired trial、并发工具副作用、错误 checkpoint 恢复，以及动态生成工作流中的适用性。

## 6. 可信度判断

**4.2/5。** 结果幅度大、因果评测设计清晰、跨两个环境验证。局限是强依赖可恢复执行状态和显式控制图，通用性还需检验。

