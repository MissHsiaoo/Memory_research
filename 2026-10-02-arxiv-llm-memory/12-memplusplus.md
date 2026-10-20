# 12 — Mem++: Non-Destructive Memory for Long-Term Organizational LLM Agents

- arXiv：[2610.02002](https://arxiv.org/abs/2610.02002)；[官方 PDF](https://arxiv.org/pdf/2610.02002)；[本地 PDF](./2610.02002.pdf)
- v1 提交：2026-10-01；正式公告：2026-10-02（北京时间）
- 作者/机构（PDF 首页核验）：Ahmad Yehia 等；The University of Texas at Austin、AIDAChip Inc.
- 机构优先级：**A+，一流高校与产业合作**；研究标签：`organizational memory` `temporal retrieval` `non-destructive storage`
- 证据范围：核读 PDF 方法、实验；数字为作者报告。

## 1. 做了什么

为多作者组织文档建立不覆盖、不在写入时丢弃证据的长期记忆，以回答“当时哪一版决定有效”。

## 2. 怎么做、实验如何设计

写入时完整保存文档、日期、作者，不调用生成模型；读时先按问题时间过滤文档，再融合字面与语义排名，交由回答模型判断版本关系。PDF 在 OrgMemBench 中规模 443 件文档、157 条线索、18 个月、73 道问题；另测 LoCoMo 与 LongMemEval-S。作者报告 OrgMemBench 较最强记忆系统高 8.0–13.1 点，gpt-4.1-mini 上较 RAG 高 2.6 点。

## 3. Conclusion

不可逆的写时总结会限制未来未知问题；原文与时间来源保留可以把解释权推迟到读时。

## 4. Future impact

个人化记忆也可采用“原始证据不可破坏 + 派生摘要可更新”的双层设计，便于撤销与审计。

## 5. Critical thinking

**推断：** 完整保存文档牺牲存储与检索成本，读时模型仍可能误判版本。应测试大规模组织、作者权限、泄露旧敏感信息及时间戳错误；73 个组织题偏少。

## 6. 可信度判断

**3.5/5。** 跨三个基准并比较 RAG 是优点；核心组织基准为单一合成组织、样本有限。
