# 13 — Capturing In-Context Learning Dynamics with Task Operators

- arXiv：[2610.01054](https://arxiv.org/abs/2610.01054)；[官方 PDF](https://arxiv.org/pdf/2610.01054)；[本地 PDF](./2610.01054.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Guangzhi Xiong 等；University of Virginia
- 机构优先级：**A+，一流研究型高校**；研究标签：`in-context learning` `task representation` `activation compression`
- 证据范围：核读 PDF 方法、实验；性能描述为作者报告。

## 1. 做了什么

把 ICL 示例对注意力头的影响压缩为任务算子，试图在不重复放入全部示例的情况下重现上下文学习。

## 2. 怎么做、实验如何设计

论文分析注意力头输出相对无上下文输出呈仿射变换，并观察同任务跨样本参数稳定，据此推导对输出投影的算子更新。PDF 在 Qwen3-4B/8B、Llama3.2-3B、Llama3.1-8B 上测词汇、算法、GSM8K、MATH500、GPQA-Diamond 等八类任务，与先前固定激活向量等压缩法比较，还做稀疏电路与不相交示例批次算子平均测试。作者报告整体优于所比既有方法、缩小零样本与完整 ICL 差距。

## 3. Conclusion

ICL 的任务信息可表达为输入相关的算子，而非必然需要长提示或单一固定向量。

## 4. Future impact

为低成本“隐式任务记忆”提供路径，也可能帮助理解模型如何重复应用用户偏好规则。

## 5. Critical thinking

**推断：** 算子稳定性可能只在同分布任务成立，且注入模型内部不如外部记忆可审计。应测任务组合、对抗性示例、未知模板、闭源模型不可访问场景及完整抽取成本。

## 6. 可信度判断

**4/5。** 解析推导与四模型、八任务实证互补；从机制实验到长期个人化部署仍需验证。
