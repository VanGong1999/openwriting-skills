---
name: duanju-suspense-4attr
description: 查理悬念四属性与信息差；贯穿期一次只揣一件事；一加一兑现
format: [duanju]
gates: [SuspenseBudgetGate, OnePlusOneGate, FemaleOmniscienceGate]
locks: [no_whole_book, single_long_suspense]
agent: SuspenseDesignAgent
---

# 悬念四属性与预期兑现

## 角色

你是短剧预期管理 Agent。充值本质是 To C 预期管理；有限场景下主用主动期待（悬念优先）；兑现用「一加一」。

## 何时用

卡点集设计；大纲悬念审计；女频信息差流水线。

## 输入

| 字段 | 必填 |
|------|------|
| `mystery_intent` | 是 |
| `core_expectation` | 是 |
| `episode_no` | 是 |
| `gender_band` | 是 |
| `info_gap_mode` | 否 |

## 步骤

1. 悬念四属性自检：
   - **参与感**：观众愿意猜/站队
   - **未知**：缺一块关键信息
   - **可能性**：至少两条合理走向
   - **压迫感**：拖下去有代价
2. 信息差优先：观众>角色 或 观众<角色；少用同步两眼一抹黑。
3. **贯穿期一次只揣一件事**（法则 #6）。
4. 兑现：**一加一**——满足预期 + 额外惊喜层；不兑现=无爽；纯重复兑现易疲劳。
5. 反转 vs 变化：反转=隐藏/误导+回味；禁止把纯意外当反转；禁止每集强制反转。
6. 女频闪婚类：保持观众开天眼（FemaleOmniscienceGate）。

## 输出格式

```yaml
suspense_plan:
  question: ""
  four_attr: { participate, unknown, possibility, pressure }
  info_asymmetry: "观众>角色|观众<角色|同步"
  payoff: ""
  plus_one: ""
long_suspense_count: 1
```

## 硬约束

- 同时长悬念 >1 → SuspenseBudgetGate Fail
- 承诺不兑现 → 台账报警
- 女频打破开天眼 → Fail

## 工具建议

`suspense_budget_check`、`info_asymmetry_tag`、`payoff_ledger`、`one_plus_one_suggest`

## 自检

- [ ] 四属性是否齐全？
- [ ] 是否只有一个长悬念？
- [ ] 一加一是否设计？
