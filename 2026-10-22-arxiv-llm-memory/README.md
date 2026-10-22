# 2026-10-22 arXiv LLM Memory 日报

## 批次与交付

官方列表标题为 **Thursday, 22 October 2026**；对应本报告北京时间2026-10-22。首次核验约16:39北京时间。只纳入官方 **New submissions**，不纳入Cross-lists或Replacements；不把10月19–21日的提交日期误当公告日期，也未扩展到历史30天。

已筛读cs、cs.CL、cs.AI、cs.LG、stat.ML官方列表，去重754条新提交目录；下载29份候选PDF进行机构/主题复核，最终收录20篇（19篇直接相关、1篇弱相关但具启发性）。这不是对754篇逐篇阅读全文，也不是声称穷尽所有学科。目标20篇已达到，无需旧文补数。官方页面快照和候选目录保存在sources，入选PDF校验值与阅读范围见verification.json。

来源：[cs](https://arxiv.org/list/cs/new)、[cs.CL](https://arxiv.org/list/cs.CL/new)、[cs.AI](https://arxiv.org/list/cs.AI/new)、[cs.LG](https://arxiv.org/list/cs.LG/new)、[stat.ML](https://arxiv.org/list/stat.ML/new)。这些在线地址会滚动变化，历史核验以本目录快照为准。

## 排序与全部入选论文

排序遵循机构优先级→直接相关性→方法新颖性/严谨性。A表示本报告强研究机构层，包括大型研究实验室及一流研究型高校；不把合作机构的名气当作证据强度。A层内部结合直接相关性和贡献排序。MemoryTax尽管机构为A，证据仍只给2分；UserSWE因主题较间接列最后。本日没有单独的低机构优先级黑马配额。每篇署名与实际阅读范围均在笔记内。

|排名|论文与中文评析|已核验机构|相关性|可信度|
|---|---|---|---|---|
|1|[PerMIT](01-PerMIT.md)|AWS AI Labs；Stony Brook University|直接相关|4/5|
|2|[Uni-Mem](02-Uni-Mem.md)|Huawei Noah’s Ark Lab；东南大学；中山大学；山东师范大学|直接相关|4/5|
|3|[MHG-Mem](03-MHG-Mem.md)|Huawei Noah’s Ark Lab；中山大学；东南大学；山东师范大学|直接相关|4/5|
|4|[PreCoMem](04-PreCoMem.md)|南开大学；vivo AI Lab；清华大学；华中科技大学；中国科学院大学|直接相关|4/5|
|5|[MOSAIC](05-MOSAIC.md)|香港科技大学；爱丁堡大学|直接相关|4/5|
|6|[ExpEvolve](06-ExpEvolve.md)|MBZUAI；CMU；香港浸会大学；香港中文大学；悉尼大学|直接相关|4/5|
|7|[LongZero](07-LongZero.md)|清华大学|直接相关|3/5|
|8|[Long-Context-Scaling](08-Long-Context-Scaling.md)|清华大学；OpenBMB|直接相关|4/5|
|9|[MCCL](09-MCCL.md)|哈尔滨工业大学（深圳）；深圳河套学院；清华大学；东南大学；中国电信星辰AGI实验室；华为|直接相关|3/5|
|10|[Looped-UDLM](10-Looped-UDLM.md)|MBZUAI；Sony Group；MIT|直接相关|4/5|
|11|[HMDLM](11-HMDLM.md)|IIT Delhi；IBM Research|直接相关|3/5|
|12|[SearchWeaver](12-SearchWeaver.md)|KAIST；高丽大学|直接相关|4/5|
|13|[ClariEdge](13-ClariEdge.md)|IBM Research|直接相关|3/5|
|14|[SpatialBrain](14-SpatialBrain.md)|上海交通大学；浙江大学|直接相关|3/5|
|15|[C2U-RAG](15-C2U-RAG.md)|南洋理工大学；东京科学大学；北京航空航天大学|直接相关|3/5|
|16|[MAPS](16-MAPS.md)|东北大学（沈阳）；清华大学|直接相关|3/5|
|17|[CAPE](17-CAPE.md)|中国科学技术大学；三位作者首页署名Independent Researcher|直接相关|4/5|
|18|[MemoryTax](18-MemoryTax.md)|上海交通大学|直接相关|2/5|
|19|[GRAFT](19-GRAFT.md)|电子科技大学|直接相关|3/5|
|20|[UserSWE](20-UserSWE.md)|Tencent Hunyuan|弱相关但具启发性|3/5|

## 机构分布

以下按署名参与计数，合作论文允许重叠：清华大学5篇；华为3篇；中山大学2篇；东南大学3篇；上海交通大学2篇；IBM Research2篇；MBZUAI2篇。AWS AI Labs、Tencent Hunyuan、vivo AI Lab、Sony Group、MIT、CMU、香港科技大学、爱丁堡大学、KAIST、南洋理工大学、中国科学技术大学等各有参与。完整署名以表格和PDF为准，未将使用某公司模型当作该公司论文。CAPE中三位使用公司邮箱的作者明确署名独立研究者，未归入蚂蚁机构。

## 主题趋势

1. **从检索命中走向行为收益。** MCCL要求分开测保留、适应和迁移；ExpEvolve/SpatialBrain把经验转成可调用决策或技能。
2. **写入与读取必须共同评价。** Uni-Mem通过阶段解耦处理联合训练归因；MemoryTax用很小的实验提醒强读者补不回丢失事实，不能据此宣布记忆系统普遍无用。
3. **多模态记忆要保留可回访来源。** MHG-Mem组织实体演化和原始证据；MOSAIC区分检索到与实际送达，防止将API打包丢失误算成阅读失败。
4. **更新、权限与遗忘是不同问题。** PreCoMem暂存未确认信念；PerMIT确认使用授权；C²U只压低检索暴露，不是彻底删除。
5. **扩散模型算力和质量需要多指标。** Looped UDLM研究循环计算，HMDLM研究先后次序，GRAFT揭示困惑度可能掩盖词汇尾部缺失。

## 最值得深读的3篇

- **Uni-Mem**：同一策略联合管理写入和检索，事件归因可直接启发可学习记忆控制器；先读同协议基线和查询全部后置的限制。
- **MOSAIC**：提供WRITE/RETRIEVE/DELIVER/READ配对诊断，适合设计多目标记忆benchmark；应保留拒答、预算和各模态分层指标。
- **PerMIT**：把记忆授权变成可审计接口，适合研究共享记忆安全；须先读信任假设，不能把形式接口保证扩大成任意LLM内容安全。

补充阅读：若优先研究个性化变化，先读PreCoMem；若做推荐，读CAPE的“候选可达率—排序命中率”双阶段诊断。

## 候选取舍与证据限制

已额外查阅或核验SkillEval、OSynth、DiffResearch、Signals and Queries、Preference Is Not Permission、持久记忆注入、AI研究团队、GeoMem-VLA、When Thoughts Become Memory等候选的PDF或首页。它们分别因与核心主题更间接、机构优先级较低或20篇配额下的取舍未进入主榜，不表示论文质量差。统计学分类的When Thoughts Become Memory署名Hassana Labs，未冒称顶级高校合作。

可信度评分是本次所读证据的保守判断，非期刊评级；本次没有执行作者代码、独立复现或逐条验证所有证明。各论文不同读者、裁判、数据划分及预算下的准确率不能横向组成统一排行榜。全部20份官方PDF已保存，笔记使用仓库内相对链接；GitHub推送状态由实际远端提交核验，不以本文件生成作为推送成功证据。
