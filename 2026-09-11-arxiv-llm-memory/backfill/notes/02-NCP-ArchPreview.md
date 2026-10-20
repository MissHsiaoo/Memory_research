# 2. NCP-ArchPreview

NCP-ArchPreview Technical Report: Moving towards Latent Space Language Models through Next Concept Prediction

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.10715v1](https://arxiv.org/abs/2609.10715v1) · [官方 PDF](https://arxiv.org/pdf/2609.10715v1) · [本地 PDF](../papers/02-NCP-ArchPreview.pdf)
- 首次提交：2026-09-09T18:12:43Z（UTC，与公告日不是同一概念）。
- 作者： NCP Team, Jiaqi Cao, Chiyu Chen, Shuang Cheng, Xu Cheng, Beiya Dai, Yufan Feng, Kewen Ge, Ruijun Ge, Jiayi Huang, Yang Jiao, Dahua Lin, Zhouhan Lin, Yifan Liu, Yuliang Liu, Biqing Qi, Mowen Ruan, Junzhe Shen, Yunchong Song, Hao Sun, Zhongbo Tian, Yixuan Wang, Rubin Wei, Jiaxin Xiong, Kangyu Yang, Qian Yao, Qi Zhang, Bowen Zhou
- 机构：Shanghai AI Lab；上海交通大学 LUMIA Lab（PDF 首页文字与视觉核验）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：直接相关｜latent representations / 参数化适应
- 原文定位：§2–5、§7，PDF 第 10–23 页。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

在 next-token prediction 外增加 Next Concept Prediction：预测多个 token 对应的离散潜在概念，再用概念指导 token 生成。

## 2. 怎么做的，实验怎么做

32 层 token 网络拆成各 16 层 encoder/decoder，增加 8 层 concept module；每 4 个 token 一组，32 个 VQ codebooks、每本 128 项。联合优化 NTP、VQ、NCP，通过残差路径注入概念。域适应可只更新约 17M VQ 参数。

实验与结果：8.94B 模型在 Dolma-3 上预训练 5.73T tokens，另有 100B mid-training；按 OLMo 协议评估 30 个基准家族。预训练后宏均值较 OLMo-3-7B 高 2.45 点，mid-training 后优势缩至 0.59 点。论文另设参数对齐 8.9B 对照，不能将 51.3% tokens 达到同损失直接解读成算力减半。VQ-only 数学适应均值 +4.27、一般能力均值 +0.39；知识适应增益弱于全参/LoRA。

## 3. Conclusion

潜在概念预测在万亿 token 规模可训练，且提供低参数适应接口；它不是已验证的长期用户记忆系统，报告明确未做长上下文训练。

## 4. Future impact

最值得借鉴的是将用户/领域适应限制在可替换概念词表中，研究记忆隔离和遗忘，而非直接动整个 backbone。

## 5. Critical thinking：优点、问题与可验证拓展

优点是规模、消融、参数对齐和能力保留指标较齐。局限：主比较参数量不同；更低 loss 未等比例转化成能力；固定 4-token 概念并不保证语义可解释。建议做多用户隔离 VQ、删除/回滚、跨用户串扰和长期偏好改变实验，并匹配总训练 FLOPs。可信度 4/5，尚未独立复现。

## 6. Novelty 与证据置信度

- 主观 novelty：**4.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**4/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

