# 3. ConvMem: Convolutional Memory for Long-Context Reasoning

- **arXiv:** [2609.10441](https://arxiv.org/abs/2609.10441) (v1, 2026-09-09)
- **Authors:** Hongming Zhang, Zhaozhen Gu, Fengshuo Bai, Ming Hao, Qingyang Zhang, Yuanyuan Wang, Shiyang Tang, Yanna Wang, Bo Xu. **Affiliations:** not verified.
- **Tags:** long context, hierarchical summarisation, training-free memory
- **Evidence level:** abstract + metadata only.

## 1. What it does

ConvMem reframes sequential memory updates for long-context QA as a hierarchical convolution. It aims to replace linear read–update chains with a logarithmic-depth tree, retaining a fixed-size textual memory while allowing parallel processing.

## 2. Method and experiments

The queried LLM acts as a convolutional kernel over text segments. Configurable strides and skip connections are intended to retain evidence; multi-kernel convolution decomposes complex queries into semantic channels. It is training-free. Experiments named in the abstract are RULER-HotpotQA and RULER-2WikiMultiHopQA, compared with training-free baselines; the authors claim better performance and reduced exposure to RL-induced parametric-prior overfitting on OOD tasks.

## 3. Conclusion

The central claim is architectural: hierarchical aggregation can trade sequential dependency for parallelism while limiting accumulation error.

## 4. Future impact

If cost and evidence recall hold at larger scales, this could be a simple execution substrate for agent memories—particularly batchable document ingestion. Its query-conditioned compression differs usefully from generic chunk summaries.

## 5. Critical thinking

Convolution is an analogy, not automatically a guarantee: cross-segment dependencies may be lost when local summaries are composed. The key missing evidence is wall-clock/cost scaling under a fixed model and token budget, plus adversarial “needle” cases whose required facts are far apart. Multi-kernel prompting can multiply cost; compare it with the same number of sequential calls and a strong retrieval baseline.

## 6. Confidence — **3.5/5 (plausible, immature evidence)**

**Strengths:** training-free, explicitly parallel design, addresses a real failure mode of recurrent textual memory. **Limits:** no reported magnitudes, compute, prompts, or split details in the accessible evidence; benchmark generalisation beyond multi-hop QA is unproven.
