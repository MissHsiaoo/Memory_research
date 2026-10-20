# 10. User Model Extraction via Belief Self-Distillation

- arXiv：[2609.31603](https://arxiv.org/abs/2609.31603)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.LG new / cs.CL cross-list）
- 作者/机构（PDF 首页核验）：Ali Holmov 等；Technical University of Munich、Helmholtz Munich
- 机构优先级：**A｜全球一流研究型高校/研究中心**
- 研究标签：LLM personalization、latent user model、causal steering、safety
- 本地 PDF：[2609.31603.pdf](./2609.31603.pdf)

## 1. 做了什么

提出 Belief Self-Distillation（BSD），从自然对话中抽取一个既可读又可写回的 128 维 latent user state；研究对象不是用户真实属性，而是 LLM“相信用户是谁”，并证明该信念会因果影响拒答。

## 2. 怎么做、实验如何设计

冻结 Llama-3.1-8B、Qwen3-8B、OLMo-3-7B，让原模型对 13 类人口/安全属性产生 teacher belief，再训练低秩读写投影，使不看对话的 student 仅靠 user vector 重现 belief。数据约 27k WildChat + 31k WildJailbreak；读出用线性 probe，写入用匹配范数的 CAA，并对 86 个属性对各采样 50 项。32× 压缩后 macro-F1 距原 hidden state 不超过 4%；Llama 上 BSD steering flip rate 78%，原状态 21%、随机 13%，且三模型均有优势。

## 3. Conclusion

隐式用户模型是可压缩、可因果编辑且安全相关的内部状态；显式 persona cue 训练的 probe 在自然对话上仅约 0.39–0.43 macro-F1，说明“声明的画像”与“自然形成的信念”不同。

## 4. Future impact

这为 latent personalized memory 提供了清晰对象：持久化的不是文本档案，而是模型自身用于条件化行为的用户信念向量；同时需要审计该向量是否诱导歧视或绕过安全。

## 5. Critical thinking

关键贡献是统一 read/write 并做因果干预。限制是 13 个预设多选属性塑造了表示，不能等同于完整开放式 user model；平均 37% 非目标属性也发生 flip，选择性仍不足。建议研究随时间更新、可撤销写入、开放属性发现、跨层/跨尺度迁移，并把真实用户授权和隐私泄露纳入评测。

## 6. 可信度判断

**4.5/5。** 已阅读全文。三模型、强随机控制、自然对话和因果写入证据扎实；白盒、小规模模型、单层线性投影限制了对闭源助手与长期个性化的外推。
