# 04 — PivotOPD: Learning to Recover from Pivotal Mistakes in Multi-Turn Agents

- arXiv：[2609.40285](https://arxiv.org/abs/2609.40285)；[官方 PDF](https://arxiv.org/pdf/2609.40285)；[本地 PDF](./2609.40285.pdf)
- v1 提交：2026-09-30；正式公告：2026-10-01（北京时间）
- 作者/机构（PDF 首页核验）：Yinghui He 等；Princeton University、NVIDIA、University of Maryland
- 机构优先级：**S，NVIDIA 与一流高校**；研究标签：`agent learning` `error recovery` `on-policy distillation`
- 证据：已核读 PDF 方法、实验与结论；以下数值为作者报告。

## 1. 做了什么

把多轮 agent 失败分解为可恢复的关键错误，训练模型既少犯关键错，也会从错误后状态恢复。

## 2. 怎么做、实验如何设计

作者在 Qwen3 8B–235B 轨迹中发现超过一半失败 rollout 有早期 pivotal mistake。PivotOPD 在该步让 teacher 给出正确动作，并在接下来几步提供恢复动作；前者用 reverse KL，后者用 forward KL 蒸馏。对 13 个基线、ALFWorld、WebShop、Search-QA 及 SWE-Bench Verified 比较，1.7B/8B 学生平均表现最强；1.7B 在 ALFWorld 比最佳基线高 5.5%，Nemotron 学生在 SWE-Bench Verified resolve rate 高 3.2%。

## 3. Conclusion

多轮学习不能只纠正单步动作；错误后可到达状态中的恢复能力也是可训练目标。

## 4. Future impact

可与 agent memory 系统结合，把失败经验存成“避免—恢复”双分支，而非单一事后反思。

## 5. Critical thinking

**推断：** pivotal mistake 的标注与 teacher 的恢复动作若依赖未来轨迹，线上使用会有信息差。应测试 teacher 错误、不可逆动作、不同恢复窗口和总教师调用预算，并报告安全约束下的恢复是否仍有效。

## 6. 可信度判断

**4.5/5。** 多模型尺度、13 基线、跨任务及跨模型家族迁移构成较强证据。局限是错误识别与教师质量仍是依赖，真实不可逆环境尚未充分覆盖。
