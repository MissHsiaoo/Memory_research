# 10｜ScienceBuddy: Recursive-in-Recursive Self-Improvement for Interactive Scientific Agents

- 来源：[arXiv v1](https://arxiv.org/abs/2609.17523v1) · [官方PDF](https://arxiv.org/pdf/2609.17523v1) · [本地PDF](../papers/2609.17523.pdf)
- 首次提交：2026-09-15；入选公告批次：2026-09-16（以官方New submissions快照核验，非按提交日猜测）。
- 作者：Shuhan Xue , Jianyuan Zhong , Ziyuan Nan , Wenbin Li , Zhaochen Yu , Jinchao Ding , Qiang Gao , Pengyu Zhan , Yuntong Zhang , Tian Cheng , Zhenfei Yin , Yingcheng Wu , Ling Yang
- 核验机构：PhAI Labs；Fudan University；University of Oxford；Stanford University；Princeton University。依据论文PDF作者署名；联合署名不代表所有机构共同主导。
- 机构优先级：A1｜一流高校合作；PhAI Labs主体
- 研究标签：直接相关｜self-evolving agent、procedural memory、harness与模型协同
- 编辑评分：novelty 4/5；证据可信度 3.5/5。均为本次阅读判断，不是同行评审结论。

## 1. 做了什么

提出双层交替改进：内层固定任务模型，修改指令与技能组成的harness；外层固定选出的harness，用RL改进任务模型，再进入下一轮。保留的技能相当于程序性记忆。它的价值在于区分“工具/流程变好”和“模型权重变好”，而非宣称无限递归自我提升。

## 2. 怎么做，实验如何设计

系统提供224个工具、22个模块。任务库895项，含LitQA2、DbQA、ProtocolQA和GWAS，共16子主题。耦合实验使用Qwen3.5-4B，正文实际运行3个周期，每周期10次harness搜索和20次RL更新，harness选择使用固定验证集；最终同一测试集单次准确率42.2%→73.3%。独立harness实验用24批、每批12次对话，共288次适应对话；固定GPT-6 Astra提出编辑，Qwen3.8-27B辅助模拟/反馈，只改指令与scoped skill文本，执行循环和预算固定。另在未用于选择的验证集比较31.1%→51.1%。固定harness的模型学习实验pass@4从48.3%→67.8%，不能与单次准确率混用。

## 3. 结论

直接证据：三个受限周期中，程序文本修订与RL分别能改善特定科学任务；真人交互案例是定性展示，不是已计分的任务包。reflector保持固定，因此任务模型变好不意味着“改进器本身越来越聪明”。论文小节标题写Two-Cycle而正文/图8为3周期，报告采用实际实验说明。

## 4. Future impact：未来影响

我的推断：memory系统可维护版本化的技能文本，并让任务模型在稳定技能环境下吸收常见经验。真正有研究价值的是两类记忆的分工：哪些应保持可编辑外部技能，哪些值得编入参数；何时切换学习层级，如何发现旧技能已不适用于新模型。

## 5. Critical thinking：批判性分析

895是任务库存，不等于每项实验都有895个独立测试样本。单次训练曲线和少量周期还不能支撑持续扩展规律，需多种子、逐周期测试、总计算预算匹配。反馈模拟器能看到正确/错误与提交状态，因此这不是没有外部监督的自我发现。强外部编辑模型也是重要资源，应该与固定模板、只改harness、只RL、交替但不继承经验进行总成本对照。

建议记录每个技能的来源轨迹、版本和回滚原因；在完全新科学领域检验迁移，加入错误技能污染及用户偏好改变。真实科学发现、湿实验验证不在当前证据范围。

## 6. 可信度、优点与局限

3.5/5。优点：明确冻结边界、独立验证、拆分harness与权重学习，系统实现值得参考。局限：规模/种子和泛化证据有限，强编辑器与模拟反馈成本需单列，尚不是自增强改进器。机构依据PDF末页作者署名核验，PhAI Labs不误写成ByteDance Seed；已读方法、四案例与附录设置，未运行系统。

## 证据与阅读范围

本笔记基于原文方法、实验及相关局限/附录的人工阅读；PDF与抽取文本保存在本日报sources中。未执行作者代码，未独立复现实验。未加“我的推断”的数值均指作者报告或明确说明的表内重算；未来影响及后续实验为本次研究建议。排序、机构层级与置信度相互独立。

