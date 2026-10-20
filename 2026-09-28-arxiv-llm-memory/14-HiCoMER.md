# 14. HiCoMER

- arXiv：[2609.30289](https://arxiv.org/abs/2609.30289)
- 提交日期：2026-09-09；正式公告批次：2026-09-28（cs.CL new）
- 作者/机构（PDF 首页核验）：Yufei Shi 等；NTU、University of Macau、Zhejiang University、WPI
- 机构优先级：**A｜一流高校联合**
- 研究标签：agent memory、collaborative memory、validity-aware retrieval
- 本地 PDF：[2609.30289.pdf](./2609.30289.pdf)

## 1. 做了什么

提出 HiCoMER，显式区分团队共识记忆与个人观察记忆，并在检索前先更新有效性，解决语义相关但已过时或与当前团队共识冲突的历史被错误召回。

## 2. 怎么做、实验如何设计

系统由 Hierarchical Memory Conflict Updater、Validity-Aware Retriever 和 grounded answer generator 组成；更新器判断 supersession/conflict，检索器只在有效集合中结合层级与相关性。作者构造两个协作 memory-QA 数据集，在 outdated retrieval rate、correct retrieval、decision F1、ROUGE-L、NDCG 等指标上与 flat retrieval/Mem0 等比较，并做科学协作情境人评；结果在两个数据集均减少旧记忆召回并提高回答质量。

## 3. Conclusion

长期协作记忆的核心不是“存更多、搜更准”，而是持续判断哪些记录仍有效；团队层级可作为个人记录的有效性约束。

## 4. Future impact

适合组织型多代理和 personalized assistant：用户当前明确偏好应覆盖旧推断，但旧原始证据仍需保留以供审计。未来可加入多级 supersession 和异步写入。

## 5. Critical thinking

方法把“当前团队共识”近似为高权威真值，若共识本身错误，系统会系统性压低少数但正确的个人观察。两个新数据集主要来自 biomedical collaboration，可能与作者设定高度同构。建议引入共识反转、恶意团队更新、来源可靠度和时间分支，并比较软失效与不可逆删除。

## 6. 可信度判断

**3.5/5。** 已阅读全文。问题定义直接、指标覆盖完整且有人评；数据域窄、主要是作者构造 benchmark，外部真实团队和长期异步流证据不足。
