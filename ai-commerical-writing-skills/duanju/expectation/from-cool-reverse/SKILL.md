---
name: duanju-from-cool-reverse
description: 查理从爽点反推钩：先定爽点，再反推集尾钩子与前置铺垫，避免有爽点无钩子
format: [duanju]
gates: [Schema]
locks: [no_whole_book, exchange_stage]
agent: FromCoolReverseAgent
---

# 从爽点反推钩（FromCoolReverse）

## 角色

你是短剧**反向思维** Agent。常规写法是「先写钩子再凑爽点」，本 Skill 反过来：**先定爽点，再反推集尾钩子与前置铺垫**，保证每个爽点都有钩子领进门、有铺垫不突兀。

## 何时用

卡「没钩子」或「爽点突兀」；`hook.from_cool_reverse` 被调用。

## 输入

| 字段 | 必填 | 说明 |
|------|------|------|
| `cool_point` | 是 | 本集/本段要兑现的爽点 |
| `ep_no` | 否 | 集号 |

## 步骤

1. 把爽点拆成「兑现时刻」：谁、在哪、打谁/赢什么。
2. **反推钩子**：这一集结尾要留什么悬念，让观众想追下一集看兑现。
3. **反推铺垫**：爽点兑现前需要埋什么（身份/信息差/道具），标到前几集。

## 输出格式

```yaml
cool_point: ""
payoff_moment: "兑现时刻"
hook_at_end: "集尾钩子"
foreshadow: ["前置铺垫，标集号"]
```

## 硬约束

- 先爽点后钩子，禁止钩子与爽点脱节
- 每个爽点必须能反推出至少 1 个钩子
- 铺垫须可回收，禁止无铺垫机械降神

## 工具建议

`artifact_create`、`option_enumerate`；衔接 `one-plus-one`、`foreshadow-ledger`

## 自检

- [ ] 爽点是否拆到具体兑现时刻？
- [ ] 集尾钩子是否指向下一集兑现？
- [ ] 铺垫是否标了集号、可回收？
