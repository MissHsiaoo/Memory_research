# 15 — GUI-HARVEST: Self-Improving GUI Agents through Evidence-Driven Harness Evolution

- arXiv：[2610.00948](https://arxiv.org/abs/2610.00948)；[官方 PDF](https://arxiv.org/pdf/2610.00948)；[本地 PDF](./2610.00948.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Geyi Yang 等；Chinese University of Hong Kong, Shenzhen、Tianjin University、Harbin Institute of Technology (Shenzhen)、East China Normal University、Shenzhen Research Institute of Big Data
- 机构优先级：**A+，一流高校合作**；研究标签：`self-evolving agent` `GUI memory` `failure evidence`
- 证据范围：核读 PDF 方法与实验；数值为作者报告。

## 1. 做了什么

用可复核的界面行动证据来改写 GUI agent 的外部执行 harness，而不改底模权重。

## 2. 怎么做、实验如何设计

先把模型意图、实际动作与前后截图对齐；同任务多次运行用来辨别随机执行噪声；跨任务汇总已验证失败模式，再转成有预先预测效果的有限源码改动。PDF 在 OSWorld-Verified 中以 80 搜索、80 验证、201 密封测试任务分割，并测六种模型、重复执行；Qwen3-VL-32B-Instruct 全集提升 12.33 点。冻结 harness 在 WindowsAgentArena 对 GPT-5 的迁移作者报告 +13.87 点。

## 3. Conclusion

自改进应绑定行动前后证据和预注册效果，而不只是靠代理自我反思产生补丁。

## 4. Future impact

可推广到 agent memory 的“经验写入前证据门”：失败模式只有跨任务复现后才晋升为长期规则。

## 5. Critical thinking

**推断：** 测试环境和截图差异可能暗示任务答案，代码补丁仍可能对 OSWorld 形式过拟合。应审计总搜索成本、密封集访问、跨 OS/GUI 版本与失败回滚能力。

## 6. 可信度判断

**4/5。** 搜索/验证/测试拆分、六底模和跨环境迁移是强点；长期在线演化及安全性仍需外部复核。
