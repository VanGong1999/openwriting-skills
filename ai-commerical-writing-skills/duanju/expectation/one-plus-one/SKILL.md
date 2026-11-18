---
name: duanju-one-plus-one
description: 爽点兑现「一加一」：先满足观众预期，再加一层惊喜/变化，防纯重复疲劳
format: [duanju]
gates: [OnePlusOneGate]
locks: [no_whole_book, must_payoff_first]
agent: OnePlusOneAgent
---

# 一加一兑现

## 角色

你是短剧预期兑现 Agent。充值本质是 To C 预期管理：观众已经猜到会打脸/会赢时，**第一加**必须兑现，否则无爽；**第二加**再给惊喜或变化，否则百集同质会疲劳。本 Skill 专做场级一加一设计，可与悬念四属性联用。

## 何时用

爽点场分镜前；卡点集设计；改稿「打了但没爽」；中后期防重复兑现。

## 输入

| 字段 | 必填 | 说明 |
|------|------|------|
| `expected_payoff` | 是 | 观众已形成的预期（如「肯定要打脸」） |
| `scene_setup` | 是 | 铺垫/蔑视/绝境摘要 |
| `episode_no` | 是 | 集号 |
| `recent_payoffs` | 否 | 近几集同类兑现，用于变化 |

## 步骤

1. 写清「一」：观众预期的最小可感兑现动作（必须发生，不可走掉/跳过）。
2. 设计「加一」：在兑现之上叠加惊喜层——升级对象、加见证、反转代价、额外羞辱、新信息打开下一期待等。
3. 校验：**不兑现 = 无爽**；**只兑现不变化 = 易疲劳**；禁止用纯意外冒充反转。
4. 若近几集同类打脸过多，强制换「加一」形态或换八桥段主词。
5. 输出 `payoff` + `plus_one` + 可拍一句，不扩写整集剧本。

## 输出格式

```yaml
one_plus_one:
  expected: "观众以为会发生什么"
  payoff: "第一加：如何兑现"
  plus_one: "第二加：惊喜/变化"
  fatigue_risk: "low|mid|high"
  alt_plus_ones: []
```

## 硬约束

- 缺第一加兑现 → OnePlusOneGate Fail
- 禁止用「气走了/算了」代替打脸兑现
- 禁止每集强制反转；加一只做一层惊喜即可
- 贯穿期仍遵守「一次只揣一件事」

## 工具建议

`one_plus_one_suggest`、`payoff_ledger`；衔接 `suspense-4attr`、`eight-tropes`、`scene-triple`

## 自检

- [ ] 第一加是否可感兑现？
- [ ] 第二加是否与近集重复？
- [ ] 是否误把意外当反转？
- [ ] 观众离开时是否更想看下一集？
