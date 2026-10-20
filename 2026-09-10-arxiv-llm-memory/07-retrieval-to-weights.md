# 7. From Retrieval to Weights: Parametric Individualization of Small Language Models with Individual Text Corpora

- **arXiv:** [2609.10155](https://arxiv.org/abs/2609.10155) (v1, 2026-09-09)
- **Authors:** Christoph Wigbels, Ali Abusaleh, Markus T. Jansen, Alexander Mehler, Markus J. Hofmann. **Affiliations:** not verified.
- **Tags:** personalised memory, parametric memory, LoRA/DoRA, individual text corpora
- **Evidence level:** abstract + metadata only.

## 1. What it does

The paper asks whether an individual’s text corpus can be consolidated into a small language model’s weights, compared with retrieval-augmented generation. It frames this as a cognitive simulation of episodic/semantic memory.

## 2. Method and experiments

The authors crawl search histories from 515 participants who answer 36 multiple-choice items, then analyse a stratified 150-person subset. Per person, they train a DoRA adapter on a small LM. They test held-out text fit and a generalised knowledge task, comparing the adapter and retrieval. The abstract reports individual-specific held-out fit (dz=1.27) but says the adapter adds knowledge without improving bias-corrected accuracy alignment; retrieval adds no further benefit.

## 3. Conclusion

Personal corpora can leave an individual-specific parametric trace, but that does not automatically create a better behavioural model of the person. This is a valuable limit result for LLM personalisation.

## 4. Future impact

It provides a warning against equating “stored in weights” with faithful personalisation. Hybrid systems should optimise user-aligned decisions explicitly, preserve provenance, and protect sensitive individual data.

## 5. Critical thinking

Search history is a noisy and privacy-sensitive proxy for personal knowledge or preference. Only 36 questions may give low power for behavioural alignment. DoRA capacity/model size and task formulation can explain the negative retrieval result. Replicate with consented diary/conversation data, temporal holdouts, user-rated advice, and privacy attacks (membership/inversion) before treating personal adaptation as safe.

## 6. Confidence — **3.5/5 (useful, narrowly scoped evidence)**

**Strengths:** participant-level design, separates text fit from alignment, reports effect size, avoids an overclaimed conclusion. **Limits:** small downstream test, proxy validity/privacy questions, unknown model/training controls from the available abstract.
