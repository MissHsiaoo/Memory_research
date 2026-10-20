# 10｜DynaTE：扩散 LLM 的动态 token 执行

- 论文：[arXiv:2610.11284](https://arxiv.org/abs/2610.11284)；[官方 PDF](https://arxiv.org/pdf/2610.11284)；[本地 PDF](10-DynaTE.pdf)。主分类 cs.AR，2026-10-09 公告批次 New submissions；首次提交 2026-10-08（UTC），v1。
- 作者/机构（PDF 首页脚注）：Minghan Jiang、Jiayi Wang、Shuaiting Li、Haibin Shen、Kejie Huang；浙江大学信息与电子工程学院。
- 机构优先级：S；标签：diffusion LLM、推理加速、硬件软件协同；相关性：直接；novelty：高。

## 1. 做了什么

提出面向 dLLM 迭代去噪的 DynaTE 加速架构：既跳过低效益 token 的计算，又处理这种选择性执行造成的硬件利用率和词表处理不均衡。

## 2. 怎么做、实验如何设计

软件侧判定 token 的动态执行效益，硬件侧重构 PE 阵列维度；FLDD 让局部依赖 token 在当前迭代内细化，Merge–Split–Merge 数据流隐藏串行开销，流式词表引擎处理不规则 LM head 负载。论文在 LLaDA-8B 与 Dream 系 dLLM 上与专用加速器、Jetson AGX Orin 比较，报告速度、能效、质量与组件消融。

## 3. 结论

直接证据：论文报告相对所测 dLLM 加速器 2.05–2.78 倍速度、2.99–3.93 倍能效；相对 Jetson AGX Orin 为 2.55 倍速度、6.07 倍能效。这是论文设定的架构评估结果，不代表已在所有生产芯片上实现。

## 4. 未来影响

我的推断：若硬件实现保持质量和吞吐，这种按 token 状态动态分配计算的机制会提高 diffusion LLM 在 agent 推理中的实用性。

## 5. Critical thinking

关键假设是低效益 token 可可靠识别且局部依赖足以提速而不损害答案。与把所有 token 同步送入同一执行路径的加速器不同，DynaTE 让执行宽度和词表需求动态变化。建议在真实 FPGA/ASIC 原型及多批次、不同输出长度、长上下文任务上测延迟尾部、功耗和质量；单独给出调度器开销。

## 6. 可信度判断

**3/5**。全文有两个模型、架构消融和质量检查；硬件性能主要依赖所给评估条件，芯片实测与真实部署负载的外部效度尚不足。
