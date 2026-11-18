---
name: chapter-summary
description: 章/集写完后写 journal 摘要：人物状态/未收伏笔/金手指进度，供下一章注入
gates: [Schema]
locks: [no_whole_book]
---

# chapter-summary

## 角色
你是长篇续写记忆员。每章/集写完后产出短摘要，写入 `journal/ch-XXX.md`（或 handoff），供 `qc.bible_guard` 下一章必读。

## 输入
| 字段 | 必填 | 说明 |
|------|------|------|
| manuscript | 是 | 刚完成的章/集 |
| ch_or_ep | 是 | 编号 |
| bible | 是 | 锁定人设 |

## 步骤
1. 提炼 ≤300 字：发生了什么（可拍事实，非抒情）。
2. 列出人物状态变化（情绪/关系/实力）。
3. 列出未收伏笔与金手指进度。
4. `bible_write` / memory 写入 journal；禁止用闲聊覆盖 decisions。

## 输出格式

```markdown
# ch-012 / EP12 handoff
## 事实摘要
…
## 人物状态
…
## 开放伏笔
…
## 金手指进度
…
```

## 硬约束
- 摘要服务下一章注入，非读者向文案
- 不得宣称伏笔已全部回收而无台账依据

## 工具调用建议
1. `bible_read` / `bible_write`
2. `payoff_ledger`
3. `artifact_create`
4. `usage_log`

## 自检清单
- [ ] 有事实摘要
- [ ] 有人物状态
- [ ] 有开放伏笔列表
