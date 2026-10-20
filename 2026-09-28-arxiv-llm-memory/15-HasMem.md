# 15. HasMem

- arXiv：[2609.30797](https://arxiv.org/abs/2609.30797)
- 提交日期：2026-09-25；正式公告批次：2026-09-28（cs.AI new）
- 作者/机构（PDF 首页核验）：Zihong He 等；HKUST(GZ)、University of Bristol、HKUST
- 机构优先级：**A｜一流高校联合**
- 研究标签：continuous memory、adaptive compression、long-term LLM agent
- 本地 PDF：[2609.30797.pdf](./2609.30797.pdf)

## 1. 做了什么

提出 Hard-Origin Adaptively Softened Memory：记忆从冻结 LLM 的真实 token embedding 开始，随后 controller 对每条记录选择 KEEP/SHRINK/EXPAND，writer 重编码宽度变化，reader 与跨轮 global state 适配读取。

## 2. 怎么做、实验如何设计

主干为冻结 Qwen2.5-7B，训练约六小时；MSC-derived 由 268 个用户、646 个事件、535 个问题组成，LongMemEval-S 使用全部 500 问。主配置以 hard reference 93.6% 的 framed positions 获得 95.3 F1（+4.4），但 EM 84.3 对 88.1。LongMemEval-S F1 从 3.4 到 8.9，NLL 从 12.257 降到 5.274，EM 反而从 1.8 降到 0.6。匹配预算下，六种配置相对规则重编码提升 8.0–23.6 EM 点。

## 3. Conclusion

从可验证的 hard origin 渐进软化，比一开始生成不可审计的 soft memory 更稳；动态宽度和适配读出存在收益，但 F1、EM、简洁性之间没有一致改善。

## 4. Future impact

它可能成为 latent memory 的版本化路线：先保存忠实 token state，再按访问和预算逐步软化；必要时保留回退到 hard record 的能力。

## 5. Critical thinking

论文把负结果写得很清楚：F1 提升伴随更少 abstention、更长答案和更低 EM，LongMemEval 的本地 judge 也未完全验证。MSC 每用户最多 7 条记录，远未到长期累积。EXPAND 几乎未被主轨迹采用。建议做数千轮历史、真实删除/更新、跨用户迁移、等显存/延迟比较，并用官方 LongMemEval evaluator 复核。

## 6. 可信度判断

**3.5/5。** 已阅读全文。指标、配对检验和多配置披露充分；结果混合且对 protocol 敏感，主张应限于“自适应软化可行”，不宜解读为全面优于 hard memory。
