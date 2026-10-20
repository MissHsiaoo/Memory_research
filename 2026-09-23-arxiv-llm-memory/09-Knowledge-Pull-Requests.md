# Knowledge Pull Requests：可审计的持续知识更新

- arXiv：[2609.26634](https://arxiv.org/abs/2609.26634)；[官方 PDF](https://arxiv.org/pdf/2609.26634)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Alexander Martin、Benjamin Van Durme；Johns Hopkins University
- 机构优先级：S（顶级研究型高校、直接相关）
- 研究标签：continual memory、knowledge update、provenance、conflict detection

## 1. 做了什么

KPR 将持续文档更新建模为“知识 pull request”：先说明哪些 claim 新增、冲突或覆盖，再生成文本 diff，从而把知识变化与写作变化分离。

## 2. 怎么做、实验如何设计

流水线从新来源抽取 claims，过滤并路由到文档 section，检测与现有内容冲突，生成 Claim Proposal + Document Diff 的 ChangeLog。作者在跨语言 Wikipedia revision 与 RAGTIME 的 temporal/conflict/balanced update 上测试，对比直接基于来源重写、基于 claims 重写和从头生成；指标覆盖新增信息、旧内容保留、faithfulness、QA grounding 与 token/review cost。

## 3. 结论

KPR 在两种设置中整合更多新信息、保留更多旧内容，并以更少生成 token 增加信息；在 RAGTIME 中显式标记冲突而不是静默决断，KPR 更新后的文档也比带 web search 的 frontier model 更适合作为某些跨语言事实的 QA grounding。

## 4. Future impact

它可直接迁移到 agent memory：每次写入不是覆盖 blob，而是提交可审核的 claim-level 更新、来源和冲突，支持回滚与权限治理。

## 5. Critical thinking

KPR 的上限受 claim extraction 与 entailment judge 限制；“显式冲突”并不自动解决真伪。Wikipedia 跨语言文本可能相互复制，不能完全视作独立证据。建议加入 source reliability、时间有效性、撤销链和人工审核时间，且评估错误 claim 是否被 ChangeLog 放大。与 event-sourcing/temporal KG 的差异也应在相同 schema 下比较。

## 6. 可信度判断

- 评分：4/5
- 依据：24 页全文、两个不同更新场景、三类 baseline、多维 intrinsic/extrinsic/cost 指标并公开代码。
- 优点：可审计、可落地；实验紧扣持续知识更新。
- 局限：依赖自动 claim/judge；长期多轮累积错误尚未充分验证。

