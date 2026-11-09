# 15. MORTIS: Compiler-Guided KV-Cache Management for LLM Agent Programs

- arXiv：[摘要及版本](https://arxiv.org/abs/2611.08638)
- PDF：[官方原文](https://arxiv.org/pdf/2611.08638) · [仓库内原文](pdf/2611.08638.pdf)
- 公告批次：2026-11-09，官方 New submissions；北京时间日报日期：2026-11-09。
- 首次提交日期：2026/11/05；与公告日期分别记录，完整官方版本记录见文末。
- 作者：Ma, Xiaoyu；Dantanarayana, Jayanaka L.；Kashmira, Savini；Li, Baichuan；Tang, Lingjia；Mars, Jason。
- 机构：首页已渲染并核验：上海交通大学；University of Michigan, Ann Arbor。
- 机构优先级：A2：优先研究型高校/实验室合作。
- 研究标签：KV-cache；编译器；经验生命周期。
- 相关性：弱相关但具启发性：计算缓存生命周期可迁移至上下文管理。
- 阅读范围：完整13页PDF已取得；重点阅读PDF物理页 1、4–10。未逐行审查所有附录、未复现实验。
- 证据边界：第3节是论文报告结果；第4节和第5节研究建议为评阅推断。

## 1. 做了什么

用typed LLM调用程序的变量共享与生命周期分析，细分提示内部组件，重排稳定前缀并指导KV保留、淘汰和预取。属于计算缓存，不直接解决语义个人记忆。

## 2. 怎么做、实验如何设计

基于Jac编译器与SGLang v0.5.10.post1；A40、Qwen3-32B-AWQ，15GB GPU及25GB CPU KV池，四agent工作负载和混合负载。对照SGLang、KVFlow、CacheScout、Continuum、Static-Adapter，另把相同重排布局提供给基线以拆开调度贡献；还有4×A40及3090敏感性实验。

## 3. 结论

四工作负载JCT与吞吐几何均值提升1.45、1.49倍；重排单独为1.30、1.36，调度单独仅1.03、1.02。预取最多贡献2.6%，收益主要来自重排加保留。质量表coding54.8对原55.3，其余改善，不能说数学上严格质量不变。

## 4. 未来影响

评阅推断：弱相关但具启发性。把记忆条目分为稳定、增长、短暂和失效等生命周期，可迁移到代理上下文管理；但这里收益来自前缀计算复用。

## 5. Critical thinking

依赖类型化调用和可分析变量，开放式自由文本agent未必满足。重排会改变语言语义注意，质量小样本没有严格等价证明。建议跨模型/多轮自适应图、不同工具等待分布测试，并报告编译分析开销和质量置信区间。

## 6. 可信度判断

4/5。依据：系统实现、同布局对照、消融与硬件敏感性实验。局限：工作负载数量及结构化编程假设，不能把KV命中率当语义记忆准确率。

## 官方提交与版本记录

Submission history From: Xiaoyu Ma [ view email ] [v1] Thu, 5 Nov 2026 19:35:20 UTC (576 KB)
