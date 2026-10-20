# 4. What Should an Agent Forget? Separating What Is Stored from What Is Used

- **arXiv:** [2609.10263](https://arxiv.org/abs/2609.10263) (v1, 2026-09-09)
- **Authors:** Yuhang Li, Yuchen Li. **Affiliations:** not verified.
- **Tags:** agent memory, forgetting, provenance, query-conditioned retrieval
- **Evidence level:** abstract + metadata only (8 pages, 3 figures, 3 tables reported).

## 1. What it does

RD-Forget argues that storage and use are different decisions. It never destroys historical observations, but builds a query-conditioned “memory view” that suppresses superseded facts for current-state questions and revives them for historical questions.

## 2. Method and experiments

A frozen LLM curator extracts evidence, groups facts into semantic slots and preserves multi-hop relations. Same-slot replacement links and intent-aware retrieval construct the answer-time view. A rate–distortion objective controls it under a budget. The abstract says experiments span conversational memory, knowledge updating, fact consolidation, long-context reasoning and personalisation, with ablations of forgetting, query conditioning, slot grouping, historical access and relation preservation.

## 3. Conclusion

“Forget” should typically mean reduce answer-time influence, not delete evidence. This is compatible with future audit, correction and historical QA.

## 4. Future impact

This is a compelling invariant for personal memory products: lossless archival provenance plus deliberate active-state selection. It can complement FR’s lifecycle policies and ROAM’s roles.

## 5. Critical thinking

The abstraction risks pushing complexity into the curator and the definition of intent. Rate–distortion may sound principled while its utility/distortion choices are task-tuned. Test for contradictions where current and historical facts must be jointly reasoned over, evaluate curator hallucinations, and report storage/query latency versus methods that truly delete/compact memory.

## 6. Confidence — **3.0/5 (conceptually sound, empirical detail sparse)**

**Strengths:** sharp conceptual separation; provenance-preserving; broad claimed evaluation scope. **Limits:** no numbers/datasets or code details in the available abstract, making claimed breadth hard to assess.
