# 17. Embodied-Harness: Towards Recursive Self-Improvement for Robotic Manipulation

- [arXiv 摘要](https://arxiv.org/abs/2611.27689) · [官方 PDF](https://arxiv.org/pdf/2611.27689) · [本地 PDF](pdfs/2611.27689.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Fan, Zhenxuan; Wang, Zhuoya; Yuan, Yuqian; Zhang, Wenqiao; Li, Juncheng; Xiao, Jun; Tang, Siliang; Zhuang, Yueting。
- 机构：首页署名核验，Zhejiang University、Huazhong University of Science and Technology。机构层级：B：强研究型高校/实验室。
- 研究标签：agent memory；hierarchical memory；embodied self-improvement。
- 阅读依据：已下载并解析完整 20 页 PDF，目视核验首页；本评析重点核读 §3、§4及表2–6，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：3/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：Actor执行、Reflector分析证据并更新harness；用短期工作记忆和长期经验记忆支持机器人反复尝试与跨任务复用，不更新基础模型参数。

## 2. 怎么做、实验如何设计

短期包括压缩任务进度与完整执行明细；长期分任务特定经验和跨任务原则。反思联系观测、动作、反馈，生成空间、接触、协调、恢复等可执行指导。测试RoboTwin2.0 C2R、RoboSPA、RMBench和三项真实机器人任务；在RoboSPA-Long L5消融Reflector、短期、长期与证据grounding，并比较多VLM/推理强度。

## 3. 结论

论文证据：RMBench九项平均94.4%；RoboSPA-Long L5成功率59.5、进度74.9。移除短期memory成功率32.1，移除长期48.5，移除Reflector43.0，移除证据grounding52.3。真实三任务平均96.7%，但少量任务的高比例不能外推为普遍机器人可靠性。

## 4. 未来影响

研究判断：对多目标记忆的启发是同一经历服务两种消费者：Actor用细节控制当前动作，Reflector用抽象经验改未来策略。可研究保真细节与可迁移抽象的存储预算分配。

## 5. Critical thinking

各消融移除的信息量与计算量不同，效果不一定纯来自“层级结构”。强模型依赖明显，GPT-6 Astra显著高于所测开源模型。与外部VLA/WAM比较需核对感知、工具、重试和经验预算。建议固定执行器，对同任务重复经验与跨任务迁移分别报告，给出首次尝试/多次尝试以及记忆写入成本。

## 6. 可信度判断

3/5。多任务、实体机器人和模块消融支持框架有用；独立重复、预算公平性与泛化边界尚需更细验证，不能由最高平均SR判断机制已经充分证明。

