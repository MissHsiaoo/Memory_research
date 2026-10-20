# Representation-guided in-context learning for medical image interpretation with multimodal large language models

- arXiv：[24057](https://arxiv.org/abs/2609.24057)；[官方 PDF](https://arxiv.org/pdf/2609.24057)
- arXiv 初次提交：2026-09-21（v1）；正式公告归属：2026-09-22 新稿，二者不可混同。
- 作者：Minda Zhao , Fangyu Hu , Yan Luo , Yutong Yang , Jiahui Cai , Kaichen Zhou , Manling Li , Paul Liang , Yilun Du , Lucy Q. Shen , Mengyu Wang（arXiv 官方列表）
- 机构：Harvard Medical School / Mass Eye and Ear；MIT Media Lab；Northwestern University 等（PDF 首页）（论文 PDF 首页核验）
- 机构优先级：A｜全球一流研究型高校
- 研究标签：多模态 ICL；示例检索；外部记忆；相关但医疗场景
- 证据说明：以下数值均为论文自身报告；“我的推断/建议”并非论文实证。

## 1. 做了什么

RG-ICL 关注“给多模态模型哪些示例”而非“给多少示例”：用冻结视觉表征为待解医学影像取相似且任务对齐的案例，不做任务参数更新。它为 ICL 和记忆检索提供一个强烈提醒：相关案例选择可能比上下文长度更重要。

## 2. 怎么做，实验怎么做的

使用冻结图像编码器检索与查询影像相近的演示；VQA 还对齐问题意图。覆盖八个组织病理、放射和视网膜眼底数据集，比较零上下文、随机或固定示例、表示引导示例和微调方法。摘要报告分类平均提高约 20 个百分点、VQA 约 13 个百分点；六个查询对齐案例优于最多 32 个随机案例。正文报告编码器组合、案例数与顺序消融，并观察随机/固定案例有时会使精度低于无上下文。

## 3. Conclusion

在所测公开数据及模型上，检索到的示例质量比盲目增加示例数更重要；这不是无需微调即可满足临床要求的证明。医疗指标依赖数据集分布、标签与影像采集流程，外部医院泛化尤为关键。

## 4. Future impact

个人记忆系统同理可先做“与当前问题的表示对齐”，再给有限高质量往事；但医学案例的视觉相似性与个人事实适用性不同，不能直接照搬检索度量。该迁移是我的推断。

## 5. Critical thinking

表征相似不一定因果相关，可能拾取医院设备、图像风格和患者群体等捷径；检索库若与测试集近重复还会夸大收益。需要患者级/医院级去重、外部时序队列、错误案例检索与检索证据可解释性。报告的平均提升应拆开看每数据集和不确定度，且必须做医生参与的前瞻验证；不得将研究分数转化为诊断建议。

## 6. 可信度判断、优点与局限

3/5：多数据集和消融有信息量，且结论对 ICL 广泛有启发。医学高风险、跨机构泛化与检索库构造细节仍限制应用信心。
