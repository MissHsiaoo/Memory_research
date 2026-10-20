# Brain-Inspired Hierarchical Modularity：一般持续学习的层级模块化

- arXiv：[2609.25146](https://arxiv.org/abs/2609.25146)；[官方 PDF](https://arxiv.org/pdf/2609.25146)
- v1 提交日期：2026-09-21；正式公告批次：2026-09-23
- 作者/机构（PDF 首页核验）：Hongwei Yan 等；清华大学、清华-北大生命科学联合中心、中山大学
- 机构优先级：S（顶级高校；弱相关但对 self-evolving memory 有启发）
- 研究标签：continual learning、modularity、foundation model adaptation、catastrophic forgetting

## 1. 做了什么

论文从果蝇学习记忆系统抽象出层级模块原则：冲突经验由专家专门化隔离，兼容经验在空间与时间尺度上集成，并将其实现为预训练 foundation model 的轻量模块适配。

## 2. 怎么做、实验如何设计

方法用 brain-inspired random expansion 做 expert routing，再通过多尺度 diversified modular integration 融合知识。实验覆盖视觉识别、vision-language understanding、ego-exo video 与 embodied vision-language-action，强调 online、无明确任务边界和分布持续演化的 general continual learning；对 replay-free 方法和模块/路由组件做比较。

## 3. 结论

论文报告跨多种模型与模态持续改进；在 embodied manipulation 中相对 replay-free alternatives 提升超过 50 个百分点，支持“分离冲突、整合兼容经验”的层级模块机制。

## 4. Future impact

对 LLM agent memory 的启发是让记忆路由与整合成为可学习模块，而非单一全局 store：领域专家负责局部写入，慢速共享层吸收跨域稳定规律。

## 5. Critical thinking

“brain-inspired”主要是设计动机，不等于神经科学证据；大幅增益需检查 baseline 容量、参数增长和 replay 公平性。当前没有直接 LLM memory benchmark，因此应视为跨方向启发。建议在固定新增参数/计算、任务边界未知、长期非平稳语言 agent 上比较 MoE adapters、LoRA pools、retrieval memory，并测负迁移与 expert collapse。

## 6. 可信度判断

- 评分：4/5
- 依据：50 页全文、多个模态与 continual-learning regime、较系统的实验。
- 优点：机构强；问题定义比传统 task-incremental 更真实；跨模态证据丰富。
- 局限：与 LLM memory 为间接关联；生物类比可能被过度解读；容量公平性需仔细复核。

