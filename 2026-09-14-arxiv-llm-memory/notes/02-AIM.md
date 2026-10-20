# 02｜AIM: A Privacy-Aware Interoperable Memory Framework for Multi-Agent Multi-User LLM Systems

- arXiv：[2609.12320v1](https://arxiv.org/abs/2609.12320v1) · [官方PDF](https://arxiv.org/pdf/2609.12320v1) · [本地PDF](../papers/02-AIM.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Zachary Johnson , Nigel Boachie Kumankumah , Somya Chatterjee , Tejas Sathyamurthi , Min Chen , Xinyi Alice Li , Xiao Wang , Emily Morgan Gelchie , Jessica Lin , Sadid A. Hasan , Sulaiman Vesal
- 核验机构：Microsoft（PDF署名，未额外写成MSR）；依据为所下载PDF首页署名。
- 机构优先级：A｜顶级产业机构。研究标签：直接相关｜multi-user memory / privacy / personalized memory。
- 主观新颖性：4/5；证据可信度：3.5/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§3–6、表1、附录LoCoMo说明；表1视觉核验。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12320-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

提出 AIM，把多用户、多agent的持久记忆管理拆成私有和共享两类，并发布 MUMBench，联合评估创建、检索、更新、删除和可见性。价值不只是检索准确率，而是将用户隔离、状态演化与记忆操作纳入同一实验对象。

## 2. 怎么做，实验怎么做

输入先识别操作，再抽取内容、标签和元数据，分类PUBLIC/PRIVATE；在对应可见范围内做ICL语义去重，判断CREATE/UPDATE/NO-OP。向量库采用HNSW、3072维embedding，并在索引查询层下推用户过滤；随后用标签筛选、LLM重排及时间新近度融合。去重把整个可见比较集合放进上下文，规模增长是潜在成本瓶颈。

MUMBench由GPT-4o合成并人工检查，672次交互、编码/客服/教育/旅行四域；五个主模型，每域三次试验，清空跨域存储，顺序回放完整流水线。表1报告strict、state-aware、visibility和内容质量。

## 3. Conclusion：原文结论及边界

GPT-5.4-mini严格操作准确率58.8%、state-aware 70.5%；96.0%的最高visibility来自GPT-5.4，不是同一配置同时达到三个headline。mini的visibility为95.0%。state-aware会按当前实际存储状态放宽某些预期操作，因此不能等同于从头到尾正确完成用户需求。作者也报告检索相关性最高45.0%，且单轮LoCoMo实验不如Mem0。

## 4. Future impact：潜在影响

我的推断：多租户agent记忆应以访问控制及可审计状态机为底座，而不是只给向量检索增加一个user_id。MUMBench可作为研究起点，扩展组级分享、权限撤销、跨agent版本一致性和删除传播。

## 5. Critical thinking：我的判断与可检验拓展

索引隔离只保护已经被正确标为PRIVATE的记录；若分类器将私人事实误标PUBLIC，检索过滤无法补救，96%不是隐私安全保证。私有/公开二分也忽略组织、项目、时间和授权主体。公共记忆允许用户创建/修改，存在投毒风险。更强实验应测敏感信息假公开率、攻击者成功率、权限变更后的残留，以及不确定时默认私有的效用代价。

## 6. 可信度、优点与不足

可信度3.5/5；novelty 4/5。优点是五模型三次运行、严格与状态容错指标分开、明确披露检索和公共写入问题。局限是合成规模小、没有正式安全证明、操作和抽取正确不等于最终回答正确。最值得复现的是错误级联与权限误分类，而非只追总体accuracy；机构强不改变安全证据尚不充分这一结论。

