# 15. Open CDLM: A Benchmark and Library for Continuous Diffusion Language Models

- [arXiv 摘要](https://arxiv.org/abs/2611.27536) · [官方 PDF](https://arxiv.org/pdf/2611.27536) · [本地 PDF](pdfs/2611.27536.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Jiang, Hao; Chen, Ruixi; Han, Jiayi; Sun, Yulei; Chen, Yujian; Li, Gen; Chen, Brian. K; Cheng, Guang; Luo, Weijian; Hu, Tianyang。
- 机构：首页署名核验，Polyadic Research Group、CUHK-Shenzhen SAGA Lab、Peking University、CUHK、National University of Singapore、UCLA、Xiaohongshu Dots Studio。机构层级：B：强研究型高校/实验室。
- 研究标签：diffusion LLM；benchmark；distributional evaluation。
- 阅读依据：已下载并解析完整 36 页 PDF，目视核验首页；本评析重点核读 §2–3、评测反例、§8局限，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：3/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：提出连续扩散语言模型评测框架，分清模型离散似然、变分界、实际采样器分布及样本集合质量。不是宣称一种新生成模型全面领先的榜单论文。

## 2. 怎么做、实验如何设计

似然侧显式区分真实离散NLL与NELBO的后验KL slack，要求匹配语料、tokenizer和评分边界；生成侧提出KTD及多样性/覆盖/有效性诊断，用real-vs-real和不确定性参考。用OWT原文构造跨样本重复、文内重复、拼接及模板替换等可控退化，检查Gen PPL、单样本熵和MAUVE是否响应。似然研究使用一个归档LangFlow checkpoint；短文本pilot与1024-token似然实验不合成同一性能表。

## 3. 结论

论文证据：文内重复使Gen PPL从15.14降到4.63，而样本熵仅由5.443到5.264；混合退化仍可保持接近真实文本的熵。常用双指标能被明显退化文本同时“优化”。MAUVE能发现collapse，但对其他扰动受表征/扰动类型影响；界更紧或数值更低不自动证明模型真实似然更好。

## 4. 未来影响

研究判断：为diffusion memory或latent-memory生成研究提供重要评测纪律：输出多样性和分布覆盖不能被一条平均质量分替代。

## 5. Critical thinking

目前是评测方法与有限pilot，不应将计划中的library/baseline release写成已独立验证的完整成熟生态。一个OWT shard、三fold无文档ID，抽样单位与重叠要谨慎；KTD同样依赖表征，未证明与人类偏好一致。建议跨语料、条件生成、独立文档采样及人评验证，同时报告feature提取成本。

## 6. 可信度判断

3/5。反例与数学对象区分清楚，对错误评测结论具有较强警示价值；广泛模型排名、普适指标优越性和大规模复现证据仍有限。

