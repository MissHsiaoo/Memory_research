# 02 — Learning from Research: Toward Lifelong Agent Harness Evolution（ScholarEvolve）

- arXiv：[2609.40169](https://arxiv.org/abs/2609.40169)；[官方 PDF](https://arxiv.org/pdf/2609.40169)；[本地 PDF](./2609.40169.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Jingbo Yang 等；University of California, Santa Barbara、Microsoft
- 机构优先级：**S，Microsoft 与一流高校**；研究标签：`self-evolving agent` `harness memory` `continual learning`
- 证据：已核读 PDF 方法、实验与结论；以下数值为作者报告。

## 1. 做了什么

提出 ScholarEvolve，让 agent harness 的长期演化吸收新论文中的方法，而非只根据当前任务失败做反应式修改。

## 2. 怎么做、实验如何设计

系统按 harness 功能模块组织改进方向，用主题建模区分研究策略，生成模块修改并测试组合；新论文可持续进入候选池。AppWorld 和 Tau2-Bench 实验中，Qwen3.5-27B 在 AppWorld Challenge 的 task goal completion 从 49.6% 到 63.6%，GPT-5.4-mini 在 Tau2-Bench Telecom 的 pass@1 从 72.7% 到 81.9%。论文还检查了未参与演化的 AppWorld 应用迁移。

## 3. Conclusion

结构化读取研究成果能给固定基座模型的 harness 提供持续、主动的改进线索。

## 4. Future impact

若能稳定运行，论文阅读系统可变成 agent 自我进化的知识输入端，推动 memory、tool use 与验证流程的长期更新。

## 5. Critical thinking

**推断：** 论文方法与评测集之间可能有隐性知识泄漏，且“新论文带来提升”需要和普通搜索预算、人工整理知识库比较。应做严格时间切分、论文相关性盲审、等 token/等美元基线，并监测 harness 复杂度和安全回退。

## 6. 可信度判断

**4/5。** 两类 agent 环境、两个模型和 held-out 应用实验支撑方向。局限是长期演化仍是有限轮模拟，剩余失败集中在需求追踪和证据覆盖，真实持续部署待验证。
