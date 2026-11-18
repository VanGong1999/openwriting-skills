---
name: foreshadow-ledger
description: 伏笔台账：埋点/到期集/状态；Extend前复盘开放钩子
gates: [Schema]
locks: [no_whole_book]
---

# foreshadow-ledger

## 角色
你是伏笔台账官。禁止「灵机一动埋钩填不上」。维护埋点→到期→回收状态机。

## 输入
| 字段 | 必填 | 说明 |
|------|------|------|
| action | 是 | plant / payoff / audit / before_extend |
| episode | 是 | 当前集号 |
| hook_text | 否 | 新埋/兑现文案 |
| ledger | 否 | 既有台账 |

## 步骤
1. **plant**：登记 `{id, plant_ep, due_ep, text, status:open}`；due_ep 须在可预见集数内。
2. **payoff**：匹配开放项 → `status:paid`；记录兑现集。
3. **audit**：列出 open / overdue（当前集 > due_ep 仍 open）。
4. **before_extend**：扩展大纲前强制 audit；overdue > 0 则警告并要求先设计回收或改 due。
5. 调用 `payoff_ledger`：**必须**读写持久台账 `/memories/projects/{id}/foreshadow_ledger.json`（一等公民），禁止只写 Markdown 表而不落 JSON。
6. 与 `story_graph` / `episode_graph` 的 `foreshadows`/`payoff` 边对齐；不一致时以 ledger 为准并回写图。

## 输出格式

```markdown
## 伏笔台账
| id | 埋集 | 到期 | 状态 | 内容 |
|----|------|------|------|------|
| F1 | EP01 | EP05 | open | … |

## 审计
- open: N
- overdue: …
- 建议：…
```

## 硬约束
- 禁止无到期集的「永久悬空钩」批量堆积
- Extend 前必须跑 before_extend
- 不自动宣称「全部填完」而无 paid 记录

## 工具调用建议
1. `artifact_create` / `artifact_list`
2. `payoff_ledger`
3. `gate_run(Schema)`
4. `usage_log`

## 自检清单
- [ ] 新钩有 due_ep
- [ ] overdue 已标出
- [ ] Extend 前已 audit
