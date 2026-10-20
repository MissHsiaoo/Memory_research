# GravityOCR：扩散起草、AR 验证的参数共享 OCR

- arXiv：[2609.26638](https://arxiv.org/abs/2609.26638)；[官方 PDF](https://arxiv.org/pdf/2609.26638)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Dohyun Kim 等；Trillion Labs、Korea University、Seoul National University
- 机构优先级：A（强校+公司、扩散方向直接相关）
- 研究标签：diffusion decoding、self-speculative decoding、AR verification、OCR

## 1. 做了什么

GravityOCR 将同一组参数同时用于 block-diffusion 起草与因果 AR 验证，利用 OCR 强视觉约束一次提出多 token，又由 AR 路径在提交前检查，避免并行 token 相互不一致。

## 2. 怎么做、实验如何设计

每个 forward 用 diffusion 提议 token block，AR 路径接受与逐 token top-1 一致的最长前缀；共享参数避免独立 draft model。作者从 GLM-OCR 适配，并通过 AR likelihood 做带序列/结构奖励的 GRPO。OmniDocBench v1.6 衡量精度，SGLang 部署测 crop decode 与整页端到端速度，同时检查 bf16 下与 AR greedy 的一致性。

## 3. 结论

GRPO 将 Overall 从 94.92 提至 95.16，接近原 GLM-OCR 95.48；平均每次 forward 提交 9.7 token，decode-only 提速 3.94×，整页端到端提速 1.32×。

## 4. Future impact

该范式可能推广到结构化生成：让 diffusion 并行提出、AR 路径负责精确验证，形成“快速联想 + 严格确认”的双系统解码。

## 5. Critical thinking

OCR 输出比开放文本更受输入约束，结果不能直接外推到通用 dLLM。3.94× decode 最终只变成 1.32× end-to-end，说明预处理/视觉 encoder 仍主导。应在代码、数学和自由生成上测试接受率、错误放大、不同长度，并与独立小 drafter 的真实内存/延迟比较。

## 6. 可信度判断

- 评分：4/5
- 依据：28 页全文、精度与系统速度同时报告、共享参数与 GRPO 消融逻辑完整。
- 优点：验证保证清晰；结果可部署；精度损失极小。
- 局限：领域特定；端到端加速有限；通用文本迁移尚未证明。

