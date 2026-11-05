# 14. Robocasa-Mem: Benchmarking Environment and Process Memory in Long-Horizon Mobile Manipulation

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06475)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06475)；[仓库内 PDF](pdf/2611.06475.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Chen, Sihang；Ye, Chen；Chen, Wei；Lei, Xiaohan；Tang, Zhipeng；Zhang, Sha；Zhang, Yuan；Chen, Zixuan；Deng, Jiajun；Li, Houqiang；Zhang, Yanyong
- 机构：首页署名已核验：USTC；Tongji University；CUHK；Anhui University；Nanjing University。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：process memory; multitask scheduling。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–6、8–9；已获取完整17页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

把移动操作中的环境记忆与过程记忆分开，包含多任务交错时未完成义务的恢复。

## 2. 怎么做、实验如何设计

9任务、每任务200演示，共1,800条；50个留出场景种子/任务。通过历史不同但当前观察近似的任务设计制造真实记忆需求；根据代理实际行为确定后续正确目标，而不强制唯一专家轨迹。HMAP用实体/过程文本记忆规划，高层子目标配低层3D视觉控制；另有10次真机物体搬运。

## 3. 结论

平均成功率约16.2%到24.2%；TempReport 0.22到0.86是明显贡献来源。但两项多任务调度所有方法成功率都为0。真机正确容器为8/10对2/10，样本很小。

## 4. 未来影响

推断：对多目标记忆尤其有用，因为会记住事实却不会切换/恢复待办的系统可被单独暴露。

## 5. Critical thinking

结果仍混合记忆、规划和控制能力；9任务未覆盖真实机器人多样性，真机10次不宜泛化。SCR与最终成功应分开。建议给oracle感知/动作和oracle记忆分别诊断，加入任务取消、抢占、等待条件变化，并增加成功率置信区间及长时状态漂移。

## 6. 可信度判断

3/5。行为条件化评价和阶段分解有价值；总体成功率低，多任务调度尚未被解决，真机证据有限。

## 官方提交记录

Submission history From: Zhipeng Tang [ view email ] [v1] Wed, 4 Nov 2026 13:16:32 UTC (1,989 KB)
