# 10｜APDMem：按查询复杂度逐层展开长期记忆

- 论文：[arXiv:2610.02472](https://arxiv.org/abs/2610.02472)｜[官方 PDF](https://arxiv.org/pdf/2610.02472)｜本地：`2610.02472.pdf`
- arXiv 正式公告：2026-10-05；首次提交：2026-10-01。
- 作者/机构：首页核验 Chin-Lun Fu 等；JPMorgan Chase & Co. Machine Learning Center of Excellence。
- 机构优先级：S；标签：personalized memory、层级检索、长对话。关联性：直接。

## 1. 做了什么

APDMem 让 Agent 自行决定是否从主题摘要下钻至个性化事实、逐轮证据和原始消息，以在答题精度与检索成本间动态权衡。

## 2. 怎么做、实验如何设计

四层记忆由 progressive-disclosure controller 访问，notes synthesizer 整理事实、事件顺序及矛盾后交给答案模型。PDF 在 LongMemEval-S 的 500 题、六种题型上与 Full-context、Mem0、LightMem、SimpleMem 比较；统一答案提示及 GPT-4.1-mini judge，GPT-4.1/mini backbone 下平均为 87.8%/79.8%，比最佳既有基线高 3.8/2.9 个百分点，只访问约 8% 会话。

## 3. 结论

多粒度按需检索在该基准可减少读取量并提高准确率；“访问 8% 会话”不等于系统总计算成本仅 8%。

## 4. 未来影响（推断）

适合做个人助理的记忆访问策略：简单问题快速停在摘要层，争议/时间问题自动回溯原始证据。

## 5. Critical thinking

PDF 的局限明确指出顶层摘要遗漏会使深层证据失去召回机会，惰性构建下层也有冷启动延迟。需评估摘要事实漏失、用户撤回/更正后的索引一致性、p95 延迟及全流程 token；比较不同 controller 是否频繁过度下钻。

## 6. 可信度：4/5

依据：已读 PDF 具体基准、基线、平均值与局限。优点是成本—精度双维度和矛盾处理；局限是主要一项基准且自动 judge 与同源基线数字可能影响结论，需独立复核。
