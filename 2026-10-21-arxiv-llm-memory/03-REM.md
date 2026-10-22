# 03. REM: What to Store, When to Recall, What to Forget in Experience Memory for Coding Agents

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27377)；[官方 PDF](https://arxiv.org/pdf/2610.27377)；[仓库 PDF](pdfs/2610.27377.pdf)
- 首次提交：19 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Xinyi Lisa Chen , Pedro Herrero-Vidal , Xiaohan Chen , Xiaojing Yu , Cris Liu , Bingqing Song , Bin Xu , Suleiman A. Khan , You-Lin Chen
- 机构（PDF 首页署名核验）：Yale University；Amazon
- 机构优先级：P1A；主题相关性：直接相关；研究标签：experience memory；读取时机；遗忘策略
- 阅读证据：正文§3–5、Limitations（PDF第3–10页）；首页。已获取完整 PDF（16页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

把经验记忆定义为存什么、何时注入、何时移除的生命周期问题。

## 2. 怎么做、实验如何设计

【论文直接证据】将55K–170K token轨迹整理成约270 token的定位/理解/修复/验证四阶段文档；top5相似检索后LLM重排。启动时提供短文档，验证失败时才注入最多12K字符的实现记录，一次曝光后移除。SWE-ContextBench Lite的99任务、300条经验；关键配置3次，其他配置多为单次方向性证据。

## 3. 结论

【论文直接证据】论文报告Match@1为68.7对55.6，解决率27.6对24.9，并降低约17%成本。即使oracle匹配的普通摘要和原轨迹也不保证有益，检索命中不能替代任务解决率。

## 4. 未来影响

【阅读者推断，尚待验证】记忆系统应优化注入干扰预算，而不仅是检索准确度；适合做可学习的读写/驱逐策略。

## 5. Critical thinking

【阅读者评析与后续建议】样本只有99题且共享仓库，任务独立假设不完全成立。固定经验池不是持续成长的在线记忆；struggle gate为手工验证失败信号。移除原记录并未移除模型已写入历史的派生内容。建议同token预算比较门控与随机时机，加入错误经验与仓库版本漂移，报告置信区间和逐任务受益/受损。

## 6. 可信度判断

**4/5**（与机构优先级独立）。有oracle、错误记忆、门控/持久化对照及配对检验；幅度不大，单次运行配置和任务相关性限制精度。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
