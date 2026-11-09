# 19. Not Your Diary, Just Your Topic: Grading the Wrong-User Control

- arXiv：[摘要及版本](https://arxiv.org/abs/2611.09609)
- PDF：[官方原文](https://arxiv.org/pdf/2611.09609) · [仓库内原文](pdf/2611.09609.pdf)
- 公告批次：2026-11-09，官方 New submissions；北京时间日报日期：2026-11-09。
- 首次提交日期：2026/11/06；与公告日期分别记录，完整官方版本记录见文末。
- 作者：Romanova, Karina；Kiselev, Igor；Platonov, Vladimir；Devbunova, Viliana；Leleytner, Gregory；Leleytner, Adeliya；Veltman, Lina；Nikolich, Aleksandr。
- 机构：首页已渲染并核验：Yandex；Accenture；RawModels；Independent Researcher；Institute for Information Transmission Problems；TBC Uzbekistan；Keenable AI。
- 机构优先级：B：低机构优先级黑马/启发性补充。
- 研究标签：personalization；用户记忆；因果对照；黑马。
- 相关性：直接相关（含持续学习、扩散语言模型及个性化方向）。
- 阅读范围：完整21页PDF已取得；重点阅读PDF物理页 1、3–6。未逐行审查所有附录、未复现实验。
- 证据边界：第3节是论文报告结果；第4节和第5节研究建议为评阅推断。

## 1. 做了什么

审计常见“换成其他用户历史后掉分”的个性化证据：随机换用户也改变主题和标签分布，因此掉分可能来自内容不匹配，而非真正识别个人。

## 2. 怎么做、实验如何设计

LaMP-2新闻15分类，1605验证样本323用户，每历史6条；冻结Qwen2.5，BGE+8槽Q-former，prefix加门控cross-attention。比较随机用户、相似用户derangement、标签/文本相似度匹配的合成历史、只标签历史，及单独训练的无历史模型。主划分大量用户训练中已见，另做两用户留出划分、三种子；电影实验仅一个种子。

## 3. 结论

自身历史79.36，评测时mask74.54，真正无历史训练77.09；因此把mask当无记忆基线会夸大收益。标签重现随机错用户差距86%；内容匹配合成历史78.44，剩余约.9点，bootstrap区间[.1,1.8]而t区间跨0。未见用户相似历史对照只余.65点、区间[-1.1,2.2]。

## 4. 未来影响

评阅推断：低机构优先级但方法学启发突出。研究个性化记忆时，应同时控制主题、标签、用户可见性与训练分布，避免把检索内容红利命名为个体化。

## 5. Critical thinking

匹配控制可能移除有意义的个体信号，不能反过来证明“个性化无用”；单任务、冻结骨干也限制结论。建议同时报告随机/主题匹配/偏好冲突/冷用户四组，预注册匹配强度，保留数据解析审计，并换生成式任务检验。

## 6. 可信度判断

4/5。依据：多层反事实对照、用户留出、种子及不确定性报告扎实。局限：范围窄、不同置信区间结论不完全一致、电影pilot有限。作为黑马收录，机构标签不影响独立证据分。

## 官方提交与版本记录

Submission history From: Karina Romanova [ view email ] [v1] Fri, 6 Nov 2026 15:34:02 UTC (162 KB)
