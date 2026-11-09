# 04. Flex-RSI: Benchmarking Recursive Self-Improvement of Frontier Agents

- arXiv：[摘要及版本](https://arxiv.org/abs/2611.08946)
- PDF：[官方原文](https://arxiv.org/pdf/2611.08946) · [仓库内原文](pdf/2611.08946.pdf)
- 公告批次：2026-11-09，官方 New submissions；北京时间日报日期：2026-11-09。
- 首次提交日期：2026/11/06；与公告日期分别记录，完整官方版本记录见文末。
- 作者：Zhang, Jingdong；Wang, Jionghao；Yu, Zhengming；Cai, Yancheng；Chow, Wei；Choy, Chris；Dou, Zhiyang；Hua, Hang；Li, Jiachen；Liu, Zhixuan；Wang, Chen；Wei, Songlin；Yang, Siyuan；Yuan, Yu；Zhan, Xiaohang；Zhang, Yucheng；Zheng, Shuhong；Li, Xin；Liu, Lingjie；Matusik, Wojciech；Tu, Zhengzhong；Wang, Wenping。
- 机构：首页已渲染并核验：Texas A&M；Cambridge；NUS；NVIDIA；MIT；MIT-IBM Watson AI Lab；UT Austin；CMU；UPenn；USC；Purdue；Adobe；Toronto（首页团队署名）。
- 机构优先级：A1：用户优先产业机构合作。
- 研究标签：self-evolving agent；递归harness优化；benchmark。
- 相关性：直接相关（含持续学习、扩散语言模型及个性化方向）。
- 阅读范围：完整68页PDF已取得；重点阅读PDF物理页 1、3–8、10–12、14–15。未逐行审查所有附录、未复现实验。
- 证据边界：第3节是论文报告结果；第4节和第5节研究建议为评阅推断。

## 1. 做了什么

构建固定预算下递归自改进agent基准：executor改任务解，improver利用轨迹和实验记录修改executor及自身。模型权重保持固定，考察外部流程的自演化。

## 2. 怎么做、实验如何设计

24任务覆盖六方向；主要比较至少六模型参加的20任务，另4任务参与模型较少。18模型从同一初始harness出发，任务内限制时间、GPU/模型调用和验证预算；隐藏验证集决定是否接受候选，最终隐藏测试集评价。验证接受阈值初始为starter分数标准差两倍，improver可调整。每模型任务通常一次运行，重复时报告最新一次。

## 3. 结论

177次运行中150次验证分提升，比例85%，提升中位数10.4；这描述验证改进，不能等同于测试提升或记忆组件因果贡献。排名基于每任务击败其他模型比例，且不同模型覆盖任务不同。报告显示闭源与开放权重模型在严格物理/正确性约束任务上的差距明显。

## 4. 未来影响

评阅推断：可用来测试记忆是否改善下一轮实验设计，而不是只增加上下文。executor与improver双层设计提供研究元记忆更新的接口。

## 5. Critical thinking

一次运行及不完整任务覆盖使总榜受任务组成和随机性影响；验证反复反馈可能被适配，接受阈值可改也须审计。建议等预算对照冻结harness、仅追加经验、仅改improver，重复多种种子，按隐藏测试增益和每百万token增益报告，而非仅看验证最好分。

## 6. 可信度判断

3/5。依据：读到数据隔离、协议、任务表和成本/轨迹分析，范围广。局限：单次运行、参与任务不均衡，本文笔记未逐项审计所有任务评测器及全部消融附录，机构强不提高证据分。

## 官方提交与版本记录

Submission history From: Jingdong Zhang [ view email ] [v1] Fri, 6 Nov 2026 03:51:20 UTC (13,907 KB)
