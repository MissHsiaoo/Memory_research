# 05. Audio LLMs Know When They Can't Hear You

- arXiv：[2609.30625](https://arxiv.org/abs/2609.30625)
- 提交日期：2026-09-24；正式公告批次：2026-09-28（cs.AI new）
- 作者/机构（PDF 首页核验）：Amirhosein Javadi 等；Apple、UC San Diego
- 机构优先级：**S｜顶级工业研究机构**
- 研究标签：弱相关但具启发性、latent state、uncertainty、memory write gate
- 本地 PDF：[2609.30625.pdf](./2609.30625.pdf)

## 1. 做了什么

研究 Audio LLM 能否预知自己的转写会失败。生成端口头自评很差，但冻结 audio encoder 的隐藏表示中已经编码了可靠性，因此作者训练一个轻量分类头，在生成前决定是否应向用户澄清。

## 2. 怎么做、实验如何设计

用固定语音和噪声/混响对，通过二分搜索找出 WER=0、10%、30% 的临界 SNR，形成四级可靠性标签；对冻结 encoder 的帧表示做 learned temporal pooling，再接两层 MLP。训练域使用 LibriSpeech、DNS/MUSAN 与模拟 RIR，跨域使用 LJSpeech、SONYC-UST 与真实 RIR；比较 SNR、无参考语音质量、token probability/entropy、Fe-WER。Qwen2-Audio 上达到 81.10%/78.09% 的域内/跨域 macro-F1，比最强对手高 10.33/11.93 点，分类头仅约 0.33M 参数。

## 3. Conclusion

模型“说不出自己不知道”，不等于内部没有信号；正确的读出位置在 encoder latent state，而非语言生成的自我报告。少量边界校准还能在音频模型家族间迁移标签库。

## 4. Future impact

对 memory system 的启发是把潜在可靠性作为写入门：低质量感知不应进入长期记忆，而应先请求澄清。该思想可扩展到视觉、工具结果和用户画像更新。

## 5. Critical thinking

标签由同一目标模型的 WER 定义，契合“model-conditional reliability”，但合成噪声边界未必覆盖口音、语义歧义和真实设备失真；分类器也可能只学到声学质量代理。建议在自然失败、跨语言、说话人迁移和端到端澄清收益上验证，并用控制实验区分“声音差”与“该模型会转错”。

## 6. 可信度判断

**4/5。** 已阅读全文。跨域、跨模型、强基线和计算开销证据完整；仍是受控声学扰动，真实用户交互中的外部效度有限。
