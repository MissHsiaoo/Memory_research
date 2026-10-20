# Informed Masking：扩散 LLM 强化学习的结构感知掩码

- arXiv：[2609.25927](https://arxiv.org/abs/2609.25927)；[官方 PDF](https://arxiv.org/pdf/2609.25927)
- v1 提交日期：2026-09-22；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Xiaoyi Yu 等；中国人民大学、Xiaomi MiLM Plus、摩德纳和雷焦艾米利亚大学、北京大学
- 机构优先级：S（头部公司+强校、直接相关）
- 研究标签：diffusion LLM、RL、masking、denoising trajectory

## 1. 做了什么

论文发现 dLLM rollout 中 token 存在 upstream/downstream 结构：揭示 upstream token 会显著改变附近未解码位置的置信度，而 downstream token 更局部。随机掩码会采到难以恢复的 upstream 子问题，故提出 Informed Masking 优先掩码 downstream token。

## 2. 怎么做、实验如何设计

方法从已有去噪轨迹计算每 token 的结构优先级，不增加推理调用，然后用该分数偏置 RL likelihood surrogate 的掩码采样。它被插入三种 dLLM RL 方法，在 LLaDA-8B-Instruct 上以数学和规划任务测试；论文分析不同 mask ratio/距离的目标 token log-probability、训练稳定性和多种消融。

## 3. 结论

PDF 报告三种 RL 方法相对平均增益最高分别为 2.01%、8.68%、5.77%，同时训练更稳定。结论是 Monte Carlo 预算很小时，采样什么子问题比单纯改进 likelihood bound 同样关键。

## 4. Future impact

这可能成为 dLLM post-training 的通用接口，并启发 latent memory：利用一次状态更新对未来位置的影响来区分“因果锚点”与“可延后细节”。

## 5. Critical thinking

downstream 较易恢复并不必然意味着其梯度对最终 reward 最有信息；方法可能通过降低方差牺牲探索难例。当前证据主要来自单一 8B backbone，应在 Dream、不同噪声 schedule、长文本和开放生成上比较等计算预算下的 bias/variance。还应直接测策略梯度估计误差，而不仅是最终准确率。

## 6. 可信度判断

- 评分：4/5
- 依据：阅读全文包含机制诊断、三种 RL 插件实验、多个任务和稳定性分析。
- 优点：结构洞见新颖、零额外推理成本、插件式验证。
- 局限：backbone 范围较窄；相对百分比需结合绝对增益；易子问题偏置的长期影响未知。

