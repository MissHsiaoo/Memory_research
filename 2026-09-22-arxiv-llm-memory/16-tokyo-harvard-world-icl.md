# Few-Shot Demonstrations Elicit the Use of In-Context World Representations in LLMs

- arXiv：[24352](https://arxiv.org/abs/2609.24352)；[官方 PDF](https://arxiv.org/pdf/2609.24352)
- arXiv 初次提交：2026-09-21（v1）；正式公告归属：2026-09-22 新稿，二者不可混同。
- 作者：Kohsei Matsutani , Gouki Minegishi , Core Francisco Park , Takeshi Kojima , Yusuke Iwasawa , Yutaka Matsuo（arXiv 官方列表）
- 机构：The University of Tokyo；Harvard University；Prior Computers（论文 PDF 首页核验）
- 机构优先级：A｜全球一流研究型高校
- 研究标签：in-context learning；世界表征；latent state；agent；直接相关
- 证据说明：以下数值均为论文自身报告；“我的推断/建议”并非论文实证。

## 1. 做了什么

论文区分两个经常混淆的问题：LLM 是否在上下文中形成了世界状态表征，以及它是否真的使用该表征做预测。作者发现少样本示例主要改变表征的读取/使用，而非简单让表征本身更可解码。这对 latent memory 的“存在不等于被用到”尤其关键。

## 2. 怎么做，实验怎么做的

在隐含图世界中，给模型随机游走和来自不同世界的示范，让它预测图上未见节点关系；跨四模型家族的六个模型测试。用线性探针定位低维图拓扑表征，比较零样本/多样本的探针可解码度和子空间方向，再对表征子空间做干预并与随机方向干预比较。论文报告 few-shot 后任务表现提高，表征接近正交方向迁移，目标干预对预测造成更大损害；还在 ARC-AGI-1/2、web agent 和 Othello 上探索迁移。文本明确说探针准确率与 Dirichlet 能量并不随 shot 数同步提高。

## 3. Conclusion

更好的 ICL 表现可能来自让已有世界表征更参与决策，而非产生全新的可线性解码知识。干预证据加强了这一解释，但不能把线性子空间完全等同“模型真实世界模型”的全部内容。

## 4. Future impact

评估 agent latent memory 不应只训练一个 probe 并宣称模型记住了；更应测表征在反事实干预后是否影响行动。若成立，提示示例排序可能是轻量的记忆读取控制器。这是我的推断。

## 5. Critical thinking

图世界的干预可控，开放网页和科研任务的世界状态却更复杂；迁移实验可能同时引入提示长度和答案格式因素。建议相同 token 预算下打乱示范拓扑/答案、分离词汇提示与规则提示，并测试隐藏事实更新后旧表征是否妨碍新推理。另要验证定位到的正交转移在不同层、模型和随机种子是否稳定。

## 6. 可信度判断、优点与局限

4/5：机制实验跨模型且有定向干预，较纯 probe 关联更可信。局限是人工图任务和下游场景的桥接尚不完全、内部表征解释仍存在多种可能。
