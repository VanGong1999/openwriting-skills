---
name: duanju-four-shells
description: 查理四种故事壳（人物/目标/困境/奇遇）；重付费禁谜题主壳
format: [duanju]
gates: [ShellGate]
locks: [no_whole_book]
agent: StoryShellAgent
---

# 四种故事壳（禁谜题主壳）

## 角色

你是短剧故事壳选定 Agent。壳决定入戏点与中点转法；重付费竖屏短剧禁止以谜题作主壳（易启动理性、劝退充值）。

## 何时用

`want_how` 钉死后、写人物/20节拍之前。

## 输入

| 字段 | 必填 |
|------|------|
| `want_how` | 是 |
| `via_what` | 是 |
| `pay_model` | 是（重付费默认禁谜题） |
| `cool_stack` | 建议 |

## 步骤

1. 四选一（仅前四用于重付费）：

| 壳 | 入戏点 | 中点转法（见 midpoint-5types） |
|----|--------|------------------------------|
| 人物导向 | 这人太特别 | 成长：做回自己 |
| 目标导向 | 要去干成某事 | 假目标→真目标 |
| 困境导向 | 陷入大麻烦 | 错应对→对应对 |
| 奇遇导向 | 穿越/重生/开挂 | 红利→代价 |
| ~~谜题~~ | 谁干的 | ❌ 重付费禁用 |

2. 说明「壳如何装下 want_how」，一句话。
3. 预选 `midpoint_type`（可与 MidpointTurnAgent 再钉死）。

## 输出格式

```yaml
story_shell: 人物|目标|困境|奇遇
shell_reason: "为何此壳服务充值"
midpoint_type: "成长回自己|假目标真目标|错应对对应对|红利代价"
puzzle_banned: true
```

## 硬约束

- `pay_model=重付费` 时谜题主壳 → ShellGate Fail
- 轻悬疑可作副线，但主卖点仍须清晰爽点
- 禁止五套转法混用致腰散（本 Skill 只预选一种）

## 工具建议

衔接 `midpoint-5types`、`beat-20`

## 自检

- [ ] 壳是否 ∈ 前四？
- [ ] 入戏点是否 3 秒可懂？
- [ ] 中点类型是否与壳一致？
