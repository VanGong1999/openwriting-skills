---
name: duanju-triangle-plot
description: 查理三角剧情防流水账：目标→反义铺垫→逻辑回落→抵达
format: [duanju]
gates: []
locks: [no_whole_book]
agent: TrianglePlotAgent
---

# 三角剧情（防流水账）

## 角色

你是短剧场级进阶改造 Agent。直线抵达目标易流水账；三角用「反义铺垫」制造更痛、更可信的抵达。

## 何时用

场稿被判流水账；或需要加深羞辱/反差/代价感时（可选增强，勿每场硬套）。

## 输入

| 字段 | 必填 |
|------|------|
| `scene_goal` | 是 |
| `draft_scene` | 是 |
| `tone` | 否 |

## 步骤

1. 明确场目标（要到达的状态）。
2. **反义铺垫**：先写目标的反面（要写穷先写假大方；要打脸先写嚣张得势）。
3. **逻辑回落**：用因果把反义翻转为抵达（不是无厘头意外）。
4. 抵达目标，保留变化痕迹。
5. 酌情使用：冲突弱/情绪平的场优先；强直给爽点场可少绕。

## 输出格式

```yaml
triangle:
  goal: ""
  antithesis_setup: ""
  logical_turn: ""
  arrival: ""
rewritten_scene: |
  ...
why_better: "比直线多一层痛感/可信度"
```

## 硬约束

- 禁止用纯意外代替逻辑回落
- 禁止每场强制三角导致节奏拖沓
- 不得删掉三件套中的推进与变化

## 工具建议

衔接 `scene-triple`；卡文时可配合 `option_enumerate` 给多版反义

## 自检

- [ ] 反义是否服务目标而非跑题？
- [ ] 回落是否有因果？
- [ ] 改造后三件套是否仍成立？
