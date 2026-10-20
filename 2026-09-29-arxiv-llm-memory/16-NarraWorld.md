# 16. NarraWorld

- 论文：**Shared Worlds, Private Minds: Structured Memory for Long-Form Writing as World Creation**
- arXiv：[2609.32401](https://arxiv.org/abs/2609.32401)；[官方 PDF](https://arxiv.org/pdf/2609.32401)
- 提交日期：2026-09-26；正式公告批次：2026-09-29（北京时间）
- 作者/机构（官方全文首页核验）：Beijing Zhongguancun Academy、Southeast University、Duke University、Renmin University、ZhuiWen Technology 等
- 机构优先级：**A｜强研究机构/高校合作**
- 研究标签：structured memory、long-form generation、world model、personalized narrative
- 证据范围：已阅读官方全文 HTML；本地 PDF 下载超时。

## 1. 做了什么

NarraWorld 将长篇写作记忆视为持续构建 storyworld，而非平铺事实列表：区分世界事实、角色私有认知、承诺、关系与后果，并恢复请求中未显式写出的依赖。

## 2. 怎么做、实验如何设计

系统构建多类型结构化记忆并进行依赖规划、预览引导重构；在 ConStory-Bench、LSGC、Tell-Me-A-Story、角色扮演和 LoCoMo 等任务评测一致性、故事质量与 QA，并提供检索、记忆、人工评价和 judge 对齐消融。

## 3. 结论

长程生成需要区分“共享世界”和“角色知道什么”，再按任务重建依赖；只召回相似片段不足以维持叙事因果。

## 4. Future impact

其 shared/private memory 分层可迁移到多用户助手：系统事实、个人偏好与权限可分开建模，避免不同主体记忆串扰。

## 5. Critical thinking

强项是对记忆语义作了细粒度建模，并用多 benchmark 与人工评价验证。局限是 ontology 建设和 LLM judge 成本高，虚构世界的“真值”比现实个人记忆更容易定义。建议测试冲突事实、角色误信念、权限泄露与跨月编辑。

## 6. 可信度判断

**4/5。** 实验与限制讨论完整，结构设计有启发；对通用 agent memory 的迁移仍是推断，不能直接等同于现实对话记忆。

