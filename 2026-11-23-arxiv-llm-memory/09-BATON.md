# 09. Perceive Once, Escalate on Demand: Handing Off Visual KV Memory from Small to Large VLMs

- [arXiv 摘要](https://arxiv.org/abs/2611.26902) · [官方 PDF](https://arxiv.org/pdf/2611.26902) · [本地 PDF](pdfs/2611.26902.pdf)
- 官方公告批次：2026-11-23，New submissions；本次补读整理：北京时间 2026-11-24。
- 首次提交日期：2026-11-19（来自官方 submission history，非公告日期）。
- 作者：Zhou, Qiang; Deng, Jianing; Dong, Siyan; Chen, Jingxian; Lin, Han-Yi; Hu, Jingtong。
- 机构：首页署名核验，University of Pittsburgh、University of Hong Kong。机构层级：B：强研究型高校/实验室。
- 研究标签：visual latent memory；KV transfer；small-large cascade。
- 阅读依据：已下载并解析完整 10 页 PDF，目视核验首页；本评析重点核读 §3–6、表1、§7局限，不声称逐行审计所有附录或独立复现实验。
- 证据可信度：4/5，与机构层级独立。下述“论文证据”指作者报告，“研究判断/建议”指本次阅读推断。

## 1. 做了什么

论文证据：小VLM持续感知并保留KV，只在困难决策把记忆交给大VLM。核心发现是“重建大模型自己的KV”不一定比“让大模型用这份记忆答对”更有效。

## 2. 怎么做、实验如何设计

每层线性映射小模型相邻相对深度层的KV，处理RoPE对齐；仅历史映射，大模型自己编码当前帧和问题。BATON用大模型原生回答做KL蒸馏，辅以0.1权重KV误差；训练1500个无标注决策两轮，模型冻结。RoboMME上主体Qwen3-VL 2B→8B；注意两模型本身先经任务LoRA，而“无标签”只指映射训练。另测多模型对、OpenEQA和级联预算，使用episode-cluster bootstrap。

## 3. 结论

论文证据：choice由小模型84.0升到86.9，大模型重看88.8；收益+2.9点区间[1.6,4.3]。point +1.9点区间[-0.2,4.1]，不能称显著提高。拟合KV的translation约83.4，虽读出误差更低却无收益。级联同路由预算下报告28–47%计算节省；64帧单次升级8倍计算差不等于端到端8倍实测加速。

## 4. 未来影响

研究判断：跨模型记忆对齐应优化下游用途而非表示距离；与多目标记忆相关的问题是同一记忆能否被多个不同能力读者有效使用。

## 5. Critical thinking

映射按模型对、同家族训练，不能直接声称任意跨架构互通。定位比语义选择弱；历史仅到64帧，计算量为解析TFLOP而非全硬件延迟。建议把同一写者映射到不同读者和多任务，测试未见目标、长视频、时间位置漂移，以及每模型对重新训练的成本。

## 6. 可信度判断

4/5。训练目标控制、部署路径消融、区间和多模型验证有力；几何定位收益不稳定，基础模型已任务适配，跨模型家族通用性尚未建立。

