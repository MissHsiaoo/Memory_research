# 05 — SkillFM: Generating Skills for LLM Agents via Latent Flow Matching

- arXiv：[2609.39382](https://arxiv.org/abs/2609.39382)；[官方 PDF](https://arxiv.org/pdf/2609.39382)；[本地 PDF](./2609.39382.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Zuming Zhang 等；Nanyang Technological University、University of Edinburgh、Meta
- 机构优先级：**S，Meta 合作与一流高校**；研究标签：`latent skill` `agent memory` `flow matching`
- 证据：已核读 PDF 方法、实验与结论；以下数值为作者报告。

## 1. 做了什么

把可复用文本 skill 编码到连续潜空间，再根据任务生成新 skill，供冻结 agent 使用，推理时无需检索 skill 库。

## 2. 怎么做、实验如何设计

先从执行轨迹构建任务—skill 库，训练可重构 codec，再以 improved MeanFlow 训练条件流；单步采样 latent 后由 LLM 解码为文本指导。ALFWorld、Search-QA 和 WebShop 测试包含任务成功率/问答准确率，并对 skill 库规模、质量和 executor 迁移做分析；论文报告在所比向量式 skill 方法中整体表现最好。

## 3. Conclusion

技能可以从检索对象变为条件生成对象；潜空间生成可把已有技能库压入模型化先验。

## 4. Future impact

对 self-evolving agent memory 有启发：未来可按新任务组合已有经验，而不受固定文本条目和相似度检索限制。

## 5. Critical thinking

**推断：** 生成的 skill 可能流畅却不可执行，且 latent codec 难以审计、撤销单条经验。应比较相同训练数据与总成本下的强检索基线，加入 skill 安全验证、分布外任务和错误技能库污染测试。

## 6. 可信度判断

**4/5。** 方法组件和三类任务覆盖较完整，代码与训练技能库已说明可用。局限是“最好”针对所选比较集，生成技能的可解释与长期在线更新仍需验证。
