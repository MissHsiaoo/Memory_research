# 15. LLM-Information-Geometry

The information geometry of large language models is shared, learned, and controllable

- 公告批次：**2026-09-11**；2026-09-12 补发，不是 9 月 12 日新论文。
- 原文：[arXiv 2609.11063v1](https://arxiv.org/abs/2609.11063v1) · [官方 PDF](https://arxiv.org/pdf/2609.11063v1) · [本地 PDF](../papers/15-LLM-Information-Geometry.pdf)
- 首次提交：2026-09-10T04:09:49Z（UTC，与公告日不是同一概念）。
- 作者：Dario Picozzi
- 机构：University College London、London Centre for Nanotechnology（PDF 首页）
- 机构优先级：强机构主榜；机构署名/归属的核验边界见上文。此为本次研究阅读偏好，不是学校综合排名。
- 研究标签：相邻启发｜latent representation / 最小干扰编辑
- 原文定位：主文及 Methods，PDF 第 16–20 页；Supplementary Note 10。核查了相关方法、实验和局限；未复跑代码或完整审计全部理论证明。

## 1. 做了什么

用输出概率的 Fisher–Rao 几何研究模型共享结构，并构造改变目标行为时尽量少扰动其他行为的局部控制。

## 2. 怎么做的，实验怎么做

将 next-token 概率 Fisher metric 拉回隐状态空间，以正则化自然梯度决定干预方向；分开处理坐标依赖的 activation geometry 与输出行为几何。

实验与结果：Pythia 70M–6.9B，Qwen 小模型、GPT-2/XL，以及 Mamba/RWKV 等跨架构比较；受控语言实验含三类架构、两个容量、八组测试语言对，调参使用单独 pilot。包括事实编辑、风格/真实性与 donor-prompt 到未见 prompt 的控制迁移。方法给出局部 KL 二阶近似及最小扰动解，未在本次逐条复核全部证明。

## 3. Conclusion

输出行为几何比原始表示坐标更适合作为某些比较与局部编辑基准；局部最优不能推出全局长程最小干扰。

## 4. Future impact

给 personalized latent memory 写入定义“损伤预算”：要求用户目标改变，同时限制 reference prompts 的输出 KL。

## 5. Critical thinking：优点、问题与可验证拓展

优点是区分坐标问题、合成随机化控制及测试集隔离。局限是论证跨度大、干预局部线性近似与阻尼选择限制外推；下一 token KL 小不保证多轮行为漂移小。建议只复现一条最小扰动个性化编辑链，再测多次更新叠加和撤回。可信度 3.5/5，广泛理论主张仍需独立审查。

## 6. Novelty 与证据置信度

- 主观 novelty：**4.5/5**。这是阅读后判断，未完成所有先行工作的穷尽式查重。
- 证据可信度：**3.5/5**。不是统计概率；评分依据是上述对照、样本范围、指标口径和局限，不因机构名气自动提高。
- 实验数字来自作者报告，不是独立复现结果。Future impact 和建议实验是我的推断，不能作为原论文已证明的结论。
- 公告证据：[当批 cs.CL RSS](../sources/cs.CL-rss.xml)、[cs.AI RSS](../sources/cs.AI-rss.xml)、[cs.LG RSS](../sources/cs.LG-rss.xml)。跨分类出现不单独证明首次公告；本期同时核对 v1、提交时间和当批条目，排除旧文更新及明显旧文 cross-list。

