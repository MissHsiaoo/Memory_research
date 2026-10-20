# 20 — Causal Memory Policy: Making Memory Utility Identifiable by Intervening on Retrieval

- arXiv：[2610.02070](https://arxiv.org/abs/2610.02070)；[官方 PDF](https://arxiv.org/pdf/2610.02070)；[本地 PDF](./2610.02070.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Arman Behnam、Binghui Wang；Illinois Institute of Technology
- 机构优先级：**B，黑马/启发性补充；机构排序低于头部实验室**；研究标签：`causal memory` `retrieval intervention` `retention policy`
- 证据范围：核读 PDF 因果推导、实验；数值为作者报告。

## 1. 做了什么

指出用“删除某条记忆后任务是否变差”衡量其效用会漏掉从不被检索到的记忆；此时效用在统计上不可识别。

## 2. 怎么做、实验如何设计

CMP 预留固定上下文槽，按已知概率随机放入候选记忆，以自归一化逆倾向加权估计其效用，并推导可识别条件、估计方差与不可逆保留决策。PDF 在 LongMemEval、LoCoMo、HotpotQA、MuSiQue、Mem0 上测试：作者报告 LongMemEval 54%、LoCoMo 67% 的必需记忆存在识别失败；干预将必需/非必需记忆区分 AUC 从 0.54 提升至 0.66。但对未见查询的保留价值，论文自己也报告现有聚合方案尚不能可靠预测。

## 3. Conclusion

记忆效用估计必须干预检索过程；即便能识别当前查询效用，也不能直接推出未来是否应永久保留。

## 4. Future impact

为 self-evolving memory 的写入/删除策略引入因果实验设计，避免仅优化被现有检索器暴露的经验。

## 5. Critical thinking

**推断：** 随机塞入记忆会占用宝贵上下文并影响用户回答，部署时需安全探索预算。应研究离线回放、分层随机化、个体隐私约束，并寻找跨查询效用的稳定表示；AUC 0.66 仍不足以直接自动删除记忆。

## 6. 可信度判断

**3.5/5。** 因果定义、理论与跨基准实证、且坦承保留策略失败，是可信优点；实际策略收益有限，机构作为黑马不应因此被误判为高优先级部署方案。
