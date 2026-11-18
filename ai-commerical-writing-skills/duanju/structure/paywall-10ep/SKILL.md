---
name: duanju-paywall-10ep
description: 查理付费卡点：每10集强钩子；8–9集加压；单集1–3爽点
format: [duanju]
gates: [PaywallCoverageGate]
locks: [no_whole_book, lock_cool_paywall]
agent: PaywallMapAgent
---

# 付费卡点规划（每 10 集）

## 角色

你是短剧付费预期 Agent。充值=To C 预期管理；前 20 集拉满主期待；每 10 集强钩子；第 8–9 集加压；卡点集禁止大段解释/回忆占篇幅。

## 何时用

`beat_20` 确认后；十集大纲与扩展 80–120 集时循环注入。

## 输入

| 字段 | 必填 |
|------|------|
| `beat_20` | 是 |
| `ep_count` | 是 |
| `core_expectation` | 是 |
| `cool_stack` | 建议 |
| `gender_band` | 是 |

## 步骤

1. `paywall_slots(total_eps)` 生成槽位：每 10 集末强钩子 + 每段 8–9 加压。
2. 每槽写：钩子类型（悬念/危机/反转/掉马甲…）+ 一加一兑现预告 + 禁止重复的旧梗列表。
3. 单集爽点预算：1–3；前 20 集主期待密度最高。
4. 女频：充值点不重复旧梗；保持观众开天眼。
5. 中后段（约 50 集后）：可加痛感/两难，但不抵消爽；乏力加反派/背叛。

## 输出格式

```yaml
paywall_map:
  - ep: 10
    phase: "强钩子"
    hook: ""
    payoff_plus_one: ""
    banned_reuse: []
  - ep: 8
    phase: "加压"
    pressure: ""
ep8_9_hooks: []
cool_per_ep_budget: "1-3"
```

## 硬约束

- 缺 10 集槽或 8–9 加压 → PaywallCoverageGate Fail
- 卡点集禁大段电话/回忆解释（no-exposition-on-paywall）
- 禁止充值后立刻注水；钩子须新信息或新压迫

## 工具建议

`paywall_slots`、`payoff_ledger`、`decay_detect`、`table_write`

## 自检

- [ ] 每 10 集是否有强钩子？
- [ ] 8–9 是否加压？
- [ ] 是否与核心预期台账一致？
