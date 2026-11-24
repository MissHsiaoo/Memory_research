# 19. NavRSI: Recursive Harness Self-Improvement for Vision-and-Language Navigation

- [arXiv 摘要](https://arxiv.org/abs/2611.27499) · [官方 PDF](https://arxiv.org/pdf/2611.27499) · [本地 PDF](pdfs/2611.27499.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Dai, Guangzhao; Lian, Guoxin; Wang, Shuo; Yue, Shengbin; Sun, Qianru; Shu, Xiangbo; Zhu, Bin。
- 机构：首页署名核验，Singapore Management University、Renmin University of China、Fudan University、Nanjing University of Science and Technology。机构层级：B：强研究型高校/实验室。
- 研究标签：self-evolving memory；designer experience；navigation。
- 阅读依据：已下载并解析完整 11 页 PDF，目视核验首页；本评析重点核读 §3–4、表4–5及信息隔离协议，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：3/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：冻结导航模型，仅根据执行失败重写harness，并保存designer的改写经验。记忆保存的是“为什么改、哪些改动有效、下次避免什么”，不是给导航器额外堆一张人工地图。

## 2. 怎么做、实验如何设计

单RGB相机、observe和step两个工具、原子移动/转向。designer每轮新session，读取训练日志、诊断和经验，产生三个候选；先规则检查/干跑，再分阶段评测，共八轮。导航器看不到模拟器特权诊断，designer看不到图像。训练search最多200回合；1302 val-unseen作开发选择，其余537回合为域内heldout（含R2R-CE-100），另测RxR-CE与NavRAG-CE。最终同harness测试17个模型。

## 3. 结论

论文证据：R2R-CE-100中GPT-5.6-Sol由56.7±2.5到68.0±4.0，三运行；17模型普遍改善但大小不同。无先前记录时52.8%新改写重复已有改写，经验记录可减少重复。论文报告完整R2R-CE85.64%包括用于选harness的开发部分，不能把完整集合分数都称独立heldout。

## 4. 未来影响

研究判断：agent memory也可以服务于优化器本身，记录实验假设、噪声判断与失败路线；这比只保存最终成功技能更有研究价值。

## 5. Critical thinking

同一开发集反复选最终harness、特权诊断和强designer成本都要计入。信息隔离改善泄漏控制，但没有消除搜索适配。建议固定总API预算、按新环境完全留出，比较仅日志/仅经验/两者及随机改写；重点测后续轮次新增收益和跨任务重复失败。

## 6. 可信度判断

3/5。跨模型、分层split、重复运行与日志记忆设计有价值；完整集合headline包含开发数据，效率优势也依赖具体API/配置，需要使用真正heldout表作主要证据。

