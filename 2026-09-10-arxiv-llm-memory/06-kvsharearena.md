# 6. KVShareArena: KV-Cache Reuse Across Contexts and Model Checkpoints

- **arXiv:** [2609.10266](https://arxiv.org/abs/2609.10266) (v1, 2026-09-09)
- **Authors:** Xi Shi, Qian Lou. **Affiliations:** not verified.
- **Tags:** KV cache, agent reports, RAG systems, memory systems
- **Evidence level:** abstract + metadata only.

## 1. What it does

KVShareArena benchmarks cache reuse where the cached text is no longer a prompt prefix: RAG chunks reordered per query and reports exchanged among agents. It also tests caches written by a different checkpoint of the same family.

## 2. Method and experiments

It evaluates position correction, partial re-encoding and trained adapters across retrieved chunks and agent reports. The score is fraction of the quality gap recovered relative to no cache/full recomputation, while separately charging compute, memory, request latency and cache-build cost. The abstract reports that position correction works until multi-source questions, after which methods that pay for recomputation/training recover roughly half to two-thirds of the gap; it covers three model boards and ships a harness/leaderboard.

## 3. Conclusion

Exact-prefix cache hits are a misleadingly easy case. Reuse is sometimes useful, but semantic/multi-source integration makes position-only repair inadequate.

## 4. Future impact

It could become infrastructure for agent-memory systems whose documents, reports and learned memory shards are frequently recomposed. Better cost accounting is very welcome.

## 5. Critical thinking

This is a benchmark, not a universal cache solution. “Fraction of gap recovered” may hide catastrophic answer failures, so include per-query tails and safety-sensitive cases. Confirm that caches from varying model versions and RoPE/scaling configurations are representative; a benchmark maintained by one community may overfit repair methods to its traces.

## 6. Confidence — **3.5/5 (useful systems evaluation)**

**Strengths:** realistic non-prefix setting, cost accounting, explicit cross-checkpoint question. **Limits:** abstract does not identify model boards/workloads or reproducibility conditions; quality metric may need task-specific complements.
