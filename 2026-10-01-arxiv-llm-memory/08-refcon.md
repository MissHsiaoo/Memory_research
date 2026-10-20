# 08 — RefCon: Iterative Refinement and Contrastive Memory Extraction for Context-Evolving Agent

- arXiv：[2609.39143](https://arxiv.org/abs/2609.39143)；[官方 PDF](https://arxiv.org/pdf/2609.39143)；[本地 PDF](./2609.39143.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Ubaidillah Ariq Prathama 等；Huawei Technologies
- 机构优先级：**S，头部企业研究团队**；研究标签：`agent memory` `experience extraction` `self-refinement`
- 证据：已核读 PDF 方法和实验；数值为作者报告。

## 1. 做了什么

解决 agent 执行上下文不断变化时，原始轨迹很难直接成为可迁移记忆的问题：通过反复修订与轨迹对比抽取经验。

## 2. 怎么做、实验如何设计

RefCon 顺序式自我修订一条经验，再并行对比多条不同轨迹，提炼稳定的可复用规则；无需人工经验标签。AppWorld、BFCL-V3 等评估结合 ACE、ReMe、ReasoningBank 等已有记忆系统；相对增益分别报告最高约 21.6%、16.6%、35.5%，还考察 SWE 类迁移及轨迹数的测试时扩展。

## 3. Conclusion

记忆质量不只取决于存储量；比较成功与失败轨迹、修订其共性可改善后续 agent 决策。

## 4. Future impact

适合做在线经验库的写入前处理，尤其是行动模式频繁变化、旧规则易失效的环境。

## 5. Critical thinking

**推断：** 自我对比可能只把同一模型偏见浓缩成更自信的“规则”。应评估不同任务时段的规则失效、错误轨迹比例、额外采样与推理成本，并对比人工标注少量高质量经验的基线。

## 6. 可信度判断

**4/5。** 多记忆框架和多基准验证是优点；增益多为相对值，轨迹生成成本与长期污染尚需明确。
