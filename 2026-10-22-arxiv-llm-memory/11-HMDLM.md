# 11. Hierarchical Masked Diffusion Language Models

- arXiv：[摘要](https://arxiv.org/abs/2610.29255) · [官方PDF](https://arxiv.org/pdf/2610.29255) · [本地PDF](pdf/2610.29255.pdf)
- 提交日期：21 Oct 2026；正式公告批次：2026-10-22（星期四），本报告对应北京时间2026-10-22。提交日不作为公告日。
- 作者：Parul Gupta , Satwik , Avni Aggarwal , Bhavesh Gurnani , Arnab Kumar Mondal , Dinesh Khandelwal , Dinesh Garg , Parag Singla
- 机构：IIT Delhi；IBM Research（PDF署名核验；MCCL为第50页作者表，其余为首页）
- 机构优先级：A（强研究机构层）；主题相关性：直接相关；标签：diffusion LLM；层次生成
- 证据可信度：3/5，与机构优先级独立。
- 阅读范围：首页及正文第4、6、8页。官方PDF共32页，已下载并解析、检查首页渲染；未声称逐页精读所有附录或独立复现实验。

## 做了什么

给token位置赋予层次优先级，让重要位置更早揭示，其他位置在其条件下并行生成。

## 怎么做、实验如何设计

先预测层次，再预测token；层次与token联合掩码，各层使用不同噪声日程并推导相应NELBO。LM1B、WikiHow与Sudoku实验，WikiHow有位置层次和频率层次两种设置。

## 结论

WikiHow频率层次的模型PPL在三种长度都优于表内基线，例如256长度17.62对ADLM22.05。位置层次虽然生成PPL低，但MAUVE不总提升；不能只选一个指标宣布全面更好。

## 未来影响

我的推断：分层去噪可用于先确定计划/记忆锚点再补细节，但这是后续设想，论文未验证记忆系统。

## Critical thinking

训练阶段使用金标准层次而推理要预测，存在暴露差异。论文说明HMDLM训练略长，且部分基线引用旧结果、ADLM复训梯度爆炸。应按总FLOPs和两次前向成本比较，并测试不准确层次标签。

## 可信度判断

3/5：有明确概率建模和多任务实验；计算公平性与基线复训限制需要保留，不能仅因IBM署名提高证据评分。

## 证据边界

方法和数值为上述阅读范围内的论文报告；未来影响与研究建议是本报告的推断，不是已验证结果。
