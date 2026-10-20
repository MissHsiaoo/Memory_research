# 02. Just-in-Time Memory

- 论文：**Just-in-Time Memory: Learning to Curate Task-Adaptive Memory for LLM Agents**
- arXiv：[2609.27334](https://arxiv.org/abs/2609.27334)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Yefan Zhou 等；Salesforce AI Research
- 机构优先级：**S｜顶级工业研究机构**
- 研究标签：agent memory、read-time curation、episodic memory、GRPO
- 本地 PDF：[2609.27334.pdf](./2609.27334.pdf)

## 1. 做了什么

挑战“记忆必须在写入时总结”的主流设计。JITMEM 保留完整原始轨迹，在未来任务已经明确的读取时刻，再把检索到的轨迹压缩为面向当前任务的临时 payload，从而避免过早、不可逆的信息丢失，也把长期信用分配改造成即时任务奖励。

## 2. 怎么做、实验如何设计

系统由原始轨迹库、BM25 任务描述检索器、可训练 curator 和冻结 executor 构成。curator 根据当前任务和 top-k 原始轨迹生成简洁指导；任务结束后仅将质量门控通过的完整轨迹写回库。训练时固定轨迹库，curator 为同一任务生成多份 payload，冻结 executor 执行后用原生任务奖励进行 GRPO 更新。实验覆盖 ALFWorld（140）、WebShop（500）和 τ2-bench，executor 包括 Qwen3-8B、Gemini-2.5-Pro、GPT-5.4；与 no-memory、ReasoningBank、MemP、SkillOS 等写时记忆比较并使用不同任务顺序重复。相对最强基线，成功率分别提升 16.2、16.3、3.9 个百分点；输入 token 减少 50.3%–56.3%，executor 步数减少 28.4%–31.4%。

## 3. Conclusion

任务条件化的读取时整理本身就是主要增益来源：即使不训练 curator，也常与或超过写时方法；RL 训练进一步提高效果，并能迁移到更强 executor。

## 4. Future impact

这可能成为 persistent agent memory 的重要分层：写入层保存可审计原始经验，读取层按任务即时编译“工作记忆”。未来可与实体索引、时间索引、隐私删除和多模态轨迹库结合。

## 5. Critical thinking

最强创新是把“何时压缩”从存储时移到使用时，直接解决一对多未来查询和 delayed credit。代价是原始轨迹库持续膨胀，隐私、存储、检索延迟与错误轨迹污染被推迟而非消除；BM25 只看任务描述也可能漏掉语义相关但描述不同的经验。论文主要在有限任务流上验证，尚未证明数百万轨迹下的可扩展性。建议增加随库规模增长的延迟/成本曲线、删除请求、失败轨迹可用性、学习检索器与跨用户污染实验。

## 6. 可信度判断

**5/5。** 已阅读全文；问题定义、训练信号、强基线、跨 executor 迁移、消融和效率指标都较完整。优势是因果链清晰且直接相关；主要局限是长期存储扩张与隐私治理未被系统验证。
