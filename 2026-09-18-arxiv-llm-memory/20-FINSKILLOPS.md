# 20. FINSKILLOPS: A Self-Evolving Multi-Agent System for SEC Filing QA

- arXiv：[论文页面](https://arxiv.org/abs/2609.19680v1)｜[官方 PDF](https://arxiv.org/pdf/2609.19680v1)｜[本地 PDF](papers/20-FINSKILLOPS-2609.19680.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Yanzhang Ma , Zhenghan Tai , Hanwei Wu , Sizhe Guan , Jianliang Lei , Hailin He , Chaolong Jiang , Jijun Chi , Tung Sum Thomas Kwok , Bohuai Xiao , Jingrui Tian , Xinlu Wu , Xingao Zhan , Peng Lu , Muzhi Li , Yihong Wu , Liheng Ma , Sicheng Lyu , Tianshuo Yan , Junhao Zhu , Yaqian Xu , Lei Ding , Yufei Cui , Ziquan Liu , Boyu Han , Hengli Liu , Ling Zhou , Xinyu Wang
- 机构：SimpleWay.AI 主导；首页含 McGill、University of Toronto、UCLA、CUHK、Mila、McMaster、Harvard、Monash、HKU、Stanford、Queen Mary 等合作署名（机构列表不等于各方均主导）。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P2｜初创机构主导/多所强高校合作；直接相关
- 研究标签：self-evolving skill memory；scoped patches；admission/retirement
- 入选理由：不是优先大公司主导，故后置；其 scoped skill、no-regression gate 与版本退休对可靠 self-evolving memory 特别有启发。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

FINSKILLOPS 将金融文件 QA 的改进视为受控行为维护：反复错误转成带作用范围的 skill patches，而不是无限添加通用反思。每条 patch 需要目标验证、既有正确案例保护、negative controls，并支持版本替换与退休。研究价值在记忆/技能生命周期与上线门槛，不是提供交易盈利策略。

## 2. 怎么做，实验如何设计

六个 benchmark 包括公开 FinanceBench、SECQUE、FinDER 与三个内部集合；enhanced 集 114 题，含 84 Zeekr、20 Lotus、10 NVIDIA。主要比较使用冻结 skill registry，由 Qwen3-Max judge 给 0–5 的 verdict-weighted correctness 等分数；作者用 150 项人工标注检查 judge 一致性，报告不同判定 κ 约 .82/.675。另有 12 轮 operational monitoring study，共 33 个提案，仅 6 个 promoted。监控循环同时改变诊断/路由，不是完全孤立的 memory 更新实验。

## 3. 结论

enhanced 正确性从初始 3.70 到 4.55；公开 FinanceBench 3.15 到 3.49、FinDER 2.68 到 2.88，改善幅度小于内部集。ungated 目标成功点值可高于 gated，但出现 3 个保护案例 regression，gated 为 0；说明入库门槛有代价与价值。监控 non-correct rate 20.0%→12.5% 是同一 operational 流程的变化，不能等同于盲测部署总体风险下降。

## 4. 未来影响

我的推断：self-evolving memory 不该把每个失败都立即写成通用规则。更合理的是候选区、作用范围、证据、受保护旧行为和可撤销版本，只有验证后晋升正式 registry。它可启发个性化记忆的更新批准机制，防止一次用户行为覆盖长期稳定偏好。

## 5. Critical thinking

主要风险是内部数据收益更大、评测多依赖模型 judge，及公开 admission logs/split manifests 仍不完整，使是否严格隔离 patch 生成与测试难以全面复现。12 轮反复看监控集合也不同于一次冻结后的未知分布评价。合作强高校很多不等于顶级机构主导，不能按 Harvard/Stanford 名字自动前排。建议公开逐 patch lineage、冻结盲测 SEC 公司/时间切分，等预算比较 ungated/gated，并让域专家独立核验财务数值与引用；退役机制需测试误删好 skill 的代价。

## 6. 可信度判断

可信度 3/5：全文有明确维护流程、消融与人工 judge 一致性，优点是重视作用域和不回退，而非只追求高分。局限是内部基准、LLM 评分、artifact 不完整、监控集合复用与多组件变化。作为较低机构优先级的强合作补充收录，证据评分独立；本文不证明金融建议安全或任何投资回报。

