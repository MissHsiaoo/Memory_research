# 03. CoEvoBench: Can LLMs Drive Recursive Co-Evolution of Agentic Systems?

- [arXiv 摘要](https://arxiv.org/abs/2611.27116) · [官方 PDF](https://arxiv.org/pdf/2611.27116) · [本地 PDF](pdfs/2611.27116.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Xiao, Chuan; Wang, Baojie; Fan, Haizhao; Du, Hongzhe; Xu, Xander。
- 机构：首页署名核验，Zhejiang University、Alibaba Group、Shanghai Jiao Tong University。机构层级：A：优先产业研究机构合作。
- 研究标签：self-evolving agents；模型-harness共同优化；benchmark。
- 阅读依据：已下载并解析完整 28 页 PDF，目视核验首页；本评析重点核读 §3–5、表1、结论与审计协议描述，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：让LLM研究者同时修改目标agent的模型与harness，评估它能否利用上一轮结果继续改进。关注的是如何分配训练与代码改动，而不是仅做一次提示优化。

## 2. 怎么做、实验如何设计

五类任务包括SWE-bench Verified、TB-Lite、AppWorld、τ²-bench Telecom和BFCL-V4。目标基座为Qwen3.5-9B-Base或MiniCPM5-2B-Base；每个研究配置有24小时与四张H20，每组合三次独立开发运行。区分可见、选择、测试集；选择集不提供题目和轨迹。最终独立评测模型-harness对，另评基础模型搭配最终harness；BFCL分数由多轮与memory指标按60/40加权。对确认的数据作弊运行有审计后降级评分。

## 3. 结论

论文证据：强研究者能弥合超过四分之五的初始系统到指令调优参考系统的差距，但交互任务和长程代码任务差异明显。Qwen目标上GPT-6 Astra加权分31.23，参考37.42；大量收益出现在第一个候选，后续反馈循环收益递减。论文没有证明递归改进可无限持续。

## 4. 未来影响

研究判断：可用于测试“经验记忆是否改变下一轮研究决策”。把记忆检索或反思模块放入研究者，在固定总预算下衡量后续轮次的新增收益，比单独比较最终一次成功率更有意义。

## 5. Critical thinking

研究者模型与CLI绑定，因此配置差异不能全归因于基础模型。不同领域通过参考差距归一化，需同时检查原始分数；接近参考不等于超过人类研发。建议固定CLI、给不同记忆方法相同工具与token预算，比较失败复发、无效训练次数、验证集过拟合和后半程增益；检查审计漏检及公开基准污染。

## 6. 可信度判断

4/5。分离开发/测试、三次运行和审计记录增强可信度；但基准公开性、研究者运行环境差异及24小时预算限定结论。作为综合自演进测评较强，作为单一记忆机制因果证据仍需新增消融。

