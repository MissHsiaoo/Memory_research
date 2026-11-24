# 13. Explicit Style Extraction for Personalized Long-Form Text Generation

- [arXiv 摘要](https://arxiv.org/abs/2611.27211) · [官方 PDF](https://arxiv.org/pdf/2611.27211) · [本地 PDF](pdfs/2611.27211.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Patel, Jenitha Reddy; Kini, Sameeksha; Rayasam, Amulya; Dye, Anisa; Sharma, Abhinav; Navuluru, Sai Karthik; Ni, Bo; Li, Li; Wu, Junda; Yu, Tong; Lipka, Nedim; Huang, Xiaolei; Derr, Tyler; Zhao, Yue; Tu, Zhengzhong; Wang, Yu; Chen, Hongjie; Nguyen, Thien Huu; Ahmed, Nesreen K.; Dernoncourt, Franck; Rossi, Ryan A.。
- 机构：首页署名核验，University of Chicago、UMass Amherst、UT Dallas、Vanderbilt、USC、Adobe Research、UCSD、University of Missouri、University of Memphis、Texas A&M、University of Georgia、University of Oregon、Dolby Laboratories、Amazon、Cisco、Zillow。机构层级：B：强研究型高校/产业合作。
- 研究标签：personalized memory；style profile；long-form generation。
- 阅读依据：已下载并解析完整 21 页 PDF，目视核验首页；本评析重点核读 §3–7、表1–2及Limitations，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：把用户写作风格显式提取成可检查profile，以28方面/7类别的STYLEPRISM指导长文修订。重点是如何使用个人历史，而非训练新的记忆存储架构。

## 2. 怎么做、实验如何设计

固定检索器取k=4历史样本，profile各项写模式、原句证据、避免事项，信息不足应标不可观察。先从样本直接起草，再结合profile修订和自评分，最后针对低分项二次修订。LongLaMP三任务全测试集：4560摘要、1822评论、2452主题写作；三种生成器、相同历史样本，与无profile、随机样本、标准RAG、隐式推断和profile-only比较。指标包括ROUGE/METEOR与九维LLM评分，另有oracle/reference-free控制。

## 3. 结论

论文证据：27个生成器×任务×指标组合中25项优于LongLaMP，平均相对增幅10.2%；风格评分8/9设置提高，但GPT评论风格评分下降，GPT摘要任务质量也下降。只用profile取代样本在27项均更差；便宜的单次隐式推断已接近完整流程。不是“结构化记忆可完全替代原文”的证据。

## 4. 未来影响

研究判断：个人记忆可拆成原始例子、抽象profile和修订检查三个用途。值得把profile当带证据的可编辑约束，保留原始样本供消歧。

## 5. Critical thinking

ROUGE和单参考相似度不能直接量化用户偏好；裁判同时也是一个生成模型，与方法自评共享风格维度。只覆盖英语固定k，缺用户盲评和偏好随时间变化。建议预算匹配单次强提示/多次重写，做同内容不同风格与同风格不同内容测试；让用户选择，测事实保持、style、成本三个独立目标。

## 6. 可信度判断

4/5。大测试集、三模型、profile-only和oracle消融有说服力；没有独立人类偏好验证，闭源API可变，尚不足证明真实用户长期满意度。

