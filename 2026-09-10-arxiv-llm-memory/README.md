# arXiv LLM Memory Daily Select — 2026-09-10

> **已更新：请阅读 [今日近 30 天重选版：20 篇 + PDF + 中文批判性笔记](reselected-30d/README.md)。** 新版按已核验的机构优先级重选，并阅读原文方法与实验。以下 7 篇为初版归档，不再代表今日正式推荐名单。

**Scope.** New arXiv submissions available in the 2026-09-09 UTC batch were screened across cs.CL and cs.AI for latent/external memory, long-context memory, personalisation, ICL and self-evolving agents. I retained **7 papers**, rather than padding to 20: these are the ones with a direct research fit and a concrete method or evaluation contribution. No retrieved record supplied verifiable affiliations; therefore this issue does **not** label any paper as a top-company/top-university paper. That filter remains a priority for future runs when the PDF/author page permits verification.

## Novelty-ranked shortlist

1. [Fortunate Recall](https://arxiv.org/abs/2609.10413) — typed lifecycle policies + unusually candid decomposition of where the gain comes from.
2. [ROAM](https://arxiv.org/abs/2609.09778) — relation-aware atomic memory organisation with answer-time fusion.
3. [ConvMem](https://arxiv.org/abs/2609.10441) — tree/convolution view of query-conditioned long-context memory; training-free and parallel.
4. [RD-Forget](https://arxiv.org/abs/2609.10263) — cleanly separates archival retention from query-time forgetting.
5. [PRAGMA](https://arxiv.org/abs/2609.09664) — evaluation moves beyond factual recall to personalised guidance in changing life histories.
6. [KVShareArena](https://arxiv.org/abs/2609.10266) — a systems benchmark for reuse of non-prefix / cross-checkpoint KV caches.
7. [From Retrieval to Weights](https://arxiv.org/abs/2609.10155) — a useful negative result on parametric individualisation versus retrieval.

## Today’s reading signal

The dominant trend is **memory governance rather than memory capacity**: FR, ROAM and RD-Forget all argue that time, contradiction, provenance and query intent must decide what is active. The striking open question is evaluation: gains on synthetic or judge-based memory QA do not yet establish that a system gives genuinely better personalised advice. PRAGMA is therefore strategically important despite being a benchmark.

### Three papers to read first

1. **Fortunate Recall**: strongest explicit lifecycle decomposition, release claims, and calibration outcome; inspect its pre-registration and the generic-policy ablation.
2. **ROAM**: closest direct design input for a self-evolving agent memory stack; validate whether its pairwise relation classification remains affordable at scale.
3. **PRAGMA**: a needed evaluation target if your goal is personalised memory rather than only fact recall.

## Evidence policy

All notes are grounded in the arXiv metadata/abstract available at run time. Scores are provisional; PDF-level details (split construction, prompts, significance tests, and affiliations) were not available to the retrieval channel and are marked accordingly rather than invented.
