# 13. Twists and Turns: A Graph-Based Benchmark and Framework for Long-Term Memory in Exploration Tasks

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06414)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06414)；[仓库内 PDF](pdf/2611.06414.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Dai, Chongyuan；Shen, Yaling；Song, Zirui；Liao, Junfeng；Hu, Jinpeng；Chen, Xiuying
- 机构：首页署名已核验：MBZUAI；Monash University；Hefei University of Technology。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：long-term memory; exploration graph。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–8；已获取完整29页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

面向长期探索中支持、推翻、修订和重启的关系记忆，提出图引导基准及图记忆方法。

## 2. 怎么做、实验如何设计

先生成类型图并演化，再用研究/软件任务实例化并扩展为对话；最终224对话、2,018问答，51K–174K tokens。LExGraph仅从原始对话建图，不读取生成真值图：按话题分段，保存摘要键和原始值，右边界父子边加跨分支关联，BM25/向量融合并扩展邻居。两reader，F1与LLM部分正确评分，并测BEAM子集。

## 3. 结论

表2：Qwen总体ACC 63.92对Vanilla 58.36；GPT-6 Luna 64.00对59.03。增益不是免费：相对Vanilla报告约1.2–1.3倍token和1.1倍检索+回答延迟。稀疏子集并非每项最好。

## 4. 未来影响

推断：适合测试科研/软件探索记忆的关系追踪与被推翻结论恢复，补充事实检索基准。

## 5. Critical thinking

图生成基准可能结构上偏爱图方法，需真实探索日志外部验证；生成/检查都大量依赖LLM且筛掉很多候选。单种子、温度零不等于无方差。建议固定相同索引/回答token预算、打乱边、独立标注关系及比较只保留原文的强检索基线。

## 6. 可信度判断

3/5。构造和无真值图访问边界清楚，有多个基线；合成同构偏好与有限reader/种子仍是主要限制。

## 官方提交记录

Submission history From: Chongyuan Dai [ view email ] [v1] Wed, 4 Nov 2026 12:13:52 UTC (1,186 KB)
