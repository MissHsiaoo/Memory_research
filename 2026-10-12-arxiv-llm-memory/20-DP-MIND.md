# 20 DP-MIND：差分隐私下的长上下文压缩记忆

- 论文：[arXiv:2610.13132](https://arxiv.org/abs/2610.13132) · [官方 PDF](https://arxiv.org/pdf/2610.13132) · [本地 PDF](2610.13132.pdf)
- 日期：**2026-10-12 正式公告**；2026-10-09 提交。
- 作者：Zhihao Liu、Yitian Cheng、Shuang Liu、Rui Wen、Yuke Hu、Zhan Qin。机构：Zhejiang University、Ant Group、Institute of Science Tokyo、King Abdullah University of Science and Technology（PDF 首页核验）。
- 机构优先级：B（强高校 + 工业研究）；研究标签：LLM memory systems、long-context inference、differential privacy。

1. **做了什么｜论文证据：**提出 DP-MIND，让外部 LLM 在输入受差分隐私扰动时，仍能以压缩记忆处理百万 token 级长上下文。
2. **怎么做、实验如何设计｜论文证据：**本地对文本扰动后分块发送，跨块传递紧凑的任务相关记忆；在扰动输入上用 RL 优化记忆构造，并在本地解噪受损的答案片段。提供隐私分析，测试 RULER-HQA、NIAH 等长上下文检索、不同隐私预算与长度。
3. **结论｜论文证据：**论文报告相比所比 DP 与长上下文基线更好的扩展性和效用；隐私结论遵循其扰动机制与可信本地计算假设，不等于任何部署均安全。
4. **未来影响｜我的推断：**隐私边界与记忆压缩可共同设计，使远程模型不必读取明文长历史。
5. **Critical thinking｜我的推断：**记忆跨块传递可能让单块错误累积；不同 ε 和扰动机制下的保护强度/可用性不可简单横比。建议形式化审计完整管线的隐私预算、成本与成员推断风险，并测试稀疏关键信息在百万 token 末端的保持率。
6. **可信度：3/5。**依据：核查隐私主张、长上下文实验与基线；优点是同时衡量效用和隐私假设，局限是组合系统的真实泄露风险及多任务泛化需要独立审计。
