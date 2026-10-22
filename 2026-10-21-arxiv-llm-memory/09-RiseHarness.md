# 09. Harness Self-Evolution for Long-Horizon Terminal Agents

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27435)；[官方 PDF](https://arxiv.org/pdf/2610.27435)；[仓库 PDF](pdfs/2610.27435.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Ruhan Wang , Yucheng Shi , Zongxia Li , Junyao Yang , Zhongzhi Li , Yue Yu , Haitao Mi , Dongruo Zhou , Leoweiliang
- 机构（PDF 首页署名核验）：Tencent HY LLM Frontier；Indiana University；University of Maryland College Park；University of Georgia；National University of Singapore
- 机构优先级：P1A；主题相关性：弱相关但具启发性；研究标签：self-evolving harness；execution memory；reliability
- 阅读证据：正文§3–4（PDF第4–10页）、附录E；首页。已获取完整 PDF（38页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

利用同任务成功/失败配对和harness内部轨迹，定位可以通过执行框架修复的重复性问题。

## 2. 怎么做、实验如何设计

【论文直接证据】固定模型权重，保存agent轨迹、运行时边界信息与Harness Handbook；从flipping任务抽取问题，研究外部实现，修改harness并重复验证。100题Terminal-Bench Hard演化，89题TB2.1迁移；GPT-6-sol和DeepSeek-V4-Flash，通常每题4次。

## 3. 结论

【论文直接证据】DeepSeek在TBH Pass@1由56.75升至64.00，4次全成功比例37→51。TB2.1表中79.49使用最佳观察的三修改版本；最终四修改版本为75.28，对种子72.19提高3.09个百分点。不能将最佳版本当作预先固定的最终迁移性能。

## 4. 未来影响

【阅读者推断，尚待验证】经验库除了记录模型说了什么，还应记录工具实际执行了什么，帮助分离记忆/推理错误与运行层错误。

## 5. Critical thinking

【阅读者评析与后续建议】只分析flipping会忽略一直失败的任务。Flip下降也可能是全失败变多，必须同时报告全成功与全失败。开发集反复选版本可能拟合噪声；建议预注册选择规则、留出最终版本、逐任务回归与更长重复运行。

## 6. 可信度判断

**4/5**（与机构优先级独立）。有双轨迹及消融、多次评价、明确披露版本差异；最佳观察迁移结果和开发集选择降低外推把握。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
