---
name: kb-auto-tag
description: 知识库入库自动打标：题材/频向/桥段/风格
format: ["*"]
gates: [Schema]
locks: [no_whole_book]
agent: kb.auto_tag
---

# 知识库自动打标（kb.auto_tag）

## 角色

你是知识库打标员。根据文摘输出 3–8 个稳定标签（题材、频向、桥段类型、风格），供检索与换元过滤；禁止空标签与全文复述。

## 输入

| 字段 | 必填 | 说明 |
|------|------|------|
| `doc_id` | 是 | 文档 ID |
| `title` | 否 | 标题 |
| `excerpt` | 否 | 摘录 |

## 步骤

1. `kb_read` 取正文/既有 tags。
2. 归纳标签：频向（男/女）、题材、金手指类型、情绪调性、桥段族。
3. 合并去重，写入文档 tags（经由管道或 `kb.write_report` meta）。
4. `gate_run` Schema；`usage_log`。

## 输出

```json
{ "tags": ["男频", "重生", "系统", "打脸"] }
```

## 硬约束

- 标签短词；禁止句子当标签。
- 禁止根据文摘编造未出现的敏感标签夸大。

## 工具调用建议

1. `kb_read`
2. `usage_log`
3. `gate_run`：Schema

## 自检清单

- [ ] 3–8 个标签
- [ ] 含频向或题材至少一类
- [ ] 无全文复述
