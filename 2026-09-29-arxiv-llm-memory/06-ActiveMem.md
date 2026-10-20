# 06. ActiveMem

- 论文：**ActiveMem: Dynamic Latent Memory Trees for Long-Horizon Agents**
- arXiv：[2609.33244](https://arxiv.org/abs/2609.33244)；[官方 PDF](https://arxiv.org/pdf/2609.33244)
- 提交日期：2026-09-27；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Tsinghua University、Huawei Noah's Ark Lab
- 机构优先级：**A+｜一流高校 + 工业实验室**
- 研究标签：latent memory、hierarchical memory、RL、long-horizon agent
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

ActiveMem 将过去轨迹递归抽象成依赖感知的 latent execution tree，试图同时保留步骤之间的程序性因果关系，并控制平面检索造成的碎片化和跨任务干扰。

## 2. 怎么做、实验如何设计

系统把轨迹压缩为可复用子任务节点，显式保存执行转移，并用强化学习学习扩展、检索和剪枝策略。实验覆盖多种 agent benchmark、Qwen2.5-1.5B、跨设置泛化、持续学习、效率和 WebShop/搜索类任务；论文报告任务完成率、推理稳定性和记忆效率均优于平面记忆方法。

## 3. 结论

长程记忆的组织结构应反映程序依赖，而非仅按语义相似度返回独立片段；动态树能让小模型复用完整工作流。

## 4. Future impact

可用于把 agent 经验转成可组合“程序块”，并与技能库、计划器及 continual learning 联动。

## 5. Critical thinking

树结构提高可解释性，但真实任务往往是 DAG、循环或多因果关系；强行树化可能复制节点或掩盖共享依赖。RL 控制器也可能把 benchmark 模板学成捷径。建议比较树/DAG/图、测量结构错误的级联代价，并在跨网站和规则变化时做压力测试。

## 6. 可信度判断

**4/5。** 全文实验面广，机构强且与 latent memory 高度相关；局限是论文摘要中的“竞争于更大闭源模型”容易受 harness 和工具预算影响。

