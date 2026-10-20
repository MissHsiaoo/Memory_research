# 13 RSI-Anything：带预测世界模型的递归改进

- 论文：[arXiv:2610.13912](https://arxiv.org/abs/2610.13912) · [官方 PDF](https://arxiv.org/pdf/2610.13912) · [本地 PDF](2610.13912.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Taoyong Cui、Pinxian Zeng、Wanghan Xu、Hao Xiao、Shuhan Xue 等。机构：PDF 附录 A 核验 PhAI Labs、The Chinese University of Hong Kong、University of Macau、Shanghai Jiao Tong University、Fudan University、University of Oxford、Stanford University、Peking University 等；首页明确把机构指向附录 A。
- 机构优先级：B（一流高校/实验室）；研究标签：recursive self-improvement、world-model memory、self-evolving agent。

1. **做了什么｜论文证据：**提出 RSI-Anything，用预测世界模型挑选值得付费验证的行动与学习数据，再依真实反馈更新策略/流程及世界模型。
2. **怎么做、实验如何设计｜论文证据：**世界模型预测收益与信息价值，观测反馈驱动更新，兼容性/组件检查决定是否保留新策略—模型组合；在代码修复、GUI、实验室规划、反应优化和免疫科学案例中测试。
3. **结论｜论文证据：**代码修复设置中固定 coder 的成功率由静态验证器 26.3% 到预测选择 29.2%、模型适应后 31.2%；GUI 平均操作数下降 39.4%，实验室规划五轮策略更新由 21.80% 到 46.01%。不同任务指标不可直接合并。
4. **未来影响｜我的推断：**可把长期代理经验压缩进可更新的环境预测器，而非只存文本反思。
5. **Critical thinking｜我的推断：**预测器会随策略变更而失准，选择验证样本本身也造成选择偏差；兼容性检查可能拦不住慢性性能退化。建议每轮冻结独立测试集、报告校准误差和保留/回滚率，并在无法实验的高风险域限制在线更新。
6. **可信度：3/5。**依据：核查了跨域实验、保留机制与附录机构；优点是多领域验证，局限是任务差异大、复杂系统的因果归因和生物案例外部确认仍弱。
