# 11. Self-Evolving Beyond Human-Crafted Experience for EDA Scripting

- [arXiv 摘要](https://arxiv.org/abs/2611.26912) · [官方 PDF](https://arxiv.org/pdf/2611.26912) · [本地 PDF](pdfs/2611.26912.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-19（来自官方 submission history，非公告日期）。
- 作者：Liu, Yang; Tong, Shengbo; Chen, Xiyuan; Hou, Shiwei; Yuan, Sen; Wang, Hao; Li, Yanfeng; Li, Hongwen; Zhu, Yiming; He, Zhuolun; Yu, Wenjian。
- 机构：首页署名核验，CXMT、Tsinghua University、USTC。机构层级：B：强研究型高校/产业合作。
- 研究标签：agent memory；skill evolution；verified experience。
- 阅读依据：已下载并解析完整 7 页 PDF，目视核验首页；本评析重点核读 §III–V、治理机制与实验口径，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：3/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：面向EDA脚本，把执行轨迹整理成可复用知识，解决专有API、静默错误与跨任务经验传递。增强的执行harness与跨任务自演进分别评估，不能把两者收益合并归因于记忆。

## 2. 怎么做、实验如何设计

检索融合语义、关键词、BM25和API家族同义映射；增加文档属性、沙箱隔离与静态检查。L0原始轨迹、L1聚合模式、L2技能版本组成三层记忆；用外部评估覆盖agent自报成功。已验证条目被明确反证两次才过滤，五轮未确认会降级；规则经泛化检查。跨split检索只预注入API名，去掉调用顺序/参数等实例细节；验证下降超过5个百分点时回滚整轮。

## 3. 结论

论文证据：158题的harness-only实验无self-evolution，最佳92.4% pass@1；五模型均优于原ZhuLong。更难、实例不重叠挑战集上，论文报告自动演进80.0% vs人工经验77.5%，差2.5点。92.4%不是自演进相对人工经验的结果。

## 4. 未来影响

研究判断：可信经验的生命周期比“多记几个成功案例”更重要。其verified/unverified/pitfall分层、反证过滤和整库回滚可迁移到代码agent记忆。

## 5. Critical thinking

外部二值验证决定可信度，不能泛化到无确定验证器任务。158题harness配置每模型只跑一次；挑战集2.5点差距应结合样本和重复运行判断。5点容忍阈值允许真实退化被接受，反复使用验证集也可能过拟合。建议固定harness，仅逐项开关四类治理机制，使用API版本迁移与语义相近但参数不同的任务检验泄漏。

## 6. 可信度判断

3/5。机制详细、区分harness和memory、主动控制泄漏是优点；专有生态、benchmark需联系获取及有限重复运行降低独立可复现性。

