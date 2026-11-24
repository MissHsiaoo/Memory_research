# 04. Contexture: Runtime Context Eviction for High-Throughput Agent Serving

- [arXiv 摘要](https://arxiv.org/abs/2611.26980) · [官方 PDF](https://arxiv.org/pdf/2611.26980) · [本地 PDF](pdfs/2611.26980.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-20（来自官方 submission history，非公告日期）。
- 作者：Hong, Colin; Shan, Bryan; Pang, Wei Siong; Lu, Chengzhi; Guo, Xu; Shivaraman, Nitin; Luo, Tao; Choukse, Esha; Lin, Kisson; Ustiugov, Dmitrii。
- 机构：首页署名核验，Nanyang Technological University、IAIC/A*STAR、Microsoft、SuperMem Pte. Ltd.（首页未标明Microsoft Research）。机构层级：A：优先产业研究机构合作。
- 研究标签：working memory；context eviction；KV serving。
- 阅读依据：已下载并解析完整 14 页 PDF，目视核验首页；本评析重点核读 §4–6、系统实现和负载/准确率评估，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：在服务运行时裁剪agent执行上下文，联合利用工具操作的覆盖关系与全局KV压力。保留harness完整历史，仅缩短模型实际执行的prompt，避免把逻辑删减与缓存驻留管理混为一谈。

## 2. 怎么做、实验如何设计

新文件读取或成功测试可使旧输出成为候选；全轮输出已被覆盖时才考虑相应推理/调用。用宽限窗口、缓存前缀驻留和re-prefill上限决定何时真正删除。原型基于vLLM 0.26；两模型、两harness（Hermes/OpenClaw）、两基准（TB2.1/SWE-Atlas）构成八配置，H100/H200测服务吞吐。使用轨迹回放控制负载，并在负载中加入真实agent探针测准确率。

## 3. 结论

论文证据：相对所测非observation-masking最佳基线，SLO内吞吐提高20–73%；对masking仅八配置中的五个提高7–63%。真实探针平均准确率提高1.4个百分点，最差下降3.7点。SLO定义为p90相对无负载慢10倍，不是固定低延迟保证；吞吐回放固定输出，不能独立说明真实工作质量。

## 4. 未来影响

研究判断：记忆删减策略应针对系统负载动态执行，评估“保留什么”和“何时删”两个问题。适合把memory研究从单会话token节省扩展到多用户吞吐与能耗。

## 5. Critical thinking

“新输出覆盖旧输出”是启发式：差分诊断、审计追溯可能仍需旧错误。原型规则仅覆盖文件/沙箱工具，外部MCP服务不在范围。建议构造必须对比旧新状态的任务，测高压力下的最差质量损失；同时测试更严格SLO、故障回退、不同模型与外部工具。

## 6. 可信度判断

4/5。有清晰运行时机制、回放与真实探针分工、消融及能耗数据。准确率有退化、语义规则覆盖有限，不能宣称无损压缩或通用安全删除。

