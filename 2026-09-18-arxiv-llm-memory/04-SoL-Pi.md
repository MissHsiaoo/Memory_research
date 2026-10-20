# 04. SoL-Pi: Recursively Scaling Auto-Research Loops for Efficient Agent Harness

- arXiv：[论文页面](https://arxiv.org/abs/2609.20519v1)｜[官方 PDF](https://arxiv.org/pdf/2609.20519v1)｜[本地 PDF](papers/04-SoL-Pi-2609.20519.pdf)
- 首次提交日期：2026-09-17；版本：v1。
- 正式公告批次：2026-09-18（北京时间本次报告日 2026-09-18；提交日不等于公告日）。已在官方 New submissions 栏核验。
- 作者：Haozhe Liu , Tian Ye , Sensen Gao , Qihang Cao , Yitong Li , Mingchen Zhuge , Duomin Wang , Ruihua Zhang , Ping Luo , Jiawang Bian , Lei Zhu , Ligeng Zhu , Enze Xie , Song Han
- 机构：NVIDIA；Nanyang Technological University；MIT（首页机构列表；不把未显示清晰上标的个别作者强行分配）。核验依据：下载的官方 PDF 首页机构/上标/脚注；不根据姓名、底座模型或被研究产品推断机构。
- 机构优先级：P1｜优先公司/高校合作，直接相关
- 研究标签：self-evolving agent；context compaction；经验验证与 harness 搜索
- 入选理由：NVIDIA/MIT/NTU 的大规模 harness 自动研究，将 context compaction 和 evidence-preserving reading 放到能力—成本取舍中。
- 方法新颖性判断：4/5（本次候选内主观判断，非全球排名）。
- 阅读范围：全文可访问；重点阅读方法、实验/定理、主要结果与局限。论文直接结果下文用“作者/实验/结果”表述，“我的推断/建议”不属于论文已经证明的结论；未独立复跑代码或完整复核全部证明。

## 1. 做了什么

SoL-Pi 把自改进焦点放在 agent harness，而非修改模型权重。自动研究循环在多种环境中提出与测试机制，最终保留 ActionFusion、OnlineContextCompact、ObservationPack、EvidencePreservingReducer 四种模块，分别针对动作执行、上下文压缩、观察整理和委托式阅读。与 memory 的直接关联是如何减少历史/工具输出负担，同时尽量保持任务能力和证据。

## 2. 怎么做，实验如何设计

作者搜索 152 个方向、535 个环境，其中 495 个 issue/PR 环境和 40 个合成环境；报告 3,000 多次运行、60,000 多次交互。各研究 lineage 使用能力和效率门槛，再在声称未用于反馈的 EdgeBench 上评估。公开主要评测是 51 个任务，另有 134 任务设置；Efficiency 固定采用四模块，Performance 表格则采用各 backend 最佳单机制，不能把它解释成同一冻结组合。费用用论文指定价格快照估算，token traffic 包括缓存读取，不等于独立新增信息量。

## 3. 结论

GPT-5.6 Sol 条件下 Pi 分数 44.833，Efficiency 为 42.003，约下降 6.3% 相对值；token traffic 从约 2.154B 降至 1.099B，减少 49%，费用 1,339 降至 894，减少约 33%。Performance 分数 47.208，但 traffic 约 2.022B，仅少约 6.1%。因此“提高性能且减半流量”不能拼接两种配置。未参与搜索的 Opus 5 在 Efficiency 条件也有成本下降，但分数并非完全保持。

## 4. 未来影响

我的推断：记忆压缩和自主研究优化值得用多目标前沿报告：任务能力、证据忠实度、token traffic、真实费用与延迟。这个工作提供可搜索的工程模块，但还不是递归改进长期无限复利的证明。对你的系统，可把摘要、状态卡和委托检索作为候选机制，先用独立评测门槛决定是否入库。

## 5. Critical thinking

需要质疑的是“comparable”是否掩盖重要能力退化，以及单机制 Performance 选择的泛化稳定性。大规模搜索成本不应从最终部署省钱中消失；缺少严格等预算的搜索宽度/深度对照，无法证明规模本身带来收益。公开任务也可能受社区开发经验影响，不能仅凭 held-out 声明排除所有间接偏差。建议固定配置后在全新任务上测试，加入关键约束遗忘、证据引用完整性及压缩后危险动作；并报告 amortization 需要多少真实任务才能偿还研究成本。

## 6. 可信度判断

可信度 3.5/5：全文流程、主结果及费用口径提供了可检查证据，且有未见 backend 的转移结果。优点是明确 harness 机制与效率路线；局限是任务规模有限、搜索与部署成本不统一、性能最佳配置依 backend 选择、能力保持不是严格不劣保证。机构高优先级与证据评分独立，不把 RSI 叙事当作已证明结论。

