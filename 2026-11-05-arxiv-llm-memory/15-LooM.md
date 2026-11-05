# 15. LooM: Loop-Invariant Memory for Causal Encoder-Decoder Language Models

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06835)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06835)；[仓库内 PDF](pdf/2611.06835.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Yang, Lele；Diao, Muxi；Yan, Zhonghao；Chen, Jiankang；Wen, Bin；Gao, Tingting；Zhang, Wentao；Liang, Kongming；Ma, Zhanyu；Xu, Weiran
- 机构：首页署名已核验：BUPT；Zhongguancun Academy；Peking University；Kling Team。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：latent memory; looped transformer。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–6；已获取完整16页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

在因果encoder-decoder中把记忆写入与循环读取分离，使增加推理深度不增加KV条目数。

## 2. 怎么做、实验如何设计

全局bank在循环前写完；decoder reader层可重复0–4次，local KV仅首次访问发布。随机深度训练支持每token 3–21次decoder调用，验证集锁定每预算一条静态路径。所有模型204M、5B训练token、同参数数据，但循环训练消耗2.9–4.7倍GPU时；测试CE、六项零样本及长上下文。

## 3. 结论

表2：所有路径128-token提示后cache均364.1 KiB；21调用CE 3.0307对6调用single-pass 3.0506，平均零样本提高0.79个百分点。低于11调用时主方法落后single-pass；固定21层循环训练本身未带来同样增益。

## 4. 未来影响

推断：为可调计算预算的latent memory架构提供一个写一次、读多次的可实现原则。

## 5. Critical thinking

cache大小不变不等于内容相同或计算免费；分布对深预算重采样，低预算差可能来自训练分配。204M规模与近随机任务成绩不能直接推到大模型。建议匹配训练FLOPs、扩展规模、测试检索而非仅PPL，并统计多种子及生产批量延迟。

## 6. 可信度判断

3/5。结构和缓存计数清楚、对照丰富；小模型、单训练种子和不匹配计算量限制性能归因。

## 官方提交记录

Submission history From: Muxi Diao [ view email ] [v1] Wed, 4 Nov 2026 17:52:11 UTC (120 KB)
