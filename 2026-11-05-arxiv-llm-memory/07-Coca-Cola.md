# 07. Tools Need Not Speak in Text: Latent Context Compression for Agents

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06500)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06500)；[仓库内 PDF](pdf/2611.06500.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Liu, Yuetong；Zhou, Zhehao；Zhang, Yitong；Chen, Haorui；Li, Jia
- 机构：首页署名已核验：Tsinghua University / Tsinghua AI Agent Group。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：latent memory; action-preserving compression。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–10；已获取完整17页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

把工具返回文本压成连续latent tokens，让代理读向量而非必须读可见摘要。

## 2. 怎么做、实验如何设计

上下文感知小模型接收任务、当前推理及观察，adapter映射到冻结代理的输入embedding；训练只更新压缩器LoRA和adapter，以完整观察下的下一行动分布做KL对齐，加轨迹行动交叉熵。Qwen与GLM两组模型，在NQ、TriviaQA、2Wiki、HotpotQA上对比原文、裁剪、摘要及同架构重建目标ICAE。

## 3. 结论

表1–3：总token减少70.01%–89.24%，耗时下降24.45%–55.97%；八种模型/数据设置均优于未压缩基线的EM/F1，但并非每项优于所有压缩基线，例如Qwen TriviaQA上ICAE更高。

## 4. 未来影响

推断：记忆的训练目标可以是保留决策所需信息，而非逐字重建。但下一步足够的信息未必足够支持后续所有任务。

## 5. Critical thinking

有限精度codebook容量只是潜在容量，不保证代理可读取或分布外鲁棒性。输入embedding接口不适用于仅提供文本API的模型；更换reader可能要重训。实验是搜索QA，尚不能证明长周期个性化、工具状态或安全授权信息保真。建议延迟查询、任务切换、罕见细节与拒答/授权对照，并做严格等预算及多种子分析。

## 6. 可信度判断

3/5。方法与结果可直接核对，重建目标对照有价值；场景和统计覆盖有限，不能从压缩率直接推出通用记忆能力。

## 官方提交记录

Submission history From: Yuetong Liu [ view email ] [v1] Wed, 4 Nov 2026 13:32:36 UTC (1,232 KB)
