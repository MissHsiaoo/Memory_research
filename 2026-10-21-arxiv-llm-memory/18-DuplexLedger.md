# 18. DuplexLedger: Benchmarking Transactional Memory in Full-Duplex Speech Agents

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2610.27581)；[官方 PDF](https://arxiv.org/pdf/2610.27581)；[仓库 PDF](pdfs/2610.27581.pdf)
- 首次提交：20 Oct 2026；官方 New submissions 公告标签：2026-10-21；北京时间报告归属：2026-10-21。
- 作者：Yuxuan Li , Xiangchen Guan , Kunrong Li , Jin Wang , Kaiwen Luo , Yang Xiao , Yufei Guo , Zhisheng Chen , Liang Lin , Kun Wang
- 机构（PDF 首页署名核验）：Nanyang Technological University；Peking University；Beijing University of Technology；Xidian University；University of Melbourne；China Aerospace Science and Industry Corporation
- 机构优先级：P1B；主题相关性：直接相关；研究标签：speech agent memory；transactional update；benchmark
- 阅读证据：正文§3、§5–6（PDF第4、6–7页）及附录I；首页。已获取完整 PDF（38页），重点阅读所列方法、实验与局限；未逐条核验全部附录推导、未运行代码复现。以下数字均为作者报告值。

## 1. 做了什么

将全双工语音记忆定义成事务：决定谁对谁说、话是否完整、是否允许写入或覆盖，而非只看问答回忆。

## 2. 怎么做、实验如何设计

【论文直接证据】1094中英会话、6564问题/检查，标WRITE/UPDATE/IGNORE/RETAIN及前后状态。5系统评测；ACT-Mem冻结MiniCPM-o4.5，用8.92M参数controller+retriever处理准入、版本与typed evidence card；219独立留出会话，40会话校准，session bootstrap20000次。

## 3. 结论

【论文直接证据】最新值准确率4.11%→8.68%，增加4.57点，95%CI[1.60,7.53]；最终状态覆盖1.27%→2.00%，CI[-0.49,1.99]跨零，不能称统计明确改善。绝对性能仍低。

## 4. 未来影响

【阅读者推断，尚待验证】提供多目标记忆操作指标：正确更新、拒绝旁人干扰、保持当前值与实时响应需要共同优化。

## 5. Critical thinking

【阅读者评析与后续建议】相对111.2%增益易掩盖8.68%的低绝对分。规则slot解析依赖领域模式，否定排除语句可能被误存；基于词汇的双语评分也需人工审计。建议在相同实际中断暴露率下比较，报告写入误报、更新正确率、延迟及最终任务收益的Pareto关系。

## 6. 可信度判断

**4/5**（与机构优先级独立）。有事务标签、独立划分和配对置信区间，反面结果披露充分；不能从小幅受控改善推出自然语音记忆已解决。

本评分评估论文当前证据对其有限结论的支持，不是保证结果可复现、已同行评审或可安全部署。
