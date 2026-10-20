# 18｜OneLA: Scaling Linear-Attention Decoding to Large Beams in Generative Recommendation

- arXiv：[2609.12399v1](https://arxiv.org/abs/2609.12399v1) · [官方PDF](https://arxiv.org/pdf/2609.12399v1) · [本地PDF](../papers/18-OneLA.pdf)
- 首次提交：2026-09-11（官方摘要页；不是公告日期）。公告归属：2026-09-14 官方 new/cross 列表；版本 v1。
- 作者：Xiangrui Yang , Cheng Peng , Yunfeng Zhao , Liang Zeng , Ao Hu , Jiawei Yang , Shengzhe Wang , Jingshan Lv , Xiao Liang , Chen Yang , Jiaqiang Liu , Yiming Qiu
- 核验机构：Kuaishou Technology、香港大学、北京大学；依据为所下载PDF首页署名。
- 机构优先级：B｜强产业团队／顶级高校合作。研究标签：相邻强启发｜shared recurrent memory / branching state / linear attention。
- 主观新颖性：4/5；证据可信度：4/5。分数不是正确概率，机构与可信度独立评估。
- 阅读范围：§3设计、§4–5、图6–8。没有复跑代码或训练；“我的推断”及建议均非论文已证结论。
- 来源快照：[官方摘要页](../sources/2609.12399-abs.html) · [批次检查](../sources/20260914T020652Z/batch-check.json)。

## 1. 做了什么

OneLA解决生成式推荐中大beam解码的状态复制问题：数百候选有相同prompt、只有很短后缀不同，逐beam复制完整线性attention状态很浪费。它把公共前缀状态与分支增量分离，对多agent共享背景、短程探索分支具有直接系统启发。

## 2. 怎么做，实验怎么做

保存一个prompt状态，加append-only的紧凑转移记录，并用轻量祖先索引追踪beam lineage；只重放当前读出需要的投影，不重建每条beam的完整矩阵，融合kernel跨beam复用共享状态。

完整模型测Qwen3.5-0.8B，6 dense+18 GDN层，4请求、beam256、prompt1K/5K、输出3–7tokens。算子套件405种形状，覆盖请求4/8/16、beam128/256/512和多种状态几何，比较vLLM/SGLang、FlashInfer、TensorRT-LLM的支持形状。

## 3. Conclusion：原文结论及边界

完整模型decode-forward加速1.54–2.46×，不是完整请求含prefill和服务开销的收益。GDN算子层面可有约40×中位加速，不能拿来代替整模型加速。405形状相对FP32 FullState最大绝对输出误差4.88e-4，支持数值一致性；未直接报告线上推荐点击/业务收益。

## 4. Future impact：潜在影响

我的推断：可以为并行agent或tree search提供共享基础latent state加分支增量，降低测试多个候选计划的内存成本。短分支适合增量表示，长时间分叉则可能需checkpoint/合并策略；该论文并未验证任意长分支。

## 5. Critical thinking：我的判断与可检验拓展

收益依赖短后缀、大beam和前缀共享。推荐只输出3–7个语义token，不能直接迁移到几千token的agent推理。beam排序还可能对小数值误差敏感，应比较最终候选排序、不同precision和长链误差积累。更完整评估要包含prefill、动态batch、CPU调度和业务质量。

## 6. 可信度、优点与不足

可信度4/5；novelty4/5。优点是状态表示与kernel设计一致、支持范围清楚、数值误差核查和整模型性能都有。局限是完整模型只有0.8B，输出很短，没有长期记忆语义实验。建议研究分支变长后的checkpoint临界点；不要把物理状态复用误说成模型学会新的个性化记忆。

