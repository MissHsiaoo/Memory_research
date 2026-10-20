# 5. PRAGMA: Evaluating Personalized Guidance with Memory Alignment in Lifelong Conversations

- **arXiv:** [2609.09664](https://arxiv.org/abs/2609.09664) (v1, 2026-09-09); metadata says **accepted to EMNLP 2026**.
- **Authors:** Hyojeong Yu, Hyukhun Koh, Minsung Kim, Yunah Jang, Kyomin Jung. **Affiliations:** not verified from available metadata.
- **Tags:** personalisation, lifelong conversation, memory evaluation
- **Evidence level:** abstract + metadata only.

## 1. What it does

PRAGMA evaluates whether LLM systems can give useful, personalised guidance from evolving conversations—not merely recall a stored fact. It explicitly includes changing preferences/experiences and incorrect user assumptions.

## 2. Method and experiments

The benchmark contains curated longitudinal histories, evidence annotations and guidance scenarios. It evaluates retrieval systems, memory systems and long-context LLMs, asking both whether they recover the right evidence and whether they use it for guidance. The abstract reports that all current families struggle; exact item counts, annotator protocol and metrics need full-text verification.

## 3. Conclusion

Memory recall is an insufficient proxy for personalised assistance. Systems fail at both evidence selection and evidence-grounded advice.

## 4. Future impact

This may become a better target than LongMemEval-style factual QA for personalised memory research. It is especially relevant for testing whether latent memory actually improves user-facing decisions.

## 5. Critical thinking

The difficult question is what counts as “good guidance” when preferences conflict or the user is mistaken. Evidence annotations improve diagnosis but can institutionalise one editorial view. Audit privacy/consent, temporal leakage, diversity of user situations, and whether judges reward agreeable prose over genuinely useful advice. Include human longitudinal preference judgments before using it as an optimisation target.

## 6. Confidence — **3.5/5 (important evaluation direction)**

**Strengths:** targets a real gap; separates retrieval from use; conference-acceptance metadata provides some signal. **Limits:** benchmark quality hinges on hidden construction/judging details; no full-text audit or affiliation verification; no result magnitudes in accessible material.
