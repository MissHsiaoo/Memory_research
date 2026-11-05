# 19. Sekai: Incremental Event Memory for Generalized Reasoning Video Segmentation

- arXiv：[摘要与版本记录](https://arxiv.org/abs/2611.06685)
- 官方 PDF：[在线原文](https://arxiv.org/pdf/2611.06685)；[仓库内 PDF](pdf/2611.06685.pdf)
- 官方列表批次：2026-11-05（New submissions）；北京时间日报日期：2026-11-05。
- 首次提交日期：2026/11/04（以官方摘要页元数据及下方版本记录核验，不等同于公告日）。
- 作者：Liu, Zhengtao；Xu, Jinrong；Kao, Shiu-Hong；Sun, Huixin；Li, Yicong
- 机构：首页署名已核验：USTC；National University of Singapore。不根据邮箱、模型名称或代码组织推断雇佣关系。
- 机构优先级：A2：一流研究型高校/实验室合作。
- 研究标签：event memory; streaming multimodal reasoning。
- 相关性：弱相关但具启发性：视频事件记忆，可迁移到多模态代理。
- 阅读范围：PDF首页及关键方法/实验页 1、4–7；已获取完整20页PDF，但不声称逐行审阅全部附录或复现实验。
- PDF核验：文件头与全部页结构可解析；首页已渲染检查。

## 1. 做了什么

研究视频流中查询目标随历史事件变化的记忆推理，将对象仍符合条件和当前可见分离。

## 2. 怎么做、实验如何设计

Isekai包含60视频、197查询、12,569评分点，11种时间查询；事件只在已观察前缀足以确认后生效。冻结事件写入器维持128-token结构记忆，LoRA定位器读取记忆+当前8帧，再由SAM传播掩码。统一因果输入比较在线方法，并做去记忆对照。

## 3. 结论

表3总体J&F 50.33对无记忆45.61；但history子集65.97低于StreamingRVOS 68.71，Latest/Never等也非最佳。20视频双标注目标集一致93%，事件一对一匹配仅80.6%。

## 4. 未来影响

推断：事件记忆的关键不是存更多帧，而是维护身份绑定、时间状态和未知性；对多模态代理记忆有直接启发。

## 5. Critical thinking

128-token固定状态随实体/事件增多必然丢信息，8帧端点刷新有反应延迟。空目标点占比大，会影响总体分数；history子集只在部分查询族定义。建议按空/单/多目标、证据年龄、身份重现分层，扩大长视频并用oracle事件判断定位/记忆各自误差。

## 6. 可信度判断

3/5。严格因果标注和去记忆对照有帮助；小样本、部分类型退化及分割器影响需要保留。

## 官方提交记录

Submission history From: Zhengtao Liu [ view email ] [v1] Wed, 4 Nov 2026 15:52:38 UTC (11,744 KB)
