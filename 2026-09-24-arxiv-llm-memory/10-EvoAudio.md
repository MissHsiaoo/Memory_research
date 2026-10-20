# 10. EvoAudio

- 论文：**EvoAudio: Recursive Self-Improvement for Audio Understanding**
- arXiv：[2609.27389](https://arxiv.org/abs/2609.27389)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Yuxiang Wang 等；香港中文大学（深圳）、清华大学、Tencent Hunyuan、Amphion Technology
- 机构优先级：**S｜顶级高校 + 头部工业实验室**
- 研究标签：self-evolving system、recursive improvement、verifiable curriculum、弱相关多模态
- 本地 PDF：[2609.27389.pdf](./2609.27389.pdf)

## 1. 做了什么

提出递归自改进音频系统：每一代模型根据自身薄弱技能生成下一轮可验证课程，同时演化波形、问题、难度和模型，而非一次性生成静态合成数据。

## 2. 怎么做、实验如何设计

系统包含 24 个工具、47 类可验证问题、6 个技能族；由当前 solver 决定技能/难度，程序化构造答案，合成后重新测量 pitch、rate、loudness、onset、tempo 等声学证据，过滤信号不足样本。每题采样 4 个 solver rollout，仅保留有混合成败、能提供 GRPO 方差的项目；每轮训练 64 步，在两个候选 checkpoint 中用 held-out set 决定是否晋级。共运行 13 轮、覆盖五种音频 encoder/语言 backbone，在 MMSU、MMAU-Pro、MMAR 上每个 backbone 的平均分均最高，最大提升 6.3 点。

## 3. Conclusion

“由当前能力塑造下一代课程 + 可执行声学 verifier + 晋级门控”能形成真实递归闭环；最弱声学技能获得最大收益。

## 4. Future impact

这是 self-evolving agent memory 的跨模态模板：把失败经验转为下一代课程，但只有经过领域 verifier 的经验才能写入。可迁移到 GUI、机器人、代码和工具代理。

## 5. Critical thinking

亮点是课程不是静态数据池，而是随 solver 演化，并用物理可测信号防止模型自标注闭环。限制在于 24 个工具定义了可探索技能空间，系统可能只在工具可表达的分布内自我提高；13 轮和三套 benchmark 尚不足以证明长期不饱和。算力为 4×8 H800 节点，复现成本高。建议测试工具扩展、长期退化、跨代灾难性遗忘和 adversarial verifier。

## 6. 可信度判断

**4/5。** 已阅读全文；多 backbone、静态课程/无验证等消融和逐轮曲线支持机制。领域限定与高算力成本限制普适性，因此作为“弱相关但高启发性”收录。
