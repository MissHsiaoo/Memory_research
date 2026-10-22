# 04. PreCoMem: Predictive Cognitive Memory for Self-Evolving Long-Term Dialogue Agents

- arXiv：[摘要](https://arxiv.org/abs/2610.29467) · [官方PDF](https://arxiv.org/pdf/2610.29467) · [本地PDF](pdf/2610.29467.pdf)
- 提交日期：21 Oct 2026；正式公告批次：2026-10-22（星期四），本报告对应北京时间2026-10-22。提交日不作为公告日。
- 作者：Jian Zhong , Zeyu Liu , Pingchuan Cao , Rongduo Han , Shunye Tang , Guohuan Xie , Mingyuan Qin , Ran Ji , Xiao Liang , Wei Wang , Haining Zhang
- 机构：南开大学；vivo AI Lab；清华大学；华中科技大学；中国科学院大学（PDF署名核验；MCCL为第50页作者表，其余为首页）
- 机构优先级：A（强研究机构层）；主题相关性：直接相关；标签：个性化记忆；信念变化；稳定性
- 证据可信度：4/5，与机构优先级独立。
- 阅读范围：首页及正文第4–8页；附录未逐项复核。官方PDF共44页，已下载并解析、检查首页渲染；未声称逐页精读所有附录或独立复现实验。

## 做了什么

用带置信度的用户信念区分短暂噪声与真实偏好变化，在保持、暂存假设和纠正之间做选择。

## 怎么做、实验如何设计

有效惊讶度结合语义偏差、矛盾检测和检索分数集中程度；固定双阈值0.2/0.6触发MAINTAIN、PROFILE、CORRECT。检索使用语义、BM25和主题信号乘置信度。评测LoCoMo、LongMemEval-S、PersonaMem-v2及自建DiMoBench，主结果三种子并用多裁判。

## 结论

GPT-4.1下LoCoMo为85.06，对比TiMem84.04；LongMemEval-S89.39，对比EverMemOS86.16。前者提升1.02、后者3.23个百分点。不是每个子任务都领先，收益主要在偏好、更新和跨会话聚合。

## 未来影响

我的推断：显式的待确认假设层比简单新信息覆盖旧信息更适合长期个性化。

## Critical thinking

集中检索不一定准确：高置信错误可能触发错误修改。把惊讶度设零的消融会让系统仅执行保持，不能等同公平移除一个特征。应读路线匹配控制，并测试反讽、隐式撤回、多个用户混淆和重复误信息。

## 可信度判断

4/5：多基准、多骨干和种子提高可信度；自建漂移任务、裁判相关性及门控可靠性仍是局限。论文的认知类比不是生物机制证据。

## 证据边界

方法和数值为上述阅读范围内的论文报告；未来影响与研究建议是本报告的推断，不是已验证结果。
