# 04 — My FAULT: Self-Diagnosis as Credit Assignment in Self-Evolving Agentic RL

- arXiv：[2610.01161](https://arxiv.org/abs/2610.01161)；[官方 PDF](https://arxiv.org/pdf/2610.01161)；[本地 PDF](./2610.01161.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Yihua Zhu 等；Alibaba Group、Kyoto University、NII LLMC，以及北大、UCLA、清华等合作单位
- 机构优先级：**S，Alibaba 与一流高校**；研究标签：`self-evolving agent` `failure memory` `credit assignment`
- 证据范围：核读 PDF 方法和实验；数字为作者报告。

## 1. 做了什么

把 agent 的自然语言自诊断转为可校验、可量化的逐步奖励归因，处理整条轨迹同成败时训练信号缺失的问题。

## 2. 怎么做、实验如何设计

FAULT 核查诊断所指向的错误证据，依据终局结果学习相对错误成本，再向相关步骤重分配信用；策略与诊断器一起更新。PDF 在 ALFWorld、WebShop、Search-based QA、两种模型规模上比较 GRPO/GiGPO 等，ALFWorld 的可用训练信号覆盖报告为 95%，对照 GRPO 41%、GiGPO 72%，并检验错误定位与任务成功。

## 3. Conclusion

可验证的失败诊断能成为代理自演化的训练信号，但不应直接相信未经校验的反思文本。

## 4. Future impact

可把行动失败记录从“文字复盘”提升为有强度、有证据的记忆，用于策略训练与纠错优先级。

## 5. Critical thinking

**推断：** 自诊断器与策略共同训练可能形成相互迎合的错误归因；信号覆盖率也不等于最终收益。应分别报告真实因果错误定位、诊断成本、等训练预算对照，以及工具反馈错误时的鲁棒性。

## 6. 可信度判断

**4/5。** 信号覆盖、任务成绩与多尺度对照支持方向；诊断正确性和跨环境迁移需独立审查。
