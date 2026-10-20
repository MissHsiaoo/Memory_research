# 13. KITE

- 论文：**KITE: KV-Invariant Transformer Expansion for Efficient Agentic LLM Scaling**
- arXiv：[2609.27294](https://arxiv.org/abs/2609.27294)
- 提交日期：2026-09-23；正式公告批次：2026-09-24（北京时间）
- 作者/机构（PDF 首页核验）：Zhiheng Hu 等；StepFun
- 机构优先级：**A+｜强工业研究团队**
- 研究标签：KV cache、model upcycling、agentic inference、弱相关但具启发性
- 本地 PDF：[2609.27294.pdf](./2609.27294.pdf)

## 1. 做了什么

提出 KV-Invariant Transformer Expansion：扩容模型时把新增参数放到不产生历史 KV 的路径，使训练可从小模型 upcycle，同时保持 prefill 的 KV-producing 路径规模不变。具体实例 SST 将网络分成 Prefiller 与读取其 KV 的 Decoder。

## 2. 怎么做、实验如何设计

从 source checkpoint 复制层到两塔，保留 Prefiller/共享参数优化器状态，Decoder 新建状态并联合续训；比较 47B classic、63B classic 与 67B SST，累计训练 FLOPs 含扩容前后全部阶段。SST 在相近理论训练算力下训练损失最低，并在 OpenBookQA、MMLU、GSM8K、MATH、HumanEval、MBPP、BBH 全部领先。按 75:25 prefill:decode 代理成本估计，SST 比 47B 低 6.7%、比 63B 低 31.6%。

## 3. Conclusion

模型容量增长不必同步扩大 KV 生产路径；在输入占比高的 agent workload 中，可用更多 decode-side capacity 换较低 prefill 成本。

## 4. Future impact

长期 memory agent 通常反复处理大提示和检索证据，prefill 占比高。KITE 可能与 KV 压缩、外部记忆和 context caching 联合优化，形成专为 agent 负载设计的模型架构。

## 5. Critical thinking

最重要的限制是成本来自解析公式而非真实 serving benchmark；只测试一个 SST 连接方案，不能分离 upcycling、参数量和 KV 不变各自贡献，也未建立 scaling law。任务分数虽一致领先，但缺少多随机种子/误差。应在真实并发 agent traces 上测 TTFT、吞吐、显存和总拥有成本，并与 MoE、YOCO、cross-layer KV sharing 做等质量比较。

## 6. 可信度判断

**3/5。** 已阅读全文；训练算力核算和下游结果完整，但核心系统收益尚是理论代理值，因果消融有限。按机构优先和架构启发收录。
