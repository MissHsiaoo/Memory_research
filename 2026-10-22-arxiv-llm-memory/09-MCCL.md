# 09. Memory-Centric Continual Learning for AI Agents

- arXiv：[摘要](https://arxiv.org/abs/2610.29357) · [官方PDF](https://arxiv.org/pdf/2610.29357) · [本地PDF](pdf/2610.29357.pdf)
- 提交日期：21 Oct 2026；正式公告批次：2026-10-22（星期四），本报告对应北京时间2026-10-22。提交日不作为公告日。
- 作者：Dongfang Li , Zhuoen Chen , Bonian Jia , Zixuan Liu , Zhengxuan Lu , Can Deng , Yukun Shi , Yuhang Meng , Xin Zhang , Jiahe Huang , Fuhao Li , Junmai Wang , Shunyao Wen , Jingjun Sun , Jiaxu Tian , Jiangling Zhang , Zihan Wang , Liangyou Li , Yitong Yao , Shuangyong Song , Beilun Wang , Pengxu Wei , Hanlin Xu , Chang Liu , Yongxiang Li , Baotian Hu , Xiangyang Ji , Min Zhang
- 机构：哈尔滨工业大学（深圳）；深圳河套学院；清华大学；东南大学；中国电信星辰AGI实验室；华为（PDF署名核验；MCCL为第50页作者表，其余为首页）
- 机构优先级：A（强研究机构层）；主题相关性：直接相关；标签：持续学习；记忆taxonomy；评测协议
- 证据可信度：3/5，与机构优先级独立。
- 阅读范围：首页、正文第5、9、15–16、18页及第50页机构作者表。官方PDF共50页，已下载并解析、检查首页渲染；未声称逐页精读所有附录或独立复现实验。

## 做了什么

提出Memory-Centric Continual Learning：判断记忆是否带来持续学习，应看未来行为收益而不只是存储与检索。

## 怎么做、实验如何设计

以存储载体、知识资产、管理策略三个轴分类，区分状态更新和策略演化双循环。建议分别测延迟/干扰下的保留、变化后的恢复以及跨任务迁移；保留率以相对无经验基线的行为增益为基础，而非记录存活率。

## 结论

主要贡献是组织框架、评测建议与资源缩放分析，不应写成一个新方法已在统一大基准全面胜出。文中明确离线学得固定管理策略不等于部署时策略持续演化。

## 未来影响

我的推断：可据此设计多目标记忆实验，分开优化记住、更新、转移和成本，避免只报QA准确率。

## Critical thinking

概念覆盖广但可操作性依赖具体任务；行为差异也可能来自更多推理算力。建议设置同预算重放、记忆重置、随机记忆和错位记忆对照，并保持延迟与干扰两个因素独立。

## 可信度判断

3/5：适合作为研究问题和评测设计依据；不是新系统性能的独立强证据。机构来自末页明确署名，不由首页logo推断。

## 证据边界

方法和数值为上述阅读范围内的论文报告；未来影响与研究建议是本报告的推断，不是已验证结果。
