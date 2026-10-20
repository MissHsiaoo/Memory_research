# 16｜中科大：CASK 为长期记忆写入保留“这是谁的事实”

- 论文：[arXiv:2610.09008](https://arxiv.org/abs/2610.09008)｜[官方 PDF](https://arxiv.org/pdf/2610.09008)｜本地 `2610.09008.pdf`
- 正式公告：2026-10-08（cs.AI New submissions）；首次提交：2026-10-06 UTC，v1。作者/机构（PDF 首页）：Hongyu Gu、Xinchang Li；University of Science and Technology of China。机构优先级：A+；标签：memory write gate、latent representation、scope/provenance；直接相关。

## 1. 做了什么

思考中的假设、模拟工具结果、他人观点与最终世界事实可能文字相似；把句子脱离话语作用域保存，会让未来 agent 把试探性内容误当事实。CASK 主张记忆提交时保留 proposition 的 discourse ownership，即它属于哪个世界、分支或说话者。

## 2. 怎么做、实验如何设计

先在冻结 Qwen2.5-3B/1.5B 的内部表示中找与 ownership 相关且可因果干预的子空间；由于具体坐标基不稳定，CASK 保存更稳定的 typed 关系不变量，而非原始坐标。PDF 在 LoCoMo 的 486 个精确答案问题上构造 972 条冲突记录，比较 gate 作用于同一 BM25 排序后的污染与回答；另用 4,860 条配对记录分别隔离 scope 与 payload，做跨对话折分、未见报告框架及工具轨迹测试。

## 3. 结论

在 3B 模型的 146 个 held-out 案例上，ownership 子空间干预使 91.78% 路由到目标 mental space，随机子空间仅 3.22%；默认阈值下 CASK 的 attachment 准确率为 83.33%（3B）及 79.82%（1.5B）。这支持内部确有可用的归属信号，但还不是通用部署证明。

## 4. 未来影响（推断）

个人化 memory 写入可以携带“用户明确说/助手猜测/模拟计划/第三方转述”等 typed provenance，避免一次推理假设变成长期画像。内部状态方法还可辅助传统文本来源标记。

## 5. Critical thinking

论文仅用两个小型 Qwen 骨干，且 LoCoMo 只选能精确匹配的 486 问、独立历史数量有限；遇到讽刺、引用嵌套和跨语种转述时 ownership 未必二元。建议与无需 hidden state 的强文本 provenance 方法对照，检验模型升级后的 key 稳定性，并在真实多参与者对话中测错误写入率及撤销成本。

## 6. 可信度：3/5

依据：已核查 PDF 的因果干预、source-isolated 协议与结果。优点是用干预而非仅相关性论证内部信号，并隔离 scope/payload；局限是数据与模型覆盖窄，复杂分布移位下的部署校准仍未完成。
