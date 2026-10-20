# 19. Epistemic Admission in Shared Agent Memory

- arXiv：[2609.30813](https://arxiv.org/abs/2609.30813)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.AI new）
- 作者/机构（PDF 首页核验）：University of Southern Queensland、UNSW、Nanjing University、Facebook 等
- 机构优先级：**A/B｜含一流高校/工业联合；部分机构较弱**
- 研究标签：shared agent memory、provenance、memory write gate
- 本地 PDF：[2609.30813.pdf](./2609.30813.pdf)

## 1. 做了什么

提出 Correlated Promotion Benchmark（CPB），研究共享记忆的写入准入：多个代理复述同一来源并不形成独立证据，但系统容易把这种重复误认为共识，让假命题进入 memory 后反复传播。

## 2. 怎么做、实验如何设计

CPB-Static 用公开标注来源构造固定 gold admission；CPB-Live 运行多代理共享 store，记录每次 write/retrieval，并用场景规定的 source lineage 跟踪复制与转述，最后让独立 consumer 只根据 store 回答。作者在四类 agent、八种 admission policy 上比较真假命题准入和下游采纳。声明来源类型的 gate 将 false adoption 降至 0.06–0.09，而其他回答策略为 0.22–0.47；一旦无争议假记忆进入 store，consumer 在 0.97–0.99 的 probe 中会复述它。

## 3. Conclusion

语义去重、投票和 LLM judge 都无法可靠识别相关来源；没有 lineage，就很难区分“多份证据”和“同一错误被多次复制”。

## 4. Future impact

共享 agent memory 应把 provenance 当一等字段，并在写入前做来源独立性判断；这也适用于 personalized memory 中由模型多次推断出的同一错误画像。

## 5. Critical thinking

最有价值的是把错误传播后果实际跑出来。source-type gate 的优异表现部分来自 benchmark 有可用声明字段，开放世界中声明可伪造；作者构造 envelope 也可能偏向 lineage 方法。建议加入恶意 provenance、混合真实/复制证据、跨模态来源和延迟纠错，并测量不可逆写入与可撤销 belief 的差异。

## 6. 可信度判断

**3.5/5。** 已阅读全文。live store、日志谱系和四 agent 家族增强了证据；但 benchmark 为新构造、机构层级混合，真实多代理组织部署尚未验证。
