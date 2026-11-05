# 11. EvoGuard: Mitigating Degradation in Online Skill Evolution

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06444)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06444)；[仓库内 PDF](pdf/2611.06444.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Wang, Yanli；Bai, Zichen；Jiang, Tianyue；Shao, Kunming；Shi, Junhao；Liu, Xueqin；Sun, Jinguo；Li, Muye；Bi, Tingting；Wang, Yanlin；Zheng, Shaoqiang；Diao, Xuefei；Zeng, Zhuwei；Duan, Nan；Cao, Peng
- 机构：首页署名已核验：JD.com；Sun Yat-sen University；University of Melbourne；HKUST。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：self-evolving memory; skill selection。
- 相关性：直接相关（含用户明确列入的扩散语言模型方向）。
- 阅读范围：PDF首页及关键方法/实验页 1、3–6；已获取完整16页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

为在线技能改写加入学习型接受/拒绝门，避免每次经验总结都直接替换旧技能。

## 2. 怎么做、实验如何设计

先离线生成多来源技能，使用独立任务集估计效用，以差距足够大的同family技能对训练A/B选择器；线上仅看family描述和两份技能文本，单前向选择，不追加rollout。冻结执行器/生成器/选择器，仅技能文本演化。评测ALFWorld、ScienceWorld、LiveCodeBench、WebShop，3采样种子。

## 3. 结论

ALFWorld 4B执行器seen/unseen成功率55.7%/62.4%，最强基线44.8%/51.2%；只接受约42%–43%有效改写。32B未提供训练效用标签时仍有收益，但部分family比无技能更差，如32B Heat unseen由50.7降至33.3。

## 4. 未来影响

推断：可将记忆写入质量控制独立成一个效用评估组件，重点从“多写经验”转向“防止退化”。

## 5. Critical thinking

无需线上验证不代表无验证成本：离线每个技能都跑了私有任务集。文中的cross-task是同family内迁移，不是新领域。效用由固定执行器和任务分布定义，模型升级或技能分布漂移会失准。建议家族留出、执行器升级、长时间接受错误累积及相同总验证预算比较。

## 6. 可信度判断

4/5。训练/线上信息边界与基线明确，3种子且报告失败family；尚不能保证每次改写都不会退化。

## 官方提交记录

Submission history From: Yanli Wang [ view email ] [v1] Wed, 4 Nov 2026 12:47:32 UTC (358 KB)
